---
title: Modifier les serveurs de noms pour configurer Microsoft avec Google Domains
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
ms.assetid: 68a08e94-26c2-4df2-9216-026b8ec907ca
description: Découvrez comment configurer Microsoft pour gérer les enregistrements DNS de votre domaine personnalisé sur Google Domains.
ms.openlocfilehash: e475e222b6f1c9717008a49b172b0ecac5ec6fc7
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658439"
---
# <a name="change-nameservers-to-set-up-microsoft-with-google-domains"></a>Modifier les serveurs de noms pour configurer Microsoft avec Google Domains

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Suivez ces instructions si vous voulez que Microsoft gère vos enregistrements DNS pour vous. (Si vous préférez, vous pouvez [gérer tous vos enregistrements DNS sur Google Domains](create-dns-records-at-google-domains.md).)
  
    
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
>  Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur Google Domains via [ce lien](https://domains.google.com/registrar). You'll be prompted to sign in. To do so:
    
1. Sélectionnez **Se connecter**.
    
2. Entrez vos informations d’identification de connexion et sélectionnez **de nouveau connexion**.
    
2. Dans la page **Domaines**, dans la section **Domaine**, sélectionnez **Configurer le DNS** pour le domaine à modifier. 
    
3. Dans la section **Custom resource records (Enregistrements de ressource personnalisés)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
|||||
|:-----|:-----|:-----|:-----|
|**Name** <br/> |**Type (Type)** <br/> |**TTL (Durée de vie)** <br/> |**Données** <br/> |
|@  <br/> |TXT  <br/> |1H  <br/> |MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)       <br/>  |
   
4. Sélectionnez **Ajouter**.
    
5. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
À présent que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous allez retourner à Microsoft et demander une recherche pour l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

Pour terminer la configuration de votre domaine avec Microsoft, vous devez modifier les enregistrements de serveur de noms de votre domaine au niveau de votre bureau d’enregistrement de domaines afin de pointer vers les serveurs de noms principaux et secondaires Microsoft. Cela permet à Microsoft de mettre à jour les enregistrements DNS du domaine pour vous. Pour finaliser la configuration, nous ajouterons tous les enregistrements de façon à ce que vous puissiez utiliser la messagerie, Skype Entreprise Online et votre site web public avec votre domaine.
  
> [!CAUTION]
> Lorsque vous modifiez les enregistrements de serveur de noms de votre domaine pour qu’ils pointent vers les serveurs de noms Microsoft, tous les services actuellement associés à votre domaine sont affectés. Par exemple, tous les messages électroniques envoyés à votre domaine (par exemple, rob@ *your_domain.*  com) démarrera à Microsoft une fois cette modification apportée. 
  
