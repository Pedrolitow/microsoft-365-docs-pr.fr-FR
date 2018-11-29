---
title: Définir les paramètres de protection des applications pour les appareils Windows 10
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
f1_keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 02e74022-44af-414b-9d74-0ebf5c2197f0
description: Découvrez comment créer une stratégie de gestion d’application et de protection des fichiers de travail sur les appareils Windows 10.
ms.openlocfilehash: acf19a72d994185a35b2e425f8334a73a121ee10
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867041"
---
# <a name="set-application-protection-settings-for-windows-10-devices"></a>Définir les paramètres de protection des applications pour les appareils Windows 10

## <a name="create-an-app-management-policy-for-windows-10"></a>Créer une stratégie de gestion des applications pour Windows 10

Si vos utilisateurs disposent d'appareils Windows 10 sur lesquels ils effectuent des tâches professionnelles, vous pouvez également protéger vos données sur ces appareils.
  
1. Connectez-vous à [Microsoft 365 Business](https://portal.office.com) avec des informations d'identification d'administrateur général. Sélectionnez la vignette **Administrateur** pour accéder au Centre d'administration. 
    
2. Dans la carte **Stratégies d'appareil** du portail d'administration, sélectionnez **Ajouter une stratégie**.
    
    ![Device policies card in the admin center.](media/27c12b61-d112-4348-b557-4f3e46204797.png)
  
3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie. 
    
4. Sous **Type de stratégie**, sélectionnez **Gestion des applications pour Windows 10**.
    
5. Sous ** type d’appareil **, choisissez **personnel** ou **Propriétaire de la société**.
    
6. L'option **Chiffrer les fichiers de travail** est activée automatiquement. 
    
7. Définissez **Empêcher les utilisateurs de copier des données d'entreprise dans leurs fichiers personnels et les obliger à enregistrer les fichiers professionnels dans OneDrive Entreprise** sur **Activé** si vous ne souhaitez pas que les utilisateurs enregistrent des fichiers professionnels sur leur PC. 
    
8. Développez **gérer comment les utilisateurs d’accès aux fichiers Office sur des appareils** \> configurer les paramètres des manière dont vous souhaitez. **Gérer les dont les utilisateurs accèdent les périphériques Office sur des appareils mobiles** est **désactivée** par défaut, mais il est recommandé que vous **allumez** et acceptez les valeurs par défaut. Pour plus d’informations, voir [paramètres disponibles](protection-settings-for-windows-10-devices.md#bkmk_settings) . 
    
    Vous pouvez toujours utiliser le lien **Réinitialiser les paramètres par défaut** pour rétablir la valeur par défaut. 
    
9. Développez **Récupérer les données sur les appareils Windows**. Nous vous recommandons d' **activer** cette option.
    
    Avant de pouvoir accéder à l'emplacement du certificat de l'agent de récupération de données, vous devez d'abord créer un tel certificat. Pour obtenir des instructions, consultez [Créer et vérifier un certificat d'agent de récupération de données EFS (Encrypting File System)](https://go.microsoft.com/fwlink/p/?linkid=853700).
    
    Par défaut, les fichiers de travail sont chiffrés à l'aide d'une clé secrète qui est stockée sur l'appareil associé au profil de l'utilisateur. Seul l'utilisateur peut ouvrir et déchiffrer le fichier. Toutefois, si un périphérique est perdu ou si un utilisateur est supprimé, un fichier peut rester bloqué à l'état chiffré. Le certificat de l'Agent de récupération de données (DRA) peut être utilisé par un administrateur pour déchiffrer le fichier.
    
    ![Browse to Data Recovery Agent certificate.](media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
10. Développez **Protéger les emplacements réseau et cloud supplémentaires** pour ajouter des domaines supplémentaires ou des sites SharePoint Online afin d'assurer que les fichiers de toutes les applications répertoriées seront protégés. Si vous devez entrer plusieurs éléments pour chaque champ, utilisez un point-virgule ( ;) entre les différents éléments. 
    
    ![Expand Protect additional network and cloud locations, and enter domains or SharePoint Online sites you own.](media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
11. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne voulez pas utiliser le groupe de sécurité par défaut **Tous les utilisateurs**, sélectionnez **Modifier**, puis les groupes de sécurité qui recevront ces paramètres \> **Sélectionner**.
    
12. Enfin, sélectionnez **Ajouter** pour enregistrer la stratégie et l'affecter à des appareils. 
    
## <a name="available-settings"></a>Paramètres disponibles

Les paramètres suivants sont disponibles pour gérer la manière dont les utilisateurs accèdent aux fichiers professionnels Office.
  
Pour plus d'informations, voir [Correspondance entre les fonctionnalités de protection de Microsoft 365 Business et les paramètres Intune](map-protection-features-to-intune-settings.md).
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Exiger un code confidentiel ou une empreinte pour accéder aux applications Office  <br/> |Si ce paramètre est **activé**, les utilisateurs doivent fournir une autre forme d'authentification, en plus de leur nom d'utilisateur et de leur mot de passe, pour pouvoir utiliser les applications Office sur leur appareil mobile.  <br/> |
|Réinitialiser le code confidentiel en cas d'échecs successifs de la connexion  <br/> |Afin d'empêcher un utilisateur non autorisé de deviner un code confidentiel de façon aléatoire, le code confidentiel est réinitialisé après le nombre d'entrées incorrectes que vous spécifiez.  <br/> |
|Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office  <br/> |Ce paramètre détermine combien de temps un utilisateur peut être inactif avant d'être invité à se connecter à nouveau.  <br/> |
   

