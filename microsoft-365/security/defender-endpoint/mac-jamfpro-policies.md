---
title: Configurer le Microsoft Defender pour point de terminaison sur les stratégies macOS dans Jamf Pro
description: Découvrez comment configurer le Microsoft Defender pour point de terminaison sur les stratégies macOS dans Jamf Pro
keywords: policies, microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: bafbce373ffdbdd8d5d7e4908f626d45282159c8
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68228622"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Configurer le Microsoft Defender pour point de terminaison sur les stratégies macOS dans Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Cette page vous guide tout au long des étapes à suivre pour configurer des stratégies macOS dans Jamf Pro.

Vous devez effectuer les étapes suivantes :

1. [Obtenir le package d’intégration Microsoft Defender pour point de terminaison](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Créer un profil de configuration dans Jamf Pro à l’aide du package d’intégration](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Configurer les paramètres Microsoft Defender pour point de terminaison](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Configurer les paramètres de notification Microsoft Defender pour point de terminaison](#step-4-configure-notifications-settings)
5. [Configurer Microsoft AutoUpdate (MAU)](#step-5-configure-microsoft-autoupdate-mau)
6. [Accorder un accès disque complet à Microsoft Defender pour point de terminaison](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Approuver l’extension de noyau pour Microsoft Defender pour point de terminaison](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Approuver les extensions système pour Microsoft Defender pour point de terminaison](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Configurer l’extension réseau](#step-9-configure-network-extension)
10. [Planifier des analyses avec Microsoft Defender pour point de terminaison sur macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [Déployer Microsoft Defender pour point de terminaison sur macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>Étape 1 : Obtenir le package d’intégration Microsoft Defender pour point de terminaison

1. Dans [Microsoft 365 Defender](https://security.microsoft.com), accédez à **Paramètres > Points de terminaison > Intégration**.

2. Sélectionnez macOS comme système d’exploitation et Mobile Gestion des appareils/Microsoft Intune comme méthode de déploiement.

   :::image type="content" source="images/onboarding-macos.png" alt-text="Page Paramètres du Centre de sécurité Microsoft Defender" lightbox="images/onboarding-macos.png":::

3. Sélectionnez **Télécharger le package d’intégration** (WindowsDefenderATPOnboardingPackage.zip).

4. Extraire `WindowsDefenderATPOnboardingPackage.zip`.

5. Copiez le fichier à l’emplacement de votre choix. Par exemple : `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>Étape 2 : Créer un profil de configuration dans Jamf Pro à l’aide du package d’intégration

1. Recherchez le fichier `WindowsDefenderATPOnboarding.plist` de la section précédente.

   :::image type="content" source="images/plist-onboarding-file.png" alt-text="Le fichier d’intégration ATP Windows Defender" lightbox="images/plist-onboarding-file.png":::

2. Connectez-vous à Jamf Pro, **accédez aux profils de configuration des ordinateurs** > , puis sélectionnez **Nouveau**.

   :::image type="content" source="images/jamf-pro-configure-profile.png" alt-text="Page sur laquelle vous créez un tableau de bord Jamf Pro" lightbox="images/jamf-pro-configure-profile.png":::

3. Entrez les détails suivants :

   **Général** :

   - Nom : intégration MDE pour macOS
   - Description : Intégration de MDE EDR pour macOS
   - Catégorie : Aucun
   - Méthode de distribution : Installer automatiquement
   - Niveau : Niveau de l’ordinateur

4.  Accédez à la page **Application & Paramètres personnalisés** , puis **sélectionnez Charger** > **ajouter**.

   :::image type="content" source="images/jamfpro-mac-profile.png" alt-text="Configurer l’application et les paramètres personnalisés" lightbox="images/jamfpro-mac-profile.png":::

5. Sélectionnez **Charger le fichier (fichier PLIST),** puis dans **Domaine de préférence** , entrez : `com.microsoft.wdav.atp`.

   :::image type="content" source="images/jamfpro-plist-upload.png" alt-text="Fichier de chargement jamfpro plist" lightbox="images/jamfpro-plist-upload.png":::

   :::image type="content" source="images/jamfpro-plist-file.png" alt-text="Fichier de liste de propriétés de fichier de chargement" lightbox="images/jamfpro-plist-file.png":::

6. Sélectionnez **Ouvrir** , puis sélectionnez le fichier d’intégration.

   :::image type="content" source="images/jamfpro-plist-file-onboard.png" alt-text="Fichier d’intégration" lightbox="images/jamfpro-plist-file-onboard.png":::

7. Sélectionnez **Télécharger**.

   :::image type="content" source="images/jamfpro-upload-plist.png" alt-text="Fichier plist de chargement" lightbox="images/jamfpro-upload-plist.png":::

8. Sélectionnez l’onglet **Étendue** .

   :::image type="content" source="images/jamfpro-scope-tab.png" alt-text="Onglet Étendue" lightbox="images/jamfpro-scope-tab.png":::

9. Sélectionnez les ordinateurs cibles.

   :::image type="content" source="images/jamfpro-target-computer.png" alt-text="Les ordinateurs cibles" lightbox="images/jamfpro-target-computer.png":::

   :::image type="content" source="images/jamfpro-targets.png" alt-text="Les cibles" lightbox="images/jamfpro-targets.png":::

10. Sélectionnez **Enregistrer**.

   :::image type="content" source="images/jamfpro-deployment-target.png" alt-text="Déploiement d’ordinateurs cibles" lightbox="images/jamfpro-deployment-target.png":::

   :::image type="content" source="images/jamfpro-target-selected.png" alt-text="Sélection des ordinateurs cibles" lightbox="images/jamfpro-target-selected.png":::

11. Sélectionnez **Terminé**.

    :::image type="content" source="images/jamfpro-target-group.png" alt-text="Ordinateurs d’un groupe cible" lightbox="images/jamfpro-target-group.png":::

    :::image type="content" source="images/jamfpro-configuration-policies.png" alt-text="Liste des profils de configuration" lightbox="images/jamfpro-configuration-policies.png":::

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>Étape 3 : Configurer Microsoft Defender pour point de terminaison paramètres

Vous pouvez utiliser JAMF Pro GUI pour modifier les paramètres individuels de la configuration Microsoft Defender pour point de terminaison, ou utiliser la méthode héritée en créant une liste Plist de configuration dans un éditeur de texte et en la chargeant dans JAMF Pro.

Notez que vous devez utiliser exact `com.microsoft.wdav` comme **domaine de préférence**, Microsoft Defender pour point de terminaison utilise uniquement ce nom et `com.microsoft.wdav.ext` pour charger ses paramètres managés !

(La `com.microsoft.wdav.ext` version peut être utilisée dans de rares cas lorsque vous préférez utiliser la méthode GUI, mais que vous devez également configurer un paramètre qui n’a pas encore été ajouté au schéma.)

### <a name="gui-method"></a>Méthode GUI

1. Téléchargez le fichier schema.json à partir [du dépôt GitHub de Defender](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) et enregistrez-le dans un fichier local :

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Créez un profil de configuration sous Ordinateurs -> Profils de configuration, entrez les détails suivants sous l’onglet **Général** :

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Un nouveau profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

    - Nom : paramètres de configuration MDAV MDATP
    - Description:\<blank\>
    - Catégorie : Aucun (valeur par défaut)
    - Niveau : Niveau de l’ordinateur (par défaut)
    - Méthode de distribution : Installer automatiquement (par défaut)

3. Faites défiler jusqu’à l’onglet **Application & Paramètres personnalisés** , sélectionnez **Applications externes**, cliquez sur **Ajouter** et utiliser le **schéma personnalisé** comme source pour le domaine de préférence.

   :::image type="content" source="images/4137189bc3204bb09eed3aabc41afd78.png" alt-text="Ajouter un schéma personnalisé" lightbox="images/4137189bc3204bb09eed3aabc41afd78.png":::

4. Entrez `com.microsoft.wdav` comme domaine de préférence, cliquez sur **Ajouter un schéma** et **chargez** le fichier schema.json téléchargé à l’étape 1. Cliquez sur **Enregistrer**.

   :::image type="content" source="images/a6f9f556037c42fabcfdcb1b697244cf.png" alt-text="Charger le schéma" lightbox="images/a6f9f556037c42fabcfdcb1b697244cf.png":::

5. Vous pouvez voir tous les paramètres de configuration Microsoft Defender pour point de terminaison pris en charge ci-dessous, sous **Propriétés du domaine préférence**. Cliquez sur **Ajouter/Supprimer des propriétés** pour sélectionner les paramètres que vous souhaitez gérer, puis cliquez sur **Ok** pour enregistrer vos modifications. (Les paramètres non sélectionnés ne seront pas inclus dans la configuration managée, un utilisateur final sera en mesure de configurer ces paramètres sur leurs machines.)

   :::image type="content" source="images/817b3b760d11467abe9bdd519513f54f.png" alt-text="Paramètres managés choisis" lightbox="images/817b3b760d11467abe9bdd519513f54f.png":::

6. Remplacez les valeurs des paramètres par les valeurs souhaitées. Vous pouvez cliquer sur **Plus d’informations** pour obtenir la documentation d’un paramètre particulier. (Vous pouvez cliquer sur **Plist preview** pour inspecter à quoi ressemblera la liste plist de configuration. Cliquez sur **l’éditeur de formulaire** pour revenir à l’éditeur visuel.)

   :::image type="content" source="images/a14a79efd5c041bb8974cb5b12b3a9b6.png" alt-text="Page sur laquelle vous modifiez les valeurs de paramètres" lightbox="images/a14a79efd5c041bb8974cb5b12b3a9b6.png":::

7. Sélectionnez l’onglet **Étendue** .

   :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Étendue du profil de configuration" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

8. Sélectionnez le **groupe d’ordinateurs de Contoso**.

9. Sélectionnez **Ajouter**, puis **Enregistrer**.

   :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Page sur laquelle vous pouvez ajouter les paramètres de configuration" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

   :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Page sur laquelle vous pouvez enregistrer les paramètres de configuration" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

10. Sélectionnez **Terminé**. Le nouveau **profil de configuration** s’affiche.

    :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Page sur laquelle vous complétez les paramètres de configuration" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

Microsoft Defender pour point de terminaison ajoute de nouveaux paramètres au fil du temps. Ces nouveaux paramètres seront ajoutés au schéma et une nouvelle version sera publiée sur GitHub.
Il vous suffit de télécharger un schéma mis à jour, de modifier le profil de configuration existant et de **modifier le schéma** sous l’onglet **Application & Paramètres personnalisés** .

### <a name="legacy-method"></a>Méthode héritée

1. Utilisez les paramètres de configuration Microsoft Defender pour point de terminaison suivants :

    - enableRealTimeProtection
    - passiveMode

    > [!NOTE]
    > Non activé par défaut, si vous envisagez d’exécuter un av tiers pour macOS, définissez-le `true`sur .

    - Exclusions
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - exclusionsMergePolicy
    - allowedThreats

    > [!NOTE]
    > EICAR est sur l’exemple, si vous passez par une preuve de concept, supprimez-le surtout si vous testez EICAR.

    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - étiquettes
    - hideStatusMenuIcon

     Pour plus d’informations, consultez [la liste des propriétés pour le profil de configuration complet JAMF](mac-preferences.md#property-list-for-jamf-full-configuration-profile).

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

2. Enregistrez le fichier sous `MDATP_MDAV_configuration_settings.plist`.

3. Dans le tableau de bord Jamf Pro, **ouvrez Ordinateurs** et leurs **profils de configuration**. Cliquez sur **Nouveau** et basculez vers l’onglet **Général** .

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Page affichant un nouveau profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

4. Entrez les détails suivants :

    **Général**

    - Nom : paramètres de configuration MDAV MDATP
    - Description:\<blank\>
    - Catégorie : Aucun (valeur par défaut)
    - Méthode de distribution : Installer automatiquement (par défaut)
    - Niveau : Niveau de l’ordinateur (par défaut)

    :::image type="content" source="images/3160906404bc5a2edf84d1d015894e3b.png" alt-text="Paramètres de configuration MDATP MDAV" lightbox="images/3160906404bc5a2edf84d1d015894e3b.png":::

5. Dans **Application & Paramètres personnalisés** , **sélectionnez Configurer**.

   :::image type="content" source="images/e1cc1e48ec9d5d688087b4d771e668d2.png" alt-text="Application et paramètres personnalisés" lightbox="images/e1cc1e48ec9d5d688087b4d771e668d2.png":::

6. Sélectionnez **Charger le fichier (fichier PLIST).**

   :::image type="content" source="images/6f85269276b2278eca4bce84f935f87b.png" alt-text="Fichier plist des paramètres de configuration" lightbox="images/6f85269276b2278eca4bce84f935f87b.png":::

7. Dans **Domaine préférences**, entrez `com.microsoft.wdav`, puis  **sélectionnez Charger le fichier PLIST**.

   :::image type="content" source="images/db15f147dd959e872a044184711d7d46.png" alt-text="Domaine des préférences des paramètres de configuration" lightbox="images/db15f147dd959e872a044184711d7d46.png":::

8. **Sélectionnez Choisir un fichier**.

    :::image type="content" source="images/526e978761fc571cca06907da7b01fd6.png" alt-text="Invite à choisir le fichier plist" lightbox="images/526e978761fc571cca06907da7b01fd6.png":::

9. Sélectionnez le **fichier MDATP_MDAV_configuration_settings.plist**, puis **ouvrez**.

   :::image type="content" source="images/98acea3750113b8dbab334296e833003.png" alt-text="Paramètres de configuration mdatpmdav" lightbox="images/98acea3750113b8dbab334296e833003.png":::

10. Sélectionnez **Télécharger**.

    :::image type="content" source="images/0adb21c13206861ba9b30a879ade93d3.png" alt-text="Chargement du paramètre de configuration" lightbox="images/0adb21c13206861ba9b30a879ade93d3.png":::

    :::image type="content" source="images/f624de59b3cc86e3e2d32ae5de093e02.png" alt-text="Invite à charger l’image liée aux paramètres de configuration" lightbox="images/f624de59b3cc86e3e2d32ae5de093e02.png":::

    > [!NOTE]
    > Si vous chargez le fichier Intune, vous obtenez l’erreur suivante :
    >
    > :::image type="content" source="images/8e69f867664668796a3b2904896f0436.png" alt-text="Invite à charger le fichier intune lié aux paramètres de configuration" lightbox="images/8e69f867664668796a3b2904896f0436.png":::

11. Sélectionnez **Enregistrer**.

    :::image type="content" source="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png" alt-text="Option permettant d’enregistrer l’image liée aux paramètres de configuration" lightbox="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png":::

12. Le fichier est chargé.

    :::image type="content" source="images/33e2b2a1611fdddf6b5b79e54496e3bb.png" alt-text="Fichier téléchargé lié aux paramètres de configuration" lightbox="images/33e2b2a1611fdddf6b5b79e54496e3bb.png":::

    :::image type="content" source="images/a422e57fe8d45689227e784443e51bd1.png" alt-text="Page paramètres de configuration" lightbox="images/a422e57fe8d45689227e784443e51bd1.png":::

13. Sélectionnez l’onglet **Étendue** .

    :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Étendue des paramètres de configuration" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

14. Sélectionnez le **groupe d’ordinateurs de Contoso**.

15. Sélectionnez **Ajouter**, puis **Enregistrer**.

    :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Les paramètres de configuration addsav" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

    :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Notification des paramètres de configuration" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

16. Sélectionnez **Terminé**. Le nouveau **profil de configuration** s’affiche.

    ![Image de l’image de profil de configuration des paramètres de configuration.](images/dd55405106da0dfc2f50f8d4525b01c8.png)
     :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Paramètres du profil de configuration" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

## <a name="step-4-configure-notifications-settings"></a>Étape 4 : Configurer les paramètres des notifications

Ces étapes s’appliquent à macOS 10.15 (Catalina) ou version ultérieure.

1. Dans le tableau de bord Jamf Pro, sélectionnez **Ordinateurs**, puis **Profils de configuration**.

2. Cliquez sur **Nouveau**, puis entrez les détails suivants pour **Options** :

    - **Onglet Général** :
        - **Nom** : Paramètres de notification MDAV MDATP
        - **Description** : macOS 10.15 (Catalina) ou version ultérieure
        - **Catégorie** : Aucun *(valeur par défaut)*
        - **Méthode de distribution** : Installer automatiquement *(par défaut)*
        - **Niveau** : Niveau de l’ordinateur *(par défaut)*

        :::image type="content" source="images/c9820a5ff84aaf21635c04a23a97ca93.png" alt-text="Nouvelle page de profil de configuration macOS" lightbox="images/c9820a5ff84aaf21635c04a23a97ca93.png":::

    - **Tabulation Notifications**, cliquez sur **Ajouter**, puis entrez les valeurs suivantes :
        - **ID de bundle** : `com.microsoft.wdav.tray`
        - **Alertes critiques** : cliquez sur **Désactiver**
        - **Notifications** : Cliquez sur **Activer**
        - **Type d’alerte de bannière** : Sélectionner **Inclure** et **Temporaire** *(par défaut)*
        - **Notifications sur l’écran de verrouillage** : Cliquez sur **Masquer**
        - **Notifications dans le Centre de notifications** : cliquez sur **Afficher**
        - **Icône de l’application badge** : Cliquez sur **Afficher**

        :::image type="content" source="images/7f9138053dbcbf928e5182ee7b295ebe.png" alt-text="La barre d’état des notifications mdatpmdav des paramètres de configuration" lightbox="images/7f9138053dbcbf928e5182ee7b295ebe.png":::

    - **Notifications** de tabulation, cliquez sur **Ajouter** une fois de plus, faites défiler jusqu’aux **nouveaux paramètres de notifications**
        - **ID de bundle** : `com.microsoft.autoupdate.fba`
        - Configurer le reste des paramètres sur les mêmes valeurs que ci-dessus

        :::image type="content" source="images/4bac6ce277aedfb4a674f2d9fcb2599a.png" alt-text="Les paramètres de configuration mdatpmdav notifications mau" lightbox="images/4bac6ce277aedfb4a674f2d9fcb2599a.png":::

        Notez que vous disposez maintenant de deux « tables » avec des configurations de notification, une pour **l’ID de bundle : com.microsoft.wdav.tray** et une autre pour **l’ID de bundle : com.microsoft.autoupdate.fba**. Bien que vous puissiez configurer les paramètres d’alerte en fonction de vos besoins, les ID de bundle doivent être exactement les mêmes que ceux décrits précédemment, et le commutateur **Inclure** doit être **activé** pour **les notifications**.

3. Sélectionnez l’onglet **Étendue** , puis **sélectionnez Ajouter**.

   :::image type="content" source="images/441aa2ecd36abadcdd8aed03556080b5.png" alt-text="Page sur laquelle vous pouvez ajouter des valeurs pour les paramètres de configuration" lightbox="images/441aa2ecd36abadcdd8aed03556080b5.png":::

4. Sélectionnez le **groupe d’ordinateurs de Contoso**.

5. Sélectionnez **Ajouter**, puis **Enregistrer**.

   :::image type="content" source="images/09a275e321268e5e3ac0c0865d3e2db5.png" alt-text="Page sur laquelle vous pouvez enregistrer des valeurs pour le groupe d’ordinateurs contoso des paramètres de configuration" lightbox="images/09a275e321268e5e3ac0c0865d3e2db5.png":::

   :::image type="content" source="images/4d2d1d4ee13d3f840f425924c3df0d51.png" alt-text="Page qui affiche la notification d’achèvement des paramètres de configuration" lightbox="images/4d2d1d4ee13d3f840f425924c3df0d51.png":::

6. Sélectionnez **Terminé**. Le nouveau **profil de configuration** s’affiche.

   :::image type="content" source="images/633ad26b8bf24ec683c98b2feb884bdf.png" alt-text="Paramètres de configuration terminés" lightbox="images/633ad26b8bf24ec683c98b2feb884bdf.png":::

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>Étape 5 : Configurer Microsoft AutoUpdate (MAU)

1. Utilisez les paramètres de configuration Microsoft Defender pour point de terminaison suivants :

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

2. Enregistrez-le sous `MDATP_MDAV_MAU_settings.plist`.

3. Dans le tableau de bord Jamf Pro, sélectionnez **Général**.

   :::image type="content" source="images/eaba2a23dd34f73bf59e826217ba6f15.png" alt-text="Paramètres de configuration" lightbox="images/eaba2a23dd34f73bf59e826217ba6f15.png":::

4. Entrez les détails suivants :

    **Général**

    - Nom : Paramètres MDATP MDAV MAU
    - Description : Paramètres de mise à jour automatique Microsoft pour MDATP pour macOS
    - Catégorie : Aucun (valeur par défaut)
    - Méthode de distribution : Installer automatiquement (par défaut)
    - Niveau : Niveau de l’ordinateur (par défaut)

5. Dans **Application & Paramètres personnalisés** , **sélectionnez Configurer**.

   :::image type="content" source="images/1f72e9c15eaafcabf1504397e99be311.png" alt-text="Application de paramètre de configuration et paramètres personnalisés" lightbox="images/1f72e9c15eaafcabf1504397e99be311.png":::

6. Sélectionnez **Charger le fichier (fichier PLIST).**

7. Dans **Domaine de préférence** , entrez : `com.microsoft.autoupdate2`, puis **sélectionnez Charger le fichier PLIST**.

   :::image type="content" source="images/1213872db5833aa8be535da57653219f.png" alt-text="Domaine de préférence de paramètre de configuration" lightbox="images/1213872db5833aa8be535da57653219f.png":::
    

8. **Sélectionnez Choisir un fichier**.

   :::image type="content" source="images/335aff58950ce62d1dabc289ecdce9ed.png" alt-text="Invite à choisir le fichier concernant le paramètre de configuration" lightbox="images/335aff58950ce62d1dabc289ecdce9ed.png":::

9. Sélectionnez **MDATP_MDAV_MAU_settings.plist**.

   :::image type="content" source="images/a26bd4967cd54bb113a2c8d32894c3de.png" alt-text="Paramètres mdatpmdavmau" lightbox="images/a26bd4967cd54bb113a2c8d32894c3de.png":::

10. Sélectionnez **Télécharger**.
    :::image type="content" source="images/4239ca0528efb0734e4ca0b490bfb22d.png" alt-text="Chargement du fichier concernant le paramètre de configuration" lightbox="images/4239ca0528efb0734e4ca0b490bfb22d.png":::

    :::image type="content" source="images/4ec20e72c8aed9a4c16912e01692436a.png" alt-text="Page affichant l’option de chargement du fichier concernant le paramètre de configuration" lightbox="images/4ec20e72c8aed9a4c16912e01692436a.png":::

11. Sélectionnez **Enregistrer**.

    :::image type="content" source="images/253274b33e74f3f5b8d475cf8692ce4e.png" alt-text="Page affichant l’option Enregistrer pour le fichier concernant le paramètre de configuration" lightbox="images/253274b33e74f3f5b8d475cf8692ce4e.png":::

12. Sélectionnez l’onglet **Étendue** .

    :::image type="content" source="images/10ab98358b2d602f3f67618735fa82fb.png" alt-text="Onglet Étendue des paramètres de configuration" lightbox="images/10ab98358b2d602f3f67618735fa82fb.png":::

13. Sélectionnez **Ajouter**.

    :::image type="content" source="images/56e6f6259b9ce3c1706ed8d666ae4947.png" alt-text="Option permettant d’ajouter des cibles de déploiement" lightbox="images/56e6f6259b9ce3c1706ed8d666ae4947.png":::

    :::image type="content" source="images/38c67ee1905c4747c3b26c8eba57726b.png" alt-text="Page sur laquelle vous ajoutez d’autres valeurs aux paramètres de configuration" lightbox="images/38c67ee1905c4747c3b26c8eba57726b.png":::

    :::image type="content" source="images/321ba245f14743c1d5d51c15e99deecc.png" alt-text="Page sur laquelle vous pouvez ajouter d’autres valeurs aux paramètres de configuration" lightbox="images/321ba245f14743c1d5d51c15e99deecc.png":::

14. Sélectionnez **Terminé**.

    :::image type="content" source="images/ba44cdb77e4781aa8b940fb83e3c21f7.png" alt-text="Notification d’achèvement concernant les paramètres de configuration" lightbox="images/ba44cdb77e4781aa8b940fb83e3c21f7.png":::

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>Étape 6 : Accorder un accès disque complet à Microsoft Defender pour point de terminaison

1. Dans le tableau de bord Jamf Pro, sélectionnez **Profils de configuration**.

   :::image type="content" source="images/264493cd01e62c7085659d6fdc26dc91.png" alt-text="Profil pour lequel les paramètres doivent être configurés" lightbox="images/264493cd01e62c7085659d6fdc26dc91.png":::

2. Sélectionnez **+ Nouveau**.

3. Entrez les détails suivants :

    **Général**
    - Nom : MDATP MDAV - Accorder l’accès disque complet à EDR et AV
    - Description : Sur macOS Catalina ou version ultérieure, le nouveau contrôle de stratégie préférences de confidentialité
    - Catégorie : Aucun
    - Méthode de distribution : Installer automatiquement
    - Niveau : Niveau de l’ordinateur

    :::image type="content" source="images/ba3d40399e1a6d09214ecbb2b341923f.png" alt-text="Paramètre de configuration en général" lightbox="images/ba3d40399e1a6d09214ecbb2b341923f.png":::
    

4. Dans **Configurer le contrôle de stratégie préférences de confidentialité** , **sélectionnez Configurer**.

   :::image type="content" source="images/715ae7ec8d6a262c489f94d14e1e51bb.png" alt-text="Contrôle de la stratégie de confidentialité de configuration" lightbox="images/715ae7ec8d6a262c489f94d14e1e51bb.png":::

5. Dans **le contrôle de stratégie préférences de confidentialité**, entrez les informations suivantes :

    - Identificateur: `com.microsoft.wdav`
    - Type d’identificateur : ID de bundle
    - Exigence de code : `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    :::image type="content" source="images/22cb439de958101c0a12f3038f905b27.png" alt-text="Détails du contrôle de stratégie de préférence de confidentialité du paramètre de configuration" lightbox="images/22cb439de958101c0a12f3038f905b27.png":::

6. Sélectionnez **+ Ajouter**.

   :::image type="content" source="images/bd93e78b74c2660a0541af4690dd9485.png" alt-text="Le paramètre de configuration ajoute l’option stratégie système tous les fichiers" lightbox="images/bd93e78b74c2660a0541af4690dd9485.png":::

    - Sous Application ou service : définir sur **SystemPolicyAllFiles**

    - Sous « access » : définir sur **Autoriser**

7. Sélectionnez **Enregistrer** (pas celui situé en bas à droite).

   :::image type="content" source="images/6de50b4a897408ddc6ded56a09c09fe2.png" alt-text="Opération d’enregistrement pour le paramètre de configuration" lightbox="images/6de50b4a897408ddc6ded56a09c09fe2.png":::

8. Cliquez sur le `+` signe en regard **d’App Access** pour ajouter une nouvelle entrée.

   :::image type="content" source="images/tcc-add-entry.png" alt-text="Opération d’enregistrement relative au paramètre de configuration" lightbox="images/tcc-add-entry.png":::

9. Entrez les détails suivants :

    - Identificateur: `com.microsoft.wdav.epsext`
    - Type d’identificateur : ID de bundle
    - Exigence de code : `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. Sélectionnez **+ Ajouter**.

    :::image type="content" source="images/tcc-epsext-entry.png" alt-text="Entrée tcc epsext du paramètre de configuration" lightbox="images/tcc-epsext-entry.png":::

    - Sous Application ou service : définir sur **SystemPolicyAllFiles**

    - Sous « access » : définir sur **Autoriser**

11. Sélectionnez **Enregistrer** (pas celui situé en bas à droite).

    :::image type="content" source="images/tcc-epsext-entry2.png" alt-text="L’autre instance du paramètre de configuration tcc epsext" lightbox="images/tcc-epsext-entry2.png":::

12. Sélectionnez l’onglet **Étendue** .

    :::image type="content" source="images/2c49b16cd112729b3719724f581e6882.png" alt-text="Page illustrant l’étendue du paramètre de configuration" lightbox="images/2c49b16cd112729b3719724f581e6882.png":::

13. Sélectionnez **+ Ajouter**.

    :::image type="content" source="images/57cef926d1b9260fb74a5f460cee887a.png" alt-text="Page illustrant le paramètre de configuration" lightbox="images/57cef926d1b9260fb74a5f460cee887a.png":::

14. Sélectionnez **Groupes d’ordinateurs** > sous **Nom de groupe** > sélectionnez **MachineGroup de Contoso**.

    :::image type="content" source="images/368d35b3d6179af92ffdbfd93b226b69.png" alt-text="Groupe d’ordinateurs contoso de paramètre de configuration" lightbox="images/368d35b3d6179af92ffdbfd93b226b69.png":::

15. Sélectionnez **Ajouter**.

16. Sélectionnez **Enregistrer**.

17. Sélectionnez **Terminé**.

    :::image type="content" source="images/809cef630281b64b8f07f20913b0039b.png" alt-text="Le paramètre de configuration contoso machine-group" lightbox="images/809cef630281b64b8f07f20913b0039b.png":::

    :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Illustration du paramètre de configuration" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

Vous pouvez également télécharger [fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) et le charger dans les profils de configuration JAMF, comme décrit dans [Déploiement de profils de configuration personnalisés à l’aide de Jamf Pro| Méthode 2 : Charger un profil de configuration dans Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>Étape 7 : Approuver l’extension de noyau pour Microsoft Defender pour point de terminaison

> [!CAUTION]
> Les appareils Apple Silicon (M1) ne prennent pas en charge KEXT. L’installation d’un profil de configuration constitué de stratégies KEXT échoue sur ces appareils.

1. Dans les **profils de configuration**, sélectionnez **+ Nouveau**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="La description du billet de réseau social générée automatiquement" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Entrez les détails suivants :

    **Général**

    - Nom : Extension du noyau MDATP MDAV
    - Description : Extension du noyau MDATP (kext)
    - Catégorie : Aucun
    - Méthode de distribution : Installer automatiquement
    - Niveau : Niveau de l’ordinateur

    :::image type="content" source="images/24e290f5fc309932cf41f3a280d22c14.png" alt-text="Noyau mdatpmdav des paramètres de configuration" lightbox="images/24e290f5fc309932cf41f3a280d22c14.png":::

3. Dans **Configurer les extensions de noyau approuvées** , **sélectionnez Configurer**.

   :::image type="content" source="images/30be88b63abc5e8dde11b73f1b1ade6a.png" alt-text="Page affichant les extensions de noyau approuvées pour les paramètres de configuration" lightbox="images/30be88b63abc5e8dde11b73f1b1ade6a.png":::

4. Dans **Les extensions de noyau approuvées** , entrez les détails suivants :

    - Nom d’affichage : Microsoft Corp.
    - ID d’équipe : UBF8T346G9

    :::image type="content" source="images/39cf120d3ac3652292d8d1b6d057bd60.png" alt-text="Volet Extensions de noyau approuvées" lightbox="images/39cf120d3ac3652292d8d1b6d057bd60.png":::

5. Sélectionnez l’onglet **Étendue** .

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Onglet Étendue de la configuration" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Sélectionnez **+ Ajouter**.

7. Sélectionnez **Groupes d’ordinateurs** > sous **Nom de groupe** > sélectionnez Le **groupe d’ordinateurs de Contoso**.

8. Sélectionnez **+ Ajouter**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Page sur laquelle vous définissez des valeurs supplémentaires pour les paramètres de configuration" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Sélectionnez **Enregistrer**.

   :::image type="content" source="images/0add8019b85a453b47fa5c402c72761b.png" alt-text="Extension du noyau MDATP MDAV" lightbox="images/0add8019b85a453b47fa5c402c72761b.png":::

10. Sélectionnez **Terminé**.

    :::image type="content" source="images/1c9bd3f68db20b80193dac18f33c22d0.png" alt-text="Page détails des profils de configuration" lightbox="images/1c9bd3f68db20b80193dac18f33c22d0.png":::

Vous pouvez également télécharger [kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) et le charger dans les profils de configuration JAMF, comme décrit dans [Déploiement de profils de configuration personnalisés à l’aide de Jamf Pro| Méthode 2 : Charger un profil de configuration dans Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>Étape 8 : Approuver les extensions système pour Microsoft Defender pour point de terminaison

1. Dans les **profils de configuration**, sélectionnez **+ Nouveau**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Description du billet de réseau social généré automatiquement" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Entrez les détails suivants :

    **Général**

    - Nom : Extensions système MDATP MDAV
    - Description : Extensions système MDATP
    - Catégorie : Aucun
    - Méthode de distribution : Installer automatiquement
    - Niveau : Niveau de l’ordinateur

    :::image type="content" source="images/sysext-new-profile.png" alt-text="Les paramètres de configuration sysext nouveau profil" lightbox="images/sysext-new-profile.png":::

3. Dans **Extensions système** , sélectionnez **Configurer**.

   :::image type="content" source="images/sysext-configure.png" alt-text="Volet avec l’option Configurer pour les extensions système" lightbox="images/sysext-configure.png":::

4. Dans **les extensions système** , entrez les détails suivants :

   - Nom d’affichage : Extensions système Microsoft Corp.
   - Types d’extensions système : extensions système autorisées
   - Identificateur d’équipe : UBF8T346G9
   - Extensions système autorisées :
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    :::image type="content" source="images/sysext-configure2.png" alt-text="Volet Extensions système MDATP MDAV" lightbox="images/sysext-configure2.png":::

5. Sélectionnez l’onglet **Étendue** .

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Volet de sélection Ordinateurs cibles" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Sélectionnez **+ Ajouter**.

7. Sélectionnez **Groupes d’ordinateurs** > sous **Nom de groupe** > sélectionnez Le **groupe d’ordinateurs de Contoso**.

8. Sélectionnez **+ Ajouter**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Volet Nouveau profil de configuration macOS" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Sélectionnez **Enregistrer**.

   :::image type="content" source="images/sysext-scope.png" alt-text="Affichage des options relatives aux extensions système MDAV MDATP" lightbox="images/sysext-scope.png":::

10. Sélectionnez **Terminé**.

    :::image type="content" source="images/sysext-final.png" alt-text="Les paramètres de configuration sysext - final" lightbox="images/sysext-final.png":::

## <a name="step-9-configure-network-extension"></a>Étape 9 : Configurer l’extension réseau

Dans le cadre des fonctionnalités de détection et de réponse des points de terminaison, Microsoft Defender pour point de terminaison sur macOS inspecte le trafic de socket et signale ces informations au portail Microsoft 365 Defender. La stratégie suivante permet à l’extension réseau d’effectuer cette fonctionnalité.

Ces étapes s’appliquent à macOS 10.15 (Catalina) ou version ultérieure.

1. Dans le tableau de bord Jamf Pro, sélectionnez **Ordinateurs**, puis **Profils de configuration**.

2. Cliquez sur **Nouveau**, puis entrez les détails suivants pour **Options** :

    - **Onglet Général** :
        - **Nom** : extension réseau Microsoft Defender
        - **Description** : macOS 10.15 (Catalina) ou version ultérieure
        - **Catégorie** : Aucun *(valeur par défaut)*
        - **Méthode de distribution** : Installer automatiquement *(par défaut)*
        - **Niveau** : Niveau de l’ordinateur *(par défaut)*

    - **Filtre de contenu** de tabulation :
        - **Nom du filtre** : filtre de contenu Microsoft Defender
        - **Identificateur** : `com.microsoft.wdav`
        - Laisser **l’adresse du service**, **l’organisation**, **le nom d’utilisateur**, le **mot de passe**, le **certificat** vide (**Inclure** *n’est pas* sélectionné)
        - **Ordre de filtre** : Inspecteur
        - **Filtre de socket :**`com.microsoft.wdav.netext`
        - **Condition requise désignée pour le filtre de socket** : `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - Laisser les champs **de filtre réseau** vides (**Inclure** *n’est pas* sélectionné)

        Notez que les valeurs exactes de spécification de **l’identificateur**, **du filtre de socket** et du **filtre de socket désigné** , comme spécifié ci-dessus.

        :::image type="content" source="images/netext-create-profile.png" alt-text="Paramètre de configuration mdatpmdav" lightbox="images/netext-create-profile.png":::

3. Sélectionnez l’onglet **Étendue** .

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Onglet Sco des paramètres de configuration" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

4. Sélectionnez **+ Ajouter**.

5. Sélectionnez **Groupes d’ordinateurs** > sous **Nom de groupe** > sélectionnez Le **groupe d’ordinateurs de Contoso**.

6. Sélectionnez **+ Ajouter**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Les paramètres de configuration adim" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

7. Sélectionnez **Enregistrer**.

   :::image type="content" source="images/netext-scope.png" alt-text="Volet Filtre de contenu" lightbox="images/netext-scope.png":::

8. Sélectionnez **Terminé**.

   :::image type="content" source="images/netext-final.png" alt-text="Le texte des paramètres de configuration - final" lightbox="images/netext-final.png":::

Vous pouvez également télécharger [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) et le charger dans les profils de configuration JAMF, comme décrit dans [Déploiement de profils de configuration personnalisés à l’aide de Jamf Pro| Méthode 2 : Charger un profil de configuration dans Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Étape 10 : Planifier des analyses avec Microsoft Defender pour point de terminaison sur macOS

Suivez les instructions sur [les analyses de planification avec Microsoft Defender pour point de terminaison sur macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>Étape 11 : Déployer Microsoft Defender pour point de terminaison sur macOS

1. Accédez à l’emplacement où vous avez enregistré `wdav.pkg`.

   :::image type="content" source="images/8dde76b5463047423f8637c86b05c29d.png" alt-text="Package wdav de l’Explorateur de fichiers" lightbox="images/8dde76b5463047423f8637c86b05c29d.png":::

2. Renommez-le en `wdav_MDM_Contoso_200329.pkg`.

   :::image type="content" source="images/fb2220fed3a530f4b3ef36f600da0c27.png" alt-text="Package wdavmdm de l’Explorateur de fichiers1" lightbox="images/fb2220fed3a530f4b3ef36f600da0c27.png":::

3. Ouvrez le tableau de bord Jamf Pro.

   :::image type="content" source="images/990742cd9a15ca9fdd37c9f695d1b9f4.png" alt-text="Paramètres de configuration pour jamfpro" lightbox="images/990742cd9a15ca9fdd37c9f695d1b9f4.png":::

4. Sélectionnez votre ordinateur, cliquez sur l’icône d’engrenage en haut, puis sélectionnez **Gestion de l’ordinateur**.

   :::image type="content" source="images/b6d671b2f18b89d96c1c8e2ea1991242.png" alt-text="Paramètres de configuration - Gestion de l’ordinateur" lightbox="images/b6d671b2f18b89d96c1c8e2ea1991242.png":::

5. Dans **Packages**, sélectionnez **+ Nouveau**.
   :::image type="content" source="images/57aa4d21e2ccc65466bf284701d4e961.png" alt-text="Description de l’oiseau pour un package généré automatiquement" lightbox="images/57aa4d21e2ccc65466bf284701d4e961.png":::

6. Dans **nouveau package** , entrez les détails suivants :

    **Onglet Général**
    - Nom d’affichage : laissez-le vide pour l’instant. Parce qu’il sera réinitialisé lorsque vous choisissez votre pkg.
    - Catégorie : Aucun (valeur par défaut)
    - Nom de fichier : Choisir un fichier

    :::image type="content" source="images/21de3658bf58b1b767a17358a3f06341.png" alt-text="Onglet Général pour les paramètres de configuration" lightbox="images/21de3658bf58b1b767a17358a3f06341.png":::

    Ouvrez le fichier et pointez-le vers `wdav.pkg` ou `wdav_MDM_Contoso_200329.pkg`.

    :::image type="content" source="images/1aa5aaa0a387f4e16ce55b66facc77d1.png" alt-text="Écran de l’ordinateur affichant la description d’un package généré automatiquement" lightbox="images/1aa5aaa0a387f4e16ce55b66facc77d1.png":::

7. Sélectionnez **Ouvrir**. Définissez le **nom complet** **sur Microsoft Defender Protection avancée contre les menaces et Microsoft Defender Antivirus**.

    **Le fichier manifeste** n’est pas obligatoire. Microsoft Defender pour point de terminaison fonctionne sans fichier manifeste.

    **Onglet Options** : Conservez les valeurs par défaut.

    **Onglet Limitations** : conservez les valeurs par défaut.

    :::image type="content" source="images/56dac54634d13b2d3948ab50e8d3ef21.png" alt-text="Onglet Limitation des paramètres de configuration" lightbox="images/56dac54634d13b2d3948ab50e8d3ef21.png":::

8. Sélectionnez **Enregistrer**. Le package est chargé sur Jamf Pro.

   :::image type="content" source="images/33f1ecdc7d4872555418bbc3efe4b7a3.png" alt-text="Processus de chargement du pack de paramètres de configuration pour le package lié aux paramètres de configuration" lightbox="images/33f1ecdc7d4872555418bbc3efe4b7a3.png":::

   Le déploiement du package peut prendre quelques minutes.

   :::image type="content" source="images/1626d138e6309c6e87bfaab64f5ccf7b.png" alt-text="Instance de chargement du package pour les paramètres de configuration" lightbox="images/1626d138e6309c6e87bfaab64f5ccf7b.png":::

9. Accédez à la page **Stratégies** .

   :::image type="content" source="images/f878f8efa5ebc92d069f4b8f79f62c7f.png" alt-text="Stratégies de paramètres de configuration" lightbox="images/f878f8efa5ebc92d069f4b8f79f62c7f.png":::

10. Sélectionnez **+ Nouveau** pour créer une stratégie.

    :::image type="content" source="images/847b70e54ed04787e415f5180414b310.png" alt-text="Nouvelle stratégie des paramètres de configuration" lightbox="images/847b70e54ed04787e415f5180414b310.png":::


11. En **général** , entrez les détails suivants :

    - Nom d’affichage : MDATP Onboarding Contoso 200329 v100.86.92 ou version ultérieure

      :::image type="content" source="images/625ba6d19e8597f05e4907298a454d28.png" alt-text="Paramètres de configuration - Intégration de MDATP" lightbox="images/625ba6d19e8597f05e4907298a454d28.png":::

12. Sélectionnez **l’archivage périodique**.

    :::image type="content" source="images/68bdbc5754dfc80aa1a024dde0fce7b0.png" alt-text="Archivage périodique des paramètres de configuration" lightbox="images/68bdbc5754dfc80aa1a024dde0fce7b0.png":::

13. Sélectionnez **Enregistrer**.

14. Sélectionnez **Packages > Configurer**.

    :::image type="content" source="images/8fb4cc03721e1efb4a15867d5241ebfb.png" alt-text="Option de configuration des packages" lightbox="images/8fb4cc03721e1efb4a15867d5241ebfb.png":::

15. Sélectionnez le bouton **Ajouter** en regard de **Microsoft Defender Protection avancée contre les menaces et Microsoft Defender Antivirus**.

    :::image type="content" source="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png" alt-text="Option permettant d’ajouter d’autres paramètres à MDATP MDA" lightbox="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png":::

16. Sélectionnez **Enregistrer**.

    :::image type="content" source="images/9d6e5386e652e00715ff348af72671c6.png" alt-text="Option d’enregistrement pour les paramètres de configuration" lightbox="images/9d6e5386e652e00715ff348af72671c6.png":::

17. Sélectionnez l’onglet **Étendue** .

    :::image type="content" source="images/8d80fe378a31143db9be0bacf7ddc5a3.png" alt-text="Onglet Étendue lié aux paramètres de configuration" lightbox="images/8d80fe378a31143db9be0bacf7ddc5a3.png":::

18. Sélectionnez les ordinateurs cibles.

    :::image type="content" source="images/6eda18a64a660fa149575454e54e7156.png" alt-text="Option permettant d’ajouter des groupes d’ordinateurs" lightbox="images/6eda18a64a660fa149575454e54e7156.png":::

    **Scope**

    Sélectionnez **Ajouter**.

    :::image type="content" source="images/1c08d097829863778d562c10c5f92b67.png" alt-text="Paramètres de configuration - ad1" lightbox="images/1c08d097829863778d562c10c5f92b67.png":::

    :::image type="content" source="images/216253cbfb6ae738b9f13496b9c799fd.png" alt-text="Paramètres de configuration - ad2" lightbox="images/216253cbfb6ae738b9f13496b9c799fd.png":::

    **Libre-service**

    :::image type="content" source="images/c9f85bba3e96d627fe00fc5a8363b83a.png" alt-text="Onglet Libre-service pour les paramètres de configuration" lightbox="images/c9f85bba3e96d627fe00fc5a8363b83a.png":::

19. Sélectionnez **Terminé**.

    :::image type="content" source="images/99679a7835b0d27d0a222bc3fdaf7f3b.png" alt-text="État d’intégration de Contoso avec une option pour l’effectuer" lightbox="images/99679a7835b0d27d0a222bc3fdaf7f3b.png":::

    :::image type="content" source="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png" alt-text="Page stratégies" lightbox="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png":::
