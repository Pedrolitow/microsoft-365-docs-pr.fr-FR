---
title: Passer en revue les exigences en matière d’architecture et la structure de Microsoft Defender pour les applications cloud
description: Les diagrammes techniques de Microsoft Defender pour les applications cloud expliquent l’architecture de Microsoft 365 Defender, ce qui vous aidera à créer un environnement pilote.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6547c1b269ede9385b384ca18fe6f2ca34d35109
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500318"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-cloud-apps"></a>Passer en revue les exigences en matière d’architecture et les concepts clés de Microsoft Defender pour les applications cloud


**S’applique à :**

- Microsoft 365 Defender

Cet article est [l’étape 1 sur 3](eval-defender-mcas-overview.md) dans le processus de configuration de l’environnement d’évaluation de Microsoft Defender pour les applications cloud avec Microsoft 365 Defender. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-identity-overview.md).

Avant d’activer Microsoft Defender pour les applications cloud, veillez à bien comprendre l’architecture et à répondre aux exigences. 

## <a name="understand-the-architecture"></a>Comprendre l’architecture

Microsoft Defender pour les applications cloud est un courtier de sécurité d’accès au cloud (CASB). Les CSB agissent comme un garde d’accès pour négocier l’accès en temps réel entre les utilisateurs de votre entreprise et les ressources cloud qu’ils utilisent, où que soient vos utilisateurs et quel que soit l’appareil qu’ils utilisent. Microsoft Defender pour les applications cloud s’intègre en natif aux fonctionnalités de sécurité Microsoft, notamment Microsoft 365 Defender.

Sans Defender pour les applications cloud, les applications cloud utilisées par votre organisation ne sont pas gestion et ne sont pas protégées, comme illustré.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-a.png" alt-text="Architecture de Microsoft Defender pour les applications cloud" lightbox="../../media/defender/m365-defender-mcas-architecture-a.png":::

Dans cette illustration :
- L’utilisation d’applications cloud par une organisation n’est pas surveillée et non protégée. 
- Cette utilisation est en dehors des protections obtenues au sein d’une organisation gérée. 

#### <a name="discovering-cloud-apps"></a>Découverte des applications cloud

La première étape de gestion de l’utilisation des applications cloud consiste à découvrir les applications cloud utilisées par votre organisation. Le diagramme suivant illustre le fonctionnement de la découverte cloud avec Defender pour les applications cloud.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-b.png" alt-text="Architecture de Microsoft Defender pour les applications cloud dans la découverte cloud" lightbox="../../media/defender/m365-defender-mcas-architecture-b.png":::


Dans cette illustration, deux méthodes peuvent être utilisées pour surveiller le trafic réseau et découvrir les applications cloud utilisées par votre organisation.
- R. Cloud App Discovery s’intègre à Microsoft Defender pour Endpoint en natif. Defender for Endpoint signale que les applications et services cloud sont accessibles à partir des appareils gérés Windows 10 et Windows 11 informatiques. 
- B. Pour une couverture sur tous les appareils connectés à un réseau, le collecteur de journaux Defender for Cloud Apps est installé sur les pare-feux et autres proxies pour collecter des données à partir des points de terminaison. Ces données sont envoyées à Defender pour les applications cloud pour analyse.

#### <a name="managing-cloud-apps"></a>Gestion des applications cloud

Après avoir découvert les applications cloud et analysé la façon dont ces applications sont utilisées par votre organisation, vous pouvez commencer à gérer les applications cloud de votre choix. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-c.png" alt-text="Architecture de Microsoft Defender pour les applications cloud lors de la gestion des applications cloud" lightbox="../../media/defender/m365-defender-mcas-architecture-c.png":::

Dans cette illustration :
- Certaines applications sont sanctionn es pour une utilisation. Cette sanction est un moyen simple de commencer à gérer les applications.
- Vous pouvez accroître la visibilité et le contrôle en connectant des applications avec des connecteurs d’application. Les connecteurs d’application utilisent les API des fournisseurs d’applications.


#### <a name="applying-session-controls-to-cloud-apps"></a>Application de contrôles de session aux applications cloud

Microsoft Defender pour les applications cloud sert de proxy inverse, fournissant un accès proxy aux applications cloud sanctionnées. Cette configuration permet à Defender for Cloud Apps d’appliquer les contrôles de session que vous configurez. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-d.png" alt-text="Architecture de Microsoft Defender pour les applications cloud : contrôle de session d’accès proxy" lightbox="../../media/defender/m365-defender-mcas-architecture-d.png":::

