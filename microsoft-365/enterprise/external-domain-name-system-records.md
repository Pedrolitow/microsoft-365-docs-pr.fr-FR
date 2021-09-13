---
title: Enregistrements DNS externes pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: Liste de références des enregistrements système de nom de domaine externe à utiliser lorsque vous planifiez d’un déploiement Office 365.
ms.openlocfilehash: e54a25aef956784fd74ad65dc54357ea3db0f57c
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59207596"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Enregistrements DNS externes pour Office 365

![Domain.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**Vous voulez afficher une liste personnalisée des enregistrements DNS pour votre organisation Office 365 ?** Vous pouvez [trouver ici les informations nécessaires pour créer des enregistrements DNS Office 365](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) pour votre domaine dans Office 365.  

**Avez besoin d’aide détaillée pour ajouter ces enregistrements  sur le DNS de l’hébergeur de votre domaine, tel que GoDaddy ou eNom ?** [Vous trouverez des liens vers des instructions détaillées pour plusieurs hôtes DNS](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). 

**Vous souhaitez utiliser la liste de référence pour votre  déploiement personnalisé ?** La liste ci-dessous peut être utilisée comme référence pour votre déploiement Office 365 personnalisé. Vous devrez sélectionner les enregistrements qui s’appliquent à votre organisation et renseigner les valeurs appropriées. 

**Retournez sur**[ planification réseau et optimisation des performances pour Office 365](./network-planning-and-performance.md).

Les enregistrements SPF et MX sont souvent les plus difficiles à comprendre. Nous avons mis à jour les instructions concernant les enregistrements SPF à la fin de cet article. Il est important de ne pas oublier que _vous ne pouvez avoir qu’un seul enregistrement SPF pour votre domaine_. Vous pouvez avoir plusieurs enregistrements MX ; toutefois, c’est souvent ce qui entraîne des problèmes de remise de messages. L’utilisation d’un enregistrement MX unique qui dirige le courrier électronique vers un seul système de messagerie supprime un grand nombre de ces problèmes potentiels.
  
Les sections ci-dessous sont organisées par service dans Office 365. Pour afficher une liste personnalisée des enregistrements DNS Office 365 pour votre domaine, connectez-vous à Office 365 pour [recueillir les informations nécessaires pour créer des enregistrements DNS Office 365](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Enregistrements DNS externes requis pour Office 365 (services principaux) :
<a name="BKMK_ReqdCore"> </a>

Chaque client Office 365 doit ajouter deux enregistrements à son serveur DNS externe. Le premier enregistrement CNAME garantit que Office 365 peut diriger les stations de travail vers la plateforme d’identité appropriée. Le second enregistrement requis est un enregistrement qui sert à prouver que vous possédez votre nom de domaine.
  
|**Enregistrement DNS** <br/> |**Objectif** <br/> |**Valeur à utiliser** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Suite)** <br/> |Utilisé par Office 365 pour l'authentification directe auprès de la plateforme d'identité correcte.[Plus d’informations](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> **Remarque :** Cette CNAME s’applique uniquement à Office 365 géré par 21Vianet. [Pour plus d’informations](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet)  |**Alias :** msoID  <br/> **Cible :** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(Vérification du domaine)** <br/> |Utilisées par Office 365 uniquement ce vous êtes le propriétaire vérifier votre domaine. Il n’affecte aucun autre élément.  <br/> |**Hôte :** @ (ou de certains fournisseurs d’hébergement DNS, votre nom de domaine)  <br/> **Valeur TXT :** _une chaîne de texte fournie par_ Office 365  <br/> L’Assistant de **configuration de domaine** Office 365 fournit les valeurs à utiliser pour créer cet enregistrement.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Enregistrements DNS externes requis pour la messagerie électronique dans Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Emailing dans Office 365 nécessite plusieurs enregistrements. Les trois principaux que les clients doivent utiliser sont les enregistrements de découverte automatique, MX et SPF.
  
- **L’enregistrement de découverte automatique** permet aux ordinateurs clients de rechercher automatiquement Exchange et de configurer correctement le client.

- **L’enregistrement MX** indique aux autres systèmes de messagerie où envoyer le courrier électronique pour votre domaine. **Lorsque vous transférez votre courrier électronique vers Office 365, la mise à jour de l’enregistrement MX de votre domaine permettra aux messages envoyés à ce domaine d’arriver dans Office 365.**  
Voulez-vous simplement faire passer quelques adresses de messagerie dans Office 365 ? Vous pouvez [piloter Office 365 avec un petit nombre d’adresses e-mail sur votre domaine personnalisé](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **L’enregistrement TXT pour SPF** est utilisé par les systèmes de messagerie du destinataire pour valider que vous approuvez le serveur d’envoi de votre message. Cela permet d’éviter les problèmes tels que l’usurpation d’identité et le hameçonnage de messagerie. Voir les [enregistrements DNS externes requis pour SPF](external-domain-name-system-records.md#BKMK_SPFrecords) dans cet article d’aide pour comprendre ce que vous incluez dans votre enregistrement.

Les clients email qui utilisent la fédération Exchange auront un enregistrement CNAME et TXT supplémentaire en bas de tableau.
  
|**Enregistrement DNS** <br/> |**Objectif** <br/> |**Valeur à utiliser** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Exchange Online)** <br/> |Aide les clients Outlook à se connecter facilement au service Exchange Online en utilisant le service de découverte automatique. La découverte automatique trouve automatiquement l’hôte Exchange Server approprié et configure Outlook pour les utilisateurs.  <br/> |**Alias :** autodiscover  <br/> **Cible :** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Envoie le courrier entrant pour votre domaine vers le service Exchange Online dans Office 365.  <br/> [!NOTE] Une fois le courrier électronique envoyé vers Exchange Online, vous devez supprimer les enregistrements MX qui pointent vers votre ancien système.   |**Domaine :** par exemple, contoso.com  <br/> **Serveur de courrier cible :**\<MX token\>.mail.protection.outlook.com  <br/> **Préférence/priorité :** Inférieur à d’autres enregistrements MX (cela garantit que le courrier est remis à Exchange Online) : par exemple, 1 ou « faible »  <br/>  Trouvez votre \<MX token\> en procédant comme suit :  <br/>  Connectez-vous à Office 365, accédez à administrateur Office 365 \> domaines.  <br/>  Dans la colonne Action pour votre domaine, sélectionnez Corriger les problèmes.  <br/>  Dans la section Enregistrements MX, sélectionnez Que faut-il corriger ?  <br/>  Suivez les instructions de cette page pour mettre à jour votre enregistrement MX.  <br/> [Quelle est la priorité MX ?](../admin/setup/domains-faq.yml) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Aide à empêcher d'autres personnes d'utiliser votre domaine pour envoyer des messages indésirables ou malveillants. Les enregistrements SPF fonctionnent en identifiant les serveurs autorisés à envoyer des messages à partir de votre domaine.  <br/> |[Enregistrements DNS externes requis pour SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Fédération Exchange)** <br/> |Utilisé pour la fédération Exchange en cas de déploiement hybride.  <br/> |**Enregistrement TXT 1 :** par exemple, contoso.com et texte associé personnalisé, texte de hachage de vérification de domaine associé généré de façon personnalisée (par exemple, Y96nu89138789315669824)  <br/> **Enregistrement TXT 2 :** par exemple, exchangedelegation.contoso.com et le texte de hachage de vérification de domaine associé personnalisé (par exemple, Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Fédération Exchange)** <br/> |Aide les clients Outlook à se connecter facilement au service Exchange Online en utilisant le service de découverte automatique quand votre société utilise la fédération Exchange. La découverte automatique trouve automatiquement l’hôte Exchange Server approprié et configure Outlook pour vos utilisateurs.  <br/> |**Alias :** par exemple, Autodiscover.service.contoso.com  <br/> **Cible :** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Enregistrements DNS externes requis pour Skype Entreprise Online
<a name="BKMK_ReqdCore"> </a>

Il existe des étapes spécifiques à suivre lorsque vous utilisez des [plages d’adresses IP et URL Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) pour vous assurer que votre réseau est correctement configuré.

> [!NOTE]
> Ces enregistrements DNS s’appliquent également à Teams, en particulier dans un scénario hybride Teams et Skype Entreprise, lorsque certains problèmes de fédération peuvent se produire.
  
|**Enregistrement DNS** <br/> |**Objectif** <br/> |**Valeur à utiliser** <br/> |
|----------|-----------|------------|
|**SRV** <br/> **(Skype Entreprise Online)** <br/> |Permet à votre domaine Office 365 de partager des fonctionnalités (MI) messagerie instantanée avec des clients externes en activant la fédération SIP. En savoir plus sur [URL Office 365 et plages d’adresses](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Service** : sipfederationtls  <br/> **Protocole :** TCP  <br/> **Priorité :** 100  <br/> **Poids :** 1  <br/> **Port :** 5061  <br/> **Cible** : sipfed.online.lync.com  <br/> **Remarque :** si le pare-feu ou le serveur proxy bloque les recherches SRV sur un DNS externe, vous devez ajouter cet enregistrement à l'enregistrement DNS interne.   |
|**SRV** <br/> **(Skype Entreprise Online)** <br/> |Utilisé par Skype Entreprise Online pour coordonner le flux d’informations entre des clients Lync.  <br/> |**Service :** sip  <br/> **Protocole :** TLS  <br/> **Priorité :** 100  <br/> **Poids :** 1  <br/> **Port :** 443  <br/> **Cible :** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype Entreprise Online)** <br/> |Utilisé par le client Lync pour trouver le service Skype Entreprise Online et se connecter.  <br/> |**Alias :** sip  <br/> **Cible :** sipdir.online.lync.com  <br/> Pour plus d’informations, voir [URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype Entreprise Online)** <br/> |Utilisé par le client Lync mobile pour trouver le service Skype Entreprise Online et se connecter.  <br/> |**Alias :** lyncdiscover  <br/> **Cible :** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Enregistrements DNS externes requis pour authentification unique Office 365
<a name="BKMK_ReqdCore"> </a>

|**Enregistrement DNS** <br/> |**Objectif** <br/> |**Valeur à utiliser** <br/> |
|----------|-----------|------------|
|**Hôte (A)** <br/> |Utilisé pour l’authentification unique (SSO). Il fournit le point de terminaison pour que vos utilisateurs hors site (et vos utilisateurs locaux, si vous le souhaitez) puissent se connecter à vos serveurs proxy de fédération Active Directory Federation Services (AD FS) ou une adresse IP virtuelle (VIP) avec équilibrage de charge.  <br/> |**Cible :** par exemple, sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Enregistrements DNS externes requis pour SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
>  SPF est conçu pour éviter l’usurpation mais il existe des techniques d’usurpation contre lesquelles SPF ne peut pas vous protéger. Afin de vous protéger contre ces techniques, une fois que vous avez configuré SPF, vous devez également configurer DKIM et DMARC pour Office 365. Consultez [Use DKIM to validate outbound email sent from your domain in Office 365](../security/office-365-security/use-dkim-to-validate-outbound-email.md) pour commencer. Ensuite, consultez la rubrique [Use DMARC to validate email in Office 365](../security/office-365-security/use-dmarc-to-validate-email.md).
  
Les enregistrements SPF texte contribuent à empêcher d’autres personnes d’utiliser votre domaine pour envoyer des messages indésirables ou malveillants. Les enregistrements SPF (Sender Policy Framework) fonctionnent en identifiant les serveurs autorisés à envoyer des messages à partir de votre domaine.
  
Vous ne pouvez avoir qu’un seul enregistrement SPF (autrement dit, un enregistrement TXT qui définit le SPF) associé à votre domaine. Cet enregistrement unique peut avoir quelques inclusions différentes, mais les recherches DNS qui en résultent ne peuvent pas être supérieures à 10 (Cela permet d’éviter les attaques par déni de service). Reportez-vous au tableau et autres exemples ci-dessous pour créer ou mettre à jour les valeurs d’enregistrement SPF appropriées pour votre environnement.
  
### <a name="structure-of-an-spf-record"></a>Structure d'un enregistrement SPF

Tous les enregistrements SPF contiennent trois parties : la déclaration qu’il s’agit d’un enregistrement SPF, les domaines et les adresses IP qui doivent envoyer le courrier électronique, et une règle de mise en œuvre. Vous devez disposer des trois pour avoir un enregistrement SPF valide. Voici un exemple d’enregistrement SPF courant pour Office 365 lorsque vous utilisez les emails Exchange Online :
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Un système de messagerie recevant un message électronique à partir de votre domaine examine l’enregistrement SPF, et si le serveur de messagerie qui a envoyé le message était un serveur Office 365, le message est accepté. Si le serveur qui a envoyé le message était votre ancien système de messagerie ou un système malveillant sur Internet, par exemple, la vérification SPF peut échouer et le message ne sera pas remis. Ces types de vérification permettent d’empêcher l’usurpation d’identité et le hameçonnage.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Choisir la structure d’enregistrement SPF dont vous avez besoin

Pour les scénarios où vous n’utilisez pas seulement les emails Exchange Online pour Office 365 (par exemple, lorsque vous utilisez le courrier électronique en provenance de SharePoint Online), utilisez le tableau suivant pour déterminer les éléments à inclure dans la valeur de l’enregistrement.
  
> [!NOTE]
> Si votre scénario est complexe et inclut, par exemple, les serveurs de messagerie edge pour la gestion du trafic de messagerie à travers votre pare-feu, vous devez configurer un enregistrement SPF plus détaillé. Découvrez comment : [configurer les enregistrements SPF dans Office 365 pour éviter l’usurpation](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md). Vous pouvez également découvrir beaucoup plus sur le fonctionnement du SPF avec Office 365 en lisant [comment Office 365 utilise l’expéditeur SPF (Sender Policy Framework) pour éviter l’usurpation](../security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing.md).
  
| Nombre|Si vous utilisez...  <br/> |Objectif  <br/> |Ajoutez ceci  <br/> |
|:-----|:-----|:-----|:-----|
|1  <br/> |Tous les systèmes de courrier (obligatoire)  <br/> |Tous les enregistrements SPF commencent par cette valeur  <br/> |v=spf1  <br/> |
|2  <br/> |Exchange Online (courant)  <br/> |Utilisez uniquement avec Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3  <br/> |Un système de messagerie tiers (moins courant)  <br/> ||Incluez :\<email system like mail.contoso.com\>  <br/> |
|4  <br/> |Le système de messagerie du site (moins courant)  <br/> |À utiliser si vous avez recours à Exchange Online Protection ou Exchange Online et un autre système de messagerie  <br/> |IP4 : \<0.0.0.0\>  <br/> ip6 : \< : : \>  <br/> Incluez : \<mail.contoso.com\>  <br/> La valeur entre crochets (\<\>) doit être les autres systèmes de messagerie chargés d’envoyer les emails pour votre domaine.  <br/> |
|5  <br/> |Tous les systèmes de courrier (obligatoire)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Exemple : Ajout à un enregistrement SPF existant
<a name="bkmk_addtospf"> </a>

Si vous avez déjà un enregistrement SPF, vous devez ajouter ou mettre à jour des valeurs pour Office 365. Par exemple, supposons que votre enregistrement SPF existant pour contoso.com est le suivant :
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Maintenant vous mettez à jour votre enregistrement SPF pour Office 365. Vous modifiez votre enregistrement actuel pour avoir un enregistrement SPF qui inclut les valeurs dont vous avez besoin. Pour Office 365, il s’agit de « sharepointonline.com ».
  
Correct :
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Incorrect :
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Autres exemples de valeurs SPF standard
<a name="bkmk_addtospf"> </a>

Si vous utilisez la suite complète Office 365 et MailChimp pour envoyer du courrier électronique marketing en votre nom, votre enregistrement SPF sur contoso.com peut ressembler au suivant, lequel utilise les lignes 1, 3 et 5 du tableau ci-dessus. N’oubliez pas que les lignes 1 et 5 sont obligatoires. « sharepointonline.com » inclut Exchange (Outlook) et la messagerie mail SharePoint.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Sinon, si vous avez une configuration Exchange hybride où le courrier électronique a été envoyé à la fois à partir d’Office 365 et du système de messagerie du site, votre enregistrement SPF sur contoso.com peut se présenter comme ceci :
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

Voici quelques exemples courants qui peuvent vous aider à adapter votre enregistrement SPF existant lorsque vous ajoutez votre domaine à Office 365 pour le courrier électronique. Si votre scénario est complexe et inclut, par exemple, les serveurs de messagerie edge pour la gestion du trafic de messagerie à travers votre pare-feu, vous devez configurer un enregistrement SPF plus détaillé. Découvrez comment : [configurer les enregistrements SPF dans Office 365 pour éviter l’usurpation](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365edns]()
