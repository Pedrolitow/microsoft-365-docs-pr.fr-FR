---
title: Intégrer Microsoft Defender pour point de terminaison à d’autres solutions Microsoft
description: Découvrez comment Microsoft Defender pour point de terminaison s’intègre à d’autres solutions Microsoft, notamment Microsoft Defender pour Identity et Microsoft Defender pour cloud.
author: mjcaparas
ms.author: macapara
ms.service: microsoft-365-security
keywords: microsoft 365 defender, accès conditionnel, office, Microsoft Defender pour point de terminaison, microsoft defender pour l’identité, microsoft defender pour Office, Microsoft Defender pour le cloud, microsoft cloud app security, azure sentinel
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 62a822e64ef739c4d2e81103b5627d9f1259e712
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586245"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Microsoft Defender pour point de terminaison et d’autres solutions Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>Intégrer à d’autres solutions Microsoft

Microsoft Defender pour point de terminaison s’intègre directement à différentes solutions Microsoft.

### <a name="microsoft-defender-for-cloud"></a>Microsoft Defender pour le cloud

Microsoft Defender pour point de terminaison fournit une solution de protection de serveur complète, notamment des fonctionnalités de détection et de réponse des points de terminaison (EDR) sur les serveurs Windows.

### <a name="microsoft-sentinel"></a>Microsoft Sentinel

Le connecteur Microsoft Defender pour point de terminaison vous permet de diffuser en continu des alertes à partir de Microsoft Defender pour point de terminaison dans Microsoft Sentinel. Cela vous permet d’analyser plus en détails les événements de sécurité au sein de votre organisation et de créer des playbooks pour une réponse efficace et immédiate.

### <a name="azure-information-protection"></a>Azure Information Protection

Nous avons récemment déconseillé l’intégration d’Azure Information Protection, car nos fonctionnalités DLP de point de terminaison intègrent une solution de détection et de protection améliorée pour les données sensibles stockées sur les appareils de point de terminaison, ce qui facilite une meilleure visibilité et une meilleure intégration entre les solutions. Ceci a été annoncé dans le [blog](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protecting-sensitive-information-on-devices/ba-p/2143555) suivant. Nous recommandons aux clients de passer à l’utilisation de DLP de point de terminaison.

### <a name="conditional-access"></a>Accès conditionnel

Le score de risque d’appareil dynamique de Microsoft Defender pour point de terminaison est intégré à l’évaluation de l’accès conditionnel, ce qui garantit que seuls les appareils sécurisés ont accès aux ressources.

### <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps tire parti des signaux Microsoft Defender pour point de terminaison pour permettre une visibilité directe sur l’utilisation des applications cloud, y compris l’utilisation de services cloud non pris en charge (shadow IT) de tous les Microsoft Defender pour point de terminaison appareils surveillés.

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender pour l’identité

Les activités suspectes sont des processus s’exécutant dans un contexte utilisateur. L’intégration entre Microsoft Defender pour point de terminaison et Microsoft Defender pour Identity offre la flexibilité nécessaire pour mener des enquêtes sur la cybersécurité entre les activités et les identités.

### <a name="microsoft-defender-for-office"></a>Microsoft Defender pour Office

[Defender pour Office 365](/office365/securitycompliance/office-365-atp) permet de protéger votre organisation contre les programmes malveillants dans les messages électroniques ou les fichiers par le biais de liens sécurisés, de pièces jointes sécurisées, de fonctionnalités avancées d’anti-hameçonnage et d’usurpation d’identité. L’intégration entre Microsoft Defender pour Office 365 et Microsoft Defender pour point de terminaison permet aux analystes de sécurité d’aller en amont pour examiner le point d’entrée d’une attaque. Grâce au partage des informations sur les menaces, les attaques peuvent être contenues et bloquées.

> [!NOTE]
> Defender pour Office 365 données sont affichées pour les événements des 30 derniers jours. Pour les alertes, Defender pour Office 365 données sont affichées en fonction de la première heure d’activité. Après cela, les données ne sont plus disponibles dans Defender pour Office 365.

### <a name="skype-for-business"></a>Skype Entreprise

L’intégration Skype Entreprise permet aux analystes de communiquer avec un utilisateur ou un propriétaire d’appareil potentiellement compromis via un bouton simple à partir du portail.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender

Avec Microsoft 365 Defender, Microsoft Defender pour point de terminaison et diverses solutions de sécurité Microsoft forment une suite de défense d’entreprise unifiée avant et après violation qui s’intègre en mode natif entre les points de terminaison, les identités, les e-mails et les applications pour détecter, empêcher, examiner et répondre automatiquement aux problèmes sophistiqués Attaques.

[En savoir plus sur Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

## <a name="related-topics"></a>Voir aussi

- [Configurer l’intégration et d’autres fonctionnalités avancées](advanced-features.md)
- [vue d’ensemble de Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)
- [Activer Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable)
- [Protéger les utilisateurs, les données et les appareils avec l’accès conditionnel](conditional-access.md)
