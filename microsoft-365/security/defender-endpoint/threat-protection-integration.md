---
title: Intégrer Microsoft Defender for Endpoint à d’autres solutions Microsoft
description: Découvrez comment Microsoft Defender pour endpoint s’intègre à d’autres solutions Microsoft, notamment Microsoft Defender pour l’identité et Azure Security Center.
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender, accès conditionnel, Office, protection avancée contre les menaces, microsoft defender pour l’identité, microsoft defender pour office, centre de sécurité Azure, sécurité des applications cloud microsoft, azure sentinel
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 287ad9adeccd527b756bdd5304d3c89fc1b2d789
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51068454"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Microsoft Defender pour le point de terminaison et d’autres solutions Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>Intégration à d’autres solutions Microsoft

Microsoft Defender pour le point de terminaison s’intègre directement à différentes solutions Microsoft.

### <a name="azure-security-center"></a>Centre de sécurité Azure
Microsoft Defender pour le point de terminaison fournit une solution de protection serveur complète, y compris les fonctionnalités de détection et de réponse des points de terminaison (EDR) sur les serveurs Windows.

### <a name="azure-sentinel"></a>Azure Sentinel
Le connecteur Microsoft Defender pour point de terminaison vous permet de diffuser des alertes de Microsoft Defender pour Endpoint dans Azure Sentinel. Cela vous permettra d’analyser plus en détail les événements de sécurité au sein de votre organisation et de créer des manuels pour obtenir une réponse efficace et immédiate.

### <a name="azure-information-protection"></a>Azure Information Protection
Sécurisation des données sensibles tout en permettant la productivité sur le lieu de travail par le biais de la découverte et de la protection des données.

### <a name="conditional-access"></a>Accès conditionnel
Le score de risque de l’appareil dynamique de Microsoft Defender pour le point de terminaison est intégré à l’évaluation de l’accès conditionnel, garantissant que seuls les appareils sécurisés ont accès aux ressources. 

### <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security
Microsoft Cloud App Security tire parti des signaux de point de terminaison Microsoft Defender pour les points de terminaison pour permettre une visibilité directe de l’utilisation des applications cloud, y compris l’utilisation de services cloud non pris en compte (shadow IT) de tous les appareils Surveillés par Microsoft Defender pour Endpoint.

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender pour Identity
Les activités suspectes sont des processus en cours d’exécution dans un contexte utilisateur. L’intégration entre Microsoft Defender pour point de terminaison et Azure ATP offre la flexibilité nécessaire pour mener des enquêtes sur la cybersécurité entre les activités et les identités.

### <a name="microsoft-defender-for-office"></a>Microsoft Defender pour Office
[Defender pour Office 365](https://docs.microsoft.com/office365/securitycompliance/office-365-atp) permet de protéger votre organisation contre les programmes malveillants dans les messages électroniques ou les fichiers par le biais de liens sécurisés ATP, de pièces jointes sécurisées ATP, d’anti-hameçonnage avancé et de fonctionnalités d’intelligence contre l’usurpation d’adresses. L’intégration entre Office 365 ATP et Microsoft Defender for Endpoint permet aux analystes de sécurité de monter en amont pour examiner le point d’entrée d’une attaque. Grâce au partage des renseignements sur les menaces, les attaques peuvent être contenues et bloquées. 

>[!NOTE]
> Les données Defender pour Office 365 sont affichées pour les événements des 30 derniers jours. Pour les alertes, les données De Defender pour Office 365 sont affichées en fonction de la première activité. Ensuite, les données ne sont plus disponibles dans Defender pour Office 365.

### <a name="skype-for-business"></a>Skype Entreprise
L’intégration de Skype Entreprise permet aux analystes de communiquer avec un utilisateur ou un propriétaire d’appareil potentiellement compromis via un bouton simple à partir du portail.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender
Avec Microsoft 365 Defender, Microsoft Defender pour point de terminaison et diverses solutions de sécurité Microsoft constituent une suite de défense d’entreprise unifiée avant et après la violation qui s’intègre en mode natif à travers les points de terminaison, l’identité, la messagerie et les applications pour détecter, empêcher, examiner et répondre automatiquement aux attaques sophistiquées. 
 
[En savoir plus sur Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection)


## <a name="related-topics"></a>Voir aussi
- [Configurer l’intégration et d’autres fonctionnalités avancées](advanced-features.md)
- [Vue d’ensemble de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection)
- [Activer Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/defender/mtp-enable)
- [Protéger les utilisateurs, les données et les appareils avec l’accès conditionnel](conditional-access.md)