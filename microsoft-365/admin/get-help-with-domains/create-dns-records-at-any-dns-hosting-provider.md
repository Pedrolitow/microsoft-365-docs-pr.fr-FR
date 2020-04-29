---
title: Créer des enregistrements DNS auprès d'un fournisseur d'hébergement DNS
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 7b7b075d-79f9-4e37-8a9e-fb60c1d95166
description: Apprenez à vérifier votre domaine et à créer des enregistrements DNS auprès d’un fournisseur d'hébergement DNS pour Microsoft 365.
ms.custom: okr_smb
ms.openlocfilehash: c727092c153e43369d5ed52d71bfcd256878db4b
ms.sourcegitcommit: 2399ee6f9bc955cf8f2a76c01fc84c19eb37ff42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2020
ms.locfileid: "43919504"
---
# <a name="create-dns-records-at-any-dns-hosting-provider"></a>Créer des enregistrements DNS auprès d'un fournisseur d'hébergement DNS

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Consultez notre liste d’[instructions spécifiques selon l’hôte](https://support.office.com/article/ae950c9e-e8d9-4108-b0cb-449156998580) pour rechercher votre hôte et suivre les étapes d’ajout des enregistrements dont vous avez besoin. 
  
Si vous ne connaissez pas le fournisseur d'hébergement DNS ou le bureau d'enregistrement pour votre domaine, voir [Rechercher mon bureau d'enregistrement de domaines ou mon fournisseur d'hébergement DNS](../get-help-with-domains/find-your-domain-registrar.md).
  
Pour configurer les enregistrements vous-même, vous devez ajouter les enregistrements suivants. Notez que vos enregistrement de vérification et enregistrement MX sont spécifiques à votre domaine. Pour les configurer, vous devez obtenir et utiliser une valeur de « jeton » spécifique pour votre domaine. Les étapes suivantes vous expliquent comment procéder.
  
> [!IMPORTANT]
> Le nom exact des zones ou  *champs*  dans lesquels vous entrez ou collez les informations pour créer chaque type d'enregistrement DNS est différent pour chaque hôte DNS. Votre hôte DNS peut éventuellement proposer une section d'aide sur son site web pour vous aider à mapper les instructions affichées ici aux champs exacts sur son site web. N'oubliez pas de vérifier si nous avons publié des instructions détaillées applicables à votre hôte DNS dans la rubrique [Créer des enregistrements DNS pour Microsoft 365](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23.aspx). >  Certains hôtes DNS ne vous permettent pas de créer tous les types d'enregistrements requis, ce qui entraîne des [limitations du service](https://support.office.com/article/7ae9a655-041d-4724-aa92-60392ee390c2.aspx) dans Microsoft 365. Si l'hôte de votre domaine ne prend pas en charge les enregistrements SRV, TXT ou CNAME, par exemple, nous vous recommandons de [transférer votre domaine](../get-help-with-domains/buy-a-domain-name.md) à un hôte DNS qui prend en charge tous les enregistrements requis. Pour utiliser un processus rapide et automatisé de configuration avec Microsoft 365, transférez votre domaine vers GoDaddy. 
  
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement quelques minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de courrier ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Rechercher et corriger les problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-or-mx-record-for-verification"></a>Ajouter un enregistrement TXT ou MX à des fins de vérification
<a name="BKMK_verify"> </a>

> [!NOTE]
> Vous ne devez créer qu'un seul des deux enregistrements. TXT est le type d'enregistrement préféré, mais certains fournisseurs d'hébergement DNS ne le prennent pas en charge, auquel cas vous pouvez créer un enregistrement MX à la place. 
  
Avant que vous puissiez utiliser votre domaine avec Microsoft 365, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft 365 que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
 **Trouvez la zone sur le site web de votre fournisseur d'hébergement DNS dans laquelle créer un enregistrement.**
  
1. Connectez-vous sur le site web de votre fournisseur d'hébergement DNS.
    
2. Choisissez votre domaine.
    
3. Recherchez la page dans laquelle vous pouvez modifier les enregistrements DNS pour votre domaine.
    
 **Créez l’enregistrement.**
  
1. Selon que vous créez un enregistrement TXT ou un enregistrement MX, effectuez l’une des opérations suivantes :
    
   - **Si vous créez un enregistrement TXT, utilisez les valeurs suivantes :**
    
      |||||
      |:-----|:-----|:-----|:-----|
      |**Type d’enregistrement**|**Alias** ou **nom d’hôte**|**Valeur**|**TTL**|
      |TXT|Effectuez l'une des opérations suivantes : Tapez **@**, laissez le champ vide ou entrez le nom de votre domaine.  <br/> **Remarque :** les conditions requises pour ce champ ne sont pas identiques pour tous les hôtes DNS. |MS=ms *XXXXXXXX*  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Microsoft 365.  <br/>        [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)     <br/>     |Définissez cette valeur sur **1 heure** ou sur l'équivalent en minutes ( **60** ), en secondes ( **3600** ), etc.  |
   
   - **Si vous créez un enregistrement MX, utilisez les valeurs suivantes :**
    
      ||||||
      |:-----|:-----|:-----|:-----|:-----|
      |**Type d’enregistrement**|**Alias** ou **nom d’hôte**|**Valeur**|**Priorité**|**TTL**|
      |MX|Entrez soit **@**, soit votre nom de domaine. |MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365.    <br/>       [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)     <br/>     |Pour **Priorité**, afin d’éviter les conflits avec l’enregistrement MX utilisé pour le flux de courrier électronique, utilisez une priorité plus basse que la priorité des enregistrements MX existants. <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> |Définissez cette valeur sur **1 heure** ou sur l'équivalent en minutes ( **60** ), en secondes ( **3600** ), etc. |
   
2. Enregistrez l'enregistrement.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Microsoft 365 et demandez à Microsoft 365 de rechercher l’enregistrement.
  
Lorsque Microsoft 365 trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
  
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
       
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.   
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-mx-record-to-route-email"></a>Ajouter un enregistrement MX pour acheminer le courrier électronique
<a name="BKMK_add_MX"> </a>

Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft 365.  *Lorsque vous mettez à jour l’enregistrement MX de votre domaine, tout nouveau message électronique adressé à une personne utilisant votre domaine mène désormais vers Microsoft 365*. Un courrier électronique que vous avez déjà reste chez votre hôte de courrier actuel, sauf si vous décidez de [migrer les courriers électroniques et contacts vers Microsoft 365.](../setup/migrate-email-and-contacts-admin.md)

 **Tâche**
  
Trouver la page sur laquelle vous pouvez créer les enregistrements pour votre domaine.
  
1. Connectez-vous sur le site web de votre hôte DNS.
    
2. Choisissez votre domaine.
    
3. Recherchez la page dans laquelle vous pouvez modifier les enregistrements DNS pour votre domaine.
    
::: moniker range="o365-worldwide"

  L'enregistrement MX que vous ajouterez inclut une valeur ( **Pointe vers l'adresse**) qui ressemble à ceci : \<MX token\>.mail.protection.outlook.com, où \<MX token\> est une valeur telle que MSxxxxxxx. 

::: moniker-end

::: moniker range="o365-germany"

  L'enregistrement MX que vous ajoutez inclut une valeur ( **Pointe vers l'adresse**) qui ressemble à ceci : \<Jeton MX\>.mail.protection.outlook.de, où \<Jeton MX\> est une valeur telle que MSxxxxxxx.   

