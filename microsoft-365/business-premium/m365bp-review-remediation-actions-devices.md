---
title: Examiner les actions de correction dans Microsoft 365 Business Premium
description: Découvrez comment afficher les corrections effectuées automatiquement ou en attente d’approbation dans le Centre de notifications.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-security
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- m365-initiative-defender-business
- tier1
ms.openlocfilehash: 1ae134f0c6a00fa00d5a5196b9dc20b9419033da
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68097948"
---
# <a name="review-remediation-actions-in-microsoft-365-business-premium"></a>Examiner les actions de correction dans Microsoft 365 Business Premium

Ok, vous avez découvert une violation de sécurité, mais que faites-vous ? Cela dépend de sa nature.

L’envoi d’un fichier en quarantaine, l’arrêt d’un processus ou la suppression complète d’une tâche planifiée sont des exemples d’actions de correction. Toutes les actions de correction sont suivies dans le centre de notifications, qui se trouve à [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center).

:::image type="content" source="../media/defender-business/mdb-actioncenter.png" alt-text="Capture d’écran du Centre de notifications dans M365.":::

**Cet article décrit**:

- [Comment utiliser le Centre de notifications](#how-to-use-your-action-center).
- [Types d’actions de correction](#types-of-remediation-actions).


## <a name="how-to-use-your-action-center"></a>Comment utiliser votre centre de notifications

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, choisissez **Centre de notifications**.

3. Sélectionnez l’onglet **En attente** pour afficher et approuver (ou rejeter) les actions en attente. Ces actions peuvent provenir d’une protection antivirus/anti-programme malveillant, d’investigations automatisées, d’activités de réponse manuelle ou de sessions de réponse en direct.

4. Sélectionnez l’onglet **Historique** pour afficher la liste des actions terminées.

## <a name="types-of-remediation-actions"></a>Types d’actions de correction

Votre abonnement inclut plusieurs types d’actions de correction pour les menaces détectées. Ces actions incluent des actions de réponse manuelles, des actions qui suivent une investigation automatisée et des actions de réponse dynamique.

Le tableau suivant répertorie les actions de correction disponibles :

| Source  | Actions  |
|---------|---------|
| [Enquêtes automatisées](../security/defender-endpoint/automated-investigations.md)      | - Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Tuer un processus <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche planifiée        |
| [Actions de réponse manuelle](../security/defender-endpoint/respond-machine-alerts.md)   | - Exécuter une analyse antivirus <br/>- Isoler l’appareil <br/>- Arrêter et mettre en quarantaine <br/>- Ajoutez des indicateurs pour bloquer ou autoriser un fichier.       |
| [Réponse en direct](../security/defender-endpoint/live-response.md)   | - Collecter des données légales <br/>- Analyser un fichier <br/>- Exécuter un script <br/>- Envoyer une entité suspecte à Microsoft pour analyse <br/>- Corriger un fichier <br/>- Repérage proactif des menaces         |
