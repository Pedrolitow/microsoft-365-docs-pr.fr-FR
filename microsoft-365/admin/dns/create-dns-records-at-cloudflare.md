---
title: Connecter vos enregistrements DNS sur Cloudflare pour Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online et d’autres services sur Cloudflare pour Microsoft.
ms.openlocfilehash: a7f1307530d5dc874120db0f40b631ada4b833e8
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568036"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>Connecter vos enregistrements DNS sur Cloudflare pour Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si Cloudflare est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

## <a name="before-you-begin"></a>Avant de commencer

Vous avez deux options pour la configuration des enregistrements DNS pour votre domaine :

- Utilisez [**Domain Connecter**](#use-domain-connect-to-verify-and-set-up-your-domain) Si vous n’avez pas encore installé votre domaine auprès d’un autre fournisseur de services de messagerie, utilisez les étapes domain Connecter pour vérifier et configurer automatiquement votre nouveau domaine à utiliser avec Microsoft 365.

    OR

- [**Utiliser les étapes manuelles**](#create-dns-records-with-manual-setup) Vérifiez votre domaine en suivant les étapes manuelles ci-dessous et choisissez quand et quels enregistrements ajouter à votre bureau d’enregistrement de domaines. Cela vous permet de configurer de nouveaux enregistrements MX (courrier), par exemple, à votre convenance.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Utiliser domain Connecter pour vérifier et configurer votre domaine

Suivez ces étapes pour vérifier et configurer automatiquement votre domaine Cloudflare avec Microsoft 365 :

1. Dans la Centre d'administration Microsoft 365, **sélectionnez Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**domaines**</a>, puis sélectionnez le domaine que vous souhaitez configurer.

1. Sélectionnez les trois points (plus d’actions) sélectionnez \> **Démarrer l’installation**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Comment voulez-vous connecter votre domaine ? page, sélectionnez **Continuer**.

1. Dans la page Ajouter des enregistrements DNS, **sélectionnez Ajouter des enregistrements DNS**.

1. Dans la page de connexion Cloudflare, connectez-vous à votre compte, puis sélectionnez **Autoriser**.

    Cela termine la configuration de votre domaine pour Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Créer des enregistrements DNS avec une configuration manuelle

Une fois ces enregistrements ajoutés sur Cloudflare, votre domaine est installé pour fonctionner avec Microsoft 365 services.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

> [!IMPORTANT]
> Vous devez effectuer cette procédure au niveau du bureau d'enregistrement de domaines auprès duquel vous avez acheté et inscrit votre domaine.

Lorsque vous vous êtes inscrit à Cloudflare, vous avez ajouté un domaine à l’aide du processus d’installation de Cloudflare.

Le domaine que vous avez ajouté a été acheté auprès de Cloudflare ou d’un bureau d’enregistrement de domaines distinct. Pour vérifier et créer des enregistrements DNS pour votre domaine dans Microsoft 365, vous devez d’abord modifier les serveurs de noms de votre bureau d’enregistrement de domaines afin qu’ils utilisent les serveurs de noms Cloudflare.

Pour modifier vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit.

1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.

2. Créez deux enregistrements de nameserver à l’aide des valeurs du tableau suivant, ou modifiez les enregistrements de nameserver existants afin qu’ils correspondent à ces valeurs.

    |Type|Valeur|
    |---|---|
    |Premier serveur de noms|Utilisez la valeur de nameserver fournie par Cloudflare.|
    |Deuxième serveur de noms|Utilisez la valeur de nameserver fournie par Cloudflare.|

    > [!TIP]
    > You should use at least two name server records. Si d’autres serveurs de noms sont répertoriés, vous devez les supprimer.

3. Enregistrez vos modifications.

> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Ensuite, votre messagerie Microsoft et d’autres services seront tous définies pour fonctionner avec votre domaine.

### <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.

> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement.

1. To get started, go to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine à mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page de gestion DNS, **sélectionnez +Ajouter un enregistrement**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type TXT dans la liste finale, puis tapez ou copiez-collez les valeurs de ce tableau.

    |Type|Nom|Durée de vie|Contenu|
    |---|---|---|:----|
    |TXT|@|30 minutes|MS=*msXXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

Maintenant que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous revenirz à Microsoft et recherchez l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

Pour vérifier l’enregistrement dans Microsoft 365 :

1. Dans le Centre d’administration, Paramètres  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**domaines**</a>.

1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer l’installation**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.

1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. To get started, go to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine à mettre à jour.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page de gestion DNS, **sélectionnez +Ajouter un enregistrement**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type MX dans la liste drop-down, puis tapez ou copiez-collez les valeurs de ce tableau.

   |Type|Nom|Serveur de messagerie|Durée de vie|Priorité|
   |---|---|---|---|---|
   |MX|@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Remarque :** Obtenez votre compte *\<domain-key\>* à partir Microsoft 365 client. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|30 minutes|1 <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/>|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Si d’autres enregistrements MX sont répertoriés dans la section **Enregistrements MX** , supprimez-les en sélectionnant **Modifier**, puis sélectionnez **Supprimer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="Sélectionnez Supprimer.":::

1. Dans la boîte de dialogue de confirmation, **sélectionnez Supprimer** pour confirmer vos modifications.

### <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. To get started, go to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine à mettre à jour.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page Gestion **DNS** , sélectionnez **+Ajouter un enregistrement**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type CNAME dans la liste drop-down, puis tapez ou copiez-collez les valeurs de ce tableau.

    |Type|Nom|Target|Durée de vie|
    |---|---|---|---|
    |CNAME|autodiscover|autodiscover.outlook.com|Auto|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft 365. Ajoutez plutôt les valeurs Microsoft 365 requises à l’enregistrement actuel afin de n’avoir qu’un *seul enregistrement* SPF qui inclut les deux ensembles de valeurs.

1. To get started, go to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine à mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page de gestion DNS, **sélectionnez +Ajouter un enregistrement**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type TXT dans la liste finale, puis tapez ou copiez-collez les valeurs de ce tableau.

    |Type|Nom|Durée de vie|Contenu|
    |---|---|---|---|
    |TXT|@|30 minutes|v=spf1 include:spf.protection.outlook.com -all <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Sélectionnez Enregistrer.":::

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que la conversation, les appels de conférence et les appels vidéo, en plus des Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

> [!IMPORTANT]
> N’oubliez pas que Cloudflare est responsable de la rendre disponible. Si vous constatez des différences entre les étapes ci-dessous et l’interface graphique graphique (INTERFACE utilisateur graphique) Cloudflare actuelle, tirez parti de [la](https://community.cloudflare.com/) Community.

1. To get started, go to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine à mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page Gestion DNS, sélectionnez **+Ajouter un enregistrement**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type SRV dans la liste drop-down, puis tapez ou copiez-collez les valeurs de ce tableau.

    |Type|Nom|Service|Protocole|Durée de vie|Priorité|Pondération|Port|Target|
    |---|---|---|---|---|---|---|---|---|
    |SRV|Utilisez votre *domain_name*; par exemple, contoso.com|_sip|TLS|30 minutes|100|1|443|sipfed.online.lync.com|
    |SRV|_sipfederationtls|TCP|Utilisez votre *domain_name*; par exemple, contoso.com|30 minutes|100|1|5061|sipfed.online.lync.com|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement SRV en copiant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. To get started, go to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine à mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page Gestion DNS, sélectionnez **+Ajouter un enregistrement**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type CNAME dans la liste drop-down, puis tapez ou copiez-collez les valeurs de ce tableau.

    |Type|Nom|Target|Durée de vie|
    |---|---|---|---|
    |CNAME|sip|sipdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 heure|
    |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils 2 enregistrements CNAME pour que les utilisateurs inscrivent des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. To get started, go to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine à mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page Gestion DNS, sélectionnez **+Ajouter un enregistrement**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type CNAME dans la liste drop-down, puis tapez ou copiez-collez les valeurs de ce tableau.

    |Type|Nom|Target|Durée de vie|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 heure|
    |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
