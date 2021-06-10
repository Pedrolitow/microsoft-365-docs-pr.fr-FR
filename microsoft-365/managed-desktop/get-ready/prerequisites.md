---
title: Configuration requise pour le Bureau géré Microsoft
description: Licences, comptes Azure, paramètres d’authentification et paramètres de Microsoft 365 à configurer avant de s’inscrire Bureau géré Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: e4469d8abcfa8308c64e2efa7f7dc4f0156e5718
ms.sourcegitcommit: b6763a8ab240fbdd56078a7c9452445d0c4b9545
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2021
ms.locfileid: "51957526"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Configuration requise pour le Bureau géré Microsoft

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure); do not delete.-->
<!--from Prerequisites -->

Cette rubrique décrit les exigences d’infrastructure que vous devez respecter pour garantir la réussite Bureau géré Microsoft. 


Domaine | Détails des conditions préalables
--- | ---
Licences |Bureau géré Microsoft nécessite la licence Microsoft 365 E3 avec Microsoft Defender pour point de terminaison (ou équivalents) attribué à vos utilisateurs.<br>Pour plus d’informations sur les plans de service spécifiques, voir [plus d’informations](#more-about-licenses) sur les licences dans cette rubrique.<br>Pour plus d’informations sur les licences disponibles, [voir Microsoft 365 licences.](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans)
Connectivité |  Tous les Bureau géré Microsoft nécessitent une connectivité à de nombreux points de terminaison de service Microsoft à partir du réseau d’entreprise.<br><br>Pour obtenir la liste complète des ADRESSES ET URL requises, voir [Configuration réseau.](../get-ready/network.md) 
Azure Active Directory |    Azure Active Directory (Azure AD) doit être la source d’autorité pour tous les comptes d’utilisateurs ou les comptes d’utilisateur doivent être synchronisés à partir d’Active Directory local à l’aide de la dernière version prise en charge d’Azure AD Connecter.<br><br>[Enterprise l’itinérance](/azure/active-directory/devices/enterprise-state-roaming-overview) d’état doit être activée pour Bureau géré Microsoft utilisateurs.<br><br>Pour plus d’informations, [voir Azure AD Connecter](/azure/active-directory/hybrid/whatis-azure-ad-connect).<br><br>Pour plus d’informations sur les versions de Connecter Azure AD, consultez l’historique des versions [d’Azure AD Connecter:Version.](/azure/active-directory/hybrid/reference-connect-version-history)
Authentification |    Si Azure AD n’est pas la source de l’authentification principale pour les comptes d’utilisateurs, vous devez configurer l’un de ces éléments dans Azure AD Connecter :<br>- Synchronisation de hachage de mot de passe<br>- Authentification directe<br>- Un fournisseur d’identité externe (y compris Windows Server ADFS et les fournisseurs de services de sécurité non Microsoft) configurés pour répondre aux exigences d’intégration Azure AD. Pour plus [d’informations,](https://www.microsoft.com/download/details.aspx?id=56843) voir les recommandations. <br><br>Lors de la définition des options d’authentification avec Azure AD Connecter, l’écriture écriture par mot de passe est également recommandée. Pour plus d’informations, consultez [l’écriture écriture par mot de passe.](/azure/active-directory/authentication/howto-sspr-writeback) <br><br>Si un fournisseur d’identité externe est implémenté, vous devez valider la solution :<br>- Répond aux exigences d’intégration d’Azure AD<br>- Prend en charge l’accès conditionnel Azure AD, qui permet de configurer la stratégie Bureau géré Microsoft conformité des appareils<br>- Permet à l’appareil d’inscrire et d’utiliser Microsoft 365 services ou fonctionnalités requis dans le cadre de Bureau géré Microsoft <br><br>Pour plus d’informations sur les options d’authentification avec Azure AD, voir Azure AD Connecter options de [authentification de l’utilisateur.](/azure/active-directory/connect/active-directory-aadconnect-user-signin)
Microsoft 365 | OneDrive Entreprise utilisateurs doivent être activés Bureau géré Microsoft utilisateurs.<br><br>Bien qu’il ne soit pas nécessaire de s’inscrire Bureau géré Microsoft, nous vous recommandons vivement de migrer les services suivants vers le cloud :<br>- Courrier électronique : migrer vers des boîtes aux lettres en nuage, Exchange en ligne ou configurer avec Exchange Online Hybride avec Exchange 2013 ou version supérieure, en local.<br>- Fichiers et dossiers : migrer vers OneDrive Entreprise ou SharePoint Online.<br>- Outils de collaboration en ligne : migrer vers Teams.
Gestion des appareils | Bureau géré Microsoft appareils nécessitent une gestion à l’aide Microsoft Intune. Intune doit être définie en tant qu’autorité de gestion des périphériques mobiles.<br><br>Pour plus d’informations, [voir Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune). 
Sauvegarde et récupération des données |  Bureau géré Microsoft les fichiers doivent être synchronisés avec les OneDrive Entreprise pour la protection. Les fichiers non synchronisés avec OneDrive Entreprise ne sont pas garantis par Bureau géré Microsoft et peuvent être perdus lors des échanges d’appareils ou des appels de support nécessitant une réinitialisation de l’appareil.<br><br>Bien que cela ne soit pas obligatoire, Bureau géré Microsoft recommande vivement la migration des lecteurs réseau mappés vers la solution cloud appropriée. Pour plus d’informations, voir [Préparer les lecteurs Bureau géré Microsoft](mapped-drives.md)

Lorsque vous êtes prêt à commencer à Bureau géré Microsoft, contactez votre Gestionnaire de comptes Microsoft. 

## <a name="more-about-licenses"></a>En savoir plus sur les licences

Bureau géré Microsoft nécessite certaines options de licence pour fonctionner. Pour [plus d Bureau géré Microsoft sur](../intro/technologies.md) l’utilisation de ces licences, voir Bureau géré Microsoft technologies de licence.

> [!TIP]
> Pour attribuer ces options de licence à des utilisateurs spécifiques, nous vous recommandons de tirer parti de la fonctionnalité de licence basée sur les groupes de Azure Active Directory. [](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)

- Azure Active Directory Premium P1
- Microsoft Intune 
- Windows 10 Entreprise  
- Microsoft Defender pour point de terminaison
- Applications Microsoft 365 for entreprise
- Microsoft Teams
- [SharePoint Online Plan 2](https://www.microsoft.com/microsoft-365/sharepoint/compare-sharepoint-plans)
- [Exchange Online Plan 2](https://www.microsoft.com/microsoft-365/exchange/compare-microsoft-exchange-online-plans) 


> [!TIP]
> Votre Gestionnaire de comptes Microsoft vous aidera à passer en revue vos licences et plans de service actuels et à trouver le chemin le plus efficace pour obtenir des licences ou des plans de service supplémentaires dont vous pourriez avoir besoin, tout en évitant la duplication.

## <a name="steps-to-get-ready"></a>Étapes pour vous préparer

1. Examiner [les conditions préalables pour Bureau géré Microsoft](prerequisites.md). (Cet article)
2. Utiliser [les outils d’évaluation de la préparation.](readiness-assessment-tool.md)
3. [Conditions préalables pour les comptes invité](guest-accounts.md)
4. [Configuration du réseau pour Bureau géré Microsoft](network.md)
5. [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft](certs-wifi-lan.md)
6. [Préparer l’accès aux ressources locales pour le Bureau géré Microsoft](authentication.md)
7. [Applications dans le Bureau géré Microsoft](apps.md)
8. [Préparer les lecteurs mappés pour le Bureau géré Microsoft](mapped-drives.md)
9. [Préparer des ressources d’impression pour le Bureau géré Microsoft](printing.md)
