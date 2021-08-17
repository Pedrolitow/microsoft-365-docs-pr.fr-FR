---
title: Bureaux d’enregistrement de domaine avec limitations de configuration
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- MET150
ROBOTS: NOINDEX
description: Certains bureaux d’enregistrement de domaine offrent des services limités, ce qui signifie que des fonctionnalités Microsoft peuvent ne pas fonctionner dans tous les domaines.
ms.openlocfilehash: 3af1503b99290611d04b1012ce5087f719f01315
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58247289"
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

Pour les comptes DNSMadeEasy, le domaine que vous avez ajouté a été acheté auprès d’un bureau d’enregistrement de domaines distinct. DNSMadeEasy ne propose pas de services d’enregistrement de domaines. Votre connexion au site DNSMadeEasy et la création de l’enregistrement DNS constituent une preuve de propriété suffisante.

## <a name="create-dns-records-at-easydns-for-microsoft"></a>Créer des enregistrements DNS sur easyDNS pour Microsoft

Les enregistrements SRV ne sont pour le moment pas disponibles sous les packages de service easyDNS. Vous devrez mettre à niveau vers un niveau de service supérieur avec easyDNS pour ajouter des enregistrements SRV nécessaires pour Teams.

## <a name="create-dns-records-at-freenom-for-microsoft"></a>Créer des enregistrements DNS auprès de Freenom pour Microsoft

Le site web Freenom ne prend pas en charge l’ajout d’enregistrements SRV, ce qui signifie que plusieurs fonctionnalités Teams et Courrier ne fonctionnent pas. Quelle que soit l’offre Microsoft que vous utilisez, il existe des limitations de service importantes et vous pouvez basculer vers un autre fournisseur d’hébergement DNS.

## <a name="create-dns-records-at-mydomain-for-microsoft"></a>Créer des enregistrements DNS auprès de MyDomain pour Microsoft

Le site web MyDomain ne prend pas en charge les enregistrements SRV, ce qui signifie que plusieurs fonctionnalités Teams et Courrier ne fonctionnent pas. Quelle que soit l’offre Microsoft que vous utilisez, si vous gérez vos enregistrements DNS via MyDomain, il existe des limitations de service importantes et vous pouvez basculer vers un autre fournisseur d’hébergement DNS.

## <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Créer des enregistrements pour Microsoft à l'aide de DNS Windows

Accédez à la page contenant les enregistrements DNS pour votre domaine. Si vous utilisez Windows Server 2008, accédez à **Démarrer**, **Exécuter**. Si vous utilisez Windows Server 2012, appuyez sur la **touche Windows** et **r**. Tapez **dnsmgmnt.msc**, puis sélectionnez **OK**. Dans le Gestionnaire DNS, développez **nom du serveur DNS**, **Zones de recherche directes**. Sélectionnez votre domaine. Vous pouvez à présent créer les enregistrements DNS.

## <a name="create-dns-records-when-your-domain-is-managed-by-google-enom"></a>Créer des enregistrements DNS lorsque votre domaine est géré par Google (eNom)

Si vous avez acheté votre domaine via Google lors de la création de votre compte Google Apps for Work, vos enregistrements DNS sont gérés par Google, mais inscrits auprès d’eNom. Vous pouvez accéder à eNom et créer un DNS via la page Google Domains.

## <a name="create-dns-records-at-11-ionos-for-microsoft"></a>Créer des enregistrements DNS auprès de 1&1 IONOS pour Microsoft

1&1 IONOS n'autorise pas un domaine à avoir à la fois un enregistrement MX et un enregistrement CNAME de découverte automatique de niveau supérieur. Cela limite les méthodes qui s'offrent à vous pour configurer Exchange Online pour Microsoft. Il existe pourtant une solution de contournement, mais nous vous recommandons de la mettre en place uniquement si vous savez déjà créer des sous-domaines sur 1&1 IONOS.

Si malgré cette limitation de service, vous décidez de gérer vos propres enregistrements DNS Microsoft sur 1&1 IONOS, suivez les étapes décrites dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour e-mail, Skype Entreprise Online, etc.

