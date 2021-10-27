---
title: Connecter vos enregistrements DNS sur Amazon Web Services (AWS) pour Microsoft 365
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
ms.assetid: 7a2efd75-0771-4897-ba7b-082fe5bfa9da
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online et d’autres services sur Amazon Web Services (AWS) pour Microsoft.
ms.openlocfilehash: 1e148b13a89def2eb034ca0bcaa4287c890fe904
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586444"
---
# <a name="connect-your-dns-records-at-amazon-web-services-aws-to-microsoft-365"></a>Connecter vos enregistrements DNS sur Amazon Web Services (AWS) pour Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si AWS est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Online pour Les entreprises, etc.
  
Une fois ces enregistrements ajoutés sur AWS, votre domaine est installé pour fonctionner avec services Microsoft.
  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
1. Sur la page d’accueil, sous **Domaines,** sélectionnez **Domaines enregistrés.**
    
1. Sous **Nom de** domaine, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque**: si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez Créer une **zone** hébergée et complétez les étapes avant de passer à l’étape suivante. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez vérifier.":::

1. Sélectionnez **Gérer DNS.** 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Nom de domaine,** sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez vérifier.":::

1. Sélectionnez **Créer un enregistrement.**
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choose the **Type** and **Routing Policy** values from the drop-down lists.) 
    
    > [!TIP]
    > The quotation marks required by the onscreen instructions are supplied automatically. You don't need to type them manually. 
  
    ||||||
    |:-----|:-----|:-----|:-----|:-----|
    |**Nom de l’enregistrement** <br/> |**Type d’enregistrement** <br/> |**Valeur** <br/> |**TTL (Seconds) (Durée de vie (secondes))** <br/> |**Stratégie de routage** <br/> |
    |(Leave this field empty.)  <br/> |TXT : utilisé pour vérifier les expéditeurs de messages électroniques  <br/> |MS=ms *XXXXXXXX*  <br/>**Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) |300  <br/> |Simple  <br/> |
   
1. Sélectionnez **Créer des enregistrements.**
    
1. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
Maintenant que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, revenir à Microsoft et demander une recherche pour l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

Pour vérifier l’enregistrement dans Microsoft 365 :
  
1. Dans le Centre d’administration, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
    
1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer la configuration.** 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.
  
1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft-365"></a>Ajoutez un enregistrement MX afin que le courrier électronique de votre domaine soit envoyé Microsoft 365

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
1. Sur la page d’accueil, sous **Domaines,** sélectionnez **Domaines enregistrés.**
    
1. Sous **Nom de** domaine, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque**: si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez Créer une **zone** hébergée et complétez les étapes avant de passer à l’étape suivante. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer DNS.** 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Nom de domaine,** sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement.**
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choisissez les **valeurs de** stratégie de type et **de routage** dans les listes de listes.) 
    
    > [!TIP]
    > The quotation marks required by the onscreen instructions are supplied automatically. You don't need to type them manually. 
    
    |**Nom de l’enregistrement**|**Type d’enregistrement**|**Valeur**|**TTL (Seconds) (Durée de vie (secondes))**|**Stratégie de routage**|
    |:-----|:-----|:-----|:-----|:-----|
    |(Laissez ce champ vide.)  <br/> |MX - Serveur de courrier  <br/> |0  *\<domain-key\>*  .mail.protection.outlook.com.  <br/> La valeur 0 est la valeur de priorité Max. Ajoutez-la au début de la valeur MX, séparée du reste de la valeur par une espace.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> **Remarque :** Obtenez votre \<*domain-key*\> compte Microsoft 365 client. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) | 300  <br/> | Routage simple <br/> |
  
1. Sélectionnez **Créer des enregistrements.**
  
1. S’il existe d’autres enregistrements MX, supprimez-les en sélectionnant l’enregistrement, puis en sélectionnant **Supprimer**.
  
## <a name="add-the-cname-record-required-for-microsoft-365"></a>Ajoutez l’enregistrement CNAME requis pour Microsoft 365

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
1. Sur la page d’accueil, sous **Domaines,** sélectionnez **Domaines enregistrés.**
    
1. Sous **Nom de** domaine, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque**: si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez Créer une **zone** hébergée et complétez les étapes avant de passer à l’étape suivante. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer DNS.** 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Nom de domaine,** sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement.**
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choisissez les **valeurs de** stratégie de type et **de routage** dans les listes de listes.) 
    
    |**Nom de l’enregistrement**|**Type d’enregistrement**|**Valeur**| **TTL** |**Stratégie de routage**|
    |:-----|:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME : approvisionnement du trafic vers un autre nom de domaine  <br/> | autodiscover.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> | 300  <br/> |Simple  <br/> |
  
