---
title: Créer des enregistrements DNS sur Freenom pour Microsoft
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
ms.assetid: d8ff45a2-19e3-413d-aa64-a9982bd6633c
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur Freenom pour Microsoft.
ms.openlocfilehash: a7ad45d3d785478966df5120567836200de316da
ms.sourcegitcommit: c7f11d851073ef14a69669f6c8b7e0c11e4bb7a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "43939226"
---
# <a name="create-dns-records-at-freenom-for-microsoft"></a>Créer des enregistrements DNS sur Freenom pour Microsoft

[Consultez le Forum aux questions sur les domaines](../setup/domains-faq.md) si vous ne trouvez pas ce que vous recherchez. 
  
> [!CAUTION]
> Le site Web Freenom ne prend pas en charge les enregistrements SRV, ce qui signifie que plusieurs fonctionnalités de Skype entreprise Online et d’Outlook Web App ne fonctionneront pas. Quelle que soit la planification Microsoft que vous utilisez, il existe des limitations de service importantes, et vous pouvez choisir d’utiliser un autre fournisseur d’hébergement DNS. 
  
Si malgré les limitations de service, vous choisissez de gérer vos propres enregistrements DNS Microsoft sur Freenom, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour la messagerie et d’autres services.
  
  
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="bkmk_txt"> </a>

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines dans Freenom à l’aide de [ce lien](https://my.freenom.com/). You'll be prompted to log in.
    
    ![Connexion Freenom](../../media/90a32855-bfdd-4dfe-881c-b9a36b2f0582.png)
  
2. Sélectionnez **services**, puis **My Domains**.
    
    ![Freenom sélectionner les services et mes domaines](../../media/1917ced2-e254-4aec-9096-46d339b84d9a.png)
  
3. Pour le domaine que vous souhaitez modifier, sélectionnez **Manage Domain (gérer le domaine**).
    
    ![Freenom sélectionnez Manage Domain (gérer le domaine)](../../media/67737b71-8b1b-42a6-abaf-62d776d3eb87.png)
  
4. Sélectionnez **gérer le DNS Freenom**.
    
    ![Freenom gérer le DNS Freenom](../../media/9854a511-27e3-4658-8903-34b3d425096d.png)
  
5. Sous **Ajouter un enregistrement**, dans la colonne **type** , choisissez **txt** dans le menu. 
    
    ![Freenom ajouter un type d’enregistrement TXT](../../media/7f0e85e7-844f-4962-815e-5d80d9e6efa0.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|
    |(Laisser vide)  <br/> |TXT  <br/> |3600 (secondes)  <br/> |MS = msXXXXXXXX  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Valeurs TXT Freenom pour la vérification](../../media/650098df-b3aa-47e5-9763-7fde24e34c3f.png)
  
7. Sélectionnez **enregistrer les modifications**.
    
    ![Enregistrement TXT Freenom enregistrer les modifications](../../media/b1a63f9a-4578-491a-9554-c40f73b37e09.png)
  
8. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
    
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
<a name="bkmk_mx"> </a>

1. Pour commencer, accédez à la page de vos domaines dans Freenom à l’aide de [ce lien](https://my.freenom.com/). You'll be prompted to log in.
    
    ![Connexion Freenom](../../media/90a32855-bfdd-4dfe-881c-b9a36b2f0582.png)
  
2. Sélectionnez **services**, puis **My Domains**.
    
    ![Freenom sélectionner les services et mes domaines](../../media/1917ced2-e254-4aec-9096-46d339b84d9a.png)
  
3. Pour le domaine que vous souhaitez modifier, sélectionnez **Manage Domain (gérer le domaine**).
    
    ![Freenom sélectionnez Manage Domain (gérer le domaine)](../../media/67737b71-8b1b-42a6-abaf-62d776d3eb87.png)
  
4. Définissez le nom pour votre domaine sur les serveurs de noms Freenom par défaut. Sélectionnez **outils de gestion**, puis serveurs de **noms**.
    
    ![Paramètre de serveur de noms Freenom](../../media/a6ae877a-c248-42b9-bae9-210a80cd01e7.png)
  
5. Assurez-vous que l’option utiliser les serveurs de **noms par défaut** est sélectionnée, puis sélectionnez Modifier les serveurs de **noms**.
    
    ![Modifier les serveurs de noms Freenom](../../media/0ef90d84-c0a0-4ef9-9e4c-43ef0aac3a2e.png)
  
6. Sélectionnez **gérer le DNS Freenom**.
    
    ![Freenom sélectionnez Manage Freenom DNS](../../media/f55a8053-2411-45da-a357-776c6699f721.png)
  
7. Sous **Ajouter un enregistrement**, dans la colonne **type** , choisissez **MX** dans le menu. 
    
    ![Freenom ajouter un type d’enregistrement MX](../../media/c728c6ee-786c-4f6a-8ad5-1d9914a5bfcf.png)
  
8. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Target (Cible)**|**Priority (Priorité)**|
    |:-----|:-----|:-----|:-----|:-----|
    |(Laisser vide)  <br/> |MX (Mail Exchanger) (MX - Serveur de courrier)  <br/> |3600 (secondes)  <br/> |\<Key\>. mail.protection.Outlook.com  <br/> **Remarque :** Obtenir votre * \<clé\> de domaine* à partir de votre compte Microsoft.   [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |10   <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/17d415c1-067e-4974-84d5-aaeaf3a0c0a9). <br/> |
   
   ![Enregistrement MX Freenom](../../media/8896c4a9-b3dd-45ed-9916-f7da2715ba8c.png)
  
9. Sélectionnez **enregistrer les modifications**.
    
    ![Enregistrement MX Freenom enregistrer les modifications](../../media/7aa0a464-d136-417f-be40-48d3f728eeb7.png)
  
10. S’il existe d’autres enregistrements MX, supprimez-les tous. Pour chaque enregistrement, sélectionnez **supprimer**. Lorsque le message voulez **-vous vraiment supprimer cette entrée ?** s’affiche, sélectionnez **OK**.
    
## <a name="add-the-cname-records-that-are-required-for-microsoft"></a>Ajouter les enregistrements CNAME requis pour Microsoft
<a name="bkmk_cname"> </a>

1. Pour commencer, accédez à la page de vos domaines dans Freenom à l’aide de [ce lien](https://my.freenom.com/). You'll be prompted to log in.
    
    ![Connexion Freenom](../../media/90a32855-bfdd-4dfe-881c-b9a36b2f0582.png)
  
2. Sélectionnez **services**, puis **My Domains**.
    
    ![Freenom sélectionner les services et mes domaines](../../media/1917ced2-e254-4aec-9096-46d339b84d9a.png)
  
3. Pour le domaine que vous souhaitez modifier, sélectionnez **Manage Domain (gérer le domaine**).
    
    ![Freenom sélectionnez Manage Domain (gérer le domaine)](../../media/67737b71-8b1b-42a6-abaf-62d776d3eb87.png)
  
4. Sélectionnez **gérer le DNS Freenom**.
    
    ![Freenom sélectionnez Manage Freenom DNS](../../media/5e7bc3a7-0d5e-431b-bb27-da3b0f316d01.png)
  
5. Sous **Ajouter un enregistrement**, dans la colonne **type** , choisissez **CNAME** dans le menu. 
    
    ![Freenom ajouter un type d’enregistrement CNAMe](../../media/9b204755-ca2a-46d2-bce2-030d82fd1f9e.png)
  
6. Créez le premier enregistrement CNAME. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    |**Name (Nom)**|**Type d'enregistrement**|**TTL (Durée de vie)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |autodiscover.outlook.com  <br/> |
    |sip  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |webdir.online.lync.com  <br/> |
    |enterpriseregistration  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |enterpriseregistration.windows.net  <br/> |
    |enterpriseenrollment  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
   
    ![Valeurs CNAMe Freenom](../../media/752fc682-e3f2-4b9c-9253-bf1ba2d414e9.png)
  
7. Sélectionnez **enregistrer les modifications**.
    
    ![Freenom CNAMe enregistrer les modifications](../../media/68103fd2-0f5f-4aac-a875-25157c6bbdd2.png)
  
8. Répétez les étapes précédentes pour créer les cinq autres enregistrements CNAMe. 
    
    Pour chaque enregistrement, tapez ou copiez-collez les valeurs de la ligne suivante du tableau ci-dessus dans les zones de cet enregistrement.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="bkmk_spf"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs. 

1. Pour commencer, accédez à la page de vos domaines dans Freenom à l’aide de [ce lien](https://my.freenom.com/). You'll be prompted to log in.
    
    ![Connexion Freenom](../../media/90a32855-bfdd-4dfe-881c-b9a36b2f0582.png)
  
2. Sélectionnez **services**, puis **My Domains**.
    
    ![Freenom sélectionner les services et mes domaines](../../media/1917ced2-e254-4aec-9096-46d339b84d9a.png)
  
3. Pour le domaine que vous souhaitez modifier, sélectionnez **Manage Domain (gérer le domaine**).
    
    ![Freenom sélectionnez Manage Domain (gérer le domaine)](../../media/67737b71-8b1b-42a6-abaf-62d776d3eb87.png)
  
4. Sélectionnez **gérer le DNS Freenom**.
    
    ![Freenom sélectionnez Manage Freenom DNS](../../media/94809955-0315-409c-a15d-703a2fe4c4ed.png)
  
5. Sous **Ajouter un enregistrement**, dans la colonne **type** , choisissez **txt** dans le menu. 
    
    ![Freenom ajouter un type d’enregistrement TXT](../../media/d8854285-c4ae-416c-a072-72a11ba1cd9a.png)
  
6. In the boxes for the new record, type or copy and paste the following values. 
    
    |**Name (Nom)**|**Type d'enregistrement**|**TTL (Durée de vie)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|
    |(Laisser vide)  <br/> |TXT  <br/> |3600 (secondes)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/>**Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![Valeurs TXT Freenom pour SPF](../../media/1b3b1199-9104-4ca1-acdb-786d139c21ac.png)
  
7. Sélectionnez **enregistrer les modifications**.
    
    ![Enregistrement TXT Freenom pour les modifications d’enregistrement SPF](../../media/e2fc52b1-0dcb-4595-9a4c-fca5e2ef9f97.png)
  

