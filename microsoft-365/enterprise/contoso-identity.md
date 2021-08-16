---
title: Identité de Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez comment Contoso tire parti de la solution de gestion des identités IDaaS et propose à ses employés une authentification basée sur le cloud, et une authentification fédérée à ses partenaires et ses clients.
ms.openlocfilehash: 9138e0743e5194e98213ab2d2c2bfe457500b0de
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58353791"
---
# <a name="identity-for-the-contoso-corporation"></a>Identité de Contoso Corporation

Microsoft fournit l’identité en tant que service (IDaaS) dans ses offres cloud via Azure Active Directory (Azure AD). Pour adopter Microsoft 365 entreprise, la solution Contoso IDaaS devait utiliser son fournisseur d’identité local et inclure l’authentification fédérée avec ses fournisseurs d’identité tiers existants.

## <a name="the-contoso-active-directory-domain-services-forest"></a>Forêt des services de domaine Active Directory contoso

Contoso utilise une seule forêt AD DS (Active Directory Domain Services) pour contoso com avec sept sous-domaines, un pour chaque région \. du monde. Le siège social, les centres régionaux et les succursales disposent de contrôleurs de domaine pour l’authentification locale et l’autorisation.

Voici la forêt Contoso avec des domaines régionaux pour les différentes régions du monde qui contiennent des centres régionaux.

![Forêt et domaines de Contoso dans le monde](../media/contoso-identity/contoso-identity-fig1.png)
 
Contoso a décidé d’utiliser les comptes et les groupes de la forêt contoso com pour l’authentification et l’autorisation pour ses charges Microsoft 365 charges de travail \. et services.

## <a name="the-contoso-federated-authentication-infrastructure"></a>Infrastructure d’authentification fédérée Contoso

Contoso autorise les éléments suivants :

- Les clients qui utilisent leurs comptes Microsoft, Facebook ou Google Mail pour se connectent au site web public de l’entreprise.
- Fournisseurs et partenaires qui utilisent leurs comptes LinkedIn, Salesforce ou Google Mail pour se connectent à l’extranet partenaire de l’entreprise.

Voici le DMZ Contoso contenant un site web public, un extranet partenaire et un ensemble de serveurs AD FS (Active Directory Federation Services). Le DMZ est connecté à Internet qui contient des clients, des partenaires et des services Internet.

![Prise en charge de Contoso pour l’authentification fédérée pour les clients et les partenaires](../media/contoso-identity/contoso-identity-fig2.png)
 
Les serveurs AD FS dans la DMZ facilitent l’authentification des informations d’identification client par leurs fournisseurs d’identité pour accéder au site web public et aux informations d’identification des partenaires pour l’accès à l’extranet du partenaire.

Contoso a décidé de conserver cette infrastructure et de la dédier à l’authentification des clients et des partenaires. Les architectes d’identité Contoso examinent la conversion de cette infrastructure en solutions [B2B](/azure/active-directory/b2b/hybrid-organizations) et [B2C](/azure/active-directory-b2c/solution-articles) Azure AD.

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>Identité hybride avec authentification directe pour l’authentification basée sur le cloud

Contoso souhaitait utiliser sa forêt AD DS sur site pour l’authentification Microsoft 365 ressources cloud. Il a décidé d’utiliser la synchronisation de hachage de mot de passe (PHS).

PHS synchronise la forêt AD DS sur site avec le client Azure AD de son Microsoft 365 pour l’abonnement d’entreprise, en copiant les comptes d’utilisateur et de groupe et une version hachée des mots de passe de compte d’utilisateur.

Pour la synchronisation d’annuaires, Contoso a déployé l’outil Connecter Azure AD sur un serveur dans son centre de données parisien.

Voici le serveur exécutant Azure AD Connecter la forêt Contoso AD DS pour les modifications, puis la synchronisation de ces modifications avec le client Azure AD.

![Infrastructure de synchronisation d’annuaires PHS Contoso](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-identity-and-device-access"></a>Stratégies d’accès conditionnel basé sur l’identité et l’appareil

Contoso a créé un jeu d’Azure AD et Intune [stratégies d’accès conditionnel](../security/office-365-security/identity-access-policies.md) pour trois niveaux de protection :

- *Les* protections de référence s’appliquent à tous les comptes d’utilisateur.
- *Les* protections sensibles s’appliquent aux cadres supérieurs et aux cadres.
- *Les protections hautement réglementées* s’appliquent à des utilisateurs spécifiques des services financiers, juridiques et de recherche qui ont accès aux données hautement réglementées.

Voici l’ensemble des stratégies d’accès conditionnel aux appareils et aux identités Contoso.

![Stratégies d’accès conditionnel basées sur l’identité et l’appareil de Contoso](../media/contoso-identity/contoso-identity-fig5.png)
 
## <a name="next-step"></a>Étape suivante

Découvrez comment Contoso utilise son infrastructure Microsoft Endpoint Configuration Manager pour déployer et maintenir la Windows 10 Entreprise [au](contoso-win10.md) sein de son organisation.

## <a name="see-also"></a>Voir aussi

[Feuille de route relative à l’identité pour Microsoft 365](identity-roadmap-microsoft-365.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)