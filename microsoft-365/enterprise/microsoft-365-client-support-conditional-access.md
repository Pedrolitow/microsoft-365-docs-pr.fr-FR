---
title: 'Prise en charge des applications clientes Microsoft 365 : accès conditionnel'
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
f1.keywords:
- NOCSH
description: Dans cet article, Découvrez les plateformes, les clients et les modules PowerShell qui prennent en charge l’accès conditionnel pour Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dc187a26cd3aa644888312327b07fc9a116950cc
ms.sourcegitcommit: 04a43a146cb62a10b1a4555ec3bed49eb08fbb99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48806681"
---
# <a name="microsoft-365-client-app-support-conditional-access"></a>Prise en charge des applications clientes Microsoft 365 : accès conditionnel

Dans l’espace de travail moderne, les utilisateurs peuvent accéder aux ressources de votre organisation à l’aide de divers appareils et applications depuis n’importe quel endroit. Par conséquent, il ne suffit plus de se concentrer sur qui peut accéder à une ressource. Votre organisation doit également prendre en charge la façon et l’emplacement d’accès à une ressource dans votre infrastructure de contrôle d’accès.

Avec l’accès conditionnel au périphérique, à l’emplacement et à l’authentification multifacteur d’Azure Active Directory, vous pouvez répondre à cette nouvelle exigence. L’accès conditionnel est une fonctionnalité d’Azure Active Directory qui vous permet d’appliquer des contrôles sur l’accès aux applications de votre environnement, toutes basées sur des conditions spécifiques et gérées à partir d’un emplacement central.

En savoir plus sur [l’accès conditionnel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/).

## <a name="supported-clients--platforms"></a>Clients & plateformes pris en charge

Les versions les plus récentes des clients et des plateformes suivants prennent en charge l’accès conditionnel. Pour plus d’informations sur la prise en charge de la plateforme dans Microsoft 365, voir [System Requirements for microsoft 365](https://www.microsoft.com/microsoft-365/microsoft-365-and-office-resources).

<br>
<br>

| Clients | Android | iOS | Mac| Windows 10 <br> Applications modernes| Windows 10 <br> Desktop |
|:---|:---:|:---:|:---:|:---:|:---:|
| Administrateur Azure Active Directory | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Access | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Administrateur Azure | N/A | N/A | N/A | N/A | N/A |
| Portail d’entreprise | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A |
| Auxquelles | Vision | Vision | S/O | ![Pris en charge](../media/check-mark.png) | N/A |
| Delve | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Edge | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Excel | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Administrateur Exchange Online | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Formulaires | N/A | N/A | N/A | N/A | N/A |
| Office 365 Admin | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |  |
| Kaizala | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Office Lens| ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Office Mobile | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Portail Office | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| OneDrive | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| OneNote | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Outlook | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Planificateur | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Power Apps | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | Vision | S/O |
| Power Automate | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Power BI | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| PowerPoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Project | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Éditeur | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Skype Entreprise | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A ||
| SharePoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Administrateur SharePoint Online | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Notes du pense-bête | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Flux | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Sway | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Teams | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) |
| Action | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A |
| Visio | S/O | ![Pris en charge](../media/check-mark.png) | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Tableau blanc collaboratif | Vision | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Word | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Analyse de l’espace de travail | N/A | N/A | N/A | N/A | N/A |
| Yammer | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) |

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

- [Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0)
- [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell)
- [SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
