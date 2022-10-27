---
title: Connecter vos enregistrements DNS à web.com à Microsoft 365
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
description: Découvrez comment vérifier votre domaine et configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online et d’autres services sur web.com pour Microsoft.
ms.openlocfilehash: 72aec638fbd3e73aa7df15608ed91f7d7f3de962
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726770"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>Connecter vos enregistrements DNS à web.com à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si web.com est votre fournisseur d’hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype Entreprise Online, etc.

Une fois que vous avez ajouté ces enregistrements à web.com, votre domaine est configuré pour fonctionner avec les services Microsoft.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

> [!IMPORTANT]
> Vous devez effectuer cette procédure au niveau du bureau d'enregistrement de domaines auprès duquel vous avez acheté et inscrit votre domaine.

Lorsque vous vous êtes inscrit à web.com, vous avez ajouté un domaine à l’aide du processus **d’installation** web.com.

Pour vérifier et créer des enregistrements DNS pour votre domaine dans Microsoft, vous devez d’abord modifier les serveurs de noms de votre bureau d’enregistrement de domaines afin qu’ils utilisent les serveurs de noms web.com.

Pour modifier vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit.

1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.

2. Créez deux enregistrements de serveur de noms en utilisant les valeurs du tableau suivant, ou modifiez les enregistrements de serveur de noms existants afin qu’ils correspondent à ces valeurs.

    |Type|Valeur|
    |---|---|
    |Premier serveur de noms|Utilisez la valeur de serveur de noms fournie par web.com.|
    |Deuxième serveur de noms|Utilisez la valeur de serveur de noms fournie par web.com.|

    > [!TIP]
    > You should use at least two name server records. Si d’autres serveurs de noms sont répertoriés, vous devez les supprimer.

3. Enregistrez vos modifications.

> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Votre messagerie Microsoft et d’autres services seront alors prêts à fonctionner avec votre domaine.

## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. Pour commencer, accédez à la page de vos domaines à web.com à l’aide [de ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste déroulante.":::

1. Faites défiler vers le bas pour sélectionner **Outils avancés**, puis en regard de **Enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous devrez peut-être sélectionner **Continuer** pour accéder à la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En regard de Enregistrements DNS avancés, sélectionnez GÉRER.":::

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+ AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **TXT** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Sélectionnez TXT dans la liste déroulante Type.":::

1. Sélectionnez ou copiez et collez les valeurs du tableau suivant.

    |Se réfère|Valeur TXT|Durée de vie|
    |---|---|:----|
    |@|MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|1 Hour|

1. Sélectionnez **AJOUTER**.

    Attendez quelques minutes avant de vérifier votre nouvel enregistrement TXT, afin que l’enregistrement que vous venez de créer puisse être mis à jour sur Internet.

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

