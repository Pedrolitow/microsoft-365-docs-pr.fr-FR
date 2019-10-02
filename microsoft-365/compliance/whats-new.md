---
title: Nouveautés du centre de conformité Microsoft 365
ms.author: brendonb
author: brendonb
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Nous ajoutons constamment de nouvelles fonctionnalités au centre de conformité Microsoft 365, à la résolution des problèmes que nous apprendons et en apportant des modifications en fonction de vos commentaires. Découvrez ce que nous avons fait dans ce mois-ci.
ms.openlocfilehash: b80edfb0425904b03426ef0ff3cdd1d251e638ea
ms.sourcegitcommit: c6eab4a9f1b70e7ff0db6b2a1128a4db2591cbaf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "37369635"
---
# <a name="whats-new-in-the-microsoft-365-compliance-center"></a>Nouveautés du centre de conformité Microsoft 365

Nous ajoutons constamment de nouvelles fonctionnalités au [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md), à la résolution des problèmes que nous apprendons et en apportant des modifications en fonction de vos commentaires. Jetez un œil à ce qui est disponible dès aujourd’hui. Certaines fonctionnalités sont déployées à des vitesses différentes à nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à la [version ciblée](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Que se passe-t-il dans d’autres centres d’administration ? Consultez les articles suivants :<br>[Nouveautés du centre d’administration Microsoft 365](https://docs.microsoft.com/office365/admin/whats-new-in-preview?view=o365-worldwide)<br>[Nouveautés du centre d’administration SharePoint](https://docs.microsoft.com/sharepoint/what-s-new-in-admin-center)

## <a name="september-2019"></a>Septembre 2019

Vous vous demandez pourquoi il est calme sur la sortie ce mois-ci ? Nous sommes en tête de création de nouvelles solutions de conformité innovantes qui seront dévoilées chez [Microsoft enflamme](https://www.microsoft.com/ignite) en novembre. Restez informé !

### <a name="new-encryption-options-for-sensitivity-labels"></a>Nouvelles options de chiffrement pour les étiquettes de sensibilité 

Lors de la configuration du chiffrement pour une étiquette de sensibilité, vous disposez de deux options qui permettent aux utilisateurs d’attribuer des autorisations lorsqu’ils appliquent manuellement l’étiquette à la messagerie et aux documents :<br>
- Lors de l’application de l’étiquette à la **messagerie Outlook**, les utilisateurs peuvent appliquer des restrictions équivalentes à celles de l’option ne pas transférer. Les destinataires seront en mesure de lire le message mais pas de transférer, imprimer ou copier le contenu.
- Lors de l’application de l’étiquette à des **fichiers Word, PowerPoint et Excel**, les utilisateurs sont invités à attribuer des autorisations d’accès à des utilisateurs et des groupes spécifiques.

[En savoir plus](encryption-sensitivity-labels.md#let-users-assign-permissions)

## <a name="august-2019"></a>Août 2019

### <a name="update-to-data-investigations"></a>Mise à jour des enquêtes de données

Lors de l’exécution d’une enquête sur les données, vous pouvez maintenant supprimer des éléments de leur emplacement d’origine. Cela signifie que vous pouvez supprimer des éléments de boîtes aux lettres Exchange, de sites SharePoint et de comptes OneDrive au sein de votre organisation. Étant donné que vous avez collecté les éléments en tant que preuve, vous pouvez effectuer des copies de ces éléments dans l’ensemble de preuves pour vous faire une étude plus approfondie ou conserver une référence. [En savoir plus](manage-data-spillage-incidents.md#step-4-delete-the-spilled-data) 

## <a name="july-2019"></a>Juillet 2019

### <a name="new-admin-roles"></a>Nouveaux rôles d’administrateur

Nous avons publié deux nouveaux rôles d’administrateur pour vous aider à gérer la sécurité et la conformité dans votre organisation. informez tous vos amis.

- **Administrateur des données de conformité**. Les utilisateurs disposant de ce rôle disposent d’autorisations pour protéger et suivre les données dans le centre de conformité Microsoft 365, le centre d’administration Microsoft 365 et Azure. Ils peuvent également gérer tout le centre d’administration Exchange, le gestionnaire de conformité, les équipes & Centre d’administration de Skype entreprise et créer des tickets de support pour Azure et Microsoft 365.
- **Opérateur de sécurité**. Les utilisateurs disposant de ce rôle peuvent gérer les alertes et disposer d’un accès global en lecture seule aux fonctionnalités liées à la sécurité, y compris tous les éléments du centre de sécurité Microsoft 365, Azure Active Directory, protection des identités, gestion des identités et Office 365 Centre de sécurité & conformité.

[En savoir plus sur ces rôles](https://docs.microsoft.com/microsoft-365/security//office-365-security/permissions-microsoft-365-compliance-security)

### <a name="search-and-filtering-for-reports"></a>Recherche et filtrage des rapports

Il n’y a plus de défilement dans un océan de rapports pour trouver ceux que vous souhaitez. Vous pouvez désormais Rechercher des rapports (en fonction de leur titre) et filtrer sur des catégories telles que « labels » et « Compliance » et des sources comme « Office 365 » et « Microsoft Cloud App Security ».

![Capture d’écran des boutons de recherche et de filtre des rapports avec un filtre appliqué](media/mcc_report_filtering.png)
