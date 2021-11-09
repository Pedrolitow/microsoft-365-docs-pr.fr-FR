---
title: Créer et afficher des exceptions pour les recommandations de sécurité - Gestion des menaces et des vulnérabilités
description: Créez et surveillez les exceptions pour les recommandations de sécurité Gestion des menaces et des vulnérabilités.
keywords: Correction tvm de Microsoft Defender pour les points de terminaison, Microsoft Defender pour endpoint tvm, Gestion des menaces et des vulnérabilités, & gestion des vulnérabilités contre les menaces, correction des menaces & gestion des vulnérabilités, correction tvm intune, tvm correction sccm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: b837199972f225a44406c7e18a57ae417363d15d
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2021
ms.locfileid: "60883472"
---
# <a name="create-and-view-exceptions-for-security-recommendations---threat-and-vulnerability-management"></a>Créer et afficher des exceptions pour les recommandations de sécurité - Gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Menaces et gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

En remplacement d’une demande de correction lorsqu’une recommandation n’est pas pertinente pour le moment, vous pouvez créer des exceptions pour les recommandations. Si votre organisation dispose de groupes d’appareils, vous serez en mesure d’étenduer l’exception à des groupes d’appareils spécifiques. Des exceptions peuvent être créées pour les groupes d’appareils sélectionnés ou pour tous les groupes d’appareils passés et présents.

Lorsqu’une exception est créée pour une recommandation, la recommandation n’est pas active avant la fin de la durée de l’exception. L’état de recommandation change en **Exception complète ou** Exception **partielle** (par groupe d’appareils).

## <a name="permissions"></a>Autorisations

Seuls les utilisateurs ayant des autorisations de « gestion des exceptions » peuvent gérer les exceptions (y compris la création ou l’annulation). [En savoir plus sur les rôles RBAC.](user-roles.md)

![Affichage de l’autorisation de gestion des exceptions.](images/tvm-exception-permissions.png)

## <a name="create-an-exception"></a>Créer une exception

Sélectionnez une recommandation de sécurité pour la création d’une exception, puis sélectionnez **Options d’exception** et remplissez le formulaire.

![Affichage de l’emplacement du bouton « options d’exception » dans un volant de recommandations de sécurité.](images/tvm-exception-options.png)

### <a name="exception-by-device-group"></a>Exception par groupe d’appareils

Appliquez l’exception à tous les groupes d’appareils actuels ou choisissez des groupes d’appareils spécifiques. Les groupes d’appareils futurs ne seront pas inclus dans l’exception. Les groupes d’appareils qui ont déjà une exception ne sont pas affichés dans la liste. Si vous sélectionnez uniquement certains groupes d’appareils, l’état de recommandation change de « actif » à « exception partielle ». L’état est « exception complète » si vous sélectionnez tous les groupes d’appareils.

![Affichage de la dropdown des groupes d’appareils.](images/tvm-exception-device-group-500.png)

#### <a name="filtered-views"></a>Affichages filtrés

Si vous avez filtré par groupe d’appareils sur l’une des pages Gestion des menaces et des vulnérabilités, seuls vos groupes d’appareils filtrés apparaîtront en tant qu’options.

Il s’agit du bouton à filtrer par groupe d’appareils sur l’une Gestion des menaces et des vulnérabilités pages suivantes :

![Affichage du filtre des groupes d’appareils sélectionnés.](images/tvm-selected-device-groups.png)

Affichage des exceptions avec groupes d’appareils filtrés :

![Affichage de la dropdown de groupe d’appareils filtré.](images/tvm-exception-device-filter500.png)

#### <a name="large-number-of-device-groups"></a>Grand nombre de groupes d’appareils

Si votre organisation compte plus de 20 groupes d’appareils, sélectionnez **Modifier** en plus de l’option de groupe d’appareils filtré.

![Montrant comment modifier un grand nombre de groupes.](images/tvm-exception-edit-groups.png)

Un volant s’affiche où vous pouvez rechercher et choisir les groupes d’appareils que vous souhaitez inclure. Sélectionnez l’icône de coche sous Recherche pour tout vérifier/décocher.

![Affichage du volant de groupe d’appareils de grande taille.](images/tvm-exception-device-group-flyout-400.png)

### <a name="global-exceptions"></a>Exceptions globales

Si vous avez des autorisations d’administrateur général, vous pourrez créer et annuler une exception globale. Elle affecte tous **les** groupes d’appareils actuels et futurs de votre organisation, et seul un utilisateur ayant des autorisations similaires peut le modifier. L’état de recommandation va changer de « actif » à « exception complète ».

