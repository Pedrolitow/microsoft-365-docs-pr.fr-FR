---
title: Forum aux questions sur les domaines
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
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 1272bad0-4bd4-4796-8005-67d6fb3afc5a
description: Pour en savoir plus sur les domaines, trouvez des réponses à vos questions fréquemment posées.
ms.openlocfilehash: c588586ddd3d57fdbe78d7751131f61e6aa53eba
ms.sourcegitcommit: dc5de2064706137256307f100b8dc61e9797bd1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45068102"
---
# <a name="domains-faq"></a>Forum aux questions sur les domaines

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

Cet article contient des réponses aux questions fréquemment posées à propos des domaines dans Microsoft 365.

Si vous ne trouvez pas la réponse à votre question, laissez-nous un commentaire et nous l'ajouterons à la liste.

Contenu de cet article

- [Quelle est la priorité MX ?](#what-is-mx-priority)
- [Comment puis-je valider des enregistrements SPF pour mon domaine ?](#how-can-i-validate-spf-records-for-my-domain)
- [Qu’est-ce qu’un nom de domaine ?](#what-is-a-domain-name)
- [Que se passe-t-il si mon fournisseur DNS ne prend pas en charge certains types d’enregistrements ?](#what-happens-if-my-dns-provider-doesnt-support-certain-record-types)
- [Comment définir ou modifier le domaine par défaut dans Microsoft 365 ?](#how-do-i-set-or-change-the-default-domain-in-microsoft-365)
- [Puis-je ajouter des sous-domaines personnalisés ou plusieurs domaines à Microsoft 365 ?](#can-i-add-custom-subdomains-or-multiple-domains-to-microsoft-365)
- [Pourquoi ai-je un domaine « onmicrosoft.com » ?](#why-do-i-have-an-onmicrosoftcom-domain)
- [Pourquoi ai-je un domaine « onmicrosoft.de » ?](#why-do-i-have-an-onmicrosoftde-domain)
- [Comment puis-je vérifier mon statut de l’organisme ou de l’éducation ?](#how-do-i-verify-my-nonprofit-or-education-status)
    
## <a name="what-is-mx-priority"></a>Quelle est la priorité MX ?

Le courrier électronique est remis au serveur Exchange de messagerie avec le numéro de préférence le plus bas (priorité la plus élevée), de sorte que l’enregistrement MX que vous utilisez pour le routage du courrier doit avoir le numéro de préférence le plus bas, généralement 0 ou *une priorité élevée* . 
  
- Lorsque vous créez un enregistrement MX, la plupart des fournisseurs d’hébergement DNS exigent que vous définiez le numéro de préférence.
    
- Une étiquette la *préférence* de zone, et une étiquette la *priorité* . 
    
- Certains nécessitent un numéro et d’autres vous demandent de sélectionner *faible* , *moyen* ou *élevé* . 
    
- Si vous n’avez qu’un seul enregistrement MX, la valeur de Priority ou preference est correcte.
    
- Si vous en avez plusieurs, assurez-vous que l’enregistrement MX pour le routage du courrier est de priorité supérieure à celle utilisée pour valider le fait que vous êtes propriétaire du domaine.
    
## <a name="how-can-i-validate-spf-records-for-my-domain"></a>Comment puis-je valider des enregistrements SPF pour mon domaine ?

Il est important de disposer ou de créer **un seul enregistrement txt pour SPF**. Si vous disposez déjà d’un enregistrement SPF, vous devez ajouter les nouvelles valeurs Microsoft 365 à ce dernier, plutôt que d’en créer un. Une fois que vous avez ajouté ou mis à jour votre enregistrement SPF pour le courrier électronique Microsoft, vous devez vérifier que la syntaxe est correcte avec l’un des outils suivants : 
  
- [Outils de test de l’enregistrement SPF](http://www.kitterman.com/spf/validate.html)
    
- [Enquêteur SPF](https://dmarcian.com/spf-survey/)
    
- [Explorer l’interface Web](http://digwebinterface.com/)

## <a name="what-is-a-domain-name"></a>Qu’est-ce qu’un nom de domaine ?

[] Un domaine est un nom unique qui apparaît après le signe **@** dans les adresses de messagerie et après **www.** dans les adresses web. Il prend généralement la forme du nom de votre organisation et d’un suffixe Internet standard, tel que *yourbusiness.com* ou *stateuniversity.edu.* 
  
L’utilisation d’un domaine personnalisé comme «**rob \@ contoso.com**» avec Microsoft 365 peut vous aider à créer une crédibilité et une reconnaissance pour votre marque. 
  
Vous pouvez [acheter un domaine dans Microsoft 365 et nous allons le configurer automatiquement](../get-help-with-domains/buy-a-domain-name.md), ou vous pouvez acheter ou en disposer un dont vous êtes déjà propriétaire auprès d’un bureau d’enregistrement de domaines.
    
## <a name="what-happens-if-my-dns-provider-doesnt-support-certain-record-types"></a>Que se passe-t-il si mon fournisseur DNS ne prend pas en charge certains types d’enregistrements ?

Si vous gérez vos propres enregistrements DNS et que votre hôte DNS ne prend pas en charge tous les enregistrements DNS dont Microsoft 365 a besoin, certaines fonctionnalités de Microsoft 365 ne fonctionneront pas. Nous vous recommandons de transférer votre domaine vers un serveur d’inscriptions qui prend en charge tous les enregistrements DNS requis.
  
Fournisseurs qui prennent en charge tous les enregistrements DNS requis :
  
- Dynadot
    
- Auprès enomcentral
    
- Europe Registry
    
- GoDaddy
    
- Sensitiv
    
- MyHosting.com
    
- Name.com
    
- Voix presque gratuite
    
- Nettica
    
- Network Information Center (NIC)
    
- Network Solutions
    
- Register.com
  
## <a name="how-do-i-set-or-change-the-default-domain-in-microsoft-365"></a>Comment définir ou modifier le domaine par défaut dans Microsoft 365 ?

Vous devez avoir au moins un domaine personnalisé que vous avez ajouté à Microsoft 365 avant de pouvoir choisir un domaine par défaut.

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">Domaines</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines</a>.

::: moniker-end
    
2. Dans la page **domaines** , sélectionnez le domaine que vous souhaitez définir par défaut pour les nouvelles adresses de messagerie. 
    
3. Sélectionnez **Définir par défaut**.
    
::: moniker range="o365-worldwide"

Vous ne pouvez pas modifier le nom de votre domaine initial *. onmicrosoft.com* . 

::: moniker-end

::: moniker range="o365-germany"

Vous ne pouvez pas modifier le nom de votre domaine initial *. onmicrosoft.de* . 

::: moniker-end

::: moniker range="o365-21vianet"

Vous ne pouvez pas modifier le nom de votre domaine initial *. Partner.onmschina.CN* . 

::: moniker-end

## <a name="can-i-add-custom-subdomains-or-multiple-domains-to-microsoft-365"></a>Puis-je ajouter des sous-domaines personnalisés ou plusieurs domaines à Microsoft 365 ?

::: moniker range="o365-worldwide"

Oui. Pour ajouter des sous-domaines, vous devez gérer vos propres paramètres DNS sur le site Web de votre registraire. Si vous autorisez Microsoft à gérer vos paramètres DNS avec des enregistrements NS, ou si vous avez acheté le domaine auprès de Microsoft, vous ne pouvez pas ajouter de sous-domaines.

::: moniker-end

::: moniker range="o365-germany"

OK! Pour ajouter des sous-domaines, vous devez gérer vos propres paramètres DNS sur le site Web de votre registraire. Si vous autorisez Microsoft à gérer vos paramètres DNS avec des enregistrements NS, ou si vous avez acheté le domaine auprès de Microsoft, vous ne pouvez pas ajouter de sous-domaines.

::: moniker-end

::: moniker range="o365-21vianet"

OK! Pour ajouter des sous-domaines, vous devez gérer vos propres paramètres DNS sur le site Web de votre registraire. Si vous laissez 21Vianet gérer vos paramètres DNS avec des enregistrements NS, vous ne pouvez pas ajouter de sous-domaines.

::: moniker-end

En règle générale, vous pouvez ajouter jusqu’à 900 domaines à votre abonnement Microsoft 365.
  
Par exemple, vous pouvez ajouter les domaines contoso.com et contosomarketing.com, puis ajouter les sous-domaines www.contoso.com, www.partners.contoso.com, www.partners.marketing.contoso.com, etc.
  
Lorsque vous ajoutez un sous-domaine, il est automatiquement vérifié en fonction du domaine parent en cours de vérification.
  
Lorsque vous ajoutez plusieurs domaines à Microsoft 365, vous pouvez héberger des services (par exemple, des courriers électroniques) sur n’importe quel domaine que vous avez ajouté.  *Lorsque vous modifiez votre courrier électronique en Microsoft 365, en mettant à jour l’enregistrement MX d’un domaine, tous les messages envoyés à ce domaine débuteront à Microsoft 365.* 
 
::: moniker range="o365-worldwide"

> [!NOTE]
> Si vous avez ajouté un domaine contoso.com à un abonnement Microsoft 365, vous pouvez également ajouter le sous-domaine xyz.contoso.com à une autre organisation Microsoft 365. Lors de l’ajout du sous-domaine, vous êtes invité à ajouter un enregistrement TXT dans le fournisseur d’hébergement DNS.

## <a name="why-do-i-have-an-onmicrosoftcom-domain"></a>Pourquoi ai-je un domaine « onmicrosoft.com » ?

Microsoft 365 crée un domaine pour vous, comme *contoso.onmicrosoft.com*, lorsque vous vous inscrivez auprès du service. Le nom d’utilisateur que vous créez lors de votre inscription comprend le domaine, par exemple *Alan@contoso.onmicrosoft.com*. 
  
 **Si vous voulez faire ressembler votre courrier électronique *Alan \@ contoso.com*:** [acheter le domaine](../get-help-with-domains/buy-a-domain-name.md) ou simplement suivre les étapes de la procédure [ajouter vos utilisateurs et votre domaine à Microsoft 365](add-domain.md) si vous en êtes déjà propriétaire. 
  
- **Vous ne pouvez pas renommer le domaine onmicrosoft après l’inscription.** Par exemple, si le domaine initial que vous avez choisi était fourthcoffee.onmicrosoft.com, vous ne pouvez pas le modifier pour qu’il soit fabrikam.onmicrosoft.com. Pour utiliser un autre domaine onmicrosoft.com, vous devez démarrer un nouvel abonnement avec Microsoft 365. 
    
- **Vous ne pouvez pas renommer l’URL de votre site d’équipe.** L’URL de votre site d’équipe est basée sur le nom de votre domaine onmicrosoft.com. Malheureusement, en raison de la façon dont fonctionne l’architecture SharePoint Online, vous ne pouvez pas renommer le site d’équipe. 
    
- **Vous ne pouvez pas supprimer votre domaine onmicrosoft.** Microsoft 365 doit la conserver car elle est utilisée en arrière-plan pour votre abonnement. Toutefois, vous n’êtes pas obligé d’utiliser le domaine vous-même après avoir ajouté un domaine personnalisé. 
    
Vous pouvez continuer à utiliser le domaine onmicrosoft.com initial même après avoir ajouté votre domaine. Il fonctionne toujours pour le courrier électronique et d’autres services, c’est donc votre choix.
  
::: moniker-end

::: moniker range="o365-germany"
## <a name="why-do-i-have-an-onmicrosoftde-domain"></a>Pourquoi ai-je un domaine « onmicrosoft.de » ?

Microsoft 365 crée un domaine pour vous, comme *contoso.onmicrosoft.de*, lorsque vous vous inscrivez auprès du service. Le nom d’utilisateur que vous créez lors de votre inscription comprend le domaine, par exemple *Alan@contoso.onmicrosoft.de*. 
  
 **Si vous souhaitez que votre courrier électronique ressemble à *Alan@contoso.de*:** [achetez le domaine](../get-help-with-domains/buy-a-domain-name.md) ou suivez simplement les étapes de la procédure [ajouter vos utilisateurs et votre domaine à Microsoft 365](add-domain.md) si vous en êtes déjà propriétaire. 
  
- **Vous ne pouvez pas renommer le domaine onmicrosoft après l’inscription.** Par exemple, si le domaine initial que vous avez choisi était fourthcoffee.onmicrosoft.de, vous ne pouvez pas le modifier pour qu’il soit fabrikam.onmicrosoft.de. Pour utiliser un autre domaine onmicrosoft.de, vous devez démarrer un nouvel abonnement avec Microsoft 365. 
    
- **Vous ne pouvez pas renommer l’URL de votre site d’équipe.** L’URL de votre site d’équipe est basée sur le nom de votre domaine onmicrosoft.de. Malheureusement, en raison de la façon dont fonctionne l’architecture SharePoint Online, vous ne pouvez pas renommer le site d’équipe. 
    
- **Vous ne pouvez pas supprimer votre domaine onmicrosoft.** Microsoft 365 doit la conserver car elle est utilisée en arrière-plan pour votre abonnement. Toutefois, vous n’êtes pas obligé d’utiliser le domaine vous-même après avoir ajouté un domaine personnalisé. 
    
Vous pouvez continuer à utiliser le domaine onmicrosoft.de initial même après avoir ajouté votre domaine. Il fonctionne toujours pour le courrier électronique et d’autres services, c’est donc votre choix.
  
::: moniker-end

## <a name="how-do-i-verify-my-nonprofit-or-education-status"></a>Comment puis-je vérifier mon statut de l’organisme ou de l’éducation ?

1. Sélectionnez **configuration** dans le [Centre d’administration](https://docs.microsoft.com/microsoft-365/admin/admin-home) pour démarrer l’Assistant. (Veillez à vous connecter d’abord à Microsoft 365.) 
    
2. Pour devenir l’administrateur de votre école, sélectionnez l’option **devenir administrateur** dans Microsoft 365. 
    
3. Vous serez invité à ajouter un enregistrement TXT DNS sur le site Web hôte DNS de votre domaine. Pourquoi ? Étant donné qu’en se connectant au niveau de l’hôte DNS et en ajoutant un enregistrement pour votre domaine, vous prouvez à Microsoft 365 que vous êtes propriétaire du nom de domaine.
    
4. Après avoir ajouté l’enregistrement, revenez au portail Microsoft 365 et confirmez que vous l’avez ajouté, afin que Microsoft 365 puisse vérifier.
    
Disposez-vous d’une offre caritative et souhaitez-vous obtenir Microsoft 365 ? Assurez-vous que [votre organisation est qualifiée](https://www.microsoft.com/en-us/nonprofits/eligibility) et inscrivez-vous au service. 
  
Vous souhaitez en savoir plus sur le devenir administrateur de votre école ? [Pour en savoir plus, consultez la rubrique](https://docs.microsoft.com/microsoft-365/education/deploy/becoming-an-admin-in-office-365-education
).