---
title: Clé client pour Microsoft 365 au niveau du client (préversion publique)
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/17/2020
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
ms.openlocfilehash: eedf0e8c9d56131016bc798af8ae471df3005bdc
ms.sourcegitcommit: 0867495cb02d0b38b439b16bdce97e6eda483ba9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "49712523"
---
# <a name="overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview"></a>Vue d’ensemble de la clé client pour Microsoft 365 au niveau du client (préversion publique)

À l’aide des clés que vous fournissez, vous pouvez créer une stratégie de chiffrement de données (DEP) et l’affecter au client. La DEP chiffre les données sur le client pour ces charges de travail :

- Les messages de conversation Teams (1:1 les conversations, les conversations de groupe, les conversations de réunion et les conversations de canal)
- Les messages multimédia Teams (images, extraits de code, vidéos, images wiki)
- Enregistrements des réunions et des appels aux équipes stockés dans le stockage teams
- Notifications de conversation de teams
- Suggestions de conversation de teams par Cortana
- Messages d’état de teams
- Informations d’utilisateur et de signal pour Exchange Online

Pour Microsoft Teams, la clé client au niveau du client chiffre les nouvelles données à partir du moment où la DEP est affectée au client. La préversion publique ne prend pas en charge le chiffrement des données passées. Pour Exchange Online, la clé client chiffre toutes les données existantes et nouvelles.

Vous pouvez créer plusieurs DEPs par client, mais uniquement une seule DEP à tout moment. Lorsque vous affectez la DEP, le chiffrement démarre automatiquement, mais peut prendre un certain temps en fonction de la taille de votre client.

## <a name="tenant-level-policies-add-broader-control-to-customer-key-for-microsoft-365"></a>Les stratégies de niveau client ajoutent un contrôle plus large à la clé client pour Microsoft 365

Si vous avez déjà configuré la clé de client pour Exchange Online et SharePoint Online, voici comment la nouvelle préversion publique de niveau client s’intègre.

La stratégie de chiffrement au niveau du client que vous créez chiffre toutes les données pour les charges de travail Microsoft teams et Exchange Online dans Microsoft 365. Cette stratégie ne gêne pas les DEPs que vous avez déjà réglées dans la clé client.

Exemples :

Les fichiers Microsoft Teams, ainsi que les enregistrements des réunions et des appels de réunion, qui sont enregistrés dans OneDrive entreprise et SharePoint sont chiffrés par une DEP SharePoint Online. Un seul SharePoint Online DEP chiffre le contenu au sein d’une seule région géographique. La DEP au niveau du client chiffre à nouveau les données chiffrées avec la nouvelle stratégie.

Pour Exchange Online, vous pouvez créer une DEP qui chiffre une ou plusieurs boîtes aux lettres utilisateur à l’aide de la clé client. Lorsque vous créez une stratégie au niveau du client, cette stratégie ne chiffre pas les boîtes aux lettres chiffrées. Toutefois, la clé de niveau client chiffrera les boîtes aux lettres qui ne sont pas affectées par une DEP.

## <a name="set-up-customer-key-at-the-tenant-level-public-preview"></a>Configurer la clé client au niveau du client (préversion publique)

Ces étapes sont similaires mais ne sont pas identiques à celles de la configuration de la clé client au niveau de l’application. Vous devez uniquement utiliser cette préversion publique avec des données de test dans les locataires de test. N’utilisez pas cette version avec des données de production ou dans votre environnement de production. Si vous disposez déjà d’un déploiement de production de la clé client, suivez les étapes ci-dessous pour configurer la clé client au niveau du client dans un environnement de test.

Vous effectuerez la plupart de ces tâches en vous connectant à distance à Azure PowerShell. Pour obtenir de meilleurs résultats, utilisez la version 4.4.0 ou une version ultérieure d’Azure PowerShell.

Avant de commencer, vérifiez les points suivants :

