---
title: Valider les paramètres de protection des applications sur les PC Windows 10
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
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
description: Découvrez comment vérifier que les paramètres de protection des applications Microsoft 365 pour les entreprises ont pris effet sur les appareils Windows 10 de vos utilisateurs.
ms.openlocfilehash: 39aee3bc811cb0090d58f9a282de7a8162c097b3
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44403587"
---
# <a name="validate-device-protection-settings-on-windows-10-pcs"></a>Valider les paramètres de protection des appareils sur des PC Windows 10

## <a name="verify-that-windows-10-device-policies-are-set"></a>Vérifier que les stratégies d’appareil Windows 10 sont définies

Une fois que vous avez [configuré les stratégies de périphériques](protection-settings-for-windows-10-pcs.md), la stratégie peut prendre plusieurs heures et prendre effet sur les appareils des utilisateurs. Vous pouvez vérifier que les stratégies ont pris effet en consultant les différents écrans de paramètres Windows sur les appareils des utilisateurs. Étant donné que les utilisateurs ne pourront pas modifier les paramètres de l’antivirus Windows Update et Windows Defender sur leurs appareils Windows 10, de nombreuses options seront grisées.
  
1. Accédez aux **paramètres** \> **mettre &amp; à jour** \> **Windows Update** \> les **options de redémarrage** de la sécurité Windows Update et vérifiez que tous les paramètres sont grisés. 
    
    ![Toutes les options de redémarrage sont grisées.](../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Accédez à **paramètres** \> **mettre &amp; à jour** \> **Windows Update** \> les **Options avancées** de sécurité Windows Update et vérifiez que tous les paramètres sont grisés. 
    
    ![Les options de mises à jour avancées de Windows sont toutes grisées.](../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Accéder aux **paramètres** \> **mettre à jour la &amp; sécurité** \> **Windows Update** \> **Advanced options** \> **sélectionnez le mode de remise des mises à jour**.
    
    Vérifiez que vous pouvez voir le message (en rouge) que certains paramètres sont masqués ou gérés par votre organisation, et que toutes les options sont grisées.
    
    ![Page choisir le mode de remise des mises à jour : indique que les paramètres sont masqués ou gérés par votre organisation.](../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Pour ouvrir le centre de sécurité Windows Defender, accédez à **paramètres** \> **mise à jour &amp; sécurité** \> **Windows Defender** \> cliquez sur Ouvrir les paramètres de **Open Windows Defender Security Center** \> ** &amp; ** \> ** &amp; protection contre les menaces**de virus de protection antivirus Windows Defender. 
    
5. Vérifiez que toutes les options sont grisées. 
    
    ![Les paramètres de protection contre les virus et les menaces sont grisés.](../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-topics"></a>Voir aussi

[Documentation et ressources de Microsoft 365 pour les entreprises](https://go.microsoft.com/fwlink/p/?linkid=853701)
  
[Prise en main de Microsoft 365 pour les entreprises](microsoft-365-business-overview.md)
  
[Gérer Microsoft 365 pour les entreprises](manage.md)
  
[Définir des configurations d'application pour les PC Windows 10](protection-settings-for-windows-10-pcs.md)
  

