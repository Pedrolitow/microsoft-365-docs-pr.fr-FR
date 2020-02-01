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
ms.openlocfilehash: c3d0efbfcf58eb001d2df5832439c22c7cc662aa
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41595781"
---
# <a name="release-notes-for-compliance-manager-preview"></a>Notes de publication pour le gestionnaire de conformité (aperçu)

La préversion publique du gestionnaire de conformité vous permet d’accéder en avant-première aux fonctionnalités et mises à jour à venir.

Vous pouvez utiliser l’outil [Gestionnaire de conformité](https://servicetrust.microsoft.com/ComplianceManager) mis à jour sur le [portail d’approbation de service](https://servicetrust.microsoft.com) pour suivre, attribuer et vérifier les activités de conformité réglementaire liées aux services Cloud de Microsoft.

## <a name="whats-new-in-compliance-manager-preview"></a>Nouveautés du gestionnaire de conformité (aperçu)

- **Accès basé sur les rôles au gestionnaire de conformité :** Le rôle d' **accès invité** par défaut a été supprimé. Pour qu’un utilisateur puisse accéder au gestionnaire de conformité, l’administrateur global doit [attribuer une autorisation à chaque utilisateur](compliance-manager-overview.md#permissions).

- **Note de conformité mise à jour**: le score de conformité inclut désormais les scores pour les actions gérées par Microsoft. Votre score augmente en conséquence.

- **Éléments d’action :** Les éléments d’action sont maintenant des éléments individuels et de nombreux incluent une collection de télémétrie provenant de l’API graphique Microsoft Secure score. Dans la mesure du possible, les recommandations d’action technique ont maintenant des liens vers la page de configuration applicable dans le service Office 365.

- **Gestion des clients :** Nouvelle interface de gestion des nouveaux éléments de données dans le gestionnaire de conformité (aperçu) :
    - **Dimensions :** Afficher, ajouter et personnaliser des métadonnées pour des modèles, des évaluations et des éléments d’action qui vous permettent de créer des tableaux croisés dynamiques personnalisés pour les filtres.
    - **Propriétaires :** Spécifiez un propriétaire pour chaque élément d’action.
    - **Actions des clients :** Gérez la liste complète des éléments actions inclus dans le gestionnaire de conformité (Preview) et activez/désactivez la surveillance du score sécurisé pour les éléments d’action intégrés avec le score sécurisé.

## <a name="known-issues-in-compliance-manager-preview"></a>Problèmes connus dans le gestionnaire de conformité (aperçu)

Les sections suivantes couvrent les problèmes connus à résoudre dans les prochaines versions du gestionnaire de conformité.

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

### <a name="microsoft-managed-controls"></a>Contrôles gérés par Microsoft

- La date de test pour les contrôles gérés par Microsoft n’apparaît pas dans l’interface utilisateur, même si elle est incluse dans l’évaluation. Pour afficher les informations de date de test, vous devez exporter l’évaluation.

### <a name="customization"></a>Personnalisation

- L’ajout de contrôles personnalisés permet d’ajouter un nouveau contrôle à une famille de contrôle existante, mais il ne vous permet pas d’ajouter une nouvelle famille de contrôle.
- Cette version ne prend pas en charge la liaison d’éléments d’action ou l’ajout d’éléments d’action ou de contrôles à une évaluation.
- Si vous créez une action personnalisée, vous ne pouvez pas la modifier ou la supprimer.

### <a name="control-families-not-shown-in-assessments"></a>Familles de contrôle non affichées dans les évaluations

- Lorsque vous importez un modèle, toutes les évaluations basées sur ce modèle reflètent toutes les familles de contrôle qui font partie du modèle. Toutefois, si vous ajoutez de nouvelles familles de contrôle au modèle, les évaluations existantes ne refléteront pas les modifications. Seules les nouvelles évaluations créées à partir du modèle mis à jour reflètent les modifications.

### <a name="templates"></a>Modèles

- Lors de la création d’un modèle, vous devez inclure des dimensions pour le **produit** et la **certification** afin de garantir l’affichage du modèle dans le score de conformité.
- Les modèles archivés sont modifiables et ils ne doivent pas être modifiables.
- Les modèles verrouillés permettent la création d’une évaluation dès qu’ils ne le sont pas. Le verrouillage d’un modèle est destiné à empêcher son utilisation pour créer des évaluations.

### <a name="export"></a>Exporter

- L’exportation de modèle vers JSON échoue lorsque l’état du modèle est défini sur **importé** ou **en attente d’approbation**.

### <a name="supported-browsers"></a>Navigateurs pris en charge

- Les versions les plus récentes de Microsoft Edge, chrome et Safari sont prises en charge.
- Dans certaines circonstances, les données mises à jour ne s’affichent pas tant que votre navigateur n’est pas actualisé.
- La version d’évaluation de Microsoft Edge n’est pas prise en charge mais n’a pas de problèmes connus.
- Internet Explorer n’est pas pris en charge.

### <a name="session-timeout"></a>Délai d’expiration de session

- Lorsqu’une session arrive à expiration, une erreur « un problème est survenu » peut apparaître. Pour résoudre ce dernier, accédez au [Gestionnaire de conformité](https://servicetrust.microsoft.com/ComplianceManager) et reconnectez-vous.
 
### <a name="language-support"></a>Prise en charge linguistique

- Toutes les langues ne sont pas prises en charge pour toutes les pages Web. Si votre langue locale n’est pas prise en charge, affichez-la en anglais (États-Unis).