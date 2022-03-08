---
title: Considérations spéciales pour les flux et les événements en direct dans les environnements VPN
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Considérations spéciales pour les flux et les événements en direct dans les environnements VPN
ms.openlocfilehash: eb2e57b844f06bc3b1e005aa1095794b176bba94
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63331194"
---
# <a name="special-considerations-for-stream-and-live-events-in-vpn-environments"></a>Considérations spéciales pour les flux et les événements en direct dans les environnements VPN

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent Microsoft 365'optimisation des utilisateurs distants.

>- Pour une vue d’ensemble de l’utilisation de la tunneling fractionnement VPN pour optimiser la connectivité Microsoft 365 pour les utilisateurs distants, voir Vue d’ensemble : [tunneling fractionnel VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Pour obtenir des instructions détaillées sur l’implémentation de la tunneling fractionnement VPN, voir [Implementing VPN split tunneling for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Pour obtenir la liste détaillée des scénarios de tunneling fractionnement VPN, voir [Scénarios courants de tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Pour obtenir des instructions sur la sécurisation Teams trafic multimédia dans les environnements de tunnel partagé VPN, voir Sécurisation du trafic Teams multimédia [pour la tunnelisation fractionnée VPN](microsoft-365-vpn-securing-teams.md).
>- Pour plus d’informations sur l’optimisation Microsoft 365 performances des clients internationaux pour les utilisateurs en Chine, voir Microsoft 365 [optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md).

le trafic des événements en direct Microsoft 365 (cela inclut les participants aux événements en direct produits par Teams et ceux produits avec un encodeur externe via Teams, Stream ou Yammer) et le trafic de flux à la demande est actuellement classé comme trafic par défaut ou Optimiser dans la  liste [URL/IP du service](urls-and-ip-address-ranges.md). Ces points de terminaison sont classés  par défaut, car ils sont hébergés sur des CDN qui peuvent également être utilisés par d’autres services. Les clients préfèrent généralement proxyer ce type de trafic et appliquer tous les éléments de sécurité normalement effectués sur des points de terminaison tels que ceux-ci.

De nombreux clients ont demandé des données URL/IP nécessaires pour connecter leurs utilisateurs aux événements Stream/Live directement à partir de leur connexion Internet locale, plutôt que d’router le trafic à volume élevé et sensible à la latence via l’infrastructure VPN. En règle générale, cela n’est pas possible sans des espaces de noms dédiés et des informations IP précises pour les points de terminaison, qui ne sont pas fournis pour les points de terminaison Microsoft 365 classés par **défaut.**

Utilisez les étapes suivantes pour activer la connectivité directe pour le service Stream/Live Events à partir des clients à l’aide d’un VPN de tunnel forcé. Cette solution est destinée à offrir aux clients une option pour éviter le routage du trafic d’événements en direct sur VPN alors qu’il y a un trafic réseau élevé en raison de scénarios de travail à domicile. Si possible, il est conseillé d’accéder au service via un proxy d’inspection.

>[!NOTE]
>À l’aide de cette solution, il peut y avoir des éléments de service qui ne sont pas résolus en adresses IP fournies et par conséquent traversent le VPN, mais l’essentiel du trafic à volume élevé comme les données de diffusion en continu doit le faire. Il peut y avoir d’autres éléments en dehors de l’étendue des événements en direct/flux qui sont capturés par ce déchargement, mais ceux-ci doivent  être limités car ils doivent répondre à la fois au nom de domaine complet et à la correspondance IP avant de passer directement.

>[!IMPORTANT]
>Les clients sont invités à évaluer le risque d’envoyer davantage de trafic qui contourne le VPN par rapport au gain de performances pour les événements en direct.

Pour implémenter l’exception de tunnel forcé Teams Live Events et Stream, les étapes suivantes doivent être appliquées :

## <a name="1-configure-external-dns-resolution"></a>1. Configurer la résolution DNS externe

Les clients ont besoin d’une résolution DNS externe récursive pour être disponibles afin que les noms d’hôte suivants soient résolus en adresses IP.

- \*.azureedge.net
- \*.media.azure.net
- \*.bmc.cdn.office.net

**\*.azureedge.net** est utilisé pour les événements Stream (Configurer des encodeurs pour la diffusion en continu en direct dans [Microsoft Stream - Microsoft Stream | Microsoft Docs](/stream/live-encoder-setup)).

**\*.media.azure.net** **\*et .bmc.cdn.office.net** sont utilisés pour les événements en direct produits par Teams (événements de démarrage rapide, événements pris en charge par RTMP-In [ID de feuille de route 84960]) programmés à partir du client Teams.

 Certains de ces points de terminaison sont partagés avec d’autres éléments en dehors des événements Stream/Live, il n’est pas conseillé d’utiliser simplement ces FQDN pour configurer le déchargement VPN, même si techniquement possible dans votre solution VPN (par exemple, si elle fonctionne sur le nom deqdn plutôt que sur IP).

Les FQDN ne sont pas requis dans la configuration VPN, ils sont purement à utiliser dans les fichiers PAC en combinaison avec les adresses IP pour envoyer le trafic direct approprié.

## <a name="2-implement-pac-file-changes-where-required"></a>2. Implémenter les modifications de fichier PAC (le cas échéant)

Pour les organisations qui utilisent un fichier PAC pour router le trafic via un proxy sur VPN, cette action est normalement obtenue à l’aide de FQDN. Toutefois, avec les événements Stream/Live, les noms d’hôte fournis contiennent des caractères génériques **\*tels que .azureedge.net**, qui englobent également d’autres éléments pour lesquels il n’est pas possible de fournir des listes IP complètes. Par conséquent, si la demande est envoyée directement en fonction de la correspondance de caractère générique DNS seule, le trafic vers ces points de terminaison sera bloqué, car il n’existe aucun itinéraire via le chemin d’accès direct pour celui-ci à l’étape [3](#3-configure-routing-on-the-vpn-to-enable-direct-egress) plus loin dans cet article.

Pour résoudre ce problème, nous pouvons fournir les IP suivantes et les utiliser en combinaison avec les noms d’hôtes dans un exemple de fichier PAC, comme décrit à [l’étape 1](#1-configure-external-dns-resolution). Le fichier PAC vérifie si l’URL correspond à celles utilisées pour les événements Stream/Live, puis, si c’est le cas, il vérifie également si l’ADRESSE IP renvoyée par une recherche DNS correspond à celles fournies pour le service. Si _les deux_ correspondent, le trafic est acheminé directement. Si l’un des deux éléments (FQDN/IP) ne correspond pas, le trafic est envoyé au proxy. Par conséquent, la configuration garantit que tout ce qui est résolu en adresse IP en dehors de l’étendue des espaces de noms IP et définis traverse normalement le proxy via le VPN.

### <a name="gathering-the-current-lists-of-cdn-endpoints"></a>Collecte des listes actuelles de points CDN de terminaison

Les événements en direct utilisent plusieurs fournisseurs CDN pour diffuser des données aux clients, afin de fournir la meilleure couverture, la meilleure qualité et la meilleure résilience. Actuellement, les Azure CDN microsoft et Verizon sont utilisés. Au fil du temps, cela peut être modifié en raison de situations telles que la disponibilité régionale. Cet article est une source qui vous permet de rester à jour sur les plages IP.

Pour Azure CDN à partir de Microsoft, vous pouvez télécharger la liste à partir de Télécharger les [plages IP azure et les balises de service – Cloud public](https://www.microsoft.com/download/details.aspx?id=56519) à partir du Centre de téléchargement Microsoft officiel - vous devez rechercher spécifiquement la balise de service *AzureFrontdoor.Frontend* dans le JSON ; *addressPrefixes* affiche les sous-réseaux IPv4/IPv6. Au fil du temps, les IP peuvent changer, mais la liste des balises de service est toujours mise à jour avant leur utilisation.

For Azure CDN from Verizon (Edgecast) you can find an exhaustive list using [https://docs.microsoft.com/rest/api/cdn/edge-nodes/list](/rest/api/cdn/edge-nodes/list) (click **Try It** ) - you will need to look specifically for the **Premium\_ Verizon** section. Notez que cette API affiche toutes les IP edgecast (origine et anycast). Il n’existe actuellement aucun mécanisme permettant à l’API de faire la distinction entre l’origine et Anycast.

Pour l’implémenter dans un fichier PAC, vous pouvez utiliser l’exemple suivant qui envoie le trafic Microsoft 365 Optimiser le trafic direct (ce qui est recommandé) via le FQDN et le trafic stream/live events direct critique via une combinaison du FQDN et de l’adresse IP renvoyée. Le nom de l’espace réservé _Contoso_ doit être modifié pour le nom de votre client spécifique où _contoso_ est issu de contoso.onmicrosoft.com

#### <a name="example-pac-file"></a>Exemple de fichier PAC

Voici un exemple de la façon de générer les fichiers PAC :

1. Enregistrez le script ci-dessous sur votre disque dur local _sousGet-TLEPacFile.ps1_.
1. Go to the [Verizon URL](/rest/api/cdn/edge-nodes/list#code-try-0) and download the resulting JSON (copy paste it into a file like cdnedgenodes.json)
1. Placez le fichier dans le même dossier que le script.
1. Dans une fenêtre PowerShell, exécutez la commande suivante. Modifiez le nom du client pour autre chose si vous souhaitez les URL SPO. Il s’agit du type 2, donc **Optimiser** et **autoriser** (le type 1 est Optimiser uniquement).

   ```powershell
   .\Get-TLEPacFile.ps1 -Instance Worldwide -Type 2 -TenantName <contoso> -CdnEdgeNodesFilePath .\cdnedgenodes.json -FilePath TLE.pac
   ```

5. Le fichier TLE.pac contient tous les espaces de noms et les IPS (IPv4/IPv6).

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

Le script va automatiquement passer la liste Azure en fonction de [l’URL](https://www.microsoft.com/download/details.aspx?id=56519) de téléchargement et des clés **d’AzureFrontDoor.Frontend**, il n’est donc pas nécessaire de l’obtenir manuellement.

Là encore, il n’est pas conseillé d’effectuer un déchargement VPN à l’aide uniquement des FQDN . l’utilisation des noms de domaine complets et des adresses IP dans la fonction permet d’limiter l’utilisation de ce déchargement à un ensemble limité de points de terminaison, y compris les événements en direct/flux. La façon dont la fonction est structurée entraîne la recherche DNS pour le nom de domaine complet qui correspond directement à ceux répertoriés par le client, c’est-à-dire que la résolution DNS des espaces de noms restants reste inchangée.

Si vous souhaitez limiter le risque de déchargement des points de terminaison non liés aux événements en direct et au flux, **\*** vous pouvez supprimer le domaine .azureedge.net de la configuration, qui est l’endroit où réside la plupart de ce risque, car il s’agit d’un domaine partagé utilisé pour tous les clients Azure CDN. L’inconvénient est que tout événement utilisant un encodeur externe n’est pas optimisé, mais que les événements produits/organisés au sein Teams seront.

## <a name="3-configure-routing-on-the-vpn-to-enable-direct-egress"></a>3. Configurer le routage sur le VPN pour activer la sortie directe

La dernière étape consiste à ajouter un itinéraire direct pour les IP d’événements en direct décrits dans la collecte des **listes** actuelles de points de terminaison CDN dans la configuration VPN pour vous assurer que le trafic n’est pas envoyé via le tunnel forcé dans le VPN. Des informations détaillées sur la façon de le faire pour Microsoft 365 Optimiser les points de terminaison sont disponibles dans la section Implémenter la [tunneling](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) fractionnement VPN de l’implémentation de [la tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md). Le processus est exactement le même pour les IPS Stream/Live Events répertoriés dans ce document.

Notez que [seules](#gathering-the-current-lists-of-cdn-endpoints) les IP (et non les FQDN) de collecte des listes actuelles de points de terminaison CDN doivent être utilisées pour la configuration VPN.

## <a name="faq"></a>FAQ

### <a name="will-this-send-all-my-traffic-to-the-service-direct"></a>Cela enverra-t-il tout mon trafic au service direct ?

Non, cela envoie directement le trafic de diffusion en continu sensible à la latence pour un événement en direct ou une vidéo de flux, tout autre trafic continuera à utiliser le tunnel VPN s’il n’est pas résolu en adresses IP publiées.

### <a name="do-i-need-to-use-the-ipv6-addresses"></a>Dois-je utiliser les adresses IPv6 ?

Non, la connectivité ne peut être IPv4 que si nécessaire.

### <a name="why-are-these-ips-not-published-in-the-microsoft-365-urlip-service"></a>Pourquoi ces adresses IP ne sont-elles pas publiées dans le service MICROSOFT 365 URL/IP ?

Microsoft dispose de contrôles stricts sur le format et le type d’informations qui se trouve dans le service pour s’assurer que les clients peuvent utiliser de manière fiable les informations pour implémenter un routage sécurisé et optimal en fonction de la catégorie de point de terminaison.

La  catégorie de point de terminaison par défaut ne dispose d’aucune information IP fournie pour de nombreuses raisons (les points de terminaison par défaut peuvent être en dehors du contrôle de Microsoft, peuvent changer trop fréquemment ou se retrouver dans des blocs partagés avec d’autres éléments). Pour cette raison, les points de terminaison par défaut sont conçus pour être envoyés via le FQDN à un proxy d’inspection, comme le trafic web normal.

Dans ce cas, les points de terminaison ci-dessus sont des CDN qui peuvent être utilisés par des éléments non Contrôlés par Microsoft autres que Des événements en direct ou Stream. Ainsi, l’envoi du trafic direct signifie également toute autre chose qui résout ces IP sera également envoyée directement à partir du client. En raison de la nature unique de la crise globale actuelle et pour répondre aux besoins à court terme de nos clients, Microsoft a fourni les informations ci-dessus que les clients peuvent utiliser comme bon leur semble.

Microsoft travaille à reconfigurer les points de terminaison Des événements en direct pour leur permettre d’être inclus dans les catégories de points de terminaison Autoriser/Optimiser à l’avenir.

### <a name="do-i-only-need-to-allow-access-to-these-ips"></a>Dois-je uniquement autoriser l’accès à ces IP ?

Non, l’accès à tous  les points de terminaison marqués obligatoires dans le [service URL/IP](urls-and-ip-address-ranges.md) est essentiel au fonctionnement du service. En outre, tout point de terminaison facultatif marqué pour Stream (ID 41-45) est requis.

### <a name="what-scenarios-will-this-advice-cover"></a>Quels scénarios seront couverts par ce conseil ?

1. Événements en direct produits dans l’application Teams
2. Affichage du contenu hébergé par Stream
3. Événements produits par l’appareil externe (encodeur)

### <a name="does-this-advice-cover-presenter-traffic"></a>Ce conseil couvre-t-il le trafic du présentateur ?

Ce n’est pas le cas, les conseils ci-dessus sont purement pour les personnes qui consomment le service. Lors d’une présentation à partir de Teams le trafic du présentateur s’affichera vers les points de terminaison UDP marqués Optimiser répertoriés à la ligne 11 de l’URL/service IP avec des conseils détaillés de déchargement VPN décrits dans la section Implémenter le [tunneling](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) fractionné VPN de l’implémentation de [la tunneling](microsoft-365-vpn-implement-split-tunnel.md) fractionné VPN pour Microsoft 365.

### <a name="does-this-configuration-risk-traffic-other-than-live-events-amp-stream-being-sent-direct"></a>Cette configuration risque-t-elle que le trafic autre que le flux d’événements &amp; en direct soit envoyé directement ?

Oui, en raison des FQDN partagés utilisés pour certains éléments du service, cela est inévitable. Ce trafic est normalement envoyé via un proxy d’entreprise qui peut appliquer l’inspection. Dans un scénario de tunnel partagé VPN, l’utilisation de FQDN et d’IPs limite ce risque au minimum, mais il existera toujours. Les clients peuvent supprimer le domaine .azureedge.net de la configuration de déchargement et réduire ce risque à un minimum, mais cela supprime le déchargement des événements en direct pris en charge par Stream (événements d’encodeur externes Teams programmés, événements Yammer produits dans Teams, événements d’encodeur externes Yammer programmés et événements stream programmés ou affichage à la demande à partir de Stream).**\*** Les événements programmés et produits dans Teams ne sont pas affectés.

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble : tunnel vpn partagé pour Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implémentation de la tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Scénarios courants de tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md)

[Microsoft 365 optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 réseau et l’optimisation des performances](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
