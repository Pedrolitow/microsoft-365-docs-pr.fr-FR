---
title: Préparer le déploiement de clients Office par Microsoft 365 pour les entreprises
f1.keywords:
- CSH
ms.author: sirkkuw
author: Sirkkuw
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
ms.assetid: ed34fff3-2881-4ed4-9906-1ba6bb8dd804
description: Découvrez comment installer automatiquement les applications Office 32 bits sur les ordinateurs Windows 10 et les maintenir à jour.
ms.openlocfilehash: 2de492914edbde2afe593aac290c4a634b801443
ms.sourcegitcommit: 2d664a95b9875f0775f0da44aca73b16a816e1c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "44470944"
---
# <a name="prepare-for-office-client-deployment-by-microsoft-365-for-business"></a>Préparer le déploiement de clients Office par Microsoft 365 pour les entreprises

Cet article s’applique à Microsoft 365 Business Premium.

## <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>Préparer l'installation automatique d'applications Office sur des ordinateurs clients

Vous pouvez utiliser Microsoft 365 Business Premium pour installer automatiquement les applications Office 32 bits sur les ordinateurs Windows 10 et les garder à jour avec les mises à jour.
  
L’installation automatique fonctionne mieux si l’ordinateur de l’utilisateur final est sur Windows 10 entreprise et :
  
- qu'aucune application de bureau Office (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access et OneDrive) ne soit installée.
    
    ou
    
- comprenne une version « Démarrer en un clic » d'Office.
    
Pour déterminer si vous possédez la version « Démarrer en un clic » d'Office, dans une application Office, accédez à **Fichier** \> **Compte** ( **Compte Office** dans Outlook). Si vous voyez les **mises à jour d’Office** comme illustré dans la figure suivante, l’installation a été effectuée à l’aide d’Office « démarrer en un clic ». 
  
![Screenshot of Office updates in Office app Account](../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
 **Qui tire parti de cette fonctionnalité ?**
  
L'utilisateur final dont le PC :
  
- **Dispose** d’une licence utilisateur Windows 10 Business, d’une licence Microsoft 365 pour les entreprises active, de Windows 10 Creators Update et est jointe à Azure Active Directory. 
    
- **N’a pas** d’applications Office 64 bits (exemple : Word, Excel, PowerPoint). Si des applications Office 64 bits sont requises, cette fonctionnalité n’est pas adaptée, car il n’existe pas de prise en charge pour le déclenchement d’une version d’Office « démarrer en un clic » 64 2016 bits d’Office à partir de la console d’administration Microsoft 365 pour les entreprises. 
    
- **ne comprend** aucune application autonome Windows Installer 2016 (MSI) (par exemple Visio ou Project). Microsoft 365 for Business upgrades Office vers la version « démarrer en un clic » d’Office 2016 et qui ne fonctionne pas avec les applications autonomes MSI Office 2016. 
    
Le tableau suivant indique les actions que les utilisateurs/administrateurs finaux peuvent avoir à effectuer, en fonction de leur état de démarrage, pour obtenir une version de déploiement d’Office « démarrer en un clic » de 32 bits à partir de la console d’administration Microsoft 365 pour entreprises.
  
|**Situation de départ à l'installation d'Office**|**Action à effectuer avant l’installation de Microsoft 365 pour Office Business**|**État final**|
|:-----|:-----|:-----|
|Aucune suite Office installée  <br/> |Aucun  <br/> |Office 2016 32 bits est installé à l’aide d’Office « démarrer en un clic »  <br/> |
|Version 32 bits « Démarrer en un clic » d'Office présente (2016 ou versions antérieures) et aucune application autonome  <br/> |Aucun  <br/> |Mise à niveau vers la dernière version 32 bits « Démarrer en un clic » d'Office 2016, le cas échéant **\*** <br/> |
|Version d’Office « démarrer en un clic » d’Office « 32 démarrer en un clic » et « démarrer en un clic » 64 ou des applications Office « 32 démarrer en un clic » (par exemple, Visio, Project).  <br/> |Aucun  <br/> |Les applications autonomes ne sont pas affectées. Mise à niveau de la suite vers la version 32 bits « Démarrer en un clic » d'Office 2016  <br/> |
|Version 32 bits « Démarrer en un clic » d'Office présente et applications autonomes 32 ou 64 bits MSI (à l'exception de 2016) présentes  <br/> |Aucun  <br/> |Les applications autonomes ne sont pas affectées. Mise à niveau de la suite vers la version 32 bits « Démarrer en un clic » d'Office 2016  <br/> ||||
|Version 64 bits « Démarrer en un clic » d'Office présente  <br/> |Désinstaller les applications Office 64 bits, si vous voulez les remplacer par des applications Office 32 bits  <br/> |Si les applications 64 bits d'Office sont supprimées, la version 32 bits « Démarrer en un clic » d'Office 2016 est installée  <br/> |
|Installation MSI d'Office 2016 existante, avec ou sans applications autonomes  <br/> |Désinstaller la version MSI d'Office 2016.  <br/> |La version 32 bits « Démarrer en un clic » d'Office 2016 est installée. Aucune modification apportée aux applications autonomes.  <br/> |
|Installation MSI d'Office 2013 (ou version antérieure) présente et/ou des applications Office autonomes présentes  <br/> |Aucune  <br/> |Coexistence de la version 32 bits « Démarrer en un clic » d'Office 2016 avec l'installation MSI d'Office préexistante (et les applications autonomes)  <br/> |
||||
   
 **(\*) Remarque :** pas de mise à niveau vers la version 32 bits « Démarrer en un clic » d'Office 2016 en raison d'un bogue répertorié. Un correctif est en cours. 
  