::: moniker-end

4. Sur le site web de votre hôte DNS, ajouter un nouvel enregistrement MX.
    
    Vous allez maintenant [récupérer les informations relatives à l’enregistrement MX](../get-help-with-domains/information-for-dns-records.md) auprès de Microsoft 365. 
    
5. Pour l’enregistrement MX (cf. l’étape ci-dessus), copiez la valeur **Pointe vers l’adresse**. 
    
    Vous allez utiliser cette valeur dans l’enregistrement que vous créez sur le site de votre hôte DNS, comme décrit dans l’étape suivante.
    
6. Dans le nouvel enregistrement MX sur le site de votre hôte DNS, vérifiez que les champs sont définis sur les valeurs suivantes :
    
   - **Record Type (Type d’enregistrement)**  : **MX**
    
   - **Priorité** : définissez la priorité de l’enregistrement MX sur la valeur la plus élevée disponible (généralement **0**).
    
      Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx).
    
   - **Nom de l’hôte**: **@**
    
   - **Pointe vers l’adresse** : collez la valeur **Pointe vers l’adresse** que vous venez de copier à partir de Microsoft 365 ici. 
    
   - **TTL** : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. 
    
7. Enregistrez l'enregistrement.
    
Supprimez les autres enregistrements MX.
  
Si des enregistrements MX associés à ce domaine envoient des courriers électroniques à un emplacement autre que Microsoft 365, supprimez-les tous.
  
## <a name="add-three-cname-records"></a>Ajouter trois enregistrements CNAME
<a name="BKMK_add_MX"> </a>

::: moniker range="o365-worldwide"

Procédez comme suit pour ajouter les trois enregistrements CNAME requis pour Microsoft 365. Si d'autres enregistrements CNAME sont répertoriés dans Microsoft 365, ajoutez ceux-ci en suivant les mêmes étapes générales que celles affichées ici.
  
