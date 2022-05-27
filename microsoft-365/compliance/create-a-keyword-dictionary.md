---
title: Créer un dictionnaire de mots clés
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
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Découvrez les étapes principales de la création d’un dictionnaire de mots clés dans le Centre de sécurité et conformité Office 365.
ms.openlocfilehash: ceb410d09d9869d87681128f2c6e7b45cd8363cb
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753669"
---
# <a name="create-a-keyword-dictionary"></a>Créer un dictionnaire de mots clés

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

La Protection contre la perte de données Microsoft Purview peut identifier, surveiller et protéger vos éléments sensibles. L’identification des éléments sensibles nécessite parfois la recherche de mots clés, en particulier lors de l’identification d’un contenu générique (comme une communication liée à la santé) ou d’un langage inapproprié ou explicite. Bien que vous puissiez créer des listes de mots clés dans des types d’informations sensibles, ces listes sont de taille limitée et nécessitent la modification du XML pour les créer ou les modifier. Les dictionnaires de mots clés facilitent la gestion des mots clés à une échelle beaucoup plus grande, en prenant en charge jusqu’à 1 Mo de termes (après compression) dans le dictionnaire. De plus, toutes les langues sont prises en charge. La limite du client est également de 1 Mo après compression. 1 Mo de limite après compression signifie que tous les dictionnaires combinés dans un client peuvent avoir près de 1 million de caractères.

## <a name="keyword-dictionary-limits"></a>Limites du dictionnaire de mots clés

Il existe une limite de 50 types d’informations sensibles basés sur un dictionnaire de mots clés que vous pouvez créer par client. Pour connaître le nombre de dictionnaires de mots clés de votre client, connectez-vous à l’aide des procédures de la section [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell) pour vous connecter à votre client et exécutez ce script PowerShell.

```powershell
$rawFile = $env:TEMP + "\rule.xml"

$kd = Get-DlpKeywordDictionary
$ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
[System.IO.File]::WriteAllBytes((Resolve-Path $rawFile), $ruleCollections.SerializedClassificationRuleCollection)
$UnicodeEncoding = New-Object System.Text.UnicodeEncoding
$FileContent = [System.IO.File]::ReadAllText((Resolve-Path $rawFile), $unicodeEncoding)

if($kd.Count -gt 0)
{
$count = 0
$entities = $FileContent -split "Entity id"
for($j=1;$j -lt $entities.Count;$j++)
{
for($i=0;$i -lt $kd.Count;$i++)
{
$Matches = Select-String -InputObject $entities[$j] -Pattern $kd[$i].Identity -AllMatches
$count = $Matches.Matches.Count + $count
if($Matches.Matches.Count -gt 0) {break}
}
}

Write-Output "Total Keyword Dictionary SIT:"
$count
}
else
{
$Matches = Select-String -InputObject $FileContent -Pattern $kd.Identity -AllMatches
Write-Output "Total Keyword Dictionary SIT:"
$Matches.Matches.Count
}

Remove-Item $rawFile
```

## <a name="basic-steps-to-creating-a-keyword-dictionary"></a>Étapes de base de la création d’un dictionnaire de mots clés

Les mots clés de votre dictionnaire peuvent provenir de diverses sources, le plus souvent d’un fichier (par exemple, une liste .csv ou .txt) importé dans le service ou par cmdlet PowerShell, depuis une liste à laquelle vous accédez directement dans la cmdlet PowerShell ou depuis un dictionnaire existant. Lorsque vous créez un dictionnaire de mots clés, vous suivez les mêmes étapes fondamentales :

1. Utilisez le *<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Portail de conformité Microsoft Purview</a> ou connectez-vous au **Portail de conformité Microsoft Purview PowerShell**.

2. **Définissez ou chargez vos mots clés à partir de la source prévue**. L’Assistant et la cmdlet acceptent tous deux une liste de mots clés séparés par des virgules pour la création d’un dictionnaire de mots clés personnalisé. Cette étape varie donc légèrement en fonction de l’origine de vos mots clés. Une fois chargés, ils sont codés et convertis en tableau d’octets avant leur importation.

