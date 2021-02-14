---
title: Activer la gestion des appareils Windows 10 joints à un domaine par Microsoft 365 pour les entreprises
f1.keywords:
- CSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Découvrez comment activer Microsoft 365 pour protéger les appareils Windows 10 locaux joints à Active Directory en quelques étapes.
ms.openlocfilehash: 6275c6c4be9cd9631ab095f8b0e1b39683022bb2
ms.sourcegitcommit: d988faa292c2661ffea43c7161aef92b2b4b99bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "46560840"
---
# <a name="enable-domain-joined-windows-10-devices-to-be-managed-by-microsoft-365-business-premium"></a>Activer la gestion des appareils Windows 10 joints à un domaine par Microsoft 365 Business Premium

Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 Business Premium pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale.
Pour configurer cette protection, vous pouvez implémenter des appareils **joints à Azure AD hybride.** Ces appareils sont joints à votre annuaire Active Directory local et à azure Active Directory.

Cette vidéo décrit les étapes à suivre pour la configurer pour le scénario le plus courant, qui est également détaillée dans les étapes qui suivent.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3C9hO]
  

## <a name="before-you-get-started-make-sure-you-complete-these-steps"></a>Avant de commencer, veillez à effectuer les étapes suivantes :
- Synchronisez les utilisateurs avec Azure AD avec Azure AD Connect.
- Synchronisez l’unité d’organisation Azure AD Connect.
- Assurez-vous que tous les utilisateurs de domaine que vous synchronisez ont des licences pour Microsoft 365 Business Premium.

Pour obtenir la procédure [à suivre, consultez](manage-domain-users.md) Synchroniser les utilisateurs de domaine avec Microsoft.

## <a name="1-verify-mdm-authority-in-intune"></a>1. Vérifier l’autorité mdm dans Intune

