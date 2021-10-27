---
title: Connecter vos enregistrements DNS sur GoDaddy pour Microsoft 365
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
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f40a9185-b6d5-4a80-bb31-aa3bb0cab48a
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services sur GoDaddy pour Microsoft.
ms.openlocfilehash: a4428b092ee1a679fe622d83dbfee7535649e9f0
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586389"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>Connecter vos enregistrements DNS sur GoDaddy pour Microsoft 365

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si GoDaddy est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

## <a name="before-you-begin"></a>Avant de commencer

Vous avez deux options pour la configuration des enregistrements DNS pour votre domaine :

- [**Utiliser l’Connecter**](#use-domain-connect-to-verify-and-set-up-your-domain) Si vous n’avez pas encore installé votre domaine auprès d’un autre fournisseur de services de messagerie, utilisez les étapes de l’Connecter de domaine pour vérifier et configurer automatiquement votre nouveau domaine à utiliser avec Microsoft 365. 

   OR

- [**Utiliser les étapes manuelles**](#create-dns-records-with-manual-setup) Vérifiez votre domaine en suivant les étapes manuelles ci-dessous et choisissez quand et quels enregistrements ajouter à votre bureau d’enregistrement de domaines. Cela vous permet de configurer de nouveaux enregistrements MX (courrier), par exemple, à votre convenance. 

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Utiliser domain Connecter pour vérifier et configurer votre domaine

Suivez ces étapes pour vérifier et configurer automatiquement votre domaine GoDaddy avec Microsoft 365 :

1. Dans la Centre d'administration Microsoft 365, **sélectionnez Paramètres** domaines, puis sélectionnez le domaine  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>que vous souhaitez configurer.

1. Sélectionnez les trois points (plus d’actions) > **sélectionnez Démarrer la configuration.**

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Comment voulez-vous connecter votre domaine ? page, sélectionnez **Continuer**.   

1. Dans la page Ajouter des enregistrements DNS, sélectionnez Ajouter des enregistrements **DNS.**

1. Sur la page de connexion GoDaddy, connectez-vous à votre compte, puis sélectionnez **Autoriser.**
    
    Cela termine la configuration de votre domaine pour Microsoft 365. 

## <a name="create-dns-records-with-manual-setup"></a>Créer des enregistrements DNS avec la configuration manuelle

Une fois ces enregistrements ajoutés sur GoDaddy, votre domaine est installé pour fonctionner avec services Microsoft.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.

> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement.

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). 

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification, sélectionnez votre nom de connexion dans le coin supérieur droit, puis sélectionnez **Mes produits**.

1. Sous **Domaines,** sélectionnez les trois points en dessous du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer le DNS.**

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Enregistrements,** **sélectionnez ADD** (vous de devez peut-être faire défiler vers le bas).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

1. Choisissez **TXT dans** la liste liste. 

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez TXT dans la liste drop-down Type.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau.

   |**Type** |**Hôte**|**VALEUR TXT**|**TTL** |
   |:-----|:-----|:-----|:-----|
   |TXT |@|MS=ms *XXXXXXXX*<br>**Remarque**: il s’agit d’un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 heure  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Remplissez les valeurs du tableau pour l’enregistrement TXT.":::

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="Sélectionnez Enregistrer.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
Pour vérifier l’enregistrement dans Microsoft 365 :
  
1. Dans le Centre d’administration, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
    
1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer la configuration.** 

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.
  
1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). 

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification, sélectionnez votre nom de connexion dans le coin supérieur droit, puis sélectionnez **Mes produits**.

2. Sous **Domaines,** sélectionnez les trois points en dessous du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer le DNS.**

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

3. Sous **Enregistrements,** sélectionnez **AJOUTER.**

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

4. Choisissez **MX dans** la liste liste.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez MX dans la liste liste type.":::

5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choisissez les **valeurs Type** et **TTL** dans la liste liste.)

    |**Type**|**Host (Hôte)**|**Points to (Destination)**|**Priorité**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX  <br/> |@  <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenez votre *\<domain-key\>* depuis votre compte Microsoft.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> |1 heure  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Remplissez les valeurs du tableau pour l’enregistrement MX.":::

6. Sélectionnez **Enregistrer**.

