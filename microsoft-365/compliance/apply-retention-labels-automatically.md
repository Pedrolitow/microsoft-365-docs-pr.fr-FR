---
title: Application automatique d’une étiquette de rétention pour conserver ou supprimer du contenu
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Créez des étiquettes de rétention et des stratégies d’étiquetage automatique afin de pouvoir appliquer les étiquettes de manière automatique pour conserver les éléments utiles et supprimer les éléments inutiles.
ms.openlocfilehash: eeeda9a41f35f6380d2d20adf80b00bc80ba4c4e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60198768"
---
# <a name="automatically-apply-a-retention-label-to-retain-or-delete-content"></a>Application automatique d’une étiquette de rétention pour conserver ou supprimer du contenu

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Ce scénario n'est pas pris en charge pour [les enregistrements réglementaires](records-management.md#records) ou les étiquettes par défaut pour une structure d'organisation telle qu'un ensemble de documents ou une bibliothèque dans Microsoft Office SharePoint Online, ou un dossier dans Exchange. Ces scénarios nécessitent une [stratégie d'étiquette de rétention publiée](create-apply-retention-labels.md#step-2-publish-retention-labels).

L’une des fonctionnalités les plus puissantes des [étiquettes de rétention](retention.md) est la possibilité d’appliquer celles-ci automatiquement à tout contenu correspondant à certaines conditions spécifiques. Dans ce cas, les personnes au sein de votre organisation ne doivent pas appliquer les étiquettes de rétention. Microsoft 365 s’en charge à leur place.
  
Les étiquettes de rétention appliquées automatiquement sont puissantes pour les raisons suivantes :
  
- Vous n’avez pas besoin de former les utilisateurs concernant l’ensemble de vos classifications.
    
- Vous n’avez pas à dépendre des utilisateurs pour classer tout le contenu correctement.
    
- Les utilisateurs n’ont plus besoin de connaître les stratégies de gouvernance des données : ils peuvent se concentrer sur leur travail.
    
Vous pouvez appliquer automatiquement des étiquettes de rétention à du contenu lorsque celui-ci contient des informations sensibles, des mots clés, des propriétés pouvant faire l’objet d’une recherche ou une correspondance pour des [classifieurs pouvant être formés](classifier-get-started-with.md).

> [!TIP]
> Utilisez des propriétés de recherche pour identifier [les enregistrements de réunion Teams](#microsoft-teams-meeting-recordings) et [les éléments auxquels une étiquette de confidentialité est appliquée](#identify-files-and-emails-that-have-a-sensitivity-label).

Les processus d’application automatique d’une étiquette de rétention sont fonction des conditions suivantes :

![Diagramme des rôles et des tâches pour les étiquettes à appliquer automatiquement.](../media/32f2f2fd-18a8-43fd-839d-72ad7a43e069.png)

Utilisez les instructions suivantes pour les deux étapes d’administration.

> [!NOTE]
> Les stratégies automatiques utilisent l’étiquetage côté service avec des conditions pour appliquer automatiquement des étiquettes de rétention. Vous pouvez également appliquer automatiquement une étiquette de rétention avec une stratégie d’étiquette lorsque vous procédez comme suit : 
>
> - Application d’une étiquette de rétention à un modèle de compréhension de document dans SharePoint Syntex.
> - Application d’une étiquette de rétention par défaut pour SharePoint et Outlook
>- Application d’une étiquette de rétention pour les e-mails à l’aide de règles Outlook
>
> Pour ces scénarios, voir [Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md).

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de votre organisation dispose de toutes les autorisations pour créer et gérer les étiquettes de rétention et leurs stratégies. Si vous ne vous connectez pas en tant qu’administrateur général, voir [Autorisations nécessaires pour créer et gérer des stratégies et des étiquettes de confidentialité](get-started-with-retention.md#permissions-required-to-create-and-manage-retention-policies-and-retention-labels).

## <a name="how-to-auto-apply-a-retention-label"></a>Application automatique d’étiquettes de rétention

Tout d’abord, créez votre étiquette de rétention. Créez ensuite une stratégie automatique pour appliquer l’étiquette. Si vous avez déjà créé votre étiquette de rétention, passez à [Création d’une stratégie automatique](#step-2-create-an-auto-apply-policy).

Les instructions de navigation varient selon que vous utilisez ou non [la gestion des enregistrements](records-management.md). Des instructions sont fournies pour les deux scénarios.

### <a name="step-1-create-a-retention-label"></a>Étape 1 : créer une étiquette de rétention

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), accédez à l’un des emplacements suivants :
    
    - Si vous utilisez la gestion des enregistrements :
        - **Solutions** > **Gestion des enregistrements** > **Plan de fichiers** onglet > **+ Créer une étiquette** > **Étiquette de rétention**
        
    - Si vous n’utilisez pas la gestion des enregistrements :
       - **Solutions** > **Gouvernance d’informations** > **Étiquettes** onglet > + **Créer une étiquette**
    
    Votre option ne s’affiche pas immédiatement ? Sélectionnez tout d’abord **Afficher tout**. 

2. Suivez les invites de l’Assistant. Si vous utilisez la gestion des enregistrements :
    
    - Pour plus d’informations sur les descripteurs de plan de fichier, consultez [Utiliser le plan de gestion des fichiers pour gérer les étiquettes de rétention](file-plan-manager.md)
    
    - Pour utiliser l’étiquette de rétention pour déclarer des enregistrements, sélectionnez **Marquer les éléments comme enregistrements**, ou **Marquer les éléments comme enregistrements réglementaires**. Pour plus d’information, voir [Configuration d’étiquettes de rétention pour déclarer des enregistrements](declare-records.md#configuring-retention-labels-to-declare-records).

3. Une fois l’étiquette créée, les options permettant de la publier s’affichent. Appliquez automatiquement l’étiquette, ou enregistrez-la simplement : sélectionnez **Appliquer automatiquement cette étiquette à un type spécifique de contenu**, puis sélectionnez **Terminé** pour démarrer l’assistant à la création d’attribution automatique d’étiquettes qui vous conduit directement à l’étape 2 de la procédure suivante.

Pour modifier une étiquette existante, sélectionnez-la, puis sélectionnez **Modifier l’étiquette** pour démarrer l’assistant à l’édition de rétention qui vous permet de modifier les descriptions d’étiquettes et les [paramètres éligibles](#updating-retention-labels-and-their-policies) à partir de l’étape 2.

### <a name="step-2-create-an-auto-apply-policy"></a>Étape 2 : créer une stratégie d’application automatique

Lorsque vous créez une stratégie d’application automatique, vous sélectionnez une étiquette de rétention pour l’appliquer automatiquement à du contenu, en fonction des conditions spécifiées.

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), accédez à l’un des emplacements suivants :
    
    - Si vous utilisez la gestion des enregistrements : **Gouvernance d’informations** :
        - **Solutions** > **Gestion des enregistrements** > **Stratégies des étiquettes** onglet > **Auto-appliquer une étiquette**
    
    - Si vous n’utilisez pas la gestion des enregistrements :
        - **Solutions** > **Gouvernance d’informations** > **Stratégies des étiquettes** onglet > **Auto-appliquer une étiquette**
    
    Votre option ne s’affiche pas immédiatement ? Sélectionnez tout d’abord **Afficher tout**. 

2. Suivez les invites de l’assistant à la création d’attribution automatique d’étiquettes.
    
    Pour plus d’informations sur la configuration des conditions qui appliquent automatiquement l’étiquette de rétention, voir la section [Configuration des conditions d’application automatique des étiquettes de rétention](#configuring-conditions-for-auto-apply-retention-labels) sur cette page.
    
    Pour plus d’informations sur la prise en charge des emplacements par des étiquettes de rétention, voir la section [Étiquettes de rétention et emplacements](retention.md#retention-label-policies-and-locations).

Pour modifier une stratégie d’application automatique d’étiquettes existante, sélectionnez-la pour démarrer l’assistant à la modification de stratégie de rétention qui vous permet de modifier l’étiquette de rétention sélectionnée et les [paramètres éligibles](#updating-retention-labels-and-their-policies) à partir de l’étape 2.

Une fois le contenu étiqueté à l'aide d'une stratégie d'étiquette d'application automatique, l'étiquette appliquée ne peut pas être automatiquement supprimée ou modifiée en modifiant le contenu ou la stratégie, ou par une nouvelle stratégie d'étiquette d'application automatique. Pour plus d'informations, voir [Une seule étiquette de rétention à la fois](retention.md#only-one-retention-label-at-a-time).

### <a name="configuring-conditions-for-auto-apply-retention-labels"></a>Configuration des conditions d’application automatique des étiquettes de rétention

Vous pouvez appliquer automatiquement des étiquettes de rétention au contenu quand celui-ci inclut :

- [Types spécifiques d’informations sensibles](#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)

- [Mots clés spécifiques ou propriétés pouvant faire l’objet d’une recherche qui correspondent à une requête que vous créez](#auto-apply-labels-to-content-with-keywords-or-searchable-properties)

- [Correspondance pour les classifieurs entraînables](#auto-apply-labels-to-content-by-using-trainable-classifiers)

Utilisez le tableau suivant pour identifier quand les étiquettes de rétention peuvent être automatiquement appliquées aux éléments pour Exchange :

|Condition|Éléments en transit (envoyés ou reçus) |Éléments existants (données au repos)|
|:-----|:-----|:-----|
|Types d’informations sensibles – intégrés| Oui | Non |
|Types d’informations sensibles – personnalisés| Oui | Non |
|Mots clés spécifiques ou propriétés pouvant faire l’objet d’une recherche| Oui |Oui |
|Classifieurs pouvant être formés| Oui | Oui (six derniers mois uniquement) |

Utilisez le tableau suivant pour identifier quand les étiquettes de rétention peuvent être automatiquement appliquées aux éléments pour SharePoint et OneDrive :

|Condition|Éléments modifiés ou nouveaux |Éléments existants (données au repos)|
|:-----|:-----|:-----|
|Types d’informations sensibles – intégrés| Oui | Oui |
|Types d’informations sensibles – personnalisés| Oui | Non |
|Mots clés spécifiques ou propriétés pouvant faire l’objet d’une recherche| Oui |Oui |
|Classifieurs pouvant être formés| Oui | Oui (six derniers mois uniquement) |

En outre, les éléments SharePoint qui sont dans les brouillons ou qui n’ont jamais été publiés ne sont pas pris en charge pour ce scénario.

#### <a name="auto-apply-labels-to-content-with-specific-types-of-sensitive-information"></a>Application automatique d’étiquettes au contenu incluant des types spécifiques d’informations sensibles

> [!IMPORTANT]
> Pour les e-mails que vous appliquez automatiquement en identifiant des informations sensibles, il n'est pas possible d'étendre la stratégie pour inclure ou exclure des destinataires spécifiques ; cette configuration de stratégie prend uniquement en charge le paramètre **Tous les destinataires**. Spécifique à cette configuration de stratégie, **Tous les destinataires** incluent les boîtes aux lettres des groupes Microsoft 365.
> 
> Également spécifique à cette configuration de stratégie, si vous sélectionnez l’emplacement des groupes **Microsoft 365,** seuls les sites SharePoint connectés à un groupe Microsoft 365 sont inclus et non les boîtes aux lettres des groupes Microsoft 365.

Lorsque vous créez des étiquettes de rétention d’application automatique pour des informations sensibles, vous voyez s’afficher la même liste de modèles de stratégie que lorsque vous créez une stratégie de protection contre la perte de données. Chaque modèle est préconfiguré pour rechercher des types spécifiques d’informations sensibles. Dans l’exemple suivant, les types d’informations sensibles proviennent de la catégorie **Confidentialité** et du modèle **Informations d’identification personnelle (PII) des États-Unis** :

![Modèles de stratégies avec des types d’informations sensibles](../media/sensitive-info-configuration.png)

Pour plus d’informations sur les types d’informations sensibles, voir les [définitions d’entités de types d’informations sensibles](sensitive-information-type-entity-definitions.md). Actuellement, les [correspondances exactes de données](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) et les [empreintes digitales de documents](document-fingerprinting.md) ne sont pas prises en charge pour ce scénario.

Après avoir sélectionné un modèle de stratégie, vous pouvez ajouter ou supprimer tous les types d’informations sensibles, et vous pouvez modifier le niveau de confiance et le nombre d’instances. Dans l’exemple de capture d’écran précédent, ces options ont été modifiées afin qu’une étiquette de rétention soit appliquée automatiquement uniquement lorsque :
  
- Le type d'informations sensibles détectées a une précision de correspondance (ou [niveau de confiance](sensitive-information-type-learn-about.md#more-on-confidence-levels)) d'au moins **une confiance moyenne** pour deux des types d'informations sensibles et **une confiance élevée** pour un. De nombreux types d'informations sensibles sont définis avec plusieurs modèles, où un modèle avec une précision de correspondance plus élevée nécessite plus de preuves à trouver (comme des mots-clés, des dates ou des adresses), tandis qu'un modèle avec une précision de correspondance plus faible nécessite moins de preuves. Plus le niveau de confiance est bas, plus il est facile pour le contenu de correspondre à la condition, mais avec un potentiel de plus de faux positifs.

- Le contenu comprend entre 1 et 9 instances de n’importe quel de ces trois types d’informations sensibles. La valeur par défaut de **à** est **N’importe lequel**.

Pour plus d’informations sur ces options, reportez-vous aux instructions suivantes de la documentation DLP : [Affiner les réglages pour rendre la correspondance plus ou moins précise](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

Lorsque vous utilisez des types d’informations sensibles pour appliquer automatiquement des étiquettes de rétention :

- Si vous utilisez des types d’informations sensibles personnalisés, ceux-ci ne peuvent pas étiqueter automatiquement des éléments existants dans SharePoint et OneDrive.

- Pour les e-mails, vous ne pouvez pas sélectionner des destinataires spécifiques à inclure ou exclure ; seul le **paramètre Tous les destinataires** est pris en charge et pour cette configuration uniquement, il inclut les boîtes aux lettres de Microsoft 365 groupes. 

#### <a name="auto-apply-labels-to-content-with-keywords-or-searchable-properties"></a>Application automatique d’étiquettes au contenu comprenant des mots clés ou des propriétés pouvant faire l’objet d’une recherche

Vous pouvez appliquer automatiquement des étiquettes au contenu à l’aide d’une requête qui contient des mots, des phrases ou des valeurs de propriétés pouvant faire l’objet d’une recherche. Vous pouvez affiner votre requête en utilisant des opérateurs de recherche tels que et, ou et non.

![Éditeur de requête.](../media/new-retention-query-editor.png)

Pour plus d’informations sur la syntaxe de requête qui utilise le langage de requête de mot clé (KQL), consultez [Référence de syntaxe de langage de requête de mot clé (KQL)](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

Les stratégies d’application automatique basées sur une requête utilisent le même index de recherche que la recherche de contenu eDiscovery pour identifier du contenu. Pour plus d’informations sur ces propriétés utilisables dans une requête, consultez [Requêtes par mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).

Éléments à prendre en compte lorsque vous utilisez des mots clés ou des propriétés utilisables dans une requête pour appliquer automatiquement des étiquettes de rétention

- Pour SharePoint, les propriétés analysées et les propriétés personnalisées ne sont pas prises en charge pour ces requêtes KQL et vous devez utiliser uniquement des propriétés gérées prédéfinies. Toutefois, vous pouvez utiliser des mappages au niveau du client avec les propriétés gérées prédéfinies qui sont activées comme affinements par défaut (RefinableDate00-19, RefinableString00-99, RefinableInt00-49, RefinableDecimals00-09 et RefinableDouble00-09). Pour plus d’informations, consultez[vue d’ensemble des propriétés analysées et gérées dans SharePoint Server](/SharePoint/technical-reference/crawled-and-managed-properties-overview)et pour obtenir des instructions, consultez [créer une propriété gérée](/sharepoint/manage-search-schema#create-a-new-managed-property).

- Si vous mappez une propriété personnalisée à l’une des propriétés d’affinement, attendez 24 heures avant de l’utiliser dans votre requête KQL pour une étiquette de rétention.

- Bien que les propriétés gérées de SharePoint puissent être renommées à l’aide d’alias, ne les utilisez pas pour les requêtes KQL dans vos étiquettes. Spécifiez toujours le nom réel de la propriété gérée (par exemple, « RefinableString01 »).

- Pour rechercher les valeurs qui contiennent des espaces ou des caractères spéciaux, utilisez les guillemets (`" "`) pour contenir la phrase; par exemple `subject:"Financial Statements"`.

- Utilisez la propriété *DocumentLink* au lieu de *Path* pour faire correspondre un élément en fonction de son URL. 

- Les recherches par caractères génériques suffixées (telles que `*cat`) ou les recherches par caractères génériques de sous-chaîne (telles que `*cat*`) ne sont pas prises en charge. Cependant, les recherches par caractères génériques suffixées (telles que `cat*`) sont prises en charge.

- Sachez que les éléments partiellement indexés peuvent être responsables du fait de ne pas étiqueter les éléments que vous attendez, ou d'étiqueter des éléments que vous pensez être exclus de l'étiquetage lorsque vous utilisez l'opérateur NOT. Pour plus d'informations, voir [Éléments partiellement indexés dans la recherche de contenu](partially-indexed-items-in-content-search.md).


Exemples de requêtes :

| Charge de travail | Exemple |
|:-----|:-----|
|Exchange   | `subject:"Financial Statements"` |
|Exchange   | `recipients:garthf@contoso.com` |
|SharePoint | `contenttype:document` |
|SharePoint | `site:https://contoso.sharepoint.com/sites/teams/procurement AND contenttype:document`|
|Exchange ou SharePoint | `"customer information" OR "private"`|

Exemples plus complexes :

La requête suivante pour SharePoint identifie des documents Word ou des feuilles de calcul Excel lorsque ces fichiers contiennent les mots clés **mot de passe**, **mots de passe** ou **pw**:

```
(password OR passwords OR pw) AND (filetype:doc* OR filetype:xls*)
```

La requête Exchange suivante identifie tout document Word ou PDF contenant le mot **accord de confidentialité** ou l’expression **contrat de non-divulgation** lorsque ces documents sont joints à un e-mail :

```
(nda OR "non disclosure agreement") AND (attachmentnames:.doc* OR attachmentnames:.pdf)
```

La requête SharePoint suivante identifie les documents qui contiennent un numéro de carte de crédit : 

```
sensitivetype:"credit card number"
```

La requête suivante contient des mots clés courants pour vous aider à identifier les documents ou les e-mails qui contiennent du contenu juridique :

```
ACP OR (Attorney Client Privilege*) OR (AC Privilege)
```

La requête suivante contient des mots clés courants pour vous aider à identifier les documents ou les e-mails des ressources humaines : 

```
(resume AND staff AND employee AND salary AND recruitment AND candidate)
```

Notez que ce dernier exemple utilise la pratique recommandée qui consiste à toujours inclure des opérateurs entre les mots clés. Un espace entre des mots-clés (ou deux expressions de valeur de propriété) revient au même que l’utilisation de l’opérateur AND. En ajoutant toujours des opérateurs, il est plus facile de voir que cet exemple de requête identifie uniquement le contenu qui contient tous ces mots clés, au lieu du contenu contenant tous les mots clés. Si vous avez l’intention d’identifier le contenu contenant l’un des mots clés, spécifiez ou au lieu de et. Comme cet exemple montre, lorsque vous spécifiez toujours les opérateurs, il est plus facile d’interpréter correctement la requête. 

##### <a name="microsoft-teams-meeting-recordings"></a>Enregistrements de réunion Microsoft Teams

> [!NOTE]
> La possibilité de conserver et de supprimer les enregistrements de réunions Teams et ne fonctionnera pas avant la sauvegarde des enregistrements dans OneDrive ou SharePoint. Pour plus d’informations, consultez [Utiliser OneDrive Entreprise et SharePoint Online ou Stream pour les enregistrements de réunion](/MicrosoftTeams/tmr-meeting-recording-change).

Pour identifier les enregistrements de réunion Microsoft Teams stockés dans les comptes OneDrive des utilisateurs ou dans SharePoint, spécifiez les éléments suivants pour **l’éditeur de requête de mot clé**:

```
ProgID:Media AND ProgID:Meeting
```

La plupart du temps, les enregistrements de réunion sont enregistrés dans OneDrive, mais pour les réunions de canal, ils sont enregistrés dans SharePoint.

##### <a name="identify-files-and-emails-that-have-a-sensitivity-label"></a>Identifiez les fichiers et les e-mails qui ont une étiquette de sensibilité

Pour identifier les fichiers dans les e-mails Microsoft Office SharePoint Online ou OneDrive et Exchange auxquels une [étiquette de confidentialité](sensitivity-labels.md) spécifique est appliquée, spécifiez les éléments suivants pour **l'éditeur de requêtes par mot-clé** :

```
InformationProtectionLabelId:<GUID>
```

Pour trouver le GUID, utilisez [l'applet de commande](/powershell/module/exchange/get-label) Get-Label de [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell) :

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid
````

#### <a name="auto-apply-labels-to-content-by-using-trainable-classifiers"></a>Appliquer automatiquement des étiquettes au contenu à l’aide de classifieurs entraînables

Lorsque vous choisissez l’option de classifieur entraînable, vous pouvez sélectionner un classifieur intégré ou un classifieur personnalisé. Les classifieurs intégrés incluent : **CV**, **SourceCode**, **Harcèlement ciblé**, **Blasphème** et la **Menace** :

![Sélectionnez un classificateur à entraîner.](../media/retention-label-classifers.png)

> [!CAUTION]
> Nous déprécions le **langage inconvenant** classifieur intégré, car il génère un grand nombre de faux positifs. N’utilisez pas ce classifieur intégré et si vous l’utilisez actuellement, vous devez déplacer vos processus métier. Nous vous recommandons d’utiliser les classifieurs intégrés de **Harcèlement ciblée** , de **blasphème** et de **Menace** à la place.

Pour appliquer automatiquement une étiquette à l’aide de cette option, les sites et boîtes aux lettres SharePoint doivent avoir au moins 10 Mo de données.

Pour plus d’informations sur les classifieurs avec capacité de formation, consultez [Découvrez les classifieurs avec capacité de formation](classifier-learn-about.md).

> [!TIP]
> Si vous utilisez des classifieurs avec capacité de formation pour Exchange, consultez [Comment recycler un classifieur dans l’explorateur de contenu](classifier-how-to-retrain-content-explorer.md).

Lorsque vous utilisez des classificateurs pouvant apprendre pour appliquer automatiquement des étiquettes de rétention :

- Vous ne pouvez pas étiqueter automatiquement des éléments qui ont plus de six mois dans SharePoint ou OneDrive.

## <a name="how-long-it-takes-for-retention-labels-to-take-effect"></a>Délai d’activation des étiquettes de rétention

Lorsque vous appliquez automatiquement des étiquettes de rétention, l’application de ces étiquettes à ce contenu peut prendre jusqu’à sept jours.
  
![Diagramme indiquant quand les étiquettes d’application automatique prennent effet.](../media/b8c00657-477a-4ade-b914-e643ef97a10d.png)

Si les étiquettes attendues n’apparaissent pas après sept jours, consultez l’**État** de la stratégie d’application automatique en sélectionnant celle-ci dans la page des **Stratégies d’étiquette** dans le centre de conformité. Si vous voyez l’état de **Désactivé (erreur)** et dans les détails des emplacements, consultez un message indiquant qu’il prend plus de temps que prévu pour déployer la stratégie (pour SharePoint) ou essayez de redéployer la stratégie (pour OneDrive), essayez d’exécuter la commande PowerShell [RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) pour réessayer la distribution de la stratégie :

1. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez la commande suivante :
    
    ```PowerShell
    Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
    ```

## <a name="updating-retention-labels-and-their-policies"></a>Mise à jour des étiquettes de rétention et de leurs stratégies

Lorsque vous modifiez une étiquette de rétention ou une stratégie d’application automatique et que l’étiquette de rétention est déjà appliquée au contenu, vos paramètres mis à jour sont automatiquement appliqués à ce contenu, en plus du contenu nouvellement identifié.

Certains paramètres ne peuvent pas être modifiés une fois l’étiquette ou la stratégie créée et enregistrée, notamment :
- Étiquette de rétention et le nom de la stratégie, et les paramètres de rétention à l’exception de la période de rétention. Cependant, vous ne pouvez pas modifier la période de rétention lorsque la période de rétention est basée sur la période d’étiquetage des éléments.
- Option de marquage des éléments comme enregistrement.

### <a name="deleting-retention-labels"></a>Suppression des étiquettes de rétention.

Vous pouvez supprimer des étiquettes de rétention qui ne sont pas actuellement incluses dans les stratégies d’étiquette de rétention, qui ne sont pas configurées pour la rétention basée sur des événements, ou qui marquent des éléments comme enregistrements réglementaires.

Pour les étiquettes de rétention que vous pouvez supprimer, si elles ont été appliquées à des éléments, la suppression échoue et un lien vers l’explorateur de contenu permettant d’identifier les éléments étiquetés s’affiche.

Toutefois, l’affichage des éléments étiquetés par l’explorateur de contenu peut prendre deux jours maximum. Dans ce scénario, l’étiquette de rétention pourrait être supprimée sans l’affichage du lien vers l’explorateur de contenu.

## <a name="locking-the-policy-to-prevent-changes"></a>Verrouillage de la stratégie pour empêcher toute modification

Si vous avez besoin de vérifier que personne ne peut désactiver la stratégie, supprimer la stratégie ou la rendre moins restrictive, veuillez consulter la rubrique [Utiliser le Verrou de Conservation pour restreindre les modifications apportées aux stratégies de rétention et aux stratégies d’étiquette de rétention](retention-preservation-lock.md).

## <a name="next-steps"></a>Prochaines étapes

Consultez [Utiliser les étiquettes de rétention pour gérer le cycle de vie des documents stockés dans SharePoint](auto-apply-retention-labels-scenario.md) pour un exemple de scénario qui utilise une stratégie d’application automatique avec des propriétés gérées dans SharePoint et la rétention basée sur les événements pour démarrer la période de rétention.
