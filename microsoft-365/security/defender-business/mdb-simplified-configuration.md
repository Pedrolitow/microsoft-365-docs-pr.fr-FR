---
title: Processus de configuration simplifié dans Microsoft Defender pour entreprises
description: Defender pour Entreprise vous permet de gagner du temps avec un processus de configuration simplifié. Découvrez comment cela fonctionne et protège votre entreprise dès le premier jour.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 7fd6f92e5d956adf43a75bac0e28f7ca79c0f930
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2022
ms.locfileid: "66770896"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>Processus de configuration simplifié dans Microsoft Defender pour entreprises

Microsoft Defender pour entreprises propose un processus de configuration simplifié conçu spécialement pour les petites et moyennes entreprises. Une expérience similaire à un Assistant ne fait pas l’objet d’une estimation de l’intégration et de la gestion des appareils. **Nous vous recommandons d’utiliser le processus de configuration simplifié, mais vous n’êtes pas limité à cette option**.

Pour intégrer des appareils et configurer des paramètres de sécurité pour les appareils de votre entreprise, vous pouvez choisir parmi les expériences suivantes :

- Processus de configuration simplifié dans Microsoft Defender pour entreprises (*recommandé*) ; ou
- Utilisez Microsoft Intune (inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md)).

## <a name="what-to-do"></a>Procédure

1. [Passez en revue vos options d’installation et de configuration](#review-your-setup-and-configuration-options).
2. [En savoir plus sur le processus de configuration simplifié dans Defender entreprise](#why-we-recommend-the-simplified-configuration-process).
3. [Passez à vos étapes suivantes](#next-steps).


## <a name="review-your-setup-and-configuration-options"></a>Passer en revue vos options d’installation et de configuration

Le tableau suivant décrit chaque expérience.

| Expérience du portail  | Description  |
|---------|---------|
| Expérience de configuration simplifiée dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Il s’agit de l’option recommandée pour la plupart des clients.*)  | L’expérience de configuration simplifiée inclut une expérience de type Assistant pour vous aider à configurer Defender entreprise et à le configurer. Pour en savoir plus, consultez [l’Assistant pour configurer Microsoft Defender pour entreprises](mdb-use-wizard.md).<br/><br/>La configuration simplifiée inclut également des stratégies et des paramètres de sécurité par défaut pour protéger les appareils de votre entreprise dès qu’ils sont intégrés à Defender entreprise. Vous pouvez afficher et modifier les stratégies par défaut en fonction des besoins de votre entreprise. Pour en savoir plus, consultez [Afficher ou modifier les stratégies d’appareil dans Microsoft Defender pour entreprises](mdb-view-edit-policies.md).<br/><br/>Avec l’expérience simplifiée, votre équipe de sécurité utilise le portail Microsoft 365 Defender comme un guichet unique pour : <ul><li>Installer et configurer Defender pour les PME</li><li>Afficher et gérer les incidents</li><li>Répondre aux menaces et les atténuer</li><li>Affichage des rapports</li><li>Examiner les actions en attente ou terminées  |
| Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Intune est un fournisseur de gestion des appareils mobiles (GPM) et de gestion des applications mobiles (MAM) basé sur le cloud pour les applications et les appareils. Si vous utilisez déjà Intune, vous pouvez continuer à utiliser le centre d’administration Endpoint Manager pour gérer des appareils tels que des téléphones mobiles, des tablettes et des ordinateurs portables. Voir [Microsoft Intune : Gestion des appareils](/mem/intune/fundamentals/what-is-device-management). <br/><br/>Intune n’est pas inclus dans la version autonome de Defender entreprise, mais vous pouvez l’ajouter à votre abonnement si nécessaire. Si vous avez [Microsoft 365 Business Premium](../../business-premium/index.md), vous avez déjà Intune. |

## <a name="why-we-recommend-the-simplified-configuration-process"></a>Pourquoi nous recommandons le processus de configuration simplifié

Nous vous recommandons le processus de configuration simplifié dans Defender entreprise, car il est rationalisé en particulier pour les petites et moyennes entreprises. L’Assistant Installation vous aide à intégrer des appareils et à les gérer dans le portail Microsoft 365 Defender, où vous verrez et gérez également les menaces détectées. Lorsque vous intègrez des appareils, ils sont protégés immédiatement avec les paramètres de sécurité et les stratégies par défaut. Vous pouvez conserver vos paramètres par défaut tels qu’ils sont ou apporter des modifications en fonction des besoins de votre entreprise. Vous pouvez également ajouter de nouvelles stratégies personnalisées en fonction des besoins de votre entreprise.

## <a name="next-steps"></a>Prochaines étapes

- [Configurez et configurez Microsoft Defender pour entreprises](mdb-setup-configuration.md).
- [Commencez à utiliser Microsoft Defender pour entreprises](mdb-get-started.md).
