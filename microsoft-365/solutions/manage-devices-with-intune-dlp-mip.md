---
title: Étape 7. Implémenter la protection contre la perte de données (DLP) avec des fonctionnalités de protection des informations
ms.author: bcarter
author: brendacarter
f1.keywords:
- Endpoint dlp
- data loss prevention
- dlp policies
manager: dougeby
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- endpoint dlp
- data loss prevention
- dlp policies
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
keywords: ''
description: Implémentez le point de terminaison DLP en travaillant avec votre équipe de protection et de gouvernance d’information pour créer des stratégies DLP pour votre organisation.
ms.openlocfilehash: 5a20f7e128890d75ec051667c41d3251639fadab
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67585463"
---
# <a name="step-7-implement-data-loss-prevention-dlp-with-information-protection-capabilities"></a>Étape 7. Implémenter la protection contre la perte de données (DLP) avec des fonctionnalités de protection des informations


Si votre organisation a déjà mis le temps nécessaire à la compréhension de vos données, au développement d’un schéma de confidentialité des données et à l’application du schéma, vous pouvez être prêt à étendre les éléments de ce schéma aux points de terminaison à l’aide de stratégies de protection contre la perte de données (DLP) Microsoft Purview. 

La protection contre la perte de données des points de terminaison Microsoft (Endpoint DLP) s’applique actuellement aux éléments suivants :
- Windows 10, Windows 11
- macOS

Les stratégies DLP sont créées par votre équipe de gouvernance et de protection des données. Chaque stratégie DLP définit les éléments à rechercher dans un ensemble de données, tels que les types ou étiquettes d’informations sensibles, et comment protéger ces données. 

Par exemple, une stratégie DLP peut rechercher des données personnelles comme un numéro de passeport. La stratégie DLP inclut une condition qui déclenche l’action de la stratégie, par exemple lorsqu’un numéro de passeport est partagé avec des personnes extérieures à votre organisation. L’action de la stratégie peut également être configurée. Il peut s’agir de signaler simplement l’action aux administrateurs, d’avertir les utilisateurs ou même d’empêcher le partage des données.

La stratégie DLP spécifie également l’emplacement à appliquer à la stratégie, par exemple, Exchange courrier électronique et SharePoint sites. Les appareils sont l’un des emplacements disponibles pour les administrateurs. Si des appareils sont sélectionnés, vous pouvez spécifier à quels utilisateurs et groupes d’utilisateurs appliquer la stratégie. Vous pouvez également spécifier des utilisateurs et des groupes d’utilisateurs à exclure de la stratégie.

Si votre équipe de protection et de gouvernance des informations est prête à étendre les stratégies DLP aux points de terminaison, vous devrez les coordonner pour activer des appareils pour point de terminaison DLP, tester et régler les stratégies DLP, former des utilisateurs et surveiller les résultats. 

![Étapes DLP du point de terminaison pour l’administrateur de l’appareil](../media/devices/endpoint-dlp-steps.png#lightbox)


Utilisez les étapes suivantes pour travailler avec votre équipe de protection des informations.


|Étape  |Description  |
|---------|---------|
|1     |  [En savoir plus sur les points de terminaison de protection contre la perte de données](../compliance/endpoint-dlp-learn-about.md).        |
|2     | Activez des appareils pour point de terminaison DLP. Si vous avez intégré des appareils à Microsoft Defender pour point de terminaison, vos appareils sont déjà activés pour point de terminaison DLP. Si vos appareils ne sont pas intégrés à Defender pour point de terminaison, consultez [Démarrage de la protection contre la perte de données de point de terminaison](../compliance/endpoint-dlp-getting-started.md) pour obtenir des instructions.|
|3     |   Travaillez avec votre équipe de protection et de gouvernance des informations pour définir, tester et régler des stratégies. Cela inclut la surveillance des résultats. Consultez les ressources suivantes :<br>- [Utilisation de la protection contre la perte de données de point de terminaison](../compliance/endpoint-dlp-using.md)<br>- [View the reports for data loss prevention](../compliance/view-the-dlp-reports.md)      |
