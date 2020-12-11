---
title: Découvrez les classificateurs de formation (préversion)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Un classificateur Microsoft 365 pouvant être formé est un outil que vous pouvez former afin de reconnaître différents types de contenu en lui donnant des échantillons positifs et négatifs. Une fois que le classifieur est formé, vous confirmez que ses résultats sont précis. Vous l’utilisez ensuite pour effectuer une recherche dans le contenu de votre organisation et le classifier pour appliquer des étiquettes de rétention ou de sensibilité ou l’inclure dans la protection contre la perte de données (DLP) ou les stratégies de rétention.
ms.openlocfilehash: 77ebefe338f393a916f0a6844b42b16e3d011d49
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49620160"
---
# <a name="learn-about-classifiers-preview"></a>En savoir plus sur les classifieurs (aperçu)

La classification et l’étiquetage du contenu de sorte qu’il puisse être protégé et géré correctement est le point de départ de la discipline de protection des informations. Microsoft 365 propose trois façons de classer le contenu.

## <a name="manually"></a>Manuellement

Cette méthode nécessite un jugement humain et une action. Un administrateur peut utiliser les étiquettes préexistantes et les types d’informations sensibles, ou créer les leurs et les publier. Les utilisateurs et les administrateurs les appliquent au contenu au fur et à mesure qu’ils le rencontrent. Vous pouvez ensuite protéger le contenu et gérer sa destruction.

## <a name="automated-pattern-matching"></a>Correspondance des modèles automatisés

Cette catégorie de mécanismes de classification inclut la recherche de contenu en :

- Mots clés ou valeurs de métadonnées (langage de requête par mot clé).
- Utilisation de modèles d’informations sensibles précédemment identifiés comme des numéros de sécurité sociale, de carte de crédit ou de compte bancaire [(définitions d’entités de type d’informations sensibles)](sensitive-information-type-entity-definitions.md).
- Reconnaissance d’un élément, car il s’agit d’une variante d’un modèle [(impression des doigts de document)](document-fingerprinting.md).
- À l’aide de la présence de chaînes exactes [(correspondance de données exacte)](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md).

Les étiquettes de sensibilité et de rétention peuvent ensuite être appliquées automatiquement pour que le contenu puisse être utilisé dans les stratégies de [protection contre la perte de données](data-loss-prevention-policies.md) et [d’application automatique pour les étiquettes de rétention](apply-retention-labels-automatically.md).

## <a name="classifiers"></a>Classifieurs requêtes

Cette méthode de classification est particulièrement adaptée au contenu qui n’est pas facilement identifiable par les méthodes de correspondance manuelle ou automatisée. Cette méthode de classification consiste davantage à former un classifieur à identifier un élément en fonction de ce qu’il est, et non par les éléments qui se trouvent dans l’élément (critères spéciaux). Un classifieur apprend à identifier un type de contenu en examinant des centaines d’exemples du contenu que vous souhaitez classer. Commencez par alimenter des exemples qui sont tous dans la catégorie. Une fois qu’il les traite, vous les testez en leur donnant une combinaison des exemples de correspondance et de non-correspondance. Le classifieur effectue ensuite des prévisions quant à l’existence d’un élément donné dans la catégorie que vous créez. Vous confirmez ensuite ses résultats, en triant les vrais positifs, les vrais négatifs, les faux positifs et les faux négatifs pour améliorer la précision de ses prévisions. 

Lorsque vous publiez le classifieur, il trie les éléments dans des emplacements tels que SharePoint Online, Exchange et OneDrive, et classifie le contenu. Après avoir publié le classifieur, vous pouvez continuer à le former à l’aide d’un processus de commentaires similaire au processus de formation initial.

### <a name="where-you-can-use-trainable-classifiers"></a>Où vous pouvez utiliser des classifieurs de formation
Les classifieurs intégrés et les classifieurs de formation sont disponibles en tant que condition pour l' [AutoLabel Office avec des étiquettes de sensibilité](apply-sensitivity-label-automatically.md), l' [application automatique des étiquettes de rétention en fonction d’une condition](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) et de [la conformité de la communication](communication-compliance.md). 

Les étiquettes de sensibilité peuvent utiliser des classifieurs comme conditions, voir [appliquer automatiquement une étiquette de sensibilité au contenu](apply-sensitivity-label-automatically.md).

> [!IMPORTANT]
> Les classifieurs fonctionnent uniquement avec des éléments qui ne sont pas chiffrés et qui sont en anglais.

## <a name="types-of-classifiers"></a>Types de classifieurs

- **classifieurs pré-formés** : Microsoft a créé et pré-formé un certain nombre de classifieurs que vous pouvez commencer à utiliser sans les former. Ces classifieurs apparaîtront avec l’état `Ready to use` .
- **classifieurs personnalisés** : Si vous avez des besoins en matière de classification qui s’étendent au-delà de ce que traite les classifieurs préqualifiés, vous pouvez créer et former vos propres classifieurs.

### <a name="pre-trained-classifiers"></a>Classifieurs pré-formés

