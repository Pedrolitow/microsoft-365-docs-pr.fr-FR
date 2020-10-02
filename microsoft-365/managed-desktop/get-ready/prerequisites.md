---
title: Configuration requise pour le Bureau géré Microsoft
description: Licences, comptes Azure, paramètres d’authentification et paramètres Microsoft 365 pour configurer avant l’inscription dans le bureau géré Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: d5aaba3d1f8606ab69b360d5916a5c9a8a653a14
ms.sourcegitcommit: e87015bf29ad15688137c785d93f2c79ca3208f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "48343282"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Configuration requise pour le Bureau géré Microsoft

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure); do not delete.-->
<!--from Prerequisites -->

Cette rubrique décrit les exigences en matière d’infrastructure que vous devez respecter pour garantir la réussite avec le bureau géré Microsoft. 


Domaine | Détails des éléments prérequis
--- | ---
Licence |Microsoft Managed Desktop requiert la licence Microsoft 365 E3 avec Microsoft Defender pour Endpoint et Azure Active Directory Premium 2 (ou équivalents).<br>Pour plus d’informations sur les plans de service spécifiques, voir en savoir [plus sur les licences](#more-about-licenses) dans cette rubrique.<br>Pour plus d’informations sur les licences disponibles, consultez la rubrique [Microsoft 365 Licensing](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).
Connectivité |  Tous les périphériques de bureau gérés Microsoft nécessitent une connectivité à de nombreux points de terminaison de service Microsoft à partir du réseau d’entreprise.<br><br>Pour obtenir la liste complète des adresses IP et des URL requises, voir [Configuration réseau](../get-ready/network.md). 
Azure Active Directory |    Azure Active Directory (Azure AD) doit être la source d’autorité pour tous les comptes d’utilisateur, ou les comptes d’utilisateur doivent être synchronisés à partir d’Active Directory local à l’aide de la dernière version prise en charge d’Azure AD Connect.<br><br>L’itinérance de l’état de l' [entreprise](https://docs.microsoft.com/azure/active-directory/devices/enterprise-state-roaming-overview) doit être activée pour les utilisateurs du bureau géré Microsoft.<br><br>Pour plus d’informations, reportez-vous à [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-azure-ad-connect).<br><br>Pour plus d’informations sur les versions Azure AD Connect prises en charge, reportez-vous à la rubrique [Azure ad Connect : version Release History](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history).
Authentification |    Si Azure AD n’est pas la source de l’authentification principale pour les comptes d’utilisateur, vous devez configurer l’un des éléments suivants dans Azure AD Connect :<br>-Synchronisation de hachage de mot de passe<br>-Authentification directe<br>-Fournisseur d’identité externe (y compris Windows Server ADFS et non-Microsoft fournisseurs) configuré pour répondre aux exigences d’intégration d’Azure AD. Pour plus d’informations, consultez les [instructions](https://www.microsoft.com/download/details.aspx?id=56843) . <br><br>Lors de la configuration des options d’authentification avec Azure AD Connect, l’écriture différée de mot de passe est également recommandée. Pour plus d’informations, consultez la rubrique [écriture différée du mot de passe](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-writeback). <br><br>Si un fournisseur d’identité externe est implémenté, vous devez valider la solution :<br>-Répondre aux exigences d’intégration d’Azure AD<br>-Prend en charge l’accès conditionnel Azure AD, qui permet de configurer la stratégie de conformité de l’appareil MMD<br>-Active l’enregistrement des appareils et l’utilisation des services ou des fonctionnalités Microsoft 365 requis dans le cadre du bureau géré Microsoft <br><br>Pour plus d’informations sur les options d’authentification avec Azure AD, reportez-vous à la rubrique [options de connexion de l’utilisateur Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-user-signin).
Microsoft 365 | OneDrive entreprise doit être activé pour les utilisateurs du bureau géré Microsoft.<br><br>Bien qu’il ne soit pas nécessaire de s’inscrire avec Microsoft Managed Desktop, nous vous recommandons vivement de migrer les services suivants vers le Cloud :<br>-Email : migrer vers des boîtes aux lettres en nuage, Exchange Online ou une configuration avec Exchange Online hybride avec Exchange 2013 ou version ultérieure, en local.<br>-Fichiers et dossiers : migrer vers OneDrive entreprise ou SharePoint Online.<br>-Outils de collaboration en ligne : migrer vers Teams.
Gestion des périphériques | Les périphériques de bureau gérés Microsoft nécessitent une gestion à l’aide de Microsoft Intune. Intune doit être défini en tant qu’autorité de gestion des appareils mobiles.<br><br>Pour plus d’informations, consultez la rubrique [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune). 
Sauvegarde et récupération des données |  Le bureau géré Microsoft requiert la synchronisation des fichiers avec OneDrive entreprise pour la protection. Tous les fichiers qui ne sont pas synchronisés avec OneDrive entreprise ne sont pas assurés par le bureau géré Microsoft et peuvent être perdus pendant les échanges d’appareils ou les appels de prise en charge exigeant une réinitialisation de l’appareil.<br><br>Bien que cela ne soit pas obligatoire, le bureau géré Microsoft recommande vivement la migration des lecteurs réseau mappés vers la solution cloud appropriée. Pour plus d’informations, consultez la rubrique [Prepare mapped Drives for Microsoft Managed Desktop](mapped-drives.md)

Lorsque vous êtes prêt à commencer à utiliser Microsoft Managed Desktop, contactez votre gestionnaire de compte Microsoft. 

## <a name="more-about-licenses"></a>En savoir plus sur les licences

Microsoft Managed Desktop requiert certaines options de licence pour fonctionner. Pour plus d’informations sur l’utilisation de ces licences, voir [Microsoft Managed Desktop Technologies](../intro/technologies.md) .

> [!TIP]
> Pour affecter ces options de licence à des utilisateurs spécifiques, nous vous recommandons de tirer parti de la fonctionnalité de gestion des [licences basée sur les groupes](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal) d’Azure Active Directory.

- Azure Active Directory Premium P2
- Microsoft Intune 
- Windows 10 Entreprise  
- Microsoft Defender pour le point de terminaison
- Applications Microsoft 365 for entreprise
- Microsoft Teams
- [SharePoint Online Plan 2](https://www.microsoft.com/microsoft-365/sharepoint/compare-sharepoint-plans)
- [Exchange Online Plan 2](https://www.microsoft.com/microsoft-365/exchange/compare-microsoft-exchange-online-plans) 


> [!TIP]
> Votre gestionnaire de compte Microsoft vous aide à consulter vos licences et plans de service actuels et à trouver le chemin le plus efficace pour obtenir les licences ou plans de service supplémentaires dont vous pouvez avoir besoin, tout en évitant la duplication.
