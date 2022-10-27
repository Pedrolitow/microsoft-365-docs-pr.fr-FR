---
title: Connecter vos enregistrements DNS sur Namecheap à Microsoft 365
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
ms.assetid: 54ae2002-b38e-43a1-82fa-3e49d78fda56
description: Découvrez comment vérifier votre domaine et configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online et d’autres services dans Namecheap pour Microsoft.
ms.openlocfilehash: ac1f2e5b02f8a3068d91579ed65fc9bad098f72f
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729476"
---
# <a name="connect-your-dns-records-at-namecheap-to-microsoft-365"></a>Connecter vos enregistrements DNS sur Namecheap à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si Namecheap est votre fournisseur d’hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online, etc.

Une fois que vous avez ajouté ces enregistrements dans Namecheap, votre domaine est configuré pour fonctionner avec les services Microsoft.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. Pour commencer, accédez à la page de vos domaines dans Namecheap à l’aide [de ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à Continuer.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Dans la page d’accueil, sous **Compte**, choisissez **Liste de domaines** dans la liste déroulante.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Sélectionnez Liste de domaines dans la liste déroulante.":::

1. Dans la page Liste des domaines, sélectionnez le domaine que vous souhaitez modifier, puis sélectionnez **Gérer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **ENREGISTREMENTS DE L’HÔTE** , sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la liste déroulante **Type** , sélectionnez **Enregistrement TXT**.

    > [!NOTE]
    > La liste déroulante **Type** s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/a5b40973-19b5-4c32-8e1b-1521aa971836.png" alt-text="Sélectionnez Enregistrement TXT.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choisissez la valeur **TTL** dans la liste déroulante.)

    |Type|Hôte|Valeur|Durée de vie|
    |---|---|---|---|
    |TXT|@|MS=ms *XXXXXXXX*  <br/>**Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|30 min|

     :::image type="content" source="../../media/fe75c0fd-f85c-4bef-8068-edaf9779b7f1.png" alt-text="Copiez et collez les valeurs de la table.":::

1. Sélectionnez le contrôle **Enregistrer les modifications** (coche).

     :::image type="content" source="../../media/b48d2c67-66b5-4aa4-8e59-0c764f236fac.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

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

1. Pour commencer, accédez à la page de vos domaines dans Namecheap à l’aide [de ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à Continuer.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Dans la page d’accueil, sous **Compte**, choisissez **Liste de domaines** dans la liste déroulante.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Choisissez Liste de domaines dans la liste déroulante.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine que vous souhaitez modifier, puis sélectionnez **Gérer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **PARAMÈTRES DE MESSAGERIE**, sélectionnez **Mx personnalisé** dans la liste déroulante **Email Transfert**.

    (Vous devrez peut-être faire défiler la page vers le bas.)

     :::image type="content" source="../../media/40199e2c-42cf-4c3f-9936-3cbe5d4e81a4.png" alt-text="Sélectionnez Mx personnalisé.":::

1. Sélectionnez **Ajouter un nouvel enregistrement**.

     :::image type="content" source="../../media/8d169b81-ba48-4d51-84ea-a08fa1616457.png" alt-text="AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (La zone **Priorité** est la zone sans nom située à droite de la zone **Valeur** . Choisissez la valeur **TTL** dans la liste déroulante.)

    |Type|Hôte|Valeur|Priorité|Durée de vie|
    |---|---|---|---|---|
    |MX Record (Enregistrement MX)|@|\<*domain-key*\>.mail.protection.outlook.com  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> **Note:** Obtenez votre à *\<domain-key\>* partir de votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml).|30 min|

     :::image type="content" source="../../media/f3b76d62-5022-48c1-901b-8615a8571309.png" alt-text="Copiez et collez les valeurs de la table.":::

1. Sélectionnez le contrôle **Enregistrer les modifications** (coche).

     :::image type="content" source="../../media/ef4e3112-36d2-47c8-a478-136a565dd71d.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. S'il existe d'autres enregistrements MX, utilisez le processus en deux étapes suivant pour supprimer chacun d'eux :

    Tout d’abord, sélectionnez **Supprimer** (corbeille) pour l’enregistrement que vous souhaitez supprimer.

     :::image type="content" source="../../media/7a7a751f-29c2-495f-8f55-98ca37ce555a.png" alt-text="Sélectionnez Supprimer.":::

    Ensuite, sélectionnez **Oui** pour confirmer la suppression.

     :::image type="content" source="../../media/85ebc0c7-8787-43ee-9e7b-647375b3345c.png" alt-text="Sélectionnez Oui.":::

    Supprimez tous les enregistrements MX à l’exception de celui que vous avez ajouté précédemment dans cette procédure.

## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines dans Namecheap à l’aide [de ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à Continuer.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Dans la page d’accueil, sous **Compte**, choisissez **Liste de domaines** dans la liste déroulante.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Sélectionnez Liste de domaines.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine que vous souhaitez modifier, puis sélectionnez **Gérer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **ENREGISTREMENTS DE L’HÔTE** , sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la liste déroulante **Type** , sélectionnez **Enregistrement CNAME**.

    > [!NOTE]
    > La liste déroulante **Type** s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Sélectionnez Enregistrement CNAME.":::

