---
title: Examiner Microsoft Defender pour point de terminaison domaines
description: Utilisez les options d’investigation pour voir si les appareils et les serveurs communiquent avec des domaines malveillants.
keywords: examiner le domaine, le domaine, le domaine malveillant, Microsoft Defender pour point de terminaison, l’alerte, l’URL
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.openlocfilehash: 9565d80da339722ba070cb4525f0f7339c1ff6ce
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67520970"
---
# <a name="investigate-a-domain-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Examiner un domaine associé à une alerte de Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatedomain-abovefoldlink)

Examinez un domaine pour voir si les appareils et les serveurs de votre réseau d’entreprise communiquent avec un domaine malveillant connu.

Vous pouvez examiner un domaine à l’aide de la fonctionnalité de recherche ou en cliquant sur un lien de domaine à partir de la **chronologie de l’appareil**.

Vous pouvez voir les informations des sections suivantes dans la vue URL :

- Détails de l’URL, contacts, serveurs de noms
- Alertes liées à cette URL 
- URL dans l’organisation
- Appareils observés les plus récents avec URL

## <a name="url-worldwide"></a>URL dans le monde entier

La section **URL Worldwide** répertorie l’URL, un lien vers des détails supplémentaires sur Whois, le nombre d’incidents ouverts associés et le nombre d’alertes actives.

## <a name="incident"></a>Incident

La carte **Incident** affiche un graphique à barres de toutes les alertes actives dans les incidents au cours des 180 derniers jours.

## <a name="prevalence"></a>Prévalence

La carte **Prévalence** fournit des détails sur la prévalence de l’URL au sein de l’organisation, sur une période spécifiée.

Bien que la période par défaut soit les 30 derniers jours, vous pouvez personnaliser la plage en sélectionnant la flèche pointant vers le bas dans le coin de la carte. La plage la plus courte disponible concerne la prévalence au cours de la dernière journée, tandis que la plus longue est celle des six derniers mois.

## <a name="alerts"></a>Alertes

L’onglet **Alertes** fournit la liste des alertes associées à l’URL. Le tableau présenté ici est une version filtrée des alertes visibles sur l’écran de file d’attente des alertes, affichant uniquement les alertes associées au domaine, leur gravité, leur état, l’incident associé, la classification, l’état d’investigation, etc.

L’onglet Alertes peut être ajusté pour afficher plus ou moins d’informations, en sélectionnant **Personnaliser les colonnes** dans le menu d’action au-dessus des en-têtes de colonne. Vous pouvez également ajuster le nombre d’éléments affichés en sélectionnant **des éléments par page** dans le même menu.

## <a name="observed-in-organization"></a>Observé dans l’organisation

**L’onglet Observé dans l’organisation** fournit une vue chronologique des événements et des alertes associées qui ont été observées sur l’URL. Cet onglet inclut une chronologie et une table personnalisable répertoriant les détails de l’événement, tels que l’heure, l’appareil et une brève description de ce qui s’est passé. 

Vous pouvez afficher les événements de différentes périodes en entrant les dates dans les champs de texte au-dessus des en-têtes de table. Vous pouvez également personnaliser l’intervalle de temps en sélectionnant différentes zones de la chronologie.

**Examinez un domaine :**

1. Sélectionnez **l’URL** dans le menu déroulant de la **barre de recherche** .
2. Entrez l’URL dans le champ **De recherche** .
3. Cliquez sur l’icône de recherche ou **appuyez sur Entrée**. Des détails sur l’URL sont affichés. Remarque : les résultats de recherche ne sont retournés que pour les URL observées dans les communications à partir d’appareils de l’organisation.
4. Utilisez les filtres de recherche pour définir les critères de recherche. Vous pouvez également utiliser la zone de recherche de chronologie pour filtrer les résultats affichés de tous les appareils de l’organisation qui communiquent avec l’URL, le fichier associé à la communication et la dernière date observée.
5. Si vous cliquez sur l’un des noms d’appareil, vous accédez à la vue de cet appareil, où vous pouvez continuer à examiner les alertes, les comportements et les événements signalés.

## <a name="related-topics"></a>Voir aussi
- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes Microsoft Defender pour point de terminaison](manage-alerts.md)
- [Examiner les alertes Microsoft Defender pour point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte de Microsoft Defender pour point de terminaison](investigate-files.md)
- [Examiner les appareils dans la liste des appareils Microsoft Defender pour point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour point de terminaison](investigate-ip.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour point de terminaison](investigate-user.md)
