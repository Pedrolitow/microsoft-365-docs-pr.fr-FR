---
title: Définir les paramètres de protection des applications pour les appareils Android ou iOS
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
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
description: Découvrez comment créer, modifier ou supprimer une stratégie de gestion des applications et protéger des fichiers de travail sur des appareils Android ou iOS.
ms.openlocfilehash: 60bc5b3b69eacf9573dd806734cb47355266d3a5
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602053"
---
# <a name="set-app-protection-settings-for-android-or-ios-devices"></a>Définir les paramètres de protection des applications pour les appareils Android ou iOS

Consultez l'[aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

Cet article s’applique à Microsoft 365 Business Premium.

## <a name="watch-secure-office-apps-on-ios"></a>Regarder : Sécuriser les applications Office sur iOS

Regardez cette vidéo ainsi que d’autres sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2197828).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FLvZ?autoplay=false]

Vous pouvez configurer une stratégie d’accès utilisateur qui exige des utilisateurs mobiles qu’ils utilisent un code confidentiel ou une empreinte digitale pour se connecter, et chiffrent les fichiers professionnels stockés sur leurs appareils.

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>.

2. Sous **Stratégies**, choisissez **Ajouter une stratégie**.

3. Dans le volet **Ajouter une stratégie**, entrez un nom sous **Nom de la stratégie**, puis choisissez le type de stratégie souhaité sous **Type de stratégie**.

4. Activez **Protéger les fichiers professionnels lorsque des appareils sont perdus ou volés**, puis vérifiez que les trois paramètres suivants sont activés :
 
    - **Forcer les utilisateurs à enregistrer tous les fichiers de travail sur OneDrive Entreprise**
  
    - **Chiffrer les fichiers de travail**

5. Activez **Gérer la façon dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et vérifiez que les paramètres sont activés ou définis pour chaque élément.

6. Sous **Dans ces applications, les fichiers seront protégés**, sélectionnez les applications Office que vous voulez protéger sur les appareils mobiles.

7. Sous **Qui pourra accéder à ces paramètres ?**, tous les utilisateurs sont sélectionnés par défaut, mais vous pouvez choisir **Modifier** pour sélectionner des groupes de sécurité que vous avez créés.

8. Pour finaliser la création de la stratégie, choisissez **Ajouter**.

9. Dans la page **Ajouter une stratégie**, choisissez **Fermer**.

10. Dans la page d’accueil du Centre d’administration, vérifiez que votre nouvelle stratégie a été ajoutée en choisissant **Stratégies**, puis en examinant votre stratégie dans la page **Stratégies**.

## <a name="create-an-app-management-policy"></a>Créer une stratégie de gestion des applications

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

2. Dans le volet de navigation de gauche, choisissez **Appareils** \> **Stratégies** \> **Ajouter**.
  
3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie.

4. Sous **Type de stratégie**, sélectionnez **Gestion des applications pour Android** ou **Gestion des applications pour iOS** selon l'ensemble de stratégies que vous voulez créer.

