---
title: Exporter un rapport de recherche de contenu
description: Au lieu d’exporter les résultats réels d’une recherche de contenu dans le portail de conformité Microsoft Purview, vous pouvez exporter un rapport de résultats de recherche. Le rapport contient un résumé des résultats de la recherche et un document contenant des informations détaillées sur chaque élément qui serait exporté.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExportReport
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- content-search
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6b059052e1fc313ac8670295a97b12e6cba6d35d
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688591"
---
# <a name="export-a-content-search-report"></a>Exporter un rapport de recherche de contenu

Au lieu d’exporter l’ensemble complet des résultats de recherche à partir d’une recherche de contenu dans le portail de conformité Microsoft Purview (ou à partir d’une recherche associée à un cas Microsoft Purview eDiscovery (Standard), vous pouvez exporter les mêmes rapports que ceux générés lorsque vous exportez les résultats de recherche réels.
  
Lorsque vous exportez un rapport, les fichiers de rapport sont téléchargés dans un dossier de votre ordinateur local qui porte le même nom que la recherche de contenu, mais qui est ajouté avec *_ReportsOnly*. Par exemple, si la recherche de contenu est nommée  *ContosoCase0815*, le rapport est téléchargé dans un dossier nommé *ContosoCase0815_ReportsOnly*. Pour obtenir la liste des documents inclus dans le rapport, consultez [Ce qui est inclus dans le rapport](#whats-included-in-the-report).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-export-a-search-report"></a>Avant d’exporter un rapport de recherche

- Pour exporter un rapport de recherche, vous devez disposer du rôle de gestion recherche de conformité dans le portail de conformité. Ce rôle est attribué par défaut aux groupes de rôles eDiscovery Manager et Gestion de l’organisation intégrés. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).
- Lorsque vous exportez un rapport, les données sont temporairement stockées dans un emplacement de stockage Azure dans le cloud Microsoft avant d’être téléchargées sur votre ordinateur local. Assurez-vous que votre organisation peut se connecter au point de terminaison dans Azure, qui est **\*.blob.core.windows.net** (le caractère générique représente un identificateur unique pour votre exportation). Les données des résultats de la recherche sont supprimées de l’emplacement stockage Azure deux semaines après leur création.
- L’ordinateur que vous utilisez pour exporter le rapport de recherche doit répondre à la configuration système suivante :
  
  - Dernière version de Windows (32 bits ou 64 bits)
  - Microsoft .NET Framework 4.7 ou version ultérieure
  
- Vous devez utiliser Microsoft Edge<sup>1</sup> pour exécuter l’outil d’exportation eDiscovery. L’utilisation d’Internet Explorer 11 pour exporter les résultats de recherche n’est plus prise en charge<sup>2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> En raison des modifications récentes apportées à Microsoft Edge, la prise en charge de SelectOnce n’est plus activée par défaut. Pour obtenir des instructions sur l’activation de la prise en charge de SelectOnce dans Edge, consultez [Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge](configure-edge-to-export-search-results.md). En outre, Microsoft ne fabrique pas d’extensions ou de modules complémentaires tiers pour les applications SelectOnce. L’exportation des résultats de recherche à l’aide d’un navigateur non pris en charge avec des extensions ou des modules complémentaires tiers n’est pas prise en charge.
  > 
  > <sup>2</sup> À compter d’août 2021, les applications et services Microsoft 365 ne prendront plus en charge Internet Explorer 11 (IE11) et les utilisateurs peuvent avoir une expérience dégradée ou être incapables de se connecter à ces applications et services. Ces applications et services seront progressivement mis hors service au cours des semaines et des mois à venir pour garantir une fin de support fluide. Chaque application et service sont supprimés selon des planifications indépendantes. Pour plus d’informations, consultez ce [billet de blog](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Si la taille totale estimée des résultats retournés par la recherche dépasse 2 To, l’exportation des rapports échoue. Pour exporter correctement les rapports, essayez de restreindre l’étendue et réexécutez la recherche afin que la taille estimée des résultats soit inférieure à 2 To.
- Si les résultats d’une recherche datent de plus de 7 jours et que vous envoyez un travail de rapport d’exportation, un message d’erreur s’affiche vous invitant à réexécuter la recherche pour mettre à jour les résultats de la recherche. Si cela se produit, annulez l’exportation, réexécutez la recherche, puis redémarrez l’exportation.
- L’exportation des rapports de recherche est comptabilisée par rapport au nombre maximal d’exportations en cours d’exécution en même temps et au nombre maximal d’exportations qu’un seul utilisateur peut exécuter. Pour plus d’informations sur les limites d’exportation, consultez [Exporter les résultats de la recherche de contenu](export-search-results.md#export-limits).
  
## <a name="step-1-generate-the-report-for-export"></a>Étape 1 : Générer le rapport pour l’exportation

La première étape consiste à préparer le rapport pour l’exportation du rapport sur votre ordinateur. Lorsque vous exportez le rapport, les documents du rapport sont chargés dans une zone de stockage Azure dans le cloud Microsoft.
  
1. Dans le portail de conformité, sélectionnez la recherche de contenu à partir de laquelle vous souhaitez exporter le rapport.
  
2. Dans le menu **Actions** en bas de la page de menu volant de recherche, sélectionnez **Exporter le rapport**.

   ![Option Exporter le rapport dans le menu Actions.](../media/ActionMenuExportReport.png)

   La page de menu volant **Exporter le rapport** s’affiche. Les options de rapport d’exportation disponibles pour exporter des informations sur la recherche varient selon que les résultats de la recherche se trouvent dans des boîtes aux lettres ou des sites ou une combinaison des deux.
  
3. Sous **Options de sortie**, choisissez l’une des options suivantes :
  
   ![Exporter les options de sortie.](../media/ExportOutputOptions.png)

    - **Tous les éléments, à l’exception de ceux dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour d’autres raisons**. Cette option exporte uniquement des informations sur les éléments indexés.
  
    - **Tous les éléments, y compris ceux dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour d’autres raisons**. Cette option exporte des informations sur les éléments indexés et non indexés.
  
    - **Seuls les éléments dont le format n’est pas reconnu, qui sont chiffrés ou qui n’ont pas été indexés pour d’autres raisons**. Cette option exporte uniquement des informations sur les éléments non indexés.

4. Configurez l’option **Activer la déduplication pour le contenu Exchange** .
  
   - Si vous sélectionnez cette option, le nombre de messages en double (avant la déduplication et après la déduplication) est inclus dans le rapport récapitulative d’exportation. En outre, une seule copie d’un message sera incluse dans le fichier manifest.xml. Toutefois, le rapport des résultats d’exportation contient une ligne pour chaque copie d’un message en double afin que vous puissiez identifier les boîtes aux lettres qui contiennent une copie du message en double. Pour plus d’informations sur les rapports exportés, consultez [Éléments inclus dans le rapport](#whats-included-in-the-report).

   - Si vous ne sélectionnez pas cette option, les rapports d’exportation contiennent des informations sur tous les messages retournés par la recherche, y compris les doublons.

     Pour plus d’informations sur la déduplication et la façon dont les éléments en double sont identifiés, consultez [Déduplication dans les résultats de la recherche eDiscovery](de-duplication-in-ediscovery-search-results.md).

5. Sélectionner **Générer un rapport**.

   Les rapports de recherche sont préparés pour le téléchargement, ce qui signifie que les documents de rapport sont chargés vers un emplacement de stockage Azure dans le cloud Microsoft. L'opération peut prendre plusieurs minutes.

Consultez la section suivante pour obtenir des instructions pour télécharger les rapports de recherche exportés.
  
## <a name="step-2-download-the-report"></a>Étape 2 : Télécharger le rapport

L’étape suivante consiste à télécharger le rapport à partir de la zone stockage Azure vers votre ordinateur local.

> [!NOTE]
> Le rapport de recherche exporté doit être téléchargé dans les 14 jours suivant la génération du rapport à l’étape 1.

1. Dans la page **Recherche de contenu** du portail de conformité, sélectionnez l’onglet **Exportations**
  
   Vous devrez peut-être sélectionner **Actualiser** pour mettre à jour la liste des travaux d’exportation afin qu’elle affiche le travail d’exportation que vous avez créé. Les travaux d’exportation de rapport portent le même nom que la recherche correspondante avec **_ReportsOnly** ajouté au nom de recherche.
  
2. Sélectionnez le travail d’exportation que vous avez créé à l’étape 1.

3. Dans la page de menu volant **Exporter le rapport** sous **Clé d’exportation**, sélectionnez **Copier dans le Presse-papiers**. Vous utilisez cette clé à l’étape 6 pour télécharger les résultats de la recherche.
  
   > [!IMPORTANT]
   > Étant donné que tout le monde peut installer et démarrer l’outil d’exportation eDiscovery, puis utiliser cette clé pour télécharger le rapport de recherche, veillez à prendre des précautions pour protéger cette clé comme vous le feriez pour protéger les mots de passe ou d’autres informations liées à la sécurité.

4. En haut de la page de menu volant, sélectionnez **Télécharger les résultats**.

5. Si vous êtes invité à installer **l’outil d’exportation eDiscovery**, sélectionnez **Installer**.

6. Dans **l’outil d’exportation eDiscovery**, procédez comme suit :

   ![Outil d’exportation eDiscovery.](../media/eDiscoveryExportTool.png)

   1. Collez la clé d’exportation que vous avez copiée à l’étape 3 dans la zone appropriée.
  
   2. Sélectionnez **Parcourir** pour spécifier l’emplacement où vous souhaitez télécharger les fichiers de rapport de recherche.

7. Sélectionnez **Démarrer** pour télécharger les résultats de la recherche sur votre ordinateur.
  
    L’**outil d’exportation de découverte électronique** affiche l’état du processus d’exportation, ainsi qu’une estimation du nombre (et de la taille) d’éléments qui doivent encore être téléchargés. Lorsque le processus d’exportation est terminé, vous pouvez accéder aux fichiers à l’emplacement où ils ont été téléchargés.
  
## <a name="whats-included-in-the-report"></a>Éléments inclus dans le rapport

Lorsque vous générez et exportez un rapport sur les résultats d’une recherche de contenu, les documents suivants sont téléchargés :
  
- **Résumé de l’exportation :** Document Excel qui contient un résumé de l’exportation. Cela inclut des informations telles que le nombre de sources de contenu qui ont fait l’objet d’une recherche, le nombre de résultats de recherche de chaque emplacement de contenu, le nombre estimé d’éléments, le nombre réel d’éléments qui seraient exportés et la taille estimée et réelle des éléments qui seraient exportés.

   Si vous incluez des éléments non indexés lors de l’exportation du rapport, le nombre d’éléments non indexés est inclus dans le nombre total de résultats de recherche estimés et dans le nombre total de résultats de recherche téléchargés (si vous deviez exporter les résultats de la recherche) qui sont répertoriés dans le rapport de synthèse d’exportation. En d’autres termes, le nombre total d’éléments qui seraient téléchargés est égal au nombre total de résultats estimés et au nombre total d’éléments non indexés.
  
- **Manifeste:** Fichier manifeste (au format XML) qui contient des informations sur chaque élément inclus dans les résultats de la recherche. Si vous avez activé l’option de déduplication, les messages en double ne sont pas inclus dans le fichier manifeste.
- **Résultats:** Document Excel qui contient une ligne contenant des informations sur chaque élément indexé qui serait exporté avec les résultats de la recherche. Pour le courrier électronique, le journal des résultats contient des informations sur chaque message, y compris : 

  - l’emplacement du message dans la boîte aux lettres source (notamment si le message est dans la boîte aux lettres principale ou d’archivage) ;
  - la date à laquelle le message a été envoyé ou reçu ;
  - l’objet du message ;
  - l’expéditeur et les destinataires du message.

  Pour les documents provenant de sites SharePoint et OneDrive Entreprise, le journal des résultats contient des informations sur chaque document, notamment :

  - l’URL du document ;
  - l’URL de la collection de sites qui héberge le document ;
  - la date à laquelle le document a été modifié pour la dernière fois ;
  - le nom du document (qui se trouve dans la colonne Objet du journal des résultats).

  > [!NOTE]
  > Le nombre de lignes dans le rapport **Résultats** doit être égal au nombre total de résultats de recherche moins le nombre total d’éléments répertoriés dans le rapport **Éléments non indexés** .
  
- **Trace.log :** Journal de suivi qui contient des informations de journalisation détaillées sur le processus d’exportation et peut aider à détecter les problèmes lors de l’exportation. Si vous ouvrez un ticket avec Support Microsoft sur un problème lié à l’exportation de rapports de recherche, vous devrez peut-être fournir ce journal de suivi.
- **Éléments non indexés :** Document Excel qui contient des informations sur les éléments non indexés inclus dans les résultats de la recherche. Si vous n’incluez pas d’éléments non indexés lorsque vous générez le rapport des résultats de recherche, ce rapport sera toujours téléchargé, mais sera vide.
