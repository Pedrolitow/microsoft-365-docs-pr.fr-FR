---
title: 'Prise en charge des applications clientes Microsoft 365 : Sign-On'
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
description: Dans cet article, découvrez les plateformes, les clients et les modules PowerShell qui la prise en charge de l' sign-on unique pour Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5a685f04ed64a89cda026ff9380aac7c6c2b3ea4
ms.sourcegitcommit: 8e696c084d097520209c864140af11aa055b979e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50097197"
---
# <a name="microsoft-365-client-app-support-single-sign-on"></a>Prise en charge des applications clientes Microsoft 365 : Sign-On

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L' sign-on unique (SSO) ajoute sécurité et commodité lorsque vos utilisateurs se connectent aux applications dans Azure Active Directory. Avec l' sign-on unique, les utilisateurs se connectent une fois avec un compte pour accéder aux appareils joints au domaine AD DS (Active Directory Domain Services) locaux, aux applications SaaS (Software as a Service) et aux applications web.

En savoir plus [sur l' sign-on unique.](/azure/active-directory/manage-apps/what-is-single-sign-on)

## <a name="supported-clients--platforms"></a>Clients pris en charge & plateformes

Les dernières versions des plateformes et des clients suivants prisent en charge l' sign-on unique. Pour plus d’informations sur la prise en charge des plateformes dans Microsoft 365, voir [la demande système requise pour Microsoft 365.](/microsoft-365/microsoft-365-and-office-resources)
<br>
<br>

| Clients | Android | iOS | Mac| Windows 10 <br> Applications modernes| Windows 10 <br> Desktop |
|:---|:---:|:---:|:---:|:---:|:---:|
| Access | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Portail d’entreprise | S/O | ![Pris en charge](../media/check-mark.png) | Planifié | ![Pris en charge](../media/check-mark.png) | N/A |
| Cortana | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Delve | Planifié | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Microsoft Edge | ![Pris en charge](../media/check-mark.png) | Planifié | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Excel | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Kaizala | ![Pris en charge](../media/check-mark.png) | Planifié | N/A | N/A | N/A |
| Office Lens| ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Office Mobile | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Portail Office | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| OneDrive | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Planifié | ![Pris en charge](../media/check-mark.png) | Planifié |
| OneNote | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Planifié |
| Outlook | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Planifié | ![Pris en charge](../media/check-mark.png) |
| Planificateur | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Power Apps | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | Planifié | S/O |
| Power Automate | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Power BI | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | Planifié |
| PowerPoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Project | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Éditeur | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Skype Entreprise | Planifié | Planifié | N/A | N/A | N/A |
| SharePoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Notes pense-tout | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Stream | Planifié | Planifié | N/A | N/A | N/A |
| Sway | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Teams | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | Planifié | S/O | Planifié |
| To Do | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Visio | S/O | ![Pris en charge](../media/check-mark.png) | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Tableau blanc collaboratif | S/O | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Word | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Yammer | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | Planifié |

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

- [Azure Active Directory PowerShell](/powershell/azure/active-directory/overview?view=azureadps-2.0)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)
- [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