3. **Créez votre dictionnaire** : Choisissez un nom et une description, puis créez votre dictionnaire.

## <a name="create-a-keyword-dictionary-using-the-security--compliance-center"></a>Créer un dictionnaire de mots clés avec le Centre de sécurité et de conformité

Procédez comme suit pour créer et importer des mots clés pour un dictionnaire personnalisé :

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Portail de conformité Microsoft Purview</a>.

2. Accédez à **Classifications > Types d’informations sensibles**.

3. Sélectionnez **Créer** et entrez un **Nom** et une **Description** pour votre type d’informations sensibles, puis sélectionnez **Suivant**

4. Sélectionnez **Ajouter un élément**, puis sélectionnez **Dictionnaire (grands mots clés)** dans la liste déroulante **Détecter le contenu contenant**.

5. Sélectionnez **Ajouter un dictionnaire**

6. Sous le Contrôle de recherche, sélectionnez **Vous pouvez créer de nouveaux dictionnaires de mots clés ici**.

7. Entrez un **Nom** pour votre dictionnaire personnalisé.

8. Sélectionnez **Importer**, puis sélectionnez **À partir d’un fichier texte** ou **À partir d’un fichier CSV** selon votre type de fichier de mots clés.

9. Dans la boîte de dialogue du fichier, sélectionnez le fichier de mots clés sur votre PC local ou sur votre partage de fichiers réseau, puis sélectionnez **Ouvrir**.

10. Sélectionnez **Enregistrer**, puis sélectionnez votre dictionnaire personnalisé dans la liste **Dictionnaires de mots clés**.

11. Sélectionnez **Ajouter**, puis **Suivant**.

12. Passez en revue et finalisez vos sélections de type d’informations sensibles, puis sélectionnez **Terminer**.

## <a name="create-a-keyword-dictionary-from-a-file-using-powershell"></a>Création d’un dictionnaire de mots clés à partir d’un fichier avec PowerShell

