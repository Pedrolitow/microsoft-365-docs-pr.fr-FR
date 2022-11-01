---
title: Étape 1 de migration des données utilisateur entre locataires OneDrive
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
description: Étape 1 de la fonctionnalité de migration interlocataire OneDrive
ms.openlocfilehash: b9bb72707e11e3257eabac093e4a76daa903bf40
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805542"
---
# <a name="step-1-cross-tenant-onedrive-migration---connect-to-the-source-and-target-tenants"></a>Étape 1 : Migration onedrive interlocataire - Se connecter aux locataires source et cible

La première étape de votre migration OneDrive interlocataire consiste à vous connecter à votre locataire source et cible SharePoint.

## <a name="before-you-begin"></a>Avant de commencer

- **Microsoft Office SharePoint Online PowerShell**. Vérifiez que la version la plus récente est installée. Si ce n’est pas le cas, [téléchargez SharePoint Online Management Shell à partir du Centre de téléchargement Microsoft officiel](/download/details.aspx?id=35588).
- Être administrateur SharePoint Online ou administrateur général Microsoft 365 sur les locataires source et cible.


### <a name="connect-to-both-tenants"></a>Se connecter aux deux locataires

1. Connectez-vous à Sharepoint Management Shell en tant qu’administrateur SharePoint Online ou administrateur général Microsoft 365.
2. Exécutez la commande suivante en entrant l’URL du locataire **source** : 

    ```powershell
    Connect-SPOService -url https://<TenantName>-admin.sharepoint.com
    ```

3. Lorsque vous y êtes invité, connectez-vous au locataire **source** à l’aide de votre nom d’utilisateur et de votre mot de passe Administration.
 
4. Exécutez la commande suivante en entrant l’URL du locataire **cible** : 

    ```powershell
    Connect-SPOService -url https://<TenantName>-admin.sharepoint.com
    ```

5. Lorsque vous y êtes invité, connectez-vous au locataire **cible** à l’aide de votre Administration nom d’utilisateur et mot de passe.

>[!Important]
>**Clients microsoft 365 multigéographiques :** Vous devez traiter chaque zone géographique comme un locataire distinct. Fournissez les URL spécifiques à la zone géographique correctes tout au long du processus de migration.

## <a name="step-2-establish-trust-between-the-source-and-target-tenants"></a>Étape 2 : [Établir l’approbation entre les locataires source et cible](cross-tenant-onedrive-migration-step2.md)