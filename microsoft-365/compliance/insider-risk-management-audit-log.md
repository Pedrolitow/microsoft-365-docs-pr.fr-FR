---
title: Journal d’audit de la gestion des risques internes
description: En savoir plus sur le journal d’audit de la gestion des risques internes dans Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: a671e25dabf5dc9c526e6e3a931a71035b908cc3
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787823"
---
# <a name="insider-risk-management-audit-log"></a>Journal d’audit de la gestion des risques internes

Le journal d’audit de la gestion des risques internes vous permet de rester informé des actions prises sur les fonctionnalités de gestion des risques internes. Ce journal permet un examen indépendant des actions effectuées par les utilisateurs affectés à un ou plusieurs groupes de rôles de gestion des risques internes. Le journal d’audit de la gestion des risques internes est automatiquement activé dans votre organisation et ne peut pas être désactivé.

![Journal d’audit de la gestion des risques internes.](../media/insider-risk-audit-log.png)

Le journal d’audit est automatiquement et immédiatement mis à jour chaque fois que des activités détectées se produisent et le journal conserve des informations sur l’activité pendant 180 jours (environ six mois). Après 180 jours, les données de l’activité sont définitivement supprimées du journal.

Les zones incluses dans la détection d’activité sont les suivantes :

- Stratégies
- Cas
- Alertes
- Paramètres
- Utilisateurs
- Modèles de notifications

Pour afficher et exporter des données à partir du journal d’audit, les utilisateurs doivent être affectés aux groupes de rôles *Insider Risk Management* ou *Insider Risk Management Auditors* . Pour en savoir plus sur les groupes de rôles de gestion des risques internes, consultez [Prise en main de la gestion des risques internes Étape 1 : Activation des autorisations](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management).

> [!NOTE]
> Le journal d’audit de gestion des risques internes n’est pas associé au journal d’audit Microsoft 365. Il s’agit de systèmes d’audit indépendants et de capture d’informations sur des activités distinctes. La désactivation de l’audit Microsoft 365 n’a pas d’impact sur l’audit des activités au sein de la gestion des risques internes.

## <a name="view-activity-in-the-insider-risk-audit-log"></a>Afficher l’activité dans le journal d’audit des risques internes

Pour afficher l’activité de fonctionnalité détectée pour la gestion des risques internes, accédez au lien du **journal d’audit des risques internes** et sélectionnez-le dans la zone supérieure droite de l’onglet Gestion des risques internes. Par défaut, les informations suivantes s’affichent pour les activités de gestion des risques internes :

- **Activité:** Description de l’activité effectuée dans la solution de gestion des risques internes par un utilisateur.
- **Catégorie:** Zone ou élément où l’activité a été effectuée. Par exemple, vous verrez *Stratégies* comme catégorie lors de l’exécution d’activités de modification de stratégie.
- **Activité effectuée par :** Nom d’utilisateur de l’utilisateur qui a effectué l’activité.
- **Date:** Date et heure d’exécution de l’activité. La date et l’heure correspondent à la date et à l’heure locales de votre organisation.

Pour plus d’informations sur une activité journalisée, sélectionnez l’activité pour afficher le volet des détails de l’activité. Ce volet inclut des informations supplémentaires sur l’activité.

## <a name="columns-and-filtering"></a>Colonnes et filtrage

Pour faciliter l’examen de l’activité journalisée par les auditeurs, le filtrage est pris en charge dans le **journal d’audit des risques internes**. Pour le filtrage de base, des colonnes de file d’attente sont disponibles à ajouter à la vue pour fournir différents tableaux croisés dynamiques sur les fichiers et les messages. Vous pouvez filtrer les activités par **catégorie, plage de dates** et **activité effectuées par** champs.

Pour ajouter ou supprimer des en-têtes de colonne pour la file d’attente d’activités, utilisez le contrôle **Personnaliser les colonnes** et sélectionnez-le dans les options de colonne. Ces colonnes correspondent aux conditions courantes prises en charge dans le **journal d’audit des risques internes** et sont répertoriées plus loin dans cet article.

