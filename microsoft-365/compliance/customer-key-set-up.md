---
title: Configurer la clé client au niveau de l’application
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
description: Découvrez comment configurer la clé client pour les fichiers Exchange Online, Skype Entreprise, SharePoint Online, OneDrive Entreprise et Teams pour Microsoft 365.
ms.openlocfilehash: 94702cecb37686c3996c5ed70b1810a825bb2ff6
ms.sourcegitcommit: b3bb5bf5efa197ef8b16a33401b0b4f5663d3aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2021
ms.locfileid: "50032611"
---
# <a name="set-up-customer-key-at-the-application-level"></a>Configurer la clé client au niveau de l’application

Avec la clé client, vous contrôlez les clés de chiffrement de votre organisation, puis vous configurez Microsoft 365 pour les utiliser pour chiffrer vos données au repos dans les centres de données de Microsoft. En d’autres termes, la clé client permet aux clients d’ajouter une couche de chiffrement qui leur appartient, avec leurs clés. Les données au repos incluent les données issues d’Exchange Online et de Skype Entreprise qui sont enregistrées dans des boîtes aux lettres et des fichiers stockés dans SharePoint Online et OneDrive Entreprise.

Vous devez configurer Azure avant de pouvoir utiliser la clé client pour Office 365. Cet article décrit les étapes à suivre pour créer et configurer les ressources Azure requises, puis fournit les étapes de configuration de la clé client dans Office 365. Une fois l’installation d’Azure terminée, vous déterminez la stratégie et, par conséquent, les clés à affecter aux boîtes aux lettres et aux fichiers de votre organisation. Les boîtes aux lettres et les fichiers pour lesquels vous n’affectez pas de stratégie utiliseront des stratégies de chiffrement contrôlées et gérées par Microsoft. Pour plus d’informations sur la clé client ou pour une vue d’ensemble, voir Chiffrement de service avec clé client [dans Office 365.](customer-key-overview.md)
  
> [!IMPORTANT]
> Nous vous recommandons vivement de suivre les meilleures pratiques de cet article. Ces éléments sont appelés **CONSEIL et** **IMPORTANT**. La clé client vous permet de contrôler les clés de chiffrement racine dont l’étendue peut être aussi importante que l’ensemble de votre organisation. Cela signifie que les erreurs réalisées avec ces clés peuvent avoir un impact important et entraîner des interruptions de service ou une perte irrévocable de vos données.
  
## <a name="before-you-set-up-customer-key"></a>Avant de configurer la clé client

Avant de commencer, assurez-vous que vous avez la licence appropriée pour votre organisation. Utilisez un abonnement Azure payant facturé à l’aide d’un contrat Entreprise ou d’un fournisseur de services Cloud. Les abonnements Azure achetés à l’aide des plans Payer comme vous allez ou d’une carte de crédit ne sont pas pris en charge pour la clé client. À compter du 1er avril 2020, la clé client dans Office 365 est proposée dans office 365 E5, M365 E5, conformité M365 E5 et M365 E5 informations protection & gouvernance. Office 365 Advanced Compliance SKU n’est plus disponible pour l’utilisation de nouvelles licences. Les licences De conformité avancée Office 365 existantes continueront d’être prise en charge.

