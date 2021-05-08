---
title: Examiner et gérer les actions de correction dans Microsoft Defender pour Office 365
keywords: AIR, autoIR, Microsoft Defender pour point de terminaison, automatisé, examen, réponse, correction, menaces, avancé, menace, protection
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez les actions de correction dans les fonctionnalités d’examen et de réponse automatisées dans Microsoft Defender pour Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.date: 01/29/2021
ms.openlocfilehash: f0c42bef1b090412a7a6422fe029323b645e90df
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52275071"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>Examiner et gérer les actions de correction dans Office 365

Comme des enquêtes automatisées sur & de collaboration  entraînent des verdicts, tels que malveillants ou suspects, certaines actions de correction sont créées. Dans Microsoft Defender pour Office 365, les actions de correction peuvent inclure :
- Blocage d’une URL (heure du clic)
- Suppression de messages électroniques ou de clusters
- Mise en quarantaine des pièces jointes ou des e-mails
- Turning off external mail forwarding

Ces mesures correctives ne sont prises que si votre équipe en charge des opérations de sécurité ne les approuve pas. Nous vous recommandons d’examiner et d’approuver les actions en attente dès que possible afin que vos enquêtes automatisées se terminent en temps voulu. Dans certains cas, vous pouvez annuler une action de correction.

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="approve-or-reject-pending-actions"></a>Approuver (ou rejeter) les actions en attente

1. Go to the Microsoft 365 security center ( <https://security.microsoft.com> ) and sign in.
2. Dans le volet de navigation, sélectionnez **Centre de l’action.**
3. Sous **l’onglet En** attente, examinez la liste des actions en attente d’approbation.
4. Sélectionnez un élément dans la liste. Son volet volant s’ouvre. 
5. Examinez les informations dans le volet volant, puis prenez l’une des étapes suivantes :
   - Sélectionnez **Ouvrir la page Examen** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Rejeter** pour empêcher une action en attente d’être prise.

## <a name="undo-one-remediation-action"></a>Annuler une action de correction

1. Go to the Action center ( <https://security.microsoft.com/action-center> ) and sign in.
2. Sous **l’onglet** Historique, sélectionnez une action à annuler.
3. Dans le volet sur le côté droit de l’écran, sélectionnez **Annuler**.

## <a name="undo-multiple-remediation-actions"></a>Annuler plusieurs actions de correction

1. Go to the Action center ( <https://security.microsoft.com/action-center> ) and sign in.
2. Sous **l’onglet** Historique, sélectionnez les actions à annuler. Veillez à sélectionner les éléments qui ont le même type d’action. Un volet volant s’ouvre.
3. Dans le volet volant, sélectionnez Annuler.

## <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Pour supprimer un fichier de la quarantaine sur plusieurs appareils

1. Go to the Action center ( <https://security.microsoft.com/action-center> ) and sign in.
2. Sous **l’onglet** Historique, sélectionnez un fichier dont le fichier de mise en quarantaine du type d’action **est sélectionné.**
3. Dans le volet sur le côté droit de l’écran, sélectionnez Appliquer à **X plus d’instances** de ce fichier, puis **sélectionnez Annuler**.

## <a name="next-steps"></a>Étapes suivantes

- [Utiliser l’Explorateur de menaces](threat-explorer.md)
- [Comment signaler les faux positifs/négatifs dans les fonctionnalités automatisées d’examen et de réponse](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Voir aussi

- [Afficher les détails et les résultats d’un examen automatisé dans Office 365](air-view-investigation-results.md)
