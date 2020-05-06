---
title: Créer des enregistrements DNS sur le point de suspension pour Microsoft
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
ms.assetid: 46ab4b10-6857-44b1-b08d-d1b5f45a69c6
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online et d’autres services sur le point de contrôle de Microsoft.
ms.openlocfilehash: 4779b8f6fadcd4b134d3954d2c6c133da40c19e6
ms.sourcegitcommit: 5476c2578400894640ae74bfe8e93c3319f685bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44048986"
---
# <a name="create-dns-records-at-hover-for-microsoft"></a>Créer des enregistrements DNS sur le point de suspension pour Microsoft

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Hover est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
     
Une fois ces enregistrements ajoutés sur pointage, votre domaine est configuré pour utiliser les services Microsoft.
  

  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
Suivez les étapes ci-dessous ou [regardez la vidéo](https://support.office.com/article/Video-Create-DNS-records-at-Hover-for-Office-365-182bd58e-8fe4-4717-9233-3a3546b72ad2?ui=en-US&amp;rs=en-US&amp;ad=US)
  
1. Pour commencer, accédez à la page de vos domaines sur Hover à l'aide de [ce lien](https://www.hover.com/domains). Vous serez invité à vous connecter.
    
    ![Connexion](../../media/f608cfaa-4962-46a1-a469-89010494e4be.png)
  
2. Sous **gérer vos domaines**, sélectionnez le nom du domaine à modifier.
    
    ![Sélectionner un domaine](../../media/ae7c1c46-7ad5-467a-b41c-077c90018989.png)
  
3. Sélectionnez l’onglet **DNS** . 
    
    ![Sélectionnez l’onglet DNS](../../media/bd727fb4-0b06-426d-9387-42a160aead42.png)
  
4. Sélectionnez **Ajouter un nouveau**.
    
    ![Sélectionnez Ajouter un nouveau](../../media/66d6b2c9-741e-40e0-a096-6e7e204d655d.png)
  
5. In the boxes for the new record, select **TXT** for the **Record Type**, and then type or copy and paste the values from the following table.
    
    ||||
    |:-----|:-----|:-----|
    |Hostname (Nom d'hôte)  <br/> |Type d’enregistrement  <br/> |Value (Valeur)  <br/> |
    |@  <br/> |TXT  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Tapez ou copiez-collez les valeurs DNS](../../media/3b0d19f9-4138-47a7-aab2-137ad120ded6.png)
  
6. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer.](../../media/07dcf68e-34be-47dc-999e-0216de68cc9c.png)
  
7. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Microsoft 365 et demandez à Microsoft 365 de rechercher l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
    
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
<a name="BKMK_add_MX"> </a>

Suivez les étapes ci-dessous ou [regardez la vidéo](https://support.office.com/article/Video-Create-DNS-records-at-Hover-for-Office-365-182bd58e-8fe4-4717-9233-3a3546b72ad2?ui=en-US&amp;rs=en-US&amp;ad=US)
  
1. Pour commencer, accédez à la page de vos domaines sur Hover à l'aide de [ce lien](https://www.hover.com/domains). Vous serez invité à vous connecter.
    
    ![Connexion](../../media/f608cfaa-4962-46a1-a469-89010494e4be.png)
  
2. Sous **gérer vos domaines**, sélectionnez le nom du domaine à modifier.
    
    ![Sélectionner un domaine](../../media/ae7c1c46-7ad5-467a-b41c-077c90018989.png)
  
3. Sélectionnez l’onglet **DNS** . 
    
    ![Sélectionnez l’onglet DNS](../../media/bd727fb4-0b06-426d-9387-42a160aead42.png)
  
4. Sélectionnez **Ajouter un nouveau**.
    
    ![Sélectionnez Ajouter un nouveau](../../media/66d6b2c9-741e-40e0-a096-6e7e204d655d.png)
  
5. Dans les zones du nouvel enregistrement, sélectionnez le **Type d'enregistrement** **MX**, puis tapez ou copiez-collez les valeurs du tableau suivant.
    
    |**Hostname (Nom d'hôte)**|**Record Type (Type d'enregistrement)**|**Priority (Priorité)**|**Hostname (Nom d'hôte)**|
    |:-----|:-----|:-----|:-----|
    |@  <br/> |MX  <br/> |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq). <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenir votre * \<clé\> de domaine* à partir de votre compte Microsoft.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Tapez ou copiez-collez les valeurs DNS](../../media/2c8915fa-04a8-4d2a-a8ae-a79de0c8ef99.png)
  
6. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer.](../../media/266c30a4-6703-48fb-a919-b510ed966193.png)
  
7. S'il existe d'autres enregistrements MX, utilisez le processus en deux étapes suivant pour supprimer chacun d'eux :
    
    Tout d’abord, en plaçant le pointeur de la souris sur un enregistrement que vous souhaitez supprimer, sélectionnez **supprimer**.
    
    ![Pointez avec la souris et sélectionnez Supprimer.](../../media/2ddf4902-8cd2-4969-a418-2cb592741e86.png)
  
    Deuxièmement, sélectionnez **Oui** pour confirmer chaque suppression. 
    
    ![Sélectionnez Oui pour confirmer la suppression](../../media/48756bd5-0205-4c4d-9803-9246795dbf4a.png)
  
    Répétez cette procédure jusqu'à avoir supprimé tous les enregistrements MX à l'exception de celui que vous avez ajouté précédemment durant cette procédure.
    
## <a name="add-the-cname-records-that-are-required-for-microsoft"></a>Ajouter les enregistrements CNAME requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

Suivez les étapes ci-dessous ou [regardez la vidéo](https://support.office.com/article/Video-Create-DNS-records-at-Hover-for-Office-365-182bd58e-8fe4-4717-9233-3a3546b72ad2?ui=en-US&amp;rs=en-US&amp;ad=US)
  
1. Pour commencer, accédez à la page de vos domaines sur Hover à l'aide de [ce lien](https://www.hover.com/domains). Vous serez invité à vous connecter.
    
    ![Connexion](../../media/f608cfaa-4962-46a1-a469-89010494e4be.png)
  
2. Sous **gérer vos domaines**, sélectionnez le nom du domaine à modifier.
    
    ![Sélectionner un domaine](../../media/ae7c1c46-7ad5-467a-b41c-077c90018989.png)
  
3. Sélectionnez l’onglet **DNS** . 
    
    ![Sélectionnez l’onglet DNS](../../media/bd727fb4-0b06-426d-9387-42a160aead42.png)
  
4. Ajoutez le premier des six enregistrements CNAME.
    
    Sélectionnez **Ajouter un nouveau**.
    
    ![Sélectionnez Ajouter un nouveau](../../media/66d6b2c9-741e-40e0-a096-6e7e204d655d.png)
  
5. Dans les zones vides du nouvel enregistrement, sélectionnez le **Type d'enregistrement** **CNAME**, puis tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    |**Hostname (Nom d'hôte)**|**Record Type (Type d'enregistrement)**|**Target Host (Hôte cible)**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |autodiscover.outlook.com  <br/> |
    |sip  <br/> |CNAME  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |webdir.online.lync.com  <br/> |
    |enterpriseregistration  <br/> |CNAME  <br/> |enterpriseregistration.windows.net  <br/> |
    |enterpriseenrollment  <br/> |CNAME  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
   
    ![Tapez ou copiez-collez les valeurs DNS](../../media/6ae607f8-d26e-47f0-a0f2-3487d37e8c7f.png)
  
6. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer.](../../media/69aa3546-32de-4c17-a2e2-8c0cd133efaa.png)
  
