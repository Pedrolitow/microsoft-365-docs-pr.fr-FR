---
title: Passer en revue les actions de correction dans Microsoft Defender pour Entreprise (prévisualisation)
description: Afficher les corrections qui ont été prises automatiquement ou qui sont en attente d’approbation dans le centre de mise en œuvre
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f1128b5fd9c27845bebbd4b6a0b45f93c5f3e0c6
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62464546"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Passer en revue les actions de correction dans le centre de mise à jour

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et sera progressivement mis en place pour les clients [](https://aka.ms/mdb-preview) et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et que nous ajouterons régulièrement des fonctionnalités.
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

Microsoft Defender pour Entreprise (prévisualisation) inclut plusieurs actions de correction. Ces actions incluent les actions de réponse manuelles, les actions qui suivent un examen automatisé et les actions de réponse en direct.

Le tableau suivant répertorie les actions de correction disponibles :

| Source  | Actions  |
|---------|---------|
| [Enquêtes automatisées](../defender-endpoint/automated-investigations.md)      | - Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Kill a process <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche programmée        |
| [Actions de réponse manuelles](../defender-endpoint/respond-machine-alerts.md)   | - Exécuter une analyse antivirus <br/>- Isoler l’appareil <br/>- Arrêter et mettre en quarantaine <br/>- Ajouter un indicateur pour bloquer ou autoriser un fichier       |
| [Réponse en direct](../defender-endpoint/live-response.md)   | - Collecter des données d’investigation <br/>- Analyser un fichier <br/>- Exécuter un script <br/>- Envoyer une entité suspecte à Microsoft pour analyse <br/>- Corriger un fichier <br/>- Recherche proactive des menaces         |

## <a name="next-steps"></a>Prochaines étapes

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Gérer les appareils dans Microsoft Defender pour Entreprises (prévisualisation)](mdb-manage-devices.md)