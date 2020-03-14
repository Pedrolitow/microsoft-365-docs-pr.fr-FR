---
title: Foire aux questions domaines
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 1272bad0-4bd4-4796-8005-67d6fb3afc5a
description: Pour plus d’informations sur les domaines dans Office 365, recherchez les réponses à vos questions dans FAQ.
ms.custom: okr_smb
ms.openlocfilehash: f3c72f1ce772e3021d79aa4568dbfdb700400803
ms.sourcegitcommit: 93e6bf1b541e22129f8c443051375d0ef1374150
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "42633182"
---
# <a name="domains-faq"></a>Foire aux questions domaines

Cet article contient des réponses aux questions fréquemment posées à propos des domaines dans Office 365.

Si vous ne trouvez pas la réponse à votre question, laissez-nous un commentaire et nous l'ajouterons à la liste.
    
## <a name="what-is-mx-priority"></a>Quelle est la priorité MX ?

Le courrier électronique est remis au serveur Exchange de messagerie avec le numéro de préférence le plus bas (priorité la plus élevée), de sorte que l’enregistrement MX que vous utilisez pour le routage du courrier doit avoir le numéro de préférence le plus bas, généralement 0 ou *une priorité élevée* . 
  
- Lorsque vous créez un enregistrement MX, la plupart des fournisseurs d’hébergement DNS exigent que vous définiez le numéro de préférence.
    
- Une étiquette la *préférence* de zone, et une étiquette la *priorité* . 
    
- Certains nécessitent un numéro et d’autres vous demandent de sélectionner *faible* , *moyen* ou *élevé* . 
    
- Si vous n’avez qu’un seul enregistrement MX, la valeur de Priority ou preference est correcte.
    
- Si vous en avez plusieurs, assurez-vous que l’enregistrement MX pour le routage du courrier est de priorité supérieure à celle utilisée pour valider le fait que vous êtes propriétaire du domaine.
    
## <a name="how-can-i-validate-spf-records-for-my-domain"></a>Comment puis-je valider des enregistrements SPF pour mon domaine ?

Il est important de disposer ou de créer **un seul enregistrement txt pour SPF**. Si vous disposez déjà d’un enregistrement SPF, vous devez ajouter les nouvelles valeurs Office 365 au lieu d’en créer un. Une fois que vous avez ajouté ou mis à jour votre enregistrement SPF pour le courrier électronique Office 365, vous devez vérifier que la syntaxe est correcte avec l’un des outils suivants : 
  
