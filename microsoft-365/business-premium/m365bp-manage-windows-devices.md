---
title: Activer la gestion des appareils Windows 10 joints à un domaine par Microsoft 365 entreprise
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
description: Découvrez comment activer les Microsoft 365 pour protéger les appareils joints à Active Directory Windows 10 en quelques étapes seulement.
ms.openlocfilehash: b57d9f4f13985d5d67b39d6486df089b82f4f05c
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64635400"
---
# <a name="enable-domain-joined-windows-10-devices-to-be-managed-by-microsoft-365-business-premium"></a>Activer la gestion des appareils Windows 10 joints à un domaine par des Microsoft 365 Business Premium

> [!NOTE]
> Microsoft Defender pour les PME est en Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Cette offre offre des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender pour les entreprises](../security/defender-business/mdb-overview.md).

Si votre organisation utilise Windows Server Active Directory localement, vous pouvez configurer Microsoft 365 Business Premium pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale.
Pour configurer cette protection, vous pouvez **implémenter des appareils joints Azure AD hybrides**. Ces appareils sont joints à votre Active Directory local et à votre Azure Active Directory.

## <a name="watch-configure-hybrid-azure-active-directory-join"></a>Regardez : Configurer la joint Azure Active Directory hybride

Cette vidéo décrit les étapes à suivre pour la configurer pour le scénario le plus courant, qui est également détaillée dans les étapes qui suivent.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3C9hO]
  
## <a name="before-you-begin"></a>Avant de commencer

- Synchronisez les utilisateurs Azure AD avec Azure AD Connecter.
- Terminez Azure AD Connecter synchronisation de l’unité d’organisation (OU).
- Assurez-vous que tous les utilisateurs de domaine que vous synchronisez ont des licences Microsoft 365 Business Premium.

Pour [plus d’Microsoft 365](../admin/setup/manage-domain-users.md), voir Synchroniser les utilisateurs de domaine.

## <a name="1-verify-mdm-authority-in-intune"></a>1. Vérifiez l’autorité de gestion des Intune

