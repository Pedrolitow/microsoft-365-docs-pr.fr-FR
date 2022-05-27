---
title: Gestion des points de terminaison Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/18/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Découvrez comment gérer Office 365 points de terminaison afin qu’ils fonctionnent avec l’architecture réseau de votre organisation d’entreprise.
ms.openlocfilehash: c32b44365a8c926e398e4441b6b50905ea77147d
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753823"
---
# <a name="managing-office-365-endpoints"></a>Gestion des points de terminaison Office 365

La plupart des organisations d’entreprise disposant de plusieurs emplacements de bureau et d’une connexion WAN de connexion auront besoin de la configuration de la connectivité réseau d’Office 365. Vous pouvez optimiser votre réseau en envoyant toutes les demandes réseau Office 365 approuvées directement via votre pare-feu, en contournant toute inspection ou traitement supplémentaire au niveau des paquets. Cela réduit ainsi la latence et les exigences relatives à la capacité du périmètre. L’identification du trafic réseau Office 365 est la première étape pour offrir des performances optimales pour vos utilisateurs. Pour plus d’informations, consultez [Office 365 Principes de connectivité réseau](microsoft-365-network-connectivity-principles.md).

Microsoft vous recommande d’accéder aux points de terminaison réseau Office 365 et de les modifier en continu à l’aide du [service web d’adresse IP et d’URL Office 365](microsoft-365-ip-web-service.md).

Quelle que soit la façon dont vous gérez le trafic réseau Office 365 vital, Office 365 nécessite une connectivité Internet. D’autres points de terminaison réseau pour lesquels une connectivité est requise sont répertoriés sur [Autres points de terminaison non inclus dans l’adresse IP d’Office 365 et le service Web d’URL](additional-office365-ip-addresses-and-urls.md).

La manière dont vous utilisez les points de terminaison réseau Office 365 dépendra de l’architecture réseau de votre entreprise. Cet article présente plusieurs façons d’intégrer les architectures réseau d’entreprise aux adresses IP et URL Office 365. Le moyen le plus simple de choisir les demandes réseau à approuver consiste à utiliser des appareils SD-WAN qui prennent en charge la configuration automatisée Office 365 à chaque emplacement de votre bureau.

## <a name="sd-wan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SD-WAN pour la sortie de branche locale du trafic réseau vital Office 365

À chaque emplacement de succursale, vous pouvez fournir un appareil SD-WAN configuré pour acheminer le trafic pour Office 365 catégorie Optimiser des points de terminaison, ou optimiser et autoriser les catégories, directement vers le réseau de Microsoft. Les autres types de trafic réseau, notamment le trafic de centre de données local, le trafic de sites Web Internet généraux et le trafic vers les points de terminaison de catégorie par défaut d’Office 365 sont envoyés à un autre emplacement dans lequel vous avez un périmètre de réseau plus important.

