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
ms.openlocfilehash: 03f8446d54d905665f5bf33c2f581a869dfc478e
ms.sourcegitcommit: d988faa292c2661ffea43c7161aef92b2b4b99bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "46560531"
---
# <a name="start-retention-when-an-event-occurs"></a>Débuter la rétention lorsqu’un événement se produit

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Lorsque vous conservez du contenu, la période de rétention est souvent basée sur l’ancienneté du contenu. Par exemple, vous pouvez conserver des documents pendant sept ans à compter de leur création, puis les supprimer. Cependant, lorsque vous configurez [étiquettes de rétention](labels.md), vous pouvez baser une période de rétention sur l’occurrence d’un type spécifique d’événement. L’événement déclenche le début de la période de rétention, et les actions de rétention d’une étiquette sont appliquées sur tout le contenu portant l’étiquette en question pour ce type d’événement.
  
Exemples d’utilisation de la rétention fondée sur les événements :
  
- **Employés quittant l'organisation**Supposons que les enregistrements d’un employé doivent être conservés 10 ans à compter de son départ de l’organisation. Une fois les 10 ans écoulés, tous les documents concernant l’embauche, les résultats et le départ de cet employé doivent être supprimés. L’événement qui déclenche la période de rétention de 10 ans est le départ de l’employé de l’organisation. 
    
- **Expiration du contrat** Supposons que tous les enregistrements liés aux contrats doivent être conservés pendant cinq ans après l’expiration du contrat. L’événement qui déclenche la période de rétention de cinq ans est l’expiration du contrat. 
    
- **Durée de vie des produits** Votre organisation a peut-être des exigences de rétention liées à la dernière date de fabrication de produits pour le contenu tel que des spécifications techniques. Dans ce cas, la dernière date de fabrication est l’événement qui déclenche la période de rétention. 
    
Les rétentions basées sur des événements sont généralement utilisées dans le cadre d’un processus de gestion des enregistrements. Il faut alors prendre en compte les points suivants :
  
- Les étiquettes basées sur des événements classent généralement le contenu en tant qu’enregistrement. Pour plus d’informations, voir [En savoir plus sur les enregistrements](records.md).

- Un document qui a été classifié comme enregistrement, mais dont l’événement déclencheur ne s’est pas encore produit, est conservé indéfiniment (les enregistrements ne peuvent pas être supprimés définitivement) jusqu’à ce qu’un événement déclenche la période de rétention du document en question.
    
- Les étiquettes de rétention basées sur des événements déclenchent généralement une révision avant destruction à la fin de la période de rétention, ce qui permet à un gestionnaire d’enregistrements de manuellement passer en revue puis supprimer le contenu. Si vous souhaitez en savoir plus, consultez la page [Destruction de contenu](disposition.md).
    

Les étiquettes basées sur un événement possèdent les mêmes fonctionnalités que les étiquettes de rétention dans Microsoft 365. Pour plus d’informations, voir [En savoir plus sur les stratégies et les étiquettes de rétention](retention.md).

## <a name="understanding-the-relationship-between-event-types-labels-events-and-asset-ids"></a>Compréhension de la relation entre les types d’événements, les étiquettes, les événements et les ID d’élément

Pour utiliser avec succès la rétention basée sur un événement, il est important de comprendre la relation entre les types d’événement, les étiquettes de rétention, les événements et les ID d’éléments, comme illustré dans les diagrammes et l’explication qui suit : 
  
![Diagramme illustrant le type d’événement, les étiquettes, les événements et les ID d’élément](../media/a5141a6b-61ca-4a60-9ab0-24e6bb45bbdb.png)
  
![Diagramme illustrant le type d’événement, les étiquettes, les événements et les ID d’élément](../media/ce89a91f-49aa-4b5a-933c-ac3a13dccd5d.png)
  
1. Vous créez des étiquettes de rétention pour différents types de contenu et vous les associez à un type d’événement. Par exemple, les étiquettes pour différents types de fichiers et d’enregistrements de produit sont associées à un type d’événement nommé Durée de vie des produits, car ces enregistrements doivent être conservés pendant 10 ans à compter de la fin de vie du produit.
    
