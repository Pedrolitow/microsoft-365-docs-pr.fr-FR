---
title: Intégrer des appareils à Microsoft Defender pour les PME
description: En savoir plus sur les options d’intégration des appareils dans Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ba816430521db2848273a4f7c6ca7d1a61703690
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862273"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Intégrer des appareils à Microsoft Defender pour les PME

> [!NOTE]
> Microsoft Defender pour les PME est désormais inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md). 

Avec Microsoft Defender pour les PME, vous avez le choix entre plusieurs options pour intégrer les appareils de votre entreprise. Cet article vous guide tout au long de vos options et inclut une vue d’ensemble du fonctionnement de l’intégration.

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="what-to-do"></a>Procédure

1. Sélectionnez l’onglet de votre système d’exploitation : 

   - clients Windows
   - serveur Windows (préversion)
   - ordinateurs macOS
   - appareils mobiles

2. Affichez vos options d’intégration et suivez les instructions de l’onglet sélectionné.

3. Passez à vos étapes suivantes.

## <a name="windows-clients"></a>[**clients Windows**](#tab/WindowsClientDevices)

## <a name="windows-clients"></a>clients Windows

Choisissez l’une des options suivantes pour intégrer Windows appareils clients à Defender entreprise :

- [Script local](#local-script-for-windows-clients) (pour l’intégration manuelle d’appareils dans le portail Microsoft 365 Defender)
- [Microsoft Endpoint Manager](#endpoint-manager-for-windows-clients) (inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md))


### <a name="local-script-for-windows-clients"></a>Script local pour les clients Windows

Vous pouvez utiliser un script local pour intégrer Windows appareils clients. Lorsque vous exécutez le script d’intégration sur un appareil, il crée une approbation avec Azure Active Directory (si cette approbation n’existe pas déjà), inscrit l’appareil dans Microsoft Endpoint Manager (s’il n’est pas déjà inscrit), puis l’intègre à Defender pour Entreprises. La méthode de script local fonctionne même si vous n’avez pas de Endpoint Manager (ou Microsoft Intune). Nous vous recommandons d’intégrer jusqu’à 10 appareils à la fois à l’aide de cette méthode.

> [!TIP]
> Nous vous recommandons d’intégrer jusqu’à 10 appareils à la fois lorsque vous utilisez la méthode de script local.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, dans la section **Méthode de déploiement**, choisissez **Script local**. 

4. Sélectionnez **Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible.

5. Sur un appareil Windows, extrayez le contenu du package de configuration à un emplacement, tel que le dossier Bureau. Vous devez avoir un fichier nommé `WindowsDefenderATPLocalOnboardingScript.cmd`. 

6. Ouvrez l’invite de commandes en tant qu’administrateur.

7. Tapez l’emplacement du fichier de script. Par exemple, si vous avez copié le fichier dans le dossier Bureau, vous tapez `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`, puis appuyez sur la touche Entrée (ou sélectionnez **OK**).

8. Une fois le script exécuté, passez à [exécuter un test de détection](#running-a-detection-test-on-a-windows-client).

### <a name="endpoint-manager-for-windows-clients"></a>Endpoint Manager pour les clients Windows

Si votre abonnement inclut [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), vous pouvez intégrer des clients Windows et d’autres appareils dans le centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Par exemple, si vous avez [Microsoft 365 Business Premium](../../business/index.yml), vous avez Endpoint Manager dans le cadre de votre abonnement. Endpoint Manager inclut [des](/mem/intune/fundamentals/what-is-intune) [fonctionnalités de Microsoft Intune et de Gestion des appareils mobile](/mem/intune/fundamentals/what-is-device-management). 

Plusieurs méthodes sont disponibles pour inscrire des appareils dans Intune. Nous vous recommandons de commencer par l’une des méthodes suivantes :

- [Activer Windows l’inscription automatique](/mem/intune/enrollment/windows-enroll) pour les appareils appartenant à l’entreprise ou gérés par l’entreprise
- [Demandez aux utilisateurs d’inscrire leurs propres appareils Windows 10/11 dans Intune](/mem/intune/user-help/enroll-windows-10-device)

#### <a name="to-enable-automatic-enrollment-for-windows-devices"></a>Pour activer l’inscription automatique pour les appareils Windows

Lorsque vous configurez l’inscription automatique, les utilisateurs ajoutent leur compte professionnel à l’appareil. En arrière-plan, l’appareil inscrit et joint Azure Active Directory (Azure AD) et est inscrit dans Intune.

1. Accédez à la Portail Azure ([https://portal.azure.com/](https://portal.azure.com/)) et connectez-vous. 

2. Sélectionnez **Azure Active Directory** >  **Mobilité (GPM et GAM)** > **Microsoft Intune**.

3. Configurez l’étendue utilisateur MDM et l’étendue de l’utilisateur GAM.

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

Une fois que vous avez intégré Windows appareils à Defender entreprise, vous pouvez exécuter un test de détection sur un appareil Windows pour vous assurer que tout fonctionne correctement.

1. Sur l’appareil Windows, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez l’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre d’invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécutée, la fenêtre d’invite de commandes se ferme automatiquement. En cas de réussite, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour l’appareil nouvellement intégré dans environ 10 minutes.

## <a name="view-a-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

Pour afficher la liste des appareils intégrés à Defender entreprise, dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sous **Points de terminaison**, choisissez **Invetory appareil**.

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet qui correspond au système d’exploitation sur les appareils [(Windows clients, Windows Server, macOS ou appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration d’appareils, passez à [l’étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les PME](mdb-configure-security-settings.md)
- Consultez [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md).

## <a name="windows-server"></a>[**Windows Server**](#tab/WindowsServerEndpoints)

## <a name="windows-server-preview"></a>serveur Windows (préversion)

Vous pouvez intégrer un appareil Windows Server à l’aide d’un script local. 

> [!IMPORTANT]
> La possibilité d’intégrer des points de terminaison Windows Server est actuellement en préversion.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, tel que **Windows Server 1803, 2019 et 2022**, puis, dans la section **Méthode de déploiement**, choisissez **Script local**. 

   Si vous sélectionnez **Windows Server 2012 R2 et 2016**, vous aurez deux packages à télécharger et à exécuter : un package d’installation et un package d’intégration. Le package d’installation contient un fichier MSI qui installe l’agent Microsoft Defender pour les PME. Le package d’intégration contient le script permettant d’intégrer votre point de terminaison Windows Server à Defender for Business. 

4. Sélectionnez **Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible.

   Si vous avez sélectionné **Windows Server 2012 R2 et 2016**, **sélectionnez également Télécharger le package d’installation** et enregistrez-le sur un lecteur amovible.

5. Sur votre point de terminaison Windows Server, extrayez le contenu des packages d’installation/intégration à un emplacement, tel que le dossier Bureau. Vous devez avoir un fichier nommé `WindowsDefenderATPLocalOnboardingScript.cmd`. 

   Si vous effectuez l’intégration Windows Server 2012 R2 ou Windows Server 2016, extrayez d’abord le package d’installation.

6. Ouvrez l’invite de commandes en tant qu’administrateur.

7. Si vous effectuez l’intégration Windows Server 2012R2 ou Windows Server 2016, exécutez la commande suivante : `Msiexec /i md4ws.msi /quiet`. 

   Si vous effectuez l’intégration Windows Server 1803, 2019 ou 2022, ignorez cette étape et passez à l’étape 8.

8. Tapez l’emplacement du fichier de script. Par exemple, si vous avez copié le fichier dans le dossier Bureau, vous tapez `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`, puis appuyez sur la touche Entrée (ou sélectionnez **OK**).

9. Procéder à [l’exécution d’un test de détection sur Windows Server](#running-a-detection-test-on-windows-server)

### <a name="running-a-detection-test-on-windows-server"></a>Exécution d’un test de détection sur Windows Server

Une fois que vous avez intégré votre point de terminaison Windows Server à Defender entreprise, vous pouvez exécuter un test de détection pour vous assurer que tout fonctionne correctement.

1. Sur l’appareil Windows Server, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez l’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre d’invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécutée, la fenêtre d’invite de commandes se ferme automatiquement. En cas de réussite, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour l’appareil nouvellement intégré dans environ 10 minutes.

## <a name="view-a-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

Pour afficher la liste des appareils intégrés à Defender entreprise, dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sous **Points de terminaison**, choisissez **Invetory appareil**.

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet qui correspond au système d’exploitation sur les appareils [(Windows clients, Windows Server, macOS ou appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration d’appareils, passez à [l’étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les PME](mdb-configure-security-settings.md)
- Consultez [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md).

## <a name="macos"></a>[**macOS**](#tab/macOSdevices)

## <a name="macos-computers"></a>ordinateurs macOS

> [!NOTE]
> - Nous vous recommandons d’utiliser un [script local pour intégrer des appareils macOS](#local-script-for-macos). Bien que vous puissiez [configurer l’inscription pour les appareils macOS dans Intune](/mem/intune/enrollment/macos-enroll), le script local est la méthode la plus simple pour intégrer des appareils macOS à Defender for Business. 

Choisissez l’une des options suivantes pour intégrer des appareils macOS :

- [Script local pour macOS](#local-script-for-macos) (*recommandé*)
- [Endpoint Manager pour macOS](#endpoint-manager-for-macos)

### <a name="local-script-for-macos"></a>Script local pour macOS

Lorsque vous exécutez le script local sur un appareil macOS, il crée une approbation avec Azure Active Directory (si cette approbation n’existe pas déjà), inscrit l’appareil dans Microsoft Endpoint Manager (s’il n’est pas déjà inscrit), puis l’intègre à Defender entreprise. La méthode de script local fonctionne même si vous n’avez pas de Endpoint Manager (ou Microsoft Intune). Nous vous recommandons d’intégrer jusqu’à 10 appareils à la fois à l’aide de cette méthode.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez **macOS**, puis, dans la section **Méthode de déploiement** , choisissez **Script local**. 

4. Sélectionnez **Télécharger le package d’intégration** et enregistrez-le sur un lecteur amovible. Sélectionnez également **Télécharger le package d’installation** et enregistrez-le sur votre appareil amovible.

5. Sur un appareil macOS, enregistrez le package d’installation dans `wdav.pkg` un répertoire local.

6. Enregistrez le package d’intégration dans `WindowsDefenderATPOnboardingPackage.zip` le répertoire que vous avez utilisé pour le package d’installation.

7. Utilisez Finder pour accéder à `wdav.pkg` votre enregistrement, puis ouvrez-le.

8. Sélectionnez **Continuer**, acceptez les termes du contrat de licence, puis entrez votre mot de passe lorsque vous y êtes invité.

9. Vous serez invité à autoriser l’installation d’un pilote de Microsoft (« Extension système bloquée » ou « L’installation est en attente », ou les deux. Le pilote doit être autorisé à être installé. Pour autoriser l’installation, sélectionnez **Ouvrir les préférences de sécurité** ou **Ouvrir les préférences** >  système **& confidentialité**, puis **sélectionnez Autoriser**.

10. Utilisez la commande Python suivante dans Bash pour exécuter le package d’intégration : `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`

11. Une fois qu’un appareil a été inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Microsoft Defender pour les PME](mdb-create-edit-device-groups.md).

### <a name="endpoint-manager-for-macos"></a>Endpoint Manager pour macOS

Si votre abonnement inclut [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), vous pouvez intégrer des appareils macOS dans le centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Par exemple, si vous avez [Microsoft 365 Business Premium](../../business/index.yml), vous avez Endpoint Manager dans le cadre de votre abonnement. Endpoint Manager inclut [des](/mem/intune/fundamentals/what-is-intune) [fonctionnalités de Microsoft Intune et de Gestion des appareils mobile](/mem/intune/fundamentals/what-is-device-management). 

Plusieurs méthodes sont disponibles pour inscrire des appareils dans Intune. Nous vous recommandons de commencer par l’une des méthodes suivantes :

- [Choisir une option pour les appareils macOS appartenant à l’entreprise](#options-for-company-owned-macos-devices)
- [Demandez aux utilisateurs d’inscrire leurs propres appareils macOS dans Intune](#ask-users-to-enroll-their-own-macos-devices-in-intune)

#### <a name="options-for-company-owned-macos-devices"></a>Options pour les appareils macOS appartenant à l’entreprise

Choisissez l’une des options du tableau suivant pour inscrire des appareils macOS gérés par l’entreprise dans Intune :

| Option  | Description  |
|---------|---------|
| Inscription d’appareils automatisée Apple |  Utilisez cette méthode pour automatiser l’expérience d’inscription sur les appareils achetés via Apple Business Manager ou Apple School Manager. L'inscription automatique des appareils déploie le profil d'inscription par voie hertzienne, de sorte que vous n'avez pas besoin d'avoir un accès physique aux appareils. <br/><br/>Voir [Inscrire automatiquement des appareils macOS auprès d’Apple Business Manager ou d’Apple School Manager](/mem/intune/enrollment/device-enrollment-program-enroll-macos). |
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

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet qui correspond au système d’exploitation sur les appareils ([Windows clients, Windows Server, macOS ou appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration d’appareils, passez à [l’étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les PME](mdb-configure-security-settings.md)
- Consultez [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md).

## <a name="mobile-devices"></a>[**appareils mobiles**](#tab/mobiles)

## <a name="mobile-devices"></a>Appareils mobiles

Vous aurez besoin de Microsoft Intune pour intégrer des appareils mobiles, tels que des appareils Android et iOS/iPadOS. Si vous avez [Microsoft 365 Business Premium](../../business/index.yml), vous avez Endpoint Manager dans le cadre de votre abonnement. Endpoint Manager inclut [des](/mem/intune/fundamentals/what-is-intune) [fonctionnalités de Microsoft Intune et de Gestion des appareils mobile](/mem/intune/fundamentals/what-is-device-management). 

Consultez les ressources suivantes pour obtenir de l’aide sur l’inscription de ces appareils dans Intune :

- [Inscrire des appareils Android](/mem/intune/enrollment/android-enroll)
- [Inscrire des appareils iOS ou iPadOS](/mem/intune/enrollment/ios-enroll)

Une fois qu’un appareil a été inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Microsoft Defender pour les PME](mdb-create-edit-device-groups.md).

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet qui correspond au système d’exploitation sur les appareils ([Windows clients, Windows Server, macOS ou appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration d’appareils, passez à [l’étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les PME](mdb-configure-security-settings.md)
- Consultez [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md).
