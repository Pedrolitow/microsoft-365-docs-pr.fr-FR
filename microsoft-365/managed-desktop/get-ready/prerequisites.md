---
title: Configuration requise pour le Bureau géré Microsoft
description: Licences, comptes Azure, paramètres d’authentification et paramètres Microsoft 365 à configurer avant de s’inscrire au Bureau géré Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 79ae949d9624021121492edb811a4ea5bfcc729a
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49659139"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Configuration requise pour le Bureau géré Microsoft

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure); do not delete.-->
<!--from Prerequisites -->

Cette rubrique décrit les exigences d’infrastructure que vous devez respecter pour garantir la réussite avec Bureau géré Microsoft. 


Domaine | Détails des conditions préalables
--- | ---
Licences |Bureau géré Microsoft requiert la licence Microsoft 365 E3 avec Microsoft Defender pour endpoint et Azure Active Directory Premium 2 (ou équivalents).<br>Pour plus d’informations sur les plans de service spécifiques, voir [plus d’informations](#more-about-licenses) sur les licences dans cette rubrique.<br>Pour plus d’informations sur les licences disponibles, voir [Licences Microsoft 365.](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)
Connectivité |  Tous les appareils Bureau géré Microsoft nécessitent une connectivité à de nombreux points de terminaison de service Microsoft à partir du réseau d’entreprise.<br><br>Pour obtenir la liste complète des ADRESSES ET URL requises, voir [Configuration réseau.](../get-ready/network.md) 
Azure Active Directory |    Azure Active Directory (Azure AD) doit être la source d’autorité pour tous les comptes d’utilisateurs, ou les comptes d’utilisateur doivent être synchronisés à partir d’Active Directory local à l’aide de la dernière version prise en charge d’Azure AD Connect.<br><br>[L’itinérance de l’état](https://docs.microsoft.com/azure/active-directory/devices/enterprise-state-roaming-overview) d’entreprise doit être activée pour les utilisateurs du Bureau géré Microsoft.<br><br>Pour plus d’informations, [voir Azure AD Connect.](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-azure-ad-connect)<br><br>Pour plus d’informations sur les versions d’Azure AD Connect prise en charge, voir l’historique des versions [d’Azure AD Connect:Version.](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)
Authentification |    Si Azure AD n’est pas la source de l’authentification principale pour les comptes d’utilisateurs, vous devez configurer l’un de ces éléments dans Azure AD Connect :<br>- Synchronisation de hachage de mot de passe<br>- Authentification directe<br>- Un fournisseur d’identité externe (y compris Windows Server ADFS et les IDP non-Microsoft) configuré pour répondre aux exigences d’intégration Azure AD. Pour plus [d’informations,](https://www.microsoft.com/download/details.aspx?id=56843) voir les recommandations. <br><br>Lors de la définition des options d’authentification avec Azure AD Connect, l’écriture écriture par mot de passe est également recommandée. Pour plus d’informations, consultez [l’écriture écriture par mot de passe.](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-writeback) <br><br>Si un fournisseur d’identité externe est implémenté, vous devez valider la solution :<br>- Répond aux exigences d’intégration d’Azure AD<br>- Prend en charge l’accès conditionnel Azure AD, qui permet la configuration de la stratégie de conformité des appareils de bureau géré Microsoft<br>- Active l’inscription des appareils et l’utilisation des services ou fonctionnalités Microsoft 365 requis dans le cadre du Bureau géré Microsoft <br><br>Pour plus d’informations sur les options d’authentification avec Azure AD, consultez les options de connexion utilisateur [Azure AD Connect.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-user-signin)
Microsoft 365 | OneDrive Entreprise doit être activé pour les utilisateurs de Bureau géré Microsoft.<br><br>Bien qu’il ne soit pas nécessaire de s’inscrire au Bureau géré Microsoft, nous vous recommandons vivement de migrer les services suivants vers le cloud :<br>- Courrier électronique : migrer vers des boîtes aux lettres en nuage, Exchange Online ou configurer avec Exchange Online hybride avec Exchange 2013 ou version supérieure, en local.<br>- Fichiers et dossiers : migrer vers OneDrive Entreprise ou SharePoint Online.<br>- Outils de collaboration en ligne : migrer vers Teams.
Gestion des périphériques | Les appareils Bureau géré Microsoft nécessitent une gestion à l’aide de Microsoft Intune. Intune doit être définie en tant qu’autorité de gestion des périphériques mobiles.<br><br>Pour plus d’informations, [voir Microsoft Intune.](https://www.microsoft.com/cloud-platform/microsoft-intune) 
Sauvegarde et récupération des données |  Bureau géré Microsoft requiert la synchronisation des fichiers avec OneDrive Entreprise pour la protection. Les fichiers non synchronisés avec OneDrive Entreprise ne sont pas garanties par le Bureau géré Microsoft et peuvent être perdus lors des échanges d’appareils ou des appels de support nécessitant une réinitialisation de l’appareil.<br><br>Bien que cela ne soit pas obligatoire, Bureau géré Microsoft recommande vivement la migration des lecteurs réseau mappés vers la solution cloud appropriée. Pour plus d’informations, voir Préparer les lecteurs [mappés pour le Bureau géré Microsoft](mapped-drives.md)

Lorsque vous êtes prêt à commencer avec bureau géré Microsoft, contactez votre gestionnaire de comptes Microsoft. 

## <a name="more-about-licenses"></a>En savoir plus sur les licences

Bureau géré Microsoft requiert certaines options de licence pour fonctionner. Pour plus [d’informations](../intro/technologies.md) sur l’utilisation de ces licences, voir les technologies bureau géré Microsoft.

> [!TIP]
> Pour attribuer ces options de licence à des utilisateurs spécifiques, nous vous recommandons de tirer parti de la fonctionnalité de licence basée sur les groupes [d’Azure](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal) Active Directory.

- Azure Active Directory Premium P2
- Microsoft Intune 
- Windows 10 Entreprise  
- Microsoft Defender pour point de terminaison
- Applications Microsoft 365 for entreprise
- Microsoft Teams
- [SharePoint Online Plan 2](https://www.microsoft.com/microsoft-365/sharepoint/compare-sharepoint-plans)
- [Exchange Online Plan 2](https://www.microsoft.com/microsoft-365/exchange/compare-microsoft-exchange-online-plans) 


> [!TIP]
> Votre Gestionnaire de comptes Microsoft vous aidera à passer en revue vos licences et plans de service actuels et à trouver le chemin le plus efficace pour obtenir des licences ou des plans de service supplémentaires dont vous pourriez avoir besoin, tout en évitant la duplication.
