---
title: Évaluation du réseau Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
description: Évaluation du réseau Microsoft 365
ms.openlocfilehash: 641b1b756872a6addfa5050276cc78cc257e4c86
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68169406"
---
# <a name="microsoft-365-network-assessment"></a>Évaluation du réseau Microsoft 365

Dans la connectivité réseau du centre Administration Microsoft 365, **les évaluations réseau** distillent un agrégat de nombreuses métriques de performances réseau en un instantané de l’intégrité du périmètre réseau de votre entreprise. Une évaluation réseau vous indique l’impact de la conception de réseau responsable du client Office 365 l’expérience utilisateur. Les évaluations réseau sont limitées à la fois à l’ensemble du locataire et à chaque emplacement géographique à partir duquel les utilisateurs se connectent à votre locataire. Les évaluations fournissent aux administrateurs Microsoft 365 un moyen simple d’obtenir instantanément une idée de l’intégrité du réseau de l’entreprise et d’explorer rapidement un rapport détaillé pour n’importe quel emplacement de bureau mondial.

La valeur des points d’évaluation réseau est comprise entre 0 et 100 et représente une moyenne de la latence TCP, de la vitesse de téléchargement et des métriques de qualité de connexion UDP. Ces métriques sont compilées une fois par jour. Les mesures de performance des réseaux appartenant à Microsoft sont exclues de ces mesures afin de garantir que les résultats de l'évaluation sont sans ambiguïté et spécifiques au réseau d'entreprise.

