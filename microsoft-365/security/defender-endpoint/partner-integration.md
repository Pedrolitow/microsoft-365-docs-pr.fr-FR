---
title: Microsoft Defender pour point de terminaison des opportunités et des scénarios de partenaires
ms.reviewer: ''
description: Découvrez comment étendre des offres de sécurité existantes en plus de l’infrastructure ouverte et d’un ensemble complet d’API pour créer des extensions et des intégrations avec Microsoft Defender pour point de terminaison
keywords: API, partenaire, extension, open framework, apis, extensions, intégrations, détection, gestion, réponse, vulnérabilités, intelligence
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
ms.openlocfilehash: 55cf82e64af6ac9397206e66754adfd125deb661
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586157"
---
# <a name="microsoft-defender-for-endpoint-partner-opportunities-and-scenarios"></a>Microsoft Defender pour point de terminaison des opportunités et des scénarios de partenaires

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Les partenaires peuvent facilement étendre leurs offres de sécurité existantes en plus de l’infrastructure ouverte et d’un ensemble complet d’API pour créer des extensions et des intégrations avec Defender pour point de terminaison. 

Les API couvrent des domaines fonctionnels, notamment la détection, la gestion, la réponse, les vulnérabilités et un large éventail de cas d’usage à l’échelle de l’intelligence. En fonction du cas d’utilisation et des besoins, les partenaires peuvent diffuser ou interroger des données à partir de Defender pour point de terminaison. 


## <a name="scenario-1-external-alert-correlation-and-automated-investigation-and-remediation"></a>Scénario 1 : Corrélation des alertes externes et investigation et correction automatisées
Defender pour point de terminaison offre des fonctionnalités d’investigation et de correction automatisées uniques pour générer une réponse aux incidents à grande échelle. 

L’intégration de la fonctionnalité d’investigation et de réponse automatisée à d’autres solutions, telles que les produits de sécurité réseau ou d’autres produits de sécurité de point de terminaison, vous aidera à résoudre les alertes. L’intégration réduit également la complexité liée à la corrélation du signal réseau et de l’appareil, ce qui simplifie efficacement les actions d’investigation et de correction des menaces sur les appareils.

Defender pour point de terminaison ajoute la prise en charge de ce scénario sous les formes suivantes :

- Les alertes externes peuvent être envoyées dans Defender pour point de terminaison et présentées côte à côte avec des alertes supplémentaires basées sur l’appareil de Defender pour point de terminaison. Cette vue fournit le contexte complet de l’alerte, avec le processus réel et l’histoire complète de l’attaque.

- Une fois qu’une alerte est générée, le signal est partagé entre tous les points de terminaison protégés par Defender pour point de terminaison dans l’entreprise. Defender pour point de terminaison prend immédiatement une réponse automatisée ou assistée par l’opérateur pour répondre à l’alerte.

## <a name="scenario-2-security-orchestration-and-automation-response-soar-integration"></a>Scénario 2 : Intégration de l’orchestration et de l’automatisation de la sécurité (SOAR)
Les solutions d’orchestration peuvent aider à créer des playbooks et à intégrer le modèle de données enrichi et les actions que les API Defender pour point de terminaison exposent pour orchestrer les réponses, telles que la requête de données d’appareil, déclencher l’isolation des appareils, bloquer/autoriser, résoudre les alertes, etc.

## <a name="scenario-3-indicators-matching"></a>Scénario 3 : Correspondance des indicateurs 
L’indicateur de compromission est une fonctionnalité essentielle dans chaque solution de protection des points de terminaison. Cette fonctionnalité est disponible dans Defender pour point de terminaison et permet de définir une liste d’indicateurs pour la prévention, la détection et l’exclusion des entités. Vous pouvez définir l’action à entreprendre ainsi que la durée d’application de l’action.

Les scénarios ci-dessus servent d’exemples d’extensibilité de la plateforme. Vous n’êtes pas limité aux exemples et nous vous encourageons certainement à tirer parti de l’infrastructure ouverte pour découvrir et explorer d’autres scénarios.

Suivez les étapes décrites dans [Devenir un partenaire Microsoft Defender pour point de terminaison](get-started-partner-integration.md) pour intégrer votre solution dans Defender pour point de terminaison.

## <a name="related-topic"></a>Rubrique connexe
- [Vue d’ensemble de la gestion et des API](management-apis.md)
