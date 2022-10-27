---
title: Débuter la rétention lorsqu’un événement se produit
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- purview-compliance
- tier1
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-may2020
- seo-marvel-jun2020
description: Dans une solution de gestion des enregistrements, vous pouvez généralement configurer une étiquette de rétention pour démarrer la période de rétention sur la base d’un événement que vous identifiez.
ms.openlocfilehash: c4354e7e1d2e9f8367b01e57fa6d84dc32b5f978
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68735922"
---
# <a name="start-retention-when-an-event-occurs"></a>Débuter la rétention lorsqu’un événement se produit

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

When you retain content, the retention period is often based on the age of the content. For example, you might retain documents for seven years after they're created and then delete them. But when you configure [retention labels](retention.md#retention-labels), you can also base a retention period on when a specific type of event occurs. The event triggers the start of the retention period, and all content with a retention label applied for that type of event get the label's retention actions enforced on them.
  
Exemples d'utilisation de la rétention basée sur les événements :

- **Employees leaving the organization** Suppose that employee records must be retained for 10 years from the time an employee leaves the organization. After 10 years elapse, all documents related to the hiring, performance, and termination of that employee must be disposed. The event that triggers the 10-year retention period is the employee leaving the organization. 

- **Contract expiration** Suppose that all records related to contracts must be retained for five years from the time the contract expires. The event that triggers the five-year retention period is the expiration of the contract. 

- **Product lifetime** Your organization might have retention requirements related to the last manufacturing date of products for content such as technical specifications. In this case, the last manufacturing date is the event that triggers the retention period. 

La rétention basée sur les événements, parfois également appelée « rétention pilotée par les événements », est généralement utilisée avec les processus de gestion des enregistrements. En d'autres termes :

- Retention labels based on events also usually mark items as a record, as a part of a records management solution. For more information, see [Learn about records management](records-management.md).

- Un document qui a été déclaré comme un enregistrement, mais dont l'événement déclencheur n'a pas encore eu lieu, est conservé indéfiniment. Tant qu’un événement n’a pas déclenché la période de rétention de ce document qui expire par la suite, les enregistrements ne peuvent pas être supprimés définitivement.

- Les étiquettes de rétention basées sur des événements déclenchent souvent une révision de destruction à la fin de la période de rétention, afin qu’un gestionnaire d’enregistrements puisse examiner et supprimer manuellement le contenu. Si vous souhaitez en savoir plus, consultez la page [Destruction de contenu](disposition.md).

Une étiquette de rétention basée sur un événement a les mêmes fonctionnalités que n’importe quelle étiquette de rétention dans Microsoft Purview. Pour plus d’informations, voir [En savoir plus sur les stratégies et les étiquettes de rétention](retention.md).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="understanding-the-relationship-between-event-types-labels-events-and-asset-ids"></a>Compréhension de la relation entre les types d’événements, les étiquettes, les événements et les ID d’élément

Pour utiliser avec succès la rétention basée sur les événements, il est important de comprendre la relation entre les types d'événements, les étiquettes de rétention, les événements et les identifications d'actifs comme l'illustrent les diagrammes et l'explication qui suit : 
  
