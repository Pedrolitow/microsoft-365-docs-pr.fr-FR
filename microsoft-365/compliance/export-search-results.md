---
title: Exporter les résultats de la recherche de contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExport
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: ed48d448-3714-4c42-85f5-10f75f6a4278
description: Exportez les résultats de recherche à partir d’une recherche de contenu dans le centre Microsoft 365 conformité sur un ordinateur local. Les résultats des e-mails sont exportés en tant que fichiers PST. Le contenu de SharePoint sites OneDrive Entreprise sites sont exportés en tant que documents Office natifs.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8ec09706fecbe703fa2ab38cad5f8f8304484f44
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52536057"
---
# <a name="export-content-search-results"></a>Exporter les résultats de la recherche de contenu

Une fois qu’une recherche de contenu est correctement exécuté, vous pouvez exporter les résultats de la recherche vers un ordinateur local. Lorsque vous exportez des résultats du courrier électronique, ils sont téléchargés sur votre ordinateur dans des fichiers PST. Lorsque vous exportez du contenu à SharePoint sites OneDrive Entreprise sites, des copies de documents Office natifs sont exportées. D’autres documents et rapports sont inclus dans les résultats de recherche exportés.
  
L’exportation des résultats d’une recherche de contenu implique la préparation des résultats, puis leur téléchargement sur un ordinateur local.
  
## <a name="before-you-export-search-results"></a>Avant d’exporter les résultats de recherche

- Pour exporter les résultats de recherche, vous devez avoir le rôle de gestion Exportation dans le Centre de sécurité & conformité. Ce rôle est affecté au groupe de rôles Gestionnaire de découverte électronique intégré. Ce rôle n’est pas affecté par défaut au groupe de rôles Gestion de l’organisation. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).

- L’ordinateur que vous utilisez pour exporter les résultats de recherche doit répondre aux exigences système suivantes :
  
  - Dernière version de Windows (32 bits ou 64 bits)
  
  - Microsoft .NET Framework 4.7
  
- Vous devez utiliser l’un des navigateurs pris en charge suivants pour exécuter l’outil d’exportation eDiscovery<sup>1</sup>:

  - Microsoft Edge <sup>2</sup>
  
    OR

  - Microsoft Internet Explorer 10 versions ultérieures
  
  > [!NOTE]
  > <sup>1</sup> Microsoft ne fabrique pas d’extensions ou d’extensions tierces pour ClickOnce applications. L’exportation des résultats de recherche à l’aide d’un navigateur non pris en charge avec des extensions ou extensions tierces n’est pas prise en charge.<br/>
  > <sup>2</sup> Suite aux modifications récentes apportées à Microsoft Edge, ClickOnce prise en charge de la recherche n’est plus activée par défaut. Pour obtenir des instructions sur l’activation ClickOnce prise en charge dans Edge, voir Utiliser l’outil d’exportation [eDiscovery dans Microsoft Edge](configure-edge-to-export-search-results.md).
  
