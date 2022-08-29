---
title: Modifier le schéma de correspondance des données exactes pour utiliser la correspondance configurable
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment modifier un schéma EDM pour utiliser une correspondance configurable.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 107a910068f3f0dfbae56530c5b589e19e0d2621
ms.sourcegitcommit: 7374c7b013890744d74e5214f7f8d69ca7874466
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2022
ms.locfileid: "67405639"
---
# <a name="modify-exact-data-match-schema-to-use-configurable-match"></a>Modifier le schéma de correspondance des données exactes pour utiliser la correspondance configurable

## <a name="applies-to"></a>S’applique à

- Création de type d’informations sensibles (SIT) de correspondance de données exactes (EDM) à l’aide de PowerShell.

La classification EDM (Exact Data Match) vous permet de créer des types d’informations sensibles personnalisés qui font référence à des valeurs exactes dans une base de données d’informations sensibles. Lorsque vous devez autoriser des variantes d’une chaîne exacte, vous pouvez utiliser la *correspondance configurable* pour indiquer à Microsoft Purview d’ignorer la casse et certains délimiteurs.

> [!IMPORTANT]
> Utilisez cette procédure pour modifier un schéma EDM et un fichier de données existants.

1. Désinstallez **EdmUploadAgent.exe** de l’ordinateur que vous utilisez pour vous connecter à Microsoft 365 afin de charger les fichiers de données et le modèle EDM.

2. Téléchargez le fichier **EdmUploadAgent.exe** approprié pour votre abonnement en utilisant les liens ci-dessous :
    - [Commercial + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) : pour la plupart des clients commerciaux
    - [GCC-High](https://go.microsoft.com/fwlink/?linkid=2137521) : conçu spécifiquement pour les abonnés cloud du secteur public haute sécurité
    - [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) : conçu spécifiquement pour les clients cloud du Department of Defense américain

3. Autorisez l’agent Télécharger EDM, ouvrez une fenêtre d’invite de commandes (en tant qu’administrateur) et exécutez la commande suivante :

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

4. Si vous n’avez pas de copie actuelle du schéma existant, vous devez en télécharger une. Exécutez la commande suivante :

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <dataStoreName> [/OutputDir [Output dir location]]
   ```

5. Personnalisez le schéma de sorte que chaque colonne utilise « caseInsensitive » et/ou « ignoredDelimiters ».  La valeur par défaut de « caseInsensitive » est « false » et « ignoredDelimiters » est une chaîne vide.

    > [!NOTE]
    > Le type d’informations sensibles personnalisé sous-jacent ou le type d’informations sensibles intégré utilisé pour détecter le modèle regex général doivent prendre en charge la détection des entrées de variantes indiquées avec ignoredDelimiters. Par exemple, le type d’informations sensibles intégré Numéro de sécurité sociale (SSN) américain permet de détecter les variantes des données qui incluent des tirets, des espaces ou une absence d’espace entre les numéros groupés qui composent le numéro de sécurité sociale. Par conséquent, les seuls délimiteurs pertinents à inclure dans ignoredDelimiters EDM pour les données SSN sont : les tirets et les espaces.

    Voici un exemple de schéma qui simule la correspondance non sensible à la casse en créant les colonnes supplémentaires nécessaires pour identifier les variations de casse dans les données sensibles.

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
               <Field name="PolicyNumber" searchable="true" />
               <Field name="PolicyNumberLowerCase" searchable="true" />
               <Field name="PolicyNumberUpperCase" searchable="true" />
               <Field name="PolicyNumberCapitalLetters" searchable="true" />
      </DataStore>
    </EdmSchema>
    ```

    Dans l’exemple ci-dessus, les variantes de la colonne d’origine `PolicyNumber` ne sont plus nécessaires si `caseInsensitive` et `ignoredDelimiters` sont ajoutés.

    Pour mettre à jour ce schéma de façon à ce qu’EDM utilise la correspondance configurable, utilisez les indicateurs `caseInsensitive` et `ignoredDelimiters`. Voici à quoi cela ressemble :

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
             <Field name="PolicyNumber" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
      </DataStore>
    </EdmSchema>
    ```

    L’indicateur `ignoredDelimiters` prend en charge tous les caractères non alphanumériques. Voici quelques exemples :
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

6. [Se connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

    > [!NOTE]
    > Si votre organisation a configuré une [Clé client pour Microsoft 365 au niveau du client (préversion publique)](customer-key-tenant-level.md#overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview), la correspondance exacte des données utilisera automatiquement sa fonctionnalité de chiffrement. Elle est disponible pour les clients sous licence E5 uniquement dans le cloud commercial.

7. Mettez à jour votre schéma en exécutant la commande suivante :

   ```powershell
   Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
   ```

8. Si nécessaire, mettez à jour le fichier de données pour qu’il corresponde à la nouvelle version du schéma.

    > [!TIP]
    > Si vous le souhaitez, vous pouvez exécuter une validation par rapport à votre fichier CSV avant de charger en exécutant :
    >
    > `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
    >
    > Par exemple : `EdmUploadAgent.exe /ValidateData /DataFile  C:\data\testdelimiters.csv /Schema C:\EDM\patientrecords.xml`
    >
    > Pour plus d’informations sur tous les EdmUploadAgent.exe pris en charge, exécutez
    >
    > `EdmUploadAgent.exe /?`

9. Ouvrez la fenêtre Invite de commandes (en tant qu’administrateur), puis exécutez la commande suivante pour hacher et charger vos données sensibles :

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Salt [custom salt] /Schema [Schema file]
   ```

## <a name="related-articles"></a>Articles connexes

- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Types d’informations sensibles personnalisés](./sensitive-information-type-learn-about.md)
- [En savoir plus sur la protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security)
- [New-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
