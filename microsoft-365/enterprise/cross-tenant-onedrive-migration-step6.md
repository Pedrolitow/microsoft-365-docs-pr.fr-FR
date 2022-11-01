---
title: Étape 6 de migration des données utilisateur entre locataires OneDrive
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
recommendations: true
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.subservice: sharepoint-migration
ms.localizationpriority: high
ms.collection:
- SPMigration
- M365-collaboration
- m365initiative-migratetom365
search.appverid: MET150
description: Étape 6 de la fonctionnalité de migration interlocataire OneDrive
ms.openlocfilehash: 6ebf12c11388d35daa4e8261c193af721af88124
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805444"
---
# <a name="step-6-start-a-onedrive-cross-tenant-migration"></a>Étape 6 : Démarrer une migration interlocataire OneDrive

Vous êtes maintenant prêt à démarrer votre migration OneDrive.  Avant de commencer une migration interlocataire, procédez comme suit. 

1. Vérifiez que vous avez vérifié l’état de compatibilité. Si vous voyez un état compatible sur votre locataire source, vous pouvez continuer. Courir:

```powershell
Get-SPOCrossTenantCompatibilityStatus –PartnerCrossTenantHostURL [Target tenant hostname]
```

2. Pour démarrer la migration, un Administration SharePoint Online ou Microsoft 365 Global Administration du locataire source doit exécuter la commande suivante :

```PowerShell
Start-SPOCrossTenantUserContentMove  -SourceUserPrincipalName <…> -TargetUserPrincipalName <…> -TargetCrossTenantHostUrl <…>
```

|Paramètres|Description|
|:-----|:-----|
|SourceUserPrincipalName|Nom d’utilisateur principal de l’utilisateur propriétaire de OneDrive sur le locataire source.|
|TargetUserPrincipalName|Nom d’utilisateur principal de l’utilisateur propriétaire de OneDrive sur le locataire cible.|
|TargetCrossTenantHostUrl|URL de l’hôte interlocataire du locataire cible. Pour rechercher targetCrossTenantHostUrl, exécutez *Get-SPOCrossTenantHostUrl* sur le locataire.|

Exemple :

```Powershell

Start-SPOCrossTenantUserContentMove -SourceUserPrincipalName DiegoS@M365x016651.OnMicrosoft.com -TargetUserPrincipalName
        Test-Diego@M365x946316.OnMicrosoft.com -TargetCrossTenantHostUrl https://m365x946316-my.sharepoint.com/ 

```

Pour planifier une migration ultérieurement, vous pouvez utiliser et ajouter la commande ci-dessus avec l’un des paramètres suivants. 

Ces commandes peuvent être utiles lors de la planification de lots en bloc de migrations OneDrive.  Vous pouvez mettre en file d’attente/migrer jusqu’à 4 000 migrations OneDrive par lot.  Si votre nombre d’utilisateurs dépasse 4 000, créez des lots distincts et planifiez leur exécution une fois le lot actuel presque terminé.

|Paramètre|Description|
|:-----|:-----|
|PreferredMoveBeginDate|La migration commencera probablement à ce moment spécifié. L’heure doit être spécifiée en temps universel coordonné (UTC).|
|PreferredMoveEndDate|La migration sera probablement effectuée à l’heure spécifiée, au mieux. L’heure doit être spécifiée en temps universel coordonné (UTC).|


## <a name="onedrive-status-pre-migration"></a>Prémigration de l’état OneDrive

Avant de commencer la migration, l’état actuel de la source OneDrive des utilisateurs est similaire à l’exemple ci-dessous.  Cet exemple provient du locataire source des utilisateurs, montrant leurs fichiers et dossiers actuels.


:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-status-premigration.png" alt-text="état de la prémigration":::

## <a name="cancelling-a-onedrive-migration"></a>Annulation d’une migration OneDrive

Vous pouvez arrêter la migration interlocataire du OneDrive d’un utilisateur à l’aide de la commande suivante, à condition que la migration ne soit pas en cours ou réussie.

```powershell

Stop-SPOCrossTenantUserContentMove – SourceUserPrincipalName [UPN name of user who you wish to stop]

Stop-SPOCrossTenantUserContentMove – SourceUserPrincipalName DiegoS@M365x016651.OnMicrosoft.com
```

## <a name="determining-current-status-of-a-migration"></a>Détermination de l’état actuel d’une migration

Après avoir démarré votre migration, vous pouvez vérifier son état à l’aide de la commande suivante sur le locataire source OU cible :

**Format de commande source**
```powershell

Get-SPOCrossTenantUserContentMoveState -PartnerCrossTenantHostURL [Target URL]
```
Exemple :

```Powershell
Get-SPOCrossTenantUserContentMoveState -PartnerCrossTenantHostURL  https://m365x946316-my.sharepoint.com/

```

**Commande cible :** 

```powershell

Get-SPOCrossTenantUserContentMoveState -PartnerCrossTenantHostURL [Source URL]
Get-SPOCrossTenantUserContentMoveState -PartnerCrossTenantHostURL  https://m365x016551-my.sharepoint.com/
```

Pour rechercher l’état de la migration d’un utilisateur spécifique, utilisez le paramètre *UserPrincipalName* :

```powershell

Get-SPOCrossTenantUserContentMoveState -PartnerCrossTenantHostURL <PartnerCrossTenantHostURL> -SourceUserPrincipalName <UPN>
Get-SPOUserAndContentMoveState -PartnerCrossTenantHostURL https://m365x946316-my.sharepoint.com -SourceUserPrincipalName DiegoS@M365x016651.OnMicrosoft.com
```

Pour obtenir l’état du déplacement en fonction de l’UPN d’un utilisateur particulier, mais avec plus d’informations, utilisez le paramètre *-Verbose* .

Exemple :

```PowerShell

Get-SPOCrossTenantUserContentMoveState -PartnerCrossTenantHostURL https://ttesttenant-my.sharepoint.com -SourceUserPrincipalName User3@stesttenant.onmicrosoft.com -Verbose 

```


## <a name="migration-states"></a>États de migration


|État|Description|
|:-----|:-----|
|NotStarted|La migration n’a pas encore démarré.|
|Scheduled|La migration se trouve désormais dans la file d’attente et est planifiée pour s’exécuter lorsqu’un emplacement devient disponible.|
|ReadytoTrigger|La migration en est à son étape de préversion et démarrera la migration sous peu.|
|InProgress|La migration est en cours dans l’un des états suivants : </br>-Validation </br>-Sauvegarde </br>-Restaurer </br>-Nettoyage|
|Opération réussie|La migration s’est terminée avec succès.|
|Reportée|La migration n’est peut-être pas terminée et a été reléguée en file d’attente pour une autre passe.|
|Échec |Échec de la migration.|


 
## <a name="post-migration-status-checks"></a>Vérifications de l’état post-migration

**Locataire cible :** Une fois la migration terminée, vérifiez l’état de l’utilisateur sur le locataire cible en vous connectant à son nouveau compte OneDrive. 

**Locataire source :** Étant donné que l’utilisateur a correctement migré vers le locataire cible, il n’a plus de compte OneDrive actif sur la source.


## <a name="step-7-post-migration-steps"></a>Étape 7 : [Étapes post-migration](cross-tenant-onedrive-migration-step7.md)