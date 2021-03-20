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
description: 'Modifiez votre adresse e-mail initiale en une adresse de messagerie conviviale comme tom@fourthcoffee.com. Pour ce faire, vous devez acheter un nom de domaine et l’ajouter à Microsoft 365. '
ms.openlocfilehash: 10dff4e0523062ae763c08a972563dc8b5582038
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50915925"
---
# <a name="change-your-email-address-to-use-your-custom-domain"></a>Changer votre adresse de courrier pour utiliser votre domaine personnalisé

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](../microsoft-365-admin-center-preview.md?preserve-view=true&view=o365-21vianet).

::: moniker-end

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
::: moniker range="o365-worldwide"

Votre adresse de messagerie initiale dans Microsoft 365 inclut .onmicrosoft.com, comme tom@fourthcoffee.onmicrosoft.com. Vous pouvez la remplacer par une adresse plus conviviale telle que tom@fourthcoffee.com. Vous devez disposer de votre propre nom de domaine, par exemple fourthcoffee.com. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-germany"

Votre adresse de messagerie initiale dans Office 365 Germany inclut .onmicrosoft.de, comme tom@fourthcoffee.onmicrosoft.de. Vous pouvez la modifier en une adresse plus conviviale comme tom@fourthcoffee.de. Vous aurez besoin de votre propre nom de domaine, comme fourthcoffee.de d’abord. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-21vianet"

Votre adresse de messagerie initiale dans Office 365 géré par 21Vianet inclut des partner.onmschina.cn, comme tom@fourthcoffee.partner.onmschina.cn. Vous pouvez la modifier en une adresse plus conviviale comme tom@fourthcoffee.cn. Vous aurez besoin de votre propre nom de domaine, comme fourthcoffee.cn d’abord. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

Lorsque vous modifiez le courrier électronique de votre domaine pour qu’il soit envoyé à Microsoft 365, en mettant à jour l’enregistrement MX de votre domaine lors de l’installation, tous les messages envoyés à ce domaine commenceront à être envoyés à Microsoft 365. Assurez-vous que vous avez ajouté des utilisateurs et créé des boîtes aux lettres dans Microsoft 365 pour toutes les personnes qui ont des messages sur votre domaine avant de modifier l’enregistrement MX. Vous ne souhaitez pas déplacer le courrier électronique de tous les employés de votre domaine vers Microsoft 365 ? Vous pouvez prendre des mesures pour [piloter Microsoft 365](../misc/pilot-microsoft-365-from-my-custom-domain.md?view=o365-worldwide)avec seulement quelques adresses de messagerie à la place.
  
## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>Modifier votre adresse de messagerie pour utiliser votre domaine personnalisé à l’aide du Centre d’administration Microsoft 365

Vous devez avoir un compte d’administrateur global pour effectuer ces étapes. 

::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>. 

::: moniker-end
   
::: moniker range="o365-germany"
    
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a>. 
    
::: moniker-end

::: moniker range="o365-21vianet"

1. Go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn </a>admin center at . 

::: moniker-end 

2. Go to the **Setup**  >  **Domains** page. 

3. Dans la page **Domaines**, sélectionnez **Ajouter un domaine**.
    
4. Suivez les étapes indiquées pour confirmer que vous êtes le propriétaire de votre domaine et que vous voulez modifier votre adresse de courrier.
    
Vous serez guidé pour tout configurer correctement avec votre domaine dans Microsoft 365.

> [!NOTE]
> Si vous n’utilisez pas de licence Exchange, vous ne pouvez pas utiliser le domaine pour envoyer ou recevoir des courriers électroniques à partir du client Microsoft 365.
  
## <a name="related-articles"></a>Articles connexes

[Acheter un domaine personnalisé à l’aide de Microsoft 365](../get-help-with-domains/buy-a-domain-name.md)
