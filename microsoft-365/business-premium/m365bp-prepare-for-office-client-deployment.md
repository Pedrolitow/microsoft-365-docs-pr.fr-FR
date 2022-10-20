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
ms.date: 10/18/2022
ms.localizationpriority: high
ms.collection:
- tier1
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
ROBOTS: NO INDEX, NO FOLLOW
description: Découvrez comment installer automatiquement les applications Microsoft 365 32 bits sur les ordinateurs Windows et les mettre à jour dans Microsoft 365 Business Premium.
ms.openlocfilehash: bb88f426cb5c252da291e2a851260dbeca5f9159
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68634847"
---
# <a name="prepare-to-automatically-install-microsoft-365-apps-to-client-computers"></a>Préparer l’installation automatique des applications Microsoft 365 sur les ordinateurs clients

Utilisez Microsoft 365 Business Premium pour installer automatiquement les applications Microsoft 365 32 bits sur les ordinateurs Windows et les tenir à jour avec les mises à jour.
  
L’installation automatique fonctionne mieux si l’ordinateur : 

- est sur Windows for Business.
  
- n’a pas d’applications de bureau Office existantes (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access et OneDrive) OU une version existante d’Office « Démarrer en un clic » est installée.

To determine if you have the Click-to-Run version of Office, in any Office app go to **File** \> **Account** ( **Office Account** in Outlook). If you see **Office Updates** as shown in the following figure, then the installation was done by using Click-to-Run.
  
![Capture d’écran des mises à jour d’Office dans le compte d’application Office.](./../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
## <a name="requirements-for-using-this-feature"></a>Configuration requise pour l’utilisation de cette fonctionnalité
  
Travaille avec :
  
- Un utilisateur disposant d’une licence d’utilisateur Windows Business, d’une licence active Microsoft 365 entreprise, de Windows 10 Creators Update et qui est joint à Azure Active Directory.

Ne fonctionne pas avec : 

- Applications Microsoft 365 64 bits (exemple : Word, Excel, PowerPoint). Si des applications Microsoft 365 64 bits sont requises, cette fonctionnalité n’est pas adaptée, car il n’existe aucune prise en charge du déclenchement d’une version 64 bits 2016 « Démarrer en un clic » d’Office à partir de la console d’administration Microsoft 365 pour les entreprises.

- Any 2016 Windows Installer (MSI) standalone apps (for example, Visio or Project). Microsoft 365 for business upgrades Office to the Click-to-Run version of Office 2016, and that doesn't work with Office 2016 MSI standalone applications.

Le tableau suivant indique l’action que les utilisateurs finaux ou les administrateurs peuvent avoir à entreprendre, en fonction de leur état de début, pour obtenir une version 32 bits « Démarrer en un clic » réussie du déploiement d’Office à partir de la console d’administration Microsoft 365 pour les entreprises.<br/>


|Situation de départ à l'installation d'Office|Action à entreprendre avant Microsoft 365 pour l’installation d’Office pour les entreprises|État final|
|:-----|:-----|:-----|
|Aucune suite Office installée  |Aucune  |Office 2016 32 bits est installé à l’aide du mode Démarrer en un clic  |
|Version 32 bits « Démarrer en un clic » d'Office présente (2016 ou versions antérieures) et aucune application autonome  |Aucune  |Mise à niveau vers la dernière version 32 bits « Démarrer en un clic » d'Office 2016, le cas échéant **\*** |
|Version 32 bits « Démarrer en un clic » d’Office et « Démarrer en un clic » 32 bits ou 64 bits d’applications Microsoft 365 autonomes (par exemple, Visio, Project)  |Aucun  |Les applications autonomes ne sont pas affectées. Mise à niveau de la suite vers la version 32 bits « Démarrer en un clic » d'Office 2016  |
|Version 32 bits « Démarrer en un clic » existante d’Office et toutes les applications Microsoft 365 autonomes MSI 32 bits ou 64 bits (à l’exception de 2016)  |Aucun  |Standalone apps aren't affected. Suite is upgraded to Click-to-Run 32-bit version of Office 2016  |
|Version 64 bits « Démarrer en un clic » d'Office présente  |Désinstallez les applications Microsoft 365 64 bits, si vous pouvez les remplacer par des applications Microsoft 365 32 bits.  |Si les applications 64 bits d'Office sont supprimées, la version 32 bits « Démarrer en un clic » d'Office 2016 est installée  |
|Installation MSI d'Office 2016 existante, avec ou sans applications autonomes  |Désinstaller la version MSI d'Office 2016.  |La version 32 bits « Démarrer en un clic » d'Office 2016 est installée. Aucune modification apportée aux applications autonomes.  |
|Installation MSI existante d’Office 2013 (ou version antérieure) et/ou d’applications Microsoft 365 autonomes  |Aucune  |Coexistence de la version 32 bits « Démarrer en un clic » d'Office 2016 avec l'installation MSI d'Office préexistante (et les applications autonomes)  |

 **(\*) Note:** Does not upgrade to Click-to-Run 32-bit version of Office 2016 due to a known bug. A fix is in progress. 

## <a name="next-objective"></a>Objectif suivant

[Créer des paramètres de protection d’application](m365bp-protection-settings-for-windows-10-devices.md)
  