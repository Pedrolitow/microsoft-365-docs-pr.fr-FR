---
title: Microsoft Defender pour point de terminaison pour les plateformes non Windows
description: En savoir plus sur les fonctionnalités de Microsoft Defender pour point de terminaison pour les plateformes non Windows
keywords: non windows, mac, macos, linux, android
search.product: eADQiWindows 10XVcnh
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
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: b290a875f7f1abcc65679f584f7380537e893268
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67692022"
---
# <a name="microsoft-defender-for-endpoint-for-non-windows-platforms"></a>Microsoft Defender pour point de terminaison pour les plateformes non Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison plan 1 et plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft a été en route pour étendre ses fonctionnalités de sécurité des points de terminaison de pointe au-delà de Windows et Windows Server à macOS, Linux, Android et iOS.

Les organisations sont confrontées à des menaces sur une variété de plateformes et d’appareils. Nos équipes se sont engagées à créer des solutions de sécurité non seulement *pour* Microsoft, mais également *pour* permettre à nos clients de protéger et de sécuriser leurs environnements hétérogènes. Nous sommes à l’écoute des commentaires des clients et travaillons en étroite collaboration avec nos clients pour créer des solutions qui répondent à leurs besoins.

Avec Microsoft Defender pour point de terminaison, les clients bénéficient d’une vue unifiée de toutes les menaces et alertes dans le portail Microsoft 365 Defender, sur les plateformes Windows et non Windows, ce qui leur permet d’obtenir une vue d’ensemble de ce qui se passe dans leur environnement, ce qui leur permet d’évaluer et de répondre plus rapidement aux menaces.

## <a name="microsoft-defender-for-endpoint-on-macos"></a>Microsoft Defender pour point de terminaison macOS

Microsoft Defender pour point de terminaison sur macOS offre des fonctionnalités antivirus, de détection et de réponse de point de terminaison (EDR) et de gestion des vulnérabilités pour les trois dernières versions publiées de macOS. Les clients peuvent déployer et gérer la solution via Microsoft Endpoint Manager et Jamf. Tout comme avec les applications Microsoft Office sur macOS, Microsoft Auto Update est utilisé pour gérer Microsoft Defender pour point de terminaison sur les mises à jour Mac. Pour plus d’informations sur les principales fonctionnalités et avantages, consultez nos [annonces](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/macOS).

Pour plus d’informations sur la prise en main, consultez la [documentation](microsoft-defender-endpoint-mac.md) defender pour point de terminaison sur macOS.

> [!NOTE]
> Les fonctionnalités suivantes ne sont actuellement pas prises en charge sur les points de terminaison macOS :
>
> - Gestion de la sécurité pour Microsoft Defender pour point de terminaison

## <a name="microsoft-defender-for-endpoint-on-linux"></a>Microsoft Defender pour point de terminaison Linux

Microsoft Defender pour point de terminaison sur Linux offre des fonctionnalités antivirus préventives (AV), de détection et de réponse de point de terminaison (EDR) et de gestion des vulnérabilités pour les serveurs Linux. Cela inclut une expérience de ligne de commande complète pour configurer et gérer l’agent, lancer des analyses et gérer les menaces. Nous prenons en charge les versions récentes des six distributions de serveur Linux les plus courantes : RHEL 7.2+, CentOS Linux 7.2+, Ubuntu 16 LTS ou versions ultérieures de LTS, SLES 12+, Debian 9+, et Oracle Linux 7.2. Microsoft Defender pour point de terminaison sur Linux peut être déployée et configurée à l’aide de Puppet, Ansible ou à l’aide de votre outil de gestion de configuration Linux existant. Pour plus d’informations sur les principales fonctionnalités et avantages, consultez nos [annonces](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Linux).

Pour plus d’informations sur la prise en main, consultez la [documentation](microsoft-defender-endpoint-linux.md) Microsoft Defender pour point de terminaison sur Linux.


> [!NOTE]
> Les fonctionnalités suivantes ne sont actuellement pas prises en charge sur les points de terminaison Linux :
>
> - Protection contre la perte de données
> - Gestion de la sécurité pour Microsoft Defender pour point de terminaison

## <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender pour point de terminaison Android

Microsoft Defender pour point de terminaison sur Android est notre solution de défense contre les menaces mobiles pour les appareils exécutant Android 6.0 et versions ultérieures. Les modes Android Entreprise (Profil professionnel) et Administrateur d’appareil sont pris en charge. Sur Android, nous offrons une protection web, qui inclut l’anti-hameçonnage, le blocage des connexions non sécurisées et la définition d’indicateurs personnalisés. La solution recherche les programmes malveillants et les applications potentiellement indésirables (PUA) et offre des fonctionnalités supplémentaires de prévention des violations par le biais de l’intégration à Microsoft Endpoint Manager et à l’accès conditionnel. Pour plus d’informations sur les principales fonctionnalités et avantages, consultez nos [annonces](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Android).

Pour plus d’informations sur la prise en main, consultez la [documentation](microsoft-defender-endpoint-android.md) Microsoft Defender pour point de terminaison sur Android.

## <a name="microsoft-defender-for-endpoint-on-ios"></a>Microsoft Defender pour point de terminaison iOS

Microsoft Defender pour point de terminaison sur iOS est notre solution de défense contre les menaces mobiles pour les appareils exécutant iOS 11.0 et versions ultérieures. Les appareils inscrits au sein du locataire d’un client (inscrits ou non inscrits) sont pris en charge. Les appareils inscrits supervisés et non supervisés sont pris en charge. Sur iOS, nous offrons une protection web, qui inclut l’anti-hameçonnage, le blocage des connexions non sécurisées et la définition d’indicateurs personnalisés et la détection de jailbreak. Pour plus d’informations sur les principales fonctionnalités et avantages, consultez nos [annonces](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

Pour plus d’informations sur la prise en main, consultez la documentation Microsoft Defender pour point de terminaison sur [iOS.](microsoft-defender-endpoint-ios.md)

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Les utilisateurs sous licence éligibles peuvent utiliser Microsoft Defender pour point de terminaison sur jusqu’à cinq appareils simultanés. Microsoft Defender pour point de terminaison est également disponible à l’achat auprès d’un fournisseur de solutions cloud (CSP).

Les clients peuvent obtenir Microsoft Defender pour point de terminaison sur macOS via une licence Microsoft Defender pour point de terminaison autonome, dans le cadre de Microsoft 365 A5/E5 ou de Microsoft 365 Security.

Les fonctionnalités récemment annoncées de Microsoft Defender pour point de terminaison sur Android et iOS sont incluses dans les offres mentionnées ci-dessus dans le cadre des cinq appareils qualifiés pour les utilisateurs sous licence éligibles.

Defender pour point de terminaison sur Linux est disponible via la référence SKU Defender pour point de terminaison qui est disponible pour les clients commerciaux et éducatifs.

Contactez votre équipe de compte ou votre fournisseur de solutions Cloud pour connaître les tarifs et les conditions d’éligibilité supplémentaires.
