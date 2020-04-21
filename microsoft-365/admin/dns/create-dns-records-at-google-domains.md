---
title: Créer des enregistrements DNS auprès de Google Domains pour Microsoft
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
ms.assetid: 0db29490-2612-48bc-9b77-1862e7a41a8c
description: Découvrez comment vérifier votre domaine et configurer des enregistrements DNS pour la messagerie, Lync et d’autres services de Google Domains pour Microsoft.
ms.openlocfilehash: 20a3ba9baefcdb26936d2d0a5fda7ed1b5db971e
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43629538"
---
# <a name="create-dns-records-at-google-domains-for-microsoft"></a>Créer des enregistrements DNS auprès de Google Domains pour Microsoft

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Google Domains est votre fournisseur d'hébergement DNS, procédez de la manière décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Lync, etc.
  
Après avoir ajouté ces enregistrements à Google Domains, votre domaine est configuré pour utiliser les services Microsoft.
  
Pour en savoir plus sur l’hébergement Web et le DNS pour les sites Web avec Microsoft, consultez [la rubrique utiliser un site Web public avec Microsoft](https://support.office.com/article/choose-a-public-website-3325d50e-d131-403c-a278-7f3296fe33a9).
  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messagerie ou d’autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS dans Microsoft](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d’utiliser votre domaine avec Microsoft, vous devez vous assurer que vous en êtes propriétaire. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que vous êtes propriétaire du domaine.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Google Domains en utilisant [ce lien](https://domains.google.com/registrar). Vous êtes invité à vous connecter. Pour ce faire :
    
1. Sélectionnez **se connecter**.
    
2. Entrez vos informations d’identification de connexion, puis sélectionnez **de nouveau connexion**.
    
2. Sur la page **Mes domaines** , recherchez le domaine que vous souhaitez utiliser avec Microsoft, puis sélectionnez le lien **gérer** en regard de celui-ci. Dans le volet de navigation de gauche, sélectionnez **DNS**.
    
3. Dans la section * * Custom Resource Records * *, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (You may have to scroll down.)
    
    (Choose the **Type** value from the drop-down list.) 
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Name** <br/> |**Type** <br/> |**TTL (Durée de vie)** <br/> |**Data (Données)** <br/> |
    |@  <br/> |TXT  <br/> |Premier  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre **adresse de destination ou de pointage** spécifique ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
4. Sélectionnez **Ajouter**.
    
5. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
À présent que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous allez revenir à Microsoft et demander l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT correct, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> .

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messagerie ou d’autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient envoyés à Microsoft
<a name="BKMK_add_MX"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site Google Domains en utilisant [ce lien](https://domains.google.com/registrar). Vous êtes invité à vous connecter. Pour ce faire :
    
2. Sélectionnez **se connecter**.
    
3. Entrez vos informations d’identification de connexion, puis sélectionnez **de nouveau connexion**.
4. Dans la page **domaines** , dans la section **domaine** , sélectionnez **configurer DNS** pour le domaine que vous souhaitez modifier.
    
    > [!IMPORTANT]
    > Si vous avez un compte de courrier G Suite, vous devez commencer par supprimer les enregistrements MX qui lui sont associés. Les enregistrements MX de la suite G vous empêchent d’ajouter d’autres enregistrements MX, y compris ceux requis pour Microsoft. Notez que la suppression d'enregistrements G Suite ne supprime pas votre compte G Suite. Pour supprimer les enregistrements MX G Suite, procédez comme suit. 
  
5. Dans la section **rapports synthétiques** , dans la zone **G suite** , sélectionnez **supprimer**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez Supprimer dans la section enregistrements synthétiques.](../../media/bd276b5d-5667-4bb1-a233-2dc5194e7ace.png)
  
6. Sélectionnez **Supprimer**.
    
    ![Sélectionnez supprimer](../../media/4413a45a-5b82-4ec6-82c6-0091f5be9696.png)
  
7. In the **Custom resource records** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (You may have to scroll down.)
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Data (Données)**|
    |:-----|:-----|:-----|:-----|
    |@  <br/> |MX  <br/> |Premier  <br/> |0  *\<clé_de_domaine\>*  .mail.protection.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> La valeur **0** représente la valeur de priorité MX. Ajoutez-la au début de la valeur MX, séparée du reste de la valeur par un espace.  <br/> **Remarque :** Obtenir votre \< *clé* \> de domaine à partir de votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> |
   
    ![Taper ou coller des valeurs dans la section Custom Resource Records (enregistrements de ressources personnalisés)](../../media/b660ca9e-984d-449f-ae59-a65fe4e2c6bd.png)
  
5. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter](../../media/32f8f23c-0b80-48da-b08e-4e04052971af.png)
  
6. Si d'autres enregistrements MX personnalisés sont répertoriés, supprimez-les.
    
1. Sélectionnez **modifier** dans la ligne enregistrement MX. 
    
    ![Sélectionnez Modifier dans la ligne enregistrement MX.](../../media/acc53ae9-3b8a-421d-8d11-d4a4108b2353.png)
  
2. Pour chacun des autres enregistrements MX personnalisés, sélectionnez l’entrée dans la zone **données** , puis appuyez sur la touche **Suppr** de votre clavier pour supprimer cet enregistrement. 
    
    Continuez jusqu'à ce que vous ayez supprimé l'entrée **Data (Données)** de chacun des autres enregistrements MX. 
    
    ![Delete entries in the Data box](../../media/28192089-7b38-4d2e-9d52-9b83422c27d5.png)
  
7. Une fois que vous avez supprimé l’entrée de **données** pour chacun des autres enregistrements MX, sélectionnez **Enregistrer** pour enregistrer vos modifications. 
    
    ![Sélectionnez Enregistrer.](../../media/bf496d01-ccbe-4800-95f4-7b2283f2e5f6.png)
  
## <a name="add-the-five-cname-records-that-are-required-for-microsoft"></a>Ajouter les cinq enregistrements CNAMe requis pour Microsoft

1. Pour commencer, accédez à la page [Google Domains] (https://domains.google.com/registrar) et connectez-vous.
    
2. Dans la page **domaines** , dans la section **domaine** , sélectionnez **configurer DNS** pour le domaine que vous souhaitez modifier. 
    
3. Ajoutez le premier enregistrement CNAME.
    
    Dans la section **Custom resource records (Enregistrements de ressource personnalisés)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    (You may have to scroll down.)
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Data (Données)**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |Premier  <br/> |autodiscover.outlook.com.  <br/> **This value MUST end with a period (.)** <br/> |
    |sip  <br/> |CNAME  <br/> |Premier  <br/> |sipdir.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |
    |lyncdiscover  <br/> |CNAME  <br/> |Premier  <br/> |webdir.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |
    |enterpriseregistration  <br/> |CNAME  <br/> |Premier  <br/> |enterpriseregistration.windows.net.  <br/> **This value MUST end with a period (.)** <br/> |
    |enterpriseenrollment  <br/> |CNAME  <br/> |Premier  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **This value MUST end with a period (.)** <br/> |
   
    ![Taper ou coller des valeurs dans la section Custom Resource Records (enregistrements de ressources personnalisés)](../../media/cff9832a-6d57-421f-a183-55320974ed87.png)
  
4. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter](../../media/4a78080a-e0b2-4582-9696-3fe4fea41e91.png)
  
5. Ajoutez les quatre autres enregistrements CNAME.
    
    Dans la section **Custom Resource Records (enregistrements de ressources personnalisés** ), créez un enregistrement en utilisant les valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Add (Ajouter** ) pour valider cet enregistrement. 
    
    Répétez cette procédure jusqu’à ce que vous ayez créé tous les enregistrements CNAMe requis.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous disposez déjà d’un enregistrement SPF pour votre domaine, n’en créez pas pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un seul enregistrement SPF qui inclut les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [enregistrements DNS externes pour Microsoft](https://support.office.com/article/c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0#bkmk_spfrecords). Pour valider votre enregistrement SPF, vous pouvez utiliser l'un des outils de [validation SPF suivants](../setup/domains-faq.md). 
  
1. Pour commencer, accédez à la page de vos domaines sur le site Google Domains en utilisant [ce lien](https://domains.google.com/registrar). Vous êtes invité à vous connecter. Pour ce faire :
    
1. Sélectionnez **se connecter**.
    
2. Entrez vos informations d’identification de connexion, puis sélectionnez **de nouveau connexion**.
    
3. Dans la page **domaines** , dans la section **domaine** , sélectionnez **configurer DNS** pour le domaine que vous souhaitez modifier. 
    
4. Dans la section **Custom Resource Records (enregistrements de ressources personnalisés** ), sur la ligne de l’enregistrement txt, sélectionnez **modifier**. 
    
    > [!IMPORTANT]
    > Google Domains stocke les enregistrements TXT en tant qu'ensemble pouvant contenir plusieurs enregistrements. Lorsque vous avez au moins un autre enregistrement TXT, par exemple, l'enregistrement TXT que vous avez utilisé pour vérifier votre domaine, vous devez ajouter de nouveaux enregistrements TXT à ce jeu d'enregistrements. Toute tentative de saisie d'enregistrements TXT supplémentaires sous forme d'entrées distinctes entraîne un message d'erreur **Enregistrement en double**. 
  
    ![Sélectionnez Modifier dans la ligne enregistrement TXT.](../../media/eae14850-8d0c-4f29-8587-df8b36129d5f.png)
  
5. Sélectionnez le contrôle **(+)** . 
    
    ![Sélectionner le contrôle plus](../../media/628604cc-d2b2-42a5-bb5b-13c327b85d9f.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
    |**Data (Données)**|
    |:-----|
    |v=spf1 include:spf.protection.outlook.com -all  <br/> 

    > [!NOTE]
    > Nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           
   
   ![Taper ou coller des valeurs dans la section Custom Resource Records (enregistrements de ressources personnalisés)](../../media/4645cc4f-9fcc-4626-9674-072ed6fa34c2.png)
  
7. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer.](../../media/20c4c926-f062-4048-9265-bf752be54e0c.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajouter les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site Google Domains en utilisant [ce lien](https://domains.google.com/registrar). Vous êtes invité à vous connecter. Pour ce faire :
    
2. Sélectionnez **se connecter**.
    
3. Entrez vos informations d’identification de connexion, puis sélectionnez **de nouveau connexion**.
    
4. Dans la page **domaines** , dans la section **domaine** , sélectionnez **configurer DNS** pour le domaine que vous souhaitez modifier. 
    
5. Ajouter le premier enregistrement SRV.
    
    In the **Custom resource records** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (You may have to scroll down.)
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**Name**|**Type**|**TTL (Durée de vie)**|**Données**|
    |:-----|:-----|:-----|:-----|
    |_sip. _tls|SRV|Premier|100 1 443 sipdir.online.lync.com. **Cette valeur doit se terminer par un point (.)** **Remarque :** Nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
    |_sipfederationtls. _tcp|SRV|Premier|100 1 5061 sipfed.online.lync.com. **This value MUST end with a period (.)**

    Nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.       
   
    ![Taper ou coller des valeurs dans la section Custom Resource Records (enregistrements de ressources personnalisés)](../../media/429d06a9-c0af-4961-b7d2-7a8dea6db37e.png)
  
6. Sélectionnez **Ajouter**.
    
    ![Sélectionnez Ajouter](../../media/89df6efd-e641-4441-baa2-d9a890424569.png)
  
7. Ajoutez l'autre enregistrement SRV.
    
    Dans la section **Custom Resource Records (enregistrements de ressources personnalisés** ), créez un enregistrement en utilisant les valeurs de la deuxième ligne du tableau, puis sélectionnez de nouveau **Add (Ajouter** ) pour valider cet enregistrement. 
    
    > [!NOTE]
    > Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messagerie ou d’autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
