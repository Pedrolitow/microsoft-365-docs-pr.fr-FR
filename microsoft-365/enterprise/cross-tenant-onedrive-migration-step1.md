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
ms.openlocfilehash: 59bb8047f1b85d1f8d9cc4843ecc3e0337cef5c2
ms.sourcegitcommit: b386eaa33e1e5cdea59916247082b6e6e6a3d99e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68807538"
---
# <a name="step-1-connect-to-the-source-and-target-tenants"></a>Étape 1 : Se connecter aux locataires source et cible

Il s’agit de l’étape 1 d’une solution conçue pour effectuer une migration OneDrive interlocataire. Pour plus d’informations, consultez [Vue d’ensemble de la migration OneDrive interlocataire](cross-tenant-onedrive-migration.md).

- **Étape 1 : [Se connecter à la source et aux locataires cibles](cross-tenant-onedrive-migration-step1.md)**
- Étape 2 : [Établir une relation de confiance entre le locataire source et le locataire cible](cross-tenant-onedrive-migration-step2.md) 
- Étape 3 : [Vérifier que l’approbation a été établie](cross-tenant-onedrive-migration-step3.md) 
- Étape 4 : [Précréer des utilisateurs et des groupes](cross-tenant-onedrive-migration-step4.md)  
- Étape 5 : [Préparer le mappage d’identité](cross-tenant-onedrive-migration-step5.md)
- Étape 6 : [Démarrer une migration OneDrive interlocataire](cross-tenant-onedrive-migration-step6.md)
- Étape 7 : [Étapes post-migration](cross-tenant-onedrive-migration-step7.md)

## <a name="before-you-begin"></a>Avant de commencer

- **Microsoft Office SharePoint Online PowerShell**. Vérifiez que la version la plus récente est installée. Si ce n’est pas le cas, [téléchargez SharePoint Online Management Shell à partir du Centre de téléchargement Microsoft officiel](/download/details.aspx?id=35588).
- Être administrateur SharePoint Online ou administrateur général Microsoft 365 sur les locataires source et cible


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