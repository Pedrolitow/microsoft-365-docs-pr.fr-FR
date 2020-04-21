---
title: Créer des enregistrements DNS sur NameCheap pour Microsoft
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
ms.assetid: 54ae2002-b38e-43a1-82fa-3e49d78fda56
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur NameCheap pour Microsoft.
ms.openlocfilehash: 2b55e529ab4a66dbada95914f213807884b4b6c0
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43629334"
---
# <a name="create-dns-records-at-namecheap-for-microsoft"></a>Créer des enregistrements DNS sur NameCheap pour Microsoft

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si NameCheap est votre fournisseur d’hébergement DNS, suivez la procédure décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online, etc.
  
Une fois ces enregistrements ajoutés sur NameCheap, votre domaine est configuré pour utiliser les services Microsoft.
  
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d’utiliser votre domaine avec Microsoft, vous devez vous assurer que vous en êtes propriétaire. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que vous êtes propriétaire du domaine.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
Suivez la procédure ci-dessous.
  
1. Pour commencer, accédez à la page de vos domaines sur NameCheap à l’aide de [ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à continuer.
    
    ![NameCheap-BP-configure-1-1](../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png)
  
2. Sur la page d' **Accueil** , sous **compte**, sélectionnez **liste de domaines** dans la liste déroulante. 
    
    ![NameCheap-BP-configure-1-2](../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png)
  
3. Dans la page **liste des domaines** , recherchez le nom du domaine que vous souhaitez modifier, puis sélectionnez **gérer**.
    
    ![NameCheap-BP-configure-1-3](../../media/fb2020d8-707c-4148-835e-304ac6244d66.png)
  
4. Sélectionnez **DNS avancé**.
    
    ![NameCheap-BP-configure-1-4](../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png)
  
5. Dans la section **Host Records (enregistrements d’hôte** ), sélectionnez **Add New Record (ajouter un nouvel enregistrement**).
    
    ![NameCheap-BP-configure-1-5](../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png)
  
6. Dans la liste déroulante **type** , sélectionnez **enregistrement txt**.
    
    > [!NOTE]
    > La liste déroulante **type** s’affiche automatiquement lorsque vous sélectionnez **Ajouter un nouvel enregistrement**. 
  
    ![NameCheap-BP-Verify-1-1](../../media/a5b40973-19b5-4c32-8e1b-1521aa971836.png)
  
7. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (Choisissez la valeur **TTL (durée de vie** ) dans la liste déroulante.) 
    
    |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |MS=ms *XXXXXXXX*  <br/>**Remarque :** il s'agit d'un exemple. Utilisez votre **adresse de destination ou de pointage** spécifique ici, à partir du tableau.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |30 min  <br/> |
       
    ![NameCheap-BP-Verify-1-2](../../media/fe75c0fd-f85c-4bef-8068-edaf9779b7f1.png)
  
8. Sélectionnez le contrôle **enregistrer les modifications** (coche). 
    
    ![NameCheap-BP-Verify-1-3](../../media/b48d2c67-66b5-4aa4-8e59-0c764f236fac.png)
  
9. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
À présent que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous allez revenir à Microsoft et demander l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT correct, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
    
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient envoyés à Microsoft
<a name="BKMK_add_MX"> </a>

Suivez la procédure ci-dessous.
  
1. Pour commencer, accédez à la page de vos domaines sur NameCheap à l’aide de [ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à continuer.
    
    ![NameCheap-BP-configure-1-1](../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png)
  
2. Sur la page d' **Accueil** , sous **compte**, sélectionnez **liste de domaines** dans la liste déroulante. 
    
    ![NameCheap-BP-configure-1-2](../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png)
  
3. Dans la page **liste des domaines** , recherchez le nom du domaine que vous souhaitez modifier, puis sélectionnez **gérer**.
    
    ![NameCheap-BP-configure-1-3](../../media/fb2020d8-707c-4148-835e-304ac6244d66.png)
  
4. Sélectionnez **DNS avancé**.
    
    ![NameCheap-BP-configure-1-4](../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png)
  
5. Dans la section **paramètres de messagerie** , sélectionnez **MX personnalisée** dans la liste déroulante **transfert du courrier** . 
    
    (You may have to scroll down.)
    
    ![NameCheap-BP-configure-2-1](../../media/40199e2c-42cf-4c3f-9936-3cbe5d4e81a4.png)
  
6. Sélectionnez **Ajouter un nouvel enregistrement**.
    
    ![NameCheap-BP-configure-2-2-1](../../media/8d169b81-ba48-4d51-84ea-a08fa1616457.png)
  
7. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (La zone **priorité** est la zone sans nom à droite de la zone **valeur** . Choisissez la valeur **TTL (durée de vie** ) dans la liste déroulante.) 
    
    |**Type**|**Host (Hôte)**|**Valeur**|**Priorité**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX Record (Enregistrement MX)  <br/> |@  <br/> |\<*Key*\>. mail.protection.Outlook.com.  <br/> **This value MUST end with a period (.)** <br/> **Remarque :** Obtenir votre * \<clé\> de domaine* à partir de votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> |30 min  <br/> |
       
    ![NameCheap-BP-configure-2-2-2](../../media/f3b76d62-5022-48c1-901b-8615a8571309.png)
  
8. Sélectionnez le contrôle **enregistrer les modifications** (coche). 
    
    ![NameCheap-BP-configure-2-3](../../media/ef4e3112-36d2-47c8-a478-136a565dd71d.png)
  
9. S'il existe d'autres enregistrements MX, utilisez le processus en deux étapes suivant pour supprimer chacun d'eux :
    
    Tout d’abord, sélectionnez l' **icône de suppression** (corbeille) pour l’enregistrement que vous souhaitez supprimer. 
    
    ![NameCheap-BP-configure-2-4](../../media/7a7a751f-29c2-495f-8f55-98ca37ce555a.png)
  
    Deuxièmement, sélectionnez **Oui** pour confirmer la suppression. 
    
    ![NameCheap-BP-configure-2-5](../../media/85ebc0c7-8787-43ee-9e7b-647375b3345c.png)
  
    Supprimez tous les enregistrements MX à l’exception de celui que vous avez ajouté précédemment dans cette procédure.

  
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a>Ajouter les six enregistrements CNAMe requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

Suivez la procédure ci-dessous.
  
1. Pour commencer, accédez à la page de vos domaines sur NameCheap à l’aide de [ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à continuer.
    
    ![NameCheap-BP-configure-1-1](../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png)
  
2. Sur la page d' **Accueil** , sous **compte**, sélectionnez **liste de domaines** dans la liste déroulante. 
    
    ![NameCheap-BP-configure-1-2](../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png)
  
3. Dans la page **liste des domaines** , recherchez le nom du domaine que vous souhaitez modifier, puis sélectionnez **gérer**.
    
    ![NameCheap-BP-configure-1-3](../../media/fb2020d8-707c-4148-835e-304ac6244d66.png)
  
4. Sélectionnez **DNS avancé**.
    
    ![NameCheap-BP-configure-1-4](../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png)
  
5. Dans la section **Host Records (enregistrements d’hôte** ), sélectionnez **Add New Record (ajouter un nouvel enregistrement**).
    
    ![NameCheap-BP-configure-1-5](../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png)
  
6. Dans la liste déroulante **type** , sélectionnez **enregistrement CNAME**.
    
    > [!NOTE]
    > La liste déroulante **type** s’affiche automatiquement lorsque vous sélectionnez **Ajouter un nouvel enregistrement**. 
  
    ![NameCheap-BP-configure-3-1](../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png)
  
7. Dans les zones vides du nouvel enregistrement, sélectionnez le **Type d'enregistrement** **CNAME**, puis tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover  <br/> |autodiscover.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |3600  <br/> |
       
    ![NameCheap-BP-configure-3-2](../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png)
  
8. Sélectionnez le contrôle **enregistrer les modifications** (coche). 
    
    ![NameCheap-BP-configure-3-3](../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png)
  
9. À l’aide des quatre étapes précédentes et des valeurs des cinq autres lignes du tableau, ajoutez chacun des cinq autres enregistrements CNAMe.

  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous disposez déjà d’un enregistrement SPF pour votre domaine, n’en créez pas pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs. 

Suivez la procédure ci-dessous.
  
1. Pour commencer, accédez à la page de vos domaines sur NameCheap à l’aide de [ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à continuer.
    
2. Sur la page d' **Accueil** , sous **compte**, sélectionnez **liste de domaines** dans la liste déroulante. 
    
    ![NameCheap-BP-configure-1-2](../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png)
  
3. Dans la page **liste des domaines** , recherchez le nom du domaine que vous souhaitez modifier, puis sélectionnez **gérer**.
    
    ![NameCheap-BP-configure-1-3](../../media/fb2020d8-707c-4148-835e-304ac6244d66.png)
  
4. Sélectionnez **DNS avancé**.
    
    ![NameCheap-BP-configure-1-4](../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png)
  
5. Dans la section **Host Records (enregistrements d’hôte** ), sélectionnez **Add New Record (ajouter un nouvel enregistrement**).
    
    ![NameCheap-BP-configure-1-5](../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png)
  
6. Dans la liste déroulante **type** , sélectionnez **enregistrement txt**.
    
    > [!NOTE]
    > La liste déroulante **type** s’affiche automatiquement lorsque vous sélectionnez **Ajouter un nouvel enregistrement**. 
  
    ![NameCheap-BP-configure-4-1](../../media/c5d1fddb-28b5-48ec-91c9-3e5d3955ac80.png)
  
7. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes du tableau suivant.
    
    (Choisissez la valeur **TTL (durée de vie** ) dans la liste déroulante.) 
    
    |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |30 min  <br/> |
       
    ![NameCheap-BP-configure-4-2](../../media/ea0829f1-990b-424b-b26e-9859468318dd.png)
  
8. Sélectionnez le contrôle **enregistrer les modifications** (coche). 
    
    ![NameCheap-BP-configure-4-3](../../media/f2846c36-ace3-43d8-be5d-a65e2c267619.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajouter les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

1. Pour commencer, accédez à la page de vos domaines sur NameCheap à l’aide de [ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). You'll be prompted to sign in.
    
    ![NameCheap-BP-configure-1-1](../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png)
  
2. Sur la page d' **Accueil** , sous **compte**, sélectionnez **liste de domaines** dans la liste déroulante. 
    
    ![NameCheap-BP-configure-1-2](../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png)
  
3. Dans la page **liste des domaines** , recherchez le nom du domaine que vous souhaitez modifier, puis sélectionnez **gérer**.
    
    ![NameCheap-BP-configure-1-3](../../media/fb2020d8-707c-4148-835e-304ac6244d66.png)
  
4. Sélectionnez **DNS avancé**.
    
    ![NameCheap-BP-configure-1-4](../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png)
  
5. Dans la section **Host Records (enregistrements d’hôte** ), sélectionnez **Add New Record (ajouter un nouvel enregistrement**).
    
    ![NameCheap-BP-configure-1-5](../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png)
  
6. Dans la liste déroulante **type** , sélectionnez **enregistrement SRV**.
    
    > [!NOTE]
    > La liste déroulante **type** s’affiche automatiquement lorsque vous sélectionnez **Ajouter un nouvel enregistrement**. 
  
    ![NameCheap-BP-configure-5-1](../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png)
  
7. Dans les zones vides pour les nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    |**Service**|**Protocol (Protocole)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |100  <br/> |0,1  <br/> |443  <br/> |sipdir.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |30 min  <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |100  <br/> |0,1  <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |30 min  <br/> |
       
    ![NameCheap-BP-configure-5-2](../../media/ff9566ea-0096-4b7f-873c-027080a23b56.png)
  
8. Sélectionnez le contrôle **enregistrer les modifications** (coche). 
    
    ![NameCheap-BP-configure-5-3](../../media/48a8dee4-c66d-449d-8759-9e9784c82b13.png)
  
9. À l’aide des quatre étapes précédentes et des valeurs de la deuxième ligne du tableau, ajoutez l’autre enregistrement SRV.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  

  
