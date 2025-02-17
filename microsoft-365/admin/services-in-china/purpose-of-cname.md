---
title: À quoi sert l'enregistrement CNAME Office 365 pour MSOID ?
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Tier2
- scotvorg
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
ms.service: microsoft-365-business
ms.localizationpriority: medium
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NOINDEX
description: En savoir plus sur l’enregistrement CNAME « MSOID » dans Office 365 qui vous dirige vers le meilleur serveur pour les processus d’authentification, vous obtiendrez donc une réponse plus rapide.
monikerRange: o365-21vianet
ms.openlocfilehash: b8f199074a23cdbd994e032e1c1f47100cc46fd2
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68727892"
---
# <a name="whats-the-purpose-of-the-office-365-cname-record-for-msoid"></a>À quoi sert l'enregistrement CNAME Office 365 pour MSOID ?

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
> [!NOTE]
> Le code suivant s’applique uniquement aux **Office 365 gérés par 21Vianet.
  
You may wonder why you need to add the "MSOID" CNAME record in Office 365. This is a record that has to be added for all custom domains, no matter which subscription you use. Why do you need it? It's a little technical, but essentially, it's so that you'll be directed to the best server for certain authentication processes, so you'll get faster response.
  
Technical details: When you run a client application that works with Office 365 such as Skype for Business Online, Outlook, Windows PowerShell or Microsoft Azure Active Directory Sync tool, your credentials must be authenticated. Office 365 uses a CNAME record to point to the correct authentication endpoint for your location, which ensures rapid authentication response times.
  
If this CNAME record is missing for your domain, these applications will use a default authentication endpoint in the United States, which means authentication might be slower. If this CNAME record isn't configured properly—for example, if you have a typo in the **Points to address**—these applications won't be able to authenticate.
  
 **Si Office 365 gère les enregistrements DNS de votre domaine,** Office 365 configure cet enregistrement CNAME pour vous. 
  
 **Si vous gérez des enregistrements DNS pour votre domaine sur votre hôte DNS,** vous créez cet enregistrement vous-même en [suivant les instructions de votre hôte DNS](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
  
Si vous planifiez un déploiement Office 365 et que vous souhaitez en savoir plus sur tous les enregistrements DNS que vous devrez peut-être ajouter ou mettre à jour, consultez [Référence : Enregistrements système de noms de domaine externes pour Office 365](../../enterprise/external-domain-name-system-records.md).
