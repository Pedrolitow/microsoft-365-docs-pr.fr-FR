---
title: Créer des enregistrements DNS sur NetRegistry pour Microsoft
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
- BEA160
ms.assetid: 48e09394-2287-4b3c-9853-21eadf61277e
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur NetRegistry pour Microsoft.
ms.openlocfilehash: 857645c685cce946b39a7c3dcadb0a45b43686cf
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49657802"
---
# <a name="create-dns-records-at-netregistry-for-microsoft"></a>Créer des enregistrements DNS sur NetRegistry pour Microsoft

[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml) si vous ne trouvez pas ce que vous recherchez. 
  
Si NetRegistry est votre fournisseur d’hébergement DNS, suivez la procédure décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online, etc.
  
Voici les principaux enregistrements à ajouter.
  
- [Ajouter un enregistrement TXT à des fins de vérification](#add-a-txt-record-for-verification)
    
- [Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft](#add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft)

- [Ajouter les enregistrements CNAME requis pour Microsoft](#add-the-cname-records-that-are-required-for-microsoft)
    
- [Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable](#add-a-txt-record-for-spf-to-help-prevent-email-spam)
    
- [Ajoutez les deux enregistrements SRV requis pour Microsoft](#add-the-two-srv-records-that-are-required-for-microsoft)
    
Une fois ces enregistrements ajoutés sur NetRegistry, votre domaine est configuré pour utiliser les services Microsoft.
  
  
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="bkmk_txt"> </a>

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines dans NetRegistry en utilisant [ce lien](https://theconsole.netregistry.com.au/). You'll be prompted to log in.
    
    ![Netregistry_login](../../media/ed3c785f-01c3-49e7-affd-c04637c0ffe9.png)
  
2. En regard du domaine que vous souhaitez gérer, sélectionnez **gérer**.
    
    ![Netregistry_Manage](../../media/64ad542a-5ec4-4148-96f8-d6e163449352.png)
  
3. Sélectionnez **Gestionnaire de zones**.
    
    ![Netregistry_selectZoneManager](../../media/e18c32f9-c1e7-4aa2-9aa6-8dc9c5ea44af.png)
  
4. Sous **Ajouter un enregistrement de zone**, choisissez **enregistrement txt** dans la liste, puis sélectionnez **créer un enregistrement**.
    
    ![Netregistry_TXT_select](../../media/eb1761e6-9deb-4631-8deb-bc5d09926722.png)
  
    > [!NOTE]
    > Vous devez utiliser des guillemets avant et après l’entrée dans la zone TXT. 
  
    Dans le **nouveau formulaire d’enregistrement txt** , tapez ou copiez-collez les valeurs du tableau suivant. 
    
    |**Name**|**DURÉE DE VIE (S)**|**TXT (pointe vers l’adresse ou la valeur)**|
    |:-----|:-----|:-----|
    |(Laisser vide)  <br/> |3600 (secondes)  <br/> |« MS = msXXXXXXXX »  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)  |
       
    ![Netregistry_verificationTXTvalues](../../media/cfe8b05a-fa8b-4dba-9554-7a3466e6c012.png)
  
6. Sélectionnez **Ajouter un enregistrement**.
    
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

1. Pour commencer, accédez à la page de vos domaines dans NetRegistry en utilisant [ce lien](https://theconsole.netregistry.com.au/). You'll be prompted to log in.
    
    ![Netregistry_login](../../media/80277b0e-547e-4635-aa6a-5d8ebe3fba85.png)
  
2. En regard du domaine que vous souhaitez gérer, sélectionnez **gérer**.
    
    ![Netregistry_Manage](../../media/96e2c6e4-21fd-4405-a4fe-b1188400b985.png)
  
3. Sélectionnez **Gestionnaire de zones**.
    
    ![Netregistry_selectZoneManager](../../media/914021f6-dff3-4640-84d6-b83cf8f61cf1.png)
  
4. Sous **enregistrements de la zone actuelle**, supprimez les enregistrements MX par défaut en sélectionnant **supprimer** en regard de chaque enregistrement MX de la liste. 
    
    ![Netregistry_MX_remove](../../media/494670a9-8b8d-46e5-8136-05e82212a115.png)
  
5. Sous **Ajouter un enregistrement de zone**, choisissez **enregistrement MX** dans la liste, puis sélectionnez **créer un enregistrement**.
    
    ![Netregistry_MX_select](../../media/29b60eb9-6c40-490f-9669-e65b65962f37.png)
  
6. Dans le **nouveau formulaire d’enregistrement MX** , tapez ou copiez-collez les valeurs du tableau suivant. 
    
    |**Name**|**DURÉE DE VIE (S)**|**Exchange (pointe vers l’adresse ou la valeur)**|**L’hôte est-il entièrement qualifié ?**|**Préférence (priorité)**|
    |:-----|:-----|:-----|:-----|:-----|
    |(Laisser vide)  <br/> |3600 (secondes)  <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenir votre  *\<domain-key\>*  à partir de votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)      |(cochez la case)  <br/> |10   <br/> For more information about priority, see What is MX priority?  <br/> |
       
    ![Netregistry_MX_values](../../media/518b3da6-4055-4e2d-b5ce-44a0fee25419.png)
  
7. Sélectionnez **Ajouter un enregistrement**.
    
    ![Netregistry_MX_values_AddRecord](../../media/8194cb38-afa0-48ac-831c-fd34b6ad652e.png)
  
## <a name="add-the-cname-records-that-are-required-for-microsoft"></a>Ajouter les enregistrements CNAME requis pour Microsoft
<a name="bkmk_cname"> </a>

1. Pour commencer, accédez à la page de vos domaines dans NetRegistry en utilisant [ce lien](https://theconsole.netregistry.com.au/). You'll be prompted to log in.
    
    ![Netregistry_login](../../media/cbf83dce-86d2-4008-9400-56def4b6fcd7.png)
  
2. En regard du domaine que vous souhaitez gérer, sélectionnez **gérer**.
    
    ![Netregistry_Manage](../../media/7bee4b0f-2c1d-43ca-b1bb-9b889ca0c5e4.png)
  
3. Sélectionnez **Gestionnaire de zones**.
    
    ![Netregistry_selectZoneManager](../../media/58384add-0a9d-472b-a5d0-51ec8155fd41.png)
  
4. Sous  **Ajouter un enregistrement de zone**, choisissez **enregistrement CNAME** dans la liste, puis sélectionnez **créer un enregistrement**.
    
    ![Netregistry_CNAME_CreateNewRecord](../../media/7b4f133f-45da-48da-93c0-62f57c786165.png)
  
5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    |**Name**|**Type (Type)**|**TTL (Durée de vie)**|**HÔTE (pointe vers ou adresse)**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |autodiscover.outlook.com  <br/> |
    |sip  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |webdir.online.lync.com  <br/> |
    |enterpriseregistration  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |enterpriseregistration.windows.net  <br/> |
    |enterpriseenrollment  <br/> |CNAME  <br/> |3600 (secondes)  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
       
    ![Netregistry_CNAME_values](../../media/93c479f0-3ce2-491a-9113-6dde1cd7131b.png)
      
6. Sélectionnez **Ajouter un enregistrement**.
    
    ![Netregistry_CNAME_values_AddRecord](../../media/046c8c64-ea71-4530-9fc6-69f0c70993b6.png)
  
7. Répétez les étapes précédentes pour créer les cinq autres enregistrements CNAMe.
    
    Pour chaque enregistrement, tapez ou copiez-collez les valeurs de la ligne suivante du tableau ci-dessus dans les zones de cet enregistrement.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="bkmk_spf"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs.
  
1. Pour commencer, accédez à la page de vos domaines dans NetRegistry en utilisant [ce lien](https://theconsole.netregistry.com.au/). You'll be prompted to log in.
    
    ![Netregistry_login](../../media/a841f11f-1c0f-4926-acea-a2b8bb083984.png)
  
2. En regard du domaine que vous souhaitez gérer, sélectionnez **gérer**.
    
    ![Netregistry_Manage](../../media/4245bbbb-4e2d-49e7-a89c-679949aa3d18.png)
  
3. Sélectionnez **Gestionnaire de zones**.
    
    ![Netregistry_selectZoneManager](../../media/372e5918-b6dc-4268-8f9a-0aa71d65deef.png)
  
4. Sous **Ajouter un enregistrement de zone**, choisissez **enregistrement txt** dans la liste, puis sélectionnez **créer un enregistrement**.
    
    ![Netregistry_TXT_select](../../media/a2930d03-853a-4f1e-9205-d00f25bed35f.png)
  
5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    > [!NOTE]
    > Vous devez utiliser des guillemets avant et après l’entrée dans la zone TXT. 
  
    |**Name**|**Type (Type)**|**TTL (Durée de vie)**|**Données TXT (cible)**|
    |:-----|:-----|:-----|:-----|
    |(Laisser vide)  <br/> |TXT  <br/> |3600 (secondes)  <br/> |"v = spf1 include include. protection. Outlook. com-All"  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![Netregistry_SPF-TXTvalues](../../media/a369345a-d774-48bc-8160-b628ab8247f9.png)
  
6. Sélectionnez **Ajouter un enregistrement**.
    
    ![Netregistry_SPF-TXTvalues_AddRecord](../../media/063bfbaf-940a-489f-970f-29c026b4b312.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft
<a name="bkmk_srv"> </a>

1. Pour commencer, accédez à la page de vos domaines dans NetRegistry en utilisant [ce lien](https://theconsole.netregistry.com.au/). You'll be prompted to log in.
    
    ![Netregistry_login](../../media/accf6584-e5f4-4d68-a641-0f8847f8370f.png)
  
2. En regard du domaine que vous souhaitez gérer, sélectionnez  **gérer**.
    
    ![Netregistry_Manage](../../media/e0ddc79e-0123-4e24-8380-9645bdb41aac.png)
  
3. Sélectionnez **Gestionnaire de zones**.
    
    ![Netregistry_selectZoneManager](../../media/f122888b-3cc5-40ec-adac-0ede04799d9a.png)
  
4. Sous  **Ajouter un enregistrement de zone**, choisissez **enregistrement SRV** dans la liste, puis sélectionnez **créer un enregistrement**.
    
    ![Netregistry_SRV_select](../../media/e5dab850-acd1-48b8-8b4a-e3b9777cf508.png)
  
5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    > [!NOTE]
    > Le champ nom est une combinaison du service (par exemple, _sip) et protocole (par exemple, _tls). 
  
    |**Type**|**Nom**|**DURÉE DE VIE (S)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV (service)  <br/> |_sip._tls  <br/> |3600 (secondes)  <br/> |100  <br/> |1   <br/> |443  <br/> |sipdir.online.lync.com  <br/> |
    |SRV (service)  <br/> |_sipfederationtls._tcp  <br/> |3600 (secondes)  <br/> |100  <br/> |1   <br/> |5061  <br/> |sipfed.online.lync.com  <br/> |
       
    ![Netregistry_SRV_values](../../media/49292846-1598-4b8c-9940-db6e10675753.png)
  
6. Sélectionnez **Ajouter un enregistrement**.
    
    ![Netregistry_SRV_values_AddRecord](../../media/abc82061-939f-4757-87e4-0e8f9e43ebcb.png)
  
7. Répétez les étapes précédentes pour créer l’autre enregistrement SRV.
    
    Tapez ou copiez-collez les valeurs de la deuxième ligne du tableau ci-dessus dans les zones du deuxième enregistrement.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  

