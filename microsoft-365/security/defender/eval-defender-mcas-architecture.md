---
title: Passer en revue les exigences d’architecture et la structure de Microsoft Defender for Cloud Apps
description: Microsoft Defender for Cloud Apps diagrammes techniques expliquent l’architecture dans Microsoft 365 Defender, ce qui vous aidera à créer un environnement pilote.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
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
- zerotrust-solution
- highpri
ms.topic: conceptual
ms.openlocfilehash: e012ee5c94a37456a67dc5624e2aae0a2a460548
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67473807"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-cloud-apps"></a>Passer en revue les exigences d’architecture et les concepts clés pour Microsoft Defender for Cloud Apps


**S’applique à :**

- Microsoft 365 Defender

Cet article est [l’étape 1 sur 3](eval-defender-mcas-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender for Cloud Apps en même temps que Microsoft 365 Defender. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-identity-overview.md).

Avant d’activer Microsoft Defender for Cloud Apps, veillez à bien comprendre l’architecture et à répondre aux exigences. 

## <a name="understand-the-architecture"></a>Comprendre l’architecture

Microsoft Defender for Cloud Apps est un courtier en sécurité d’accès cloud (CASB). Les casb agissent comme un gardien pour répartit l’accès en temps réel entre vos utilisateurs d’entreprise et les ressources cloud qu’ils utilisent, où que se trouvent vos utilisateurs et quel que soit l’appareil qu’ils utilisent. Microsoft Defender for Cloud Apps s’intègre en mode natif aux fonctionnalités de sécurité Microsoft, y compris Microsoft 365 Defender.

Sans Defender pour Cloud Apps, les applications cloud utilisées par votre organisation ne sont pas gérées et non protégées, comme illustré.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-a.png" alt-text="Architecture de Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-architecture-a.png":::

Dans cette illustration :
- L’utilisation d’applications cloud par une organisation n’est pas surveillée et non protégée. 
- Cette utilisation ne correspond pas aux protections obtenues au sein d’une organisation gérée. 

#### <a name="discovering-cloud-apps"></a>Découverte d’applications cloud

La première étape de la gestion de l’utilisation des applications cloud consiste à découvrir quelles applications cloud sont utilisées par votre organisation. Ce diagramme suivant illustre le fonctionnement de la découverte cloud avec Defender pour Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-b.png" alt-text="Architecture pour Microsoft Defender for Cloud Apps dans la découverte cloud" lightbox="../../media/defender/m365-defender-mcas-architecture-b.png":::


Dans cette illustration, deux méthodes peuvent être utilisées pour surveiller le trafic réseau et découvrir les applications cloud utilisées par votre organisation.
- R. Cloud App Discovery s’intègre à Microsoft Defender pour point de terminaison en mode natif. Defender pour point de terminaison signale les applications et services cloud accessibles à partir d’appareils Windows 10 et Windows 11 gérés par l’informatique. 
- B. Pour une couverture sur tous les appareils connectés à un réseau, le collecteur de journaux Defender pour Cloud Apps est installé sur des pare-feu et d’autres proxys pour collecter des données à partir de points de terminaison. Ces données sont envoyées à Defender pour Cloud Apps à des fins d’analyse.

#### <a name="managing-cloud-apps"></a>Gestion des applications cloud

Après avoir découvert les applications cloud et analysé la façon dont ces applications sont utilisées par votre organisation, vous pouvez commencer à gérer les applications cloud que vous choisissez. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-c.png" alt-text="Architecture pour Microsoft Defender for Cloud Apps lors de la gestion des applications cloud" lightbox="../../media/defender/m365-defender-mcas-architecture-c.png":::

Dans cette illustration :
- Certaines applications sont autorisées à être utilisées. Cette sanction est un moyen simple de commencer à gérer les applications.
- Vous pouvez améliorer la visibilité et le contrôle en connectant des applications à des connecteurs d’application. Les connecteurs d’application utilisent les API des fournisseurs d’applications.


#### <a name="applying-session-controls-to-cloud-apps"></a>Application de contrôles de session à des applications cloud

Microsoft Defender for Cloud Apps sert de proxy inverse, fournissant un accès proxy aux applications cloud approuvées. Cette disposition permet à Defender pour Cloud Apps d’appliquer les contrôles de session que vous configurez. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-d.png" alt-text="Architecture pour Microsoft Defender for Cloud Apps - Contrôle de session d’accès proxy" lightbox="../../media/defender/m365-defender-mcas-architecture-d.png":::

