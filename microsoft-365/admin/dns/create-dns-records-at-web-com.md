---
title: Créer des enregistrements DNS web.com microsoft
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
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services sur web.com pour Microsoft.
ms.openlocfilehash: b667b2e69822fcd69babda7790a6468b640b073b
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50909981"
---
# <a name="create-dns-records-at-webcom-for-microsoft"></a>Créer des enregistrements DNS web.com microsoft

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si web.com est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
Une fois ces enregistrements ajoutés web.com, votre domaine est installé pour fonctionner avec les services Microsoft.

  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine
<a name="BKMK_Nameservers"> </a>

> [!IMPORTANT]
> Vous devez effectuer cette procédure au niveau du bureau d'enregistrement de domaines auprès duquel vous avez acheté et inscrit votre domaine. 
  
Lorsque vous vous êtes inscrit à web.com, vous avez ajouté un domaine à l’aide du processus **web.com’installation.** 
  
Pour vérifier et créer des enregistrements DNS pour votre domaine dans Microsoft, vous devez d’abord modifier les serveurs de noms de votre bureau d’enregistrement de domaines afin qu’ils utilisent les serveurs de noms web.com.
  
Pour modifier vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit.
  
1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.
    
2. Créez deux enregistrements de nameserver à l’aide des valeurs du tableau suivant, ou modifiez les enregistrements de nameserver existants afin qu’ils correspondent à ces valeurs.
    
    |||
    |:-----|:-----|
    |Premier serveur de noms  <br/> |Utilisez la valeur de nameserver fournie par web.com.  <br/> |
    |Deuxième serveur de noms  <br/> |Utilisez la valeur de nameserver fournie par web.com.  <br/> |
   
    > [!TIP]
    > You should use at least two name server records. Si d’autres serveurs de noms sont répertoriés, vous devez les supprimer. 
  
3. Enregistrez vos modifications.
    
> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Ensuite, votre messagerie Microsoft et d’autres services seront tous définies pour fonctionner avec votre domaine. 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
  
2. Dans la page **Gestionnaire de comptes,** sélectionnez **Mes noms de domaine.** 
  
3. Sous **Gérer *mon domaine***, sélectionnez **Modifier les enregistrements DNS avancés.**

  
4. Dans la page **Noms de** domaine, sous **Texte (Enregistrements TXT),** cliquez sur Modifier les enregistrements **TXT,** puis sélectionnez les valeurs dans le tableau suivant. 
    
    |**Host (Hôte)**|**TTL (Durée de vie)**|**Text (Texte)**|
    |:-----|:-----|:----|
    |@  <br/> |3600  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)    |
  
    
5. Sélectionnez **Continuer**.
  
  
6. Patientez quelques minutes avant de vérifier votre nouvel enregistrement TXT, afin que l’enregistrement que vous venons de créer puisse être mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
    
  
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
<a name="BKMK_add_MX"> </a>

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
  
2. Dans la page **Gestionnaire de comptes,** sélectionnez **Mes noms de domaine.** 
  
3. Sous **Gérer *mon domaine***, sélectionnez **Modifier les enregistrements DNS avancés.**

4. Sous **Serveurs de messagerie (enregistrements MX),** cliquez sur Modifier les enregistrements **MX,** puis sélectionnez les valeurs dans le tableau suivant. 
    
    |**Priorité**|**TTL**|**Mail Server (Serveur de courrier)**|
    |:-----|:-----|:-----|
    |1  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> |3600  <br/> |*\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenez votre *\<domain-key\>* depuis votre compte Microsoft.   [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) |
   

5. Sélectionnez **Enregistrer**.
  
6. Si d’autres enregistrements MX sont répertoriés dans la section **Enregistrements MX,** cochez la case en regard de l’enregistrement sous **Supprimer,** puis sélectionnez **Enregistrer.** 
  
7. Dans l’écran de confirmation, sélectionnez **Enregistrer les modifications.** 

  
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a>Ajouter les six enregistrements CNAME requis pour Microsoft
<a name="BKMK_add_CNAME"> </a>

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Avant toute chose, vous serez invité à vous connecter.
     
2. Dans la page **Gestionnaire de comptes,** sélectionnez **Mes noms de domaine.** 
  
3. Sous **Gérer *mon domaine***, sélectionnez **Modifier les enregistrements DNS avancés.**

4. Ajoutez le premier des six enregistrements CNAME.
    
    Sous **Alias d’hôte (enregistrements CNAME),** cliquez sur Modifier les enregistrements **CNAME,** puis sélectionnez les valeurs dans le tableau suivant.
    
    
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

    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. 
  
1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
    
  
2. Dans la page **Gestionnaire de comptes,** sélectionnez **Mes noms de domaine.** 
  
3. Sous **Gérer *mon domaine***, sélectionnez **Modifier les enregistrements DNS avancés.**

  
4. Dans la page **Noms de** domaine, sous **Texte (Enregistrements TXT),** cliquez sur Modifier les enregistrements **TXT,** puis sélectionnez les valeurs dans le tableau suivant.   
    
    |**Host (Hôte)**|**TTL (Durée de vie)**|**Text (Texte)**|
    |:-----|:-----|:-----|
    |@  <br/> |3600  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.   |

 
5. Sélectionnez **Continuer**.

6. Sélectionnez **Enregistrer les modifications**.
    

  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft
<a name="BKMK_add_SRV"> </a>

> [!IMPORTANT]
> N’oubliez pas que web.com est chargé de rendre cette fonctionnalité disponible. Si vous constatez des différences entre les étapes ci-dessous et l’interface utilisateur graphique web.com (interface utilisateur graphique), tirez parti de [la communauté web.com.](https://community.web.com.com/) 

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
      
2. Dans la page **Gestionnaire de comptes,** sélectionnez **Mes noms de domaine.** 
  
3. Sous **Gérer *mon domaine***, sélectionnez **Modifier les enregistrements DNS avancés.**
  
4. Ajoutez le premier des deux enregistrements SRV.

    Sous **Service (Enregistrements SRV),** cliquez sur Modifier les enregistrements **SRV,** puis sélectionnez les valeurs dans le tableau suivant. 
        
    |**Service**|**Protocol (Protocole)**|**TTL (Durée de vie)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip |_tls |3600 | 100|1 |443 |sipfed.online.lync.com  |
    |_sipfederationtls |_tcp |3600 |100 |1 |5061 | sipfed.online.lync.com |

  
5. Ajoutez l’autre enregistrement SRV en choisissant les valeurs de la deuxième ligne du tableau. 
  
6. Sélectionnez **Continuer**.

7. Sélectionnez **Enregistrer les modifications**.

    
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
