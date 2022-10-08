---
title: Gérer Microsoft 365 avec Windows PowerShell pour les partenaires DAP
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: landing-page
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Comment les partenaires CSP (Syndication and Cloud Solution Provider) peuvent utiliser Windows PowerShell pour gérer les locataires clients Microsoft 365.
ms.openlocfilehash: b48b6872693ebdc960606c40f847bb92d417407e
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68185422"
---
# <a name="how-to-manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-partners"></a>Comment gérer Microsoft 365 avec Windows PowerShell pour les partenaires d’autorisations d’accès délégué

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Beaucoup sont des fournisseurs de réseaux ou de télécommunications. Ils regroupent les abonnements Microsoft 365 dans leurs offres de service. Lorsqu’ils vendent un abonnement Microsoft 365, ils se voient automatiquement accorder des autorisations d’administration au nom de (AOBO) aux locataires du client afin qu’ils puissent administrer et signaler ces locations. Ces tâches sont difficiles à effectuer dans le Centre d'administration Microsoft 365. Il est beaucoup plus facile d’utiliser PowerShell pour Microsoft 365 pour effectuer des tâches administratives telles que :
- Répertorier tous les **TenantIds client** et leurs domaines 
- Identifier tous les utilisateurs d’une location client et leurs licences attribuées
> [!NOTE]
> Certaines tâches d’administration ne peuvent être effectuées que dans PowerShell.

Les articles suivants montrent comment la syndication et les partenaires CSP utilisent PowerShell pour administrer leurs locations client :
  
- [Gérer les locataires Microsoft 365 avec Windows PowerShell pour les partenaires DAP (Delegated Access Permissions)](manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [Ajout d'un domaine à la location d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
- [Récupération des données des rapports du locataire d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
