---
title: Créer des enregistrements DNS à 1&IONOS 1 pour Microsoft
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online et d’autres services sur 1&1 IONOS pour Microsoft.
ms.openlocfilehash: 983fba73a6f82308d6d1bcf706ff93d72b98976c
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44400592"
---
# <a name="create-dns-records-at-11-ionos-for-microsoft"></a>Créer des enregistrements DNS à 1&IONOS 1 pour Microsoft

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
> [!CAUTION]
> Notez que 1&1 IONOS ne permet pas à un domaine d’avoir à la fois un enregistrement MX et un enregistrement CNAMe de découverte automatique de niveau supérieur. Cela limite les moyens de configurer Exchange Online pour Microsoft. Il existe une solution de contournement, mais nous vous recommandons de l’utiliser **uniquement** si vous avez déjà des expériences en matière de création de sous-domaines à 1&1 Ionos. > si en dépit de cette [limitation de service](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq) vous choisissez de gérer vos propres enregistrements DNS Microsoft à 1&1 Ionos, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online, etc. 
  
Une fois ces enregistrements ajoutés à 1&1 IONOS, votre domaine est configuré pour utiliser les services Microsoft.
  
  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 0:42)](https://docs.microsoft.com/microsoft-365/admin/dns/create-dns-records-at-1-1-internet).
  
1. Pour commencer, accédez à la page de vos domaines à l’adresse 1&1 IONOS à l’aide de [ce lien](https://my.1and1.com/). You'll be prompted to log in.
    
2. Sélectionnez **gérer les domaines**.
    
3. Sur la page **Centre de domaine** , recherchez le domaine que vous souhaitez mettre à jour, puis sélectionnez le contrôle de **volet** ( **v**) pour ce domaine.
    
4. Dans la zone **paramètres du domaine** , sélectionnez Modifier les **paramètres DNS**.
    
5. Dans la section **txt and SRV Records (enregistrements TXT** ), sélectionnez **Add record (ajouter un enregistrement**).
    
6. In the **Add Record** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    ||||
    |:-----|:-----|:-----|
    |**Type** <br/> |**Prefix (Préfixe)** <br/> |**Name Value (Valeur de nom)** <br/> |
    |TXT  <br/> |(Laissez ce champ vide)  <br/> |MS=ms *XXXXXXXX*  <br/> Remarque : Voici un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
7. Sélectionnez **Enregistrer**.
    
8. Sélectionnez de nouveau **Enregistrer** . 
    
9. Dans la boîte de dialogue **modifier les paramètres DNS** , sélectionnez **Oui**.
    
10. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Microsoft 365 et demandez à Microsoft 365 de rechercher l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
<a name="BKMK_add_MX"> </a>

Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 3:22)](https://docs.microsoft.com/microsoft-365/admin/dns/create-dns-records-at-1-1-internet).
  
> [!NOTE]
> Si vous avez enregistré auprès de 1und1.de, connectez-vous [ici](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Pour commencer, accédez à la page de vos domaines à l’adresse 1&1 IONOS à l’aide de [ce lien](https://my.1and1.com/). You'll be prompted to log in.
    
2. Sélectionnez **gérer les domaines**.
    
3. Sur la page **Centre de domaine** , recherchez le domaine que vous souhaitez mettre à jour, puis sélectionnez le contrôle de **volet** ( **v**) pour ce domaine.
    
4. Dans la zone **paramètres du domaine** , sélectionnez Modifier les **paramètres DNS**.
    
5. Dans la section **MX Records (enregistrements MX** ), dans la zone serveur de **messagerie (enregistrement MX)** , sélectionnez **autre serveur de messagerie**.<br/>(You may have to scroll down.)<br/>![1 &amp; -BP-configurer-2-1](../../media/b0db72ae-9431-460f-ba7a-3268590b892e.png) <br/>
  
6. Si d'autres enregistrements MX sont déjà répertoriés, supprimez-les en sélectionnant un enregistrement et en appuyant sur la touche **Suppr**.<br/>(Si aucun enregistrement MX n'est déjà répertorié, passez à l'étape suivante.)<br/>![1 &amp; -BP-configurer-2-2](../../media/4a39bac7-7310-481d-bda4-1dd5c220c60f.png)<br/>
  
7. Dans les zones de l'enregistrement **MX 1**, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    |**MX 1**|**Priority (Priorité)**|
    |:-----|:-----|
    | *\<domain-key\>*. mail.protection.outlook.com  <br/>  Remarque : Obtenez votre \<domain-key\> de votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |10   <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq). <br/> | 
    
    ![1 et 1-configurer 2 et 3](../../media/3afb04d1-7bbf-4147-89ae-561e14ded26d.png)<br/>
  
8. Sélectionnez **Enregistrer**.<br/>(You may have to scroll down.)<br/>![1 &amp; -BP-configurer-2-4](../../media/355b3ba7-4d2b-45ed-aa17-ac4affb54fe3.png)
  
9. Dans la boîte de dialogue **modifier les paramètres DNS** , sélectionnez **Oui**.<br/>![Sélection de Oui dans la boîte de dialogue Modifier les paramètres DNS](../../media/920cc95f-fedf-4da2-94a4-9cb41ed49bcf.png)
  
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a>Ajouter les six enregistrements CNAMe requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

1&1 IONOS nécessite une solution de contournement afin que vous puissiez utiliser un enregistrement MX avec les enregistrements CNAMe requis pour les services de messagerie Microsoft. Cette solution de contournement nécessite que vous créez un ensemble de sous-domaines à 1&1 IONOS, et que vous les affectiez à des enregistrements CNAMe.
  
> [!IMPORTANT]
> Vérifiez que vous avez au moins deux sous-domaines disponibles avant de commencer cette procédure. Nous vous recommandons cette solution uniquement si vous avez déjà des expériences en matière de création de sous-domaines à 1&1 IONOS. 
  
### <a name="basic-cname-records"></a>Enregistrements CNAME de base

Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 3:57)](https://docs.microsoft.com/microsoft-365/admin/dns/create-dns-records-at-1-1-internet).
  
> [!NOTE]
> Si vous avez enregistré auprès de 1und1.de, connectez-vous [ici](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Pour commencer, accédez à la page de vos domaines à l’adresse 1&1 IONOS à l’aide de [ce lien](https://my.1and1.com/). You'll be prompted to log in.
    
2. Sélectionnez **gérer les domaines**.
    
3. Sur la page **Centre de domaines** , recherchez le domaine que vous souhaitez mettre à jour, puis sélectionnez gérer les sous- **domaines**.<br/>![1 &amp; -BP-configurer-3-0](../../media/d570d03f-5c38-463d-809e-5bb9e4fb2777.png) <br/>Vous allez maintenant créer deux sous-domaines et définir une valeur **Alias (Alias)** pour chaque sous-domaine.<br/>(Cette opération est nécessaire, car 1&1 IONOS prend en charge un seul enregistrement CNAMe de niveau supérieur, mais Microsoft requiert plusieurs enregistrements CNAMe.)<br/>Tout d'abord, vous devez créer le sous-domaine de découverte automatique.
    
4. Dans la section **subdomain Overview (vue d’ensemble** des sous-domaines), sélectionnez **Create Subdomain**.
    
    ![1&amp;1-BP-Configure-3-1](../../media/95c63639-eb80-443d-8951-98e8b6cdcc4f.png)
  
5. Dans la zone **Create Subdomain (Créer un sous-domaine)** correspondant au nouveau sous-domaine, tapez ou copiez-collez uniquement la valeur **Create Subdomain (Créer un sous-domaine)** du tableau suivant. (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)

    |**Create Subdomain (Créer un sous-domaine)**|**Alias**|
    |:-----|:-----|
    |autodiscover  <br/> |autodiscover.outlook.com   | 

    ![1 &amp; -BP-configurer-3-2](../../media/9be45113-ebaf-48e6-983c-a7e6ff9eea45.png)
  
6. Sélectionnez **créer un sous-domaine**.<br/>![1 &amp; -BP-configurer-3-3](../../media/1e7bc874-f174-4597-8c08-df611d16a74d.png)
  
7. Dans la section **vue d’ensemble** des sous-domaines, recherchez le sous-domaine de **découverte automatique** que vous venez de créer, puis sélectionnez le contrôle de **volet (v)** correspondant à ce sous-domaine. <br/>![1 &amp; -BP-configurer-3-4](../../media/10e2e446-3e54-4fb2-8a29-8c442536cc31.png)
  
8. Dans la zone paramètres de sous- **domaine** , sélectionnez **modifier les paramètres DNS**. <br/>![1 &amp; -BP-configurer-3-5](../../media/5c602118-b89b-4897-9faf-0736be8a6a0d.png)
  
9. Dans la section **enregistrements a/aaaa (adresses IP)** , dans la zone **adresse IP (enregistrement A)** , sélectionnez **CNAME**.<br/>![1 &amp; -BP-configurer-3-6](../../media/7f57f468-fbee-4440-a53d-3e334d8e5b71.png)
  
10. Dans la zone **Alias: (Alias :)**, tapez ou copiez-collez uniquement la valeur **Alias (Alias)** du tableau suivant.<br/> 
    
    |**Create Subdomain (Créer un sous-domaine)**|**Alias**|
    |:-----|:-----|
    |autodiscover  <br/> |autodiscover.outlook.com   |

    ![1 &amp; -BP-configurer-3-7](../../media/afac3118-3337-4f99-98dd-a7ca930230ce.png)
  
11. Cochez la case correspondant à la clause d'exclusion de responsabilité **I am aware** (J'accepte).<br/>![1 &amp; -BP-configurer-3-8-1](../../media/6c4cac1a-23f2-4ff3-b2d1-3dca908638d2.png)
  
12. Sélectionnez **Enregistrer**.<br/>![1 &amp; -BP-configurer-3-8-2](../../media/ea1dfc06-c175-4146-ab40-da4d162097e1.png)
  
  
### <a name="additional-cname-records"></a>Enregistrements CNAME supplémentaires

Les enregistrements CNAME supplémentaires créés au cours de la procédure suivante activent les services Skype Entreprise Online. Vous allez suivre les mêmes étapes que vous avez suivies précédemment pour créer les deux enregistrements CNAME.
  
1. Créez le troisième sous-domaine (Lyncdiscover).<br/>Dans la section **subdomain Overview (vue d’ensemble** des sous-domaines), sélectionnez **Create Subdomain**.
    
2. Dans la zone **Create Subdomain (Créer un sous-domaine)** correspondant au nouveau sous-domaine, tapez ou copiez-collez uniquement la valeur **Create Subdomain (Créer un sous-domaine)** du tableau suivant. (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)<br/> 
    
    |**Create Subdomain (Créer un sous-domaine)**|**Alias**|
    |:-----|:-----|
    |lyncdiscover   |webdir.online.lync.com  |
   
3. Sélectionnez **créer un sous-domaine**.
    
4. Sur la page **Centre de domaines** , sélectionnez gérer les sous- **domaines**.
    
5. Dans la section **subdomain Overview (vue d’ensemble** des sous-domaines), recherchez le sous-domaine **lyncdiscover** que vous venez de créer, puis sélectionnez le contrôle de **volet (v)** correspondant à ce sous-domaine. <br/>Dans la zone paramètres de sous- **domaine** , sélectionnez **modifier les paramètres DNS**.
    
6. Dans la section **enregistrements a/aaaa (adresses IP)** , dans la zone **adresse IP (enregistrement A)** , sélectionnez **CNAME**.
    
7. Dans la zone **Alias: (Alias :)**, tapez ou copiez-collez uniquement la valeur **Alias (Alias)** du tableau suivant. <br/>
    
    |**Create Subdomain (Créer un sous-domaine)**|**Alias**|
    |:-----|:-----|
    |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |
   
8. Cochez la case correspondant à la clause d’exclusion de responsabilité **je suis conscientes** , puis sélectionnez **Enregistrer**.
    
9. Dans la boîte de dialogue **modifier les paramètres DNS** , sélectionnez **Oui**.
    
10. Créez le quatrième sous-domaine (SIP) : <br/>Dans la section **subdomain Overview (vue d’ensemble** des sous-domaines), sélectionnez **Create Subdomain**.
    
11. Dans la zone **Create Subdomain (Créer un sous-domaine)** correspondant au nouveau sous-domaine, tapez ou copiez-collez uniquement la valeur **Create Subdomain (Créer un sous-domaine)** du tableau suivant. (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)<br/>
    
    |**Create Subdomain (Créer un sous-domaine)**|**Alias**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |
   
12. Sélectionnez **créer un sous-domaine**.
    
13. Sur la page **Centre de domaines** , sélectionnez gérer les sous- **domaines**.
    
14. Dans la section **subdomain Overview (vue d’ensemble** des sous-domaines), recherchez le sous-domaine **SIP** que vous venez de créer, puis sélectionnez le contrôle de **volet (v)** correspondant à ce sous-domaine. <br/>Dans la zone paramètres de sous- **domaine** , sélectionnez **modifier les paramètres DNS**.
    
15. Dans la section **enregistrements a/aaaa (adresses IP)** , dans la zone **adresse IP (enregistrement A)** , sélectionnez **CNAME**.
    
16. Dans la zone **Alias: (Alias :)**, tapez ou copiez-collez uniquement la valeur **Alias (Alias)** du tableau suivant. 
    
    |**Create Subdomain (Créer un sous-domaine)**|**Alias**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |
   
17. Cochez la case correspondant à la clause d’exclusion de responsabilité **je suis conscientes** , puis sélectionnez **Enregistrer**.
    
18. Dans la boîte de dialogue **modifier les paramètres DNS** , sélectionnez **Oui**.
    
### <a name="cname-records-needed-for-mdm"></a>Enregistrements CNAME requis pour la gestion des appareils mobiles

> [!IMPORTANT]
> Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. 
  
|**Create Subdomain (Créer un sous-domaine)**|**Alias**|
|:-----|:-----|
|enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |
|enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
   
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](https://docs.microsoft.com/office365/enterprise/external-domain-name-system-records). Pour valider votre enregistrement SPF, vous pouvez utiliser l’un de ces[outils de validation SPF](../setup/domains-faq.md). 
  
Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 5:09)](https://docs.microsoft.com/microsoft-365/admin/dns/create-dns-records-at-1-1-internet).
  
> [!NOTE]
> Si vous avez enregistré auprès de 1und1.de, connectez-vous [ici](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Pour commencer, accédez à la page de vos domaines à l’adresse 1&1 IONOS à l’aide de [ce lien](https://my.1and1.com/). You'll be prompted to log in.
    
2. Sélectionnez **gérer les domaines**.
    
3. Sur la page **Centre de domaine** , recherchez le domaine que vous souhaitez mettre à jour, puis sélectionnez le contrôle de **volet** (**v**) pour ce domaine.
    
4. Dans la zone **paramètres du domaine** , sélectionnez Modifier les **paramètres DNS**.
    
5. Dans la section **txt and SRV Records (enregistrements TXT** ), sélectionnez **Add record (ajouter un enregistrement**). <br/>(You may have to scroll down.)
    
6. In the **Add Record** area, in the boxes for the new record, type or copy and paste the values from the following table. <br/>(Choose the **Type** value from the drop-down list.) <br/>
    
    |**Type**|**Prefix (Préfixe)**|**Name Value (Valeur de nom)**|
    |:-----|:-----|:-----|
    |TXT  <br/> |(Leave this field empty.)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           | 
    
    ![Enregistrement TXT](../../media/0b3ba3b4-64b9-4d68-9ee1-04eb3a17d4c5.png)
  
7. Sélectionnez **Enregistrer**.<br/>![Ajouter un enregistrement](../../media/0f222eb9-3bfd-4908-9a99-516cc6fb1d0e.png)
  
8. Sélectionnez **Enregistrer**.<br/>![Enregistrer un enregistrement](../../media/86ed1b59-31b2-4094-9cd4-32b94eb09e35.png)
  
9. Dans la boîte de dialogue **modifier les paramètres DNS** , sélectionnez **Oui**.<br/>![Sélection de Oui dans la boîte de dialogue Modifier les paramètres DNS](../../media/920cc95f-fedf-4da2-94a4-9cb41ed49bcf.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft

Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 5:51)](https://docs.microsoft.com/microsoft-365/admin/dns/create-dns-records-at-1-1-internet).
  
> [!NOTE]
> Si vous avez enregistré auprès de 1und1.de, connectez-vous [ici](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Pour commencer, accédez à la page de vos domaines à l’adresse 1&1 IONOS à l’aide de [ce lien](https://my.1and1.com/). You'll be prompted to log in.
    
2. Sélectionnez **gérer les domaines**.
    
3. Sur la page **Centre de domaine** , recherchez le domaine que vous souhaitez mettre à jour, puis sélectionnez le contrôle de **volet** ( **v**) pour ce domaine.
    
4. Dans la zone **paramètres du domaine** , sélectionnez Modifier les **paramètres DNS**.
    
5. Dans la section **txt and SRV Records (enregistrements TXT** ), sélectionnez **Add record (ajouter un enregistrement**).
    
6. Ajoutez le premier des deux enregistrements SRV :<br/>Dans la zone **Add Record (Ajouter un enregistrement)**, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. <br/>(Choisissez les valeurs **type** et **TTL** dans la liste déroulante.) 
    
    |**Type**|**Service**|**Protocol (Protocole)**|**Name (Nom)**|**Host (Hôte)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV  <br/> |sip  <br/> |tls  <br/> |(Leave this field empty.)  <br/> |sipdir.online.lync.com  <br/> |100  <br/> |1   <br/> |443  <br/> |3600 (1 h)  <br/> |
    |SRV  <br/> |sipfederationtls  <br/> |tcp  <br/> |(Laissez ce champ vide.)  <br/> |sipfed.online.lync.com  <br/> |100  <br/> |1   <br/> |5061  <br/> |3600 (1 h)  <br/> |  
    
    ![1 &amp; -BP-configurer-5-1](../../media/087e337d-926b-42ff-b11d-b449cfaed76c.png)
  
7. Sélectionnez **Enregistrer**. <br/>![1 &amp; -BP-configurer-5-2](../../media/aa5f803d-fb24-48e0-976a-6759c5fd252c.png)
  
8. Sélectionnez **Enregistrer**. <br/>![1 &amp; -BP-configurer-5-3](../../media/097e7e95-4899-4878-b6e7-c3abd8193c52.png)
  
9. Dans la boîte de dialogue **modifier les paramètres DNS** , sélectionnez **Oui**. <br/>![Sélection de Oui dans la boîte de dialogue Modifier les paramètres DNS](../../media/920cc95f-fedf-4da2-94a4-9cb41ed49bcf.png)
  
10. Ajoutez l'autre enregistrement SRV. <br/>Dans la section **txt and SRV Records (enregistrements TXT** ), sélectionnez **Add record (ajouter un enregistrement**). <br/>Dans la zone **Ajouter un enregistrement** , créez un enregistrement à l’aide des valeurs de l’autre ligne du tableau, puis sélectionnez à nouveau **Ajouter**, **Enregistrer**et **Oui** pour terminer l’enregistrement. 
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
