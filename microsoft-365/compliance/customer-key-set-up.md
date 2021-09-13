---
title: Configurer la clé client
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Découvrez comment configurer la clé client pour Microsoft 365.
ms.openlocfilehash: e187c01a355cc9b926e892cb3326b5a527c714a4
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59203382"
---
# <a name="set-up-customer-key"></a>Configurer la clé client

Avec la clé client, vous contrôlez les clés de chiffrement de votre organisation, puis configurez les Microsoft 365 pour les utiliser pour chiffrer vos données au repos dans les centres de données de Microsoft. En d’autres termes, la clé client permet aux clients d’ajouter une couche de chiffrement qui leur appartient, avec leurs clés.

Configurer Azure avant de pouvoir utiliser la clé client pour Office 365. Cet article décrit les étapes à suivre pour créer et configurer les ressources Azure requises, puis fournit les étapes de configuration de la clé client dans Office 365. Après avoir installé Azure, vous déterminez la stratégie et, par conséquent, les clés à affecter pour chiffrer les données entre différentes charges Microsoft 365 charges de travail au sein de votre organisation. Pour plus d’informations sur la clé client ou pour obtenir une vue d’ensemble générale, voir Chiffrement de service avec clé [client dans Office 365](customer-key-overview.md).
  
> [!IMPORTANT]
> Nous vous recommandons vivement de suivre les meilleures pratiques de cet article. Ces éléments sont appelés **CONSEIL et** **IMPORTANT**. La clé client vous permet de contrôler les clés de chiffrement racine dont l’étendue peut être aussi importante que l’ensemble de votre organisation. Cela signifie que les erreurs réalisées avec ces clés peuvent avoir un impact important et entraîner des interruptions de service ou une perte irrévocable de vos données.
  
## <a name="before-you-set-up-customer-key"></a>Avant de configurer la clé client

Avant de commencer, assurez-vous que vous avez les abonnements et licences Azure appropriés pour votre organisation. Utilisez des abonnements Azure payants à l’aide d’Accord Entreprise ou d’un fournisseur de services Cloud. Les paiements par carte de crédit ne sont pas acceptés. Approuver et configurer les besoins de compte pour la facturation. Les abonnements gratuits, d’essai, de soutien, d’abonnement MSDN et de support hérité ne sont pas éligibles.

Office 365 E5, Microsoft 365 E5, Microsoft 365 E5 Conformité et Microsoft 365 E5 SSK Protection des informations & gouvernance offrent la clé client. Conformité avancée Office 365 La référence (SKU) n’est plus disponible pour l’utilisation de nouvelles licences. Les licences Conformité avancée Office 365 existantes continueront d’être prise en charge.

Pour comprendre les concepts et procédures décrits dans cet article, examinez la documentation [relative au coffre de clés Azure.](/azure/key-vault/) Familiarisez-vous également avec les termes utilisés dans Azure, par exemple, [client Azure AD.](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant)
  
Si vous avez besoin d’une assistance supplémentaire au-delà de la documentation, contactez Microsoft Consulting Services (MCS), Premier Field Engineering (PFE) ou un partenaire Microsoft pour obtenir de l’aide. Pour fournir des commentaires sur la clé client, y compris la documentation, envoyez vos idées, suggestions et perspectives à customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Vue d’ensemble des étapes de la mise en place de la clé client

Pour configurer la clé client, complétez ces tâches dans l’ordre répertorié. Le reste de cet article fournit des instructions détaillées pour chaque tâche ou fournit des liens vers des informations supplémentaires pour chaque étape du processus.
  
**Dans Azure et Microsoft, FastTrack :**
  
Vous effectuerez la plupart de ces tâches en vous connectant à distance à Azure PowerShell. Pour obtenir de meilleurs résultats, utilisez la version 4.4.0 ou Azure PowerShell.
  
