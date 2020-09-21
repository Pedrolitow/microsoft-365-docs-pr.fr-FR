---
title: Microsoft 365 Network Assessment (aperçu)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/17/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 Network Assessment (aperçu)
ms.openlocfilehash: 21fb9515ea1621225cffbe23fe87d0daeb5265de
ms.sourcegitcommit: adaedd1418a3bd6e4875b77fd9e008b47e0b2a51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "48104545"
---
# <a name="microsoft-365-network-assessment-preview"></a>Microsoft 365 Network Assessment (aperçu)

Dans la connectivité réseau du centre d’administration 365 de Microsoft, les **évaluations de réseau** convertissent un ensemble de nombreuses mesures de performances réseau en un instantané de l’état de votre périmètre réseau d’entreprise, représenté par une valeur de points de 0-100. Une évaluation réseau indique le degré d’impact de la conception du réseau responsable du client sur l’expérience utilisateur d’Office 365. Les évaluations réseau sont étendues à la fois à l’ensemble du client et à chaque emplacement géographique à partir duquel les utilisateurs se connectent à votre client, ce qui permet aux administrateurs de Microsoft 365 de mieux appréhender instantanément un Gestalt de l’état du réseau de l’entreprise et d’accéder rapidement à un rapport détaillé sur un emplacement Office global.

La valeur points d’évaluation réseau est une moyenne de la latence TCP, de la vitesse de téléchargement et des mesures de qualité de la connexion UDP compilées une fois par jour. Les mesures de performances des réseaux appartenant à Microsoft sont exclues de ces mesures afin de s’assurer que les résultats de l’évaluation ne sont pas ambigus et spécifiques au réseau d’entreprise.