6. Sélectionnez **Créer des enregistrements.**
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](../../enterprise/external-domain-name-system-records.md). Pour valider votre enregistrement SPF, vous pouvez utiliser l’un de ces outils[de validation SPF.](../setup/domains-faq.yml) 
  
1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
1. Sur la page d’accueil, sous **Domaines,** sélectionnez **Domaines enregistrés.**
    
1. Sous **Nom de** domaine, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque**: si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez Créer une **zone** hébergée et complétez les étapes avant de passer à l’étape suivante. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer DNS.** 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Nom de domaine,** sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement.**
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choisissez la **valeur Type** dans les listes de listes.) 
    
    |**Type d’enregistrement** | **Valeur**|
    |:-----|:-----|
    |TXT : utilisé pour vérifier les expéditeurs de messages électroniques et les valeurs propres à l’application |v=spf1 include:spf.protection.outlook.com -all  <br/> (Les guillemets requis pour les instructions à l'écran sont insérés automatiquement. Vous n'avez pas besoin de les entrer manuellement.)  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.   |
  
6. Sélectionnez **Créer des enregistrements.**

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversation, les appels de conférence et les appels vidéo, en plus de Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
1. Sur la page d’accueil, sous **Domaines,** sélectionnez **Domaines enregistrés.**
    
1. Sous **Nom de** domaine, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque**: si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez Créer une **zone** hébergée et complétez les étapes avant de passer à l’étape suivante. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer DNS.** 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Nom de domaine,** sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement.**
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choose the **Type** and **Routing Policy** values from the drop-down lists.) 
    
    |**Nom de l’enregistrement**|**Type d’enregistrement**|**Valeur**|**TTL (Seconds) (Durée de vie (secondes))**|**Stratégie de routage**|
    |:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|SRV - Localisation de service|100 1 443 sipdir.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**><br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte. | 300 |Simple|
    |_sipfederationtls._tcp|SRV - Localisation de service|100 1 5061 sipfed.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**<br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.    | 300 |Simple|
  
7. Pour ajouter l’autre enregistrement SRV, sélectionnez Ajouter un autre **enregistrement,** créez un enregistrement à l’aide des valeurs de la ligne suivante du tableau, puis sélectionnez de nouveau **Créer des enregistrements.** 
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis 
    
1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
1. Sur la page d’accueil, sous **Domaines,** sélectionnez **Domaines enregistrés.**
    
1. Sous **Nom de** domaine, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque**: si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez Créer une **zone** hébergée et complétez les étapes avant de passer à l’étape suivante. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer DNS.** 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Nom de domaine,** sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement.** 
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choisissez les **valeurs de** stratégie de type et **de routage** dans les listes de listes.) 

    |**Nom de l’enregistrement**|**Type d’enregistrement**|**Valeur**| **TTL** |**Stratégie de routage**|
    |:-----|:-----|:-----|:-----|:-----|
    |sip  <br/> |CNAME - Nom canonique  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |300  <br/> |Simple  <br/> |
    |lyncdiscover  <br/> |CNAME - Nom canonique  <br/> |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/>  |300  <br/> ||Simple  <br/> |
  
1. Pour ajouter l’autre enregistrement CNAME, sélectionnez Ajouter un autre **enregistrement,** créez un enregistrement à l’aide des valeurs de la ligne suivante du tableau. 

1. Sélectionnez **Créer des enregistrements.**
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et gestion des périphériques mobiles pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. La gestion des périphériques mobiles nécessite deux enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.
    
1. Sur la page d’accueil, sous **Domaines,** sélectionnez **Domaines enregistrés.**
    
1. Sous **Nom de** domaine, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque**: si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez Créer une **zone** hébergée et complétez les étapes avant de passer à l’étape suivante. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer DNS.** 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Nom de domaine,** sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement.**

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    (Choisissez les **valeurs de** stratégie de type et **de routage** dans les listes de listes.) 
    
    |**Nom de l’enregistrement**|**Type d’enregistrement**|**Valeur**| **TTL** |**Stratégie de routage**|
    |:-----|:-----|:-----|:-----|:-----|
    |enterpriseregistration  <br/> |CNAME - Nom canonique  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |300  <br/> |Simple  <br/> |
    |enterpriseenrollment  <br/> |CNAME - Nom canonique  <br/> | enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/>|300  <br/> | |Simple  <br/> |
  
1. Pour ajouter l’autre enregistrement CNAME, sélectionnez Ajouter un autre **enregistrement,** créez un enregistrement à l’aide des valeurs de la ligne suivante du tableau. 

1. Sélectionnez **Créer des enregistrements.**
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).