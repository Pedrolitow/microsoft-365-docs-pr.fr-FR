---
title: Afficher l’activité d’audit des consignataires
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
description: Utilisez l’outil Advanced eDiscovery gestion des dépositaires pour accéder facilement à l’activité des dépositaires dans votre cas et y effectuer des recherches.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: f9e96d0b5dd3bf42dbba56a6e1be91014485ce98
ms.sourcegitcommit: 51a9f34796535309b8ca8b52da92da0a3621327b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "45024764"
---
# <a name="view-custodian-audit-activity"></a>Afficher l’activité d’audit des consignataires

Vous avez besoin de déterminer si un utilisateur a consulté un document spécifique ou supprimé définitivement un élément de sa boîte aux lettres ? Advanced eDiscovery est désormais intégré à l’outil de recherche de journal d’audit existant dans le Centre de sécurité & conformité. À l’aide de cette expérience incorporée, vous pouvez utiliser l’outil de gestion des dépositaires Advanced eDiscovery pour faciliter votre examen en accédant facilement à l’activité des dépositaires dans votre cas et en recherchant celui-ci.

## <a name="get-permissions"></a>Obtenir des autorisations

Vous devez avoir le rôle Journaux d’audit en affichage seul ou Journaux d’audit dans Exchange Online pour pouvoir effectuer des recherches dans le journal d’audit. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page Autorisations dans le Centre d’administration Exchange. Pour permettre à un utilisateur d’effectuer des recherches dans le journal d’audit Advanced eDiscovery avec le niveau minimal de privilèges, vous pouvez créer un groupe de rôles personnalisé dans Exchange Online, ajouter le rôle Journaux d’audit en affichage seul ou Journaux d’audit, puis ajouter l’utilisateur en tant que membre du nouveau groupe de rôles. Pour plus d’informations, voir Gérer les groupes de rôles dans Exchange Online.

> [!IMPORTANT]
> Si vous attribuez à un utilisateur le rôle Journaux d’audit View-Only ou Journaux d’audit dans la page Autorisations du Centre de sécurité & conformité, il ne pourra pas effectuer de recherche dans le journal d’audit. Vous devez affecter les autorisations dans Exchange Online. En effet, la cmdlet sous-jacente utilisée pour les recherches dans le journal d’audit est une cmdlet Exchange Online.

## <a name="step-1-search-the-audit-log-for-activities-performed-by-a-custodian"></a>Étape 1 : rechercher dans le journal d’audit les activités effectuées par un dépositaire

1. Go to **eDiscovery > Advanced eDiscovery** and open the case.
  
2. Cliquez sur **l’onglet Sources.**
  
3. Dans la page **Des dépositaires,** sélectionnez un dépositaire dans la liste, puis cliquez sur **Afficher** l’activité des dépositaires dans la page de flyout.

    La page de recherche activités du dépositaire s’affiche. Notez que le dépositaire que vous avez  sélectionné à l’étape précédente s’affiche dans la zone de la zone de présentation du dépositaire. Vous pouvez sélectionner différents dépositaires dans la zone de drop-down, mais vous pouvez uniquement rechercher des activités pour un dépositaire à la fois.

    ![Page de recherche activités du consignataire](../media/AeDCustodianActivities1.png)
   
4. Configurez les critères de recherche suivants : 
      
   1. **Activités :** cliquez sur la liste liste de listes pour afficher les activités que vous pouvez rechercher. Une fois la recherche terminée, seuls les enregistrements d’audit correspondant aux activités sélectionnées apparaissent. La sélection **Afficher les résultats pour toutes** les activités affiche les résultats de toutes les activités effectuées par le dépositaire qui correspondent aux autres critères de recherche.

      ![Liste des activités](../media/CustodianActivityAudit.PNG)
      
   1. **Date de début et date de fin** : sélectionnez une plage de dates et d’heures pour afficher les événements qui se sont produits au cours de cette période. Les sept derniers jours sont sélectionnés par défaut. Les date et heure sont présentées au format UTC (temps universel coordonné). La plage de dates maximale que vous pouvez spécifier est une année.
      
   1. **Dépositaires** : cliquez dans cette zone, puis sélectionnez un dépositaire spécifique pour afficher les résultats de la recherche. Les enregistrements d’audit pour l’activité sélectionnée effectuée par les utilisateurs que vous sélectionnez dans cette zone sont affichés dans la liste des résultats.
      
5. Clic  ![Bouton Rechercher](../media/SearchButton.PNG)  pour exécuter la recherche à l’aide de vos critères de recherche. Les résultats de la recherche sont chargés et, après quelques instants, ils sont affichés sous Résultats sur la page de recherche Activités des dépositaires. 

## <a name="step-2-view-the-audit-log-search-results"></a>Étape 2 : Afficher les résultats de recherche du journal d’audit

Les résultats d’une recherche dans le journal d’audit sont affichés sous Résultats dans la page journal d’audit du dépositaire. Un maximum de 5 000 événements (les plus récents) sont affichés par incréments de 150 événements. Pour afficher davantage d’événements, vous pouvez utiliser la barre de défilement du volet Résultats ou appuyer sur Maj+Fin afin d’afficher les 150 événements suivants.