Go to the Microsoft Endpoint Manager admin center ([https://endpoint.microsoft.com](https://endpoint.microsoft.com/#blade/Microsoft_Intune_Enrollment/EnrollmentMenu/overview)) and select **Device enrollment**, then on the **Overview** page, make sure **MDM authority** is **Intune**.

- Si **l’autorité de gestion des stratégies** de gestion **des stratégies** de groupe est **Aucune**, cliquez sur l’autorité de gestion des **stratégies** de gestion des Intune.
- Si  l’autorité de gestion des périphériques mobiles est **Microsoft Office 365**, go to **DevicesEnroll**  >  devices and use the **Add MDM authority** dialog on the right to add **Intune MDM** **authority (the Add MDM Authority** dialog is only available if the **MDM Authority** is set to Microsoft Office 365).

## <a name="2-verify-azure-ad-is-enabled-for-joining-computers"></a>2. Vérifiez que Azure AD est activé pour joindre des ordinateurs

1. Go to the Centre d'administration Microsoft 365 at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> and select **Azure Active Directory** (select Show all if Azure Active Directory is not visible) in the **Admin centers** list. 

2. Dans le **Azure Active Directory d’administration**, **Azure Active Directory, choisissez** Appareils, puis **Paramètres de l’appareil**.

3. **VerifyUsers peut joindre des appareils Azure AD** est activé 

    1. Pour activer tous les utilisateurs, définissez-le sur **Tous**.

    2. Pour activer des utilisateurs spécifiques, **définissez-le sur Sélectionné** pour activer un groupe spécifique d’utilisateurs.

        - Ajoutez les utilisateurs de domaine souhaités synchronisés Azure AD à un [groupe de sécurité](../admin/create-groups/create-groups.md).

        - **Sélectionnez Sélectionner des groupes** pour activer l’étendue de l’utilisateur MDM pour ce groupe de sécurité.

## <a name="3-verify-azure-ad-is-enabled-for-mdm"></a>3. Vérifiez que Azure AD est activé pour la gestion des données de gestion des données

1. Go to the Centre d'administration Microsoft 365 at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> and select **Endpoint Management** (select **Show all** if **Endpoint Manager** is not visible)

2. Dans le **Microsoft Endpoint Manager d’administration**, allez sur **Appareils** >  **Windows** >  **Windows Inscription** >  **automatique**.

3. Vérifiez que l’étendue de l’utilisateur mdm est activée.

    1. Pour inscrire tous les ordinateurs, définissez-le sur Tous pour inscrire automatiquement tous les ordinateurs utilisateur qui sont joints à Azure AD et aux nouveaux ordinateurs lorsque les utilisateurs ajoutent un compte de travail à Windows.
  
    2. Définir sur **Some pour** inscrire les ordinateurs d’un groupe spécifique d’utilisateurs.
  
        -  Ajoutez les utilisateurs de domaine souhaités synchronisés Azure AD à un [groupe de sécurité](/admin/create-groups/create-groups.md).
  
       -  **Sélectionnez Sélectionner des groupes** pour activer l’étendue de l’utilisateur MDM pour ce groupe de sécurité.

## <a name="4-create-the-required-resources"></a>4. Créer les ressources requises 

L’utilisation de l’cmdlet [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) trouvée dans le module [SecMgmt](https://www.powershellgallery.com/packages/SecMgmt) PowerShell a simplifié l’utilisation des tâches requises pour configurer la jointage de [Azure AD](/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join) hybride. Lorsque vous voquez cette cmdlet, elle crée et configure le point de connexion de service et la stratégie de groupe requis.

Vous pouvez installer ce module en invoquant les éléments suivants à partir d’une instance de PowerShell :

```powershell
Install-Module SecMgmt
```

> [!IMPORTANT]
> Installez ce module sur le serveur Windows exécutant Azure AD Connecter.

Pour créer le point de connexion de service et la stratégie de groupe requis, vous allez appeler l’cmdlet  [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) . Vous aurez besoin de vos informations d Microsoft 365 Business Premium d’administrateur global lors de l’effectuer. Lorsque vous êtes prêt à créer les ressources,  invoke the following:

```powershell
PS C:\> Connect-SecMgmtAccount
PS C:\> Initialize-SecMgmtHybirdDeviceEnrollment -GroupPolicyDisplayName 'Device Management'
```

La première commande établit une connexion avec le cloud Microsoft et, lorsque vous y êtes invité, spécifiez vos informations d’Microsoft 365 Business Premium d’administrateur général.

## <a name="5-link-the-group-policy"></a>5. Lier le stratégie de groupe

1. Dans la console stratégie de groupe Management Console (GPMC), cliquez avec le bouton droit sur l’emplacement où vous souhaitez lier la stratégie et sélectionnez Lier un *GPO existant...* dans le menu contextique.

2. Sélectionnez la stratégie créée à l’étape ci-dessus, puis cliquez sur **OK**.

## <a name="get-the-latest-administrative-templates"></a>Obtenir les derniers modèles d’administration

Si vous ne voyez pas la stratégie Activer l’inscription **mdm** automatique à l’aide des informations d’identification Azure AD par défaut, cela peut être dû au fait que vous n’avez pas installé ADMX pour Windows 10, version 1803 ou ultérieure. Pour résoudre le problème, suivez les étapes suivantes (Remarque : la dernière version de MDM.admx est à compatibilité avec l’arrière) :

1. Téléchargement : [Modèles d’administration (.admx) pour Windows 10 mise à jour d’octobre 2020 (20H2)](https://www.microsoft.com/download/102157).

2. Installez le package sur un contrôleur de domaine.

3. Accédez au dossier en fonction de la version des modèles d’administration : **C:\Program Files (x86)\Microsoft stratégie de groupe\Windows 10 Octobre 2020 (20H2)**.

4. Renommons **le dossier Définitions de stratégie dans** le chemin d’accès ci-dessus **en PolicyDefinitions**.

5. Copiez **le dossier PolicyDefinitions** dans votre partage SYSVOL, par défaut situé à l’emplacement .`C:\Windows\SYSVOL\domain\Policies`

   Si vous envisagez d’utiliser un magasin central de stratégies pour l’ensemble de votre domaine, ajoutez-y le contenu de PolicyDefinitions.

6. Si vous avez plusieurs contrôleurs de domaine, attendez que SYSVOL réplique pour que les stratégies soient disponibles. Cette procédure fonctionne également pour toute version ultérieure des modèles d’administration.

À ce stade, vous devriez être en mesure de voir la stratégie Activer l’inscription **mdm** automatique à l’aide des informations d’Azure AD disponibles.

## <a name="related-content"></a>Contenu connexe

- [Synchroniser les utilisateurs de domaine avec Microsoft 365](../admin/setup/manage-domain-users.md)(article)\

- [Créer un groupe dans le Centre d’administration](../admin/create-groups/create-groups.md) (article)\

- [Didacticiel : Configurer la joint Azure Active Directory hybride pour les domaines gérés](/azure/active-directory/devices/hybrid-azuread-join-managed-domains) (article)

- [10 principales façons de sécuriser les Microsoft 365 pour les plans d’entreprise](../admin/security-and-compliance/secure-your-business-data.md)
