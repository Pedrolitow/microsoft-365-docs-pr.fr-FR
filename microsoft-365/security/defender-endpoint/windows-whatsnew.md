---
title: Nouveautés de Microsoft Defender pour point de terminaison sur Windows
description: Découvrez les dernières versions de fonctionnalités de Microsoft Defender pour point de terminaison sur le client et le serveur Windows.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, windows, client Windows, serveur Windows, nouveautés
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: v-mathavale
author: v-mathavale
ms.localizationpriority: medium
ms.date: 09/20/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: reference
ms.subservice: mde
ms.openlocfilehash: 90e5ab9fec1c6c8663f493ee9c9135ffbe33daa2
ms.sourcegitcommit: 0380a7cd5adb710b80a0ed6fcd349199f1571080
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2022
ms.locfileid: "68334843"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-windows"></a>Nouveautés de Microsoft Defender pour point de terminaison sur Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Toutes les mises à jour contiennent :
- Améliorations en termes de performances
- Améliorations de la facilité de service
- Améliorations de l’intégration (Cloud, [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804))

<details>
  <summary>Août 2022 (version de publication : 10.8210.*)</summary>

|Système d’exploitation  |Ko  |Version de publication  |
|---------|---------|---------|
|Windows Server 2012 R2, 2016 |[5005292 de base de connaissances](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)|10.8210.22621.1011|
|Windows 11 21H2 (Cobalt)<br> (Windows 11 SV 21H2)     | [5016691 de base de connaissances](https://support.microsoft.com/en-us/topic/august-25-2022-kb5016691-os-build-22000-918-preview-59097044-915a-49a0-8870-49823236adbd)        | 10.8210.22000.918        |
|Serveur 2022 (fer)     | [5016693 de base de connaissances](https://support.microsoft.com/en-us/topic/august-16-2022-kb5016693-os-build-20348-946-preview-ee90d0bc-c162-4124-b7c6-f963ee7b17ed)        |10.8210.20348.946         |
|Windows 10 20H2/21H1/21H2<br> Windows Server 20H2 (Vibranium)     | [5016688 de base de connaissances](https://support.microsoft.com/en-us/topic/august-26-2022-kb5016688-os-builds-19042-1949-19043-1949-and-19044-1949-preview-ec31ebdc-067d-44dd-beb0-eabcc984d843)       | 10.8210.19041.1949        |
|Windows Server 2019 (RS5)   |[5016690 de base de connaissances](https://support.microsoft.com/en-us/topic/august-23-2022-kb5016690-os-build-17763-3346-preview-b81d1ac5-75c7-42c1-b638-f13aa4242f42)       |10.8210.17763.3346         |

**Nouveautés**

- Ajout d’un correctif pour résoudre un problème de certificat intermédiaire manquant avec l’utilisation de « TelemetryProxyServer » sur Windows Server 2012 R2 exécutant l’agent unifié.
- DLP de point de terminaison amélioré avec la possibilité de protéger les fichiers protégés et chiffrés par mot de passe et non les fichiers d’étiquette.
- DLP de point de terminaison amélioré avec prise en charge des données de contexte dans la télémétrie d’audit (preuve courte).
- Amélioration Microsoft Defender pour point de terminaison prise en charge de l’authentification client pour les appareils VDI.
- Amélioration de la capacité de Microsoft Defender pour point de terminaison à identifier et à intercepter les ransomware et les attaques avancées.
- La fonctionnalité Contain prend désormais en charge d’autres versions de bureau et de serveur pour effectuer l’action Contain et bloquer les appareils détectés lorsqu’ils sont contenus.
- Extension de la fonctionnalité de mode de dépannage à d’autres versions de bureau et de serveur. Pour obtenir la liste complète des versions de système d’exploitation prises en charge et plus d’informations sur les prérequis, consultez [Prise en main du mode de résolution des problèmes dans Microsoft Defender pour point de terminaison](enable-troubleshooting-mode.md).
- Les améliorations apportées à la réponse dynamique incluent une latence de création de session réduite lors de l’utilisation de proxys, une commande manuelle de correction d’annulation, la prise en charge du partage OneDrive dans l’action FindFile, ainsi qu’une isolation et une stabilité améliorées.
- [La gestion de la sécurité pour Microsoft Defender pour point de terminaison](security-config-management.md#configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management) offre désormais la possibilité de synchroniser la configuration de l’appareil à la demande au lieu d’attendre une cadence spécifique.

 > [!NOTE] 
 > Le package de mise à jour KB5005292 est en cours de déploiement progressif via Windows Update. Vers la fin de cette planification, le package sera publié complètement, y compris dans le catalogue de mises à jour pour téléchargement manuel. Pour la version actuelle, il s’agit de la deuxième moitié du mois d’octobre. Si vous souhaitez tester le package plus tôt, vous pouvez utiliser [des contrôles de déploiement progressif pour les mises à jour de plateforme afin](configure-updates.md) de sélectionner le canal d’aperçu.
  
<br/>
</details>

Voir aussi : 
- [Nouveautés dans Microsoft Defender pour point de terminaison](whats-new-in-microsoft-defender-endpoint.md)
- [Nouveautés de Defender pour point de terminaison sur macOS](mac-whatsnew.md)
- [Nouveautés de Defender pour point de terminaison sur iOS](ios-whatsnew.md)
- [Nouveautés de Defender pour point de terminaison sur Linux](linux-whatsnew.md)
