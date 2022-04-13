---
title: Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune
description: Décrit comment déployer Microsoft Defender pour point de terminaison sur Android avec Microsoft Intune
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mde, android, installation, deploy, uninstallation,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 461664cc72486a49e5b7bd9be44235559409adff
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825253"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Découvrez comment déployer Defender pour point de terminaison sur Android sur Portail d'entreprise Intune appareils inscrits. Pour plus d’informations sur Intune’inscription d’appareil, consultez [Inscrire votre appareil](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **Defender pour point de terminaison sur Android est désormais disponible sur [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> Vous pouvez vous connecter à Google Play à partir de Intune pour déployer l’application Defender pour point de terminaison sur les modes d’inscription Administrateur d’appareil et Android Enterprise.
>
> Les mises à jour de l’application sont automatiques via Google Play.

## <a name="deploy-on-device-administrator-enrolled-devices"></a>Déployer sur des appareils inscrits par l’administrateur d’appareil

**Déployer Defender pour point de terminaison sur Android sur Portail d'entreprise Intune - Appareils inscrits par l’administrateur d’appareil**

Découvrez comment déployer Defender pour point de terminaison sur Android sur Portail d'entreprise Intune - Appareils inscrits par l’administrateur d’appareil.

### <a name="add-as-android-store-app"></a>Ajouter en tant qu’application du Store Android

