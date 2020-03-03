---
title: Modifier les serveurs de noms pour configurer Office 365 auprès de Hostgator
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
- Adm_NonTOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f3bd3c62-0477-48e4-b2b5-21e329d67985
description: Découvrez comment configurer Office 365 pour gérer les enregistrements DNS de votre domaine personnalisé sur Hostgator.
ms.openlocfilehash: 95131e258482fdb0ff9aa7f00b3339e1c6f9509d
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42351845"
---
# <a name="change-nameservers-to-set-up-office-365-with-hostgator"></a>Modifier les serveurs de noms pour configurer Office 365 auprès de Hostgator

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez.
  
Si vous voulez qu'Office 365 gère vos enregistrements DNS Office 365 à votre place, suivez ces instructions (vous pouvez également [gérer tous vos enregistrements DNS Office 365 via Hostgator](create-dns-records-at-hostgator.md)).
  
    
## <a name="point-your-domain-to-your-hosting-account"></a>Pointez votre domaine vers votre compte d'hébergement.

> [!IMPORTANT]
> Vous devez effectuer cette procédure avant d'effectuer celle décrite dans la section **Ajouter un enregistrement TXT de vérification)**.
  
Suivez ces étapes pour associer votre domaine et vos comptes d'hébergement.
  
1. Pour commencer, accédez à votre page du portail client sur le site Hostgator en utilisant [ce lien](https://portal.hostgator.com/domain/manage). Vous serez invité à vous connecter.
    
    ![Hostgator-BP-Redelegate-1-0](../../media/6749ac23-4832-4daf-8f3b-bc3b9b1b979c.png)
  
2. Sélectionnez l’onglet **domaines** .
    
    ![Hostgator-BP-Redelegate-1-1](../../media/56d12bfd-3549-4033-90dc-077c76ca798c.png)
  
3. Sur la page **gérer les domaines** , dans la zone **Mes domaines** , sélectionnez le domaine que vous souhaitez mettre à jour.
    
    ![Hostgator-BP-Redelegate-1-2](../../media/2c2f8530-26a1-4e62-bb04-b3874bc1cf36.png)
  
4. Dans la page **vue d’ensemble des domaines** , dans la zone **serveurs de noms** , sélectionnez **modifier**.
    
    ![Hostgator-BP-Redelegate-1-3](../../media/c8979d8a-ee96-4064-a8df-c5b01054cb16.png)
  
5. Sur la page **serveurs de noms** de votre domaine, dans la liste déroulante Sélectionner un compte d' **hébergement** , sélectionnez le compte d' **hébergement** associé à votre domaine.
    
    ![Hostgator-BP-Redelegate-1-4](../../media/4cf61060-1e8a-4758-9892-32059ffc90c2.png)
  
6. Sélectionnez **enregistrer les serveurs de noms**.
    
    ![Hostgator-BP-Redelegate-1-9](../../media/b52a825a-6d54-49ba-87c8-52f770fdfa0c.png)
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

> [!IMPORTANT]
> Avant d’effectuer cette procédure, vous devez d’abord effectuer la procédure décrite dans la première section de cet article, [faire pointer votre domaine vers votre compte d’hébergement.](#point-your-domain-to-your-hosting-account).
  
Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement.
  
1. Pour commencer, accédez à la page cPanel sur Hostgator. Avant toute chose, vous serez invité à vous connecter.
    
    (Une adresse cPanel unique est affectée à chaque compte hébergé sur Hostgator. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. Le message d'inscription que vous avez reçu de Hostgator mentionne cette adresse.)
    
    > [!IMPORTANT]
    > To have a cPanel associated with your domain, you need a hosting account with Hostgator. Pour commencer à utiliser Office 365, vous pouvez acheter un compte d’hébergement auprès d’Hostgator ou [modifier les enregistrements de serveur de noms de votre domaine (NS)](#change-your-domains-nameserver-ns-records) de sorte qu’il pointe vers Office 365. 
  
2. Sur la page **panneau de configuration** , dans la zone **domaines** , sélectionnez **éditeur de zone DNS avancée**.
    
    (You may have to scroll down.) 
    
3. On the **Advanced DNS Zone Editor** page, in the **Add a Record** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
|||||
|:-----|:-----|:-----|:-----|
|**Name (Nom)** <br/> |**TTL (Durée de vie)** <br/> |**Type (Type)** <br/> |**TXT Data (Données TXT)** <br/> |
|Utilisez votre  *nom_de_domaine*  (par exemple, fourthcoffee.com).<br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |0,1  <br/> |TXT  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)     <br/>  |
   
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
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

Pour finaliser la configuration de votre domaine avec Office 365, vous devez modifier les enregistrements de serveur de noms auprès de votre bureau d'enregistrement de domaines afin qu'ils pointent vers les serveurs de noms principal et secondaire Office 365. Office 365 est ainsi informé qu'il doit mettre à jour les enregistrements DNS du domaine pour vous. Pour finaliser la configuration, nous ajouterons tous les enregistrements de façon à ce que vous puissiez utiliser la messagerie, Skype Entreprise Online et votre site web public avec votre domaine.
  
> [!CAUTION]
> Lorsque vous modifiez les enregistrements de serveur de noms de votre domaine de façon à ce qu'ils pointent vers les serveurs de noms Office 365, tous les services actuellement associés à votre domaine sont affectés. Par exemple, les messages envoyés à votre domaine (tel que thomas@ *votre_domaine*  .com) arriveront dans Office 365 une fois cette modification appliquée.
  
> [!IMPORTANT]
> La procédure suivante montre comment supprimer tous les autres serveurs de noms indésirables de la liste, et également comment ajouter les serveurs de noms corrects s’ils ne sont pas déjà répertoriés. Une fois que vous avez effectué les étapes de cette section, les seuls serveurs de noms qui doivent être répertoriés sont les quatre suivants : **NS1.BDM.microsoftonline.com**, **ns2.BDM.microsoftonline.com**, **NS3.BDM.microsoftonline.com**et **NS4.BDM.microsoftonline.com**.
  
1. Pour commencer, accédez à votre page du portail clients sur le site Hostgator en utilisant [ce lien](https://portal.hostgator.com/domain/manage). Vous serez invité à vous connecter.
    
    ![Hostgator-BP-Redelegate-1-0](../../media/6749ac23-4832-4daf-8f3b-bc3b9b1b979c.png)
  
2. Sélectionnez l’onglet **domaines** . 
    
    ![Hostgator-BP-Redelegate-1-1](../../media/56d12bfd-3549-4033-90dc-077c76ca798c.png)
  
3. Sur la page **gérer les domaines** , dans la zone **Mes domaines** , sélectionnez le domaine que vous souhaitez mettre à jour. 
    
    ![Hostgator-BP-Redelegate-1-2](../../media/2c2f8530-26a1-4e62-bb04-b3874bc1cf36.png)
  
4. Dans la page **vue d’ensemble du domaine** , dans la zone **serveurs de noms** , sélectionnez **modifier**.
    
    ![Hostgator-BP-Redelegate-1-3](../../media/c8979d8a-ee96-4064-a8df-c5b01054cb16.png)
  
5. Sur la page **serveurs de noms** de votre domaine, dans la liste déroulante Sélectionner un compte d' **hébergement** , sélectionnez le compte d' **hébergement** associé à votre domaine. 
    
    ![Hostgator-BP-Redelegate-1-4](../../media/4cf61060-1e8a-4758-9892-32059ffc90c2.png)
  
6. Sélectionnez **définir manuellement les serveurs mon nom**.
    
    ![Hostgator-BP-Redelegate-1-5](../../media/5b73ae32-f26e-48aa-b5ad-6da20f1c491a.png)
  
7.   **Attention**: suivez ces étapes uniquement si vous avez des serveurs de noms existants autres que les quatre serveurs de noms corrects. (Autrement dit, supprimez uniquement les serveurs de noms en cours qui *ne sont pas* nommés **NS1.BDM.microsoftonline.com**, **ns2.BDM.microsoftonline.com**, **NS3.BDM.microsoftonline.com**ou **NS4.BDM.microsoftonline.com**.)
  
        Toujours sur la page **Name Servers (Serveurs de noms)** pour votre domaine, dans la liste des serveurs de noms, supprimez les serveurs de noms individuellement dans la liste en les sélectionnant un par un et en appuyant sur la touche **Suppr** du clavier. 
    
   ![Hostgator-BP-Redelegate-1-6](../../media/fa9820e7-28bb-4792-b16c-51e54d83feb1.png)
  
8. Toujours dans la liste des serveurs de noms, tapez ou copiez-collez les deux premières valeurs du tableau suivant.
    
|||
|:-----|:-----|
|**Name server 1 (Serveur de noms 1) :** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Name server 2 (Serveur de noms 2) :** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**Serveur de noms 3 :** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Serveur de noms 4 :** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![Hostgator-BP-redelegate-1-7-1](../../media/a8c10aa7-30b0-4bc8-9596-20256d396274.png)
  
9. Ajoutez les autres valeurs de serveur de noms.
    
    Sélectionnez **(+)** ajouter, puis tapez ou copiez-collez la valeur de la ligne suivante du tableau dans la zone de l’enregistrement. 
    
    Répétez cette procédure jusqu'à avoir créé les quatre enregistrements de serveur de noms.
    
    ![Hostgator-BP-Redelegate-1-7-2](../../media/92159a39-e498-4220-9b0d-ae2e718c7fb9.png)
  
10. Sélectionnez **enregistrer les serveurs de noms**.
    
    ![Hostgator-BP-Redelegate-1-8](../../media/bd6b0dfa-5d39-4805-970d-7ab153cff117.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine.
