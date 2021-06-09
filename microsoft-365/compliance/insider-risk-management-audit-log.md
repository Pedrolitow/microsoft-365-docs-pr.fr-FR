---
title: Journal d’audit de la gestion des risques internes
description: En savoir plus sur le journal d’audit de la gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: bda9633ab37fd21fd66b3a8a53d4dd522e48ced1
ms.sourcegitcommit: 8b1bd7ca8cd81e4270f0c1e06d2b6ca81804a6aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2021
ms.locfileid: "50820272"
---
# <a name="insider-risk-management-audit-log"></a>Journal d’audit de la gestion des risques internes

Le journal d’audit de la gestion des risques internes vous permet de rester informé des actions qui ont été prises sur les fonctionnalités de gestion des risques internes. Ce journal permet un examen indépendant des actions entreprises par les utilisateurs affectés à un ou plusieurs groupes de rôles de gestion des risques internes. Le journal d’audit de la gestion des risques internes est automatiquement activé dans votre organisation et ne peut pas être désactivé.

![Journal d’audit de la gestion des risques internes](../media/insider-risk-audit-log.png)

Le journal d’audit est automatiquement et immédiatement mis à jour chaque fois que des activités surveillées se produisent et que le journal conserve les informations sur l’activité pendant 180 jours (environ six mois). Après 180 jours, les données de l’activité sont définitivement supprimées du journal.

Les domaines inclus dans l’analyse des activités sont les suivants :

- Stratégies
- Cas
- Alertes
- Paramètres
- Utilisateurs
- Modèles de notifications

