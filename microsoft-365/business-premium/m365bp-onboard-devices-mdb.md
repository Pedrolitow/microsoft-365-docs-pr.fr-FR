---
title: Intégrer les appareils de votre organisation à Microsoft Defender pour les PME
description: Intégrer les appareils de votre organisation à Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 774c23a4da7d368f46607fd588a07ffb01e92f53
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094194"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

Maintenant que vous avez inscrit les appareils, vous devez les intégrer à Microsoft Defender pour les PME pour implémenter la protection de nouvelle génération (antivirus, logiciel anti-programme malveillant et protection fournie par le cloud), la protection pare-feu, le filtrage de contenu web, etc. 

Pour intégrer des appareils, vous pouvez choisir parmi plusieurs options :

- [Utiliser l’intégration automatique pour les appareils Windows déjà inscrits dans Microsoft Endpoint Manager](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)

- [Utiliser un script local pour intégrer des appareils Windows et macOS](#use-a-local-script-to-onboard-windows-and-macos-devices)

- [Utiliser Endpoint Manager pour inscrire des appareils](#use-microsoft-endpoint-manager-to-enroll-devices) (Windows, macOS, iOS et Android), puis appliquer des stratégies Defender entreprise à ces appareils

Cet article inclut également les rubriques suivantes :

- [Comment exécuter un test de détection sur un appareil Windows](#run-a-detection-test-on-a-windows-device)

- [Comment intégrer des appareils progressivement](#onboard-devices-gradually)

- [Comment déconnecter un appareil](#offboard-a-device) si un appareil est remplacé ou si une personne quitte l’organisation

> [!IMPORTANT]
> Si un problème se produit et que votre processus d’intégration échoue, consultez [Résolution des problèmes Microsoft Defender pour les PME](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>Utiliser l’intégration automatique pour les appareils Windows déjà inscrits dans Microsoft Endpoint Manager

L’option d’intégration automatique s’applique uniquement aux appareils Windows. L’intégration automatique est disponible si les conditions suivantes sont remplies :

- Votre organisation utilisait déjà Microsoft Endpoint Manager, Microsoft Intune ou Gestion des appareils mobiles (GAM) dans Microsoft Intune avant de recevoir Defender for Business ( Microsoft 365 Business Premium clients ont déjà Microsoft Intune).

- Vous disposez déjà d’appareils Windows inscrits dans Endpoint Manager.

Si Windows appareils sont déjà inscrits dans Endpoint Manager, Defender pour les PME détecte ces appareils pendant que vous êtes en train de configurer Defender pour les PME. Vous serez invité à indiquer si vous souhaitez utiliser l’intégration automatique pour tout ou partie de vos appareils Windows. Vous pouvez intégrer tous les appareils Windows à la fois, ou sélectionner des appareils spécifiques pour commencer, puis ajouter d’autres appareils ultérieurement.

> [!TIP]
> Nous vous recommandons de sélectionner l’option « Tous les appareils inscrits ». Ainsi, lorsque Windows appareils sont inscrits dans Endpoint Manager ultérieurement, ils sont automatiquement intégrés à Defender pour les PME.
Pour en savoir plus sur l’intégration automatique, consultez l’étape 2 de [l’Assistant Pour configurer Microsoft Defender pour les PME](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>Utiliser un script local pour intégrer des appareils Windows et macOS

Vous pouvez utiliser un script local pour intégrer des appareils Windows et Mac. Lorsque vous exécutez le script d’intégration sur un appareil, il crée une approbation avec Azure Active Directory (si cette approbation n’existe pas déjà), inscrit l’appareil dans Microsoft Endpoint Manager (s’il n’est pas déjà inscrit), puis l’intègre à Defender pour les PME. Cette méthode est utile pour l’intégration d’appareils dans Defender pour les PME. Vous pouvez intégrer jusqu’à 10 appareils à la fois.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11** ou **macOS**, puis, dans la section **Méthode de déploiement**, choisissez **Script local**. 

4. Sélectionnez **Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible. (Si vous avez sélectionné **macOS**, sélectionnez également **Télécharger le package d’installation** et l’enregistrer sur votre appareil amovible.)

5. Suivez les instructions suivantes :

   - AAppareils Windows [Intégrer les appareils Windows utilisant un script local](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)

   - Appareils macOS : [déploiement manuel pour Microsoft Defender pour point de terminaison sur macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>Utiliser Microsoft Endpoint Manager pour inscrire des appareils

Pour inscrire un appareil, inscrivez-le vous-même ou demandez à vos utilisateurs de se connecter au portail d’entreprise et d’inscrire et d’installer les applications nécessaires. 

Si vous utilisiez déjà Endpoint Manager (qui inclut Microsoft Intune et Gestion des appareils mobiles), avant d’obtenir Defender pour les PME, vous pouvez continuer à utiliser Endpoint Manager pour intégrer les appareils de votre organisation. Avec Endpoint Manager, vous pouvez intégrer des ordinateurs, des tablettes et des téléphones, y compris des appareils iOS et Android.

Consultez [inscription de l’appareil dans Microsoft Intune](/mem/intune/enrollment/device-enrollment). 

## <a name="run-a-detection-test-on-a-windows-device"></a>Exécuter un test de détection sur un appareil nouvellement intégré

Une fois que vous avez intégré les appareils Windows à Defender pour les PME, vous pouvez exécuter un test de détection sur un appareil Windows pour vous assurer que tout fonctionne correctement.

1. Sur l’appareil Windows, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez une fenêtre d’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre d’invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécutée, la fenêtre d’invite de commandes se ferme automatiquement. En cas de réussite, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour l’appareil nouvellement intégré dans environ dix minutes.

## <a name="onboard-devices-gradually"></a>Intégrer progressivement des appareils

Si vous préférez intégrer des appareils par phases, ce que nous appelons *l’intégration progressive des appareils*, procédez comme suit : 

1. Identifiez un ensemble d’appareils à intégrer.

2. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

3. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

4. Sélectionnez un système d’exploitation (par exemple **, Windows 10 et 11)**, puis choisissez une méthode d’intégration (par exemple, un **Script local**). Suivez les instructions fournies pour la méthode que vous avez sélectionnée.

5. Répétez ce processus pour chaque ensemble d’appareils que vous souhaitez intégrer. 

> [!TIP]
> Vous n’avez pas besoin d’utiliser le même package d’intégration chaque fois que vous insérons des appareils. Par exemple, vous pouvez utiliser un script local pour intégrer certains appareils. Par la suite, vous pouvez choisir une autre méthode pour intégrer davantage d’appareils.

## <a name="offboard-a-device"></a>Annuler l’intégration d’un appareil

Si vous souhaitez déconnecter un appareil, utilisez l’une des procédures suivantes :

1. Dans le volet de navigation, choisissez **Paramètres**, puis choisissez **Points de terminaison**.

1. Sous **Gestion des appareils**, choisissez **Retrait**.

1. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, sous **Désinscrit un appareil**, dans la section **Méthode de déploiement**, choisissez **Script local**. 

1. Dans l’écran de confirmation, passez en revue les informations, puis choisissez **Télécharger** pour continuer.

1. Sélectionnez **Télécharger le package de retrait**. Nous vous recommandons d’enregistrer le package de retrait sur un lecteur amovible.

1. Exécutez le script sur chaque appareil que vous souhaitez déclasser. Vous avez besoin d’aide pour cette tâche ? Consultez les ressources suivantes :   

   - Appareils Windows : [retirer les appareils Windows à l’aide d’un script local](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   
   - Appareils macOS : [désinstallation sur macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Le retrait d’un appareil entraîne l’arrêt de l’envoi de données à Defender pour les PME. Toutefois, les données reçues avant le retrait sont conservées jusqu’à six (6) mois.

## <a name="next-objective"></a>Objectif suivant

Prenez le temps d’[examiner et modifier les stratégies](m365bp-view-edit-create-mdb-policies.md).

