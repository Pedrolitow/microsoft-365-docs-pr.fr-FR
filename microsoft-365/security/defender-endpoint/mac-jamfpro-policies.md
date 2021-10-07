---
title: Configurer microsoft Defender pour le point de terminaison sur les stratégies macOS dans Jamf Pro
description: Découvrez comment configurer les stratégies Microsoft Defender for Endpoint sur macOS dans Jamf Pro
keywords: policies, microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamfpro, macos, defender, mojave, high sierra
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
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 0bc0b09bcb834c67cb5da13469139875037440b0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60198684"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Configurer microsoft Defender pour le point de terminaison sur les stratégies macOS dans Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)

Cette page vous guide à travers les étapes à suivre pour configurer des stratégies macOS dans Jamf Pro.

Vous devez suivre les étapes suivantes :

1. [Obtenir le package d’intégration De Microsoft Defender pour point de terminaison](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Créer un profil de configuration dans Jamf Pro à l’aide du package d’intégration](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Configurer les paramètres de Microsoft Defender pour les points de terminaison](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Configurer microsoft Defender pour les paramètres de notification de point de terminaison](#step-4-configure-notifications-settings)
5. [Configurer la mise à jour automatique Microsoft (AutoUpdate)](#step-5-configure-microsoft-autoupdate-mau)
6. [Accorder un accès disque complet à Microsoft Defender pour le point de terminaison](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Approuver l’extension de noyau pour Microsoft Defender pour le point de terminaison](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Approuver les extensions système pour Microsoft Defender pour le point de terminaison](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Configurer l’extension réseau](#step-9-configure-network-extension)
10. [Planifier des analyses avec Microsoft Defender pour endpoint sur macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [Déployer Microsoft Defender pour le point de terminaison sur macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>Étape 1 : Obtenir le package d’intégration De Microsoft Defender pour point de terminaison

1. In [Centre de sécurité Microsoft Defender](https://securitycenter.microsoft.com), navigate to **Paramètres > Onboarding**.

2. Sélectionnez macOS comme système d’exploitation et Gestion des périphériques mobiles/Microsoft Intune comme méthode de déploiement.

    ![Image de Centre de sécurité Microsoft Defender.](images/onboarding-macos.png)

3. Sélectionnez **Télécharger le package d’intégration** (WindowsDefenderATPOnboardingPackage.zip).

4. Extraire `WindowsDefenderATPOnboardingPackage.zip` .

5. Copiez le fichier à votre emplacement préféré. Par exemple, `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>Étape 2 : Créer un profil de configuration dans Jamf Pro à l’aide du package d’intégration

1. Recherchez le `WindowsDefenderATPOnboarding.plist` fichier dans la section précédente.

   ![Image du fichier WindowsDefenderATPOnboarding.](images/plist-onboarding-file.png)

2. Dans le tableau de bord Pro Jamf, sélectionnez **Nouveau**.

    ![Image de la création d’un tableau de bord Pro Jamf.](images/jamf-pro-configure-profile.png)

3. Entrez les détails suivants :

   **Général**:

   - Nom : intégration MDATP pour macOS
   - Description : intégration PEPT MDATP pour macOS
   - Catégorie : Aucun
   - Méthode de distribution : installer automatiquement
   - Niveau : niveau ordinateur

4. In **Application & Custom Paramètres** select **Configure**.

    ![Image de la configuration de l’application et des paramètres personnalisés.](images/jamfpro-mac-profile.png)

5. Sélectionnez **Télécharger fichier (fichier PLIST),** puis dans **Domaine** de préférence, entrez `com.microsoft.wdav.atp` :

    ![Image du fichier de téléchargement plist jamfpro.](images/jamfpro-plist-upload.png)

    ![Image du fichier de liste des propriétés de fichier de téléchargement.](images/jamfpro-plist-file.png)

6. Sélectionnez **Ouvrir** et sélectionnez le fichier d’intégration.

    ![Image du fichier d’intégration.](images/jamfpro-plist-file-onboard.png)

7. Sélectionnez **Télécharger**.

    ![Image du téléchargement d’un fichier plist.](images/jamfpro-upload-plist.png)

8. Sélectionnez **l’onglet** Étendue.

    ![Image de l’onglet d’étendue.](images/jamfpro-scope-tab.png)

9. Sélectionnez les ordinateurs cibles.

    ![Image des ordinateurs cibles.](images/jamfpro-target-computer.png)

    ![Image des cibles.](images/jamfpro-targets.png)

10. Sélectionnez **Enregistrer**.

    ![Image des ordinateurs cibles de déploiement.](images/jamfpro-deployment-target.png)

    ![Image des ordinateurs cibles sélectionnés.](images/jamfpro-target-selected.png)

11. Sélectionnez **Terminé**.

    ![Image des ordinateurs de groupe cibles.](images/jamfpro-target-group.png)

    ![Liste des profils de configuration.](images/jamfpro-configuration-policies.png)

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>Étape 3 : Configurer Microsoft Defender pour les paramètres de point de terminaison

Vous pouvez utiliser jamf Pro GUI pour modifier les paramètres individuels de la configuration Microsoft Defender ou utiliser la méthode héritée en créant un Plist de configuration dans un éditeur de texte et en le téléchargeant dans jamf Pro.

Notez que vous devez utiliser exact comme domaine de préférence , Microsoft Defender utilise uniquement ce nom et pour `com.microsoft.wdav` charger ses  `com.microsoft.wdav.ext` paramètres gérés !

(La version peut être utilisée dans de rares cas lorsque vous préférez utiliser la méthode GUI, mais que vous devez également configurer un paramètre qui n’a pas encore été ajouté au `com.microsoft.wdav.ext` schéma.)

### <a name="gui-method"></a>Méthode GUI

1. Téléchargez le fichier schema.json à partir du référentiel [GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) defender et enregistrez-le dans un fichier local :

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Créez un profil de configuration sous Ordinateurs -> profils de configuration, entrez les détails suivants sous **l’onglet Général** :

    ![Nouveau profil.](images/644e0f3af40c29e80ca1443535b2fe32.png)

    - Nom : paramètres de configuration MDAV MDATP
    - Description :\<blank\>
    - Catégorie : Aucun (par défaut)
    - Niveau : niveau ordinateur (par défaut)
    - Méthode de distribution : installer automatiquement (par défaut)

3. Faites défiler vers le bas jusqu’à l’onglet Application &  Custom  **Paramètres,** sélectionnez **Applications** externes, cliquez sur Ajouter et utiliser le schéma personnalisé comme source à utiliser pour le domaine de préférence.

    ![Ajoutez un schéma personnalisé.](images/4137189bc3204bb09eed3aabc41afd78.png)

4. Entrez comme domaine de préférence, cliquez sur Ajouter un schéma et Télécharger fichier `com.microsoft.wdav` schema.json téléchargé à l’étape 1.   Cliquez sur **Enregistrer**.

    ![Télécharger schéma.](images/a6f9f556037c42fabcfdcb1b697244cf.png)

5. Vous pouvez voir tous les paramètres de configuration de Microsoft Defender pris en charge ci-dessous, sous **Propriétés de domaine de préférence.** Cliquez **sur Ajouter/Supprimer des propriétés** pour sélectionner les paramètres à gérer, puis cliquez sur **OK** pour enregistrer vos modifications. (Paramètres non sélectionné ne sera pas inclus dans la configuration gérée, un utilisateur final pourra configurer ces paramètres sur ses ordinateurs.)

    ![Sélectionnez les paramètres gérés.](images/817b3b760d11467abe9bdd519513f54f.png)

6. Modifiez les valeurs des paramètres en valeurs souhaitées. Vous pouvez cliquer **sur Plus d’informations** pour obtenir la documentation d’un paramètre particulier. (Vous pouvez cliquer sur **aperçu Plist** pour inspecter l’apparence de la liste de configuration. Cliquez **sur Éditeur de formulaire** pour revenir à l’éditeur visuel.)

    ![Modifier les valeurs des paramètres.](images/a14a79efd5c041bb8974cb5b12b3a9b6.png)

7. Sélectionnez **l’onglet** Étendue.

    ![Étendue du profil de configuration.](images/9fc17529e5577eefd773c658ec576a7d.png)

8. Sélectionnez **Le groupe d’ordinateurs de Contoso.**

9. Sélectionnez **Ajouter,** puis **Enregistrer.**

    ![Paramètres de configuration : ajouter.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![Paramètres de configuration : enregistrer.](images/6f093e42856753a3955cab7ee14f12d9.png)

10. Sélectionnez **Terminé**. Vous verrez le nouveau profil **de configuration.**

    ![Paramètres de configuration : terminé.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

Microsoft Defender ajoute de nouveaux paramètres au fil du temps. Ces nouveaux paramètres seront ajoutés au schéma et une nouvelle version sera publiée sur Github.
Il vous suffit de télécharger un schéma mis à jour, de modifier  le profil de configuration existant et de modifier le schéma sous l’onglet Application **& Custom Paramètres.**

### <a name="legacy-method"></a>Méthode héritée

1. Utilisez les paramètres de configuration de Microsoft Defender pour les points de terminaison suivants :

    - enableRealTimeProtection
    - passiveMode

    > [!NOTE]
    > Non désactivé par défaut, si vous envisagez d’exécuter un antivirus tiers pour macOS, définissez-le sur `true` .

    - exclusions
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - exclusionsMergePolicy
    - allowedThreats

    > [!NOTE]
    > EICAR est sur l’exemple, si vous êtes en train de passer par une preuve de concept, supprimez-le en particulier si vous testez EICAR.

    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - étiquettes
    - hideStatusMenuIcon

     Pour plus d’informations, [voir Liste des propriétés pour le profil de configuration complet JAMF.](mac-preferences.md#property-list-for-jamf-full-configuration-profile)

     ```XML
     <?xml version="1.0" encoding="UTF-8"?>
     <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
     <plist version="1.0">
     <dict>
         <key>antivirusEngine</key>
         <dict>
             <key>enableRealTimeProtection</key>
             <true/>
             <key>passiveMode</key>
             <false/>
             <key>exclusions</key>
             <array>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <false/>
                     <key>path</key>
                     <string>/var/log/system.log</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <true/>
                     <key>path</key>
                     <string>/home</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileExtension</string>
                     <key>extension</key>
                     <string>pdf</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileName</string>
                     <key>name</key>
                     <string>cat</string>
                 </dict>
             </array>
             <key>exclusionsMergePolicy</key>
             <string>merge</string>
             <key>allowedThreats</key>
             <array>
                 <string>EICAR-Test-File (not a virus)</string>
             </array>
             <key>disallowedThreatActions</key>
             <array>
                 <string>allow</string>
                 <string>restore</string>
             </array>
             <key>threatTypeSettings</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>potentially_unwanted_application</string>
                     <key>value</key>
                     <string>block</string>
                 </dict>
                 <dict>
                     <key>key</key>
                     <string>archive_bomb</string>
                     <key>value</key>
                     <string>audit</string>
                 </dict>
             </array>
             <key>threatTypeSettingsMergePolicy</key>
             <string>merge</string>
         </dict>
         <key>cloudService</key>
         <dict>
             <key>enabled</key>
             <true/>
             <key>diagnosticLevel</key>
             <string>optional</string>
             <key>automaticSampleSubmission</key>
             <true/>
         </dict>
         <key>edr</key>
         <dict>
             <key>tags</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>GROUP</string>
                     <key>value</key>
                     <string>ExampleTag</string>
                 </dict>
             </array>
         </dict>
         <key>userInterface</key>
         <dict>
             <key>hideStatusMenuIcon</key>
             <false/>
         </dict>
     </dict>
     </plist>
     ```

2. Enregistrez le fichier sous `MDATP_MDAV_configuration_settings.plist` .

3. Dans le tableau de bord Jamf Pro, ouvrez **Ordinateurs,** et il y a des **profils de configuration.** Cliquez sur **Nouveau (* et basculez vers **l’onglet** Général.

    ![Nouveau profil.](images/644e0f3af40c29e80ca1443535b2fe32.png)

4. Entrez les détails suivants :

    **Général**

    - Nom : paramètres de configuration MDAV MDATP
    - Description :\<blank\>
    - Catégorie : Aucun (par défaut)
    - Méthode de distribution : installer automatiquement (par défaut)
    - Niveau : Niveau ordinateur (par défaut)

    ![Image des paramètres de configuration MDAV MDATP.](images/3160906404bc5a2edf84d1d015894e3b.png)

5. In **Application & Custom Paramètres** select **Configure**.

    ![Image de l’application et des paramètres personnalisés.](images/e1cc1e48ec9d5d688087b4d771e668d2.png)

6. Sélectionnez **Télécharger fichier (fichier PLIST).**

    ![Image du fichier plist des paramètres de configuration.](images/6f85269276b2278eca4bce84f935f87b.png)

7. In **Preferences Domain**, enter `com.microsoft.wdav` , then select Télécharger **PLIST File**.

    ![Image du domaine des préférences de paramètres de configuration.](images/db15f147dd959e872a044184711d7d46.png)

8. Sélectionnez **Choisir un fichier.**

    ![Image des paramètres de configuration choisir un fichier.](images/526e978761fc571cca06907da7b01fd6.png)

9. Sélectionnez **le MDATP_MDAV_configuration_settings.plist,** puis sélectionnez **Ouvrir.**

    ![Image des paramètres de configuration mdatpmdav.](images/98acea3750113b8dbab334296e833003.png)

10. Sélectionnez **Télécharger**.

    ![Image du téléchargement des paramètres de configuration.](images/0adb21c13206861ba9b30a879ade93d3.png)

    ![Image de l’image de téléchargement des paramètres de configuration.](images/f624de59b3cc86e3e2d32ae5de093e02.png)

    > [!NOTE]
    > Si vous téléchargez le fichier Intune, vous obtenez l’erreur suivante :
    >
    >![Image du téléchargement de fichiers intune des paramètres de configuration.](images/8e69f867664668796a3b2904896f0436.png)

11. Sélectionnez **Enregistrer**.

    ![Image des paramètres de configuration Enregistrer l’image.](images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png)

12. Le fichier est téléchargé.

    ![Image de l’image téléchargée du fichier de paramètres de configuration.](images/33e2b2a1611fdddf6b5b79e54496e3bb.png)

    ![Image du fichier de paramètres de configuration téléchargé.](images/a422e57fe8d45689227e784443e51bd1.png)

13. Sélectionnez **l’onglet** Étendue.

    ![Image de l’étendue des paramètres de configuration.](images/9fc17529e5577eefd773c658ec576a7d.png)

14. Sélectionnez **Le groupe d’ordinateurs de Contoso.**

15. Sélectionnez **Ajouter,** puis **Enregistrer.**

    ![Image des paramètres de configuration addsav.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![Image des paramètres de configuration enregistrer ajouter.](images/6f093e42856753a3955cab7ee14f12d9.png)

16. Sélectionnez **Terminé**. Vous verrez le nouveau profil **de configuration.**

    ![Image de l’image de profil de configuration des paramètres de configuration.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

## <a name="step-4-configure-notifications-settings"></a>Étape 4 : Configurer les paramètres de notification

Ces étapes s’appliquent à macOS 10.15 (Genre), ou une nouveauté.

1. Dans le tableau de bord Jamf Pro, **sélectionnez Ordinateurs,** puis **Profils de configuration.**

2. Cliquez **sur** Nouveau, puis entrez les détails suivants pour **options**:

    - Onglet **Général**:
        - **Name**: Paramètres de notification MDAV MDATP
        - **Description**: macOS 10.15 (Contrôle) ou une nouveauté
        - **Catégorie**: Aucun *(par défaut)*
        - **Méthode de distribution**: installer automatiquement *(par défaut)*
        - **Niveau**: niveau ordinateur *(par défaut)*

        ![Image du nouvel écran de profil de configuration macOS.](images/c9820a5ff84aaf21635c04a23a97ca93.png)

    - Tab **Notifications,** click **Add**, and enter the following values:
        - **ID d’offre groupée**: `com.microsoft.wdav.tray`
        - **Alertes critiques**: cliquez sur **Désactiver**
        - **Notifications :** cliquez sur **Activer**
        - **Type d’alerte bannière**: sélectionner **Inclure** **et temporaire** *(par défaut)*
        - **Notifications sur l’écran de verrouillage**: cliquez sur **Masquer**
        - **Notifications dans le Centre de notifications**: cliquez sur **Afficher**
        - **Icône d’application de badge**: cliquez sur **Afficher**

        ![Image du bac de notifications mdatpmdav des paramètres de configuration.](images/7f9138053dbcbf928e5182ee7b295ebe.png)

    - Tab **Notifications**, click **Add** one more time, scroll down to **New Notifications Paramètres**
        - **ID d’offre groupée**: `com.microsoft.autoupdate2`
        - Configurer le reste des paramètres sur les mêmes valeurs que ci-dessus

        ![Image des paramètres de configuration mdatpmdav notifications mau.](images/4bac6ce277aedfb4a674f2d9fcb2599a.png)

        Notez que vous avez maintenant deux « tables » avec des configurations de notification, une pour l’ID d’offre groupée : **com.microsoft.wdav.tray** et une autre pour l’ID d’offre groupée : **com.microsoft.autoupdate2**. Bien que vous pouvez configurer les paramètres d’alerte en fonction de vos  besoins,  les ID d’offre groupée doivent être exactement les mêmes que ceux décrits précédemment, et le commutateur Inclure doit être en cours pour les **notifications.**

3. Sélectionnez **l’onglet** Étendue, puis **sélectionnez Ajouter.**

    ![Image de l’étendue des paramètres de configuration.](images/441aa2ecd36abadcdd8aed03556080b5.png)

4. Sélectionnez **Le groupe d’ordinateurs de Contoso.**

5. Sélectionnez **Ajouter,** puis **Enregistrer.**

    ![Image des paramètres de configuration contoso machine grp save.](images/09a275e321268e5e3ac0c0865d3e2db5.png)

    ![Image des paramètres de configuration pour ajouter l’enregistrer.](images/4d2d1d4ee13d3f840f425924c3df0d51.png)

6. Sélectionnez **Terminé**. Vous verrez le nouveau profil **de configuration.**

    ![Image du paramètre de configuration terminé img.](images/633ad26b8bf24ec683c98b2feb884bdf.png)

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>Étape 5 : Configurer la mise à jour automatique Microsoft (AutoUpdate)

1. Utilisez les paramètres de configuration de Microsoft Defender pour les points de terminaison suivants :

      ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
    <key>ChannelName</key>
    <string>Current</string>
    <key>HowToCheck</key>
    <string>AutomaticDownload</string>
    <key>EnableCheckForUpdatesButton</key>
    <true/>
    <key>DisableInsiderCheckbox</key>
    <false/>
    <key>SendAllTelemetryEnabled</key>
    <true/>
   </dict>
   </plist>
   ```

2. Enregistrez-le sous `MDATP_MDAV_MAU_settings.plist` .

3. Dans le tableau de bord Pro Jamf, sélectionnez **Général**.

    ![Image de l’image générale du paramètre de configuration.](images/eaba2a23dd34f73bf59e826217ba6f15.png)

4. Entrez les détails suivants :

    **Général**

    - Name: MDATP MDAV MAU settings
    - Description : Paramètres de mise à jour automatique Microsoft pour MDATP pour macOS
    - Catégorie : Aucun (par défaut)
    - Méthode de distribution : installer automatiquement (par défaut)
    - Niveau : Niveau ordinateur (par défaut)

5. In **Application & Custom Paramètres** select **Configure**.

    ![Image de l’application de paramètre de configuration et des paramètres personnalisés.](images/1f72e9c15eaafcabf1504397e99be311.png)

6. Sélectionnez **Télécharger fichier (fichier PLIST).**

    ![Image de la liste plist des paramètres de configuration.](images/1213872db5833aa8be535da57653219f.png)

7. In **Preference Domain** enter: , then select Télécharger `com.microsoft.autoupdate2` **PLIST File**.

    ![Image du domaine préf du paramètre de configuration.](images/1213872db5833aa8be535da57653219f.png)

8. Sélectionnez **Choisir un fichier.**

    ![Image du fichier choosefile du paramètre de configuration.](images/335aff58950ce62d1dabc289ecdce9ed.png)

9. Sélectionnez **MDATP_MDAV_MAU_settings.plist.**

    ![Image des paramètres de configuration mdatpmdavmau.](images/a26bd4967cd54bb113a2c8d32894c3de.png)

10. Sélectionnez **Télécharger**.
    ![Image de la configuration de la configuration de délimitation.](images/4239ca0528efb0734e4ca0b490bfb22d.png)

    ![Image de la configuration de la configuration de la délimitation.](images/4ec20e72c8aed9a4c16912e01692436a.png)

11. Sélectionnez **Enregistrer**.

    ![Image du paramètre de configuration saveimg.](images/253274b33e74f3f5b8d475cf8692ce4e.png)

12. Sélectionnez **l’onglet** Étendue.

     ![Image du paramètre de configuration scopetab.](images/10ab98358b2d602f3f67618735fa82fb.png)

13. Sélectionnez **Ajouter**.

    ![Image du paramètre de configuration addimg1.](images/56e6f6259b9ce3c1706ed8d666ae4947.png)

    ![Image du paramètre de configuration addimg2.](images/38c67ee1905c4747c3b26c8eba57726b.png)

    ![Image du paramètre de configuration addimg3.](images/321ba245f14743c1d5d51c15e99deecc.png)

14. Sélectionnez **Terminé**.

    ![Image du paramètre de configuration doneimage.](images/ba44cdb77e4781aa8b940fb83e3c21f7.png)

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>Étape 6 : Accorder un accès disque complet à Microsoft Defender pour le point de terminaison

1. Dans le tableau de bord Jamf Pro, sélectionnez **Profils de configuration.**

    ![Image du profil de configuration des paramètres de configuration.](images/264493cd01e62c7085659d6fdc26dc91.png)

2. Sélectionnez **+ Nouveau**.

3. Entrez les détails suivants :

    **Général**
    - Nom : MDATP MDAV - accorder un accès disque total à PEPT et antivirus
    - Description : sur macOS Ou une nouveauté, le nouveau contrôle de stratégie des préférences de confidentialité
    - Catégorie : Aucun
    - Méthode de distribution : installer automatiquement
    - Niveau : niveau ordinateur

    ![Image du paramètre de configuration général.](images/ba3d40399e1a6d09214ecbb2b341923f.png)

4. In **Configure Privacy Preferences Policy Control** select **Configure**.

    ![Image du contrôle de la stratégie de confidentialité de la configuration.](images/715ae7ec8d6a262c489f94d14e1e51bb.png)

5. Dans **le contrôle de stratégie des préférences de confidentialité,** entrez les détails suivants :

    - Identificateur : `com.microsoft.wdav`
    - Type d’identificateur : ID d’offre groupée
    - Conditions requises pour le code : `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    ![Image des détails du contrôle de stratégie de confidentialité des paramètres de configuration.](images/22cb439de958101c0a12f3038f905b27.png)

6. Sélectionnez **+ Ajouter**.

    ![Image du paramètre de configuration pour ajouter la stratégie système à tous les fichiers.](images/bd93e78b74c2660a0541af4690dd9485.png)

    - Sous Application ou service : définir sur **SystemPolicyAllFiles**

    - Sous « accès » : définir sur **Autoriser**

7. Sélectionnez **Enregistrer** (et non celui en bas à droite).

    ![Image des images d’enregistrer les paramètres de configuration.](images/6de50b4a897408ddc6ded56a09c09fe2.png)

8. Cliquez sur le `+` signe en de côté **d’App Access** pour ajouter une nouvelle entrée.

    ![Image de l’accès à l’application de paramètre de configuration.](images/tcc-add-entry.png)

9. Entrez les détails suivants :

    - Identificateur : `com.microsoft.wdav.epsext`
    - Type d’identificateur : ID d’offre groupée
    - Conditions requises pour le code : `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. Sélectionnez **+ Ajouter**.

    ![Image de l’entrée tcc epsext du paramètre de configuration.](images/tcc-epsext-entry.png)

    - Sous Application ou service : définir sur **SystemPolicyAllFiles**

    - Sous « accès » : définir sur **Autoriser**

11. Sélectionnez **Enregistrer** (et non celui en bas à droite).

    ![Image du paramètre de configuration tcc epsext image2.](images/tcc-epsext-entry2.png)

12. Sélectionnez **l’onglet** Étendue.

    ![Image de l’étendue du paramètre de configuration.](images/2c49b16cd112729b3719724f581e6882.png)

13. Sélectionnez **+ Ajouter**.

    ![Image de l’image addimage du paramètre de configuration.](images/57cef926d1b9260fb74a5f460cee887a.png)

14. Sélectionnez **Groupes d’ordinateurs** > **sous Nom** de groupe > sélectionnez Groupe MachineGroup de **Contoso.**

    ![Image du paramètre de configuration contoso machinegrp.](images/368d35b3d6179af92ffdbfd93b226b69.png)

15. Sélectionnez **Ajouter**.

16. Sélectionnez **Enregistrer**.

17. Sélectionnez **Terminé**.

    ![Image de donimg des paramètres de configuration.](images/809cef630281b64b8f07f20913b0039b.png)

    ![Image du paramètre de configuration donimg2.](images/6c8b406ee224335a8c65d06953dc756e.png)

Vous pouvez également télécharger [fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) et le télécharger dans les profils de configuration JAMF, comme décrit dans [Deploying Custom Configuration Profiles using Jamf Pro| Méthode 2 : Télécharger profil de configuration à Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>Étape 7 : Approuver l’extension de noyau pour Microsoft Defender pour le point de terminaison

> [!CAUTION]
> Les appareils Apple Silicon (M1) ne supportent pas KEXT. L’installation d’un profil de configuration constitué de stratégies KEXT échoue sur ces appareils.

1. Dans les **profils de configuration,** **sélectionnez + Nouveau**.

    ![Capture d’écran d’un billet de réseau social Description généré automatiquement.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. Entrez les détails suivants :

    **Général**

    - Name: MDATP MDAV Kernel Extension
    - Description : extension de noyau MDATP (kext)
    - Catégorie : Aucun
    - Méthode de distribution : installer automatiquement
    - Niveau : niveau ordinateur

    ![Image du noyau mdatpmdav des paramètres de configuration.](images/24e290f5fc309932cf41f3a280d22c14.png)

3. In **Configure Approved Kernel Extensions** select **Configure**.

    ![Image de l’ext de noyau approuvé des paramètres de configuration.](images/30be88b63abc5e8dde11b73f1b1ade6a.png)

4. Dans **Extensions de noyau approuvées,** entrez les détails suivants :

    - Nom complet : Microsoft Corp.
    - ID d’équipe : UBF8T346G9

    ![Image de l’extension de noyau appr des paramètres de configuration.](images/39cf120d3ac3652292d8d1b6d057bd60.png)

5. Sélectionnez **l’onglet** Étendue.

    ![Image de l’onglet d’étendue des paramètres de configuration img.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. Sélectionnez **+ Ajouter**.

7. Sélectionnez **Groupes d’ordinateurs** > **sous Nom du** > sélectionnez Groupe ordinateur de **Contoso.**

8. Sélectionnez **+ Ajouter**.

    ![L’image des paramètres de configuration ajoute des images.](images/0dde8a4c41110dbc398c485433a81359.png)

9. Sélectionnez **Enregistrer**.

    ![Image de l’économiserie des paramètres de configuration.](images/0add8019b85a453b47fa5c402c72761b.png)

10. Sélectionnez **Terminé**.

    ![Image des paramètres de configuration doneimag.](images/1c9bd3f68db20b80193dac18f33c22d0.png)

Vous pouvez également télécharger [kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) et le télécharger dans les profils de configuration JAMF, comme décrit dans [Deploying Custom Configuration Profiles using Jamf Pro| Méthode 2 : Télécharger profil de configuration à Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>Étape 8 : Approuver les extensions système pour Microsoft Defender pour le point de terminaison

1. Dans les **profils de configuration,** **sélectionnez + Nouveau**.

    ![Capture d’écran d’un billet de réseau social Description généré automatiquement.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. Entrez les détails suivants :

    **Général**

    - Name: MDATP MDAV System Extensions
    - Description : extensions système MDATP
    - Catégorie : Aucun
    - Méthode de distribution : installer automatiquement
    - Niveau : niveau ordinateur

    ![Image du nouveau prof des paramètres de configuration.](images/sysext-new-profile.png)

3. Dans **les extensions système,** **sélectionnez Configurer.**

   ![Image de configuration sysext des paramètres de configuration.](images/sysext-configure.png)

4. Dans **les extensions système,** entrez les détails suivants :

   - Nom complet : Microsoft Corp. System Extensions
   - Types d’extension système : extensions système autorisées
   - Identificateur d’équipe : UBF8T346G9
   - Extensions système autorisées :
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    ![Image des paramètres de configuration sysextconfig2.](images/sysext-configure2.png)

5. Sélectionnez **l’onglet** Étendue.

    ![Image de l’étendue des paramètres de configuration.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. Sélectionnez **+ Ajouter**.

7. Sélectionnez **Groupes d’ordinateurs** > **sous Nom du** > sélectionnez Groupe ordinateur de **Contoso.**

8. Sélectionnez **+ Ajouter**.

   ![Image de l’addima des paramètres de configuration.](images/0dde8a4c41110dbc398c485433a81359.png)

9. Sélectionnez **Enregistrer**.

   ![Image de l’étendue sysext des paramètres de configuration.](images/sysext-scope.png)

10. Sélectionnez **Terminé**.

    ![Image des paramètres de configuration sysext-final.](images/sysext-final.png)

## <a name="step-9-configure-network-extension"></a>Étape 9 : Configurer l’extension réseau

Dans le cadre des fonctionnalités de détection et de réponse des points de terminaison, Microsoft Defender for Endpoint sur macOS inspecte le trafic de socket et signale ces informations au portail Centre de sécurité Microsoft Defender. La stratégie suivante permet à l’extension réseau d’effectuer cette fonctionnalité.

Ces étapes s’appliquent à macOS 10.15 (Genre), ou une nouveauté.

1. Dans le tableau de bord Jamf Pro, **sélectionnez Ordinateurs,** puis **Profils de configuration.**

2. Cliquez **sur** Nouveau, puis entrez les détails suivants pour **options**:

    - Onglet **Général**:
        - **Nom**: Extension réseau Microsoft Defender ATP
        - **Description**: macOS 10.15 (Contrôle) ou une nouveauté
        - **Catégorie**: Aucun *(par défaut)*
        - **Méthode de distribution**: installer automatiquement *(par défaut)*
        - **Niveau**: niveau ordinateur *(par défaut)*

    - Filtre **de contenu d’onglet**:
        - **Nom du** filtre : filtre de contenu Microsoft Defender ATP
        - **Identificateur**: `com.microsoft.wdav`
        - Laisser **l’adresse du service,** **l’organisation,** **le nom d’utilisateur,** le mot de **passe,** **le certificat** vide (**Inclure** *n’est pas* sélectionné)
        - **Filter Order**: Inspector
        - **Filtre de socket**: `com.microsoft.wdav.netext`
        - **Exigence désignée par le filtre de socket**: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - Laisser **les champs Filtre réseau** vides **(Inclure** *n’est pas* sélectionné)

        Notez que **l’identificateur,** le filtre de **socket** et le **filtre de socket désignent** les valeurs exactes requises comme spécifié ci-dessus.

        ![Image du paramètre de configuration mdatpmdav.](images/netext-create-profile.png)

3. Sélectionnez **l’onglet** Étendue.

   ![Image de l’onglet de tabulation des paramètres de configuration.](images/0df36fc308ba569db204ee32db3fb40a.png)

4. Sélectionnez **+ Ajouter**.

5. Sélectionnez **Groupes d’ordinateurs** > **sous Nom du** > sélectionnez Groupe ordinateur de **Contoso.**

6. Sélectionnez **+ Ajouter**.

    ![Image des paramètres de configuration adim.](images/0dde8a4c41110dbc398c485433a81359.png)

7. Sélectionnez **Enregistrer**.

    ![Image des paramètres de configuration savimg netextscop.](images/netext-scope.png)

8. Sélectionnez **Terminé**.

    ![Image des paramètres de configuration netextfinal.](images/netext-final.png)

Vous pouvez également télécharger [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) et le télécharger dans les profils de configuration JAMF, comme décrit dans [Deploying Custom Configuration Profiles using Jamf Pro| Méthode 2 : Télécharger profil de configuration à Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Étape 10 : Planifier des analyses avec Microsoft Defender pour Endpoint sur macOS

Suivez les instructions des [analyses de planification avec Microsoft Defender for Endpoint sur macOS.](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>Étape 11 : Déployer Microsoft Defender pour endpoint sur macOS

1. Accédez à l’endroit où vous avez `wdav.pkg` enregistré.

    ![Image de l’explorateur de fichiers wdav pkg.](images/8dde76b5463047423f8637c86b05c29d.png)

2. Renommons-le `wdav_MDM_Contoso_200329.pkg` .

    ![Image de l’explorateur de fichiers 1 wdavmdmpkg.](images/fb2220fed3a530f4b3ef36f600da0c27.png)

3. Ouvrez le tableau de bord Pro Jamf.

    ![Image des paramètres de configuration jamfpro.](images/990742cd9a15ca9fdd37c9f695d1b9f4.png)

4. Sélectionnez votre ordinateur et cliquez sur l’icône d’engrenage en haut, puis sélectionnez **Gestion de l’ordinateur.**

    ![Image des paramètres de configuration compmgmt.](images/b6d671b2f18b89d96c1c8e2ea1991242.png)

5. Dans **les packages,** **sélectionnez + Nouveau**.
    ![Image contenant une nouvelle description des nouveaux packages généré automatiquement.](images/57aa4d21e2ccc65466bf284701d4e961.png)

6. Dans **le nouveau package,** entrez les détails suivants :

    **Onglet Général**
    - Nom complet : laissez-le vide pour le moment. Parce qu’il sera réinitialisé lorsque vous choisirez votre pkg.
    - Catégorie : Aucun (par défaut)
    - Filename: Choose File

    ![Image de l’onglet général des paramètres de configuration.](images/21de3658bf58b1b767a17358a3f06341.png)

    Ouvrez le fichier et pointer vers `wdav.pkg` ou `wdav_MDM_Contoso_200329.pkg` .

    ![Capture d’écran d’une description d’ordinateur générée automatiquement.](images/1aa5aaa0a387f4e16ce55b66facc77d1.png)

7. Sélectionnez **Ouvrir**. Définissez **le nom complet sur** Microsoft Defender - Protection avancée contre les **menaces et Antivirus Microsoft Defender**.

    **Le fichier manifeste n’est** pas requis. Microsoft Defender pour le point de terminaison fonctionne sans fichier manifeste.

    **Onglet Options**: conserver les valeurs par défaut.

    **Onglet Limitations :** conserver les valeurs par défaut.

     ![Image de l’onglet limitation des paramètres de configuration.](images/56dac54634d13b2d3948ab50e8d3ef21.png)

8. Sélectionnez **Enregistrer**. Le package est téléchargé vers Jamf Pro.

   ![Image des paramètres de configuration pack upl jamf pro.](images/33f1ecdc7d4872555418bbc3efe4b7a3.png)

   Le déploiement du package peut prendre quelques minutes.

   ![Image de l’upl du pack de paramètres de configuration.](images/1626d138e6309c6e87bfaab64f5ccf7b.png)

9. Accédez à la page **Stratégies.**

    ![Image des paramètres de configuration.](images/f878f8efa5ebc92d069f4b8f79f62c7f.png)

10. Sélectionnez **+ Nouveau** pour créer une stratégie.

    ![Image de la nouvelle stratégie des paramètres de configuration.](images/847b70e54ed04787e415f5180414b310.png)


11. En **général,** entrez les détails suivants :

    - Nom complet : MDATP Onboarding Contoso 200329 v100.86.92 ou ultérieur

    ![Image de configuration settingsmdatponboard.](images/625ba6d19e8597f05e4907298a454d28.png)

12. Sélectionnez **l’enregistrement périodique.**

    ![Image des paramètres de configuration récurrent l’checkin.](images/68bdbc5754dfc80aa1a024dde0fce7b0.png)

13. Sélectionnez **Enregistrer**.

14. Sélectionnez **packages > configurer**.

    ![Image du pack de paramètres de configuration configuré.](images/8fb4cc03721e1efb4a15867d5241ebfb.png)

15. Sélectionnez **le bouton** Ajouter en haut de Microsoft Defender - Protection avancée contre les **menaces et Antivirus Microsoft Defender**.

    ![Image des paramètres de configuration ajoutés par MDATP et MDA.](images/526b83fbdbb31265b3d0c1e5fbbdc33a.png)

16. Sélectionnez **Enregistrer**.

    ![Image de configuration settingssavimg.](images/9d6e5386e652e00715ff348af72671c6.png)

17. Sélectionnez **l’onglet** Étendue.

    ![Image de scptab des paramètres de configuration.](images/8d80fe378a31143db9be0bacf7ddc5a3.png)

18. Sélectionnez les ordinateurs cibles.

    ![Image des paramètres de configuration tgtcomp.](images/6eda18a64a660fa149575454e54e7156.png)

    **Scope**

    Sélectionnez **Ajouter**.

    ![Image des paramètres de configuration ad1img.](images/1c08d097829863778d562c10c5f92b67.png)

    ![Image des paramètres de configuration ad2img.](images/216253cbfb6ae738b9f13496b9c799fd.png)

    **Libre-service**

    ![Image des paramètres de configuration en libre-service.](images/c9f85bba3e96d627fe00fc5a8363b83a.png)

19. Sélectionnez **Terminé**.

    ![Image des paramètres de configuration do1img.](images/99679a7835b0d27d0a222bc3fdaf7f3b.png)

    ![Image des paramètres de configuration do2img.](images/632aaab79ae18d0d2b8e0c16b6ba39e2.png)
