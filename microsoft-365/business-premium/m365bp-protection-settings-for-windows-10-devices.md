---
title: Modifier ou définir les paramètres de protection des applications pour les appareils Windows 10
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
f1.keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
ms.localizationpriority: high
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
description: Découvrez comment créer ou modifier des stratégies de gestion des applications et protéger des fichiers de travail sur les appareils Windows 10 personnels de vos utilisateurs.
ms.openlocfilehash: f636c138d9364d9bc4739cc5ee11737707d32913
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096009"
---
# <a name="set-or-edit-application-protection-settings-for-windows-10-devices"></a>Définir les paramètres de protection des applications pour les appareils Windows 10

Cet article s’applique à Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender pour les PME est déployée pour les clients Microsoft 365 Business Premium, à compter du 1er mars 2022. Cette offre fournit des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender for Business](../security/defender-business/mdb-overview.md).

## <a name="edit-an-app-management-policy-for-windows-10"></a>Modifier une stratégie de gestion des applications pour Windows 10

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     

2. Dans le volet de navigation gauche, choisissez **Appareils** \> **Stratégies** .

3. Choisissez une stratégie d’application Windows existante, puis **Modifier**.

4. Choisissez **Modifier** à côté d’un paramètre que vous souhaitez modifier, puis **Enregistrer**.

## <a name="create-an-app-management-policy-for-windows-10"></a>Créer une stratégie de gestion des applications pour Windows 10

Si vos utilisateurs disposent d'appareils Windows 10 sur lesquels ils effectuent des tâches professionnelles, vous pouvez également protéger vos données sur ces appareils.
  
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 

2. Dans le volet de navigation gauche, choisissez **Appareils** \> **Stratégies** \> **Ajouter**.

3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie. 

4. Sous **Type de stratégie**, sélectionnez **Gestion des applications pour Windows 10**.

5. Sous **Type d’appareil**, choisissez **Personnel** ou **D’entreprise**.

6. L'option **Chiffrer les fichiers de travail** est activée automatiquement. 

7. Définissez **Empêcher les utilisateurs de copier des données d'entreprise dans leurs fichiers personnels et les obliger à enregistrer les fichiers professionnels dans OneDrive Entreprise** sur **Activé** si vous ne souhaitez pas que les utilisateurs enregistrent des fichiers professionnels sur leur PC. 

8. Développez **Récupérer des données sur les appareils Windows**. Nous vous recommandons de l’**Activer**.
    Avant de pouvoir accéder à l'emplacement du certificat de l'agent de récupération de données, vous devez d'abord créer un tel certificat. Pour obtenir des instructions, consultez [Créer et vérifier un certificat d’agent de récupération de données (DRA) du système de fichiers EFS (EFS)](/windows/security/information-protection/windows-information-protection/create-and-verify-an-efs-dra-certificate).
    
    Par défaut, les fichiers de travail sont chiffrés à l’aide d’une clé secrète stockée sur l’appareil et associée au profil de l’utilisateur. Seul l’utilisateur peut ouvrir et déchiffrer le fichier. Toutefois, si un appareil est perdu ou qu’un utilisateur est supprimé, un fichier peut être bloqué dans un état chiffré. Un administrateur peut utiliser le certificat DRA (Data Recovery Agent) pour déchiffrer le fichier.
    
    ![Browse to Data Recovery Agent certificate.](./../media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
9. Développez **Protégez des emplacements réseau et cloud supplémentaires** si vous souhaitez ajouter des domaines ou des emplacements SharePoint Online supplémentaires pour vous assurer que les fichiers de toutes les applications répertoriées sont protégés. Si vous devez entrer plusieurs éléments pour chaque champ, utilisez un point-virgule (;) entre les éléments.
    
    ![Expand Protect additional network and cloud locations, and enter domains or SharePoint Online sites you own.](./../media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
11. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne voulez pas utiliser le groupe de sécurité par défaut **Tous les utilisateurs**, sélectionnez **Modifier**, puis les groupes de sécurité qui recevront ces paramètres \> **Sélectionner**.
12. Enfin, sélectionnez **Ajouter** pour enregistrer la stratégie et l'affecter à des appareils.

## <a name="see-also"></a>Voir aussi

[10 principales façons de sécuriser les plans Microsoft 365 pour les entreprises](../admin/security-and-compliance/secure-your-business-data.md)