---
title: Gérer Microsoft 365 avec Windows PowerShell pour les partenaires DAP
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Comment les partenaires fournisseurs de solutions Cloud et de syndication peuvent utiliser Windows PowerShell pour gérer les clients Microsoft 365.
ms.openlocfilehash: a7b2fbb5423e3b923e17aa2d9c488e7dd085be35
ms.sourcegitcommit: aeb94601a81db3ead8610c2f36cff30eb9fe10e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "47429877"
---
# <a name="how-to-manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-partners"></a>Comment gérer Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. De nombreux fournisseurs sont des fournisseurs de réseau ou de télécommunication. Ils regroupent les abonnements Microsoft 365 dans leurs offres de services. Lorsqu’ils vendent un abonnement Microsoft 365, ils se voient automatiquement accorder des autorisations Administrer de la part de (AOBO) sur les locations du client afin qu’ils peuvent administrer et signaler ces locations. Ces tâches sont difficiles à effectuer dans le Centre d’administration Microsoft 365. Il est beaucoup plus facile d’utiliser PowerShell pour Microsoft 365 pour effectuer des tâches administratives telles que :
- List all the customer **TenantIds** and their domains 
- Identifier tous les utilisateurs d’une location client et leurs licences attribuées
> [!NOTE]
> Certaines tâches administratives peuvent uniquement être réalisées dans PowerShell.

Les articles suivants montrent comment les partenaires de syndication et de CSP utilisent PowerShell pour administrer les locations de leurs clients :
  
- [Gérer les clients Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué](manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [Ajout d'un domaine à la location d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [Connexion à Exchange Online PowerShell](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [Récupération des données des rapports du locataire d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
   