- [Outils de test de l’enregistrement SPF](http://www.kitterman.com/spf/validate.html)
    
- [Enquêteur SPF](https://dmarcian.com/spf-survey/)
    
- [Explorer l’interface Web](http://digwebinterface.com/)
    
## <a name="how-does-office-365-manage-my-dns-records"></a>Comment Office 365 gère-t-il mes enregistrements DNS ?

Il existe deux options pour la gestion du DNS avec Office 365 :
  
1. Vous modifiez vos enregistrements de serveur de noms (NS), puis Office 365 prend en charge tous les enregistrements spécifiques aux services, comme la configuration de votre enregistrement MX pour le courrier électronique. **Recommandation**
    
2. Vous ajoutez vous-même des enregistrements DNS pour le courrier électronique et d’autres services Office 365 au niveau de votre hôte DNS. **(Experts uniquement)**
    
### <a name="office-365-creates-and-hosts-the-dns-records"></a>Office 365 crée et héberge les enregistrements DNS 
**Avantages** 
- Vous n’avez pas à vous soucier des erreurs dans les valeurs que vous entrez pour les enregistrements DNS pour les services Office 365.  
- Vous bénéficiez d’une plus grande flexibilité dans votre choix de bureau d’enregistrement de domaines et d’hôte DNS. 
- Tout fournisseur qui vous permet de modifier vos enregistrements de serveur de noms fonctionnera, même si le fournisseur ne prend pas en charge tous les types d’enregistrements requis.   
- Lorsque Office 365 ajoute de nouveaux enregistrements DNS, il n’est pas nécessaire d’effectuer des mises à jour.  

#### <a name="disadvantages"></a>Inconvénients 
- Vous ne pouvez pas modifier vos enregistrements DNS pour héberger le courrier électronique en dehors d’Office 365. 
- Si vous utilisez déjà un site Web public avec votre domaine pour son adresse, par exemple www.fourthcoffee.com, vous devez rediriger les personnes vers cette adresse à partir d’Office 365. 
- La configuration de la redirection nécessite une adresse IP statique, qui n’est pas toujours facilement disponible pour les sites Web publics. -Si votre bureau d’enregistrement de domaines actuel ne vous permet pas de modifier les enregistrements de serveur de noms de votre domaine, vous devez passer à un autre serveur d’inscriptions pour utiliser cette option de gestion DNS.  

 ### <a name="you-manage-the-dns-records-yourself"></a>Vous gérez les enregistrements DNS vous-même 
 #### <a name="advantages"></a>Avantages
- Vous contrôlez les enregistrements DNS pour les services Office 365.   
- Si vous disposez d’un site Web public avec votre domaine pour son adresse, par exemple www.fourthcoffee.com, vous n’avez pas à vous soucier de l’utilisation de la redirection afin de vous assurer que les utilisateurs peuvent toujours accéder à votre site Web après avoir configuré votre domaine dans Office 365.    
- Vous avez la possibilité d’héberger des messages ailleurs, par exemple avec un serveur Exchange local.  
 
#### <a name="disadvantages"></a>Inconvénients
Vous devez configurer les enregistrements DNS pour les services Office 365 vous-même (sauf si vous disposez d’un domaine GoDaddy). 
-  Si votre hôte DNS actuel ne prend pas en charge tous les types d’enregistrements requis pour Office 365, certaines fonctionnalités Office 365 ne seront pas disponibles et vous devrez peut-être basculer vers un autre hôte DNS. 
- Lorsque Office 365 modifie les conditions requises pour les enregistrements DNS, ou ajoute de nouveaux services, vous devez effectuer des mises à jour vous-même auprès de votre hôte DNS. 
   
## <a name="what-is-a-domain-name"></a>Qu’est-ce qu’un nom de domaine ?


[] Un domaine est un nom unique qui apparaît après le signe **@** dans les adresses de messagerie et après **www.** dans les adresses web. Il prend généralement la forme du nom de votre organisation et d’un suffixe Internet standard, tel que *yourbusiness.com* ou *stateuniversity.edu.* 
  
L’utilisation d’un domaine personnalisé comme «**rob\@contoso.com**» avec Office 365 peut vous aider à créer une crédibilité et une reconnaissance pour votre marque. 
  
Vous pouvez [acheter un domaine dans Office 365 et nous allons le configurer automatiquement](../get-help-with-domains/buy-a-domain-name.md), ou vous pouvez acheter ou en disposer un dont vous êtes déjà propriétaire auprès d’un bureau d’enregistrement de domaines.
  
## <a name="can-i-transfer-a-domain-i-purchased-from-microsoft-to-another-provider"></a>Puis-je transférer un domaine que j’ai acheté de Microsoft à un autre fournisseur ?

Oui, mais vous ne pouvez pas transférer un domaine Office 365 vers un autre bureau d’enregistrement jusqu’à 60 jours après l’avoir acheté avec Office 365.

Veuillez noter qu’une requête *Whois* affiche un bureau d’enregistrement de domaines Office 365 acheté comme sauvage West Domains LLC. Toutefois, seul Office 365 doit être contacté concernant votre domaine acheté Office 365.
  
Suivez les étapes ci-dessous pour obtenir le code sur Office 365, puis accédez au site Web du Bureau d’enregistrement de domaine pour configurer le transfert de votre nom de domaine vers ce serveur d’inscriptions.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
    Si vous utilisez Office 365 Germany, accédez à la page de ces <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">domaines</a> . 
    
    Si vous utilisez Office 365 géré par 21Vianet, accédez à la page de ce <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domaine</a> .
    
2. Sur la page **domaines** , sélectionnez le domaine Office 365 que vous souhaitez transférer vers un autre bureau d’enregistrement de domaines, puis sélectionnez **transfert** > de domaine activé pour le transfert de**domaine**.
       
4. Suivez les étapes pour préparer le transfert de votre domaine.
    
5. Une fois le code obtenu, accédez au site Web du Bureau d’enregistrement de domaines dans lequel vous souhaitez gérer le nom de votre domaine et suivre leur orientation pour le transfert d’un domaine (recherchez de l’aide sur son site Web).
    
6. Si vous avez besoin de nouveau de voir le code, dans la page **paramètres du domaine** dans Office 365, sélectionnez **afficher le code d’autorisation pour le transfert de domaine**.
    
7. Une fois le transfert terminé, vous allez renouveler votre domaine au niveau du nouveau bureau d’enregistrement de domaines.
    
8. Pour terminer le processus, revenez à la page **domaines** du centre d’administration et sélectionnez **effectuer un transfert de domaine complet**. 

*Remarque : Notez que les domaines achetés par Office 365 ne sont pas éligibles pour les modifications de serveur de noms ou transférant le domaine entre les locataires Office 365.  Si l’une ou l’autre de ces valeurs est requise, l’inscription de domaine doit être transférée vers un autre serveur d’inscriptions.*
    
## <a name="how-do-i-change-how-my-dns-records-are-managed-in-office-365"></a>Comment puis-je modifier la façon dont mes enregistrements DNS sont gérés dans Office 365 ?

### <a name="change-dns-management-to-a-dns-host-outside-office-365"></a>Modifier la gestion du DNS en hôte DNS en dehors d’Office 365
   
1. Connectez-vous au bureau d’enregistrement de domaines de votre domaine.
    
2. Recherchez la zone sur le site Web du serveur d’inscriptions où vous mettez à jour les enregistrements de serveur de noms et mettez à jour les serveurs de noms pour qu’ils pointent vers l’hôte DNS de votre domaine. (L’hôte DNS est souvent le Bureau d’enregistrement de domaines.)
    
3. Suivez un lien pour accéder à l’Assistant Configuration des domaines :
    
4. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
    Si vous utilisez Office 365 Germany, accédez à la page de ces <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">domaines</a> . 
    
    Si vous utilisez Office 365 géré par 21Vianet, accédez à la page de ce <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domaine</a> .
    
5. Dans la page **domaines** , sélectionnez le domaine que vous changez, puis sélectionnez **gestion DNS**.
    
6. Dans l’Assistant Configuration des domaines, dans la page **configurer vos services en ligne** , sélectionnez **je vais gérer mes propres enregistrements DNS**, puis cliquez sur **suivant**.
    
7. Ajoutez les enregistrements DNS suggérés par l’Assistant sur la page **mettre à jour les paramètres DNS** sur le site Web de votre registraire. 
    
8. Une fois que vous avez ajouté les enregistrements, revenez à Office 365 et sélectionnez **vérifier**.
    

### <a name="change-dns-management-to-office-365"></a>Modifier la gestion du DNS vers Office 365
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
    Si vous utilisez Office 365 Germany, accédez à la page de ces <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">domaines</a> . 
    
    Si vous utilisez Office 365 géré par 21Vianet, accédez à la page de ce <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domaine</a> .
    
2. Dans la page **domaines** , sélectionnez le domaine que vous changez, puis sélectionnez **gestion DNS**.
    
3. Dans l’Assistant Configuration des domaines, dans la page **configurer vos services en ligne** , sélectionnez **configurer mes services en ligne pour moi. (Recommandé)**, puis cliquez sur **suivant**.
    
4. Si vous n’avez pas encore vérifié le domaine, suivez la procédure décrite ci-dessous.
    
5. Sur la page **mettre à jour les paramètres DNS** , nous répertorions les serveurs de noms pour Office 365. Accédez au bureau d’enregistrement de domaines de votre domaine et mettez à jour les serveurs de noms sur les serveurs de noms Office 365. 
    
4. Une fois que vous avez mis à jour les serveurs de noms, **Patientez au moins une heure**. Ensuite, dans l’Assistant dans Office 365, sélectionnez **vérifier**.
    
## <a name="what-happens-if-my-dns-provider-doesnt-support-certain-record-types"></a>Que se passe-t-il si mon fournisseur DNS ne prend pas en charge certains types d’enregistrements ?

Si vous gérez vos propres enregistrements DNS et que votre hôte DNS ne prend pas en charge tous les enregistrements DNS dont Office 365 a besoin, certaines fonctionnalités Office 365 ne fonctionneront pas. Nous vous recommandons de transférer votre domaine vers un serveur d’inscriptions qui prend en charge tous les enregistrements DNS requis.
  
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
    
 **Si les enregistrements SRV ne sont pas pris en charge**, les fonctionnalités Office 365 suivantes ne sont pas disponibles : 
  
- Intégration de la messagerie instantanée et de la présence Skype entreprise Online à Outlook Web App
    
- Communication externe (Fédération) avec des utilisateurs de Skype entreprise Online dans d’autres organisations.
    
- Connectivité Internet publique (PIC) avec des utilisateurs de Skype entreprise Online connectés à l’aide d’un compte Microsoft (anciennement appelé Windows Live ID).
    
 **Si plusieurs enregistrements CNAME ne sont pas pris en charge,** vous devez choisir entre les fonctionnalités suivantes pour Skype entreprise Online : 
  
- Les clients de bureau et les clients mobiles de messagerie peuvent utiliser la découverte automatique pour trouver automatiquement le service Exchange Online afin que les utilisateurs puissent se connecter sans avoir à entrer un nom de serveur.
    
- Les clients de bureau Skype entreprise Online peuvent utiliser la découverte automatique pour trouver automatiquement le service Skype entreprise Online afin que les utilisateurs puissent se connecter sans avoir à entrer un nom de serveur.
    
- Les clients mobiles Skype entreprise Online peuvent utiliser la découverte automatique pour trouver automatiquement le service Skype entreprise Online afin que les utilisateurs puissent se connecter sans avoir à entrer un nom de serveur.
    
 **Si les enregistrements SPF/txt ne sont pas pris en charge**, d’autres personnes peuvent être en mesure d’utiliser votre domaine pour envoyer du courrier indésirable ou d’autres messages malveillants. Les enregistrements SPF fonctionnent en identifiant les serveurs qui sont autorisés à envoyer des messages électroniques à partir de votre domaine. 
  
## <a name="how-do-i-set-or-change-the-default-domain-in-office-365"></a>Comment définir ou modifier le domaine par défaut dans Office 365 ?

Vous devez avoir au moins un domaine personnalisé que vous avez ajouté à Office 365 avant de pouvoir choisir un domaine par défaut.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
    Si vous utilisez Office 365 Germany, accédez à la page de ces <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">domaines</a> . 
    
    Si vous utilisez Office 365 géré par 21Vianet, accédez à la page de ce <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domaine</a> .
    
2. Dans la page **domaines** , sélectionnez le domaine que vous souhaitez définir par défaut pour les nouvelles adresses de messagerie. 
    
3. Sélectionnez **définir par défaut**.
    
::: moniker range="o365-worldwide"

Vous ne pouvez pas modifier le nom de votre domaine initial *. onmicrosoft.com* . 

::: moniker-end

::: moniker range="o365-germany"

Vous ne pouvez pas modifier le nom de votre domaine initial *. onmicrosoft.de* . 

::: moniker-end

::: moniker range="o365-21vianet"

Vous ne pouvez pas modifier le nom de votre domaine initial *. Partner.onmschina.CN* . 

::: moniker-end

## <a name="can-i-add-custom-subdomains-or-multiple-domains-to-office-365"></a>Puis-je ajouter des sous-domaines personnalisés ou plusieurs domaines à Office 365 ?

::: moniker range="o365-worldwide"

OK! Pour ajouter des sous-domaines, vous devez gérer vos propres paramètres DNS sur le site Web de votre registraire. Si vous autorisez Microsoft à gérer vos paramètres DNS avec des enregistrements NS, ou si vous avez acheté le domaine auprès de Microsoft, vous ne pouvez pas ajouter de sous-domaines.

::: moniker-end

::: moniker range="o365-germany"

OK! Pour ajouter des sous-domaines, vous devez gérer vos propres paramètres DNS sur le site Web de votre registraire. Si vous autorisez Microsoft à gérer vos paramètres DNS avec des enregistrements NS, ou si vous avez acheté le domaine auprès de Microsoft, vous ne pouvez pas ajouter de sous-domaines.

::: moniker-end

::: moniker range="o365-21vianet"

OK! Pour ajouter des sous-domaines, vous devez gérer vos propres paramètres DNS sur le site Web de votre registraire. Si vous laissez 21Vianet gérer vos paramètres DNS avec des enregistrements NS, vous ne pouvez pas ajouter de sous-domaines.

::: moniker-end

En règle générale, vous pouvez ajouter jusqu’à 900 domaines à votre abonnement Office 365.
  
Par exemple, vous pouvez ajouter les domaines contoso.com et contosomarketing.com, puis ajouter les sous-domaines www.contoso.com, www.partners.contoso.com, www.partners.marketing.contoso.com, etc.
  
Lorsque vous ajoutez un sous-domaine, il est automatiquement vérifié en fonction du domaine parent en cours de vérification.
  
Lorsque vous ajoutez plusieurs domaines à Office 365, vous pouvez héberger des services (par exemple, des courriers électroniques) sur n’importe quel domaine que vous avez ajouté.  *Lorsque vous modifiez votre courrier électronique en Office 365, en mettant à jour l’enregistrement MX d’un domaine, tous les messages envoyés à ce domaine débuteront dans Office 365.* 
 
::: moniker range="o365-worldwide"

> [!NOTE]
> Si vous avez déjà ajouté un domaine contoso.com à un client Office 365, vous pouvez également ajouter le sous-domaine xyz.contoso.com à un autre client Office 365. Lors de l’ajout du sous-domaine, vous serez invité à ajouter un enregistrement TXT dans le fournisseur d’hébergement DNS.

## <a name="why-do-i-have-an-onmicrosoftcom-domain"></a>Pourquoi ai-je un domaine « onmicrosoft.com » ?

Office 365 crée un domaine pour vous, comme *contoso.onmicrosoft.com*, lorsque vous vous inscrivez auprès du service. Le nom d’utilisateur que vous créez lors de votre inscription comprend le domaine, par exemple *Alan@contoso.onmicrosoft.com*. 
  
 **Si vous voulez faire ressembler votre courrier *électronique\@Alan contoso.com*:** [acheter le domaine](../get-help-with-domains/buy-a-domain-name.md) ou simplement suivre les étapes de la procédure [ajouter vos utilisateurs et votre domaine à Office 365](add-domain.md) si vous en êtes déjà propriétaire. 
  
- **Vous ne pouvez pas renommer le domaine onmicrosoft après l’inscription.** Par exemple, si le domaine initial que vous avez choisi était fourthcoffee.onmicrosoft.com, vous ne pouvez pas le modifier pour qu’il soit fabrikam.onmicrosoft.com. Pour utiliser un autre domaine onmicrosoft.com, vous devez démarrer un nouvel abonnement avec Office 365. 
    
- **Vous ne pouvez pas renommer l’URL de votre site d’équipe.** L’URL de votre site d’équipe est basée sur le nom de votre domaine onmicrosoft.com. Malheureusement, en raison de la façon dont fonctionne l’architecture SharePoint Online, vous ne pouvez pas renommer le site d’équipe. 
    
- **Vous ne pouvez pas supprimer votre domaine onmicrosoft.** Office 365 doit le conserver, car il est utilisé en arrière-plan pour votre abonnement. Toutefois, vous n’êtes pas obligé d’utiliser le domaine vous-même après avoir ajouté un domaine personnalisé. 
    
Vous pouvez continuer à utiliser le domaine onmicrosoft.com initial même après avoir ajouté votre domaine. Il fonctionne toujours pour le courrier électronique et d’autres services, c’est donc votre choix.
  
::: moniker-end

::: moniker range="o365-germany"
## <a name="why-do-i-have-an-onmicrosoftde-domain"></a>Pourquoi ai-je un domaine « onmicrosoft.de » ?

Office 365 crée un domaine pour vous, comme *contoso.onmicrosoft.de*, lorsque vous vous inscrivez auprès du service. Le nom d’utilisateur que vous créez lors de votre inscription comprend le domaine, par exemple *Alan@contoso.onmicrosoft.de*. 
  
 **Si vous souhaitez que votre courrier électronique ressemble à *Alan@contoso.de*:** [achetez le domaine](../get-help-with-domains/buy-a-domain-name.md) ou suivez simplement les étapes de la procédure [ajouter vos utilisateurs et votre domaine à Office 365](add-domain.md) si vous en êtes déjà propriétaire. 
  
- **Vous ne pouvez pas renommer le domaine onmicrosoft après l’inscription.** Par exemple, si le domaine initial que vous avez choisi était fourthcoffee.onmicrosoft.de, vous ne pouvez pas le modifier pour qu’il soit fabrikam.onmicrosoft.de. Pour utiliser un autre domaine onmicrosoft.de, vous devez démarrer un nouvel abonnement avec Office 365. 
    
- **Vous ne pouvez pas renommer l’URL de votre site d’équipe.** L’URL de votre site d’équipe est basée sur le nom de votre domaine onmicrosoft.de. Malheureusement, en raison de la façon dont fonctionne l’architecture SharePoint Online, vous ne pouvez pas renommer le site d’équipe. 
    
- **Vous ne pouvez pas supprimer votre domaine onmicrosoft.** Office 365 doit le conserver, car il est utilisé en arrière-plan pour votre abonnement. Toutefois, vous n’êtes pas obligé d’utiliser le domaine vous-même après avoir ajouté un domaine personnalisé. 
    
Vous pouvez continuer à utiliser le domaine onmicrosoft.de initial même après avoir ajouté votre domaine. Il fonctionne toujours pour le courrier électronique et d’autres services, c’est donc votre choix.
  
::: moniker-end

## <a name="how-do-i-verify-my-nonprofit-or-education-status"></a>Comment puis-je vérifier mon statut de l’organisme ou de l’éducation ?

1. Sélectionnez **configuration** dans le [Centre d’administration](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791.aspx) pour démarrer l’Assistant. (Veillez à vous connecter d’abord à Office 365.) 
    
2. Pour devenir l’administrateur de votre école, sélectionnez l’option **devenir administrateur** dans Office 365. 
    
3. Vous serez invité à ajouter un enregistrement TXT DNS sur le site Web hôte DNS de votre domaine. Pourquoi ? Étant donné qu’en se connectant au niveau de l’hôte DNS et en ajoutant un enregistrement pour votre domaine, vous prouvez à Office 365 que vous êtes propriétaire du nom de domaine.
    
4. Après avoir ajouté l’enregistrement, revenez au portail Office 365 et confirmez que vous l’avez ajouté, de sorte que Office 365 puisse vérifier.
    
Disposez-vous d’une offre caritative et souhaitez obtenir Office 365 ? Assurez-vous que [votre organisation est qualifiée](https://www.microsoft.com/en-us/nonprofits/eligibility) et inscrivez-vous au service. 
  
Vous souhaitez en savoir plus sur le devenir administrateur de votre école ? [Pour en savoir plus, consultez la rubrique](https://docs.microsoft.com/microsoft-365/education/deploy/becoming-an-admin-in-office-365-education
).
  
## <a name="can-i-pilot-office-365-with-just-a-few-email-addresses-from-my-custom-domain"></a>Puis-je piloter Office 365 avec seulement quelques adresses de messagerie à partir de mon domaine personnalisé ?

Vous pouvez, mais il existe des limitations :
  
- Votre fournisseur de messagerie actuel doit fournir le transfert du courrier électronique.
    
- Vous devez gérer vos enregistrements DNS Office 365 auprès de votre fournisseur d’hébergement DNS, au lieu de faire en sorte que Office 365 gère ces enregistrements pour vous. Pour en savoir plus, consultez la rubrique ajouter votre domaine à Office 365 lorsque vous voulez gérer vos propres enregistrements DNS.
    
- Certaines fonctionnalités Office 365 ne seront pas disponibles :
- Les utilisateurs ne peuvent pas voir les informations de disponibilité pour les utilisateurs qui se trouvent sur l’autre fournisseur de messagerie.
- Les administrateurs ne pourront pas administrer les comptes de tous les utilisateurs à partir d’un seul emplacement.
- Les utilisateurs peuvent ne pas être en mesure d’utiliser le filtrage du courrier indésirable Office 365

### <a name="how-to-set-up-an-office-365-pilot"></a>Procédure de configuration d’un pilote Office 365
    
1. Se connecter au centre d’administration Microsoft 365
    
    1. Connectez-vous à Office 365 avec votre compte professionnel ou scolaire.
        
    2. Accédez à **paramètres** \> **Domains**. 
    
2. Vérifier que vous êtes propriétaire du domaine que vous souhaitez utiliser
    
    1. Dans la page **domaines** , sélectionnez **Ajouter un domaine**. 
        
    2. Dans le panneau, tapez le domaine, dans cet exemple cohowinery.com, puis cliquez sur **suivant**. 
        
    3. Sur la page **vérifier** le domaine, suivez les instructions pas à pas. 
        
    4. Dans la liste déroulante, sélectionnez votre fournisseur d’hébergement DNS et suivez les instructions pour montrer que vous êtes propriétaire du domaine.
        
    5. Sélectionnez **Verify (vérifier**). Les modifications DNS prennent effet entre quelques minutes et 72 heures. 
        
    6. Une fois la vérification réussie, vous serez invité à modifier vos enregistrements DNS.
    
3. Marquer le domaine comme étant partagé dans Exchange Online
    
    1. Accédez au **Centre d’administration Exchange** . 
        
    2. Dans la section **flux de messagerie** , sélectionnez **domaines acceptés**. 
        
    3. Double-cliquez sur le domaine que vous souhaitez modifier.
        
    4. Dans la fenêtre qui s’ouvre, sélectionnez **relais interne**. 
        
    5. Cliquez sur **Enregistrer**. Ce paramètre peut nécessiter quelques minutes. 
    
4. Si vous le souhaitez, débloquez le serveur de messagerie existant.
    
    1. Office 365 utilise Exchange Online Protection (EOP) pour la protection contre le courrier indésirable. Si EOP détecte un volume élevé de courrier indésirable transféré par votre serveur de messagerie actuel, il peut le bloquer, ce qui empêche le transfert de fonctionner. Si vous êtes sûr de la protection anti-courrier indésirable que votre autre fournisseur de messagerie utilise, vous pouvez autoriser son serveur dans Office 365. Toutefois, cela permettra également aux courriers indésirables qui transitent par votre serveur d’origine d’être transmis aux boîtes aux lettres Office 365 et vous ne pourrez pas évaluer la manière dont Office 365 empêche le courrier indésirable.
    
    2. Accédez au centre d’administration Exchange.
        
    3. Dans le centre d’administration Exchange, sélectionnez **protection**, puis **filtre de connexion**. 
        
    4. Dans la **liste**d’adresses IP autorisées **+**, sélectionnez et ajoutez l’adresse IP du serveur de messagerie que vous pouvez obtenir de votre fournisseur de messagerie actuel. 
    
5. Créer des comptes d’utilisateurs et définir l’adresse principale (de réponse)
    
    1. Aller au Centre d’administration Microsoft 365.
        
    2. Dans la barre de navigation de gauche **, sélectionnez** \> utilisateurs **actifs**. 
        
    3. Créez les comptes d’utilisateur.
        
    4. Pour chaque compte, sélectionnez **+ (nouveau)**, puis renseignez les informations requises. 
        
    5. Pour conserver le courrier électronique de l’utilisateur comme il le fait, le champ **nom d’utilisateur** doit être identique à l’adresse de messagerie existante de l’utilisateur. 
        
    6. En regard de nom d’utilisateur, sélectionnez votre nom de domaine personnalisé dans la liste déroulante.
        
    7. Sélectionnez **créer** \> une **fermeture**. 
        
6. Mettre à jour les enregistrements DNS au niveau de votre fournisseur d’hébergement DNS
    
    1. Connectez-vous au site Web de votre fournisseur d’hébergement DNS et suivez les [étapes créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Office 365](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). **Faites les exceptions suivantes :**
    
        1. Ne créez pas de nouvel enregistrement MX ou ne modifiez pas votre enregistrement MX existant.
            
        2. Si vous disposez déjà d’un enregistrement SPF (Sender Policy Framework) pour votre fournisseur de messagerie précédent, au lieu de créer un nouvel enregistrement SPF (TXT) pour Exchange Online, ajoutez simplement « inclure include. protection. Outlook. com » à l’enregistrement TXT actuel. Par exemple, « v = spf1 mx include :adatum. com include include. protection. Outlook. com ~ All ».
            
        3. Si vous n’avez pas encore d’enregistrement SPF, modifiez celui recommandé par Office 365 pour inclure le domaine de votre fournisseur de messagerie actuel, plus spf.protection.outlook.com. Autorise les messages sortants des deux systèmes de messagerie.
            
7. Configurer le transfert du courrier électronique auprès de votre fournisseur actuel
    
    1. Auprès de votre fournisseur de messagerie actuel, configurez le transfert pour vos comptes de messagerie des utilisateurs vers votre domaine onmicrosoft.com :
        
    2. La boîte aux lettres de l’utilisateur A doit transférer vers usera@yourcompany.onmicrosoft.com
        
    3. La boîte aux lettres de l’utilisateur B doit transférer vers userb@yourcompany.onmicrosoft.com
        
    4. Lorsque vous effectuez cette étape :
        
    5. Tous les messages envoyés à usera@yourcompany.com et userb@yourcompany.com seront disponibles dans Office 365.
    
    6. Remarques :
        
        - Contactez votre fournisseur de messagerie actuel pour obtenir les étapes exactes de configuration du transfert.
            
        - Vous n’avez pas besoin de conserver une copie des messages au niveau du fournisseur de messagerie actuel.
            
        - La plupart des fournisseurs transfèrent le courrier électronique en laissant l’adresse de réponse de l’expéditeur intacte, de sorte que les réponses soient envoyées à l’expéditeur d’origine.
    
8. Tester le flux de courrier
    
    1. Connectez-vous à Outlook Web App en utilisant les informations d’identification de l’utilisateur A.
        
    2. Effectuez les tests suivants :
        
    3. Testez le courrier électronique 365 Office local. Par exemple, envoyez un message électronique à l’utilisateur B. Ce message électronique doit être remis immédiatement. Dans ce scénario, le message n’est pas acheminé vers la boîte aux lettres de l’utilisateur B sur votre serveur d’origine car Office 365 voit la boîte aux lettres comme étant locale.
        
    4. Testez le courrier électronique à une personne qui se trouve sur l’autre système de courrier. Par exemple, envoyez un message électronique à l’utilisateur C. Ce message électronique doit être remis à la boîte aux lettres de l’utilisateur C sur votre serveur de messagerie d’origine.
        
    5. À partir d’un compte extérieur ou du compte de messagerie d’un employé sur l’autre système de courrier, vérifiez que le transfert est correctement configuré sur l’autre système de messagerie. Par exemple, à partir du compte de serveur origninal de l’utilisateur C ou d’un compte Hotmail, envoyez un courrier électronique à l’utilisateur et vérifiez qu’il arrive dans la boîte aux lettres Office 365 de l’utilisateur A.
        
9. Déplacer le contenu de la boîte aux lettres
    
    1. Étant donné que deux utilisateurs seulement peuvent être déplacés, et comme l’utilisateur A et l’utilisateur B utilisent tous deux Outlook, le message peut être déplacé en ouvrant l’ancien. PST dans le nouveau profil Outlook et en copiant les messages, les éléments de calendrier, les contacts, etc., comme indiqué dans importer des éléments Outlook à partir d’un fichier de données Outlook (. pst). Une fois organisés aux emplacements appropriés dans la boîte aux lettres Office 365, les éléments sont accessibles à partir de n’importe quel appareil, où qu’ils soient.
        
    2. Lorsque d’autres boîtes aux lettres sont impliquées, ou si les employés n’utilisent pas encore Outlook, vous pouvez utiliser les outils de migration disponibles dans le centre d’administration Exchange. Pour commencer, accédez au centre d’administration Exchange et suivez les instructions de la migration du courrier électronique à partir d’un serveur IMAP vers des boîtes aux lettres Exchange Online.
    
