---
title: Microsoft 365'évaluation du réseau
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
description: Microsoft 365'évaluation du réseau
ms.openlocfilehash: c09e34b1bc3a8bf0f82a4a1e3c72e67f320abd43
ms.sourcegitcommit: fb6c5e04ade1e82b26b2f911577b5ac721f1c544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "52470473"
---
# <a name="microsoft-365-network-assessment"></a>Microsoft 365'évaluation du réseau

Dans la Microsoft 365 réseau du Centre d’administration,  les évaluations réseau regroupent de nombreuses mesures de performances réseau dans un instantané de l’état du périmètre de votre réseau d’entreprise. Une évaluation réseau vous indique l’impact de la conception de réseau responsable du client sur Office 365 l’expérience utilisateur. Les évaluations réseau sont limitées à l’ensemble du client et à chaque emplacement géographique à partir duquel les utilisateurs se connectent à votre client. Les évaluations permettent aux administrateurs Microsoft 365 d’avoir instantanément une idée de l’état du réseau de l’entreprise et d’obtenir rapidement un rapport détaillé pour n’importe quel emplacement de bureau global.

La valeur des points d’évaluation réseau est de 0 à 100 et est une moyenne de la latence TCP, de la vitesse de téléchargement et des mesures de qualité de connexion UDP. Ces mesures sont compilées une fois par jour. Les mesures de performances pour les réseaux microsoft sont exclues de ces mesures pour s’assurer que les résultats de l’évaluation sont non ambigus et spécifiques au réseau d’entreprise.