7. En suivant les trois étapes précédentes et en utilisant les valeurs des cinq autres lignes du tableau, ajoutez les cinq autres enregistrements CNAME.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
Suivez les étapes ci-dessous ou [regardez la vidéo](https://support.office.com/article/Video-Create-DNS-records-at-Hover-for-Office-365-182bd58e-8fe4-4717-9233-3a3546b72ad2?ui=en-US&amp;rs=en-US&amp;ad=US)
  
1. Pour commencer, accédez à la page de vos domaines sur Hover à l'aide de [ce lien](https://www.hover.com/domains). Vous serez invité à vous connecter.
    
    ![Connexion](../../media/f608cfaa-4962-46a1-a469-89010494e4be.png)
  
2. Sous **gérer vos domaines**, sélectionnez le nom du domaine à modifier.
    
    ![Sélectionner un domaine](../../media/ae7c1c46-7ad5-467a-b41c-077c90018989.png)
  
3. Sélectionnez l’onglet **DNS** . 
    
    ![Sélectionnez l’onglet DNS](../../media/bd727fb4-0b06-426d-9387-42a160aead42.png)
  
4. Sélectionnez **Ajouter un nouveau**.
    
    ![Sélectionnez Ajouter un nouveau](../../media/66d6b2c9-741e-40e0-a096-6e7e204d655d.png)
  
5. In the boxes for the new record, select **TXT** for the **Record Type**, and then type or copy and paste the values from the following table.
    
    |**Hostname (Nom d'hôte)**|**Record Type (Type d'enregistrement)**|**Value (Valeur)**|
    |:-----|:-----|:-----|
    |@  <br/> |TXT  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/>**Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![Tapez ou copiez-collez les valeurs DNS](../../media/ed36b9e0-aaa9-45fb-804d-7d4e82ba0c7f.png)
  
6. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer.](../../media/13a395b9-e0e8-4393-b568-5f99b2da39da.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

Suivez les étapes ci-dessous ou [regardez la vidéo](https://support.office.com/article/Video-Create-DNS-records-at-Hover-for-Office-365-182bd58e-8fe4-4717-9233-3a3546b72ad2?ui=en-US&amp;rs=en-US&amp;ad=US)
  
1. Pour commencer, accédez à la page de vos domaines sur Hover à l'aide de [ce lien](https://www.hover.com/domains). Vous serez invité à vous connecter.
    
    ![Connexion](../../media/f608cfaa-4962-46a1-a469-89010494e4be.png)
  
2. Sous **gérer vos domaines**, sélectionnez le nom du domaine à modifier.
    
    ![Sélectionner un domaine](../../media/ae7c1c46-7ad5-467a-b41c-077c90018989.png)
  
3. Sélectionnez l’onglet **DNS** . 
    
    ![Sélectionnez l’onglet DNS](../../media/bd727fb4-0b06-426d-9387-42a160aead42.png)
  
4. Ajoutez le premier des deux enregistrements SRV.
    
    Sélectionnez **Ajouter un nouveau**.
    
    ![Sélectionnez Ajouter un nouveau](../../media/66d6b2c9-741e-40e0-a096-6e7e204d655d.png)
  
5. Dans les zones vides du nouvel enregistrement, sélectionnez le **Type d'enregistrement** **SRV**, puis tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    |**Hostname (Nom d'hôte)**|**Record Type (Type d'enregistrement)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip. _tls  <br/> |SRV  <br/> |100  <br/> |0,1  <br/> |443  <br/> |sipdir.online.lync.com  <br/> |
    |_sipfederationtls. _tcp  <br/> |SRV  <br/> |100  <br/> |0,1  <br/> |5061  <br/> |sipfed.online.lync.com  <br/> |
   
    ![Tapez ou copiez-collez les valeurs DNS](../../media/67562cd6-c598-4c37-af53-626f153c0197.png)
  
6. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer.](../../media/0d7ec216-9277-4709-b637-e94c8662730f.png)
  
7. À l'aide des trois étapes précédentes et des valeurs de la deuxième ligne du tableau, ajoutez l'autre enregistrement SRV.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
