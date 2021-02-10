---
title: Examiner et gérer les actions de correction dans Microsoft Defender pour Office 365
keywords: AIR, autoIR, ATP, automatisé, examen, réponse, correction, menaces, avancé, menace, protection
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
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
ms.openlocfilehash: 3fb77fa41ff3e9af995cf80b9f4024aa92a51212
ms.sourcegitcommit: 3dc795ea862b180484f76b3eb5d046e74041252b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2021
ms.locfileid: "50176014"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>Examiner et gérer les actions de correction dans Office 365

Comme des enquêtes automatisées sur & de collaboration  entraînent des verdicts, tels que malveillants ou suspects, certaines actions de correction sont créées. Dans Microsoft Defender pour Office 365, les actions de correction peuvent inclure :
- Blocage d’une URL (heure de clic)
- Suppression de messages électroniques ou de clusters de suppression (soft)
- Mise en quarantaine des pièces jointes ou des e-mails
- Turning off external mail forwarding

Ces mesures correctives ne sont prises que si votre équipe en charge des opérations de sécurité ne les approuve pas. Nous vous recommandons d’examiner et d’approuver les actions en attente dès que possible afin que vos enquêtes automatisées se terminent en temps voulu. Dans certains cas, vous pouvez annuler une action de correction.

**S’applique à**
- [Microsoft Defender pour Office 365 (plan 2)](https://go.microsoft.com/fwlink/?linkid=2148715)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="approve-or-reject-pending-actions"></a>Approuver (ou rejeter) les actions en attente

1. Go to the Microsoft 365 security center [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.
2. Dans le volet de navigation, sélectionnez **Centre de l’action.**
3. Sous **l’onglet En** attente, examinez la liste des actions en attente d’approbation.
4. Sélectionnez un élément dans la liste. Son volet volant s’ouvre. 
5. Examinez les informations dans le volet volant, puis prenez l’une des étapes suivantes :
   - Sélectionnez **Ouvrir la page Examen** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Rejeter** pour empêcher une action en attente d’être prise.

## <a name="undo-one-remediation-action"></a>Annuler une action de correction

1. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) and sign in.
2. Sous **l’onglet** Historique, sélectionnez une action à annuler.
3. Dans le volet sur le côté droit de l’écran, sélectionnez **Annuler**.

## <a name="undo-multiple-remediation-actions"></a>Annuler plusieurs actions de correction

1. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) and sign in.
2. Sous **l’onglet** Historique, sélectionnez les actions à annuler. Veillez à sélectionner les éléments qui ont le même type d’action. Un volet volant s’ouvre.
3. Dans le volet volant, sélectionnez Annuler.

## <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Pour supprimer un fichier de la quarantaine sur plusieurs appareils

1. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) and sign in.
2. Sous **l’onglet** Historique, sélectionnez un fichier dont le fichier de mise en quarantaine du type d’action **est sélectionné.**
3. Dans le volet sur le côté droit de l’écran, sélectionnez Appliquer à **X plus d’instances** de ce fichier, puis **sélectionnez Annuler**.

## <a name="next-steps"></a>Étapes suivantes

- [Utiliser l’Explorateur de menaces](threat-explorer.md)
- [Comment signaler les faux positifs/négatifs dans les fonctionnalités automatisées d’examen et de réponse](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Voir aussi

- [Afficher les détails et les résultats d’une enquête automatisée dans Office 365](air-view-investigation-results.md)
