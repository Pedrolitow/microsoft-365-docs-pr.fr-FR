---
title: Évaluation de l’accès continu pour Microsoft 365 - Microsoft 365 entreprise
description: Décrit comment l’évaluation de l’accès conditionnel pour Microsoft 365 et Azure AD de manière proactive met fin aux sessions utilisateur actives et applique les modifications de stratégie de client en temps quasi réel.
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-overview
ms.technology: mdo
ms.openlocfilehash: 1625f266bff322bf77f6eeaeb0d0690853587dad
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60661796"
---
# <a name="continuous-access-evaluation-for-microsoft-365"></a>Évaluation de l’accès continu pour Microsoft 365

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

Les services cloud modernes qui utilisent OAuth 2.0 pour l’authentification s’appuient traditionnellement sur l’expiration du jeton d’accès pour révoquer l’accès d’un compte d’utilisateur. En pratique, cela signifie que même si un administrateur révoque l’accès d’un compte d’utilisateur, l’utilisateur pourra toujours y accéder jusqu’à l’expiration du jeton d’accès, qui, pour Microsoft 365 par défaut, était jusqu’à une heure après l’événement de révocation initial.  

L’évaluation de l’accès conditionnel pour Microsoft 365 et Azure Active Directory (Azure AD) met fin de manière proactive aux sessions utilisateur actives et applique les modifications de stratégie de client en temps quasi réel au lieu de s’appuyer sur l’expiration du jeton d’accès. Azure AD avertit les services de Microsoft 365 activés pour l’évaluation de l’accès continu (tels que SharePoint, Teams et Exchange) lorsque le compte d’utilisateur ou le client a changé d’une manière qui nécessite une réévaluation de l’état d’authentification du compte d’utilisateur. 

Lorsqu’un client activé pour l’évaluation de l’accès continu tel que Outlook tente d’accéder à Exchange avec un jeton d’accès existant, le jeton est rejeté par le service, ce qui demande une nouvelle authentification Azure AD. Résultat : l’application en temps quasi réel des modifications de compte d’utilisateur et de stratégie.  

Voici quelques avantages supplémentaires :

- Pour un insider malveillant qui copie et exporte un jeton d’accès valide en dehors de votre organisation, l’évaluation de l’accès continu empêche l’utilisation de ce jeton via une stratégie d’emplacement d’adresse IP Azure AD. Avec l’évaluation de l’accès continu, Azure AD synchronise les stratégies vers les services Microsoft 365 pris en charge. Ainsi, lorsqu’un jeton d’accès tente d’accéder au service en dehors de la plage d’adresses IP de la stratégie, le service rejette le jeton. 

- L’évaluation de l’accès continu améliore la résilience en nécessitant moins d’actualisations de jeton. Étant donné que les services de prise en charge reçoivent des notifications proactives sur la nécessité d’une réauthentisation, les Azure AD peuvent émettre des jetons à plus longue durée de vie, par exemple, au-delà d’une heure. Avec des jetons à durée de vie plus longue, les clients n’ont pas besoin de demander une actualisation de jeton à Azure AD aussi souvent, de sorte que l’expérience utilisateur est plus résiliente.

Voici quelques exemples de situations dans lesquelles l’évaluation de l’accès continu améliore la sécurité du contrôle d’accès utilisateur : 

- Le mot de passe d’un compte d’utilisateur a été compromis de sorte qu’un administrateur invalide toutes les sessions existantes et réinitialise leur mot de passe à partir du Centre d'administration Microsoft 365. En temps quasi réel, toutes les sessions utilisateur existantes avec Microsoft 365 services sont invalidées. 

- Un utilisateur travaillant sur un document dans Word prend sa tablette vers un café public qui ne se trouve pas dans une plage d’adresses IP définie par l’administrateur et approuvée. Dans le café, l’accès de l’utilisateur au document est immédiatement bloqué. 

Pour Microsoft 365, l’évaluation de l’accès continu est actuellement prise en charge par :