![Valeur d’évaluation du réseau](../media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

Une évaluation réseau très faible suggère que les clients Microsoft 365 auront des problèmes importants pour se connecter au client ou maintenir une expérience utilisateur réactive, tandis qu’une valeur élevée indique un réseau correctement configuré avec peu de problèmes de performances. Une valeur de 80% représente une base saine, dans laquelle vous ne devez pas vous attendre à recevoir des plaintes d’utilisateur normales concernant la connectivité ou la réactivité Microsoft 365 en raison des performances du réseau. À mesure que des améliorations de connectivité réseau itératives sont apportées, cette valeur augmente en fonction de l’expérience utilisateur.

| Évaluation du réseau | Expérience utilisateur attendue |
| :----------------- | :----------------------- |
| 100                | Idéale                     |
| 80                 | Répond aux recommandations    |
| 60                 | Acceptable               |
| 40                 | Les utilisateurs peuvent être confronté à des problèmes |
| vingtaine                 | Les utilisateurs peuvent se plaindre       |
| 0                  | Problèmes réseau un sujet courant de discussion |

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont uniquement disponibles pour les locataires Microsoft 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="network-assessment-panel"></a>Panneau d’évaluation du réseau

Chaque évaluation réseau, qu’elle soit portée au client ou à un emplacement de bureau spécifique, présente un panneau détaillant les détails de l’évaluation. Ce panneau affiche un graphique à barres de l’évaluation à la fois sous forme de pourcentage et de total pour chaque charge de travail de composant, y compris les charges de travail où les données de mesure ont été reçues. Pour une évaluation du réseau d’emplacements de bureau, nous proposons également une comparaison avec le pourcentage de clients Microsoft 365 dans chacune des cinq quintiles qui ont signalé des données dans la même ville que votre emplacement de bureau.

![Exemple de valeur d’évaluation du réseau](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

La **répartition** de l’évaluation dans le panneau indique l’évaluation de chacune des charges de travail des composants.

L' **historique** de l’évaluation indique les 30 derniers jours de l’évaluation et du benchmark. Vous pouvez également rendre compte de l’historique des mesures de n’importe quel emplacement de bureau pendant une période de deux ans au maximum à l’aide de l’onglet historique. L’onglet historique vous permet de sélectionner les attributs à signaler et de choisir une période de rapports, vous pouvez mettre en surbrillance l’impact d’un projet de mise à jour réseau et voir l’amélioration de votre évaluation du réseau.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Évaluations du réseau client et évaluation du réseau de l’emplacement Office

Une évaluation réseau mesure la conception du périmètre réseau d’un emplacement de bureau sur le réseau de Microsoft. Les améliorations apportées au périmètre réseau sont les meilleures à chaque emplacement de bureau.

Nous affichons une valeur d’évaluation réseau pour l’ensemble du client Microsoft 365 sur la page vue d’ensemble des performances réseau, qui est une moyenne pondérée des évaluations réseau pour tous les emplacements de bureau. Il existe également une valeur d’évaluation du réseau spécifique pour chaque emplacement Office détecté sur la page de résumé de cet emplacement.

## <a name="exchange-online"></a>Exchange Online

Pour Exchange Online, la latence TCP entre l’ordinateur client et le service Exchange frontal est mesurée. Cela peut être influencé par la distance que le réseau traverse sur le réseau local et le réseau étendu du client. Elle peut également être affectée par les appareils ou services intermédiaires réseau qui retardent la connectivité ou provoquent le renvoi des paquets. Elle est influencée par le degré d’éloignement de la porte de service Exchange la plus proche. La médiane (également appelée mesure 50e centile ou P50) est prise pour toutes les mesures au cours des trois jours précédents.

L’évaluation Exchange Online est effectuée à l’aide du tableau suivant. Un nombre de latence TCP entre les seuils est affecté de points de façon linéaire au sein de la bande.

| Latence TCP   | Points |
| :------------ | :----- |
| 10 ms au maximum  | 100    |
| 25ms          | 80     |
| 100 ms         | 60     |
| 200 ms         | 40     |
| 300 m         | vingtaine     |
| 350ms ou plus | 0      |

## <a name="sharepoint-online"></a>SharePoint Online

Pour SharePoint Online, la vitesse de téléchargement disponible pour un utilisateur pour accéder à un document à partir de SharePoint ou de OneDrive est mesurée. Cela peut être influencé par la bande passante disponible sur les circuits réseau entre l’ordinateur client et le réseau Microsoft. Il est également souvent influencé par la congestion du réseau qui se trouve dans des périphériques réseau complexes ou dans des zones de non-fidélité de mauvaise qualité. La vitesse de téléchargement est exprimée en mégaoctets par seconde, soit approximativement un dixième de circuits classés par seconde. L’unité de méga-octets par seconde est utile, car vous pouvez voir directement quel fichier de taille peut être téléchargé en 1 seconde. Le 25e centile (également appelé mesure P25) est pris en charge pour toutes les mesures au cours des trois jours précédents. Ce 25e centile permet de réduire l’impact d’une congestion variable au fil du temps.

L’évaluation de SharePoint Online est effectuée à l’aide du tableau suivant. Un numéro de vitesse de téléchargement entre les seuils est affecté de points de façon linéaire au sein de la bande.

| Vitesse de téléchargement | Points |
| :------------- | :----- |
| 20MBps ou plus | 100    |
| 14MBps         | 80     |
| 8MBps          | 60     |
| 4MBps          | 40     |
| 2MBps          | vingtaine     |
| 0MBps          | 0      |

## <a name="microsoft-teams"></a>Microsoft Teams

Pour Microsoft Teams, la qualité du réseau est mesurée en tant que latence UDP, gigue UDP et perte de paquets UDP. UDP est utilisé pour la connectivité audio et vidéo d’appel et de conférence pour Microsoft Teams. Cela peut être influencé par les mêmes facteurs que pour la latence et la vitesse de téléchargement en plus des lacunes de connectivité dans la prise en charge UDP d’un réseau étant donné que le protocole UDP est configuré séparément pour le protocole TCP le plus courant. La médiane (également appelée mesure 50e centile ou P50) est prise pour toutes les mesures au cours des trois jours précédents. 

Nous calculons la note moyenne d’opinion à partir de ces mesures UDP pour une mise à l’ampleur comprise entre un et cinq. Nous allons ensuite établir une correspondance avec l’échelle de 0-100 points pour l’évaluation réseau Microsoft Teams.  La qualité globale est supérieure à 87,5 points et le mauvais est inférieur à 50 points.

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le centre d’administration Microsoft 365 (version d’évaluation)](office-365-network-mac-perf-overview.md)

[Informations sur les performances du réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Test de connectivité Microsoft 365 dans le centre d’administration M365 (aperçu)](office-365-network-mac-perf-onboarding-tool.md)

[Services d’emplacement de connectivité réseau Microsoft 365 (aperçu)](office-365-network-mac-location-services.md)

[Outil de test de connectivité réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-onboarding-tool.md)
