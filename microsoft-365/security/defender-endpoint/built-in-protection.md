---
title: La protection intégrée permet de se protéger contre les rançongiciels
description: Découvrez comment la protection intégrée protège contre les rançongiciels dans le cadre de Microsoft Defender pour point de terminaison.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 10/20/2022
ms.service: microsoft-365-security
ms.subservice: mde
ms.localizationpriority: medium
ms.collection:
- m365-security
- tier2
ms.custom: ''
ms.reviewer: joshbregman
f1.keywords: NOCSH
ms.openlocfilehash: 25074c0540f00d9edf4b508a271e47c3777792e1
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660662"
---
# <a name="built-in-protection-helps-guard-against-ransomware"></a>La protection intégrée permet de se protéger contre les rançongiciels

[Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) permet de prévenir, détecter, examiner et répondre aux menaces avancées, telles que les attaques par ransomware. Les fonctionnalités de protection et [de réduction de la surface d’attaque](overview-attack-surface-reduction.md) [de nouvelle génération](next-generation-protection.md) dans Defender pour point de terminaison ont été conçues pour intercepter les menaces émergentes. Pour que la meilleure protection contre les rançongiciels et autres cybermenaces soit en place, certains paramètres doivent être configurés. La protection intégrée peut vous aider en vous fournissant des paramètres par défaut pour une meilleure protection.

> [!TIP]
> **Vous n’avez pas besoin d’attendre que la protection intégrée vienne à vous** ! Vous pouvez maintenant protéger les appareils de votre organisation en configurant ces fonctionnalités :
> - [Activer la protection cloud](why-cloud-protection-should-be-on-mdav.md)
> - [Activer la protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md)
> - [Définir des règles de réduction de la surface d’attaque standard en mode bloc](attack-surface-reduction-rules-deployment.md)
> - [Activer la protection réseau en mode bloc](enable-network-protection.md)

## <a name="what-is-built-in-protection-and-how-does-it-work"></a>Qu’est-ce que la protection intégrée et comment fonctionne-t-elle ?

La protection intégrée est un ensemble de paramètres par défaut qui sont déployés pour vous assurer que vos appareils sont protégés. Ces paramètres par défaut sont conçus pour protéger les appareils contre les rançongiciels et d’autres menaces. Initialement, la protection intégrée inclut l’activation de la [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) pour votre locataire, avec d’autres paramètres par défaut bientôt disponibles. Pour plus d’informations, consultez le billet de blog tech community, [La protection contre les falsifications sera activée pour tous les clients d’entreprise](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/tamper-protection-will-be-turned-on-for-all-enterprise-customers/ba-p/3616478).