2. Les utilisateurs (en général les gestionnaires des enregistrements) appliquent ces étiquettes de rétention au contenu et (pour les documents SharePoint et OneDrive) entrent un ID d’élément pour chaque élément. Dans cet exemple, l’ID d’actif est un nom de produit ou un code utilisé par l’organisation. Par conséquent, les enregistrements de chaque produit se voient attribuer une étiquette de rétention, et chaque enregistrement possède une propriété contenant un ID d’actif. Le diagramme représente **l’ensemble du contenu** de tous les enregistrements des produits d’une organisation, et chaque élément porte l’ID d’élément du produit auquel appartient l’enregistrement. 
    
3. La fin de vie d’un produit est un « événement ». La durée de vie de ce produit est un « type d’événement ». Lorsqu’un événement (« fin de vie ») se produit pour un type d’événement (« durée de vie du produit »), vous devez créer un événement qui spécifie :
    
   - Un ID d’élément (pour les documents SharePoint et OneDrive).
    
   - Des mots clés (pour les éléments Exchange) Dans cet exemple, l’organisation utilise un code de produit dans les messages contenant des enregistrements de produit. Le mot clé pour les éléments Exchange est donc identique à l’ID d’élément pour les documents SharePoint et OneDrive.
    
   - La date à laquelle l’événement s'est produit. Cette date est utilisée comme point de départ de la période de rétention. Cette date peut être la date actuelle, passée ou une date future.

4. Lorsque vous avez créé un événement, sa date est synchronisée avec tout le contenu portant l’étiquette de rétention du type d’événement correspondant et contenant l’ID d’élément ou le mot clé spécifié. Comme pour toute étiquette de rétention, cette synchronisation peut prendre jusqu’à 7 jours. Dans le diagramme précédent, la période de rétention de tous les éléments encerclés en rouge est déclenchée par cet événement. En d’autres termes, lorsque ce produit atteint sa fin de vie, cet événement déclenche la période de rétention pour les enregistrements de ce produit.

Il est important de comprendre que si vous ne spécifiez pas d’ID d’élément ou de mot clé pour un événement, **tout le contenu** portant une étiquette de ce type d’événement verra sa période de rétention déclenchée par l’événement. Cela signifie que, dans le diagramme précédent, tout le contenu commencera à être conservé. Ce n’est peut-être pas ce que vous voulez faire. 

Enfin, rappelez-vous que chaque étiquette de rétention possède ses propres paramètres de rétention. Dans cet exemple, ils indiquent tous 10 ans, mais un événement peut très bien déclencher des étiquettes de rétention dont chacune possède sa propre période de rétention.
  
## <a name="how-to-set-up-event-driven-retention"></a>Configuration des rétentions basées sur des événements

Flux de travail général pour la rétention basée sur un événement :
  
![Diagramme du flux de travail de la configuration des rétentions basées sur des événements](../media/event-based-retention-process.png)
  
> [!TIP]
> Consultez [Gérer le cycle de vie des documents sauvegardés sur SharePoint avec des étiquettes de rétention](auto-apply-retention-labels-scenario.md) pour un scénario détaillé sur l’utilisation de propriétés gérées dans SharePoint afin d'appliquer automatiquement des étiquettes de rétention et exécuter la rétention basée sur un événement.

### <a name="step-1-create-a-label-whose-retention-period-is-based-on-an-event"></a>Étape 1 : créer une étiquette dont la période de rétention est basée sur des événements