Microsoft 365 est fourni avec cinq classifieurs prédéfinis :

> [!CAUTION]
> Nous déconfigurons le classificateur de **langue choquante** , car il a produit un nombre élevé de faux positifs. Ne l’utilisez pas et, si vous l’utilisez, vous devez déconnecter vos processus d’entreprise. Nous vous recommandons d’utiliser à la place les classifieurs préqualifiés de **menace**, de **blasphème** et de **harcèlement** .

- **CV**: détecte les éléments qui sont des comptes textuels des qualifications personnelles, éducatives, qualifications professionnelles, expérience professionnelle et autres informations d’identification personnelle d’un demandeur.
- **Code source**: détecte les éléments qui contiennent un ensemble d’instructions et d’instructions écrites dans les 25 principaux langages de programmation informatique utilisés sur GitHub
    - 3.0
    - C
    - C#
    - C++
    - Clojure
    - CoffeeScript
    - Activer
    - Haskell
    - Java
    - JavaScript
    - Privilège
    - MATLAB
    - Objective-C
    - Langage
    - PHP
    - Python
    - R
    - Ruby
    - Scalaire
    - Shell
    - Rapide
    - 6,7
    - Script vim

> [!NOTE]
> Le code source est formé pour détecter si la majorité du texte est du code source. Il ne détecte pas le texte de code source qui est intercalé en texte brut.

- **Harcèlement**: détecte une catégorie spécifique d’éléments de texte de langue choquants liés à un comportement offensant ciblant une ou plusieurs personnes en fonction des caractéristiques suivantes : race, ethnique, religion, origine nationale, sexe, orientation sexuelle, âge, handicap
- **Blasphème**: détecte une catégorie spécifique d’éléments de texte en langue choquante qui contiennent des expressions qui déportent la plupart des utilisateurs
- **Menace**: détecte une catégorie spécifique d’éléments de texte de langue offensant liés aux menaces pour valider la violence ou causer des dommages ou dégâts physiques à une personne ou à une propriété.

Ces éléments apparaissent dans la vue classification des données du **Centre de conformité Microsoft 365**  >  **(aperçu)**  >   avec le statut `Ready to use` .

![classifieurs-classifieurs pré-formés](../media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Veuillez noter que le langage offensant, le harcèlement, le catégoriseur et les classifieurs de menaces ne fonctionnent qu’avec le texte pouvant faire l’objet d’une recherche.  De plus, les normes linguistiques et culturelles changent en permanence, et à la lumière de ces réalités, Microsoft se réserve le droit de mettre à jour ces classifieurs à sa discrétion. Alors que les classifieurs peuvent aider votre organisation à surveiller les autres langues choquantes et autres, les classifieurs ne traitent pas les conséquences de ces langues et ne sont pas destinés à fournir aux seuls moyens de surveillance ou de réponse à l’utilisation de ces langues. Votre organisation, et non Microsoft ou ses filiales, reste responsable de toutes les décisions relatives à la surveillance, à l’application, au blocage, à la suppression et à la rétention de tout contenu identifié par un classificateur pré-formé.

### <a name="custom-classifiers"></a>Classifieurs personnalisés

Lorsque les classifieurs prédéfinis ne répondent pas à vos besoins, vous pouvez créer et former vos propres classifieurs. La création de vos propres tâches est beaucoup plus importante, mais elles seront beaucoup mieux adaptées à vos besoins. 

Par exemple, vous pouvez créer des classifieurs pouvant être formés pour :
 
- Documents légaux, tels que les privilèges du client pour les avocats, les groupes de fermeture, le cahier des charges
- Documents métiers stratégiques : Communiqués de presse, fusions et acquisitions, offres commerciales, plans d’entreprise ou marketing, droits de propriété intellectuelle, brevets, docs de conception
- Informations de tarification, telles que les factures, les prix, les ordres de travail, les documents d’enchères 
- Informations financières, telles que les investissements organisationnels, les résultats trimestriels ou annuels    

#### <a name="process-flow-for-creating-custom-classifiers"></a>Flux de processus pour la création de classifieurs personnalisés

La création et la publication d’un classifieur à utiliser dans les solutions de conformité, telles que les stratégies de rétention et la surveillance des communications, suivent ce flux. Pour plus d’informations sur la création d’un classificateur de formation personnalisée, consultez [la rubrique Création d’un classifieur personnalisé](classifier-get-started-with.md).

![classifieur personnalisé de flux de processus](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Recyclage des classifieurs

Vous pouvez améliorer la précision de tous les classifieurs personnalisés et de certains classifieurs prédéfinis en leur fournissant des commentaires sur la précision de la classification qu’ils effectuent. Cette méthode est appelée « reformation » et suit ce flux de travail.

![flux de travail de recyclage de classifieur](../media/classifier-retraining-workflow.png)

## <a name="see-also"></a>Voir aussi

- [Étiquettes de rétention](retention.md)
- [Protection contre la perte de données (DLP)](data-loss-prevention-policies.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Impression des doigts de document](document-fingerprinting.md)
- [Correspondance exacte des données](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)
