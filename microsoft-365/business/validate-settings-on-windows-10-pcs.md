---
title: Valider les paramètres de protection des applications sur les PC Windows 10
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Adm_O365
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: fae8819d-7235-495f-9f07-d016f545887f
description: Découvrez comment valider les paramètres de protection Microsoft 365 Business application pour les appareils Windows 10.
ms.openlocfilehash: db05c86bd75cc30e22e025034a3dab478d0f5365
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867006"
---
# <a name="validate-device-protection-settings-on-windows-10-pcs"></a>Valider les paramètres de protection de périphériques sur Windows 10 PC

## <a name="verify-that-windows-10-device-policies-are-set"></a>Vérifiez que les stratégies d’appareil Windows 10 sont définies

Après vous [configurez des stratégies de périphériques](protection-settings-for-windows-10-pcs.md), elle peut prendre quelques heures pour la stratégie prennent effet sur les périphériques des utilisateurs. Vous pouvez vérifier que les stratégies en vigueur en examinant les écrans différents paramètres Windows sur les périphériques de l’utilisateur. Étant donné que les utilisateurs ne seront pas en mesure de modifier les paramètres de mise à jour de Windows et Windows Defender Antivirus sur leurs appareils Windows 10, un grand nombre de ces options est grisé.
  
1. Accédez à **paramètres** \> **mise à jour &amp; sécurité** \> **Mise à jour Windows** \> **les options de redémarrage** et vérifiez que tous les paramètres sont estompées. 
    
    ![Toutes les options de redémarrage sont estompées.](media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Accédez à **paramètres** \> **mise à jour &amp; sécurité** \> **Mise à jour Windows** \> **options avancées** et vérifiez que tous les paramètres sont estompées. 
    
    ![Options avancées de Windows de mises à jour sont toutes estompées.](media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Accédez à **paramètres** \> **mise à jour &amp; sécurité** \> **Mise à jour Windows** \> **options avancées** \> **Choisir comment les mises à jour sont remis**.
    
    Vérifiez que vous pouvez voir le message (en rouge) certains paramètres sont masqués ou gérés par votre organisation, et toutes les options sont estompées.
    
    ![Choisir la façon dont les mises à jour sont remis page indique les paramètres sont masqués ou gérés par votre organisation.](media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Pour ouvrir le centre de sécurité Windows Defender, accédez à **paramètres** \> **mise à jour &amp; sécurité** \> **Windows Defender** \> cliquez sur **Ouvrir le centre de sécurité Windows Defender** \> **Virus &amp; thread protection** \> **Virus &amp; paramètres de protection contre les menaces**. 
    
5. Vérifiez que toutes les options sont estompées. 
    
    ![Les paramètres de protection contre les Virus et les menaces sont estompées.](media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-topics"></a>Rubriques connexes

[Documentation et ressources pour Microsoft 365 Business](https://go.microsoft.com/fwlink/p/?linkid=853701)
  
[Prise en main de Microsoft 365 Business](microsoft-365-business-overview.md)
  
[Gérer Microsoft 365 Business](manage.md)
  
[Définir des configurations d'application pour les PC Windows 10](protection-settings-for-windows-10-pcs.md)
  