### <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). 

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification, sélectionnez votre nom de connexion dans le coin supérieur droit, puis sélectionnez **Mes produits**.

2. Sous **Domaines,** sélectionnez les trois points en dessous du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer le DNS.**

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

3. Sous **Enregistrements,** sélectionnez **AJOUTER.**

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

4. Choisissez **CNAME dans** la liste de listes.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez CNAME dans la liste drop-down Type.":::

5. Créez l’enregistrement CNAME.

    Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

    (Choisissez la **valeur TTL** dans la liste.)

    |**Type**|**Host (Hôte)**|**Points to (Destination)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover <br/> |autodiscover.outlook.com  <br/> |1 heure  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Remplissez les valeurs du tableau pour l’enregistrement CNAME.":::

6. Sélectionnez **Enregistrer**.

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs.

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). 

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification, sélectionnez votre nom de connexion dans le coin supérieur droit, puis sélectionnez **Mes produits**.

2. Sous **Domaines,** sélectionnez les trois points en dessous du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer le DNS.**

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

3. Sous **Enregistrements,** sélectionnez **AJOUTER.**

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

4. Choisissez **TXT dans** la liste liste.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez TXT dans la liste drop-down Type.":::

5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes.

    (Choisissez la **valeur TTL** dans les listes de listes.)

    |**Type**|**Hôte**|**VALEUR TXT**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte. |1 heure  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Remplissez les valeurs du tableau pour l’enregistrement TXT.":::

6. Sélectionnez **Enregistrer**.

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversation, les appels de conférence et les appels vidéo, en plus de Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). 

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification, sélectionnez votre nom de connexion dans le coin supérieur droit, puis sélectionnez **Mes produits**.

1. Sous **Domaines,** sélectionnez les trois points en dessous du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer le DNS.**

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Enregistrements,** sélectionnez **AJOUTER.**

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

1. Choisissez **SRV** dans la liste liste.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez SRV dans la liste drop-down Type.":::

1. Créez le premier enregistrement SRV.

    Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

    (Choisissez les **valeurs Type** et **TTL** dans les listes de listes.)

    |**Type**|**Service**|**Protocol (Protocole)**| **Name (Nom)** | **Target (Cible)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV   <br/> |_sip  <br/> |_tls  <br/> |@  <br/> |sipdir.online.lync.com  <br/> |100 <br/> | 1  <br/> |443  <br/> |1 heure  <br/> |
    |SRV  <br/> |_sipfederationtls  <br/> |_tcp  <br/> |@  <br/> | sipfed.online.lync.com  <br/> | 100  <br/> |1  <br/> |5061  <br/> |1 heure  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="Remplissez les valeurs du tableau pour l’enregistrement SRV.":::

1. Sélectionnez **Enregistrer**.

1. Ajoutez l’autre enregistrement SRV en choisissant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis
  
1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). 

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification, sélectionnez votre nom de connexion dans le coin supérieur droit, puis sélectionnez **Mes produits**.

2. Sous **Domaines,** sélectionnez les trois points en dessous du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer le DNS.**

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Enregistrements,** sélectionnez **AJOUTER.**

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

1. Choisissez **CNAME dans** la liste de listes.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez CNAME dans la liste drop-down Type.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    |**Type**|**Host (Hôte)**|**Points to (Destination)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1 heure  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1 Hour  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Remplissez les valeurs du tableau pour l’enregistrement CNAME.":::
  
1. Sélectionnez **Enregistrer**. 
  
1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et gestion des périphériques mobiles pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. La gestion des périphériques mobiles nécessite 2 enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). 

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification, sélectionnez votre nom de connexion dans le coin supérieur droit, puis sélectionnez **Mes produits**.

1. Sous **Domaines,** sélectionnez les trois points en dessous du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer le DNS.**

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer le DNS dans la liste.":::

1. Sous **Enregistrements,** sélectionnez **AJOUTER.**

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

1. Choisissez **CNAME dans** la liste de listes.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez CNAME dans la liste drop-down Type.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    |**Type**|**Host (Hôte)**|**Points to (Destination)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1 heure  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |1 Hour  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Remplissez les valeurs du tableau pour l’enregistrement CNAME.":::
  
1. Sélectionnez **Enregistrer**. 
  
1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
