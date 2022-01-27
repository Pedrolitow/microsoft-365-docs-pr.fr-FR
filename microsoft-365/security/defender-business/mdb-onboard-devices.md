---
title: Intégrer des appareils à Microsoft Defender pour Entreprises (prévisualisation)
description: En savoir plus sur les options d’intégration d’appareil dans Microsoft Defender entreprise (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/23/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365initiative-defender-business
ms.openlocfilehash: a9aa664c7b7e6c2093817772f8f0bfaefdff3d9e
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "62244570"
---
# <a name="onboard-devices-to-microsoft-defender-for-business-preview"></a>Intégrer des appareils à Microsoft Defender pour Entreprises (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et [](https://aka.ms/mdb-preview) sera progressivement mis en place pour les clients et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un ensemble initial de [scénarios](mdb-tutorials.md#try-these-preview-scenarios)et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Avec Microsoft Defender entreprise (prévisualisation), vous avez le choix entre plusieurs options pour intégrer les appareils de votre entreprise. Cet article vous présente vos options et inclut une vue d’ensemble du fonctionnement de l’intégration.

## <a name="what-to-do"></a>Procédure

1. [Découvrez les méthodes d’intégration](#types-of-onboarding-methods)et déterminez si vous utilisez l’intégration automatique ou manuelle.

2. Effectuez l'une des opérations suivantes :

   - Si vous utilisez l’intégration automatique, allez à l’étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les entreprises [(prévisualisation).](mdb-configure-security-settings.md)
   - Si vous procédez manuellement à l’intégration des appareils, procédez à l’intégration d’un appareil à l’aide d’un [script local dans Microsoft 365 Defender](#onboard-a-device-using-a-local-script-in-defender-for-business).
   - Si vous utilisez déjà Microsoft Intune, procédez à l’intégration des appareils [à l’aide Microsoft Intune](#onboard-devices-using-microsoft-intune).

3. [Exécutez un test de détection pour](#run-a-detection-test) les appareils nouvellement intégrés.

4. [Voir les étapes suivantes.](#next-steps) 

Cet article inclut également des informations [sur la façon d’utiliser un appareil.](#what-if-i-want-to-offboard-a-device)

## <a name="types-of-onboarding-methods"></a>Types de méthodes d’intégration

Le tableau suivant décrit les types de méthodes d’intégration qui sont pris en charge dans Defender pour Entreprise pendant la prévisualisation. 
<br/><br/>

| Méthode d’intégration  | Description  |
|---------|---------|
| **Intégration automatique**<br/>(*disponible pour les clients qui utilisent déjà Microsoft Endpoint Manager*) | Si vous utilisiez déjà Microsoft Endpoint Manager avant d’obtenir Defender entreprise (prévisualisation), Defender for Business le détectera. Vous serez invité à savoir si vous souhaitez utiliser le processus d’intégration automatique pour les appareils précédemment intégrés à Microsoft Endpoint Manager. <br/><br/>L’intégration automatique permet de mettre en place une connexion entre Defender entreprise (prévisualisation) et Microsoft Endpoint Manager, puis d’intégrer des appareils à Defender for Business (prévisualisation). Cette option vous permet d’intégrer des appareils à Defender for Business (prévisualisation) rapidement et efficacement. Tous Windows appareils actuellement inscrits dans Microsoft Endpoint Manager seront intégrés à Defender pour Entreprise. <br/><br/>Si vous choisissez l’intégration automatique, ignorez les procédures de cet article et passez à l’étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les entreprises [(prévisualisation).](mdb-configure-security-settings.md)  |
| **Script local**<br/>(*recommandé lors de la prévisualisation ; utile pour l’intégration de quelques appareils à la fois)*  | Pendant la prévisualisation, vous pouvez intégrer des appareils dans Defender for Business (prévisualisation) à l’aide d’un script que vous téléchargez et exécutez sur des appareils macOS, Windows 10 ou 11 et Linux. L’exécution du script sur un appareil crée une relation d’Azure Active Directory (Azure AD) et inscrit l’appareil avec Microsoft Intune. Le processus est très similaire à celui de [l’intégration d’appareils à Microsoft Defender for Endpoint](../defender-endpoint/onboarding.md).<br/><br/>Pour utiliser cette méthode, procédez à [l’intégration d’un appareil à l’aide](#onboard-a-device-using-a-local-script-in-defender-for-business)d’un script local Microsoft 365 Defender . |
| **Microsoft Intune** <br/>(*disponible pour les clients qui utilisent déjà Microsoft Intune*) | Si vous utilisiez déjà [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) avant d’obtenir Defender entreprise (prévisualisation), vous pouvez utiliser Microsoft Intune pour intégrer des appareils. Pendant la prévisualisation, vous pouvez utiliser Microsoft Intune pour intégrer des appareils Windows, iOS, macOS, Linux et Android à Defender for Business (prévisualisation). <br/><br/>Pour utiliser cette méthode, voir [Inscription des appareils dans Intune.](/mem/intune/enrollment/device-enrollment) |

> [!TIP]
> Si un problème se produit lors de l’intégration d’appareils, consultez La résolution des problèmes de Microsoft Defender entreprise [(prévisualisation).](mdb-troubleshooting.yml) 

## <a name="onboard-a-device-using-a-local-script-in-defender-for-business"></a>Intégrer un appareil à l’aide d’un script local dans Defender for Business

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ), and sign in.

2. Dans le volet de navigation, choisissez **Paramètres** points de terminaison, puis sous Gestion des appareils  >  , choisissez **Intégration.** 

3. Sélectionnez un système d’exploitation, **tel que Windows 10 et 11,** puis, sous Intégrer un appareil, dans la section Méthode de déploiement, choisissez Script   **local.** 

4. Sélectionnez **Télécharger le package d’intégration.** Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible.

5. Suivez les instructions des articles suivants :

   - Windows : intégrer [des appareils Windows à l’aide d’un script local](../defender-endpoint/configure-endpoints-script.md#onboard-devices)
   - Appareils macOS : [déploiement manuel de Microsoft Defender pour endpoint sur macOS](../defender-endpoint/mac-install-manually.md#client-configuration)
   - Appareils Linux : [déployer Microsoft Defender pour point de terminaison sur Linux manuellement](../defender-endpoint/linux-install-manually.md#client-configuration)

6. Exécutez un [test de détection pour](#run-a-detection-test) Windows appareils.

> [!IMPORTANT]
> Si un problème se produit et que votre processus d’intégration échoue, consultez La résolution des problèmes de Microsoft Defender entreprise [(prévisualisation).](mdb-troubleshooting.yml)

## <a name="onboard-devices-using-microsoft-intune"></a>Intégrer des appareils à l’aide Microsoft Intune

Si vous utilisiez déjà Microsoft Intune avant d’obtenir Defender entreprise (prévisualisation), vous pouvez utiliser Microsoft Intune pour intégrer des appareils. Pour obtenir de l’aide à ce sujet, voir [Inscription de l’appareil dans Microsoft Intune](/mem/intune/enrollment/device-enrollment).

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Une fois que vous avez intégré un Windows manuellement, vous pouvez exécuter un test de détection pour vous assurer que tout fonctionne correctement avec Defender for Business (prévisualisation).

1. Sur le Windows, créez un dossier : `C:\test-MDATP-test` .

2. Ouvrez l’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre Invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécuté, la fenêtre d’invite de commandes se ferme automatiquement. Si elle réussit, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender pour le périphérique nouvellement intégré dans environ 10 minutes.

## <a name="what-if-i-want-to-offboard-a-device"></a>Que se passe-t-il si je souhaite hors d’un appareil ?

Si vous souhaitez hors d’un appareil, suivez les étapes suivantes :

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.

2. Dans le volet de navigation, choisissez **Paramètres,** puis choisissez **Points de terminaison.**

3. Sous **Gestion des appareils,** choisissez **Offboarding**.

4. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11,** puis, sous Horsboard d’un **appareil,** dans la **section** Méthode de déploiement, choisissez Script **local.** 

5. Dans l’écran de confirmation, examinez les informations, puis choisissez **Télécharger** pour continuer.

6. Select **Download offboarding package**. Nous vous recommandons d’enregistrer le package de déboardage sur un lecteur amovible.

7. Exécutez le script sur chaque appareil que vous souhaitez hors d’board. 

   Vous avez besoin d’aide pour cette tâche ? Consultez les ressources suivantes :   

   - Windows périphériques : [hors Windows à l’aide d’un script local](../defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   - Appareils macOS : [désinstallation sur macOS](../defender-endpoint/mac-resources.md#uninstalling)
   - Appareils Linux [: désinstallation sur Linux](../defender-endpoint/linux-resources.md#uninstall)

> [!IMPORTANT]
> L’arrêt de l’board d’un appareil entraîne l’arrêt de l’envoi de données à Defender for Business (prévisualisation). Toutefois, les données reçues avant laboarding sont conservées pendant six (6) mois au plus.

## <a name="next-steps"></a>Prochaines étapes

Procédez comme il se doit pour :

- [Étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour Entreprise (prévisualisation)](mdb-configure-security-settings.md)

- [Commencer à utiliser Microsoft Defender pour les entreprises (prévisualisation)](mdb-get-started.md) 