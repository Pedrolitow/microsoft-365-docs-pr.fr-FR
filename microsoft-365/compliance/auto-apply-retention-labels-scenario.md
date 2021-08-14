---
title: Utiliser les étiquettes de rétention pour gérer le cycle de vie des documents stockés dans SharePoint
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Comment vous pouvez utiliser les étiquettes de rétention pour gérer le cycle de vie des documents dans SharePoint en utilisant des métadonnées pour classifier le contenu, appliquer automatiquement les étiquettes et utiliser la rétention basée sur les événements pour démarrer la période de rétention.
ms.openlocfilehash: 6a58e339bd3c99bff85bf933d1cf3e079551c84462fad49874487cc7d4fcb9f4
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53881175"
---
# <a name="use-retention-labels-to-manage-the-lifecycle-of-documents-stored-in-sharepoint"></a>Utiliser les étiquettes de rétention pour gérer le cycle de vie des documents stockés dans SharePoint

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Cet article décrit la gestion du cycle de vie des documents stockés dans SharePoint à l’aide d’étiquettes de rétention appliquées automatiquement et de la rétention basée sur les événements.

La fonctionnalité d'application automatique utilise les métadonnées SharePoint pour la classification des documents. L'exemple de cet article concerne les documents relatifs aux produits, mais les mêmes concepts peuvent être utilisés pour d'autres scénarios. Par exemple, dans l'industrie pétrolière et du gaz, vous pourriez l'utiliser pour gérer le cycle de vie des documents relatifs aux actifs physiques tels que les plateformes pétrolières, les journaux de bord des puits ou les licences de production. Dans le secteur des services financiers, vous pourriez gérer les documents relatifs aux comptes bancaires, aux hypothèques ou aux contrats d'assurance. Dans le secteur public, vous pourriez gérer les permis de construire ou les formulaires fiscaux.

Dans cet article, nous examinerons l'architecture de l'information et la définition des étiquettes de conservation. Ensuite, nous classerons les documents en appliquant automatiquement les étiquettes. Et enfin, nous allons générer les événements qui déclenchent la période de rétention.

## <a name="information-architecture"></a>Architecture des informations

Notre scénario est celui d'une entreprise de fabrication qui utilise SharePoint pour stocker tous les documents relatifs aux produits qu'elle développe. Ces documents incluent les spécifications du produit, les accords avec des fournisseurs et les manuels de l’utilisateur. Lorsque ces documents sont stockés dans SharePoint par le biais de politiques de gestion de contenu d'entreprise, des métadonnées de document sont définies, qui sont utilisées pour les classer. Chaque document possède les propriétés de métadonnées suivantes :

