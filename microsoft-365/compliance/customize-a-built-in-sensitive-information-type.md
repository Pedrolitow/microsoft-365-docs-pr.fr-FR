---
title: Personnaliser un type d’informations sensibles intégré
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment créer un type d’informations sensibles personnalisé qui vous permettra d’utiliser des règles répondant aux besoins de votre organisation.
ms.openlocfilehash: 14fb645a4b7f58f609995bc71edae24090c83cc7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630982"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>Personnaliser un type d’informations sensibles intégré

Lorsque vous recherchez des informations de contenu sensible vous devez décrire ces informations dans ce que l'on appelle une *règle*. La protection contre la perte de données Microsoft Purview (DLP) comprend des règles pour les types d'informations sensibles les plus courants que vous pouvez utiliser immédiatement. Pour utiliser ces règles, vous devez les inclure dans une stratégie. Vous voudrez peut-être ajuster ces règles intégrées pour répondre aux besoins spécifiques de votre organisation, et vous pouvez le faire en créant un type d'informations sensibles personnalisé. Cette rubrique vous montre comment personnaliser le fichier XML qui contient la collection de règles existante pour détecter un plus large éventail d'informations potentielles relatives aux cartes de crédit.

Vous pouvez prendre cet exemple et l’appliquer à d’autres types d’informations sensibles intégrés. Pour obtenir la liste des types d’informations sensibles par défaut et des définitions XML, voir [Définitions des entités de type information sensible](sensitive-information-type-entity-definitions.md).

## <a name="export-the-xml-file-of-the-current-rules"></a>Exporter le fichier XML des règles actuelles

