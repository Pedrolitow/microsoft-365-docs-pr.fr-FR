---
title: Hacher et charger la table de source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Hachage et chargement de la table des sources d’informations sensibles pour les types d’informations sensibles de correspondance exacte des données.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8d3effe3d46375ffcaec268e4b3fc6d53fc5044e
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526497"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>Hacher et charger la table de source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles

Cet article vous montre comment hachage et télécharger votre table de sources d’informations sensibles.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>Hachage et chargement de la table des sources d’informations sensibles

Dans cette phase, vous :

1. configurer un groupe de sécurité et un compte d’utilisateur personnalisés
2. configurer l’outil Agent Télécharger EDM
3. Utilisez l’outil agent Télécharger EDM pour hachage, avec une valeur salt, la table des sources d’informations sensibles et téléchargez-la.

L’opération de hachage et de chargement peut être effectuée à l’aide d’un ordinateur ou vous pouvez séparer ces deux étapes pour renforcer la sécurité.

Si vous voulez hacher et charger à partir d’un ordinateur, vous devez le faire à partir d’un ordinateur qui peut se connecter directement à votre client Microsoft 365. Pour cela, votre fichier de table de sources d’informations sensibles en texte clair doit se trouve sur cet ordinateur pour le hachage.

Si vous ne souhaitez pas exposer votre fichier de table de sources d’informations sensibles en texte clair sur l’ordinateur à accès direct, vous pouvez le hachage sur un ordinateur qui se trouve dans un emplacement sécurisé, puis copier le fichier de hachage et le fichier salt sur un ordinateur qui peut se connecter directement à votre client Microsoft 365 pour le chargement. Dans le scénario de hachage et de chargement séparés, vous aurez besoin d’EDMUploadAgent sur les deux ordinateurs.

> [!IMPORTANT]
> Si vous avez utilisé l’Assistant Correspondance exacte des données et type d’informations sensibles pour créer votre fichier  de schéma, vous devez télécharger le schéma pour cette procédure si vous ne l’avez pas déjà fait. Voir Exporter [le fichier de schéma EDM au format XML](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> Si votre organisation a installé la clé client pour [Microsoft 365](customer-key-overview.md) au niveau du client, la correspondance exacte des données utilisera automatiquement sa fonctionnalité de chiffrement. Cette offre est disponible uniquement pour les clients sous licence E5 dans le cloud commercial.

### <a name="best-practices"></a>Meilleures pratiques

Séparez les processus de hachage et de chargement des données sensibles afin de pouvoir isoler plus facilement les problèmes dans le processus.
 
Une fois en production, conservez les deux étapes distinctes dans la plupart des cas. L’opération de hachage sur un ordinateur isolé, puis le transfert du fichier à télécharger vers un ordinateur accessible sur Internet garantit que les données réelles ne sont jamais disponibles en texte clair sur un ordinateur qui aurait pu être compromis en raison de sa connexion à Internet.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>Assurez-vous que votre table de données sensibles n’a pas de problèmes de mise en forme. 

Avant de hachage et de chargement de vos données sensibles, faites une recherche pour valider la présence de caractères spéciaux qui peuvent entraîner des problèmes d’analyse du contenu. Vous pouvez vérifier que le tableau est dans un format approprié à utiliser avec EDM à l’aide de l’agent de chargement EDM avec la syntaxe suivante :

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file] 
```

Si l’outil indique une non-compatibilité en nombre de colonnes, il peut être dû à la présence de virgules ou de guillemets dans les valeurs du tableau qui sont confondues avec les délimiteur de colonnes. Sauf s’ils entourent une valeur entière, les guillemets simples et doubles peuvent provoquer une erreur d’identification de l’endroit où une colonne individuelle démarre ou se termine. 

**Si vous trouvez des guillemets simples ou doubles entourant** des valeurs complètes : vous pouvez les laisser tels quelles.

Si vous trouvez des guillemets simples ou des virgules à l’intérieur d’une valeur : par exemple, le nom de la personne Tom O’Quotes ou la ville 's-Gravenhage qui commence par une apostrophe, vous devez modifier le processus d’exportation de données utilisé pour générer la table d’informations sensibles afin de entourer ces colonnes de guillemets doubles.

**Si des guillemets** doubles sont trouvés à l’intérieur des valeurs, il peut être préférable d’utiliser le format délimité par des tabulations pour le tableau qui est moins susceptible de ces problèmes.

### <a name="prerequisites"></a>Configuration requise

- Un compte professionnel ou scolaire pour Microsoft 365 qui sera ajouté au groupe de sécurité **EDM\_DataUploaders**
- un Windows 10 ou un Windows Server 2016 avec .NET version 4.6.2 <!--4.7.2 un comment this around 9/29-->pour l’exécution de l’EDMUploadAgent
- Un répertoire sur votre ordinateur de téléchargement pour :
  - [Agent de Télécharger EDM](#links-to-edm-upload-agent-by-subscription-type)
  - votre fichier d’élément sensible au format .csv, .tsv ou pipe (|), **PatientRecords.csvdans nos** exemples
  - fichiers de hachage et salt de sortie créés dans cette procédure ;
  - Le nom du magasin de données provenant du fichier **edm.xml**, ici `PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>Configurer les groupe de sécurité personnalisé et compte d’utilisateur

