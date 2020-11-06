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
description: Vous avez besoin d’une solution de gestion des enregistrements pour Microsoft 365 qui gère les contenus à forte valeur ajoutée pour les obligations légales, professionnelles ou réglementaires, mais vous ne savez pas par où commencer ? Lisez quelques conseils pratiques pour commencer.
ms.openlocfilehash: 679300f581dd9177c00f367f4452d12142f49ee4
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48919852"
---
# <a name="get-started-with-records-management"></a>Prise en main de la gestion des enregistrements

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Etes-vous prêt à démarrer la gestion du contenu à forte valeur de votre organisation relatif aux obligations légales, professionnelles ou réglementaires à l’aide d’une solution de gestion des enregistrements dans Microsoft 365? Utilisez les instructions de haut niveau suivantes pour commencer :

1. **Comprenez le fonctionnement de la solution de gestion des enregistrements** et identifiez les actions autorisées ou bloquées lorsque les documents et les messages électroniques sont des enregistrements déclarés : [En savoir plus sur la gestion des enregistrements](records-management.md). 

2. **Comprenez le fonctionnement de la rétention et des étiquettes de rétention** pour SharePoint et Exchange, car les étiquettes de rétention sont utilisées pour déclarer des enregistrements : [En savoir plus sur les stratégies et les étiquettes de rétention](retention.md)

