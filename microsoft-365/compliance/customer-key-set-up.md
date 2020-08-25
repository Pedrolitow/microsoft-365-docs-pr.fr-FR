---
title: Configurer la clé client
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 02/05/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Découvrez comment configurer la clé client pour les fichiers Microsoft 365 pour Exchange Online, Skype entreprise, SharePoint Online, OneDrive entreprise et Teams.
ms.openlocfilehash: 0743b4339dae8e70960293f51a7869dc61fea606
ms.sourcegitcommit: 22dab0f7604cc057a062698005ff901d40771692
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "46868889"
---
# <a name="set-up-customer-key"></a>Configurer la clé client

Avec la clé client, vous contrôlez les clés de chiffrement de votre organisation, puis vous configurez Microsoft 365 afin de les utiliser pour chiffrer vos données au repos dans les centres de données de Microsoft. En d’autres termes, la clé client permet aux clients d’ajouter une couche de chiffrement qui leur appartient, avec leurs clés. Les données au repos incluent les données issues d’Exchange Online et de Skype Entreprise qui sont enregistrées dans des boîtes aux lettres et des fichiers stockés dans SharePoint Online et OneDrive Entreprise.

Vous devez configurer Azure avant de pouvoir utiliser la clé client pour Office 365. Cette rubrique décrit les étapes à suivre pour créer et configurer les ressources Azure requises, puis fournit la procédure de configuration de la clé client dans Office 365. Une fois que vous avez terminé la configuration d’Azure, vous déterminez la stratégie et, par conséquent, les clés, à affecter aux boîtes aux lettres et aux fichiers de votre organisation. Les boîtes aux lettres et les fichiers pour lesquels vous n’affectez pas de stratégie utilisent des stratégies de chiffrement qui sont contrôlées et gérées par Microsoft. Pour plus d’informations sur la clé client ou pour obtenir une vue d’ensemble, consultez la rubrique [service Encryption with Customer Key in Office 365](customer-key-overview.md).
  
> [!IMPORTANT]
> Nous vous recommandons vivement de suivre les meilleures pratiques de cette rubrique. Ces éléments sont appelés « **Conseil** » et « **important**». La clé client vous permet de contrôler les clés de chiffrement racines dont l’étendue peut être aussi importante que l’ensemble de votre organisation. Cela signifie que les erreurs comprises avec ces clés peuvent avoir un impact général et peuvent entraîner des interruptions de service ou une perte irrévocable de vos données.
  
## <a name="before-you-set-up-customer-key"></a>Avant de configurer la clé client

