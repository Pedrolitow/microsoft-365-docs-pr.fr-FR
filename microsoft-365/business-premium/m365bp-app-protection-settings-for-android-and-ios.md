---
title: Définir les paramètres de protection des applications pour les appareils Android ou iOS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 6f2b80b4-81c3-4714-a7bc-ae69313e8a33
description: Découvrez comment créer, modifier ou supprimer une stratégie de gestion des applications et protéger les fichiers de travail sur les appareils Android ou iOS.
ms.openlocfilehash: 8965f70a19161be24f4276b8dac20c84865d9a71
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64635335"
---
# <a name="set-app-protection-settings-for-android-or-ios-devices"></a>Définir les paramètres de protection des applications pour les appareils Android ou iOS

Cet article s’applique aux Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender pour les PME est en Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Cette offre offre des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender pour les entreprises](../business-premium/m365bp-app-protection-settings-for-android-and-ios.md).

## <a name="watch-secure-office-apps-on-ios"></a>Regardez : Sécuriser Office applications sur iOS

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FLvZ?autoplay=false]

Vous pouvez configurer une stratégie d’accès utilisateur qui oblige les utilisateurs mobiles à entrer un code confidentiel ou une empreinte digitale pour se connecter, et chiffre également les fichiers de travail stockés sur leurs appareils.

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>.

2. Sous **Stratégies**, **sélectionnez Ajouter une stratégie**.

3. Dans le **volet Ajouter une** stratégie, entrez un nom sous nom de **stratégie, puis** choisissez le type de stratégie que vous souhaitez sous **Type de stratégie**.

4. Activer la **gestion de la façon dont les utilisateurs accèdent Office fichiers sur** les appareils mobiles, puis assurez-vous que les trois paramètres suivants sont actifs :
 
    - **Exiger un code confidentiel ou une empreinte pour accéder aux applications Office**
 
    - **Protéger les fichiers de travail en cas de perte ou de vol d’appareils**
 
    - **Chiffrer les fichiers de travail**

5. Sous **Les fichiers de ces applications** seront protégés, sélectionnez les Office que vous souhaitez protéger sur les appareils mobiles.

6. Sous Qui vous obtenez ces paramètres ?, tous les **utilisateurs sont sélectionnés** par défaut, mais vous pouvez choisir Modifier  pour sélectionner les groupes de sécurité que vous avez créés.

7. Pour terminer la création de la stratégie, choisissez **Ajouter**.

8. Dans la page **Ajouter une stratégie** , choisissez **Fermer**.

9. Dans la page d’accueil du Centre d’administration, confirmez que votre nouvelle stratégie  a été ajoutée en choisissant Stratégies et en l’avisant sur la page **Stratégies**.

## <a name="create-an-app-management-policy"></a>Créer une stratégie de gestion des applications

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
    
2. Dans le navigation de gauche, choisissez **Ajouter des** **stratégies**\> **d’appareils**\>.
  
3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie. 
    
4. Sous **Type de stratégie**, choisissez **Gestion des applications pour Android** ou Gestion des applications **pour iOS**, en fonction de l’ensemble de stratégies que vous souhaitez créer. 
    
