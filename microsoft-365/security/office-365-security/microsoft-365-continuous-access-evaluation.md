---
title: Évaluation continue de l’accès pour Microsoft 365 - Microsoft 365 pour les entreprises
description: Décrit comment l’évaluation de l’accès conditionnel pour Microsoft 365 et Azure AD met fin de manière proactive aux sessions utilisateur actives et applique les modifications de stratégie de locataire en quasi-temps réel.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.service: microsoft-365-security
ms.topic: conceptual
audience: Admin
f1.keywords:
- NOCSH
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- m365-security
- m365solution-identitydevice
- m365solution-scenario
- highpri
ms.subservice: mdo
search.appverid: met150
ms.openlocfilehash: a3f531aa8782878b69a5c61a763c01e974e0e069
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68624926"
---
# <a name="continuous-access-evaluation-for-microsoft-365"></a>Évaluation continue de l’accès pour Microsoft 365

Les services cloud modernes qui utilisent OAuth 2.0 pour l’authentification s’appuient généralement sur l’expiration du jeton d’accès pour révoquer l’accès d’un compte d’utilisateur. Dans la pratique, cela signifie que, même si un administrateur révoque l’accès d’un compte d’utilisateur, l’utilisateur aura toujours accès jusqu’à ce que le jeton d’accès expire, ce qui, par défaut, pour Microsoft 365, était jusqu’à une heure après l’événement de révocation initial.

L’évaluation de l’accès conditionnel pour Microsoft 365 et Azure Active Directory (Azure AD) met fin de manière proactive aux sessions utilisateur actives et applique les modifications de stratégie de locataire en quasi temps réel au lieu de s’appuyer sur l’expiration du jeton d’accès. Azure AD avertit les services Microsoft 365 avec évaluation continue (tels que SharePoint, Teams et Exchange) lorsque le compte d’utilisateur ou le locataire a changé d’une manière qui nécessite une réévaluation de l’état d’authentification du compte d’utilisateur.

Lorsqu’un client avec évaluation d’accès continu tel qu’Outlook tente d’accéder à Exchange avec un jeton d’accès existant, le jeton est rejeté par le service, ce qui demande une nouvelle authentification Azure AD. Le résultat est l’application en quasi temps réel des modifications de compte d’utilisateur et de stratégie.

Voici quelques avantages supplémentaires :

- Pour un insider malveillant qui copie et exporte un jeton d’accès valide en dehors de votre organisation, l’évaluation continue de l’accès empêche l’utilisation de ce jeton via la stratégie d’emplacement d’adresse IP Azure AD. Avec l’évaluation continue de l’accès, Azure AD synchronise les stratégies vers les services Microsoft 365 pris en charge. Ainsi, lorsqu’un jeton d’accès tente d’accéder au service à partir de l’extérieur de la plage d’adresses IP de la stratégie, le service rejette le jeton.

- L’évaluation continue de l’accès améliore la résilience en exigeant moins d’actualisations de jetons. Étant donné que les services de prise en charge reçoivent des notifications proactives sur la nécessité d’une réauthentification, Azure AD peut émettre des jetons à durée de vie plus longue, par exemple, au-delà d’une heure. Avec les jetons à durée de vie plus longue, les clients n’ont pas besoin de demander une actualisation des jetons à Partir d’Azure AD aussi souvent, de sorte que l’expérience utilisateur est plus résiliente.

Voici quelques exemples de situations où l’évaluation continue de l’accès améliore la sécurité du contrôle d’accès des utilisateurs :

- Le mot de passe d’un compte d’utilisateur a été compromis de sorte qu’un administrateur invalide toutes les sessions existantes et réinitialise son mot de passe à partir du Centre d'administration Microsoft 365. En quasi-temps réel, toutes les sessions utilisateur existantes avec les services Microsoft 365 sont invalidées.

- Un utilisateur travaillant sur un document dans Word prend sa tablette dans un café public qui n’est pas dans une plage d’adresses IP définie par l’administrateur et approuvée. Dans le café, l’accès de l’utilisateur au document est bloqué immédiatement.

