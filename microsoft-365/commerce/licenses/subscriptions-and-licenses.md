---
title: Comprendre les abonnements et les licences dans Microsoft 365 entreprise
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: micurn, nicholak
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- okr_smb
- AdminSurgePortfolio
- manage_licenses
- commerce_licensing
- AdminTemplateSet
search.appverid: MET150
description: Les applications et les services que vous recevez dépendent du produit Microsoft 365 que vous avez acheté, par exemple, Applications Microsoft 365 pour les PME.
ms.date: 07/01/2020
ms.openlocfilehash: e380ac61033435a86118f7178da9e014d13ad436
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62524044"
---
# <a name="understand-subscriptions-and-licenses-in-microsoft-365-for-business"></a>Comprendre les abonnements et les licences dans Microsoft 365 entreprise

Lorsque vous achetez un abonnement à Microsoft 365 entreprise, vous vous inscrivez pour un ensemble d’applications et de services que vous payez sur une base mensuelle ou annuelle. Les applications et services que vous recevez dans le cadre de votre abonnement dépendent du produit que vous avez acheté, tel que Applications Microsoft 365 pour les PME ou Microsoft 365 Business Standard. Vous pouvez voir ce qui est livré avec chaque produit sur la [Microsoft 365 page](https://products.office.com/compare-all-microsoft-office-products?&activetab=tab:primaryr1) pour les petites et moyennes entreprises.

Lorsque vous achetez un abonnement, vous spécifiez le nombre de licences dont vous avez besoin, en fonction du nombre de personnes de votre organisation. Après avoir acheté un abonnement, vous créez des comptes pour les membres de votre organisation, puis attribuez une licence à chaque personne. À mesure que les besoins de votre organisation changent, vous pouvez acheter d’autres licences pour prendre en charge de nouvelles personnes ou réaffecter des licences à d’autres utilisateurs lorsqu’une personne quitte votre organisation.

Si vous disposez de plusieurs abonnements, vous pouvez attribuer des licences à différentes personnes pour chaque abonnement. Par exemple, vous pouvez affecter tous vos utilisateurs à tous les services et applications Microsoft 365 dans le cadre d’un abonnement Microsoft 365 Business Standard’abonnement. Vous pouvez également affecter un sous-ensemble d’utilisateurs à Visio Online via un abonnement Visio distinct.

## <a name="how-many-devices-can-people-install-office-on"></a>Sur combien d'appareils les utilisateurs peuvent-ils installer Office ?

Si votre abonnement inclut l’un des produits suivants, chaque utilisateur peut installer Office sur cinq PC ou Mac, cinq tablettes et cinq téléphones.

:::row:::
   :::column span="":::
        - Applications Microsoft 365 pour les PME - Applications Microsoft 365 pour les grandes entreprises - Microsoft 365 Business Standard - Microsoft 365 Business Premium - Microsoft 365 A3 - Microsoft 365 A5
   :::column-end:::
   :::column span="":::
        - Microsoft 365 E3 - Microsoft 365 E5 - Office 365 A1 Plus - Office 365 A3 - Office 365 A5 - Office 365 E3 - Office 365 E5
   :::column-end:::
:::row-end:::

## <a name="what-happens-when-you-assign-a-license-to-someone"></a>Que se passe-t-il lorsque vous attribuez une licence à une personne ?

Le tableau suivant indique ce qui se produit automatiquement lorsque vous attribuez une licence à quelqu'un :
  
|**Si l'abonnement inclut ce service**|**Cet événement se produit automatiquement**|
|:-----|:-----|
|Exchange Online  <br/> |Une boîte aux lettres est créée pour cette personne. <br/> Pour en savoir plus sur le SLA de cette tâche à accomplir, voir [« Configuration... » dans le Centre d'administration Microsoft 365](https://support.microsoft.com/help/2635238/setting-up-messages-in-the-office-365-admin-center). |
|SharePoint Online  <br/> |Les autorisations de modification du site d'équipe SharePoint Online par défaut sont attribuées à cette personne.  <br/> |
|Skype Entreprise Online  <br/> |La personne a accès aux fonctionnalités associées à la licence.  <br/> |
|Applications Microsoft 365 pour les grandes entreprises et Applications Microsoft 365 pour les PME  <br/> |La personne peut télécharger Office applications sur cinq Mac ou PC, cinq tablettes et cinq smartphones au plus.  <br/> |

## <a name="understand-licenses-for-non-user-mailboxes"></a>Comprendre les licences pour les boîtes aux lettres non-utilisateur

Vous n'êtes pas obligé d'attribuer des licences aux boîtes aux lettres de ressources, de salle, et partagées, sauf si elles dépassent leur quota de stockage de 50 gigaoctets (Go). Pour plus d'informations sur les boîtes aux lettres non-utilisateur, voir les articles suivants :
  
- [Créer une boîte aux lettres partagée](../../admin/email/create-a-shared-mailbox.md)
- [Supprimer une licence à partir d’une boîte aux lettres partagée](../../admin/email/remove-license-from-shared-mailbox.md)
- [Boîtes aux lettres partagées dans Exchange Online](/exchange/collaboration-exo/shared-mailboxes) pour tous les autres plans Microsoft 365 de messagerie.

## <a name="who-can-assign-licenses"></a>Qui pouvez attribuer des licences ?

Plusieurs types d'administrateurs peuvent utiliser des licences de différentes façons, en fonction de leur rôle. Le tableau ci-dessous recense les options les plus courantes. Pour consulter la liste complète des rôles et des privilèges d'administrateur, voir [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  
|**Rôle d'administrateur**|**Attribuer une licence**|**Désattribuer une licence**|**Acheter d’autres licences**|**Supprimer un compte**|
|:-----|:-----|:-----|:-----|:-----|
|Administrateur de facturation  <br/> |Non  <br/> |Non  <br/> |Oui  <br/> |Non  <br/> |
|Administrateur global  <br/> |Oui  <br/> |Oui  <br/> |Oui  <br/> |Oui  <br/> |
|Administrateur de licences <br/> |Oui <br/>|Oui <br/> |Non <br/> |Non <br/> |
|Administrateur de support de service  <br/> |Non  <br/> |Non  <br/> |Non  <br/> |Non  <br/> |
|Administrateur d’utilisateurs  <br/> |Oui  <br/> |Oui  <br/> |Non  <br/> |Oui  <br/> |

## <a name="related-content"></a>Contenu associé

[Acheter ou supprimer des licences pour votre abonnement commercial](buy-licenses.md) (article)\
[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)\
[Déattribuer des licences aux utilisateurs](../../admin/manage/remove-licenses-from-users.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](../../admin/email/remove-license-from-shared-mailbox.md) (article)
