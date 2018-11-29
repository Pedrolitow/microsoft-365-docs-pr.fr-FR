---
title: Sécurité dans le bureau géré Microsoft
description: ''
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: jdeckerms
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 0ea0bbc6a8055ee8459fadd85a6fa4ddac14bdb7
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867464"
---
# <a name="security-in-microsoft-managed-desktop"></a>Sécurité dans le bureau géré Microsoft

<!--Security, also Onboarding doc: data handling/store, privileged account access -->

À l’aide de nombreuses technologies Microsoft, nous pouvons prévoir que les périphériques de bureau Microsoft sont sécurisés et que l’équipe les opérations de sécurité de bureau Microsoft peut empêcher, détecter et répondre aux menaces. Produits de sécurité tiers, applications et services ne sont pas autorisés. Microsoft s’appliquera une planification standard de stratégie pour vous assurer de périphériques, identité, réseau, et les données d’entreprise sont sécurisées et protégées.

Ces catégories de sécurité sont documentées dans les sections suivantes :

- [Sécurité des données](#data-security) - comment nous assurer que vos données sont stockée et répond aux exigences de sécurité Azure positionnement
- [Sécurité des périphériques](#device-security) – comment nous assurer que les périphériques de bureau Microsoft sont sécurisés
- [Sécurité de l’identité](#identity-security) – comment nous assurer que les utilisateurs de l’espace de travail moderne ne sont pas compromis
- [Sécurité du réseau](#network-security) – comment nous assurer un accès sécurisé aux ressources d’entreprise
- [Sécurité de l’information](#information-security) – comment nous assurer que les données d’entreprise est sécurisé
- [Accès de compte privilégié](#privileged-account-access) - comment nous restreindre l’accès

## <a name="data-security"></a>Sécurité des données

Données transmises à partir de votre client sont stockées dans des bases de données SQL Azure dans le client Microsoft hébergés aux États-Unis. Vos données sont stockées et répond aux exigences de sécurité Azure positionnement. 

Pour plus d’informations, voir [sécurité Microsoft Azure](https://www.microsoft.com/TrustCenter/Security/azure-security).

Cette liste répertorie les types de données transmises entre Microsoft et votre client. 

- À partir de Microsoft de votre client
    - Noms de groupe
    - Configuration de stratégie de sécurité
    - Commandes de périphérique
    - Comptes d’utilisateurs (msadmin, mstest, Microsoft gérées Desktop_soc_ro, Microsoft gérées Desktop_wdgsoc)
    - Affectation de licence E5 à 4 utilisateurs
    - Stratégies pour les sonneries de mise à jour de la mise à jour Windows
    - À l’avenir, autres fonctionnalités seront développées pour permettre la validation d’autres types de contenu, y compris des applications, des stratégies et paramètres de la configuration.
- À partir de votre client à Microsoft
    - Données de mise à jour, l’utilisation et la fiabilité des périphériques
    - Données de déploiement et la fiabilité d’application
    - Données de déploiement de stratégie de sécurité et de mise à jour
    - Utilisateurs affectés à des périphériques



## <a name="device-security"></a>Sécurité des périphériques

Pour empêcher les failles de sécurité, il est important de vérifier que tous les périphériques de bureau Microsoft sont sain et sécurisé. Il est également important pour nous pouvons détecter les périphériques défectueux et réduire le risque dès que possible.

Le tableau suivant répertorie les services fournis afin de périphériques de bureau Microsoft sont approuvés, sain et sécurisé.

Service | Description
--- | ---
Antivirus | Nous permet de garantir que :<br>-Windows Defender antivirus est installé et configuré<br>-Définitions Windows Defender antivirus sont à jour
Chiffrement de Volume complet |    Windows BitLocker est la solution de chiffrement des données pour les périphériques de bureau Microsoft.<br><br>Une fois qu’une organisation est onboarded dans le service, périphériques seront chiffrés à l’aide de Windows BitLocker avec intégrés Trust Platform Module (TPM) pour interdire l’accès aux données locales lorsque le périphérique est en mode veille ou inactif. 
Analyse |    Windows Defender avancée contre les menaces (Windows Defender DAV) est la solution pour tous les périphériques de bureau Microsoft de surveillance de menace de sécurité. Windows Defender DAV pour les entreprises à détecter, examiner et répondre aux menaces avancées dans leur réseau d’entreprise. Pour plus d’informations, voir [contre les menaces avancées Windows Defender.](https://docs.microsoft.com/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) 
Mises à jour logicielles |  Microsoft permet de garantir que les périphériques de bureau Microsoft sont toujours sécurisés avec la dernière mise à jour de sécurité, pour Windows et Office, à l’aide de Windows Update pour les entreprises.
Récupération |  Données d’entreprise sont stockées sur OneDrive entreprise et peuvent être facilement restaurées pour les périphériques de bureau Microsoft. Pour plus d’informations, voir [OneDrive for Business.](https://support.office.com/article/Restore-a-previous-version-of-a-file-in-OneDrive-159cad6d-d76e-4981-88ef-de6e96c93893?ui=en-US&rs=en-US&ad=US) 



## <a name="identity-security"></a>Sécurité d’identité

Gestion des identités et l’accès protège les actifs de l’entreprise et les données critiques. Azure Active Directory (AD Azure) fournit des services d’identité dans le nuage et authentification basée sur le cloud activer qui garantit que seules les personnes approuvés peut accéder à des ressources d’entreprise à partir de périphériques de bureau Microsoft.

Service | Description
--- | ---
Fournisseur d’authentification de niveau entreprise |  Les éditions AD Premium Azure utilisées par Microsoft vous fournissent un service de haute disponibilité hébergé dans les centres de données dispersés géographiquement. Le service gère les milliards d’authentifications chaque jour à partir de plus de 200 millions d’utilisateurs actifs et vous donne un SLA de 99,9 %.
Authentification biométrique |  Hello Windows permet aux utilisateurs d’ouvrir une session à l’aide de leur image ou un code confidentiel, rendant les mots de passe plus difficile à oubliez ou voler. Cela peut nécessiter un travail supplémentaire pour configurer. Pour plus d’informations, voir [Windows Hello.](https://docs.microsoft.com/windows-hardware/design/device-experiences/windows-hello)
Authentification à plusieurs facteurs | L’authentification multifacteur Azure empêche l’accès non autorisé à locaux et en nuage des applications en fournissant un niveau supplémentaire de l’authentification à l’aide d’un téléphone mobile, ainsi que libre-service de réinitialisation de mot de passe. 
Autorisation de l’utilisateur standard |  Pour protéger le système et rendre plus sécurisé, l’utilisateur sera attribué des autorisations utilisateur Standard. Il est affecté dans le cadre de l’expérience d’out-of-box pilote Windows.



## <a name="network-security"></a>Sécurité réseau

Les clients sont responsables de la sécurité réseau. 

Service | Description
--- | ---
VPN | Clients possèdent leur infrastructure VPN, afin de garantir des ressources d’entreprise limitées peuvent être exposés à l’extérieur de l’intranet.<br><br>Configuration minimale requise : bureau Microsoft Managed requiert une solution VPN pris en charge et compatible Windows 10. Si votre organisation a besoin d’une solution VPN, il doit prendre en charge Windows 10 et package et déployer via Intune. Pour plus d’informations, contactez votre éditeur de logiciels.<br><br>Recommandation :<br>-Microsoft recommande une solution VPN moderne qui peut être facilement déployée via Intune aux profils VPN de type push. Cela offre un moyen de-on, transparent, fiable et sécurisé pour l’accès réseau d’entreprise. Pour plus d’informations, consultez Paramètres VPN dans Intune.<br>-Les clients VPN épais ou des clients hérités VPN, ne sont pas recommandées par Microsoft lors de l’utilisation de bureau Microsoft comme il peut avoir un impact sur l’environnement de l’utilisateur final.<br>-Microsoft recommande que le trafic web sortant accède directement à Internet sans passer par le réseau VPN pour éviter les problèmes de performances.<br>-Dans l’idéal, Microsoft recommande l’utilisation d’Azure Active Directory Application Proxy au lieu d’un réseau privé virtuel.


## <a name="information-security"></a>Sécurité des informations

Les clients peuvent configurer ces services facultatifs pour protéger les ressources de valeur élevée d’entreprise. 

Service | Description
--- | ---
Accès conditionnel |    Autoriser l’accès aux ressources d’entreprise et des services uniquement lorsque le périphérique est compatible.
Récupération des données  | Les informations stockées dans les dossiers de clés sur l’appareil sont sauvegardées vers OneDrive pour Bbusiness. Ordinateur de bureau Microsoft n’est pas chargé de données n’est pas synchronisée avec OneDrive entreprise. 
Protection des informations Windows |    Pour les entreprises qui nécessitent des hauts niveaux de sécurité de l’information, nous vous recommandons de [Protection des informations](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) et [Azure la Protection des informations.](https://www.microsoft.com/cloud-platform/azure-information-protection). 


## <a name="privileged-account-access"></a>Accès de compte privilégié

Aujourd'hui, nous restreindre l’accès pour les informations d’identification de client MSAdmin et l’application par le biais de ces mécanismes :

- **Opérateurs** – Microsoft plein-temps-employés situé dans le fuseau horaire est terminé une vérification périodique d’arrière-plan et de sécurité.
- **Identité de l’opérateur** – protégée conformément aux normes définies par Microsoft. Pour plus d’informations, voir [Gestion des identités d’utilisateur et sécuriser l’accès à Microsoft](https://www.microsoft.com/itshowcase/Article/Content/931/Managing-user-identities-and-secure-access-at-Microsoft). 
- **La journalisation** est effectuée dans l’environnement de l’opérateur et dans le client du client. Journaliser les données et les informations personnelles sont conservées dans les environnements respectifs et ne traversent pas les environnements. 

