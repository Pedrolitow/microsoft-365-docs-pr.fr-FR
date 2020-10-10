---
title: Passer en revue et approuver les actions de correction en attente dans l’instruction et la réponse automatisées
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
ms.collection:
- M365-security-compliance
- m365-initiative-defender-office365
description: Découvrez les actions de correction dans les fonctionnalités d’analyse et de réponse automatisées dans Office 365 Advanced Threat Protection Plan 2.
ms.openlocfilehash: 29a3c2f59ba85c2c5d9965c0c7f262dcba1ecda7
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48411985"
---
# <a name="view-pending-or-completed-remediation-actions-following-an-automated-investigation-in-office-365"></a>Afficher les actions de correction en attente ou terminées à la suite d’une enquête automatisée dans Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]



![Page action de l’enquête par avion](../../media/air-investigationactionspage.png)

## <a name="approve-or-reject-pending-actions"></a>Approuver (ou rejeter) les actions en attente

Lors de l’affichage [des détails d’une enquête](air-view-investigation-results.md), vous pouvez approuver ou refuser les actions correctives en attente. Nous vous recommandons de le faire dès que possible pour que vos investigations automatiques soient terminées.

> [!IMPORTANT]
> Les autorisations appropriées sont requises pour approuver ou rejeter les actions correctives. Consultez la rubrique [Required Permissions to use air Capabilities](office-365-air.md#required-permissions-to-use-air-capabilities).

1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous. Cette opération vous permet d’accéder au centre de sécurité & conformité.

2. Accédez aux enquêtes de **gestion des menaces**  >  **Investigations**.

3. Dans la liste des enquêtes, sélectionnez un élément dans la colonne **ID** . 

4. Sélectionnez l’onglet **actions** .

5. Sélectionnez un élément dans la liste. (Cela active les boutons approuver et rejeter.)

6. Examinez les informations disponibles pour les éléments que vous avez sélectionnés, puis approuvez ou rejetez la ou les actions. 
   - **Approuver** : le début de la correction.
   - Le **rejet** n’effectue aucune action supplémentaire

## <a name="next-steps"></a>Étapes suivantes

- [Détails et résultats d’une enquête automatisée dans Office 365](air-view-investigation-results.md)

- [Utiliser l’Explorateur de menaces](threat-explorer.md)
