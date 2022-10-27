---
title: Connecter vos enregistrements DNS sur GoDaddy à Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
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
description: Apprenez à vérifier votre domaine et à configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online et d’autres services sur GoDaddy pour Microsoft.
ms.openlocfilehash: ce9d26d5ecf2bb91ac267e6ab0305e1d50eb4095
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729498"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>Connecter vos enregistrements DNS sur GoDaddy à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si GoDaddy est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

## <a name="before-you-begin"></a>Avant de commencer

Vous avez deux options pour configurer des enregistrements DNS pour votre domaine :

- [**Utiliser Domain Connect**](#use-domain-connect-to-verify-and-set-up-your-domain) Si vous n’avez pas configuré votre domaine avec un autre fournisseur de services de messagerie, suivez les étapes connexion au domaine pour vérifier et configurer automatiquement votre nouveau domaine à utiliser avec Microsoft 365.

   OR

- [**Utiliser les étapes manuelles**](#create-dns-records-with-manual-setup) Vérifiez votre domaine à l’aide des étapes manuelles ci-dessous et choisissez quand et quels enregistrements ajouter à votre bureau d’enregistrement de domaines. Cela vous permet de configurer de nouveaux enregistrements MX (mail), par exemple, à votre convenance.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Utiliser Domain Connect pour vérifier et configurer votre domaine

Suivez ces étapes pour vérifier et configurer automatiquement votre domaine GoDaddy avec Microsoft 365 :

1. Dans le Centre d'administration Microsoft 365, sélectionnez **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>, puis sélectionnez le domaine que vous souhaitez configurer.

1. Sélectionnez les trois points (autres actions) > choisissez **Démarrer l’installation**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Dans comment voulez-vous connecter votre domaine ? , sélectionnez **Continuer**.

1. Dans la page Ajouter des enregistrements DNS, sélectionnez **Ajouter des enregistrements DNS**.

1. Dans la page de connexion GoDaddy, connectez-vous à votre compte, puis sélectionnez **Autoriser**.

   Cette opération termine la configuration de votre domaine pour Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Créer des enregistrements DNS avec une configuration manuelle

Une fois que vous avez ajouté ces enregistrements sur GoDaddy, votre domaine est configuré pour fonctionner avec les services Microsoft.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled).

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification de connexion, sélectionnez votre nom de connexion en haut à droite, puis sélectionnez **Mes produits**.

1. Sous **Domaines**, sélectionnez les trois points en regard du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Enregistrements**, sélectionnez **AJOUTER** (vous devrez peut-être faire défiler vers le bas).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

1. Choisissez **TXT** dans la liste déroulante.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez TXT dans la liste déroulante Type.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la table.

   |Type|Hôte|TXT Value|Durée de vie|
   |---|---|---|---|
   |TXT|@|MS=ms *XXXXXXXX*<br>**Remarque** : Il s’agit d’un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 heure  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Renseignez les valeurs de la table pour l’enregistrement TXT.":::

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="Sélectionnez Enregistrer.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
Pour vérifier l’enregistrement dans Microsoft 365 :
  
1. Dans le Centre d’administration, accédez aux **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>.

1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer l’installation**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.
  
1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled).

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification de connexion, sélectionnez votre nom de connexion en haut à droite, puis sélectionnez **Mes produits**.

2. Sous **Domaines**, sélectionnez les trois points en regard du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

3. Sous **Enregistrements**, sélectionnez **AJOUTER**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

4. Choisissez **MX** dans la liste déroulante.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez MX dans la liste déroulante Type.":::

5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

   (Choisissez les valeurs **Type** et **TTL** dans la liste déroulante.)

   |Type|Hôte|Points to |Priorité|Durée de vie|
   |---|---|---|---|---|
   |MX|@| *\<domain-key\>*.mail.protection.outlook.com  <br/> **Note:** Obtenez votre à *\<domain-key\>* partir de votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|10  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml).|1 heure|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Renseignez les valeurs de la table pour l’enregistrement MX.":::

6. Sélectionnez **Enregistrer**.

### <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled).

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification de connexion, sélectionnez votre nom de connexion en haut à droite, puis sélectionnez **Mes produits**.

2. Sous **Domaines**, sélectionnez les trois points en regard du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

3. Sous **Enregistrements**, sélectionnez **AJOUTER**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

4. Choisissez **CNAME** dans la liste déroulante.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez CNAME dans la liste déroulante Type.":::

