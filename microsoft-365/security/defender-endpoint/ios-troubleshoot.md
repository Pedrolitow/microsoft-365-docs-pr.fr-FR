---
title: Résoudre les problèmes et trouver des réponses sur les QUESTIONS liées à Microsoft Defender for Endpoint sur iOS
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
ms.openlocfilehash: 71ae504caa9cea6b7fe2d10437271140986f9f38e1760b81a9019e3bd22ddaba
ms.sourcegitcommit: 9410944dab4a34c38ee420e66b14c58ca037f31c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2021
ms.locfileid: "57803439"
---
# <a name="troubleshoot-issues-and-find-answers-to-faqs-on-microsoft-defender-for-endpoint-on-ios"></a>Résoudre les problèmes et trouver des réponses aux QUESTIONS sur Microsoft Defender pour le point de terminaison sur iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique fournit des informations de dépannage pour vous aider à résoudre les problèmes qui peuvent survenir lorsque vous utilisez Microsoft Defender pour Endpoint sur iOS.



> [!NOTE]
> Defender pour le point de terminaison sur iOS utiliserait un VPN pour fournir la fonctionnalité de protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/en boucle autonome qui ne prend pas le trafic en dehors de l’appareil.

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>Les applications ne fonctionnent pas lorsque le VPN est allumé
Certaines applications cessent de fonctionner lorsqu’un VPN actif est détecté. Vous pouvez désactiver le VPN pendant la durée d’utilisation de ces applications. 

Par défaut, Defender pour le point de terminaison sur iOS inclut et active la fonctionnalité de protection web. [La protection web permet](web-protection-overview.md) de sécuriser les appareils contre les menaces web et de protéger les utilisateurs contre les attaques par hameçonnage. Defender pour le point de terminaison sur iOS utilise un VPN pour fournir cette protection. Notez qu’il s’agit d’un VPN local et, contrairement au VPN traditionnel, le trafic réseau n’est pas envoyé à l’extérieur de l’appareil.

Bien qu’il soit activé par défaut, il se peut que vous de soyez dans certains cas dans l’obligation de désactiver le VPN. Par exemple, vous souhaitez exécuter certaines applications qui ne fonctionnent pas lorsqu’un VPN est configuré. Dans ce cas, vous pouvez choisir de désactiver le VPN de l’application sur l’appareil en suivant les étapes ci-dessous :

1. Sur votre appareil iOS, ouvrez **l’application Paramètres,** cliquez ou appuyez sur **Général,** puis **sur VPN.**
1. Cliquez ou appuyez sur le bouton « i » de Microsoft Defender pour le point de terminaison.
1. Désactivez la **Connecter à la demande** pour désactiver le VPN.

    > [!div class="mx-imgBorder"]
    > ![Connexion de la connexion VPN à la demande](images/ios-vpn-config.png)

> [!NOTE]
> La protection web n’est pas disponible lorsque le VPN est désactivé. Pour activer à nouveau la Protection Web, ouvrez l’application Microsoft Defender pour point de terminaison sur l’appareil, puis cliquez ou appuyez sur **Démarrer le VPN.**

## <a name="co-existence-with-multiple-vpn-profiles"></a>Coexistence avec plusieurs profils VPN

Apple iOS ne prend pas en **charge** plusieurs VPN à l’échelle de l’appareil pour être actifs simultanément. Alors que plusieurs profils VPN peuvent exister sur l’appareil, un seul VPN peut être actif à la fois.

Le VPN Microsoft Defender pour point de terminaison peut co-exister avec d’autres VPN configurés comme par application ou *« Personnel*». 

## <a name="battery-consumption"></a>Consommation de batterie

