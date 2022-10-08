---
title: démonstration de la réputation de l’application Microsoft Defender pour point de terminaison SmartScreen
description: Tester la façon dont Microsoft Defender pour point de terminaison SmartScreen vous aide à identifier les sites web de hameçonnage et de programmes malveillants
keywords: Microsoft Defender pour point de terminaison, site web de hameçonnage, site web de programmes malveillants, réputation de l’application,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: evaluation
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 4601bc851266618dd2c55b1544f63e307336b125
ms.sourcegitcommit: 55672e44de74209f2e23b4bd9ca74a2ee7e88cd9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2022
ms.locfileid: "68319299"
---
# <a name="smartscreen-app-reputation-demonstration"></a>Démonstration de la réputation de l’application SmartScreen

Testez comment Microsoft Defender pour point de terminaison SmartScreen vous aide à identifier les sites web de hameçonnage et de programmes malveillants en fonction de la réputation de l’application.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10
- Navigateur Internet Explorer ou Microsoft Edge requis
- Pour activer/désactiver, accédez à La mise à jour **des paramètres** > **& Sécurité** >  **Sécurité Windows** >  **Dépendant Sécurité Windows** >  **App & contrôle** >  de navigateur **Vérifier les applications et les fichiers**

## <a name="scenario-demos"></a>Démonstrations de scénario

### <a name="known-good-program"></a>Bon programme connu

Ce programme a une bonne réputation; le téléchargement doit s’exécuter sans interruption :

- [Un bon téléchargement de programme connu](https://demo.smartscreen.msft.net/download/known/freevideo.exe)

  <!-- Hide {this intro with no subsequent list items} [Replace this link when new/updated source becomes available] -->

  Le lancement de ce lien doit afficher un message similaire à ce qui suit :

  :::image type="content" source="images/smartscreen-app-reputation-known-good.png" alt-text="En fonction de la réputation du fichier cible, SmartScreen autorise le téléchargement sans interférence.":::

### <a name="unknown-program"></a>Programme inconnu

Étant donné que le téléchargement du programme n’a pas la réputation suffisante pour garantir sa fiabilité, SmartScreen affiche un avertissement avant d’exécuter le téléchargement du programme.

- [Programme inconnu](https://demo.smartscreen.msft.net/download/unknown/freevideo.exe)

  <!-- Hide {this intro with no subsequent list items} [Replace this link when new/updated source becomes available] -->
  
  Le lancement de ce lien doit afficher un message similaire à ce qui suit :

  :::image type="content" source="images/smartscreen-app-reputation-unknown.png" alt-text="SmartScreen ne dispose pas d’informations de réputation suffisantes sur le fichier de téléchargement et avertit l’utilisateur d’arrêter ou de continuer avec précaution.":::

### <a name="known-malware"></a>Programmes malveillants connus

Ce téléchargement est un programme malveillant connu ; SmartScreen doit empêcher l’exécution de ce programme.

- [Programmes malveillants connus](https://demo.smartscreen.msft.net/download/known/knownmalicious.exe)

  <!-- Hide {this intro with no subsequent list items} [Replace this link when new/updated source becomes available] -->  

  Le lancement de ce lien doit afficher un message similaire à ce qui suit :

  :::image type="content" source="images/smartscreen-app-reputation-known-malware.png" alt-text="SmartScreen détecte un téléchargement de fichiers dont la réputation n’est pas sûre.; le téléchargement est bloqué.":::

## <a name="learn-more"></a>En savoir plus

[documentation Microsoft Defender SmartScreen](/windows/security/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview.md)

## <a name="see-also"></a>Voir aussi

[Microsoft Defender pour point de terminaison - Scénarios de démonstration](defender-endpoint-demonstrations.md)
