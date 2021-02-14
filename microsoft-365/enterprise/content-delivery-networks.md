---
title: Réseaux de distribution de contenu
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/15/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Utilisez ces informations pour en savoir plus sur la façon dont Office 365 utilise les réseaux de distribution de contenu (CDN) pour améliorer les performances.
ms.openlocfilehash: 1c2230b76f354bf6f3de524b2b8c75b7d8c380e7
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46689800"
---
# <a name="content-delivery-networks-cdns"></a>Réseaux de distribution de contenu (CDN)

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les CDN permettent à Office 365 de rester rapide et fiable pour les utilisateurs finaux. Les services cloud tels qu’Office 365 utilisent des CDN pour mettre en cache des ressources statiques plus proches des navigateurs leur demandant d’accélérer les téléchargements et de réduire la latence perçue par les utilisateurs finaux. Les informations de cette rubrique vous aideront à en savoir plus sur les réseaux de distribution de contenu (CDN) et leur utilisation par Office 365.

## <a name="what-exactly-is-a-cdn"></a>Qu’est-ce qu’un CDN ?

Un CDN est un réseau distribué géographiquement composé de serveurs proxy et de fichiers dans des centres de données connectés par des réseaux de dorsale dorsale haute vitesse. Les CDN sont utilisés pour réduire la latence et les temps de chargement d’un ensemble spécifié de fichiers et d’objets dans un site web ou un service. Un CDN peut avoir plusieurs milliers de points de terminaison pour assurer une maintenance optimale des demandes entrantes en provenance de n’importe quel emplacement.

Les CDN sont couramment utilisés pour fournir des téléchargements plus rapides de contenu générique pour un site web ou un service tel que des fichiers javascript, des icônes et des images, et peuvent également fournir un accès privé au contenu des utilisateurs, tels que des fichiers dans des bibliothèques de documents SharePoint Online, des fichiers multimédias de diffusion en continu et du code personnalisé.

Les CDN sont utilisés par la plupart des services cloud d’entreprise. Les services cloud tels qu’Office 365 comptent des millions de clients qui téléchargent un mélange de contenu propriétaire (par exemple, les e-mails) et de contenu générique (par exemple, des icônes) à la fois. Il est plus efficace de placer les images que tout le monde utilise, comme les icônes, aussi près que possible de l’ordinateur de l’utilisateur. Comme il n’est pas pratique pour chaque service cloud de créer des centres de données CDN qui stockent ce contenu générique dans toutes les régions métropolitaines, ou même dans tous les principaux centres Internet du monde entier, certains de ces CDN sont partagés.

## <a name="how-do-cdns-make-services-work-faster"></a>Comment les CDN accélèrent-ils le fonctionnement des services ?

Le téléchargement d’objets courants, tels que des images de site et des icônes, peut prendre une bande passante réseau qui peut être mieux utilisée pour télécharger du contenu personnel important, tel que des e-mails ou des documents. Étant donné qu’Office 365 utilise une architecture qui inclut des CDN, les icônes, les scripts et d’autres contenus génériques peuvent être téléchargés à partir de serveurs plus proches des ordinateurs clients, ce qui accélère les téléchargements. Cela signifie un accès plus rapide à votre contenu personnel, qui est stocké en toute sécurité dans les centres de données Office 365.

Les CDN permettent d’améliorer les performances du service cloud de plusieurs façons :

- Les CDN déplacent une partie de la charge de téléchargement du réseau et des fichiers du service cloud, libérant ainsi les ressources de service cloud pour le service de contenu utilisateur et d’autres services en réduisant la nécessité de répondre aux demandes de ressources statiques.
- Les CDN sont conçus pour fournir un accès aux fichiers à faible latence en implémentant des réseaux et des serveurs de fichiers hautes performances, et en tirant parti des protocoles réseau mis à jour tels que [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) avec une compression hautement efficace et un multiplexage de demande.
- Les réseaux CDN utilisent de nombreux points de terminaison distribués globalement pour rendre le contenu disponible aussi près que possible pour les utilisateurs.

## <a name="the-office-365-cdn"></a>The Office 365 CDN

