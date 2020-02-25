---
title: Créer des enregistrements DNS sur Freenom pour Office 365
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
ms.assetid: d8ff45a2-19e3-413d-aa64-a9982bd6633c
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur Freenom pour Office 365.
ms.openlocfilehash: a1396964c7dc9c279589a6020e0c741fd0cb29d5
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42244771"
---
# <a name="create-dns-records-at-freenom-for-office-365"></a>Créer des enregistrements DNS sur Freenom pour Office 365

[Consultez le Forum aux questions sur les domaines](../setup/domains-faq.md) si vous ne trouvez pas ce que vous recherchez. 
  
> [!CAUTION]
> Le site Web Freenom ne prend pas en charge les enregistrements SRV, ce qui signifie que plusieurs fonctionnalités de Skype entreprise Online et d’Outlook Web App ne fonctionneront pas. Quelle que soit la planification d’Office 365 que vous utilisez, il existe des limitations de service importantes, et vous pouvez choisir d’utiliser un autre fournisseur d’hébergement DNS. 
  
Si malgré les limitations de service, vous choisissez de gérer vos propres enregistrements DNS Office 365 sur Freenom, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour la messagerie et d’autres services.
  
Pour en savoir plus sur l'hébergement web et le DNS pour les sites web avec Office 365, voir [Utiliser un site web public avec Office 365](https://support.office.com/article/a8178510-501d-4bd8-9921-b04f2e9517a5.aspx).
  
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="bkmk_txt"> </a>

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines dans Freenom à l’aide de [ce lien](https://my.freenom.com/). You'll be prompted to log in.
    
    ![Connexion Freenom](../media/90a32855-bfdd-4dfe-881c-b9a36b2f0582.png)
  
2. Sélectionnez **services**, puis **My Domains**.
    
    ![Freenom sélectionner les services et mes domaines](../media/1917ced2-e254-4aec-9096-46d339b84d9a.png)
  
3. Pour le domaine que vous souhaitez modifier, sélectionnez **Manage Domain (gérer le domaine**).
    
    ![Freenom sélectionnez Manage Domain (gérer le domaine)](../media/67737b71-8b1b-42a6-abaf-62d776d3eb87.png)
  
4. Sélectionnez **gérer le DNS Freenom**.
    
    ![Freenom gérer le DNS Freenom](../media/9854a511-27e3-4658-8903-34b3d425096d.png)
  
5. Sous **Ajouter un enregistrement**, dans la colonne **type** , choisissez **txt** dans le menu. 
    
    ![Freenom ajouter un type d’enregistrement TXT](../media/7f0e85e7-844f-4962-815e-5d80d9e6efa0.png)
  
6. In the boxes for the new record, type or copy and paste the values from the following table. 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Target**|
    |:-----|:-----|:-----|:-----|
    |(Laisser vide)  <br/> |TXT  <br/> |3600 (secondes)  <br/> |MS = msXXXXXXXX  <br/> **Remarque :** Voici un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Valeurs TXT Freenom pour la vérification](../media/650098df-b3aa-47e5-9763-7fde24e34c3f.png)
  
7. Sélectionnez **enregistrer les modifications**.
    
    ![Enregistrement TXT Freenom enregistrer les modifications](../media/b1a63f9a-4578-491a-9554-c40f73b37e09.png)
  
8. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
Now that you've added the record at your domain registrar's site, you'll go back to Office 365 and request Office 365 to look for the record.
  
When Office 365 finds the correct TXT record, your domain is verified.
  
1. Dans le centre d’administration, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> .

    
2. Dans la page **domaines** , sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Sur la page **installation** , sélectionnez **Démarrer l’installation**.
    
    
  
4. Sur la page **vérifier le domaine** , sélectionnez **vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365
<a name="bkmk_mx"> </a>

