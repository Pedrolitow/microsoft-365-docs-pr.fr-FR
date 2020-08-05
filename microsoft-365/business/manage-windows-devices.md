---
title: Activer la gestion des appareils Windows 10 associés à un domaine par Microsoft 365 pour les entreprises
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
description: Découvrez comment permettre à Microsoft 365 de protéger les appareils Windows 10 à annuaire Active Directory joints en quelques étapes seulement.
ms.openlocfilehash: 6275c6c4be9cd9631ab095f8b0e1b39683022bb2
ms.sourcegitcommit: d988faa292c2661ffea43c7161aef92b2b4b99bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "46560840"
---
# <a name="enable-domain-joined-windows-10-devices-to-be-managed-by-microsoft-365-business-premium"></a>Activer la gestion des appareils Windows 10 associés à un domaine par Microsoft 365 Business Premium

Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 Business Premium pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale.
Pour configurer cette protection, vous pouvez implémenter des **appareils joints Azure ad hybrides**. Ces appareils sont joints à votre annuaire Active Directory local et à votre Azure Active Directory.

Cette vidéo décrit la procédure à suivre pour le scénario le plus courant, qui est également détaillée dans les étapes suivantes.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3C9hO]
  

## <a name="before-you-get-started-make-sure-you-complete-these-steps"></a>Avant de commencer, veillez à effectuer les étapes suivantes :
- Synchroniser les utilisateurs vers Azure AD avec Azure AD Connect.
- Exécutez la synchronisation des unités d’organisation Azure AD Connect.
- Assurez-vous que tous les utilisateurs du domaine que vous synchronisez disposent de licences pour Microsoft 365 Business Premium.

Pour plus d’informations, consultez la rubrique [synchroniser les utilisateurs de domaine à Microsoft](manage-domain-users.md) .

## <a name="1-verify-mdm-authority-in-intune"></a>1. vérifier l’autorité MDM dans Intune

