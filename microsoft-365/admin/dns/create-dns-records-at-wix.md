---
title: Connecter vos enregistrements DNS sur Wix to Microsoft 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services via Wix pour Microsoft.
ms.openlocfilehash: 13dd84c9e7704a0680c2a3f0ca2e456767f6d231
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568497"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>Connecter vos enregistrements DNS sur Wix to Microsoft 365

**[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si Wix est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

Une fois ces enregistrements ajoutés sur Wix, votre domaine est installé pour fonctionner avec services Microsoft.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant d’utiliser votre domaine avec Microsoft, nous devons nous assurer qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que vous êtes propriétaire du domaine.

> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine, il n’a pas d’autre fonction. Vous pouvez le supprimer ultérieurement si vous le souhaitez.

> [!NOTE]
> WIX ne prend pas en charge les entrées DNS pour les sous-domaine.

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

2. **Sélectionnez Domaines** \> **...**, puis **gérez les enregistrements DNS** dans la liste liste.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

3. **Sélectionnez + Ajouter un enregistrement** dans la **ligne TXT (texte)** de l’éditeur DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Sélectionnez Ajouter un enregistrement.":::

4. In the boxes for the new record, type or copy and paste the values from the following table.

   |Nom d’hôte|TXT Value|TTL (Durée de vie)|
   |---|---|---|
   |Rempli automatiquement (laisser vide)|MS=*msXXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 heure|

5. **SelectSave**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Sélectionnez Enregistrer.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.


L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

Pour vérifier l’enregistrement dans Microsoft 365 :

1. Dans le Centre d’administration, Paramètres  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**domaines**</a>.

1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer l’installation**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.

1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

1. **Sélectionnez Domaines** \> **...**, puis **gérez les enregistrements DNS** dans la liste liste.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

1. Sous **MX (échange de courrier),** **sélectionnez Modifier les enregistrements MX**.

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="Sélectionnez Modifier les enregistrements MX.":::

1. Choisissez **Autre dans** la liste, puis **sélectionnez + Ajouter un enregistrement**.

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="Sélectionnez Autre dans la liste liste.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :

   |Nom d’hôte|Points to |Priority (Priorité)|TTL (Durée de vie)|
   |---|---|---|---|
   |Rempli automatiquement|*\<domain-key\>*.mail.protection.outlook.com <br/> **Remarque :** Obtenez votre compte *\<domain-key\>* Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|0 <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml).|1 heure|

1. Si d’autres enregistrements MX sont répertoriés, supprimez chacun d’eux.

  :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="Sélectionnez Supprimer.":::

1. Sélectionnez **Enregistrer**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

2. **Sélectionnez Domaines** \> **...**, puis **gérez les enregistrements DNS** dans la liste liste.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

3. **Sélectionnez + Ajouter un enregistrement** dans la ligne **CNAME (Alias)** de l’éditeur DNS pour l’enregistrement CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Sélectionnez + Ajouter un enregistrement.":::

4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :

   |Nom d’hôte|Valeur|Durée de vie|
   |---|---|---|
   |autodiscover|autodiscover.outlook.com|1 heure|

5. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de n’avoir qu’un *seul enregistrement* SPF qui inclut les deux ensembles de valeurs.

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

2. **Sélectionnez Domaines** \> **...**, puis **gérez les enregistrements DNS** dans la liste liste.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

3. **Sélectionnez + Ajouter un enregistrement** dans la **ligne TXT (texte)** de l’éditeur DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Sélectionnez + Ajouter un enregistrement.":::

   **Remarque** : Wix fournit une ligne SPF dans l’éditeur DNS. Ignorez cette ligne et utilisez la **ligne TXT (Texte)** pour entrer les valeurs SPF ci-dessous.

4. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant :

   |Nom d’hôte|Valeur|Durée de vie|
   |---|---|---|
   |[laissez ce vide]|v=spf1 include:spf.protection.outlook.com -all <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|1 Hour|

5. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Sélectionnez Enregistrer.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que la conversation, les appels de conférence et les appels vidéo, en plus des Microsoft Teams. Skype a besoin de quatre enregistrements : deux enregistrements SRV pour la communication utilisateur à utilisateur et deux enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

1. **Sélectionnez Domaines** \> **...**, puis **gérez les enregistrements DNS** dans la liste liste.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

1. **Sélectionnez + Ajouter un enregistrement** dans la **ligne SRV** de l’éditeur DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="Sélectionnez + Ajouter un enregistrement.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau :

   |Service|Protocole|Nom d’hôte|Pondération|Port|Target|Priority (Priorité)|TTL (Durée de vie)|
   |---|---|---|---|---|---|---|---|
   |sip|tls|Rempli automatiquement|1|443|sipdir.online.lync.com|100|1 Hour|
   |sipfed|tcp|Rempli automatiquement|1|5061|sipfed.online.lync.com|100|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement SRV en copiant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. **Sélectionnez + Ajoutez-en** une autre dans la ligne **CNAME (Alias)** de l’éditeur DNS, puis entrez les valeurs de la première ligne du tableau suivant.

   |Type|Hôte|Valeur|Durée de vie|
   |---|---|---|---|
   |CNAME|sip|sipdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 heure|
   |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils deux enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. To get started, go to your domains page at Wix by using [this link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Avant toute chose, vous serez invité à vous connecter.

1. **Sélectionnez Domaines** \> **...**, puis **gérez les enregistrements DNS** dans la liste liste.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

1. **Sélectionnez + Ajouter un enregistrement** dans la ligne **CNAME (Alias)** de l’éditeur DNS pour l’enregistrement CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Sélectionnez + Ajouter un enregistrement.":::

1. Entrez les valeurs de la première ligne du tableau suivant.

    |Type|Hôte|Valeur|Durée de vie|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 heure|
    |CNAME|enterpriseenrollment|enterpriseenrollment.manage.microsoft.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|1 Hour|

1. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Sélectionnez Enregistrer.":::

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
