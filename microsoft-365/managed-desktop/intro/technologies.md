---
title: Technologies associées de Bureau géré Microsoft
description: Cet article répertorie les technologies et applications utilisées dans bureau géré Microsoft.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 4932a40455c8ed4d8fdfc0dfae99c8001e582ff4
ms.sourcegitcommit: c0cfb9b354db56fdd329aec2a89a9b2cf160c4b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50094866"
---
# <a name="microsoft-managed-desktop-technologies"></a>Technologies associées de Bureau géré Microsoft

Cet article répertorie les technologies et applications utilisées dans bureau géré Microsoft.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Les licences Microsoft 365 Entreprise sont requises pour tous les utilisateurs du Bureau géré Microsoft. Pour plus d’informations sur les conditions requises en matière de licences pour le service, voir [Prerequisites for Microsoft Managed Desktop](../get-ready/prerequisites.md).

Cet article récapitule les composants inclus dans les licences d’entreprise requises, avec une description de la façon dont le service utilise chaque composant avec les appareils bureau géré Microsoft. Les rôles et responsabilités spécifiques pour chaque domaine sont détaillés dans la documentation du Bureau géré Microsoft. 

## <a name="office-365-e3-or-e5"></a>Office 365 E3 ou E5
 |
 --- | ---
Applications Microsoft 365 pour les entreprises (64 bits) | Ces applications Office seront livrées avec l’appareil : Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype Entreprise, OneNote.<br><br>Les versions complètes 64 bits de Microsoft Project et Microsoft Visio ne sont pas incluses. Toutefois, étant donné que l’installation de ces applications dépend de l’installation des applications Microsoft 365 pour les entreprises, Bureau géré Microsoft a créé des déploiements et des groupes de sécurité Microsoft Intune par défaut que vous pouvez ensuite utiliser pour déployer ces applications pour les utilisateurs sous licence. Pour plus d’informations, voir [Installer Microsoft Project ou Microsoft Visio sur les appareils de bureau géré Microsoft.](../get-started/project-visio.md)
OneDrive |L’ion unique Azure Active Directory est activée pour les utilisateurs lorsqu’ils se connectent pour la première fois à OneDrive.<br><br>La redirection de dossiers connue pour les dossiers « Bureau », « Document » et « Images » est incluse ; activé et configuré par Bureau géré Microsoft.
Store Apps |    Microsoft Sway et Power BI ne sont pas livrés avec l’appareil. Ces applications sont disponibles en téléchargement à partir du Microsoft Store.
Win32 Applications |    Teams n’est pas fourni avec l’appareil, mais il est empaqueté et fourni par Microsoft pour les appareils bureau géré Microsoft. Le client Azure Information Protection n’est pas livré avec l’appareil, mais vous pouvez le faire empaqueté pour le déploiement.
Applications Web |  Yammer, Office dans un navigateur, Delve, Flow, StaffHub, PowerApps et planner ne sont pas livrés avec l’appareil. Les utilisateurs peuvent accéder à la version web de ces applications avec un navigateur.



## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Entreprise E5 ou E3 avec Microsoft Defender pour point de terminaison
Recommandé
 |
 --- | ---
