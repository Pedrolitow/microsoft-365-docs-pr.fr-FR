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
description: Hachez et chargez la table source d’informations sensibles pour que les données exactes correspondent aux types d’informations sensibles.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4c40802a76ab09dc86dcada5ebfd17187136f42e
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760226"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>Hacher et charger la table de source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles

Cet article vous montre comment hacher et charger votre table source d’informations sensibles.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>Hachage et chargement de la table source d’informations sensibles

Dans cette phase, vous :

1. configurer un groupe de sécurité et un compte d’utilisateur personnalisés
2. configurer l’outil EDM Télécharger Agent
3. Utilisez l’outil EDM Télécharger Agent pour le hachage, avec une valeur salt, la table source d’informations sensibles et chargez-la.

L’opération de hachage et de chargement peut être effectuée à l’aide d’un ordinateur ou vous pouvez séparer ces deux étapes pour renforcer la sécurité.

Si vous voulez hacher et charger à partir d’un ordinateur, vous devez le faire à partir d’un ordinateur qui peut se connecter directement à votre client Microsoft 365. Cela nécessite que votre fichier de table source d’informations sensibles en texte clair se trouve sur cet ordinateur pour le hachage.

Si vous ne souhaitez pas exposer votre fichier de table source d’informations sensibles en texte clair sur l’ordinateur à accès direct, vous pouvez le hacher sur un ordinateur qui se trouve dans un emplacement sécurisé, puis copier le fichier de hachage et le fichier salt sur un ordinateur qui peut se connecter directement à votre client Microsoft 365 pour le chargement. Dans le scénario de hachage et de chargement séparés, vous aurez besoin d’EDMUploadAgent sur les deux ordinateurs.

> [!IMPORTANT]
> Si vous avez utilisé l’Assistant Correspondance exacte des données et type d’informations sensibles pour créer votre fichier de schéma, vous ***devez*** télécharger le schéma de cette procédure si vous ne l’avez pas déjà fait. Consultez [l’article Exporter le fichier de schéma EDM au format XML](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> Si votre organisation a configuré [la clé client pour Microsoft 365 au niveau du locataire, la](customer-key-overview.md) correspondance exacte des données utilise automatiquement ses fonctionnalités de chiffrement. Cette offre est disponible uniquement pour les clients sous licence E5 dans le cloud commercial.

### <a name="best-practices"></a>Meilleures pratiques

Séparez les processus de hachage et de chargement des données sensibles afin de pouvoir isoler plus facilement les problèmes du processus.

Une fois en production, conservez les deux étapes distinctes dans la plupart des cas. L’exécution du processus de hachage sur un ordinateur isolé, puis le transfert du fichier vers un ordinateur accessible sur Internet garantit que les données réelles ne sont jamais disponibles sous forme de texte clair sur un ordinateur qui aurait pu être compromis en raison de sa connexion à Internet.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>Vérifiez que votre table de données sensible n’a pas de problèmes de mise en forme

Avant de hacher et de charger vos données sensibles, effectuez une recherche pour valider la présence de caractères spéciaux susceptibles de provoquer des problèmes lors de l’analyse du contenu.
Vous pouvez vérifier que la table est dans un format approprié à utiliser avec EDM à l’aide de l’agent de chargement EDM avec la syntaxe suivante :

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]
```

Si l’outil indique une incompatibilité dans le nombre de colonnes, cela peut être dû à la présence de virgules ou de guillemets dans les valeurs de la table qui sont confondues avec les délimiteurs de colonnes. Sauf s’ils entourent une valeur entière, les guillemets simples et doubles peuvent amener l’outil à mésidentifier l’endroit où une colonne individuelle démarre ou se termine.

**Si vous trouvez des guillemets simples ou doubles qui entourent des valeurs complètes** : vous pouvez les laisser tels qu’ils sont.

**Si vous trouvez des guillemets simples ou des virgules dans une valeur** : par exemple, le nom de la personne Tom O’Neil ou la ville 's-Gravenhage qui commence par un caractère apostrophe, vous devrez modifier le processus d’exportation de données utilisé pour générer la table d’informations sensibles pour entourer ces colonnes de guillemets doubles.

**Si des guillemets doubles sont trouvés à l’intérieur des valeurs**, il peut être préférable d’utiliser le format délimité par tabulation pour la table qui est moins sensible à ces problèmes.

### <a name="prerequisites"></a>Configuration requise

- Un compte professionnel ou scolaire pour Microsoft 365 qui sera ajouté au groupe de sécurité **EDM\_DataUploaders**
- une machine Windows 10 ou Windows Server 2016 avec .NET version 4.6.2 <!--4.7.2 un comment this around 9/29-->pour l’exécution d’EDMUploadAgent
- Un répertoire sur votre ordinateur de téléchargement pour :
  - [EDM Télécharger Agent](#links-to-edm-upload-agent-by-subscription-type)
  - votre fichier d’élément sensible au format .csv, .tsv ou pipe (|), **PatientRecords.csv** dans nos exemples
  - les fichiers de hachage et de sel de sortie créés dans cette procédure
  - Le nom du magasin de données provenant du fichier **edm.xml**, ici `PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>Configurer les groupe de sécurité personnalisé et compte d’utilisateur

1. En tant qu’administrateur général, accédez au centre d’administration à l’aide du [lien approprié pour votre abonnement](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription) et [créez un groupe de sécurité](/office365/admin/email/create-edit-or-delete-a-security-group) nommé **EDM\_DataUploaders**.

2. Ajoutez un ou plusieurs utilisateurs au groupe de sécurité **EDM\_DataUploaders**. (ces utilisateurs peuvent gérer la base de données d’informations sensibles).

