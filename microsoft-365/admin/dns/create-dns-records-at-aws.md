---
title: Connecter vos enregistrements DNS sur Amazon Web Services (AWS) à Microsoft 365
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
ms.assetid: 7a2efd75-0771-4897-ba7b-082fe5bfa9da
description: Apprenez à vérifier votre domaine et à configurer des enregistrements DNS pour le courrier électronique, Skype Entreprise Online et d’autres services sur Amazon Web Services (AWS) pour Microsoft.
ms.openlocfilehash: 9938168c3fb29e4d6bd862414f309c8b58db1223
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68719159"
---
# <a name="connect-your-dns-records-at-amazon-web-services-aws-to-microsoft-365"></a>Connecter vos enregistrements DNS sur Amazon Web Services (AWS) à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si AWS est votre fournisseur d’hébergement DNS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier électronique, Skype Online Entreprise, etc.

Une fois que vous avez ajouté ces enregistrements sur AWS, votre domaine est configuré pour fonctionner avec les services Microsoft.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sous **Domaines**, sélectionnez **Domaines inscrits**.

1. Sous **Nom de domaine**, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque** : Si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez **Créer une zone hébergée** et effectuez les étapes avant de passer à l’étape suivante.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez vérifier.":::

1. Sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Nom de domaine**, sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine que vous souhaitez vérifier.":::

1. Sélectionnez **Créer un enregistrement**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Sélectionnez Créer un enregistrement.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choisissez les valeurs **de stratégie Type** et **Routage** dans les listes déroulantes.)

    > [!TIP]
    > The quotation marks required by the onscreen instructions are supplied automatically. You don't need to type them manually.

    |Nom de l’enregistrement|Type d’enregistrement|Valeur|TTL (Seconds)|Stratégie de routage|
    |:-----|:-----|:-----|:-----|:-----|
    |(Leave this field empty.)|TXT : utilisé pour vérifier les expéditeurs d’e-mails|MS=ms *XXXXXXXX* <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|300|Simple|

1. Sélectionnez **Créer des enregistrements**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Sélectionnez Créer des enregistrements.":::

   Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.

Maintenant que vous avez ajouté l’enregistrement sur le site de votre bureau d’enregistrement de domaines, vous allez revenir à Microsoft et demander une recherche pour l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

Pour vérifier l’enregistrement dans Microsoft 365 :

1. Dans le Centre d’administration, accédez aux **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>.

1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer l’installation**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.

1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft-365"></a>Ajoutez un enregistrement MX pour que les e-mails de votre domaine soient redirigés vers Microsoft 365

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sous **Domaines**, sélectionnez **Domaines inscrits**.

1. Sous **Nom de domaine**, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque** : Si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez **Créer une zone hébergée** et effectuez les étapes avant de passer à l’étape suivante.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Nom de domaine**, sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Sélectionnez Créer un enregistrement.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choisissez les valeurs **de stratégie Type** et **Routage** dans les listes déroulantes.)

    > [!TIP]
    > The quotation marks required by the onscreen instructions are supplied automatically. You don't need to type them manually.

    |Nom de l’enregistrement|Type d’enregistrement|Valeur|TTL (Seconds)|Stratégie de routage|
    |:-----|:-----|:-----|:-----|:-----|
    |(Leave this field empty.)|MX - Spécifie les serveurs de messagerie|0 *\<domain-key\>*.mail.protection.outlook.com. <br/> The 0 is the MX priority value. Add it to the beginning of the MX value, separated from the remainder of the value by a space. <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> **Note:** Obtenez votre à \<*domain-key*\> partir de votre compte Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|300|Routage simple|

1. Sélectionnez **Créer des enregistrements**.

   :::image type="content" source="../../media/dns-aws/aws-domains-mx-create-records.png" alt-text="Sélectionnez Créer des enregistrements.":::

1. S’il existe d’autres enregistrements MX, supprimez-les en sélectionnant l’enregistrement, puis en sélectionnant **Supprimer**.

## <a name="add-the-cname-record-required-for-microsoft-365"></a>Ajouter l’enregistrement CNAME requis pour Microsoft 365

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sous **Domaines**, sélectionnez **Domaines inscrits**.

1. Sous **Nom de domaine**, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque** : Si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez **Créer une zone hébergée** et effectuez les étapes avant de passer à l’étape suivante.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Nom de domaine**, sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Sélectionnez Créer un enregistrement.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choisissez les valeurs **de stratégie Type** et **Routage** dans les listes déroulantes.)

    |Nom de l’enregistrement|Type d’enregistrement|Valeur|Durée de vie|Stratégie de routage|
    |:-----|:-----|:-----|:-----|:-----|
    |autodiscover|CNAME : achemine le trafic vers un autre nom de domaine|autodiscover.outlook.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|300|Simple|

1. Sélectionnez **Créer des enregistrements**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Sélectionnez Créer des enregistrements.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Au lieu de cela, ajoutez les valeurs Microsoft requises à l’enregistrement actif afin d’avoir un *seul* enregistrement SPF qui inclut les deux jeux de valeurs. Voici quelques exemples. Consultez ces [Enregistrements DNS externes pour Microsoft](../../enterprise/external-domain-name-system-records.md). Pour valider votre enregistrement SPF, vous pouvez utiliser l’un de ces[outils de validation SPF](../setup/domains-faq.yml).

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sous **Domaines**, sélectionnez **Domaines inscrits**.

