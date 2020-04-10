---
title: Modifier les serveurs de noms pour configurer Office 365 auprès de Bluehost
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
ms.assetid: 7712b6af-329c-43a0-af7b-c4e4c1befb0e
description: 'Découvrez comment configurer Office 365 pour gérer vos enregistrements DNS sur Bluehost. '
ms.openlocfilehash: dbd06791df2e7f8e6ca085b82dc880e9626c065c
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43212340"
---
# <a name="change-nameservers-to-set-up-office-365-with-bluehost"></a>Modifier les serveurs de noms pour configurer Office 365 auprès de Bluehost

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si vous voulez qu'Office 365 gère vos enregistrements DNS Office 365 à votre place, suivez ces instructions (vous pouvez également [gérer tous vos enregistrements DNS Office 365 via Bluehost](create-dns-records-at-bluehost.md)).
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Bluehost en utilisant [ce lien](https://my.bluehost.com/cgi/dm). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **domains (domaines)**, dans la zone **domain (domaine)**, recherchez la ligne associée au domaine que vous modifiez, puis cochez la case correspondant à ce domaine. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.) 
    
3. Dans la zone **domain_name** , sur la ligne **éditeur de zone DNS** , sélectionnez **gérer les enregistrements DNS**.
    
4. On the **DNS Zone Editor** page, in the Add DNS Record area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
|||||
|:-----|:-----|:-----|:-----|
|**Host Record** <br/> |**TTL (Durée de vie)** <br/> |**Type (Type)** <br/> |**TXT Value** <br/> |
|@  <br/> |14400  <br/> |TXT  <br/> |MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) <br/> |

   
5. Sélectionnez **Ajouter un enregistrement**.
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
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
>  La procédure suivante montre comment supprimer tous les autres serveurs de noms indésirables de la liste, et également comment ajouter les serveurs de noms corrects s’ils ne sont pas déjà répertoriés. > lorsque vous avez effectué les étapes de cette section, les seuls serveurs de noms qui doivent être répertoriés sont les quatre suivants : > ns1.bdm.microsoftonline.com > ns2.bdm.microsoftonline.com > ns3.bdm.microsoftonline.com > ns4.bdm.microsoftonline.com 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Bluehost en utilisant [ce lien](https://my.bluehost.com/cgi/dm). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **domaines** , dans la zone **domain_name** , activez la case à cocher pour votre domaine, puis sélectionnez **serveurs de noms**.
    
    ![Bluehost-BP-Redelegate-1-1](../../media/8f384386-197c-4272-9675-82037922dac4.png)
  
3. Dans la zone **domain_name** , sélectionnez utiliser des serveurs de **noms personnalisés**.
    
    ![Bluehost-BP-Redelegate-1-2](../../media/9fb47d21-c4ce-4eee-af90-c9569870a329.png)
  
4. Suivez l'une des procédures suivantes en fonction du scénario qui s'applique à votre cas dans la page qui s'affiche :
    
  - Si **AUCUN** serveur de noms n'est encore répertorié, [Si AUCUN serveur de noms n'est encore répertorié](#if-there-are-no-nameservers-already-listed).
    
  - Si **DES** serveurs de noms sont déjà répertoriés, [Si DES serveurs de noms sont déjà répertoriés](#if-there-are-nameservers-already-listed).
    
### <a name="if-there-are-no-nameservers-already-listed"></a>Si AUCUN serveur de noms n'est encore répertorié

1. Dans la section **Use Custom Nameservers (Utiliser des serveurs de noms personnalisés)**, tapez ou copiez-collez les valeurs du tableau suivant. 
    
|||
|:-----|:-----|
|**Première ligne vide** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Deuxième ligne vide** <br/> |ns2.bdm.microsoftonline.com  <br/> |
   
   ![Bluehost-BP-redelegate-1-3-1](../../media/07b13d6d-a34e-45b5-afd5-48ebd4c1344f.png)
  
2. Sélectionnez **Ajouter une ligne**.
    
    ![Bluehost-BP-Redelegate-1-3-2](../../media/db34b632-1d10-44b7-aa1f-44bd27bf09e3.png)
  
3. Toujours dans la section **Use Custom Nameservers** (Utiliser des serveurs de noms personnalisés), tapez ou copiez-collez les valeurs du tableau suivant dans la première ligne vide. 
    
|||
|:-----|:-----|
|**Troisième ligne vide** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Quatrième ligne vide** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
    ![Bluehost-BP-Redelegate-1-3-3](../../media/480b32bb-af27-40a5-90c5-5617ed02bb41.png)
  
4. Pour ajouter le quatrième enregistrement de serveur de noms, sélectionnez de nouveau **Ajouter une ligne** , puis créez un enregistrement à l’aide des valeurs de la dernière ligne du tableau ci-dessus. 
    
5. Sélectionnez **enregistrer les paramètres**serveur de noms.
    
    ![Bluehost-BP-Redelegate-1-4](../../media/b24a4cfd-924b-4b6d-ad3d-2dea148fc77f.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine. 
  
### <a name="if-there-are-nameservers-already-listed"></a>Si DES serveurs de noms sont déjà répertoriés

> [!CAUTION]
> Follow these steps only if you have existing nameservers other than the four correct nameservers. (Autrement dit, supprimez uniquement les serveurs de noms en cours qui *ne sont pas* nommés **NS1.BDM.microsoftonline.com**, **ns2.BDM.microsoftonline.com**, **NS3.BDM.microsoftonline.com**ou **NS4.BDM.microsoftonline.com**.) 
  
1. Si d'autres serveurs de noms sont répertoriés, supprimez-les individuellement en les sélectionnant et en appuyant sur la touche **Suppr** du clavier. 
    
    ![Bluehost-BP-Redelegate-1-5](../../media/d1051c43-f8ff-46d7-af26-3975d3f0f621.png)
  
2. Toujours dans la section **Use Custom Nameservers (Utiliser des serveurs de noms personnalisés)**, tapez ou copiez-collez les valeurs du tableau suivant. 
    
|||
|:-----|:-----|
|**Première ligne vide** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Deuxième ligne vide** <br/> |ns2.bdm.microsoftonline.com  <br/> |
   
   ![Bluehost-BP-redelegate-1-3](../../media/1523debf-5eb0-4765-8e05-bcd56e375c20.png)
  
3. Sélectionnez **Ajouter une ligne**.
    
    ![Bluehost-BP-Redelegate-1-3-2](../../media/db34b632-1d10-44b7-aa1f-44bd27bf09e3.png)
  
4. Toujours dans la section **Use Custom Nameservers** (Utiliser des serveurs de noms personnalisés), tapez ou copiez-collez les valeurs du tableau suivant dans la première ligne vide. 
    
|||
|:-----|:-----|
|**Troisième ligne vide** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Quatrième ligne vide** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![Bluehost-BP-redelegate-1-3-3](../../media/480b32bb-af27-40a5-90c5-5617ed02bb41.png)
  
5. Pour ajouter le quatrième enregistrement de serveur de noms, sélectionnez de nouveau **Ajouter une ligne** , puis créez un enregistrement à l’aide des valeurs de la dernière ligne du tableau ci-dessus. 
    
6. Sélectionnez **enregistrer les paramètres**serveur de noms.
    
    ![Bluehost-BP-Redelegate-1-4](../../media/b24a4cfd-924b-4b6d-ad3d-2dea148fc77f.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine. 
  
