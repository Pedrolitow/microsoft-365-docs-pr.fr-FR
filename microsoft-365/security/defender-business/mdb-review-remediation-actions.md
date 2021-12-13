---
title: Passer en revue les actions de correction dans Microsoft Defender pour Entreprise (prévisualisation)
description: Afficher les corrections qui ont été prises automatiquement ou qui sont en attente d’approbation dans le centre de mise en œuvre
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 12/10/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 314bb913a161e21ef61c09568cd87aad61ccd10e
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61421869"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Passer en revue les actions de correction dans le centre de mise à jour

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Cet article inclut des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Microsoft Defender pour Entreprises (prévisualisation).

À mesure que les menaces sont détectées, des actions de correction entrent en jeu. En fonction de la menace particulière et de la façon dont vos paramètres de sécurité sont configurés, des actions de correction peuvent être prises automatiquement ou uniquement après approbation. L’envoi d’un fichier en quarantaine, l’arrêt d’un processus et la suppression d’une tâche programmée sont des exemples d’actions de correction. Toutes les actions de correction sont suivis dans le centre de correction.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Capture d’écran du centre de l’action":::

**Cet article décrit**:

- [Utilisation du centre de travail](#how-to-use-the-action-center)
- [Actions de correction](#remediation-actions)

## <a name="how-to-use-the-action-center"></a>Utilisation du centre de travail

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ), and sign in.

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