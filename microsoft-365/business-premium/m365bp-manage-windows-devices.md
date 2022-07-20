---
title: Permettre aux appareils Windows 10 reliés à un domaine d'être gérés par Microsoft 365 for business.
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection: ''
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: Découvrez comment activer Microsoft 365 pour protéger les appareils Windows 10 joints à Active Directory en quelques étapes.
ms.openlocfilehash: 427010f073eb86a7fe685335189550cf48ea9549
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893186"
---
# <a name="manage-windows-devices-with-microsoft-365-business-premium"></a>Gérer les appareils Windows avec Microsoft 365 Business Premium

Si votre organisation utilise Windows Server Active Directory localement, vous pouvez configurer Microsoft 365 Business Premium pour protéger vos appareils Windows tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale.

Pour configurer cela, implémentez **Appareils joints Azure AD Hybride**. Ces dispositifs sont joints à la fois à votre Active Directory sur site et à votre Active Directory Azure.

> [!NOTE]
> Microsoft Defender pour les PME est déployée pour les clients Microsoft 365 Business Premium, à compter du 1er mars 2022. Cette offre fournit des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender for Business](../security/defender-business/mdb-overview.md).

## <a name="watch-configure-hybrid-azure-active-directory-join"></a>Regarder : Configurer la jonction Azure Active Directory hybride

Cette vidéo décrit les étapes à suivre pour configurer ce scénario pour le scénario le plus courant, qui est également détaillé dans les étapes qui suivent.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3C9hO]
  
## <a name="before-you-begin"></a>Avant de commencer

- Synchronisez les utilisateurs avec Azure AD avec Azure AD Connecter.
- Effectuez Azure AD Connecter synchronisation de l’unité d’organisation (UO).
- Assurez-vous que tous les utilisateurs du domaine que vous synchronisez disposent de licences pour Microsoft 365 Business Premium.

Consultez [Synchroniser les utilisateurs de domaine pour Microsoft 365](../admin/setup/manage-domain-users.md) pour connaître les étapes à suivre.

## <a name="possible-device-actions-and-statuses"></a>Actions et statuts d’appareil possibles
  
![In the Device actions list, you can see the Devices states.](./../media/a621c47e-45d9-4e1a-beb9-c03254d40c1d.png)

Les appareils et leurs actions associées peuvent avoir les états suivants :
  
|**État**|**Description**|
|:-----|:-----|
|Géré par Intune  |Géré par Microsoft 365 Business Premium.  |
|Mise hors service en attente  |Microsoft 365 Entreprise s'apprête à supprimer des données d'entreprise de l'appareil.  |
|Mise hors service en cours  |Microsoft 365 Entreprise est en train de supprimer des données d'entreprise de l'appareil.  |
|Échec de la mise hors service  | L'action de suppression des données d'entreprise a échoué.  |
|Mise hors service annulée  |L'action de mise hors service a été annulée.  |
|Réinitialisation en attente  |En attente du rétablissement des paramètres d'usine.  |
|Réinitialisation en cours  |Le rétablissement des paramètres d'usine a démarré.  |
|Échec de la réinitialisation  |Le rétablissement des paramètres d'usine n'a pas pu être effectué.  |
|Réinitialiser annulée  |Le rétablissement des paramètres d'usine a été annulé.  |
|Défectueux  |Cela signifie qu'une action est en attente (ou en cours) mais que l'appareil n'a pas archivé depuis plus de 30 jours.  |
|Suppression en attente  |Une action de suppression est en attente.  |
|Détecté  |Microsoft 365 Entreprise a détecté l'appareil.  |

## <a name="1-verify-mdm-authority-in-intune"></a>1. Vérifier l’autorité MDM dans Intune

Allez dans le centre d'administration de Microsoft Endpoint Manager ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com/#blade/Microsoft_Intune_Enrollment/EnrollmentMenu/overview))) et sélectionnez **Inscription d’appareil**, puis sur la page **Vue d’ensemble**, assurez-vous que **l'autorité MDM** est **Intune**.

