---
title: Forum aux questions sur la protection contre les falsifications
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Forum aux questions sur la configuration de la protection contre les falsifications.
keywords: programmes malveillants, defender, antivirus, protection contre les falsifications
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom:
- nextgen
- admindeeplinkDEFENDER
ms.subservice: mde
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: f316687fc0a894cc72578d8e556dc1e1ab322fed
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68180021"
---
# <a name="frequently-asked-questions-on-tamper-protection"></a>Forum aux questions sur la protection contre les falsifications

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

## <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>Sur quelles versions de Windows puis-je configurer la « protection contre les falsifications » ?

- Windows 11
- Multisession Windows 11 Entreprise
- Windows 10 système d’exploitation [1709](/lifecycle/announcements/revised-end-of-service-windows-10-1709), [1803](/lifecycle/announcements/windows-server-1803-end-of-servicing), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) ou version ultérieure avec [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint).
- Windows 10 Entreprise à sessions multiples
  
Si vous utilisez Configuration Manager, version 2006, avec attachement de locataire, la protection contre les falsifications peut être étendue à Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 et Windows Server 2022. Voir [Attachement de locataire : Créer et déployer une stratégie antivirus de sécurité de point de terminaison à partir du centre d’administration (préversion).](/mem/configmgr/tenant-attach/deploy-antivirus-policy)

## <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>La protection contre les falsifications affecte-t-elle l’inscription d’antivirus non-Microsoft dans l’application Sécurité Windows ?

Non. Les offres antivirus non Microsoft continueront de s’inscrire auprès de l’application Sécurité Windows.

## <a name="what-happens-if-microsoft-defender-antivirus-isnt-active-on-a-device"></a>Que se passe-t-il si Microsoft Defender Antivirus n’est pas actif sur un appareil ?

Les appareils intégrés à Microsoft Defender pour point de terminaison auront Microsoft Defender Antivirus s’exécutant en mode passif. Dans ce cas, la protection contre les falsifications continuera à protéger le service et ses fonctionnalités.

## <a name="how-do-i-turn-tamper-protection-on-or-off"></a>Comment faire activer ou désactiver la protection contre les falsifications ?

Si vous êtes un utilisateur domestique, consultez [Gérer la protection contre les falsifications sur un appareil individuel](manage-tamper-protection-individual-device.md).

Si vous êtes une organisation qui utilise [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint), vous devez être en mesure de gérer la « protection contre les falsifications » dans Intune de la même façon que vous gérez d’autres fonctionnalités de protection des points de terminaison. Consultez les sections suivantes de cet article :

- [Gérer la protection contre les falsifications à l’aide de Microsoft Endpoint Manager](manage-tamper-protection-microsoft-endpoint-manager.md)
- [Gérer la protection contre les falsifications à l’aide de Microsoft 365 Defender](manage-tamper-protection-microsoft-365-defender.md)

## <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>Comment la configuration de la protection contre les falsifications dans Intune affecte-t-elle la façon dont je gère Microsoft Defender Antivirus avec stratégie de groupe ?

Si vous utilisez actuellement Intune pour configurer et gérer la « protection contre les falsifications », vous devez continuer à utiliser Intune. 

La stratégie de groupe ne s’applique pas à la protection contre les falsifications. Les modifications apportées aux paramètres antivirus Microsoft Defender à l’aide de stratégie de groupe sont ignorées lorsque la protection contre les falsifications est activée ou lorsque la protection contre les falsifications est configurée avec Intune.

## <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>Si nous utilisons Microsoft Intune pour configurer la « protection contre les falsifications », s’applique-t-elle uniquement à l’ensemble de l’organisation ?

Vous disposez d’une certaine flexibilité dans la configuration de la protection contre les falsifications avec Intune. Vous pouvez cibler l’ensemble de votre organisation ou sélectionner des appareils et des groupes d’utilisateurs spécifiques.

## <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>Puis-je configurer la protection contre les falsifications avec Microsoft Endpoint Configuration Manager ?

Si vous utilisez l’attachement de locataire, vous pouvez utiliser Microsoft Endpoint Configuration Manager. Consultez les ressources suivantes :

- [Gérer la protection contre les falsifications à l’aide de l’attachement de locataire avec Configuration Manager, version 2006](manage-tamper-protection-configuration-manager.md)
- [Blog tech community : Annonce de la protection contre les falsifications pour Configuration Manager clients d’attachement de locataire](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>J’ai l’inscription Windows E3. Puis-je utiliser la configuration de la protection contre les falsifications dans Intune ?

Actuellement, la configuration de la protection contre les falsifications dans Intune est disponible uniquement pour les clients qui ont [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint).

## <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Je suis un client d’entreprise. Les administrateurs locaux peuvent-ils modifier la protection contre les falsifications sur leurs appareils ?

Non. Les administrateurs locaux ne peuvent pas modifier les paramètres de « protection contre les falsifications ».

## <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Que se passe-t-il si mon appareil est intégré à Microsoft Defender pour point de terminaison puis passe à un état hors-carte ?

Si un appareil est désintégré à partir de Microsoft Defender pour point de terminaison, la protection contre les falsifications est activée, qui est l’état par défaut pour les appareils non gérés.

## <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>Si l’état de la protection contre les falsifications change, les alertes sont-ils affichées dans le portail Microsoft 365 Defender ?

Oui. L’alerte s’affiche [https://security.microsoft.com](https://security.microsoft.com) sous **Alertes**.

Votre équipe des opérations de sécurité peut également utiliser des requêtes de chasse, comme l’exemple suivant :

`AlertInfo|where Title == "Tamper Protection bypass"`

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