Go to [Endpoint Manager](https://endpoint.microsoft.com/#blade/Microsoft_Intune_Enrollment/EnrollmentMenu/overview) and on the Microsoft Intune page, select **Device enrollment**, then on the **Overview** page, make sure **MDM authority** is **Intune**.

- Si **l’autorité MDM** est **Aucune,** cliquez sur l’autorité **DE GESTION** pour la définir sur **Intune**.
- Si  l’autorité de gestion des périphériques mobiles est Microsoft Office **365**, allez sur Périphériques Inscrire des appareils et utilisez la boîte de dialogue Ajouter une autorité de gestion des appareils mobiles sur le droit pour ajouter l’autorité de gestion des appareils mobiles  >   **Intune** (la boîte de dialogue Ajouter une autorité **MDM** est disponible uniquement si l’autorité **mdm** est définie sur Microsoft Office 365). 

## <a name="2-verify-azure-ad-is-enabled-for-joining-computers"></a>2. Vérifiez qu’Azure AD est activé pour joindre des ordinateurs

- Go to the admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>  and select Azure Active **Directory** (select Show all if Azure Active Directory is not visible) in the **Admin centers** list. 
- Dans le **Centre d’administration Azure Active Directory,** allez à **Azure Active Directory,** choisissez Appareils, puis **Paramètres de l’appareil.** 
- Vérifier **que les utilisateurs peuvent joindre des appareils à Azure AD** est activé 
    1. Pour activer tous les utilisateurs, définissez-le sur **Tous.**
    2. Pour activer des utilisateurs spécifiques, **définissez-le sur Sélectionné** pour activer un groupe spécifique d’utilisateurs.
        - Ajoutez les utilisateurs de domaine souhaités synchronisés dans Azure AD à un [groupe de sécurité.](../admin/create-groups/create-groups.md)
        - Choisissez **Sélectionner des groupes** pour activer l’étendue de l’utilisateur MDM pour ce groupe de sécurité.

## <a name="3-verify-azure-ad-is-enabled-for-mdm"></a>3. Vérifier qu’Azure AD est activé pour la gestion des données de gestion des données

- Go to the admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>  and select **select Endpoint Managemen** t (select **Show all** if **Endpoint Manager** is not visible)
- Dans le Centre **d’administration Microsoft Endpoint Manager,** allez sur **Appareils**  >    >  **Windows Inscription** automatique  >  .
- Vérifiez que l’étendue de l’utilisateur mdm est activée.

    1. Pour inscrire tous les  ordinateurs, définissez-le sur Tous pour inscrire automatiquement tous les ordinateurs utilisateur qui sont joints à Azure AD et les nouveaux ordinateurs lorsque les utilisateurs ajoutent un compte de travail à Windows.
    2. Définir sur **Some pour** inscrire les ordinateurs d’un groupe spécifique d’utilisateurs.
        -  Ajoutez les utilisateurs de domaine souhaités synchronisés dans Azure AD à un [groupe de sécurité.](../admin/create-groups/create-groups.md)
        -  Choisissez **Sélectionner des groupes** pour activer l’étendue de l’utilisateur MDM pour ce groupe de sécurité.

## <a name="4-create-the-required-resources"></a>4. Créer les ressources requises 

L’utilisation de l’cmdlet [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) trouvée dans le module [SecMgmt](https://www.powershellgallery.com/packages/SecMgmt) PowerShell simplifie l’réalisation des tâches requises pour configurer la jointage [Azure AD](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join) hybride. Lorsque vous voquez cette cmdlet, elle crée et configure le point de connexion de service et la stratégie de groupe requis.

Vous pouvez installer ce module en invoquant les éléments suivants à partir d’une instance de PowerShell :

```powershell
Install-Module SecMgmt
```

> [!IMPORTANT]
> Il est recommandé d’installer ce module sur le serveur Windows exécutant Azure AD Connect.

Pour créer le point de connexion de service et la stratégie de groupe requis, vous allez appeler l’cmdlet [Initialize-SecMgmtHybirdDeviceEnrollment.](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) Vous aurez besoin de vos informations d’identification d’administrateur global Microsoft 365 Business Premium pour effectuer cette tâche. Lorsque vous êtes prêt à créer les ressources, invoke the following:

```powershell
PS C:\> Connect-SecMgmtAccount
PS C:\> Initialize-SecMgmtHybirdDeviceEnrollment -GroupPolicyDisplayName 'Device Management'
```

La première commande établit une connexion avec le cloud Microsoft et, lorsque vous y êtes invité, spécifiez vos informations d’identification d’administrateur général Microsoft 365 Business Premium.

## <a name="5-link-the-group-policy"></a>5. Lier la stratégie de groupe

1. Dans la Console de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’emplacement où vous souhaitez lier la stratégie et sélectionnez Lier un *GPO existant...* dans le menu contextique.
2. Sélectionnez la stratégie créée à l’étape ci-dessus, puis cliquez sur **OK.**

## <a name="get-the-latest-administrative-templates"></a>Obtenir les derniers modèles d’administration

Si vous ne voyez pas la stratégie Activer l’inscription mdm automatique à l’aide des informations d’identification **Azure AD** par défaut, c’est peut-être parce que vous n’avez pas installé ADMX pour Windows 10, version 1803, version 1809 ou version 1903. Pour résoudre le problème, suivez les étapes suivantes (Remarque : la dernière version de MDM.admx est à compatibilité avec l’arrière) :

1.  Téléchargement : Modèles d’administration (.admx) pour la mise à jour de mai [2019 de Windows 10 (1903)](https://www.microsoft.com/download/details.aspx?id=58495&WT.mc_id=rss_alldownloads_all).
2.  Installez le package sur le contrôleur de domaine principal (PDC).
3.  Naviguez, en fonction de la version vers le dossier : **C:\Program Files (x86)\Microsoft Group Policy\Windows 10 May 2019 Update (1903) v3**.
4.  Renommons le **dossier Définitions de stratégie dans** le chemin d’accès ci-dessus à **PolicyDefinitions**.
5.  Copiez **le dossier PolicyDefinitions** **dans C:\Windows\SYSVOL\domain\Policies**. 
    -   Si vous envisagez d’utiliser un magasin central de stratégies pour l’ensemble de votre domaine, ajoutez le contenu de PolicyDefinitions à cet élément.
6.  Redémarrez le contrôleur de domaine principal pour que la stratégie soit disponible. Cette procédure fonctionne également pour n’importe quelle version future.

À ce stade, vous devriez être en mesure de voir la stratégie Activer l’inscription mdm automatique à l’aide des informations d’identification **Azure AD par défaut** disponibles.
