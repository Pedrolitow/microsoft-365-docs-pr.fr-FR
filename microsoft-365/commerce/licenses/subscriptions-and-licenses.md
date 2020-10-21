---
title: Comprendre les abonnements et les licences dans Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_TOC
- commerce
ms.custom:
- okr_SMB
- AdminSurgePortfolio
- manage_licenses
search.appverid:
- MET150
description: Découvrez les abonnements et les licences dans Microsoft 365 pour les entreprises.
ms.date: 07/01/2020
ms.openlocfilehash: 51d07e777fd5a9e44c864ea11bb00ddc8c1c70d1
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48638194"
---
# <a name="understand-subscriptions-and-licenses-in-microsoft-365-for-business"></a>Comprendre les abonnements et les licences dans Microsoft 365 pour les entreprises

Lorsque vous achetez un abonnement à Microsoft 365 pour les entreprises, vous vous inscrivez à un ensemble d’applications et de services que vous payez mensuellement ou annuellement. Les applications et les services que vous recevez dans le cadre de votre abonnement dépendent du produit que vous avez acheté, tel que Microsoft 365 Apps for Business ou Microsoft 365 Business standard. Vous pouvez voir ce qui est fourni avec chaque produit sur la page [Microsoft 365 pour les petites et moyennes entreprises](https://products.office.com/compare-all-microsoft-office-products?&activetab=tab:primaryr1) .

Lorsque vous achetez un abonnement, vous spécifiez le nombre de licences dont vous avez besoin, en fonction du nombre de personnes de votre organisation. Après avoir acheté un abonnement, vous créez des comptes pour les personnes de votre organisation, puis attribuez une licence à chaque personne. À mesure que les besoins de votre organisation évoluent, vous pouvez acheter des licences supplémentaires pour accueillir de nouvelles personnes ou réattribuer des licences à d’autres utilisateurs lorsqu’un utilisateur quitte votre organisation.

Si vous disposez de plusieurs abonnements, vous pouvez attribuer des licences à différentes personnes pour chaque abonnement. Par exemple, vous pouvez affecter tous vos utilisateurs à l’ensemble des applications et services Microsoft 365 dans le cadre d’un abonnement Microsoft 365 Business standard. Vous pouvez également affecter un sous-ensemble d’utilisateurs à Visio online via un abonnement Visio distinct.

## <a name="how-many-devices-can-people-install-office-on"></a>Sur combien d'appareils les utilisateurs peuvent-ils installer Office ?

Si votre abonnement inclut l’un des produits suivants, chaque personne peut installer Office sur un maximum de cinq PC ou Mac, cinq tablettes et cinq téléphones.

:::row:::
   :::column span="":::
        -Microsoft 365 Apps for Business-Microsoft 365 applications pour les entreprises-Microsoft 365 Business standard-Microsoft 365 Business Premium-Microsoft 365 a3-Microsoft 365 a5
   :::column-end:::
   :::column span="":::
        -Microsoft 365 E3-Microsoft 365 E5-Office 365 a1 plus-Office 365 a3-Office 365 a5-Office 365 E3-Office 365 E5
   :::column-end:::
:::row-end:::

## <a name="what-happens-when-you-assign-a-license-to-someone"></a>Que se passe-t-il lorsque vous attribuez une licence à quelqu’un ?

Le tableau suivant indique ce qui se produit automatiquement lorsque vous attribuez une licence à quelqu'un :
  
|**Si l'abonnement inclut ce service**|**Cet événement se produit automatiquement**|
|:-----|:-----|
|Exchange Online  <br/> |Une boîte aux lettres est créée pour cette personne. <br/> Pour plus d’informations sur le contrat SLA pour cette tâche, voir [«Configuration... messages dans le centre d’administration Microsoft 365](https://support.microsoft.com/help/2635238/setting-up-messages-in-the-office-365-admin-center). |
|SharePoint Online  <br/> |Les autorisations de modification du site d'équipe SharePoint Online par défaut sont attribuées à cette personne.  <br/> |
|Skype Entreprise Online  <br/> |La personne a accès aux fonctionnalités associées à la licence.  <br/> |
|Applications Microsoft 365 pour les entreprises  <br/> |La personne peut télécharger des applications Office sur un maximum de cinq Mac ou PC, de cinq tablettes et de cinq smartphones.  <br/> |

## <a name="understand-licenses-for-non-user-mailboxes"></a>Comprendre les licences pour les boîtes aux lettres non-utilisateur

Vous n'êtes pas obligé d'attribuer des licences aux boîtes aux lettres de ressources, de salle, et partagées, sauf si elles dépassent leur quota de stockage de 50 gigaoctets (Go). Pour plus d'informations sur les boîtes aux lettres non-utilisateur, voir les articles suivants :
  
- [Créer une boîte aux lettres partagée](../../admin/email/create-a-shared-mailbox.md)
- [Supprimer une licence à partir d’une boîte aux lettres partagée](../../admin/email/remove-license-from-shared-mailbox.md)
- [Boîtes aux lettres partagées dans Exchange Online](https://docs.microsoft.com/exchange/collaboration-exo/shared-mailboxes) pour tous les autres plans Microsoft 365.
- [Créer et gérer des boîtes aux lettres de salle](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-room-mailboxes)
- [Gérer des boîtes aux lettres de ressource](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-equipment-mailboxes).

## <a name="who-can-assign-licenses"></a>Qui peut attribuer des licences ?

Plusieurs types d'administrateurs peuvent utiliser des licences de différentes façons, en fonction de leur rôle. Le tableau ci-dessous recense les options les plus courantes. Pour consulter la liste complète des rôles et des privilèges d'administrateur, voir [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  
|**Rôle d'administrateur**|**Attribuer une licence**|**Annuler l’affectation d’une licence**|**Acheter plus de licences**|**Supprimer un compte**|
|:-----|:-----|:-----|:-----|:-----|
|Administrateur de facturation  <br/> |Non  <br/> |Non  <br/> |Oui  <br/> |Non  <br/> |
|Administrateur global  <br/> |Oui  <br/> |Oui  <br/> |Oui  <br/> |Oui  <br/> |
|Administrateur de licences <br/> |Oui <br/>|Oui <br/> |Non <br/> |Non <br/> |
|Administrateur de support de service  <br/> |Non  <br/> |Non  <br/> |Non  <br/> |Non  <br/> |
|Administrateur d’utilisateurs  <br/> |Oui  <br/> |Oui  <br/> |Non  <br/> |Oui  <br/> |

## <a name="related-content"></a>Contenu connexe

[Acheter ou supprimer des licences pour votre abonnement professionnel](buy-licenses.md) (article) \
[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article) \
[Déattribuer des licences aux utilisateurs](../../admin/manage/remove-licenses-from-users.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](../../admin/email/remove-license-from-shared-mailbox.md) (article)