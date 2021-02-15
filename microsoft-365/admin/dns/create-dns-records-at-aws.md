---
title: Créer des enregistrements DNS sur Amazon Web Services (AWS) pour Microsoft
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
ms.assetid: 7a2efd75-0771-4897-ba7b-082fe5bfa9da
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services sur Amazon Web Services (AWS) pour Microsoft.
ms.openlocfilehash: bb687b8685aed79f5f768c12d652205bbbed0f59
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49657971"
---
# <a name="create-dns-records-at-amazon-web-services-aws-for-microsoft"></a>Créer des enregistrements DNS sur Amazon Web Services (AWS) pour Microsoft

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si AWS est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Online pour les entreprises, etc.
  
Une fois ces enregistrements ajoutés sur AWS, votre domaine est installé pour fonctionner avec les services Microsoft.
  

  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **Ressources,** sélectionnez **Zones hébergées.**
    
3. Dans la page **Zones hébergées,** dans la colonne **Nom** de domaine, sélectionnez le nom du domaine à modifier. 
    
4. Sélectionnez **Créer un jeu d’enregistrement.**
    
5. In the **Create Record Set** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** and **Routing Policy** values from the drop-down lists.) 
    
    > [!TIP]
    > The quotation marks required by the onscreen instructions are supplied automatically. You don't need to type them manually. 
  
    |||||||
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |**Name** <br/> |**Type (Type)** <br/> |**Alias** <br/> |**TTL (Seconds) (Durée de vie (secondes))** <br/> |**Value (Valeur)** <br/> |**Routing Policy (Stratégie de routage)** <br/> |
    |(Leave this field empty.)  <br/> |TXT - Text  <br/> |Non  <br/> |300  <br/> |MS=ms *XXXXXXXX*  <br/>**Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |Simple  <br/> |
   
6. Sélectionnez **Créer**.
    
7. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
Maintenant que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous revenir à Microsoft et demander une recherche pour l’enregistrement.
  
Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration Microsoft, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft-365"></a>Ajouter un enregistrement MX afin que le courrier électronique de votre domaine soit envoyé à Microsoft 365
<a name="BKMK_add_MX"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **Ressources,** sélectionnez **Zones hébergées.**
    
3. Dans la page **Zones hébergées,** dans la colonne **Nom** de domaine, sélectionnez le nom du domaine à modifier. 
    
4. Sélectionnez **Créer un jeu d’enregistrement.**
    
5. In the **Create Record Set** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
    (Choose the **Type** and **Routing Policy** values from the drop-down lists.) 
    
    |**Name**|**Type (Type)**|**Alias**|**TTL (Seconds) (Durée de vie (secondes))**|**Value (Valeur)**|**Routing Policy (Stratégie de routage)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |(Laissez ce champ vide.)  <br/> |MX - Serveur de courrier  <br/> |Non  <br/> |300  <br/> |0  *\<domain-key\>*  .mail.protection.outlook.com.  <br/> La valeur 0 est la valeur de priorité Max. Ajoutez-la au début de la valeur MX, séparée du reste de la valeur par une espace.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> **Remarque :** Obtenez votre \<*domain-key*\> compte Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |Simple  <br/> |
       
    ![AWS-BP-Configure-2-1](../../media/94a71ce7-1b3b-4b1a-9ad3-9592db133075.png)
  
6. Sélectionnez **Créer**.
    
    ![AWS-BP-Configurer-2-2](../../media/1c050c72-c04f-48d5-a8e9-44cd83ddd33e.png)
  
