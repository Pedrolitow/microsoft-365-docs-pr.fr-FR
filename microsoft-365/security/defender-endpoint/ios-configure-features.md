---
title: Configurer Microsoft Defender pour le point de terminaison sur les fonctionnalités iOS
description: Décrit comment déployer Microsoft Defender pour endpoint sur les fonctionnalités iOS
keywords: microsoft, defender, atp, ios, configurer, fonctionnalités, ios
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
ms.openlocfilehash: f5f7345f92b3ac76aa647a9caed63e5684be9c30
ms.sourcegitcommit: 13ce4b31303a1a21ca53700a54bcf8d91ad2f8c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2021
ms.locfileid: "51903309"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>Configurer Microsoft Defender pour endpoint sur les fonctionnalités iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l'expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

> [!NOTE]
> Defender pour le point de terminaison pour iOS utiliserait un VPN pour fournir la fonctionnalité de protection web. Il ne s'agit pas d'un VPN normal et d'un VPN local/en boucle autonome qui ne prend pas le trafic en dehors de l'appareil.

## <a name="conditional-access-with-defender-for-endpoint-for-ios"></a>Accès conditionnel avec Defender pour point de terminaison pour iOS  
Microsoft Defender pour endpoint sur iOS avec Microsoft Intune et Azure Active Directory permet d'appliquer des stratégies de conformité des appareils et d'accès conditionnel en fonction des niveaux de risque de l'appareil. Defender pour point de terminaison est une solution de défense contre les menaces mobiles (MTD) que vous pouvez déployer pour tirer parti de cette fonctionnalité via Intune.

Pour plus d'informations sur la façon de configurer l'accès conditionnel avec Defender pour Endpoint pour iOS, voir [Defender pour Endpoint et Intune.](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection)

## <a name="web-protection-and-vpn"></a>Protection web et VPN

Par défaut, Defender pour le point de terminaison pour iOS inclut et active la fonctionnalité de protection web. [La protection web permet](web-protection-overview.md) de sécuriser les appareils contre les menaces web et de protéger les utilisateurs contre les attaques par hameçonnage. Defender pour le point de terminaison pour iOS utilise un VPN pour fournir cette protection. Notez qu'il s'agit d'un VPN local et, contrairement au VPN traditionnel, le trafic réseau n'est pas envoyé à l'extérieur de l'appareil.

Bien qu'il soit activé par défaut, il se peut que vous de soyez dans certains cas dans l'obligation de désactiver le VPN. Par exemple, vous souhaitez exécuter certaines applications qui ne fonctionnent pas lorsqu'un VPN est configuré. Dans ce cas, vous pouvez choisir de désactiver le VPN de l'application sur l'appareil en suivant les étapes ci-dessous :

1. Sur votre appareil iOS, ouvrez l'application **Paramètres,** cliquez ou appuyez sur **Général,** puis **sur VPN.**
1. Cliquez ou appuyez sur le bouton « i » de Microsoft Defender pour le point de terminaison.
1. Désactivez la connexion **à la demande** pour désactiver le VPN.

    > [!div class="mx-imgBorder"]
    > ![Connexion de la connexion VPN à la demande](images/ios-vpn-config.png)

> [!NOTE]
> La protection web n'est pas disponible lorsque le VPN est désactivé. Pour activer à nouveau la Protection Web, ouvrez l'application Microsoft Defender pour point de terminaison sur l'appareil, puis cliquez ou appuyez sur **Démarrer le VPN.**

## <a name="co-existence-of-multiple-vpn-profiles"></a>Coexistence de plusieurs profils VPN

Apple iOS ne prend pas en charge plusieurs VPN à l'échelle de l'appareil pour être actifs simultanément. Même si plusieurs profils VPN peuvent exister sur l'appareil, un seul VPN peut être actif à la fois.


## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Configurer la stratégie de conformité contre les appareils jailbreakés