1. En tant qu’administrateur général, accédez au centre d’administration à l’aide du [lien approprié pour votre abonnement](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription) et [créez un groupe de sécurité](/office365/admin/email/create-edit-or-delete-a-security-group) nommé **EDM\_DataUploaders**.

2. Ajoutez un ou plusieurs utilisateurs au groupe de sécurité **EDM\_DataUploaders**. (ces utilisateurs peuvent gérer la base de données d’informations sensibles).

### <a name="hash-and-upload-from-one-computer"></a>Hacher et charger à partir d’un même ordinateur

Cet ordinateur doit avoir accès directement à votre client Microsoft 365.

> [!NOTE]
> Avant de commencer cette procédure, assurez-vous que vous êtes membre du groupe de sécurité **EDM\_DataUploaders**.

> [!TIP] 
>Si vous le souhaitez, vous pouvez exécuter une validation sur votre fichier de table de sources d’informations sensibles pour vérifier s’il y a des erreurs avant le chargement en exécutant :
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> Pour plus d’informations sur tous les paramètres pris EdmUploadAgent.exe'exécuter
>
> `EdmUploadAgent.exe /?`

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>Liens vers l’agent de chargement EDM par type d’abonnement

- [Commercial + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) : pour la plupart des clients commerciaux
- [GCC-High](https://go.microsoft.com/fwlink/?linkid=2137521) : conçu spécifiquement pour les abonnés cloud du secteur public haute sécurité
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) : conçu spécifiquement pour les clients cloud du Department of Defense américain

1. Créez un répertoire de travail pour EDMUploadAgent. Par exemple, **C:\EDM\Data**. Placez le fichier **PatientRecords.csv** à cet emplacement.

