---
title: Avis de service pour la limitation eDiscovery dans la surveillance Exchange Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Découvrez les avis de service pour la limitation eDiscovery dans Exchange Online surveillance.
ms.openlocfilehash: 61bc8b59cce6ff74c6633b85d915309c4c2d388a
ms.sourcegitcommit: 0ca3ab2abe07810e9b2cc2d806e3c6b9f35b146c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68685235"
---
# <a name="service-advisories-for-ediscovery-throttling-in-exchange-online-monitoring"></a>Avis de service pour la limitation eDiscovery dans la surveillance Exchange Online

Nous avons publié un nouvel avis de service Exchange Online qui vous informe de la limitation d’eDiscovery. Ces avis de service fournissent une visibilité sur les instances lorsque l’utilisateur n’est pas en mesure d’envoyer la recherche et l’exportation en raison de la limitation.

Ces avis de service sont affichés dans le Centre d'administration Microsoft 365. Pour afficher ces avis de service, accédez à **Intégrité**  |  **[État des services](https://go.microsoft.com/fwlink/p/?linkid=842900)** |  **Exchange Online**. Voici un exemple de conseil du service eDiscovery.

![Capture d’écran de l’intégrité du service eDiscovery](../media/ediscovery-service-health.jpg)

## <a name="what-does-this-service-advisory-indicate"></a>Qu’indique cet avis de service ?

Les avis de service pour la limitation eDiscovery informent les administrateurs que leur locataire est limité en raison du nombre de travaux de recherche et d’exportation dépassant la limite définie par Microsoft. Différentes limites sont appliquées aux outils de recherche eDiscovery dans le portail de conformité [Microsoft Purview](/compliance/index.yml) . Cela inclut les recherches exécutées sur la page [Recherche de contenu](/compliance/search-for-content) et les recherches associées à un cas eDiscovery sur la page [eDiscovery (Standard).](/compliance/get-started-core-ediscovery) Ces limites aident à maintenir l’intégrité et la qualité des services fournis aux organisations. Ces avis vous permettent de prendre ces limites en considération lors de la planification, de l’exécution et de la résolution des problèmes liés aux recherches et aux exportations eDiscovery.

Pour connaître les limites liées à l’outil Microsoft Purview eDiscovery (Standard), consultez [Limites de la recherche de contenu et de l’eDiscovery (Standard) dans le centre de conformité](/compliance/limits-for-content-search?viewFallbackFrom=o365-worldwide%20for%20service%20limits).

### <a name="how-often-will-i-see-these-service-advisories"></a>À quelle fréquence vais-je voir ces avis de service ?

Vous pouvez vous attendre à voir ce type d’avis jusqu’à l’heure où les travaux de recherche et d’exportation se trouvent dans la limite définie.

## <a name="more-information"></a>Plus d’informations

- Pour plus d’informations sur la résolution et la résolution des problèmes de conformité eDiscovery, consultez [Résolution des problèmes liés à Microsoft Purview](/troubleshoot/microsoft-365-compliance-welcome).
- Pour plus d’informations sur Microsoft Purview, consultez [Qu’est-ce que Microsoft Purview ?](/purview/purview)
- Pour en savoir plus sur les solutions Microsoft Purview eDiscovery, consultez [solutions Microsoft Purview eDiscovery](/compliance/ediscovery)
