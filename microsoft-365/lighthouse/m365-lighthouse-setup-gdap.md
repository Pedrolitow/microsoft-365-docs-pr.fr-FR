---
title: Configurer GDAP pour vos clients
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: magarlan, chrigreen
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment configurer GDAP pour vos clients.
ms.openlocfilehash: b7baa473b19c2431edf1f5e85c9f106cc60e962d
ms.sourcegitcommit: 0ad7edcfdcdd11d02fa8a14ffe4b36e120d92deb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2022
ms.locfileid: "68785898"
---
# <a name="set-up-gdap-for-your-customers"></a>Configurer GDAP pour vos clients


> [!NOTE]
> Cette fonctionnalité est déployée à des vitesses différentes pour nos clients. Si vous ne voyez pas encore cette fonctionnalité, vous devriez la voir bientôt.

Les partenaires intégrés à Microsoft 365 Lighthouse peuvent désormais configurer tous leurs clients avec des privilèges d’administration délégués granulaires (GDAP) via Lighthouse, quelle que soit leur licence ou leur taille. Lighthouse permet aux partenaires de migrer rapidement leur organisation vers GDAP et de commencer la transition vers les privilèges minimum pour leur accès délégué aux clients. En configurant votre organisation avec GDAP pour les locataires clients que vous gérez, les utilisateurs de votre organisation disposent des autorisations nécessaires pour effectuer leur travail tout en assurant la sécurité des locataires clients.

L’accès délégué via DAP ou GDAP est un prérequis pour que les clients soient entièrement intégrés à Lighthouse. Par conséquent, la création de relations GDAP peut être la première étape de la gestion de vos clients dans Lighthouse.

Pendant le processus de configuration GDAP, vous allez attribuer des rôles à des niveaux de fonctions de travail pour les employés de votre organisation, puis créer des modèles GDAP qui attribueront ces rôles hiérarchisé à des groupes de sécurité spécifiques avec des utilisateurs pour des groupes de clients. Les rôles GDAP sont limités aux [rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference). Lorsque vous configurez GDAP, vous verrez des recommandations pour un ensemble de rôles nécessaires pour chaque niveau.

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez disposer d’autorisations spécifiques dans votre propre locataire :

  - Pour établir des groupes de sécurité GDAP et ajouter des utilisateurs, vous devez disposer d’un administrateur général, d’un administrateur d’utilisateurs ou d’un administrateur de groupes pour configurer des utilisateurs disposant d’un accès permanent aux rôles GDAP. Vous pouvez attribuer ces rôles dans Azure Active Directory (ADD).

    - Pour activer le niveau juste-à-temps (JIT) uniquement, vous devez disposer d’un administrateur général ou d’une combinaison d’administrateur d’utilisateur et d’administrateur de rôle de privilège.

  - Pour créer et compléter des relations GDAP, vous devez être membre du groupe Agents Administration dans l’Espace partenaires.

- Tout client peut être géré par un partenaire Lighthouse, s’il est configuré dans l’Espace partenaires avec une relation de revendeur ou une relation déléguée existante (DAP ou GDAP).

- Pour activer les autorisations de niveau JIT uniquement, vous avez également besoin d’une licence Azure AD P2.

## <a name="set-up-gdap-for-the-first-time"></a>Configurer GDAP pour la première fois

Lorsque vous configurez GDAP pour la première fois, vous devez suivre les sections suivantes dans l’ordre. Une fois que vous avez terminé, vous pouvez revenir et modifier n’importe quelle section si nécessaire.

Pour commencer :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Accueil.**

2. Dans la carte **Configurer GDAP pour votre organisation** , sélectionnez **Commencer l’installation.**

