---
title: Services d’emplacement de connectivité réseau Microsoft 365 (prévisualisation)
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
description: Services d’emplacement de connectivité réseau Microsoft 365 (prévisualisation)
ms.openlocfilehash: f2ab872f67eca70ab2791d3ad6fe1396b009cc18
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48200780"
---
# <a name="microsoft-365-network-connectivity-location-services-preview"></a>Services d’emplacement de connectivité réseau Microsoft 365 (prévisualisation)

Le Centre d’administration Microsoft 365 affiche désormais Les informations réseau et les recommandations de performances, qui sont des mesures de performances en direct collectées à partir de votre client Microsoft 365 et disponibles uniquement pour les utilisateurs **administratifs** de votre client. La connectivité réseau organisationnelle est conçue par emplacement de bureau via un emplacement de sortie réseau vers Internet. La connectivité client Microsoft 365 utilise cet itinéraire, puis via Internet vers les serveurs de porte du service Microsoft. L’identification des emplacements de bureau est essentielle pour pouvoir afficher ces informations réseau.

## <a name="location-in-network-measurements"></a>Emplacement dans les mesures réseau

L’administrateur d’une organisation peut choisir d’inclure l’emplacement dans les mesures réseau utilisées par cette fonctionnalité. Cela permet la découverte automatique de la ville où se trouve chaque bureau. Les informations d’emplacement ne sont pas précises et sont obscurcies à 300 m et classées par ville. Au moment où l’emplacement est capturé sur  un appareil Windows, il affiche une icône Emplacement en cours d’utilisation dans la boîte à outils et les administrateurs peuvent vouloir en informer les utilisateurs. Avec ce traitement, l’emplacement est traité comme l’emplacement du bureau de l’organisation et non comme l’emplacement d’une personne ou d’un appareil. Des informations réseau peuvent être affichées dans ces villes d’emplacements de bureau découvertes. Si vous souhaitez obtenir une meilleure précision des recommandations, un administrateur peut entrer des adresses d’emplacement de bureau spécifiques et les informations réseau sont regroupées à celles-ci à la place. Les emplacements de bureau ne peuvent pas être agrégés plus près que 300 mètres.

## <a name="location-in-the-microsoft-365-admin-center"></a>Emplacement dans le Centre d’administration Microsoft 365

Dans le Centre d’administration Microsoft 365, les contrôles de carte Bing sont utilisés pour afficher l’emplacement des bureaux de l’organisation et pour afficher la topologie de périmètre réseau pour un emplacement de bureau sélectionné. Lorsqu’un administrateur ajoute des détails d’adresse spécifiques pour les emplacements de bureau, Bing Maps est également utilisé pour suggérer des adresses pour faciliter la saisie de données.

## <a name="terms-of-use"></a>Conditions d’utilisation

Tout contenu fourni via Bing Maps, y compris les géocodes, peut uniquement être utilisé dans le produit par le biais duquel le contenu est fourni. L’utilisation par le client de la fonctionnalité Services de localisation du Centre d’administration Microsoft 365, optimisée par Bing Cartes, est régie par les conditions d’utilisation de l’utilisateur final _bing Maps_ disponibles dans et la déclaration de confidentialité <https://go.microsoft.com/?linkid=9710837> _Microsoft_ disponible sur <https://go.microsoft.com/fwlink/?LinkID=248686.>

Cette fonctionnalité, fournie via Bing Maps, est également prise en charge par **Here Technologies**. La façon dont Bing Maps exploite les services de localisation fournis par Here Technologies est régie par les conditions du _service Here Technologies_ disponibles à <https://legal.here.com/en-gb/terms> l’adresse .

## <a name="related-topics"></a>Rubriques connexes

[Connectivité réseau dans le Centre d’administration Microsoft 365 (prévisualisation)](office-365-network-mac-perf-overview.md)

[Informations sur les performances du réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Évaluation du réseau Microsoft 365 (prévisualisation)](office-365-network-mac-perf-score.md)

[Test de connectivité Microsoft 365 dans le Centre d’administration M365 (prévisualisation)](office-365-network-mac-perf-onboarding-tool.md)
