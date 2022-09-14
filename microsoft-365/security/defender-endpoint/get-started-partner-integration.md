---
title: Devenir un partenaire Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Découvrez les étapes et les exigences pour intégrer votre solution à Microsoft Defender pour point de terminaison et être partenaire
keywords: partenaire, intégration, validation de solution, certification, exigences, membre, misa, portail d’application
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: cef657818549e28375ea1ab44de815dc46f6da86
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67696042"
---
# <a name="become-a-microsoft-defender-for-endpoint-partner"></a>Devenir un partenaire Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Pour devenir un partenaire de solution Defender pour point de terminaison, vous devez suivre et effectuer les étapes suivantes.

## <a name="step-1-subscribe-to-a-microsoft-defender-for-endpoint-license"></a>Étape 1 : S’abonner à une licence Microsoft Defender pour point de terminaison

Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink) L’abonnement vous permet d’utiliser un locataire Microsoft Defender pour point de terminaison avec jusqu’à trois appareils pour développer des solutions qui s’intègrent à Microsoft Defender pour point de terminaison.

## <a name="step-2-fulfill-the-solution-validation-and-certification-requirements"></a>Étape 2 : Répondre aux exigences de validation et de certification de la solution

La meilleure façon pour les partenaires technologiques de certifier que leur intégration fonctionne consiste à demander à un client commun d’approuver la conception d’intégration suggérée (le client peut utiliser l’option \(**Recommander un partenaire** Partenaires et l’API > applications\) partenaires dans la page Application partenaire du Microsoft 365 Defender et la faire tester et rétrograder dans la [page Application](https://security.microsoft.com/interoperability/partnersapps) partenaire Microsoft Defender pour point de terminaison équipe.

Une fois que l’équipe Microsoft Defender pour point de terminaison a examiné et approuvé l’intégration, nous vous conseillons d’être inclus en tant que partenaire auprès de Microsoft Intelligent Security Association.

## <a name="step-3-get-listed-in-the-microsoft-defender-for-endpoint-partner-application-portal"></a>Étape 3 : Être répertorié dans le portail d’application du partenaire Microsoft Defender pour point de terminaison

Microsoft Defender pour point de terminaison prend en charge la découverte et l’intégration d’applications tierces à l’aide de la [page partenaire](partner-applications.md) intégrée au produit incorporée dans le portail de gestion Microsoft Defender pour point de terminaison.

Pour que votre entreprise soit répertoriée en tant que partenaire dans la page partenaire dans le produit, vous devez fournir les informations suivantes :

1. Logo carré (SVG).
2. Nom du produit à présenter.
3. Fournissez une description de produit de 15 mots.
4. Lien vers la page d’accueil pour que le client termine l’intégration ou le billet de blog qui inclut suffisamment d’informations pour les clients. Tous les communiqués de presse, y compris le nom du produit Microsoft Defender pour point de terminaison, doivent être examinés par les équipes de marketing et d’ingénierie. Attendez au moins 10 jours que le processus d’examen soit effectué.
5. Si vous utilisez une approche Azure AD mutualisée, nous aurons besoin du nom de l’application Azure AD pour suivre l’utilisation de l’application.
6. Incluez le champ User-Agent dans chaque appel d’API effectué pour Microsoft Defender pour point de terminaison ensemble public d’API ou d’API de sécurité Graph. Il sera utilisé à des fins statistiques, de dépannage et de reconnaissance des partenaires. En outre, cette étape est obligatoire pour l’appartenance à Microsoft Intelligent Security Association (MISA).

   Procédez comme suit :

   - Définissez le champ User-Agent dans chaque en-tête de requête HTTP au format ci-dessous.

     ```http
     MdePartner-{CompanyName}-{ProductName}/{Version}
     ```

     Par exemple, User-Agent :

     ```http
     MdePartner-Contoso-ContosoCognito/1.0.0
     ```

   - Pour plus d’informations, consultez [la section RFC 2616-14.43](https://tools.ietf.org/html/rfc2616#section-14.43).

Les partenariats avec Microsoft Defender pour point de terminaison aider nos clients mutuels à simplifier, intégrer et orchestrer davantage les défenses. Nous sommes heureux que vous avez choisi de devenir un partenaire Microsoft Defender pour point de terminaison et d’atteindre notre objectif commun de protéger efficacement les clients et leurs ressources en empêchant et en répondant aux menaces modernes ensemble.

## <a name="misa-nomination"></a>Mise en candidature MISA 
Les fournisseurs de services de sécurité managés (MSSP) et les éditeurs de logiciels indépendants (ISV) peuvent être nommés à la Microsoft Intelligent Security Association (MISA). Pour plus d’informations, consultez la [page d’informations MISA](https://www.microsoft.com/security/business/intelligent-security-association).


## <a name="related-topics"></a>Voir aussi

- [Opportunités de partenariat technique](partner-integration.md)
