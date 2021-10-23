---
title: Connecter vos enregistrements DNS sur Wix to Microsoft 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services via Wix pour Microsoft.
ms.openlocfilehash: ba5b814278c601c6fd6e9599075d4e297b87db58
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60556744"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>Connecter vos enregistrements DNS sur Wix to Microsoft 365

**[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Wix est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

Une fois ces enregistrements ajoutés sur Wix, votre domaine est installé pour fonctionner avec services Microsoft.
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
 
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 

> [!NOTE]
> WIX ne prend pas en charge les entrées DNS pour les sous-domaine.
  
1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
2. Sélectionnez   >  **Domaines...**, puis gérez les enregistrements **DNS** dans la liste de listes. 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::
    
3. Sélectionnez **+ Ajouter un enregistrement** dans la ligne **TXT (texte)** de l’éditeur DNS. 
    
4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. 
    
   ||||
   |:-----|:-----|:-----|
   | **Nom d’hôte **<br/> | **VALEUR TXT** <br/> | **TTL** <br/> |
   |Rempli automatiquement (laisser vide)  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 heure <br/> |          |
   
5. Sélectionnez **Enregistrer.** 
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié. 

Pour vérifier l’enregistrement dans Microsoft 365 :
  
1. Dans le Centre d’administration, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
    
2. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer la configuration.**   
  
3. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
1. Sélectionnez   >  **Domaines...**, puis gérez les enregistrements **DNS** dans la liste de listes. 
    
   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

1. Sous **MX (échange de courrier),** **sélectionnez Modifier les enregistrements MX.** 

1. Choose **Other** from the drop-down list, and select **+ Add record**.
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
   | **Host Name** | **Points to (Pointe vers)** | **Priorité** | **TTL** |
   |:-----|:-----|:-----|:-----|
   |Rempli automatiquement <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenez votre *\<domain-key\>* depuis votre compte Microsoft.   [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). | 1 heure|
   
1. Si d’autres enregistrements MX sont répertoriés, supprimez chacun d’eux. 
    
6. Sélectionnez **Enregistrer**.
    
## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
2. Sélectionnez   >  **Domaines...**, puis gérez les enregistrements **DNS** dans la liste de listes. 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

3. Sélectionnez **+ Ajoutez-en** une autre dans la ligne **CNAME (Alias)** de l’éditeur DNS pour l’enregistrement CNAME. 
    
4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
   | **Host Name (Nom d'hôte)** | **Valeur** | **TTL** |
   |:-----|:-----|:-----|
   |autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 heure  <br/> |
   
5. Sélectionnez **Enregistrer**. 
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs.  
  
1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
2. Sélectionnez   >  **Domaines...**, puis gérez les enregistrements **DNS** dans la liste de listes. 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::
    
3. Sélectionnez **+ Ajouter un enregistrement** dans la ligne **TXT (texte)** de l’éditeur DNS. 

   **Remarque**: Wix fournit une ligne SPF dans l’éditeur DNS. Ignorez cette ligne et utilisez la **ligne TXT (Texte)** pour entrer les valeurs SPF ci-dessous. 
    
4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :
    
   | **Host Name (Nom d'hôte)** | **Valeur** | **TTL** |
   |:-----|:-----|:-----|
   |[laissez ce vide]  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.<br/> | 1 Hour |
   
5. Sélectionnez **Enregistrer**. 
    
6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversation, les appels de conférence et les appels vidéo, en plus de Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
1. Sélectionnez   >  **Domaines...**, puis gérez les enregistrements **DNS** dans la liste de listes. 
 
   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::
   
1. Sélectionnez **+ Ajouter un enregistrement** dans la ligne **SRV** de l’éditeur DNS. 
 
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau :
    
   | **Service** | **Protocol (Protocole)** | **Name (Nom)** | **Weight (Poids)** | **Port (Port)** | **Target (Cible)** | **Priorité** | **TTL** |
   |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
   |sip  |tls  |Rempli automatiquement |1  |443   |sipdir.online.lync.com |100 |1 Hour |
   |sipfed|tcp |Rempli automatiquement|1 |5061 |sipfed.online.lync.com|100 | 1 Hour |
   
1. Sélectionnez **Enregistrer**. 
  
1. Ajoutez l’autre enregistrement SRV en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis 

1. Sélectionnez **+ Ajoutez-en** une autre dans la ligne **CNAME (Alias)** de l’éditeur DNS, puis entrez les valeurs de la première ligne du tableau suivant. 
    
   |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
   |:-----|:-----|:-----|:-----|
   |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1 heure  <br/> |
   |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1 Hour  <br/> |
  
1. Sélectionnez **Enregistrer**.
  
1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et gestion des périphériques mobiles pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. La gestion des périphériques mobiles nécessite deux enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.
    
2. Sélectionnez   >  **Domaines...**, puis gérez les enregistrements **DNS** dans la liste de listes. 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

3. Sélectionnez **+ Ajoutez-en** une autre dans la ligne **CNAME (Alias)** de l’éditeur DNS, puis entrez les valeurs de la première ligne du tableau suivant. 
    
    |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1 heure  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1 Hour  <br/> |
  
1. Sélectionnez **Enregistrer**.
  
1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
  
