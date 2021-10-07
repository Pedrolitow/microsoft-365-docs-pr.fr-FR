---
title: Délai d’Microsoft 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
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
- M365-security-compliance
description: Découvrez comment les délai d’accès aux sessions sont utilisés pour équilibrer la sécurité et la facilité d’accès Microsoft 365 applications clientes.
ms.openlocfilehash: f5b7c87cabfd6f80061c2795568cd53955caa10f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60213264"
---
# <a name="session-timeouts-for-microsoft-365"></a>Délai d’Microsoft 365

Les durées de vie des sessions sont une partie importante de l’authentification pour Microsoft 365 et sont un composant important de l’équilibrage de la sécurité et du nombre de fois où les utilisateurs sont invités à obtenir leurs informations d’identification.

## <a name="session-times-for-microsoft-365-services"></a>Temps de session pour Microsoft 365 services

Lorsque les utilisateurs s’authentifier dans Microsoft 365 applications web ou mobiles, une session est établie. Pendant toute la durée de la session, les utilisateurs n’ont pas besoin de se ré-authentifier. Les sessions peuvent expirer lorsque les utilisateurs sont inactifs, lorsqu’ils ferment le navigateur ou l’onglet, ou lorsque leur jeton d’authentification expire pour d’autres raisons, telles que la réinitialisation de leur mot de passe. Les services Microsoft 365 ont des délai d’ouverture de session différents pour correspondre à l’utilisation classique de chaque service.

Le tableau suivant répertorie les durées de vie des sessions Microsoft 365 services :

| Service Microsoft 365 | Délai d’délai de session |
|:-----|:-----|
|Centre d’administration Microsoft 365  <br/> |Vous êtes invité à fournir des informations d’identification pour le Centre d’administration toutes les 8 heures.  <br/> |
|SharePoint Online  <br/> |5 jours d’inactivité tant que les utilisateurs choisissent Maintenir **la signature.** Si l’utilisateur accède à SharePoint Online une fois que 24 heures ou plus se sont écoulées à partir de la dernière ouverture de contrat, la valeur du délai d’SharePoint est réinitialisée à 5 jours.  <br/> |
|Outlook Web App  <br/> |6 heures.  <br/> Vous pouvez modifier cette valeur à l’aide du paramètre _ActivityBasedAuthenticationTimeoutInterval_ dans la cmdlet [Set-OrganizationConfig.](/powershell/module/exchange/set-organizationconfig)  <br/> |
|Azure Active Directory  <br/> (Utilisé par les applications Office et Microsoft 365 dans Windows clients avec l’authentification moderne activée)  <br/> | L’authentification moderne utilise des jetons d’accès et des jetons d’actualisation pour accorder à l’utilisateur l’accès Microsoft 365 ressources à l’aide Azure Active Directory. Un jeton d’accès est un jeton web JSON fourni après une authentification réussie et est valide pendant 1 heure. Un jeton d’actualisation avec une durée de vie plus longue est également fourni. Lorsque les jetons d’accès expirent, Office clients utilisent un jeton d’actualisation valide pour obtenir un nouveau jeton d’accès. Cet échange réussit si l’authentification initiale de l’utilisateur est toujours valide.  <br/>  Les jetons d’actualisation sont valides pendant 90 jours et, avec une utilisation continue, ils peuvent être valides jusqu’à leur révocation.  <br/>  Les jetons d’actualisation peuvent être invalidés par plusieurs événements tels que :  <br/>  Le mot de passe de l’utilisateur a changé depuis l’émission du jeton d’actualisation.  <br/>  Un administrateur peut appliquer des stratégies d’accès conditionnel qui limitent l’accès à la ressource à l’accès que l’utilisateur tente d’accéder.  <br/> |
|SharePoint et OneDrive applications mobiles pour Android, iOS et Windows 10  <br/> |La durée de vie par défaut du jeton d’accès est de 1 heure. La durée d’inactivité maximale par défaut du jeton d’actualisation est de 90 jours.  <br/> [En savoir plus sur les jetons et la configuration des durées de vie des jetons](/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Pour révoquer le jeton d’actualisation, vous pouvez réinitialiser le mot de passe Microsoft 365 utilisateur  <br/> |
|Yammer avec Microsoft 365 Sign-In  <br/> |Durée de vie du navigateur. Si les utilisateurs ferment le navigateur et accèdent Yammer dans un nouveau navigateur, Yammer les authentifier à nouveau avec Microsoft 365. Si les utilisateurs utilisent des navigateurs tiers qui met en cache les cookies, ils n’ont peut-être pas besoin de s’authentifier à nouveau lorsqu’ils rouvrent le navigateur.  <br/> > [!NOTE]> ce n’est valide que pour les réseaux utilisant Microsoft 365 Sign-In pour Yammer.           |