Le réseau de distribution de contenu (CDN) Office 365 intégré permet aux administrateurs Office 365 d’offrir de meilleures performances aux pages SharePoint Online de leur organisation en achant les ressources statiques plus près des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. Le CDN Office 365 utilise le [protocole HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) pour améliorer les vitesses de compression et de téléchargement.

> [!NOTE]
> Le CDN Office 365 est uniquement disponible pour les clients dans le cloud **de production** (dans le monde). Les locataires du gouvernement des États-Unis, de la Chine et de l’Allemagne ne supportent pas actuellement le CDN Office 365.

Le réseau de distribution de contenu Office 365 est composé de plusieurs réseaux de distribution de contenu qui vous permettent d’héberger des ressources statiques à différents emplacements (ou _origines_) et de les servir à partir de réseaux à haut débit mondiaux. Selon le type de contenu que vous souhaitez héberger sur le réseau de distribution de contenu Office 365, vous pouvez ajouter des origines **publiques**, **privées** ou les deux.

![Diagramme conceptuel du CDN Office 365](../media/O365-CDN/o365-cdn-flow-transparent.svg "Diagramme conceptuel du CDN Office 365")

Le contenu des origines **publiques** du réseau de distribution de contenu Office 365 est anonymement accessible à toute personne qui dispose des URL d’accès aux ressources hébergées. Comme l’accès au contenu des origines publiques est anonyme, vous ne devez l’utiliser que pour mettre en cache du contenu générique non sensible, comme des scripts, des icônes, des images et des fichiers javascript. Le réseau de distribution de contenu Office 365 est utilisé par défaut pour télécharger des ressources génériques, telles que les applications clientes Office 365, à partir d’une origine publique.

**Les origines** privées dans le CDN Office 365 fournissent un accès privé au contenu utilisateur, tel que les bibliothèques de documents SharePoint Online, les sites et les images propriétaires. L’accès au contenu des origines privées est sécurisé à l’aide de jetons générés dynamiquement, de sorte qu’il n’est accessible qu’aux utilisateurs autorisés à accéder à la bibliothèque de documents ou à l’emplacement de stockage d’origine. Les origines privées du réseau de distribution de contenu Office 365 ne peuvent être utilisées que pour du contenu SharePoint Online, et vous ne pouvez accéder aux ressources que par redirection à partir de votre client SharePoint Online.

Le réseau de distribution de contenu Office 365 est inclus dans votre abonnement SharePoint Online.

Pour plus d’informations sur l’utilisation du CDN Office 365, voir Utiliser le réseau de distribution de contenu [Office 365 avec SharePoint Online.](use-microsoft-365-cdn-with-spo.md)

