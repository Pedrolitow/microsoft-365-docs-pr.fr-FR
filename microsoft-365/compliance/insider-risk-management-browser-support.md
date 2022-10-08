---
title: Découvrez et configurez la détection des signaux du navigateur de gestion des risques internes
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
ms.openlocfilehash: 5e0d29d96eeafe418d1773e20a73e33b402389fa
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503487"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>Découvrez et configurez la détection des signaux du navigateur de gestion des risques internes

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou involontaires, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Créés avec la confidentialité par conception, les utilisateurs sont pseudonymes par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Les navigateurs web sont souvent utilisés par les utilisateurs pour accéder aux fichiers sensibles et non sensibles au sein d’une organisation. La gestion des risques internes permet à votre organisation de détecter et d’agir sur les signaux d’exfiltration de navigateur pour tous les fichiers non exécutables affichés dans les navigateurs [Microsoft Edge](https://www.microsoft.com/edge) et [Google Chrome](https://www.google.com/chrome) . Avec ces signaux, les analystes et les enquêteurs peuvent agir rapidement lorsque l’une des activités suivantes est effectuée par des utilisateurs de stratégie dans l’étendue lors de l’utilisation de ces navigateurs :

- Fichiers copiés dans le stockage cloud personnel
- Fichiers imprimés sur des appareils locaux ou réseau
- Fichiers transférés ou copiés vers un partage réseau
- Fichiers copiés sur des périphériques USB
- Navigation sur des sites web à risque

Les signaux de ces événements sont détectés dans Microsoft Edge à l’aide des fonctionnalités de navigateur intégrées et du module complémentaire *d’extension de conformité Microsoft* . Dans Google Chrome, les clients utilisent *l’extension de conformité Microsoft* pour la détection de signal.

Le tableau suivant récapitule les activités détectées et la prise en charge des extensions pour chaque navigateur :

| **Activités détectées**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| Fichiers copiés dans le stockage cloud personnel         | Natif             | Extension         |
| Fichiers imprimés sur des appareils locaux ou réseau      | Natif             | Extension         |
| Fichiers transférés ou copiés vers un partage réseau | Extension          | Extension         |
| Fichiers copiés sur des périphériques USB                    | Extension          | Extension         |
| Navigation sur des sites web à risque                        | Extension          | Extension         |

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="common-requirements"></a>Conditions courantes

Avant d’installer le module complémentaire Microsoft Edge ou l’extension Google Chrome, les clients doivent s’assurer que les appareils pour les utilisateurs de stratégie d’étendue répondent aux exigences suivantes :

- La dernière version Windows 10 x64 est recommandée, au minimum Windows 10 build x64 1809 pour la prise en charge de la détection de signal. La détection des signaux du navigateur n’est actuellement pas prise en charge sur les appareils non Windows.
- Abonnement [Microsoft 365](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) actuel avec prise en charge de la gestion des risques internes.
- Les appareils doivent être [intégrés](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) au portail de conformité Microsoft Purview.

Pour connaître les exigences spécifiques de configuration du navigateur, consultez les sections Microsoft Edge et Google Chrome plus loin dans cet article.

## <a name="additional-requirements"></a>Autres conditions requises 

Si vous utilisez des stratégies basées sur le modèle *d’utilisation du navigateur à risque*, au moins un *indicateur de navigation* doit être sélectionné dans **les indicateurs de stratégie des paramètres** de gestion  >  des  > **risques internes**.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>Configurer la détection des signaux du navigateur pour Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>Configuration requise pour le navigateur Microsoft Edge

- Répondre aux exigences courantes
- Dernière version de Microsoft Edge x64 (91.0.864.41 ou ultérieure)
- Dernier module complémentaire *d’extension de conformité Microsoft* (1.0.0.44 ou version ultérieure)
- Edge.exe n’est pas configuré en tant que navigateur non autorisé

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>Option 1 : Configuration de base (recommandée pour les tests avec Edge)

Utilisez cette option pour configurer un seul selfhost d’ordinateur pour chaque appareil de votre organisation lors du test de la détection des signaux du navigateur.

Pour l’option d’installation de base, effectuez les étapes suivantes :

1. Accédez à [l’extension de conformité Microsoft](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. Installez l’extension.

### <a name="option-2-intune-setup-for-edge"></a>Option 2 : configuration Intune pour Edge

Utilisez cette option pour configurer l’extension et les exigences de votre organisation à l’aide de Intune.

Pour l’option de configuration Intune, effectuez les étapes suivantes :

1. Connectez-vous au [Centre de Endpoint Manager Administration Microsoft](https://endpoint.microsoft.com) à l’aide d’autorisations d’administrateur.
2. Accédez aux **profils de configuration**.
3. Sélectionnez **Créer le profil**.
4. Choisissez **Windows 10** comme plateforme.
5. Choisissez **Modèles d’administration** comme *type de profil* , puis sélectionnez **Créer.**
6. Sélectionnez l’onglet **Paramètres**.
7. Sélectionnez **Edge version 77 et ultérieure.**
8. Recherchez **des extensions** qui vous donnent une vue d’ensemble de tous les paramètres liés aux extensions.
9. Sélectionnez le paramètre **Contrôler les extensions installées en mode silencieux.**
10. Sélectionnez **Activé.**
11. Ajoutez l’ID d’extension lorsque vous y êtes invité : *lcmcgbabdcbngcbcfabdncmoppkajglo***.**
12. Sélectionnez **OK.**

### <a name="option-3-group-policy-setup-for-edge"></a>Option 3 : configuration stratégie de groupe pour Edge

Utilisez cette option pour configurer l’extension et les exigences à l’échelle de l’organisation à l’aide de stratégie de groupe.

Pour l’option de configuration stratégie de groupe, effectuez les étapes suivantes :

**Étape 1 : Importer le dernier fichier de modèle d’administration Microsoft Edge (.admx).**

Les appareils doivent être gérables à l’aide de stratégies de groupe et tous les [modèles d’administration Microsoft Edge doivent être importés](https://www.microsoft.com/edge/business/download) dans le magasin central stratégie de groupe. Pour plus d’informations, reportez-vous à l’article [Comment créer et gérer le magasin central des modèles d’administration de stratégie de groupe dans Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Étape 2 : Ajouter le module complémentaire *d’extension de conformité Microsoft* à la liste *d’installation de la force* .**

Effectuez les étapes suivantes pour ajouter l’extension :

1. Dans **l’éditeur de gestion stratégie de groupe**, accédez à votre unité d’organisation.
2. Développez le chemin d’accès **Suivant Stratégies de configuration** \>  \> ordinateur/utilisateur **Modèles d’administration Modèles** \> **d’administration classiques Extensions** \> **Microsoft Edge**\>. Ce chemin d’accès peut varier en fonction de la configuration de votre organisation.
3. Sélectionnez **Configurer les extensions installées en mode silencieux.**
4. Cliquez avec le bouton droit et **sélectionnez Modifier**.
5. Cochez la case **d’option Activée** .
6. Sélectionnez **Afficher**.
7. Pour **Valeur**, ajoutez l’entrée suivante : *lcmcgbabdcbngcbcfabdncmoppkajglo;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. Sélectionnez **OK** et **sélectionnez Appliquer**.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>Configurer la détection des signaux du navigateur pour Google Chrome

La prise en charge de la détection des signaux du navigateur de gestion des risques internes pour Google Chrome est activée via *l’extension de conformité Microsoft*. Cette extension prend également en charge endpoint DLP sur Chrome. Pour plus d’informations sur la prise en charge de endpoint DLP, consultez [Prise en main de l’extension de conformité Microsoft (préversion).](/microsoft-365/compliance/dlp-chrome-get-started)

### <a name="google-chrome-browser-requirements"></a>Configuration requise pour le navigateur Google Chrome

- Répondre aux exigences courantes
- Dernière version de Google Chrome x64
- Dernière version de *l’extension de conformité Microsoft* (2.0.0.183 ou version ultérieure)
- Chrome.exe n’est pas configuré en tant que navigateur non autorisé

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>Option 1 : Configuration de base (recommandée pour les tests avec Chrome)

Utilisez cette option pour configurer l’auto-installation d’une seule machine pour chaque appareil de votre organisation lors du test de la détection des signaux du navigateur.

Pour l’option d’installation de base, effectuez les étapes suivantes :

**Étape 1 : Activer les clés de Registre requises avec PowerShell**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>Ces clés de Registre sont nécessaires pour garantir les fonctionnalités appropriées de l’extension. Vous devez activer ces clés de Registre avant de tester les signaux.*

**Étape 2 : Installer *l’extension de conformité Microsoft***

1. Accédez à [l’extension de conformité Microsoft](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. Installez l’extension.

### <a name="option-2-intune-setup-for-chrome"></a>Option 2 : configuration Intune pour Chrome

Utilisez cette option pour configurer l’extension et les exigences de votre organisation à l’aide de Intune.

Pour l’option de configuration Intune, effectuez les étapes suivantes :

**Étape 1 : Activer la clé de Registre requise avec Intune**

1. Exécutez le script PowerShell suivant :

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. Connectez-vous au [Centre de Endpoint Manager Administration Microsoft](https://endpoint.microsoft.com).
3. Accédez aux **scripts d’appareils**  \> et sélectionnez **Ajouter.**
4. Accédez à l’emplacement du script créé lorsque vous y avez été invité.
5. Sélectionnez les paramètres suivants :

    - Exécutez ce script à l’aide des informations d’identification connectées : *Oui*
    - Appliquer la vérification de signature de script : *Non*
    - Exécuter un script dans l’hôte PowerShell 64 bits : *Oui*

6. Sélectionnez les groupes d’appareils appropriés et appliquez la stratégie.

**Étape 2 : Configurer Intune Force Install**

Avant d’ajouter l’extension Microsoft DLP Chrome à la liste des extensions installées par force, vous devez installer le fichier de modèle d’administration Chrome (.admx) pour Intune gestion. Pour obtenir des conseils pas à pas, consultez [Gérer Chrome Browser avec Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). Après avoir installé le fichier modèle d’administration, procédez comme suit :

1. Connectez-vous au [Centre de Endpoint Manager Administration Microsoft](https://endpoint.microsoft.com).
2. Accédez aux **profils de configuration**.
3. Sélectionnez **Créer le profil**.
4. Choisissez **Windows 10** comme *plateforme*.
5. Choisissez **Personnalisé** comme type de *profil* .
6. Sélectionnez l’onglet **Paramètres**.
7. Sélectionnez **Ajouter.**
8. Entrez les informations de stratégie suivantes :

    - OMA-URI : *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - Type de données : *Chaîne*
    - Valeur: *\<enabled/\>\<data id="ExtensionInstallForcelistDesc" value="1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/\>*

9. Sélectionnez **Créer**.

### <a name="option-3-group-policy-setup-for-chrome"></a>Option 3 : configuration stratégie de groupe pour Chrome

Utilisez cette option pour configurer l’extension et les exigences à l’échelle de l’organisation à l’aide de stratégie de groupe.

Pour l’option de configuration stratégie de groupe, effectuez les étapes suivantes :

**Étape 1 : Importer le fichier modèle d’administration Chrome**

Vos appareils doivent être gérables à l’aide de stratégie de groupe et tous les [modèles d’administration Chrome doivent être importés](https://chromeenterprise.google/browser/download/) dans le magasin central stratégie de groupe. Pour plus d’informations, reportez-vous à l’article [Comment créer et gérer le magasin central des modèles d’administration de stratégie de groupe dans Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Étape 2 : Activer la clé de Registre requise avec PowerShell**

1. Créez un script PowerShell avec le contenu suivant :

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Ouvrez la **Console de gestion des stratégies de groupe** et accédez à votre unité d’organisation.
3. Cliquez avec le bouton droit et **sélectionnez Créer un objet de stratégie de groupe dans ce domaine et liez-le ici**. Lorsque vous y êtes invité, attribuez un nom descriptif à cet objet stratégie de groupe (GPO). Par exemple, *script PowerShell immédiat DLP Chrome*.
4. Après avoir créé l’objet de stratégie de groupe, cliquez avec le bouton droit et sélectionnez **Modifier**. Cette sélection vous amène à l’objet stratégie de groupe.
5. Accédez aux paramètres du panneau de configuration \> **Préférences** \> de **l’ordinateur**, **paramètres des tâches planifiées**\>.
6. Cliquez avec le bouton droit sur la zone vide sous **Tâches planifiées** et sélectionnez **Nouvelle** \> **tâche immédiate (au moins Windows 7).**
7. Entrez un *nom* de tâche et *une description*.
8. Choisissez le compte correspondant pour exécuter la tâche immédiate. Par exemple, *NT Authority*.
9. Sélectionnez **Exécuter avec les autorisations maximales**.
10. Configurez la stratégie pour Windows 10.
11. Sous l’onglet **Actions** , **choisissez Démarrer un programme**.
12. Entrez le chemin d’accès au programme/script créé à **l’étape 1**.
13. Sélectionnez **Appliquer**.

**Étape 3 : Ajouter l’extension Chrome à la liste d’installation de force**

1. Dans **l’éditeur de gestion stratégie de groupe**, accédez à votre unité d’organisation.
2. Développez le chemin d’accès **suivant Stratégies de configuration** \>  \> ordinateur/utilisateur **Modèles d’administration Classiques** \> **modèles** \> d’administration **Google** \> **Google Chrome** \> **Extensions**. Ce chemin d’accès peut varier en fonction de la configuration de votre organisation.
3. Sélectionnez **Configurer la liste des extensions installées par force**.
4. Cliquez avec le bouton droit et **sélectionnez Modifier**.
5. Sélectionnez la case **d’option Activée** .
6. Sélectionnez **Afficher**.
7. Pour **Valeur**, ajoutez l’entrée suivante : *echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. Sélectionnez **OK** et **sélectionnez Appliquer**.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>Tester et vérifier les détections de signal du navigateur de gestion des risques internes

1. Créez une stratégie de gestion des risques internes avec les indicateurs d’appareil activés.
2. Pour tester la détection de signal pour les fichiers copiés dans le stockage cloud personnel, effectuez les étapes suivantes à partir d’un appareil Windows pris en charge :

    - Ouvrez un site web de partage de fichiers (Microsoft OneDrive, Google Drive, etc.) avec le type de navigateur que vous avez configuré pour la détection de signal.
    - Avec le navigateur, chargez un fichier non exécutable sur le site web.
3. Pour tester la détection de signal pour les fichiers imprimés sur des appareils locaux ou réseau, les fichiers transférés ou copiés vers un partage réseau et les fichiers copiés sur des périphériques USB, effectuez les étapes suivantes à partir d’un appareil Windows pris en charge :

    - Ouvrez un fichier non exécutable directement dans le navigateur. Le fichier doit être ouvert directement via Explorateur de fichiers ou ouvert dans un nouvel onglet de navigateur pour l’affichage plutôt qu’une page web.
    - Imprimez le fichier.
    - Enregistrez le fichier sur un périphérique USB.
    - Enregistrez le fichier sur un lecteur réseau.
  
4. Une fois que votre première stratégie de gestion des risques internes a été créée, vous commencerez à recevoir des alertes à partir d’indicateurs d’activité après environ 24 heures. Consultez le [tableau de bord Alertes](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) pour les alertes de gestion des risques internes pour les activités testées.
