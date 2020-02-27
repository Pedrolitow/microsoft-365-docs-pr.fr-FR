---
title: Actions correctives dans Office 365 automatisation de l’analyse et de la réponse
keywords: AIR, autoIR, ATP, automatisation, analyse, réponse, correction, menaces, avancé, menace, protection
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: Découvrez les actions de correction dans les fonctionnalités d’analyse et de réponse automatisées dans Office 365 Advanced Threat Protection Plan 2.
ms.openlocfilehash: 0db49a28fb90bcddcdd874ac54216957e4be5fa1
ms.sourcegitcommit: 45ee610a380db113c2a50f6ea82d30137498babb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "42288512"
---
# <a name="remediation-actions-following-an-automated-investigation-in-office-365"></a>Actions de correction suite à une enquête automatisée dans Office 365

## <a name="remediation-actions"></a>Actions de correction

[Les fonctionnalités d’analyse et de réponse automatisées](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air) dans Office 365 protection avancée contre les menaces incluent certaines actions de correction. Lorsqu’une enquête automatisée est en cours d’exécution ou qu’elle est terminée, vous verrez généralement une ou plusieurs actions correctives qui nécessitent l’approbation de votre équipe d’opérations de sécurité. 

Le tableau suivant récapitule les actions de correction actuellement disponibles dans [Office 365 Advanced Threat Protection](office-365-atp.md). 

|Opération | Description |
|-----|-----|
|Bloquer l’URL (heure du clic) |Se protéger contre les e-mails et les documents contenant des URL malveillantes. Cela permet de bloquer les liens malveillants et les pages Web associées via [des liens fiables](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-links) lorsque l’utilisateur clique sur un lien dans un fichier Office existant ou dans un ancien message électronique. |
|Courrier électronique de suppression douce  |Suppression logicielle de messages électroniques spécifiques de la boîte aux lettres d’un utilisateur|
|Clusters de suppression de courrier électronique  |Suppression logicielle de messages électroniques malveillants correspondant à une requête de toutes les boîtes aux lettres des utilisateurs|
|Désactiver le transfert de courrier externe |Supprime la règle de transfert d’une boîte aux lettres d’un utilisateur final spécifique.|

## <a name="approve-or-reject-pending-actions"></a>Approuver (ou rejeter) les actions en attente

![Page action de l’enquête par avion](../../media/air-investigationactionspage.png)

Lors de l’affichage [des détails d’une enquête](air-view-investigation-results.md), vous pouvez approuver ou refuser les actions correctives en attente. Nous vous recommandons de le faire dès que possible pour que vos investigations automatiques soient terminées.

> [!IMPORTANT]
> Les autorisations appropriées sont requises pour approuver ou rejeter les actions correctives. Consultez la rubrique [Required Permissions to use air Capabilities](office-365-air.md#required-permissions-to-use-air-capabilities).

1. Sélectionnez l’onglet **actions** .

2. Sélectionnez un élément dans la liste. (Cela active les boutons approuver et rejeter.)

3. Examinez les informations disponibles pour les éléments que vous avez sélectionnés, puis approuvez ou rejetez la ou les actions. 
 - **Approuver** : le début de la correction.
 - Le **rejet** n’effectue aucune action supplémentaire

## <a name="next-steps"></a>Étapes suivantes

- [En savoir plus sur le manifeste de sécurité de l’utilisateur compromis](https://docs.microsoft.com/microsoft-365/security/office-365-security/address-compromised-users-quickly)

- [Afficher vos rapports ATP](https://docs.microsoft.com/microsoft-365/security/office-365-security/view-reports-for-atp)