1. Dans les zones vides du nouvel enregistrement, sélectionnez le **Type d'enregistrement** **CNAME**, puis tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

    |Type|Hôte|Valeur|Durée de vie|
    |---|---|---|---|
    |CNAME|autodiscover|autodiscover.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|Automatique|

     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Copiez et collez les valeurs de la table.":::

1. Sélectionnez le contrôle **Enregistrer les modifications** (coche).

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Au lieu de cela, ajoutez les valeurs Microsoft requises à l’enregistrement actif afin d’avoir un *seul*  enregistrement SPF qui inclut les deux jeux de valeurs.

1. Pour commencer, accédez à la page de vos domaines dans Namecheap à l’aide [de ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Vous serez invité à vous connecter et à Continuer.

1. Dans la page d’accueil, sous **Compte**, choisissez **Liste de domaines** dans la liste déroulante.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Sélectionnez Liste de domaines.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine que vous souhaitez modifier, puis sélectionnez **Gérer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **ENREGISTREMENTS DE L’HÔTE** , sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la liste déroulante **Type** , sélectionnez **Enregistrement TXT**.

    > [!NOTE]
    > La liste déroulante **Type** s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/c5d1fddb-28b5-48ec-91c9-3e5d3955ac80.png" alt-text="Sélectionnez Enregistrement TXT.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes du tableau suivant.

    (Choisissez la valeur **TTL** dans la liste déroulante.)

    |Type|Hôte|Valeur|Durée de vie|
    |---|---|---|---|
    |TXT|@|v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|30 min|

     :::image type="content" source="../../media/ea0829f1-990b-424b-b26e-9859468318dd.png" alt-text="Copiez et collez les valeurs de la table.":::

1. Sélectionnez le contrôle **Enregistrer les modifications** (coche).

     :::image type="content" source="../../media/f2846c36-ace3-43d8-be5d-a65e2c267619.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversations, les téléconférences et les appels vidéo, en plus de Microsoft Teams. Skype a besoin de 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter les utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines dans Namecheap à l’aide [de ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). You'll be prompted to sign in.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Dans la page d’accueil, sous **Compte**, choisissez **Liste de domaines** dans la liste déroulante.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Choisissez Liste de domaines.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine que vous souhaitez modifier, puis sélectionnez **Gérer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **ENREGISTREMENTS DE L’HÔTE** , sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la liste déroulante **Type** , sélectionnez **Enregistrement SRV**.

    > [!NOTE]
    > La liste déroulante **Type** s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Sélectionnez le type d’enregistrement SRV.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.

    |Service|Protocole|Priorité|Pondération|Port|Target|Durée de vie|
    |---|---|---|---|---|---|---|
    |_sip|_tls|100|1|443|sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|Automatique|
    |_sipfederationtls|_tcp|100|1|5061|sipfed.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|Automatique|

     :::image type="content" source="../../media/ff9566ea-0096-4b7f-873c-027080a23b56.png" alt-text="Copiez et collez les valeurs de la table.":::

1. Sélectionnez le contrôle **Enregistrer les modifications** (coche).

     :::image type="content" source="../../media/48a8dee4-c66d-449d-8759-9e9784c82b13.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. Ajoutez l’autre enregistrement SRV en choisissant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Ajoutez les deux enregistrements CNAME requis pour Skype Entreprise

1. Dans la section **ENREGISTREMENTS DE L’HÔTE** , sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEAU NOM.":::

1. Dans la liste déroulante **Type** , sélectionnez **CNAME**.

    > [!NOTE]
    > La liste déroulante **Type** s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Sélectionnez CNAME.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau.

    |Type|Hôte|Valeur|Durée de vie|
    |---|---|---|---|
    |CNAME|sip|sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|Automatique|
    |CNAME|lyncdiscover|webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|Automatique|

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Copiez et collez les valeurs CNAME de la table.":::

1. Sélectionnez le contrôle **Enregistrer les modifications** (coche).

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils a besoin de deux enregistrements CNAME pour permettre aux utilisateurs d’inscrire des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. Pour commencer, accédez à la page de vos domaines dans Namecheap à l’aide [de ce lien](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). You'll be prompted to sign in.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Dans la page d’accueil, sous **Compte**, choisissez **Liste de domaines** dans la liste déroulante.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Sélectionnez Liste de domaines.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine que vous souhaitez modifier, puis sélectionnez **Gérer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste déroulante.":::

1. Dans la section **ENREGISTREMENTS DE L’HÔTE** , sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la liste déroulante **Type** , sélectionnez **Enregistrement CNAME**.

    > [!NOTE]
    > La liste déroulante **Type** s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT**.

     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Sélectionnez Enregistrement CNAME.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau.

    |Type|Hôte|Valeur|Durée de vie|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)**|Automatique|
    |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|Automatique|

     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Copiez et collez les valeurs de la table.":::

1. Sélectionnez le contrôle **Enregistrer les modifications** .

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne de la table.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).
