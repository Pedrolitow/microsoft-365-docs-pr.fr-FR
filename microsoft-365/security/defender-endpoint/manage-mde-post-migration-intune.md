---
title: Gérer Microsoft Defender pour point de terminaison à l’aide de Intune
description: Découvrez comment gérer Microsoft Defender pour point de terminaison avec Intune
keywords: post-migration, gérer, opérations, maintenance, utilisation, intune, Microsoft Defender pour point de terminaison, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
ms.date: 07/01/2022
ms.reviewer: chventou
ms.openlocfilehash: c8a7b949118375fa10ac12a18ce82c4fadebd6f3
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67327154"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>Gérer Microsoft Defender pour point de terminaison avec Intune

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem), qui inclut Microsoft Intune (Intune) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). [En savoir plus sur Endpoint Manager](/mem/endpoint-manager-overview).

Cet article explique comment trouver vos paramètres de Microsoft Defender pour point de terminaison dans Intune et répertorie les différentes tâches que vous pouvez effectuer.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>Recherchez vos paramètres de Microsoft Defender pour point de terminaison dans Intune

> [!IMPORTANT]
> Le rôle Administrateur général ou Administrateur de service doit être attribué dans Intune pour configurer les paramètres décrits dans cet article. Pour en savoir plus, consultez **[Types d’administrateurs (Intune).](/mem/intune/fundamentals/users-add#types-of-administrators)**

1. Accédez à la Portail Azure ([https://portal.azure.com](https://portal.azure.com)) et connectez-vous.

2. Sous **Services Azure**, choisissez **Intune**.

3. Dans le volet de navigation à gauche, choisissez **Configuration de l’appareil**, puis, sous **Gérer**, choisissez **Profils**.

4. Sélectionnez un profil existant ou créez-en un.

> [!TIP]
> Besoin d’aide ? Voir **[Utilisation de Microsoft Defender pour point de terminaison avec Intune](/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**.

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>Configurer Microsoft Defender pour point de terminaison avec Intune

Le tableau suivant répertorie les différentes tâches que vous pouvez effectuer pour configurer Microsoft Defender pour point de terminaison avec Intune. Vous n’avez pas besoin de tout configurer en même temps ; choisissez une tâche, lisez les ressources correspondantes, puis continuez.

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Gérer les appareils de votre organisation à l’aide de Intune** pour protéger ces appareils et les données qui y sont stockés|[Protégez vos appareils avec Microsoft Intune](/mem/intune/protect/device-protect)|
|**Intégrer Microsoft Defender pour point de terminaison à Intune** en tant que solution mobile de défense contre les menaces <br/>*(pour les appareils Android exécutant Windows 10 ou Windows 11)*|[Appliquer la conformité pour Microsoft Defender pour point de terminaison avec l’accès conditionnel dans Intune](/mem/intune/protect/advanced-threat-protection)|
|**Utiliser l’accès conditionnel** pour contrôler les appareils et les applications qui peuvent se connecter à votre messagerie électronique et aux ressources de votre entreprise|[Configurer l’accès conditionnel dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/configure-conditional-access)|
|**Configurer les paramètres de l’Antivirus Microsoft Defender** à l’aide du fournisseur de services de configuration de stratégie ([fournisseur de services de configuration de](/windows/client-management/mdm/policy-configuration-service-provider) stratégie)|[Restrictions d’appareil : Antivirus Microsoft Defender](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) <br/><br/> [Fournisseur de solutions cloud de stratégie - Microsoft Defender pour point de terminaison](/windows/client-management/mdm/policy-csp-defender)|
|**Si nécessaire, spécifiez des exclusions pour l’antivirus Microsoft Defender** <br/><br/> *En règle générale, vous n’avez pas besoin d’appliquer des exclusions. L’Antivirus Microsoft Defender inclut un certain nombre d’exclusions automatiques basées sur les comportements connus du système d’exploitation et les fichiers de gestion classiques, tels que ceux utilisés dans la gestion d’entreprise, la gestion des bases de données et d’autres scénarios d’entreprise.*|[Recommandations d’analyse antivirus pour les ordinateurs d’entreprise qui exécutent des versions actuellement prises en charge de Windows](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers) <br/><br/> [Restrictions d’appareil : Exclusions de l’antivirus Microsoft Defender pour les appareils Windows 10 et Windows 11](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/> [Configurer les exclusions de l’Antivirus Microsoft Defender sur Windows Server 2016 ou 2019 ou 2022](/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**Configurer vos règles de réduction de la surface d’attaque** pour cibler les comportements logiciels souvent utilisés par les attaquants <br/><br/> *Configurez d’abord vos règles de réduction de la surface d’attaque en [mode audit](/microsoft-365/security/defender-endpoint/audit-windows-defender) (pendant au moins une semaine et jusqu’à deux mois). Vous pouvez surveiller l’état à l’aide de Power BI ([obtenir notre modèle](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules)), puis définir ces règles en mode actif lorsque vous êtes prêt.*|[Mode Audit en Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/audit-windows-defender) <br/><br/> [Endpoint Protection : Réduction de la surface d’attaque](/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction) <br/><br/> [En savoir plus sur les règles de réduction de la surface d’attaque](/microsoft-365/security/defender-endpoint/attack-surface-reduction) <br/><br/> [Billet de blog tech community : Démystifier les règles de réduction de la surface d’attaque - Partie 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)|
|**Configurer votre filtrage réseau** pour bloquer les connexions sortantes de n’importe quelle application vers des adresses IP ou des domaines dont la réputation est faible  <br/><br/> *Le filtrage réseau est également appelé [protection réseau](/microsoft-365/security/defender-endpoint/network-protection).* <br/><br/> *Assurez-vous que les dernières [mises à jour de plateforme anti-programme malveillant](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) sont installées sur les appareils Windows 10 et Windows 11.*|[Protection des points de terminaison : filtrage réseau](/mem/intune/protect/endpoint-protection-windows-10#network-filtering) <br/><br/> [Passer en revue les événements de protection réseau dans Windows observateur d'événements](/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer)|
|**Configurer l’accès contrôlé aux dossiers** pour vous protéger contre les ransomware <br/><br/> *[L’accès contrôlé aux dossiers](/microsoft-365/security/defender-endpoint/controlled-folders) est également appelé protection antiransomware.*|[Endpoint Protection : accès contrôlé aux dossiers](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Activer l’accès contrôlé aux dossiers dans Intune](/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)|
|**Configurer exploit protection** pour protéger les appareils de votre organisation contre les programmes malveillants qui utilisent des exploits pour propager et infecter d’autres appareils <br/><br/> *[Exploit Protection](/microsoft-365/security/defender-endpoint/exploit-protection) est également appelé Exploit Guard.*|[Endpoint Protection : Microsoft Defender Exploit Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/> [Activer la protection contre les attaques dans Intune](/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune)|
|**Configurez Microsoft Defender SmartScreen** pour vous protéger contre les sites et fichiers malveillants sur Internet. <br/><br/> *Microsoft Edge doit être installé sur les appareils de votre organisation. Pour la protection sur les navigateurs Google Chrome et FireFox, configurez exploit protection.*|[Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/> [Restrictions d’appareil : Microsoft Defender SmartScreen](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen) <br/><br/> [Paramètres de stratégie pour la gestion de SmartScreen dans Intune](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)|
|**Configurer le Pare-feu Microsoft Defender** pour bloquer le trafic réseau non autorisé entrant ou sortant des appareils de votre organisation|[Protection des points de terminaison : Pare-feu Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [Pare-feu Microsoft Defender avec sécurité avancée](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)|
|**Configurer le chiffrement et BitLocker** pour protéger les informations sur les appareils de votre organisation exécutant Windows|[Protection des points de terminaison : Chiffrement Windows](/mem/intune/protect/endpoint-protection-windows-10#windows-encryption) <br/><br/> [BitLocker pour les appareils Windows 10 et Windows 11](/windows/security/information-protection/bitlocker/bitlocker-overview)|
|**Configurer Microsoft Defender Credential Guard** pour vous protéger contre les attaques par vol d’informations d’identification|Pour Windows 10, Windows 11, Windows Server 2016 et Windows Server 2019 et Windows Server 2022, consultez [Endpoint Protection : Microsoft Defender Credential Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/> Pour Windows 7 SP1, Windows Server 2008 R2 SP1, Windows 8.1 et Windows Server 2012 R2, consultez [Atténuant les attaques par pass-the-hash (PtH) et autres vols](https://www.microsoft.com/download/details.aspx?id=36036) d’informations d’identification, versions 1 et 2|
|**Configurer Microsoft Defender Application Control** pour choisir d’auditer ou d’approuver des applications sur les appareils de votre organisation <br/><br/> *Microsoft Defender Application Control est également appelé [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).*|[Déployer des stratégies De contrôle d’application Microsoft Defender à l’aide de Microsoft Intune](/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) <br/><br/> [Endpoint Protection : Microsoft Defender Application Control](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control) <br/><br/> [CSP AppLocker](/windows/client-management/mdm/applocker-csp)|
|**Configurer le contrôle d’appareil et l’accès aux périphériques USB** pour empêcher les menaces sur les périphériques non autorisés de compromettre vos appareils|[Contrôler les périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour point de terminaison et de Intune](/windows/security/threat-protection/device-control/control-usb-devices-using-intune)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Configurer votre portail Microsoft 365 Defender

Si vous ne l’avez pas encore fait, configurez votre portail Microsoft 365 Defender pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre organisation. Voir [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Vous pouvez également configurer si et quelles fonctionnalités les utilisateurs finaux peuvent voir dans le portail Microsoft 365 Defender.

- [Vue d’ensemble de Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Endpoint Protection : Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Prochaines étapes

- [Obtenir une vue d’ensemble de La gestion des vulnérabilités defender](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Visitez le tableau de bord des opérations de sécurité du portail Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
