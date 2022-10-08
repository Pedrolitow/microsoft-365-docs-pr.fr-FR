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
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
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
ms.openlocfilehash: c097905050bdbe285e83b31008b9ff7f53f32e1f
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68180756"
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

You don't need to assign licenses to resource mailboxes, room mailboxes, and shared mailboxes, except when they are over their storage quota of 50 gigabytes (GB). For more about non-user mailboxes, see the following articles:
  
- [Créer une boîte aux lettres partagée](../../admin/email/create-a-shared-mailbox.md)
- [Supprimer une licence à partir d’une boîte aux lettres partagée](../../admin/email/remove-license-from-shared-mailbox.md)
- [Boîtes aux lettres partagées dans Exchange Online](/exchange/collaboration-exo/shared-mailboxes) pour tous les autres plans Microsoft 365.

## <a name="who-can-assign-licenses"></a>Qui peut attribuer des licences ?

Different types of admins can work with licenses in different ways, depending on their roles. The following table lists the most common options. For a complete list of admin roles and privileges, see [About admin roles](../../admin/add-users/about-admin-roles.md).
  
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
