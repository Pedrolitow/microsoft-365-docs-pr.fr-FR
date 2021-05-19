---
title: Résoudre les problèmes sur Microsoft Defender pour point de terminaison sur iOS
description: Résolution des problèmes et FAQ - Microsoft Defender pour point de terminaison sur iOS
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, troubleshoot, faq, how to
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 82a3fcc58b97f53f584befae77c86e8a18952a23
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52539303"
---
# <a name="troubleshoot-issues-on-microsoft-defender-for-endpoint-on-ios"></a>Résoudre les problèmes sur Microsoft Defender pour point de terminaison sur iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

Cette rubrique fournit des informations de dépannage pour vous aider à résoudre les problèmes qui peuvent survenir lorsque vous utilisez Microsoft Defender pour Endpoint sur iOS.



> [!NOTE]
> Defender pour le point de terminaison sur iOS utiliserait un VPN pour fournir la fonctionnalité de protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/en boucle autonome qui ne prend pas le trafic en dehors de l’appareil.

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>Les applications ne fonctionnent pas lorsque le VPN est allumé
Certaines applications cessent de fonctionner lorsqu’un VPN actif est détecté. Vous pouvez désactiver le VPN pendant la durée d’utilisation de ces applications. 

Par défaut, Defender pour le point de terminaison sur iOS inclut et active la fonctionnalité de protection web. [La protection web permet](web-protection-overview.md) de sécuriser les appareils contre les menaces web et de protéger les utilisateurs contre les attaques par hameçonnage. Defender pour le point de terminaison sur iOS utilise un VPN pour fournir cette protection. Notez qu’il s’agit d’un VPN local et, contrairement au VPN traditionnel, le trafic réseau n’est pas envoyé en dehors de l’appareil.

Bien qu’il soit activé par défaut, il se peut que vous de soyez dans certains cas dans l’obligation de désactiver le VPN. Par exemple, vous souhaitez exécuter certaines applications qui ne fonctionnent pas lorsqu’un VPN est configuré. Dans ce cas, vous pouvez choisir de désactiver le VPN de l’application sur l’appareil en suivant les étapes ci-dessous :

1. Sur votre appareil iOS, ouvrez **l’application Paramètres,** cliquez ou appuyez sur **Général,** puis **sur VPN.**
1. Cliquez ou appuyez sur le bouton « i » de Microsoft Defender pour le point de terminaison.
1. Désactivez la **Connecter à la demande** pour désactiver le VPN.

    > [!div class="mx-imgBorder"]
    > ![Connexion de la connexion VPN à la demande](images/ios-vpn-config.png)

> [!NOTE]
> La protection web n’est pas disponible lorsque le VPN est désactivé. Pour activer à nouveau la Protection Web, ouvrez l’application Microsoft Defender pour point de terminaison sur l’appareil, puis cliquez ou appuyez sur **Démarrer le VPN.**

## <a name="issues-with-multiple-vpn-profiles"></a>Problèmes avec plusieurs profils VPN

Apple iOS ne prend pas en charge plusieurs VPN à l’échelle de l’appareil pour être actifs simultanément. Même si plusieurs profils VPN peuvent exister sur l’appareil, un seul VPN peut être actif à la fois.


## <a name="battery-consumption"></a>Consommation de batterie

L’utilisation de la batterie par une application est calculée par Apple en fonction d’une multitude de facteurs, notamment l’utilisation du processeur et du réseau. Microsoft Defender pour le point de terminaison utilise un VPN local/loop-back en arrière-plan pour vérifier le trafic web des sites web ou connexions malveillants. Les paquets réseau de n’importe quelle application sont vérifiés et l’utilisation de la batterie de Microsoft Defender for Endpoint est calculée de manière incorrecte. Cela donne une fausse impression à l’utilisateur. La consommation réelle de batterie de Microsoft Defender pour le point de terminaison est inférieure à ce qui est affiché sur la page Paramètres batterie sur l’appareil. Cette opération est basée sur des tests effectués sur l’application Microsoft Defender for Endpoint pour comprendre la consommation de batterie.

En outre, le VPN utilisé est un VPN local et, contrairement à un VPN traditionnel, le trafic réseau n’est pas envoyé en dehors de l’appareil.

## <a name="data-usage"></a>Utilisation des données

Microsoft Defender pour le point de terminaison utilise un VPN local/loopback pour vérifier le trafic web des sites web ou connexions malveillants. Pour cette raison, Apple compte de manière incorrecte l’utilisation des données dans Microsoft Defender for Endpoint. L’utilisation réelle des données par Microsoft Defender pour le point de terminaison n’est pas significative et beaucoup moins importante que ce qui est indiqué sur la Paramètres d’utilisation des données sur l’appareil.

## <a name="report-unsafe-site"></a>Signaler un site non sécurisé

Les sites web de hameçonnage usurpent l’identité de sites web dignes de confiance dans le but d’obtenir vos informations personnelles ou financières. Consultez la page [Fournir des commentaires sur la protection](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) du réseau pour signaler un site web qui pourrait être un site de hameçonnage.

## <a name="malicious-site-detected"></a>Site malveillant détecté

Microsoft Defender pour le point de terminaison vous protège contre le hameçonnage ou d’autres attaques basées sur le web. Si un site malveillant est détecté, la connexion est bloquée et une alerte est envoyée au portail centre de sécurité de l’organisation. L’alerte inclut le nom de domaine de la connexion, l’adresse IP distante et les détails du périphérique.

En outre, une notification s’affiche sur l’appareil iOS. Appuyer sur la notification ouvre l’écran suivant pour que l’utilisateur examine les détails.

> [!div class="mx-imgBorder"]
> ![Image du site signalée comme notification non sûre](images/ios-phish-alert.png)

## <a name="data-and-privacy"></a>Données et confidentialité

Pour plus d’informations sur les données collectées et la confidentialité, voir Informations sur la confidentialité [- Microsoft Defender pour endpoint sur iOS](ios-privacy.md).

