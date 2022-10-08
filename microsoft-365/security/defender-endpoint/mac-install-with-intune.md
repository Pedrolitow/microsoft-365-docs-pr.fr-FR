---
title: déploiement basé sur Intune pour Microsoft Defender pour point de terminaison sur Mac
description: Installez Microsoft Defender pour point de terminaison sur Mac à l’aide de Microsoft Intune.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 83d2bf85a6e6edf612975b7679e40769d06a3a89
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68221585"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>déploiement basé sur Intune pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Cette rubrique explique comment déployer des Microsoft Defender pour point de terminaison sur macOS via Intune. Un déploiement réussi nécessite l’achèvement de toutes les étapes suivantes :

1. [Télécharger le package d’intégration](#download-the-onboarding-package)
1. [Configuration de l’appareil client](#client-device-setup)
1. [Approuver les extensions système](#approve-system-extensions)
1. [Créer des profils de configuration système](#create-system-configuration-profiles)
1. [Publier l'application](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>Prérequis et configuration requise

Avant de commencer, consultez [la page principale Microsoft Defender pour point de terminaison sur macOS](microsoft-defender-endpoint-mac.md) pour obtenir une description des prérequis et de la configuration système requise pour la version actuelle du logiciel.

## <a name="overview"></a>Vue d’ensemble

Le tableau suivant récapitule les étapes à suivre pour déployer et gérer des Microsoft Defender pour point de terminaison sur Mac, via Intune. Des étapes plus détaillées sont disponibles ci-dessous.

<br>

****

|Étape|Exemples de noms de fichiers|BundleIdentifier|
|---|---|---|
|[Télécharger le package d’intégration](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[Approuver l’extension système pour Microsoft Defender pour point de terminaison](#approve-system-extensions)|MDATP_SysExt.xml|S/O|
|[Approuver l’extension de noyau pour Microsoft Defender pour point de terminaison](#download-the-onboarding-package)|MDATP_KExt.xml|S/O|
|[Accorder un accès disque complet à Microsoft Defender pour point de terminaison](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[Stratégie d’extension réseau](#network-filter)|MDATP_NetExt.xml|S/O|
|[Configurer Microsoft AutoUpdate (MAU)](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[Microsoft Defender pour point de terminaison paramètres de configuration](mac-preferences.md#intune-full-profile) <p> **Note:** Si vous envisagez d’exécuter un av tiers pour macOS, définissez `passiveMode` `true`sur .|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[Configurer les notifications Microsoft Defender pour point de terminaison et MS AutoUpdate (MAU)](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 ou com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>Télécharger le package d’intégration

Téléchargez les packages d’intégration à partir du portail Microsoft 365 Defender :

1. Dans Microsoft 365 Defender portail, accédez à **Paramètres** \> **Endpoints** \> **Device Management** \> **Onboarding**.

2. Définissez le système d’exploitation sur **macOS** et la méthode de déploiement sur **Mobile Gestion des appareils /Microsoft Intune**.

   :::image type="content" source="images/macos-install-with-intune.png" alt-text="Page Paramètres d’intégration" lightbox="images/macos-install-with-intune.png":::

3. Sélectionnez **Télécharger le package d’intégration**. Enregistrez-le en _tant queWindowsDefenderATPOnboardingPackage.zip_ dans le même répertoire.

4. Extrayez le contenu du fichier .zip :

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    warning:  WindowsDefenderATPOnboardingPackage.zip appears to use backslashes as path separators
      inflating: intune/kext.xml
      inflating: intune/WindowsDefenderATPOnboarding.xml
      inflating: jamf/WindowsDefenderATPOnboarding.plist
    ```

## <a name="create-system-configuration-profiles"></a>Créer des profils de configuration système

L’étape suivante consiste à créer des profils de configuration système dont Microsoft Defender pour point de terminaison a besoin.
Dans le [Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com/), ouvrez les **profils de configuration** **des appareils**\>.

### <a name="onboarding-blob"></a>Objet blob d’intégration

Ce profil contient des informations de licence pour Microsoft Defender pour point de terminaison. Sans ce profil, Microsoft Defender pour point de terminaison signale qu’il n’est pas sous licence.

1. Sélectionnez **Créer un profil** sous **Profils de configuration**.
1. Sélectionnez **Plateforme**=**macOS**,**modèles** **de type de profil**=. **Nom du modèle**= **Personnalisé**. Cliquez sur **Créer**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-1.png" alt-text="Page de création du profil de configuration personnalisé" lightbox="images/mdatp-6-systemconfigurationprofiles-1.png":::

1. Choisissez un nom pour le profil, par exemple , « Intégration de Defender pour le cloud ou de point de terminaison pour macOS ». Cliquez sur **Suivant**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Champ Nom du profil de configuration personnalisé" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Choisissez un nom pour le nom du profil de configuration, par exemple , « Intégration de Defender pour point de terminaison pour macOS ».
1. Choisissez un [canal de déploiement](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices).
1. Sélectionnez intune/WindowsDefenderATPOnboarding.xml que vous avez extrait du package d’intégration ci-dessus en tant que fichier de profil de configuration.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles.png" alt-text="Importation d’une configuration à partir d’un fichier pour le profil de configuration personnalisé" lightbox="images/mdatp-6-systemconfigurationprofiles.png":::

1. Cliquez sur **Suivant**.
1. Affectez des appareils sous l’onglet **Affectation** . Cliquez sur **Suivant**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Profil de configuration personnalisé - affectation" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Vérifier et **créer**.
1. Ouvrez les **profils de configuration** **des appareils**\>. Vous pouvez y voir votre profil créé.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-3.png" alt-text="Saisie semi-automatique du profil de configuration personnalisé" lightbox="images/mdatp-6-systemconfigurationprofiles-3.png":::

### <a name="approve-system-extensions"></a>Approuver les extensions système

Ce profil est nécessaire pour macOS 10.15 (Catalina) ou version ultérieure. Elle sera ignorée sur macOS plus ancien.

1. Sélectionnez **Créer un profil** sous **Profils de configuration**.
1. Sélectionnez **Plateforme**=**macOS**,**modèles** **de type de profil**=. **Nom du modèle**= **Extensions**. Cliquez sur **Créer**.
1. Sous l’onglet **Informations de base** , donnez un nom à ce nouveau profil.
1. Dans l’onglet **Paramètres de configuration** , développez **Extensions système** , puis ajoutez les entrées suivantes dans la section **Extensions système autorisées** :

    |Identificateur de bundle|Identificateur d’équipe|
    |---|---|
    |com.microsoft.wdav.epsext|UBF8T346G9|
    |com.microsoft.wdav.netext|UBF8T346G9|

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-system-extension-intune2.png" alt-text="Paramètres de l’extension du système" lightbox="images/mac-system-extension-intune2.png":::

1. Sous l’onglet **Affectations** , affectez ce profil à **tous les utilisateurs & tous les appareils**.
1. Examinez et créez ce profil de configuration.

### <a name="kernel-extensions"></a>Extensions de noyau

Ce profil est nécessaire pour macOS 10.15 (Catalina) ou version antérieure. Elle sera ignorée sur macOS plus récent.

> [!CAUTION]
> Les appareils Apple Silicon (M1) ne prennent pas en charge KEXT. L’installation d’un profil de configuration constitué de stratégies KEXT échoue sur ces appareils.

1. Sélectionnez **Créer un profil** sous **Profils de configuration**.
1. Sélectionnez **Plateforme**=**macOS**,**modèles** **de type de profil**=. **Nom du modèle**= **Extensions**. Cliquez sur **Créer**.
1. Sous l’onglet **Informations de base** , donnez un nom à ce nouveau profil.
1. Sous l’onglet **Paramètres de configuration** , développez **Extensions de noyau**.
1. Définissez **l’identificateur d’équipe** sur **UBF8T346G9** , puis cliquez sur **Suivant**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-kernel-extension-intune2.png" alt-text="Identificateurs d’équipe autorisés pour les extensions de noyau." lightbox="images/mac-kernel-extension-intune2.png":::

1. Sous l’onglet **Affectations** , affectez ce profil à **tous les utilisateurs & tous les appareils**.
1. Examinez et créez ce profil de configuration.

### <a name="full-disk-access"></a>Accès au disque complet

   > [!CAUTION]
   > macOS 10.15 (Catalina) contient de nouvelles améliorations en matière de sécurité et de confidentialité. À compter de cette version, par défaut, les applications ne peuvent pas accéder à certains emplacements sur le disque (tels que Documents, Téléchargements, Bureau, etc.) sans consentement explicite. En l’absence de ce consentement, Microsoft Defender pour point de terminaison ne peut pas protéger entièrement votre appareil.
   >
   > Ce profil de configuration accorde l’accès au disque complet à Microsoft Defender pour point de terminaison. Si vous avez précédemment configuré Microsoft Defender pour point de terminaison via Intune, nous vous recommandons de mettre à jour le déploiement avec ce profil de configuration.

Téléchargez [**fulldisk.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) à partir de [notre référentiel GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Suivez les instructions [d’intégration de l’objet blob](#onboarding-blob) ci-dessus, en utilisant « Defender pour point de terminaison Full Disk Access » comme nom de profil et **fulldisk.mobileconfig** téléchargé en tant que nom de profil de configuration.

### <a name="network-filter"></a>Filtre réseau

Dans le cadre des fonctionnalités de détection et de réponse des points de terminaison, Microsoft Defender pour point de terminaison sur macOS inspecte le trafic de socket et signale ces informations au portail Microsoft 365 Defender. La stratégie suivante permet à l’extension réseau d’effectuer cette fonctionnalité.

Téléchargez [**netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) à partir de [notre référentiel GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Suivez les instructions pour [intégrer l’objet blob](#onboarding-blob) ci-dessus, en utilisant « Defender pour endpoint Network Filter » comme nom de profil et **netfilter.mobileconfig** téléchargé en tant que nom de profil de configuration.

### <a name="notifications"></a>Notifications

Ce profil permet à Microsoft Defender pour point de terminaison sur macOS et Microsoft Auto Update d’afficher des notifications dans l’interface utilisateur sur macOS 10.15 (Catalina) ou version ultérieure.

Téléchargez [**notif.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) à partir de [notre référentiel GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Suivez les instructions pour [intégrer l’objet blob](#onboarding-blob) ci-dessus, en utilisant « Defender pour les notifications de point de terminaison » comme nom de profil et en téléchargeant **notif.mobileconfig** comme nom de profil de configuration.

### <a name="view-status"></a>Afficher l’état

Une fois que les modifications Intune sont propagées aux appareils inscrits, vous pouvez les voir répertoriés sous **Surveiller** \> **l’état de l’appareil** :

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/mdatp-7-devicestatusblade.png" alt-text="Vue de l’état de l’appareil" lightbox="images/mdatp-7-devicestatusblade.png":::

## <a name="publish-application"></a>Publier l'application

Cette étape permet de déployer Microsoft Defender pour point de terminaison sur des machines inscrites.

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com/), ouvrez **Applications**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-8-app-before.png" alt-text="Page vue d’ensemble de l’application" lightbox="images/mdatp-8-app-before.png":::

1. Sélectionnez By platform > macOS > Add.
1. Choisissez **le type d’application**=**macOS**, puis cliquez sur **Sélectionner**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-9-app-type.png" alt-text="Type d’application spécifique" lightbox="images/mdatp-9-app-type.png":::

1. Conservez les valeurs par défaut, cliquez sur **Suivant**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-10-properties.png" alt-text="Page propriétés de l’application" lightbox="images/mdatp-10-properties.png":::

1. Ajoutez des affectations, cliquez sur **Suivant**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-11-assignments.png" alt-text="Page d’informations sur les affectations Intune" lightbox="images/mdatp-11-assignments.png":::

1. Vérifier et **créer**.
1. Vous pouvez visiter La **plateforme** \> **Apps** \> By **macOS** pour la voir dans la liste de toutes les applications.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-12-applications.png" alt-text="Page listes d’applications" lightbox="images/mdatp-12-applications.png":::

Pour plus d’informations, consultez [Ajouter des Microsoft Defender pour point de terminaison aux appareils macOS à l’aide de Microsoft Intune](/mem/intune/apps/apps-advanced-threat-protection-macos).)

   > [!CAUTION]
   > Vous devez créer tous les profils de configuration requis et les envoyer (push) à toutes les machines, comme expliqué ci-dessus.

## <a name="client-device-setup"></a>Configuration de l’appareil client

Vous n’avez pas besoin d’un approvisionnement spécial pour un appareil Mac au-delà d’une [installation Portail d'entreprise](/intune-user-help/enroll-your-device-in-intune-macos-cp) standard.

1. Confirmez la gestion des appareils.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-3-confirmdevicemgmt.png" alt-text="Page Confirmer la gestion des appareils" lightbox="images/mdatp-3-confirmdevicemgmt.png":::

    Sélectionnez **Ouvrir les préférences système**, localisez le **profil de gestion** dans la liste, puis **sélectionnez Approuver...**. Votre profil de gestion s’affiche comme **vérifié** :

    :::image type="content" source="images/mdatp-4-managementprofile.png" alt-text="Page Profil de gestion" lightbox="images/mdatp-4-managementprofile.png":::

2. Sélectionnez **Continuer** et terminez l’inscription.

   Vous pouvez maintenant inscrire d’autres appareils. Vous pouvez également les inscrire ultérieurement, une fois que vous avez terminé l’approvisionnement de la configuration du système et des packages d’application.

3. Dans Intune, **ouvrez Gérer** \> les **appareils** \> **tous les appareils**. Ici, vous pouvez voir votre appareil parmi ceux répertoriés :

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mdatp-5-alldevices.png" alt-text="Page Tous les appareils" lightbox="images/mdatp-5-alldevices.png":::

## <a name="verify-client-device-state"></a>Vérifier l’état de l’appareil client

1. Une fois les profils de configuration **déployés sur vos** appareils, ouvrez **profils de préférences** \> système sur votre appareil Mac.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-13-systempreferences.png" alt-text="Page Préférences système" lightbox="images/mdatp-13-systempreferences.png":::

   :::image type="content" source="images/mdatp-14-systempreferencesprofiles.png" alt-text="Page Profils des préférences système" lightbox="images/mdatp-14-systempreferencesprofiles.png":::

2. Vérifiez que les profils de configuration suivants sont présents et installés. Le **profil de gestion** doit être le profil système Intune. _Wdav-config_ et _wdav-kext_ sont des profils de configuration système qui ont été ajoutés dans Intune :

   :::image type="content" source="images/mdatp-15-managementprofileconfig.png" alt-text="Page Profils" lightbox="images/mdatp-15-managementprofileconfig.png":::

3. Vous devez également voir l’icône Microsoft Defender pour point de terminaison dans le coin supérieur droit :

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Icône pour Microsoft Defender pour point de terminaison dans la barre d’état" lightbox="images/mdatp-icon-bar.png":::

## <a name="troubleshooting"></a>Résolution des problèmes

Problème : Aucune licence trouvée.

Solution : suivez les étapes ci-dessus pour créer un profil d’appareil à l’aide de WindowsDefenderATPOnboarding.xml.

## <a name="logging-installation-issues"></a>Problèmes d’installation de la journalisation

Pour plus d’informations sur la recherche du journal généré automatiquement créé par le programme d’installation en cas d’erreur, consultez [Problèmes d’installation de la journalisation](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>Désinstallation

Pour plus d’informations sur la suppression de Microsoft Defender pour point de terminaison sur macOS sur les appareils clients, consultez [Désinstallation](mac-resources.md#uninstalling).
