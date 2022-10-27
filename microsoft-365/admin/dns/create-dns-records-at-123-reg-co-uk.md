---
title: Connecter vos enregistrements DNS à 123-reg.co.uk à Microsoft 365
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
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: Découvrez comment vérifier votre domaine et configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online et d’autres services sur 123-reg.co.uk pour Microsoft.
ms.openlocfilehash: ff9ba53b60f3eb2ccbf2b8e5ddcaab5543e4e8ae
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729520"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>Connecter vos enregistrements DNS à 123-reg.co.uk à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si 123-reg.co.uk est votre fournisseur d'hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

Une fois que vous avez ajouté ces enregistrements à 123-reg.co.uk, votre domaine est configuré pour fonctionner avec les services Microsoft.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.

2. Sélectionnez **Domaines**, puis, dans la page Vue d’ensemble du nom de domaine, sélectionnez le nom du domaine que vous souhaitez vérifier ou accédez au Panneau de configuration.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le domaine que vous souhaitez vérifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés**, choisissez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

4. Dans la page Gérer votre DNS, sélectionnez l’onglet **DNS avancé** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::

5. Dans la zone **Type** du nouvel enregistrement, choisissez **TXT/SPF** dans la liste déroulante, puis tapez ou copiez et collez les autres valeurs du tableau suivant.

    |Hostname (Nom d'hôte)|Type|Destination TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Sélectionnez le type TXT/SPF dans la liste déroulante, puis renseignez les valeurs.":::

6. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Sélectionnez Ajouter.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

Maintenant que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous allez revenir à Microsoft et demander une recherche pour l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

Pour vérifier l’enregistrement dans Microsoft 365 :

1. Dans le Centre d’administration, accédez aux **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>.

1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer l’installation**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.

1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.

2. On the Domain name overview page, select the name of the domain that you want to edit.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez modifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés**, choisissez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

4. Dans la page Gérer votre DNS, sélectionnez l’onglet **DNS avancé** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::

5. Dans la zone **Type** du nouvel enregistrement, choisissez **MX** dans la liste déroulante, puis tapez ou copiez et collez les autres valeurs du tableau suivant.

    |Hostname (Nom d'hôte)|Type (Type)|Priorité|Destination MX (Enregistrement MX de la destination)|
    |---|---|---|---|
    |@|MX|1 <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml).|*\<domain-key\>*.mail.protection.outlook.com. <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> **Remarque :** Obtenez votre \<domain-key\> depuis votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="Sélectionnez le type MX dans la liste déroulante, puis renseignez les valeurs.":::

6. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="Sélectionnez Ajouter.":::

7. S’il existe d’autres enregistrements MX, supprimez-les en sélectionnant l’icône **Supprimer (corbeille)** pour cet enregistrement.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="Sélectionnez Supprimer (corbeille).":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.

2. On the Domain name overview page, select the name of the domain that you want to edit.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez modifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés**, choisissez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

4. Dans la page Gérer votre DNS, sélectionnez l’onglet **DNS avancé** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::

5. Ajoutez l’enregistrement CNAME.

    Dans la zone **Type** du nouvel enregistrement, choisissez **CNAME** dans la liste déroulante, puis tapez ou copiez et collez les autres valeurs du tableau suivant.

    |Hostname (Nom d'hôte)|Type|Destination CNAME (Enregistrement CNAME de la destination)|
    |---|---|---|
    |autodiscover|CNAME|autodiscover.outlook.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Sélectionnez le type CNAME dans la liste déroulante, puis renseignez les valeurs.":::

6. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Sélectionnez Ajouter.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous disposez déjà d’un enregistrement SPF pour votre domaine, n’en créez pas un pour Microsfot. Au lieu de cela, ajoutez les valeurs Microsoft requises à l’enregistrement actif afin d’avoir un *seul* enregistrement SPF qui inclut les deux jeux de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](../../enterprise/external-domain-name-system-records.md). To validate your SPF record, you can use one of these [SPF validation tools](../setup/domains-faq.yml).

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.

2. On the Domain name overview page, select the name of the domain that you want to edit.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez modifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés**, choisissez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

4. Dans la page Gérer votre DNS, sélectionnez l’onglet **DNS avancé** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::

5. Dans la zone **Type** du nouvel enregistrement, choisissez **TXT/SPF** dans la liste déroulante, puis tapez ou copiez et collez les autres valeurs du tableau suivant.

    |Hostname (Nom d'hôte)|Type|Destination TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|v=spf1 include:spf.protection.outlook.com -all <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Sélectionnez le type TXT/SPF dans la liste déroulante, puis renseignez les valeurs.":::

6. Sélectionnez **Ajouter**.

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversations, les téléconférences et les appels vidéo, en plus de Microsoft Teams. Skype a besoin de 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter les utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.

2. On the Domain name overview page, select the name of the domain that you want to edit.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez modifier.":::

3. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés**, choisissez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

4. Dans la page Gérer votre DNS, sélectionnez l’onglet **DNS avancé** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::

5. Ajoutez le premier des deux enregistrements SRV :

   Dans la zone **Type** du nouvel enregistrement, choisissez **SRV** dans la liste déroulante, puis tapez ou copiez et collez les autres valeurs du tableau suivant.

    |Hostname (Nom d'hôte)|Type (Type)|Priority (Priorité)|TTL (Durée de vie)|Destination SRV (Enregistrement SRV de la destination)|
    |---|---|---|---|---|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **Cette valeur DOIT se terminer par un point (.)** <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **Cette valeur DOIT se terminer par un point (.)** <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Sélectionnez le type TXT/SPF dans la liste déroulante, puis renseignez les valeurs.":::

6. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Sélectionnez Ajouter.":::

7. Ajoutez l’autre enregistrement SRV.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Ajoutez les deux enregistrements CNAME requis pour Skype Entreprise

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.

1. On the Domain name overview page, select the name of the domain that you want to edit.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez modifier.":::

1. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés**, choisissez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Dans la page Gérer votre DNS, sélectionnez l’onglet **DNS avancé** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::

1. Ajoutez le premier enregistrement CNAME.

    Dans la zone **Type** du nouvel enregistrement, choisissez **CNAME** dans la liste déroulante, puis tapez ou copiez et collez les autres valeurs du tableau suivant.

    |Hostname (Nom d'hôte)|Type|Destination CNAME (Enregistrement CNAME de la destination)|
    |---|---|---|
    |sip|CNAME|sipdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|
    |lyncdiscover|CNAME|webdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Sélectionnez le type CNAME dans la liste déroulante, puis renseignez les valeurs.":::

1. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Sélectionnez Ajouter.":::

1. Ajoutez l’autre enregistrement CNAME.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils a besoin de deux enregistrements CNAME pour permettre aux utilisateurs d’inscrire des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. Pour commencer, accédez à la page de vos domaines sur le site 123-reg.co.uk en utilisant [ce lien](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Avant toute chose, vous serez invité à vous connecter.

1. On the Domain name overview page, select the name of the domain that you want to edit.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez modifier.":::

1. Dans la page Gérer le domaine, sous **Paramètres de domaine avancés**, choisissez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Dans la page Gérer votre DNS, sélectionnez l’onglet **DNS avancé** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Sélectionnez l’onglet DNS avancé.":::

1. Ajoutez le premier enregistrement CNAME.

    Dans la zone **Type** du nouvel enregistrement, choisissez **CNAME** dans la liste déroulante, puis tapez ou copiez et collez les autres valeurs du tableau suivant.

   |Hostname (Nom d'hôte)|Type|Destination CNAME (Enregistrement CNAME de la destination)|
   |---|---|---|
   |enterpriseregistration|CNAME|enterpriseregistration.windows.net. <br/> **Cette valeur DOIT se terminer par un point (.)**|
   |enterpriseenrollment|CNAME|enterpriseenrollment.manage.microsoft.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Sélectionnez le type CNAME dans la liste déroulante, puis renseignez les valeurs.":::

1. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Sélectionnez Ajouter.":::

1. Ajoutez l’autre enregistrement CNAME.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).
