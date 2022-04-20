---
title: Technologies associées de Bureau géré Microsoft
description: Cet article répertorie les technologies et applications utilisées dans Microsoft Managed Desktop.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: d7a7b6889451d83aaa6c2b53c1dce6ed035f9916
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945624"
---
# <a name="microsoft-managed-desktop-technologies"></a>Technologies associées de Bureau géré Microsoft

Cet article répertorie les technologies et applications utilisées dans Microsoft Managed Desktop.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Microsoft 365 Entreprise licence est requise pour tous les utilisateurs Microsoft Managed Desktop. Pour plus d’informations sur les exigences en matière de licences pour le service, consultez [Prérequis pour Microsoft Managed Desktop](../get-ready/prerequisites.md).

Cet article récapitule les composants inclus dans les licences Enterprise requises et comment le service utilise chaque composant avec Microsoft Managed Desktop appareils. Les rôles et responsabilités spécifiques pour chaque domaine sont détaillés dans Microsoft Managed Desktop documentation.

## <a name="office-365-e3-or-e5"></a>Office 365 E3 ou E5

| Produit | Informations |
| ----- | ----- |
| Applications Microsoft 365 pour les grandes entreprises (64 bits) | Les applications Office suivantes seront livrées avec l’appareil :<br><ul><li>Word</li><li>Excel</li><li>PowerPoint</li><li>Outlook</li><li>Éditeur</li><li>Accès</li><li>Skype Entreprise</li><li>OneNote</li></ul><br>Les versions complètes 64 bits de Microsoft Project et microsoft Visio ne sont pas incluses. Toutefois, étant donné que l’installation de ces applications dépend de la Microsoft 365 Apps pour l’installation Enterprise, Microsoft Managed Desktop créé des déploiements Microsoft Intune par défaut et des groupes de sécurité que vous pouvez utiliser pour déployer ces applications sur des utilisateurs sous licence. Pour plus d’informations, consultez [Installer Microsoft Project ou Microsoft Visio sur Microsoft Managed Desktop appareils](../get-started/project-visio.md). |
| OneDrive | Azure Active Directory’authentification unique est activée pour les utilisateurs lorsqu’ils se connectent pour la première fois à OneDrive.<br><br>La redirection de dossiers connus pour les dossiers Bureau, Document et Images est incluse. Ces dossiers sont activés et configurés par Microsoft Managed Desktop. |
| Store Apps | Microsoft Sway et Power BI ne sont pas livrés avec l’appareil. Ces applications sont disponibles en téléchargement à partir de Microsoft Store. |
| Win32 Applications | Teams n’est pas fourni avec l’appareil, mais il est empaqueté et fourni par Microsoft pour les appareils Microsoft Managed Desktop. Azure Information Protection Client n’est pas fourni avec l’appareil, mais vous pouvez le faire empaqueter pour le déploiement. |
| Applications Web | Les applications web suivantes ne sont pas fournies avec l’appareil : <ul><li>Yammer</li><li>Office dans un navigateur</li><li>Delve</li><li>Flow</li><li>StaffHub</li><li>Power Apps</li><li>Planificateur</li></ul> <br>Les utilisateurs peuvent accéder à la version web de ces applications avec un navigateur. |

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Entreprise E5 ou E3 avec Microsoft Defender pour point de terminaison

Nous recommandons à vos administrateurs informatiques de configurer les paramètres suivants.

> [!NOTE]
> Ces paramètres ne sont pas inclus ou gérés dans le cadre de Microsoft Managed Desktop.

| Produit | Informations |
| ----- | ----- |
| Windows Hello Entreprise | Vous devez implémenter Windows Hello Entreprise pour remplacer les mots de passe par une authentification à deux facteurs forte pour les appareils Microsoft Managed Desktop. Pour plus d’informations, consultez [Windows Hello Entreprise](/windows/security/identity-protection/hello-for-business/hello-identity-verification). |
| Virtualisation d’application | Vous pouvez déployer des packages Application Virtualization (App-V) à l’aide du client de gestion des applications Intune Win32. Pour plus d’informations, consultez [Application Virtualization](/windows/application-management/app-v/appv-technical-reference). |
| Protection contre la perte de données Microsoft Purview | Vous devez implémenter la protection contre la perte de données pour surveiller les actions effectuées sur les éléments que vous avez déterminés sensibles et pour empêcher le partage involontaire de ces éléments. Pour plus d’informations, consultez [la protection contre la perte de données](../../compliance/endpoint-dlp-learn-about.md). |

Fonctionnalités incluses et gérées dans le cadre de Microsoft Managed Desktop :

