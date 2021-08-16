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
- m365solution-mig
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Vous êtes prêt à mettre en place des stratégies et des étiquettes de fidélisation pour la gouvernance des données de votre organisation, mais vous ne savez pas par où commencer ?
ms.openlocfilehash: a02b119f40c5ce939d601fe387bc523ecc27c6f453af8811384fb58b2e45c4fb
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53885986"
---
# <a name="get-started-with-retention-policies-and-retention-labels"></a>Prise en main des stratégies et des étiquettes de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Vous êtes prêt à commencer à gouverner les données de votre organisation en conservant le contenu que vous devez conserver et en supprimant les autres contenus ? Utiliser les instructions suivantes, pour commencer:

1. **Découvrez comment fonctionne la rétention** dans Microsoft 365, puis déterminer si vous avez besoin d’utiliser des stratégies de rétention ou des étiquettes de rétention, ou une combinaison : [Découvrir la rétention](retention.md)

2. **Identifiez les paramètres de rétention et les actions** requises par les stratégies de votre organisation ou par les réglementations de votre secteur.
    
    Dans le cadre de cette évaluation, déterminez si vous utiliserez la [gestion des enregistrements](records-management.md).

3. **Créez des stratégies de rétention et des étiquettes de rétention**, en fonction des paramètres de rétention et des actions que vous avez identifiés.
    
    Pour les étiquettes de rétention, il peut être utile d’utiliser un [plan de fichiers](file-plan-manager.md) afin de définir et d’affiner vos étiquettes de rétention dans une feuille de calcul. Importez ensuite cette feuille de calcul pour créer vos étiquettes.
    