Dans l’Paramètres, iOS affiche uniquement l’utilisation de la batterie des applications visibles par l’utilisateur pendant une durée spécifique. L’utilisation de la batterie par les applications affichées à l’écran ne dure que pendant cette durée et est calculée par iOS en fonction d’une multitude de facteurs, notamment l’utilisation du processeur et du réseau. Microsoft Defender pour le point de terminaison utilise un VPN local/de bouc-back en arrière-plan pour vérifier le trafic web des sites web ou connexions malveillants. Les paquets réseau de n’importe quelle application sont vérifiés et l’utilisation de la batterie de Microsoft Defender for Endpoint est calculée de manière incorrecte. La consommation réelle de batterie de Microsoft Defender pour le point de terminaison est beaucoup moins élevée que celle affichée sur la page Paramètres batterie sur l’appareil.

En moyenne, l’utilisation quotidienne de la batterie par Microsoft Defender pour le point de terminaison en cours d’exécution en arrière-plan représente environ **8,81 %** de la batterie globale consommée au cours de cette journée. Cette mesure est signalée par Apple en fonction de l’utilisation réelle de Microsoft Defender pour Endpoint sur les appareils des utilisateurs finaux et, pour des raisons mentionnées ci-dessus, peut également être liée à d’autres applications qui ont une activité réseau.

En outre, le VPN utilisé est un VPN local et, contrairement à un VPN traditionnel, le trafic réseau n’est pas envoyé à l’extérieur de l’appareil.

## <a name="data-usage"></a>Utilisation des données

Microsoft Defender pour le point de terminaison utilise un VPN local/loopback pour vérifier le trafic web des sites web ou des connexions malveillants. Pour cette raison, l’utilisation des données de Microsoft Defender pour les points de terminaison peut être incorrectement expliquée. Nous avons également observé que si l’appareil est uniquement sur le réseau cellulaire, l’utilisation des données signalée par le fournisseur de services est très proche de la consommation réelle alors que dans l’application Paramètres, Apple affiche environ 1,5x à 2x de données réelles consommées.

Nous avons également des observations similaires avec d’autres services VPN et l’avons signalé à Apple.

En outre, il est essentiel que Microsoft Defender pour Point de terminaison soit à jour avec nos services de système principal afin de fournir une meilleure protection. Toutefois, nous travaillons sur l’optimisation de l’utilisation des données par Microsoft Defender pour endpoint.

## <a name="report-unsafe-site"></a>Signaler un site non sécurisé

Les sites web de hameçonnage usurpent l’identité de sites web dignes de confiance dans le but d’obtenir vos informations personnelles ou financières. Consultez la page [Fournir des commentaires sur la protection](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) du réseau pour signaler un site web qui pourrait être un site de hameçonnage.

## <a name="malicious-site-detected"></a>Site malveillant détecté

Microsoft Defender pour le point de terminaison vous protège contre le hameçonnage ou d’autres attaques basées sur le web. Si un site malveillant est détecté, la connexion est bloquée et une alerte est envoyée au portail centre de sécurité de l’organisation. L’alerte inclut le nom de domaine de la connexion, l’adresse IP distante et les détails du périphérique.

En outre, une notification s’affiche sur l’appareil iOS. Appuyer sur la notification ouvre l’écran suivant pour que l’utilisateur examine les détails.

> [!div class="mx-imgBorder"]
> ![Image du site signalée comme notification non sûre](images/ios-phish-alert.png)

## <a name="device-not-seen-on-the-defender-for-endpoint-console-after-onboarding"></a>Appareil non visible sur la console Defender for Endpoint après l’intégration.

Après l’intégration, l’appareil peut s’afficher dans l’inventaire des appareils dans la console de sécurité Defender for Endpoint. Assurez-vous également que l’appareil est correctement inscrit auprès Azure Active Directory et que l’appareil dispose d’une connectivité Internet. Pour que l’intégration réussisse, l’appareil doit être inscrit via Microsoft Authenticator ou Portail d’entreprise Intune et l’utilisateur doit se connecter à l’aide du même compte avec lequel l’appareil est inscrit auprès d’Azure AD.

## <a name="data-and-privacy"></a>Données et confidentialité

Pour plus d’informations sur les données collectées et la confidentialité, voir Informations sur la confidentialité - Microsoft Defender pour point de [terminaison sur iOS](ios-privacy.md).

