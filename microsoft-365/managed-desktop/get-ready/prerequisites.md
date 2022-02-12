---
title: Configuration requise pour le Bureau géré Microsoft
description: Licences, comptes Azure, paramètres d’authentification et paramètres de Microsoft 365 à configurer avant de s’inscrire Microsoft Manged Desktop
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 495aa7e505bdcec8b5848499ac688847afa129bc
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62765623"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Configuration requise pour le Bureau géré Microsoft

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure). DO NOT DELETE.-->
<!--from Prerequisites -->

Cet article décrit les exigences d’infrastructure que vous devez respecter pour garantir la réussite Microsoft Manged Desktop.

| Zone | Détails des conditions préalables |
| ----- | ----- |
| Licences | Microsoft Manged Desktop nécessite la licence Microsoft 365 E3 avec Microsoft Defender pour le point de terminaison (ou des équivalents) attribué à vos utilisateurs. <ul><li>Pour plus d’informations sur les plans de service spécifiques, voir [Plus d’informations sur les licences](#more-about-licenses).</li><li> Pour plus d’informations sur les licences disponibles, [voir Microsoft 365 licences.](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans)</li></ul>
| Connectivité | Tous les Microsoft Manged Desktop nécessitent une connectivité à de nombreux points de terminaison de service Microsoft à partir du réseau d’entreprise.<br><br> Pour obtenir la liste complète des ADRESSES ET URL requises, voir [Configuration du réseau](../get-ready/network.md).
| Azure Active Directory | Azure Active Directory (Azure AD) doit être la source d’autorité pour tous les comptes d’utilisateurs ou les comptes d’utilisateur doivent être synchronisés à partir d’Active Directory local à l’aide de la dernière version prise en charge de Azure AD Connecter. <ul><li>Pour plus d’informations, [voir Azure AD Connecter](/azure/active-directory/hybrid/whatis-azure-ad-connect).</li><li> Pour plus d’informations sur les versions Azure AD Connecter prise en charge, voir [Azure AD Connecter:Version release history](/azure/active-directory/hybrid/reference-connect-version-history).</li></ul>
| Authentification | Si Azure AD n’est pas la source d’authentification principale pour les comptes d’utilisateurs, vous devez configurer l’une des méthodes d’authentification suivantes dans Azure AD Connecter :<ul><li> Synchronisation de hachage de mot de passe.</li> <li> Authentification directe.</li><li>Un fournisseur d’identité externe (y compris Windows Server ADFS et les fournisseurs de services de sécurité non Microsoft) configurés pour répondre aux Azure AD’intégration requises. Pour plus d’informations, voir les [instructions](https://www.microsoft.com/download/details.aspx?id=56843).</li></ul> <br> Lors de la définition des options d’authentification Azure AD Connecter, l’écriture écriture par mot de passe est également recommandée. Pour plus d’informations, consultez [l’écriture écriture par mot de passe](/azure/active-directory/authentication/howto-sspr-writeback). <br><br> Si un fournisseur d’identité externe est implémenté, vous devez valider la solution :<ul><li>Répond aux Azure AD’intégration requises.</li><li>Prend Azure AD l’accès conditionnel, ce qui permet Microsoft Manged Desktop stratégie de conformité des appareils à configurer.</li><li>Active l’inscription des appareils, l’utilisation de services Microsoft 365 ou des fonctionnalités requises dans le cadre de Microsoft Manged Desktop.</li></ul> <br>Pour plus d’informations sur les options d’authentification Azure AD, voir Azure AD Connecter [options de authentification de l’utilisateur](/azure/active-directory/connect/active-directory-aadconnect-user-signin).
| Microsoft 365 | OneDrive Entreprise être activée pour les utilisateurs Microsoft Manged Desktop utilisateurs.<br><br>Bien qu’il ne soit pas nécessaire de s’inscrire Microsoft Manged Desktop, nous vous recommandons vivement de migrer les services suivants vers le cloud :<ul><li>Courrier électronique : migrez vers des boîtes aux lettres en nuage, Exchange en ligne ou configurez avec Exchange Online Hybride avec Exchange 2013 ou version supérieure, en local.</li><li>Fichiers et dossiers : migrez vers OneDrive Entreprise ou SharePoint Online.</li><li>Outils de collaboration en ligne : migrer vers Teams.</ul> |
| Gestion des périphériques | Microsoft Manged Desktop appareils nécessitent une gestion à l’aide Microsoft Intune. Intune doit être définie en tant qu’autorité de gestion des périphériques mobiles.<br><br> Pour plus d’informations, [voir Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).
| Sauvegarde et récupération des données | Microsoft Manged Desktop nécessite la synchronisation des fichiers avec OneDrive Entreprise protection. Les fichiers non synchronisés avec OneDrive Entreprise ne sont pas garantis par Microsoft Manged Desktop. Les fichiers peuvent être perdus lors des échanges de périphériques ou des appels de support nécessitant une réinitialisation de l’appareil.<br><br>Bien que cela ne soit pas obligatoire, Microsoft Manged Desktop recommande vivement la migration des lecteurs réseau mappés vers la solution cloud appropriée. Pour plus d’informations, voir [Préparer les lecteurs Microsoft Manged Desktop](mapped-drives.md)

Lorsque vous êtes prêt à commencer à Microsoft Manged Desktop, contactez votre Gestionnaire de comptes Microsoft.

## <a name="more-about-licenses"></a>En savoir plus sur les licences

Microsoft Manged Desktop nécessite certaines options de licence pour fonctionner. Voir [Microsoft Manged Desktop technologies de](../intro/technologies.md) licence pour plus d’informations sur l’utilisation de ces licences.

> [!TIP]
> Pour attribuer ces options de licence à des utilisateurs spécifiques, nous vous recommandons de [](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal) tirer parti de la fonctionnalité de licence basée sur les groupes de Azure Active Directory.

- Azure Active Directory Premium P1
- Microsoft Intune
- Windows 10 Entreprise  
- Microsoft Defender pour point de terminaison
- Applications Microsoft 365 for entreprise
- Microsoft Teams
- [SharePoint Online Plan 2](https://www.microsoft.com/microsoft-365/sharepoint/compare-sharepoint-plans)
- [Exchange Online Plan 2](https://www.microsoft.com/microsoft-365/exchange/compare-microsoft-exchange-online-plans)

> [!TIP]
> Votre Gestionnaire de comptes Microsoft vous aidera à passer en revue vos licences actuelles, vos plans de service et à trouver le chemin le plus efficace pour obtenir des licences ou des plans de service supplémentaires dont vous pourriez avoir besoin, tout en évitant la duplication.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Étapes pour vous préparer à la Microsoft Manged Desktop

1. Passer en revue les conditions préalables (cet article).
1. Exécutez les [outils d’évaluation de la préparation](readiness-assessment-tool.md).
1. Achetez [Portail d’entreprise](../get-started/company-portal.md).
1. Passez en revue les [prérequis pour les comptes invités](guest-accounts.md).
1. Vérifiez la[configuration réseau](network.md).
1. [Préparer les certificats et les profils réseau](certs-wifi-lan.md).
1. [Préparer l’accès utilisateur aux données](authentication.md).
1. [Préparer les applications](apps.md).
1. [Préparer les lecteurs mappés](mapped-drives.md).
1. [Préparer les ressources d’impression](printing.md).
1. [noms d’appareil](address-device-names.md) d’une adresse.
