---
title: Microsoft 365 collaboration entre les locataires
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
f1.keywords:
- NOCSH
description: Découvrez comment Microsoft 365 collaboration fonctionne entre les locataires et les organisations, ce qui permet à différentes organisations de collaborer en toute sécurité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9cb91b6bcaac212eeaf0ef4051f466751d8dbbd9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60163335"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Microsoft 365 collaboration entre les locataires

Supposons que deux organisations, Fabrikam et Contoso, ont chacune un client Microsoft 365 entreprise et qu’elles souhaitent collaborer sur plusieurs projets ; certains d’entre eux s’exécutent pendant une durée limitée et d’autres sont en cours. Comment Fabrikam et Contoso peuvent-ils permettre à leurs employés et équipes de collaborer plus efficacement entre leurs différents locataires Microsoft 365 de manière sécurisée ? Microsoft 365, conjointement avec Azure Active Directory collaboration B2B (Azure AD), fournit plusieurs options. Cet article décrit plusieurs scénarios clés que Fabrikam et Contoso peuvent prendre en compte.

Microsoft 365 options de collaboration entre clients incluent l’utilisation d’un emplacement central pour les fichiers et les conversations, le partage de calendriers, l’utilisation de la messagerie instantanée, des appels audio/vidéo pour la communication et la sécurisation de l’accès aux ressources et aux applications. Utilisez les tableaux suivants pour sélectionner des solutions et en savoir plus.

