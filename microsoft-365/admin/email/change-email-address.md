---
title: Changer votre adresse de courrier pour utiliser votre domaine personnalisé
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
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
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: f4d8cae9-6d06-4c4b-b4e5-6581fd05ea82
description: 'Remplacez votre adresse de messagerie initiale par une adresse de messagerie conviviale telle que tom@fourthcoffee.com. Pour ce faire, vous devez acheter un nom de domaine et l’ajouter à Office 365. '
ms.openlocfilehash: dc0ab64003b48eec50bf34e60d8a6df463b4fe89
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43212032"
---
# <a name="change-your-email-address-to-use-your-custom-domain"></a>Changer votre adresse de courrier pour utiliser votre domaine personnalisé

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
::: moniker range="o365-worldwide"

Votre adresse de courrier initiale dans Office 365 contient .onmicrosoft.com, par exemple tom@fourthcoffee.onmicrosoft.com. Vous pouvez la remplacer par une adresse plus conviviale telle que tom@fourthcoffee.com. Vous devez disposer de votre propre nom de domaine, par exemple fourthcoffee.com. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-germany"

Votre adresse de messagerie initiale dans Office 365 Germany inclut. onmicrosoft.de, comme tom@fourthcoffee.onmicrosoft.de. Vous pouvez le remplacer par une adresse plus conviviale telle que tom@fourthcoffee.de. Vous aurez besoin de votre propre nom de domaine, par exemple fourthcoffee.de. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-21vianet"

Votre adresse de messagerie initiale dans Office 365 géré par 21Vianet inclut partner.onmschina.cn, comme tom@fourthcoffee.partner.onmschina.cn. Vous pouvez le remplacer par une adresse plus conviviale telle que tom@fourthcoffee.cn. Vous aurez besoin de votre propre nom de domaine, par exemple fourthcoffee.cn. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

Lorsque vous modifiez l'adresse de courrier de votre domaine de manière à utiliser Office 365 en mettant à jour l'enregistrement MX de votre domaine lors de la configuration, TOUS les messages envoyés à ce domaine arriveront dans Office 365. Vérifiez que vous avez ajouté les utilisateurs et créé les boîtes aux lettres dans Office 365 pour les personnes qui reçoivent du courrier électronique sur votre domaine AVANT de modifier l'enregistrement MX. Vous ne voulez pas déplacer le courrier électronique de tous les membres de votre domaine vers Office 365 ? Vous pouvez prendre des mesures pour [tester Office 365 avec seulement quelques adresses de courrier](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7.aspx).
  
## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>Modifier votre adresse de courrier pour utiliser votre domaine personnalisé à l’aide du centre d’administration Microsoft 365

Pour effectuer ces étapes, vous devez disposer d’un compte d’administrateur global. 

::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>. 

::: moniker-end
   
::: moniker range="o365-germany"
    
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a>. 
    
::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au centre d’administration à <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn </a>l’adresse. 

::: moniker-end 

2. Accédez à la page**domaines** **d’installation** > . 

3. Dans la page **domaines** , sélectionnez **Ajouter un domaine**.
    
4. Suivez les étapes indiquées pour confirmer que vous êtes le propriétaire de votre domaine et que vous voulez modifier votre adresse de courrier.
    
Vous serez guidé afin de configurer correctement votre domaine dans Office 365.

> [!NOTE]
> Si vous n’utilisez pas de licence Exchange, vous ne pouvez pas utiliser le domaine pour envoyer ou recevoir des courriers électroniques à partir du client Office 365.
  
## <a name="related-articles"></a>Articles connexes

[Acheter un domaine personnalisé à l'aide d'Office 365](../get-help-with-domains/buy-a-domain-name.md)
 