1&1 IONOS nécessite une solution de contournement pour pouvoir utiliser un enregistrement MX conjointement avec les enregistrements CNAME qui sont nécessaires pour obtenir les services de e-mails Microsoft. Cette solution nécessite la création d’un ensemble de sous-domaines sur 1&1 IONOS, et leur attribution aux enregistrements CNAME.

> [!NOTE]
> Vérifiez que vous avez au moins deux sous-domaines disponibles avant de commencer cette procédure. Nous vous recommandons cette solution uniquement si vous avez de l’expérience en création de sous-domaines sur 1&1 IONOS.

### <a name="basic-cname-records"></a>Enregistrements CNAME de base

1.  Pour commencer, accédez à la page de vos domaines sur le site 1&1 IONOS. Vous serez invité à vous connecter.

1.  Sélectionnez **Gérer les domaines**.

1.  Sur la page Centre des domaines, recherchez le domaine que vous voulez mettre à jour, puis sélectionnez **Gérer les sous-domaines**. Vous créez maintenant deux sous-domaines et vous leur définissez la valeur **Alias** (cette action est nécessaire car 1&1 IONOS ne prend en charge qu’un seul enregistrement CNAME de niveau supérieur et que Microsoft requiert plusieurs enregistrements CNAME).

1.  Tout d'abord, vous devez créer le sous-domaine de découverte automatique. Dans la section **Vue d'ensemble des sous-domaines**, sélectionnez **Créer un sous-domaine**.

1.  Dans la zone **Créer un sous-domaine** correspondant au nouveau sous-domaine, tapez ou copiez-collez uniquement la valeur **Créer un sous-domaine** du tableau suivant. (Vous ajouterez la valeur **Alias** au cours d’une étape ultérieure.)

    |Créer un sous-domaine|Alias|
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

Les enregistrements CNAME supplémentaires de la procédure suivante activent les services Skype Entreprise Online. Utilisez les mêmes étapes que pour les deux enregistrements CNAME que vous avez déjà créés.

**Créer le troisième le sous-domaine (Lyncdiscover)**

1.  Dans la section **Vue d'ensemble des sous-domaines**, sélectionnez **Créer un sous-domaine**.

1.  Dans la zone **Créer un sous-domaine** correspondant au nouveau sous-domaine, tapez ou copiez-collez uniquement la valeur **Créer un sous-domaine** du tableau suivant. (Vous ajouterez la valeur **Alias** au cours d’une étape ultérieure.)

    |Créer un sous-domaine|Alias|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Sélectionnez **Créer un sous-domaine**.

1.  Sur la page Centre des domaines, sélectionnez **Gérer les sous-domaines**.

1.  Dans la section **Vue d'ensemble des sous-domaines**, recherchez le sous-domaine lyncdiscover que vous venez de créer, puis sélectionnez le contrôle de volet (v) correspondant à ce sous-domaine. Dans la zone **Paramètres des sous-domaines**, sélectionnez **Modifier les paramètres DNS**.

1.  Dans la section **A/AAAA Records (IP Addresses)**, dans la zone **IP address (A Record)**, sélectionnez **CNAME**.

1.  Dans la zone **Alias :**, tapez ou copiez-collez uniquement la valeur **Alias** du tableau suivant.

    |Create Subdomain (Créer un sous-domaine)|Alias|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Cochez la case correspondant à la clause d'exclusion de responsabilité **J'accepte**, puis sélectionnez **Enregistrer**.

1.  Dans la zone de dialogue **Modifier les paramètres DNS**, sélectionnez **Oui**.

**Créez le quatrième sous-domaine (SIP)**

1.  Dans la section **Vue d'ensemble des sous-domaines**, sélectionnez **Créer un sous-domaine**.

1.  Dans la zone **Créer un sous-domaine** correspondant au nouveau sous-domaine, tapez ou copiez-collez uniquement la valeur **Créer un sous-domaine** du tableau suivant. (Vous ajouterez la valeur **Alias** au cours d’une étape ultérieure.)

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
