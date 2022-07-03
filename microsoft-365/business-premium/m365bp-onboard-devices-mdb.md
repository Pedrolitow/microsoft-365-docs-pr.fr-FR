---
title: Intégrer les appareils de votre organisation à Microsoft Defender pour les PME
description: Intégrer les appareils de votre organisation à Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 70be4a5b7991d038dd1e34c00778de6bb3a67b84
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573966"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

Microsoft 365 Business Premium comprend Microsoft Defender pour les entreprises, une solution de sécurité des points de terminaison pour les petites et moyennes entreprises. Le Defender pour entreprise offre une protection de nouvelle génération (antivirus, antimalware et protection fournie par le cloud), une protection par pare-feu, un filtrage du contenu Web et bien plus encore pour les appareils de votre entreprise. La protection est appliquée lorsque vous embarquez des appareils. 

Pour intégrer des appareils, vous pouvez choisir parmi plusieurs options :

- [Embarquement automatique des appareils Windows inscrits dans Microsoft Intune.](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune)
- [Un script local pour intégrer les appareils Windows et macOS à Defender pour entreprise](#use-a-local-script-to-onboard-windows-and-macos-devices-to-defender-for-business)
- [Intune pour inscrire les appareils, y compris les appareils](#use-intune-to-enroll-devices) mobiles (Windows, macOS, iOS et Android), puis appliquer les politiques de Defender pour entreprise à ces appareils.

Cet article inclut également les rubriques suivantes :

- [Comment exécuter un test de détection sur un appareil Windows](#run-a-detection-test-on-a-windows-device)
- [Comment intégrer des appareils progressivement](#onboard-devices-gradually)
- [Comment déconnecter un appareil](#offboard-a-device) si un appareil est remplacé ou si une personne quitte l’organisation

> [!IMPORTANT]
> Si un problème se produit et que votre processus d’intégration échoue, consultez [Résolution des problèmes Microsoft Defender pour les PME](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune"></a>Utilisez l'intégration automatique pour les appareils Windows qui sont déjà inscrits dans Intune.

Vous pouvez intégrer automatiquement les appareils Windows à Defender pour entreprises si ces appareils sont déjà inscrits dans Intune. Defender pour entreprise détecte les appareils clients Windows qui sont inscrits dans Intune et vous invite à choisir si vous voulez embarquer ces appareils automatiquement. Les stratégies et paramètres de sécurité de Defender pour entreprise sont ensuite appliqués à ces appareils. Nous appelons ce processus *embarquement automatique*. Notez que l'option d'embarquement automatique ne s'applique qu'aux appareils Windows. L’intégration automatique est disponible si les conditions suivantes sont remplies :

- Votre entreprise utilisait déjà le gestionnaire de terminaux Microsoft Endpoint Manager, Microsoft Intune ou Mobile Device Management (MDM) dans Intune avant d'obtenir Defender pour entreprise (les clients Microsoft 365 Business Premium disposent déjà de Microsoft Intune).
- Vous avez déjà des appareils Windows inscrits dans Intune.

> [!TIP]
> Lorsque vous êtes invité à utiliser l'intégration automatique, nous vous recommandons de sélectionner l'option «tous les appareils inscrits». Ainsi, lorsque les appareils Windows seront inscrits dans Intune par la suite, ils seront automatiquement intégrés à Defender pour entreprise.

Pour en savoir plus sur l'intégration automatique, voir Utiliser[ l'assistant pour configurer Microsoft Defender pour entreprise](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices-to-defender-for-business"></a>Utiliser un script local pour intégrer les appareils Windows et macOS à Defender pour entreprise

Vous pouvez utiliser un script local pour intégrer des appareils Windows et Mac. Lorsque vous exécutez le script d'intégration sur un appareil, il crée une confiance avec Azure Active Directory (si cette confiance n'existe pas déjà), inscrit l'appareil dans Intune (s'il n'est pas déjà inscrit), puis intègre l'appareil à Defender pour entreprise. Vous pouvez embarquer jusqu'à 10 appareils à la fois en utilisant le script local.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11** ou **macOS**, puis, dans la section **Méthode de déploiement**, choisissez **Script local**. 

4. Sélectionnez **Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible. (Si vous avez sélectionné **macOS**, sélectionnez également **Télécharger le package d’installation** et l’enregistrer sur votre appareil amovible.)

5. Suivez les instructions suivantes :

   - AAppareils Windows [Intégrer les appareils Windows utilisant un script local](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)
   - Appareils macOS : [déploiement manuel pour Microsoft Defender pour point de terminaison sur macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-intune-to-enroll-devices"></a>Utilisez Intune pour inscrire les appareils

Pour inscrire un appareil, inscrivez-le vous-même ou demandez à vos utilisateurs de se connecter au portail d’entreprise et d’inscrire et d’installer les applications nécessaires. 

Si vous utilisiez déjà Intune ou la gestion des appareils mobiles avant de vous procurer Defender pour entreprise, vous pouvez continuer à utiliser Intune pour intégrer les appareils de votre organisation. Grâce à Intune, vous pouvez embarquer des ordinateurs, des tablettes et des téléphones, y compris des appareils iOS et Android.

Consultez [inscription de l’appareil dans Microsoft Intune](/mem/intune/enrollment/device-enrollment). 

## <a name="run-a-detection-test-on-a-windows-device"></a>Exécuter un test de détection sur un appareil nouvellement intégré

Une fois que vous avez intégré les appareils Windows à Defender pour les PME, vous pouvez exécuter un test de détection sur un appareil Windows pour vous assurer que tout fonctionne correctement.

1. Sur l’appareil Windows, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez une fenêtre d’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre d’invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécutée, la fenêtre d’invite de commandes se ferme automatiquement. En cas de réussite, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour l’appareil nouvellement intégré en dix minutes environ.

## <a name="onboard-devices-gradually"></a>Intégrer progressivement des appareils

Si vous préférez intégrer des appareils par phases, ce que nous appelons *l’intégration progressive des appareils*, procédez comme suit : 

1. Identifiez un ensemble d’appareils à intégrer.

2. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

3. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

4. Sélectionnez un système d’exploitation (par exemple **Windows 10 et 11)** puis choisissez une méthode d’intégration (par exemple, **Script local**). Suivez les instructions fournies pour la méthode que vous avez sélectionnée.

5. Répétez ce processus pour chaque ensemble d’appareils que vous souhaitez intégrer. 

> [!TIP]
> Vous n’avez pas besoin d’utiliser le même package d’intégration chaque fois que vous insérons des appareils. Par exemple, vous pouvez utiliser un script local pour intégrer certains appareils. Par la suite, vous pouvez choisir une autre méthode pour intégrer davantage d’appareils.

## <a name="offboard-a-device"></a>Annuler l’intégration d’un appareil

Si vous souhaitez déconnecter un appareil, utilisez l’une des procédures suivantes :

1. Dans le volet de navigation, choisissez **Paramètres**, puis choisissez **Points de terminaison**.

2. Sous **Gestion des appareils**, choisissez **Retrait**.

3. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, sous **Désinscrit un appareil**, dans la section **Méthode de déploiement**, choisissez **Script local**. 

4. Dans l’écran de confirmation, passez en revue les informations, puis choisissez **Télécharger** pour continuer.

5. Sélectionnez **Télécharger le package de retrait** Nous vous recommandons d’enregistrer le package de retrait sur un lecteur amovible.

6. Exécutez le script sur chaque appareil que vous souhaitez déclasser. Vous avez besoin d’aide pour cette tâche ? Consultez les ressources suivantes :   

   - Appareils Windows : [retirer les appareils Windows à l’aide d’un script local](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script) 
   - Appareils macOS : [désinstallation sur macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Le retrait d’un appareil entraîne l’arrêt de l’envoi de données à Defender pour les PME. Toutefois, les données reçues avant le retrait sont conservées jusqu’à six (6) mois.

## <a name="next-objective"></a>Objectif suivant

[Configurez la protection de vos appareils Windows](m365bp-protection-settings-for-windows-10-devices.md).
