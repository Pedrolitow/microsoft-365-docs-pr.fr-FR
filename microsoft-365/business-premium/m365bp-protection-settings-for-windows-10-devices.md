---
title: Modifier ou définir les paramètres de protection des applications pour les appareils Windows
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
f1.keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: microsoft-365-business
ms.subservice: business-premium
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection: ''
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment créer ou modifier des stratégies de gestion des applications et protéger des fichiers professionnels sur les appareils Windows personnels de vos utilisateurs.
ms.openlocfilehash: 067cacfdd52b2d0a10bb221d426c54e8cbe9bb16
ms.sourcegitcommit: db89873e22a12705ed313964c1bc2fa19d4fe719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67712546"
---
# <a name="set-or-edit-application-protection-settings-for-windows-devices"></a>Définir ou modifier les paramètres de protection des applications pour les appareils Windows

Vous devez maintenant configurer des stratégies de protection d’application pour les appareils Windows de votre organisation afin de vous assurer que tous vos utilisateurs sont protégés lorsqu’ils utilisent des applications pour leur travail.

## <a name="edit-an-app-management-policy-for-windows-devices"></a>Modifier une stratégie de gestion des applications pour les appareils Windows

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     

2. Dans le volet de navigation gauche, choisissez **Appareils** \> **Stratégies** .

3. Choisissez une stratégie d’application Windows existante, puis **Modifier**.

4. Choisissez **Modifier** à côté d’un paramètre que vous souhaitez modifier, puis **Enregistrer**.

## <a name="create-an-app-management-policy-for-windows-devices"></a>Créer une stratégie de gestion des applications pour les appareils Windows

Si vos utilisateurs disposent d’appareils Windows personnels sur lesquels ils effectuent des tâches professionnelles, vous pouvez protéger vos données sur ces appareils.
  
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
  
10. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne voulez pas utiliser le groupe de sécurité par défaut **Tous les utilisateurs**, sélectionnez **Modifier**, puis les groupes de sécurité qui recevront ces paramètres \> **Sélectionner**.
11. Enfin, sélectionnez **Ajouter** pour enregistrer la stratégie et l'affecter à des appareils.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Objectif suivant

[Validez vos paramètres Windows](m365bp-validate-settings-on-windows-10-pcs.md).