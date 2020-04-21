---
title: Créer des enregistrements DNS pour les zones DNS Azure
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
ms.assetid: fbcef2d7-ebaf-40d0-ba1f-cdaeff9f50ef
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur les zones DNS Azure pour Microsoft.
ms.openlocfilehash: 7104fb18a6581b7ebc853f938b85171ae1886cfd
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43629142"
---
# <a name="create-dns-records-for-azure-dns-zones"></a>Créer des enregistrements DNS pour les zones DNS Azure

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Azure est votre fournisseur d’hébergement DNS, suivez la procédure décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online, etc.
  
Voici les principaux enregistrements à ajouter. 
  
- [Modifier les enregistrements de serveur de noms (NS) de votre domaine](#change-your-domains-nameserver-ns-records)
    
- [Ajouter un enregistrement TXT à des fins de vérification](#add-a-txt-record-for-verification)

- [Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient envoyés à Microsoft](#add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft)
    
- [Ajouter les quatre enregistrements CNAMe requis pour Microsoft](#add-the-four-cname-records-that-are-required-for-microsoft)
    
- [Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable](#add-a-txt-record-for-spf-to-help-prevent-email-spam)
    
- [Ajouter les deux enregistrements SRV requis pour Microsoft](#add-the-two-srv-records-that-are-required-for-microsoft)
    
Une fois ces enregistrements ajoutés sur Azure, votre domaine est configuré pour utiliser les services Microsoft.
  
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine
<a name="BKMK_NS"> </a>

> [!IMPORTANT]
> Vous devez effectuer cette procédure au niveau du bureau d'enregistrement de domaines auprès duquel vous avez acheté et inscrit votre domaine. 
  
Lorsque vous vous êtes inscrit à Azure, vous avez créé un groupe de ressources au sein d’une zone DNS, puis attribué votre nom de domaine à ce groupe de ressources. Ce nom de domaine est enregistré auprès d’un bureau d’enregistrement de domaines externes ; Azure ne propose pas de services d’inscription de domaine.
  
Pour vérifier et créer des enregistrements DNS pour votre domaine dans Microsoft, vous devez d’abord modifier les serveurs de noms dans votre bureau d’enregistrement de domaines afin qu’ils utilisent les serveurs de noms Azure attribués à votre groupe de ressources.
  
Pour modifier vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit.
  
1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.
    
2. Créez deux enregistrements de serveur de noms à l’aide des valeurs indiquées dans le tableau suivant, ou modifiez les enregistrements de serveur de noms existants afin qu’ils correspondent à ces valeurs. Vous trouverez ci-dessous un exemple de serveurs de noms attribués Azure.
    


**Premier serveur de noms :** Utilisez la valeur de serveur de noms attribuée par Azure.  
**Deuxième serveur de noms :** Utilisez la valeur de serveur de noms attribuée par Azure.  

![Azure-BP-redelegate-1-1](../../media/3e4805ea-608a-4df9-8f68-1fbf70d13d08.png)
  
> [!TIP]
> You should use at least two name server records. Si d’autres serveurs de noms sont répertoriés sur le site Web de votre bureau d’enregistrement de domaines, vous devez les supprimer. 
  
3. Enregistrez vos modifications.
    
> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Votre messagerie Microsoft et les autres services seront tous configurés pour fonctionner avec votre domaine. 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d’utiliser votre domaine avec Microsoft, vous devez vous assurer que vous en êtes propriétaire. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que vous êtes propriétaire du domaine.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur Azure à l’aide de [ce lien](https://portal.azure.com ). Avant toute chose, vous serez invité à vous connecter.
    
    ![Azure-BP-configure-1-1](../../media/ed377cad-0c47-4f9f-b322-c3e06b309b1f.png)
  
2. À l’aide de la **barre de recherche** de la page **tableau de bord** , tapez dans **zones DNS**. Dans l’affichage des résultats, sélectionnez **zones DNS** sous la partie **services** . Une fois que vous avez été redirigé, sélectionnez le domaine que vous souhaitez mettre à jour.
    
    ![Azure-BP-configure-1-2](../../media/eb4baad2-92d7-49c9-95e5-1dd8510d5ec9.png)
  
3. Sur la page **paramètres** de votre domaine, dans la zone **zone DNS** , sélectionnez **+ jeu d’enregistrements**.
    
    ![Azure-BP-configure-1-3](../../media/b04db89a-3dbc-4cd2-aaca-af17fda53a60.png)
  
4. Dans la zone **Ajouter un jeu d’enregistrements** , dans les zones du nouveau jeu d’enregistrements, sélectionnez les valeurs du tableau suivant. 
    
    (Choisissez les valeurs **type** et **unité de durée de vie** dans les listes déroulantes.) 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Unité de durée de vie**|**Value (Valeur)**|
    |:-----|:-----|:-----|:-----|:-----|
    |@  <br/> |TXT  <br/> |0,1  <br/> |Heures  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre **adresse de destination ou de pointage** spécifique ici, à partir du tableau.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Azure-BP-Verify-1-1](../../media/7d5a253c-e88f-4565-a00a-79bba52f9970.png)
  
5. Sélectionnez **OK**.
  
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
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

1. Pour commencer, accédez à la page de vos domaines sur Azure à l’aide de [ce lien](https://portal.azure.com ). Avant toute chose, vous serez invité à vous connecter.
    
    ![Azure-BP-configure-1-1](../../media/ed377cad-0c47-4f9f-b322-c3e06b309b1f.png)
  
2. Sur la page **tableau de bord** , dans la zone **toutes les ressources** , sélectionnez le domaine que vous souhaitez mettre à jour. 
    
    ![Azure-BP-configure-1-2](../../media/eb4baad2-92d7-49c9-95e5-1dd8510d5ec9.png)
  
3. Sur la page **paramètres** de votre domaine, dans la zone **zone DNS** , sélectionnez **+ jeu d’enregistrements**.
    
    ![Azure-BP-configure-1-3](../../media/b04db89a-3dbc-4cd2-aaca-af17fda53a60.png)
  
4. Dans la zone **Ajouter un jeu d’enregistrements** , dans les zones du nouveau jeu d’enregistrements, sélectionnez les valeurs du tableau suivant. 
    
    (Choisissez les valeurs **type** et **unité de durée de vie** dans les listes déroulantes.) 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Unité de durée de vie**|**Preference (Préférence)**|**Exchange mail**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |@  <br/> |MX  <br/> |0,1  <br/> |Heures  <br/> |10   <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenir votre * \<clé\> de domaine* à partir de votre compte Microsoft.   [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)  
   
    ![Azure-BP-configure-2-1](../../media/712c23ae-9d38-4af2-94e0-0704e70744fe.png)
  
5. Sélectionnez **OK**.
    
    ![Azure-BP-configure-2-2](../../media/2f24225f-69ac-41dc-91c5-93d327360f74.png)
  
6. Si d’autres enregistrements MX sont répertoriés dans la section **MX Records (enregistrements MX** ), vous devez les supprimer. 
    
    Tout d’abord, dans la zone **zone DNS** , sélectionnez le **jeu d’enregistrements MX**.
    
    ![Azure-BP-configure-2-3](../../media/9890da61-6fcd-4c61-888e-ccbb84f80cd0.png)
  
    Ensuite, sélectionnez l’enregistrement MX que vous souhaitez supprimer.
    
    ![Azure-BP-configure-2-4](../../media/afe54f12-66d2-4ff3-80e9-427448e4c32c.png)
  
7. Sélectionnez le **menu contextuel (...)**, puis cliquez sur **supprimer**.
    
    ![Azure-BP-configure-2-5](../../media/25219e25-bc14-4bc7-84ed-ee65eb28a8ed.png)
  
8. Sélectionnez **Enregistrer**.
    
    ![Azure-BP-configure-2-6](../../media/c6133096-5e43-4637-9c01-b63ee4b03517.png)
  
## <a name="add-the-four-cname-records-that-are-required-for-microsoft"></a>Ajouter les quatre enregistrements CNAMe requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

1. Pour commencer, accédez à la page de vos domaines sur Azure à l’aide de [ce lien](https://portal.azure.com ). Avant toute chose, vous serez invité à vous connecter.
    
    ![Azure-BP-configure-1-1](../../media/ed377cad-0c47-4f9f-b322-c3e06b309b1f.png)
  
2. Sur la page **tableau de bord** , dans la zone **toutes les ressources** , sélectionnez le domaine que vous souhaitez mettre à jour. 
    
    ![Azure-BP-configure-1-2](../../media/eb4baad2-92d7-49c9-95e5-1dd8510d5ec9.png)
  
3. Sur la page **paramètres** de votre domaine, dans la zone **zone DNS** , sélectionnez **+ jeu d’enregistrements**.
    
    ![Azure-BP-configure-1-3](../../media/b04db89a-3dbc-4cd2-aaca-af17fda53a60.png)
  
4. Ajoutez le premier des quatre enregistrements CNAMe.
    
    Dans la zone **Ajouter un jeu d’enregistrements** , dans les zones du nouveau jeu d’enregistrements, tapez ou copiez-collez les valeurs de la première ligne dans le tableau suivant. 
    
    (Choisissez les valeurs **type** et **unité de durée de vie** dans les listes déroulantes.) 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Unité de durée de vie**|**Alias**|
    |:-----|:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |0,1  <br/> |Heures  <br/> |autodiscover.outlook.com  <br/> |
    |sip  <br/> |CNAME  <br/> |0,1  <br/> |Heures  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |0,1  <br/> |Heures  <br/> |webdir.online.lync.com  <br/> |
    
   
    ![Azure-BP-configure-3-1](../../media/a1c4d869-da97-43b3-952c-d513a20231dc.png)
  
5. Sélectionnez **OK**.
    
    ![Azure-BP-configure-3-2](../../media/b89b51da-1c07-43cf-9fab-75d2e5eb3544.png)
  
6. Ajoutez chacun des trois autres enregistrements CNAMe.
    
    Dans la zone **zone DNS** , sélectionnez **+ jeu d’enregistrements**. Ensuite, dans le jeu d’enregistrements vide, créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **OK** pour valider cet enregistrement. 
    
    Répétez cette procédure jusqu’à ce que vous ayez créé les quatre enregistrements CNAMe.
    
7.  Module Ajoutez 2 enregistrements CNAMe pour MDM.

> [!IMPORTANT]
> Si vous disposez de la gestion des appareils mobiles pour Microsoft, vous devez créer deux enregistrements CNAMe supplémentaires. Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. (Si vous ne disposez pas de MDM, vous pouvez ignorer cette étape.) 
  
|**Name**|**Type**|**TTL (Durée de vie)**|**Unité de durée de vie**|**Alias**|
|:-----|:-----|:-----|:-----|:-----|
|enterpriseregistration  <br/> |CNAME  <br/> |0,1  <br/> |Heures  <br/> |enterpriseregistration.windows.net  <br/> |
|enterpriseenrollment  <br/> |CNAME  <br/> |0,1  <br/> |Heures  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
   
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous disposez déjà d’un enregistrement SPF pour votre domaine, n’en créez pas pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
1. Pour commencer, accédez à la page de vos domaines sur Azure à l’aide de [ce lien](https://portal.azure.com ). Avant toute chose, vous serez invité à vous connecter.
    
    ![Azure-BP-configure-1-1](../../media/ed377cad-0c47-4f9f-b322-c3e06b309b1f.png)
  
2. Sur la page **tableau de bord** , dans la zone **toutes les ressources** , sélectionnez le domaine que vous souhaitez mettre à jour. 
    
    ![Azure-BP-configure-1-2](../../media/eb4baad2-92d7-49c9-95e5-1dd8510d5ec9.png)
  
3. Dans la zone **zone DNS** , sélectionnez le **jeu d’enregistrements TXT**.
    
    ![Azure-BP-configure-4-1](../../media/03095196-5010-4072-8503-79b812084dbf.png)
  
4. Dans la zone Propriétés de l' **ensemble d’enregistrements** , dans les zones du nouveau jeu d’enregistrements, sélectionnez les valeurs du tableau suivant. 
    
    (Choisissez les valeurs **type** et **unité de durée de vie** dans les listes déroulantes.) 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Unité de durée de vie**|**Value (Valeur)**|
    |:-----|:-----|:-----|:-----|:-----|
    |@  <br/> |TXT  <br/> |0,1  <br/> |Heures  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           

    ![Azure-BP-configure-4-2](../../media/78e84c43-e0ce-433f-8e74-9157fb093cca.png)
  
5. Sélectionnez **Enregistrer**.
    
    ![Azure-BP-configure-4-3](../../media/d7421c7f-ea63-4e11-8595-a482b8c165e0.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajouter les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

1. Pour commencer, accédez à la page de vos domaines sur Azure à l’aide de [ce lien](https://portal.azure.com ). Avant toute chose, vous serez invité à vous connecter.
    
    ![Azure-BP-configure-1-1](../../media/ed377cad-0c47-4f9f-b322-c3e06b309b1f.png)
  
2. Sur la page **tableau de bord** , dans la zone **toutes les ressources** , sélectionnez le domaine que vous souhaitez mettre à jour. 
    
    ![Azure-BP-configure-1-2](../../media/eb4baad2-92d7-49c9-95e5-1dd8510d5ec9.png)
  
3. Sur la page **paramètres** de votre domaine, dans la zone **zone DNS** , sélectionnez **+ jeu d’enregistrements**.
    
    ![Azure-BP-configure-1-3](../../media/b04db89a-3dbc-4cd2-aaca-af17fda53a60.png)
  
4. Ajoutez le premier des deux enregistrements SRV.
    
    Dans la zone **Ajouter un jeu d’enregistrements** , dans les zones du nouveau jeu d’enregistrements, sélectionnez les valeurs de la première ligne du tableau suivant. 
    
    (Choisissez les valeurs **type** et **unité de durée de vie** dans les listes déroulantes.) 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Unité de durée de vie**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip. _tls  <br/> |SRV  <br/> |0,1  <br/> |Heures  <br/> |100  <br/> |0,1  <br/> |443  <br/> |sipdir.online.lync.com  <br/> |
    |_sipfederationtls. _tcp  <br/> |SRV  <br/> |0,1  <br/> |Heures  <br/> |100  <br/> |0,1  <br/> |5061  <br/> |sipfed.online.lync.com  <br/> 

    ![Azure-BP-configure-5-1](../../media/a436e0b4-8bb8-4a66-9c22-4e3b2dcf54ff.png)
  
5. Sélectionnez **OK**.
    
    ![Azure-BP-configure-5-2](../../media/a35b6c8a-d001-4b3c-8a67-96b4890e564c.png)
  
6. Ajoutez l'autre enregistrement SRV.
    
    Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
