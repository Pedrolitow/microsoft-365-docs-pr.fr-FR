---
title: Connecter vos enregistrements DNS sur Network Solutions Microsoft 365
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
ms.assetid: 1dc55f9f-5309-450f-acc3-b2b4119c8be3
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services sur Network Solutions pour Microsoft.
ms.openlocfilehash: f0599ef178e9a3dde097b94e7c3f980f59e88636
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586359"
---
# <a name="connect-your-dns-records-at-network-solutions-to-microsoft-365"></a>Connecter vos enregistrements DNS sur Network Solutions Microsoft 365

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Network Solutions est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
    
Une fois ces enregistrements ajoutés sur Network Solutions, votre domaine est installé pour fonctionner avec services Microsoft.
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.**

1. Cochez la case en regard du domaine à modifier.
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
  
1. Faites défiler vers le bas pour sélectionner **Outils** avancés et en côté **des enregistrements DNS** avancés, sélectionnez **GÉRER**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.
  
1. Sélectionnez **Continuer** et, dans la page Gérer les enregistrements DNS avancés, **sélectionnez +AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **TXT** dans la liste liste.
  
1. In the boxes for the new record, type or copy and paste the values in the following table.
    
    |**Fait référence à**|**VALEUR TXT**|**TTL**|
    |:-----|:-----|:-----|
    |@  <br/> (The system will change this value to **@ (None)** when you save the record.)  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) |3600  <br/>    |
  
1. Sélectionnez **AJOUTER**.
  
    > [!NOTE]
    > Sélectionnez **Affichage** classique dans le coin supérieur droit pour afficher l’enregistrement TXT que vous avez créé.   
  
1. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
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
  
1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.**

1. Cochez la case en regard du domaine à modifier.
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
  
1. Faites défiler vers le bas pour sélectionner **Outils** avancés et en côté **des enregistrements DNS** avancés, sélectionnez **GÉRER**.
    
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.
    
1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **MX** dans la liste liste.
  
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    **Fait référence à** |**Mail Server (Serveur de courrier)**|**Priorité**|**TTL**|
    |:-----|:-----|:-----|:-----|
    | @ | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> **Remarque :** Obtenez votre *\<domain-key\>* depuis votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) | 0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> | 1 heure  <br/> |  
  
1. Sélectionnez **AJOUTER**.
  
    > [!NOTE]
    > Sélectionnez **Affichage** classique dans le coin supérieur droit pour afficher l’enregistrement TXT que vous avez créé.  

1. S’il existe d’autres enregistrements MX, supprimez-les tous en sélectionnant l’outil d’édition, puis supprimez **pour** chaque enregistrement. 
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.**

1. Cochez la case en regard du domaine à modifier.
  
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
  
1. Select **Advanced Tools**, and next to Advanced **DNS Records**, select **MANAGE**.
    
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **CNAME** dans la liste de listes.
  
1. Dans les zones de l’enregistrement CNAME, tapez ou copiez-collez les valeurs du tableau suivant.
    
    |**Fait référence à | Nom d’hôte**|**Alias to (Alias vers)**| **TTL (Durée de vie)** |
    |:-----|:-----|:-----|:-----|
    |Autre hôte| autodiscover  <br/> | autodiscover.outlook.com cette **valeur ne peut pas se terminer par un point (.)** <br/> 1 Hour  <br/> |
  
1. Sélectionnez **AJOUTER**.

    > [!NOTE]
    > Sélectionnez **Affichage** classique dans le coin supérieur droit pour afficher l’enregistrement que vous avez créé.  
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. 
  
1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.**

1. Cochez la case en regard du domaine à modifier.
    
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
 
1. Select **Advanced Tools**, and next to Advanced **DNS Records**, select **MANAGE**.
    
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+AJOUTER UN ENREGISTREMENT.**

