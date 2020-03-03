---
title: Modifier les serveurs de noms de manière à configurer Office 365 avec Google Domains
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
ms.assetid: 68a08e94-26c2-4df2-9216-026b8ec907ca
description: Découvrez comment configurer Office 365 pour gérer les enregistrements DNS de votre domaine personnalisé sur Google Domains.
ms.openlocfilehash: f6faaa4a7b6540086752e88da2051a73450f4455
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42351965"
---
# <a name="change-nameservers-to-set-up-office-365-with-google-domains"></a>Modifier les serveurs de noms de manière à configurer Office 365 avec Google Domains

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si vous voulez laisser Office 365 gérer vos enregistrements DNS Office 365 à votre place, suivez ces instructions (si vous préférez, vous pouvez [gérer tous vos enregistrements DNS Office 365 via Google Domains](create-dns-records-at-google-domains.md)).
  
    
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
>  Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur Google Domains via [ce lien](https://domains.google.com/registrar). You'll be prompted to sign in. To do so:
    
1. Sélectionnez **se connecter**.
    
2. Entrez vos informations d’identification de connexion et sélectionnez **de nouveau connexion**.
    
2. Dans la page **domaines** , dans la section **domaine** , sélectionnez **configurer DNS** pour le domaine que vous souhaitez modifier. 
    
3. In the **Custom resource records** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (You may have to scroll down.)
    
    (Choose the **Type** value from the drop-down list.) 
    
|||||
|:-----|:-----|:-----|:-----|
|**Nom** <br/> |**Type** <br/> |**TTL (Durée de vie)** <br/> |**Data (Données)** <br/> |
|@  <br/> |TXT  <br/> |Premier  <br/> |MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)       <br/>  |
   
4. Sélectionnez **Ajouter**.
    
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
> Lorsque vous modifiez les enregistrements de serveur de noms de votre domaine de façon à ce qu'ils pointent vers les serveurs de noms Office 365, tous les services actuellement associés à votre domaine sont affectés. Par exemple, tous les messages électroniques envoyés à votre domaine (par exemple, rob@ *your_domain.*  com) commencera à Office 365 une fois cette modification apportée. 
  
> [!IMPORTANT]
> The following procedure will show you how to delete any other, unwanted nameservers from the list, and also how to add the correct nameservers if they are not already in the list. > lorsque vous avez effectué les étapes de cette section, les seuls serveurs de noms qui doivent être répertoriés sont les quatre suivants : 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Google Domains en utilisant [ce lien](https://domains.google.com/registrar). Vous êtes invité à vous connecter. Pour ce faire :
    
1. Sélectionnez **se connecter**.
    
2. Entrez vos informations d’identification de connexion, puis sélectionnez **de nouveau connexion**.
    
2. Dans la page **domaines** , dans la section **domaine** , sélectionnez **configurer DNS** pour le domaine que vous souhaitez modifier. 
    
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
    
4. Cliquez sur **Enregistrer**.
    
    ![Google-Domains-BP-Redelegate-1-5](../../media/cb954aa2-12ee-4e90-9b67-184cbe898bbb.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine. 
  
### <a name="if-there-are-nameservers-already-listed"></a>Si DES serveurs de noms sont déjà répertoriés

1. Si d’autres serveurs de noms sont répertoriés, sélectionnez **modifier**.
    
    > [!CAUTION]
    > Follow these steps only if you have existing nameservers other than the four correct nameservers. (Autrement dit, supprimez uniquement les serveurs de noms en cours qui *ne sont pas* nommés **NS1.BDM.microsoftonline.com**, **ns2.BDM.microsoftonline.com**, **NS3.BDM.microsoftonline.com**ou **NS4.BDM.microsoftonline.com**.) 
  
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
    
6. Cliquez sur **Enregistrer**.
    
    ![Google-Domains-BP-Redelegate-1-5](../../media/cb954aa2-12ee-4e90-9b67-184cbe898bbb.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine. 
  