1. Dans [Microsoft Endpoint Manager centre d’administration](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications** \> **Android Apps** \> **Add \> Android Store app** et **choisissez Sélectionner**.

   :::image type="content" source="images/mda-addandroidstoreapp.png" alt-text="Volet Ajouter une application du magasin Android dans le portail Microsoft Endpoint Manager Centre d’administration"  lightbox="images/mda-addandroidstoreapp.png":::

2. Dans la page **Ajouter une application** , dans la section *Informations sur l’application* , entrez :

   - **Name**
   - **Description**
   - **Publisher** en tant que Microsoft.
   - **URL de l’App Store** en tant qu’URL https://play.google.com/store/apps/details?id=com.microsoft.scmx (URL Google Play Store de l’application Defender pour point de terminaison)

   Les autres champs sont facultatifs. Sélectionnez **Suivant**.

   :::image type="content" source="images/mda-addappinfo.png" alt-text="Page Ajouter une application affichant les informations de l’éditeur et de l’URL de l’application dans le portail Microsoft Endpoint Manager Centre d’administration" lightbox="images/mda-addappinfo.png":::

3. Dans la section *Affectations* , accédez à la section **Obligatoire** et sélectionnez **Ajouter un groupe.** Vous pouvez ensuite choisir le ou les groupes d’utilisateurs que vous souhaitez cibler Defender pour point de terminaison sur l’application Android. **Sélectionnez Sélectionner**, puis **Suivant**.

    > [!NOTE]
    > Le groupe d’utilisateurs sélectionné doit se composer de Intune utilisateurs inscrits.
    >
    > :::image type="content" source="images/363bf30f7d69a94db578e8af0ddd044b.png" alt-text="Volet Ajouter un groupe dans la page Ajouter une application dans le portail Microsoft Endpoint Manager Centre d’administration" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. Dans la section **Vérifier+Créer** , vérifiez que toutes les informations entrées sont correctes, puis sélectionnez **Créer**.

    Dans quelques instants, l’application Defender pour point de terminaison est créée avec succès et une notification s’affiche en haut à droite de la page.

    :::image type="content" source="images/86cbe56f88bb6e93e9c63303397fc24f.png" alt-text="Volet État de l’application dans le portail Microsoft Endpoint Manager Centre d’administration" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. Dans la page d’informations de l’application qui s’affiche, dans la section **Moniteur** , sélectionnez **l’état d’installation** de l’appareil pour vérifier que l’installation de l’appareil s’est terminée correctement.

    :::image type="content" source="images/513cf5d59eaaef5d2b5bc122715b5844.png" alt-text="Page État de l’installation de l’appareil dans le portail Microsoft Defender 365" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>Terminer l’intégration et vérifier l’état

1. Une fois Defender pour point de terminaison sur Android installé sur l’appareil, l’icône de l’application s’affiche.

   :::image type="content" source="images/7cf9311ad676ec5142002a4d0c2323ca.jpg" alt-text="Icône Microsoft Defender ATP répertoriée dans le volet De recherche" lightbox="images/7cf9311ad676ec5142002a4d0c2323ca.jpg":::

2. Appuyez sur l’icône Microsoft Defender pour point de terminaison application et suivez les instructions à l’écran pour terminer l’intégration de l’application. Les détails incluent l’acceptation par l’utilisateur final des autorisations Android requises par Defender pour point de terminaison sur Android.

3. Une fois l’intégration réussie, l’appareil commence à s’afficher dans la liste Des appareils dans le portail Microsoft 365 Defender.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Un appareil dans le portail Microsoft Defender pour point de terminaison"  lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>Déployer sur des appareils android Enterprise inscrits

Defender pour point de terminaison sur Android prend en charge android Enterprise les appareils inscrits.

Pour plus d’informations sur les options d’inscription prises en charge par Intune, consultez [Options d’inscription](/mem/intune/enrollment/android-enroll).

**Actuellement, les appareils appartenant à l’utilisateur avec profil professionnel et les inscriptions d’appareils utilisateur entièrement gérés appartenant à l’entreprise sont pris en charge pour le déploiement.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>Ajouter Microsoft Defender pour point de terminaison sur Android en tant qu’application Google Play managée

Suivez les étapes ci-dessous pour ajouter Microsoft Defender pour point de terminaison application dans votre Google Play managé.

1. Dans [Microsoft Endpoint Manager centre d’administration](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications** \> **Android Apps** \> **Ajouter** et sélectionnez **l’application Google Play managée**.

    :::image type="content" source="images/579ff59f31f599414cedf63051628b2e.png" alt-text="Volet d’ajout d’applications dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. Sur votre page Google Play managée qui se charge par la suite, accédez à la zone de recherche et entrez `Microsoft Defender`. Votre recherche doit afficher l’application Microsoft Defender pour point de terminaison dans votre Google Play managé. Cliquez sur l’application Microsoft Defender pour point de terminaison à partir du résultat de recherche Applications.

    :::image type="content" source="images/0f79cb37900b57c3e2bb0effad1c19cb.png" alt-text="Page Google Play géré dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/0f79cb37900b57c3e2bb0effad1c19cb.png":::

3. Dans la page de description de l’application qui s’affiche ensuite, vous devez être en mesure de voir les détails de l’application sur Defender pour point de terminaison. Passez en revue les informations de la page, puis **sélectionnez Approuver**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/07e6d4119f265037e3b80a20a73b856f.png" alt-text="Page google play managée dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/07e6d4119f265037e3b80a20a73b856f.png":::
      

4. Vous recevrez les autorisations que Defender pour point de terminaison obtient pour qu’il fonctionne. Examinez-les, puis **sélectionnez Approuver**.

    :::image type="content" source="images/206b3d954f06cc58b3466fb7a0bd9f74.png" alt-text="Page d’approbation des autorisations dans le portail Microsoft Defender 365" lightbox="images/206b3d954f06cc58b3466fb7a0bd9f74.png":::

5. La page Paramètres d’approbation s’affiche. La page confirme votre préférence pour gérer les nouvelles autorisations d’application que Defender pour point de terminaison sur Android peut demander. Passez en revue les choix et sélectionnez votre option préférée. Sélectionnez **Terminé**.

    Par défaut, Google Play géré sélectionne **Conserver approuvé lorsque l’application demande de nouvelles autorisations**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ffecfdda1c4df14148f1526c22cc0236.png" alt-text=" Page d’achèvement de la configuration des paramètres d’approbation dans le portail Microsoft Defender 365" lightbox="images/ffecfdda1c4df14148f1526c22cc0236.png":::

6. Une fois la sélection des autorisations de gestion effectuée, sélectionnez **Synchroniser** pour synchroniser Microsoft Defender pour point de terminaison avec votre liste d’applications.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/34e6b9a0dae125d085c84593140180ed.png" alt-text="Volet Synchronisation dans le portail Microsoft Defender 365" lightbox="images/34e6b9a0dae125d085c84593140180ed.png":::

7. La synchronisation se termine dans quelques minutes.

    :::image type="content" source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" alt-text="Volet d’état de synchronisation des applications dans la page Applications Android du portail Microsoft Defender 365"  lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. Sélectionnez le bouton **Actualiser** dans l’écran Applications Android et Microsoft Defender pour point de terminaison doit être visible dans la liste des applications.

    :::image type="content" source="images/fa4ac18a6333335db3775630b8e6b353.png" alt-text="Page affichant l’application synchronisée" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. Defender pour point de terminaison prend en charge les stratégies de configuration d’application pour les appareils gérés via Intune. Cette fonctionnalité peut être exploitée pour sélectionner différentes configurations pour Defender.

    1. Dans la page **Applications** , accédez à Stratégie **> Stratégies de configuration d’application > Ajouter des appareils managés >**.

       :::image type="content" source="images/android-mem.png" alt-text="Volet Stratégies de configuration d’application dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/android-mem.png":::

    1. Dans la page Créer une stratégie de **configuration d’application** , entrez les détails suivants :

        - Nom : Microsoft Defender pour point de terminaison.
        - Choisissez **Android Enterprise** comme plateforme.
        - Choisissez **profil professionnel uniquement** en tant que type de profil.
        - Cliquez sur **Sélectionner l’application**, choisissez **Microsoft Defender ATP**, sélectionnez **OK** , puis **Suivant**.

        :::image type="content" source="images/android-create-app.png" alt-text=" Volet Détails de l’application associée" lightbox="images/android-create-app.png":::

    1. Dans la page **Paramètres**, accédez à la section **Paramètres de configuration** et choisissez **« Utiliser le concepteur de configuration »** au format Paramètres de configuration. 

       :::image type="content" alt-text="Image de la stratégie de configuration d’application de création d’application Android." source="images/configurationformat.png" lightbox="images/configurationformat.png":::

    1. Cliquez sur **Ajouter** pour afficher la liste des configurations prises en charge. Sélectionnez la configuration requise, puis cliquez sur **OK**.

       :::image type="content" alt-text="Image de la sélection des stratégies de configuration pour Android." source="images/selectconfigurations.png" lightbox="images/selectconfigurations.png":::


    1. Vous devez voir toutes les configurations sélectionnées répertoriées. Vous pouvez modifier la valeur de configuration en fonction des besoins, puis sélectionner **Suivant**.
        
        :::image type="content" alt-text="Image des stratégies de configuration sélectionnées." source="images/listedconfigurations.png" lightbox="images/listedconfigurations.png":::
       

    1. Dans la page **Affectations** , sélectionnez le groupe d’utilisateurs auquel cette stratégie de configuration d’application serait affectée. Cliquez sur **Sélectionner des groupes à inclure** et en sélectionnant le groupe applicable, puis en sélectionnant **Suivant**. Le groupe sélectionné ici est généralement le même groupe que celui auquel vous attribuez Microsoft Defender pour point de terminaison application Android.

       :::image type="content" source="images/android-select-group.png" alt-text="Volet Groupes sélectionnés" lightbox="images/android-select-group.png":::

    1. Dans la page **Vérifier + créer** qui vient ensuite, passez en revue toutes les informations, puis sélectionnez **Créer**.

        La stratégie de configuration de l’application pour Defender pour point de terminaison en grantant automatiquement l’autorisation de stockage est désormais affectée au groupe d’utilisateurs sélectionné.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="images/android-review-create.png" alt-text="Onglet Vérifier + créer dans la page Créer une stratégie de configuration d’application" lightbox="images/android-review-create.png":::

10. Sélectionnez l’application **Microsoft Defender ATP** dans la liste \> Modifier **les affectations de propriétés** \>  \> **.**

   :::image type="content" source="images/mda-properties.png" alt-text="Option Modifier sur la page Propriétés" lightbox="images/mda-properties.png":::

11. Affectez l’application en tant qu’application *obligatoire* à un groupe d’utilisateurs. Il est automatiquement installé dans le *profil professionnel* lors de la prochaine synchronisation de l’appareil via Portail d'entreprise’application. Cette affectation peut être effectuée en accédant à la section \> *Obligatoire* **Ajouter un groupe,** en sélectionnant le groupe d’utilisateurs, puis en cliquant sur **Sélectionner**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ea06643280075f16265a596fb9a96042.png" alt-text="Page Modifier l’application" lightbox="images/ea06643280075f16265a596fb9a96042.png":::

12. Dans la page **Modifier l’application** , passez en revue toutes les informations entrées ci-dessus. Sélectionnez **Ensuite Vérifier + Enregistrer** , puis **Enregistrer** à nouveau pour commencer l’affectation.

### <a name="auto-setup-of-always-on-vpn"></a>Configuration automatique du VPN Always-on

Defender pour point de terminaison prend en charge les stratégies de configuration d’appareil pour les appareils gérés via Intune. Cette fonctionnalité peut être utilisée pour **configurer automatiquement le VPN Always-on** sur Android Enterprise les appareils inscrits. L’utilisateur final n’a donc pas besoin de configurer le service VPN lors de l’intégration.

1. Sur **les appareils**, sélectionnez **Profils** \> de configuration **Créer une** **plateforme** \> de **profils** \> Android Enterprise

   Sélectionnez **Restrictions d’appareil** sous l’une des options suivantes, en fonction du type d’inscription de votre appareil :
   - **Profil professionnel entièrement managé, dédié et Corporate-Owned**
   - **Profil professionnel appartenant à l’utilisateur**

   Sélectionnez **Créer**.

   :::image type="content" source="images/1autosetupofvpn.png" alt-text="Élément de menu Profils de configuration dans le volet Stratégie" lightbox="images/1autosetupofvpn.png":::

2. **Configuration Paramètres** Fournir un **nom** et une **description** pour identifier de manière unique le profil de configuration.

   :::image type="content" source="images/2autosetupofvpn.png" alt-text="Champs Nom et Description du profil de configuration des appareils dans le volet De base" lightbox="images/2autosetupofvpn.png":::

3. Sélectionnez **Connectivité** et configurez le VPN :

   - Activer **le VPN Always-on**

     Configurez un client VPN dans le profil professionnel pour vous connecter et vous reconnecter automatiquement au VPN dans la mesure du possible. Un seul client VPN peut être configuré pour un VPN toujours actif sur un appareil donné. Veillez donc à ne pas déployer plus d’une stratégie VPN always on sur un seul appareil.

   - Sélectionner **Personnalisé** dans la liste déroulante du client VPN

     Dans ce cas, le VPN personnalisé est Defender pour point de terminaison, qui est utilisé pour fournir la fonctionnalité De protection web.

     > [!NOTE]
     > Microsoft Defender pour point de terminaison application doit être installée sur l’appareil de l’utilisateur, afin de fonctionner de la configuration automatique de ce VPN.

   - Entrez **l’ID de package** de l’application Microsoft Defender pour point de terminaison dans Google Play Store. Pour l’URL <https://play.google.com/store/apps/details?id=com.microsoft.scmx>de l’application Defender, l’ID de package est **com.microsoft.scmx**

   - **Mode verrouillage** Non configuré (par défaut)

     :::image type="content" source="images/3autosetupofvpn.png" alt-text="Volet Connectivité sous l’onglet Paramètres de configuration" lightbox="images/3autosetupofvpn.png":::

4. **Assignment**

   Dans la page **Affectations** , sélectionnez le groupe d’utilisateurs auquel cette stratégie de configuration d’application serait affectée. **Choisissez Sélectionner des groupes** à inclure et en sélectionnant le groupe applicable, puis sélectionnez **Suivant**. Le groupe sélectionné ici est généralement le même groupe que celui auquel vous attribuez Microsoft Defender pour point de terminaison application Android.

   :::image type="content" source="images/4autosetupofvpn.png" alt-text="Volet Affectation du profil de configuration des appareils dans les restrictions d’appareil" lightbox="images/4autosetupofvpn.png":::

5. Dans la page **Vérifier + créer** qui vient ensuite, passez en revue toutes les informations, puis sélectionnez **Créer**.
Le profil de configuration de l’appareil est maintenant affecté au groupe d’utilisateurs sélectionné.

   :::image type="content" source="images/5autosetupofvpn.png" alt-text="Provision d’un profil de configuration d’appareil pour Vérifier + créer" lightbox="images/5autosetupofvpn.png":::

## <a name="check-status-and-complete-onboarding"></a>Vérifier l’état et terminer l’intégration

1. Confirmez l’état d’installation de Microsoft Defender pour point de terminaison sur Android en cliquant sur **l’état d’installation de l’appareil**. Vérifiez que l’appareil est affiché ici.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/900c0197aa59f9b7abd762ab2b32e80c.png" alt-text="Volet État de l’installation de l’appareil" lightbox="images/900c0197aa59f9b7abd762ab2b32e80c.png":::

2. Sur l’appareil, vous pouvez valider l’état d’intégration en accédant au **profil professionnel**. Vérifiez que Defender pour point de terminaison est disponible et que vous êtes inscrit sur les **appareils personnels avec profil professionnel**. Si vous êtes inscrit sur un **appareil utilisateur d’entreprise entièrement géré**, vous disposez d’un profil unique sur l’appareil sur lequel vous pouvez confirmer que Defender pour point de terminaison est disponible.

    :::image type="content" source="images/c2e647fc8fa31c4f2349c76f2497bc0e.png" alt-text="Volet d’affichage de l’application" lightbox="images/c2e647fc8fa31c4f2349c76f2497bc0e.png":::

3. Une fois l’application installée, ouvrez l’application et acceptez les autorisations, puis votre intégration doit réussir.

    :::image type="content" source="images/MDE_new.png" alt-text="Ième affichage d’une application Microsoft Defender pour point de terminaison sur un appareil mobile" lightbox="images/MDE_new.png":::

4. À ce stade, l’appareil est correctement intégré à Defender pour point de terminaison sur Android. Vous pouvez le vérifier sur le [portail Microsoft 365 Defender](https://security.microsoft.com) en accédant à la page **Inventaire des appareils**.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Portail Microsoft Defender pour point de terminaison" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md)
- [Configurer Microsoft Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
