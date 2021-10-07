---
title: Fichier CSV de liste d’appareils
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Découvrez comment faire un fichier CSV pour AutoPilot dans Microsoft 365 entreprise.
ms.openlocfilehash: de29df41f60a1cf257291942eda70a776466c09c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60180435"
---
# <a name="device-list-csv-file"></a>Fichier CSV de liste d’appareils

## <a name="device-list-csv-file-format"></a>Format de fichier .csv liste des appareils

Pour gérer et déployer des appareils via Windows Autopilot, vous aurez besoin d’un fichier .csv contenant des informations spécifiques sur les appareils.
  
Les colonnes du fichier de liste d’appareils doivent avoir les en-têtes suivants dans l’ordre spécifié :
  
- Colonne A : Numéro de série de l'appareil

- Colonne B : laisser vide

- Colonne C : Hachage du matériel

Vous pouvez obtenir ces informations à partir de votre fournisseur de matériel ou vous pouvez utiliser le [script Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) qui génèrera un fichier CSV. 

Lorsque vous ajoutez des appareils, vous devez également les ajouter à un profil. Un profil est utilisé pour appliquer des profils AutoPilot Deployment à un appareil ou à un groupe d’appareils.
  
## <a name="related-content"></a>Contenu associé

[Microsoft 365 documentation et ressources pour les entreprises](../../index.yml)
  
[Mise en place Microsoft 365 entreprise](../../business-video/what-is-microsoft-365.md)