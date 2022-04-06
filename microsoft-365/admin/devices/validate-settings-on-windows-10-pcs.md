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
ms.openlocfilehash: 47c220b36050376d1eddf7d83435f175e00f88cb
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64633280"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Valider les paramètres de protection des appareils pour Windows 10 PC

> [!NOTE]
> Microsoft Defender pour les PME est en Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Cette offre offre des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender pour les entreprises](../../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>Vérifier que les Windows 10 d’appareil sont définies

Après avoir [installé les stratégies d’appareil](../../business-premium/m365bp-protection-settings-for-windows-10-pcs.md), l’application de la stratégie sur les appareils des utilisateurs peut prendre jusqu’à quelques heures. Vous pouvez confirmer que les stratégies ont pris effet en regardant différents écrans Windows Paramètres sur les appareils des utilisateurs. Étant donné que les utilisateurs ne pourront pas modifier les paramètres Windows Update et Antivirus Microsoft Defender sur leurs appareils Windows 10, de nombreuses options seront grisées.
  
1. Go to **Paramètres** \> **Update &amp; security** \> **Windows Update** \> **Restart options** and confirm that all settings are grayed out. 
    
    ![Toutes les options de redémarrage sont grisées.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Go to **Paramètres** \> **Update &amp; security** \> **Windows Update** \> **Advanced options** and confirm that all settings are grayed out. 
    
    ![Windows options de mises à jour avancées sont toutes grisées.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Go to **Paramètres** \> **Update &amp; security** \> **Windows Update** \> **Advanced options** \> **Choose how updates are delivered**.
    
    Confirmez que vous pouvez voir le message (en rouge) que certains paramètres sont masqués ou gérés par votre organisation, et que toutes les options sont grisées.
    
    ![Choisissez la manière dont les mises à jour sont remis page indique que les paramètres sont masqués ou gérés par votre organisation.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Pour ouvrir le Centre de sécurité Windows Defender,  \> **&amp;** \> consultez la Paramètres de sécurité mise à jour **Windows Defender** \> cliquez sur Paramètres de **protection contre les virus du centre de sécurité Open Windows Defender Security Center &amp;**  \> \> **&amp;**. 
    
5. Vérifiez que toutes les options sont grisées. 
    
    ![Les paramètres de protection contre les virus et les menaces sont grisés.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Contenu connexe

[Microsoft 365 documentation et ressources pour les entreprises](/admin)

[Définir des configurations d’appareil Windows 10 10 méthodes PCsTop](../../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
 [pour sécuriser les Microsoft 365 pour les entreprises](../../admin/security-and-compliance/secure-your-business-data.md)
