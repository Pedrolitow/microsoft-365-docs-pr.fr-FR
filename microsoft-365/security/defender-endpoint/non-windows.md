---
title: Microsoft Defender pour point de terminaison pour les plateformes non Windows
description: En savoir plus sur les fonctionnalités de Microsoft Defender pour les points de terminaison pour les plateformes Windows non-serveurs
keywords: non windows, mac, macos, linux, android
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a975daa6b73f39722b077cda307aa5ea806b1e1b
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59181078"
---
# <a name="microsoft-defender-for-endpoint-for-non-windows-platforms"></a>Microsoft Defender pour point de terminaison pour les plateformes non Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft est en train d’étendre ses principales fonctionnalités de sécurité de point de terminaison au-delà de Windows et Windows Server vers macOS, Linux, Android et iOS.

Les organisations sont confrontées à des menaces sur divers appareils et plateformes. Nos équipes s’engagent à créer des solutions de sécurité non seulement pour *Microsoft,* mais aussi pour *permettre* à nos clients de protéger et de sécuriser leurs environnements hetératifs. Nous sommes à l’écoute des commentaires des clients et nous travaillons en étroite collaboration avec nos clients pour créer des solutions qui répondent à leurs besoins.

Avec Microsoft Defender pour point de terminaison, les clients bénéficient d’une vue unifiée de toutes les menaces et alertes dans le Centre de sécurité Microsoft Defender, sur les plateformes Windows et non-Windows, ce qui leur permet d’obtenir une vue complète de ce qui se passe dans leur environnement, ce qui leur permet d’évaluer et de répondre plus rapidement aux menaces.

## <a name="microsoft-defender-for-endpoint-on-macos"></a>Microsoft Defender pour point de terminaison macOS 

Microsoft Defender pour le point de terminaison sur macOS offre des fonctionnalités antivirus, protection évolutive des points de terminaison (PEPT) et gestion des vulnérabilités pour les trois dernières versions publiées de macOS. Les clients peuvent déployer et gérer la solution via Microsoft Endpoint Manager et Jamf. Comme avec les applications Microsoft Office sur macOS, Microsoft Auto Update est utilisé pour gérer les mises à jour de Microsoft Defender pour Endpoint sur Mac. Pour plus d’informations sur les principales fonctionnalités et avantages, lisez [nos annonces.](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/macOS)

Pour plus d’informations sur la mise en place, consultez la [documentation](microsoft-defender-endpoint-mac.md)de Defender for Endpoint sur macOS.

>[!NOTE]
>Les fonctionnalités suivantes ne sont actuellement pas pris en charge sur les points de terminaison macOS :
>- Protection contre la perte de données
>- Réponse en direct


## <a name="microsoft-defender-for-endpoint-on-linux"></a>Microsoft Defender pour point de terminaison Linux

Microsoft Defender pour point de terminaison sur Linux offre des fonctionnalités préventives, protection évolutive des points de terminaison (PEPT) et gestion des vulnérabilités pour les serveurs Linux. Cela inclut une expérience de ligne de commande complète pour configurer et gérer l’agent, lancer des analyses et gérer les menaces. Nous groupons les versions récentes des six distributions linux server les plus courantes : RHEL 7.2+, CentOS Linux 7.2+, Ubuntu 16 LTS ou version ultérieure LTS, SLES 12+, Debian 9+ et Oracle Linux 7.2. Microsoft Defender pour point de terminaison sur Linux peut être déployé et configuré à l’aide de l’outil de gestion de la configuration Linux existant, Enfiché, Ansible ou. Pour plus d’informations sur les principales fonctionnalités et avantages, lisez [nos annonces.](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Linux)

Pour plus d’informations sur la mise en place, consultez la [documentation](microsoft-defender-endpoint-linux.md)de Microsoft Defender pour Endpoint sur Linux.

>[!NOTE]
>Les fonctionnalités suivantes ne sont actuellement pas pris en charge sur les points de terminaison Linux :
>- Protection contre la perte de données
>- Réponse en direct
>- SIEM



## <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender pour point de terminaison Android

Microsoft Defender pour point de terminaison sur Android est notre solution de défense contre les menaces mobiles pour les appareils exécutant Android 6.0 et version supérieure. Les modes Enterprise Android (Profil de travail) et Administrateur d’appareil sont pris en charge. Sur Android, nous proposons une protection web, qui inclut l’anti-hameçonnage, le blocage des connexions non sécurisées et la définition d’indicateurs personnalisés. La solution recherche les programmes malveillants et les applications potentiellement indésirables (PUA) et offre des fonctionnalités supplémentaires de protection contre les violations grâce à l’intégration avec Microsoft Endpoint Manager et l’accès conditionnel. Pour plus d’informations sur les principales fonctionnalités et avantages, lisez [nos annonces.](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Android)

Pour plus d’informations sur la mise en place, consultez la [documentation](microsoft-defender-endpoint-android.md)de Microsoft Defender for Endpoint sur Android.

## <a name="microsoft-defender-for-endpoint-on-ios"></a>Microsoft Defender pour point de terminaison iOS

Microsoft Defender pour point de terminaison sur iOS est notre solution de défense contre les menaces mobiles pour les appareils exécutant iOS 11.0 et des appareils plus élevés. Les appareils inscrits au sein du client d’un client (inscrits ou non inscrits) sont pris en charge. Les appareils inscrits supervisés et non pris en charge sont pris en charge. Sur iOS, nous proposons une protection web, qui inclut l’anti-hameçonnage, le blocage des connexions non sécurisées et la définition d’indicateurs personnalisés, ainsi que la détection d’attaques par jailbreak. Pour plus d’informations sur les principales fonctionnalités et avantages, lisez [nos annonces.](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bg-p/MicrosoftDefenderATPBlog/label-name/iOS) 

Pour plus d’informations sur la mise en place, consultez la [documentation](microsoft-defender-endpoint-ios.md)de Microsoft Defender for Endpoint sur iOS.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence 

Les utilisateurs titulaires d’une licence éligible peuvent utiliser Microsoft Defender pour endpoint sur cinq appareils simultanés au plus. Microsoft Defender for Endpoint est également disponible à l’achat auprès d’un fournisseur de solutions Cloud (CSP).

Les clients peuvent obtenir Microsoft Defender pour le point de terminaison sur macOS via une licence Microsoft Defender pour point de terminaison autonome, dans le cadre de Microsoft 365 A5/E5 ou Microsoft 365 Security.

Les fonctionnalités récemment annoncées de Microsoft Defender pour Endpoint sur Android et iOS sont incluses dans les offres mentionnées ci-dessus dans le cadre des cinq appareils qualifiés pour les utilisateurs sous licence éligibles.

Defender pour le point de terminaison sur Linux est disponible via la référence SKU de Defender for Endpoint Server disponible pour les clients commerciaux et éducation.

Veuillez contacter votre équipe de compte ou votre CSP pour obtenir des tarifs et des conditions d’éligibilité supplémentaires.
