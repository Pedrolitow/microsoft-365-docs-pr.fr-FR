---
title: 'Étape 13 : Surveiller l’activité de connexion et du client'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/01/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez l’accès Azure AD et le rapport d’utilisation.
ms.openlocfilehash: 997d52bc11036e1dbb7dcc6e1f9f48a59b2ddbf5
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866825"
---
# <a name="step-13-monitor-tenant-and-sign-in-activity"></a>Étape 13 : Surveiller l’activité de connexion et du client

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Dans cette étape, vous allez passer en revue les journaux d’audit et l’activité de connexion à l’aide des rapports Azure AD. Deux types de rapports sont disponibles.

Le **rapport d’activité des journaux d’audit** enregistre l’historique de toutes les tâches effectuées dans votre client Azure AD. Ce rapport répond aux questions telles que :

- Qui a ajouté une personne à un groupe d’administration ?
- Quels sont les utilisateurs qui se connectent à une application spécifique ?
- Combien de réinitialisations de mot de passe sont prévues ?

Le **rapport d’activité des connexions** enregistre l’auteur des tâches indiquées par le rapport des journaux d’audit. Ce rapport répond aux questions telles que :

- Pour un utilisateur spécifique à l’étude, quel est son modèle de connexion ?
- Quel est mon volume de connexions par jour, semaine ou mois ?
- Combien de ces tentatives de connexion n’ont pas abouti, et pour quels comptes ?

Pour plus d’informations sur les rapports et la façon d’y accéder, reportez-vous à la rubrique [Création de rapports Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-azure-portal).

Après cette étape, vous connaîtrez ces rapports et saurez comment les utiliser pour obtenir des informations sur les activités et événements Azure AD à des fins de planification et de sécurité.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step14.png)| [Autorisez les utilisateurs à créer et gérer leurs propres groupes](identity-self-service-group-management.md) |
