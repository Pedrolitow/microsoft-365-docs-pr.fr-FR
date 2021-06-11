---
title: Créer des types d’informations sensibles personnalisés à l’aide du classifieur Exact Data Match
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment créer des types d’informations sensibles personnalisés à l’aide d’une classification Exact Data Match.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6839401bc1dd00acc45992f902a6360eb7f20120
ms.sourcegitcommit: 337e8d8a2fee112d799edd8a0e04b3a2f124f900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "52878195"
---
# <a name="create-custom-sensitive-information-types-with-exact-data-match-based-classification"></a>Créez des types d’informations sensibles personnalisés à l’aide d’une classification Exact Data Match.



[Les types d’informations sensibles personnalisés](sensitive-information-type-learn-about.md) sont utilisés pour vous aider à identifier les éléments sensibles afin de pouvoir empêcher leur partage par inadvertance. Vous définissez un type d’informations sensibles personnalisé (SIT) basé sur :

- modèles
- mots clés de preuve, tels que *employé*,*badge* ou *ID*
- caractère à proximité de la preuve dans un modèle particulier
- niveaux de confiance

 De tels types d’informations sensibles personnalisés répondent aux besoins métier de nombreuses organisations.

Mais que se passe-t-il si vous voulez utiliser un type d’informations sensibles personnalisé qui utilise des valeurs de données exactes, au lieu d’un type qui établissait des correspondances avec des modèles génériques ? Une classification Exact Data Match (EDM) vous permet de créer un type d’informations sensibles personnalisé conçu pour :

- être dynamique et actualisé facilement ;
- être plus évolutif ;
- entraîner moins de faux positifs ;
- utiliser des données sensibles structurées ;
- gérer les informations sensibles de manière plus sécurisée ;
- être utilisé avec différents services de cloud computing Microsoft.

![Classification EDM](../media/EDMClassification.png)

La classification EDM vous permet de créer des types d’informations sensibles personnalisés qui font référence à des valeurs exactes dans une base de données d’informations sensibles. La base de données peut être actualisée quotidiennement et peut contenir jusqu’à 100 millions de lignes de données. À mesure que des employés, patients ou clients vont et viennent, et que les enregistrements changent, vos types d’informations sensibles personnalisés restent à jour et valides. Vous pouvez également utiliser la classification basée sur EDM avec des stratégies, telles [que les stratégies de protection contre la perte de données](dlp-learn-about-dlp.md) ou [les stratégies de fichier de Microsoft Cloud App Security](/cloud-app-security/data-protection-policies).

