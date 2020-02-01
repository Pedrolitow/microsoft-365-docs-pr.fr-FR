---
title: Prise en main des classificateurs de formation (préversion)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Un classificateur Microsoft 365 pouvant être formé est un outil que vous pouvez former afin de reconnaître différents types de contenu en lui donnant des échantillons positifs et négatifs. Une fois que le classifieur est formé, vous confirmez que ses résultats sont précis. Vous l’utilisez ensuite pour effectuer une recherche dans le contenu de votre organisation et le classifier pour appliquer des étiquettes de rétention ou de sensibilité ou l’inclure dans la protection contre la perte de données (DLP) ou les stratégies de rétention.
ms.openlocfilehash: 4b4bfa996b1f68f9db8c206aaaec43878abf3f42
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41595901"
---
# <a name="getting-started-with-trainable-classifiers-preview"></a>Prise en main des classificateurs de formation (préversion)

La classification et l’étiquetage du contenu de sorte qu’il puisse être protégé et géré correctement est le point de départ de la discipline de protection des informations. Microsoft 365 propose trois façons de classer le contenu.

## <a name="manually"></a>Manuellement

Cette méthode nécessite un jugement humain et une action. Un administrateur peut utiliser les étiquettes préexistantes et les types d’informations sensibles, ou créer les leurs et les publier. Les utilisateurs et les administrateurs les appliquent au contenu au fur et à mesure qu’ils le rencontrent. Vous pouvez ensuite protéger le contenu et gérer sa destruction.

## <a name="automated-pattern-matching"></a>Correspondance des modèles automatisés

Cette catégorie de mécanismes de classification inclut la recherche de contenu en :

- Mots clés ou valeurs de métadonnées (langage de requête par mot clé)
- utilisation de modèles d’informations sensibles précédemment identifiés comme des numéros de sécurité sociale, de carte bancaire ou de compte bancaire [(types d’informations sensibles)](what-the-sensitive-information-types-look-for.md)
- Reconnaissance d’un élément car il s’agit d’une variante d’un modèle [(impression des doigts de document)](document-fingerprinting.md)
- à l’aide de la présence de chaînes exactes [(correspondance de données exacte)](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md).

Les étiquettes de sensibilité et de rétention peuvent ensuite être appliquées automatiquement pour que le contenu soit disponible dans la [protection contre la perte de données (DLP)](data-loss-prevention-policies.md) et les [stratégies de rétention](retention-policies.md).

## <a name="trainable-classifiers"></a>Classifieurs de formation

Cette méthode de classification est particulièrement adaptée au contenu qui n’est pas facilement identifiable par les méthodes de correspondance manuelle ou automatisée. Cette méthode de classification est plus relative à la formation d’un classifieur permettant d’identifier un élément en fonction de ce que est l’élément, pas par les éléments qui se trouvent dans l’élément (critères spéciaux). Un classifieur apprend à identifier un type de contenu en examinant des centaines d’exemples du contenu que vous souhaitez classer. Commencez par alimenter des exemples qui sont tous dans la catégorie. Une fois qu’il les traite, vous les testez en leur donnant une combinaison des exemples de correspondance et de non-correspondance. Le classifieur effectue ensuite des prévisions quant à l’existence d’un élément donné dans la catégorie que vous créez. Ensuite, vérifiez ses résultats, en triant les positifs, les négatifs, les faux positifs et les faux négatifs pour améliorer la précision de ses prévisions. Lorsque vous publiez le classifieur formé, il trie les éléments dans des emplacements comme SharePoint Online, Exchange et OneDrive, et classifie le contenu.

