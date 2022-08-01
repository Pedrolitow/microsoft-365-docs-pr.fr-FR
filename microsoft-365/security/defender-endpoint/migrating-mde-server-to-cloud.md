---
title: Migration de serveurs de Microsoft Defender pour point de terminaison vers Microsoft Defender pour cloud
description: Découvrez comment migrer des serveurs de Microsoft Defender pour point de terminaison vers Microsoft Defender pour cloud.
keywords: migrate server, server, Microsoft Defender pour point de terminaison server, Microsoft Defender for Cloud, MDE, azure, azure cloud, CSPM, CWP, protection contre la charge de travail cloud, protection contre les menaces, protection avancée contre les menaces, Microsoft Azure, connecteur multicloud
author: alekyaj
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: migrationguides
ms.date: 07/19/2022
ms.technology: mde
ms.openlocfilehash: d6ce0fe6b001c537a6bb801f18920f759a1cce09
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2022
ms.locfileid: "67108434"
---
# <a name="migrating-servers-from-microsoft-defender-for-endpoint-to-microsoft-defender-for-cloud"></a>Migration de serveurs de Microsoft Defender pour point de terminaison vers Microsoft Defender pour cloud

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Cet article vous guide dans la migration de serveurs de Microsoft Defender pour point de terminaison (MDE) vers Defender pour cloud.

[Microsoft Defender pour point de terminaison](https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-endpoint) (MDE) est une plateforme de sécurité de point de terminaison d’entreprise conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées.

