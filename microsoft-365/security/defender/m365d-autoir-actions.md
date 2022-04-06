---
title: Afficher et gérer les actions dans le Centre d’actions
description: Utiliser le Centre d’actions pour afficher et gérer les actions de correction
keywords: action, center, autoair, automated, investigation, response, remediation
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 43c48081a86e33cd918bc4de8f01859bc1107583
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666831"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>Afficher et gérer les actions dans le Centre d’actions

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Les fonctionnalités de protection contre les menaces dans Microsoft 365 Defender peuvent entraîner certaines actions de correction. Voici quelques exemples :

- [Les enquêtes automatisées](m365d-autoir.md) peuvent entraîner des actions de correction qui sont effectuées automatiquement ou attendent votre approbation.
- Antivirus, logiciel anti-programme malveillant et autres fonctionnalités de protection contre les menaces peuvent entraîner des actions de correction, telles que le blocage d’un fichier, d’une URL ou d’un processus, ou l’envoi d’un artefact en quarantaine.
- Votre équipe chargée des opérations de sécurité peut effectuer des actions de correction manuellement, par exemple pendant la [chasse avancée](advanced-hunting-overview.md) ou lors de l’examen [des alertes](investigate-alerts.md) ou [des incidents](investigate-incidents.md).

> [!NOTE]
> Vous devez disposer des [autorisations appropriées](m365d-action-center.md#required-permissions-for-action-center-tasks) pour approuver ou rejeter les actions de correction. Pour plus d’informations, consultez les [prérequis](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

## <a name="review-pending-actions-in-the-action-center"></a>Passer en revue les actions en attente dans le Centre d’actions

Il est important d’approuver (ou de refuser) les actions en attente dès que possible de sorte que vos enquêtes automatisées puissent se poursuivre et se terminer dans un délai raisonnable. 

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Dans le centre d’actions, sous l’onglet **En attente** , sélectionnez un élément dans la liste. Son volet volant s’ouvre. Voici un exemple.

   :::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Options d’approbation ou de rejet d’une action" lightbox="../../media/air-actioncenter-itemselected.png":::

4. Passez en revue les informations contenues dans le volet volant, puis effectuez l’une des étapes suivantes :
   - Sélectionnez **Ouvrir la page d’enquête** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Refuser** pour empêcher l’exécution d’une action en attente.
   - Sélectionnez **Go Hunt** pour passer à [la chasse avancée](advanced-hunting-overview.md). 

## <a name="undo-completed-actions"></a>Annuler les actions terminées

Si vous avez déterminé qu’un appareil ou un fichier n’est pas une menace, vous pouvez annuler les actions de correction qui ont été effectuées, que ces actions aient été effectuées automatiquement ou manuellement. Dans le centre d’actions, sous l’onglet **Historique** , vous pouvez annuler l’une des actions suivantes :  

| Source de l’action | Actions prises en charge |
|:---|:---|
| - Investigation automatisée <br/>- Antivirus Microsoft Defender <br/>- Actions de réponse manuelles | - Isoler l’appareil <br/>- Restreindre l’exécution du code <br/>- Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche planifiée |

### <a name="undo-one-remediation-action"></a>Annuler une action de correction

1. Accédez au centre d’action ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) et connectez-vous.

2. Sous l’onglet **Historique** , sélectionnez une action à annuler.

3. Dans le volet à droite de l’écran, sélectionnez **Annuler**.

### <a name="undo-multiple-remediation-actions"></a>Annuler plusieurs actions de correction

1. Accédez au centre d’action (https://security.microsoft.com/action-center) et connectez-vous.

2. Sous l’onglet **Historique** , sélectionnez les actions que vous souhaitez annuler. Veillez à sélectionner les éléments qui ont le même type d’action. Un volet volant s’ouvre.

3. Dans le volet de menu volant, sélectionnez **Annuler**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Pour supprimer un fichier de la quarantaine sur plusieurs appareils 

1. Accédez au centre d’action ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) et connectez-vous.

2. Sous l’onglet **Historique** , sélectionnez un fichier qui a un type d’action de **fichier de quarantaine** .

3. Dans le volet à droite de l’écran, **sélectionnez Appliquer à X autres instances de ce fichier**, puis **sélectionnez Annuler**.

## <a name="next-steps"></a>Prochaines étapes

- [Consulter les détails et les résultats d'un examen automatisé](m365d-autoir-results.md)
- [Résoudre les faux positifs ou les faux négatifs](m365d-autoir-report-false-positives-negatives.md)
