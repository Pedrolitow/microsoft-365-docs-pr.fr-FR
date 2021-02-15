---
title: Créer des enregistrements DNS chez DNSMadeEasy pour Microsoft
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
ms.assetid: e158b079-b054-4b7e-8e01-e55169ce18d7
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services sur DNSMadeEasy pour Microsoft.
ms.openlocfilehash: 719b416564447b3a6f4108b747ae921b4f6f6bb8
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49657947"
---
# <a name="create-dns-records-at-dnsmadeeasy-for-microsoft"></a>Créer des enregistrements DNS chez DNSMadeEasy pour Microsoft

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si DNSMadeEasy est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
Une fois ces enregistrements ajoutés sur DNSMadeEasy, votre domaine est installé pour fonctionner avec les services Microsoft.
  

  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
> [!IMPORTANT]
> Pour les comptes DNSMadeEasy, le domaine que vous avez ajouté a été acheté auprès d'un bureau d'enregistrement de domaines distinct. DNSMadeEasy ne propose pas de services d'enregistrement de domaines. Votre connexion au site DNSMadeEasy et la création de l'enregistrement DNS constituent une preuve de propriété suffisante. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site DNSMadeEasy en utilisant [ce lien](https://cp.dnsmadeeasy.com/). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page Console  **de** gestion, dans la zone Domaines récemment mis à jour, sélectionnez le domaine à mettre à jour. 
    
3. Dans la page **DNS géré,** dans la zone **Enregistrements TXT,** sélectionnez le contrôle **+** ( ) ( Ajouter **nouveau**).
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
4. In the **Add TXT Records** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    ||||
    |:-----|:-----|:-----|
    |**Name** <br/> |**Valeur** <br/> |**TTL** <br/> |
    |(Laissez ce champ vide.)  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |1800  <br/> |
   
5. Sélectionnez **Envoyer**.
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
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

1. Pour commencer, accédez à la page de vos domaines sur le site DNSMadeEasy en utilisant [ce lien](https://cp.dnsmadeeasy.com/). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page Console  **de** gestion, dans la zone Domaines récemment mis à jour, sélectionnez le domaine à mettre à jour. 
    
    Dans la page Console  **de** gestion, dans la zone Domaines récemment mis à jour, sélectionnez le domaine à mettre à jour. 
    
    ![DNSMadeEasy-BP-Configure-1-2](../../media/8d8f403e-d7cd-429e-913b-dacb1f4644a2.png)
  
3. Dans la page **DNS géré,** dans la zone **Enregistrements MX,** sélectionnez **le contrôle (+)** ( **Ajouter nouveau**).
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    ![DNSMadeEasy-BP-Configure-2-1](../../media/404c73bf-1db4-4d68-82d8-68303f418ed4.png)
  
4. Dans la zone **Add MX Records (Ajouter des enregistrements MX)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    |**Name**|**Server**|**MX Level (Niveau MX)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|
    |(Laissez ce champ vide.)  <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> **Remarque :** Obtenez votre \<*domain-key*\> depuis votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |10   <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq). <br/> |1800  <br/> |
   
    ![DNSMadeEasy-BP-Configure-2-2](../../media/69b53af9-1eec-435c-8434-1b6058c1ec82.png)
  
5. Sélectionnez **Envoyer**.
    
    ![DNSMadeEasy-BP-Configure-2-3](../../media/381054a6-bb85-4ebb-b576-42cbba78ed1b.png)
  
6. Si d'autres enregistrements MX sont répertoriés dans la section **MX Records (Enregistrements MX)**, supprimez-les tous en les sélectionnant individuellement. 
    
    ![DNSMadeEasy-BP-Configure-2-4-1](../../media/58a07769-0b30-4111-b555-bfc3b82a7d4c.png)
  
7. Lorsque tous les enregistrements sont sélectionnés, **sélectionnez Supprimer sélectionné.**
    
    ![DNSMadeEasy-BP-Configure-2-4-2](../../media/e9064c07-1ce7-4387-b47a-90d4193da374.png)
  
8. Dans la **boîte de dialogue Supprimer les enregistrements MX,** **sélectionnez Supprimer** pour confirmer vos modifications. 
    
    ![DNSMadeEasy-BP-Configure-2-5](../../media/03c405e5-868f-468f-b6d2-046d27b201fb.png)
  
## <a name="add-the-five-cname-records-that-are-required-for-microsoft"></a>Ajouter les cinq enregistrements CNAME requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site DNSMadeEasy en utilisant [ce lien](https://cp.dnsmadeeasy.com/). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page Console  **de** gestion, dans la zone Domaines récemment mis à jour, sélectionnez le domaine à mettre à jour. 
    
3. Dans la page **DNS géré,** dans la zone Enregistrements **CNAME,** sélectionnez **le contrôle (+)** ( **Ajouter nouveau**).
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    ![DNSMadeEasy-BP-Configure-3-1](../../media/a5feb238-690d-4b64-a625-91a82b3f4068.png)
  
4. Ajoutez le premier des cinq enregistrements CNAME.
    
    Dans la zone **Add CNAME Records (Ajouter des enregistrements CNAME)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    |**Name (Nom)**|**Alias to (Alias vers)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |autodiscover.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1800  <br/> |
    |sip  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1800  <br/> |
    |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1800  <br/> |
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1800  <br/> |
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1800  <br/> |
   
    ![DNSMadeEasy-BP-Configure-3-2](../../media/de6dddcd-bf0a-4993-ab4c-a6d10167bf34.png)
  
5. Sélectionnez **Envoyer**.
    
    ![DNSMadeEasy-BP-Configure-3-3](../../media/e44ef73e-99cb-41ce-a3f2-549cb2f29eef.png)
  
6. Ajoutez chacun des quatre autres enregistrements CNAME.
    
    Dans la section Enregistrements  **CNAME,** sélectionnez le contrôle **(+)** ( Ajouter nouveau ), créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau Envoyer pour terminer cet enregistrement.  
    
    Répétez ce processus jusqu’à ce que vous avez créé les cinq enregistrements CNAME.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de n’avoir qu’un seul  *enregistrement*  SPF qui inclut les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](https://docs.microsoft.com/microsoft-365/enterprise/external-domain-name-system-records). Pour valider votre enregistrement SPF, vous pouvez utiliser l’un de ces outils[de validation SPF.](../setup/domains-faq.yml) 
  
1. Pour commencer, accédez à la page de vos domaines sur le site DNSMadeEasy en utilisant [ce lien](https://cp.dnsmadeeasy.com/). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page Console  **de** gestion, dans la zone Domaines récemment mis à jour, sélectionnez le domaine à mettre à jour. 
    
3. Dans la page **DNS géré,** dans la zone **Enregistrements TXT,** sélectionnez **le contrôle (+)** ( **Ajouter nouveau**).
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    ![DNSMadeEasy-BP-Configure-4-1](../../media/657b87a5-dcb4-4ae7-8f27-bd857f0f4189.png)
  
4. In the **Add TXT Records** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    |**Name**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|
    |(Laissez ce champ vide.)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |1800  <br/> |
   
    ![DNSMadeEasy-BP-Configure-4-2](../../media/b317bcb9-18c6-4609-a8f4-963823032669.png)
  
5. Sélectionnez **Envoyer**.
    
    ![DNSMadeEasy-BP-Configure-4-3](../../media/8a1c53c3-1222-4127-a190-70f6f5059433.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site DNSMadeEasy en utilisant [ce lien](https://cp.dnsmadeeasy.com/). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page Console  **de** gestion, dans la zone Domaines récemment mis à jour, sélectionnez le domaine à mettre à jour. 
    
3. Dans la page **DNS géré,** dans la zone **Enregistrements SRV,** sélectionnez **le contrôle (+)** ( **Ajouter nouveau**).
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    ![DNSMadeEasy-BP-Configure-5-1](../../media/5c9e8f50-adbd-4f23-8ce3-2844b2896f3f.png)
  
4. Ajoutez le premier des deux enregistrements SRV.
    
    Dans la zone **Add SRV Records (Ajouter des enregistrements SRV)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    |**Name (Nom)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Host (Hôte)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip._tls  <br/> |100  <br/> |1   <br/> |443  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1800  <br/> |
    |_sipfederationtls._tcp  <br/> |100  <br/> |1   <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1800  <br/> |
   
    ![DNSMadeEasy-BP-Configure-5-2](../../media/e1155f94-575f-441a-9a61-d948391d42ca.png)
  
5. Sélectionnez **Envoyer**.
    
    ![DNSMadeEasy-BP-Configure-5-3](../../media/7eae54e1-08bd-4902-afdf-fd5cc251ab59.png)
  
6. Ajoutez l'autre enregistrement SRV.
    
    Dans la section Enregistrements  **SRV,** sélectionnez le contrôle **(+)** ( Ajouter nouveau ), créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau Envoyer pour terminer cet enregistrement.  
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  