1. Pour commencer, accédez à la page de vos domaines à web.com à l’aide [de ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste déroulante.":::

1. Faites défiler vers le bas pour sélectionner **Outils avancés**, puis en regard de **Enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous devrez peut-être sélectionner **Continuer** pour accéder à la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En regard de Enregistrements DNS avancés, sélectionnez GÉRER.":::

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+ AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **MX** dans la liste déroulante.

1. Sélectionnez ou copiez et collez les valeurs du tableau suivant.

    |Se rapporte à|Serveur de messagerie|Priorité|Durée de vie|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Note:** Obtenez votre *\<domain-key\>* à partir du Centre d’administration Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> 1|1 Hour|

1. Sélectionnez **AJOUTER**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="Sélectionnez AJOUTER.":::

1. S’il existe d’autres enregistrements MX, supprimez-les tous en sélectionnant l’outil d’édition, puis **Supprimer** pour chaque enregistrement.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="Sélectionnez Modifier.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines à web.com à l’aide [de ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste déroulante.":::

1. Faites défiler vers le bas pour sélectionner **Outils avancés**, puis en regard de **Enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous devrez peut-être sélectionner **Continuer** pour accéder à la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En regard de Enregistrements DNS avancés, sélectionnez GÉRER.":::

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+ AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **CNAME** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Sélectionnez CNAME dans la liste déroulante Type.":::

1. Sélectionnez ou copiez et collez les valeurs du tableau suivant.

    |Se rapporte à|Nom d’hôte|Alias to (Alias vers)|Durée de vie|
    |---|---|---|---|
    |Autre hôte|autodiscover|autodiscover.outlook.com|1 Hour|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Tapez ou copiez et collez les valeurs CNAME dans la fenêtre.":::

1. Sélectionnez **AJOUTER**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Au lieu de cela, ajoutez les valeurs Microsoft requises à l’enregistrement actif afin d’avoir un *seul* enregistrement SPF qui inclut les deux jeux de valeurs.

1. Pour commencer, accédez à la page de vos domaines à web.com à l’aide [de ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste déroulante.":::

1. Faites défiler vers le bas pour sélectionner **Outils avancés**, puis en regard de **Enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous devrez peut-être sélectionner **Continuer** pour accéder à la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En regard de Enregistrements DNS avancés, sélectionnez GÉRER.":::

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+ AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **TXT** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Sélectionnez TXT dans la liste déroulante Type.":::

1. Sélectionnez ou copiez et collez les valeurs du tableau suivant.

    |Se rapporte à|Valeur TXT|Durée de vie|
    |---|---|---|
    |@|v=spf1 include:spf.protection.outlook.com -all <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|1 Hour|

1. Sélectionnez **AJOUTER**.

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversations, les téléconférences et les appels vidéo, en plus de Microsoft Teams. Skype a besoin de 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter les utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines à web.com à l’aide [de ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste déroulante.":::

1. Faites défiler vers le bas pour sélectionner **Outils avancés**, puis en regard de **Enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous devrez peut-être sélectionner **Continuer** pour accéder à la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En regard de Enregistrements DNS avancés, sélectionnez GÉRER.":::

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+ AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **SRV** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="Sélectionnez SRV dans la liste déroulante Type.":::

1. Sélectionnez ou copiez et collez les valeurs du tableau suivant.

    |Type|Service|Protocole|Pondération|Port|Target|Priorité|Durée de vie|
    |---|---|---|---|---|---|---|---|
    |SRV|_sip|TLS|100|443|sipdir.online.lync.com <br/> **Cette valeur NE PEUT PAS se terminer par un point (.)**|1|1 Hour|
    |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com <br/> **Cette valeur NE PEUT PAS se terminer par un point (.)**|1|1 Hour|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="Tapez ou copiez et collez les valeurs de la table dans la fenêtre d’enregistrement SRV.":::

1. Sélectionnez **AJOUTER**.

1. Ajoutez l’autre enregistrement SRV en copiant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Ajoutez les deux enregistrements CNAME requis pour Skype Entreprise

1. Pour commencer, accédez à la page de vos domaines à web.com à l’aide [de ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste déroulante.":::

1. Faites défiler vers le bas pour sélectionner **Outils avancés**, puis en regard de **Enregistrements DNS avancés**, sélectionnez **GÉRER**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En regard de Enregistrements DNS avancés, sélectionnez GÉRER.":::

    Vous devrez peut-être sélectionner **Continuer** pour accéder à la page Gérer les enregistrements DNS avancés.

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+ AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **CNAME** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Sélectionnez CNAME dans la liste déroulante Type.":::

1. Sélectionnez ou copiez et collez les valeurs du tableau suivant.

    |Type|Se rapporte à|Nom d’hôte|Alias to (Alias vers)|Durée de vie|
    |---|---|---|---|---|
    |CNAME|Autre hôte|sip|sipdir.online.lync.com <br/> **Cette valeur NE PEUT PAS se terminer par un point (.)**|1 Hour|
    |CNAME|Autre hôte|lyncdiscover|webdir.online.lync.com <br/> **Cette valeur NE PEUT PAS se terminer par un point (.)**|1 Hour|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Tapez ou copiez et collez les valeurs CNAME dans la fenêtre.":::

1. Sélectionnez **AJOUTER**.

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils a besoin de 2 enregistrements CNAME pour permettre aux utilisateurs d’inscrire des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. Pour commencer, accédez à la page de vos domaines à web.com à l’aide [de ce lien](https://checkout.web.com/manage-it/index.jsp). Connectez-vous d’abord.

1. Sur la page d’accueil, sélectionnez **Noms de domaine**.

1. Sous **Actions**, sélectionnez les trois points, puis sélectionnez **Gérer** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Sélectionnez Gérer dans la liste déroulante.":::

1. Faites défiler vers le bas pour sélectionner **Outils avancés**, puis en regard de **Enregistrements DNS avancés**, sélectionnez **GÉRER**.

    Vous devrez peut-être sélectionner **Continuer** pour accéder à la page Gérer les enregistrements DNS avancés.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="En regard de Enregistrements DNS avancés, sélectionnez GÉRER.":::

1. Dans la page Gérer les enregistrements DNS avancés, sélectionnez **+ AJOUTER UN ENREGISTREMENT**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Sélectionnez + AJOUTER UN ENREGISTREMENT.":::

1. Sous **Type**, sélectionnez **CNAME** dans la liste déroulante.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Sélectionnez CNAME dans la liste déroulante Type.":::

1. Sélectionnez ou copiez et collez les valeurs du tableau suivant.

    |Type|Se rapporte à|Nom d’hôte|Alias to (Alias vers)|Durée de vie|
    |---|---|---|---|---|
    |CNAME|Autre hôte|enterpriseregistration|enterpriseregistration.windows.net <br/> **Cette valeur NE PEUT PAS se terminer par un point (.)**|1 Hour|
    |CNAME|Autre hôte|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com <br/> **Cette valeur NE PEUT PAS se terminer par un point (.)**|1 Hour|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Tapez ou copiez et collez les valeurs CNAME de la table dans la fenêtre.":::

1. Sélectionnez **AJOUTER**.

1. Ajoutez l’autre enregistrement CNAME en copiant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).
