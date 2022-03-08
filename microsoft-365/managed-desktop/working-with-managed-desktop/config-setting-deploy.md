---
title: Déployer des paramètres configurables dans Microsoft Manged Desktop
description: Déployez et suivez les modifications des paramètres configurables dans Microsoft Manged Desktop.
keywords: Microsoft Manged Desktop, Microsoft 365, service, documentation, déployer, déploiement par étapes, paramètres configurables
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: a52995ff9ab2f946ca11417d4ed7bfa13825353f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326776"
---
# <a name="deploy-and-track-configurable-settings---microsoft-managed-desktop"></a>Déployer et suivre les paramètres configurables : Microsoft Manged Desktop

Après avoir apporté des modifications à vos catégories de paramètres et organisé un déploiement, la page État du déploiement vous permet de commencer à déployer vos paramètres dans des groupes. Cette page affiche un résumé de chaque paramètre configurable. Lors de l’ouverture d’une catégorie de paramètres, vous pouvez déployer des paramètres sur des groupes et suivre la progression de ces déploiements.

## <a name="deployment-statuses"></a>Statuts de déploiement

Voici les états que vous verrez pour chaque déploiement.

État | Explication
--- | ---
Déployer | Votre modification attend d’être déployée sur ce groupe.
En cours | La modification est appliquée aux appareils actifs de ce groupe.
Exécuter | Modification effectuée sur tous les appareils actifs de ce groupe.
Échec | La modification a échoué sur 10 % des appareils actifs du groupe. Le déploiement a été arrêté.<br><br> Une demande de support est automatiquement ouverte avec les Microsoft Manged Desktop pour résoudre les problèmes de déploiement.
Révérence | La modification a été revenir à la dernière modification qui a été correctement déployée sur tous les groupes de déploiement.

## <a name="deploy-changes"></a>Déployer les modifications

Par exemple, nous allons utiliser une image d’arrière-plan de bureau dans ces instructions. Après avoir mis en place un déploiement, vous déployez les modifications à partir de la page État du déploiement.

**Pour déployer les modifications :**

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils**.
2. Dans la section Microsoft Manged Desktop, sélectionnez **Paramètres**.
3. Dans **l’espace de travail** État du déploiement, sélectionnez le paramètre à déployer. Ensuite, sélectionnez le déploiement par étapes à déployer.
4. **Sélectionnez Déployer** pour déployer la modification dans l’un des groupes de déploiement.

> [!NOTE]
> L’icône d’avertissement orange indique qu’un groupe précédent est disponible pour le déploiement, car il est recommandé de le déployer dans l’ordre.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Trusted sites pane on the right. In the Deployment groups section are three columns: deployment groups, devices, and status. In the status column, "deploy" is highlighted.](../../media/1deployedit.png) -->

Nous vous recommandons de déployer les groupes de déploiement dans cet ordre : Test, Premier, Rapide, puis Large.

Lorsque les modifications sont terminées dans chaque groupe, l’état est **terminé**.

<!-- Needs picture updated to show MEM ![Deployment status workspace with columns for date updated, version, test, first, fast, and broad. The Proxy row is expanded, showing a dated setting flagged as "complete" in each of the four deployment groups.](../../media/2completeedit.png) -->

## <a name="revert-deployment"></a>Revert deployment

Une fois que vous avez déployé une modification, vous pouvez revenir à **l’état de déploiement**. Lorsque vous inversez une modification en cours **ou** **terminée**, le déploiement actuel s’arrête. Le paramètre revient à la dernière version qui a été déployée sur tous les groupes.

Par exemple, nous allons inverser l’image d’arrière-plan du bureau.

**Pour inverser une modification :**

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils**.
2. Dans la section Microsoft Manged Desktop, sélectionnez **Paramètres**.
3. Dans **l’espace de travail** État du déploiement, sélectionnez le paramètre à revenir. Ensuite, sélectionnez le déploiement par étapes à inverser.
4. Under **Need to revert this change?**, select **Revert deployment**.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Browser start pages is selected, opening a pane on the right side with data about the submitted change and its status. At the bottom is the "need to revert this change" area where you can select "Revert deployment."](../../media/3revert.png) -->

## <a name="additional-resources"></a>Ressources supplémentaires

- [Vue d’ensemble des paramètres configurables](config-setting-overview.md)
- [Référence des paramètres configurables](config-setting-ref.md)
