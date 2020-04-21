---
title: Créer des enregistrements DNS sur 123-reg.co.uk pour Microsoft
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
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur 123-reg.co.uk pour Microsoft.
ms.openlocfilehash: 887e7e6fc42fb55d4cc09ba66b68a2bb9702bbb9
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43629742"
---
# <a name="create-dns-records-at-123-regcouk-for-microsoft"></a>Créer des enregistrements DNS sur 123-reg.co.uk pour Microsoft

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si 123-reg.co.uk est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
Une fois ces enregistrements ajoutés sur 123-reg.co.uk, votre domaine est configuré pour utiliser les services Microsoft.
  
Pour en savoir plus sur l’hébergement Web et le DNS pour les sites Web avec Microsoft, consultez [la rubrique utiliser un site Web public avec Microsoft](https://support.office.com/article/choose-a-public-website-3325d50e-d131-403c-a278-7f3296fe33a9).
  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messagerie ou d’autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d’utiliser votre domaine avec Microsoft, vous devez vous assurer que vous en êtes propriétaire. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que vous êtes propriétaire du domaine.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. On the **Domain name overview** page, select the name of the domain that you want to edit. 
    
3. Choose **DNS** from the **Select action** drop-down list. 
    
4. Sur la page **gérer votre DNS** , sélectionnez l’onglet **DNS avancé** . 
    
5. In the **Advanced DNS** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    ||||
    |:-----|:-----|:-----|
    |**Hostname (Nom d'hôte)** <br/> |**Type (Type)** <br/> |**Destination TXT/SPF** <br/> |
    |@  <br/> |TXT/SPF  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre **adresse de destination ou de pointage** spécifique ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
6. Sélectionnez **Ajouter**.
    
7. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
À présent que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous allez retourner à Microsoft et demander une recherche pour l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT correct, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> .

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messagerie ou d’autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient envoyés à Microsoft
<a name="BKMK_add_MX"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. On the **Domain name overview** page, select the name of the domain that you want to edit. 
    
3. Choose **DNS** from the **Select action** drop-down list. 
    
4. Sur la page **gérer votre DNS** , sélectionnez l’onglet **DNS avancé** . 
    
5. In the **Advanced DNS** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Hostname (Nom d'hôte)**|**Type (Type)**|**Priority (Priorité)**|**Destination MX (Enregistrement MX de la destination)**|
    |:-----|:-----|:-----|:-----|
    |@  <br/> |MX  <br/> |0,1  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> | *\<clé_de_domaine\>*  .mail.protection.outlook.com.  <br/> **This value MUST end with a period (.)** <br/> **Remarque :** Obtenir votre \<clé\> de domaine à partir de votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Copier et coller des valeurs à partir du tableau](../../media/65366165-85a6-4a39-b9a7-6c5f47fbe790.png)
  
6. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter](../../media/a8ae6c0c-4365-4137-af8a-6e003996e3d0.png)
  
7. Si d'autres enregistrements MX sont répertoriés, supprimez-les individuellement en sélectionnant l'icône **Delete (Supprimer)** représentant une corbeille des enregistrements. 
    
    ![Sélectionnez Supprimer (l’icône Corbeille)](../../media/3be635e6-b591-49af-8430-a158272834b4.png)
  
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a>Ajouter les six enregistrements CNAMe requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. On the **Domain name overview** page, select the name of the domain that you want to edit. 
    
3. Choose **DNS** from the **Select action** drop-down list. 
    
4. Sur la page **gérer votre DNS** , sélectionnez l’onglet **DNS avancé** . 
    
5. Ajoutez le premier des six enregistrements CNAME.
    
    In the **Advanced DNS** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Hostname (Nom d'hôte)**|**Type (Type)**|**Destination CNAME (Enregistrement CNAME de la destination)**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |autodiscover.outlook.com.  <br/> **This value MUST end with a period (.)** <br/> |
    |sip  <br/> |CNAME  <br/> |sipdir.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |webdir.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |
    |enterpriseregistration  <br/> |CNAME  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |enterpriseenrollment  <br/> |CNAME  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
   
    ![Copiez et collez les valeurs de la table.](../../media/24bf388c-5f7f-4fc0-b4ec-4b17226b6246.png)
  
6. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter](../../media/825a9854-559d-4a22-90ac-5e7a0a54269a.png)
  
7. Ajoutez les cinq autres enregistrements CNAME.
    
    Dans la section **DNS avancé** , créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Ajouter** pour valider cet enregistrement. 
    
    Répétez cette procédure jusqu'à avoir créé les 6 enregistrements CNAME.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous disposez déjà d’un enregistrement SPF pour votre domaine, ne créez pas de nouvel enregistrement pour Microsfot. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [enregistrements DNS externes pour Microsoft](https://support.office.com/article/c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0#bkmk_spfrecords). Pour valider votre enregistrement SPF, vous pouvez utiliser l'un des outils de [validation SPF suivants](../setup/domains-faq.md). 
  
1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. On the **Domain name overview** page, select the name of the domain that you want to edit. 
    
3. Choose **DNS** from the **Select action** drop-down list. 
    
4. Sur la page **gérer votre DNS** , sélectionnez l’onglet **DNS avancé** . 
    
5. In the **Advanced DNS** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Hostname (Nom d'hôte)**|**Type (Type)**|**Destination TXT/SPF**|
    |:-----|:-----|:-----|
    |@  <br/> |TXT/SPF  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![123Reg-BP-configure-4-1](../../media/4697701c-eba0-4b03-8d75-4f7fc3bef94a.png)
  
6. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter](../../media/7906dd91-fd23-44c3-bb37-ef185655c6eb.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajouter les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. On the **Domain name overview** page, select the name of the domain that you want to edit. 
    
3. Choose **DNS** from the **Select action** drop-down list. 
    
4. Sur la page **gérer votre DNS** , sélectionnez l’onglet **DNS avancé** . 
    
5. Ajoutez le premier des deux enregistrements SRV :
    
    In the **Advanced DNS** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    ||||||
    |:-----|:-----|:-----|:-----|:-----|
    |Hostname (Nom d'hôte)|Type (Type)|Priority (Priorité)|TTL (Durée de vie)|Destination SRV (Enregistrement SRV de la destination)|
    |_sip. _tls|SRV|100|3600|1 443 sipdir.online.lync.com. **This value MUST end with a period (.)**<br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
    |_sipfederationtls. _tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **This value MUST end with a period (.)** <br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![Copiez et collez les valeurs de la table.](../../media/c1786b86-52ef-4dca-8b99-b479554fa531.png)
  
6. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter](../../media/5fd9d3a2-a8bb-466b-829f-b3a6e54b5104.png)
  
7. Pour ajouter l'autre enregistrement SRV :
    
    Dans la section **DNS avancé** , créez un enregistrement en utilisant les valeurs de la deuxième ligne du tableau, puis sélectionnez de nouveau **Ajouter** pour valider cet enregistrement. 
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messagerie ou d’autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
