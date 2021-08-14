---
title: 'Microsoft 365 Prise en charge des applications clientes : authentification basée sur les certificats'
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
description: Dans cet article, recherchez des détails sur Microsoft 365 prise en charge de l’application cliente pour l’authentification basée sur les certificats.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cef2cc9084b44e568afd1df7291a21dce8c4ae3dd7a3feb8dcba31f20d5a31b0
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53855051"
---
# <a name="microsoft-365-client-app-support-certificate-based-authentication"></a>Microsoft 365 Prise en charge des applications clientes : authentification basée sur les certificats

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L’authentification moderne est un terme générique pour une combinaison de méthodes d’authentification et d’autorisation. Ces méthodes sont les suivantes :

- **Méthodes d’authentification**: authentification multifacteur ; Authentification basée sur un certificat client.
- **Méthodes d’autorisation**: implémentation d’Open Authorization (OAuth) par Microsoft.

L’authentification moderne est activée à l’aide d’une bibliothèque d’authentification, comme la bibliothèque d’authentification Active Directory (ADAL) ou la bibliothèque d’authentification Microsoft (MSAL). L’authentification moderne est ce que les clients utilisent pour authentifier et autoriser l’accès Microsoft 365 ressources. L’authentification moderne utilise OAuth et fournit un mécanisme sécurisé permettant aux clients d’accéder Microsoft 365 services, sans nécessiter l’accès aux informations d’identification de l’utilisateur. Lors de la connectez-vous, l’utilisateur s’authentifier directement auprès Azure Active Directory et reçoit une paire de jetons d’accès/actualisation en retour. Le jeton d’accès accorde au client l’accès aux ressources appropriées dans Microsoft 365 client. Un jeton d’actualisation est utilisé pour obtenir une nouvelle paire de jetons d’accès ou d’actualisation à l’expiration du jeton d’accès actuel.

L’authentification moderne prend en charge différents mécanismes d’authentification, tels que l’authentification basée sur les certificats. Les clients sur Windows, Android ou iOS peuvent utiliser l’authentification basée sur les certificats (CBA) pour s’authentifier Azure Active Directory l’aide d’un certificat client sur l’appareil. Au lieu d’un nom d’utilisateur/mot de passe classique, le certificat est utilisé pour obtenir une paire de jetons d’accès/actualisation à partir Azure Active Directory.

En savoir plus sur [l’authentification basée sur les certificats.](/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started)

## <a name="supported-clients--platforms"></a>Clients pris en charge & plateformes

Les dernières versions des plateformes et des clients suivants prendre en charge l’authentification basée sur les certificats lors de la signature de comptes Azure Active Directory au sein du client (par exemple, lors de l’ajout d’un compte à l’application). Pour plus d’informations sur la prise en charge de la plateforme dans Microsoft 365, voir [La Microsoft 365](/microsoft-365/microsoft-365-and-office-resources).
<br>
<br>

[!INCLUDE [Certificate-based authentication services support table](../includes/microsoft-365-client-support-certificate-based-authentication-include.md)]

> [!NOTE]
> Edge pour iOS et Android prend en charge l’authentification basée sur les certificats lors de l’ajout de flux de compte. Edge pour iOS et Android ne prend pas en charge l’authentification basée sur les certificats lors de l’authentification sur des sites web, qui sont généralement des sites intranet. <br><br>  Dans ce scénario, un utilisateur navigue vers un site web (généralement sur l’intranet) où il doit s’authentifier via un certificat. Cela n’implique pas du tout l’authentification moderne et ne tire pas parti d’une bibliothèque d’authentification Microsoft. Cela est dû à une limitation avec iOS : iOS empêche les applications tierces d’accéder auchain système dans lequel les certificats sont stockés (seules les applications Apple et le contrôleur [Safari WebView](https://developer.apple.com/documentation/safariservices/sfsafariviewcontroller) peuvent accéder auchain du système). <br><br> Comme Edge s’appuie sur l’infrastructure [WebKit](https://developer.apple.com/documentation/webkit) pour le rendu des sites web, Edge ne peut pas accéder au trousseaux système et présenter à l’utilisateur un choix de certificat. Malheureusement, cela est dû à l’architecture d’Apple.

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

- [Azure Active Directory PowerShell](/powershell/azure/active-directory/overview)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)
- [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
