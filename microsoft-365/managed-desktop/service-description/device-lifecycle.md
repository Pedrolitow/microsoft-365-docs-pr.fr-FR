---
title: Cycle de vie des produits bureau géré Microsoft
description: Cette rubrique répertorie les spécifications de périphérique utilisées dans le bureau géré Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.openlocfilehash: 431b28635f856ebd50e1de4129c00149e1e7c78d
ms.sourcegitcommit: b65c80051e53d9be223f4769f4d42a39f5a07735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "39962341"
---
# <a name="microsoft-managed-desktop-product-lifecycle"></a>Cycle de vie des produits bureau géré Microsoft

Microsoft Managed Desktop propose aux utilisateurs finaux qu’ils utilisent toujours des appareils offrant les meilleures performances, la fiabilité, la conception et la sécurité (par exemple, la prise en charge de fonctionnalités telles que Windows Hello). Pour ce faire, le bureau géré Microsoft gère un petit catalogue d' [appareils approuvés](device-list.md)mis à jour en permanence. 
 
Cette rubrique décrit en détail le cycle de vie des appareils à mesure qu’ils sont ajoutés et supprimés du catalogue approuvé. 

> [!NOTE]
> Dans cette rubrique, nous allons établir une distinction entre le « périphérique » et le « produit ». Par « périphérique », nous entendons un ordinateur individuel spécifique. Par exemple, « Serial Number 1234 », « Bill Laptop », « Shared VM XYZ » se réfèrent à des appareils spécifiques. Toutefois, un « produit » fait référence à une collection ou à une famille d’appareils. Par exemple, « Fabrikam Laptop », « adatum ZX450 Laptop », etc. Ceci est important, car les produits sont ajoutés à notre liste ou catalogue [approuvé](device-list.md), et les appareils sont les ce que vous obtenez inscrit dans Microsoft Managed Desktop.

## <a name="product-lifecycle"></a>Cycle de vie du produit

 En règle générale, les produits passent par les phases de cycle de vie suivantes :