Lorsque vous avez besoin de créer un dictionnaire volumineux, c’est souvent pour utiliser des mots clés d’un fichier ou d’une liste exportée à partir d’une autre source. Dans ce cas, créez un dictionnaire de mots clés contenant une liste de termes inappropriés à rechercher dans les e-mails externes. Vous devez d’abord vous [connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

1. Copiez les mots clés dans un fichier texte et assurez-vous que chaque mot clé est sur une ligne distincte.

2. Enregistrez le fichier texte avec le codage Unicode. Dans le Bloc-notes \> **Enregistrer sous** \> **Codage** \> **Unicode**.

3. Lisez le fichier dans une variable en exécutant la cmdlet suivante :

    ```powershell
    $fileData = [System.IO.File]::ReadAllBytes('<filename>')
    ```

4. Créez le dictionnaire en exécutant la cmdlet suivante :

    ```powershell
    New-DlpKeywordDictionary -Name <name> -Description <description> -FileData $fileData
    ```

## <a name="using-keyword-dictionaries-in-custom-sensitive-information-types-and-dlp-policies"></a>Utilisation des dictionnaires de mots clés dans les types d’informations sensibles personnalisés et les stratégies DLP

Les dictionnaires de mots clés peuvent être utilisés dans le cadre de la configuration requise de recherche pour un type personnalisé d’informations sensibles ou en tant que type d’informations sensibles eux-mêmes. Les deux cas nécessitent que vous créez un [type personnalisé d’informations sensibles](create-a-custom-sensitive-information-type-in-scc-powershell.md). Suivez les instructions dans l’article lié pour créer un type d’informations sensibles. Une fois que vous avez le fichier XML, vous aurez besoin de l’identificateur GUID du dictionnaire pour utiliser ce dernier.

```xml
<Entity id="9e5382d0-1b6a-42fd-820e-44e0d3b15b6e" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef=". . ."/>
    </Pattern>
</Entity>
```

Pour obtenir l’identité de votre dictionnaire, exécutez la commande suivante et copiez la valeur de la propriété **Identité** :

```powershell
Get-DlpKeywordDictionary -Name "Diseases"
```

Le résultat de la commande ressemble à ceci :

`RunspaceId        : 138e55e7-ea1e-4f7a-b824-79f2c4252255`
`Identity          : 8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f`
`Name              : Diseases`
`Description       : Names of diseases and injuries from ICD-10-CM lexicon`
`KeywordDictionary : aarskog's syndrome, abandonment, abasia, abderhalden-kaufmann-lignac, abdominalgia, abduction contracture, abetalipo` `proteinemia, abiotrophy, ablatio, ablation, ablepharia, abocclusion, abolition, aborter, abortion, abortus, aboulomania,`
                    `abrami's disease, abramo`
`IsValid           : True`
`ObjectState       : Unchanged`

Collez l’identité dans le code XML de votre type personnalisé d’informations sensibles et chargez-le. Votre dictionnaire s’affiche désormais dans votre liste de types d’informations sensibles et vous pouvez l’utiliser directement dans votre stratégie en indiquant le nombre de mots clés qui doivent correspondre.

```xml
<Entity id="d333c6c2-5f4c-4131-9433-db3ef72a89e8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f" />
      </Pattern>
    </Entity>
    <LocalizedStrings>
      <Resource idRef="d333c6c2-5f4c-4131-9433-db3ef72a89e8">
        <Name default="true" langcode="en-us">Diseases</Name>
        <Description default="true" langcode="en-us">Detects various diseases</Description>
      </Resource>
    </LocalizedStrings>
```

> [!NOTE]
> Microsoft 365 Information Protection prend en charge les langues de jeux de caractères à double octets pour :
>
> - Chinois (simplifié)
> - Chinois (traditionnel)
> - Korean
> - Japanese
>
> Cette prise en charge est disponible pour les types d’informations sensibles. Si vous souhaitez en savoir plus, consultez l’article [Prise en charge de la protection des informations pour les jeux de caractères à double octets (préversion)](mip-dbcs-relnotes.md).

> [!TIP]
> Pour détecter les modèles contenant des caractères chinois/japonais et des caractères d’octet unique ou pour détecter les modèles contenant du chinois/le japonais et l’anglais, définissez deux variantes du mot clé ou de regex.
>
> - Par exemple, pour détecter un mot clé tel que « 机密的document », utilisez deux variantes du mot clé ; l’un avec un espace entre le texte japonais et anglais et l’autre sans espace entre le texte japonais et l’anglais. Par conséquent, les mots clés à ajouter dans le SIT doivent être « 机密的 document » et « 机密的document ». De la même façon, pour détecter une expression « 東京オリンピック2020 », deux variantes doivent être utilisées : « 東京オリンピック 2020 » et « 東京オリンピック2020 ».
>
> En plus des caractères chinois/japonais/caractères sur deux octets, si la liste des mots clés/expressions contient également des mots non chinois/japonais (comme l’anglais uniquement), il est recommandé de créer deux dictionnaires/listes de mots clés. Un pour les mots clés contenant des caractères chinois/japonais/sur deux octets et un autre pour l’anglais uniquement.
>
> - Par exemple, si vous souhaitez créer un dictionnaire/liste de mots clés avec trois phrases « Hautement confidentiel », « 機密性が高い » et « document 机密的 », vous devez créer deux listes de mots clés.
>   1. Extrêmement confidentiel
>   2. Document 機密性が高い, 机密的 et document 机密的
>
> Lorsque vous créez une regex en utilisant un trait d'union à double octet ou un point à double octet, assurez-vous d'échapper les deux caractères comme on le ferait pour un trait d'union ou un point dans une regex. Voici un exemple regex pour référence :
>
> - `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4}`
>
> Nous vous recommandons d’utiliser une correspondance de chaîne au lieu d’une correspondance de mot dans une liste de mots clés.