3. Suivez les sections suivantes dans l’ordre.

    [Étape 1 : Définir les niveaux d’autorisations](#step-1-define-tiers-of-permissions)

    [Étape 2 : Créer des modèles GDAP](#step-2-create-gdap-templates)

    [Étape 3 : Créer des groupes de sécurité](#step-3-create-security-groups)

    [Étape 4 : Attribuer des locataires client](#step-4-assign-customer-tenants)

    [Étape 5 : Passer en revue les paramètres](#step-5-review-settings)

### <a name="step-1-define-tiers-of-permissions"></a>Étape 1 : Définir les niveaux d’autorisations

Choisissez les rôles nécessaires pour chaque niveau en fonction des fonctions de travail de vos employés.

1. Dans la page **Définir les niveaux d’autorisations** , sélectionnez les rôles nécessaires pour chaque niveau en fonction des fonctions de travail de vos employés. Vous pouvez

    - Adoptez les configurations recommandées, ou

    - Attribuez manuellement un rôle à chaque niveau.

2. Sélectionnez **Suivant** pour accéder à la section suivante ou sélectionnez **Enregistrer et fermer** pour enregistrer vos paramètres et quitter le programme d’installation GDAP.

Vous pouvez renommer les niveaux en fonction des besoins de votre organisation. Vous pouvez supprimer des rôles de chaque niveau dans les recommandations. Certains rôles ne peuvent pas être ajoutés à différents niveaux. Par exemple, les rôles du niveau JIT uniquement ne peuvent pas être ajoutés à un autre niveau.

### <a name="step-2-create-gdap-templates"></a>Étape 2 : Créer des modèles GDAP

Un modèle GDAP est une collection de :

- Niveaux avec rôles

- Groupes de sécurité par niveau

- Utilisateurs de chaque groupe de sécurité
 
Pour créer un modèle GDAP :

1. Dans la page **Créer des modèles GDAP** , sélectionnez **Créer un modèle**.

2. Dans le volet modèle, entrez le nom et la description du modèle dans les champs appropriés.

3. Sélectionnez un ou plusieurs niveaux dans la liste.

4. Sélectionnez **Enregistrer**.

5. Sélectionnez **Suivant** pour accéder à la section suivante, ou sélectionnez **Enregistrer et fermer** pour enregistrer vos paramètres et quitter le programme d’installation GDAP.

### <a name="step-3-create-security-groups"></a>Étape 3 : Créer des groupes de sécurité

Vous aurez besoin d’au moins un groupe de sécurité par niveau pour chaque modèle. Pour le premier modèle, vous allez créer un groupe de sécurité, mais sur les modèles suivants, vous pouvez réutiliser des groupes si vous le souhaitez.

1. Dans la page **Créer des groupes de sécurité** , sélectionnez **Créer un groupe de sécurité**.

2. Dans le volet groupe de sécurité, entrez le nom et la description.

3. Sélectionnez **Ajouter des utilisateurs**.

4. Dans la liste Ajouter des utilisateurs, sélectionnez les utilisateurs que vous souhaitez inclure dans ce groupe de sécurité.

5. Sélectionnez **Enregistrer.**

6. Sélectionnez **Enregistrer** à nouveau.

7. Sélectionnez **Suivant** pour accéder à la section suivante ou sélectionnez **Enregistrer et fermer** pour enregistrer vos paramètres et quitter le programme d’installation GDAP.

### <a name="step-4-assign-customer-tenants"></a>Étape 4 : Attribuer des locataires client

Affectez des groupes de clients à chaque modèle. Chaque client ne peut être affecté qu’à un seul modèle, de sorte qu’une fois sélectionné, ce locataire client n’est pas affiché en tant qu’option sur les modèles suivants.

Si vous souhaitez réaffecter un locataire client, réexécutez le programme d’installation GDAP et désélectionnez ce client de l’affectation existante. Vous pouvez ensuite le réaffecter à un autre modèle. Vous pouvez filtrer la liste à l’aide de la zone de recherche dans le coin supérieur droit.

1. Dans la page **Affecter des locataires clients** , sélectionnez les locataires que vous souhaitez associer au groupe de sécurité que vous avez créé.

2. Sélectionnez **Suivant** pour accéder à la section suivante ou sélectionnez **Enregistrer et fermer** pour enregistrer vos paramètres et quitter le programme d’installation GDAP.

### <a name="step-5-review-settings"></a>Étape 5 : Passer en revue les paramètres

1. Dans la page **Vérifier les paramètres** , passez en revue les paramètres que vous avez créés, puis sélectionnez **Terminer.**

2. Sélectionnez **Terminé.**

Si des locataires clients avaient déjà une relation DAP, pendant la fenêtre sans consentement, ces paramètres sont automatiquement appliqués. Pour les clients sans DAP, ou si la fenêtre d’absence de consentement s’est fermée, choisir **Terminer** vous permet d’accéder à la dernière page où des liens de consentement sont générés pour chaque client en fonction des besoins. Une fois que le client a donné son consentement à la relation GDAP, les autres paramètres sont automatiquement appliqués.

Une fois que vous avez terminé la configuration GDAP, vous pouvez accéder à différentes étapes pour effectuer des mises à jour ou des modifications de niveaux, de rôles, de groupes de sécurité ou de modèles. Les relations GDAP seront également visibles dans l’Espace partenaires, et les groupes de sécurité seront également visibles dans Azure AD.

## <a name="related-content"></a>Contenu associé

[Vue d’ensemble des autorisations](m365-lighthouse-overview-of-permissions.md) (article)\
[Configurer la sécurité du portail](m365-lighthouse-configure-portal-security.md) (article)\
[Présentation des privilèges d’administrateur délégué granulaires (GDAP)](/partner-center/gdap-introduction) (article)\
[Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference) (article)\
[En savoir plus sur les groupes et les droits d’accès dans Azure Active Directory](/azure/active-directory/fundamentals/concept-learn-about-groups) (article)\
[Qu’est-ce que la gestion des droits d’utilisation Azure AD ?](/azure/active-directory/governance/entitlement-management-overview) (article)