- Vous devez utiliser un compte professionnel ou scolaire qui dispose du rôle d’administrateur de conformité pour configurer la clé client au niveau du client.
- Assurez-vous que vous disposez de la licence appropriée pour votre organisation. Utilisez un abonnement Azure payant facturé à l’aide d’un contrat Enterprise ou d’un fournisseur de services Cloud. Les abonnements Azure achetés à l’aide de l’offre de paiement ou d’une carte de crédit ne sont pas pris en charge pour la clé client. À partir du 1er avril 2020, la clé client dans Office 365 est proposée dans Office 365 E5, M365 E5, M365 E5 conformité et M365 E5 information protection & gouvernance. Office 365 Advanced Compliance SKU n’est plus disponible pour la création de nouvelles licences. Les licences Office 365 Advanced Compliance existantes continueront à être prises en charge. Bien que le service puisse être activé avec au moins une licence sous le client disposant de la licence appropriée, vous devez vous assurer que tous les utilisateurs qui bénéficient du service disposent des licences appropriées. Vous aurez besoin d’une des licences suivantes :

### <a name="create-two-new-azure-subscriptions"></a>Créer deux nouveaux abonnements Azure

La clé client nécessite deux clés pour chaque stratégie de chiffrement de données (DEP). Pour ce faire, vous devez créer deux abonnements Azure. En guise de meilleure pratique, Microsoft recommande que les membres distincts de votre organisation configurent une clé dans chaque abonnement. Utilisez uniquement ces abonnements Azure pour administrer les clés de chiffrement pour Microsoft 365. Cela protège votre organisation si l’un de vos opérateurs supprime accidentellement, intentionnellement ou de manière malveillante ou non des clés dont il est responsable.

Il n’existe pas de limite pratique au nombre d’abonnements Azure que vous pouvez créer pour votre organisation. Le suivi de cette meilleure pratique contribue à réduire l’impact de l’erreur humaine tout en aidant à gérer les ressources utilisées par la clé client.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Enregistrer des abonnements Azure pour utiliser une période de rétention obligatoire

La perte temporaire ou définitive de clés de chiffrement racine peut entraîner des interruptions de service ou des pertes de données. Pour cette raison, les ressources utilisées avec la clé client nécessitent une protection renforcée. Toutes les ressources Azure utilisées avec les mécanismes de protection de l’offre de clé client au-delà de la configuration par défaut. Les abonnements Azure peuvent être balisés ou enregistrés de manière à empêcher toute annulation immédiate et irrévocable. Il s’agit de l’enregistrement pour une période de rétention obligatoire. Les étapes nécessaires à l’inscription des abonnements Azure pour une période de rétention obligatoire nécessitent une collaboration avec Microsoft. Ce processus peut prendre jusqu’à cinq jours ouvrés. Auparavant, il était parfois appelé « ne pas annuler ».
  
