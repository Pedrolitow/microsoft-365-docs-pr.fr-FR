---
title: Connecter vos enregistrements DNS 123-reg.co.uk à Microsoft 365
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
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services sur 123-reg.co.uk microsoft.
ms.openlocfilehash: 98bbd9fa4963b24b08c417f608f7a0a3d8d84f31
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586927"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>Connecter vos enregistrements DNS 123-reg.co.uk à Microsoft 365

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si 123-reg.co.uk est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
Une fois ces enregistrements ajoutés 123-reg.co.uk, votre domaine est installé pour fonctionner avec services Microsoft. 
  
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. Sélectionnez **Domaines** et, dans la page Vue d’ensemble du nom de domaine, sélectionnez le nom du domaine que vous souhaitez vérifier. 
    
   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le domaine à vérifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés,** choisissez **Gérer DNS.**
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::
  
4. Dans la page Gérer votre DNS, sélectionnez **l’onglet DNS** avancé. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::
  
5. Dans la **zone Type** du nouvel enregistrement, choisissez **TXT/SPF** dans la liste de listes, puis tapez ou copiez-collez les autres valeurs du tableau suivant. 
    
    ||||
    |:-----|:-----|:-----|
    |**Hostname (Nom d'hôte)** <br/> |**Type (Type)** <br/> |**Destination TXT/SPF** <br/> |
    |@  <br/> |TXT/SPF  <br/> |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Sélectionnez le type TXT/SPF dans la liste de listes et remplissez les valeurs.":::
 
6. Sélectionnez **Ajouter**.
 
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Sélectionnez Ajouter.":::
   
   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
Maintenant que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous revenir à Microsoft et demander une recherche pour l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
Pour vérifier l’enregistrement dans Microsoft 365 :
  
1. Dans le Centre d’administration, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
    
1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer la configuration.** 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.
  
1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. On the Domain name overview page, select the name of the domain that you want to edit. 
    
   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine à modifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés,** choisissez **Gérer DNS.**
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::
  
4. Dans la page Gérer votre DNS, sélectionnez **l’onglet DNS** avancé. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::
    
5. Dans la **zone Type** du nouvel enregistrement, choisissez **MX** dans la liste, puis tapez ou copiez-collez les autres valeurs du tableau suivant. 
    
    |**Hostname (Nom d'hôte)**|**Type (Type)**|**Priority (Priorité)**|**Destination MX (Enregistrement MX de la destination)**|
    |:-----|:-----|:-----|:-----|
    |@  <br/> |MX  <br/> |1  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> | *\<domain-key\>*  .mail.protection.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> **Remarque :** Obtenez votre \<domain-key\> depuis votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
 
   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="Sélectionnez le type MX dans la liste liste et remplissez les valeurs.":::
 
6. Sélectionnez **Ajouter**.
 
   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="Sélectionnez Ajouter.":::
 
7. Si d'autres enregistrements MX sont répertoriés, supprimez-les individuellement en sélectionnant l'icône **Delete (Supprimer)** représentant une corbeille des enregistrements. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="Sélectionnez Supprimer (corbeille).":::
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. On the Domain name overview page, select the name of the domain that you want to edit. 
    
   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine à modifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés,** choisissez **Gérer DNS.**
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::
  
4. Dans la page Gérer votre DNS, sélectionnez **l’onglet DNS** avancé. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::
    
5. Ajoutez l’enregistrement CNAME.
    
    Dans la **zone Type** du nouvel enregistrement, choisissez **CNAME** dans la liste, puis tapez ou copiez-collez les autres valeurs du tableau suivant. 
    
    |**Hostname (Nom d'hôte)**|**Type (Type)**|**Destination CNAME (Enregistrement CNAME de la destination)**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |autodiscover.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
 
   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Sélectionnez le type CNAME dans la liste de listes et remplissez les valeurs.":::
 
6. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Sélectionnez Ajouter.":::
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, n’en créez pas de nouveau pour Microsfot. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](../../enterprise/external-domain-name-system-records.md). To validate your SPF record, you can use one of these [SPF validation tools](../setup/domains-faq.yml). 
  
1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. On the Domain name overview page, select the name of the domain that you want to edit. 
    
   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine à modifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés,** choisissez **Gérer DNS.**
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::
  
4. Dans la page Gérer votre DNS, sélectionnez **l’onglet DNS** avancé. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::
    
5. Dans la **zone Type** du nouvel enregistrement, choisissez **TXT/SPF** dans la liste de listes, puis tapez ou copiez-collez les autres valeurs du tableau suivant.
    
    |**Hostname (Nom d'hôte)**|**Type (Type)**|**Destination TXT/SPF**|
    |:-----|:-----|:-----|
    |@  <br/> |TXT/SPF  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Sélectionnez le type TXT/SPF dans la liste de listes et remplissez les valeurs.":::
  
6. Sélectionnez **Ajouter**.

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversation, les appels de conférence et les appels vidéo, en plus de Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.
    
2. On the Domain name overview page, select the name of the domain that you want to edit. 
    
   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine à modifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés,** choisissez **Gérer DNS.**
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::
  
4. Dans la page Gérer votre DNS, sélectionnez **l’onglet DNS** avancé. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::
    
5. Ajoutez le premier des deux enregistrements SRV :
    
   Dans la **zone Type** du nouvel enregistrement, choisissez **SRV** dans la liste, puis tapez ou copiez-collez les autres valeurs du tableau suivant.
    
    ||||||
    |:-----|:-----|:-----|:-----|:-----|
    |**Hostname (Nom d'hôte)**|**Type (Type)**|**Priorité**|**TTL**|**Destination SRV (Enregistrement SRV de la destination)**|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**<br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **Cette valeur DOIT se terminer par un point (.)** <br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Sélectionnez le type TXT/SPF dans la liste de listes et remplissez les valeurs.":::

6. Sélectionnez **Ajouter**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Sélectionnez Ajouter.":::

7. Ajoutez l’autre enregistrement SRV.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis 
    
1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.

1. On the Domain name overview page, select the name of the domain that you want to edit. 
    
   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine à modifier.":::

1. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés,** choisissez **Gérer DNS.**
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::
  
1. Dans la page Gérer votre DNS, sélectionnez **l’onglet DNS** avancé. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::
    
1. Ajoutez le premier enregistrement CNAME.
    
    Dans la **zone Type** du nouvel enregistrement, choisissez **CNAME** dans la liste, puis tapez ou copiez-collez les autres valeurs du tableau suivant.
    
    | **Hostname (Nom d'hôte)** |**Type (Type)**|**Destination CNAME (Enregistrement CNAME de la destination)**|
    |:-----|:-----|:-----|
    |sip  <br/>|CNAME  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |lyncdiscover  <br/>|CNAME  <br/> |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
 
   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Sélectionnez le type CNAME dans la liste de listes et remplissez les valeurs.":::
 
1. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Sélectionnez Ajouter.":::
  
1. Ajoutez l’autre enregistrement CNAME.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et gestion des périphériques mobiles pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. La gestion des périphériques mobiles nécessite deux enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.

1. On the Domain name overview page, select the name of the domain that you want to edit. 
    
   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine à modifier.":::

1. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés,** choisissez **Gérer DNS.**
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::
  
1. Dans la page Gérer votre DNS, sélectionnez **l’onglet DNS** avancé. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::
    
1. Ajoutez le premier enregistrement CNAME.
    
    Dans la **zone Type** du nouvel enregistrement, choisissez **CNAME** dans la liste, puis tapez ou copiez-collez les autres valeurs du tableau suivant.
    
   | **Hostname (Nom d'hôte)**|**Type (Type)**|**Destination CNAME (Enregistrement CNAME de la destination)**|
   |:-----|:-----|:-----|
   | enterpriseregistration <br/> | CNAME  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
   |enterpriseenrollment  <br/> | CNAME  <br/> |enterpriseenrollment.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Sélectionnez le type CNAME dans la liste de listes et remplissez les valeurs.":::

1. Sélectionnez **Ajouter**.
 
   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Sélectionnez Ajouter.":::
 
1. Ajoutez l’autre enregistrement CNAME.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
  
