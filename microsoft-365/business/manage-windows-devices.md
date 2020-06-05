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
ms.openlocfilehash: 857651081fb10856d28dd419333ebef655388407
ms.sourcegitcommit: e6e704cbd9a50fc7db1e6a0cf5d3f8c6cbb94363
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "44564934"
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

Accédez à portal.azure.com et dans la partie supérieure de la page recherche de Intune.
Sur la page Microsoft Intune, sélectionnez l’option d’enregistrement de l' **appareil** et, dans la page de **vue d’ensemble** , vérifiez que l' **autorité MDM** est **Intune**.

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

## <a name="4-set-up-service-connection-point-scp"></a>4. configurer le point de connexion de service (SCP)

Ces étapes sont simplifiées à partir de la configuration de la [jointure Azure ad hybride](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join). Pour effectuer les étapes, vous devez utiliser Azure AD Connect et vos mots de passe d’administrateur global Microsoft 365 Business Premium et d’administrateur Active Directory.

1.  Démarrez Azure AD Connect, puis sélectionnez **configurer**.
2.  Sur la page **tâches supplémentaires** , sélectionnez **configurer les options des appareils**, puis **suivant**.
3.  Sur la page **vue d’ensemble** , sélectionnez **suivant**.
4.  Sur la page **connexion à Azure ad** , entrez les informations d’identification d’un administrateur général pour Microsoft 365 Business Premium.
5.  Sur la page **options d’appareil** , sélectionnez configurer une **jointure Azure ad hybride**, puis cliquez sur **suivant**.
6.  Sur la page **SCP** , pour chaque forêt dans laquelle vous souhaitez qu’Azure ad Connect configure le SCP, effectuez les étapes suivantes, puis cliquez sur **suivant**:
    - Activez la case à cocher en regard du nom de la forêt. La forêt doit être le nom de votre domaine AD.
    - Dans la colonne **service d’authentification** , ouvrez la liste déroulante et sélectionnez nom de domaine correspondant (il ne doit y avoir qu’une seule option).
    - Sélectionnez **Ajouter** pour entrer les informations d’identification d’administrateur de domaine.  
7.  Sur la page **système d’exploitation des appareils** , sélectionnez appareils joints à un domaine Windows 10 ou version ultérieure uniquement.
8.  Sur la page **prêt à configurer** , sélectionnez **configurer**.
9.  Sur la page **Configuration terminée** , sélectionnez **quitter**.


## <a name="5-create-a-gpo-for-intune-enrollment--admx-method"></a>5. créer un objet de stratégie de groupe pour l’enregistrement Intune – ADMX, méthode

Utilisant. Fichier de modèle ADMX.

1.  Connectez-vous à AD Server, recherchez et ouvrez les outils du **Gestionnaire de serveur**  >  **Tools**  >  **gestion des stratégies de groupe**.
2.  Sélectionnez votre nom de domaine sous **domaines** , puis cliquez avec le bouton droit sur **objets de stratégie de groupe** pour sélectionner **nouveau**.
3.  Donnez un nom au nouvel objet de stratégie de groupe, par exemple «*Cloud_Enrollment*», puis cliquez sur **OK**.
4.  Cliquez avec le bouton droit sur le nouvel objet GPO sous **objets de stratégie de groupe** et sélectionnez **modifier**.
5.  Dans l' **éditeur de gestion des stratégies de groupe**, accédez à stratégies de configuration de l' **ordinateur**  >  **Policies**  >  **modèles d’administration**  >  **Windows Components**  >  **MDM**.
6. Cliquez avec le bouton droit sur **activer l’enregistrement MDM automatique à l’aide des informations d’identification Azure ad par défaut** , puis sélectionnez **activé**  >  **OK**. Fermez la fenêtre de l’éditeur.

> [!IMPORTANT]
> Si vous ne voyez pas la stratégie **activer l’enregistrement MDM automatique à l’aide des informations d’identification Azure ad par défaut**, reportez-vous à [la rubrique obtenir les derniers modèles d’administration](#get-the-latest-administrative-templates).

## <a name="6-deploy-the-group-policy"></a>6. déployer la stratégie de groupe

1.  Dans le gestionnaire de serveur, sous **domaines** > objets de stratégie de groupe, sélectionnez l’objet GPO de l’étape 3 ci-dessus, par exemple « Cloud_Enrollment ».
2.  Sélectionnez l’onglet **étendue** de votre objet de stratégie de groupe.
3.  Dans l’onglet étendue de l’objet de stratégie de groupe, cliquez avec le bouton droit sur le lien vers le domaine sous **liens**.
4.  Sélectionnez **appliqué** pour déployer l’objet de stratégie de groupe, puis **OK** dans l’écran de confirmation.

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

