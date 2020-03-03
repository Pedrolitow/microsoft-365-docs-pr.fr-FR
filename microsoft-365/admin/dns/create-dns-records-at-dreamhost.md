---
title: Créer des enregistrements DNS sur Dreamhost pour Office 365
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
ms.assetid: 9c0812e0-908b-4b41-a64b-77f0dbd3db7a
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur Dreamhost pour Office 365.
ms.openlocfilehash: 201452bc68f82138c08e2054452747a900ed0e6b
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42349485"
---
# <a name="create-dns-records-at-dreamhost-for-office-365"></a>Créer des enregistrements DNS sur Dreamhost pour Office 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si DreamHost est votre fournisseur d’hébergement DNS, suivez la procédure décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Lync, etc.
 
Une fois ces enregistrements ajoutés sur DreamHost, votre domaine est configuré pour utiliser les services Office 365.
  
Pour en savoir plus sur l'hébergement web et le DNS pour les sites web avec Office 365, voir [Utiliser un site web public avec Office 365](https://support.office.com/article/a8178510-501d-4bd8-9921-b04f2e9517a5.aspx).
  
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur DreamHost à l’aide de [ce lien](https://panel.dreamhost.com/). Vous serez invité à vous connecter.
    
    ![Dreamhost-BP-configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. Sur la page **tableau de bord** , sélectionnez **domaines**, puis gérer les **domaines**.
    
    ![Dreamhost-BP-configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. Dans la page **gérer les domaines** , dans la section **domaine** , sélectionnez **DNS** pour le domaine à modifier. 
    
    ![Dreamhost-BP-configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (You may have to scroll down.)
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Nom**|**Type**|**Valeur**|**Comment**|
    |:-----|:-----|:-----|:-----|
    |(Leave this field empty.)  <br/> |TXT  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |(Ce champ est facultatif.)  <br/> |
   
   ![Dreamhost-BP-Verify-1-1](../../media/ed4a7d43-eeeb-4ec8-849c-37f81315dc69.png)
  
5. Sélectionnez **Ajouter un enregistrement maintenant.**
    
    ![Dreamhost-BP-Verify-1-2](../../media/5b89c89b-3a8e-4624-895a-86f3cc4638f6.png)
  
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Office 365 et demandez à Office 365 de rechercher l’enregistrement.
  
Lorsqu’Office 365 trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
    
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  

  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365
<a name="BKMK_add_MX"> </a>

Suivez la procédure ci-dessous.
  
1. Pour commencer, accédez à la page de vos domaines sur DreamHost à l’aide de [ce lien](https://panel.dreamhost.com/). Vous serez invité à vous connecter.
    
    ![Dreamhost-BP-configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. Sur la page **tableau de bord** , sélectionnez **courrier**, puis **MX personnalisé**.
    
    ![Dreamhost-BP-configure-2-1](../../media/58478679-4018-49cc-9d83-371dc5fa4a22.png)
  
3. Dans la section **gérer la remise du courrier** , dans la colonne **actions** , sélectionnez **modifier** pour le domaine à modifier. 
    
    ![Dreamhost-BP-configure-2-2](../../media/6eed0be2-6477-4f49-9f90-39e190499a53.png)
  
4. Dans la section **enregistrement MX personnalisé** , dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes du tableau suivant. 
    
    (You may have to scroll down.)
    
    (S’il existe d’autres enregistrements MX existants, marquez-les comme devant être supprimés.)
    
    |**Enregistrement MX (obligatoire)**|
    |:-----|
    |0  *\<clé_de_domaine\>*  .mail.protection.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> La valeur 0 est la valeur de priorité Max. Ajoutez-la au début de la valeur MX, séparée du reste de la valeur par une espace.  <br/> **Remarque :** Obtenez votre * \<clé\> de domaine* à partir de votre compte Office 365.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Dreamhost-BP-configure-2-3](../../media/90da1816-e186-4016-ab22-7962f8b86add.png)
  
5. Sélectionnez **modifier ce domaine pour utiliser des enregistrements MX personnalisés maintenant !**
    
    ![Dreamhost-BP-configure-2-4](../../media/3221c767-83d3-4f30-9d08-dc998772d2a3.png)
  
6. S’il existe d’autres enregistrements MX, supprimez chaque enregistrement en sélectionnant l’entrée et en appuyant sur la touche **Suppr** du clavier. 
    
    ![Dreamhost-BP-configure-2-5](../../media/1827733c-3609-4b0f-bba1-531ab090da91.png)
  
7. Si vous avez supprimé des enregistrements, sélectionnez **mettre à jour vos enregistrements MX personnalisés maintenant !**
    
    ![Dreamhost-BP-configure-2-6](../../media/177462be-0686-47b7-a389-025dfc8d6526.png)

  
## <a name="add-the-six-cname-records-that-are-required-for-office-365"></a>Ajouter les 6 enregistrements CNAME requis pour Office 365
<a name="BKMK_add_CNAME"> </a>

Suivez la procédure ci-dessous.
  
1. Pour commencer, accédez à la page de vos domaines sur DreamHost à l’aide de [ce lien](https://panel.dreamhost.com/). Vous serez invité à vous connecter.
    
    ![Dreamhost-BP-configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. Sur la page **tableau de bord** , sélectionnez **domaines**, puis gérer les **domaines**.
    
    ![Dreamhost-BP-configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. Dans la page **gérer les domaines** , dans la section **domaine** , sélectionnez **DNS** pour le domaine à modifier. 
    
    ![Dreamhost-BP-configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. Dans la section **Ajouter un enregistrement DNS personnalisé** , dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne dans le tableau suivant. 
    
    (You may have to scroll down.)
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Nom**|**Type**|**Valeur**|**Comment**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |autodiscover.outlook.com.  <br/> **This value MUST end with a period (.)** <br/> |(Ce champ est facultatif.)  <br/> |
    |sip  <br/> |CNAME  <br/> |sipdir.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |(Ce champ est facultatif.)  <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |webdir.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |(Ce champ est facultatif.)  <br/> |
    |enterpriseregistration  <br/> |CNAME  <br/> |enterpriseregistration.windows.net.  <br/> **This value MUST end with a period (.)** <br/> |(Ce champ est facultatif.)  <br/> |
    |enterpriseenrollment  <br/> |CNAME  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **This value MUST end with a period (.)** <br/> |(Ce champ est facultatif.)  <br/> |
   
    ![Dreamhost-BP-configure-3-1](../../media/0c4cc587-ea24-47f2-8dc6-a35735b250e6.png)
  
5. Sélectionnez **Ajouter un enregistrement maintenant.**
    
    ![Dreamhost-BP-configure-3-2](../../media/b5d4f939-de6d-4d1f-a20a-4eb5fe715281.png)
  
6. À l’aide des deux étapes précédentes et des valeurs des cinq autres lignes du tableau, ajoutez chacun des cinq autres enregistrements CNAMe.

  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. If you already have an SPF record for your domain, don't create a new one for Office 365. Ajoutez plutôt les valeurs Office 365 requises à l'enregistrement actuel de manière à n'avoir qu'un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs.
  
Suivez la procédure ci-dessous.
  
1. Pour commencer, accédez à la page de vos domaines sur DreamHost à l’aide de [ce lien](https://panel.dreamhost.com/). Vous serez invité à vous connecter.
    
    ![Dreamhost-BP-configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. Sur la page **tableau de bord** , sélectionnez **domaines**, puis gérer les **domaines**.
    
    ![Dreamhost-BP-configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. Dans la page **gérer les domaines** , dans la section **domaine** , sélectionnez **DNS** pour le domaine à modifier. 
    
    ![Dreamhost-BP-configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. Dans la section **Ajouter un enregistrement DNS personnalisé** , dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne dans le tableau suivant. 
    
    (You may have to scroll down.)
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Nom**|**Type**|**Valeur**|**Comment**|
    |:-----|:-----|:-----|:-----|
    |(Leave this field empty.)  <br/> |TXT  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |(Ce champ est facultatif.)  <br/> |
   
   ![Dreamhost-BP-configure-4-1](../../media/cbc4bbca-bdbc-4dc9-b1b7-b55491eb1e53.png)
  
5. Sélectionnez **Ajouter un enregistrement maintenant.**
    
    ![Dreamhost-BP-configure-4-2](../../media/2bd7cae8-1fbc-4407-8dfa-06ce37c586c0.png)
  
6. À l’aide des deux étapes précédentes et des valeurs de la deuxième ligne du tableau, ajoutez l’autre enregistrement SRV.
    
  
## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>Ajoutez les 2 enregistrements SRV requis pour Office 365
<a name="BKMK_add_SRV"> </a>

Suivez la procédure ci-dessous.
  
1. Pour commencer, accédez à la page de vos domaines sur DreamHost à l’aide de [ce lien](https://panel.dreamhost.com/). Vous serez invité à vous connecter.
    
    ![Dreamhost-BP-configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. Sur la page **tableau de bord** , sélectionnez **domaines**, puis gérer les **domaines**.
    
    ![Dreamhost-BP-configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. Dans la page **gérer les domaines** , dans la section **domaine** , sélectionnez **DNS** pour le domaine à modifier. 
    
    ![Dreamhost-BP-configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. Dans la section **Ajouter un enregistrement DNS personnalisé** , dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne dans le tableau suivant. 
    
    (You may have to scroll down.)
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Nom**|**Type**|**Valeur**|**Comment**|
    |:-----|:-----|:-----|:-----|
    |_sip. _tls  <br/> |SRV  <br/> |100 1 443  <br/> sipdir.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |(Ce champ est facultatif.)  <br/> |
    |_sipfederationtls. _tcp  <br/> |SRV  <br/> |100 1 5061  <br/> sipfed.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |(Ce champ est facultatif.)  <br/> |
   
    ![Dreamhost-BP-configure-5-1](../../media/934eb79f-3617-4b72-802c-c42c7d165283.png)
  
5. Sélectionnez **Ajouter un enregistrement maintenant**.
    
    ![Dreamhost-BP-configure-5-2](../../media/015bc73c-8f88-49ce-87f9-e5a6ea3e10a8.png)
  
6. À l’aide des deux étapes précédentes et des valeurs de la deuxième ligne du tableau, ajoutez l’autre enregistrement SRV.
    
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

  
