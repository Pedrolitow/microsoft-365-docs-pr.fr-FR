---
title: Microsoft 365 modèles d’identité et Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 09/30/2020
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Découvrez comment gérer le service d’identité d’utilisateur Azure AD dans Microsoft 365 à l’aide de modèles d’identité cloud uniquement ou hybrides.
ms.openlocfilehash: 93a37f39a4d96d7c2e434ed6edf4df588e672a0f
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53228494"
---
# <a name="microsoft-365-identity-models-and-azure-active-directory"></a>Microsoft 365 modèles d’identité et Azure Active Directory

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 utilise Azure Active Directory (Azure AD), un service d’authentification et d’identité d’utilisateur basé sur le cloud inclus dans votre abonnement Microsoft 365, pour gérer les identités et l’authentification pour Microsoft 365. La configuration correcte de votre infrastructure d’identité est essentielle à la gestion Microsoft 365'accès des utilisateurs et des autorisations pour votre organisation.

Avant de commencer, regardez cette vidéo pour obtenir une vue d’ensemble des modèles d’identité et de l’authentification pour Microsoft 365.

<p> </p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

Votre premier choix de planification est le modèle Microsoft 365'identité.

## <a name="microsoft-365-identity-models"></a>Microsoft 365 d’identité

Pour planifier les comptes d’utilisateurs, vous devez d’abord comprendre les deux modèles d’identité Microsoft 365. Vous pouvez gérer les identités de votre organisation uniquement dans le cloud, ou vous pouvez conserver vos identités AD DS (Active Directory Domain Services) locales et les utiliser pour l’authentification lorsque les utilisateurs accèdent aux services cloud Microsoft 365.

Voici les deux types d’identité et leur meilleur ajustement et leurs avantages.

| Attribut | Identité cloud uniquement | Identité hybride |
|:-------|:-----|:-----|
| **Définition** | Le compte d’utilisateur existe uniquement dans le client Azure AD pour votre abonnement Microsoft 365 client. | Le compte d’utilisateur existe dans AD DS et une copie se trouve également dans le client Azure AD pour votre abonnement Microsoft 365 client. Le compte d’utilisateur dans Azure AD peut également inclure une version hachée du mot de passe de compte d’utilisateur AD DS déjà haché. |
| **Comment Microsoft 365 authentifier les informations d’identification de l’utilisateur** | Le client Azure AD de votre abonnement Microsoft 365 effectue l’authentification avec le compte d’identité cloud. | Le client Azure AD de votre abonnement Microsoft 365 gère le processus d’authentification ou redirige l’utilisateur vers un autre fournisseur d’identité. |
| **Recommandé pour** | Organisations qui n’ont pas ou n’ont pas besoin d’une AD DS locale. | Organisations utilisant AD DS ou un autre fournisseur d’identité. |
| **Plus grand avantage** | Simple à utiliser. Aucun outil ou serveur d’annuaire supplémentaire n’est requis. | Les utilisateurs peuvent utiliser les mêmes informations d’identification lors de l’accès à des ressources sur site ou en nuage. |
||||

## <a name="cloud-only-identity"></a>Identité cloud uniquement

Une identité cloud uniquement utilise des comptes d’utilisateur qui existent uniquement dans Azure AD. L’identité cloud uniquement est généralement utilisée par les petites organisations qui n’ont pas de serveurs locaux ou qui n’utilisent pas AD DS pour gérer les identités locales.

Voici les composants de base de l’identité cloud uniquement.

![Composants de base de l’identité cloud uniquement](../media/about-microsoft-365-identity/cloud-only-identity.png)

Les utilisateurs locaux et distants (en ligne) utilisent leurs comptes d’utilisateur et mots de passe Azure AD pour accéder Microsoft 365 services cloud. Azure AD authentifier les informations d’identification de l’utilisateur en fonction de ses comptes d’utilisateur et mots de passe stockés.

### <a name="administration"></a>Administration
Étant donné que les comptes d’utilisateur sont stockés uniquement dans Azure AD, vous gérez les identités cloud à l’aide d’outils tels que Centre d’administration Microsoft 365 [et](../admin/add-users/index.yml) [Windows PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md).

## <a name="hybrid-identity"></a>Identité hybride

L’identité hybride utilise des comptes qui proviennent d’un service AD DS local et qui ont une copie dans le client Azure AD d’un abonnement Microsoft 365 client. Toutefois, la plupart des modifications ne s' flowent qu’à sens unique. Les modifications apportées aux comptes d’utilisateurS AD DS sont synchronisées avec leur copie dans Azure AD. Toutefois, les modifications apportées aux comptes basés sur le cloud dans Azure AD, telles que les nouveaux comptes d’utilisateur, ne sont pas synchronisées avec AD DS.

Azure AD Connecter la synchronisation continue des comptes. Il s’exécute sur un serveur local, recherche les modifications dans les AD DS et les a transmis à Azure AD. Azure AD Connecter permet de filtrer les comptes qui sont synchronisés et de synchroniser une version hachée des mots de passe utilisateur, appelée synchronisation de hachage de mot de passe (PHS).

Lorsque vous implémentez une identité hybride, votre AD DS local est la source faisant autorité pour les informations de compte. Cela signifie que vous effectuez des tâches d’administration principalement locales, qui sont ensuite synchronisées avec Azure AD.

Voici les composants de l’identité hybride.

![Composants de l’identité hybride](../media/about-microsoft-365-identity/hybrid-identity.png)

Le client Azure AD dispose d’une copie des comptes AD DS. Dans cette configuration, les utilisateurs locaux et distants qui accèdent Microsoft 365 services cloud s’authentifier sur Azure AD.

> [!NOTE]
> Vous devez toujours utiliser Azure AD Connecter pour synchroniser les comptes d’utilisateur pour l’identité hybride. Vous avez besoin des comptes d’utilisateur synchronisés dans Azure AD pour effectuer l’attribution de licences et la gestion des groupes, configurer les autorisations et d’autres tâches administratives qui impliquent des comptes d’utilisateurs.

### <a name="administration"></a>Administration

Étant donné que les comptes d’utilisateur d’origine et faisant autorité sont stockés dans les AD DS locales, vous gérez vos identités avec les mêmes outils que vous gérez vos AD DS.

Vous n’utilisez pas l’Centre d’administration Microsoft 365 ou PowerShell pour Microsoft 365 gérer les comptes d’utilisateur synchronisés dans Azure AD.

## <a name="next-step"></a>Étape suivante

Si vous avez besoin du modèle d’identité cloud uniquement, voir [Identité cloud uniquement.](cloud-only-identities.md)

Si vous avez besoin du modèle d’identité hybride, voir [Identité hybride.](plan-for-directory-synchronization.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)
