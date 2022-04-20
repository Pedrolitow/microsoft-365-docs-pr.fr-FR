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
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: ed48d448-3714-4c42-85f5-10f75f6a4278
description: Exportez les résultats de la recherche à partir d’une recherche de contenu dans le portail de conformité Microsoft Purview vers un ordinateur local. Les résultats de l’e-mail sont exportés sous forme de fichiers PST. Le contenu des sites SharePoint et OneDrive Entreprise est exporté en tant que documents Office natifs.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 38faaf29087e67aef161e46a1fbc6c338d9c33e4
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995467"
---
# <a name="export-content-search-results"></a>Exporter les résultats de la recherche de contenu

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Une fois la recherche de contenu exécutée, vous pouvez exporter les résultats de la recherche vers un ordinateur local. Lorsque vous exportez des résultats du courrier électronique, ils sont téléchargés sur votre ordinateur dans des fichiers PST. Lorsque vous exportez du contenu à partir de sites SharePoint et OneDrive Entreprise, des copies de documents Office natifs sont exportées. D’autres documents et rapports sont inclus dans les résultats de recherche exportés.
  
L’exportation des résultats d’une recherche de contenu implique la préparation des résultats, puis leur téléchargement sur un ordinateur local. Ces étapes d’exportation des résultats de recherche s’appliquent également à l’exportation des résultats d’une recherche associée à des cas de découverte électronique Microsoft Purview (Standard).
  
## <a name="before-you-export-search-results"></a>Avant d’exporter les résultats de la recherche

- Pour exporter les résultats de la recherche, vous devez disposer du rôle de gestion d’exportation dans le portail de conformité Microsoft Purview. Ce rôle est affecté au groupe de rôles Gestionnaire de découverte électronique intégré. Ce rôle n’est pas affecté par défaut au groupe de rôles Gestion de l’organisation. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).

- L’ordinateur que vous utilisez pour exporter les résultats de recherche doit répondre aux exigences système suivantes :
  
  - Dernière version de Windows (32 bits ou 64 bits)
  
  - Microsoft .NET Framework 4.7 ou version ultérieure
  
