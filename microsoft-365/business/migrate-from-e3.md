---
title: Migrer vers Microsoft 365 Entreprise à partir de Office 365 E3
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
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
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
description: Si vous avez un abonnement Office 365 E3 mais que vous n’avez pas plus de 300 employés, envisagez de passer à Microsoft 365 Business Premium.
ms.openlocfilehash: c1b4da07b3bf28cce1a48424ab45cde6ea54d367
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53394168"
---
# <a name="migrating-from-office-365-e3-to-microsoft-365-business-premium"></a>Migration de Office 365 E3 vers Microsoft 365 Business Premium

Microsoft 365 Business Premium dispose de tout ce dont vous avez besoin pour votre petite entreprise, en combinant les applications de productivité cloud les plus populaires avec une gestion et une sécurité des appareils simples. Si vous disposez actuellement d’un abonnement Office 365 E3, mais que vous n’avez pas plus de 300 employés, envisagez de passer à Microsoft 365 Business Premium fonctionnalités de sécurité supplémentaires.

La migration est simple : vous devez d’abord changer de licence et toutes vos données et informations utilisateur dans votre abonnement actuel sont conservées. Après la migration, vous devez configurer les fonctionnalités ajoutées dans Microsoft 365 Business Premium.

## <a name="differences-between-office-365-e3-and-microsoft-365-business-premium"></a>Différences entre Office 365 E3 et Microsoft 365 Business Premium

Ce tableau présente les différences entre Microsoft 365 Business Premium et Office 365 E3.

| Fonctionnalité    | Prise en charge dans Microsoft 365 Business Premium    | Prise en charge dans Office 365 E3 |
|:-------|:-----|:-----|
| **Sur site**        | | |
| Office applications<sup>1</sup>    | Microsoft 365 Apps for business    | Microsoft 365 Apps for enterprise |
| **Applications de productivité cloud**        | | |
| Exchange Online et Outlook    | Limite de stockage de 50 Go par boîte aux lettres et nombre Archivage Exchange Online    | Limite de stockage de 100 Go par boîte aux lettres et nombre Archivage Exchange Online |
| Teams    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png) | 
| OneDrive Entreprise    | Limite de stockage de 1 To par utilisateur    | Illimité | 
| Yammer, SharePoint Online, Planner, Stream    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png) | 
| StaffHub    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png) |
| **Protection contre les menaces**        | | |
| Microsoft Defender pour Office 365 Plan 1 | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | Non inclus, mais peut être ajouté sur |
| **Gestion des identités**        | | |
| Réinitialisation du mot de passe en libre-service pour les comptes Azure Active Directory hybrides (Azure AD), authentification multifacteur Azure AD (MFA), accès conditionnel, écriture écriture par mot de passe pour les identités locales|     ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    |  |
| **Données de gestion des appareils et des applications**        | | |
| Microsoft Intune, Windows AutoPilot|     ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    |  |
| Activation d'ordinateurs partagés|     ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Office 365 E3](../media/check-mark.png)| 
| Droits de mise à niveau Windows 10 Professionnel à partir de licences win 7/8.1 Pro licences|     ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    ||
| **Protection des informations**        | | |
|Prévention des pertes de données Office 365|    ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)|![Inclus dans Office 365 E3](../media/check-mark.png)|
|Azure Information Protection Plan 1, application de BitLocker|![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)||
|Azure Information Protection Plan 1, Étiquettes de sensibilité|![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)||
|**Licence d’accès client (droits cal)**|||
|Enterprise CAL Suite (Exchange, SharePoint, Skype)||![Inclus dans Office 365 E3](../media/check-mark.png)|

<sup>1</sup> La version Microsoft 365 Business Premium des applications Office n’inclut pas l’activation en volume par le biais de la stratégie de groupe, de la télémétrie d’application, des contrôles de mise à jour, de la comparaison et de l’analyse de feuilles de calcul ou de l’intelligence métier.

## <a name="migration"></a>Migration

Pour migrer votre abonnement, consultez [les plans](../commerce/subscriptions/change-plans-manually.md) de modification manuellement pour obtenir des instructions si vous souhaitez déplacer uniquement quelques personnes vers Microsoft 365 Business Premium. Vous pouvez également mettre [à](../commerce/subscriptions/upgrade-to-different-plan.md)niveau tout le monde automatiquement ou travailler avec un partenaire pour déplacer votre abonnement E3 et vos licences vers un abonnement Microsoft 365 Business Premium abonnement.
Les sections suivantes décrivent les modifications que vous devez apporter, le cas nécessaire, et ce que vous pouvez faire après la migration.

### <a name="office-365-e3-subscription-configuration-and-data"></a>Office 365 E3 de configuration et de données d’abonnement
Vous n’avez pas besoin d’apporter des modifications à votre abonnement ou données actuels avant la migration, notamment :

- Configuration de l’abonnement, telle que les enregistrements DNS et les noms de domaine.
- Comptes d’utilisateur et de groupe et paramètres d’authentification, tels que l’authentification multifacteur ou les stratégies d’accès conditionnel.
- Configurations des services de productivité et leurs données, telles que les Teams, les boîtes aux lettres Exchange Online, les sites SharePoint Online, les dossiers OneDrive Entreprise et les blocs-OneNote portables.
- Office applications seront automatiquement mis à l’échelle. Office 365 licence moderne vérifie l’attribution de licence de l’utilisateur toutes les 72 heures et convertit les applications Office la version qui correspond à l’abonnement utilisateur.

