---
title: Intégrer les appareils de votre organisation pour Microsoft Defender pour les PME
description: Intégrer les appareils de votre organisation pour Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: e9810b453136025e094ef8a0e88bff526f2c5a51
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634776"
---
# <a name="onboard-managed-devices-to-microsoft-defender-for-business"></a>Intégrer des appareils gérés à Microsoft Defender pour les PME

Intégrer des appareils à Microsoft Defender pour les PME pour les protéger avec une protection nouvelle génération (antivirus, logiciel anti-programme malveillant et protection cloud), une protection pare-feu, le filtrage de contenu web et bien plus encore. 

Pour intégrer des appareils, vous pouvez choisir parmi plusieurs options :

- [Utiliser l’intégration automatique pour Windows appareils déjà inscrits dans Microsoft Endpoint Manager](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)

- [Utiliser un script local pour intégrer des appareils Windows macOS](#use-a-local-script-to-onboard-windows-and-macos-devices)

- [Utilisez Endpoint Manager pour](#use-microsoft-endpoint-manager-to-enroll-devices) inscrire des appareils (Windows, macOS, iOS et Android), puis appliquer des stratégies Defender entreprise à ces appareils

Cet article inclut également les articles suivants :

- [Comment exécuter un test de détection sur un Windows périphérique](#run-a-detection-test-on-a-windows-device)

- [Comment intégrer progressivement des appareils](#onboard-devices-gradually)

- [Comment faire pour quitter un appareil si](#offboard-a-device) un appareil est remplacé ou si quelqu’un quitte l’organisation

> [!IMPORTANT]
> Si un problème se passe et que votre processus d’intégration échoue, consultez [Microsoft Defender pour les PME résolution des problèmes](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>Utiliser l’intégration automatique pour Windows appareils déjà inscrits dans Microsoft Endpoint Manager

L’option d’intégration automatique s’applique Windows appareils uniquement. L’intégration automatique est disponible si votre organisation utilisait déjà Microsoft Endpoint Manager, Microsoft Intune ou mobile Gestion des appareils (MDM) dans Microsoft Intune avant d’obtenir Defender pour les entreprises et que vous en avez déjà Windows  les appareils inscrits dans Endpoint Manager. 

Si Windows appareils sont déjà inscrits dans Endpoint Manager, Defender entreprise détecte ces appareils pendant que vous êtes en train de configurer Defender pour les entreprises. Vous serez invité à vous demander si vous souhaitez utiliser l’intégration automatique pour l’ensemble ou une partie de Windows appareils. Vous pouvez intégrer tous les Windows en même temps, ou sélectionner des appareils spécifiques pour commencer, puis ajouter d’autres appareils ultérieurement.

Pour en savoir plus sur l’intégration automatique, consultez l’étape 2 de l’Assistant pour [configurer Microsoft Defender pour les PME](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>Utiliser un script local pour intégrer des appareils Windows macOS

Vous pouvez utiliser un script local pour intégrer des Windows et des appareils macOS. Lorsque vous exécutez le script d’intégration sur un appareil, il crée une relation d’confiance avec Azure Active Directory (si cette confiance n’existe pas encore), inscrit l’appareil dans Microsoft Endpoint Manager (s’il n’est pas déjà inscrit), puis l’insérait à Defender pour Entreprise. 

Vous pouvez intégrer jusqu’à 10 appareils à la fois avec cette méthode.

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis sous Gestion **des appareils,** choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, tel **que Windows 10 et 11**, puis, sous Intégrer un **appareil, dans** **la section Méthode** de déploiement, choisissez **Script local**. 

4. **Sélectionnez Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible.

5. Suivez les instructions des articles suivants :

   - Windows : intégrer [des appareils Windows à l’aide d’un script local](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)

   - Appareils macOS : [déploiement manuel pour Microsoft Defender pour point de terminaison sur macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>Utiliser Microsoft Endpoint Manager pour inscrire des appareils

Si vous utilisiez déjà Endpoint Manager (qui inclut Microsoft Intune et Mobile Gestion des appareils), avant d’obtenir Defender pour Entreprise, vous pouvez continuer à utiliser Endpoint Manager pour intégrer les appareils de votre organisation. Avec Endpoint Manager, vous pouvez intégrer des ordinateurs, des tablettes et des téléphones, y compris des appareils iOS et Android.

Si votre organisation utilise des appareils Android, utilisez cette méthode.

Voir [Inscription des appareils dans Microsoft Intune](/mem/intune/enrollment/device-enrollment).


## <a name="run-a-detection-test-on-a-windows-device"></a>Exécuter un test de détection sur un Windows périphérique

Une fois que vous avez intégré des appareils Windows à Defender for Business, vous pouvez exécuter un test de détection sur un appareil Windows pour vous assurer que tout fonctionne correctement.

1. Sur le Windows, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez l’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre Invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécuté, la fenêtre d’invite de commandes se ferme automatiquement. Si elle réussit, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour le périphérique nouvellement intégré dans environ 10 minutes.

## <a name="onboard-devices-gradually"></a>Intégrer progressivement des appareils

Si vous préférez intégrer des appareils par phases, que nous appelons l’intégration *progressive d’appareils*, suivez les étapes suivantes : 

1. Identifiez un ensemble d’appareils à intégrer.

2. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in.

3. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis sous Gestion **des appareils,** choisissez **Intégration**.

4. Sélectionnez un système d’exploitation (**Windows 10 et 11),** puis choisissez une méthode d’intégration (par exemple, **un script local**). Suivez les instructions fournies pour la méthode que vous avez sélectionnée.

5. Répétez ce processus pour chaque ensemble d’appareils que vous souhaitez intégrer. 

> [!TIP]
> Vous n’avez pas besoin d’utiliser le même package d’intégration chaque fois que vous intégrerez des appareils. Par exemple, vous pouvez utiliser un script local pour intégrer certains appareils, puis choisir une autre méthode pour intégrer davantage d’appareils.

## <a name="offboard-a-device"></a>Hors-carte d’un appareil

Si vous souhaitez hors d’un appareil, suivez les étapes suivantes :

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Dans le volet de navigation, choisissez **Paramètres**, puis les **points de terminaison**.

3. Sous **Gestion des appareils**, sélectionnez **Offboarding (Boarding).**

4. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, sous Horsboard d’un **appareil, dans** **la section Méthode** de déploiement, choisissez **Script local**. 

5. Dans l’écran de confirmation, examinez les informations, puis choisissez **Télécharger** pour continuer.

6. **Sélectionnez Télécharger le package deboarding**. Nous vous recommandons d’enregistrer le package de déboardage sur un lecteur amovible.

7. Exécutez le script sur chaque appareil que vous souhaitez hors d’board. Vous avez besoin d’aide pour cette tâche ? Consultez les ressources suivantes :   

   - Windows : hors [Windows à l’aide d’un script local](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   
   - Appareils macOS : [désinstallation sur macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Laboarding d’un appareil entraîne l’arrêt de l’envoi de données à Defender for Business. Toutefois, les données reçues avant laboarding sont conservées pendant six (6) mois au plus.

## <a name="next-steps"></a>Prochaines étapes

[Examiner les actions de correction dans Microsoft 365 Business Premium](m365bp-review-remediation-actions-devices.md)