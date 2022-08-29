---
title: Générer des requêtes à l’aide du mode guidé dans Microsoft 365 Defender repérage avancé
description: Découvrez comment générer des requêtes en mode guidé en combinant différents filtres et conditions disponibles.
keywords: mode guidé, repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 583e22a57d591176c0077cc9e6d2656c6802d05e
ms.sourcegitcommit: 7374c7b013890744d74e5214f7f8d69ca7874466
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2022
ms.locfileid: "67406546"
---
# <a name="build-hunting-queries-using-guided-mode-in-microsoft-365-defender"></a>Générer des requêtes de chasse à l’aide du mode guidé dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Le générateur de requêtes en mode guidé permet aux analystes de créer des requêtes de chasse significatives *sans connaître Langage de requête Kusto (KQL) ou le schéma de données*. Les analystes de chaque niveau d’expérience peuvent utiliser le générateur de requêtes pour filtrer les données des 30 derniers jours afin de rechercher des menaces, d’étendre les enquêtes sur les incidents, d’effectuer des analyses de données sur les données de menaces ou de se concentrer sur des zones de menace spécifiques.

L’analyste peut choisir le jeu de données à examiner et les filtres et conditions à utiliser pour limiter les données à ce dont ils ont besoin. 


## <a name="open-query-in-builder"></a>Ouvrir la requête dans le générateur
Dans la page **Repérage avancé** , **sélectionnez Créer nouveau** pour ouvrir un nouvel onglet de requête, puis sélectionnez **Requête dans le générateur**. 

![Capture d’écran du générateur de requêtes en mode guidé](../../media/guided-hunting/query-in-builder-page.png)

Cela vous amène au mode guidé, où vous pouvez ensuite construire votre requête en sélectionnant différents composants à l’aide de menus déroulants.

## <a name="specify-the-data-domain-to-hunt-in"></a>Spécifier le domaine de données dans lequel effectuer la chasse
Vous pouvez contrôler l’étendue de la chasse en sélectionnant le domaine couvert par la requête :

![Capture d’écran de la liste déroulante des domaines du générateur de requêtes en mode guidé](../../media/guided-hunting/query-builder-view-in.png)


La sélection de **Tous** inclut les données de tous les domaines auxquels vous avez actuellement accès. Le rétrécissement vers un domaine spécifique autorise uniquement les filtres pertinents pour ce domaine. 

Vous pouvez choisir :
- Tous les domaines : pour examiner toutes les données disponibles dans votre requête
- Points de terminaison : pour examiner les données de point de terminaison fournies par Microsoft Defender pour point de terminaison
- Applications et identités : pour examiner les données d’application et d’identité fournies par Microsoft Defender for Cloud Apps et Microsoft Defender pour Identity ; les utilisateurs familiarisés avec le [journal d’activité](/defender-cloud-apps/activity-filters) peuvent trouver les mêmes données ici
- Email et la collaboration - pour examiner les données des applications de messagerie et de collaboration comme SharePoint, OneDrive et d’autres; les utilisateurs familiarisés avec [l’Explorateur de menaces](/office-365-security/threat-explorer) peuvent trouver les mêmes données ici

## <a name="use-basic-filters"></a>Utiliser des filtres de base

Par défaut, la chasse guidée inclut quelques filtres de base pour vous aider à démarrer rapidement. 

![Capture d’écran du jeu de filtres de base du générateur de requêtes en mode guidé](../../media/guided-hunting/query-builder-basic-filters.png)



Lorsque vous choisissez une source de données, par exemple des **points** de terminaison, le générateur de requêtes affiche uniquement les groupes de filtres applicables. Vous pouvez ensuite choisir un filtre qui vous intéresse en sélectionnant ce groupe de filtres, par exemple **EventType**, et en sélectionnant le filtre de votre choix.

![Capture d’écran du jeu de filtres de base du générateur de requêtes en mode guidé](../../media/guided-hunting/query-builder-query-basic-filter.png)



Une fois la requête prête, sélectionnez le bouton **Exécuter la requête** en bleu. Si le bouton est grisé, cela signifie que la requête doit être renseignée ou modifiée. 

>[!NOTE]
> La vue de filtre de base utilise uniquement l’opérateur **AND** , ce qui signifie que l’exécution de la requête génère des résultats pour lesquels tous les filtres définis sont vrais. 


## <a name="load-sample-queries"></a>Charger des exemples de requêtes

