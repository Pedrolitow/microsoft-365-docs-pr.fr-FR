---
title: Services d’emplacement de connectivité réseau Microsoft 365
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
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
description: Services d’emplacement de connectivité réseau Microsoft 365
ms.openlocfilehash: 68569be7de9924ada4c2323d00630cdf084525e4
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67670794"
---
# <a name="microsoft-365-network-connectivity-location-services"></a>Services d’emplacement de connectivité réseau Microsoft 365

Le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> affiche désormais **les recommandations en matière d’insights réseau et de performances**, qui sont des métriques de performances dynamiques collectées à partir de votre locataire Microsoft 365. Ces métriques peuvent être consultées uniquement par les utilisateurs administratifs de votre locataire. La connectivité réseau organisationnelle est conçue par emplacement de bureau via un emplacement de sortie réseau vers Internet. La connectivité client Microsoft 365 utilise cette route, puis via Internet vers les serveurs de porte d’entrée du service Microsoft. L’identification des emplacements de bureau est essentielle pour pouvoir afficher ces insights réseau.

## <a name="location-in-network-measurements"></a>Emplacement dans les mesures réseau

L’administrateur d’une organisation peut choisir l’emplacement à inclure dans les mesures réseau utilisées par cette fonctionnalité. Cela permet la découverte automatique de la ville où se trouve chaque bureau. Les informations de localisation ne sont pas précises et sont masquées à 300m et classées par ville. Au moment où l’emplacement est capturé sur un appareil Windows, l’appareil affiche une icône **Emplacement en usage** dans la barre d’outils. Les administrateurs peuvent souhaiter informer les utilisateurs de l’apparence de cette icône. Avec ce traitement, l’emplacement est traité comme l’emplacement du bureau de l’organisation et non comme l’emplacement d’une personne ou d’un appareil. Les informations réseau peuvent être affichées dans ces villes d’emplacement de bureau découvertes. Si vous souhaitez obtenir une plus grande précision dans les recommandations, vous pouvez entrer des adresses d’emplacement de bureau spécifiques. Les insights réseau seront agrégés à ces emplacements à la place. Les emplacements d’office ne peuvent pas être agrégés plus étroitement que 300 mètres.

## <a name="location-in-the-microsoft-365-admin-center"></a>Emplacement dans le centre de Administration Microsoft 365

Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, les contrôles de carte Bing sont utilisés pour indiquer où se trouvent les emplacements des bureaux de l’organisation. Les contrôles affichent également la topologie de périmètre réseau pour un emplacement de bureau sélectionné. Lorsqu’un administrateur ajoute des détails d’adresse spécifiques pour les emplacements de bureau, Bing Cartes est également utilisé pour suggérer des adresses afin de faciliter la saisie des données.

## <a name="terms-of-use"></a>Conditions d’utilisation

Tout contenu fourni via Bing Cartes, y compris les géocodes, ne peut être utilisé que dans le produit par le biais duquel le contenu est fourni. L’utilisation par le client de la fonctionnalité <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> Location Services, optimisée par Bing Cartes, est régie par les _Bing Cartes End-User conditions d’utilisation_ disponibles dans <https://go.microsoft.com/?linkid=9710837> et la [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkID=248686).

Cette fonctionnalité, fournie via Bing Cartes, est également prise en charge par **TomTom**. Pour plus d’informations sur les produits et services de TomTom, consultez [https://www.tomtom.com/legal](https://www.tomtom.com/legal).

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le centre de Administration Microsoft 365](office-365-network-mac-perf-overview.md)

[Insights sur les performances réseau de Microsoft 365](office-365-network-mac-perf-insights.md)

[Évaluation du réseau Microsoft 365](office-365-network-mac-perf-score.md)

[Test de connectivité Microsoft 365 dans le Centre d'administration Microsoft 365](office-365-network-mac-perf-onboarding-tool.md)
