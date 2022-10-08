---
title: Connecter vos enregistrements DNS à IONOS par 1&1 à Microsoft 365
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: Découvrez comment vérifier votre domaine et configurer des enregistrements DNS pour les e-mails, Skype Entreprise Online et d’autres services à l’adresse 1&1 IONOS pour Microsoft.
ms.openlocfilehash: a17ee719f51dcd736e83c65beb7ff9a2073816fb
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68187402"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>Connecter vos enregistrements DNS à IONOS par 1&1 à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si IONOS par 1&1 est votre fournisseur d’hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online, et ainsi de suite.

## <a name="before-you-begin"></a>Avant de commencer

Vous avez deux options pour configurer des enregistrements DNS pour votre domaine :

- [**Utiliser Domain Connect**](#use-domain-connect-to-verify-and-set-up-your-domain) Si vous n’avez pas configuré votre domaine avec un autre fournisseur de services de messagerie, suivez les étapes de Connexion au domaine pour vérifier et configurer automatiquement votre nouveau domaine à utiliser avec Microsoft 365.

    OR

- [**Utiliser les étapes manuelles**](#create-dns-records-with-manual-setup) Vérifiez votre domaine en suivant les étapes manuelles ci-dessous et choisissez quand et quels enregistrements ajouter à votre bureau d’enregistrement de domaines. Cela vous permet de configurer de nouveaux enregistrements MX (courrier), par exemple, à votre convenance.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Utiliser Domain Connect pour vérifier et configurer votre domaine

Procédez comme suit pour vérifier et configurer automatiquement votre IONOS par 1&1 domaine avec Microsoft 365 :

1. Dans le Centre d'administration Microsoft 365, sélectionnez **Domaines de paramètres** > , puis sélectionnez le domaine que vous souhaitez configurer.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-1.png" alt-text="Sélectionnez votre domaine dans Microsoft 365.":::

1. Sélectionnez les trois points (autres actions) > **choisissez Démarrer l’installation**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Sur la page Comment voulez-vous connecter votre domaine ? page, **sélectionnez Continuer**.

1. Dans la page Ajouter des enregistrements DNS, **sélectionnez Ajouter des enregistrements DNS**.

1. Dans la page de connexion IONOS par 1&1, connectez-vous à votre compte, puis **sélectionnez Se connecter** et **Autoriser**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-3.png" alt-text="Sélectionnez Se connecter, puis Autoriser.":::

    Cela termine la configuration de votre domaine pour Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Créer des enregistrements DNS avec une configuration manuelle

Une fois ces enregistrements ajoutés à IONOS par 1&1, votre domaine est configuré pour fonctionner avec les services Microsoft.

> [!CAUTION]
> Notez qu’IONOS de 1&1 n’autorise pas un domaine à avoir à la fois un enregistrement MX et un enregistrement CNAME de découverte automatique de niveau supérieur. Cela limite les méthodes qui s'offrent à vous pour configurer Exchange Online pour Microsoft. Il existe une solution de contournement, mais nous vous recommandons de l’utiliser **uniquement** si vous avez déjà de l’expérience dans la création de sous-domaines à IONOS par 1&1.
> Si, malgré cette [limitation de service](../setup/domains-faq.yml), vous choisissez de gérer vos propres enregistrements DNS Microsoft sur IONOS par 1&1, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online, et ainsi de suite.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. Pour commencer, accédez à la page de vos domaines sur IONOS par 1&1 à l’aide de [ce lien](https://my.1and1.com/). Vous serez invité à vous connecter.

1. Sélectionnez **Menu**, puis **Domaines et SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::

1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste déroulante.":::

1. Sélectionnez **Ajouter un enregistrement**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez la section **TXT** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-4.png" alt-text="Sélectionnez la section TXT.":::

1. Dans la page Ajouter un enregistrement DNS, dans les zones du nouvel enregistrement, tapez ou copiez et collez les valeurs du tableau suivant.

    |Nom d’hôte|Valeur|Durée de vie|
    |---|---|---|
    |(Laissez ce champ vide)|MS=ms *XXXXXXXX*  <br/> REMARQUE : Il s’agit d’un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 heure|

1. Sélectionnez **Enregistrer**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-5.png" alt-text="Sélectionnez Enregistrer.":::

    Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Microsoft 365 et demandez à Microsoft 365 de rechercher l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

Pour vérifier l’enregistrement dans Microsoft 365 :

1. Dans le centre d’administration, accédez aux <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**domaines**</a> **de paramètres**\>.

1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis **sélectionnez Démarrer l’installation**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.

1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

> [!NOTE]
> Si vous vous êtes inscrit auprès de 1und1.de, [connectez-vous ici](https://go.microsoft.com/fwlink/?linkid=859152).

1. Pour commencer, accédez à la page de vos domaines sur IONOS par 1&1 à l’aide de [ce lien](https://my.1and1.com/). Vous serez invité à vous connecter.

1. Sélectionnez **Menu**, puis **Domaines et SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::

1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste déroulante.":::

1. Sélectionnez **Ajouter un enregistrement**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez la section **MX** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX.png" alt-text="Sélectionnez la section MX.":::

1. Dans la page Ajouter un enregistrement DNS, dans les zones du nouvel enregistrement, tapez ou copiez et collez les valeurs du tableau suivant.

    |Nom d’hôte|Points to |Priorité|Durée de vie|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com  <br/>  REMARQUE : Obtenez votre \<domain-key\> fichier à partir de votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|10  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml).|1 heure|

1. Sélectionnez **Enregistrer**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX-Save.png" alt-text="Sélectionnez Enregistrer.":::

1. S’il existe des enregistrements MX déjà répertoriés, supprimez chacun d’eux en sélectionnant la corbeille **Supprimer l’enregistrement** dans la page **Ajouter un enregistrement** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Delete.png" alt-text="Sélectionnez Supprimer l’enregistrement.":::

### <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

> [!NOTE]
> Si vous vous êtes inscrit auprès de 1und1.de, [connectez-vous ici](https://go.microsoft.com/fwlink/?linkid=859152).

1. Pour commencer, accédez à la page de vos domaines sur IONOS par 1&1 à l’aide de [ce lien](https://my.1and1.com/). Vous serez invité à vous connecter.

1. Sélectionnez **Menu**, puis **Domaines et SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::

1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste déroulante.":::

   Vous allez maintenant créer deux sous-domaines et définir une valeur **Alias (Alias)** pour chaque sous-domaine.

   (Cela est nécessaire, car 1&1 IONOS ne prend en charge qu’un seul enregistrement CNAME de niveau supérieur, mais Microsoft requiert plusieurs enregistrements CNAME.)

   Tout d'abord, vous devez créer le sous-domaine de découverte automatique.

1. Sélectionnez **Sous-domaines**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Sélectionnez Sous-domaine.":::

1. Sélectionnez **Ajouter un sous-domaine**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Sélectionnez Ajouter des sous-domaines.":::

1. Dans la zone **Ajouter un sous-domaine** pour le nouveau sous-domaine, tapez ou copiez et collez uniquement la valeur **Ajouter un sous-domaine** du tableau suivant. (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)

    |Ajouter un sous-domaine|Alias|
    |---|---|
    |autodiscover|autodiscover.outlook.com|

1. Sous **Actions** pour le sous-domaine de **découverte automatique** que vous venez de créer, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS** dans la liste déroulante.

1. Sélectionnez **Ajouter un enregistrement**, puis sélectionnez la section **CNAME** .

1. Dans la zone **Alias :**, tapez ou copiez-collez uniquement la valeur **Alias** du tableau suivant.

    |Ajouter un sous-domaine|Alias|
    |---|---|
    |autodiscover|autodiscover.outlook.com|

1. Sélectionnez **Enregistrer**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](../../enterprise/external-domain-name-system-records.md). Pour valider votre enregistrement SPF, vous pouvez utiliser l’un de ces[outils de validation SPF](../setup/domains-faq.yml).

> [!NOTE]
> Si vous vous êtes inscrit auprès de 1und1.de, [connectez-vous ici](https://go.microsoft.com/fwlink/?linkid=859152).

1. Pour commencer, accédez à la page de vos domaines sur IONOS par 1&1 à l’aide de [ce lien](https://my.1and1.com/). Vous serez invité à vous connecter.

1. Sélectionnez **Menu**, puis **Domaines et SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::

1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste déroulante.":::

1. Sélectionnez **Ajouter un enregistrement**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez la section **SPF (TXT** ).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT.png" alt-text="Sélectionnez la section SPF (TXT).":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    |Type|Nom d’hôte|Valeur|Durée de vie|
    |---|---|---|---|
    |SPF (TXT)|(Leave this field empty.)|v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|1 heure|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT-Save.png" alt-text="Sélectionnez Enregistrer.":::

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que la conversation, les téléconférences et les appels vidéo, en plus de Microsoft Teams. Skype a besoin de 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur-utilisateur et 2 enregistrements CNAME pour se connecter et connecter les utilisateurs au service.

### <a name="add-two-additional-cname-records"></a>Ajouter deux enregistrements CNAME supplémentaires

1. Pour commencer, accédez à la page de vos domaines sur IONOS par 1&1 à l’aide de [ce lien](https://my.1and1.com/). Vous serez invité à vous connecter.

1. Sélectionnez **Menu**, puis **Domaines et SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::

1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste déroulante.":::

   Vous allez maintenant créer deux sous-domaines et définir une valeur **Alias (Alias)** pour chaque sous-domaine.

   (Cela est nécessaire, car 1&1 IONOS ne prend en charge qu’un seul enregistrement CNAME de niveau supérieur, mais Microsoft requiert plusieurs enregistrements CNAME.)

   Tout d’abord, vous allez créer le sous-domaine lyncdiscover.

1. Sélectionnez **Sous-domaines**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Sélectionnez Sous-domaine.":::

1. Sélectionnez **Ajouter un sous-domaine**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Sélectionnez Ajouter des sous-domaines.":::

1. Dans la zone **Ajouter un sous-domaine** pour le nouveau sous-domaine, tapez ou copiez et collez uniquement la valeur **Ajouter un sous-domaine** du tableau suivant. (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)

    |Ajouter un sous-domaine|Alias|
    |---|---|
    |lyncdiscover   |webdir.online.lync.com  |

1. Sous **Actions** pour le sous-domaine **lyncdiscover** que vous venez de créer, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS** dans la liste déroulante.

1. Sélectionnez **Ajouter un enregistrement**, puis sélectionnez la section **CNAME** .

1. Dans la zone **Alias :**, tapez ou copiez-collez uniquement la valeur **Alias** du tableau suivant.

    |Create Subdomain (Créer un sous-domaine)|Alias|
    |---|---|
    |lyncdiscover|webdir.online.lync.com|

1. Créer un autre sous-domaine (SIP) : sélectionnez **Ajouter un sous-domaine**.

1. Dans la zone **Ajouter un sous-domaine** pour le nouveau sous-domaine, tapez ou copiez et collez uniquement la valeur **Ajouter un sous-domaine** du tableau suivant. (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)

    |Ajouter un sous-domaine|Alias|
    |---|---|
    |sip|sipdir.online.lync.com|

1. Sous **Actions** pour le sous-domaine que vous venez de créer, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS** dans la liste déroulante.

1. Sélectionnez **Ajouter un enregistrement**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez la section **CNAME** .

1. dans la zone **Alias :** tapez ou copiez et collez uniquement la valeur **Alias** du tableau suivant.

    |Create Subdomain (Créer un sous-domaine)|Alias|
    |---|---|
    |sip|sipdir.online.lync.com|

1. Cochez la case correspondant à la clause d'exclusion de responsabilité **J'accepte**, puis sélectionnez **Enregistrer**.

## <a name="add-the-two-srv-records-required-for-microsoft"></a>Ajouter les deux enregistrements SRV requis pour Microsoft

> [!NOTE]
> Si vous vous êtes inscrit auprès de 1und1.de, [connectez-vous ici](https://go.microsoft.com/fwlink/?linkid=859152).

1. Pour commencer, accédez à la page de vos domaines sur IONOS par 1&1 à l’aide de [ce lien](https://my.1and1.com/). Vous serez invité à vous connecter.

1. Sélectionnez **Menu**, puis **Domaines et SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::

1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste déroulante.":::

1. Sélectionnez **Ajouter un enregistrement**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez la section **SRV** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV.png" alt-text="Sélectionnez la section SRV.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    |Type|Service|Protocole|Nom d’hôte|Points to |Priorité|Pondération|Port|Durée de vie|
    |---|---|---|---|---|---|---|---|---|
    |SRV|_sip|tls|(Laissez ce champ vide.)|sipdir.online.lync.com|100|1|443|1 heure|
    |SRV|_sipfederationtls|tcp|(Laissez ce champ vide.)|sipfed.online.lync.com|100|1|5061|1 heure|

1. Sélectionnez **Enregistrer**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV-Save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement SRV.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils a besoin de 2 enregistrements CNAME pour permettre aux utilisateurs d’inscrire des appareils auprès du service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

> [!IMPORTANT]
> Suivez la procédure de sous-domaine que vous avez utilisée pour les autres enregistrements CNAME et fournissez les valeurs du tableau suivant.

1. Pour commencer, accédez à la page de vos domaines sur IONOS par 1&1 à l’aide de [ce lien](https://my.1and1.com/). Vous serez invité à vous connecter.

1. Sélectionnez **Menu**, puis **Domaines et SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Sélectionnez Domaines et SSL.":::

1. Sous **Actions** pour le domaine que vous souhaitez mettre à jour, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Sélectionnez DNS dans la liste déroulante.":::

   Vous allez maintenant créer deux sous-domaines et définir une valeur **Alias (Alias)** pour chaque sous-domaine.

   (Cela est nécessaire, car 1&1 IONOS ne prend en charge qu’un seul enregistrement CNAME de niveau supérieur, mais Microsoft requiert plusieurs enregistrements CNAME.)

   Tout d’abord, vous allez créer le sous-domaine lyncdiscover.

1. Sélectionnez **Sous-domaines**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Sélectionnez Sous-domaine.":::

1. Sélectionnez **Ajouter un sous-domaine**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Sélectionnez Ajouter des sous-domaines.":::

1. Dans la zone **Ajouter un sous-domaine** pour le nouveau sous-domaine, tapez ou copiez et collez uniquement la valeur **Ajouter un sous-domaine** du tableau suivant. (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)

    |Ajouter un sous-domaine|Alias|
    |---|---|
    |enterpriseregistration|enterpriseregistration.windows.net|

1. Sous **Actions** pour le sous-domaine **enterpriseregistration** que vous venez de créer, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS** dans la liste déroulante.

1. Sélectionnez **Ajouter un enregistrement**, puis sélectionnez la section **CNAME** .

1. Dans la zone **Alias :**, tapez ou copiez-collez uniquement la valeur **Alias** du tableau suivant.

    |Ajouter un sous-domaine|Alias|
    |---|---|
    |enterpriseregistration|enterpriseregistration.windows.net|

1. Créez un autre sous-domaine : sélectionnez **Ajouter un sous-domaine**.

1. Dans la zone **Ajouter un sous-domaine** pour le nouveau sous-domaine, tapez ou copiez et collez uniquement la valeur **Ajouter un sous-domaine** du tableau suivant. (Vous ajouterez la valeur **Alias (Alias)** au cours d'une étape ultérieure.)

    |Ajouter un sous-domaine|Alias|
    |---|---|
    |enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|

1. Sous **Actions** pour le sous-domaine **enterpriseenrollment** que vous venez de créer, sélectionnez le contrôle d’engrenage, puis sélectionnez **DNS** dans la liste déroulante.

1. Sélectionnez **Ajouter un enregistrement**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

1. Sélectionnez la section **CNAME** .

1. dans la zone **Alias :** tapez ou copiez et collez uniquement la valeur **Alias** du tableau suivant.

    |Create Subdomain (Créer un sous-domaine)|Alias|
    |---|---|
    |enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|

1. Cochez la case correspondant à la clause d'exclusion de responsabilité **J'accepte**, puis sélectionnez **Enregistrer**.
