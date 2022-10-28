---
title: Examiner les domaines et LES URL associés à une alerte Microsoft Defender pour point de terminaison
description: Utilisez les options d’investigation pour voir si les appareils et les serveurs communiquent avec des domaines malveillants.
keywords: examiner le domaine, domaine, domaine malveillant, Microsoft Defender pour point de terminaison, alerte, URL
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
ms.topic: conceptual
ms.date: 04/24/2018
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 7f218836b3b4fe54533fae623217a7781852e2bf
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68769488"
---
# <a name="investigate-domains-and-urls-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Examiner les domaines et LES URL associés à une alerte Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatedomain-abovefoldlink)

Examinez un domaine pour voir si les appareils et les serveurs de votre réseau d’entreprise communiquent avec un domaine malveillant connu.

Vous pouvez examiner une URL ou un domaine à l’aide de la fonctionnalité de recherche, à partir de l’expérience de l’incident (sous l’onglet preuve ou à partir de l’article de l’alerte) ou en cliquant sur le lien URL ou domaine à partir de la **chronologie de l’appareil**.

Vous pouvez voir les informations des sections suivantes dans la vue URL et domaine :

- Détails du domaine, informations de contact de l’inscrit

- Verdict Microsoft

- Incidents liés à cette URL ou à ce domaine

- Prévalence de l’URL ou du domaine dans l’organisation

- Appareils les plus récents observés avec une URL ou un domaine

 ![La section Vue d’ensemble de la nouvelle URL & page de domaine en un clin d’œil.](media/domain-url-overview.png)

## <a name="domain-entity"></a>Entité de domaine

Vous pouvez effectuer un tableau croisé dynamique vers la page de domaine à partir des détails du domaine dans la page URL ou le panneau latéral. Cliquez simplement sur le lien **Afficher la page de domaine** . L’entité de domaine affiche une agrégation de toutes les données des URL avec le nom de domaine complet (FQDN). Par exemple, si un appareil communique avec `sub.domain.tld/path1`et qu’un autre appareil communique avec `sub.domain.tld/path2`, chaque URL de l’objet ci-dessus affiche une observation d’appareil et le domaine affiche les deux observations d’appareil. Dans ce cas, un appareil qui a communiqué avec `othersub.domain.tld/path` n’est pas corrélé à cette page de domaine, mais à `othersub.domain.tld`.

## <a name="url-and-domain-overview"></a>Vue d’ensemble de l’URL et du domaine

La section URL dans le monde entier répertorie l’URL, un lien vers d’autres détails sur Whois, le nombre d’incidents ouverts associés et le nombre d’alertes actives.

### <a name="url-summary-details"></a>Détails du résumé de l’URL

Affiche l’URL d’origine (informations d’URL existantes), avec les paramètres de requête et le protocole au niveau de l’application. Vous trouverez ci-dessous les détails complets du domaine, tels que la date d’inscription, la date de modification et les informations de contact de l’inscrit.

Verdict Microsoft de l’URL ou du domaine et d’une section sur la prévalence des appareils. Dans cette zone, vous pouvez voir le nombre d’appareils qui ont communiqué avec l’URL ou le domaine au cours des 30 derniers jours et basculer immédiatement vers le premier ou le dernier événement dans la chronologie de l’appareil. Pour examiner l’accès initial ou s’il existe toujours une activité malveillante dans votre environnement.

### <a name="incidents-and-alerts"></a>Incidents et alertes

La section Incident et alertes affiche un graphique à barres de toutes les alertes actives dans les incidents au cours des 180 derniers jours.

### <a name="microsoft-verdict"></a>Microsoft Verdict

La section Verdict Microsoft affiche le verdict de l’URL ou du domaine de la bibliothèque Microsoft TI. Il indique si l’URL ou le domaine est déjà appelé hameçonnage ou entité malveillante.

### <a name="prevalence"></a>Prévalence

