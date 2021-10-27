---
title: Examiner Microsoft Defender pour les domaines de point de terminaison
description: Utilisez les options d’examen pour déterminer si les appareils et les serveurs communiquent avec des domaines malveillants.
keywords: examiner le domaine, le domaine, le domaine malveillant, Microsoft Defender pour le point de terminaison, alerte, URL
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 9f2514c0f43bd8a7f1ab5dade389c0a12f3c4e54
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60587788"
---
# <a name="investigate-a-domain-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Examiner un domaine associé à une alerte Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatedomain-abovefoldlink)

Examinez un domaine pour voir si les appareils et les serveurs de votre réseau d’entreprise communiquent avec un domaine malveillant connu.

Vous pouvez examiner un domaine à l’aide de la fonctionnalité de recherche ou en cliquant sur un lien de domaine à partir de la chronologie **de l’appareil.**

Vous pouvez voir les informations des sections suivantes dans l’affichage URL :

- Détails de l’URL, Contacts, Serveurs de noms
- Alertes associées à cette URL 
- URL dans l’organisation
- Appareils les plus récemment observés avec UNE URL

## <a name="url-worldwide"></a>URL dans le monde entier

La section **URL dans le** monde entier répertorie l’URL, un lien vers d’autres détails sur Whois, le nombre d’incidents ouverts connexes et le nombre d’alertes actives.

## <a name="incident"></a>Incident

La **carte Incident** affiche un graphique à barres de toutes les alertes actives dans les incidents au cours des 180 derniers jours.

## <a name="prevalence"></a>Prévalence

La **carte de** prévalence fournit des détails sur la prévalence de l’URL au sein de l’organisation, sur une période spécifiée.

Bien que la période par défaut soit les 30 derniers jours, vous pouvez personnaliser la plage en sélectionnant la flèche pointant vers le bas dans le coin de la carte. La plage la plus courte disponible est pour la prévalence au cours du dernier jour, tandis que la plage la plus longue se trouve sur les 6 derniers mois.

## <a name="alerts"></a>Alertes

**L’onglet Alertes** fournit une liste des alertes associées à l’URL. Le tableau présenté ici est une version filtrée des alertes visibles sur l’écran de file d’attente des alertes, affichant uniquement les alertes associées au domaine, leur gravité, leur état, l’incident associé, la classification, l’état de l’enquête, etc.

L’onglet Alertes peut être ajusté pour afficher plus  ou moins d’informations, en sélectionnant Personnaliser les colonnes dans le menu Actions au-dessus des en-têtes de colonne. Le nombre d’éléments affichés peut également être ajusté en sélectionnant des **éléments par page** dans le même menu.

## <a name="observed-in-organization"></a>Observé dans l’organisation

**L’onglet Observé dans l’organisation** fournit une vue chronologique des événements et des alertes associées qui ont été observés sur l’URL. Cet onglet inclut une chronologie et un tableau personnalisable répertoriant les détails des événements, tels que l’heure, l’appareil et une brève description de ce qui s’est passé. 

Vous pouvez afficher les événements de différentes périodes en entrant les dates dans les champs de texte au-dessus des en-têtes de tableau. Vous pouvez également personnaliser l’plage de temps en sélectionnant différentes zones de la chronologie.

**Examinez un domaine :**

1. Sélectionnez **l’URL** dans le menu déroulant **de** la barre de recherche.
2. Entrez l’URL dans le **champ** Recherche.
3. Cliquez sur l’icône de recherche ou appuyez sur **Entrée.** Des détails sur l’URL sont affichés. Remarque : les résultats de la recherche seront renvoyés uniquement pour les URL observées dans les communications à partir d’appareils de l’organisation.
4. Utilisez les filtres de recherche pour définir les critères de recherche. Vous pouvez également utiliser la zone de recherche de chronologie pour filtrer les résultats affichés de tous les appareils de l’organisation observés en communication avec l’URL, le fichier associé à la communication et la dernière date observée.
5. En cliquant sur l’un des noms d’appareils, vous pouvez continuer à examiner les alertes, comportements et événements signalés.

## <a name="related-topics"></a>Voir aussi
- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes microsoft Defender pour les points de terminaison](manage-alerts.md)
- [Examiner microsoft Defender pour les alertes de point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte Microsoft Defender pour le point de terminaison](investigate-files.md)
- [Examiner les appareils de la liste Microsoft Defender pour les appareils de point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour le point de terminaison](investigate-ip.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour le point de terminaison](investigate-user.md)