- [Version et évaluation du produit](#product-release-and-evaluation)
- [Période de disponibilité principale du produit](#product-primary-availability-period)
- [Période de grâce du produit](#product-grace-period)
- [Retrait du produit](#product-retirement)


La séquence entière est illustrée dans cette illustration :

![chronologie du cycle de vie : en commençant par la disponibilité générale du produit, la « disponibilité principale » est de deux ans. Pendant ce temps, la fenêtre de certification se termine et, à un moment donné, l’appareil est intégré. À la fin de la disponibilité principale, le produit est archivé et la « période de grâce » de trois ans commence. À partir du moment où l’appareil est intégré, il dispose d’une période d’utilisation de 3 ans jusqu’à ce qu’il soit retiré de la gestion. À la fin de la période de grâce, nous supprimons le produit du catalogue.](images/non-dark1-edits.PNG)

Les produits restent dans le catalogue pendant une période de 24 mois, mais les <em>appareils</em> restent sous gestion pendant 3 ans en fonction de leur date d’inscription individuelle. En effet, chaque produit a trois dates importantes, mais chaque périphérique ne possède qu’un seul. Pour les produits, ces trois dates sont calculées en fonction de la <em>Date d’approbation</em>et, par conséquent, nous publions ces dates lors de l’approbation afin que vous puissiez toujours continuer et planifier l’ensemble du cycle de vie du produit.

Ce tableau montre des exemples de dates pour un produit théorique :


|Produit  |Date approuvée  |Fin de la disponibilité principale  |Fin de eligiblity  |
|---------|---------|---------|---------|
|Ordinateur portable Fabrikam    | 1/1/2017 | 6/1/2019 | 6/1/2022 |
|Ordinateur portable adatum   | 1/1/2018 | 6/1/2020 | 6/1/2023  |

Ce tableau montre des exemples de dates pour les *appareils*théoriques :


|ID de l’appareil  |Date d’enregistrement  |Date de déclassement  |
|---------|---------|---------|
|#123412 d’ordinateur portable     |  2/3/2018       |  2/3/2021       |
|#321513 de bureau     | 6/2/2018        |  6/2/2021       |


## <a name="product-release-and-evaluation"></a>Version et évaluation du produit

Le cycle de vie du produit démarre lorsqu’un fabricant publie publiquement le produit :

![chronologie de cycle de vie montrant la publication et la période d’évaluation](images/non-dark3-edits.PNG)

Pendant cette phase, l’équipe d’ingénierie de bureau géré Microsoft procède à son évaluation et à sa certification pour un produit. L’équipe évalue les fonctionnalités telles que la fiabilité et les performances avec Windows, la conformité avec une référence matérielle, le sentiment de marché et la préparation des stocks et des canaux, entre autres choses. Ce processus prend généralement environ 6 semaines.
  
Microsoft Managed Desktop n’évalue que les appareils pour la certification dans les six premiers mois de disponibilité. Cela permet de s’assurer que nous focalisons toujours sur la dernière génération de matériel.
 
À la fin de cette phase, le bureau géré Microsoft ajoute le produit à la [liste approuvée](device-list.md), libérant ainsi le produit pour les inscriptions client. Quelle que soit la date à laquelle un appareil est certifié, sa **Date approuvée** est la date de retour à la date de disponibilité générale des produits. 


## <a name="product-primary-availability-period"></a>Période de disponibilité principale du produit

Cette période est le cœur de la disponibilité du produit :

![chronologie de la durée de vie avec la disponibilité principale](images/non-dark4-edits.PNG)

Tout périphérique inscrit pendant cette période reçoit les trois années de prise en charge complètes du bureau géré Microsoft (comme illustré par le scénario bleu). Cette période dure jusqu’à ce qu’une date de fin soit définie sur 24 mois à compter de la date de disponibilité générale.

Vous pouvez considérer cette période comme une « ouverture » efficace, afin d’optimiser la valeur du bureau géré Microsoft, vous devez cibler vos modèles d’approvisionnement et les produits sélectionnés pour qu’ils tombent dans cette période. En guise d’exemple, un client doit éviter de le régler sur une période de déploiement sur deux ans à l’aide d’un produit qui se trouve dans le dernier mois de la disponibilité principale : la plupart de ces appareils ne recevront pas les trois années complètes de la gestion de bureau géré Microsoft (voir [période de grâce](#product-grace-period) pour plus d’informations).  

## <a name="product-grace-period"></a>Période de grâce du produit

La période de grâce du produit est une période de trois ans suivant la disponibilité principale. Cette phase vous permet d’inscrire des appareils provenant d’une famille de produits pris en charge, tout en conservant les promesses du bureau géré Microsoft concernant les performances du matériel et des appareils modernes. Cette phase est idéale pour les clients qui ont pris des décisions d’approvisionnement avant de connaître Microsoft Managed Desktop. 

Si vous avez récemment acheté un certain nombre d’appareils approuvés avant de vous inscrire à l’aide de Microsoft Managed Desktop, vous pouvez toujours les inscrire, mais vous ne recevrez pas les trois années de gestion. Au lieu de cela, ils ne sont pas conformes à la date de déclassement, quel que soit le moment de leur enregistrement. En arrière-plan, le bureau géré Microsoft traitera ces appareils comme s’ils étaient inclus dans le dernier jour de disponibilité principale. Dans cette illustration, vous pouvez voir ce scénario en notant que le périphérique bleu et le périphérique vert se terminent le même jour, en dépit de leur différence d’un an dans l’enregistrement :


![chronologie de la durée de vie avec la période de grâce](images/non-dark2-edits.PNG)

L’exemple de Fabrikam Laptop du tableau précédent illustre cette situation : 

|Produit  |Date approuvée  |Fin de la disponibilité principale  |Fin de eligiblity  |
|---------|---------|---------|---------|
|Ordinateur portable Fabrikam    | 6/1/2017 | 6/1/2019 | 6/1/2022 |

En tant que client, vous pouvez inscrire les ordinateurs portables Fabrikam jusqu’à 6/1/2022, mais ils seront tous traités comme si vous les aviez inscrits le 6/1/2019. Si vous inscrivez un ordinateur portable Fabrikam sur 6/1/2021, vous n’obtiendrez qu’un an de gestion. Cette stratégie vous permet d’extraire des cycles de vie partiels des produits précédemment pris en charge, au lieu de devoir acheter de nouveaux appareils prématurément. 

Enfin, pendant cette phase, l’appareil est retiré de la [liste des périphériques](device-list.md) et déplacé vers la liste des [périphériques archivés](archived-device-list.md).


## <a name="product-retirement"></a>Retrait du produit

Le retrait du produit est la phase finale du cycle de vie. Dans cette phase, aucun nouveau périphérique de ce type de produit ne peut être inscrire dans Microsoft Managed Desktop et, par définition, tous les périphériques existants sont désormais en dehors de leur période de trois ans autorisée. Pendant ce temps, le bureau géré Microsoft supprime entièrement l’appareil de la liste publique. Il s’agit également de cette phase où, si vous n’avez pas déjà effectué des remplacements, vous commencez à voir les services réduits, car le bureau géré par Microsoft commence à sortir des appareils qui ne sont pas conformes. 

## <a name="devices-that-are-out-of-compliance"></a>Périphériques non conformes

Un périphérique n’est pas conforme lorsque sa fenêtre autorisée pour la gestion de bureau géré Microsoft s’est écoulée. Cela se produit lorsque le périphérique a atteint les trois années de gestion ou lorsque ce type de produit est supprimé du catalogue d’appareils, selon ce qui se produit en premier. Vous devez toujours cibler vos cycles d’approvisionnement de manière à ce que les nouveaux appareils soient déployés avant les appareils actuels ne sont pas conformes.

L’équipe de bureau géré Microsoft sait que les cycles d’approvisionnement sont longs et planifiés sur les budgets de longue durée. Pour vous assurer que vous êtes toujours conscient de l’état de votre population de périphériques, nous fournissons un [site Web](https://aka.ms/mmdportal) qui répertorie tous les périphériques sous gestion, la date de la retraite future et un état indiquant sa conformité. Cela signifie que vous avez toujours les dernières informations relatives à l’âge de l’appareil et que vous pouvez utiliser le rapport dans n’importe quel cycle de planification des approvisionnements. 


En outre, nous allons également effectuer les actions automatiques suivantes pour vous assurer que les nouveaux appareils sont déployés à temps :


|Chronologie  |Action  |
|---------|---------|
|T-90     | Nous marquerons ce périphérique comme **expirant bientôt**, avec un marqueur jaune sur le site Web de l’inventaire des appareils.  |
|T-60     | Nous marquerons ce périphérique comme **arrivant à expiration** avec un marqueur rouge sur le site Web de l’inventaire des appareils.       |
|T-30     | Nous allons publier un message sur le portail d’administration indiquant que les appareils quittent la conformité de façon imminente.       |
|0     |  Nous allons ajuster le portail d’administration pour dire que les appareils ont expiré redirigez d’abord les administrateurs vers les terrains sur la liste des appareils.       |
|T + 30     |  Nous réduirons la fonctionnalité de portail d’administration jusqu’à ce que de nouveaux appareils soient déployés.       |
|T + 60     |  Nous réduirons la fonctionnalité de portail d’administration jusqu’à ce que de nouveaux appareils soient déployés.       |
|T + 90     |  Nous supprimons l’appareil de la gestion. À ce stade, le périphérique est uniquement votre propre responsabilité et vous ne devez plus le considérer comme sécurisé ou à jour. Par ailleurs, l’appareil sera dans un état inconnu, car chaque fournisseur de service de configuration contrôle ses propres paramètres.|




