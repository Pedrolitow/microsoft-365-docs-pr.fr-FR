---
title: Changer votre adresse de courrier pour utiliser votre domaine personnalisé
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: f4d8cae9-6d06-4c4b-b4e5-6581fd05ea82
description: Changez votre adresse e-mail à une adresse e-mail conviviale tom@fourthcoffee.com en achetant un nom de domaine et en l’ajoutant Microsoft 365.
ms.openlocfilehash: d5e70856c9200cd7e5df0eded25b6ff460e5d1fe
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572092"
---
# <a name="change-your-email-address-to-use-your-custom-domain"></a>Changer votre adresse de courrier pour utiliser votre domaine personnalisé

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
::: moniker range="o365-worldwide"

Votre adresse e-mail initiale dans Microsoft 365 comprend .onmicrosoft.com, comme tom@fourthcoffee.onmicrosoft.com. Vous pouvez la remplacer par une adresse plus conviviale telle que tom@fourthcoffee.com. Vous devez disposer de votre propre nom de domaine, par exemple fourthcoffee.com. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-germany"

Votre adresse e-mail initiale en Office 365 Allemagne comprend .onmicrosoft.de, comme tom@fourthcoffee.onmicrosoft.de. Vous pouvez le changer en une adresse plus conviviale comme tom@fourthcoffee.de. Vous aurez besoin de votre propre nom de domaine, comme fourthcoffee.de premier. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-21vianet"

Votre adresse e-mail initiale Office 365 exploitée par 21Vianet comprend partner.onmschina.cn, comme tom@fourthcoffee.partner.onmschina.cn. Vous pouvez le changer en une adresse plus conviviale comme tom@fourthcoffee.cn. Vous aurez besoin de votre propre nom de domaine, comme fourthcoffee.cn premier. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

Lorsque vous modifiez l’e-mail de votre domaine pour venir à Microsoft 365, en mettant à jour l’enregistrement MX de votre domaine pendant la configuration, tous les e-mails envoyés à ce domaine commenceront à arriver à Microsoft 365. Assurez-vous d’ajouter des utilisateurs et de créer des boîtes aux lettres en Microsoft 365 pour tous ceux qui ont des e-mails sur votre domaine avant de modifier l’enregistrement MX. Vous ne voulez pas déplacer l’e-mail pour tout le monde sur votre domaine Microsoft 365? Vous pouvez prendre des mesures pour [piloter Microsoft 365 avec seulement quelques adresses e-mail à la place](../misc/pilot-microsoft-365-from-my-custom-domain.md).
  
## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>Modifiez votre adresse e-mail pour utiliser votre domaine personnalisé en utilisant le Microsoft 365 d’administration

Vous devez avoir un compte administrateur global pour effectuer ces étapes. 

::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>. 

::: moniker-end
   
::: moniker range="o365-germany"
    
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a>. 
    
::: moniker-end

::: moniker range="o365-21vianet"

1. Aller au centre <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn </a>admin à . 

::: moniker-end 

2. Allez à la page  >  **Domaines d’installation.** 

3. Dans la page **Domaines**, sélectionnez **Ajouter un domaine**.
    
4. Suivez les étapes indiquées pour confirmer que vous êtes le propriétaire de votre domaine et que vous voulez modifier votre adresse de courrier.
    
Vous serez guidé pour que tout soit correctement mis en place avec votre domaine dans Microsoft 365.

> [!NOTE]
> Si vous n’utilisez pas de licence Exchange, vous ne pouvez pas utiliser le domaine pour envoyer ou recevoir des e-mails du Microsoft 365 locataire.
  
## <a name="related-content"></a>Contenu connexe

[Acheter un domaine personnalisé en utilisant Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (article)
