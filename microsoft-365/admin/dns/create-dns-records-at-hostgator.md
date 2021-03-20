---
title: Créer des enregistrements DNS chez Hostgator pour Microsoft
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
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5f0c840e-4140-4571-88ed-cf235ff142d6
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services chez Hostgator pour Microsoft.
ms.openlocfilehash: 790a7d77c9dbab37b87f8e7533515e75d2018e92
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50910197"
---
# <a name="create-dns-records-at-hostgator-for-microsoft"></a>Créer des enregistrements DNS chez Hostgator pour Microsoft

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Hostgator est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
> [!IMPORTANT]
> Vous devez exécuter la première [procédure,](#point-your-domain-to-your-hosting-account)Pointer votre domaine vers votre compte d’hébergement, avant d’ajouter des enregistrements DNS à l’aide de l’une des autres procédures de cet article. 

Une fois que vous avez apporté toutes ces modifications sur Hostgator, votre domaine est installé pour fonctionner avec les services Microsoft.
  

  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="point-your-domain-to-your-hosting-account"></a>Faire pointer votre domaine vers votre compte d'hébergement
<a name="BKMK_PointDomain"> </a>

> [!IMPORTANT]
> Vous devez effectuer cette procédure avant d'effectuer les autres procédures décrites dans cet article. 
  
Suivez ces étapes pour associer votre domaine et vos comptes d'hébergement.
  
1. Pour commencer, accédez à la page de gestion de vos domaines sur le site Hostgator en utilisant [ce lien](https://portal.hostgator.com/). Vous serez invité à vous connecter.
    
2. Sélectionnez **Domaines** sur la gauche.
  
3. Dans la page **Gérer les domaines,** sélectionnez le domaine à mettre à jour. 
  
4. Dans le menu déroulant à gauche, sélectionnez **Serveurs de noms.**
  
5. Dans la page **Serveurs** de noms  de votre domaine, dans la liste de listes de listes des comptes d’hébergement automatiquement, sélectionnez le compte d’hébergement associé à votre domaine. 
  
6. Sélectionnez **Enregistrer les serveurs de noms.**
    
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page cPanel sur Hostgator. Avant toute chose, vous serez invité à vous connecter.
    
    (Une adresse cPanel unique est affectée à chaque compte hébergé sur Hostgator. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. L’e-mail d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page **d’hébergement.)**
    
    > [!IMPORTANT]
    > To have a cPanel associated with your domain, you need a hosting account with Hostgator. Pour commencer à utiliser Microsoft, vous pouvez acheter un compte d’hébergement auprès de Hostgator ou redéléguer vos serveurs de noms pour [qu’ils pointent vers Microsoft.](change-nameservers-at-hostgator.md) 
  
2. Dans la page **Panneau de contrôle,** dans la zone **Domaines,** sélectionnez **Advanced Zone Editor**.
    
3. Dans la page Éditeur de  **zone** avancée, dans la zone Ajouter un enregistrement, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Name** <br/> |**TTL (Durée de vie)** <br/> |**Type (Type)** <br/> |**TXT Data (Données TXT)** <br/> |
    |Utilisez votre  *domain_name*. (for example, fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1  <br/> |TXT  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
4. Sélectionnez **Ajouter un enregistrement**.
    
5. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
<a name="BKMK_add_MX"> </a>

> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
1. Pour commencer, accédez à la page cPanel sur Hostgator. Avant toute chose, vous serez invité à vous connecter.
    
    (Une adresse cPanel unique est affectée à chaque compte hébergé sur Hostgator. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. L’e-mail d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page **d’hébergement.)**
    
    > [!IMPORTANT]
    > To have a cPanel associated with your domain, you need a hosting account with Hostgator. Pour commencer à utiliser Microsoft, vous pouvez acheter un compte d’hébergement auprès de Hostgator ou redéléguer vos serveurs de noms pour [qu’ils pointent vers Microsoft.](change-nameservers-at-hostgator.md) 
  
2. Dans la page **Panneau de contrôle,** dans la zone **Courrier,** sélectionnez **Entrée MX.**
    
 
3. Dans la zone **Email Routing (Routage des courriers électroniques)**, sélectionnez **Remote Mail Exchanger (Serveur de courrier distant)**.

4. Sélectionnez **Modifier**.
  
5. Dans la **zone Ajouter un nouvel** enregistrement, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    |**Priority (Priorité)**|**Destination (Destination)**|
    |:-----|:-----|
    |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenez votre \< *domain-key*  \> à partir de votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
  
6. Sélectionnez **Ajouter un nouvel enregistrement.**
   
 
7. S’il existe d’autres enregistrements MX dans la section **Enregistrements MX,** supprimez chacun d’eux. 

    
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a>Ajouter les six enregistrements CNAME requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
1. Pour commencer, accédez à la page cPanel sur Hostgator. Avant toute chose, vous serez invité à vous connecter.
    
    (Une adresse cPanel unique est affectée à chaque compte hébergé sur Hostgator. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. L’e-mail d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page **d’hébergement.)**
    
    > [!IMPORTANT]
    > To have a cPanel associated with your domain, you need a hosting account with Hostgator. Pour commencer à utiliser Microsoft, vous pouvez acheter un compte d’hébergement auprès de Hostgator ou redéléguer vos serveurs de noms pour [qu’ils pointent vers Microsoft.](change-nameservers-at-hostgator.md) 
  
2. Dans la page **Panneau de contrôle,** dans la zone **Domaines,** sélectionnez **Advanced Zone Editor**.
    
3. Ajoutez le premier des six enregistrements CNAME.
    
    Dans la page Éditeur de  **zone** avancée, dans la zone Ajouter un enregistrement, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |**Name**|**TTL (Durée de vie)**|**Type (Type)**|**CNAME**|
    |:-----|:-----|:-----|:-----|
    |autodiscover. *domain_name*. (par exemple, autodiscover.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |autodiscover.outlook.com  <br/> |
    |sip. *domain_name*. (par exemple, sip.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover. *domain_name*. (par exemple, lyncdiscover.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |webdir.online.lync.com  <br/> |
    |enterpriseregistration. *domain_name*. (par exemple, enterpriseregistration.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |enterpriseregistration.windows.net  <br/> |
    |enterpriseenrollment. *domain_name*. (par exemple, enterpriseregistration.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |CNAME  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

  
4. Sélectionnez **Ajouter un enregistrement**.

5. Ajoutez successivement les 5 autres enregistrements CNAME.
    
    Dans la section **Ajouter** un enregistrement, créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Ajouter** un enregistrement pour terminer cet enregistrement. 
    
    Répétez cette procédure jusqu'à avoir créé les 6 enregistrements CNAME.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir qu’un seul enregistrement SPF qui inclut les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](../../enterprise/external-domain-name-system-records.md#bkmk_spfrecords). To validate your SPF record, you can use one of these [SPF validation tools](../setup/domains-faq.yml). 
  
> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
1. Pour commencer, accédez à la page cPanel sur Hostgator. Avant toute chose, vous serez invité à vous connecter.
    
    (Une adresse cPanel unique est affectée à chaque compte hébergé sur Hostgator. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. L’e-mail d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page **d’hébergement.)**
    
    > [!IMPORTANT]
    > To have a cPanel associated with your domain, you need a hosting account with Hostgator. Pour commencer à utiliser Microsoft, vous pouvez acheter un compte d’hébergement auprès de Hostgator ou redéléguer vos serveurs de noms pour [qu’ils pointent vers Microsoft.](change-nameservers-at-hostgator.md) 
  
2. Dans la page **Panneau de contrôle,** dans la zone **Domaines,** sélectionnez **Advanced Zone Editor**.
    
3. On the **Advanced DNS Zone Editor** page, in the **Add a Record** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |**Name**|**TTL (Durée de vie)**|**Type (Type)**|**TXT Data (Données TXT)**|
    |:-----|:-----|:-----|:-----|
    |Utilisez votre  *domain_name*. (for example, fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |TXT  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
  
4. Sélectionnez **Ajouter un enregistrement**.
    
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

> [!IMPORTANT]
> Avant d'effectuer cette procédure, vous devez suivre celle décrite dans la première section de cet article ([Faire pointer votre domaine vers votre compte d'hébergement](#point-your-domain-to-your-hosting-account)). 
  
1. Pour commencer, accédez à la page cPanel sur Hostgator. Avant toute chose, vous serez invité à vous connecter.
    
    (Une adresse cPanel unique est affectée à chaque compte hébergé sur Hostgator. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. L’e-mail d’inscription que vous avez reçu de Hostgator spécifie cette adresse et un lien cPanel est également disponible sur la page **d’hébergement.)**
    
    > [!IMPORTANT]
    > To have a cPanel associated with your domain, you need a hosting account with Hostgator. Pour commencer à utiliser Microsoft, vous pouvez acheter un compte d’hébergement auprès de Hostgator ou redéléguer vos serveurs de noms pour [qu’ils pointent vers Microsoft.](change-nameservers-at-hostgator.md) 
  
2. Dans la page **Panneau de contrôle,** dans la zone **Domaines,** sélectionnez **Advanced Zone Editor**.

    
3. Ajoutez le premier des deux enregistrements SRV.
    
    Sur la page **Advanced DNS Zone Editor (Éditeur de zone DNS avancé)**, dans la zone **Add a Record (Ajouter un enregistrement)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |**Name**|**TTL (Durée de vie)**|**Type (Type)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip._tls. *domain_name*. (par exemple, _sip._tls.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |SRV  <br/> |100  <br/> |1  <br/> |443  <br/> |sipdir.online.lync.com  <br/> |
    |_sipfederationtls._tcp. *domain_name*. (par exemple, _sipfederationtls._tcp.fourthcoffee.com.)  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |SRV  <br/> |100  <br/> |1  <br/> |5061  <br/> |sipfed.online.lync.com  <br/> |
   

4. Sélectionnez **Ajouter un enregistrement**.

  
5. Ajoutez l’autre enregistrement SRV.
    
    Dans la section **Ajouter** un enregistrement, créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Ajouter** un enregistrement pour terminer cet enregistrement. 
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).