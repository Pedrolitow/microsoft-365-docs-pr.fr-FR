---
title: Informations générales supplémentaires pour la migration à partir de Microsoft Cloud Deutschland
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/01/2020
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
description: 'Résumé : informations générales supplémentaires sur les services lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers les services Office 365 dans la nouvelle région de centre de données allemande.'
ms.openlocfilehash: 6fa09165f8aaa68e0f9fc567d96a4e53baaa594e
ms.sourcegitcommit: 38d828ae8d4350ae774a939c8decf30cb36c3bea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49551781"
---
# <a name="additional-general-information-for-the-migration-from-microsoft-cloud-deutschland"></a>Informations générales supplémentaires pour la migration à partir de Microsoft Cloud Deutschland

Les sections suivantes fournissent des informations supplémentaires sur les services, les considérations de pré-travail et l’expérience utilisateur.

## <a name="azure-active-directory"></a>Azure Active Directory

Pour effectuer le déplacement du Cloud Azure allemand vers le cloud public Azure, nous recommandons que le point de terminaison d’authentification, le graphique Azure Active Directory (Azure AD) Graph et les points de terminaison MS Graph pour vos applications soient mis à jour vers ceux du nuage commercial lorsque le point de terminaison OpenID Connect (OIDC), `https://login.microsoftonline.com/\<TenantIdOrDomain\>/.well-known/openid-configuration` commence à signaler les points de terminaison Cloud commerciaux. 
 
**Quand dois-je procéder à cette modification ?**

Vous recevrez une notification dans Azure/Office Portal lorsque votre client effectuera la migration du Cloud allemand vers le Cloud commercial. Vous avez 30 jours après avoir reçu cette notification pour effectuer ces mises à jour afin que votre application continue à fonctionner pour les clients qui sont migrés depuis Azure Germany Cloud vers le cloud public Azure.
 
Il existe trois conditions préalables à la mise à jour de votre autorité de connexion :

 - Le point de terminaison de découverte OIDC pour votre client `https://login.microsoftonline.com/\<TenantIdOrDomain\>/.well-known/openid-configuration` renvoie les points de terminaison du cloud public Azure ad.

 - Si votre client est configuré pour la Fédération, les services ADFS (Active Directory Federation Services) sont mis à jour pour être synchronisés avec Azure AD public. Vous pouvez suivre les instructions pour mettre à jour les paramètres Azure AD Connect pour apporter cette modification.

 - Les applications de ressource, le cas échéant, utilisées par vos applications sont modifiées afin d’accepter les jetons signés par Azure AD Germany et Azure AD public.
 
**Quels types d’applications ?**

Une application peut être l’une des suivantes :

- Application à page unique (SPA)
- Application Web qui se connecte aux utilisateurs
- Application Web qui appelle des API Web
- API Web protégée
- API Web qui appelle des API Web
- Application de bureau
- App daemon
- Application mobile
 
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

    - Azure PowerShell
    - Azure AD PowerShell (MSOnline)
    - Azure AD PowerShell (AzureAD)
    - Interface de commande de commande Azure
 
**Qu’en est-il des applications que je publie ?**

Si vous publiez une application accessible aux utilisateurs qui se trouvent à l’extérieur de votre client, vous devrez peut-être modifier l’inscription de votre application pour garantir la continuité. Les autres clients qui utilisent votre application peuvent être déplacés à un autre moment que votre client. Pour vous assurer qu’ils ne perdent jamais l’accès à votre application, vous devez consentir à la synchronisation de votre application d’Azure Germany à Azure public.

### <a name="additional-considerations"></a>Considérations supplémentaires

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

## <a name="exchange-online"></a>Exchange Online 

- `myaccount.msft.com` fonctionnera uniquement après le basculement d’Office 365. Les liens génèrent des messages d’erreur « un problème est survenu » jusqu’à ce moment.

- Les utilisateurs d’Outlook Web App qui accèdent à une boîte aux lettres partagée dans l’autre environnement (par exemple, un utilisateur de l’environnement Germany qui accède à une boîte aux lettres partagée dans l’environnement global) seront invités à s’authentifier une deuxième fois. L’utilisateur doit d’abord s’authentifier et accéder à sa boîte aux lettres dans `outlook.office.de` , puis ouvrir la boîte aux lettres partagée qui se trouve dans `outlook.office365.com` . Ils devront s’authentifier une deuxième fois lors de l’accès aux ressources partagées hébergées dans l’autre service.