Pour regarder une série de courtes vidéos qui fournissent des informations conceptuelles et howTO sur l’utilisation du CDN Office 365, visitez la chaîne [YouTube Modèles](https://aka.ms/sppnp-videos)et pratiques du développeur SharePoint.

## <a name="other-microsoft-cdns"></a>Autres CDN Microsoft

Bien qu’ils ne font pas partie du CDN Office 365, vous pouvez utiliser ces CDN dans votre client Office 365 pour accéder aux bibliothèques de développement SharePoint, au code personnalisé et à d’autres fins qui n’entrent pas dans le cadre du CDN Office 365.

### <a name="azure-cdn"></a>Azure CDN

>[!NOTE]
>À partir du 3e trimestre 2020, SharePoint Online commencera la mise en cache des vidéos sur le CDN Azure pour prendre en charge une lecture vidéo améliorée et la fiabilité. Les vidéos populaires sont diffusées à partir du point de terminaison CDN le plus proche de l’utilisateur. Ces données resteront dans la limite de conformité de Microsoft 365. Il s’agit d’un service gratuit pour tous les clients et il ne nécessite aucune action du client à configurer.

Vous pouvez utiliser le **CDN Azure** pour déployer votre propre instance CDN pour l’hébergement de composants Web Parts, bibliothèques et autres ressources personnalisés, ce qui vous permet d’appliquer des touches d’accès rapide à votre stockage CDN et d’exercer un contrôle accru sur votre configuration cdN. L’utilisation du CDN Azure n’est pas gratuite et nécessite un abonnement Azure.

Pour plus d’informations sur la configuration d’une instance de CDN Azure, voir Démarrage rapide : intégrer un compte de stockage [Azure à Azure CDN.](https://docs.microsoft.com/azure/cdn/cdn-create-a-storage-account-with-cdn)

Pour obtenir un exemple de la façon dont le CDN Azure peut être utilisé pour héberger des composants Web Part SharePoint, voir Déployer votre composant Web Part côté [client SharePoint sur Azure CDN](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn).

Pour plus d’informations sur le module Azure CDN PowerShell, voir [Gérer le CDN Azure avec PowerShell.](https://docs.microsoft.com/azure/cdn/cdn-manage-powershell)

### <a name="microsoft-ajax-cdn"></a>Microsoft Ajax CDN

Le **CDN Ajax** de Microsoft est un CDN en lecture seule qui propose de nombreuses bibliothèques de développement populaires, notamment jQuery (et toutes ses autres bibliothèques), ASP.NET Ajax, Bootstrap, Knockout.js, etc.
  
Pour inclure ces scripts dans votre projet, remplacez simplement les références à ces bibliothèques disponibles publiquement par des références à l’adresse CDN au lieu de l’inclure dans votre projet lui-même. Par exemple, utilisez le code suivant pour lier jQuery :

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Pour plus d’informations sur l’utilisation du CDN Microsoft Ajax, voir [CDN Microsoft Ajax.](https://docs.microsoft.com/aspnet/ajax/cdn/overview)

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Comment Office 365 utilise-t-il le contenu d’un CDN ?

Quel que soit le CDN que vous configurez pour votre client Office 365, le processus de récupération des données de base est le même.

1. Votre client (navigateur ou application cliente Office) demande des données à Office 365.

2. Office 365 renvoie les données directement à votre client ou, si les données font partie d’un ensemble de contenu hébergé par le CDN, redirige votre client vers l’URL du CDN.

    a. Si les données sont déjà mises en cache dans une origine _publique,_ votre client télécharge les données directement à partir de l’emplacement CDN le plus proche vers votre client.

    b. Si les données sont déjà  mises en cache dans une origine privée, le service CDN vérifie les autorisations de votre compte d’utilisateur Office 365 sur l’origine. Si vous avez des autorisations, SharePoint Online génère dynamiquement une URL personnalisée composée du chemin d’accès à la bien dans le CDN et de deux jetons d’accès, et renvoie l’URL personnalisée à votre client. Votre client télécharge ensuite les données directement à partir de l’emplacement CDN le plus proche vers votre client à l’aide de l’URL personnalisée.

3. Si les données ne sont pas mises en cache sur le CDN, le nœud CDN demande les données à Office 365, puis les met en cache pendant un certain temps une fois que votre client a téléchargé les données.

Le CDN indique le centre de données le plus proche du navigateur de l’utilisateur et, à l’aide de la redirection, télécharge les données demandées à partir de cet endroit. La redirection CDN est rapide et permet aux utilisateurs de gagner beaucoup de temps de téléchargement.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Comment configurer mon réseau pour que les CDN fonctionnent mieux avec Office 365 ?

La réduction de la latence entre les clients de votre réseau et les points de terminaison CDN est essentielle pour garantir des performances optimales. Vous pouvez utiliser les meilleures pratiques décrites dans La gestion des points de terminaison [Office 365](managing-office-365-endpoints.md) pour vous assurer que votre configuration réseau permet aux navigateurs clients d’accéder directement au CDN au lieu de router le trafic CDN via les proxies centraux pour éviter d’introduire une latence inutile.

Vous pouvez également lire les principes de connectivité réseau [d’Office 365](https://aka.ms/o365networkingprinciples) pour comprendre les concepts de l’optimisation des performances réseau d’Office 365.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Existe-t-il une liste de tous les CDN qu’Office 365 utilise ?

Les CDN utilisés par Office 365 sont toujours sujets à modification et, dans de nombreux cas, plusieurs partenaires CDN sont configurés dans le cas où l’un d’eux est indisponible. Les CDN principaux utilisés par Office 365 sont :

|CDN  |Company  |Utilisation  |Liens  |
|---------|---------|---------|---------|
|Office 365 CDN     |Akamai         |Ressources génériques dans les origines publiques, contenu utilisateur SharePoint dans les origines privées         |[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md)         |
|Azure CDN     |Microsoft         |Code personnalisé, solutions SharePoint Framework         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|CDN Microsoft Ajax (lecture seule)     |Microsoft         |Bibliothèques courantes pour Ajax, jQuery, ASP.NET, Bootstrap, Knockout.js, etc.         |[Microsoft Ajax CDN](https://docs.microsoft.com/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>Quels gains de performances un CDN offre-t-il ?

Il existe de nombreux facteurs impliqués dans la mesure des différences de performances spécifiques entre les données téléchargées directement à partir d’Office 365 et les données téléchargées à partir d’un CDN spécifique, tels que votre emplacement par rapport à votre client et au point de terminaison CDN le plus proche, le nombre de ressources sur une page qui sont servies par le CDN et les modifications temporaires de la latence et de la bande passante du réseau. Toutefois, un simple test A/B peut vous aider à montrer la différence de temps de téléchargement pour un fichier spécifique.

Les captures d’écran suivantes illustrent la différence de vitesse de téléchargement entre l’emplacement du fichier natif dans Office 365 et le même fichier hébergé sur le réseau de distribution de contenu [Microsoft Ajax.](https://docs.microsoft.com/aspnet/ajax/cdn/overview) Ces captures d’écran sont disponibles sous **l’onglet** Réseau des outils de développement Internet Explorer 11. Ces captures d’écran montrent la latence sur la bibliothèque jQuery populaire. Pour faire monter cet écran, dans Internet Explorer,  appuyez sur **F12** et sélectionnez l’onglet Réseau qui est marqué par une icône Wi-Fi de connexion.
  
![Capture d’écran du réseau F12](../media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Cette capture d’écran montre la bibliothèque téléchargée vers la galerie de pages maîtres sur le site SharePoint Online lui-même. Le temps de chargement de la bibliothèque est de 1,51 seconde.
  
![Capture d’écran du temps de chargement de 1,51 s](../media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
La deuxième capture d’écran montre le même fichier remis par le CDN de Microsoft. Cette fois, la latence est d’environ 496 millisecondes. Il s’agit d’une amélioration importante qui montre qu’une seconde entière est en dehors du temps total de téléchargement de l’objet.
  
![Capture d’écran du temps de chargement de 469 ms](../media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>Mes données sont-elles sécurisées ?

Nous prenons soin de protéger les données qui gèrent votre entreprise. Les données stockées dans le CDN Office 365 sont chiffrées en transit et au repos, et l’accès aux données dans le CDN SharePoint Office 365 est sécurisé par les autorisations des utilisateurs Office 365 et l’autorisation de jeton. Les demandes de données dans le CDN SharePoint Office 365 doivent être référengées (redirigées) à partir de votre client Office 365, sinon un jeton d’autorisation ne sera pas généré.

Pour vous assurer que vos données restent sécurisées, nous vous recommandons de ne jamais stocker de contenu utilisateur ou d’autres données sensibles dans un CDN public. Étant donné que l’accès aux données dans un CDN public est anonyme, les CDN publics doivent uniquement être utilisés pour héberger du contenu générique tel que des fichiers de script web, des icônes, des images et d’autres ressources non sensibles.

> [!NOTE]
> Les fournisseurs de CDN tiers peuvent avoir des normes de confidentialité et de conformité qui diffèrent des engagements décrits par le Centre de confidentialité Office 365. Les données mises en cache via le service CDN peuvent ne pas être conformes aux conditions de traitement des données Microsoft (DPT) et se trouver en dehors des limites de conformité du Centre de gestion de la conformité Office 365.

Pour obtenir des informations détaillées sur la confidentialité et la protection des données pour les fournisseurs de CDN Office 365, consultez les informations suivantes :  

- En savoir plus sur la protection de la confidentialité et des données Office 365 dans le Centre de gestion [de la confidentialité Microsoft](https://www.microsoft.com/trustcenter)
- En savoir plus sur la confidentialité et la protection des données [d’Akamai](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp) dans le Centre de gestion de la confidentialité Akamai
- En savoir plus sur la protection des données et la confidentialité Azure dans [le Centre de gestion de la confidentialité Azure](https://azure.microsoft.com/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Comment puis-je sécuriser mon réseau avec tous ces services tiers ?

L’utilisation d’un ensemble étendu de services partenaires permet à Office 365 de mettre à l’échelle et de répondre aux exigences de disponibilité, ainsi que d’améliorer l’expérience utilisateur lors de l’utilisation d’Office 365. Les services tiers dont Office 365 tire parti incluent les deux listes de révocation de certificats . par exemple, crl.microsoft.com ou sa.symcb.com, et CDN ; par exemple, r3.res.outlook.com. Chaque FQDN CDN généré par Office 365 est un FQDN personnalisé pour Office 365. Si vous êtes envoyé à un FQDN à la demande d’Office 365, vous pouvez être certain que le fournisseur cdN contrôle le FQDN et le contenu sous-jacent à cet emplacement.
  
Pour les clients qui souhaitent séparer les demandes destinées à un centre de données Microsoft ou Office 365 des demandes destinées à un tiers, nous avons écrit des conseils sur la gestion des points de terminaison [Office 365.](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Existe-t-il une liste de tous les FQDN qui exploitent les CDN ?

La liste des FQDN et la façon dont ils exploitent les CDN changent au fil du temps. Reportez-vous à notre page d’URL et de [plages d’adresses IP Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744) publiée pour vous mettre à jour sur les derniers FQDN qui exploitent les CDN.

Vous pouvez également utiliser le service Web d’URL et d’adresse [IP Office 365](microsoft-365-ip-web-service.md) pour demander les URL et plages d’adresses IP Office 365 actuelles au format CSV ou JSON.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Puis-je utiliser mon propre CDN et le contenu du cache sur mon réseau local ?

Nous recherchons continuellement de nouvelles façons de répondre aux besoins de nos clients et explorons actuellement l’utilisation de solutions proxy de mise en cache et d’autres solutions CDN sur site.

Bien qu’il ne fait pas partie du CDN Office 365, vous pouvez également utiliser le **CDN Azure** pour héberger des composants Web, des bibliothèques et d’autres ressources personnalisés, ce qui vous permet d’appliquer des touches d’accès rapide à votre stockage CDN et d’exercer un meilleur contrôle sur votre configuration cdN. L’utilisation du CDN Azure n’est pas gratuite et nécessite un abonnement Azure. Pour plus d’informations sur la configuration d’une instance de CDN Azure, voir Démarrage rapide : intégrer un compte de stockage [Azure à Azure CDN.](https://docs.microsoft.com/azure/cdn/cdn-create-a-storage-account-with-cdn)

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>J’utilise Azure ExpressRoute pour Office 365, cela change-t-il les choses ?

[Azure ExpressRoute pour Office 365](azure-expressroute.md) fournit une connexion dédiée à l’infrastructure Office 365 séparée de l’Internet public. Cela signifie que les clients devront toujours se connecter sur des connexions non ExpressRoute pour se connecter à des CDN et à d’autres infrastructures Microsoft qui ne sont pas explicitement incluses dans la liste des services pris en charge par ExpressRoute. Pour plus d’informations sur l’itinéraire d’un trafic spécifique tel que les demandes destinées aux CDN, reportez-vous à la gestion du [trafic réseau Office 365.](routing-with-expressroute.md)

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>Puis-je utiliser des CDN avec SharePoint Server local ?

L’utilisation de CDN n’est logique que dans un contexte SharePoint Online et doit être évitée avec SharePoint Server. Cela est dû au fait que tous les avantages de l’emplacement géographique ne sont pas réels si le serveur se trouve en local ou se ferme géographiquement quand même. En outre, s’il existe une connexion réseau aux serveurs où il est hébergé, le site peut être utilisé sans connexion Internet et, par conséquent, ne peut pas récupérer les fichiers CDN. Dans le cas contraire, vous devez utiliser un CDN s’il en existe un disponible et stable pour la bibliothèque et les fichiers dont vous avez besoin pour votre site.
  
Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Voir aussi

[Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples)

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/trustcenter)

[Optimisation des performances Office 365](tune-microsoft-365-performance.md)
