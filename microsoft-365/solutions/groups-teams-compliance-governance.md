---
title: Options de conformité pour les groupes Microsoft 365, teams et collaboration SharePoint
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
description: Découvrez les options de conformité pour les groupes, les équipes et la collaboration SharePoint de Microsoft 365.
ms.openlocfilehash: 0383b0728d9b8ea12ce75de8bf0e250932d14ae5
ms.sourcegitcommit: 9841058fcc95f7c2fed6af92bc3c3686944829b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "48377532"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>Options de conformité pour les groupes Microsoft 365, teams et collaboration SharePoint

Microsoft 365 offre une suite complète d’outils permettant de gérer la conformité à mesure que vos utilisateurs collaborent. Passez en revue ces options et réfléchissez à la façon dont elles correspondent à vos besoins professionnels, à la sensibilité de vos données et à l’étendue des personnes avec lesquelles vos utilisateurs doivent collaborer.

Le tableau suivant fournit une référence rapide pour les contrôles de conformité disponibles dans Microsoft 365. Pour plus d’informations, reportez-vous aux sections suivantes.

|Catégorie|Description|Référence|
|:-------|:----------|:--------|
|Rétention des informations|||
||Retain Groups mail and SharePoint content|[En savoir plus sur les stratégies de rétention dans SharePoint et OneDrive](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-sharepoint)|
||Conserver la conversation et les messages|[En savoir plus sur les stratégies de rétention dans Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-teams)|
|Classification des informations|||
||Classer les groupes et les équipes|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)|
||Classer automatiquement le contenu sensible|[Appliquer automatiquement une étiquette de confidentialité à du contenu](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically)|
||Chiffrer le contenu sensible|[Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)|
|Protection des informations|||
||Empêcher la perte d’informations sensibles|[Vue d’ensemble de la protection contre la perte de données](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies)|
||Protéger les informations sensibles dans la conversation.|[Protection contre la perte de données et Microsoft teams](https://docs.microsoft.com/microsoft-365/compliance/dlp-microsoft-teams)|
||Définir les informations sensibles de votre organisation|[Types d’informations sensibles personnalisés](https://docs.microsoft.com/microsoft-365/compliance/custom-sensitive-info-types)|
|Segmentation des utilisateurs|||
||Limiter la communication entre les segments d’utilisateur|[Obstacles aux informations](https://docs.microsoft.com/microsoft-365/compliance/information-barriers)|

## <a name="information-retention"></a>Rétention des informations

Les stratégies de rétention sont disponibles pour conserver ou supprimer les éléments utilisés pour la collaboration dans les groupes et les équipes, y compris les fichiers, les messages et les messages électroniques. Les stratégies peuvent être définies de façon à conserver et supprimer, à conserver uniquement ou à supprimer uniquement. Les informations couvertes par une stratégie de rétention sont protégées en cas d’expiration du groupe ou de l’équipe ou si elles sont supprimées.

La configuration d’une stratégie de rétention pour les groupes Microsoft 365 couvre la boîte aux lettres de groupe et les fichiers et le site SharePoint associés.

- [En savoir plus sur les stratégies de rétention dans SharePoint et OneDrive](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-sharepoint)

Les stratégies de rétention pour teams conservent les messages de conversation et de canal. Bien que les messages de conversation et de canal soient stockés dans les boîtes aux lettres Exchange, ils ne sont pas affectés par les stratégies de rétention Exchange. Vous devez définir vos stratégies de rétention à appliquer aux conversations de teams et aux messages de canal teams :

- [En savoir plus sur les stratégies de rétention dans Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-teams)

- [Stratégies de rétention dans Microsoft Teams](https://docs.microsoft.com/microsoftteams/retention-policies)

Une seule stratégie de rétention peut être définie pour s’appliquer aux groupes Microsoft 365, Team Chat et teams Channel messages. 

Ressources supplémentaires :

- [Découvrir les stratégies de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)

- [Balises de rétention et stratégies de rétention](https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) dans Exchange

## <a name="information-classification"></a>Classification des informations

Vous pouvez utiliser les étiquettes de confidentialité pour gérer l’accès invité, la confidentialité des groupes et de l’équipe, et l’accès par des appareils non gérés pour les groupes et les équipes. En appliquant l’étiquette, ces paramètres sont automatiquement configurés comme spécifié par les paramètres d’étiquette.

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)

Vous pouvez configurer Microsoft 365 pour appliquer automatiquement des étiquettes de confidentialité aux fichiers et aux courriers électroniques en fonction des critères que vous spécifiez, y compris la détection des types d’informations sensibles ou de la correspondance des modèles avec des classifieurs pouvant être formés.

- [Appliquer automatiquement une étiquette de confidentialité à du contenu](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically)

Vous pouvez utiliser les étiquettes de confidentialité pour chiffrer les fichiers, en autorisant uniquement les utilisateurs disposant d’autorisations à les déchiffrer et à les lire.

- [Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)

- [Configurer une équipe avec l’isolation de sécurité](https://docs.microsoft.com/microsoft-365/solutions/secure-teams-security-isolation)

Ressources supplémentaires :

- [En savoir plus sur les étiquettes de niveau de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)


## <a name="information-protection"></a>Protection des informations

Les stratégies DLP peuvent empêcher le partage accidentel d’informations sensibles entre SharePoint, Exchange et Teams. Vous pouvez créer des stratégies qui spécifient les actions à effectuer (telles que le blocage de l’accès) en fonction d’un ensemble de règles.

- [Vue d’ensemble de la protection contre la perte de données](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies)

DLP dans teams peut vous aider à protéger les informations sensibles dans les conversations et les messages des canaux de teams en supprimant les messages contenant des informations sensibles.

- [Protection contre la perte de données et Microsoft teams](https://docs.microsoft.com/microsoft-365/compliance/dlp-microsoft-teams)

Si vous avez des informations sensibles propres à votre organisation, telles que des noms de code de projet, vous pouvez créer vos propres types d’informations sensibles et les appliquer à des stratégies DLP pour protéger le contenu des groupes, des équipes et de SharePoint.

- [Types d’informations sensibles personnalisés](https://docs.microsoft.com/microsoft-365/compliance/custom-sensitive-info-types)

## <a name="user-segmentation"></a>Segmentation des utilisateurs

Avec des barrières d’informations, vous pouvez segmenter vos données et utilisateurs pour limiter la communication et la collaboration indésirables entre les groupes et éviter les conflits d’intérêt dans votre organisation. Les barrières d’informations vous permettent de créer des stratégies pour autoriser ou empêcher la collaboration sur les fichiers, les conversations, les appels ou les invitations aux réunions entre les groupes de personnes de votre organisation.

- [Obstacles aux informations](https://docs.microsoft.com/microsoft-365/compliance/information-barriers)

- [Barrières des informations dans Microsoft teams](https://docs.microsoft.com/microsoftteams/information-barriers-in-teams)

- [Utiliser les barrières relatives aux informations avec SharePoint](https://docs.microsoft.com/sharepoint/information-barriers)

## <a name="related-topics"></a>Voir aussi

[Sécurité et conformité pour Exchange Online](https://docs.microsoft.com/exchange/security-and-compliance/security-and-compliance)

[Protéger les informations](https://docs.microsoft.com/microsoft-365/compliance/protect-information)


