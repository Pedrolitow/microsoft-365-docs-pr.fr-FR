---
title: Déploiement basé sur l’application pour Microsoft Defender pour Endpoint sur iOS
ms.reviewer: ''
description: Décrit comment déployer Microsoft Defender pour endpoint sur iOS à l’aide d’une application
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, ios, application, installation, déployer, désinstallation, intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 612089ef8e4b4ba3429c5116847a5888c8ea752e4543da5c2d97b217f179bca4
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53817969"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-ios"></a>Déployer Microsoft Defender pour le point de terminaison sur iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Cette rubrique décrit le déploiement de Defender pour Endpoint sur iOS Portail d’entreprise Intune appareils inscrits. Pour plus d’informations sur l’inscription d’appareils Intune, voir Inscrire des appareils [iOS/iPadOS dans Intune.](/mem/intune/enrollment/ios-enroll)

## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vous avez accès au [Centre d’administration Microsoft Endpoint Manager.](https://go.microsoft.com/fwlink/?linkid=2109431)

- Assurez-vous que l’inscription iOS est effectuée pour vos utilisateurs. Une licence Defender pour point de terminaison doit être attribuée aux utilisateurs pour pouvoir utiliser Defender pour Endpoint sur iOS. Reportez-vous [à Attribuer des licences aux](/azure/active-directory/users-groups-roles/licensing-groups-assign) utilisateurs pour obtenir des instructions sur la façon d’attribuer des licences.

> [!NOTE]
> Microsoft Defender pour le point de terminaison sur iOS est disponible dans [l’App Store d’Apple.](https://aka.ms/mdatpiosappstore)

## <a name="deployment-steps"></a>Étapes de déploiement

Déployez Defender pour endpoint sur iOS via Portail d’entreprise Intune.

### <a name="add-ios-store-app"></a>Ajouter une application du Store iOS

1. Dans [le Centre d’administration Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)allez sur **Applications**  ->  **iOS/iPadOS** Ajouter une application de la Boutique  ->    ->  **d’applications iOS,** puis cliquez sur **Sélectionner.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager Centre d’administration 1](images/ios-deploy-1.png)

1. Dans la page Ajouter une application, cliquez sur Rechercher dans **l’App Store** et tapez **Microsoft Defender Endpoint** dans la barre de recherche. Dans la section des résultats de la recherche, cliquez sur Le point de terminaison *Microsoft Defender* et cliquez sur **Sélectionner.**

1. Sélectionnez **iOS 11.0 comme** système d’exploitation minimum. Consultez le reste des informations sur l’application et cliquez sur **Suivant.**

1. Dans la section *Affectations,* allez à la section **Obligatoire** et **sélectionnez Ajouter un groupe.** Vous pouvez ensuite choisir le ou les groupes d’utilisateurs que vous souhaitez cibler Defender pour le point de terminaison sur l’application iOS. Cliquez **sur Sélectionner,** puis **sur Suivant.**

    > [!NOTE]
    > Le groupe d’utilisateurs sélectionné doit être constitué d’utilisateurs inscrits à Intune.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager Admin Center2](images/ios-deploy-2.png)

1. Dans la section *Révision + Créer,* vérifiez que toutes les informations entrées sont correctes, puis sélectionnez **Créer.** Dans quelques instants, l’application Defender pour point de terminaison doit être créée correctement et une notification doit s’afficher dans le coin supérieur droit de la page.

1. Dans la page d’informations sur l’application  qui s’affiche, dans la **section** Moniteur, sélectionnez État de l’installation de l’appareil pour vérifier que l’installation de l’appareil s’est correctement terminée.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager Centre d’administration 3](images/ios-deploy-3.png)

## <a name="auto-onboarding-of-vpn-profile-simplified-onboarding"></a>Intégration automatique du profil VPN (intégration simplifiée)

Les administrateurs peuvent configurer la configuration automatique du profil VPN. Cela permet de configurer automatiquement le profil VPN Defender pour point de terminaison sans que l’utilisateur le fait lors de l’intégration. Notez que le VPN est utilisé pour fournir la fonctionnalité de protection Web. Il ne s’agit pas d’un VPN normal et d’un VPN local/en boucle autonome qui ne prend pas le trafic en dehors de l’appareil.

1. Dans [le Centre d’administration Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)allez à   ->  **Profils de configuration des**  ->  **appareils.**
1. Choisissez **Plateforme en** tant que **iOS/iPadOS** et type de profil en **tant** que **VPN**. Cliquez sur **Créer**.
1. Tapez un nom pour le profil, puis cliquez sur **Suivant.**
1. Sélectionnez **VPN personnalisé** pour le type de connexion et, dans la section VPN de **base,** entrez ce qui suit :
    - Nom de connexion = Microsoft Defender pour le point de terminaison
    - Adresse du serveur VPN = 127.0.0.1
    - Méthode Auth = « Nom d’utilisateur et mot de passe »
    - Tunneling fractionner = Désactiver
    - Identificateur VPN = com.microsoft.scmx
    - Dans les paires clé-valeur, entrez la clé **AutoOnboard** et définissez la valeur sur **True**.
    - Type de VPN automatique = VPN à la demande
    - Cliquez **sur** Ajouter pour **les règles à** la demande et sélectionnez « Je veux faire ce qui suit = Établir un **VPN**, je souhaite me limiter à = Tous **les domaines**».

    ![Capture d’écran de la configuration de profil VPN](images/ios-deploy-8.png)

