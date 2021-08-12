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
ms.openlocfilehash: a015755d0848b0287854db67021599917851d889bb178ff4f4129e02c09919db
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53806289"
---
# <a name="create-indicators"></a>Créer des indicateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> [!TIP]
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

L’indicateur de compromission (IoCs) est une fonctionnalité essentielle dans chaque solution de protection des points de terminaison. Cette fonctionnalité permet à SecOps de définir une liste d’indicateurs pour la détection et le blocage (prévention et réponse).

Créez des indicateurs qui définissent la détection, la prévention et l’exclusion des entités. Vous pouvez définir l’action à prendre, ainsi que la durée de l’application de l’action, ainsi que l’étendue du groupe d’appareils à appliquer.

Les sources actuellement pris en charge sont le moteur de détection cloud de Defender pour Endpoint, le moteur automatisé d’investigation et de correction et le moteur de prévention des points de terminaison (Antivirus Microsoft Defender).

**Moteur de détection cloud**<br>
Le moteur de détection cloud de Defender for Endpoint analyse régulièrement les données collectées et tente de correspondre aux indicateurs que vous avez définies. En cas de correspondance, une action est prise en fonction des paramètres que vous avez spécifiés pour l’IoC.

**Moteur de prévention des points de terminaison**<br>
La même liste d’indicateurs est honorée par l’agent de prévention. Autrement dit, si Microsoft Defender AV est le principal antivirus configuré, les indicateurs de correspondance seront traités en fonction des paramètres. Par exemple, si l’action est « Alerte et bloquer », l’Antivirus Microsoft Defender empêche les exécutions de fichiers (bloquer et corriger) et une alerte correspondante est élevée. En revanche, si l’action est définie sur « Autoriser », l’Antivirus Microsoft Defender ne détecte pas et ne bloque pas l’exécuter.

**Moteur d’examen et de correction automatisé**<BR>
L’examen et la correction automatisés se comportent de la même manière. Si un indicateur est définie sur « Autoriser », l’examen et la correction automatisés ignorent un verdict « mauvais » pour lui. S’il est définie sur « Bloquer », les examens et corrections automatisés le traitent comme « mauvais ».

> [!NOTE]
> Le paramètre EnableFileHashComputation calcule le hachage de fichier pour le cert et l’IoC de fichier pendant les analyses de fichiers. Il prend en charge l’application IoC des haps et des certs appartenant à des applications fiables. Elle sera activée et désactivée simultanément avec le paramètre autoriser ou bloquer le fichier. EnableFileHashComputation est activé manuellement par le biais de la stratégie de groupe et est désactivé par défaut.


Les actions actuellement prises en charge sont :
- Autoriser
- Alerte uniquement
- Alerte et blocage


Vous pouvez créer un indicateur pour :
- [Files](indicator-file.md)
- [Adresses IP, URL/domaines](indicator-ip-domain.md)
- [Certificats](indicator-certificates.md)


> [!NOTE]
> Il existe une limite de 15 000 indicateurs par client. Les indicateurs de fichier et de certificat ne bloquent pas les [exclusions définies pour Antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus). Les indicateurs ne sont pas pris en charge Antivirus Microsoft Defender lorsqu’il est en mode passif. 


## <a name="related-topics"></a>Sujets connexes

- [Créer un IoC contextuel](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Utiliser l’API d’indicateurs microsoft Defender pour les points de terminaison](ti-indicator.md)
- [Utiliser des solutions intégrées par des partenaires](partner-applications.md)
