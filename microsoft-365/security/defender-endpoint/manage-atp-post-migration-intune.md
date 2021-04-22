---
title: Gérer Microsoft Defender pour le point de terminaison à l'aide d'Intune
description: Découvrez comment gérer Microsoft Defender pour Endpoint avec Intune
keywords: post-migration, manage, operations, maintenance, utilization, intune, Microsoft Defender for Endpoint, edr
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
ms.topic: article
ms.date: 09/22/2020
ms.reviewer: chventou
ms.openlocfilehash: d8396c352e593f9922b11e23119f7d9718eaf752
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51934224"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>Gérer Microsoft Defender pour le point de terminaison avec Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Nous vous recommandons d'utiliser [Microsoft Endpoint Manager,](https://docs.microsoft.com/mem)qui inclut Microsoft Intune (Intune) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). [En savoir plus sur endpoint Manager](https://docs.microsoft.com/mem/endpoint-manager-overview).

Cet article décrit comment rechercher vos paramètres microsoft Defender pour point de terminaison dans Intune et répertorie les différentes tâches que vous pouvez effectuer.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>Rechercher vos paramètres de point de terminaison Microsoft Defender dans Intune

> [!IMPORTANT]
> Vous devez être administrateur général ou administrateur de service dans Intune pour configurer les paramètres décrits dans cet article. Pour plus d'informations, voir **[Types d'administrateurs (Intune).](https://docs.microsoft.com/mem/intune/fundamentals/users-add#types-of-administrators)**

1. Go to the Azure portal ( [https://portal.azure.com](https://portal.azure.com) ) and sign in.

2. Sous **Azure Services,** choisissez **Intune.**

3. Dans le volet de navigation sur la gauche, choisissez **Configuration** de l'appareil, puis, sous **Gérer**, choisissez **Profils**.

4. Sélectionnez un profil existant ou créez-en un.

> [!TIP]
> Besoin d’aide ? Voir **[Utilisation de Microsoft Defender pour endpoint avec Intune.](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**  

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>Configurer Microsoft Defender pour endpoint avec Intune

Le tableau suivant répertorie les différentes tâches que vous pouvez effectuer pour configurer Microsoft Defender pour Endpoint avec Intune. Vous n'avez pas besoin de tout configurer en même temps . choisissez une tâche, lisez les ressources correspondantes, puis continuez.

|Tâche  |Ressources pour en savoir plus  |
|---------|---------|
|**Gérer les appareils de votre organisation à l'aide d'Intune** pour protéger ces appareils et données qu'ils stockent     |[Protégez vos appareils avec Microsoft Intune](https://docs.microsoft.com/mem/intune/protect/device-protect)         |
|**Intégrer Microsoft Defender pour endpoint à Intune en** tant que solution de défense contre les menaces mobiles <br/>*(pour les appareils Android et les appareils exécutant Windows 10 ou version ultérieure)*   |[Appliquer la conformité de Microsoft Defender pour le point de terminaison avec l'accès conditionnel dans Intune](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection)         |
|**Utiliser l'accès conditionnel** pour contrôler les appareils et les applications qui peuvent se connecter à vos ressources de messagerie et d'entreprise |[Configurer l'accès conditionnel dans Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-conditional-access) |
|**Configurer les paramètres de l'Antivirus Microsoft Defender** à l'aide du fournisseur de services de configuration de stratégie ([Fournisseur CSP Policy](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)) |[Restrictions d'appareil : Antivirus Microsoft Defender](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)<br/><br/>[Stratégie CSP - Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)  | 
|**Si nécessaire, spécifiez des exclusions pour l'Antivirus Microsoft Defender** <br/><br/>*En règle générale, il n'est pas nécessaire d'appliquer des exclusions. L'Antivirus Microsoft Defender inclut un certain nombre d'exclusions automatiques basées sur les comportements connus du système d'exploitation et les fichiers de gestion classiques, tels que ceux utilisés dans la gestion d'entreprise, la gestion des bases de données et d'autres scénarios d'entreprise.* |[Recommandations en matière d'analyse antivirus pour les ordinateurs d'entreprise qui exécutent actuellement des versions de Windows actuellement pris en charge](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers)<br/><br/>[Restrictions d'appareil : exclusions de l'antivirus Microsoft Defender pour les appareils Windows 10](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/>[Configurer les exclusions de l'Antivirus Microsoft Defender sur Windows Server 2016 ou 2019](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**Configurer vos règles de réduction de la surface d'attaque** pour cibler les comportements logiciels qui sont souvent abusés par les attaquants<br/><br/>*Configurez d'abord vos règles de réduction de la surface d'attaque en [mode audit](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/audit-windows-defender) (pendant au moins une semaine et jusqu'à deux mois). Vous pouvez surveiller l'état à l'aide de Power BI [(obtenir](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules)notre modèle), puis définir ces règles en mode actif lorsque vous êtes prêt.* |[Mode audit dans Microsoft Defender pour point de terminaison ](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/audit-windows-defender)<br/><br/>[Protection des points de terminaison : Réduction de la surface d'attaque](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction)<br/><br/>[En savoir plus sur les règles de réduction de la surface d'attaque](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/attack-surface-reduction)<br/><br/>[Billet de blog de la communauté technique : Démystifier les règles de réduction de la surface d'attaque - Partie 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) |
|**Configurer votre filtrage réseau pour** bloquer les connexions sortantes entre n'importe quelle application et les adresses IP ou les domaines ayant une réputation faible  <br/><br/>*Le filtrage réseau est également appelé [protection réseau.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/network-protection)*<br/><br/>*Assurez-vous que les dernières mises à jour de la plateforme [anti-programme](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) malveillant sont installées sur les appareils Windows 10.*|[Protection des points de terminaison : filtrage réseau](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#network-filtering)<br/><br/>[Passer en revue les événements de protection réseau dans l'Observateur d'événements Windows](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer) |
|**Configurer l'accès contrôlé aux dossiers pour** la protection contre les ransomware <br/><br/>*[L'accès contrôlé aux](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/controlled-folders) dossiers est également appelé protection anti-programme malveillant.*  |[Protection des points de terminaison : accès contrôlé aux dossiers](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/>[Activer l'accès contrôlé aux dossiers dans Intune](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)  |
|**Configurer Exploit Protection pour protéger** les appareils de votre organisation contre les programmes malveillants qui utilisent des attaques pour se propager et infecter d'autres appareils <br/><br/> *[Exploit Protection](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/exploit-protection) est également appelé Exploit Guard.* |[Protection des points de terminaison : Microsoft Defender Exploit Guard](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/>[Activer Exploit Protection dans Intune](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune) |
|**Configurez Microsoft Defender SmartScreen pour vous** protéger contre les sites et fichiers malveillants sur Internet. <br/><br/> *Microsoft Edge doit être installé sur les appareils de votre organisation. Pour une protection sur les navigateurs Google Chrome et FireFox, configurez Exploit Protection.*  |[Microsoft Defender SmartScreen](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/>[Restrictions d'appareil : Microsoft Defender SmartScreen](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen)<br/><br/>[Paramètres de stratégie pour la gestion de SmartScreen dans Intune](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)  |
|**Configurer le Pare-feu Microsoft Defender** pour bloquer le trafic réseau non autorisé qui circule vers ou hors des appareils de votre organisation  |[Protection des points de terminaison : Pare-feu Microsoft Defender](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [Pare-feu Microsoft Defender avec fonctions avancées de sécurité](https://docs.microsoft.com/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) |
|**Configurer le chiffrement et BitLocker pour** protéger les informations sur les appareils de votre organisation exécutant Windows |[Protection des points de terminaison : chiffrement Windows](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#windows-encryption)<br/><br/>[BitLocker pour appareils Windows 10](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview) |
|**Configurer Microsoft Defender Credential Guard pour vous** protéger contre les attaques par vol d'informations d'identification |Pour Windows 10, Windows Server 2016 et Windows Server 2019, voir [Endpoint Protection : Microsoft Defender Credential Guard](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/>Pour Windows 7 SP1, Windows Server 2008 R2 SP1, Windows 8.1 et Windows Server 2012 R2, voir Atténuation des attaques par hachage [(PtH)](https://www.microsoft.com/download/details.aspx?id=36036) et autres vol d'informations d'identification, versions 1 et 2  |
|**Configurer Microsoft Defender Application Control pour** choisir s'il faut auditer ou faire confiance aux applications sur les appareils de votre organisation <br/><br/>*Microsoft Defender Application Control est également appelé [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).*|[Déployer des stratégies Microsoft Defender Application Control à l'aide de Microsoft Intune](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune)<br/><br/>[Protection des points de terminaison : contrôle d'application Microsoft Defender](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control)<br/><br/>[AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)|
|**Configurer le contrôle d'appareil et l'accès aux périphériques USB** pour empêcher les menaces dans les périphériques non autorisés de compromettre vos appareils |[Contrôler les périphériques USB et autres supports amovibles à l'aide de Microsoft Defender pour Endpoint et Intune](https://docs.microsoft.com/windows/security/threat-protection/device-control/control-usb-devices-using-intune)  |

## <a name="configure-your-microsoft-defender-security-center"></a>Configurer votre Centre de sécurité Microsoft Defender

Si vous ne l'avez pas déjà fait, configurez votre Centre de sécurité **Microsoft Defender** ( ) pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre [https://securitycenter.windows.com](https://securitycenter.windows.com) organisation. 

Vous pouvez également configurer si et quelles fonctionnalités les utilisateurs finaux peuvent voir dans le Centre de sécurité Microsoft Defender.

- [Vue d'ensemble du Centre de sécurité Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/use)

- [Protection des points de terminaison : Centre de sécurité Microsoft Defender](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Étapes suivantes

- [Obtenir une vue d'ensemble de la gestion des menaces et des vulnérabilités](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [Visiter le tableau de bord opérations de sécurité du Centre de sécurité Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/security-operations-dashboard)
