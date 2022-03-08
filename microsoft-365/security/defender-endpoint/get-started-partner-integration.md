---
title: Devenir un partenaire Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Découvrez les étapes et les conditions requises pour intégrer votre solution à Microsoft Defender pour Endpoint et être partenaire
keywords: partenaire, intégration, validation de solution, certification, exigences, membre, misa, portail d’applications
ms.prod: w10
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
ms.openlocfilehash: b063d8435817d7dd64c3febf6e3399f3876ef894
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319824"
---
# <a name="become-a-microsoft-defender-for-endpoint-partner"></a>Devenir un partenaire Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Pour devenir un partenaire de solution Defender pour Endpoint, vous devez suivre et effectuer les étapes suivantes.

## <a name="step-1-subscribe-to-a-microsoft-defender-for-endpoint-license"></a>Étape 1 : s’abonner à une licence Microsoft Defender pour point de terminaison

Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink). L’abonnement vous permet d’utiliser un client Microsoft Defender pour Endpoint avec jusqu’à trois appareils pour développer des solutions qui s’intègrent à Microsoft Defender pour Endpoint.

## <a name="step-2-fulfill-the-solution-validation-and-certification-requirements"></a>Étape 2 : répondre aux exigences de validation et de certification de la solution

La meilleure façon pour les partenaires technologiques de certifier que leur intégration fonctionne consiste à faire en sorte qu’un client commun approuve la conception d’intégration suggérée (le client peut utiliser **l’option** \(Partenaire recommandée et API > Applications\) partenaires dans la [page Application](https://security.microsoft.com/interoperability/partnersapps) partenaire du Microsoft 365 Defender et le faire tester et le faire rétrograder à l’équipe Microsoft Defender pour point de terminaison.

Une fois que l’équipe Microsoft Defender pour le point de terminaison a examiné et approuvé l’intégration, nous vous dirigeons vers l’intégration en tant que partenaire auprès de l’Association de sécurité intelligente de Microsoft.

## <a name="step-3-get-listed-in-the-microsoft-defender-for-endpoint-partner-application-portal"></a>Étape 3 : Obtenir une liste dans le portail d’application partenaire Microsoft Defender pour Endpoint

Microsoft Defender pour le point de terminaison prend en charge la découverte et l’intégration d’applications tierces à l’aide de la [page](partner-applications.md) partenaire intégrée au produit incorporée dans le portail de gestion microsoft Defender pour les points de terminaison.

Pour que votre société soit répertoriée en tant que partenaire dans la page partenaire du produit, vous devez fournir les informations suivantes :

1. Logo carré (SVG).
2. Nom du produit à présenter.
3. Fournissez une description de produit de 15 mots.
4. Lien vers la page d’accueil pour que le client termine l’intégration ou le billet de blog qui inclut des informations suffisantes pour les clients. Tout communiqué de presse, y compris le nom du produit Microsoft Defender for Endpoint, doit être examiné par les équipes marketing et d’ingénierie. Attendez au moins 10 jours que le processus de révision soit terminé.
5. Si vous utilisez une approche Azure AD client multiple, nous avons besoin du nom Azure AD’application pour suivre l’utilisation de l’application.
6. Incluez le User-Agent dans chaque appel d’API effectué à Microsoft Defender pour l’ensemble public d’API ou d’API Graph Endpoint. Il sera utilisé à des fins statistiques, de dépannage et de reconnaissance des partenaires. En outre, cette étape est requise pour l’appartenance à Microsoft Intelligent Security Association (MISA).

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

## <a name="misa-nomination"></a>MISA dossier 
Les fournisseurs de services de sécurité gérés (MSSP) et les éditeurs de logiciels indépendants peuvent être désignés comme membres de l’Intelligent Security Association (MISA) de Microsoft. Pour plus d’informations, consultez la [page d’informations misa](https://www.microsoft.com/security/business/intelligent-security-association).


## <a name="related-topics"></a>Voir aussi

- [Opportunités de partenariat technique](partner-integration.md)
