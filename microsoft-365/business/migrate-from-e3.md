---
title: Migrer vers Microsoft 365 entreprise à partir d’Office 365 E3
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
ms.openlocfilehash: d72f0c52a745ff973868b6fdaa95efa1a37a3dbd
ms.sourcegitcommit: e5bc49f0a25954d008b6cc09c2b98bb7bfe1aa2f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "44785927"
---
# <a name="migrating-from-office-365-e3-to-microsoft-365-business-premium"></a>Migration à partir d’Office 365 E3 vers Microsoft 365 Business Premium 

Microsoft 365 Business Premium offre tout ce dont vous avez besoin pour votre petite entreprise, en combinant les meilleures applications de productivité basées sur le Cloud et la sécurité et la gestion des appareils simples. Si vous disposez actuellement d’un abonnement Office 365 E3, mais que vous n’avez pas plus de 300 employés, envisagez de passer à Microsoft 365 Business Premium pour bénéficier de fonctionnalités de sécurité supplémentaires.

La migration est simple : vous changez tout d’abord les licences et toutes vos données et les informations utilisateur dans votre abonnement actuel sont conservées. Après la migration, vous devrez configurer les fonctionnalités ajoutées dans Microsoft 365 Business Premium.

## <a name="differences-between-office-365-e3-and-microsoft-365-business-premium"></a>Différences entre Office 365 E3 et Microsoft 365 Business Premium

Ce tableau présente les différences entre Microsoft 365 Business Premium et Office 365 E3.

| Fonctionnalité    | Prise en charge dans Microsoft 365 Business Premium    | Prise en charge dans Office 365 E3 | 
|:-------|:-----|:-----|
| **Sur site**        | | | 
| Applications Office<sup>1</sup>    | Applications Microsoft 365 pour les entreprises    | Applications Microsoft 365 pour les grandes entreprises | 
| **Applications de productivité sur le Cloud**        | | | 
| Exchange Online et Outlook    | limite de stockage de 50 Go par boîte aux lettres et archivage Exchange Online illimité    | limite de stockage de 100 Go par boîte aux lettres et archivage Exchange Online illimité | 
| Teams    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png) | 
| OneDrive Entreprise    | limite de stockage de 1 to par utilisateur    | Illimité | 
| Yammer, SharePoint Online, planificateur, flux    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png) | 
| StaffHub    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png) | 
| Gestionnaire de clients Outlook, MileIQ    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | | 
| **Protection contre les menaces**        | | | 
| Office 365 Advanced Threat Protection (ATP) plan 1 | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | Non inclus, mais peut être ajouté sur | 
| **Gestion des identités**        | | | 
| Réinitialisation du mot de passe en libre-service pour les comptes hybrides Azure Active Directory (Azure AD), Azure Multi-Factor Authentication (MFA), l’accès conditionnel, l’écriture différée de mot de passe pour les identités locales|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    |  | 
| **Gestion des appareils et des applications**        | | |
| Microsoft Intune, Windows AutoPilot|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    |  |
| Activation d'ordinateurs partagés|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png)| 
| Droits de mise à niveau vers Windows 10 professionnel à partir de licences Win 7/8.1 Pro|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    || 
| **Protection des informations**        | | |
|Prévention des pertes de données Office 365|    ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)|![Inclus dans Office 365 E3](../media/check-mark.png)|
|Azure information Protection Plan 1, application BitLocker|![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)||
|Azure information Protection Plan 1, étiquettes de sensibilité|![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)||
|**Licence d’accès client (CAL)**|||
|Suite CAL Enterprise (Exchange, SharePoint, Skype)||![Inclus dans Office 365 E3](../media/check-mark.png)|

<sup>1</sup> la version Microsoft 365 Business Premium des applications Office n’inclut pas l’activation en volume via la stratégie de groupe, la télémétrie d’application, les contrôles de mise à jour, la comparaison des feuilles de calcul, l’interrogation et l’aide à la décision.

## <a name="migration"></a>Migration

Pour migrer votre abonnement, consultez la rubrique [modifier les offres manuellement](../commerce/subscriptions/change-plans-manually.md) pour obtenir des instructions si vous souhaitez déplacer seulement quelques personnes vers Microsoft 365 Business Premium. Vous pouvez également [mettre à niveau tous les utilisateurs automatiquement](../commerce/subscriptions/upgrade-to-different-plan.md)ou collaborer avec un partenaire pour déplacer votre abonnement et vos licences E3 vers un abonnement Microsoft 365 Business Premium.
Les sections suivantes décrivent les modifications que vous devez effectuer, le cas échéant, et ce que vous pouvez faire après la migration.

