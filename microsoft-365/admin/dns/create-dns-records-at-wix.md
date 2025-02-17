---
title: Connecter vos enregistrements DNS sur Wix à Microsoft 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Découvrez comment vérifier votre domaine et configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online et d’autres services sur Wix pour Microsoft.
ms.openlocfilehash: 758c73eac3ca2dfb687635b1609d77049399b8ee
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68730422"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>Connecter vos enregistrements DNS sur Wix à Microsoft 365

**[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si Wix est votre fournisseur d’hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online, etc.

Une fois que vous avez ajouté ces enregistrements sur Wix, votre domaine est configuré pour fonctionner avec les services Microsoft.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant d’utiliser votre domaine avec Microsoft, nous devons nous assurer que vous le possédez. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que vous êtes propriétaire du domaine.

> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine, il n’a pas d’autre fonction. Vous pouvez le supprimer ultérieurement si vous le souhaitez.

> [!NOTE]
> WIX ne prend pas en charge les entrées DNS pour les sous-domaines.

1. Pour commencer, accédez à la page de vos domaines sur Wix à l’aide [de ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

2. Sélectionnez **Domaines** \> **...**, puis **Gérer les enregistrements DNS** dans la liste déroulante.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste déroulante.":::

3. Sélectionnez **+ Ajouter un enregistrement** dans la ligne **TXT (Texte)** de l’éditeur DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

4. In the boxes for the new record, type or copy and paste the values from the following table.

   |Nom d’hôte|TXT Value|Durée de vie|
   |---|---|---|
   |Renseigné automatiquement (laissez vide)|MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 Hour|

5. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Sélectionnez Enregistrer.":::

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

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. Pour commencer, accédez à la page de vos domaines sur Wix à l’aide [de ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

1. Sélectionnez **Domaines** \> **...**, puis **Gérer les enregistrements DNS** dans la liste déroulante.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste déroulante.":::

1. Sous **MX (Échange de courrier),** sélectionnez **Modifier les enregistrements MX**.

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="Sélectionnez Modifier les enregistrements MX.":::

1. Choisissez **Autre** dans la liste déroulante, puis sélectionnez **+ Ajouter un enregistrement**.

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="Sélectionnez Autre dans la liste déroulante.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :

   |Nom d’hôte|Points to |Priorité|Durée de vie|
   |---|---|---|---|
   |Renseigné automatiquement|*\<domain-key\>*.mail.protection.outlook.com <br/> **Note:** Obtenez votre à *\<domain-key\>* partir de votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|0 <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml).|1 Hour|

1. Si d’autres enregistrements MX sont répertoriés, supprimez chacun d’eux.

  :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="Sélectionnez Supprimer.":::

1. Sélectionnez **Enregistrer**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines sur Wix à l’aide [de ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

2. Sélectionnez **Domaines** \> **...**, puis **Gérer les enregistrements DNS** dans la liste déroulante.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste déroulante.":::

3. Sélectionnez **+ Ajouter un enregistrement** dans la ligne **CNAME (Alias)** de l’éditeur DNS pour l’enregistrement CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Sélectionnez + Ajouter un enregistrement.":::

4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :

   |Nom d’hôte|Valeur|Durée de vie|
   |---|---|---|
   |autodiscover|autodiscover.outlook.com|1 Hour|

5. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Au lieu de cela, ajoutez les valeurs Microsoft requises à l’enregistrement actif afin d’avoir un *seul* enregistrement SPF qui inclut les deux jeux de valeurs.

1. Pour commencer, accédez à la page de vos domaines sur Wix à l’aide [de ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

2. Sélectionnez **Domaines** \> **...**, puis **Gérer les enregistrements DNS** dans la liste déroulante.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste déroulante.":::

3. Sélectionnez **+ Ajouter un enregistrement** dans la ligne **TXT (Texte)** de l’éditeur DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Sélectionnez + Ajouter un enregistrement.":::

   **Remarque** : Wix fournit une ligne SPF dans l’éditeur DNS. Ignorez cette ligne et utilisez la ligne **TXT (Text)** pour entrer les valeurs SPF ci-dessous.

4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :

   |Nom d’hôte|Valeur|Durée de vie|
   |---|---|---|
   |[Laissez ce champ vide]|v=spf1 include:spf.protection.outlook.com -all <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|1 Hour|

5. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Sélectionnez Enregistrer.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversations, les téléconférences et les appels vidéo, en plus de Microsoft Teams. Skype a besoin de quatre enregistrements : deux enregistrements SRV pour la communication utilisateur à utilisateur et deux enregistrements CNAME pour se connecter et connecter les utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines sur Wix à l’aide [de ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

1. Sélectionnez **Domaines** \> **...**, puis **Gérer les enregistrements DNS** dans la liste déroulante.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste déroulante.":::

1. Sélectionnez **+ Ajouter un enregistrement** dans la ligne **SRV** de l’éditeur DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="Sélectionnez + Ajouter un enregistrement.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau :

   |Service|Protocole|Nom d’hôte|Pondération|Port|Target|Priorité|Durée de vie|
   |---|---|---|---|---|---|---|---|
   |sip|tls|Renseigné automatiquement|1|443|sipdir.online.lync.com|100|1 Hour|
   |sipfed|tcp|Renseigné automatiquement|1|5061|sipfed.online.lync.com|100|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement SRV en copiant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Ajoutez les deux enregistrements CNAME requis pour Skype Entreprise

1. Sélectionnez **+ Ajouter un autre** dans la ligne **CNAME (Alias)** de l’éditeur DNS, puis entrez les valeurs de la première ligne du tableau suivant.

   |Type|Hôte|Valeur|Durée de vie|
   |---|---|---|---|
   |CNAME|sip|sipdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|
   |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils a besoin de deux enregistrements CNAME pour permettre aux utilisateurs d’inscrire des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. Pour commencer, accédez à la page de vos domaines sur Wix à l’aide [de ce lien](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

1. Sélectionnez **Domaines** \> **...**, puis **Gérer les enregistrements DNS** dans la liste déroulante.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste déroulante.":::

1. Sélectionnez **+ Ajouter un enregistrement** dans la ligne **CNAME (Alias)** de l’éditeur DNS pour l’enregistrement CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Sélectionnez + Ajouter un enregistrement.":::

1. Entrez les valeurs de la première ligne du tableau suivant.

    |Type|Hôte|Valeur|Durée de vie|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|
    |CNAME|enterpriseenrollment|enterpriseenrollment.manage.microsoft.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).
