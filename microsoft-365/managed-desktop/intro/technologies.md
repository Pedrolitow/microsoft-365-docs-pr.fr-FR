---
title: Technologies associées de Bureau géré Microsoft
description: Cet article répertorie les technologies et applications utilisées dans Microsoft Manged Desktop.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 7cc8faf8e37d1e700a8eb4e06be90259dc54a007
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60667457"
---
# <a name="microsoft-managed-desktop-technologies"></a>Technologies associées de Bureau géré Microsoft

Cet article répertorie les technologies et applications utilisées dans Microsoft Manged Desktop.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Microsoft 365 Entreprise licences est requise pour tous les Microsoft Manged Desktop utilisateurs. Pour plus d’informations sur les conditions de licence requises pour le service, voir [Prerequisites for Microsoft Manged Desktop](../get-ready/prerequisites.md).

Cet article récapitule les composants inclus dans les licences Enterprise requises, avec une description de la façon dont le service utilise chaque composant avec Microsoft Manged Desktop périphériques. Des rôles et responsabilités spécifiques pour chaque domaine sont détaillés dans Microsoft Manged Desktop documentation. 

## <a name="office-365-e3-or-e5"></a>Office 365 E3 ou E5

| Produit |Informations |
--- |--- 
Applications Microsoft 365 pour les grandes entreprises (64 bits) | Ces Office applications seront livrées avec l’appareil : Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype Entreprise, OneNote.<br><br>Les versions complètes 64 bits Microsoft Project et Microsoft Visio ne sont pas incluses. Toutefois, étant donné que l’installation de ces applications dépend de l’installation Applications Microsoft 365 pour les grandes entreprises, Microsoft Manged Desktop a créé des déploiements Microsoft Intune par défaut et des groupes de sécurité que vous pouvez ensuite utiliser pour déployer ces applications aux utilisateurs titulaires d’une licence. Pour plus d’informations, [voir Install Microsoft Project ou Microsoft Visio sur Microsoft Manged Desktop appareils.](../get-started/project-visio.md)
OneDrive |Azure Active Directory L' sign on unique est activée pour les utilisateurs lorsqu’ils se connectent pour la première fois à OneDrive.<br><br>La redirection de dossiers connue pour les dossiers « Bureau », « Document » et « Images » est incluse ; activées et configurées par Microsoft Manged Desktop.
Store Apps | Microsoft Sway et Power BI ne sont pas livrés avec l’appareil. Ces applications sont disponibles en téléchargement à partir Microsoft Store.
Win32 Applications | Teams n’est pas fourni avec l’appareil, mais il est empaqueté et fourni par Microsoft pour Microsoft Manged Desktop appareils. Le client Azure Information Protection n’est pas livré avec l’appareil, mais vous pouvez le faire empaqueté pour le déploiement.
Applications Web | Yammer, Office dans un navigateur, Delve, Flow, StaffHub, Power Apps et planner ne sont pas livrés avec l’appareil. Les utilisateurs peuvent accéder à la version web de ces applications avec un navigateur.

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Entreprise E5 ou E3 avec Microsoft Defender pour le point de terminaison

Nous recommandons à vos administrateurs informatiques de configurer les paramètres suivants. Ces paramètres ne sont pas inclus ou gérés dans le cadre de Microsoft Manged Desktop.

Produit  |Informations
--- | ---
Windows Hello Entreprise | Vous devez implémenter Windows Hello entreprise pour remplacer les mots de passe par une authentification forte à deux facteurs pour Microsoft Manged Desktop appareils. Pour plus d’informations, [voir Windows Hello entreprise.](/windows/security/identity-protection/hello-for-business/hello-identity-verification)
Application Virtualization | Vous pouvez déployer des packages Application Virtualization (App-V) à l’aide du client de gestion des applications Intune Win32. Pour plus d’informations, [voir Application Virtualization](/windows/application-management/app-v/appv-technical-reference).
Microsoft 365 protection contre la perte de données | Vous devez implémenter Microsoft 365 protection contre la perte de données pour surveiller les actions entreprises sur les éléments que vous avez déterminés comme sensibles et pour empêcher le partage involontaire de ces éléments. Pour plus d’informations, [voir Microsoft 365 protection contre la perte de données.](../../compliance/endpoint-dlp-learn-about.md)

Fonctionnalités incluses et gérées dans le cadre Microsoft Manged Desktop :

