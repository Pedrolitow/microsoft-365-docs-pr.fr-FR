---
title: Connecter vos enregistrements DNS à Cloudflare à Microsoft 365
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Découvrez comment vérifier votre domaine et configurer des enregistrements DNS pour les e-mails, les Skype Entreprise Online et d’autres services chez Cloudflare pour Microsoft.
ms.openlocfilehash: 29a0d6dc6c4ed0f3372c78728894ab4dc9ec6e6a
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729872"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>Connecter vos enregistrements DNS à Cloudflare à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si Cloudflare est votre fournisseur d’hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype Entreprise Online, etc.

## <a name="before-you-begin"></a>Avant de commencer

Vous avez deux options pour configurer des enregistrements DNS pour votre domaine :

- [**Utiliser Domain Connect**](#use-domain-connect-to-verify-and-set-up-your-domain) Si vous n’avez pas configuré votre domaine avec un autre fournisseur de services de messagerie, suivez les étapes connexion au domaine pour vérifier et configurer automatiquement votre nouveau domaine à utiliser avec Microsoft 365.

    OR

- [**Utiliser les étapes manuelles**](#create-dns-records-with-manual-setup) Vérifiez votre domaine à l’aide des étapes manuelles ci-dessous et choisissez quand et quels enregistrements ajouter à votre bureau d’enregistrement de domaines. Cela vous permet de configurer de nouveaux enregistrements MX (mail), par exemple, à votre convenance.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Utiliser Domain Connect pour vérifier et configurer votre domaine

Procédez comme suit pour vérifier et configurer automatiquement votre domaine Cloudflare avec Microsoft 365 :

1. Dans la Centre d'administration Microsoft 365, sélectionnez **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>, puis sélectionnez le domaine que vous souhaitez configurer.

1. Sélectionnez les trois points (plus d’actions) \> choisissez **Démarrer la configuration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Dans comment voulez-vous connecter votre domaine ? , sélectionnez **Continuer**.

1. Dans la page Ajouter des enregistrements DNS, sélectionnez **Ajouter des enregistrements DNS**.

1. Dans la page de connexion à Cloudflare, connectez-vous à votre compte, puis sélectionnez **Autoriser**.

    Cette opération termine la configuration de votre domaine pour Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Créer des enregistrements DNS avec une configuration manuelle

Après avoir ajouté ces enregistrements à Cloudflare, votre domaine est configuré pour fonctionner avec les services Microsoft 365.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

### <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

> [!IMPORTANT]
> Vous devez effectuer cette procédure au niveau du bureau d'enregistrement de domaines auprès duquel vous avez acheté et inscrit votre domaine.

Lorsque vous vous êtes inscrit à Cloudflare, vous avez ajouté un domaine à l’aide du processus d’installation de Cloudflare.

Le domaine que vous avez ajouté a été acheté auprès de Cloudflare ou d’un bureau d’enregistrement de domaines distinct. Pour vérifier et créer des enregistrements DNS pour votre domaine dans Microsoft 365, vous devez d’abord modifier les serveurs de noms de votre bureau d’enregistrement de domaines afin qu’ils utilisent les serveurs de noms Cloudflare.

Pour modifier vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit.

1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.

2. Créez deux enregistrements de serveur de noms en utilisant les valeurs du tableau suivant, ou modifiez les enregistrements de serveur de noms existants afin qu’ils correspondent à ces valeurs.

    |Type|Valeur|
    |---|---|
    |Premier serveur de noms|Utilisez la valeur de serveur de noms fournie par Cloudflare.|
    |Deuxième serveur de noms|Utilisez la valeur de serveur de noms fournie par Cloudflare.|

    > [!TIP]
    > You should use at least two name server records. Si d’autres serveurs de noms sont répertoriés, vous devez les supprimer.

3. Enregistrez vos modifications.

> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Votre messagerie Microsoft et d’autres services seront alors prêts à fonctionner avec votre domaine.

### <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. Pour commencer, accédez à la page de vos domaines sur Cloudflare à l’aide [de ce lien](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine que vous souhaitez mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page gestion DNS, sélectionnez **+Ajouter un enregistrement**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type TXT dans la liste déroulante, puis tapez ou copiez et collez les valeurs de cette table.

    |Type|Nom|Durée de vie|Contenu|
    |---|---|---|:----|
    |TXT|@|30 minutes|MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

Maintenant que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous allez revenir à Microsoft et rechercher l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

Pour vérifier l’enregistrement dans Microsoft 365 :

1. Dans le Centre d’administration, accédez aux **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>.

1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer l’installation**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.

1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. Pour commencer, accédez à la page de vos domaines sur Cloudflare à l’aide [de ce lien](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine que vous souhaitez mettre à jour.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page gestion DNS, sélectionnez **+Ajouter un enregistrement**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type MX dans la liste déroulante, puis tapez ou copiez et collez les valeurs de cette table.

   |Type|Nom|Serveur de messagerie|Durée de vie|Priorité|
   |---|---|---|---|---|
   |MX|@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Note:** Obtenez votre à *\<domain-key\>* partir de votre compte Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|30 minutes|1 <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/>|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Si d’autres enregistrements MX sont répertoriés dans la section **Enregistrements MX** , supprimez-les en sélectionnant **Modifier**, puis **Supprimer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="Sélectionnez Supprimer.":::

1. Dans la boîte de dialogue de confirmation, sélectionnez **Supprimer** pour confirmer vos modifications.

### <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines sur Cloudflare à l’aide [de ce lien](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine que vous souhaitez mettre à jour.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page **de gestion DNS** , sélectionnez **+Ajouter un enregistrement**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type CNAME dans la liste déroulante, puis tapez ou copiez et collez les valeurs de cette table.

    |Type|Nom|Target|Durée de vie|
    |---|---|---|---|
    |CNAME|autodiscover|autodiscover.outlook.com|Auto|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft 365. Au lieu de cela, ajoutez les valeurs Microsoft 365 requises à l’enregistrement actif afin d’avoir un enregistrement SPF *unique* qui inclut les deux jeux de valeurs.

1. Pour commencer, accédez à la page de vos domaines sur Cloudflare à l’aide [de ce lien](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine que vous souhaitez mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page gestion DNS, sélectionnez **+Ajouter un enregistrement**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type TXT dans la liste déroulante, puis tapez ou copiez et collez les valeurs de cette table.

    |Type|Nom|Durée de vie|Contenu|
    |---|---|---|---|
    |TXT|@|30 minutes|v=spf1 include:spf.protection.outlook.com -all <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Sélectionnez Enregistrer.":::

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversations, les téléconférences et les appels vidéo, en plus de Microsoft Teams. Skype a besoin de 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter les utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

> [!IMPORTANT]
> Gardez à l’esprit que Cloudflare est responsable de la mise à disposition de cette fonctionnalité. Si vous voyez des différences entre les étapes ci-dessous et l’interface utilisateur graphique de Cloudflare actuelle, tirez parti de la [communauté Cloudflare](https://community.cloudflare.com/).

1. Pour commencer, accédez à la page de vos domaines sur Cloudflare à l’aide [de ce lien](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine que vous souhaitez mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page de gestion DNS, sélectionnez **+Ajouter un enregistrement**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type SRV dans la liste déroulante, puis tapez ou copiez et collez les valeurs de ce tableau.

    |Type|Nom|Service|Protocole|Durée de vie|Priorité|Pondération|Port|Target|
    |---|---|---|---|---|---|---|---|---|
    |SRV|Utilisez votre *domain_name* ; par exemple, contoso.com|_sip|TLS|30 minutes|100|1|443|sipfed.online.lync.com|
    |SRV|Utilisez votre *domain_name* ; par exemple, contoso.com|_sipfederationtls|TCP|30 minutes|100|1|5061|sipfed.online.lync.com|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement SRV en copiant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Ajoutez les deux enregistrements CNAME requis pour Skype Entreprise

1. Pour commencer, accédez à la page de vos domaines sur Cloudflare à l’aide [de ce lien](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine que vous souhaitez mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page de gestion DNS, sélectionnez **+Ajouter un enregistrement**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type CNAME dans la liste déroulante, puis tapez ou copiez et collez les valeurs de cette table.

    |Type|Nom|Target|Durée de vie|
    |---|---|---|---|
    |CNAME|sip|sipdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|
    |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils a besoin de 2 enregistrements CNAME pour permettre aux utilisateurs d’inscrire des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. Pour commencer, accédez à la page de vos domaines sur Cloudflare à l’aide [de ce lien](https://www.cloudflare.com/a/login). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sélectionnez le domaine que vous souhaitez mettre à jour.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez mettre à jour.":::

1. Dans la page Vue d’ensemble de votre domaine, sélectionnez **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Sélectionnez DNS.":::

1. Dans la page de gestion DNS, sélectionnez **+Ajouter un enregistrement**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez le type CNAME dans la liste déroulante, puis tapez ou copiez et collez les valeurs de cette table.

    |Type|Nom|Target|Durée de vie|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|
    |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).
