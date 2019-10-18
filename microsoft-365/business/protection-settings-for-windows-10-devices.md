---
title: Définir les paramètres de protection des applications pour les appareils Windows 10
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
f1_keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 02e74022-44af-414b-9d74-0ebf5c2197f0
description: Découvrez comment créer une stratégie de gestion des applications et protéger les fichiers de travail sur les appareils Windows 10.
ms.openlocfilehash: 0e1221e533418166b80afd94431414016774f247
ms.sourcegitcommit: bd52f7b662887f552f90c46f69d6a2a42fb66914
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "37575775"
---
# <a name="set-application-protection-settings-for-windows-10-devices"></a>Définir les paramètres de protection des applications pour les appareils Windows 10

## <a name="create-an-app-management-policy-for-windows-10"></a>Créer une stratégie de gestion des applications pour Windows 10

Si vos utilisateurs disposent d'appareils Windows 10 sur lesquels ils effectuent des tâches professionnelles, vous pouvez également protéger vos données sur ces appareils.
  
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
    
2. Dans le volet de navigation de gauche, choisissez **Ajout**de **stratégies** \> de **périphériques** \> .

3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie. 
    
4. Sous **Type de stratégie**, sélectionnez **Gestion des applications pour Windows 10**.
    
5. Sous **type d’appareil**, choisissez **personnel** ou **société appartenant**.
    
6. L'option **Chiffrer les fichiers de travail** est activée automatiquement. 
    
7. Définissez **Empêcher les utilisateurs de copier des données d'entreprise dans leurs fichiers personnels et les obliger à enregistrer les fichiers professionnels dans OneDrive Entreprise** sur **Activé** si vous ne souhaitez pas que les utilisateurs enregistrent des fichiers professionnels sur leur PC. 
    
9. Développez **Récupérer les données sur les appareils Windows**. Nous vous recommandons d' **activer** cette option.
    
    Avant de pouvoir accéder à l'emplacement du certificat de l'agent de récupération de données, vous devez d'abord créer un tel certificat. Pour obtenir des instructions, consultez [Créer et vérifier un certificat d'agent de récupération de données EFS (Encrypting File System)](https://go.microsoft.com/fwlink/p/?linkid=853700).
    
    Par défaut, les fichiers de travail sont chiffrés à l'aide d'une clé secrète qui est stockée sur l'appareil associé au profil de l'utilisateur. Seul l'utilisateur peut ouvrir et déchiffrer le fichier. Toutefois, si un périphérique est perdu ou si un utilisateur est supprimé, un fichier peut rester bloqué à l'état chiffré. Le certificat de l'Agent de récupération de données (DRA) peut être utilisé par un administrateur pour déchiffrer le fichier.
    
    ![Browse to Data Recovery Agent certificate.](media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
10. Développez **Protéger les emplacements réseau et cloud supplémentaires** pour ajouter des domaines supplémentaires ou des sites SharePoint Online afin d'assurer que les fichiers de toutes les applications répertoriées seront protégés. Si vous devez entrer plusieurs éléments pour chaque champ, utilisez un point-virgule ( ;) entre les différents éléments.
    
    ![Expand Protect additional network and cloud locations, and enter domains or SharePoint Online sites you own.](media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
11. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne voulez pas utiliser le groupe de sécurité par défaut **Tous les utilisateurs**, sélectionnez **Modifier**, puis les groupes de sécurité qui recevront ces paramètres \> **Sélectionner**.
    
12. Enfin, sélectionnez **Ajouter** pour enregistrer la stratégie et l'affecter à des appareils. 