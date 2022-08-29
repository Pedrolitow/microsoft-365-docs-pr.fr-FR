---
title: Préparer votre posture de sécurité pour votre premier incident
description: Configurez la posture de sécurité de votre locataire Microsoft 365 pour votre premier incident dans Microsoft 365 Defender.
keywords: incidents, alertes, enquêter, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte de réception, e-mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: eeaa5c663d7f35a1a43f883953cd08c5aa1920aa
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67329044"
---
# <a name="prepare-your-security-posture-for-your-first-incident"></a>Préparer votre posture de sécurité pour votre premier incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

La préparation à la gestion des incidents implique la configuration d’une protection suffisante du réseau d’une organisation contre différents types d’incidents de sécurité. Pour réduire le risque d’incidents de sécurité, le National Institute of Standards and Technology (NIST) recommande plusieurs pratiques de sécurité, notamment les évaluations des risques, le renforcement de la sécurité des hôtes, la configuration sécurisée des réseaux et la prévention des programmes malveillants.

Microsoft 365 Defender pouvez vous aider à résoudre plusieurs aspects de la prévention des incidents :

- Implémentation d’une [infrastructure Confiance nulle](/security/zero-trust/)
- Détermination de votre posture de sécurité en attribuant un score avec [microsoft secure score](microsoft-secure-score.md)
- Prévention des menaces par le biais d’évaluations des vulnérabilités dans [Gestion des vulnérabilités Defender](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Comprendre les dernières menaces de sécurité afin de pouvoir les préparer avec [l’analytique des menaces](threat-analytics.md)

## <a name="step-1-implement-zero-trust"></a>Étape 1. Implémenter Confiance nulle

[Confiance nulle](/security/zero-trust/) est une philosophie de sécurité intégrée et une stratégie de bout en bout qui tient compte de la nature complexe de tout environnement moderne, y compris la main-d’œuvre mobile et les utilisateurs, appareils, applications et données, où qu’ils se trouvent. En fournissant un seul volet de verre pour gérer toutes les détections de manière cohérente, Microsoft 365 Defender pouvez faciliter l’implémentation des [principes directeurs](/security/zero-trust/#guiding-principles-of-zero-trust) de Confiance nulle par votre équipe chargée des opérations de sécurité.

Les composants de Microsoft 365 Defender peuvent afficher des violations de règles qui ont été implémentées pour établir des stratégies d’accès conditionnel pour Confiance nulle en intégrant des données de Microsoft Defender pour point de terminaison  ou d’autres fournisseurs de sécurité mobile comme source d’informations pour les stratégies de conformité des appareils et l’implémentation des stratégies d’accès conditionnel basées sur les appareils.

Le risque d’appareil influence directement les ressources qui seront accessibles par l’utilisateur de cet appareil. Le refus d’accès aux ressources en fonction de certains critères est le thème principal de Confiance nulle et Microsoft 365 Defender fournit les informations nécessaires pour déterminer les critères de niveau de confiance. Par exemple, Microsoft 365 Defender pouvez fournir le niveau de version logicielle d’un appareil via le Gestion des vulnérabilités Microsoft Defender, anciennement la page Gestion des vulnérabilités & menaces, tandis que les stratégies d’accès conditionnel limitent les appareils dont les versions sont obsolètes ou vulnérables.

L’automatisation est un élément essentiel de l’implémentation et de la maintenance d’un environnement Confiance nulle tout en réduisant le nombre d’alertes susceptibles d’entraîner des événements de réponse aux incidents (IR). Les composants de Microsoft 365 Defender peuvent être automatisés, tels que les [actions de correction](m365d-autoir.md) (appelées investigations pour un incident dans le portail Microsoft 365 Defender), les actions de notification et même la création de tickets de support comme dans [ServiceNow](https://microsoft.service-now.com/sp/).

## <a name="step-2-determine-your-organizations-security-posture"></a>Étape 2. Déterminer la posture de sécurité de votre organisation

Ensuite, les organisations peuvent utiliser le [score de sécurité Microsoft](microsoft-secure-score.md) dans Microsoft 365 Defender pour déterminer votre posture de sécurité actuelle et envisager des recommandations sur la façon de l’améliorer. Plus le score est élevé, plus les recommandations de sécurité et les actions d’amélioration ont été prises par l’organisation. Les recommandations de degré de sécurisation peuvent être prises sur différents produits et permettre aux organisations d’augmenter encore plus leurs scores.

:::image type="content" source="../../media/first-incident-prepare/first-incident-secure-score.png" alt-text="Page Microsoft Secure Score dans le portail Microsoft 365 Defender" lightbox="../../media/first-incident-prepare/first-incident-secure-score.png":::

## <a name="step-3-assess-your-organizations-vulnerability-exposure"></a>Étape 3. Évaluer l’exposition aux vulnérabilités de votre organisation

La prévention des incidents peut aider à simplifier les efforts des opérations de sécurité pour se concentrer sur les incidents de sécurité critiques et importants en cours. Les vulnérabilités logicielles sont souvent un point d’entrée évitable pour les attaques qui peuvent entraîner un vol de données, une perte de données ou une interruption des opérations commerciales. Si aucune attaque n’est en cours, les opérations de sécurité doivent s’efforcer d’atteindre et de maintenir un niveau acceptable [d’exposition aux vulnérabilités](../defender-endpoint/tvm-exposure-score.md) dans leur organisation.

Pour vérifier la progression des mises à jour correctives logicielles, visitez la page [Gestion des vulnérabilités Microsoft Defender](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) dans Defender pour point de terminaison, à laquelle vous pouvez accéder à partir de Microsoft 365 Defender via l’onglet **Plus de ressources**.

:::image type="content" source="../../media/first-incident-prepare/first-incident-vulnerability.png" alt-text="Page Menaces et vulnérabilités dans le portail Microsoft 365 Defender" lightbox="../../media/first-incident-prepare/first-incident-vulnerability.png":::

## <a name="4-understand-emerging-threats"></a>4. Comprendre les menaces émergentes

Utilisez [l’analytique des menaces](threat-analytics.md) dans le portail Microsoft 365 Defender pour rester à jour avec le paysage actuel des menaces de sécurité. Des experts en sécurité Microsoft créent des rapports qui décrivent en détail les dernières cybermenaces pour vous permettre de comprendre comment elles peuvent affecter votre abonnement, vos appareils et vos utilisateurs Microsoft 365. Ces rapports peuvent inclure :

- Acteurs de menaces actifs et leurs campagnes
- Techniques d’attaque populaires et nouvelles
- Vulnérabilités critiques
- Surface d'attaque courantes
- Programmes malveillants répandus

Analyse des menaces examine également votre configuration et vos alertes pour déterminer le niveau de risque et si des alertes actives s’appliquent à un rapport.

Vous pouvez implémenter les recommandations d’une menace émergente pour renforcer votre posture de sécurité et réduire votre surface d’attaque.

Prenez le temps de consulter régulièrement la section [Analyse des menaces](threat-analytics.md) du portail Microsoft 365 Defender. Pour plus d’informations, consultez [l’exemple d’opérations de sécurité pour Microsoft 365 Defender](incidents-overview.md#example-security-operations-for-microsoft-365-defender).

## <a name="next-step"></a>Étape suivante

Découvrez comment [trier et analyser les incidents](first-incident-analyze.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
