---
title: Comment signaler les faux positifs ou les faux négatifs dans AIR dans la protection contre les menaces Microsoft
description: Un message a-t-il été manqué ou incorrectement détecté par AIR dans la protection contre les menaces Microsoft ? Découvrez comment soumettre des faux positifs ou faux négatifs à Microsoft pour analyse.
keywords: automatisation, analyse, alerte, déclencheur, action, correction, faux positif, faux négatif
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.custom: autoir
ms.openlocfilehash: d9175e78326832a2be874359babae5ae9c689420
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41600081"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Comment signaler les faux positifs/négatifs dans les fonctionnalités d’analyse et de réponse automatisées

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

La protection contre les menaces a-t-elle permis d’effectuer des [recherches et des réponses automatiques](mtp-autoir.md) dans Microsoft Threat Protection ? Vous pouvez le signaler à Microsoft ou ajuster vos alertes (le cas échéant). Utilisez le tableau suivant comme guide : 


|Item  |Détectés par  |Comment le signaler  |
|---------|---------|---------|
|Message électronique <br/>Pièce jointe de courrier électronique <br/>URL dans un message électronique ou un fichier Office      |[Protection avancée contre les menaces dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)        |[Soumission de courrier indésirable, hameçon, URL et fichiers suspects à Microsoft pour l’analyse Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/admin-submission)         |
|Fichier ou application sur un appareil    |[Microsoft Defender – Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection)         |[Envoi d’un fichier à Microsoft pour l’analyse des programmes malveillants](https://www.microsoft.com/wdsi/filesubmission)         |
|Alerte déclenchée par une utilisation légitime <br/>Alerte inexacte    |[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)<br/> ou <br/>[Détection de menaces avancées Azure](https://docs.microsoft.com/azure/security/fundamentals/threat-detection)         |[Gérer les alertes dans le portail de sécurité des applications Cloud](https://docs.microsoft.com/cloud-app-security/managing-alerts)         |


## <a name="next-steps"></a>Étapes suivantes

- [Approuver ou refuser les actions liées à un examen et réponse automatisées](mtp-autoir-actions.md)
- [En savoir plus sur le centre de notifications](mtp-action-center.md).
- [Repérage proactive de menaces avec repérage avancé dans la Protection Microsoft contre les menaces](advanced-hunting-overview.md)
