---
title: Intégrer des appareils et configurer les fonctionnalités de Microsoft Defender pour point de terminaison
description: Intégrer Windows 10 appareils, serveurs, appareils non Windows et apprendre à exécuter un test de détection.
keywords: intégration, Microsoft Defender pour point de terminaison intégration, sccm, stratégie de groupe, mdm, script local, test de détection
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 1640355cf1312a84d1e4c5d5c4da49b5abe4ade1
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586355"
---
# <a name="onboard-devices-and-configure-microsoft-defender-for-endpoint-capabilities"></a>Intégrer des appareils et configurer les fonctionnalités de Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Le déploiement de Microsoft Defender pour point de terminaison est un processus en deux étapes.

- Intégrer des appareils à des services
- Configurer les fonctionnalités du service

:::image type="content" source="images/deployment-steps.png" alt-text="Processus d’intégration et de configuration" lightbox="images/deployment-steps.png":::

## <a name="role-based-access-control"></a>Contrôle d'accès basé sur les rôles

Nous vous recommandons d’utiliser Privileged Identity Management pour gérer vos rôles afin de fournir un audit, un contrôle et une révision d’accès supplémentaires pour les utilisateurs disposant d’autorisations d’annuaire.

Defender pour point de terminaison prend en charge deux façons de gérer les autorisations :

- **Gestion des autorisations de base** : définit les autorisations sur un accès complet ou en lecture seule. Les utilisateurs disposant de rôles d’administrateur général ou d’administrateur de sécurité dans Azure Active Directory (Azure AD) ont un accès complet. Le rôle lecteur de sécurité dispose d’un accès en lecture seule et n’accorde pas l’accès pour afficher l’inventaire des machines/appareils.

- **Contrôle d’accès en fonction du rôle (RBAC)** : définit des autorisations granulaires en définissant des rôles, en affectant des groupes d’utilisateurs Azure AD aux rôles et en accordant aux groupes d’utilisateurs l’accès aux groupes d’appareils. Pour plus d’informations. consultez [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](rbac.md).

Nous vous recommandons d’utiliser RBAC pour vous assurer que seuls les utilisateurs disposant d’une justification métier peuvent accéder à Defender pour point de terminaison.

## <a name="onboard-devices-to-the-service"></a>Intégrer des appareils à des services
Vous devez accéder à la section d’intégration du portail Defender pour point de terminaison pour intégrer l’un des appareils pris en charge. Selon l’appareil, vous serez guidé avec les étapes appropriées et les options d’outils de gestion et de déploiement fournies pour l’appareil. 

Pour intégrer des appareils au service :

- Vérifier que l’appareil répond aux [exigences minimales](minimum-requirements.md)
- Selon l’appareil, suivez les étapes de configuration fournies dans la section d’intégration du portail Defender pour point de terminaison
- Utiliser l’outil de gestion et la méthode de déploiement appropriés pour vos appareils
- Exécuter un test de détection pour vérifier que les appareils sont correctement intégrés et signaler au service

Cet article fournit des informations sur les méthodes d’intégration applicables aux versions client et serveur Windows.

## <a name="onboarding-and-configuration-tool-options"></a>Options de l’outil d’intégration et de configuration
Le tableau suivant répertorie les outils disponibles en fonction du point de terminaison à intégrer.

