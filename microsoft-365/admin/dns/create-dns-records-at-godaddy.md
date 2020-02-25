---
title: Créer des enregistrements DNS auprès de GoDaddy pour Office 365
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
ms.assetid: f40a9185-b6d5-4a80-bb31-aa3bb0cab48a
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur GoDaddy pour Office 365.
ms.custom: okr_smb
ms.openlocfilehash: 4a67ef090c2b91c4cf1fdde376ab35e3a4ed4e20
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42239148"
---
# <a name="create-dns-records-at-godaddy-for-office-365"></a>Créer des enregistrements DNS auprès de GoDaddy pour Office 365

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez.

Si GoDaddy est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

Une fois ces enregistrements ajoutés sur GoDaddy, votre domaine est configuré pour utiliser les services Office 365.

Pour en savoir plus sur l'hébergement web et le DNS pour les sites web avec Office 365, voir [Utiliser un site web public avec Office 365](https://support.office.com/article/choose-a-public-website-3325d50e-d131-403c-a278-7f3296fe33a9).

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification
<a name="BKMK_verify"> </a>

Avant d'utiliser votre domaine avec Office 365, nous devons vérifier que celui-ci vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d'enregistrement de domaines et à créer l'enregistrement DNS montre à Office 365 que le domaine vous appartient réellement.

> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement.

