---
title: Préparer le déploiement du client Office avec Microsoft 365 Business Premium
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
ms.date: 04/01/2022
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: M365-subscription-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: ed34fff3-2881-4ed4-9906-1ba6bb8dd804
description: Découvrez comment installer automatiquement les applications Office 32 bits sur les ordinateurs Windows et les maintenir à jour dans Microsoft 365 Business Premium.
ms.openlocfilehash: d4e9c16dea6697a428c5f7e51b7c8c1f819c75e4
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622047"
---
# <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>Préparer l'installation automatique d'applications Office sur des ordinateurs clients

Utilisez Microsoft 365 Business Premium pour iautomatiquement les applications Office 32 bits sur les ordinateurs Windows et les tenir à jour.
  
L’installation automatique fonctionne mieux si l’ordinateur : 

- est sur Windows for Business.
  
- n’a pas d’applications de bureau Office existantes (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access et OneDrive) OU une version existante d’Office « Démarrer en un clic » est installée.

Pour déterminer si vous possédez la version « Démarrer en un clic » d'Office, dans une application Office, accédez à **Fichier** \> **Compte** ( **Compte Office** dans Outlook). Si **Mises à jour pour Office** se présente comme dans la figure suivante, cela signifie que l'installation a été effectuée à l'aide de « Démarrer en un clic ».
  
![Capture d’écran des mises à jour d’Office dans le compte d’application Office.](./../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
## <a name="requirements-for-using-this-feature"></a>Configuration requise pour l’utilisation de cette fonctionnalité
  
Travaille avec :
  
- Un utilisateur disposant d’une licence d’utilisateur Windows Business, d’une licence active Microsoft 365 entreprise, de Windows 10 Creators Update et qui est joint à Azure Active Directory.

Ne fonctionne pas avec : 

- Applications Office 64 bits (exemple : Word, Excel, PowerPoint). Si des applications Office 64 bits sont requises, cette fonctionnalité n’est pas adaptée, car il n’existe aucune prise en charge pour déclencher une version 64 bits 2016 « Démarrer en un clic » d’Office à partir de la console d’administration Microsoft 365 pour les entreprises.

- Toutes les applications autonomes Windows Installer (MSI) 2016 (par exemple, Visio ou Project). Microsoft 365 pour les entreprises met à niveau Office vers la version Démarrer en un clic d’Office 2016, et cela ne fonctionne pas avec les applications autonomes Office 2016 MSI.

Le tableau suivant indique l’action que les utilisateurs finaux ou les administrateurs peuvent avoir à entreprendre, en fonction de leur état de début, pour obtenir une version 32 bits « Démarrer en un clic » réussie du déploiement d’Office à partir de la console d’administration Microsoft 365 pour les entreprises.<br/>


|Situation de départ à l'installation d'Office|Action à entreprendre avant Microsoft 365 pour l’installation d’Office pour les entreprises|État final|
|:-----|:-----|:-----|
|Aucune suite Office installée  |Aucune  |Office 2016 32 bits est installé à l’aide du mode Démarrer en un clic  |
|Version 32 bits « Démarrer en un clic » d'Office présente (2016 ou versions antérieures) et aucune application autonome  |Aucune  |Mise à niveau vers la dernière version 32 bits « Démarrer en un clic » d'Office 2016, le cas échéant **\*** |
|Version 32 bits « Démarrer en un clic » existante d’Office et « Démarrer en un clic » 32 bits ou 64 bits d’applications Office autonomes (par exemple, Visio, Project)  |Aucun  |Les applications autonomes ne sont pas affectées. La suite est mise à niveau vers la version 32 bits « Démarrer en un clic d’Office 2016  |
|Version 32 bits « Démarrer en un clic » d'Office présente et applications autonomes 32 ou 64 bits MSI (à l'exception de 2016) présentes  |Aucune  |Les applications autonomes ne sont pas affectées. La suite est mise à niveau vers la version 32 bits « Démarrer en un clic d’Office 2016  |
|Version 64 bits « Démarrer en un clic » d'Office présente  |Désinstallez les applications Office 64 bits, si vous pouvez les remplacer par des applications Office 32 bits  |Si les applications 64 bits d'Office sont supprimées, la version 32 bits « Démarrer en un clic » d'Office 2016 est installée  |
|Installation MSI d'Office 2016 existante, avec ou sans applications autonomes  |Désinstaller la version MSI d'Office 2016.  |La version 32 bits « Démarrer en un clic » d'Office 2016 est installée. Aucune modification apportée aux applications autonomes.  |
|Installation MSI d'Office 2013 (ou version antérieure) présente et/ou des applications Office autonomes présentes  |Aucune  |Coexistence de la version 32 bits « Démarrer en un clic » d'Office 2016 avec l'installation MSI d'Office préexistante (et les applications autonomes)  |

 **(\*) Remarque :** ne met pas à niveau vers la version 32 bits « Démarrer en un clic » d’Office 2016 en raison d’un bogue connu. Un correctif est en cours. 

## <a name="next-objective"></a>Objectif suivant

[Examiner et modifier les stratégies d’appareil](m365bp-view-edit-create-mdb-policies.md)
  