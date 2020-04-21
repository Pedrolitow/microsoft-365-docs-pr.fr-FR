---
title: Modifier les serveurs de noms pour configurer Microsoft avec Bluehost
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
description: 'Découvrez comment configurer Microsoft pour gérer vos enregistrements DNS sur Bluehost. '
ms.openlocfilehash: 63084b35c3f0d71764bca1995f25d7c6f0842a86
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43629910"
---
# <a name="change-nameservers-to-set-up-microsoft-with-bluehost"></a>Modifier les serveurs de noms pour configurer Microsoft avec Bluehost

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Suivez ces instructions si vous voulez que Microsoft gère vos enregistrements DNS pour vous. (Si vous préférez, vous pouvez [gérer tous vos enregistrements DNS sur Bluehost](create-dns-records-at-bluehost.md).)
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant d’utiliser votre domaine avec Microsoft, vous devez vous assurer que vous en êtes propriétaire. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que vous êtes propriétaire du domaine.
  
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
|@  <br/> |14400  <br/> |TXT  <br/> |MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre **adresse de destination ou de pointage** spécifique ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) <br/> |

   
5. Sélectionnez **Ajouter un enregistrement**.
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
À présent que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous allez retourner à Microsoft et demander une recherche pour l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT correct, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> .

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messagerie ou d’autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

Pour terminer la configuration de votre domaine avec Microsoft, vous devez modifier les enregistrements de serveur de noms de votre domaine au niveau de votre bureau d’enregistrement de domaines afin de pointer vers les serveurs de noms principaux et secondaires. Cela permet à Microsoft de mettre à jour les enregistrements DNS du domaine pour vous. Pour finaliser la configuration, nous ajouterons tous les enregistrements de façon à ce que vous puissiez utiliser la messagerie, Skype Entreprise Online et votre site web public avec votre domaine.
  
> [!CAUTION]
> Lorsque vous modifiez les enregistrements de serveur de noms de votre domaine pour qu’ils pointent vers les serveurs de noms Microsoft, tous les services actuellement associés à votre domaine sont affectés. Par exemple, tous les messages électroniques envoyés à votre domaine (par exemple, rob@ *your_domain* . com) débuteront à Microsoft après avoir effectué cette modification. 
  
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
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Votre messagerie Microsoft et les autres services seront tous configurés pour fonctionner avec votre domaine. 
  
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
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Votre messagerie Microsoft et les autres services seront tous configurés pour fonctionner avec votre domaine. 
  
