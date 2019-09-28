---
title: Se préparer pour le déploiement du client Office par Microsoft 365 Entreprise
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 10/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: M365-subscription-management
ms.custom: OKR_SMB_M365
search.appverid:
- BCS160
- MET150
ms.assetid: ed34fff3-2881-4ed4-9906-1ba6bb8dd804
description: Découvrez comment installer automatiquement les applications Office 32 bits sur les ordinateurs Windows 10 et les maintenir à jour.
ms.openlocfilehash: fe1f946e4a216050e533604afa7c6e74e7b5980f
ms.sourcegitcommit: 6003d6da0a85c97357eb3dba3918eb145f381fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "37288392"
---
# <a name="prepare-for-office-client-deployment-by-microsoft-365-business"></a>Se préparer pour le déploiement du client Office par Microsoft 365 Entreprise

## <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>Préparer l'installation automatique d'applications Office sur des ordinateurs clients

Vous pouvez utiliser Microsoft 365 Entreprise pour automatiquement installer et mettre à jour les applications Office 32 bits sur des ordinateurs Windows 10.
  
Il est préférable que l'ordinateur de l'utilisateur final fonctionne sous Windows 10 Business et :
  
- qu'aucune application de bureau Office (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access et OneDrive) ne soit installée.
    
    ou
    
- comprenne une version « Démarrer en un clic » d'Office.
    
Pour déterminer si vous possédez la version « Démarrer en un clic » d'Office, dans une application Office, accédez à **Fichier** \> **Compte** ( **Compte Office** dans Outlook). Si Mises à jour pour Office se présente comme dans la figure suivante, cela signifie que l'installation a été effectuée à l'aide de « Démarrer en un clic ». 
  
![Screenshot of Office updates in Office app Account](media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
 **Pour qui cette fonctionnalité est-elle utile ?**
  
L'utilisateur final dont le PC :
  
- **est associé** à une licence d'utilisateur Windows 10 Business activeMicrosoft 365 Entreprise, comprend Windows 10 Creators Update et est inscrit à Azure Active Directory ; 
    
- **ne comprend pas** les applications Office 64 bits (par exemple, Word, Excel, Powerpoint). Si les applications Office 64 bits sont requises, cette fonctionnalité n'est pas adaptée, car il n'est alors pas possible de déclencher une version « Démarrer en un clic » 64 bits d'Office 2016 à partir de la console d'administration Microsoft 365 Entreprise ; 
    
- **ne comprend** aucune application autonome Windows Installer 2016 (MSI) (par exemple Visio ou Project). Microsoft 365 Entreprise met à niveau Office vers la version « Démarrer en un clic » d'Office 2016 et cela ne fonctionne pas avec les applications autonomes Office 2016 MSI. 
    
Le tableau suivant décrit en détail les mesures que les utilisateurs finaux/administrateurs doivent éventuellement prendre, en fonction de leur situation de départ, pour pouvoir déployer la version 32 bits « Démarrer en un clic » d'Office à partir de la console d'administration Microsoft 365 Entreprise.
  
|**Situation de départ à l'installation d'Office**|**Mesure à prendre avant d'installer Office Microsoft 365 Entreprise**|**État final**|
|:-----|:-----|:-----|
|Aucune suite Office installée  <br/> |Aucun  <br/> |Office 2016 32 bits installé à l'aide de la technologie « Démarrer en un clic »  <br/> |
|Version 32 bits « Démarrer en un clic » d'Office présente (2016 ou versions antérieures) et aucune application autonome  <br/> |Aucun  <br/> |Mise à niveau vers la dernière version 32 bits « Démarrer en un clic » d'Office 2016, le cas échéant **\*** <br/> |
|Version 32 bits « Démarrer en un clic » d'Office présente et applications autonomes 32 ou 64 bits « Démarrer en un clic » d'Office (par exemple Visio, Project) présentes  <br/> |Aucun  <br/> |Les applications autonomes ne sont pas concernées. Mise à niveau de la suite vers la version 32 bits « Démarrer en un clic » d'Office 2016  <br/> |
|Version 32 bits « Démarrer en un clic » d'Office présente et applications autonomes 32 ou 64 bits MSI (à l'exception de 2016) présentes  <br/> |Aucun  <br/> |Les applications autonomes ne sont pas concernées. Mise à niveau de la suite vers la version 32 bits « Démarrer en un clic » d'Office 2016  <br/> ||||
|Version 64 bits « Démarrer en un clic » d'Office présente  <br/> |Désinstaller les applications 64 bits d'Office, si leur remplacement par les applications 32 bits d'Office ne pose aucun problème.  <br/> |Si les applications 64 bits d'Office sont supprimées, la version 32 bits « Démarrer en un clic » d'Office 2016 est installée  <br/> |
|Installation MSI d'Office 2016 existante, avec ou sans applications autonomes  <br/> |Désinstaller la version MSI d'Office 2016.  <br/> |La version 32 bits « Démarrer en un clic » d'Office 2016 est installée. Aucune modification apportée aux applications autonomes.  <br/> |
|Installation MSI d'Office 2013 (ou version antérieure) présente et/ou des applications Office autonomes présentes  <br/> |Aucune  <br/> |Coexistence de la version 32 bits « Démarrer en un clic » d'Office 2016 avec l'installation MSI d'Office préexistante (et les applications autonomes)  <br/> |
||||
   
 **(\*) Remarque :** pas de mise à niveau vers la version 32 bits « Démarrer en un clic » d'Office 2016 en raison d'un bogue répertorié. La correction est en cours. 
  


