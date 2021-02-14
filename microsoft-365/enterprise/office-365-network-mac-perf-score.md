---
title: Évaluation du réseau Microsoft 365 (prévisualisation)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Évaluation du réseau Microsoft 365 (prévisualisation)
ms.openlocfilehash: 3d80130dbf9ca41342bc1a01fe3ce992303efb48
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48200746"
---
# <a name="microsoft-365-network-assessment-preview"></a>Évaluation du réseau Microsoft 365 (prévisualisation)

Dans la connectivité réseau du Centre d’administration  Microsoft 365, les évaluations réseau regroupent de nombreuses mesures de performances réseau dans une capture instantanée de l’état du périmètre de votre réseau d’entreprise, représentée par une valeur de points de 0 à 100. Une évaluation réseau vous indique l’impact de la conception de réseau responsable du client sur l’expérience utilisateur d’Office 365. Les évaluations réseau sont limitées à l’ensemble du client et à chaque emplacement géographique à partir duquel les utilisateurs se connectent à votre client, offrant aux administrateurs Microsoft 365 un moyen simple de saisir instantanément un gestalt de l’état du réseau de l’entreprise et d’obtenir rapidement un rapport détaillé pour n’importe quel emplacement de bureau global.

La valeur des points d’évaluation réseau est une moyenne de la latence TCP, de la vitesse de téléchargement et des mesures de qualité de connexion UDP compilées une fois par jour. Les mesures de performances pour les réseaux microsoft sont exclues de ces mesures pour s’assurer que les résultats de l’évaluation sont non ambigus et spécifiques au réseau d’entreprise.