Dans cette illustration :
- L’accès aux applications cloud approuvées à partir d’utilisateurs et d’appareils de votre organisation est routée via Defender pour Cloud Apps.
- Cet accès proxy permet d’appliquer des contrôles de session.
- Les applications cloud que vous n’avez pas approuvées ou explicitement non approuvées ne sont pas affectées.

Les contrôles de session vous permettent d’appliquer des paramètres à la façon dont les applications cloud sont utilisées par votre organisation. Par exemple, si votre organisation utilise Salesforce, vous pouvez configurer une stratégie de session qui autorise uniquement les appareils gérés à accéder aux données de votre organisation sur Salesforce. Un exemple plus simple peut être la configuration d’une stratégie pour surveiller le trafic à partir d’appareils non gérés afin que vous puissiez analyser le risque de ce trafic avant d’appliquer des stratégies plus strictes.

#### <a name="integrating-with-azure-ad-with-conditional-access-app-control"></a>Intégration à Azure AD avec le contrôle d’application d’accès conditionnel

Vous avez peut-être déjà ajouté des applications SaaS à votre locataire Azure AD pour appliquer l’authentification multifacteur et d’autres stratégies d’accès conditionnel. Microsoft Defender for Cloud Apps s’intègre en mode natif à Azure AD. Il vous suffit de configurer une stratégie dans Azure AD pour utiliser le contrôle d’application d’accès conditionnel dans Defender pour les applications cloud. Cela achemine le trafic réseau pour ces applications SaaS gérées via Defender pour Cloud Apps en tant que proxy, ce qui permet à Defender pour Cloud Apps de surveiller ce trafic et d’appliquer des contrôles de session. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-e.png" alt-text="Architecture des applications Microsoft Defender for Cloud Apps - SaaS" lightbox="../../media/defender/m365-defender-mcas-architecture-e.png":::

Dans cette illustration :
- Les applications SaaS sont intégrées au locataire Azure AD. Cette intégration permet à Azure AD d’appliquer des stratégies d’accès conditionnel, notamment l’authentification multifacteur.
- Une stratégie est ajoutée à Azure Active Directory pour diriger le trafic des applications SaaS vers Defender pour Cloud Apps. La stratégie spécifie les applications SaaS auxquelles appliquer cette stratégie. Par conséquent, une fois qu’Azure AD applique toutes les stratégies d’accès conditionnel qui s’appliquent à ces applications SaaS, Azure AD dirige (proxys) le trafic de session via Defender pour Cloud Apps.
- Defender pour Cloud Apps surveille ce trafic et applique toutes les stratégies de contrôle de session qui ont été configurées par les administrateurs. 

Vous avez peut-être découvert et approuvé des applications cloud qui n’ont pas été ajoutées à Azure AD à l’aide de Defender pour Cloud Apps. Vous pouvez tirer parti du contrôle d’application d’accès conditionnel en ajoutant ces applications cloud à votre locataire Azure AD et à l’étendue de vos règles d’accès conditionnel.

#### <a name="protecting-your-organization-from-hackers"></a>Protection de votre organisation contre les pirates informatiques

Defender pour Cloud Apps fournit une protection puissante par elle-même. Toutefois, lorsqu’il est combiné avec les autres fonctionnalités de Microsoft 365 Defender, Defender pour Cloud Apps fournit des données dans les signaux partagés qui (ensemble) permettent d’arrêter les attaques.

Il est intéressant de répéter cette illustration de la vue d’ensemble à ce guide d’évaluation et de pilote Microsoft 365 Defender. 

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="Comment Microsoft 365 Defender arrête une chaîne de menaces" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

En se concentrant sur le côté droit de cette illustration, Microsoft Defender for Cloud Apps remarque un comportement anormal, tel qu’un déplacement impossible, un accès aux informations d’identification, un téléchargement inhabituel, un partage de fichiers ou une activité de transfert de courrier, et signale ces comportements à l’équipe de sécurité. Par conséquent, Defender pour Cloud Apps permet d’éviter le déplacement latéral par les pirates informatiques et l’exfiltration de données sensibles. Microsoft 356 Defender pour cloud met en corrélation les signaux de tous les composants pour fournir l’histoire complète des attaques.

## <a name="understand-key-concepts"></a>Comprendre les concepts clés

Le tableau suivant a identifié des concepts clés qui sont importants à comprendre lors de l’évaluation, de la configuration et du déploiement de Microsoft Defender for Cloud Apps.