5. Développez **Protéger les fichiers de travail lorsque des appareils sont perdus ou volés** et **Gérer l’accès des utilisateurs aux fichiers Office sur les appareils mobiles**. Configurez les paramètres selon vos préférences. L’option **Gérer l’accès des utilisateurs aux fichiers Office sur les appareils mobiles** est **Désactivé** par défaut, mais nous vous recommandons de la définir sur **Activé** et d’accepter les valeurs par défaut. Pour plus d’informations, voir [Paramètres disponibles](#available-settings).

    Vous pouvez toujours utiliser le lien **Réinitialiser les paramètres par défaut** pour rétablir le paramètre par défaut.

:::image type="content" source="Media/m365bp-add-policy.png" alt-text="Créez une stratégie avec la gestion des applications.":::
  
6. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne voulez pas utiliser le groupe de sécurité par défaut **Tous les utilisateurs**, sélectionnez **Modifier**, puis les groupes de sécurité qui recevront ces paramètres \> **Sélectionner**.

7. Enfin, sélectionnez **Terminé** pour enregistrer la stratégie et l'affecter à des appareils.

## <a name="edit-an-app-management-policy"></a>Modifier une stratégie de gestion des applications

1. Dans la carte **Stratégies**, sélectionnez **Modifier une stratégie**.

2. Dans le volet **Modifier une stratégie**, sélectionnez la stratégie que vous voulez modifier.

3. Sélectionnez **Modifier** en regard de chaque paramètre pour modifier les valeurs de la stratégie. Lorsque vous modifiez une valeur, celle-ci est enregistrée automatiquement dans la stratégie.

4. Lorsque vous avez terminé, fermez le volet **Modifier une stratégie**.

## <a name="delete-an-app-management-policy"></a>Supprimer une stratégie de gestion des applications

1. Dans la page **Stratégies** , choisissez une stratégie, puis **supprimer**.

2. Dans le volet **Supprimer la stratégie**, sélectionnez **Confirmer** pour supprimer la ou les stratégies sélectionnées. 

## <a name="available-settings"></a>Paramètres disponibles

Les tableaux suivants donnent des informations détaillées sur les paramètres dont vous disposez pour protéger les fichiers professionnels sur les appareils et sur les paramètres qui contrôlent la manière dont les utilisateurs accèdent aux fichiers Office à partir de leurs appareils mobiles.
  
 Pour plus d'informations, voir [Correspondance entre les fonctionnalités de protection de Microsoft 365 Business Premium et les paramètres Intune](m365bp-map-protection-features-to-intune-settings.md). 
  
### <a name="settings-that-protect-work-files"></a>Paramètres de protection des fichiers professionnels

Les paramètres suivants sont disponibles pour protéger les fichiers professionnels si l'appareil d'un utilisateur est perdu ou volé :


|Paramètre  |Description  |
|:-----|:-----|
|Supprimer les fichiers professionnels d'un appareil inactif après tant de jours  |Si un appareil n'est pas utilisé pendant le nombre de jours que vous spécifiez ici, les fichiers professionnels stockés sur l'appareil sont automatiquement supprimés.  |
|Obliger les utilisateurs à enregistrer tous les fichiers de travail dans OneDrive Entreprise  |Si ce paramètre est sur **Activé**, le seul emplacement d'enregistrement accessible pour les fichiers professionnels sera OneDrive Entreprise.  |
|Chiffrer les fichiers professionnels  |Laissez ce paramètre sur **Activé** afin que les fichiers professionnels soient protégés par chiffrement. Même si l'appareil est perdu ou volé, personne ne pourra lire les données de votre société.  |

### <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a>Paramètres qui contrôlent la façon dont les utilisateurs accèdent aux fichiers Office sur appareils mobiles

Les paramètres suivants sont disponibles pour gérer la manière dont les utilisateurs accèdent aux fichiers professionnels Office :

|Paramètre  |Description  |
|:-----|:-----|
|Exiger un code confidentiel ou une empreinte pour accéder aux applications Office  |Si ce paramètre est sur **Activé**, les utilisateurs doivent fournir une autre forme d'authentification, en plus de leur nom d'utilisateur et de leur mot de passe, pour pouvoir utiliser les applications Office sur leur appareil mobile.|
|Réinitialiser le code confidentiel en cas d'échecs successifs de la connexion  |Afin d'empêcher un utilisateur non autorisé de deviner un code confidentiel de façon aléatoire, le code confidentiel est réinitialisé après le nombre d'entrées incorrectes que vous spécifiez.  |
|Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office  |Ce paramètre détermine combien de temps un utilisateur peut être inactif avant d'être invité à se connecter à nouveau.  |
|Refuser l'accès aux fichiers de travail sur les appareils « jailbreakés » ou débridés  |Les utilisateurs intelligents peuvent avoir un appareil jailbreaké ou rooté. Cela signifie que l'utilisateur est en mesure de modifier le système d'exploitation, ce qui peut rendre l'appareil plus vulnérable aux logiciels malveillants. Ces appareils sont bloqués lorsque ce paramètre est **activé**.    |
|Ne pas autoriser les utilisateurs à copier le contenu des applications Office dans des applications personnelles  |Cela est interdit par défaut, mais si le paramètre est sur **Activé**, l'utilisateur peut copier des informations d'un fichier professionnel vers un fichier personnel. Si le paramètre est sur **Désactivé**, l'utilisateur ne peut pas copier d'informations à partir d'un compte professionnel vers une application personnelle ou un compte personnel.  |

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)