---
title: Déployer des paramètres configurables dans le bureau géré Microsoft
description: Déployer et suivre les modifications de paramètres configurables dans le bureau géré Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation, Deploy, Staging Deployment, configurable Settings
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: e6946c138cb6fde15e35374b447038d5c302187e
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42085753"
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

1. Se connecter au [portail d’administration de bureau géré Microsoft](https://aka.ms/mwaasportal)
2. Sous **paramètres**, sélectionnez **configurable**.
3. Dans l’espace de travail **État de déploiement** , sélectionnez le paramètre que vous souhaitez déployer, puis sélectionnez le déploiement intermédiaire à déployer.
4. Sélectionnez **déployer** pour déployer la modification dans l’un des groupes de déploiement.

> [!NOTE] 
> L’icône orange attention indique qu’un groupe précédent est disponible pour le déploiement, car il est recommandé de le déployer dans l’ordre. 

![Espace de travail État de déploiement. Volet sites de confiance à droite. La section groupes de déploiement comporte trois colonnes : les groupes de déploiement, les appareils et l’État. Dans la colonne État, « déployer » est mis en surbrillance.](../../media/1deployedit.png)
Nous vous recommandons de déployer les groupes de déploiement dans cet ordre : test, First, Fast, puis large. 

Lorsque les modifications sont terminées dans chaque groupe, l’État devient **terminé**.

![Espace de travail État de déploiement avec les colonnes Date de mise à jour, version, test, tout d’abord, rapide et large. La ligne proxy est développée, avec un paramètre daté indiquant « terminé » dans chacun des quatre groupes de déploiement.](../../media/2completeedit.png)

## <a name="revert-deployment"></a>Rétablir le déploiement

Une fois que vous avez déployé une modification, vous pouvez revenir à l' **État de déploiement**. Lorsque vous rétablissez une modification qui est **en cours** ou **terminée**, le déploiement actuel s’arrête. Le paramètre reprendra la dernière version qui a été déployée sur tous les groupes. 

Nous allons vous montrer les étapes permettant de rétablir une modification à l’aide de l’image d’arrière-plan du Bureau à titre d’exemple. 

**Pour annuler une modification**
1. Se connecter au [portail d’administration de bureau géré Microsoft](https://aka.ms/mwaasportal)
2. Sous **paramètres**, sélectionnez **configurable**.
3. Dans l’espace de travail **État de déploiement** , sélectionnez le paramètre que vous souhaitez rétablir, puis sélectionnez le déploiement intermédiaire à rétablir.
4. Sous **besoin de rétablir cette modification ?**, sélectionnez **rétablir le déploiement**.

![Espace de travail État de déploiement. Pages de démarrage du navigateur est sélectionné, en ouvrant un volet du côté droit avec des données sur la modification envoyée et son état. Dans la partie inférieure se trouve la zone « je dois rétablir ce changement » où vous pouvez sélectionner « rétablir le déploiement ».](../../media/3revert.png) 

## <a name="additional-resources"></a>Ressources supplémentaires
- [Vue d’ensemble des paramètres configurables](config-setting-overview.md)
- [Référence des paramètres configurables](config-setting-ref.md) 
