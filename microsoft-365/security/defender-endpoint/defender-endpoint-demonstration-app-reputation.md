---
title: Microsoft Defender pour point de terminaison démonstration de la réputation de l’application SmartScreen
description: Tester comment Microsoft Defender pour point de terminaison SmartScreen vous aide à identifier les sites web d’hameçonnage et de programmes malveillants
keywords: Microsoft Defender pour point de terminaison, site web d’hameçonnage, site web malveillant, réputation des applications,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: evaluation
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
- demo
ms.topic: article
ms.subservice: mde
ms.date: 10/21/2022
ms.openlocfilehash: cc7081f8c6e71e321e68016f45c5d400e3a1c3cd
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68730268"
---
# <a name="smartscreen-app-reputation-demonstration"></a>Démonstration de la réputation des applications SmartScreen

Testez la façon dont Microsoft Defender pour point de terminaison SmartScreen vous aide à identifier les sites web d’hameçonnage et de programmes malveillants en fonction de la réputation des applications.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10
- Internet Explorer ou navigateur Microsoft Edge requis
- Pour activer/désactiver, accédez à **Paramètres** > **Mise à jour & sécurité** >  **Sécurité Windows** >  **Ouvrir Sécurité Windows** >  App **& contrôle du** >  navigateur **Vérifier les applications et les fichiers**

## <a name="scenario-demos"></a>Démonstrations de scénario

### <a name="known-good-program"></a>Programme correct connu

Ce programme a une bonne réputation; le téléchargement doit s’exécuter sans interruption :

- [Téléchargement de programme correct connu](https://demo.smartscreen.msft.net/download/known/freevideo.exe)

  Le lancement de ce lien doit afficher un message similaire à ce qui suit :

  :::image type="content" source="images/smartscreen-app-reputation-known-good.png" alt-text="En fonction de la réputation du fichier cible, SmartScreen autorise le téléchargement sans interférence.":::

### <a name="unknown-program"></a>Programme inconnu

Étant donné que le téléchargement du programme n’a pas une réputation suffisante pour garantir sa fiabilité, SmartScreen affiche un avertissement avant d’exécuter le téléchargement du programme.

- [Programme inconnu](https://demo.smartscreen.msft.net/download/unknown/freevideo.exe)
  
  Le lancement de ce lien doit afficher un message similaire à ce qui suit :

  :::image type="content" source="images/smartscreen-app-reputation-unknown.png" alt-text="SmartScreen ne dispose pas d’informations de réputation suffisantes sur le fichier de téléchargement et avertit l’utilisateur d’arrêter ou de procéder avec prudence.":::

### <a name="known-malware"></a>Programmes malveillants connus

Ce téléchargement est un programme malveillant connu ; SmartScreen doit bloquer l’exécution de ce programme.

- [Programmes malveillants connus](https://demo.smartscreen.msft.net/download/known/knownmalicious.exe)

  Le lancement de ce lien doit afficher un message similaire à ce qui suit :

  :::image type="content" source="images/smartscreen-app-reputation-known-malware.png" alt-text="Capture d’écran montrant comment SmartScreen détecte un téléchargement de fichier avec une réputation dangereuse. le téléchargement est bloqué.":::

## <a name="learn-more"></a>En savoir plus

[documentation Microsoft Defender SmartScreen](/windows/security/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview.md)

## <a name="see-also"></a>Voir aussi

[Microsoft Defender pour point de terminaison - scénarios de démonstration](defender-endpoint-demonstrations.md)
