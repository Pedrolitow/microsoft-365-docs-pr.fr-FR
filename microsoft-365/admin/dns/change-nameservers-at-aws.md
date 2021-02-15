---
title: Modifier les serveurs de noms pour configurer Microsoft auprès d’Amazon Web Services (AWS)
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
ms.assetid: 0ddbe33c-81ea-4c02-8db9-e71d3810c0ec
description: 'Découvrez comment configurer Microsoft pour gérer vos enregistrements DNS sur Amazon Web Services (AWS). '
ms.openlocfilehash: 4700557c40973ab051cced81c129197a826964ab
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658451"
---
# <a name="change-nameservers-to-set-up-microsoft-with-amazon-web-services-aws"></a>Modifier les serveurs de noms pour configurer Microsoft auprès d’Amazon Web Services (AWS)

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si vous souhaitez que Microsoft gère vos enregistrements DNS à votre place, suivez ces instructions. (Si vous préférez, vous pouvez gérer tous vos [enregistrements DNS Microsoft sur AWS.)](create-dns-records-at-aws.md)
  
    
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **Ressources,** sélectionnez **Zones hébergées.**
    
3. Dans la page **Zones hébergées,** dans la colonne **Nom** de domaine, sélectionnez le nom du domaine à modifier. 
    
4. Sélectionnez **Créer un jeu d’enregistrement.**
    
5. In the **Create Record Set** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** and **Routing Policy** values from the drop-down lists.) 
    
    > [!TIP]
    > The quotation marks required by the onscreen instructions are supplied automatically. You don't need to type them manually. 
  
|||||||
|:-----|:-----|:-----|:-----|:-----|:-----|
|**Name** <br/> |**Type (Type)** <br/> |**Alias** <br/> |**TTL (Seconds) (Durée de vie (secondes))** <br/> |**Value (Valeur)** <br/> |**Routing Policy (Stratégie de routage)** <br/> |
|(Laissez ce champ vide)  <br/> |TXT - Text  <br/> |Non  <br/> |300  <br/> |MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)  <br/>  |Simple <br/> |
   
6. Sélectionnez **Créer**.
    
7. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
Maintenant que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, revenir à Microsoft et demander une recherche pour l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

Pour terminer la configuration de votre domaine avec Microsoft, vous modifiez les enregistrements NS de votre domaine auprès de votre bureau d’enregistrement de domaines pour qu’ils pointent vers les serveurs de noms principaux et secondaires de Microsoft. Cela permet à Microsoft de mettre à jour les enregistrements DNS du domaine pour vous. Pour finaliser la configuration, nous ajouterons tous les enregistrements de façon à ce que vous puissiez utiliser la messagerie, Skype Entreprise Online et votre site web public avec votre domaine.
  
> [!CAUTION]
> Lorsque vous modifiez les enregistrements NS de votre domaine pour qu’ils pointent vers les serveurs de noms Microsoft, tous les services actuellement associés à votre domaine sont affectés. Par exemple, tous les e-mails envoyés à votre domaine (comme rob@ *your_domain*  .com) commenceront à arriver à Microsoft après avoir fait cette modification. 
  
> [!IMPORTANT]
>  La procédure suivante vous montre comment supprimer d’autres serveurs de noms indésirables de la liste et comment ajouter les serveurs de noms corrects s’ils ne sont pas déjà répertoriés. > lorsque vous avez effectué les étapes de cette section, les seuls serveurs de noms qui doivent être répertoriés sont les quatre : > ns1.bdm.microsoftonline.com > ns2.bdm.microsoftonline.com > ns3.bdm.microsoftonline.com > ns4.bdm.microsoftonline.com 
  
1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **Ressources,** sélectionnez **Zones hébergées.**
    
3. Dans la page **Zones hébergées,** dans la colonne **Nom** de domaine, sélectionnez le nom du domaine à modifier. 
    
4. Sélectionnez le jeu d'enregistrement **Serveur de noms**. 
    
    ![Select the recordset](../../media/24e618e4-0a16-43a2-9886-f4f5dac79374.png)
  
5. Dans le jeu d'enregistrements **NS - Serveur de noms**, dans la zone **Valeur**, supprimez tous les serveurs de noms en les sélectionnant, puis en appuyant sur la touche **Suppr** du clavier. 
    
    > [!CAUTION]
    > Follow these steps only if you have existing nameservers other than the four correct nameservers. (Autrement dit, supprimez uniquement les  serveurs de noms actuels qui ne sont pas nommés **ns1.bdm.microsoftonline.com,** **ns2.bdm.microsoftonline.com,** **ns3.bdm.microsoftonline.com** ou **ns4.bdm.microsoftonline.com**.) 
  
    ![Select and delete all of the nameservers in the Value box](../../media/ecf1e897-fa7d-4abc-b00b-bf55b8ed2139.png)
  
6. Dans la **zone TTL (Secondes)** : **sélectionnez 1h** (1 heure). 
    
    ![Sélectionner 1H pour une heure](../../media/c70070e1-4bde-41a7-b271-9d22c475edf6.png)
  
7. Toujours dans le jeu d'enregistrements **NS - Serveur de noms**, dans la zone **Valeur**, tapez ou copiez-collez la valeur de la **première ligne** du tableau suivant, appuyez sur la touche **Entrée** du clavier, puis tapez ou copiez-collez la valeur de la **ligne** suivante. 
    
    > [!IMPORTANT]
    > Chaque valeur de serveur de noms  *doit*  figurer sur sa propre ligne distincte dans la zone **Valeur**, comme dans l'illustration suivante. 
  
|||
|:-----|:-----|
|**Première ligne** <br/> |ns1.bdm.microsoftonline.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
|**Deuxième ligne** <br/> |ns2.bdm.microsoftonline.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
|**Troisième ligne** <br/> |ns3.bdm.microsoftonline.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
|**Quatrième ligne** <br/> |ns4.bdm.microsoftonline.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
   
   ![Tapez ou collez la valeur de première ligne dans la zone Valeur](../../media/b63f41e0-51ef-4ab2-a4b8-ee7380e5ab35.png)
  
8. Sélectionnez **Enregistrer le jeu d’enregistrement.**
    
    ![Sélectionnez Enregistrer le jeu d’enregistrement](../../media/ab3c0558-bb7c-41e4-871e-ea82f1553476.png)
  
> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Ensuite, votre messagerie Microsoft et d’autres services seront tous définies pour fonctionner avec votre domaine. 
