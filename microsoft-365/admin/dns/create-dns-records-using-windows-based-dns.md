---
title: Créer des enregistrements pour Microsoft à l'aide de DNS Windows
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
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
description: Apprenez à vérifier votre domaine et à configurer des enregistrements DNS pour les e-mails, Skype Entreprise Online et d’autres services dans DNS windows pour Microsoft.
ms.openlocfilehash: 8a72bb2a6620f5eb52153c8d4c237a2733b21fcd
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68206936"
---
# <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Créer des enregistrements pour Microsoft à l'aide de DNS Windows

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
   
Si vous hébergez vos propres enregistrements DNS à l'aide du DNS Windows, suivez les étapes décrites dans cet article pour configurer vos enregistrements associés au courrier, à Skype Entreprise Online, etc.
  
Pour commencer, vous devez [rechercher vos enregistrements DNS dans DNS basé sur Windows](#find-your-dns-records-in-windows-based-dns) afin de pouvoir les mettre à jour. En outre, si vous envisagez de synchroniser votre Active Directory local avec Microsoft, consultez [l’adresse e-mail non routable utilisée en tant qu’UPN dans votre annuaire Active Directory local](#non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory).
  
Problèmes liés au flux de courrier ou à d’autres problèmes après l’ajout d’enregistrements DNS. Consultez [Résolution des problèmes après la modification de votre nom de domaine ou de vos enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="find-your-dns-records-in-windows-based-dns"></a>Rechercher vos enregistrements DNS dans un DNS Windows
<a name="BKMK_find_your_dns_1"> </a> Accédez à la page qui contient les enregistrements DNS de votre domaine. Si vous travaillez dans Windows Server 2008, accédez à **Démarrer** > **l’exécution**. Si vous utilisez Windows Server 2012, appuyez sur la touche Windows et **r**. Tapez **dnsmgmnt.msc**, puis sélectionnez **OK**. Dans le Gestionnaire DNS, **développez\<DNS server name\>\> Zones de recherche avancée**. Sélectionnez votre domaine. Vous pouvez à présent créer les enregistrements DNS.
   
## <a name="add-mx-record"></a>Ajouter l'enregistrement MX
<a name="BKMK_add_MX"> </a>

Ajoutez un enregistrement MX pour que le courrier électronique de votre domaine soit envoyé à Microsoft.
- L’enregistrement MX que vous allez ajouter inclut une valeur (la valeur **points à adresse** ) qui ressemble à ceci : \<MX token\>.mail.protection.outlook.com, où \<MX token\> se trouve une valeur comme MSxxxxxxxxx. 
- À partir de la ligne MX de la section Exchange Online de la page Ajouter des enregistrements DNS dans Microsoft, copiez la valeur répertoriée sous Points to address. Vous allez utiliser cette valeur dans l’enregistrement que vous créez dans cette tâche. 
- Dans la page Gestionnaire DNS du domaine, accédez à **Action** > **Mail Exchanger (MX).** Pour trouver cette page pour le domaine, consultez [Rechercher vos enregistrements DNS dans DNS basé sur Windows](#find-your-dns-records-in-windows-based-dns).  
- Dans la boîte **de dialogue Nouvel enregistrement de ressource** , vérifiez que les champs sont définis avec précision sur les valeurs suivantes : 
    - Nom d’hôte : 
    - @Address : collez les points pour la valeur d’adresse que vous venez de copier à partir de Microsoft ici.  
    - Pref: 
- Sélectionnez **Enregistrer les modifications**.
- Supprimez les enregistrements MX obsolètes. Si vous avez d’anciens enregistrements MX pour ce domaine qui routent l’e-mail ailleurs, activez la case à cocher en regard de chaque ancien enregistrement, puis **sélectionnez Supprimer** > **OK**. 
   
## <a name="add-cname-records"></a>Ajouter les enregistrements CNAME
<a name="BKMK_add_CNAME"> </a>

Ajoutez les enregistrements CNAME requis pour Microsoft. Si des enregistrements CNAME supplémentaires sont répertoriés dans Microsoft, ajoutez ceux qui suivent les mêmes étapes générales que celles présentées ici.
  
> [!IMPORTANT]
> Si vous avez Mobile Gestion des appareils (MDM) pour Microsoft, vous devez créer deux enregistrements CNAME supplémentaires. Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. (Si vous n’avez pas de GPM, vous pouvez ignorer cette étape.) 

- Dans la page Gestionnaire DNS du domaine, accédez à **Action** > **CNAME (CNAME).**
- Dans la boîte **de dialogue Nouvel enregistrement de ressource** , vérifiez que les champs sont définis avec précision sur les valeurs suivantes :  
    - Nom d’hôte : découverte automatique
    - Type : 
    - CNAMEAddress : autodiscover.outlook.com
- Sélectionnez **O** K.

Ajoutez l'enregistrement CNAME SIP. 
- Dans la page Gestionnaire DNS du domaine, accédez à **Action** \> **CNAME (CNAME).** 
- Dans la boîte **de dialogue Nouvel enregistrement de ressource** , vérifiez que les champs sont définis avec précision sur les valeurs suivantes :  
    - Nom d’hôte : sip
    - Type : CNAME
    - Adresse : sipdir.online.lync.com
- Sélectionnez **OK**.

Ajoutez l'enregistrement de découverte automatique CNAME Skype Entreprise Online.  
- Dans la page Gestionnaire DNS du domaine, accédez à **Action** \> **CNAME (CNAME).** Dans la boîte **de dialogue Nouvel enregistrement de ressource** , vérifiez que les champs sont définis avec précision sur les valeurs suivantes :  
    - Nom d’hôte : lyncdiscover
    - Type : CNAME
    - Adresse : webdir.online.lync.com
- Sélectionnez **OK**.
   
### <a name="add-two-cname-records-for-mobile-device-management-mdm-for-microsoft"></a>Ajouter deux enregistrements CNAME pour Mobile Gestion des appareils (MDM) pour Microsoft

> [!IMPORTANT]
> Si vous avez Mobile Gestion des appareils (MDM) pour Microsoft, vous devez créer deux enregistrements CNAME supplémentaires. Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. >(Si vous n’avez pas de GPM, vous pouvez ignorer cette étape.) 
  

Ajoutez l'enregistrement CNAME Enterpriseregistration MDM.  
- Dans la page Gestionnaire DNS du domaine, accédez à **Action** \> **CNAME (CNAME).** 
- Dans la boîte **de dialogue Nouvel enregistrement de ressource** , vérifiez que les champs sont définis avec précision sur les valeurs suivantes :  
- Nom d’hôte : enterpriseregistration
- Type : CNAME
- Adresse : enterpriseregistration.windows.net
- Sélectionnez **OK**. 

Ajoutez l'enregistrement CNAME Enterpriseenrollment MDM. 
-  Dans la page Gestionnaire DNS du domaine, accédez à **Action** \> **CNAME (CNAME).** 
-  Dans la boîte **de dialogue Nouvel enregistrement de ressource** , vérifiez que les champs sont définis avec précision sur les valeurs suivantes :  
    - Nom d’hôte : enterpriseenrollment
    - Type : CNAME
    - Adresse : enterpriseenrollment-s.manage.microsoft.com
- Sélectionnez **OK**.
   
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. 
  
Ajoutez l'enregistrement TXT SPF pour votre domaine pour éviter le courrier indésirable.
  
- You might already have other strings in the TXT value for this record (such as strings for marketing email), which is fine. Leave those strings in place and add this one, placing double-quotes around each string to separate them. 
- Dans la page Gestionnaire DNS de votre domaine, accédez à Texte **d’action** \> **(TXT).** 
-  Dans la boîte **de dialogue Nouvel enregistrement de ressource** , vérifiez que les champs sont définis avec précision sur les valeurs suivantes. 
 > [!IMPORTANT]
> Dans certaines versions de Windows DNS Manager, le domaine a peut-être été configuré de sorte que lorsque vous créez un enregistrement txt, le nom d’accueil est défini par défaut sur le domaine parent. Dans cette situation, lors de l'ajout d'un enregistrement TXT, définissez le nom d'hôte sur vide (sans valeur) au lieu de le définir sur @ ou sur le nom de domaine. 

-  Type d’hôte : @
-  Type d’enregistrement : TXT
-  Adresse : v=spf1 include:spf.protection.outlook.com -all 
         
-  Sélectionnez **OK**.
   
## <a name="add-srv-records"></a>Ajouter les enregistrements SRV
<a name="BKMK_add_SRV"> </a>

Ajoutez les deux enregistrements SRV requis pour Microsoft.

Ajoutez l'enregistrement SRV SIP pour les conférences web Skype Entreprise Online.  <br/> 
-  Dans la page Gestionnaire DNS de votre domaine, accédez à **Action** \> **Other New Records**. 
-   Dans la fenêtre **Type d’enregistrement** de ressource, sélectionnez **L’emplacement du service (SRV),** puis **sélectionnez Créer un enregistrement**. 
-   Dans la boîte **de dialogue Nouvel enregistrement de ressource** , vérifiez que les champs sont définis avec précision sur les valeurs suivantes :  
    -  Service : _sip
    -  Protocole : _tls
    -  Priorité : 100
    -  Poids : 1
    -  Port : 443
    -  Cible (nom d’hôte) : sipdir.online.lync.com
-  Sélectionnez **OK**. 


Ajoutez l'enregistrement SRV SIP pour la fédération Skype Entreprise Online.  
-  Dans la page Gestionnaire DNS de votre domaine, accédez à **Action** \> **Other New Records**.  
-  Dans la fenêtre **Type d’enregistrement** de ressource, sélectionnez **L’emplacement du service (SRV),** puis **sélectionnez Créer un enregistrement**. 
-   Dans la boîte **de dialogue Nouvel enregistrement de ressource** , vérifiez que les champs sont définis avec précision sur les valeurs suivantes :  
    -  Service : _sipfederationtls
    -  Protocole : _tcp
    -  Priorité : 100
    -  Poids : 1
    -  Port : 5061
    -  Cible (nom d’hôte) : sipfed.online.lync.com
-  Sélectionnez **OK**. 
   
## <a name="add-a-record-to-verify-that-you-own-the-domain-if-you-havent-already"></a>Ajouter un enregistrement pour vérifier que vous êtes propriétaire du domaine, si ce n'est déjà fait
<a name="BKMK_verify"> </a>

Avant d’ajouter les enregistrements DNS pour configurer vos services Microsoft, Microsoft doit confirmer que vous êtes propriétaire du domaine que vous ajoutez. Pour ce faire, vous ajoutez un enregistrement, en suivant les étapes ci-dessous.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine, il n’a pas d’autre fonction. 
  

1. Collectez des informations auprès de Microsoft.  <br/> 
2. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>. 
3. Dans la page **Domaines** , dans la colonne **Actions** du domaine que vous vérifiez, **sélectionnez Démarrer l’installation**. 
4. Dans la page **Ajouter un domaine à Microsoft** , **sélectionnez Démarrer l’étape 1**. 
5. Dans la page **Confirmer que vous êtes propriétaire de votre domaine** , dans les **instructions voir pour effectuer cette étape avec** la liste déroulante, choisissez **Instructions générales**. 
6. Dans le tableau, copiez la valeur Adresse de destination ou de pointage. Vous en aurez besoin au cours de l'étape suivante. Nous vous recommandons de copier et coller cette valeur, afin que l'espacement reste correct.

Ajoutez un enregistrement TXT. 
-  Dans la page Gestionnaire DNS de votre domaine, accédez à Texte **d’action** \> **(TXT).** 
-   Dans la boîte **de dialogue Nouvel enregistrement de ressource** , **sélectionnez Modifier**.  
-  Dans la zone **Noms d’hôte personnalisés** de la boîte de dialogue **Nouvel enregistrement de ressource** , assurez-vous que les champs sont définis avec précision sur les valeurs suivantes. 

> [!IMPORTANT] 
> Dans certaines versions de Windows DNS Manager, le domaine a peut-être été configuré de sorte que lorsque vous créez un enregistrement txt, le nom d’accueil est défini par défaut sur le domaine parent. Dans cette situation, lors de l'ajout d'un enregistrement TXT, définissez le nom d'hôte sur vide (sans valeur) au lieu de le définir sur @ ou sur le nom de domaine. 

- Nom d’hôte : @
- Type : TXT
- Adresse : collez ici la valeur Destination ou Points to Address que vous venez de copier à partir de Microsoft.  
- Sélectionnez **OK** > **Terminé**.

Vérifiez votre domaine dans Microsoft.  
> [!IMPORTANT]
> Attendez environ 15 minutes avant de procéder ainsi, afin que l’enregistrement que vous venez de créer puisse être mis à jour sur Internet.       

- Retour à Microsoft et suivez les étapes ci-dessous pour demander une vérification de vérification. La vérification recherche l'enregistrement TXT que vous avez ajouté à l'étape précédente. Lorsqu'elle trouve l'enregistrement TXT correct, le domaine est vérifié.  
1. Dans le Centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a> **d’installation**\>.
2. Dans la page **Domaines** , dans la colonne **Action** du domaine que vous vérifiez, **sélectionnez Démarrer l’installation**. 
3. Dans la page **Confirmer que vous êtes propriétaire de votre domaine** , sélectionnez **Terminé, Vérifiez maintenant**, puis dans la boîte de dialogue de confirmation, **sélectionnez Terminer**. 
   
> [!NOTE]
>  Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory"></a>Adresse de courrier non routable utilisée en tant qu'UPN dans votre annuaire Active Directory local
<a name="BKMK_ADNote"> </a>

Si vous envisagez de synchroniser votre Active Directory local avec Microsoft, vous devez vous assurer que le suffixe de nom d’utilisateur principal (UPN) Active Directory est un suffixe de domaine valide et non un suffixe de domaine non pris en charge tel que @contoso.local. Si vous devez modifier votre suffixe UPN, consultez [Comment préparer un domaine non routable pour la synchronisation d’annuaires](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md).
  
> [!NOTE]
>  Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="related-content"></a>Contenu associé

[Transférer un domaine de Micrsoft 365 vers un autre hôte](../get-help-with-domains/transfer-a-domain-from-microsoft-to-another-host.md) (article)\
[Pilote Microsoft 365 à partir de mon domaine personnalisé](../misc/pilot-microsoft-365-from-my-custom-domain.md) (article)\
[FAQ sur les domaines](../setup/domains-faq.yml) (article)