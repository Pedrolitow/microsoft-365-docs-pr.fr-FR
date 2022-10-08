---
title: Passer en revue les actions de correction dans Microsoft Defender pour entreprises
description: Affichez les corrections qui ont été prises sur les menaces détectées avec Defender entreprise. Vous pouvez afficher les actions dans le Centre d’actions dans le portail Microsoft 365 Defender.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 08/11/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- m365-initiative-defender-business
- tier1
ms.openlocfilehash: 064ad2551899047cd87d65b4b1d4e9587bb1c952
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68097333"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Passer en revue les actions de correction dans le Centre d’actions

Au fur et à mesure que des menaces sont détectées, des actions de correction entrent en jeu. En fonction de la menace particulière et de la façon dont vos paramètres de sécurité sont configurés, des actions de correction peuvent être effectuées automatiquement ou uniquement après approbation. Voici quelques exemples d’actions de correction : 
- Envoyer un fichier en quarantaine
- Arrêter l’exécution d’un processus
- Supprimer une tâche planifiée

Toutes les actions de correction sont suivies dans le Centre de notifications.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Capture d’écran du centre d’actions":::

**Cet article décrit**:

- [Comment utiliser le centre de notifications](#how-to-use-the-action-center)
- [Actions de correction](#remediation-actions)


## <a name="how-to-use-the-action-center"></a>Comment utiliser le Centre d’actions

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Centre de notifications**.

3. Sélectionnez l’onglet **En attente** pour afficher et approuver (ou rejeter) les actions en attente. Les actions peuvent provenir de la protection antivirus/anti-programme malveillant, d’investigations automatisées, d’activités de réponse manuelle ou de sessions de réponse en direct.

4. Sélectionnez l’onglet **Historique** pour afficher la liste des actions terminées.

## <a name="remediation-actions"></a>Actions de correction

Defender entreprise inclut plusieurs actions de correction. Ces actions incluent des actions de réponse manuelles, des actions qui suivent une investigation automatisée et des actions de réponse dynamique.

Le tableau suivant répertorie les actions de correction disponibles.

| Source  | Actions  |
|---------|---------|
| [Enquêtes automatisées](../defender-endpoint/automated-investigations.md)      |<ul><li>Mettre en quarantaine un fichier</li><li>Supprimer une clé de Registre</li><li>Tuer un processus</li><li>Arrêter un service</li><li>Désactiver un pilote</li><li>Supprimer une tâche planifiée </li></ul> |
| [Actions de réponse manuelle](../defender-endpoint/respond-machine-alerts.md)   |<ul><li>Exécuter une analyse antivirus</li><li>Isoler un appareil</li><li>Arrêter et mettre en quarantaine</li><li>Ajouter un indicateur pour bloquer ou autoriser un fichier</li></ul> |
| [Réponse en direct](../defender-endpoint/live-response.md)   |<ul><li>Collecter des données légales</li><li>Analyser un fichier</li><li>Exécuter un script</li><li>Envoyer une entité suspecte à Microsoft pour analyse</li><li>Corriger un fichier </li><li>Repérage proactif des menaces</li></ul>|

## <a name="next-steps"></a>Prochaines étapes

- [Répondre aux menaces et les atténuer dans Defender entreprise](mdb-respond-mitigate-threats.md)
- [Gérer les appareils dans Defender entreprise](mdb-manage-devices.md)