| Produit | Informations |
| ----- | ----- |
| Chiffrement de lecteur BitLocker | BitLocker Drive Encryption est utilisé pour chiffrer tous les lecteurs système. Pour plus d’informations, consultez [Chiffrement de lecteur BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview). |
| Windows Defender System Guard | Protège l’intégrité du système au démarrage et vérifie que l’intégrité du système a été véritablement maintenue. Pour plus d’informations, consultez [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Windows Defender Credential Guard | Windows Defender Credential Guard utilise la sécurité basée sur la virtualisation pour isoler les secrets afin que seuls les logiciels système privilégiés puissent y accéder. Pour plus d’informations, consultez [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Microsoft Defender pour point de terminaison - Détection et réponse des points de terminaison | Microsoft Managed Desktop Opérations de sécurité répond aux alertes et prend des mesures pour corriger les menaces à l’aide de la détection et de la réponse des points de terminaison. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison - Endpoint Detection and Response](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response). |
| Microsoft Defender pour point de terminaison - Experts en menaces | Microsoft Managed Desktop s’intègre aux informations et aux données d’Experts en menaces par le biais de notifications d’attaque ciblées. Vous devez fournir un consentement supplémentaire avant d’activer ce service. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison - Threat Experts](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts). |
| Microsoft Defender pour point de terminaison - Gestion des menaces et des vulnérabilités | Requis pour une utilisation ultérieure dans le plan de service Microsoft Managed Desktop. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison - Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). |
| Microsoft Defender pour point de terminaison - Réduction de la surface d’attaque | Cible les comportements logiciels à risque qui sont souvent abusés par les attaquants. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison - Réduction de la surface d’attaque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction). |
| Microsoft Defender pour point de terminaison - Exploit Protection | Protège contre les programmes malveillants qui utilisent des exploits pour infecter les appareils et se propage en appliquant automatiquement des techniques d’atténuation des attaques aux processus et applications du système d’exploitation. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison - Exploit Protection](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection). |
| Microsoft Defender pour point de terminaison - Protection réseau | Étend l’étendue de Microsoft Defender SmartScreen pour bloquer tout le trafic HTTP et HTTPS sortant qui tente de se connecter à des sources de faible réputation. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison - Protection réseau](/windows/security/threat-protection/microsoft-defender-atp/network-protection). |
| Protection contre les falsifications Microsoft Defender | Windows protection contre les falsifications est utilisée pour empêcher la modification des paramètres de sécurité tels que la protection antivirus. Pour plus d’informations, consultez [Microsoft Defender Tamper Protection](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection). |
| Antivirus Microsoft Defender protection antivirus basée sur le comportement, heuristique et en temps réel | Toujours activé pour rechercher les menaces de fichier et de traitement qui peuvent ne pas être détectées comme des programmes malveillants. Pour plus d’informations, consultez [Antivirus Microsoft Defender protection antivirus basée sur le comportement, heuristique et en temps réel](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md). |
| Antivirus Microsoft Defender protection fournie par le cloud | Fournit une protection dynamique quasi instantanée et automatisée contre les menaces nouvelles et émergentes. Pour plus d’informations, consultez [Antivirus Microsoft Defender Protection fournie par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus). |
| Microsoft Defender pour point de terminaison - « Bloquer à la première consultation » | Fournit la détection et le blocage de nouveaux programmes malveillants lorsque Windows détecte un fichier suspect ou inconnu. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison - Bloquer à la première consultation](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus). |
| Antivirus Microsoft Defender applications potentiellement indésirables | Permet de bloquer les applications qui peuvent entraîner l’exécution lente de votre machine, d’afficher des publicités inattendues ou, au pire, d’installer d’autres logiciels qui peuvent être inattendus ou indésirables. Pour plus d’informations, consultez [Antivirus Microsoft Defender applications potentiellement indésirables](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus). |
| pare-feu Windows Defender avec sécurité avancée | Le filtrage du trafic réseau bidirectionnel basé sur l’hôte pour un appareil, Windows Defender Pare-feu bloque le trafic réseau non autorisé entrant ou sortant de l’appareil local. Pour plus d’informations, consultez [Windows Defender Pare-feu avec Advanced Security](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). |
| Contrôle de compte d’utilisateur | Le contrôle de compte d’utilisateur bascule vers le Bureau sécurisé lorsqu’une tâche ou une action nécessite l’accès au type de compte administrateur. Microsoft Managed Desktop utilisateurs se voient attribuer un accès utilisateur standard lors de l’inscription. Pour plus d’informations, consultez [Contrôle de compte d’utilisateur](/windows/security/identity-protection/user-account-control/how-user-account-control-works). |

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

| Produit | Informations |
| ----- | ----- |
| Enterprise Mobility + Security E3<br><br>Azure Active Directory Premium P2 | Vous pouvez utiliser toutes les fonctionnalités de Enterprise Mobility + Security E3 pour gérer les appareils GPM.<br><br>Vous pouvez utiliser Azure Active Directory Premium P2 comme fonctionnalité facultative avec Microsoft Managed Desktop. |
| Microsoft Defender for Cloud Apps | Vous pouvez utiliser cette fonctionnalité facultative avec Microsoft Managed Desktop.
| Azure Information Protection P2  | Vous pouvez utiliser cette fonctionnalité facultative avec Microsoft Managed Desktop.
