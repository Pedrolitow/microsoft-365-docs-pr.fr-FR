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
ms.openlocfilehash: d309f8851720578dfdd321efff862f15afd9bca8
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59183248"
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

## <a name="prerequisites"></a>Configuration requise

La protection web utilise la protection réseau pour assurer la sécurité de la navigation web sur Microsoft Edge navigateurs web tiers.

Pour activer la protection réseau sur vos appareils :

- Modifiez la ligne de base de sécurité Defender for Endpoint sous **Web & Network Protection** pour activer la protection réseau avant de la déployer ou de la redéployer. [En savoir plus sur l’examen et l’affectation de la ligne de base de sécurité defender pour point de terminaison](configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline)
- Activer la protection réseau sur l’utilisation de la configuration de l’appareil Intune, de SCCM, de la stratégie de groupe ou de votre solution MDM. [En savoir plus sur l’activation de la protection réseau](enable-network-protection.md)

> [!NOTE]
> Si vous définissez la protection réseau sur **Audit uniquement,** le blocage sera indisponible. En outre, vous pourrez détecter et enregistrer les tentatives d’accès à des sites web malveillants et indésirables Microsoft Edge uniquement.

## <a name="configure-web-threat-protection"></a>Configurer la protection contre les menaces web

La procédure suivante décrit comment configurer la protection contre les menaces web à l’aide Microsoft Endpoint Manager centre d’administration.

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ), and sign in.
 
2. Choisissez **Réduction de la**  >  **surface d’attaque** du point de terminaison de sécurité, puis choisissez + Créer une **stratégie.**

3. Sélectionnez une plateforme, telle que **Windows 10 et ultérieures,** sélectionnez le profil **de protection Web,** puis choisissez **Créer.** 

4. Sous **l’onglet Éléments de** base, spécifiez un nom et une description, puis choisissez **Suivant**.

5. Sous **l’onglet Paramètres de configuration,** **développez Protection Web,** spécifiez vos paramètres, puis choisissez **Suivant**.

   - Définissez **Activer la protection réseau** sur Activé **afin** que la protection web soit activée. Vous pouvez également définir la protection réseau en **mode Audit** pour voir comment elle fonctionne dans votre environnement. En mode audit, la protection réseau n’empêche pas les utilisateurs de visiter des sites ou des domaines, mais elle fait le suivi des détections en tant qu’événements. 
   - Pour protéger les utilisateurs contre les tentatives d’hameçonnage et les logiciels malveillants potentiels, **Version antérieure de Microsoft Edge à** **Oui.**
   - Pour empêcher les utilisateurs de contourner les avertissements concernant les sites potentiellement malveillants, définissez l’accès au **site malveillant** sur **Oui.**
   - Pour empêcher les utilisateurs de contourner les avertissements et de télécharger des fichiers non vérifiées, définissez Bloquer le téléchargement de fichier non vérifiée **tl** **Oui**. 

6. Sous **l’onglet Balises** d’étendue, si votre organisation utilise des balises d’étendue, choisissez **+** Sélectionner des balises d’étendue, puis choisissez **Suivant**. (Si vous n’utilisez pas de balises d’étendue, choisissez **Suivant.)** Pour en savoir plus sur les balises d’étendue, voir Utiliser un contrôle d’accès basé sur un rôle [(RBAC)](/mem/intune/fundamentals/scope-tags)et des balises d’étendue pour le service it distribué.

7. Sous **l’onglet Affectations,** spécifiez les utilisateurs et les appareils pour recevoir la stratégie de protection web, puis choisissez **Suivant**.

8. Sous **l’onglet Révision + créer,** examinez vos paramètres de stratégie, puis choisissez **Créer.**

## <a name="related-topics"></a>Rubriques connexes

- [Vue d’ensemble de la protection web](web-protection-overview.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Surveiller la sécurité web](web-protection-monitoring.md)
- [Répondre aux menaces web](web-protection-response.md)
- [Protection du réseau](network-protection.md)