1. Pour commencer, accédez à la page de vos domaines dans Freenom à l’aide de [ce lien](https://my.freenom.com/). You'll be prompted to log in.
    
    ![Connexion Freenom](../media/90a32855-bfdd-4dfe-881c-b9a36b2f0582.png)
  
2. Sélectionnez **services**, puis **My Domains**.
    
    ![Freenom sélectionner les services et mes domaines](../media/1917ced2-e254-4aec-9096-46d339b84d9a.png)
  
3. Pour le domaine que vous souhaitez modifier, sélectionnez **Manage Domain (gérer le domaine**).
    
    ![Freenom sélectionnez Manage Domain (gérer le domaine)](../media/67737b71-8b1b-42a6-abaf-62d776d3eb87.png)
  
4. Définissez le nom pour votre domaine sur les serveurs de noms Freenom par défaut. Sélectionnez **outils de gestion**, puis serveurs de **noms**.
    
    ![Paramètre de serveur de noms Freenom](../media/a6ae877a-c248-42b9-bae9-210a80cd01e7.png)
  
5. Assurez-vous que l’option utiliser les serveurs de **noms par défaut** est sélectionnée, puis sélectionnez Modifier les serveurs de **noms**.
    
    ![Modifier les serveurs de noms Freenom](../media/0ef90d84-c0a0-4ef9-9e4c-43ef0aac3a2e.png)
  
6. Sélectionnez **gérer le DNS Freenom**.
    
    ![Freenom sélectionnez Manage Freenom DNS](../media/f55a8053-2411-45da-a357-776c6699f721.png)
  
7. Sous **Ajouter un enregistrement**, dans la colonne **type** , choisissez **MX** dans le menu. 
    
    ![Freenom ajouter un type d’enregistrement MX](../media/c728c6ee-786c-4f6a-8ad5-1d9914a5bfcf.png)
  
8. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Target**|**Priorité**|
    |:-----|:-----|:-----|:-----|:-----|
    |(Laisser vide)  <br/> |MX (Mail Exchanger) (MX - Serveur de courrier)  <br/> |3600 (secondes)  <br/> |\<Key\>. mail.protection.Outlook.com  <br/> **Remarque :** Obtenez votre * \<clé\> de domaine* à partir de votre compte Office 365.   [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |10   <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/17d415c1-067e-4974-84d5-aaeaf3a0c0a9). <br/> |
   
   ![Enregistrement MX Freenom](../media/8896c4a9-b3dd-45ed-9916-f7da2715ba8c.png)
  
9. Sélectionnez **enregistrer les modifications**.
    
    ![Enregistrement MX Freenom enregistrer les modifications](../media/7aa0a464-d136-417f-be40-48d3f728eeb7.png)
  
10. S’il existe d’autres enregistrements MX, supprimez-les tous. Pour chaque enregistrement, sélectionnez **supprimer**. Lorsque le message voulez **-vous vraiment supprimer cette entrée ?** s’affiche, sélectionnez **OK**.
    
## <a name="add-the-cname-records-that-are-required-for-office-365"></a>Ajouter les enregistrements CNAME requis pour Office 365
<a name="bkmk_cname"> </a>

1. Pour commencer, accédez à la page de vos domaines dans Freenom à l’aide de [ce lien](https://my.freenom.com/). You'll be prompted to log in.
    
    ![Connexion Freenom](../media/90a32855-bfdd-4dfe-881c-b9a36b2f0582.png)
  
2. Sélectionnez **services**, puis **My Domains**.
    
    ![Freenom sélectionner les services et mes domaines](../media/1917ced2-e254-4aec-9096-46d339b84d9a.png)
  
3. Pour le domaine que vous souhaitez modifier, sélectionnez **Manage Domain (gérer le domaine**).
    
    ![Freenom sélectionnez Manage Domain (gérer le domaine)](../media/67737b71-8b1b-42a6-abaf-62d776d3eb87.png)
  
4. Sélectionnez **gérer le DNS Freenom**.
    
    ![Freenom sélectionnez Manage Freenom DNS](../media/5e7bc3a7-0d5e-431b-bb27-da3b0f316d01.png)
  
5. Sous **Ajouter un enregistrement**, dans la colonne **type** , choisissez **CNAME** dans le menu. 
    
    ![Freenom ajouter un type d’enregistrement CNAMe](../media/9b204755-ca2a-46d2-bce2-030d82fd1f9e.png)
  
6. Créez le premier enregistrement CNAME. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    |**Name (Nom)**|**Type d'enregistrement**|**TTL**|**Target**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |autodiscover.outlook.com  <br/> |
    |sip  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |webdir.online.lync.com  <br/> |
    |enterpriseregistration  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |enterpriseregistration.windows.net  <br/> |
    |enterpriseenrollment  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
   
    ![Valeurs CNAMe Freenom](../media/752fc682-e3f2-4b9c-9253-bf1ba2d414e9.png)
  
7. Sélectionnez **enregistrer les modifications**.
    
    ![Freenom CNAMe enregistrer les modifications](../media/68103fd2-0f5f-4aac-a875-25157c6bbdd2.png)
  
8. Répétez les étapes précédentes pour créer les cinq autres enregistrements CNAMe. 
    
    Pour chaque enregistrement, tapez ou copiez-collez les valeurs de la ligne suivante du tableau ci-dessus dans les zones de cet enregistrement.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="bkmk_spf"> </a>

> [!IMPORTANT]
> You cannot have more than one TXT record for SPF for a domain. If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues. If you already have an SPF record for your domain, don't create a new one for Office 365. Ajoutez plutôt les valeurs Office 365 requises à l'enregistrement actuel de manière à n'avoir qu'un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs. 

1. Pour commencer, accédez à la page de vos domaines dans Freenom à l’aide de [ce lien](https://my.freenom.com/). You'll be prompted to log in.
    
    ![Connexion Freenom](../media/90a32855-bfdd-4dfe-881c-b9a36b2f0582.png)
  
2. Sélectionnez **services**, puis **My Domains**.
    
    ![Freenom sélectionner les services et mes domaines](../media/1917ced2-e254-4aec-9096-46d339b84d9a.png)
  
3. Pour le domaine que vous souhaitez modifier, sélectionnez **Manage Domain (gérer le domaine**).
    
    ![Freenom sélectionnez Manage Domain (gérer le domaine)](../media/67737b71-8b1b-42a6-abaf-62d776d3eb87.png)
  
4. Sélectionnez **gérer le DNS Freenom**.
    
    ![Freenom sélectionnez Manage Freenom DNS](../media/94809955-0315-409c-a15d-703a2fe4c4ed.png)
  
5. Sous **Ajouter un enregistrement**, dans la colonne **type** , choisissez **txt** dans le menu. 
    
    ![Freenom ajouter un type d’enregistrement TXT](../media/d8854285-c4ae-416c-a072-72a11ba1cd9a.png)
  
6. In the boxes for the new record, type or copy and paste the following values. 
    
    |**Name**|**Type d'enregistrement**|**TTL**|**Target**|
    |:-----|:-----|:-----|:-----|
    |(Laisser vide)  <br/> |TXT  <br/> |3600 (secondes)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/>**Remarque :** Nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![Valeurs TXT Freenom pour SPF](../media/1b3b1199-9104-4ca1-acdb-786d139c21ac.png)
  
7. Sélectionnez **enregistrer les modifications**.
    
    ![Enregistrement TXT Freenom pour les modifications d’enregistrement SPF](../media/e2fc52b1-0dcb-4595-9a4c-fca5e2ef9f97.png)
  

