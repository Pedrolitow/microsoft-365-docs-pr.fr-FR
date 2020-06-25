---
title: Vue d’ensemble des rétentions basées sur des événements
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-may2020
- seo-marvel-jun2020
description: Dans une solution de gestion des enregistrements, vous pouvez généralement configurer une étiquette de rétention pour démarrer la période de rétention sur la base d’un événement que vous identifiez.
ms.openlocfilehash: 1e716cc886e8378308054d4f2eedf961045f4486
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44817803"
---
# <a name="overview-of-event-driven-retention"></a>Vue d’ensemble des rétentions basées sur des événements

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

When you retain content, the retention period is often based on the age of the content - for example, you might retain documents for seven years after they're created and then delete them. But with retention labels in Microsoft 365, you can also base a retention period on when a specific type of event occurs. The event triggers the start of the retention period, and all content with a retention label applied for that type of event get the label's retention actions enforced on them.
  
Par exemple, vous pouvez utiliser des étiquettes avec des rétentions basées sur des événements pour les éléments suivants :
  
- **Employees leaving the organization** Suppose that employee records must be retained for 10 years from the time an employee leaves the organization. After 10 years elapse, all documents related to the hiring, performance, and termination of that employee need to be disposed. The event that triggers the 10-year retention period is the employee leaving the organization. 
    
- **Contract expiration** Suppose that all records related to contracts need to be retained for five years from the time the contract expires. The event that triggers the five-year retention period is the expiration of the contract. 
    
- **Product lifetime** Your organization might have retention requirements related to the last manufacturing date of products for content such as technical specifications. In this case, the last manufacturing date is the event that triggers the retention period. 
    
Event-driven retention is typically used as part of a records-management process. This means that:
  
