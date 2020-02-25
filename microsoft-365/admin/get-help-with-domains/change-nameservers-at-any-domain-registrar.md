---
title: Modifier les serveurs de noms de manière à configurer Office 365 avec n'importe quel bureau d'enregistrement de domaines
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
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
- GEU150
- GEA150
ms.assetid: a8b487a9-2a45-4581-9dc4-5d28a47010a2
description: Découvrez comment ajouter et configurer votre domaine dans Office 365 de sorte que vos services de messagerie électronique et Skype entreprise Online utilisent votre propre nom de domaine.
ms.custom: okr_smb
ms.openlocfilehash: 3030fc33a6d528fd6cb4e97c27cdbb7c251e9a97
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42252970"
---
# <a name="change-nameservers-to-set-up-office-365-with-any-domain-registrar"></a>Modifier les serveurs de noms de manière à configurer Office 365 avec n'importe quel bureau d'enregistrement de domaines

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Consultez [la rubrique Configurer votre domaine (instructions spécifiques à l’hôte)](../get-help-with-domains/set-up-your-domain-host-specific-instructions.md) pour savoir si nous avons des instructions pour votre serveur d’inscriptions. 
  
Suivez ces instructions pour ajouter et configurer votre domaine dans Office 365 afin que vos services tels que le courrier électronique et Skype Entreprise Online utilisent le nom de votre domaine. Pour ce faire, vous devez vérifier votre domaine et modifier les serveurs de noms de votre domaine afin qu'ils utilisent Office 365 et que les enregistrements DNS corrects puissent être configurés automatiquement. Procédez comme suit si les instructions suivantes décrivent votre situation :
  
- Vous disposez de votre propre domaine et souhaitez le configurer pour qu'il fonctionne avec Office 365.
    
- Vous voulez qu'Office 365 gère vos enregistrements DNS pour vous (vous pouvez naturellement [gérer vos propres enregistrements DNS](../setup/add-domain.md)).
    
## <a name="add-a-txt-or-mx-record-for-verification"></a>Ajouter un enregistrement TXT ou MX à des fins de vérification
<a name="BKMK_verify"> </a>

> [!NOTE]
> Vous ne devez créer qu'un seul des deux enregistrements. TXT est le type d'enregistrement préféré, mais certains fournisseurs d'hébergement DNS ne le prennent pas en charge, auquel cas vous pouvez créer un enregistrement MX à la place. 
  
Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
### <a name="find-the-area-on-your-dns-hosting-providers-website-where-you-can-create-a-new-record"></a>Recherchez la zone sur le site Web de votre fournisseur d’hébergement DNS où vous pouvez créer un nouvel enregistrement.

1. Connectez-vous sur le site web de votre fournisseur d'hébergement DNS.
    
2. Choisissez votre domaine.
    
3. Trouvez la page sur laquelle vous pouvez modifier les enregistrements DNS pour votre domaine.
    
### <a name="create-the-record"></a>Créer l’enregistrement

Selon que vous créez un enregistrement TXT ou un enregistrement MX, effectuez l'une des opérations suivantes :
  
**Si vous créez un enregistrement TXT, utilisez les valeurs suivantes :**
    
|||||
|:-----|:-----|:-----|:-----|
|**Type d'enregistrement** <br/> |**Alias** ou **nom d'hôte** <br/> |**Valeur** <br/> |**TTL** <br/> |
|TXT  <br/> |Effectuez l'une des opérations suivantes : Tapez **@**, laissez le champ vide ou entrez le nom de votre domaine.  <br/> > [!NOTE]> Les conditions requises pour ce champ ne sont pas identiques pour tous les hôtes DNS.           
|MS=ms *XXXXXXXX*  <br/> > [!NOTE]> Il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |Définissez cette valeur sur **1 heure** ou sur l'équivalent en minutes ( **60** ), en secondes ( **3600** ), etc.  <br/> |
   
**Si vous créez un enregistrement MX, utilisez les valeurs suivantes :**
    
||||||
|:-----|:-----|:-----|:-----|:-----|
|**Type d'enregistrement**|**Alias** ou **nom d'hôte**|**Valeur**|**Priorité**|**TTL**|
|MX|Entrez soit **@**, soit votre nom de domaine. |MS=ms *XXXXXXXX* > [!NOTE]> Il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |Pour **Priority**, pour éviter les conflits avec l’enregistrement MX utilisé pour le flux de messagerie, utilisez une priorité inférieure à la priorité des enregistrements MX existants. Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.md#what-is-mx-priority). |Définissez cette valeur sur **1 heure** ou sur l'équivalent en minutes ( **60** ), en secondes ( **3600** ), etc. |
   
### <a name="save-the-record"></a>Enregistrer l’enregistrement

Now that you've added the record at your domain registrar's site, you'll go back to Office 365 and request Office 365 to look for the record.
  
When Office 365 finds the correct TXT record, your domain is verified.
  

1. Dans le centre d’administration, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> .
    
2. Dans la page **domaines** , sélectionnez le domaine que vous vérifiez. 
    
  
3. Sur la page **installation** , sélectionnez **Démarrer l’installation**.
 
    
  
4. Sur la page **vérifier le domaine** , sélectionnez **vérifier**.
    
    
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine
<a name="BKMK_nameservers"> </a>

