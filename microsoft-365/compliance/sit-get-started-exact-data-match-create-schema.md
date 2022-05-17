---
title: Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes
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
description: Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9eb4e69aa833e8a355115115e1c965e57d65716c
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435278"
---
# <a name="create-the-schema-for-exact-data-match-based-sensitive-information-types"></a>Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Vous pouvez créer le schéma et EDM SIT à l’aide de [l’Assistant Utiliser le schéma de correspondance exacte des données et le modèle de type d’informations sensibles](#use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard) ou [manuellement](#create-exact-data-match-schema-manually-and-upload). Vous pouvez également combiner les deux à l’aide d’une méthode pour créer le schéma et le modifier ultérieurement à l’aide de l’autre méthode.

Si vous n’êtes pas familiarisé avec les services SES basés sur EDM ou leur implémentation, vous devez vous familiariser avec les éléments suivants :

- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

Un schéma EDM unique peut être utilisé dans plusieurs types d’informations sensibles qui utilisent la même table de données sensibles. Vous pouvez créer jusqu’à 10 schémas EDM différents dans un locataire Microsoft 365.



## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-wizard"></a>Utiliser l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles

Vous pouvez utiliser cet Assistant pour simplifier le processus de création de fichier de schéma.

## <a name="pre-requisites"></a>Conditions préalables

- Effectuez les étapes [d’exportation des données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type).

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Utiliser l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles

1. Dans le portail de conformité Microsoft Purview de votre locataire, accédez à **Data classificationExact** >  **data matchsEDM** >  **schemas**.

2. Choisissez **Créer un schéma EDM** pour ouvrir le menu volant de configuration de l’Assistant de schéma.

   ![Menu volant de configuration de l’Assistant Création de schéma EDM.](../media/edm-schema-wizard-1.png)

3. Indiquez un nom **approprié** et **Description**.