### <a name="office-365-e3-subscription-configuration-and-data"></a>Données et configuration de l’abonnement à Office 365 E3
Vous n’avez pas besoin d’effectuer des modifications dans votre abonnement ou vos données actuelles avant la migration, ce qui inclut :

- Configuration des abonnements, tels que les enregistrements DNS et les noms de domaine.
- Les comptes d’utilisateur et de groupe et les paramètres d’authentification, tels que l’authentification multifacteur ou les stratégies d’accès conditionnel.
- Les configurations de service de productivité et leurs données, telles que les équipes, les boîtes aux lettres Exchange Online, les sites SharePoint Online, les dossiers OneDrive entreprise et les blocs-notes OneNote.
- Les applications Office sont mises à l’horizontale automatiquement. La gestion des licences Office 365 moderne vérifie l’attribution de licence de l’utilisateur toutes les 72 heures et convertit les applications Office en version correspondant à l’abonnement de l’utilisateur.

### <a name="windows-10"></a>Windows 10

Si votre Windows ne se trouve pas déjà sur la mise à jour du créateur Windows professionnel, [Mettez-les à niveau vers Windows Pro Creators Update](upgrade-to-windows-pro-creators-update.md).

### <a name="set-up-policies-to-protect-user-devices-and-files"></a>Configurer des stratégies pour protéger les appareils et les fichiers des utilisateurs

> [!NOTE]
> Si vous configurez les stratégies et appareils MDM Office 365, ces appareils seront affichés sur la page **périphériques** dans le centre d’administration Microsoft 365. Toutes les stratégies que vous configurez apparaîtront dans la liste des stratégies classiques dans le [portail Intune](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview).

Une fois que vous avez attribué des licences à Microsoft 365 Business Premium, vous pouvez commencer à protéger les appareils et les fichiers des utilisateurs.

Si vous avez mis à niveau tous les membres de votre organisation vers Microsoft 365 Business Premium, l’Assistant installation s’affiche sur la page d’accueil et vous pouvez suivre les étapes de configuration de [microsoft 365 Business Premium dans l’Assistant de configuration](set-up.md) pour protéger les fichiers et les appareils mobiles.

Vous pouvez également effectuer ces étapes dans la page périphériques :
  
1. Dans le centre d’administration, dans le volet de navigation de gauche, accédez à stratégies de **périphériques** \> **Policies**.
    
2. Sur la page **stratégies d’appareil** , sélectionnez **Ajouter**.
    
3. Dans le volet **Ajouter une stratégie** , donnez un nom à la stratégie, puis choisissez un type de **stratégie** dans la liste déroulante. 
    
     Vous pouvez configurer des stratégies d’application pour protéger les fichiers sur les appareils Android et iPhone, ainsi que Windows 10, et vous pouvez configurer des stratégies de configuration d’appareil pour les appareils Windows 10 appartenant à une société. Pour plus d’informations, consultez les liens suivants :
    
  - [Définir les paramètres de protection des applications pour les appareils Android ou iOS](app-protection-settings-for-android-and-ios.md)
    
  - [Définir les paramètres de protection des applications pour les appareils Windows 10](protection-settings-for-windows-10-devices.md)
    
  - [Définir les paramètres de protection des appareils pour les PC Windows 10](protection-settings-for-windows-10-pcs.md)
  
4. Une fois que vous avez configuré les stratégies, vous et vos employés pouvez configurer des appareils :
    
  - Consultez la rubrique [configurer des appareils Windows pour les utilisateurs de Microsoft 365 Business Premium](set-up-windows-devices.md) pour connaître les étapes des appareils Windows. 
    
  - Consultez la rubrique [configurer des appareils mobiles pour les utilisateurs de Microsoft 365 Business Premium](set-up-mobile-devices.md) pour connaître les étapes des téléphones Android et des iPhone. 

### <a name="threat-protection"></a>Protection contre les menaces

Après la migration vers Microsoft 365 Business Premium, vous disposez d’Office 365 ATP. Consultez la rubrique [Office 365 ATP](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) pour obtenir une vue d’ensemble. Pour configurer, voir [set up ATP Safe Links](https://support.microsoft.com/office/61492713-53c2-47da-a6e7-fa97479e97fa), [set up Safe Attachments](https://support.microsoft.com/office/e7e68934-23dc-4b9c-b714-e82e27a8f8a5)et [set up ATP anti-phishing](https://support.microsoft.com/office/86c425e1-1686-430a-9151-f7176cce4f2c).

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Pour commencer à utiliser les étiquettes de confidentialité, voir [vue d’ensemble des étiquettes de sensibilité](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) et [créer et gérer des étiquettes de confidentialité](https://support.microsoft.com/office/2fb96b54-7dd2-4f0c-ac8d-170790d4b8b9) vidéo.
