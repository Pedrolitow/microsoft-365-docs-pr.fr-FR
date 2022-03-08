---
title: Modifier ou définir les paramètres de protection des applications pour Windows 10 appareils
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
f1.keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 02e74022-44af-414b-9d74-0ebf5c2197f0
description: Découvrez comment créer ou modifier des stratégies de gestion des applications et protéger les fichiers de travail sur les appareils personnels Windows 10 utilisateurs.
ms.openlocfilehash: 3a565586be4d0dfec308b2dad3b068e01774b161
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313788"
---
# <a name="set-or-edit-application-protection-settings-for-windows-10-devices"></a>Définir ou modifier les paramètres de protection des applications pour Windows 10 appareils

Cet article s’applique aux Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender for Business est en déploiement Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Cette offre offre des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender pour les entreprises](../../security/defender-business/mdb-overview.md).

## <a name="edit-an-app-management-policy-for-windows-10"></a>Modifier une stratégie de gestion des applications pour Windows 10

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     
2. Dans le navigation de gauche, sélectionnez **Stratégies d’appareils**\>.
1. Choisissez une stratégie d’Windows existante, puis **modifiez**.
1. Choose **Edit** next to a setting you want to change and then **Save**.

## <a name="create-an-app-management-policy-for-windows-10"></a>Créer une stratégie de gestion des applications pour Windows 10

Si vos utilisateurs disposent d'appareils Windows 10 sur lesquels ils effectuent des tâches professionnelles, vous pouvez également protéger vos données sur ces appareils.
  
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
2. Dans le navigation de gauche, choisissez **Ajouter des** **stratégies**\> **d’appareils**\>.
3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie. 
4. Sous **Type de stratégie**, sélectionnez **Gestion des applications pour Windows 10**.
5. Sous **Type d’appareil**, choisissez **Personnel** ou **Entreprise**.
6. L'option **Chiffrer les fichiers de travail** est activée automatiquement. 
7. Définissez **Empêcher les utilisateurs de copier des données d'entreprise dans leurs fichiers personnels et les obliger à enregistrer les fichiers professionnels dans OneDrive Entreprise** sur **Activé** si vous ne souhaitez pas que les utilisateurs enregistrent des fichiers professionnels sur leur PC. 
9. **Développez récupérer des données sur Windows périphériques.** Nous vous recommandons de **l’activer**.
    Avant de pouvoir accéder à l'emplacement du certificat de l'agent de récupération de données, vous devez d'abord créer un tel certificat. Pour obtenir des instructions, voir Créer et vérifier un certificat d’agent de récupération de données de système de fichiers [EFS( Encrypting File System).](/windows/security/information-protection/windows-information-protection/create-and-verify-an-efs-dra-certificate)
    
    Par défaut, les fichiers de travail sont chiffrés à l'aide d'une clé secrète qui est stockée sur l'appareil associé au profil de l'utilisateur. Seul l'utilisateur peut ouvrir et déchiffrer le fichier. Toutefois, si un périphérique est perdu ou si un utilisateur est supprimé, un fichier peut rester bloqué à l'état chiffré. Un administrateur peut utiliser le certificat d’agent de récupération de données (DRA) pour déchiffrer le fichier.
    
    ![Browse to Data Recovery Agent certificate.](../../media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
10. **Développez Protéger des** emplacements réseau et cloud supplémentaires si vous souhaitez ajouter des domaines ou des emplacements SharePoint Online supplémentaires pour vous assurer que les fichiers de toutes les applications répertoriées sont protégés. Si vous devez entrer plusieurs éléments pour chaque champ, utilisez un point-virgule ( ;) entre les différents éléments.
    
    ![Expand Protect additional network and cloud locations, and enter domains or SharePoint Online sites you own.](../../media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
11. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne voulez pas utiliser le groupe de sécurité par défaut **Tous les utilisateurs**, sélectionnez **Modifier**, puis les groupes de sécurité qui recevront ces paramètres \> **Sélectionner**.
12. Enfin, sélectionnez **Ajouter** pour enregistrer la stratégie et l'affecter à des appareils.

## <a name="see-also"></a>Voir aussi

[10 principales façons de sécuriser les Microsoft 365 pour les plans d’entreprise](../security-and-compliance/secure-your-business-data.md)