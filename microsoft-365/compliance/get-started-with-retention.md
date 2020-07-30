---
title: Prise en main des stratégies et des étiquettes de rétention
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
description: Vous êtes prêt à mettre en place des stratégies et des étiquettes de rétention pour la gouvernance des données de votre organisation, mais vous ne savez pas par où commencer ? Lisez quelques conseils pratiques pour commencer.
ms.openlocfilehash: 4bf8499cc8f29438da407c6dfcdaa53533fea467
ms.sourcegitcommit: 583fd1ac1f385c58b93bda648907a1bd8e0a1950
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45430232"
---
# <a name="get-started-with-retention-policies-and-retention-labels"></a>Prise en main des stratégies et des étiquettes de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Vous êtes prêt à commencer à gouverner les données de votre organisation en conservant le contenu que vous devez conserver et en supprimant les autres contenus ? Utilisez les instructions de haut niveau suivantes pour commencer :

1. **Découvrez comment fonctionne la rétention** dans Microsoft 365, puis déterminer si vous avez besoin d’utiliser des stratégies de rétention ou des étiquettes de rétention, ou une combinaison : [Découvrir la rétention](retention.md)

2. **Identifiez les paramètres de rétention et les actions** requises par les stratégies de votre organisation ou par les réglementations de votre secteur.
    
    Dans le cadre de cette évaluation, déterminez si vous utiliserez la [gestion des enregistrements](records-management.md).

3. **Créez des stratégies de rétention et des étiquettes de rétention**, en fonction des paramètres de rétention et des actions que vous avez identifiés.
    
    Pour les étiquettes de rétention, il peut être utile d’utiliser un [plan de fichiers](file-plan-manager.md) afin de définir et d’affiner vos étiquettes de rétention dans une feuille de calcul. Importez ensuite cette feuille de calcul pour créer vos étiquettes.
    
3. **Publiez et appliquez vos étiquettes de rétention**. Alors que les stratégies de rétention sont conçues pour être définies en une seule fois, les étiquettes de rétention sont des blocs de construction réutilisables dans plusieurs stratégies et qui peuvent être incorporés dans les flux de travail des utilisateurs. Consultez la liste des [scénarios courants](#common-scenarios-for-retention-policies-and-retention-labels) pour savoir comment utiliser les étiquettes de rétention. 

## <a name="subscription-and-licensing-requirements-for-retention-policies-and-retention-labels"></a>Conditions d’abonnement et de licence pour les stratégies et les étiquettes de rétention

Différents abonnements prennent en charge les stratégies et les étiquettes de rétention et les conditions requises pour les licences des utilisateurs dépendent des fonctionnalités utilisées.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft 365, voir les [Conseils de licence Microsoft 365 pour la sécurité et la conformité](https://aka.ms/ComplianceSD). Pour la rétention, voir la section [Gouvernance des informations](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) ainsi que le fichier PDF ou Excel téléchargeable associé aux exigences de licences au niveau des fonctionnalités.

## <a name="permissions-required-to-create-and-manage-retention-policies-and-retention-labels"></a>Autorisations requises pour créer et gérer les stratégies et les étiquettes de rétention

Les membres de votre équipe de conformité, appelés à créer et gérer des stratégies et des étiquettes de rétention, ont besoin d’autorisations pour accéder au [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Par défaut, votre administrateur client (administrateur général) a accès à cet emplacement et peut accorder aux responsables de la conformité et à d’autres personnes un accès sans leur donner toutes les autorisations d’un administrateur client. Pour accorder des autorisations à cette administration limitée, nous vous recommandons d'ajouter des utilisateurs au groupe de rôles d’administrateur **Administrateur de la conformité**. Pour obtenir des instructions, veuillez consulter la page [Octroi de l’accès au Centre de sécurité et conformité aux utilisateurs](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center).

Ces autorisations sont nécessaires uniquement pour créer et appliquer une stratégie de rétention. La personne qui configure la stratégie de rétention n’a pas besoin d’accéder au contenu.

## <a name="common-scenarios-for-retention-policies-and-retention-labels"></a>Scénarios courants pour les stratégies et étiquettes de rétention

Utilisez le tableau suivant pour vous aider à faire correspondre vos besoins métier aux scénarios de rétention pris en charge par les stratégies et étiquettes de rétention.

|Je veux...|Documentation|
|----------------|---------------|
|Configurez efficacement les actions de rétention et de suppression pour l’organisation, ou par service Microsoft 365 : <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- Groupes Microsoft 365 <br />- Skype Entreprise  <br />- Microsoft Teams  |[Créer et configurer des stratégies de rétention](create-retention-policies.md)|
|Permettez aux administrateurs et aux utilisateurs d’appliquer manuellement un groupe d’actions de rétention et de suppression pour les documents et e-mails : <br />- SharePoint <br />- OneDrive <br />- Outlook et Outlook sur le web|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux administrateurs de site de définir une étiquette de rétention par défaut à tout le contenu dans une bibliothèque, un dossier ou un ensemble de documents SharePoint|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux utilisateurs d’appliquer automatiquement une étiquette de rétention aux courriers électroniques à l’aide des règles Outlook|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Appliquez automatiquement un groupe d’actions de rétention et de suppression pour les documents et e-mails |[Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)|
|Démarrez la période de rétention lorsqu’un événement se produit, par exemple :  <br />- Des employés quittent l’organisation <br />- Des contrats expirent <br />- Fin de vie d’un produit| [Débuter la rétention lorsqu’un événement se produit](event-driven-retention.md)|
|Gérer le cycle de vie de différents types de documents dans SharePoint| [Gérer le cycle de vie des documents SharePoint avec des étiquettes de rétention](auto-apply-retention-labels-scenario.md)|
|Utilisez une seule solution de gestion des enregistrements pour les documents et les e-mails |[Gestion des enregistrements dans Microsoft 365](records-management.md) |
|Conformez-vous à la réglementation SEC Rule 17 a-4|[Utiliser Exchange Online et le centre de sécurité et conformité pour se conformer à la réglementation SEC Rule 17 a-4](use-exchange-online-to-comply-with-sec-rule-17a-4.md) |
|Vérifiez que le contenu est révisé et approuvé avant sa suppression à la fin de sa période de rétention|[Révisions avant destruction](disposition.md#disposition-reviews) |
|Obtenez une preuve de destruction du contenu à la fin de sa période de rétention.|[Destruction des enregistrements](disposition.md#disposition-of-records) |

## <a name="end-user-documentation-for-retention-labels"></a>Documentation de l’utilisateur final sur les étiquettes de rétention

Les étiquettes de rétention, contrairement aux stratégies de rétention, sont présentes dans l’interface utilisateur des applications Microsoft 365. Veillez à fournir des instructions pour les utilisateurs finaux et votre support technique avant de déployer les étiquettes de rétention sur votre réseau de production.

La documentation la plus efficace pour l’utilisateur final est une aide personnalisée en fonction des instructions que vous fournissez pour les noms d’étiquette de rétention et des configurations que vous choisissez. Toutefois, vous pouvez utiliser les informations suivantes pour afficher des instructions de base :

- [Appliquer manuellement des étiquettes de rétention](create-apply-retention-labels.md#manually-apply-retention-labels)
