---
title: Connecter vos enregistrements DNS web.com à Microsoft 365
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
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services sur web.com microsoft.
ms.openlocfilehash: 612c22b518402fccaf9ced76b2506aa15c0e89f6
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568409"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>Connecter vos enregistrements DNS web.com à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si web.com est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

Une fois ces enregistrements ajoutés web.com, votre domaine est installé pour fonctionner avec services Microsoft.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

> [!IMPORTANT]
> Vous devez effectuer cette procédure au niveau du bureau d'enregistrement de domaines auprès duquel vous avez acheté et inscrit votre domaine.

Lorsque vous vous êtes inscrit à web.com, vous avez ajouté un domaine à l’aide du processus **web.com’installation** .

Pour vérifier et créer des enregistrements DNS pour votre domaine dans Microsoft, vous devez d’abord modifier les serveurs de noms de votre bureau d’enregistrement de domaines afin qu’ils utilisent les serveurs web.com noms.

Pour modifier vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit.

1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.

2. Créez deux enregistrements de nameserver à l’aide des valeurs du tableau suivant, ou modifiez les enregistrements de nameserver existants afin qu’ils correspondent à ces valeurs.

    |Type|Valeur|
    |---|---|
    |Premier serveur de noms|Utilisez la valeur de nameserver fournie par web.com.|
    |Deuxième serveur de noms|Utilisez la valeur de nameserver fournie par web.com.|

    > [!TIP]
    > You should use at least two name server records. Si d’autres serveurs de noms sont répertoriés, vous devez les supprimer.

3. Enregistrez vos modifications.

> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Ensuite, votre messagerie Microsoft et d’autres services seront tous définies pour fonctionner avec votre domaine.

## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.

> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement.

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::

1. Faites défiler vers le bas **pour sélectionner Outils** avancés, puis en côté **des enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **TXT** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Sélectionnez TXT dans la liste drop-down Type.":::

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant.

    |Fait référence|Valeur TXT|Durée de vie|
    |---|---|:----|
    |@|MS=*msXXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 heure|

1. **Sélectionnez AJOUTER**.

    Patientez quelques minutes avant de vérifier votre nouvel enregistrement TXT, afin que l’enregistrement que vous venons de créer puisse être mis à jour sur Internet.

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

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::

1. Faites défiler vers le bas **pour sélectionner Outils** avancés, puis en côté **des enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **MX** dans la liste liste.

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant.

    |Se rapporte à|Serveur de messagerie|Priority (Priorité)|TTL (Durée de vie)|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Remarque :** Obtenez-le *\<domain-key\>* à partir du Centre d’administration Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> 1|1 Hour|

1. **Sélectionnez AJOUTER**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="Sélectionnez AJOUTER.":::

1. S’il existe d’autres enregistrements MX, supprimez-les tous en sélectionnant l’outil d’édition, puis supprimez **pour chaque** enregistrement.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="Sélectionnez Modifier.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::

1. Faites défiler vers le bas **pour sélectionner Outils** avancés, puis en côté **des enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **CNAME** dans la liste de listes.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Sélectionnez CNAME dans la liste drop-down Type.":::

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant.

    |Se rapporte à|Nom d’hôte|Alias to (Alias vers)|Durée de vie|
    |---|---|---|---|
    |Autre hôte|autodiscover|autodiscover.outlook.com|1 heure|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Tapez ou copiez-collez les valeurs CNAME dans la fenêtre.":::

1. **Sélectionnez AJOUTER**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de n’avoir qu’un *seul enregistrement* SPF qui inclut les deux ensembles de valeurs.

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::

1. Faites défiler vers le bas **pour sélectionner Outils** avancés, puis en côté **des enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **TXT** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Sélectionnez TXT dans la liste drop-down Type.":::

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant.

    |Se rapporte à|Valeur TXT|Durée de vie|
    |---|---|---|
    |@|v=spf1 include:spf.protection.outlook.com -all <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|1 Hour|

1. **Sélectionnez AJOUTER**.

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que la conversation, les appels de conférence et les appels vidéo, en plus des Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::

1. Faites défiler vers le bas **pour sélectionner Outils** avancés, puis en côté **des enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, **sélectionnez SRV** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="Sélectionnez SRV dans la liste drop-down Type.":::

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant.

    |Type|Service|Protocole|Pondération|Port|Target|Priority (Priorité)|TTL (Durée de vie)|
    |---|---|---|---|---|---|---|---|
    |SRV|_sip|TLS|100|443|sipdir.online.lync.com <br/> **Cette valeur ne peut pas se terminer par un point (.)**|1|1 heure|
    |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com <br/> **Cette valeur ne peut pas se terminer par un point (.)**|1|1 Hour|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="Tapez ou copiez-collez les valeurs du tableau dans la fenêtre d’enregistrement SRV.":::

1. **Sélectionnez AJOUTER**.

1. Ajoutez l’autre enregistrement SRV en copiant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::

1. Faites défiler vers le bas **pour sélectionner Outils** avancés, puis en côté **des enregistrements DNS avancés**, sélectionnez **GÉRER**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **CNAME** dans la liste de listes.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Sélectionnez CNAME dans la liste drop-down Type.":::

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant.

    |Type|Se rapporte à|Nom d’hôte|Alias to (Alias vers)|Durée de vie|
    |---|---|---|---|---|
    |CNAME|Autre hôte|sip|sipdir.online.lync.com <br/> **Cette valeur ne peut pas se terminer par un point (.)**|1 heure|
    |CNAME|Autre hôte|lyncdiscover|webdir.online.lync.com <br/> **Cette valeur ne peut pas se terminer par un point (.)**|1 Hour|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Tapez ou copiez-collez les valeurs CNAME dans la fenêtre.":::

1. **Sélectionnez AJOUTER**.

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils 2 enregistrements CNAME pour que les utilisateurs inscrivent des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Connectez-vous en premier.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste liste.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste liste.":::

1. Faites défiler vers le bas **pour sélectionner Outils** avancés, puis en côté **des enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous de devez **peut-être sélectionner Continuer** pour obtenir la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En plus des enregistrements DNS avancés, sélectionnez MANAGE.":::

1. Dans la page Gérer les enregistrements DNS avancés, **sélectionnez + AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **CNAME** dans la liste de listes.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Sélectionnez CNAME dans la liste drop-down Type.":::

1. Sélectionnez ou copiez-collez les valeurs du tableau suivant.

    |Type|Se rapporte à|Nom d’hôte|Alias to (Alias vers)|Durée de vie|
    |---|---|---|---|---|
    |CNAME|Autre hôte|enterpriseregistration|enterpriseregistration.windows.net <br/> **Cette valeur ne peut pas se terminer par un point (.)**|1 heure|
    |CNAME|Autre hôte|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com <br/> **Cette valeur ne peut pas se terminer par un point (.)**|1 Hour|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Tapez ou copiez-collez les valeurs CNAME du tableau dans la fenêtre.":::

1. **Sélectionnez AJOUTER**.

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne du tableau.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).