Produit |Informations
--- |---
Chiffrement de lecteur BitLocker | Le chiffrement de lecteur BitLocker est utilisé pour chiffrer tous les lecteurs système. Pour plus d’informations, [voir Chiffrement de lecteur BitLocker.](/windows/security/information-protection/bitlocker/bitlocker-overview)
Windows Defender System Guard | Protège l’intégrité du système au démarrage et confirme que l’intégrité du système a réellement été conservée. Pour plus d’informations, [voir Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows).
Windows Defender Credential Guard | Windows Defender Credential Guard utilise la sécurité basée sur la virtualisation pour isoler les secrets afin que seuls les logiciels système privilégiés y accèdent. Pour plus d’informations, [voir Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows).
Microsoft Defender pour le point de terminaison - Détection et réponse des points de terminaison | Microsoft Manged Desktop Les opérations de sécurité répondent aux alertes et prennent des mesures pour corriger les menaces à l’aide de la détection et de la réponse des points de terminaison. Pour plus d’informations, [voir Microsoft Defender for Endpoint - Endpoint Detection and Response](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response).
Microsoft Defender pour le point de terminaison - Experts en menaces | Microsoft Manged Desktop s’intègre aux informations et aux données des experts en menaces par le biais de notifications d’attaque ciblées. Vous devez fournir un consentement supplémentaire avant d’activer ce service. Pour plus d’informations, [voir Microsoft Defender for Endpoint - Threat Experts](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts).
Microsoft Defender pour le point de terminaison - Gestion des menaces et des vulnérabilités | Obligatoire pour une utilisation future dans le plan Microsoft Manged Desktop service. Pour plus d’informations, voir Microsoft Defender pour le point de terminaison - Gestion des [menaces et des vulnérabilités.](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
Microsoft Defender pour le point de terminaison - Réduction de la surface d’attaque | La réduction de la surface d’attaque cible les comportements logiciels à risque qui sont souvent abusés par les attaquants. Pour plus d’informations, [voir Microsoft Defender pour le point de terminaison - Réduction de la surface d’attaque.](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)
Microsoft Defender pour le point de terminaison - Exploit Protection | Protège contre les programmes malveillants qui utilisent des attaques pour infecter les appareils et se propager en appliquant automatiquement des techniques d’atténuation des attaques aux processus et applications du système d’exploitation. Pour plus d’informations, [voir Microsoft Defender for Endpoint - Exploit Protection](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection).
Microsoft Defender pour le point de terminaison - Protection du réseau | La protection du réseau étend l’étendue des Microsoft Defender SmartScreen pour bloquer tout le trafic HTTP et HTTPS sortant qui tente de se connecter à des sources de réputation faible. Pour plus d’informations, [voir Microsoft Defender for Endpoint - Network Protection](/windows/security/threat-protection/microsoft-defender-atp/network-protection).
Protection contre la falsification Microsoft Defender | Windows La protection contre les falsifications permet d’empêcher les paramètres de sécurité tels que la protection antivirus d’être modifiés. Pour plus d’informations, voir Protection contre la falsification [Microsoft Defender.](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection)
Antivirus Microsoft Defender Protection antivirus en temps réel, heuristique et basée sur le comportement | Recherchez toujours les menaces de fichier et de traitement qui ne sont peut-être pas détectées comme des programmes malveillants. Pour plus d’informations, Antivirus Microsoft Defender protection antivirus en temps [réel, heuristique et basée sur le comportement.](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md)
Antivirus Microsoft Defender Protection cloud | Fournit une protection automatisée et immédiate dynamique contre les menaces nouvelles et émergentes. Pour plus d’informations, [Antivirus Microsoft Defender protection cloud.](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus)
Microsoft Defender pour le point de terminaison - « Bloquer à la première vue » | Permet de détecter et de bloquer les nouveaux programmes malveillants Windows un fichier suspect ou inconnu. Pour plus d’informations, [voir Microsoft Defender pour point de terminaison - Bloquer à la première vue.](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus)
Antivirus Microsoft Defender Applications potentiellement indésirables | Les applications potentiellement indésirables sont utilisées pour bloquer les applications qui peuvent ralentir votre ordinateur, afficher des publicités inattendues ou, au pire, installer d’autres logiciels qui peuvent être inattendus ou indésirables. Pour plus d’informations, [voir Antivirus Microsoft Defender Applications potentiellement indésirables.](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
Windows Defender Pare-feu avec fonctions avancées de sécurité | Le filtrage du trafic réseau à double sens basé sur l’hôte pour un appareil, Windows Defender Firewall bloque le trafic réseau non autorisé qui circule à l’entrée ou à l’sortie de l’appareil local. Pour plus d’informations, [voir Windows Defender Firewall with Advanced Security](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
Contrôle de compte d’utilisateur | Le contrôle de compte d’utilisateur bascule vers le Bureau sécurisé lorsqu’une tâche ou une action nécessite un accès de type compte administrateur. Microsoft Manged Desktop utilisateurs standard se voit attribuer un accès utilisateur standard lors de l’inscription. Pour plus d’informations, [voir Contrôle de compte d’utilisateur.](/windows/security/identity-protection/user-account-control/how-user-account-control-works)


## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

Produit |Informations
 --- | ---
Enterprise Mobility + Security E3<br>Azure Active Directory Premium P2 | Vous pouvez utiliser toutes les fonctionnalités de Enterprise Mobility + Security E3 gestion des appareils mobiles. Vous pouvez utiliser Azure Active Directory Premium P2 en tant que fonctionnalité facultative avec Microsoft Manged Desktop.
Microsoft Cloud App Security | Vous pouvez utiliser cette fonctionnalité facultative avec Microsoft Manged Desktop.
Azure Information Protection P2  | Vous pouvez utiliser cette fonctionnalité facultative avec Microsoft Manged Desktop.
