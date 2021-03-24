---
title: Créer des indicateurs
ms.reviewer: ''
description: Créez des indicateurs pour un hachage de fichier, une adresse IP, des URL ou des domaines qui définissent la détection, la prévention et l’exclusion des entités.
keywords: gérer, autorisé, bloqué, bloquer, nettoyer, malveillant, hachage de fichier, adresse IP, url, domaine
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: fc3bce7130dbdcec76a67df70eb1a6c72474013e
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064049"
---
# <a name="create-indicators"></a>Créer des indicateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

L’indicateur de compromission (IoCs) est une fonctionnalité essentielle dans chaque solution de protection des points de terminaison. Cette fonctionnalité permet à SecOps de définir une liste d’indicateurs pour la détection et le blocage (prévention et réponse).

Créez des indicateurs qui définissent la détection, la prévention et l’exclusion des entités. Vous pouvez définir l’action à prendre, ainsi que la durée de l’application de l’action, ainsi que l’étendue du groupe d’appareils à appliquer.

Les sources actuellement pris en charge sont le moteur de détection cloud de Defender pour Endpoint, le moteur d’examen et de correction automatisé et le moteur de prévention des points de terminaison (Microsoft Defender AV).

**Moteur de détection cloud**<br>
Le moteur de détection cloud de Defender for Endpoint analyse régulièrement les données collectées et tente de correspondre aux indicateurs que vous avez définies. En cas de correspondance, une action est prise en fonction des paramètres que vous avez spécifiés pour l’IoC.

**Moteur de prévention des points de terminaison**<br>
La même liste d’indicateurs est honorée par l’agent de prévention. Autrement dit, si Microsoft Defender AV est le principal antivirus configuré, les indicateurs de correspondance seront traités en fonction des paramètres. Par exemple, si l’action est « Alerte et bloquer », l’Antivirus Microsoft Defender empêche les exécutions de fichiers (bloquer et corriger) et une alerte correspondante est élevée. En revanche, si l’action est définie sur « Autoriser », l’Antivirus Microsoft Defender ne détecte pas et ne bloque pas l’exécuter.

**Moteur d’examen et de correction automatisé**<BR>
L’examen et la correction automatisés se comportent de la même manière. Si un indicateur est définie sur « Autoriser », l’examen et la correction automatisés ignorent un verdict « mauvais » pour lui. S’il est définie sur « Bloquer », les examens et corrections automatisés le traitent comme « mauvais ».


Les actions actuellement prises en charge sont :
- Autoriser
- Alerte uniquement
- Alerte et blocage


Vous pouvez créer un indicateur pour :
- [Files](indicator-file.md)
- [Adresses IP, URL/domaines](indicator-ip-domain.md)
- [Certificats](indicator-certificates.md)


>[!NOTE]
>Il existe une limite de 15 000 indicateurs par client.


## <a name="related-topics"></a>Voir aussi

- [Créer un IoC contextuel](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Utiliser l’API d’indicateurs microsoft Defender pour les points de terminaison](ti-indicator.md)
- [Utiliser des solutions intégrées par des partenaires](partner-applications.md)
