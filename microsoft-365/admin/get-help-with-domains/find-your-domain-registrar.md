---
title: Rechercher votre bureau d’enregistrement de domaine
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: b5b633ba-1e56-4a98-8ff5-2acaac63a5c8
description: Découvrez comment rechercher votre bureau d’enregistrement de domaines et votre fournisseur d’hébergement DNS à l’aide de la recherche InterNIC.
ms.openlocfilehash: 0574e911e9175fc99b419ac96a0ed73d1e2ef8a3
ms.sourcegitcommit: aebcdbef52e42f37492a7f780b8b9b2bc0998d5c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59774579"
---
# <a name="find-your-domain-registrar"></a>Rechercher votre bureau d’enregistrement de domaine

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

## <a name="domain-registrar"></a>Bureau d'enregistrement de domaines

### <a name="find-your-domain-name-registrar"></a>Rechercher votre bureau d’enregistrement de noms de domaine

> [!NOTE]
> Seuls les domaines se terminant par *. COM*, *.NET* et *.EDU* sont compatibles avec cet outil.

1. Sur la [page de recherche InterNIC](https://go.microsoft.com/fwlink/p/?LinkId=402770), dans la zone **Whois Search**, tapez votre domaine (par exemple,  *contoso.com).*

2. Sélectionnez l'option **Domaine**, puis cliquez sur **Envoyer**.

3. Sur la page **Whois Search Results**, recherchez l’entrée **Registrar**. Cette entrée indique l’organisation qui fournit le service de bureau d’enregistrement pour votre domaine.

## <a name="dns-hosting-provider"></a>Fournisseur d’hébergement DNS

### <a name="find-your-dns-hosting-provider"></a>Rechercher votre fournisseur d’hébergement DNS

> [!NOTE]
> Seuls les domaines se terminant par *. COM*, *.NET* et *.EDU* sont compatibles avec cet outil.

1. Sur la [page de recherche InterNIC](https://go.microsoft.com/fwlink/p/?LinkId=402770), dans la zone **Whois Search**, tapez votre domaine (par exemple, contoso.com).

2. Sélectionnez l'option **Domaine**, puis cliquez sur **Envoyer**.

3. Sur la page **Whois Search Results**, localisez la première entrée **Name Server**.

4. Copiez les informations sur le serveur de noms (NS) affichées après les deux-points (:), puis collez-les dans la zone **Search** en haut de la page. Sélectionnez **Nameserver**, puis sélectionnez **Envoyer**.

5. Sur la page **Whois Search Results**, recherchez l’entrée **Registrar**. Cette entrée indique votre fournisseur d’hébergement DNS, le fournisseur DNS qui est propriétaire du serveur de noms pour votre domaine.

---