![Affichage de l’option d’exception globale.](images/tvm-exception-global.png)

Voici quelques éléments à garder à l’esprit :

- Si une recommandation fait l’objet d’une exception globale, les exceptions nouvellement créées pour les groupes d’appareils sont suspendues jusqu’à ce que l’exception globale ait expiré ou ait été annulée. Après ce point, les nouvelles exceptions de groupe d’appareils entreront en vigueur jusqu’à leur expiration.
- Si une recommandation a déjà des exceptions pour des groupes d’appareils spécifiques et qu’une exception globale est créée, l’exception de groupe d’appareils est suspendue jusqu’à son expiration ou l’exception globale est annulée avant son expiration.

### <a name="justification"></a>Justification

Sélectionnez votre justification pour l’exception que vous devez déposer au lieu de corriger la recommandation de sécurité en question. Remplissez le contexte de justification, puis définissez la durée de l’exception.

La liste suivante détaille les justifications des options d’exception :

- **Contrôle tiers** - Un produit ou un logiciel tiers répond déjà à cette recommandation : le choix de ce type de justification réduit votre score d’exposition et augmente votre score de sécurité car votre risque est réduit
- **Atténuation de** remplacement : un outil interne répond déjà à cette recommandation : le choix de ce type de justification réduit votre score d’exposition et augmente votre score de sécurité car votre risque est réduit
- **Risque accepté :** pose un risque faible et/ou l’implémentation de la recommandation est trop coûteuse
- **Correction planifiée (grâce)** : déjà planifiée mais en attente d’exécution ou d’autorisation

## <a name="view-all-exceptions"></a>Afficher toutes les exceptions

Accédez à **l’onglet Exceptions** dans la page **Correction.** Vous pouvez filtrer par justification, type et état.

 Sélectionnez une exception pour ouvrir un volant avec plus de détails. Les exceptions par groupe d’appareils auront une liste de chaque groupe d’appareils couvert par l’exception, que vous pouvez exporter. Vous pouvez également afficher la recommandation associée ou annuler l’exception.

![Affichage de l’onglet « Exceptions » dans la page Correction.](images/tvm-exception-view.png)

## <a name="how-to-cancel-an-exception"></a>Comment annuler une exception

Pour annuler une exception, accédez à **l’onglet Exceptions** dans la page **Correction.** Sélectionnez l’exception.

Pour annuler l’exception pour tous les groupes d’appareils ou pour une exception globale, sélectionnez l’exception Annuler pour tous les groupes **d’appareils.** Vous pourrez uniquement annuler les exceptions pour les groupes d’appareils pour qui vous avez des autorisations.

![Bouton Annuler.](images/tvm-exception-cancel.png)

### <a name="cancel-the-exception-for-a-specific-device-group"></a>Annuler l’exception pour un groupe d’appareils spécifique

Sélectionnez le groupe d’appareils spécifique pour annuler l’exception. Un volant s’affiche pour le groupe d’appareils, et vous pouvez sélectionner **l’exception Annuler.**

![Montrant comment sélectionner un groupe d’appareils spécifique.](images/tvm-exception-device-group-hover.png)

## <a name="view-impact-after-exceptions-are-applied"></a>Afficher l’impact après application des exceptions

Dans la page Sécurité Recommandations,  sélectionnez Personnaliser les colonnes et cochez les cases pour les appareils exposés **(après les exceptions)** et **l’impact (après les exceptions).**

![Affichage des options de personnalisation des colonnes.](images/tvm-after-exceptions.png)

La colonne appareils exposés (après les exceptions) affiche les autres appareils qui sont encore exposés aux vulnérabilités après l’application des exceptions. Les justifications d’exception qui affectent l’exposition incluent « contrôle tiers » et « atténuation de remplacement ». D’autres justifications ne réduisent pas l’exposition d’un appareil et sont toujours considérées comme exposées.

L’impact (après les exceptions) indique l’impact restant sur le score d’exposition ou le score sécurisé après l’application des exceptions. Les justifications d’exception qui affectent les scores incluent « contrôle tiers » et « atténuation alternative ». D’autres justifications ne réduisent pas l’exposition d’un appareil, de sorte que le score d’exposition et le score de sécurité ne changent pas.

![Affichage des colonnes dans le tableau.](images/tvm-after-exceptions-table.png)

## <a name="related-topics"></a>Rubriques connexes

- [Vue d’ensemble gestion des vulnérabilités menaces et gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Corriger des vulnérabilités](tvm-remediation.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)
- [Score d'exposition](tvm-exposure-score.md)
- [Niveau de sécurité Microsoft pour les appareils](tvm-microsoft-secure-score-devices.md)
