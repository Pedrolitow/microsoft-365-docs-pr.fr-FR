---
title: 'Étape 6 : Utiliser des groupes pour faciliter la gestion'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Apprenez à configurer la gestion des groupes en libre-service Azure AD.
ms.openlocfilehash: 67c3a0e45fa253bdaedead03ac1137422ee0f8de
ms.sourcegitcommit: 66bb5af851947078872a4d31d3246e69f7dd42bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34073604"
---
# <a name="step-6-use-groups-for-easier-management"></a>Étape 6 : Utiliser des groupes pour faciliter la gestion

<a name="identity-self-service-groups"></a>
## <a name="allow-users-to-create-and-manage-their-own-groups"></a>Autoriser les utilisateurs à créer et gérer leurs propres groupes

*Cette étape facultative s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette section, vous allez identifier les groupes Azure Active Directory (Azure AD) qui peuvent être gérés par les propriétaires des groupes plutôt que par les administrateurs informatiques. Appelée *gestion de groupes en libre-service*, cette fonctionnalité permet aux propriétaires de groupes qui ne disposent d’aucun rôle administratif de créer et de gérer des groupes de sécurité. 

Les utilisateurs peuvent demander à appartenir à un groupe de sécurité. Cette demande est envoyée au propriétaire du groupe, et non à l’administrateur informatique. Ainsi, le contrôle quotidien de l’appartenance au groupe peut être délégué aux propriétaires d’équipes, de projets ou d’entreprises qui comprennent l’usage du groupe pour l’entreprise et peuvent gérer ses membres.

>[!Note]
>La gestion des groupes en libre-service est réservée aux groupes Office 365 et aux groupes de sécurité Azure AD. Elle n’est pas accessible aux groupes à extension messagerie, aux listes de distribution ou aux groupes synchronisés à partir de vos services AD DS (Active Directory Domain Services) locaux.
>

Pour plus d’informations, consultez les [instructions de configuration d’un groupe Azure AD pour la gestion en libre-service](https://docs.microsoft.com/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

Comme point de contrôle intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-self-service-groups) de cette section.

<a name="identity-dyn-groups"></a>
## <a name="set-up-dynamic-group-membership"></a>Configurer l’appartenance à un groupe dynamique

*Cette étape facultative s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette section, vous allez créer une série de règles permettant d’ajouter ou de supprimer automatiquement des comptes d’utilisateur en tant que membres d’un groupe Azure AD. C’est ce que l’on appelle l’*appartenance à un groupe dynamique*. Les règles sont basées sur les attributs du compte d’utilisateur, comme le département ou le pays.

Voici comment les règles sont appliquées :

- Si un compte d’utilisateur correspond à toutes les règles pour le groupe, il devient un membre.
- Si un compte d’utilisateur n’est pas membre du groupe, mais que ses attributs changent pour qu’il corresponde à toutes les règles pour le groupe, il devient un membre de ce groupe.
- Si un compte d’utilisateur ne correspond pas à toutes les règles pour le groupe, il n’est pas ajouté au groupe.
- Si un compte d’utilisateur est membre du groupe, mais que ses attributs changent pour qu’il ne corresponde plus à toutes les règles pour le groupe, il est supprimé comme membre du groupe.

Pour utiliser l’appartenance dynamique, vous devez commencer par déterminer les ensembles de groupes qui ont un ensemble commun d’attributs de compte d’utilisateur. Par exemple, tous les membres du service Ventes doivent être dans le groupe Ventes Azure AD, en fonction de l’attribut de compte d’utilisateur Service défini sur « Ventes ».

Reportez-vous aux [instructions pour créer et configurer les règles pour un groupe Azure AD dynamique](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

Les résultats de cette section sont les suivants :

- Un ensemble de groupes Azure AD qui peut être configuré pour l’appartenance dynamique
- Un ensemble de règles sur chaque groupe dynamique

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : Automatiser les licences et l’appartenance au groupe](automate-licenses-group-membership-microsoft-365-test-environment.md) |
|||

Comme point de contrôle intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-dyn-groups) de cette section.

<a name="identity-group-license"></a>
## <a name="set-up-automatic-licensing"></a>Configurer la gestion des licences automatique

*Cette étape facultative s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette section, vous allez configurer des groupes de sécurité dans Azure AD pour attribuer automatiquement les licences d’un ensemble d’abonnements à tous les membres du groupe. C’est ce que l’on appelle la *gestion des licences basée sur les groupes*. Si un compte d’utilisateur est ajouté ou supprimé du groupe, les licences des abonnements du groupe sont automatiquement attribuées ou supprimées du compte d’utilisateur.

Pour Microsoft 365 Entreprise, vous allez configurer des groupes de sécurité Azure AD pour affecter ces deux licences :

- Office 365 Entreprise E3 ou E5
- Enterprise Mobility + Security (EMS) E3 ou E5

Utilisez les groupes identifiés à l’Étape 2 pour rechercher les groupes qui contiennent une liste de comptes où tous les utilisateurs de ce groupe doivent avoir des licences Office 365 et EMS. Vérifiez que vous avez suffisamment de licences pour tous les membres du groupe. Si vous n’avez plus de licences, aucune licence ne sera attribuée aux nouveaux utilisateurs tant que d’autres licences ne sont pas disponibles.

>[!Note]
>Vous ne devez pas configurer la *gestion des licences par groupes* pour des groupes qui contiennent des comptes B2B Azure.
>

Consultez des informations supplémentaires dans la rubrique [Principes de base des licences basées sur les groupes dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal).

Consultez les [étapes pour configurer la gestion des licences par groupes pour un groupe de sécurité Azure](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).

Les résultats de cette section sont les suivants :

- Vous avez identifié les groupes de sécurité qui sont adaptés à la gestion des licences par groupes.
- Vous avez configuré ces groupes pour la gestion des licences par groupes.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : Automatiser les licences et l’appartenance au groupe](automate-licenses-group-membership-microsoft-365-test-environment.md) |
|||

Comme point de contrôle intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-group-license) de cette section.

## <a name="next-step"></a>Étape suivante

[ Identifier les critères de sortie de l’infrastructure](identity-exit-criteria.md)