Un autre moyen rapide de se familiariser avec la chasse guidée consiste à charger des exemples de requêtes à l’aide du menu déroulant **Charger les exemples de requêtes** . 
![Capture d’écran de la liste des exemples de requêtes de chargement du générateur de requêtes en mode guidé](../../media/guided-hunting/load-sample-queries.png)

>[!NOTE] 
> La sélection d’un exemple de requête remplace la requête existante. 

Une fois l’exemple de requête chargé, sélectionnez **Exécuter la requête**.

![Capture d’écran de la requête chargée du générateur de requêtes en mode guidé](../../media/guided-hunting/load-sample-queries-1.png)

Si vous avez déjà sélectionné un domaine, la liste des exemples de requêtes disponibles change en conséquence.

![Capture d’écran de la liste restreinte du générateur de requêtes en mode guidé](../../media/guided-hunting/load-sample-queries-2.png)

Pour restaurer la liste complète des exemples de requêtes, sélectionnez **Tous les domaines** , puis **rouvrez Les exemples de requêtes de chargement**.

Si l’exemple de requête chargé utilise des filtres en dehors du jeu de filtres de base, le bouton bascule est grisé. Pour revenir au jeu de filtres de base, sélectionnez **Effacer tout** , puis **basculez Tous les filtres**. 


## <a name="use-more-filters"></a>Utiliser d’autres filtres

Pour afficher plus de groupes de filtres et de conditions, sélectionnez **Basculer pour afficher d’autres filtres et conditions**.

![Capture d’écran du bouton bascule plus de filtres du générateur de requêtes en mode guidé](../../media/guided-hunting/query-builder-view-in-endpoints.png)

Lorsque le bouton bascule **Tous les filtres** est actif, vous pouvez désormais utiliser la plage complète de filtres et de conditions en mode guidé.

![Capture d’écran du générateur de requêtes en mode guidé tous les filtres actifs](../../media/guided-hunting/query-builder-all-filters.png)




### <a name="create-conditions"></a>Créer des conditions

Pour spécifier un jeu de données à utiliser dans la requête, **sélectionnez Sélectionner un filtre**. Explorez les différentes sections de filtre pour trouver ce qui est disponible pour vous.
 
![Capture d’écran montrant différents filtres que vous pouvez utiliser](../../media/guided-hunting/query-builder-filters.png)

Tapez les titres de la section dans la zone de recherche en haut de la liste pour rechercher le filtre. Les sections se terminant par *des informations* contiennent des filtres qui fournissent des informations sur les différents composants que vous pouvez examiner et filtrent les états des entités. Les sections se terminant par *des événements* contiennent des filtres qui vous permettent de rechercher tout événement surveillé sur l’entité. Par exemple, pour rechercher des activités impliquant certains appareils, vous pouvez utiliser les filtres sous la section **Événements de l’appareil** .

>[!NOTE]
> Le choix d’un filtre qui ne figure pas dans la liste de filtres de base désactive ou grise le bouton bascule pour revenir à la vue de filtres de base. Pour réinitialiser la requête ou supprimer les filtres existants dans la requête active, sélectionnez **Effacer tout**. Cela réactive également la liste des filtres de base.


Ensuite, définissez la condition appropriée pour filtrer davantage les données en les sélectionnant dans le deuxième menu déroulant et en fournissant des entrées dans le troisième menu déroulant si nécessaire :

![Capture d’écran montrant différentes conditions que vous pouvez utiliser](../../media/guided-hunting/query-builder-operators-equals.png)

Vous pouvez ajouter d’autres conditions à votre requête à l’aide des conditions **AND** et **OR** . AND retourne des résultats qui remplissent toutes les conditions de la requête, tandis que OR retourne des résultats qui remplissent l’une des conditions de la requête.  

![Capture d’écran montrant les opérateurs AND OR](../../media/guided-hunting/query-builder-operators.png)

L’affinement de votre requête vous permet de passer automatiquement au crible les enregistrements volumineux pour générer une liste de résultats déjà ciblés pour votre besoin spécifique de repérage des menaces.

Pour savoir quels types de données sont pris en charge et d’autres fonctionnalités de mode guidé pour vous aider à affiner votre requête, lisez [Affiner votre requête en mode guidé](advanced-hunting-query-builder-details.md).

## <a name="try-sample-query-walk-throughs"></a>Essayer des exemples de procédures de requête

Une autre façon de se familiariser avec la chasse guidée consiste à charger des exemples de requêtes précréés en mode guidé. 

