---
title: Fichier CSV de liste d’appareils
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
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
description: Découvrez comment créer un fichier CSV pour AutoPilot dans Microsoft 365 pour les entreprises.
ms.openlocfilehash: 755f13358efd4da00235f3fb8f69912b433c92ff
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68735460"
---
# <a name="windows-autopilot-device-list-csv-file"></a>Fichier CSV de liste d’appareils Windows Autopilot

## <a name="device-list-csv-file-format"></a>Format de fichier .csv liste d’appareils

Pour gérer et déployer des appareils via Windows Autopilot, vous avez besoin d’un fichier .csv qui contient des informations spécifiques sur les appareils.
  
Les colonnes du fichier de liste d’appareils doivent avoir les en-têtes suivants dans l’ordre spécifié :
  
- Colonne A : Numéro de série de l'appareil

- Colonne B : laissez vide

- Colonne C : Hachage du matériel

Vous pouvez obtenir ces informations à partir de votre fournisseur de matériel ou vous pouvez utiliser le [script Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) qui génèrera un fichier CSV. 

Lorsque vous ajoutez des appareils, vous devez également les ajouter à un profil. Un profil est utilisé pour appliquer des profils de déploiement AutoPilot à un appareil ou à un groupe d’appareils.
  
## <a name="related-content"></a>Contenu associé

[Documentation et ressources Microsoft 365 pour les entreprises](../../index.yml)
  
[Bien démarrer avec Microsoft 365 pour les entreprises](../../admin/admin-overview/what-is-microsoft-365.md)