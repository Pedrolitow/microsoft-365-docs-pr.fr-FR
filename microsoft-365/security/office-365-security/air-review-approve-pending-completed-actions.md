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
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Découvrez les actions de correction dans les fonctionnalités d’examen et de réponse automatisées dans Microsoft Defender pour Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.date: 06/10/2021
ms.openlocfilehash: bc8c99a547e4f30e10575e8353afd6ca02bf233b
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61932772"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>Examiner et gérer les actions de correction dans Office 365

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

Comme des enquêtes automatisées sur & de collaboration  entraînent des verdicts, tels que malveillants ou suspects, certaines actions de correction sont créées. Dans Microsoft Defender pour Office 365, les actions de correction peuvent inclure :

- Suppression de messages électroniques ou de clusters
- Turning off external mail forwarding

Ces mesures correctives ne sont prises que si votre équipe en charge des opérations de sécurité ne les approuve pas. Nous vous recommandons d’examiner et d’approuver les actions en attente dès que possible afin que vos enquêtes automatisées se terminent en temps voulu. Dans certains cas, vous pouvez reconsidérer les actions envoyées.  Vous devez faire partie du rôle de & de recherche avant d’effectuer des actions.

## <a name="approve-or-reject-pending-actions"></a>Approuver (ou rejeter) les actions en attente

Il existe quatre méthodes différentes pour rechercher et prendre des mesures d’investigation automatique :

- [File d’attente des incidents](https://security.microsoft.com/incidents)
- Examen proprement dit (accessible via incident ou à partir d’une alerte)
- [Centre de actions](https://security.microsoft.com/action-center/pending)
- [File d’attente des examens d’investigation et de correction](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>File d’attente des incidents

1. In the Microsoft 365 Defender portal at <https://security.microsoft.com> , go to the **Incidents** page at **Incidents &** \> **alerts Incidents**. Pour aller directement à la page **Incidents,** utilisez <https://security.microsoft.com/incidents> .
2. Dans la page **Incidents,** sélectionnez un nom d’incident pour ouvrir sa page récapitulatif.
3. Sélectionnez **l’onglet Preuve et** réponse.
4. Sélectionnez un élément dans la liste. Son volet latéral s’ouvre.
5. Dans le volet latéral, prenez des mesures d’approbation ou de rejet.

## <a name="action-center"></a>Centre de notifications

1. In the Microsoft 365 Defender portal at <https://security.microsoft.com> , go to the Action **center** page by selecting **Action center**. Pour aller directement à la page centre **de l’action,** utilisez <https://security.microsoft.com/action-center/pending> .
2. Dans la page **Centre** de  l’action, vérifiez que l’onglet En attente est sélectionné, puis examinez la liste des actions en attente d’approbation.
   - Sélectionnez **Ouvrir la page Examen** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Rejeter** pour empêcher une action en attente d’être prise.

## <a name="investigation-and-remediation-investigations-queue"></a>File d’attente des examens d’investigation et de correction

1. In the Microsoft 365 Defender portal at <https://security.microsoft.com> , go to the Threat **investigation** page at Email **& collaboration** \> **Investigations**. Pour aller directement à la page **d’examen des menaces,** utilisez <https://security.microsoft.com/airinvestigation> .
2. Dans la page **Examen des menaces,** recherchez et un élément de la liste dont l’état est **Action en attente**.
3. Cliquez ![ sur Ouvrir dans l’icône Nouvelle fenêtre.](../../media/m365-cc-sc-open-icon.png) **Ouvrir dans une nouvelle fenêtre de** l’heure de liste (entre **ID** et **État).**
4. Dans la page qui s’ouvre, prenez des mesures d’approbation ou de rejet.

## <a name="change-or-undo-one-remediation-action"></a>Modifier ou annuler une action de correction

Il existe deux façons de reconsidérer les actions envoyées :

- Via le centre [de l’action unifiée.](https://security.microsoft.com/action-center)
- Bien que le [centre Office actions .](https://security.microsoft.com/threatincidents)

## <a name="change-or-undo-through-the-unified-action-center"></a>Modifier ou annuler par le biais du centre de l’action unifiée

1. Dans le portail Microsoft 365 Defender, allez au centre de l’action unifiée <https://security.microsoft.com> en sélectionnant Centre **de l’action.** Pour aller directement au centre de l’action unifiée, utilisez <https://security.microsoft.com/action-center/> .
2. Dans la page Centre  **de l’action,** sélectionnez l’onglet Historique, puis sélectionnez l’action à modifier ou annuler.
3. Dans le volet sur le côté droit de l’écran, sélectionnez l’action appropriée **(déplacer** vers la boîte de **réception,** déplacer vers le courrier **indésirable,** déplacer vers les éléments supprimés, supprimer (supprimer) ou supprimer **définitivement).**

## <a name="change-or-undo-through-the-office-action-center"></a>Modifier ou annuler via le centre de Office actions

1. Dans le portail Microsoft 365 Defender à l’adresse , go <https://security.microsoft.com> to the Office action center at Email & **collaboration** \> **Review** \> **Action center**. Pour aller directement au centre de Office actions, utilisez <https://security.microsoft.com/threatincidents> .
2. Dans la page **Centre de l’action,** sélectionnez la correction appropriée.
3. Dans le panneau latéral, cliquez sur l’entrée des envois de courrier et attendez le chargement de la liste.
4. Attendez que le bouton Action en haut s’active et sélectionnez le bouton Action pour modifier le type d’action.
5. Cela crée les actions appropriées.

## <a name="next-steps"></a>Prochaines étapes

- [Utiliser l’Explorateur de menaces](threat-explorer.md)
- [Actions d’administration /manuelles](remediate-malicious-email-delivered-office-365.md)
- [Comment signaler les faux positifs/négatifs dans les fonctionnalités automatisées d’examen et de réponse](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Voir aussi

- [Afficher les détails et les résultats d’un examen automatisé dans Office 365](air-view-investigation-results.md)
