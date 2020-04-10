---
title: Modifier les serveurs de noms pour configurer Office 365 avec NameCheap
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
ms.assetid: 84f467f6-28cf-40f0-94d0-a2a27ddfc2e7
description: 'Apprenez à configurer votre domaine personnalisé Office 365 avec NameCheap si vous souhaitez qu’Office 365 gère vos enregistrements DNS. '
ms.openlocfilehash: 1130f8aca0f2d014d73f5a1b2e2edb2785a7c6b8
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43212316"
---
# <a name="change-nameservers-to-set-up-office-365-with-namecheap"></a>Modifier les serveurs de noms pour configurer Office 365 avec NameCheap

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez.
  
Suivez ces instructions si vous voulez laisser le soin à Office 365 de gérer vos enregistrements DNS Office 365 à votre place. (Si vous préférez, vous pouvez [gérer tous vos enregistrements DNS Office 365 sur NameCheap](create-dns-records-at-namecheap.md).)
  
    
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

1. Pour commencer, accédez à la page de vos domaines sur NameCheap à l’aide de [ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à continuer.
    
    ![NameCheap-BP-configure-1-1](../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png)
  
2. Sur la page d' **Accueil** , sous **compte**, sélectionnez **liste de domaines** dans la liste déroulante. 
    
    ![NameCheap-BP-configure-1-2](../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png)
  
3. Dans la page **liste des domaines** , recherchez le nom du domaine que vous souhaitez modifier, puis sélectionnez **gérer**.
    
    ![NameCheap-BP-configure-1-3](../../media/fb2020d8-707c-4148-835e-304ac6244d66.png)
  
4. Sélectionnez **DNS avancé**.
    
    ![NameCheap-BP-configure-1-4](../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png)
  
5. Dans la section **Host Records (enregistrements d’hôte** ), sélectionnez **Add New Record (ajouter un nouvel enregistrement**).
    
    ![NameCheap-BP-configure-1-5](../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png)
  
6. Dans la liste déroulante **type** , sélectionnez **enregistrement txt**.
    
    > [!NOTE]
    > La liste déroulante **type** s’affiche automatiquement lorsque vous sélectionnez **Ajouter un nouvel enregistrement**.
  
    ![NameCheap-BP-Verify-1-1](../../media/a5b40973-19b5-4c32-8e1b-1521aa971836.png)
  
7. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (Choisissez la valeur **TTL (durée de vie** ) dans la liste déroulante.) 
    
|**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
|:-----|:-----|:-----|:-----|
|TXT  <br/> |@  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque**: Voici un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |30 min  <br/> |
   
   ![NameCheap-BP-Verify-1-2](../../media/fe75c0fd-f85c-4bef-8068-edaf9779b7f1.png)
  
8. Sélectionnez le contrôle **enregistrer les modifications** (coche). 
    
    ![NameCheap-BP-Verify-1-3](../../media/b48d2c67-66b5-4aa4-8e59-0c764f236fac.png)
  
9. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Office 365 et demandez à Office 365 de rechercher l’enregistrement.
  
Lorsqu’Office 365 trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
    
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

Pour finaliser la configuration de votre domaine avec Office 365, vous devez modifier les enregistrements de serveur de noms auprès de votre bureau d'enregistrement de domaines afin qu'ils pointent vers les serveurs de noms principal et secondaire Office 365. Office 365 est ainsi informé qu'il doit mettre à jour les enregistrements DNS du domaine pour vous. Pour finaliser la configuration, nous ajouterons tous les enregistrements de façon à ce que vous puissiez utiliser la messagerie, Skype Entreprise Online et votre site web public avec votre domaine.
  
> [!CAUTION]
> Lorsque vous modifiez les enregistrements de serveur de noms de votre domaine de façon à ce qu'ils pointent vers les serveurs de noms Office 365, tous les services actuellement associés à votre domaine sont affectés. Par exemple, les messages envoyés à votre domaine (tel que thomas@ *votre_domaine*  .com) arriveront dans Office 365 une fois cette modification appliquée. 
  
> [!IMPORTANT]
>  Une fois les étapes décrites dans cette section accomplies, les  *seuls*  serveurs de noms qui doivent être répertoriés sont les quatre suivants : >  ns1.bdm.microsoftonline.com >  ns2.bdm.microsoftonline.com >  ns3.bdm.microsoftonline.com >  ns4.bdm.microsoftonline.com >  La procédure suivante décrit comment supprimer tout autre serveur de noms indésirable de la liste, et y ajouter les serveurs de noms  *corrects*  qui n'y figurent pas encore. 
  
1. Pour commencer, accédez à la page de vos domaines sur NameCheap à l’aide de [ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à continuer.
    
    ![NameCheap-BP-configure-1-1](../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png)
  
2. Sur la page d' **Accueil** , sous **compte**, sélectionnez **liste de domaines** dans la liste déroulante. 
    
    ![NameCheap-BP-configure-1-2](../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png)
  
3. Dans la page **liste des domaines** , recherchez le nom du domaine que vous souhaitez modifier, puis sélectionnez **gérer**.
    
    ![NameCheap-BP-configure-1-3](../../media/fb2020d8-707c-4148-835e-304ac6244d66.png)
  
4. Sélectionnez **domaine**.
    
    ![NameCheap-BP-redelegate-1-1](../../media/59588406-794e-4ae4-8526-35e3111b5791.png)
  
5. Recherchez la section serveurs de **noms** , puis sélectionnez **personnalisée** dans la liste déroulante **NameCheap par défaut** . 
    
    ![NameCheap-BP-redelegate-1-2](../../media/7df56295-fdb3-472f-9442-13f780c2c93e.png)
  
6. Selon qu’il y a déjà ou non des serveurs de noms répertoriés dans la page qui s’affiche maintenant, passez à l’une des deux procédures suivantes.
    
### <a name="if-there-are-no-nameservers-already-listed"></a>Si AUCUN serveur de noms n'est encore répertorié
<a name="BKMK_ProcedureWithOUT"> </a>

1. Sélectionnez **Ajouter** un serveur de noms à deux reprises pour ajouter deux nouvelles lignes.
    
    ![NameCheap-BP-redelegate-1-3-1](../../media/e8816bf5-bb59-49d5-bfca-43e502242dc3.png)
  
2. Dans les zones serveur de **noms** , tapez ou copiez-collez les valeurs du tableau suivant.
    
|||
|:-----|:-----|
|**Nameserver 1 (Serveur de noms 1)** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Nameserver 2 (Serveur de noms 2)** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**Nameserver 3 (Serveur de noms 3)** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Nameserver 4 (Serveur de noms 4)** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![NameCheap-BP-redelegate-1-3-2](../../media/21d681b7-4f96-4e96-ac27-9534c388537c.png)
  
3. Sélectionnez le contrôle **Enregistrer** (case à cocher). 
    
    ![NameCheap-BP-redelegate-1-5](../../media/07aaf1e5-c24f-4c51-bfe0-f99868b3bf35.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine. 
  
### <a name="if-there-are-nameservers-already-listed"></a>Si DES serveurs de noms sont déjà répertoriés

> [!CAUTION]
> Suivez ces étapes  *uniquement*  si vous avez des serveurs de noms existants autres que les quatre serveurs de noms  *corrects*  . Autrement dit, ne supprimez  *que*  les serveurs de noms  *qui ne sont pas*  nommés **ns1.bdm.microsoftonline.com**, **ns2.bdm.microsoftonline.com**, **ns3.bdm.microsoftonline.com** ou **ns4.bdm.microsoftonline.com**. 
  
1. Si d’autres serveurs de noms sont répertoriés dans les zones serveur de **noms** , supprimez-les en les sélectionnant et en appuyant sur la touche **Suppr** du clavier. 
    
    ![NameCheap-BP-redelegate-1-4](../../media/3270603a-c4f4-40b7-acad-733d56e2f53c.png)
  
2. Sélectionnez **Ajouter** un serveur de noms à deux reprises pour ajouter deux nouvelles lignes. 
    
    ![NameCheap-BP-redelegate-1-3-1](../../media/e8816bf5-bb59-49d5-bfca-43e502242dc3.png)
  
3. Dans les zones serveur de **noms** , tapez ou copiez-collez les valeurs du tableau suivant.
 
    
|||
|:-----|:-----|
|**Name Server 1 (Serveur de noms 1)** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Name Server 2 (Serveur de noms 2)** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**Nameserver 3 (Serveur de noms 3)** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Nameserver 4 (Serveur de noms 4)** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![NameCheap-BP-redelegate-1-3-2](../../media/21d681b7-4f96-4e96-ac27-9534c388537c.png)
  
4. Sélectionnez le contrôle **Enregistrer** (case à cocher). 
    
    ![NameCheap-BP-redelegate-1-5](../../media/07aaf1e5-c24f-4c51-bfe0-f99868b3bf35.png)
  
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine.