## <a name="exchange-online-collaboration-options"></a>Exchange Online options de collaboration

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Partager des calendriers avec une autre Microsoft 365 organisation |Les administrateurs peuvent configurer différents niveaux d’accès au calendrier dans Exchange Online pour permettre aux entreprises de collaborer avec d’autres entreprises et permettre aux utilisateurs de partager les plannings (informations de libre/occupé) avec d’autres personnes. | <ul><li>[Partage](/exchange/sharing/sharing) </li><li> [Relations des organisations](/exchange/sharing/organization-relationships/organization-relationships) </li><li> [Créer une relation d’organisation](/exchange/sharing/organization-relationships/create-an-organization-relationship) </li><li> [Modifier une relation d’organisation](/exchange/sharing/organization-relationships/modify-an-organization-relationship) </li><li> [Supprimer une relation d’organisation](/exchange/sharing/organization-relationships/remove-an-organization-relationship) </li><li> [Partager des calendriers avec des utilisateurs externes](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|Contrôler la façon dont les utilisateurs partagent leurs calendriers avec des personnes extérieures à votre organisation | Les administrateurs appliquent des stratégies de partage aux boîtes aux lettres des utilisateurs pour contrôler avec qui il peut être partagé et le niveau d’accès accordé |  <ul><li> [Stratégies de partage](/exchange/sharing/sharing-policies/sharing-policies) </li><li> [Créer une stratégie de partage](/exchange/sharing/sharing-policies/create-a-sharing-policy) </li><li> [Appliquer une stratégie de partage aux boîtes aux lettres](/exchange/sharing/sharing-policies/apply-a-sharing-policy) </li><li> [Modifier, désactiver ou supprimer une stratégie de partage](/exchange/sharing/sharing-policies/modify-a-sharing-policy) </li></ul> |
|Configurer des canaux de messagerie sécurisés et contrôler le flux de messagerie avec les organisations partenaires | Les administrateurs créent des connecteurs pour appliquer la sécurité aux échanges de messages avec une organisation partenaire ou un fournisseur de services. Les connecteurs appliquent le chiffrement via le protocole TLS (Transport Layer Security) et autorisent des restrictions sur les noms de domaine ou les plages d’adresses IP à partir des envois de courrier électronique par vos partenaires. |  <ul><li> [Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie](../compliance/exchange-online-uses-tls-to-secure-email-connections.md) </li><li> [Configurer le flux de messagerie à l’aide des connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) </li><li> [Domaines distants](/exchange/mail-flow-best-practices/remote-domains/remote-domains) </li><li> [Configurer un connecteur pour un flux de messagerie sécurisé avec une organisation partenaire](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) </li><li> [Meilleures pratiques en matière de flux de messagerie (vue d’ensemble)](/exchange/mail-flow-best-practices/mail-flow-best-practices) </li></ul> |

## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Options de collaboration OneDrive Entreprise en ligne et en ligne

| Objectifs de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Partager des sites et des documents avec des utilisateurs externes | Les administrateurs configurent le partage au niveau du client ou de la collection de sites pour le compte Microsoft authentifié, le compte professionnel ou scolaire authentifié ou les comptes invités |  <ul><li> [Gérer le partage externe pour votre environnement SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [Restreindre le partage de contenu SharePoint et OneDrive par domaine](/sharepoint/restricted-domains-sharing) </li><li> [Utiliser SharePoint Online en tant que solution extranet B2B (business-to-business)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|Suivi et contrôle du partage externe pour les utilisateurs finaux | OneDrive Entreprise propriétaires de fichiers et SharePoint les utilisateurs finaux en ligne configurent le partage de sites et de documents et établissent des notifications pour suivre le partage |  <ul><li> [Configurer des notifications pour le partage externe pour OneDrive Entreprise](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [Partager des fichiers ou dossiers SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |

## <a name="skype-for-business-collaboration-options"></a>Skype Entreprise options de collaboration

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Skype Entreprise En ligne : messagerie instantanée, appels et présence avec d’autres Skype Entreprise utilisateurs | Les administrateurs peuvent activer leurs utilisateurs Skype Entreprise Online pour la messagerie instantanée, effectuer des appels audio/vidéo et voir la présence des utilisateurs dans un autre Microsoft 365 client. | [Autoriser les utilisateurs à contacter des utilisateurs Skype Entreprise externes](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)|
|Skype Entreprise En ligne : messagerie instantanée, appels et présence avec Skype utilisateurs (consommateurs) | Les administrateurs peuvent activer Skype Entreprise utilisateurs en ligne pour la messagerie instantanée, effectuer des appels et voir la présence Skype utilisateurs (consommateurs). | [Autoriser les utilisateurs Skype Entreprise à ajouter des contacts Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)|

## <a name="azure-ad-b2b-collaboration-options"></a>Options de collaboration Azure AD B2B

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Collaboration Azure AD B2B : partage de contenu en ajoutant des utilisateurs externes à un groupe dans l’annuaire d’une organisation | Un administrateur Azure **AD DC,** un administrateur de  **sécurité,** un administrateur **utilisateur,** un administrateur d’application **cloud** ou un administrateur général pour un client Microsoft 365 peut inviter des personnes d’un autre client Microsoft 365 à rejoindre leur annuaire, ajouter ces utilisateurs externes à un groupe et accorder l’accès au contenu, tel que les sites SharePoint et les bibliothèques pour le groupe. |  <ul><li> [Qu’est-ce qu’Azure AD B2B Collaboration Preview ?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B : les nouvelles mises à jour rendent le collab entre entreprises facile](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [Partage externe et Azure Active Directory collaboration B2B](/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [Azure Active Directory API de collaboration B2B et personnalisation](/azure/active-directory/active-directory-b2b-api) </li><li> [Azure AD et Identity Show : Collaboration Azure AD B2B (Entreprise à Entreprise)](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |

## <a name="microsoft-365-collaboration-options"></a>Microsoft 365 options de collaboration

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Microsoft 365 Groupes : messagerie électronique, calendrier, OneNote et fichiers partagés à un endroit central | Les groupes sont pris en charge dans Business Essentials, Business Premium, Éducation et les plans Enterprise E1, E3 et E5. Les personnes d’un Microsoft 365 client peuvent créer un groupe et inviter des personnes dans un autre Microsoft 365 client en tant qu’utilisateurs invités. S’applique également à Dynamics CRM. |  <ul><li> [Apprendre sur les groupes Microsoft 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [Accès invité dans Microsoft 365 groupes](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [Déployer Microsoft 365 groupes](/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn896591(v=crm.8)) </li></ul> |

## <a name="yammer-collaboration-options"></a>Yammer options de collaboration

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Yammer : collaboration via un support social d’entreprise | À moins que la possibilité de créer des groupes externes soit désactivée par un administrateur Yammer, les utilisateurs peuvent créer des groupes externes pour collaborer dans Yammer via des conversations, la possibilité d’aimer et de suivre des billets, de partager des fichiers et de discuter en ligne. | [Créer et gérer des groupes externes dans Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)|

## <a name="teams-collaboration-options"></a>Teams options de collaboration

|Objectif de partage|Action administrative|Informations sur les how-to|
|:-----|:-----|:-----|
|Collaborer dans Teams avec des utilisateurs externes à l’organisation | Un **administrateur utilisateur** ou un administrateur **global** pour l’invitation Microsoft 365 client doit activer la collaboration externe dans Teams. Les administrateurs globaux et les propriétaires d’équipe peuvent désormais inviter toute personne ayant une adresse de messagerie à collaborer dans Teams.  <br/> Les administrateurs peuvent également gérer et modifier les invités déjà présents dans leur client. |  <ul><li> [Autoriser l’accès invité](/microsoftteams/teams-dependencies) </li><li> [Activer ou désactiver l’accès invité dans Teams](/microsoftteams/set-up-guests) </li><li> [Utiliser PowerShell pour contrôler l’accès invité](/microsoftteams/guest-access-powershell) </li><li> [Liste de contrôle d’accès invité](/microsoftteams/guest-access-checklist) </li><li> [Afficher les utilisateurs invités](/microsoftteams/view-guests) </li><li> [Modifier les informations d’un utilisateur invité](/microsoftteams/edit-guests-information) </li></ul> |
|Les propriétaires d’équipe peuvent inviter et gérer la façon dont les invités collaborent au sein de leurs équipes.  |Les propriétaires d’équipes ont des contrôles supplémentaires sur ce que les invités peuvent faire au sein de leurs équipes. |  <ul><li> [Ajouter des invités](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [Ajouter un invité à une équipe](/microsoftteams/add-guests) </li><li> [Gérer l’accès invité dans Teams](/microsoftteams/manage-guests) </li><li> [Voir qui fait équipe ou dans un canal](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|Les invités d’autres clients peuvent afficher le contenu dans Teams et collaborer avec d’autres membres | Aucun. | [Expérience d’accès invité](/microsoftteams/guest-experience)|

## <a name="power-bi-collaboration-options"></a>Power BI de collaboration

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Power BI permet aux utilisateurs invités externes d’utiliser du contenu qui leur est partagé via des liens. Cela permet aux utilisateurs de l’organisation de distribuer du contenu de manière sécurisée entre les organisations.<br/> | L’administrateur Power BI peut contrôler si les utilisateurs peuvent inviter des utilisateurs externes à afficher du contenu au sein de l’organisation.| [Distribuer Power BI contenu aux utilisateurs invités externes avec Azure AD B2B](/power-bi/service-admin-azure-ad-b2b) |

## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>Points à connaître sur la collaboration entre Microsoft 365 client

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Partage de comptes d’utilisateurs, de licences, d’abonnements et de stockage

Chaque organisation conserve ses propres comptes d’utilisateur, identités, groupes de sécurité, abonnements, licences et stockage. Les personnes utilisent les fonctionnalités de collaboration dans Microsoft 365 avec les stratégies de partage et les paramètres de sécurité pour fournir l’accès aux informations nécessaires tout en conservant le contrôle des biens de l’entreprise.

- **Comptes d’utilisateur :** Les comptes ne peuvent pas être partagés ou dupliqués entre les locataires ou les partitions dans les services de domaine Active Directory locaux.

- **Abonnements &amp; aux licences** : dans Microsoft 365, les licences des plans de gestion des licences (également appelées plans SSK ou plans Microsoft 365) donnent aux utilisateurs l’accès aux services Microsoft 365 définis pour ces plans.

- **Stockage :** Dans Microsoft 365 plans de gestion des licences, les limites et frontières logicielles pour SharePoint Online sont gérées séparément des limites de stockage des boîtes aux lettres. Les limites de stockage de boîtes aux lettres sont définies et gérées à l’aide Exchange Online. Dans les deux scénarios, le stockage ne peut pas être partagé entre les locataires.

### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>Pouvons-nous partager des espaces de noms de domaine Microsoft 365 locataires ?

Non. Les noms de domaine d’organisation, tels fabrikam.com ou tailspintoys.com, ne peuvent être associés et utilisés qu’avec un seul Microsoft 365 client. Chaque client doit avoir son propre espace de noms. Les espaces de noms UPN, SMTP et SIP ne peuvent pas être partagés entre les locataires.

### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>Qu’en est-il des composants hybrides et Microsoft 365 collaboration inter-locataires ?

Les composants hybrides locaux, tels qu’une organisation Exchange et azure AD Connecter, ne peuvent pas être répartis sur plusieurs locataires.
