---
title: Créer des enregistrements DNS sur OVH pour Microsoft
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
ms.assetid: 5176feef-36dc-4d84-842f-1f2b5a21ba96
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur OVH pour Microsoft.
ms.openlocfilehash: 14c3796ff6686ae0d98ec32ec6ddf6afc004a3c3
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49657778"
---
# <a name="create-dns-records-at-ovh-for-microsoft"></a>Créer des enregistrements DNS sur OVH pour Microsoft

[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml) si vous ne trouvez pas ce que vous recherchez. 
  
Si OVH est votre fournisseur d’hébergement DNS, suivez la procédure décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online, etc.
  
Voici les principaux enregistrements à ajouter. 
  
- [Créer des enregistrements DNS sur OVH pour Microsoft](#create-dns-records-at-ovh-for-microsoft)
    
- [Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft](#add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft)
    
- [Ajouter les enregistrements CNAME requis pour Microsoft](#add-the-cname-records-that-are-required-for-microsoft)
    
- [Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable](#add-a-txt-record-for-spf-to-help-prevent-email-spam)
    
- [Ajoutez les deux enregistrements SRV requis pour Microsoft](#add-the-two-srv-records-that-are-required-for-microsoft)
    
Une fois ces enregistrements ajoutés sur OVH, votre domaine est configuré pour utiliser les services Microsoft.

  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="bkmk_txt"> </a>

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines dans OVH à l’aide de [ce lien](https://www.ovh.com/manager/). You'll be prompted to log in.
    
    ![Connexion OVH](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
2. Sous **domaines**, sélectionnez le nom du domaine à modifier.
    
    ![OVH sélectionnez le domaine](../../media/fe407909-4ea6-4b92-a3bd-dec4022b1d8d.png)
  
3. Sélectionnez **zone DNS**.
    
    ![OVH sélectionner une zone DNS](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
4. Sélectionnez **Ajouter une entrée**.
    
    ![OVH ajouter une entrée](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
5. Sélectionnez **txt**
    
    ![OVH Select TXT Entry](../../media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. Pour affecter une valeur de durée de vie, sélectionnez **personnalisée** dans la liste déroulante, puis tapez la valeur dans la zone de texte. 
    
    |**Type d'enregistrement**|**Sous-domaine**|**TTL (Durée de vie)**|**Value (Valeur)**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |(Laisser vide)  <br/> |3600 (secondes)  <br/> |MS = msxxxxxxxx  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
7. Sélectionnez  **Confirmer**. 
    
    ![OVH confirmer le TXT pour vérification](../../media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png)
  
8. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
    
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
<a name="bkmk_mx"> </a>

1. Pour commencer, accédez à la page de vos domaines dans OVH à l’aide de [ce lien](https://www.ovh.com/manager/). You'll be prompted to log in.
    
    ![Connexion OVH](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
2. Sous **domaines**, sélectionnez le nom du domaine à modifier.
    
    ![OVH sélectionnez le domaine](../../media/fe407909-4ea6-4b92-a3bd-dec4022b1d8d.png)
  
3. Sélectionnez **zone DNS**.
    
    ![OVH sélectionner une zone DNS](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
4. Sélectionnez **Ajouter une entrée**.
    
    ![OVH ajouter une entrée](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
5. Sélectionnez **MX**.
    
    ![Type d’enregistrement MX OVH](../../media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. Pour affecter une valeur de durée de vie, sélectionnez **personnalisée** dans la liste déroulante, puis tapez la valeur dans la zone de texte. 
    
    > [!NOTE]
    > Par défaut OVH utilise la notation relative pour la cible, qui ajoute le nom de domaine à la fin de l’enregistrement cible. Pour utiliser la notation absolue, ajoutez un point à l’enregistrement cible comme indiqué dans le tableau ci-dessous. 
  
    |**Type d'enregistrement**|**Sous-domaine**|**TTL (Durée de vie)**|**Priority (Priorité)**|**Target**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX  <br/> |(Laisser vide)  <br/> |3600 (secondes)  <br/> |10   <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq). <br/> |\<domain-key\>. mail.protection.outlook.com.  <br/> **Remarque :** Obtenir votre  *\<domain-key\>*  à partir de votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)  |
   
    ![Enregistrement MX OVH pour le courrier électronique](../../media/6e2f5655-93e2-4620-8f19-c452e7edf8f0.png)
  
7. Sélectionnez **Suivant**.
    
    ![Enregistrement MX OVH sélectionnez suivant](../../media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png)
  
8. Sélectionnez  **Confirmer**.
    
    ![Enregistrement MX OVH sélectionnez confirmer](../../media/090bfb11-a753-4af0-8982-582a4069a169.png)
  
9. S’il existe d’autres enregistrements MX, supprimez-les tous dans la liste de la page **zone DNS** . Sélectionnez chaque enregistrement, puis, dans la colonne **actions** , sélectionnez l’icône Corbeille-peut-être **supprimée** . 
    
    ![OVH supprimer un enregistrement MX](../../media/892b328b-7057-4828-b8c5-fe26284dc8c2.png)
  
10. Sélectionnez  **Confirmer**.
    
## <a name="add-the-cname-records-that-are-required-for-microsoft"></a>Ajouter les enregistrements CNAME requis pour Microsoft
<a name="bkmk_cname"> </a>

1. Pour commencer, accédez à la page de vos domaines dans OVH à l’aide de [ce lien](https://www.ovh.com/manager/). You'll be prompted to log in.
    
    ![Connexion OVH](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
2. Sous **domaines**, sélectionnez le nom du domaine à modifier.
    
    ![OVH sélectionnez le domaine](../../media/fe407909-4ea6-4b92-a3bd-dec4022b1d8d.png)
  
3. Sélectionnez **zone DNS**.
    
    ![OVH sélectionner une zone DNS](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
4. Sélectionnez **Ajouter une entrée**.
    
    ![OVH ajouter une entrée](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
5. Sélectionnez **CNAME**.
    
    ![OVH ajouter un type d’enregistrement CNAMe](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)
  
6. Créez le premier enregistrement CNAME.
    
    Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. Pour affecter une valeur de durée de vie, sélectionnez **personnalisée** dans la liste déroulante, puis tapez la valeur dans la zone de texte. 
    
    |**Type d'enregistrement**|**Sous-domaine**|**Target (Cible)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover  <br/> |autodiscover.outlook.com.  <br/> |3600 secondes  <br/> |
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> |3600 secondes  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> |3600 secondes  <br/> |
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> |3600 secondes  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> |3600 secondes  <br/> |
   
    ![Enregistrement CNAMe OVH](../../media/516938b3-0b12-4736-a631-099e12e189f5.png)
  
7. Sélectionnez **Suivant**.
    
    ![OVH ajouter des valeurs CNAMe et sélectionner suivant](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
8. Sélectionnez  **Confirmer**.
    
9. Répétez les étapes précédentes pour créer les cinq autres enregistrements CNAMe.
    
    Pour chaque enregistrement, tapez ou copiez-collez les valeurs de la ligne suivante du tableau ci-dessus dans les zones de cet enregistrement.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="bkmk_spf"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
1. Pour commencer, accédez à la page de vos domaines dans OVH à l’aide de [ce lien](https://www.ovh.com/manager/). You'll be prompted to log in.
    
    ![Connexion OVH](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
2. Sous **domaines**, sélectionnez le nom du domaine à modifier.
    
    ![OVH sélectionnez le domaine](../../media/fe407909-4ea6-4b92-a3bd-dec4022b1d8d.png)
  
3. Sélectionnez **zone DNS**.
    
    ![OVH sélectionner une zone DNS](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
4. Sélectionnez **Ajouter une entrée**.
    
    ![OVH ajouter une entrée](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
5. Sélectionnez **txt**.
    
6. In the boxes for the new record, type or copy and paste the following values.
    
    |**Type d'enregistrement**|**Sous-domaine**|**TTL (Durée de vie)**|**VALEUR TXT**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |(Laisser vide)  <br/> |3600 (secondes)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![OVH ajouter un enregistrement TXT pour SPF](../../media/f50466e9-1557-4548-8a39-e98978a5ee2e.png)
  
7. Sélectionnez **Suivant**.
    
    ![OVH ajouter un enregistrement TXT pour SPF et sélectionner suivant](../../media/7937eb7c-114f-479f-a916-bcbe476d6108.png)
  
8. Sélectionnez  **Confirmer**.
    
    ![OVH ajouter un enregistrement TXT pour SPF et confirmer](../../media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft
<a name="bkmk_srv"> </a>

1. Pour commencer, accédez à la page de vos domaines dans OVH à l’aide de [ce lien](https://www.ovh.com/manager/). You'll be prompted to log in.
    
    ![Connexion OVH](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
2. Sous **domaines**, sélectionnez le nom du domaine à modifier.
    
    ![OVH sélectionnez le domaine](../../media/fe407909-4ea6-4b92-a3bd-dec4022b1d8d.png)
  
3. Sélectionnez **zone DNS**.
    
    ![OVH sélectionner une zone DNS](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
4. Sélectionnez **Ajouter une entrée**.
    
    ![OVH ajouter une entrée](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
5. Sélectionnez **SRV**.
    
    ![OVH sélectionner un type d’enregistrement SRV](../../media/66bad536-a531-4a4e-b08d-c0d99f6ea1b2.png)
  
6. Créez le premier enregistrement SRV.
    
    Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. Pour affecter une valeur de durée de vie, sélectionnez **personnalisée** dans la liste déroulante, puis tapez la valeur dans la zone de texte. 
    
    |**Type d'enregistrement**|**Sous-domaine**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**TTL (Durée de vie)**|**Target**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV (Service)  <br/> |_sip._tls  <br/> |100  <br/> |1   <br/> |443  <br/> |3600 (secondes)  <br/> |sipdir.online.lync.com.  <br/> |
    |SRV (Service)  <br/> |_sipfederationtls._tcp  <br/> |100  <br/> |1   <br/> |5061  <br/> |3600 (secondes)  <br/> |sipfed.online.lync.com.  <br/> |
       
    ![Enregistrement SRV OVH](../../media/73956b9e-9e4f-40a5-803e-c4ead2f77fa6.png)
  
7. Sélectionnez **Suivant**.
    
    ![Enregistrement SRV OVH sélectionner suivant](../../media/cb4ad7e2-a8f0-4ab1-9797-d1b51c1d2da9.png)
  
8. Sélectionnez  **Confirmer**.
    
9. Répétez les étapes précédentes pour créer l’autre enregistrement SRV. Tapez ou copiez-collez les valeurs de la deuxième ligne du tableau ci-dessus dans les zones du deuxième enregistrement.
    
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
