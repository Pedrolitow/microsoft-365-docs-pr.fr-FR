---
title: URL et plages d’adresses IP Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/29/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Résumé : Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles pour les clients utilisant des plans Office 365, y compris GCC (Government Community Cloud).'
hideEdit: true
ms.openlocfilehash: e01ee3d14889d03c8501b18f48a308a69f75c2e1
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2022
ms.locfileid: "66970185"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>URL et plages d’adresses IP Office 365

Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles pour les clients utilisant des plans Office 365, y compris GCC (Government Community Cloud).
  
*Office 365 dans le monde entier (+Cloud de la communauté du secteur public)*\|[Office 365 géré par 21 vianet](urls-and-ip-address-ranges-21vianet.md)\|[Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) \| [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) \|

|Remarques|Télécharger|Utilisation|
|---|---|---|
|**Dernière mise à jour :** 29/06/2022 – ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement au journal des modifications](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Téléchargement :** toutes les destinations obligatoires et facultatives dans une liste [au format JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).|**Utilisation :** nos [fichiers PAC](managing-office-365-endpoints.md#pacfiles) proxy|
|

Commencez avec la [Gestion des points de terminaison Office 365](managing-office-365-endpoints.md) afin de comprendre nos recommandations pour gérer la connectivité réseau à l’aide de ces données. Les données de points de terminaison sont mises à jour au début de chaque mois avec de nouvelles adresses IP et URL publiées 30 jours avant d’être activées. Cela permet aux clients qui n’ont pas encore de mises à jour automatisées de terminer leurs processus avant qu’une nouvelle connectivité soit requise. Les points de terminaison peuvent également être mis à jour au cours du mois si besoin est pour traiter les demandes de support, les incidents de sécurité ou autres exigences opérationnelles immédiates. Les données contenues sur la page ci-dessous sont générées à partir des services web REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devriez aller directement au [service web](microsoft-365-ip-web-service.md).

Les données de point de terminaison ci-dessous répertorient les conditions requises pour la connectivité de l’ordinateur d’un utilisateur à Office 365. Pour plus d’informations sur les adresses IP utilisées pour les connexions réseau de Microsoft vers un réseau client, parfois appelées connexions réseau entrantes ou hybrides, voir [Points de terminaison supplémentaires](additional-office365-ip-addresses-and-urls.md) pour plus d’informations.

Les points de terminaison sont regroupés en quatre zones de service représentant les trois charges de travail principales et un ensemble de ressources communes. Les groupes peuvent être utilisés pour associer des flux de trafic à une application particulière, mais étant donné que les fonctionnalités consomment souvent des points de terminaison sur plusieurs charges de travail, ces groupes peuvent être utilisés pour limiter l’accès.

Les colonnes de données affichées sont :

- **ID** : numéro d’identification de la ligne, également connu sous forme d’un ensemble de points de terminaison. Cet ID est le même que celui retourné par le service web pour l’ensemble de points de terminaison.

- **Catégorie** : Indique si l'ensemble de points de terminaison est classé dans la catégorie **Optimiser**, **Autoriser** ou **Par défaut**. Cette colonne indique également les ensembles des points de terminaison qui doivent avoir une connectivité réseau. Pour les ensembles des points de terminaison qui ne sont pas tenus d'avoir une connectivité réseau, nous fournissons des notes dans ce champ pour indiquer la fonctionnalité qui manquerait si l'ensemble des points de terminaison était bloqué. Si vous excluez une zone de service entière, les ensembles de points de terminaison énumérés comme requis ne nécessitent pas de connectivité.

   Vous pouvez en savoir plus sur ces catégories et des conseils pour leur gestion dans [les nouvelles catégories de points de terminaison Office 365](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories).

- **ER** : ceci est **oui** si l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes de route Office 365. La communauté BGP qui inclut les préfixes d’itinéraire affichés s’aligne sur la zone de service répertoriée. Lorsque l’ER a la valeur **Non**, cela signifie qu’ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison.

   Certains itinéraires peuvent être publiés dans plusieurs communautés BGP, ce qui permet aux points de terminaison d’une plage d’adresses IP donnée de traverser le circuit ER, mais ne sont toujours pas pris en charge. Dans tous les cas, la valeur de la colonne ER d’un jeu de points de terminaison donné doit être respectée. Pour plus d’informations sur les communautés BGP, consultez [Utilisation de communautés BGP dans les scénarios ExpressRoute pour Office 365](bgp-communities-in-expressroute.md#key-planning-considerations-to-using-bgp-communities).

- **Adresses** : répertorie les noms de domaine complets ou les noms de domaine génériques et les plages d’adresses IP pour l’ensemble de points de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure de nombreuses adresses IP individuelles dans le réseau spécifié.

- **Ports** : répertorie les ports TCP ou UDP qui sont combinés avec les adresses IP répertoriées pour former le point de terminaison réseau. Vous remarquerez peut-être une duplication dans les plages d’adresses IP où différents ports sont répertoriés.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

> [!NOTE]
> Pour des recommandations sur les adresses IP et les URL de Yammer, voir [L'utilisation d'adresses IP codées en dur pour Yammer n'est pas recommandée](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592)sur le blog Yammer.

## <a name="related-topics"></a>Rubriques connexes

[Points de terminaison supplémentaires non inclus dans le service web pour URL et adresses IP Office 365](additional-office365-ip-addresses-and-urls.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[Terminaux généraux Microsoft Stream ](/stream/network-overview#general-microsoft-stream-endpoints)
  
[Surveiller la connectivité Microsoft 365](./monitor-connectivity.md)

[L'AC racine et l'AC intermédiaire se regroupent sur le système d'application tiers](../compliance/encryption-office-365-certificate-chains.md)
  
[Connectivité des clients](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Réseaux de distribution de contenu](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Les gammes d'IP et les étiquettes de service de Microsoft Azure - Public Cloud](https://www.microsoft.com/download/details.aspx?id=56519)

[Les gammes d'IP et les étiquettes de service de Microsoft Azure - Cloud du gouvernement américain](https://www.microsoft.com/download/details.aspx?id=57063)

[Les gammes d'IP et les étiquettes de service de Microsoft Azure - China Cloud](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

[Nom du service et protocole de transport Registre des numéros de port](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
