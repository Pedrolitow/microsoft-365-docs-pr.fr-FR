---
title: Notes de publication du score de conformité Microsoft
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
description: Notes de publication et problèmes connus pour le score de conformité Microsoft (aperçu), une fonctionnalité du centre de conformité M365 qui permet de simplifier et d’automatiser les évaluations des risques.
ms.openlocfilehash: 192519e323f9d23420f82a603979b50f4581ac4f
ms.sourcegitcommit: e2ed110c4c3a8434f9fcc9d610069bc77bc39220
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "38685875"
---
# <a name="microsoft-compliance-score-release-notes-preview"></a>Notes de publication du score de conformité Microsoft (aperçu)

La préversion publique du score de conformité Microsoft vous permet d’accéder en avant-première aux nouvelles fonctionnalités et mises à jour.

Le score de conformité est une nouvelle fonctionnalité du [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md) qui calcule un score basé sur les risques en mesurant la progression de l’exécution des actions recommandées qui permettent de réduire les risques de conformité.

## <a name="compliance-score-and-compliance-manager-relationship"></a>Relation avec le score de conformité et le gestionnaire de conformité

De nombreuses fonctions de conformité gérées dans le gestionnaire de conformité peuvent désormais être réalisées dans le score de conformité. Toutefois, certaines fonctionnalités se trouvent toujours dans le gestionnaire de conformité et certaines fonctionnalités antérieures dans le gestionnaire de conformité sont modifiées pendant la période d’évaluation publique. 

Gardez les points suivants à l’esprit lorsque vous utilisez le score de conformité et le gestionnaire de conformité lors de la préversion publique :

- **Gestion des évaluations**: les utilisateurs peuvent consulter les évaluations et leurs informations d’État dans le score de conformité. Toutefois, les utilisateurs peuvent uniquement effectuer des tâches de gestion d’évaluation dans le gestionnaire de conformité ([afficher les instructions](working-with-compliance-manager.md#assessments)) et des tâches, et sont limitées aux éléments suivants :
    - Télécharger de nouvelles évaluations, mais pas modifier les évaluations existantes. Si vous devez modifier une évaluation existante, vous devrez télécharger un nouveau modèle.
    - Exporter des évaluations
    - Archives d’archivage
    - Afficher les évaluations archivées
 - **Création de modèles pour les évaluations**: 
   - Les utilisateurs doivent accéder au gestionnaire de conformité pour créer de nouveaux modèles et exporter des modèles existants. 
   - Les modèles existants ne peuvent pas être personnalisés. Lisez les instructions relatives à [la gestion des modèles dans le gestionnaire de conformité](working-with-compliance-manager.md#templates).
   - Lors de la création d’un modèle, vous devez inclure des dimensions pour le **produit** et la **certification** afin de garantir l’affichage du modèle dans le score de conformité.
 - **Définition des autorisations**: le score de conformité les utilisateurs qui n’ont pas reçu précédemment des autorisations dans le gestionnaire de conformité doivent avoir leurs autorisations définies dans le centre de conformité Microsoft 365. Les utilisateurs dont les rôles ont été définis précédemment dans le gestionnaire de conformité peuvent utiliser ce même niveau d’accès lorsqu’ils travaillent sur le score de conformité.
- **Transfert de données**: les organisations dont les données résident dans le gestionnaire de conformité voient ces données dans le score de conformité, et inversement.
- **Connexion au gestionnaire de conformité à partir du score de conformité**: si un utilisateur est connecté à un score de conformité et sélectionne un lien pour accéder au gestionnaire de conformité, il n’a pas besoin de se reconnecter. Après avoir cliqué sur le lien, un nouvel onglet s’ouvre dans votre navigateur avec une boîte de dialogue. Dans la section supérieure avec l’en-tête «déjà un client des services Cloud Microsoft ? Connectez-vous à votre compte, «cliquez sur le bouton de **connexion** pour vous connecter automatiquement au gestionnaire de conformité.

## <a name="known-issues-in-compliance-score-preview"></a>Problèmes connus dans le score de conformité (aperçu)

Les sections suivantes couvrent les problèmes connus à résoudre dans les versions à venir du score de conformité.

### <a name="launch-now-links-in-certain-improvement-actions"></a>Lancer maintenant des liens dans certaines actions d’amélioration

Dans certaines actions d’amélioration, le fait de sélectionner le lien **lancer maintenant** qui apparaît sous les instructions d’implémentation génère une erreur. Pour accéder à la destination appropriée, qui est le centre d’administration SharePoint, procédez comme suit :

1. Accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
2. Dans le menu de navigation de gauche, sélectionnez **Afficher tout**.
3. Sous **centres d’administration,** sélectionnez **SharePoint**.

Vous trouverez ci-dessous les actions d’amélioration concernées, qui se trouvent dans la catégorie **protéger les informations** :
  - Appliquer le chiffrement à la bibliothèque SharePoint
  - Classer les données dans SharePoint Online
  - Configurer l’expiration des liens de partage externe
  - Activer le contrôle de version pour les bibliothèques de documents

### <a name="long-load-times-for-non-admin-users"></a>Temps de chargement long pour les utilisateurs non-administrateurs
Score de conformité les utilisateurs qui détiennent des rôles autres qu’un rôle d’administrateur peuvent avoir des temps de chargement longs lors de la tentative de connexion. L’actualisation de votre navigateur permet de résoudre ce problème. (En savoir plus sur les [rôles de score de conformité](compliance-score-setup.md#set-user-permissions-and-assign-roles).)

### <a name="supported-browsers"></a>Navigateurs pris en charge

- Les versions les plus récentes de Microsoft Edge, chrome et Safari sont prises en charge.
- Dans certaines circonstances, les données mises à jour ne s’affichent pas tant que votre navigateur n’est pas actualisé.
- La version d’évaluation de Microsoft Edge n’est pas prise en charge, mais n’a pas de problèmes connus.
- Internet Explorer n’est pas pris en charge.
 
### <a name="language-support"></a>Prise en charge linguistique

- Le score de conformité est uniquement disponible en anglais (États-Unis).