Suivez la procédure ci-dessous.

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). Vous serez invité à vous connecter.

    ![GoDaddy-BP-configure-1-1](../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Sous **domaines**, sélectionnez DNS sous le domaine à modifier.

    ![GoDaddy-BP-configure-1-2](../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Sélectionnez **Ajouter**.

    ![GoDaddy-BP-configure-1-4](../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. Choisissez **TXT (Text)** (TXT (Texte)) dans la liste déroulante. In the boxes for the new record, type or copy and paste the values from the following table.

    |**Record type (Type d'enregistrement)** |**Host (Hôte)**|**TXT Value (Valeur TXT)**|**TTL** |
    |:-----|:-----|:-----|:-----|
    |TXT (Text) (TXT (Texte))|@|MS=ms *XXXXXXXX*<br>**Remarque**: Voici un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Office 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 hour  <br>(Sélectionnez une valeur dans la liste déroulante.)|

      ![GoDaddy-BP-Verify-1-0](../media/dns/56526870-d6465780-651a-11e9-9cf0-d6fff71e2f62.png)

5. Cliquez sur **Enregistrer**.

6. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

Now that you've added the record at your domain registrar's site, you'll go back to Office 365 and request Office 365 to look for the record.

When Office 365 finds the correct TXT record, your domain is verified.
  
1. Dans le centre d’administration, accédez à la page **paramètres** \> des <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> .

    
2. Dans la page **domaines** , sélectionnez le domaine que vous vérifiez. 
    
    
  
3. Sur la page **installation** , sélectionnez **Démarrer l’installation**.



4. Sur la page **vérifier le domaine** , sélectionnez **vérifier**.



> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Office 365
<a name="BKMK_add_MX"> </a>

Suivez la procédure ci-dessous.

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). Vous serez invité à vous connecter.

    ![GoDaddy-BP-configure-1-1](../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Sous **domaines**, sélectionnez DNS sous le domaine à modifier.

    ![GoDaddy-BP-configure-1-2](../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Sélectionnez **Ajouter**.

    ![GoDaddy-BP-configure-1-4](../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. Choisissez **MX (Mail Exchanger)** (MX - Serveur de courrier) dans la liste déroulante.

    ![GoDaddy-BP-configure-2-0](../media/dns/56528642-85842e00-651d-11e9-8dd8-217f468f9a18.png)

5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choisissez la valeur **TTL (durée de vie** ) dans la liste déroulante.)

    |**Record type (Type d'enregistrement)**|**Host (Hôte)**|**Points to (Pointe vers)**|**Priority (Priorité)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX (Mail Exchanger) (MX - Serveur de courrier)  <br/> |@  <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Remarque :** Obtenez votre * \<clé\> de domaine* à partir de votre compte Office 365.           [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |10   <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx). <br/> |1 heure  <br/> |

6. Cliquez sur **Enregistrer**.

## <a name="add-the-cname-records-that-are-required-for-office-365"></a>Ajouter les enregistrements CNAME requis pour Office 365
<a name="BKMK_add_CNAME"> </a>

Suivez la procédure ci-dessous.

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). Vous serez invité à vous connecter.

    ![GoDaddy-BP-configure-1-1](../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Sous **domaines**, sélectionnez DNS sous le domaine à modifier.

    ![GoDaddy-BP-configure-1-2](../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Sélectionnez **Ajouter**.

    ![GoDaddy-BP-configure-1-4](../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)


4. Choisissez **CNAME (Alias)** dans la liste déroulante.

    ![GoDaddy-BP-configure-3-0](../media/dns/56528891-e7449800-651d-11e9-8eac-112285b8e38c.png)

5. Créez le premier enregistrement CNAME.

    Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

    (Choisissez la valeur **TTL (durée de vie** ) dans la liste déroulante.)

    |**Record type (Type d'enregistrement)**|**Host (Hôte)**|**Points to (Pointe vers)**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME (Alias)  <br/> |autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 hour  <br/> |
    |CNAME (Alias)  <br/> |sip  <br/> |sipdir.online.lync.com  <br/> |1 heure  <br/> |
    |CNAME (Alias)  <br/> |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |1 heure  <br/> |
    |CNAME (Alias)  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |1 heure  <br/> |
    |CNAME (Alias)  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment.manage.microsoft.com  <br/> |1 hour  <br/> |



6. Répétez ces étapes pour ajouter l’enregistrement CNAMe suivant jusqu’à ce que vous ayez créé les six enregistrements CNAMe.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajouter un enregistrement TXT pour SPF afin d'éviter le courrier indésirable
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> You cannot have more than one TXT record for SPF for a domain. If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues. If you already have an SPF record for your domain, don't create a new one for Office 365. Ajoutez plutôt les valeurs Office 365 requises à l'enregistrement actuel de manière à n'avoir qu'un  *seul*  enregistrement SPF qui inclut les deux ensembles de valeurs.

Suivez la procédure ci-dessous.

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). Vous serez invité à vous connecter.

    ![GoDaddy-BP-configure-1-1](../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Sous **domaines**, sélectionnez DNS sous le domaine à modifier.

    ![GoDaddy-BP-configure-1-2](../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Sélectionnez **Ajouter**.

    ![GoDaddy-BP-configure-1-4](../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. Choisissez **TXT (Text)** (TXT (Texte)) dans la liste déroulante.

    ![GoDaddy-BP-configure-4-0](../media/dns/56529449-c0d32c80-651e-11e9-90e9-895aa1c4bbf1.png)

5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes.

    (Choisissez la valeur **TTL (durée de vie** ) dans les listes déroulantes.)

    |**Record type (Type d'enregistrement)**|**Host (Hôte)**|**TXT Value (Valeur TXT)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|
    |TXT (Text) (TXT (Texte))  <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** Nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.           |1 hour  <br/> |

    ![GoDaddy-BP-configure-4-1](../media/7c724f02-c9b3-42ab-b9c0-78959fa6ffad.png)

6. Cliquez sur **Enregistrer**.


## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>Ajouter les 2 enregistrements SRV requis pour Office 365
<a name="BKMK_add_SRV"> </a>

Suivez la procédure ci-dessous.

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled). Vous serez invité à vous connecter.

    ![GoDaddy-BP-configure-1-1](../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Sous **domaines**, sélectionnez DNS sous le domaine à modifier.

    ![GoDaddy-BP-configure-1-2](../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Sélectionnez **Ajouter**.

    ![GoDaddy-BP-configure-1-4](../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. Choisissez **SRV (Service)** (SRV (Service)) dans la liste déroulante.

    ![GoDaddy-BP-configure-5-0](../media/dns/56529669-1dcee280-651f-11e9-8ba2-ecf4fc2f6dca.png)

5. Créez le premier enregistrement SRV.

    Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

    (Choisissez le **type d’enregistrement** et les valeurs de **durée de vie** dans les listes déroulantes.)

    |**Type d'enregistrement**|**Name (Nom)**|**Target (Cible)**|**Protocol (Protocole)**|**Service (Service)**|**Priority (Priorité)**|**Weight (Poids)**|**Port**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV (Service)  <br/> |@  <br/> |sipdir.online.lync.com  <br/> |_tls  <br/> |_sip  <br/> |100  <br/> |0,1  <br/> |443  <br/> |1 heure  <br/> |
    |SRV (Service)  <br/> |@  <br/> |sipfed.online.lync.com  <br/> |_tcp  <br/> |_sipfederationtls  <br/> |100  <br/> |0,1  <br/> |5061  <br/> |1 heure  <br/> |

    ![GoDaddy-BP-configure-5-1](../media/a1b15ab1-eb6a-4672-90d1-7ac3e0beb223.png)


6. Répétez l' **étape 5** pour créer l’autre enregistrement SRV.

7. Cliquez sur **Enregistrer**.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
