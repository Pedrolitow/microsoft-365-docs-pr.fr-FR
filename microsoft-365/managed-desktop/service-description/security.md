---
title: Sécurité dans le bureau géré Microsoft
description: ''
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 928d01e7386bedc500e984b9c2a3240c6229bb43
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867464"
---
# <a name="security-in-microsoft-managed-desktop"></a>Sécurité dans le bureau géré Microsoft

<!--Security, also Onboarding doc: data handling/store, privileged account access -->

Ordinateur de bureau Microsoft applique un ensemble de stratégies standard et utilise de nombreuses technologies Microsoft pour vous aider à des périphériques de bureau Microsoft sécurisés et données de l’entreprise stockées. Les domaines répertoriés ci-dessous sont détaillés plus loin :  

- [Sécurité des données](#data-security) - types de données collectées par Microsoft de bureau et où il est stocké en toute sécurité
- [Sécurité des périphériques](#device-security) – sécurité et protection sur les périphériques de bureau Microsoft
- [Gestion des accès et identité](#identity-and-access-management) – gestion sécurisée utilisent des périphériques via les services d’identité Azure Active Directory
- [Sécurité du réseau](#network-security) – informations de réseau privé virtuel et de bureau Microsoft recommandé de solution et les paramètres
- [Sécurité des informations](#information-security) – facultatifs services disponibles pour renforcer la protection des informations sensibles 

## <a name="data-security"></a>Sécurité des données

Les données collectées à partir de clients de client (ce qui permet les opérations et des services informatiques de bureau géré Microsoft) sont stockées dans des bases de données SQL Azure dans le client Microsoft hébergées dans les États-Unis d’Amérique.

Pour plus d’informations, voir [sécurité Microsoft Azure](https://docs.microsoft.com/azure/security/azure-database-security-overview).

Vous trouverez ci-dessous les types de données transmises à partir de votre client :

- Données de mise à jour, l’utilisation et la fiabilité des périphériques
- Données de déploiement et la fiabilité d’application
- Données de déploiement de stratégie de sécurité et de mise à jour
- Utilisateurs affectés à des périphériques



## <a name="device-security"></a>Sécurité des périphériques

Ordinateur de bureau Microsoft s’assure que tous les périphériques gérés sont sécurisés et protégé et détecte les menaces dès que possible à l’aide des services suivants :

Service | Description
--- | ---
Antivirus | Windows Defender antivirus est installé et configuré<br>Les définitions de Windows Defender AV sont à jour
Chiffrement de Volume complet |    Windows BitLocker est la solution de chiffrement de volume pour les périphériques de bureau Microsoft.<br><br>Une fois qu’une organisation est onboarded dans le service, périphériques seront chiffrés à l’aide de Windows BitLocker avec intégrés Trust Platform Module (TPM) pour interdire l’accès aux données locales lorsque le périphérique est en mode veille ou inactif. 
Analyse |    Windows Defender avancée contre les menaces (Windows Defender DAV) est utilisé pour la surveillance des menaces de sécurité sur tous les périphériques de bureau Microsoft. Windows Defender DAV pour les entreprises à détecter, examiner et répondre aux menaces dans leur réseau d’entreprise. Pour plus d’informations, voir [contre les menaces avancées Windows Defender.](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) 
Mises à jour logicielles |  Périphériques de bureau Microsoft sont toujours sécurisés avec les dernières mises à jour de sécurité.
Configuration du périphérique d’informations sécurisé |   Ordinateur de bureau Microsoft implémente le Guide de sécurité de Microsoft. Pour plus d’informations, voir [des bases de sécurité Windows.](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)



## <a name="identity-and-access-management"></a>Gestion des identités et des accès

Gestion des identités et l’accès protège les actifs de l’entreprise et les données critiques. Ordinateur de bureau Microsoft configure les périphériques afin d’assurer une utilisation sécurisée avec Azure Active Directory (AD Azure) gestion des identités. Il est de la responsabilité du client pour conserver les informations exactes dans leur client Azure AD. 

Service | Description
--- | ---
Authentification biométrique |  Hello Windows permet aux utilisateurs d’ouvrir une session à l’aide de leur image ou un code confidentiel, rendant les mots de passe plus difficile à oubliez ou voler. Pour plus d’informations, voir [Windows Hello.](https://docs.microsoft.com/windows-hardware/design/device-experiences/windows-hello)
	Authentification multifacteur | L’authentification multifacteur Azure plus étroitement contrôle l’accès aux fonctions sensibles du service Microsoft de bureau en fournissant un niveau supplémentaire de l’authentification à l’aide d’un téléphone mobile, comme la réinitialisation du mot de passe bien en libre-service. 
Autorisation de l’utilisateur standard |  Pour protéger le système et rendre plus sécurisé, l’utilisateur sera attribué des autorisations utilisateur Standard. Il est affecté dans le cadre de l’expérience d’out-of-box pilote Windows.



## <a name="network-security"></a>Sécurité réseau

Les clients sont responsables de la sécurité réseau. 

Service | Description
--- | ---
VPN | Clients possèdent leur infrastructure VPN, afin de garantir des ressources d’entreprise limitées peuvent être exposés à l’extérieur de l’intranet.<br><br>Configuration minimale requise : bureau Microsoft Managed requiert une solution VPN pris en charge et compatible Windows 10. Si votre organisation a besoin d’une solution VPN, il doit prendre en charge Windows 10 et package et déployer via Intune. Pour plus d’informations, contactez votre éditeur de logiciels.<br><br>Recommandation :<br>-Microsoft recommande une solution VPN moderne qui peut être facilement déployée via Intune aux profils VPN de type push. Cela offre un moyen de-on, transparent, fiable et sécurisé pour l’accès réseau d’entreprise. Pour plus d’informations, voir [[paramètres VPN dans Intune]](https://docs.microsoft.com/intune/vpn-settings-configure).<br>-Les clients VPN épais ou des clients hérités VPN, ne sont pas recommandées par Microsoft lors de l’utilisation de bureau Microsoft comme il peut avoir un impact sur l’environnement de l’utilisateur final.<br>-Microsoft recommande que le trafic web sortant accède directement à Internet sans passer par le réseau VPN pour éviter les problèmes de performances.<br>-Dans l’idéal, Microsoft recommande l’utilisation d’Azure Active Directory Application Proxy au lieu d’un réseau privé virtuel.


## <a name="information-security"></a>Sécurité des informations

Les clients peuvent configurer ces services facultatifs pour protéger les ressources de valeur élevée d’entreprise. 

Service | Description
--- | ---
Récupération des données  | Les informations stockées dans les dossiers de clés sur l’appareil sont sauvegardées vers OneDrive entreprise. Ordinateur de bureau Microsoft n’est pas chargé de données n’est pas synchronisée avec OneDrive entreprise. 
Protection des informations Windows |    Pour les entreprises qui nécessitent des hauts niveaux de sécurité de l’information, nous vous recommandons de [Protection des informations](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) et [Azure la Protection des informations.](https://www.microsoft.com/cloud-platform/azure-information-protection). 

