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
ms.openlocfilehash: 2efe0124304a9f9dcfdc92b548c850882ad507a0
ms.sourcegitcommit: 841c06a5d566d404c35d5e9c0c7de5088daab976
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "42836857"
---
# <a name="remediation-actions-following-an-automated-investigation-in-office-365"></a>Actions de correction suite à une enquête automatisée dans Office 365

## <a name="remediation-actions"></a>Actions de correction

[Les fonctionnalités d’analyse et de réponse automatisées](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air) (air) dans [Office 365 Advanced Threat Protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) (Office 365 ATP) plan 2 incluent certaines actions de correction. Lorsqu’une enquête automatisée est en cours d’exécution ou qu’elle est terminée, vous verrez généralement une ou plusieurs actions correctives qui nécessitent l’approbation de votre équipe d’opérations de sécurité. 

Le tableau suivant récapitule les actions de correction actuellement disponibles dans Office 365 ATP. 

|Opération | Description |
|-----|-----|
|Bloquer l’URL (heure du clic) |Protège contre les messages électroniques et les documents contenant des URL malveillantes. Cela permet de bloquer les liens malveillants et les pages Web associées via [des liens fiables](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-links) lorsque l’utilisateur clique sur un lien dans un fichier Office existant ou dans un ancien message électronique. |
|Courrier électronique de suppression douce  |Suppression logicielle de messages électroniques spécifiques de la boîte aux lettres d’un utilisateur. <br/>Un message supprimé (récupérable) est déplacé vers le dossier éléments récupérables d’un utilisateur et est conservé jusqu’à l’expiration de la période de rétention des éléments supprimés. |
|Clusters de suppression de courrier électronique  |Soft supprime les messages électroniques malveillants qui correspondent à une requête de toutes les boîtes aux lettres des utilisateurs. <br/>Les messages supprimés de manière récupérable sont déplacés vers le dossier éléments récupérables des utilisateurs et sont conservés jusqu’à l’expiration de la période de rétention des éléments supprimés. |
|Désactiver le transfert de courrier externe |Supprime une règle de transfert d’une boîte aux lettres d’un utilisateur final spécifique.|

> [!NOTE]
> Dans Office 365 ATP, aucune action de correction n’est effectuée automatiquement. Les actions de correction ne sont prises qu’après approbation de l’équipe de sécurité de votre organisation. 

## <a name="next-steps"></a>Étapes suivantes

- [Afficher les actions de correction en attente ou terminées à la suite d’une enquête automatisée dans Office 365](air-review-approve-pending-completed-actions.md)

- [Détails et résultats d’une enquête automatisée dans Office 365](air-view-investigation-results.md)