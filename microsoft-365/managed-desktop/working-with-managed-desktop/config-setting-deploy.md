---
title: Déployer des paramètres configurables dans le bureau géré Microsoft
description: Déployer et suivre les modifications de paramètres configurables dans le bureau géré Microsoft.
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation, Deploy, Staging Deployment, configurable Settings
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 2/17/2019
ms.openlocfilehash: d6e669ecb2e00158dd3ce6712014244fa2f081c9
ms.sourcegitcommit: b838e1dc7a98fcce1bdf7b76173f5f04f16be703
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "30175776"
---
# <a name="deploy-and-track-configurable-settings---microsoft-managed-desktop"></a>Déployer et suivre les paramètres configurables-bureau géré Microsoft

Après avoir apporté des modifications à vos catégories de paramètres et à déployer un déploiement, vous pouvez déployer et suivre la progression du déploiement sur l'état du déploiement. Cette page affiche un résumé de chaque paramètre configurable. Ouvrez une catégorie de paramètres pour afficher chaque déploiement et ses détails, afin de déployer les modifications. 

## <a name="deployment-statuses"></a>Statuts de déploiement 

Voici les statues que vous verrez pour chaque déploiement.

État  | Explication 
--- | --- 
Déployer | Votre modification attend d'être déployée sur cette sonnerie.
En cours | La modification est appliquée aux appareils actifs dans cette sonnerie. 
Complète | Modification effectuée sur tous les périphériques actifs de cette sonnerie. 
Échec | La modification a échoué sur 10% des appareils actifs dans l'anneau, de sorte que le déploiement a été arrêté.<br><br> Une demande de support sera automatiquement ouverte avec les opérations de bureau géré Microsoft pour résoudre les problèmes de déploiement. 
Retrouveront | La modification a été rétablie à la dernière modification qui a été correctement déployée sur toutes les sonneries de déploiement.

## <a name="deploy-changes"></a>Déployer les modifications

Nous allons afficher l'image d'arrière-plan du bureau dans ces instructions. Une fois que vous avez déployé un déploiement, vous déployez les modifications à partir de l'état du déploiement. 

**Pour déployer les modifications**

1. Se connecter au [portail d'administration de bureau géré Microsoft](http://aka.ms/mwaasportal)
2. Sous **paramètres**, sélectionnez **configurable**.
3. Dans l'espace de travail **État de déploiement** , sélectionnez le paramètre que vous souhaitez déployer, puis sélectionnez le déploiement intermédiaire à déployer.
4. Sélectionnez **déployer** pour déployer la modification vers l'une des sonneries de déploiement.

![Vue d'ensemble du statut de déploiement des paramètres configurables](images/deploy-cs-overview.png)

Microsoft maNaged Desktop recommande le déploiement aux sonneries de déploiement dans cet ordre: test, First, Fast, puis large. 

Lorsque les modifications sont terminées dans chaque sonnerie, l'État devient **terminé**.

![Déploiement des paramètres configurables terminé](images/config-setting-complete.png)

## <a name="revert-deployment"></a>Rétablir le déploiement

Nous allons afficher l'image d'arrière-plan du bureau dans ces instructions. 

Une fois que vous avez déployé une modification, vous pouvez revenir à l' **État de déploiement**. Lorsque vous rétablissez une modification qui est **en cours** ou **terminée**, le déploiement actuel s'arrête. Le paramètre reprendra la dernière version qui a été déployée sur toutes les sonneries. 

**Pour annuler une modification**
1. Se connecter au [portail d'administration de bureau géré Microsoft](http://aka.ms/mwaasportal)
2. Sous **paramètres**, sélectionnez **configurable**.
3. Dans l'espace de travail **État de déploiement** , sélectionnez le paramètre que vous souhaitez rétablir, puis sélectionnez le déploiement intermédiaire à rétablir.
4. Sous **nécessité de rétablir cette modification**, sélectionnez **rétablir le déploiement**.

![Rétablissement du déploiement des paramètres configurables](images/config-setting-revert.png) 

## <a name="additional-resources"></a>Ressources supplémentaires
- [Vue d'ensemble des paramètres configurables](config-setting-overview.md)
- [Référence des paramètres configurables](config-setting-ref.md) 