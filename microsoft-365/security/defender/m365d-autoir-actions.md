---
title: Afficher et gérer les actions dans le Centre d’actions
description: Utiliser le Centre d’actions pour afficher et gérer les actions de correction
keywords: action, center, autoair, automated, investigation, response, remediation
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 07/27/2022
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
ms.openlocfilehash: b6cd87846b9225ced8a818252ef5b0e90e562470
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67482073"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>Afficher et gérer les actions dans le Centre d’actions

**S’applique à :**
- Microsoft 365 Defender

Les fonctionnalités de protection contre les menaces dans Microsoft 365 Defender peuvent entraîner certaines actions de correction. Voici quelques exemples :

- [Les enquêtes automatisées](m365d-autoir.md) peuvent entraîner des actions de correction qui sont effectuées automatiquement ou attendent votre approbation.
- Antivirus, logiciel anti-programme malveillant et autres fonctionnalités de protection contre les menaces peuvent entraîner des actions de correction, telles que le blocage d’un fichier, d’une URL ou d’un processus, ou l’envoi d’un artefact en quarantaine.
- Votre équipe chargée des opérations de sécurité peut effectuer des actions de correction manuellement, par exemple pendant la [chasse avancée](advanced-hunting-overview.md) ou lors de l’examen [des alertes](investigate-alerts.md) ou [des incidents](investigate-incidents.md).

> [!NOTE]
> Vous devez disposer des [autorisations appropriées](m365d-action-center.md#required-permissions-for-action-center-tasks) pour approuver ou rejeter les actions de correction. Pour plus d’informations, consultez les [prérequis](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

Pour accéder au Centre d’actions, effectuez l’une des étapes suivantes :

- Accédez à [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center); ou
- Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans la carte de réponse & examen automatisé, **sélectionnez Approuver dans le Centre d’actions**.

## <a name="review-pending-actions-in-the-action-center"></a>Examiner les actions en attente dans le centre d'action

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
