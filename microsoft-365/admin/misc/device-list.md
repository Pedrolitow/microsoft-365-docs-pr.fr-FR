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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 932e3676-2491-49f0-9177-d893d2f5276e
ROBOTS: NOINDEX
description: Découvrez comment créer un fichier CSV pour AutoPilot dans Microsoft 365 pour les entreprises.
ms.openlocfilehash: c83862675db1372aa2cef27c727c04577b4cf5a3
ms.sourcegitcommit: 7f307b4f583b602f11f69adae46d7f3bf6982c65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44064650"
---
# <a name="device-list-csv-file"></a>Fichier CSV de liste d’appareils

## <a name="device-list-csv-file-format"></a>Format de fichier. csv de liste d’appareils

Pour gérer et déployer des appareils via Windows AutoPilot, vous aurez besoin d’un fichier. csv contenant des informations spécifiques sur les appareils.
  
Les colonnes du fichier de liste d’appareils doivent avoir les en-têtes suivants dans l’ordre spécifié :
  
- Colonne A : Numéro de série de l'appareil

- Colonne B : laisser vide

- Colonne C : Hachage du matériel

Vous pouvez obtenir ces informations à partir de votre fournisseur de matériel ou vous pouvez utiliser le [script Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) qui génèrera un fichier CSV. 

Lorsque vous ajoutez des appareils, vous devez également les ajouter à un profil. Un profil est utilisé pour appliquer des profils de déploiement AutoPilot à un appareil ou à un groupe d’appareils.
  
## <a name="related-articles"></a>Articles connexes

[Documentation et ressources de Microsoft 365 pour les entreprises](https://go.microsoft.com/fwlink/p/?linkid=853701)
  
[Prise en main de Microsoft 365 pour les entreprises](https://docs.microsoft.com/microsoft-365/business/microsoft-365-business-overview)
  
[Gérer Microsoft 365 pour les entreprises](https://docs.microsoft.com/microsoft-365/business/manage)
  
