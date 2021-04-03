---
title: URL et plages d’adresses IP Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/01/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
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
description: 'Résumé : Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles pour les clients utilisant des plans Office 365, y compris GCC (Government Community Cloud).'
hideEdit: true
ms.openlocfilehash: b4b256e9138f89cd9d44182a08dd22050b17f7c2
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51581105"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>URL et plages d’adresses IP Office 365

Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles pour les clients utilisant des plans Office 365, y compris GCC (Government Community Cloud).
  
*Office 365 dans le monde (GCC inclus)* | [Office 365 géré par 21Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](microsoft-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) |

||||
|:-----|:-----|:-----|
|**Dernière mise à jour :** 01/03/2021 : ![RSS](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Modifier l'abonnement au journal](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Téléchargement :** toutes les destinations obligatoires et facultatives dans une liste [au format JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> | **Utilisation :** nos [fichiers PAC](managing-office-365-endpoints.md#pacfiles) proxy <br/> |

 Commencez par [Gestion des points de terminaison Office 365](managing-office-365-endpoints.md) pour comprendre nos recommandations en matière de gestion de la connectivité réseau à l’aide de ces données. Les données du point de terminaison sont mis à jour sont mises à jour au besoin au début de chaque mois avec de nouvelles adresses IP et URL publiés 30 jours avant d’être activé(e). Cela permet aux clients qui ne disposent pas encore de mises à jour automatisées de compléter leurs processus avant qu'une nouvelle connectivité ne soit nécessaire. Les points de terminaison peuvent également être mis à jour au cours du mois si nécessaire pour les demandes des remontés de support, les incidents de sécurité ou autres exigences opérationnelles immédiates. Les données affichées sur cette page ci-dessous sont toutes générées à partir des services web REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez accéder directement au [service web](microsoft-365-ip-web-service.md).

Les données de point de terminaison ci-dessous répertorient les exigences de connectivité à partir de l’ordinateur d’un utilisateur vers Office 365. Elles n’incluent pas les connexions réseau de Microsoft vers un réseau client, parfois appelées connexions réseau entrantes ou hybrides. Voir [Autres points de terminaison](additional-office365-ip-addresses-and-urls.md) pour plus d’informations.

Les points de terminaison sont regroupés en quatre zones de service. Les trois premières zones de service peuvent être sélectionnées indépendamment pour la connectivité. La quatrième zone de service est une dépendance courante (appelée Microsoft 365 Common et Office) et doit toujours avoir une connectivité réseau.

Les colonnes de données affichées sont :

- **ID** : numéro d’identification de la ligne, également connu sous forme d’un ensemble de points de terminaison. Cet ID est le même que celui retourné par le service web pour l’ensemble de points de terminaison.

- **Catégorie** : indique si l’ensemble de points de terminaison est associé à la classe « Optimiser », « Autoriser » ou « Par défaut ». Des informations sur ces catégories et des instructions pour les gérer sont disponibles dans la rubrique [Nouvelles catégories de points de terminaison Office 365](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). Cette colonne répertorie également les ensembles de points de terminaison nécessaires pour que la connectivité réseau fonctionne. Pour les ensembles de points de terminaison qui ne nécessitent pas de connectivité réseau, nous fournissons des remarques dans ce champ pour indiquer les fonctionnalités manquantes si l’ensemble de points de terminaison est bloqué. Si vous excluez l’ensemble d’une zone de service, les ensembles de points de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER** : cette option est définie sur **Oui** si l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes d’itinéraire Office 365. La Communauté BGP qui inclut les préfixes d’itinéraire indiqués s’aligne avec la zone de service répertoriée. Quand ER est défini sur **Non**, cela signifie qu’ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison. Toutefois, le fait qu’ER soit défini sur **Non** ne signifie pas pour autant qu’aucun itinéraire n’est proposé pour un ensemble de points de terminaison.

- **Adresses** : répertorie les noms de domaine complets ou noms de domaines génériques et plages d’adresses IP pour l’ensemble de points de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure plusieurs adresses IP individuelles dans le réseau spécifié.
 
- **Ports** : répertorie les ports TCP ou UDP associés aux adresses pour former le point de terminaison réseau. Vous remarquerez peut-être certains doublons dans les plages d’adresses IP lorsque plusieurs ports sont répertoriés.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

>[!Note]
>Pour des recommandations sur les adresses IP et les URL de Yammer, voir [L'utilisation d'adresses IP codées en dur pour Yammer n'est pas recommandée](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592)sur le blog Yammer.
>

## <a name="related-topics"></a>Rubriques connexes
[Points de terminaison supplémentaires non inclus dans le service web pour URL et adresses IP Office 365](https://docs.microsoft.com/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls?view=o365-worldwide)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[Terminaux généraux Microsoft Stream ](/stream/network-overview#general-microsoft-stream-endpoints)
  
[Surveiller la connectivité Microsoft 365](./monitor-connectivity.md)

[L'AC racine et l'AC intermédiaire se regroupent sur le système d'application tiers](../compliance/encryption-office-365-certificate-chains.md)
  
[Connectivité des clients](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Réseaux de distribution de contenu](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Les gammes d'IP et les étiquettes de service de Microsoft Azure - Public Cloud](https://www.microsoft.com/download/details.aspx?id=56519)

[Les gammes d'IP et les étiquettes de service de Microsoft Azure - Cloud du gouvernement américain](https://www.microsoft.com/download/details.aspx?id=57063)

[Les gammes d'IP et les étiquettes de service de Microsoft Azure - Allemagne Cloud](https://www.microsoft.com/download/details.aspx?id=57064)

[Les gammes d'IP et les étiquettes de service de Microsoft Azure - China Cloud](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

[Nom du service et protocole de transport Registre des numéros de port](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