- **Type de document**(tel que spécification de produit, accord ou manuel d'utilisation)

- **Nom du produit**

- **État** (brouillon ou final)

Ces métadonnées forment un type de contenu de base appelé *Document de production* pour tous les documents.

![Tableau des métadonnées de la documentation sur les produits](../media/SPRetention1.png)

> [!NOTE]
> Les propriétés **Type de document** et **Status** sont utilisées par les politiques de conservation plus loin dans ce scénario pour classer et appliquer automatiquement les étiquettes de conservation.

Nous pouvons avoir plusieurs types de contenu qui représentent différents types de documents, mais concentrons-nous sur la documentation du produit.

Dans ce scénario, nous utilisons le service de gestion des métadonnées et le Term Store pour créer un ensemble de termes pour *le type de document* et un autre pour le *nom du produit*. Pour chaque ensemble de termes, nous créons un terme pour chaque valeur. Cela ressemblerait à quelque chose comme ça dans Term Store pour votre organisation SharePoint :

![Sample term set for product documentation in Term Store](../media/SPRetention2.png)

*Le type de contenu* peut être créé et publié en utilisant le [centre de types de contenu](https://support.office.com/article/manage-content-type-publishing-06f39ac0-5576-4b68-abbc-82b68334889b). Vous pouvez également créer et publier un type de contenu en utilisant des outils de provisionnement de site, tels que le [cadre de provisionnement PnP](/sharepoint/dev/solution-guidance/pnp-provisioning-framework) ou [le schéma JSON de conception de site](/sharepoint/dev/declarative-customization/site-design-json-schema#define-a-new-content-type).

Chaque produit dispose d'un site SharePoint dédié qui contient une bibliothèque de documents dont les types de contenu appropriés sont activés. Tous les documents sont stockés dans cette bibliothèque de documents.

[ ![Bibliothèque de documents pour la documentation sur le produit](../media/SPRetention3.png) ](../media/SPRetention3.png#lightbox)

> [!NOTE]
> Au lieu d'avoir un site SharePoint par produit, l'entreprise de fabrication dans ce scénario pourrait utiliser Team Microsoft par produit pour soutenir la collaboration entre les membres de l'équipe, par exemple par le biais d'un chat permanent, et utilise **l'onglet Fichiers** dans Teams pour la gestion des documents. Dans cet article, nous concentrons uniquement sur les documents, nous n'utiliserons donc qu'un site.

Voici un aperçu de la bibliothèque de documents pour le produit widget de rotation :

[ ![Bibliothèque de documents du widget rotatif](../media/SPRetention4.png) ](../media/SPRetention4.png#lightbox)

Maintenant que nous avons mis en place l'architecture d'information de base pour la gestion des documents, examinons la stratégie de conservation et d'élimination des documents qui utilisent les métadonnées et la manière dont nous classons ces documents.

## <a name="retention-and-disposition"></a>Rétention et destruction

Les politiques de conformité et de gouvernance des données de l'entreprise manufacturière dictent la manière dont les données sont conservées et éliminées. Les documents relatifs aux produits doivent être conservés aussi longtemps que le produit est fabriqué et pendant une certaine période supplémentaire. Le délai supplémentaire diffère selon les spécifications des produits, les accords et les manuels d'utilisation. Le tableau suivant indique les conditions requises pour la rétention et la suppression :

|   Type de document            |   Rétention                            |   Destruction                                |
| -------------------------- | -------------------------------------- | -------------------------------------------- |
| Spécifications des produits      | 5 ans après l'arrêt de la production  | Supprimer                                       |
| Accords de produits          | 10 ans après l'arrêt de la production | Révision                                       |
| Manuels d'utilisation                | 5 ans après l'arrêt de la production  | Supprimer                                       |
| Tous les autres types de documents | Ne pas retenir activement  | Supprimer lorsque le document date de plus de 3 ans <br /><br /> Un document est considéré comme datant de plus de 3 ans s'il n'a pas été modifié au cours des 3 dernières années. |
|||

Nous utilisons le centre de conformité Microsoft 365 pour créer[les labels de conservation suivants](retention.md#retention-labels):

  - Spécification du produit

  - Accord de produit

  - Manuel de l’utilisateur

Dans cet article, nous expliquons uniquement comment créer et appliquer automatiquement l’étiquette de rétention de la spécification de produit. Pour implémenter le scénario complet, vous devez également créer et appliquer automatiquement des étiquettes de conservation pour les deux autres types de documents.

### <a name="settings-for-the-product-specification-retention-label"></a>Paramètres de l’étiquette de rétention de la spécification de produit

Voici le [plan de gestion de fichiers](file-plan-manager.md) l’étiquette de rétention de la spécification de produit :

- **Nom :** Spécifications du produit

- **Description pour les utilisateurs :** Conserver pendant 5 ans après l'arrêt de la production.

- **Description pour les admins :** Conserver pendant 5 ans après l'arrêt de la production, suppression automatique, conservation en fonction des événements, le type d'événement est *Arrêt du produit*.

- **Action de rétention :** Conserver et supprimer.

- **Retention duration:** 5 ans (1 825 jours).

- **Étiquette d’enregistrement** : Configurer l’étiquette de rétention pour marquer les éléments comme [enregistrement](records-management.md#records), ce qui signifie que les documents étiquetés ne peuvent pas être modifiés ou supprimés par les utilisateurs.

- **Descripteurs de plans de gestion de fichiers :** Pour simplifier le scénario, aucun descripteur de fichier facultatif n'est fourni.

La capture d'écran suivante montre les paramètres lorsque vous créez l'étiquette de conservation de la spécification du produit dans le centre de conformité Microsoft 365. Vous pouvez créer *le type d'événement* « Arrêt des produits » lorsque vous créez l'étiquette de conservation. Voir la procédure dans la section suivante.

![Paramètres de conservation pour le label de spécification du produit](../media/SPRetention5.png)

> [!NOTE]
> Pour éviter une attente de 5 ans pour la suppression d'un document, fixez la durée de conservation à ***1 jour*** si vous recréez ce scénario dans un environnement de test.

### <a name="create-an-event-type-when-you-create-a-retention-label"></a>Créer un type d'événement lorsque vous créez un label de conservation

1. Dans la page **Définir les paramètres de rétention** de l’assistant de création d’étiquette de rétention, derrière **Démarrer la période de rétention sur la base de**, sélectionnez **Créer un nouveau type d’événement** :

    ![Créer un nouveau type d'événement pour la boîte de dialogue de l’étiquette Spécification du produit.](../media/SPRetention6.png)

3. Dans la page **Nommer votre type d’événement**, entrez **Arrêt du produit** et une description facultative. Sélectionnez ensuite **Suivant**, **Envoyer**, puis **Terminé**.

4. Une fois de retour dans la page **Définir les paramètres de rétention**, pour **Démarrer la période de rétention sur la base de**, utilisez la zone déroulante pour sélectionner le type d’événement **Arrêt du produit** que vous avez créé.

    Voici à quoi ressemblent les paramètres de l’étiquette de rétention de Spécification du produit :

   ![Paramètres de la nouvelle étiquette Spécification du produit](../media/SPRetention7.png)

6. Sélectionnez **Créer une étiquette** : les options permettant de la publier s’affichent dans la page suivante. Appliquez automatiquement l’étiquette, ou enregistrez-la simplement : sélectionnez **Enregistrez simplement l’étiquette pour l'instant**, puis sélectionnez **Terminé**.

    > [!TIP]
    > Pour des étapes plus détaillées, consultez la rubrique [Créer une étiquette dont la période de rétention est basée sur un événement](event-driven-retention.md#step-1-create-a-label-whose-retention-period-is-based-on-an-event).

Voyons maintenant comment appliquer automatiquement l'étiquette de rétention au contenu des spécifications du produit.

## <a name="auto-apply-retention-labels-to-documents"></a>Appliquer automatiquement des étiquettes de rétention à des documents

Nous allons utiliser le Keyword Query Language (KQL) pour [appliquer automatiquement](apply-retention-labels-automatically.md)les étiquettes de rétention que nous avons créées. KQL est le langage qui est utilisé pour construire les requêtes de recherche. Dans KQL, vous pouvez effectuer des recherches en utilisant des mots clés ou des propriétés gérées. Pour plus d'informations, voir [Référence syntaxique du mot-clé KQL (Keyword Query Language)](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

Fondamentalement, nous voulons dire à Microsoft 365 d'appliquer **l'étiquette de conservation de la spécification de produit** à tous les documents qui ont un **statut** de **final** et un **type de document** de **spécification de produit**. Rappelons que **Statut** et **Type de document** sont les colonnes du site que nous avons définies pour le type de contenu Documentation produit dans [la section Architecture](#information-architecture) de l'information. Pour ce faire, nous devons configurer le schéma de recherche.

Lorsque SharePoint indexe le contenu, il génère automatiquement des propriétés analysées pour chaque colonne de site. Pour ce scénario, nous sommes intéressés par les propriétés **Type de document** et **État**. Nous avons besoin de documents dans la bibliothèque qui sont du bon type de contenu et dont les colonnes du site sont remplies pour la recherche afin de créer les propriétés analysées.

Dans le centre d'administration de SharePoint, ouvrez la configuration de recherche et sélectionnez **Gérer le schéma de recherche** pour afficher et configurer les propriétés analysées.

![Propriétés analysées dans le schéma de recherche](../media/SPRetention8.png)

Si nous tapons **statut** _ dans la _ *boîte propriétés analysées** et que nous sélectionnons la flèche verte, nous devrions voir un résultat comme celui-ci :

![La propriété analysée ows_Status](../media/SPRetention9.png)

La **propriété\_\_ows Status** (remarquez le double soulignement) est celle qui nous intéresse. Il correspond à la **propriété Statut** du type de contenu du document de production.

Maintenant, si nous tapons ***ows\_document*** et sélectionnons la flèche verte, nous devrions voir quelque chose comme ceci :

![La propriété analysée ows_Doc_Type](../media/SPRetention10.png)

La **propriété \_de type ows document\_x0020\_est la deuxième** propriété qui nous intéresse. Il correspond à la **propriété Type de document** du type de contenu du document de production.

> [!TIP]
> Pour identifier le nom d'une propriété analysées pour ce scénario, allez à la bibliothèque de documents qui contient les documents de production. Ensuite, allez dans les paramètres de la bibliothèque. Pour **les colonnes**, sélectionnez le nom de la colonne (par exemple, **Statut** ou **Type de document**) pour ouvrir la page de la colonne du site.           Le paramètre *Champ* dans l’URL de la page contient le nom du champ. Ce nom de champ, préfixé avec « ows_ », est le nom de la propriété analysée. Par exemple, l’URL `https://tenantname.sharepoint.com/sites/SpinningWidget/_layouts/15/FldEdit.aspx?List=%7BC38C2F45-3BD6-4C3B-AA3B-EF5DF6B3D172%7D&Field=_Status` correspond à *ows\_\_État* propriété analysée.

Si les propriétés analysées que vous recherchez n'apparaissent pas dans la section Gérer le schéma de recherche dans le centre d'administration de SharePoint :

- Peut-être que les documents n'ont pas été indexés. Vous pouvez forcer une réindexation de la bibliothèque en allant à **Paramètres de la bibliothèque de documents** > **Paramètres  avancés**.

- Si la bibliothèque de documents se trouve sur un site moderne, assurez-vous que l’administrateur SharePoint est également un administrateur de collection de sites.

Pour plus d’informations sur les propriétés gérées et analysées, voir [A propos des propriétés gérées créées automatiquement dans le serveur SharePoint](/sharepoint/technical-reference/automatically-created-managed-properties-in-sharepoint).

### <a name="map-crawled-properties-to-pre-defined-managed-properties"></a>Cartographie des propriétés analysées vers des propriétés gérées prédéfinies

KQL ne peut pas utiliser les propriétés analysées dans les requêtes de recherche. Elle doit utiliser une propriété gérée. Dans un scénario de recherche typique, nous créons une propriété gérée et la mettons en correspondance avec la propriété analysée dont nous avons besoin. Toutefois, pour l'application automatique des étiquettes de conservation, vous pouvez uniquement spécifier des propriétés gérées prédéfinies dans KQL, et non des propriétés gérées personnalisées. Il existe un ensemble de propriétés gérées prédéfinies dans le système pour les chaînes *RefinableString00* à *RefinableString199* que vous pouvez utiliser.         Pour obtenir la liste complète, voir [Propriétés gérées non utilisées par défaut](/sharepoint/manage-search-schema#default-unused-managed-properties). Ces propriétés gérées par défaut sont généralement utilisées pour définir des affinements de recherche.

Pour que la requête KQL applique automatiquement l'étiquette de conservation correcte au contenu du document du produit, nous faisons correspondre les propriétés analysées **ows\_ Document\_x0020\_Type* et *ows\_\_Statut** à deux propriétés gérées raffinées.                Dans notre environnement de test pour ce scénario, **RefinableString00** et **RefinableString01** ne sont pas utilisés.            Nous l'avons déterminé en examinant **la gestion des propriétés** dans **le schéma de recherche** du centre d'administration de SharePoint.             

[ ![Propriétés gérées dans schéma de recherche](../media/SPRetention12.png) ](../media/SPRetention12.png#lightbox)

Notez que la colonne **Propriétés analysées mappées** de la capture d’écran précédente est vide.

Pour cartographier la **propriété de l'ows\_document\_x0020\_Type** analysée suivez ces étapes :  

1. Dans la zone de filtre **Propriété gérée**, tapez **_RefinableString00_** puis sélectionnez la flèche verte.

2. Dans la liste des résultats, sé le lien **RefinableString00**, puis faites défiler vers le bas jusqu’à la section **Mappages aux propriétés analysées**.

3. Sélectionnez **Ajouter un mappage**, puis tapez **_ows\_Doc\_x0020\_Type_*_ dans la _* zone Rechercher un nom de propriété analysée** dans la fenêtre **Sélection de propriété analysée**. Sélectionnez **Rechercher**.

4. Dans la liste des résultats, sélectionnez **ows\_doc\_x0020\_Type** puis sélectionnez **OK**.

   Dans la section **Propriétés analysées mappées**, vous devriez voir quelque chose de semblable à la capture d’écran suivante :

   [ ![Sélectionnez Ajouter une cartographie dans la section Propriétés cartographiées et analysées](../media/SPRetention13.png) ](../media/SPRetention13.png#lightbox)


5. Faites défiler jusqu'au bas de la page et sélectionnez **OK** pour enregistrer la cartographie.      

Répétez ces étapes pour cartographier **RefinableString01** et **ows\_\_Status**.           

Maintenant, vous devriez avoir deux propriétés gérées qui correspondent aux deux propriétés analysées :

[ ![Les propriétés gérées sont présentées sous forme de cartes pour les propriétés analysées](../media/SPRetention14.png) ](../media/SPRetention14.png#lightbox).

Vérifions que notre configuration est correcte en lançant une recherche d'entreprise. Dans un navigateur, allez *https://\<your_tenant>.sharepoint.com/search*.         Dans la boîte de recherche, tapez ***RefinableString00 : «Spécification du produit »** _ et appuyez sur la touche Entrée. Cette recherche devrait renvoyer tous les documents qui ont une _ *Spécification de produit** de **_Type document_**.

Dans la boîte de recherche, tapez **RefinableString00: « Spécification du produit » ET RefinableString01:Final** et appuyez sur entrée. Il doit retourner tous les documents qui ont une **Spécification de produit** de **_Type document_*_ et un _* statut** de **_document final_**.

### <a name="create-auto-apply-label-policies"></a>Créer des politiques d'application automatique des étiquettes

Maintenant que vérification a été faite que la requête KQL fonctionne, créons une stratégie d’application automatique d'étiquettes utilisant une requête KQL pour appliquer automatiquement l'étiquette de rétention Spécification du produit sur les documents appropriés.

1. Dans le [centre de conformité](https://compliance.microsoft.com/homepage), allez à **Gestion des enregistrements** > **Politiques d'étiquetage** > **Appliquer automatiquement un label**.                

   [ ![Sélectionnez « Auto-appliquer un label » sur la page Label](../media/SPRetention16.png) ](../media/SPRetention16.png#lightbox)

2. Dans l’assistant de création de stratégie d’étiquetage automatique, sur la page **Nommer votre stratégie d’étiquetage automatique**, entrez un nom tel que **Application automatique d’étiquette Spécification du produit** et une description facultative. Ensuite, sélectionnez **Suivant**.

3. Dans la page **Choisir le type de contenu auquel vous voulez appliquer cette étiquette**, sélectionnez **Appliquer une étiquette au contenu incluant des mots ou des phrases spécifiques**, ou des propriétés, puis sélectionnez **Suivant**.

   [ ![Sélectionnez Appliquer l’étiquette au contenu incluant des mots ou des phrases spécifiques, ou des propriétés](../media/SPRetention17.png) ](../media/SPRetention17.png#lightbox)

   Cette option permet de fournir la même requête de recherche KQL que celle que nous avons testée dans la section précédente. Cette requête renvoie tous les documents de spécification de produit qui ont un statut de *Final*. Lorsque cette requête est utilisée dans la stratégie d'applicage automatique d’étiquette, l'étiquette de rétention Spécification du produit sera automatiquement appliquée à tous les documents qui y correspondent.

4. Dans la page **Appliquer l’étiquette au contenu correspondant à cette requête**, tapez **RefinableString00:"Spécification du produit" ET RefinableString01:Final**, puis sélectionnez **Suivant**.

   ![Spécifiez la requête dans la zone Éditeur de requête de mot clé](../media/SPRetention19.png)

5. Dans la page **Choisir des emplacements auxquels appliquer la stratégie**, sélectionnez les emplacements de contenu auxquels vous voulez appliquer la stratégie. Pour ce scénario, nous appliquons la politique uniquement aux sites SharePoint, car tous les documents de production sont stockés dans des bibliothèques de documents SharePoint. Basculez l’état de **Courrier Exchange**, **Comptes OneDrive** et **Groupes Microsoft 365** sur **Désactivé**. Assurez-vous que le statut des sites SharePoint est défini sur **Activé** avant de sélectionner **Suivant** :

    ![Choisissez des sites spécifiques auxquels appliquer automatiquement des étiquettes](../media/SPRetentionSPlocations.png)

   > [!TIP]
   > Plutôt que d’appliquer la stratégie à tous les sites SharePoint, vous pouvez sélectionner **Choisir un site** et ajouter les URL de sites SharePoint spécifiques.

6. Dans la page **Choisir une étiquette à appliquer automatiquement**, sélectionnez **Ajouter une étiquette**.

7. Dans la liste d’étiquettes de rétention, sélectionnez **Spécification du produit**. Sélectionnez ensuite **Ajouter** puis **Suivant**.

8. Vérifiez vos paramètres :

    ![Paramètres pour l'application automatique de l’étiquette](../media/SPRetention18.png)

9. Sélectionnez **Envoyer** pour créer la stratégie d’application automatique d’étiquettes.

   > [!NOTE]
   > Il faut jusqu'à 7 jours pour appliquer automatiquement l'étiquette de la spécification du produit à tous les documents qui correspondent à la requête de recherche KQL.

### <a name="verify-that-the-retention-label-was-automatically-applied"></a>Vérifier que l'étiquette de conservation a été appliquée automatiquement

Après 7 jours, utilisez l’[explorateur d'activités](data-classification-activity-explorer.md) dans le centre de conformité pour vérifier que la politique d'application automatique d’étiquettes que nous avons créée a bien appliqué automatiquement les étiquettes de rétention aux documents de produits.

Consultez également les propriétés des documents de la bibliothèque de documents. Dans le panneau d’informations, vous pouvez voir que l’étiquette de rétention est appliquée à un document sélectionné.

[ ![Vérifiez que l’étiquette a été appliquée en examinant les propriétés du document dans la bibliothèque de documents](../media/SPRetention21.png) ](../media/SPRetention21.png#lightbox)

Comme les étiquettes de conservation ont été appliquées automatiquement aux documents, ceux-ci sont protégés contre la suppression car l'étiquette de conservation a été configurée pour déclarer les documents comme des *enregistrements*. À titre d'exemple de cette protection, nous recevons le message d'erreur suivant lorsque nous essayons de supprimer l'un de ces documents :

[ ![Un message d'erreur indique que les documents ne peuvent pas être supprimés car l'étiquette déclare que les documents sont des enregistrements.](../media/SPRetention22.png) ](../media/SPRetention22.png#lightbox)

## <a name="generate-the-event-that-triggers-the-retention-period"></a>Générer l'événement qui déclenche la période de rétention

Maintenant que les étiquettes de conservation sont appliquées, concentrons-nous sur l'événement qui indiquera la fin de la production pour un produit particulier. Cet événement déclenche le début de la période de conservation qui est définie dans les étiquettes de conservation. Par exemple, pour les cahiers des charges des produits, la période de conservation de 5 ans commence lorsque l'événement « fin de la production est déclenché.

Vous pouvez créer manuellement l'événement dans le centre de conformité Microsoft 365 en vous rendant **sur la page Événements de** > **gestion des enregistrements**.                Vous devez choisir le type d'événement, définir les bons numéros d'identification d’élément des actifs et entrer une date pour l'événement. Pour plus d'informations, voir [Commencer la rétention lorsqu'un événement se produit](event-driven-retention.md).                

Mais pour ce scénario, nous allons générer automatiquement l'événement à partir d'un système de production externe. Le système est une simple liste SharePoint qui indique si un produit est en cours de production. Un flux [Power Automate](/flow/getting-started) associé à la liste qui déclenchera l'événement.        Dans un scénario réel, vous pourriez utiliser différents systèmes pour générer l'événement, tels qu'un système de RH ou de CRM. Power Automate contient de nombreuses interactions prêtes à l'emploi et des éléments de base pour les charges de travail de Microsoft 365, comme Microsoft Exchange, SharePoint, Teams et Dynamics 365, ainsi que des applications tierces comme Twitter, Box, Salesforce et Workdays. Cette fonctionnalité permet d'intégrer facilement Power Automate à divers systèmes. Pour plus d’informations, voir[Automatiser la rétention basée sur un événement](./event-driven-retention.md#automate-events-by-using-a-rest-api).

La capture d’écran suivante montre la liste SharePoint qui sera utilisée pour déclencher l’événement :

[ ![La liste qui déclenchera l'événement de rétention](../media/SPRetention23.png) ](../media/SPRetention23.png#lightbox)

Il y a deux produits actuellement en production, comme l'indique le **Oui** _ dans la colonne _ *En production**. Lorsque la valeur dans cette colonne est définie sur **_Aucun_** pour un produit, le flux associé à la liste génère automatiquement l’événement. L'événement déclenche le début de la période de conservation de l'étiquette de conservation qui a été appliquée automatiquement sur les documents du produit correspondant.

Pour ce scénario, nous utilisons le flux suivant pour déclencher l’événement :

[ ![Configuration du flux qui déclenchera l’événement](../media/SPRetention24.png) ](../media/SPRetention24.png#lightbox)

Pour créer ce flux, commencez à partir d’un connecteur SharePoint et sélectionnez le déclencheur **Lorsqu’un élément est créé ou modifié**. Précisez l'adresse du site et le nom de la liste. Ajoutez ensuite une condition basée sur le moment où la valeur de la colonne de la liste **En production** est définie sur **_Non_* _ (ou égale à _faux sur la carte de condition). Ajoutez ensuite une action basée sur le modèle HTTP intégré. Utilisez les valeurs de la section suivante pour configurer l’action HTTP. Vous pouvez copier les valeurs des propriétés **URI** et **Body** de la section suivante et les coller dans le modèle.                     

- **Method** : PUBLIER
- **URI** : `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Headers** : Clé = Type de contenu, Valeur = application/atom+xml
- **Body** :

    ```xml
    <?xml version='1.0' encoding='utf-8' standalone='yes'>
    <entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices' xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata' xmlns='https://www.w3.org/2005/Atom'>
    <category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent'>
    <updated>9/9/2017 10:50:00 PM</updated>
    <content type='application/xml'>
    <m:properties>
    <d:Name>Cessation Production @{triggerBody()?['Product_x0020_Name']?['Value']}</d:Name>
    <d:EventType>Product Cessation&lt;</d:EventType>
    <d:SharePointAssetIdQuery>ProductName:&quot;@{triggerBody()?['Product_x0020_Name']?['Value']}<d:SharePointAssetIdQuery>
    <d:EventDateTime>@{formatDateTime(utcNow(),'yyyy-MM-dd')}</d:EventDateTime>
    </m:properties>
    </content&gt>
    </entry>
    ```

Cette liste décrit les paramètres dans la propriété **Body** de l'action qui doivent être configurés pour ce scénario :

- **Nom**: Ce paramètre spécifie le nom de l'événement qui sera créé dans le centre de conformité Microsoft 365. Pour ce scénario, le nom est  Arrêt de la production *xxx*,où *xxx* est la valeur de la propriété gérée **ProductName** que nous avons créée précédemment.      
- **EventType** : la valeur de ce paramètre correspond au type d’événement auquel l’événement créé s'applique. Ce type d’événement a été défini lors de la création de l’étiquette de rétention. Pour ce scénario, le type d'événement est « Arrêt du produit ».
- **SharePointAssetIdQuery**: Ce paramètre définit les identifiants des actifs pour l'événement. La conservation basée sur un événement nécessite un identifiant unique pour le document. Nous pouvons utiliser les identifications des actifs pour identifier les documents auxquels un événement particulier s'applique ou, comme dans ce scénario, la colonne de métadonnées **Nom du produit**. Pour ce faire, nous devons créer une nouvelle propriété gérée **ProductName** qui peut être utilisée dans la requête KQL.      (On pourrait aussi utiliser **RefinableString00** au lieu de créer une nouvelle propriété gérée).                 Nous devons également mettre en correspondance cette nouvelle propriété gérée avec la propriété **ows_Product_x0020_Name** analysée.              Voici une capture d’écran de cette propriété gérée.

    [ ![Propriété gérée par la rétention](../media/SPRetention25.png) ](../media/SPRetention25.png#lightbox)

- **EventDateTime**: Ce paramètre définit la date à laquelle l'événement se produit. Utilisez le format de la date actuelle :<br/><br/>*formatDateTime(utcNow(), 'yyyy-MM-dd'*)

### <a name="putting-it-all-together"></a>Tout mettre ensemble

Maintenant, l'étiquette de rétention est créée et appliquée automatiquement, et le flux est configuré et créé. Lorsque la valeur de la colonne **En production** pour le produit widget de rotation de la liste Produits est remplacée de **_Oui_*_ à _*_Non_*_, le flux est déclenché pour créer l’événement. Pour afficher cet événement dans le centre de conformité, accédez à _* Gestion des enregistrements** > **Événements**.

[ ![L'événement qui a été déclenché par le flux est affiché sur la page Événements dans le centre de conformité.](../media/SPRetention28.png) ](../media/SPRetention28.png#lightbox)

Sélectionnez l'événement pour voir les détails sur la page du menu volant. Notez que même si l'événement est créé, le statut de l'événement montre qu'aucun site ou document SharePoint n'a été traité.

![Détails de l'événement](../media/SPRetention29.png)

Mais après un certain délai, le statut de l'événement indique qu'un site SharePoint et un document SharePoint ont été traités.

![Les détails de l'événement montrent que les documents ont été traités.](../media/SPRetention31.png)

Cela montre que la période de conservation du label appliqué au document du produit Spinning Widget a été lancée, sur la base de la date de l'événement *Arrêt de la production Spinning Widget*. En supposant que vous ayez mis en œuvre le scénario dans votre environnement de test en configurant une période de conservation d'une journée, vous pouvez vous rendre à la bibliothèque de documents de votre produit quelques jours après la création de l'événement et vérifier que le document a été supprimé (après l'exécution du travail de suppression dans SharePoint).

### <a name="more-about-asset-ids"></a>En savoir plus sur l'identification des actifs

Comme [l'explique l'article Démarrer la rétention lorsqu'un événement se produit](event-driven-retention.md) il est important de comprendre la relation entre les types d'événements, les étiquettes de rétention, les événements et les identifications d'actifs.      . Cette identification est simplement une propriété du document dans SharePoint et OneDrive. Il vous aide à identifier les documents dont la période de conservation sera déclenchée par l'événement. Par défaut, SharePoint possède une **identification d’élément** que vous pouvez utiliser pour la conservation des données en fonction des événements :          

![La propriété d’identification d’élément est affichée sur une page de détail des propriétés du document.](../media/SPRetention26.png)

Comme le montre la capture d'écran suivante, le bien géré par l’identification d’élément est appelé **ComplianceAssetId**.    

[ ![Propriété gérée par ComplianceAssetId](../media/SPRetention27.png) ](../media/SPRetention27.png#lightbox)

Au lieu d'utiliser la propriété **identification d’élément** par défaut comme nous le faisons dans ce scénario, vous pouvez utiliser n'importe quelle autre propriété.           Mais il est important de comprendre que si vous ne spécifiez pas d'identifiant ou de mots clés pour un événement, tout le contenu qui a une étiquette de ce type d'événement aura sa période de conservation déclenchée par l'événement.

### <a name="using-advanced-search-in-sharepoint"></a>Utilisation de la recherche avancée dans SharePoint

Dans la capture d'écran précédente, vous pouvez voir qu'il y a une autre propriété gérée liée aux étiquettes de rétention appelée **ComplianceTag** qui est cartographiée à une propriété analysée. Les propriétés par **ComplianceAssetId** gérées par le ComplianceAssetId sont également cartographiées en tant que propriétés analysées.   Cela signifie que vous pouvez utiliser ces propriétés gérées dans la recherche avancée pour récupérer tous les documents qui ont été étiquetés avec une étiquette de conservation.