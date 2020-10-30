---
title: 'Prise en charge des applications clientes Microsoft 365 : Sign-On unique'
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
description: Dans cet article, Découvrez les plateformes, les clients et les modules PowerShell qui prennent en charge l’authentification unique pour Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b70f0c1ec4a6e94651b987830c8b29993732a3c2
ms.sourcegitcommit: 04a43a146cb62a10b1a4555ec3bed49eb08fbb99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48806661"
---
# <a name="microsoft-365-client-app-support-single-sign-on"></a>Prise en charge des applications clientes Microsoft 365 : Sign-On unique

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L’authentification unique (SSO) renforce la sécurité et la commodité lorsque vos utilisateurs se connectent à des applications dans Azure Active Directory. Avec l’authentification unique, les utilisateurs se connectent une seule fois avec un compte pour accéder aux appareils liés aux services de domaine Active Directory (AD DS) locaux, aux applications SaaS (Software as a service) et applications Web.

En savoir plus sur l' [authentification unique](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="supported-clients--platforms"></a>Clients & plateformes pris en charge

Les versions les plus récentes des clients et des plateformes suivants prennent en charge l’authentification unique. Pour plus d’informations sur la prise en charge de la plateforme dans Microsoft 365, voir [System Requirements for microsoft 365](https://products.office.com/office-system-requirements).
<br>
<br>

| Clients | Android | iOS | Mac| Windows 10 <br> Applications modernes| Windows 10 <br> Desktop |
|:---|:---:|:---:|:---:|:---:|:---:|
| Access | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Portail d’entreprise | S/O | ![Pris en charge](../media/check-mark.png) | Vision | ![Pris en charge](../media/check-mark.png) | N/A |
| Auxquelles | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Delve | Vision | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Edge | ![Pris en charge](../media/check-mark.png) | Vision | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Excel | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Kaizala | ![Pris en charge](../media/check-mark.png) | Vision | N/A | N/A | N/A |
| Office Lens| ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Office Mobile | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Portail Office | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| OneDrive | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Vision | ![Pris en charge](../media/check-mark.png) | Vision |
| OneNote | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Vision |
| Outlook | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Vision | ![Pris en charge](../media/check-mark.png) |
| Planificateur | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Power Apps | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | Vision | S/O |
| Power Automate | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Power BI | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | Vision |
| PowerPoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Project | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Éditeur | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Skype Entreprise | Vision | Vision | N/A | N/A | N/A |
| SharePoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Notes du pense-bête | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Flux | Vision | Vision | N/A | N/A | N/A |
| Sway | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Teams | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Vision | S/O | Vision |
| Action | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Visio | S/O | ![Pris en charge](../media/check-mark.png) | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Tableau blanc collaboratif | S/O | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Word | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Yammer | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | Vision |

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

- [Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0)
- [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell)
- [SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
