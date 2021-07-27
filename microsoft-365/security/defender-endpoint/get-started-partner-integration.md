---
title: Devenir un partenaire Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Découvrez les étapes et les conditions requises pour intégrer votre solution à Microsoft Defender pour Endpoint et être partenaire
keywords: partenaire, intégration, validation de solution, certification, exigences, membre, misa, portail d’applications
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.openlocfilehash: 10482cf13784234d0a73b761f2d06e4a72c6802a
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53542692"
---
# <a name="become-a-microsoft-defender-for-endpoint-partner"></a>Devenir un partenaire Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pour devenir un partenaire de solution Defender pour Endpoint, vous devez suivre et effectuer les étapes suivantes.

## <a name="step-1-subscribe-to-a-microsoft-defender-for-endpoint-developer-license"></a>Étape 1 : s’abonner à une licence Microsoft Defender pour les développeurs de points de terminaison

Abonnez-vous [à la licence Microsoft Defender for Endpoint Developer](https://winatpregistration-prd.trafficmanager.net/Developer/UserAgreement?Length=9). L’abonnement vous permet d’utiliser un client Microsoft Defender pour Endpoint avec jusqu’à 10 appareils pour développer des solutions qui s’intègrent à Microsoft Defender pour Endpoint.

## <a name="step-2-fulfill-the-solution-validation-and-certification-requirements"></a>Étape 2 : répondre aux exigences de validation et de certification de la solution

La meilleure façon pour les partenaires technologiques de certifier que leur intégration fonctionne consiste  à faire en sorte qu’un client commun approuve la conception d’intégration suggérée (le client peut utiliser l’option Recommander un partenaire dans la [page](https://securitycenter.microsoft.com/interoperability/partners) Application partenaire de l’Centre de sécurité Microsoft Defender) et faire en sorte qu’elle soit testée et rétrogradée à l’équipe Microsoft Defender pour le point de terminaison.

Une fois que l’équipe Microsoft Defender pour le point de terminaison a examiné et approuvé l’intégration, nous vous dirigeons vers l’intégration en tant que partenaire auprès de l’Association de sécurité intelligente de Microsoft.

## <a name="step-3-become-a--microsoft-intelligent-security-association-member"></a>Étape 3 : devenir membre de l’Association de sécurité intelligente Microsoft

[Microsoft Intelligent Security Association](https://www.microsoft.com/security/partnerships/intelligent-security-association) est un programme spécifiquement conçu pour les partenaires de sécurité Microsoft afin d’enrichir vos produits de sécurité et d’améliorer la découverte par les clients de vos intégrations aux produits de sécurité Microsoft.

## <a name="step-4-get-listed-in-the-microsoft-defender-for-endpoint-partner-application-portal"></a>Étape 4 : Obtenir une liste dans le portail d’application partenaire Microsoft Defender pour Endpoint

Microsoft Defender pour le point de terminaison prend en charge la découverte et l’intégration d’applications tierces à l’aide de la [page](partner-applications.md) partenaire intégrée au produit incorporée dans le portail de gestion microsoft Defender pour les points de terminaison.

Pour que votre société soit répertoriée en tant que partenaire dans la page partenaire du produit, vous devez fournir les informations suivantes :

1. Logo carré (SVG).
2. Nom du produit à présenter.
3. Fournissez une description de produit de 15 mots.
4. Lien vers la page d’accueil pour que le client termine l’intégration ou le billet de blog qui inclut des informations suffisantes pour les clients. Tout communiqué de presse, y compris le nom du produit Microsoft Defender for Endpoint, doit être examiné par les équipes marketing et d’ingénierie. Attendez au moins 10 jours que le processus de révision soit terminé.
5. Si vous utilisez une approche Azure AD multi-locataire, nous avons besoin du nom de l’application Azure AD pour suivre l’utilisation de l’application.
6. Incluez le User-Agent dans chaque appel d’API effectué à Microsoft Defender pour l’ensemble public d’API ou d’API de sécurité Graph Endpoint. Il sera utilisé à des fins statistiques, de dépannage et de reconnaissance des partenaires. En outre, cette étape est requise pour l’appartenance à Microsoft Intelligent Security Association (MISA).

   Procédez comme suit :

   - Définissez le User-Agent dans chaque en-tête de requête HTTP au format ci-dessous.

     ```http
     MdePartner-{CompanyName}-{ProductName}/{Version}
     ```

     Par exemple, Agent utilisateur :

     ```http
     MdePartner-Contoso-ContosoCognito/1.0.0
     ```

   - Pour plus d’informations, [voir la section RFC 2616-14.43](https://tools.ietf.org/html/rfc2616#section-14.43).

Les partenariats avec Microsoft Defender pour point de terminaison aident nos clients mutuels à rationaliser, intégrer et orchestrer davantage les défenses. Nous sommes heureux que vous choisissiez de devenir un partenaire Microsoft Defender pour Points de terminaison et d’atteindre notre objectif commun de protéger efficacement les clients et leurs biens en empêchant les menaces modernes et en y répondant ensemble.

## <a name="related-topics"></a>Voir aussi

- [Opportunités de partenariat technique](partner-integration.md)
