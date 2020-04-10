---
title: Créer des enregistrements DNS auprès d'Hostgator pour Office 365
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
- Adm_NonTOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5f0c840e-4140-4571-88ed-cf235ff142d6
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur Hostgator pour Office 365.
ms.openlocfilehash: a5a41e5c1eba9d99d1927192472da7746277dd38
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43211714"
---
# <a name="create-dns-records-at-hostgator-for-office-365"></a>Créer des enregistrements DNS auprès d'Hostgator pour Office 365

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Hostgator est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
> [!IMPORTANT]
> Vous devez effectuer la première procedurebelow, [pointez votre domaine sur votre compte d’hébergement](#point-your-domain-to-your-hosting-account), avant d’ajouter des enregistrements DNS à l’aide de l’une des autres procédures décrites dans cet article. 

Une fois ces modifications effectuées sur Hostgator, votre domaine est configuré pour utiliser les services Office 365.
  
Pour en savoir plus sur l'hébergement web et le DNS pour les sites web avec Office 365, voir [Utiliser un site web public avec Office 365](https://support.office.com/article/choose-a-public-website-3325d50e-d131-403c-a278-7f3296fe33a9).
  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d'autres problèmes suite à l'ajout des enregistrements DNS, consultez [Rechercher et corriger les problèmes suite à l'ajout de votre domaine ou des enregistrements DNS dans Office 365](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="point-your-domain-to-your-hosting-account"></a>Faire pointer votre domaine vers votre compte d'hébergement
<a name="BKMK_PointDomain"> </a>

> [!IMPORTANT]
> Vous devez effectuer cette procédure avant d'effectuer les autres procédures décrites dans cet article. 
  
Suivez ces étapes pour associer votre domaine et vos comptes d'hébergement.
  
1. Pour commencer, accédez à la page de gestion de vos domaines sur le site Hostgator en utilisant [ce lien](https://portal.hostgator.com/). Vous serez invité à vous connecter.
    
2. Sélectionnez **domaines** sur la gauche.
  
3. Sur la page **gérer les domaines** , sélectionnez le domaine que vous souhaitez mettre à jour. 
  
4. Dans le menu contextuel situé à gauche, sélectionnez **serveurs de noms**.
  
5. Sur la page **serveurs de noms** de votre domaine, dans la liste déroulante **pointer automatiquement ce domaine sur mon compte d’hébergement** , sélectionnez le compte d’hébergement associé à votre domaine. 
  
6. Sélectionnez **enregistrer les serveurs de noms**.
    
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page cPanel sur Hostgator. Avant toute chose, vous serez invité à vous connecter.
    
    (Une adresse cPanel unique est affectée à chaque compte hébergé sur Hostgator. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. Le courrier électronique d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page d' **hébergement** .)
    
    > [!IMPORTANT]
    > Pour associer une adresse cPanel à votre domaine, vous devez héberger un compte auprès de Hostgator. Pour prendre en main Office 365, vous pouvez acheter un compte d'hébergement auprès de Hostgator ou [redéléguer vos serveurs de noms afin qu'ils pointent vers Office 365](change-nameservers-at-hostgator.md). 
  
2. Sur la page **panneau de configuration** , dans la zone **domaines** , sélectionnez **Advanced zone Editor**.
    
3. Sur la page **éditeur de zone avancé** , dans la zone **Ajouter un enregistrement** , dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Name (Nom)** <br/> |**TTL (Durée de vie)** <br/> |**Type** <br/> |**TXT Data (Données TXT)** <br/> |
    |Utilisez votre *domain_name*. (for example, fourthcoffee.com.)  <br/> **This value MUST end with a period (.)** <br/> |0,1  <br/> |TXT  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
4. Sélectionnez **Ajouter un enregistrement**.
    
5. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Office 365 et demandez à Office 365 de rechercher l’enregistrement.
  
Lorsqu’Office 365 trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d'autres problèmes suite à l'ajout des enregistrements DNS, consultez [Rechercher et corriger les problèmes suite à l'ajout de votre domaine ou des enregistrements DNS dans Office 365](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365
<a name="BKMK_add_MX"> </a>

> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
1. To get started, go to your cPanel page at Hostgator. You'll be prompted to log in first.
    
    (Each hosted account at Hostgator is assigned a unique cPanel address. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. Le courrier électronique d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page d' **hébergement** .)
    
    > [!IMPORTANT]
    > Pour associer une adresse cPanel à votre domaine, vous devez héberger un compte auprès de Hostgator. Pour prendre en main Office 365, vous pouvez acheter un compte d'hébergement auprès de Hostgator ou [redéléguer vos serveurs de noms afin qu'ils pointent vers Office 365](change-nameservers-at-hostgator.md). 
  
2. Sur la page **panneau de configuration** , dans la zone **courrier électronique** , sélectionnez **entrée MX**.
    
 
3. Dans la zone **Email Routing (Routage des courriers électroniques)**, sélectionnez **Remote Mail Exchanger (Serveur de courrier distant)**.

4. Sélectionnez **modifier**.
  
5. Dans la zone **Ajouter un nouvel enregistrement** , dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    |**Priority (Priorité)**|**Destination (Destination)**|
    |:-----|:-----|
    |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenez votre \< *clé* \> de domaine à partir de votre compte Office 365.    [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
  
6. Sélectionnez **Ajouter un nouvel enregistrement**.
   
 
7. S’il existe d’autres enregistrements MX dans la section **MX Records (enregistrements MX** ), supprimez chacun d’eux. 

    
## <a name="add-the-six-cname-records-that-are-required-for-office-365"></a>Ajouter les 6 enregistrements CNAME requis pour Office 365
<a name="BKMK_add_CNAME"> </a>

> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
1. To get started, go to your cPanel page at Hostgator. You'll be prompted to log in first.
    
    (Each hosted account at Hostgator is assigned a unique cPanel address. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. Le courrier électronique d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page d' **hébergement** .)
    
    > [!IMPORTANT]
    > Pour associer une adresse cPanel à votre domaine, vous devez héberger un compte auprès de Hostgator. Pour prendre en main Office 365, vous pouvez acheter un compte d'hébergement auprès de Hostgator ou [redéléguer vos serveurs de noms afin qu'ils pointent vers Office 365](change-nameservers-at-hostgator.md). 
  
2. Sur la page **panneau de configuration** , dans la zone **domaines** , sélectionnez **Advanced zone Editor**.
    
3. Ajoutez le premier des six enregistrements CNAME.
    
    Sur la page **éditeur de zone avancé** , dans la zone **Ajouter un enregistrement** , dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |**Name (Nom)**|**TTL (Durée de vie)**|**Type (Type)**|**CNAME**|
    |:-----|:-----|:-----|:-----|
    |autodiscover. *domain_name*. (par exemple, autodiscover.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |autodiscover.outlook.com  <br/> |
    |sip. *domain_name*. (par exemple, sip.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover. *domain_name*. (par exemple, lyncdiscover.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |webdir.online.lync.com  <br/> |
    |enterpriseregistration. *domain_name*. (par exemple, enterpriseregistration.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |enterpriseregistration.windows.net  <br/> |
    |enterpriseenrollment. *domain_name*. (par exemple, enterpriseregistration.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

  
4. Sélectionnez **Ajouter un enregistrement**.

5. Ajoutez successivement les 5 autres enregistrements CNAME.
    
    Dans la section **Add a record (ajouter un enregistrement** ), créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Add record (ajouter un enregistrement** ) pour valider cet enregistrement. 
    
    Répétez cette procédure jusqu'à avoir créé les 6 enregistrements CNAME.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. If you already have an SPF record for your domain, don't create a new one for Office 365. Ajoutez plutôt les valeurs Office 365 requises à l'enregistrement actuel de manière à n'avoir qu'un seul enregistrement SPF qui inclut les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Office 365](https://support.office.com/article/c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0#bkmk_spfrecords). To validate your SPF record, you can use one of these [SPF validation tools](../setup/domains-faq.md). 
  
> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
1. To get started, go to your cPanel page at Hostgator. You'll be prompted to log in first.
    
    (Each hosted account at Hostgator is assigned a unique cPanel address. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. Le courrier électronique d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page d' **hébergement** .)
    
    > [!IMPORTANT]
    > Pour associer une adresse cPanel à votre domaine, vous devez héberger un compte auprès de Hostgator. Pour prendre en main Office 365, vous pouvez acheter un compte d'hébergement auprès de Hostgator ou [redéléguer vos serveurs de noms afin qu'ils pointent vers Office 365](change-nameservers-at-hostgator.md). 
  
2. Sur la page **panneau de configuration** , dans la zone **domaines** , sélectionnez **Advanced zone Editor**.
    
3. On the **Advanced DNS Zone Editor** page, in the **Add a Record** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |**Name (Nom)**|**TTL (Durée de vie)**|**Type (Type)**|**TXT Data (Données TXT)**|
    |:-----|:-----|:-----|:-----|
    |Utilisez votre *domain_name*. (for example, fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |TXT  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
  
4. Sélectionnez **Ajouter un enregistrement**.
    
## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>Ajoutez les 2 enregistrements SRV requis pour Office 365
<a name="BKMK_add_SRV"> </a>

> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
1. To get started, go to your cPanel page at Hostgator. You'll be prompted to log in first.
    
    (Each hosted account at Hostgator is assigned a unique cPanel address. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. Le courrier électronique d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page d' **hébergement** .)
    
    > [!IMPORTANT]
    > Pour associer une adresse cPanel à votre domaine, vous devez héberger un compte auprès de Hostgator. Pour prendre en main Office 365, vous pouvez acheter un compte d'hébergement auprès de Hostgator ou [redéléguer vos serveurs de noms afin qu'ils pointent vers Office 365](change-nameservers-at-hostgator.md). 
  
2. Sur la page **panneau de configuration** , dans la zone **domaines** , sélectionnez **Advanced zone Editor**.

    
3. Ajoutez le premier des deux enregistrements SRV.
    
    Sur la page **Advanced DNS Zone Editor (Éditeur de zone DNS avancé)**, dans la zone **Add a Record (Ajouter un enregistrement)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |**Name (Nom)**|**TTL (Durée de vie)**|**Type**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip. _tls. *domain_name*. (par exemple, _sip. _tls. fourthcoffee. com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |SRV  <br/> |100  <br/> |0,1  <br/> |443  <br/> |sipdir.online.lync.com  <br/> |
    |_sipfederationtls. _tcp. *domain_name*. (par exemple, _sipfederationtls. _tcp. fourthcoffee. com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |SRV  <br/> |100  <br/> |0,1  <br/> |5061  <br/> |sipfed.online.lync.com  <br/> |
   

4. Sélectionnez **Ajouter un enregistrement**.

  
5. Ajoutez l'autre enregistrement SRV.
    
    Dans la section **Add a record (ajouter un enregistrement** ), créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Add record (ajouter un enregistrement** ) pour valider cet enregistrement. 
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d'autres problèmes suite à l'ajout des enregistrements DNS, consultez [Rechercher et corriger les problèmes suite à l'ajout de votre domaine ou des enregistrements DNS dans Office 365](../get-help-with-domains/find-and-fix-issues.md). 