À la dernière étape de l'Assistant de configuration de domaines dans Office 365, vous devez exécuter une dernière tâche. Pour configurer votre domaine avec les services Office 365 tels que le courrier, vous devez modifier les enregistrements de serveur de noms de votre domaine auprès de votre bureau d'enregistrement de domaines afin qu'ils pointent vers les serveurs de noms principal et secondaire d'Office 365. Comme Office 365 héberge votre DNS, les enregistrements DNS nécessaires pour vos services sont configurés automatiquement. Vous pouvez mettre à jour les enregistrements de serveur de noms vous-même en suivant les étapes fournies éventuellement par votre bureau d'enregistrement de domaines dans l'aide disponible sur son site web. Si vous n'êtes pas familiarisé avec DNS, contactez le support du bureau d'enregistrement de domaines.

::: moniker range="o365-worldwide"
  
Pour changer vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit :
  
1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.
    
2. Créez deux enregistrements de serveur de noms, ou modifiez les enregistrements existants pour qu'ils correspondent aux valeurs suivantes :
    
|||
|:-----|:-----|
|Premier serveur de noms  <br/> |ns1.bdm.microsoftonline.com  <br/> |
|Deuxième serveur de noms  <br/> |ns2.bdm.microsoftonline.com  <br/> |
   
   > [!TIP]
   > Vous devez utiliser au moins deux enregistrements de serveur de noms. Si d’autres serveurs de noms sont répertoriés, vous pouvez les supprimer ou les remplacer par **NS3.BDM.microsoftonline.com** et **NS4.BDM.microsoftonline.com**. 
  
3. Enregistrez vos modifications.
    
> [!CAUTION]
> Quand vous modifiez les enregistrements de serveur de noms de votre domaine afin qu'ils pointent vers les serveurs de noms d'Office 365, tous les services actuellement associés à votre domaine sont affectés. Si vous passez une étape de l'Assistant (par exemple, ajout des adresses de courrier) ou si vous utilisez votre domaine pour les blogs, les paniers ou d'autres services, des étapes supplémentaires sont nécessaires, sans quoi cette modification pourrait entraîner une interruption de service telle que la perte de l'accès au courrier ou le blocage de l'accès à votre site web. 

::: moniker-end

::: moniker range="o365-21vianet"
  
1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.
    
2. Créez deux enregistrements de serveur de noms, ou modifiez les enregistrements existants pour qu'ils correspondent aux valeurs suivantes :
    
|||
|:-----|:-----|
|Premier serveur de noms  <br/> |ns1.dns.partner.microsoftonline.cn  <br/> |
|Deuxième serveur de noms  <br/> |ns2.dns.partner.microsoftonline.cn  <br/> |
   
   > [!TIP]
   > Vous devez utiliser au moins deux enregistrements de serveur de noms. Si d’autres serveurs de noms sont répertoriés, vous pouvez les supprimer ou les remplacer par **NS3.DNS.Partner.microsoftonline.CN** et **NS4.DNS.Partner.microsoftonline.CN**. 
  
3. Enregistrez vos modifications.
    
> [!CAUTION]
> Lorsque vous modifiez les enregistrements de serveur de noms de votre domaine pour qu’ils pointent vers l’Office 365 géré par les serveurs de noms 21Vianet, tous les services actuellement associés à votre domaine sont affectés. Si vous avez ignoré les étapes de l’Assistant, telles que l’ajout d’adresses de messagerie, ou si vous utilisez votre domaine pour les blogs, les paniers d’achat ou d’autres services, des étapes supplémentaires sont requises. Dans le cas contraire, cette modification pourrait entraîner un temps d’arrêt du service, tel qu’un manque d’accès à la messagerie ou votre site Web actuel inaccessible. 

::: moniker-end
  
Voici, par exemple, quelques étapes supplémentaires qui peuvent être nécessaires pour le courrier et l'hébergement du site web :
  
- Déplacez toutes les adresses de courrier qui utilisent votre domaine vers Office 365 avant de modifier vos enregistrements NS.
    
- Vous souhaitez ajouter un domaine actuellement utilisé avec une adresse de site Web, par exemple www.fourthcoffee.com ? Vous pouvez suivre les étapes ci-dessous pendant que vous ajoutez le domaine pour conserver son site Web hébergé sur lequel le site est hébergé maintenant afin que les utilisateurs puissent toujours accéder au site Web une fois que vous avez modifié les enregistrements de serveur de noms de domaine pour qu’ils pointent vers Office 365.

1. Dans le centre d’administration, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> .

3. Dans la page Domaines, sélectionnez un domaine.

4. Sous **paramètres DNS**, sélectionnez **enregistrements personnalisés**, puis **nouvel enregistrement personnalisé**.

5. Sélectionnez le type d’enregistrement DNS que vous souhaitez ajouter, puis tapez les informations pour le nouvel enregistrement.

6. Cliquez sur **Enregistrer**.
    
> [!NOTE]
> L'application des modifications apportées à votre enregistrement de serveur de noms dans le système DNS sur Internet peut prendre plusieurs heures. Vous pourrez ensuite utiliser votre messagerie et les autres services Office 365 avec votre domaine. 
  