4. Choisissez **Ignorer les délimiteurs et la ponctuation pour tous les champs de schéma** si vous souhaitez ce comportement pour l’ensemble du schéma. Pour en savoir plus sur la configuration d’EDM pour ignorer la casse ou les délimiteurs, consultez [Utilisation des champs caseInsensitive et ignoredDelimiters](#using-the-caseinsensitive-and-ignoreddelimiters-fields) pour plus d’informations sur cette fonctionnalité.

5. Renseignez les valeurs souhaitées pour votre **Champ de schéma n° 1** et ajoutez des champs si nécessaire. Chaque champ de schéma doit être identique aux en-têtes de colonne dans votre fichier source d’informations sensibles.

6. Si vous le souhaitez, définissez les valeurs par champ pour :
    1. **Champ pouvant faire l’objet d’une recherche**
    1. **Le champ ne respecte pas la casse**
    1. **Choisir des délimiteurs et des signes de ponctuation à ignorer pour ce champ**
    1. **Entrez les délimiteurs personnalisés et la ponctuation pour ce champ**

   > [!IMPORTANT]
   > Au moins un champ, mais pas plus de cinq, doivent être désignés comme pouvant faire l’objet d’une recherche.

7. Cliquez sur **Enregistrer**. Votre schéma est désormais répertorié et disponible pour une utilisation.

   > [!IMPORTANT]
   > Si vous voulez supprimer un schéma et que celui-ci est déjà associé à un type d’informations sensibles EDM, vous devez commencer par supprimer le type d’informations sensibles EDM. Vous pouvez ensuite supprimer le schéma. La suppression d’un schéma associé à un magasin de données supprime également le magasin de données dans les 24 heures.

## <a name="export-of-the-edm-schema-file-in-xml-format"></a>Exportation du fichier de schéma EDM au format XML

Si vous avez créé le schéma EDM dans l’Assistant Schéma EDM, vous devez exporter le fichier de schéma EDM au format XML. Vous en aurez besoin dans le [hachage et chargez la table source d’informations sensibles pour la phase de correspondance exacte des données avec les types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) .

1. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

2. Pour exporter le fichier de schéma EDM, utilisez la syntaxe suivante :

   ```powershell
   $Schema = Get-DlpEdmSchema -Identity "[your EDM Schema name]"
   Set-Content -Path ".\Schemafile.xml" -Value $Schema.EdmSchemaXML
   ```

3. Enregistrez ce fichier pour une utilisation ultérieure.

## <a name="create-exact-data-match-schema-manually-and-upload"></a>Créer manuellement le schéma de correspondance exacte des données et charger

Dans le fichier de schéma, configurez une entrée pour chaque colonne de la table source d’informations sensibles, à l’aide de la syntaxe :

```xml
<Field name="FieldName" searchable="true/false" caseInsensitive="true/false" ignoredDelimiters="delimiter characters" />
```

### <a name="using-the-caseinsensitive-and-ignoreddelimiters-fields"></a>Utilisation des champs caseInsensitive et ignoredDelimiters

L’exemple XML de schéma suivant utilise les champs *caseInsensitive* et *ignoredDelimiters* .

Lorsque vous incluez le champ *caseInsensitive* défini sur la valeur de votre définition de `true` schéma, EDM n’exclut pas un élément en fonction des différences de cas. Par exemple, EDM voit les valeurs **FOO-1234** et **fOo-1234** comme étant identiques pour le `PatientID` champ.

Lorsque vous incluez le champ *ignoredDelimiters avec des* caractères pris en charge, EDM ignore ces caractères. Par conséquent, EDM voit les valeurs **FOO-1234** et **FOO#1234** comme étant identiques pour le `PatienID` champ.

Dans cet exemple, où les deux `caseInsensitive` et `ignoredDelimiters` sont utilisés, EDM voit **FOO-1234** et **fOo#1234** comme identiques et classifie l’élément comme un type d’informations sensibles d’enregistrement de patient.

Ces deux paramètres sont utilisés par champ.

> [!IMPORTANT]
> Si vous configurez des *espaces* à ignorer, cela ne sera efficace que pour les colonnes de champ primaire et pour lesquelles un type d’informations sensibles pouvant détecter des chaînes multi-mots est défini. Sinon, la comparaison sera effectuée par rapport à chaque mot individuel dans le contenu analysé.

*L’indicateur ignoredDelimiters* prend en charge tout caractère non alphanumérique. Voici quelques exemples :

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

> [!IMPORTANT]
> Lors de la définition de votre type d’informations sensibles EDM, *ignoreDelimiters* n’affecte pas la façon dont le type d’informations sensibles classification associé à l’élément principal dans un modèle EDM identifie le contenu d’un élément. Par conséquent, si vous configurez *ignoreDelimiters* pour un champ pouvant faire l’objet d’une recherche, vous devez vous assurer que le type d’informations sensibles utilisé pour un élément principal basé sur ce champ choisira des chaînes avec et sans ces caractères présents.
>
> Le nombre de colonnes dans votre table source d’informations sensibles et le nombre de champs dans votre schéma doivent correspondre, l’ordre n’a pas d’importance.

1. Définissez le schéma au format XML (comme dans notre exemple ci-dessous). Nommez ce fichier de schéma **edm.xml** et configurez-le de telle sorte que pour chaque colonne de la table source d’informations sensibles, il existe une ligne qui utilise la syntaxe :

      `\<Field name="" searchable=""/\>`.

      - Utilisez les noms de colonne pour les valeurs de *nom de champ*.
      - Utilisez *searchable="true »* pour les champs que vous souhaitez rechercher et les champs principaux jusqu’à un maximum de 5 champs. Au moins un champ doit pouvoir faire l’objet d’une recherche.

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

   Une fois que vous avez créé le fichier de schéma EDM au format XML, vous devez le charger dans le service cloud.

2. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

3. Pour charger le schéma de base de données, exécutez la commande suivante :

      ```powershell
      New-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
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
   > Si vous souhaitez que vos modifications se produisent sans confirmation, n’utilisez `-Confirm:$true` pas à l’étape 3.

> [!NOTE]
> La mise à jour du schéma EDMS avec les ajouts peut prendre de 10 à 60 minutes. Vous devez l’effectuer avant d’exécuter les étapes qui utilisent les ajouts.

## <a name="next-step"></a>Étape suivante

- [Hacher et charger la table de source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)