Sur le site web de votre hôte DNS, vous devez créer trois nouveaux enregistrements CNAME, généralement l'un à la suite de l'autre.
  
1. Dans les zones de chaque nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. Après avoir ajouté les trois premiers enregistrements, choisissez de créer un autre enregistrement CNAME.
    
      |||||
      |:-----|:-----|:-----|:-----|
      |**Record Type (Type d’enregistrement)** <br/> |**Host (Hôte)** <br/> |**Points to (Destination)** <br/> |**TTL (Durée de vie)** <br/> |
      |CNAME (Alias)  <br/> |autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 heure  <br/> |
      |CNAME (Alias)  <br/> |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |1 heure  <br/> |
      |CNAME (Alias)  <br/> |sip  <br/> |sipdir.online.lync.com  <br/> |1 heure  <br/> |
   
   > [!NOTE]
   > Pour **TTL** : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. > Ces enregistrements ne s’appliquent pas aux déploiements hybrides Exchange, Lync ou Skype Entreprise. 
  
2. Lorsque vous avez terminé, enregistrez les enregistrements.
    
::: moniker-end
::: moniker range="o365-germany"

Procédez comme suit pour ajouter les trois enregistrements CNAME requis pour Microsoft 365. Si d'autres enregistrements CNAME sont répertoriés dans Microsoft 365, ajoutez ceux-ci en suivant les mêmes étapes générales que celles affichées ici.
  
Sur le site web de votre hôte DNS, vous devez créer trois nouveaux enregistrements CNAME, généralement l'un à la suite de l'autre.
  
1. Dans les zones de chaque nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. Après avoir ajouté les trois premiers enregistrements, choisissez de créer un autre enregistrement CNAME.
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Record Type (Type d’enregistrement)** <br/> |**Host (Hôte)** <br/> |**Points to (Destination)** <br/> |**TTL (Durée de vie)** <br/> |
    |CNAME (Alias)  <br/> |autodiscover  <br/> |autodiscover-outlook.office.de  <br/> |1 heure  <br/> |
    |CNAME (Alias)  <br/> |lyncdiscover  <br/> |webdir.online.skype.de  <br/> |1 heure  <br/> |
    |CNAME (Alias)  <br/> |sip  <br/> |sipdir.online.lync.de  <br/> |1 heure  <br/> |
   
     > [!NOTE]
     > Pour **TTL** : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. > Ces enregistrements ne s’appliquent pas aux déploiements hybrides Exchange, Lync ou Skype Entreprise. 
  
2. Lorsque vous avez terminé, enregistrez les enregistrements.
    
::: moniker-end

::: moniker range="o365-21vianet"

Procédez comme suit pour ajouter les trois enregistrements CNAME requis pour Microsoft 365. Si d'autres enregistrements CNAME sont répertoriés dans Microsoft 365, ajoutez ceux-ci en suivant les mêmes étapes générales que celles affichées ici.
  
Sur le site web de votre hôte DNS, vous devez créer trois nouveaux enregistrements CNAME, généralement l'un à la suite de l'autre.
  
1. Dans les zones de chaque nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. Après avoir ajouté les trois premiers enregistrements, choisissez de créer un autre enregistrement CNAME.
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Record Type (Type d’enregistrement)** <br/> |**Host (Hôte)** <br/> |**Points to (Destination)** <br/> |**TTL (Durée de vie)** <br/> |
    |CNAME (Alias)  <br/> |autodiscover  <br/> |autodiscover.partner.outlook.cn  <br/> |1 heure  <br/> |
    |CNAME (Alias)  <br/> |lyncdiscover  <br/> |webdir.online.partner.lync.cn  <br/> |1 heure  <br/> |
    |CNAME (Alias)  <br/> |sip  <br/> |sipdir.online.partner.lync.cn  <br/> |1 heure  <br/> |
   
     > [!NOTE]
     > Pour **TTL** : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. > Ces enregistrements ne s’appliquent pas aux déploiements hybrides Exchange, Lync ou Skype Entreprise. 
  
2. Lorsque vous avez terminé, enregistrez les enregistrements.
    
::: moniker-end

## <a name="add-two-cname-records-for-mobile-device-management-mdm-for-microsoft-365"></a>Ajouter deux enregistrements CNAME pour la gestion des appareils mobiles (MDM) pour Microsoft 365
<a name="BKMK_add_MX"> </a>

::: moniker range="o365-worldwide"

