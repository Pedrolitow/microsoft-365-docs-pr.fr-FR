---
title: Modifier les serveurs de noms pour configurer Microsoft auprès de Hostgator
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
ms.assetid: f3bd3c62-0477-48e4-b2b5-21e329d67985
description: Découvrez comment configurer Microsoft pour gérer les enregistrements DNS de votre domaine personnalisé sur Hostgator.
ms.openlocfilehash: 34e7bbe3abc084185f72f4fef004ad891492ef3c
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658019"
---
# <a name="change-nameservers-to-set-up-microsoft-365-with-hostgator"></a>Modifier les serveurs de noms pour configurer Microsoft 365 auprès de Hostgator

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.
  
Si vous souhaitez que Microsoft gère vos enregistrements DNS à votre place, suivez ces instructions. (Si vous préférez, vous pouvez gérer tous vos [enregistrements DNS Microsoft sur Hostgator.)](create-dns-records-at-hostgator.md)
  
    
## <a name="point-your-domain-to-your-hosting-account"></a>Pointez votre domaine vers votre compte d'hébergement.

> [!IMPORTANT]
> Vous devez effectuer cette procédure avant d'effectuer celle décrite dans la section **Ajouter un enregistrement TXT de vérification)**.
  
Suivez ces étapes pour associer votre domaine et vos comptes d'hébergement.
  
