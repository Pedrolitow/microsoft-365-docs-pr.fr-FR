---
title: Examiner les domaines et les URL associés à une alerte de Microsoft Defender pour point de terminaison
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
- m365-security
- tier2
ms.topic: article
ms.date: 04/24/2018
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 9024268e6a0c254d84f57faf92261aaa4bbf4dae
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68225347"
---
# <a name="investigate-domains-and-urls-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Examiner les domaines et les URL associés à une alerte de Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatedomain-abovefoldlink)

Examinez un domaine pour voir si les appareils et serveurs de votre réseau d’entreprise communiquent avec un domaine malveillant connu. 

Vous pouvez examiner une URL ou un domaine à l’aide de la fonctionnalité de recherche, de l’expérience d’incident (sous l’onglet Preuve ou de l’article d’alerte) ou en cliquant sur l’URL ou le lien de domaine à partir de la **chronologie de l’appareil**.

Vous pouvez voir les informations des sections suivantes dans l’URL et la vue de domaine : 

- Détails du domaine, informations de contact de l’inscrit

- Verdict de Microsoft 

- Incidents liés à cette URL ou à ce domaine 

- Prévalence de l’URL ou du domaine dans l’organisation

- Appareils observés les plus récents avec UNE URL ou un domaine

 ![La section Vue d’ensemble de la nouvelle URL & page de domaine en un clin d’œil.](media/domain-url-overview.png)

### <a name="domain-entity"></a>Entité de domaine

Vous pouvez pivoter vers la page de domaine à partir des détails du domaine dans la page URL ou le panneau latéral, il vous suffit de cliquer sur Afficher le lien de **la page de domaine** . L’entité de domaine affiche une agrégation de toutes les données des URL avec le nom de domaine complet (FQDN). Par exemple, si un appareil est observé communiquant avec `sub.domain.tld/path1`, et qu’un autre appareil est observé communiquant avec `sub.domain.tld/path2`, chaque URL de ce qui précède affiche une observation d’appareil, et le domaine affiche les deux observations d’appareil. Dans ce cas, un appareil qui a communiqué avec `othersub.domain.tld/path` n’est pas corrélé à cette page de domaine, mais à `othersub.domain.tld`.  

## <a name="url-and-domain-overview"></a>Vue d’ensemble de l’URL et du domaine 

La section URL dans le monde entier répertorie l’URL, un lien vers des détails supplémentaires sur Whois, le nombre d’incidents ouverts associés et le nombre d’alertes actives. 

### <a name="url-summary-details"></a>Détails du résumé de l’URL 

Affiche l’URL d’origine (informations d’URL existantes), avec les paramètres de requête et le protocole au niveau de l’application. Vous trouverez ci-dessous les détails complets du domaine, tels que la date d’inscription, la date de modification et les informations de contact de l’inscrit. 

Verdict Microsoft de l’URL ou du domaine et d’une section sur la prévalence des appareils. Dans cette zone, vous pouvez voir le nombre d’appareils qui ont communiqué avec l’URL ou le domaine au cours des 30 derniers jours, et pivoter immédiatement vers le premier ou le dernier événement dans la chronologie de l’appareil. Pour examiner l’accès initial ou s’il existe toujours une activité malveillante dans votre environnement.   

### <a name="incidents-and-alerts"></a>Incidents et alertes 

La section Incident et alertes affiche un graphique à barres de toutes les alertes actives dans les incidents au cours des 180 derniers jours. 

### <a name="microsoft-verdict"></a>Microsoft Verdict 

La section Verdict de Microsoft affiche le verdict de l’URL ou du domaine à partir de la bibliothèque Microsoft TI. Il indique si l’URL ou le domaine est déjà appelé hameçonnage ou entité malveillante.  

### <a name="prevalence"></a>Prévalence 

