---
title: Approuver ou rejeter les actions en attente à la suite d’un examen automatisé
description: Utiliser le centre d’actions pour gérer les actions liées à une enquête et une réponse automatisées
keywords: action, center, autoair, automated, investigation, response, remediation
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.date: 12/09/2020
ms.technology: m365d
ms.openlocfilehash: 3776dea4a5a24f4695a5c617325af14f1f03494f
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930377"
---
# <a name="approve-or-reject-pending-actions-following-an-automated-investigation"></a>Approuver ou rejeter les actions en attente à la suite d’un examen automatisé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Lorsqu’une enquête automatisée s’exécute, elle peut engendrer une ou plusieurs [actions de correction](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-remediation-actions) nécessitant une approbation pour continuer. Par exemple, il peut être nécessaire de supprimer un cluster d’e-mails ou un fichier mis en quarantaine. Il est important d’approuver (ou de refuser) les actions en attente dès que possible de sorte que vos enquêtes automatisées puissent se poursuivre et se terminer dans un délai raisonnable. 

> [!TIP]
> Si vous pensez que quelque chose a été manqué ou détecté à tort par les fonctionnalités d’investigation et de réponse automatisées dans Microsoft 365 Defender, faites-le nous savoir ! Découvrez comment signaler les faux positifs/négatifs dans les fonctionnalités d’investigation et de réponse [automatisées (AIR) dans Microsoft 365 Defender.](mtp-autoir-report-false-positives-negatives.md)

Les actions en attente peuvent être examinées et approuvées à l’aide du centre [de](#review-a-pending-action-in-the-action-center) actions ou de l’affichage [détails de l’enquête.](#review-a-pending-action-in-the-investigation-details-view)

> [!NOTE]
> Vous devez disposer des [autorisations appropriées](mtp-action-center.md#required-permissions-for-action-center-tasks) pour approuver ou rejeter les actions de correction. Pour plus d’informations, voir [Conditions préalables à l’examen et à la réponse automatisés dans Microsoft 365 Defender.](mtp-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)

## <a name="review-a-pending-action-in-the-action-center"></a>Examiner une action en attente dans le centre de notifications

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Dans le centre de notifications, dans l’onglet **En attente**, sélectionnez un élément dans la liste. 

    - Si vous sélectionnez un élément dans la colonne **Numéro de l’enquête**, la page Détails de l’enquête s’ouvre. Là, vous pouvez afficher les résultats de l’enquête, puis approuver ou rejeter l’action recommandée.
 
    - Si vous sélectionnez une ligne dans la liste, un menu volant affiche des informations relatives à cet élément. <br/>![Approuver ou rejeter une action](../../media/air-actioncenter-itemselected.png)<br/>Utilisez les liens pour afficher une alerte ou une enquête associée, puis approuvez ou refusez l’action.

## <a name="review-a-pending-action-in-the-investigation-details-view"></a>Examiner une action en attente dans la vue de détails de l’enquête

![Détails de l’enquête](../../media/mtp-air-investdetails.png)

1. Sur une page de [détails de l’enquête](mtp-autoir-results.md), sélectionnez l’onglet **Actions en attente** (ou **Actions**). Les éléments en attente d’approbation sont répertoriés ici.

2. Sélectionnez un élément dans la liste, puis choisissez **Approuver** ou **Rejeter**.

## <a name="undo-completed-actions"></a>Annuler les actions terminées

Si vous avez déterminé qu’un appareil ou un fichier n’est pas une menace, vous pouvez annuler les actions de correction qui ont été prises, que ces actions soient prises automatiquement ou manuellement. Dans le centre de actions, sous **l’onglet** Historique, vous pouvez annuler l’une des actions suivantes :  

| Source d’action | Actions prises en charge |
|:---|:---|
| - Examen automatisé <br/>- Antivirus Microsoft Defender <br/>- Actions de réponse manuelles | - Isoler l’appareil <br/>- Restreindre l’exécution du code <br/>- Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche programmée |

### <a name="to-undo-a-remediation-action"></a>Pour annuler une action de correction

1. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) and sign in.

2. Sous **l’onglet** Historique, sélectionnez une action à annuler.

3. Dans le volet sur le côté droit de l’écran, sélectionnez **Annuler**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Pour supprimer un fichier de la quarantaine sur plusieurs appareils 

1. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) and sign in.

2. Sous **l’onglet** Historique, sélectionnez un fichier dont le fichier de mise en quarantaine du type d’action **est sélectionné.**

3. Dans le volet sur le côté droit de l’écran, sélectionnez Appliquer à **X plus d’instances** de ce fichier, puis **sélectionnez Annuler**.

## <a name="next-steps"></a>Étapes suivantes

- [Consulter les détails et les résultats d'un examen automatisé](mtp-autoir-results.md)
- [Gérer les faux positifs/négatifs dans les fonctionnalités automatisées d’examen et de réponse](mtp-autoir-report-false-positives-negatives.md)
