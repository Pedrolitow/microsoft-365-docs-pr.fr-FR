---
title: Préparer le déploiement Office client par Microsoft 365 entreprise
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
ms.date: 10/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
description: Découvrez comment installer automatiquement les applications Office 32 bits sur Windows 10 ordinateurs et les maintenir à jour.
ms.openlocfilehash: ea131e37fa7f82a0ab03aa52b71569e3c96a2c7f
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58566107"
---
# <a name="prepare-for-office-client-deployment-by-microsoft-365-for-business"></a>Préparer le déploiement Office client par Microsoft 365 entreprise

Cet article s’applique aux Microsoft 365 Business Premium.

## <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>Préparer l'installation automatique d'applications Office sur des ordinateurs clients

Vous pouvez utiliser Microsoft 365 Business Premium pour installer automatiquement les applications Office 32 bits sur Windows 10 ordinateurs et les tenir informés des mises à jour.
  
L’installation automatique fonctionne mieux si l’ordinateur de l’utilisateur final est Windows 10 Business et :
  
- qu'aucune application de bureau Office (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access et OneDrive) ne soit installée.
    
    ou
    
- comprenne une version « Démarrer en un clic » d'Office.
    
Pour déterminer si vous possédez la version « Démarrer en un clic » d'Office, dans une application Office, accédez à **Fichier** \> **Compte** ( **Compte Office** dans Outlook). Si vous voyez **Office mises à** jour comme illustré dans la figure suivante, l’installation s’est effectuée à l’aide de Click-to-Run. 
  
![Capture d’écran Office mises à jour de application Office compte.](../../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
 **Qui avantages de cette fonctionnalité**
  
L'utilisateur final dont le PC :
  
- **Possède** une licence Windows 10 Business utilisateur, une licence Microsoft 365 entreprise active, Windows 10 Creators Update et est jointe à Azure Active Directory. 
    
- **N’a pas d’applications** Office 64 bits (par exemple, Word, Excel, PowerPoint). Si des applications Office 64 bits sont requises, cette fonctionnalité n’est pas adaptée, car il n’existe aucune prise en charge du déclenchement d’une version « 64 bits 2016 en un clic » de Office à partir de la console d’administration Microsoft 365 pour les entreprises. 
    
- **ne comprend** aucune application autonome Windows Installer 2016 (MSI) (par exemple Visio ou Project). Microsoft 365 mises à niveau pour les entreprises Office vers la version « En un clic » de Office 2016 et qui ne fonctionne pas avec les applications autonomes MSI Office 2016. 
    
Le tableau suivant indique l’action que les utilisateurs finaux/administrateurs peuvent avoir besoin d’exécuter, en fonction de leur état de départ, pour obtenir une version 32 bits réussie du déploiement « En un clic » de Office à partir de la console d’administration Microsoft 365 pour les entreprises.<br/>


|Situation de départ à l'installation d'Office|Action à prendre avant Microsoft 365'installation Office entreprise|État final|
|:-----|:-----|:-----|
|Aucune suite Office installée  <br/> |Aucune  <br/> |Office 2016 32 bits est installé à l’aide de Click-to-Run  <br/> |
|Version 32 bits « Démarrer en un clic » d'Office présente (2016 ou versions antérieures) et aucune application autonome  <br/> |Aucune  <br/> |Mise à niveau vers la dernière version 32 bits « Démarrer en un clic » d'Office 2016, le cas échéant **\*** <br/> |
|Version 32 bits « Click-to-Run » existante de Office et applications Office autonomes 32 bits ou 64 bits « Click-to-Run » (par exemple, Visio, Project)  <br/> |Aucune  <br/> |Les applications autonomes ne sont pas affectées. Mise à niveau de la suite vers la version 32 bits « Démarrer en un clic » d'Office 2016  <br/> |
|Version 32 bits « Démarrer en un clic » d'Office présente et applications autonomes 32 ou 64 bits MSI (à l'exception de 2016) présentes  <br/> |Aucune  <br/> |Les applications autonomes ne sont pas affectées. Mise à niveau de la suite vers la version 32 bits « Démarrer en un clic » d'Office 2016  <br/> |
|Version 64 bits « Démarrer en un clic » d'Office présente  <br/> |Désinstallez les applications Office 64 bits, s’il est acceptable de les remplacer par des applications Office 32 bits  <br/> |Si les applications 64 bits d'Office sont supprimées, la version 32 bits « Démarrer en un clic » d'Office 2016 est installée  <br/> |
|Installation MSI d'Office 2016 existante, avec ou sans applications autonomes  <br/> |Désinstaller la version MSI d'Office 2016.  <br/> |La version 32 bits « Démarrer en un clic » d'Office 2016 est installée. Aucune modification apportée aux applications autonomes.  <br/> |
|Installation MSI d'Office 2013 (ou version antérieure) présente et/ou des applications Office autonomes présentes  <br/> |Aucune  <br/> |Coexistence de la version 32 bits « Démarrer en un clic » d'Office 2016 avec l'installation MSI d'Office préexistante (et les applications autonomes)  <br/> |
||||
   
 **(\*) Remarque :** pas de mise à niveau vers la version 32 bits « Démarrer en un clic » d'Office 2016 en raison d'un bogue répertorié. Un correctif est en cours. 
  
