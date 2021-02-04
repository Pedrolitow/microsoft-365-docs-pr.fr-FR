---
title: 'Prise en charge des applications clientes Microsoft 365 : authentification basée sur les certificats'
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
description: Dans cet article, recherchez des détails sur la prise en charge de l’application cliente Microsoft 365 pour l’authentification basée sur les certificats.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f7ab5e4a2575796e37a115b36a4f78add20414ef
ms.sourcegitcommit: 8e696c084d097520209c864140af11aa055b979e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50097257"
---
# <a name="microsoft-365-client-app-support-certificate-based-authentication"></a>Prise en charge des applications clientes Microsoft 365 : authentification basée sur les certificats

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L’authentification moderne est un terme générique pour une combinaison de méthodes d’authentification et d’autorisation. Cela inclut ce qui suit :

- **Méthodes d’authentification**: authentification multifacteur ; Authentification basée sur un certificat client.
- **Méthodes d’autorisation**: implémentation d’Open Authorization (OAuth) par Microsoft.

L’authentification moderne est activée par le biais d’une bibliothèque d’authentification, telle que la bibliothèque d’authentification Active Directory (ADAL) ou la bibliothèque d’authentification Microsoft (MSAL). L’authentification moderne est ce que les clients utilisent pour authentifier et autoriser l’accès aux ressources Microsoft 365. L’authentification moderne tire parti d’OAuth et fournit un mécanisme sécurisé permettant aux clients d’accéder aux services Microsoft 365, sans nécessiter l’accès aux informations d’identification de l’utilisateur. Lors de la connectez-vous, l’utilisateur s’authentifier directement auprès d’Azure Active Directory et reçoit une paire de jetons d’accès/actualisation en retour. Le jeton d’accès accorde au client l’accès aux ressources appropriées dans le client Microsoft 365. Un jeton d’actualisation est utilisé pour obtenir une nouvelle paire de jetons d’accès ou d’actualisation à l’expiration du jeton d’accès actuel.

L’authentification moderne prend en charge différents mécanismes d’authentification, tels que l’authentification basée sur les certificats. Les clients sur les appareils Windows, Android ou iOS peuvent utiliser l’authentification basée sur les certificats (CBA) pour s’authentifier dans Azure Active Directory à l’aide d’un certificat client sur l’appareil. Au lieu d’un nom d’utilisateur/mot de passe classique, le certificat est utilisé pour obtenir une paire de jetons d’accès/actualisation à partir d’Azure Active Directory.

En savoir plus sur [l’authentification basée sur les certificats.](/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started)

## <a name="supported-clients--platforms"></a>Clients pris en charge & plateformes

Les dernières versions des plateformes et des clients suivants prendre en charge l’authentification basée sur les certificats lors de la signature de comptes Azure Active Directory au sein du client (par exemple, lors de l’ajout d’un compte à l’application). Pour plus d’informations sur la prise en charge des plateformes dans Microsoft 365, voir la demande système [requise pour Microsoft 365.](/microsoft-365/microsoft-365-and-office-resources)
<br>
<br>

| Clients | Android | iOS | Mac| Windows 10 <br> Applications modernes| Windows 10 <br> Desktop |
|:---|:---:|:---:|:---:|:---:|:---:|
| Administrateur Azure Active Directory | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Access | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Administrateur Azure | N/A | N/A | N/A | N/A | N/A |
| Portail d’entreprise | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A |
| Cortana | Planifié | Planifié | S/O | ![Pris en charge](../media/check-mark.png) | N/A |
| Delve | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Edge<sup>1</sup> | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Excel | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Administrateur Exchange Online | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Formulaires | N/A | N/A | N/A | N/A | N/A |
| Office 365 Admin | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |  |
| Kaizala | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Office Lens| ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Office Mobile | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Portail Office | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| OneDrive | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Planifié | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
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
| Administrateur Skype Entreprise | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| SharePoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Administrateur SharePoint Online | Planifié | Planifié | N/A | N/A | N/A |
| Notes pense-tout | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Stream | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Sway | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Teams | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | Planifié |
| To Do | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A |
| Visio | S/O | ![Pris en charge](../media/check-mark.png) | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Tableau blanc collaboratif | Planifié | Planifié | S/O | ![Pris en charge](../media/check-mark.png) | N/A |
| Word | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Analyse de l’espace de travail | N/A | N/A | N/A | N/A | N/A |
| Yammer | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Planifié | S/O | Planifié |

>[!NOTE]
><sup>1</sup> Edge pour iOS et Android prend en charge l’authentification basée sur les certificats lors de l’ajout de flux de compte. Edge pour iOS et Android ne prend pas en charge l’authentification basée sur les certificats lors de l’authentification sur des sites web, qui sont généralement des sites intranet. <br><br>  Dans ce scénario, un utilisateur navigue vers un site web (généralement sur l’intranet) où il doit s’authentifier via un certificat. Cela n’implique pas du tout l’authentification moderne et ne tire pas parti d’une bibliothèque d’authentification Microsoft. Cela est dû à une limitation avec iOS : iOS empêche les applications tierces d’accéder auchain système dans lequel les certificats sont stockés (seules les applications Apple et le contrôleur [Safari WebView](https://developer.apple.com/documentation/safariservices/sfsafariviewcontroller) peuvent accéder auchain système). <br><br> Comme Edge s’appuie sur l’infrastructure [WebKit](https://developer.apple.com/documentation/webkit) pour le rendu des sites web, Edge ne peut pas accéder au trousseaux système et présenter à l’utilisateur un choix de certificat. Malheureusement, cela est dû à l’architecture d’Apple.

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

- [Azure Active Directory PowerShell](/powershell/azure/active-directory/overview?view=azureadps-2.0)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)
- [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