Pour protéger les données d'entreprise contre l'accès sur les appareils iOS jailbreakés, nous vous recommandons de configurer la stratégie de conformité suivante sur Intune.

> [!NOTE]
> Pour l'instant, Microsoft Defender for Endpoint sur iOS ne fournit pas de protection contre les scénarios de jailbreak. S'il est utilisé sur un appareil jailbreaké, dans des scénarios spécifiques, les données utilisées par l'application telles que votre ID de messagerie d'entreprise et votre image de profil d'entreprise (si disponible) peuvent être exposées localement.

Suivez les étapes ci-dessous pour créer une stratégie de conformité contre les appareils jailbreakés.

1. Dans [le Centre d'administration Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)allez **aux** stratégies de conformité  ->  **des appareils**  ->  **Créer une stratégie.** Sélectionnez « iOS/iPadOS » comme plateforme, puis cliquez sur **Créer.**

    > [!div class="mx-imgBorder"]
    > ![Créer une stratégie](images/ios-jb-policy.png)

2. Spécifiez un nom de stratégie, par exemple « Stratégie de conformité pour jailbreak ».
3. Dans la page paramètres de conformité, cliquez  pour développer la **section** État de l'appareil, puis cliquez sur Bloquer pour les **appareils jailbreakés.**

    > [!div class="mx-imgBorder"]
    > ![Paramètres de stratégie](images/ios-jb-settings.png)

4. Dans la *section Action pour non-conformité,* sélectionnez les actions en conformité avec vos besoins, puis sélectionnez **Suivant**.

    > [!div class="mx-imgBorder"]
    > ![Actions de stratégie](images/ios-jb-actions.png)

5. Dans la section *Affectations,* sélectionnez les groupes d'utilisateurs que vous souhaitez inclure pour cette stratégie, puis sélectionnez **Suivant.**
6. Dans la section **Révision+Créer,** vérifiez que toutes les informations entrées sont correctes, puis sélectionnez **Créer.**

## <a name="configure-custom-indicators"></a>Configurer des indicateurs personnalisés

Defender pour le point de terminaison pour iOS permet aux administrateurs de configurer également des indicateurs personnalisés sur les appareils iOS. Pour plus d'informations sur la configuration des indicateurs personnalisés, voir [Gérer les indicateurs.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/manage-indicators)

> [!NOTE]
> Defender pour le point de terminaison pour iOS prend en charge la création d'indicateurs personnalisés uniquement pour les adresses IP et les URL/domaines.

## <a name="report-unsafe-site"></a>Signaler un site non sécurisé

Les sites web de hameçonnage usurpent l'identité de sites web dignes de confiance dans le but d'obtenir vos informations personnelles ou financières. Consultez la page [Fournir des commentaires sur la protection](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) du réseau si vous souhaitez signaler un site web qui pourrait être un site de hameçonnage.

## <a name="battery-consumption-issues-on-ios-when-microsoft-defender-for-endpoint-is-installed"></a>Problèmes de consommation de batterie sur iOS lors de l'installation de Microsoft Defender for Endpoint

L'utilisation de la batterie par une application est calculée par Apple en fonction d'une multitude de facteurs, notamment l'utilisation du processeur et du réseau. Microsoft Defender pour le point de terminaison utilise un VPN local/loop-back en arrière-plan pour vérifier le trafic web des sites web ou connexions malveillants. Les paquets réseau de n'importe quelle application sont vérifiés et l'utilisation de la batterie de Microsoft Defender for Endpoint est calculée de manière incorrecte. Cela donne une fausse impression à l'utilisateur. La consommation réelle de batterie de Microsoft Defender pour le point de terminaison est inférieure à ce qui est affiché dans la page Paramètres de la batterie sur l'appareil. Cette opération est basée sur des tests effectués sur l'application Microsoft Defender for Endpoint pour comprendre la consommation de batterie.

En outre, le VPN utilisé est un VPN local et contrairement aux VPN traditionnels, le trafic réseau n'est pas envoyé en dehors de l'appareil.