1. Pour commencer, accédez à votre page du portail client sur le site Hostgator en utilisant [ce lien](https://portal.hostgator.com/domain/manage). Vous serez invité à vous connecter.
    
    ![Hostgator-BP-Redelegate-1-0](../../media/6749ac23-4832-4daf-8f3b-bc3b9b1b979c.png)
  
2. Sélectionnez **l’onglet Domaines.**
    
    ![Hostgator-BP-Redelegate-1-1](../../media/56d12bfd-3549-4033-90dc-077c76ca798c.png)
  
3. Dans la page **Gérer les domaines,** dans la zone **Mes** domaines, sélectionnez le domaine que vous souhaitez mettre à jour.
    
    ![Hostgator-BP-Redelegate-1-2](../../media/2c2f8530-26a1-4e62-bb04-b3874bc1cf36.png)
  
4. Dans la page **Vue d’ensemble** des domaines, dans la zone **Serveurs de** noms, sélectionnez **Modifier.**
    
    ![Hostgator-BP-Redelegate-1-3](../../media/c8979d8a-ee96-4064-a8df-c5b01054cb16.png)
  
5. Dans la page **Serveurs de noms** de votre domaine, dans  la liste de listes de listes listes de sélection du compte d’hébergement, choisissez le compte d’hébergement associé à votre domaine. 
    
    ![Hostgator-BP-Redelegate-1-4](../../media/4cf61060-1e8a-4758-9892-32059ffc90c2.png)
  
6. Sélectionnez **Enregistrer les serveurs de noms.**
    
    ![Hostgator-BP-Redelegate-1-9](../../media/b52a825a-6d54-49ba-87c8-52f770fdfa0c.png)
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

> [!IMPORTANT]
> Avant d’effectuer cette procédure, vous devez d’abord effectuer la procédure de la première section de cet article, pointez votre domaine vers [votre compte d’hébergement.](#point-your-domain-to-your-hosting-account)
  
Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement.
  
1. Pour commencer, accédez à la page cPanel sur Hostgator. Avant toute chose, vous serez invité à vous connecter.
    
    (Une adresse cPanel unique est affectée à chaque compte hébergé sur Hostgator. Votre adresse cPanel doit ressembler à ceci : https://YourSiteAddress:secure-port-numberéro-port-sécurisé. Le message d'inscription que vous avez reçu de Hostgator mentionne cette adresse.)
    
    > [!IMPORTANT]
    > To have a cPanel associated with your domain, you need a hosting account with Hostgator. To get started, you can either purchase a hosting account from Hostgator or [change your domain's nameserver (NS) records](#change-your-domains-nameserver-ns-records) to point to Microsoft. 
  
2. Dans la page **Panneau de** contrôle, dans la zone **Domaines,** sélectionnez **Advanced DNS Zone Editor**.
    
    (Vous devrez peut-être faire défiler la page vers le bas.) 
    
3. On the **Advanced DNS Zone Editor** page, in the **Add a Record** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
|||||
|:-----|:-----|:-----|:-----|
|**Name** <br/> |**TTL (Durée de vie)** <br/> |**Type (Type)** <br/> |**TXT Data (Données TXT)** <br/> |
|Utilisez votre  *nom_de_domaine*  (par exemple, fourthcoffee.com).<br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1   <br/> |TXT  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)     <br/>  |
   
4. Sélectionnez **Ajouter un enregistrement**.
    
5. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
Maintenant que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous revenir à Microsoft et demander une recherche pour l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

Pour terminer la configuration de votre domaine avec Microsoft, vous modifiez les enregistrements NS de votre domaine auprès de votre bureau d’enregistrement de domaines pour qu’ils pointent vers les serveurs de noms principal et secondaire Microsoft. Cela permet à Microsoft de mettre à jour les enregistrements DNS du domaine pour vous. Pour finaliser la configuration, nous ajouterons tous les enregistrements de façon à ce que vous puissiez utiliser la messagerie, Skype Entreprise Online et votre site web public avec votre domaine.
  
> [!CAUTION]
> Lorsque vous modifiez les enregistrements NS de votre domaine pour qu’ils pointent vers les serveurs de noms Microsoft, tous les services actuellement associés à votre domaine sont affectés. Par exemple, tous les e-mails envoyés à votre domaine (comme rob@ *your_domain*  .com) commenceront à arriver à Microsoft après avoir fait cette modification.
  
> [!IMPORTANT]
> La procédure suivante vous montre comment supprimer d’autres serveurs de noms indésirables de la liste et comment ajouter les serveurs de noms corrects s’ils ne sont pas déjà répertoriés. Une fois que vous avez effectué les étapes de cette section, les seuls serveurs de noms qui doivent être répertoriés sont les quatre :  **ns1.bdm.microsoftonline.com,** **ns2.bdm.microsoftonline.com,** **ns3.bdm.microsoftonline.com** et **ns4.bdm.microsoftonline.com**.
  
1. Pour commencer, accédez à votre page du portail clients sur le site Hostgator en utilisant [ce lien](https://portal.hostgator.com/domain/manage). Vous serez invité à vous connecter.
    
    ![Hostgator-BP-Redelegate-1-0](../../media/6749ac23-4832-4daf-8f3b-bc3b9b1b979c.png)
  
2. Sélectionnez **l’onglet Domaines.** 
    
    ![Hostgator-BP-Redelegate-1-1](../../media/56d12bfd-3549-4033-90dc-077c76ca798c.png)
  
3. Dans la page **Gérer les domaines,** dans la zone **Mes** domaines, sélectionnez le domaine que vous souhaitez mettre à jour. 
    
    ![Hostgator-BP-Redelegate-1-2](../../media/2c2f8530-26a1-4e62-bb04-b3874bc1cf36.png)
  
4. Dans la page **Vue d’ensemble** du domaine, dans la zone **Serveurs de** noms, sélectionnez **Modifier.**
    
    ![Hostgator-BP-Redelegate-1-3](../../media/c8979d8a-ee96-4064-a8df-c5b01054cb16.png)
  
5. Dans la page **Serveurs de noms** de votre domaine, dans  la liste de listes de listes listes de sélection du compte d’hébergement, choisissez le compte d’hébergement associé à votre domaine.  
    
    ![Hostgator-BP-Redelegate-1-4](../../media/4cf61060-1e8a-4758-9892-32059ffc90c2.png)
  
6. Sélectionnez **Définir manuellement mes serveurs de noms.**
    
    ![Hostgator-BP-Redelegate-1-5](../../media/5b73ae32-f26e-48aa-b5ad-6da20f1c491a.png)
  
7.   **ATTENTION**: suivez ces étapes uniquement si vous avez des serveurs de noms existants autres que les quatre serveurs de noms corrects. (Autrement dit, supprimez uniquement les  serveurs de noms actuels qui ne sont pas nommés **ns1.bdm.microsoftonline.com,** **ns2.bdm.microsoftonline.com,** **ns3.bdm.microsoftonline.com** ou **ns4.bdm.microsoftonline.com**.)
  
        Toujours sur la page **Name Servers (Serveurs de noms)** pour votre domaine, dans la liste des serveurs de noms, supprimez les serveurs de noms individuellement dans la liste en les sélectionnant un par un et en appuyant sur la touche **Suppr** du clavier. 
    
   ![Hostgator-BP-Redelegate-1-6](../../media/fa9820e7-28bb-4792-b16c-51e54d83feb1.png)
  
8. Toujours dans la liste des serveurs de noms, tapez ou copiez-collez les deux premières valeurs du tableau suivant.
    
|||
|:-----|:-----|
|**Name server 1 (Serveur de noms 1) :** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Name server 2 (Serveur de noms 2) :** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**Serveur de noms 3 :** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Serveur de noms 4 :** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![Hostgator-BP-Redelegate-1-7-1](../../media/a8c10aa7-30b0-4bc8-9596-20256d396274.png)
  
9. Ajoutez les autres valeurs de serveur de noms.
    
    Sélectionnez **(+),** puis tapez ou copiez-collez la valeur de la ligne suivante du tableau dans la zone de l’enregistrement. 
    
    Répétez cette procédure jusqu'à avoir créé les quatre enregistrements de serveur de noms.
    
    ![Hostgator-BP-Redelegate-1-7-2](../../media/92159a39-e498-4220-9b0d-ae2e718c7fb9.png)
  
10. Sélectionnez **Enregistrer les serveurs de noms.**
    
    ![Hostgator-BP-Redelegate-1-8](../../media/bd6b0dfa-5d39-4805-970d-7ab153cff117.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Ensuite, votre messagerie Microsoft et d’autres services seront tous définies pour fonctionner avec votre domaine.
