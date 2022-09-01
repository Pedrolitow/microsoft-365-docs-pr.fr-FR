---
title: Vue d’ensemble de la gestion et des API
ms.reviewer: ''
description: En savoir plus sur les outils de gestion et les catégories d’API dans Microsoft Defender pour point de terminaison
keywords: intégration, api, siem, rbac, access, portail, intégration, investigation, réponse, entités, entité, contexte utilisateur, contexte d’application, streaming
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
ms.custom: api
ms.openlocfilehash: 212a21accc314cc9ff235138eeb2784521a32502
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67516497"
---
# <a name="overview-of-management-and-apis"></a>Vue d’ensemble de la gestion et des API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mgt-apis-abovefoldlink)


Defender pour point de terminaison prend en charge un large éventail d’options pour garantir que les clients peuvent facilement adopter la plateforme.

Reconnaissant que les environnements et les structures des clients peuvent varier, Defender pour point de terminaison a été créé avec flexibilité et un contrôle granulaire pour répondre à différentes exigences des clients.

## <a name="endpoint-onboarding-and-portal-access"></a>Intégration des points de terminaison et accès au portail

L’intégration des appareils est entièrement intégrée à Microsoft Endpoint Manager et Microsoft Intune pour les appareils clients et Microsoft Defender pour les appareils serveur, offrant une expérience complète de bout en bout de la configuration, du déploiement et de la surveillance. En outre, Microsoft Defender pour point de terminaison prend en charge stratégie de groupe et d’autres outils tiers utilisés pour la gestion des appareils.

Defender pour point de terminaison offre un contrôle précis sur ce que les utilisateurs ayant accès au portail peuvent voir et faire grâce à la flexibilité du contrôle d’accès en fonction du rôle (RBAC). Le modèle RBAC prend en charge toutes les versions de la structure des équipes de sécurité :

- Organisations et équipes de sécurité mondialement distribuées
- Équipes d’opérations de sécurité de modèle hiérarchisation
- Divisions entièrement séparées avec des équipes d’opérations de sécurité globale centralisées uniques

## <a name="available-apis"></a>API disponibles

La solution Microsoft Defender pour point de terminaison repose sur une plateforme prête pour l’intégration.

Defender pour point de terminaison expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous permettront d’automatiser les flux de travail et d’innover en fonction des fonctionnalités de Defender pour point de terminaison.

:::image type="content" source="images/mdatp-apis.png" alt-text="API et intégration disponibles dans Microsoft Defender pour point de terminaison" lightbox="images/mdatp-apis.png":::

Les API Defender pour point de terminaison peuvent être regroupées en trois :

- API Microsoft Defender pour point de terminaison
- API de diffusion en continu de données brutes
- Intégration SIEM

## <a name="microsoft-defender-for-endpoint-apis"></a>API Microsoft Defender pour point de terminaison

Defender pour point de terminaison offre un modèle d’API en couches exposant des données et des fonctionnalités dans un modèle structuré, clair et facile à utiliser, exposé via un modèle d’authentification et d’autorisation Azure AD standard autorisant l’accès dans le contexte des utilisateurs ou des applications SaaS. Le modèle d’API a été conçu pour exposer des entités et des fonctionnalités sous une forme cohérente.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide des API de Defender pour point de terminaison.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

**L’API Investigation** expose la richesse de Defender pour point de terminaison , en exposant des entités calculées ou « profilées » (par exemple, un appareil, un utilisateur et un fichier) et des événements discrets (par exemple, la création de processus et de fichiers) qui décrit généralement un comportement lié à une entité, ce qui permet d’accéder aux données via des interfaces d’investigation permettant un accès basé sur une requête aux données. Pour plus d’informations, consultez [API prises en charge](exposed-apis-list.md).

**L’API Response** expose la possibilité d’effectuer des actions dans le service et sur les appareils, ce qui permet aux clients d’ingérer des indicateurs, de gérer les paramètres, l’état des alertes, ainsi que d’effectuer des actions de réponse sur les appareils par programmation, comme isoler les appareils du réseau, mettre en quarantaine des fichiers, etc.

## <a name="raw-data-streaming-api"></a>API de diffusion en continu de données brutes

L’API de streaming de données brutes Defender pour point de terminaison permet aux clients d’envoyer des événements et des alertes en temps réel à partir de leurs instances lorsqu’ils se produisent dans un flux de données unique, ce qui fournit un mécanisme de livraison à faible latence et à débit élevé.

Les informations sur les événements Defender pour point de terminaison sont envoyées directement au stockage Azure pour la conservation des données à long terme, ou pour Azure Event Hubs à la consommation par des services de visualisation ou des moteurs de traitement de données supplémentaires.

Pour plus d’informations, consultez [l’API de streaming de données brutes](raw-data-export.md).

La nouvelle API de diffusion en continu Microsoft 365 Defender inclut des événements d’e-mail et d’alerte en plus des événements de l’appareil.
Pour plus d’informations, consultez [Microsoft 365 Defender API de streaming](../defender/streaming-api.md).

## <a name="siem-api"></a>SIEM API

Lorsque vous activez l’intégration des informations de sécurité et de la gestion des événements (SIEM), elle vous permet d’extraire des détections de Microsoft 365 Defender à l’aide de votre solution SIEM ou en vous connectant directement à l’API REST des détections. Cela active la section détails d’accès du connecteur SIEM avec des valeurs préremplies et une application est créée sous votre locataire Azure Active Directory (Azure AD). 

## <a name="related-topics"></a>Voir aussi

- [Accéder aux API Microsoft Defender pour point de terminaison](apis-intro.md)
- [API prises en charge](exposed-apis-list.md)
- [Opportunités de partenariat technique](partner-integration.md)