- Nous vous recommandons de télécharger les résultats de recherche sur un ordinateur local. Pour éliminer les problèmes de pare-feu ou d’infrastructure proxy de votre entreprise lors du téléchargement des résultats de recherche, vous pouvez envisager de télécharger les résultats de la recherche sur un bureau virtuel en dehors de votre réseau. Cela peut réduire les délai d’utilisation des connexions de données Azure lors de l’exportation d’un grand nombre de fichiers. Pour plus d’informations sur les bureaux virtuels, [voir Windows Virtual Desktop](https://azure.microsoft.com/services/virtual-desktop).

- Pour améliorer les performances lors du téléchargement des résultats de recherche, envisagez de diviser les recherches qui retournent un grand ensemble de résultats en recherches plus petites. Par exemple, vous pouvez utiliser des plages de dates dans les requêtes de recherche pour renvoyer un ensemble de résultats plus petit qui peut être téléchargé plus rapidement.
  
- Lorsque vous exportez des résultats de recherche, les données sont stockées temporairement dans un emplacement stockage Azure fourni par Microsoft dans le cloud Microsoft avant d’être téléchargées sur votre ordinateur local. Assurez-vous que votre organisation peut se connecter au point de terminaison dans Azure, qui est **\* .blob.core.windows.net** (le caractère générique représente un identificateur unique pour votre exportation). Les données des résultats de la recherche sont supprimées de l’emplacement stockage Azure deux semaines après leur création. 
  
- Si votre organisation utilise un serveur proxy pour communiquer avec Internet, vous devez définir les paramètres du serveur proxy sur l’ordinateur que vous utilisez pour exporter les résultats de la recherche (afin que l’outil d’exportation puisse être authentifié par votre serveur proxy). Pour ce faire, ouvrez *lemachine.config* à l’emplacement qui correspond à votre version de Windows. 
  
  - **32 bits :**`%windir%\Microsoft.NET\Framework\[version]\Config\machine.config`
  
  - **64 bits :**`%windir%\Microsoft.NET\Framework64\[version]\Config\machine.config`
  
    Ajoutez les lignes suivantes  *au fichiermachine.config*  quelque part entre les  `<configuration>` balises et les  `</configuration>` balises. N’oubliez pas  `ProxyServer` de remplacer et avec les  `Port` valeurs correctes pour votre organisation ; par exemple, `proxy01.contoso.com:80` . 
  
    ```xml
    <system.net>
       <defaultProxy enabled="true" useDefaultCredentials="true">
         <proxy proxyaddress="https://ProxyServer :Port " 
                usesystemdefault="False" 
                bypassonlocal="True" 
                autoDetect="False" />
       </defaultProxy>
    </system.net>
    ```

- Si les résultats d’une recherche de contenu sont plus anciens que 7 jours et que vous soumettez une tâche d’exportation, un message d’erreur s’affiche vous invite à réexécuter la recherche pour mettre à jour les résultats de la recherche. Si cela se produit, annulez l’exportation, réexécutez la recherche, puis recommencez l’exportation.

## <a name="step-1-prepare-search-results-for-export"></a>Étape 1 : Préparer les résultats de recherche pour l’exportation

Vous devez préparer les résultats de recherche pour l’exportation. Lorsque vous préparez les résultats, ils sont téléchargés vers un emplacement fourni par Microsoft stockage Azure dans le cloud Microsoft. Le contenu des boîtes aux lettres et des sites est téléchargé à un taux maximal de 2 Go par heure.
  
1. Dans le centre Microsoft 365 conformité, sélectionnez la recherche de contenu à partir de qui vous souhaitez exporter les résultats.
  
2. Dans le menu **Actions** en bas de la page volante, cliquez sur **Exporter les résultats.**

   ![Option Exporter les résultats dans le menu Actions](../media/ActionMenuExportResults.png)

   La page **de présentation** des résultats d’exportation s’affiche. Les options d’exportation disponibles pour exporter du contenu varient selon que les résultats de la recherche sont situés dans des boîtes aux lettres ou des sites ou une combinaison des deux.

3. Sous **Options de sortie,** choisissez l’une des options suivantes :
  
   ![Exporter les options de sortie](../media/ExportOutputOptions.png)

    - Tous les éléments, à l’exception de ceux dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été **indexés pour d’autres raisons.** Cette option exporte uniquement les éléments indexés.
  
    - Tous les éléments, y compris ceux qui ont un format non reconnu, sont chiffrés ou n’ont pas été **indexés pour d’autres raisons.** Cette option exporte les éléments indexés et non indexés.
  
    - Seuls les éléments qui ont un format non reconnu, sont chiffrés ou n’ont pas été indexés pour **d’autres raisons.** Cette option exporte uniquement les éléments nonndex.

      Consultez la section [Plus d’informations](#more-information) pour obtenir une description de l’exportation des éléments partiellement indexés. Pour plus d’informations sur les éléments partiellement indexés, voir [Éléments partiellement indexés dans la recherche de contenu.](partially-indexed-items-in-content-search.md)

4. Sous **Exporter Exchange contenu sous**, choisissez l’une des options suivantes :
  
   ![Exchange options](../media/ExchangeExportOptions.png)

    - **Un fichier PST pour chaque boîte aux** lettres : exporte un fichier PST pour chaque boîte aux lettres utilisateur qui contient les résultats de la recherche. Tous les résultats de la boîte aux lettres d’archivage de l’utilisateur sont inclus dans le même fichier PST. Cette option reproduit la structure de dossiers de boîte aux lettres à partir de la boîte aux lettres source.
  
    - **Un fichier PST** contenant tous les messages : exporte un fichier PST unique (nommé *Exchange.pst*) qui contient les résultats de recherche de toutes les boîtes aux lettres source incluses dans la recherche. Cette option reproduit la structure de dossiers de boîte aux lettres pour chaque message.
  
    - **Un fichier PST contenant** tous les messages dans un dossier unique : exporte les résultats de la recherche vers un seul fichier PST où tous les messages se trouvent dans un dossier de niveau supérieur unique. Cette option permet aux réviseurs de réviser les éléments dans l’ordre chronologique (les éléments sont triés par date d’envoi) sans avoir à naviguer dans la structure de dossiers de boîte aux lettres d’origine pour chaque élément.
  
    - **Messages individuels**: exporte les résultats de la recherche sous forme de messages électroniques individuels, au format .msg. Si vous sélectionnez cette option, les résultats de la recherche par courrier électronique sont exportés vers un dossier dans le système de fichiers. Le chemin d’accès au dossier des messages individuels est identique à celui utilisé si vous avez exporté les résultats dans un fichier PST.
  
5. Configurez les options supplémentaires suivantes :

   ![Configurer d’autres options d’exportation](../media/OtherExportOptions.png)

   1. Activez la case à cocher Activer la **déplication Exchange contenu** pour exclure les messages en double.
  
      Si vous sélectionnez cette option, une seule copie d’un message sera exportée, même si plusieurs copies du même message sont trouvées dans les boîtes aux lettres dans les recherches. Le rapport des résultats de l’exportation (qui est un fichier nommé Results.csv) contient une ligne pour chaque copie d’un message en double afin que vous pouvez identifier les boîtes aux lettres (ou dossiers publics) qui contiennent une copie du message en double. Pour plus d’informations sur la dédoplication et la façon dont les éléments dupliqués sont identifiés, voir Dédoplication dans les résultats de recherche [eDiscovery](de-duplication-in-ediscovery-search-results.md).
  
   2. Cochez **la case Inclure les versions SharePoint fichiers pour** exporter toutes les versions de SharePoint documents. Cette option s’affiche uniquement si les sources de contenu de la recherche incluent SharePoint ou OneDrive Entreprise sites.
  
   3. Sélectionnez **les fichiers d’exportation dans un dossier compressé (compressé). Inclut uniquement les messages individuels et SharePoint de documents** pour exporter les résultats de la recherche dans des dossiers compressés. Cette option s’affiche uniquement lorsque vous choisissez d’exporter Exchange éléments en tant que messages individuels et lorsque les résultats de la recherche incluent SharePoint ou OneDrive documents. Cette option est principalement utilisée pour contourner la limite de 260 caractères Windows noms de chemin d’accès lorsque des éléments sont exportés. Voir les « Noms de fichiers des éléments exportés » dans la section [Plus d’informations.](#more-information)
  
6. Cliquez **sur Exporter** pour démarrer le processus d’exportation. Les résultats de la recherche sont préparés pour le téléchargement, ce qui signifie qu’ils sont collectés à partir des emplacements de contenu d’origine, puis téléchargés vers un emplacement stockage Azure dans le cloud Microsoft. L'opération peut prendre plusieurs minutes.

Consultez la section suivante pour obtenir des instructions sur le téléchargement des résultats de recherche exportés.
  
## <a name="step-2-download-the-search-results"></a>Étape 2 : Télécharger les résultats de recherche

L’étape suivante consiste à télécharger les résultats de la recherche à partir stockage Azure’emplacement sur votre ordinateur local.
  
1. Dans la page **Recherche de** contenu dans le centre Microsoft 365 conformité, sélectionnez **l’onglet** Exportation
  
   Vous de devez peut-être cliquer sur **Actualiser** pour mettre à jour la liste des tâches d’exportation afin qu’elle affiche la tâche d’exportation que vous avez créée. Les travaux d’exportation ont le même nom que la recherche correspondante avec **_Export** au nom de recherche.
  
2. Sélectionnez la tâche d’exportation que vous avez créée à l’étape 1.

3. Dans la page volante sous **la touche Exporter,** cliquez **sur Copier dans le Presse-papiers.** Vous utilisez cette clé à l’étape 6 pour télécharger les résultats de la recherche.
  
   > [!IMPORTANT]
   > Étant donné que tout le monde peut installer et lancer l’outil d’exportation de découverte électronique, et utiliser cette clé pour télécharger les résultats de recherche, prenez toutes les précautions nécessaires pour protéger cette clé, comme vous le feriez avec les mots de passe ou d’autres informations de sécurité. 

4. En haut de la page volante, cliquez sur **Télécharger les résultats.**

5. Si vous êtes invité à installer l’outil **d’exportation eDiscovery,** cliquez sur **Installer.**

6. Dans **l’outil d’exportation eDiscovery,** faites les choses suivantes :

   ![Outil d’exportation eDiscovery](../media/eDiscoveryExportTool.png)

   1. Collez la clé d’exportation que vous avez copiée à l’étape 3 dans la zone appropriée.
  
   2. Cliquez sur **Parcourir** pour spécifier l’emplacement de téléchargement du fichier des résultats de recherche.
  
      > [!IMPORTANT]
      >  En raison d’une activité réseau élevée pendant le téléchargement, vous devez télécharger les résultats de recherche uniquement à un emplacement sur un lecteur interne sur votre ordinateur local. Pour une expérience de téléchargement de premier choix, suivez les instructions suivantes : <br/>
      >- Ne téléchargez pas les résultats de recherche dans un chemin UNC, un lecteur réseau mappé, un lecteur USB externe ou un compte OneDrive Entreprise synchronisé.<br/>
      >- Désactivez l’analyse antivirus pour le dossier dans qui vous téléchargez le résultat de la recherche.<br/>
      >- Téléchargez les résultats de recherche dans différents dossiers pour les travaux de téléchargement simultanés.

6. Cliquez sur **Démarrer** pour télécharger les résultats de recherche sur votre ordinateur.
  
    L’**outil d’exportation de découverte électronique** affiche l’état du processus d’exportation, ainsi qu’une estimation du nombre (et de la taille) d’éléments qui doivent encore être téléchargés. Une fois le processus d’exportation terminé, vous pouvez accéder aux fichiers à l’emplacement où ils ont été téléchargés.

## <a name="more-information"></a>Plus d’informations

Voici plus d’informations sur l’exportation des résultats de recherche.
  
[Limites d’exportation](#export-limits)
  
[Exporter des rapports](#export-reports)
  
[Exportation d’éléments partiellement indexés](#exporting-partially-indexed-items)

[Exportation de messages individuels ou de fichiers PST](#exporting-individual-messages-or-pst-files)

[Déchiffrement des messages électroniques protégés par RMS et des pièces jointes chiffrées](#decrypting-rms-protected-email-messages-and-encrypted-file-attachments)

[Noms de fichiers des éléments exportés](#filenames-of-exported-items)  
  
[Divers](#miscellaneous)
  
### <a name="export-limits"></a>Limites d’exportation

Pour plus d’informations sur les limites lors de l’exportation des résultats de recherche de contenu, voir la section « Limites d’exportation » dans [Limites pour la recherche de contenu.](limits-for-content-search.md#export-limits)

### <a name="export-reports"></a>Exporter des rapports
  
- Lorsque vous exportez des résultats de recherche, les rapports suivants sont inclus en plus des résultats de recherche.
  
  - **Résumé de l’exportation** Un Excel qui contient un résumé de l’exportation. Cela inclut des informations telles que le nombre de sources de contenu qui ont fait l’objet d’une recherche, les tailles estimées et téléchargées des résultats de la recherche, ainsi que le nombre estimé et téléchargé d’éléments exportés.
  
  - **Manifeste** Fichier manifeste (au format XML) qui contient des informations sur chaque élément inclus dans les résultats de la recherche.
  
  - **Résultats** Un Excel qui contient des informations sur chaque élément téléchargé en tant que résultat de recherche. Pour le courrier électronique, le journal des résultats contient des informations sur chaque message, y compris :
  
    - l’emplacement du message dans la boîte aux lettres source (notamment si le message est dans la boîte aux lettres principale ou d’archivage) ;
  
    - la date à laquelle le message a été envoyé ou reçu ;

    - l’objet du message ;

    - l’expéditeur et les destinataires du message.

    - Indique si le message est un message en double si vous avez activé l’option de déplication lors de l’exportation des résultats de la recherche. Les messages en double ont une valeur dans **la** colonne Dupliquer vers l’élément qui identifie le message en tant que doublon. La valeur de la colonne **Dupliquer** vers l’élément contient l’identité de l’élément du message exporté. Pour plus d’informations, voir Dédoublement dans les résultats de recherche [eDiscovery.](de-duplication-in-ediscovery-search-results.md)

      Pour les documents provenant SharePoint sites OneDrive Entreprise sites web, le journal des résultats contient des informations sur chaque document, notamment :

      - l’URL du document ;

      - l’URL de la collection de sites qui héberge le document ;

      - la date à laquelle le document a été modifié pour la dernière fois ;

      - le nom du document (qui se trouve dans la colonne Objet du journal des résultats).

  - **Éléments nonndexés** Un Excel qui contient des informations sur les éléments partiellement indexés qui seraient inclus dans les résultats de la recherche. Si vous n’incluez pas d’éléments partiellement indexés lorsque vous générez le rapport des résultats de la recherche, ce rapport sera toujours téléchargé, mais il sera vide.

  - **Erreurs et avertissements** Contient des erreurs et des avertissements pour les fichiers rencontrés lors de l’exportation. Consultez la colonne Détails de l’erreur pour obtenir des informations spécifiques à chaque erreur ou avertissement.

  - **Éléments ignorés** Lorsque vous exportez des résultats de recherche à SharePoint et OneDrive Entreprise sites, l’exportation inclut généralement un rapport d’éléments ignorés (SkippedItems.csv). Les éléments mentionnés dans ce rapport sont généralement des éléments qui ne sont pas téléchargés, tels qu’un dossier ou un ensemble de documents. L’exportation de ces types d’éléments n’est pas une exportation par conception. Pour les autres éléments ignorés, les champs « Type d’erreur » et « Détails de l’erreur » dans le rapport d’éléments ignorés indiquent la raison pour laquelle l’élément a été ignoré et n’a pas été téléchargé avec les autres résultats de recherche.

  - **Trace.log Contient des** informations de journalisation détaillées sur le processus d’exportation et peut vous aider à découvrir les problèmes pendant l’exportation. Si vous ouvrez un ticket avec le Support Microsoft à propos d’un problème lié à l’exportation des résultats de recherche, vous pouvez être invité à fournir ce journal de suivi.
  
    > [!NOTE]
    > Vous pouvez simplement exporter ces documents sans avoir à exporter les résultats de recherche réels. Voir [Exporter un rapport de recherche de contenu.](export-a-content-search-report.md)
  
### <a name="exporting-partially-indexed-items"></a>Exportation d’éléments partiellement indexés
  
- Si vous exportez des éléments de boîte aux lettres à partir d’une recherche de contenu qui renvoie tous les éléments de boîte aux lettres dans les résultats de la recherche (car aucun mot clé n’est inclus dans la requête de recherche), les éléments partiellement indexés ne seront pas copiés dans le fichier PST qui contient les éléments non indexés. En effet, tous les éléments, y compris les éléments partiellement indexés, sont automatiquement inclus dans les résultats de recherche ordinaires. Cela signifie que les éléments partiellement indexés seront inclus dans un fichier PST (ou sous forme de messages individuels) qui contient les autres éléments indexés.

    Si vous exportez à la fois les éléments indexés et partiellement indexés ou si vous exportez uniquement les éléments indexés à partir d’une recherche de contenu qui renvoie tous les éléments, le même nombre d’éléments sera téléchargé. Cela se produit même si les résultats de recherche estimés pour la recherche de contenu (affichés dans les statistiques de recherche dans le Centre de sécurité & conformité) incluront toujours une estimation distincte du nombre d’éléments partiellement indexés. Par exemple, supposons que l’estimation d’une recherche qui inclut tous les éléments (aucun mot clé dans la requête de recherche) indique que 1 000 éléments ont été trouvés et que 200 éléments partiellement indexés ont également été trouvés. Dans ce cas, les 1 000 éléments incluent les éléments partiellement indexés, car la recherche renvoie tous les éléments. En d’autres termes, il y a 1 000 éléments au total renvoyés par la recherche, et non 1 200 éléments (comme vous pouvez vous y attendre). Si vous exportez les résultats de cette recherche et choisissez d’exporter des éléments indexés et partiellement indexés (ou n’exportez que des éléments partiellement indexés), 1 000 éléments seront téléchargés. Là encore, les éléments partiellement indexés sont inclus dans les résultats réguliers (indexés) lorsque vous utilisez une requête de recherche vide pour renvoyer tous les éléments. Dans ce même exemple, si vous choisissez d’exporter uniquement des éléments partiellement indexés, seuls les 200 éléments non indexés seront téléchargés.

    Notez également que dans l’exemple précédent (lorsque vous exportez des éléments indexés et partiellement indexés ou que vous exportez uniquement des éléments indexés), le rapport de synthèse d’exportation inclus avec les résultats de recherche exportés résumait 1 000 éléments estimés et 1 000 éléments téléchargés pour les mêmes raisons que précédemment décrites.  

- Si la recherche dont vous exportez les résultats était une recherche d’emplacements de contenu spécifiques ou de tous les emplacements de contenu de votre organisation, seuls les éléments partiels provenant d’emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche seront exportés. En d’autres termes, si aucun résultat de recherche n’est trouvé dans une boîte aux lettres ou un site, les éléments partiellement indexés dans cette boîte aux lettres ou ce site ne seront pas exportés. En effet, l’exportation d’éléments partiellement indexés à partir de nombreux emplacements de l’organisation peut augmenter la probabilité d’erreurs d’exportation et augmenter le temps d’exportation et de téléchargement des résultats de la recherche.

    Pour exporter des éléments partiellement indexés à partir de tous les emplacements de contenu pour une recherche, configurez la recherche pour qu’elle retourne tous les éléments (en supprimant tous les mots clés de la requête de recherche), puis exportez uniquement les éléments partiellement indexés lorsque vous exportez les résultats de la recherche.

    ![Utiliser la troisième option d’exportation pour exporter uniquement les éléments nonndex](../media/5d7be338-a0e5-425f-8ba5-92769c24bf75.png)
  
- Lors de l’exportation des résultats de recherche à partir de sites SharePoint ou OneDrive Entreprise, la possibilité d’exporter des éléments non indexés dépend également de l’option d’exportation que vous sélectionnez et du fait qu’un site qui a fait l’objet d’une recherche contienne un élément indexé qui correspond aux critères de recherche. Par exemple, si vous recherchez des sites SharePoint ou OneDrive Entreprise spécifiques et qu’aucun résultat de recherche n’est trouvé, aucun éléments non indexés de ces sites n’est exporté si vous choisissez la deuxième option d’exportation pour exporter les éléments indexés et non indexés. Si un élément indexé d’un site correspond aux critères de recherche, tous les éléments non indexés de ce site sont exportés lors de l’exportation des éléments indexés et non indexés. L’illustration suivante décrit les options d’exportation selon qu’un site contient un élément indexé qui correspond aux critères de recherche.

    ![Choisissez l’option d’exportation selon qu’un site contient un élément indexé qui correspond aux critères de recherche](../media/94f78786-c6bb-42fb-96b3-7ea3998bcd39.png)

    a. Seuls les éléments indexés qui correspondent aux critères de recherche sont exportés. Aucun des éléments partiellement indexés n’est exporté.

    b. Si aucun des éléments indexés d’un site ne correspond aux critères de recherche, les éléments partiellement indexés à partir de ce même site ne sont pas exportés. Si les éléments indexés d’un site sont renvoyés dans les résultats de la recherche, les éléments partiellement indexés de ce site sont exportés. En d’autres termes, seuls les éléments partiellement indexés à partir de sites qui contiennent des éléments qui correspondent aux critères de recherche sont exportés.

    c. Tous les éléments partiellement indexés de tous les sites de la recherche sont exportés, qu’un site contienne ou non des éléments qui correspondent aux critères de recherche.

    Si vous choisissez d’exporter des éléments partiellement indexés, les éléments de boîte aux lettres partiellement indexés sont exportés dans un fichier PST distinct, quelle que soit l’option que vous choisissez sous Exporter le contenu **Exchange** en tant que .

- Si des éléments partiellement indexés sont renvoyés dans les résultats de la recherche (car d’autres propriétés d’éléments partiellement indexés correspondent aux critères de recherche), ceux partiellement indexés sont exportés avec les résultats de recherche ordinaires. Par conséquent, si vous choisissez d’exporter à la fois les éléments indexés et les éléments partiellement indexés (en sélectionnant tous les éléments, y compris ceux dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour **d’autres** raisons d’exportation), les éléments partiellement indexés exportés avec les résultats réguliers sont répertoriés dans le rapport Results.csv. Ils ne sont pas répertoriés dans le rapport de items.csv non-ndes.
  
### <a name="exporting-individual-messages-or-pst-files"></a>Exportation de messages individuels ou de fichiers PST
  
- Si le nom du chemin d’accès d’un message dépasse la limite de caractères maximale Windows, le nom du chemin d’accès du fichier est tronqué. Toutefois, le nom du chemin d’accès du fichier d’origine sera répertorié dans le manifeste et resultsLog.
  
- Comme indiqué précédemment, les résultats de la recherche de courrier électronique sont exportés vers un dossier dans le système de fichiers. Le chemin d’accès du dossier pour les messages individuels réplique le chemin d’accès du dossier dans la boîte aux lettres de l’utilisateur. Par exemple, pour une recherche nommée « ContosoCase101 » messages dans la boîte de réception d’un utilisateur se trouve dans le chemin d’accès du dossier  `~ContosoCase101\\<date of export\Exchange\user@contoso.com (Primary)\Top of Information Store\Inbox` .

- Si vous choisissez d’exporter des messages électroniques dans un fichier  PST contenant tous les messages d’un même dossier, un dossier Éléments supprimés et un dossier **Dossiers** de recherche sont inclus dans le niveau supérieur du dossier PST. Ces dossiers sont vides.

- Comme indiqué précédemment, vous devez exporter les résultats de la recherche de courrier électronique en tant que messages individuels pour déchiffrer les messages protégés par RMS lorsqu’ils sont exportés. Les messages chiffrés restent chiffrés si vous exportez les résultats de la recherche de courrier électronique en tant que fichier PST.
  
### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments"></a>Déchiffrement des messages électroniques protégés par RMS et des pièces jointes chiffrées

Tous les messages électroniques protégés par des droits (protégés par RMS) inclus dans les résultats d’une recherche de contenu sont déchiffrés lorsque vous les exportez. En outre, tout fichier chiffré avec une technologie de chiffrement [Microsoft](encryption.md) et joint à un message électronique inclus dans les résultats de la recherche est également déchiffré lorsqu’il est exporté. Cette fonctionnalité de déchiffrement est activée par défaut pour les membres du groupe de rôles Gestionnaire eDiscovery. Cela est dû au fait que le rôle de gestion déchiffrement RMS est attribué par défaut à ce groupe de rôles. Gardez les points suivants à l’esprit lors de l’exportation de pièces jointes et de messages électroniques chiffrés :
  
- Comme indiqué précédemment, pour déchiffrer les messages protégés par RMS lorsque vous les exportez, vous devez exporter les résultats de la recherche en tant que messages individuels. Si vous exportez des résultats de recherche dans un fichier PST, les messages protégés par RMS restent chiffrés.

- Les messages déchiffrés sont identifiés dans le **rapport ResultsLog.** Ce rapport contient une colonne nommée **État** du décodage et une valeur **décodée** dans cette colonne identifie les messages qui ont été déchiffrés.

- Outre le déchiffrement des pièces jointes lors de l’exportation des résultats de recherche, vous pouvez afficher un aperçu du fichier déchiffré lors de l’aperçu des résultats de recherche. Vous pouvez uniquement afficher le message électronique protégé par des droits après l’avoir exporté.

- Pour l’instant, la fonctionnalité de déchiffrement lors de l’exportation des résultats de recherche n’inclut pas le contenu chiffré des sites SharePoint et OneDrive Entreprise sites. Toutefois, la prise en charge des documents chiffrés avec les technologies de chiffrement Microsoft et stockés dans SharePoint Online et OneDrive Entreprise.

- Si vous devez empêcher quelqu’un de déchiffrer les messages protégés par RMS et les pièces jointes chiffrées, vous devez créer un groupe de rôles personnalisé (en copiant le groupe de rôles gestionnaire eDiscovery intégré), puis supprimer le rôle de gestion déchiffrement RMS du groupe de rôles personnalisé. Ajoutez ensuite la personne qui ne doit pas déchiffrer les messages en tant que membre du groupe de rôles personnalisé.
  
### <a name="filenames-of-exported-items"></a>Noms de fichiers des éléments exportés
  
- Il existe une limite de 260 caractères (imposée par le système d’exploitation) pour le nom du chemin d’accès complet pour les messages électroniques et les documents de site exportés vers votre ordinateur local. Le nom complet du chemin d’accès des éléments exportés inclut l’emplacement d’origine de l’élément et l’emplacement du dossier sur l’ordinateur local sur lequel les résultats de la recherche sont téléchargés. Par exemple, si vous spécifiez de télécharger les résultats de recherche dans l’outil d’exportation  `C:\Users\Admin\Desktop\SearchResults` eDiscovery, le chemin d’accès complet d’un élément de courrier téléchargé est  `C:\Users\Admin\Desktop\SearchResults\ContentSearch1\03.15.2017-1242PM\Exchange\sarad@contoso.com (Primary)\Top of Information Store\Inbox\Insider trading investigation.msg` .

- Si la limite de 260 caractères est dépassée, le nom du chemin d’accès complet d’un élément est tronqué, en fonction des éléments suivants :

  - Si le nom du chemin d’accès complet est plus de 260 caractères, le nom de fichier est raccourci pour passer sous la limite ; Notez que le nom de fichier tronqué (à l’exception de l’extension de fichier) ne sera pas inférieur à huit caractères.

  - Si le nom du chemin d’accès complet est encore trop long après avoir raccourci le nom de fichier, l’élément est déplacé de son emplacement actuel vers le dossier parent. Si le chemin d’accès est encore trop long, le processus est répété : raccourcissez le nom de fichier et, si nécessaire, déplacez à nouveau vers le dossier parent. Ce processus est répété jusqu’à ce que le chemin d’accès complet soit sous la limite de 260 caractères.

  - Si un nom de chemin d’accès complet tronqué existe déjà, un numéro de version est ajouté à la fin du nom de fichier ; par exemple, `statusmessage(2).msg` .

    Pour atténuer ce problème, envisagez de télécharger les résultats de la recherche vers un emplacement avec un nom de chemin d’accès court . par exemple, le téléchargement des résultats de recherche dans un dossier nommé ajouterait moins de caractères aux noms de chemin d’accès des éléments exportés que de les télécharger dans un  `C:\Results` dossier nommé  `C:\Users\Admin\Desktop\Results` .

- Lorsque vous exportez des documents de site, il est également possible que le nom de fichier d’origine d’un document soit modifié. Cela se produit spécifiquement pour les documents qui ont été supprimés d’un site SharePoint ou OneDrive Entreprise qui a été mis en attente. Une fois qu’un document qui se trouve sur un site placé en conservation est supprimé, le document supprimé est automatiquement déplacé vers la bibliothèque de conservation et de préservation du site (qui a été créée lorsque le site a été placé en conservation). Lorsque le document supprimé est déplacé vers la bibliothèque de conservation et de préservation des documents, un ID unique et généré de manière aléatoire est ensuite intégré au nom de fichier d’origine du document. Par exemple, si le nom de fichier d’un document est et que ce document est ensuite supprimé et déplacé vers la bibliothèque de conservation et de préservation, le nom de fichier du document déplacé vers la bibliothèque de conservation et de préservation des documents est modifié comme . `FY2017Budget.xlsx` `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx` Si un document de la bibliothèque de conservation et de préservation correspond à la requête d’une recherche de contenu et que vous exportez les résultats de cette recherche, le fichier exporté a le nom de fichier modifié . dans cet exemple, le nom de fichier du document exporté serait  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx` .

    Lorsqu’un document sur un site en attente est modifié (et que le système de version de la bibliothèque de documents du site a été activé), une copie du fichier est automatiquement créée dans la bibliothèque de conservation et de préservation des documents. Dans ce cas, un ID unique et généré de manière aléatoire est également appendé au nom de fichier du document copié dans la bibliothèque de conservation et de préservation.

    La raison pour laquelle les noms de fichiers des documents déplacés ou copiés dans la bibliothèque de conservation et de préservation des documents est pour éviter les conflits de noms de fichiers. Pour plus d’informations sur le placement d’une conservation sur les sites et la bibliothèque de conservation, voir Vue d’ensemble de la conservation in place dans [SharePoint Server 2016](https://support.office.com/article/5e400d68-cd51-444a-8fe6-e4df1d20aa95).

### <a name="miscellaneous"></a>Divers
  
- Lorsque vous téléchargez des résultats de recherche à l’aide de l’outil d’exportation eDiscovery, il est possible que vous receviez l’erreur suivante : Il s’agit d’une erreur passagère, qui se produit généralement à `System.Net.WebException: The remote server returned an error: (412) The condition specified using HTTP conditional header(s) is not met.` l’emplacement stockage Azure. Pour résoudre ce problème, réessayez de [télécharger](#step-2-download-the-search-results)les résultats de la recherche, ce qui redémarrera l’outil d’exportation eDiscovery.

- Tous les résultats de recherche et les rapports d’exportation sont inclus dans un dossier qui a le même nom que la recherche de contenu. Les courriers électroniques exportés se trouvent dans un dossier nommé **Exchange**. Les documents se trouvent dans un dossier nommé **SharePoint**.

- Les métadonnées du système de fichiers pour les documents SharePoint sites OneDrive Entreprise sont conservées lorsque les documents sont exportés vers votre ordinateur local. En d’autres termes, les propriétés de document (par exemple, Date de création et Date de la dernière modification) ne sont pas modifiées lorsque les documents sont exportés.

- Si vos résultats de recherche incluent un élément de liste provenant de SharePoint qui correspond à la requête de recherche, toutes les lignes de la liste sont exportées en plus de l’élément qui correspond à la requête de recherche et des pièces jointes de la liste. La raison de ce comportement est de fournir un contexte pour les éléments de liste qui sont renvoyés dans les résultats de la recherche. Les éléments de liste et pièces jointes supplémentaires peuvent entraîner une différence entre le nombre d’éléments exportés et l’estimation initiale des résultats de la recherche.
