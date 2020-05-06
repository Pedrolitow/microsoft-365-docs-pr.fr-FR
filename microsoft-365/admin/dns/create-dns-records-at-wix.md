---
title: Créer des enregistrements DNS auprès de WiX pour Microsoft
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services chez WiX pour Microsoft.
ms.openlocfilehash: 6f88cc65ae19f747a9fc3740ea1578f30d18b5e2
ms.sourcegitcommit: 5476c2578400894640ae74bfe8e93c3319f685bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44048854"
---
# <a name="create-dns-records-at-wix-for-microsoft"></a>Créer des enregistrements DNS auprès de WiX pour Microsoft

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si WiX est votre fournisseur d’hébergement DNS, suivez la procédure décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online, etc.
  
Voici les principaux enregistrements à ajouter. 
  
- [Ajoutez un enregistrement txt à des fins de vérification](#add-a-txt-record-for-verification).
    
- [Ajoutez un enregistrement MX afin que les messages électroniques pour votre domaine soient envoyés à Microsoft](#add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft).
    
- [Ajoutez les cinq enregistrements CNAME requis pour Microsoft](#add-the-five-cname-records-that-are-required-for-microsoft).
    
- [Ajoutez un enregistrement txt pour SPF afin d’éviter le courrier indésirable](#add-a-txt-record-for-spf-to-help-prevent-email-spam).
    
- [Ajoutez les deux enregistrements SRV requis pour Microsoft](#add-the-two-srv-records-that-are-required-for-microsoft).
    
Une fois que vous avez ajouté ces enregistrements à WiX, votre domaine est configuré pour utiliser les services Microsoft.
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_txt"> </a>

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
2. Sur la page **Mes domaines** , dans la zone **avancé** , sélectionnez le bouton **modifier le DNS** . 
    
3. Sélectionnez **+ Ajouter un autre** dans la ligne **txt (texte)** de l’éditeur DNS. 
    
4. In the boxes for the new record, type or copy and paste the values from the following table. 
    
||||
|:-----|:-----|:-----|
|**Host Name** <br/> |**VALEUR TXT** <br/> |**TTL** <br/> |
|Rempli automatiquement  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 Hour <br/> |          |
   
5. Sélectionnez le bouton **enregistrer le DNS** en haut de l’éditeur DNS. 
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
  
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
   
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
<a name="BKMK_mx"> </a>

1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
2. Sur la page **Mes domaines** , dans la zone **boîtes aux lettres** , sélectionnez le lien **configurer votre enregistrement MX** . 
    
3. Sélectionnez **autre** dans la liste déroulante **votre fournisseur de messagerie** . 
    
4. Sélectionnez **+ Ajouter un autre**.
    
5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
|**Host Name**|**Points to (Pointe vers)**|**Priorité**|**TTL**|
|:-----|:-----|:-----|:-----|
|Rempli automatiquement <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenir votre * \<clé\> de domaine* à partir de votre compte Microsoft.   [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq). | 1 Hour|
   
6. Si d’autres enregistrements MX sont répertoriés, supprimez-les chacun. 
    
7. Sélectionnez **OK**.
    
8. Dans la boîte de dialogue de confirmation, sélectionnez **OK**.
    
## <a name="add-the-five-cname-records-that-are-required-for-microsoft"></a>Ajouter les cinq enregistrements CNAMe requis pour Microsoft
<a name="BKMK_cname"> </a>

1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). You'll be prompted to login first.
    
2. Sur la page **Mes domaines** , dans la zone **avancé** , sélectionnez le bouton **modifier le DNS** . 
    
3. Sélectionnez **+ Ajouter un autre** dans la ligne **CNAME (alias)** de l’éditeur DNS pour chaque enregistrement CNAME. 
    
4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
|**Host Name**|**Points to (Destination)**|**TTL (Durée de vie)**|
|:-----|:-----|:-----|
|autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 Hour  <br/> |
|sip  <br/> |sipdir.online.lync.com  <br/> |1 Hour <br/> |
|lyncdiscover  <br/> |webdir.online.lync.com   <br/> |1 Hour  <br/> |
|enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |1 heure <br/> |
|enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |1 Hour  <br/> |
   
5. Sélectionnez le bouton **enregistrer le DNS** en haut de l’éditeur DNS. 
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_spf"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs.  
  
1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
2. Sur la page **Mes domaines** , dans la zone **avancé** , sélectionnez le bouton **modifier le DNS** . 
    
3. Sélectionnez **+ Ajouter un autre** dans la ligne **txt (texte)** de l’éditeur DNS. 
    
4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
|**Host Name**|**VALEUR TXT**|**TTL**|
|:-----|:-----|:-----|
|[Laissez ce champ vide]  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.<br/> |TXT  <br/> | 1 Hour |
   
5. Sélectionnez le bouton **enregistrer le DNS** en haut de l’éditeur DNS. 
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_srv"> </a>

1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
2. Sur la page **Mes domaines** , dans la zone **avancé** , sélectionnez le bouton **modifier le DNS** . 
    
3. Sélectionnez **+ Ajouter un autre** dans la ligne **SRV** de l’éditeur DNS. 
    
4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
|**Service**|**Protocol (Protocole)**|**Name (Nom)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|**Priorité**|**TTL**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|sip  |tls  |Rempli automatiquement |0,1  |443   |sipdir.online.lync.com |100 |1 Hour |
|sipfed|tcp |Rempli automatiquement|0,1 |5061 |sipfed.online.lync.com|100 | 1 Hour |
   
5. Sélectionnez le bouton **enregistrer le DNS** en haut de l’éditeur DNS. 
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  