Les résultats contiennent les informations suivantes sur chaque événement renvoyé par la recherche.
- **Date :** Date et heure (au format UTC) auxquelles l’événement s’est produit.

- **Adresse IP :** Adresse IP de l’appareil utilisé lors de l’enregistrement de l’activité. L’adresse IP apparaît au format d’adresse IPv4 ou IPv6.

- **Utilisateur :** Utilisateur (ou compte de service) qui a effectué l’action ayant déclenché l’événement.

- **Activité :** Activité effectuée par l’utilisateur. Cette valeur correspond aux activités que vous avez sélectionnées dans la liste déroulante Activités. Pour un événement figurant dans le journal d’audit de l’administrateur Exchange, la valeur dans cette colonne est une cmdlet Exchange.

- **Élément :** Objet qui a été créé ou modifié suite à l’activité correspondante. Par exemple, fichier consulté ou modifié, ou compte d’utilisateur mis à jour. Certaines activités n’ont pas de valeur dans cette colonne.

- **Détails** : Détails supplémentaires sur une activité. Là encore, toutes les activités n’ont pas de valeur.

## <a name="step-3-filter-the-search-results"></a>Étape 3 : filtrer les résultats de la recherche

Vous pouvez également filtrer les résultats d’une recherche dans le journal d’audit. Cela peut vous aider à filtrer rapidement les résultats d’un utilisateur ou d’une activité spécifique. 

Pour filtrer les résultats :

 1. Créez et exécutez une recherche dans le journal d’audit.
  
2. Lorsque les résultats sont affichés, cliquez sur **Filtrer les résultats**.
 
3. Les zones de mot clé apparaissent sous chaque en-tête de colonne.
  
4. Cliquez sur une des zones sous un en-tête de colonne et tapez un mot ou une expression, en fonction de la colonne qui fait l’objet du filtrage. Les résultats sont réajustés dynamiquement pour afficher les événements qui correspondent à votre filtre.
  
5. Pour effacer un filtre, cliquez sur **le X** dans la zone de filtre ou cliquez simplement sur **Masquer le filtrage.**

## <a name="export-the-search-results-to-a-file"></a>Exporter les résultats de la recherche dans un fichier

Vous pouvez exporter les résultats d’une recherche dans le journal d’audit vers un fichier de valeurs séparées par des virgules (CSV) sur votre ordinateur local. Vous pouvez ouvrir ce fichier dans Microsoft Excel et utiliser des fonctionnalités telles que la recherche, le tri, le filtrage et le fractionnement d’une colonne unique (qui contient des cellules à valeurs multiples) en plusieurs colonnes.

1. Effectuez une recherche dans le journal d’audit, puis modifiez les critères de recherche jusqu’à obtenir les résultats souhaités.
  
2. Cliquez sur Exporter les résultats, puis sélectionnez l’une des options suivantes :

    - **Enregistrez les résultats chargés :** Choisissez cette option pour exporter uniquement les  entrées qui sont affichées sous Résultats sur la page de recherche du journal d’audit **du** dépositaire. Le fichier .csv téléchargé contient les mêmes colonnes (et données) que celles affichées sur la page (Date, Utilisateur, Activité, Élément et Détails). Une colonne supplémentaire (intitulée **Plus)** est incluse dans le fichier CSV qui contient plus d’informations à partir de l’entrée du journal d’audit. Comme vous exportez les mêmes résultats que ceux chargés (et visibles) sur la page Recherche dans le journal d’audit, 5 000 entrées au maximum sont exportées.
        
    - **Téléchargez tous les résultats :** Choisissez cette option pour exporter toutes les entrées du journal d’audit qui répondent aux critères de recherche. Pour un grand nombre de résultats de recherche, choisissez cette option pour télécharger toutes les entrées du journal d’audit en plus des 5 000 résultats qui peuvent être affichés dans la page de recherche du journal **d’audit** du dépositaire. Cette option télécharge les données brutes du journal d’audit dans un fichier CSV et contient des informations supplémentaires à partir de l’entrée du journal d’audit dans une colonne nommée AuditData. Le téléchargement du fichier peut prendre plus de temps si vous choisissez cette option d’exportation, car le fichier peut-être plus volumineux que celui téléchargé à l’aide de l’autre option.
    
      > [!IMPORTANT]
      > Vous pouvez télécharger un maximum de 50 000 entrées dans un fichier .csv à partir d’une seule recherche dans le journal d’audit. Si 50 000 résultats sont téléchargés dans le fichier .csv, vous pouvez partir du principe que plus de 50 000 événements remplissent les critères de recherche. Pour exporter davantage de résultats, essayez d’utiliser une plage de dates pour réduire le nombre d’entrées du journal d’audit. Vous devrez peut-être effectuer plusieurs recherches avec des plages de dates plus réduites pour exporter plus de 50 000 entrées.
        

3. Après avoir sélectionné une option d’exportation, un message s’affiche en bas de la fenêtre qui vous invite à ouvrir le fichier CSV, à l’enregistrer dans le dossier Téléchargements ou à l’enregistrer dans un dossier spécifique

Pour plus d’informations sur l’affichage, le filtrage ou l’exportation des résultats de recherche dans le journal d’audit, voir Rechercher dans le journal d’audit dans le Centre de sécurité [& conformité.](search-the-audit-log-in-security-and-compliance.md)