> [!div class="mx-imgBorder"]
> ![Valeur d’évaluation réseau.](../media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

Une valeur d’évaluation réseau très faible suggère que les clients Microsoft 365 auront d’importants problèmes pour se connecter au locataire ou maintenir une expérience utilisateur réactive. Une valeur élevée indique un réseau correctement configuré avec peu de problèmes de performances en cours. Une valeur de 80 % représente une base de référence saine, au-delà de laquelle vous ne devez pas vous attendre à recevoir régulièrement des plaintes d'utilisateurs concernant la connectivité ou la réactivité de Microsoft 365 en raison des performances du réseau. À mesure que des améliorations itératives de la connectivité réseau sont apportées, cette valeur augmente en même temps que l’expérience utilisateur.

| Évaluation du réseau | Expérience utilisateur attendue |
| :----------------- | :----------------------- |
| 100                | Idéale                     |
| 80                 | Répond aux recommandations    |
| 60                 | Acceptable               |
| 40                 | Les utilisateurs peuvent rencontrer des problèmes |
| 20                 | Les utilisateurs peuvent se plaindre       |
| 0                  | Les problèmes de réseau sont un sujet de discussion courant |

## <a name="network-assessment-panel"></a>Panneau Évaluation du réseau

Chaque évaluation réseau, qu’elle s’applique au locataire ou à un emplacement de bureau spécifique, affiche un panneau contenant des détails sur l’évaluation. Ce panneau affiche un graphique à barres de l’évaluation sous forme de pourcentage et de points totaux pour chaque charge de travail de composant, y compris uniquement les charges de travail où les données de mesure ont été reçues. Pour une évaluation du réseau d’emplacement de bureau, nous montrons également une comparaison avec le pourcentage de clients Microsoft 365 dans chacun des cinq clusters qui ont signalé des données dans la même ville que votre emplacement de bureau.

> [!div class="mx-imgBorder"]
> ![Exemple de valeur d’évaluation réseau.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

La **répartition de l’évaluation** dans le panneau montre l’évaluation pour chacune des charges de travail des composants.

**L’historique d’évaluation** indique les 30 derniers jours de l’évaluation et le benchmark. Vous pouvez également créer un rapport sur l’historique des métriques pour n’importe quel emplacement de bureau pendant deux ans au maximum à l’aide de l’onglet Historique. L’onglet Historique vous permet de sélectionner vos attributs sur lesquels créer des rapports. En choisissant une période de rapport, vous pouvez mettre en évidence l’impact d’un projet de mise à jour réseau et voir l’amélioration de votre évaluation réseau.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Évaluations réseau des locataires et évaluations réseau de l’emplacement des bureaux

Une évaluation réseau mesure la conception du périmètre réseau d’un emplacement de bureau sur le réseau de Microsoft. Les améliorations apportées au périmètre réseau sont préférables à chaque emplacement de bureau.

Nous affichons une valeur d’évaluation réseau pour l’ensemble du locataire Microsoft 365 sur la page vue d’ensemble des performances réseau. Cette valeur est une moyenne pondérée des évaluations réseau pour tous les emplacements de bureau. Il existe également une valeur d’évaluation réseau spécifique pour chaque emplacement de bureau détecté sur la page récapitulative de cet emplacement.

## <a name="exchange-online"></a>Exchange Online

Pour Exchange Online, la latence TCP entre l’ordinateur client et la porte d’entrée du service Exchange est mesurée. Cette latence peut être affectée par la distance parcourue par le réseau sur le réseau local et le RÉSEAU ÉTENDU des clients. Il peut également être affecté par les appareils ou services intermédiaires réseau, qui retardent la connectivité ou provoquent le réentrain des paquets. Et elle est affectée par l’éloignement de la porte d’entrée du service Exchange la plus proche. La médiane (également appelée 50e centile ou mesure P50) est prise pour toutes les mesures au cours des trois derniers jours.

L’évaluation Exchange Online est effectuée à l’aide du tableau suivant. Tout numéro de latence TCP entre les seuils se voit attribuer des points de manière linéaire dans la bande.

| Latence TCP   | Points |
| :------------ | :----- |
| 10 ms ou moins  | 100    |
| 25 ms          | 80     |
| 100 ms         | 60     |
| 200 ms         | 40     |
| 300 ms         | 20     |
| 350 ms ou plus | 0      |

## <a name="sharepoint-online"></a>SharePoint Online

Pour SharePoint Online, la vitesse de téléchargement disponible pour qu’un utilisateur accède à un document à partir de SharePoint ou OneDrive est mesurée. Cela peut être affecté par la bande passante disponible sur les circuits réseau entre la machine cliente et le réseau de Microsoft. Il est également souvent affecté par la congestion du réseau qui existe dans les goulots d’étranglement dans les périphériques réseau complexes ou dans les zones de couverture Wi-Fi pauvres. La vitesse de téléchargement est mesurée en mégaoctets par seconde, soit environ un dixième d’un circuit évalué en mégabits par seconde. L’unité MegaByte par seconde est utile, car vous pouvez voir directement quel fichier de taille peut être téléchargé en 1 seconde. Le 25e centile (également appelé mesure P25) est pris pour toutes les mesures effectuées au cours des trois derniers jours. Ce 25e centile permet de réduire l’impact de la congestion variable au fil du temps.

L’évaluation SharePoint Online est effectuée à l’aide du tableau suivant. Tout numéro de vitesse de téléchargement entre les seuils se voit attribuer des points de manière linéaire au sein de la bande.

| Vitesse de téléchargement | Points |
| :------------- | :----- |
| 20 Mbits/s ou plus | 100    |
| 14 Mbits/s         | 80     |
| 8 Mbits/s          | 60     |
| 4 Mbits/s          | 40     |
| 2 Mbits/s          | 20     |
| 0 Mbits/s          | 0      |

## <a name="microsoft-teams"></a>Microsoft Teams

Pour Microsoft Teams, la qualité du réseau est mesurée en tant que latence UDP, instable UDP et perte de paquets UDP. UDP est utilisé pour la connectivité audio et vidéo des appels et des conférences pour Microsoft Teams. Cela peut être affecté par les mêmes facteurs que pour la latence et la vitesse de téléchargement, en plus des lacunes de connectivité dans la prise en charge UDP d’un réseau, car UDP est configuré séparément avec le protocole TCP le plus courant. La médiane (également appelée 50e centile ou mesure P50) est prise pour toutes les mesures au cours des trois derniers jours. 

Nous calculons un score d’opinion moyen à partir de ces mesures UDP pour une échelle comprise entre 1 et 5. Ensuite, nous mappons cela à l’échelle de 0 à 100 points pour l’évaluation du réseau Microsoft Teams.  Le bon global est supérieur à 87,5 points et le mauvais global est inférieur à 50 points.

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le centre de Administration Microsoft 365](office-365-network-mac-perf-overview.md)

[Insights sur les performances réseau de Microsoft 365](office-365-network-mac-perf-insights.md)

[Outil de test de la connectivité du réseau Microsoft 365](office-365-network-mac-perf-onboarding-tool.md)

[Services d’emplacement de connectivité réseau Microsoft 365](office-365-network-mac-location-services.md)
