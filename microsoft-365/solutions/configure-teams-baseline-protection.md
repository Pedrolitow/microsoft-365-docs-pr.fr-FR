---
title: Configurer les équipes avec la protection de référence
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
recommendations: false
description: Découvrez comment déployer des équipes à l’aide d’un niveau de protection de référence.
ms.openlocfilehash: ec8c2a1a5c4480ffd36b77fe9e9accc91214c6a3
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52538206"
---
# <a name="configure-teams-with-baseline-protection"></a>Configurer les équipes avec la protection de référence

Dans cet article, nous allons voir comment déployer des équipes à l’aide d’un niveau de protection de référence. Ce niveau permet aux utilisateurs de bénéficier d’un large éventail d’options de collaboration tout en améliorant la gestion des autorisations et en offrant une protection de référence contre le partage. Les protections recommandées pour ce niveau incluent les stratégies d’accès aux identités et appareils et la protection contre les programmes malveillants. Vous pouvez également appliquer les stratégies d’accès conditionnel et les protections contre la perte de données, le cas échéant.

## <a name="initial-protections"></a>Protections initiales

Pour commencer, nous vous recommandons de configurer les stratégies de base sur l’identité et l’accès aux appareils. Pour plus d’informations, consultez [recommandations en matière de stratégie pour la sécurisation des conversations, des groupes et des fichiers](../security/office-365-security/teams-access-policies.md).

Nous vous recommandons également d’activer les fonctionnalités de base de Defender pour Office 365 pour vous prémunir contre les programmes malveillants dans les documents, pièces jointes et liens. Nous vous recommandons d’activer chacune des options du tableau suivant.

|Option|Informations|
|:------|:-----------|
|Pièces jointes fiables pour SPO, OneDrive et Teams|[Pièces jointes fiables](../security/office-365-security/safe-attachments.md)<br>[Defender pour Office 365 – SharePoint, OneDrive et Microsoft Teams](../security/office-365-security/mdo-for-spo-odb-and-teams.md).|
|Documents sécurisés|[Documents sécurisés dans Microsoft Defender pour Office 365](../security/office-365-security/safe-docs.md)|
|Liens fiables pour Teams|[Liens fiables Office 365 dans Teams](../security/office-365-security/safe-links.md)<br>[Liens fiables](../security/office-365-security/safe-links.md)|

## <a name="teams-guest-sharing"></a>Partage d'invités Teams

Dans chacun des niveaux, nous avons la possibilité de partager avec des personnes extérieures à votre organisation. Pour les niveaux sensibles et hautement sensibles, nous aurons la possibilité de désactiver le partage d'invités au niveau de l'équipe à l'aide d'étiquettes de confidentialité. Cependant, le paramètre de partage d’invités au niveau de l’organisation doit être activé pour que le partage d’invités fonctionne dans Teams.

![Capture d’écran du commutateur Accès invité dans Teams](../media/teams-guest-access-toggle-on.png)

Pour déterminer les paramètres d’accès invité Teams, procédez comme suit :