Pour Microsoft 365, l’évaluation continue de l’accès est actuellement prise en charge par :

- Services Exchange, SharePoint et Teams.
- Outlook, Teams, Office et OneDrive dans un navigateur web et pour les clients Win32, iOS, Android et Mac.

Microsoft travaille sur d’autres services et clients Microsoft 365 pour prendre en charge l’évaluation continue de l’accès.

L’évaluation continue de l’accès sera incluse dans toutes les versions de Office 365 et Microsoft 365. La configuration des stratégies d’accès conditionnel nécessite Azure AD Premium P1, qui est incluse dans toutes les versions de Microsoft 365.

> [!NOTE]
> Consultez [cet article](/azure/active-directory/conditional-access/concept-continuous-access-evaluation#limitations) pour connaître les limitations de l’évaluation continue de l’accès.

## <a name="scenarios-supported-by-microsoft-365"></a>Scénarios pris en charge par Microsoft 365

L’évaluation continue de l’accès prend en charge deux types d’événements :

- Les événements critiques sont ceux dans lesquels un utilisateur doit perdre l’accès.
- L’évaluation de la stratégie d’accès conditionnel se produit lorsqu’un utilisateur doit perdre l’accès à une ressource en fonction d’une stratégie définie par l’administrateur.

Les événements critiques sont les suivants :

- Le compte d’utilisateur est désactivé
- Le mot de passe est modifié
- Les sessions utilisateur sont révoquées
- L’authentification multifacteur est activée pour l’utilisateur
- Risque de compte accru en fonction de l’évaluation de l’accès à partir [d’Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection)

L’évaluation de la stratégie d’accès conditionnel se produit lorsque le compte d’utilisateur ne se connecte plus à partir d’un réseau approuvé.

Les services Microsoft 365 suivants prennent actuellement en charge l’évaluation continue de l’accès en écoutant les événements d’Azure AD.

|Type d’application|Exchange|SharePoint|Équipes|
|---|---|---|---|
|**Événements critiques :**||||
|Révocation d’utilisateurs|Pris en charge|Pris en charge|Pris en charge|
|Risque de l’utilisateur|Pris en charge|Non pris en charge|Pris en charge|
|**Évaluation de la stratégie d’accès conditionnel :**||||
|Stratégie d’emplacement d’adresse IP|Pris en charge|Pris en charge\*|Soutenu\**|

\* L’accès au navigateur web SharePoint Office prend en charge l’application instantanée de la stratégie IP en activant le mode strict. Sans mode strict, la durée de vie du jeton d’accès est d’une heure.

\** Les appels, les réunions et les conversations dans Teams ne sont pas conformes aux stratégies d’accès conditionnel basées sur IP.

Pour plus d’informations sur la configuration d’une stratégie d’accès conditionnel, consultez [cet article](/azure/active-directory/conditional-access/overview).

## <a name="microsoft-365-clients-supporting-continuous-access-evaluation"></a>Clients Microsoft 365 qui prennent en charge l’évaluation continue de l’accès

Les clients compatibles avec l’évaluation de l’accès continu pour Microsoft 365 prennent en charge un défi de revendication, qui est une redirection d’une session utilisateur vers Azure AD à des fins d’authentification, lorsqu’un jeton d’utilisateur mis en cache est rejeté par un service Microsoft 365 avec évaluation d’accès continu.

Les clients suivants prennent en charge l’évaluation continue de l’accès sur le web, Win32, iOS, Android et Mac :

- Outlook
- Teams
- Office\*
- SharePoint
- OneDrive

\* Le défi de revendication n’est pas pris en charge sur Office pour le web.

Pour les clients qui ne prennent pas en charge l’évaluation continue de l’accès, la durée de vie du jeton d’accès à Microsoft 365 reste d’une heure par défaut.

## <a name="see-also"></a>Voir aussi

- [Évaluation continue de l'accès](/azure/active-directory/conditional-access/concept-continuous-access-evaluation)
- [Documentation sur l’accès conditionnel](/azure/active-directory/conditional-access/overview)
- [Documentation Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection)
