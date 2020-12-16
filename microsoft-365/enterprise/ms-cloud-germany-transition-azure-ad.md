---
title: Informations supplémentaires sur Azure Active Directory pour la migration à partir de Microsoft Cloud Deutschland
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
description: 'Résumé : informations supplémentaires sur Azure Active Directory lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers les services Office 365 dans la nouvelle région de centre de données allemande.'
ms.openlocfilehash: 4fc5dda95e5e7afc4d69141a9a4debd0a74c492b
ms.sourcegitcommit: 849b365bd3eaa9f3c3a9ef9f5973ef81af9156fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49688804"
---
# <a name="additional-azure-active-directory-information-for-the-migration-from-microsoft-cloud-deutschland"></a>Informations supplémentaires sur Azure Active Directory pour la migration à partir de Microsoft Cloud Deutschland

Pour effectuer le déplacement du Cloud Azure allemand vers le cloud public Azure, nous recommandons que le point de terminaison d’authentification, le graphique Azure Active Directory (Azure AD) Graph et les points de terminaison MS Graph pour vos applications soient mis à jour vers ceux du nuage commercial lorsque le point de terminaison OpenID Connect (OIDC), `https://login.microsoftonline.com/\<TenantIdOrDomain\>/.well-known/openid-configuration` commence à signaler les points de terminaison Cloud commerciaux. 
 
**Quand dois-je procéder à cette modification ?**

Vous recevrez une notification dans Azure/Office Portal lorsque votre client effectuera la migration du Cloud allemand vers le Cloud commercial. Vous avez 30 jours après avoir reçu cette notification pour effectuer ces mises à jour afin que votre application continue à fonctionner pour les clients qui sont migrés depuis Azure Germany Cloud vers le cloud public Azure.
 
Il existe trois conditions préalables à la mise à jour de votre autorité de connexion :

 - Le point de terminaison de découverte OIDC pour votre client `https://login.microsoftonline.com/\<TenantIdOrDomain\>/.well-known/openid-configuration` renvoie les points de terminaison du cloud public Azure ad.

 - Si votre client est configuré pour la Fédération, les services ADFS (Active Directory Federation Services) sont mis à jour pour être synchronisés avec Azure AD public. Vous pouvez suivre les instructions pour mettre à jour les paramètres Azure AD Connect pour apporter cette modification.

 - Les applications de ressource, le cas échéant, utilisées par vos applications sont modifiées afin d’accepter les jetons signés par Azure AD Germany et Azure AD public.
 
**Quels types d’applications ?**

Une application peut être l’une des suivantes :

