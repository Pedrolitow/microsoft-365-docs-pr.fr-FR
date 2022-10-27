---
title: Microsoft Defender pour point de terminaison démonstrations de réputation d’URL SmartScreen
description: Montre comment Microsoft Defender SmartScreen identifie les sites web d’hameçonnage et de programmes malveillants en fonction de la réputation des URL.
keywords: Microsoft Defender pour point de terminaison, protection contre le hameçonnage de site web, protection contre les programmes malveillants de site web, réputation d’URL, démonstration,
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
ms.openlocfilehash: 3f00b4cf32c3813bfcf67e2390f503156097d9f2
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729630"
---
# <a name="url-reputation-demonstrations"></a>Démonstrations de réputation d’URL

Testez comment Microsoft Defender SmartScreen vous aide à identifier les sites web d’hameçonnage et de programmes malveillants en fonction de la réputation des URL.
Configuration requise et configuration du scénario

- Windows 10 ou 11
- Navigateur Microsoft Edge requis
- Pour plus d’informations, consultez [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

## <a name="smartscreen-for-microsoft-edge-url-scenario-demonstrations"></a>Démonstrations de scénarios d’URL SmartScreen pour Microsoft Edge

### <a name="is-this-phishing"></a>S’agit-il d’un hameçonnage ?

Alerte l’utilisateur à une page suspecte et demande des commentaires :

- [S’agit-il d’un hameçonnage ?](https://demo.smartscreen.msft.net/other/areyousure.html)

  Le lancement de ce lien doit afficher un message similaire à la capture d’écran suivante :

  :::image type="content" source="images/smartscreen-url-reputation-is-this-phishing.png" alt-text="SmartScreen avertit l’utilisateur que le site est potentiellement un site d’hameçonnage et potentiellement dangereux":::

### <a name="phishing-page"></a>Page d’hameçonnage

Page connue pour le hameçonnage qui doit être bloquée :

- [Page d’hameçonnage connue](https://demo.smartscreen.msft.net/phishingdemo.html)

  Le lancement de ce lien doit afficher un message similaire à l’exemple suivant :

  :::image type="content" source="images/smartscreen-url-reputation-this-is-phishing.png" alt-text="SmartScreen signale que le site est connu pour contenir des menaces d’hameçonnage":::

### <a name="malware-page"></a>Page Des programmes malveillants

Page qui héberge des programmes malveillants et qui doit être bloquée :

- [Une page de programmes malveillants connus](https://demo.smartscreen.msft.net/other/malware.html)

  Le lancement de ce lien doit afficher un message similaire à la capture d’écran suivante :

  :::image type="content" source="images/smartscreen-url-reputation-malware-page.png" alt-text="SmartScreen avertit l’utilisateur que le site est connu pour contenir des programmes dangereux":::

### <a name="blocked-download"></a>Téléchargement bloqué

Blocage du téléchargement en raison de sa réputation d’URL

- [Téléchargement bloqué en raison de la réputation de l’URL](https://demo.smartscreen.msft.net/download/malwaredemo/freevideo.exe)

  Le lancement de ce lien doit afficher un message similaire au message de la page Programme malveillant.

### <a name="exploit-page"></a>Page Exploit

Page qui attaque une vulnérabilité de navigateur

- [Page d’exploitation du navigateur connu](https://demo.smartscreen.msft.net/other/exploit.html)

  Le lancement de ce lien doit afficher un message similaire au message de la page Programme malveillant.

### <a name="malvertising"></a>Malvertisation

Page inoffensive hébergeant une publicité malveillante

- [Une page connue pour contenir des publicités malveillantes](https://demo.smartscreen.msft.net/other/exploit_frame.html)

  Le lancement de ce lien doit afficher un message similaire à la capture d’écran suivante :

  :::image type="content" source="images/smartscreen-url-reputation-malvertising.png" alt-text="Démonstration de la façon dont SmartScreen répond à un cadre sur une page détectée comme malveillante. Seule la trame malveillante est bloquée":::

## <a name="see-also"></a>Voir aussi

[documentation Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

[Microsoft Defender pour point de terminaison - scénarios de démonstration](defender-endpoint-demonstrations.md)
