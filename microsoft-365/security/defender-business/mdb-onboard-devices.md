---
title: Intégrer des appareils à Microsoft Defender pour Les Entreprises
description: En savoir plus sur les options d’intégration d’appareil dans Microsoft Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/14/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: c5de66418b242beb975cce0d6ece299753360c99
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504791"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Intégrer des appareils à Microsoft Defender pour Les Entreprises

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement [Microsoft 365 Business Premium clients,](../../business-premium/index.md) à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Avec Microsoft Defender entreprise, vous avez le choix entre plusieurs options pour intégrer les appareils de votre organisation. Cet article vous présente vos options et inclut une vue d’ensemble du fonctionnement de l’intégration.

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="get-the-device-onboarding-guide"></a>Obtenir le guide d’intégration d’appareil

Utilisez le guide et les informations suivants pour choisir la meilleure option pour votre organisation.

[:::image type="content" source="media/mdb-device-onboarding.png" alt-text="Capture d’écran du diagramme d’intégration d’appareil":::](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.pdf) <br/>
[PDF](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.pdf) | [Visio](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.vsdx)

## <a name="what-to-do"></a>Procédure

1. [Consultez les options d’intégration des appareils](#device-onboarding-methods) et sélectionnez une méthode. 

   - [Utiliser l’intégration automatique pour Windows appareils déjà inscrits dans Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
   - [Utiliser un script local pour intégrer des Windows ou macOS](#local-script-in-defender-for-business)
   - [Utiliser Microsoft Endpoint Manager pour intégrer des appareils Windows, macOS ou mobiles](#microsoft-endpoint-manager)
   - [En savoir plus sur l’intégration d’appareils avec la configuration de sécurité de Microsoft Defender entreprise](#microsoft-defender-for-business-security-configuration)

2. [Exécutez un test de détection](#run-a-detection-test) sur les appareils Windows nouvellement intégrés.

3. [Consultez les étapes suivantes](#next-steps). 

Cet article inclut également des informations [sur laboardage d’un appareil](#offboarding-a-device).

## <a name="device-onboarding-methods"></a>Méthodes d’intégration d’appareil

Defender for Business vous propose plusieurs méthodes différentes pour l’intégration d’appareils, que vous utilisiez déjà Microsoft Endpoint Manager ou que vous vouliez simplement une expérience d’intégration simplifiée. Les méthodes les plus couramment utilisées pour intégrer des appareils à Defender for Business sont les suivantes :

- **L’intégration** automatique Windows appareils déjà inscrits dans Microsoft Endpoint Manager. L’intégration automatique définit une connexion entre Defender entreprise et Microsoft Endpoint Manager, puis Windows appareils à Defender for Business. Pour utiliser cette option, vos appareils doivent déjà être inscrits Endpoint Manager. Pour en savoir plus, [consultez l’intégration automatique](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager).

- **Script local pour** intégrer manuellement Windows appareils macOS à Defender for Business. Vous pouvez intégrer jusqu’à 10 appareils à la fois à l’aide du script local. Pour plus d’informations, [voir script local dans Defender for Business](#local-script-in-defender-for-business).

- **Microsoft Intune** ou **Microsoft Endpoint Manager** pour intégrer Windows, macOS et appareils mobiles. Vous pouvez inscrire des appareils dans Endpoint Manager, puis intégrer vos appareils à Defender for Business. [Microsoft 365 Business Premium](../../business-premium/index.md) clients ont déjà des [Microsoft Intune](/mem/intune/fundamentals/what-is-intune), et les deux Microsoft Intune [gestion](/mem/intune/enrollment/device-enrollment) des appareils mobiles font désormais partie de Endpoint Manager. Pour utiliser cette méthode, voir [Microsoft Endpoint Manager](#microsoft-endpoint-manager).

- **Configuration de la sécurité De Microsoft Defender entreprise pour** intégrer les appareils directement dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Pour utiliser cette option, vous configurez certains paramètres pour faciliter la communication entre Defender for Business et Endpoint Manager. Ensuite, vous devez intégrer des appareils dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) à l’aide d’un package que vous sélectionnez, téléchargez et exécutez sur chaque appareil. Une relation d’confiance est établie entre les appareils et Azure Active Directory (Azure AD), et les stratégies de sécurité de Defender for Business sont poussées vers les appareils. Pour en savoir plus, [consultez la configuration de la sécurité de Microsoft Defender entreprise](#microsoft-defender-for-business-security-configuration). 

> [!IMPORTANT]
> Si un problème se produit et que votre processus d’intégration échoue, consultez [La résolution des problèmes de Microsoft Defender entreprise](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Intégration automatique pour les appareils Windows inscrits dans Microsoft Endpoint Manager

L’option d’intégration automatique s’applique Windows appareils uniquement. L’intégration automatique est disponible si les conditions suivantes sont remplies :

- Votre organisation utilisait déjà Microsoft Endpoint Manager, Microsoft Intune ou la gestion des périphériques mobiles (MDM) dans Microsoft Intune avant d’obtenir Defender pour les entreprises

- Vous avez déjà Windows des appareils inscrits dans Endpoint Manager

Si Windows appareils sont déjà inscrits dans Endpoint Manager, Defender entreprise détecte ces appareils pendant que vous êtes en train de configurer Defender pour les entreprises. Vous serez invité à vous demander si vous souhaitez utiliser l’intégration automatique pour l’ensemble ou une partie de Windows appareils. Vous pouvez intégrer tous les Windows en même temps, ou sélectionner des appareils spécifiques pour commencer, puis ajouter d’autres appareils ultérieurement.

> [!TIP]
> Nous vous recommandons de sélectionner l’option « Tous les appareils inscrits ». Ainsi, lorsque Windows sont inscrits Endpoint Manager ultérieurement, ils sont automatiquement intégrés à Defender for Business. En outre, si vous gérez les stratégies et paramètres de sécurité dans Endpoint Manager, nous vous recommandons de basculer vers le portail Microsoft 365 Defender pour gérer vos appareils, stratégies et paramètres. Pour plus d’informations, voir [Choisir où gérer les stratégies et les appareils de sécurité](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

Pour en savoir plus sur l’intégration automatique, consultez l’étape 2 de l’Assistant pour [configurer Microsoft Defender pour les entreprises](mdb-use-wizard.md).

## <a name="local-script-in-defender-for-business"></a>Script local dans Defender for Business

Vous pouvez utiliser un script local pour intégrer des Windows mac. Lorsque vous exécutez le script d’intégration sur un appareil, il crée une relation d’confiance avec Azure Active Directory (si cette confiance n’existe pas encore), inscrit l’appareil dans Microsoft Endpoint Manager (s’il n’est pas déjà inscrit), puis l’insérait à Defender pour Entreprise. Cette méthode est utile pour l’intégration d’appareils dans Defender for Business. Vous pouvez intégrer jusqu’à 10 appareils à la fois.

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis sous Gestion **des appareils,** choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, Windows 10 **11** ou **macOS**, puis, dans **la section Méthode** de déploiement, choisissez **Script local**. 

4. **Sélectionnez Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible. (Si vous avez sélectionné **macOS**, sélectionnez également Télécharger le **package d’installation** et enregistrez-le sur votre appareil amovible.)

5. Suivez les instructions du tableau suivant :

   | Système d’exploitation | Procedure |
   |---|---|
   | Windows | 1. Sur un appareil Windows, extrayez le contenu du package de configuration à un emplacement, tel que le dossier Bureau. Vous devez avoir un fichier nommé `WindowsDefenderATPLocalOnboardingScript.cmd`. <br/><br/>2. Ouvrez l’invite de commandes en tant qu’administrateur.<br/><br/>3. Tapez l’emplacement du fichier de script. Par exemple, si vous avez copié le fichier dans le dossier Bureau, tapez : `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`, puis appuyez sur Entrée (ou sélectionnez **OK**).<br/><br/>4. Une fois le script exécuté, exécutez [un test de détection](#run-a-detection-test). |
   | macOS | 1. Sur un ordinateur Mac, enregistrez le package d’installation dans `wdav.pkg` un répertoire local. <br/><br/>2. Enregistrez le package d’intégration dans `WindowsDefenderATPOnboardingPackage.zip` le répertoire que vous avez utilisé pour le package d’installation. <br/><br/>3. Utilisez Finder pour accéder `wdav.pkg` à votre site enregistré, puis ouvrez-le.<br/><br/>4. Sélectionnez **Continuer**, acceptez les termes du contrat de licence, puis entrez votre mot de passe à l’invite.<br/><br/>5. Vous serez invité à autoriser l’installation d’un pilote microsoft (« Extension système bloquée » ou « L’installation est en attente », ou les deux. Le pilote doit être autorisé à être installé. Pour autoriser l’installation, sélectionnez **Open Security Preferences** ou **Open System PreferencesSecurity** >  **& Privacy**, puis **sélectionnez Autoriser**.<br/><br/>6. Utilisez la commande Python suivante dans Bash pour exécuter le package d’intégration : `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`. <br/><br/>7. Pour confirmer que l’appareil est associé à votre organisation, utilisez la commande Python suivante dans Bash : `mdatp health --field org_id`<br/><br/>8. Si vous utilisez macOS 10.15 (Îles) ou une ultérieure, accordez le consentement de Defender for Business pour protéger votre appareil. Accédez **à System PreferencesSecurity** >  **&** **PrivacyPrivacyFull** >  >  **Disk Access**.  Sélectionnez l’icône de verrouillage pour apporter des modifications (en bas de la boîte de dialogue), puis sélectionnez Microsoft Defender Entreprise (ou Defender pour le point de terminaison, si c’est ce que vous voyez). <br/><br/>9. Pour vérifier que l’appareil est intégré, utilisez la commande suivante dans Bash : `mdatp health --field real_time_protection_enabled`    |

## <a name="microsoft-endpoint-manager"></a>Gestionnaire de point de terminaison Microsoft

Si vous utilisiez déjà Endpoint Manager (qui inclut Microsoft Intune et Gestion des appareils mobiles), avant d’obtenir Defender pour Entreprise, vous pouvez continuer à utiliser Endpoint Manager pour intégrer les appareils de votre organisation. Avec Endpoint Manager, vous pouvez intégrer des ordinateurs, des tablettes et des téléphones, y compris des appareils iOS et Android.

Voir [Inscription des appareils dans Microsoft Intune](/mem/intune/enrollment/device-enrollment).

## <a name="microsoft-defender-for-business-security-configuration"></a>Configuration de la sécurité de Microsoft Defender pour les entreprises

> [!NOTE]
> Si vous utilisez déjà Endpoint Manager pour gérer vos appareils et vos stratégies de sécurité, ignorez cette méthode et [Microsoft Endpoint Manager à la](#microsoft-endpoint-manager) place.

La configuration de la sécurité de Microsoft Defender pour les entreprises a été conçue sur une fonctionnalité appelée Gestion de la sécurité [pour Microsoft Defender pour point de terminaison (prévisualisation).](/mem/intune/protect/mde-security-integration) Il vous permet d’intégrer des appareils à Defender for Business dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) sans que ces appareils soient entièrement inscrits au Microsoft Endpoint Manager préalablement. 

Cette méthode vous permet d’intégrer des appareils et de gérer vos stratégies antivirus et de pare-feu dans le Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Voici comment tout fonctionne :

1. Vous téléchargez un package d’intégration à partir du portail Microsoft 365 Defender, puis exécutez le package sur vos appareils pour intégrer ces appareils à Defender for Business.

2. L’exécution du package établit une relation d’confiance entre chaque appareil (si l’trust n’existe pas déjà) et Azure Active Directory (Azure AD). 

3. Les appareils communiquent avec Endpoint Manager à l’aide de leur identité Azure AD, et les stratégies de sécurité dans Defender for Business sont poussées vers les appareils.

4. Vous pouvez afficher vos appareils et stratégies à la fois dans le portail Microsoft 365 Defender et dans le centre d’administration Endpoint Manager([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

Pour utiliser cette option, certains paramètres doivent être configurés au préalable. Pour en savoir plus, y compris les conditions préalables et les systèmes d’exploitation pris en charge, voir [Gérer Microsoft Defender pour endpoint](/mem/intune/protect/mde-security-integration) sur les appareils Microsoft Endpoint Manager.

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Une fois que vous avez intégré des appareils Windows à Defender for Business, vous pouvez exécuter un test de détection sur un appareil Windows pour vous assurer que tout fonctionne correctement.

1. Sur le Windows, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez l’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre Invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécuté, la fenêtre d’invite de commandes se ferme automatiquement. Si elle réussit, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour le périphérique nouvellement intégré dans environ 10 minutes.

## <a name="gradual-device-onboarding"></a>Intégration progressive d’appareils

Vous pouvez intégrer les appareils de votre organisation par phases. *Nous appelons cela l’intégration progressive d’appareils*. 

1. Identifiez un ensemble d’appareils à intégrer.

2. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in.

3. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis sous Gestion **des appareils,** choisissez **Intégration**.

4. Sélectionnez un système d’exploitation (**Windows 10 et 11),** puis choisissez une méthode d’intégration (par exemple, **un script local**). Suivez les instructions fournies pour la méthode que vous avez sélectionnée.

5. Répétez ce processus pour chaque ensemble d’appareils que vous souhaitez intégrer. 

> [!TIP]
> Vous n’avez pas besoin d’utiliser le même package d’intégration chaque fois que vous intégrerez des appareils. Par exemple, vous pouvez utiliser un script local pour intégrer certains appareils, puis choisir une autre méthode pour intégrer davantage d’appareils.

## <a name="offboarding-a-device"></a>Boarding d’un appareil

Si vous souhaitez mettre hors service un appareil, utilisez l’une des procédures suivantes :

| Système d’exploitation | Procedure |
|---|---|
| Windows | 1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.<br/><br/>2. Dans le volet de navigation, choisissez **Paramètres**, puis les **points de terminaison**.<br/><br/>3. Sous **Gestion des appareils**, sélectionnez **Offboarding (Boarding).**<br/><br/>4. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, sous Horsboard d’un **appareil, dans** **la section Méthode** de déploiement, choisissez **Script local**. <br/><br/>5. Dans l’écran de confirmation, examinez les informations, puis choisissez **Télécharger** pour continuer.<br/><br/>6. **Sélectionnez Télécharger le package deboarding**. Nous vous recommandons d’enregistrer le package de déboardage sur un lecteur amovible.<br/><br/>7. Exécutez le script sur chaque appareil que vous souhaitez hors d’board.| 
| macOS | 1. Go to **FinderApplications** > . <br/><br/>2. Cliquez avec le bouton droit sur Microsoft Defender pour les entreprises, puis choisissez **Déplacer vers la corbeille**. <br/><br/>--- ou --- <br/><br/> Utilisez la commande suivante : `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.|

> [!IMPORTANT]
> Laboarding d’un appareil entraîne l’arrêt de l’envoi de données à Defender for Business. Toutefois, les données reçues avant laboarding sont conservées pendant six (6) mois au plus.

## <a name="next-steps"></a>Étapes suivantes

Procédez comme il se doit pour :

- [Étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les entreprises](mdb-configure-security-settings.md)

- [Commencer à utiliser Microsoft Defender pour les entreprises](mdb-get-started.md) 
