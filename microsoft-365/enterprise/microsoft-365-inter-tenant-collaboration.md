---
title: Collaboration entre clients Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
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
description: Découvrez comment la collaboration Microsoft 365 fonctionne entre les clients et les organisations, ce qui permet à différentes organisations de collaborer en toute sécurité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 00eacfc21d3223b5b9a1ad420cd5d1d85bf4ea8e
ms.sourcegitcommit: 11d1044c6600b1f568b6dc8a53db9b07f2f0ad1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "48384824"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Collaboration entre clients Microsoft 365

Supposons que deux organisations, Fabrikam et Contoso, ont chacune un client Microsoft 365 pour les entreprises et qu’elles souhaitent collaborer sur plusieurs projets ; certains d’entre eux s’exécutent pendant une durée limitée et d’autres sont en cours. Comment Fabrikam et Contoso peuvent-ils permettre à leurs employés et équipes de collaborer plus efficacement entre leurs différents clients Microsoft 365 de manière sécurisée ? Microsoft 365, conjointement avec azure Active Directory (Azure AD) B2B collaboration, fournit plusieurs options. Cet article décrit plusieurs scénarios clés que Fabrikam et Contoso peuvent prendre en compte.
  
Les options de collaboration entre clients Microsoft 365 incluent l’utilisation d’un emplacement central pour les fichiers et les conversations, le partage de calendriers, l’utilisation de la messagerie instantanée, des appels audio/vidéo pour la communication et la sécurisation de l’accès aux ressources et aux applications. Utilisez les tableaux suivants pour sélectionner des solutions et en savoir plus.
  
