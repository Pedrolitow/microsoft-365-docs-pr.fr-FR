---
title: Intégrer des appareils à Microsoft Defender pour Les Entreprises
description: En savoir plus sur les options d’intégration d’appareil dans Microsoft Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/03/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: e4b28078c79b47ae48af590457d6721b0b470659
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317400"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Intégrer des appareils à Microsoft Defender pour Les Entreprises

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

L’expérience d’intégration d’appareil dans Defender pour Entreprise repose sur des processus similaires à ceux que nous utilisons dans Microsoft Defender pour Endpoint. Regardez la vidéo suivante pour voir comment cela fonctionne :<br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Avec Microsoft Defender entreprise, vous avez le choix entre plusieurs options pour intégrer les appareils de votre organisation. Cet article vous présente vos options et inclut une vue d’ensemble du fonctionnement de l’intégration.

> [!TIP]
> Pour afficher des informations plus détaillées sur l’intégration d’appareils dans Defender pour le point de terminaison, voir Appareils intégrés et configurer [Microsoft Defender pour les fonctionnalités de point de terminaison](../defender-endpoint/onboard-configure.md).

## <a name="what-to-do"></a>Procédure

1. Consultez les options [d’intégration des appareils](#device-onboarding-methods) et sélectionnez l’une des méthodes suivantes : 

   - [Intégration automatique pour les appareils Windows inscrits dans Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
   - [Script local pour les Windows et Mac](#local-script-in-defender-for-business)
   - [Microsoft Endpoint Manager (Microsoft Intune)](#microsoft-endpoint-manager)
   - [Configuration de la sécurité de Microsoft Defender pour les entreprises](#microsoft-defender-for-business-security-configuration)

2. [Exécutez un test de détection](#run-a-detection-test) pour les appareils Windows intégrés.

3. [Consultez les étapes suivantes](#next-steps). 

Cet article inclut également des informations sur l’exécution [d’un test de détection pour Windows appareils mobiles](#run-a-detection-test) et laboarding [d’un appareil](#offboarding-a-device).

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="device-onboarding-methods"></a>Méthodes d’intégration d’appareil

Le tableau suivant décrit les méthodes les plus couramment utilisées pour intégrer des appareils à Defender for Business. 

| Méthode d’intégration  | Description  | Système d’exploitation |
|---------|---------|---------|
| **Intégration automatique**<br/>(*disponible pour les clients qui utilisent déjà Microsoft Endpoint Manager*) | *Microsoft 365 Business Premium clients ont déjà Microsoft Intune et peuvent utiliser cette option*. L’intégration automatique définit une connexion entre Defender entreprise et Microsoft Endpoint Manager, puis Windows appareils à Defender for Business. Pour utiliser cette option, vos appareils doivent déjà être inscrits Endpoint Manager.<br/><br/>Pour en savoir plus, [consultez l’intégration automatique](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager). | Windows |
| **Script local** <br/> | Cette option vous permet d’intégrer manuellement des appareils individuels à Defender for Business. Vous pouvez intégrer jusqu’à 10 appareils à la fois à l’aide du script local.<br/><br/>Pour plus d’informations, [voir script local dans Defender for Business](#local-script-in-defender-for-business). | Windows <br/>macOS |
| **Microsoft Intune** ou **Microsoft Endpoint Manager**<br/>(*disponible pour les clients qui utilisent Microsoft Intune ou Endpoint Manager*) | [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [gestion des](/mem/intune/enrollment/device-enrollment) périphériques mobiles font partie des Endpoint Manager. Microsoft 365 Business Premium clients ont déjà Microsoft Intune et peuvent utiliser cette option.<br/><br/>Si vous utilisiez déjà Endpoint Manager avant d’obtenir Defender entreprise, vous pouvez choisir de continuer à utiliser Endpoint Manager pour intégrer et gérer les appareils<br/><br/>Pour utiliser cette méthode, voir [Microsoft Endpoint Manager](#microsoft-endpoint-manager). | Windows <br/>macOS<br/>iOS<br/>Système d’exploitation Android | 
| **Configuration de la sécurité de Microsoft Defender pour les entreprises** <br/>(*utilise le portail Microsoft 365 Defender)*) | Pour utiliser cette option, vous configurez certains paramètres pour faciliter la communication entre Defender for Business et Endpoint Manager. Ensuite, vous devez intégrer des appareils dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) à l’aide d’un package que vous téléchargez et exécutez sur chaque appareil. Une relation d’confiance est établie entre les appareils et Azure Active Directory (Azure AD), et les stratégies de sécurité de Defender for Business sont poussées vers les appareils.<br/><br/>Pour en savoir plus, [consultez la configuration de la sécurité de Microsoft Defender entreprise](#microsoft-defender-for-business-security-configuration). | Windows <br/>macOS |



> [!IMPORTANT]
> Si un problème se produit et que votre processus d’intégration échoue, consultez [La résolution des problèmes de Microsoft Defender entreprise](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Intégration automatique pour les appareils Windows inscrits dans Microsoft Endpoint Manager

L’option d’intégration automatique s’applique Windows appareils uniquement. L’intégration automatique est disponible si votre organisation utilisait déjà Microsoft Endpoint Manager, Microsoft Intune ou la gestion des périphériques mobiles (MDM) dans Microsoft Intune avant d’obtenir Defender pour les entreprises et que vous avez déjà inscrit Windows appareils Endpoint Manager. 

Si Windows appareils sont déjà inscrits dans Endpoint Manager, Defender entreprise détecte ces appareils pendant que vous êtes en train de configurer Defender pour les entreprises. Vous serez invité à vous demander si vous souhaitez utiliser l’intégration automatique pour l’ensemble ou une partie de Windows appareils. Vous pouvez intégrer tous les Windows en même temps, ou sélectionner des appareils spécifiques pour commencer, puis ajouter d’autres appareils ultérieurement.

Pour en savoir plus sur l’intégration automatique, consultez l’étape 2 de l’Assistant pour [configurer Microsoft Defender pour les entreprises](mdb-use-wizard.md).

## <a name="local-script-in-defender-for-business"></a>Script local dans Defender for Business

Vous pouvez utiliser un script local pour intégrer des Windows mac. Lorsque vous exécutez le script d’intégration sur un appareil, il crée une relation d’confiance avec Azure Active Directory, inscrit l’appareil dans Microsoft Endpoint Manager et l’intégrera à Defender for Business. Cette méthode est utile pour l’intégration d’appareils dans Defender for Business. Vous pouvez intégrer jusqu’à 10 appareils à la fois.

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis sous Gestion **des appareils,** choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, tel **que Windows 10 et 11**, puis, sous Intégrer un **appareil, dans** **la section Méthode** de déploiement, choisissez **Script local**. 

4. **Sélectionnez Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible.

5. Suivez les instructions des articles suivants :

   - Windows : intégrer [des appareils Windows à l’aide d’un script local](../defender-endpoint/configure-endpoints-script.md#onboard-devices)
   - Appareils macOS : [déploiement manuel de Microsoft Defender pour endpoint sur macOS](../defender-endpoint/mac-install-manually.md#client-configuration)

## <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

Si vous utilisiez déjà Endpoint Manager (qui inclut Microsoft Intune et Gestion des appareils mobiles), avant d’obtenir Defender pour Entreprise, vous pouvez continuer à utiliser Endpoint Manager pour intégrer les appareils de votre organisation. Avec Endpoint Manager, vous pouvez intégrer des ordinateurs, des tablettes et des téléphones, y compris des appareils iOS et Android.

Voir [Inscription des appareils dans Microsoft Intune](/mem/intune/enrollment/device-enrollment).

## <a name="microsoft-defender-for-business-security-configuration"></a>Configuration de la sécurité de Microsoft Defender pour les entreprises

> [!NOTE]
> Si vous utilisez déjà Endpoint Manager pour gérer vos appareils et vos stratégies de sécurité, ignorez cette méthode et [Microsoft Endpoint Manager à la](#microsoft-endpoint-manager) place.

La configuration de la sécurité de Microsoft Defender pour les entreprises a été conçue sur une fonctionnalité appelée Gestion de la sécurité [pour Microsoft Defender pour point de terminaison (prévisualisation).](/mem/intune/protect/mde-security-integration) Il vous permet d’intégrer des appareils à Defender for Business dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) sans que ces appareils soient entièrement inscrits au Microsoft Endpoint Manager préalablement. 

Cette méthode vous permet d’intégrer des appareils et de gérer vos stratégies antivirus et de pare-feu dans le Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Voici le principe de fonctionnement :

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

Si vous souhaitez hors d’un appareil, suivez les étapes suivantes :

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Dans le volet de navigation, choisissez **Paramètres**, puis les **points de terminaison**.

3. Sous **Gestion des appareils**, sélectionnez **Offboarding (Boarding).**

4. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, sous Horsboard d’un **appareil, dans** **la section Méthode** de déploiement, choisissez **Script local**. 

5. Dans l’écran de confirmation, examinez les informations, puis choisissez **Télécharger** pour continuer.

6. **Sélectionnez Télécharger le package deboarding**. Nous vous recommandons d’enregistrer le package de déboardage sur un lecteur amovible.

7. Exécutez le script sur chaque appareil que vous souhaitez hors d’board. Vous avez besoin d’aide pour cette tâche ? Consultez les ressources suivantes :   

   - Windows : hors [Windows à l’aide d’un script local](../defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   - Appareils macOS : [désinstallation sur macOS](../defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Laboarding d’un appareil entraîne l’arrêt de l’envoi de données à Defender for Business. Toutefois, les données reçues avant laboarding sont conservées pendant six (6) mois au plus.

## <a name="next-steps"></a>Étapes suivantes

Procédez comme il se doit pour :

- [Étape 5 : Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les entreprises](mdb-configure-security-settings.md)

- [Commencer à utiliser Microsoft Defender pour les entreprises](mdb-get-started.md) 
