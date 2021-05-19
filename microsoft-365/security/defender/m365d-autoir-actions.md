---
title: Afficher et gérer les actions dans le centre de gestion des actions
description: Utiliser le Centre de gestion des actions pour afficher et gérer les actions de correction
keywords: action, center, autoair, automated, investigation, response, remediation
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 9e82f1c5de9fe1f4a03385458338edf18c4f35bd
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52538842"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>Afficher et gérer les actions dans le centre de gestion des actions

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Les fonctionnalités de protection contre les menaces Microsoft 365 Defender peuvent entraîner certaines actions de correction. Voici quelques exemples :

- [Les enquêtes](m365d-autoir.md) automatisées peuvent entraîner des actions de correction qui sont prises automatiquement ou qui attendent votre approbation.
- Un antivirus, un logiciel anti-programme malveillant et d’autres fonctionnalités de protection contre les menaces peuvent entraîner des actions de correction, telles que le blocage d’un fichier, d’une URL ou d’un processus, ou l’envoi d’un artefact en quarantaine.
- Votre équipe en matière d’opérations de [](advanced-hunting-overview.md) sécurité peut prendre des mesures correctives manuellement, par exemple lors d’une recherche avancée ou lors de l’investigation d’alertes [ou d’incidents.](investigate-incidents.md) [](investigate-alerts.md)

> [!NOTE]
> Vous devez disposer des [autorisations appropriées](m365d-action-center.md#required-permissions-for-action-center-tasks) pour approuver ou rejeter les actions de correction. Pour plus d’informations, consultez [les conditions préalables.](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)

## <a name="review-pending-actions-in-the-action-center"></a>Passer en revue les actions en attente dans le centre de actions

Il est important d’approuver (ou de refuser) les actions en attente dès que possible de sorte que vos enquêtes automatisées puissent se poursuivre et se terminer dans un délai raisonnable. 

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Dans le centre de notifications, dans l’onglet **En attente**, sélectionnez un élément dans la liste. Son volet volant s’ouvre. Voici un exemple.

   ![Approuver ou rejeter une action](../../media/air-actioncenter-itemselected.png)

4. Examinez les informations dans le volet volant, puis prenez l’une des étapes suivantes :
   - Sélectionnez **Ouvrir la page Examen** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Rejeter** pour empêcher une action en attente d’être prise.
   - Sélectionnez **Go hunt** (Aller à la recherche) pour aller [dans le recherche avancée](advanced-hunting-overview.md). 

## <a name="undo-completed-actions"></a>Annuler les actions terminées

Si vous avez déterminé qu’un appareil ou un fichier n’est pas une menace, vous pouvez annuler les actions de correction qui ont été prises, que ces actions soient prises automatiquement ou manuellement. Dans le centre de actions, sous **l’onglet** Historique, vous pouvez annuler l’une des actions suivantes :  

| Source de l’action | Actions prises en charge |
|:---|:---|
| - Examen automatisé <br/>- Antivirus Microsoft Defender <br/>- Actions de réponse manuelles | - Isoler l’appareil <br/>- Restreindre l’exécution du code <br/>- Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche programmée |

### <a name="undo-one-remediation-action"></a>Annuler une action de correction

1. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) and sign in.

2. Sous **l’onglet** Historique, sélectionnez une action à annuler.

3. Dans le volet sur le côté droit de l’écran, sélectionnez **Annuler**.

### <a name="undo-multiple-remediation-actions"></a>Annuler plusieurs actions de correction

1. Go to the Action center ( https://security.microsoft.com/action-center) and sign in.

2. Sous **l’onglet** Historique, sélectionnez les actions à annuler. Veillez à sélectionner les éléments qui ont le même type d’action. Un volet volant s’ouvre.

3. Dans le volet volant, sélectionnez **Annuler.**

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Pour supprimer un fichier de la quarantaine sur plusieurs appareils 

1. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) and sign in.

2. Sous **l’onglet** Historique, sélectionnez un fichier dont le type de fichier de mise en **quarantaine** est action.

3. Dans le volet sur le côté droit de l’écran, sélectionnez Appliquer à **X plus d’instances** de ce fichier, puis **sélectionnez Annuler**.

## <a name="next-steps"></a>Étapes suivantes

- [Consulter les détails et les résultats d'un examen automatisé](m365d-autoir-results.md)
- [Corriger les faux positifs ou les faux négatifs](m365d-autoir-report-false-positives-negatives.md)
