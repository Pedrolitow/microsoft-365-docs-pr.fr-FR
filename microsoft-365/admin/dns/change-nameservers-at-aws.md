---
title: Modifier les serveurs de noms de manière à configurer Office 365 avec Amazon Web Services (AWS)
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
ms.assetid: 0ddbe33c-81ea-4c02-8db9-e71d3810c0ec
description: 'Découvrez comment configurer Office 365 pour gérer vos enregistrements DNS sur Amazon Web Services (AWS). '
ms.openlocfilehash: a7125cf0add8200fe152c426f47e7f27a8f6226c
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43212352"
---
# <a name="change-nameservers-to-set-up-office-365-with-amazon-web-services-aws"></a>Modifier les serveurs de noms de manière à configurer Office 365 avec Amazon Web Services (AWS)

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si vous voulez laisser Office 365 gérer vos enregistrements DNS Office 365 à votre place, suivez ces instructions (si vous préférez, vous pouvez [gérer tous vos enregistrements DNS Office 365 via AWS](create-dns-records-at-aws.md)).
  
    
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
2. Sur la page **ressources** , sélectionnez **zones hébergées**.
    
3. Dans la page **zones hébergées** , dans la colonne **nom de domaine** , sélectionnez le nom du domaine à modifier. 
    
4. Sélectionnez **créer un jeu d’enregistrements**.
    
5. In the **Create Record Set** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** and **Routing Policy** values from the drop-down lists.) 
    
    > [!TIP]
    > The quotation marks required by the onscreen instructions are supplied automatically. You don't need to type them manually. 
  
|||||||
|:-----|:-----|:-----|:-----|:-----|:-----|
|**Name** <br/> |**Type** <br/> |**Alias** <br/> |**TTL (Seconds) (Durée de vie (secondes))** <br/> |**Value (Valeur)** <br/> |**Routing Policy (Stratégie de routage)** <br/> |
|(Laissez ce champ vide)  <br/> |TXT - Text  <br/> |Non  <br/> |300  <br/> |MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)  <br/>  |Simple <br/> |
   
6. Sélectionnez **Créer**.
    
7. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
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
  
1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
2. Sur la page **ressources** , sélectionnez **zones hébergées**.
    
3. Dans la page **zones hébergées** , dans la colonne **nom de domaine** , sélectionnez le nom du domaine à modifier. 
    
4. Sélectionnez le jeu d'enregistrement **Serveur de noms**. 
    
    ![Select the recordset](../../media/24e618e4-0a16-43a2-9886-f4f5dac79374.png)
  
5. Dans le jeu d'enregistrements **NS - Serveur de noms**, dans la zone **Valeur**, supprimez tous les serveurs de noms en les sélectionnant, puis en appuyant sur la touche **Suppr** du clavier. 
    
    > [!CAUTION]
    > Follow these steps only if you have existing nameservers other than the four correct nameservers. (Autrement dit, supprimez uniquement les serveurs de noms en cours qui *ne sont pas* nommés **NS1.BDM.microsoftonline.com**, **ns2.BDM.microsoftonline.com**, **NS3.BDM.microsoftonline.com**ou **NS4.BDM.microsoftonline.com**.) 
  
    ![Select and delete all of the nameservers in the Value box](../../media/ecf1e897-fa7d-4abc-b00b-bf55b8ed2139.png)
  
6. Dans la zone **TTL (secondes) :** , sélectionnez **1H** (1 heure). 
    
    ![Sélectionner 1H pour une heure](../../media/c70070e1-4bde-41a7-b271-9d22c475edf6.png)
  
7. Toujours dans le jeu d'enregistrements **NS - Serveur de noms**, dans la zone **Valeur**, tapez ou copiez-collez la valeur de la **première ligne** du tableau suivant, appuyez sur la touche **Entrée** du clavier, puis tapez ou copiez-collez la valeur de la **ligne** suivante. 
    
    > [!IMPORTANT]
    > Chaque valeur de serveur de noms  *doit*  figurer sur sa propre ligne distincte dans la zone **Valeur**, comme dans l'illustration suivante. 
  
|||
|:-----|:-----|
|**Première ligne** <br/> |ns1.bdm.microsoftonline.com.  <br/> **This value MUST end with a period (.)** <br/> |
|**Deuxième ligne** <br/> |ns2.bdm.microsoftonline.com.  <br/> **This value MUST end with a period (.)** <br/> |
|**Troisième ligne** <br/> |ns3.bdm.microsoftonline.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
|**Quatrième ligne** <br/> |ns4.bdm.microsoftonline.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
   
   ![Tapez ou collez la valeur de la première ligne dans la zone valeur.](../../media/b63f41e0-51ef-4ab2-a4b8-ee7380e5ab35.png)
  
8. Sélectionnez **enregistrer le jeu d’enregistrements**.
    
    ![Sélectionnez Enregistrer le jeu d’enregistrements](../../media/ab3c0558-bb7c-41e4-871e-ea82f1553476.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine. 