Dans cette illustration :
- L’accès aux applications cloud prises en compte par les utilisateurs et les appareils de votre organisation est acheminé via Defender pour les applications cloud.
- Cet accès proxy permet d’appliquer des contrôles de session.
- Les applications cloud que vous n’avez pas sanctionn es ou explicitement non affectées ne sont pas affectées.

Les contrôles de session vous permettent d’appliquer des paramètres à la façon dont les applications cloud sont utilisées par votre organisation. Par exemple, si votre organisation utilise Salesforce, vous pouvez configurer une stratégie de session qui permet uniquement aux appareils gérés d’accéder aux données de votre organisation via Salesforce. Un exemple plus simple peut être la configuration d’une stratégie pour surveiller le trafic provenant d’appareils non utilisés afin que vous pouvez analyser les risques de ce trafic avant d’appliquer des stratégies plus strictes.

#### <a name="integrating-with-azure-ad-with-conditional-access-app-control"></a>Intégration à Azure AD avec le contrôle d’application d’accès conditionnel

Il se peut que des applications SaaS soient déjà ajoutées à votre client Azure AD pour appliquer l’authentification multifacteur et d’autres stratégies d’accès conditionnel. Microsoft Defender pour les applications cloud s’intègre en natif à Azure AD. Il vous s agit de configurer une stratégie dans Azure AD utiliser le contrôle d’application d’accès conditionnel dans Defender pour les applications cloud. Cela a pour effet d’approvisionnement du trafic réseau pour ces applications SaaS gérées via Defender pour les applications cloud en tant que proxy, ce qui permet à Defender for Cloud Apps de surveiller ce trafic et d’appliquer des contrôles de session. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-e.png" alt-text="Architecture de Microsoft Defender pour les applications Cloud - Applications SaaS" lightbox="../../media/defender/m365-defender-mcas-architecture-e.png":::

Dans cette illustration :
- Les applications SaaS sont intégrées au client Azure AD client. Cette intégration permet aux Azure AD d’appliquer des stratégies d’accès conditionnel, notamment l’authentification multifacteur.
- Une stratégie est ajoutée à Azure Active Directory pour diriger le trafic des applications SaaS vers Defender pour les applications cloud. La stratégie spécifie les applications SaaS à appliquer à cette stratégie. Par conséquent, une fois Azure AD les stratégies d’accès conditionnel qui s’appliquent à ces applications SaaS, Azure AD dirige ensuite (par proxies) le trafic de session via Defender pour les applications Cloud.
- Defender pour les applications cloud surveille ce trafic et applique toutes les stratégies de contrôle de session qui ont été configurées par les administrateurs. 

Vous avez peut-être découvert et sanctioné des applications cloud à l’aide de Defender pour les applications cloud qui n’ont pas été ajoutées à Azure AD. Vous pouvez tirer parti du contrôle d’application d’accès conditionnel en ajoutant ces applications cloud à votre client Azure AD et l’étendue de vos règles d’accès conditionnel.

#### <a name="protecting-your-organization-from-hackers"></a>Protection de votre organisation contre les pirates informatiques

Defender pour les applications cloud offre une protection puissante. Toutefois, lorsqu’il est combiné avec les autres fonctionnalités de Microsoft 365 Defender, Defender pour les applications cloud fournit des données dans les signaux partagés qui contribuent (ensemble) à arrêter les attaques.

Il est utile de répéter cette illustration de la vue d’ensemble à cette Microsoft 365 Defender’évaluation et au guide pilote. 

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="Comment Microsoft 365 Defender arrêter une chaîne de menaces" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

En se concentrant sur le côté droit de cette illustration, Microsoft Defender pour les applications cloud remarque un comportement anormal tel que les déplacements impossibles, l’accès aux informations d’identification et le téléchargement inhabituel, le partage de fichiers ou l’activité de transport de courrier, et signale ces comportements à l’équipe de sécurité. Par conséquent, Defender pour les applications cloud permet d’empêcher le déplacement latéral par des pirates informatiques et l’exfiltration de données sensibles. Microsoft 356 Defender pour le Cloud met en corrélation les signaux de tous les composants pour fournir l’article complet sur les attaques.

## <a name="understand-key-concepts"></a>Comprendre les concepts clés

Le tableau suivant a identifié les concepts clés à comprendre lors de l’évaluation, de la configuration et du déploiement de Microsoft Defender pour les applications cloud.