| Point de terminaison     | Options de l’outil                       |
|--------------|------------------------------------------|
| **Client Windows**  |     [Mobile Gestion des appareils / Microsoft Intune](configure-endpoints-mdm.md) <br> [Stratégie de groupe](configure-endpoints-gp.md) <br> [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>[Scripts VDI](configure-endpoints-vdi.md) <br> [Intégration de à Microsoft Defender pour le cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **Windows Server**  | [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Scripts VDI](configure-endpoints-vdi.md) <br> [Intégration de à Microsoft Defender pour le cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **MacOS**    | [Scripts locaux](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md) |
| **Serveur Linux** | [Script local](linux-install-manually.md) <br> [Marionnette](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md) <br> [Intégration de à Microsoft Defender pour le cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)     |
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)           |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)            | 


> [!NOTE]
> Pour les appareils qui ne sont pas gérés par un Endpoint Manager Microsoft (Microsoft Intune ou Microsoft Endpoint Configuration Manager), vous pouvez utiliser la gestion de la sécurité pour Microsoft Defender pour point de terminaison  pour recevoir des configurations de sécurité pour Microsoft Defender directement à partir de Endpoint Manager.

Le tableau suivant répertorie les outils disponibles en fonction du point de terminaison à intégrer.

## <a name="configure-capabilities-of-the-service"></a>Configurer les fonctionnalités du service
L’intégration des appareils active efficacement la fonctionnalité de détection et de réponse des points de terminaison de Microsoft Defender pour point de terminaison.

Après avoir intégré les appareils, vous devez configurer les autres fonctionnalités du service. Le tableau suivant répertorie les fonctionnalités que vous pouvez configurer pour obtenir la meilleure protection pour votre environnement.

| Fonctionnalité | Description |
|-|-|
| [Configurer Gestion des vulnérabilités Microsoft Defender (MDVM)](tvm-prerequisites.md) | Defender Vulnerability Management est un composant de Microsoft Defender pour point de terminaison et fournit aux administrateurs de sécurité et aux équipes des opérations de sécurité une valeur unique, notamment : <br><br> - Insights de détection et de réponse des points de terminaison en temps réel (EDR) corrélés avec les vulnérabilités de point de terminaison. <br><br> - Contexte de vulnérabilité d’appareil inestimable pendant les enquêtes sur les incidents. <br><br> - Processus de correction intégrés via Microsoft Intune et Microsoft System Center Configuration Manager.  |
| [Configurer la protection nouvelle génération (NGP)](configure-microsoft-defender-antivirus-features.md) | L’antivirus Microsoft Defender est une solution anti-programme malveillant intégrée qui fournit une protection de nouvelle génération pour les ordinateurs de bureau, les ordinateurs portables et les serveurs. L’antivirus Microsoft Defender inclut les éléments suivants :<br> <br>- Protection fournie par le cloud pour la détection quasi instantanée et le blocage des menaces nouvelles et émergentes. Tout comme l’apprentissage automatique et le système Intelligent Security Graph, la protection fournie par le cloud fait partie des technologies nouvelle génération intégrées à l’antivirus Microsoft Defender.<br> <br> - Analyse en permanence à l’aide de la surveillance avancée du comportement des fichiers et des processus et d’autres heuristiques (également appelées « protection en temps réel »).<br><br> - Mises à jour de protection dédiées basées sur le Machine Learning, l’analyse du Big Data humaine et automatisée, ainsi que la recherche approfondie sur la résistance aux menaces. |
| [Configurer la réduction de la surface d’attaque (ASR)](overview-attack-surface-reduction.md) | Les fonctionnalités de réduction de la surface d’attaque dans Microsoft Defender pour point de terminaison aident à protéger les appareils et les applications de l’organisation contre les menaces nouvelles et émergentes. |
| [Configurer les fonctionnalités air (Auto Investigation & Remediation)](configure-automated-investigations-remediation.md) | Microsoft Defender pour point de terminaison utilise des investigations automatisées pour réduire considérablement le volume d’alertes qui doivent être examinées individuellement. La fonctionnalité d’investigation automatisée utilise différents algorithmes d’inspection et processus utilisés par les analystes (tels que les playbooks) pour examiner les alertes et prendre des mesures de correction immédiates pour résoudre les violations. Cela réduit considérablement les volumes d’alertes, ce qui permet aux experts en matière de sécurité de se concentrer sur des menaces plus sophistiquées et d’autres initiatives de grande valeur. |
| [Configurer les fonctionnalités Spécialistes des menaces Microsoft (MTE)](configure-microsoft-threat-experts.md) | Spécialistes des menaces Microsoft est un service de chasse managé qui fournit aux centres d’opérations de sécurité (SOC) une surveillance et une analyse de niveau expert pour les aider à s’assurer que les menaces critiques dans leurs environnements uniques ne sont pas manquées.      |

Pour plus d’informations, consultez [Fonctionnalités de Microsoft Defender pour point de terminaison prises en charge par plateforme](supported-capabilities-by-platform.md).


