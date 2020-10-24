---
title: Identité de Contoso Corporation
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
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
ms.openlocfilehash: dea0f53ef1c3fdc2ea32256303c6120c614c904d
ms.sourcegitcommit: 66b8fc1d8ba4f17487cd2004ac19cf2fff472f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48754635"
---
# <a name="identity-for-the-contoso-corporation"></a>Identité de Contoso Corporation

Microsoft fournit une identité sous forme de service (IDaaS) dans ses offres Cloud via Azure Active Directory (Azure AD). Pour adopter Microsoft 365 pour Enterprise, la solution Contoso IDaaS devait utiliser son fournisseur d’identité local et inclure l’authentification fédérée avec ses fournisseurs d’identité tiers approuvés existants.

## <a name="the-contoso-active-directory-domain-services-forest"></a>Forêt des services de domaine Active Directory contoso

Contoso utilise une seule forêt des services de domaine Active Directory (AD DS) pour Contoso \. com avec sept sous-domaines, un pour chaque région du monde. Le siège social, les centres régionaux et les succursales disposent de contrôleurs de domaine pour l’authentification locale et l’autorisation.

Voici la forêt contoso avec des domaines régionaux pour les différentes parties du monde qui contiennent des concentrateurs régionaux.

![Forêt et domaines de Contoso dans le monde](../media/contoso-identity/contoso-identity-fig1.png)
 
Contoso a décidé d’utiliser les comptes et les groupes de la \. forêt Contoso com pour l’authentification et l’autorisation pour ses services et charges de travail Microsoft 365.

## <a name="the-contoso-federated-authentication-infrastructure"></a>Infrastructure d’authentification contoso fédérée

Contoso autorise les éléments suivants :

- Aux clients d’utiliser leurs comptes Microsoft, Facebook ou Google Mail pour se connecter au site Web public de la société.
- Les fournisseurs et les partenaires peuvent utiliser leurs comptes LinkedIn, Salesforce ou Google Mail pour se connecter à l’extranet partenaires de l’entreprise.

Voici la zone DMZ contoso contenant un site Web public, un extranet de partenaire et un ensemble de serveurs AD FS (Active Directory Federation Services). La zone DMZ est connectée à Internet et contient des clients, des partenaires et des services Internet.

![Prise en charge de contoso pour l’authentification fédérée pour les clients et les partenaires](../media/contoso-identity/contoso-identity-fig2.png)
 
Les serveurs AD FS de la DMZ facilitent l’authentification des informations d’identification des clients par leurs fournisseurs d’identité pour accéder au site Web public et aux informations d’identification des partenaires pour accéder à l’extranet des partenaires.

Contoso a décidé de conserver cette infrastructure et de la dédier à l’authentification des partenaires et des clients. Les architectes d’identité contoso étudient la conversion de cette infrastructure en solutions [B2B](https://docs.microsoft.com/azure/active-directory/b2b/hybrid-organizations) et [B2C](https://docs.microsoft.com/azure/active-directory-b2c/solution-articles) Azure ad.

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>Identité hybride avec authentification directe pour l’authentification basée sur le cloud

Contoso souhaitait utiliser sa forêt AD DS locale pour l’authentification auprès des ressources cloud de Microsoft 365. Il a décidé d’utiliser la synchronisation de hachage de mot de passe (hachage).

HACHAGE synchronise la forêt AD DS locale avec le client Azure AD de ses Microsoft 365 pour l’abonnement Enterprise, en copiant les comptes d’utilisateur et de groupe, ainsi qu’une version hachée des mots de passe de compte d’utilisateur.

Pour effectuer une synchronisation d’annuaires, Contoso a déployé l’outil Azure AD Connect sur un serveur dans son centre de centre de Paris.

Voici le serveur exécutant Azure AD Connect interrogeant la forêt Contoso AD DS pour les modifications, puis en synchronisant ces modifications avec le locataire Azure AD.

![Infrastructure de synchronisation d’annuaires contoso hachage](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-identity-and-device-access"></a>Stratégies d’accès conditionnel basé sur l’identité et l’appareil

Contoso a créé un jeu d’Azure AD et Intune [stratégies d’accès conditionnel](identity-access-policies.md) pour trois niveaux de protection :

- Les protections de *base* s’appliquent à tous les comptes d’utilisateur.
- Les protections *sensibles* s’appliquent au leadership et au personnel de direction.
- Les protections *hautement réglementées* s’appliquent à des utilisateurs spécifiques des services financiers, juridiques et de recherche qui ont accès à des données hautement réglementées.

Voici l’ensemble des stratégies d’accès conditionnel d’appareil et d’identité contoso.

![Stratégies d’accès conditionnel basées sur l’identité et l’appareil de Contoso](../media/contoso-identity/contoso-identity-fig5.png)
 
## <a name="next-step"></a>Étape suivante

Découvrez comment Contoso utilise son infrastructure de gestionnaire de configuration de point de terminaison Microsoft pour [déployer et conserver Windows 10 entreprise actuelle](contoso-win10.md) au sein de son organisation.

## <a name="see-also"></a>Voir également

[Feuille de route relative à l’identité pour Microsoft 365](identity-roadmap-microsoft-365.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