> [!IMPORTANT]
> Si vous avez la gestion des appareils mobiles (MDM) pour Microsoft 365, vous devez créer deux autres enregistrements CNAME. Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. > (Si vous n’avez pas MDM, vous pouvez ignorer cette étape.) 
  
   |||||
   |:-----|:-----|:-----|:-----|
   |**Type d’enregistrement** <br/> |**Host (Hôte)** <br/> |**Points to (Destination)** <br/> |**TTL (Durée de vie)** <br/> |
   |CNAME (Alias)  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |1 heure  <br/> |
   |CNAME (Alias)  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment.manage.microsoft.com  <br/> |1 heure  <br/> |
   
::: moniker-end

::: moniker range="o365-germany"

> [!IMPORTANT]
> Si vous avez la gestion des appareils mobiles (MDM) pour Microsoft 365, vous devez créer deux autres enregistrements CNAME. Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez les valeurs du tableau suivant. > (Si vous n’avez pas MDM, vous pouvez ignorer cette étape.) 
  
   |||||
   |:-----|:-----|:-----|:-----|
   |**Type d’enregistrement** <br/> |**Host (Hôte)** <br/> |**Points to (Destination)** <br/> |**TTL (Durée de vie)** <br/> |
   |CNAME (Alias)  <br/> |enterpriseregistration  <br/> |enterpriseregistration.microsoftonline.de  <br/> |1 heure  <br/> |
   |CNAME (Alias)  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |1 heure  <br/> |
   
::: moniker-end

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_MX"> </a>

::: moniker range="o365-worldwide"

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft 365. Ajoutez plutôt les valeurs Microsoft 365 requises à l’enregistrement actuel de manière à n’avoir qu’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs.
  
Sur le site web de votre hôte DNS, modifiez l'enregistrement SPF existant ou créez un enregistrement TXT pour SPF.
  
