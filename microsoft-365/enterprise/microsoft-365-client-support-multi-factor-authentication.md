---
title: 'Prise en charge des applications clientes Microsoft 365 : authentification multifacteur'
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
description: Dans cet article, découvrez les plateformes, les clients et les modules PowerShell qui supportent l’authentification multifacteur pour Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fdec611fc595cdc15abb0fc1fb7a998f7a615ff7
ms.sourcegitcommit: 8e696c084d097520209c864140af11aa055b979e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50097467"
---
# <a name="microsoft-365-client-app-support-multi-factor-authentication"></a>Prise en charge des applications clientes Microsoft 365 : authentification multifacteur

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour fournir un niveau de sécurité supplémentaire pour les connecteurs, les clients peuvent être configurés pour utiliser l’authentification multifacteur (MFA), qui utilise à la fois un mot de passe utilisateur et une méthode de vérification utilisateur supplémentaire basée sur :

- Quelque chose en leur possession qui n’est pas facilement dupliqué, tel qu’un smartphone.
- Quelque chose que l’utilisateur possède de manière unique et err ment, par exemple ses empreintes digitales, son visage ou tout autre attribut biométrique

En savoir plus sur [l’authentification multifacteur.](/azure/active-directory/authentication/multi-factor-authentication)

## <a name="supported-clients--platforms"></a>Clients pris en charge & plateformes

Les dernières versions des plateformes et des clients suivants prisent en charge l’authentification multifacteur. Pour plus d’informations sur la prise en charge des plateformes dans Microsoft 365, voir la demande système [requise pour Microsoft 365.](/microsoft-365/microsoft-365-and-office-resources)
<br>
<br>

| Clients | Android | iOS | Mac| Windows 10 <br> Applications modernes| Windows 10 <br> Desktop |
|:---|:---:|:---:|:---:|:---:|:---:|
| Administrateur Azure Active Directory | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Access | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Administrateur Azure | N/A | N/A | N/A | N/A | N/A |
| Portail d’entreprise | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A |
| Cortana | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Delve | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Microsoft Edge | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
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
| Power Apps | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Power Automate | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Power BI | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| PowerPoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Project | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Éditeur | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Skype Entreprise | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) |
| Administrateur Skype Entreprise | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| SharePoint | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Administrateur SharePoint Online | N/A | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Notes pense-tout | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Stream | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | N/A | N/A |
| Sway | N/A | N/A | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Teams | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) |
| To Do | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A |
| Visio | S/O | ![Pris en charge](../media/check-mark.png) | N/A | N/A | ![Pris en charge](../media/check-mark.png) |
| Tableau blanc collaboratif | Planifié | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) | N/A |
| Word | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) |
| Analyse de l’espace de travail | N/A | N/A | N/A | N/A | N/A |
| Yammer | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | ![Pris en charge](../media/check-mark.png) | N/A | ![Pris en charge](../media/check-mark.png) |

## <a name="supported-powershell-modules"></a>Modules PowerShell pris en charge

- [Azure Active Directory PowerShell](/powershell/azure/active-directory/overview?view=azureadps-2.0)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)
- [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)