> [!div class="mx-imgBorder"]
> ![Valeur d’évaluation du réseau](../media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

Une très faible valeur d’évaluation réseau suggère que Microsoft 365 clients auront des problèmes importants lors de la connexion au client ou de la maintenance d’une expérience utilisateur réactive. Une valeur élevée indique un réseau correctement configuré avec peu de problèmes de performances en cours. Une valeur de 80 % représente une ligne de base saine, au-dessus de laquelle vous ne devriez pas vous attendre à recevoir régulièrement des réclamations des utilisateurs concernant la connectivité Microsoft 365 ou la réactivité en raison des performances du réseau. Au fil des améliorations apportées à la connectivité réseau itérative, cette valeur augmente avec l’expérience utilisateur.

| Évaluation du réseau | Expérience utilisateur attendue |
| :----------------- | :----------------------- |
| 100                | Idéale                     |
| 80                 | Répond aux recommandations    |
| 60                 | Acceptable               |
| 40                 | Les utilisateurs peuvent être en situation de problèmes |
| 20                 | Les utilisateurs peuvent se plaindra peut-être       |
| 0                  | Problèmes réseau : sujet de discussion courant |

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le Centre d’administration Microsoft 365 sont actuellement en état de prévisualisation et sont uniquement disponibles pour les locataires Microsoft 365 qui ont été inscrits au programme d’aperçu des fonctionnalités.

## <a name="network-assessment-panel"></a>Panneau d’évaluation du réseau

Chaque évaluation réseau, qu’elle soit limitée au client ou à un emplacement de bureau spécifique, affiche un panneau avec des détails sur l’évaluation. Ce panneau présente un graphique à barres de l’évaluation sous la mesure d’un pourcentage et en tant que points totaux pour chaque charge de travail de composant, y compris uniquement les charges de travail où les données de mesure ont été reçues. Pour une évaluation du réseau d’emplacements de bureau, nous montrons également une comparaison avec le pourcentage de clients Microsoft 365 dans chacun des cinq bureaux qui ont signalé des données dans la même ville que votre bureau.

> [!div class="mx-imgBorder"]
> ![Exemple de valeur d’évaluation du réseau](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

La **répartition de l’évaluation** dans le panneau affiche l’évaluation pour chacune des charges de travail de composant.

**L’historique des** évaluations indique les 30 derniers jours de l’évaluation et le critère. Vous pouvez également faire un rapport sur l’historique des mesures pour n’importe quel emplacement de bureau pendant deux ans à l’aide de l’onglet Historique. L’onglet Historique vous permet de sélectionner vos attributs à signaler. En choisissant une période de rapport, vous pouvez mettre en évidence l’impact d’un projet de mise à jour réseau et voir l’amélioration de votre évaluation du réseau.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Évaluations réseau des locataires et évaluations du réseau de l’emplacement du bureau

Une évaluation du réseau mesure la conception du périmètre réseau d’un emplacement de bureau sur le réseau de Microsoft. Il est préférable d’améliorer le périmètre réseau à chaque emplacement de bureau.

Nous montrons une valeur d’évaluation réseau pour l’ensemble Microsoft 365 client dans la page vue d’ensemble des performances réseau. Cette valeur est une moyenne pondérée des évaluations réseau pour tous les bureaux. Il existe également une valeur d’évaluation réseau spécifique pour chaque emplacement de bureau détecté sur la page récapitulatif de cet emplacement.

## <a name="exchange-online"></a>Exchange Online

Par Exchange Online, la latence TCP entre l’ordinateur client et la porte d’Exchange service est mesurée. Cette latence peut être impactée par la distance parcourue par le réseau sur les réseaux lan et wan des clients. Elle peut également être impactée par les services ou les périphériques intermédiaires réseau, qui retardent la connectivité ou entraînent la réentrence des paquets. Elle est également impactée par la distance de la porte d’Exchange service la plus proche. La médiane (également appelée 50e centile ou mesure P50) est prise pour toutes les mesures des trois jours précédents.

L Exchange Online’évaluation est réalisée à l’aide du tableau suivant. Un nombre de latence TCP entre les seuils est affecté de manière linéaire au sein de la bande.

| Latence TCP   | Points |
| :------------ | :----- |
| 10 ms ou moins  | 100    |
| 25 ms          | 80     |
| 100 ms         | 60     |
| 200 ms         | 40     |
| 300 ms         | 20     |
| 350 ms ou plus | 0      |

## <a name="sharepoint-online"></a>SharePoint Online

Par SharePoint en ligne, la vitesse de téléchargement disponible pour un utilisateur pour accéder à un document à partir SharePoint ou OneDrive est mesurée. Cela peut être impacté par la bande passante disponible sur les circuits réseau entre l’ordinateur client et le réseau de Microsoft. Il est également souvent touché par la congestion du réseau qui existe dans les goulots d’étranglement sur les périphériques réseau complexes ou dans une couverture médiocre Wi-Fi zones. La vitesse de téléchargement est mesurée en mégaoctets par seconde, ce qui représente environ un dixième d’un circuit évalué en mégabits par seconde. Le mégaoctet par seconde est utile, car vous pouvez voir directement quel fichier de taille peut être téléchargé en 1 seconde. Le 25e centile (également appelé mesure P25) est pris pour toutes les mesures des trois jours précédents. Ce 25e centile permet de réduire l’impact d’une congestion variable au fil du temps.

L SharePoint en ligne est réalisée à l’aide du tableau suivant. Tout numéro de vitesse de téléchargement entre les seuils est affecté de manière linéaire au sein de la bande.

| Vitesse de téléchargement | Points |
| :------------- | :----- |
| 20 MBits/s ou plus | 100    |
| 14MBps         | 80     |
| 8MBps          | 60     |
| 4MBps          | 40     |
| 2MBps          | 20     |
| 0MBps          | 0      |

## <a name="microsoft-teams"></a>Microsoft Teams

Par Microsoft Teams la qualité du réseau est mesurée en tant que latence UDP, gigue UDP et perte de paquets UDP. UDP est utilisé pour la connectivité multimédia audio et vidéo d’appel et de conférence pour Microsoft Teams. Cela peut être impacté par les mêmes facteurs que pour la latence et la vitesse de téléchargement en plus des lacunes de connectivité dans la prise en charge UDP d’un réseau dans la mesure où UDP est configuré séparément sur le protocole TCP le plus courant. La médiane (également appelée 50e centile ou mesure P50) est prise pour toutes les mesures des trois jours précédents. 

Nous calculons un score d’opinion moyenne à partir de ces mesures UDP pour une échelle de 1 à 5. Ensuite, nous mions cela à l’échelle de 0 à 100 points pour l’évaluation Microsoft Teams réseau.  La valeur globale est de plus de 87,5 points et la valeur globale est inférieure à 50 points.

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le Centre d’administration Microsoft 365 (prévisualisation)](office-365-network-mac-perf-overview.md)

[Microsoft 365 informations sur les performances du réseau (aperçu)](office-365-network-mac-perf-insights.md)

[Microsoft 365 de test de connectivité réseau (prévisualisation)](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 Services de localisation de connectivité réseau (prévisualisation)](office-365-network-mac-location-services.md)
