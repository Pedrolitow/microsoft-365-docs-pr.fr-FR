---
title: Configurer la clé client
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Découvrez comment configurer la clé client.
ms.openlocfilehash: 93cf56ba30f333697ccb1ef6f4064918e73d4fcf
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042437"
---
# <a name="set-up-customer-key"></a>Configurer la clé client

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Avec la clé client, vous contrôlez les clés de chiffrement de votre organisation, puis configurez Microsoft 365 pour les utiliser pour chiffrer vos données au repos dans les centres de données de Microsoft. En d’autres termes, la clé client permet aux clients d’ajouter une couche de chiffrement qui leur appartient, avec leurs clés.

Configurez Azure avant de pouvoir utiliser la clé client. Cet article décrit les étapes à suivre pour créer et configurer les ressources Azure requises, puis fournit les étapes de configuration de la clé client. Après avoir configuré Azure, vous déterminez la stratégie et, par conséquent, les clés à affecter pour chiffrer les données dans différentes charges de travail Microsoft 365 de votre organisation. Pour plus d’informations sur la clé client ou pour une vue d’ensemble, consultez [chiffrement de service avec la clé client Microsoft Purview](customer-key-overview.md).
  
> [!IMPORTANT]
> Nous vous recommandons vivement de suivre les meilleures pratiques décrites dans cet article. Ceux-ci sont appelés comme **TIP** et **IMPORTANT**. La clé client vous permet de contrôler les clés de chiffrement racine dont l’étendue peut être aussi grande que l’ensemble de votre organisation. Cela signifie que les erreurs commises avec ces clés peuvent avoir un impact général et entraîner des interruptions de service ou une perte irrévocable de vos données.
  
## <a name="before-you-set-up-customer-key"></a>Avant de configurer la clé client

Avant de commencer, vérifiez que vous disposez des abonnements Azure et des licences M365/O365 appropriés pour votre organisation. Vous devez utiliser des abonnements Azure payants. Les abonnements que vous avez obtenu via des abonnements gratuits, d’évaluation, de parrainages, d’abonnements MSDN et ceux sous support hérité ne sont pas éligibles.

> [!IMPORTANT]
> Les licences M365/O365 valides qui offrent la clé client M365 sont les suivantes :
>
> - Office 365 E5
> - Microsoft 365 E5
> - Microsoft 365 E5 Conformité
> - références SKU de gouvernance Microsoft 365 E5 Information Protection &
> - Microsoft 365 sécurité et conformité pour FLW

Les licences Conformité avancée Office 365 existantes continueront d’être prises en charge.

Pour comprendre les concepts et procédures de cet article, consultez la documentation [Azure Key Vault](/azure/key-vault/). En outre, familiarisez-vous avec les termes utilisés dans Azure, par exemple, [le locataire Azure AD](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant).
  
Si vous avez besoin d’un support supplémentaire au-delà de la documentation, contactez Microsoft Consulting Services (MCS), Premier Field Engineering (PFE) ou un partenaire Microsoft pour obtenir de l’aide. Pour fournir des commentaires sur la clé client, y compris la documentation, envoyez vos idées, suggestions et points de vue à customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Vue d’ensemble des étapes de configuration de la clé client

Pour configurer la clé client, effectuez ces tâches dans l’ordre répertorié. Le reste de cet article fournit des instructions détaillées pour chaque tâche ou fournit des liens vers plus d’informations pour chaque étape du processus.
  
**Dans Azure et Microsoft FastTrack :**
  
Vous effectuerez la plupart de ces tâches en vous connectant à distance à Azure PowerShell. Pour de meilleurs résultats, utilisez la version 4.4.0 ou ultérieure de Azure PowerShell.
  
