---
title: Processus de configuration simplifié dans Microsoft Defender pour les PME
description: En savoir plus sur le processus de configuration simplifié dans Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 02f970f7ad9981336ba54aaafcf936e952f1b726
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663113"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>Processus de configuration simplifié dans Microsoft Defender pour les PME

> [!IMPORTANT]
> Microsoft Defender pour les PME est déployée pour [Microsoft 365 Business Premium](../../business-premium/index.md) clients, à compter du 1er mars 2022. Defender entreprise en tant qu’abonnement autonome est en préversion et sera déployé progressivement pour les clients et les partenaires informatiques qui [s’inscrivent ici](https://aka.ms/mdb-preview) pour le demander. La préversion inclut un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios), et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations contenues dans cet article concernent des produits/services prédéfinis qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expresse ou implicite, pour les informations fournies ici. 

Microsoft Defender pour les PME propose un processus de configuration simplifié, conçu spécialement pour les petites et moyennes entreprises. Cette expérience permet de deviner comment intégrer et gérer des appareils, avec une expérience de type Assistant et des stratégies par défaut conçues pour protéger les appareils de votre entreprise dès le premier jour. **Nous vous recommandons d’utiliser le processus de configuration simplifié. Toutefois, vous n’êtes pas limité à cette option**.

Quand il s’agit d’intégrer des appareils et de configurer des paramètres de sécurité pour les appareils de votre entreprise, vous pouvez choisir parmi plusieurs expériences : 

- Processus de configuration simplifié dans Microsoft Defender pour les PME (*recommandé*) 
- Microsoft Endpoint Manager, qui inclut Microsoft Intune (inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md))
- Votre solution non-Microsoft pour la gestion des appareils 

## <a name="what-to-do"></a>Procédure

1. [Passer en revue vos options d’installation et de configuration](#review-your-setup-and-configuration-options)

2. [En savoir plus sur le processus de configuration simplifié dans Defender entreprise](#why-we-recommend-using-the-simplified-configuration-process)

3. [Passez à vos étapes suivantes](#next-steps)

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">court sondage sur Microsoft Defender pour les PME</a>. Vos commentaires sont les bienvenus.
>

## <a name="review-your-setup-and-configuration-options"></a>Passer en revue vos options d’installation et de configuration

Le tableau suivant décrit chaque expérience :
<br/><br/>

| Expérience du portail  | Description  |
|---------|---------|
| Expérience de configuration simplifiée dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Il s’agit de l’option recommandée pour la plupart des clients*)  | L’expérience de configuration simplifiée inclut une expérience de type Assistant pour vous aider à configurer Defender entreprise et à le configurer. La configuration simplifiée inclut également des paramètres de sécurité et des stratégies par défaut pour vous aider à protéger les appareils de votre entreprise dès qu’ils sont intégrés à Defender entreprise. <br/><br/>Avec cette expérience, votre équipe de sécurité utilise le portail Microsoft 365 Defender pour : <br/>- Configurer et configurer Defender entreprise <br/>- Afficher et gérer les incidents<br/>- Répondre aux menaces et les atténuer<br/>- Afficher les rapports<br/>- Passer en revue les actions en attente ou terminées <br/><br/> Le portail Microsoft 365 Defender est votre magasin unique pour les paramètres de sécurité et les fonctionnalités de protection contre les menaces de votre entreprise. Vous bénéficiez d’une expérience simplifiée pour vous aider à démarrer rapidement et efficacement. Pour plus d’informations, consultez [Utiliser l’Assistant pour configurer Microsoft Defender pour les PME](mdb-use-wizard.md).<br/><br/>Vous pouvez également modifier vos paramètres ou définir de nouvelles stratégies en fonction des besoins de votre entreprise.<br/><br/>Pour en savoir plus, consultez [Afficher ou modifier les stratégies d’appareil dans Microsoft Defender pour les PME](mdb-view-edit-policies.md). |
| Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Endpoint Manager inclut Microsoft Intune, un fournisseur de gestion des appareils mobiles (GPM) basé sur le cloud et un fournisseur de gestion des applications mobiles (GAM) pour les applications et les appareils. [Microsoft 365 Business Premium](../../business-premium/index.md) clients ont déjà Endpoint Manager. <br/><br/>De nombreuses entreprises utilisent Intune pour gérer leurs appareils, tels que les téléphones mobiles, les tablettes et les ordinateurs portables. Pour plus d’informations, consultez [Microsoft Intune est un fournisseur GPM et GAM pour vos appareils](/mem/intune/fundamentals/what-is-intune). <br/><br/>Si vous utilisez déjà Microsoft Intune ou Microsoft Endpoint Manager, vous pouvez continuer à utiliser cette solution. |
| Votre solution de gestion des appareils non Microsoft  | Si vous utilisez une solution de gestion des appareils et de productivité non Microsoft, vous pouvez continuer à utiliser cette solution avec Defender entreprise. <br/><br/>Lorsque les appareils sont intégrés à Defender entreprise, vous verrez leur état et leurs alertes dans le portail Microsoft 365 Defender. Pour en savoir plus, consultez [les options de l’outil d’intégration et de configuration pour Defender pour point de terminaison](../defender-endpoint/onboard-configure.md). |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Pourquoi nous vous recommandons d’utiliser le processus de configuration simplifié

**Nous vous recommandons d’utiliser le processus de configuration simplifié dans Microsoft Defender pour les PME** pour la plupart des clients. Le processus de configuration simplifié est simplifié, en particulier pour les petites et moyennes entreprises. Defender entreprise est conçu pour vous aider à protéger les appareils de votre entreprise dès le premier jour, sans avoir besoin d’une expertise technique approfondie ou d’une connaissance particulière. Avec les paramètres et stratégies de sécurité par défaut, vos appareils sont protégés dès qu’ils sont intégrés.

Defender entreprise est conçu pour fournir une protection renforcée tout en vous faisant gagner du temps et des efforts dans la configuration de vos paramètres de sécurité. L’expérience simplifiée du portail Microsoft 365 Defender simplifie l’intégration et la gestion des appareils. En outre, les stratégies par défaut sont incluses afin que les appareils de votre entreprise soient protégés dès qu’ils sont intégrés. Vous pouvez conserver vos paramètres par défaut tels qu’ils sont ou apporter des modifications en fonction des besoins de votre entreprise. Vous pouvez également ajouter de nouvelles stratégies pour gérer les appareils en fonction des besoins.

## <a name="next-steps"></a>Prochaines étapes

- [Configurer et configurer Microsoft Defender pour les PME](mdb-setup-configuration.md)

- [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md)