> [!IMPORTANT]
> The following procedure will show you how to delete any other, unwanted nameservers from the list, and also how to add the correct nameservers if they are not already in the list. > lorsque vous avez effectué les étapes de cette section, les seuls serveurs de noms qui doivent être répertoriés sont les quatre suivants : 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Google Domains en utilisant [ce lien](https://domains.google.com/registrar). Vous êtes invité à vous connecter. Pour ce faire :
    
1. Sélectionnez **Se connecter**.
    
2. Entrez vos informations d’identification, puis sélectionnez à nouveau **Se connecter**.
    
2. Dans la page **Domaines**, dans la section **Domaine**, sélectionnez **Configurer le DNS** pour le domaine à modifier. 
    
3. Dans la page **Domains** (domaines), dans la section **Name servers** (Serveurs de noms), sélectionnez **Use custom name servers** (Utiliser les serveurs de noms personnalisés).
    
    ![Google-Domains-BP-Redelegate-1-1](../../media/e264bc05-5a56-4962-bcaf-e2d999f62278.png)
  
4. Suivez l'une des procédures suivantes en fonction du scénario qui s'applique à votre cas dans la page qui s'affiche :
    
  - Si **AUCUN** serveur de noms n'est encore répertorié, [Si AUCUN serveur de noms n'est encore répertorié](#if-there-are-no-nameservers-already-listed).
    
  - Si **DES** serveurs de noms sont déjà répertoriés, [Si DES serveurs de noms sont déjà répertoriés](#if-there-are-nameservers-already-listed).
    
### <a name="if-there-are-no-nameservers-already-listed"></a>Si AUCUN serveur de noms n'est encore répertorié

1. Ajoutez le premier serveur de noms.
    
    Dans la section **Name servers (Serveurs de noms)**, dans la zone **NAME SERVER (SERVEUR DE NOMS)**, tapez ou copiez-collez la première valeur du tableau suivant. 
    
|||
|:-----|:-----|
|**Premier serveur de noms** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Deuxième serveur de noms** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**Troisième serveur de noms** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Quatrième serveur de noms** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![Google-Domains-BP-redelegate-1-2](../../media/6d14544d-7783-4ed4-b4dd-691624af7172.png)
  
2. Sélectionnez le contrôle **+ (ajouter)** pour créer une ligne vide. 
    
    ![Google-Domains-BP-Redelegate-1-3](../../media/ea23e5fc-07e1-4ffc-b8cf-8526867b752d.png)
  
3. Ajoutez les trois autres enregistrements de serveur de noms.
    
    Dans la section **utiliser des serveurs de noms personnalisés** , créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez le contrôle **+ (ajouter)** pour ajouter une autre ligne. 
    
    Répétez cette procédure jusqu'à avoir créé les quatre enregistrements de serveur de noms.
    
4. Sélectionnez **Enregistrer**.
    
    ![Google-Domains-BP-Redelegate-1-5](../../media/cb954aa2-12ee-4e90-9b67-184cbe898bbb.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Votre messagerie Microsoft et les autres services seront tous configurés pour fonctionner avec votre domaine. 
  
### <a name="if-there-are-nameservers-already-listed"></a>Si DES serveurs de noms sont déjà répertoriés

1. Si d’autres serveurs de noms sont répertoriés, sélectionnez **modifier**.
    
    > [!CAUTION]
    > Follow these steps only if you have existing nameservers other than the four correct nameservers. (Autrement dit, supprimez uniquement les serveurs de noms en cours qui  *ne sont pas*  nommés **NS1.BDM.microsoftonline.com**, **ns2.BDM.microsoftonline.com**, **NS3.BDM.microsoftonline.com** ou **NS4.BDM.microsoftonline.com**.) 
  
    ![Google-Domains-BP-Redelegate-1-6-1](../../media/fb45d120-55ab-42c2-bdb6-19b130c3c7db.png)
  
2. Supprimez chacun d'eux en le sélectionnant, puis en appuyant sur la touche **Suppr** du clavier. 
    
    ![Google-Domains-BP-Redelegate-1-6-2](../../media/524e64ad-56e6-4254-8a64-e4a4c3230f89.png)
  
3. Toujours dans la section **Name servers** (Serveurs de noms), dans les lignes **NAME SERVER** (SERVEUR DE NOMS), tapez ou copiez-collez les valeurs du tableau suivant. 
    
|||
|:-----|:-----|
|**Premier serveur de noms** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Deuxième serveur de noms** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**Troisième serveur de noms** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Quatrième serveur de noms** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![Google-Domains-BP-redelegate-1-7](../../media/e008dccb-d789-4f52-8ecc-02831b7c6fb2.png)
  
4. Sélectionnez le contrôle **+ (ajouter)** pour créer une ligne vide. 
    
    ![Google-Domains-BP-Redelegate-1-8](../../media/6ce40b1e-8464-443f-a64a-825dc8764590.png)
  
5. Ajoutez les deux autres enregistrements de serveur de noms.
    
    Dans la section **utiliser des serveurs de noms personnalisés** , créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez le contrôle **+ (ajouter)** pour ajouter une autre ligne. 
    
    Répétez cette procédure jusqu'à avoir créé les quatre enregistrements de serveur de noms.
    
6. Sélectionnez **Enregistrer**.
    
    ![Google-Domains-BP-Redelegate-1-5](../../media/cb954aa2-12ee-4e90-9b67-184cbe898bbb.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Votre messagerie Microsoft et les autres services seront tous configurés pour fonctionner avec votre domaine. 
  
