---
title: Journal d’audit de la gestion des risques internes
description: En savoir plus sur le journal d’audit de gestion des risques internes dans Microsoft Purview
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
ms.collection:
- tier1
- purview-compliance
ms.openlocfilehash: c1b381ed918f91b0334446117c4897eb3bfa0dd1
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68730906"
---
# <a name="insider-risk-management-audit-log"></a>Journal d’audit de la gestion des risques internes

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Le journal d’audit de gestion des risques internes vous permet de rester informé des actions effectuées sur les fonctionnalités de gestion des risques internes. Ce journal permet un examen indépendant des actions effectuées par les utilisateurs affectés à un ou plusieurs groupes de rôles de gestion des risques internes. Le journal d’audit de gestion des risques internes est automatiquement activé dans votre organisation et ne peut pas être désactivé.

![Journal d’audit de la gestion des risques internes.](../media/insider-risk-audit-log.png)

Le journal d’audit est automatiquement et immédiatement mis à jour chaque fois que des activités à risque identifiées sont détectées. Le journal d’audit conserve les informations pendant 180 jours (environ six mois). Après 180 jours, les données sont définitivement supprimées du journal.

Les domaines de détection des activités à risque identifiés sont les suivants :

- Politiques
- Cas
- Alertes
- Paramètres
- Utilisateurs
- Modèles de notifications

Pour afficher et exporter des données à partir du journal d’audit, les utilisateurs doivent être affectés aux groupes de rôles *Insider Risk Management* ou *Insider Risk Management Auditeurs* . Pour en savoir plus sur les groupes de rôles de gestion des risques internes, consultez [Prise en main de la gestion des risques internes Étape 1 : activation des autorisations](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management).

> [!NOTE]
> Le journal d’audit de gestion des risques internes n’est pas associé au journal d’audit Microsoft 365, car il s’agit de systèmes d’audit indépendants et de capture d’informations sur des domaines distincts. La désactivation de l’audit Microsoft 365 n’a pas d’impact sur l’audit des activités dans la gestion des risques internes.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="view-activity-in-the-insider-risk-audit-log"></a>Afficher l’activité dans le journal d’audit des risques internes

Pour afficher l’activité des fonctionnalités détectées pour la gestion des risques internes, accédez à et sélectionnez le lien **Journal d’audit des risques internes** dans la zone supérieure droite de l’onglet Gestion des risques internes. Par défaut, les informations suivantes s’affichent pour les activités de gestion des risques internes :

- **Activité:** Description de l’activité à risque identifiée prise dans la solution de gestion des risques internes par un utilisateur.
- **Catégorie:** Zone ou élément dans lequel l’activité à risque identifiée a été effectuée. Par exemple, vous verrez *Stratégies* comme catégorie lorsque des activités de modification de stratégie ont été effectuées.
- **Activité effectuée par :** Nom d’utilisateur de l’utilisateur qui a effectué l’activité à risque identifiée.
- **Date:** Date et heure à laquelle l’activité à risque identifiée a été effectuée. La date et l’heure correspondent à la date et à l’heure locales de votre organisation.

Pour plus d’informations sur une activité journalisée, sélectionnez l’activité pour afficher le volet détails de l’activité. Ce volet inclut des informations supplémentaires sur l’activité à risque identifiée.

## <a name="columns-and-filtering"></a>Colonnes et filtrage

Pour faciliter l’examen des journaux d’audit par les auditeurs, le filtrage est pris en charge dans le **journal d’audit des risques internes**. Pour le filtrage de base, des colonnes de file d’attente peuvent être ajoutées à la vue pour fournir différents tableaux croisés dynamiques sur les fichiers et les messages. Vous pouvez filtrer les activités à risque identifiées en fonction de la **catégorie, de la plage de dates** et **de l’activité effectuée par** les champs.

Pour ajouter ou supprimer des en-têtes de colonne pour la file d’attente, utilisez le contrôle **Personnaliser les colonnes** et sélectionnez parmi les options de colonne. Ces colonnes correspondent aux conditions courantes prises en charge dans le **journal d’audit des risques internes** et sont répertoriées plus loin dans cet article.