[Microsoft Defender pour cloud](https://azure.microsoft.com/services/defender-for-cloud/) est une solution pour la gestion de la posture de sécurité cloud (CSPM) et la protection des charges de travail cloud (CWP) qui recherche des points faibles dans votre configuration cloud. Il contribue également à renforcer la posture de sécurité globale de votre environnement et peut protéger les charges de travail dans les environnements multiclouds et hybrides contre les menaces en constante évolution.

Bien que les deux produits offrent des fonctionnalités de protection des serveurs, Microsoft Defender pour cloud est notre solution principale pour protéger les ressources d’infrastructure, y compris les serveurs. 

## <a name="how-do-i-migrate-my-servers-from-microsoft-defender-for-endpoint-to-microsoft-defender-for-cloud"></a>Comment faire migrer mes serveurs de Microsoft Defender pour point de terminaison vers Microsoft Defender pour cloud ?

Si vous avez des serveurs intégrés à Defender pour point de terminaison, le processus de migration varie en fonction du type d’ordinateur, mais il existe un ensemble de conditions préalables partagées. 

Microsoft Defender pour cloud est un service basé sur un abonnement dans le Portail Azure Microsoft. Par conséquent, Defender pour le cloud et les plans sous-jacents tels que Microsoft Defender pour serveurs Plan 2 doivent être activés sur les abonnements Azure.

Pour activer Defender pour serveurs pour les machines virtuelles Azure et les machines non-Azure connectées via des [serveurs avec Azure Arc](/azure/azure-arc/servers/overview), suivez les instructions suivantes :

1. Si vous n’utilisez pas déjà Azure, planifiez votre environnement en suivant [Azure Well-Architected Framework](/azure/architecture/framework/).
2. Activez [Microsoft Defender pour cloud](/azure/defender-for-cloud/get-started) sur vos abonnements.
3. Activez l’un des plans Microsoft Defender pour Server sur vos [abonnements](/azure/defender-for-cloud/enable-enhanced-security). Si vous utilisez Defender pour serveurs Plan 2, veillez à l’activer également sur l’espace de travail Log Analytics sur lequel vos machines sont connectées ; Il vous permettra d’utiliser des fonctionnalités facultatives telles que la surveillance de l’intégrité des fichiers, les contrôles d’application adaptatifs, etc.
4. Vérifiez que [l’intégration MDE](/azure/defender-for-cloud/integration-defender-for-endpoint?tabs=windows) est activée sur votre abonnement. Si vous avez des abonnements Azure préexistants, vous pouvez voir l’un des deux boutons d’adhésion (ou les deux) affichés dans l’image ci-dessous.
     :::image type="content" source="images/mde-integration.png" alt-text="Capture d’écran montrant comment activer l’intégration MDE.":::
Si vous avez l’un de ces boutons dans votre environnement, veillez à activer l’intégration pour les deux. Sur les nouveaux abonnements, les deux options sont activées par défaut.
5. Assurez-vous que les exigences de connectivité pour Azure Arc sont remplies. Microsoft Defender pour cloud requiert que toutes les machines locales et non Azure soient connectées via l’agent Azure Arc. En outre, Azure Arc ne prend pas en charge tous les systèmes d’exploitation pris en charge par MDE. Découvrez donc comment planifier [les déploiements Azure Arc ici](/azure/azure-arc/servers/plan-at-scale-deployment).
6. *Recommandé:* Si vous souhaitez voir les résultats des vulnérabilités dans Defender pour cloud, veillez à activer [Gestion des vulnérabilités Microsoft Defender](/azure/defender-for-cloud/enable-data-collection?tabs=autoprovision-va) pour Defender pour cloud.
   :::image type="content" source="images/enable-threat-and-vulnerability-management.png" alt-text="Capture d’écran montrant comment activer la gestion des vulnérabilités."::: 

## <a name="how-do-i-migrate-existing-azure-vms-to-microsoft-defender-for-cloud"></a>Comment faire migrer des machines virtuelles Azure existantes vers Microsoft Defender pour cloud ?

Pour les machines virtuelles Azure, aucune étape supplémentaire n’est requise. Celles-ci sont automatiquement intégrées à Microsoft Defender pour cloud, grâce à l’intégration native entre la plateforme Azure et Defender pour cloud.

## <a name="how-do-i-migrate-on-premises-machines-to-microsoft-defender-for-servers"></a>Comment faire migrer des machines locales vers Microsoft Defender pour serveurs ?

[Connectez](/azure/defender-for-cloud/quickstart-onboard-machines?pivots=azure-arc) vos machines locales via des serveurs connectés à Azure Arc.

## <a name="how-do-i-migrate-vms-from-aws-or-gcp-environments"></a>Comment faire migrer des machines virtuelles à partir d’environnements AWS ou GCP ?

1. Créez un connecteur multicloud sur votre abonnement. (Pour plus d’informations sur le connecteur, consultez [les comptes AWS](/azure/defender-for-cloud/quickstart-onboard-aws?pivots=env-settings) ou les [projets GCP](/azure/defender-for-cloud/quickstart-onboard-gcp?pivots=env-settings).
2. Sur votre connecteur multicloud, activez Defender pour serveurs sur des connecteurs [AWS](/azure/defender-for-cloud/quickstart-onboard-aws?pivots=env-settings#prerequisites) ou [GCP](/azure/defender-for-cloud/quickstart-onboard-gcp?pivots=env-settings#configure-the-servers-plan) .
3. Activez l’approvisionnement automatique sur le connecteur multicloud pour l’agent Azure Arc, l’extension Microsoft Defender pour point de terminaison, l’évaluation des vulnérabilités et, éventuellement, l’extension Log Analytics.
     :::image type="content" source="images/select-plans-aws-gcp.png" alt-text="Capture d’écran montrant comment activer l’approvisionnement automatique pour l’agent Azure Arc.":::
Pour plus [d’informations, consultez les fonctionnalités multiclouds de Defender pour Cloud](https://aka.ms/mdcmc).

## <a name="what-happens-once-all-migration-steps-are-completed"></a>Que se passe-t-il une fois toutes les étapes de migration terminées ?

Une fois que vous avez effectué les étapes de migration appropriées, Microsoft Defender pour cloud déploie l’extension `MDE.Windows` sur `MDE.Linux` vos machines virtuelles Azure et non-Azure connectées via Azure Arc (y compris les machines virtuelles dans le calcul AWS et GCP).

L’extension agit comme une interface de gestion et de déploiement, qui orchestre et encapsule les scripts d’installation MDE à l’intérieur du système d’exploitation et reflète son état d’approvisionnement dans le plan de gestion Azure. Le processus d’installation reconnaît une installation defender pour point de terminaison existante et la connecte à Defender pour cloud en ajoutant automatiquement des balises de service Defender pour point de terminaison.

Si vous avez Windows Server 2012 machines R2 ou 2016 approvisionnées avec la solution Microsoft Defender pour point de terminaison héritée basée sur Log Analytics, le processus de déploiement de Microsoft Defender pour Cloud déploiera la [solution unifiée](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) Defender pour point de terminaison. Une fois le déploiement réussi, il arrête et désactive le processus Defender pour point de terminaison hérité sur ces machines.
