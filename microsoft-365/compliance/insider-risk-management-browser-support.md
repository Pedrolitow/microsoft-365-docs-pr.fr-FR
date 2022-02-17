---
title: En savoir plus et configurer la détection du signal du navigateur de gestion des risques internes
description: En savoir plus sur la détection du signal du navigateur de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: c3cb9e432f3ea94f88c63cfad928ba577471b420
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2022
ms.locfileid: "62879083"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>En savoir plus et configurer la détection du signal du navigateur de gestion des risques internes

Les navigateurs web sont souvent utilisés par les utilisateurs pour accéder aux fichiers sensibles et non sensibles au sein d’une organisation. La gestion des risques internes permet à votre organisation de détecter et d’agir sur les signaux d’exfiltration du navigateur pour tous les fichiers non exécutables dans les navigateurs [Microsoft Edge](https://www.microsoft.com/edge) et [Google Chrome](https://www.google.com/chrome). Avec ces signaux, les analystes et enquêteurs peuvent agir rapidement lorsque l’une des activités suivantes est effectuée par les utilisateurs de stratégies dans l’étendue lors de l’utilisation de ces navigateurs :

- Fichiers copiés dans le stockage cloud personnel
- Fichiers imprimés sur des périphériques locaux ou réseau
- Fichiers transférés ou copiés sur un partage réseau
- Fichiers copiés sur des périphériques USB

Les signaux de ces événements sont détectés dans Microsoft Edge à l’aide des fonctionnalités de navigateur intégrées et à l’aide du module extension de conformité *Microsoft*. Dans Google Chrome, les clients utilisent *l’extension de conformité Microsoft pour* la détection de signal.

Le tableau suivant récapitule les activités détectées et la prise en charge des extensions pour chaque navigateur :

| **Activités détectées**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| Fichiers copiés dans le stockage cloud personnel         | Natif             | Extension         |
| Fichiers imprimés sur des périphériques locaux ou réseau      | Natif             | Extension         |
| Fichiers transférés ou copiés sur un partage réseau | Extension          | Extension         |
| Fichiers copiés sur des périphériques USB                    | Extension          | Extension         |

## <a name="common-requirements"></a>Conditions courantes

Avant d’installer le module Microsoft Edge ou l’extension Google Chrome, les clients doivent s’assurer que les appareils des utilisateurs de stratégies dans l’étendue répondent aux exigences suivantes :

- La Windows 10 version x64 la plus récente est recommandée, au minimum Windows 10 version x64 1809 pour la prise en charge de la détection de signal. La détection du signal du navigateur n’est actuellement pas prise en charge sur les appareils Windows navigateur.
- Abonnement actuel [Microsoft 365 avec prise](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) en charge de la gestion des risques internes.
- Les appareils doivent être [intégrés](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) au portail Microsoft 365 conformité.

Pour des exigences de configuration de navigateur spécifiques, voir les sections Microsoft Edge et Google Chrome plus loin dans cet article.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>Configurer la détection du signal du navigateur pour Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>Microsoft Edge navigateur requis

- Répondre aux exigences courantes
- Microsoft Edge version x64, 91.0.864.41 ou supérieure
- *Extension de conformité Microsoft* version 1.0.0.44 ou supérieure
- Edge.exe n’est pas configuré en tant que navigateur nonallé

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>Option 1 : Configuration de base (recommandée pour les tests avec Edge)

Utilisez cette option pour configurer l’auto-host d’un seul ordinateur pour chaque appareil de votre organisation lors du test de la détection du signal du navigateur.

Pour l’option de configuration de base, effectuer les étapes suivantes :

1. Accédez à [l’extension de conformité Microsoft](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. Installez l’extension.

### <a name="option-2-intune-setup-for-edge"></a>Option 2 : configuration d’Intune pour Edge

Utilisez cette option pour configurer l’extension et la configuration requise pour votre organisation à l’aide d’Intune.

Pour l’option d’installation d’Intune, effectuer les étapes suivantes :

1. Connectez-vous au [Centre d Microsoft Endpoint Manager’administration à](https://endpoint.microsoft.com) l’aide des autorisations d’administrateur.
2. Accédez aux **profils de configuration**.
3. Sélectionnez **Créer le profil**.
4. Choisissez **Windows 10** en tant que plateforme.
5. Choisissez **Modèles d’administration en** *tant que type de profil* , puis **sélectionnez Créer.**
6. Sélectionnez l’onglet **Paramètres**.
7. **Sélectionnez Edge version 77 et ultérieures.**
8. Recherchez **des extensions** qui vous donnent une vue d’ensemble de tous les paramètres liés aux extensions.
9. Sélectionnez le paramètre **Contrôler les extensions installées en mode silencieux.**
10. **Sélectionnez Activé.**
11. Ajoutez l’ID d’extension à l’invite : *lcmcgbabdcbngcbcfabdncmoppkajglo***.**
12. **Sélectionnez OK.**

### <a name="option-3-group-policy-setup-for-edge"></a>Option 3 : Configuration de la stratégie de groupe pour Edge

Utilisez cette option pour configurer l’extension et la configuration requise à l’échelle de l’organisation à l’aide de la stratégie de groupe.

Pour l’option de configuration de la stratégie de groupe, effectuer les étapes suivantes :

**Étape 1 : Importez la dernière Microsoft Edge fichier de modèle d’administration (.admx).**

Les appareils doivent être gérables à l’aide de stratégies de groupe [et tous Microsoft Edge modèles](https://www.microsoft.com/edge/business/download) d’administration doivent être importés dans le magasin central de stratégie de groupe. Pour plus d’informations, reportez-vous à l’article [Comment créer et gérer le magasin central des modèles d’administration de stratégie de groupe dans Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Étape 2 : Ajoutez le module extension de conformité *Microsoft* à la *liste Force Install* .**

Pour ajouter l’extension, vous pouvez effectuer les étapes suivantes :

1. Dans **l’Éditeur de gestion des stratégies** de groupe, accédez à votre unité d’organisation.
2. Développez le chemin d’accès suivant **Stratégies d’administration** stratégies de configuration \>  \> utilisateur/ordinateur **Modèles** \> **d’administration classiques** \> **Microsoft Edge** \> **extensions**. Ce chemin d’accès peut varier en fonction de la configuration de votre organisation.
3. **Sélectionnez Configurer les extensions installées en mode silencieux.**
4. Cliquez avec le bouton droit et sélectionnez **Modifier**.
5. Cochez **la bouton d’radio** Activé.
6. Sélectionnez **Afficher**.
7. Pour **Value**, ajoutez l’entrée suivante : *lcmcgbabdcbngcbcfabdncmoppkajglo;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. **Sélectionnez OK** et sélectionnez **Appliquer**.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>Configurer la détection du signal du navigateur pour Google Chrome

La prise en charge de la détection du signal du navigateur de gestion des risques internes pour Google Chrome est activée via *l’extension de conformité Microsoft*. Cette extension prend également en charge endpoint DLP sur Chrome. Pour plus d’informations sur la prise en charge du point de terminaison DLP, voir Prise en charge de [l’extension de conformité Microsoft (prévisualisation).](/microsoft-365/compliance/dlp-chrome-get-started)

### <a name="google-chrome-browser-requirements"></a>Exigences relatives au navigateur Google Chrome

- Répondre aux exigences courantes
- Dernière version de Google Chrome x64
- *Extension de conformité Microsoft* version 2.0.0.183 ou supérieure
- Chrome.exe n’est pas configuré en tant que navigateur nonallé

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>Option 1 : Configuration de base (recommandée pour les tests avec Chrome)

Utilisez cette option pour configurer l’auto-host d’un seul ordinateur pour chaque appareil de votre organisation lors du test de la détection du signal du navigateur.

Pour l’option de configuration de base, effectuer les étapes suivantes :

**Étape 1 : Activer les clés de Registre requises avec PowerShell**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>Ces clés de Registre sont requises pour garantir la bonne fonctionnalité de l’extension. Vous devez activer ces clés de Registre avant de tester les signaux.*

**Étape 2 : Installer *l’extension de conformité Microsoft***

1. Accédez à [l’extension de conformité Microsoft](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. Installez l’extension.

### <a name="option-2-intune-setup-for-chrome"></a>Option 2 : configuration d’Intune pour Chrome

Utilisez cette option pour configurer l’extension et la configuration requise pour votre organisation à l’aide d’Intune.

Pour l’option d’installation d’Intune, effectuer les étapes suivantes :

**Étape 1 : Activer la clé de Registre requise avec Intune**

1. Exécutez le script PowerShell suivant :

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. Connectez-vous au [Microsoft Endpoint Manager Admin Center](https://endpoint.microsoft.com).
3. Accédez à **Périphériques** \> **Scripts et** sélectionnez **Ajouter.**
4. Accédez à l’emplacement du script créé lorsque vous y avez été invité.
5. Sélectionnez les paramètres suivants :

    - Exécutez ce script à l’aide des informations d’identification connectées : *Oui*
    - Appliquer la vérification de signature de script : *Non*
    - Exécuter un script dans l’hôte PowerShell 64 bits : *Oui*

6. Sélectionnez les groupes d’appareils appropriés et appliquez la stratégie.

**Étape 2 : Configurer l’installation force Intune**

Avant d’ajouter l’extension Microsoft DLP Chrome à la liste des extensions installées de force, vous devez installer le fichier de modèle d’administration Chrome (.admx) pour la gestion Intune. Pour obtenir des instructions pas à pas, voir [Gérer le navigateur Chrome avec Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). Après avoir installé le fichier de modèle d’administration, effectuer les étapes suivantes :

1. Connectez-vous au [Microsoft Endpoint Manager Admin Center](https://endpoint.microsoft.com).
2. Accédez aux **profils de configuration**.
3. Sélectionnez **Créer le profil**.
4. Choisissez **Windows 10** en tant que *plateforme*.
5. Choisissez **Personnalisé** comme type *de* profil.
6. Sélectionnez l’onglet **Paramètres**.
7. **Sélectionnez Ajouter.**
8. Entrez les informations de stratégie suivantes :

    - OMA-URI : *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - Type de données : *Chaîne*
    - Valeur : *\<enabled/\>\<data id=”ExtensionInstallForcelistDesc” value=”1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx″/\>*

9. Sélectionnez **Créer**.

### <a name="option-3-group-policy-setup-for-chrome"></a>Option 3 : Configuration de la stratégie de groupe pour Chrome

Utilisez cette option pour configurer l’extension et la configuration requise à l’échelle de l’organisation à l’aide de la stratégie de groupe.

Pour l’option de configuration de la stratégie de groupe, effectuer les étapes suivantes :

**Étape 1 : Importer le fichier de modèle d’administration Chrome**

Vos appareils doivent être gérables à l’aide de la stratégie de groupe et tous les modèles d’administration Chrome doivent être [importés](https://chromeenterprise.google/browser/download/) dans le magasin central de stratégie de groupe. Pour plus d’informations, reportez-vous à l’article [Comment créer et gérer le magasin central des modèles d’administration de stratégie de groupe dans Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Étape 2 : Activer la clé de Registre requise avec PowerShell**

1. Créez un script PowerShell avec le contenu suivant :

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Ouvrez la **Console de gestion des stratégies de groupe** et accédez à votre unité d’organisation.
3. Cliquez avec le bouton droit et **sélectionnez Créer un GPO dans ce domaine et l’lier ici**. Lorsque vous y invitez, attribuez un nom descriptif à cet objet de stratégie de groupe (GPO). Par exemple, *DLP Chrome Immediate PowerShell Script*.
4. Après avoir créé l’GPO, cliquez avec le bouton droit et sélectionnez **Modifier**. Cette sélection vous prend à l’objet de stratégie de groupe.
5. Accédez aux **paramètres** \> du **panneau de configuration** \> **Préférences de l’ordinateur Tâches programmées**\>.
6. Cliquez avec le bouton droit sur la zone vierge sous **Tâches** programmées  et \> sélectionnez Nouvelle **tâche immédiate (au moins Windows 7).**
7. Entrez un nom *et une* *description de tâche*.
8. Choisissez le compte correspondant pour exécuter la tâche immédiate. Par exemple, *NT Authority*.
9. Sélectionnez **Exécuter avec les autorisations maximales**.
10. Configurez la stratégie pour Windows 10.
11. Sous **l’onglet Actions** , **sélectionnez Démarrer un programme**.
12. Entrez le chemin d’accès au programme/script créé à **l’étape 1**.
13. Sélectionnez **Appliquer**.

**Étape 3 : Ajouter l’extension Chrome à la liste Force Install**

1. Dans **l’Éditeur de gestion des stratégies** de groupe, accédez à votre unité d’organisation.
2. Développez le chemin **d’accès suivant Computer/User configuration** \> **Policies** \> **Administrative templates** \> **Classic administrative templates** \> **Google** \> **Google Chrome** \> **Extensions**. Ce chemin d’accès peut varier en fonction de la configuration de votre organisation.
3. **Sélectionnez Configurer la liste des extensions installées de force**.
4. Cliquez avec le bouton droit et sélectionnez **Modifier**.
5. Sélectionnez **la bouton d’radio** Activé.
6. Sélectionnez **Afficher**.
7. Pour **Value**, ajoutez l’entrée suivante : *echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. **Sélectionnez OK** et sélectionnez **Appliquer**.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>Tester et vérifier les détections de signal du navigateur de gestion des risques internes

1. Créez une stratégie de gestion des risques internes avec des indicateurs d’appareil activés.
2. Pour tester la détection du signal pour les fichiers copiés dans le stockage cloud personnel, effectuer les étapes suivantes à partir d’un Windows pris en charge :

    - Ouvrez un site web de partage de fichiers (Microsoft OneDrive, Google Drive, etc.) avec le type de navigateur que vous avez configuré pour la détection de signal.
    - Avec le navigateur, téléchargez un fichier non exécutable sur le site web.
3. Pour tester la détection du signal pour les fichiers imprimés sur des périphériques locaux ou réseau, les fichiers transférés ou copiés sur un partage réseau et les fichiers copiés sur des périphériques USB, effectuer les étapes suivantes à partir d’un appareil Windows pris en charge :

    - Ouvrez un fichier non exécutable directement dans le navigateur. Le fichier doit être ouvert directement par le biais de l’Explorateur de fichiers ou ouvert dans un nouvel onglet de navigateur pour être affiché au lieu d’une page web.
    - Imprime le fichier.
    - Enregistrez le fichier sur un périphérique USB.
    - Enregistrez le fichier sur un lecteur réseau.
  
4. Une fois votre première stratégie de gestion des risques internes créée, vous commencerez à recevoir des alertes des indicateurs d’activité après environ 24 heures. Consultez le [tableau de bord Alertes](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) pour les alertes de gestion des risques internes pour les activités testées.