![Valeur d’évaluation du réseau](../media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

Une très faible valeur d’évaluation du réseau suggère que les clients Microsoft 365 auront des problèmes importants pour se connecter au client ou maintenir une expérience utilisateur réactive, tandis qu’une valeur élevée indique un réseau correctement configuré avec peu de problèmes de performances en cours. Une valeur de 80 % représente une ligne de base saine où vous ne devriez pas vous attendre à recevoir des réclamations régulières des utilisateurs concernant la connectivité ou la réactivité de Microsoft 365 en raison des performances du réseau. Au fil des améliorations apportées à la connectivité réseau itérative, cette valeur augmente avec l’expérience utilisateur.

| Évaluation du réseau | Expérience utilisateur attendue |
| :----------------- | :----------------------- |
| 100                | Idéale                     |
| 80                 | Répond aux recommandations    |
| 60                 | Acceptable               |
| 40                 | Les utilisateurs peuvent être en situation de problèmes |
| 20                 | Les utilisateurs peuvent se plaindr       |
| 0                  | Problèmes réseau : sujet de discussion courant |

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le Centre d’administration Microsoft 365 sont actuellement en état de prévisualisation et sont uniquement disponibles pour les clients Microsoft 365 qui ont été inscrits au programme d’aperçu des fonctionnalités.

## <a name="network-assessment-panel"></a>Panneau d’évaluation du réseau

Chaque évaluation réseau, qu’elle soit limitée au client ou à un emplacement de bureau spécifique, affiche un panneau avec des détails sur l’évaluation. Ce panneau présente un graphique à barres de l’évaluation sous la mesure d’un pourcentage et en tant que points totaux pour chaque charge de travail de composant, y compris uniquement les charges de travail où les données de mesure ont été reçues. Pour une évaluation du réseau d’emplacements de bureau, nous montrons également une comparaison avec le pourcentage de clients Microsoft 365 dans chacun des cinq emplacements qui ont signalé des données dans la même ville que votre bureau.

![Exemple de valeur d’évaluation du réseau](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

La **répartition de l’évaluation** dans le panneau affiche l’évaluation pour chacune des charges de travail de composant.

**L’historique des** évaluations indique les 30 derniers jours de l’évaluation et le critère. Vous pouvez également signaler l’historique des mesures pour n’importe quel emplacement de bureau pendant deux ans à l’aide de l’onglet Historique. L’onglet Historique vous permet de sélectionner vos attributs sur les rapports et en choisissant une période de rapport, vous pouvez mettre en évidence l’impact d’un projet de mise à jour réseau et voir l’amélioration de votre évaluation du réseau.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Évaluations réseau des locataires et évaluations du réseau de l’emplacement du bureau

Une évaluation du réseau mesure la conception du périmètre réseau d’un emplacement de bureau sur le réseau de Microsoft. Il est préférable d’améliorer le périmètre réseau à chaque emplacement de bureau.

Nous montrons une valeur d’évaluation réseau pour l’ensemble du client Microsoft 365 sur la page de vue d’ensemble des performances réseau, qui est une moyenne pondérée des évaluations réseau pour tous les emplacements de bureau. Il existe également une valeur d’évaluation réseau spécifique pour chaque emplacement de bureau détecté sur la page récapitulatif de cet emplacement.

## <a name="exchange-online"></a>Exchange Online

Pour Exchange Online, la latence TCP entre l’ordinateur client et la porte d’entrée du service Exchange est mesurée. Cela peut être impacté par la distance parcourue par le réseau local (WAN) des clients. Elle peut également être impactée par des services ou des périphériques intermédiaires réseau qui retardent la connectivité ou entraînent la réentrence des paquets. Elle est également impactée par la distance de la porte d’entrée du service Exchange la plus proche. La médiane (également appelée 50e centile ou mesure P50) est prise pour toutes les mesures des trois jours précédents.

L’évaluation d’Exchange Online est réalisée à l’aide du tableau suivant. Un nombre de latence TCP entre les seuils est affecté de manière linéaire au sein de la bande.

| Latence TCP   | Points |
| :------------ | :----- |
| 10 ms ou moins  | 100    |
| 25 ms          | 80     |
| 100 ms         | 60     |
| 200 ms         | 40     |
| 300 ms         | 20     |
| 350 ms ou plus | 0      |

## <a name="sharepoint-online"></a>SharePoint Online

Pour SharePoint Online, la vitesse de téléchargement disponible pour un utilisateur pour accéder à un document à partir de SharePoint ou OneDrive est mesurée. Cela peut être impacté par la bande passante disponible sur les circuits réseau entre l’ordinateur client et le réseau de Microsoft. Il est également souvent touché par la congestion du réseau qui existe dans les goulots d’étranglement sur les périphériques réseau complexes ou dans une couverture médiocre Wi-Fi zones. La vitesse de téléchargement est mesurée en mégaoctets par seconde, ce qui représente environ un dixième d’un circuit évalué en mégabits par seconde. Le mégaoctet par seconde est utile, car vous pouvez voir directement quel fichier de taille peut être téléchargé en 1 seconde. Le 25e centile (également appelé mesure P25) est pris pour toutes les mesures des trois jours précédents. Ce 25e centile permet de réduire l’impact d’une congestion variable au fil du temps.

L’évaluation de SharePoint Online est réalisée à l’aide du tableau suivant. Tout numéro de vitesse de téléchargement entre les seuils est affecté de manière linéaire au sein de la bande.

| Vitesse de téléchargement | Points |
| :------------- | :----- |
| 20 MBits/s ou plus | 100    |
| 14MBps         | 80     |
| 8MBps          | 60     |
| 4MBps          | 40     |
| 2MBps          | 20     |
| 0MBps          | 0      |

## <a name="microsoft-teams"></a>Microsoft Teams

Pour Microsoft Teams, la qualité du réseau est mesurée en tant que latence UDP, gigue UDP et perte de paquets UDP. UDP est utilisé pour la connectivité multimédia audio et vidéo des appels et des conférences pour Microsoft Teams. Cela peut être impacté par les mêmes facteurs que pour la latence et la vitesse de téléchargement, en plus des lacunes de connectivité dans la prise en charge UDP d’un réseau, car UDP est configuré séparément sur le protocole TCP le plus courant. La médiane (également appelée 50e centile ou mesure P50) est prise pour toutes les mesures des trois jours précédents. 

Nous calculons un score d’opinion moyenne à partir de ces mesures UDP pour une échelle de 1 à 5. Ensuite, nous mions cela à l’échelle de 0 à 100 points pour l’évaluation du réseau Microsoft Teams.  La valeur globale est de plus de 87,5 points et la valeur globale est inférieure à 50 points.

## <a name="related-topics"></a>Rubriques connexes

[Connectivité réseau dans le Centre d’administration Microsoft 365 (prévisualisation)](office-365-network-mac-perf-overview.md)

[Informations sur les performances du réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Outil de test de connectivité réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-onboarding-tool.md)

[Services d’emplacement de connectivité réseau Microsoft 365 (prévisualisation)](office-365-network-mac-location-services.md)