- [Créer deux abonnements Azure](#create-two-new-azure-subscriptions)

- [Envoyer une demande d’activation de la clé client pour Office 365](#submit-a-request-to-activate-customer-key-for-office-365)

- [Inscrire des abonnements Azure pour utiliser une période de rétention obligatoire](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  Ce processus d’inscription prendra cinq jours ouvrables.
- [Contactez l’alias Microsoft correspondant pour poursuivre le processus](#contact-the-corresponding-microsoft-alias-to-proceed-with-the-process)

- [Créer une Key Vault Azure Premium dans chaque abonnement](#create-a-premium-azure-key-vault-in-each-subscription)

- [Attribuer des autorisations à chaque coffre de clés](#assign-permissions-to-each-key-vault)

- [Vérifiez que la suppression réversible est activée sur vos coffres de clés](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [Ajouter une clé à chaque coffre de clés en créant ou en important une clé](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Vérifier la date d’expiration de vos clés](#verify-expiration-date-of-your-keys)

- [Vérifier le niveau de récupération de vos clés](#check-the-recovery-level-of-your-keys)

- [Sauvegarder azure Key Vault](#back-up-azure-key-vault)

- [Obtenir l’URI pour chaque clé Azure Key Vault](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Effectuer des tâches dans Azure Key Vault et Microsoft FastTrack pour la clé client

Effectuez ces tâches dans Azure Key Vault. Vous devez effectuer ces étapes pour toutes les dep que vous utilisez avec la clé client.
  
### <a name="create-two-new-azure-subscriptions"></a>Créer deux abonnements Azure

La clé client nécessite deux abonnements Azure. En guise de bonne pratique, Microsoft vous recommande de créer des abonnements Azure à utiliser avec la clé client. Les clés Azure Key Vault ne peuvent être autorisées que pour les applications du même locataire Azure Active Directory (Microsoft Azure Active Directory), vous devez créer les nouveaux abonnements à l’aide du même locataire Azure AD que celui utilisé avec votre organisation où les DEP seront affectés. Par exemple, en utilisant votre compte professionnel ou scolaire disposant de privilèges d’administrateur général dans votre organisation. Pour obtenir des instructions détaillées, consultez [S’inscrire à Azure en tant qu’organisation](/azure/active-directory/fundamentals/sign-up-organization).
  
> [!IMPORTANT]
> La clé client nécessite deux clés pour chaque stratégie de chiffrement des données (DEP). Pour ce faire, vous devez créer deux abonnements Azure. En guise de bonne pratique, Microsoft recommande de disposer de membres distincts de votre organisation pour configurer une clé dans chaque abonnement. Vous devez utiliser ces abonnements Azure uniquement pour administrer des clés de chiffrement pour Office 365. Cela protège votre organisation en cas de suppression accidentelle, intentionnelle ou malveillante de l’un de vos opérateurs ou d’une mauvaise gestion des clés dont ils sont responsables.

Il n’existe aucune limite pratique au nombre d’abonnements Azure que vous pouvez créer pour votre organisation. En suivant ces bonnes pratiques, vous réduisez l’impact de l’erreur humaine tout en aidant à gérer les ressources utilisées par la clé client.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Envoyer une demande d’activation de la clé client pour Office 365

Une fois que vous avez créé les deux nouveaux abonnements Azure, vous devez envoyer la demande d’offre de clé client appropriée dans le [portail Microsoft FastTrack](https://fasttrack.microsoft.com/). Les sélections que vous effectuez dans le formulaire d’offre concernant les désignations autorisées au sein de votre organisation sont essentielles et nécessaires pour terminer l’inscription de la clé client. Les agents de ces rôles sélectionnés au sein de votre organisation garantissent l’authenticité de toute demande de révocation et de destruction de toutes les clés utilisées avec une stratégie de chiffrement des données de clé client. Vous devez effectuer cette étape une fois pour chaque type DEP de clé client que vous envisagez d’utiliser pour votre organisation.

**L’équipe FastTrack ne fournit pas d’assistance avec la clé client. Office 365 utilise simplement le portail FastTrack pour vous permettre de soumettre le formulaire et de nous aider à suivre les offres pertinentes pour la clé client. Une fois que vous avez soumis la demande de FastTrack, contactez l’équipe d’intégration de clé client correspondante pour démarrer le processus d’intégration.**
  
Pour soumettre une offre pour activer la clé client, procédez comme suit :
  
1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, connectez-vous au [portail Microsoft FastTrack](https://fasttrack.microsoft.com/).

2. Une fois connecté, sélectionnez le domaine approprié.

3. Pour le domaine sélectionné, choisissez **Déployer** dans la barre de navigation supérieure, puis passez en revue la liste des offres disponibles.

4. Choisissez la carte d’informations pour l’offre qui s’applique à vous :

   - **Plusieurs charges de travail Microsoft 365 :** choisissez **l’aide de la clé de chiffrement de demande pour Microsoft 365** offre.

   - **Exchange Online et Skype Entreprise :** choisissez **l’aide de la clé de chiffrement de demande pour Exchange** offre.

   - **SharePoint fichiers en ligne, OneDrive et Teams :** choisissez **l’aide de la clé de chiffrement de demande pour SharePoint et OneDrive Entreprise** offre.

5. Une fois que vous avez examiné les détails de l’offre, **choisissez Continuer à l’étape 2**.

6. Renseignez tous les détails applicables et les informations demandées sur le formulaire d’offre. Portez une attention particulière à vos sélections pour les responsables de votre organisation que vous souhaitez autoriser à approuver la destruction permanente et irréversible des clés de chiffrement et des données. Une fois que vous avez rempli le formulaire, **choisissez Envoyer**.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Inscrire des abonnements Azure pour utiliser une période de rétention obligatoire

La perte temporaire ou permanente de clés de chiffrement racine peut être perturbatrice, voire catastrophique pour le fonctionnement du service, et peut entraîner une perte de données. Pour cette raison, les ressources utilisées avec la clé client nécessitent une protection renforcée. Toutes les ressources Azure utilisées avec customer key offrent des mécanismes de protection au-delà de la configuration par défaut. Vous pouvez étiqueter ou inscrire des abonnements Azure pour une *période de rétention obligatoire*. Une période de rétention obligatoire empêche l’annulation immédiate et irrévocable de votre abonnement Azure. Les étapes requises pour inscrire des abonnements Azure pour une période de rétention obligatoire nécessitent une collaboration avec l’équipe Microsoft 365. L’exécution de ce processus prendra cinq jours ouvrables. Auparavant, la période de rétention obligatoire était parfois appelée « Ne pas annuler ».
  
> [!IMPORTANT]
> Avant de contacter l’équipe Microsoft 365, vous devez effectuer les étapes suivantes pour **chaque** abonnement Azure que vous utilisez avec la clé client. Vérifiez que le module [Azure PowerShell Az](/powershell/azure/new-azureps-module-az) est installé avant de commencer.

1. Connectez-vous avec Azure PowerShell. Pour obtenir des instructions, consultez [Se connecter avec Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Exécutez l’applet de commande Register-AzProviderFeature pour inscrire vos abonnements afin d’utiliser une période de rétention obligatoire. Effectuez cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

### <a name="contact-the-corresponding-microsoft-alias-to-proceed-with-the-process"></a>Contactez l’alias Microsoft correspondant pour poursuivre le processus

>[!NOTE]
> Avant de contacter l’alias Microsoft correspondant, vérifiez que vous avez effectué vos demandes de FastTrack pour la clé client M365.

- Pour activer la clé client pour l’affectation de DEP à des boîtes aux lettres Exchange Online individuelles, contactez [exock@microsoft.com](mailto:exock@microsoft.com).

- Pour activer la clé client permettant d’affecter des dep pour chiffrer SharePoint contenu en ligne et OneDrive Entreprise (y compris les fichiers Teams) pour tous les utilisateurs locataires, contactez [spock@microsoft.com](mailto:spock@microsoft.com).

- Pour activer la clé client permettant d’affecter des dep pour chiffrer le contenu sur plusieurs charges de travail Microsoft 365 (Exchange Online, Teams, Microsoft Purview Information Protection) pour tous les utilisateurs locataires, contactez [m365-ck@service.microsoft.com](mailto:m365-ck@service.microsoft.com).

- Incluez les informations suivantes dans votre e-mail :

     **Objet** : Clé client pour \<*Your tenant's fully qualified domain name*\>

     **Corps** : incluez les ID de demande de FastTrack et les ID d’abonnement pour **chacun** des services de clé client auxquels vous souhaitez être intégré. Ces ID d’abonnement sont ceux que vous souhaitez terminer la période de rétention obligatoire et la sortie de Get-AzProviderFeature pour chaque abonnement.

Le contrat de niveau de service (SLA) pour la fin de ce processus est de cinq jours ouvrables une fois que Microsoft a été informé (et vérifié) que vous avez inscrit vos abonnements pour utiliser une période de rétention obligatoire.

### <a name="verify-the-status-of-each-your-azure-subscriptions"></a>Vérifier l’état de chacun de vos abonnements Azure

Une fois que vous recevez une notification de Microsoft indiquant que l’inscription est terminée, vérifiez l’état de votre inscription en exécutant la commande Get-AzProviderFeature comme suit. S’il est vérifié, la commande Get-AzProviderFeature retourne la valeur **Registered** for the **Registration State** property. Effectuez cette étape pour **chaque** abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

Pour terminer le processus, exécutez la commande Register-AzResourceProvider. Effectuez cette étape pour **chaque** abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   ```

   ```powershell
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

> [!TIP]
> Avant de passer à l’étape suivante, assurez-vous que « RegistrationState » est défini sur « Inscrit » comme l’image ci-dessous.
>
> ![Période de rétention obligatoire](../media/MandatoryRetentionPeriod.png)

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Créer une Key Vault Azure Premium dans chaque abonnement

Les étapes de création d’un coffre de clés sont documentées dans [Prise en main avec Azure Key Vault](/azure/key-vault/general/overview), qui vous guide tout au long de l’installation et du lancement de Azure PowerShell, de la connexion à votre abonnement Azure, de la création d’un groupe de ressources et de la création d’un coffre de clés dans ce groupe de ressources.
  
Lorsque vous créez un coffre de clés, vous devez choisir une référence SKU : Standard ou Premium. La référence SKU Standard permet de protéger les clés Azure Key Vault avec des logiciels ( il n’existe aucune protection de clé HSM ) et la référence SKU Premium autorise l’utilisation de modules HSM pour la protection des clés Key Vault. Customer Key accepte les coffres de clés qui utilisent l’une ou l’autre référence SKU, bien que Microsoft vous recommande vivement d’utiliser uniquement la référence SKU Premium. Le coût des opérations avec des clés de chaque type est le même. La seule différence de coût est donc le coût par mois pour chaque clé protégée par HSM. Pour plus d’informations, consultez [Key Vault tarification](https://azure.microsoft.com/pricing/details/key-vault/).
  
> [!IMPORTANT]
> Utilisez les coffres de clés de référence SKU Premium et les clés protégées par HSM pour les données de production, et utilisez uniquement des coffres de clés de référence SKU standard et des clés à des fins de test et de validation.
  
Pour chaque service Microsoft 365 avec lequel vous utiliserez la clé client, créez un coffre de clés dans chacun des deux abonnements Azure que vous avez créés. Par exemple, pour permettre à customer Key d’utiliser des dep pour Exchange Online, SharePoint Online et plusieurs scénarios de charge de travail, vous allez créer trois paires de coffres de clés.
  
Utilisez une convention d’affectation de noms pour les coffres de clés qui reflète l’utilisation prévue du dep avec lequel vous allez associer les coffres. Consultez la section Meilleures pratiques ci-dessous pour connaître les recommandations relatives aux conventions d’affectation de noms.
  
Créez un ensemble distinct de coffres couplés pour chaque stratégie de chiffrement des données. Pour Exchange Online, l’étendue d’une stratégie de chiffrement des données est choisie par vous lorsque vous affectez la stratégie à la boîte aux lettres. Une boîte aux lettres ne peut avoir qu’une seule stratégie affectée, et vous pouvez créer jusqu’à 50 stratégies. L’étendue d’une stratégie SharePoint Online inclut toutes les données d’une organisation dans un emplacement géographique ou *géographique*. L’étendue d’une stratégie multi-charge de travail inclut toutes les données des charges de travail prises en charge pour tous les utilisateurs.

La création de coffres de clés nécessite également la création de groupes de ressources Azure, car les coffres de clés ont besoin d’une capacité de stockage (bien que faible) et Key Vault journalisation, si elle est activée, génère également des données stockées. En guise de bonne pratique, Microsoft recommande d’utiliser des administrateurs distincts pour gérer chaque groupe de ressources, avec l’administration alignée sur l’ensemble des administrateurs qui géreront toutes les ressources de clé client associées.
  
### <a name="assign-permissions-to-each-key-vault"></a>Attribuer des autorisations à chaque coffre de clés

Vous devez définir trois ensembles d’autorisations distincts pour chaque coffre de clés, en fonction de votre implémentation. Par exemple, vous devez définir un ensemble d’autorisations pour chacune des opérations suivantes :
  
- **Administrateurs de coffre de** clés qui gèrent quotidiennement votre coffre de clés pour votre organisation. Ces tâches incluent la sauvegarde, la création, l’obtention, l’importation, la liste et la restauration.

  > [!IMPORTANT]
  > L’ensemble d’autorisations attribuées aux administrateurs de coffre de clés n’inclut pas l’autorisation de supprimer des clés. C’est une pratique intentionnelle et importante. La suppression des clés de chiffrement n’est généralement pas effectuée, car cela détruit définitivement les données. Il est recommandé de ne pas accorder cette autorisation aux administrateurs de coffre de clés par défaut. Au lieu de cela, réservez-le aux contributeurs de coffre de clés et attribuez-le uniquement à un administrateur à court terme une fois qu’une compréhension claire des conséquences est comprise.
  
  Pour attribuer ces autorisations à un utilisateur de votre organisation, connectez-vous à votre abonnement Azure avec Azure PowerShell. Pour obtenir des instructions, consultez [Se connecter avec Azure PowerShell](/powershell/azure/authenticate-azureps).

  - Exécutez l’applet de commande Set-AzKeyVaultAccessPolicy pour attribuer les autorisations nécessaires.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Par exemple :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **Contributeurs de coffre de** clés qui peuvent modifier les autorisations sur le Key Vault Azure lui-même. Vous devez modifier ces autorisations au fur et à mesure que les employés quittent ou rejoignent votre équipe. Dans les rares cas où les administrateurs de coffre de clés ont légitimement besoin d’autorisations pour supprimer ou restaurer une clé, vous devez également modifier les autorisations. Ce jeu de contributeurs de coffre de clés doit avoir le rôle **Contributeur** sur votre coffre de clés. Vous pouvez attribuer ce rôle à l’aide d’Azure Resource Manager. Pour obtenir des instructions détaillées, consultez [Utiliser Role-Based Access Control pour gérer l’accès à vos ressources d’abonnement Azure](/azure/active-directory/role-based-access-control-configure). L’administrateur qui crée un abonnement dispose implicitement de cet accès et de la possibilité d’affecter d’autres administrateurs au rôle Contributeur.

- **Autorisations d’Microsoft 365 applications** pour chaque coffre de clés que vous utilisez pour la clé client, vous devez accorder wrapKey, unwrapKey et obtenir des autorisations sur le principal de service Microsoft 365 correspondant.

  Pour accorder l’autorisation à Microsoft 365 principal de service, exécutez l’applet de commande **Set-AzKeyVaultAccessPolicy** à l’aide de la syntaxe suivante :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Où :
   - *le nom du coffre* de clés que vous avez créé.
   - Pour Exchange Online et Skype Entreprise, remplacez *Office 365 appID* par`00000002-0000-0ff1-ce00-000000000000`
   - Pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, remplacez *Office 365 appID* par`00000003-0000-0ff1-ce00-000000000000`
   - Pour une stratégie multi-charge de travail (Exchange, Teams, Microsoft Purview Information Protection) qui s’applique à tous les utilisateurs locataires, remplacez *Office 365 appID* par`c066d759-24ae-40e7-a56f-027002b5d3e4`

  Exemple : Définition des autorisations pour Exchange Online et Skype Entreprise :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Exemple : Définition d’autorisations pour les fichiers SharePoint Online, OneDrive Entreprise et Teams :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

  Vérifiez que *Get, wrapKey et unwrapKey* sont accordés à **chaque** coffre de clés en exécutant l’applet *de commande Get-AzKeyVault* .

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```  

> [!Tip]
> Avant de passer à l’opération, vérifiez que les autorisations sont correctement configurées pour le coffre de clés. *Les autorisations sur les clés* retournent **wrapKey, unwrapKey, get**.
> Veillez à corriger les autorisations sur le service approprié dans lequel vous effectuez l’intégration. Le *nom complet* de chaque service est répertorié ci-dessous :  
  >
  > - Exchange Online et Skype Entreprise : *Office 365 Exchange Online*
  > - fichiers SharePoint Online, OneDrive et Teams : *Office 365 SharePoint Online*
  > - Charges de travail Microsoft 365 multiples : *M365DataAtRestEncryption*
  >  
  > Par exemple, l’extrait de code ci-dessous est un exemple de s’assurer que les autorisations sont configurées pour M365DataAtRestEncryption. L’applet de commande ci-dessous avec un coffre nommé *mmcexchangevault* affiche les champs suivants.
  >
  > ```powershell
  >   Get-AzKeyVault -VaultName mmcexchangevault | fl
  >   ```  
  >
  >
  > ![Chiffrement des chiffrements pour Exchange Online clé client.](../media/KeyVaultPermissions.png)

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>Vérifiez que la suppression réversible est activée sur vos coffres de clés

Lorsque vous pouvez récupérer rapidement vos clés, vous êtes moins susceptible de rencontrer une interruption de service étendue en raison de clés supprimées accidentellement ou malveillantment. Activez cette configuration, appelée suppression réversible, avant de pouvoir utiliser vos clés avec la clé client. L’activation de la suppression réversible vous permet de récupérer des clés ou des coffres dans les 90 jours suivant la suppression sans avoir à les restaurer à partir de la sauvegarde.
  
Pour activer la suppression réversible sur vos coffres de clés, procédez comme suit :
  
1. Connectez-vous à votre abonnement Azure avec Windows PowerShell. Pour obtenir des instructions, consultez [Se connecter avec Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Exécutez l’applet [de commande Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) . Dans cet exemple, le *nom du coffre* est le nom du coffre de clés pour lequel vous activez la suppression réversible :

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. Vérifiez que la suppression réversible est configurée pour le coffre de clés en exécutant l’applet de commande **Get-AzKeyVault** . Si la suppression réversible est correctement configurée pour le coffre de clés, la propriété *Suppression réversible activée* retourne la valeur **True** :

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

> [!TIP]
> Avant de passer à autre chose, assurez-vous que la suppression réversible est activée ? est défini sur « True » comme l’image ci-dessous.
>
> <img src="../media/SoftDeleteEnabled.png" alt="SoftDelete" width="400"/>

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>Ajouter une clé à chaque coffre de clés en créant ou en important une clé

Il existe deux façons d’ajouter des clés à un Key Vault Azure : vous pouvez créer une clé directement dans Key Vault ou importer une clé. La création d’une clé directement dans Key Vault est moins compliquée, mais l’importation d’une clé offre un contrôle total sur la façon dont la clé est générée. Utilisez les clés RSA. Azure Key Vault ne prend pas en charge l’habillage et le déballage avec des touches de courbe elliptique.

Pour obtenir des instructions sur l’ajout d’une clé à chaque coffre, consultez [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey).

 Pour obtenir des instructions détaillées pour créer une clé localement et l’importer dans votre coffre de clés, consultez [Comment générer et transférer des clés protégées par HSM pour Azure Key Vault](/azure/key-vault/keys/hsm-protected-keys). Utilisez les instructions Azure pour créer une clé dans chaque coffre de clés.

### <a name="verify-expiration-date-of-your-keys"></a>Vérifier la date d’expiration de vos clés

Pour vérifier qu’aucune date d’expiration n’est définie pour vos clés, exécutez l’applet de commande [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

La clé client ne peut pas utiliser de clé expirée. Les opérations tentées avec une clé expirée échouent et peuvent entraîner une panne du service. Nous recommandons vivement que les clés utilisées avec la clé client n’aient pas de date d’expiration. Une date d’expiration, une fois définie, ne peut pas être supprimée, mais peut être modifiée à une autre date. Si une clé doit être utilisée avec une date d’expiration définie, remplacez la valeur d’expiration par 12/31/9999. Les clés dont la date d’expiration est définie sur une date autre que le 31/12/9999 ne réussissent pas Microsoft 365 validation.
  
Pour modifier une date d’expiration qui a été définie sur une valeur autre que le 31/12/9999, exécutez l’applet de commande [Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) comme suit :
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Ne définissez pas de dates d’expiration sur les clés de chiffrement que vous utilisez avec la clé client.  

### <a name="check-the-recovery-level-of-your-keys"></a>Vérifier le niveau de récupération de vos clés

Microsoft 365 nécessite que l’abonnement Azure Key Vault soit défini sur Ne pas annuler et que la suppression réversible soit activée pour les clés utilisées par la clé client. Vous pouvez confirmer les paramètres de vos abonnements en examinant le niveau de récupération sur vos clés.
  
Pour vérifier le niveau de récupération d’une clé, dans Azure PowerShell, exécutez l’applet de commande Get-AzKeyVaultKey comme suit :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

> [!Tip]
> Avant de passer à autre chose, si la propriété *Recovery Level* retourne autre chose qu’une valeur **de Recoverable+ProtectedSubscription**, vérifiez que vous avez inscrit la fonctionnalité *MandatoryRetentionPeriodEnabled* sur l’abonnement et que la suppression réversible est activée sur chacun de vos coffres de clés.
>
>    <img src="../media/RecoveryLevel.png" alt="drawing" width="500"/>

### <a name="back-up-azure-key-vault"></a>Sauvegarder azure Key Vault

Immédiatement après la création ou toute modification apportée à une clé, effectuez une sauvegarde et stockez des copies de la sauvegarde, en ligne et hors connexion.
Pour créer une sauvegarde d’une clé Azure Key Vault, exécutez l’applet de commande [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey).

### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Obtenir l’URI pour chaque clé Azure Key Vault

Une fois que vous avez configuré vos coffres de clés et ajouté vos clés, exécutez la commande suivante pour obtenir l’URI de la clé dans chaque coffre de clés. Vous utiliserez ces URI lors de la création et de l’affectation de chaque DEP ultérieurement. Enregistrez donc ces informations dans un emplacement sûr. Exécutez cette commande une fois pour chaque coffre de clés.
  
Dans Azure PowerShell :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez effectué les étapes décrites dans cet article, vous êtes prêt à créer et à affecter des dep. Pour obtenir des instructions, consultez [Gérer la clé client](customer-key-manage.md).

## <a name="related-articles"></a>Articles connexes

- [Chiffrement du service avec la clé client](customer-key-overview.md)

- [Gérer la clé client](customer-key-manage.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Chiffrement de service](office-365-service-encryption.md)
