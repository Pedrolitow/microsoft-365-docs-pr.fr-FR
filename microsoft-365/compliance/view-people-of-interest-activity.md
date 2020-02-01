---
title: Afficher l’activité d’audit des personnes concernées
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: ''
ms.openlocfilehash: eac58e10e97b639a296717210f7a9576abef5e35
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41597241"
---
# <a name="view-the-audit-activity-of-people-of-interest"></a>Afficher l’activité d’audit des personnes concernées

Vous avez besoin de déterminer si un utilisateur a consulté un document spécifique ou supprimé définitivement un élément de sa boîte aux lettres ? Les enquêtes de données (préversion) sont désormais intégrées à l’outil de recherche de journal d’audit existant dans le centre de sécurité & conformité. À l’aide de cette expérience intégrée, vous pouvez utiliser l’outil de gestion des données (préversion) personnes d’un outil de gestion des intérêts pour faciliter votre enquête en accédant facilement à l’activité des personnes intéressantes et en les recherchant dans votre enquête.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez avoir le rôle Journaux d’audit en affichage seul ou Journaux d’audit dans Exchange Online pour pouvoir effectuer des recherches dans le journal d’audit Office 365. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page Autorisations dans le Centre d’administration Exchange. Pour permettre à un utilisateur d’effectuer des recherches dans le journal d’audit des enquêtes de données (aperçu) avec le niveau minimal de privilèges, vous pouvez créer un groupe de rôles personnalisé dans Exchange Online, ajouter les journaux d’audit en affichage seul ou les journaux d’audit, puis ajouter l’utilisateur en tant que membre du nouveau groupe de rôles. oup. Pour plus d’informations, voir Gérer les groupes de rôles dans Exchange Online.

> [!IMPORTANT]
> Si vous attribuez à un utilisateur le rôle journaux d’audit en affichage seul ou journaux d’audit sur la page autorisations dans le centre de sécurité & conformité, il ne pourra pas effectuer de recherche dans le journal d’audit Office 365. Vous devez affecter les autorisations dans Exchange Online. En effet, la cmdlet sous-jacente utilisée pour les recherches dans le journal d’audit est une cmdlet Exchange Online.

## <a name="step-1-create-an-data-investigations-preview-audit-log-search"></a>Étape 1 : créer une recherche de journaux d’audit (aperçu)

   1. Sélectionnez une enquête existante dans le **Centre de sécurité & conformité > enquêtes de données (aperçu)**.
   
   2. Accédez à l’onglet **personnes d’intérêt** et sélectionnez une personne.
   
   3. Une fois que vous avez sélectionné une personne, cliquez sur **afficher l’activité** dans le panneau de détails.
   
   4. Configurez les critères de recherche suivants : 
      
      a. **Activités** : cliquez sur la liste déroulante pour afficher les activités que vous pouvez rechercher. Après l’exécution de la recherche, seuls les enregistrements d’audit des activités sélectionnées sont affichés. Sélectionnez **afficher les résultats pour toutes les activités** pour afficher les résultats de toutes les activités qui répondent aux autres critères de recherche.
      
      b. **Date de début et date de fin** : sélectionnez une date et une plage horaire pour afficher les événements qui se sont produits au cours de cette période. Les sept derniers jours sont sélectionnés par défaut. Les date et heure sont présentées au format UTC (temps universel coordonné). La plage de dates maximale que vous pouvez spécifier est d’un an.
      
      c. **Personnes concernées** : cliquez dans cette zone, puis sélectionnez un dépositaire spécifique pour lequel afficher les résultats de la recherche. Les enregistrements d’audit de l’activité sélectionnée effectuée par les utilisateurs que vous sélectionnez dans cette zone sont affichés dans la liste des résultats.
    
    1. Cliquez sur **Rechercher** pour effectuer la recherche à l’aide de vos critères de recherche.  Les résultats de la recherche sont chargés et après quelques instants, ils s’affichent sous résultats sur la page de recherche des personnes d’intérêt. 

## <a name="step-2-view-the-audit-log-search-results"></a>Étape 2 : afficher les résultats de la recherche du journal d’audit

Les résultats d’une recherche dans le journal d’audit sont affichés sous résultats dans la page du journal d’audit des personnes concernées. Un maximum de 5 000 (plus récent) événements sont affichés par incréments de 150 événements. Pour afficher davantage d’événements, vous pouvez utiliser la barre de défilement du volet Résultats ou appuyer sur Maj+Fin afin d’afficher les 150 événements suivants.

Les résultats contiennent les informations suivantes sur chaque événement renvoyé par la recherche.
- **Date :** Date et heure (au format UTC) auxquelles l’événement s’est produit.

- **Adresse IP :** Adresse IP de l’appareil utilisé lors de l’enregistrement de l’activité. L’adresse IP apparaît au format d’adresse IPv4 ou IPv6.

