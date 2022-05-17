---
title: Changer votre adresse de courrier pour utiliser votre domaine personnalisé
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
description: Remplacez votre adresse e-mail par une adresse e-mail conviviale comme tom@fourthcoffee.com en achetant un nom de domaine et en l’ajoutant à Microsoft 365.
ms.openlocfilehash: a71e92b48e7091ae243b62ec594cd2be5ce52406
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437280"
---
# <a name="change-your-microsoft-365-email-address-to-use-your-custom-domain"></a>Modifier votre adresse e-mail Microsoft 365 pour utiliser votre domaine personnalisé

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
::: moniker range="o365-worldwide"

Votre adresse e-mail initiale dans Microsoft 365 inclut .onmicrosoft.com, comme tom@fourthcoffee.onmicrosoft.com. Vous pouvez la remplacer par une adresse plus conviviale telle que tom@fourthcoffee.com. Vous devez disposer de votre propre nom de domaine, par exemple fourthcoffee.com. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-21vianet"

Votre adresse e-mail initiale dans Office 365 gérée par 21Vianet inclut partner.onmschina.cn, comme tom@fourthcoffee.partner.onmschina.cn. Vous pouvez la remplacer par une adresse plus conviviale comme tom@fourthcoffee.cn. Vous aurez besoin de votre propre nom de domaine, comme fourthcoffee.cn d’abord. Si c'est déjà le cas, tant mieux. Sinon, découvrez comment en [acheter un auprès d'un bureau d'enregistrement de domaines](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

Lorsque vous modifiez l’e-mail de votre domaine pour qu’il arrive à Microsoft 365, en mettant à jour l’enregistrement MX de votre domaine lors de l’installation, tous les e-mails envoyés à ce domaine commencent à Microsoft 365. Avant de modifier l’enregistrement MX, veillez à ajouter des utilisateurs et à créer des boîtes aux lettres dans Microsoft 365 pour toutes les personnes qui ont des e-mails sur votre domaine. Vous ne souhaitez pas déplacer le courrier électronique de tous les utilisateurs de votre domaine vers Microsoft 365 ? Vous pouvez prendre des mesures pour [piloter Microsoft 365 avec seulement quelques adresses e-mail à la place](../misc/pilot-microsoft-365-from-my-custom-domain.md).
  
## <a name="set-up-business-email-with-a-new-domain"></a>Configurer la messagerie professionnelle avec un nouveau domaine

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA?autoplay=false]

Achetez un nouveau nom de domaine pour votre adresse e-mail et configurez les adresses e-mail avec Microsoft 365.

1. Achetez un nouveau nom de domaine pour votre adresse e-mail en fournissant vos informations de contact pour le nouveau nom de domaine, en choisissant votre mode de paiement, puis en passant votre commande.
1. Modifiez la première partie de l’adresse (avant le signe @) ou laissez-la en l’état. 
1. Déconnectez-vous de Microsoft 365, puis connectez-vous avec votre nouvelle adresse e-mail. Les adresses e-mail de vos employés sont mises à jour avec le nouveau domaine. 

## <a name="set-up-business-email-with-an-existing-domain"></a>Configurer la messagerie professionnelle avec un domaine existant

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu?autoplay=false]

Utilisez un nom de domaine que vous possédez déjà, que vous l’utilisiez pour une adresse de site web ou une adresse e-mail auprès d’un autre fournisseur.

1. Connectez-vous au site web qui héberge votre domaine. Cliquez sur un bouton pour vérifier automatiquement ou mettre à jour le domaine manuellement. 
1. Personnalisez l’adresse e-mail ou laissez-la tel quelle.
1. Déconnectez-vous de Microsoft 365, puis connectez-vous avec votre nouvelle adresse e-mail. Les adresses e-mail de vos employés sont mises à jour avec le nouveau domaine.

## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>Modifiez votre adresse e-mail pour utiliser votre domaine personnalisé à l’aide de la Centre d'administration Microsoft 365

Vous devez être un Administrateur général pour procéder à ces étapes.

::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn</a>.

::: moniker-end

2. Accédez à la page **SetupDomains** > .

3. Dans la page **Domaines**, sélectionnez **Ajouter un domaine**.

4. Suivez les étapes pour confirmer que vous êtes propriétaire de votre domaine. Vous serez guidé pour tout configurer correctement avec votre domaine dans Microsoft 365.

5. Accédez aux **utilisateurs UsersActive** > .

6. Sélectionnez un utilisateur pour modifier son nom d’utilisateur et le remplacer par le domaine que vous venez d’ajouter.

> [!NOTE]
> Si vous n’utilisez pas de licence Exchange, vous ne pouvez pas utiliser le domaine pour envoyer ou recevoir des e-mails du locataire Microsoft 365.
  
## <a name="related-content"></a>Contenu connexe

[Acheter un domaine personnalisé à l’aide de Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (article)\
[Gérer les domaines](/admin) (page de liens)\
[FAQ sur les domaines](../setup/domains-faq.yml) (article)