Pour comprendre les concepts et procédures décrits dans cet article, examinez la documentation [relative au coffre de clés Azure.](https://docs.microsoft.com/azure/key-vault/) Familiarisez-vous également avec les termes utilisés dans Azure, par exemple, [client Azure AD.](https://docs.microsoft.com/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant)

FastTrack est utilisé uniquement pour collecter les informations de configuration de service et client requises utilisées pour s’inscrire à la clé client. Les offres de clés client sont publiées via FastTrack afin que vous et nos partenaires pouvez envoyer facilement les informations requises à l’aide de la même méthode. FastTrack facilite également l’archivage des données que vous fournissez dans l’offre.
  
Si vous avez besoin d’une assistance supplémentaire au-delà de la documentation, contactez Microsoft Consulting Services (MCS), Premier Field Engineering (PFE) ou un partenaire Microsoft pour obtenir de l’aide. Pour fournir des commentaires sur la clé client, y compris la documentation, envoyez vos idées, suggestions et perspectives à customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Vue d’ensemble des étapes de la mise en place de la clé client

Pour configurer la clé client, remplissez ces tâches dans la commande répertoriée. Le reste de cet article fournit des instructions détaillées pour chaque tâche ou fournit des liens vers des informations supplémentaires pour chaque étape du processus.
  
**Dans Azure et Microsoft FastTrack :**
  
Vous effectuerez la plupart de ces tâches en vous connectant à distance à Azure PowerShell. Pour obtenir de meilleurs résultats, utilisez la version 4.4.0 ou ultérieure d’Azure PowerShell.
  
- [Créer deux nouveaux abonnements Azure](#create-two-new-azure-subscriptions)

- [Inscrire des abonnements Azure pour utiliser une période de rétention obligatoire](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  L’inscription peut prendre entre 1 et 5 jours ou moins.

- [Envoyer une demande d’activation de la clé client pour Office 365](#submit-a-request-to-activate-customer-key-for-office-365)

Une fois que vous avez créé les deux nouveaux abonnements Azure, vous devez envoyer la demande d’offre de clé client appropriée en remplissant un formulaire web hébergé sur le portail Microsoft FastTrack. **L’équipe FastTrack ne fournit pas d’assistance avec la clé client. Office utilise simplement le portail FastTrack pour** vous permettre de soumettre le formulaire et de nous aider à suivre les offres pertinentes pour la clé client.

- [Créer un coffre de clés Azure premium dans chaque abonnement](#create-a-premium-azure-key-vault-in-each-subscription)

- [Attribuer des autorisations à chaque coffre de clés](#assign-permissions-to-each-key-vault)

- [Activer, puis confirmer la suppression possible sur vos coffres de clés](#enable-and-then-confirm-soft-delete-on-your-key-vaults)

- [Ajouter une clé à chaque coffre de clés en créant ou en important une clé](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Vérifier le niveau de récupération de vos clés](#check-the-recovery-level-of-your-keys)

- [Back up Azure Key Vault](#back-up-azure-key-vault)

- [Valider les paramètres de configuration d’Azure Key Vault](#validate-azure-key-vault-configuration-settings)

- [Obtenir l’URI de chaque clé Azure Key Vault](#obtain-the-uri-for-each-azure-key-vault-key)

**Dans Office 365 :**
  
Exchange Online et Skype Entreprise :
  
- [Créer une stratégie de chiffrement de données à utiliser avec Exchange Online et Skype Entreprise](#create-a-data-encryption-policy-dep-for-use-with-exchange-online-and-skype-for-business)

- [Affecter un deP à une boîte aux lettres](#assign-a-dep-to-a-mailbox)

- [Valider le chiffrement de boîte aux lettres](#validate-mailbox-encryption)

SharePoint Online et OneDrive Entreprise :
  
- [Créer une stratégie de chiffrement de données (DEP) pour chaque site géographique SharePoint Online et OneDrive Entreprise](#create-a-data-encryption-policy-dep-for-each-sharepoint-online-and-onedrive-for-business-geo)

- [Valider le chiffrement de fichiers pour les fichiers SharePoint Online, OneDrive Entreprise et Teams](#validate-file-encryption)

## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Effectuer des tâches dans Azure Key Vault et Microsoft FastTrack pour la clé client

Effectuer ces tâches dans Azure Key Vault. Vous devez effectuer ces étapes, que vous vouliez configurer la clé client pour Exchange Online et Skype Entreprise ou pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, ou pour tous les services pris en charge dans Office 365.
  
### <a name="create-two-new-azure-subscriptions"></a>Créer deux nouveaux abonnements Azure

La clé client nécessite deux abonnements Azure. En tant que meilleure pratique, Microsoft vous recommande de créer de nouveaux abonnements Azure à utiliser avec la clé client. Les clés Azure Key Vault peuvent uniquement être autorisées pour les applications dans le même client Azure Active Directory (Microsoft Azure Active Directory), vous devez créer les nouveaux abonnements à l’aide du même client Azure AD que celui utilisé avec votre organisation où les dep seront affectés. Par exemple, à l’aide de votre compte professionnel ou scolaire qui dispose de privilèges d’administrateur général dans votre organisation. Pour obtenir la procédure détaillée, voir [S’inscrire à Azure en tant qu’organisation.](https://azure.microsoft.com/documentation/articles/sign-up-organization/)
  
> [!IMPORTANT]
> La clé client nécessite deux clés pour chaque stratégie de chiffrement de données (DEP). Pour ce faire, vous devez créer deux abonnements Azure. En tant que meilleure pratique, Microsoft recommande que des membres distincts de votre organisation configurent une clé dans chaque abonnement. Vous devez uniquement utiliser ces abonnements Azure pour administrer les clés de chiffrement pour Office 365. Cela protège votre organisation au cas où l’un de vos opérateurs supprimerait accidentellement, intentionnellement ou malveillantement les clés dont ils sont responsables, ou en cas de mauvaise gestion.
>

Il n’existe aucune limite pratique au nombre d’abonnements Azure que vous pouvez créer pour votre organisation. Le fait de suivre ces meilleures pratiques permet de minimiser l’impact des erreurs humaines tout en aidant à gérer les ressources utilisées par la clé client.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Envoyer une demande d’activation de la clé client pour Office 365

Une fois que vous avez terminé les étapes Azure, vous devez envoyer une demande d’offre dans le portail [Microsoft FastTrack.](https://fasttrack.microsoft.com/) Une fois que vous avez envoyé une demande via le portail web FastTrack, Microsoft vérifie les données de configuration azure Key Vault et les informations de contact que vous avez fournies. Les sélections que vous faites dans le formulaire d’offre concernant les responsables autorisés de votre organisation sont essentielles et nécessaires pour l’inscription à la clé client. Les responsables de votre organisation garantissent l’authenticité de toute demande de révocation et de destruction de toutes les clés utilisées avec une stratégie de chiffrement de données de clé client. Vous devez faire cette étape une fois pour activer la clé client pour la couverture Exchange Online et Skype Entreprise et une deuxième fois pour activer la clé client pour SharePoint Online et OneDrive Entreprise.
  
Pour soumettre une offre d’activation de la clé client, effectuer les étapes suivantes :
  
1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous au [portail Microsoft FastTrack.](https://fasttrack.microsoft.com/)

2. Une fois que vous êtes connecté, accédez au tableau **de bord.**

3. Choisissez **Déployer dans** la barre de navigation OU **sélectionnez** Afficher toutes **les** ressources de déploiement sur la carte d’informations Déployer et passer en revue la liste des offres actuelles. 

4. Choisissez la carte d’informations pour l’offre qui vous concerne :

   - **Exchange Online et Skype Entreprise :** Choisissez **l’aide de la clé de chiffrement de demande pour l’offre Exchange Online.**

   - **Fichiers SharePoint Online, OneDrive et Teams :** Choisissez **l’aide de la clé de chiffrement de demande pour l’offre Sharepoint et OneDrive.**

5. Une fois que vous avez examiné les détails de l’offre, choisissez **Continuer à l’étape 2**.

6. Remplissez tous les détails applicables et les informations demandées sur le formulaire d’offre. Accordez une attention particulière à vos sélections pour les responsables de votre organisation que vous souhaitez autoriser à approuver la destruction définitive et irréversible des clés de chiffrement et des données. Une fois que vous avez terminé le formulaire, choisissez **Envoyer.**

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Inscrire des abonnements Azure pour utiliser une période de rétention obligatoire

La perte temporaire ou permanente des clés de chiffrement racine peut perturber ou même catastrophique le fonctionnement du service et entraîner la perte de données. Pour cette raison, les ressources utilisées avec la clé client nécessitent une protection forte. Toutes les ressources Azure utilisées avec la clé client offrent des mécanismes de protection au-delà de la configuration par défaut. Vous pouvez baliser ou inscrire des abonnements Azure pour *une période de rétention obligatoire.* Une période de rétention obligatoire empêche l’annulation immédiate et irrévocable de votre abonnement Azure. Les étapes nécessaires pour inscrire des abonnements Azure pour une période de rétention obligatoire nécessitent une collaboration avec l’équipe Microsoft 365. Ce processus peut prendre entre un et cinq jours ou moins. Auparavant, la période de rétention obligatoire était parfois appelée « Ne pas annuler ».
  
Avant de contacter l’équipe Microsoft 365, vous devez suivre les étapes suivantes pour chaque abonnement Azure que vous utilisez avec la clé client. Assurez-vous que le module [Azure PowerShell Az](https://docs.microsoft.com/powershell/azure/new-azureps-module-az) est installé avant de commencer.
  
1. Connectez-vous avec Azure PowerShell. Pour obtenir des instructions, [voir Se connectez avec Azure PowerShell.](https://docs.microsoft.com/powershell/azure/authenticate-azureps)

2. Exécutez la cmdlet Register-AzProviderFeature pour inscrire vos abonnements afin d’utiliser une période de rétention obligatoire. Effectuer cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

3. Contactez Microsoft pour terminer le processus. Pour l’équipe SharePoint et OneDrive [Entreprise,](mailto:spock@microsoft.com)contactez spock@microsoft.com . Pour Exchange Online et Skype Entreprise, contactez [exock@microsoft.com](mailto:exock@microsoft.com). Incluez les informations suivantes dans votre courrier électronique :

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

Les étapes de création d’un coffre de clés sont documentées dans La mise en route [d’Azure Key Vault,](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)qui vous guide tout au long de l’installation et du lancement d’Azure PowerShell, de la connexion à votre abonnement Azure, de la création d’un groupe de ressources et de la création d’un coffre de clés dans ce groupe de ressources.
  
Lorsque vous créez un coffre de clés, vous devez choisir une référence (SKU) : Standard ou Premium. La référence SKU standard permet de protéger les clés Azure Key Vault avec des logiciels (il n’existe pas de protection de clé de module de sécurité matérielle (HSM) ) et la référence SKU Premium permet d’utiliser des HSM pour la protection des clés de coffre de clés. La clé client accepte les coffres de clés qui utilisent l’une ou l’autre référence (SKU), même si Microsoft recommande vivement d’utiliser uniquement la référence SKU Premium. Le coût des opérations avec des clés de l’un ou l’autre type est le même, donc la seule différence de coût est le coût par mois pour chaque clé protégée par HSM. Pour plus [d’informations,](https://azure.microsoft.com/pricing/details/key-vault/) voir la tarification du coffre de clés.
  
> [!IMPORTANT]
> Utilisez les coffres de clés SKU Premium et les clés protégées par HSM pour les données de production, et utilisez uniquement les clés et coffres de clés SKU standard à des fins de test et de validation.
  
Pour chaque service Microsoft 365 avec lequel vous utiliserez la clé client, créez un coffre de clés dans chacun des deux abonnements Azure que vous avez créés. Par exemple, pour Exchange Online et Skype Entreprise uniquement ou SharePoint Online et OneDrive Entreprise uniquement, vous ne créerez qu’une seule paire de coffres. Pour activer la clé client pour Exchange Online et SharePoint Online, vous allez créer deux paires de coffres de clés.
  
Utilisez une convention d’attribution de noms pour les coffres de clés qui reflète l’utilisation prévue du dep auquel vous associerez les coffres. Consultez la section Recommandations ci-dessous pour obtenir des recommandations en matière de convention d’attribution de noms.
  
Créez un ensemble distinct de coffres couplés pour chaque stratégie de chiffrement de données. Pour Exchange Online, l’étendue d’une stratégie de chiffrement de données est choisie par vous lorsque vous affectez la stratégie à la boîte aux lettres. Une boîte aux lettres ne peut avoir qu’une seule stratégie affectée et vous pouvez créer jusqu’à 50 stratégies. L’étendue d’une stratégie SharePoint Online inclut toutes les données au sein d’une organisation dans un emplacement géographique ou _géographique._

La création de coffres de clés nécessite également la création de groupes de ressources Azure, dans la mesure où les coffres de clés nécessitent une capacité de stockage (mais de petite taille) et la journalisation du coffre de clés, si elle est activée, génère également des données stockées. En tant que meilleure pratique, Microsoft recommande d’utiliser des administrateurs distincts pour gérer chaque groupe de ressources, avec l’administration alignée sur l’ensemble d’administrateurs qui gérera toutes les ressources de clé client associées.
  
> [!IMPORTANT]
> Pour optimiser la disponibilité, vos coffres de clés doivent se trouver dans des régions proches de votre service Microsoft 365. Par exemple, si votre organisation Exchange Online est en Amérique du Nord, placez vos coffres de clés en Amérique du Nord. Si votre organisation Exchange Online se trouve en Europe, placez vos coffres de clés en Europe.
> 
> Utilisez un préfixe commun pour les coffres de clés et incluez une abréviation de l’utilisation et de l’étendue du coffre de clés et des clés (par exemple, pour le service SharePoint Contoso où les coffres seront situés en Amérique du Nord, une paire de noms possible est Contoso-O365SP-NA-VaultA1 et Contoso-O365SP-NA-VaultA2). Les noms de coffre sont des chaînes globalement uniques dans Azure. Par conséquent, vous devrez peut-être essayer les variantes de vos noms souhaités si les noms souhaités sont déjà revendiqués par d’autres clients Azure. À compter de juillet 2017, les noms des coffres ne peuvent pas être modifiés. Il est donc préférable d’avoir un plan écrit pour l’installation et d’utiliser une deuxième personne pour vérifier que le plan est exécuté correctement.
> 
> Si possible, créez vos coffres dans des régions non couplées. Les régions Azure couplées fournissent une haute disponibilité entre les domaines de défaillance de service. Par conséquent, les paires régionales peuvent être pensés comme la région de sauvegarde l’une de l’autre. Cela signifie qu’une ressource Azure placée dans une région gagne automatiquement en tolérance de pannes via la région couplée. Pour cette raison, le choix de régions pour deux coffres utilisés dans une stratégie de chiffrement de données dans laquelle les régions sont couplées signifie que seules deux régions de disponibilité sont en cours d’utilisation. La plupart des zones géographiques ne comptent que deux régions. Il n’est donc pas encore possible de sélectionner des régions non couplées. Si possible, choisissez deux régions non couplées pour les deux coffres utilisés avec une stratégie de chiffrement de données. Cela bénéficie d’un total de quatre régions de disponibilité. Pour plus d’informations, voir Continuité d’activité et récupération d’urgence [(BCDR)](https://docs.microsoft.com/azure/best-practices-availability-paired-regions) : Azure Paired Regions pour obtenir la liste actuelle des paires régionales.
  
### <a name="assign-permissions-to-each-key-vault"></a>Attribuer des autorisations à chaque coffre de clés

Vous devez définir trois ensembles distincts d’autorisations pour chaque coffre de clés, en fonction de votre implémentation. Par exemple, vous devez définir un ensemble d’autorisations pour chacune des autorisations suivantes :
  
- **Administrateurs de coffre de clés** qui font la gestion quotidienne de votre coffre de clés pour votre organisation. Ces tâches incluent la sauvegarde, la création, l’importation, la liste et la restauration.

  > [!IMPORTANT]
  > L’ensemble des autorisations attribuées aux administrateurs de coffre de clés n’inclut pas l’autorisation de supprimer des clés. Cette pratique est intentionnelle et importante. La suppression des clés de chiffrement n’est généralement pas effectuée, car cela détruit définitivement les données. En tant que meilleure pratique, n’accordez pas cette autorisation aux administrateurs de coffre de clés par défaut. Au lieu de cela, réservez-le aux contributeurs de coffre de clés et affectez-le uniquement à un administrateur à court terme une fois que vous comprenez clairement les conséquences.
  
  Pour attribuer ces autorisations à un utilisateur de votre organisation, connectez-vous à votre abonnement Azure avec Azure PowerShell. Pour obtenir des instructions, [voir Se connectez avec Azure PowerShell.](https://docs.microsoft.com/powershell/azure/authenticate-azureps)

- Exécutez lSet-AzKeyVaultAccessPolicy cmdlet pour attribuer les autorisations nécessaires.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Par exemple :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **Contributeurs de coffre de clés** qui peuvent modifier les autorisations sur le coffre de clés Azure lui-même. Vous devez modifier ces autorisations lorsque les employés quittent ou rejoignent votre équipe. Dans les rares cas où les administrateurs de coffre de clés ont légitimement besoin d’autorisations pour supprimer ou restaurer une clé, vous devez également modifier les autorisations. Cet ensemble de contributeurs de coffre de clés doit avoir le rôle **Collaborateur** sur votre coffre de clés. Vous pouvez attribuer ce rôle à l’aide d’Azure Resource Manager. Pour obtenir la procédure détaillée, voir Utiliser Role-Based contrôle d’accès pour gérer l’accès [à vos ressources d’abonnement Azure.](https://docs.microsoft.com/azure/active-directory/role-based-access-control-configure) L’administrateur qui crée un abonnement dispose de cet accès implicitement et de la possibilité d’affecter d’autres administrateurs au rôle collaborateur.

- Si vous avez l’intention d’utiliser la clé client avec Exchange Online et Skype Entreprise, vous devez accorder à Microsoft 365 l’autorisation d’utiliser le coffre de clés pour le compte d’Exchange Online et de Skype Entreprise. De même, si vous envisagez d’utiliser la clé client avec SharePoint Online et OneDrive Entreprise, vous devez ajouter l’autorisation à Microsoft 365 d’utiliser le coffre de clés pour le compte de SharePoint Online et OneDrive Entreprise. Pour accorder des autorisations à Microsoft 365, exécutez la cmdlet **Set-AzKeyVaultAccessPolicy** à l’aide de la syntaxe suivante :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Où :

    - *Le nom du* coffre est le nom du coffre de clés que vous avez créé.

    - Pour Exchange Online et Skype Entreprise, remplacez  *appID Office 365* par `00000002-0000-0ff1-ce00-000000000000`

    - Pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, remplacez  *appID Office 365* par `00000003-0000-0ff1-ce00-000000000000`

  Exemple : définition d’autorisations pour Exchange Online et Skype Entreprise :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Exemple : définition d’autorisations pour les fichiers SharePoint Online, OneDrive Entreprise et Teams :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

### <a name="enable-and-then-confirm-soft-delete-on-your-key-vaults"></a>Activer, puis confirmer la suppression possible sur vos coffres de clés

Lorsque vous pouvez récupérer rapidement vos clés, vous êtes moins susceptible d’être en panne de service étendue en raison de clés supprimées accidentellement ou malveillantment. Vous devez activer cette configuration, appelée suppression possible, avant de pouvoir utiliser vos clés avec la clé client. L’activation de la suppression possible vous permet de récupérer des clés ou des coffres dans les 90 jours suivant la suppression sans avoir à les restaurer à partir d’une sauvegarde.
  
Pour activer la suppression possible sur vos coffres de clés, complétez les étapes suivantes :
  
1. Connectez-vous à votre abonnement Azure avec Windows PowerShell. Pour obtenir des instructions, [voir Se connectez avec Azure PowerShell.](https://docs.microsoft.com/powershell/azure/authenticate-azureps)

2. Exécutez [l’cmdlet Get-AzKeyVault.](https://docs.microsoft.com/powershell/module/az.keyvault/get-azkeyvault) Dans cet exemple, le *nom du coffre est* le nom du coffre de clés pour lequel vous activer la suppression possible :

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

Il existe deux façons d’ajouter des clés à un coffre de clés Azure ; vous pouvez créer une clé directement dans le coffre de clés ou importer une clé. La création d’une clé directement dans le coffre de clés est la méthode la moins complexe, tandis que l’importation d’une clé permet un contrôle total sur la façon dont la clé est générée. Utilisez les touches RSA. Azure Key Vault ne prend pas en charge l’habillage et l’unwrapping avec des touches de courbe elliptiques.
  
Pour créer une clé directement dans votre coffre de clés, exécutez la cmdlet [Add-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/add-azkeyvaultkey) comme suit :
  
```powershell
Add-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Destination <HSM|Software> -KeyOps wrapKey,unwrapKey
```

Où :

- *Le nom du* coffre est le nom du coffre de clés dans lequel vous souhaitez créer la clé.

- *est* le nom que vous souhaitez donner à la nouvelle clé.

  > [!TIP]
  > Nommez les clés à l’aide d’une convention d’attribution de noms similaire, comme décrit ci-dessus pour les coffres de clés. Ainsi, dans les outils qui n’indiquent que le nom de la clé, la chaîne est auto-décrivante.
  
Si vous avez l’intention de protéger la clé avec un HSM, veillez à spécifier **HSM** comme valeur du paramètre _Destination,_ sinon, spécifiez **Software**.

Par exemple :
  
```powershell
Add-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -Name Contoso-O365EX-NA-VaultA1-Key001 -Destination HSM -KeyOps wrapKey,unwrapKey
```

Pour importer une clé directement dans votre coffre de clés, vous devez avoir un module de sécurité matérielle nCipher nShield.
  
Certaines organisations préfèrent cette approche pour établir la provenance de leurs clés, puis cette méthode fournit également les attestations suivantes :
  
- L’ensemble d’outils utilisé pour l’importation inclut l’attestation à partir de nCipher que la clé KEK (Key Exchange Key Exchange Key) utilisée pour chiffrer la clé que vous générez n’est pas exportable et qu’elle est générée à l’intérieur d’un HSM authentique qui a été fabriqué par nCipher.

- L’ensemble d’outils inclut l’attestation de nCipher que le monde de la sécurité Azure Key Vault a également été généré sur un HSM authentique fabriqué par nCipher. Cette attestation vous prouve que Microsoft utilise également du matériel nCipher authentique.

Consultez votre groupe de sécurité pour déterminer si les attestations ci-dessus sont requises. Pour obtenir la procédure détaillée de création d’une clé sur site et de son importation dans votre coffre de clés, voir Comment générer et transférer des clés protégées par [HSM](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/)pour Azure Key Vault . Utilisez les instructions Azure pour créer une clé dans chaque coffre de clés.
  
### <a name="check-the-recovery-level-of-your-keys"></a>Vérifier le niveau de récupération de vos clés

Microsoft 365 exige que l’abonnement Azure Key Vault soit réglé sur Ne pas annuler et que la suppression possible soit activée sur les clés utilisées par la clé client. Vous pouvez confirmer vos paramètres d’abonnement en regardant le niveau de récupération sur vos clés.
  
Pour vérifier le niveau de récupération d’une clé, dans Azure PowerShell, exécutez l'Get-AzKeyVaultKey cmdlet comme suit :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

Si la propriété _Recovery Level_ renvoie autre chose qu’une valeur **récupérable+ ProtectedSubscription**, assurez-vous que vous avez placé l’abonnement dans la liste Ne pas annuler et que la suppression possible est activée sur chacun de vos coffres de clés.
  
### <a name="back-up-azure-key-vault"></a>Back up Azure Key Vault

Immédiatement après la création ou toute modification d’une clé, effectuez une sauvegarde et stockez des copies de la sauvegarde, à la fois en ligne et hors connexion. Les copies hors connexion ne doivent être connectées à aucun réseau, par exemple dans une installation de stockage physique sécurisée ou commerciale. Au moins une copie de la sauvegarde doit être stockée dans un emplacement accessible en cas d’incident. Les objets blob de sauvegarde sont l’unique moyen de restaurer le matériel de clé si une clé de coffre de clés doit être définitivement détruite ou rendue inopérante. Les clés qui sont externes à Azure Key Vault et qui ont été importées dans Azure Key Vault ne sont pas éligibles en tant que sauvegarde, car les métadonnées nécessaires pour que la clé client utilise la clé n’existent pas avec la clé externe. Seule une sauvegarde provenant d’Azure Key Vault peut être utilisée pour les opérations de restauration avec la clé client. Par conséquent, vous devez créer une sauvegarde d’Azure Key Vault après avoir téléchargé ou créé une clé.
  
Pour créer une sauvegarde d’une clé Azure Key Vault, exécutez l’cmdlet [Backup-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/backup-azkeyvaultkey) comme suit :

```powershell
Backup-AzKeyVaultKey -VaultName <vault name> -Name <key name>
-OutputFile <filename.backup>
```

Assurez-vous que votre fichier de sortie utilise le suffixe `.backup` .
  
Le fichier de sortie résultant de cette cmdlet est chiffré et ne peut pas être utilisé en dehors d’Azure Key Vault. La sauvegarde peut être restaurée uniquement dans l’abonnement Azure à partir duquel la sauvegarde a été prise.
  
> [!TIP]
> Pour le fichier de sortie, choisissez une combinaison de votre nom de coffre-fort et de votre nom de clé. Cela rend le nom de fichier auto-décrivant. Cela permet également de s’assurer que les noms de fichiers de sauvegarde ne sont pas en conflit.
  
Par exemple :
  
```powershell
Backup-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -Name Contoso-O365EX-NA-VaultA1-Key001 -OutputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

### <a name="validate-azure-key-vault-configuration-settings"></a>Valider les paramètres de configuration d’Azure Key Vault

La validation avant l’utilisation de clés dans une PED est facultative, mais vivement recommandée. Si vous utilisez les étapes pour configurer vos clés et coffres autres que ceux décrits dans cet article, validez l’état de vos ressources Azure Key Vault avant de configurer la clé client.
  
Pour vérifier que vos clés sont `get` `wrapKey` activées, et que les `unwrapKey` opérations sont activées :
  
Exécutez [l’cmdlet Get-AzKeyVault](https://docs.microsoft.com/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
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
Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
```

Par exemple, pour SharePoint Online et OneDrive Entreprise :
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365SP-NA-VaultA1
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
```

Pour vérifier qu’une date d’expiration n’est pas définie pour vos clés, exécutez la cmdlet [Get-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

La clé client ne peut pas utiliser une clé expirée. Les opérations tentées avec une clé expirée échouent et peuvent entraîner une panne du service. Nous vous recommandons vivement de ne pas avoir de date d’expiration pour les clés utilisées avec la clé client. Une date d’expiration, une fois définie, ne peut pas être supprimée, mais peut être modifiée à une autre date. Si vous devez utiliser une clé dont la date d’expiration est définie, définissez la valeur d’expiration sur 31/12/9999. Les clés dont la date d’expiration est définie sur une date autre que le 31/12/9999 ne seront pas validées par Microsoft 365.
  
Pour modifier une date d’expiration qui a été définie sur une valeur autre que le 31/12/9999, exécutez la cmdlet [Update-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/update-azkeyvaultkey) comme suit :
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Ne définissez pas de dates d’expiration sur les clés de chiffrement que vous utilisez avec la clé client.
  
### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Obtenir l’URI de chaque clé Azure Key Vault

Une fois que vous avez installé vos coffres de clés et ajouté vos clés, exécutez la commande suivante pour obtenir l’URI de la clé dans chaque coffre de clés. Vous devrez utiliser ces URIs lorsque vous créerez et affecterez chaque deP ultérieurement, donc enregistrez ces informations dans un endroit sûr. Exécutez cette commande une fois pour chaque coffre de clés.
  
Dans Azure PowerShell :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="office-365-setting-up-customer-key-for-exchange-online-and-skype-for-business"></a>Office 365 : configuration de la clé client pour Exchange Online et Skype Entreprise

Avant de commencer, assurez-vous d’avoir effectué les tâches requises pour configurer Azure Key Vault. Pour plus [d’informations, voir](#complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key) Tâches terminées dans Azure Key Vault et Microsoft FastTrack for Customer Key.
  
Pour configurer la clé client pour Exchange Online et Skype Entreprise, vous devez effectuer ces étapes en vous connectant à distance à Exchange Online avec Windows PowerShell.
  
### <a name="create-a-data-encryption-policy-dep-for-use-with-exchange-online-and-skype-for-business"></a>Créer une stratégie de chiffrement de données à utiliser avec Exchange Online et Skype Entreprise

Un dep est associé à un ensemble de clés stockées dans Azure Key Vault. Vous affectez un deP à une boîte aux lettres dans Microsoft 365. Microsoft 365 utilisera ensuite les clés identifiées dans la stratégie pour chiffrer la boîte aux lettres. Pour créer le PED, vous avez besoin des URL de coffre de clés que vous avez obtenues précédemment. Pour obtenir des instructions, consultez l’URI de chaque clé [Azure Key Vault.](#obtain-the-uri-for-each-azure-key-vault-key)
  
N’oubliez pas ! Lorsque vous créez un deP, vous spécifiez deux clés dans deux coffres de clés Azure différents. Créez ces clés dans deux régions Azure distinctes pour assurer la redondance géographique.
  
Pour créer le PD DEP, suivez les étapes suivantes :
  
1. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous à [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) dans Windows PowerShell fenêtre.

2. Pour créer une dep, utilisez la cmdlet New-DataEncryptionPolicy en tapant la commande suivante.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Où :

   - *PolicyName est* le nom que vous souhaitez utiliser pour la stratégie. Les noms ne peuvent pas contenir d’espaces. Par exemple, USA_mailboxes.

   - *La description de* la stratégie est une description conviviale de la stratégie qui vous aidera à vous souvenir de l’objectif de la stratégie. Vous pouvez inclure des espaces dans la description. Par exemple, « Clé racine pour les boîtes aux lettres aux États-Unis et ses territoires ».

   - *KeyVaultURI1 est* l’URI de la première clé de la stratégie. Par exemple, <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2 est* l’URI de la deuxième clé de la stratégie. Par exemple, <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. Séparez les deux URS par une virgule et un espace.

   Exemple :
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01, https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-DataEncryptionPolicy](https://docs.microsoft.com/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Affecter un deP à une boîte aux lettres

Affectez le deP à une boîte aux lettres à l’aide Set-Mailbox cmdlet. Une fois la stratégie assignée, Microsoft 365 peut chiffrer la boîte aux lettres avec la clé identifiée dans le PD DEP.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

Où *MailboxIdParameter* spécifie une boîte aux lettres utilisateur. Pour plus d’informations sur la cmdlet Set-Mailbox, voir [Set-Mailbox](https://docs.microsoft.com/powershell/module/exchange/set-mailbox).

Dans les environnements hybrides, vous pouvez affecter un deP aux données de boîte aux lettres sur site synchronisées dans votre client Exchange Online. Pour affecter un dep à ces données de boîte aux lettres synchronisées, vous devez utiliser la cmdlet Set-MailUser de messagerie. Pour plus d’informations sur les données de boîte aux lettres dans l’environnement hybride, voir les boîtes aux lettres sur site utilisant Outlook pour iOS et Android avec l’authentification [moderne hybride.](https://docs.microsoft.com/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Où *MailUserIdParameter* spécifie un utilisateur de messagerie (également appelé utilisateur à messagerie). Pour plus d’informations sur la cmdlet Set-MailUser, voir [Set-MailUser](https://docs.microsoft.com/powershell/module/exchange/set-mailuser).
  
### <a name="validate-mailbox-encryption"></a>Valider le chiffrement de boîte aux lettres

Le chiffrement d’une boîte aux lettres peut prendre un certain temps. Pour l’attribution de stratégie pour la première fois, la boîte aux lettres doit également passer complètement d’une base de données à une autre pour que le service puisse chiffrer la boîte aux lettres. Nous vous recommandons d’attendre 72 heures avant d’essayer de valider le chiffrement après avoir changé une dep ou la première fois que vous affectez un deP à une boîte aux lettres.
  
Utilisez la cmdlet Get-MailboxStatistics pour déterminer si une boîte aux lettres est chiffrée.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

La propriété IsEncrypted renvoie la valeur **true** si la boîte aux lettres est chiffrée et la valeur **false** si la boîte aux lettres n’est pas chiffrée. Le temps de déplacement des boîtes aux lettres dépend du nombre de boîtes aux lettres à laquelle vous attribuez une dep pour la première fois et de la taille des boîtes aux lettres. Si les boîtes aux lettres n’ont pas été chiffrées après une semaine à partir de l’heure à partir de la PED, contactez Microsoft.

## <a name="office-365-setting-up-customer-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Office 365 : configuration de la clé client pour les fichiers SharePoint Online, OneDrive Entreprise et Teams

Avant de commencer, assurez-vous d’avoir effectué les tâches requises pour configurer Azure Key Vault. Pour plus [d’informations, voir](#complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key) Tâches terminées dans Azure Key Vault et Microsoft FastTrack for Customer Key.
  
Pour configurer la clé client pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, vous devez effectuer ces étapes en vous connectant à distance à SharePoint Online avec Windows PowerShell.
  
### <a name="create-a-data-encryption-policy-dep-for-each-sharepoint-online-and-onedrive-for-business-geo"></a>Créer une stratégie de chiffrement de données (DEP) pour chaque géo SharePoint Online et OneDrive Entreprise

Vous associez un deP à un ensemble de clés stockées dans Azure Key Vault. Vous appliquez un deP à toutes vos données dans un emplacement géographique, également appelé géo. Si vous utilisez la fonctionnalité multigéogéo d’Office 365, vous pouvez créer une dep par géo avec la possibilité d’utiliser différentes clés par géo. Si vous n’utilisez pas multigéogé, vous pouvez en créer un dans votre organisation pour l’utiliser avec les fichiers SharePoint Online, OneDrive Entreprise et Teams. Microsoft 365 utilise les clés identifiées dans le PD DEP pour chiffrer vos données dans cette géo. Pour créer le PED, vous avez besoin des URL de coffre de clés que vous avez obtenues précédemment. Pour obtenir des instructions, consultez l’URI de chaque clé [Azure Key Vault.](#obtain-the-uri-for-each-azure-key-vault-key)
  
N’oubliez pas ! Lorsque vous créez un deP, vous spécifiez deux clés dans deux coffres de clés Azure différents. Créez ces clés dans deux régions Azure distinctes pour assurer la redondance géographique.
  
Pour créer un PDV, vous devez vous connecter à distance à SharePoint Online à l’aide de Windows PowerShell.
  
1. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps&preserve-view=true).

2. Dans Microsoft SharePoint Online Management Shell, exécutez l'Register-SPODataEncryptionPolicy cmdlet suivante :

   ```powershell
   Register-SPODataEncryptionPolicy -Identity <adminSiteCollectionURL> -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Exemple :
  
   ```powershell
   Register-SPODataEncryptionPolicy -Identity https://contoso.sharepoint.com -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a’
   ```

   Lorsque vous inscrivez la PD DEP, le chiffrement commence sur les données de la géo. Le chiffrement peut prendre un certain temps. Pour plus d’informations sur l’utilisation de ce paramètre, voir [Register-SPODataEncryptionPolicy](https://docs.microsoft.com/powershell/module/sharepoint-online/register-spodataencryptionpolicy?view=sharepoint-ps&preserve-view=true).

### <a name="validate-file-encryption"></a>Valider le chiffrement de fichiers

 Pour valider le chiffrement des fichiers SharePoint Online, OneDrive Entreprise et Teams, connectez-vous à [SharePoint Online PowerShell,](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)puis utilisez la cmdlet Get-SPODataEncryptionPolicy pour vérifier l’état de votre client. La _propriété State_ renvoie une valeur enregistrée **si** le chiffrement de clé client est activé et que tous les fichiers de tous les sites ont été chiffrés. Si le chiffrement est toujours en cours, cette cmdlet fournit des informations sur le pourcentage de sites terminés.

## <a name="related-articles"></a>Articles connexes

- [Chiffrement du service avec la clé client](customer-key-overview.md)

- [Gérer la clé client](customer-key-manage.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Chiffrement de service](office-365-service-encryption.md)