Pour exporter le code XML, vous devez vous [connecter au PowerShell de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

1. Dans PowerShell, saisissez la commande suivante pour afficher les règles de votre organisation à l’écran. Si vous n’avez pas créé votre propre règle, vous ne verrez que les règles intégrées par défaut, sous le libellé « Package de règles Microsoft ».

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. Stockez les règles de votre organisation dans une variable en tapant ce qui suit. Le stockage d’un élément dans une variable le rend facilement disponible ultérieurement dans un format qui fonctionne pour les commandes PowerShell.

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. Créez un fichier XML formaté avec toutes ces données en tapant ce qui suit.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > Assurez-vous que vous utilisez l’emplacement de fichier dans lequel votre pack de règles est effectivement stocké. `C:\custompath\` est un espace réservé.

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>Rechercher la règle à modifier dans le fichier XML

Les cmdlets ci-dessus ont exporté l’ensemble de la *collection de règles* qui inclut les règles par défaut que nous fournissons. Ensuite, vous devez rechercher la règle de numéro de carte de crédit spécifique à modifier.

1. Utilisez un éditeur de texte pour ouvrir le fichier XML que vous avez exporté dans la section précédente.

2. Faites défiler l’écran jusqu’à la balise `<Rules>`, qui constitue le début de la section contenant les règles DLP. En effet, ce fichier XML contenant les informations de toute la collection de règles, il contient d’autres informations dans la partie supérieure que vous devez faire défiler pour accéder aux règles.

3. Recherchez *Func_credit_card* pour trouver la définition de règle de numéro de carte de crédit. En code XML, les noms des règles ne peuvent pas contenir d’espaces. Ces derniers sont donc généralement remplacés par le tiret du bas et les noms des règles sont parfois abrégés. Par exemple, la règle du Social Security number (numéro de sécurité sociale aux États-Unis) est abrégée en _SSN_. Le code XML de la règle de numéro de carte de crédit doit ressembler à l’exemple de code suivant.

   ```xml
   <Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085"
          patternsProximity="300" recommendedConfidence="85">
         <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_credit_card" />
           <Any minMatches="1">
             <Match idRef="Keyword_cc_verification" />
             <Match idRef="Keyword_cc_name" />
             <Match idRef="Func_expiration_date" />
           </Any>
         </Pattern>
       </Entity>
   ```

Maintenant que vous avez localisé la définition de règle de numéro de carte de crédit dans le XML, vous pouvez personnaliser le code XML de la règle en fonction de vos besoins. Pour un rappel des définitions XML, voir [Glossaire terminologique](#term-glossary) à la fin de cette rubrique.

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>Modifier le XML et créer un type d’informations sensibles

Tout d'abord, vous devez créer un type d'informations sensibles, car vous ne pouvez pas modifier directement les règles par défaut. Vous pouvez effectuer un large éventail de tâches avec des types d’informations sensibles personnalisés, qui sont décrits dans [Créer un type d’informations sensibles personnalisé dans le PowerShell de sécurité et conformité](create-a-custom-sensitive-information-type-in-scc-powershell.md). Pour cet exemple, nous allons rester simples et nous contenter de supprimer les preuves crédibles et d'ajouter des mots clés à la règle de numéro de carte de crédit.

Toutes les définitions de règle XML sont construites sur le modèle général suivant. Vous devez copier et coller le XML de définition de numéro de carte de crédit dans le modèle, modifier certaines valeurs (remarquez les espaces réservés « . . ." dans l'exemple suivant), puis télécharger le XML modifié en tant que nouvelle règle pouvant être utilisée dans des stratégies.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id=". . .">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id=". . ." />
    <Details defaultLangCode=". . .">
      <LocalizedDetails langcode=" . . . ">
         <PublisherName>. . .</PublisherName>
         <Name>. . .</Name>
         <Description>. . .</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
   <!-- Paste the Credit Card Number rule definition here.-->
      <LocalizedStrings>
         <Resource idRef=". . .">
           <Name default="true" langcode=" . . . ">. . .</Name>
           <Description default="true" langcode=". . ."> . . .</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

Vous obtenez maintenant quelque chose qui ressemble au XML suivant. Étant donné que les packages de règles et les règles sont identifiés par leur GUID unique, vous devez générer deux GUID : un pour le package de règles et un pour remplacer le GUID de la règle de numéro de carte de crédit. Le GUID pour l’ID d’entité dans l’exemple de code suivant est celui de la définition de notre règle intégrée, que vous devez remplacer. Il existe plusieurs façons de générer des GUID, mais vous pouvez le faire facilement dans PowerShell en saisissant **[guid]::NewGuid()**.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id="8aac8390-e99f-4487-8d16-7f0cdee8defc">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="8d34806e-cd65-4178-ba0e-5d7d712e5b66" />
    <Details defaultLangCode="en">
      <LocalizedDetails langcode="en">
        <PublisherName>Contoso Ltd.</PublisherName>
        <Name>Financial Information</Name>
        <Description>Modified versions of the Microsoft rule package</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f"
       patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
      <LocalizedStrings>
         <Resource idRef="db80b3da-0056-436e-b0ca-1f4cf7080d1f">
<!-- This is the GUID for the preceding Credit Card Number entity because the following text is for that Entity. -->
           <Name default="true" langcode="en-us">Modified Credit Card Number</Name>
           <Description default="true" langcode="en-us">Credit Card Number that looks for additional keywords, and another version of Credit Card Number that doesn't require keywords (but has a lower confidence level)</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>Supprimer l’exigence de preuve crédible d’un type d’informations sensibles

À présent que vous disposez d’un nouveau type d’informations sensibles que vous pouvez charger vers le Portail de conformité Microsoft Purview et de la prochaine étape consiste à rendre la règle plus spécifique. Modifiez la règle de sorte qu’elle recherche uniquement un nombre à 16 chiffres qui passe la somme de contrôle, mais qu’elle ne nécessite pas de preuve (corroborante) supplémentaire comme des mots clés. Pour ce faire, vous devez retirer la partie du XML qui recherche la preuve corroborante. Les preuves corroborantes sont très utiles pour réduire les faux positifs. En l’occurrence, des mots clés ou une date d’expiration figurent généralement à proximité du numéro de carte de crédit. Si vous supprimez cette preuve, vous devez également ajuster votre niveau de confiance par rapport au fait que vous avez trouvé un numéro de carte de crédit en abaissant la valeur du paramètre `confidenceLevel` qui est définie sur 85 dans l’exemple.

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>Rechercher des mots clés propres à votre organisation

Vous voulez peut-être exiger des preuves crédibles, mais aussi des mots clés différents ou supplémentaires, et vous voulez aussi peut-être modifier l’endroit où rechercher ces preuves. Vous pouvez ajuster le paramètre `patternsProximity` afin de développer ou réduire la fenêtre pour la preuve probante autour du numéro à 16 chiffres. Pour ajouter vos propres mots clés, vous devez définir une liste de mots clés et la référencer dans votre règle. Le XML suivant ajoute les mots clés « company card » et « Contoso card » de sorte que tous les messages qui contiennent ces expressions au sein des 150 caractères d’un numéro de carte de crédit soient identifiés comme des numéros de carte de crédit.

```xml
<Rules>
<! -- Modify the patternsProximity to be "150" rather than "300." -->
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="150" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
<!-- Add the following XML, which references the keywords at the end of the XML sample. -->
          <Match idRef="My_Additional_Keywords" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
<!-- Add the following XML, and update the information inside the <Term> tags with the keywords that you want to detect. -->
    <Keyword id="My_Additional_Keywords">
      <Group matchStyle="word">
        <Term caseSensitive="false">company card</Term>
        <Term caseSensitive="false">Contoso card</Term>
      </Group>
    </Keyword>
```

## <a name="upload-your-rule"></a>Télécharger votre règle

Pour télécharger votre règle, vous devez procéder comme suit.

1. Enregistrez-la en tant que fichier .xml avec le codage Unicode. Ceci est important car la règle ne fonctionne pas si le fichier est enregistré dans un codage différent.

2. [Se connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

3. Dans PowerShell, saisissez la commande suivante.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > Assurez-vous que vous utilisez l’emplacement de fichier dans lequel votre pack de règles est effectivement stocké. `C:\custompath\` est un espace réservé.

4. Pour confirmer, saisissez Y, puis appuyez sur **Entrée**.

5. Vérifiez que votre nouvelle règle a été chargée et que son nom s’affiche en tapant la commande suivante :

   ```powershell
   Get-DlpSensitiveInformationType
   ```

Pour commencer à utiliser la nouvelle règle afin de détecter des informations sensibles, vous devez l’ajouter à une stratégie DLP. Pour découvrir comment ajouter la règle à une stratégie, consultez l’article [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md).

## <a name="term-glossary"></a>Glossaire terminologique

Voici les définitions des termes que vous avez rencontrés au cours de cette procédure.

<br>

****

|Terme|Définition|
|---|---|
|Entity|Les entités sont ce que nous appelons des types d'informations sensibles, comme les numéros de carte de crédit. Chaque entité possède un GUID unique qui constitue son ID. Si vous copiez un GUID et que vous le recherchez dans le XML, vous trouvez la définition de règle XML, ainsi que toutes les traductions localisées de cette règle XML. Vous pouvez également trouver cette définition en localisant le GUID de la traduction, puis en recherchant ce GUID.|
|Fonctions|Le fichier XML fait référence à `Func_credit_card`, qui est une fonction dans le code compilé. Les fonctions sont utilisées pour exécuter des expressions régulières complexes et vérifier que les sommes de contrôle correspondent avec nos règles intégrées). Comme cela se passe dans le code, certaines des variables n'apparaissent pas dans le fichier XML.|
|IdMatch|Il s’agit de l’identificateur auquel le modèle tente de correspondre, par exemple un numéro de carte de crédit.|
|Listes de mots clés|Le fichier XML fait également référence à `keyword_cc_verification` et à `keyword_cc_name`, qui sont des listes de mots clés dans lesquelles nous recherchons des correspondances à l'intérieur du paramètre `patternsProximity` pour l'entité. Ces éléments ne sont actuellement pas affichés dans le fichier XML.|
|Modèle|Le modèle contient la liste de ce que le type sensible recherche. Cela inclut des mots clés, des expressions régulières et des fonctions internes, qui effectuent des tâches telles que la vérification des sommes de contrôle. Ces types d’informations sensibles peuvent avoir plusieurs modèles avec des niveaux de confiance uniques. Ceci est utile lors de la création d’un type d’informations sensibles qui renvoie un niveau de confiance élevé si des preuves crédibles sont trouvées et un niveau de confiance faible dans le cas contraire.|
|confidenceLevel|Il s’agit du niveau de confiance appliqué lorsque le moteur DLP trouve une correspondance. Ce niveau de confiance est associé à une correspondance pour le modèle si les exigences du modèle sont remplies. C’est la mesure de confiance à prendre en considération lorsque vous utilisez des règles de flux de messagerie Exchange (également appelées règles de transport).|
|patternsProximity|Lorsque nous trouvons ce qui ressemble à un modèle de numéro de carte de crédit, `patternsProximity` correspond à la proximité de recherche de preuves corroborantes autour de ce numéro.|
|recommendedConfidence|Il s’agit du niveau de confiance que nous recommandons pour cette règle. Le niveau de confiance recommandé s’applique aux entités et aux affinités. Pour les entités, ce nombre n’est jamais évalué par rapport au paramètre `confidenceLevel` pour le modèle. Il s’agit d’une simple suggestion pour vous aider à choisir un niveau de confiance, si vous voulez en appliquer un. Pour les affinités, le paramètre `confidenceLevel` du modèle doit être supérieur au nombre `recommendedConfidence` pour une action de règle de flux de messagerie à appeler. Le paramètre `recommendedConfidence` correspond au niveau de confiance par défaut utilisé dans les règles de flux de messagerie qui appelle une action. Si vous le souhaitez, vous pouvez modifier manuellement la règle de flux de courrier pour qu'il soit invoqué en fonction du niveau de confiance du modèle.|
|

## <a name="for-more-information"></a>Pour plus d'informations

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md)
- [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)
