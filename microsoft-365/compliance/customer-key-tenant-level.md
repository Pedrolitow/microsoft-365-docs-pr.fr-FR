---
title: Clé client pour Microsoft 365 au niveau du client (préversion publique)
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/17/2021
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
description: Découvrez comment configurer la clé client pour toutes les données de votre client Microsoft 365.
ms.openlocfilehash: f50986b4e72808d4a1cd4dc8ee0182eb9c0a2455
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50922688"
---
# <a name="overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview"></a>Vue d’ensemble de la clé client pour Microsoft 365 au niveau du client (prévisualisation publique)

À l’aide des clés que vous fournissez, vous pouvez créer une stratégie de chiffrement de données (DEP) et l’affecter au client. Le PD DEP chiffre les données sur le client pour ces charges de travail :

- Messages de conversation Teams (conversations 1:1, conversations de groupe, conversations de réunion et conversations de canal)
- Messages multimédias Teams (images, extraits de code, messages vidéo, messages audio, images wiki)
- Enregistrements d’appels et de réunions Teams stockés dans le stockage Teams
- Notifications de conversation Teams
- Suggestions de conversation Teams par Cortana
- Messages d’état Teams
- Informations sur l’utilisateur et le signal pour Exchange Online
- Boîtes aux lettres Exchange Online qui ne sont pas déjà chiffrées Au niveau de l’application

Pour Microsoft Teams, la clé client au niveau du client chiffre les nouvelles données à partir du moment où le dep est affecté au client. La prévisualisation publique ne prend pas en charge le chiffrement des données passées. Pour Exchange Online, la clé client chiffre toutes les données existantes et nouvelles.

Vous pouvez créer plusieurs dep par client, mais vous ne pouvez en attribuer qu’un seul à tout moment. Lorsque vous affectez le dep, le chiffrement commence automatiquement, mais peut prendre un certain temps en fonction de la taille de votre client.

## <a name="tenant-level-policies-add-broader-control-to-customer-key-for-microsoft-365"></a>Les stratégies de niveau client ajoutent un contrôle plus large à la clé client pour Microsoft 365

Si vous avez déjà installé la clé client pour Exchange Online et Sharepoint Online, voici comment la nouvelle prévisualisation publique au niveau du client s’intègre.

La stratégie de chiffrement au niveau du client que vous créez chiffre toutes les données pour les charges de travail Microsoft Teams et Exchange Online dans Microsoft 365. Toutefois, pour Exchange Online, si vous avez déjà affecté des dep de clé client à des boîtes aux lettres individuelles, la stratégie au niveau du client ne remplacera pas ces DPS. La stratégie au niveau du client chiffre uniquement les boîtes aux lettres qui ne sont pas déjà affectées à un dep de clé client au niveau de la boîte aux lettres.

Par exemple, les fichiers Microsoft Teams et certains enregistrements d’appels et de réunions Teams enregistrés dans OneDrive Entreprise et SharePoint sont chiffrés par un dep SharePoint Online. Un seul deP SharePoint Online chiffre le contenu au sein d’une seule géo.

## <a name="set-up-customer-key-at-the-tenant-level-public-preview"></a>Configurer la clé client au niveau du client (prévisualisation publique)

