---
title: Bureaux d’enregistrement de domaine avec limitations de configuration
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- MET150
ROBOTS: NOINDEX
description: Certains bureaux d’enregistrement de domaine offrent des services limités, ce qui signifie que des fonctionnalités Microsoft peuvent ne pas fonctionner dans tous les domaines.
ms.openlocfilehash: 361faf93e2b923b0c16ce7051f43663998be4dc7
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68191186"
---
# <a name="domain-registrars-with-setup-limitations"></a>Bureaux d’enregistrement de domaine avec limitations de configuration

[Créer des enregistrements DNS auprès de DNSMadeEasy pour Microsoft](#create-dns-records-at-dnsmadeeasy-for-microsoft)\
[Créer des enregistrements DNS auprès de easyDNS pour Microsoft](#create-dns-records-at-easydns-for-microsoft)\
[Créer des enregistrements DNS auprès de Freenom pour Microsoft](#create-dns-records-at-freenom-for-microsoft)\
[Créer des enregistrements DNS auprès de MyDomain pour Microsoft](#create-dns-records-at-mydomain-for-microsoft)\
[Créer des enregistrements DNS pour Microsoft à l'aide de DNS Windows](#create-dns-records-for-microsoft-using-windows-based-dns)\
[Créer des enregistrements DNS lorsque votre domaine est géré par Google (eNom)](#create-dns-records-when-your-domain-is-managed-by-google-enom)\
[Créer des enregistrements DNS auprès de 1&1 IONOS pour Microsoft](#create-dns-records-at-11-ionos-for-microsoft)

Certains bureaux d’enregistrement de domaine ont des limitations de services importantes, ce qui signifie que des fonctionnalités Microsoft peuvent ne pas fonctionner dans tous les domaines. Les limitations spécifiques de certains bureaux d’enregistrement sont identifiés dans cet article. 

## <a name="create-dns-records-at-dnsmadeeasy-for-microsoft"></a>Créer des enregistrements DNS sur DNSMadeEasy pour Microsoft

For DNSMadeEasy accounts, the domain you added was purchased from a separate domain registrar. DNSMadeEasy does not offer domain registration services. Your ability to log in at DNSMadeEasy and create the DNS record is sufficient proof of ownership.

## <a name="create-dns-records-at-easydns-for-microsoft"></a>Créer des enregistrements DNS sur easyDNS pour Microsoft

Les enregistrements SRV ne sont pour le moment pas disponibles sous les packages de service easyDNS. Vous devrez mettre à niveau vers un niveau de service supérieur avec easyDNS pour ajouter des enregistrements SRV nécessaires pour Teams.

## <a name="create-dns-records-at-freenom-for-microsoft"></a>Créer des enregistrements DNS auprès de Freenom pour Microsoft

The Freenom website doesn't support adding SRV records, which means that several Teams and Email features won't work. No matter which Microsoft plan you use, there are significant service limitations, and you may want to switch to a different DNS hosting provider.

## <a name="create-dns-records-at-mydomain-for-microsoft"></a>Créer des enregistrements DNS auprès de MyDomain pour Microsoft

The MyDomain website doesn't support SRV records, which means several Teams and Email features won't work. No matter which Microsoft plan you use, if you manage your DNS records at MyDomain, there are significant service limitations, and you might want to switch to a different DNS hosting provider.

## <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Créer des enregistrements pour Microsoft à l'aide de DNS Windows

Accédez à la page contenant les enregistrements DNS pour votre domaine. Si vous utilisez Windows Server 2008, accédez à **Démarrer**, **Exécuter**. Si vous utilisez Windows Server 2012, appuyez sur la **touche Windows** et **r**. Tapez **dnsmgmnt.msc**, puis sélectionnez **OK**. Dans le Gestionnaire DNS, développez **nom du serveur DNS**, **Zones de recherche directes**. Sélectionnez votre domaine. Vous pouvez à présent créer les enregistrements DNS.

## <a name="create-dns-records-when-your-domain-is-managed-by-google-enom"></a>Créer des enregistrements DNS lorsque votre domaine est géré par Google (eNom)

If you purchased your domain through Google while signing up for your Google Apps for Work account, your DNS records are managed by Google but registered with eNom. You can access eNom, and create DNS, through the Google Domains page.

## <a name="create-dns-records-at-11-ionos-for-microsoft"></a>Créer des enregistrements DNS auprès de 1&1 IONOS pour Microsoft

1&1 IONOS n'autorise pas un domaine à avoir à la fois un enregistrement MX et un enregistrement CNAME de découverte automatique de niveau supérieur. Cela limite les méthodes qui s'offrent à vous pour configurer Exchange Online pour Microsoft. Il existe pourtant une solution de contournement, mais nous vous recommandons de la mettre en place uniquement si vous savez déjà créer des sous-domaines sur 1&1 IONOS.

Si malgré cette limitation de service, vous décidez de gérer vos propres enregistrements DNS Microsoft sur 1&1 IONOS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour e-mail, Skype Entreprise Online, etc.

1&1 IONOS requires a workaround so that you can use an MX record together with the CNAME records required for Microsoft email services. This workaround requires you to create a set of subdomains at 1&1 IONOS, and to assign them to CNAME records.

> [!NOTE]
> Make sure that you have at least two available subdomains before starting this procedure. We recommend this solution only if you already have experience with creating subdomains at 1&1 IONOS.

### <a name="basic-cname-records"></a>Enregistrements CNAME de base

1.  To get started, go to your domains page at 1&1 IONOS. You'll be prompted to log in.

1.  Sélectionnez **Gérer les domaines**.

1.  Sur la page Centre des domaines, recherchez le domaine que vous voulez mettre à jour, puis sélectionnez **Gérer les sous-domaines**. Vous créez maintenant deux sous-domaines et vous leur définissez la valeur **Alias** (cette action est nécessaire car 1&1 IONOS ne prend en charge qu’un seul enregistrement CNAME de niveau supérieur et que Microsoft requiert plusieurs enregistrements CNAME).

1.  Tout d'abord, vous devez créer le sous-domaine de découverte automatique. Dans la section **Vue d'ensemble des sous-domaines**, sélectionnez **Créer un sous-domaine**.

1.  In the **Create Subdomain** box for the new subdomain, type or copy and paste only the **Create Subdomain** value from the following table. (You'll add the **Alias** value at a later step.)

    |Create Subdomain (Créer un sous-domaine)|Alias|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1.  Sélectionnez **Créer un sous-domaine**.

1.  Dans la section **Vue d'ensemble des sous-domaines**, recherchez le sous-domaine découverte automatique que vous venez de créer, puis sélectionnez le contrôle de volet (v) correspondant à ce sous-domaine.

1.  Dans la zone **Paramètres des sous-domaines**, sélectionnez **Modifier les paramètres DNS**.

1.  Dans la section **A/AAAA Records (IP Addresses)**, dans la zone **IP address (A Record)**, sélectionnez **CNAME**.

1. Dans la zone **Alias :**, tapez ou copiez-collez uniquement la valeur **Alias** du tableau suivant.

    |Create Subdomain (Créer un sous-domaine)|Alias|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1. Cochez la case correspondant à la clause d'exclusion de responsabilité **I am aware** (J'accepte).

1. Sélectionnez **Enregistrer**.

### <a name="additional-cname-records"></a>Enregistrements CNAME supplémentaires

The additional CNAME records in the following procedure enable Skype for Business Online services. Use the same steps that you used for the two CNAME records you already created.

**Créer le troisième le sous-domaine (Lyncdiscover)**

1.  Dans la section **Vue d'ensemble des sous-domaines**, sélectionnez **Créer un sous-domaine**.

1.  In the **Create Subdomain** box for the new subdomain, type or copy and paste only the **Create Subdomain** value from the following table. (You'll add the **Alias** value at a later step.)

    |Créer un sous-domaine|Alias|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Sélectionnez **Créer un sous-domaine**.

1.  Sur la page Centre des domaines, sélectionnez **Gérer les sous-domaines**.

1.  In the **Subdomain Overview** section, find the lyncdiscover subdomain that you just created, and then select the Panel (v) control for that subdomain. In the **Subdomain Settings** area, select **Edit DNS Settings**.

1.  Dans la section **A/AAAA Records (IP Addresses)**, dans la zone **IP address (A Record)**, sélectionnez **CNAME**.

1.  Dans la zone **Alias :**, tapez ou copiez-collez uniquement la valeur **Alias** du tableau suivant.

    |Create Subdomain (Créer un sous-domaine)|Alias|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Cochez la case correspondant à la clause d'exclusion de responsabilité **J'accepte**, puis sélectionnez **Enregistrer**.

1.  Dans la zone de dialogue **Modifier les paramètres DNS**, sélectionnez **Oui**.

**Créez le quatrième sous-domaine (SIP)**

1.  Dans la section **Vue d'ensemble des sous-domaines**, sélectionnez **Créer un sous-domaine**.

1.  In the **Create Subdomain** box for the new subdomain, type or copy and paste only the **Create Subdomain** value from the following table. (You'll add the **Alias** value a later step.)

    |Créer un sous-domaine|Alias|
    |:----|:----|
    |sip|sipdir.online.lync.com|  

1.  Sélectionnez **Créer un sous-domaine**.

1.  Sur la page Centre des domaines, sélectionnez **Gérer les sous-domaines**.

1.  Dans la section **Vue d'ensemble des sous-domaines**, recherchez le sous-domaine sip que vous venez de créer, puis sélectionnez le contrôle de volet (v) correspondant à ce sous-domaine. <br/> Dans la zone **Paramètres des sous-domaines**, sélectionnez **Modifier les paramètres DNS**.

1.  Dans la section **A/AAAA Records (IP Addresses)**, dans la zone **IP address (A Record)**, sélectionnez **CNAME**.

1.  Dans la zone **Alias :**, tapez ou copiez-collez uniquement la valeur **Alias** du tableau suivant.

    |Create Subdomain (Créer un sous-domaine)|Alias|
    |:----|:----|
    |sip|sipdir.online.lync.com|

1.  Cochez la case correspondant à la clause d'exclusion de responsabilité **J'accepte**, puis sélectionnez **Enregistrer**.

1.  Dans la zone de dialogue **Modifier les paramètres DNS**, sélectionnez **Oui**.

### <a name="cname-records-needed-for-mdm"></a>Enregistrements CNAME requis pour MDM

Suivez la procédure que vous avez utilisée pour les quatre autres enregistrements CNAME, mais fournissez ces valeurs :

|Créer un sous-domaine|Alias|
|:----|:----|
|enterpriseregistration|enterpriseregistration.windows.net|
|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|