3. **Publiez et appliquez vos étiquettes de rétention**. Alors que les stratégies de rétention sont conçues pour être définies en une seule fois, les étiquettes de rétention sont des blocs de construction réutilisables dans plusieurs stratégies et qui peuvent être incorporés dans les flux de travail des utilisateurs. Consultez la liste des [scénarios courants](#common-scenarios-for-retention-policies-and-retention-labels) pour savoir comment utiliser les étiquettes de rétention. 

## <a name="subscription-and-licensing-requirements-for-retention-policies-and-retention-labels"></a>Conditions d’abonnement et de licence pour les stratégies et les étiquettes de rétention

Différents abonnements prennent en charge les stratégies et les étiquettes de rétention et les conditions requises pour les licences des utilisateurs dépendent des fonctionnalités utilisées.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft 365, voir les [Conseils de licence Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Pour la rétention, voir la section [Gouvernance des informations](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) ainsi que le fichier PDF ou Excel téléchargeable associé aux exigences de licences au niveau des fonctionnalités.

## <a name="permissions-required-to-create-and-manage-retention-policies-and-retention-labels"></a>Autorisations requises pour créer et gérer les stratégies et les étiquettes de rétention

Les membres de votre équipe de conformité, appelés à créer et gérer des stratégies et des étiquettes de rétention, ont besoin d’autorisations pour accéder au [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Par défaut, votre administrateur client (administrateur général) a accès à cet emplacement et peut accorder aux responsables de la conformité et à d’autres personnes un accès sans leur donner toutes les autorisations d’un administrateur client. Pour accorder des autorisations à cette administration limitée, nous vous recommandons d'ajouter des utilisateurs au groupe de rôles d’administrateur **Administrateur de la conformité**.

Au lieu d'utiliser ce rôle par défaut, vous pouvez créer un nouveau groupe de rôles et y ajouter le rôle **Gestion de la rétention**. Pour un rôle en lecture seule, utilisez la **Gestion de rétention en lecture seule**. 

Pour obtenir des instructions pour ajouter des utilisateurs aux rôles par défaut ou créer vos propres groupes de rôles, consultez [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md).

Ces autorisations ne sont nécessaires que pour créer, configurer et appliquer des politiques de rétention et des étiquettes de rétention. La personne qui configure ces stratégies et étiquettes n’a pas besoin d’avoir un accès au contenu.

## <a name="common-scenarios-for-retention-policies-and-retention-labels"></a>Scénarios courants pour les stratégies et étiquettes de rétention

Utilisez le tableau suivant pour vous aider à faire correspondre vos besoins métier aux scénarios de rétention pris en charge par les stratégies et étiquettes de rétention.

|Je veux...|Documentation|
|----------------|---------------|
|Configurez efficacement les actions de rétention et de suppression par service Microsoft 365 : <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- Groupes Microsoft 365 <br />- Skype Entreprise  <br />- Microsoft Teams <br />- Réseau Yammer |[Créer et configurer des stratégies de rétention](create-retention-policies.md)|
|Permettez aux administrateurs et aux utilisateurs d’appliquer manuellement les actions de rétention et de suppression pour les documents et e-mails : <br />- SharePoint <br />- OneDrive <br />- Outlook et Outlook sur le web|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux administrateurs de site de définir les actions de rétention et de suppression par défaut à tout le contenu dans une bibliothèque, un dossier ou un ensemble de documents SharePoint|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux utilisateurs d’appliquer automatiquement les actions de rétention et de suppression aux courriers électroniques à l’aide des règles Outlook|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Permettez aux administrateurs d’appliquer des actions de rétention et de suppression à un modèle de compréhension de document afin que celles-ci soient automatiquement appliquées aux documents identifiés dans une bibliothèque SharePoint|[Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)|
|Appliquez automatiquement les actions de rétention et de suppression pour les documents et e-mails |[Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)|
|Démarrez la période de rétention lorsqu’un événement se produit, par exemple :  <br />- Des employés quittent l’organisation <br />- Des contrats expirent <br />- Fin de vie d’un produit| [Débuter la rétention lorsqu’un événement se produit](event-driven-retention.md)|
|Limiter les modifications apportées aux stratégies afin de répondre aux exigences réglementaires ou de protéger contre les administrateurs malveillants| [Utiliser le verrouillage de conservation pour restreindre les modifications apportées aux stratégies de rétention et d’étiquettes de rétention](retention-preservation-lock.md)
|Vérifiez que le contenu est révisé et approuvé avant sa suppression à la fin de sa période de rétention|[Révisions avant destruction](disposition.md#disposition-reviews) |
| Contrôler la manière dont les paramètres conserver et supprimer sont appliqués aux éléments | [Surveillance des étiquettes de rétention](retention.md#monitoring-retention-labels) |
|Utiliser une solution unique de gestion des documents et des e-mails |[En savoir plus sur la gestion des enregistrements](records-management.md) |

Si vous utilisez des étiquettes de rétention pour la gestion des enregistrements, il existe d'autres scénarios qui sont propres aux étiquettes de rétention qui marquent le contenu comme un enregistrement. Voir [ Scénarios communs pour la gestion des enregistrements](get-started-with-records-management.md#common-scenarios-for-records-management).

## <a name="end-user-documentation-for-retention"></a>Documentation de l’utilisateur final sur la rétention

La plupart des stratégies de rétention fonctionnent discrètement en arrière-plan, sans interaction de l'utilisateur, et nécessitent donc peu de documentation pour les utilisateurs. Les stratégies de rétention pour Teams informe les utilisateurs lorsque leurs messages ont été supprimés avec un lien vers [Messages Teams concernant les stratégies de rétention](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Étant donné que les étiquettes de rétention sont présentes dans Microsoft 365 Apps, veillez à fournir des conseils aux utilisateurs finaux et à votre service d’assistance avant de déployer ces étiquettes sur votre réseau de production. Pour aider les utilisateurs à appliquer des étiquettes de fidélisation dans SharePoint et OneDrive, voir [Appliquer des étiquettes de fidélisation aux fichiers dans SharePoint ou OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Toutefois, la documentation la plus efficace pour l’utilisateur final sera la personnalisation des instructions que vous fournissez pour les noms et configurations d’étiquettes de fidélisation que vous choisissez. Consultez la page suivante et les téléchargements que vous pouvez utiliser pour former vos utilisateurs : [Formation des utilisateurs finaux pour les étiquettes de rétention](https://microsoft.github.io/ComplianceCxE/enduser/retention/).