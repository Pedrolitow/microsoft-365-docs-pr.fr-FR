---
title: Créer des enregistrements pour Microsoft à l'aide de DNS Windows
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9eec911d-5773-422c-9593-40e1147ffbde
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online et d’autres services sur Windows DNS basé sur Windows microsoft.
ms.openlocfilehash: 0349366e1cb3af23de1161a69b9b37305cc1237a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313480"
---
# <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Créer des enregistrements pour Microsoft à l'aide de DNS Windows

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
   
Si vous hébergez vos propres enregistrements DNS à l'aide du DNS Windows, suivez les étapes décrites dans cet article pour configurer vos enregistrements associés au courrier, à Skype Entreprise Online, etc.
  
Pour commencer, vous devez trouver vos enregistrements [DNS dans Windows DNS basé sur un système DNS](#find-your-dns-records-in-windows-based-dns) afin de pouvoir les mettre à jour. En outre, si vous envisagez de synchroniser votre annuaire Active Directory local avec Microsoft, consultez l’adresse de messagerie [non routable utilisée en tant qu’UPN dans active Directory](#non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory) local.
  
Trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="find-your-dns-records-in-windows-based-dns"></a>Rechercher vos enregistrements DNS dans un DNS Windows
<a name="BKMK_find_your_dns_1"> </a> Go to the page that has the DNS records for your domain. Si vous travaillez dans Windows Server 2008, allez à **StartRun** > . Si vous utilisez Windows Server 2012, appuyez sur la touche Windows et **r**. Tapez **dnsmgmnt.msc**, puis sélectionnez **OK**. Dans le Gestionnaire DNS, développez **zones\<DNS server name\>\> de recherche avant**. Sélectionnez votre domaine. Vous pouvez à présent créer les enregistrements DNS.
   
## <a name="add-mx-record"></a>Ajouter l'enregistrement MX
<a name="BKMK_add_MX"> </a>

Ajoutez un enregistrement MX afin que le courrier électronique de votre domaine soit envoyé à Microsoft.
- L’enregistrement MX que vous allez ajouter inclut une valeur  (la valeur d’adresse Points vers) \<MX token\>qui ressemble à ceci : .mail.protection.outlook.com, \<MX token\> où est une valeur comme MSxxxxxxx. 
- À partir de la ligne MX de la section Exchange Online de la page Ajouter des enregistrements DNS dans Microsoft, copiez la valeur répertoriée sous Adresse des points. Vous utiliserez cette valeur dans l’enregistrement que vous créez dans cette tâche. 
- Dans la page Gestionnaire DNS du domaine, sélectionnez **ActionMail** >  **Exchanger (MX).** Pour trouver cette page pour le domaine, voir Rechercher vos enregistrements [DNS dans Windows DNS basé sur un nom de domaine.](#find-your-dns-records-in-windows-based-dns)  
- Dans la **boîte de dialogue Nouvel enregistrement de** ressource, assurez-vous que les champs sont précisément les valeurs suivantes : 
    - Nom de l’hôte :  
    - @Address : collez la valeur d’adresse points que vous avez copiée ici à partir de Microsoft.  
    - Préf : 
- Sélectionnez **Enregistrer les modifications**.
- Supprimez les enregistrements MX obsolètes. Si vous avez d’anciens enregistrements MX pour ce domaine qui routent le courrier électronique ailleurs, cochez la case en regard de chaque ancien enregistrement, puis sélectionnez **DeleteOK** > . 
   
## <a name="add-cname-records"></a>Ajouter les enregistrements CNAME
<a name="BKMK_add_CNAME"> </a>

Ajoutez les enregistrements CNAME requis pour Microsoft. Si d’autres enregistrements CNAME sont répertoriés dans Microsoft, ajoutez-les en suivant les mêmes étapes générales que celles indiquées ici.
  
> [!IMPORTANT]
> Si vous avez la gestion des périphériques mobiles (MDM) pour Microsoft, vous devez créer deux enregistrements CNAME supplémentaires. Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. (Si vous n’avez pas de gestion des mdm, vous pouvez ignorer cette étape.) 

- Dans la page Gestionnaire DNS du domaine, sélectionnez **ActionCNAME** >  **(CNAME).**
- Dans la **boîte de dialogue Nouvel enregistrement de** ressource, assurez-vous que les champs sont précisément les valeurs suivantes :  
    - Nom d’hôte : découverte automatique
    - Type : 
    - CNAMEAddress : autodiscover.outlook.com
- **Sélectionnez OK**.

Ajoutez l'enregistrement CNAME SIP. 
- Dans la page Gestionnaire DNS du domaine, sélectionnez **Action** \> **CNAME (CNAME).** 
- Dans la **boîte de dialogue Nouvel enregistrement de** ressource, assurez-vous que les champs sont précisément les valeurs suivantes :  
    - Nom d’hôte : sip
    - Type : CNAME
    - Adresse : sipdir.online.lync.com
- Sélectionnez **OK**.

Ajoutez l'enregistrement de découverte automatique CNAME Skype Entreprise Online.  
- Dans la page Gestionnaire DNS du domaine, sélectionnez **Action** \> **CNAME (CNAME).** Dans la **boîte de dialogue Nouvel enregistrement de** ressource, assurez-vous que les champs sont précisément les valeurs suivantes :  
    - Nom d’hôte : lyncdiscover
    - Type : CNAME
    - Adresse : webdir.online.lync.com
- Sélectionnez **OK**.
   
### <a name="add-two-cname-records-for-mobile-device-management-mdm-for-microsoft"></a>Ajouter deux enregistrements CNAME pour la gestion des périphériques mobiles (MDM) pour Microsoft

> [!IMPORTANT]
> Si vous avez la gestion des périphériques mobiles (MDM) pour Microsoft, vous devez créer deux enregistrements CNAME supplémentaires. Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. >(Si vous n’avez pas de gestion des mdm, vous pouvez ignorer cette étape.) 
  

Ajoutez l'enregistrement CNAME Enterpriseregistration MDM.  
- Dans la page Gestionnaire DNS du domaine, sélectionnez **Action** \> **CNAME (CNAME).** 
- Dans la **boîte de dialogue Nouvel enregistrement de** ressource, assurez-vous que les champs sont précisément les valeurs suivantes :  
- Nom d’hôte : enterpriseregistration
- Type : CNAME
- Adresse : enterpriseregistration.windows.net
- Sélectionnez **OK**. 

Ajoutez l'enregistrement CNAME Enterpriseenrollment MDM. 
-  Dans la page Gestionnaire DNS du domaine, sélectionnez **Action** \> **CNAME (CNAME).** 
-  Dans la **boîte de dialogue Nouvel enregistrement de** ressource, assurez-vous que les champs sont précisément les valeurs suivantes :  
    - Nom d’hôte : enterpriseenrollment
    - Type : CNAME
    - Adresse : enterpriseenrollment-s.manage.microsoft.com
- Sélectionnez **OK**.
   
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. 
  
Ajoutez l'enregistrement TXT SPF pour votre domaine pour éviter le courrier indésirable.
  
- Vous disposez peut-être déjà d'autres chaînes dans la valeur TXT pour cet enregistrement (telles que les chaînes pour la courrier électronique publicitaire). Vous pouvez les conserver. Conservez ces chaînes et ajoutez celle-ci, en plaçant des guillemets autour de chaque chaîne pour les séparer. 
- Dans la page Gestionnaire DNS de votre domaine, sélectionnez **Texte de l’action** \> **(TXT).** 
-  Dans la **boîte de dialogue Nouvel enregistrement de** ressource, assurez-vous que les champs sont précisément les valeurs suivantes. 
 > [!IMPORTANT]
> Dans certaines versions du Gestionnaire DNS Windows, le domaine a peut-être été mis en place de sorte que lorsque vous créez un enregistrement txt, le nom d’accueil se définisse par défaut sur le domaine parent. Dans cette situation, lors de l'ajout d'un enregistrement TXT, définissez le nom d'hôte sur vide (sans valeur) au lieu de le définir sur @ ou sur le nom de domaine. 

-  Type d’hôte : @
-  Type d’enregistrement : TXT
-  Adresse : v=spf1 include:spf.protection.outlook.com -all 
         
-  Sélectionnez **OK**.
   
## <a name="add-srv-records"></a>Ajouter les enregistrements SRV
<a name="BKMK_add_SRV"> </a>

Ajoutez les deux enregistrements SRV requis pour Microsoft.

Ajoutez l'enregistrement SRV SIP pour les conférences web Skype Entreprise Online.  <br/> 
-  Dans la page Gestionnaire DNS de votre domaine, sélectionnez **Action** \> **Autres nouveaux enregistrements**. 
-   Dans la **fenêtre Type d’enregistrement** de ressource, sélectionnez **Emplacement du service (SRV),** puis **sélectionnez Créer un enregistrement**. 
-   Dans la **boîte de dialogue Nouvel enregistrement de** ressource, assurez-vous que les champs sont précisément les valeurs suivantes :  
    -  Service : _sip
    -  Protocole : _tls
    -  Priorité : 100
    -  Poids : 1
    -  Port : 443
    -  Cible (nom d’hôte) : sipdir.online.lync.com
-  Sélectionnez **OK**. 


Ajoutez l'enregistrement SRV SIP pour la fédération Skype Entreprise Online.  
-  Dans la page Gestionnaire DNS de votre domaine, sélectionnez **Action** \> **Autres nouveaux enregistrements**.  
-  Dans la **fenêtre Type d’enregistrement** de ressource, sélectionnez **Emplacement du service (SRV),** puis **sélectionnez Créer un enregistrement**. 
-   Dans la **boîte de dialogue Nouvel enregistrement de** ressource, assurez-vous que les champs sont précisément les valeurs suivantes :  
    -  Service : _sipfederationtls
    -  Protocole : _tcp
    -  Priorité : 100
    -  Poids : 1
    -  Port : 5061
    -  Cible (nom d’hôte) : sipfed.online.lync.com
-  Sélectionnez **OK**. 
   
## <a name="add-a-record-to-verify-that-you-own-the-domain-if-you-havent-already"></a>Ajouter un enregistrement pour vérifier que vous êtes propriétaire du domaine, si ce n'est déjà fait
<a name="BKMK_verify"> </a>

Avant d’ajouter les enregistrements DNS pour configurer votre services Microsoft, Microsoft doit confirmer que vous êtes propriétaire du domaine que vous ajoutez. Pour ce faire, vous ajoutez un enregistrement, en suivant les étapes ci-dessous.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. 
  

1. Recueillir des informations de Microsoft.  <br/> 
2. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>. 
3. Dans la page **Domaines** , dans la colonne **Actions** du domaine que vous vérifiez, sélectionnez **Démarrer la configuration**. 
4. Dans la page **Ajouter un domaine à Microsoft** , sélectionnez **Démarrer l’étape 1**. 
5. On the **Confirm that you own your domain** page, in the **See instructions for performing this step with** drop-down list, choose **General instructions**. 
6. Dans le tableau, copiez la valeur Adresse de destination ou de pointage. Vous en aurez besoin au cours de l'étape suivante. Nous vous recommandons de copier et coller cette valeur, afin que l'espacement reste correct.

Ajoutez un enregistrement TXT. 
-  Dans la page Gestionnaire DNS de votre domaine, sélectionnez **Texte de l’action** \> **(TXT).** 
-   Dans la **boîte de dialogue Nouvel enregistrement de** ressource, sélectionnez **Modifier**.  
-  Dans la **zone Noms d’hôte** personnalisés de la boîte de dialogue Nouvel enregistrement de ressource, assurez-vous que les champs sont définies sur les valeurs suivantes. 

> [!IMPORTANT] 
> Dans certaines versions du Gestionnaire DNS Windows, le domaine a peut-être été mis en place de sorte que lorsque vous créez un enregistrement txt, le nom d’accueil se définisse par défaut sur le domaine parent. Dans cette situation, lors de l'ajout d'un enregistrement TXT, définissez le nom d'hôte sur vide (sans valeur) au lieu de le définir sur @ ou sur le nom de domaine. 

- Nom d’hôte : @
- Type : TXT
- Adresse : collez la valeur Destination ou Pointe vers l’adresse que vous avez copiée ici à partir de Microsoft.  
- **Sélectionnez OKDone** > .

Vérifiez votre domaine dans Microsoft.  
> [!IMPORTANT]
> Patientez environ 15 minutes avant de le faire, afin que l’enregistrement que vous venons de créer puisse être mis à jour sur Internet.       

- Revenir à Microsoft et suivez les étapes ci-dessous pour demander une vérification. La vérification recherche l'enregistrement TXT que vous avez ajouté à l'étape précédente. Lorsqu'elle trouve l'enregistrement TXT correct, le domaine est vérifié.  
1. Dans le centre d’administration, allez à la page **Domaines** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">d’installation</a> .
2. Dans la page **Domaines** , dans la colonne **Action** du domaine que vous vérifiez, sélectionnez **Démarrer la configuration**. 
3. Dans la page **Confirmer que vous** êtes propriétaire de votre domaine, sélectionnez Terminé **, vérifiez** maintenant, puis, dans la boîte de dialogue de confirmation, sélectionnez **Terminer**. 
   
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory"></a>Adresse de courrier non routable utilisée en tant qu'UPN dans votre annuaire Active Directory local
<a name="BKMK_ADNote"> </a>

Si vous envisagez de synchroniser votre annuaire Active Directory local avec Microsoft, vous devez vous assurer que le suffixe du nom d’utilisateur principal (UPN) Active Directory est un suffixe de domaine valide, et non un suffixe de domaine non pris en compte tel que @contoso.local. Si vous devez modifier votre suffixe UPN, voir Comment préparer un domaine [non routable pour la synchronisation d’annuaires](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md).
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="related-content"></a>Contenu associé

[Transférer un domaine de Microsoft 365 vers un autre hôte](../get-help-with-domains/transfer-a-domain-from-microsoft-to-another-host.md) (article)\
[Pilote Microsoft 365 à partir de mon domaine personnalisé](../misc/pilot-microsoft-365-from-my-custom-domain.md) (article)\
[FAQ sur les domaines](../setup/domains-faq.yml) (article)