- Si **l’autorité MDM** est **Aucune**, cliquez sur **l’autorité MDM** pour la définir sur **Intune**.
- Si **l'autorité MDM** est **Microsoft Office 365**, allez dans **Dispositifs** > **Inscrire des dispositifs** et utilisez la boîte de dialogue **Ajouter une autorité MDM** sur la droite pour ajouter l'autorité **MDM Intune** (la boîte de dialogue **Ajouter une autorité MDM** est uniquement disponible si **l'autorité MDM** est définie sur Microsoft Office 365).

## <a name="2-verify-azure-ad-is-enabled-for-joining-computers"></a>2. Vérifiez que Azure AD est activé pour joindre des ordinateurs

1. Accédez à l’Centre d'administration Microsoft 365 <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> et sélectionnez **Azure Active Directory** (sélectionnez Afficher tout si Azure Active Directory n’est pas visible) dans la liste **des centres d’administration**. 

2. Dans le **centre d’administration Azure Active Directory**, accédez à **Azure Active Directory**, choisissez **Appareils**, puis **Paramètres de l’appareil**.

3. Vérifier que **les utilisateurs peuvent joindre des appareils à Azure AD** est activé. 

    1. Pour activer tous les utilisateurs, définissez sur **Tout**.

    2. Pour activer des utilisateurs spécifiques, affectez la valeur **Sélectionnée** pour activer un groupe spécifique d’utilisateurs.

        - Ajoutez les utilisateurs de domaine souhaités synchronisés dans Azure AD à un [groupe de sécurité](../admin/create-groups/create-groups.md).

        - Choisissez **Sélectionner des groupes** pour activer l’étendue utilisateur MDM pour ce groupe de sécurité.

## <a name="3-verify-azure-ad-is-enabled-for-mdm"></a>3. Vérifiez que Azure AD est activé pour MDM

1. Accédez au centre d'administration Microsoft 365 à l'adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> et sélectionnez **Gestion de point de terminaison** (sélectionnez **Show all** si **Gestion de point de terminaison** n'est pas visible).

2. Dans le **centre d'administration Endpoint Manager**, accédez à **appareils** > **Windows** > **Enregistrement Windows** > **Enregistrement Automatique**.

3. Vérifiez que l’étendue de l’utilisateur MDM est activée.

    1. Pour inscrire tous les ordinateurs, définissez l'option **Tout** pour inscrire automatiquement tous les ordinateurs des utilisateurs qui sont joints à Azure AD et les nouveaux ordinateurs lorsque les utilisateurs ajoutent un compte professionnel à Windows.
  
    2. Définissez sur **Certains** pour inscrire les ordinateurs d’un groupe spécifique d’utilisateurs.
  
        -  Ajoutez les utilisateurs de domaine souhaités synchronisés dans Azure AD à un [groupe de sécurité](/admin/create-groups/create-groups.md).
  
       -  Choisissez **Sélectionner des groupes** pour activer l’étendue utilisateur MDM pour ce groupe de sécurité.

## <a name="4-create-the-required-resources"></a>4. Créer les ressources requises 

L’exécution des tâches requises pour [configurer la jointure hybride Azure AD](/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join) a été simplifiée grâce à l’utilisation de l’applet de commande [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) trouvée dans le module [SecMgmt](https://www.powershellgallery.com/packages/SecMgmt) PowerShell. Lorsque vous invoquez cette cmdlet, elle crée et configure le point de connexion de service et la stratégie de groupe requis.

Vous pouvez installer ce module en appelant ce qui suit à partir d’une instance de PowerShell :

```powershell
Install-Module SecMgmt
```

> [!IMPORTANT]
> Installez ce module sur le serveur Windows exécutant Azure AD Connecter.

Pour créer le point de connexion de service et la stratégie de groupe requis, vous allez appeler l’applet de commande  [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) . Vous aurez besoin de vos informations d’identification d’administrateur général Microsoft 365 Business Premium lors de l’exécution de cette tâche. Lorsque vous êtes prêt à créer les ressources, appelez les éléments suivants :

```powershell
PS C:\> Connect-SecMgmtAccount
PS C:\> Initialize-SecMgmtHybirdDeviceEnrollment -GroupPolicyDisplayName 'Device Management'
```

La première commande établit une connexion avec le cloud Microsoft et, lorsque vous y êtes invité, spécifiez vos informations d’identification d’administrateur général Business Premium Microsoft 365.

## <a name="5-link-the-group-policy"></a>5. Lier le stratégie de groupe

1. Dans la console de gestion stratégie de groupe (GPMC), cliquez avec le bouton droit sur l’emplacement où vous souhaitez lier la stratégie, puis sélectionnez *lier un objet de stratégie de groupe existant...* dans le menu contextuel.

2. Sélectionnez la stratégie créée à l’étape ci-dessus, puis cliquez sur **OK**.

## <a name="get-the-latest-administrative-templates"></a>Téléchargez l’outil de modèles d’administration.

Si vous ne voyez pas la stratégie **Activer l’inscription MDM automatique à l’aide des informations d’identification de Azure AD par défaut**, cela peut être dû au fait qu’ADMX n’est pas installé pour Windows 10, version 1803 ou ultérieure. Pour résoudre le problème, procédez comme suit (Remarque : le dernier fichier MDM.admx est à compatibilité descendante) :

1. Télécharger et installer [Modèles d’administration (.admx) pour Windows 10, mise à jour d’octobre 2020 (20H2)](https://www.microsoft.com/download/102157).

2. Installez le package sur un contrôleur de domaine.

3. Accédez, selon la version des modèles d’administration, au dossier **: C:\Program Files (x86)\Microsoft stratégie de groupe\Windows 10 Mise à jour d’octobre 2020 (20H2).**

4. Renommez le dossier **Définitions** de stratégie dans le chemin ci-dessus en **PolicyDefinitions**.

5. Copiez le dossier **PolicyDefinitions** dans votre partage SYSVOL, par défaut situé à l’emplacement `C:\Windows\SYSVOL\domain\Policies`.

   Si vous envisagez d’utiliser un magasin de stratégies central pour l’ensemble de votre domaine, ajoutez-y le contenu de PolicyDefinitions.

6. Si vous avez plusieurs contrôleurs de domaine, attendez que SYSVOL soit répliqué pour que les stratégies soient disponibles. Cette procédure fonctionne également pour toute version ultérieure des modèles d’administration.

À ce stade, vous devez être en mesure de voir la stratégie **Activer l’inscription MDM automatique à l’aide des informations d’identification Azure AD par défaut disponibles**.

## <a name="related-content"></a>Contenu connexe

- [Synchroniser les utilisateurs de domaine avec Microsoft 365](../admin/setup/manage-domain-users.md)

- [Créer un groupe dans le Centre d’administration](../admin/create-groups/create-groups.md)

- [Tutoriel : Configurer la jointure Azure Active Directory hybride pour les domaines managés](/azure/active-directory/devices/hybrid-azuread-join-managed-domains)

- [Configurer des mots de passe en libre-service](../admin/add-users/let-users-reset-passwords.md)

- [Configurer la gestion des groupes en libre-service](/azure/active-directory/enterprise-users/groups-self-service-management)

- [Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Objectif suivant

[Préparation au déploiement client Office](m365bp-prepare-for-office-client-deployment.md)