---
title: Préparer le déploiement du client Office avec Microsoft 365 Business Premium
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-security
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: high
ms.collection:
- tier1
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
ROBOTS: NO INDEX, NO FOLLOW
description: Découvrez comment installer automatiquement les applications Office 32 bits sur les ordinateurs Windows et les maintenir à jour dans Microsoft 365 Business Premium.
ms.openlocfilehash: 48357de681d1647e3ce9cc84fedb831588e27ed8
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68097070"
---
# <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>Préparer l'installation automatique d'applications Office sur des ordinateurs clients

Utilisez Microsoft 365 Business Premium pour iautomatiquement les applications Office 32 bits sur les ordinateurs Windows et les tenir à jour.
  
L’installation automatique fonctionne mieux si l’ordinateur : 

- est sur Windows for Business.
  
- n’a pas d’applications de bureau Office existantes (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access et OneDrive) OU une version existante d’Office « Démarrer en un clic » est installée.

To determine if you have the Click-to-Run version of Office, in any Office app go to **File** \> **Account** ( **Office Account** in Outlook). If you see **Office Updates** as shown in the following figure, then the installation was done by using Click-to-Run.
  
![Capture d’écran des mises à jour d’Office dans le compte d’application Office.](./../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
## <a name="requirements-for-using-this-feature"></a>Configuration requise pour l’utilisation de cette fonctionnalité
  
Travaille avec :
  
- Un utilisateur disposant d’une licence d’utilisateur Windows Business, d’une licence active Microsoft 365 entreprise, de Windows 10 Creators Update et qui est joint à Azure Active Directory.

Ne fonctionne pas avec : 

- 64-bit Office apps (example: Word, Excel, PowerPoint). If 64-bit Office apps are required, then this feature isn't a good fit because there's no support for triggering a 64-bit 2016 Click-to-Run version of Office from the Microsoft 365 for business admin console.

- Any 2016 Windows Installer (MSI) standalone apps (for example, Visio or Project). Microsoft 365 for business upgrades Office to the Click-to-Run version of Office 2016, and that doesn't work with Office 2016 MSI standalone applications.

Le tableau suivant indique l’action que les utilisateurs finaux ou les administrateurs peuvent avoir à entreprendre, en fonction de leur état de début, pour obtenir une version 32 bits « Démarrer en un clic » réussie du déploiement d’Office à partir de la console d’administration Microsoft 365 pour les entreprises.<br/>


|Situation de départ à l'installation d'Office|Action à entreprendre avant Microsoft 365 pour l’installation d’Office pour les entreprises|État final|
|:-----|:-----|:-----|
|Aucune suite Office installée  |Aucune  |Office 2016 32 bits est installé à l’aide du mode Démarrer en un clic  |
|Version 32 bits « Démarrer en un clic » d'Office présente (2016 ou versions antérieures) et aucune application autonome  |Aucune  |Mise à niveau vers la dernière version 32 bits « Démarrer en un clic » d'Office 2016, le cas échéant **\*** |
|Version 32 bits « Démarrer en un clic » existante d’Office et « Démarrer en un clic » 32 bits ou 64 bits d’applications Office autonomes (par exemple, Visio, Project)  |Aucun  |Standalone apps aren't affected. Suite is upgraded to Click-to-Run 32-bit version of Office 2016  |
|Version 32 bits « Démarrer en un clic » d'Office présente et applications autonomes 32 ou 64 bits MSI (à l'exception de 2016) présentes  |Aucune  |Standalone apps aren't affected. Suite is upgraded to Click-to-Run 32-bit version of Office 2016  |
|Version 64 bits « Démarrer en un clic » d'Office présente  |Désinstallez les applications Office 64 bits, si vous pouvez les remplacer par des applications Office 32 bits  |Si les applications 64 bits d'Office sont supprimées, la version 32 bits « Démarrer en un clic » d'Office 2016 est installée  |
|Installation MSI d'Office 2016 existante, avec ou sans applications autonomes  |Désinstaller la version MSI d'Office 2016.  |Click-to-Run 32-bit version of Office 2016 is installed. No change to standalone apps  |
|Installation MSI d'Office 2013 (ou version antérieure) présente et/ou des applications Office autonomes présentes  |Aucune  |Coexistence de la version 32 bits « Démarrer en un clic » d'Office 2016 avec l'installation MSI d'Office préexistante (et les applications autonomes)  |

 **(\*) Note:** Does not upgrade to Click-to-Run 32-bit version of Office 2016 due to a known bug. A fix is in progress. 

## <a name="next-objective"></a>Objectif suivant

[Créer des paramètres de protection d’application](m365bp-protection-settings-for-windows-10-devices.md)
  