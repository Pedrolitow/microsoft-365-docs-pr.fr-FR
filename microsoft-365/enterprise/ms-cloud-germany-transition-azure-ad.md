---
title: Informations Azure Active Directory supplémentaires pour la migration à partir de Microsoft Cloud Deutschland
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/15/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
description: 'Résumé : Informations supplémentaires Azure Active Directory lors du déplacement de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers Office 365 services dans la nouvelle région de centres de données allemands.'
ms.openlocfilehash: 1e3871dc5a8a8a9ecbef29df21431aa3707871d0
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50923849"
---
# <a name="additional-azure-active-directory-information-for-the-migration-from-microsoft-cloud-deutschland"></a>Informations Azure Active Directory supplémentaires pour la migration à partir de Microsoft Cloud Deutschland

Pour effectuer le déplacement du cloud Azure allemand vers le cloud public Azure, nous vous recommandons de mettre à jour les points de terminaison d’authentification, Graph Azure Active Directory (Azure AD) et MS Graph pour vos applications vers ceux du cloud commercial lorsque le point de terminaison OpenID Connecter (OIDC) commence à signaler les points de terminaison du `https://login.microsoftonline.com/\<TenantIdOrDomain\>/.well-known/openid-configuration` cloud commercial. 
 
**Quand dois-je effectuer cette modification ?**

Vous recevrez une notification dans le portail Azure/Office lorsque votre client termine la migration du cloud allemand vers le cloud commercial. Vous avez 30 jours après avoir reçu cette notification pour effectuer ces mises à jour afin que votre application continue de fonctionner pour les locataires migrés du cloud Azure Germany vers le cloud public Azure.
 
Il existe trois conditions préalables à la mise à jour de votre autorité de signature :

 - Le point de terminaison de découverte OIDC pour votre client renvoie les points de terminaison du `https://login.microsoftonline.com/\<TenantIdOrDomain\>/.well-known/openid-configuration` cloud public Azure AD.

 - Si votre client est prêt pour la fédération, les services AD FS (Active Directory Federation Services) sont mis à jour pour être synchronisés avec Azure AD Public. Vous pouvez suivre des instructions pour mettre à jour les paramètres Connecter Azure AD pour effectuer cette modification.

 - Les applications de ressources, le cas cas, utilisées par vos applications sont modifiées pour accepter les jetons signés par Azure AD Germany et Azure AD Public.
 
**Quel type d’applications ?**

Une application peut être l’une des suivantes :

- [Application mono-page (SPA)](/azure/active-directory/develop/scenario-spa-overview)
- [Application web qui se signe avec les utilisateurs](/azure/active-directory/develop/scenario-web-app-sign-user-overview)
- [Application web qui appelle des API web](/azure/active-directory/develop/scenario-web-app-call-api-overview)
- [API web protégée](/azure/active-directory/develop/scenario-protected-web-api-overview)
- [API web qui appelle les API web](/azure/active-directory/develop/scenario-web-api-call-api-overview)
- [Application de bureau](/azure/active-directory/develop/scenario-desktop-overview)
- [Application daemon](/azure/active-directory/develop/scenario-daemon-overview)
- [Application mobile](/azure/active-directory/develop/scenario-mobile-overview)
 
> [!NOTE] 
> Lorsqu’une application bascule vers l’utilisation en tant qu’autorité, les jetons sont `login.microsoftonline.com` signés par cette nouvelle autorité. Si vous hébergez des applications de ressources que d’autres applications appellent, vous devez autoriser la validation du jeton laxiste. Cela signifie que votre application doit autoriser les jetons signés par les clouds publics Azure AD Germany et Azure AD. Cette validation de jeton lax est nécessaire jusqu’à ce que toutes les applications clientes qui appellent votre service soient entièrement migrées vers le cloud public Azure AD. Après la migration, votre application de ressources doit uniquement accepter les jetons signés par le cloud public Azure AD.

**De quoi ai-je besoin pour mettre à jour ?**

1. Si vous hébergez une application dans Azure Germany utilisée pour authentifier les utilisateurs Azure Germany ou Office 365 Germany, assurez-vous qu’elle est utilisée comme autorité dans le contexte `https://login.microsoftonline.com` d’authentification.

    - Consultez les contextes d’authentification Azure AD.
    - Cela s’applique à la fois à l’authentification à votre application et à toute API que votre application peut appeler (c’est-à-dire, Microsoft Graph, Azure AD Graph, Azure Resource Manager).

2. Mettez à jour azure AD Graph point de terminaison à être `https://graph.windows.net` .

3. Mettez à jour Graph point de terminaison MS à être `https://graph.microsoft.com` .

4. Mettez à jour tous les points de terminaison cloud allemands (tels que ceux pour Exchange Online et SharePoint Online) qui sont utilisés par vos applications pour être ceux du cloud public.

5. Mettez à jour les paramètres d’environnement pour qu’ils soient (et non) dans les `AzurePublic` `AzureGermany` outils d’administration et les scripts pour :

    - [Azure PowerShell](/powershell/azure/install-az-ps)
    - [Azure AD PowerShell (MSOnline)](/powershell/azure/active-directory/overview)
    - [Azure AD PowerShell (AzureAD)](/powershell/azure/active-directory/install-adv2)
    - [Azure CLI](/cli/azure/install-azure-cli)
 
**Qu’en est-il des applications que je publie ?**

Si vous publiez une application disponible pour les utilisateurs extérieurs à votre client, vous devrez peut-être modifier votre inscription d’application pour garantir la continuité. D’autres locataires qui utilisent votre application peuvent être déplacés à un moment différent de celui de votre client. Pour vous assurer qu’ils ne perdent jamais l’accès à votre application, vous devez consentir à la synchronisation de votre application d’Azure Germany vers Azure public.