Microsoft travaille avec les fournisseurs SD-WAN pour activer la configuration automatisée. Pour plus d’informations, voir [Programme de partenariat réseau Office 365](microsoft-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Utiliser un fichier PAC pour le routage direct du trafic Office 365 vital

Utilisez les fichiers PAC ou WPAD pour gérer les requêtes réseau associées à Office 365, mais qui n’ont aucune adresse IP. Les requêtes réseau classiques envoyées via un proxy ou un périphérique de périmètre augmentent la latence. Si l’arrêt et l’inspection de SSL créent la latence la plus élevée, d’autres services tels que l’authentification proxy et la recherche de réputation peuvent entraîner des performances médiocres et une expérience utilisateur incorrecte. De plus, ces périphériques réseau de périmètre ont besoin de suffisamment de ressources pour traiter toutes les requêtes de connexion réseau. Nous vous recommandons de contourner votre infrastructure de proxy ou d’inspection pour les requêtes réseau Office 365 directes.
  
[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) est un script PowerShell qui lit les derniers points de terminaison réseau à partir de l’adresse IP et du service Web d’URL Office 365 et crée un exemple de fichier PAC. Vous pouvez modifier le script de sorte qu’il s’intègre à votre gestion de fichiers PAC existante.

> [!NOTE]
> Pour plus d’informations sur les considérations relatives à la sécurité et aux performances de la connectivité directe aux points de terminaison Office 365, consultez [Office 365 principes de connectivité réseau](microsoft-365-network-connectivity-principles.md).

![Connexion à Office 365 via des pare-feu et des proxys.](../media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Figure 1 : périmètre de réseau d’entreprise simple**

Le fichier PAC est déployé sur les navigateurs Web au point 1 de la figure 1. Lors de l’utilisation d’un fichier PAC pour la sortie directe du trafic réseau Office 365 vital, vous devez également autoriser la connectivité aux adresses IP situées derrière ces URL sur votre pare-feu de périmètre réseau. Pour ce faire, il suffit de récupérer les adresses IP des mêmes catégories de points de terminaison Office 365, comme spécifié dans le fichier PAC et de créer des listes de contrôle d’accès de pare-feu sur la base de ces adresses. Le pare-feu est le point 3 de la figure 1.

Séparément, si vous choisissez d’effectuer uniquement le routage direct pour les points de terminaison de la catégorie Optimiser, les points de terminaison de la catégorie Autoriser que vous envoyez au serveur proxy devront être répertoriés sur le serveur proxy afin de contourner le traitement. Par exemple, les points de terminaison Optimiser et Authentification de proxy sont incompatibles avec les points de terminaison Optimiser et Autoriser. Le serveur proxy est le point 2 de la figure 1.

La configuration courante consiste à autoriser sans traiter tout le trafic sortant du serveur proxy pour les adresses IP de destination du trafic réseau Office 365 qui atteint le serveur proxy. Pour plus d’informations sur les problèmes liés à l’utilisation de SSL Break et Inspect, voir [Utilisation d’appareils ou de solutions de réseau tiers sur le trafic Office 365](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Le script Get-PacFile génère deux types de fichiers PAC.

| Type | Description |
|:-----|:-----|
|**1** <br/> |Envoyez au serveur proxy Optimiser le trafic de point de terminaison direct et tout le reste. <br/> |
|**2** <br/> |Envoyez au serveur proxy Optimiser et Autoriser le trafic de point de terminaison direct et tout le reste. Ce type peut également être utilisé pour envoyer toutes les ExpressRoute prises en charge pour le trafic Office 365 vers ExpressRoute segments réseau et tout le reste vers le serveur proxy. <br/> |

Voici un exemple simple d’appel du script PowerShell :

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Il existe de nombreux paramètres que vous pouvez passer au script :

| Paramètre | Description |
|:-----|:-----|
|**ClientRequestId** <br/> |Ceci est requis et il s’agit d’un GUID transmis au service Web qui représente l’ordinateur client à l’origine de l’appel. <br/> |
|**Instance** <br/> |Instance de service Office 365, qui est par défaut Worldwide. Il est également transmis au service web. <br/> |
|**TenantName** <br/> |Votre nom de client Office 365. Transmises au service Web et utilisées comme paramètre remplaçable dans certaines URL d’Office 365. <br/> |
|**Type** <br/> |Type du fichier PAC de proxy que vous voulez générer. <br/> |

Voici un autre exemple d’appel du script PowerShell avec d’autres paramètres :

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Contournement de serveur proxy avec traitement du trafic réseau Office 365

Lorsque les fichiers PAC ne sont pas utilisés pour le trafic sortant direct, vous souhaitez toujours contourner le traitement sur votre périmètre réseau en configurant votre serveur proxy. Certains fournisseurs de serveur proxy ont activé la configuration automatisée, ce qui est décrit dans le [Programme de partenariat réseau Office 365](microsoft-365-networking-partner-program.md).

Si vous effectuez cette opération manuellement, vous devez obtenir les données de catégorie Optimiser et Autoriser le point de terminaison à partir du service web d’adresse IP et d’URL Office 365 et configurer votre serveur proxy pour contourner le traitement de ces derniers. Il est important d’éviter l’arrêt et l’inspection de SSL et l’authentification proxy pour les points de terminaison Optimiser et Autoriser.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Gestion des modifications pour Office 365 adresses IP et URL

En plus de sélectionner la configuration appropriée pour votre périmètre réseau, il est essentiel d’adopter un processus de gestion des modifications pour Office 365 points de terminaison. Ces points de terminaison changent régulièrement et si vous ne gérez pas les modifications, vous pouvez vous retrouver avec des utilisateurs bloqués ou avec des performances médiocres après l’ajout d’une nouvelle adresse IP ou d’une nouvelle URL.

Les modifications apportées aux adresses IP et URL Office 365 sont généralement publiées autour du dernier jour de chaque mois. Il peut arriver qu’une modification soit publiée en dehors de cette planification en raison de besoins opérationnels, de support ou de sécurité.

Lorsqu’une modification est publiée et que vous devez agir parce qu’une adresse IP ou une URL a été ajoutée, vous devez vous attendre à recevoir un préavis de 30 jours à partir du moment où nous publions la modification jusqu’à ce qu’il y ait un service Office 365 sur ce point de terminaison. Cela se reflète sous la forme de la date d’effet. Bien que nous cherchions à utiliser cette période de notification, il est possible qu’elle ne soit pas toujours possible en raison de besoins opérationnels, de support ou de sécurité. Les modifications qui ne nécessitent pas d’action immédiate pour maintenir la connectivité, telles que la suppression d’adresses IP ou d’URL ou de modifications moins importantes, n’incluent pas de notification préalable. Dans ces cas, aucune date d’effet n’est fournie. Quelle que soit la notification fournie, nous annonçons la date de mise en service attendue pour chaque changement.

### <a name="change-notification-using-the-web-service"></a>Notification des modifications à l’aide du service Web

Vous pouvez utiliser l’adresse IP Office 365 et le service Web d’URL pour obtenir la notification de modification. Nous vous recommandons d’appeler la méthode web **/version** une fois par heure pour vérifier la version des points de terminaison que vous utilisez pour vous connecter à Office 365. Si cette version change alors qu’elle est comparée à la version que vous utilisez, vous devriez obtenir les données de point de terminaison les plus récentes à partir de la méthode Web **/Endpoints** et éventuellement obtenir les différences par rapport à la méthode Web **/changes**. Il n’est pas nécessaire d’appeler les **méthodes web /endpoints** ou **/changes** si aucune modification n’a été apportée à la version que vous avez trouvée.

Pour plus d’informations, voir [Service web d’URL et d’adresses IP Office 365](microsoft-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Notification des modifications à l’aide de flux RSS

L’adresse IP et le service Web d’URL Office 365 fournissent un flux RSS auquel vous pouvez vous abonner dans Outlook. Il existe des liens vers les URL RSS sur chacune des pages spécifiques aux instances de service Office 365 pour les adresses IP et URL. Pour plus d’informations, voir [Service web d’URL et d’adresses IP Office 365](microsoft-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-power-automate"></a>Notification des changements et examen de l'approbation à l'aide de Power Automate

Nous savons qu’il est possible que vous deviez continuer à traiter manuellement les modifications apportées aux points de terminaison réseau par mois. Vous pouvez utiliser Power Automate pour créer un flux qui vous avertit par e-mail et exécute éventuellement un processus d’approbation pour les modifications lorsque Office 365 points de terminaison réseau ont des modifications. Une fois la révision terminée, vous pouvez faire en sorte que le flux envoie par email automatiquement les modifications apportées à l’équipe de gestion de votre pare-feu et serveur proxy.

Pour plus d’informations sur un exemple et un modèle Power Automate, consultez [Utiliser Power Automate pour recevoir un e-mail pour les modifications apportées aux adresses IP et URL Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Forum aux questions sur les points de terminaison réseau Office 365

Consultez ces questions fréquemment posées sur Office 365 connectivité réseau.
  
### <a name="how-do-i-submit-a-question"></a>Comment puis-je envoyer une question ?

Cliquez sur le lien situé au bas de la page pour indiquer si l’article vous a été utile ou non, mais également pour poser d’autres questions. Nous surveillons les commentaires et mettons à jour les questions contenues dans cet article avec celles que les clients nous posent le plus fréquemment.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Comment déterminer l’emplacement de mon client ?

 **L’emplacement du client** est mieux déterminé à l’aide de notre [carte de centre de données](./o365-data-locations.md).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Est-ce que ma relation d’homologation avec Microsoft est appropriée ?

 Les **emplacements d’homologation** sont décrits plus en détail dans l’article [Homologation avec Microsoft](https://www.microsoft.com/peering).
  
Avec plus de 2 500 relations d’homologation avec des fournisseurs de services Internet dans le monde entier et 70 points de présence, l’accès depuis votre réseau à nos réseaux devrait être transparent. En quelques minutes, vous pouvez vous assurer que la relation d’homologation de votre fournisseur de services Internet est optimale. [Voici quelques exemples](/archive/blogs/onthewire/__guidance) de bonnes et de mauvaises configurations d’homologation à notre réseau.
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Je vois des requêtes réseau envoyées à des adresses IP ne figurant pas sur la liste publiée. Dois-je leur octroyer l’accès ?

Nous fournissons uniquement des adresses IP pour les serveurs Office 365 sur lesquels vous devez router directement. Cette liste d’adresses IP associées aux requêtes réseau n’est pas exhaustive. Vous verrez des demandes réseau adressées à Microsoft et à des adresses IP détenues par des tiers, non publiées. Ces adresses IP sont gérées ou générées de manière dynamique. Il est donc impossible de fournir un préavis immédiat en cas de modification. Si votre pare-feu ne peut pas autoriser l’accès sur la base des noms de domaines complets associés à ces requêtes réseau, utilisez un fichier PAC ou WPAD pour gérer les requêtes.
  
Voir une adresse IP associée à Office 365 sur laquelle vous voulez obtenir plus d’informations.
  
1. Vérifiez si l’adresse IP est incluse dans une plage publiée plus grande à l’aide d’une calculatrice CIDR, comme celles-ci pour [IPv4](https://www.ipaddressguide.com/cidr) ou [IPv6](https://www.ipaddressguide.com/ipv6-cidr). Par exemple, 40.96.0.0/13 inclut l’adresse IP 40.103.0.1 Malgré 40.96 ne correspondant pas à 40.103.
2. Vérifiez si l’adresse IP appartient à un partenaire en utilisant une [requête whois](https://dnsquery.org/). Si elle appartient à Microsoft, il peut s’agir d’un partenaire interne. De nombreux points de terminaison de réseau de partenaires sont répertoriés comme appartenant à la catégorie _par défaut_ , pour laquelle les adresses IP ne sont pas publiées.
3. L’adresse IP ne fait pas partie d’Office 365 ou d’une dépendance. Office 365 publication de points de terminaison réseau n’inclut pas tous les points de terminaison réseau Microsoft.
4. Vérifiez le certificat. Avec un navigateur, connectez-vous à l’adresse IP à l’aide  *de HTTPS://\<IP_ADDRESS\>* et vérifiez les domaines répertoriés sur le certificat pour comprendre quels domaines sont associés à l’adresse IP. S’il s’agit d’une adresse IP appartenant à Microsoft et non dans la liste des adresses IP Office 365, il est probable que l’adresse IP soit associée à un CDN Microsoft tel que *MSOCDN.NET* ou un autre domaine Microsoft sans informations IP publiées. Si vous constatez que le domaine figurant sur le certificat est l’un de ceux dont nous déclarons répertorier l’adresse IP, faites-le nous savoir.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Certaines URL Office 365 pointent vers des enregistrements CNAME au lieu d’un enregistrement dans le DNS. Que dois-je faire des enregistrements CNAME ?

Les ordinateurs clients ont besoin d’un enregistrement DNS A ou AAAA qui inclut une ou plusieurs adresses IP pour se connecter à un service cloud. Certaines URL incluses dans Office 365 affichent les enregistrements CNAME au lieu des enregistrements A ou AAAA. Ces enregistrements CNAME sont intermédiaires. Il peut y en avoir plusieurs dans une chaîne. Ils sont toujours résolus en un enregistrement A ou AAAA pour une adresse IP. Par exemple, considérez la série d’enregistrements DNS suivante, qui est traduite en une adresse IP _IP_1_:

```console
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Ces redirections CNAME constituent une partie normale du DNS et sont transparentes pour l’ordinateur client et transparent pour les serveurs proxy. Elles sont utilisées pour l’équilibrage de charge, les réseaux de distribution de contenu, la haute disponibilité et l’atténuation des incidents de service. Microsoft ne publie pas les enregistrements CNAME intermédiaires, ils sont susceptibles d’être modifiés à tout moment et vous n’avez pas besoin de les configurer comme autorisé dans votre serveur proxy.

Un serveur proxy valide l’URL initiale, qui est serviceA.office.com dans l’exemple ci-dessus, et cette URL est incluse dans Office 365 publication. Le serveur proxy demande la résolution DNS de cette URL à une adresse IP et recevra IP_1. Il ne valide pas les enregistrements de redirection CNAME intermédiaires.

Les configurations codées en dur ou l’utilisation d’une liste verte basée sur des noms de domaine complets Office 365 indirects ne sont pas recommandées, ne sont pas prises en charge par Microsoft et sont connues pour provoquer des problèmes de connectivité client. Les solutions DNS qui bloquent la redirection CNAME, ou qui résolvent de manière incorrecte Office 365 entrées DNS, peuvent être résolues via des redirecteurs DNS avec la récursivité DNS activée ou à l’aide d’indicateurs racines DNS. De nombreux produits de périmètre réseau tiers intègrent en mode natif le point de terminaison de Office 365 recommandé pour inclure une liste verte dans leur configuration à l’aide du [service web d’adresse IP et d’URL Office 365](microsoft-365-ip-web-service.md).

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Pourquoi des noms tels que nsatc.net ou akadns.net figurent-ils parmi les noms de domaine de Microsoft ?

Office 365 et d’autres services Microsoft utilisent des services tiers tels que MarkMonitor et Akamai pour améliorer votre expérience d’Office 365. Pour continuer de vous offrir la meilleure expérience possible, il se peut que vous changions ces services à l’avenir. Les domaines tiers peuvent héberger du contenu, tel qu’un CDN, ou ils peuvent héberger un service, tel qu’un service de gestion du trafic géographique. Voici quelques-uns des services actuellement utilisés :
  
[MarkMonitor](https://www.markmonitor.com/) est utilisé lorsque vous voyez des demandes qui incluent  *\*.nsatc.net*. Ce service fournit une protection de nom de domaine et une surveillance pour protéger contre des comportements malveillants.
  
[ExactTarget](https://www.marketingcloud.com/) est utilisé lorsque vous voyez des demandes adressées à  *\*.exacttarget.com*. Ce service fournit une gestion des liens de messagerie électronique et une surveillance pour protéger contre des comportements malveillants.
  
[Akamai](https://www.akamai.com/) est utilisé lorsque vous voyez des requêtes incluant l’un des noms de domaine complets (FQDN) suivants. Ce service offre des services de géo-DNS et de réseau de distribution de contenu.
  
```console
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

<a name="bkmk_thirdparty"> </a>
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>J’ai besoin de la connectivité minimale pour Office 365

Office 365 est une suite de services conçue pour fonctionner sur Internet. Les promesses de fiabilité et de disponibilité sont basées sur l’accès à de nombreux services Internet standard. Par exemple, des services Internet standard tels que DNS, CRL et CDN doivent être accessibles pour utiliser Office 365, tout comme ils doivent l’être pour utiliser les services Internet les plus modernes.

La suite Office 365 est divisée en zones de service majeures. Ceux-ci peuvent être activés de manière sélective pour la connectivité et il existe une zone commune, qui est une dépendance pour tous et qui est toujours requise.

| Zone de service | Description |
|:-----|:-----|
|**Exchange** <br/> |Exchange Online et Exchange Online Protection <br/> |
|**SharePoint** <br/> |Sharepoint Online et OneDrive Entreprise <br/> |
|**Skype Entreprise Online et Microsoft Teams** <br/> |Skype Entreprise et Microsoft Teams <br/> |
|**Courant** <br/> |Office 365 Pro Plus, Office dans un navigateur, Azure AD et les autres points de terminaison réseau courants <br/> |

En plus des services Internet de base, il existe des services tiers utilisés uniquement pour intégrer des fonctionnalités. Bien qu’ils soient nécessaires pour l’intégration, ils sont marqués comme facultatifs dans l’article Office 365 points de terminaison, ce qui signifie que les fonctionnalités principales du service continueront de fonctionner si le point de terminaison n’est pas accessible. Tout point de terminaison réseau requis aura l’attribut requis défini sur true. Tout point de terminaison réseau facultatif aura l’attribut requis défini sur false et l’attribut notes détaillera les fonctionnalités manquantes que vous devez attendre si la connectivité est bloquée.
  
Si vous essayez d’utiliser Office 365 et que vous trouvez que les services tiers ne sont pas accessibles, vous devez [vous assurer que tous les noms de domaine complets marqués comme obligatoires ou facultatifs dans cet article sont autorisés par le biais du proxy et du pare-feu](urls-and-ip-address-ranges.md).
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Comment bloquer l’accès aux services grand public de Microsoft ?

La fonctionnalité de restrictions de locataire prend désormais en charge le blocage de l’utilisation de toutes les applications grand public Microsoft (applications MSA) telles que OneDrive, Hotmail et Xbox.com. Cela utilise un en-tête distinct pour le point de terminaison login.live.com. Pour plus d’informations, consultez [Utiliser les restrictions de locataire pour gérer l’accès aux applications cloud SaaS](/azure/active-directory/manage-apps/tenant-restrictions#blocking-consumer-applications).

<a name="bkmk_IPOnlyFirewall"> </a>

### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>Mon pare-feu nécessite des adresses IP et ne peut pas traiter les URL. Comment puis-je le configurer pour Office 365 ?

Office 365 ne fournit pas d’adresses IP de tous les points de terminaison réseau requis. Certaines sont proposées sous forme d’URL uniquement et sont classées par défaut. Les URL de la catégorie par défaut requises doivent être autorisées par le biais d’un serveur proxy. Si vous n’avez pas de serveur proxy, examinez comment vous avez configuré les requêtes web pour les URL que les utilisateurs tapent dans la barre d’adresses d’un navigateur web ; l’utilisateur ne fournit pas non plus d’adresse IP. Les URL de catégorie Office 365 par défaut qui ne fournissent pas d’adresses IP doivent être configurées de la même façon.

## <a name="related-topics"></a>Voir aussi

[Service web d’URL et d’adresses IP Office 365](microsoft-365-ip-web-service.md)

[Plages d’adresses IP du centre de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Configuration requise pour l’infrastructure réseau pour Microsoft Intune](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute et Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Principes de connectivité réseau Office 365](microsoft-365-network-connectivity-principles.md)
