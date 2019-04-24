---
title: Définir les paramètres de protection des applications pour les appareils Android ou iOS
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
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
search.appverid:
- BCS160
- MET150
ms.assetid: 6f2b80b4-81c3-4714-a7bc-ae69313e8a33
description: Découvrez comment créer, modifier ou supprimer une stratégie de gestion des applications et protéger les fichiers de travail sur les appareils Android ou iOS.
ms.openlocfilehash: e81ff8a4bd71dbbbf7ccc31249d450e03f4bd241
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32277445"
---
# <a name="set-app-protection-settings-for-android-or-ios-devices"></a>Définir les paramètres de protection des applications pour les appareils Android ou iOS

## <a name="create-an-app-management-policy"></a>Créer une stratégie de gestion des applications

1. Connectez-vous au [Centre d'administration de Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=837890) avec les informations d'identification d'administrateur général. 
    
2. Dans le centre d'administration, choisissez **stratégies** \> de **périphériques** \> **Ajouter une stratégie**.
  
3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie. 
    
4. Sous **Type de stratégie**, sélectionnez **Gestion des applications pour Android** ou **Gestion des applications pour iOS** selon l'ensemble de stratégies que vous voulez créer. 
    
5. Expand **Protect work files when devices are lost or stolen** and **Manage how users access Office files on mobile devices** \> configure the settings how you would like. The **Manage how users access Office files on mobile devices** is **Off** by default, but it is recommended that you turn it **On** and accept the default values. Pour plus d'informations, consultez la section [paramètres disponibles](#available-settings) . 
    
    Vous pouvez toujours utiliser le lien **Réinitialiser les paramètres par défaut** pour rétablir la valeur par défaut. 
    
    ![Screenshot of Create a policy with Application management for Android selected](media/eabbe06d-ac0a-4f3a-8630-68c808b1e662.png)
  
6. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne voulez pas utiliser le groupe de sécurité par défaut **Tous les utilisateurs**, sélectionnez **Modifier**, puis les groupes de sécurité qui recevront ces paramètres \> **Sélectionner**.
    
7. Enfin, sélectionnez **Terminé** pour enregistrer la stratégie et l'affecter à des appareils. 
    
## <a name="edit-an-app-management-policy"></a>Modifier une stratégie de gestion des applications

1. Dans la fiche **stratégies** , choisissez **modifier la stratégie**.
    
2. Dans le volet **Modifier une stratégie**, sélectionnez la stratégie que vous voulez modifier. 
    
3. Sélectionnez **Modifier** en regard de chaque paramètre pour modifier les valeurs de la stratégie. Lorsque vous modifiez une valeur, celle-ci est enregistrée automatiquement dans la stratégie. 
    
4. Lorsque vous avez terminé, fermez le volet **Modifier une stratégie**. 
    
## <a name="delete-an-app-management-policy"></a>Supprimer une stratégie de gestion des applications

1. On the **Policies** card, choose **Delete policy**.
    
2. Dans le volet **Supprimer la stratégie**, sélectionnez les stratégies à supprimer \> **Sélectionner**, puis **Confirmer** pour supprimer la ou les stratégies que vous avez sélectionnées. 
    
## <a name="available-settings"></a>Paramètres disponibles

Les tableaux suivants donnent des informations détaillées sur les paramètres dont vous disposez pour protéger les fichiers professionnels sur les appareils et sur les paramètres qui contrôlent la manière dont les utilisateurs accèdent aux fichiers Office à partir de leurs appareils mobiles.
  
 Pour plus d'informations, voir [Correspondance entre les fonctionnalités de protection de Microsoft 365 Business et les paramètres Intune](map-protection-features-to-intune-settings.md). 
  
### <a name="settings-that-protect-work-files"></a>Paramètres de protection des fichiers professionnels

Les paramètres suivants sont disponibles pour protéger les fichiers professionnels si l'appareil d'un utilisateur est perdu ou volé :
  
|||
|:-----|:-----|
|Paramètre  <br/> |Description  <br/> |
|Supprimer les fichiers professionnels d'un appareil inactif après tant de jours  <br/> |Si un appareil n'est pas utilisé pendant le nombre de jours que vous spécifiez ici, les fichiers professionnels stockés sur l'appareil sont automatiquement supprimés.  <br/> |
|Obliger les utilisateurs à enregistrer tous les fichiers de travail dans OneDrive Entreprise  <br/> |Si ce paramètre est **activé**, le seul emplacement d'enregistrement accessible pour les fichiers professionnels sera OneDrive Entreprise.  <br/> |
|Chiffrer les fichiers professionnels  <br/> |Laissez ce paramètre **activé** afin que les fichiers professionnels soient protégés par chiffrement. Même si l'appareil est perdu ou volé, personne ne sera en mesure de lire les données de votre société.  <br/> |
   
### <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a>Paramètres qui contrôlent la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles

Les paramètres suivants sont disponibles pour gérer la manière dont les utilisateurs accèdent aux fichiers professionnels Office :
  
|||
|:-----|:-----|
|Paramètre  <br/> |Description  <br/> |
|Exiger un code confidentiel ou une empreinte pour accéder aux applications Office  <br/> |Si ce paramètre est **activé**, les utilisateurs doivent fournir une autre forme d'authentification, en plus de leur nom d'utilisateur et de leur mot de passe, pour pouvoir utiliser les applications Office sur leur appareil mobile.  <br/> |
|Réinitialiser le code confidentiel en cas d'échecs successifs de la connexion  <br/> |Afin d'empêcher un utilisateur non autorisé de deviner un code confidentiel de façon aléatoire, le code confidentiel est réinitialisé après le nombre d'entrées incorrectes que vous spécifiez.  <br/> |
|Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office  <br/> |Ce paramètre détermine combien de temps un utilisateur peut être inactif avant d'être invité à se connecter à nouveau.  <br/> |
|Refuser l'accès aux fichiers de travail sur les appareils « jailbreakés » ou débridés  <br/> |Les utilisateurs intelligents peuvent avoir un appareil jailbreaké ou rooté. Cela signifie que l'utilisateur est en mesure de modifier le système d'exploitation, ce qui peut rendre l'appareil plus vulnérable aux logiciels malveillants. Ces appareils sont bloqués lorsque ce paramètre est **activé**.  <br/> |
|Autoriser les utilisateurs à copier le contenu des applications Office dans des applications personnelles  <br/> |Cela est interdit par défaut, mais si le paramètre est **activé**, l'utilisateur peut copier des informations d'un fichier professionnel vers un fichier personnel. Si le paramètre est **désactivé**, l'utilisateur ne peut pas copier d'informations à partir d'un compte professionnel vers une application personnelle ou un compte personnel.  <br/> |
   

  

