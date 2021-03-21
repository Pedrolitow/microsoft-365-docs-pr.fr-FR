---
title: Technologies associées de Bureau géré Microsoft
description: Cet article répertorie les technologies et applications utilisées dans bureau géré Microsoft.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 22371d22562960efdc50235657a08e15dba893d3
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50920575"
---
# <a name="microsoft-managed-desktop-technologies"></a>Technologies associées de Bureau géré Microsoft

Cet article répertorie les technologies et applications utilisées dans bureau géré Microsoft.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

La gestion des licences Microsoft 365 Entreprise est requise pour tous les utilisateurs du Bureau géré Microsoft. Pour plus d’informations sur les conditions requises en matière de licences pour le service, voir [Prerequisites for Microsoft Managed Desktop](../get-ready/prerequisites.md).

Cet article récapitule les composants inclus dans les licences d’entreprise requises, avec une description de la façon dont le service utilise chaque composant avec les appareils bureau géré Microsoft. Les rôles et responsabilités spécifiques pour chaque domaine sont détaillés dans la documentation du Bureau géré Microsoft. 

## <a name="office-365-e3-or-e5"></a>Office 365 E3 ou E5
 |
 --- | ---
Applications Microsoft 365 pour les entreprises (64 bits) | Ces applications Office seront livrées avec l’appareil : Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype Entreprise, OneNote.<br><br>Les versions complètes 64 bits de Microsoft Project et Microsoft Visio ne sont pas incluses. Toutefois, étant donné que l’installation de ces applications dépend de l’installation des applications Microsoft 365 pour les entreprises, Bureau géré Microsoft a créé des déploiements et des groupes de sécurité Microsoft Intune par défaut que vous pouvez ensuite utiliser pour déployer ces applications pour les utilisateurs sous licence. Pour plus d’informations, [voir Installer Microsoft Project ou Microsoft Visio sur les appareils de bureau géré Microsoft.](../get-started/project-visio.md)
OneDrive |L’ion unique Azure Active Directory est activée pour les utilisateurs lorsqu’ils se connectent pour la première fois à OneDrive.<br><br>La redirection de dossiers connue pour les dossiers « Bureau », « Document » et « Images » est incluse ; activé et configuré par Bureau géré Microsoft.
Store Apps |    Microsoft Sway et Power BI ne sont pas livrés avec l’appareil. Ces applications sont disponibles en téléchargement à partir du Microsoft Store.
Win32 Applications |    Teams n’est pas fourni avec l’appareil, mais il est empaqueté et fourni par Microsoft pour les appareils bureau géré Microsoft. Le client Azure Information Protection n’est pas livré avec l’appareil, mais vous pouvez le faire empaqueté pour le déploiement.
Applications Web |  Yammer, Office dans un navigateur, Delve, Flow, StaffHub, PowerApps et planner ne sont pas livrés avec l’appareil. Les utilisateurs peuvent accéder à la version web de ces applications avec un navigateur.


## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Entreprise E5 ou E3 avec Microsoft Defender pour Point de terminaison
Nous recommandons à vos administrateurs informatiques de configurer les paramètres suivants. Ces paramètres ne sont pas inclus ou gérés dans le cadre du Bureau géré Microsoft.

 |
 --- | ---
Windows Hello Entreprise | Vous devez implémenter Windows Hello Entreprise pour remplacer les mots de passe par une authentification forte à deux facteurs pour les appareils bureau géré Microsoft. Pour plus d’informations, [voir Windows Hello Entreprise.](/windows/security/identity-protection/hello-for-business/hello-identity-verification)
Application Virtualization | Vous pouvez déployer des packages Application Virtualization (App-V) à l’aide du client de gestion des applications Intune Win32. Pour plus d’informations, [voir Application Virtualization](/windows/application-management/app-v/appv-technical-reference).
Protection contre la perte de données Microsoft 365 | Vous devez implémenter la protection contre la perte de données Microsoft 365 pour surveiller les actions entreprises sur les éléments que vous avez déterminés comme sensibles et pour empêcher le partage involontaire de ces éléments. Pour plus d’informations, voir Protection contre la perte de données [Microsoft 365.](../../compliance/endpoint-dlp-learn-about.md)


Fonctionnalités incluses et gérées dans le cadre du Bureau géré Microsoft :

 |
 --- | ---