## <a name="audit-log-export"></a>Exportation du journal d’audit

Les utilisateurs affectés aux groupes de rôles *Gestion des risques internes* ou *Auditeurs de gestion des risques internes* peuvent exporter l’activité du journal d’audit vers un fichier .csv (valeurs séparées par des virgules) en sélectionnant **Exporter** dans la page **du journal d’audit des risques internes** . Selon l’activité du journal d’audit, certains champs peuvent ne pas être inclus dans la file d’attente filtrée. Par conséquent, ces champs apparaissent comme vides dans le fichier exporté.

Le fichier contient des informations sur l’activité du journal d’audit pour les champs suivants :

- **Activité effectuée par :** Nom de l’utilisateur qui modifie une valeur d’élément. Les utilisateurs répertoriés ici ont été affectés à un ou plusieurs des groupes de rôles de [gestion des risques internes](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management) suivants : *Gestion des risques internes*, *Administrateurs de gestion des risques internes, Analystes* de *gestion des risques* internes, *Enquêteurs en gestion des risques internes*. Chaque groupe de rôles a des niveaux d’autorisation différents pour la gestion des fonctionnalités de risque interne.
- **Activité:** Type d’activité effectuée sur un élément. Les valeurs sont *Affichage, Suppression, Ajout, Stratégie modifiée, Cas, Utilisateur, Alerte* et *Paramètres.*
- **Ajouté** : objets qui ont été ajoutés pendant l’activité à risque identifiée, tels que les utilisateurs, les types de fichiers ou les domaines.
- **Volume d’alerte** : niveau de volume d’alerte défini dans les paramètres de gestion des risques internes.
- **Montant** : montants d’indicateurs personnalisés actuellement sélectionnés pour une stratégie.
- **ID de** ressource : ID de ressource de la ressource physique prioritaire sur laquelle l’activité a été effectuée.
- **Catégorie:** Catégorie de l’élément modifié. Les valeurs sont *Les stratégies, les cas, les utilisateurs, les alertes, les paramètres* et les *modèles de notification.*
- **Date:** Date et heure, répertoriées dans la date et l’heure locales de votre organisation.
- **Description** : description entrée par l’utilisateur pour l’objet traité (par exemple, une stratégie ou un groupe d’utilisateurs prioritaire).
- **Stratégie DLP** : stratégie Protection contre la perte de données Microsoft Purview (DLP) sélectionnée pour déclencher l’inclusion dans une stratégie de gestion des risques internes.
- **Indicateur** : indicateur dans les paramètres de risque interne sur lequel l’activité a été effectuée (par exemple, l’ajout ou la suppression d’un indicateur).
- **Modèle de notification** : notez le modèle sur lequel l’activité à risque identifiée a été effectuée.
- **Nombre de jours** : fenêtre d’activation de stratégie définie dans les paramètres de risque interne.
- **Nombre de fichiers** : limite de volume de fichiers définie dans les paramètres de gestion des risques internes.
- **Modèle de stratégie** : modèle de stratégie auquel appartient les indicateurs qui ont agi.
- **Montant précédent** : montants d’indicateurs personnalisés précédemment sélectionnés pour une stratégie.
- **Groupe d’utilisateurs prioritaire** : groupe d’utilisateurs prioritaire sur lequel l’activité à risque identifiée a été effectuée.
- **Supprimé :** objets qui ont été supprimés pendant l’activité à risque identifiée, tels que les utilisateurs, les types de fichiers ou les domaines.
- **Expéditeur** : champ Expéditeur du modèle de notification sur lequel l’activité à risque identifiée a été effectuée.
- **Stratégie cible** : stratégie sur laquelle l’activité à risque identifiée a été effectuée (par exemple, l’ajout d’un utilisateur ou la suppression d’un utilisateur).
- **Corps du message de modèle** : corps du message du modèle de notification sur lequel l’activité à risque identifiée a été effectuée.
- **Objet du modèle** : champ objet du modèle d’avis sur lequel l’activité à risque identifiée a été effectuée.
- **Utilisateur:** Utilisateur sur lequel l’activité à risque identifiée a été effectuée.