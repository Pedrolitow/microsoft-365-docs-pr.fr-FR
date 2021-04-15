---
title: Configuration requise de l’appareil
description: Résumé de la configuration matérielle et logicielle minimale requise pour que les appareils fonctionnent avec le Bureau géré Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: baaebd185389e7ac1f2173aed092141067a5629f
ms.sourcegitcommit: 4acf613587128cae27e0fd470d1216b509775529
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2021
ms.locfileid: "51768889"
---
# <a name="device-requirements"></a>Configuration requise de l’appareil

Bureau géré Microsoft évalue régulièrement les besoins en matière d'appareils à inclure dans le service. Cet article décrit la configuration matérielle et logicielle requise pour qu'un appareil fonctionne avec le Bureau géré Microsoft. Vous pouvez consulter la liste des appareils [spécifiques déjà](device-list.md) approuvés pour une utilisation avec le service en fonction de ces exigences.

> [!NOTE]
> Ces exigences peuvent changer à tout moment, mais nous vous fournirons un préavis de 30 jours pour toute modification de la configuration matérielle requise. Les exigences les plus récemment modifiées sont marquées par **\*** . 

## <a name="check-hardware-requirements"></a>Vérifier la configuration matérielle requise

Outre l'examen des spécifications de l'appareil, vous pouvez également utiliser le contrôle d'évaluation de la disponibilité [téléchargeable](../get-ready/readiness-assessment-downloadable.md) pour vérifier qu'un appareil donné répond aux exigences nécessaires. Cet outil vérifie également les paramètres réseau et les points de terminaison qui sont également nécessaires au bon travail du service.

## <a name="minimum-requirements"></a>Configuration minimale requise

Pour être inscrit au Bureau géré Microsoft, un appareil doit satisfaire ou dépasser toutes ces exigences.

### <a name="manufacturer"></a>Fabricant

L'appareil doit avoir été effectué par l'un de ces fabricants :

- Dell
- HP
- Lenovo
- Microsoft


### <a name="installed-software"></a>Logiciels installés

Ce logiciel doit être préinstallé sur l'appareil :

- Windows 10 Édition Entreprise, Professionnel ou Professionnel
- La version 64 bits de Microsoft 365 Apps pour entreprise 
- Tous les pilotes de périphérique applicables


### <a name="physical-features"></a>Fonctionnalités physiques

Les appareils doivent avoir les fonctionnalités ci-après :

- Activé pour le démarrage sécurisé UEFI 
- Module de plateforme fiable 2.0 
- Capable de la sécurité basée sur la virtualisation 
- [Intégrité du code protégée par l'hyperviseur](/windows-hardware/drivers/bringup/device-guard-and-credential-guard) prise en charge par le BIOS

Pour plus d'informations sur ces fonctionnalités et les technologies qui y sont associées que le service utilise, voir [Technologies bureau](../intro/technologies.md)géré Microsoft .

> [!NOTE]
> ARM processeurs ne sont pas pris en charge.

Les appareils doivent respecter ou dépasser les limites suivantes pour le stockage et la mémoire :

- Le lecteur de démarrage doit être n'importe quel type autre qu'un disque dur. Par exemple, les lecteurs SSD, NVMe et eMMC sont tous des choix valides.
- Le lecteur de démarrage doit avoir une capacité d'au moins 128 Go.
- La mémoire ram interne de l'appareil doit être égale ou supérieure à 8 Go.

Si l'appareil a été effectué après le 1er juillet 2020, il doit également avoir un appareil photo ir, un lecteur d'empreintes digitales ou les deux, afin de prendre en charge [Windows Hello](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security).

## <a name="recommended-features"></a>Fonctionnalités recommandées

Vos utilisateurs auront une bien meilleure expérience si vous choisissez les appareils qui disposent de ces fonctionnalités :

- Processeur Intel vPro-platform ou processeur AMD Ryzen Pro
- Lecteur de démarrage du type SSD avec une capacité d'au moins 256 Go
- Mémoire ram (RAM) interne d'au moins 16 Go
- Prise en charge de la veille moderne
- L’appareil est de type PC sécurisé
- Prend en charge la protection DMA du noyau
