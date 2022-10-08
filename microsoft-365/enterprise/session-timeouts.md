---
title: Délais d’expiration de session pour Microsoft 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- scotvorg
- M365-security-compliance
description: Découvrez comment les délais d’expiration de session sont utilisés pour équilibrer la sécurité et la facilité d’accès dans les applications clientes Microsoft 365.
ms.openlocfilehash: f14d28e1cba153afcf3afda6f9c7a646079c3002
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68200712"
---
# <a name="session-timeouts-for-microsoft-365"></a>Délais d’expiration de session pour Microsoft 365

Les durées de vie des sessions sont une partie importante de l’authentification pour Microsoft 365 et constituent un composant important dans l’équilibrage de la sécurité et le nombre de fois où les utilisateurs sont invités à entrer leurs informations d’identification.

## <a name="session-times-for-microsoft-365-services"></a>Durées de session pour les services Microsoft 365

Lorsque les utilisateurs s’authentifient dans l’une des applications web ou applications mobiles Microsoft 365, une session est établie. Pendant la durée de la session, les utilisateurs n’ont pas besoin de s’authentifier à nouveau. Les sessions peuvent expirer lorsque les utilisateurs sont inactifs, lorsqu’ils ferment le navigateur ou l’onglet, ou lorsque leur jeton d’authentification expire pour d’autres raisons, telles que la réinitialisation de leur mot de passe. Les services Microsoft 365 ont des délais d’expiration de session différents pour correspondre à l’utilisation classique de chaque service.

Le tableau suivant répertorie les durées de vie des sessions pour les services Microsoft 365 :

| Service Microsoft 365 | Délai d’expiration de session |
|:-----|:-----|
|Centre d’administration Microsoft 365  <br/> |Vous êtes invité à fournir des informations d’identification pour le Centre d’administration toutes les 8 heures.  <br/> |
|SharePoint Online  <br/> |5 jours d’inactivité tant que les utilisateurs choisissent **Conserver ma connexion**. Si l’utilisateur accède à nouveau à SharePoint Online après 24 heures ou plus après la connexion précédente, la valeur du délai d’expiration est réinitialisée à 5 jours.  <br/> |
|Outlook Web App  <br/> |6 heures.  <br/> Vous pouvez modifier cette valeur à l’aide du paramètre  _ActivityBasedAuthenticationTimeoutInterval_ dans [l’applet de commande Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) .  <br/> |
|Azure Active Directory  <br/> (Utilisé par les applications Office et Microsoft 365 dans les clients Windows avec l’authentification moderne activée)  <br/> | L’authentification moderne utilise des jetons d’accès et des jetons d’actualisation pour accorder l’accès utilisateur aux ressources Microsoft 365 à l’aide d’Azure Active Directory. Un jeton d’accès est un jeton web JSON fourni après une authentification réussie et valide pendant 1 heure. Un jeton d’actualisation avec une durée de vie plus longue est également fourni. Lorsque les jetons d’accès expirent, les clients Office utilisent un jeton d’actualisation valide pour obtenir un nouveau jeton d’accès. Cet échange réussit si l’authentification initiale de l’utilisateur est toujours valide.  <br/>  Les jetons d’actualisation sont valides pendant 90 jours et, avec une utilisation continue, ils peuvent être valides jusqu’à révocation.  <br/>  Les jetons d’actualisation peuvent être invalidés par plusieurs événements tels que :  <br/>  Le mot de passe de l’utilisateur a changé depuis l’émission du jeton d’actualisation.  <br/>  Un administrateur peut appliquer des stratégies d’accès conditionnel qui limitent l’accès à la ressource à laquelle l’utilisateur tente d’accéder.  <br/> |
|Applications mobiles SharePoint et OneDrive pour Android, iOS et Windows 10  <br/> |La durée de vie par défaut du jeton d’accès est de 1 heure. La durée maximale d’inactivité par défaut du jeton d’actualisation est de 90 jours.  <br/> [En savoir plus sur les jetons et la configuration des durées de vie des jetons](/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Pour révoquer le jeton d’actualisation, vous pouvez réinitialiser le mot de passe Microsoft 365 de l’utilisateur  <br/> |
|Yammer avec Microsoft 365 Sign-In  <br/> |Durée de vie du navigateur. Si les utilisateurs ferment le navigateur et accèdent à Yammer dans un nouveau navigateur, Yammer les authentifie à nouveau auprès de Microsoft 365. Si les utilisateurs utilisent des navigateurs tiers qui mettent en cache des cookies, ils n’ont peut-être pas besoin de s’authentifier à nouveau lorsqu’ils rouvrent le navigateur.  <br/> > [!NOTE]> Ceci est valide uniquement pour les réseaux utilisant Microsoft 365 Sign-In pour Yammer.           |