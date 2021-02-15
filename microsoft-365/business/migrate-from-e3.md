---
title: Migrer vers Microsoft 365 Business à partir d’Office 365 E3
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
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Découvrez comment déplacer votre entreprise vers Microsoft 365 Business Premium à partir d’Office 365 E3.
ms.openlocfilehash: eebf78c24ed4bfd1a4fc2d843f37aebbe3d35e31
ms.sourcegitcommit: c1dd5be42fe0c5dcc7c05817c941edd9076febf8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49558255"
---
# <a name="migrating-from-office-365-e3-to-microsoft-365-business-premium"></a>Migration d’Office 365 E3 vers Microsoft 365 Business Premium 

Microsoft 365 Business Premium offre tout ce dont vous avez besoin pour votre petite entreprise, en combinant les applications de productivité basées sur le cloud les plus classes avec une gestion et une sécurité des appareils simples. Si vous disposez actuellement d’un abonnement Office 365 E3, mais que vous n’avez pas plus de 300 employés, envisagez de passer à Microsoft 365 Business Premium pour ajouter des fonctionnalités de sécurité.

La migration est simple : vous changez d’abord de licence et toutes vos données et informations utilisateur dans votre abonnement actuel sont conservées. Après la migration, vous devez configurer les fonctionnalités ajoutées dans Microsoft 365 Business Premium.

## <a name="differences-between-office-365-e3-and-microsoft-365-business-premium"></a>Différences entre Office 365 E3 et Microsoft 365 Business Premium

Ce tableau présente les différences entre Microsoft 365 Business Premium et Office 365 E3.

| Fonctionnalité    | Prise en charge dans Microsoft 365 Business Premium    | Prise en charge dans Office 365 E3 | 
|:-------|:-----|:-----|
| **Sur site**        | | | 
| Applications Office<sup>1</sup>    | Applications Microsoft 365 pour les entreprises    | Applications Microsoft 365 for entreprise | 
| **Applications de productivité cloud**        | | | 
| Exchange Online et Outlook    | Limite de stockage de 50 Go par boîte aux lettres et nombre Archivage Exchange Online    | Limite de stockage de 100 Go par boîte aux lettres et nombre Archivage Exchange Online | 
| Teams    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png) | 
| OneDrive Entreprise    | Limite de stockage de 1 To par utilisateur    | Illimité | 
| Yammer, SharePoint Online, Planificateur, Stream    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png) | 
| StaffHub    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png) | 
| Gestionnaire client Outlook, MileIQ    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | | 
| **Protection contre les menaces**        | | | 
| Defender pour Office 365 Plan 1 | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | Non inclus, mais peut être ajouté sur | 
| **Gestion des identités**        | | | 
| Réinitialisation du mot de passe en libre-service pour les comptes Azure Active Directory (Azure AD) hybrides, authentification multifacteur Azure AD (MFA), accès conditionnel, écriture d’écriture de mot de passe pour les identités locales|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    |  | 
| **Données de gestion des appareils et des applications**        | | |
| Microsoft Intune, Windows AutoPilot|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    |  |
| Activation d'ordinateurs partagés|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png)| 
| Mettre à niveau les droits vers Windows 10 Professionnel à partir des licences Win 7/8.1 Professionnel|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    || 
| **Protection des informations**        | | |
|Prévention des pertes de données Office 365|    ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)|![Inclus dans Office 365 E3](../media/check-mark.png)|
|Azure Information Protection Plan 1, application de Bitlocker|![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)||
|Azure Information Protection Plan 1, Étiquettes de sensibilité|![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)||
|**Licence d’accès client (droits cal)**|||
|Enterprise CAL Suite (Exchange, SharePoint, Skype)||![Inclus dans Office 365 E3](../media/check-mark.png)|

<sup>1</sup> La version Microsoft 365 Business Premium des applications Office n’inclut pas l’activation en volume par le biais de la stratégie de groupe, de la télémétrie d’application, des contrôles de mise à jour, de la comparaison et de l’analyse de feuilles de calcul ou de l’aide à la commande.

## <a name="migration"></a>Migration

Pour migrer votre abonnement, consultez [Les plans](../commerce/subscriptions/change-plans-manually.md) de modification manuellement pour obtenir des instructions si vous souhaitez déplacer quelques personnes vers Microsoft 365 Business Premium. Vous pouvez également mettre [à](../commerce/subscriptions/upgrade-to-different-plan.md)niveau tout le monde automatiquement ou travailler avec un partenaire pour déplacer votre abonnement E3 et vos licences vers un abonnement Microsoft 365 Business Premium.
Les sections suivantes décrivent les modifications que vous devez apporter, le cas nécessaire, et ce que vous pouvez faire après la migration.

### <a name="office-365-e3-subscription-configuration-and-data"></a>Configuration et données de l’abonnement Office 365 E3
Vous n’avez pas besoin d’apporter des modifications à votre abonnement ou données actuels avant la migration, notamment :