Chiffrement de lecteur BitLocker | Le chiffrement de lecteur BitLocker est utilisé pour chiffrer tous les lecteurs système. Pour plus d’informations, [voir Chiffrement de lecteur BitLocker.](/windows/security/information-protection/bitlocker/bitlocker-overview)
Windows Defender System Guard | Protège l’intégrité du système au démarrage et confirme que l’intégrité du système a réellement été conservée. Pour plus d’informations, [voir Windows Defender System Guard]( https://docs.microsoft.com/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows).
Windows Defender Credential Guard | Windows Defender Credential Guard utilise la sécurité basée sur la virtualisation pour isoler les secrets afin que seuls les logiciels système privilégiés y accèdent. Pour plus d’informations, [voir Windows Defender System Guard]( https://docs.microsoft.com/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows).
Microsoft Defender pour le point de terminaison - Détection et réponse des points de terminaison | Les opérations de sécurité du bureau géré Microsoft répondent aux alertes et prennent des mesures pour corriger les menaces à l’aide de la détection et de la réponse des points de terminaison. Pour plus d’informations, [voir Microsoft Defender for Endpoint - Endpoint Detection and Response](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response).
Microsoft Defender pour le point de terminaison - Experts en menaces | Bureau géré Microsoft s’intègre aux informations et données des experts en menaces par le biais de notifications d’attaque ciblées. Vous devez fournir un consentement supplémentaire avant d’activer ce service. Pour plus d’informations, [voir Microsoft Defender for Endpoint - Threat Experts](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts).
Microsoft Defender pour le point de terminaison - Gestion des menaces et des vulnérabilités | Requis pour une utilisation future dans le plan de service Bureau géré Microsoft. Pour plus d’informations, voir Microsoft Defender pour le point de terminaison - Gestion des [menaces et des vulnérabilités.](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
Microsoft Defender pour le point de terminaison - Réduction de la surface d’attaque | La réduction de la surface d’attaque cible les comportements logiciels à risque qui sont souvent abusés par les attaquants. Pour plus d’informations, [voir Microsoft Defender pour le point de terminaison - Réduction de la surface d’attaque.](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)
Microsoft Defender pour le point de terminaison - Exploit Protection | Protège contre les programmes malveillants qui utilisent des attaques pour infecter les appareils et se propager en appliquant automatiquement des techniques d’atténuation des attaques aux processus et applications du système d’exploitation. Pour plus d’informations, [voir Microsoft Defender for Endpoint - Exploit Protection](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection).
Microsoft Defender pour le point de terminaison - Protection du réseau | La protection du réseau étend l’étendue de Microsoft Defender SmartScreen pour bloquer tout le trafic HTTP et HTTPS sortant qui tente de se connecter à des sources de réputation faible. Pour plus d’informations, [voir Microsoft Defender for Endpoint - Network Protection](/windows/security/threat-protection/microsoft-defender-atp/network-protection).
Protection contre la falsification Microsoft Defender | La Protection contre les falsifications Windows permet d’empêcher les paramètres de sécurité tels que la protection antivirus d’être modifiés. Pour plus d’informations, voir Protection contre la falsification [Microsoft Defender.](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection)
Protection antivirus en temps réel, heuristique et basée sur le comportement de l’antivirus Microsoft Defender | Recherchez toujours les menaces de fichier et de traitement qui ne sont peut-être pas détectées comme des programmes malveillants. Pour plus d’informations, voir Protection antivirus en temps réel, heuristique et basée sur le comportement [de l’antivirus Microsoft Defender.]( https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)
Protection cloud de l’antivirus Microsoft Defender | Fournit une protection automatisée et immédiate dynamique contre les menaces nouvelles et émergentes. Pour plus d’informations, [voir Protection de l’antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus)dans le cloud.
Microsoft Defender « Bloquer à la première vue » | Permet de détecter et de bloquer les nouveaux programmes malveillants lorsque Windows détecte un fichier suspect ou inconnu. Pour plus d’informations, [voir Microsoft Defender Bloquer à la première vue.](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus)
Applications potentiellement indésirables de Microsoft Defender AV | Les applications potentiellement indésirables sont utilisées pour bloquer les applications qui peuvent ralentir votre ordinateur, afficher des publicités inattendues ou, au pire, installer d’autres logiciels qui peuvent être inattendus ou indésirables. Pour plus d’informations, [voir Applications potentiellement indésirables de Microsoft Defender AV.](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
Windows Defender pare-feu avec fonctions avancées de sécurité | Le filtrage du trafic réseau à double sens basé sur l’hôte pour un appareil, Windows Defender Firewall bloque le trafic réseau non autorisé qui circule à l’entrée ou à l’sortie de l’appareil local. Pour plus d’informations, [voir Windows Defender Firewall with Advanced Security](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
Contrôle de compte d’utilisateur | Le contrôle de compte d’utilisateur bascule vers le Bureau sécurisé lorsqu’une tâche ou une action nécessite un accès de type compte administrateur. L’accès utilisateur standard est attribué aux utilisateurs du Bureau géré Microsoft lors de l’inscription. Pour plus d’informations, [voir Contrôle de compte d’utilisateur.](/windows/security/identity-protection/user-account-control/how-user-account-control-works)


## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

 |
 --- | ---
Enterprise Mobility + Security E3<br>Azure Active Directory Premium P2 |    Vous pouvez utiliser toutes les fonctionnalités d’Enterprise Mobility + Security E3 et Azure Active Directory Premium P2 pour gérer les appareils GDM.
Microsoft Cloud App Security |  Vous pouvez utiliser cette fonctionnalité facultative avec Bureau géré Microsoft.
Azure Information Protection P2  | Vous pouvez utiliser cette fonctionnalité facultative avec Bureau géré Microsoft.