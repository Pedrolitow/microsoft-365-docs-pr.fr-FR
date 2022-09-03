---
title: Protéger votre organisation contre les menaces web
description: Découvrez la protection web dans Microsoft Defender pour point de terminaison et comment elle peut protéger votre organisation.
keywords: protection web, protection contre les menaces web, navigation web, sécurité, hameçonnage, programmes malveillants, exploit, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 08/22/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: f5df3cdfa8b7bb699126e9362de53a7cfa52b8fc
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67576228"
---
# <a name="protect-your-organization-against-web-threats"></a>Protéger votre organisation contre les menaces web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

La protection contre les menaces web fait partie de la [protection web](web-protection-overview.md) dans Defender pour point de terminaison. Il utilise la [protection réseau](network-protection.md) pour sécuriser vos appareils contre les menaces web. En s’intégrant à Microsoft Edge et à des navigateurs tiers populaires comme Chrome et Firefox, la protection contre les menaces web arrête les menaces web sans proxy web et peut protéger les appareils lorsqu’ils sont absents ou en local. La protection contre les menaces web arrête l’accès aux sites de hameçonnage, aux vecteurs de programmes malveillants, aux sites d’exploitation, aux sites non approuvés ou à faible réputation, ainsi qu’aux sites que vous avez bloqués dans votre [liste d’indicateurs personnalisés](manage-indicators.md).

> [!NOTE]
> La réception de nouveaux indicateurs personnalisés peut prendre jusqu’à deux heures pour les appareils.

## <a name="prerequisites"></a>Prerequisites

La protection web utilise la protection réseau pour assurer la sécurité de la navigation web sur Microsoft Edge et les navigateurs web tiers.

Pour activer la protection réseau sur vos appareils :

- Modifiez la ligne de base de sécurité Defender pour point de terminaison sous **Web & Network Protection** pour activer la protection réseau avant de la déployer ou de la redéployer. [En savoir plus sur l’examen et l’affectation de la base de référence de sécurité Defender pour point de terminaison](configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline)
- Activez la protection réseau à l’aide de Intune configuration d’appareil, SCCM, stratégie de groupe ou votre solution GPM. [En savoir plus sur l’activation de la protection réseau](enable-network-protection.md)

> [!NOTE]
> Si vous définissez la protection réseau **sur Audit uniquement**, le blocage n’est pas disponible. En outre, vous serez en mesure de détecter et de consigner les tentatives d’accès aux sites web malveillants et indésirables sur Microsoft Edge uniquement.

## <a name="configure-web-threat-protection"></a>Configurer la protection contre les menaces web

La procédure suivante décrit comment configurer la protection contre les menaces web à l’aide du Centre d’administration Microsoft Endpoint Manager.

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.
 
2. Choisissez **La réduction de la surface d’attaque** de **sécurité** \> des points de terminaison, puis **choisissez + Créer une stratégie**.

3. Sélectionnez une plateforme, telle que **Windows 10 et versions ultérieures**, sélectionnez le profil de **protection web**, puis choisissez **Créer**. 

4. Sous l’onglet **Informations de base** , spécifiez un nom et une description, puis choisissez **Suivant**.

5. Sous l’onglet **Paramètres de configuration** , développez **protection web**, spécifiez vos paramètres, puis choisissez **Suivant**.

   - **Définissez Activer la protection réseau** sur **Activé** pour activer la protection web. Vous pouvez également définir la protection réseau en **mode Audit** pour voir comment elle fonctionnera dans votre environnement. En mode audit, la protection réseau n’empêche pas les utilisateurs de visiter des sites ou des domaines, mais elle effectue le suivi des détections en tant qu’événements. 
   - Pour protéger les utilisateurs contre les tentatives d’hameçonnage potentielles et les logiciels malveillants, **affectez à Require SmartScreen pour Version antérieure de Microsoft Edge** la valeur **Oui**.
   - Pour empêcher les utilisateurs de contourner les avertissements concernant les sites potentiellement malveillants, **définissez Bloquer l’accès aux sites malveillants** sur **Oui**.
   - Pour empêcher les utilisateurs de contourner les avertissements et de télécharger des fichiers non vérifiés, **définissez Bloquer le téléchargement de fichiers non vérifiés** sur **Oui**. 

6. Sous l’onglet **Balises d’étendue** , si votre organisation utilise des balises d’étendue, **choisissez + Sélectionner des balises d’étendue**, puis choisissez **Suivant**. (Si vous n’utilisez pas de balises d’étendue, choisissez **Suivant**.) Pour en savoir plus sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour le service informatique distribué](/mem/intune/fundamentals/scope-tags).

7. Sous l’onglet **Affectations** , spécifiez les utilisateurs et les appareils pour recevoir la stratégie de protection web, puis choisissez **Suivant**.

8. Sous l’onglet **Vérifier + créer** , passez en revue vos paramètres de stratégie, puis choisissez **Créer**.

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la protection web](web-protection-overview.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Surveiller la sécurité web](web-protection-monitoring.md)
- [Répondre aux menaces web](web-protection-response.md)
- [Protection du réseau](network-protection.md)
