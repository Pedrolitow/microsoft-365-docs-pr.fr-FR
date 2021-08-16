---
title: Démarrer la gestion des enregistrements dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Vous avez besoin d’une solution de gestion des enregistrements pour Microsoft 365 qui gère des contenus à forte valeur pour les obligations légales, professionnelles, ou réglementaires, mais vous ne savez pas où commencer ? Lisez des instructions pratiques pour démarrer.
ms.openlocfilehash: 8837b764b3e84f16ed1d79d2e0aaf0d677c40fcce2105a34c837ae4bd638342a
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53886010"
---
# <a name="get-started-with-records-management"></a>Prise en main de la gestion des enregistrements

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Etes-vous prêt à démarrer la gestion de contenus à forte valeur de votre organisation relatifs aux obligations légales, professionnelles, ou réglementaires à l’aide d’une solution de gestion des enregistrements dans Microsoft 365? Suivez ces instructions pour démarrer :

1. **Comprenez le fonctionnement de la solution de gestion des enregistrements** et identifiez les actions autorisées ou bloquées lorsque les documents et les messages électroniques sont des enregistrements déclarés : [En savoir plus sur la gestion des enregistrements](records-management.md).

2. **Comprenez le fonctionnement de la rétention et des étiquettes de rétention** pour SharePoint et Exchange, car les étiquettes de rétention sont utilisées pour déclarer des enregistrements : [En savoir plus sur les stratégies et les étiquettes de rétention](retention.md)

