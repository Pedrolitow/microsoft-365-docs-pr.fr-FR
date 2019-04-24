---
title: Sécurité dans le bureau géré Microsoft
description: ''
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: b91b646b00869827dfb2131e9df9db38a770d9df
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32278633"
---
# <a name="security-in-microsoft-managed-desktop"></a>Sécurité dans le bureau géré Microsoft

<!--Security, also Onboarding doc: data handling/store, privileged account access -->

Microsoft maNaged Desktop applique un ensemble standard de stratégies et utilise de nombreuses technologies Microsoft pour sécuriser les appareils de bureau gérés par Microsoft, les données d'entreprise stockées, et bien plus encore. Les zones répertoriées ci-dessous sont détaillées plus en détail:  

- [Sécurité des données](#data-security) : types de données collectées par le bureau géré Microsoft et emplacement de stockage sécurisé
- [Sécurité des appareils](#device-security) – sécurité et protection sur les appareils de bureau gérés Microsoft
- [Gestion des identités et des accès](#identity-and-access-management) : gestion de l'utilisation sécurisée des appareils via les services d'identité Azure Active Directory
- [Sécurité réseau](#network-security) – informations VPN et solution et paramètres recommandés pour Microsoft maNaged Desktop
- [Sécurité des informations](#information-security) – services disponibles en option pour protéger davantage les informations sensibles 

## <a name="data-security"></a>Sécurité des données

Les données collectées à partir de locataires client (qui activent les services et les opérations Microsoft maNaged Desktop IT) sont stockées dans des bases de données SQL Azure dans le client Microsoft hébergé aux États-Unis d'Amérique.

Pour plus d'informations, consultez la rubrique [Microsoft Azure Security](https://docs.microsoft.com/azure/security/azure-database-security-overview).

Voici les types de données transmis par votre client:

- Données de mise à jour des périphériques, d'utilisation et de fiabilité
- Données de fiabilité et de déploiement d'application
- Mise à jour et données de déploiement de stratégie de sécurité
- Utilisateurs affectés aux appareils



## <a name="device-security"></a>Sécurité de l'appareil

Microsoft maNaged Desktop garantit que tous les appareils gérés sont sécurisés et protégés, et détecte les menaces dès que possible à l'aide des services suivants:

Service | Description
--- | ---
Antivirus | L'antivirus Windows Defender est installé et configuré<br>Les définitions d'antivirus Windows Defender sont à jour
Chiffrement de volume complet |    Windows BitLocker est la solution de chiffrement de volume pour les appareils de bureau gérés par Microsoft.<br><br>Une fois qu'une organisation est intégrée au service, les appareils sont chiffrés à l'aide de Windows BitLocker avec le module de plateforme d'approbation intégré (TPM) pour empêcher l'accès non autorisé aux données locales lorsque l'appareil est en mode veille ou inversement. 
Surveillance |    Windows Defender Advanced Threat Protection (Windows Defender ATP) est utilisé pour la surveillance des menaces de sécurité sur tous les appareils de bureau gérés par Microsoft. Windows Defender ATP permet aux clients d'entreprise de détecter, d'examiner et de répondre aux menaces avancées dans leur réseau d'entreprise. Pour plus d'informations, consultez la rubrique [protection avancée contre les menaces Windows Defender.](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) 
Mises à jour du système d'exploitation |  Les périphériques de bureau gérés Microsoft sont toujours sécurisés avec les dernières mises à jour de sécurité.
Configuration d'appareil sécurisée |   Microsoft maNaged Desktop implémente la base de sécurité Microsoft. Pour plus d'informations, consultez la rubrique [Windows Security baselines.](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)



## <a name="identity-and-access-management"></a>Gestion des identités et des accès

La gestion des identités et des accès protège les ressources d'entreprise et les données critiques. Microsoft maNaged Desktop configure les appareils pour garantir une utilisation sécurisée avec les identités gérées Azure Active Directory (Azure AD). Il incombe au client de maintenir des informations précises dans son client Azure AD. 

Service | Description
--- | ---
Authentification biométrique |  Windows Hello permet aux utilisateurs de se connecter à l'aide de leur face ou d'un code confidentiel, ce qui rend les mots de passe plus difficiles à oublier ou à voler. Pour plus d'informations, consultez la rubrique [Windows Hello.](https://docs.microsoft.com/windows-hardware/design/device-experiences/windows-hello)
Authentification multifacteur | L'authentification multifacteur Azure contrôle plus étroitement l'accès aux fonctions sensibles du service bureau géré Microsoft en fournissant un niveau supplémentaire d'authentification à l'aide d'un téléphone mobile, ainsi qu'une réinitialisation du mot de passe en libre-service. 
Autorisation utilisateur standard |  Pour protéger le système et le sécuriser, l'utilisateur reçoit des autorisations d'utilisateur standard. Cela est affecté dans le cadre de l'expérience utilisateur Windows AutoPilot.



## <a name="network-security"></a>Sécurité réseau

Les clients sont responsables de la sécurité du réseau. 

Service | Description
--- | ---
VPN | Les clients possèdent leur infrastructure VPN, afin de s'assurer que les ressources d'entreprise limitées peuvent être exposées à l'extérieur de l'intranet.<br><br>Configuration minimale requise: Microsoft maNaged Desktop requiert une solution VPN compatible et prise en charge Windows 10. Si votre organisation a besoin d'une solution VPN, elle doit prendre en charge Windows 10 et être empaquetée et déployée via Intune. Pour plus d'informations, contactez votre éditeur de logiciel.<br><br>Conseille<br>-Microsoft recommande une solution VPN moderne pouvant être déployée facilement via Intune pour envoyer des profils VPN. Cela permet d'accéder aux réseaux d'entreprise de manière permanente, fiable et sécurisée. Pour plus d'informations, reportez-vous à [[VPN Settings in Intune]](https://docs.microsoft.com/intune/vpn-settings-configure).<br>-Les clients VPN épais, ou les clients VPN hérités, ne sont pas recommandés par Microsoft lors de l'utilisation du bureau géré Microsoft car cela peut avoir un impact sur l'environnement de l'utilisateur final.<br>-Microsoft recommande que le trafic Web sortant accède directement à Internet sans passer par le VPN pour éviter les problèmes de performances.<br>Pour l'idéal, Microsoft recommande l'utilisation du proxy d'application Azure Active Directory au lieu d'un VPN.


## <a name="information-security"></a>Sécurité des informations

Les clients peuvent configurer ces services facultatifs afin de protéger les biens d'entreprise à valeur élevée. 

Service | Description
--- | ---
Récupération de données  | Les informations stockées dans les dossiers clés sur l'appareil sont sauvegardées dans OneDrive entreprise. Le bureau géré Microsoft n'est pas responsable des données qui ne sont pas synchronisées avec OneDrive entreprise. 
Protection des informations Windows |    Pour les entreprises qui nécessitent des niveaux élevés de sécurité des informations, nous recommandons la protection des informations [Windows](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) et [Azure information protection.](https://www.microsoft.com/cloud-platform/azure-information-protection). 

