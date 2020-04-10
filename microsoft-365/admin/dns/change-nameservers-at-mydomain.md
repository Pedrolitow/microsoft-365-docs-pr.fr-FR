---
title: Modifier les serveurs de noms de manière à configurer Office 365 avec MyDomain
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
ms.assetid: c5f6140a-4a12-401b-9bbd-7dfb0d6b0ba3
description: Découvrez comment configurer Office 365 pour gérer les enregistrements DNS de votre domaine personnalisé sur Mon_domaine.
ms.openlocfilehash: f88f0528caf2229441fd3e5364b53864b923099f
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43212044"
---
# <a name="change-nameservers-to-set-up-office-365-with-mydomain"></a>Modifier les serveurs de noms de manière à configurer Office 365 avec MyDomain

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez.
  
Si vous voulez laisser Office 365 gérer vos enregistrements DNS Office 365 à votre place, suivez ces instructions (si vous préférez, vous pouvez [gérer tous vos enregistrements DNS Office 365 via MyDomain](create-dns-records-at-mydomain.md)).
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site MyDomain en utilisant [ce lien](https://www.mydomain.com/controlpanel). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la rubrique **Mes favoris**, choisissez **Domaine central**.
    
3. Sous **Domaine**, sélectionnez le nom du domaine à modifier.
    
4. Sur la ligne de la **Vue d'ensemble**, choisissez **DNS**.
    
5. Dans la liste déroulante **Modifier**, sélectionnez **Enregistrement TXT/SPF**.
    
6. Sous **Content (Contenu)**, dans la zone du nouvel enregistrement, tapez ou copiez-collez la valeur du tableau suivant.
    
||
|:-----|
|**Content** <br/> |
|MS=ms *XXXXXXXX*  <br/> **Remarque**: Voici un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
7. Sélectionnez **Ajouter**.
    
8. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
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
> Lorsque vous modifiez les enregistrements de serveur de noms de votre domaine de façon à ce qu'ils pointent vers les serveurs de noms Office 365, tous les services actuellement associés à votre domaine sont affectés. Par exemple, tous les messages électroniques envoyés à votre domaine (par exemple, rob@ *your_domain.* com) commencera à Office 365 une fois cette modification apportée. 
  
> [!IMPORTANT]
> The following procedure will show you how to delete any other, unwanted nameservers from the list, and also how to add the correct nameservers if they are not already in the list. <br/> When you have completed the steps in this section, the only nameservers that should be listed are these four:
  
1. Pour commencer, accédez à la page de vos domaines sur le site MyDomain en utilisant [ce lien](https://www.mydomain.com/controlpanel). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la rubrique **Mes favoris**, choisissez **Domaine central**.
    
3. Sous **Domaine**, sélectionnez le nom du domaine à modifier.
    
4. Dans la ligne **vue d’ensemble** , sélectionnez serveurs de **noms**.
    
    ![Mondomaine-BP-redelegate-1-1](../../media/49e91235-44b5-46d6-a82e-8f11329db3d6.png)
  
5. Dans la section **Update Name Servers**, sélectionnez **Use different name servers**.
    
    ![Mondomaine-BP-redelegate-1-2-1](../../media/f869fb26-54dc-4b66-8378-a78a79b582bd.png)
  
6. Selon qu’il y a déjà ou non des serveurs de noms répertoriés dans la page qui s’affiche maintenant, passez à l’une des deux procédures suivantes.
    
### <a name="if-the-correct-nameservers-are-already-listed"></a>Si les serveurs de noms appropriés SONT déjà répertoriés

- Si les serveurs de noms corrects sont répertoriés, vous pouvez ignorer cette étape.
    
    ![Mondomaine-BP-redelegate-1-2-2](../../media/601f6a46-15bd-4a92-b792-ac628ff86628.png)
  
### <a name="if-the-correct-nameservers-are-not-already-listed"></a>Si les serveurs de noms corrects ne sont PAS répertoriés

> [!CAUTION]
> Follow these steps only if you have existing nameservers other than the four correct nameservers. (Autrement dit, supprimez uniquement les serveurs de noms en cours qui *ne sont pas* nommés **NS1.BDM.microsoftonline.com**, **ns2.BDM.microsoftonline.com**, **NS3.BDM.microsoftonline.com**ou **NS4.BDM.microsoftonline.com**.) 
  
1. Supprimez les serveurs de noms existants en sélectionnant chaque entrée du champ **Nameserver : (Serveur de noms :)**, puis en appuyant sur la touche **Suppr** de votre clavier. 
    
    ![Mondomaine-BP-redelegate-1-3-1](../../media/5024cd27-a2b1-42a2-99e4-5ceb5e6eddb9.png)
  
2. Sélectionnez **plus** deux fois pour ajouter deux nouvelles lignes de serveur de noms. 
    
    ![Mondomaine-BP-redelegate-1-3-2](../../media/19307893-2f73-4e4d-9221-a5870e09ab48.png)
  
3. Dans les zones des enregistrements, tapez ou copiez-collez les valeurs de serveur de noms du tableau suivant.
    
|||
|:-----|:-----|
|**Nameserver 1 (Serveur de noms 1)** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Nameserver 2 (Serveur de noms 2)** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**Nameserver 3 (Serveur de noms 3)** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Nameserver 4 (Serveur de noms 4)** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![Mondomaine-BP-redelegate-1-4](../../media/7427e99c-49c7-4a2e-a5bf-66fc46900cd1.png)
  
4. Cliquez sur **Enregistrer**.
    
    ![Mondomaine-BP-redelegate-1-5](../../media/48473816-b881-47f0-9344-74622efa3bf8.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine. 
