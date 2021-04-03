---
title: Préparer le déploiement du client Office par Microsoft 365 pour les entreprises
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
ms.assetid: ed34fff3-2881-4ed4-9906-1ba6bb8dd804
description: Découvrez comment installer automatiquement les applications Office 32 bits sur les ordinateurs Windows 10 et les maintenir à jour.
ms.openlocfilehash: 868d06fadfef0f55b41131b7fdfbb368b9128405
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51580051"
---
# <a name="prepare-for-office-client-deployment-by-microsoft-365-for-business"></a>Préparer le déploiement du client Office par Microsoft 365 pour les entreprises

Cet article s’applique à Microsoft 365 Business Premium.

## <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>Préparer l'installation automatique d'applications Office sur des ordinateurs clients

Vous pouvez utiliser Microsoft 365 Business Premium pour installer automatiquement les applications Office 32 bits sur les ordinateurs Windows 10 et les tenir informés des mises à jour.
  
L’installation automatique fonctionne mieux si l’ordinateur de l’utilisateur final est sur Windows 10 Entreprise et :
  
- qu'aucune application de bureau Office (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access et OneDrive) ne soit installée.
    
    ou
    
- comprenne une version « Démarrer en un clic » d'Office.
    
Pour déterminer si vous possédez la version « Démarrer en un clic » d'Office, dans une application Office, accédez à **Fichier** \> **Compte** ( **Compte Office** dans Outlook). Si vous voyez **les mises à** jour Office comme indiqué dans la figure suivante, l’installation a été effectuée à l’aide de « Click-to-Run ». 
  
![Screenshot of Office updates in Office app Account](../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
 **Avantages de cette fonctionnalité**
  
L'utilisateur final dont le PC :
  
- **Dispose**  d’une licence utilisateur Windows 10 Business, d’une licence Microsoft 365 entreprise active, de Windows 10 Creators Update et est joint à Azure Active Directory. 
    
- **N’a pas d’applications** Office 64 bits (par exemple : Word, Excel, PowerPoint). Si des applications Office 64 bits sont requises, cette fonctionnalité ne convient pas, car il n’existe aucune prise en charge du déclenchement d’une version 64 bits 2016 d’Office « En un clic » d’Office à partir de la console d’administration Microsoft 365 pour les entreprises. 
    
- **ne comprend** aucune application autonome Windows Installer 2016 (MSI) (par exemple Visio ou Project). Microsoft 365 for business upgrades Office to the Click-to-Run version of Office 2016 and that doesn’t work with Office 2016 MSI standalone apps. 
    
Le tableau suivant indique l’action que les utilisateurs finaux/administrateurs peuvent avoir besoin d’exécuter, en fonction de leur état de départ, pour obtenir une version 32 bits réussie du déploiement Office « En un clic » d’Office à partir de la console d’administration Microsoft 365 pour les entreprises.
  
|**Situation de départ à l'installation d'Office**|**Action à prendre avant l’installation d’Office Microsoft 365 pour les entreprises**|**État final**|
|:-----|:-----|:-----|
|Aucune suite Office installée  <br/> |Aucune  <br/> |Office 2016 32 bits est installé en un clic  <br/> |
|Version 32 bits « Démarrer en un clic » d'Office présente (2016 ou versions antérieures) et aucune application autonome  <br/> |Aucune  <br/> |Mise à niveau vers la dernière version 32 bits « Démarrer en un clic » d'Office 2016, le cas échéant **\*** <br/> |
|Version 32 bits « Exécuter en un clic » d’Office existante et applications Office autonomes « Exécuter en un clic » 32 bits ou 64 bits (par exemple, Visio, Project)  <br/> |Aucun  <br/> |Les applications autonomes ne sont pas affectées. Mise à niveau de la suite vers la version 32 bits « Démarrer en un clic » d'Office 2016  <br/> |
|Version 32 bits « Démarrer en un clic » d'Office présente et applications autonomes 32 ou 64 bits MSI (à l'exception de 2016) présentes  <br/> |Aucune  <br/> |Les applications autonomes ne sont pas affectées. Mise à niveau de la suite vers la version 32 bits « Démarrer en un clic » d'Office 2016  <br/> ||||
|Version 64 bits « Démarrer en un clic » d'Office présente  <br/> |Désinstallez les applications Office 64 bits, s’il est acceptable de les remplacer par des applications Office 32 bits  <br/> |Si les applications 64 bits d'Office sont supprimées, la version 32 bits « Démarrer en un clic » d'Office 2016 est installée  <br/> |
|Installation MSI d'Office 2016 existante, avec ou sans applications autonomes  <br/> |Désinstaller la version MSI d'Office 2016.  <br/> |La version 32 bits « Démarrer en un clic » d'Office 2016 est installée. Aucune modification apportée aux applications autonomes.  <br/> |
|Installation MSI d'Office 2013 (ou version antérieure) présente et/ou des applications Office autonomes présentes  <br/> |Aucune  <br/> |Coexistence de la version 32 bits « Démarrer en un clic » d'Office 2016 avec l'installation MSI d'Office préexistante (et les applications autonomes)  <br/> |
||||
   
 **(\*) Remarque :** pas de mise à niveau vers la version 32 bits « Démarrer en un clic » d'Office 2016 en raison d'un bogue répertorié. Un correctif est en cours. 
  
