---
title: Afficher vos rôles Azure Active Directory dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: magarlan, chrigreen
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les techniciens du fournisseur de services managés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment afficher vos rôles Azure Active Directory (Azure AD) sur les différents locataires clients gérés par votre organisation.
ms.openlocfilehash: a2cb9349f0511d2c9891e7b8611ef13f0aad6ee1
ms.sourcegitcommit: 23a53b5c5e372a2a7ad5e175850224d3d464f6dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2022
ms.locfileid: "67055809"
---
# <a name="view-your-azure-active-directory-roles-in-microsoft-365-lighthouse"></a>Afficher vos rôles Azure Active Directory dans Microsoft 365 Lighthouse

Cet article fournit des instructions sur la façon d’afficher vos rôles Azure Active Directory (Azure AD) sur les différents locataires clients gérés par votre organisation. Votre rôle détermine les actions que vous pouvez effectuer dans Lighthouse.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez avoir accès à un locataire partenaire qui a été intégré au service Microsoft 365 Lighthouse.

## <a name="view-your-roles"></a>Afficher vos rôles

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Locataires**.

2. Dans la liste des locataires, sélectionnez n’importe quel nom de locataire pour ouvrir la page **Vue d’ensemble** du locataire.

3. En regard de **Rôles**, sélectionnez le lien indiquant le nombre de rôles que vous détenez dans le locataire. La page **Rôles** s’ouvre.

    Si vous conservez un ou plusieurs rôles dans un locataire client, une coche verte s’affiche dans la colonne **Activé** pour ce locataire, ainsi que le nombre de rôles que vous détenez. Si vous n’avez aucun rôle dans un locataire, un **X** rouge s’affiche.
 
4. Pour les locataires clients avec une coche verte à côté d’eux, développez le locataire pour afficher la liste des rôles que vous détenez dans ce locataire. Pour plus d’informations sur les rôles Azure AD et les autorisations qu’ils accordent, consultez [les rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference).

    La page **Rôles** affiche également toutes les balises personnalisées qui ont été appliquées à vos locataires. Vous pouvez filtrer les données sur la page en fonction des rôles ou balises attribués.

## <a name="next-steps"></a>Prochaines étapes

Si vous n’êtes pas autorisé à effectuer une action que vous devez effectuer dans Lighthouse, contactez un administrateur de votre locataire partenaire qui peut vous attribuer le rôle approprié pour l’action que vous essayez d’effectuer.

## <a name="related-content"></a>Contenu associé

[Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md) (article)\
[Gérer votre liste de locataires dans Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md) (article)
