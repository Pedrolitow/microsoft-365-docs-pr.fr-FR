---
title: Créer des enregistrements DNS auprès de Network Solutions pour Office 365
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
ms.assetid: 1dc55f9f-5309-450f-acc3-b2b4119c8be3
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur les solutions réseau pour Office 365.
ms.openlocfilehash: 6bbe954f763e0cb06e9bf32b991e60da34393c57
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43211121"
---
# <a name="create-dns-records-at-network-solutions-for-office-365"></a>Créer des enregistrements DNS auprès de Network Solutions pour Office 365

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Network Solutions est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
Voici les principaux enregistrements à ajouter. Suivez les étapes ci-dessous ou [regardez la vidéo](https://support.office.com/article/Video-Create-DNS-records-at-Network-Solutions-for-Office-365-c49698c2-6991-47fb-b5ac-18e49a505099?ui=en-US&amp;rs=en-US&amp;ad=US) 
  
- [Ajouter un enregistrement TXT à des fins de vérification](#add-a-txt-record-for-verification)
    
- [Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365](#add-an-mx-record-so-email-for-your-domain-will-come-to-office-365)
    
- [Ajouter les enregistrements CNAME requis pour Office 365](#add-the-cname-records-that-are-required-for-office-365)
    
- [Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable](#add-a-txt-record-for-spf-to-help-prevent-email-spam)
    
- [Ajouter les 2 enregistrements SRV requis pour Office 365](#add-the-two-srv-records-that-are-required-for-office-365)
    
Une fois ces enregistrements ajoutés sur Network Solutions, votre domaine est configuré pour utiliser les services Office 365.
  
Pour en savoir plus sur l'hébergement web et le DNS pour les sites web avec Office 365, voir [Utiliser un site web public avec Office 365](https://support.office.com/article/choose-a-public-website-3325d50e-d131-403c-a278-7f3296fe33a9).
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 0:47)](https://support.office.com/article/Video-Create-DNS-records-at-Network-Solutions-for-Office-365-c49698c2-6991-47fb-b5ac-18e49a505099?ui=en-US&amp;rs=en-US&amp;ad=US).
  
1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
    
    > [!IMPORTANT]
    > Avant de cliquer sur le bouton de **connexion** , choisissez **gérer mes noms de domaine** dans la liste déroulante **se connecter à :** . 
  
    ![Sélectionnez Manage My Domain Names (Gérer mes noms de domaine) et connectez-vous à Network Solutions](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. Cochez la case située en regard du nom du domaine que vous modifiez.
    
    ![Activez la case à cocher correspondant à votre domaine](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. Sélectionnez **modifier DNS**.
    
    ![Sélectionnez Modifier DNS](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. Sélectionnez **gérer les enregistrements DNS avancés**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez gérer les enregistrements DNS avancés](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. Faites défiler jusqu’à la section **texte (enregistrements TXT)** , puis sélectionnez **modifier les enregistrements TXT**.
    
    ![Sélectionnez modifier les enregistrements TXT](../../media/240a01d6-750a-4da6-8554-641b571e4b71.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs figurant dans le tableau suivant.
    
    |**Host (Hôte)**|**TTL (Durée de vie)**|**Text (Texte)**|
    |:-----|:-----|:-----|
    |@  <br/> (The system will change this value to **@ (None)** when you save the record.)  <br/> |3600  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)   |
       
    ![Tapez ou collez des valeurs dans les zones du nouvel enregistrement.](../../media/8a76daab-b6ff-4c82-ba68-192b24fbb934.png)
  
7. Sélectionnez **Continuer**.
    
    ![Sélectionnez continuer](../../media/89e7fb38-b4d9-4949-a1bb-d0dd10b361e0.png)
  
8. Sélectionnez **enregistrer les modifications**.
    
    ![Sélectionnez Enregistrer les modifications.](../../media/bd4d7cd0-c8a3-497a-b080-cfd5a5c60dc5.png)
  
9. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Office 365 et demandez à Office 365 de rechercher l’enregistrement.
  
Lorsqu’Office 365 trouve l’enregistrement TXT approprié, votre domaine est vérifié.

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
    
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365
<a name="BKMK_add_MX"> </a>

Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 3:51)](https://support.office.com/article/Video-Create-DNS-records-at-Network-Solutions-for-Office-365-c49698c2-6991-47fb-b5ac-18e49a505099?ui=en-US&amp;rs=en-US&amp;ad=US).
  
1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
    
    > [!IMPORTANT]
    > Avant de cliquer sur le bouton de **connexion** , choisissez **gérer mes noms de domaine** dans la liste déroulante **se connecter à :** . 
  
    ![Sélectionnez Manage My Domain Names (Gérer mes noms de domaine) et connectez-vous à Network Solutions](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. Cochez la case située en regard du nom du domaine que vous modifiez.
    
    ![Activez la case à cocher correspondant à votre domaine](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. Sélectionnez **modifier DNS**.
    
    ![Sélectionnez Modifier DNS](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. Sélectionnez **gérer les enregistrements DNS avancés**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez gérer les enregistrements DNS avancés](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. Faites défiler vers le bas jusqu’à la section **serveurs de messagerie (enregistrements MX)** , puis sélectionnez **modifier les enregistrements MX**.
    
    ![Sélectionnez modifier les enregistrements MX](../../media/74b4e412-9073-4d2d-8710-fe340b223798.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    |**Priorité**|**TTL**|**Mail Server (Serveur de courrier)**|
    |:-----|:-----|:-----|
    |10   <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> |3600  <br/> | *\<clé_de_domaine\>*  .mail.protection.outlook.com.  <br/> **This value MUST end with a period (.)** <br/> **Remarque :** Obtenez votre * \<clé\> de domaine* à partir de votre compte Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
       
    ![Tapez ou collez des valeurs dans les zones du nouvel enregistrement.](../../media/0bb96872-cc6e-4dfa-a649-fb7efbbf0012.png)
  
7. Sélectionnez **Continuer**.
    
    ![Sélectionnez continuer](../../media/963f758b-e79d-4452-8340-7eba8a3972c9.png)
  
8. Sélectionnez **enregistrer les modifications**.
    
    ![Sélectionnez Enregistrer les modifications.](../../media/7c2f784a-6dee-4364-866c-ad7202ef1fc2.png)
  
9. Si d'autres enregistrements MX sont répertoriés, supprimez-les individuellement en sélectionnant l'icône **Delete (Supprimer)** associée à chaque enregistrement. 
    
    ![Select the Delete check box for other MX records](../../media/709d6133-9f5d-490a-a91e-95e21ca94695.png)
  
10. Lorsqu’elles sont toutes sélectionnées, sélectionnez **Continuer**.
    
    ![Sélectionnez continuer](../../media/4710f988-0bbc-4ba7-bf31-ca2392b2900e.png)
  
11. Sélectionnez **enregistrer les modifications**.
    
    ![Sélectionnez Enregistrer les modifications.](../../media/24432ec6-666b-4612-9488-37c06437959b.png)
  
## <a name="add-the-cname-records-that-are-required-for-office-365"></a>Ajouter les enregistrements CNAME requis pour Office 365
<a name="BKMK_add_CNAME"> </a>

Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 4:43)](https://support.office.com/article/Video-Create-DNS-records-at-Network-Solutions-for-Office-365-c49698c2-6991-47fb-b5ac-18e49a505099?ui=en-US&amp;rs=en-US&amp;ad=US).
  
1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
    
    > [!IMPORTANT]
    > Avant de cliquer sur le bouton de **connexion** , choisissez **gérer mes noms de domaine** dans la liste déroulante **se connecter à :** . 
  
    ![Sélectionnez Manage My Domain Names (Gérer mes noms de domaine) et connectez-vous à Network Solutions](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. Cochez la case située en regard du nom du domaine que vous modifiez.
    
    ![Activez la case à cocher correspondant à votre domaine](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. Sélectionnez **modifier DNS**.
    
    ![Sélectionnez Modifier DNS](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. Sélectionnez **gérer les enregistrements DNS avancés**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez gérer les enregistrements DNS avancés](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. Faites défiler jusqu’à la section **alias d’hôte (enregistrements CNAME)** , puis sélectionnez **modifier les enregistrements CNAME**.
    
    ![Sélectionnez modifier les enregistrements CNAMe sous alias d’hôte](../../media/2d0a4666-8d40-48f4-886c-64a5157baaf5.png)
  
6. Dans les zones des quatre nouveaux enregistrements, tapez ou copiez-collez les valeurs du tableau suivant.
    
    |**Alias (Alias)**|**TTL (Durée de vie)**|**Refers to Host Name (Fait référence au nom d'hôte)**|**Other Host (Autre hôte)          (sélectionnez la case d'option **Other Host (Autre hôte)**)**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |3600  <br/> |(Aucun paramètre)  <br/> |autodiscover.outlook.com.  <br/> **This value MUST end with a period (.)** <br/> |
    |sip  <br/> |3600  <br/> |(Aucun paramètre)  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |lyncdiscover  <br/> |3600  <br/> |(Aucun paramètre)  <br/> |webdir.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |
    |enterpriseregistration  <br/> |3600  <br/> |(Aucun paramètre)  <br/> |enterpriseregistration.windows.net  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |enterpriseenrollment  <br/> |3600  <br/> |(Aucun paramètre)  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> **This value MUST end with a period (.)** <br/> |
    
    ![Taper ou coller des valeurs pour les nouveaux enregistrements](../../media/5ce0b30c-b46c-4778-aa5a-fb5e2f0961c1.png)
  
7. Une fois que vous avez ajouté tous les enregistrements CNAMe dont vous avez besoin, sélectionnez **Continuer**.
    
    ![Sélectionnez continuer](../../media/4978bd8b-f6a6-458d-9522-ad612b301c4a.png)
  
8. Sélectionnez **enregistrer les modifications**.
    
    ![Sélectionnez Enregistrer les modifications.](../../media/f005c38a-0d8d-4c61-bec6-15e60c89aa5a.png)
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. If you already have an SPF record for your domain, don't create a new one for Office 365. Ajoutez plutôt les valeurs Office 365 requises à l'enregistrement actuel de manière à n'avoir qu'un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 5:35)](https://support.office.com/article/Video-Create-DNS-records-at-Network-Solutions-for-Office-365-c49698c2-6991-47fb-b5ac-18e49a505099?ui=en-US&amp;rs=en-US&amp;ad=US).
  
1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
    
    > [!IMPORTANT]
    > Avant de cliquer sur le bouton de **connexion** , choisissez **gérer mes noms de domaine** dans la liste déroulante **se connecter à :** . 
  
    ![Sélectionnez Manage My Domain Names (Gérer mes noms de domaine) et connectez-vous à Network Solutions](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. Cochez la case située en regard du nom du domaine que vous modifiez.
    
    ![Activez la case à cocher correspondant à votre domaine](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. Sélectionnez **modifier DNS**.
    
    ![Sélectionnez Modifier DNS](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. Sélectionnez **gérer les enregistrements DNS avancés**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez gérer les enregistrements DNS avancés](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. Faites défiler jusqu’à la section **texte (enregistrements TXT)** , puis sélectionnez **modifier les enregistrements TXT**.
    
    ![Sélectionnez modifier les enregistrements TXT sous texte](../../media/a69a2631-6da2-4e81-99ab-9a9ab9b30b07.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes.
    
    |**Host (Hôte)**|**TTL (Durée de vie)**|**Text (Texte)**|
    |:-----|:-----|:-----|
    |@  <br/> (The system will change this value to **@ (None)** when you save the record.)  <br/> |3600  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte. |
       
    ![Taper ou coller des valeurs pour le nouvel enregistrement](../../media/11564eca-e2ee-4f17-af2b-a00eb7c157db.png)
  
7. Sélectionnez **Continuer**.
    
    ![Sélectionnez continuer](../../media/482a8dae-0c79-47c4-8bd8-87965683de24.png)
  
8. Sélectionnez **enregistrer les modifications**.
    
    ![Sélectionnez Enregistrer les modifications.](../../media/600b8c6d-184f-4213-a50e-8f119ebf3ff0.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>Ajoutez les 2 enregistrements SRV requis pour Office 365
<a name="BKMK_add_SRV"> </a>

Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 6:18)](https://support.office.com/article/Video-Create-DNS-records-at-Network-Solutions-for-Office-365-c49698c2-6991-47fb-b5ac-18e49a505099?ui=en-US&amp;rs=en-US&amp;ad=US).
  
1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
    
    > [!IMPORTANT]
    > Avant de cliquer sur le bouton de **connexion** , choisissez **gérer mes noms de domaine** dans la liste déroulante **se connecter à :** . 
  
    ![Sélectionnez Manage My Domain Names (Gérer mes noms de domaine) et connectez-vous à Network Solutions](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. Cochez la case située en regard du nom du domaine que vous modifiez.
    
    ![Activez la case à cocher correspondant à votre domaine](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. Sélectionnez **modifier DNS**.
    
    ![Sélectionnez Modifier DNS](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. Sélectionnez **gérer les enregistrements DNS avancés**.
    
    (You may have to scroll down.)
    
    ![Sélectionnez gérer les enregistrements DNS avancés](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. Faites défiler jusqu’à la section **service (enregistrements SRV)** , puis sélectionnez **modifier les enregistrements SRV**.
    
    ![Sélectionnez modifier les enregistrements SRV sous service.](../../media/9a9248ea-5de5-4e16-9364-f7600fa371f5.png)
  
6. Dans les zones des deux nouveaux enregistrements, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (Sélectionnez les valeurs **Service (Service)** et **Protocol (Protocole)** dans les listes déroulantes.) 
    
    |**Service (Service)**|**Protocol (Protocole)**|**TTL (Durée de vie)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |3600  <br/> |100  <br/> |0,1  <br/> |443  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |3600  <br/> |100  <br/> |0,1  <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> **This value MUST end with a period (.)** <br/> |
       
    ![Taper ou coller des valeurs pour les nouveaux enregistrements](../../media/86968d1c-8e43-4e61-aeaa-37fc7d7ef7a7.png)
  
7. Sélectionnez **Continuer**.
    
    ![Sélectionnez continuer](../../media/bfe2c778-5d2b-4bb6-a79d-c3ff9caf9e1e.png)
  
8. Sélectionnez **enregistrer les modifications**.
    
    ![Sélectionnez Enregistrer les modifications.](../../media/6d323126-0ebe-45ab-8567-c234711d84c7.png)
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
