---
title: Résoudre les problèmes et trouver des réponses aux questions relatives à Microsoft Defender pour point de terminaison sur iOS
description: Résolution des problèmes et FAQ - Microsoft Defender pour point de terminaison sur iOS
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, ios, résolution des problèmes, faq, procédure
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
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: d6cf7a9e2d19f694711b565f786f7c0560b962f0
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67522100"
---
# <a name="troubleshoot-issues-and-find-answers-to-faqs-on-microsoft-defender-for-endpoint-on-ios"></a>Résoudre les problèmes et trouver des réponses aux questions fréquentes sur Microsoft Defender pour point de terminaison sur iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique fournit des informations de dépannage pour vous aider à résoudre les problèmes qui peuvent survenir lorsque vous utilisez Microsoft Defender pour point de terminaison sur iOS.

> [!NOTE]
> Defender pour point de terminaison sur iOS utiliserait un VPN pour fournir la fonctionnalité De protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/auto-bouclage qui ne prend pas le trafic en dehors de l’appareil.

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>Les applications ne fonctionnent pas lorsque le VPN est activé
Certaines applications cessent de fonctionner lorsqu’un VPN actif est détecté. Vous pouvez désactiver le VPN pendant que vous utilisez de telles applications.

Par défaut, Defender pour point de terminaison sur iOS inclut et active la fonctionnalité de protection web. La [protection web](web-protection-overview.md) permet de sécuriser les appareils contre les menaces web et de protéger les utilisateurs contre les attaques par hameçonnage. Defender pour point de terminaison sur iOS utilise un VPN pour fournir cette protection. Notez qu’il s’agit d’un VPN local et, contrairement au VPN traditionnel, le trafic réseau n’est pas envoyé en dehors de l’appareil.

Bien qu’il soit activé par défaut, il peut arriver que vous deviez désactiver le VPN. Par exemple, vous souhaitez exécuter des applications qui ne fonctionnent pas lorsqu’un VPN est configuré. Dans ce cas, vous pouvez choisir de désactiver le VPN directement à partir de l’application Defender pour point de terminaison ou en procédant comme suit :

1. Sur votre appareil iOS, **ouvrez** l’application Paramètres, cliquez ou appuyez sur **Général** , puis **sur VPN**.
1. Cliquez ou appuyez sur le bouton « i » pour Microsoft Defender pour point de terminaison.
1. Désactivez **La connexion à la demande** pour désactiver le VPN.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="Option Se connecter à la demande" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> La protection web ne sera pas disponible lorsque le VPN est désactivé. Pour réactiver la protection web, ouvrez l’application Microsoft Defender pour point de terminaison sur l’appareil et activez la protection web.

## <a name="coexistence-with-multiple-vpn-profiles"></a>Coexistence avec plusieurs profils VPN

Apple iOS ne prend pas en charge plusieurs VPN à **l’échelle de l’appareil** pour être actifs simultanément. Bien que plusieurs profils VPN puissent exister sur l’appareil, un seul VPN peut être actif à la fois. Si vous devez utiliser un autre VPN sur l’appareil, vous pouvez désactiver Defender pour point de terminaison VPN pendant que vous utilisez l’autre VPN.

## <a name="battery-consumption"></a>Consommation de batterie

