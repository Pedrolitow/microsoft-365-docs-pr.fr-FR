---
title: Créer des données exactes correspondant au type d’informations sensibles/au package de règles
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
description: Créer des données exactes correspondant au type d’informations sensibles/au package de règles
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e44d18bc1a779ace95fb2f64171ff0bf91de57ed
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526039"
---
# <a name="create-exact-data-match-sensitive-information-typerule-package"></a>Créer des données exactes correspondant au type d’informations sensibles/au package de règles

Vous pouvez créer un type d’informations sensibles (SIT) de correspondance de données exacte (EDM) à l’aide du schéma [EDM](#use-the-edm-schema-and-sit-wizard) et de l’Assistant SIT dans le Centre de conformité ou créer manuellement le fichier XML du package de [règles.](#create-a-rule-package-manually) Vous pouvez également combiner les deux à l’aide d’une méthode pour créer le schéma et le modifier ultérieurement à l’aide de l’autre méthode.

Si vous n’êtes pas familiarisé avec EDM based SITS ou leur implémentation, vous devez vous familiariser avec :

- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

## <a name="use-the-edm-schema-and-sit-wizard"></a>Utiliser le schéma EDM et l’Assistant SIT

Vous pouvez utiliser cet Assistant pour créer vos fichiers de type d’informations sensibles (SIT) afin de simplifier le processus.

Un type d’informations sensibles EDM est composé d’un ou plusieurs modèles. Chaque modèle décrit une combinaison de preuves (champs du schéma) qui seront utilisées pour identifier le contenu sensible dans un document ou un e-mail.

## <a name="pre-requisites"></a>Conditions préalables

Effectuez les étapes des articles suivants :

1. [Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
2. [Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)
3. [Hacher et charger la table de source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)

- Que vous créiez un type d’informations sensibles EDM à l’aide de l’Assistant ou du fichier XML du package de règles via PowerShell, vous devez avoir des autorisations d’administrateur global ou d’administrateur de conformité pour créer, tester et déployer un type d’informations sensibles personnalisé via l’interface utilisateur. Voir [à propos des rôles d’administrateur dans Office 365](/office365/admin/add-users/about-admin-roles).
- Identifiez l’un des sits intégrés à utiliser comme type d’informations sensibles des éléments principaux.
  - Si aucun des types d’informations sensibles intégrés ne correspond aux données de la colonne que vous avez sélectionnée, vous devez créer un type d’informations sensibles personnalisé.
  - Si vous avez sélectionné l’option Delimiters ignorés pour la colonne d’élément principal dans votre schéma, assurez-vous que la fonction SIT personnalisée que vous créez correspondra aux données avec et sans les délimiteurs sélectionnés.
  - Si vous utilisez un sit intégré, assurez-vous qu’il détecte exactement les chaînes que vous souhaitez sélectionner, et n’inclut pas les caractères environnants ou n’exclut aucune partie valide de la chaîne telle qu’elle est stockée dans votre table d’informations sensibles.

Voir [Définitions d’entités de types d’informations sensibles](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) et [Créer des types d’informations sensibles personnalisés dans le Centre de conformité](create-a-custom-sensitive-information-type.md).

### <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Utiliser l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles

1. Dans le Centre de conformité Microsoft 365 pour votre client, accédez à **Classification des données** > **Correspondances exactes des données**.

2. Choisissez **Types d’informations sensibles EDM** et **Créer un type d’informations sensibles EDM** pour ouvrir l’Assistant de configuration des types d’informations sensibles.

3. Choose **Choose an existing EDM schema** and choose the schema you created in [Create the schema for exact data match based sensitive information types](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

4. Choisissez **Suivant**, puis **Créer un modèle**.

5. Choisissez le **Niveau de confiance** et l’**Élément principal**. Pour en savoir plus sur les niveaux de confiance, voir [En savoir plus sur les types d’informations sensibles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

6. Choisissez le **type d’informations sensibles de l’élément** principal à associer pour définir le texte du document qui sera comparé à toutes les valeurs du champ d’élément principal. Voir [Définitions des entités de types d’informations sensibles](sensitive-information-type-entity-definitions.md) pour en savoir plus sur les types d’informations sensibles disponibles.

   > [!IMPORTANT]
   > Sélectionnez un type d’informations sensibles qui correspond étroitement au format du contenu que vous souhaitez trouver. La sélection d’un type d’informations sensibles qui correspond à du contenu inutile, tel qu’un type qui correspond à toutes les chaînes de texte, ou tous les nombres peuvent entraîner une charge excessive dans le système, ce qui peut entraîner l’manquée d’informations sensibles. Consultez la section Recommandations de l’article Introduction à la correspondance exacte des données de cette documentation pour obtenir des recommandations sur la sélection d’un type d’informations sensibles à utiliser ici.

7. Choisissez vos **éléments de prise en charge** et les options de correspondance.

8. Choisissez **Terminé** et **Suivant**.

9. Choisissez vos **Niveau de confiance et proximité des caractères** souhaités. Il s’ra de la valeur par défaut pour l’ensemble du type d’informations sensibles EDM.

10. Choisissez **Créer un modèle** si vous souhaitez créer des modèles supplémentaires pour votre type d’informations sensibles EDM.

11. Choisissez **Suivant**, puis entrez un **Nom** et une **Description pour les administrateurs**.

12. Passez en revue vos paramètres, puis sélectionnez **Envoyer**.

### <a name="edit-or-delete-the-sensitive-information-type-pattern"></a>Modifier ou supprimer le modèle de type d’informations sensibles

1. Ouvrir **le centre de conformitéData** >  **classificationExact** >  **correspond aux données**.

2. Choisissez **les types d’informations sensibles EDM**.

3. Choisissez l’EDM SIT que vous souhaitez modifier.

4. Choisissez **Modifier le type d’informations sensibles EDM** ou **supprimer le type** d’informations sensibles EDM dans le volant.

## <a name="create-a-rule-package-manually"></a>Créer manuellement un package de règles

Cette procédure vous montre comment créer un fichier au format XML appelé package de règles (avec codage Unicode), puis le télécharger dans Microsoft 365 à l’aide des cmdlets PowerShell du Centre de conformité.

> [!NOTE]
> Si le sit que vous mappé peut détecter des preuves corroborante à plusieurs mots, les éléments secondaires que vous définissez dans un package de règles créé manuellement peuvent être mappés à la sit. Par exemple, `John Smith` le nom ne correspond pas en tant qu’élément secondaire, car nous le comparerions et le trouverions séparément dans le terme téléchargé dans l’un des champs, si ce champ de preuve corroborante n’a `John` `Smith` `John Smith` pas été mappé à un sit qui peut détecter ce modèle.
>
> Il existe une limite de 10 packages de règles dans un Microsoft 365 client. Dans la mesure où un package de règles peut contenir un nombre arbitraire de types d’informations sensibles, vous pouvez éviter de créer un nouveau package de règles chaque fois que vous souhaitez définir un nouveau type d’informations sensibles à l’aide de cette méthode, au lieu d’exporter un package de règles existant et d’ajouter vos types d’informations sensibles au XML avant de le re-télécharger.

1. Créez un package de règles au format XML (avec codage Unicode) similaire à l’exemple suivant. (vous pouvez copier, modifier et utiliser notre exemple).

   Lorsque vous définissez votre package de règles, veillez à référencer correctement votre fichier de table de sources d’informations sensibles .csv, .tsv ou pipe (|) délimité par des informations sensibles **** et votre fichier de schémaedm.xmlinformations sensibles. Vous pouvez copier, modifier et utiliser notre exemple. Dans cet exemple de xml, les champs suivants doivent être personnalisés pour créer votre type sensible EDM :

   - **RulePack id & ExactMatch id** : utilisez [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) pour générer un GUID.

   - **Datastore** : ce champ spécifie le magasin de données de recherche EDM à utiliser. Vous indiquez le nom de la source de données du schéma EDM configuré.

   - **idMatch** : ce champ pointe vers l’élément principal pour EDM.
   - **Correspondances** : spécifie le champ à utiliser dans la recherche exacte. Vous fournissez un nom de champ pouvant faire l’objet d’une recherche dans le schéma EDM pour le magasin de données.
   - **Classification** : ce champ spécifie la correspondance de type d’informations sensibles qui déclenche la recherche EDM. Vous pouvez utiliser le nom ou le GUID d’un type d’informations sensibles intégré ou personnalisé existant.

   > [!NOTE]
   > N’ignorez pas que toute chaîne qui correspond à la sit fournie sera hachée et comparée à chaque entrée de la table des sources d’informations sensibles. Pour éviter les problèmes de performances si vous choisissez une sit personnalisée pour l’élément de classification, n’utilisez pas une autre qui correspondra à un pourcentage élevé de contenu. Par exemple, un qui correspond à « n’importe quel nombre » ou « tout mot à cinq lettres ». Vous pouvez la différencier en ajoutant des mots clés de prise en charge ou en incluant la mise en forme dans la définition de la classification personnalisée SIT.

   - **Correspondance** : ce champ pointe vers des preuves supplémentaires trouvées à proximité d’idMatch.
   - **Correspondances** : vous fournissez n’importe quel nom de champ dans le schéma EDM pour DataStore.
   - **Resource idRef:** Cette section spécifie le nom et la description du type sensible dans plusieurs paramètres régionaux
     - Vous fournissez le GUID de l’ID ExactMatch.
     - **Nom** &  **description**: customize as required.

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

2. Télécharger package de règles en exécutant la commande PowerShell suivante :

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('.\\rulepack.xml'))
   ```

> [!NOTE]
> La syntaxe du fichier de package de règles est identique à celle des autres types d’informations sensibles. Pour obtenir des détails complets sur la syntaxe du fichier de package de règles et des options de configuration supplémentaires, et pour obtenir des instructions sur la modification et la suppression de types d’informations sensibles à l’aide de PowerShell, créez un type d’informations sensibles personnalisé à l’aide de [PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md#create-a-custom-sensitive-information-type-using-powershell).

## <a name="next-step"></a>Étape suivante

- [Tester un type d’informations sensibles correspondant exactement aux données](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)
