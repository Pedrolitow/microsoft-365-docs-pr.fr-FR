---
title: Définir les paramètres de protection des applications pour les appareils Android ou iOS
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
search.appverid:
- BCS160
- MET150
ms.assetid: 6f2b80b4-81c3-4714-a7bc-ae69313e8a33
description: Découvrez comment créer, modifier ou supprimer une stratégie de gestion des applications et protéger les fichiers de travail sur les appareils Android ou iOS.
ms.openlocfilehash: 0adb103ac3bef72e340c1f5daf54a6b8a184d85c
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42894277"
---
# <a name="set-app-protection-settings-for-android-or-ios-devices"></a>Définir les paramètres de protection des applications pour les appareils Android ou iOS

![Bannière pointant vers https://aka.ms/aboutM365preview.](../media/m365admincenterchanging.png)

## <a name="create-an-app-management-policy"></a>Créer une stratégie de gestion des applications

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
    
2. Dans le volet de navigation de gauche, choisissez **Ajout**de **stratégies** \> de **périphériques** \> .
  
3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie. 
    
4. Sous **type de stratégie**, sélectionnez **gestion des applications pour Android** ou **gestion des applications pour iOS**, en fonction de l’ensemble de stratégies que vous souhaitez créer. 
    
5. Développer **protéger les fichiers de travail en cas de perte ou de vol des appareils** et **gérer la manière dont les utilisateurs accèdent aux fichiers Office sur des appareils mobiles**. Configurez les paramètres de votre choix. **Gérer la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** est **désactivé** par défaut, mais nous vous recommandons de l’activer et **d'** accepter les valeurs par défaut. Pour plus d’informations, consultez la rubrique [available Settings](#available-settings). 
    
    Vous pouvez toujours utiliser le lien **Réinitialiser les paramètres par défaut** pour rétablir la valeur par défaut. 
    
    ![Screenshot of Create a policy with Application management for Android selected](../media/eabbe06d-ac0a-4f3a-8630-68c808b1e662.png)
  
6. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne souhaitez pas utiliser le groupe de sécurité par défaut **tous les utilisateurs** , choisissez **modifier**, puis \> **Sélectionnez**les groupes de sécurité qui obtiennent ces paramètres.
    
7. Enfin, sélectionnez **Terminé** pour enregistrer la stratégie et l'affecter à des appareils. 
    
## <a name="edit-an-app-management-policy"></a>Modifier une stratégie de gestion des applications

1. Dans la fiche **stratégies** , choisissez **modifier la stratégie**.
    
2. Dans le volet **Modifier une stratégie**, sélectionnez la stratégie que vous voulez modifier. 
    
3. Sélectionnez **Modifier** en regard de chaque paramètre pour modifier les valeurs de la stratégie. Lorsque vous modifiez une valeur, elle est automatiquement enregistrée dans la stratégie.
    
4. Lorsque vous avez terminé, fermez le volet **modifier la stratégie** . 
    
## <a name="delete-an-app-management-policy"></a>Supprimer une stratégie de gestion des applications

1. Sur la page **stratégies** , sélectionnez une stratégie, puis **supprimer**.
    
2. Dans le volet **Supprimer la stratégie** , sélectionnez **confirmer** pour supprimer la ou les stratégies que vous avez choisies. 
    
## <a name="available-settings"></a>Paramètres disponibles

Les tableaux suivants fournissent des informations détaillées sur les paramètres disponibles pour protéger les fichiers de travail sur les appareils et les paramètres qui contrôlent la façon dont les utilisateurs accèdent aux fichiers Office à partir de leurs appareils mobiles.
  
 Pour plus d'informations, voir [Correspondance entre les fonctionnalités de protection de Microsoft 365 Business et les paramètres Intune](map-protection-features-to-intune-settings.md). 
  
### <a name="settings-that-protect-work-files"></a>Paramètres de protection des fichiers professionnels

Les paramètres suivants sont disponibles pour protéger les fichiers professionnels si l'appareil d'un utilisateur est perdu ou volé :
  
|||
|:-----|:-----|
|Setting  <br/> |Description  <br/> |
|Supprimer les fichiers professionnels d'un appareil inactif après tant de jours  <br/> |Si un appareil n’est pas utilisé pendant le nombre de jours que vous spécifiez ici, tous les fichiers de travail stockés sur l’appareil seront automatiquement supprimés.  <br/> |
|Obliger les utilisateurs à enregistrer tous les fichiers de travail dans OneDrive Entreprise  <br/> |Si ce paramètre est **activé**, la seule emplacement d’enregistrement disponible pour les fichiers de travail est OneDrive entreprise.  <br/> |
|Chiffrer les fichiers professionnels  <br/> |Laissez ce paramètre **activé** afin que les fichiers professionnels soient protégés par chiffrement. Même si l’appareil est perdu ou volé, personne ne peut lire les données de votre entreprise.  <br/> |
   
### <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a>Paramètres qui contrôlent la façon dont les utilisateurs accèdent aux fichiers Office sur appareils mobiles

Les paramètres suivants sont disponibles pour gérer la manière dont les utilisateurs accèdent aux fichiers professionnels Office :
  
|||
|:-----|:-----|
|Setting  <br/> |Description  <br/> |
|Exiger un code confidentiel ou une empreinte pour accéder aux applications Office  <br/> |Si ce paramètre est **activé** , les utilisateurs doivent fournir une autre forme d’authentification, en plus de leur nom d’utilisateur et de leur mot de passe, avant de pouvoir utiliser les applications Office sur leurs appareils mobiles.<br/> |
|Réinitialiser le code confidentiel en cas d'échecs successifs de la connexion  <br/> |Afin d'empêcher un utilisateur non autorisé de deviner un code confidentiel de façon aléatoire, le code confidentiel est réinitialisé après le nombre d'entrées incorrectes que vous spécifiez.  <br/> |
|Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office  <br/> |Ce paramètre détermine la durée pendant laquelle un utilisateur peut être inactif avant d’être invité à se reconnecter.  <br/> |
|Refuser l'accès aux fichiers de travail sur les appareils « jailbreakés » ou débridés  <br/> |Les utilisateurs intelligents peuvent avoir un appareil jailbreaké ou rooté. Cela signifie que l'utilisateur est en mesure de modifier le système d'exploitation, ce qui peut rendre l'appareil plus vulnérable aux logiciels malveillants. Ces appareils sont bloqués lorsque ce paramètre est **activé**.  <br/> |
|Ne pas autoriser les utilisateurs à copier le contenu des applications Office dans des applications personnelles  <br/> |Cela est interdit par défaut, mais si le paramètre est **activé**, l'utilisateur peut copier des informations d'un fichier professionnel vers un fichier personnel. Si le paramètre est **désactivé**, l'utilisateur ne peut pas copier d'informations à partir d'un compte professionnel vers une application personnelle ou un compte personnel.  <br/> |