| Phase | Action exécutée |
|:---|:---|
| La protection intégrée est en cours de déploiement | Les clients reçoivent une [notification](#what-does-the-notification-look-like) indiquant que la protection intégrée est à venir. Si elle n’est pas déjà configurée, la protection contre les falsifications est activée pour les clients qui ont Defender pour point de terminaison Plan 2 ou Microsoft 365 E5. |
| La protection intégrée devient disponible pour votre locataire | Vous serez [informé](#what-does-the-notification-look-like) que votre locataire est sur le point de recevoir une protection intégrée et que la protection contre les falsifications sera activée (si elle n’est pas déjà configurée). |
| La protection intégrée arrive | La protection contre les falsifications sera activée pour votre locataire et appliquée aux appareils Windows de votre organisation. Vous pouvez [désactiver](#can-i-opt-out) ou [modifier vos paramètres de protection intégrés](#can-i-change-built-in-protection-settings). |
| Une fois la protection intégrée arrivée | Chaque fois que de nouveaux appareils sont intégrés à Defender pour point de terminaison, les paramètres de protection intégrés sont appliqués à tous les nouveaux appareils exécutant Windows. Vous pouvez toujours [modifier vos paramètres de protection intégrés](#can-i-change-built-in-protection-settings). |

> [!NOTE]
> La protection intégrée définit les valeurs par défaut pour les appareils Windows. Si les paramètres de sécurité des points de terminaison changent, par exemple via des bases de référence ou des stratégies dans [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), ces paramètres remplacent les paramètres de protection intégrés.  

## <a name="what-does-the-notification-look-like"></a>À quoi ressemble la notification ?

Vous pouvez vous attendre à recevoir deux types de notifications :

- Publication du centre de messages indiquant que la protection intégrée est bientôt disponible ; Et 
- Bannière dans le portail Microsoft 365 Defender qui ressemble à l’image suivante :

   :::image type="content" source="media/bip-notification-m365defender.png" alt-text="Capture d’écran montrant la bannière jaune mettant en évidence la protection intégrée dans Microsoft 365 Defender portail.":::

Votre notification vous indiquera quand la protection intégrée sera disponible et quand la protection contre les falsifications sera activée (si elle n’est pas déjà configurée) pour votre locataire.

## <a name="can-i-opt-out"></a>Puis-je refuser ?

Vous pouvez désactiver la protection intégrée en spécifiant vos propres paramètres de sécurité. Par exemple, si vous préférez ne pas activer automatiquement la protection contre les falsifications pour votre locataire, vous pouvez le désactiver explicitement.

> [!NOTE]
> **Nous vous déconseillons de désactiver la protection contre les falsifications**. La protection contre les falsifications vous offre une meilleure protection contre les rançongiciels.
> Vous devez être administrateur général ou administrateur de la sécurité pour effectuer la procédure suivante.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Accédez à **Paramètres Points** > **de terminaison****Fonctionnalités avancées** > .

3. Définissez **Protection contre les falsifications** **sur Activé** (s’il n’est pas déjà activé), puis sélectionnez **Enregistrer les préférences**. *Ne quittez pas encore cette page*.

4. Définissez **Protection contre les falsifications** sur **Désactivé**, puis sélectionnez **Enregistrer les préférences**.

## <a name="can-i-change-built-in-protection-settings"></a>Puis-je modifier les paramètres de protection intégrés ?

La protection intégrée est un ensemble de paramètres par défaut. Vous n’êtes pas obligé de conserver ces paramètres par défaut en place. Vous pouvez toujours modifier vos paramètres en fonction des besoins de votre entreprise. Le tableau suivant répertorie les tâches que votre équipe de sécurité peut effectuer, ainsi que des liens pour en savoir plus. 

| Tâche | Description |
|:---|:---|
| Déterminer si la protection contre les falsifications est activée | 1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.<br/>2. Accédez à **Paramètres Points** > **de terminaison****Fonctionnalités avancées** > **Protection contre les falsifications** > .  |
| Gérer la protection contre les falsifications à l’échelle du locataire à l’aide du portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.<br/>2. Accédez à **Paramètres Points** > **de terminaison****Fonctionnalités avancées** > .<br/>3. Définissez **Protection contre les falsifications** **sur Activé** (*recommandé*) ou **Désactivé**.<br/>4. Sélectionnez **Enregistrer les préférences**.<br/><br/>Consultez [Gérer la protection contre les falsifications pour votre organisation à l’aide Microsoft 365 Defender portail](manage-tamper-protection-microsoft-365-defender.md). |
| Définir des paramètres de protection contre les falsifications pour certains appareils, mais pas tous | Utilisez des stratégies et des profils de sécurité de point de terminaison qui sont appliqués à des appareils spécifiques. Consultez les articles suivants :<br/>- [Gérer la protection contre les falsifications à l’aide de Microsoft Endpoint Manager](manage-tamper-protection-microsoft-endpoint-manager.md)<br/>- [Gérer la protection contre les falsifications à l’aide de l’attachement de locataire avec Configuration Manager, version 2006](manage-tamper-protection-configuration-manager.md)|
| Activer ou désactiver la protection contre les falsifications sur un appareil individuel | 1. Sur votre appareil Windows, sélectionnez **Démarrer**, puis commencez à taper *Sécurité*.<br/>2. Dans les résultats de la recherche, sélectionnez **Sécurité Windows**.<br/>3. Sélectionnez **Virus & threat protection** > **Antivirus & Threat Protection**.<br/>4. Définissez **Protection contre les falsifications** **sur Activé** (*recommandé*) ou **Désactivé**. <br/><br/>Si l’appareil est intégré à Defender pour point de terminaison ou s’il est géré dans le Centre d’administration Microsoft Endpoint Manager, ces paramètres remplacent les paramètres utilisateur sur l’appareil individuel. <br/><br/>Consultez [Gérer la protection contre les falsifications sur un appareil individuel](manage-tamper-protection-individual-device.md). |
| Désactiver temporairement la protection contre les falsifications sur un appareil à des fins de résolution des problèmes | Consultez les articles suivants :<br/>- [Prise en main du mode résolution des problèmes dans Microsoft Defender pour point de terminaison](enable-troubleshooting-mode.md)<br/>- [Scénarios de mode de résolution des problèmes dans Microsoft Defender pour point de terminaison](troubleshooting-mode-scenarios.md) |

## <a name="see-also"></a>Voir aussi

- [Blog de la communauté technique : La protection contre les falsifications sera activée pour tous les clients d’entreprise](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/tamper-protection-will-be-turned-on-for-all-enterprise-customers/ba-p/3616478)
- [Protéger les paramètres de sécurité avec la protection contre la falsifiation](prevent-changes-to-security-settings-with-tamper-protection.md)
- [Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security)
- [Configuration de Microsoft Defender pour point de terminaison dans Intune](/mem/intune/protect/advanced-threat-protection-configure)
- [Gérer les Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Réponse aux attaques par rançongiciels](../defender/playbook-responding-ransomware-m365-defender.md)
