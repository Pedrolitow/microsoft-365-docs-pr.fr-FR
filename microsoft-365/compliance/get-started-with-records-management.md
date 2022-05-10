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
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Vous avez besoin d’une solution de gestion des enregistrements pour Microsoft 365 qui gère des contenus à forte valeur pour les obligations légales, professionnelles, ou réglementaires, mais vous ne savez pas où commencer ? Lisez des instructions pratiques pour démarrer.
ms.openlocfilehash: 86d6f21963b33fde59cb498868b8ecec315e1ad8
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286777"
---
# <a name="get-started-with-records-management"></a>Prise en main de la gestion des enregistrements

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Etes-vous prêt à démarrer la gestion de contenus à forte valeur de votre organisation relatifs aux obligations légales, professionnelles, ou réglementaires à l’aide d’une solution de gestion des enregistrements dans Microsoft 365? Suivez ces instructions pour démarrer :

1. **Comprendre le fonctionnement de la rétention et de la suppression** dans Microsoft 365 et déterminer si vous devez utiliser des stratégies de rétention pour compléter les étiquettes de rétention qui gèrent les documents et les e-mails au niveau de l’élément : [En savoir plus sur les stratégies de rétention et les étiquettes de rétention](retention.md)
    
    Si nécessaire, [créer des stratégies de rétention](create-retention-policies.md) pour la gouvernance de base des données sur Microsoft 365 charges de travail.
    
2. **Comprendre la solution de gestion des enregistrements** et comment les étiquettes de rétention peuvent être utilisées pour autoriser ou bloquer des actions lorsque des documents et des e-mails sont déclarés des enregistrements : [En savoir plus sur la gestion des enregistrements](records-management.md)

3. **Créer votre plan de fichiers pour les paramètres et actions de rétention et de suppression, et quand les éléments doivent être marqués comme enregistrements** en important un plan existant si vous en avez un, ou créez de nouvelles étiquettes de rétention : [Utilisez le plan de fichiers pour créer et gérer des étiquettes de rétention](file-plan-manager.md)

