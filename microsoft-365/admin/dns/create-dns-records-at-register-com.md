---
title: Créer des enregistrements DNS Register.com microsoft
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
ms.assetid: 55bd8c38-3316-48ae-a368-4959b2c1684e
description: Découvrez comment vérifier votre domaine et configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online et d’autres services sur Register.com microsoft.
ms.openlocfilehash: dd2f3d516b5309fee85dd572470fe610ff277a68
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49657591"
---
# <a name="create-dns-records-at-registercom-for-microsoft"></a>Créer des enregistrements DNS Register.com microsoft

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Register.com est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
Voici les principaux enregistrements à ajouter. Suivez les étapes ci-dessous ou [regardez la vidéo](https://support.microsoft.com/office/7448dd9e-c0e7-4d5e-a7e9-f0e4715433c4)
  
- [Ajouter un enregistrement TXT auprès de Register.com pour vérifier que vous êtes propriétaire du domaine](#add-a-txt-record-at-registercom-to-verify-that-you-own-the-domain)
    
- [Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft](#add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft)
    
- [Ajouter les enregistrements CNAME requis pour Microsoft](#add-the-cname-records-that-are-required-for-microsoft)
    
- [Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable](#add-a-txt-record-for-spf-to-help-prevent-email-spam)

- [Ajoutez les deux enregistrements SRV requis pour Microsoft](#add-the-two-srv-records-that-are-required-for-microsoft)
    
Une fois ces enregistrements ajoutés Register.com, votre domaine est installé pour fonctionner avec les services Microsoft.
  

  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-at-registercom-to-verify-that-you-own-the-domain"></a>Ajouter un enregistrement TXT auprès de Register.com pour vérifier que vous êtes propriétaire du domaine
<a name="BKMK_verify"> </a>

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 0:44)](https://support.microsoft.com/office/7448dd9e-c0e7-4d5e-a7e9-f0e4715433c4).
  
1. Pour commencer, accédez à la page de vos domaines sur le site Register.com en utilisant [ce lien](https://www.register.com/myaccount/). Vous serez invité à vous connecter.
    
2. Sélectionnez **Domaines**.
    
3. Sélectionnez **Gérer**.
    
4. Recherchez la ligne qui contient le nom du domaine à modifier . puis, dans cette ligne, sélectionnez **Gérer.**
    
5. Faites défiler vers le bas **jusqu’à** la section Paramètres techniques avancés, puis sélectionnez Modifier les enregistrements **TXT (SPF).**
    
6. In the boxes for the new record, type or copy and paste the values from the following table.
    
    |||
    |:-----|:-----|
    |**Host Name** <br/> |**TXT Record** <br/> |
    |@  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
7. Sélectionnez **Continuer**.
    
8. Sur la page suivante, **sélectionnez Continuer** à nouveau pour confirmer vos modifications. 
    
9. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
<a name="BKMK_add_MX"> </a>

Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 3:32)](https://support.microsoft.com/office/7448dd9e-c0e7-4d5e-a7e9-f0e4715433c4).
  
1. Pour commencer, accédez à la page de vos domaines sur le site Register.com en utilisant [ce lien](https://www.register.com/myaccount/). Vous serez invité à vous connecter.
    
2. Sélectionnez **Domaines**.
    
3. Sélectionnez **Gérer**.
    
4. Recherchez la ligne qui contient le nom du domaine à modifier . puis, dans cette ligne, sélectionnez **Gérer.**
    
5. Faites défiler **jusqu’à la** section Paramètres techniques avancés, puis sélectionnez **Modifier les enregistrements de l’échangeur de messages.**
    
    ![Select Edit Mail Exchanger Records](../../media/366b96a1-9147-4bbb-9f8f-50856466cc61.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (Choisissez la **valeur Priorité** dans la liste.) 
    
    |****Host Name (Nom d'hôte)****|****Priority (Priorité)****|****Mail Server (Serveur de courrier)****|
    |:-----|:-----|:-----|
    |@  <br/> |High  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq). <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/>  <br/>**Remarque :** Obtenez votre \<*domain-key*\> à partir de votre compte Microsoft. <br> [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Copier et coller la valeur du tableau](../../media/a1a15a14-c3dc-45dc-adcd-90fdb3f7455d.png)
  
7. Si d'autres enregistrements MX sont répertoriés dans la liste, sélectionnez-les individuellement pour les supprimer.
    
    ![Select each record to delete](../../media/0708d03e-346f-4ae7-8cc4-01589efc00ce.png)
  
8. Sélectionnez **Continuer**.
    
    ![Sélectionner Continuer](../../media/6ef6ce01-ce21-4e3c-8209-4aa9a3dd4b76.png)
  
9. Sur la page suivante, **sélectionnez Continuer** à nouveau pour confirmer et enregistrer vos modifications. 
    
    ![Sélectionner Continuer](../../media/adba4a60-bf61-44fc-9ad9-360e66f8a2ee.png)
  
## <a name="add-the-cname-records-that-are-required-for-microsoft"></a>Ajouter les enregistrements CNAME requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 4:23)](https://support.microsoft.com/office/7448dd9e-c0e7-4d5e-a7e9-f0e4715433c4).
  
1. Pour commencer, accédez à la page de vos domaines sur le site Register.com en utilisant [ce lien](https://www.register.com/myaccount/). Vous serez invité à vous connecter.
    
2. Sélectionnez **Domaines**.
    
3. Sélectionnez **Gérer**.
    
4. Recherchez la ligne qui contient le nom du domaine à modifier . puis, dans cette ligne, sélectionnez **Gérer.**
    
5. Faites défiler la page **jusqu’à** la section Paramètres techniques avancés, puis sélectionnez Modifier les enregistrements **d’alias de domaine.**
    
    ![Sélectionner Modifier les enregistrements d’alias de domaine](../../media/9fbc31ed-d67c-4828-8bd4-b51068f1e0ca.png)
  
6. Sélectionnez **Ajouter d’autres alias de domaine.**
    
    ![Select Add more domains aliases](../../media/b787505f-5566-4879-8552-13f9e89cbf6b.png)
  
7. Ajoutez les enregistrements CNAME nécessaires.
    
    Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    |****First field (unlabeled) (Premier champ (sans étiquette))****|****Points to (Destination)****|
    |:-----|:-----|
    |autodiscover  <br/> |autodiscover.outlook.com  <br/>  <br/> |
    |sip  <br/> |sipdir.online.lync.com  <br/>  <br/> |
    |lyncdiscover  <br/> |webdir.online.lync.com <br/>  <br/> |
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/>  <br/> |
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/>  <br/> |
   
     ![Copier et coller les valeurs DNS du tableau](../../media/0e2b36b2-8a0b-4019-addf-301763f9a626.png)
  
8. Lorsque vous avez ajouté tous les enregistrements CNAME dont vous avez besoin, sélectionnez **Continuer.**
    
    ![Sélectionner Continuer](../../media/1942612b-338a-48fa-a45d-2d5434516723.png)
  
9. Sur la page suivante, **sélectionnez Continuer** à nouveau pour confirmer et enregistrer vos modifications. 
    
    ![Sélectionner Continuer](../../media/3342b570-0633-49c5-9175-5cc8e4a67b53.png)
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir qu’un seul enregistrement SPF qui inclut les deux ensembles de valeurs.  
  
Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 5:12)](https://support.microsoft.com/office/7448dd9e-c0e7-4d5e-a7e9-f0e4715433c4).
  
1. Pour commencer, accédez à la page de vos domaines sur le site Register.com en utilisant [ce lien](https://www.register.com/myaccount/). Vous serez invité à vous connecter.
    
2. Sélectionnez **Domaines**.
    
3. Sélectionnez **Gérer**.
    
4. Recherchez la ligne qui contient le nom du domaine à modifier . puis, dans cette ligne, sélectionnez **Gérer.**
    
5. Faites défiler **jusqu’à la** section Paramètres techniques avancés, puis sélectionnez Modifier les enregistrements **TXT (SPF).**
    
    ![Sélectionner Modifier les enregistrements TXT (SPF)](../../media/c917577a-8b3a-4210-ab6e-776e84f926d0.png)
  
6. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    |****Host Name (Nom d'hôte)****|****TXT Record (Enregistrement TXT)****|
    |:-----|:-----|
    |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.  |
   
     ![Copier et coller les valeurs du tableau](../../media/b1dc5036-c13c-4306-b1e3-5a38a74643b7.png)
  
7. Sélectionnez **Continuer**.
    
    ![Sélectionner Continuer](../../media/08250c98-1a86-48a8-ad94-f96cf338126b.png)
  
8. Sur la page suivante, **sélectionnez Continuer** à nouveau pour confirmer et enregistrer vos modifications. 
    
    ![Sélectionner Continuer](../../media/56be3b0a-dc71-471c-9be3-6ab927296f67.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 5:55)](https://support.microsoft.com/office/7448dd9e-c0e7-4d5e-a7e9-f0e4715433c4).
  
1. Pour commencer, accédez à la page de vos domaines sur le site Register.com en utilisant [ce lien](https://www.register.com/myaccount/). Vous serez invité à vous connecter.
    
2. Sélectionnez **Domaines**.
    
3. Sélectionnez **Gérer**.
    
4. Recherchez la ligne qui contient le nom du domaine à modifier . puis, dans cette ligne, sélectionnez **Gérer.**
    
5. Faites défiler **jusqu’à la** section Paramètres techniques avancés, puis sélectionnez **Modifier les enregistrements SRV.**
    
    ![Sélectionner Modifier les enregistrements SRV](../../media/73c149ae-f0d6-460e-880a-7e04a995acc3.png)
  
6. Ajoutez le premier des deux enregistrements SRV :
    
    Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    (Choisissez la **valeur Priorité** dans la liste.) 
    
    |****Service (Service)****|****Proto (Protocole)****|****Name (Nom)****|****Priority (Priorité)****|****Weight (Poids)****|****Port (Port)****|****Target (Cible)****|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |@  <br/> |High  <br/> |1   <br/> |443  <br/> |sipdir.online.lync.com  <br/>  <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |@  <br/> |High  <br/> |1   <br/> |5061  <br/> |sipfed.online.lync.com  <br/>  <br/> |
   
    ![Copier et coller les valeurs du tableau](../../media/71304c81-5845-4a8f-b969-d9efc8721184.png)
  
7. Sélectionnez **Ajouter d’autres enregistrements SRV.**
    
    ![Sélectionnez Ajouter d’autres enregistrements SRV](../../media/823c6bd2-4af7-4079-bf8c-8d35a5c6730f.png)
  
8. Ajoutez le deuxième enregistrement SRV.
    
    Tapez ou copiez-collez les valeurs de la deuxième ligne du tableau ci-dessus dans les zones du deuxième enregistrement.
    
9. Lorsque vous avez ajouté les deux enregistrements SRV, sélectionnez **Continuer**.
    
    ![Sélectionner Continuer](../../media/008b255a-42d3-442d-83ea-3ffcb7c8fc5d.png)
  
10. Sur la page suivante, **sélectionnez Continuer** à nouveau pour confirmer et enregistrer vos modifications. 
    
    ![Sélectionner Continuer](../../media/b4166e3d-7e4b-41ef-b616-747e95aefc37.png)
  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
