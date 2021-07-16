---
title: Isolation du client dans Microsoft 365 Search
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Dans cet article, trouvez une explication du fonctionnement de l’isolation des clients pour séparer les données client dans Microsoft 365 recherche.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3416afdeceaa7000b516ec89b4a2a1e59d8708d0
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "53464083"
---
# <a name="tenant-isolation-in-microsoft-365-search"></a>Isolation du client dans Microsoft 365 Search

SharePoint La recherche en ligne utilise un modèle de séparation des clients qui équilibre l’efficacité des structures de données partagées avec la protection contre la fuite d’informations entre les clients. Avec ce modèle, nous empêchons les fonctionnalités de recherche de :

- Renvoi des résultats de requête qui contiennent des documents provenant d’autres locataires
- Exposition d’informations suffisantes dans les résultats de requête qu’un utilisateur compétent peut déduire des informations sur d’autres locataires
- Affichage du schéma ou des paramètres d’un autre client
- La combinaison des informations de traitement de l’analyse entre les clients ou le magasin entraîne la mauvaise relation client
- Utilisation d’entrées de dictionnaire d’un autre client

Pour chaque type de données client, nous utilisons une ou plusieurs couches de protection dans le code pour éviter toute fuite accidentelle d’informations. Les données les plus critiques disposent du plus grand nombre de couches de protection pour s’assurer qu’un seul défaut ne se produit pas de fuite d’informations réelle ou perçue.

## <a name="tenant-separation-for-the-search-index"></a>Séparation des locataires pour l’index de recherche

L’index de recherche est stocké sur disque sur les serveurs hébergeant les composants d’index et les clients partagent les fichiers d’index. Les documents indexés d’un client sont visibles uniquement pour les requêtes de ce client. Trois mécanismes indépendants empêchent la fuite d’informations :

- Filtrage des ID de client
- Préfixe de terme d’ID de client
- Vérifications de la contrôle d’accès

Les trois mécanismes doivent échouer pour que la recherche retourne des documents au mauvais client.

## <a name="tenant-id-filtering-and-tenant-id-term-prefixing"></a>Filtrage des ID de client et préfixe des termes de l’ID de locataire

La recherche préfixe chaque terme indexé dans l’index de texte intégral avec l’ID client. Par exemple, lorsque le terme «*foo*» est indexé pour un client dont l’ID est «*123*», l’entrée dans l’index de texte intégral est «*123foo.*»

Chaque requête est convertie pour inclure l’ID de client à l’aide d’un processus appelé filtrage d’ID de client. Par exemple, la requête « foo » est *convertie* en « <*guid*>. *foo* AND *tenantID*:<*guid*> », où <*guid*> représente le client qui exécute la requête. Cette conversion de requête se produit dans chaque nœud d’index et ni la requête ni le traitement du contenu ne peuvent l’influencer. Étant donné que l’ID de client est ajouté à chaque requête, la fréquence d’un terme dans d’autres locataires ne peut pas être déduite en regardant le meilleur classement des correspondances dans un client.

Le préfixe de terme de l’ID client se produit uniquement dans l’index de texte intégral. Les recherches sur le terrain, telles que «*title:foo*», sont dans un index de recherche synthétique dans lequel les termes ne sont pas précédés de l’ID de locataire. Au lieu de cela, les recherches dans les champs sont précédées du nom du champ. Par exemple, la requête «*title:foo*» est convertie en «*fields.title:foo AND fields.tenantID*:<*guid*> ». Étant donné que la fréquence d’un terme n’influence pas le classement des occurrences dans l’index de recherche synthétique, il n’est pas nécessaire de séparer le client par préfixe de termes. Pour une recherche sur le champ telle que «*title:foo*», la séparation du contenu du client dépend du filtrage de l’ID client par conversion de requête.

## <a name="document-access-control-list-checks"></a>Vérifications des listes de contrôle d’accès aux documents

La recherche contrôle l’accès aux documents via des ACA enregistrées dans l’index de recherche. Chaque élément est indexé avec un ensemble de termes dans un champ ACL spécial. Le champ ACL contient un terme par groupe ou utilisateur qui peut afficher le document. Chaque requête est complétée par une liste de termes ACE (Access Control Entry), un pour chaque groupe auquel appartient l’utilisateur authentifié.

Par exemple, une requête telle que « <*guid*>. *foo AND tenantID*:<*guid*> » devient : « <*guid*>. *foo AND tenantID*:<*guid* >  *AND* (*docACL:* < *ace1* >  *OR docACL*:<*ace2* >  *OR docACL*:<*ace3* >  *...*) »

Étant donné que les identificateurs d’utilisateurs et de groupes et donc les entrées de contrôle d’accès sont uniques, cela offre un niveau de sécurité supplémentaire entre les clients pour les documents qui ne sont visibles que par certains utilisateurs. Il en va de même pour l’ace spéciale « Tout le monde sauf les utilisateurs externes » qui accorde l’accès aux utilisateurs réguliers dans le client. Toutefois, étant donné que les ace pour « Tout le monde » sont identiques pour tous les locataires, la séparation des locataires pour les documents publics dépend du filtrage des ID de client. Les aces de refus sont également pris en charge. L’augmentation de requête ajoute une clause qui supprime un document du résultat lorsqu’il existe une correspondance avec une ace de refus.

Dans Exchange Online recherche, l’index est partitioné sur l’ID de boîte aux lettres des boîtes aux lettres d’un utilisateur individuel au lieu de l’ID de locataire (ID d’abonnement) comme dans SharePoint Online. Le mécanisme de partitionnement est identique à SharePoint Online, mais il n’existe aucun filtrage ACL.
