---
title: Déployer des paramètres configurables dans le bureau géré Microsoft
description: Déployer et suivre les modifications de paramètres configurables dans le bureau géré Microsoft.
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation, Deploy, Staging Deployment, configurable Settings
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 2/12/2019
ms.openlocfilehash: fd0e0750332fa8f650cfc4756f8eb108be2a71df
ms.sourcegitcommit: 59bc66eaa2575bad8ecb34d45b1172cda23a729b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2019
ms.locfileid: "30051125"
---
# <a name="deploy-and-track-configurable-settings---microsoft-managed-desktop"></a>Déployer et suivre les paramètres configurables-bureau géré Microsoft

Après avoir apporté des modifications à vos catégories de paramètres et à déployer un déploiement, vous pouvez déployer et suivre la progression du déploiement sur l'état du déploiement. Cette page affiche un résumé de chaque paramètre configurable. Ouvrez une catégorie de paramètres pour afficher chaque déploiement et ses détails, afin de déployer les modifications. 

## <a name="deployment-statuses"></a>Statuts de déploiement 

Voici les statues que vous verrez pour chaque déploiement.

État  | Explication 
--- | --- 
Déployer | Votre modification attend d'être déployée sur cette sonnerie.
En cours | La modification est appliquée aux appareils de cette sonnerie. 
Complète | La modification est appliquée aux appareils de cette sonnerie. 
Échec | La modification a échoué sur 10% des périphériques dans l'anneau, de sorte que le déploiement a été arrêté.<br><br> Une demande de support sera automatiquement ouverte avec les opérations de bureau géré Microsoft pour résoudre les problèmes de déploiement. 
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