## <a name="audit-log-export"></a>Auditer l’exportation du journal

Les utilisateurs affectés aux groupes de rôles *Insider Risk Management* ou *Insider Risk Management Auditors* peuvent exporter toutes les activités du journal d’audit vers un fichier .csv (valeurs séparées par des virgules) en sélectionnant **Exporter** dans la page du **journal d’audit des risques Insider** . Selon l’activité, certains champs d’une activité peuvent ne pas s’appliquer à l’activité et ces champs apparaissent comme vides dans le fichier exporté.

Le fichier contient des informations d’activité pour les champs suivants :

- **Activité effectuée par :** Nom d’utilisateur de l’utilisateur qui modifie une valeur d’élément. Les utilisateurs répertoriés ici ont été affectés à un ou plusieurs des groupes de rôles de [gestion des risques internes](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management) suivants : *Insider Risk Management*, *Insider Risk Management Admins*, *Insider Risk Management Analysts*, *Insider Risk Management Investigators*. Chaque groupe de rôles a des niveaux d’autorisation différents pour la gestion des fonctionnalités de risque interne.
- **Activité:** Activité effectuée sur un élément. Les valeurs sont *Affichées, Supprimées, Ajoutées, Modifiées, Cas, Utilisateur, Alerte* et *Paramètres.*
- **Ajouté** : objets qui ont été ajoutés pendant l’activité, tels que les utilisateurs, les types de fichiers ou les domaines.
- **Volume d’alerte** : niveau de volume d’alerte défini dans les paramètres de gestion des risques internes.
- **Montant** : montants de l’indicateur personnalisé actuellement sélectionné pour une stratégie.
- **ID de** ressource : ID de ressource de la ressource physique de priorité sur laquelle l’activité a été effectuée.
- **Catégorie:** Catégorie de l’élément modifié. Les valeurs sont *les modèles Stratégies, Cas, Utilisateurs, Alertes, Paramètres* et *Avis.*
- **Date:** Date et heure, répertoriées dans la date et l’heure locales de votre organisation.
- **Description** : entrée de description par l’utilisateur pour l’objet sur lequel il agit (par exemple, une stratégie ou un groupe d’utilisateurs prioritaire).
- **Stratégie DLP** : stratégie Protection contre la perte de données Microsoft Purview (DLP) sélectionnée pour déclencher l’inclusion dans une stratégie de gestion des risques internes.
- **Indicateur** : indicateur dans les paramètres de risque interne sur lequel l’activité a été effectuée (par exemple, l’ajout ou la suppression d’un indicateur).
- **Modèle de notification** : modèle d’avis sur lequel l’activité a été effectuée.
- **Nombre de jours** : fenêtre d’activation de stratégie définie dans les paramètres de risque interne.
- **Nombre de fichiers** : limite de volume de fichiers définie dans les paramètres de gestion des risques internes.
- **Modèle de** stratégie : le modèle de stratégie auquel les indicateurs ont agi appartient.
- **Montant précédent** : les montants d’indicateur personnalisé précédemment sélectionnés pour une stratégie.
- **Groupe d’utilisateurs prioritaire** : groupe d’utilisateurs prioritaire sur lequel l’activité a été effectuée.
- **Supprimé** : objets qui ont été supprimés pendant l’activité, tels que les utilisateurs, les types de fichiers ou les domaines.
- **Expéditeur** : champ expéditeur du modèle d’avis sur lequel l’activité a été effectuée.
- **Stratégie cible** : stratégie sur lequel l’activité a été effectuée (par exemple, ajout d’un utilisateur ou suppression d’un utilisateur).
- **Corps du message de** modèle : corps du message du modèle d’avis sur lequel l’activité a été effectuée.
- **Objet du modèle** : champ objet du modèle d’avis sur lequel l’activité a été effectuée.
- **Utilisateur:** Utilisateur sur lequel l’activité a été effectuée.