1. Connectez-vous au Centre d’administration Microsoft 365 sur[https://admin.microsoft.com](https://admin.microsoft.com).
2. Dans la barre de navigation de gauche, cliquez sur **Afficher tout**.
3. Sous **Centres d’administration**, cliquez sur **Teams**.
4. Dans le Centre d’administration Teams, dans le volet de navigation gauche, développez **Paramètres à l’échelle de l’organisation**, puis cliquez sur **Accès invité**.
5. Assurez-vous que **Autoriser l’accès invité dans Teams** est défini sur **Activé**.
6. Apportez les modifications souhaitées aux autres paramètres invités, puis cliquez sur **Enregistrer**.

> [!NOTE]
> La mise en service du paramètre invité Teams peut prendre jusqu'à vingt-quatre heures.

Le partage d’invités est activé par défaut pour les groupes Office 365 et SharePoint. Toutefois, si vous avez modifié les paramètres de partage d’invités de votre organisation, nous vous recommandons de consulter [Collaborer avec des invités dans une équipe](./collaborate-as-team.md) afin de vous assurer que le partage d’invités est disponible dans Teams.

## <a name="site-and-file-sharing"></a>Partage de sites et fichiers

Pour réduire le risque de partager accidentellement des fichiers ou des dossiers avec des personnes externes à votre organisation, nous vous recommandons de modifier le lien de partage par défaut de SharePoint à *Uniquement les membres de votre organisation*. (Si les utilisateurs doivent partager en externe et que vous avez activé le partage d’invités, ils peuvent modifier le type de lien lorsqu’ils partagent le lien.)

Pour modifier le lien de partage par défaut, procédez comme suit :
1. Ouvrez le [Centre d’administration SharePoint](https://admin.microsoft.com/sharepoint).
2. Sous **Stratégies**, cliquez sur **Partage**.
3. Sous **Liens de fichier et de dossier**, sélectionnez **Uniquement les membres de votre organisation**.
4. Cliquez sur **Enregistrer**.

Pour une expérience de partage d’invités optimale, nous vous recommandons également d’activer [L’intégration de SharePoint et OneDrive à l’aide d’Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview).

## <a name="create-a-team"></a>Créer une équipe

Une configuration supplémentaire pour le niveau de protection de référence est effectuée sur le site SharePoint associé à une équipe. [Créez une équipe publique ou privée](https://support.office.com/article/174adf5f-846b-4780-b765-de1a0a737e2b) avant de passer à la section suivante.

## <a name="site-sharing-settings"></a>Paramètres de partage de site

Par défaut, les membres d’un site SharePoint peuvent inviter d’autres personnes sur le site. Lorsqu’un site fait partie d’une équipe, les membres de l’équipe sont inclus en tant que membres du site. Toutefois, les personnes ajoutées directement au site n’ont pas accès au reste de l’équipe. Pour cette raison, nous vous recommandons de gérer les autorisations en exclusivité au sein de l’équipe.

Pour faciliter la gestion des autorisations, nous recommandons de configurer le site associé de manière à autoriser uniquement les propriétaires à partager le site. Cela simplifie la gestion des autorisations et permet d’empêcher l’accès par des personnes qui ne possèdent pas d’informations sur le propriétaire d’une équipe. Procédez ainsi pour chaque équipe qui a besoin d'une protection de référence.

Pour mettre à jour les paramètres de partage de site, procédez comme suit :
1. Dans la barre d’outils de l’équipe, cliquez sur **Fichiers**.
2. Cliquez sur **Ouvrir dans SharePoint**.
3. Dans la barre d’outils du site SharePoint, cliquez sur l’icône Paramètres, puis cliquez sur **Autorisations du site**.
4. Dans le volet **Autorisations de site**, sous **Partage de site**, cliquez sur **Modifier les modalités de partage par les membres**.
5. Sous **Autorisations de partage**, sélectionnez **Propriétaires et membres du site. les personnes disposant des autorisations de modification peuvent partager des fichiers et des dossiers, mais seuls les propriétaires de site peuvent partager le site**, puis cliquer sur **Enregistrer**.

## <a name="additional-protections"></a>Autres protections

Microsoft 365 offre d’autres méthodes pour la sécurisation de votre contenu. Envisagez d’utiliser les options suivantes pour renforcer la sécurité au sein de votre organisation.

- Demandez aux invités d’accepter les [conditions d’utilisation](/azure/active-directory/conditional-access/terms-of-use).
- Configurez une [stratégie de délai d’expiration de session](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) pour les invités.
- Créez les [Types d’informations sensibles](../compliance/sensitive-information-type-learn-about.md) et utilisez [Protection contre la perte de données](../compliance/dlp-learn-about-dlp.md) pour définir des stratégies autour de l’accès aux informations sensibles.

## <a name="see-also"></a>Voir aussi

[Gérer les stratégies de réunion dans Teams](/microsoftteams/meeting-policies-in-teams)

[Prise en main de la gestion des risques internes](../compliance/insider-risk-management-configure.md)