1. Sous **Nom de domaine**, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque** : Si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez **Créer une zone hébergée** et effectuez les étapes avant de passer à l’étape suivante.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Nom de domaine**, sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Sélectionnez Créer un enregistrement.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choisissez la valeur **Type** dans les listes déroulantes.)

    |Type d’enregistrement|Valeur|
    |:-----|:-----|
    |TXT : utilisé pour vérifier les expéditeurs d’e-mails et pour les valeurs propres à l’application|v=spf1 include:spf.protection.outlook.com -all <br/> (Les guillemets requis pour les instructions à l'écran sont insérés automatiquement. Vous n'avez pas besoin de les entrer manuellement.) <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|

1. Sélectionnez **Créer des enregistrements**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Sélectionnez Créer des enregistrements.":::

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversations, les téléconférences et les appels vidéo, en plus de Microsoft Teams. Skype a besoin de 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter les utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sous **Domaines**, sélectionnez **Domaines inscrits**.

1. Sous **Nom de domaine**, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque** : Si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez **Créer une zone hébergée** et effectuez les étapes avant de passer à l’étape suivante.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Nom de domaine**, sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Sélectionnez Créer un enregistrement.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choose the **Type** and **Routing Policy** values from the drop-down lists.)

    |Nom de l’enregistrement|Type d’enregistrement|Valeur|TTL (Seconds)|Stratégie de routage|
    |:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|SRV : valeurs spécifiques à l’application qui id serveurs|100 1 443 sipdir.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**> <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|300|Simple|
    |_sipfederationtls._tcp|SRV : valeurs spécifiques à l’application qui id serveurs|100 1 5061 sipfed.online.lync.com. **Cette valeur DOIT se terminer par un point (.)** <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.|300|Simple|

1. Pour ajouter l’autre enregistrement SRV, sélectionnez **Ajouter un autre enregistrement**, créez un enregistrement à l’aide des valeurs de la ligne suivante dans le tableau, puis sélectionnez **à nouveau Créer des enregistrements**.

   :::image type="content" source="../../media/dns-aws/aws-domians-srv-create-records.png" alt-text="Sélectionnez Créer des enregistrements.":::

> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Ajoutez les deux enregistrements CNAME requis pour Skype Entreprise

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sous **Domaines**, sélectionnez **Domaines inscrits**.

1. Sous **Nom de domaine**, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque** : Si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez **Créer une zone hébergée** et effectuez les étapes avant de passer à l’étape suivante.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Nom de domaine**, sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Sélectionnez Créer un enregistrement.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choisissez les valeurs **de stratégie Type** et **Routage** dans les listes déroulantes.)

    |Nom de l’enregistrement|Type d’enregistrement|Valeur|Durée de vie|Stratégie de routage|
    |:-----|:-----|:-----|:-----|:-----|
    |sip|CNAME - Nom canonique|sipdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|300|Simple|
    |lyncdiscover|CNAME - Nom canonique|webdir.online.lync.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|300|Simple|

1. Pour ajouter l’autre enregistrement CNAME, sélectionnez **Ajouter un autre enregistrement**, créez un enregistrement à l’aide des valeurs de la ligne suivante dans la table.

1. Sélectionnez **Créer des enregistrements**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Sélectionnez Créer des enregistrements.":::

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et mobile Gestion des appareils pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. Mobile Gestion des appareils a besoin de deux enregistrements CNAME pour permettre aux utilisateurs d’inscrire des appareils au service.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Ajoutez les deux enregistrements CNAME requis pour Mobile Gestion des appareils

1. Pour commencer, accédez à la page de vos domaines sur le site AWS en utilisant [ce lien](https://console.aws.amazon.com/route53/home). Avant toute chose, vous serez invité à vous connecter.

1. Dans la page d’accueil, sous **Domaines**, sélectionnez **Domaines inscrits**.

1. Sous **Nom de domaine**, sélectionnez le domaine que vous souhaitez configurer dans Microsoft 365.

    **Remarque** : Si vous n’avez pas créé de zone hébergée pour votre domaine, sélectionnez **Créer une zone hébergée** et effectuez les étapes avant de passer à l’étape suivante.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Gérer LE DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Sélectionnez Gérer DNS dans la liste déroulante.":::

1. Sous **Nom de domaine**, sélectionnez le nom de domaine pour la version de zone hébergée du domaine que vous souhaitez vérifier.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Sélectionnez le nom du domaine.":::

1. Sélectionnez **Créer un enregistrement**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Sélectionnez Créer un enregistrement.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.

    (Choisissez les valeurs **de stratégie Type** et **Routage** dans les listes déroulantes.)

    |Nom de l’enregistrement|Type d’enregistrement|Valeur|Durée de vie|Stratégie de routage|
    |:-----|:-----|:-----|:-----|:-----|
    |enterpriseregistration|CNAME - Nom canonique|enterpriseregistration.windows.net. <br/> **Cette valeur DOIT se terminer par un point (.)**|300|Simple|
    |enterpriseenrollment|CNAME - Nom canonique|enterpriseenrollment-s.manage.microsoft.com. <br/> **Cette valeur DOIT se terminer par un point (.)**|300|Simple|

1. Pour ajouter l’autre enregistrement CNAME, sélectionnez **Ajouter un autre enregistrement**, créez un enregistrement à l’aide des valeurs de la ligne suivante dans la table.

1. Sélectionnez **Créer des enregistrements**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Sélectionnez Créer des enregistrements.":::

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).
