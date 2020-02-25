---
title: Créer des enregistrements DNS auprès de WiX pour Office 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Découvrez comment vérifier votre domaine et configurer des enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur WiX pour Office 365.
ms.openlocfilehash: 43d2f2417153dd0c848c33736733237b1681c02c
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42243048"
---
# <a name="create-dns-records-at-wix-for-office-365"></a>Créer des enregistrements DNS auprès de WiX pour Office 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si WiX est votre fournisseur d’hébergement DNS, suivez la procédure décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online, etc.
  
Voici les principaux enregistrements à ajouter. 
  
- [Ajoutez un enregistrement txt à des fins de vérification](#add-a-txt-record-for-verification).
    
- [Ajoutez un enregistrement MX de sorte que le courrier électronique pour votre domaine arrivera dans Office 365](#add-an-mx-record-so-email-for-your-domain-will-come-to-office-365).
    
- [Ajoutez les cinq enregistrements CNAME requis pour Office 365](#add-the-five-cname-records-that-are-required-for-office-365).
    
- [Ajoutez un enregistrement txt pour SPF afin d’éviter le courrier indésirable](#add-a-txt-record-for-spf-to-help-prevent-email-spam).
    
- [Ajoutez les deux enregistrements SRV requis pour Office 365](#add-the-two-srv-records-that-are-required-for-office-365).
    
Une fois que vous avez ajouté ces enregistrements à WiX, votre domaine est configuré pour utiliser les services Office 365.
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_txt"> </a>

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). You'll be prompted to log in first.
    
2. Sur la page **Mes domaines** , dans la zone **avancé** , sélectionnez le bouton **modifier le DNS** . 
    
3. Sélectionnez **+ Ajouter un autre** dans la ligne **txt (texte)** de l’éditeur DNS. 
    
4. In the boxes for the new record, type or copy and paste the values from the following table. 
    
||||
|:-----|:-----|:-----|
|**Host Name** <br/> |**TXT Value (Valeur TXT)** <br/> |**TTL** <br/> |
|Rempli automatiquement  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** Voici un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 Hour <br/> |          |
   
5. Sélectionnez le bouton **enregistrer le DNS** en haut de l’éditeur DNS. 
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
Now that you've added the record at your domain registrar's site, you'll go back to Office 365 and request Office 365 to look for the record.
  
When Office 365 finds the correct TXT record, your domain is verified.
  
1. Dans le centre d’administration, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> .
    
2. Dans la page **domaines** , sélectionnez le domaine que vous vérifiez. 
  
  
3. Sur la page **installation** , sélectionnez **Démarrer l’installation**.
   
  
4. Sur la page **vérifier le domaine** , sélectionnez **vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365
<a name="BKMK_mx"> </a>

1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). You'll be prompted to log in first.
    
2. Sur la page **Mes domaines** , dans la zone **boîtes aux lettres** , sélectionnez le lien **configurer votre enregistrement MX** . 
    
3. Sélectionnez **autre** dans la liste déroulante **votre fournisseur de messagerie** . 
    
4. Sélectionnez **+ Ajouter un autre**.
    
5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
|**Host Name**|**Points to (Pointe vers)**|**Priority (Priorité)**|**TTL**|
|:-----|:-----|:-----|:-----|
|Rempli automatiquement <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenez votre * \<clé\> de domaine* à partir de votre compte Office 365.   [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/What-is-MX-priority-2784cc4d-95be-443d-b5f7-bb5dd867ba83). | 1 Hour|
   
6. Si d’autres enregistrements MX sont répertoriés, supprimez-les chacun. 
    
7. Sélectionnez **OK**.
    
8. Dans la boîte de dialogue de confirmation, sélectionnez **OK**.
    
## <a name="add-the-five-cname-records-that-are-required-for-office-365"></a>Ajouter les cinq enregistrements CNAMe requis pour Office 365
<a name="BKMK_cname"> </a>

1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). You'll be prompted to login first.
    
2. Sur la page **Mes domaines** , dans la zone **avancé** , sélectionnez le bouton **modifier le DNS** . 
    
3. Sélectionnez **+ Ajouter un autre** dans la ligne **CNAME (alias)** de l’éditeur DNS pour chaque enregistrement CNAME. 
    
4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
|**Host Name**|**Points to (Pointe vers)**|**TTL (Durée de vie)**|
|:-----|:-----|:-----|
|autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 Hour  <br/> |
|sip  <br/> |sipdir.online.lync.com  <br/> |1 Hour <br/> |
|lyncdiscover  <br/> |webdir.online.lync.com   <br/> |1 Hour  <br/> |
|enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |1 heure <br/> |
|enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |1 Hour  <br/> |
   
5. Sélectionnez le bouton **enregistrer le DNS** en haut de l’éditeur DNS. 
    
6. Wait a few minutes before you continue, so that the record you just created can update across the Internet.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_spf"> </a>

> [!IMPORTANT]
> You cannot have more than one TXT record for SPF for a domain. If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues. If you already have an SPF record for your domain, don't create a new one for Office 365. Ajoutez plutôt les valeurs Office 365 requises à l'enregistrement actuel de manière à n'avoir qu'un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs.  
  
1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). You'll be prompted to log in first.
    
2. Sur la page **Mes domaines** , dans la zone **avancé** , sélectionnez le bouton **modifier le DNS** . 
    
3. Sélectionnez **+ Ajouter un autre** dans la ligne **txt (texte)** de l’éditeur DNS. 
    
4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
|**Host Name**|**TXT Value (Valeur TXT)**|**TTL**|
|:-----|:-----|:-----|
|[Laissez ce champ vide]  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** Nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.<br/> |TXT  <br/> | 1 Hour |
   
5. Sélectionnez le bouton **enregistrer le DNS** en haut de l’éditeur DNS. 
    
6. Wait a few minutes before you continue, so that the record you just created can update across the Internet.
    
## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>Ajouter les 2 enregistrements SRV requis pour Office 365
<a name="BKMK_srv"> </a>

1. Pour commencer, accédez à la page de vos domaines sur WiX en utilisant [ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). You'll be prompted to log in first.
    
2. Sur la page **Mes domaines** , dans la zone **avancé** , sélectionnez le bouton **modifier le DNS** . 
    
3. Sélectionnez **+ Ajouter un autre** dans la ligne **SRV** de l’éditeur DNS. 
    
4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
|**Service**|**Protocol (Protocole)**|**Name (Nom)**|**Weight (Poids)**|**Port**|**Target (Cible)**|**Priorité**|**TTL**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|sip  |tls  |Rempli automatiquement |0,1  |443   |sipdir.online.lync.com |100 |1 Hour |
|sipfed|tcp |Rempli automatiquement|0,1 |5061 |sipfed.online.lync.com|100 | 1 Hour |
   
5. Sélectionnez le bouton **enregistrer le DNS** en haut de l’éditeur DNS. 
    
6. Wait a few minutes before you continue, so that the record you just created can update across the Internet.
    
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  