- [Application à page unique (SPA)](https://docs.microsoft.com/azure/active-directory/develop/scenario-spa-overview)
- [Application Web qui se connecte aux utilisateurs](https://docs.microsoft.com/azure/active-directory/develop/scenario-web-app-sign-user-overview)
- [Application Web qui appelle des API Web](https://docs.microsoft.com/azure/active-directory/develop/scenario-web-app-call-api-overview)
- [API Web protégée](https://docs.microsoft.com/azure/active-directory/develop/scenario-protected-web-api-overview)
- [API Web qui appelle des API Web](https://docs.microsoft.com/azure/active-directory/develop/scenario-web-api-call-api-overview)
- [Application de bureau](https://docs.microsoft.com/azure/active-directory/develop/scenario-desktop-overview)
- [App daemon](https://docs.microsoft.com/azure/active-directory/develop/scenario-daemon-overview)
- [Application mobile](https://docs.microsoft.com/azure/active-directory/develop/scenario-mobile-overview)
 
> [!NOTE] 
> Lorsqu’une application bascule vers en utilisant `login.microsoftonline.com` comme autorité, les jetons sont signés par cette nouvelle autorité. Si vous hébergez des applications de ressource appelées par d’autres applications, vous devrez autoriser la validation des jetons de Lax. Cela signifie que votre application doit autoriser les jetons signés par les nuages publics Azure AD Germany et Azure AD. Cette validation de jeton LAX est nécessaire jusqu’à ce que toutes les applications clientes qui appellent votre service soient entièrement migrées vers le cloud public Azure AD. Après la migration, votre application de ressource doit uniquement accepter les jetons signés par le cloud public Azure AD.

**Que dois-je mettre à jour ?**

1. Si vous hébergez une application dans Azure Germany qui est utilisée pour authentifier les utilisateurs Azure Germany ou Office 365 Germany, assurez-vous qu' `https://login.microsoftonline.com` elle est utilisée en tant qu’autorité dans le contexte d’authentification.

    - Voir contextes d’authentification Azure AD.
    - Cela s’applique à la fois à l’authentification pour votre application, ainsi qu’à toutes les API que votre application peut appeler (Microsoft Graph, Azure AD Graph, Azure Resource Manager).

2. Mettez à jour le point de terminaison Azure AD Graph sur `https://graph.windows.net` .

3. Mettez à jour le point de terminaison MS Graph `https://graph.microsoft.com` .

4. Mettez à jour les points de terminaison de Cloud allemands (tels que ceux d’Exchange Online et de SharePoint Online) utilisés par vos applications comme étant ceux du cloud public.

5. Mettez à jour les paramètres d’environnement `AzurePublic` (au lieu `AzureGermany` ) dans les outils d’administration et les scripts pour :

    - [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps)
    - [Azure AD PowerShell (MSOnline)](https://docs.microsoft.com/powershell/azure/active-directory/overview)
    - [Azure AD PowerShell (AzureAD)](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?)
    - [Interface de commande de commande Azure](https://docs.microsoft.com/cli/azure/install-azure-cli)
 
**Qu’en est-il des applications que je publie ?**

Si vous publiez une application accessible aux utilisateurs qui se trouvent à l’extérieur de votre client, vous devrez peut-être modifier l’inscription de votre application pour garantir la continuité. Les autres clients qui utilisent votre application peuvent être déplacés à un autre moment que votre client. Pour vous assurer qu’ils ne perdent jamais l’accès à votre application, vous devez consentir à la synchronisation de votre application d’Azure Germany à Azure public.

## <a name="additional-considerations"></a>Considérations supplémentaires

Voici quelques considérations supplémentaires pour Azure AD :

- Pour l’authentification fédérée :

  - Vous ne devez pas créer, promouvoir ou rétrograder un domaine fédéré pendant que la transition de client est en cours. Une fois la migration vers le service Azure AD terminée (le client est entièrement complet), vous pouvez reprendre la gestion des domaines fédérés.

  - Si vous utilisez l’authentification fédérée avec Active Directory Federation Services (AD FS), vous ne devez pas modifier les URI d’émetteur utilisés pour toute authentification avec vos services de domaine Active Directory (AD DS) locaux lors de la migration. La modification des URI de l’émetteur entraîne des échecs d’authentification pour les utilisateurs du domaine. Les URI d’émetteur peuvent être modifiés directement dans AD FS ou lorsqu’un domaine est converti d’un domaine géré à un domaine fédéré, et inversement. Microsoft recommande aux clients de ne pas ajouter, supprimer ou convertir un domaine fédéré dans le client Azure AD en cours de migration. Les URI de l’émetteur peuvent être modifiés une fois la migration entièrement terminée.

- Pour la mise en réseau :

  - La création de réseaux nommés par IPv6 ne fonctionne pas dans le portail Azure `http://portal.microsoftazure.de/` . Utilisez le portail Azure `https://portal.azure.com` pour créer des réseaux nommés IPv6.
 
   - Vous ne pouvez pas créer de plages d’adresses IP approuvées pour les paramètres du service d’authentification multifacteur Azure (MFA) à partir du portail Microsoft Cloud Deutschland. Utilisez les services Azure AD Portal pour Office 365 pour créer des plages d’adresses IP approuvées d’Azure MFA.


- Pour un accès conditionnel : 

  - Les stratégies d’accès conditionnel avec les contrôles d’octroi suivants ne sont pas prises en charge jusqu’à ce que la migration vers les services Office 365 soit terminée (après la phase de finalisation de la migration [Azure ad](ms-cloud-germany-transition.md#how-is-the-migration-organized) ) :

    - Exiger un appareil conforme
    - Exiger une application approuvée
    - Exiger une stratégie de protection des applications
    
  - L’interface de stratégie d’accès conditionnel donne un avertissement faux sur les valeurs par défaut de sécurité activées pour le client même si elle est désactivée et des stratégies d’accès conditionnel existent déjà pour le client. Vous devez ignorer l’avertissement ou utiliser le portail des services Office 365 pour gérer les stratégies d’accès conditionnel. 

- Les scénarios Intune sont pris en charge uniquement par les points de terminaison internationaux une fois la migration du client terminée, y compris toutes les migrations de charges de travail Office.

- Microsoft Cloud Deutschland les utilisateurs qui utilisent la méthode de notification d’application mobile pour les demandes MFA voient le ObjectId (un GUID) de l’utilisateur au lieu du nom d’utilisateur principal (UPN) dans l’application Microsoft Authenticator. Une fois la migration du client Azure AD terminée et hébergée dans les services Office 365, les nouvelles activations de l’authentificateur Microsoft afficheront les UPN des utilisateurs. Les comptes Microsoft authentificateur existants continueront à afficher l’ObjectId de l’utilisateur, mais ils continueront à fonctionner pour les notifications d’applications mobiles. 

- Pour les clients créés après le 22 octobre 2019, les paramètres de sécurité par défaut peuvent être automatiquement activés pour le client lors de la migration vers le service Office 365. Les administrateurs de client peuvent choisir de laisser les paramètres de sécurité par défaut activés et s’inscrire pour l’authentification multifacteur, ou désactiver la fonctionnalité. Pour plus d’informations, consultez la rubrique [désactivation des paramètres de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults#disabling-security-defaults). 

  > [!NOTE]
  > Les organisations qui ne sont pas activées automatiquement lors de la migration peuvent toujours être automatiquement intégrées à l’avenir, car la fonctionnalité permettant d’activer les paramètres de sécurité par défaut est déployée dans le service Office 365. Les administrateurs qui choisissent de désactiver ou d’activer les paramètres de sécurité par défaut peuvent le faire en mettant à jour la fonctionnalité sous **Azure Active Directory > propriétés**. Une fois la fonctionnalité activée de manière explicite par l’administrateur, elle ne sera pas activée automatiquement.

- Une fois que le client est en cours de migration, vous recevrez un avertissement sur la version d’Azure AD Connect dans le portail Office 365 Germany et sur le portail Office 365. Ceci peut être ignoré si l’avertissement de version n’affiche plus l’avertissement une fois la migration terminée. S’il existe un avertissement, avant ou après la migration, dans l’un ou l’autre portail, Azure AD Connect doit être mis à jour. Le message d’avertissement indique : "nous avons détecté que vous utilisez un outil de synchronisation d’annuaires obsolète. Nous vous recommandons d’accéder au centre de téléchargement Microsoft pour obtenir la dernière version d’Azure AD Connect.

## <a name="more-information"></a>Informations supplémentaires

Mise en route :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client lors de la migration](ms-cloud-germany-transition-experience.md)

Navigation par le biais de la transition :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour [Azure ad](ms-cloud-germany-transition-azure-ad.md), [appareils](ms-cloud-germany-transition-add-devices.md), [expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications Cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
