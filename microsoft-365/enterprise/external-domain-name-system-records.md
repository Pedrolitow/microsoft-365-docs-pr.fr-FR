---
title: Enregistrements DNS externes pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/10/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
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
ms.openlocfilehash: 47a8bfe283041ad0350cfdf1db0b9e97bfa18b60
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824825"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Enregistrements DNS externes pour Office 365

![Domain.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**Vous voulez afficher une liste personnalisée des enregistrements DNS pour votre organisation Office 365 ?** Vous pouvez [trouver ici les informations nécessaires pour créer des enregistrements DNS Office 365](../admin/get-help-with-domains/information-for-dns-records.md) pour votre domaine dans Office 365.  

**Avez besoin d’aide détaillée pour ajouter ces enregistrements  sur le DNS de l’hébergeur de votre domaine, tel que GoDaddy ou eNom ?** [Vous trouverez des liens vers des instructions détaillées pour plusieurs hôtes DNS](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). 

**Vous souhaitez utiliser la liste de référence pour votre  déploiement personnalisé ?** La liste ci-dessous peut être utilisée comme référence pour votre déploiement Office 365 personnalisé. Vous devrez sélectionner les enregistrements qui s’appliquent à votre organisation et renseigner les valeurs appropriées. 

**Retournez sur**[ planification réseau et optimisation des performances pour Office 365](./network-planning-and-performance.md).

Les enregistrements SPF et MX sont souvent les plus difficiles à comprendre. Nous avons mis à jour les instructions concernant les enregistrements SPF à la fin de cet article. Il est important de ne pas oublier que _vous ne pouvez avoir qu’un seul enregistrement SPF pour votre domaine_. Vous pouvez avoir plusieurs enregistrements MX ; toutefois, c’est souvent ce qui entraîne des problèmes de remise de messages. L’utilisation d’un enregistrement MX unique qui dirige le courrier électronique vers un seul système de messagerie supprime un grand nombre de ces problèmes potentiels.

Les sections ci-dessous sont organisées par service dans Office 365. Pour afficher une liste personnalisée des enregistrements DNS Office 365 pour votre domaine, connectez-vous à Office 365 pour [recueillir les informations nécessaires pour créer des enregistrements DNS Office 365](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).

## <a name="external-dns-records-required-for-office-365-core-services"></a>Enregistrements DNS externes requis pour Office 365 (services principaux) :
<a name="BKMK_ReqdCore"> </a>

L’enregistrement TXT est nécessaire pour prouver que vous êtes propriétaire du domaine et qu’il est requis pour tous les clients.

L’enregistrement CNAME est uniquement requis pour les clients utilisant [Office 365 géré par 21Vianet](/microsoft-365/admin/services-in-china/services-in-china). Il garantit qu'Office 365 peut diriger les postes de travail pour s'authentifier avec la plateforme d'identité appropriée.

|Enregistrement DNS|Objectif|Valeur à utiliser|S’applique à|
|---|---|---|---|
|**TXT** <br/> **(Vérification du domaine)**|Utilisées par Office 365 uniquement ce vous êtes le propriétaire vérifier votre domaine. Il n’affecte aucun autre élément.|**Hôte :** @ (ou de certains fournisseurs d’hébergement DNS, votre nom de domaine) <br/> **Valeur TXT :** _une chaîne de texte fournie par_ Office 365 <br/> L’Assistant de **configuration de domaine** Office 365 fournit les valeurs à utiliser pour créer cet enregistrement.|Tous les clients|
|**CNAME** <br/> **(Suite)**|Utilisé par Office 365 pour l'authentification directe auprès de la plateforme d'identité correcte.[Plus d’informations](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> **Remarque** cette CNAME s’applique uniquement à Office 365 géré par 21Vianet. S’il est présent et que votre Office 365 n’est pas géré par 21Vianet, les utilisateurs de votre domaine personnalisé obtiennent une erreur « *un domaine personnalisé* n’est pas dans notre système » et ne peuvent pas activer leur licence Office 365. [Plus d’informations](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet) |**Alias :** msoID <br/> **Cible :** clientconfig.partner.microsoftonline-p.net.cn| Clients 21Vianet uniquement|

## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Enregistrements DNS externes requis pour la messagerie électronique dans Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Emailing dans Office 365 nécessite plusieurs enregistrements. Les trois principaux que les clients doivent utiliser sont les enregistrements de découverte automatique, MX et SPF.

- **L’enregistrement de découverte automatique** permet aux ordinateurs clients de rechercher automatiquement Exchange et de configurer correctement le client.

- **L’enregistrement MX** indique à d’autres systèmes de messagerie où envoyer des messages électroniques pour votre domaine. **Remarque :** Lorsque vous remplacez votre messagerie vers Office 365, en mettant à jour l’enregistrement MX de votre domaine, TOUS les messages envoyés à ce domaine commencent à arriver dans Office 365. Vous voulez simplement basculer quelques adresses e-mail vers Office 365 ? Vous pouvez [Piloter Office 365 avec quelques adresses e-mail sur votre domaine personnalisé](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **L’enregistrement TXT pour SPF** est utilisé par les systèmes de messagerie du destinataire pour valider que vous approuvez le serveur d’envoi de votre message. Cela permet d’éviter les problèmes tels que l’usurpation d’identité et le hameçonnage de messagerie. Voir les [enregistrements DNS externes requis pour SPF](external-domain-name-system-records.md#BKMK_SPFrecords) dans cet article d’aide pour comprendre ce que vous incluez dans votre enregistrement.

Les clients email qui utilisent la fédération Exchange auront un enregistrement CNAME et TXT supplémentaire en bas de tableau.

|Enregistrement DNS|Objectif|Valeur à utiliser|
|---|---|---|
|**CNAME** <br/> **(Exchange Online)**|Aide les clients Outlook à se connecter facilement au service Exchange Online en utilisant le service de découverte automatique. La découverte automatique trouve automatiquement l’hôte Exchange Server approprié et configure Outlook pour les utilisateurs.|**Alias :** autodiscover <br/> **Cible :** autodiscover.outlook.com|
|**MX** <br/> **(Exchange Online)**|Envoie le courrier entrant pour votre domaine vers le service Exchange Online dans Office 365. <br/> **Remarque :** une fois le courrier électronique envoyé vers Exchange Online, vous devez supprimer les enregistrements MX qui pointent vers votre ancien système. |**Domaine :** par exemple, contoso.com <br/> **Serveur de courrier cible :**\<MX token\>.mail.protection.outlook.com <br/> **Valeur de temps de vie (TTL) :** 3600 <br/> **Préférence/priorité :** Inférieur à d’autres enregistrements MX (cela garantit que le courrier est remis à Exchange Online) : par exemple, 1 ou « faible » <br/> Trouvez votre \<MX token\> en procédant comme suit : <br/> Connectez-vous à Office 365, accédez à administrateur Office 365 \> domaines. <br/> Dans la colonne Action pour votre domaine, sélectionnez Corriger les problèmes. <br/> Dans la section Enregistrements MX, sélectionnez Que faut-il corriger ? <br/> Suivez les instructions de cette page pour mettre à jour votre enregistrement MX. <br/> [Quelle est la priorité MX ?](../admin/setup/domains-faq.yml)|
|**SPF (TXT)** <br/> **(Exchange Online)**|Aide à empêcher d'autres personnes d'utiliser votre domaine pour envoyer des messages indésirables ou malveillants. Les enregistrements SPF fonctionnent en identifiant les serveurs autorisés à envoyer des messages à partir de votre domaine.|[Enregistrements DNS externes requis pour SPF](external-domain-name-system-records.md#BKMK_SPFrecords)|
|**TXT** <br/> **(Fédération Exchange)**|Utilisé pour la fédération Exchange en cas de déploiement hybride.|**Enregistrement TXT 1 :** par exemple, contoso.com et texte associé personnalisé, texte de hachage de vérification de domaine associé généré de façon personnalisée (par exemple, Y96nu89138789315669824) <br/> **Enregistrement TXT 2 :** par exemple, exchangedelegation.contoso.com et le texte de hachage de vérification de domaine associé personnalisé (par exemple, Y3259071352452626169)|
|**CNAME** <br/> **(Fédération Exchange)**|Aide les clients Outlook à se connecter facilement au service Exchange Online en utilisant le service de découverte automatique quand votre société utilise la fédération Exchange. La découverte automatique trouve automatiquement l’hôte Exchange Server approprié et configure Outlook pour vos utilisateurs.|**Alias :** par exemple, Autodiscover.service.contoso.com <br/> **Cible :** autodiscover.outlook.com|

## <a name="external-dns-records-required-for-skype-for-business-online"></a>Enregistrements DNS externes requis pour Skype Entreprise Online
<a name="BKMK_ReqdCore"> </a>

Il existe des étapes spécifiques à suivre lorsque vous utilisez [des URL Office 365 et des plages d’adresses IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) pour vous assurer que votre réseau est correctement configuré.

> [!NOTE]
> Ces enregistrements DNS s’appliquent également à Teams, en particulier dans un scénario hybride Teams et Skype Entreprise, lorsque certains problèmes de fédération peuvent se produire.

|Enregistrement DNS|Objectif|Valeur à utiliser|
|---|---|---|
|**SRV** <br/> **(Skype Entreprise Online)**|Permet à votre domaine Office 365 de partager des fonctionnalités (MI) messagerie instantanée avec des clients externes en activant la fédération SIP. En savoir plus sur [URL Office 365 et plages d’adresses](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  |**Service** : sipfederationtls <br/> **Protocole :** TCP <br/> **Priorité :** 100 <br/> **Poids :** 1 <br/> **Port :** 5061 <br/> **Cible** : sipfed.online.lync.com <br/> **Remarque :** si le pare-feu ou le serveur proxy bloque les recherches SRV sur un DNS externe, vous devez ajouter cet enregistrement à l'enregistrement DNS interne. |
|**SRV** <br/> **(Skype Entreprise Online)**|Utilisé par Skype Entreprise Online pour coordonner le flux d’informations entre des clients Lync.|**Service :** sip <br/> **Protocole :** TLS <br/> **Priorité :** 100 <br/> **Poids :** 1 <br/> **Port :** 443 <br/> **Cible :** sipdir.online.lync.com|
|**CNAME** <br/> **(Skype Entreprise Online)**|Utilisé par le client Lync pour trouver le service Skype Entreprise Online et se connecter.|**Alias :** sip <br/> **Cible :** sipdir.online.lync.com <br/> Pour plus d’informations, voir [URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).|
|**CNAME** <br/> **(Skype Entreprise Online)**|Utilisé par le client Lync mobile pour trouver le service Skype Entreprise Online et se connecter.|**Alias :** lyncdiscover <br/> **Cible :** webdir.online.lync.com|

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Enregistrements DNS externes requis pour authentification unique Office 365
<a name="BKMK_ReqdCore"> </a>

|Enregistrement DNS|Objectif|Valeur à utiliser|
|---|---|---|
|**Hôte (A)**|Utilisé pour l’authentification unique (SSO). Il fournit le point de terminaison pour que vos utilisateurs hors site (et vos utilisateurs locaux, si vous le souhaitez) puissent se connecter à vos serveurs proxy de fédération Active Directory Federation Services (AD FS) ou une adresse IP virtuelle (VIP) avec équilibrage de charge.|**Cible :** par exemple, sts.contoso.com|

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

|Nombre|Si vous utilisez...|Objectif|Ajoutez ceci|
|---|---|---|---|
|1|Tous les systèmes de courrier (obligatoire)|Tous les enregistrements SPF commencent par cette valeur|v=spf1|
|2|Exchange Online (courant)|Utilisez uniquement avec Exchange Online|include:spf.protection.outlook.com|
|3|Un système de messagerie tiers (moins courant)||Incluez :\<email system like mail.contoso.com\>|
|4|Le système de messagerie du site (moins courant)|À utiliser si vous avez recours à Exchange Online Protection ou Exchange Online et un autre système de messagerie|IP4 : \<0.0.0.0\> <br/> ip6 : \< : : \> <br/> Incluez : \<mail.contoso.com\> <br/> La valeur entre crochets (\<\>) doit être les autres systèmes de messagerie chargés d’envoyer les emails pour votre domaine.|
|5|Tous les systèmes de courrier (obligatoire)||-all|

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

Voici un lien que vous pouvez utiliser pour revenir : <https://aka.ms/o365edns>
