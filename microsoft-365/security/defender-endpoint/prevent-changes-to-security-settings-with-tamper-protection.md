---
title: Protéger les paramètres de sécurité avec la protection contre la falsifiation
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Utilisez la protection contre les falsifications pour empêcher les applications malveillantes de modifier les paramètres de sécurité importants.
keywords: programmes malveillants, defender, antivirus, protection contre les falsifications
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.date: 09/23/2022
audience: ITPro
ms.topic: conceptual
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
ms.openlocfilehash: 5f2a87f1fa8ff8130e460f46c9ac94275ba0735d
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68221321"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Protéger les paramètres de sécurité avec la protection contre la falsifiation

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

La protection contre les falsifications est disponible pour les appareils qui exécutent l’une des versions suivantes de Windows :

- Windows 11
- Multisession Windows 11 Entreprise 
- Windows 10
- Windows 10 Entreprise à sessions multiples
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016
- Windows Server 2012 R2

> [!NOTE]
> La protection contre les falsifications dans Windows Server 2012 R2 est disponible pour les appareils intégrés à l’aide du package de solution unifié moderne. Pour plus d’informations, consultez [Intégrer des serveurs Windows au service Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

## <a name="overview"></a>Vue d’ensemble

Pendant certains types de cyberattaques, les mauvais acteurs essaient de désactiver les fonctionnalités de sécurité, telles que la protection antivirus, sur vos machines. Les acteurs malveillants aiment désactiver vos fonctionnalités de sécurité pour accéder plus facilement à vos données, installer des programmes malveillants ou exploiter vos données, votre identité et vos appareils. La protection contre les falsifications permet d’éviter que ces types de choses se produisent. Avec la protection contre les falsifications, les applications malveillantes sont empêchées d’effectuer des actions telles que :

- Désactivation de la protection contre les virus et les menaces
- Désactivation de la protection en temps réel
- Désactivation de la surveillance du comportement
- Désactivation de la protection antivirus, telle que IOfficeAntivirus (IOAV)
- Désactivation de la protection fournie par le cloud
- Suppression des mises à jour du renseignement de sécurité
- Désactivation des actions automatiques sur les menaces détectées
- Suppression des notifications dans l’application Sécurité Windows
- Désactivation de l’analyse des archives et des fichiers réseau

> [!IMPORTANT]
> La protection intégrée (préversion) inclut l’activation de la protection contre les falsifications par défaut. Pour en savoir plus sur la protection intégrée, consultez :
> - [La protection intégrée permet de se protéger contre les ransomware](built-in-protection.md) (article)
> - [La protection contre les falsifications sera activée pour tous les clients d’entreprise](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/tamper-protection-will-be-turned-on-for-all-enterprise-customers/ba-p/3616478) (billet de blog Tech Community)

### <a name="how-it-works"></a>Mode de fonctionnement

La protection contre les falsifications verrouille essentiellement Microsoft Defender Antivirus à ses valeurs sécurisées par défaut et empêche la modification de vos paramètres de sécurité par le biais d’applications et de méthodes telles que :

- Configuration des paramètres dans l’Éditeur du Registre sur votre appareil Windows
- Modification des paramètres via les applets de commande PowerShell
- Modification ou suppression des paramètres de sécurité via stratégie de groupe

La protection contre les falsifications ne vous empêche pas d’afficher vos paramètres de sécurité. De plus, la protection contre les falsifications n’affecte pas la façon dont les applications antivirus non Microsoft s’inscrivent auprès de l’application Sécurité Windows. Si votre organisation utilise Windows 10 Entreprise E5, les utilisateurs individuels ne peuvent pas modifier le paramètre de protection contre les falsifications . Dans ce cas, la protection contre les falsifications est gérée par votre équipe de sécurité.

### <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

|Pour effectuer cette tâche...|Consultez cette section...|
|---|---|
|Gérer la protection contre les falsifications dans votre locataire <p> Utiliser le portail Microsoft 365 Defender pour activer ou désactiver la protection contre les falsifications|[Gérer la protection contre les falsifications pour votre organisation à l’aide de Microsoft 365 Defender](manage-tamper-protection-microsoft-365-defender.md)|
|Ajuster les paramètres de protection contre les falsifications dans votre organisation <p> Utilisez Intune (Microsoft Endpoint Manager) pour activer ou désactiver la protection contre les falsifications. Vous pouvez configurer la protection contre les falsifications pour certains utilisateurs ou tous les utilisateurs avec cette méthode.|[Gérer la protection contre les falsifications pour votre organisation à l’aide de Microsoft Endpoint Manager](manage-tamper-protection-microsoft-endpoint-manager.md)|
|Activer ou désactiver la protection contre les falsifications pour votre organisation avec Configuration Manager|[Gérer la protection contre les falsifications pour votre organisation à l’aide de l’attachement de locataire avec Configuration Manager, version 2006](manage-tamper-protection-configuration-manager.md)|
|Activer ou désactiver la protection contre les falsifications pour un appareil individuel|[Gérer la protection contre les falsifications sur un appareil individuel](manage-tamper-protection-individual-device.md)|
|Afficher des détails sur les tentatives de falsification sur les appareils|[Afficher des informations sur les tentatives de falsification](#view-information-about-tampering-attempts)|
|Passez en revue vos recommandations de sécurité|[Passer en revue les recommandations de sécurité](#review-your-security-recommendations)|
|Consulter la liste des questions fréquentes (FAQ)|[Parcourir les questions fréquentes (FAQ)](faqs-tamper-protection.md)|

## <a name="potential-dependency-on-cloud-protection"></a>Dépendance potentielle vis-à-vis de la protection cloud  
  
Selon la méthode ou l’outil de gestion que vous utilisez pour activer la protection contre les falsifications, il peut y avoir une dépendance [vis-à-vis de la protection fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md). La protection fournie par le cloud est également appelée protection cloud, ou Microsoft Advanced Protection Service (MAPS).

Le tableau suivant fournit des détails sur les méthodes, les outils et les dépendances.

| Activation de la protection contre les falsifications | Dépendance vis-à-vis de la protection cloud |
|---|---|
|Microsoft Intune|Non|
|Microsoft Endpoint Configuration Manager with Tenant Attach|Non|
|portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))|Oui|

## <a name="are-you-using-windows-server-2012-r2-2016-or-windows-version-1709-1803-or-1809"></a>Utilisez-vous Windows Server 2012 R2, 2016 ou Windows version 1709, 1803 ou 1809 ?

Si vous utilisez Windows Server 2012 R2 à l’aide de la solution unifiée moderne, Windows Server 2016, Windows 10 version 1709, 1803 ou [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019), vous ne **verrez pas la protection contre les falsifications** dans l’application Sécurité Windows. Au lieu de cela, vous pouvez utiliser PowerShell pour déterminer si la protection contre les falsifications est activée.

Sur Windows Server 2016, l’application Paramètres ne reflète pas avec précision l’état de la protection en temps réel lorsque la protection contre les falsifications est activée.

### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>Utiliser PowerShell pour déterminer si la protection contre les falsifications et la protection en temps réel sont activées

1. Ouvrez l’application Windows PowerShell.

2. Utilisez l’applet [de commande Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell.

3. Dans la liste des résultats, recherchez `IsTamperProtected` ou `RealTimeProtectionEnabled`. (La *valeur true signifie* que la protection contre les falsifications est activée.)

## <a name="view-information-about-tampering-attempts"></a>Afficher des informations sur les tentatives de falsification

Les tentatives de falsification indiquent généralement des cyberattaques plus importantes. Les acteurs malveillants tentent de modifier les paramètres de sécurité pour conserver et ne pas être détectés. Si vous faites partie de l’équipe de sécurité de votre organisation, vous pouvez afficher des informations sur ces tentatives, puis prendre les mesures appropriées pour atténuer les menaces.

Lorsqu’une tentative de falsification est détectée, une alerte est déclenchée dans le [portail Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/portal-overview) ([https://security.microsoft.com](https://security.microsoft.com)).

À l’aide des fonctionnalités avancées de [détection et de réponse](overview-endpoint-detection-response.md) des points de terminaison et de [repérage avancées](advanced-hunting-overview.md) dans Microsoft Defender pour point de terminaison, votre équipe des opérations de sécurité peut examiner et résoudre ces tentatives.

## <a name="review-your-security-recommendations"></a>Passez en revue vos recommandations de sécurité

La protection contre les falsifications s’intègre à [Gestion des vulnérabilités Microsoft Defender](next-gen-threat-and-vuln-mgt.md) fonctionnalités. [Les recommandations de sécurité](tvm-security-recommendation.md) incluent la garantie que la protection contre les falsifications est activée. Par exemple, vous pouvez effectuer une recherche sur la *falsification*. Dans les résultats, vous pouvez sélectionner **Activer la protection contre les falsifications** pour en savoir plus et l’activer.

Pour en savoir plus sur Gestion des vulnérabilités Microsoft Defender, consultez [Dashboard Insights - Defender Vulnerability Management](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management).


> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Sécuriser les PC Windows avec Endpoint Protection pour Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Obtenir une vue d’ensemble de Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint)
- [Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](why-use-microsoft-defender-antivirus.md)
- [Activer le mode de résolution des problèmes](enable-troubleshooting-mode.md)
- [Scénarios de mode de dépannage](troubleshooting-mode-scenarios.md)
