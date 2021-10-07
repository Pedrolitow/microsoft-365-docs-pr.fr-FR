---
title: Configuration requise pour le Bureau géré Microsoft
description: Licences, comptes Azure, paramètres d’authentification et paramètres de Microsoft 365 à configurer avant de s’inscrire Microsoft Manged Desktop
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 71b5491ac619fd48a68cb2ee4f3b5d82512e2262
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60152453"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Configuration requise pour le Bureau géré Microsoft

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure); do not delete.-->
<!--from Prerequisites -->

Cette rubrique décrit les exigences d’infrastructure que vous devez respecter pour garantir la réussite de Microsoft Manged Desktop.


Zone | Détails des conditions préalables
--- | ---
Licences |Microsoft Manged Desktop nécessite la licence Microsoft 365 E3 avec Microsoft Defender pour le point de terminaison (ou des équivalents) attribué à vos utilisateurs.<br>Pour plus d’informations sur les plans de service spécifiques, voir [plus d’informations](#more-about-licenses) sur les licences dans cette rubrique.<br>Pour plus d’informations sur les licences disponibles, [voir Microsoft 365 licences.](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans)
Connectivité | Tous les Microsoft Manged Desktop nécessitent une connectivité à de nombreux points de terminaison de service Microsoft à partir du réseau d’entreprise.<br><br>Pour obtenir la liste complète des ADRESSES ET URL requises, voir [Configuration réseau.](../get-ready/network.md) 
Azure Active Directory | Azure Active Directory (Azure AD) doit être la source d’autorité pour tous les comptes d’utilisateurs ou les comptes d’utilisateur doivent être synchronisés à partir d’Active Directory local à l’aide de la dernière version prise en charge d’Azure AD Connecter.<br><br>Pour plus d’informations, [voir Azure AD Connecter](/azure/active-directory/hybrid/whatis-azure-ad-connect).<br><br>Pour plus d’informations sur les versions de Connecter Azure AD, consultez l’historique des versions [d’Azure AD Connecter:Version.](/azure/active-directory/hybrid/reference-connect-version-history)
Authentification | Si Azure AD n’est pas la source de l’authentification principale pour les comptes d’utilisateurs, vous devez configurer l’un de ces éléments dans Azure AD Connecter :<br>- Synchronisation de hachage de mot de passe<br>- Authentification directe<br>- Un fournisseur d’identité externe (y compris Windows Server ADFS et les fournisseurs de services de sécurité non Microsoft) configurés pour répondre aux exigences d’intégration Azure AD. Pour plus [d’informations,](https://www.microsoft.com/download/details.aspx?id=56843) voir les recommandations. <br><br>Lors de la définition des options d’authentification avec Azure AD Connecter, l’écriture écriture par mot de passe est également recommandée. Pour plus d’informations, consultez [l’écriture écriture par mot de passe.](/azure/active-directory/authentication/howto-sspr-writeback) <br><br>Si un fournisseur d’identité externe est implémenté, vous devez valider la solution :<br>- Répond aux exigences d’intégration d’Azure AD<br>- Prend en charge l’accès conditionnel Azure AD, qui permet de configurer la stratégie Microsoft Manged Desktop conformité des appareils<br>- Permet l’inscription des appareils et l’utilisation Microsoft 365 services ou fonctionnalités requis dans le cadre de Microsoft Manged Desktop <br><br>Pour plus d’informations sur les options d’authentification avec Azure AD, voir Azure AD Connecter options de [authentification de l’utilisateur.](/azure/active-directory/connect/active-directory-aadconnect-user-signin)
Microsoft 365 | OneDrive Entreprise être activée pour les utilisateurs Microsoft Manged Desktop utilisateurs.<br><br>Bien qu’il ne soit pas nécessaire de s’inscrire Microsoft Manged Desktop, nous vous recommandons vivement de migrer les services suivants vers le cloud :<br>- Courrier électronique : migrer vers des boîtes aux lettres en nuage, Exchange en ligne ou configurer avec Exchange Online Hybride avec Exchange 2013 ou version supérieure, en local.<br>- Fichiers et dossiers : migrer vers OneDrive Entreprise ou SharePoint Online.<br>- Outils de collaboration en ligne : migrer vers Teams.
Gestion des périphériques | Microsoft Manged Desktop appareils nécessitent une gestion à l’aide Microsoft Intune. Intune doit être définie en tant qu’autorité de gestion des périphériques mobiles.<br><br>Pour plus d’informations, [voir Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).
Sauvegarde et récupération des données | Microsoft Manged Desktop nécessite la synchronisation des fichiers avec OneDrive Entreprise protection. Les fichiers non synchronisés avec OneDrive Entreprise ne sont pas garantis par Microsoft Manged Desktop et peuvent être perdus pendant les échanges d’appareils ou les appels de support nécessitant une réinitialisation de l’appareil.<br><br>Bien que cela ne soit pas obligatoire, Microsoft Manged Desktop recommande vivement la migration des lecteurs réseau mappés vers la solution cloud appropriée. Pour plus d’informations, voir [Préparer les lecteurs Microsoft Manged Desktop](mapped-drives.md)

Lorsque vous êtes prêt à commencer à Microsoft Manged Desktop, contactez votre Gestionnaire de comptes Microsoft. 

## <a name="more-about-licenses"></a>En savoir plus sur les licences

Microsoft Manged Desktop nécessite certaines options de licence pour fonctionner. Pour [plus d Microsoft Manged Desktop sur](../intro/technologies.md) l’utilisation de ces licences, voir Microsoft Manged Desktop technologies de licence.

> [!TIP]
> Pour attribuer ces options de licence à des utilisateurs spécifiques, nous vous recommandons de tirer parti de la fonctionnalité de licence basée sur les groupes de Azure Active Directory. [](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)

- Azure Active Directory Premium P1
- Microsoft Intune
- Windows 10 Entreprise  
- Microsoft Defender pour point de terminaison
- Microsoft 365 Apps for enterprise
- Microsoft Teams
- [SharePoint Online Plan 2](https://www.microsoft.com/microsoft-365/sharepoint/compare-sharepoint-plans)
- [Exchange Online Plan 2](https://www.microsoft.com/microsoft-365/exchange/compare-microsoft-exchange-online-plans)

> [!TIP]
> Votre Gestionnaire de comptes Microsoft vous aidera à passer en revue vos licences et plans de service actuels et à trouver le chemin le plus efficace pour obtenir des licences ou des plans de service supplémentaires dont vous pourriez avoir besoin, tout en évitant la duplication.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Étapes pour vous préparer à la Microsoft Manged Desktop

1. Examiner les conditions préalables (cet article).
2. Exécutez les [outils d’évaluation de la préparation](readiness-assessment-tool.md).
1. Achetez [Portail d’entreprise](../get-started/company-portal.md).
1. Passez en revue les [prérequis pour les comptes invités](guest-accounts.md).
1. Vérifiez la[configuration réseau](network.md).
1. [Préparer les certificats et les profils réseau](certs-wifi-lan.md).
1. [Préparer l’accès utilisateur aux données](authentication.md).
1. [Préparer les applications](apps.md).
1. [Préparer les lecteurs mappés](mapped-drives.md).
1. [Préparer les ressources d’impression](printing.md).
1. [noms d’appareil](address-device-names.md) d’une adresse.