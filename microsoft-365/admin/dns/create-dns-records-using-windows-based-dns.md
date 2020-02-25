---
title: Créer des enregistrements pour Office 365 à l'aide de DNS Windows
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9eec911d-5773-422c-9593-40e1147ffbde
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur le DNS Windows pour Office 365.
ms.openlocfilehash: ddea5cb95a7f2abef8b68b37de473f936ee08eb5
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42245028"
---
# <a name="create-dns-records-for-office-365-using-windows-based-dns"></a>Créer des enregistrements pour Office 365 à l'aide de DNS Windows

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
   
Si vous hébergez vos propres enregistrements DNS à l'aide du DNS Windows, suivez les étapes décrites dans cet article pour configurer vos enregistrements associés au courrier, à Skype Entreprise Online, etc.
  
Pour commencer, vous devez [Rechercher vos enregistrements DNS dans le DNS Windows afin de](#find-your-dns-records-in-windows-based-dns) pouvoir les mettre à jour. De plus, si vous envisagez de synchroniser votre annuaire Active Directory local avec Office 365, consultez [la rubrique adresse de messagerie non routable utilisée comme nom d’utilisateur principal dans votre local Active Directory](#non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory).
  
Problèmes de flux de messagerie ou autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique résolution des problèmes après avoir modifié votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="find-your-dns-records-in-windows-based-dns"></a>Rechercher vos enregistrements DNS dans un DNS Windows
<a name="BKMK_find_your_dns_1"></a> Accédez à la page qui contient les enregistrements DNS pour votre domaine. Si vous utilisez Windows Server 2008, accédez à **Démarrer** > l'**exécution**. Si vous utilisez Windows Server 2012, appuyez sur la touche Windows et sur **r**. Tapez **dnsmgmnt. msc**, puis cliquez sur **OK**. Dans le Gestionnaire DNS, développez ** \<le\> \> nom du serveur DNS zones de recherche directes  **. Sélectionnez votre domaine. Vous pouvez à présent créer les enregistrements DNS.
   
## <a name="add-mx-record"></a>Ajouter l'enregistrement MX
<a name="BKMK_add_MX"> </a>

Ajoutez un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365.
- L'enregistrement MX que vous ajouterez inclut une valeur ( **Pointe vers l'adresse**) qui ressemble à ceci : \<MX token\>.mail.protection.outlook.com, où \<MX token\> est une valeur telle que MSxxxxxxx. 
- À partir de la ligne MX de la section Exchange Online de la page Ajouter des enregistrements DNS dans Office 365, copiez la valeur figurant sous points à l’adresse. Vous utiliserez cette valeur dans l’enregistrement que vous créez dans cette tâche. 
- Sur la page Gestionnaire DNS du domaine, accédez à **action** > **Mail Exchanger (MX)**. Pour trouver cette page pour le domaine, voir [Rechercher vos enregistrements DNS dans le DNS Windows](#find-your-dns-records-in-windows-based-dns).  
- Dans la boîte de dialogue **nouvel enregistrement de ressource** , vérifiez que les champs sont définis sur les valeurs suivantes : 
    - Nom de l’hôte : 
    - @Address : collez ici la valeur de l’adresse de pointage que vous venez de copier depuis Office 365.  
    - Préférences 
- Sélectionnez **enregistrer les modifications**.
- Supprimez les enregistrements MX obsolètes. Si vous avez des anciens enregistrements MX pour ce domaine qui acheminent les messages ailleurs, activez la case à cocher en regard de chaque ancien enregistrement, puis sélectionnez **supprimer** > **OK**. 
   
## <a name="add-cname-records"></a>Ajouter les enregistrements CNAME
<a name="BKMK_add_CNAME"> </a>

Ajoutez les enregistrements CNAME requis pour Office 365. Si d'autres enregistrements CNAME sont répertoriés dans Office 365, ajoutez-les en suivant les mêmes étapes générales présentées ici.
  
> [!IMPORTANT]
> Si vous disposez de la gestion des appareils mobiles pour Office 365, vous devez créer deux enregistrements CNAMe supplémentaires. Follow the procedure that you used for the other four CNAME records, but supply the values from the following table. (Si vous ne disposez pas de MDM, vous pouvez ignorer cette étape.) 

- Sur la page du Gestionnaire DNS du domaine, accédez à l' **action** > **CNAME (CNAME)**.
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
   
### <a name="add-two-cname-records-for-mobile-device-management-mdm-for-office-365"></a>Ajouter deux enregistrements CNAME pour la gestion des appareils mobiles pour Office 365

> [!IMPORTANT]
> Si vous disposez de la gestion des appareils mobiles pour Office 365, vous devez créer deux enregistrements CNAMe supplémentaires. Follow the procedure that you used for the other four CNAME records, but supply the values from the following table. > (si vous n’avez pas MDM, vous pouvez ignorer cette étape.) 
  

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
   
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> You cannot have more than one TXT record for SPF for a domain. If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues. If you already have an SPF record for your domain, don't create a new one for Office 365. Ajoutez plutôt les valeurs Office 365 requises à l'enregistrement actuel de manière à n'avoir qu'un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
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

Ajoutez les 2 enregistrements SRV requis pour Office 365.

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

Avant d'ajouter les enregistrements DNS pour configurer vos services Office 365, Office 365 doit vérifier que vous êtes propriétaire du domaine que vous ajoutez. Pour ce faire, vous ajoutez un enregistrement, en suivant les étapes ci-dessous.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. 
  

1. Collectez les informations sur Office 365.  <br/> 
2. Dans le centre d’administration, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> . 
3. Dans la page **domaines** , dans la colonne **actions** du domaine que vous vérifiez, sélectionnez **Démarrer la configuration**. 
4. Sur la page **Ajouter un domaine à Office 365** , sélectionnez **Démarrer l’étape 1**. 
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
- Adresse : collez ici la valeur adresse de destination ou de pointage que vous venez de copier à partir d’Office 365.  
- Sélectionnez **OK** > **.**

Vérifiez votre domaine dans Office 365.  
> [!IMPORTANT]
> Patientez environ 15 minutes avant de le faire, afin que l’enregistrement que vous venez de créer puisse être mis à jour sur Internet.       

- Revenez à Office 365 et suivez les étapes ci-dessous pour demander une vérification. La vérification recherche l'enregistrement TXT que vous avez ajouté à l'étape précédente. Lorsqu'elle trouve l'enregistrement TXT correct, le domaine est vérifié.  
1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> **d’installation** \> .
2. Dans la page **domaines** , dans la colonne **action** du domaine que vous vérifiez, sélectionnez Démarrer la **configuration**. 
3. Dans la page **confirmer que vous êtes le propriétaire de votre domaine** , sélectionnez **terminé, vérifier maintenant**, puis, dans la boîte de dialogue de confirmation, sélectionnez **Terminer**. 
   
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory"></a>Adresse de courrier non routable utilisée en tant qu'UPN dans votre annuaire Active Directory local
<a name="BKMK_ADNote"> </a>

Si vous envisagez de synchroniser votre annuaire Active Directory local avec Office 365, vous souhaiterez vous assurer que le suffixe du nom d'utilisateur principal (UPN) Active Directory est un suffixe de domaine valide et non pas un suffixe de domaine qui n'est pas pris en charge tel que @contoso.local. Si vous devez modifier votre suffixe UPN, consultez [la rubrique How to prepare a non routable domain for Directory Synchronization](https://support.office.com/article/e7968303-c234-46c4-b8b0-b5c93c6d57a7).
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