- Labels based on events also usually classify content as a record. For more information, see [Using Content Search to find all content with a specific retention label applied to it](labels.md#using-content-search-to-find-all-content-with-a-specific-retention-label-applied-to-it).
    
- Un document qui a été déclaré comme enregistrement, mais dont l’événement déclencheur ne s’est pas encore produit, est conservé indéfiniment (les enregistrements ne peuvent pas être supprimés définitivement) jusqu’à ce qu’un événement déclenche la période de rétention du document en question.
    
- Retention labels based on events usually trigger a disposition review at the end of the retention period, so that a records manager can manually review and dispose the content. For more information, see [Disposition of content](disposition.md).
    
Les étiquettes basées sur un événement possèdent les mêmes fonctionnalités que les étiquettes de rétention dans Microsoft 365. Pour plus d’informations, voir [En savoir plus sur les étiquettes de rétention](labels.md).

## <a name="understanding-the-relationship-between-event-types-labels-events-and-asset-ids"></a>Compréhension de la relation entre les types d’événements, les étiquettes, les événements et les ID d’élément

Pour utiliser avec succès la rétention basée sur les événements, il est important de comprendre la relation entre les types d’événement, les étiquettes de rétention, les événements et les ID d’éléments, comme illustré dans les diagrammes et l’explication qui suit : 
  
![Diagramme illustrant le type d’événement, les étiquettes, les événements et les ID d’élément](../media/a5141a6b-61ca-4a60-9ab0-24e6bb45bbdb.png)
  
![Diagramme illustrant le type d’événement, les étiquettes, les événements et les ID d’élément](../media/ce89a91f-49aa-4b5a-933c-ac3a13dccd5d.png)
  
1. Vous créez des étiquettes de rétention pour différents types de contenu et vous les associez à un type d’événement. Par exemple, les étiquettes pour différents types de fichiers et d’enregistrements de produit sont associées à un type d’événement nommé Durée de vie des produits, car ces enregistrements doivent être conservés pendant 10 ans à compter de la fin de vie du produit.
    
2. Les utilisateurs (en général les gestionnaires des enregistrements) appliquent ces étiquettes de rétention au contenu et (pour les documents SharePoint et OneDrive) entrent un ID d’élément pour chaque élément. Dans cet exemple, l’ID d’actif est un nom de produit ou un code utilisé par l’organisation. Par conséquent, les enregistrements de chaque produit se voient attribuer une étiquette de rétention, et chaque enregistrement possède une propriété contenant un ID d’actif. Le diagramme représente **l’ensemble du contenu** de tous les enregistrements des produits d’une organisation, et chaque élément porte l’ID d’élément du produit auquel appartient l’enregistrement. 
    
3. Product Lifetime is the event type; a specific product reaching end of life is an event. When an event of that event type occurs - in this case, when a product reaches its end of life - you create an event that specifies:
    
  - Un ID d’élément (pour les documents SharePoint et OneDrive).
    
  - Keywords (for Exchange items). In this example, the organization uses a product code in messages containing product records, so the keyword for Exchange items is the same as the asset ID for SharePoint and OneDrive documents.
    
  - The date when the event occurred. This date is used as the start of the retention period. This date can be the current, a past, or a future date.
    
4. Une fois un événement créé, la date correspondante est synchronisée avec tout le contenu portant l’étiquette de rétention de ce type d’événement et contenant l’ID d’élément ou le mot clé spécifié. Comme pour toute étiquette de rétention, cette synchronisation peut prendre jusqu’à 7 jours. Dans le diagramme précédent, la période de rétention de tous les éléments encerclés en rouge est déclenchée par cet événement. En d’autres termes, lorsque ce produit atteint sa fin de vie, cet événement déclenche la période de rétention pour les enregistrements de ce produit.
    
Il est important de comprendre que si vous ne spécifiez pas d’ID d’élément ou de mot clé pour un événement, **tout le contenu** portant une étiquette de ce type d’événement verra sa période de rétention déclenchée par l’événement. Cela signifie que, dans le diagramme précédent, tout le contenu commencera à être conservé. Ce n’est peut-être pas ce que vous voulez faire. 
  
Enfin, rappelez-vous que chaque étiquette de rétention possède ses propres paramètres de rétention. Dans cet exemple, ils indiquent tous 10 ans, mais un événement peut très bien déclencher des étiquettes de rétention dont chacune possède sa propre période de rétention.
  
## <a name="how-to-set-up-event-driven-retention"></a>Configuration des rétentions basées sur des événements

Flux de travail général pour la rétention basée sur un événement :
  
![Diagramme du flux de travail de la configuration des rétentions basées sur des événements](../media/event-based-retention-process.png)
  
> [!TIP]
> Consultez [Gérer le cycle de vie des documents SharePoint avec des étiquettes de rétention](auto-apply-retention-labels-scenario.md) pour un scénario détaillé sur l’utilisation de propriétés gérées dans SharePoint afin d'appliquer automatiquement des étiquettes de rétention et implémenter la rétention basée sur les événements.

### <a name="step-1-create-a-label-whose-retention-period-is-based-on-an-event"></a>Étape 1 : créer une étiquette dont la période de rétention est basée sur des événements

Dans le Centre de conformité Microsoft 365, dans le volet de navigation gauche, sélectionnez **Gouvernance des informations** > **Étiquettes** > **Créer une étiquette**. Si **Gouvernance des informations** ne s’affiche pas dans le volet de navigation, faites défiler la liste vers le bas, puis sélectionnez **Afficher tout**.
  
When you create the label, turn on retention, and then choose the option shown below to retain or delete the content based on an event. This means that the retention settings won't go into effect until Step 5, when you create an event on the **Events** page. 
  
Notez que la rétention basée sur un événement est généralement utilisée pour le contenu classé comme enregistrement. C’est pourquoi, lorsque vous créez des étiquettes de rétention en fonction d’un événement, vous choisissez généralement l’option **Utiliser une étiquette pour classer le contenu comme un « enregistrement »**.
  
Notez également que les rétentions basées sur des événements requièrent des paramètres de rétention qui :
  
- Conservent le contenu.
    
- suppriment automatiquement le contenu ou déclenchent une révision de destruction à la fin de la période de rétention.
    
![Option pour baser une étiquette sur un événement](../media/a4902281-5196-4194-9737-f30231d95861.png)
  
### <a name="step-2-choose-an-event-type-for-that-label"></a>Étape 2 : choisir un type d’événement pour cette étiquette

Dans les paramètres d’étiquette, après avoir choisi l’option de baser l’étiquette sur **un événement**, l’option **Choisir un type d’événement** apparaît. Un type d’événement est simplement une description générale d’un événement auquel vous voulez associer une étiquette.
  
Par exemple, si vous créez un type d’événement nommé Durée de vie des produits, vous allez créer des étiquettes de rétention basées sur un événement avec des noms qui décrivent les types de contenu auxquels vous souhaitez appliquer des étiquettes. Par exemple, « Fichiers de développement des produits » ou « Enregistrements de la décision commerciale des produits ».
  
Notez qu’une fois que vous sélectionnez un type d’événement et créez l’étiquette de rétention, le type d’événement ne peut pas être modifié.
  
![Options permettant de créer ou de sélectionner un type d’événement](../media/8b7afe79-72cb-462e-81d4-b5ddbe899dbc.png)
  
### <a name="step-3-publish-or-auto-apply-the-event-based-retention-labels"></a>Étape 3 : publier ou appliquer automatiquement les étiquettes de rétention basées sur les événements

Comme pour n’importe quelle étiquette de rétention, vous devez [publier ou appliquer automatiquement](create-retention-labels.md) une étiquette basée sur un événement, de sorte qu’elle soit appliquée au contenu de façon manuelle ou automatique.

> [!NOTE]
> Si vous sélectionnez une étiquette de rétention basée sur un événement à partir d’un onglet **Gestion des enregistrements** > **Plan de gestion des fichiers** ou **Gouvernance des données** > **Étiquettes**, le bouton **Appliquer automatiquement une étiquette** n’est pas disponible.
> 
> Au lieu de ce bouton, utilisez l’option **Appliquer automatiquement une étiquette** au-dessus de la liste des étiquettes ou des stratégies à partir de l’un des emplacements suivants :
> - Onglet **Gestion des enregistrements** > **Stratégies des étiquettes**
> - Onglet **Gouvernance des données** > **Étiquettes** ou **Stratégies des étiquettes**


![Options permettant de publier ou d’appliquer automatiquement une étiquette de rétention](..\media\compliance-information-governance-publish-labels.png)

### <a name="step-4-enter-an-asset-id"></a>Étape 4 : saisissez un ID d’élément

After an event-driven label is applied to content, you can enter an asset ID for each item. For example, your organization might use:
  
- Des codes de produit que vous pouvez utiliser pour conserver le contenu relatif à un produit spécifique.
    
- Des codes de projet que vous pouvez utiliser pour conserver le contenu relatif à un projet spécifique.
    
- ID d’employé à utiliser pour conserver uniquement le contenu d’une personne spécifique.
    
L’ID d’élément constitue simplement une autre propriété de document dans SharePoint et OneDrive Entreprise. Votre organisation utilise peut-être déjà d’autres ID et propriétés de document pour classer le contenu. Le cas échéant, vous pouvez également utiliser ces propriétés et valeurs lorsque vous créez un événement (voir l’étape 6 ci-après). L’essentiel est que votre organisation utilise une combinaison propriété:valeur dans les propriétés du document pour associer cet élément à un type d’événement.
  
![Zone de texte pour saisir un ID d’élément](../media/6d31628e-7162-4370-a8d7-de704aafa350.png)
  
### <a name="step-5-create-an-event"></a>Étape 5 : créer un événement

When a particular instance of that event type occurs - for example, a product reaches its end of life - go to the **Records management** > **Events** page in the Microsoft 365 compliance center and create an event. You need to manually trigger an event by creating it.
  
### <a name="step-6-choose-the-same-event-type-used-by-the-label-in-step-2"></a>Étape 6 : choisir le même type d’événement utilisé par l’étiquette à l’étape 2

Lorsque vous créez l’événement, choisissez le type d’événement utilisé par l’étiquette de rétention à l’étape 2 (par exemple, durée de vie du produit). La période de rétention sera déclenchée uniquement pour le contenu auquel sont appliquées des étiquettes de rétention de ce type d’événement.
  
![Option dans les paramètres d’événement permettant de choisir un type d’événement](../media/11663591-5628-419e-9537-61eb8f5c741f.png)
  
### <a name="step-7-enter-keywords-or-an-asset-id"></a>Étape 7 : saisir des mots clés ou un ID d’élément

Now you narrow the scope of the content by specifying asset IDs for SharePoint and OneDrive content or keywords for Exchange content. For asset IDs, retention will be enforced only on content with the specified property:value pair. If an asset ID is not entered, **all content** with labels of that event type get the same retention date applied to them. 
  
L’ID d’élément constitue simplement une autre propriété de document dans SharePoint et OneDrive Entreprise. Si vous utilisez la propriété ID d’élément, vous entrez ComplianceAssetID:\<value\> dans la zone réservée aux ID d’élément illustrée ci-dessous.
  
Your organization might have applied other properties and IDs to the documents related to this event type. For example, if you need to detect a specific product's records, the ID might be a combination of your custom property ProductID and the value "XYZ". In this case, you'd enter ProductID:XYZ in the box for asset IDs shown below.
  
For Exchange items, you can include keywords. You can refine your query by using search operators like AND, OR, and NOT. For more information on operators, see [Keyword queries and search conditions for Content Search](keyword-queries-and-search-conditions.md).
  
Enfin, sélectionnez la date à laquelle l’événement s’est produit. cette date est utilisée comme début de la période de rétention. Une fois que vous avez créé un événement, la date de l’événement est synchronisée avec tout le contenu avec une étiquette de rétention de ce type d’événement, de l’ID d’actif et des mots clés. Comme pour toute étiquette de rétention, cette synchronisation peut prendre jusqu’à 7 jours.
  
![Page Paramètres des événements](../media/40d3c9db-f624-49a5-b38a-d16bcce20231.png)
  
## <a name="use-content-search-to-find-all-content-with-a-specific-label-or-asset-id"></a>Utilisation de la recherche de contenu pour rechercher tout le contenu portant une étiquette ou un ID d’élément spécifique

Une fois que les étiquettes de rétention sont attribuées au contenu, vous pouvez utiliser la recherche de contenu pour rechercher tout le contenu classé avec une étiquette de rétention spécifique ou qui contient un ID d’élément spécifique.
  
Lorsque vous créez une recherche de contenu, procédez comme suit :
  
- Pour trouver tout le contenu portant une étiquette de rétention spécifique, sélectionnez la condition **Balise de conformité**, puis saisissez le nom d’étiquette en partie ou en intégralité et utilisez un caractère générique. 
    
- Pour trouver tout le contenu portant un ID d’élément spécifique, saisissez la propriété **ComplianceAssetID** et une valeur, telle que ComplianceAssetID:\<value\>. 
    
Si vous souhaitez en savoir plus, consultez la page [Requêtes par mots-clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).
  
## <a name="permissions"></a>Autorisations

To get access to the **Events** page, reviewers must be members of a role group with the **Disposition Management** role and the **View-Only Audit Logs** role. We recommend creating a new role group called Disposition Reviewers, adding these two roles to that role group, and then adding members to the role group. 
  
Pour obtenir plus d’informations, consultez l’article [Octroi de l’accès au Centre de sécurité &amp; conformité Office 365 aux utilisateurs](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
## <a name="automate-events-by-using-powershell"></a>Automatisation des événements à l’aide de PowerShell

In the admin center, you can only create events manually; it's not possible to automatically trigger an event when it occurs. However, you can use a Rest API to trigger events automatically; for more information, see [Automate event-based retention](automate-event-driven-retention.md).

Vous pouvez aussi utiliser un script PowerShell pour automatiser une rétention basée sur l’événement à partir de vos applications entreprise. Les cmdlets PowerShell disponibles pour les rétentions basées sur des événements :
  
- [Get-ComplianceRetentionEventType](https://go.microsoft.com/fwlink/?linkid=873002)
    
- [New-ComplianceRetentionEventType](https://go.microsoft.com/fwlink/?linkid=873004)
    
- [Remove-ComplianceRetentionEventType](https://go.microsoft.com/fwlink/?linkid=873005)
    
- [Set-ComplianceRetentionEventType](https://go.microsoft.com/fwlink/?linkid=873006)
    
- [Get-ComplianceRetentionEvent](https://go.microsoft.com/fwlink/?linkid=873001)
    
- [New-ComplianceRetentionEvent](https://go.microsoft.com/fwlink/?linkid=873003)
    