> [!IMPORTANT]
> SPF est conçu pour lutter contre l’usurpation d’adresse, mais il existe des techniques d’usurpation d’adresse contre lesquelles SPF ne peut rien faire. Pour vous protéger contre ces techniques, une fois que vous avez configuré SPF, vous devez également configurer DKIM et DMARC pour Microsoft 365. Pour commencer, consultez la rubrique [Utilisation de DKIM pour valider les e-mails sortants envoyés à partir de votre domaine dans Microsoft 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Ensuite, consultez la rubrique [Utiliser DMARC pour valider les e-mails dans Microsoft 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx). 
  
1. Dans les zones du nouvel enregistrement, entrez ou copiez-collez l’ensemble de valeurs ci-dessous qui s’applique à votre cas.
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Type d’enregistrement** <br/> |**Hôte** <br/> |**VALEUR TXT** <br/> |**TTL** <br/> |
    |TXT (texte)  <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |1 heure  <br/> |
   
    Pour **TTL (Durée de vie)**  : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. 
    
2. Lorsque vous avez terminé, enregistrez l’enregistrement.
    
3. Pour valider votre enregistrement SPF, utilisez l'un des [outils de validation SPF](https://docs.microsoft.com/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain) suivants

::: moniker-end

::: moniker range="o365-germany"

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft 365. Ajoutez plutôt les valeurs Microsoft 365 requises à l’enregistrement actuel de manière à n’avoir qu’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
Sur le site web de votre hôte DNS, modifiez l'enregistrement SPF existant ou créez un enregistrement TXT pour SPF.
  
> [!IMPORTANT]
> SPF est conçu pour lutter contre l’usurpation d’adresse, mais il existe des techniques d’usurpation d’adresse contre lesquelles SPF ne peut rien faire. Pour vous protéger contre ces techniques, une fois que vous avez configuré SPF, vous devez également configurer DKIM et DMARC pour Microsoft 365. Pour commencer, consultez la rubrique [Utilisation de DKIM pour valider les e-mails sortants envoyés à partir de votre domaine dans Microsoft 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Ensuite, consultez la rubrique [Utiliser DMARC pour valider les e-mails dans Microsoft 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx). 
  
1. Dans les zones du nouvel enregistrement, entrez ou copiez-collez l’ensemble de valeurs ci-dessous qui s’applique à votre cas.
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Type d’enregistrement**|**Hôte**|**VALEUR TXT**|**TTL**|
    |TXT (texte)|@|v=spf1 include:spf.protection.outlook.de -all <br/>  Nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |1 heure|
   
    Pour **TTL (Durée de vie)**  : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. 
    
2. Lorsque vous avez terminé, enregistrez l’enregistrement.
    
3. Pour valider votre enregistrement SPF, utilisez l'un des [outils de validation SPF](https://docs.microsoft.com/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain) suivants
    
::: moniker-end

::: moniker range="o365-21vianet"

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft 365. Ajoutez plutôt les valeurs Microsoft 365 requises à l’enregistrement actuel de manière à n’avoir qu’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs. 
  
Sur le site web de votre hôte DNS, modifiez l'enregistrement SPF existant ou créez un enregistrement TXT pour SPF.
  
> [!IMPORTANT]
> SPF est conçu pour lutter contre l’usurpation d’adresse, mais il existe des techniques d’usurpation d’adresse contre lesquelles SPF ne peut rien faire. Pour vous protéger contre ces techniques, une fois que vous avez configuré SPF, vous devez également configurer DKIM et DMARC pour Microsoft 365. Pour commencer, consultez la rubrique [Utilisation de DKIM pour valider les e-mails sortants envoyés à partir de votre domaine dans Microsoft 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Ensuite, consultez la rubrique [Utiliser DMARC pour valider les e-mails dans Microsoft 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx). 
  
1. Dans les zones du nouvel enregistrement, entrez ou copiez-collez l’ensemble de valeurs ci-dessous qui s’applique à votre cas.
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**Type d’enregistrement**|**Hôte**|**VALEUR TXT**|**TTL**|
    |TXT (texte)|@|v=spf1 include:spf.protection.partner.outlook.cn -all> [!NOTE]> Nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |1 heure|
   
    Pour **TTL (Durée de vie)**  : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. 
    
2. Lorsque vous avez terminé, enregistrez l’enregistrement.
    
3. Pour valider votre enregistrement SPF, utilisez l'un des [outils de validation SPF](https://docs.microsoft.com/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain) suivants
    
::: moniker-end

## <a name="add-two-srv-records"></a>Ajouter deux enregistrements SRV
<a name="BKMK_add_MX"> </a>

::: moniker range="o365-worldwide"

Sur le site web de votre hôte DNS, vous devez créer deux enregistrements SRV, généralement l'un à la suite de l'autre. En d'autres termes, après avoir ajouté le premier enregistrement SRV auprès du site web, choisissez de créer un autre enregistrement SRV.
  
1. Dans les zones de chaque nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. **(Voir les notes ci-dessous sur la création d'enregistrements SRV lorsque votre hôte DNS ne dispose pas de tous ces éléments dans des champs distincts.)**
    
    ||||||||||
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |**Type d’enregistrement** <br/> |**Name (Nom)** <br/> |**Target (Cible)** <br/> |**Protocol (Protocole)** <br/> |**Service (Service)** <br/> |**Priority (Priorité)** <br/> |**Weight (Poids)** <br/> |**Port (Port)** <br/> |**TTL (Durée de vie)** <br/> |
    |SRV (Service)  <br/> |@  <br/> (Ou laissez le champ vide, si la valeur @ n’est pas autorisée)  <br/> |sipdir.online.lync.com  <br/> |_tls  <br/> |_sip  <br/> |100  <br/> |1  <br/> |443  <br/> |1 heure  <br/> |
    |SRV (Service)  <br/> |@  <br/> (Ou laissez le champ vide, si la valeur @ n’est pas autorisée)  <br/> |sipfed.online.lync.com  <br/> |_tcp  <br/> |_sipfederationtls  <br/> |100  <br/> |1  <br/> |5061  <br/> |1 heure  <br/> |
   
    > [!NOTE]
    >  Pour **Name (Nom)**  : si votre hôte DNS n’autorise pas la définition de la valeur de ce paramètre sur **@**, laissez ce champ vide. Utilisez cette approche *uniquement* lorsque votre hôte DNS utilise des champs distincts pour les valeurs Service et Protocole. Dans le cas contraire, consultez les notes sur les valeurs Service et Protocole ci-dessous. 
    > 
    >  Pour les valeurs **Service (Service)** et **Protocol (Protocole)** : si votre hôte DNS ne fournit pas ces champs pour les enregistrements SRV, vous devez spécifier les valeurs **Service (Service)** et **Protocol (Protocole)** comme valeur **Name (Nom)** de l’enregistrement. (Remarque : suivant votre hôte DNS, le champ **Name (Nom)** peut avoir une autre appellation, comme : **Host (Hôte)**, **Hostname (Nom d’hôte)** ou **Subdomain (Sous-domaine)**). Pour configurer la valeur combinée, vous devez créer une seule chaîne, en séparant les valeurs par un point.  Par exemple : **Nom** : _sip._tls 
    > 
    >  Pour les valeurs **Priority (Priorité)**, **Weight (Poids)** et **Port (Port)** : si votre hôte DNS ne fournit pas ces champs pour les enregistrements SRV, vous devez les spécifier comme valeur **Target (Cible)** de l’enregistrement. (Remarque : suivant votre hôte DNS, le champ **Target (Cible)** peut avoir une autre appellation, comme : **Content (Contenu)**, **IP Address (Adresse IP)** ou **Target Host (Hôte cible)**). Pour configurer la valeur combinée, vous devez créer une seule chaîne, en séparant les valeurs par un point. Les valeurs doivent être incluses dans l’ordre suivant : Priority (Priorité), Weight (Poids), Port (Port), Target (Cible). Par exemple : **Target (Cible)**  : 100 1 443 sipdir.online.lync.com. 
    > 
    >  Variation pour **Priority (Priorité)**, **Weight (Poids)** et **Port (Port)**  : certains hôtes DNS fournissent une partie, mais pas l’ensemble des champs requis séparément. Pour ces sites d’hôte DNS, spécifiez les valeurs qui ne sont pas affichées séparément sous forme d’une chaîne combinée, dans l’ordre, pour la valeur **Target (Cible)** de l’enregistrement. (Remarque : suivant votre hôte DNS, le champ **Target (Cible)** peut avoir une autre appellation, comme : **Content (Contenu)**, **IP Address (Adresse IP)** ou **Target Host (Hôte cible)**). Pour configurer la valeur combinée, vous créez une seule chaîne pour les champs qui n’apparaissent pas individuellement, en séparant les valeurs par des espaces. Les valeurs doivent être incluses *dans l’ordre*, en laissant les valeurs ayant des champs distincts disponibles : Priority (Priorité), Weight (Poids), Port (Port), Target (Cible). Par exemple, lorsque la priorité comporte un champ distinct, concaténez uniquement les valeurs Weight (Poids), Port (Port) et Target (Cible) : **Target (Cible)**  : 1 443 sipdir.online.lync.com 
    > 
    > Pour **TTL (Durée de vie)**  : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. 
  
2. Lorsque vous avez terminé, enregistrez les enregistrements.
    
    > [!NOTE]
    >  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
::: moniker-end


::: moniker range="o365-germany"

Sur le site web de votre hôte DNS, vous devez créer deux enregistrements SRV, généralement l'un à la suite de l'autre. En d'autres termes, après avoir ajouté le premier enregistrement SRV auprès du site web, choisissez de créer un autre enregistrement SRV.
  
1. Dans les zones de chaque nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. **(Voir les notes ci-dessous sur la création d'enregistrements SRV lorsque votre hôte DNS ne dispose pas de tous ces éléments dans des champs distincts.)**
    
    ||||||||||
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |**Type d’enregistrement** <br/> |**Name (Nom)** <br/> |**Target (Cible)** <br/> |**Protocol (Protocole)** <br/> |**Service (Service)** <br/> |**Priority (Priorité)** <br/> |**Weight (Poids)** <br/> |**Port (Port)** <br/> |**TTL (Durée de vie)** <br/> |
    |SRV (Service)  <br/> |@  <br/> (Ou laissez le champ vide, si la valeur @ n’est pas autorisée)  <br/> |sipdir.online.lync.de  <br/> |_tls  <br/> |_sip  <br/> |100  <br/> |1  <br/> |443  <br/> |1 heure  <br/> |
    |SRV (Service)  <br/> |@  <br/> (Ou laissez le champ vide, si la valeur @ n’est pas autorisée)  <br/> |sipfed.online.lync.de  <br/> |_tcp  <br/> |_sipfederationtls  <br/> |100  <br/> |1  <br/> |5061  <br/> |1 heure  <br/> |
   
    > [!NOTE]
    >  Pour **Name (Nom)**  : si votre hôte DNS n’autorise pas la définition de la valeur de ce paramètre sur **@**, laissez ce champ vide. Utilisez cette approche *uniquement* lorsque votre hôte DNS utilise des champs distincts pour les valeurs Service et Protocole. Dans le cas contraire, consultez les notes sur les valeurs Service et Protocole ci-dessous. 
    > 
    >  Pour les valeurs **Service (Service)** et **Protocol (Protocole)** : si votre hôte DNS ne fournit pas ces champs pour les enregistrements SRV, vous devez spécifier les valeurs **Service (Service)** et **Protocol (Protocole)** comme valeur **Name (Nom)** de l’enregistrement. (Remarque : suivant votre hôte DNS, le champ **Name (Nom)** peut avoir une autre appellation, comme : **Host (Hôte)**, **Hostname (Nom d’hôte)** ou **Subdomain (Sous-domaine)**). Pour configurer la valeur combinée, vous devez créer une seule chaîne, en séparant les valeurs par un point. >  Par exemple : **Name (Nom)** : _sip._tls 
    > 
    >  Pour les valeurs **Priority (Priorité)**, **Weight (Poids)** et **Port (Port)** : si votre hôte DNS ne fournit pas ces champs pour les enregistrements SRV, vous devez les spécifier comme valeur **Target (Cible)** de l’enregistrement. (Remarque : suivant votre hôte DNS, le champ **Target (Cible)** peut avoir une autre appellation, comme : **Content (Contenu)**, **IP Address (Adresse IP)** ou **Target Host (Hôte cible)**). Pour configurer la valeur combinée, vous devez créer une seule chaîne, en séparant les valeurs par un point. Les valeurs doivent être incluses dans l’ordre suivant : Priority (Priorité), Weight (Poids), Port (Port), Target (Cible). >  Par exemple : **Target (Cible)**  : 100 1 443 sipdir.online.lync.de. 
    > 
    >  Variation pour **Priority (Priorité)**, **Weight (Poids)** et **Port (Port)**  : certains hôtes DNS fournissent une partie, mais pas l’ensemble des champs requis séparément. Pour ces sites d’hôte DNS, spécifiez les valeurs qui ne sont pas affichées séparément sous forme d’une chaîne combinée, dans l’ordre, pour la valeur **Target (Cible)** de l’enregistrement. (Remarque : suivant votre hôte DNS, le champ **Target (Cible)** peut avoir une autre appellation, comme : **Content (Contenu)**, **IP Address (Adresse IP)** ou **Target Host (Hôte cible)**). Pour configurer la valeur combinée, vous créez une seule chaîne pour les champs qui n’apparaissent pas individuellement, en séparant les valeurs par des espaces. Les valeurs doivent être incluses *dans l’ordre*, en laissant les valeurs ayant des champs distincts disponibles : Priority (Priorité), Weight (Poids), Port (Port), Target (Cible). >  Par exemple, lorsque la valeur Priority (Priorité) comporte un champ distinct, concaténez uniquement les valeurs Weight (Poids), Port (Port) et Target (Cible) : **Target (Cible)**  : 1 443 sipdir.online.lync.de 
    > 
    >  Pour **TTL (Durée de vie)**  : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. 
  
2. Lorsque vous avez terminé, enregistrez les enregistrements.
    
    > [!NOTE]
    >  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
::: moniker-end


::: moniker range="o365-21vianet"

Sur le site web de votre hôte DNS, vous devez créer deux enregistrements SRV, généralement l'un à la suite de l'autre. En d'autres termes, après avoir ajouté le premier enregistrement SRV auprès du site web, choisissez de créer un autre enregistrement SRV.
  
1. Dans les zones de chaque nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. **(Voir les notes ci-dessous sur la création d'enregistrements SRV lorsque votre hôte DNS ne dispose pas de tous ces éléments dans des champs distincts.)**
    
    ||||||||||
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |**Type d’enregistrement** <br/> |**Name (Nom)** <br/> |**Target (Cible)** <br/> |**Protocol (Protocole)** <br/> |**Service (Service)** <br/> |**Priority (Priorité)** <br/> |**Weight (Poids)** <br/> |**Port (Port)** <br/> |**TTL (Durée de vie)** <br/> |
    |SRV (Service)  <br/> |@  <br/> (Ou laissez le champ vide, si la valeur @ n’est pas autorisée)  <br/> |sipdir.online.partner.lync.cn  <br/> |_tls  <br/> |_sip  <br/> |100  <br/> |1  <br/> |443  <br/> |1 heure  <br/> |
    |SRV (Service)  <br/> |@  <br/> (Ou laissez le champ vide, si la valeur @ n’est pas autorisée)  <br/> |sipfed.online.partner.lync.cn  <br/> |_tcp  <br/> |_sipfederationtls  <br/> |100  <br/> |1  <br/> |5061  <br/> |1 heure  <br/> |
   
    > [!NOTE]
    >  Pour **Name (Nom)**  : si votre hôte DNS n’autorise pas la définition de la valeur de ce paramètre sur **@**, laissez ce champ vide. Utilisez cette approche *uniquement* lorsque votre hôte DNS utilise des champs distincts pour les valeurs Service et Protocole. Dans le cas contraire, consultez les notes sur les valeurs Service et Protocole ci-dessous. 
    > 
    >  Pour les valeurs **Service (Service)** et **Protocol (Protocole)** : si votre hôte DNS ne fournit pas ces champs pour les enregistrements SRV, vous devez spécifier les valeurs **Service (Service)** et **Protocol (Protocole)** comme valeur **Name (Nom)** de l’enregistrement. (Remarque : suivant votre hôte DNS, le champ **Name (Nom)** peut avoir une autre appellation, comme : **Host (Hôte)**, **Hostname (Nom d’hôte)** ou **Subdomain (Sous-domaine)**). Pour configurer la valeur combinée, vous devez créer une seule chaîne, en séparant les valeurs par un point. >  Par exemple : **Name (Nom)** : _sip._tls 
    > 
    >  Pour les valeurs **Priority (Priorité)**, **Weight (Poids)** et **Port (Port)** : si votre hôte DNS ne fournit pas ces champs pour les enregistrements SRV, vous devez les spécifier comme valeur **Target (Cible)** de l’enregistrement. (Remarque : suivant votre hôte DNS, le champ **Target (Cible)** peut avoir une autre appellation, comme : **Content (Contenu)**, **IP Address (Adresse IP)** ou **Target Host (Hôte cible)**). Pour configurer la valeur combinée, vous devez créer une seule chaîne, en séparant les valeurs par un point. Les valeurs doivent être incluses dans l’ordre suivant : Priority (Priorité), Weight (Poids), Port (Port), Target (Cible). >  Par exemple : **Target (Cible)**: 100 1 443 sipdir.online.partner.lync.cn. 
    > 
    >  Variation pour **Priority (Priorité)**, **Weight (Poids)** et **Port (Port)**  : certains hôtes DNS fournissent une partie, mais pas l’ensemble des champs requis séparément. Pour ces sites d’hôte DNS, spécifiez les valeurs qui ne sont pas affichées séparément sous forme d’une chaîne combinée, dans l’ordre, pour la valeur **Target (Cible)** de l’enregistrement. (Remarque : suivant votre hôte DNS, le champ **Target (Cible)** peut avoir une autre appellation, comme : **Content (Contenu)**, **IP Address (Adresse IP)** ou **Target Host (Hôte cible)**). Pour configurer la valeur combinée, vous créez une seule chaîne pour les champs qui n’apparaissent pas individuellement, en séparant les valeurs par des espaces. Les valeurs doivent être incluses *dans l’ordre*, en laissant les valeurs ayant des champs distincts disponibles : Priority (Priorité), Weight (Poids), Port (Port), Target (Cible). >  Par exemple, lorsque la valeur Priority (Priorité) comporte un champ distinct, concaténez uniquement les valeurs Weight (Poids), Port (Port) et Target (Cible) : **Target (Cible)**  : 1 443 sipdir.online.partner.lync.cn 
    > 
    >  Pour **TTL (Durée de vie)**  : définissez cette valeur sur **1 heure** ou sur l’équivalent en minutes ( **60** ), secondes ( **3600** ), etc. 
  
2. Lorsque vous avez terminé, enregistrez les enregistrements.
    
    > [!NOTE]
    >  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
::: moniker-end

## <a name="more-about-updating-dns-records"></a>En savoir plus sur la mise à jour des enregistrements DNS
<a name="BKMK_MoreAbout"> </a>

 **Si vous savez comment mettre à jour les enregistrements DNS auprès de l'hôte DNS de votre domaine**, utilisez les valeurs DNS Microsoft 365 pour modifier les enregistrements auprès de l'hôte DNS de votre domaine, par exemple, pour configurer un enregistrement MX ou SPF. Recherchez les valeurs spécifiques à utiliser en [procédant comme suit](../get-help-with-domains/information-for-dns-records.md), ou passez celles-ci en revue dans l'Assistant Configuration des domaines au cours de l'exécution de ce dernier.
  
 **Si vous avez besoin d'aide pour savoir comment ajouter les enregistrements DNS requis**, consultez la rubrique [Configurer votre domaine (instructions spécifiques à l'hôte)](https://docs.microsoft.com/office365/admin/get-help-with-domains/set-up-your-domain-host-specific-instructions?view=o365-worldwide), commencez par [rassembler les informations nécessaires pour créer les enregistrements DNS Microsoft 365](../get-help-with-domains/information-for-dns-records.md). Utilisez ensuite les étapes générales décrites dans cette rubrique pour configurer les enregistrements DNS de votre domaine, de façon à ce que vous puissiez utiliser votre domaine avec les services Microsoft 365, tels que le courrier.
  
 **Si vous n'utilisez pas de site web avec votre domaine personnalisé**, Microsoft 365 peut configurer et gérer les enregistrements DNS associés à votre domaine à votre place. Découvrez les [deux options permettant de configurer et de gérer des enregistrements DNS pour un domaine personnalisé](https://support.office.com/article/5980474a-097f-4f21-a864-21245314957f.aspx) dans Microsoft 365. 
  

