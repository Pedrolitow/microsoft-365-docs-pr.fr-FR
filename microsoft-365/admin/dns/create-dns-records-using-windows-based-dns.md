---
title: Créer des enregistrements DNS pour Microsoft à l’aide du DNS basé sur Windows
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
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
ms.assetid: 9eec911d-5773-422c-9593-40e1147ffbde
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur le serveur DNS Windows pour Microsoft.
ms.openlocfilehash: f0c2b8c4aaaa1012e0f11e3778c7ca6b092c053f
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47306946"
---
# <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Créer des enregistrements DNS pour Microsoft à l’aide du DNS basé sur Windows

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
   
Si vous hébergez vos propres enregistrements DNS à l'aide du DNS Windows, suivez les étapes décrites dans cet article pour configurer vos enregistrements associés au courrier, à Skype Entreprise Online, etc.
  
Pour commencer, vous devez [Rechercher vos enregistrements DNS dans le DNS Windows afin de](#find-your-dns-records-in-windows-based-dns) pouvoir les mettre à jour. De plus, si vous envisagez de synchroniser votre annuaire Active Directory local avec Microsoft, consultez [la rubrique adresse de messagerie non routable utilisée comme nom d’utilisateur principal dans votre local Active Directory](#non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory).
  
Problèmes de flux de messagerie ou autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique résolution des problèmes après avoir modifié votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="find-your-dns-records-in-windows-based-dns"></a>Rechercher vos enregistrements DNS dans un DNS Windows
<a name="BKMK_find_your_dns_1"> </a> Accédez à la page qui contient les enregistrements DNS pour votre domaine. Si vous utilisez Windows Server 2008, accédez à démarrer l' **Start**  >  **exécution**. Si vous utilisez Windows Server 2012, appuyez sur la touche Windows et sur **r**. Tapez **dnsmgmnt. msc**, puis cliquez sur **OK**. Dans le Gestionnaire DNS, développez ** \<DNS server name\> \> zones de recherche directes  **. Sélectionnez votre domaine. Vous pouvez à présent créer les enregistrements DNS.
   
## <a name="add-mx-record"></a>Ajouter l'enregistrement MX
<a name="BKMK_add_MX"> </a>

Ajoutez un enregistrement MX afin que les messages électroniques pour votre domaine soient envoyés à Microsoft.
- L’enregistrement MX que vous ajoutez inclut une valeur ( **points à** la valeur de l’adresse) ressemblant à ceci : \<MX token\> . mail.protection.Outlook.com, où \<MX token\> est une valeur comme MSxxxxxxx. 
- À partir de la ligne MX de la section Exchange Online de la page Ajouter des enregistrements DNS de Microsoft, copiez la valeur figurant sous points à l’adresse. Vous utiliserez cette valeur dans l’enregistrement que vous créez dans cette tâche. 
- Sur la page Gestionnaire DNS du domaine, accédez à **action**  >  **Mail Exchanger (MX)**. Pour trouver cette page pour le domaine, voir [Rechercher vos enregistrements DNS dans le DNS Windows](#find-your-dns-records-in-windows-based-dns).  
- Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes : 
    - Nom de l’hôte :  
    - @Address : collez la valeur de pointage vers l’adresse que vous venez de copier à partir de Microsoft ici.  
    - Préférences 
- Sélectionnez **enregistrer les modifications**.
- Supprimez les enregistrements MX obsolètes. Si vous avez des anciens enregistrements MX pour ce domaine qui acheminent les messages ailleurs, activez la case à cocher en regard de chaque ancien enregistrement, puis sélectionnez **supprimer**  >  **OK**. 
   
## <a name="add-cname-records"></a>Ajouter les enregistrements CNAME
<a name="BKMK_add_CNAME"> </a>

Ajoutez les enregistrements CNAMe requis pour Microsoft. Si d’autres enregistrements CNAMe sont répertoriés dans Microsoft, ajoutez ceux-ci en suivant les mêmes étapes générales que celles indiquées ici.
  
> [!IMPORTANT]
> Si vous disposez de la gestion des appareils mobiles pour Microsoft, vous devez créer deux enregistrements CNAMe supplémentaires. Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. (Si vous ne disposez pas de MDM, vous pouvez ignorer cette étape.) 

- Sur la page du Gestionnaire DNS du domaine, accédez à l' **action**  >  **CNAME (CNAME)**.
- Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes :  
    - Nom de l’hôte : découverte automatique
    - Type : 
    - Cnameadresse : autodiscover.outlook.com
- Sélectionnez **O**K.

Ajoutez l'enregistrement CNAME SIP. 
- Sur la page du Gestionnaire DNS du domaine, accédez à l' **action** \> **CNAME (CNAME)**. 
- Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes :  
    - Nom de l’hôte : SIP
    - Type : CNAMe
    - Adresse : sipdir.online.lync.com
- Sélectionnez **OK**.

Ajoutez l'enregistrement de découverte automatique CNAME Skype Entreprise Online.  
- Sur la page du Gestionnaire DNS du domaine, accédez à l' **action** \> **CNAME (CNAME)**. Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes :  
    - Nom de l’hôte : lyncdiscover
    - Type : CNAMe
    - Adresse : webdir.online.lync.com
- Sélectionnez **OK**.
   
### <a name="add-two-cname-records-for-mobile-device-management-mdm-for-microsoft"></a>Ajouter deux enregistrements CNAMe pour la gestion des appareils mobiles (MDM) pour Microsoft

> [!IMPORTANT]
> Si vous disposez de la gestion des appareils mobiles pour Microsoft, vous devez créer deux enregistrements CNAMe supplémentaires. Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. > (si vous n’avez pas MDM, vous pouvez ignorer cette étape.) 
  

Ajoutez l'enregistrement CNAME Enterpriseregistration MDM.  
- Sur la page du Gestionnaire DNS du domaine, accédez à l' **action** \> **CNAME (CNAME)**. 
- Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes :  
- Nom de l’hôte : enterpriseregistration
- Type : CNAMe
- Adresse : enterpriseregistration.windows.net
- Sélectionnez **OK**. 

Ajoutez l'enregistrement CNAME Enterpriseenrollment MDM. 
-  Sur la page du Gestionnaire DNS du domaine, accédez à l' **action** \> **CNAME (CNAME)**. 
-  Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes :  
    - Nom de l’hôte : enterpriseenrollment
    - Type : CNAMe
    - Adresse : enterpriseenrollment-s.manage.microsoft.com
- Sélectionnez **OK**.
   
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de disposer d’un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
Ajoutez l'enregistrement TXT SPF pour votre domaine pour éviter le courrier indésirable.
  
- Vous disposez peut-être déjà d'autres chaînes dans la valeur TXT pour cet enregistrement (telles que les chaînes pour la courrier électronique publicitaire). Vous pouvez les conserver. Conservez ces chaînes et ajoutez celle-ci, en plaçant des guillemets autour de chaque chaîne pour les séparer. 
- Sur la page Gestionnaire DNS de votre domaine, accédez à texte de l' **action** \> **(txt)**. 
-  Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes. 
 > [!IMPORTANT]
> Dans certaines versions du Gestionnaire DNS Windows, le domaine a peut-être été configuré de sorte que lorsque vous créez un enregistrement txt, le nom d’origine par défaut est le domaine parent. Dans cette situation, lors de l'ajout d'un enregistrement TXT, définissez le nom d'hôte sur vide (sans valeur) au lieu de le définir sur @ ou sur le nom de domaine. 

-  Type d’hôte : @
-  Type d’enregistrement : TXT
-  Address : v = spf1 include include. protection. Outlook. com-All 
         
-  Sélectionnez **OK**.
   
## <a name="add-srv-records"></a>Ajouter les enregistrements SRV
<a name="BKMK_add_SRV"> </a>

Ajoutez les deux enregistrements SRV requis pour Microsoft.

Ajoutez l'enregistrement SRV SIP pour les conférences web Skype Entreprise Online.  <br/> 
-  Sur la page Gestionnaire DNS de votre domaine, accédez à **action** \> **autres nouveaux enregistrements**. 
-   Dans la fenêtre **type d’enregistrement de ressource** , sélectionnez emplacement du **service (SRV)**, puis sélectionnez **créer un enregistrement**. 
-   Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes :  
    -  Service : _sip
    -  Protocole : _tls
    -  Priorité : 100
    -  Poids : 1
    -  Port : 443
    -  Cible (nomhôte) : sipdir.online.lync.com
-  Sélectionnez **OK**. 


Ajoutez l'enregistrement SRV SIP pour la fédération Skype Entreprise Online.  
-  Sur la page Gestionnaire DNS de votre domaine, accédez à **action** \> **autres nouveaux enregistrements**.  
-  Dans la fenêtre **type d’enregistrement de ressource** , sélectionnez emplacement du **service (SRV)**, puis sélectionnez **créer un enregistrement**. 
-   Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes :  
    -  Service : _sipfederationtls
    -  Protocole : _tcp
    -  Priorité : 100
    -  Poids : 1
    -  Port : 5061
    -  Cible (nomhôte) : sipfed.online.lync.com
-  Sélectionnez **OK**. 
   
## <a name="add-a-record-to-verify-that-you-own-the-domain-if-you-havent-already"></a>Ajouter un enregistrement pour vérifier que vous êtes propriétaire du domaine, si ce n'est déjà fait
<a name="BKMK_verify"> </a>

Avant d’ajouter les enregistrements DNS pour configurer vos services Microsoft, Microsoft doit confirmer que vous êtes propriétaire du domaine que vous ajoutez. Pour ce faire, vous ajoutez un enregistrement, en suivant les étapes ci-dessous.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. 
  

1. Recueillez des informations auprès de Microsoft.  <br/> 
2. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>. 
3. Dans la page **domaines** , dans la colonne **actions** du domaine que vous vérifiez, sélectionnez **Démarrer la configuration**. 
4. Sur la page **Ajouter un domaine à Microsoft** , sélectionnez **Démarrer l’étape 1**. 
5. Dans la page **confirmer que vous êtes le propriétaire de votre domaine** , dans la liste déroulante **voir les instructions pour l’exécution de cette étape avec** , sélectionnez **instructions générales**. 
6. Dans le tableau, copiez la valeur Adresse de destination ou de pointage. Vous en aurez besoin au cours de l'étape suivante. Nous vous recommandons de copier et coller cette valeur, afin que l'espacement reste correct.

Ajoutez un enregistrement TXT. 
-  Sur la page Gestionnaire DNS de votre domaine, accédez à texte de l' **action** \> **(txt)**. 
-   Dans la boîte de dialogue **nouvel enregistrement de ressource** , sélectionnez **modifier**.  
-  Dans la zone **noms d’hôtes personnalisés** de la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes. 

> [!IMPORTANT] 
> Dans certaines versions du Gestionnaire DNS Windows, le domaine a peut-être été configuré de sorte que lorsque vous créez un enregistrement txt, le nom d’origine par défaut est le domaine parent. Dans cette situation, lors de l'ajout d'un enregistrement TXT, définissez le nom d'hôte sur vide (sans valeur) au lieu de le définir sur @ ou sur le nom de domaine. 

- Nom de l’hôte : @
- Type : TXT
- Adresse : collez la valeur adresse de destination ou de pointage que vous venez de copier à partir de Microsoft ici.  
- Sélectionnez **OK**  >  **Done**.

Vérifiez votre domaine dans Microsoft.  
> [!IMPORTANT]
> Patientez environ 15 minutes avant de le faire, afin que l’enregistrement que vous venez de créer puisse être mis à jour sur Internet.       

- Revenez à Microsoft et suivez les étapes ci-dessous pour demander un contrôle de vérification. La vérification recherche l'enregistrement TXT que vous avez ajouté à l'étape précédente. Lorsqu'elle trouve l'enregistrement TXT correct, le domaine est vérifié.  
1. Dans le centre d’administration, accédez à la page domaines **d’installation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domains</a> .
2. Dans la page **domaines** , dans la colonne **action** du domaine que vous vérifiez, sélectionnez Démarrer la **configuration**. 
3. Dans la page **confirmer que vous êtes le propriétaire de votre domaine** , sélectionnez **terminé, vérifier maintenant**, puis, dans la boîte de dialogue de confirmation, sélectionnez **Terminer**. 
   
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory"></a>Adresse de courrier non routable utilisée en tant qu'UPN dans votre annuaire Active Directory local
<a name="BKMK_ADNote"> </a>

Si vous envisagez de synchroniser votre annuaire Active Directory local avec Microsoft, vous devez vous assurer que le suffixe UPN (nom d’utilisateur principal) Active Directory est un suffixe de domaine valide et non pas un suffixe de domaine non pris en charge tel que @contoso. local. Si vous devez modifier votre suffixe UPN, consultez [la rubrique How to prepare a non routable domain for Directory Synchronization](https://docs.microsoft.com/microsoft-365/enterprise/prepare-a-non-routable-domain-for-directory-synchronization).
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