> [!IMPORTANT]
> Les deux types de classifieurs sont disponibles en tant que condition pour la [stratégie d’étiquette de rétention automatique basée sur une condition et une](labels.md#applying-a-retention-label-automatically-based-on-conditions) conformité de [communication](communication-compliance.md).

> [!IMPORTANT]
> Les classifieurs pouvant être formés ne fonctionnent qu’avec des éléments qui ne sont pas chiffrés et qui sont en anglais.

## <a name="types-of-classifiers"></a>Types de classifieurs

Il est prêt à utiliser des classifieurs et des classifieurs de formation. L’obtention d’un classificateur de formation à un État publiable nécessite un investissement de temps pour le former. Pour vous aider à commencer à utiliser les classifieurs, Microsoft 365 est fourni avec quelques classifieurs prêts à l’emploi.

> [!NOTE]
> Avant d’utiliser un classificateur prêt à utiliser dans votre classification et votre flux de travail d’étiquetage, vous devez le tester par rapport à un exemple de votre contenu d’organisation correspondant à la catégorie afin de vérifier que ses prévisions de classification répondent à vos attentes.

### <a name="understanding-ready-to-use-classifiers"></a>Présentation des classifieurs prêts à l’emploi

Microsoft 365 est fourni avec six classifieurs prêts à l’emploi suivants :

- **Offensant**: détecte les éléments de texte qui contiennent des blasphèmes, Slurs, taunts et des expressions déguisées (qui sont des expressions qui ont la même signification qu’un terme plus offensant).
- **CV**: détecte les éléments qui sont des comptes textuels des qualifications personnelles, éducatives, professionnelles, d’expérience professionnelle, ainsi que d’autres informations d’identification personnelle d’un demandeur.
- **Sourcecode**: détecte des éléments qui contiennent un ensemble d’instructions et d’instructions écrites dans des langages de programmation informatique largement utilisés.
- **Harcèlement**: détecte une catégorie spécifique d’éléments de texte de langue choquants liés à un comportement offensant ciblant une ou plusieurs personnes en fonction des caractéristiques suivantes : race, ethnique, religion, origine nationale, sexe, orientation sexuelle, âge, invalidité.
- **Blasphème**: détecte une catégorie spécifique d’éléments de texte en langue choquante qui contiennent des expressions qui déportent la plupart des gens.
- **Menace**: détecte une catégorie spécifique d’éléments de texte de langue choquants liés aux menaces pour valider la violence ou causer des dégâts ou des dommages physiques à une personne ou à une propriété.

Ces éléments apparaissent dans**la vue** classification des données `Ready to use`du centre > de **conformité Microsoft 365****(aperçu)** > avec le statut.

![classifieurs-prêts à l’emploi-classifieurs](media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Veuillez noter que le langage offensant, le harcèlement, le catégoriseur et les classifieurs de menaces ne fonctionnent qu’avec le texte pouvant faire l’objet d’une recherche.  De plus, les normes linguistiques et culturelles changent en permanence, et à la lumière de ces réalités, Microsoft se réserve le droit de mettre à jour ces classifieurs à sa discrétion. Tandis que les classifieurs peuvent aider votre organisation à surveiller le offensant et d’autres langues, les classifieurs ne traitent pas les conséquences de cette langue et ne sont pas destinés à fournir aux seuls moyens de surveillance ou de réponse à l’utilisation de cette langue. Votre organisation, et non Microsoft ou ses filiales, reste responsable de toutes les décisions relatives à la surveillance, à l’application, au blocage, à la suppression et à la rétention de tout contenu identifié par un classificateur pré-formé.

#### <a name="process-flow-for-using-ready-to-use-classifiers"></a>Flux de processus pour l’utilisation de classifieurs prêts à l’emploi

Prêt à utiliser les classifieurs n’a pas besoin d’être formé, mais vous devez confirmer qu’ils identifient les types de contenu dont vous avez besoin avant de les utiliser dans des solutions de conformité. Le test d’un classificateur pré-qualifié suit ce flux.

![test du flux de processus d’un classificateur pré-formé](media/classifier-pre-trained-classifier-flow.png)

### <a name="understanding-trainable-classifiers"></a>Présentation des classifieurs de formation

Lorsque les classifieurs prêts à l’emploi ne répondent pas à vos besoins, vous pouvez créer et former vos propres classifieurs. La création de vos propres tâches est beaucoup plus importante, mais elles seront beaucoup mieux adaptées à vos besoins. Pour plus d’informations sur l’utilisation d’un classificateur pré-formé, consultez la rubrique [utilisation d’un classificateur prêt à utiliser](classifier-using-a-ready-to-use-classifier.md)

> [!IMPORTANT]
> Seul l’utilisateur qui crée un classificateur de formation peut former et examiner les prévisions effectuées par ce classifieur.

#### <a name="process-flow-for-creating-trainable-classifiers"></a>Flux de processus pour la création de classifieurs de formation

La création et la publication d’un classificateur pour l’utilisation dans les solutions de conformité, telles que les stratégies de rétention et la surveillance des communications, suivent ce flux. Pour plus d’informations sur la création d’un classificateur de formation, consultez [la rubrique Création d’un classificateur de formation](classifier-creating-a-trainable-classifier.md).

![classificateur de flux de processus](media/classifier-trainable-classifier-flow.png)

## <a name="see-also"></a>Voir aussi

- [étiquettes de rétention](labels.md)
- [stratégies de rétention](retention-policies.md)
- [protection contre la perte de données (DLP)](data-loss-prevention-policies.md)
- [étiquettes de sensibilité](sensitivity-labels.md)
- [types d’informations sensibles](what-the-sensitive-information-types-look-for.md)
- [impression des doigts de document](document-fingerprinting.md)
- [correspondance exacte des données](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)
