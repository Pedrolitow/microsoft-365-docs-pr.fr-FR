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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6e3a31343468b79ff1117a60eca6a87825562778
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466782"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Configurer microsoft Defender pour le point de terminaison sur les stratégies macOS dans Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Defender pour le point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Cette page vous guide à travers les étapes à suivre pour configurer des stratégies macOS dans Jamf Pro.

Vous devez suivre les étapes suivantes :

1. [Obtenir le package d’intégration De Microsoft Defender pour point de terminaison](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Créer un profil de configuration dans Jamf Pro à l’aide du package d’intégration](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Configurer les paramètres de Microsoft Defender pour les points de terminaison](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Configurer les paramètres de notification microsoft Defender pour les points de terminaison](#step-4-configure-notifications-settings)
5. [Configurer la mise à jour automatique Microsoft (AutoUpdate)](#step-5-configure-microsoft-autoupdate-mau)
6. [Accorder un accès disque complet à Microsoft Defender pour le point de terminaison](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Approuver l’extension de noyau pour Microsoft Defender pour le point de terminaison](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Approuver les extensions système pour Microsoft Defender pour le point de terminaison](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Configurer l’extension réseau](#step-9-configure-network-extension)
10. [Planifier des analyses avec Microsoft Defender pour endpoint sur macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [Déployer Microsoft Defender pour le point de terminaison sur macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>Étape 1 : Obtenir le package d’intégration De Microsoft Defender pour point de terminaison

1. In [Microsoft 365 Defender](https://security.microsoft.com), navigate to **Paramètres > Endpoints > Onboarding**.

2. Sélectionnez macOS comme système d’exploitation et Gestion des périphériques mobiles/Microsoft Intune comme méthode de déploiement.

   :::image type="content" source="images/onboarding-macos.png" alt-text="Page Paramètres de l’Centre de sécurité Microsoft Defender" lightbox="images/onboarding-macos.png":::

3. **Sélectionnez Télécharger le package d’intégration** (WindowsDefenderATPOnboardingPackage.zip).

4. Extraire `WindowsDefenderATPOnboardingPackage.zip`.

5. Copiez le fichier à votre emplacement préféré. Par exemple : `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>Étape 2 : Créer un profil de configuration dans Jamf Pro à l’aide du package d’intégration

1. Recherchez le fichier `WindowsDefenderATPOnboarding.plist` dans la section précédente.

   :::image type="content" source="images/plist-onboarding-file.png" alt-text="Le Windows Defender d’intégration ATP" lightbox="images/plist-onboarding-file.png":::

2. Connectez-vous à Jamf Pro, accédez à **Profils** **ComputersConfiguration** > , puis sélectionnez **Nouveau**.

   :::image type="content" source="images/jamf-pro-configure-profile.png" alt-text="Page sur laquelle vous créez un tableau de bord jamf Pro tableau de bord" lightbox="images/jamf-pro-configure-profile.png":::

3. Entrez les détails suivants :

   **Général** :

   - Nom : intégration MDE pour macOS
   - Description : intégration PEPT MDE pour macOS
   - Catégorie : Aucun
   - Méthode de distribution : installer automatiquement
   - Niveau : niveau ordinateur

4.  Accédez à la **page Application & custom Paramètres** et sélectionnez **Télécharger** >  **Add**.

   :::image type="content" source="images/jamfpro-mac-profile.png" alt-text="Configurer l’application et les paramètres personnalisés" lightbox="images/jamfpro-mac-profile.png":::

5. **Sélectionnez Télécharger fichier (fichier PLIST), puis dans** **Domaine** de préférence, entrez : `com.microsoft.wdav.atp`

   :::image type="content" source="images/jamfpro-plist-upload.png" alt-text="Fichier de téléchargement de la liste plist jamfpro" lightbox="images/jamfpro-plist-upload.png":::

   :::image type="content" source="images/jamfpro-plist-file.png" alt-text="Fichier de liste des propriétés de fichier de téléchargement" lightbox="images/jamfpro-plist-file.png":::

6. **Sélectionnez Ouvrir** et sélectionnez le fichier d’intégration.

   :::image type="content" source="images/jamfpro-plist-file-onboard.png" alt-text="Fichier d’intégration" lightbox="images/jamfpro-plist-file-onboard.png":::

7. Sélectionnez **Télécharger**.

   :::image type="content" source="images/jamfpro-upload-plist.png" alt-text="Fichier plist de téléchargement" lightbox="images/jamfpro-upload-plist.png":::

8. Sélectionnez **l’onglet** Étendue.

   :::image type="content" source="images/jamfpro-scope-tab.png" alt-text="Onglet Étendue" lightbox="images/jamfpro-scope-tab.png":::

9. Sélectionnez les ordinateurs cibles.

   :::image type="content" source="images/jamfpro-target-computer.png" alt-text="Ordinateurs cibles" lightbox="images/jamfpro-target-computer.png":::

   :::image type="content" source="images/jamfpro-targets.png" alt-text="Cibles" lightbox="images/jamfpro-targets.png":::

10. Sélectionnez **Enregistrer**.

   :::image type="content" source="images/jamfpro-deployment-target.png" alt-text="Le déploiement des ordinateurs cibles" lightbox="images/jamfpro-deployment-target.png":::

   :::image type="content" source="images/jamfpro-target-selected.png" alt-text="Sélection des ordinateurs cibles" lightbox="images/jamfpro-target-selected.png":::

11. Sélectionnez **Terminé**.

    :::image type="content" source="images/jamfpro-target-group.png" alt-text="Ordinateurs d’un groupe cible" lightbox="images/jamfpro-target-group.png":::

    :::image type="content" source="images/jamfpro-configuration-policies.png" alt-text="Liste des profils de configuration" lightbox="images/jamfpro-configuration-policies.png":::

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>Étape 3 : Configurer Microsoft Defender pour les paramètres de point de terminaison

Vous pouvez utiliser l’interface graphique graphique jamf Pro pour modifier les paramètres individuels de la configuration de Microsoft Defender for Endpoint, ou utiliser la méthode héritée en créant un Plist de configuration dans un éditeur de texte et en le téléchargeant dans jamf Pro.

Notez que vous devez utiliser exact `com.microsoft.wdav` comme domaine de **préférence, Microsoft** Defender pour point `com.microsoft.wdav.ext` de terminaison utilise uniquement ce nom et pour charger ses paramètres gérés !

(La `com.microsoft.wdav.ext` version peut être utilisée dans de rares cas lorsque vous préférez utiliser la méthode GUI, mais que vous devez également configurer un paramètre qui n’a pas encore été ajouté au schéma.)

### <a name="gui-method"></a>Méthode GUI

1. Téléchargez le fichier schema.json à partir du référentiel [GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) defender et enregistrez-le dans un fichier local :

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Créez un profil de configuration sous Ordinateurs -> profils de configuration, entrez les détails suivants sous **l’onglet Général** :

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Un nouveau profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

    - Nom : paramètres de configuration MDAV MDATP
    - Description :\<blank\>
    - Catégorie : Aucun (par défaut)
    - Niveau : niveau ordinateur (par défaut)
    - Méthode de distribution : installer automatiquement (par défaut)

3. Faites défiler vers le bas jusqu’à   **l’onglet Application & Custom Paramètres**, sélectionnez **Applications** externes, cliquez sur Ajouter et utiliser le schéma personnalisé comme source à utiliser pour le domaine de préférence.

   :::image type="content" source="images/4137189bc3204bb09eed3aabc41afd78.png" alt-text="Ajouter un schéma personnalisé" lightbox="images/4137189bc3204bb09eed3aabc41afd78.png":::

4. Entrez `com.microsoft.wdav` comme domaine de préférence, cliquez sur  Ajouter un schéma **et Télécharger** fichier schema.json téléchargé à l’étape 1. Cliquez sur **Enregistrer**.

   :::image type="content" source="images/a6f9f556037c42fabcfdcb1b697244cf.png" alt-text="Télécharger schéma" lightbox="images/a6f9f556037c42fabcfdcb1b697244cf.png":::

5. Vous pouvez voir tous les paramètres de configuration de Microsoft Defender for Endpoint pris en charge ci-dessous, sous **Propriétés de domaine de préférence**. Cliquez **sur Ajouter/Supprimer des propriétés** pour sélectionner les paramètres à gérer, puis cliquez sur **OK** pour enregistrer vos modifications. (Paramètres non sélectionné ne sera pas inclus dans la configuration gérée, un utilisateur final pourra configurer ces paramètres sur ses ordinateurs.)

   :::image type="content" source="images/817b3b760d11467abe9bdd519513f54f.png" alt-text="Paramètres gérés choisis" lightbox="images/817b3b760d11467abe9bdd519513f54f.png":::

6. Modifiez les valeurs des paramètres en valeurs souhaitées. Vous pouvez cliquer **sur Plus d’informations** pour obtenir la documentation d’un paramètre particulier. (Vous pouvez cliquer sur **aperçu Plist** pour inspecter l’apparence de la liste de configuration. Cliquez **sur Éditeur de** formulaire pour revenir à l’éditeur visuel.)

   :::image type="content" source="images/a14a79efd5c041bb8974cb5b12b3a9b6.png" alt-text="Page sur laquelle vous modifiez les valeurs des paramètres" lightbox="images/a14a79efd5c041bb8974cb5b12b3a9b6.png":::

7. Sélectionnez **l’onglet** Étendue.

   :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Étendue du profil de configuration" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

8. **Sélectionnez Le groupe d’ordinateurs de Contoso**.

9. **Sélectionnez Ajouter**, puis **Enregistrer**.

   :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Page sur laquelle vous pouvez ajouter les paramètres de configuration" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

   :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Page sur laquelle vous pouvez enregistrer les paramètres de configuration" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

10. Sélectionnez **Terminé**. Vous verrez le nouveau profil **de configuration**.

    :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Page sur laquelle vous complétez les paramètres de configuration" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

Microsoft Defender pour le point de terminaison ajoute de nouveaux paramètres au fil du temps. Ces nouveaux paramètres seront ajoutés au schéma et une nouvelle version sera publiée sur Github.
Il vous suffit de télécharger un schéma mis à jour, de modifier le profil de configuration existant et de modifier le schéma sous  l’onglet Application **& Custom Paramètres**.

### <a name="legacy-method"></a>Méthode héritée

1. Utilisez les paramètres de configuration microsoft Defender pour les points de terminaison suivants :

    - enableRealTimeProtection
    - passiveMode

    > [!NOTE]
    > Non désactivé par défaut, si vous envisagez d’exécuter un antivirus tiers pour macOS, définissez-le sur `true`.

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

     Pour plus d’informations, [voir Liste des propriétés pour le profil de configuration complet JAMF](mac-preferences.md#property-list-for-jamf-full-configuration-profile).

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

3. Dans le tableau de bord Jamf Pro, ouvrez **Ordinateurs** et leurs **profils de configuration**. Cliquez **sur Nouveau** et passez à **l’onglet** Général.

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Page affichant un nouveau profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

4. Entrez les détails suivants :

    **Général**

    - Nom : paramètres de configuration MDAV MDATP
    - Description :\<blank\>
    - Catégorie : Aucun (par défaut)
    - Méthode de distribution : installer automatiquement (par défaut)
    - Niveau : Niveau ordinateur (par défaut)

    :::image type="content" source="images/3160906404bc5a2edf84d1d015894e3b.png" alt-text="Paramètres de configuration MDAV MDATP" lightbox="images/3160906404bc5a2edf84d1d015894e3b.png":::

5. Dans **Application & personnalisé Paramètres** **sélectionnez Configurer**.

   :::image type="content" source="images/e1cc1e48ec9d5d688087b4d771e668d2.png" alt-text="L’application et les paramètres personnalisés" lightbox="images/e1cc1e48ec9d5d688087b4d771e668d2.png":::

6. **Sélectionnez Télécharger fichier (fichier PLIST).**

   :::image type="content" source="images/6f85269276b2278eca4bce84f935f87b.png" alt-text="Fichier plist des paramètres de configuration" lightbox="images/6f85269276b2278eca4bce84f935f87b.png":::

7. Dans **Domaine préférences**, entrez `com.microsoft.wdav`, puis sélectionnez **Télécharger fichier PLIST**.

   :::image type="content" source="images/db15f147dd959e872a044184711d7d46.png" alt-text="Domaine des préférences de paramètres de configuration" lightbox="images/db15f147dd959e872a044184711d7d46.png":::

8. **Sélectionnez Choisir un fichier**.

    :::image type="content" source="images/526e978761fc571cca06907da7b01fd6.png" alt-text="Invite à choisir le fichier plist" lightbox="images/526e978761fc571cca06907da7b01fd6.png":::

9. Sélectionnez **le MDATP_MDAV_configuration_settings.plist**, puis sélectionnez **Ouvrir**.

   :::image type="content" source="images/98acea3750113b8dbab334296e833003.png" alt-text="Paramètres de configuration mdatpmdav" lightbox="images/98acea3750113b8dbab334296e833003.png":::

10. Sélectionnez **Télécharger**.

    :::image type="content" source="images/0adb21c13206861ba9b30a879ade93d3.png" alt-text="Téléchargement du paramètre de configuration" lightbox="images/0adb21c13206861ba9b30a879ade93d3.png":::

    :::image type="content" source="images/f624de59b3cc86e3e2d32ae5de093e02.png" alt-text="Invite à télécharger l’image liée aux paramètres de configuration" lightbox="images/f624de59b3cc86e3e2d32ae5de093e02.png":::

    > [!NOTE]
    > Si vous téléchargez le fichier Intune, vous obtenez l’erreur suivante :
    >
    > :::image type="content" source="images/8e69f867664668796a3b2904896f0436.png" alt-text="Invite à télécharger le fichier Intune associé aux paramètres de configuration" lightbox="images/8e69f867664668796a3b2904896f0436.png":::

11. Sélectionnez **Enregistrer**.

    :::image type="content" source="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png" alt-text="Option d’enregistrer l’image liée aux paramètres de configuration" lightbox="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png":::

12. Le fichier est téléchargé.

    :::image type="content" source="images/33e2b2a1611fdddf6b5b79e54496e3bb.png" alt-text="Fichier téléchargé lié aux paramètres de configuration" lightbox="images/33e2b2a1611fdddf6b5b79e54496e3bb.png":::

    :::image type="content" source="images/a422e57fe8d45689227e784443e51bd1.png" alt-text="Page paramètres de configuration" lightbox="images/a422e57fe8d45689227e784443e51bd1.png":::

13. Sélectionnez **l’onglet** Étendue.

    :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Étendue des paramètres de configuration" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

14. **Sélectionnez Le groupe d’ordinateurs de Contoso**.

15. **Sélectionnez Ajouter**, puis **Enregistrer**.

    :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Les paramètres de configuration addsav" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

    :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Notification des paramètres de configuration" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

16. Sélectionnez **Terminé**. Vous verrez le nouveau profil **de configuration**.

    ![Image de l’image de profil de configuration des paramètres de configuration.](images/dd55405106da0dfc2f50f8d4525b01c8.png)
     :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Paramètres du profil de configuration" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

## <a name="step-4-configure-notifications-settings"></a>Étape 4 : Configurer les paramètres de notifications

Ces étapes s’appliquent à macOS 10.15 (Genreline) ou aux appareils plus nouveaux.

1. Dans le tableau de bord Jamf Pro, **sélectionnez Ordinateurs**, puis **Profils de configuration**.

2. Cliquez **sur Nouveau**, puis entrez les détails suivants pour **Options** :

    - Onglet **Général** :
        - **Nom :** paramètres de notification MDAV MDATP
        - **Description** : macOS 10.15 (Contrôle) ou une nouveauté
        - **Catégorie** : Aucun *(par défaut)*
        - **Méthode de distribution** : installer automatiquement *(par défaut)*
        - **Niveau :** niveau ordinateur *(par défaut)*

        :::image type="content" source="images/c9820a5ff84aaf21635c04a23a97ca93.png" alt-text="Nouvelle page de profil de configuration macOS" lightbox="images/c9820a5ff84aaf21635c04a23a97ca93.png":::

    - Tab **Notifications**, click **Add**, and enter the following values:
        - **ID d’offre groupée** : `com.microsoft.wdav.tray`
        - **Alertes critiques** : cliquez sur **Désactiver**
        - **Notifications :** cliquez sur **Activer**
        - **Type d’alerte bannière** : sélectionner **Inclure** **et temporaire** *(par défaut)*
        - **Notifications sur l’écran de verrouillage** : cliquez sur **Masquer**
        - **Notifications dans le Centre de notifications** : cliquez sur **Afficher**
        - **Icône d’application de badge** : cliquez sur **Afficher**

        :::image type="content" source="images/7f9138053dbcbf928e5182ee7b295ebe.png" alt-text="Bac de notifications mdatpmdav des paramètres de configuration" lightbox="images/7f9138053dbcbf928e5182ee7b295ebe.png":::

    - Tab **Notifications**, click **Add** one more time, scroll down to **New Notifications Paramètres**
        - **ID d’offre groupée** : `com.microsoft.autoupdate2`
        - Configurer le reste des paramètres sur les mêmes valeurs que ci-dessus

        :::image type="content" source="images/4bac6ce277aedfb4a674f2d9fcb2599a.png" alt-text="Les paramètres de configuration mdatpmdav notifications mau" lightbox="images/4bac6ce277aedfb4a674f2d9fcb2599a.png":::

        Notez que vous avez maintenant deux « tables » avec des configurations de notification, une pour l’ID d’offre groupée : **com.microsoft.wdav.tray** et une autre pour l’ID d’offre groupée : **com.microsoft.autoupdate2**. Bien que vous pouvez configurer les paramètres d’alerte en fonction de vos besoins, les ID d’offre groupée doivent  être exactement les mêmes  que ceux décrits précédemment, et le commutateur Inclure doit être en cours pour les **notifications**.

3. Sélectionnez **l’onglet** Étendue, puis **Ajoutez**.

   :::image type="content" source="images/441aa2ecd36abadcdd8aed03556080b5.png" alt-text="Page sur laquelle vous pouvez ajouter des valeurs pour les paramètres de configuration" lightbox="images/441aa2ecd36abadcdd8aed03556080b5.png":::

4. **Sélectionnez Le groupe d’ordinateurs de Contoso**.

5. **Sélectionnez Ajouter**, puis **Enregistrer**.

   :::image type="content" source="images/09a275e321268e5e3ac0c0865d3e2db5.png" alt-text="Page sur laquelle vous pouvez enregistrer des valeurs pour le groupe d’ordinateurs paramètres de configuration contoso" lightbox="images/09a275e321268e5e3ac0c0865d3e2db5.png":::

   :::image type="content" source="images/4d2d1d4ee13d3f840f425924c3df0d51.png" alt-text="Page qui affiche la notification d’achèvement des paramètres de configuration" lightbox="images/4d2d1d4ee13d3f840f425924c3df0d51.png":::

6. Sélectionnez **Terminé**. Vous verrez le nouveau profil **de configuration**.

   :::image type="content" source="images/633ad26b8bf24ec683c98b2feb884bdf.png" alt-text="Paramètres de configuration terminés" lightbox="images/633ad26b8bf24ec683c98b2feb884bdf.png":::

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>Étape 5 : Configurer la mise à jour automatique Microsoft (AutoUpdate)

1. Utilisez les paramètres de configuration microsoft Defender pour les points de terminaison suivants :

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

3. Dans le tableau de bord Pro Jamf, sélectionnez **Général**.

   :::image type="content" source="images/eaba2a23dd34f73bf59e826217ba6f15.png" alt-text="Paramètres de configuration" lightbox="images/eaba2a23dd34f73bf59e826217ba6f15.png":::

4. Entrez les détails suivants :

    **Général**

    - Name: MDATP MDAV MAU settings
    - Description : Paramètres de mise à jour automatique Microsoft pour MDATP pour macOS
    - Catégorie : Aucun (par défaut)
    - Méthode de distribution : installer automatiquement (par défaut)
    - Niveau : Niveau ordinateur (par défaut)

5. Dans **Application & personnalisé Paramètres** **sélectionnez Configurer**.

   :::image type="content" source="images/1f72e9c15eaafcabf1504397e99be311.png" alt-text="Application de paramètre de configuration et paramètres personnalisés" lightbox="images/1f72e9c15eaafcabf1504397e99be311.png":::

6. **Sélectionnez Télécharger fichier (fichier PLIST).**

7. In **Preference Domain** enter: `com.microsoft.autoupdate2`, then select **Télécharger PLIST File**.

   :::image type="content" source="images/1213872db5833aa8be535da57653219f.png" alt-text="Domaine de préférence du paramètre de configuration" lightbox="images/1213872db5833aa8be535da57653219f.png":::
    

8. **Sélectionnez Choisir un fichier**.

   :::image type="content" source="images/335aff58950ce62d1dabc289ecdce9ed.png" alt-text="Invite à choisir le fichier concernant le paramètre de configuration" lightbox="images/335aff58950ce62d1dabc289ecdce9ed.png":::

9. **Sélectionnez MDATP_MDAV_MAU_settings.plist**.

   :::image type="content" source="images/a26bd4967cd54bb113a2c8d32894c3de.png" alt-text="Paramètres mdatpmdavmau" lightbox="images/a26bd4967cd54bb113a2c8d32894c3de.png":::

10. Sélectionnez **Télécharger**.
    :::image type="content" source="images/4239ca0528efb0734e4ca0b490bfb22d.png" alt-text="Téléchargement du fichier concernant le paramètre de configuration" lightbox="images/4239ca0528efb0734e4ca0b490bfb22d.png":::

    :::image type="content" source="images/4ec20e72c8aed9a4c16912e01692436a.png" alt-text="Page affichant l’option de téléchargement pour le fichier concernant le paramètre de configuration" lightbox="images/4ec20e72c8aed9a4c16912e01692436a.png":::

11. Sélectionnez **Enregistrer**.

    :::image type="content" source="images/253274b33e74f3f5b8d475cf8692ce4e.png" alt-text="Page affichant l’option d’enregistrer pour le fichier concernant le paramètre de configuration" lightbox="images/253274b33e74f3f5b8d475cf8692ce4e.png":::

12. Sélectionnez **l’onglet** Étendue.

    :::image type="content" source="images/10ab98358b2d602f3f67618735fa82fb.png" alt-text="Onglet Étendue pour les paramètres de configuration" lightbox="images/10ab98358b2d602f3f67618735fa82fb.png":::

13. Sélectionnez **Ajouter**.

    :::image type="content" source="images/56e6f6259b9ce3c1706ed8d666ae4947.png" alt-text="Option d’ajout de cibles de déploiement" lightbox="images/56e6f6259b9ce3c1706ed8d666ae4947.png":::

    :::image type="content" source="images/38c67ee1905c4747c3b26c8eba57726b.png" alt-text="Page sur laquelle vous ajoutez des valeurs aux paramètres de configuration" lightbox="images/38c67ee1905c4747c3b26c8eba57726b.png":::

    :::image type="content" source="images/321ba245f14743c1d5d51c15e99deecc.png" alt-text="Page sur laquelle vous pouvez ajouter des valeurs aux paramètres de configuration" lightbox="images/321ba245f14743c1d5d51c15e99deecc.png":::

14. Sélectionnez **Terminé**.

    :::image type="content" source="images/ba44cdb77e4781aa8b940fb83e3c21f7.png" alt-text="Notification d’achèvement concernant les paramètres de configuration" lightbox="images/ba44cdb77e4781aa8b940fb83e3c21f7.png":::

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>Étape 6 : Accorder un accès disque total à Microsoft Defender pour le point de terminaison

1. Dans le tableau de bord Jamf Pro, sélectionnez **Profils de configuration**.

   :::image type="content" source="images/264493cd01e62c7085659d6fdc26dc91.png" alt-text="Profil pour lequel les paramètres doivent être configurés" lightbox="images/264493cd01e62c7085659d6fdc26dc91.png":::

2. **Sélectionnez + Nouveau**.

3. Entrez les détails suivants :

    **Général**
    - Nom : MDATP MDAV : accorder un accès disque total à PEPT et antivirus
    - Description : sur macOS Ou une nouveauté, le nouveau contrôle de stratégie des préférences de confidentialité
    - Catégorie : Aucun
    - Méthode de distribution : installer automatiquement
    - Niveau : niveau ordinateur

    :::image type="content" source="images/ba3d40399e1a6d09214ecbb2b341923f.png" alt-text="Le paramètre de configuration en général" lightbox="images/ba3d40399e1a6d09214ecbb2b341923f.png":::
    

4. In **Configure Privacy Preferences Policy Control** select **Configure**.

   :::image type="content" source="images/715ae7ec8d6a262c489f94d14e1e51bb.png" alt-text="Contrôle de la stratégie de confidentialité de la configuration" lightbox="images/715ae7ec8d6a262c489f94d14e1e51bb.png":::

5. Dans **le contrôle de stratégie préférences de confidentialité**, entrez les détails suivants :

    - Identificateur : `com.microsoft.wdav`
    - Type d’identificateur : ID d’offre groupée
    - Conditions requises pour le code : `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    :::image type="content" source="images/22cb439de958101c0a12f3038f905b27.png" alt-text="Détails du contrôle de stratégie de confidentialité des paramètres de configuration" lightbox="images/22cb439de958101c0a12f3038f905b27.png":::

6. Sélectionnez **+ Ajouter**.

   :::image type="content" source="images/bd93e78b74c2660a0541af4690dd9485.png" alt-text="Le paramètre de configuration permet d’ajouter une stratégie système à tous les fichiers" lightbox="images/bd93e78b74c2660a0541af4690dd9485.png":::

    - Sous Application ou service : définir sur **SystemPolicyAllFiles**

    - Sous « accès » : définir sur **Autoriser**

7. **Sélectionnez Enregistrer** (et non celui en bas à droite).

   :::image type="content" source="images/6de50b4a897408ddc6ded56a09c09fe2.png" alt-text="Opération d’enregistrer pour le paramètre de configuration" lightbox="images/6de50b4a897408ddc6ded56a09c09fe2.png":::

8. Cliquez sur le signe `+` en de côté **d’App Access** pour ajouter une nouvelle entrée.

   :::image type="content" source="images/tcc-add-entry.png" alt-text="Opération d’enregistrer relative au paramètre de configuration" lightbox="images/tcc-add-entry.png":::

9. Entrez les détails suivants :

    - Identificateur : `com.microsoft.wdav.epsext`
    - Type d’identificateur : ID d’offre groupée
    - Conditions requises pour le code : `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. Sélectionnez **+ Ajouter**.

    :::image type="content" source="images/tcc-epsext-entry.png" alt-text="Entrée tcc epsext du paramètre de configuration" lightbox="images/tcc-epsext-entry.png":::

    - Sous Application ou service : définir sur **SystemPolicyAllFiles**

    - Sous « accès » : définir sur **Autoriser**

11. **Sélectionnez Enregistrer** (et non celui en bas à droite).

    :::image type="content" source="images/tcc-epsext-entry2.png" alt-text="L’autre instance du paramètre de configuration tcc epsext" lightbox="images/tcc-epsext-entry2.png":::

12. Sélectionnez **l’onglet** Étendue.

    :::image type="content" source="images/2c49b16cd112729b3719724f581e6882.png" alt-text="Page illustrant l’étendue du paramètre de configuration" lightbox="images/2c49b16cd112729b3719724f581e6882.png":::

13. Sélectionnez **+ Ajouter**.

    :::image type="content" source="images/57cef926d1b9260fb74a5f460cee887a.png" alt-text="Page illustrant le paramètre de configuration" lightbox="images/57cef926d1b9260fb74a5f460cee887a.png":::

14. **Sélectionnez Groupes d’ordinateurs** > **sous Nom** de > **sélectionnez MachineGroup de Contoso**.

    :::image type="content" source="images/368d35b3d6179af92ffdbfd93b226b69.png" alt-text="Groupe d’ordinateurs contoso du paramètre de configuration" lightbox="images/368d35b3d6179af92ffdbfd93b226b69.png":::

15. Sélectionnez **Ajouter**.

16. Sélectionnez **Enregistrer**.

17. Sélectionnez **Terminé**.

    :::image type="content" source="images/809cef630281b64b8f07f20913b0039b.png" alt-text="Paramètre de configuration contoso machine-group" lightbox="images/809cef630281b64b8f07f20913b0039b.png":::

    :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Illustration des paramètres de configuration" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

Vous pouvez également télécharger [fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) et le télécharger dans les profils de configuration JAMF, comme décrit dans [Deploying Custom Configuration Profiles using Jamf Pro| Méthode 2 : Télécharger profil de configuration à Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>Étape 7 : Approuver l’extension de noyau pour Microsoft Defender pour le point de terminaison

> [!CAUTION]
> Les appareils Apple Silicon (M1) ne supportent pas KEXT. L’installation d’un profil de configuration constitué de stratégies KEXT échoue sur ces appareils.

1. Dans les **profils de configuration**, **sélectionnez + Nouveau**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Le billet de réseau social Description généré automatiquement" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Entrez les détails suivants :

    **Général**

    - Name: MDATP MDAV Kernel Extension
    - Description : extension de noyau MDATP (kext)
    - Catégorie : Aucun
    - Méthode de distribution : installer automatiquement
    - Niveau : niveau ordinateur

    :::image type="content" source="images/24e290f5fc309932cf41f3a280d22c14.png" alt-text="Les paramètres de configuration mdatpmdav kernel" lightbox="images/24e290f5fc309932cf41f3a280d22c14.png":::

3. Dans **Configurer les extensions de noyau approuvées, sélectionnez** **Configurer**.

   :::image type="content" source="images/30be88b63abc5e8dde11b73f1b1ade6a.png" alt-text="Page affichant les paramètres de configuration des extensions de noyau approuvées" lightbox="images/30be88b63abc5e8dde11b73f1b1ade6a.png":::

4. Dans **Extensions de noyau approuvées,** entrez les détails suivants :

    - Nom complet : Microsoft Corp.
    - ID d’équipe : UBF8T346G9

    :::image type="content" source="images/39cf120d3ac3652292d8d1b6d057bd60.png" alt-text="Volet Extensions de noyau approuvées" lightbox="images/39cf120d3ac3652292d8d1b6d057bd60.png":::

5. Sélectionnez **l’onglet** Étendue.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Onglet Étendue pour la configuration" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Sélectionnez **+ Ajouter**.

7. **Sélectionnez Groupes d’ordinateurs** > **sous Nom** de > **sélectionnez Groupe d’ordinateurs de Contoso**.

8. Sélectionnez **+ Ajouter**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Page sur laquelle vous définissez des valeurs supplémentaires pour les paramètres de configuration" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Sélectionnez **Enregistrer**.

   :::image type="content" source="images/0add8019b85a453b47fa5c402c72761b.png" alt-text="Extension de noyau MDAV MDATP" lightbox="images/0add8019b85a453b47fa5c402c72761b.png":::

10. Sélectionnez **Terminé**.

    :::image type="content" source="images/1c9bd3f68db20b80193dac18f33c22d0.png" alt-text="Page de détails des profils de configuration" lightbox="images/1c9bd3f68db20b80193dac18f33c22d0.png":::

Vous pouvez également télécharger [kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) et le télécharger dans les profils de configuration JAMF, comme décrit dans [Deploying Custom Configuration Profiles using Jamf Pro| Méthode 2 : Télécharger profil de configuration à Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>Étape 8 : Approuver les extensions système pour Microsoft Defender pour le point de terminaison

1. Dans les **profils de configuration**, **sélectionnez + Nouveau**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Description du billet de réseau social généré automatiquement" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Entrez les détails suivants :

    **Général**

    - Name: MDATP MDAV System Extensions
    - Description : extensions système MDATP
    - Catégorie : Aucun
    - Méthode de distribution : installer automatiquement
    - Niveau : niveau ordinateur

    :::image type="content" source="images/sysext-new-profile.png" alt-text="Nouveau profil des paramètres de configuration" lightbox="images/sysext-new-profile.png":::

3. Dans **Les extensions système,** **sélectionnez Configurer**.

   :::image type="content" source="images/sysext-configure.png" alt-text="Volet avec l’option Configurer pour les extensions système" lightbox="images/sysext-configure.png":::

4. Dans **les extensions système** , entrez les détails suivants :

   - Nom complet : Microsoft Corp. System Extensions
   - Types d’extension système : extensions système autorisées
   - Identificateur d’équipe : UBF8T346G9
   - Extensions système autorisées :
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    :::image type="content" source="images/sysext-configure2.png" alt-text="Volet Extensions système MDAV MDATP" lightbox="images/sysext-configure2.png":::

5. Sélectionnez **l’onglet** Étendue.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Volet de sélection Ordinateurs cibles" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Sélectionnez **+ Ajouter**.

7. **Sélectionnez Groupes d’ordinateurs** > **sous Nom** de > **sélectionnez Groupe d’ordinateurs de Contoso**.

8. Sélectionnez **+ Ajouter**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Volet Nouveau profil de configuration macOS" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Sélectionnez **Enregistrer**.

   :::image type="content" source="images/sysext-scope.png" alt-text="Affichage des options concernant les extensions système MDAV MDATP" lightbox="images/sysext-scope.png":::

10. Sélectionnez **Terminé**.

    :::image type="content" source="images/sysext-final.png" alt-text="Les paramètres de configuration sysext - final" lightbox="images/sysext-final.png":::

## <a name="step-9-configure-network-extension"></a>Étape 9 : Configurer l’extension réseau

Dans le cadre des fonctionnalités de détection et de réponse des points de terminaison, Microsoft Defender for Endpoint sur macOS inspecte le trafic de socket et signale ces informations au portail Microsoft 365 Defender. La stratégie suivante permet à l’extension réseau d’effectuer cette fonctionnalité.

Ces étapes s’appliquent à macOS 10.15 (Genreline) ou aux appareils plus nouveaux.

1. Dans le tableau de bord Jamf Pro, **sélectionnez Ordinateurs**, puis **Profils de configuration**.

2. Cliquez **sur Nouveau**, puis entrez les détails suivants pour **Options** :

    - Onglet **Général** :
        - **Nom :** Extension réseau Microsoft Defender
        - **Description** : macOS 10.15 (Contrôle) ou une nouveauté
        - **Catégorie** : Aucun *(par défaut)*
        - **Méthode de distribution** : installer automatiquement *(par défaut)*
        - **Niveau :** niveau ordinateur *(par défaut)*

    - Filtre **de contenu d’onglet** :
        - **Nom du filtre** : filtre de contenu Microsoft Defender
        - **Identificateur** : `com.microsoft.wdav`
        - Laisser **l’adresse du service**, **l’organisation**, **le nom d’utilisateur**, **le** mot de passe, **le certificat** vide (**Inclure** *n’est pas* sélectionné)
        - **Ordre de filtrage** : Inspecteur
        - **Filtre de socket** : `com.microsoft.wdav.netext`
        - **Exigence désignée par le filtre de socket** : `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - Laisser **les champs Filtre réseau** vides (**Inclure** *n’est pas* sélectionné)

        Notez que **l’identificateur**, le filtre de **socket** et le **filtre de socket désignent** les valeurs exactes requises comme indiqué ci-dessus.

        :::image type="content" source="images/netext-create-profile.png" alt-text="Paramètre de configuration mdatpmdav" lightbox="images/netext-create-profile.png":::

3. Sélectionnez **l’onglet** Étendue.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Onglet Paramètres de configuration" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

4. Sélectionnez **+ Ajouter**.

5. **Sélectionnez Groupes d’ordinateurs** > **sous Nom** de > **sélectionnez Groupe d’ordinateurs de Contoso**.

6. Sélectionnez **+ Ajouter**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Adim des paramètres de configuration" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

7. Sélectionnez **Enregistrer**.

   :::image type="content" source="images/netext-scope.png" alt-text="Volet Filtre de contenu" lightbox="images/netext-scope.png":::

8. Sélectionnez **Terminé**.

   :::image type="content" source="images/netext-final.png" alt-text="Texte final des paramètres de configuration" lightbox="images/netext-final.png":::

Vous pouvez également télécharger [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) et le télécharger dans les profils de configuration JAMF comme décrit dans [Deploying Custom Configuration Profiles using Jamf Pro| Méthode 2 : Télécharger profil de configuration à Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Étape 10 : Planifier des analyses avec Microsoft Defender pour Endpoint sur macOS

Suivez les instructions des [analyses de planification avec Microsoft Defender for Endpoint sur macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>Étape 11 : Déployer Microsoft Defender pour endpoint sur macOS

1. Accédez à l’endroit où vous avez enregistré `wdav.pkg`.

   :::image type="content" source="images/8dde76b5463047423f8637c86b05c29d.png" alt-text="Package wdav de l’explorateur de fichiers" lightbox="images/8dde76b5463047423f8637c86b05c29d.png":::

2. Renommons-le `wdav_MDM_Contoso_200329.pkg`.

   :::image type="content" source="images/fb2220fed3a530f4b3ef36f600da0c27.png" alt-text="Package wdavmdm de l’explorateur de fichiers 1" lightbox="images/fb2220fed3a530f4b3ef36f600da0c27.png":::

3. Ouvrez le tableau de bord Pro Jamf.

   :::image type="content" source="images/990742cd9a15ca9fdd37c9f695d1b9f4.png" alt-text="Paramètres de configuration de jamfpro" lightbox="images/990742cd9a15ca9fdd37c9f695d1b9f4.png":::

4. Sélectionnez votre ordinateur et cliquez sur l’icône d’engrenage en haut, puis **sélectionnez Gestion de l’ordinateur**.

   :::image type="content" source="images/b6d671b2f18b89d96c1c8e2ea1991242.png" alt-text="Paramètres de configuration : gestion de l’ordinateur" lightbox="images/b6d671b2f18b89d96c1c8e2ea1991242.png":::

5. Dans **les packages**, **sélectionnez + Nouveau**.
   :::image type="content" source="images/57aa4d21e2ccc65466bf284701d4e961.png" alt-text="Description de l’observation d’un package généré automatiquement" lightbox="images/57aa4d21e2ccc65466bf284701d4e961.png":::

6. Dans **le nouveau package** , entrez les détails suivants :

    **Onglet Général**
    - Nom complet : laissez-le vide pour le moment. Parce qu’il sera réinitialisé lorsque vous choisirez votre pkg.
    - Catégorie : Aucun (par défaut)
    - Filename: Choose File

    :::image type="content" source="images/21de3658bf58b1b767a17358a3f06341.png" alt-text="Onglet Général pour les paramètres de configuration" lightbox="images/21de3658bf58b1b767a17358a3f06341.png":::

    Ouvrez le fichier et pointer vers `wdav.pkg` ou `wdav_MDM_Contoso_200329.pkg`.

    :::image type="content" source="images/1aa5aaa0a387f4e16ce55b66facc77d1.png" alt-text="Écran de l’ordinateur affichant la description d’un package généré automatiquement" lightbox="images/1aa5aaa0a387f4e16ce55b66facc77d1.png":::

7. Sélectionnez **Ouvrir**. Définissez **le nom complet sur** **Microsoft Defender - Protection avancée contre les menaces et Antivirus Microsoft Defender**.

    **Le fichier manifeste n’est** pas requis. Microsoft Defender pour le point de terminaison fonctionne sans fichier manifeste.

    **Onglet Options :** conserver les valeurs par défaut.

    **Onglet Limitations : conserver les valeurs** par défaut.

    :::image type="content" source="images/56dac54634d13b2d3948ab50e8d3ef21.png" alt-text="Onglet De limitation pour les paramètres de configuration" lightbox="images/56dac54634d13b2d3948ab50e8d3ef21.png":::

8. Sélectionnez **Enregistrer**. Le package est téléchargé vers Jamf Pro.

   :::image type="content" source="images/33f1ecdc7d4872555418bbc3efe4b7a3.png" alt-text="Processus de téléchargement du pack de paramètres de configuration pour le package lié aux paramètres de configuration" lightbox="images/33f1ecdc7d4872555418bbc3efe4b7a3.png":::

   Le déploiement du package peut prendre quelques minutes.

   :::image type="content" source="images/1626d138e6309c6e87bfaab64f5ccf7b.png" alt-text="Instance de téléchargement du package pour les paramètres de configuration" lightbox="images/1626d138e6309c6e87bfaab64f5ccf7b.png":::

9. Accédez à la page **Stratégies** .

   :::image type="content" source="images/f878f8efa5ebc92d069f4b8f79f62c7f.png" alt-text="Stratégies de paramètres de configuration" lightbox="images/f878f8efa5ebc92d069f4b8f79f62c7f.png":::

10. **Sélectionnez + Nouveau** pour créer une stratégie.

    :::image type="content" source="images/847b70e54ed04787e415f5180414b310.png" alt-text="Nouvelle stratégie des paramètres de configuration" lightbox="images/847b70e54ed04787e415f5180414b310.png":::


11. En **général,** entrez les détails suivants :

    - Nom complet : MDATP Onboarding Contoso 200329 v100.86.92 ou ultérieur

      :::image type="content" source="images/625ba6d19e8597f05e4907298a454d28.png" alt-text="Paramètres de configuration : intégration MDATP" lightbox="images/625ba6d19e8597f05e4907298a454d28.png":::

12. **Sélectionnez L’enregistrement périodique**.

    :::image type="content" source="images/68bdbc5754dfc80aa1a024dde0fce7b0.png" alt-text="L’enregistrement périodique des paramètres de configuration" lightbox="images/68bdbc5754dfc80aa1a024dde0fce7b0.png":::

13. Sélectionnez **Enregistrer**.

14. **Sélectionnez Packages > Configurer**.

    :::image type="content" source="images/8fb4cc03721e1efb4a15867d5241ebfb.png" alt-text="Option de configuration des packages" lightbox="images/8fb4cc03721e1efb4a15867d5241ebfb.png":::

15. Sélectionnez **le bouton** Ajouter à côté de **Microsoft Defender - Protection avancée contre les menaces et Antivirus Microsoft Defender**.

    :::image type="content" source="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png" alt-text="Option d’ajout de paramètres à MDATP MDA" lightbox="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png":::

16. Sélectionnez **Enregistrer**.

    :::image type="content" source="images/9d6e5386e652e00715ff348af72671c6.png" alt-text="Option d’enregistrer pour les paramètres de configuration" lightbox="images/9d6e5386e652e00715ff348af72671c6.png":::

17. Sélectionnez **l’onglet** Étendue.

    :::image type="content" source="images/8d80fe378a31143db9be0bacf7ddc5a3.png" alt-text="Onglet Étendue associé aux paramètres de configuration" lightbox="images/8d80fe378a31143db9be0bacf7ddc5a3.png":::

18. Sélectionnez les ordinateurs cibles.

    :::image type="content" source="images/6eda18a64a660fa149575454e54e7156.png" alt-text="Option d’ajout de groupes d’ordinateurs" lightbox="images/6eda18a64a660fa149575454e54e7156.png":::

    **Scope**

    Sélectionnez **Ajouter**.

    :::image type="content" source="images/1c08d097829863778d562c10c5f92b67.png" alt-text="Paramètres de configuration - ad1" lightbox="images/1c08d097829863778d562c10c5f92b67.png":::

    :::image type="content" source="images/216253cbfb6ae738b9f13496b9c799fd.png" alt-text="Paramètres de configuration - ad2" lightbox="images/216253cbfb6ae738b9f13496b9c799fd.png":::

    **Libre-service**

    :::image type="content" source="images/c9f85bba3e96d627fe00fc5a8363b83a.png" alt-text="Onglet Libre-service pour les paramètres de configuration" lightbox="images/c9f85bba3e96d627fe00fc5a8363b83a.png":::

19. Sélectionnez **Terminé**.

    :::image type="content" source="images/99679a7835b0d27d0a222bc3fdaf7f3b.png" alt-text="État d’intégration contoso avec une option pour le terminer" lightbox="images/99679a7835b0d27d0a222bc3fdaf7f3b.png":::

    :::image type="content" source="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png" alt-text="Page Stratégies" lightbox="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png":::
