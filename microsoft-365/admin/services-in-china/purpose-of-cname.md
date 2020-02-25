---
title: À quoi sert l'enregistrement CNAME Office 365 pour MSOID ?
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: get-started-article
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NOINDEX
description: Pour plus d’informations sur l’enregistrement CNAMe « MSOID » dans Office 365 qui vous dirige vers le meilleur serveur pour les processus d’authentification, vous allez obtenir une réponse plus rapide.
monikerRange: o365-21vianet
ms.openlocfilehash: fdf728dcaebf65485b1eaed9b41e49f5327e9a41
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42254127"
---
# <a name="whats-the-purpose-of-the-office-365-cname-record-for-msoid"></a>À quoi sert l'enregistrement CNAME Office 365 pour MSOID ?

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
> [!NOTE]
> Le code suivant s’applique uniquement à * * Office 365 géré par 21Vianet.
  
Vous vous demandez peut-être pourquoi vous devez ajouter l'enregistrement CNAME « MSOID » dans Office 365. Cet enregistrement doit être ajouté pour tous les domaines personnalisés, quel que soit l'abonnement que vous utilisez. Pourquoi en avez-vous besoin ? Il s'agit d'un aspect un peu technique. Grosso modo, cet enregistrement vous permet d'être redirigé vers le meilleur serveur pour certains processus d'authentification, afin de recevoir une réponse plus rapide.
  
Informations techniques : lorsque vous exécutez une application cliente compatible avec Office 365, telle que Skype Entreprise Online, Outlook, Windows PowerShell ou l'outil de synchronisation Microsoft Azure Azure Active Directory, vos informations d'identification doivent être authentifiées. Office 365 utilise un enregistrement CNAME pour pointer vers le point de terminaison d'authentification correct pour votre emplacement, ce qui garantit des temps de réponse d'authentification rapides.
  
Si cet enregistrement CNAME est manquant pour votre domaine, ces applications utiliseront un point de terminaison d'authentification par défaut aux États-Unis, ce qui peut ralentir le processus d'authentification. Si cet enregistrement CNAME n'est pas correctement configuré (par exemple, si la valeur **Adresse de pointage** inclut une coquille), ces applications ne pourront pas s'authentifier.
  
 **Si Office 365 gère les enregistrements DNS de votre domaine,** Office 365 configure cet enregistrement CNAMe pour vous. 
  
 **Si vous gérez des enregistrements DNS pour votre domaine au niveau de votre hôte DNS,** vous pouvez créer cet enregistrement vous-même en [suivant les instructions de votre hôte DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23.aspx).
  
Si vous planifiez un déploiement d’Office 365 et que vous souhaitez en savoir plus sur tous les enregistrements DNS que vous aurez peut-être besoin d’ajouter ou de mettre à jour, lisez les informations à ce sujet dans la [référence : enregistrements DNS externes pour Office 365](https://go.microsoft.com/fwlink/?LinkId=579013).
  

