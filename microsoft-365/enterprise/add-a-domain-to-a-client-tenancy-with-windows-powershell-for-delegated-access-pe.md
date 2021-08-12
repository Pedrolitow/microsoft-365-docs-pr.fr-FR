---
title: Ajouter un domaine à une location de client avec Windows PowerShell pour les partenaires DAP
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Résumé : Utilisez PowerShell pour Microsoft 365 ajouter un autre nom de domaine à un client existant.'
ms.openlocfilehash: a7a1039f29b73cef50ed14fe6ad3189faf3365087e9526f5517b866ac0440f77
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53835450"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Ajout d’un domaine à la location d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez créer et associer de nouveaux domaines à la location de votre client avec PowerShell pour Microsoft 365 plus rapidement que d’utiliser le Centre d’administration Microsoft 365.

Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés. Ils regroupent Microsoft 365 abonnements dans leurs offres de services à leurs clients. Lorsqu’ils vendent un abonnement Microsoft 365, ils se voient automatiquement accorder des autorisations Administrer de la part de (AOBO) aux locations du client afin de pouvoir administrer les locations du client et en signaler les locations.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

Les procédures de cette rubrique exigent que vous vous connectiez à [Connecter à Microsoft 365 avec PowerShell.](connect-to-microsoft-365-powershell.md)

Vous avez aussi besoin des informations d’identification d’administrateur de la location du partenaire.

Vous avez également besoin des informations suivantes :

- Vous avez besoin du nom de domaine complet (FQDN) que votre client souhaite utiliser.

- Vous avez besoin du code **TenantID** du client.

- Le nom de domaine complet doit être enregistré auprès d'un bureau d'enregistrement de domaines DNS Internet, comme GoDaddy. Pour plus d'informations sur l'inscription publique d'un nom de domaine, voir [Comment acheter un nom de domaine](../admin/get-help-with-domains/buy-a-domain-name.md).

- Vous devez savoir comment ajouter un enregistrement TXT à la zone DNS enregistrée pour votre bureau d’enregistrement DNS. Pour plus d’informations sur l’ajout d’un enregistrement TXT, voir Ajouter des enregistrements [DNS pour connecter votre domaine.](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d’enregistrement DNS.

## <a name="create-domains"></a>Création de domaines

 Vos clients vous demanderont probablement de créer des domaines supplémentaires à associer à leur location, car ils ne voudront probablement pas que le domaine<domain>.onmicrosoft.comsoit le domaine principal qui représente leur identité d'entreprise aux yeux du monde entier. Cette procédure vous guide au fil du processus de création d'un domaine associé à la location de votre client.

> [!NOTE]
> Pour effectuer certaines de ces opérations, le compte d’administrateur partenaire avec qui vous vous connectez doit être définie sur **Administration** complète pour l’attribution d’un accès **administratif** aux sociétés que vous supportez et qui se trouvent dans les détails du compte d’administrateur dans le Centre d’administration Microsoft 365. Pour plus d’informations sur la gestion des rôles d’administrateur partenaire, voir [Partenaires : proposer une administration déléguée.](https://go.microsoft.com/fwlink/p/?LinkId=532435)

### <a name="create-the-domain-in-azure-active-directory"></a>Création du domaine dans Azure Active Directory

Cette commande crée le domaine dans Azure Active Directory, mais ne l'associe pas au domaine inscrit publiquement. Cela se produit lorsque vous prouvez que vous êtes propriétaire du domaine inscrit publiquement à Microsoft Microsoft 365 entreprise.

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Obtention des données pour l’enregistrement de vérification TXT DNS

 Microsoft 365 génère les données spécifiques que vous devez placer dans l’enregistrement de vérification TXT DNS. Pour obtenir les données, exécutez cette commande.

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Elle vous fournira des résultats semblables à :

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> Vous aurez besoin de ce texte pour créer l'enregistrement TXT dans la zone DNS enregistrée publiquement. Copiez-le et enregistrez-le.

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Ajout d’un enregistrement TXT à la zone DNS enregistrée publiquement

Avant Microsoft 365 commencer à accepter le trafic qui est dirigé vers le nom de domaine inscrit publiquement, vous devez prouver que vous êtes propriétaire et que vous avez des autorisations d’administrateur sur le domaine. Pour prouver que vous êtes propriétaire du domaine, créez un enregistrement TXT dans le domaine. Un enregistrement TXT n'a aucun effet sur votre domaine, et il peut être supprimé une fois qu'il est établi que vous êtes propriétaire du domaine. Pour créer les enregistrements TXT, suivez les procédures de la procédure d’ajout d’enregistrements [DNS pour connecter votre domaine.](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d'enregistrement DNS.

Confirmez la création de l'enregistrement TXT via nslookup. Suivez cette syntaxe.

```console
nslookup -type=TXT <FQDN of registered domain>
```

Elle vous fournira des résultats semblables à ceci :

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>Valider la propriété du domaine dans Microsoft 365

Dans cette dernière étape, vous validez pour Microsoft 365 que vous êtes propriétaire du domaine inscrit publiquement. Après cette étape, Microsoft 365 commencer à accepter le trafic acheminé vers le nouveau nom de domaine. Pour terminer la création du domaine et le processus d’inscription, exécutez cette commande.

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Cette commande ne renvoie aucun résultat, par conséquent, pour vérifier qu’elle a fonctionné, exécutez la commande suivante.

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Celle-ci renverra des résultats semblables à ce qui suit.

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

## <a name="see-also"></a>Voir aussi

[Aide pour les partenaires](https://go.microsoft.com/fwlink/p/?LinkID=533477)