Pour créer et configurer votre étiquette de rétention, suivez les instructions de [Créer et configurer des étiquettes de rétention](create-retention-labels.md#create-and-configure-retention-labels) puis, lorsque vous activez la rétention, sélectionnez l’option permettant de conserver ou de supprimer le contenu sur la base d’un événement. Ce paramètre signifie que les paramètres de rétention ne prendront pas effet avant l’étape 5, à laquelle vous créez un événement sur la page **Événements**. 
  
La rétention basée sur un événement est généralement utilisée pour les contenus classés sous la forme d’un enregistrement, c’est le moment idéal pour vérifier si vous avez également besoin de sélectionner l’option qui marque du contenu comme enregistrement.
  
La rétention basée sur un événement nécessite des paramètres de rétention qui :
  
- Conservent le contenu.
    
- suppriment automatiquement le contenu ou déclenchent une révision de destruction à la fin de la période de rétention.
    
![Option pour baser une étiquette sur un événement](../media/a4902281-5196-4194-9737-f30231d95861.png)

### <a name="step-2-choose-an-event-type-for-that-label"></a>Étape 2 : choisir un type d’événement pour cette étiquette

Dans les paramètres d’étiquette, après avoir choisi l’option de baser l’étiquette sur **un événement**, l’option **Choisir un type d’événement** apparaît. Un type d’événement est simplement une description générale d’un événement auquel vous voulez associer une étiquette.
  
Par exemple, si vous créez un type d’événement nommé Durée de vie des produits, vous allez créer des étiquettes de rétention basées sur un événement avec des noms qui décrivent les types de contenu auxquels vous souhaitez appliquer des étiquettes. Par exemple, « Fichiers de développement des produits » ou « Enregistrements de la décision commerciale des produits ».

Sélectionnez l’un des types d’événements intégrés, ou créez votre propre événement, puis sélectionnez-le.

Une fois que vous avez sélectionné un type d’événement et enregistré l’étiquette de rétention, le type d’événement ne peut pas être modifié.
  
![Options permettant de créer ou de sélectionner un type d’événement](../media/8b7afe79-72cb-462e-81d4-b5ddbe899dbc.png)
  
### <a name="step-3-publish-or-auto-apply-the-event-based-retention-labels"></a>Étape 3 : publier ou appliquer automatiquement les étiquettes de rétention basées sur les événements

Comme pour n’importe quelle étiquette de rétention, vous devez publier ou appliquer automatiquement une étiquette basée sur un événement, de sorte qu’elle soit appliquée au contenu de façon manuelle ou automatique :
- [Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
- [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)


> [!NOTE]
> Si vous sélectionnez une étiquette de rétention basée sur un événement à partir d’un onglet **Gestion des enregistrements** > **Plan de gestion des fichiers** ou **Gouvernance des données** > **Étiquettes**, le bouton **Appliquer automatiquement une étiquette** n’est pas disponible.
> 
> Au lieu de ce bouton, utilisez l’option **Appliquer automatiquement une étiquette** au-dessus de la liste des étiquettes ou des stratégies à partir de l’un des emplacements suivants :
> - Onglet **Gestion des enregistrements** > **Stratégies des étiquettes**
> - Onglet **Gouvernance des données** > **Étiquettes** ou **Stratégies des étiquettes**


![Options permettant de publier ou d’appliquer automatiquement une étiquette de rétention](..\media\compliance-information-governance-publish-labels.png)

### <a name="step-4-enter-an-asset-id"></a>Étape 4 : saisissez un ID d’élément

Une fois qu’une étiquette basée sur un événement a été appliquée au contenu, vous pouvez entrer un ID d’élément pour chaque élément. Par exemple, votre organisation peut utiliser :
  
- Des codes de produit que vous pouvez utiliser pour conserver le contenu relatif à un produit spécifique.
    
- Des codes de projet que vous pouvez utiliser pour conserver le contenu relatif à un projet spécifique.
    
- ID d’employé à utiliser pour conserver uniquement le contenu d’une personne spécifique.
    
L’ID d’élément constitue simplement une autre propriété de document qui est disponible dans SharePoint et OneDrive. Votre organisation utilise peut-être déjà d’autres ID et propriétés de document pour classer le contenu. Le cas échéant, vous pouvez également utiliser ces propriétés et valeurs lorsque vous créez un événement (voir l’étape 6, plus bas). L’essentiel est que vous utilisez une combinaison *propriété:valeur* dans les propriétés du document pour associer cet élément à un type d’événement.
  
![Zone de texte pour saisir un ID d’élément](../media/6d31628e-7162-4370-a8d7-de704aafa350.png)
  
### <a name="step-5-create-an-event"></a>Étape 5 : créer un événement

Lorsqu’une instance précise de ce type d’événement se produit (par exemple, un produit arrive en fin de vie), accédez à la page **Gestions des enregistrements** > **Événements** dans le Centre de conformité Microsoft 365, et créez un événement. Vous devez déclencher un événement en le créant.
  
### <a name="step-6-choose-the-same-event-type-used-by-the-label-in-step-2"></a>Étape 6 : choisir le même type d’événement utilisé par l’étiquette à l’étape 2

Lorsque vous créez l’événement, choisissez le type d’événement utilisé par l’étiquette de rétention à l’étape 2 (par exemple, « Durée de vie du produit »). La période de rétention sera déclenchée uniquement pour le contenu auquel sont appliquées des étiquettes de rétention de ce type d’événement.
  
![Option dans les paramètres d’événement permettant de choisir un type d’événement](../media/11663591-5628-419e-9537-61eb8f5c741f.png)
  
### <a name="step-7-enter-keywords-or-an-asset-id"></a>Étape 7 : saisir des mots clés ou un ID d’élément

Vous réduisez à présent l’étendue du contenu en spécifiant des ID d’élément pour le contenu SharePoint et OneDrive ou des mots clés pour le contenu Exchange. Pour les ID d’élément, la rétention sera appliquée uniquement au contenu comportant la paire *propriété:valeur* spécifiée. Si vous n’entrez pas d’ID d’élément, tout le contenu portant des étiquettes de ce type d’événement se voit appliquer la même date de rétention.

Par exemple : Si vous utilisez la propriété ID d’élément, vous entrez `ComplianceAssetID:<value>` dans la zone réservée aux ID d’élément illustrée ci-dessous.
  
Votre organisation a peut-être appliqué d’autres propriétés et ID aux documents associés à ce type d’événement. Par exemple, si vous avez besoin de détecter les enregistrements d’un produit spécifique, l’ID peut être une combinaison de la propriété personnalisée ProductID et de la valeur « XYZ ». Vous entrerez dans ce cas `ProductID:XYZ` dans la zone réservée aux ID d’élément illustrée dans l’image suivante.
  
Pour les éléments Exchange, utilisez des mots clés. Vous pouvez utiliser une requête en utilisant des opérateurs de recherche tels que ET, OU et NON. Si vous souhaitez en savoir plus, consultez la page [Requêtes par mots-clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).
  
Enfin, sélectionnez la date à laquelle l’événement s’est produit. cette date est utilisée comme début de la période de rétention. Une fois que vous avez créé un événement, la date de l’événement est synchronisée avec tout le contenu avec une étiquette de rétention de ce type d’événement, de l’ID d’actif et des mots clés. Comme pour toute étiquette de rétention, cette synchronisation peut prendre jusqu’à sept jours.
  
![Page Paramètres des événements](../media/40d3c9db-f624-49a5-b38a-d16bcce20231.png)

Une fois que vous avez créé un événement, les paramètres de rétention prennent effet pour le contenu déjà étiqueté et indexé. Si l’étiquette de rétention est ajoutée au nouveau contenu une fois l’événement créé, vous devez créer un événement avec les mêmes détails.

La suppression d’un événement n’annule pas les paramètres de rétention qui sont désormais appliqués pour le contenu qui est déjà étiqueté. Pour ce faire, créez un événement avec les mêmes détails, mais laissez la date vide. 

## <a name="use-content-search-to-find-all-content-with-a-specific-label-or-asset-id"></a>Utilisation de la recherche de contenu pour rechercher tout le contenu portant une étiquette ou un ID d’élément spécifique

Une fois que les étiquettes de rétention sont attribuées au contenu, vous pouvez utiliser la recherche de contenu pour rechercher tout le contenu classé avec une étiquette de rétention spécifique ou qui contient un ID d’élément spécifique :
  
- Pour trouver tout le contenu portant une étiquette de rétention spécifique, sélectionnez la condition **Étiquette de rétention**, puis saisissez le nom d’étiquette en partie ou en intégralité et utilisez un caractère générique. 
    
- Pour trouver tout le contenu portant un ID d’élément spécifique, saisissez la propriété **ComplianceAssetID** et une valeur, telle que `ComplianceAssetID:<value>`. 
    
Si vous souhaitez en savoir plus, consultez la page [Requêtes par mots-clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).
  
## <a name="permissions"></a>Autorisations

Pour accéder à la page **Événements**, les réviseurs doivent être membres du groupe de rôles possédant le rôle **Gestion de la destruction** et le rôle **Journaux d’audit en lecture seule**. Nous vous recommandons de créer un nouveau groupe de rôles appelé Réviseurs de destruction, d’ajouter ces deux rôles à ce groupe de rôles, puis d’ajouter des membres au groupe de rôles. 
  
Pour obtenir plus d’informations, consultez l’article [Octroi de l’accès au Centre de sécurité &amp; conformité Office 365 aux utilisateurs](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
## <a name="automate-events-by-using-powershell"></a>Automatisation des événements à l’aide de PowerShell

Vous pouvez utiliser un script PowerShell pour automatiser une rétention basée sur un événement à partir de vos applications métier. Les cmdlets PowerShell disponibles pour les rétentions basées sur des événements :
  
- [Get-ComplianceRetentionEventType](https://go.microsoft.com/fwlink/?linkid=873002)
    
- [New-ComplianceRetentionEventType](https://go.microsoft.com/fwlink/?linkid=873004)
    
- [Remove-ComplianceRetentionEventType](https://go.microsoft.com/fwlink/?linkid=873005)
    
- [Set-ComplianceRetentionEventType](https://go.microsoft.com/fwlink/?linkid=873006)
    
- [Get-ComplianceRetentionEvent](https://go.microsoft.com/fwlink/?linkid=873001)
    
- [New-ComplianceRetentionEvent](https://go.microsoft.com/fwlink/?linkid=873003)
    

## <a name="automate-events-by-using-a-rest-api"></a>Automatisation des événements à l’aide de l’API REST

Vous pouvez utiliser une API REST pour créer automatiquement les événements qui déclenchent la période de rétention.

Une API REST est un point de terminaison de service prenant en charge les ensembles d’opérations HTTP (méthodes) qui fournissent les droits d’accès de création/récupération/mise à jour/suppression aux ressources du service. Si vous souhaitez en savoir plus, veuillez consulter la section [Composants d’une demande/réponse d’API REST](https://docs.microsoft.com/rest/api/gettingstarted/#components-of-a-rest-api-requestresponse). L’API REST de Microsoft 365 vous permet de créer et d’extraire des événements à l’aide des méthodes POST et GET.

Vous pouvez utiliser l’API REST de deux manières :

- Avec **Microsoft Power Automate ou une application similaire** pour déclencher automatiquement l’occurrence d’un événement. Microsoft Power Automate est un orchestrateur permettant de se connecter à d'autres systèmes, vous n'avez donc pas besoin d'écrire une solution personnalisée. Si vous souhaitez en savoir plus, veuillez consulter le [site web de Power automate](https://flow.microsoft.com/fr-FR/).

- Avec **PowerShell ou un client HTTP pour appeler l’API REST** pour créer des événements à l’aide de PowerShell (version 6 ou ultérieure), dans le cadre d’une solution personnalisée.

Avant d’utiliser l’API REST, en tant qu’administrateur général, confirmez l’URL à utiliser pour l’appel d’événement de rétention. Pour ce faire, exécutez un appel d’événement de rétention GET à l’aide de l’URL de l’API REST :

```console
https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent
```

Vérifiez le code de réponse. S’il est 302, récupérez l’URL redirigée à partir de la propriété Location de l’en-tête de réponse, puis utilisez cette URL au lieu de `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent` dans les instructions qui suivent.

Les événements qui sont créés automatiquement peuvent être confirmés en les affichant dans le Centre de conformité Microsoft 365 > **Gestion des enregistrements** >  **Événements**.

### <a name="use-microsoft-power-automate-to-create-the-event"></a>Utiliser Microsoft Power Automate pour créer l’événement

Créez un flux qui crée un événement en utilisant l’API REST Microsoft 365 :

![Utilisation le flux pour créer un événement](../media/automate-event-driven-retention-flow-1.png)

![Utilisation du flux pour appeler des API REST](../media/automate-event-driven-retention-flow-2.png)

#### <a name="create-an-event"></a>Créer un événement

Utilisation du code d’exemple pour appeler des API REST :

- **Method** : PUBLIER
- **URL** :`https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Headers** : Clé = Type de contenu, Valeur = application/atom+xml
- **Body** :
    
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
    
- **Authentification** : de base
- **Nom d’utilisateur** : « Complianceuser »
- **Password** : « Compliancepassword »


##### <a name="available-parameters"></a>Paramètres disponibles


|Paramètres|Description|Notes|
|--- |--- |--- |
|<d:Name></d:Name>|Entrez un nom unique pour la base de données,|Ne peut pas contenir les espaces ou les caractères suivants : % * \ & < \> \| # ? , : ;|
|<d:EventType></d:EventType>|Entrez le nom de l’événement (ou Guid),|Exemple : « Fin de contrat d’un employé ». Le type d’événement doit être associé à une étiquette de rétention.|
|<d:SharePointAssetIdQuery></d:SharePointAssetIdQuery>|Entrez « ComplianceAssetId : » suivi de l’ID de l’employé|Example: "ComplianceAssetId:12345"|
|<d:EventDateTime></d:EventDateTime>|Date et heure de l’événement.|Format : AAAA-MM-jjTHH : mm : ssZ ; exemple : 2018-12-01T00:00:00Z
|

###### <a name="response-codes"></a>Codes de réponse

| Code de réponse | Description       |
| ----------------- | --------------------- |
| 302               | Rediriger              |
| 201               | Créé               |
| 403               | Autorisation échouée  |
| 401               | Message d’échec d’authentification |

##### <a name="get-events-based-on-a-time-range"></a>Obtenir des événements en fonction de l’intervalle de temps

- **Méthode **: GET

- **URL** :`https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent?BeginDateTime=2019-01-11&EndDateTime=2019-01-16`

- **Headers** : Clé = Type de contenu, Valeur = application/atom+xml

- **Authentification** : de base

- **Nom d’utilisateur** : « Complianceuser »

- **Password** : « Compliancepassword »


###### <a name="response-codes"></a>Codes de réponse

| Code de réponse | Description                   |
| ----------------- | --------------------------------- |
| 200               | OK, une liste d’événements dans atome + xml |
| 404               | Introuvable                         |
| 302               | Rediriger                          |
| 401               | Autorisation échouée              |
| 403               | Message d’échec d’authentification             |

##### <a name="get-an-event-by-id"></a>Obtenir un événement par ID

- **Méthode **: GET

- **URL** :`https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent('174e9a86-74ff-4450-8666-7c11f7730f66')`

- **Headers** : Clé = Type de contenu, Valeur = application/atom+xml

- **Authentification** : de base

- **Nom d’utilisateur** : « Complianceuser »

- **Password** : « Compliancepassword »

###### <a name="response-codes"></a>Codes de réponse

| Code de réponse | Description                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, le corps du message de réponse contient l’événement dans atome + xml |
| 404               | Introuvable                                            |
| 302               | Rediriger                                             |
| 401               | Autorisation échouée                                 |
| 403               | Message d’échec d’authentification                                |

##### <a name="get-an-event-by-name"></a>Obtenir un événement par le nom

- **Méthode **: GET

- **URL** :`https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`

- **Headers** : Clé = Type de contenu, Valeur = application/atom+xml

- **Authentification** : de base

- **Nom d’utilisateur** : « Complianceuser »

- **Password** : « Compliancepassword »


###### <a name="response-codes"></a>Codes de réponse

| Code de réponse | Description                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, le corps du message de réponse contient l’événement dans atome + xml |
| 404               | Introuvable                                            |
| 302               | Rediriger                                             |
| 401               | Autorisation échouée                                 |
| 403               | Message d’échec d’authentification                                |

### <a name="use-powershell-or-any-http-client-to-create-the-event"></a>Utiliser PowerShell ou n’importe quel client HTTP pour créer l’événement

Vous devez utiliser au moins la version 6 de PowerShell.

Dans une session PowerShell, exécutez le script suivant :

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