- Configuration de l’abonnement, telle que les enregistrements DNS et les noms de domaine.
- Comptes d’utilisateur et de groupe et paramètres d’authentification, tels que l’authentification multifacteur ou les stratégies d’accès conditionnel.
- Configurations du service de productivité et leurs données, telles que Teams, boîtes aux lettres Exchange Online, sites SharePoint Online, dossiers OneDrive Entreprise et blocs-notes OneNote.
- Les applications Office sont automatiquement mis à l’échelle. Les licences modernes Office 365 vérifient l’attribution de licence de l’utilisateur toutes les 72 heures et convertissent les applications Office en la version qui correspond à l’abonnement utilisateur.

### <a name="windows-10"></a>Windows 10

Si votre windows n’est pas déjà sur la mise à jour du Créateur Windows Pro, mettez-les à [niveau vers Windows Pro Creators Update.](upgrade-to-windows-pro-creators-update.md)

### <a name="set-up-policies-to-protect-user-devices-and-files"></a>Configurer des stratégies pour protéger les appareils et les fichiers des utilisateurs

> [!NOTE]
> Si vous avez installé des stratégies et des appareils de gestion des appareils mobiles Office 365, ces appareils sont répertoriés dans la **page** Appareils du Centre d’administration Microsoft 365. Toutes les stratégies que vous avez définies s’afficheront dans la liste des stratégies classiques dans [le portail Intune.](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)

Une fois que vous avez attribué des licences à Microsoft 365 Business Premium, vous pouvez commencer à protéger les appareils et les fichiers des utilisateurs.

Si vous avez mis à niveau tous les membres de votre organisation vers Microsoft 365 Business Premium, vous verrez l’Assistant Configuration sur la page d’accueil et pouvez suivre la procédure Configurer [Microsoft 365 Business Premium](set-up.md) dans les étapes de l’Assistant Configuration pour protéger les fichiers et les appareils mobiles.

Vous pouvez également effectuer ces étapes dans la page Appareils :
  
1. Dans le centre d’administration, dans le navigation gauche, allez à **Stratégies des** \> **appareils.**
    
2. Dans la page **Stratégies d’appareil,** choisissez **Ajouter.**
    
3. Dans le **volet Ajouter une** stratégie, donnez un nom à la stratégie, puis choisissez un **type** de stratégie dans la zone de la zone de baisse. 
    
     Vous pouvez configurer des stratégies d’application pour la protection des fichiers sur les appareils Android et iPhone, ainsi que Windows 10, et vous pouvez configurer des stratégies de configuration d’appareil pour les appareils Windows 10 d’entreprise. Pour plus d’informations, voir les liens suivants :
    
  - [Définir les paramètres de protection des applications pour les appareils Android ou iOS](app-protection-settings-for-android-and-ios.md)
    
  - [Définir les paramètres de protection des applications pour les appareils Windows 10](protection-settings-for-windows-10-devices.md)
    
  - [Définir les paramètres de protection des appareils pour les PC Windows 10](protection-settings-for-windows-10-pcs.md)
  
4. Une fois les stratégies définies, vous et vos employés pouvez configurer des appareils :
    
  - Voir [Configurer des appareils Windows pour les utilisateurs de Microsoft 365 Business Premium](set-up-windows-devices.md) pour obtenir la procédure à suivre pour les appareils Windows. 
    
  - Voir Configurer des appareils mobiles pour [les utilisateurs de Microsoft 365 Business Premium](set-up-mobile-devices.md) pour obtenir la procédure pour les téléphones et iPhone Android. 
  
### <a name="mailbox-size"></a>Taille de la boîte aux lettres

Microsoft 365 Business Premium a une limite de stockage de 50 Go car il utilise Exchange Online Plan 1. Lors de la migration vers Microsoft 365 Business Premium, si l’un de vos utilisateurs dépasse 50 Go de stockage de boîtes aux lettres, il est recommandé d’affecter à cet utilisateur un plan Exchange Online 2 et de supprimer l’offre Exchange Online Plan 1, car il n’est pas possible d’affecter les deux.


### <a name="threat-protection"></a>Protection contre les menaces

Après avoir migré vers Microsoft 365 Business Premium, vous avez Defender pour Office 365. Consultez [Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) pour obtenir une vue d’ensemble. Pour configurer, voir [configurer](https://support.microsoft.com/office/61492713-53c2-47da-a6e7-fa97479e97fa)des liens sécurisés, configurer des pièces [jointes sécurisées](https://support.microsoft.com/office/e7e68934-23dc-4b9c-b714-e82e27a8f8a5)et configurer l’anti-hameçonnage dans [Defender pour Office 365.](https://support.microsoft.com/office/86c425e1-1686-430a-9151-f7176cce4f2c)

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Pour commencer à utiliser des étiquettes de sensibilité, voir [Vue](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) d’ensemble des étiquettes de sensibilité et créer et gérer la vidéo sur [les étiquettes de](https://support.microsoft.com/office/2fb96b54-7dd2-4f0c-ac8d-170790d4b8b9) sensibilité.