|Concept  |Description |Plus d’informations  |
|---------|---------|---------|
| Tableau de bord Defender pour les applications cloud | Présente une vue d’ensemble des informations les plus importantes concernant votre organisation et fournit des liens vers des recherches plus approfondies.        | [Travailler avec le tableau de bord ](/cloud-app-security/daily-activities-to-protect-your-cloud-environment)       |
| Contrôle d’application d’accès conditionnel    | Architecture de proxy inverse qui s’intègre à votre fournisseur d’identité (IdP) pour Azure AD stratégies d’accès conditionnel et appliquer de manière sélective les contrôles de session.        |  [Protéger les applications avec microsoft Defender pour le contrôle d’application d’accès conditionnel aux applications cloud](/cloud-app-security/proxy-intro-aad)       |
|  Catalogue d’applications cloud   | Le catalogue d’applications cloud vous donne une vue d’ensemble du catalogue Microsoft de plus de 16 000 applications cloud classées et classées en fonction de plus de 80 facteurs de risque.    |  [Travailler avec les scores de risque de l’application](/cloud-app-security/risk-score)       |
| Tableau de bord de découverte cloud    | La découverte cloud analyse vos journaux de trafic et est conçue pour fournir plus d’informations sur la façon dont les applications cloud sont utilisées dans votre organisation, ainsi que pour fournir des alertes et des niveaux de risque.     |  [Travailler avec des applications découvertes   ](/cloud-app-security/discovered-apps)    |
|Applications connectées |Defender pour les applications cloud fournit une protection de bout en bout pour les applications connectées à l’aide de l’intégration cloud à cloud, des connecteurs d’API et des contrôles d’accès et de session en temps réel à l’aide de nos contrôles d’accès aux applications conditionnelles. |[Protection des applications connectées](/cloud-app-security/protect-connected-apps) |
| | | |

## <a name="review-architecture-requirements"></a>Passer en revue les exigences en matière d’architecture

### <a name="discovering-cloud-apps"></a>Découverte des applications cloud

Pour découvrir les applications cloud utilisées dans votre environnement, vous pouvez implémenter l’une des méthodes suivantes ou les deux :

- Préparez-vous rapidement à la découverte cloud en intégrant Microsoft Defender pour Endpoint. Cette intégration native vous permet de commencer immédiatement à collecter des données sur le trafic cloud sur vos appareils Windows 11 et Windows 10, sur et hors de votre réseau.
- Pour découvrir toutes les applications cloud accessibles par tous les appareils connectés à votre réseau, déployez le collecteur de journaux Defender for Cloud Apps sur vos pare-feu et autres proxies. Ce déploiement permet de collecter des données à partir de vos points de terminaison et de les envoyer à Defender pour les applications cloud pour analyse. Defender pour les applications cloud s’intègre en natif à certains proxies tiers pour encore plus de fonctionnalités.

Ces options sont incluses à [l’étape 2. Activez l’environnement d’évaluation](eval-defender-mcas-enable-eval.md). 

### <a name="applying-azure-ad-conditional-access-policies-to-cloud-apps"></a>Application de stratégies Azure AD’accès conditionnel aux applications cloud

Le contrôle d’application d’accès conditionnel (possibilité d’appliquer des stratégies d’accès conditionnel aux applications cloud) nécessite une intégration avec Azure AD. Cette intégration n’est pas une condition requise pour la mise en place de Defender pour les applications cloud. Il s’agit d’une étape que nous vous encourageons à tester au cours de la phase pilote , [à savoir l’étape 3. Pilotez Microsoft Defender pour les applications cloud](eval-defender-mcas-pilot.md).

## <a name="siem-integration"></a>Intégration SIEM

Vous pouvez intégrer Microsoft Defender pour les applications cloud à votre serveur SIEM générique ou à Microsoft Sentinel pour activer la surveillance centralisée des alertes et des activités à partir d’applications connectées. 

En outre, Microsoft Sentinel inclut un connecteur Microsoft Defender pour les applications cloud pour fournir une intégration plus approfondie avec Microsoft Sentinel. Cette disposition vous permet non seulement de gagner en visibilité sur vos applications cloud, mais également d’obtenir des analyses sophistiquées pour identifier et lutter contre les cybermenaces et contrôler la façon dont vos données circulent.

- [Intégration d’une solution SIEM générique](/cloud-app-security/siem)
- [Diffuser des alertes et des journaux de découverte cloud à partir de Defender pour les applications cloud dans Microsoft Sentinel](/azure/sentinel/connect-cloud-app-security)

### <a name="next-steps"></a>Prochaines étapes

Étape 2 sur 3 : activer [l’environnement d’évaluation de Microsoft Defender pour les applications cloud](eval-defender-mcas-enable-eval.md)

Revenir à la vue d’ensemble [de l’évaluation de Microsoft Defender pour les applications cloud](eval-defender-mcas-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)