7. S'il existe d'autres enregistrements MX, supprimez-les.
    
    > [!IMPORTANT]
    > AWS stocke les enregistrements MX en tant qu'ensemble pouvant contenir plusieurs enregistrements. **NE sélectionnez** **PAS Supprimer le jeu d’enregistrements,** car cela supprimera tous vos enregistrements MX, y compris celui que vous viennent d’ajouter. Suivez plutôt les instructions suivantes. 
  
    Tout d’abord, sélectionnez le jeu d’enregistrement MX.
    
    ![AWS-BP-Configurer-2-3](../../media/9d9388cb-e2d0-43b7-928c-e1d07e519c6f.png)
  
    Ensuite, dans la zone **Edit Record Set (Modifier le jeu d'enregistrements)**, supprimez chaque enregistrement MX obsolète en sélectionnant son entrée dans la zone **Value (Valeur)** en appuyant sur la touche **Suppr** de votre clavier. 
    
    ![AWS-BP-Configurer-2-4](../../media/c3b0c1bc-21ab-44cc-84b7-f504725c5540.png)
  
8. Sélectionnez **Enregistrer le jeu d’enregistrement.**
    
    ![AWS-BP-Configurer-2-5](../../media/86f0998d-f5d4-4750-a93d-ac13b318c40b.png)
  
## <a name="add-the-five-cname-records-that-are-required-for-microsoft-365"></a>Ajouter les cinq enregistrements CNAME requis pour Microsoft 365
<a name="BKMK_add_CNAME"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **Ressources,** sélectionnez **Zones hébergées.**
    
3. Dans la page **Zones hébergées,** dans la colonne **Nom** de domaine, sélectionnez le nom du domaine à modifier. 
    
4. Sélectionnez **Créer un jeu d’enregistrement.**
    
5. Ajoutez le premier enregistrement CNAME.
    
    Dans la zone **Create Record Set (Créer un jeu d'enregistrements)**, dans les champs du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    (Sélectionnez les valeurs **Type (Type)** et **Routing Policy (Stratégie de routage)** dans les listes déroulantes.) 
    
    |**Name**|**Type (Type)**|**Alias**|**TTL (Seconds) (Durée de vie (secondes))**|**Value (Valeur)**|**Routing Policy (Stratégie de routage)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME - Nom canonique  <br/> |Non  <br/> |300  <br/> |autodiscover.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Simple  <br/> |
    |sip  <br/> |CNAME - Nom canonique  <br/> |Non  <br/> |300  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Simple  <br/> |
    |lyncdiscover  <br/> |CNAME - Nom canonique  <br/> |Non  <br/> |300  <br/> |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Simple  <br/> |
    |enterpriseregistration  <br/> |CNAME - Nom canonique  <br/> |Non  <br/> |300  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Simple  <br/> |
    |enterpriseenrollment  <br/> |CNAME - Nom canonique  <br/> |Non  <br/> |300  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Simple  <br/> |
   
    ![AWS-BP-Configure-3-1](../../media/895c71bd-0e3a-425e-9681-98c1c67e714b.png)
  
6. Sélectionnez **Créer**.
    
    ![AWS-BP-Configurer-3-2](../../media/33964846-5282-44a4-b241-62ce02b96735.png)
  
7. Ajoutez les quatre autres enregistrements CNAME.
    
    Dans la page **Zones** hébergées, sélectionnez Créer un jeu d’enregistrement, créez  un enregistrement à l’aide des valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau Créer pour terminer cet enregistrement.  
    
    Répétez ce processus jusqu’à ce que vous avez créé les cinq enregistrements CNAME.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de n’avoir qu’un seul  *enregistrement*  SPF qui inclut les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](https://docs.microsoft.com/microsoft-365/enterprise/external-domain-name-system-records). Pour valider votre enregistrement SPF, vous pouvez utiliser l’un de ces outils[de validation SPF.](../setup/domains-faq.yml) 
  
1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **Ressources,** sélectionnez **Zones hébergées.**
    
3. Dans la page **Zones hébergées,** dans la colonne **Nom** de domaine, sélectionnez le nom du domaine à modifier. 
    
4. Sélectionnez **le jeu d’enregistrement TXT.** 
    
    ![AWS-BP-Configurer-4-1](../../media/0310fa66-c016-4987-80df-930f1c8f3c39.png)
  
5. Dans la zone **Edit Record Set (Modifier le jeu d'enregistrements)**, à la fin de l'entrée active dans le champ **Value (Valeur)** pour l'enregistrement existant, appuyez sur la touche Entrée de votre clavier pour créer une ligne. Ensuite, dans cette nouvelle ligne (sous la valeur existante), tapez ou copiez-collez la valeur du tableau suivant (vous pouvez voir un exemple dans l'illustration située sous le tableau). 
    
    |**Valeur :**|
    |:-----|
    |v=spf1 include:spf.protection.outlook.com -all  <br/> (Les guillemets requis pour les instructions à l'écran sont insérés automatiquement. Vous n'avez pas besoin de les entrer manuellement.)  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
   
    ![AWS-BP-Configure-4-2](../../media/beb3c086-eaf8-4245-9860-18512a3ff72e.png)
  
6. Sélectionnez **Enregistrer le jeu d’enregistrement.**
    
    ![AWS-BP-Configurer-4-3](../../media/94b9306c-bdc9-4f84-ad6f-6d12edbfde90.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft-365"></a>Ajouter les deux enregistrements SRV requis pour Microsoft 365
<a name="BKMK_add_SRV"> </a>

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
2. Dans la page **Ressources,** sélectionnez **Zones hébergées.**
    
3. Dans la page **Zones hébergées,** dans la colonne **Nom** de domaine, sélectionnez le nom du domaine à modifier. 
    
4. Sélectionnez **Créer un jeu d’enregistrement.**
    
5. Ajouter le premier enregistrement SRV.
    
    Dans la zone **Create Record Set (Créer un jeu d'enregistrements)**, dans les champs du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. 
    
    (Sélectionnez les valeurs **Type (Type)** et **Routing Policy (Stratégie de routage)** dans les listes déroulantes.) 
    
    |**Name**|**Type (Type)**|**Alias**|**TTL (Seconds) (Durée de vie (secondes))**|**Value (Valeur)**|**Routing Policy (Stratégie de routage)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|SRV - Localisation de service|Non|300|100 1 443 sipdir.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**><br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |Simple|
    |_sipfederationtls._tcp|SRV - Localisation de service|Non|300|100 1 5061 sipfed.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**<br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |Simple|
   
    ![AWS-BP-Configure-5-1](../../media/c3f841d3-6076-428f-bb04-e71cc5f392fa.png)
  
6. Sélectionnez **Créer**.
    
    ![AWS-BP-Configurer-5-2](../../media/1bf5dc58-a46b-47a5-bd69-7c2147dd4e50.png)
  
7. Pour ajouter l'autre enregistrement SRV :
    
    Dans la page **Zones** hébergées, sélectionnez Créer un jeu d’enregistrement, créez  un enregistrement à l’aide des valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau Créer pour terminer cet enregistrement.  
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
