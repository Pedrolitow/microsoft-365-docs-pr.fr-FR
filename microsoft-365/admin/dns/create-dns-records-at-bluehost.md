---
title: Créer des enregistrements DNS sur Bluehost pour Office 365
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
ms.assetid: 657934ff-d9d2-4563-9ccf-ef4832a03a99
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur Bluehost pour Office 365.
ms.openlocfilehash: 0e64ed8787dca9822e71a63c57de7a7a3e2b3fe4
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42350955"
---
# <a name="create-dns-records-at-bluehost-for-office-365"></a>Créer des enregistrements DNS sur Bluehost pour Office 365

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Bluehost est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
Une fois ces enregistrements ajoutés sur Bluehost, votre domaine est configuré pour utiliser les services Office 365.
  
Pour en savoir plus sur l'hébergement web et le DNS pour les sites web avec Office 365, voir [Utiliser un site web public avec Office 365](https://support.office.com/article/choose-a-public-website-3325d50e-d131-403c-a278-7f3296fe33a9).
  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d'autres problèmes suite à l'ajout des enregistrements DNS, consultez [Rechercher et corriger les problèmes suite à l'ajout de votre domaine ou des enregistrements DNS dans Office 365](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Bluehost en utilisant [ce lien](https://my.bluehost.com/cgi/dm). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **domains (domaines)**, dans la zone **domain (domaine)**, recherchez la ligne associée au domaine que vous modifiez, puis cochez la case correspondant à ce domaine. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
3. Dans la zone ***domain_name*** , sur la ligne **éditeur de zone DNS** , sélectionnez **gérer les enregistrements DNS**.
    
4. Dans la page * * éditeur de zone DNS * *, dans la zone **Ajouter un enregistrement DNS** , dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Host Record** <br/> |**TTL (Durée de vie)** <br/> |**Type** <br/> |**TXT Value** <br/> |
    |@  <br/> |14400  <br/> |TXT  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
5. Sélectionnez **Ajouter un enregistrement**.
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Office 365 et demandez à Office 365 de rechercher l’enregistrement.
  
Lorsqu’Office 365 trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d'autres problèmes suite à l'ajout des enregistrements DNS, consultez [Rechercher et corriger les problèmes suite à l'ajout de votre domaine ou des enregistrements DNS dans Office 365](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365
<a name="BKMK_add_MX"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site Bluehost en utilisant [ce lien](https://my.bluehost.com/cgi/dm). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **domains (domaines)**, dans la zone **domain (domaine)**, recherchez la ligne associée au domaine que vous modifiez, puis cochez la case correspondant à ce domaine. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
3. Dans la zone ***domain_name*** , sur la ligne **éditeur de zone DNS** , sélectionnez **gérer les enregistrements DNS**.
    
4. On the **DNS Zone Editor** page, in the **Add DNS Record** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Host Record**|**TTL (Durée de vie)**|**Type (Type)**|**Points to (Destination)**|**Priority (Priorité)**|
    |:-----|:-----|:-----|:-----|:-----|
    |@  <br/> |14400  <br/> |MX  <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/>**Remarque :** Obtenez votre \<*clé de domaine*\> à partir de votre compte Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> |
   
   ![Choisissez type dans la liste déroulante.](../../media/70791420-d83c-4a5d-a46c-5cc3bc67f565.png)
  
5. Sélectionnez **Ajouter un enregistrement**.
    
    ![Sélectionnez Ajouter un enregistrement](../../media/c7ef9733-1665-4dbf-accc-caadf1574abc.png)
  
6. Si d'autres enregistrements MX sont répertoriés dans la section **MX (Mail Exchanger) (MX (Mail Exchanger))**, supprimez-les individuellement. 
    
    Pour l’un des autres enregistrements MX, sélectionnez **Supprimer.**
    
    ![Sélectionnez Delete pour chaque enregistrement MX supplémentaire](../../media/6be17f54-3f33-47af-a9db-4689141530c2.png)
  
7. Dans la boîte de dialogue de confirmation, sélectionnez **OK**.
    
    ![Sélectionnez OK.](../../media/a50df7a3-2906-4cc0-87d4-1231ab234230.png)
  
8. Utilisez la même procédure pour supprimer tous les enregistrements MX déjà répertoriés.
    
## <a name="add-the-six-cname-records-that-are-required-for-office-365"></a>Ajouter les 6 enregistrements CNAME requis pour Office 365
<a name="BKMK_add_CNAME"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site Bluehost en utilisant [ce lien](https://my.bluehost.com/cgi/dm). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **domains (domaines)**, dans la zone **domain (domaine)**, recherchez la ligne associée au domaine que vous modifiez, puis cochez la case correspondant à ce domaine. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
3. Dans la zone ***domain_name*** , sur la ligne **éditeur de zone DNS** , sélectionnez **gérer les enregistrements DNS**.
    
4. Dans la section **A (hôte)** , recherchez la ligne de l’enregistrement de **découverte automatique** , puis sélectionnez **supprimer** pour cette ligne. 
    
    > [!IMPORTANT]
    > Vous devez supprimer l'enregistrement **autodiscover** existant  *avant*  d'ajouter l'enregistrement **autodiscover** requis par Office 365. Bluehost ne vous permet pas de conserver deux enregistrements **autodiscover** simultanément. 
  
    ![Sélectionnez supprimer](../../media/416a447e-3710-4ae7-8bf1-459381af4f6e.png)
  
5. Sélectionnez **OK**.
    
    ![Sélectionnez OK.](../../media/0c8f409d-c39f-4ed2-9c95-9af3e61c2411.png)
  
6. Créer le premier des six enregistrements CNAME.
    
    Sur la page **DNS Zone Editor (Éditeur de zone DNS)**, dans la zone **Add DNS Record (Ajouter un enregistrement DNS)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs dans la première ligne du tableau suivant. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Host Record**|**TTL (Durée de vie)**|**Type (Type)**|**Points to (Destination)**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |14400  <br/> |CNAME  <br/> |autodiscover.outlook.com  <br/> |
    |sip  <br/> |14400  <br/> |CNAME  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover  <br/> |14400  <br/> |CNAME  <br/> |webdir.online.lync.com  <br/> |
    |enterpriseregistration  <br/> |14400  <br/> |CNAME  <br/> |enterpriseregistration.windows.net  <br/> |
    |enterpriseenrollment  <br/> |14400  <br/> |CNAME  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
   
    ![Créer le premier enregistrement CNAMe](../../media/4f12e9b1-9dec-4bc2-aa15-8bffa71fe131.png)
  
7. Sélectionnez **Ajouter un enregistrement**.
    
    ![Sélectionnez Ajouter un enregistrement](../../media/c2782250-a9a6-4aee-bb15-f57cb0008587.png)
  
8. Ajoutez successivement les 5 autres enregistrements CNAME.
    
    Toujours dans la section **Add DNS record (ajouter un enregistrement DNS** ), créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Add record (Ajouter** un enregistrement) pour valider cet enregistrement. 
    
    Répétez cette procédure jusqu'à avoir créé les 6 enregistrements CNAME.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. If you already have an SPF record for your domain, don't create a new one for Office 365. Ajoutez plutôt les valeurs Office 365 requises à l'enregistrement actuel de manière à n'avoir qu'un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Office 365](https://support.office.com/article/c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0). Pour valider votre enregistrement SPF, vous pouvez utiliser l’un de ces[outils de validation SPF](../setup/domains-faq.md). 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Bluehost en utilisant [ce lien](https://my.bluehost.com/cgi/dm). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **domains (domaines)**, dans la zone **domain (domaine)**, recherchez la ligne associée au domaine que vous modifiez, puis cochez la case correspondant à ce domaine. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
3. Dans la zone ***domain_name*** , sur la ligne **éditeur de zone DNS** , sélectionnez **gérer les enregistrements DNS**.
    
4. On the **DNS Zone Editor** page, in the **Add DNS Record** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
        
    |**Host Record**|**TTL (Durée de vie)**|**Type**|**TXT Value**|
    |:-----|:-----|:-----|:-----|
    |@  <br/> |14400  <br/> |TXT  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/>**Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![Copier la valeur TXT](../../media/b2dabd7a-ee3d-4209-aa1e-0233eb8cf3b9.png)
  
5. Sélectionnez **Ajouter un enregistrement**.
    
    ![Sélectionnez Ajouter un enregistrement](../../media/c050e9a2-2274-4640-8f0f-6752d382df5d.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>Ajoutez les 2 enregistrements SRV requis pour Office 365
<a name="BKMK_add_SRV"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site Bluehost en utilisant [ce lien](https://my.bluehost.com/cgi/dm). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **domains (domaines)**, dans la zone **domain (domaine)**, recherchez la ligne associée au domaine que vous modifiez, puis cochez la case correspondant à ce domaine. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
3. Dans la zone ***domain_name*** , sur la ligne **éditeur de zone DNS** , sélectionnez **gérer les enregistrements DNS**.
    
4. Créez le premier des deux enregistrements SRV.
    
    Sur la page **DNS Zone Editor (Éditeur de zone DNS)**, dans la zone **Add DNS Record (Ajouter un enregistrement DNS)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs dans la première ligne du tableau suivant. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Service**|**Protocol (Protocole)**|**Host (Hôte)**|**TTL (Durée de vie)**|**Type (Type)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Points to (Destination)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |@  <br/> |14400  <br/> |SRV  <br/> |100  <br/> |0,1  <br/> |443  <br/> |sipdir.online.lync.com  <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |@  <br/> |14400  <br/> |SRV  <br/> |100  <br/> |0,1  <br/> |5061  <br/> |sipfed.online.lync.com  <br/> |
   
    ![Copier la valeur du nouvel enregistrement](../../media/e2911bca-c00b-4b8a-837f-f1d438c474c4.png)
  
5. Sélectionnez **Ajouter un enregistrement**.
    
    ![Sélectionnez Ajouter un enregistrement](../../media/0fd6a587-03fd-4bce-8321-b14e6ad21f5c.png)
  
6. Ajoutez l'autre enregistrement SRV.
    
    Toujours dans la section **Add DNS record (ajouter un enregistrement DNS** ), créez un enregistrement en utilisant les valeurs de l’autre ligne du tableau, puis sélectionnez de nouveau **Add record (Ajouter** un enregistrement) pour valider cet enregistrement. 
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d'autres problèmes suite à l'ajout des enregistrements DNS, consultez [Rechercher et corriger les problèmes suite à l'ajout de votre domaine ou des enregistrements DNS dans Office 365](../get-help-with-domains/find-and-fix-issues.md). 
  