4. **Publiez et appliquez vos étiquettes de rétention**. Les étiquettes de rétention sont des blocs de construction réutilisables dans plusieurs stratégies et qui peuvent être incorporés dans les flux de travail des utilisateurs :

    - [Publier des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
    - [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)

## <a name="subscription-and-licensing-requirements"></a>Conditions d’abonnement et de licence

Différents abonnements prennent en charge la gestion des enregistrements et les conditions requises pour les licences des utilisateurs dépendent des fonctionnalités utilisées.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft Purview, affichez les [Conseils de licence Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Pour la gestion des enregistrements, voir la section [Gestion des enregistrements de Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management) ainsi que le fichier PDF téléchargeable associé aux exigences de licences au niveau des fonctionnalités.

## <a name="permissions"></a>Autorisations

Les membres de votre équipe de conformité qui sont chargés de la gestion des enregistrements ont besoin d’autorisations pour accéder au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Portail de conformité Microsoft Purview</a>. Par défaut, l’administrateur client (administrateur général) a accès à cet emplacement et peut accorder aux responsables de la conformité et à d’autres personnes un accès sans leur donner toutes les autorisations d’un administrateur client. Pour accorder des autorisations pour cette administration limitée, nous vous recommandons d'ajouter les utilisateurs au groupe de rôles d’administrateur de la **Gestion des Enregistrements** qui autorise toutes les fonctionnalités liées à la gestion des enregistrements, y compris l'[examen et la vérification de la suppression](disposition.md).

Pour un rôle en lecture seule, vous pouvez créer un nouveau groupe de rôles et ajouter le rôle de **Gestion des enregistrements en lecture seule** à ce groupe.

Pour obtenir des instructions pour ajouter des utilisateurs aux rôles par défaut ou créer vos propres groupes de rôles, consultez [Autorisations dans le Portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md).

Ces autorisations sont requises uniquement pour créer, configurer et appliquer des étiquettes de rétention qui déclarent des enregistrements et gère la suppression. La personne qui configure ces étiquettes n’a pas besoin d’accéder au contenu.

## <a name="common-scenarios"></a>Scénarios courants

Utilisez le tableau suivant pour vous aider à faire correspondre vos besoins métier aux scénarios pris en charge par la gestion des enregistrements.

> [!TIP]
> Vous devez vous conformer à une réglementation spécifique du secteur ? Consultez [Exigences réglementaires pour la gestion du cycle de vie des données et la gestion des enregistrements](retention-regulatory-requirements.md) pour obtenir des conseils spécifiques à la réglementation.

|Je veux...|Documentation|
|----------------|---------------|
|Déclarer un enregistrement |[Déclarer des enregistrements à l’aide d’étiquettes de rétention](declare-records.md)|
|Mettre à jour un enregistrement |[Utiliser le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive](record-versioning.md)|
|Permettez aux administrateurs et aux utilisateurs d’appliquer manuellement les actions de rétention et de suppression pour les documents et e-mails : <br />- SharePoint <br />- OneDrive <br />- Outlook et Outlook sur le web|[Publier des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux administrateurs de site de définir les actions de rétention et de suppression par défaut à tout le contenu dans une bibliothèque, un dossier ou un ensemble de documents SharePoint|[Publier des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux utilisateurs d’appliquer automatiquement les actions de rétention et de suppression aux courriers électroniques à l’aide des règles Outlook|[Publier des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux administrateurs d’appliquer des actions de rétention et de suppression à un modèle de compréhension de document afin que celles-ci soient automatiquement appliquées aux documents identifiés dans une bibliothèque SharePoint|[Publier des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Appliquez automatiquement les actions de rétention et de suppression pour les documents et e-mails |[Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)|
|Démarrez la période de rétention lorsqu’un événement se produit, par exemple :  <br />- Des employés quittent l’organisation <br />- Des contrats expirent <br />- Fin de vie d’un produit| [Débuter la rétention lorsqu’un événement se produit](event-driven-retention.md)|
|Limiter les modifications apportées aux stratégies afin de répondre aux exigences réglementaires ou de protéger contre les administrateurs malveillants| [Utiliser le verrouillage de conservation pour restreindre les modifications apportées aux stratégies de rétention et d’étiquettes de rétention](retention-preservation-lock.md)
|Gérer le cycle de vie de différents types de documents dans SharePoint| [Utiliser les étiquettes de rétention pour gérer le cycle de vie des documents stockés dans SharePoint](auto-apply-retention-labels-scenario.md)|
|Appliquer une étiquette de rétention à un fichier lorsque je reçois une alerte indiquant que le contenu contenant des données personnelles est stocké ou reste intact pendant trop longtemps| [Examiner et corriger les alertes dans gestion des risques liés à la confidentialité](/privacy/priva/risk-management-alerts)|
|Vérifiez que le contenu est révisé et approuvé avant sa suppression à la fin de sa période de rétention|[Révisions avant destruction](disposition.md#disposition-reviews) |
|Obtenez une preuve de destruction permanente du contenu à la fin de sa période de rétention.|[Destruction des enregistrements](disposition.md#disposition-of-records) |
| Contrôler la manière dont les paramètres conserver et supprimer sont appliqués aux éléments | [Surveillance des étiquettes de rétention](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation"></a>Documentation de l’utilisateur final

Si vous utilisez des stratégies de rétention pour la gouvernance des données de base, elles fonctionnent généralement de manière discrète en arrière-plan sans intervention de l’utilisateur. Par conséquent, ils ont besoin de peu de documentation pour les utilisateurs. Les stratégies de rétention pour Teams informe les utilisateurs lorsque leurs messages ont été supprimés avec un lien vers [Messages Teams concernant les stratégies de rétention](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

En comparaison, les étiquettes de rétention étant présentes dans Microsoft 365 applications, veillez à fournir des conseils aux utilisateurs finaux et au support technique avant de déployer ces étiquettes sur votre réseau de production. Pour aider les utilisateurs à appliquer des étiquettes de rétention dans SharePoint et OneDrive, ainsi que des informations sur le déverrouillage des enregistrements à modifier, consultez [Appliquer des étiquettes de rétention aux fichiers dans SharePoint ou OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Toutefois, la documentation la plus efficace pour l’utilisateur final sera la personnalisation des instructions que vous fournissez pour les noms et configurations d’étiquettes de fidélisation que vous choisissez. Consultez la page suivante et les téléchargements que vous pouvez utiliser pour former vos utilisateurs : [Formation des utilisateurs finaux pour les étiquettes de rétention](https://microsoft.github.io/ComplianceCxE/enduser/retention/).
