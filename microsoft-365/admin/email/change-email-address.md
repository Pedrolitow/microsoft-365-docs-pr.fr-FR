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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: f4d8cae9-6d06-4c4b-b4e5-6581fd05ea82
description: Modifiez votre adresse e-mail en une adresse de messagerie conviviale comme tom@fourthcoffee.com en achetant un nom de domaine et en l’ajoutant à Microsoft 365.
ms.openlocfilehash: f388bfcea3131df6a66733c940ed2f566827d2e5
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61370571"
---
# <a name="change-your-email-address-to-use-your-custom-domain"></a>Changer votre adresse de courrier pour utiliser votre domaine personnalisé

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
::: moniker range="o365-worldwide"

Votre adresse de messagerie initiale dans Microsoft 365 inclut .onmicrosoft.com, comme tom@fourthcoffee.onmicrosoft.com. Vous pouvez la remplacer par une adresse plus conviviale telle que tom@fourthcoffee.com. Vous devez disposer de votre propre nom de domaine, par exemple fourthcoffee.com. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-21vianet"

Votre adresse de messagerie initiale dans Office 365 géré par 21Vianet inclut des partner.onmschina.cn, comme tom@fourthcoffee.partner.onmschina.cn. Vous pouvez la modifier en une adresse plus conviviale comme tom@fourthcoffee.cn. Vous aurez besoin de votre propre nom de domaine, comme fourthcoffee.cn d’abord. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

Lorsque vous modifiez le courrier électronique de votre domaine pour qu’il arrive à Microsoft 365, en mettant à jour l’enregistrement MX de votre domaine lors de l’installation, tous les messages envoyés à ce domaine commenceront à Microsoft 365. Assurez-vous que vous avez ajouté des utilisateurs et créé des boîtes aux lettres dans Microsoft 365 pour toutes les personnes qui ont des messages sur votre domaine AVANT de modifier l’enregistrement MX. Vous ne souhaitez pas déplacer le courrier électronique de tous les personnes de votre domaine vers Microsoft 365 ? Vous pouvez prendre des mesures pour [piloter Microsoft 365 avec seulement quelques adresses e-mail à la place.](../misc/pilot-microsoft-365-from-my-custom-domain.md)
  
## <a name="set-up-business-email-with-a-new-domain"></a>Configurer la messagerie professionnelle avec un nouveau domaine

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA?autoplay=false]

Achetez un nouveau nom de domaine pour votre adresse e-mail et définissez les adresses de messagerie avec Microsoft 365.

1. Achetez un nouveau nom de domaine pour votre adresse e-mail en fournissant vos informations de contact pour le nouveau nom de domaine, en choisissant votre mode de paiement, puis en plaçant votre commande.
1. Modifiez la première partie de l’adresse (avant le signe @) ou laissez-la telle qu’elle est. 
1. Sign out of Microsoft 365, and then sign back in with your new email address. Les adresses e-mail de vos employés sont mises à jour avec le nouveau domaine. 

## <a name="set-up-business-email-with-an-existing-domain"></a>Configurer la messagerie professionnelle avec un domaine existant

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu?autoplay=false]

Utilisez un nom de domaine que vous possédez déjà, que vous l’utilisiez pour une adresse de site web ou une adresse de messagerie d’un autre fournisseur.

1. Connectez-vous au site web qui héberge votre domaine. Cliquez sur un bouton pour vérifier automatiquement ou mettre à jour le domaine manuellement. 
1. Personnalisez l’adresse e-mail ou laissez-la telle qu’elle est.
1. Sign out of Microsoft 365, and then sign back in with your new email address. Les adresses e-mail de vos employés sont mises à jour avec le nouveau domaine.

## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>Modifiez votre adresse de messagerie pour utiliser votre domaine personnalisé à l’aide du Centre d'administration Microsoft 365

Vous devez être un Administrateur général pour procéder à ces étapes.

::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn </a>admin center at .

::: moniker-end

2. Go to the **Setup**  >  **Domains** page.

3. Dans la page **Domaines**, sélectionnez **Ajouter un domaine**.

4. Suivez les étapes pour confirmer que vous êtes propriétaire de votre domaine. Vous serez guidé pour que tout soit correctement installé avec votre domaine dans Microsoft 365.

5. Go to **Users**  >  **Active users**.

6. Sélectionnez un utilisateur pour modifier son nom d’utilisateur et changez-le en domaine que vous avez ajouté.

> [!NOTE]
> Si vous n’utilisez pas de licence Exchange, vous ne pouvez pas utiliser le domaine pour envoyer ou recevoir des courriers électroniques du client Microsoft 365 client.
  
## <a name="related-content"></a>Contenu associé

[Acheter un domaine personnalisé à l’Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (article)\
[Gérer les domaines](/admin) (page de liens)\
[FAQ sur les domaines](../setup/domains-faq.yml) (article)