### <a name="windows-10"></a>Windows 10

Si votre Windows n’est pas déjà Windows Pro la mise à jour du Créateur, mettez-les à [niveau vers Windows Pro Creators Update.](upgrade-to-windows-pro-creators-update.md)

### <a name="set-up-policies-to-protect-user-devices-and-files"></a>Configurer des stratégies pour protéger les appareils et les fichiers des utilisateurs

> [!NOTE]
> Si vous avez Office 365 des stratégies et des appareils de gestion des périphériques mobiles, ces appareils sont répertoriés dans la **page** Appareils de la Centre d’administration Microsoft 365. Toutes les stratégies que vous avez définies s’afficheront dans la liste des stratégies classiques dans [le portail Intune.](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)

Une fois que vous avez affecté des licences à Microsoft 365 Business Premium, vous pouvez commencer à protéger les appareils et les fichiers des utilisateurs.

Si vous avez mis à niveau tous les membres de votre organisation vers Microsoft 365 Business Premium, vous verrez l’Assistant Configuration sur la page d’accueil et pouvez suivre [l’Microsoft 365 Business Premium](set-up.md) De configuration dans les étapes de l’Assistant d’installation pour protéger les fichiers et les appareils mobiles.

Vous pouvez également effectuer ces étapes dans la page Appareils :
  
1. Dans le centre d’administration, dans  le navigation gauche, allez à \> **Stratégies des appareils.**

2. Dans la page **Stratégies d’appareil,** choisissez **Ajouter.**

3. Dans le **volet Ajouter une** stratégie, donnez un nom à la stratégie, puis choisissez un **type** de stratégie dans la zone de la zone de baisse.

     Vous pouvez configurer des stratégies d’application pour la protection des fichiers sur les appareils Android et iPhone, ainsi que des Windows 10, et vous pouvez configurer des stratégies de configuration d’appareil pour les appareils Windows 10 entreprise. Pour plus d’informations, voir les liens suivants :

  - [Définir les paramètres de protection des applications pour les appareils Android ou iOS](app-protection-settings-for-android-and-ios.md)

  - [Définir les paramètres de protection des applications pour les appareils Windows 10](protection-settings-for-windows-10-devices.md)

  - [Définir les paramètres de protection des appareils pour Windows 10 PC](protection-settings-for-windows-10-pcs.md)
  
4. Une fois les stratégies définies, vous et vos employés pouvez configurer des appareils :

  - Voir [Configurer des Windows pour les Microsoft 365 Business Premium utilisateurs pour](set-up-windows-devices.md) obtenir les étapes à suivre Windows appareils. 

  - Voir [Configurer des appareils mobiles pour Microsoft 365 Business Premium utilisateurs pour](set-up-mobile-devices.md) obtenir la procédure pour les téléphones et iPhone Android. 
  
### <a name="mailbox-size"></a>Taille de la boîte aux lettres

Microsoft 365 Business Premium a une limite de stockage de 50 Go, car il utilise Exchange Online Plan 1. Lors de la migration vers Microsoft 365 Business Premium, si l’un de vos utilisateurs dépasse 50 Go de stockage de boîtes aux lettres, il est recommandé d’affecter à cet utilisateur un plan Exchange Online Plan 2 et de supprimer le plan Exchange Online Plan 1, car il n’est pas possible d’affecter les deux.

### <a name="threat-protection"></a>Protection contre les menaces

Après avoir migré vers Microsoft 365 Business Premium, vous avez Defender for Office 365. Consultez [Microsoft Defender pour Office 365](../security/office-365-security/defender-for-office-365.md) pour obtenir une vue d’ensemble. Pour configurer, voir [configurer](https://support.microsoft.com/office/61492713-53c2-47da-a6e7-fa97479e97fa)Coffre liens, configurer Coffre [pièces jointes](https://support.microsoft.com/office/e7e68934-23dc-4b9c-b714-e82e27a8f8a5)et configurer l’anti-hameçonnage dans [Defender pour Office 365](https://support.microsoft.com/office/86c425e1-1686-430a-9151-f7176cce4f2c).

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Pour commencer à utiliser des étiquettes de sensibilité, voir [Vue d’ensemble](../compliance/sensitivity-labels.md) des étiquettes de sensibilité et créer et gérer la vidéo sur [les étiquettes de](../business-video/create-sensitivity-labels.md) sensibilité.

## <a name="related-content"></a>Contenu associé

[Modifier les plans manuellement](../commerce/subscriptions/change-plans-manually.md) (article)\
[Mettre à niveau Windows appareils vers Windows 10 Professionnel](upgrade-to-windows-pro-creators-update.md) (vidéo)\
[Définir les paramètres de protection des applications pour les appareils Android](app-protection-settings-for-android-and-ios.md) ou iOS (article)\
[Définir ou modifier les paramètres de protection des](protection-settings-for-windows-10-devices.md) applications pour Windows 10 appareils mobiles (article)\
[]

