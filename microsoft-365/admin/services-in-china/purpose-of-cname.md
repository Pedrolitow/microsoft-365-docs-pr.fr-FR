---
title: À quoi sert l'enregistrement CNAME Office 365 pour MSOID ?
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NOINDEX
description: En savoir plus sur l’enregistrement CNAME « MSOID » dans Office 365 qui vous dirige vers le meilleur serveur pour les processus d’authentification, afin que vous receviez une réponse plus rapide.
monikerRange: o365-21vianet
ms.openlocfilehash: a1d587abc9db03c9a1f7c5f66711fde3648a0e96
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59176275"
---
# <a name="whats-the-purpose-of-the-office-365-cname-record-for-msoid"></a>À quoi sert l'enregistrement CNAME Office 365 pour MSOID ?

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
> [!NOTE]
> L’exemple suivant s’applique uniquement à **Office 365 géré par 21Vianet.
  
Vous vous demandez peut-être pourquoi vous devez ajouter l'enregistrement CNAME « MSOID » dans Office 365. Cet enregistrement doit être ajouté pour tous les domaines personnalisés, quel que soit l'abonnement que vous utilisez. Pourquoi en avez-vous besoin ? Il s'agit d'un aspect un peu technique. Grosso modo, cet enregistrement vous permet d'être redirigé vers le meilleur serveur pour certains processus d'authentification, afin de recevoir une réponse plus rapide.
  
Informations techniques : lorsque vous exécutez une application cliente compatible avec Office 365, telle que Skype Entreprise Online, Outlook, Windows PowerShell ou l'outil de synchronisation Microsoft Azure Azure Active Directory, vos informations d'identification doivent être authentifiées. Office 365 utilise un enregistrement CNAME pour pointer vers le point de terminaison d'authentification correct pour votre emplacement, ce qui garantit des temps de réponse d'authentification rapides.
  
Si cet enregistrement CNAME est manquant pour votre domaine, ces applications utiliseront un point de terminaison d'authentification par défaut aux États-Unis, ce qui peut ralentir le processus d'authentification. Si cet enregistrement CNAME n'est pas correctement configuré (par exemple, si la valeur **Adresse de pointage** inclut une coquille), ces applications ne pourront pas s'authentifier.
  
 Si Office 365 les enregistrements **DNS** de votre domaine, Office 365 cet enregistrement CNAME pour vous. 
  
 Si vous gérez des enregistrements DNS pour votre domaine sur votre hôte **DNS,** vous créez cet enregistrement vous-même en suivant les instructions pour votre hôte [DNS.](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)
  
Si vous planifiez un déploiement Office 365 et que vous souhaitez en savoir plus sur tous les enregistrements DNS que vous devrez peut-être ajouter ou mettre à jour, lisez-les dans Référence : Enregistrements du système de noms de domaine externe pour [Office 365](../../enterprise/external-domain-name-system-records.md).