3. **Créez votre plan de gestion de fichiers pour les actions et les paramètres de rétention** en [important un plan existant](file-plan-manager.md#import-retention-labels-into-your-file-plan ) si vous en avez un, ou créez des [étiquettes de rétention qui déclarent des enregistrements](declare-records.md).

4. **Publiez et appliquez vos étiquettes de rétention**. Les étiquettes de rétention sont des blocs de construction réutilisables dans plusieurs stratégies et qui peuvent être incorporés dans les flux de travail des utilisateurs : 
    
    - [Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
    - [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)

## <a name="subscription-and-licensing-requirements-for-records-management"></a>Conditions d’abonnement et d’acquisition de licence pour la gestion des enregistrements

Différents abonnements prennent en charge la gestion des enregistrements et les conditions requises pour les licences des utilisateurs dépendent des fonctionnalités utilisées.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft 365, voir les [Conseils de licence Microsoft 365 pour la sécurité et la conformité](https://aka.ms/ComplianceSD). Pour la gestion des enregistrements, voir la section [Gestion des enregistrements](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) ainsi que le fichier PDF ou Excel téléchargeable associé aux exigences de licences au niveau des fonctionnalités.

## <a name="permissions-required-for-records-management"></a>Autorisations requises pour la gestion des enregistrements

Les membres de votre équipe de conformité qui sont chargés de la gestion des enregistrements ont besoin d’autorisations pour accéder au [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Par défaut, l’administrateur client (administrateur général) a accès à cet emplacement et peut accorder aux responsables de la conformité et à d’autres personnes un accès sans leur donner toutes les autorisations d’un administrateur client. Pour accorder des autorisations pour cette administration limitée, nous vous recommandons d'ajouter les utilisateurs au groupe de rôles d’administrateur de la **Gestion des Enregistrements** qui autorise le rôle de la **Gestion d’Enregistrement**.

Les autorisations incluses dans ce groupe de rôles n’incluent pas les autorisations nécessaires pour [la révision et la vérification avant la suppression](disposition.md), et même un administrateur général ne possède pas cette autorisation par défaut. Pour gérer la suppression, utilisez **le rôle** Gestion de la Suppression, en créant un groupe de rôles personnalisé ou en utilisant un groupe de rôles par défaut qui inclut un rôle (tel que **l’Administrateur de la Conformité** ).

Pour plus d’informations sur ces groupes de rôles et les rôles, consultez [Autorisations dans le Centre de Sécurité et de Conformité](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center#roles-in-the-security--compliance-center).

Pour obtenir des instructions sur l’ajout d’utilisateurs aux groupes de rôles et l’attribution de rôles, consultez [Autoriser l’accès au Centre de Sécurité et de Conformité aux utilisateurs](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center).

Ces autorisations sont requises uniquement pour créer, configurer et appliquer des étiquettes de rétention qui déclarent des enregistrements et gère la suppression. La personne qui configure ces étiquettes n’a pas besoin d’accéder au contenu.

## <a name="common-scenarios-for-records-management"></a>Scénarios courants de gestion des enregistrements

Utilisez le tableau suivant pour vous aider à faire correspondre vos besoins métier aux scénarios pris en charge par la gestion des enregistrements.

> [!NOTE]
> La gestion des enregistrements utilisant des étiquettes de rétention pour marquer un élément comme enregistrement, de nombreux scénarios dans ce tableau sont également répertoriés comme [scénarios courants pour les stratégies et les étiquettes de rétention](get-started-with-retention.md#common-scenarios-for-retention-policies-and-retention-labels).

|Je veux...|Documentation|
|----------------|---------------|
|Déclarer un enregistrement |[Déclarer des enregistrements à l’aide d’étiquettes de rétention](declare-records.md)|
|Mettre à jour un enregistrement |[Utiliser le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive](record-versioning.md)|
|Permettez aux administrateurs et aux utilisateurs d’appliquer manuellement les actions de rétention et de suppression pour les documents et e-mails : <br />- SharePoint <br />- OneDrive <br />- Outlook et Outlook sur le web|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux administrateurs de site de définir les actions de rétention et de suppression par défaut à tout le contenu dans une bibliothèque, un dossier ou un ensemble de documents SharePoint|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux utilisateurs d’appliquer automatiquement les actions de rétention et de suppression aux courriers électroniques à l’aide des règles Outlook|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux administrateurs d’appliquer des actions de rétention et de suppression à un modèle de compréhension de document afin que celles-ci soient automatiquement appliquées aux documents identifiés dans une bibliothèque SharePoint|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Appliquez automatiquement les actions de rétention et de suppression pour les documents et e-mails |[Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)|
|Démarrez la période de rétention lorsqu’un événement se produit, par exemple :  <br />- Des employés quittent l’organisation <br />- Des contrats expirent <br />- Fin de vie d’un produit| [Débuter la rétention lorsqu’un événement se produit](event-driven-retention.md)|
|Limiter les modifications apportées aux stratégies afin de répondre aux exigences réglementaires ou de protéger contre les administrateurs malveillants| [Utiliser le verrouillage de conservation pour restreindre les modifications apportées aux stratégies de rétention et d’étiquettes de rétention](retention-preservation-lock.md)
|Gérer le cycle de vie de différents types de documents dans SharePoint| [Utiliser les étiquettes de rétention pour gérer le cycle de vie des documents stockés dans SharePoint](auto-apply-retention-labels-scenario.md)|
|Vérifiez que le contenu est révisé et approuvé avant sa suppression à la fin de sa période de rétention|[Révisions avant destruction](disposition.md#disposition-reviews) |
|Obtenez une preuve de destruction permanente du contenu à la fin de sa période de rétention.|[Destruction des enregistrements](disposition.md#disposition-of-records) |
| Contrôler la manière dont les paramètres conserver et supprimer sont appliqués aux éléments | [Surveillance des étiquettes de rétention](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation-for-records"></a>Documentation de l’utilisateur final sur les enregistrements

Les étiquettes de rétention utilisées pour la gestion des enregistrements sont présentes dans l’interface utilisateur des applications Microsoft 365. Veillez à fournir des instructions pour les utilisateurs finaux et votre support technique avant de déployer les étiquettes de rétention sur votre réseau de production.

La documentation la plus efficace pour l’utilisateur final est une aide personnalisée en fonction des instructions que vous fournissez pour les noms d’étiquette de rétention et des configurations que vous choisissez. Consultez le billet suivant pour obtenir un package de téléchargement que vous pouvez utiliser pour former les utilisateurs et développer l’adoption : [Formation de l’utilisateur final pour les étiquettes de rétention dans M365, comment accélérer l’adoption](https://techcommunity.microsoft.com/t5/microsoft-security-and/end-user-training-for-retention-labels-in-m365-how-to-accelerate/ba-p/1750861).

Vous trouverez également des instructions utilisateur de base dans la section suivante : [Appliquer manuellement des étiquettes de rétention](create-apply-retention-labels.md#manually-apply-retention-labels).
