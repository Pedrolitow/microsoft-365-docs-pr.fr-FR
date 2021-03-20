---
title: Fichier CSV de liste d’appareils
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- MSB365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 932e3676-2491-49f0-9177-d893d2f5276e
ROBOTS: NOINDEX
description: Découvrez comment faire un fichier CSV pour AutoPilot dans Microsoft 365 pour les entreprises.
ms.openlocfilehash: 78a9012bac054329bdb87b02757f49f30dd44f65
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50914737"
---
# <a name="device-list-csv-file"></a>Fichier CSV de liste d’appareils

## <a name="device-list-csv-file-format"></a>Format de fichier .csv de liste d’appareils

Pour gérer et déployer des appareils via Windows Autopilot, vous aurez besoin d’un fichier .csv qui contient des informations spécifiques sur les appareils.
  
Les colonnes du fichier de liste d’appareils doivent avoir les en-têtes suivants dans l’ordre spécifié :
  
- Colonne A : Numéro de série de l'appareil

- Colonne B : laisser vide

- Colonne C : Hachage du matériel

Vous pouvez obtenir ces informations à partir de votre fournisseur de matériel ou vous pouvez utiliser le [script Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) qui génèrera un fichier CSV. 

Lorsque vous ajoutez des appareils, vous devez également les ajouter à un profil. Un profil est utilisé pour appliquer des profils AutoPilot Deployment à un appareil ou à un groupe d’appareils.
  
## <a name="related-articles"></a>Articles connexes

[Documentation et ressources microsoft 365 pour les entreprises](../../business/index.yml)
  
[Mise en place de Microsoft 365 pour les entreprises](../../business/microsoft-365-business-overview.md)
  
[Gérer Microsoft 365 pour les entreprises](../../business/manage.md)
