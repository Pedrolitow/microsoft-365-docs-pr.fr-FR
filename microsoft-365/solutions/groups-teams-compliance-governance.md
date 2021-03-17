---
title: Options de conformité pour les groupes Microsoft 365, Teams et la collaboration SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Découvrez les options de conformité pour les groupes Microsoft 365, Teams et la collaboration SharePoint.
ms.openlocfilehash: f68381ab45e74b9b7c8f44465387add82bd4150a
ms.sourcegitcommit: 8f1721de52dbe3a12c11a0fa5ed0ef5972ca8196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2021
ms.locfileid: "50838650"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>Options de conformité pour les groupes Microsoft 365, Teams et la collaboration SharePoint

Microsoft 365 offre une suite complète d’outils pour maintenir la conformité à mesure que vos utilisateurs collaborent. Examinez ces options et réfléchissez à la façon dont elles s’miquent aux besoins de votre entreprise, à la sensibilité de vos données et à l’étendue des personnes avec qui vos utilisateurs doivent collaborer.

Le tableau suivant fournit une référence rapide pour les contrôles de conformité disponibles dans Microsoft 365. Des informations supplémentaires sont fournies dans les sections suivantes.

|Catégorie|Description|Référence|
|:-------|:----------|:--------|
|Rétention des informations|||
||Conserver la messagerie et le contenu SharePoint des groupes|[En savoir plus sur les stratégies de rétention dans SharePoint et OneDrive](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-sharepoint)|
||Conserver la conversation et les messages|[En savoir plus sur les stratégies de rétention dans Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-teams)|
|Classification des informations|||
||Classifier les groupes et les équipes|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)|
||Classifier automatiquement le contenu sensible|[Appliquer automatiquement une étiquette de confidentialité à du contenu](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically)|
||Chiffrer le contenu sensible|[Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)|
|Protection des informations|||
||Empêcher la perte d’informations sensibles|[Vue d’ensemble de la protection contre la perte de données](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies)|
||Protéger les informations sensibles dans la conversation.|[Prévention des pertes de données et Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/dlp-microsoft-teams)|
||Définir les informations sensibles de votre organisation|[Types d’informations sensibles personnalisés](https://docs.microsoft.com/microsoft-365/compliance/custom-sensitive-info-types)|
|Segmentation des utilisateurs|||
||Restreindre la communication entre les segments d’utilisateurs|[Obstacles aux informations](https://docs.microsoft.com/microsoft-365/compliance/information-barriers)|

## <a name="information-retention"></a>Rétention des informations

Les stratégies de rétention sont disponibles pour conserver ou supprimer des éléments utilisés pour la collaboration dans des groupes et des équipes, notamment des fichiers, des messages et des messages électroniques. Les stratégies peuvent être définies pour conserver et supprimer, conserver uniquement ou supprimer uniquement. Les informations couvertes par une stratégie de rétention sont protégées en cas d’expiration ou de suppression du groupe ou de l’équipe.

La configuration d’une stratégie de rétention pour les groupes Microsoft 365 couvre la boîte aux lettres de groupe et le site et les fichiers SharePoint associés.

- [En savoir plus sur les stratégies de rétention dans SharePoint et OneDrive](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-sharepoint)

Les stratégies de rétention pour Teams conservent les messages de conversation et de canal. Bien que les messages de conversation et de canal soient stockés dans des boîtes aux lettres Exchange, ils ne sont pas affectés par les stratégies de rétention Exchange. Vous devez définir vos stratégies de rétention pour qu’ils s’appliquent aux conversations teams et aux messages de canal Teams. 

Les conversations utilisateur sont conservées indéfiniment, même si un compte d’utilisateur est supprimé. Si vous ne souhaitez pas conserver ces données indéfiniment, envisagez d’utiliser une stratégie de rétention pour supprimer les conversations utilisateur après une période spécifiée ou incluez cette suppression dans votre processus de suppression d’utilisateur.

- [En savoir plus sur les stratégies de rétention dans Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-teams)

- [Stratégies de rétention dans Microsoft Teams](https://docs.microsoft.com/microsoftteams/retention-policies)

Une stratégie de rétention unique peut être définie pour s’appliquer aux groupes Microsoft 365, aux messages de conversation Teams et aux messages de canal Teams. 

Ressources supplémentaires :

- [Découvrir les stratégies de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)

- [Balises et stratégies de](https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) rétention dans Exchange

## <a name="information-classification"></a>Classification des informations

Vous pouvez utiliser des étiquettes de confidentialité pour régir l’accès invité, la confidentialité des groupes et des équipes, et l’accès par des appareils nonmanagés pour les groupes et les équipes. En appliquant l’étiquette, ces paramètres sont automatiquement configurés comme spécifié par les paramètres d’étiquette.

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)

Vous pouvez configurer Microsoft 365 pour appliquer automatiquement des étiquettes de sensibilité aux fichiers et aux e-mails en fonction des critères que vous spécifiez, y compris la détection des types d’informations sensibles ou de la correspondance de modèles avec des classifieurs entraisables.

- [Appliquer automatiquement une étiquette de confidentialité à du contenu](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically)

Vous pouvez utiliser des étiquettes de niveau de sensibilité pour chiffrer des fichiers, en permettant uniquement à ceux qui ont des autorisations de les déchiffrer et de les lire.

- [Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)

- [Configurer une équipe avec l’isolation de sécurité](https://docs.microsoft.com/microsoft-365/solutions/secure-teams-security-isolation)

Ressources supplémentaires :

- [En savoir plus sur les étiquettes de niveau de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)


## <a name="information-protection"></a>Protection des informations

Les stratégies DLP peuvent empêcher le partage accidentel d’informations sensibles entre SharePoint, Exchange et Teams. Vous pouvez créer des stratégies qui spécifient les actions à prendre (par exemple, le blocage d’accès) en fonction d’un ensemble de règles.

- [Vue d’ensemble de la protection contre la perte de données](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies)

DLP dans Teams peut aider à protéger les informations sensibles dans les messages de conversation et de canal Teams en supprimant les messages qui contiennent des informations sensibles.

- [Prévention des pertes de données et Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/dlp-microsoft-teams)

Si vous avez des informations sensibles propres à votre organisation, telles que des noms de code de projet, vous pouvez créer vos propres types d’informations sensibles et les appliquer aux stratégies DLP pour protéger le contenu dans les groupes, les équipes et SharePoint.

- [Types d’informations sensibles personnalisés](https://docs.microsoft.com/microsoft-365/compliance/custom-sensitive-info-types)

## <a name="user-segmentation"></a>Segmentation des utilisateurs

Avec les obstacles à l’information, vous pouvez segmenter vos données et vos utilisateurs pour limiter la communication et la collaboration indésirables entre les groupes et éviter les conflits d’intérêt au niveau de votre organisation. Les obstacles à l’information vous permettent de créer des stratégies pour autoriser ou empêcher la collaboration sur des fichiers, des conversations, des appels ou des invitations à des réunions entre des groupes de personnes de votre organisation.

- [Obstacles aux informations](https://docs.microsoft.com/microsoft-365/compliance/information-barriers)

- [Cloisonnement de l’information dans Microsoft Teams](https://docs.microsoft.com/microsoftteams/information-barriers-in-teams)

- [Utiliser les obstacles aux informations avec SharePoint](https://docs.microsoft.com/sharepoint/information-barriers)

## <a name="related-topics"></a>Rubriques connexes

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Sécurité et conformité pour Exchange Online](https://docs.microsoft.com/exchange/security-and-compliance/security-and-compliance)

[Protéger les informations](https://docs.microsoft.com/microsoft-365/compliance/protect-information)
