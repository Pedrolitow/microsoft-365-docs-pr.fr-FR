---
title: Collaboration entre locataires Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
f1.keywords:
- NOCSH
description: Découvrez comment la collaboration Microsoft 365 fonctionne entre les locataires et les organisations, ce qui permet à différentes organisations de collaborer en toute sécurité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5dc6879e724ecca2ba25f8dc95d260cc46817e66
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68196114"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Collaboration entre locataires Microsoft 365

Supposons que deux organisations, Fabrikam et Contoso, aient chacune un locataire Microsoft 365 pour les entreprises et qu’elles souhaitent travailler ensemble sur plusieurs projets ; certains d’entre eux s’exécutent pendant une durée limitée et certains d’entre eux sont en cours. Comment Fabrikam et Contoso peuvent-ils permettre à leurs collaborateurs et équipes de collaborer plus efficacement entre leurs différents locataires Microsoft 365 de manière sécurisée ? Microsoft 365, conjointement avec Azure Active Directory (Azure AD) B2B Collaboration, propose plusieurs options. Cet article décrit plusieurs scénarios clés que Fabrikam et Contoso peuvent prendre en compte.

Les options de collaboration entre locataires Microsoft 365 incluent l’utilisation d’un emplacement central pour les fichiers et les conversations, le partage de calendriers, l’utilisation de la messagerie instantanée, les appels audio/vidéo pour la communication et la sécurisation de l’accès aux ressources et aux applications. Utilisez les tableaux suivants pour sélectionner des solutions et en savoir plus.

## <a name="exchange-online-collaboration-options"></a>options de collaboration Exchange Online