3. **Créez votre plan de gestion de fichiers pour les actions et les paramètres de rétention** en [important un plan existant](file-plan-manager.md#import-retention-labels-into-your-file-plan) si vous en avez un, ou créez des [étiquettes de rétention qui déclarent des enregistrements](declare-records.md).

4. **Publiez et appliquez vos étiquettes de rétention**. Les étiquettes de rétention sont des blocs de construction réutilisables dans plusieurs stratégies et qui peuvent être incorporés dans les flux de travail des utilisateurs :

    - [Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
    - [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)

## <a name="subscription-and-licensing-requirements-for-records-management"></a>Conditions d’abonnement et d’acquisition de licence pour la gestion des enregistrements

Différents abonnements prennent en charge la gestion des enregistrements et les conditions requises pour les licences des utilisateurs dépendent des fonctionnalités utilisées.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft 365, voir les [Conseils de licence Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Pour la gestion des enregistrements, voir la section [Gestion des enregistrements](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) ainsi que le fichier PDF ou Excel téléchargeable associé aux exigences de licences au niveau des fonctionnalités.

## <a name="permissions-required-for-records-management"></a>Autorisations requises pour la gestion des enregistrements

Les membres de votre équipe de conformité qui sont chargés de la gestion des enregistrements ont besoin d’autorisations pour accéder au [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Par défaut, l’administrateur client (administrateur général) a accès à cet emplacement et peut accorder aux responsables de la conformité et à d’autres personnes un accès sans leur donner toutes les autorisations d’un administrateur client. Pour accorder des autorisations pour cette administration limitée, nous vous recommandons d'ajouter les utilisateurs au groupe de rôles d’administrateur de la **Gestion des Enregistrements** qui autorise toutes les fonctionnalités liées à la gestion des enregistrements, y compris l'[examen et la vérification de la suppression](disposition.md).

Pour un rôle en lecture seule, vous pouvez créer un nouveau groupe de rôles et ajouter le rôle de **Gestion des enregistrements en lecture seule** à ce groupe.

Pour obtenir des instructions pour ajouter des utilisateurs aux rôles par défaut ou créer vos propres groupes de rôles, consultez [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md).

Ces autorisations sont requises uniquement pour créer, configurer et appliquer des étiquettes de rétention qui déclarent des enregistrements et gère la suppression. La personne qui configure ces étiquettes n’a pas besoin d’accéder au contenu.

## <a name="common-scenarios-for-records-management"></a>Scénarios courants de gestion des enregistrements

Utilisez le tableau suivant pour vous aider à faire correspondre vos besoins métier aux scénarios pris en charge par la gestion des enregistrements.

> [!NOTE]
> La gestion des enregistrements utilisant des étiquettes de rétention pour marquer un élément comme enregistrement, de nombreux scénarios dans ce tableau sont également répertoriés comme [scénarios courants pour les stratégies et les étiquettes de rétention](get-started-with-retention.md#common-scenarios-for-retention-policies-and-retention-labels).

|Je veux...|Documentation|
|----------------|---------------|
|Déclarer un enregistrement |[Déclarer des enregistrements à l’aide d’étiquettes de rétention](declare-records.md)|
|Mettre à jour un enregistrement |[Utiliser le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive](record-versioning.md)|
|Permettez aux administrateurs et aux utilisateurs d’appliquer manuellement les actions de rétention et de suppression pour les documents et e-mails : <br />- SharePoint <br />- OneDrive <br />- Outlook et Outlook sur le web|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux administrateurs de site de définir les actions de rétention et de suppression par défaut à tout le contenu dans une bibliothèque, un dossier ou un ensemble de documents SharePoint|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux utilisateurs d’appliquer automatiquement les actions de rétention et de suppression aux courriers électroniques à l’aide des règles Outlook|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux administrateurs d’appliquer des actions de rétention et de suppression à un modèle de compréhension de document afin que celles-ci soient automatiquement appliquées aux documents identifiés dans une bibliothèque SharePoint|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Appliquez automatiquement les actions de rétention et de suppression pour les documents et e-mails |[Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)|
|Démarrez la période de rétention lorsqu’un événement se produit, par exemple :  <br />- Des employés quittent l’organisation <br />- Des contrats expirent <br />- Fin de vie d’un produit| [Débuter la rétention lorsqu’un événement se produit](event-driven-retention.md)|
|Limiter les modifications apportées aux stratégies afin de répondre aux exigences réglementaires ou de protéger contre les administrateurs malveillants| [Utiliser le verrouillage de conservation pour restreindre les modifications apportées aux stratégies de rétention et d’étiquettes de rétention](retention-preservation-lock.md)
|Gérer le cycle de vie de différents types de documents dans SharePoint| [Utiliser les étiquettes de rétention pour gérer le cycle de vie des documents stockés dans SharePoint](auto-apply-retention-labels-scenario.md)|
|Vérifiez que le contenu est révisé et approuvé avant sa suppression à la fin de sa période de rétention|[Révisions avant destruction](disposition.md#disposition-reviews) |
|Obtenez une preuve de destruction permanente du contenu à la fin de sa période de rétention.|[Destruction des enregistrements](disposition.md#disposition-of-records) |
| Contrôler la manière dont les paramètres conserver et supprimer sont appliqués aux éléments | [Surveillance des étiquettes de rétention](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation-for-records"></a>Documentation de l’utilisateur final sur les enregistrements

Les étiquettes de rétention utilisées pour la gestion des enregistrements sont associées à une présence d’interface utilisateur dans Microsoft 365 Apps. Veillez à fournir des conseils aux utilisateurs finaux et à votre support technique avant de déployer les étiquettes sur votre réseau de production.

Pour aider les utilisateurs à appliquer des étiquettes de rétention dans SharePoint et OneDrive, incluant des informations sur le déverrouillage d’enregistrements pour la modification, consultez [Appliquer des étiquettes de rétention aux fichiers dans SharePoint ou OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Toutefois, la documentation la plus efficace de l’utilisateur final sera un guide personnalisé pour les noms d’étiquette de rétention et les configurations que vous choisissez. Consultez le billet de blog suivant pour obtenir un package de téléchargement que vous pouvez utiliser pour former les utilisateurs et développer l’adoption : [Formation de l’utilisateur final pour les étiquettes de rétention dans M365, comment accélérer l’adoption](https://techcommunity.microsoft.com/t5/microsoft-security-and/end-user-training-for-retention-labels-in-m365-how-to-accelerate/ba-p/1750861).