- [Créer deux nouveaux abonnements Azure](#create-two-new-azure-subscriptions)

- [Envoyer une demande d’activation de la clé client pour Office 365](#submit-a-request-to-activate-customer-key-for-office-365)
 
- [Inscrire des abonnements Azure pour utiliser une période de rétention obligatoire](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  L’inscription peut prendre entre 1 et 5 jours ou moins.

- [Créer un coffre de clés Azure premium dans chaque abonnement](#create-a-premium-azure-key-vault-in-each-subscription)

- [Attribuer des autorisations à chaque coffre de clés](#assign-permissions-to-each-key-vault)

- [Assurez-vous que la suppression possible est activée sur vos coffres de clés](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [Ajouter une clé à chaque coffre de clés en créant ou en important une clé](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Vérifier le niveau de récupération de vos clés](#check-the-recovery-level-of-your-keys)

- [Back up Azure Key Vault](#back-up-azure-key-vault)

- [Valider les paramètres de configuration d’Azure Key Vault](#validate-azure-key-vault-configuration-settings)

- [Obtenir l’URI de chaque clé Azure Key Vault](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Effectuer des tâches dans Azure Key Vault et Microsoft FastTrack for Customer Key

Effectuer ces tâches dans Azure Key Vault. Vous devez effectuer ces étapes pour tous les DEP que vous utilisez avec la clé client.
  
### <a name="create-two-new-azure-subscriptions"></a>Créer deux nouveaux abonnements Azure

La clé client nécessite deux abonnements Azure. En tant que meilleure pratique, Microsoft vous recommande de créer de nouveaux abonnements Azure à utiliser avec la clé client. Les clés Azure Key Vault peuvent uniquement être autorisées pour les applications dans le même client Azure Active Directory (Microsoft Azure Active Directory), vous devez créer les nouveaux abonnements à l’aide du même client Azure AD que celui utilisé avec votre organisation où les dep seront affectés. Par exemple, à l’aide de votre compte professionnel ou scolaire qui dispose de privilèges d’administrateur général dans votre organisation. Pour obtenir la procédure détaillée, voir [S’inscrire à Azure en tant qu’organisation.](/azure/active-directory/fundamentals/sign-up-organization)
  
> [!IMPORTANT]
> La clé client nécessite deux clés pour chaque stratégie de chiffrement de données (DEP). Pour ce faire, vous devez créer deux abonnements Azure. En tant que meilleure pratique, Microsoft recommande que des membres distincts de votre organisation configurent une clé dans chaque abonnement. Vous devez uniquement utiliser ces abonnements Azure pour administrer les clés de chiffrement Office 365. Cela protège votre organisation au cas où l’un de vos opérateurs supprime accidentellement, intentionnellement ou malveillantment les clés dont ils sont responsables, ou en cas de mauvaise gestion.

Il n’existe aucune limite pratique au nombre d’abonnements Azure que vous pouvez créer pour votre organisation. Le fait de suivre ces meilleures pratiques permet de minimiser l’impact d’une erreur humaine tout en aidant à gérer les ressources utilisées par la clé client.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Envoyer une demande d’activation de la clé client pour Office 365

Une fois que vous avez créé les deux nouveaux abonnements Azure, vous devez envoyer la demande d’offre de clé client appropriée dans le portail [Microsoft FastTrack](https://fasttrack.microsoft.com/). Les sélections que vous faites dans le formulaire d’offre concernant les désignations autorisées au sein de votre organisation sont essentielles et nécessaires pour l’inscription de la clé client. Les responsables de ces rôles sélectionnés au sein de votre organisation garantissent l’authenticité de toute demande de révocation et de destruction de toutes les clés utilisées avec une stratégie de chiffrement de données de clé client. Vous devez faire cette étape une fois pour chaque type de dep de clé client que vous avez l’intention d’utiliser pour votre organisation.

**L FastTrack ne fournit pas d’assistance avec la clé client. Office 365 utilise simplement le portail FastTrack pour vous permettre de soumettre le formulaire et pour nous aider à suivre les offres pertinentes pour la clé client. Une fois que vous avez envoyé la demande FastTrack, demandez à l’équipe d’intégration de clé client correspondante de démarrer le processus d’intégration.**
  
Pour soumettre une offre d’activation de la clé client, effectuer les étapes suivantes :
  
1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous au portail [Microsoft FastTrack.](https://fasttrack.microsoft.com/)

2. Une fois que vous êtes connecté, sélectionnez le domaine approprié.

3. Pour le domaine sélectionné, choisissez Demander **des services** dans la barre de navigation supérieure et examinez la liste des offres disponibles.

4. Choisissez la carte d’informations pour l’offre qui vous concerne :

   - **Charges Microsoft 365 charges de travail multiples :** Choisissez **l’aide de la clé de chiffrement de demande** Microsoft 365'offre.

   - **Exchange Online et Skype Entreprise :** Choisissez **l’aide de la clé de chiffrement** de demande Exchange’offre.

   - **SharePoint en ligne, OneDrive et Teams fichiers :** Choisissez **l’aide de la** clé de chiffrement de demande SharePoint et OneDrive Entreprise’offre.

5. Une fois que vous avez examiné les détails de l’offre, choisissez **Continuer à l’étape 2**.

6. Remplissez tous les détails applicables et les informations demandées sur le formulaire d’offre. Accordez une attention particulière à vos sélections pour les responsables de votre organisation que vous souhaitez autoriser à approuver la destruction définitive et irréversible des clés de chiffrement et des données. Une fois que vous avez terminé le formulaire, choisissez **Envoyer.**

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Inscrire des abonnements Azure pour utiliser une période de rétention obligatoire

La perte temporaire ou permanente des clés de chiffrement racine peut perturber ou même catastrophique le fonctionnement du service et entraîner la perte de données. Pour cette raison, les ressources utilisées avec la clé client nécessitent une protection forte. Toutes les ressources Azure utilisées avec la clé client offrent des mécanismes de protection au-delà de la configuration par défaut. Vous pouvez baliser ou inscrire des abonnements Azure pour une *période de rétention obligatoire.* Une période de rétention obligatoire empêche l’annulation immédiate et irrévocable de votre abonnement Azure. Les étapes requises pour inscrire des abonnements Azure pour une période de rétention obligatoire nécessitent une collaboration avec l Microsoft 365 de rétention. Ce processus peut prendre entre un et cinq jours ou moins. Auparavant, la période de rétention obligatoire était parfois appelée « Ne pas annuler ».
  
Avant de contacter l’équipe Microsoft 365, vous devez suivre les étapes suivantes pour chaque abonnement Azure que vous utilisez avec la clé client. Assurez-vous que le module [Azure PowerShell Az](/powershell/azure/new-azureps-module-az) est installé avant de commencer.
  
1. Connectez-vous avec Azure PowerShell. Pour obtenir des instructions, [voir Se Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Exécutez la cmdlet Register-AzProviderFeature pour inscrire vos abonnements afin d’utiliser une période de rétention obligatoire. Effectuer cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

3. Contactez Microsoft pour terminer le processus.

   - Pour activer la clé client pour l’affectation de deP à des boîtes aux lettres Exchange Online données individuelles, contactez [exock@microsoft.com](mailto:exock@microsoft.com).

   - Pour permettre à la clé client d’affecter des dep pour chiffrer le contenu SharePoint Online et OneDrive Entreprise (y compris les fichiers Teams) pour tous les utilisateurs du client, contactez [spock@microsoft.com](mailto:spock@microsoft.com).

   - Pour permettre à la clé client d’affecter des PED pour chiffrer le contenu sur plusieurs charges de travail Microsoft 365 (Exchange Online, Teams, MIP EDM) pour tous les utilisateurs du client, contactez [m365-ck@service.microsoft.com](mailto:m365-ck@service.microsoft.com).

- Incluez les informations suivantes dans votre courrier électronique :

   **Objet**: Clé client pour \<*Your tenant's fully qualified domain name*\>

   **Corps**: incluez les ID d’abonnement pour lesquels vous souhaitez terminer la période de rétention obligatoire et la sortie de Get-AzProviderFeature pour chaque abonnement.

   Le contrat de niveau de service (SLA) pour la réalisation de ce processus est de cinq jours ou jours, une fois que Microsoft a été averti (et vérifié) que vous avez inscrit vos abonnements pour utiliser une période de rétention obligatoire.

4. Une fois que vous recevez une notification de Microsoft vous avertissant que l’inscription est terminée, vérifiez l’état de votre inscription en exécutant la Get-AzProviderFeature suivante. Si elle est vérifiée, la commande Get-AzProviderFeature renvoie la valeur **Registered** pour la **propriété Registration State.** Terminez cette étape pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

5. Pour terminer le processus, exécutez la commande Register-AzResourceProvider commande. Terminez cette étape pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Créer un coffre de clés Azure premium dans chaque abonnement

Les étapes de création d’un coffre de clés sont documentées dans La mise en route [d’Azure Key Vault,](/azure/key-vault/general/overview)qui vous guide tout au long de l’installation et du lancement de Azure PowerShell, de la connexion à votre abonnement Azure, de la création d’un groupe de ressources et de la création d’un coffre de clés dans ce groupe de ressources.
  
Lorsque vous créez un coffre de clés, vous devez choisir une référence (SKU) : Standard ou Premium. La référence SKU standard permet de protéger les clés Azure Key Vault avec des logiciels (il n’existe pas de protection de clé de module de sécurité matérielle (HSM) ) et la référence Premium permet d’utiliser des HSM pour la protection des clés de coffre de clés. La clé client accepte les coffres de clés qui utilisent l’une ou l’autre des références( SKU), bien que Microsoft recommande vivement d’utiliser uniquement Premium référence (SKU). Le coût des opérations avec des clés de l’un ou l’autre type est le même, donc la seule différence de coût est le coût par mois pour chaque clé protégée par HSM. Pour plus [d’informations,](https://azure.microsoft.com/pricing/details/key-vault/) voir la tarification du coffre de clés.
  
> [!IMPORTANT]
> Utilisez les coffres de clés SKU Premium et les clés protégées par HSM pour les données de production, et utilisez uniquement les clés et coffres de clés SKU standard à des fins de test et de validation.
  
Pour chaque Microsoft 365 service avec lequel vous allez utiliser la clé client, créez un coffre de clés dans chacun des deux abonnements Azure que vous avez créés. Par exemple, pour permettre à la clé client d’utiliser des ppp pour les scénarios Exchange Online, SharePoint Online et multi-charges de travail, vous allez créer trois paires de coffres de clés.
  
Utilisez une convention d’attribution de noms pour les coffres de clés qui reflète l’utilisation prévue du dep auquel vous associerez les coffres. Consultez la section Recommandations ci-dessous pour obtenir des recommandations en matière de convention d’attribution de noms.
  
Créez un ensemble distinct de coffres couplés pour chaque stratégie de chiffrement de données. Par Exchange Online, l’étendue d’une stratégie de chiffrement de données est choisie par vous lorsque vous affectez la stratégie à la boîte aux lettres. Une boîte aux lettres ne peut avoir qu’une seule stratégie affectée et vous pouvez créer jusqu’à 50 stratégies. L’étendue d’une stratégie SharePoint Online inclut toutes les données au sein d’une organisation dans un emplacement géographique ou _géographique._ L’étendue d’une stratégie à charges de travail multiples inclut toutes les données sur les charges de travail prise en charge pour tous les utilisateurs.

La création de coffres de clés nécessite également la création de groupes de ressources Azure, dans la mesure où les coffres de clés nécessitent une capacité de stockage (mais de petite taille) et la journalisation du coffre de clés, si elle est activée, génère également des données stockées. En tant que meilleure pratique, Microsoft recommande d’utiliser des administrateurs distincts pour gérer chaque groupe de ressources, avec l’administration alignée sur l’ensemble d’administrateurs qui gérera toutes les ressources de clé client associées.
  
> [!IMPORTANT]
> Pour optimiser la disponibilité, placez vos coffres de clés dans des régions proches de votre service Microsoft 365 Par exemple, si votre organisation Exchange Online se trouve en Amérique du Nord, placez vos coffres de clés en Amérique du Nord. Si votre organisation Exchange Online se trouve en Europe, placez vos coffres de clés en Europe.
>
> Utilisez un préfixe commun pour les coffres de clés et incluez une abréviation de l’utilisation et de l’étendue du coffre de clés et des clés (par exemple, pour le service Contoso SharePoint où les coffres seront situés en Amérique du Nord, une paire de noms possible est Contoso-CK-SP-NA-VaultA1 et Contoso-CK-SP-NA-VaultA2. Les noms de coffre sont des chaînes globalement uniques dans Azure. Par conséquent, vous devrez peut-être essayer les variantes de vos noms souhaités si les noms souhaités sont déjà revendiqués par d’autres clients Azure. À compter de juillet 2017, les noms des coffres ne peuvent pas être modifiés. Il est donc préférable d’avoir un plan écrit pour l’installation et d’utiliser une deuxième personne pour vérifier que le plan est exécuté correctement.
>
> Si possible, créez vos coffres dans des régions non couplées. Les régions Azure couplées fournissent une haute disponibilité entre les domaines de défaillance de service. Par conséquent, les paires régionales peuvent être pensés comme la région de sauvegarde l’une de l’autre. Cela signifie qu’une ressource Azure placée dans une région gagne automatiquement en tolérance de pannes via la région couplée. Pour cette raison, le choix de régions pour deux coffres utilisés dans une stratégie de chiffrement de données dans laquelle les régions sont couplées signifie que seules deux régions de disponibilité sont en cours d’utilisation. La plupart des zones géographiques ne comptent que deux régions. Il n’est donc pas encore possible de sélectionner des régions non couplées. Si possible, choisissez deux régions non couplées pour les deux coffres utilisés avec une stratégie de chiffrement de données. Cela bénéficie d’un total de quatre régions de disponibilité. Pour plus d’informations, voir Continuité d’activité et récupération d’urgence [(BCDR)](/azure/best-practices-availability-paired-regions) : Azure Paired Regions pour obtenir la liste actuelle des paires régionales.
  
### <a name="assign-permissions-to-each-key-vault"></a>Attribuer des autorisations à chaque coffre de clés

Vous devez définir trois ensembles distincts d’autorisations pour chaque coffre de clés, en fonction de votre implémentation. Par exemple, vous devrez définir un ensemble d’autorisations pour chacune des autorisations suivantes :
  
- **Administrateurs de coffre de clés** qui font la gestion quotidienne de votre coffre de clés pour votre organisation. Ces tâches incluent la sauvegarde, la création, l’importation, la liste et la restauration.

  > [!IMPORTANT]
  > L’ensemble des autorisations attribuées aux administrateurs de coffre de clés n’inclut pas l’autorisation de supprimer des clés. Cette pratique est intentionnelle et importante. La suppression des clés de chiffrement n’est généralement pas effectuée, car cela détruit définitivement les données. En tant que meilleure pratique, n’accordez pas cette autorisation aux administrateurs de coffre de clés par défaut. Au lieu de cela, réservez-le aux contributeurs de coffre de clés et affectez-le uniquement à un administrateur à court terme une fois que vous comprenez bien les conséquences.
  
  Pour attribuer ces autorisations à un utilisateur de votre organisation, connectez-vous à votre abonnement Azure à l’Azure PowerShell. Pour obtenir des instructions, [voir Se Azure PowerShell](/powershell/azure/authenticate-azureps).

- Exécutez lSet-AzKeyVaultAccessPolicy cmdlet pour attribuer les autorisations nécessaires.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Par exemple :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **Contributeurs de coffre de clés** qui peuvent modifier les autorisations sur le coffre de clés Azure lui-même. Vous devez modifier ces autorisations lorsque les employés quittent ou rejoignent votre équipe. Dans les rares cas où les administrateurs de coffre de clés ont légitimement besoin d’autorisations pour supprimer ou restaurer une clé, vous devez également modifier les autorisations. Cet ensemble de contributeurs de coffre de clés doit avoir le rôle **Collaborateur** sur votre coffre de clés. Vous pouvez attribuer ce rôle à l’aide d’Azure Resource Manager. Pour obtenir la procédure détaillée, voir Utiliser Role-Based contrôle d’accès pour gérer [l’accès à vos ressources d’abonnement Azure.](/azure/active-directory/role-based-access-control-configure) L’administrateur qui crée un abonnement dispose de cet accès implicitement et de la possibilité d’affecter d’autres administrateurs au rôle collaborateur.

- **Les autorisations** pour Microsoft 365 applications pour chaque coffre de clés que vous utilisez pour la clé client, vous devez donner wrapKey, unwrapKey et obtenir des autorisations pour le principal de service Microsoft 365 correspondant. 

Pour accorder l’autorisation Microsoft 365 principal de service, exécutez la cmdlet **Set-AzKeyVaultAccessPolicy** à l’aide de la syntaxe suivante :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Où :

   - *Le nom du* coffre est le nom du coffre de clés que vous avez créé.
   - Pour Exchange Online et Skype Entreprise, remplacez *Office 365 appID par*`00000002-0000-0ff1-ce00-000000000000`
   - Pour SharePoint en ligne, OneDrive Entreprise et Teams fichiers, remplacez Office 365 *appID par*`00000003-0000-0ff1-ce00-000000000000`
   - Pour la stratégie à charges de travail multiples (Exchange, Teams, MIP EDM) qui s’applique à tous les utilisateurs du client, remplacez Office 365 *appID* par`c066d759-24ae-40e7-a56f-027002b5d3e4`

  Exemple : définition d’autorisations pour Exchange Online et Skype Entreprise :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Exemple : définition d’autorisations pour SharePoint online, OneDrive Entreprise et Teams fichiers :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>Assurez-vous que la suppression possible est activée sur vos coffres de clés

Lorsque vous pouvez récupérer rapidement vos clés, vous êtes moins susceptible d’être en panne de service étendue en raison de clés supprimées accidentellement ou malveillantment. Activez cette configuration, appelée suppression possible, avant de pouvoir utiliser vos clés avec la clé client. L’activation de la suppression possible vous permet de récupérer des clés ou des coffres dans les 90 jours suivant la suppression sans avoir à les restaurer à partir d’une sauvegarde.
  
Pour activer la suppression possible sur vos coffres de clés, complétez les étapes suivantes :
  
1. Connectez-vous à votre abonnement Azure avec Windows PowerShell. Pour obtenir des instructions, [voir Se Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Exécutez [l’cmdlet Get-AzKeyVault.](/powershell/module/az.keyvault/get-azkeyvault) Dans cet exemple, *le nom du coffre est* le nom du coffre de clés pour lequel vous activer la suppression possible :

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. Confirmez que la suppression (soft delete) est configurée pour le coffre de clés en exécutant l’cmdlet **Get-AzKeyVault.** Si la suppression possible est configurée correctement pour le coffre de clés, la propriété _Soft Delete Enabled_ renvoie la valeur **True**:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>Ajouter une clé à chaque coffre de clés en créant ou en important une clé

Il existe deux façons d’ajouter des clés à un coffre de clés Azure ; vous pouvez créer une clé directement dans le coffre de clés ou importer une clé. La création d’une clé directement dans le coffre de clés est moins compliquée, mais l’importation d’une clé permet un contrôle total sur la façon dont la clé est générée. Utilisez les touches RSA. Azure Key Vault ne prend pas en charge l’habillage et l’unwrapping avec des touches de courbe elliptiques.
  
Pour créer une clé directement dans votre coffre de clés, exécutez la cmdlet [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey) comme suit :
  
```powershell
Add-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Destination <HSM|Software> -KeyOps wrapKey,unwrapKey
```

Où :

- *Le nom du* coffre est le nom du coffre de clés dans lequel vous souhaitez créer la clé.

- *est* le nom que vous souhaitez donner à la nouvelle clé.

  > [!TIP]
  > Nommez les clés à l’aide d’une convention d’attribution de noms similaire, comme décrit ci-dessus pour les coffres de clés. Ainsi, dans les outils qui n’indiquent que le nom de la clé, la chaîne est auto-description.
  
Si vous avez l’intention de protéger la clé avec un HSM, veillez à spécifier **HSM** comme valeur du paramètre _Destination,_ sinon, spécifiez **Software**.

Par exemple :
  
```powershell
Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps wrapKey,unwrapKey
```

Pour importer une clé directement dans votre coffre de clés, vous devez avoir un module de sécurité matérielle nCipher nShield.
  
Certaines organisations préfèrent cette approche pour établir la provenance de leurs clés, puis cette méthode fournit également les attestations suivantes :
  
- L’ensemble d’outils utilisé pour l’importation inclut l’attestation à partir de nCipher que la clé Exchange ke key (KEK) utilisée pour chiffrer la clé que vous générez n’est pas exportable et qu’elle est générée à l’intérieur d’un HSM authentique qui a été fabriqué par nCipher.

- L’ensemble d’outils inclut l’attestation de nCipher que le monde de la sécurité Azure Key Vault a également été généré sur un HSM authentique fabriqué par nCipher. Cette attestation prouve que Microsoft utilise également du matériel nCipher authentique.

Consultez votre groupe de sécurité pour déterminer si les attestations ci-dessus sont requises. Pour obtenir la procédure détaillée de création d’une clé sur site et de son importation dans votre coffre de clés, voir Comment générer et transférer des clés protégées par [HSM](/azure/key-vault/keys/hsm-protected-keys)pour Azure Key Vault . Utilisez les instructions Azure pour créer une clé dans chaque coffre de clés.
  
### <a name="check-the-recovery-level-of-your-keys"></a>Vérifier le niveau de récupération de vos clés

Microsoft 365 nécessite que l’abonnement Azure Key Vault soit définie sur Ne pas annuler et que la suppression possible soit activée sur les clés utilisées par la clé client. Vous pouvez confirmer vos paramètres d’abonnement en regardant le niveau de récupération sur vos clés.
  
Pour vérifier le niveau de récupération d’une clé, Azure PowerShell, exécutez la cmdlet Get-AzKeyVaultKey comme suit :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

Si la propriété _Recovery Level_ renvoie autre chose qu’une valeur **récupérable+ ProtectedSubscription**, assurez-vous que vous avez placé l’abonnement dans la liste Ne pas annuler et que la suppression possible est activée sur chacun de vos coffres de clés.
  
### <a name="back-up-azure-key-vault"></a>Back up Azure Key Vault

Immédiatement après la création ou toute modification d’une clé, effectuez une sauvegarde et stockez des copies de la sauvegarde, à la fois en ligne et hors connexion. Ne connectez pas les copies hors connexion à un réseau. Stockez-les plutôt dans un emplacement hors connexion, par exemple dans une installation de stockage physique sécurisée ou commerciale. Au moins une copie de la sauvegarde doit être stockée dans un emplacement accessible en cas d’urgence. Les objets blob de sauvegarde sont l’unique moyen de restaurer le matériel de clé si une clé de coffre de clés doit être définitivement détruite ou rendue inopérante. Les clés qui sont externes à Azure Key Vault et importées dans Azure Key Vault ne sont pas éligibles en tant que sauvegarde, car les métadonnées nécessaires pour que la clé client utilise la clé n’existent pas avec la clé externe. Seule une sauvegarde provenant d’Azure Key Vault peut être utilisée pour les opérations de restauration avec la clé client. Par conséquent, vous devez créer une sauvegarde d’Azure Key Vault après avoir téléchargé ou créé une clé.
  
Pour créer une sauvegarde d’une clé Azure Key Vault, exécutez l’cmdlet [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey) comme suit :

```powershell
Backup-AzKeyVaultKey -VaultName <vault name> -Name <key name>
-OutputFile <filename.backup>
```

Assurez-vous que votre fichier de sortie utilise le `.backup` suffixe.
  
Le fichier de sortie résultant de cette cmdlet est chiffré et ne peut pas être utilisé en dehors d’Azure Key Vault. La sauvegarde peut être restaurée uniquement dans l’abonnement Azure à partir duquel la sauvegarde a été prise.
  
> [!TIP]
> Pour le fichier de sortie, choisissez une combinaison de votre nom de coffre-fort et de votre nom de clé. Cela rend le nom de fichier auto-décrivant. Cela permet également de s’assurer que les noms de fichiers de sauvegarde ne sont pas en conflit.
  
Par exemple :
  
```powershell
Backup-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -OutputFile Contoso-CK-EX-NA-VaultA1-Key001-Backup-20170802.backup
```

### <a name="validate-azure-key-vault-configuration-settings"></a>Valider les paramètres de configuration d’Azure Key Vault

La validation avant l’utilisation de clés dans une PED est facultative, mais vivement recommandée. Si vous utilisez les étapes pour configurer vos clés et coffres autres que ceux décrits dans cet article, validez l’état de vos ressources Azure Key Vault avant de configurer la clé client.
  
Pour vérifier que vos clés sont `get` `wrapKey` activées, et que les `unwrapKey` opérations sont activées :
  
Exécutez [l’cmdlet Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
```powershell
Get-AzKeyVault -VaultName <vault name>
```

Dans la sortie, recherchez la stratégie d’accès et l’identité Exchange Online (GUID) ou l’identité SharePoint Online (GUID) selon le cas. Les trois autorisations ci-dessus doivent être affichées sous Autorisations sur les clés.
  
Si la configuration de la stratégie d’accès est incorrecte, exécutez la cmdlet Set-AzKeyVaultAccessPolicy suivante :
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
```

Par exemple, pour Exchange Online et Skype Entreprise :
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
```

Par exemple, pour SharePoint Online et OneDrive Entreprise :
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
```

Pour vérifier qu’une date d’expiration n’est pas définie pour vos clés, exécutez la cmdlet [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

La clé client ne peut pas utiliser une clé expirée. Les opérations tentées avec une clé expirée échouent et peuvent entraîner une panne du service. Nous vous recommandons vivement de ne pas avoir de date d’expiration pour les clés utilisées avec la clé client. Une date d’expiration, une fois définie, ne peut pas être supprimée, mais peut être modifiée à une autre date. Si vous devez utiliser une clé dont la date d’expiration est définie, définissez la valeur d’expiration sur 31/12/9999. Les clés dont la date d’expiration est définie sur une date autre que le 31/12/9999 ne passeront pas Microsoft 365 validation.
  
Pour modifier une date d’expiration qui a été définie sur une valeur autre que le 31/12/9999, exécutez la cmdlet [Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) comme suit :
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Ne définissez pas de dates d’expiration sur les clés de chiffrement que vous utilisez avec la clé client.
  
### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Obtenir l’URI de chaque clé Azure Key Vault

Une fois que vous avez installé vos coffres de clés et ajouté vos clés, exécutez la commande suivante pour obtenir l’URI de la clé dans chaque coffre de clés. Vous utiliserez ces URIs lorsque vous créerez et affecterez chaque deP ultérieurement, donc enregistrez ces informations dans un endroit sûr. Exécutez cette commande une fois pour chaque coffre de clés.
  
Dans Azure PowerShell :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez effectué les étapes de cet article, vous êtes prêt à créer et attribuer des dep. Pour obtenir des instructions, voir [Gérer la clé client.](customer-key-manage.md)

## <a name="related-articles"></a>Articles connexes

- [Chiffrement du service avec la clé client](customer-key-overview.md)

- [Gérer la clé client](customer-key-manage.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Chiffrement de service](office-365-service-encryption.md)