1. Cliquez sur Suivant et affectez le profil à des utilisateurs ciblés.
1. Dans la section *Révision + Créer,* vérifiez que toutes les informations entrées sont correctes, puis sélectionnez **Créer.**

## <a name="complete-onboarding-and-check-status"></a>Terminer l’intégration et vérifier l’état

1. Une fois Que Defender pour le point de terminaison sur iOS a été installé sur l’appareil, vous verrez l’icône de l’application.

    ![Capture d’écran d’une description de smartphone générée automatiquement](images/41627a709700c324849bf7e13510c516.png)

2. Appuyez sur l’icône de l’application Defender for Endpoint (MSDefender) et suivez les instructions à l’écran pour effectuer les étapes d’intégration. Les détails incluent l’acceptation par l’utilisateur final des autorisations iOS requises par Defender pour endpoint sur iOS.

3. Une fois l’intégration réussie, l’appareil commence à s’afficher dans la liste Appareils du portail Microsoft 365 Defender web.

    > [!div class="mx-imgBorder"]
    > ![Capture d’écran d’une description de téléphone portable générée automatiquement](images/device-inventory-screen.png)

## <a name="configure-microsoft-defender-for-endpoint-for-supervised-mode"></a>Configurer Microsoft Defender pour le point de terminaison pour le mode Supervisé

Microsoft Defender pour endpoint sur l’application iOS dispose d’une capacité spécialisée sur les appareils iOS/iPadOS supervisés, étant donné les fonctionnalités de gestion accrues fournies par la plateforme sur ces types d’appareils. Pour tirer parti de ces fonctionnalités, l’application Defender for Endpoint doit savoir si un appareil est en mode Supervisé.

### <a name="configure-supervised-mode-via-intune"></a>Configurer le mode Supervisé via Intune

Intune vous permet de configurer l’application Defender pour iOS via une stratégie de configuration d’application.

   > [!NOTE]
   > Cette stratégie de configuration d’application pour les appareils supervisés s’applique uniquement aux appareils gérés et doit être ciblée pour tous les appareils iOS gérés en tant que meilleure pratique.

1. Connectez-vous au [centre d Microsoft Endpoint Manager’administration](https://go.microsoft.com/fwlink/?linkid=2109431) et allez aux stratégies de configuration **des applications**  >  **.**  >   Cliquez sur **Appareils gérés.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager Centre d’administration 4](images/ios-deploy-4.png)

1. Dans la page *Créer une stratégie de configuration d’application,* fournissez les informations suivantes :
    - Nom de la stratégie
    - Plateforme : sélectionner iOS/iPadOS
    - Application ciblée : sélectionner le **point de terminaison Microsoft Defender** dans la liste

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager Centre d’administration 5](images/ios-deploy-5.png)

1. Dans l’écran suivant, sélectionnez Utiliser **le concepteur de configuration** comme format. Spécifiez la propriété suivante :
    - Clé de configuration : issupervised
    - Type de valeur : Chaîne
    - Valeur de configuration : {{issupervised}}
    
    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager Centre d’administration 6](images/ios-deploy-6.png)

1. Cliquez **sur Suivant** pour ouvrir la page **Balises d’étendue.** Les balises d’étendue sont facultatives. Cliquez sur **Suivant** pour continuer.

1. Dans la page **Affectations,** sélectionnez les groupes qui recevront ce profil. Pour ce scénario, il est préférable de cibler **tous les appareils.** Pour plus d’informations sur l’attribution de profils, voir [Attribuer des profils utilisateur et d’appareil.](/mem/intune/configuration/device-profile-assign)

   Lors du déploiement sur des groupes d’utilisateurs, un utilisateur doit se connecter à un appareil avant que la stratégie ne s’applique.

   Cliquez sur **Suivant**.

1. On the **Review + create** page, when you’re done, choose **Create**. Le nouveau profil s’affiche dans la liste des profils de configuration.

1. Ensuite, pour les fonctionnalités anti-hameçonnage améliorées, vous pouvez déployer un profil personnalisé sur les appareils iOS supervisés. Suivez les étapes ci-dessous :
    - Télécharger le profil de config à partir de [https://aka.ms/mdatpiossupervisedprofile](https://aka.ms/mdatpiossupervisedprofile)
    - Accéder aux **profils**  ->  **de configuration iOS/iPadOS** Des appareils  ->    ->  **créent un profil**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager Centre d’administration 7](images/ios-deploy-7.png)

    - Fournissez le nom du profil. Lorsque vous y invitez l’importation d’un fichier de profil de configuration, sélectionnez celui téléchargé ci-dessus.
    - Dans la section **Affectation,** sélectionnez le groupe d’appareils auquel vous souhaitez appliquer ce profil. Il est préférable de l’appliquer à tous les appareils iOS gérés. Cliquez sur **Suivant**.
    - On the **Review + create** page, when you’re done, choose **Create**. Le nouveau profil s’affiche dans la liste des profils de configuration.

## <a name="next-steps"></a>Étapes suivantes

- [Configurer la stratégie de protection des applications pour inclure les signaux de risque de Point de terminaison Defender (MAM)](ios-install-unmanaged.md)
- [Configurer Defender pour endpoint sur les fonctionnalités iOS](ios-configure-features.md)
