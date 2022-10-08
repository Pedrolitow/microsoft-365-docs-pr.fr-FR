---
title: Fonctionnalités de Microsoft Defender pour point de terminaison prises en charge par plateforme
description: Découvrez les fonctionnalités Microsoft Defender pour point de terminaison prises en charge pour Windows 10 appareils, serveurs et appareils non Windows.
keywords: intégration, Microsoft Defender pour point de terminaison intégration, sccm, stratégie de groupe, mdm, script local, test de détection
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
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: dcff54381dbdaf1362f9d4dd7cdc364e29c53426
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68227743"
---
# <a name="supported-microsoft-defender-for-endpoint-capabilities-by-platform"></a>Fonctionnalités de Microsoft Defender pour point de terminaison prises en charge par plateforme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Découvrez comment [intégrer des appareils et configurer Microsoft Defender pour point de terminaison fonctionnalités](onboard-configure.md).

Le tableau suivant fournit des informations sur les fonctionnalités de Microsoft Defender pour point de terminaison prises en charge par plateforme.

|Système d’exploitation  |Windows 10 & 11  |Windows Server 2012 R2 <sup>[[1](#fn1)]</sup>, <br> 2016 <sup>[[1](#fn1)]</sup>, <br> 2019 & 2022, <br> 1803+ |macOS |Linux| 
|---------|---------|---------|---------|---------|
|**Prévention**    |         |         |         |         | 
|Règles de réduction de la surface d’attaque     | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)     |  ![Non](images/svg/check-no.svg)       |  ![Non](images/svg/check-no.svg)        |
|Accès contrôlé aux dossiers     | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)    |  ![Non](images/svg/check-no.svg)       |  ![Non](images/svg/check-no.svg)        |
|Contrôle des appareils     | ![Oui.](images/svg/check-yes.svg)        | ![Non](images/svg/check-no.svg)   |  ![Oui.](images/svg/check-yes.svg)       |  ![Non](images/svg/check-no.svg)        |  
|Pare-feu      | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)    |  ![Non](images/svg/check-no.svg)       |  ![Non](images/svg/check-no.svg)        |
|Protection réseau      | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)   |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)]</sup>       |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)]</sup>        |
|Protection de nouvelle génération       | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)  |  ![Oui.](images/svg/check-yes.svg)       |  ![Oui.](images/svg/check-yes.svg)         |
|Protection contre les falsifications        | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)  |  ![Oui.](images/svg/check-yes.svg)       |  ![Non](images/svg/check-no.svg)         |
|Web Protection       | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)     |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)]</sup>       |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)]</sup>        |
||||||
|**Détection**     |         |         |         |       |
|Repérage avancé        | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg) |  ![Oui.](images/svg/check-yes.svg)       |  ![Oui.](images/svg/check-yes.svg)         |
|Indicateurs de fichier personnalisés         | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)  |  ![Oui.](images/svg/check-yes.svg)       |  ![Oui.](images/svg/check-yes.svg)         |
|Indicateurs réseau personnalisés        | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)  |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)]</sup>       |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)]</sup>        |
|Bloc EDR       | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)  |  ![Non](images/svg/check-no.svg)       |  ![Non](images/svg/check-no.svg)        |
|Mode passif          | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)  |  ![Oui.](images/svg/check-yes.svg)       |  ![Oui.](images/svg/check-yes.svg)         |
|Capteur de détection des sens          | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)   |  ![Oui.](images/svg/check-yes.svg)       |  ![Oui.](images/svg/check-yes.svg)         |
|Point de terminaison & découverte d’appareil réseau      | ![Oui.](images/svg/check-yes.svg)        | ![Non](images/svg/check-no.svg)  |  ![Non](images/svg/check-no.svg)       |  ![Non](images/svg/check-no.svg)        |
|Gestion des vulnérabilités          | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg) |  ![Oui.](images/svg/check-yes.svg)       |  ![Oui.](images/svg/check-yes.svg)         |
||||||
|**Réponse**     |         |         |         ||
|Réponse & d’investigation automatisée (AIR)        | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)  |  ![Non](images/svg/check-no.svg)       |  ![Non](images/svg/check-no.svg)        |
|Fonctionnalités de réponse de l’appareil : collecter le package d’investigation, exécuter l’analyse AV        | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)   |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)] [[3](#fn3)]</sup>       |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)] [[3](#fn3)]</sup>        |
|Isolation de l’appareil        | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)   |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)] [[3](#fn3)]</sup>       |  ![Non](images/svg/check-no.svg)    |
|Fonctionnalités de réponse aux fichiers : collecter des fichiers, analyser en profondeur, bloquer des fichiers, arrêter et mettre en quarantaine des processus        | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg)   |  ![Non](images/svg/check-no.svg) <sup>[[4](#fn4)]</sup>      |  ![Non](images/svg/check-no.svg) <sup>[[4](#fn4)]</sup>    |
|Réponse en direct       | ![Oui.](images/svg/check-yes.svg)        | ![Oui.](images/svg/check-yes.svg) |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)]</sup>       |  ![Oui.](images/svg/check-yes.svg) <sup>[[2](#fn2)]</sup>        |


(<a id="fn1">1</a>) Fait référence à la solution moderne et unifiée pour Windows Server 2012 R2 et 2016. Pour plus d’informations, consultez [Intégrer des serveurs Windows au service Defender pour point de terminaison](configure-server-endpoints.md).

(<a id="fn2">2</a>) La fonctionnalité est actuellement en préversion ([Microsoft Defender pour point de terminaison fonctionnalités en préversion](preview.md)) 

(<a id="fn3">3</a>) Fonctionnalités de réponse en direct [2] 

(<a id="fn4">4</a>) Collecter le fichier uniquement à l’aide de live response [2]  
>[!NOTE]
>Windows 7, 8.1, Windows Server 2008 R2 incluent la prise en charge du capteur EDR et av à l’aide de System Center Endpoint Protection (SCEP).