> [!NOTE]
> Microsoft 365 Information Protection prend désormais en charge, en préversion, les langues de jeu de caractères à double octets pour :
> - Chinois (simplifié)
> - Chinois (traditionnel)
> - Korean
> - Japanese
> 
> Cette prise en charge est disponible pour les types d’informations sensibles. Si vous souhaitez en savoir plus, consultez l’article [Prise en charge de la protection des informations pour les jeux de caractères à double octets (préversion)](mip-dbcs-relnotes.md).
 

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Pour effectuer les tâches décrites dans cet article, vous devez être un administrateur général, un administrateur de conformité ou un administrateur Exchange Online. Pour en avoir plus sur les autorisations DLP, consultez la section[Autorisations](data-loss-prevention-policies.md#permissions).

La classification EDM est incluse dans ces abonnements

- Office 365 E5
- Microsoft 365 E5
- Microsoft 365 E5 Conformité
- Microsoft E5/A5 Information Protection et gouvernance

## <a name="portal-links-for-your-subscription"></a>Liens vers les portails de votre abonnement


|Portail  |World Wide/GCC  |GCC-High  |DOD  |
|---------|---------|---------|---------|
|Office SCC     |  protection.office.com       |scc.office365.us         |scc.protection.apps.mil |
|Centre de sécurité Microsoft 365     |security.microsoft.com         |security.microsoft.us         |security.apps.mil|
|Centre de conformité Microsoft 365     |compliance.microsoft.com         |compliance.microsoft.us         |compliance.apps.mil|


## <a name="the-work-flow-at-a-glance"></a>Flux de travail en un clin d’œil

|Phase  |De quoi ai-je besoin ?  |
|---------|---------|
|[Partie 1: configurer la classification EDM](#part-1-set-up-edm-based-classification)<br/><br/>(selon vos besoins)<br/>- [Modifier le schéma de base de données](#editing-the-schema-for-edm-based-classification) <br/>- [Supprimer le schéma](#removing-the-schema-for-edm-based-classification) |-Accès en lecture aux données sensibles<br/>-Schéma de base de données au format XML (fourni en exemple)<br/>-Package de règles au format XML (fourni en exemple)<br/>-Autorisations d’administrateur sur le centre de sécurité & conformité (à l’aide de PowerShell) |
|[Partie 2 : hacher et télécharger les données sensibles](#part-2-hash-and-upload-the-sensitive-data)<br/><br/>(selon vos besoins)<br/>[Actualiser les données](#refreshing-your-sensitive-information-database) |-Groupe de sécurité personnalisé et compte d’utilisateur<br/>-Accès administrateur local à l’ordinateur à l’aide de l’agent de téléchargement EDM<br/>-Accès en lecture aux données sensibles<br/>-Processus et planification pour l’actualisation des données|
|[Partie 3: utiliser la classification EDM avec vos services Cloud Microsoft](#part-3-use-edm-based-classification-with-your-microsoft-cloud-services) |- Abonnement Microsoft 365 avec DLP<br/>- Fonctionnalité de classification EDM activée |

### <a name="part-1-set-up-edm-based-classification"></a>Partie 1 : configurer la classification EDM

La configuration de la classification basée sur EDM inclut les étapes suivantes :

1. [Enregistrement de données sensibles au format .csv ou .tsv](#save-sensitive-data-in-csv-or-tsv-format)
2. [Définition de votre schéma de base de données d’informations sensibles](#define-the-schema-for-your-database-of-sensitive-information)
3. [Création d’un package de règles](#set-up-a-rule-package)


#### <a name="save-sensitive-data-in-csv-or-tsv-format"></a>Enregistrer des données sensibles au format .csv format .tsv ou .tsv

1. Identifiez les informations sensibles que vous voulez utiliser. Exportez les données vers une application, telle que Microsoft Excel, et enregistrez le fichier dans un fichier texte. Le fichier peut être enregistré au format .csv (valeurs séparées par des virgules), .tsv (valeurs séparées par des tabulations) ou séparés par des |. Le format .tsv est recommandé dans les cas où vos valeurs de données peuvent inclure des virgules, telles que des adresses postales.
Le fichier de données peut inclure au maximum :
      - 100 millions de lignes de données sensibles
      - 32 colonnes (champs) par source de données
      - 5 colonnes (champs) marquées comme pouvant faire l’objet d’une recherche

2. Structurez les données sensibles dans le fichier .csv ou .tsv afin que la première ligne comprenne les noms des champs utilisés pour la classification EDM. Dans votre fichier, vous pouvez avoir des noms de champ tels que « ssn », « birthdate », « firstname », « lastname ». Les noms d’en-tête de colonne ne peuvent pas contenir des espaces ni des traits de soulignement. Par exemple, le fichier .csv utilisé dans cet exemple est appelé *PatientRecords.csv*. Ses colonnes incluent *PatientID*, *MRN*, *LastName*, *FirstName*, *SSN*, etc.

3. Prêtez attention au format des champs de données sensibles. En particulier, les champs qui peuvent contenir des virgules dans leur contenu, par exemple, une adresse de rue qui contient la valeur « Seattle,WA » sera évaluée en tant que deux champs distincts lors de l'.csv si le format .csv est sélectionné. Pour éviter cela, utilisez le format .tsv ou entourez la virgule contenant des valeurs par des guillemets doubles dans la table de données sensibles. Si des virgules contenant des valeurs contiennent également des espaces, vous devez créer un sit personnalisé qui correspond au format correspondant. Par exemple, un SIT qui détecte une chaîne à plusieurs mots avec des virgules et des espaces.

#### <a name="define-the-schema-for-your-database-of-sensitive-information"></a>Définir le schéma de votre base de données d’informations sensibles

Si, pour des raisons commerciales ou techniques, vous préférez ne pas utiliser PowerShell ou la ligne de commande pour créer votre schéma et votre modèle de type d’informations sensibles EDM (package de règles), vous pouvez utiliser l’[Assistant de correspondance exacte de données et de type d’informations sensibles](sit-edm-wizard.md) pour les créer. Lorsque vous avez terminé de créer le schéma et le modèle de type d’informations sensibles EDM, revenez à la procédure afin d’effectuer toutes les étapes nécessaires pour que votre type d’informations sensibles EDM soit disponible.

> [!NOTE]
> L’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles est disponible uniquement pour les nuages mondiaux et GCC.

1. Définissez le schéma pour la base de données d’informations sensibles dans un fichier XML (comme dans l’exemple ci-dessous). Nommez ce fichier de schéma **edm.xml** et configurez-le de telle sorte que pour chaque colonne de la base de données, une ligne utilise la syntaxe : 

      `\<Field name="" searchable=""/\>`.

      - Utilisez les noms de colonne pour les valeurs de *nom de champ*.
      - Utilisez *searchable="true"* pour jusqu’à 5 champs dont vous voulez qu’il puissent faire l’objet d’une recherche. Au moins un champ doit pouvoir faire l’objet d’une recherche.

      Par exemple, le fichier XML suivant définit le schéma d’une base de données de dossiers de patients, avec cinq champs pouvant faire l’objet d’une recherche : *PatientID*, *MRN*, *SSN*, *Phone*, and *DOB*.

      (vous pouvez copier, modifier et utiliser notre exemple).

      ```xml
      <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
            <DataStore name="PatientRecords" description="Schema for patient records" version="1">
                  <Field name="PatientID" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
                  <Field name="MRN" searchable="true" />
                  <Field name="FirstName" />
                  <Field name="LastName" />
                  <Field name="SSN" searchable="true" />
                  <Field name="Phone" searchable="true" />
                  <Field name="DOB" searchable="true" />
                  <Field name="Gender" />
                  <Field name="Address" />
            </DataStore>
      </EdmSchema>
      ```

##### <a name="configurable-match-using-the-caseinsensitive-and-ignoreddelimiters-fields"></a>Correspondance configurable à l’aide des champs caseInsensitive et ignoredDelimiters

L’exemple XML ci-dessus utilise les champs `caseInsensitive` et `ignoredDelimiters`. 

Lorsque vous incluez le champ ***caseInsensitive** _ défini sur la valeur `true` dans votre définition de schéma, EDM n’exclut pas un élément sur la base des différences de casse dans le champ `PatientID`. EDM considère donc `PatientID` _ *FOO-1234** et **fOo-1234** comme étant identiques.

Lorsque vous incluez le champ **ignoredDelimiters** _ avec les caractères pris en charge, EDM ignore ces caractères dans `PatientID`. EDM considère donc `PatientID` _ *FOO-1234** et `PatientID` **FOO#1234** comme étant identiques. L’indicateur `ignoredDelimiters` prend en charge tous les caractères non alphanumériques. Voici quelques exemples :
- \.
- \-
- \/
- \_
- \*
- \^
- \#
- \!
- \?
- \[
- \]
- \{
- \}
- \\
- \~
- \; 

L’indicateur `ignoredDelimiters` ne prend pas en charge :
- Les caractères 0 à 9
- A-Z
- a-z
- \"
- \,

Dans cet exemple, où `caseInsensitive` et `ignoredDelimiters` sont utilisés ensemble, EDM considère **FOO-1234** et **fOo#1234** comme étant identiques et classifie l’élément comme un type d’informations sensibles de dossier de patient. 

4. Connectez-vous au Centre de sécurité et conformité en utilisant la procédure [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

5. Pour charger le schéma de base de données, exécutez les cmdlets suivantes, l’une après l’autre :

      ```powershell
      $edmSchemaXml=Get-Content .\\edm.xml -Encoding Byte -ReadCount 0
      New-DlpEdmSchema -FileData $edmSchemaXml -Confirm:$true
      ```

      Vous êtes invité à confirmer comme suit :

      > Confirmer
      >
      > Êtes-vous sûr de vouloir effectuer cette action ?
      >
      > Un nouveau schéma EDM pour le magasin de données « patientrecords » va être importé.
      >
      > \[Y\] Oui \[A\] Oui pour tout \[N\] Non \[L\] Non pour tout \[?\] Aide (par défaut « Y ») :

> [!TIP]
> Si vous souhaitez que vos modifications se produisent sans confirmation, à l’étape 5, utilisez plutôt la cmdlet New-DlpEdmSchema -FileData $edmSchemaXml

> [!NOTE]
> La mise à jour du schéma EDMS avec les ajouts peut prendre de 10 à 60 minutes. Vous devez l’effectuer avant d’exécuter les étapes qui utilisent les ajouts.

#### <a name="set-up-a-rule-package"></a>Configurer un package de règles

1. Créez un package de règles au format XML (avec codage Unicode) similaire à l’exemple suivant. (vous pouvez copier, modifier et utiliser notre exemple).

      Lorsque vous définissez votre package de règles, veillez à référencer correctement .csv fichier .tsv ou .tsv **etedm.xml** fichier. Vous pouvez copier, modifier et utiliser notre exemple. Dans cet exemple de fichier xml, les champs suivants doivent être personnalisés pour créer votre type sensible d’EDM :

      - **RulePack id & ExactMatch id** : utilisez [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) pour générer un GUID.

      - **Datastore** : ce champ spécifie le magasin de données de recherche EDM à utiliser. Vous indiquez un nom de source de données ou un schéma EDM configuré.

      - **idMatch** : ce champ pointe vers l’élément principal pour EDM.
        - Matches : spécifie le champ à utiliser dans la recherche exacte. Vous fournissez un nom de champ pouvant faire l’objet d’une recherche dans le schéma EDM pour le magasin de données.
        - Classification : ce champ spécifie la correspondance de type sensible qui déclenche la recherche EDM. Vous pouvez fournir le nom ou le GUID d’un type d’informations sensibles intégré ou personnalisé. N’ignorez pas que toute chaîne qui correspond au type d’informations sensibles fourni sera hachée et comparée à chaque entrée de la table des informations sensibles. Pour éviter de provoquer des problèmes de performances, si vous utilisez un type d’informations sensibles personnalisé comme élément Classification dans Dem, évitez d’en utiliser un qui corresponde à un grand pourcentage de contenu (par exemple, « n’importe quel nombre » ou « tout mot de cinq lettres ») en ajoutant des mots clés à l’appui ou en ajoutant une mise en forme dans la définition du type d’informations sensibles de classification personnalisée. 

      - **Match :** ce champ pointe vers d’autres preuves à proximité d’idMatch.
        - Matches : vous indiquez un nom de champ dans le schéma EDM pour DataStore.
      - **Resource :** cette section spécifie le nom et la description du type sensible dans plusieurs paramètres régionaux.
        - idRef : fournissez un GUID pour ExactMatch ID.
        - Nom et descriptions : personnalisez si nécessaire.

      ```xml
      <RulePackage xmlns="http://schemas.microsoft.com/office/2018/edm">
        <RulePack id="fd098e03-1796-41a5-8ab6-198c93c62b11">
          <Version build="0" major="2" minor="0" revision="0" />
          <Publisher id="eb553734-8306-44b4-9ad5-c388ad970528" />
          <Details defaultLangCode="en-us">
            <LocalizedDetails langcode="en-us">
              <PublisherName>IP DLP</PublisherName>
              <Name>Health Care EDM Rulepack</Name>
              <Description>This rule package contains the EDM sensitive type for health care sensitive types.</Description>
            </LocalizedDetails>
          </Details>
        </RulePack>
        <Rules>
          <ExactMatch id = "E1CC861E-3FE9-4A58-82DF-4BD259EAB371" patternsProximity = "300" dataStore ="PatientRecords" recommendedConfidence = "65" >
            <Pattern confidenceLevel="65">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
            </Pattern>
            <Pattern confidenceLevel="75">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
              <Any minMatches ="3" maxMatches ="6">
                <match matches="PatientID" />
                <match matches="MRN"/>
                <match matches="FirstName"/>
                <match matches="LastName"/>
                <match matches="Phone"/>
                <match matches="DOB"/>
              </Any>
            </Pattern>
          </ExactMatch>
          <LocalizedStrings>
            <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB371">
              <Name default="true" langcode="en-us">Patient SSN Exact Match.</Name>
              <Description default="true" langcode="en-us">EDM Sensitive type for detecting Patient SSN.</Description>
            </Resource>
          </LocalizedStrings>
        </Rules>
      </RulePackage>
      ```

2. Téléchargez le package de règles en exécutant les cmdlets PowerShell suivantes, l’une après l’autre :

      ```powershell
      $rulepack=Get-Content .\\rulepack.xml -Encoding Byte -ReadCount 0
      New-DlpSensitiveInformationTypeRulePackage -FileData $rulepack
      ```

À ce stade, vous avez configuré la classification EDM. L’étape suivante consiste à hacher les données sensibles, puis à charger les hachages pour l’indexation.

Rappelez-vous que la procédure précédente de notre schéma PatientRecords définit cinq champs pouvant faire l’objet d’une recherche : *PatientID*,*MRN*, *SSN*, *Phone* et *DOB*. Notre exemple de package de règles inclut ces champs et référence le fichier de schéma de base de données (**edm.xml**), avec un seul élément *ExactMatch* par champ pouvant faire l’objet d’une recherche. Prenons l’élément ExactMatch suivant :

```xml
<ExactMatch id = "E1CC861E-3FE9-4A58-82DF-4BD259EAB371" patternsProximity = "300" dataStore ="PatientRecords" recommendedConfidence = "65" >
      <Pattern confidenceLevel="65">
        <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
        <Any minMatches ="3" maxMatches ="100">
          <match matches="PatientID" />
          <match matches="MRN"/>
          <match matches="FirstName"/>
          <match matches="LastName"/>
          <match matches="Phone"/>
          <match matches="DOB"/>
        </Any>
      </Pattern>
    </ExactMatch>
```

À partir de cet exemple, notez les points suivants :

- Le nom du magasin de données fait référence au fichier .csv que nous avons créé précédemment : **dataStore = "PatientRecords"**.

- La valeur idMatch fait référence à un champ pouvant faire l’objet d’une recherche figurant dans le fichier de schéma de base de données : **idMatch matches = "SSN"**.

- La valeur de classification fait référence à un type d’informations sensibles existant ou personnalisé : **classification = "U.S. Social Security Number (SSN)"** (en l’occurrence, nous utilisons le type d’informations sensibles existant pour le numéro de sécurité sociale aux États-Unis).

> [!NOTE]
> La mise à jour du schéma EDMS avec les ajouts peut prendre de 10 à 60 minutes. Vous devez l’effectuer avant d’exécuter les étapes qui utilisent les ajouts.
 
Après avoir importé votre package de règles avec votre type d’informations sensibles EDM et importé votre table de données sensibles, vous pouvez tester votre type nouvellement créé à l’aide de la fonction **Tester** dans l’Assistant Gestion des problèmes de sécurité des données dans le Centre de conformité. Consultez [Utiliser l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles](sit-edm-wizard.md) pour obtenir des instructions sur l’utilisation de cette fonctionnalité.

#### <a name="editing-the-schema-for-edm-based-classification"></a>Modification du schéma pour la classification EDM

Si vous souhaitez modifier votre fichier **edm.xml**, par exemple pour changer les champs utilisés pour la classification EDM, procédez comme suit :

> [!TIP]
> Vous pouvez modifier votre schéma EDM et votre fichier de données pour tirer parti d’une **correspondance configurable**. Lorsqu’il est configuré, EDM ignore les différences de casse et certains séparateurs lorsqu’il évalue un élément. Cela simplifie la définition de votre schéma XML et de vos fichiers de données sensibles. Pour plus d’informations, voir [Modifier le schéma de correspondance des données exactes pour utiliser la correspondance configurable](sit-modify-edm-schema-configurable-match.md).

1. Modifiez votre fichier **edm.xml** (présenté dans la section [Définir le schéma](#define-the-schema-for-your-database-of-sensitive-information) de cet article).

2. Connectez-vous au Centre de sécurité et conformité en utilisant la procédure [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

3. Pour mettre à jour votre schéma de base de données, exécutez les cmdlets suivantes, l’une après l’autre :

      ```powershell
      $edmSchemaXml=Get-Content .\\edm.xml -Encoding Byte -ReadCount 0
      Set-DlpEdmSchema -FileData $edmSchemaXml -Confirm:$true
      ```

      Vous êtes invité à confirmer comme suit :

      > Confirmer
      >
      > Êtes-vous sûr de vouloir effectuer cette action ?
      >
      > Le schéma EDM pour le magasin de données « patientrecords » va être mis à jour.
      >
      > \[Y\] Oui \[A\] Oui pour tout \[N\] Non \[L\] Non pour tout \[?\] Aide (par défaut « Y ») :

      > [!TIP]
      > Si vous souhaitez que vos modifications se produisent sans confirmation, à l’étape 3, utilisez plutôt la cmdlet Set-DlpEdmSchema -FileData $edmSchemaXml

      > [!NOTE]
      > La mise à jour du schéma EDMS avec les ajouts peut prendre de 10 à 60 minutes. Vous devez l’effectuer avant d’exécuter les étapes qui utilisent les ajouts.

#### <a name="removing-the-schema-for-edm-based-classification"></a>Suppression du schéma pour la classification EDM

(Le cas échéant) Si vous voulez supprimer le schéma que vous utilisez pour la classification EDM, procédez comme suit :

1. Connectez-vous au Centre de sécurité et conformité en utilisant la procédure [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez les applets de commande PowerShell suivantes, en remplaçant le nom de magasin de données « patient records » par celui que vous voulez supprimer :

      ```powershell
      Remove-DlpEdmSchema -Identity patientrecords
      ```

      Vous serez invité à confirmer :

      > Confirmer
      >
      > Êtes-vous sûr de vouloir effectuer cette action ?
      >
      > Le schéma EDM pour le magasin de données « patientrecords » va être supprimé.
      >
      > \[Y\] Oui \[A\] Oui pour tout \[N\] Non \[L\] Non pour tout \[?\] Aide (par défaut « Y ») :

      > [!TIP]
      >  Si vous souhaitez que vos modifications se produisent sans confirmation, à l’étape 2, utilisez plutôt la cmdlet Remove-DlpEdmSchema -Identity patientrecords -Confirm:$false

### <a name="part-2-hash-and-upload-the-sensitive-data"></a>Partie 2 : hacher et charger les données sensibles

Au cours de cette phase, vous configurez un groupe de sécurité personnalisé et un compte d’utilisateur, et configurez l’outil de chargement de l’agent EDM. Vous utilisez ensuite l’outil pour hacher les données sensibles avec valeur salt et les charger.

L’opération de hachage et de chargement peut être effectuée à l’aide d’un ordinateur ou vous pouvez séparer ces deux étapes pour renforcer la sécurité.

Si vous voulez hacher et charger à partir d’un ordinateur, vous devez le faire à partir d’un ordinateur qui peut se connecter directement à votre client Microsoft 365. Vos fichiers de données sensibles en texte clair doivent se trouver sur cet ordinateur pour le hachage.

Si vous ne souhaitez pas exposer votre fichier de données sensibles en texte clair, vous pouvez le hacher sur un ordinateur dans un emplacement sécurisé, puis copier le fichier de hachage et le fichier salt sur un ordinateur qui peut se connecter directement à votre client Microsoft 365 pour le chargement. Dans ce scénario, vous aurez besoin d’EDMUploadAgent sur les deux ordinateurs.

> [!IMPORTANT]
> Si vous utilisiez l’assistant du schéma de correspondance des données exacte et du type d’informations sensibles pour créer vos fichiers de schéma et de modèle, vous ***devez*** télécharger le schéma pour cette procédure.

> [!NOTE]
> Si votre organisation a installé la clé client pour [Microsoft 365](customer-key-overview.md)au niveau du client, la correspondance exacte des données utilisera automatiquement sa fonctionnalité de chiffrement. Cette offre est disponible uniquement pour les clients sous licence E5 dans le cloud commercial.

#### <a name="prerequisites"></a>Configuration requise

- Un compte professionnel ou scolaire pour Microsoft 365 qui sera ajouté au groupe de sécurité **EDM\_DataUploaders**
- Un ordinateur Windows 10 ou Windows Server 2016 avec .NET version 4.6.2 pour l’exécution d’EDMUploadAgent
- Un répertoire sur votre ordinateur de téléchargement pour :
    -  EDMUploadAgent
    - votre fichier d’élément sensible au format .csv .tsv ou .tsv, **PatientRecords.csv** dans nos exemples
    -  Les fichiers de hachage et salt générés
    - Le nom du magasin de données provenant du fichier **edm.xml**, ici `PatientRecords`
- Si vous avez utilisé l’[Assistant de schéma de correspondance exacte des données et de type d’informations sensibles](sit-edm-wizard.md), vous ***devez*** le télécharger.

#### <a name="set-up-the-security-group-and-user-account"></a>Configurer les groupe de sécurité personnalisé et compte d’utilisateur

1. En tant qu’administrateur général, accédez au centre d’administration à l’aide du [lien approprié pour votre abonnement](#portal-links-for-your-subscription) et [créez un groupe de sécurité](/office365/admin/email/create-edit-or-delete-a-security-group?view=o365-worldwide) nommé **EDM\_DataUploaders**.

2. Ajoutez un ou plusieurs utilisateurs au groupe de sécurité **EDM\_DataUploaders**. (ces utilisateurs peuvent gérer la base de données d’informations sensibles).

#### <a name="hash-and-upload-from-one-computer"></a>Hacher et charger à partir d’un même ordinateur

Cet ordinateur doit avoir accès directement à votre client Microsoft 365.

>[!NOTE]
> Avant de commencer cette procédure, assurez-vous que vous êtes membre du groupe de sécurité **EDM\_DataUploaders**.

> [!TIP]
> Si vous le souhaitez, vous pouvez exécuter une validation sur votre fichier .csv .tsv ou .tsv avant de télécharger en exécutant :
>
>`EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
>Pour plus d’informations sur tous les paramètres pris en charge par EdmUploadAgent.exe
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

   > [!TIP]
   > Exécutez l'agent sans arguments pour obtenir une liste des paramètres de commande pris en charge. Par exemple, « EdmUploadAgent.exe ».

2. Autorisez l’agent de chargement EDM, en ouvrant l’invite de commandes Windows (en tant qu’administrateur), puis en accédant au répertoire **C:\EDM\Data** pour exécuter la commande suivante :

   `EdmUploadAgent.exe /Authorize`

3. Connectez-vous à l’aide de votre compte professionnel ou scolaire pour Microsoft 365 qui a été ajouté au groupe de sécurité EDM_DataUploaders. Vos informations de client sont extraites du compte d’utilisateur pour établir la connexion.

   FACULTATIF : si vous avez utilisé l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles pour créer vos fichiers de schéma et de modèle, exécutez la commande suivante dans une fenêtre Invite de commandes :

   `EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>`

4. Pour hacher et charger les données sensibles, exécutez la commande suivante dans l’invite de commandes Windows :

   `EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"]`

   Exemple : **EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml**

   Le format par défaut du fichier de données sensibles est les valeurs séparées par des virgules. Vous pouvez spécifier un fichier séparé par des tabulations en indiquant l’option « {Tab} » avec le paramètre /ColumnSeparator, ou vous pouvez spécifier un fichier séparé par un canal en indiquant l’option « | ».  
   Cette commande ajoute automatiquement une valeur salt générée de manière aléatoire au hachage pour une sécurité accrue. Si vous voulez utiliser votre propre valeur salt, vous pouvez également ajouter **/Salt <saltvalue>** à la commande. Cette valeur doit comporter 64 caractères et ne peut contenir que les caractères allant de a à z et de 0 à 9.

5. Vérifiez l’état du chargement en exécutant la commande suivante :

   `EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>`

   Exemple : **EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords**

   Vous verrez l’état **ProcessingInProgress**. Vérifiez à quelques minutes d’intervalle jusqu’à ce que l’état devienne **Completed**. Une fois que le chargement est à l’état Completed, vos données EDM sont prêtes à l’emploi.

#### <a name="separate-hash-and-upload"></a>Séparer le hachage et le chargement

Effectuez le hachage sur un ordinateur dans un environnement sécurisé.

FACULTATIF : si vous avez utilisé l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles pour créer vos fichiers de schéma et de modèle, exécutez la commande suivante dans une fenêtre Invite de commandes :

`EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>`

1. À l’invite de commandes, exécutez la commande suivante :

   `EdmUploadAgent.exe /CreateHash /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] >`

   Par exemple :

   > **EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml**

   Cela génère un fichier haché et un fichier salt avec les extensions suivantes si vous n’avez pas spécifié l’option **/Salt <saltvalue>**  :
   - .EdmHash
   - .EdmSalt

2. Copiez ces fichiers de manière sécurisée sur l’ordinateur que vous utiliserez pour télécharger vos éléments sensibles .csv ou .tsv (PatientRecords) vers votre client.

   Pour charger les données hachées, exécutez la commande suivante dans l’invite de commandes Windows :

   `EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\>`

   Par exemple :

   > **EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\PatientRecords.EdmHash**


   Pour vérifier que vos données sensibles ont été téléchargées, exécutez la commande suivante dans l’invite de commandes Windows :

   `EdmUploadAgent.exe /GetDataStore`

   La liste des magasins de données apparaît, ainsi que la date de la dernière mise à jour.

   Si vous voulez afficher toutes les données téléchargées vers un magasin particulier, exécutez la commande suivante dans une invite de commandes Windows :

   `EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>`

   Poursuivez la configuration de votre processus et planifiez l’[actualisation de votre base de données d'informations sensibles](#refreshing-your-sensitive-information-database).

À ce stade, vous êtes prêt à utiliser la classification basée sur EDM avec vos services de Cloud Computing Microsoft. Par exemple, vous pouvez [configurer une stratégie DLP à l’aide d’une classification basée sur EDM](#to-create-a-dlp-policy-with-edm).

#### <a name="refreshing-your-sensitive-information-database"></a>Actualisation de votre base de données d’informations sensibles

Vous pouvez actualiser quotidiennement votre base de données d’informations sensibles, et l’outil de chargement EDM peut réindexer les données sensibles, puis recharger les données indexées.

1. Déterminez vos processus et leur fréquence (quotidien ou hebdomadaire) pour actualiser la base de données d’informations sensibles.

2. Réexportez les données sensibles vers une application, telle que Microsoft Excel, et enregistrez le fichier au format .csv ou .tsv. Conservez le même nom de fichier et l’emplacement que vous avez utilisé lorsque vous avez suivi les étapes décrites dans[Hachage et téléchargement des données sensibles](#part-2-hash-and-upload-the-sensitive-data).

      > [!NOTE]
      > Si aucune modification n’est apportée à la structure (noms de champs) du fichier .csv ou .tsv, vous n’avez pas besoin d’apporter des modifications à votre fichier de schéma de base de données lorsque vous actualisez les données. Si vous devez apporter des modifications, assurez-vous de modifier le schéma de base de données et votre package de règles en conséquence.

3. Utilisez [le planificateur de tâches](/windows/desktop/TaskSchd/task-scheduler-start-page) pour automatiser les étapes 2 et 3 dans la procédure[hacher et télécharger les données sensibles](#part-2-hash-and-upload-the-sensitive-data). Vous pouvez planifier des tâches à l’aide de plusieurs méthodes :

      | Méthode             | Procédure |
      | ---------------------- | ---------------- |
      | Windows PowerShell     | Consultez la documentation[ScheduledTasks](/powershell/module/scheduledtasks/?view=win10-ps) et l’[exemple de script PowerShell](#example-powershell-script-for-task-scheduler) dans cet article |
      | API planificateur de tâches     | Consultez la documentation relative au [planificateur de tâches](/windows/desktop/TaskSchd/using-the-task-scheduler)                                                                                                                                                                                                                                                                                |
      | Interface utilisateur Windows | Dans Windows, cliquez sur **Démarrer**, puis tapez Planificateur de tâches. Dans la liste des résultats, cliquez avec le bouton droit sur **planificateur de tâches**, puis sélectionnez **exécuter en tant qu’administrateur**.                                                                                                                                                                                                                                                                           |

#### <a name="example-powershell-script-for-task-scheduler"></a>Exemple de script PowerShell pour le planificateur de tâches

Cette section inclut un exemple de script PowerShell que vous pouvez utiliser pour planifier vos tâches de hachage de données et de téléchargement des données hachées :

##### <a name="to-schedule-hashing-and-upload-in-a-combined-step"></a>Pour planifier un hachage et effectuer un téléchargement dans une étape seule combinée

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext"
$uploadDataArgs = '/UploadData /DataStoreName ' + $dataStoreName + ' /DataFile ' + $dataFile + ' /HashLocation' + $hashLocation + ' /Schema ' + $schemaFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadDataArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

#### <a name="to-schedule-hashing-and-upload-as-separate-steps"></a>Pour planifier un hachage et effectuer un téléchargement en deux étapes distinctes

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$edmext = '.EdmHash'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
$hashFile = "$fileLocation\\$dataStoreName$edmext"
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext "

\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$createHashArgs = '/CreateHash' + ' /DataFile ' + $dataFile + ' /HashLocation ' + $hashLocation + ' /Schema ' + $schemaFile
$uploadHashArgs = '/UploadHash /DataStoreName ' + $dataStoreName + ' /HashFile ' + $hashFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $createHashArgs -WorkingDirectory $edminstallpath
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadHashArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password

```

### <a name="part-3-use-edm-based-classification-with-your-microsoft-cloud-services"></a>Partie 3 : utiliser la classification EDM avec vos services de cloud computing Microsoft

Ces emplacements prennent en charge les types d’informations sensibles EDM :

- DLP pour Exchange Online (e-mail)
- OneDrive Entreprise (fichiers)
- Microsoft Teams (conversations)
- DLP pour SharePoint (fichiers)
- Stratégies DLP de la sécurité de l’application Microsoft Cloud
- Stratégies d’étiquetage automatique côté serveur : disponibles pour les clients du cloud commercial <!--, UNCOMMENT THIS ON 6/15 and government cloud customers-->

#### <a name="to-create-a-dlp-policy-with-edm"></a>Pour créer une stratégie DLP avec EDM

1. Accédez au Centre de conformité et de sécurité à l’aide du [lien approprié pour votre abonnement](#portal-links-for-your-subscription).

2. Sélectionnez stratégie de **Protection contre la perte de données** \> ****.

3. Sélectionnez **Créer une stratégie** \> **Personnaliser** \> **Suivant**.

4. Sous l'onglet **Nommez votre stratégie**, spécifiez un nom et une description, puis sélectionnez **suivant**.

5. Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.

6. Dans la colonne **État**, sélectionnez **Courrier Exchange, Comptes OneDrive, Messages de conversation et de canal de Teams**, puis **Suivant**.

7. Sous l'onglet **paramètres de stratégie**, sélectionnez **utiliser les paramètres avancés**, puis **suivant**.

8. Sélectionnez **+ Nouvelle règle**.

9. Dans la section **Nom**, spécifiez un nom et une description pour la règle.

10. Dans la section **conditions**, dans la liste **+ ajouter une condition**, sélectionnez **le contenu contient un type de contenu sensible**.

      ![Le contenu contient des types d’informations sensibles](../media/edm-dlp-newrule-conditions.png)

11. Recherchez le type d’informations sensibles que vous avez créé lorsque vous avez configuré votre package de règles, puis sélectionnez **+ ajouter**.  
    Sélectionnez **Terminer**.

12. Terminez de sélectionner les options de votre règle, telles que **notifications d’utilisateur**,**remplacements d’utilisateur**, **rapports d’incident**, puis sélectionnez **Enregistrer**.

13. Sous l'onglet **paramètres de stratégie**, passez en revue vos règles, puis sélectionnez **suivant**.

14. Indiquez si vous voulez activer la stratégie immédiatement, tester celle-ci ou la maintenir désactivée. Sélectionnez **Suivant**.

15. Sous l'onglet **Vérifier vos paramètres**, passez en revue votre stratégie. Apportez les modifications nécessaires. Lorsque vous avez terminé, sélectionnez **Créer**.

> [!NOTE]
> Comptez environ une heure avant que votre nouvelle stratégie DLP soit appliquée à l’ensemble de votre centre de données.

## <a name="related-articles"></a>Articles connexes

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md).
- [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)
- [Microsoft Cloud App Security](/cloud-app-security)
- [New-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
- [Modifier le schéma de correspondance des données exactes pour utiliser la correspondance configurable](sit-modify-edm-schema-configurable-match.md)
