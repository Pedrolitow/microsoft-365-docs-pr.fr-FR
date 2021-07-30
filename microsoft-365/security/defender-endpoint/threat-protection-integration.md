---
title: Intégrer Microsoft Defender for Endpoint à d’autres solutions Microsoft
description: Découvrez comment Microsoft Defender pour endpoint s’intègre à d’autres solutions Microsoft, notamment Microsoft Defender pour l’identité et Azure Defender.
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender, accès conditionnel, office, Microsoft Defender pour le point de terminaison, microsoft defender pour l’identité, microsoft defender pour office, Azure Defender, microsoft cloud app security, azure sentinel
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
ms.openlocfilehash: a5bd08de8e685dc30908647b6d2a0544309b074e
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53649106"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Microsoft Defender pour le point de terminaison et d’autres solutions Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>Intégration à d’autres solutions Microsoft

Microsoft Defender pour point de terminaison s’intègre directement à différentes solutions Microsoft.

### <a name="azure-defender"></a>Azure Defender
Microsoft Defender pour le point de terminaison fournit une solution de protection serveur complète, notamment des fonctionnalités protection évolutive des points de terminaison (PEPT) sur Windows serveurs.

### <a name="azure-sentinel"></a>Azure Sentinel
Le connecteur Microsoft Defender pour point de terminaison vous permet de diffuser des alertes de Microsoft Defender pour Endpoint dans Azure Sentinel. Cela vous permettra d’analyser plus en détail les événements de sécurité au sein de votre organisation et de créer des manuels pour obtenir une réponse efficace et immédiate.

### <a name="azure-information-protection"></a>Azure Information Protection
Nous avons récemment supprimé l’intégration Azure Information Protection, car nos fonctionnalités DLP de point de terminaison intègrent une solution de découverte et de protection améliorée pour les données sensibles stockées sur les appareils de point de terminaison, ce qui facilite la visibilité et l’intégration entre les solutions. Cela a été annoncé dans le [blog suivant.](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protecting-sensitive-information-on-devices/ba-p/2143555) Nous recommandons aux clients de passer à l’utilisation du point de terminaison DLP.

### <a name="conditional-access"></a>Accès conditionnel
Le score de risque de l’appareil dynamique de Microsoft Defender pour le point de terminaison est intégré à l’évaluation de l’accès conditionnel, garantissant que seuls les appareils sécurisés ont accès aux ressources. 

### <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security
Microsoft Cloud App Security utilise les signaux de point de terminaison Microsoft Defender pour les points de terminaison pour permettre une visibilité directe de l’utilisation des applications cloud, y compris l’utilisation de services cloud non pris en compte (shadow IT) de tous les appareils surveillés par Microsoft Defender pour Endpoint.

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender pour l’identité
Les activités suspectes sont des processus en cours d’exécution dans un contexte utilisateur. L’intégration entre Microsoft Defender pour point de terminaison et Microsoft Defender pour l’identité offre la flexibilité nécessaire pour mener des enquêtes sur la cybersécurité entre les activités et les identités.

### <a name="microsoft-defender-for-office"></a>Microsoft Defender pour Office
[Defender for Office 365](/office365/securitycompliance/office-365-atp) permet de protéger votre organisation contre les programmes malveillants dans les messages électroniques ou les fichiers par le biais de liens Coffre, de pièces jointes Coffre, d’anti-hameçonnage avancé et de fonctionnalités d’intelligence contre l’usurpation d’informations. L’intégration entre Microsoft Defender pour Office 365 et Microsoft Defender pour le point de terminaison permet aux analystes de sécurité de monter en amont pour examiner le point d’entrée d’une attaque. Grâce au partage des renseignements sur les menaces, les attaques peuvent être contenues et bloquées. 

>[!NOTE]
> Defender pour Office 365 données est affiché pour les événements des 30 derniers jours. Pour les alertes, defender pour Office 365 données s’affiche en fonction de la première activité. Ensuite, les données ne sont plus disponibles dans Defender pour les Office 365.

### <a name="skype-for-business"></a>Skype Entreprise
L’intégration Skype Entreprise’analyse permet aux analystes de communiquer avec un utilisateur ou un propriétaire d’appareil potentiellement compromis par le biais d’un bouton simple à partir du portail.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender
Avec Microsoft 365 Defender, Microsoft Defender pour point de terminaison et diverses solutions de sécurité Microsoft forment une suite de défense d’entreprise unifiée avant et après la violation qui s’intègre en mode natif à travers le point de terminaison, l’identité, la messagerie électronique et les applications pour détecter, empêcher, examiner et répondre automatiquement aux attaques sophistiquées. 
 
[En savoir plus sur Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)


## <a name="related-topics"></a>Voir aussi
- [Configurer l’intégration et d’autres fonctionnalités avancées](advanced-features.md)
- [Microsoft 365 Defender vue d’ensemble](/microsoft-365/security/defender/microsoft-threat-protection)
- [Activer Microsoft 365 Defender](/microsoft-365/security/defender/mtp-enable)
- [Protéger les utilisateurs, les données et les appareils avec l’accès conditionnel](conditional-access.md)