2. Téléchargez et installez l’[agent de chargement EDM](#links-to-edm-upload-agent-by-subscription-type) approprié pour votre abonnement dans le répertoire créé à l’étape 1.

   > [!NOTE]
   > La version d’EDMUploadAgent fournie à travers les liens ci-dessus a été mise à jour afin d’ajouter automatiquement une valeur salt aux données hachées. Vous pouvez également fournir votre propre valeur salt. Une fois que vous avez utilisé cette version, vous ne pourrez pas utiliser la version précédente d’EDMUploadAgent.
   >
   > Vous pouvez télécharger des données avec EDMUploadAgent vers n’importe quel magasin de données donné deux fois par jour uniquement.

3. Autorisez l’agent Télécharger EDM, ouvrez la fenêtre d’invite de commandes en tant qu’administrateur, basculez vers **le répertoire C:\EDM\Data**, puis exécutez la commande suivante :

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> Vous devez exécuter **EdmUploadAgent** à partir du dossier où il est installé et indiquer le chemin d’accès complet à vos fichiers de données. 

4. Connectez-vous à l’aide de votre compte professionnel ou scolaire pour Microsoft 365 qui a été ajouté au groupe de sécurité EDM_DataUploaders. Vos informations de client sont extraites du compte d’utilisateur pour établir la connexion.

   FACULTATIF : si vous avez utilisé l’Assistant Correspondance exacte des données et type d’informations sensibles pour créer votre  schéma, vous devez le télécharger pour l’utiliser dans cette procédure si ce n’est pas déjà fait. Exécutez cette commande dans une fenêtre d’invite de commandes :

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. Pour hacher et charger les données sensibles, exécutez la commande suivante dans l’invite de commandes Windows :

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```
   > [!NOTE]
> Le format par défaut du fichier de données sensibles est les valeurs séparées par des virgules. Vous pouvez spécifier un fichier séparé par des tabulations en indiquant l’option « {Tab} » avec le paramètre /ColumnSeparator, ou vous pouvez spécifier un fichier séparé par un canal en indiquant l’option « | ».

   Exemple : **EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5**

Si votre table d’informations sensibles a des valeurs mal formatées, mais que vous souhaitez importer les données restantes tout en ignorant les lignes non valides, vous pouvez utiliser le paramètre */AllowedBadLinesPercentage* dans la commande. L’exemple ci-dessus spécifie un seuil de cinq pour cent. Cela signifie que l’outil va hachage et télécharger la table des informations sensibles même si jusqu’à cinq pour cent des lignes ne sont pas valides. 

Cette commande ajoute automatiquement une valeur salt générée de manière aléatoire au hachage pour une sécurité accrue. Si vous voulez utiliser votre propre valeur salt, vous pouvez également ajouter **/Salt <saltvalue>** à la commande. Cette valeur doit comporter 64 caractères et ne peut contenir que les caractères allant de a à z et de 0 à 9.

6. Vérifiez l’état du chargement en exécutant la commande suivante :

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   Exemple : **EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords**

   Vous verrez l’état **ProcessingInProgress**. Vérifiez à quelques minutes d’intervalle jusqu’à ce que l’état devienne **Completed**. Une fois que le chargement est à l’état Completed, vos données EDM sont prêtes à l’emploi. Selon la taille de votre fichier de table de sources d’informations sensibles, cette opération peut prendre de quelques minutes à plusieurs heures. 

> [!TIP]
> Si vous souhaitez être averti une fois que les données sensibles téléchargées sont prêtes à être utilisés, suivez les procédures de création de notifications pour les activités de correspondance de [données exactes](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities).

### <a name="separate-hash-and-upload"></a>Séparer le hachage et le chargement

Effectuez le hachage sur un ordinateur dans un environnement sécurisé. **L’EDMUploadAgent doit** être installé sur les deux ordinateurs.

FACULTATIF : si vous avez utilisé l’Assistant Correspondance exacte des données et type d’informations sensibles pour créer votre schéma et que vous ne l’avez pas déjà téléchargé, exécutez la commande suivante dans une fenêtre d’invite de commandes pour télécharger le fichier au format XML :

```dos
EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
````

1. Sur l’ordinateur dans l’environnement sécurisé, exécutez la commande suivante dans les fenêtres d’invite de commandes :

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /AllowedBadLinesPercentage [value]
   ```

   Par exemple :

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5
   ```

> [!NOTE]
> Le format par défaut du fichier de données sensibles est les valeurs séparées par des virgules. Vous pouvez spécifier un fichier séparé par des tabulations en indiquant l’option « {Tab} » avec le paramètre /ColumnSeparator, ou vous pouvez spécifier un fichier séparé par un canal en indiquant l’option « | ».


   Cela génère un fichier haché et un fichier salt avec les extensions suivantes si vous n’avez pas spécifié l’option **/Salt <saltvalue>**  :

   - .EdmHash
   - .EdmSalt


2. Copiez ces fichiers de manière sécurisée sur l’ordinateur que vous utiliserez pour télécharger votre fichier de table de sources d’informations sensibles (PatientRecords) vers votre client.

3. Autorisez l’agent Télécharger EDM, ouvrez la fenêtre d’invite de commandes en tant qu’administrateur, basculez vers **le répertoire C:\EDM\Data**, puis exécutez la commande suivante :

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> Vous devez exécuter **EdmUploadAgent** à partir du dossier où il est installé et indiquer le chemin d’accès complet à vos fichiers de données. 

4. Connectez-vous à l’aide de votre compte professionnel ou scolaire pour Microsoft 365 qui a été ajouté au groupe de sécurité EDM_DataUploaders. Vos informations de client sont extraites du compte d’utilisateur pour établir la connexion.

5. Pour charger les données hachées, exécutez la commande suivante dans l’invite de commandes Windows :

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\ /ColumnSeparator ["{Tab}"|"|"]
   ```

   Par exemple :

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\**PatientRecords.EdmHash**
   ```

6. Pour vérifier que vos données sensibles ont été téléchargées, exécutez la commande suivante dans l’invite de commandes Windows :

   ```dos
   EdmUploadAgent.exe /GetDataStore
   ```
   La liste des magasins de données apparaît, ainsi que la date de la dernière mise à jour.

7. Si vous souhaitez voir tous les téléchargements de données dans un magasin particulier, exécutez la commande suivante dans une invite de commandes Windows pour voir la liste de tous les magasins de données et quand ils ont été mis à jour :

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```
     
## <a name="next-step"></a>Étape suivante

- [Créer des données exactes correspondant au type d’informations sensibles/au package de règles](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)

