---
title: Valider les paramètres de protection des applications pour Windows 10 PC
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: fae8819d-7235-495f-9f07-d016f545887f
description: Découvrez comment vérifier que les paramètres Microsoft 365 protection des applications pour les entreprises ont pris effet sur les appareils Windows 10 utilisateurs.
ms.openlocfilehash: 311da3efec8cd3ad57e722aea5a8c3888d1af7b0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60165327"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Valider les paramètres de protection des appareils Windows 10 PC

## <a name="verify-that-windows-10-device-policies-are-set"></a>Vérifier que les Windows 10 d’appareil sont définies

Une fois [les stratégies d’appareils](protection-settings-for-windows-10-pcs.md)définies, l’application de la stratégie sur les appareils des utilisateurs peut prendre jusqu’à quelques heures. Vous pouvez vérifier que les stratégies ont pris effet en regardant différents écrans Windows Paramètres sur les appareils des utilisateurs. Étant donné que les utilisateurs ne pourront pas modifier les paramètres Windows Update et Antivirus Windows Defender sur leurs appareils Windows 10, de nombreuses options seront grisées.
  
1. Go to **Paramètres** \> **Update &amp; security** \> **Windows Update** Restart \> **options** and confirm that all settings are grayed out. 
    
    ![Toutes les options de redémarrage sont grisées.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Go to **Paramètres** \> **Update &amp; security** \> **Windows Update** Advanced \> **options** and confirm that all settings are grayed out. 
    
    ![Windows Les options de mises à jour avancées sont toutes grisées.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Go to **Paramètres** \> **Update &amp; security** \> **Windows Update** Advanced \> **options** Choose how \> **updates are delivered**.
    
    Confirmez que vous pouvez voir le message (en rouge) que certains paramètres sont masqués ou gérés par votre organisation, et que toutes les options sont grisées.
    
    ![Choisissez la manière dont les mises à jour sont remis page indique que les paramètres sont masqués ou gérés par votre organisation.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Pour ouvrir le Centre de sécurité  Windows Defender, consultez la Paramètres de sécurité mise à jour Windows Defender cliquez sur Ouvrir Windows Defender Paramètres de protection antivirus contre les \> **&amp;** \>  \>  \> **&amp;** \> **menaces du &amp; centre de sécurité**. 
    
5. Vérifiez que toutes les options sont grisées. 
    
    ![Les paramètres de protection contre les virus et les menaces sont grisés.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Contenu associé

[Microsoft 365 documentation et ressources pour les entreprises](/admin)\
[Définir des configurations d'application pour les PC Windows 10](protection-settings-for-windows-10-pcs.md)
