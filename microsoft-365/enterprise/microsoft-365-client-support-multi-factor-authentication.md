---
title: 'Microsoft 365 Prise en charge des applications clientes : authentification multifacteur'
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
description: Dans cet article, découvrez les plateformes, les clients et les modules PowerShell qui la prise en charge de l’authentification multifacteur pour Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d18ce34ef3b963b66ca2309f8ef0c9cc244aaeb6da4865e9a16a91623430c735
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53855014"
---
# <a name="microsoft-365-client-app-support-multi-factor-authentication"></a>Microsoft 365 Prise en charge des applications clientes : authentification multifacteur

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour fournir un niveau de sécurité supplémentaire pour les sign-ins, les clients peuvent être configurés pour utiliser l’authentification multifacteur (MFA), qui utilise à la fois un mot de passe utilisateur et une autre méthode de vérification utilisateur en fonction des éléments suivants :

- Quelque chose en leur possession qui n’est pas facilement dupliqué, tel qu’un smartphone.
- Quelque chose que l’utilisateur possède de manière unique et err ment, par exemple ses empreintes digitales, son visage ou tout autre attribut biométrique

En savoir plus sur [l’authentification multifacteur.](/azure/active-directory/authentication/multi-factor-authentication)

## <a name="supported-clients--platforms"></a>Clients pris en charge & plateformes

Les dernières versions des plateformes et des clients suivants prisent en charge l’authentification multifacteur. Pour plus d’informations sur la prise en charge de la plateforme dans Microsoft 365, voir [La Microsoft 365](/microsoft-365/microsoft-365-and-office-resources).
<br>
<br>

[!INCLUDE [Multi-factor authentication services support table](../includes/microsoft-365-client-support-modern-authentication-include.md)]

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

- [Azure Active Directory PowerShell](/powershell/azure/active-directory/overview)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)
- [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