## <a name="exchange-online-collaboration-options"></a>Options de collaboration Exchange Online

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Partager des calendriers avec une autre organisation Microsoft 365 |Les administrateurs peuvent configurer différents niveaux d’accès au calendrier dans Exchange Online pour permettre aux entreprises de collaborer avec d’autres entreprises et pour permettre aux utilisateurs de partager les plannings (informations de libre/occupé) avec d’autres personnes. | <ul><li>[Partage](https://technet.microsoft.com/library/jj916670%28v=exchg.150%29.aspx) </li><li> [Relations des organisations](https://technet.microsoft.com/library/jj916658%28v=exchg.150%29.aspx) </li><li> [Créer une relation d’organisation](https://technet.microsoft.com/library/jj916671%28v=exchg.150%29.aspx) </li><li> [Modifier une relation organisationnelle ](https://technet.microsoft.com/library/jj916659%28v=exchg.150%29.aspx) </li><li> [Supprimer une relation d’organisation](https://technet.microsoft.com/library/jj916657%28v=exchg.150%29.aspx) </li><li> [Partager des calendriers avec des utilisateurs externes](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|Contrôler la façon dont les utilisateurs partagent leurs calendriers avec des personnes extérieures à votre organisation | Les administrateurs appliquent des stratégies de partage aux boîtes aux lettres des utilisateurs pour contrôler avec qui il peut être partagé et le niveau d’accès accordé |  <ul><li> [Stratégies de partage](https://technet.microsoft.com/library/jj916673%28v=exchg.150%29.aspx) </li><li> [Créer une stratégie de partage](https://technet.microsoft.com/library/jj916676%28v=exchg.150%29.aspx) </li><li> [Appliquer une stratégie de partage aux boîtes aux lettres](https://technet.microsoft.com/library/jj916672%28v=exchg.150%29.aspx) </li><li> [Modifier, désactiver ou supprimer une stratégie de partage](https://technet.microsoft.com/library/jj916674%28v=exchg.150%29.aspx) </li></ul> |
|Configurer des canaux de messagerie sécurisés et contrôler le flux de messagerie avec les organisations partenaires | Les administrateurs créent des connecteurs pour appliquer la sécurité aux échanges de messages avec une organisation partenaire ou un fournisseur de services. Les connecteurs appliquent le chiffrement via le protocole TLS (Transport Layer Security) et autorisent des restrictions sur les noms de domaine ou les plages d’adresses IP à partir des envois de messages électroniques par vos partenaires. |  <ul><li> [Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie](https://technet.microsoft.com/library/mt163898.aspx) </li><li> [Configurer le flux de messagerie à l’aide des connecteurs](https://technet.microsoft.com/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) </li><li> [Domaines distants](https://technet.microsoft.com/library/jj966211%28v=exchg.150%29.aspx) </li><li> [Configurer un connecteur pour un flux de messagerie sécurisé avec une organisation partenaire](https://technet.microsoft.com/library/dn751021%28v=exchg.150%29.aspx) </li><li> [Meilleures pratiques en matière de flux de messagerie (vue d’ensemble)](https://technet.microsoft.com/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) </li></ul> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>Options de collaboration SharePoint Online et OneDrive Entreprise

| Objectifs de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Partager des sites et des documents avec des utilisateurs externes | Les administrateurs configurent le partage au niveau du client ou de la collection de sites pour le compte Microsoft authentifié, le compte professionnel ou scolaire authentifié ou les comptes invités |  <ul><li> [Gérer le partage externe pour votre environnement SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [Restreindre le partage de contenu SharePoint et OneDrive par domaine](https://docs.microsoft.com/sharepoint/restricted-domains-sharing) </li><li> [Utiliser SharePoint Online en tant que solution extranet business-to-business (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|Suivi et contrôle du partage externe pour les utilisateurs finaux | Les propriétaires de fichiers OneDrive Entreprise et les utilisateurs finaux SharePoint Online configurent le partage de sites et de documents et établissent des notifications pour suivre le partage |  <ul><li> [Configurer des notifications pour le partage externe pour OneDrive Entreprise](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [Partager des fichiers ou dossiers SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |
   
## <a name="skype-for-business-collaboration-options"></a>Options de collaboration Skype Entreprise

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Skype Entreprise Online : messagerie instantanée, appels et présence avec d’autres utilisateurs de Skype Entreprise | Les administrateurs peuvent activer la messagerie instantanée pour leurs utilisateurs Skype Entreprise Online, effectuer des appels audio/vidéo et voir la présence des utilisateurs dans un autre client Microsoft 365. | [Autoriser les utilisateurs à contacter des utilisateurs Skype Entreprise externes](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)| 
|Skype Entreprise Online : messagerie instantanée, appels et présence avec les utilisateurs de Skype (grand public) | Les administrateurs peuvent activer la messagerie instantanée pour leurs utilisateurs Skype Entreprise Online, effectuer des appels et consulter la présence des utilisateurs de Skype (consommateur). | [Autoriser les utilisateurs Skype Entreprise à ajouter des contacts Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)| 
   
## <a name="azure-ad-b2b-collaboration-options"></a>Options de collaboration Azure AD B2B

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Collaboration Azure AD B2B : partage de contenu en ajoutant des utilisateurs externes à un groupe dans l’annuaire d’une organisation | Un administrateur général pour un client Microsoft 365 peut inviter des personnes d’un autre client Microsoft 365 à rejoindre leur annuaire, ajouter ces utilisateurs externes à un groupe et accorder l’accès à du contenu, tel que des sites et des bibliothèques SharePoint pour le groupe. |  <ul><li> [Qu’est-ce qu’Azure AD B2B Collaboration Preview ?](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B : les nouvelles mises à jour rendent le collab entre entreprises facile](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [Partage externe et collaboration B2B Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [Personnalisation et API de collaboration B2B Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-api) </li><li> [Azure AD et Identity Show : Collaboration Azure AD B2B (Entreprise à Entreprise)](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |
   
## <a name="microsoft-365-collaboration-options"></a>Options de collaboration Microsoft 365

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Groupes Microsoft 365 : messagerie électronique, calendrier, OneNote et fichiers partagés à un endroit central | Les groupes sont pris en charge dans les plans Business Essentials, Business Premium, Éducation et Entreprise E1, E3 et E5. Les personnes d’un client Microsoft 365 peuvent créer un groupe et inviter des personnes dans un autre client Microsoft 365 en tant qu’utilisateurs invités. S’applique également à Dynamics CRM. |  <ul><li> [En savoir plus sur les groupes Microsoft 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [Accès invité dans les groupes Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [Déployer des groupes Microsoft 365](https://technet.microsoft.com/library/dn896591.aspx) </li></ul> |
   
## <a name="yammer-collaboration-options"></a>Yammer options de collaboration

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Yammer : collaboration via un support social d’entreprise | À moins que la possibilité de créer des groupes externes ne soit désactivée par un administrateur Yammer, les utilisateurs peuvent créer des groupes externes pour collaborer dans Yammer via des conversations, la possibilité d’aimer et de suivre des billets, de partager des fichiers et de discuter en ligne. | [Créer et gérer des groupes externes dans Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)| 
   
## <a name="teams-collaboration-options"></a>Options de collaboration Teams

|Objectif de partage|Action administrative|Informations sur les how-to|
|:-----|:-----|:-----|
|Collaborer dans Teams avec des utilisateurs externes à l’organisation | Un administrateur global pour l’invitation du client Microsoft 365 doit activer la collaboration externe dans Teams. Les administrateurs globaux et les propriétaires d’équipe peuvent désormais inviter toute personne ayant une adresse de messagerie à collaborer dans Teams.  <br/> Les administrateurs peuvent également gérer et modifier les invités déjà présents dans leur client. |  <ul><li> [Autoriser l’accès invité](https://docs.microsoft.com/microsoftteams/teams-dependencies) </li><li> [Activer ou désactiver l’accès invité dans Teams](https://docs.microsoft.com/microsoftteams/set-up-guests) </li><li> [Utiliser PowerShell pour contrôler l’accès invité](https://docs.microsoft.com/microsoftteams/guest-access-powershell) </li><li> [Liste de contrôle d’accès invité](https://docs.microsoft.com/microsoftteams/guest-access-checklist) </li><li> [Afficher les utilisateurs invités](https://docs.microsoft.com/microsoftteams/view-guests) </li><li> [Modifier les informations d’un utilisateur invité](https://docs.microsoft.com/microsoftteams/edit-guests-information) </li></ul> |
|Les propriétaires d’équipe peuvent inviter et gérer la façon dont les invités collaborent au sein de leurs équipes.  |Les propriétaires d’équipes ont des contrôles supplémentaires sur ce que les invités peuvent faire au sein de leurs équipes. |  <ul><li> [Ajouter des invités](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [Ajouter un invité à une équipe](https://docs.microsoft.com/microsoftteams/add-guests) </li><li> [Gérer l’accès invité dans Teams](https://docs.microsoft.com/microsoftteams/manage-guests) </li><li> [Voir qui fait équipe ou dans un canal](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|Les invités d’autres clients peuvent afficher le contenu dans Teams et collaborer avec d’autres membres | Aucun. | [Expérience d’accès invité](https://docs.microsoft.com/microsoftteams/guest-experience)| 

## <a name="power-bi-collaboration-options"></a>Options de collaboration Power BI

| Objectif de partage | Action administrative | Informations sur les how-to |
|:-----|:-----|:-----|
|Power BI permet aux utilisateurs invités externes d’utiliser du contenu qui leur est partagé via des liens. Cela permet aux utilisateurs de l’organisation de distribuer du contenu de manière sécurisée entre les organisations.<br/> | L’administrateur Power BI peut contrôler si les utilisateurs peuvent inviter des utilisateurs externes à afficher du contenu au sein de l’organisation.| [Distribuer du contenu Power BI à des utilisateurs invités externes avec Azure AD B2B](https://docs.microsoft.com/power-bi/service-admin-azure-ad-b2b) | 
 
## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>Points à connaître sur la collaboration entre clients Microsoft 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Partage de comptes d’utilisateurs, de licences, d’abonnements et de stockage

Chaque organisation conserve ses propres comptes d’utilisateur, identités, groupes de sécurité, abonnements, licences et stockage. Les personnes utilisent les fonctionnalités de collaboration dans Microsoft 365 avec les stratégies de partage et les paramètres de sécurité pour fournir l’accès aux informations nécessaires tout en conservant le contrôle des biens de l’entreprise.
  
- **Comptes d’utilisateur :** Les comptes ne peuvent pas être partagés ou dupliqués entre les locataires ou les partitions dans les services de domaine Active Directory locaux. 
    
- **Abonnements aux &amp; licences** : dans Microsoft 365, les licences des plans de gestion des licences (également appelées SSK ou plans Microsoft 365) donnent aux utilisateurs l’accès aux services Microsoft 365 définis pour ces plans. 
    
- **Stockage :** Dans les plans de gestion des licences Microsoft 365, les limites et frontières logicielles pour SharePoint Online sont gérées séparément des limites de stockage des boîtes aux lettres. Les limites de stockage de boîtes aux lettres sont définies et gérées à l’aide d’Exchange Online. Dans les deux scénarios, le stockage ne peut pas être partagé entre les locataires. 
    
### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>Pouvons-nous partager des espaces de noms de domaine entre des clients Microsoft 365 ?

Non. Les noms de domaine d’organisation, tels fabrikam.com ou tailspintoys.com, ne peuvent être associés et utilisés qu’avec un seul client Microsoft 365. Chaque client doit avoir son propre espace de noms. Les espaces de noms UPN, SMTP et SIP ne peuvent pas être partagés entre les locataires.
  
### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>Qu’en est-il des composants hybrides et de la collaboration entre clients Microsoft 365 ?

Les composants hybrides locaux, tels qu’une organisation Exchange et Azure AD Connect, ne peuvent pas être répartis sur plusieurs locataires.
 

