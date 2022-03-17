---
title: Passer en revue les actions de correction dans Microsoft Defender pour les entreprises
description: Afficher les corrections qui ont été prises automatiquement ou qui sont en attente d’approbation dans le centre de mise en œuvre
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/10/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b5bb61d4a0b8f3cb0732633463fbf2c96ec258e9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525513"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Passer en revue les actions de correction dans le centre de mise à jour

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement [Microsoft 365 Business Premium clients,](../../business-premium/index.md) à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

À mesure que les menaces sont détectées, des actions de correction entrent en jeu. En fonction de la menace particulière et de la façon dont vos paramètres de sécurité sont configurés, des actions de correction peuvent être prises automatiquement ou uniquement après approbation. L’envoi d’un fichier en quarantaine, l’arrêt d’un processus et la suppression d’une tâche programmée sont des exemples d’actions de correction. Toutes les actions de correction sont suivis dans le centre de correction.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Capture d’écran du centre de l’action":::

**Cet article décrit** :

- [Utilisation du centre de travail](#how-to-use-the-action-center)

- [Actions de correction](#remediation-actions)

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="how-to-use-the-action-center"></a>Utilisation du centre de travail

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in.

2. Dans le volet de navigation, choisissez **Centre de notifications**.

3. Sélectionnez **l’onglet En** attente pour afficher et approuver (ou rejeter) les actions en attente. De telles actions peuvent survenir à partir d’une protection antivirus/anti-programme malveillant, d’enquêtes automatisées, d’activités de réponse manuelles ou de sessions de réponse en direct.

4. Sélectionnez **l’onglet** Historique pour afficher la liste des actions terminées. 

## <a name="remediation-actions"></a>Actions de correction

Microsoft Defender pour les entreprises inclut plusieurs actions de correction. Ces actions incluent les actions de réponse manuelles, les actions qui suivent un examen automatisé et les actions de réponse en direct.

Le tableau suivant répertorie les actions de correction disponibles :

| Source  | Actions  |
|---------|---------|
| [Enquêtes automatisées](../defender-endpoint/automated-investigations.md)      | - Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Kill a process <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche programmée        |
| [Actions de réponse manuelles](../defender-endpoint/respond-machine-alerts.md)   | - Exécuter une analyse antivirus <br/>- Isoler l’appareil <br/>- Arrêter et mettre en quarantaine <br/>- Ajouter un indicateur pour bloquer ou autoriser un fichier       |
| [Réponse en direct](../defender-endpoint/live-response.md)   | - Collecter des données d’investigation <br/>- Analyser un fichier <br/>- Exécuter un script <br/>- Envoyer une entité suspecte à Microsoft pour analyse <br/>- Corriger un fichier <br/>- Recherche proactive des menaces         |

## <a name="next-steps"></a>Prochaines étapes

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise](mdb-respond-mitigate-threats.md)

- [Gérer les appareils dans Microsoft Defender pour les entreprises](mdb-manage-devices.md)