[Windows Hello Entreprise](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification) | Nous recommandons aux clients d’implémenter Windows Hello Entreprise pour remplacer les mots de passe par une authentification forte à deux facteurs utilisée sur les appareils bureau géré Microsoft.
[Application Virtualization](https://docs.microsoft.com/windows/application-management/app-v/appv-technical-reference) | Les clients peuvent déployer des packages Application Virtualization (App-V) à l’aide du client de gestion des applications Intune Win32.
[Protection contre la perte de données Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/endpoint-dlp-learn-about) | Les clients sont recommandés d’implémenter la protection contre la perte de données Microsoft 365 (DLP) pour surveiller les actions entreprises sur les éléments que vous avez déterminés comme sensibles et pour empêcher le partage involontaire de ces éléments.   

Inclus et géré dans le service
 |
 --- | ---
[Chiffrement de lecteur BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview) | Le chiffrement de lecteur BitLocker est utilisé pour chiffrer tous les lecteurs système. 
[Windows Defender System Guard]( https://docs.microsoft.com/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows) | Protège l’intégrité du système au démarrage et confirme que l’intégrité du système a réellement été conservée.
[Windows Defender Credential Guard]( https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard) | Windows Defender Credential Guard utilise la sécurité basée sur la virtualisation pour isoler les secrets afin que seuls les logiciels système privilégiés y accèdent.
[Microsoft Defender pour point de terminaison | Détection et réponse des points de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) |     Les opérations de sécurité du bureau géré Microsoft répondent aux alertes et prennent des mesures pour corriger les menaces à l’aide de la détection et de la réponse des points de terminaison.
[Microsoft Defender pour point de terminaison | Experts en matière de menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts) | Bureau géré Microsoft s’intègre aux informations et données des experts en menaces par le biais de notifications d’attaque ciblées. Les clients doivent fournir un consentement supplémentaire avant d’activer ce service.  
[Microsoft Defender pour point de terminaison | Gestion des menaces et des vulnérabilités](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) | Requis pour une utilisation future dans le plan de service Bureau géré Microsoft.
[Microsoft Defender pour point de terminaison | Réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction) | La réduction de la surface d’attaque cible les comportements logiciels à risque qui sont souvent abusés par les attaquants.
[Microsoft Defender pour point de terminaison | Exploit Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) | Protège contre les programmes malveillants qui utilisent des attaques pour infecter les appareils et se propager en appliquant automatiquement des techniques d’atténuation des attaques aux processus et applications du système d’exploitation.
[Microsoft Defender pour point de terminaison | Protection du réseau](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/network-protection) | La protection du réseau étend l’étendue de Microsoft Defender SmartScreen pour bloquer tout le trafic HTTP sortant qui tente de se connecter à des sources de faible réputation.
[Protection contre la falsification Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) | La Protection contre les falsifications Windows permet d’empêcher les paramètres de sécurité tels que la protection antivirus d’être modifiés.
[Protection antivirus en temps réel, heuristique et basée sur le comportement de l’antivirus Microsoft Defender]( https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) | Recherchez toujours les menaces de fichier et de traitement qui ne sont peut-être pas détectées comme des programmes malveillants.
[Protection de l’antivirus Microsoft Defender dans le cloud](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus) | Fournit une protection automatisée et immédiate dynamique contre les menaces nouvelles et émergentes.
[Microsoft Defender Bloquer à la première vue](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus) | Permet de détecter et de bloquer les nouveaux programmes malveillants lorsque Windows détecte un fichier suspect ou inconnu.
[Applications potentiellement indésirables de Microsoft Defender AV](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) | Les applications potentiellement indésirables (PUA) sont utilisées pour bloquer les applications qui peuvent ralentir votre ordinateur, afficher des publicités inattendues ou, au pire, installer d’autres logiciels qui peuvent être inattendus ou indésirables.
[Windows Defender pare-feu avec fonctions avancées de sécurité](https://docs.microsoft.com/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) | Le filtrage du trafic réseau à double sens basé sur l’hôte pour un appareil, Windows Defender Firewall bloque le trafic réseau non autorisé qui circule à l’entrée ou à l’sortie de l’appareil local.
[Contrôle de compte d’utilisateur](https://docs.microsoft.com/windows/security/identity-protection/user-account-control/how-user-account-control-works) | Le contrôle de compte d’utilisateur bascule vers le Bureau sécurisé lorsqu’une tâche ou une action nécessite l’accès au type de compte administrateur. L’accès utilisateur standard est attribué aux utilisateurs du Bureau géré Microsoft lors de l’inscription. 


## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

 |
 --- | ---
Enterprise Mobility + Security E3<br>Azure Active Directory Premium P2 |    Vous pouvez utiliser toutes les fonctionnalités d’Enterprise Mobility + Security E3 et Azure Active Directory Premium P2 pour gérer les appareils GDM.
Microsoft Cloud App Security |  Vous pouvez utiliser cette fonctionnalité facultative avec bureau géré Microsoft.
Azure Information Protection P2  | Vous pouvez utiliser cette fonctionnalité facultative avec bureau géré Microsoft.
