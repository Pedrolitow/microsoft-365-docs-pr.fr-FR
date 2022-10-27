---
title: Connecter vos enregistrements DNS sur OVH à Microsoft 365
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
ms.assetid: 5176feef-36dc-4d84-842f-1f2b5a21ba96
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online et les autres services sur OVH pour Microsoft.
ms.openlocfilehash: ea109c391882c5b5524b5cb520f47c12d8708c6f
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68730290"
---
# <a name="connect-your-dns-records-at-ovh-to-microsoft-365"></a>Connecter vos enregistrements DNS sur OVH à Microsoft 365

[Consultez les FAQ des domaines](../setup/domains-faq.yml) si vous ne trouvez pas ce que vous recherchez.

Si OVH est votre fournisseur d'hébergement DNS, procédez de la manière décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.

Une fois ces enregistrements ajoutés sur OVH, votre domaine est configuré pour utiliser les services Microsoft.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.

    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Dans la page d’accueil du tableau de bord, sous **Afficher toute mon activité**, sélectionnez le nom du domaine que vous souhaitez modifier.

1. Sélectionnez **zone DNS**.

    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Sélectionnez **Ajouter une entrée**.

    ![OVH Ajouter une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Sélectionnez **TXT**

    ![OVH sélectionnez l’entrée TXT.](../../media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png)

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. Pour affecter une valeur de durée de vie, choisissez **Personnalisé** dans la liste déroulante, puis tapez la valeur dans la zone de texte.

   |Type d’enregistrement|Sous-domaine|Durée de vie|Valeur|
   |---|---|---|---|
   |TXT|(laissez vide)|3600 secondes|MS=msXXXXXXXX  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|

1. Sélectionnez **Suivant**.

1. Sélectionner **Confirmer**.

    ![OVH confirmez TXT pour vérification.](../../media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png)

1. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

Pour vérifier l’enregistrement dans Microsoft 365 :

1. Dans le Centre d’administration, accédez aux **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>.

1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer l’installation**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.

1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
>  Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.

    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Dans la page d’accueil du tableau de bord, sous **Afficher toute mon activité**, sélectionnez le nom du domaine que vous souhaitez modifier.

1. Sélectionnez **zone DNS**.

    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Sélectionnez **Ajouter une entrée**.

    ![OVH Ajouter une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Sélectionnez **MX**.

    ![Type d’enregistrement MX OVH.](../../media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png)

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. Pour affecter une valeur de durée de vie, choisissez **Personnalisé** dans la liste déroulante, puis tapez la valeur dans la zone de texte.

    > [!NOTE]
    > Par défaut, OVH utilise une notation relative pour localiser la cible. Celle-ci s’ajoute au nom de domaine à la fin de l’enregistrement cible. Pour utiliser une notation absolue, ajoutez un point à l’enregistrement cible, ainsi que montré dans le tableau ci-dessous.

   |Sous-domaine|Durée de vie|Priorité|Target|
   |---|---|---|---|
   |(laissez vide)|3600 secondes|0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml).|\<domain-key\>.mail.protection.outlook.com  <br/> **Note:** Obtenez votre à *\<domain-key\>* partir de votre compte Microsoft. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|

    ![Enregistrement MX OVH pour le courrier.](../../media/6e2f5655-93e2-4620-8f19-c452e7edf8f0.png)

1. Sélectionnez **Suivant**.

    ![Enregistrement MX OVH sélectionnez Suivant.](../../media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png)

1. Sélectionner **Confirmer**.

    ![Enregistrement MX OVH sélectionnez Confirmer.](../../media/090bfb11-a753-4af0-8982-582a4069a169.png)

1. Supprimez tous les autres enregistrements MX de la liste sur la page **zone DNS** . Sélectionnez chaque enregistrement et, dans la colonne **Actions** , sélectionnez l’icône **Supprimer** de la corbeille.

    ![OVH supprime l’enregistrement MX.](../../media/892b328b-7057-4828-b8c5-fe26284dc8c2.png)

1. Sélectionner **Confirmer**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.

    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Dans la page d’accueil du tableau de bord, sous **Afficher toute mon activité**, sélectionnez le nom du domaine que vous souhaitez modifier.

1. Sélectionnez **zone DNS**.

    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Sélectionnez **Ajouter une entrée**.

    ![OVH Ajouter une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Sélectionnez **CNAME**.

    ![OVH Ajouter un type d’enregistrement CNAME.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. Pour affecter une valeur de durée de vie, choisissez **Personnalisé** dans la liste déroulante, puis tapez la valeur dans la zone de texte.

   |Sous-domaine|Durée de vie|Target|
   |---|---|---|
   |autodiscover|3600 secondes|autodiscover.outlook.com.|

    ![Enregistrement CNAME OVH.](../../media/516938b3-0b12-4736-a631-099e12e189f5.png)

1. Sélectionnez **Suivant**.

    ![OVH Ajouter des valeurs CNAME et sélectionner Suivant.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. Sélectionner **Confirmer**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs.

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.

    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Dans la page d’accueil du tableau de bord, sous **Afficher toute mon activité**, sélectionnez le nom du domaine que vous souhaitez modifier.

1. Sélectionnez **zone DNS**.

    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Sélectionnez **Ajouter une entrée**.

    ![OVH Ajouter une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Sélectionnez **TXT**.

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. Pour affecter une valeur de durée de vie, choisissez **Personnalisé** dans la liste déroulante, puis tapez la valeur dans la zone de texte.

   |Sous-domaine|Durée de vie|Valeur|
   |---|---|---|
   |(laissez vide)|3600 secondes|v=spf1 include:spf.protection.outlook.com -all <br/**Remarque :** nous vous recommandons de copier et coller cette entrée, afin que tout l’espacement reste correct.|

    ![OVH Ajouter un enregistrement TXT pour SPF.](../../media/f50466e9-1557-4548-8a39-e98978a5ee2e.png)

1. Sélectionnez **Suivant**.

    ![OVH Ajouter un enregistrement TXT pour SPF et sélectionner Suivant.](../../media/7937eb7c-114f-479f-a916-bcbe476d6108.png)

1. Sélectionner **Confirmer**.

    ![OVH Ajouter un enregistrement TXT pour SPF et Confirmer.](../../media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png)

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversations, les téléconférences et les appels vidéo, en plus de Microsoft Teams. Skype a besoin de 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter les utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.

    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Dans la page d’accueil du tableau de bord, sous **Afficher toute mon activité**, sélectionnez le nom du domaine que vous souhaitez modifier.

1. Sélectionnez **zone DNS**.

    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Sélectionnez **Ajouter une entrée**.

    ![OVH Ajouter une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Sélectionnez **SRV**.

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. Pour affecter une valeur de durée de vie, choisissez **Personnalisé** dans la liste déroulante, puis tapez la valeur dans la zone de texte.

   |Sous-domaine|TTL (Seconds)|Priorité|Pondération|Port|Target|
   |---|---|---|---|---|---|
   |_sip._tls|3600 (s.)|100|1|443|sipdir.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**><br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|
   |_sipfederationtls._tcp|3600 (s.)|100|1|5061|sipfed.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**<br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|

1. Pour ajouter l’autre enregistrement SRV, sélectionnez **Ajouter un autre enregistrement**, créez un enregistrement à l’aide des valeurs de la ligne suivante dans la table, puis sélectionnez **Créer des enregistrements**.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Ajoutez les deux enregistrements CNAME requis pour Skype Entreprise

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.

    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Dans la page d’accueil du tableau de bord, sous **Afficher toute mon activité**, sélectionnez le nom du domaine que vous souhaitez modifier.

1. Sélectionnez **zone DNS**.

    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Sélectionnez **Ajouter une entrée**.

    ![OVH Ajouter une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Sélectionnez **CNAME**.

    ![OVH Ajouter un type d’enregistrement CNAME.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. Pour affecter une valeur de durée de vie, choisissez **Personnalisé** dans la liste déroulante, puis tapez la valeur dans la zone de texte.

   |Sous-domaine|Durée de vie|Target|
   |---|---|---|
   |sip|3600 (s.)|sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|
   |lyncdiscover|3600 (s.)|webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|

1. Sélectionnez **Suivant**.

    ![OVH Ajouter des valeurs CNAME et sélectionner Suivant.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. Sélectionner **Confirmer**.

1. Ajoutez l’autre enregistrement CNAME.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils a besoin de deux enregistrements CNAME pour permettre aux utilisateurs d’inscrire des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.

    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Dans la page d’accueil du tableau de bord, sous **Afficher toute mon activité**, sélectionnez le nom du domaine que vous souhaitez modifier.

1. Sélectionnez **zone DNS**.

    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Sélectionnez **Ajouter une entrée**.

    ![OVH Ajouter une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Sélectionnez **CNAME**.

    ![OVH Ajouter un type d’enregistrement CNAME.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. Pour affecter une valeur de durée de vie, choisissez **Personnalisé** dans la liste déroulante, puis tapez la valeur dans la zone de texte.

   |Sous-domaine|Durée de vie|Target|
   |---|---|---|
   |enterpriseregistration  <br/>|3600 (s.)|enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)**|
   |enterpriseenrollment|3600 (s.)|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)**|

1. Sélectionnez **Suivant**.

    ![OVH Ajouter des valeurs CNAME et sélectionner Suivant.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. Sélectionner **Confirmer**.

1. Ajoutez l’autre enregistrement CNAME.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).