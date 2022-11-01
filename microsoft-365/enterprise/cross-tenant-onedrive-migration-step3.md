---
title: Étape 3 de migration des données utilisateur entre locataires OneDrive
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
description: Étape 3 de la fonctionnalité de migration interlocataire OneDrive
ms.openlocfilehash: c59706de4300f6c505582b74aef4ec7223fb3d08
ms.sourcegitcommit: b386eaa33e1e5cdea59916247082b6e6e6a3d99e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68807758"
---
# <a name="step-3-verifying-trust"></a>Étape 3 : Vérification de l’approbation

Il s’agit de l’étape 3 d’une solution conçue pour effectuer une migration OneDrive interlocataire. Pour plus d’informations, consultez [Vue d’ensemble de la migration OneDrive interlocataire](cross-tenant-onedrive-migration.md).

- Étape 1 : [Se connecter à la source et aux locataires cibles](cross-tenant-onedrive-migration-step1.md)
- Étape 2 : [Établir une relation de confiance entre le locataire source et le locataire cible](cross-tenant-onedrive-migration-step2.md) 
- **Étape 3 : [Vérifier que l’approbation a été établie](cross-tenant-onedrive-migration-step3.md)** 
- Étape 4 : [Précréer des utilisateurs et des groupes](cross-tenant-onedrive-migration-step4.md)  
- Étape 5 : [Préparer le mappage d’identité](cross-tenant-onedrive-migration-step5.md)
- Étape 6 : [Démarrer une migration OneDrive interlocataire](cross-tenant-onedrive-migration-step6.md)
- Étape 7 : [Étapes post-migration](cross-tenant-onedrive-migration-step7.md)

Avant de poursuivre votre migration, vous devez vérifier que l’approbation est terminée. L’état *GoodToProceed* confirme que l’approbation est vérifiée.

## <a name="to-verify-trust-has-been-established"></a>Pour vérifier que l’approbation a été établie

1. Sur le **locataire source** , exécutez :
 
```powershell

Verify-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Target -PartnerCrossTenantHostUrl <TARGETCrossTenantHostUrl>

```
2. Sur le **locataire cible** , exécutez :

```powershell 

Verify-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Source -PartnerCrossTenantHostUrl <SOURCECrossTenantHostUrl>
```

## <a name="troubleshooting-trust-issues"></a>Résolution des problèmes d’approbation

Lors de la vérification de l’approbation, valeurs possibles

|Valeur|Description|
|:-----|:-----|
|NotEstablished|L’approbation n’a pas été demandée localement.|
|NotEstablishedByPartner|L’approbation n’a pas été demandée par le partenaire|
|DormantByPartner|L’approbation demandée par le partenaire est dans le délai d’attente de sept jours suivant la création.|
|CouldNotContactPartner|Impossible de contacter le partenaire pour déterminer l’état.|
|GoodToProceed|Vérifié pour continuer.|


## <a name="step-4-pre-create-users-and-groups"></a>Étape 4 : [Précréer des utilisateurs et des groupes](cross-tenant-onedrive-migration-step4.md)