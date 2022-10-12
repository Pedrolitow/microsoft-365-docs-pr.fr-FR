---
title: démonstrations de réputation d’URL Microsoft Defender pour point de terminaison SmartScreen
description: Montre comment Microsoft Defender SmartScreen identifie les sites web de hameçonnage et de programmes malveillants en fonction de la réputation de l’URL.
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
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 7303d0eb27a13d296a353d10b16b5fa32bcc0267
ms.sourcegitcommit: 4f8200453d347de677461f27eb5a3802ce5cc888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68542582"
---
<!--- v-jweston resumes authorship and ms.authorship appx April-May 2023 ---> 

# <a name="url-reputation-demonstrations"></a>Démonstrations de réputation d’URL

Testez comment Microsoft Defender SmartScreen vous aide à identifier les sites web de hameçonnage et de programmes malveillants en fonction de la réputation de l’URL.
Configuration requise et configuration du scénario

- Windows 10 ou 11
- Navigateur Microsoft Edge requis
- Pour plus d’informations, consultez [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

## <a name="smartscreen-for-microsoft-edge-url-scenario-demonstrations"></a>Démonstrations de scénarios d’URL SmartScreen pour Microsoft Edge

### <a name="is-this-phishing"></a>S’agit-il d’un hameçonnage ?

Avertit l’utilisateur d’une page suspecte et demande des commentaires :

- [S’agit-il d’un hameçonnage ?](https://demo.smartscreen.msft.net/other/areyousure.html)

  Le lancement de ce lien doit afficher un message similaire à la capture d’écran suivante :

  :::image type="content" source="images/smartscreen-url-reputation-is-this-phishing.png" alt-text="SmartScreen avertit l’utilisateur que le site est potentiellement un site de hameçonnage et peut-être dangereux":::

### <a name="phishing-page"></a>Page Hameçonnage

Page connue pour le hameçonnage qui doit être bloquée :

- [Page d’hameçonnage connue](https://demo.smartscreen.msft.net/phishingdemo.html)

  Le lancement de ce lien doit afficher un message similaire à l’exemple suivant :

  :::image type="content" source="images/smartscreen-url-reputation-this-is-phishing.png" alt-text="SmartScreen signale que le site est connu pour contenir des menaces de hameçonnage":::

### <a name="malware-page"></a>Page Programmes malveillants

Page qui héberge des programmes malveillants et qui doit être bloquée :

- [Page des programmes malveillants connus](https://demo.smartscreen.msft.net/other/malware.html)

  Le lancement de ce lien doit afficher un message similaire à la capture d’écran suivante :

  :::image type="content" source="images/smartscreen-url-reputation-malware-page.png" alt-text="SmartScreen avertit l’utilisateur que le site est connu pour contenir des programmes dangereux":::

### <a name="blocked-download"></a>Téléchargement bloqué

Blocage du téléchargement en raison de sa réputation d’URL

- [Téléchargement bloqué en raison de la réputation de l’URL](https://demo.smartscreen.msft.net/download/malwaredemo/freevideo.exe)

  Le lancement de ce lien doit afficher un message similaire au message de la page Programmes malveillants.

### <a name="exploit-page"></a>Page Exploit

Page qui attaque une vulnérabilité de navigateur

- [Page d’exploit de navigateur connue](https://demo.smartscreen.msft.net/other/exploit.html)

  Le lancement de ce lien doit afficher un message similaire au message de la page Programmes malveillants.

### <a name="malvertising"></a>Malvertisation

Une page bénigne hébergeant une publicité malveillante

- [Page connue pour contenir des publicités malveillantes](https://demo.smartscreen.msft.net/other/exploit_frame.html)

  Le lancement de ce lien doit afficher un message similaire à la capture d’écran suivante :

  :::image type="content" source="images/smartscreen-url-reputation-malvertising.png" alt-text="Démonstration de la façon dont SmartScreen répond à un cadre d’une page détectée comme malveillante. Seul le cadre malveillant est bloqué":::

## <a name="see-also"></a>Voir aussi

[documentation Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

[Microsoft Defender pour point de terminaison - Scénarios de démonstration](defender-endpoint-demonstrations.md)