Avant de commencer, assurez-vous que vous disposez de la licence appropriée pour votre organisation. La clé client dans Microsoft 365 est proposée dans Office 365 E5 ou le SKU de conformité avancée. Pour comprendre les concepts et procédures présentés dans cette rubrique, consultez la documentation sur le [coffre-fort des clés Azure](https://docs.microsoft.com/azure/key-vault/) . De même, familiarisez-vous avec les termes utilisés dans Azure, par exemple, [client](https://docs.microsoft.com/previous-versions/azure/azure-services/jj573650(v=azure.100)).

FastTrack est utilisé uniquement pour collecter les informations de configuration de service et de client requises utilisées pour s’inscrire à la clé client. Les offres de clés de client sont publiées via FastTrack pour que vous et nos partenaires pouvez envoyer les informations requises à l’aide de la même méthode. FastTrack facilite également l’archivage des données que vous fournissez dans l’offre.
  
Si vous avez besoin d’une assistance supplémentaire au-delà de la documentation, contactez Microsoft Consulting Services (MCS), premier Field Engineering (PFE) ou un partenaire Microsoft pour obtenir de l’aide. Pour fournir des commentaires sur la clé client, y compris la documentation, envoyez vos idées, suggestions et perspectives à customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Vue d’ensemble des étapes de configuration de la clé client

Pour configurer la clé client, effectuez les tâches suivantes dans l’ordre indiqué. Le reste de cet article fournit des instructions détaillées pour chaque tâche, ou des liens vers des informations supplémentaires pour chaque étape du processus.
  
**Dans Azure et Microsoft FastTrack :**
  
Vous effectuerez la plupart de ces tâches en vous connectant à distance à Azure PowerShell. Pour obtenir de meilleurs résultats, utilisez la version 4.4.0 ou une version ultérieure d’Azure PowerShell.
  
- [Créer deux nouveaux abonnements Azure](#create-two-new-azure-subscriptions)

- [Enregistrer des abonnements Azure pour utiliser une période de rétention obligatoire](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  L’inscription peut prendre entre un et cinq jours ouvrés.

- [Soumettre une demande d’activation de la clé client pour Office 365](#submit-a-request-to-activate-customer-key-for-office-365)

Une fois que vous avez créé les deux nouveaux abonnements Azure, vous devez soumettre la demande d’offre de clé client appropriée en remplissant un formulaire Web hébergé dans le portail Microsoft FastTrack. **L’équipe FastTrack ne fournit pas d’assistance pour la clé client. Office utilise simplement le portail FastTrack pour vous permettre d’envoyer le formulaire et de nous aider à suivre les offres pertinentes pour la clé client**.

- [Créer un coffre-fort de clés Azure pour chaque abonnement](#create-a-premium-azure-key-vault-in-each-subscription)

- [Attribuer des autorisations à chaque coffre-fort de clés](#assign-permissions-to-each-key-vault)

- [Activer, puis confirmer la suppression logicielle de vos coffres-forts principaux](#enable-and-then-confirm-soft-delete-on-your-key-vaults)

- [Ajouter une clé à chaque coffre-fort de clés en créant ou en important une clé](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Vérifier le niveau de récupération de vos clés](#check-the-recovery-level-of-your-keys)

- [Sauvegarder le coffre de clés Azure](#back-up-azure-key-vault)

- [Valider les paramètres de configuration de coffre-fort de clés Azure](#validate-azure-key-vault-configuration-settings)

- [Obtenir l’URI de chaque clé Azure Key Vault](#obtain-the-uri-for-each-azure-key-vault-key)

**Dans Office 365 :**
  
Exchange Online et Skype entreprise :
  
- [Créer une stratégie de chiffrement de données (DEP) à utiliser avec Exchange Online et Skype entreprise](#create-a-data-encryption-policy-dep-for-use-with-exchange-online-and-skype-for-business)

- [Affecter une DEP à une boîte aux lettres](#assign-a-dep-to-a-mailbox)

- [Valider le chiffrement de boîtes aux lettres](#validate-mailbox-encryption)

SharePoint Online et OneDrive entreprise :
  
- [Créer une stratégie de chiffrement de données (DEP) pour chaque région de SharePoint Online et OneDrive entreprise](#create-a-data-encryption-policy-dep-for-each-sharepoint-online-and-onedrive-for-business-geo)

- [Valider le chiffrement de fichiers pour SharePoint Online, OneDrive entreprise et les fichiers teams](#validate-file-encryption)

## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Effectuer des tâches dans Azure Key Vault et Microsoft FastTrack pour la clé client

Effectuez ces tâches dans le coffre-fort des clés Azure. Vous devez effectuer ces étapes, que vous souhaitiez configurer la clé client pour Exchange Online et Skype entreprise ou pour les fichiers SharePoint Online, OneDrive entreprise et Teams, ou pour tous les services pris en charge dans Office 365.
  
### <a name="create-two-new-azure-subscriptions"></a>Créer deux nouveaux abonnements Azure

La clé client nécessite deux abonnements Azure. Pour une meilleure pratique, Microsoft vous recommande de créer de nouveaux abonnements Azure à utiliser avec la clé client. Les clés Azure Key Vault peuvent uniquement être autorisées pour les applications dans le même client Azure Active Directory (Microsoft Azure Active Directory), vous devez créer les nouveaux abonnements à l’aide du même client Azure AD que celui utilisé avec votre organisation où le DEPs sera affecté. Par exemple, à l’aide de votre compte professionnel ou scolaire disposant de privilèges d’administrateur général dans votre organisation. Pour obtenir la procédure détaillée, consultez la rubrique [Inscrivez-vous à Azure en tant qu’organisation](https://azure.microsoft.com/documentation/articles/sign-up-organization/).
  
> [!IMPORTANT]
> La clé client nécessite deux clés pour chaque stratégie de chiffrement de données (DEP). Pour ce faire, vous devez créer deux abonnements Azure. En guise de meilleure pratique, Microsoft recommande que les membres distincts de votre organisation configurent une clé dans chaque abonnement. En outre, ces abonnements Azure ne doivent être utilisés que pour administrer les clés de chiffrement pour Office 365. Cela protège votre organisation si l’un de vos opérateurs supprime accidentellement, intentionnellement ou de manière malveillante ou non des clés dont il est responsable. <br/> Nous vous recommandons de configurer de nouveaux abonnements Azure uniquement utilisés pour gérer les ressources Azure Key Vault à utiliser avec la clé client. Il n’existe pas de limite pratique au nombre d’abonnements Azure que vous pouvez créer pour votre organisation. Le suivi de ces meilleures pratiques réduira l’impact de l’erreur humaine tout en aidant à gérer les ressources utilisées par la clé client.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Soumettre une demande d’activation de la clé client pour Office 365

Une fois que vous avez terminé les étapes Azure, vous devrez soumettre une demande d’offre dans le [portail Microsoft FastTrack](https://fasttrack.microsoft.com/). Une fois que vous avez soumis une demande via le portail Web FastTrack, Microsoft vérifie les données de configuration du coffre de clés Azure et les informations de contact que vous avez fournies. Les sélections effectuées dans le formulaire d’offre concernant les responsables autorisés de votre organisation sont essentielles et nécessaires à la réalisation de l’enregistrement de la clé client. Les responsables de votre organisation sélectionnés dans le formulaire seront utilisés pour garantir l’authenticité de toute demande de révocation et de destruction de toutes les clés utilisées avec une stratégie de chiffrement des données de clé client. Vous devrez effectuer cette étape une fois pour activer la clé client pour la couverture Exchange Online et Skype entreprise et une deuxième fois pour activer la clé client pour SharePoint Online et OneDrive entreprise.
  
Pour soumettre une offre d’activation de la clé client, procédez comme suit :
  
1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur globales dans votre organisation, connectez-vous au [portail Microsoft FastTrack](https://fasttrack.microsoft.com/).

2. Une fois que vous êtes connecté, accédez au **tableau de bord**.

3. Choisissez **Deploy** dans la barre de navigation **ou** sélectionnez **afficher toutes les ressources de déploiement** sur la carte de **déploiement** des informations, puis passez en revue la liste des offres actuelles.

4. Choisissez la carte d’informations de l’offre qui vous concerne :

   - **Exchange Online et Skype entreprise :** Choisissez l' **aide de la clé de chiffrement de demande pour l’offre Exchange Online** .

   - **Fichiers SharePoint Online, OneDrive et teams :** Choisissez l' **aide de la clé de chiffrement de demande pour SharePoint et OneDrive** offre.

5. Une fois que vous avez consulté les détails de l’offre, choisissez **passer à l’étape 2**.

6. Renseignez toutes les informations pertinentes et les informations demandées dans le formulaire d’offre. Prêtez particulièrement attention à vos choix pour les responsables de votre organisation autorisés à approuver la destruction permanente et irréversible des clés et des données de chiffrement. Une fois que vous avez terminé le formulaire, sélectionnez **Envoyer**.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Enregistrer des abonnements Azure pour utiliser une période de rétention obligatoire

La perte temporaire ou définitive de clés de chiffrement racine peut être très perturbatrice ou même catastrophique pour les opérations de service et peut entraîner une perte de données. Pour cette raison, les ressources utilisées avec la clé client nécessitent une protection renforcée. Toutes les ressources Azure utilisées avec les mécanismes de protection de l’offre de clé client au-delà de la configuration par défaut. Les abonnements Azure peuvent être balisés ou enregistrés de manière à empêcher toute annulation immédiate et irrévocable. Il s’agit de l’enregistrement pour une période de rétention obligatoire. Les étapes requises pour enregistrer les abonnements Azure pour une période de rétention obligatoire nécessitent une collaboration avec l’équipe Microsoft 365. Ce processus peut prendre entre un et cinq jours ouvrés. Auparavant, il était parfois appelé « ne pas annuler ».
  
Avant de contacter l’équipe Microsoft 365, vous devez effectuer les étapes suivantes pour chaque abonnement Azure que vous utilisez avec la clé client. Assurez-vous que le module [Azure PowerShell AZ](https://docs.microsoft.com/powershell/azure/new-azureps-module-az) est installé avant de commencer.
  
1. Connectez-vous avec Azure PowerShell. Pour obtenir des instructions, consultez la rubrique [se connecter avec Azure PowerShell](https://docs.microsoft.com/powershell/azure/authenticate-azureps).

2. Exécutez la cmdlet Register-AzProviderFeature pour enregistrer vos abonnements afin d’utiliser une période de rétention obligatoire. Effectuez cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

3. Contactez Microsoft pour finaliser le processus. Pour l’équipe SharePoint et OneDrive entreprise, contactez [Spock@microsoft.com](mailto:spock@microsoft.com). Pour Exchange Online et Skype entreprise, contactez [exock@microsoft.com](mailto:exock@microsoft.com). Incluez les éléments suivants dans votre courrier :

   **Objet**: clé client pour \<*Your tenant's fully-qualified domain name*\>

   **Body**: ID d’abonnement pour lesquels vous souhaitez que la période de rétention obligatoire soit finalisée.
   La sortie de Get-AzProviderFeature pour chaque abonnement.

   Le contrat de niveau de service (SLA) pour la fin de ce processus est de cinq jours ouvrés une fois que Microsoft a été informé (et vérifié) que vous avez enregistré vos abonnements afin d’utiliser une période de rétention obligatoire.

4. Une fois que vous recevez une notification de Microsoft que l’enregistrement est terminé, vérifiez l’état de votre inscription en exécutant la commande Get-AzProviderFeature comme suit. Si elle est vérifiée, la commande Get-AzProviderFeature renvoie la valeur **inscrite** pour la propriété de l’état de l' **inscription** . Effectuez cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

5. Pour terminer le processus, exécutez la commande Register-AzResourceProvider. Effectuez cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Créer un coffre-fort de clés Azure pour chaque abonnement

Les étapes à suivre pour créer un coffre-fort de clés sont documentées dans [Getting Started with Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/), qui vous guide tout au long de l’installation et du lancement d’Azure PowerShell, de la connexion à votre abonnement Azure, de la création d’un groupe de ressources et de la création d’un coffre-fort de clés dans ce groupe de ressources.
  
Lorsque vous créez un coffre-fort de clés, vous devez choisir un SKU : standard ou Premium. La référence SKU standard permet de protéger les clés du coffre-fort de clés Azure avec le logiciel : il n’existe pas de protection de clé HSM (Hardware Security Module) et la référence Premium permet d’utiliser des HSM pour la protection des clés de coffre-fort. La clé client accepte les coffres clés qui utilisent l’un des deux SKU, bien que Microsoft recommande vivement d’utiliser uniquement le SKU Premium. Le coût des opérations avec des clés de l’un des deux types est le même, de sorte que la seule différence de coût est le coût par mois pour chaque clé protégée par HSM. Pour plus d’informations, consultez la rubrique [prix clé du coffre](https://azure.microsoft.com/pricing/details/key-vault/) .
  
> [!IMPORTANT]
> Utilisez les coffres-forts de clés SKU Premium et les clés protégées par HSM pour les données de production, et utilisez uniquement les clés et coffres-forts de clé SKU standard à des fins de test et de validation.
  
Pour chaque service Microsoft 365 avec lequel vous utiliserez la clé client, créez un coffre-fort de clés dans chacun des deux abonnements Azure que vous avez créés. Par exemple, pour Exchange Online et Skype entreprise uniquement ou SharePoint Online et OneDrive entreprise uniquement, vous ne devez créer qu’une seule paire de coffres-forts. Pour activer la clé client pour Exchange Online et SharePoint Online, vous devez créer deux paires de coffres-forts clés.
  
Utilisez une convention d’affectation de noms pour les coffres-forts de clés reflétant l’utilisation prévue de la stratégie de chiffrement de données avec laquelle vous allez associer les coffres-forts. Consultez la section Méthodes conseillées ci-dessous pour connaître les recommandations de convention d’affectation de noms.
  
Créez un ensemble distinct de coffres couplés pour chaque stratégie de chiffrement de données. Pour Exchange Online, l’étendue d’une stratégie de chiffrement de données est choisie par vous lorsque vous affectez la stratégie à la boîte aux lettres. Une boîte aux lettres ne peut avoir qu’une seule stratégie affectée, et vous pouvez créer jusqu’à 50 stratégies. Pour SharePoint Online, l’étendue d’une stratégie est l’ensemble des données d’une organisation se trouvant dans un emplacement géographique ou dans une _région_géographique.

La création de coffre-fort de clés nécessite également la création de groupes de ressources Azure, car les coffres clés nécessitent une capacité de stockage (bien que très petite) et la journalisation de coffre de clés, si elle est activée, génère également des données stockées. Pour une meilleure pratique, Microsoft recommande d’utiliser des administrateurs distincts pour gérer chaque groupe de ressources, avec l’administration alignée sur l’ensemble des administrateurs qui géreront toutes les ressources liées à la clé client correspondante.
  
> [!IMPORTANT]
> Pour optimiser la disponibilité, vos coffres-forts principaux doivent se trouver dans des régions proches de votre service Microsoft 365. Par exemple, si votre organisation Exchange Online est en Amérique du Nord, placez vos coffres clés en Amérique du Nord. Si votre organisation Exchange Online est en Europe, placez vos coffres clés en Europe.<br/>Utilisez un préfixe commun pour les coffres-forts de clés, et incluez une abréviation de l’utilisation et de l’étendue du coffre-fort de clés et des clés (par exemple, pour le service Contoso SharePoint où les coffres seront situés en Amérique du Nord, contoso-O365SP-NA-VaultA1 et contoso-O365SP-NA-VaultA2. Les noms de coffre-fort sont des chaînes uniques au sein d’Azure, de sorte que vous devrez peut-être essayer des variantes des noms souhaités au cas où les noms souhaités seraient déjà réclamés par d’autres clients Azure. Depuis juillet 2017, les noms de coffre-fort ne peuvent pas être modifiés, c’est pourquoi il est recommandé de disposer d’un plan écrit pour la configuration et d’utiliser une deuxième personne pour vérifier que le plan est exécuté correctement.<br/>Si possible, créez vos coffres dans des régions non couplées. Les régions Azure couplées fournissent une haute disponibilité entre les domaines ayant échoué. Par conséquent, les paires régionales peuvent être considérées comme la région de sauvegarde de chacune d’elles. Cela signifie qu’une ressource Azure placée dans une région bénéficie automatiquement de la tolérance de panne par le biais de la région couplée. Pour cette raison, le choix des régions pour deux coffres utilisés dans une stratégie de chiffrement de données dans laquelle les régions sont couplées signifie que seul un total de deux régions de disponibilité est en cours d’utilisation. La plupart des régions géographiques n’ont que deux régions, de sorte qu’il n’est pas encore possible de sélectionner des régions non couplées. Dans la mesure du possible, choisissez deux régions non couplées pour les deux coffres utilisés avec une stratégie de chiffrement de données. Cette opération bénéficie d’un total de quatre régions de disponibilité. Pour plus d’informations, consultez la rubrique [services de continuité d’activité et de récupération d’urgence (BCDR) : régions couplées Azure](https://docs.microsoft.com/azure/best-practices-availability-paired-regions) pour obtenir la liste actuelle des paires régionales.
  
### <a name="assign-permissions-to-each-key-vault"></a>Attribuer des autorisations à chaque coffre-fort de clés

Pour chaque coffre-fort de clés, vous devez définir trois ensembles distincts d’autorisations pour la clé client, en fonction de votre implémentation. Par exemple, vous devez définir un ensemble d’autorisations pour chacun des éléments suivants :
  
- **Administrateurs de coffre-fort principal** qui effectueront la gestion quotidienne de votre coffre-fort pour votre organisation. Ces tâches incluent Backup, Create, Get, Import, List et Restore.

  > [!IMPORTANT]
  > Le jeu d’autorisations affectées aux administrateurs de coffre-fort n’inclut pas l’autorisation de suppression de clés. Cette procédure est intentionnelle et pratique importante. La suppression de clés de chiffrement n’est généralement pas effectuée, car cette opération détruit définitivement les données. Nous vous recommandons de ne pas accorder cette autorisation aux administrateurs de coffre-fort par défaut. Au lieu de cela, réservez ceci pour les contributeurs de coffre-fort principal et ne l’attribuez à un administrateur de manière courte qu’une fois qu’une bonne compréhension des conséquences est comprise.
  
  Pour attribuer ces autorisations à un utilisateur de votre organisation, connectez-vous à votre abonnement Azure avec Azure PowerShell. Pour obtenir des instructions, consultez la rubrique [se connecter avec Azure PowerShell](https://docs.microsoft.com/powershell/azure/authenticate-azureps).

- Exécutez la cmdlet Set-AzKeyVaultAccessPolicy pour attribuer les autorisations nécessaires.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Par exemple :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- Les **contributeurs de coffre-fort de clé** qui peuvent modifier les autorisations sur le coffre-fort des clés Azure. Vous devrez modifier ces autorisations lorsque les employés quittent ou rejoignent votre équipe, ou dans la situation extrêmement rare que les administrateurs clés de coffre-fort ont besoin de l’autorisation de supprimer ou de restaurer une clé. Cet ensemble de contributeurs de coffre-fort doit recevoir le rôle de **contributeur** sur votre coffre-fort de clés. Vous pouvez attribuer ce rôle à l’aide d’Azure Resource Manager. Pour obtenir la procédure détaillée, consultez [la rubrique utiliser le contrôle d’accès basé sur un rôle pour gérer l’accès à vos ressources d’abonnement Azure](https://docs.microsoft.com/azure/active-directory/role-based-access-control-configure). L’administrateur qui crée un abonnement bénéficie implicitement de cet accès, ainsi que de la possibilité d’affecter d’autres administrateurs au rôle contributeur.

- Si vous envisagez d’utiliser la clé client avec Exchange Online et Skype entreprise, vous devez accorder à Microsoft 365 l’autorisation d’utiliser le coffre-fort de clés pour Exchange Online et Skype entreprise. De même, si vous avez l’intention d’utiliser la clé client avec SharePoint Online et OneDrive entreprise, vous devez ajouter des autorisations pour le Microsoft 365 afin d’utiliser le coffre-fort de clés pour SharePoint Online et OneDrive entreprise. Pour accorder l’autorisation à Microsoft 365, exécutez la cmdlet **Set-AzKeyVaultAccessPolicy** à l’aide de la syntaxe suivante : 

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Où :

    - *Vault Name* est le nom du coffre-fort de clés que vous avez créé.

    - Pour Exchange Online et Skype entreprise, remplacez  *Office 365 AppID* par `00000002-0000-0ff1-ce00-000000000000`

    - Pour les fichiers SharePoint Online, OneDrive entreprise et Teams, remplacez  *Office 365 AppID* par `00000003-0000-0ff1-ce00-000000000000`

  Exemple : définition des autorisations pour Exchange Online et Skype entreprise :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Exemple : définition des autorisations pour SharePoint Online, OneDrive entreprise et les fichiers teams :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

### <a name="enable-and-then-confirm-soft-delete-on-your-key-vaults"></a>Activer, puis confirmer la suppression logicielle de vos coffres-forts principaux

Lorsque vous pouvez rapidement récupérer vos clés, il est moins probable que vous rencontriez une panne de service étendue en raison de la suppression accidentelle ou malveillante de clés. Vous devez activer cette configuration, appelée suppression récupérable, avant de pouvoir utiliser vos clés avec la clé client. L’activation de la suppression douce vous permet de récupérer des clés ou des coffres dans les 90 jours suivant la suppression sans avoir à les restaurer à partir d’une sauvegarde.
  
Pour activer la suppression logicielle sur vos coffres-forts principaux, procédez comme suit :
  
1. Connectez-vous à votre abonnement Azure avec Windows PowerShell. Pour obtenir des instructions, consultez la rubrique [se connecter avec Azure PowerShell](https://docs.microsoft.com/powershell/azure/authenticate-azureps).

2. Exécutez la cmdlet [Get-AzKeyVault](https://docs.microsoft.com/powershell/module/az.keyvault/get-azkeyvault) . Dans cet exemple, le *nom de coffre-fort* est le nom du coffre-fort de clés pour lequel vous activez la suppression douce :

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. Vérifiez que la suppression logicielle est configurée pour le coffre-fort de clés en exécutant la cmdlet **Get-AzKeyVault** . Si la suppression logicielle est correctement configurée pour le coffre-fort de clés, la propriété de _suppression logicielle activée_ renvoie la valeur **true**:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>Ajouter une clé à chaque coffre-fort de clés en créant ou en important une clé

Il existe deux façons d’ajouter des clés à un coffre-fort de clés Azure ; vous pouvez créer une clé directement dans le coffre-fort de clés ou importer une clé. La création d’une clé directement dans le coffre-fort est la méthode moins compliquée, tandis que l’importation d’une clé fournit un contrôle total sur la génération de la clé.
  
Pour créer une clé directement dans votre coffre-fort de clés, exécutez la cmdlet [Add-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/add-azkeyvaultkey) comme suit :
  
```powershell
Add-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Destination <HSM|Software> -KeyOps wrapKey,unwrapKey
```

Où :

- *Vault Name* est le nom du coffre-fort de clés dans lequel vous souhaitez créer la clé.

- *nom* de la clé est le nom que vous souhaitez donner à la nouvelle clé.

  > [!TIP]
  > Clés de nom à l’aide d’une convention d’affectation de noms similaire à celle décrite ci-dessus pour les coffres clés. De cette manière, dans les outils qui affichent uniquement le nom de la clé, la chaîne est auto-descriptive.
  
- Si vous avez l’intention de protéger la clé avec un HSM, vérifiez que vous spécifiez **HSM** comme valeur du paramètre _destination_ , sinon, spécifiez **Software**.

Par exemple :
  
```powershell
Add-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -Name Contoso-O365EX-NA-VaultA1-Key001 -Destination Software -KeyOps wrapKey,unwrapKey
```

Pour importer directement une clé dans votre coffre-fort de clés, vous devez disposer d’un module de sécurité matérielle nCipher nShield.
  
Certaines organisations préfèrent établir la provenance de leurs clés, puis cette méthode fournit également les éléments suivants :
  
- L’ensemble d’outils utilisé pour l’importation inclut l’attestation de nCipher que la clé d’échange de clés (KEK) utilisée pour chiffrer la clé que vous générez n’est pas exportable et est générée à l’intérieur d’un HSM authentique fabriqué par nCipher.

- L’ensemble d’outils inclut l’attestation de nCipher que le World Key Vault Security a été également généré sur un autohsm fabriqué par nCipher. Cette attestation prouve que Microsoft utilise également du matériel nCipher authentique.

Vérifiez auprès de votre groupe de sécurité si les attestations ci-dessus sont requises. Pour obtenir la procédure détaillée de création d’une clé locale et de son importation dans votre coffre-fort de clés, consultez [la rubrique How to Generate and Transfer My protected Keys for Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/). Utilisez les instructions Azure pour créer une clé dans chaque coffre-fort de clés.
  
### <a name="check-the-recovery-level-of-your-keys"></a>Vérifier le niveau de récupération de vos clés

Microsoft 365 nécessite que le abonnement Azure Key Vault soit défini sur do not Cancel et que les clés utilisées par la clé client aient activé la suppression douce. Vous pouvez vérifier cela en examinant le niveau de récupération de vos clés.
  
Pour vérifier le niveau de récupération d’une clé, dans Azure PowerShell, exécutez la cmdlet Get-AzKeyVaultKey comme suit :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

Si la propriété de _niveau de récupération_ renvoie une valeur autre que **récupérable + ProtectedSubscription**, vous devez consulter cette rubrique et vous assurer que vous avez suivi toutes les étapes pour placer l’abonnement dans la liste ne pas annuler et que la suppression logicielle est activée sur chaque coffre-fort de clés.
  
### <a name="back-up-azure-key-vault"></a>Sauvegarder le coffre de clés Azure

Immédiatement après la création ou la modification d’une clé, effectuez une sauvegarde et stockez des copies de la sauvegarde, en ligne et hors connexion. Les copies hors connexion ne doivent pas être connectées à un réseau, par exemple dans une installation de stockage sécurisé physique ou commerciale. Au moins une copie de la sauvegarde doit être stockée à un emplacement accessible en cas de sinistre. Les objets BLOB de sauvegarde constituent le seul moyen de restaurer le matériel de clé si une clé de coffre-fort de clé est détruite définitivement ou s’il est inopérable. Les clés externes au coffre-fort Azure et qui ont été importées vers le coffre-fort Azure ne sont pas qualifiées de sauvegarde car les métadonnées nécessaires à l’utilisation de la clé par le client n’existent pas avec la clé externe. Seule une sauvegarde effectuée à partir du coffre-fort de clés Azure peut être utilisée pour les opérations de restauration avec la clé client. Par conséquent, il est essentiel qu’une sauvegarde du coffre de clés Azure soit effectuée une fois qu’une clé est chargée ou créée.
  
Pour créer une sauvegarde d’une clé Azure Key Vault, exécutez la cmdlet [Backup-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/backup-azkeyvaultkey) comme suit :

```powershell
Backup-AzKeyVaultKey -VaultName <vault name> -Name <key name>
-OutputFile <filename.backup>
```

Assurez-vous que votre fichier de sortie utilise le suffixe `.backup` .
  
Le fichier de sortie résultant de cette cmdlet est chiffré et ne peut pas être utilisé en dehors du coffre-fort de clés Azure. La sauvegarde ne peut être restaurée qu’à partir de l’abonnement Azure à partir duquel la sauvegarde a été effectuée.
  
> [!TIP]
> Pour le fichier de sortie, choisissez une combinaison de votre nom de coffre-fort et de votre nom de clé. Cela fera en sorte que le nom de fichier soit auto-descriptif. Elle garantit également que les noms de fichier de sauvegarde n’entrent pas en conflit.
  
Par exemple :
  
```powershell
Backup-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -Name Contoso-O365EX-NA-VaultA1-Key001 -OutputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

### <a name="validate-azure-key-vault-configuration-settings"></a>Valider les paramètres de configuration de coffre-fort de clés Azure

Effectuer la validation avant d’utiliser des clés dans une DEP est facultatif, mais fortement recommandé. En particulier, si vous utilisez les étapes pour configurer vos clés et coffres-forts autres que ceux décrits dans cette rubrique, vous devez valider l’intégrité de vos ressources Azure Key Vault avant de configurer la clé client.
  
Pour vérifier que les opérations Get, wrapKey et unwrapKey sont activées sur vos clés, procédez comme suit :
  
Exécutez la cmdlet [Get-AzKeyVault](https://docs.microsoft.com/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
```powershell
Get-AzKeyVault -VaultName <vault name>
```

Dans la sortie, recherchez la stratégie d’accès et l’identité Exchange Online (GUID) ou l’identité SharePoint Online (GUID), selon le cas. Les trois autorisations ci-dessus doivent être affichées sous autorisations sur clés.
  
Si la configuration de la stratégie d’accès est incorrecte, exécutez la cmdlet Set-AzKeyVaultAccessPolicy comme suit :
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
```

Par exemple, pour Exchange Online et Skype entreprise :
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
```

Par exemple, pour SharePoint Online et OneDrive entreprise :
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365SP-NA-VaultA1
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
```

Pour vérifier qu’une date d’expiration n’est pas définie pour vos clés, exécutez la cmdlet [Get-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

Une clé expirée ne peut pas être utilisée par la clé client et les opérations tentées avec une clé expirée échoueront, ce qui peut entraîner une panne de service. Il est vivement recommandé que les clés utilisées avec la clé client n’aient pas de date d’expiration. Une date d’expiration, une fois définie, ne peut pas être supprimée, mais peut être remplacée par une date différente. Si une clé doit être utilisée avec une date d’expiration définie, modifiez la valeur d’expiration sur 12/31/9999. Les clés dont la date d’expiration est définie sur une date autre que 12/31/9999 ne passent pas la validation Microsoft 365.
  
Pour modifier une date d’expiration qui a été définie sur une valeur autre que 12/31/9999, exécutez la cmdlet [Update-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/update-azkeyvaultkey) comme suit :
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Ne définissez pas de date d’expiration sur les clés de chiffrement que vous utilisez avec la clé client.
  
### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Obtenir l’URI de chaque clé Azure Key Vault

Une fois que vous avez effectué toutes les étapes dans Azure pour configurer votre coffre-fort de clés et ajouté vos clés, exécutez la commande suivante pour obtenir l’URI de la clé dans chaque coffre-fort de clés. Vous devrez utiliser ces URI lorsque vous créerez et affecterez chaque DEP plus tard, donc Enregistrez ces informations dans un endroit sûr. N’oubliez pas d’exécuter cette commande une fois pour chaque coffre-fort de clés.
  
Dans Azure PowerShell :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="office-365-setting-up-customer-key-for-exchange-online-and-skype-for-business"></a>Office 365 : configuration de la clé client pour Exchange Online et Skype entreprise

Avant de commencer, vérifiez que vous avez terminé les tâches requises pour configurer Azure Key Vault. Pour plus d’informations, consultez la rubrique [tâches terminées dans Azure Key Vault et Microsoft FastTrack pour la clé client](#complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key) .
  
Pour configurer la clé client pour Exchange Online et Skype entreprise, vous devez effectuer ces étapes en vous connectant à distance à Exchange Online à l’aide de Windows PowerShell.
  
### <a name="create-a-data-encryption-policy-dep-for-use-with-exchange-online-and-skype-for-business"></a>Créer une stratégie de chiffrement de données (DEP) à utiliser avec Exchange Online et Skype entreprise

Une DEP est associée à un ensemble de clés stockées dans Azure Key Vault. Vous affectez une DEP à une boîte aux lettres dans Microsoft 365. Microsoft 365 utilise ensuite les clés identifiées dans la stratégie pour chiffrer la boîte aux lettres. Pour créer la DEP, vous avez besoin des URI de coffre-fort que vous avez obtenus précédemment. Consultez [la rubrique obtenir l’URI pour chaque clé Azure Key Vault](#obtain-the-uri-for-each-azure-key-vault-key) pour obtenir des instructions.
  
Pensez! Lorsque vous créez une DEP, vous spécifiez deux clés qui résident dans deux coffres de clés Azure différents. Assurez-vous que ces clés se situent dans deux régions Azure distinctes pour garantir la redondance géographique.
  
Pour créer la DEP, procédez comme suit :
  
1. Sur votre ordinateur local, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

2. Pour créer une DEP, utilisez la cmdlet New-DataEncryptionPolicy en tapant la commande suivante.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Où :

   - *PolicyName* est le nom que vous souhaitez utiliser pour la stratégie. Les noms ne peuvent pas contenir d’espaces. Par exemple, USA_mailboxes.

   - La description de la *stratégie* est une description conviviale de la stratégie qui vous permettra de vous souvenir de ce à quoi la stratégie est destinée. Vous pouvez inclure des espaces dans la description. Par exemple, « clé racine pour les boîtes aux lettres dans les États-Unis et ses territoires ».

   - *KeyVaultURI1* est l’URI de la première clé de la stratégie. Par exemple, <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* est l’URI de la deuxième clé de la stratégie. Par exemple, <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. Séparez les deux URI par une virgule et un espace.

   Exemple :
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01, https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-DataEncryptionPolicy](https://docs.microsoft.com/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Affecter une DEP à une boîte aux lettres

Affecter la DEP à une boîte aux lettres à l’aide de la cmdlet Set-Mailbox. Une fois que vous avez affecté la stratégie, Microsoft 365 peut chiffrer la boîte aux lettres à l’aide de la clé désignée dans la DEP.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

Où *MailboxIdParameter* spécifie une boîte aux lettres. Pour plus d’informations sur la cmdlet Set-Mailbox, consultez la rubrique [Set-Mailbox](https://docs.microsoft.com/powershell/module/exchange/set-mailbox).

Pour les [boîtes aux lettres locales utilisant Outlook pour iOS et Android avec l’authentification moderne hybride](https://docs.microsoft.com/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth), les données de la boîte aux lettres locale qui est synchronisée dans votre client Exchange Online peuvent avoir une DEP affectée à l’aide de la cmdlet Set-MailUser.

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Où *MailUserIdParameter* spécifie un utilisateur de messagerie (également appelé utilisateur à extension messagerie). Pour plus d’informations sur la cmdlet Set-MailUser, voir [Set-MailUser](https://docs.microsoft.com/powershell/module/exchange/set-mailuser).
  
### <a name="validate-mailbox-encryption"></a>Valider le chiffrement de boîtes aux lettres

Le chiffrement d’une boîte aux lettres peut prendre du temps. Pour une attribution de stratégie pour la première fois, la boîte aux lettres doit également être complètement déplacée d’une base de données à une autre pour que le service puisse chiffrer la boîte aux lettres. Nous vous recommandons d’attendre 72 heures avant de valider le chiffrement après avoir modifié une DEP ou la première fois que vous affectez une DEP à une boîte aux lettres.
  
Utilisez la cmdlet Get-MailboxStatistics pour déterminer si une boîte aux lettres est chiffrée.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

La propriété IsEncrypted renvoie la valeur **true** si la boîte aux lettres est chiffrée et la valeur **false** si la boîte aux lettres n’est pas chiffrée.

Le temps nécessaire au déplacement des boîtes aux lettres dépend du nombre de boîtes aux lettres auxquelles vous affectez une DEP pour la première fois, ainsi que de la taille des boîtes aux lettres. Si les boîtes aux lettres n’ont pas été chiffrées après une semaine à partir du moment où vous avez attribué la DEP, contactez Microsoft.

## <a name="office-365-setting-up-customer-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Office 365 : configuration de la clé client pour les fichiers SharePoint Online, OneDrive entreprise et Teams

Avant de commencer, vérifiez que vous avez terminé les tâches requises pour configurer Azure Key Vault. Pour plus d’informations, consultez la rubrique [tâches terminées dans Azure Key Vault et Microsoft FastTrack pour la clé client](#complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key) .
  
Pour configurer la clé client pour SharePoint Online, OneDrive entreprise et les fichiers Teams, vous devez effectuer ces étapes en vous connectant à distance à SharePoint Online avec Windows PowerShell.
  
### <a name="create-a-data-encryption-policy-dep-for-each-sharepoint-online-and-onedrive-for-business-geo"></a>Créer une stratégie de chiffrement de données (DEP) pour chaque région de SharePoint Online et OneDrive entreprise

Vous associez une DEP à un ensemble de clés stockées dans le coffre-fort des clés Azure. Vous appliquez une DEP à toutes vos données dans un emplacement géographique, également appelé géo. Si vous utilisez la fonctionnalité multigéographique d’Office 365, vous pouvez créer une DEP par zone géographique avec la capacité d’utiliser différentes clés par zone géographique. Si vous n’utilisez pas de multi-géo, vous pouvez créer une DEP dans votre organisation pour l’utiliser avec les fichiers SharePoint Online, OneDrive entreprise et Teams. Microsoft 365 utilise les clés identifiées dans la DEP pour chiffrer vos données dans cette région. Pour créer la DEP, vous avez besoin des URI de coffre-fort que vous avez obtenus précédemment. Consultez [la rubrique obtenir l’URI pour chaque clé Azure Key Vault](#obtain-the-uri-for-each-azure-key-vault-key) pour obtenir des instructions.
  
Pensez! Lorsque vous créez une DEP, vous spécifiez deux clés qui résident dans deux coffres de clés Azure différents. Assurez-vous que ces clés se situent dans deux régions Azure distinctes pour garantir la redondance géographique.
  
Pour créer une DEP, vous devez vous connecter à distance à SharePoint Online à l’aide de Windows PowerShell.
  
1. Sur votre ordinateur local, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [Connectez-vous à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

2. Dans Microsoft SharePoint Online Management Shell, exécutez la cmdlet Register-SPODataEncryptionPolicy comme suit :

   ```powershell
   Register-SPODataEncryptionPolicy -Identity <SPOAdminSiteUrl> -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Lorsque vous enregistrez la DEP, le chiffrement commence sur les données de la région géographique. Cela peut prendre un certain temps.

### <a name="validate-file-encryption"></a>Valider le chiffrement de fichiers

 Pour valider le chiffrement des fichiers SharePoint Online, OneDrive entreprise et Teams, [Connectez-vous à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps), puis utilisez la cmdlet Get-SPODataEncryptionPolicy pour vérifier l’état de votre client. La propriété _State_ renvoie la valeur **Registered** si le chiffrement de clé du client est activé et si tous les fichiers de tous les sites ont été chiffrés. Si le chiffrement est toujours en cours, cette applet de commande fournit des informations sur le pourcentage de sites terminé.

## <a name="related-articles"></a>Articles connexes

- [Chiffrement de service avec clé client](customer-key-overview.md)

- [Gérer la clé client](customer-key-manage.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Chiffrement de service](office-365-service-encryption.md)
