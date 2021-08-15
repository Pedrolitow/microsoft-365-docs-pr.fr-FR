---
title: Protéger votre organisation contre les menaces web
description: Découvrez la protection web dans Microsoft Defender pour point de terminaison et la façon dont elle peut protéger votre organisation.
keywords: protection web, protection contre les menaces web, navigation web, sécurité, hameçonnage, programmes malveillants, attaque, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3ba4c4dbb2b5b8315fb09023b9fa0c0e29c4fd1c3b3f95da0328522a7d839ffc
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53884258"
---
# <a name="protect-your-organization-against-web-threats"></a>Protéger votre organisation contre les menaces web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

La protection contre les menaces web fait partie de [la protection Web](web-protection-overview.md) dans Defender for Endpoint. Il utilise la [protection réseau](network-protection.md) pour sécuriser vos appareils contre les menaces web. En intégrant des Microsoft Edge et des navigateurs tiers populaires tels que Chrome et Firefox, la protection contre les menaces web arrête les menaces web sans proxy web et peut protéger les appareils lorsqu’ils sont absents ou locaux. La protection contre les menaces web arrête l’accès aux sites de hameçonnage, aux vecteurs de programmes malveillants, aux sites d’exploitation, aux sites non fiables ou à faible réputation, ainsi qu’aux sites que vous avez bloqués dans votre liste d’indicateurs [personnalisés.](manage-indicators.md)

> [!NOTE]
> La réception de nouveaux indicateurs personnalisés peut prendre jusqu’à une heure.

## <a name="prerequisites"></a>Conditions préalables

La protection web utilise la protection réseau pour assurer la sécurité de la navigation web sur Microsoft Edge navigateurs web tiers.

Pour activer la protection réseau sur vos appareils :

- Modifiez la ligne de base de sécurité Defender for Endpoint sous **Web & Network Protection** pour activer la protection réseau avant de la déployer ou de la redéployer. [En savoir plus sur l’examen et l’affectation de la ligne de base de sécurité defender pour point de terminaison](configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline)
- Activer la protection réseau sur l’utilisation de la configuration de l’appareil Intune, de SCCM, de la stratégie de groupe ou de votre solution MDM. [En savoir plus sur l’activation de la protection réseau](enable-network-protection.md)

> [!NOTE]
> Si vous définissez la protection réseau sur **Audit uniquement,** le blocage sera indisponible. En outre, vous pourrez détecter et enregistrer les tentatives d’accès à des sites web malveillants et indésirables Microsoft Edge uniquement.

## <a name="related-topics"></a>Sujets connexes

- [Vue d’ensemble de la protection web](web-protection-overview.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Surveiller la sécurité web](web-protection-monitoring.md)
- [Répondre aux menaces web](web-protection-response.md)
- [Protection du réseau](network-protection.md)
