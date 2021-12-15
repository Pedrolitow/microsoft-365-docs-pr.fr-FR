---
title: Processus de configuration simplifié dans Microsoft Defender entreprise (prévisualisation)
description: En savoir plus sur le processus de configuration simplifié dans Microsoft Defender pour Entreprises (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/13/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: e8cf2ae8e17898753be43c9e2160d8a473f8db8d
ms.sourcegitcommit: 74f79aacb4ffcc6cb0e315239b1493324eabb449
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2021
ms.locfileid: "61508285"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business-preview"></a>Processus de configuration simplifié dans Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et [](https://aka.ms/mdb-preview) sera progressivement mis en place pour les clients et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un ensemble initial de [scénarios](mdb-tutorials.md#try-these-preview-scenarios)et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Microsoft Defender pour Entreprise (prévisualisation) propose un processus de configuration simplifié, conçu en particulier pour les petites et moyennes entreprises. Cette expérience tire le risque de l’intégration et de la gestion des appareils, avec une expérience de l’assistant et des stratégies par défaut conçues pour protéger les appareils de votre entreprise dès le premier jour. **Nous vous recommandons d’utiliser le processus de configuration simplifié ; toutefois, vous n’êtes** pas limité à cette option.

En ce qui concerne l’intégration d’appareils et la configuration des paramètres de sécurité pour les appareils de votre entreprise, vous pouvez choisir parmi plusieurs expériences : 

- Processus de configuration simplifié dans Microsoft Defender entreprise (prévisualisation)*(recommandé)* 
- Microsoft Endpoint Manager, qui inclut les Microsoft Intune
- Votre solution non-Microsoft pour la gestion des appareils 

## <a name="what-to-do"></a>Procédure

1. [Passer en revue vos options d’installation et de configuration](#review-your-setup-and-configuration-options)
2. [En savoir plus sur le processus de configuration simplifié dans Defender pour Entreprises (prévisualisation)](#why-we-recommend-using-the-simplified-configuration-process)
3. [Passer aux étapes suivantes](#next-steps)

## <a name="review-your-setup-and-configuration-options"></a>Passer en revue vos options d’installation et de configuration

Le tableau suivant décrit chaque expérience :
<br/><br/>

| Expérience de portail  | Description  |
|---------|---------|
| Expérience de configuration simplifiée dans le portail Microsoft 365 Defender ( [https://security.microsoft.com](https://security.microsoft.com) ) <br/>(*Il s’agit de l’option recommandée pour la plupart des clients)*  | L’expérience de configuration simplifiée inclut des paramètres de sécurité et des stratégies par défaut qui vous aident à protéger les appareils de votre entreprise dès le premier jour. Avec cette expérience, votre équipe de sécurité utilise le portail Microsoft 365 Defender pour : <br/>- Installer et configurer Defender pour les entreprises (prévisualisation) <br/>- Afficher et gérer les incidents<br/>- Répondre aux menaces et les atténuer<br/>- Afficher les rapports<br/>- Examiner les actions en attente ou terminées <br/><br/> Ce portail est votre magasin unique pour les paramètres de sécurité et les fonctionnalités de protection contre les menaces de votre entreprise. Vous obtenez une expérience simplifiée pour vous aider à démarrer rapidement et efficacement.  De plus, vous pouvez modifier vos paramètres ou définir de nouvelles stratégies en fonction des besoins de votre entreprise.<br/><br/>Pour plus d’informations, voir [Afficher ou modifier des stratégies d’appareil dans Microsoft Defender entreprise (prévisualisation).](mdb-view-edit-policies.md) |
| Le Microsoft Endpoint Manager d’administration de l’utilisateur ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) )  | Microsoft Endpoint Manager inclut Microsoft Intune, un fournisseur de gestion des périphériques mobiles (MDM) basé sur le cloud et de gestion des applications mobiles (MAM) pour les applications et les appareils. <br/><br/>De nombreuses organisations utilisent Intune pour gérer leurs appareils, tels que les téléphones mobiles, les tablettes et les ordinateurs portables. Pour en savoir plus, voir Microsoft Intune est un fournisseur de gestion des appareils mobiles et de gestion des appareils [mobiles pour vos appareils.](/mem/intune/fundamentals/what-is-intune) <br/><br/>Si vous utilisez déjà Microsoft Intune ou Microsoft Endpoint Manager, vous pouvez continuer à utiliser cette solution. |
| Votre solution de gestion des appareils non-Microsoft  | Si vous utilisez une solution de gestion des appareils et de la productivité non Microsoft, telle que Jamf pour macOS ou Ansible pour Linux, vous pouvez continuer à utiliser cette solution avec Defender for Business (prévisualisation). <br/><br/>Lorsque les appareils sont intégrés à Defender pour Entreprises (prévisualisation), leur état et leurs alertes s’afficheront sur le Microsoft 365 Defender web. Pour en savoir plus, consultez les options de l’outil d’intégration [et de configuration de Defender pour Endpoint.](../defender-endpoint/onboard-configure.md)<br/><br/>Si vous utilisez déjà une solution de gestion des appareils non Microsoft, vous pouvez continuer à utiliser cette solution. |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Pourquoi nous vous recommandons d’utiliser le processus de configuration simplifié

**Nous vous recommandons d’utiliser le processus de configuration simplifié dans Microsoft Defender entreprise (prévisualisation)** pour la plupart des clients. Le processus de configuration simplifié est simplifié, en particulier pour les petites et moyennes entreprises. Defender pour les entreprises (prévisualisation) est conçu pour vous aider à protéger les appareils de votre entreprise le premier jour, sans nécessiter une expertise technique approfondie ou des connaissances spéciales. Avec les stratégies et paramètres de sécurité par défaut, vos appareils sont protégés dès qu’ils sont intégrés.


Defender for Business (prévisualisation) est conçu pour fournir une protection renforcée tout en vous faisant gagner du temps et des efforts dans la configuration de vos paramètres de sécurité. L’expérience simplifiée dans le portail Microsoft 365 Defender facilite l’intégration des appareils et leur gestion. En outre, les stratégies par défaut sont incluses afin que les appareils de votre entreprise soient protégés dès qu’ils sont intégrés. Vous pouvez conserver vos paramètres par défaut tels qu’ils sont ou apporter des modifications en fonction des besoins de votre entreprise. Vous pouvez également ajouter de nouvelles stratégies pour gérer les appareils selon vos besoins.

## <a name="next-steps"></a>Étapes suivantes

- [Installer et configurer Microsoft Defender pour les entreprises (prévisualisation)](mdb-setup-configuration.md)

- [Commencer à utiliser Microsoft Defender pour les entreprises (prévisualisation)](mdb-get-started.md)