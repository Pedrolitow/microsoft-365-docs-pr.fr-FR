---
title: Déployer des paramètres configurables dans le bureau géré Microsoft
description: Déployer et suivre les modifications de paramètres configurables dans le bureau géré Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation, Deploy, Staging Deployment, configurable Settings
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: a24d0dc64e2262a8b208119c45a4a6bade701c10
ms.sourcegitcommit: adaedd1418a3bd6e4875b77fd9e008b47e0b2a51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "48104533"
---
# <a name="deploy-and-track-configurable-settings---microsoft-managed-desktop"></a>Déployer et suivre les paramètres configurables-bureau géré Microsoft

Une fois que vous avez apporté des modifications à vos catégories de paramètres et que vous déployez un déploiement, la page État du déploiement vous permet de commencer à déployer vos paramètres dans des groupes. Cette page affiche un résumé de chaque paramètre configurable. En ouvrant une catégorie de paramètres, vous pouvez déployer des paramètres dans des groupes et suivre la progression de ces déploiements.

## <a name="deployment-statuses"></a>Statuts de déploiement 

Voici les statuts que vous verrez pour chaque déploiement.

Statut  | Explication 
--- | --- 
Déployer | Votre modification attend d’être déployée sur ce groupe.
En cours | La modification est appliquée aux appareils actifs de ce groupe. 
Exécuter | Modification effectuée sur tous les appareils actifs de ce groupe. 
Échec | La modification a échoué sur 10% des appareils actifs dans le groupe, de sorte que le déploiement a été arrêté.<br><br> Une demande de support sera automatiquement ouverte avec les opérations de bureau géré Microsoft pour résoudre les problèmes de déploiement. 
Retrouveront | Le changement a été rétabli sur la dernière modification qui a été déployée avec succès sur tous les groupes de déploiement.

## <a name="deploy-changes"></a>Déployer les modifications

Nous allons afficher l’image d’arrière-plan du bureau dans ces instructions. Une fois que vous avez déployé un déploiement, vous déployez les modifications à partir de la page État du déploiement. 

**Pour déployer les modifications**

1. Connectez-vous au [Gestionnaire de point de terminaison Microsoft](https://endpoint.microsoft.com/) et accédez au menu **appareils** .
2. Recherchez la section bureau géré Microsoft, puis sélectionnez **paramètres**.
3. Dans l’espace de travail **État de déploiement** , sélectionnez le paramètre que vous souhaitez déployer, puis sélectionnez le déploiement intermédiaire à déployer.
4. Sélectionnez **déployer** pour déployer la modification dans l’un des groupes de déploiement.

> [!NOTE] 
> L’icône orange attention indique qu’un groupe précédent est disponible pour le déploiement, car il est recommandé de le déployer dans l’ordre. 

<!-- Needs picture updated to show MEM ![Deployment status workspace. Trusted sites pane on the right. In the Deployment groups section are three columns: deployment groups, devices, and status. In the status column, "deploy" is highlighted.](../../media/1deployedit.png) -->

Nous vous recommandons de déployer les groupes de déploiement dans cet ordre : test, First, Fast, puis large. 

Lorsque les modifications sont terminées dans chaque groupe, l’État devient **terminé**.

<!-- Needs picture updated to show MEM ![Deployment status workspace with columns for date updated, version, test, first, fast, and broad. The Proxy row is expanded, showing a dated setting flagged as "complete" in each of the four deployment groups.](../../media/2completeedit.png) -->

## <a name="revert-deployment"></a>Rétablir le déploiement

Une fois que vous avez déployé une modification, vous pouvez revenir à l' **État de déploiement**. Lorsque vous rétablissez une modification qui est **en cours** ou **terminée**, le déploiement actuel s’arrête. Le paramètre reprendra la dernière version qui a été déployée sur tous les groupes. 

Nous allons vous montrer les étapes permettant de rétablir une modification à l’aide de l’image d’arrière-plan du Bureau à titre d’exemple. 

**Pour annuler une modification**
1. Connectez-vous au [Gestionnaire de point de terminaison Microsoft](https://endpoint.microsoft.com/) et accédez au menu **appareils** .
2. Recherchez la section bureau géré Microsoft, puis sélectionnez **paramètres**.
3. Dans l’espace de travail **État de déploiement** , sélectionnez le paramètre que vous souhaitez rétablir, puis sélectionnez le déploiement intermédiaire à rétablir.
4. Sous **besoin de rétablir cette modification ?**, sélectionnez **rétablir le déploiement**.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Browser start pages is selected, opening a pane on the right side with data about the submitted change and its status. At the bottom is the "need to revert this change" area where you can select "Revert deployment."](../../media/3revert.png) -->

## <a name="additional-resources"></a>Ressources supplémentaires
- [Vue d’ensemble des paramètres configurables](config-setting-overview.md)
- [Référence des paramètres configurables](config-setting-ref.md) 
