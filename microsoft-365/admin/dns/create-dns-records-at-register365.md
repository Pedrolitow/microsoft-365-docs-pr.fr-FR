---
title: Créer des enregistrements DNS sur Register365 pour Microsoft
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
ms.assetid: 004030b4-10ad-4026-96e7-011b6afc7e73
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur Register365 pour Microsoft.
ms.openlocfilehash: 08db53df7510de76c6c5c33d2047cba4203324d8
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43629262"
---
# <a name="create-dns-records-at-register365-for-microsoft"></a>Créer des enregistrements DNS sur Register365 pour Microsoft

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Register365 est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc. 
  
Voici les principaux enregistrements à ajouter.  
  
- [Ajouter un enregistrement TXT à des fins de vérification](#add-a-txt-record-for-verification)
    
- [Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient envoyés à Microsoft](#add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft)
    
- [Ajouter les six enregistrements CNAMe requis pour Microsoft](#add-the-six-cname-records-that-are-required-for-microsoft)
    
- [Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable](#add-a-txt-record-for-spf-to-help-prevent-email-spam)
    
- [Ajouter les deux enregistrements SRV requis pour Microsoft](#add-the-two-srv-records-that-are-required-for-microsoft)
    
Une fois que vous avez ajouté ces enregistrements auprès de Microsoft, votre domaine est configuré pour utiliser les services Microsoft.
  
Pour en savoir plus sur l’hébergement Web et le DNS pour les sites Web avec Microsoft, consultez [la rubrique utiliser un site Web public avec Microsoft](https://support.office.com/article/choose-a-public-website-3325d50e-d131-403c-a278-7f3296fe33a9).
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d’utiliser votre domaine avec Microsoft, vous devez vous assurer que vous en êtes propriétaire. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que vous êtes propriétaire du domaine.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Register365 en utilisant [ce lien](https://admin.register365.com/dns/). Avant toute chose, vous serez invité à vous connecter.
    
    ![Page de connexion au Panneau de configuration](../../media/d7ec9791-d03f-45dd-b080-8aaae5d19ea6.png)
  
2. Sur la page **Dashboard (Tableau de bord)**, recherchez le nom du domaine à mettre à jour, puis sélectionnez **DNS Settings (Paramètres DNS)** dans la liste déroulante. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    ![Sélection des paramètres DNS dans la liste](../../media/57944802-3f6b-49bb-971a-b1d20936cba3.png)
  
3. On the **Add/Modify DNS Zone** page, in the **A, CNAME, AAAA, TXT and NS records** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    (Si vous avez besoin d’ajouter une ligne, sélectionnez **Ajouter des enregistrements a/CNAME (+)**.)
    
    (You may have to scroll down.)
    
    |**Host name (Nom d'hôte)**|**Type (Type)**|**Résultat**|
    |:-----|:-----|:-----|
    |(Leave this field empty.)  <br/> |TXT  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre **adresse de destination ou de pointage** spécifique ici, à partir du tableau.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Entrée de valeurs dans la page Add/Modify DNS zone (ajouter/modifier la zone DNS)](../../media/22326005-de95-464d-8e33-08ea31a89b2d.png)
  
4. Sélectionnez **Enregistrer**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez Enregistrer.](../../media/157cfb98-d5d0-48a3-8dd1-c4e759c2f8a8.png)
  
5. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
À présent que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous allez revenir à Microsoft et demander l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT correct, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
    
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient envoyés à Microsoft
<a name="BKMK_add_MX"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site Register365 en utilisant [ce lien](https://admin.register365.com/dns/). Avant toute chose, vous serez invité à vous connecter.
    
    ![Page de connexion au Panneau de configuration](../../media/d7ec9791-d03f-45dd-b080-8aaae5d19ea6.png)
  
2. Sur la page **Dashboard (Tableau de bord)**, recherchez le nom du domaine à mettre à jour, puis sélectionnez **DNS Settings (Paramètres DNS)** dans la liste déroulante. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    ![Sélection des paramètres DNS dans la liste](../../media/57944802-3f6b-49bb-971a-b1d20936cba3.png)
  
3. Dans la page **Add/Modify DNS Zone (Ajouter/modifier la zone DNS)**, dans la section **Mail exchange records (Enregistrements MX)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (You may have to scroll down.)
    
    |**Host name (Nom d'hôte)**|**Priority (Priorité)**|**Result (Résultat)**|
    |:-----|:-----|:-----|
    |(Laissez ce champ vide.)  <br/> |0,1  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenir votre * \<clé\> de domaine* à partir de votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)     |
   
    ![Entrée de valeurs dans la page Add/Modify DNS zone (ajouter/modifier la zone DNS)](../../media/2d3645a8-9cb8-435e-b895-5535b6b1fffd.png)
  
4. Sélectionnez **Enregistrer**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez Enregistrer.](../../media/0e565fb0-a126-4a48-8ff7-2c2d79d4af32.png)
  
5. Si d'autres enregistrements MX sont répertoriés dans la section **Mail exchange records (Enregistrements MX)**, supprimez-les en les sélectionnant et en appuyant sur la touche **Suppr** de votre clavier. 
    
    ![Deleting records in the Mail exchange records section](../../media/8cc37e4f-2e85-4242-af0e-78149434167f.png)
  
6. Sélectionnez **Enregistrer**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez Enregistrer.](../../media/1fb69bb5-b5df-4060-adf1-eb26cfaa6c4f.png)
  
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a>Ajouter les six enregistrements CNAMe requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site Register365 en utilisant [ce lien](https://admin.register365.com/dns/). Avant toute chose, vous serez invité à vous connecter.
    
    ![Page de connexion au Panneau de configuration](../../media/d7ec9791-d03f-45dd-b080-8aaae5d19ea6.png)
  
2. Sur la page **Dashboard (Tableau de bord)**, recherchez le nom du domaine à mettre à jour, puis sélectionnez **DNS Settings (Paramètres DNS)** dans la liste déroulante. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    ![Sélection des paramètres DNS dans la liste](../../media/57944802-3f6b-49bb-971a-b1d20936cba3.png)
  
3. Dans la page **Add/Modify DNS Zone (Ajouter/modifier la zone DNS)**, dans la section **A, CNAME, AAAA, TXT and NS records (Enregistrements A, CNAME, AAAA, TXT et NS)**, dans les zones des nouveaux enregistrements, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    (Si vous avez besoin d’ajouter une ligne, sélectionnez **Ajouter des enregistrements a/CNAME (+)**.)
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    |****Host name (Nom d'hôte)****|****Type (Type)****|****Result (Résultat)****|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |autodiscover.outlook.com  <br/> |
    |sip  <br/> |CNAME  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |webdir.online.lync.com  <br/> |
    |enterpriseregistration  <br/> |CNAME  <br/> |enterpriseregistration.windows.net  <br/> |
    |enterpriseenrollment  <br/> |CNAME  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
   
    ![Entrée de valeurs dans la page Add/Modify DNS zone (ajouter/modifier la zone DNS)](../../media/3b79f0de-9cab-4c98-8fa8-c92b35241e8b.png)
  
4. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer.](../../media/8ded6428-af97-4fd8-9104-477fa22a5586.png)
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous disposez déjà d’un enregistrement SPF pour votre domaine, n’en créez pas pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Register365 en utilisant [ce lien](https://admin.register365.com/dns/). Avant toute chose, vous serez invité à vous connecter.
    
    ![Page de connexion au Panneau de configuration](../../media/d7ec9791-d03f-45dd-b080-8aaae5d19ea6.png)
  
2. Sur la page **Dashboard (Tableau de bord)**, recherchez le nom du domaine à mettre à jour, puis sélectionnez **DNS Settings (Paramètres DNS)** dans la liste déroulante. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    ![Sélection des paramètres DNS dans la liste](../../media/57944802-3f6b-49bb-971a-b1d20936cba3.png)
  
3. On the **Add/Modify DNS Zone** page, in the **A, CNAME, AAAA, TXT and NS records** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    (Si vous avez besoin d’ajouter une ligne, sélectionnez **Ajouter des enregistrements a/CNAME (+)**.)
    
    (You may have to scroll down.)
    
    |**Host name (Nom d'hôte)**|**Type (Type)**|**Résultat**|
    |:-----|:-----|:-----|
    |(Leave this field empty.)  <br/> |TXT  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/>**Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![Entrée de valeurs dans la page Add/Modify DNS zone (ajouter/modifier la zone DNS)](../../media/33976398-da8a-439b-8e3d-534503b20ee0.png)
  
4. Sélectionnez **Enregistrer**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez Enregistrer.](../../media/1d8da122-4861-4ca3-bc9b-d01f18557d4c.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajouter les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site Register365 en utilisant [ce lien](https://admin.register365.com/dns/). Avant toute chose, vous serez invité à vous connecter.
    
    ![Page de connexion au Panneau de configuration](../../media/d7ec9791-d03f-45dd-b080-8aaae5d19ea6.png)
  
2. Sur la page **Dashboard (Tableau de bord)**, recherchez le nom du domaine à mettre à jour, puis sélectionnez **DNS Settings (Paramètres DNS)** dans la liste déroulante. 
    
    (You may have to scroll down.)
    
    ![Sélection des paramètres DNS dans la liste](../../media/57944802-3f6b-49bb-971a-b1d20936cba3.png)
  
3. Dans la page **Add/Modify DNS Zone (Ajouter/modifier la zone DNS)**, dans la section **Service records (Enregistrements du service)**, dans les zones des nouveaux enregistrements, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    |**Name (Nom)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Result (Résultat)**|
    |:-----|:-----|:-----|:-----|:-----|
    |_sip. _tls  <br/> |100  <br/> |0,1  <br/> |443  <br/> |sipdir.online.lync.com  <br/> |
    |_sipfederationtls. _tcp  <br/> |100  <br/> |0,1  <br/> |5061  <br/> |sipfed.online.lync.com  <br/> |
   
    ![Entrée de valeurs dans la section des enregistrements de service](../../media/56bb1813-90e2-40c8-98bf-750e2dc3f8b6.png)
  
4. Sélectionnez **Enregistrer**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez Enregistrer.](../../media/3b80757c-01e1-492d-b2ce-f721d71f7235.png)
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
