---
title: Configuration requise de l’appareil
description: Résumé de la configuration matérielle et logicielle minimale requise pour que les appareils fonctionnent Microsoft Manged Desktop
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 957203829bfcfeb36696a1a4c34888938712b471
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326782"
---
# <a name="device-requirements"></a>Configuration requise de l’appareil

Microsoft Manged Desktop évalue régulièrement les besoins des appareils à inclure dans le service. Cet article décrit la configuration matérielle et logicielle requise pour qu’un appareil fonctionne avec Microsoft Manged Desktop.

Vous pouvez consulter la liste des appareils spécifiques déjà approuvés pour une utilisation en fonction de ces exigences. Filtrez les Microsoft Manged Desktop dans la page [Windows Pro appareils d’entreprise](https://www.microsoft.com/en-us/windows/business/devices).

> [!NOTE]
> Ces exigences peuvent changer à tout moment, mais nous vous fournirons un préavis de 30 jours pour toute modification de la configuration matérielle requise. Les exigences les plus récemment modifiées sont marquées par <b>\*</b>.

## <a name="check-hardware-requirements"></a>Vérifier la configuration matérielle requise

Outre l’examen des spécifications de l’appareil, vous pouvez également utiliser le contrôle d’évaluation de la disponibilité [téléchargeable pour](../get-ready/readiness-assessment-downloadable.md) vérifier que l’appareil répond aux exigences nécessaires.

Cet outil vérifie également les paramètres réseau et les points de terminaison nécessaires au bon travail du service.

## <a name="minimum-requirements"></a>Configuration minimale requise

Pour être inscrit à Microsoft Manged Desktop, un appareil doit satisfaire ou dépasser toutes ces exigences.

### <a name="manufacturer"></a>Fabricant

L’appareil doit avoir été effectué par l’un de ces fabricants :

- Dell
- HP
- Lenovo
- Microsoft

> [!NOTE]
> Depuis le 01 mars 2022, les appareils gérés par Microsoft Manged Desktop doivent être pris en charge par l’OEM.<br><br>Travaillez avec votre OEM pour savoir quand les appareils de votre portefeuille atteindront la prise en charge de la fin de vie. Les clients sont chargés de s’assurer que les appareils sont remplacés avant la fin de vie. Tous les appareils en dehors de la prise en charge OEM continueront d’être gérés par Microsoft Manged Desktop, mais la prise en charge de ces appareils peut être limitée car ils sont exposés à des problèmes de sécurité et de performances qui ne peuvent pas être atténués par notre service.
</b>

### <a name="installed-software"></a>Logiciels installés

Ce logiciel doit être préinstallé sur l’appareil :

- <b>\*</b>Windows 10 ou Windows 11 : Enterprise, Pro ou Pro Édition Station de travail.
- Version 64 bits de Microsoft 365 Apps pour Enterprise.
- Tous les pilotes de périphérique applicables.

### <a name="physical-features"></a>Fonctionnalités physiques

Les appareils doivent avoir les fonctionnalités ci-après :

- Activé pour le démarrage sécurisé UEFI.
- Module de plateforme fiable 2.0.
- Capable de la sécurité basée sur la virtualisation.
- [Intégrité du code protégée par l’hyperviseur prise](/windows-hardware/drivers/bringup/device-guard-and-credential-guard) en charge par le BIOS.

Pour plus d’informations sur ces fonctionnalités et les technologies associées utilisées par le service, voir [Microsoft Manged Desktop technologies](../intro/technologies.md).

> [!NOTE]
>- ARM processeurs ne sont pas pris en charge.
>- <b>\*</b>Windows 11 configuration matérielle [requise supplémentaire](/windows/whats-new/windows-11-requirements).

Les appareils doivent respecter ou dépasser les limites suivantes pour le stockage et la mémoire :

- Le lecteur de démarrage doit être n’importe quel type autre qu’un disque dur. Par exemple, les lecteurs SSD, NVMe et eMMC sont tous des choix valides.
- Le lecteur de démarrage doit avoir une capacité d’au moins 128 Go.
- La mémoire ram interne de l’appareil doit être égale ou supérieure à 8 Go.

Si l’appareil a été effectué après le 1er juillet 2020, il doit également avoir un appareil photo ir, un lecteur d’empreintes digitales ou les deux, afin de prendre en [charge Windows Hello](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security).

## <a name="recommended-features"></a>Fonctionnalités recommandées

Vos utilisateurs auront une bien meilleure expérience si vous choisissez des appareils dotés de ces fonctionnalités :

- Soit un processeur intel vPro-platform, soit un processeur Pro AMD Ryzen.
- Lecteur de démarrage du type SSD avec une capacité d’au moins 256 Go.
- Mémoire d’appareil interne (RAM) d’au moins 16 Go.
- Prise en charge de la veille moderne.
- L’appareil est de type PC de type Secured-core.
- Prend en charge la protection DMA du noyau.
