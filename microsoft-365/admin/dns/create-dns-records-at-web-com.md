---
title: Créer des enregistrements DNS sur web.com pour Office 365
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
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur web.com pour Office 365.
ms.openlocfilehash: eb231f85e568e81a5e229f0533d8176feb590f48
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42249454"
---
# <a name="create-dns-records-at-webcom-for-office-365"></a>Créer des enregistrements DNS sur web.com pour Office 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Si web.com est votre fournisseur d’hébergement DNS, suivez la procédure décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype entreprise Online, etc.
  
Une fois ces enregistrements ajoutés sur web.com, votre domaine est configuré pour utiliser les services Office 365.
  
Pour en savoir plus sur l'hébergement web et le DNS pour les sites web avec Office 365, voir [Utiliser un site web public avec Office 365](https://support.office.com/article/a8178510-501d-4bd8-9921-b04f2e9517a5.aspx).
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine
<a name="BKMK_Nameservers"> </a>

> [!IMPORTANT]
> Vous devez effectuer cette procédure au niveau du bureau d'enregistrement de domaines auprès duquel vous avez acheté et inscrit votre domaine. 
  
Lorsque vous vous êtes inscrit à web.com, vous avez ajouté un domaine à l’aide du processus de **configuration** de Web.com. 
  
Pour vérifier et créer des enregistrements DNS pour votre domaine dans Office 365, vous devez d’abord modifier les serveurs de noms dans votre bureau d’enregistrement de domaines afin qu’ils utilisent les serveurs de noms de Web. com.
  
Pour modifier vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit.
  
1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.
    
2. Créez deux enregistrements de serveur de noms à l’aide des valeurs indiquées dans le tableau suivant, ou modifiez les enregistrements de serveur de noms existants afin qu’ils correspondent à ces valeurs.
    
    |||
    |:-----|:-----|
    |Premier serveur de noms  <br/> |Utilisez la valeur de serveur de noms fournie par web.com.  <br/> |
    |Deuxième serveur de noms  <br/> |Utilisez la valeur de serveur de noms fournie par web.com.  <br/> |
   
    > [!TIP]
    > You should use at least two name server records. Si d’autres serveurs de noms sont répertoriés, vous devez les supprimer. 
  
3. Enregistrez vos modifications.
    
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine. 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur web.com à l’aide de [ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.
  
2. Sur la page **Gestionnaire de comptes** , sélectionnez **mes noms de domaine**. 
  
3. Sous * * Manage * my Domain * * *, sélectionnez **modifier les enregistrements DNS avancés**.

  
4. Dans la page **noms de domaine** , sous **texte (enregistrements TXT)**, cliquez sur **modifier les enregistrements TXT**, puis sélectionnez les valeurs du tableau suivant. 
    
    |**Host (Hôte)**|**TTL**|**Text (Texte)**|
    |:-----|:-----|:----|
    |@  <br/> |3600  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** Voici un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)    |
  
    
5. Sélectionnez **Continuer**.
  
  
6. Patientez quelques minutes avant de vérifier votre nouvel enregistrement TXT, afin que l’enregistrement que vous venez de créer puisse être mis à jour sur Internet.
    
Now that you've added the record at your domain registrar's site, you'll go back to Office 365 and request Office 365 to look for the record.
  
When Office 365 finds the correct TXT record, your domain is verified.
  
1. Dans le centre d’administration, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> .

    
2. Dans la page **domaines** , sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Sur la page **installation** , sélectionnez **Démarrer l’installation**.
    
    
  
4. Sur la page **vérifier le domaine** , sélectionnez **vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365
<a name="BKMK_add_MX"> </a>