Pour afficher et exporter des données à partir du journal d’audit, les utilisateurs doivent être affectés aux groupes de rôles Insider *Risk Management* ou Insider Risk *Management Auditors.* Pour en savoir plus sur les groupes de rôles de gestion des risques internes, voir Prise en charge de la gestion des risques internes Étape 1 : [Activation des autorisations.](insider-risk-management-configure.md#step-1-enable-permissions-for-insider-risk-management)

>[!NOTE]
>Le journal d’audit de la gestion des risques internes n’est pas associé au journal d’audit Microsoft 365, il s’agit de systèmes d’audit indépendants et de capture d’informations sur des activités distinctes. La désactivation Microsoft 365'audit n’a pas d’impact sur l’audit des activités au sein de la gestion des risques internes.

## <a name="view-activity-in-the-insider-risk-audit-log"></a>Afficher l’activité dans le journal d’audit des risques internes

Pour afficher l’activité des fonctionnalités surveillée pour la gestion des risques internes, accédez au lien du journal **d’audit** des risques internes et sélectionnez-le dans la zone supérieure droite de n’importe quel onglet de gestion des risques internes. Par défaut, les informations suivantes s’affichent pour les activités de gestion des risques internes :

- **Activité :** Description de l’activité entreprise dans la solution de gestion des risques internes par un utilisateur.
- **Catégorie :** Zone ou élément dans lequel l’activité a été effectuée. Par exemple, vous verrez *Stratégies* comme catégorie lorsque des activités de modification de stratégie ont été effectuées.
- **Activité effectuée par :** Nom d’utilisateur de l’utilisateur qui a effectué l’activité.
- **Date :** Date et heure d’activité. La date et l’heure sont les date et heure locales de votre organisation.

Pour plus d’informations sur une activité enregistrée, sélectionnez l’activité pour afficher le volet d’informations sur l’activité. Ce volet inclut des informations supplémentaires sur l’activité.

## <a name="columns-and-filtering"></a>Colonnes et filtrage

Pour faciliter la vérification de l’activité enregistrée par les auditeurs, le filtrage est pris en charge dans le journal d’audit des risques **internes.** Pour le filtrage de base, des colonnes de file d’attente peuvent être ajoutés à l’affichage pour fournir différents tableaux croisés dynamiques sur les fichiers et les messages. Vous pouvez filtrer les activités par **catégorie, plage de dates** et **activité effectuées par champs.**

Pour ajouter ou supprimer des en-tête  de colonne pour la file d’attente d’activités, utilisez le contrôle Personnaliser les colonnes et sélectionnez-le dans les options de colonne. Ces colonnes s’appuient sur des conditions courantes prise en charge dans le journal **d’audit** des risques internes et sont répertoriées plus loin dans cet article.

## <a name="audit-log-export"></a>Exportation du journal d’audit

Les *utilisateurs affectés* aux groupes de rôles Insider *Risk Management* ou Insider Risk Management Auditors peuvent exporter toute l’activité du journal d’audit vers un fichier .csv (valeurs séparées par des virgules) en sélectionnant **Exporter** dans la page journal **d’audit** des risques internes. Selon l’activité, certains champs d’une activité peuvent ne pas être applicables à l’activité et ces champs apparaîtront comme vides dans le fichier exporté.

Le fichier contient des informations d’activité pour les champs suivants :

- **Activité effectuée par :** Nom d’utilisateur de l’utilisateur qui modifie une valeur d’élément. Les *utilisateurs répertoriés* ici ont été [](insider-risk-management-configure.md#step-1-enable-permissions-for-insider-risk-management)affectés à un ou plusieurs des groupes de rôles de gestion des risques internes suivants : Insider *Risk Management*, Insider Risk Management Admins , *Insider Risk Management Analysts*, Insider Risk Management *Investigators*. Chaque groupe de rôles dispose de différents niveaux d’autorisation pour gérer les fonctionnalités de risque internes.
- **Activité :** Activité entreprise sur un élément. Les *valeurs sont Viewed, Deleted, Added, Edited policy, Case, User, Alert et* *Paramètres.*
- **Ajout :** objets qui ont été ajoutés au cours de l’activité, tels que les utilisateurs, les types de fichiers ou les domaines.
- **Volume d’alerte**: niveau du volume d’alerte défini dans les paramètres de gestion des risques internes.
- **Montant**: montants des indicateurs personnalisés actuellement sélectionnés pour une stratégie.
- **ID d’actif**: ID de l’actif physique de priorité sur qui l’activité a été effectuée.
- **Catégorie :** Catégorie de l’élément modifié. Les valeurs *sont les modèles Stratégies, Cas, Utilisateurs, Alertes, Paramètres* et *Notification.*
- **Date :** Date et heure, répertoriées dans la date et l’heure locales de votre organisation.
- **Description**: entrée de description par l’utilisateur pour l’objet en cours d’action (par exemple, une stratégie ou un groupe d’utilisateurs prioritaire).
- **Stratégie DLP :** stratégie de protection contre la perte de données (DLP) sélectionnée pour déclencher l’inclusion dans une stratégie de gestion des risques internes.
- **Indicateur**: indicateur dans les paramètres de risque internes sur l’activité (par exemple, ajout ou suppression d’un indicateur).
- **Modèle de notification**: modèle d’avis sur qui l’activité a été effectuée.
- **Nombre de jours :** fenêtre d’activation de stratégie définie dans les paramètres de risque interne.
- **Nombre de fichiers**: limite de volume de fichiers définie dans les paramètres de gestion des risques internes.
- **Modèle de stratégie**: le modèle de stratégie sur qui les indicateurs ont agit appartient.
- **Montant précédent :** montants des indicateurs personnalisés précédemment sélectionnés pour une stratégie.
- **Groupe d’utilisateurs prioritaire**: groupe d’utilisateurs prioritaire sur qui l’activité a été effectuée.
- **Supprimé :** objets qui ont été supprimés pendant l’activité, tels que les utilisateurs, les types de fichiers ou les domaines.
- **Expéditeur :** champ de l’expéditeur du modèle d’avis sur qui l’activité a été effectuée.
- **Stratégie cible**: stratégie sur quelle stratégie l’activité a été effectuée (par exemple, ajout d’un utilisateur ou suppression d’un utilisateur).
- **Corps du message du** modèle : corps du message du modèle d’avis sur qui l’activité a été effectuée.
- **Objet du** modèle : champ d’objet du modèle d’avis sur qui l’activité a été effectuée.
- **Utilisateur :** Utilisateur sur qui l’activité a été effectuée.
