---
title: Résoudre les Windows d’installation de PC Cloud 365 Business
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- MET150
- MOE150
description: Découvrez comment résoudre les problèmes d’installation pour Windows 365 Business Cloud.
ms.date: 08/13/2021
ms.openlocfilehash: cae971187e188e6213242481b9cfaeb7dc21c7f2
ms.sourcegitcommit: 7e7effd8ef4ffe75cdee7bb8517fec8608e4c230
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2021
ms.locfileid: "59444126"
---
# <a name="troubleshoot-windows-365-business-cloud-pc-setup-issues"></a>Résoudre les Windows d’installation de PC Cloud 365 Business

Si vos utilisateurs obtiennent l’erreur « Le programme d’installation a échoué » ou si le programme d’installation prend plus de 90 minutes après leur avoir attribué une licence, utilisez les étapes de cet article pour résoudre le problème.

> [!IMPORTANT]
> Vous devez être un administrateur global pour effectuer la plupart des tâches décrites dans cet article. Si d’autres rôles d’administrateur peuvent être utilisés pour une procédure spécifique, ils sont indiqués avant la procédure. Si vous n’êtes pas autorisé à vous connecter à des composants du portail Azure ou à y accéder, contactez votre administrateur informatique. Pour plus d’informations sur les règles Azure, voir rôles intégrés [Azure AD.](/azure/active-directory/roles/permissions-reference) Pour en savoir plus sur le portail Azure, consultez la vue [d’ensemble du portail Azure.](/azure/azure-portal/azure-portal-overview)

## <a name="step-1-verify-azure-ad-device-settings"></a>Étape 1. Vérifier les paramètres de l’appareil Azure AD

**Assurez-vous que les utilisateurs peuvent joindre des appareils à Azure AD** est définie sur **Tous.**

