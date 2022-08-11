---
title: Comprendre les abonnements et les licences dans Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: shegu, nicholak
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- okr_smb
- AdminSurgePortfolio
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: Les applications et services que vous recevez dépendent du produit Microsoft 365 que vous avez acheté, tel que Applications Microsoft 365 pour les PME.
ms.date: 05/12/2022
ms.openlocfilehash: 2d5b35bd4696e25aa1372dea0ac1bdd0371f0ef5
ms.sourcegitcommit: 414682b9bf42dc19a89c893d3c515aee9765b6e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2022
ms.locfileid: "67281309"
---
# <a name="understand-subscriptions-and-licenses-in-microsoft-365-for-business"></a>Comprendre les abonnements et les licences dans Microsoft 365 pour les entreprises

Lorsque vous achetez un abonnement à Microsoft 365 pour les entreprises, vous vous inscrivez à un ensemble d’applications et de services que vous payez régulièrement. Les applications et services que vous recevez dans le cadre de votre abonnement dépendent du produit que vous avez acheté, tel que Applications Microsoft 365 pour les PME ou Microsoft 365 Business Standard. Vous pouvez voir ce qui est fourni avec chaque produit dans la page [Microsoft 365 pour les petites et moyennes entreprises](https://www.microsoft.com/microsoft-365/business/compare-all-microsoft-365-business-products) .

Lorsque vous achetez un abonnement, vous spécifiez le nombre de licences dont vous avez besoin, en fonction du nombre de personnes de votre organisation. Après avoir acheté un abonnement, vous créez des comptes pour les membres de votre organisation, puis vous attribuez une licence à chaque personne. À mesure que les besoins de votre organisation changent, vous pouvez acheter plus de licences pour accueillir de nouvelles personnes ou réaffecter des licences à d’autres utilisateurs lorsqu’une personne quitte votre organisation.

Si vous disposez de plusieurs abonnements, vous pouvez attribuer des licences à différentes personnes pour chaque abonnement. Par exemple, vous pouvez affecter tous vos utilisateurs à toutes les applications et services Microsoft 365 dans le cadre d’un abonnement Microsoft 365 Business Standard. Vous pouvez également affecter un sous-ensemble d’utilisateurs à Visio Online via un abonnement Visio distinct.

## <a name="how-many-devices-can-people-install-office-on"></a>Sur combien d'appareils les utilisateurs peuvent-ils installer Office ?

Si votre abonnement inclut l’un des produits suivants, chaque personne peut installer Office sur jusqu’à cinq PC ou Mac, cinq tablettes et cinq téléphones.

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
  
|Si l'abonnement inclut ce service|Cet événement se produit automatiquement|
|---|---|
|Exchange Online|Une boîte aux lettres est créée pour cette personne. <br/> Pour en savoir plus sur le contrat SLA pour que cette tâche soit terminée, consultez [« Configuration... » messages dans le Centre d'administration Microsoft 365](https://support.microsoft.com/help/2635238/setting-up-messages-in-the-office-365-admin-center).|
|SharePoint Online|Les autorisations de modification du site d'équipe SharePoint Online par défaut sont attribuées à cette personne.|
|Microsoft Teams|La personne a accès aux fonctionnalités associées à la licence.|
|Applications Microsoft 365 pour les grandes entreprises et Applications Microsoft 365 pour les PME|La personne peut télécharger des applications Office sur jusqu’à cinq Mac ou PC, cinq tablettes et cinq smartphones.|

## <a name="understand-licenses-for-non-user-mailboxes"></a>Comprendre les licences pour les boîtes aux lettres non-utilisateur

Vous n'êtes pas obligé d'attribuer des licences aux boîtes aux lettres de ressources, de salle, et partagées, sauf si elles dépassent leur quota de stockage de 50 gigaoctets (Go). Pour plus d'informations sur les boîtes aux lettres non-utilisateur, voir les articles suivants :
  
- [Créer une boîte aux lettres partagée](../../admin/email/create-a-shared-mailbox.md)
- [Supprimer une licence à partir d’une boîte aux lettres partagée](../../admin/email/remove-license-from-shared-mailbox.md)
- [Boîtes aux lettres partagées dans Exchange Online](/exchange/collaboration-exo/shared-mailboxes) pour tous les autres plans Microsoft 365.

## <a name="who-can-assign-licenses"></a>Qui peut attribuer des licences ?

Plusieurs types d'administrateurs peuvent utiliser des licences de différentes façons, en fonction de leur rôle. Le tableau ci-dessous recense les options les plus courantes. Pour consulter la liste complète des rôles et des privilèges d'administrateur, voir [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  
|Rôle d’administrateur|Attribuer une licence|Annuler l’affectation d’une licence|Acheter davantage de licences|Supprimer un compte|
|---|:---:|:---:|:---:|:---:|
|Administrateur de facturation|Non|Non|Oui|Non|
|Administrateur global|Oui|Oui|Oui|Oui|
|Administrateur de licences|Oui|Oui|Non|Non|
|Administrateur de support de service|Non|Non|Non|Non|
|Administrateur d’utilisateurs|Oui|Oui|Non|Oui|

## <a name="related-content"></a>Contenu associé

[Acheter ou supprimer des licences pour votre abonnement professionnel](buy-licenses.md) (article)\
[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)\
[Déattribuer des licences aux utilisateurs](../../admin/manage/remove-licenses-from-users.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](../../admin/email/remove-license-from-shared-mailbox.md) (article)