La section Prévalence fournit les détails sur la prévalence de l’URL au sein de l’organisation, au cours des 30 derniers jours, ainsi que le graphique de tendances, qui indique le nombre d’appareils distincts qui ont communiqué avec l’URL ou le domaine sur une période spécifique. Ci-dessous, si vous pouvez trouver des détails sur la première et la dernière observation de l’appareil communiquées avec l’URL au cours des 30 derniers jours, où vous pouvez pivoter immédiatement vers la chronologie de l’appareil, examiner l’accès initial à partir du lien phish, ou s’il existe toujours une communication malveillante dans votre environnement.  

## <a name="incident-and-alerts"></a>Incident et alertes 

![L’onglet Incidents et alertes fournit la liste des incidents associés à l’URL ou au domaine.](media/domain-incidents.png)

L’onglet Incidents et alertes fournit la liste des incidents associés à l’URL ou au domaine. Le tableau présenté ici est une version filtrée des incidents visibles sur l’écran de file d’attente des incidents, affichant uniquement les incidents associés à l’URL ou au domaine, leur gravité, les ressources affectées, etc.  

L’onglet Incidents et alertes peut être ajusté pour afficher plus ou moins d’informations, en sélectionnant **Personnaliser les colonnes** dans le menu d’action au-dessus des en-têtes de colonne. Vous pouvez également ajuster le nombre d’éléments affichés en sélectionnant des éléments par page dans le même menu. 

## <a name="devices"></a>Appareils

![L’onglet appareil affiche le nombre d’appareils distincts qui ont communiqué avec l’URL ou le domaine sur une période spécifique.](media/domain-device-overview.png)

L’onglet Appareils fournit une vue chronologique de tous les appareils qui ont été observés pour une URL spécifique ou un domaine. Cet onglet inclut un graphique de tendances et un tableau personnalisable répertoriant les détails de l’appareil, tels que le niveau de risque, le domaine et bien plus encore. Au-delà de cela, vous pouvez voir les heures du premier et du dernier événement où l’appareil a interagi avec l’URL ou le domaine, ainsi que le type d’action de cet événement. À l’aide du menu en regard du nom de l’appareil, vous pouvez rapidement pivoter vers la chronologie de l’appareil pour examiner plus en détail ce qui s’est passé avant ou après l’événement qui a impliqué cette URL ou ce domaine.  

Bien que la période par défaut soit les 30 derniers jours, vous pouvez la personnaliser à partir de la liste déroulante disponible au coin de la carte. La plage la plus courte disponible concerne la prévalence au cours de la dernière journée, tandis que la plus longue est celle des six derniers mois.  

À l’aide du bouton d’exportation situé au-dessus du tableau, vous pouvez exporter toutes les données dans un fichier .csv (y compris l’heure du premier et dernier événement et le type d’action), afin d’approfondir l’examen et la création de rapports.

### <a name="investigate-a-url-or-domain"></a>Examiner une URL ou un domaine

1. Sélectionnez **l’URL** dans le menu déroulant de la **barre de recherche** .
 
2. Entrez l’URL dans le champ **De recherche** .
 
3. Cliquez sur l’icône de recherche ou **appuyez sur Entrée**. Des détails sur l’URL sont affichés. 

   > [!NOTE]
   > Les résultats de la recherche ne sont retournés que pour les URL observées dans les communications à partir d’appareils de l’organisation.
   
4. Utilisez les filtres de recherche pour définir les critères de recherche. Vous pouvez également utiliser la zone de recherche de chronologie pour filtrer les résultats affichés de tous les appareils de l’organisation qui communiquent avec l’URL, le fichier associé à la communication et la dernière date observée.
 
5. Si vous cliquez sur l’un des noms d’appareils, vous accédez à la vue de cet appareil, où vous pouvez continuer à examiner les alertes, les comportements et les événements signalés.

## <a name="related-articles"></a>Articles connexes
- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes Microsoft Defender pour point de terminaison](manage-alerts.md)
- [Examiner les alertes Microsoft Defender pour point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte de Microsoft Defender pour point de terminaison](investigate-files.md)
- [Examiner les appareils dans la liste des appareils Microsoft Defender pour point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour point de terminaison](investigate-ip.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour point de terminaison](investigate-user.md)
