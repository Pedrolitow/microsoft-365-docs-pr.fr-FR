---
title: Connecter vos enregistrements DNS sur IONOS de 1&1 à Microsoft 365
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online et d’autres services au niveau 1&1 IONOS pour Microsoft.
ms.openlocfilehash: 9fe9d97f381369836b036a3302e9d28fae070fac
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60556690"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>Connecter vos enregistrements DNS sur IONOS de 1&1 à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 

Si IONOS par 1&1 est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

## <a name="before-you-begin"></a>Avant de commencer

Vous avez deux options pour la configuration des enregistrements DNS pour votre domaine :

- [**Utiliser l’Connecter**](#use-domain-connect-to-verify-and-set-up-your-domain) Si vous n’avez pas encore installé votre domaine auprès d’un autre fournisseur de services de messagerie, utilisez les étapes de l’Connecter de domaine pour vérifier et configurer automatiquement votre nouveau domaine à utiliser avec Microsoft 365. 

OR

- [**Utiliser les étapes manuelles**](#create-dns-records-with-manual-setup) Vérifiez votre domaine en suivant les étapes manuelles ci-dessous et choisissez quand et quels enregistrements ajouter à votre bureau d’enregistrement de domaines. Cela vous permet de configurer de nouveaux enregistrements MX (courrier), par exemple, à votre convenance. 

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Utiliser domain Connecter pour vérifier et configurer votre domaine

Suivez ces étapes pour vérifier et configurer automatiquement votre domaine Cloudflare avec Microsoft 365 :

1. Dans la Centre d'administration Microsoft 365, **sélectionnez Paramètres** domaines, puis sélectionnez le domaine  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>que vous souhaitez configurer.

1. Sélectionnez les trois points (plus d’actions) > **sélectionnez Démarrer la configuration.**

1. Comment voulez-vous connecter votre domaine ? page, sélectionnez **Continuer**.   

1. Dans la page Ajouter des enregistrements DNS, sélectionnez Ajouter des enregistrements **DNS.**

1. On the IONOS by 1&1 login page, sign in to your account, and select **Connecter**, and **Allow**.
    
    Cela termine la configuration de votre domaine pour Microsoft 365. 

## <a name="create-dns-records-with-manual-setup"></a>Créer des enregistrements DNS avec la configuration manuelle

Une fois ces enregistrements ajoutés sur IONOS par 1&1, votre domaine est installé pour fonctionner avec services Microsoft.
  
> [!CAUTION]
> Notez que la fonction IONOS par 1&1 n’autorise pas un domaine à avoir à la fois un enregistrement MX et un enregistrement CNAME de découverte automatique de niveau supérieur. Cela limite les méthodes qui s'offrent à vous pour configurer Exchange Online pour Microsoft. Il existe une solution de contournement,  mais nous vous recommandons de l’utiliser uniquement si vous avez déjà de l’expérience dans la création de sous-domaine auprès d’IONOS d'&1. Si, malgré cette limitation de [service,](../setup/domains-faq.yml) vous choisissez de gérer vos propres enregistrements DNS Microsoft sur IONOS par 1&1, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online, etc. 
  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
### <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. To get started, go to your domains page at IONOS by 1&1 by using [this link](https://my.1and1.com/). Vous serez invité à vous connecter.

1. Sélectionnez **Menu,** puis **sélectionnez Domaines et SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::
  
1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis **sélectionnez DNS**.
 
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste liste liste.":::
    
1. Sélectionnez **Ajouter** un enregistrement, puis sélectionnez la section **TXT.**
    
1. Dans la page Ajouter un enregistrement DNS, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    ||||
    |:-----|:-----|:-----|
  |**Nom de l’hôte** <br/> |**Valeur** <br/> |
|(Laissez ce champ vide)  <br/> |MS=ms *XXXXXXXX*  <br/> REMARQUE : il s’agit d’un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
1. Sélectionnez **Enregistrer**.
    
1. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Microsoft 365 et demandez à Microsoft 365 de rechercher l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

Pour vérifier l’enregistrement dans Microsoft 365 :
  
1. Dans le Centre d’administration, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
    
2. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer la configuration.**   
  
3. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
  
### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
  
> [!NOTE]
> Si vous vous êtes inscrit auprès 1und1.de, [connectez-vous ici.](https://go.microsoft.com/fwlink/?linkid=859152) 
  
1. To get started, go to your domains page at IONOS by 1&1 by using [this link](https://my.1and1.com/). Vous serez invité à vous connecter.
    
1. Sélectionnez **Menu,** puis **sélectionnez Domaines et SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::
  
1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis **sélectionnez DNS**.
 
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste liste liste.":::
    
1. Sélectionnez **Ajouter** un enregistrement, puis sélectionnez la section **MX.**
    
1. Dans la page Ajouter un enregistrement DNS, dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
    | **Nom de l’hôte**| **Points to (Pointe vers)** |**Priorité**| **TTL** |
    |:-----|:-----|:-----| :-----|
    |  @  | *\<domain-key\>*  .mail.protection.outlook.com  <br/>  REMARQUE : obtenez le vôtre \<domain-key\> à partir de votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). | 1 heure |
  
8. Sélectionnez **Enregistrer**.<br/>(Vous devrez peut-être faire défiler la page vers le bas.)<br/>

6. S’il existe des enregistrements MX déjà répertoriés, supprimez chacun d’eux en sélectionnant **Supprimer l’enregistrement**.
  
### <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

> [!NOTE]
> Si vous vous êtes inscrit auprès 1und1.de, [connectez-vous ici.](https://go.microsoft.com/fwlink/?linkid=859152) 
  
1. To get started, go to your domains page at IONOS by 1&1 by using [this link](https://my.1and1.com/). Vous serez invité à vous connecter.
    
1. Sélectionnez **Menu,** puis **sélectionnez Domaines et SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::
  
1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis **sélectionnez DNS**.
 
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste liste liste.":::
    
    Vous allez maintenant créer deux sous-domaines et définir une valeur **Alias (Alias)** pour chaque sous-domaine.<br/>(Ceci est obligatoire car 1&1 IONOS prend en charge un seul enregistrement CNAME de niveau supérieur, mais Microsoft requiert plusieurs enregistrements CNAME.)<br/>Tout d'abord, vous devez créer le sous-domaine de découverte automatique.
    
1. Sélectionnez **Ajouter un sous-domaine.**
  
1. Dans la **zone Ajouter un sous-domaine** pour le nouveau sous-domaine, tapez ou copiez-collez uniquement la valeur Ajouter un sous-domaine du tableau suivant.  (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)

    |**Ajouter un sous-domaine**|**Alias**|
    |:-----|:-----|
    |autodiscover  <br/> |autodiscover.outlook.com   | 
  
1. Sous **Actions** pour le **sous-domaine** de découverte automatique que vous venons de créer, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS** dans la liste. <br/>

1. Sélectionnez **Ajouter** un enregistrement, puis sélectionnez la section **CNAME.**
  
1. Dans la zone **Alias :**, tapez ou copiez-collez uniquement la valeur **Alias** du tableau suivant.<br/> 
    
    |**Ajouter un sous-domaine**|**Alias**|
    |:-----|:-----|
    |autodiscover  <br/> |autodiscover.outlook.com   |
  
1. Cochez la case correspondant à la clause d'exclusion de responsabilité **I am aware** (J'accepte).<br/>
  
1. Sélectionnez **Enregistrer**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](../../enterprise/external-domain-name-system-records.md). Pour valider votre enregistrement SPF, vous pouvez utiliser l’un de ces outils[de validation SPF.](../setup/domains-faq.yml) 
  
> [!NOTE]
> Si vous vous êtes inscrit auprès 1und1.de, [connectez-vous ici.](https://go.microsoft.com/fwlink/?linkid=859152) 
  
1. To get started, go to your domains page at IONOS by 1&1 by using [this link](https://my.1and1.com/). Vous serez invité à vous connecter.
    
1. Sélectionnez **Menu,** puis **sélectionnez Domaines et SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::
  
1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis **sélectionnez DNS**.
 
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste liste liste.":::
   
1. Sélectionnez **Ajouter** un enregistrement, puis sélectionnez la section **SPF (TXT).**
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. <br/>
    
    |**Type (Type)**|**Nom de l’hôte**|**Valeur**| **TTL** |
    |:-----|:-----|:-----|:-----|
    |SPF (TXT)  <br/> |(Laissez ce champ vide.)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte. | 1 heure |
  
1. Sélectionnez **Enregistrer**.<br/>!
  
## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversation, les appels de conférence et les appels vidéo, en plus de Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-two-additional-cname-records"></a>Ajouter deux enregistrements CNAME supplémentaires
  
1. Créez un autre sous-domaine (Lyncdiscover) en utilisant les instructions du premier enregistrement CNAME ci-dessus.
    
1. Dans la **zone Ajouter un sous-domaine** pour le nouveau sous-domaine, tapez ou copiez-collez uniquement la valeur Ajouter un sous-domaine du tableau suivant.  (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)<br/> 
    
    |**Ajouter un sous-domaine**|**Alias**|
    |:-----|:-----|
    |lyncdiscover   |webdir.online.lync.com  |
   
1. Sous **Actions** pour le **sous-domaine** de découverte automatique que vous venons de créer, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS** dans la liste. <br/>
    
1. Sélectionnez **Ajouter** un enregistrement, puis sélectionnez la section **CNAME.**

1. Dans la zone **Alias: (Alias :)**, tapez ou copiez-collez uniquement la valeur **Alias (Alias)** du tableau suivant. <br/>
    
    |**Create Subdomain (Créer un sous-domaine)**|**Alias**|
    |:-----|:-----|
    |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |
   
1. Cochez la case correspondant à la clause d'exclusion de responsabilité **J'accepte**, puis sélectionnez **Enregistrer**.
    
1. Créez un autre sous-domaine (SIP) : <br/>Sélectionnez **Ajouter un sous-domaine.**
    
1. Dans la **zone Ajouter un sous-domaine** pour le nouveau sous-domaine, tapez ou copiez-collez uniquement la valeur Ajouter un sous-domaine du tableau suivant.  (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.) <br/>
    
    |**Ajouter un sous-domaine**|**Alias**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |

1. Sous **Actions** pour le sous-domaine que vous venons de créer, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS** dans la liste liste liste. <br/>
    
1. Sélectionnez **Ajouter** un enregistrement, puis sélectionnez la section **CNAME.**

1. dans la **zone Alias:** , tapez ou copiez-collez uniquement la valeur **Alias** du tableau suivant. 
    
    |**Create Subdomain (Créer un sous-domaine)**|**Alias**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |
   
1. Cochez la case correspondant à la clause d'exclusion de responsabilité **J'accepte**, puis sélectionnez **Enregistrer**.

## <a name="add-the-two-srv-records-required-for-microsoft"></a>Ajouter les deux enregistrements SRV requis pour Microsoft
  
> [!NOTE]
> Si vous vous êtes inscrit auprès 1und1.de, [connectez-vous ici.](https://go.microsoft.com/fwlink/?linkid=859152) 
  
1. To get started, go to your domains page at IONOS by 1&1 by using [this link](https://my.1and1.com/). Vous serez invité à vous connecter.
    
1. Sélectionnez **Menu,** puis **sélectionnez Domaines et SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::
  
1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis **sélectionnez DNS**.
 
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste liste liste.":::
    
1. Sélectionnez **Ajouter** un enregistrement, puis sélectionnez la section **SRV.**
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. <br/>
    
    |**Type**|**Service**|**Protocol (Protocole)**|**Nom de l’hôte**|**Points to (Pointe vers)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV  <br/> |sip  <br/> |tls  <br/> |(Laissez ce champ vide.)  <br/> |sipdir.online.lync.com  <br/> |100  <br/> |1  <br/> |443  <br/> |3600 (1 h)  <br/> |
    |SRV  <br/> |sipfederationtls  <br/> |tcp  <br/> |(Laissez ce champ vide.)  <br/> |sipfed.online.lync.com  <br/> |100  <br/> |1  <br/> |5061  <br/> |3600 (1 h)  <br/> |  
  
1. Sélectionnez **Enregistrer**. <br/>
  
1. Ajoutez l’autre enregistrement SRV. 
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
    
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et gestion des périphériques mobiles pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. La gestion des périphériques mobiles nécessite 2 enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

> [!IMPORTANT]
> Suivez la procédure que vous avez utilisée pour les autres enregistrements CNAME et fournissez les valeurs du tableau suivant. 
  
|**Ajouter un sous-domaine**|**Alias**|
|:-----|:-----|
|enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |
|enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |
   

  
