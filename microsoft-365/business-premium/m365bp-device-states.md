---
title: États des appareils
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: c3ac23c5-d4b4-4b1b-b7ce-ea759521bf8c
description: Découvrez les différents états de l’appareil dans la liste des actions de l’appareil dans la page d’accueil de l’administrateur dans Microsoft 365 pour les entreprises.
ms.openlocfilehash: 00a2b86265c342d131c703b207682e2eeff26b79
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320799"
---
# <a name="device-states"></a>États des appareils

Cet article s’applique à Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender pour les PME est déployée pour les clients Microsoft 365 Business Premium, à compter du 1er mars 2022. Cette offre fournit des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender for Business](../security/defender-business/mdb-overview.md).

Les appareils de la liste **Actions de l'appareil** (accueil Administrateur \> **Actions de l'appareil**) peuvent présenter les états suivants.
  
![In the Device actions list, you can see the Devices states.](./../media/a621c47e-45d9-4e1a-beb9-c03254d40c1d.png)
  
|**État**|**Description**|
|:-----|:-----|
|Géré par Intune  |Géré par Microsoft 365 Business Premium.  |
|Mise hors service en attente  |Microsoft 365 Entreprise s'apprête à supprimer des données d'entreprise de l'appareil.  |
|Mise hors service en cours  |Microsoft 365 Entreprise est en train de supprimer des données d'entreprise de l'appareil.  |
|Échec de la mise hors service  | L'action de suppression des données d'entreprise a échoué.  |
|Mise hors service annulée  |L'action de mise hors service a été annulée.  |
|Réinitialisation en attente  |En attente du rétablissement des paramètres d'usine.  |
|Réinitialisation en cours  |Le rétablissement des paramètres d'usine a démarré.  |
|Échec de la réinitialisation  |Le rétablissement des paramètres d'usine n'a pas pu être effectué.  |
|Réinitialiser annulée  |Le rétablissement des paramètres d'usine a été annulé.  |
|Défectueux  |Cela signifie qu'une action est en attente (ou en cours) mais que l'appareil n'a pas archivé depuis plus de 30 jours.  |
|Suppression en attente  |Une action de suppression est en attente.  |
|Détecté  |Microsoft 365 Entreprise a détecté l'appareil.  |
   

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)