1. Sous **Type,** sélectionnez **TXT** dans la liste liste.

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes.
    
    |**Fait référence à**|**VALEUR TXT**| **TTL**
    |:-----|:-----|:-----|
    |@  <br/> (The system will change this value to **@ (None)** when you save the record.)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte. | 1 Hour  <br/> |
       
1. Sélectionnez **AJOUTER**.
  
    > [!NOTE]
    > Sélectionnez **Affichage** classique dans le coin supérieur droit pour afficher l’enregistrement que vous avez créé.  
  
## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversation, les appels de conférence et les appels vidéo, en plus de Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.**

1. Cochez la case en regard du domaine à modifier.
    
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::

1. Select **Advanced Tools**, and next to Advanced **DNS Records**, select **MANAGE**.
    
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+AJOUTER UN ENREGISTREMENT.**

1. Dans les zones des deux nouveaux enregistrements, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (Sélectionnez les valeurs **Service (Service)** et **Protocol (Protocole)** dans les listes déroulantes.) 
    
    | **Type** |**Service**|**Protocol (Protocole)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|**Priorité**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    | SRV |_sip  <br/> |_tls  <br/> |100  <br/> |443  <br/> |sipdir.online.lync.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> | 1  <br/> | 1 heure  <br/> |
    | SRV |_sipfederationtls  <br/> |_tcp  <br/> |100  <br/> |5061  <br/> |sipfed.online.lync.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> |1  <br/> | 1 Hour  <br/> |
  
1. Sélectionnez **AJOUTER**.
 
    > [!NOTE]
    > Sélectionnez **Affichage** classique dans le coin supérieur droit pour afficher l’enregistrement que vous avez créé.  

1. Ajoutez l’autre enregistrement SRV en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis 
    
1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.**

1. Cochez la case en regard du domaine à modifier.
    
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
 
1. Select **Advanced Tools**, and next to Advanced **DNS Records**, select **MANAGE**.
    
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT.**
    
1. Ajoutez le premier enregistrement CNAME.
    
    In the **Advanced DNS** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    | **Type (Type)**|**Fait référence à | Nom d’hôte**|**Alias to (Alias vers)**| **TTL (Durée de vie)** |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Autre hôte | sip  <br/> |sipdir.online.lync.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> |1 heure  <br/> |
    | CNAME| Autre hôte | lyncdiscover  <br/> |webdir.online.lync.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> | 1 Hour  <br/> |
   
1. Sélectionnez **AJOUTER**.
 
    > [!NOTE]
    > Sélectionnez **Affichage** classique dans le coin supérieur droit pour afficher l’enregistrement que vous avez créé.  
   
1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et gestion des périphériques mobiles pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. La gestion des appareils mobiles nécessite 2 enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. Pour commencer, accédez à la page de vos domaines sur Network Solutions à l'aide de [ce lien](https://www.networksolutions.com/manage-it). Vous serez invité à vous connecter.
  
1. Sur la page d’accueil, sélectionnez **Noms de domaine.**

1. Cochez la case en regard du domaine à modifier.
    
1. Sous **Actions,** sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::
 
1. Select **Advanced Tools**, and next to Advanced **DNS Records**, select **MANAGE**.
    
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+AJOUTER UN ENREGISTREMENT.**
  
1. Ajoutez le premier enregistrement CNAME.
    
    In the **Advanced DNS** section, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** value from the drop-down list.) 
    
    | **Type (Type)**|**Fait référence à | Nom d’hôte**|**Alias to (Alias vers)**| **TTL (Durée de vie)** |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Autre hôte | enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> | 1 heure  <br/> |
    | CNAME | Autre hôte |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> **Cette valeur ne peut pas se terminer par un point (.)** <br/> | 1 Hour  <br/> |
   
1. Sélectionnez **AJOUTER**.
  
    > [!NOTE]
    > Sélectionnez **Affichage** classique dans le coin supérieur droit pour afficher l’enregistrement que vous avez créé.  

1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
  

  
