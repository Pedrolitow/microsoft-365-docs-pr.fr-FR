---
title: Examiner et gérer les actions de correction dans Microsoft Defender pour Office 365
keywords: AIR, autoIR, Microsoft Defender pour point de terminaison, automatisé, investigation, réponse, correction, menaces, avancées, menaces, protection
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- m365-security
- m365initiative-defender-office365
ms.custom: ''
description: Découvrez les actions de correction dans les fonctionnalités d’investigation et de réponse automatisées dans Microsoft Defender pour Office 365 Plan 2.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.date: 06/10/2021
ms.openlocfilehash: 0342ad8b4319d82205889785cd243b0a6aa5d9e2
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68086044"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>Examiner et gérer les actions de correction dans Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

À mesure que des enquêtes automatisées sur les e-mails & du contenu de collaboration entraînent des verdicts, tels que *malveillants* ou *suspects*, certaines actions de correction sont créées. Dans Microsoft Defender pour Office 365, les actions de correction peuvent inclure :

- Suppression réversible de messages électroniques ou de clusters
- Désactivation du transfert de courrier externe

Ces actions de correction ne sont pas effectuées tant que votre équipe chargée des opérations de sécurité ne les approuve pas. Nous vous recommandons d’examiner et d’approuver toutes les actions en attente dès que possible afin que vos enquêtes automatisées se terminent en temps voulu. Dans certains cas, vous pouvez reconsidérer les actions soumises.  Vous devez faire partie du rôle De recherche & purge avant d’effectuer des actions.

## <a name="approve-or-reject-pending-actions"></a>Approuver (ou rejeter) les actions en attente

Il existe quatre façons différentes de rechercher et d’effectuer des actions d’investigation automatique :

- [File d’attente d’incidents](https://security.microsoft.com/incidents)
- Investigation proprement dite (accessible via un incident ou à partir d’une alerte)
- [Centre d’action](https://security.microsoft.com/action-center/pending)
- [File d’attente d’investigations et de corrections](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>File d’attente d’incidents

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Incidents** sur **Incidents & alertes Incidents**\>. Pour accéder directement à la page **Incidents** , utilisez <https://security.microsoft.com/incidents>.
2. Dans la page **Incidents** , sélectionnez un nom d’incident pour ouvrir sa page récapitulative.
3. Sélectionnez l’onglet **Preuve et réponse** .
4. Sélectionnez un élément dans la liste. Son volet latéral s’ouvre.
5. Dans le volet latéral, effectuez des actions d’approbation ou de rejet.

## <a name="action-center"></a>Centre de notifications

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Centre d’actions** en sélectionnant **Centre d’actions**. Pour accéder directement à la page **Centre d’actions** , utilisez <https://security.microsoft.com/action-center/pending>.
2. Dans la page **Centre d’actions** , vérifiez que l’onglet **En attente** est sélectionné, puis passez en revue la liste des actions en attente d’approbation.
   - Sélectionnez **Ouvrir la page d’enquête** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Refuser** pour empêcher l’exécution d’une action en attente.

## <a name="investigation-and-remediation-investigations-queue"></a>File d’attente d’investigations et de corrections

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Enquête sur les menaces** à **l’adresse Email &** **Investigations de** collaboration\>. Pour accéder directement à la page **d’enquête sur les menaces** , utilisez <https://security.microsoft.com/airinvestigation>.
2. Dans la page **d’enquête sur les menaces** , recherchez et un élément de la liste dont l’état est **En attente d’action**.
3. Cliquez sur ![Ouvrir dans l’icône Nouvelle fenêtre.](../../media/m365-cc-sc-open-icon.png) **Ouvrez dans une nouvelle fenêtre** l’heure de la liste (entre **l’ID** et **l’état**).
4. Dans la page qui s’ouvre, effectuez des actions d’approbation ou de rejet.

## <a name="change-or-undo-one-remediation-action"></a>Modifier ou annuler une action de correction

Il existe deux façons différentes de reconsidérer les actions soumises :

- Via le [centre d’action unifié](https://security.microsoft.com/action-center).
- Bien que le [centre d’action Office](https://security.microsoft.com/threatincidents).

## <a name="change-or-undo-through-the-unified-action-center"></a>Modifier ou annuler via le centre d’action unifié

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez au centre d’action unifié en sélectionnant **Centre d’actions**. Pour accéder directement au centre d’action unifié, utilisez <https://security.microsoft.com/action-center/>.
2. Dans la page **Centre d’actions** , sélectionnez l’onglet **Historique** , puis sélectionnez l’action que vous souhaitez modifier ou annuler.
3. Dans le volet à droite de l’écran, sélectionnez l’action appropriée (**accéder à la boîte de réception**, **passer à la boîte de** réception, **accéder aux éléments supprimés**, **supprimer de manière réversible** ou **supprimer en dur**).

## <a name="change-or-undo-through-the-office-action-center"></a>Modifier ou annuler via le centre d’actions Office

1. Dans le portail Microsoft 365 Defender, accédez au <https://security.microsoft.com>Centre d’action Office à Email & **centre d’action** de **révision** \> de **collaboration**\>. Pour accéder directement au centre d’action Office, utilisez <https://security.microsoft.com/threatincidents>.
2. Dans la page **Centre d’actions** , sélectionnez la correction appropriée.
3. Dans le volet latéral, cliquez sur l’entrée des soumissions de courrier et attendez le chargement de la liste.
4. Attendez que le bouton Action en haut active et sélectionnez le bouton Action pour modifier le type d’action.
5. Cela crée les actions appropriées.

## <a name="next-steps"></a>Prochaines étapes

- [Utiliser l’Explorateur de menaces](threat-explorer.md)
- [Administration /Actions manuelles](remediate-malicious-email-delivered-office-365.md)
- [Comment signaler des faux positifs/négatifs dans les fonctionnalités d’investigation et de réponse automatisées](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Voir aussi

- [Afficher les détails et les résultats d’une enquête automatisée dans Office 365](air-view-investigation-results.md)