1. Connectez-vous au portail Microsoft Azure sur [https://portal.azure.com/](https://go.microsoft.com/fwlink/p/?linkid=516942) .
2. Sous **Gérer Azure Active Directory,** sélectionnez **Afficher.**
3. Dans le navigation de gauche, sous **Gérer,** sélectionnez **Appareils,** puis sélectionnez **Paramètres de l’appareil.**
4. Si **les utilisateurs peuvent joindre des appareils à Azure AD** n’est pas définie sur **Tout,** sélectionnez **Tout,** puis **sélectionnez Enregistrer**.
5. Allez à [l’étape 2. Vérifiez que le compte Windows système d’utilisateur permanent BPRT 365 est actif.](#step-2-verify-that-the-windows-365-bprt-permanent-user-system-account-is-active)

Assurez-vous que le nombre **maximal** d’appareils par utilisateur est suffisamment élevé pour que les PC Cloud que vous essayez d’installer soient affectés aux utilisateurs désignés.

1. Connectez-vous au portail Microsoft Azure sur https://portal.azure.com/ .
2. Sous **Gérer Azure Active Directory,** sélectionnez **Afficher.**
3. Dans le navigation de gauche, sous **Gérer,** sélectionnez **Appareils,** puis sélectionnez **Paramètres de l’appareil.**
4. Pour **le nombre maximal d’appareils par utilisateur,** entrez la valeur.
5. Si vous avez apporté des modifications, sélectionnez **Enregistrer.**

## <a name="step-2-verify-that-the-windows-365-bprt-permanent-user-system-account-is-active"></a>Étape 2. Vérifier que le compte Windows système d’utilisateur permanent BPRT 365 est actif

La première fois qu’une licence Windows 365 est attribuée dans votre organisation, un compte système appelé utilisateur permanent **WINDOWS 365 BPRT** est automatiquement créé dans Azure AD. Ne supprimez pas ce compte et n’a modifiez pas ce compte (par exemple, en modifiant le nom ou l’UPN). Si le compte système est modifié ou supprimé, l’installation échoue. Ce compte système garantit un processus de configuration fluide et n’a pas de fonctionnalités d’écriture ni d’accès à votre organisation au-delà des fonctionnalités de service étendues de Windows 365 Business. Si vous supprimez ou modifiez ce compte système, vous devez vous connecter à windows365.microsoft.com avec n’importe quel compte 365 Business avec une licence Windows 365 Business et attendre 12 heures pour que le jeton s’actualise.

Pour vous assurer que le compte Windows utilisateur permanent BPRT 365 est actif dans Azure AD, utilisez les étapes suivantes.

1. Dans le portail Azure, go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=516942" target="_blank">Azure Active Directory Overview</a> page.
2. Dans le navigation de gauche, sous **Gérer,** sélectionnez **Utilisateurs.**
3. Dans la zone de recherche, tapez Windows utilisateur permanent **BPRT 365,** puis appuyez sur **Entrée**.
4. Si le Windows système d’utilisateur permanent BPRT 365 est présent, allez à [l’étape 3. Vérifiez que l' mba basée sur l’appareil est désactivée.](#step-3-verify-that-device-based-mfa-is-turned-off)
5. Si le compte système d’utilisateur permanent Windows 365 BPRT est manquant ou si des modifications lui ont été apportées (par exemple, réinitialisation du mot de passe, modification de propriété, attribution ou désins attribution d’une licence, etc.), connectez-vous à windows365.microsoft.com avec tout compte titulaire d’une licence Windows 365 Business attribuée après 12 heures. Un nouvel Windows utilisateur permanent BPRT 365 sera généré. Une fois le jeton régénéré, allez directement à [l’étape 6. Réinitialisez vos PC cloud.](#step-6-reset-your-cloud-pcs)

## <a name="step-3-verify-that-device-based-mfa-is-turned-off"></a>Étape 3. Vérifier que l’mfmf basée sur l’appareil est désactivée

Il est possible que votre organisation soit configurée de sorte que l’authentification multifacteur (MFA) soit requise pour joindre des appareils avec Azure AD. Si c’est le cas, vous devez désactiver ce paramètre. Pour vous assurer que la fonctionnalité Exiger l’authentification **multifacteur** pour inscrire ou joindre des appareils avec Azure AD est définie sur **Non,** utilisez les étapes suivantes.

1. Dans le portail Azure, go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=516942" target="_blank">Azure Active Directory Overview</a> page.
2. Dans le navigation de gauche, sous **Gérer,** sélectionnez **Appareils,** puis sélectionnez **Paramètres de l’appareil.**
3. Si **vous avez besoin de l’authentification multifacteur** pour inscrire ou joindre des appareils avec Azure AD est définie sur **Oui,** sélectionnez **Non,** puis sélectionnez **Enregistrer**.
4. Allez à [l’étape 4. Assurez-vous que l' mappe MFA ne bloque pas l’installation.](#step-4-make-sure-that-mfa-doesnt-block-setup)

## <a name="step-4-make-sure-that-mfa-doesnt-block-setup"></a>Étape 4. Assurez-vous que l' mappe MFA ne bloque pas l’installation

Si vous n’avez pas de licence Azure AD Premium P1 qui inclut l’accès conditionnel, accédez à [l’étape 5. Assurez-vous que la configuration de l’autorité mdm est correctement définie.](#step-5-make-sure-mdm-authority-configuration-is-set-up-correctly) Si vous ne savez pas si votre abonnement inclut Azure AD Premium P1, voir [de quel abonnement ai-je besoin ?](../admin-overview/what-subscription-do-i-have.md)

Si vous avez une licence Azure AD Premium P1 qui inclut l’accès conditionnel, sélectionnez un utilisateur pour être le premier utilisateur à se connecter à la page d’accueil Windows 365 une fois que vous avez terminé les étapes restantes de cet [https://windows365.microsoft.com](https://windows365.microsoft.com) article. Assurez-vous qu’il n’existe aucune stratégie d’accès conditionnel MFA pour ce premier utilisateur. L’mf doit rester désactivée pendant toutes les tentatives d’installation. Une fois que tous les PC Cloud ont été correctement configurer au sein de votre organisation, vous pouvez activer l’mfmf pour cet utilisateur. Pour en savoir plus sur les stratégies d’accès conditionnel, consultez [la Azure Active Directory .](/azure/active-directory/conditional-access/overview)

Pour vérifier les stratégies d’accès conditionnel, utilisez les étapes suivantes.

1. Dans le portail Azure, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2169290" target="_blank">Stratégies d’accès conditionnel.</a>
2. Si aucune stratégie n’est répertoriée, continuez à [l’étape 5. Assurez-vous que la configuration de l’autorité mdm est correctement définie.](#step-5-make-sure-mdm-authority-configuration-is-set-up-correctly)
3. Si des stratégies sont répertoriées sur la page, sélectionnez un nom de stratégie.
4. Dans la section **Contrôles** d’accès, sous **Accorder,** s’il indique « 0 contrôles sélectionnés », revenir à la liste des stratégies et sélectionner la stratégie suivante. Dans le cas contraire, continuez à l’étape 5.
5. Dans la section **Contrôles** d’accès, sous **Accorder,** s’il indique que plusieurs contrôles sont sélectionnés, sélectionnez le lien **_n_ contrôles** sélectionnés.
6. Dans le volet droit, si l’authentification **multifacteur** est sélectionnée, cochez la case, puis sélectionnez **le bouton** Sélectionner.
   > [!TIP]
   > Vous pouvez également exclure le premier utilisateur de la stratégie. Pour savoir comment faire, voir Gérer les [utilisateurs exclus des stratégies d’accès conditionnel.](/azure/active-directory/governance/conditional-access-exclusion)
7. Répétez les étapes 3 à 6 jusqu’à ce que vous avez supprimé l’mfmf pour toutes les stratégies d’accès conditionnel.
8. Allez à [l’étape 5. Assurez-vous que la configuration de l’autorité mdm est correctement définie.](#step-5-make-sure-mdm-authority-configuration-is-set-up-correctly)

## <a name="step-5-make-sure-mdm-authority-configuration-is-set-up-correctly"></a>Étape 5. Assurez-vous que la configuration de l’autorité mdm est correctement définie

Si vous avez apporté des modifications en fonction des étapes 1 à 4 précédentes de cet article, il est possible que la cause première soit maintenant résolue. Pour vérifier que le problème est résolu, allez à [l’étape 6. Réinitialisez vos PC cloud.](#step-6-reset-your-cloud-pcs)

Si vous n’avez pas apporté de modifications pour les étapes 1 à 4, il est possible que l’échec de l’installation soit dû à la configuration de l’autorité de gestion des stratégies de groupe dans votre environnement. Si c’est le cas, vous avez deux chemins d’accès à suivre, selon que vous envisagez d’utiliser Microsoft Intune pour gérer les PC cloud.

- Si vous utilisez ou prévoyez d’utiliser Microsoft Intune pour vos PC Cloud, suivez les étapes du chemin d’accès A : Assurez-vous que les paramètres de mobilité (MDM et MAM) sont correctement [configurés.](#path-a-use-microsoft-intune-to-manage-your-cloud-pcs)
- Si vous ne prévoyez pas d’utiliser Microsoft Intune pour gérer vos PC Cloud, suivez les étapes du chemin d’accès B : Désactiver l’inscription [mdm automatique.](#path-b-turn-off-automatic-mdm-enrollment)

### <a name="path-a-use-microsoft-intune-to-manage-your-cloud-pcs"></a>Chemin D’accès A. Utilisez Microsoft Intune pour gérer vos PC Cloud

Si vous utilisez déjà Microsoft Intune ou prévoyez de l’utiliser pour gérer vos PC cloud Windows 365, assurez-vous que vos paramètres de mobilité **(MDM** et MAM) dans Azure AD sont correctement configurés.

1. Dans le portail Azure, go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=516942" target="_blank">Azure Active Directory Overview</a> page.
2. Dans le navigation de gauche, sous **Gérer,** sélectionnez **Mobilité (MDM et MAM),** puis sélectionnez **Microsoft Intune**.
3. Dans la page **Configurer,** en de côté de l’étendue **utilisateur MDM,** sélectionnez **Tout** ou **partie,** puis **sélectionnez Enregistrer**.
4. Dans le navigation de gauche, sous **Gérer,** sélectionnez **Mobilité (MDM** et MAM), sélectionnez Microsoft Intune **inscription,** puis répétez l’étape 3.

Une licence Intune doit être attribuée aux utilisateurs affectés à un PC cloud. Il n’est pas nécessaire d’attribuer une licence Intune au compte système CloudPCBPRT.

> [!IMPORTANT]
> Pour attribuer des licences, vous devez être un administrateur global ou un administrateur de licences, ou avoir un rôle avec des autorisations de licence.

1. Dans le centre [Microsoft Endpoint Manager' administration,](https://go.microsoft.com/fwlink/p/?linkid=2169290)sélectionnez **Utilisateurs**  >  **tous les utilisateurs.**
2. Dans la **liste Tous les utilisateurs,** sélectionnez un utilisateur.
3. Dans la page **Profil utilisateur,** sélectionnez **Licences.**
4. Dans la page **Licences,** sélectionnez **Affectations.**
5. Recherchez **Intune,** cochez la case, puis sélectionnez **Enregistrer.** Le compte d’utilisateur dispose désormais des autorisations nécessaires pour utiliser le service et inscrire des appareils.
6. Allez à [l’étape 6. Réinitialisez vos PC cloud.](#step-6-reset-your-cloud-pcs)

### <a name="path-b-turn-off-automatic-mdm-enrollment"></a>Chemin D’accès B. Désactiver l’inscription mdm automatique

Si vous ne prévoyez pas d’utiliser Microsoft Intune pour la gestion de votre PC Cloud, vous devez désactiver l’inscription mdM automatique.

> [!IMPORTANT]
> Si vous n’êtes pas l’administrateur DE LAM, n’utilisez aucune des procédures suivantes sans avoir consulté au départ votre administrateur informatique. Suivez uniquement ces procédures si les PC cloud ne sont pas en cours de mise en place. Toute modification de configuration peut avoir un impact sur votre environnement de gestion. Si vous avez besoin d’aide, [contactez le support Intune.](/mem/get-support)

#### <a name="use-the-azure-ad-portal-to-turn-off-automatic-intune-enrollment"></a>Utiliser le portail Azure AD pour désactiver l’inscription Automatique à Intune

1. Dans le portail Azure, go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=516942" target="_blank">Azure Active Directory Overview</a> page.
2. Dans le navigation de gauche, sous **Gérer,** sélectionnez **Mobilité (MDM et MAM),** puis sélectionnez **Microsoft Intune**.
3. Dans la page **Configurer,** vous verrez l’un des deux éléments. Si vous avez un abonnement Azure AD Premium, sélectionnez **Aucun** en de côté de l’étendue utilisateur MDM, puis **sélectionnez Enregistrer**. Si vous n’avez pas d’abonnement Azure AD Premium, **sélectionnez Désactiver.**
4. Dans le navigation de gauche, sous **Gérer,** sélectionnez **Mobilité (MDM** et MAM), sélectionnez Microsoft Intune **inscription,** puis répétez l’étape 3.
5. Allez à [l’étape 6. Réinitialisez vos PC cloud.](#step-6-reset-your-cloud-pcs)


## <a name="step-6-reset-your-cloud-pcs"></a>Étape 6. Réinitialiser vos PC cloud

Une fois que vous avez terminé les étapes de résolution des problèmes de cet article, vos utilisateurs doivent redémarrer leur configuration de PC cloud. 

Si vous avez terminé [l’étape 3. Vérifiez que l'](#step-3-verify-that-device-based-mfa-is-turned-off)mbam basé sur l’appareil est désactivé et attendez au moins dix minutes que les modifications prennent effet avant de continuer. Assurez-vous que l’utilisateur que vous avez exclu de l’mfmf est le premier utilisateur à se connecter à la [page d’Windows 365.](https://windows365.microsoft.com)

Indiquez à tous les utilisateurs de PC cloud qui ont vu l’erreur « Échec du programme d’installation » d’utiliser les étapes suivantes pour réinitialiser leurs PC Cloud.

1. Sur la [page d Windows 365,](https://windows365.microsoft.com)sélectionnez l’icône d’engrenage pour n’importe quel PC Cloud dont l’état est « Échec de l’installation », puis sélectionnez Réinitialiser.  Cette action redémarre le processus d’installation.
2. Après la réinitialisation, si l’erreur « Échec du programme d’installation » s’affiche toujours et que vous avez ignoré [l’étape 5. Assurez-vous que la configuration de](#step-5-make-sure-mdm-authority-configuration-is-set-up-correctly)l’autorité MDM est correctement définie, terminez cette étape, puis réinitialisez à nouveau le CloudPC. Dans le cas contraire, dans le navigation gauche, sélectionnez Nouvelle demande **de support** pour ouvrir un ticket de support.
