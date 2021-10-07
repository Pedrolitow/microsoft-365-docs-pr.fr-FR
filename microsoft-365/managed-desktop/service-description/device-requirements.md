---
title: Configuration requise de l’appareil
description: Résumé de la configuration matérielle et logicielle minimale requise pour que les appareils fonctionnent Microsoft Manged Desktop
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 1ce5f0c3782b8e8082d0e1ede53339a190b7259f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60209464"
---
# <a name="device-requirements"></a>Configuration requise de l’appareil

Microsoft Manged Desktop évalue régulièrement les besoins de l’appareil à inclure dans le service. Cet article décrit la configuration matérielle et logicielle requise pour qu’un appareil fonctionne avec Microsoft Manged Desktop. Vous pouvez consulter la liste des appareils spécifiques déjà approuvés pour une utilisation avec le service en fonction de ces exigences. Filtre des Microsoft Manged Desktop sur le site [Windows Pro d’entreprise](https://www.microsoft.com/en-us/windows/business/devices)

> [!NOTE]
> Ces exigences peuvent changer à tout moment, mais nous vous fournirons un préavis de 30 jours pour toute modification de la configuration matérielle requise. Les exigences les plus récemment modifiées sont marquées par <b>\*</b> . 

## <a name="check-hardware-requirements"></a>Vérifier la configuration matérielle requise

Outre l’examen des spécifications de l’appareil, vous pouvez également utiliser le contrôle d’évaluation de la disponibilité [téléchargeable](../get-ready/readiness-assessment-downloadable.md) pour vérifier qu’un appareil donné répond aux exigences nécessaires. Cet outil vérifie également les paramètres réseau et les points de terminaison qui sont également nécessaires au bon travail du service.

## <a name="minimum-requirements"></a>Configuration minimale requise

Pour être inscrit à Microsoft Manged Desktop, un appareil doit satisfaire ou dépasser toutes ces exigences.

### <a name="manufacturer"></a>Fabricant

L’appareil doit avoir été effectué par l’un de ces fabricants :

- Dell
- HP
- Lenovo
- Microsoft


### <a name="installed-software"></a>Logiciels installés

Ce logiciel doit être préinstallé sur l’appareil :

- <b>\*</b>Windows 10 ou Windows 11 : édition Enterprise, Pro ou Pro Workstation
- la version 64 bits de Applications Microsoft 365 pour les grandes entreprises 
- Tous les pilotes de périphérique applicables


### <a name="physical-features"></a>Fonctionnalités physiques

Les appareils doivent avoir les fonctionnalités ci-après :

- Activé pour le démarrage sécurisé UEFI 
- Module de plateforme fiable 2.0 
- Capable de la sécurité basée sur la virtualisation 
- [Intégrité du code protégée par l’hyperviseur](/windows-hardware/drivers/bringup/device-guard-and-credential-guard) prise en charge par le BIOS

Pour plus d’informations sur ces fonctionnalités et les technologies qui y sont associées que le service utilise, voir [Microsoft Manged Desktop technologies.](../intro/technologies.md)

> [!NOTE]
>- ARM processeurs ne sont pas pris en charge.
>- <b>\*</b>Windows 11 présente une configuration [matérielle supplémentaire requise.](/windows/whats-new/windows-11-requirements)

Les appareils doivent respecter ou dépasser les limites suivantes pour le stockage et la mémoire :

- Le lecteur de démarrage doit être n’importe quel type autre qu’un disque dur. Par exemple, les lecteurs SSD, NVMe et eMMC sont tous des choix valides.
- Le lecteur de démarrage doit avoir une capacité d’au moins 128 Go.
- La mémoire ram interne de l’appareil doit être égale ou supérieure à 8 Go.

Si l’appareil a été effectué après le 1er juillet 2020, il doit également avoir un appareil photo ir, un lecteur d’empreintes digitales ou les deux, afin de prendre en [charge Windows Hello](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security).

## <a name="recommended-features"></a>Fonctionnalités recommandées

Vos utilisateurs auront une bien meilleure expérience si vous choisissez les appareils qui disposent de ces fonctionnalités :

- Soit un processeur intel vPro-platform, soit un processeur Pro AMD Ryzen
- Lecteur de démarrage du type SSD avec une capacité d’au moins 256 Go
- Mémoire ram (RAM) interne d’au moins 16 Go
- Prise en charge de la veille moderne
- L’appareil est de type PC sécurisé
- Prend en charge la protection DMA du noyau