- Pour les clients Microsoft Cloud Deutschland existants ou ceux en transition, lorsqu’une boîte aux lettres partagée est ajoutée à Outlook à l’aide des **informations de > de fichiers > ajouter un compte**, l’affichage des autorisations de calendrier peut échouer (le client Outlook tente d’utiliser l’API REST `https://outlook.office.de/api/v2.0/Me/Calendars` ). Les clients qui souhaitent ajouter un compte pour afficher les autorisations de calendrier peuvent ajouter la clé de registre telle que décrite dans la rubrique [User expérience Changes for sharing a Calendar in Outlook](https://support.microsoft.com/office/user-experience-changes-for-sharing-a-calendar-in-outlook-5978620a-fe6c-422a-93b2-8f80e488fdec) pour garantir la réussite de cette action. Cette clé de Registre peut être déployée à l’échelle de l’organisation à l’aide de la stratégie de groupe.

- Pendant la phase de migration, l’utilisation des applets de commande PowerShell **New-migrationEndpoint**, **Set-migrationEndpoint** et **test-MigrationsServerAvailability** peut entraîner des erreurs (en cas d’erreur sur le proxy). Cela se produit lorsque la boîte aux lettres d’arbitrage a été migrée vers le monde entier, mais que la boîte aux lettres d’administrateur n’a pas été ou inversement. Pour résoudre ce cas, lors de la création de la session PowerShell client, utilisez la boîte aux lettres d’arbitrage comme indicateur de routage dans le **ConnectionUri**. Par exemple : `New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid?email=Migration.8f3e7716-2011-43e4-96b1-aba62d229136@TENANT.onmicrosoft.de" -Credential $UserCredential -Authentication Basic -AllowRedirection`

- Si vous utilisez Exchange Online hybride :

    - Vous devez réexécuter l’Assistant Configuration hybride (HCW) pour mettre à jour la configuration locale par rapport à Microsoft Cloud Deutschland avant la transition, puis réexécuter l’HCW lors du nettoyage sur les services Office 365. Des mises à jour DNS supplémentaires peuvent être nécessaires si vous utilisez des domaines personnalisés.

Pour plus d’informations sur les actions requises pendant la phase de migration de cette charge de travail ou sur l’impact de l’administration ou de l’utilisation, consultez la section Exchange Online des [phases et des actions de migration](ms-cloud-germany-transition-phases.md#exchange-online).

## <a name="office-services"></a>Services Office

Le service le plus récemment utilisé dans Office est un basculement entre le service Germany et les services Office 365, et non une migration. Seuls les liens MRU du côté des services Office 365 seront visibles après la migration à partir du portail Office.com. Les liens MRU du service d’Allemagne ne sont pas visibles en tant que liens MRU dans les services Office 365. Dans Office 365, les liens MRU ne sont accessibles qu’une fois la migration du client terminée.

## <a name="sharepoint-online-and-onedrive"></a>SharePoint Online et OneDrive

- Une fois la migration de SharePoint Online vers la région allemande terminée, les index de données sont recréés. Les fonctionnalités qui dépendent des index de recherche peuvent être affectées lors de la réindexation.

- Si votre organisation utilise toujours les flux de travail SharePoint 2010, ils ne fonctionneront plus après le 31 décembre 2021. Les flux de travail SharePoint 2013 resteront pris en charge, bien qu’ils soient désactivés par défaut pour les nouveaux clients à compter du 1er novembre 2020. Une fois la migration vers le service SharePoint Online terminée, nous vous recommandons de passer à Power automate ou d’autres solutions prises en charge.

- Une fois la migration OneDrive terminée vers la région allemande, les index de données sont recréés. Les fonctionnalités qui dépendent des index de recherche peuvent être affectées lors de la réindexation en cours.


## <a name="more-information"></a>Plus d’informations

Mise en route :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client lors de la migration](ms-cloud-germany-transition-experience.md)

Navigation par le biais de la transition :

- [Actions et impacts sur les phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour les [services](ms-cloud-germany-transition-add-general.md), les [appareils](ms-cloud-germany-transition-add-devices.md), les [expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications Cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
