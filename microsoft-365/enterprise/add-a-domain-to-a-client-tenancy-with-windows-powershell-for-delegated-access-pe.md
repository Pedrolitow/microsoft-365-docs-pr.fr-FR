---
title: Ajouter un domaine à une location de client avec Windows PowerShell pour les partenaires DAP
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Résumé : Utilisez PowerShell pour Microsoft 365 pour ajouter un autre nom de domaine à un locataire client existant.'
ms.openlocfilehash: c4dcdb34f9065009ccaa77d23222601506b537b5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099035"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Ajout d’un domaine à la location d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez créer et associer de nouveaux domaines à la location de votre client à PowerShell pour Microsoft 365 plus rapidement que l’utilisation de la Centre d'administration Microsoft 365.

Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés. Ils regroupent Microsoft 365 abonnements dans leurs offres de service à leurs clients. Lorsqu’ils vendent un abonnement Microsoft 365, ils reçoivent automatiquement des autorisations d’administration au nom de (AOBO) aux locataires du client afin qu’ils puissent administrer et signaler les locations du client.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

Les procédures décrites dans cette rubrique vous obligent à vous connecter à [Connecter à Microsoft 365 avec PowerShell](connect-to-microsoft-365-powershell.md).

Vous avez aussi besoin des informations d’identification d’administrateur de la location du partenaire.

Vous avez également besoin des informations suivantes :

- Vous avez besoin du nom de domaine complet (FQDN) que votre client souhaite utiliser.

- Vous avez besoin du code **TenantID** du client.

- Le nom de domaine complet doit être enregistré auprès d'un bureau d'enregistrement de domaines DNS Internet, comme GoDaddy. Pour plus d'informations sur l'inscription publique d'un nom de domaine, voir [Comment acheter un nom de domaine](../admin/get-help-with-domains/buy-a-domain-name.md).

- Vous devez savoir comment ajouter un enregistrement TXT à la zone DNS enregistrée pour votre bureau d’enregistrement DNS. Pour plus d’informations sur l’ajout d’un enregistrement TXT, consultez [Ajouter des enregistrements DNS pour connecter votre domaine](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d’enregistrement DNS.

## <a name="create-domains"></a>Création de domaines

 Vos clients vous demanderont probablement de créer des domaines supplémentaires à associer à leur location, car ils ne voudront probablement pas que le domaine\<domain>.onmicrosoft.comsoit le domaine principal qui représente leur identité d'entreprise aux yeux du monde entier. Cette procédure vous guide au fil du processus de création d'un domaine associé à la location de votre client.

> [!NOTE]
> Pour effectuer certaines de ces opérations, le compte d’administrateur partenaire avec lequel vous vous connectez doit être défini sur **Administration complète** pour l’attribution d’un **accès administratif aux entreprises que vous prenez en charge** dans les détails du compte d’administrateur dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Pour plus d’informations sur la gestion des rôles d’administrateur partenaire, consultez [Partenaires : Offre d’administration déléguée](https://go.microsoft.com/fwlink/p/?LinkId=532435).

### <a name="create-the-domain-in-azure-active-directory"></a>Création du domaine dans Azure Active Directory

Cette commande crée le domaine dans Azure Active Directory, mais ne l'associe pas au domaine inscrit publiquement. Cela se fait lorsque vous prouvez que vous possédez le domaine inscrit publiquement auprès de Microsoft Microsoft 365 pour les entreprises.

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

Avant Microsoft 365 commencez à accepter le trafic dirigé vers le nom de domaine inscrit publiquement, vous devez prouver que vous êtes propriétaire et que vous disposez d’autorisations d’administrateur sur le domaine. Pour prouver que vous êtes propriétaire du domaine, créez un enregistrement TXT dans le domaine. Un enregistrement TXT n'a aucun effet sur votre domaine, et il peut être supprimé une fois qu'il est établi que vous êtes propriétaire du domaine. Pour créer les enregistrements TXT, suivez les procédures [d’ajout d’enregistrements DNS pour connecter votre domaine](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Si ces procédures ne fonctionnent pas pour vous, vous devez rechercher les procédures pour votre bureau d'enregistrement DNS.

Confirmez la création de l'enregistrement TXT via nslookup. Suivez cette syntaxe.

```console
nslookup -type=TXT <FQDN of registered domain>
```

Elle vous fournira des résultats semblables à ceci :

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>Valider la propriété du domaine dans Microsoft 365

Dans cette dernière étape, vous validez pour Microsoft 365 que vous êtes propriétaire du domaine enregistré publiquement. Après cette étape, Microsoft 365 commence à accepter le trafic acheminé vers le nouveau nom de domaine. Pour terminer la création du domaine et le processus d’inscription, exécutez cette commande.

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
