---
title: 'Prise en charge des applications clientes Microsoft 365 : authentification basée sur des certificats'
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Dans cet article, vous trouverez des détails sur la prise en charge de l’application cliente Microsoft 365 pour l’authentification basée sur les certificats..
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2f2f5acb88e49cf7a81bd5e89c0c9c85feea6672
ms.sourcegitcommit: 86e878849a8bdd456cee6a3f49939d26223fb626
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48997802"
---
# <a name="microsoft-365-client-app-support-certificate-based-authentication"></a>Prise en charge des applications clientes Microsoft 365 : authentification basée sur des certificats

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L’authentification moderne est un terme générique pour une combinaison de méthodes d’authentification et d’autorisation. Cela inclut ce qui suit :

- Méthodes d’authentification : authentification multifacteur ; Authentification basée sur les certificats clients.

- Méthodes d’autorisation : mise en œuvre par Microsoft de l’autorisation Open (OAuth).

L’authentification moderne est activée par le biais de l’utilisation d’une bibliothèque d’authentification, telle que ADAL ou MSAL. L’authentification moderne est celle que les clients utilisent pour authentifier et autoriser l’accès aux ressources Microsoft 365. L’authentification moderne s’appuie sur OAuth et fournit un mécanisme sécurisé permettant aux clients d’accéder aux services Microsoft 365, sans avoir à accéder aux informations d’identification de l’utilisateur. Lors de la connexion, l’utilisateur s’authentifie directement auprès d’Azure Active Directory et reçoit une paire de jetons accès/actualiser en retour. Le jeton d’accès octroie au client l’accès aux ressources appropriées dans le client Microsoft 365. Un jeton d’actualisation est utilisé pour obtenir une nouvelle paire de jetons d’accès ou d’actualisation lorsque le jeton d’accès actuel arrive à expiration.

L’authentification moderne prend en charge différents mécanismes d’authentification, tels que l’authentification basée sur les certificats. Les clients sur des appareils Windows, Android ou iOS peuvent utiliser l’authentification basée sur les certificats (CBA) pour s’authentifier auprès d’Azure Active Directory à l’aide d’un certificat client sur l’appareil. Au lieu d’un nom d’utilisateur/mot de passe standard, le certificat est utilisé pour obtenir une paire de jetons accès/actualisation à partir d’Azure Active Directory.

En savoir plus sur [l’authentification basée sur les certificats](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started).

## <a name="supported-clients--platforms"></a>Clients & plateformes pris en charge

Les versions les plus récentes des clients et des plateformes suivants prennent en charge l’authentification basée sur les certificats lors de la connexion à des comptes Azure Active Directory au sein du client (par exemple, lors de l’ajout d’un compte à l’application). Pour plus d’informations sur la prise en charge de la plateforme dans Microsoft 365, voir [System Requirements for microsoft 365](https://www.microsoft.com/microsoft-365/microsoft-365-and-office-resources).
<br>
<br>

| Clients | Android | iOS | Mac| Windows 10 <br> Applications modernes| Windows 10 <br> Desktop |
|:---|:---:|:---:|:---:|:---:|:---:|
| Administrateur Azure Active Directory | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Access | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Administrateur Azure | N/A | N/A | N/A | N/A | N/A |
| Portail d’entreprise | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A |
| Auxquelles | Vision | Vision | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Delve | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Edge | ![Pris en charge](../media/check-mark.png)* | ![Pris en charge](../media/check-mark.png)* | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Excel | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Administrateur Exchange Online | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Formulaires | N/A | N/A | N/A | N/A | N/A |
| Office 365 Admin | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |  |
| Kaizala | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Office Lens| ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Office Mobile | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Portail Office | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| OneDrive | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Vision | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| OneNote | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Outlook | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Planificateur | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Power Apps | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Power Automate | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Power BI | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| PowerPoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Project | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Éditeur | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Skype Entreprise | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) |
| Administrateur Skype entreprise | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| SharePoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Administrateur SharePoint Online | Vision | Vision | N/A | N/A | N/A |
| Notes du pense-bête | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Flux | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Sway | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Teams | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | Vision |
| Action | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A |
| Visio | N/A | ![Pris en charge](../media/check-mark.png) | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Tableau blanc collaboratif | Vision | Vision | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Word | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Analyse de l’espace de travail | N/A | N/A | N/A | N/A | N/A |
| Yammer | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Vision | N/A | Vision |

> [!IMPORTANT]
> Edge pour iOS et Android prend en charge l’authentification basée sur des certificats lors de l’ajout de flux. Edge pour iOS et Android ne prend pas en charge l’authentification basée sur les certificats lors de l’exécution de l’authentification sur des sites Web, qui sont généralement des sites intranet. Dans ce scénario, un utilisateur accède à un site Web (généralement sur l’intranet) où le site Web demande à l’utilisateur de s’authentifier via un certificat. Cela n’implique pas du tout l’authentification moderne et n’utilise pas de bibliothèque d’authentification Microsoft. Ceci est dû à une limitation de iOS : iOS empêche les applications tierces d’accéder à la chaîne de trousseau système où les certificats sont stockés (seules les applications Apple et le [contrôleur WebView Safari](https://developer.apple.com/documentation/safariservices/sfsafariviewcontroller) peuvent accéder à la chaîne de trousseau système).

 

Comme le serveur Edge s’appuie sur WebKit, Edge ne peut pas accéder au trousseau du système et présenter l’utilisateur avec le choix de certificat. Ceci, malheureusement, est par conception en raison de l’architecture d’Apple.

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

- [Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0)
- [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell)
- [SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