|Concept  |Description |Plus d’informations  |
|---------|---------|---------|
| Tableau de bord defender pour les applications cloud | Présente une vue d’ensemble des informations les plus importantes sur votre organisation et fournit des liens vers une investigation plus approfondie.        | [Utilisation du tableau de bord ](/cloud-app-security/daily-activities-to-protect-your-cloud-environment)       |
| Contrôle d’application d’accès conditionnel    | Architecture de proxy inverse qui s’intègre à votre fournisseur d’identité (IdP) pour fournir des stratégies d’accès conditionnel Azure AD et appliquer de manière sélective les contrôles de session.        |  [Protéger les applications avec Microsoft Defender for Cloud Apps contrôle d’application d’accès conditionnel](/cloud-app-security/proxy-intro-aad)       |
|  Catalogue d’applications cloud   | Le catalogue d’applications cloud vous donne une image complète du catalogue Microsoft de plus de 16 000 applications cloud classées et notées en fonction de plus de 80 facteurs de risque.    |  [Utilisation des scores de risque de l’application](/cloud-app-security/risk-score)       |
| Tableau de bord Cloud Discovery    | Cloud Discovery analyse vos journaux de trafic et est conçu pour fournir plus d’informations sur la façon dont les applications cloud sont utilisées dans votre organisation, ainsi que pour fournir des alertes et des niveaux de risque.     |  [Utilisation d’applications découvertes   ](/cloud-app-security/discovered-apps)    |
|Applications connectées |Defender pour Cloud Apps fournit une protection de bout en bout pour les applications connectées à l’aide de l’intégration cloud-à-cloud, des connecteurs d’API et des contrôles d’accès en temps réel et de session à l’aide de nos contrôles d’accès conditionnel aux applications. |[Protection des applications connectées](/cloud-app-security/protect-connected-apps) |
| | | |

## <a name="review-architecture-requirements"></a>Passer en revue les exigences en matière d’architecture

### <a name="discovering-cloud-apps"></a>Découverte d’applications cloud

Pour découvrir les applications cloud utilisées dans votre environnement, vous pouvez implémenter une ou les deux méthodes suivantes :

- Démarrez rapidement avec Cloud Discovery en vous intégrant à Microsoft Defender pour point de terminaison. Cette intégration native vous permet de commencer immédiatement à collecter des données sur le trafic cloud sur vos appareils Windows 11 et Windows 10, sur et hors de votre réseau.
- Pour découvrir toutes les applications cloud accessibles par tous les appareils connectés à votre réseau, déployez le collecteur de journaux Defender pour Cloud Apps sur vos pare-feu et autres proxys. Ce déploiement permet de collecter des données à partir de vos points de terminaison et de les envoyer à Defender pour Cloud Apps à des fins d’analyse. Defender pour Cloud Apps s’intègre en mode natif à certains proxys tiers pour encore plus de fonctionnalités.

Ces options sont incluses à [l’étape 2. Activez l’environnement d’évaluation](eval-defender-mcas-enable-eval.md). 

### <a name="applying-azure-ad-conditional-access-policies-to-cloud-apps"></a>Application de stratégies d’accès conditionnel Azure AD aux applications cloud

Le contrôle d’application d’accès conditionnel (la possibilité d’appliquer des stratégies d’accès conditionnel aux applications cloud) nécessite une intégration à Azure AD. Cette intégration n’est pas nécessaire pour la prise en main de Defender pour Cloud Apps. Il s’agit d’une étape que nous vous encourageons à essayer pendant la phase pilote, [à savoir l’étape 3. Pilote Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md).

## <a name="siem-integration"></a>Intégration SIEM

Vous pouvez intégrer Microsoft Defender for Cloud Apps à votre serveur SIEM générique ou à Microsoft Sentinel pour activer la surveillance centralisée des alertes et des activités à partir d’applications connectées. 

En outre, Microsoft Sentinel inclut un connecteur Microsoft Defender for Cloud Apps pour fournir une intégration plus approfondie à Microsoft Sentinel. Cette disposition vous permet non seulement d’obtenir une visibilité sur vos applications cloud, mais également d’obtenir des analyses sophistiquées pour identifier et combattre les cybermenaces et contrôler le mode de déplacement de vos données.

- [Intégration d’une solution SIEM générique](/cloud-app-security/siem)
- [Diffuser en continu des alertes et des journaux Cloud Discovery de Defender pour Cloud Apps vers Microsoft Sentinel](/azure/sentinel/connect-cloud-app-security)

### <a name="next-steps"></a>Prochaines étapes

Étape 2 sur 3 : [Activer l’environnement d’évaluation pour Microsoft Defender for Cloud Apps](eval-defender-mcas-enable-eval.md)

Revenir à la vue d’ensemble de [Evaluate Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