- Exchange, SharePoint et Teams services. 
- Outlook, Teams, Office et OneDrive dans un navigateur web et pour les clients Win32, iOS, Android et Mac. 

Microsoft travaille sur des services et des clients Microsoft 365 supplémentaires pour prendre en charge l’évaluation de l’accès continu. 

L’évaluation de l’accès continu sera incluse dans toutes les versions Office 365 et Microsoft 365. La configuration des stratégies d’accès conditionnel Azure AD Premium P1, qui est incluse dans toutes Microsoft 365 versions.

>[!Note]
>Consultez [cet article pour](/azure/active-directory/conditional-access/concept-continuous-access-evaluation#limitations) les limitations de l’évaluation de l’accès continu.
>

## <a name="scenarios-supported-by-microsoft-365"></a>Scénarios pris en charge par Microsoft 365 

L’évaluation de l’accès continu prend en charge deux types d’événements : 

- Les événements critiques sont ceux dans lesquels un utilisateur doit perdre l’accès. 
- L’évaluation de la stratégie d’accès conditionnel se produit lorsqu’un utilisateur doit perdre l’accès à une ressource basée sur une stratégie définie par l’administrateur.  

Les événements critiques sont les suivants : 

- Le compte d’utilisateur est désactivé 
- Le mot de passe est modifié 
- Les sessions utilisateur sont révoquées 
- L’authentification multifacteur est activée pour l’utilisateur 
- Le risque de compte augmente en fonction de l’évaluation de l’accès [à partir Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection)

L’évaluation de la stratégie d’accès conditionnel se produit lorsque le compte d’utilisateur ne se connecte plus à partir d’un réseau approuvé. 

Les services de Microsoft 365 suivants peuvent actuellement prendre en charge l’évaluation de l’accès continu en écoute des événements Azure AD.  

| Type d’application  | Exchange | SharePoint | Équipes |
|:-------|:-----|:-------|:-------|
| **Événements critiques :** |  |  |  |
| Révocation des utilisateurs | Pris en charge | Pris en charge | Pris en charge |
| Risque de l’utilisateur | Pris en charge | Non pris en charge | Non pris en charge |
| **Évaluation de la stratégie d’accès conditionnel :** |  |  |  |
| Stratégie d’emplacement des adresses IP | Pris en charge | Pris en charge* | Pris en charge |

* SharePoint Office navigateur web prend en charge l’application de stratégies IP instantanées en activant le mode strict. Sans mode strict, la durée de vie du jeton d’accès est d’une heure.   

Pour plus d’informations sur la façon de configurer une stratégie d’accès conditionnel, consultez [cet article.](/azure/active-directory/conditional-access/overview)

## <a name="microsoft-365-clients-supporting-continuous-access-evaluation"></a>Microsoft 365 clients de prise en charge de l’évaluation de l’accès continu 

Les clients activés pour l’évaluation de l’accès continu pour Microsoft 365 supportent une demande de revendication, c’est-à-dire une redirection d’une session utilisateur vers Azure AD pour la réauthentisation, lorsqu’un jeton utilisateur mis en cache est rejeté par un service Microsoft 365 activé pour l’évaluation de l’accès continu.  

Les clients suivants supportent l’évaluation de l’accès continu sur le web, Win32, iOS, Android et Mac : 

- Outlook 
- Teams 
- Office*
- SharePoint 
- OneDrive 

* La demande de revendication n’est pas prise en charge Office pour le web.

Pour les clients qui ne la prisent pas en charge de l’évaluation de l’accès continu, la durée de vie du jeton d’Microsoft 365 reste d’une heure par défaut.    

## <a name="see-also"></a>Voir aussi

- [Évaluation de l’accès continu](/azure/active-directory/conditional-access/concept-continuous-access-evaluation)
- [Documentation sur l’accès conditionnel](/azure/active-directory/conditional-access/overview)
- [Azure AD Documentation sur la protection des identités](/azure/active-directory/identity-protection/overview-identity-protection)