| Objectif de partage | Action administrative | Informations de procédures |
|:-----|:-----|:-----|
|Partager des calendriers avec une autre organisation Microsoft 365 |Les administrateurs peuvent configurer différents niveaux d’accès au calendrier dans Exchange Online pour permettre aux entreprises de collaborer avec d’autres entreprises et de permettre aux utilisateurs de partager les planifications (informations de disponibilité) avec d’autres personnes. | <ul><li>[Partage](/exchange/sharing/sharing) </li><li> [Relations des organisations](/exchange/sharing/organization-relationships/organization-relationships) </li><li> [Créer une relation d’organisation](/exchange/sharing/organization-relationships/create-an-organization-relationship) </li><li> [Modifier une relation d’organisation](/exchange/sharing/organization-relationships/modify-an-organization-relationship) </li><li> [Supprimer une relation d’organisation](/exchange/sharing/organization-relationships/remove-an-organization-relationship) </li><li> [Partager des calendriers avec des utilisateurs externes](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|Contrôler la façon dont les utilisateurs partagent leurs calendriers avec des personnes extérieures à votre organisation | Les administrateurs appliquent des stratégies de partage aux boîtes aux lettres des utilisateurs pour contrôler avec qui elles peuvent être partagées et le niveau d’accès accordé |  <ul><li> [Stratégies de partage](/exchange/sharing/sharing-policies/sharing-policies) </li><li> [Créer une stratégie de partage](/exchange/sharing/sharing-policies/create-a-sharing-policy) </li><li> [Appliquer une stratégie de partage aux boîtes aux lettres](/exchange/sharing/sharing-policies/apply-a-sharing-policy) </li><li> [Modifier, désactiver ou supprimer une stratégie de partage](/exchange/sharing/sharing-policies/modify-a-sharing-policy) </li></ul> |
|Configurer des canaux de messagerie sécurisés et contrôler le flux de courrier avec les organisations partenaires | Les administrateurs créent des connecteurs pour appliquer la sécurité aux échanges de courrier avec une organisation partenaire ou un fournisseur de services. Les connecteurs appliquent le chiffrement via TLS (Transport Layer Security) et autorisent des restrictions sur les noms de domaine ou les plages d’adresses IP à partir desquelles vos partenaires envoient des e-mails. |  <ul><li> [Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie](../compliance/exchange-online-uses-tls-to-secure-email-connections.md) </li><li> [Configurer le flux de messagerie à l’aide des connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) </li><li> [Domaines distants](/exchange/mail-flow-best-practices/remote-domains/remote-domains) </li><li> [Configurer le connecteur pour sécuriser le flux de courrier avec une organisation partenaire](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) </li><li> [Meilleures pratiques relatives au flux de courrier (vue d’ensemble)](/exchange/mail-flow-best-practices/mail-flow-best-practices) </li></ul> |

## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>Options de collaboration SharePoint Online et OneDrive Entreprise

| Partage des objectifs | Action administrative | Informations de procédures |
|:-----|:-----|:-----|
|Partager des sites et des documents avec des utilisateurs externes | Les administrateurs configurent le partage au niveau du locataire ou de la collection de sites pour les comptes Microsoft authentifiés, les comptes professionnels ou scolaires authentifiés ou les comptes invités |  <ul><li> [Gérer le partage externe pour votre environnement SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [Restreindre le partage de contenu SharePoint et OneDrive par domaine](/sharepoint/restricted-domains-sharing) </li><li> [Utiliser SharePoint Online comme solution extranet B2B](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|Suivi et contrôle du partage externe pour les utilisateurs finaux | OneDrive Entreprise les propriétaires de fichiers et les utilisateurs finaux SharePoint Online configurent le partage de sites et de documents, et établissent des notifications pour suivre le partage |  <ul><li> [Configurer des notifications pour le partage externe pour OneDrive Entreprise](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [Partager des fichiers ou dossiers SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |

## <a name="skype-for-business-collaboration-options"></a>options de collaboration Skype Entreprise

| Objectif de partage | Action administrative | Informations de procédures |
|:-----|:-----|:-----|
|Skype Entreprise Online : messagerie instantanée, appels et présence avec d’autres utilisateurs Skype Entreprise | Les administrateurs peuvent autoriser leurs utilisateurs Skype Entreprise Online à communiquer par messagerie instantanée, passer des appels audio/vidéo et voir la présence d’utilisateurs dans un autre locataire Microsoft 365. | [Autoriser les utilisateurs à contacter des utilisateurs Skype Entreprise externes](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)|
|Skype Entreprise Online - Messagerie instantanée, appels et présence avec des utilisateurs Skype (consommateurs) | Les administrateurs peuvent activer leur Skype Entreprise les utilisateurs En ligne à la messagerie instantanée, passer des appels et voir la présence avec les utilisateurs Skype (consommateur). | [Autoriser les utilisateurs Skype Entreprise à ajouter des contacts Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)|

## <a name="azure-ad-b2b-collaboration-options"></a>Options de B2B Collaboration Azure AD

| Objectif de partage | Action administrative | Informations de procédures |
|:-----|:-----|:-----|
|Azure AD B2B Collaboration - Partage de contenu en ajoutant des utilisateurs externes à un groupe dans l’annuaire d’une organisation | Un **administrateur Azure AD DC**, **security Administration**, **user Administration**, **cloud application Administration** ou **administrateur général** pour un locataire Microsoft 365 peut inviter des personnes d’un autre locataire Microsoft 365 à rejoindre leur annuaire, à ajouter ces utilisateurs externes à un groupe et à accorder l’accès au contenu, tel que les sites et bibliothèques SharePoint pour le groupe. |  <ul><li> [Qu’est-ce que la préversion d’Azure AD B2B Collaboration ?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B : Les nouvelles mises à jour facilitent la création de collabs interentraux](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [Partage externe et collaboration Azure Active Directory B2B](/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [API et personnalisation azure Active Directory B2B Collaboration](/azure/active-directory/active-directory-b2b-api) </li><li> [Azure AD et Identity Show : Azure AD B2B Collaboration (Business to Business)](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |

## <a name="microsoft-365-collaboration-options"></a>Options de collaboration Microsoft 365

| Objectif de partage | Action administrative | Informations de procédures |
|:-----|:-----|:-----|
|Groupes Microsoft 365 : Email, calendrier, OneNote et fichiers partagés dans un emplacement central | Les groupes sont pris en charge dans les plans Business Essentials, Business Premium, Éducation et Entreprise E1, E3 et E5. Personnes dans un locataire Microsoft 365 peut créer un groupe et inviter des personnes dans un autre locataire Microsoft 365 en tant qu’utilisateurs invités. S’applique également à Dynamics CRM. |  <ul><li> [Apprendre sur les groupes Microsoft 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [Accès invité dans Groupes Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [Déployer Groupes Microsoft 365](/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn896591(v=crm.8)) </li></ul> |

## <a name="yammer-collaboration-options"></a>Options de collaboration Yammer

| Objectif de partage | Action administrative | Informations de procédures |
|:-----|:-----|:-----|
|Yammer - Collaboration via un support social d’entreprise | À moins que la possibilité de créer des groupes externes soit désactivée par un administrateur Yammer, les utilisateurs peuvent créer des groupes externes pour collaborer dans Yammer via des conversations, la possibilité d’aimer et de suivre des publications, de partager des fichiers et de discuter en ligne. | [Créer et gérer des groupes externes dans Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)|

## <a name="teams-collaboration-options"></a>Options de collaboration Teams

|Objectif de partage|Action administrative|Informations de procédures|
|:-----|:-----|:-----|
|Collaborer dans Teams avec des utilisateurs externes à l’organisation | Un **utilisateur Administration** ou **un administrateur général** pour le locataire Microsoft 365 invité doit activer la collaboration externe dans Teams. Les administrateurs généraux et les propriétaires d’équipe pourront désormais inviter toute personne disposant d’une adresse e-mail à collaborer dans Teams.  <br/> Les administrateurs peuvent également gérer et modifier les invités déjà présents dans leur locataire. |  <ul><li> [Autoriser l’accès invité](/microsoftteams/teams-dependencies) </li><li> [Activer ou désactiver l’accès invité dans Teams](/microsoftteams/set-up-guests) </li><li> [Utiliser PowerShell pour contrôler l’accès invité](/microsoftteams/guest-access-powershell) </li><li> [Liste de vérification de l’accès invité](/microsoftteams/guest-access-checklist) </li><li> [Afficher les utilisateurs invités](/microsoftteams/view-guests) </li><li> [Modifier les informations d’un utilisateur invité](/microsoftteams/edit-guests-information) </li></ul> |
|Les propriétaires d’équipe peuvent inviter et gérer la façon dont les invités collaborent au sein de leurs équipes.  |Les propriétaires d’équipe disposent de contrôles supplémentaires sur ce que les invités peuvent faire au sein de leurs équipes. |  <ul><li> [Ajouter des invités](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [Ajouter un invité à une équipe](/microsoftteams/add-guests) </li><li> [Gérer l’accès invité dans Teams](/microsoftteams/manage-guests) </li><li> [Voir les membres d’une équipe ou d’un canal](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|Les invités d’autres locataires peuvent afficher le contenu dans Teams et collaborer avec d’autres membres | Aucun. | [Expérience d’accès invité](/microsoftteams/guest-experience)|

## <a name="power-bi-collaboration-options"></a>Options de collaboration Power BI

| Objectif de partage | Action administrative | Informations de procédures |
|:-----|:-----|:-----|
|Power BI permet aux utilisateurs invités externes de consommer du contenu partagé avec eux via des liens. Cela permet aux utilisateurs de l’organisation de distribuer du contenu de manière sécurisée entre les organisations.<br/> | Le Administration Power BI peut contrôler si les utilisateurs peuvent inviter des utilisateurs externes à afficher du contenu au sein de l’organisation.| [Distribuer du contenu Power BI à des utilisateurs invités externes avec Azure AD B2B](/power-bi/service-admin-azure-ad-b2b) |

## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>Points à connaître sur la collaboration entre locataires Microsoft 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Partage de comptes d’utilisateur, de licences, d’abonnements et de stockage

Chaque organisation gère ses propres comptes d’utilisateur, identités, groupes de sécurité, abonnements, licences et stockage. Personnes utiliser les fonctionnalités de collaboration dans Microsoft 365 avec des stratégies de partage et des paramètres de sécurité pour fournir l’accès aux informations nécessaires tout en conservant le contrôle des ressources de l’entreprise.

- **Comptes d’utilisateur :** Les comptes ne peuvent pas être partagés ou dupliqués entre les locataires ou les partitions dans les services de domaine Active Directory local.

- **Abonnements aux licences &amp; :** Dans Microsoft 365, les licences des plans de licence (également appelées références SKU ou plans Microsoft 365) permettent aux utilisateurs d’accéder aux services Microsoft 365 définis pour ces plans.

- **Stockage:** Dans les plans de licence Microsoft 365, les limites logicielles et les limites pour SharePoint Online sont gérées séparément des limites de stockage des boîtes aux lettres. Les limites de stockage de boîte aux lettres sont configurées et gérées à l’aide de Exchange Online. Dans les deux scénarios, le stockage ne peut pas être partagé entre les locataires.

### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>Pouvons-nous partager des espaces de noms de domaine entre des locataires Microsoft 365 ?

Non. Les noms de domaine d’organisation, tels que fabrikam.com ou tailspintoys.com, ne peuvent être associés et utilisés qu’avec un seul locataire Microsoft 365. Chaque locataire doit avoir son propre espace de noms. Les espaces de noms UPN, SMTP et SIP ne peuvent pas être partagés entre les locataires.

### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>Qu’en est-il des composants hybrides et de la collaboration entre locataires Microsoft 365 ?

Les composants hybrides locaux, tels qu’une organisation Exchange et Azure AD Connect, ne peuvent pas être répartis entre plusieurs locataires.