### <a name="hash-and-upload-from-one-computer"></a>Hacher et charger à partir d’un même ordinateur

Cet ordinateur doit avoir accès directement à votre client Microsoft 365.

> [!NOTE]
> Avant de commencer cette procédure, assurez-vous que vous êtes membre du groupe de sécurité **EDM\_DataUploaders**.

> [!TIP]
>Si vous le souhaitez, vous pouvez exécuter une validation sur votre fichier de table source d’informations sensibles pour rechercher des erreurs avant le chargement en exécutant :
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> Pour plus d’informations sur toutes les EdmUploadAgent.exe les paramètres pris en charge s’exécutent
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

3. Autorisez l’agent Télécharger EDM, ouvrez la fenêtre d’invite de commandes en tant qu’administrateur, basculez vers le répertoire **C:\EDM\Data**, puis exécutez la commande suivante :

   `EdmUploadAgent.exe /Authorize`

   > [!IMPORTANT]
   > Vous devez exécuter **EdmUploadAgent** à partir du dossier où il est installé et indiquer le chemin d’accès complet à vos fichiers de données.

4. Connectez-vous à l’aide de votre compte professionnel ou scolaire pour Microsoft 365 qui a été ajouté au groupe de sécurité EDM_DataUploaders. Vos informations de client sont extraites du compte d’utilisateur pour établir la connexion.

   FACULTATIF : Si vous avez utilisé l’Assistant Type d’informations sensibles et le schéma Exact Data Match pour créer votre schéma, vous ***devez*** le télécharger pour l’utiliser dans cette procédure si vous ne l’avez pas déjà fait. Exécutez cette commande dans une fenêtre d’invite de commandes :

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. Pour hacher et charger les données sensibles, exécutez la commande suivante dans l’invite de commandes Windows :

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```

   > [!NOTE]
   > Le format par défaut du fichier de données sensibles est des valeurs séparées par des virgules. Vous pouvez spécifier un fichier séparé par des tabulations en indiquant l’option « {Tab} » avec le paramètre /ColumnSeparator, ou vous pouvez spécifier un fichier séparé par canal en indiquant l’option « | ».
   >
   > Exemple : `EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5`

   Si votre table d’informations sensibles a des valeurs incorrectement mises en forme, mais que vous souhaitez importer les données restantes tout en ignorant les lignes non valides de toute façon, vous pouvez utiliser le paramètre */AllowedBadLinesPercentage* dans la commande. L’exemple ci-dessus spécifie un seuil de cinq pour cent. Cela signifie que l’outil va hacher et charger la table d’informations sensibles, même si jusqu’à cinq pour cent des lignes ne sont pas valides.

   Cette commande ajoute automatiquement une valeur salt générée de manière aléatoire au hachage pour une sécurité accrue. Si vous voulez utiliser votre propre valeur salt, vous pouvez également ajouter **/Salt \<saltvalue\>** à la commande. Cette valeur doit comporter 64 caractères et ne peut contenir que les caractères allant de a à z et de 0 à 9.

6. Vérifiez l’état du chargement en exécutant la commande suivante :

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   Exemple : `EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords`

   Vous verrez l’état **ProcessingInProgress**. Vérifiez à quelques minutes d’intervalle jusqu’à ce que l’état devienne **Completed**. Une fois que le chargement est à l’état Completed, vos données EDM sont prêtes à l’emploi. Selon la taille de votre fichier de table source d’informations sensibles, cela peut prendre de quelques minutes à plusieurs heures.

> [!TIP]
> Si vous souhaitez être averti une fois que les données sensibles chargées sont prêtes à être utilisées, suivez les procédures [décrites dans Créer des notifications pour les activités de correspondance exacte des données](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities).

### <a name="separate-hash-and-upload"></a>Séparer le hachage et le chargement

Effectuez le hachage sur un ordinateur dans un environnement sécurisé. **EDMUploadAgent** doit être installé sur les deux ordinateurs.

FACULTATIF : Si vous avez utilisé l’Assistant Schéma exact de correspondance de données et type d’informations sensibles pour créer votre schéma et que vous ne l’avez pas encore téléchargé, exécutez la commande suivante dans une fenêtre d’invite de commandes pour télécharger le fichier au format XML :

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
   > Le format par défaut du fichier de données sensibles est des valeurs séparées par des virgules. Vous pouvez spécifier un fichier séparé par des tabulations en indiquant l’option « {Tab} » avec le paramètre /ColumnSeparator, ou vous pouvez spécifier un fichier séparé par canal en indiquant l’option « | ».

   Cela génère un fichier haché et un fichier salt avec les extensions suivantes si vous n’avez pas spécifié l’option **/Salt \<saltvalue\>**  :

   - .EdmHash
   - .EdmSalt

2. Copiez ces fichiers de manière sécurisée sur l’ordinateur que vous utiliserez pour charger votre fichier de table source d’informations sensibles (PatientRecords) sur votre locataire.

3. Autorisez l’agent Télécharger EDM, ouvrez la fenêtre d’invite de commandes en tant qu’administrateur, basculez vers le répertoire **C:\EDM\Data**, puis exécutez la commande suivante :

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

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

7. Si vous souhaitez voir tous les chargements de données dans un magasin particulier, exécutez la commande suivante dans une invite de commandes Windows pour afficher la liste de tous les magasins de données et quand ils ont été mis à jour :

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```

## <a name="next-step"></a>Étape suivante

- [Créer des données exactes correspondant au type d’informations sensibles/au package de règles](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)
