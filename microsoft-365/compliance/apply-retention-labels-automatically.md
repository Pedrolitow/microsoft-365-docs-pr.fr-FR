---
title: Appliquer automatiquement une étiquette de rétention aux éléments Microsoft 365
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
- purview-compliance
- tier1
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Créez des stratégies de rétention d’étiquetage automatique afin de pouvoir appliquer automatiquement des étiquettes pour conserver ce dont vous avez besoin et supprimer ce que vous n’avez pas
ms.openlocfilehash: 2320b7d882c999bace37bb3aeea79f23926e0969
ms.sourcegitcommit: 1f4c51d022d1cfb6c194bf0f0af9c2841c781d68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2022
ms.locfileid: "68574074"
---
# <a name="automatically-apply-a-retention-label-to-retain-or-delete-content"></a>Application automatique d’une étiquette de rétention pour conserver ou supprimer du contenu

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> This scenario is not supported for [regulatory records](records-management.md#records) or default labels for an organizing structure such as a document set or library in SharePoint, or a folder in Exchange. These scenarios require a [published retention label policy](create-apply-retention-labels.md).

One of the most powerful features of [retention labels](retention.md) is the ability to apply them automatically to content that matches specified conditions. In this case, people in your organization don't need to apply the retention labels. Microsoft 365 does the work for them.

Les étiquettes de rétention appliquées automatiquement sont puissantes pour les raisons suivantes :

- Vous n’avez pas besoin de former les utilisateurs concernant l’ensemble de vos classifications.
- Vous n’avez pas à dépendre des utilisateurs pour classer tout le contenu correctement.
- Les utilisateurs n’ont plus besoin de connaître les stratégies de gouvernance des données : ils peuvent se concentrer sur leur travail.

Vous pouvez appliquer automatiquement des étiquettes de rétention à du contenu lorsque celui-ci ne contient pas encore d’étiquette de rétention appliquée et des informations sensibles, des mots clés, des propriétés pouvant faire l’objet d’une recherche ou une correspondance pour des [classifieurs pouvant être formés](classifier-get-started-with.md). Désormais en prévisualisation, vous pouvez également appliquer automatiquement une étiquette de rétention aux pièces jointes dans le cloud qui sont stockées dans SharePoint ou OneDrive.

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
> - Application d’une étiquette de rétention pour les e-mails à l’aide de règles Outlook
>
> Pour ces scénarios, consultez [Publier les étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de votre organisation dispose de toutes les autorisations pour créer et gérer les étiquettes de rétention et leurs stratégies. Si vous ne vous connectez pas en tant qu’administrateur général, consultez les informations d’autorisation pour la [gestion des enregistrements](get-started-with-records-management.md#permissions) ou la [gestion du cycle de vie des données](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels), en fonction de la solution que vous utilisez.

Vérifiez que vous avez [créé les étiquettes de rétention](file-plan-manager.md#create-retention-labels)que vous souhaitez appliquer aux éléments.

## <a name="how-to-create-an-auto-apply-retention-label-policy"></a>Comment créer une stratégie d’étiquette de rétention d’application automatique

Déterminez avant de créer votre stratégie d’étiquette de rétention si elle sera **adaptative** ou **statique.** Pour plus d’informations, voir étendues de stratégie adaptative ou statique [pour la rétention.](retention.md#adaptive-or-static-policy-scopes-for-retention) Si vous décidez d’utiliser une stratégie adaptative, vous devez créer une ou plusieurs étendues adaptatives avant de créer votre stratégie d’étiquette de rétention, puis les sélectionner au cours du processus de création de stratégie d’étiquette de rétention. Pour obtenir des instructions, [consultez les informations de configuration pour les étendues adaptatives.](retention-settings.md#configuration-information-for-adaptive-scopes)

Lorsque vous créez une stratégie d’application automatique, vous sélectionnez une étiquette de rétention pour l’appliquer automatiquement à du contenu, en fonction des conditions spécifiées.

1. Dans le [Centre de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à l’un des emplacements suivants :

    - Si vous utilisez la gestion des enregistrements :
        - **Solutions** \> **Gestion des enregistrements** \> **onglet** Stratégies des étiquettes\> **Appliquer automatiquement une étiquette**

    - Si vous utilisez la solution de gestion du cycle de vie des données :
        - **Solutions** \> **Gestion du cycle de vie des** \> données **Microsoft 365** \> **Onglet Stratégies** d’étiquette \> **- Appliquer automatiquement une étiquette**

    Vous ne voyez pas immédiatement votre solution dans le volet de navigation? Sélectionnez tout d’abord **Afficher tout**.

2. Entrez un nom et une description pour cette stratégie d’étiquetage automatique, puis sélectionnez **Suivant**.

3. Pour choisir le type de contenu à appliquer à cette **étiquette,** sélectionnez l’une des conditions disponibles. Pour plus d’informations sur la configuration des conditions qui appliquent automatiquement l’étiquette de rétention, voir la section [Configuration des conditions d’application automatique des étiquettes de rétention](#configuring-conditions-for-auto-apply-retention-labels) sur cette page.

4. Pour choisir **le type** de stratégie de rétention à créer, sélectionnez **Adaptatif** ou **Statique,** en fonction du choix que vous avez effectué à partir des [instructions](#before-you-begin) avant de commencer. Si vous n’avez pas encore créé **d’étendues adaptatives, vous pouvez sélectionner Adaptive**, mais comme il n’y aura aucune étendue adaptative à sélectionner, vous ne pourrez pas terminer l’Assistant avec cette option.

5. En fonction de l’étendue sélectionnée :

    - Si vous **avez** choisi Adaptatif : dans la page Choisir les étendues et les **emplacements** de stratégie adaptative, sélectionnez Ajouter des **étendues** et sélectionnez une ou plusieurs étendues adaptatives qui ont été créées. Sélectionnez ensuite un ou plusieurs emplacements. Les emplacements que vous pouvez sélectionner dépendent des [types d’étendue](retention-settings.md#configuration-information-for-adaptive-scopes) ajoutés. Par exemple, si vous avez uniquement **ajouté un type d’étendue** d’utilisateur, vous pourrez sélectionner Exchange **courrier** électronique, mais pas SharePoint **sites.**
    
    - Si vous avez choisi **Statique :** dans **la** page Choisir des emplacements pour activer ou désactiver l'un des emplacements. Vous pouvez laisser pour chaque emplacement la valeur par défaut [Appliquer la stratégie à l’intégralité de l’emplacement](retention-settings.md#a-policy-that-applies-to-entire-locations) ou [Spécifier des inclusions et des exclusions](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).

    Pour plus d’informations sur les choix d’emplacement, voir [Emplacements.](retention-settings.md#locations)

6. Suivez les instructions de l'assistant pour sélectionner une étiquette de conservation, puis révisez et soumettez vos choix de configuration.

Pour modifier une stratégie d’étiquette de rétention existante (le type de stratégie est **Appliquer automatiquement**), sélectionnez-la, puis sélectionnez l’option **Modifier** pour démarrer la configuration de l’action **Modifier la stratégie de rétention**.

After content is labeled by using an auto-apply label policy, the applied label can't be automatically removed or changed by changing the content or the policy, or by a new auto-apply label policy. For more information, see [Only one retention label at a time](retention.md#only-one-retention-label-at-a-time).

> [!NOTE]
> Une stratégie d’application automatique des étiquettes de rétention ne remplacera jamais une étiquette de rétention existante appliquée au contenu. Si vous souhaitez réétiqueter du contenu à l’aide des conditions que vous configurez, vous devez supprimer manuellement l’étiquette de rétention actuelle du contenu existant.

### <a name="configuring-conditions-for-auto-apply-retention-labels"></a>Configuration des conditions d’application automatique des étiquettes de rétention

Vous pouvez appliquer automatiquement des étiquettes de rétention au contenu quand celui-ci inclut :

- [Types spécifiques d’informations sensibles](#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)

- [Mots clés spécifiques ou propriétés pouvant faire l’objet d’une recherche qui correspondent à une requête que vous créez](#auto-apply-labels-to-content-with-keywords-or-searchable-properties)

- [Correspondance pour les classifieurs entraînables](#auto-apply-labels-to-content-by-using-trainable-classifiers)

Vous pouvez également appliquer automatiquement des étiquettes de rétention aux pièces [jointes sur le nuage nouvellement partagées.](#auto-apply-labels-to-cloud-attachments)

Lorsque vous configurez les étiquettes de rétention pour qu'elles s'appliquent automatiquement sur la base d'informations sensibles, de mots-clés ou de propriétés interrogeables, ou de classificateurs entraînables, utilisez le tableau suivant pour identifier quand les étiquettes de rétention peuvent être appliquées automatiquement.

Exchange :

|Condition|Éléments en transit (envoyés ou reçus) |Éléments existants (données au repos)|
|:-----|:-----|:-----|
|Types d’informations sensibles – intégrés| Oui | Non |
|Types d’informations sensibles – personnalisés| Oui | Non |
|Mots clés spécifiques ou propriétés pouvant faire l’objet d’une recherche| Oui |Oui |
|Classifieurs pouvant être formés| Oui | Oui (six derniers mois uniquement) |

SharePoint et OneDrive:

|Condition|Éléments modifiés ou nouveaux |Éléments existants |
|:-----|:-----|:-----|
|Types d’informations sensibles – intégrés| Oui | Oui |
|Types d’informations sensibles – personnalisés| Oui | Non |
|Mots clés spécifiques ou propriétés pouvant faire l’objet d’une recherche| Oui |Oui |
|Classifieurs pouvant être formés| Oui | Oui (six derniers mois uniquement) |

En outre, les éléments SharePoint qui sont dans les brouillons ou qui n’ont jamais été publiés ne sont pas pris en charge pour ce scénario.

#### <a name="auto-apply-labels-to-content-with-specific-types-of-sensitive-information"></a>Application automatique d’étiquettes au contenu incluant des types spécifiques d’informations sensibles

> [!IMPORTANT]
> Pour les e-mails que vous appliquez automatiquement en identifiant des informations sensibles, toutes les boîtes aux lettres sont automatiquement incluses, ce qui inclut les boîtes aux lettres de Microsoft 365 groupes. Par défaut, l’emplacement de **messagerie Exchange** n’est pas sélectionné pour les étendues adaptatives lorsque vous disposez de cette configuration. Même si vous pouvez sélectionner l’emplacement, les étiquettes de rétention ne s’appliquent pas aux éléments Exchange.
>
> Bien que les boîtes aux lettres de groupe soient généralement incluses en sélectionnant l’emplacement des groupes **Microsoft 365,** pour cette configuration de stratégie spécifique, l’emplacement des groupes inclut uniquement les sites SharePoint connectés à un groupe Microsoft 365.

Lorsque vous créez des stratégies d’étiquette de rétention d’application automatique pour des informations sensibles, vous voyez s’afficher la même liste de modèles de stratégie que lorsque vous créez une stratégie de protection contre la perte de données (DLP) Microsoft Purview. Chaque modèle est préconfiguré pour rechercher des types spécifiques d’informations sensibles. Dans l’exemple suivant, les types d’informations sensibles proviennent de la catégorie **Confidentialité** et du modèle **Informations d’identification personnelle (PII) des États-Unis** :

![Modèles de stratégies avec des types d’informations sensibles](../media/sensitive-info-configuration.png)

Pour en savoir plus sur les types d’informations de confidentialité, consultez [En savoir plus sur les types d’informations sensibles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types). Actuellement, les [types d’informations sensibles basés sur la correspondance exacte des données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) et [l'empreinte digitale des documents](document-fingerprinting.md) ne sont pas prises en charge pour ce scénario.

After you select a policy template, you can add or remove any types of sensitive information, and you can change the confidence level and instance count. In the previous example screenshot, these options have been changed so that a retention label will be auto-applied only when:

- The type of sensitive information that's detected has a match accuracy (or [confidence level](sensitive-information-type-learn-about.md#more-on-confidence-levels)) of at least **Medium confidence** for two of the sensitive info types, and **High confidence** for one. Many sensitive information types are defined with multiple patterns, where a pattern with a higher match accuracy requires more evidence to be found (such as keywords, dates, or addresses), while a pattern with a lower match accuracy requires less evidence. The lower the confidence level, the easier it is for content to match the condition but with the potential for more false positives.

- Le contenu comprend entre 1 et 9 instances de n’importe quel de ces trois types d’informations sensibles. La valeur par défaut de **à** est **N’importe lequel**.

Pour plus d’informations sur ces options, reportez-vous aux instructions suivantes de la documentation DLP : [Affiner les réglages pour rendre la correspondance plus ou moins précise](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

> [!IMPORTANT]
> Les types d’informations sensibles ont deux manières différentes de définir les paramètres de nombre d’instances uniques maximum. Pour plus d’informations, voir [Nombre d’instances prises en charge pour SIT](sit-limits.md#instance-count-supported-values-for-sit).

Lorsque vous utilisez des types d’informations sensibles pour appliquer automatiquement des étiquettes de rétention :

- Si vous utilisez des types d’informations sensibles personnalisés, ceux-ci ne peuvent pas étiqueter automatiquement des éléments existants dans SharePoint et OneDrive.

- Pour les e-mails, vous ne pouvez pas sélectionner des destinataires spécifiques à inclure ou exclure ; seul le **paramètre Tous les destinataires** est pris en charge et pour cette configuration uniquement, il inclut les boîtes aux lettres de Microsoft 365 groupes.

#### <a name="auto-apply-labels-to-content-with-keywords-or-searchable-properties"></a>Application automatique d’étiquettes au contenu comprenant des mots clés ou des propriétés pouvant faire l’objet d’une recherche

You can auto-apply labels to content by using a query that contains specific words, phrases, or values of searchable properties. You can refine your query by using search operators such as AND, OR, and NOT.

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

- Be aware that partially indexed items can be responsible for not labeling items that you're expecting, or labeling items that you're expecting to be excluded from labeling when you use the NOT operator. For more information, see [Partially indexed items in Content Search](partially-indexed-items-in-content-search.md).

- Nous vous recommandons de ne pas utiliser d’espaces entre les mots dans les valeurs RefinableStrings sur des documents. RefinableString n’est pas une propriété de saut de mot.

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

```KQL
(password OR passwords OR pw) AND (filetype:doc* OR filetype:xls*)
```

La requête Exchange suivante identifie tout document Word ou PDF contenant le mot **accord de confidentialité** ou l’expression **contrat de non-divulgation** lorsque ces documents sont joints à un e-mail :

```KQL
(nda OR "non disclosure agreement") AND (attachmentnames:.doc* OR attachmentnames:.pdf)
```

La requête SharePoint suivante identifie les documents qui contiennent un numéro de carte de crédit :

```KQL
sensitivetype:"credit card number"
```

La requête suivante contient des mots clés courants pour vous aider à identifier les documents ou les e-mails qui contiennent du contenu juridique :

```KQL
ACP OR (Attorney Client Privilege*) OR (AC Privilege)
```

La requête suivante contient des mots clés courants pour vous aider à identifier les documents ou les e-mails des ressources humaines :

```KQL
(resume AND staff AND employee AND salary AND recruitment AND candidate)
```

Notez que ce dernier exemple utilise la pratique recommandée qui consiste à toujours inclure des opérateurs entre les mots clés. Un espace entre des mots-clés (ou deux expressions property:value) revient au même que l’utilisation de l’opérateur AND. En ajoutant toujours des opérateurs, il est plus facile de voir que cet exemple de requête identifie uniquement le contenu qui contient tous ces mots clés, au lieu du contenu contenant tous les mots clés. Si vous avez l’intention d’identifier le contenu contenant l’un des mots clés, spécifiez ou au lieu de et. Comme cet exemple montre, lorsque vous spécifiez toujours les opérateurs, il est plus facile d’interpréter correctement la requête.

##### <a name="microsoft-teams-meeting-recordings"></a>Enregistrements de réunion Microsoft Teams

> [!NOTE]
> La possibilité de conserver et de supprimer les enregistrements de réunions Teams et ne fonctionnera pas avant la sauvegarde des enregistrements dans OneDrive ou SharePoint. Pour plus d’informations, consultez [Utiliser OneDrive Entreprise et SharePoint Online ou Stream pour les enregistrements de réunion](/MicrosoftTeams/tmr-meeting-recording-change).

Pour identifier les enregistrements de réunion Microsoft Teams stockés dans les comptes OneDrive des utilisateurs ou dans SharePoint, spécifiez les éléments suivants pour **l’éditeur de requête de mot clé**:

```KQL
ProgID:Media AND ProgID:Meeting
```

Most of the time, meeting recordings are saved to OneDrive. But for channel meetings, they are saved in SharePoint.

##### <a name="identify-files-and-emails-that-have-a-sensitivity-label"></a>Identifiez les fichiers et les e-mails qui ont une étiquette de sensibilité

Pour identifier les fichiers dans les e-mails Microsoft Office SharePoint Online ou OneDrive et Exchange auxquels une [étiquette de confidentialité](sensitivity-labels.md) spécifique est appliquée, spécifiez les éléments suivants pour **l'éditeur de requêtes par mot-clé** :

```KQL
InformationProtectionLabelId:<GUID>
```

Pour trouver le GUID, utilisez l’applet de commande [Get-Label](/powershell/module/exchange/get-label) du [PowerShell de sécurité et conformité](/powershell/exchange/scc-powershell):

```powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid
```

#### <a name="auto-apply-labels-to-content-by-using-trainable-classifiers"></a>Appliquer automatiquement des étiquettes au contenu à l’aide de classifieurs entraînables

> [!IMPORTANT]
> Actuellement, les classifieurs pouvant être formés pour l’étiquetage automatique ne peuvent pas être [utilisés avec des étendues adaptatives](retention.md#adaptive-or-static-policy-scopes-for-retention). Utilisez plutôt une étendue statique.

Lorsque vous choisissez l'option pour un classificateur entraînable, vous pouvez sélectionner un ou plusieurs classificateurs pré-entraînés ou personnalisés :

![Sélectionnez un classificateur à entraîner.](../media/retention-label-classifers.png)

Les classifieurs préentraînés disponibles sont souvent mis à jour. Il peut donc y avoir plus d’entrées à sélectionner que celles affichées dans cette capture d’écran.

Pour plus d’informations sur les classifieurs avec capacité de formation, consultez [Découvrez les classifieurs avec capacité de formation](classifier-learn-about.md).

Pour appliquer automatiquement une étiquette à l’aide de cette option, les sites SharePoint, ainsi que les boîtes aux lettres doivent avoir au moins 10 Mo de données.

> [!TIP]
> Si vous utilisez des classifieurs avec capacité de formation pour Exchange, consultez [Comment recycler un classifieur dans l’explorateur de contenu](classifier-how-to-retrain-content-explorer.md).

Lorsque vous utilisez des classificateurs pouvant apprendre pour appliquer automatiquement des étiquettes de rétention :

- Vous ne pouvez pas étiqueter automatiquement des éléments qui ont plus de six mois dans SharePoint ou OneDrive.

#### <a name="auto-apply-labels-to-cloud-attachments"></a>Appliquer automatiquement des étiquettes aux pièces jointes cloud

> [!NOTE]
> Cette option est en aperçu et est sujette à modifications.

Vous devrez peut-être utiliser cette option si vous devez capturer et conserver toutes les copies de fichiers dans votre client qui sont envoyées via les communications par les utilisateurs. Vous utilisez cette option conjointement avec les stratégies de rétention pour les services de communication eux-mêmes, Exchange et Teams.

> [!IMPORTANT]
> Lorsque vous sélectionnez une étiquette à utiliser pour appliquer automatiquement des **étiquettes de rétention pour les pièces jointes cloud**, assurez-vous que le paramètre de rétention des étiquettes démarre la période de rétention en fonction de l’étiquette des **éléments.**

Les pièces jointes cloud, parfois appelées pièces jointes modernes, sont un mécanisme de partage qui utilise des liens incorporés vers des fichiers stockés dans le nuage. Ils peuvent prendre en charge le stockage centralisé pour le contenu partagé avec des avantages collaboratifs, tels que le contrôle de version. Les pièces jointes cloud ne sont pas des copies jointes d’un fichier ou un lien de texte d’URL vers un fichier. Il peut s’avérer utile de consulter les listes de contrôle visuelles pour les pièces jointes cloud [Outlook](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-outlook) et [Teams](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-teams).

Lorsque vous choisissez l’option d’application d’une étiquette de rétention aux pièces jointes dans le cloud, à des fins de conformité, une copie de ce fichier est créée au moment du partage. L'étiquette de conservation que vous avez sélectionnée est alors appliquée à la copie qui peut ensuite être [identifiée à l'aide de l'eDiscovery](advanced-ediscovery-cloud-attachments.md). Les utilisateurs ne connaissent pas la copie stockée dans la bibliothèque de conservation et de préservation des données. L’étiquette de rétention n’est pas appliquée au message lui-même ou au fichier d’origine.

Si le fichier est modifié et partagé à nouveau, une nouvelle copie du fichier en tant que nouvelle version est enregistrée dans la bibliothèque de conservation et de préservation. Pour plus d’informations, notamment **sur la raison pour laquelle vous devez utiliser le paramètre** Lorsque les éléments ont été étiquetés, voir Comment fonctionne la rétention avec les pièces [jointes cloud](retention-policies-sharepoint.md#how-retention-works-with-cloud-attachments).

Les pièces jointes cloud prises en charge pour cette option sont des fichiers tels que des documents, des vidéos et des images qui sont stockés dans SharePoint et OneDrive. Pour Teams, les pièces jointes cloud partagées dans les messages de conversation et les canaux standard et privés sont pris en charge. Les pièces jointes cloud partagées sur les invitations aux réunions et les applications autres que Teams ou Outlook ne sont pas pris en charge. Les pièces jointes cloud doivent être partagées par les utilisateurs; les pièces jointes cloud envoyées via des bots ne sont pas pris en charge.

Bien que cela ne soit pas obligatoire pour cette option, nous vous recommandons de vous assurer que le traitement des versions est activé pour vos sites SharePoint et comptes OneDrive afin que la version partagée puisse être capturée avec précision. Si le jeu de versions n’est pas activé, la dernière version disponible est conservée. Les documents en brouillon ou qui n’ont jamais été publiés ne sont pas pris en charge.

Lorsque vous sélectionnez une étiquette à utiliser pour appliquer automatiquement des étiquettes **de rétention pour les pièces jointes cloud, assurez-vous que le paramètre de rétention des étiquettes démarre la période de** rétention en fonction de l’étiquette des **éléments.**

Lorsque vous configurez les emplacements de cette option, vous pouvez sélectionner :

- **SharePoint sites** pour les fichiers partagés stockés dans des sites de communication SharePoint, des sites d’équipe qui ne sont pas connectés par des groupes Microsoft 365 et des sites classiques.
- **Microsoft 365 groupes pour** les fichiers partagés stockés dans des sites d’équipe connectés Microsoft 365 groupes.
- OneDrive pour les fichiers **partagés** stockés dans les comptes de OneDrive.

Vous devrez créer des stratégies de rétention distinctes si vous souhaitez conserver ou supprimer les fichiers, messages électroniques ou messages Teams d’origine.

> [!NOTE]
> Si vous souhaitez que les pièces jointes dans le cloud conservées expirent en même temps que les messages qui les contenaient, configurez l’étiquette de rétention de manière à ce qu’elle soit conservée, puis supprimez les actions et les délais que vos stratégies de rétention pour Exchange et Teams.

À prendre en compte lors de l’application automatique d’étiquettes de rétention aux pièces jointes cloud :

- Seules les pièces jointes cloud nouvellement partagées seront automatiquement étiquetées pour la rétention.

- Lorsqu’un utilisateur est ajouté à une conversation Teams et qu’il a accès à l’historique complet de la conversation, cet historique peut inclure des pièces jointes cloud. S’ils ont été partagés dans les 48 heures suivant l’ajout de l’utilisateur à la conversation, les copies actuelles des pièces jointes cloud sont étiquetées automatiquement pour conservation. Les pièces jointes cloud partagées avant cette période ne sont pas prises en charge pour les utilisateurs nouvellement ajoutés.

- Les pièces jointes cloud partagées en dehors Teams et Outlook ne sont pas pris en charge.

- Les éléments suivants ne sont pas pris en charge en tant que pièces jointes cloud qui peuvent être conservées :
  - SharePoint sites, pages, listes, formulaires, dossiers, ensembles de documents et pages OneNote pages.
  - Fichiers partagés par les utilisateurs qui n’ont pas accès à ces fichiers au moment du partage.
  - Fichiers supprimés ou déplacés avant l’envoi de la pièce jointe cloud. Par exemple, un utilisateur copie et colle une pièce jointe partagée précédemment à partir d’un autre message, sans confirmer au préalable que le fichier est toujours disponible. Ou bien, quelqu’un envoie un ancien message lorsque le fichier est maintenant supprimé.
  - Fichiers partagés par des invités ou des utilisateurs externes à votre organisation
  - Fichiers dans les messages électroniques provisoires et les messages qui ne sont pas envoyés
  - Fichiers vides

## <a name="how-long-it-takes-for-retention-labels-to-take-effect"></a>Délai d’activation des étiquettes de rétention

Lorsque vous appliquez automatiquement des étiquettes de conservation basées sur des informations sensibles, des mots-clés ou des propriétés interrogeables, ou des classificateurs entraînables, l'application des étiquettes de conservation peut prendre jusqu'à sept jours :

![Diagramme indiquant quand les étiquettes d’application automatique prennent effet.](../media/retention-labels-autoapply-timings.png)

Si les étiquettes attendues n’apparaissent pas après sept jours, vérifiez l’**État** de la stratégie d’application automatique en sélectionnant celle-ci dans la page des **Stratégies d’étiquette** dans le portail de conformité Microsoft Purview. Si vous voyez l’état de **Désactivé (erreur)** et dans les détails des emplacements, consultez un message indiquant qu’il prend plus de temps que prévu pour déployer la stratégie (pour SharePoint) ou essayez de redéployer la stratégie (pour OneDrive), essayez d’exécuter la commande PowerShell [RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) pour réessayer la distribution de la stratégie :

1. [Se connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez la commande suivante :

    ```PowerShell
    Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
    ```

## <a name="updating-retention-labels-and-their-policies"></a>Mise à jour des étiquettes de rétention et de leurs stratégies

Pour appliquer automatiquement les politiques d'étiquetage de conservation qui sont configurées pour les informations sensibles, les mots-clés ou les propriétés recherchables, ou une correspondance pour les classificateurs entraînables : Lorsqu'une étiquette de conservation de la politique est déjà appliquée au contenu, un changement de configuration de l'étiquette et de la politique sélectionnées sera automatiquement appliqué à ce contenu en plus du contenu nouvellement identifié.

Pour les stratégies d’étiquette de rétention à appliquer automatiquement qui sont configurées pour les pièces jointes dans le cloud : étant donné que cette stratégie s’applique aux nouveaux fichiers partagés plutôt qu’aux fichiers existants, une modification de la configuration de l’étiquette et de la stratégie sélectionnées sera automatiquement appliquée au contenu nouvellement partagé uniquement.

Certains paramètres ne peuvent pas être modifiés une fois l’étiquette ou la stratégie créée et enregistrée, notamment :

- Noms pour les étiquettes de rétention et leurs stratégies, le type d’étendue (adaptatif ou statique) et les paramètres de rétention à l’exception de la période de rétention. Cependant, vous ne pouvez pas modifier la période de rétention lorsque la période de rétention est basée sur la période d’étiquetage des éléments.
- Option de marquage des éléments comme enregistrement.

### <a name="deleting-retention-labels"></a>Suppression des étiquettes de rétention.

Vous pouvez supprimer des étiquettes de rétention qui ne sont pas actuellement incluses dans les stratégies d’étiquette de rétention, qui ne sont pas configurées pour la rétention basée sur des événements, ou qui marquent des éléments comme enregistrements réglementaires.

Pour les étiquettes de rétention que vous pouvez supprimer, si elles ont été appliquées à des éléments, la suppression échoue et un lien vers l’explorateur de contenu permettant d’identifier les éléments étiquetés s’affiche.

Toutefois, l’affichage des éléments étiquetés par l’explorateur de contenu peut prendre deux jours maximum. Dans ce scénario, l’étiquette de rétention pourrait être supprimée sans l’affichage du lien vers l’explorateur de contenu.

## <a name="locking-the-policy-to-prevent-changes"></a>Verrouillage de la stratégie pour empêcher toute modification

Si vous avez besoin de vérifier que personne ne peut désactiver la stratégie, supprimer la stratégie ou la rendre moins restrictive, veuillez consulter la rubrique [Utiliser le Verrou de Conservation pour restreindre les modifications apportées aux stratégies de rétention et aux stratégies d’étiquette de rétention](retention-preservation-lock.md).

## <a name="next-steps"></a>Prochaines étapes

Pour vous aider à suivre les étiquettes appliquées à partir de vos stratégies d’étiquetage automatique :

- [Surveillance des étiquettes de rétention](retention.md#monitoring-retention-labels)
- [Utilisation de la recherche de contenu pour rechercher tout le contenu portant une étiquette de rétention spécifique](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)
- [Audit des actions de rétention](retention.md#auditing-retention-actions)

Consultez [Utiliser les étiquettes de rétention pour gérer le cycle de vie des documents stockés dans SharePoint](auto-apply-retention-labels-scenario.md) pour un exemple de scénario qui utilise une stratégie d’application automatique avec des propriétés gérées dans SharePoint et la rétention basée sur les événements pour démarrer la période de rétention.
