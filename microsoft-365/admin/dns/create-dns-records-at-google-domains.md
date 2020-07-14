---
title: Créer des enregistrements DNS via Google Domains pour Microsoft
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0db29490-2612-48bc-9b77-1862e7a41a8c
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Lync et les autres services sur Google Domains pour Microsoft.
ms.openlocfilehash: e6b1dd1eb90957a4e7fe22bd4b66ac87b2a51d09
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44400448"
---
# <a name="create-dns-records-at-google-domains-for-microsoft"></a>Créer des enregistrements DNS via Google Domains pour Microsoft

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Google Domains est votre fournisseur d’hébergement DNS, procédez de la manière décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Lync, etc.
  
Une fois ces enregistrements ajoutés sur Google Domains, votre domaine est configuré pour utiliser les services Microsoft.
  

  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d'autres problèmes suite à l'ajout des enregistrements DNS, consultez [Rechercher et corriger les problèmes suite à l'ajout de votre domaine ou des enregistrements DNS dans Microsoft](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.
  
> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like. 
  
1. To get started, go to your domains page at Google Domains by using [this link](https://domains.google.com/registrar). You'll be prompted to sign in. To do so:
    
1. Sélectionnez **Se connecter**.
    
2. Entrez vos informations d’identification, puis sélectionnez à nouveau **Se connecter**.
    
2. Dans la page **Mes domaines**, recherchez le domaine à utiliser avec Microsoft, puis sélectionnez le lien **GÉRER** en regard de celui-ci. Dans le volet de navigation gauche, sélectionnez **DNS**.
    
3. Dans la section **Custom resource records (Enregistrements de ressource personnalisés)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Name** <br/> |**Type (Type)** <br/> |**TTL (Durée de vie)** <br/> |**Données** <br/> |
    |@  <br/> |TXT  <br/> |1H  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
4. Sélectionnez **Ajouter**.
    
5. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
<a name="BKMK_add_MX"> </a>

1. To get started, go to your domains page at Google Domains by using [this link](https://domains.google.com/registrar). You'll be prompted to sign in. To do so:
    
2. Sélectionnez **Se connecter**.
    
3. Entrez vos informations d’identification, puis sélectionnez à nouveau **Se connecter**.
4. Dans la page **Domaines**, dans la section **Domaine**, sélectionnez **Configurer le DNS** pour le domaine à modifier.
    
    > [!IMPORTANT]
    > Si vous avez un compte de messagerie G Suite, vous devez commencer par supprimer les enregistrements MX qui lui sont associés. Les enregistrements MX G Suite vous empêchent d'ajouter d'autres enregistrements MX, notamment ceux requis pour Microsoft 365. Notez que la suppression d’enregistrements G Suite ne supprime pas votre compte G Suite. Pour supprimer les enregistrements MX G Suite, procédez comme suit. 
  
5. Dans la section **Enregistrements synthétiques**, dans la zone **G Suite**, sélectionnez **Supprimer**.
    
    (vous devrez peut-être faire défiler la page vers le bas).
    
    ![Sélectionnez Supprimer dans la section des Enregistrements synthétiques](../../media/bd276b5d-5667-4bb1-a233-2dc5194e7ace.png)
  
6. Sélectionnez **Supprimer**.
    
    ![Sélectionnez Supprimer](../../media/4413a45a-5b82-4ec6-82c6-0091f5be9696.png)
  
7. Dans la section **Custom resource records (Enregistrements de ressource personnalisés)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |**Name**|**Type (Type)**|**TTL (Durée de vie)**|**Données**|
    |:-----|:-----|:-----|:-----|
    |@  <br/> |MX  <br/> |1H  <br/> |0  *\<domain-key\>*  .mail.protection.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> The **0** is the MX priority value. Add it to the beginning of the MX value, separated from the remainder of the value by a space.  <br/> **Remarque :** Obtenez votre \<*domain-key*\> depuis votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq). <br/> |
   
    ![Tapez ou collez les valeurs dans la section Enregistrements de ressource personnalisés.](../../media/b660ca9e-984d-449f-ae59-a65fe4e2c6bd.png)
  
5. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter.](../../media/32f8f23c-0b80-48da-b08e-4e04052971af.png)
  
6. Si d’autres enregistrements MX personnalisés sont répertoriés, supprimez-les.
    
1. Sélectionnez **Modifier** dans la ligne d’enregistrement MX. 
    
    ![Sélectionnez Modifier dans la ligne d’enregistrement MX.](../../media/acc53ae9-3b8a-421d-8d11-d4a4108b2353.png)
  
2. Pour chacun des autres enregistrements MX personnalisés, sélectionnez l'entrée dans la zone **Data (Données)**, puis appuyez sur la touche **Suppr** du clavier pour supprimer cet enregistrement. 
    
    Continuez jusqu’à ce que vous ayez supprimé l’entrée **Data (Données)** de chacun des autres enregistrements MX. 
    
    ![Delete entries in the Data box](../../media/28192089-7b38-4d2e-9d52-9b83422c27d5.png)
  
7. Lorsque vous aurez supprimé l'entrée **Données** pour chacun des autres enregistrements MX, sélectionnez **Enregistrer** pour enregistrer vos modifications. 
    
    ![Sélectionnez Enregistrer](../../media/bf496d01-ccbe-4800-95f4-7b2283f2e5f6.png)
  
## <a name="add-the-five-cname-records-that-are-required-for-microsoft"></a>Ajouter les cinq enregistrements CNAME requis pour Microsoft

1. Pour commencer, accédez à la [page de vos domaines Google] (https://domains.google.com/registrar) et connectez-vous.
    
2. Dans la page **Domaines**, dans la section **Domaine**, sélectionnez **Configurer le DNS** pour le domaine à modifier. 
    
3. Ajoutez le premier enregistrement CNAME.
    
    Dans la section **Custom resource records (Enregistrements de ressource personnalisés)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |**Name**|**Type (Type)**|**TTL (Durée de vie)**|**Données**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |1H  <br/> |autodiscover.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |sip  <br/> |CNAME  <br/> |1H  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |1H  <br/> |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |enterpriseregistration  <br/> |CNAME  <br/> |1H  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |enterpriseenrollment  <br/> |CNAME  <br/> |1H  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
   
    ![Tapez ou collez les valeurs dans la section Enregistrements de ressource personnalisés.](../../media/cff9832a-6d57-421f-a183-55320974ed87.png)
  
4. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter.](../../media/4a78080a-e0b2-4582-9696-3fe4fea41e91.png)
  
5. Ajoutez les quatre autres enregistrements CNAME.
    
    Dans la section **Enregistrements de ressources personnalisés**, créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Ajouter** pour valider cet enregistrement. 
    
    Répétez cette procédure jusqu'à avoir créé tous les enregistrements CNAME requis.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir qu’un seul enregistrement SPF qui inclut les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](https://docs.microsoft.com/office365/enterprise/external-domain-name-system-records#bkmk_spfrecords). To validate your SPF record, you can use one of these [SPF validation tools](../setup/domains-faq.md). 
  
1. To get started, go to your domains page at Google Domains by using [this link](https://domains.google.com/registrar). You'll be prompted to sign in. To do so:
    
1. Sélectionnez **Se connecter**.
    
2. Entrez vos informations d’identification, puis sélectionnez à nouveau **Se connecter**.
    
3. Dans la page **Domaines**, dans la section **Domaine**, sélectionnez **Configurer le DNS** pour le domaine à modifier. 
    
4. Dans la section **Enregistrements de ressource personnalisée**, sur la ligne d’enregistrement TXT, sélectionnez **Modifier**. 
    
    > [!IMPORTANT]
    > Google Domains stores TXT records as a set that may contain multiple records. When you have at least one other TXT record, such as the TXT record you used to verify your domain, you must add TXT new records to that record set. Any attempt to enter additional TXT records as separate entries will result in a **Duplicate record** error message. 
  
    ![Sélectionnez la ligne d’enregistrement TXT](../../media/eae14850-8d0c-4f29-8587-df8b36129d5f.png)
  
5. Sélectionnez le contrôle **(+)**. 
    
    ![Sélectionnez le signe plus control](../../media/628604cc-d2b2-42a5-bb5b-13c327b85d9f.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    |**Données**|
    |:-----|
    |v=spf1 include:spf.protection.outlook.com -all  <br/> 

    > [!NOTE]
    > Nous vous recommandons de copier et de coller cette entrée, afin que l’espacement reste correct.           
   
   ![Tapez ou collez les valeurs dans la section Enregistrements de ressource personnalisés.](../../media/4645cc4f-9fcc-4626-9674-072ed6fa34c2.png)
  
7. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer](../../media/20c4c926-f062-4048-9265-bf752be54e0c.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

1. To get started, go to your domains page at Google Domains by using [this link](https://domains.google.com/registrar). You'll be prompted to sign in. To do so:
    
2. Sélectionnez **Se connecter**.
    
3. Entrez vos informations d’identification, puis sélectionnez à nouveau **Se connecter**.
    
4. Dans la page **Domaines**, dans la section **Domaine**, sélectionnez **Configurer le DNS** pour le domaine à modifier. 
    
5. Ajoutez le premier enregistrement SRV.
    
    Dans la section **Custom resource records (Enregistrements de ressource personnalisés)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    (Choisissez la valeur **Type (Type)** dans la liste déroulante.) 
    
    |**Name**|**Type (Type)**|**TTL (Durée de vie)**|**Données**|
    |:-----|:-----|:-----|:-----|
    |_sip._tls|SRV|1H|100 1 443 sipdir.online.lync.com. **Cette valeur DOIT se terminer par un point (.)****Remarque :** Nous enregistrons et collons cette entrée pour que l'espacement reste correct.           |
    |_sipfederationtls._tcp|SRV|1H|100 1 5061 sipfed.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**

    Nous vous recommandons de copier et de coller cette entrée, afin que l’espacement reste correct.       
   
    ![Tapez ou collez les valeurs dans la section Enregistrements de ressource personnalisés.](../../media/429d06a9-c0af-4961-b7d2-7a8dea6db37e.png)
  
6. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter.](../../media/89df6efd-e641-4441-baa2-d9a890424569.png)
  
7. Ajoutez l’autre enregistrement SRV.
    
    Dans la section **Enregistrements de ressources personnalisés**, créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Add ** pour valider cet enregistrement. 
    
    > [!NOTE]
    > Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
