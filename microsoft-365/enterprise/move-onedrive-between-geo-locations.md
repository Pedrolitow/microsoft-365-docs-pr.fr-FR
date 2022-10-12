---
title: Déplacer un site OneDrive vers un autre emplacement géographique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Recherchez des informations sur le déplacement d’un site OneDrive vers un autre emplacement géographique, notamment la planification des déplacements de site et la communication des attentes aux utilisateurs.
ms.openlocfilehash: bafe97fd1dc049b1a9fbb0bdcc2d9d1660baead4
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68536541"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Déplacer un site OneDrive vers un autre emplacement géographique

Avec le déplacement géographique OneDrive, vous pouvez déplacer oneDrive d’un utilisateur vers un autre emplacement géographique. Le déplacement géographique OneDrive est effectué par l’administrateur SharePoint Online ou l’administrateur général Microsoft 365. Avant de commencer un déplacement géographique OneDrive, veillez à informer l’utilisateur dont OneDrive est déplacé et à lui recommander de fermer tous les fichiers pendant la durée du déplacement. (Si un document est ouvert à l’aide du client Office pendant le déplacement, le document doit être enregistré au nouvel emplacement à la fin du déplacement.) Le déplacement peut être planifié pour une heure ultérieure, si vous le souhaitez.

Le service OneDrive utilise Stockage Blob Azure pour stocker du contenu. L’objet blob de stockage associé au OneDrive de l’utilisateur sera déplacé de la source vers l’emplacement géographique de destination dans les 40 jours suivant la mise à la disposition de l’utilisateur de OneDrive de destination. L’accès au OneDrive de l’utilisateur est restauré dès que la destination OneDrive est disponible.

Pendant la fenêtre de déplacement géographique OneDrive (environ 2 à 6 heures), onedrive de l’utilisateur est défini sur lecture seule. L’utilisateur peut toujours accéder à ses fichiers via l’application Synchronisation OneDrive ou son site OneDrive dans SharePoint Online. Une fois le déplacement géographique OneDrive terminé, l’utilisateur est automatiquement connecté à son OneDrive à l’emplacement géographique de destination lorsqu’il accède à OneDrive dans le lanceur d’applications Microsoft 365. L’application de synchronisation commence automatiquement la synchronisation à partir du nouvel emplacement.

