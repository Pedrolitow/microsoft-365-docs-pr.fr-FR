---
title: Rechercher votre bureau d’enregistrement de domaine
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- Tier2
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom:
- VSBFY23
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: b5b633ba-1e56-4a98-8ff5-2acaac63a5c8
description: Découvrez comment rechercher votre bureau d’enregistrement de domaines et votre fournisseur d’hébergement DNS à l’aide de la recherche InterNIC.
ms.openlocfilehash: 2cc67c4f351e86952f198e7b65dc70918f6525b3
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729784"
---
# <a name="find-your-domain-registrar"></a>Rechercher votre bureau d’enregistrement de domaine

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

## <a name="domain-registrar"></a>Bureau d'enregistrement de domaines

### <a name="find-your-domain-name-registrar"></a>Rechercher votre bureau d’enregistrement de noms de domaine

> [!NOTE]
> Seuls les domaines se terminant par *. COM*, *.NET* et *.EDU* sont compatibles avec cet outil.

1. On the [InterNIC search page](https://go.microsoft.com/fwlink/p/?LinkId=402770), in the **Whois Search** box, type your domain. For example,  *contoso.com.*

2. Sélectionnez l'option **Domaine**, puis cliquez sur **Envoyer**.

3. On the **Whois Search Results** page, locate the **Registrar** entry. This entry lists the organization that provides registrar service for your domain.

## <a name="dns-hosting-provider"></a>Fournisseur d’hébergement DNS

### <a name="find-your-dns-hosting-provider"></a>Rechercher votre fournisseur d’hébergement DNS

> [!NOTE]
> Seuls les domaines se terminant par *. COM*, *.NET* et *.EDU* sont compatibles avec cet outil.

1. On the [InterNIC search page](https://go.microsoft.com/fwlink/p/?LinkId=402770), in the **Whois Search** box, type your domain. For example, contoso.com.

2. Sélectionnez l'option **Domaine**, puis cliquez sur **Envoyer**.

3. Sur la page **Whois Search Results**, localisez la première entrée **Name Server**.

4. Copy the name server (NS) information that appears after the colon (:), and then paste it into the **Search** box at the top of the page. Select **Nameserver**, and then select **Submit**.

5. On the **Whois Search Results** page, locate the **Registrar** entry. This entry lists your DNS hosting provider, the DNS provider who owns the name server for your domain.

---

