---
title: Examiner les actions de correction dans Microsoft 365 Business Premium
description: Découvrez comment afficher les corrections qui ont été prises automatiquement ou qui sont en attente d’approbation dans le centre de mise en œuvre
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 160cef2ec7691fbc9debad809b20461a0d3efe23
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526635"
---
# <a name="review-remediation-actions-in-microsoft-365-business-premium"></a>Examiner les actions de correction dans Microsoft 365 Business Premium

À mesure que les menaces sont détectées, des actions de correction entrent en jeu. En fonction de la menace particulière et de la façon dont vos paramètres de sécurité sont configurés, des actions de correction peuvent être prises automatiquement ou uniquement après approbation. L’envoi d’un fichier en quarantaine, l’arrêt d’un processus et la suppression d’une tâche programmée sont des exemples d’actions de correction. Toutes les actions de correction sont suivis dans le centre de actions, qui se trouve à l’emplacement .[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)

:::image type="content" source="../media/defender-business/mdb-actioncenter.png" alt-text="Capture d’écran du centre de actions dans M365.":::

**Cet article décrit** :

- [Utilisation du centre de travail](#how-to-use-your-action-center)

- [Types d’actions de correction](#types-of-remediation-actions)


## <a name="how-to-use-your-action-center"></a>Utilisation de votre centre de travail

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in.

2. Dans le volet de navigation, choisissez **Centre de notifications**.

3. Sélectionnez **l’onglet En** attente pour afficher et approuver (ou rejeter) les actions en attente. De telles actions peuvent survenir à partir d’une protection antivirus/anti-programme malveillant, d’enquêtes automatisées, d’activités de réponse manuelles ou de sessions de réponse en direct.

4. Sélectionnez **l’onglet** Historique pour afficher la liste des actions terminées. 

## <a name="types-of-remediation-actions"></a>Types d’actions de correction

Votre abonnement inclut différents types d’actions de correction pour les menaces détectées. Ces actions incluent les actions de réponse manuelles, les actions qui suivent un examen automatisé et les actions de réponse en direct.

Le tableau suivant répertorie les actions de correction disponibles :

| Source  | Actions  |
|---------|---------|
| [Enquêtes automatisées](../security/defender-endpoint/automated-investigations.md)      | - Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Kill a process <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche programmée        |
| [Actions de réponse manuelles](../security/defender-endpoint/respond-machine-alerts.md)   | - Exécuter une analyse antivirus <br/>- Isoler l’appareil <br/>- Arrêter et mettre en quarantaine <br/>- Ajouter un indicateur pour bloquer ou autoriser un fichier       |
| [Réponse en direct](../security/defender-endpoint/live-response.md)   | - Collecter des données d’investigation <br/>- Analyser un fichier <br/>- Exécuter un script <br/>- Envoyer une entité suspecte à Microsoft pour analyse <br/>- Corriger un fichier <br/>- Recherche proactive des menaces         |