- **Utilisateur** : Utilisateur (ou compte de service) qui a effectué l’action ayant déclenché l’événement.

- **Activité :** Activité effectuée par l’utilisateur. Cette valeur correspond aux activités que vous avez sélectionnées dans la liste déroulante Activités. Pour un événement figurant dans le journal d’audit de l’administrateur Exchange, la valeur dans cette colonne est une cmdlet Exchange.

- **Élément :** Objet qui a été créé ou modifié suite à l’activité correspondante. Par exemple, fichier consulté ou modifié, ou compte d’utilisateur mis à jour. Certaines activités n’ont pas de valeur dans cette colonne.

- **Détail**: détails supplémentaires sur une activité. Une fois encore, toutes les activités n’auront pas de valeur.

## <a name="step-3-filter-the-search-results"></a>Étape 3 : filtrer les résultats de la recherche

Vous pouvez également filtrer les résultats d’une recherche dans le journal d’audit. Cela peut vous aider à filtrer rapidement les résultats d’une activité ou d’un utilisateur spécifique. 

Pour filtrer les résultats :

 1. Créez et exécutez une recherche de journal d’audit.
  
2. Lorsque les résultats sont affichés, cliquez sur **Filtrer les résultats**.
 
3. Les zones de mot clé apparaissent sous chaque en-tête de colonne.
  
4. Cliquez sur une des zones sous un en-tête de colonne et tapez un mot ou une expression, en fonction de la colonne qui fait l’objet du filtrage. Les résultats sont réajustés dynamiquement pour afficher les événements qui correspondent à votre filtre.
  
5. Pour effacer un filtre, cliquez sur **X** dans la zone filtre ou cliquez simplement sur **masquer le filtrage**.

## <a name="export-the-search-results-to-a-file"></a>Exporter les résultats de la recherche dans un fichier

Vous pouvez exporter les résultats d’une recherche de journal d’audit dans un fichier de valeurs séparées par des virgules (CSV) sur votre ordinateur local. Vous pouvez ouvrir ce fichier dans Microsoft Excel et utiliser des fonctionnalités telles que la recherche, le tri, le filtrage et le fractionnement d’une seule colonne (contenant des cellules à plusieurs valeurs) en plusieurs colonnes.

1. Effectuez une recherche dans le journal d’audit, puis modifiez les critères de recherche jusqu’à obtenir les résultats souhaités.
  
2. Cliquez sur Exporter les résultats, puis sélectionnez l’une des options suivantes :

    - **Enregistrer les résultats chargés :** Choisissez cette option pour exporter uniquement les entrées affichées sous **résultats** sur la page **de recherche du journal d’audit des personnes concernées** . Le fichier .csv téléchargé contient les mêmes colonnes (et données) que celles affichées sur la page (Date, Utilisateur, Activité, Élément et Détails). Une colonne supplémentaire (intitulée **More**) est incluse dans le fichier CSV qui contient plus d’informations à partir de l’entrée du journal d’audit. Comme vous exportez les mêmes résultats que ceux chargés (et visibles) sur la page Recherche dans le journal d’audit, 5 000 entrées au maximum sont exportées.
        
    - **Télécharger tous les résultats :** Choisissez cette option pour exporter toutes les entrées du journal d’audit Office 365 correspondant aux critères de recherche. Pour un grand ensemble de résultats de recherche, choisissez cette option pour télécharger toutes les entrées à partir du journal d’audit en plus des résultats 5 000 qui peuvent être affichés sur la page **de recherche des personnes concernées** . Cette option télécharge les données brutes à partir du journal d’audit vers un fichier CSV, et contient des informations supplémentaires provenant de l’entrée du journal d’audit dans une colonne nommée AuditData. Le téléchargement du fichier peut prendre plus de temps si vous choisissez cette option d’exportation, car le fichier peut-être plus volumineux que celui téléchargé à l’aide de l’autre option.
    
      > [!IMPORTANT]
      > Vous pouvez télécharger un maximum de 50 000 entrées dans un fichier .csv à partir d’une seule recherche dans le journal d’audit. Si 50 000 résultats sont téléchargés dans le fichier .csv, vous pouvez partir du principe que plus de 50 000 événements remplissent les critères de recherche. Pour exporter davantage de résultats, essayez d’utiliser une plage de dates pour réduire le nombre d’entrées du journal d’audit. Vous devrez peut-être effectuer plusieurs recherches avec des plages de dates plus réduites pour exporter plus de 50 000 entrées.
        

3. Une fois que vous avez sélectionné une option d’exportation, un message s’affiche en bas de la fenêtre qui vous invite à ouvrir le fichier CSV, à l’enregistrer dans le dossier téléchargements, ou à l’enregistrer dans un dossier spécifique.

Pour plus d’informations sur l’affichage, le filtrage ou l’exportation des résultats de la recherche du journal d’audit, consultez [la rubrique Search the Audit Log in the Office 365](search-the-audit-log-in-security-and-compliance.md).