![Diagramme 1 de 2 : Type d'événement, étiquettes, événements et identification des actifs.](../media/a5141a6b-61ca-4a60-9ab0-24e6bb45bbdb.png)
  
![Diagramme 2 de 2 : Type d'événement, étiquettes, événements et identification des actifs.](../media/ce89a91f-49aa-4b5a-933c-ac3a13dccd5d.png)
  
1. You create retention labels for different types of content and then associate them with a type of event. For example, retention labels for different types of product files and records are associated with an event type named Product Lifetime because those records must be retained for 10 years from the time the product reaches its end of life.
    
2. Les utilisateurs, qui sont généralement des gestionnaires de documents, appliquent ces étiquettes de rétention au contenu et (pour les documents dans SharePoint et OneDrive) saisissent un identifiant de ressource pour chaque élément. Dans cet exemple, l’ID d’actif est un nom de produit ou un code utilisé par l’organisation. Ensuite, une étiquette de rétention est attribuée aux enregistrements de chaque produit, et chaque enregistrement possède une propriété qui contient un numéro d'identification de l'actif. Le diagramme représente **l'ensemble du contenu** de tous les enregistrements de produits dans une organisation, et chaque article porte l'ID de l'actif du produit dont il est l'enregistrement. 
    
3. Product Lifetime is the event type; a specific product reaching end of life is an event. When an event of that event type occurs—in this case, when a product reaches its end of life—you create an event that specifies:
    
   - Un ID d’élément (pour les documents SharePoint et OneDrive).
    
   - Keywords (for Exchange items). In this example, the organization uses a product code in messages containing product records, so the keyword for Exchange items is functionally the same as the asset ID for SharePoint and OneDrive documents.
    
   - The date when the event occurred. This date is used as the start of the retention period. This date can be the current, a past, or a future date.

4. After you create an event, that event date is synchronized to all the content that has a retention label of that event type and that contains the specified asset ID or keyword. Like any retention label, this synchronization can take up to seven days. In the previous diagram, all the items circled in red have their retention period triggered by this event. In other words, when this product reaches its end of life, that event triggers the retention period for that product's records.

Il est important de comprendre que si vous ne spécifiez pas d'identifiant ou de mots clés pour un événement, **tout contenu** avec une étiquette de rétention de ce type d'événement aura sa période de rétention déclenchée par l'événement. Cela signifie que, dans le diagramme précédent, tout le contenu commencera à être conservé. Il est peu probable que ce résultat corresponde à ce que vous avez prévu.

Finally, remember that each retention label has its own retention settings. In this example, they all specify 10 years, but it's possible for an event to trigger retention labels where each label has a different retention period.
  
## <a name="how-to-set-up-event-based-retention"></a>Comment configurer la rétention basée sur les événements

Flux de travail de haut niveau pour la rétention basée sur les événements :
  
![Diagramme de workflow pour la configuration de la rétention basée sur les événements.](../media/event-based-retention-process.png)
  
> [!TIP]
> Consultez [Utiliser les étiquettes de rétention pour gérer le cycle de vie des documents stockés dans SharePoint](auto-apply-retention-labels-scenario.md) pour obtenir un scénario détaillé sur l’utilisation de propriétés gérées dans SharePoint pour appliquer automatiquement des étiquettes de rétention et implémenter la rétention basée sur les événements.

### <a name="step-1-create-a-label-whose-retention-period-is-based-on-an-event"></a>Étape 1 : créer une étiquette dont la période de rétention est basée sur des événements

Pour créer et configurer votre étiquette de rétention, consultez les instructions pour [Créer des étiquettes de rétention](file-plan-manager.md#create-retention-labels) pour la gestion des enregistrements. Mais une rétention spécifique basée sur les événements :

- Dans la page **Définir les paramètres d’étiquette** lorsque vous créez l’étiquette de rétention, veillez à sélectionner **Conserver indéfiniment des éléments ou pendant une période spécifique**. Ensuite :
    
    Dans la page **Définir la période**, une fois la période défini, sélectionnez l’un des types d’événements par défaut dans la liste déroulante pour **Quand la période doit-elle commencer ?** Vous pouvez également créer votre propre type d’événement en sélectionnant **Créer un type d’événement** et en suivant les invites de configuration :
    
    ![Créer un nouveau type d’événement pour une étiquette de rétention.](../media/SPRetention6.png)

Un type d’événement est simplement une description générale d’un événement auquel vous voulez associer une étiquette de rétention.

Les types d’événements par défaut ont **(type d’événement)** après leur nom dans la liste déroulante afin de faciliter l’identification, et vous pouvez également afficher et créer un type d’événement à partir de la **gestion des enregistrements** > **Événements** > **gérer les types d’événements**.

La rétention basée sur un événement nécessite des paramètres de rétention qui :
  
- Conservent le contenu.
    
- suppriment automatiquement le contenu ou déclenchent une révision de destruction à la fin de la période de rétention.
  
La rétention basée sur les événements est généralement utilisée pour les contenus déclarés comme un enregistrement, c’est le moment idéal pour vérifier si vous avez également besoin de sélectionner l’option qui marque du contenu comme [enregistrement](records-management.md#records).

Si vous utilisez un type d’événement existant plutôt que de créer un nouveau type d’événement, passez à l’étape 3.

> [!NOTE]
> Une fois le type d’événement sélectionné et l’étiquette de rétention enregistrée, le type d’événement ne peut pas être modifié.

### <a name="step-2-create-a-new-event-type-for-your-label"></a>Étape 2 : Créer un nouveau type d’événement pour votre étiquette

For the retention settings, if you selected **Create new event type**, enter a name and description for your event type. Then select **Next**, **Submit**, and **Done**.

Une fois de retour dans la page **Définir la période**, pour la question **Quand la période doit-elle commencer ?**, utilisez la liste déroulante pour sélectionner le type d’événement que vous avez créé.

  
### <a name="step-3-publish-or-auto-apply-the-event-based-retention-labels"></a>Étape 3 : publier ou appliquer automatiquement les étiquettes de rétention basées sur les événements

Comme pour n’importe quelle étiquette de rétention, vous devez publier ou appliquer automatiquement une étiquette basée sur un événement, de sorte qu’elle soit appliquée au contenu de façon manuelle ou automatique :
- [Publier des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
- [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)

### <a name="step-4-enter-an-asset-id"></a>Étape 4 : saisissez un ID d’élément

After an event-based label is applied to content, you can enter an asset ID for each item. For example, your organization might use:
  
- Des codes de produit que vous pouvez utiliser pour conserver le contenu relatif à un produit spécifique.
    
- Des codes de projet que vous pouvez utiliser pour conserver le contenu relatif à un projet spécifique.
    
- ID d’employé à utiliser pour conserver uniquement le contenu d’une personne spécifique.
    
Asset ID is simply another document property that's available in SharePoint and OneDrive. Your organization might already use other document properties and IDs to classify content. If so, you can also use those properties and values when you create an event—see step 6 that follows. The important point is that you must use some *property:value* combination in the document properties to associate that item with an event type.
  
![Zone de texte pour saisir un ID d’élément.](../media/6d31628e-7162-4370-a8d7-de704aafa350.png)
  
### <a name="step-5-create-an-event"></a>Étape 5 : créer un événement

When a particular instance of that event type occurs, such as a product reaches its end of life, go to the **Records management** > **Events** page in the Microsoft Purview compliance portal, and select **+ Create** to create an event. You trigger the event by creating it, here.

![Créer un événement pour déclencher le démarrage de la rétention pour les étiquettes de rétention basée sur les événements.](../media/create-event-records-management.png)

Jusqu’à 1 000 000 d’événements sont pris en charge par client.

### <a name="step-6-choose-the-same-event-type-used-by-the-label-in-step-2"></a>Étape 6 : Choisir le même type d’événement utilisé par l’étiquette à l’étape 2

Lorsque vous créez l’événement, choisissez le même type d'événement que celui spécifié dans les paramètres de l’étiquette de rétention à l’étape 2. Par exemple, si vous avez sélectionné **Durée de vie du produit** comme type d'événement pour les paramètres de l’étiquette, sélectionnez **Durée de vie du produit** lorsque vous créez l'événement. La période de rétention sera déclenchée uniquement pour le contenu auquel sont appliquées des étiquettes de rétention de ce type d’événement.

![Option dans les paramètres d’événement permettant de choisir un type d’événement.](../media/choose-event-type-records-management.png)

Par ailleurs, si vous devez créer un événement pour plusieurs étiquettes de rétention qui ont différents types d'événements, sélectionnez l'option **Choisir les étiquettes existantes**. Sélectionnez ensuite les étiquettes configurées pour les types d’événements que vous voulez associer à cet événement.

### <a name="step-7-enter-keywords-or-a-query-or-asset-id-for-sharepoint-and-onedrive"></a>Étape 7 : Entrer des mots clés, une requête ou un ID de ressource pour SharePoint et OneDrive

Vous limitez maintenant l’étendue du contenu. Pour ce faire, spécifiez des mots clés ou une requête. Pour le contenu SharePoint et OneDrive, vous pouvez également le faire en spécifiant des ID de ressource.

Les requêtes utilisent le langage KQL (Keyword Query Language). Pour plus d'informations sur la syntaxe de requête, voir [Référence de syntaxe de langage de requête de mot clé (KQL)](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference). Pour plus d’informations sur ces propriétés utilisables dans une requête, consultez [Requêtes par mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).

Pour les ID de ressource, la rétention sera appliquée uniquement au contenu comportant la paire *propriété:valeur* spécifiée. Par exemple, Si vous utilisez la propriété ID d’élément, vous entrez `ComplianceAssetID:<value>` dans la zone réservée aux ID de ressource illustrée dans l’image suivante.

Si vous n’entrez pas d’ID de ressource, tout le contenu portant des étiquettes de ce type d’événement se voit appliquer la même date de rétention.

Your organization might have applied other properties and IDs to the documents related to this event type. For example, if you need to detect a specific product's records, the ID might be a combination of your custom property ProductID and the value "XYZ". In this case, you'd enter `ProductID:XYZ` in the box for asset IDs shown in the following picture.

Finally, choose the date when the event occurred; this date is used as the start of the retention period. After you create an event, that event date is synchronized to all the content with a retention label of that event type, asset ID, and keywords or queries. As with any retention label, this synchronization can take up to seven days.
  
![Page Paramètres des événements.](../media/40d3c9db-f624-49a5-b38a-d16bcce20231.png)

Une fois que vous avez créé un événement, les paramètres de rétention prennent effet pour le contenu déjà étiqueté et indexé. Si l’étiquette de rétention est ajoutée au nouveau contenu une fois l’événement créé, vous devez créer un événement avec les mêmes détails.

Deleting an event doesn't cancel the retention settings that are now in effect for the content that's already labeled. Currently, you can't cancel events after they're triggered.

## <a name="use-content-search-to-find-all-content-with-a-specific-label-or-asset-id"></a>Utilisation de la recherche de contenu pour rechercher tout le contenu portant une étiquette ou un ID d’élément spécifique

Une fois que les étiquettes de rétention sont attribuées au contenu, vous pouvez utiliser la recherche de contenu pour rechercher tout le contenu qui a une étiquette de rétention spécifique ou qui contient un ID de ressource spécifique :
  
- Pour trouver tout le contenu portant une étiquette de rétention spécifique, sélectionnez la condition **Étiquette de rétention**, puis saisissez le nom d’étiquette en partie ou en intégralité et utilisez un caractère générique. 
    
- Pour trouver tout le contenu portant un ID d’élément spécifique, saisissez la propriété **ComplianceAssetID** et une valeur, telle que `ComplianceAssetID:<value>`. 
    
Si vous souhaitez en savoir plus, consultez la page [Requêtes par mots-clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).

## <a name="automate-events-by-using-powershell"></a>Automatisation des événements à l’aide de PowerShell

Vous pouvez utiliser un script PowerShell pour automatiser une rétention basée sur un événement à partir de vos applications métier. Les cmdlets PowerShell disponibles pour les rétentions basées sur des événements :
  
- [Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype)
    
- [New-ComplianceRetentionEventType](/powershell/module/exchange/new-complianceretentioneventtype)
    
- [Remove-ComplianceRetentionEventType](/powershell/module/exchange/remove-complianceretentioneventtype)
    
- [Set-ComplianceRetentionEventType](/powershell/module/exchange/set-complianceretentioneventtype)
    
- [Get-ComplianceRetentionEvent](/powershell/module/exchange/get-complianceretentionevent)
    
- [New-ComplianceRetentionEvent](/powershell/module/exchange/new-complianceretentionevent)
    

pour identifier d’autres cmdlets permettant de créer des étiquettes de rétention et leurs stratégies, consultez les [cmdlets PowerShell pour les stratégies de rétention et les étiquettes de rétention](retention-cmdlets.md).

## <a name="automate-events-by-using-a-rest-api"></a>Automatisation des événements à l’aide de l’API REST

Vous pouvez utiliser une API REST pour créer automatiquement les événements qui déclenchent la période de rétention.

> [!NOTE]
> À présent déployé en préversion, vous pouvez également utiliser [Microsoft Graph API pour la gestion des enregistrements](compliance-extensibility.md#microsoft-graph-api-for-records-management-preview) afin de créer l’événement, ainsi que des types d’événements et des étiquettes de rétention.
> 
> Nous vous encourageons à essayer ces API Graph, car les API REST de cette section seront bientôt déconseillées et cesseront de fonctionner.

A REST API is a service endpoint that supports sets of HTTP operations (methods), which provide create/retrieve/update/delete access to the service's resources. For more information, see [Components of a REST API request/response](/rest/api/gettingstarted/#components-of-a-rest-api-requestresponse). By using the Microsoft 365 REST API, events can be created and retrieved using the POST and GET methods.

Vous pouvez utiliser l’API REST de deux manières :

- Avec **Microsoft Power Automate ou une application similaire** pour déclencher automatiquement l’occurrence d’un événement. Microsoft Power Automate est un orchestrateur permettant de se connecter à d'autres systèmes, vous n'avez donc pas besoin d'écrire une solution personnalisée. Si vous souhaitez en savoir plus, veuillez consulter le [site web de Power automate](https://flow.microsoft.com/en-us/).

- Avec **PowerShell ou un client HTTP pour appeler l’API REST** pour créer des événements à l’aide de PowerShell (version 6 ou ultérieure), dans le cadre d’une solution personnalisée.

Avant d’utiliser l’API REST, en tant qu’administrateur général, confirmez l’URL à utiliser pour l’appel d’événement de rétention. Pour ce faire, exécutez un appel d’événement de rétention GET à l’aide de l’URL de l’API REST :

```http
https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent
```

Check the response code. If it's 302, get the redirected URL from the Location property of the response header and use that URL instead of `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent` in the instructions that follow.

Les événements qui sont créés automatiquement peuvent être confirmés en les affichant dans le portail de conformité Microsoft Purview > **Gestion des enregistrements** >  **Événements**.

### <a name="use-microsoft-power-automate-to-create-the-event"></a>Utiliser Microsoft Power Automate pour créer l’événement

Créez un flux qui crée un événement en utilisant l’API REST Microsoft 365 :

![Utilisation du fux pour créer un événement.](../media/automate-event-driven-retention-flow-1.png)

![Utilisation du flux pour appeler des API REST.](../media/automate-event-driven-retention-flow-2.png)

#### <a name="create-an-event"></a>Créer un événement

Utilisation du code d’exemple pour appeler des API REST :

- **Method** : PUBLIER
- **URL** :`https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Headers** : Clé = Type de contenu, Valeur = application/atom+xml
- **Body** :

    ```xml
    <?xml version='1.0' encoding='utf-8' standalone='yes'?>
    
    <entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'
    
    xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'
    
    xmlns='http://www.w3.org/2005/Atom'>
    
    <category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />
    
    <updated>9/9/2017 10:50:00 PM</updated>
    
    <content type='application/xml'>
    
    <m:properties>
    
    <d:Name>Employee Termination </d:Name>
    
    <d:EventType>99e0ae64-a4b8-40bb-82ed-645895610f56</d:EventType>
    
    <d:SharePointAssetIdQuery>1234</d:SharePointAssetIdQuery>
    
    <d:EventDateTime>2018-12-01T00:00:00Z </d:EventDateTime>
    
    </m:properties>
    
    </content>
    
    </entry>
    ```

- **Authentification** : de base
- **Nom d’utilisateur** : « Complianceuser »
- **Password** : « Compliancepassword »


##### <a name="available-parameters"></a>Paramètres disponibles


|Paramètres|Description|Notes|
|--- |--- |--- |
|<d:Name></d:Name>|Entrez un nom unique pour la base de données,|Ne peut pas contenir les espaces ou les caractères suivants : % * \ & < \> \| # ? , : ;|
|<d:EventType></d:EventType>|Entrez le nom de l’événement (ou Guid),|Example: "Employee termination". Event type has to be associated with a retention label.|
|<d:SharePointAssetIdQuery></d:SharePointAssetIdQuery>|Entrez « ComplianceAssetId : » suivi de l’ID de l’employé|Example: "ComplianceAssetId:12345"|
|<d:EventDateTime></d:EventDateTime>|Date et heure de l’événement.|Format : AAAA-MM-jjTHH : mm : ssZ ; exemple : 2018-12-01T00:00:00Z
|

###### <a name="response-codes"></a>Codes de réponse

| Code de réponse | Description       |
| ----------------- | --------------------- |
| 302               | Rediriger              |
| 201               | Créé               |
| 403               | Autorisation échouée  |
| 401               | Message d’échec d’authentification |

##### <a name="get-events-based-on-a-time-range"></a>Obtenir des événements en fonction de l’intervalle de temps

- **Méthode**: GET

- **URL** :`https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent?BeginDateTime=2019-01-11&EndDateTime=2019-01-16`

- **Headers** : Clé = Type de contenu, Valeur = application/atom+xml

- **Authentification** : de base

- **Nom d’utilisateur** : « Complianceuser »

- **Password** : « Compliancepassword »

###### <a name="response-codes"></a>Codes de réponse

| Code de réponse | Description                   |
| ----------------- | --------------------------------- |
| 200                | OK, une liste d’événements dans atome + xml |
| 404                | Introuvable                         |
| 302               | Rediriger                          |
| 401               | Autorisation échouée              |
| 403               | Message d’échec d’authentification             |

##### <a name="get-an-event-by-id"></a>Obtenir un événement par ID

- **Méthode**: GET

- **URL** :`https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent('174e9a86-74ff-4450-8666-7c11f7730f66')`

- **Headers** : Clé = Type de contenu, Valeur = application/atom+xml

- **Authentification** : de base

- **Nom d’utilisateur** : « Complianceuser »

- **Password** : « Compliancepassword »

###### <a name="response-codes"></a>Codes de réponse

| Code de réponse | Description                                      |
| ----------------- | ---------------------------------------------------- |
| 200                | OK, le corps du message de réponse contient l’événement dans atome + xml |
| 404                | Introuvable                                            |
| 302               | Rediriger                                             |
| 401               | Autorisation échouée                                 |
| 403               | Message d’échec d’authentification                                |

##### <a name="get-an-event-by-name"></a>Obtenir un événement par le nom

- **Méthode**: GET

- **URL** :`https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`

- **Headers** : Clé = Type de contenu, Valeur = application/atom+xml

- **Authentification** : de base

- **Nom d’utilisateur** : « Complianceuser »

- **Password** : « Compliancepassword »

###### <a name="response-codes"></a>Codes de réponse

| Code de réponse | Description                                      |
| ----------------- | ---------------------------------------------------- |
| 200                | OK, le corps du message de réponse contient l’événement dans atome + xml |
| 404                | Introuvable                                            |
| 302               | Rediriger                                             |
| 401               | Autorisation échouée                                 |
| 403               | Message d’échec d’authentification                                |

### <a name="use-powershell-or-any-http-client-to-create-the-event"></a>Utiliser PowerShell ou n’importe quel client HTTP pour créer l’événement

Vous devez utiliser au moins la version 6 de PowerShell.

Dans une session PowerShell, exécutez le script suivant :

```powershell
param([string]$baseUri)

$userName = "UserName"

$password = "Password"

$securePassword = ConvertTo-SecureString $password -AsPlainText -Force

$credentials = New-Object System.Management.Automation.PSCredential($userName, $securePassword)

$EventName="EventByRESTPost-$(([Guid]::NewGuid()).ToString('N'))"

Write-Host "Start to create an event with name: $EventName"

$body = "<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'

xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'

xmlns='http://www.w3.org/2005/Atom'>

<category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />

<updated>7/14/2017 2:03:36 PM</updated>

<content type='application/xml'>

<m:properties>

<d:Name>$EventName</d:Name>

<d:EventType>e823b782-9a07-4e30-8091-034fc01f9347</d:EventType>

<d:SharePointAssetIdQuery>'ComplianceAssetId:123'</d:SharePointAssetIdQuery>

</m:properties>

</content>

</entry>"

$event = $null

try

{

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri "$baseUri/ComplianceRetentionEvent" -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

catch

{

$response = $_.Exception.Response

if($response.StatusCode -eq "Redirect")

{

$url = $response.Headers.Location

Write-Host "redirected to $url"

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri $url -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

}

$event | fl *
```
