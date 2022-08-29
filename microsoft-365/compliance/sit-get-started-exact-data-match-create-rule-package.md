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
ms.openlocfilehash: 1ff8a9d39dec1fe46924dc02f8e05473947fd61f
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67359118"
---
# <a name="create-exact-data-match-sensitive-information-typerule-package"></a>Créer des données exactes correspondant au type d’informations sensibles/au package de règles

## <a name="applies-to"></a>S’applique à

- [Expérience classique](sit-create-edm-sit-classic-ux-workflow.md)

Vous pouvez créer un type d’informations sensibles (SIT) de correspondance de données exacte (SIT) à [l’aide du schéma EDM et de l’Assistant SIT](#use-the-edm-schema-and-sit-wizard) dans le Centre de conformité ou créer [manuellement](#create-a-rule-package-manually) le fichier XML du package de règles. Vous pouvez également combiner les deux à l’aide d’une méthode pour créer le schéma et le modifier ultérieurement à l’aide de l’autre méthode.

Si vous n’êtes pas familiarisé avec LES SERVICES basés sur EDM ou leur implémentation, vous devez vous familiariser avec les éléments suivants :

- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

## <a name="use-the-edm-schema-and-sit-wizard"></a>Utiliser le schéma EDM et l’Assistant SIT

Vous pouvez utiliser cet Assistant pour créer vos fichiers de type d’informations sensibles (SIT) afin de simplifier le processus.

Un type d’informations sensibles EDM est composé d’un ou de plusieurs modèles. Chaque modèle décrit une combinaison de preuves (champs du schéma) qui seront utilisées pour identifier le contenu sensible dans un document ou un e-mail.

## <a name="pre-requisites"></a>Conditions préalables

Effectuez les étapes décrites dans ces articles :

1. [Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
2. [Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)
3. [Hacher et charger la table de source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)

- Que vous créiez un type d’informations sensibles EDM à l’aide de l’Assistant ou du fichier XML du package de règles via PowerShell, vous devez disposer des autorisations d’administrateur général ou d’administrateur de conformité pour créer, tester et déployer un type d’informations sensibles personnalisé via l’interface utilisateur. [Consultez À propos des rôles d’administrateur dans Office 365](/office365/admin/add-users/about-admin-roles).
- Identifiez l’un des SIT intégrés à utiliser comme type d’informations sensibles d’éléments principaux.
  - Si aucun des types d’informations sensibles intégrés ne correspond aux données de la colonne que vous avez sélectionnée, vous devez créer un type d’informations sensibles personnalisé qui le fait.
  - Si vous avez sélectionné l’option Délimiteurs ignorés pour la colonne d’élément principal dans votre schéma, assurez-vous que le SIT personnalisé que vous créez correspondra aux données avec et sans les délimiteurs sélectionnés.
  - Si vous utilisez un sit intégré, assurez-vous qu’il détecte exactement les chaînes que vous souhaitez sélectionner, et n’inclut aucun caractère environnant ou exclut une partie valide de la chaîne telle qu’elle est stockée dans votre table d’informations sensibles.

Consultez les [définitions d’entité de type d’informations sensibles](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) et [créez des types d’informations sensibles personnalisés dans le Centre de conformité](create-a-custom-sensitive-information-type.md).

### <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Utiliser l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles

1. Dans le portail de conformité Microsoft Purview de votre locataire, accédez à la **classification** > **des données Correspondances exactes des données**.

2. Choisissez **Types d’informations sensibles EDM** et **Créer un type d’informations sensibles EDM** pour ouvrir l’Assistant de configuration des types d’informations sensibles.

3. **Choisissez un schéma EDM existant** et choisissez le schéma que vous avez créé dans [Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

4. Choisissez **Suivant**, puis **Créer un modèle**.

5. Choisissez le **Niveau de confiance** et l’**Élément principal**. Pour en savoir plus sur les niveaux de confiance, consultez [En savoir plus sur les types d’informations sensibles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

6. Choisissez le **type d’informations sensibles de l’élément principal** à associer pour définir le texte du document qui sera comparé à toutes les valeurs du champ d’élément principal. Voir [Définitions des entités de types d’informations sensibles](sensitive-information-type-entity-definitions.md) pour en savoir plus sur les types d’informations sensibles disponibles.

   > [!IMPORTANT]
   > Sélectionnez un type d’informations sensibles qui correspond étroitement au format du contenu que vous souhaitez trouver. La sélection d’un type d’informations sensibles qui correspond à du contenu inutile, comme celui qui correspond à toutes les chaînes de texte, ou tous les nombres peut entraîner une charge excessive dans le système, ce qui peut entraîner l’absence d’informations sensibles.

7. Choisissez vos **éléments de prise en charge** et les options de correspondance.

8. Choisissez **Terminé** et **Suivant**.

9. Choisissez vos **Niveau de confiance et proximité des caractères** souhaités. Il s’agit de la valeur par défaut pour l’ensemble du type d’informations sensibles EDM.

10. Choisissez **Créer un modèle** si vous souhaitez créer des modèles supplémentaires pour votre type d’informations sensibles EDM.

11. Choisissez **Suivant**, puis entrez un **Nom** et une **Description pour les administrateurs**.

12. Passez en revue vos paramètres, puis sélectionnez **Envoyer**.

### <a name="edit-or-delete-the-sensitive-information-type-pattern"></a>Modifier ou supprimer le modèle de type d’informations sensibles

1. Ouvrir la classification des données **du Centre** >  de **conformité** > **Correspondances exactes des données**.

2. Choisissez les **types d’informations sensibles EDM**.

3. Choisissez le SIT EDM que vous souhaitez modifier.

4. Choisissez **Modifier le type d’informations sensibles EDM** ou **Supprimer le type d’informations sensibles EDM** dans le menu volant.

## <a name="working-with-specific-types-of-data"></a>Utilisation de types de données spécifiques

Pour des raisons de performances, il est essentiel d’utiliser des modèles qui réduisent le nombre de correspondances inutiles. Par exemple, vous pouvez utiliser un type d’informations sensibles basé sur l’expression régulière.

`\b\w*\b`

Cela correspondrait à chaque mot ou numéro individuel dans un document ou un e-mail. Cela entraînerait une surcharge du service avec des correspondances et une absence de détection des correspondances vraies. L’utilisation de modèles plus précis peut éviter cette situation. Voici quelques recommandations pour identifier la configuration appropriée pour certains types de données courants.

**Email adresses** : Email adresses peuvent être faciles à identifier, mais étant donné qu’elles sont si courantes dans le contenu, elles peuvent entraîner une charge importante dans le système si elles sont utilisées comme champ principal. Utilisez-les uniquement comme preuve secondaire. S’ils doivent être utilisés comme preuve principale, essayez de définir un type d’informations sensibles personnalisé qui utilise la logique pour exclure leur utilisation en tant que `From` ou `To` champs dans les e-mails, et d’exclure ceux avec l’adresse e-mail de votre entreprise afin de réduire le nombre de chaînes inutiles qui doivent être mises en correspondance.

**Numéros de téléphone** : les numéros de téléphone peuvent être dans de nombreux formats différents, y compris ou à l’exclusion des préfixes de pays, des codes régionaux et des séparateurs. Pour réduire les faux négatifs tout en maintenant la charge au minimum, utilisez-les uniquement comme éléments secondaires, excluez tous les séparateurs probables, comme les parenthèses et les tirets, et incluez uniquement dans votre table de données sensible la partie qui sera toujours présente dans le numéro de téléphone.

**Noms de la personne** : n’utilisez pas les noms de la personne comme éléments principaux si vous utilisez un type d’informations sensibles basé sur une expression régulière comme élément de classification pour ce type EDM, car ils sont difficiles à distinguer des mots courants.

Si vous devez utiliser un élément principal difficile à identifier avec un modèle spécifique, comme un nom de code de projet qui peut générer un grand nombre de correspondances à traiter, veillez à inclure des mots clés dans le type d’informations sensibles que vous utilisez comme élément de classification pour votre type EDM. Par exemple, si vous utilisez des noms de code de projet qui peuvent être des mots réguliers, vous pouvez utiliser le mot `project` comme preuve supplémentaire requise à proximité du modèle d’expression régulière de nom de projet dans le type sensible utilisé comme élément de classification pour votre type EDM. Vous pouvez également envisager d’utiliser un type sensible basé sur un dictionnaire standard comme élément de classification pour votre sit EDM.

Lorsque vous essayez de faire correspondre des chaînes numériques, spécifiez les plages autorisées de nombres, telles que le nombre de chiffres ou les chiffres de départ, le cas échéant. Si vous devez faire correspondre une plage de nombres relativement flexible, vous pouvez utiliser des mots clés dans le SIT de base pour réduire le nombre de correspondances. Par exemple, si vous tentez de faire correspondre des numéros de compte composés de 7 à 11 chiffres, ajoutez les mots `account`, `customer``acct.` au SIT en tant que preuve supplémentaire requise. Cela réduit la probabilité de correspondances inutiles qui pourraient entraîner le dépassement des limites de correspondances à traiter par EDM.

Si un champ que vous devez utiliser comme élément principal suit un modèle simple susceptible de provoquer un grand nombre de correspondances et que vous ne pouvez pas ajouter la présence de mots clés comme preuve supplémentaire dans le type d’informations sensibles, vous pouvez également exiger un nombre minimal d’occurrences de ce modèle. Par exemple, vous pouvez utiliser un type d’informations sensibles personnalisé défini de la manière suivante pour détecter au moins 29 autres nombres à cinq chiffres entourant un nombre potentiel à cinq chiffres à faire correspondre à EDM :

```xml
 <Entity id="98703510-18b3-43d4-961f-15317594beb7"
                  patternsProximity="300"
                  recommendedConfidence="85"
                  relaxProximity="false">
                  <Pattern confidenceLevel="85"
                              proximity="300">
                              <IdMatch idRef="MRN"/>
                              <Match idRef="30 AccountNrs"
                                    minCount="30"
                                    proximity="3000"
                                    uniqueResults="true"/>
                  </Pattern>
      </Entity>
      <Regex id="30 AccountNrs">\d{5}</Regex>
```

Dans certains cas, vous devrez peut-être identifier certains numéros d’identification de compte ou d’enregistrement qui, pour des raisons historiques, ne suivent pas un modèle standardisé. Par exemple, `Medical Record Numbers` peut être composé de nombreuses permutations différentes de lettres et de nombres au sein de la même organisation. Même s’il peut être difficile au début d’identifier un modèle, une inspection plus étroite vous permet souvent d’affiner un modèle qui décrit toutes les valeurs valides sans provoquer un nombre excessif de correspondances non valides. Par exemple, il peut être détecté que « tous les MRN ont au moins sept caractères, ont au moins deux chiffres numériques en eux, et s’ils contiennent des lettres, ils commencent par un ». La création d’une expression régulière basée sur de tels critères doit vous permettre de réduire les correspondances inutiles tout en capturant toutes les valeurs souhaitées, et une analyse plus approfondie peut permettre une précision accrue en définissant des modèles distincts qui décrivent différents formats.

## <a name="create-a-rule-package-manually"></a>Créer un package de règles manuellement

Cette procédure vous montre comment créer un fichier au format XML appelé package de règles (avec encodage Unicode), puis le charger dans Microsoft Purview à l’aide des applets de commande PowerShell sécurité & conformité.

> [!NOTE]
> Si le sit auquel vous mappez peut détecter des preuves corroborantes multi-mots, les éléments secondaires que vous définissez dans un package de règles créé manuellement peuvent être mappés au SIT. Par exemple, le nom `John Smith` ne correspondrait pas en tant qu’élément secondaire, car nous comparions `John` et `Smith` trouvions le contenu séparément au terme `John Smith` chargé dans l’un des champs, si ce champ de preuve corroborant n’était pas mappé à un SIT capable de détecter ce modèle.
>
> Il existe une limite de 10 packages de règles dans un locataire Microsoft 365. Étant donné qu’un package de règles peut contenir un nombre arbitraire de types d’informations sensibles, vous pouvez éviter de créer un package de règles chaque fois que vous souhaitez définir un nouveau type d’informations sensibles à l’aide de cette méthode, à la place exporter un package de règles existant et ajouter vos types d’informations sensibles au code XML avant de le charger à nouveau.

1. Créez un package de règles au format XML (avec codage Unicode) similaire à l’exemple suivant. (vous pouvez copier, modifier et utiliser notre exemple).

   Lorsque vous configurez votre package de règles, veillez à référencer correctement votre fichier de table source d’informations sensibles .csv, .tsv ou pipe (|) délimité et **edm.xml** fichier de schéma. Vous pouvez copier, modifier et utiliser notre exemple. Dans cet exemple xml, les champs suivants doivent être personnalisés pour créer votre type sensible EDM :

   - **RulePack id & ExactMatch id** : utilisez [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) pour générer un GUID.

   - **Datastore** : ce champ spécifie le magasin de données de recherche EDM à utiliser. Vous fournissez le nom de la source de données du schéma EDM configuré.

   - **idMatch** : ce champ pointe vers l’élément principal pour EDM.
   - **Correspondances** : spécifie le champ à utiliser dans la recherche exacte. Vous fournissez un nom de champ pouvant faire l’objet d’une recherche dans le schéma EDM pour le magasin de données.
   - **Classification** : ce champ spécifie la correspondance de type d’informations sensibles qui déclenche la recherche EDM. Vous pouvez utiliser le nom ou le GUID d’un type d’informations sensibles intégré ou personnalisé existant.

   > [!NOTE]
   > N’oubliez pas que toute chaîne qui correspond au SIT fourni sera hachée et comparée à chaque entrée de la table source d’informations sensibles. Pour éviter les problèmes de performances si vous choisissez un SIT personnalisé pour l’élément de classification, n’utilisez pas celui qui correspond à un pourcentage important de contenu. Par exemple, un qui correspond à « n’importe quel nombre » ou « n’importe quel mot de cinq lettres ». Vous pouvez le différencier en ajoutant des mots clés de prise en charge ou en incluant la mise en forme dans la définition de la classification personnalisée SIT.

   - **Correspondance** : ce champ pointe vers des preuves supplémentaires trouvées à proximité d’idMatch.
   - **Correspondances** : vous fournissez n’importe quel nom de champ dans le schéma EDM pour DataStore.
   - **IDRef de ressource :** Cette section spécifie le nom et la description du type sensible dans plusieurs paramètres régionaux
     - Vous fournissez le GUID pour l’ID ExactMatch.
     - **Nom** &  **description** : personnaliser en fonction des besoins.

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

2. Chargez le package de règles en exécutant la commande PowerShell suivante :

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('.\\rulepack.xml'))
   ```

> [!NOTE]
> La syntaxe du fichier de package de règles est la même que pour les autres types d’informations sensibles. Pour plus d’informations sur la syntaxe du fichier de package de règles et d’autres options de configuration, et pour obtenir des instructions sur la modification et la suppression de types d’informations sensibles à l’aide de PowerShell, [créez un type d’informations sensibles personnalisé à l’aide de PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md#create-a-custom-sensitive-information-type-using-powershell).

## <a name="next-step"></a>Étape suivante

- **Pour une expérience classique** : [tester un type d’informations sensibles correspondant exactement aux données](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)
