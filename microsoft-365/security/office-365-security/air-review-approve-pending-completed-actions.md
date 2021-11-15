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
ms.custom: admindeeplinkDEFENDER
description: Découvrez les actions de correction dans les fonctionnalités d’examen et de réponse automatisées dans Microsoft Defender pour Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.date: 06/10/2021
ms.openlocfilehash: 5321f1cbe35727649c80dc17778dc843630f695e
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2021
ms.locfileid: "60962734"
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
- [Centre de actions](https://security.microsoft.com/action-center/pending)
- Examen proprement dit (accessible via incident ou à partir d’une alerte)
- [File d’attente des examens d’investigation et de correction](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>File d’attente des incidents

1. Ouvrez <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">le Microsoft 365 Defender et</a> connectez-vous.
2. Dans le volet de navigation, sélectionnez **Incidents & alertes > Incidents**.
3. Sélectionnez un nom d’incident pour ouvrir sa page récapitulatif.
4. Sélectionnez **l’onglet Preuve et** réponse.
5. Sélectionnez un élément dans la liste. Son volet latéral s’ouvre.
6. Dans le volet latéral, prenez des mesures d’approbation ou de rejet.

## <a name="investigation-queue"></a>File d’attente d’examen

1. Ouvrez <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">le Microsoft 365 Defender et</a> connectez-vous.
2. Accédez à la page alertes/incident.
3. Dans la page Examen, allez dans **l’onglet Actions en attente.**
4. Sélectionnez un élément dans la liste. Son volet latéral s’ouvre.
5. Dans le volet latéral, prenez des mesures d’approbation ou de rejet.

## <a name="action-center"></a>Centre de notifications

1. Ouvrez <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">le Microsoft 365 Defender et</a> connectez-vous.
2. Dans le volet de navigation, sélectionnez **Centre de l’action.**
3. Sous **l’onglet En** attente, examinez la liste des actions en attente d’approbation.
   - Sélectionnez **Ouvrir la page Examen** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Rejeter** pour empêcher une action en attente d’être prise.

## <a name="investigation-and-remediation-investigations-queue"></a>File d’attente des examens d’investigation et de correction

1. Ouvrez <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">le Microsoft 365 Defender et</a> connectez-vous.
2. Ouvrir les enquêtes en attente.
3. Dans la page Examen, allez dans **l’onglet Actions en attente.**
4. Sélectionnez un élément dans la liste. Son volet latéral s’ouvre.
5. Dans le volet latéral, prenez des mesures d’approbation ou de rejet.

## <a name="change-or-undo-one-remediation-action"></a>Modifier ou annuler une action de correction

Il existe deux façons de reconsidérer les actions envoyées :

- Via le centre [de l’action unifiée.](https://security.microsoft.com/action-center)
- Bien que le [centre Office actions .](https://security.microsoft.com/threatincidents)

## <a name="change-or-undo-through-the-unified-action-center"></a>Modifier ou annuler par le biais du centre de l’action unifiée

1. Go to the [unified action center](https://security.microsoft.com/action-center) and sign in.
2. Sous **l’onglet** Historique, sélectionnez une action que vous souhaitez modifier ou annuler.
3. Dans le volet sur le côté droit de l’écran, sélectionnez l’action appropriée **(déplacer** vers la boîte de **réception,** déplacer vers le courrier **indésirable,** déplacer vers les éléments supprimés, supprimer (supprimer) ou supprimer **définitivement).**

## <a name="change-or-undo-through-the-office-action-center"></a>Modifier ou annuler via le centre de Office actions

1. Go to the [Office action center](https://security.microsoft.com/threatincidents) and sign in.
2. Sélectionnez la correction appropriée.
3. Dans le volet latéral, cliquez sur l’entrée des envois de courrier et attendez le chargement de la liste.
4. Attendez que le bouton Action en haut s’active et sélectionnez le bouton Action pour modifier le type d’action.
5. Cela crée les actions appropriées.

## <a name="next-steps"></a>Étapes suivantes

- [Utiliser l’Explorateur de menaces](threat-explorer.md)
- [Actions d’administration /manuelles](remediate-malicious-email-delivered-office-365.md)
- [Comment signaler les faux positifs/négatifs dans les fonctionnalités automatisées d’examen et de réponse](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Voir aussi

- [Afficher les détails et les résultats d’un examen automatisé dans Office 365](air-view-investigation-results.md)