## <a name="additional-considerations"></a>Considérations supplémentaires

Voici quelques considérations supplémentaires pour Azure AD :

- Pour l’authentification fédérée :

  - Vous ne devez pas créer, promouvoir ou rétrograder un domaine fédéré pendant la transition du client. Une fois la migration vers le service Azure AD terminée (le client est entièrement terminé), vous pouvez reprendre la gestion des domaines fédérés.

  - Si vous utilisez l’authentification fédérée avec les services AD FS (Active Directory Federation Services), vous ne devez pas apporter de modifications aux URIs d’émetteur utilisés pour toutes les authentifications avec vos services de domaine Active Directory (AD DS) locaux lors de la migration. La modification des URL d’émetteur entraîne des échecs d’authentification pour les utilisateurs du domaine. Les URIs d’émetteur peuvent être modifiés directement dans AD FS ou lorsqu’un domaine est converti de géré en fédéré et vice versa. Microsoft recommande aux clients de ne pas ajouter, supprimer ou convertir un domaine fédéré dans le client Azure AD en cours de migration. Les URL de l’émetteur peuvent être modifiées une fois la migration terminée.

- Pour la mise en réseau :

  - La création de réseaux nommés IPv6 ne fonctionne pas dans le portail `http://portal.microsoftazure.de/` Azure. Utilisez le portail Azure sur `https://portal.azure.com` le site pour créer des réseaux nommés IPv6.
 
   - Vous ne pouvez pas créer de plages d’adresses IP fiables pour les paramètres du service Azure Multi-Factor Authentication (MFA) à partir du portail Microsoft Cloud Deutschland. Utilisez le portail Azure AD pour Office 365 services pour créer des plages d’adresses IP fiables Azure MFA.


- Pour l’accès conditionnel : 

  - Les stratégies d’accès conditionnel avec les contrôles d’octroi suivants ne sont pas pris en charge tant que la migration vers Office 365 services n’est pas terminée (après la phase finaliser la migration [d’Azure AD)](ms-cloud-germany-transition.md#how-is-the-migration-organized) :

    - Exiger un appareil conforme
    - Exiger une application approuvée
    - Exiger une stratégie de protection des applications
    
  - L’interface de stratégie d’accès conditionnel donne un faux avertissement concernant les paramètres de sécurité par défaut activés pour le client même lorsqu’il est désactivé, et que des stratégies d’accès conditionnel existent déjà pour le client. Vous devez ignorer l’avertissement ou utiliser le portail Office 365 services pour gérer les stratégies d’accès conditionnel. 

- Les scénarios Intune sont pris en charge uniquement par rapport aux points de terminaison internationaux une fois la migration des clients terminée, y compris toutes les migrations de charges de travail Office.

- Les utilisateurs de Microsoft Cloud Deutschland qui utilisent la méthode de notification d’application mobile pour les demandes MFA voient l’ObjectId (un GUID) de l’utilisateur au lieu du nom d’utilisateur principal (UPN) dans l’application Microsoft Authenticator. Une fois la migration du client Azure AD terminée et hébergée dans les services Office 365, les nouvelles activations Microsoft Authenticator afficheront les UPN des utilisateurs. Les comptes Microsoft Authenticator existants continueront d’afficher l’ObjectId de l’utilisateur, mais ils continueront à fonctionner pour les notifications d’application mobile. 

- Pour les clients créés après le 22 octobre 2019, les paramètres de sécurité par défaut peuvent être activés automatiquement pour le client lors de sa migration vers le service Office 365. Les administrateurs client peuvent choisir de laisser les paramètres de sécurité par défaut activés et de s’inscrire à l’mf, ou ils peuvent désactiver la fonctionnalité. Pour plus d’informations, voir [Désactiver les paramètres de sécurité par défaut.](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults#disabling-security-defaults) 

  > [!NOTE]
  > Les organisations qui ne sont pas activées automatiquement lors de la migration peuvent toujours être inscrites automatiquement à l’avenir, car la fonctionnalité permettant d’activer les paramètres de sécurité par défaut est déployée dans le service Office 365. Les administrateurs qui choisissent de désactiver ou d’activer explicitement les paramètres de sécurité par défaut peuvent le faire en mettant à jour la fonctionnalité **sous Azure Active Directory > propriétés.** Une fois que la fonctionnalité est explicitement activée par l’administrateur, elle ne sera pas activée automatiquement.

- Un avertissement s’est produit sur la version d’Azure AD Connecter sur le portail Office 365 Germany, ainsi que sur le portail Office 365 une fois que le client est en migration. Cela peut être ignoré si l’avertissement de version n’affiche plus l’avertissement une fois la migration terminée. En cas d’avertissement, avant ou après la migration, dans l’un des portails, Azure AD Connecter être mis à jour. Le message d’avertissement indique : « Nous avons détecté que vous utilisez un outil de synchronisation d’annuaires obsolète. Nous vous recommandons d’aller au Centre de téléchargement Microsoft pour obtenir la dernière version d’Azure AD Connecter. »

## <a name="more-information"></a>Plus d’informations

Mise en place :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centres de données allemandes](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client pendant la migration](ms-cloud-germany-transition-experience.md)

Transition :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour [Azure AD,](ms-cloud-germany-transition-azure-ad.md) [les appareils,](ms-cloud-germany-transition-add-devices.md) [les expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications cloud :

- [Informations sur le programme de migration Dynamics 365](/dynamics365/get-started/migrate-data-german-region)
- [Informations sur le programme de migration Power BI](/power-bi/admin/service-admin-migrate-data-germany)
- [Prise en main de votre mise à niveau vers Microsoft Teams](/microsoftteams/upgrade-start-here)