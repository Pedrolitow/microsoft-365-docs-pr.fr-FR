---
title: Passer en revue les actions de correction dans Microsoft Defender pour les PME
description: Afficher les corrections qui ont été effectuées automatiquement ou qui sont en attente d’approbation dans le Centre d’action
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 15a64491f6e97137d1e919aa126d4bf134c47999
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862211"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Passer en revue les actions de correction dans le Centre d’actions

> [!NOTE]
> Microsoft Defender pour les PME est désormais inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md). 

À mesure que des menaces sont détectées, des actions de correction entrent en jeu. En fonction de la menace particulière et de la façon dont vos paramètres de sécurité sont configurés, des actions de correction peuvent être effectuées automatiquement ou uniquement après approbation. Parmi les actions de correction, citons l’envoi d’un fichier en quarantaine, l’arrêt de l’exécution d’un processus et la suppression d’une tâche planifiée. Toutes les actions de correction sont suivies dans le Centre d’actions.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Capture d’écran du centre d’actions":::

**Cet article décrit :**

- [Comment utiliser le Centre d’actions](#how-to-use-the-action-center)
- [Actions de correction](#remediation-actions)

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="how-to-use-the-action-center"></a>Comment utiliser le Centre d’actions

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, choisissez **Centre de notifications**.

3. Sélectionnez l’onglet **En attente** pour afficher et approuver (ou rejeter) les actions en attente. Ces actions peuvent provenir de la protection antivirus/anti-programme malveillant, d’investigations automatisées, d’activités de réponse manuelle ou de sessions de réponse en direct.

4. Sélectionnez l’onglet **Historique** pour afficher la liste des actions terminées. 

## <a name="remediation-actions"></a>Actions de correction

Microsoft Defender pour les PME comprend plusieurs actions de correction. Ces actions incluent des actions de réponse manuelles, des actions qui suivent une investigation automatisée et des actions de réponse en direct.

Le tableau suivant répertorie les actions de correction disponibles :

| Source  | Actions  |
|---------|---------|
| [Enquêtes automatisées](../defender-endpoint/automated-investigations.md)      | - Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Tuer un processus <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche planifiée        |
| [Actions de réponse manuelle](../defender-endpoint/respond-machine-alerts.md)   | - Exécuter l’analyse antivirus <br/>- Isoler l’appareil <br/>- Arrêter et mettre en quarantaine <br/>- Ajouter un indicateur pour bloquer ou autoriser un fichier       |
| [Réponse en direct](../defender-endpoint/live-response.md)   | - Collecter des données légales <br/>- Analyser un fichier <br/>- Exécuter un script <br/>- Envoyer une entité suspecte à Microsoft pour analyse <br/>- Corriger un fichier <br/>- Rechercher de manière proactive les menaces         |

## <a name="next-steps"></a>Prochaines étapes

- [Répondre aux menaces et les atténuer dans Microsoft Defender pour les PME](mdb-respond-mitigate-threats.md)
- [Gérer les appareils dans Microsoft Defender pour les PME](mdb-manage-devices.md)