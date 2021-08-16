---
title: Méthodes et outils d’intégration pour Windows 10 appareils
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Intégrer Windows 10 des appareils afin qu’ils peuvent envoyer des données de capteur aux solutions Microsoft 365 conformité
ms.openlocfilehash: ac2cbf41d77960338885a98ffddc707618988848c6be8cc7ef4cb911da50a40d
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53895306"
---
# <a name="onboarding-tools-and-methods-for-windows-10-devices"></a>Outils et méthodes d’intégration pour les appareils Windows 10.

**S’applique à :**
- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)

Les appareils de votre organisation doivent être configurés pour que le service Microsoft 365 protection contre la perte de données du point de terminaison puisse obtenir des données de capteur à partir de ces derniers. Il existe différentes méthodes et outils de déploiement que vous pouvez utiliser pour configurer les appareils de votre organisation.

Les méthodes et outils de déploiement suivants sont pris en charge :

- stratégie de groupe
- Microsoft Endpoint Configuration Manager
- Gestion des appareils mobiles (y compris Microsoft Intune)
- script local

## <a name="in-this-section"></a>Dans cette section
Rubrique | Description
:---|:---
[Intégrer des Windows 10 à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md) | Utilisez la stratégie de groupe pour déployer le package de configuration sur les appareils.
[Intégrer Windows appareils à l’aide Microsoft Endpoint Configuration Manager](dlp-configure-endpoints-sccm.md) | Vous pouvez utiliser la version Microsoft Endpoint Configuration Manager (branche actuelle) 1606 ou la version 1602 de Microsoft Endpoint Configuration Manager (branche actuelle) ou une version antérieure pour déployer le package de configuration sur les appareils.
[Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md) | Utilisez les outils de gestion des appareils mobiles ou Microsoft Intune pour déployer le package de configuration sur l’appareil.
[Intégrer les appareils Windows 10 utilisant un script local](dlp-configure-endpoints-script.md) | Découvrez comment utiliser le script local pour déployer le package de configuration sur les points de terminaison.
[Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](dlp-configure-endpoints-vdi.md) | Découvrez comment utiliser le package de configuration pour configurer des appareils VDI.