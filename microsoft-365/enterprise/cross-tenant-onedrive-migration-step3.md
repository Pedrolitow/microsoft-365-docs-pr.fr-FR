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
ms.openlocfilehash: 6a42b833ecfc59d96f69d5061a0e6fe64746a8c6
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805405"
---
# <a name="step-3-cross-tenant-onedrive-migration---verifying-trust"></a>Étape 3 : Migration onedrive interlocataire - Vérification de l’approbation

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