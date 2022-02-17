---
title: Intégrer des appareils à Microsoft Defender pour Entreprises (prévisualisation)
description: En savoir plus sur les options d’intégration d’appareil dans Microsoft Defender entreprise (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/16/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 073478300e6b5a9d5a9fc10e634f6e3113897fb3
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2022
ms.locfileid: "62879239"
---
# <a name="onboard-devices-to-microsoft-defender-for-business-preview"></a>Intégrer des appareils à Microsoft Defender pour Entreprises (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et sera progressivement mis en place pour les clients [](https://aka.ms/mdb-preview) et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

L’expérience d’intégration d’appareil dans Defender for Business repose sur les mêmes processus d’intégration d’appareil que ceux utilisés dans Microsoft Defender pour Endpoint. Regardez la vidéo suivante pour voir comment cela fonctionne :<br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Avec Microsoft Defender entreprise (prévisualisation), vous avez le choix entre plusieurs options pour intégrer les appareils de votre organisation. Cet article vous présente vos options et inclut une vue d’ensemble du fonctionnement de l’intégration.

> [!TIP]
> Pour afficher des informations plus détaillées sur l’intégration d’appareils dans Defender pour le point de terminaison, voir Appareils intégrés et configurer [Microsoft Defender pour les fonctionnalités de point de terminaison](../defender-endpoint/onboard-configure.md).

## <a name="what-to-do"></a>Procédure

1. Consultez les options [d’intégration des appareils](#device-onboarding-methods).

2. Intégrer un appareil à l’aide de l’une des méthodes suivantes :
    - [Intégration automatique pour les appareils Windows inscrits dans Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
    - [Un script local pour Windows, macOS et Linux](#onboard-devices-using-a-local-script-in-defender-for-business)
    - [Microsoft Endpoint Manager pour ordinateurs, tablettes et téléphones](#onboard-devices-using-microsoft-endpoint-manager)
    - [Stratégie de groupe pour Windows appareils mobiles](#onboard-windows-devices-using-group-policy)
    - [Autre méthode non répertoriée ici](#onboard-devices-using-a-method-not-listed-here)

3. [Exécutez un test de détection](#run-a-detection-test) pour les appareils Windows nouvellement intégrés.

4. [Consultez les étapes suivantes](#next-steps). 

Cet article inclut également des informations [sur laboardage d’un appareil](#offboarding-a-device).

## <a name="device-onboarding-methods"></a>Méthodes d’intégration d’appareil

Le tableau suivant décrit les méthodes les plus couramment utilisées pour intégrer des appareils à Defender for Business. 

| Méthode d’intégration  | Description  |
|---------|---------|
| **Intégration automatique**<br/>(*disponible pour les clients qui utilisent déjà Microsoft Endpoint Manager*) | L’intégration automatique définit une connexion entre Defender pour Entreprise (prévisualisation) et Microsoft Endpoint Manager, puis Windows appareils à Defender for Business (prévisualisation). Les appareils doivent déjà être inscrits dans Endpoint Manager.<br/><br/>Pour plus d’informations, voir [Utiliser l’intégration automatique Windows appareils inscrits dans Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager). |
| **Script local**<br/>(*recommandé lors de la prévisualisation ; utile pour l’intégration de quelques appareils à la fois*)  | Vous pouvez intégrer des ordinateurs à Defender for Business (prévisualisation) à l’aide d’un script que vous téléchargez et exécutez sur des appareils Windows, macOS ou Linux. Le script définit une relation d’Azure Active Directory et inscrit l’appareil.<br/><br/>Pour utiliser cette méthode, voir [Appareils intégrés à l’aide d’un script local dans Defender for Business](#onboard-devices-using-a-local-script-in-defender-for-business). |
| **Microsoft Intune** ou **Microsoft Endpoint Manager**<br/>(*disponible pour les clients qui utilisent déjà Microsoft Intune ou Endpoint Manager*) | [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [gestion des](/mem/intune/enrollment/device-enrollment) périphériques mobiles font partie de Endpoint Manager. Si vous utilisiez déjà Endpoint Manager avant d’obtenir Defender entreprise (prévisualisation), vous pouvez choisir de continuer à utiliser Endpoint Manager pour intégrer et gérer les appareils<br/><br/>Pour utiliser cette méthode, voir [Appareils intégrés à l’aide Microsoft Endpoint Manager](#onboard-devices-using-microsoft-endpoint-manager). |
| **Stratégie de groupe** | Si votre organisation utilise déjà la stratégie de groupe, vous pouvez créer des G GPO et les appliquer aux appareils de votre organisation dans Defender for Business (prévisualisation).<br/><br/>Pour en savoir plus sur cette méthode, consultez [la Windows de groupe à l’aide de la stratégie de groupe](#onboard-windows-devices-using-group-policy). | 

> [!IMPORTANT]
> Si un problème se produit et que votre processus d’intégration échoue, consultez [La résolution des problèmes de Microsoft Defender entreprise](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Intégration automatique pour les appareils Windows inscrits dans Microsoft Endpoint Manager

L’option d’intégration automatique s’applique Windows appareils uniquement. Cette option est disponible si votre organisation utilisait déjà Microsoft Endpoint Manager, Microsoft Intune ou la gestion des périphériques mobiles (MDM) dans Microsoft Intune avant d’obtenir Defender entreprise (prévisualisation) et que vous avez déjà inscrit Windows appareils. Endpoint Manager. 

Si Windows appareils sont déjà inscrits dans Endpoint Manager, Defender entreprise détecte ces appareils pendant que vous êtes en train de configurer et de configurer Defender pour les entreprises. Vous serez invité à vous demander si vous souhaitez utiliser l’intégration automatique pour l’ensemble ou une partie de Windows appareils. 

Le processus d’intégration automatique permet de mettre en place une connexion entre Defender entreprise et Endpoint Manager, puis d’intégrer des appareils à Defender for Business. Vous pouvez choisir d’intégrer tous les appareils Windows en même temps, ou sélectionner un ensemble d’appareils Windows à intégrer.

Pour en savoir plus, consultez l’étape 3 de l’Assistant pour [configurer Microsoft Defender pour les entreprises (prévisualisation).](mdb-use-wizard.md)

## <a name="onboard-devices-using-a-local-script-in-defender-for-business"></a>Intégrer des appareils à l’aide d’un script local dans Defender for Business

Vous pouvez utiliser un script local pour intégrer des Windows, macOS et Linux à Defender for Business. Lorsque vous exécutez le script d’intégration sur un appareil, il crée une relation d’confiance avec Azure Active Directory, inscrit l’appareil dans Microsoft Endpoint Manager et l’intégrera à Defender for Business. Cette méthode est utile pour l’intégration d’appareils dans Defender for Business et pour l’intégration de quelques appareils à la fois.

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis sous Gestion **des appareils,** choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, **tel que Windows 10 et 11**, puis, sous Intégrer un **appareil, dans** **la section Méthode** de déploiement, choisissez **Script local**. 

4. **Sélectionnez Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible.

5. Suivez les instructions des articles suivants :

   - Windows : intégrer [des appareils Windows à l’aide d’un script local](../defender-endpoint/configure-endpoints-script.md#onboard-devices)
   - Appareils macOS : [déploiement manuel de Microsoft Defender pour endpoint sur macOS](../defender-endpoint/mac-install-manually.md#client-configuration)
   - Appareils Linux : [déployer Microsoft Defender pour point de terminaison sur Linux manuellement](../defender-endpoint/linux-install-manually.md#client-configuration)

> [!IMPORTANT]
> Si un problème se produit et que votre processus d’intégration échoue, consultez La résolution des problèmes [de Microsoft Defender entreprise (prévisualisation](mdb-troubleshooting.yml)).

## <a name="onboard-devices-using-microsoft-endpoint-manager"></a>Intégrer des appareils à l’aide Microsoft Endpoint Manager

Si vous utilisiez déjà Microsoft Intune avant d’obtenir Defender entreprise (prévisualisation), vous pouvez continuer à utiliser Microsoft Intune pour intégrer des appareils. Avec Endpoint Manager, vous pouvez intégrer des ordinateurs, des tablettes et des téléphones. 

Voir [Inscription des appareils dans Microsoft Intune](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-windows-devices-using-group-policy"></a>Intégrer des appareils Windows à l’aide d’une stratégie de groupe

[La stratégie de](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831791(v=ws.11)) groupe est une infrastructure qui vous permet de spécifier des configurations gérées pour les utilisateurs et les ordinateurs via les paramètres de stratégie de groupe et les préférences de stratégie de groupe. Un objet de stratégie de groupe (GPO) est un objet logique composé d’un conteneur de stratégie de groupe et d’un modèle de stratégie de groupe. 

Si votre organisation utilise déjà la stratégie de groupe pour gérer les appareils, vous pouvez utiliser la stratégie de groupe pour intégrer des appareils à Defender for Business. Si vous débutez avec la stratégie de groupe, nous vous recommandons d’utiliser une autre méthode, telle que Endpoint Manager ou un script local à la place. 

Voir [Intégrer Windows à l’aide de la stratégie de groupe](../defender-endpoint/configure-endpoints-gp.md).

## <a name="onboard-devices-using-a-method-not-listed-here"></a>Intégrer des appareils à l’aide d’une méthode non répertoriée ici

Si vous souhaitez utiliser une autre méthode qui n’est pas répertoriée dans cet article pour intégrer des appareils, consultez les options de l’outil d’intégration [et de configuration](../defender-endpoint/onboard-configure.md#onboarding-and-configuration-tool-options).

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Une fois que vous avez intégré des appareils Windows à Defender for Business (prévisualisation), vous pouvez exécuter un test de détection sur un appareil Windows pour vous assurer que tout fonctionne correctement.

1. Sur le Windows, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez l’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre Invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécuté, la fenêtre d’invite de commandes se ferme automatiquement. Si elle réussit, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour le périphérique nouvellement intégré dans environ 10 minutes.

## <a name="gradual-device-onboarding"></a>Intégration progressive d’appareils

Si vous souhaitez intégrer les appareils de votre organisation par phases, suivez les étapes suivantes :

1. Identifiez un ensemble d’appareils à intégrer.

2. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in.

3. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis sous Gestion **des appareils,** choisissez **Intégration**.

4. Sélectionnez un système d’exploitation (**par exemple, Windows 10 et 11),** puis choisissez une méthode d’intégration (par exemple, **un script local**). Suivez les instructions fournies pour la méthode que vous avez sélectionnée.

5. Répétez ce processus pour chaque ensemble d’appareils que vous souhaitez intégrer. 

> [!TIP]
> Vous n’avez pas besoin d’utiliser le même package d’intégration chaque fois que vous intégrerez des appareils. Par exemple, vous pouvez utiliser un script local pour intégrer certains appareils, puis choisir une autre méthode pour intégrer davantage d’appareils.

## <a name="offboarding-a-device"></a>Boarding d’un appareil

Si vous souhaitez hors d’un appareil, suivez les étapes suivantes :

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Dans le volet de navigation, choisissez **Paramètres**, puis les **points de terminaison**.

3. Sous **Gestion des appareils**, sélectionnez **Offboarding (Boarding).**

4. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, sous Horsboard d’un **appareil, dans** **la section Méthode** de déploiement, choisissez **Script local**. 

5. Dans l’écran de confirmation, examinez les informations, puis choisissez **Télécharger** pour continuer.

6. **Sélectionnez Télécharger le package deboarding**. Nous vous recommandons d’enregistrer le package de déboardage sur un lecteur amovible.

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