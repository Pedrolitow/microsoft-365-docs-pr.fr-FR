---
title: Découvrir et configurer la détection des signaux du navigateur de gestion des risques internes
description: En savoir plus sur la détection des signaux du navigateur de gestion des risques internes dans Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
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
- purview-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- highpri
- tier1
ms.openlocfilehash: 9e3563348e0139fc092f5d40722d29bffd13b212
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68733634"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>Découvrir et configurer la détection des signaux du navigateur de gestion des risques internes

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Les navigateurs web sont souvent utilisés par les utilisateurs pour accéder à des fichiers sensibles et non sensibles au sein d’une organisation. La gestion des risques internes permet à votre organisation de détecter et d’agir sur les signaux d’exfiltration du navigateur pour tous les fichiers non exécutables affichés dans les navigateurs [Microsoft Edge](https://www.microsoft.com/edge) et [Google Chrome](https://www.google.com/chrome) . Avec ces signaux, les analystes et les enquêteurs peuvent agir rapidement lorsque l’une des activités à risque suivantes est effectuée par les utilisateurs de stratégie dans l’étendue lors de l’utilisation de ces navigateurs :

- Fichiers copiés dans le stockage cloud personnel
- Fichiers imprimés sur des appareils locaux ou réseau
- Fichiers transférés ou copiés vers un partage réseau
- Fichiers copiés sur des périphériques USB
- Navigation sur des sites web à risque
- Navigation sur des sites web potentiellement risqués

Les signaux pour ces événements sont détectés dans Microsoft Edge à l’aide des fonctionnalités de navigateur intégrées et à l’aide du module complémentaire *d’extension de conformité Microsoft* . Dans Google Chrome, les clients utilisent *l’extension de conformité Microsoft* pour la détection du signal.

Le tableau suivant récapitule les activités à risque identifiées et la prise en charge des extensions pour chaque navigateur :

| **Activités détectées** | **Microsoft Edge** | **Google Chrome** |
| ----------------------- | ------------------ | ----------------- |
| Fichiers copiés dans le stockage cloud personnel | Natif  | Extension  |
| Fichiers imprimés sur des appareils locaux ou réseau | Natif | Extension |
| Fichiers transférés ou copiés vers un partage réseau | Extension  | Extension  |
| Fichiers copiés sur des périphériques USB | Extension   | Extension    |
| Navigation sur des sites web à risque     | Extension   | Extension    |

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="common-requirements"></a>Conditions courantes

Avant d’installer le module complémentaire Microsoft Edge ou l’extension Google Chrome, les clients doivent s’assurer que les appareils des utilisateurs de stratégie dans l’étendue répondent aux exigences suivantes :

- La dernière version Windows 10 x64 est recommandée, au minimum Windows 10 build x64 1809 pour la prise en charge de la détection des signaux. La détection du signal du navigateur n’est actuellement pas prise en charge sur les appareils non Windows.
- Abonnement [Microsoft 365](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) actuel avec prise en charge de la gestion des risques internes.
- Les appareils doivent être [intégrés](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) au portail de conformité Microsoft Purview.

Pour connaître les exigences spécifiques de configuration du navigateur, consultez les sections Microsoft Edge et Google Chrome plus loin dans cet article.

## <a name="additional-requirements"></a>Autres conditions requises 

Si vous utilisez des stratégies basées sur le modèle *d’utilisation du navigateur à risque*, au moins un *indicateur de navigation* doit être sélectionné dans Paramètres **de gestion des** >  risques internes **Indicateurs** > **de stratégie**.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>Configurer la détection du signal du navigateur pour Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>Configuration requise du navigateur Microsoft Edge

- Répondre aux exigences courantes
- Dernière version de Microsoft Edge x64 (91.0.864.41 ou ultérieure)
- Dernier module complémentaire *d’extension de conformité Microsoft* (1.0.0.44 ou version ultérieure)
- Edge.exe n’est pas configuré en tant que navigateur non autorisé

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>Option 1 : Configuration de base (recommandée pour les tests avec Edge)

Utilisez cette option pour configurer un seul ordinateur auto-hôte pour chaque appareil de votre organisation lors du test de la détection du signal du navigateur.

Pour l’option d’installation de base, procédez comme suit :

1. Accédez à [Extension de conformité Microsoft](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. Installez l’extension.

### <a name="option-2-intune-setup-for-edge"></a>Option 2 : configuration Intune pour Edge

Utilisez cette option pour configurer l’extension et les exigences de votre organisation à l’aide de Intune.

Pour l’option d’installation Intune, procédez comme suit :

1. Connectez-vous au [Centre d’Administration Microsoft Endpoint Manager](https://endpoint.microsoft.com) à l’aide des autorisations d’administrateur.
2. Accédez à **Profils de configuration**.
3. Sélectionnez **Créer le profil**.
4. Choisissez **Windows 10** comme plateforme.
5. Choisissez **Modèles d’administration** comme *Type de profil* , puis sélectionnez **Créer.**
6. Sélectionnez l’onglet **Paramètres**.
7. Sélectionnez **Edge Version 77 et versions ultérieures.**
8. Recherchez **Extensions** qui vous donne une vue d’ensemble de tous les paramètres liés à l’extension.
9. Sélectionnez le paramètre **Contrôler les extensions installées en mode silencieux.**
10. Sélectionnez **Activé.**
11. Ajoutez l’ID d’extension lorsque vous y êtes invité : *lcmcgbabdcbngcbcfabdncmoppkajglo***.**
12. Sélectionnez **OK.**

### <a name="option-3-group-policy-setup-for-edge"></a>Option 3 : configuration stratégie de groupe pour Edge

Utilisez cette option pour configurer l’extension et les exigences à l’échelle de l’organisation à l’aide de stratégie de groupe.

Pour l’option d’installation stratégie de groupe, procédez comme suit :

**Étape 1 : Importez le dernier fichier de modèle d’administration Microsoft Edge (.admx).**

Les appareils doivent être gérables à l’aide de stratégies de groupe et tous les [modèles d’administration Microsoft Edge](https://www.microsoft.com/edge/business/download) doivent être importés dans le magasin central stratégie de groupe. Pour plus d’informations, reportez-vous à l’article [Comment créer et gérer le magasin central des modèles d’administration de stratégie de groupe dans Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Étape 2 : Ajoutez le module complémentaire *Extension de conformité Microsoft* à la liste *Forcer l’installation* .**

Effectuez les étapes suivantes pour ajouter l’extension :

1. Dans **l’Éditeur de gestion stratégie de groupe**, accédez à votre unité d’organisation .
2. Développez le chemin suivant Stratégies de  configuration \> \> **ordinateur/utilisateur** **Modèles** \> **d’administration Modèles d’administration Modèles** \> d’administration classiques **Extensions Microsoft Edge**\>. Ce chemin peut varier en fonction de la configuration de votre organisation.
3. Sélectionnez **Configurer les extensions installées en mode silencieux.**
4. Cliquez avec le bouton droit et sélectionnez **Modifier**.
5. Cochez la case d’option **Activé** .
6. Sélectionnez **Afficher**.
7. Pour **Valeur**, ajoutez l’entrée suivante : *lcmcgbabdcbngcbcfabdncmoppkajglo;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. Sélectionnez **OK** , puis **sélectionnez Appliquer**.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>Configurer la détection du signal du navigateur pour Google Chrome

La prise en charge de la détection des signaux du navigateur de gestion des risques internes pour Google Chrome est activée via *l’extension de conformité Microsoft*. Cette extension prend également en charge endpoint DLP sur Chrome. Pour plus d’informations sur la prise en charge de la protection contre la perte de données de point de terminaison, consultez [Prise en main de l’extension de conformité Microsoft (préversion)](/microsoft-365/compliance/dlp-chrome-get-started) .

### <a name="google-chrome-browser-requirements"></a>Configuration requise pour le navigateur Google Chrome

- Répondre aux exigences courantes
- Dernière version de Google Chrome x64
- Dernière version de *l’extension de conformité Microsoft* (2.0.0.183 ou ultérieure)
- Chrome.exe n’est pas configuré en tant que navigateur non autorisé

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>Option 1 : Configuration de base (recommandée pour les tests avec Chrome)

Utilisez cette option pour configurer un seul ordinateur auto-hôte pour chaque appareil de votre organisation lors du test de la détection du signal du navigateur.

Pour l’option d’installation de base, procédez comme suit :

**Étape 1 : Activer les clés de Registre requises avec PowerShell**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

> [!Important]
> Ces clés de Registre sont nécessaires pour garantir les fonctionnalités appropriées de l’extension. Vous devez activer ces clés de Registre avant de tester les signaux.*

**Étape 2 : Installer *l’extension de conformité Microsoft***

1. Accédez à [Extension de conformité Microsoft](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. Installez l’extension.

### <a name="option-2-intune-setup-for-chrome"></a>Option 2 : configuration Intune pour Chrome

Utilisez cette option pour configurer l’extension et les exigences de votre organisation à l’aide de Intune.

Pour l’option d’installation Intune, procédez comme suit :

**Étape 1 : Activer la clé de Registre requise avec Intune**

1. Exécutez le script PowerShell suivant :

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. Connectez-vous au [Centre de Administration Microsoft Endpoint Manager](https://endpoint.microsoft.com).
3. Accédez à **Scripts d’appareils**\>, puis sélectionnez **Ajouter.** 
4. Accédez à l’emplacement du script créé lorsque vous y avez été invité.
5. Sélectionnez les paramètres suivants :

    - Exécutez ce script à l’aide des informations d’identification de connexion : *Oui*
    - Appliquer la vérification de la signature du script : *Non*
    - Exécuter le script dans l’hôte PowerShell 64 bits : *Oui*

6. Sélectionnez les groupes d’appareils appropriés et appliquez la stratégie.

**Étape 2 : Configurer Intune Forcer l’installation**

Avant d’ajouter l’extension Microsoft DLP Chrome à la liste des extensions installées de force, vous devez installer le fichier modèle d’administration Chrome (.admx) pour la gestion Intune. Pour obtenir des instructions pas à pas, consultez [Gérer le navigateur Chrome avec Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). Après avoir installé le fichier de modèle d’administration, procédez comme suit :

1. Connectez-vous au [Centre de Administration Microsoft Endpoint Manager](https://endpoint.microsoft.com).
2. Accédez à **Profils de configuration**.
3. Sélectionnez **Créer le profil**.
4. Choisissez **Windows 10** comme *plateforme*.
5. Choisissez **Personnalisé** comme type *de profil* .
6. Sélectionnez l’onglet **Paramètres**.
7. Sélectionnez **Ajouter.**
8. Entrez les informations de stratégie suivantes :

    - OMA-URI : *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - Type de données : *Chaîne*
    - Valeur: *\<enabled/\>\<data id="ExtensionInstallForcelistDesc" value="1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/\>*

9. Sélectionnez **Créer**.

### <a name="option-3-group-policy-setup-for-chrome"></a>Option 3 : configuration stratégie de groupe pour Chrome

Utilisez cette option pour configurer l’extension et les exigences à l’échelle de l’organisation à l’aide de stratégie de groupe.

Pour l’option d’installation stratégie de groupe, procédez comme suit :

**Étape 1 : Importer le fichier de modèle d’administration Chrome**

Vos appareils doivent être gérables à l’aide de stratégie de groupe et tous les [modèles d’administration Chrome](https://chromeenterprise.google/browser/download/) doivent être importés dans le magasin central stratégie de groupe. Pour plus d’informations, reportez-vous à l’article [Comment créer et gérer le magasin central des modèles d’administration de stratégie de groupe dans Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Étape 2 : Activer la clé de Registre requise avec PowerShell**

1. Créez un script PowerShell avec le contenu suivant :

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Ouvrez la **Console de gestion des stratégies de groupe** et accédez à votre unité d’organisation.
3. Cliquez avec le bouton droit, sélectionnez **Créer un objet de stratégie de groupe dans ce domaine et liez-le ici**. Lorsque vous y êtes invité, attribuez un nom descriptif à cet objet stratégie de groupe (GPO). Par exemple, *DLP Chrome Immediate PowerShell Script*.
4. Après avoir créé l’objet de stratégie de groupe, cliquez avec le bouton droit et sélectionnez **Modifier**. Cette sélection vous permet d’accéder à l’objet stratégie de groupe.
5. Accédez à **Configuration de l’ordinateur** \> **Préférences** \> **panneau de configuration Paramètres** \> **Tâches planifiées**.
6. Cliquez avec le bouton droit sur la zone vide sous **Tâches planifiées** et sélectionnez **Nouvelle** \> **tâche immédiate (au moins Windows 7).**
7. Entrez un *nom* et une *description* de tâche.
8. Choisissez le compte correspondant pour exécuter la tâche immédiate. Par exemple, *autorité NT*.
9. Sélectionnez **Exécuter avec les autorisations maximales**.
10. Configurez la stratégie pour Windows 10.
11. Sous l’onglet **Actions** , choisissez **Démarrer un programme**.
12. Entrez le chemin du programme/script créé à **l’étape 1**.
13. Sélectionnez **Appliquer**.

**Étape 3 : Ajouter l’extension Chrome à la liste Forcer l’installation**

1. Dans **l’Éditeur de gestion stratégie de groupe**, accédez à votre unité d’organisation (UO).
2. Développez le chemin suivant Stratégies de  configuration \> \> **ordinateur/utilisateur** **Modèles** \> **d’administration Modèles d’administration Classiques** \> **Google** \> **Google Chrome** \> Extensions. Ce chemin peut varier en fonction de la configuration de votre organisation.
3. Sélectionnez **Configurer la liste des extensions installées de force**.
4. Cliquez avec le bouton droit et sélectionnez **Modifier**.
5. Sélectionnez la case d’option **Activé** .
6. Sélectionnez **Afficher**.
7. Pour **Valeur**, ajoutez l’entrée suivante : *echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. Sélectionnez **OK** , puis **sélectionnez Appliquer**.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>Tester et vérifier les détections de signal du navigateur de gestion des risques internes

1. Créez une stratégie de gestion des risques internes avec les indicateurs d’appareil activés.
2. Pour tester la détection des signaux pour les fichiers copiés dans le stockage cloud personnel, effectuez les étapes suivantes à partir d’un appareil Windows pris en charge :

    - Ouvrez un site web de partage de fichiers (Microsoft OneDrive, Google Drive, etc.) avec le type de navigateur que vous avez configuré pour la détection des signaux.
    - Avec le navigateur, chargez un fichier non exécutable sur le site web.
3. Pour tester la détection des signaux pour les fichiers imprimés sur des appareils locaux ou réseau, les fichiers transférés ou copiés vers un partage réseau et les fichiers copiés sur des périphériques USB, effectuez les étapes suivantes à partir d’un appareil Windows pris en charge :

    - Ouvrez un fichier non exécutable directement dans le navigateur. Le fichier doit être ouvert directement via Explorateur de fichiers ou dans un nouvel onglet de navigateur à afficher plutôt qu’une page web.
    - Imprimez le fichier.
    - Enregistrez le fichier sur un périphérique USB.
    - Enregistrez le fichier sur un lecteur réseau.
  
4. Une fois que votre première stratégie de gestion des risques internes a été créée, vous commencez à recevoir des alertes à partir des indicateurs d’activité après environ 24 heures. Consultez le [tableau de bord Alertes](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) pour les alertes de gestion des risques internes pour les activités testées.