- Vous devez utiliser Microsoft Edge <sup>1</sup> pour exécuter l’outil d’exportation eDiscovery. L’utilisation d’Internet Explorer 11 pour exporter les résultats de la recherche n’est plus prise <sup>en charge2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> Suite aux modifications récentes apportées à Microsoft Edge, ClickOnce prise en charge n’est plus activée par défaut. Pour obtenir des instructions sur l’activation de ClickOnce prise en charge dans Edge, consultez [Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge](configure-edge-to-export-search-results.md). En outre, Microsoft ne fabrique pas d’extensions ou de modules complémentaires tiers pour les applications ClickOnce. L’exportation des résultats de recherche à l’aide d’un navigateur non pris en charge avec des extensions ou des modules complémentaires tiers n’est pas prise en charge.
  >
  > <sup>2</sup> À compter d’août 2021, Microsoft 365 applications et services ne prendront plus en charge Internet Explorer 11 (IE11) et les utilisateurs peuvent avoir une expérience dégradée ou ne pas pouvoir se connecter à ces applications et services. Ces applications et services seront progressivement supprimés au cours des semaines et des mois à venir pour garantir une fin de support fluide. Chaque application et service sont progressivement supprimés selon des planifications indépendantes. Pour plus d’informations, consultez ce [billet de blog](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- L’outil d’exportation eDiscovery que vous utilisez à l’étape 2 pour télécharger les résultats de la recherche ne prend pas en charge l’automatisation (à l’aide d’un script ou d’applets de commande en cours d’exécution). Nous vous recommandons vivement de ne pas automatiser le processus de préparation à l’étape 1 ou le processus de téléchargement à l’étape 2. Si vous automatiser l’un de ces processus, Support Microsoft ne fournira pas d’assistance si vous rencontrez des problèmes.

- Nous vous recommandons de télécharger les résultats de la recherche sur un ordinateur local. Pour empêcher le pare-feu ou l’infrastructure proxy de votre entreprise de provoquer des problèmes lors du téléchargement des résultats de la recherche, vous pouvez envisager de télécharger les résultats de la recherche sur un bureau virtuel en dehors de votre réseau. Cela peut réduire les délais d’expiration qui se produisent dans les connexions de données Azure lors de l’exportation d’un grand nombre de fichiers. Pour plus d’informations sur les bureaux virtuels, consultez [Windows Virtual Desktop](https://azure.microsoft.com/services/virtual-desktop).

- Pour améliorer les performances lors du téléchargement des résultats de recherche, envisagez de diviser les recherches qui retournent un grand ensemble de résultats en recherches plus petites. Par exemple, vous pouvez utiliser des plages de dates dans les requêtes de recherche pour retourner un plus petit ensemble de résultats qui peuvent être téléchargés plus rapidement.
  
- Lorsque vous exportez des résultats de recherche, les données sont temporairement stockées dans un emplacement de stockage Azure fourni par Microsoft dans le cloud Microsoft avant d’être téléchargées sur votre ordinateur local. Assurez-vous que votre organisation peut se connecter au point de terminaison dans Azure, qui est **\*.blob.core.windows.net** (le caractère générique représente un identificateur unique pour votre exportation). Les données des résultats de la recherche sont supprimées de l’emplacement stockage Azure deux semaines après leur création. 
  
- Si votre organisation utilise un serveur proxy pour communiquer avec Internet, vous devez définir les paramètres du serveur proxy sur l’ordinateur que vous utilisez pour exporter les résultats de recherche (afin que l’outil d’exportation puisse être authentifié par votre serveur proxy). Pour ce faire, ouvrez le fichier *machine.config* à l’emplacement correspondant à votre version de Windows. 
  
  - **32 bits :** `%windir%\Microsoft.NET\Framework\[version]\Config\machine.config`
  
  - **64 bits :** `%windir%\Microsoft.NET\Framework64\[version]\Config\machine.config`
  
    Ajoutez les lignes suivantes au fichier *machine.config* quelque part entre les balises et `</configuration>` les `<configuration>` balises. Veillez à remplacer et `Port` à utiliser `ProxyServer` les valeurs appropriées pour votre organisation; par exemple, `proxy01.contoso.com:80`. 
  
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

- Si les résultats d’une recherche sont antérieurs à 7 jours et que vous envoyez un travail d’exportation, un message d’erreur s’affiche, vous invitant à réexécuter la recherche pour mettre à jour les résultats de la recherche. Si cela se produit, annulez l’exportation, réexécutez la recherche, puis redémarrez l’exportation.

## <a name="step-1-prepare-search-results-for-export"></a>Étape 1 : Préparer les résultats de recherche pour l’exportation

Vous devez préparer les résultats de recherche pour l’exportation. Lorsque vous préparez les résultats, ils sont chargés vers un emplacement de stockage Azure fourni par Microsoft dans le cloud Microsoft. Le contenu des boîtes aux lettres et des sites est chargé à un taux maximal de 2 Go par heure.
  
1. Dans le portail de conformité, sélectionnez la recherche de contenu à partir de laquelle vous souhaitez exporter les résultats.
  
2. Dans le menu **Actions** en bas de la page de menu volant, cliquez sur **Exporter les résultats**.

   ![Option Exporter les résultats dans le menu Actions.](../media/ActionMenuExportResults.png)

   La page de menu volant **Exporter les résultats** s’affiche. Les options d’exportation disponibles pour exporter du contenu varient selon que les résultats de la recherche se trouvent dans des boîtes aux lettres ou des sites ou une combinaison des deux.

3. Sous **Options de sortie**, choisissez l’une des options suivantes :
  
   ![Exporter les options de sortie.](../media/ExportOutputOptions.png)

    - **Tous les éléments, à l’exception de celles dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour d’autres raisons**. Cette option exporte uniquement les éléments indexés.
  
    - **Tous les éléments, y compris ceux dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour d’autres raisons**. Cette option exporte les éléments indexés et non indexés.
  
    - **Seuls les éléments dont le format n’est pas reconnu sont chiffrés ou qui n’ont pas été indexés pour d’autres raisons**. Cette option exporte uniquement les éléments non indexés.

      Consultez la section [Plus d’informations](#more-information) pour obtenir une description de la façon dont les éléments partiellement indexés sont exportés. Pour plus d’informations sur les éléments partiellement indexés, consultez [Éléments partiellement indexés dans la recherche de contenu](partially-indexed-items-in-content-search.md).

4. Sous **Exporter Exchange contenu,** choisissez l’une des options suivantes :
  
   ![Exchange options.](../media/ExchangeExportOptions.png)

    - **Un fichier PST pour chaque boîte aux lettres** : exporte un fichier PST pour chaque boîte aux lettres utilisateur qui contient les résultats de la recherche. Tous les résultats de la boîte aux lettres d’archivage de l’utilisateur sont inclus dans le même fichier PST. Cette option reproduit la structure de dossiers de boîte aux lettres à partir de la boîte aux lettres source.
  
    - **Un fichier PST contenant tous les messages** : exporte un seul fichier PST (nommé *Exchange.pst*) qui contient les résultats de recherche de toutes les boîtes aux lettres sources incluses dans la recherche. Cette option reproduit la structure de dossiers de boîte aux lettres pour chaque message.
  
    - **Un fichier PST contenant tous les messages d’un même dossier** : exporte les résultats de la recherche vers un seul fichier PST où tous les messages se trouvent dans un seul dossier de niveau supérieur. Cette option permet aux réviseurs de passer en revue les éléments dans l’ordre chronologique (les éléments sont triés par date d’envoi) sans avoir à parcourir la structure de dossiers de boîte aux lettres d’origine pour chaque élément.
  
    - **Messages individuels** : exporte les résultats de la recherche en tant que messages électroniques individuels, au format .msg. Si vous sélectionnez cette option, les résultats de la recherche par e-mail sont exportés vers un dossier du système de fichiers. Le chemin d’accès au dossier des messages individuels est le même que celui utilisé si vous avez exporté les résultats dans un fichier PST.
  
5. Configurez les options supplémentaires suivantes :

   ![Configurez d’autres options d’exportation.](../media/OtherExportOptions.png)

   1. Activez la case à cocher **Activer la déduplication pour Exchange contenu** afin d’exclure les messages en double.
  
      Si vous sélectionnez cette option, une seule copie d’un message est exportée, même si plusieurs copies du même message sont trouvées dans les boîtes aux lettres qui ont fait l’objet d’une recherche. Le rapport des résultats d’exportation (qui est un fichier nommé Results.csv) contient une ligne pour chaque copie d’un message en double afin que vous puissiez identifier les boîtes aux lettres (ou dossiers publics) qui contiennent une copie du message en double. Pour plus d’informations sur la déduplication et la façon dont les éléments en double sont identifiés, consultez [Déduplication dans les résultats de la recherche eDiscovery](de-duplication-in-ediscovery-search-results.md).
  
   2. Cochez la case **Inclure les versions des fichiers SharePoint** pour exporter toutes les versions de SharePoint documents. Cette option s’affiche uniquement si les sources de contenu de la recherche incluent des sites SharePoint ou OneDrive Entreprise.
  
   3. Sélectionnez les **fichiers Exporter dans un dossier compressé (compressé). Inclut uniquement les messages individuels et la case à cocher SharePoint documents** pour exporter les résultats de la recherche vers des dossiers compressés. Cette option s’affiche uniquement lorsque vous choisissez d’exporter Exchange éléments en tant que messages individuels et lorsque les résultats de la recherche incluent SharePoint ou OneDrive documents. Cette option est principalement utilisée pour contourner la limite de 260 caractères dans Windows noms de chemin d’accès de fichier lorsque des éléments sont exportés. Consultez les « Noms de fichiers des éléments exportés » dans la section [Plus d’informations](#more-information) .
   > [!IMPORTANT]
   > L’exportation de fichiers dans un dossier compressé (compressé) augmente les temps d’exportation.
  
6. Cliquez sur **Exporter** pour démarrer le processus d’exportation. Les résultats de la recherche sont préparés pour le téléchargement, ce qui signifie qu’ils sont collectés à partir des emplacements de contenu d’origine, puis chargés vers un emplacement stockage Azure dans le cloud Microsoft. L'opération peut prendre plusieurs minutes.

Consultez la section suivante pour obtenir des instructions pour télécharger les résultats de recherche exportés.
  
## <a name="step-2-download-the-search-results"></a>Étape 2 : Télécharger les résultats de recherche

L’étape suivante consiste à télécharger les résultats de la recherche à partir de l’emplacement stockage Azure sur votre ordinateur local.

> [!NOTE]
> Les résultats de la recherche exportée doivent être téléchargés dans les 14 jours suivant la création du travail d’exportation à l’étape 1.
  
1. Dans la page **Recherche de contenu** dans le portail de conformité, sélectionnez l’onglet **Exportations**
  
   Vous devrez peut-être cliquer sur **Actualiser** pour mettre à jour la liste des travaux d’exportation afin qu’elle affiche le travail d’exportation que vous avez créé. Les travaux d’exportation portent le même nom que la recherche correspondante avec **_Export** ajoutées au nom de recherche.
  
2. Sélectionnez le travail d’exportation que vous avez créé à l’étape 1.

3. Dans la page de menu volant sous **Clé d’exportation**, cliquez sur **Copier dans le Presse-papiers**. Vous utilisez cette clé à l’étape 6 pour télécharger les résultats de la recherche.
  
   > [!IMPORTANT]
   > Étant donné que tout le monde peut installer et lancer l’outil d’exportation de découverte électronique, et utiliser cette clé pour télécharger les résultats de recherche, prenez toutes les précautions nécessaires pour protéger cette clé, comme vous le feriez avec les mots de passe ou d’autres informations de sécurité. 

4. En haut de la page de menu volant, cliquez sur **Télécharger les résultats**.

5. Si vous êtes invité à installer **l’outil d’exportation eDiscovery**, cliquez sur **Installer**.

6. Dans **l’outil d’exportation eDiscovery**, procédez comme suit :

   ![Outil d’exportation eDiscovery.](../media/eDiscoveryExportTool.png)

   1. Collez la clé d’exportation que vous avez copiée à l’étape 3 dans la zone appropriée.
  
   2. Cliquez sur **Parcourir** pour spécifier l’emplacement de téléchargement du fichier des résultats de recherche.
  
      > [!IMPORTANT]
      >  En raison d’une activité réseau élevée pendant le téléchargement, vous devez télécharger les résultats de la recherche uniquement à un emplacement sur un lecteur interne sur votre ordinateur local. Pour une expérience de téléchargement optimale, suivez les instructions suivantes : <br/>
      >- Ne téléchargez pas les résultats de la recherche sur un chemin UNC, un lecteur réseau mappé, un lecteur USB externe ou un compte OneDrive Entreprise synched.<br/>
      >- Désactivez l’analyse antivirus pour le dossier dans lequel vous téléchargez le résultat de la recherche.<br/>
      >- Téléchargez les résultats de la recherche dans différents dossiers pour les travaux de téléchargement simultanés.

7. Cliquez sur **Démarrer** pour télécharger les résultats de recherche sur votre ordinateur.
  
    L’**outil d’exportation de découverte électronique** affiche l’état du processus d’exportation, ainsi qu’une estimation du nombre (et de la taille) d’éléments qui doivent encore être téléchargés. Lorsque le processus d’exportation est terminé, vous pouvez accéder aux fichiers à l’emplacement où ils ont été téléchargés.

## <a name="more-information"></a>Plus d’informations

Voici plus d’informations sur l’exportation des résultats de recherche.
  
[Limites d’exportation](#export-limits)
  
[Exporter des rapports](#export-reports)
  
[Exportation d’éléments indexés partiellement](#exporting-partially-indexed-items)

[Exportation de messages individuels ou de fichiers PST](#exporting-individual-messages-or-pst-files)

[Déchiffrement des messages électroniques protégés par RMS et des pièces jointes chiffrées](#decrypting-rms-protected-email-messages-and-encrypted-file-attachments)

[Noms de fichiers des éléments exportés](#filenames-of-exported-items)  
  
[Divers](#miscellaneous)
  
### <a name="export-limits"></a>Limites d’exportation

Pour plus d’informations sur les limites lors de l’exportation des résultats de la recherche de contenu, consultez la section « Exporter les limites » dans [Limites pour la recherche de contenu](limits-for-content-search.md#export-limits).

### <a name="export-reports"></a>Exporter des rapports
  
- Lorsque vous exportez des résultats de recherche, les rapports suivants sont inclus en plus des résultats de recherche.
  
  - **Résumé de l’exportation** Document Excel qui contient un résumé de l’exportation. Cela inclut des informations telles que le nombre de sources de contenu qui ont été recherchées, les tailles estimées et téléchargées des résultats de la recherche, ainsi que le nombre estimé et téléchargé d’éléments exportés.
  
  - **Manifeste** Fichier manifeste (au format XML) qui contient des informations sur chaque élément inclus dans les résultats de la recherche.
  
  - **Résultats** Document Excel qui contient des informations sur chaque élément téléchargé en tant que résultat de recherche. Pour le courrier électronique, le journal des résultats contient des informations sur chaque message, y compris :
  
    - l’emplacement du message dans la boîte aux lettres source (notamment si le message est dans la boîte aux lettres principale ou d’archivage) ;
  
    - la date à laquelle le message a été envoyé ou reçu ;

    - l’objet du message ;

    - l’expéditeur et les destinataires du message.

    - Indique si le message est un message en double si vous avez activé l’option de déduplication lors de l’exportation des résultats de la recherche. Les messages en double ont une valeur dans la colonne **Dupliquer à l’élément** qui identifie le message comme étant un doublon. La valeur de la colonne **Dupliquer à l’élément** contient l’identité de l’élément du message qui a été exporté. Pour plus d’informations, consultez [Dédoublement dans les résultats de la recherche eDiscovery](de-duplication-in-ediscovery-search-results.md).

      Pour les documents des sites SharePoint et OneDrive Entreprise, le journal des résultats contient des informations sur chaque document, notamment :

      - l’URL du document ;

      - l’URL de la collection de sites qui héberge le document ;

      - la date à laquelle le document a été modifié pour la dernière fois ;

      - le nom du document (qui se trouve dans la colonne Objet du journal des résultats).

  - **Éléments non indexés** Document Excel qui contient des informations sur les éléments partiellement indexés qui seraient inclus dans les résultats de la recherche. Si vous n’incluez pas d’éléments partiellement indexés lorsque vous générez le rapport de résultats de recherche, ce rapport est toujours téléchargé, mais il est vide.

  - **Erreurs et avertissements** Contient des erreurs et des avertissements pour les fichiers rencontrés lors de l’exportation. Consultez la colonne Détails de l’erreur pour obtenir des informations spécifiques à chaque erreur ou avertissement individuel.

  - **Éléments ignorés** Lorsque vous exportez des résultats de recherche à partir de sites SharePoint et OneDrive Entreprise, l’exportation inclut généralement un rapport d’éléments ignorés (SkippedItems.csv). Les éléments cités dans ce rapport sont généralement des éléments qui ne seront pas téléchargés, tels qu’un dossier ou un ensemble de documents. Ne pas exporter ces types d’éléments est par conception. Pour les autres éléments qui ont été ignorés, les champs « Type d’erreur » et « Détails de l’erreur » dans le rapport d’éléments ignorés indiquent la raison pour laquelle l’élément a été ignoré et n’a pas été téléchargé avec les autres résultats de recherche.

  - **Trace.log** contient des informations de journalisation détaillées sur le processus d’exportation et peut vous aider à détecter les problèmes lors de l’exportation. Si vous ouvrez un ticket avec Support Microsoft à propos d’un problème lié à l’exportation des résultats de recherche, vous pouvez être invité à fournir ce journal de suivi.
  
    > [!NOTE]
    > Vous pouvez simplement exporter ces documents sans avoir à exporter les résultats de recherche réels. Voir [Exporter un rapport de recherche de contenu](export-a-content-search-report.md).
  
### <a name="exporting-partially-indexed-items"></a>Exporter des éléments partiellement indexés
  
- Si vous exportez des éléments de boîte aux lettres à partir d’une recherche de contenu qui retourne tous les éléments de boîte aux lettres dans les résultats de la recherche (car aucun mot clé n’est inclus dans la requête de recherche), les éléments partiellement indexés ne sont pas copiés dans le fichier PST qui contient les éléments non indexés. Cela est dû au fait que tous les éléments, y compris les éléments partiellement indexés, sont automatiquement inclus dans les résultats de recherche réguliers. Cela signifie que les éléments partiellement indexés seront inclus dans un fichier PST (ou en tant que messages individuels) qui contient les autres éléments indexés.

    Si vous exportez les éléments indexés et partiellement indexés ou si vous exportez uniquement les éléments indexés à partir d’une recherche de contenu qui retourne tous les éléments, le même nombre d’éléments est téléchargé. Cela se produit même si les résultats de recherche estimés pour la recherche de contenu (affichés dans les statistiques de recherche dans le portail de conformité) incluent toujours une estimation distincte du nombre d’éléments partiellement indexés. Par exemple, supposons que l’estimation d’une recherche qui inclut tous les éléments (aucun mot clé dans la requête de recherche) indique que 1 000 éléments ont été trouvés et que 200 éléments partiellement indexés ont également été trouvés. Dans ce cas, les 1 000 éléments incluent les éléments partiellement indexés, car la recherche retourne tous les éléments. En d’autres termes, 1 000 éléments au total sont retournés par la recherche, et non 1 200 éléments (comme vous pouvez vous y attendre). Si vous exportez les résultats de cette recherche et choisissez d’exporter des éléments indexés et partiellement indexés (ou d’exporter uniquement des éléments partiellement indexés), 1 000 éléments seront téléchargés. Là encore, cela est dû au fait que les éléments partiellement indexés sont inclus dans les résultats réguliers (indexés) lorsque vous utilisez une requête de recherche vide pour renvoyer tous les éléments. Dans ce même exemple, si vous choisissez d’exporter uniquement des éléments partiellement indexés, seuls les 200 éléments non indexés sont téléchargés.

    Notez également que dans l’exemple précédent (lorsque vous exportez des éléments indexés et partiellement indexés ou que vous exportez uniquement des éléments indexés), le rapport **Résumé** de l’exportation inclus dans les résultats de recherche exportés répertorie 1 000 éléments estimés et 1 000 éléments téléchargés pour les mêmes raisons que celles décrites précédemment. 

- Si la recherche à partir de laquelle vous exportez des résultats était une recherche d’emplacements de contenu spécifiques ou de tous les emplacements de contenu de votre organisation, seuls les éléments partiels des emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche seront exportés. En d’autres termes, si aucun résultat de recherche n’est trouvé dans une boîte aux lettres ou un site, les éléments partiellement indexés dans cette boîte aux lettres ou ce site ne seront pas exportés. Cela est dû au fait que l’exportation d’éléments partiellement indexés à partir de nombreux emplacements de l’organisation peut augmenter la probabilité d’erreurs d’exportation et augmenter le temps nécessaire pour exporter et télécharger les résultats de la recherche.

    Pour exporter des éléments partiellement indexés à partir de tous les emplacements de contenu pour une recherche, configurez la recherche pour renvoyer tous les éléments (en supprimant tous les mots clés de la requête de recherche), puis exportez uniquement les éléments partiellement indexés lorsque vous exportez les résultats de la recherche.

    ![Utilisez la troisième option d’exportation pour exporter uniquement des éléments non indexés.](../media/5d7be338-a0e5-425f-8ba5-92769c24bf75.png)
  
- Lors de l’exportation des résultats de recherche à partir de sites SharePoint ou OneDrive Entreprise, la possibilité d’exporter des éléments non indexés dépend également de l’option d’exportation que vous sélectionnez et si un site qui a fait l’objet d’une recherche contient un élément indexé qui correspond aux critères de recherche. Par exemple, si vous effectuez une recherche sur des sites SharePoint ou OneDrive Entreprise et qu’aucun résultat de recherche n’est trouvé, aucun élément non indexé de ces sites n’est exporté si vous choisissez la deuxième option d’exportation pour exporter des éléments indexés et non indexés. Si un élément indexé d’un site correspond aux critères de recherche, tous les éléments non indexés de ce site sont exportés lors de l’exportation d’éléments indexés et non indexés. L’illustration suivante décrit les options d’exportation selon qu’un site contient un élément indexé qui correspond aux critères de recherche.

    ![Choisissez l’option d’exportation selon qu’un site contient un élément indexé qui correspond aux critères de recherche.](../media/94f78786-c6bb-42fb-96b3-7ea3998bcd39.png)

    a. Seuls les éléments indexés qui correspondent aux critères de recherche sont exportés. Aucun élément partiellement indexé n’est exporté.

    b. Si aucun élément indexé d’un site ne correspond aux critères de recherche, les éléments partiellement indexés de ce même site ne sont pas exportés. Si les éléments indexés d’un site sont retournés dans les résultats de la recherche, les éléments partiellement indexés de ce site sont exportés. En d’autres termes, seuls les éléments partiellement indexés des sites qui contiennent des éléments qui correspondent aux critères de recherche sont exportés.

    c. Tous les éléments partiellement indexés de tous les sites de la recherche sont exportés, qu’un site contienne ou non des éléments qui correspondent aux critères de recherche.

    Si vous choisissez d’exporter des éléments partiellement indexés, les éléments de boîte aux lettres partiellement indexés sont exportés dans un fichier PST distinct, quelle que soit l’option que vous choisissez sous **Exporter Exchange contenu.**

- Si des éléments partiellement indexés sont retournés dans les résultats de la recherche (car d’autres propriétés d’éléments partiellement indexés correspondent aux critères de recherche), ceux partiellement indexés sont exportés avec les résultats de recherche réguliers. Par conséquent, si vous choisissez d’exporter à la fois les éléments indexés et les éléments partiellement indexés (en sélectionnant **tous les éléments, y compris ceux dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour d’autres raisons** , l’option d’exportation), les éléments partiellement indexés exportés avec les résultats réguliers sont répertoriés dans le rapport Results.csv. Elles ne sont pas répertoriées dans le rapport items.csv non indexé.
  
### <a name="exporting-individual-messages-or-pst-files"></a>Exportation de messages individuels ou de fichiers PST
  
- Si le nom du chemin d’accès d’un message dépasse la limite de caractères maximale pour Windows, le nom du chemin d’accès du fichier est tronqué. Toutefois, le nom du chemin d’accès du fichier d’origine est répertorié dans le manifeste et le journal des résultats.
  
- Comme expliqué précédemment, les résultats de la recherche par e-mail sont exportés vers un dossier du système de fichiers. Le chemin d’accès au dossier pour les messages individuels réplique le chemin d’accès au dossier dans la boîte aux lettres de l’utilisateur. Par exemple, pour une recherche nommée « ContosoCase101 » dans la boîte de réception d’un utilisateur se trouve dans le chemin d’accès  `~ContosoCase101\\<date of export\Exchange\user@contoso.com (Primary)\Top of Information Store\Inbox`du dossier.

- Si vous choisissez d’exporter des messages électroniques dans un fichier PST contenant tous les messages d’un dossier unique, un dossier **Éléments supprimés** et un dossier **Dossiers de recherche** sont inclus dans le niveau supérieur du dossier PST. Ces dossiers sont vides.

- Comme indiqué précédemment, vous devez exporter les résultats de la recherche par e-mail en tant que messages individuels pour déchiffrer les messages protégés par RMS lorsqu’ils sont exportés. Les messages chiffrés restent chiffrés si vous exportez les résultats de la recherche par e-mail en tant que fichier PST.
  
### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments"></a>Déchiffrement des messages électroniques protégés par RMS et des pièces jointes chiffrées

Tous les messages électroniques protégés par des droits (protégés par RMS) inclus dans les résultats d’une recherche de contenu sont déchiffrés lorsque vous les exportez. En outre, tout fichier chiffré à l’aide d’une [technologie de chiffrement Microsoft](encryption.md) et attaché à un e-mail inclus dans les résultats de la recherche sera également déchiffré lors de son exportation. Cette fonctionnalité de déchiffrement est activée par défaut pour les membres du groupe de rôles eDiscovery Manager. Cela est dû au fait que le rôle de gestion de déchiffrement RMS est attribué à ce groupe de rôles par défaut. Gardez à l’esprit les éléments suivants lors de l’exportation de courriers électroniques chiffrés et de pièces jointes :
  
- Comme expliqué précédemment, pour déchiffrer les messages protégés par RMS lorsque vous les exportez, vous devez exporter les résultats de la recherche en tant que messages individuels. Si vous exportez les résultats de la recherche dans un fichier PST, les messages protégés par RMS restent chiffrés.

- Les messages déchiffrés sont identifiés dans le rapport **ResultsLog** . Ce rapport contient une colonne nommée **État de décodage**, et une valeur de **Décodage** dans cette colonne identifie les messages qui ont été déchiffrés.

- Outre le déchiffrement des pièces jointes de fichier lors de l’exportation des résultats de recherche, vous pouvez également afficher un aperçu du fichier déchiffré lors de l’aperçu des résultats de la recherche. Vous pouvez uniquement afficher le message électronique protégé par des droits après l’avoir exporté.

- À ce stade, la fonctionnalité de déchiffrement lors de l’exportation des résultats de recherche n’inclut pas de contenu chiffré à partir de sites SharePoint et OneDrive Entreprise. Toutefois, le support sera bientôt disponible pour les documents chiffrés avec les technologies de chiffrement Microsoft et stockés dans SharePoint Online et OneDrive Entreprise.

- Si vous devez empêcher quelqu’un de déchiffrer les messages de protection RMS et les pièces jointes de fichiers chiffrés, vous devez créer un groupe de rôles personnalisé (en copiant le groupe de rôles eDiscovery Manager intégré), puis supprimer le rôle de gestion de déchiffrement RMS du groupe de rôles personnalisé. Ajoutez ensuite la personne dont vous ne souhaitez pas déchiffrer les messages en tant que membre du groupe de rôles personnalisé.
  
### <a name="filenames-of-exported-items"></a>Noms de fichiers des éléments exportés
  
- Il existe une limite de 260 caractères (imposée par le système d’exploitation) pour le nom complet du chemin d’accès pour les messages électroniques et les documents de site exportés vers votre ordinateur local. Le nom complet du chemin d’accès pour les éléments exportés inclut l’emplacement d’origine de l’élément et l’emplacement du dossier sur l’ordinateur local sur lequel les résultats de la recherche sont téléchargés. Par exemple, si vous spécifiez pour télécharger les résultats de  `C:\Users\Admin\Desktop\SearchResults` la recherche dans l’outil d’exportation eDiscovery, le chemin d’accès complet d’un élément de courrier téléchargé serait  `C:\Users\Admin\Desktop\SearchResults\ContentSearch1\03.15.2017-1242PM\Exchange\sarad@contoso.com (Primary)\Top of Information Store\Inbox\Insider trading investigation.msg`.

- Si la limite de 260 caractères est dépassée, le nom complet du chemin d’accès d’un élément est tronqué, en fonction des éléments suivants :

  - Si le nom du chemin d’accès complet est supérieur à 260 caractères, le nom de fichier est raccourci pour passer sous la limite ; Notez que le nom de fichier tronqué (à l’exclusion de l’extension de fichier) ne sera pas inférieur à huit caractères.

  - Si le nom du chemin d’accès complet est encore trop long après le raccourcissement du nom de fichier, l’élément est déplacé de son emplacement actuel vers le dossier parent. Si le chemin d’accès est encore trop long, le processus est répété : raccourcissez le nom du fichier et, si nécessaire, revenez au dossier parent. Ce processus est répété jusqu’à ce que le chemin d’accès complet soit sous la limite de 260 caractères.

  - Si un nom de chemin d’accès complet tronqué existe déjà, un numéro de version est ajouté à la fin du nom de fichier ; par exemple, `statusmessage(2).msg`.

    Pour atténuer ce problème, envisagez de télécharger les résultats de la recherche vers un emplacement avec un nom de chemin d’accès court; Par exemple, le téléchargement des résultats de recherche dans un dossier nommé  `C:\Results` ajouterait moins de caractères aux noms de chemin d’accès des éléments exportés que de les télécharger dans un dossier nommé  `C:\Users\Admin\Desktop\Results`.

- Lorsque vous exportez des documents de site, il est également possible que le nom de fichier d’origine d’un document soit modifié. Cela se produit spécifiquement pour les documents qui ont été supprimés d’un site SharePoint ou OneDrive Entreprise qui a été mis en attente. Une fois qu’un document se trouve sur un site en attente est supprimé, le document supprimé est automatiquement déplacé vers la bibliothèque de conservation du site (qui a été créée lorsque le site a été mis en attente). Lorsque le document supprimé est déplacé vers la bibliothèque de conservation, un ID généré de manière aléatoire et unique est ajouté au nom de fichier d’origine du document. Par exemple, si le nom de fichier d’un document est  `FY2017Budget.xlsx` et que ce document est supprimé par la suite et déplacé vers la bibliothèque de conservation de la conservation, le nom de fichier du document déplacé vers la bibliothèque de conservation est modifié en quelque chose comme  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`. Si un document dans la bibliothèque conservation de la conservation correspond à la requête d’une recherche de contenu et que vous exportez les résultats de cette recherche, le fichier exporté a le nom de fichier modifié ; Dans cet exemple, le nom de fichier du document exporté serait  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`.

    Lorsqu’un document sur un site en attente est modifié (et que le contrôle de version de la bibliothèque de documents dans le site a été activé), une copie du fichier est automatiquement créée dans la bibliothèque de conservation de la conservation. Dans ce cas, un ID généré de manière aléatoire et unique est également ajouté au nom de fichier du document copié dans la bibliothèque conservation de la conservation.

    La raison pour laquelle les noms de fichiers des documents qui sont déplacés ou copiés dans la bibliothèque de conservation de la conservation sont pour empêcher les noms de fichiers en conflit. Pour plus d’informations sur la mise en attente sur les sites et la bibliothèque de conservation, consultez [Vue d’ensemble de la conservation sur place dans SharePoint Server 2016](https://support.office.com/article/5e400d68-cd51-444a-8fe6-e4df1d20aa95).

### <a name="miscellaneous"></a>Divers
  
- Lors du téléchargement des résultats de la recherche à l’aide de l’outil d’exportation eDiscovery, il est possible que vous receviez l’erreur suivante : `System.Net.WebException: The remote server returned an error: (412) The condition specified using HTTP conditional header(s) is not met.` il s’agit d’une erreur temporaire, qui se produit généralement à l’emplacement stockage Azure. Pour résoudre ce problème, réessayez [de télécharger les résultats de la recherche](#step-2-download-the-search-results), ce qui redémarrera l’outil d’exportation eDiscovery.

- Tous les résultats de la recherche et les rapports d’exportation sont inclus dans un dossier qui porte le même nom que la recherche de contenu. Les courriers électroniques exportés se trouvent dans un dossier nommé **Exchange**. Les documents se trouvent dans un dossier nommé **SharePoint**.

- Les métadonnées du système de fichiers pour les documents sur les sites SharePoint et OneDrive Entreprise sont conservées lorsque les documents sont exportés vers votre ordinateur local. En d’autres termes, les propriétés de document (par exemple, Date de création et Date de la dernière modification) ne sont pas modifiées lorsque les documents sont exportés.

- Si vos résultats de recherche incluent un élément de liste de SharePoint qui correspond à la requête de recherche, toutes les lignes de la liste sont exportées en plus de l’élément correspondant à la requête de recherche et aux pièces jointes de la liste. La raison de ce comportement est de fournir un contexte pour les éléments de liste retournés dans les résultats de la recherche. Les éléments de liste et pièces jointes supplémentaires peuvent entraîner une différence entre le nombre d’éléments exportés et l’estimation d’origine des résultats de la recherche.