Les procédures décrites dans cet article nécessitent le [module Microsoft SharePoint Online PowerShell](https://www.microsoft.com/download/details.aspx?id=35588).

## <a name="communicating-to-your-users"></a>Communication avec vos utilisateurs

When moving OneDrive sites between geo locations, it's important to communicate to your users what to expect. This can help reduce user confusion and calls to your help desk. Email your users before the move and let them know the following information:

- La date de début prévue du déplacement et la durée attendue de l’opération.
- L’emplacement géographique vers lequel est déplacé leur espace OneDrive et l’URL permettant d’accéder au nouvel emplacement.
- Conseillez-leur de fermer leurs fichiers et de ne pas y apporter de modifications lors du déplacement.
- Le partage et les autorisations de fichiers ne sont modifiés par la migration.
- Présentez-leur l’[expérience utilisateur dans un environnement multigéographique](multi-geo-user-experience.md).

N’oubliez pas d’envoyer un courrier électronique à vos utilisateurs une fois le déplacement terminé pour les avertir qu’ils peuvent reprendre leur travail dans OneDrive.

## <a name="scheduling-onedrive-site-moves"></a>Planification de déplacements de site OneDrive

You can schedule OneDrive site moves in advance (described later in this article). We recommend that you start with a small number of users to validate your workflows and communication strategies. Once you are comfortable with the process, you can schedule moves as follows:

- Vous pouvez planifier jusqu’à 4 000 déplacements à la fois.
- Lorsque les déplacements commencent, vous pouvez planifier plus d’informations, avec un maximum de 4 000 déplacements dans la file d’attente et à un moment donné.
- La taille maximale d’un élément pouvant être déplacé par OneDrive est de 1 téraoctet (1 to).

## <a name="moving-a-onedrive-site"></a>Déplacement d’un site OneDrive

Pour effectuer un déplacement géographique OneDrive, l’administrateur client doit d’abord définir l’emplacement de données préféré (PDL) de l’utilisateur sur l’emplacement géographique approprié. Une fois le fichier PDL défini, attendez au moins 24 heures que la mise à jour PDL se synchronise entre les emplacements géographiques avant de commencer le déplacement géographique OneDrive.

Lorsque vous utilisez les applets de commande de déplacement géographique, connectez-vous au service SPO à l’emplacement géographique OneDrive actuel de l’utilisateur, à l’aide de la syntaxe suivante :

```powershell
Connect-SPOService -url https://<tenantName>-admin.sharepoint.com
```

Par exemple : pour déplacer OneDrive de l’utilisateur « Matt@contosoenergy.onmicrosoft.com », connectez-vous au centre de Administration EUR SharePoint, car OneDrive de l’utilisateur se trouve à l’emplacement géographique EUR :

```powershell
Connect-SPOService -url https://contosoenergyeur-admin.sharepoint.com
```

![Capture d’écran de la fenêtre PowerShell montrant l’applet de commande connect-sposervice.](../media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>Validation de l’environnement

Avant de commencer un déplacement géographique OneDrive, nous vous recommandons de valider l’environnement.

Pour vous assurer que tous les emplacements géographiques sont compatibles, exécutez :

```powershell
Get-SPOGeoMoveCrossCompatibilityStatus
```

Cela a pour effet d’afficher les emplacements géographiques et d’indiquer si leur environnement est compatible avec l’emplacement géographique cible. Si un emplacement géographique est incompatible, cela signifie qu’une mise à jour est en cours à cet emplacement. Réessayez dans quelques jours.

Si un OneDrive contient, par exemple, un sous-site, il ne peut pas être déplacé. Vous pouvez utiliser la cmdlet Start-SPOUserAndContentMove avec le paramètre -ValidationOnly pour contrôler si le site OneDrive peut être déplacé :

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly
```

This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.

## <a name="start-a-onedrive-geo-move"></a>Démarrer un déplacement géographique OneDrive

Pour démarrer le déplacement, exécutez :

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>
```

À l’aide de ces paramètres :

- _UserPrincipalName_ : UPN de l’utilisateur dont le site OneDrive est déplacé.
- _DestinationDataLocation_ : Geo-Location où onedrive doit être déplacé. Cela doit être identique à l’emplacement de données préféré de l’utilisateur.

Par exemple, pour déplacer le site OneDrive de matt@contosoenergy.onmicrosoft.com de l’emplacement EUR à AUS, exécutez :

```powershell
Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS
```

![Capture d’écran de la fenêtre PowerShell montrant Start-SPOUserAndContentMove cmdlet.](../media/move-onedrive-between-geo-locations-image2.png)

Pour planifier un déplacement géographique à un autre moment, utilisez l’un des paramètres suivants :

- _PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).
- _PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).

## <a name="cancel-a-onedrive-geo-move"></a>Annuler un déplacement géographique OneDrive

Vous pouvez arrêter le déplacement géographique du OneDrive d’un utilisateur, à condition que le déplacement ne soit pas en cours ou terminé à l’aide de l’applet de commande :

```powershell
Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>
```

où _UserPrincipalName_ est l’UPN de l’utilisateur dont vous souhaitez arrêter le déplacement du site OneDrive.

## <a name="determining-current-status"></a>Déterminer l’état actuel

Vous pouvez vérifier l’état d’un déplacement géographique OneDrive vers ou hors de la zone géographique à laquelle vous êtes connecté à l’aide de l’applet de commande Get-SPOUserAndContentMoveState.

Les états de déplacement sont décrits dans le tableau suivant.