La section Prévalence fournit des détails sur la prévalence de l’URL au sein de l’organisation, au cours des 30 derniers jours, par exemple et le graphique de tendance, qui indique le nombre d’appareils distincts qui ont communiqué avec l’URL ou le domaine sur une période spécifique. Ci-dessous, si vous pouvez trouver les détails des première et dernière observations d’appareil communiquées avec l’URL au cours des 30 derniers jours, où vous pouvez immédiatement pivoter vers la chronologie de l’appareil, pour examiner l’accès initial à partir du lien hameçonnage, ou s’il existe toujours une communication malveillante dans votre environnement.

## <a name="incident-and-alerts"></a>Incident et alertes

![L’onglet Incident et alertes fournit une liste des incidents associés à l’URL ou au domaine.](media/domain-incidents.png)

L’onglet Incident et alertes fournit une liste des incidents associés à l’URL ou au domaine. Le tableau présenté ici est une version filtrée des incidents visibles sur l’écran File d’attente des incidents, montrant uniquement les incidents associés à l’URL ou au domaine, leur gravité, les ressources affectées, etc.

L’onglet Incidents et alertes peut être ajusté pour afficher plus ou moins d’informations, en sélectionnant **Personnaliser les colonnes** dans le menu Action au-dessus des en-têtes de colonne. Le nombre d’éléments affichés peut également être ajusté en sélectionnant les éléments par page dans le même menu.

## <a name="devices"></a>Appareils

![L’onglet Appareil affiche le nombre d’appareils distincts qui ont communiqué avec l’URL ou le domaine sur une période spécifique.](media/domain-device-overview.png)

L’onglet Appareils fournit une vue chronologique de tous les appareils qui ont été observés pour une URL ou un domaine spécifique. Cet onglet inclut un graphique de tendances et une table personnalisable répertoriant les détails de l’appareil, tels que le niveau de risque, le domaine, etc. En outre, vous pouvez voir les heures du premier et du dernier événement où l’appareil a interagi avec l’URL ou le domaine, ainsi que le type d’action de cet événement. À l’aide du menu en regard du nom de l’appareil, vous pouvez rapidement pivoter vers la chronologie de l’appareil pour examiner plus en détail ce qui s’est passé avant ou après l’événement qui a impliqué cette URL ou ce domaine.

Bien que la période par défaut corresponde aux 30 derniers jours, vous pouvez la personnaliser à partir de la liste déroulante disponible au coin de la carte. La fourchette la plus courte disponible concerne la prévalence au cours de la dernière journée, tandis que la plus longue est au cours des six derniers mois.

À l’aide du bouton Exporter au-dessus de la table, vous pouvez exporter toutes les données dans un fichier .csv (y compris l’heure du premier et du dernier événement et le type d’action), pour une investigation et un rapport plus approfondis.

### <a name="investigate-a-url-or-domain"></a>Examiner une URL ou un domaine

1. Sélectionnez **URL** dans le menu déroulant **barre de recherche** .

2. Entrez l’URL dans le champ **Rechercher** .

3. Cliquez sur l’icône de recherche ou **appuyez sur Entrée**. Les détails de l’URL sont affichés.

   > [!NOTE]
   > Les résultats de la recherche sont retournés uniquement pour les URL observées dans les communications à partir d’appareils de l’organisation.

4. Utilisez les filtres de recherche pour définir les critères de recherche. Vous pouvez également utiliser la zone de recherche de chronologie pour filtrer les résultats affichés de tous les appareils de l’organisation qui communiquent avec l’URL, le fichier associé à la communication et la dernière date observée.

5. En cliquant sur l’un des noms d’appareils, vous accédez à l’affichage de cet appareil, où vous pouvez continuer à examiner les alertes, les comportements et les événements signalés.

## <a name="related-articles"></a>Articles connexes

- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes Microsoft Defender pour point de terminaison](manage-alerts.md)
- [Examiner les alertes Microsoft Defender pour point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte Microsoft Defender pour point de terminaison](investigate-files.md)
- [Examiner les appareils dans la liste des appareils Microsoft Defender pour point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour point de terminaison](investigate-ip.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour point de terminaison](investigate-user.md)
