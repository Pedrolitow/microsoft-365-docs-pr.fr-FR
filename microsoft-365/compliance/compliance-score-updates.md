---
title: Mises à jour du score de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Détails sur les futures mises à jour de Microsoft Compliance score (Preview), une fonctionnalité du centre de conformité M365 qui permet de simplifier et d’automatiser les évaluations des risques.
ms.openlocfilehash: c46b70d0762a805e4ecfc83b70173c56d21a3933
ms.sourcegitcommit: fe4beef350ef9f39b1098755cff46fa2b8e7dc4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "42857761"
---
# <a name="microsoft-compliance-score-preview-updates"></a>Mises à jour du score de conformité Microsoft (aperçu)

 Cet article fournit des détails sur les mises à jour futures du [score de conformité Microsoft](compliance-score.md) et du [Gestionnaire de conformité Microsoft](compliance-manager-overview.md). En savoir plus sur leur [relation](compliance-score-release-notes.md#compliance-score-relationship-to-compliance-manager).

## <a name="improved-template-creation-and-update-processes"></a>Amélioration des processus de création et de mise à jour des modèles

Nous simplifions le processus d’importation, d’exportation et de modification des modèles pour les évaluations. La nouvelle expérience vous permettra d’apporter plus facilement vos propres évaluations dans le score de conformité et de les maintenir à jour.

### <a name="the-current-process"></a>Processus actuel

Il existe deux façons de créer un modèle dans le gestionnaire de conformité. Vous pouvez copier un modèle existant ou importer des données de modèle à partir d’une feuille de calcul Excel dans un nouveau modèle. À partir de votre page **modèles** , sélectionnez **Ajouter un modèle** pour créer un nouveau modèle en saisissant un nom, en sélectionnant dimensions et en téléchargeant un fichier Excel avec un format et un schéma spécifiques. Vous pouvez aussi activer la case à cocher **copier à partir d’un modèle existant** , sélectionner un modèle à copier et vérifier les dimensions, comme illustré dans l’image ci-dessous. La personnalisation de votre modèle nécessite un [processus en plusieurs étapes](working-with-compliance-manager.md#templates) , qui commence par la sélection de l’option **Ajouter un contrôle personnalisé** après la création de votre modèle.

![Score de conformité-tableau de bord](../media/compliance-score-template-update-old.png "Processus de copie de modèle actuel")

### <a name="whats-changing"></a>Nouveautés

Nous allons faciliter la création de nouveaux modèles. Dans le processus d' **extension** en une étape, vous pouvez ajouter une feuille de calcul avec vos actions et contrôles à un modèle Microsoft existant pour créer votre propre version personnalisée. Dans le volet flyout de **modèle** , activez la case à cocher **créer une extension à partir du modèle global** , comme indiqué dans l’image ci-dessous. Vous ajouterez ensuite des personnalisations à l’aide d’un nouveau format Excel moins complexe que celui actuel. Ce nouveau processus remplace la **copie actuelle d’un modèle existant** et ajoute des fonctions de **contrôle personnalisé** .

Chaque fois que l’évaluation d’origine est mise à jour via le processus de gestion des versions décrit ci-dessous, votre évaluation personnalisée hérite de ces mises à jour et conserve vos contrôles personnalisés.

Nous simplifions également la modification de vos propres modèles existants. Vous pouvez exporter votre modèle, apporter des modifications dans le même classeur, puis l’importer avec vos modifications enregistrées.

![Score de conformité-tableau de bord](../media/compliance-score-template-update-new.png "Processus de création d’un nouveau modèle")

## <a name="versioning-notice-and-control"></a>Notification et contrôle de version

Votre organisation recevra des évaluations mises à jour dans la prochaine version du score de conformité et du gestionnaire de conformité pour vous aider à vous aligner sur les mises à jour de certification et de réglementation.

À l’avenir, lorsqu’une mise à jour est disponible pour le modèle d’une évaluation ou une action d’amélioration, une icône d’alerte vous signale qu’une mise à jour est prête. Lorsque vous cliquez sur cette icône, une fenêtre contextuelle explique la mise à jour et vous invite à accepter. Voici un exemple d’alerte de contrôle de version pour une évaluation :

![Score de conformité-alerte de contrôle de version](../media/compliance-score-assessment-version.png "Alerte de mise à jour de version d’évaluation")

La sélection de l’icône d’alerte révèle un volet flyout expliquant la mise à jour et vous invitant à accepter les éléments suivants :

![Score de conformité-menu volant de gestion des versions](../media/compliance-score-assessment-version-accept.png "Volet de confirmation de mise à jour d’évaluation")

## <a name="common-actions-will-synch-status-across-groups"></a>Les actions courantes synchronisent l’état entre les groupes

Si votre organisation dispose de plusieurs groupes d’évaluations, le comportement des actions **techniques** (c’est-à-dire, des actions affectant l’ensemble de votre organisation) est modifié. Toutes les actions dupliquées entre les groupes seront regroupées en une seule action. Cette action unique contiendra toutes les notes téléchargées et les preuves des versions en double. Avec cette modification, les actions techniques se comporteront comme si elles appartenaient au même groupe. Toutes les modifications apportées à l’action dans un groupe ou une évaluation apparaissent maintenant dans toutes les instances. L' **État**de l’implémentation, les **fichiers DAT d’implémentation**, l' **État des tests**et la date de **test**reflètent les mises à jour les plus récentes.

## <a name="language-support"></a>Prise en charge linguistique

Le score de conformité sera désormais disponible dans les langues suivantes, en plus de l’anglais : chinois (simplifié), chinois (traditionnel), français, allemand, italien, japonais, coréen, portugais (Brésil), russe et espagnol.
