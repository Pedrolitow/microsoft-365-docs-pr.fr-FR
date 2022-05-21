---
title: Intégrer des appareils à Microsoft Defender pour les PME
description: Découvrez comment intégrer des appareils à Defender entreprise pour protéger vos appareils du premier jour.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 8f716f692687276e5c1c4482429ab016f9574f2f
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621319"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Intégrer des appareils à Microsoft Defender pour les PME

Avec Microsoft Defender pour les PME, vous avez le choix entre plusieurs options pour intégrer les appareils de votre entreprise. Cet article vous guide tout au long de vos options et inclut une vue d’ensemble du fonctionnement de l’intégration.

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="what-to-do"></a>Procédure

1. Sélectionnez l’onglet de votre système d’exploitation : **clients Windows**, **ordinateurs macOS** ou **appareils mobiles**.
2. Affichez vos options d’intégration et suivez les instructions de l’onglet sélectionné.
3. Passez à vos étapes suivantes.

## <a name="windows-clients"></a>[**clients Windows**](#tab/WindowsClientDevices)

## <a name="windows-clients"></a>clients Windows

Choisissez l’une des options suivantes pour intégrer Windows appareils clients à Defender entreprise :

- [Script local](#local-script-for-windows-clients) (pour l’intégration manuelle d’appareils dans le portail Microsoft 365 Defender)
- [stratégie de groupe](#group-policy-for-windows-clients) (si vous utilisez déjà stratégie de groupe dans votre organisation)
- [Microsoft Intune](#microsoft-intune-for-windows-clients) (inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md))


### <a name="local-script-for-windows-clients"></a>Script local pour les clients Windows

Vous pouvez utiliser un script local pour intégrer Windows appareils clients. Lorsque vous exécutez le script d’intégration sur un appareil, il crée une approbation avec Azure Active Directory (si cette approbation n’existe pas déjà), inscrit l’appareil dans Microsoft Intune (s’il n’est pas déjà inscrit), puis l’intègre à Defender entreprise. La méthode de script local fonctionne même si vous n’avez pas de Intune actuellement. Nous vous recommandons d’intégrer jusqu’à 10 appareils à la fois à l’aide de cette méthode.

> [!TIP]
> Nous vous recommandons d’intégrer jusqu’à 10 appareils à la fois lorsque vous utilisez la méthode de script local.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, dans la section **Méthode de déploiement**, choisissez **Script local**. 

4. Sélectionnez **Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible.

5. Sur un appareil Windows, extrayez le contenu du package de configuration à un emplacement, tel que le dossier Bureau. Vous devez avoir un fichier nommé `WindowsDefenderATPLocalOnboardingScript.cmd`. 

6. Ouvrez une fenêtre d’invite de commandes en tant qu’administrateur.

7. Tapez l’emplacement du fichier de script. Par exemple, si vous avez copié le fichier dans le dossier Bureau, vous tapez `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`, puis appuyez sur la touche Entrée (ou sélectionnez **OK**).

8. Une fois le script exécuté, passez à [exécuter un test de détection](#running-a-detection-test-on-a-windows-client).

### <a name="group-policy-for-windows-clients"></a>stratégie de groupe pour les clients Windows

Si vous préférez utiliser stratégie de groupe pour intégrer Windows clients, suivez les instructions fournies dans [Intégrer des appareils Windows à l’aide de stratégie de groupe](../defender-endpoint/configure-endpoints-gp.md). Cet article décrit les étapes d’intégration à Microsoft Defender pour point de terminaison ; toutefois, les étapes d’intégration à Defender entreprise sont similaires.

### <a name="microsoft-intune-for-windows-clients"></a>Microsoft Intune pour les clients Windows

Si votre abonnement inclut Intune, vous pouvez intégrer Windows clients et d’autres appareils dans le centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Par exemple, si vous avez [Microsoft 365 Business Premium](../../business/index.yml), vous avez Intune dans le cadre de votre abonnement.  

Plusieurs méthodes sont disponibles pour inscrire des appareils dans Intune. Nous vous recommandons de commencer par l’une des méthodes suivantes :

- [Activer Windows l’inscription automatique](/mem/intune/enrollment/windows-enroll) pour les appareils appartenant à l’entreprise ou gérés par l’entreprise
- [Demandez aux utilisateurs d’inscrire leurs propres appareils Windows 10/11 dans Intune](/mem/intune/user-help/enroll-windows-10-device)

#### <a name="to-enable-automatic-enrollment-for-windows-devices"></a>Pour activer l’inscription automatique pour les appareils Windows

Lorsque vous configurez l’inscription automatique, les utilisateurs ajoutent leur compte professionnel à l’appareil. En arrière-plan, l’appareil inscrit et joint Azure Active Directory (Azure AD) et est inscrit dans Intune.

1. Accédez à la Portail Azure ([https://portal.azure.com/](https://portal.azure.com/)) et connectez-vous. 

2. Sélectionnez **Azure Active Directory** >  **Mobilité (GPM et GAM)** > **Microsoft Intune**.

3. Configurez **l’étendue utilisateur MDM** et **l’étendue de l’utilisateur GAM**.

   :::image type="content" source="media/mem-mam-scope-azure-ad.png" alt-text="Capture d’écran de la définition de l’étendue utilisateur MDM et de l’étendue de l’utilisateur GAM dans Intune.":::

   - Pour l’étendue utilisateur MDM, nous vous recommandons de sélectionner **Tout** pour que tous les utilisateurs puissent inscrire automatiquement leurs appareils Windows.
   - Dans la section Étendue de l’utilisateur MAM, nous vous recommandons d’utiliser les valeurs par défaut suivantes pour les URL :

       - **URL des conditions d’utilisation de la gestion des données de référence**
       - **URL de détection MDM**
       - **URL de conformité GAM**

4. Cliquez sur **Enregistrer**.

5. Une fois qu’un appareil a été inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Microsoft Defender pour les PME](mdb-create-edit-device-groups.md).


> [!TIP]
> Pour en savoir plus sur l’inscription automatique, consultez [Activer Windows l’inscription automatique](/mem/intune/enrollment/windows-enroll).

#### <a name="to-have-users-enroll-their-own-windows-devices"></a>Pour que les utilisateurs inscrivent leurs propres appareils Windows

1. Regardez la vidéo suivante pour voir comment fonctionne l’inscription : <br/><br/>

   > [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]  

2. Partagez cet article avec les utilisateurs de votre organisation : [Inscrire des appareils Windows 10/11 dans Intune](/mem/intune/user-help/enroll-windows-10-device).

3. Une fois qu’un appareil a été inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Microsoft Defender pour les PME](mdb-create-edit-device-groups.md).

### <a name="running-a-detection-test-on-a-windows-client"></a>Exécution d’un test de détection sur un client Windows

Une fois que vous avez intégré les appareils Windows à Defender pour les PME, vous pouvez exécuter un test de détection sur un appareil Windows pour vous assurer que tout fonctionne correctement.

1. Sur l’appareil Windows, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez une fenêtre d’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre d’invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécutée, la fenêtre d’invite de commandes se ferme automatiquement. En cas de réussite, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour l’appareil nouvellement intégré dans environ 10 minutes.

## <a name="view-a-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

Pour afficher la liste des appareils intégrés à Defender entreprise, dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sous **Points de terminaison**, choisissez **Inventaire des appareils**.

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet qui correspond au système d’exploitation sur les appareils [(clients Windows, serveur Windows, macOS ou appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration d’appareils, passez à [l’étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les PME](mdb-configure-security-settings.md)
- Consultez [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md).

## <a name="macos"></a>[**macOS**](#tab/macOSdevices)

## <a name="macos-computers"></a>ordinateurs macOS

> [!NOTE]
> - Nous vous recommandons d’utiliser un [script local pour intégrer macOS appareils](#local-script-for-macos). Bien que vous puissiez [configurer l’inscription pour macOS appareils dans Intune](/mem/intune/enrollment/macos-enroll), le script local est la méthode la plus simple pour intégrer macOS appareils à Defender entreprise. 

Choisissez l’une des options suivantes pour intégrer macOS appareils :

- [Script local pour macOS](#local-script-for-macos) (*recommandé*)
- [Intune pour macOS](#microsoft-intune-for-macos)

### <a name="local-script-for-macos"></a>Script local pour macOS

Lorsque vous exécutez le script local sur un appareil macOS, il crée une approbation avec Azure Active Directory (si cette approbation n’existe pas déjà), inscrit l’appareil dans Microsoft Intune (s’il n’est pas déjà inscrit), puis l’intègre à Defender entreprise. La méthode de script local fonctionne même si vous n’avez pas de Intune actuellement. Nous vous recommandons d’intégrer jusqu’à 10 appareils à la fois à l’aide de cette méthode.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez **macOS**, puis, dans la section **Méthode de déploiement**, choisissez **Script local**. 

4. Sélectionnez **Télécharger le package d’intégration** et enregistrez-le sur un lecteur amovible. Sélectionnez également **Télécharger le package d’installation** et enregistrez-le sur votre appareil amovible.

5. Sur un appareil macOS, enregistrez le package d’installation dans `wdav.pkg` un répertoire local.

6. Enregistrez le package d’intégration dans `WindowsDefenderATPOnboardingPackage.zip` le répertoire que vous avez utilisé pour le package d’installation.

7. Utilisez Finder pour accéder à `wdav.pkg` votre enregistrement, puis ouvrez-le.

8. Sélectionnez **Continuer**, acceptez les termes du contrat de licence, puis entrez votre mot de passe lorsque vous y êtes invité.

9. Vous êtes invité à autoriser l’installation d’un pilote de Microsoft (« Extension système bloquée » ou « L’installation est en attente », ou les deux. Le pilote doit être autorisé à être installé. Pour autoriser l’installation, sélectionnez **Ouvrir les préférences de sécurité** ou **Ouvrir les préférences** >  système **& confidentialité**, puis **sélectionnez Autoriser**.

10. Utilisez la commande Python suivante dans Bash pour exécuter le package d’intégration : `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.sh`

11. Une fois qu’un appareil a été inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Microsoft Defender pour les PME](mdb-create-edit-device-groups.md).

### <a name="microsoft-intune-for-macos"></a>Microsoft Intune pour macOS

Si votre abonnement inclut Microsoft Intune, vous pouvez intégrer macOS appareils dans le centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Par exemple, si vous avez [Microsoft 365 Business Premium](../../business/index.yml), vous avez Intune dans le cadre de votre abonnement.  

Plusieurs méthodes sont disponibles pour inscrire des appareils dans Intune. Nous vous recommandons de commencer par l’une des méthodes suivantes :

- [Choisir une option pour les appareils macOS appartenant à l’entreprise](#options-for-company-owned-macos-devices)
- [Demandez aux utilisateurs d’inscrire leurs propres appareils macOS dans Intune](#ask-users-to-enroll-their-own-macos-devices-in-intune)

#### <a name="options-for-company-owned-macos-devices"></a>Options pour les appareils macOS appartenant à l’entreprise

Choisissez l’une des options du tableau suivant pour inscrire des appareils macOS gérés par l’entreprise dans Intune :

| Option  | Description  |
|---------|---------|
| Inscription d’appareils automatisée Apple |  Utilisez cette méthode pour automatiser l’expérience d’inscription sur les appareils achetés via Apple Business Manager ou Apple School Manager. L'inscription automatique des appareils déploie le profil d'inscription par voie hertzienne, de sorte que vous n'avez pas besoin d'avoir un accès physique aux appareils. <br/><br/>Consultez [Inscrire automatiquement macOS appareils auprès d’Apple Business Manager ou d’Apple School Manager](/mem/intune/enrollment/device-enrollment-program-enroll-macos). |
| Gestionnaire d’inscription d’appareil (DEM)  |  Utilisez cette méthode pour les déploiements à grande échelle et lorsqu’il existe plusieurs personnes dans votre organisation qui peuvent vous aider à configurer l’inscription. Une personne disposant des droits de gestionnaire d'inscription de l'appareil (DEM) peut inscrire jusqu'à 1 000 appareils avec un seul compte Azure Active Directory. Cette méthode utilise l'application Company Portal ou l'application Microsoft Intune pour inscrire les appareils. Vous ne pouvez pas utiliser un compte DEM pour inscrire des appareils via l'inscription automatique des appareils.<br/><br/> Consultez [Inscrire des appareils dans Intune à l’aide d’un compte gestionnaire d’inscription d’appareils](/mem/intune/enrollment/device-enrollment-manager-enroll).  |
| Inscription directe  | L’inscription directe inscrit des appareils sans affinité utilisateur. Cette méthode est donc préférable pour les appareils qui ne sont pas associés à un seul utilisateur. Cette méthode exige que vous ayez un accès physique aux Macs que vous inscrivez. <br/><br/>Consultez [Utiliser l’inscription directe pour les appareils macOS](/mem/intune/enrollment/device-enrollment-direct-enroll-macos).      |

#### <a name="ask-users-to-enroll-their-own-macos-devices-in-intune"></a>Demandez aux utilisateurs d’inscrire leurs propres appareils macOS dans Intune

Si votre entreprise préfère que des personnes inscrivent leurs propres appareils dans Intune, demandez aux utilisateurs de suivre les étapes suivantes :

1. Accédez au site web Portail d'entreprise ([https://portal.manage.microsoft.com/](https://portal.manage.microsoft.com/)) et connectez-vous.

2. Suivez les instructions du site web Portail d'entreprise pour ajouter leur appareil.

3. Installez l’application Portail d'entreprise à [https://aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac)l’adresse et suivez les instructions de l’application.

### <a name="confirm-that-a-macos-device-is-onboarded"></a>Vérifier qu’un appareil macOS est intégré

1. Pour vérifier que l’appareil est associé à votre entreprise, utilisez la commande Python suivante dans Bash : `mdatp health --field org_id`.

2. Si vous utilisez macOS 10.15 (Catalina) ou version ultérieure, accordez à Defender pour Entreprise le consentement pour protéger votre appareil. Accédez à **System PreferencesSecurity** >  **&** **PrivacyPrivacyFull** >  >  **Disk Access**. Sélectionnez l’icône de verrouillage pour apporter des modifications (en bas de la boîte de dialogue), puis sélectionnez **Microsoft Defender pour les PME** (ou **Defender pour point de terminaison**, si c’est ce que vous voyez).

3. Pour vérifier que l’appareil est intégré, utilisez la commande suivante dans Bash : `mdatp health --field real_time_protection_enabled`

4. Une fois qu’un appareil a été inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Microsoft Defender pour les PME](mdb-create-edit-device-groups.md).

## <a name="view-a-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

Pour afficher la liste des appareils intégrés à Defender entreprise, dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sous **Points de terminaison**, choisissez **Inventaire des appareils**.

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet qui correspond au système d’exploitation sur les appareils ([clients Windows, serveur Windows, macOS ou appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration d’appareils, passez à [l’étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les PME](mdb-configure-security-settings.md)
- Consultez [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md).

## <a name="mobile-devices"></a>[**appareils mobiles**](#tab/mobiles)

## <a name="mobile-devices"></a>Appareils mobiles

Vous aurez besoin de Microsoft Intune pour intégrer des appareils mobiles, tels que des appareils Android et iOS/iPadOS. Si vous avez [Microsoft 365 Business Premium](../../business/index.yml), vous avez Intune. 

Consultez les ressources suivantes pour obtenir de l’aide sur l’inscription de ces appareils dans Intune :

- [Inscrire des appareils Android](/mem/intune/enrollment/android-enroll)
- [Inscrire des appareils iOS ou iPadOS](/mem/intune/enrollment/ios-enroll)

Une fois qu’un appareil a été inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Microsoft Defender pour les PME](mdb-create-edit-device-groups.md).

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet qui correspond au système d’exploitation sur les appareils ([clients Windows, serveur Windows, macOS ou appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration d’appareils, passez à [l’étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les PME](mdb-configure-security-settings.md)
- Consultez [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md).
