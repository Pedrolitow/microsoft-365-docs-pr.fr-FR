---
title: Connecter vos enregistrements DNS web.com à Microsoft 365
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
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
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services sur web.com microsoft.
ms.openlocfilehash: b95fd5412b7ddc4363e8d5e4ea345c1f551feef8
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586800"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>Connecter vos enregistrements DNS web.com à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si web.com est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
Une fois ces enregistrements ajoutés web.com, votre domaine est installé pour fonctionner avec services Microsoft.

> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

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

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.** 
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste."::: 
  
1. Faites défiler vers le bas pour sélectionner **Outils** avancés et en côté **des enregistrements DNS** avancés, sélectionnez **GÉRER**.
    
    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **TXT** dans la liste liste.

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant. 
    
    |**Fait référence**|**Valeur TXT**|**TTL (Durée de vie)**|
    |:-----|:-----|:----|
    |@  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)    |1 heure  <br/> |
  
5. Sélectionnez **AJOUTER**.
  
6. Patientez quelques minutes avant de vérifier votre nouvel enregistrement TXT, afin que l’enregistrement que vous venons de créer puisse être mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
Pour vérifier l’enregistrement dans Microsoft 365 :
  
1. Dans le Centre d’administration, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
    
1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer la configuration.** 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.
  
1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.** 
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
  
1. Faites défiler vers le bas pour sélectionner **Outils** avancés et en côté **des enregistrements DNS** avancés, sélectionnez **GÉRER**.
    
    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **MX** dans la liste liste.

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant. 
    
    | **Fait référence à** | **Mail Server (Serveur de courrier)**|**Priorité**|**TTL**|
    |:-----|:-----|:-----|:-----| 
    | @ |*\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenez-le  *\<domain-key\>*  à partir du Centre d’administration Microsoft.   [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) | Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> 1| 1 Hour  <br/> |
   
1. Sélectionnez **AJOUTER**.
  
1. Si d’autres enregistrements MX sont répertoriés dans la section **Enregistrements MX,** cochez la case en regard de l’enregistrement sous **Supprimer,** puis sélectionnez **Enregistrer.** 

## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.** 
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.
 
    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
 
1. Faites défiler vers le bas pour sélectionner **Outils** avancés et en côté **des enregistrements DNS** avancés, sélectionnez **GÉRER**.
    
    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **CNAME** dans la liste de listes.

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant. 
    
    |**Fait référence à** | **Nom de l’hôte** | **Alias to (Alias vers)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|
    | Autre hôte  <br/>| autodiscover  <br/>| autodiscover.outlook.com  <br/> | 1 heure  <br/>  |
  
1. Sélectionnez **AJOUTER**.
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. 
  
1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.** 
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
  
1. Faites défiler vers le bas pour sélectionner **Outils** avancés et en côté **des enregistrements DNS** avancés, sélectionnez **GÉRER**.
    
    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **TXT** dans la liste liste.

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant. 
    
    |**Fait référence à**|**Valeur TXT**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|
    |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.  | 1 Hour  <br/> 
 
5. Sélectionnez **AJOUTER**.
  
## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversation, les appels de conférence et les appels vidéo, en plus de Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.** 
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
  
1. Faites défiler vers le bas pour sélectionner **Outils** avancés et en côté **des enregistrements DNS** avancés, sélectionnez **GÉRER**.
    
    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** **sélectionnez SRV** dans la liste liste.

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant. 
    
    | **Type** |**Service**|**Protocol (Protocole)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|**Priorité**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    | SRV |_sip  <br/> |TLS  <br/> |100  <br/> |443  <br/> |sipdir.online.lync.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> | 1  <br/> | 1 heure  <br/> |
    | SRV |_sipfederationtls  <br/> |TCP <br/> |100  <br/> |5061  <br/> |sipfed.online.lync.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> |1  <br/> | 1 Hour  <br/> |
  
6. Sélectionnez **AJOUTER**.
  
7. Pour ajouter l'autre enregistrement SRV :
    
    Dans la section **DNS** avancée, créez un enregistrement en utilisant les valeurs de la deuxième ligne du tableau, puis sélectionnez de nouveau **ADD** pour compléter cet enregistrement. 
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis 
    
1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.** 
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.
 
    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
 
1. Faites défiler vers le bas pour sélectionner **Outils** avancés et en côté **des enregistrements DNS** avancés, sélectionnez **GÉRER**.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **CNAME** dans la liste de listes.

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant. 
    
    | **Type (Type)**|**Fait référence à | Nom d’hôte**|**Alias to (Alias vers)**| **TTL (Durée de vie)** |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Autre hôte | sip  <br/> |sipdir.online.lync.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> |1 heure  <br/> |
    | CNAME| Autre hôte | lyncdiscover  <br/> |webdir.online.lync.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> | 1 Hour  <br/> |
  
1. Sélectionnez **AJOUTER**.
  
1. À l’aide des étapes précédentes et des valeurs de la deuxième ligne du tableau, ajoutez l’autre enregistrement CNAME.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et gestion des périphériques mobiles pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. La gestion des appareils mobiles nécessite 2 enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.** 
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.
 
    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
 
1. Faites défiler vers le bas pour sélectionner **Outils** avancés et en côté **des enregistrements DNS** avancés, sélectionnez **GÉRER**.
    
    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **CNAME** dans la liste de listes.

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant. 
    
    | **Type (Type)**|**Fait référence à | Nom d’hôte**|**Alias to (Alias vers)**| **TTL (Durée de vie)** |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Autre hôte | enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> | 1 heure  <br/> |
    | CNAME | Autre hôte |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> | 1 Hour  <br/> |
  
1. Sélectionnez **AJOUTER**.
  
1. À l’aide des étapes précédentes et des valeurs de la deuxième ligne du tableau, ajoutez l’autre enregistrement CNAME.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).