Ces étapes sont similaires, mais pas identiques aux étapes de configuration de la clé client au niveau de l’application. Vous devez utiliser cette prévisualisation publique uniquement avec les données de test dans les clients de test. N’utilisez pas cette version avec des données de production ou dans votre environnement de production. Si vous avez déjà un déploiement de production de la clé client, utilisez ces étapes pour configurer la clé client au niveau du client dans un environnement de test. Une fois que vous avez affecté un dep de niveau client à votre client, vous pouvez démarrer le processus de validation et vous m365ck@microsoft.com toute question ou tout problème. Vous trouverez également des étapes de validation documentées dans la prévisualisation publique des instructions de validation pour le chiffrement de données au [repos pour Microsoft 365.](https://aka.ms/CustomerKey/PublicPreviewValidation)

Vous effectuerez la plupart de ces tâches en vous connectant à distance à Azure PowerShell. Pour obtenir de meilleurs résultats, utilisez la version 4.4.0 ou ultérieure d’Azure PowerShell.

Avant de commencer, assurez-vous des choses suivantes :

- Vous devez utiliser un compte professionnel ou scolaire qui a le rôle d’administrateur de conformité pour configurer la clé client au niveau du client.
- Assurez-vous que vous avez la licence appropriée pour votre organisation. Utilisez un abonnement Azure payant facturé à l’aide d’un contrat Entreprise ou d’un fournisseur de services Cloud. Les abonnements Azure achetés à l’aide des plans Payer en cours ou d’une carte de crédit ne sont pas pris en charge pour la clé client. À compter du 1er avril 2020, la clé client dans Office 365 est proposée dans office 365 E5, M365 E5, conformité M365 E5 et M365 E5 informations protection & gouvernance. Office 365 Advanced Compliance SKU n’est plus disponible pour obtenir de nouvelles licences. Les licences De conformité avancée Office 365 existantes continueront d’être prise en charge. Bien que le service puisse être activé avec un minimum d’une licence sous le client qui a la licence appropriée, vous devez toujours vous assurer que tous les utilisateurs qui bénéficient du service ont les licences appropriées.

### <a name="create-two-new-azure-subscriptions"></a>Créer deux nouveaux abonnements Azure

La clé client nécessite deux clés pour chaque stratégie de chiffrement de données (PDN). Pour ce faire, vous devez créer deux abonnements Azure. En tant que meilleure pratique, Microsoft recommande que des membres distincts de votre organisation configurent une clé dans chaque abonnement. Utilisez uniquement ces abonnements Azure pour administrer les clés de chiffrement pour Microsoft 365. Cela protège votre organisation au cas où l’un de vos opérateurs supprime accidentellement, intentionnellement ou malveillantment les clés dont ils sont responsables, ou en cas de mauvaise gestion.

Il n’existe aucune limite pratique au nombre d’abonnements Azure que vous pouvez créer pour votre organisation. Le suivi de cette meilleure pratique permet de minimiser l’impact d’une erreur humaine tout en aidant à gérer les ressources utilisées par la clé client.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Inscrire des abonnements Azure pour utiliser une période de rétention obligatoire

La perte temporaire ou permanente des clés de chiffrement racine peut perturber ou même catastrophique le fonctionnement du service et entraîner la perte de données. Pour cette raison, les ressources utilisées avec la clé client nécessitent une protection forte. Toutes les ressources Azure utilisées avec la clé client offrent des mécanismes de protection au-delà de la configuration par défaut. Les abonnements Azure peuvent être marqués ou enregistrés de manière à empêcher une annulation immédiate et irrévocable. Il s’agit de l’inscription à une période de rétention obligatoire. Les étapes requises pour inscrire des abonnements Azure pour une période de rétention obligatoire nécessitent une collaboration avec Microsoft. Ce processus peut prendre jusqu’à cinq jours ou moins. Auparavant, il était parfois appelé « Ne pas annuler ».
  
Avant de contacter l’équipe Microsoft 365, vous devez effectuer les étapes suivantes pour chaque abonnement Azure que vous utilisez avec la clé client. Assurez-vous que le module [Azure PowerShell Az](/powershell/azure/new-azureps-module-az) est installé avant de commencer.

1. Connectez-vous avec Azure PowerShell. Pour obtenir des instructions, [voir Se connectez avec Azure PowerShell.](/powershell/azure/authenticate-azureps)

2. Exécutez la cmdlet Register-AzProviderFeature pour inscrire vos abonnements afin d’utiliser une période de rétention obligatoire. Effectuez cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

3. Contactez Microsoft pour finaliser le processus à [m365ck@microsoft.com](mailto:m365ck@microsoft.com). Incluez ce qui suit dans votre courrier électronique :

   **Objet**: Clé client pour \<*Your tenant's fully-qualified domain name*\>

   **Corps**: ID d’abonnement pour lesquels vous souhaitez finaliser la période de rétention obligatoire.
   Résultat de la Get-AzProviderFeature pour chaque abonnement.

   Le contrat de niveau de service (SLA) pour la réalisation de ce processus est de cinq jours ou jours, une fois que Microsoft a été informé (et vérifié) que vous avez inscrit vos abonnements pour utiliser une période de rétention obligatoire.

4. Une fois que vous recevez une notification de Microsoft vous avertissant que l’inscription est terminée, vérifiez l’état de votre inscription en exécutant la Get-AzProviderFeature suivante. Si elle est vérifiée, la commande Get-AzProviderFeature renvoie la valeur **Registered** pour la **propriété Registration State.** Effectuez cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

5. Pour terminer le processus, exécutez la commande Register-AzResourceProvider commande. Effectuez cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Créer un coffre de clés Azure premium dans chaque abonnement

Les étapes de création d’un coffre de clés sont documentées dans La mise en route [d’Azure Key Vault,](/azure/key-vault/general/overview)qui vous guide tout au long de l’installation et du lancement d’Azure PowerShell, de la connexion à votre abonnement Azure, de la création d’un groupe de ressources et de la création d’un coffre de clés dans ce groupe de ressources.
  
Lorsque vous créez un coffre de clés, vous devez choisir une référence (SKU) : Standard ou Premium. La référence SKU standard permet de protéger les clés Azure Key Vault avec des logiciels (il n’existe pas de protection de clé de module de sécurité matérielle (HSM) ) et la référence SKU Premium permet d’utiliser des HSM pour la protection des clés de coffre de clés. La clé client accepte les coffres de clés qui utilisent l’une ou l’autre référence (SKU), bien que Microsoft recommande vivement d’utiliser uniquement la référence SKU Premium. Le coût des opérations avec des clés de l’un ou l’autre type est le même, donc la seule différence de coût est le coût par mois pour chaque clé protégée par HSM. Pour plus [d’informations,](https://azure.microsoft.com/pricing/details/key-vault/) voir la tarification du coffre de clés.
  
> [!IMPORTANT]
> Utilisez les coffres de clés SKU Premium et les clés protégées par HSM pour les données de production, et utilisez uniquement les clés et coffres de clés SKU standard à des fins de test et de validation.

Utilisez un préfixe commun pour les coffres de clés et incluez une abréviation de l’utilisation et de l’étendue du coffre de clés et des clés. Par exemple, pour le service Contoso où les coffres seront situés en Amérique du Nord, une paire de noms possible est Contoso-O365-NA-VaultA1 et Contoso-O365-NA-VaultA2. Les noms de coffre sont des chaînes globalement uniques dans Azure. Par conséquent, vous devrez peut-être essayer les variantes de vos noms souhaités au cas où les noms souhaités se se trouveraient déjà revendiqués par d’autres clients Azure. Une fois configurés, les noms des coffres ne peuvent pas être modifiés. Il est donc préférable d’avoir un plan écrit pour l’installation et d’utiliser une deuxième personne pour vérifier que le plan est exécuté correctement.

Si possible, créez vos coffres dans des régions non couplées. Les régions Azure couplées fournissent une haute disponibilité entre les domaines de défaillance de service. Par conséquent, les paires régionales peuvent être pensés comme la région de sauvegarde l’une de l’autre. Cela signifie qu’une ressource Azure placée dans une région gagne automatiquement en tolérance de pannes via la région couplée. Pour cette raison, le choix de régions pour deux coffres utilisés dans une stratégie de chiffrement de données dans laquelle les régions sont couplées signifie que seules deux régions de disponibilité sont en cours d’utilisation. La plupart des zones géographiques ne comptent que deux régions. Il n’est donc pas encore possible de sélectionner des régions non couplées. Si possible, choisissez deux régions non couplées pour les deux coffres utilisés avec une stratégie de chiffrement de données. Cela bénéficie d’un total de quatre régions de disponibilité. Pour plus d’informations, voir Continuité d’activité et récupération d’urgence [(BCDR)](/azure/best-practices-availability-paired-regions) : Régions couplées Azure pour obtenir la liste actuelle des paires régionales.

### <a name="assign-permissions-to-each-key-vault"></a>Attribuer des autorisations à chaque coffre de clés

Pour chaque coffre de clés, vous devez définir trois ensembles distincts d’autorisations pour la clé client, en fonction de votre implémentation. Par exemple, vous devez définir un ensemble d’autorisations pour chacune des autorisations suivantes :
  
- **Administrateurs de coffre de clés** qui effectueront la gestion quotidienne de votre coffre de clés pour votre organisation. Ces tâches incluent la sauvegarde, la création, l’importation, la liste et la restauration.

  > [!IMPORTANT]
  > L’ensemble des autorisations attribuées aux administrateurs de coffre de clés n’inclut pas l’autorisation de supprimer des clés. Cette pratique est intentionnelle et importante. La suppression des clés de chiffrement n’est généralement pas effectuée, car cela détruit définitivement les données. En tant que meilleure pratique, n’accordez pas cette autorisation aux administrateurs de coffre de clés par défaut. Au lieu de cela, réservez-le aux contributeurs de coffre de clés et affectez-le uniquement à un administrateur à court terme une fois que vous comprenez clairement les conséquences.
  
  Pour attribuer ces autorisations à un utilisateur de votre organisation, connectez-vous à votre abonnement Azure avec Azure PowerShell. Pour obtenir des instructions, [voir Se connectez avec Azure PowerShell.](/powershell/azure/authenticate-azureps)

   Exécutez lSet-AzKeyVaultAccessPolicy cmdlet pour attribuer les autorisations nécessaires.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Par exemple :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **Contributeurs de coffre de clés** qui peuvent modifier les autorisations sur le coffre de clés Azure lui-même. Vous devrez modifier ces autorisations lorsque les employés quittent ou rejoignent votre équipe, ou dans les rares cas où les administrateurs de coffre de clés ont légitimement besoin d’autorisation pour supprimer ou restaurer une clé. Ce jeu de contributeurs de coffre de clés doit avoir le rôle Collaborateur sur votre coffre de clés. Vous pouvez attribuer ce rôle à l’aide d’Azure Resource Manager. Pour obtenir la procédure détaillée, voir [Utiliser Role-Based contrôle d’accès](/azure/active-directory/role-based-access-control-configure) pour gérer l’accès à vos ressources d’abonnement Azure. L’administrateur qui crée un abonnement dispose de cet accès par défaut et de la possibilité d’affecter d’autres administrateurs au rôle collaborateur.

- Service de chiffrement des données **Microsoft 365 au repos** qui fait le travail de la clé client au niveau du client. Pour accorder l’autorisation à Microsoft 365, exécutez l’cmdlet **Set-AzKeyVaultAccessPolicy** à l’aide de la syntaxe suivante :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Microsoft 365 appID>
   ```

  Où :

  - *Le nom du* coffre est le nom du coffre de clés que vous avez créé.

  Exemple : pour le service de chiffrement de données Microsoft 365 au repos, remplacez  *l’appID Microsoft 365* par `c066d759-24ae-40e7-a56f-027002b5d3e4`

  ```powershell
  Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName c066d759-24ae-40e7-a56f-027002b5d3e4
  ```

### <a name="enable-and-then-confirm-soft-delete-on-your-key-vaults"></a>Activer, puis confirmer la suppression possible sur vos coffres de clés

Lorsque vous pouvez récupérer rapidement vos clés, vous êtes moins susceptible d’être en panne de service étendue en raison de clés supprimées accidentellement ou malveillantment. Activez cette configuration, appelée suppression possible, avant de pouvoir utiliser vos clés avec la clé client. L’activation de la suppression possible vous permet de récupérer des clés ou des coffres dans les 90 jours suivant la suppression sans avoir à les restaurer à partir d’une sauvegarde.
  
Pour activer la suppression possible sur vos coffres de clés, complétez les étapes suivantes :
  
1. Connectez-vous à votre abonnement Azure avec Windows PowerShell. Pour obtenir des instructions, [voir Se connectez avec Azure PowerShell.](/powershell/azure/authenticate-azureps)

2. Exécutez [l’cmdlet Get-AzKeyVault.](/powershell/module/az.keyvault/get-azkeyvault) Dans cet exemple, le *nom du coffre est* le nom du coffre de clés pour lequel vous activer la suppression possible :

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
  
Pour créer une clé directement dans votre coffre de clés, exécutez la cmdlet [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey) comme suit :
  
```powershell
Add-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Destination <HSM|Software> -KeyOps wrapKey,unwrapKey
```

Où :

- *Le nom du* coffre est le nom du coffre de clés dans lequel vous souhaitez créer la clé.

- *est* le nom que vous souhaitez donner à la nouvelle clé.

  > [!TIP]
  > Nommez les clés à l’aide d’une convention d’attribution de noms similaire à celle décrite ci-dessus pour les coffres de clés. Ainsi, dans les outils qui n’indiquent que le nom de la clé, la chaîne est auto-décrivante.
  
Si vous avez l’intention de protéger la clé avec un HSM, veillez à spécifier **HSM** comme valeur du paramètre _Destination,_ sinon, spécifiez **Software**.

Par exemple :
  
```powershell
Add-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -Name Contoso-O365EX-NA-VaultA1-Key001 -Destination HSM -KeyOps wrapKey,unwrapKey
```

### <a name="check-the-recovery-level-of-your-keys"></a>Vérifier le niveau de récupération de vos clés

Microsoft 365 exige que l’abonnement Azure Key Vault soit réglé sur Ne pas annuler et que la suppression possible soit activée sur les clés utilisées par la clé client. Vous pouvez le confirmer en regardant le niveau de récupération sur vos clés.
  
Pour vérifier le niveau de récupération d’une clé, dans Azure PowerShell, exécutez l'Get-AzKeyVaultKey cmdlet comme suit :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

Si la propriété _Recovery Level_ renvoie autre chose qu’une valeur **récupérable+ ProtectedSubscription**, vous devez consulter cet article et vous assurer que vous avez suivi toutes les étapes pour placer l’abonnement dans la liste Ne pas annuler et que vous avez activé la « suppression possible » sur chacun de vos coffres de clés. Ensuite, envoyez une capture d’écran de la sortie de `(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes` l’e-mail m365ck@microsoft.com.

### <a name="back-up-azure-key-vault"></a>Back up Azure Key Vault

Immédiatement après la création ou toute modification d’une clé, effectuez une sauvegarde et stockez des copies de la sauvegarde, à la fois en ligne et hors connexion. Ne connectez pas les copies hors connexion à un réseau. Au lieu de cela, stockez-les dans une installation de stockage physique sécurisée ou commerciale. Au moins une copie de la sauvegarde doit être stockée dans un emplacement accessible en cas d’urgence. Les objets blob de sauvegarde sont le seul moyen de restaurer le matériel de clé si une clé de coffre de clés doit être définitivement détruite ou rendue inopérante. Les clés qui sont externes à Azure Key Vault et qui ont été importées dans Azure Key Vault ne sont pas éligibles en tant que sauvegarde, car les métadonnées nécessaires pour que la clé client utilise la clé n’existent pas avec la clé externe. Seule une sauvegarde provenant d’Azure Key Vault peut être utilisée pour les opérations de restauration avec la clé client. Par conséquent, il est essentiel d’effectuer une sauvegarde d’Azure Key Vault une fois qu’une clé est téléchargée ou créée.
  
Pour créer une sauvegarde d’une clé Azure Key Vault, exécutez l’cmdlet [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey) comme suit :

```powershell
Backup-AzKeyVaultKey -VaultName <vault name> -Name <key name>
-OutputFile <filename.backup>
```

Assurez-vous que votre fichier de sortie utilise le `.backup` suffixe.
  
Le fichier de sortie résultant de cette cmdlet est chiffré et ne peut pas être utilisé en dehors d’Azure Key Vault. La sauvegarde peut être restaurée uniquement dans l’abonnement Azure à partir duquel la sauvegarde a été prise.
  
Par exemple :
  
```powershell
Backup-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -Name Contoso-O365EX-NA-VaultA1-Key001 -OutputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

### <a name="validate-azure-key-vault-configuration-settings"></a>Valider les paramètres de configuration d’Azure Key Vault

L’utilisation de la validation avant l’utilisation de clés dans une PED est facultative, mais vivement recommandée. En particulier, si vous utilisez des étapes pour configurer vos clés et coffres autres que ceux décrits dans cette rubrique, vous devez valider l’état de vos ressources Azure Key Vault avant de configurer la clé client.
  
Pour vérifier que les opérations get, wrapKey et unwrapKey sont activées sur vos clés :
  
Exécutez [l’cmdlet Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
```powershell
Get-AzKeyVault -VaultName <vault name>
```

Dans la sortie, recherchez la stratégie d’accès et l’ID d’application Microsoft 365 (GUID) selon le cas. Les trois opérations, get, wrapKey et unwrapKey, doivent être affichées sous Autorisations sur les clés.
  
Si la configuration de la stratégie d’accès est incorrecte, exécutez la cmdlet Set-AzKeyVaultAccessPolicy suivante :
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Microsoft 365 appID>
```

Exemple : pour le service de chiffrement de données Microsoft 365 au repos, remplacez  *l’appID Microsoft 365* par `c066d759-24ae-40e7-a56f-027002b5d3e4`

  ```powershell
  Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName c066d759-24ae-40e7-a56f-027002b5d3e4
  ```

Pour vérifier qu’une date d’expiration n’est pas définie pour vos clés, exécutez la cmdlet [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

Une clé expirée ne peut pas être utilisée par la clé client et les opérations tentées avec une clé expirée échouent et peuvent entraîner une panne du service. Nous vous recommandons vivement de ne pas avoir de date d’expiration pour les clés utilisées avec la clé client. Une date d’expiration, une fois définie, ne peut pas être supprimée, mais peut être modifiée à une autre date. Si vous devez utiliser une clé dont la date d’expiration est définie, définissez la valeur d’expiration sur 31/12/9999. Les clés dont la date d’expiration est définie sur une date autre que le 31/12/9999 ne sont pas validées par Microsoft 365.
  
Pour modifier une date d’expiration qui a été définie sur une valeur autre que le 31/12/9999, exécutez la cmdlet [Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) comme suit :
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Obtenir l’URI de chaque clé Azure Key Vault

Une fois que vous avez effectué toutes les étapes dans Azure pour configurer vos coffres de clés et ajouté vos clés, exécutez la commande suivante pour obtenir l’URI de la clé dans chaque coffre de clés. Vous devrez utiliser ces URIs lorsque vous créerez et affecterez chaque deP ultérieurement, donc enregistrez ces informations dans un endroit sûr. N’oubliez pas d’exécuter cette commande une fois pour chaque coffre de clés.
  
Dans Azure PowerShell :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="set-up-the-customer-key-encryption-policy-for-your-tenant"></a>Configurer la stratégie de chiffrement de clé client pour votre client

Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces cmdlets. Bien que cet article répertorie tous les paramètres des cmdlets, vous n’avez peut-être pas accès à certains paramètres s’ils ne sont pas inclus dans les autorisations qui vous sont attribuées. Pour rechercher les autorisations requises pour exécuter une cmdlet ou un paramètre dans votre organisation, voir [Find the permissions required to run any Exchange cmdlet](/powershell/exchange/exchange-server/find-exchange-cmdlet-permissions).

### <a name="create-policy"></a>Création d’une stratégie

```powershell
   New-M365DataAtRestEncryptionPolicy [-Name] <String> -AzureKeyIDs <MultiValuedProperty> [-Description <String>]
```

Description : permettre à l’administrateur de conformité de créer une stratégie de chiffrement de données (DEP) à l’aide de deux clés racine AKV. Une fois créée, une stratégie peut être affectée à l’aide Set-M365DataAtRestEncryptionPolicyAssignment cmdlet. Lors de la première affectation de touches ou après la rotation des touches, l’application des nouvelles touches peut prendre jusqu’à 24 heures. Si le nouveau PD DEP prend plus de 24 heures pour prendre effet, contactez Microsoft.

Exemple :

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Default_Policy" -AzureKeyIDs "https://contosoWestUSvault01.vault.azure.net/keys/Key_01","https://contosoEastUSvault01.vault.azure.net/keys/Key_02" -Description "Tenant default policy"
```

Paramètres :

| Nom | Description | Facultatif (Y/N) |
|----------|----------|---------|
|Nom|Nom convivial de la stratégie de chiffrement de données|N|
|AzureKeyIDs|Spécifie deux valeurs d’URI des clés Azure Key Vault, séparées par une virgule, à associer à la stratégie de chiffrement de données|N|
|Description|Description de la stratégie de chiffrement des données|N|

### <a name="assign-policy"></a>Affecter une stratégie

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "<Default_PolicyName or Default_PolicyID>"
```

Description : cette cmdlet est utilisée pour configurer la stratégie de chiffrement de données par défaut. Cette stratégie sera utilisée pour chiffrer ensuite les données sur toutes les charges de travail de prise en charge. 

Exemple :

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Default_PolicyName"
```

Paramètres :

| Nom | Description | Facultatif (Y/N) |
|----------|----------|---------|
-DataEncryptionPolicy|Spécifie la stratégie de chiffrement de données à attribuer ; spécifiez le nom de la stratégie ou l’ID de stratégie.|N|

### <a name="modify-or-refresh-policy"></a>Modifier ou actualiser une stratégie

```powershell
Set-M365DataAtRestEncryptionPolicy [-Identity] <M365DataAtRestEncryptionPolicy DataEncryptionPolicyIdParameter> -Refresh [-Enabled <Boolean>] [-Name <String>] [-Description <String>]
```

Description : la cmdlet peut être utilisée pour modifier ou actualiser une stratégie existante. Il peut également être utilisé pour activer ou désactiver une stratégie. Lors de la première affectation de touches ou après la rotation des touches, l’application des nouvelles touches peut prendre jusqu’à 24 heures. Si le nouveau PD DEP prend plus de 24 heures pour prendre effet, contactez Microsoft.

Exemples :

Désactivez une stratégie de chiffrement de données.

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "NAM Policy" -Enabled $false
```

Actualisez une stratégie de chiffrement de données.

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "EUR Policy" -Refresh
```

Paramètres :

| Nom | Description | Facultatif (Y/N) |
|----------|----------|---------|
|-Identity|Spécifie la stratégie de chiffrement de données à modifier.|N|
|-Refresh|Utilisez le commutateur Actualiser pour mettre à jour la stratégie de chiffrement des données après avoir fait pivoter l’une des clés associées dans azure Key Vault. Il n’est pas nécessaire de spécifier une valeur pour ce commutateur.|v|
|-Enabled|Le paramètre Enabled active ou désactive la stratégie de chiffrement des données. Avant de désactiver une stratégie, vous devez la désattribuer à votre client. Les valeurs valides sont les suivantes :</br > $true : la stratégie est activée</br > $true : la stratégie est activée. Il s’agit de la valeur par défaut.
|v|
|-Name|Le paramètre Name spécifie le nom unique de la stratégie de chiffrement de données.|v|
|-Description|Le paramètre Description spécifie une description facultative pour la stratégie de chiffrement de données.|v|

### <a name="get-policy-details"></a>Obtenir les détails de la stratégie

```powershell
Get-M365DataAtRestEncryptionPolicy [-Identity] <M365DataAtRestEncryptionPolicy DataEncryptionPolicyIdParameter>
```

Description : cette cmdlet répertorie toutes les stratégies de chiffrement M365DataAtRest créées pour le client ou des détails sur une stratégie spécifique.

Exemples :

Cet exemple renvoie une liste récapitulatif des stratégies de chiffrement M365DatRest dans l’organisation.

```powershell
Get-M365DataAtRestEncryptionPolicy
```

Cet exemple renvoie des informations détaillées sur la stratégie de chiffrement de données nommée « NAM Policy ».

```powershell
Get-M365DataAtRestEncryptionPolicy -Identity "NAM Policy"
```

Paramètres :

| Nom | Description | Facultatif (Y/N) |
|----------|----------|---------|
|-Identity|Spécifie la stratégie de chiffrement de données dont vous souhaitez obtenir la liste des détails.|v|

### <a name="get-policy-assignment-info"></a>Obtenir les informations d’attribution de stratégie

```powershell
Get-M365DataAtRestEncryptionPolicyAssignment
```

Description : cette cmdlet répertorie la stratégie actuellement attribuée au client.

## <a name="offboarding-from-customer-key"></a>Offboarding from Customer Key

Si vous devez revenir aux clés gérées par Microsoft, vous pouvez le faire. Lorsque vous déboardez, vos données sont re-chiffrées à l’aide du chiffrement par défaut pris en charge par chaque charge de travail individuelle. Par exemple, Exchange Online prend en charge le chiffrement par défaut à l’aide de clés gérées par Microsoft.

Si vous avez décidé de désinserriser votre client de la clé client au niveau du client, contactez Microsoft avec une demande par courrier électronique pour « désactiver » le service pour le client à [l’adresse m365ck@microsoft.com](mailto:m365ck@microsoft.com).

> [!IMPORTANT]
> Laboarding n’est pas la même chose qu’une purge de données. Une purge des données supprime définitivement les données de votre organisation de Microsoft 365, ce qui n’est pas le cas de la suppression de laboarding. Vous ne pouvez pas effectuer de purge de données pour une stratégie au niveau du client. Pour plus d’informations sur le chemin d’accès de la purge des données, voir [Révoquer vos clés et démarrer le processus de purge des données.](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process)

## <a name="about-the-availability-key"></a>À propos de la clé de disponibilité

Pour plus d’informations sur la clé de disponibilité, voir [En savoir plus sur la clé de disponibilité.](customer-key-availability-key-understand.md)

## <a name="key-rotation"></a>Rotation de touche

Pour plus d’informations sur les touches de rotation ou de rotation utilisées avec la clé client, voir [Roll or rotate a Customer Key or an availability key](customer-key-availability-key-roll.md). Lorsque vous mettez à jour le deP pour utiliser la nouvelle version des clés, vous exécutez la cmdlet Set-M365DataAtRestEncryptionPolicy comme décrit plus haut dans cet article.

## <a name="related-articles"></a>Articles connexes :

- [Chiffrement du service avec la clé client](customer-key-overview.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Chiffrement de service](office-365-service-encryption.md)