Avant de contacter l’équipe Microsoft 365, vous devez effectuer les étapes suivantes pour chaque abonnement Azure que vous utilisez avec la clé client. Assurez-vous que le module [Azure PowerShell AZ](https://docs.microsoft.com/powershell/azure/new-azureps-module-az) est installé avant de commencer.

1. Connectez-vous avec Azure PowerShell. Pour obtenir des instructions, consultez la rubrique [se connecter avec Azure PowerShell](https://docs.microsoft.com/powershell/azure/authenticate-azureps).

2. Exécutez l’applet de commande Register-AzProviderFeature pour enregistrer vos abonnements afin d’utiliser une période de rétention obligatoire. Effectuez cette action pour chaque abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

3. Contactez Microsoft pour finaliser le processus sur [m365ck@microsoft.com](mailto:m365ck@microsoft.com). Incluez les éléments suivants dans votre courrier :

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

Utilisez un préfixe commun pour les coffres clés et incluez une abréviation de l’utilisation et de l’étendue du coffre-fort et des clés. Par exemple, pour le service Contoso où se trouvent les coffres-forts en Amérique du Nord, une paire de noms possible est contoso-O365-NA-VaultA1 et contoso-O365-NA-VaultA2. Les noms de coffre-fort sont des chaînes uniques au sein d’Azure, de sorte que vous devrez peut-être essayer des variantes des noms souhaités au cas où les noms souhaités seraient déjà réclamés par d’autres clients Azure. Une fois configurés, les noms de coffre-fort ne peuvent pas être modifiés, c’est pourquoi il est recommandé d’avoir un plan écrit pour la configuration et d’utiliser une deuxième personne pour vérifier que le plan est exécuté correctement.

Si possible, créez vos coffres dans des régions non couplées. Les régions Azure couplées fournissent une haute disponibilité entre les domaines ayant échoué. Par conséquent, les paires régionales peuvent être considérées comme la région de sauvegarde de chacune d’elles. Cela signifie qu’une ressource Azure placée dans une région bénéficie automatiquement de la tolérance de panne par le biais de la région couplée. Pour cette raison, le choix des régions pour deux coffres utilisés dans une stratégie de chiffrement de données dans laquelle les régions sont couplées signifie que seul un total de deux régions de disponibilité est en cours d’utilisation. La plupart des régions géographiques n’ont que deux régions, de sorte qu’il n’est pas encore possible de sélectionner des régions non couplées. Dans la mesure du possible, choisissez deux régions non couplées pour les deux coffres utilisés avec une stratégie de chiffrement de données. Cette opération bénéficie d’un total de quatre régions de disponibilité. Pour plus d’informations, consultez la rubrique [services de continuité d’activité et de récupération d’urgence (BCDR) : régions couplées Azure](https://docs.microsoft.com/azure/best-practices-availability-paired-regions) pour obtenir la liste actuelle des paires régionales.

### <a name="assign-permissions-to-each-key-vault"></a>Attribuer des autorisations à chaque coffre-fort de clés

Pour chaque coffre-fort de clés, vous devez définir trois ensembles distincts d’autorisations pour la clé client, en fonction de votre implémentation. Par exemple, vous devez définir un ensemble d’autorisations pour chacun des éléments suivants :
  
- **Administrateurs de coffre-fort principal** qui effectueront la gestion quotidienne de votre coffre-fort pour votre organisation. Ces tâches incluent Backup, Create, Get, Import, List et Restore.

  > [!IMPORTANT]
  > Le jeu d’autorisations affectées aux administrateurs de coffre-fort n’inclut pas l’autorisation de suppression de clés. Cette procédure est intentionnelle et pratique importante. La suppression de clés de chiffrement n’est généralement pas effectuée, car cette opération détruit définitivement les données. Nous vous recommandons de ne pas accorder cette autorisation aux administrateurs de coffre-fort par défaut. Au lieu de cela, réservez ceci pour les contributeurs de coffre-fort principal et ne l’attribuez à un administrateur de manière courte qu’une fois qu’une bonne compréhension des conséquences est comprise.
  
  Pour attribuer ces autorisations à un utilisateur de votre organisation, connectez-vous à votre abonnement Azure avec Azure PowerShell. Pour obtenir des instructions, consultez la rubrique [se connecter avec Azure PowerShell](https://docs.microsoft.com/powershell/azure/authenticate-azureps).

   Exécutez l’applet de commande Set-AzKeyVaultAccessPolicy pour attribuer les autorisations nécessaires.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Par exemple :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- Les **contributeurs de coffre-fort de clé** qui peuvent modifier les autorisations sur le coffre-fort des clés Azure. Vous devrez modifier ces autorisations à mesure que les employés quittent ou rejoignent votre équipe, ou dans la situation rare que les administrateurs clés de coffre-fort ont besoin de l’autorisation de supprimer ou de restaurer une clé. Cet ensemble de contributeurs de coffre-fort doit recevoir le rôle de contributeur sur votre coffre-fort de clés. Vous pouvez attribuer ce rôle à l’aide d’Azure Resource Manager. Pour obtenir la procédure détaillée, consultez la rubrique [Use Role-Based Access Control](https://docs.microsoft.com/azure/active-directory/role-based-access-control-configure) pour gérer l’accès à vos ressources d’abonnement Azure. L’administrateur qui crée un abonnement dispose par défaut de cet accès et de la possibilité d’affecter d’autres administrateurs au rôle contributeur.

- **Données Microsoft 365 du service de chiffrement Rest** qui effectue le travail de la clé client au niveau du client. Pour accorder l’autorisation à Microsoft 365, exécutez la cmdlet **Set-AzKeyVaultAccessPolicy** à l’aide de la syntaxe suivante :

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Microsoft 365 appID>
   ```

  Où :

  - *Vault Name* est le nom du coffre-fort de clés que vous avez créé.

  Exemple : pour les données Microsoft 365 du service de chiffrement REST, remplacez  *microsoft 365 AppID* par `c066d759-24ae-40e7-a56f-027002b5d3e4`

  ```powershell
  Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName c066d759-24ae-40e7-a56f-027002b5d3e4
  ```

### <a name="enable-and-then-confirm-soft-delete-on-your-key-vaults"></a>Activer, puis confirmer la suppression logicielle de vos coffres-forts principaux

Lorsque vous pouvez rapidement récupérer vos clés, il est moins probable que vous rencontriez une panne de service étendue en raison de la suppression accidentelle ou malveillante de clés. Activez cette configuration, appelée suppression récupérable, avant de pouvoir utiliser vos clés avec la clé client. L’activation de la suppression douce vous permet de récupérer des clés ou des coffres dans les 90 jours suivant la suppression sans avoir à les restaurer à partir d’une sauvegarde.
  
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

Il existe deux façons d’ajouter des clés à un coffre-fort de clés Azure ; vous pouvez créer une clé directement dans le coffre-fort de clés ou importer une clé. La création d’une clé directement dans le coffre-fort est la méthode moins compliquée, tandis que l’importation d’une clé fournit un contrôle total sur la génération de la clé. Utilisez les clés RSA. Le coffre-fort de clés Azure ne prend pas en charge l’habillage et la déconditionnement avec des courbes elliptiques.
  
Pour créer une clé directement dans votre coffre-fort de clés, exécutez la cmdlet [Add-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/add-azkeyvaultkey) comme suit :
  
```powershell
Add-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Destination <HSM|Software> -KeyOps wrapKey,unwrapKey
```

Où :

- *Vault Name* est le nom du coffre-fort de clés dans lequel vous souhaitez créer la clé.

- *nom* de la clé est le nom que vous souhaitez donner à la nouvelle clé.

  > [!TIP]
  > Clés de nom à l’aide d’une convention d’affectation de noms similaire à celle décrite ci-dessus pour les coffres clés. De cette manière, dans les outils qui affichent uniquement le nom de la clé, la chaîne est auto-descriptive.
  
Si vous avez l’intention de protéger la clé avec un HSM, vérifiez que vous spécifiez **HSM** comme valeur du paramètre _destination_ , sinon, spécifiez **Software**.

Par exemple :
  
```powershell
Add-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -Name Contoso-O365EX-NA-VaultA1-Key001 -Destination HSM -KeyOps wrapKey,unwrapKey
```

### <a name="check-the-recovery-level-of-your-keys"></a>Vérifier le niveau de récupération de vos clés

Microsoft 365 nécessite que le abonnement Azure Key Vault soit défini sur do not Cancel et que les clés utilisées par la clé client aient activé la suppression douce. Vous pouvez vérifier cela en examinant le niveau de récupération de vos clés.
  
Pour vérifier le niveau de récupération d’une clé, dans Azure PowerShell, exécutez l’applet de commande Get-AzKeyVaultKey comme suit :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

Si la propriété de _niveau de récupération_ renvoie une valeur autre que **récupérable + ProtectedSubscription**, vous devez passer en revue cet article et vous assurer que vous avez suivi toutes les étapes pour placer l’abonnement dans la liste ne pas annuler et que vous avez activé la « suppression récupérable » sur chacun de vos coffres clés. Ensuite, envoyez une capture d’écran de la sortie de `(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes` dans un message électronique à m365ck@microsoft.com.

### <a name="back-up-azure-key-vault"></a>Sauvegarder le coffre de clés Azure

Immédiatement après la création ou la modification d’une clé, effectuez une sauvegarde et stockez des copies de la sauvegarde, en ligne et hors connexion. Ne connectez pas les copies hors connexion à un réseau. Au lieu de cela, stockez-les dans un emplacement de stockage physique sécurisé ou commercial. Au moins une copie de la sauvegarde doit être stockée à un emplacement accessible en cas de sinistre. Les objets BLOB de sauvegarde constituent le seul moyen de restaurer le matériel de clé si une clé de coffre-fort de clé est détruite définitivement ou s’il est inopérable. Les clés externes au coffre-fort Azure et qui ont été importées vers le coffre-fort Azure ne sont pas qualifiées de sauvegarde car les métadonnées nécessaires à l’utilisation de la clé par le client n’existent pas avec la clé externe. Seule une sauvegarde effectuée à partir du coffre-fort de clés Azure peut être utilisée pour les opérations de restauration avec la clé client. Par conséquent, il est essentiel de créer une sauvegarde d’Azure Key Vault une fois qu’une clé est chargée ou créée.
  
Pour créer une sauvegarde d’une clé Azure Key Vault, exécutez la cmdlet [Backup-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/backup-azkeyvaultkey) comme suit :

```powershell
Backup-AzKeyVaultKey -VaultName <vault name> -Name <key name>
-OutputFile <filename.backup>
```

Assurez-vous que votre fichier de sortie utilise le suffixe `.backup` .
  
Le fichier de sortie résultant de cette cmdlet est chiffré et ne peut pas être utilisé en dehors du coffre-fort de clés Azure. La sauvegarde ne peut être restaurée qu’à partir de l’abonnement Azure à partir duquel la sauvegarde a été effectuée.
  
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

Dans la sortie, recherchez la stratégie d’accès et, le cas échéant, l’ID d’application Microsoft 365 (GUID). Les trois opérations, Get, wrapKey et unwrapKey, doivent apparaître sous autorisations sur les clés.
  
Si la configuration de la stratégie d’accès est incorrecte, exécutez l’applet de commande Set-AzKeyVaultAccessPolicy comme suit :
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Microsoft 365 appID>
```

Exemple : pour les données Microsoft 365 du service de chiffrement REST, remplacez  *microsoft 365 AppID* par `c066d759-24ae-40e7-a56f-027002b5d3e4`

  ```powershell
  Set-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName c066d759-24ae-40e7-a56f-027002b5d3e4
  ```

Pour vérifier qu’une date d’expiration n’est pas définie pour vos clés, exécutez la cmdlet [Get-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/get-azkeyvault) comme suit :
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

Une clé expirée ne peut pas être utilisée par la clé client et les opérations tentées avec une clé expirée échoueront et provoqueraient une panne de service. Il est vivement recommandé que les clés utilisées avec la clé client n’aient pas de date d’expiration. Une date d’expiration, une fois définie, ne peut pas être supprimée, mais peut être remplacée par une date différente. Si une clé doit être utilisée avec une date d’expiration définie, modifiez la valeur d’expiration sur 12/31/9999. Les clés dont la date d’expiration est définie sur une date autre que 12/31/9999 ne passent pas la validation Microsoft 365.
  
Pour modifier une date d’expiration qui a été définie sur une valeur autre que 12/31/9999, exécutez la cmdlet [Update-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/update-azkeyvaultkey) comme suit :
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Obtenir l’URI de chaque clé Azure Key Vault

Une fois que vous avez effectué toutes les étapes dans Azure pour configurer votre coffre-fort de clés et ajouté vos clés, exécutez la commande suivante pour obtenir l’URI de la clé dans chaque coffre-fort de clés. Vous devrez utiliser ces URI lorsque vous créerez et affecterez chaque DEP plus tard, donc Enregistrez ces informations dans un endroit sûr. N’oubliez pas d’exécuter cette commande une fois pour chaque coffre-fort de clés.
  
Dans Azure PowerShell :
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="set-up-the-customer-key-encryption-policy-for-your-tenant"></a>Configurer la stratégie de chiffrement par clé client pour votre client

Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces applets de commande. Bien que cet article répertorie tous les paramètres des applets de commande, il se peut que vous n’ayez pas accès à certains paramètres s’ils ne sont pas inclus dans les autorisations qui vous sont attribuées. Pour rechercher les autorisations requises pour exécuter une cmdlet ou un paramètre dans votre organisation, voir [Find the permissions required to run any Exchange cmdlet](https://docs.microsoft.com/powershell/exchange/exchange-server/find-exchange-cmdlet-permissions).

### <a name="create-policy"></a>Création d’une stratégie

```powershell
   New-M365DataAtRestEncryptionPolicy [-Name] <String> -AzureKeyIDs <MultiValuedProperty> [-Description <String>] [-Enabled <Boolean>]
```

Description : activez l’administrateur de conformité pour créer une stratégie de chiffrement de données à l’aide de deux clés racines AKV. Une fois créée, une stratégie peut être affectée à l’aide de Set-M365DataAtRestEncryptionPolicy cmdlet. Lors de la première affectation des clés ou de la rotation des clés, la prise d’effet des nouvelles clés peut prendre jusqu’à 24 heures. Si la nouvelle DEP prend effet plus de 24 heures, contactez Microsoft.

Exemple :

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Default_Policy" -AzureKeyIDs "https://contosoWestUSvault01.vault.azure.net/keys/Key_01","https://contosoEastUSvault01.vault.azure.net/keys/Key_02" -Description "Tenant default policy"
```

Paramètres :

| Nom | Description | Facultatif (o/N) |
|--|--|--|
|Nom|Nom convivial de la stratégie de chiffrement des données|N|
|AzureKeyIDs|Spécifie deux valeurs d’URI des clés Azure Key Vault, séparées par une virgule, à associer à la stratégie de chiffrement des données.|N|
|Description|Description de la stratégie de chiffrement des données|N|

### <a name="assign-policy"></a>Affecter une stratégie

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -Policy “<Default_PolicyName or Default_PolicyID>”
```

Description : cette applet de commande est utilisée pour la configuration de la stratégie de chiffrement de données par défaut. Cette stratégie sera utilisée pour chiffrer les données de toutes les charges de travail de prise en charge. 

Exemple :

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -Policy “Tenant default policy”
```

Paramètres :
| Nom | Description | Facultatif (o/N) |
|--|--|--|
-Policy|Spécifie la stratégie de chiffrement de données qui doit être affectée ; Spécifiez le nom de la stratégie ou l’ID de la stratégie.|N|

### <a name="modify-or-refresh-policy"></a>Modifier ou actualiser la stratégie

```powershell
Set-M365DataAtRestEncryptionPolicy [-Identity] < M365DataAtRestEncryptionPolicy DataEncryptionPolicyIdParameter> -Refresh [-Enabled <Boolean>] [-Name <String>] [-Description <String>]
```

Description : l’applet de commande peut être utilisée pour modifier ou actualiser une stratégie existante. Elle peut également être utilisée pour activer ou désactiver une stratégie. Lors de la première affectation des clés ou de la rotation des clés, la prise d’effet des nouvelles clés peut prendre jusqu’à 24 heures. Si la nouvelle DEP prend effet plus de 24 heures, contactez Microsoft.

Exemples :

Désactivez une stratégie de chiffrement de données.

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "NAM Policy" -Enabled $false
```

Actualisez une stratégie de chiffrement de données.

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity “EUR Policy” -Refresh
```

Paramètres :
| Nom | Description | Facultatif (o/N) |
|--|--|--|
|-Identity|Spécifie la stratégie de chiffrement de données à modifier.|N|
|-Actualiser|Utilisez le commutateur Refresh pour mettre à jour la stratégie de chiffrement des données après avoir fait pivoter l’une des clés associées dans le coffre-fort de clés Azure. Il n’est pas nécessaire de spécifier une valeur pour ce commutateur.|v|
|-Enabled|Le paramètre Enabled active ou désactive la stratégie de chiffrement des données. Avant de désactiver une stratégie, vous devez l’annuler à partir de votre client. Les valeurs valides sont les suivantes :</br > $true : la stratégie est activée.</br > $true : la stratégie est activée. Il s’agit de la valeur par défaut.
|v|
|-Name|Le paramètre Name spécifie le nom unique de la stratégie de chiffrement de données.|v
|-Description|Le paramètre Description spécifie une description facultative pour la stratégie de chiffrement de données.|v|

### <a name="get-policy-details"></a>Obtenir les détails de la stratégie

```powershell
Get-M365DataAtRestEncryptionPolicy [-Identity] < M365DataAtRestEncryptionPolicy DataEncryptionPolicyIdParameter>
```

Description : cette cmdlet répertorie toutes les stratégies de chiffrement M365DataAtRest créées pour le client ou les détails d’une stratégie spécifique.

Exemples :

Cet exemple renvoie la liste récapitulative des stratégies de chiffrement M365DatAtRest de l’organisation.

```powershell
Get-M365DataAtRestEncryptionPolicy
```

Cet exemple renvoie des informations détaillées sur la stratégie de chiffrement de données nommée « NAM Policy ».

```powershell
Get-M365DataAtRestEncryptionPolicy -Identity "NAM Policy"
```

Paramètres :

| Nom | Description | Facultatif (o/N) |
|--|--|--|
|-Identity|Spécifie la stratégie de chiffrement de données pour laquelle vous souhaitez répertorier les détails.|v|

### <a name="get-policy-assignment-info"></a>Obtenir des informations sur l’affectation de stratégie

```powershell
Get-M365DataAtRestEncryptionPolicyAssignment
```

Description : cette cmdlet répertorie la stratégie actuellement affectée au client.

## <a name="offboarding-from-customer-key"></a>Par débarquement à partir de la clé client

Si vous devez revenir aux clés gérées par Microsoft, vous pouvez. Lorsque vous débarquement, vos données sont rechiffrées à l’aide du chiffrement par défaut pris en charge par chaque charge de travail individuelle. Par exemple, Exchange Online prend en charge le chiffrement par défaut à l’aide de clés gérées par Microsoft.

Si vous décidez d’débarquement votre client à partir de la clé client au niveau du client, adressez-vous à Microsoft à l’aide de la messagerie électronique pour « désactiver » le service pour le client sur [m365ck@microsoft.com](mailto:m365ck@microsoft.com).

> [!IMPORTANT]
> Par débarquement n’est pas la même chose qu’une purge des données. Une opération de purge des données à la fois-supprime les données de votre organisation de Microsoft 365, par débarquement ne le fait pas. Vous ne pouvez pas effectuer une purge des données pour une stratégie au niveau du client. Pour plus d’informations sur le chemin de purge des données, voir [révoquer vos clés et démarrer le processus de chemin de purge des données](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

## <a name="about-the-availability-key"></a>À propos de la clé de disponibilité

Pour plus d’informations sur la clé de disponibilité, voir [en savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md).

## <a name="key-rotation"></a>Rotation de la clé

Pour plus d’informations sur les touches de rotation ou de roulement utilisées avec la clé client, voir [Roll or Rotate a client Key or an Availability](customer-key-availability-key-roll.md)Key. Lorsque vous mettez à jour la DEP pour utiliser la nouvelle version des clés, vous exécuterez la cmdlet Set-M365DataAtRestEncryptionPolicy comme décrit plus haut dans cet article.

## <a name="related-articles"></a>Articles connexes :

- [Chiffrement du service avec la clé client](customer-key-overview.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Chiffrement de service](office-365-service-encryption.md)
