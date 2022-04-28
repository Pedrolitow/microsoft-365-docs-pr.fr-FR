---
title: Exporter un rapport de recherche de contenu
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExportReport
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 5c8c1db6-d8ac-4dbb-8a7a-f65d452169b9
description: Au lieu d’exporter les résultats réels d’une recherche de contenu dans le portail de conformité Microsoft Purview, vous pouvez exporter un rapport de résultats de recherche. Le rapport contient un résumé des résultats de la recherche et un document contenant des informations détaillées sur chaque élément qui serait exporté.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 35e0a0b13594a6396ae1f757e3a1fc8a3e952173
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093062"
---
# <a name="export-a-content-search-report"></a>Exporter un rapport de recherche de contenu

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Au lieu d’exporter l’ensemble complet des résultats de recherche à partir d’une recherche de contenu dans le portail de conformité Microsoft Purview (ou à partir d’une recherche associée à un cas Microsoft Purview eDiscovery (Standard), vous pouvez exporter les mêmes rapports générés lorsque vous exportez les résultats de recherche réels.
  
Lorsque vous exportez un rapport, les fichiers de rapport sont téléchargés dans un dossier sur votre ordinateur local qui porte le même nom que la recherche de contenu, mais qui est ajouté à *_ReportsOnly*. Par exemple, si la recherche de contenu est nommée  *ContosoCase0815*, le rapport est téléchargé dans un dossier nommé *ContosoCase0815_ReportsOnly*. Pour obtenir la liste des documents inclus dans le rapport, consultez [ce qui est inclus dans le rapport](#whats-included-in-the-report).

## <a name="before-you-export-a-search-report"></a>Avant d’exporter un rapport de recherche

- Pour exporter un rapport de recherche, vous devez disposer du rôle de gestion de la recherche de conformité dans le portail de conformité. Ce rôle est attribué par défaut aux groupes de rôles eDiscovery Manager et Organization Management intégrés. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).

- Lorsque vous exportez un rapport, les données sont temporairement stockées dans un emplacement stockage Azure dans le cloud Microsoft avant d’être téléchargées sur votre ordinateur local. Assurez-vous que votre organisation peut se connecter au point de terminaison dans Azure, qui est **\*.blob.core.windows.net** (le caractère générique représente un identificateur unique pour votre exportation). Les données des résultats de la recherche sont supprimées de l’emplacement stockage Azure deux semaines après leur création.

- L’ordinateur que vous utilisez pour exporter le rapport de recherche doit répondre aux exigences système suivantes :
  
  - Dernière version de Windows (32 bits ou 64 bits)
  
  - Microsoft .NET Framework 4.7 ou version ultérieure
  
- Vous devez utiliser Microsoft Edge <sup>1</sup> pour exécuter l’outil d’exportation eDiscovery. L’utilisation d’Internet Explorer 11 pour exporter les résultats de la recherche n’est plus prise <sup>en charge2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> Suite aux modifications récentes apportées à Microsoft Edge, ClickOnce prise en charge n’est plus activée par défaut. Pour obtenir des instructions sur l’activation de ClickOnce prise en charge dans Edge, consultez [Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge](configure-edge-to-export-search-results.md). En outre, Microsoft ne fabrique pas d’extensions ou de modules complémentaires tiers pour les applications ClickOnce. L’exportation des résultats de recherche à l’aide d’un navigateur non pris en charge avec des extensions ou des modules complémentaires tiers n’est pas prise en charge.
  > 
  > <sup>2</sup> À compter d’août 2021, Microsoft 365 applications et services ne prendront plus en charge Internet Explorer 11 (IE11) et les utilisateurs peuvent avoir une expérience dégradée ou ne pas pouvoir se connecter à ces applications et services. Ces applications et services seront progressivement supprimés au cours des semaines et des mois à venir pour garantir une fin de support fluide. Chaque application et service sont progressivement supprimés selon des planifications indépendantes. Pour plus d’informations, consultez ce [billet de blog](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Si la taille totale estimée des résultats retournés par la recherche dépasse 2 To, l’exportation des rapports échoue. Pour exporter correctement les rapports, essayez de limiter l’étendue et de réexécuter la recherche afin que la taille estimée des résultats soit inférieure à 2 To.

- Si les résultats d’une recherche sont antérieurs à 7 jours et que vous envoyez un travail de rapport d’exportation, un message d’erreur s’affiche, vous invitant à réexécuter la recherche pour mettre à jour les résultats de la recherche. Si cela se produit, annulez l’exportation, réexécutez la recherche, puis redémarrez l’exportation.

- L’exportation de rapports de recherche est comptabilisée par rapport au nombre maximal d’exportations exécutées en même temps et au nombre maximal d’exportations qu’un seul utilisateur peut exécuter. Pour plus d’informations sur les limites d’exportation, consultez [les résultats de la recherche de contenu d’exportation](export-search-results.md#export-limits).
  
## <a name="step-1-generate-the-report-for-export"></a>Étape 1 : Générer le rapport pour l’exportation

La première étape consiste à préparer le rapport pour le téléchargement sur votre ordinateur à l’exportation. Lorsque vous exportez le rapport, les documents de rapport sont chargés dans une zone stockage Azure dans le cloud Microsoft.
  
1. Dans le portail de conformité, sélectionnez la recherche de contenu à partir de laquelle vous souhaitez exporter le rapport.
  
2. Dans le menu **Actions** en bas de la page de menu volant de recherche, cliquez sur **Exporter le rapport**.

   ![Option Exporter le rapport dans le menu Actions.](../media/ActionMenuExportReport.png)

   La page de menu volant **exporter le rapport** s’affiche. Les options de rapport d’exportation disponibles pour exporter des informations sur la recherche varient selon que les résultats de la recherche se trouvent dans des boîtes aux lettres ou des sites ou une combinaison des deux.
  
3. Sous **Options de sortie**, choisissez l’une des options suivantes :
  
   ![Exporter les options de sortie.](../media/ExportOutputOptions.png)

    - **Tous les éléments, à l’exception de celles dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour d’autres raisons**. Cette option exporte uniquement des informations sur les éléments indexés.
  
    - **Tous les éléments, y compris ceux dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour d’autres raisons**. Cette option exporte des informations sur les éléments indexés et non indexés.
  
    - **Seuls les éléments dont le format n’est pas reconnu sont chiffrés ou qui n’ont pas été indexés pour d’autres raisons**. Cette option exporte uniquement des informations sur les éléments non indexés.

4. Configurez l’option **Activer la dédoublement pour Exchange contenu**.
  
   - Si vous sélectionnez cette option, le nombre de messages en double (avant la déduplication et après la déduplication) est inclus dans le rapport récapitulatif d’exportation. En outre, une seule copie d’un message est incluse dans le fichier manifest.xml. Toutefois, le rapport des résultats d’exportation contient une ligne pour chaque copie d’un message en double afin que vous puissiez identifier les boîtes aux lettres qui contiennent une copie du message en double. Pour plus d’informations sur les rapports exportés, consultez [ce qui est inclus dans le rapport](#whats-included-in-the-report).

   - Si vous ne sélectionnez pas cette option, les rapports d’exportation contiennent des informations sur tous les messages retournés par la recherche, y compris les doublons.

     Pour plus d’informations sur la déduplication et la façon dont les éléments en double sont identifiés, consultez [Déduplication dans les résultats de la recherche eDiscovery](de-duplication-in-ediscovery-search-results.md).

5. Cliquez sur **Générer un rapport**.

   Les rapports de recherche sont préparés pour le téléchargement, ce qui signifie que les documents de rapport sont chargés à un emplacement stockage Azure dans le cloud Microsoft. L'opération peut prendre plusieurs minutes.

Consultez la section suivante pour obtenir des instructions pour télécharger les rapports de recherche exportés.
  
## <a name="step-2-download-the-report"></a>Étape 2 : Télécharger le rapport

L’étape suivante consiste à télécharger le rapport à partir de la zone stockage Azure sur votre ordinateur local.

> [!NOTE]
> Le rapport de recherche exporté doit être téléchargé dans les 14 jours suivant la génération du rapport à l’étape 1.

1. Dans la page **Recherche de contenu** dans le portail de conformité, sélectionnez l’onglet **Exportations**
  
   Vous devrez peut-être cliquer sur **Actualiser** pour mettre à jour la liste des travaux d’exportation afin qu’elle affiche le travail d’exportation que vous avez créé. Les tâches de rapport d’exportation ont le même nom que la recherche correspondante avec **_ReportsOnly** ajoutée au nom de recherche.
  
2. Sélectionnez le travail d’exportation que vous avez créé à l’étape 1.

3. Dans la page de menu volant **Exporter le rapport** sous **Clé d’exportation**, cliquez sur **Copier dans le Presse-papiers**. Vous utilisez cette clé à l’étape 6 pour télécharger les résultats de la recherche.
  
   > [!IMPORTANT]
   > Étant donné que n’importe qui peut installer et démarrer l’outil d’exportation eDiscovery, puis utiliser cette clé pour télécharger le rapport de recherche, veillez à prendre des précautions pour protéger cette clé tout comme vous protégeriez les mots de passe ou d’autres informations relatives à la sécurité.

4. En haut de la page de menu volant, cliquez sur **Télécharger les résultats**.

5. Si vous êtes invité à installer **l’outil d’exportation eDiscovery**, cliquez sur **Installer**.

6. Dans **l’outil d’exportation eDiscovery**, procédez comme suit :

   ![Outil d’exportation eDiscovery.](../media/eDiscoveryExportTool.png)

   1. Collez la clé d’exportation que vous avez copiée à l’étape 3 dans la zone appropriée.
  
   2. Cliquez sur **Parcourir** pour spécifier l’emplacement où vous souhaitez télécharger les fichiers de rapport de recherche.

7. Cliquez sur **Démarrer** pour télécharger les résultats de recherche sur votre ordinateur.
  
    L’**outil d’exportation de découverte électronique** affiche l’état du processus d’exportation, ainsi qu’une estimation du nombre (et de la taille) d’éléments qui doivent encore être téléchargés. Lorsque le processus d’exportation est terminé, vous pouvez accéder aux fichiers à l’emplacement où ils ont été téléchargés.
  
## <a name="whats-included-in-the-report"></a>Éléments inclus dans le rapport

Lorsque vous générez et exportez un rapport sur les résultats d’une recherche de contenu, les documents suivants sont téléchargés :
  
- **Résumé de l’exportation :** Document Excel qui contient un résumé de l’exportation. Cela inclut des informations telles que le nombre de sources de contenu qui ont été recherchées, le nombre de résultats de recherche à partir de chaque emplacement de contenu, le nombre estimé d’éléments, le nombre réel d’éléments qui seraient exportés et la taille estimée et réelle des éléments qui seraient exportés.

   Si vous incluez des éléments non indexés lors de l’exportation du rapport, le nombre d’éléments non indexés est inclus dans le nombre total de résultats de recherche estimés et dans le nombre total de résultats de recherche téléchargés (si vous exportez les résultats de la recherche) qui sont répertoriés dans le rapport récapitulatif d’exportation. En d’autres termes, le nombre total d’éléments qui seraient téléchargés est égal au nombre total de résultats estimés et au nombre total d’éléments non indexés.
  
- **Manifeste:** Fichier manifeste (au format XML) qui contient des informations sur chaque élément inclus dans les résultats de la recherche. Si vous avez activé l’option de déduplication, les messages en double ne sont pas inclus dans le fichier manifeste.

- **Résultats:** Document Excel qui contient une ligne contenant des informations sur chaque élément indexé qui serait exporté avec les résultats de la recherche. Pour le courrier électronique, le journal des résultats contient des informations sur chaque message, y compris : 

  - l’emplacement du message dans la boîte aux lettres source (notamment si le message est dans la boîte aux lettres principale ou d’archivage) ;

  - la date à laquelle le message a été envoyé ou reçu ;

  - l’objet du message ;

  - l’expéditeur et les destinataires du message.

  Pour les documents des sites SharePoint et OneDrive Entreprise, le journal des résultats contient des informations sur chaque document, notamment :

  - l’URL du document ;

  - l’URL de la collection de sites qui héberge le document ;

  - la date à laquelle le document a été modifié pour la dernière fois ;

  - le nom du document (qui se trouve dans la colonne Objet du journal des résultats).

  > [!NOTE]
  > Le nombre de lignes dans le rapport **résultats** doit être égal au nombre total de résultats de recherche moins le nombre total d’éléments répertoriés dans le rapport **Éléments non indexés** .
  
- **Trace.log :** Journal de suivi qui contient des informations de journalisation détaillées sur le processus d’exportation et qui peut aider à détecter les problèmes lors de l’exportation. Si vous ouvrez un ticket avec Support Microsoft à propos d’un problème lié à l’exportation de rapports de recherche, vous pouvez être invité à fournir ce journal de suivi.

- **Éléments non indexés :** Document Excel qui contient des informations sur les éléments non indexés inclus dans les résultats de la recherche. Si vous n’incluez pas d’éléments non indexés lorsque vous générez le rapport de résultats de recherche, ce rapport est toujours téléchargé, mais il est vide.