Dans la section **Prise en main** de la page de chasse, nous avons fourni trois exemples de requêtes guidées que vous pouvez charger. Les exemples de requête contiennent certains des filtres et entrées les plus courants dont vous avez généralement besoin dans votre chasse. Le chargement de l’un des trois exemples de requêtes ouvre une visite guidée de la façon dont vous allez construire l’entrée à l’aide du mode guidé.

![Capture d’écran des procédures pas à pas du générateur de requêtes en mode guidé](../../media/guided-hunting/load-examples.png)

Suivez les instructions des bulles d’enseignement bleues pour construire votre requête. Sélectionnez **Exécuter la requête**.

## <a name="try-some-queries"></a>Essayer des requêtes

### <a name="hunt-for-successful-connections-to-specific-ip"></a>Rechercher des connexions réussies à une adresse IP spécifique
Pour rechercher des communications réseau réussies vers une adresse IP spécifique, commencez à taper « ip » pour obtenir les filtres suggérés :

![Capture d’écran du générateur de requêtes en mode guidé pour rechercher les connexions réussies à un premier filtre IP spécifique](../../media/guided-hunting/query-builder-hunt-ip.png)

Pour rechercher des événements impliquant une adresse IP spécifique où l’adresse IP est la destination de la communication, sélectionnez `DestinationIPAddress` sous la section Événements d’adresse IP. Sélectionnez ensuite l’opérateur **Equals** . Tapez l’adresse IP dans le troisième menu déroulant, puis **appuyez sur Entrée** :

![Capture d’écran du générateur de requêtes en mode guidé à la recherche de connexions réussies à une adresse IP spécifique](../../media/guided-hunting/query-builder-hunt-ip-2.png)

Ensuite, pour ajouter une deuxième condition qui recherche les événements de communication réseau réussis, recherchez le filtre d’un type d’événement spécifique :

![Capture d’écran du générateur de requêtes en mode guidé pour rechercher les connexions réussies à une adresse IP spécifique, deuxième condition](../../media/guided-hunting/query-builder-hunt-ip-3.png)

Le filtre **EventType** recherche les différents types d’événements enregistrés. Il est équivalent à la colonne **ActionType** qui existe dans la plupart des tables dans la chasse avancée. Sélectionnez-le pour choisir un ou plusieurs types d’événements à filtrer. Pour rechercher les événements de communication réseau réussis, développez la section **DeviceNetworkEvents** , puis choisissez `ConnectionSuccess`:

![Capture d’écran du générateur de requêtes en mode guidé pour rechercher les connexions réussies à une troisième condition IP spécifique](../../media/guided-hunting/query-builder-hunt-ip-4.png)

Enfin, sélectionnez **Exécuter la requête** pour rechercher toutes les communications réseau réussies vers l’adresse IP 52.168.117.170 :

![Capture d’écran du générateur de requêtes en mode guidé à la recherche de connexions réussies à une vue de résultats IP spécifique](../../media/guided-hunting/query-builder-hunt-ip-5.png)

### <a name="hunt-for-high-confidence-phish-or-spam-emails-delivered-to-inbox"></a>Rechercher les e-mails de hameçonnage ou de courrier indésirable à haut niveau de confiance remis à la boîte de réception 

Pour rechercher tous les e-mails de hameçonnage et de courrier indésirable à haut niveau de confiance qui ont été remis au dossier de boîte de réception au moment de la remise, commencez par sélectionner **ConfidenceLevel** sous Email Événements, sélectionnez **Valeurs égales** et choisissez **Haute** sous **Phish** et **Spam** dans la liste fermée suggérée qui prend en charge la sélection multiple :

![Capture d’écran du générateur de requêtes en mode guidé pour chasser les e-mails de hameçonnage ou de courrier indésirable à haut niveau de confiance remis à la boîte de réception, première condition](../../media/guided-hunting/hunt-phishing-1.png)

Ensuite, ajoutez une autre condition, en spécifiant cette fois le dossier ou **DeliveryLocation, boîte de réception/dossier**. 

![Capture d’écran du générateur de requêtes en mode guidé pour chasser le hameçonnage à haut niveau de confiance ou les courriers indésirables remis à la boîte de réception, deuxième condition](../../media/guided-hunting/hunt-phishing-2.png)




## <a name="see-also"></a>Voir aussi

- [Affiner votre requête en mode guidé](advanced-hunting-query-builder-details.md)
- [Utiliser les résultats de la requête en mode guidé](advanced-hunting-query-builder-results.md)
 - [Comprendre le schéma](advanced-hunting-schema-tables.md)