5. **Développez Protéger les fichiers professionnels lorsque des appareils sont** perdus ou volés et gérez la façon dont les utilisateurs **accèdent Office fichiers sur les appareils mobiles**. Configurez les paramètres comme vous le souhaitez. **Gérer la façon dont les utilisateurs accèdent Office fichiers** sur  les appareils mobiles est éteint par défaut, mais nous vous  recommandons de l’activer et d’accepter les valeurs par défaut. Pour plus d’informations, voir [Paramètres disponibles](#available-settings). 
    
    Vous pouvez toujours utiliser le lien **Réinitialiser les paramètres par défaut** pour rétablir la valeur par défaut. 
    
    ![Capture d’écran de Créer une stratégie avec la gestion des applications pour Android sélectionnée.](/media/eabbe06d-ac0a-4f3a-8630-68c808b1e662.png)
  
6. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne souhaitez pas utiliser le groupe de  sécurité Par défaut Tous les utilisateurs, choisissez **Modifier, choisissez** les groupes de sécurité qui obtiennent ces paramètres \> **Sélectionner**.
    
7. Enfin, sélectionnez **Terminé** pour enregistrer la stratégie et l'affecter à des appareils. 
    
## <a name="edit-an-app-management-policy"></a>Modifier une stratégie de gestion des applications

1. Dans la carte **Stratégies** , choisissez **Modifier la stratégie**.
    
2. Dans le volet **Modifier une stratégie**, sélectionnez la stratégie que vous voulez modifier. 
    
3. Sélectionnez **Modifier** en regard de chaque paramètre pour modifier les valeurs de la stratégie. Lorsque vous modifiez une valeur, elle est automatiquement enregistrée dans la stratégie.
    
4. Lorsque vous avez terminé, fermez le volet Modifier **la** stratégie. 
    
## <a name="delete-an-app-management-policy"></a>Supprimer une stratégie de gestion des applications

1. Dans la page **Stratégies** , choisissez une stratégie, puis **supprimez**.
    
2. Dans le **volet Supprimer la stratégie** , choisissez **Confirmer** pour supprimer la ou les stratégies que vous avez choisies. 
    
## <a name="available-settings"></a>Paramètres disponibles

Les tableaux suivants donnent des informations détaillées sur les paramètres disponibles pour protéger les fichiers professionnels sur les appareils et sur les paramètres qui contrôlent la façon dont les utilisateurs accèdent aux fichiers Office à partir de leurs appareils mobiles.
  
 Pour plus d’informations, voir [How do protection features in Microsoft 365 Business Premium map to Intune settings](m365bp-map-protection-features-to-intune-settings.md). 
  
### <a name="settings-that-protect-work-files"></a>Paramètres de protection des fichiers professionnels

Les paramètres suivants sont disponibles pour protéger les fichiers professionnels si l'appareil d'un utilisateur est perdu ou volé :


|Paramètre  |Description  |
|:-----|:-----|
|Supprimer les fichiers professionnels d'un appareil inactif après tant de jours  |Si un appareil n’est pas utilisé pendant le nombre de jours que vous spécifiez ici, tous les fichiers de travail stockés sur l’appareil sont supprimés automatiquement.  |
|Obliger les utilisateurs à enregistrer tous les fichiers de travail dans OneDrive Entreprise  |Si ce paramètre est **sur,** le seul emplacement d’enregistrer disponible pour les fichiers de travail est OneDrive Entreprise.  |
|Chiffrer les fichiers professionnels  |Laissez ce paramètre **activé** afin que les fichiers professionnels soient protégés par chiffrement. Même si l’appareil est perdu ou volé, personne ne peut lire les données de votre entreprise.  |
   
### <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a>Paramètres qui contrôlent la façon dont les utilisateurs accèdent aux fichiers Office sur appareils mobiles

Les paramètres suivants sont disponibles pour gérer la manière dont les utilisateurs accèdent aux fichiers professionnels Office :


|Paramètre  |Description  |
|:-----|:-----|
|Exiger un code confidentiel ou une empreinte pour accéder aux applications Office  |Si ce paramètre est  Sur, les utilisateurs doivent fournir une autre forme d’authentification, en plus de leur nom d’utilisateur et mot de passe, pour pouvoir utiliser des applications Office sur leurs appareils mobiles.|
|Réinitialiser le code confidentiel en cas d'échecs successifs de la connexion  |Afin d'empêcher un utilisateur non autorisé de deviner un code confidentiel de façon aléatoire, le code confidentiel est réinitialisé après le nombre d'entrées incorrectes que vous spécifiez.  |
|Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office  |Ce paramètre détermine la durée pendant combien de temps un utilisateur peut être inactif avant d’être invité à se ré-inscrire.  |
|Refuser l'accès aux fichiers de travail sur les appareils « jailbreakés » ou débridés  |Les utilisateurs intelligents peuvent avoir un appareil jailbreaké ou rooté. Cela signifie que l'utilisateur est en mesure de modifier le système d'exploitation, ce qui peut rendre l'appareil plus vulnérable aux logiciels malveillants. Ces appareils sont bloqués lorsque ce paramètre est **activé**.    |
|Ne pas autoriser les utilisateurs à copier du contenu de Office applications dans des applications personnelles  |Cela est interdit par défaut, mais si le paramètre est **activé**, l'utilisateur peut copier des informations d'un fichier professionnel vers un fichier personnel. Si le paramètre est **désactivé**, l'utilisateur ne peut pas copier d'informations à partir d'un compte professionnel vers une application personnelle ou un compte personnel.  |

## <a name="see-also"></a>Voir aussi

[10 principales façons de sécuriser les Microsoft 365 pour les plans d’entreprise](../admin/security-and-compliance/secure-your-business-data.md)