5. Créez l’enregistrement CNAME.

   Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

   (Choisissez la valeur **TTL** dans la liste déroulante.)

   |Type|Hôte|Points to |Durée de vie|
   |---|---|---|---|
   |CNAME|autodiscover|autodiscover.outlook.com|1 heure|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Renseignez les valeurs de la table pour l’enregistrement CNAME.":::

6. Sélectionnez **Enregistrer**.

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs.

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled).

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification de connexion, sélectionnez votre nom de connexion en haut à droite, puis sélectionnez **Mes produits**.

2. Sous **Domaines**, sélectionnez les trois points en regard du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

3. Sous **Enregistrements**, sélectionnez **AJOUTER**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

4. Choisissez **TXT** dans la liste déroulante.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez TXT dans la liste déroulante Type.":::

5. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes.

   (Choisissez la valeur **TTL** dans les listes déroulantes.)

   |Type|Hôte|TXT Value|Durée de vie|
   |---|---|---|---|
   |TXT|@|v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|1 heure|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Renseignez les valeurs de la table pour l’enregistrement TXT.":::

6. Sélectionnez **Enregistrer**.

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversations, les téléconférences et les appels vidéo, en plus de Microsoft Teams. Skype a besoin de 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter les utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled).

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification de connexion, sélectionnez votre nom de connexion en haut à droite, puis sélectionnez **Mes produits**.

1. Sous **Domaines**, sélectionnez les trois points en regard du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Enregistrements**, sélectionnez **AJOUTER**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

1. Choisissez **SRV** dans la liste déroulante.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez SRV dans la liste déroulante Type.":::

1. Créez le premier enregistrement SRV.

   Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

   (Choisissez les valeurs **Type** et **TTL** dans les listes déroulantes.)

   |Type|Service|Protocole|Nom|Target|Priorité|Pondération|Port|Durée de vie|
   |---|---|---|---|---|---|---|---|---|
   |SRV|_sip|_tls|@|sipdir.online.lync.com|100| 1|443|1 heure|
   |SRV|_sipfederationtls|_tcp|@| sipfed.online.lync.com| 100|1|5061|1 Hour|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="Renseignez les valeurs de la table pour l’enregistrement SRV.":::

1. Sélectionnez **Enregistrer**.

1. Ajoutez l’autre enregistrement SRV en choisissant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Ajoutez les deux enregistrements CNAME requis pour Skype Entreprise
  
1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled).

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification de connexion, sélectionnez votre nom de connexion en haut à droite, puis sélectionnez **Mes produits**.

1. Sous **Domaines**, sélectionnez les trois points en regard du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Enregistrements**, sélectionnez **AJOUTER**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

1. Choisissez **CNAME** dans la liste déroulante.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez CNAME dans la liste déroulante Type.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

   |Type|Hôte|Points to |Durée de vie|
   |---|---|---|---|
   |CNAME|sip|sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|
   |CNAME|lyncdiscover|webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Renseignez les valeurs de la table pour l’enregistrement CNAME.":::
  
1. Sélectionnez **Enregistrer**.
  
1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils a besoin de 2 enregistrements CNAME pour permettre aux utilisateurs d’inscrire des appareils au service.

### <a name="add-the-two-required-cname-records-mobile-device-management"></a>Ajouter les deux enregistrements CNAME requis Mobile Gestion des appareils

1. Pour commencer, accédez à la page de vos domaines sur le site GoDaddy en utilisant [ce lien](https://account.godaddy.com/products/?go_redirect=disabled).

   Si vous êtes invité à vous connecter, utilisez vos informations d’identification de connexion, sélectionnez votre nom de connexion en haut à droite, puis sélectionnez **Mes produits**.

1. Sous **Domaines**, sélectionnez les trois points en regard du domaine que vous souhaitez vérifier, puis sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Enregistrements**, sélectionnez **AJOUTER**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Sélectionnez AJOUTER.":::

1. Choisissez **CNAME** dans la liste déroulante.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Sélectionnez CNAME dans la liste déroulante Type.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

   |Type|Hôte|Points to |Durée de vie|
   |---|---|---|---|
   |CNAME|enterpriseregistration|enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|
   |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Renseignez les valeurs de la table pour l’enregistrement CNAME.":::
  
1. Sélectionnez **Enregistrer**.
  
1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).
