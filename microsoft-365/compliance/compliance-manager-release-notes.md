---
title: Notes de publication du gestionnaire de conformité Microsoft
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
description: Le gestionnaire de conformité Microsoft est un outil d’évaluation des risques gratuit basé sur un flux de travail dans le portail d’approbation de service Microsoft. Le gestionnaire de conformité vous permet de suivre, d’affecter et de vérifier les activités de conformité réglementaire liées aux services Cloud de Microsoft.
ms.openlocfilehash: 3e710f83bebd94719ef66cde7844f1301611adf4
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43637534"
---
# <a name="microsoft-compliance-manager-preview-release-notes"></a>Notes de publication du gestionnaire de conformité Microsoft (version préliminaire)

La préversion publique du gestionnaire de conformité vous permet d’accéder en avant-première aux fonctionnalités et mises à jour à venir. Cette page contient des mises à jour sur les nouvelles fonctionnalités, des fonctionnalités améliorées et des problèmes connus avec la version actuelle.

Vous pouvez utiliser l’outil [Gestionnaire de conformité](https://servicetrust.microsoft.com/ComplianceManager) sur le portail d’approbation de [service](https://servicetrust.microsoft.com) pour suivre, attribuer et vérifier les activités de conformité réglementaire liées aux services Cloud de Microsoft.

## <a name="improved-template-creation-and-update-process"></a>Amélioration du processus de création et de mise à jour des modèles

Nous avons mis à jour le processus d’importation, d’exportation et de modification des modèles pour les évaluations. La nouvelle expérience simplifiée vous permettra d’apporter plus facilement vos propres évaluations à votre flux de travail et de les maintenir à jour.

### <a name="the-old-process"></a>Ancien processus

Il existe deux façons de créer un modèle dans le gestionnaire de conformité. Vous pouvez copier un modèle existant ou importer des données de modèle à partir d’une feuille de calcul Excel dans un nouveau modèle. À partir de votre page **modèles** , sélectionnez **Ajouter un modèle** pour créer un nouveau modèle en saisissant un nom, en sélectionnant dimensions et en téléchargeant un fichier Excel avec un format et un schéma spécifiques. Vous pouvez également activer la case à cocher **copier à partir d’un modèle existant** , sélectionner un modèle à copier et vérifier les dimensions. Personnalisation de la conception votre modèle nécessite un processus en plusieurs étapes qui a commencé en sélectionnant **Ajouter un contrôle personnalisé** après la création de votre modèle.

### <a name="the-new-process"></a>Le nouveau processus

Nous avons facilité la création de nouveaux modèles. Dans le processus d' **extension** en une étape, vous pouvez ajouter une feuille de calcul avec vos actions et contrôles à un modèle Microsoft existant pour créer votre propre version personnalisée. Sur la page des **modèles** dans le gestionnaire de conformité, sélectionnez **+ Ajouter un modèle**. Dans le volet flyout de **modèle** , activez la case à cocher **créer une extension à partir du modèle global** . Vous pouvez ajouter des personnalisations avec un nouveau format Excel moins complexe que le précédent. Ce nouveau processus remplace l’ancienne **copie à partir d’un modèle existant** et ajoute des fonctions de **contrôle personnalisé** .

Chaque fois que l’évaluation d’origine est mise à jour via le processus de gestion des versions décrit ci-dessous, votre évaluation personnalisée hérite de ces mises à jour et conserve vos contrôles personnalisés.

Il est également plus facile de modifier vos propres modèles existants. Vous pouvez exporter votre modèle, apporter des modifications dans le même classeur, puis l’importer avec vos modifications enregistrées.

Affichez les instructions détaillées sur la [création de modèles](working-with-compliance-manager.md#templates) avec ce nouveau processus.

## <a name="versioning-notice-and-control"></a>Notification et contrôle de version

Votre organisation a reçu des évaluations mises à jour dans la version d’avril 2020 du gestionnaire de conformité afin de vous aider à vous aligner sur les mises à jour de certification et de réglementation. À l’avenir, nous vous fournirons une façon claire de comprendre et d’accepter toutes les futures mises à jour via des **alertes de gestion des versions**.

Lorsqu’une mise à jour est disponible pour le modèle d’une évaluation ou une action d’amélioration, une icône d’alerte vous signale qu’une mise à jour est prête. Lorsque vous cliquez sur cette icône, une fenêtre contextuelle explique la mise à jour et vous invite à accepter. La sélection de l’icône d’alerte révèle un volet flyout expliquant la mise à jour et vous invitant à accepter. En savoir plus sur l' [acceptation de mises à jour pour les évaluations](working-with-compliance-manager.md#versioning-alerts-for-assessment-updates).

## <a name="common-actions-will-synch-status-across-groups"></a>Les actions courantes synchronisent l’état entre les groupes

Si votre organisation dispose de plusieurs groupes d’évaluations, le comportement des actions **techniques** (c’est-à-dire, des actions affectant l’ensemble de votre organisation) a changé. Toutes les actions dupliquées entre les groupes ont été regroupées en une seule action. Cette action unique contient toutes les notes et preuves téléchargées des versions en double. Avec cette modification, les actions techniques se comporteront désormais comme lorsqu’elles appartenaient au même groupe. Toutes les modifications apportées à l’action dans un groupe ou une évaluation apparaissent maintenant dans toutes les instances. L' **État de mise en œuvre**, la **Date de mise en œuvre**, l' **État du test**et la **Date de test** reflètent les mises à jour les plus récentes.

## <a name="language-support"></a>Prise en charge linguistique

Le gestionnaire de conformité est désormais disponible dans les langues suivantes, en plus de l’anglais : chinois (simplifié), chinois (traditionnel), français, allemand, italien, japonais, coréen, portugais (Brésil), russe et espagnol.

## <a name="known-issues-in-compliance-manager-preview"></a>Problèmes connus dans le gestionnaire de conformité (aperçu)

La section suivante décrit les problèmes connus dans la version actuelle du gestionnaire de conformité.

### <a name="compliance-score"></a>Score de conformité

- Pour les éléments d’action marqués comme **n’appartenant pas à l’étendue**, le score attribué à l’action n’est pas exclu du calcul du score de conformité. Les éléments d’action marqués **n’augmentent pas** votre score de conformité.

### <a name="secure-score"></a>Degré de sécurisation

- Les résultats du score de sécurité ne sont pas disponibles pour certaines actions dans certains abonnements Microsoft 365 et Office 365. Le résultat du score de sécurité n’a **pas pu être détecté** dans les cas suivants.
- Parfois, les résultats de la fonction de chiffrement sécurisé sont renvoyés pour les stratégies et les éléments d’action non terminés.
- Pour les nouveaux clients, les mises à jour du score de sécurité pour toutes les actions sont automatiquement activées. L’administrateur général peut définir le commutateur de mise à jour continue du score de sécurité sur désactivé, ce qui désactive les mises à jour pour toutes les actions.
  - **Remarque**: lorsque les organisations déploient pour la première fois Microsoft 365 ou Office 365, le score de sécurité requis pour collecter intégralement les données est d’environ sept jours et les évaluer dans votre score. Pendant ce temps, la définition du commutateur de mise à jour continue de score de sécurité sur **désactivé** et la définition manuelle d’une action sur **implémenté** compteront cette action vers votre score. Une fois les sept jours initiaux, l’activation de la mise à jour continue du score sécurisé active la surveillance continue à partir de ce moment-là.
- Lorsque les mises à jour du score sécurisé sont activées, les actions sont activement surveillées par le score sécurisé, bien que la date de test de l’action ne soit pas mise à jour pour refléter la surveillance.
- Lors de la création d’évaluations, les scores incluent automatiquement les scores de contrôle gérés par Microsoft et l’intégration de la note de sécurité.
- Toutes les actions qui ne sont pas prises en charge par l’intégration de la note sécurisée peuvent être implémentées manuellement. Une implémentation manuelle concerne le score du groupe de cette action.

### <a name="export"></a>Exporter

- L’exportation de modèle vers JSON échoue lorsque l’état du modèle est défini sur **importé** ou **en attente d’approbation**.

### <a name="supported-browsers"></a>Navigateurs pris en charge

- Les versions les plus récentes de Microsoft Edge, chrome et Safari sont prises en charge.
- Dans certaines circonstances, les données mises à jour ne s’affichent pas tant que votre navigateur n’est pas actualisé.
- La version d’évaluation de Microsoft Edge n’est pas prise en charge mais n’a pas de problèmes connus.
- Internet Explorer n’est pas pris en charge.

### <a name="session-timeout"></a>Délai d’expiration de session

- Lorsqu’une session arrive à expiration, une erreur « un problème est survenu » peut apparaître. Pour résoudre ce dernier, accédez au [Gestionnaire de conformité](https://servicetrust.microsoft.com/ComplianceManager) et reconnectez-vous.