1. Pour commencer, accédez à la page de vos domaines sur web.com à l’aide de [ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.
  
2. Sur la page **Gestionnaire de comptes** , sélectionnez **mes noms de domaine**. 
  
3. Sous * * Manage * my Domain * * *, sélectionnez **modifier les enregistrements DNS avancés**.

4. Sous **serveurs de messagerie (enregistrements MX)**, cliquez sur **modifier les enregistrements MX**, puis sélectionnez les valeurs du tableau suivant. 
    
    |**Priorité**|**TTL**|**Mail Server (Serveur de courrier)**|
    |:-----|:-----|:-----|
    |0,1  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> |3600  <br/> |*\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenez votre * \<clé\> de domaine* à partir de votre compte Office 365.   [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) |
   

5. Cliquez sur **Enregistrer**.
  
6. Si d’autres enregistrements MX sont répertoriés dans la section **MX Records (enregistrements MX** ), activez la case à cocher en regard de l’enregistrement sous **Delete (supprimer**), puis sélectionnez Save ( **Enregistrer**). 
  
7. Dans l’écran de confirmation, sélectionnez **enregistrer les modifications**. 

  
## <a name="add-the-six-cname-records-that-are-required-for-office-365"></a>Ajouter les six enregistrements CNAMe requis pour Office 365
<a name="BKMK_add_CNAME"> </a>

1. Pour commencer, accédez à la page de vos domaines sur web.com à l’aide de [ce lien](https://checkout.web.com/manage-it/index.jsp). You'll be prompted to log in first.
     
2. Sur la page **Gestionnaire de comptes** , sélectionnez **mes noms de domaine**. 
  
3. Sous * * Manage * my Domain * * *, sélectionnez **modifier les enregistrements DNS avancés**.

4. Ajoutez le premier des six enregistrements CNAME.
    
    Sous **alias d’hôte (enregistrements CNAME)**, cliquez sur **modifier les enregistrements CNAME**, puis sélectionnez les valeurs du tableau suivant.
    
    
    |**Alias (Alias)**|**TTL (Durée de vie)**|**Refers to Host Name (Fait référence au nom d'hôte)**|**Autre hôte**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |3600  <br/> |@ (aucun)  <br/> |autodiscover.outlook.com  <br/> |
    |sip  <br/> |3600  <br/> |@ (aucun)  <br/> |sipdir.online.lync.com  <br/> |
    |lyncdiscover  <br/> |3600  <br/> |@ (aucun)  <br/> | webdir.online.lync.com  <br/> |
    |enterpriseregistration  <br/> |3600  <br/> |@ (aucun)  <br/> |enterpriseregistration.windows.net  <br/> |
    |enterpriseenrollment  <br/> |3600  <br/> |@ (aucun)  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
    |msoid  <br/> |3600  <br/> |@ (aucun)  <br/> |clientconfig.microsoftonline-p.net  <br/> |
    
  
5. Sélectionnez **Continuer**.
  
6. Ajoutez successivement les 5 autres enregistrements CNAME.

    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> You cannot have more than one TXT record for SPF for a domain. If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues. If you already have an SPF record for your domain, don't create a new one for Office 365. Ajoutez plutôt les valeurs Office 365 requises à l'enregistrement actuel de manière à n'avoir qu'un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
1. Pour commencer, accédez à la page de vos domaines sur web.com à l’aide de [ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.
    
  
2. Sur la page **Gestionnaire de comptes** , sélectionnez **mes noms de domaine**. 
  
3. Sous * * Manage * my Domain * * *, sélectionnez **modifier les enregistrements DNS avancés**.

  
4. Dans la page **noms de domaine** , sous **texte (enregistrements TXT)**, cliquez sur **modifier les enregistrements TXT**, puis sélectionnez les valeurs du tableau suivant.   
    
    |**Host (Hôte)**|**TTL**|**Text (Texte)**|
    |:-----|:-----|:-----|
    |@  <br/> |3600  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** Nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.   |

 
5. Sélectionnez **Continuer**.

6. Sélectionnez **enregistrer les modifications**.
    

  
## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>Ajouter les 2 enregistrements SRV requis pour Office 365
<a name="BKMK_add_SRV"> </a>

> [!IMPORTANT]
> N’oubliez pas que web.com est responsable de la mise à disposition de cette fonctionnalité. Si vous constatez des incohérences entre les étapes ci-dessous et l’interface utilisateur graphique (GUI) web.com actuelle, utilisez la [communauté Web.com](https://community.web.com.com/). 

1. Pour commencer, accédez à la page de vos domaines sur web.com à l’aide de [ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.
      
2. Sur la page **Gestionnaire de comptes** , sélectionnez **mes noms de domaine**. 
  
3. Sous * * Manage * my Domain * * *, sélectionnez **modifier les enregistrements DNS avancés**.
  
4. Ajoutez le premier des deux enregistrements SRV.

    Sous **service (enregistrements SRV)**, cliquez sur **modifier les enregistrements SRV**, puis sélectionnez les valeurs du tableau suivant. 
        
    |**Service**|**Protocol (Protocole)**|**TTL (Durée de vie)**|**Priority (Priorité)**|**Weight (Poids)**|**Port**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip |_tls |3600 | 100|0,1 |443 |sipfed.online.lync.com  |
    |_sipfederationtls |_tcp |3600 |100 |0,1 |5061 | sipfed.online.lync.com |

  
5. Ajoutez l’autre enregistrement SRV en choisissant les valeurs de la deuxième ligne du tableau. 
  
6. Sélectionnez **Continuer**.

7. Sélectionnez **enregistrer les modifications**.

    
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