Accédez à [Gestionnaire de point de terminaison](https://endpoint.microsoft.com/#blade/Microsoft_Intune_Enrollment/EnrollmentMenu/overview) et sur la page Microsoft Intune, sélectionnez enregistrement de l' **appareil**, puis, dans la page **vue d’ensemble** , vérifiez que l' **autorité MDM** est **Intune**.

- Si l' **autorité MDM** est **None**, cliquez sur l' **autorité MDM** pour la définir sur **Intune**.
- Si l' **autorité MDM** est **Microsoft Office 365**, accédez **à périphériques**d'  >  **inscription** des appareils et utilisez la boîte de dialogue Ajouter une **autorité** MDM sur la droite pour ajouter l’autorité **MDM MDM** (la boîte de dialogue **Ajouter une autorité** MDM est uniquement disponible si l' **autorité MDM** est définie sur Microsoft Office 365).

## <a name="2-verify-azure-ad-is-enabled-for-joining-computers"></a>2. Vérifiez que Azure AD est activé pour la jonction d’ordinateurs

- Accédez au centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> et sélectionnez **Azure Active Directory** (sélectionnez Afficher tout si Azure Active Directory n’est pas visible) dans la liste **centres d’administration** . 
- Dans le **Centre d’administration Azure Active Directory**, accédez à **Azure Active Directory** , sélectionnez **périphériques** , puis paramètres de l' **appareil**.
- Vérifier que**les utilisateurs peuvent joindre des appareils à Azure ad** est activé 
    1. Pour activer tous les utilisateurs, définissez sur **tous**.
    2. Pour activer des utilisateurs spécifiques, définissez sur **sélectionné** pour activer un groupe spécifique d’utilisateurs.
        - Ajoutez les utilisateurs de domaine souhaités synchronisés dans Azure Active Directory à un [groupe de sécurité](../admin/create-groups/create-groups.md).
        - Sélectionnez **Sélectionner les groupes** pour activer l’étendue utilisateur MDM pour ce groupe de sécurité.

## <a name="3-verify-azure-ad-is-enabled-for-mdm"></a>3. Vérifiez que Azure AD est activé pour MDM

- Accédez au centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> et sélectionnez Sélectionner le **point de terminaison Manager**t (sélectionnez **Afficher tout** si le **Gestionnaire de point de terminaison** n’est pas visible).
- Dans le **Centre d’administration du gestionnaire de points de terminaison Microsoft**, accédez à **périphériques**  >  **Windows**  >  **Windows inscriptions**  >  **automatiques**.
- Vérifiez que l’étendue utilisateur MDM est activée.

    1. Pour inscrire tous les ordinateurs, définissez sur **tous** pour inscrire automatiquement tous les ordinateurs des utilisateurs qui sont joints à Azure ad et les nouveaux ordinateurs lorsque les utilisateurs ajoutent un compte professionnel à Windows.
    2. Définissez sur **some** pour inscrire les ordinateurs d’un groupe d’utilisateurs spécifique.
        -  Ajoutez les utilisateurs de domaine souhaités synchronisés dans Azure Active Directory à un [groupe de sécurité](../admin/create-groups/create-groups.md).
        -  Sélectionnez **Sélectionner les groupes** pour activer l’étendue utilisateur MDM pour ce groupe de sécurité.

## <a name="4-create-the-required-resources"></a>4. créer les ressources requises 

L’exécution des tâches requises pour [configurer la jointure Azure ad hybride](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join) a été simplifiée à l’aide de la cmdlet [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) figurant dans le module [SecMgmt](https://www.powershellgallery.com/packages/SecMgmt) PowerShell. Lorsque vous appelez cette applet de commande, celle-ci crée et configure le point de connexion de service et la stratégie de groupe requis.

Vous pouvez installer ce module en appelant les éléments suivants à partir d’une instance de PowerShell :

```powershell
Install-Module SecMgmt
```

> [!IMPORTANT]
> Il est recommandé d’installer ce module sur le serveur Windows exécutant Azure AD Connect.

Pour créer le point de connexion de service et la stratégie de groupe requis, vous devez appeler la cmdlet [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) . Vous aurez besoin de vos informations d’identification d’administrateur global Microsoft 365 Business Premium lorsque vous effectuerez cette tâche. Lorsque vous êtes prêt à créer les ressources, appelez les éléments suivants :

```powershell
PS C:\> Connect-SecMgmtAccount
PS C:\> Initialize-SecMgmtHybirdDeviceEnrollment -GroupPolicyDisplayName 'Device Management'
```

La première commande établira une connexion avec le Cloud Microsoft et, lorsque vous y êtes invité, spécifiez vos informations d’identification d’administrateur global Microsoft 365 Business Premium.

## <a name="5-link-the-group-policy"></a>5. lier la stratégie de groupe

1. Dans la console de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’emplacement auquel vous souhaitez lier la stratégie, puis sélectionnez *lier un objet de stratégie de groupe existant...* dans le menu contextuel.
2. Sélectionnez la stratégie créée à l’étape ci-dessus, puis cliquez sur **OK**.

## <a name="get-the-latest-administrative-templates"></a>Obtenir les derniers modèles d’administration

Si vous ne voyez pas la stratégie **activer l’enregistrement MDM automatique à l’aide des informations d’identification Azure ad par défaut**, il se peut que vous n’ayez pas installé ADMX pour Windows 10, version 1803, version 1809 ou version 1903. Pour résoudre le problème, procédez comme suit (Remarque : la dernière version de MDM. admx est compatible avec les versions antérieures) :

1.  Téléchargement : [modèles d’administration (. admx) pour Windows 10 mai 2019 mise à jour (1903)](https://www.microsoft.com/download/details.aspx?id=58495&WT.mc_id=rss_alldownloads_all).
2.  Installez le package sur le contrôleur de domaine principal (PDC).
3.  Naviguez en fonction de la version du dossier : **C:\Program Files (x86) \Microsoft Group Policy\Windows 10 mai 2019 mise à jour (1903) v3**.
4.  Renommez le dossier des **définitions de stratégie** dans le chemin d’accès ci-dessus en **PolicyDefinitions**.
5.  Copiez le dossier **PolicyDefinitions** dans **C:\Windows\SYSVOL\domain\Policies**. 
    -   Si vous envisagez d’utiliser un magasin de stratégies central pour l’ensemble de votre domaine, ajoutez le contenu de PolicyDefinitions.
6.  Redémarrez le contrôleur de domaine principal pour que la stratégie soit disponible. Cette procédure fonctionnera également pour toute version ultérieure.

À ce stade, vous devriez être en mesure d’afficher la stratégie **activer l’enregistrement MDM automatique à l’aide des informations d’identification Azure ad par défaut** disponibles.
