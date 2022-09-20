---
title: Étiqueter les documents d’un jeu à réviser
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: L’étiquetage des documents dans un ensemble de révisions permet de supprimer le contenu inutile et d’identifier le contenu pertinent dans un cas eDiscovery (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: f3b250dad79b7e22b2cea71d18fab6eb053e4ce8
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67819180"
---
# <a name="tag-documents-in-a-review-set-in-ediscovery-premium"></a>Baliser des documents dans un ensemble de révisions dans eDiscovery (Premium)

L’organisation du contenu dans un ensemble de révisions est importante pour effectuer différents flux de travail dans le processus eDiscovery. Cela inclut les opérations suivantes :

- Élimination de contenu inutile

- Identification du contenu pertinent

- Identification du contenu qui doit être examiné par un expert ou un avocat

Lorsque des experts, des avocats ou d’autres utilisateurs passent en revue le contenu d’un ensemble de révisions, leurs opinions relatives au contenu peuvent être capturées à l’aide de balises. Par exemple, si l’objectif est d’éliminer le contenu inutile, un utilisateur peut baliser des documents avec une balise telle que « non réactif ». Une fois le contenu révisé et balisé, une recherche d’ensemble de révision peut être créée pour exclure tout contenu marqué comme « non réactif ». Ce processus élimine le contenu non réactif des étapes suivantes du flux de travail eDiscovery. Le panneau d’étiquetage d’un ensemble de révisions peut être personnalisé pour chaque cas afin que les balises prennent en charge le flux de travail de révision prévu pour le cas.

> [!NOTE]
> L’étendue des balises est un cas eDiscovery (Premium). Cela signifie qu’un cas ne peut avoir qu’un seul ensemble de balises que les réviseurs peuvent utiliser pour baliser les documents de l’ensemble de révisions. Vous ne pouvez pas configurer un autre ensemble de balises à utiliser dans différents ensembles de révision dans le même cas.

## <a name="tag-types"></a>Types de balises

eDiscovery (Premium) fournit deux types de balises :

- **Balises à choix unique** : limite les réviseurs à la sélection d’une balise unique au sein d’un groupe. Ces types de balises peuvent être utiles pour s’assurer que les réviseurs ne sélectionnent pas les balises conflictuelles telles que « réactif » et « non réactif ». Les balises à choix unique apparaissent sous forme de cases d’option.

- **Balises à choix multiples** : autoriser les révisions à sélectionner plusieurs balises au sein d’un groupe. Ces types de balises apparaissent sous forme de cases à cocher.

## <a name="tag-structure"></a>Structure des balises

En plus des types de balises, la structure de la façon dont les balises sont organisées dans le panneau de balises peut être utilisée pour rendre les documents d’étiquetage plus intuitifs. Les balises sont regroupées par sections. La recherche d’ensemble de révision prend en charge la possibilité de rechercher par balise et par section d’étiquette. Cela signifie que vous pouvez créer une recherche d’ensemble de révisions pour récupérer des documents marqués avec n’importe quelle balise dans une section.

![Sections de balise dans le panneau d’étiquettes.](../media/TagTypes.png)

Vous pouvez organiser davantage les balises en les imbriquer dans une section. Par exemple, si l’intention est d’identifier et de baliser le contenu privilégié, l’imbrication peut être utilisée pour indiquer clairement qu’un réviseur peut marquer un document comme « Privilégié » et sélectionner le type de privilège en vérifiant la balise imbriquée appropriée.

![Balises imbriqués dans une section de balise.](../media/NestingTags.png)

## <a name="creating-and-applying-tags"></a>Création et application de balises

L’étiquetage des éléments dans les jeux de révision est un processus en deux étapes. La première étape consiste à créer les balises qui sont ensuite appliquées à la révision des éléments définis. Après avoir créé des balises, vous et d’autres réviseurs pouvez les appliquer aux éléments d’un ensemble de révisions. Comme expliqué précédemment, un cas eDiscovery (Premium) ne peut avoir qu’un seul ensemble de balises que les réviseurs peuvent utiliser pour baliser des éléments de jeu de révision.

### <a name="create-tags"></a>Créer des balises

Avant d’appliquer des balises aux éléments d’un jeu de révision, vous devez créer une structure de balises.

1. Ouvrez un ensemble de révisions, accédez à la barre de commandes, puis sélectionnez **Baliser les fichiers**.

2. Dans la page de menu volant **Des fichiers de** balises, cliquez sur **Créer/modifier des balises**.

   ![Cliquez sur Créer/modifier des balises dans la page de menu volant.](../media/CreateAeDTags1.png)

3. Dans la page **Étiquettes** , sélectionnez **Ajouter une section**.

4. Tapez un titre de groupe de balises et une description facultative, puis cliquez sur **Enregistrer**.

5. Sélectionnez le menu déroulant à trois points en regard du titre du groupe de balises, puis cliquez sur **Case à cocher Ajouter** ou **Bouton Ajouter une option**.

6. Tapez un nom et une description pour la case à cocher ou le bouton d’option.

7. Répétez ce processus pour créer des sections de balises, des options de balise et des cases à cocher. Par exemple, la capture d’écran suivante montre un groupe de balises nommé **Révision**, qui se compose de cases à cocher **réactives** et **non réactives** .

   ![Configurez la structure des balises.](../media/ManageTagOptions3.png)

### <a name="apply-tags"></a>Apply tags

Une fois la structure des balises en place, les réviseurs peuvent appliquer des balises aux éléments d’un ensemble de révisions en configurant les paramètres d’étiquetage.

1. Dans la barre de commandes de l’ensemble de révisions, sélectionnez **Fichiers de** balises pour afficher la page de menu volant **Des fichiers** de balises (également appelée *panneau d’étiquetage*).

   ![Cliquez sur Baliser les fichiers dans la barre de commandes pour ouvrir le panneau d’étiquetage.](../media/TagFilesFlyoutPage.png)

2. Dans la page de menu volant **Des fichiers** de balises, vous pouvez définir les options suivantes pour configurer la façon de baliser les éléments affichés dans le jeu de révision. Les filtres ou les requêtes de filtre actuellement appliqués au jeu de révision déterminent les éléments affichés et par conséquent les éléments auxquels vous pouvez appliquer des balises. Pour plus d’informations, consultez [Interroger et filtrer du contenu dans un ensemble de révisions](review-set-search.md).

   - **Choisissez la sélection**. Choisissez l’une des options suivantes pour déterminer l’étendue des éléments auxquels appliquer des balises.

      - **Baliser les éléments sélectionnés** : cette option applique des balises aux éléments que vous sélectionnez. Vous pouvez sélectionner des éléments avant ou après le lancement du panneau d’étiquetage. Cette option affiche (en temps réel) le nombre d’éléments sélectionnés qui seront marqués.

      - **Baliser tous les éléments de la liste** : cette option applique des balises à tous les éléments affichés dans le jeu de révision. Cette option affiche le nombre total d’éléments qui seront marqués.

   - **Développer la sélection** : utilisez les options suivantes pour baliser des éléments supplémentaires liés aux éléments marqués dans le jeu de révision.

      - **Inclure les éléments de famille associés** : cette option applique la même balise aux éléments de famille associés aux éléments étiquetés.  *Les éléments de famille* sont des éléments qui partagent la même valeur de propriété de métadonnées **FamilyId** . Par exemple, un document joint à un message électronique partage le même **FamilyId** que le message électronique. Par conséquent, si cette option est sélectionnée pour cet exemple, l’e-mail et le document sont marqués, même si le document peut ne pas être inclus dans la liste des éléments de l’ensemble de révisions.

      - **Inclure les éléments de conversation associés** : cette option applique la même balise à tous les éléments qui se trouvent dans la même conversation Teams ou Yammer que les éléments marqués. *Les éléments de conversation* sont des éléments qui partagent la même valeur de propriété de métadonnées **ConversationId** . Tous les messages, billets et fichier de transcription correspondant d’une conversation partagent le même **ConversationId**. Si cette option est sélectionnée, tous les éléments de la même conversation (et du même fichier de transcription) sont marqués, même si certains de ces éléments de conversation peuvent ne pas être inclus dans la liste des éléments de jeu de révision. Pour plus d’informations sur les éléments de conversation, consultez la section « Regroupement » dans le [flux de travail eDiscovery (Premium) pour le contenu dans Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#grouping).

      - **Aucun** : cette option n’applique pas de balises aux éléments de famille ou aux éléments de conversation. Il applique uniquement les balises aux éléments sélectionnés ou à tous les éléments de la liste d’ensembles de révision.

   > [!NOTE]
   > L’inclusion d’éléments de famille ou de conversation associés ne modifie pas le nombre d’éléments affichés dans la **balise Éléments sélectionnés** ou **Baliser tous les éléments dans les options de liste** . En d’autres termes, le nombre d’éléments associés qui seront marqués n’est pas affiché.

   - **Attribuer des balises** : cette section affiche les balises (organisées par groupes de balises) que vous pouvez appliquer aux documents. Vous ne pouvez appliquer qu’une seule balise à choix unique (identifiée par une case d’option) par groupe de balises. Toutefois, vous pouvez appliquer plusieurs balises à choix multiples (qui sont identifiées par une case à cocher).

3. Cliquez sur **Appliquer des balises** pour appliquer les balises en fonction de vos paramètres.

   Le message **d’état Appliquer les balises** s’affiche pour chaque groupe de balises dans le panneau d’étiquetage pour indiquer qu’un travail d’étiquetage a été démarré. Les balises de chaque groupe de balises de la section **Attribuer des balises** sont grisées jusqu’à ce que le travail soit terminé.

> [!TIP]
> Si vous êtes en train de configurer les paramètres dans le panneau d’étiquetage, mais que vous souhaitez recommencer, cliquez sur **Réinitialiser l’attribution de balise** pour effacer le paramètre actuel. Ce contrôle ne s’applique pas aux éléments déjà marqués, et il ne modifie pas ou ne supprime pas les balises des éléments précédemment marqués.  

#### <a name="monitor-tagging-jobs"></a>Surveiller les travaux d’étiquetage

Lorsque vous marquez un grand nombre d’éléments (ou sélectionnez l’option **Baliser tous les éléments de la liste**), un travail **d’étiquetage des documents** est créé. Vous affichez l’état de ce travail sous l’onglet **Travaux** dans le cas. Cela vous permet de suivre les travaux d’étiquetage volumineux qui peuvent prendre beaucoup de temps. Dans certains cas, un travail d’étiquetage peut être terminé, mais le message **d’état Appliquer les balises** dans le panneau d’étiquetage s’affiche toujours. Pour mettre à jour l’état des travaux d’étiquetage, cliquez sur **Actualiser** dans la barre de commandes du jeu de révisions.

## <a name="removing-tags"></a>Suppression de balises

Vous pouvez supprimer des balises des éléments d’un ensemble de révisions. Toutefois, vous ne pouvez pas supprimer une balise à choix unique qui a été appliquée à un élément de jeu de révision. Vous pouvez uniquement remplacer une balise à choix unique par une autre balise à choix unique dans le même groupe de balises.

Pour supprimer une balise :

1. Sélectionnez les éléments dont vous souhaitez supprimer la balise.

2. Cliquez sur **Baliser les fichiers** pour afficher le panneau d’étiquetage.

3. Sous **Attribuer des balises**, désélectionnez la balise, puis cliquez sur **Appliquer des balises**.

Vous pouvez également utiliser la procédure précédente pour modifier la balise appliquée aux éléments sélectionnés. Après avoir désélectionner la balise actuelle, vous pouvez en sélectionner une autre.