|Statut|Description|
|---|---|
|NotStarted|Le déplacement n’a pas démarré|
|InProgress (*n*/4)|Le déplacement est en cours dans l’un des états suivants : <ul><li>Validation (1/4)</li><li>Sauvegarde (2/4)</li><li>Restaurer (3/4)</li><li>Nettoyage (4/4)</li></ul>|
|Opération réussie|Le déplacement a réussi.|
|Échec|Le déplacement a échoué.|

Pour rechercher l’état du déplacement d’un utilisateur spécifique, utilisez le paramètre *UserPrincipalName* :

```powershell
Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>
```

Pour trouver l’état de tous les déplacements dans ou hors de l’emplacement géographique auquel vous êtes connecté, utilisez le paramètre *MoveState* avec l’une des valeurs suivantes : NotStarted, InProgress, Success, Failed, All.

```powershell
Get-SPOUserAndContentMoveState -MoveState <value>
```

Vous pouvez également ajouter le paramètre *Détaillé* pour obtenir des descriptions plus détaillées de l’état de déplacement.

## <a name="user-experience"></a>Expérience de l’utilisateur

Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.

### <a name="users-onedrive"></a>Lecteur OneDrive d’un utilisateur

Pendant que le déplacement est en cours, oneDrive de l’utilisateur est défini en lecture seule. Une fois le déplacement terminé, l’utilisateur est dirigé vers son OneDrive dans le nouvel emplacement géographique lorsqu’il accède à OneDrive le lanceur d’applications Microsoft 365 ou un navigateur web.

### <a name="permissions-on-onedrive-content"></a>Autorisations sur le contenu OneDrive

Les utilisateurs disposant d’autorisations sur le contenu OneDrive continueront d’avoir accès au contenu pendant le déplacement et une fois celui-ci terminé.

### <a name="onedrive-sync-app"></a>application Synchronisation OneDrive

L’application Synchronisation OneDrive détecte et transfère automatiquement la synchronisation vers le nouvel emplacement OneDrive une fois le déplacement géographique OneDrive terminé. L’utilisateur n’a pas besoin de se reconnecter ou d’effectuer une autre action.  (Version 17.3.6943.0625 ou ultérieure de l’application de synchronisation requise.)

Si un utilisateur met à jour un fichier pendant que le déplacement géographique de OneDrive est en cours, l’application de synchronisation l’informe que les chargements de fichiers sont en attente pendant le déplacement.

### <a name="sharing-links"></a>Liens de partage

Lorsque le déplacement géographique de OneDrive est terminé, les liens partagés existants pour les fichiers qui ont été déplacés redirigent automatiquement vers le nouvel emplacement géographique.

### <a name="onenote-experience"></a>Expérience OneNote

OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:

- OneNote win32 – Version 16.0.8326.2096 (et versions ultérieures)
- OneNote UWP – Version 16.0.8431.1006 (et versions ultérieures)
- Application mobile OneNote : Version 16.0.8431.1011 (et versions ultérieures)

### <a name="teams-app"></a>Application Teams

Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.

### <a name="onedrive-mobile-app-ios"></a>OneDrive Mobile App (iOS)

Lorsque le déplacement géographique de OneDrive est terminé, l’utilisateur doit se déconnecter et se reconnecter sur l’application mobile iOS pour réaliser la synchronisation avec le nouvel emplacement OneDrive.

### <a name="existing-followed-groups-and-sites"></a>Sites et groupes suivis existants

Les sites et groupes suivis s’affichent dans OneDrive de l’utilisateur, quel que soit son emplacement géographique. Les sites et groupes hébergés dans un autre emplacement géographique s’ouvrent dans un onglet distinct.

### <a name="delve-geo-url-updates"></a>Mises à jour de l’URL géographique de Delve

Les utilisateurs ne seront envoyés à la zone géographique Delve correspondant à leur PDL qu’une fois que oneDrive aura été déplacé vers la nouvelle zone géographique.