Afin de vous protéger en permanence contre les menaces web, Microsoft Defender pour point de terminaison doit s’exécuter en arrière-plan à tout moment. Cela peut entraîner une légère augmentation de la consommation globale de batterie de votre appareil. Si vous constatez un drainage important de la batterie, [envoyez-nous vos commentaires](ios-troubleshoot.md#send-in-app-feedback) et nous examinerons.

De plus, dans l’application Paramètres, iOS affiche uniquement l’utilisation de la batterie des applications visibles par l’utilisateur pendant une durée spécifique. L’utilisation de la batterie par les applications affichées à l’écran est uniquement pendant cette durée et est calculée par iOS en fonction d’une multitude de facteurs, notamment l’utilisation du processeur et du réseau. Microsoft Defender pour point de terminaison utilise un VPN local/en boucle en arrière-plan pour vérifier le trafic web des sites web malveillants ou des connexions. Les paquets réseau de n’importe quelle application passent par cette vérification, ce qui entraîne le calcul incorrect de l’utilisation de la batterie de Microsoft Defender pour point de terminaison. La consommation réelle de batterie de Microsoft Defender pour point de terminaison est inférieure à celle affichée sur la page Paramètres de la batterie sur l’appareil.

Notez que le VPN utilisé est un VPN local et, contrairement à un VPN traditionnel, le trafic réseau n’est pas envoyé en dehors de l’appareil.

## <a name="data-usage"></a>Utilisation des données

Microsoft Defender pour point de terminaison utilise un VPN local/de bouclage pour vérifier le trafic web des sites web malveillants ou des connexions. Pour cette raison, Microsoft Defender pour point de terminaison l’utilisation des données peut être incorrectement comptabilisée. Nous avons également observé que si l’appareil se trouve uniquement sur le réseau cellulaire, l’utilisation des données signalée par le fournisseur de services est très proche de la consommation réelle alors que dans l’application Paramètres, les nombres peuvent être inexacts.

Nous avons également des observations similaires avec d’autres services VPN.

En outre, il est essentiel que Microsoft Defender pour point de terminaison soient à jour avec nos services principaux afin de fournir une meilleure protection.

## <a name="report-unsafe-site"></a>Signaler un site non sécurisé

Les sites web de hameçonnage empruntent l’identité de sites web dignes de confiance pour obtenir vos informations personnelles ou financières. Visitez la page [Fournir des commentaires sur la protection réseau](https://www.microsoft.com/wdsi/support/report-unsafe-site) pour signaler un site web qui pourrait être un site de hameçonnage.

## <a name="malicious-site-detected"></a>Site malveillant détecté

Microsoft Defender pour point de terminaison vous protège contre le hameçonnage ou d’autres attaques web. Si un site malveillant est détecté, la connexion est bloquée et une alerte est envoyée au portail Microsoft 365 Defender de l’organisation. L’alerte inclut le nom de domaine de la connexion, l’adresse IP distante et les détails de l’appareil.

En outre, une notification s’affiche sur l’appareil iOS. L’appui sur la notification ouvre l’écran suivant pour que l’utilisateur passe en revue les détails.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/ios-phish-alert.png" alt-text="Le site signalé comme notification non sécurisée" lightbox="images/ios-phish-alert.png":::

## <a name="device-not-seen-on-the-defender-for-endpoint-console-after-onboarding"></a>Appareil introuvable sur la console Defender pour point de terminaison après l’intégration

Après l’intégration, l’affichage de l’appareil dans l’inventaire des appareils dans la console de sécurité Defender pour point de terminaison prend quelques heures. Vérifiez également que l’appareil est correctement inscrit auprès d’Azure Active Directory et que l’appareil dispose d’une connectivité Internet. Pour réussir l’intégration, l’appareil doit être inscrit via Microsoft Authenticator ou Portail d'entreprise Intune et l’utilisateur doit se connecter à l’aide du même compte avec lequel l’appareil est inscrit auprès d’Azure AD.

> [!NOTE]
> Parfois, le nom de l’appareil n’est pas cohérent avec celui de la console Microsoft Endpoint Manager (Intune). Le nom de l’appareil dans la console Defender pour point de terminaison est au format <username_iPhone/iPad model>. Vous pouvez également utiliser l’ID d’appareil Azure AD pour identifier l’appareil dans la console Defender pour point de terminaison.

## <a name="data-and-privacy"></a>Données et confidentialité

Pour plus d’informations sur les données collectées et la confidentialité, consultez [Informations de confidentialité - Microsoft Defender pour point de terminaison sur iOS](ios-privacy.md).

## <a name="connectivity-issue-on-cellular-network"></a>Problème de connectivité sur le réseau cellulaire

Si vous rencontrez des problèmes de connectivité Internet sur le réseau cellulaire, vérifiez si Microsoft Defender pour point de terminaison dispose de données cellulaires activées : Ouvrez l’application Paramètres > MS Defender > assurez-vous que « Données cellulaires » est activé pour MS Defender.

Si vous rencontrez toujours des problèmes de connectivité, vérifiez si l’activation/désactivation du mode Avion permet de résoudre le problème. Si le problème persiste, [envoyez-nous les journaux](ios-troubleshoot.md#send-in-app-feedback).

## <a name="issues-on-supervised-devices-with-content-filter-profile-installed"></a>Problèmes sur les appareils supervisés avec le profil de filtre de contenu installé

Il existe un problème sur les appareils supervisés avec le filtre de contenu Defender pour point de terminaison installé. Si vous observez une lenteur ou une latence dans la connectivité Internet sur ces appareils, désinstallez ou supprimez le profil de filtre de contenu de l’appareil. Nous nous efforçons de résoudre ce problème et nous allons mettre à jour cet endroit une fois que nous aurons une solution. 

## <a name="issues-during-app-updates-from-the-app-store"></a>Problèmes lors des mises à jour de l’application à partir de l’App Store

Si vous observez des problèmes lorsque l’application est mise à jour via l’App Store (mises à jour automatiques ou mises à jour manuelles), vous devrez peut-être redémarrer l’appareil. Si cela ne résout pas le problème, vous pouvez désactiver le VPN Defender et effectuer la mise à jour de l’application. Vous pouvez également fournir des commentaires dans l’application pour signaler ce problème.

## <a name="send-in-app-feedback"></a>Envoyer des commentaires dans l’application

Si un utilisateur rencontre un problème qui n’est pas déjà résolu dans les sections ci-dessus ou qui ne peut pas être résolu à l’aide des étapes répertoriées, l’utilisateur peut fournir des commentaires dans l’application ainsi que des données de diagnostic. Notre équipe examinera ensuite les journaux pour fournir la solution appropriée. Les utilisateurs peuvent utiliser les étapes suivantes pour envoyer des commentaires :

- Ouvrez l’application MSDefender sur l’appareil iOS/iPadOS.
- Appuyez sur Menu (icône de profil) dans le coin supérieur gauche.
- Appuyez sur **Envoyer des commentaires**.
- Choisissez parmi les options données. Pour signaler un problème, sélectionnez **Je n’aime pas quelque chose**.
- Fournissez des détails sur le problème auquel vous êtes confronté et vérifiez **envoyer des données de diagnostic**. Nous vous recommandons d’inclure votre adresse e-mail afin que l’équipe puisse vous contacter pour obtenir une solution ou un suivi.
- Appuyez sur **Envoyer** pour envoyer les commentaires.
