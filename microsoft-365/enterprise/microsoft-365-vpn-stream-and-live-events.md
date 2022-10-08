---
title: Considérations spéciales sur les événements stream et en direct dans les environnements VPN
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Considérations spéciales sur les événements stream et en direct dans les environnements VPN
ms.openlocfilehash: 7325c228c3b9bd7ffb808a56da09415709d3fdfb
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68187886"
---
# <a name="special-considerations-for-stream-and-live-events-in-vpn-environments"></a>Considérations spéciales sur les événements stream et en direct dans les environnements VPN

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent de l’optimisation de Microsoft 365 pour les utilisateurs distants.

>- Pour obtenir une vue d’ensemble de l’utilisation du tunneling fractionné VPN pour optimiser la connectivité Microsoft 365 pour les utilisateurs distants, consultez [Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Pour obtenir des conseils détaillés sur l’implémentation du tunneling fractionné VPN, consultez [Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Pour obtenir la liste détaillée des scénarios de tunneling fractionné [VPN, consultez les scénarios de tunneling fractionné VPN courants pour Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Pour obtenir des conseils sur la sécurisation du trafic multimédia Teams dans les environnements de tunneling fractionné VPN, consultez [Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md).
>- Pour plus d’informations sur l’optimisation des performances des locataires Microsoft 365 dans le monde entier pour les utilisateurs en Chine, consultez [l’optimisation des performances de Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md).

Le trafic d’événements en direct Microsoft 365 (cela inclut les participants aux événements en direct produits par Teams et ceux produits avec un encodeur externe via Teams, Stream ou Yammer) et le trafic de flux à la demande est actuellement classé par **défaut par rapport** **à Optimize** dans la [liste URL/IP du service](urls-and-ip-address-ranges.md). Ces points de terminaison sont classés par **défaut** , car ils sont hébergés sur des CDN qui peuvent également être utilisés par d’autres services. Les clients préfèrent généralement proxyer ce type de trafic et appliquer tous les éléments de sécurité normalement effectués sur des points de terminaison tels que ceux-ci.

De nombreux clients ont demandé les données URL/IP nécessaires pour connecter leurs utilisateurs aux événements stream/en direct directement à partir de leur connexion Internet locale, plutôt que d’acheminer le trafic à volume élevé et sensible à la latence via l’infrastructure VPN. En règle générale, cela n’est pas possible sans des espaces de noms dédiés et des informations IP précises pour les points de terminaison, ce qui n’est pas fourni pour les points de terminaison Microsoft 365 classés par **défaut**.

Utilisez les étapes suivantes pour activer la connectivité directe pour le service Stream/Live Events à partir de clients utilisant un VPN de tunnel forcé. Cette solution est destinée à offrir aux clients une option permettant d’éviter le routage du trafic d’événements en direct sur vpN, alors qu’il y a un trafic réseau élevé en raison de scénarios de travail à domicile. Si possible, il est recommandé d’accéder au service par le biais d’un proxy d’inspection.

>[!NOTE]
>À l’aide de cette solution, il peut y avoir des éléments de service qui ne sont pas résolus en adresses IP fournies et par conséquent parcourent le VPN, mais la majeure partie du trafic à volume élevé, comme les données de streaming, le doivent. Il peut y avoir d’autres éléments en dehors de l’étendue des événements en direct/flux qui sont interceptés par ce déchargement, mais ceux-ci doivent être limités, car ils doivent répondre à la fois au nom de domaine complet _et_ à la correspondance IP avant d’aller directement.

>[!IMPORTANT]
>Il est conseillé aux clients de peser le risque d’envoyer davantage de trafic qui contourne le VPN par rapport au gain de performances des événements en direct.

Pour implémenter l’exception de tunnel forcé pour les événements en direct teams et stream, les étapes suivantes doivent être appliquées :

## <a name="1-configure-external-dns-resolution"></a>1. Configurer la résolution DNS externe

Les clients ont besoin d’une résolution DNS externe et récursive pour être disponibles afin que les noms d’hôtes suivants puissent être résolus en adresses IP.

- \*.azureedge.net
- \*.media.azure.net
- \*.bmc.cdn.office.net

**\*.azureedge.net** est utilisé pour les événements Stream ([configurer des encodeurs pour la diffusion en continu en direct dans Microsoft Stream - Microsoft Stream | Microsoft Docs](/stream/live-encoder-setup)).

**\*.media.azure.net** et **\*.bmc.cdn.office.net** sont utilisés pour les événements en direct générés par Teams (événements de démarrage rapide, RTMP-In événements pris en charge [ID de feuille de route 84960]) planifiés à partir du client Teams.

 Certains de ces points de terminaison sont partagés avec d’autres éléments en dehors des événements Stream/Live. Il n’est pas recommandé d’utiliser simplement ces noms de domaine complets pour configurer le déchargement VPN, même si cela est techniquement possible dans votre solution VPN (par exemple, s’il fonctionne au nom de domaine complet plutôt qu’à l’adresse IP).

Les noms de domaine complets ne sont pas requis dans la configuration VPN, ils sont uniquement destinés à être utilisés dans les fichiers PAC en association avec les adresses IP pour envoyer le trafic direct approprié.

## <a name="2-implement-pac-file-changes-where-required"></a>2. Implémenter les modifications de fichier PAC (si nécessaire)

Pour les organisations qui utilisent un fichier PAC pour acheminer le trafic par le biais d’un proxy sur vpN, cela est normalement réalisé à l’aide de noms de domaine complets. Toutefois, avec Stream/Live Events, les noms d’hôtes fournis contiennent des caractères génériques tels que **\*.azureedge.net**, qui englobe également d’autres éléments pour lesquels il n’est pas possible de fournir des listes IP complètes. Par conséquent, si la requête est envoyée directement en fonction de la correspondance de caractère générique DNS seule, le trafic vers ces points de terminaison sera bloqué, car il n’y a pas d’itinéraire via le chemin d’accès direct pour celui-ci à [l’étape 3](#3-configure-routing-on-the-vpn-to-enable-direct-egress) plus loin dans cet article.

Pour résoudre ce problème, nous pouvons fournir les adresses IP suivantes et les utiliser en combinaison avec les noms d’hôte dans un exemple de fichier PAC, comme décrit à [l’étape 1](#1-configure-external-dns-resolution). Le fichier PAC vérifie si l’URL correspond à celles utilisées pour les événements stream/en direct, puis s’il le fait, il vérifie également si l’adresse IP retournée à partir d’une recherche DNS correspond à celles fournies pour le service. Si _les deux_ correspondent, le trafic est routée directement. Si l’un des éléments (FQDN/IP) ne correspond pas, le trafic est envoyé au proxy. Par conséquent, la configuration garantit que tout ce qui se résout en adresse IP en dehors de l’étendue de l’adresse IP et des espaces de noms définis traverse normalement le proxy via le VPN.

### <a name="gathering-the-current-lists-of-cdn-endpoints"></a>Collecte des listes actuelles de points de terminaison CDN

Live Events utilise plusieurs fournisseurs CDN pour diffuser en continu vers les clients, afin de fournir une couverture, une qualité et une résilience optimales. Actuellement, le CDN Azure de Microsoft et de Verizon est utilisé. Au fil du temps, cela peut être modifié en raison de situations telles que la disponibilité régionale. Cet article est une source qui vous permet de rester à jour sur les plages d’adresses IP.

Pour Azure CDN à partir de Microsoft, vous pouvez télécharger la liste à partir de [Download Azure IP Ranges and Service Tags ( Public Cloud from Official Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=56519) ), vous devez rechercher spécifiquement la balise de service *AzureFrontdoor.Frontend* dans le JSON ; *addressPrefixes* affiche les sous-réseaux IPv4/IPv6. Au fil du temps, les adresses IP peuvent changer, mais la liste des balises de service est toujours mise à jour avant qu’elles ne soient utilisées.

Pour Azure CDN de Verizon (Edgecast), vous pouvez trouver une liste exhaustive à l’aide de [nœuds Edge - Liste](/rest/api/cdn/edge-nodes/list) (cliquez sur **Essayer**) - vous devez rechercher spécifiquement la section **Verizon Premium\_**. Notez que cette API affiche toutes les adresses IP Edgecast (origin et Anycast). Actuellement, il n’existe pas de mécanisme permettant à l’API de faire la distinction entre l’origine et Anycast.

Pour implémenter cela dans un fichier PAC, vous pouvez utiliser l’exemple suivant qui envoie le trafic Direct Microsoft 365 Optimize (meilleure pratique recommandée) par le biais du nom de domaine complet et le trafic critique stream/événements en direct via une combinaison du nom de domaine complet et de l’adresse IP retournée. Le nom de l’espace réservé _Contoso_ doit être modifié vers le nom de votre locataire spécifique, où _contoso_ est issu de contoso.onmicrosoft.com

#### <a name="example-pac-file"></a>Exemple de fichier PAC

Voici un exemple de génération des fichiers PAC :

1. Enregistrez le script ci-dessous sur votre disque dur local en tant que _Get-TLEPacFile.ps1_.
1. Accédez à [l’URL Verizon](/rest/api/cdn/edge-nodes/list#code-try-0) et téléchargez le fichier JSON résultant (copiez-le dans un fichier comme cdnedgenodes.json)
1. Placez le fichier dans le même dossier que le script.
1. Dans une fenêtre PowerShell, exécutez la commande suivante. Modifiez le nom du locataire pour autre chose si vous souhaitez obtenir les URL SPO. Il s’agit de type 2, donc **Optimize** et **Allow** (type 1 est Optimize uniquement).

   ```powershell
   .\Get-TLEPacFile.ps1 -Instance Worldwide -Type 2 -TenantName <contoso> -CdnEdgeNodesFilePath .\cdnedgenodes.json -FilePath TLE.pac
   ```

5. Le fichier TLE.pac contient tous les espaces de noms et adresses IP (IPv4/IPv6).

##### <a name="get-tlepacfileps1"></a>Get-TLEPacFile.ps1

```powershell
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

<#PSScriptInfo

.VERSION 1.0.4

.AUTHOR Microsoft Corporation

.GUID 7f692977-e76c-4582-97d5-9989850a2529

.COMPANYNAME Microsoft

.COPYRIGHT
Copyright (c) Microsoft Corporation. All rights reserved.
Licensed under the MIT License.

.TAGS PAC Microsoft Microsoft365 365

.LICENSEURI

.PROJECTURI http://aka.ms/ipurlws

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

#>

<#

.SYNOPSIS

Create a PAC file for Microsoft 365 prioritized connectivity

.DESCRIPTION

This script will access updated information to create a PAC file to prioritize Microsoft 365 Urls for
better access to the service. This script will allow you to create different types of files depending
on how traffic needs to be prioritized.

.PARAMETER Instance

The service instance inside Microsoft 365.

.PARAMETER ClientRequestId

The client request id to connect to the web service to query up to date Urls.

.PARAMETER DirectProxySettings

The direct proxy settings for priority traffic.

.PARAMETER DefaultProxySettings

The default proxy settings for non priority traffic.

.PARAMETER Type

The type of prioritization to give. Valid values are 1 and 2, which are 2 different modes of operation.
Type 1 will send Optimize traffic to the direct route. Type 2 will send Optimize and Allow traffic to
the direct route.

.PARAMETER Lowercase

Flag this to include lowercase transformation into the PAC file for the host name matching.

.PARAMETER TenantName

The tenant name to replace wildcard Urls in the webservice.

.PARAMETER ServiceAreas

The service areas to filter endpoints by in the webservice.

.PARAMETER FilePath

The file to print the content to.

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type1.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance China -Type 2 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type2.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance WorldWide -Lowercase -TenantName tenantName -ServiceAreas Sharepoint

#>

#Requires -Version 2

[CmdletBinding(SupportsShouldProcess=$True)]
Param (
    [Parameter(Mandatory = $false)]
    [ValidateSet('Worldwide', 'Germany', 'China', 'USGovDoD', 'USGovGCCHigh')]
    [String] $Instance = "Worldwide",

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [guid] $ClientRequestId = [Guid]::NewGuid().Guid,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DirectProxySettings = 'DIRECT',

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DefaultProxySettings = 'PROXY 10.10.10.10:8080',

    [Parameter(Mandatory = $false)]
    [ValidateRange(1, 2)]
    [int] $Type = 1,

    [Parameter(Mandatory = $false)]
    [switch] $Lowercase = $false,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $TenantName,

    [Parameter(Mandatory = $false)]
    [ValidateSet('Exchange', 'SharePoint', 'Common', 'Skype')]
    [string[]] $ServiceAreas,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $FilePath,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $CdnEdgeNodesFilePath
)

##################################################################################################################
### Global constants
##################################################################################################################

$baseServiceUrl = "https://endpoints.office.com/endpoints/$Instance/?ClientRequestId={$ClientRequestId}"
$directProxyVarName = "direct"
$defaultProxyVarName = "proxyServer"
$bl = "`r`n"

##################################################################################################################
### Functions to create PAC files
##################################################################################################################

function Get-PacClauses
{
    param(
        [Parameter(Mandatory = $false)]
        [string[]] $Urls,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $ReturnVarName
    )

    if (!$Urls)
    {
        return ""
    }

    $clauses =  (($Urls | ForEach-Object { "shExpMatch(host, `"$_`")" }) -Join "$bl        || ")

@"
    if($clauses)
    {
        return $ReturnVarName;
    }
"@
}

function Get-PacString
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [array[]] $MapVarUrls
    )

@"
// This PAC file will provide proxy config to Microsoft 365 services
//  using data from the public web service for all endpoints
function FindProxyForURL(url, host)
{
    var $directProxyVarName = "$DirectProxySettings";
    var $defaultProxyVarName = "$DefaultProxySettings";

$( if ($Lowercase) { "    host = host.toLowerCase();" })

$( ($MapVarUrls | ForEach-Object { Get-PACClauses -ReturnVarName $_.Item1 -Urls $_.Item2 }) -Join "$bl$bl" )

$( if (!$ServiceAreas -or $ServiceAreas.Contains('Skype')) { Get-TLEPacConfiguration })

    return $defaultProxyVarName;
}
"@ -replace "($bl){3,}","$bl$bl" # Collapse more than one blank line in the PAC file so it looks better.
}

##################################################################################################################
### Functions to get and filter endpoints
##################################################################################################################

function Get-TLEPacConfiguration {
    param ()
    $PreBlock = @"
    // Don't Proxy Teams Live Events traffic

    if(shExpMatch(host, "*.azureedge.net")
    || shExpMatch(host, "*.bmc.cdn.office.net")
    || shExpMatch(host, "*.media.azure.net"))
    {
        var resolved_ip = dnsResolveEx(host);

"@
    $TLESb = New-Object 'System.Text.StringBuilder'
    $TLESb.Append($PreBlock) | Out-Null

    if (![string]::IsNullOrEmpty($CdnEdgeNodesFilePath) -and (Test-Path -Path $CdnEdgeNodesFilePath)) {
        $CdnData = Get-Content -Path $CdnEdgeNodesFilePath -Raw -ErrorAction SilentlyContinue | ConvertFrom-Json | Select-Object -ExpandProperty value | 
            Where-Object { $_.name -eq 'Premium_Verizon'} | Select-Object -First 1 -ExpandProperty properties | 
            Select-Object -ExpandProperty ipAddressGroups
        $CdnData | Select-Object -ExpandProperty ipv4Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
        $CdnData | Select-Object -ExpandProperty ipv6Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
    }
    $AzureIPsUrl = Invoke-WebRequest -Uri "https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519" -UseBasicParsing -ErrorAction SilentlyContinue  | 
            Select-Object -ExpandProperty Links | Select-Object -ExpandProperty href | 
            Where-Object { $_.EndsWith('.json') -and $_ -match 'ServiceTags' } | Select-Object -First 1
    if ($AzureIPsUrl) {
        Invoke-RestMethod -Uri $AzureIPsUrl -ErrorAction SilentlyContinue | Select-Object -ExpandProperty values | 
            Where-Object { $_.name -eq 'AzureFrontDoor.Frontend' } | Select-Object -First 1 -ExpandProperty properties |
            Select-Object -ExpandProperty addressPrefixes | ForEach-Object {
                if ($TLESb.Length -eq $PreBlock.Length) {
                    $TLESb.Append("        if(") | Out-Null
                }
                else {
                    $TLESb.AppendLine() | Out-Null
                    $TLESb.Append("        || ") | Out-Null
                }
                $TLESb.Append("isInNetEx(resolved_ip, `"$_`")") | Out-Null
            }
    }
    if ($TLESb.Length -gt $PreBlock.Length) {
        $TLESb.AppendLine(")") | Out-Null
        $TLESb.AppendLine("        {") | Out-Null
        $TLESb.AppendLine("            return $directProxyVarName;") | Out-Null
        $TLESb.AppendLine("        }") | Out-Null
    }
    else {
        $TLESb.AppendLine("        // no addresses found for service via script") | Out-Null
    }
    $TLESb.AppendLine("    }") | Out-Null
    return $TLESb.ToString()
}

function Get-Regex
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $Fqdn
    )

    return "^" + $Fqdn.Replace(".", "\.").Replace("*", ".*").Replace("?", ".?") + "$"
}

function Match-RegexList
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $ToMatch,

        [Parameter(Mandatory = $false)]
        [string[]] $MatchList
    )

    if (!$MatchList)
    {
        return $false
    }
    foreach ($regex in $MatchList)
    {
        if ($regex -ne $ToMatch -and $ToMatch -match (Get-Regex $regex))
        {
            return $true
        }
    }
    return $false
}

function Get-Endpoints
{
    $url = $baseServiceUrl
    if ($TenantName)
    {
        $url += "&TenantName=$TenantName"
    }
    if ($ServiceAreas)
    {
        $url += "&ServiceAreas=" + ($ServiceAreas -Join ",")
    }
    return Invoke-RestMethod -Uri $url
}

function Get-Urls
{
    param(
        [Parameter(Mandatory = $false)]
        [psobject[]] $Endpoints
    )

    if ($Endpoints)
    {
        return $Endpoints | Where-Object { $_.urls } | ForEach-Object { $_.urls } | Sort-Object -Unique
    }
    return @()
}

function Get-UrlVarTuple
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $VarName,

        [Parameter(Mandatory = $false)]
        [string[]] $Urls
    )
    return New-Object 'Tuple[string,string[]]'($VarName, $Urls)
}

function Get-MapVarUrls
{
    Write-Verbose "Retrieving all endpoints for instance $Instance from web service."
    $Endpoints = Get-Endpoints

    if ($Type -eq 1)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -eq "Optimize" })
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -ne "Optimize" }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
    elseif ($Type -eq 2)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -in @("Optimize", "Allow")})
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -notin @("Optimize", "Allow") }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
}

##################################################################################################################
### Main script
##################################################################################################################

$content = Get-PacString (Get-MapVarUrls)

if ($FilePath)
{
    $content | Out-File -FilePath $FilePath -Encoding ascii
}
else
{
    $content
}
```

Le script analyse automatiquement la liste Azure en fonction de [l’URL de téléchargement](https://www.microsoft.com/download/details.aspx?id=56519) et des clés **d’AzureFrontDoor.Frontend**. Il n’est donc pas nécessaire de l’obtenir manuellement.

Là encore, il n’est pas recommandé d’effectuer un déchargement VPN à l’aide uniquement des noms de domaine complets ; **L’utilisation** des noms de domaine complets et des adresses IP dans la fonction permet d’étendre l’utilisation de ce déchargement à un ensemble limité de points de terminaison, y compris les événements en direct/flux. La façon dont la fonction est structurée entraîne une recherche DNS pour le nom de domaine complet qui correspond directement à celles répertoriées par le client, c’est-à-dire que la résolution DNS des espaces de noms restants reste inchangée.

Si vous souhaitez limiter le risque de déchargement de points de terminaison non liés aux événements en direct et à Stream, vous pouvez supprimer le **\*domaine .azureedge.net** de la configuration, où réside la plupart de ce risque, car il s’agit d’un domaine partagé utilisé pour tous les clients Azure CDN. L’inconvénient est que tout événement utilisant un encodeur externe ne sera pas optimisé, mais les événements générés/organisés dans Teams le seront.

## <a name="3-configure-routing-on-the-vpn-to-enable-direct-egress"></a>3. Configurer le routage sur le VPN pour activer la sortie directe

La dernière étape consiste à ajouter un itinéraire direct pour les adresses IP d’événement en direct décrites dans **La collecte des listes actuelles de points de terminaison CDN** dans la configuration VPN pour vous assurer que le trafic n’est pas envoyé via le tunnel forcé dans le VPN. Vous trouverez des informations détaillées sur la façon de procéder pour les points de terminaison Microsoft 365 Optimize dans la section [Implémenter le tunneling fractionné VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) de [l’implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md). Le processus est exactement le même pour les adresses IP Stream/Live Events répertoriées dans ce document.

Notez que seules les adresses IP (et non les noms de domaine complets) de [la collecte des listes actuelles de points de terminaison CDN doivent être utilisées](#gathering-the-current-lists-of-cdn-endpoints) pour la configuration VPN.

## <a name="faq"></a>Questions fréquentes (FAQ)

### <a name="will-this-send-all-my-traffic-to-the-service-direct"></a>Est-ce que cela enverra tout mon trafic vers le service directement ?

Non, cela envoie le trafic de streaming sensible à la latence pour un événement en direct ou un flux vidéo direct. Tout autre trafic continuera à utiliser le tunnel VPN s’ils ne sont pas résolus en adresses IP publiées.

### <a name="do-i-need-to-use-the-ipv6-addresses"></a>Dois-je utiliser les adresses IPv6 ?

Non, la connectivité ne peut être IPv4 que si nécessaire.

### <a name="why-are-these-ips-not-published-in-the-microsoft-365-urlip-service"></a>Pourquoi ces adresses IP ne sont-elles pas publiées dans le service URL/IP Microsoft 365 ?

Microsoft dispose de contrôles stricts sur le format et le type d’informations qui se trouvent dans le service pour s’assurer que les clients peuvent utiliser les informations de manière fiable pour implémenter un routage sécurisé et optimal en fonction de la catégorie de point de terminaison.

La catégorie de point de terminaison **par défaut** ne contient aucune information IP fournie pour de nombreuses raisons (les points de terminaison par défaut peuvent être hors du contrôle de Microsoft, changer trop fréquemment ou se trouver dans des blocs partagés avec d’autres éléments). Pour cette raison, les points de terminaison par défaut sont conçus pour être envoyés via un nom de domaine complet à un proxy d’inspection, comme le trafic web normal.

Dans ce cas, les points de terminaison ci-dessus sont des CDN qui peuvent être utilisés par des éléments non contrôlés par Microsoft autres que des événements en direct ou stream. Par conséquent, l’envoi direct du trafic signifie également tout autre chose qui résout ces adresses IP sera également envoyé directement à partir du client. En raison de la nature unique de la crise mondiale actuelle et pour répondre aux besoins à court terme de nos clients, Microsoft a fourni les informations ci-dessus pour les clients à utiliser comme ils le souhaitent.

Microsoft s’efforce de reconfigurer les points de terminaison d’événements en direct pour qu’ils puissent être inclus dans les catégories Autoriser/Optimiser les points de terminaison à l’avenir.

### <a name="do-i-only-need-to-allow-access-to-these-ips"></a>Dois-je uniquement autoriser l’accès à ces adresses IP ?

Non, l’accès à tous les points de terminaison marqués **requis** dans [le service URL/IP](urls-and-ip-address-ranges.md) est essentiel pour que le service fonctionne. En outre, tout point de terminaison facultatif marqué pour Stream (ID 41-45) est requis.

### <a name="what-scenarios-will-this-advice-cover"></a>Quels scénarios ce conseil couvre-t-il ?

1. Événements en direct produits dans l’application Teams
2. Affichage du contenu hébergé par Stream
3. Événements générés par un appareil externe (encodeur)

### <a name="does-this-advice-cover-presenter-traffic"></a>Ces conseils couvrent-ils le trafic des présentateurs ?

Ce n’est pas le cas, les conseils ci-dessus ne s’appliquent qu’à ceux qui consomment le service. La présentation à partir de Teams verra le trafic du présentateur transitant vers les points de terminaison UDP marqués d’optimisation répertoriés dans la ligne 11 du service URL/IP, avec des conseils détaillés sur le déchargement VPN décrits dans la section [Implémenter le tunneling fractionné VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) de [l’implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

### <a name="does-this-configuration-risk-traffic-other-than-live-events-amp-stream-being-sent-direct"></a>Ce trafic de configuration présente-t-il des risques autres que le flux d’événements &amp; en direct envoyé directement ?

Oui, en raison des noms de domaine complets partagés utilisés pour certains éléments du service, cela est inévitable. Ce trafic est normalement envoyé via un proxy d’entreprise qui peut appliquer l’inspection. Dans un scénario de tunnel fractionné VPN, l’utilisation des noms de domaine complets et des adresses IP limitera ce risque au minimum, mais il existera toujours. Les clients peuvent supprimer le **\*domaine .azureedge.net** de la configuration de déchargement et réduire ce risque au strict minimum, mais cela supprimera le déchargement des événements en direct pris en charge par Stream (événements d’encodeur externes planifiés par Teams, événements Yammer produits dans Teams, événements d’encodeur externe planifiés par Yammer et événements planifiés par Stream ou affichage à la demande à partir de Stream). Les événements planifiés et produits dans Teams ne sont pas affectés.

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Scénarios courants de tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md)

[Optimisation des performances de Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Optimisation des performances et du réseau Microsoft 365](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
