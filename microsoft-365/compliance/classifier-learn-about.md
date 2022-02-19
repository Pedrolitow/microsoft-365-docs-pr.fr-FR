---
title: En savoir plus sur les classifieurs avec capacité d’apprentissage
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Les classifieurs entraisables peuvent reconnaître différents types de contenu pour l’étiquetage ou l’application de stratégie en lui donnant des exemples positifs et négatifs à examiner.
ms.openlocfilehash: 50d20c3a40b21696c06064b548d7766684fb12a0
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2022
ms.locfileid: "62909638"
---
# <a name="learn-about-trainable-classifiers"></a>En savoir plus sur les classifieurs avec capacité d’apprentissage

La classification et l’étiquetage du contenu afin qu’il puisse être protégé et géré correctement constitue le point de départ de la protection des informations. Microsoft 365 trois façons de classifier le contenu.

## <a name="manually"></a>Manuellement

La classification manuelle nécessite un juge humain et une action. Les utilisateurs et les administrateurs les appliquent au contenu à mesure qu’ils le rencontrent. Vous pouvez utiliser les étiquettes pré-existantes et les types d’informations sensibles ou utiliser des étiquettes créées personnalisées.  Vous pouvez ensuite protéger le contenu et gérer sa disposition.

## <a name="automated-pattern-matching"></a>Mise en correspondance automatique des modèles

Cette catégorie de mécanismes de classification inclut la recherche de contenu par :

- Mots clés ou valeurs de métadonnées (langage de requête de mot clé).
- Utilisation de modèles précédemment identifiés d’informations sensibles telles que la sécurité sociale, la carte bancaire ou les numéros de compte bancaire (définitions d’entités de [type d’informations sensibles)](sensitive-information-type-entity-definitions.md)
- Reconnaissance d’un élément, car il s’agit d’une variante d’un modèle [(impression avec le doigt du document).](document-fingerprinting.md)
- L’utilisation de la présence de chaînes [exactes correspond exactement aux données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

Les étiquettes de sensibilité et de rétention peuvent ensuite être appliquées automatiquement pour rendre le contenu disponible [](dlp-learn-about-dlp.md) pour utilisation dans La recherche sur la protection contre la perte de données et l’application automatique des [stratégies pour les étiquettes de rétention](apply-retention-labels-automatically.md).

## <a name="classifiers"></a>Classifieurs

Cette méthode de classification est bien adaptée au contenu qui n’est pas facilement identifié par les méthodes manuelles ou automatisées de correspondance de modèles. Cette méthode de classification consiste davantage à utiliser un classificateur pour identifier un élément en fonction de ce qu’est l’élément, et non par des éléments qui se trouve dans l’élément (correspondance de modèle). Un classifieur apprend à identifier un type de contenu en regardant des centaines d’exemples de contenu que vous souhaitez classer.

> [!NOTE]
> En prévisualisation : vous pouvez afficher les classifieurs entra nerables dans l’explorateur de contenu en développez **classifieurs entra nessables** dans le panneau de filtres. Les classifieurs entra nements afficheront automatiquement le nombre d’incidents trouvés dans SharePoint, Teams et OneDrive, sans nécessiter d’étiquetage.
> Si vous ne souhaitez pas utiliser cette fonctionnalité, vous devez déposer une demande auprès du Support Microsoft pour désactiver la classification pré- Cela désactive l’analyse de votre contenu sensible et étiqueté avant de créer des stratégies d’étiquetage.

### <a name="where-you-can-use-classifiers"></a>Où utiliser des classifieurs

Les classifieurs peuvent être utilisés comme condition pour l’Office [l’étiquetage](apply-sensitivity-label-automatically.md) automatique avec des étiquettes de confidentialité, l’application automatique d’une stratégie d’étiquette de rétention basée sur une [condition](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) et la conformité des [communications](communication-compliance.md). 

Les étiquettes de sensibilité peuvent utiliser des classifieurs comme conditions. Voir Appliquer automatiquement une étiquette de sensibilité [au contenu](apply-sensitivity-label-automatically.md).

> [!IMPORTANT]
> Les classifieurs fonctionnent uniquement avec les éléments qui ne sont pas chiffrés.

## <a name="types-of-classifiers"></a>Types de classifieurs

- **Classifieurs pré-formés** : Microsoft a créé et pré-formé plusieurs classifieurs que vous pouvez commencer à utiliser sans les former. Ces classifieurs apparaissent avec l’état de `Ready to use`.
- **Classifieurs entraisables personnalisés** : si vous avez des besoins de classification qui étendent au-delà de ce que couvrent les classifieurs pré-formés, vous pouvez créer et former vos propres classifieurs.

### <a name="pre-trained-classifiers"></a>Classifieurs pré-formés

Microsoft 365 est livré avec plusieurs classifieurs pré-formés :

> [!CAUTION]
> Nous déconseillons le classificateur **Langage choquant** pré-formé, car il a produit un grand nombre de faux positifs. Ne l’utilisez pas et si vous l’utilisez actuellement, vous devez en déplacer vos processus d’entreprise. Nous vous recommandons plutôt **d’utiliser** les classifieurs  pré-formés contre les menaces **, les** blasphémités et le harcèlement.

- **Cv** : détecte les éléments docx, .pdf, .rtf, .txt qui sont des comptes textuels des qualifications personnelles, pédagogiques, professionnelles, professionnelles et autres informations d’identification personnelle d’un candidat
- **Code source** : détecte les éléments qui contiennent un ensemble d’instructions et d’instructions écrites dans les 25 langages de programmation informatique les plus utilisés sur GitHub : ActionScript, C, C#, C++, Chefjure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script. Détecte le contenu dans .msg, .as, .h, .c, .cs, .cc, .cpp, .hpp, .cxx, .hh, .c++, .clj, .edn, .cljc, .cljs, .coffee, .litcoffee, .go, .hs, .lhs, .java, .jar, .js, .mjs, .lua, .m, .mm, .pl, .pm, .t, .xs, .pod, .php, .pho, .php4, .pyc, . R, .r, .rda, . Fichiers RData, .rds, .rb, .scala, .sc, .sh, .swift.

> [!NOTE]
> Le code source est formé pour détecter quand l’essentiel du texte est du code source. Il ne détecte pas le texte de code source qui est entrecoupé de texte simple.

- **Accords :** détecte le contenu lié aux accords juridiques tels que les accords de non-divulgation, les déclarations de travail, les contrats de prêt et de bail, les contrats de travail et de non-concurrence. Détecte le contenu des fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.
- **Discrimination** : détecte un langage explicite de discrimination et est sensible au langage de discrimination à l’encontre des communautés américaines/noires d’Amérique du Sud par rapport à d’autres communautés.
- **Finance** : détecte le contenu des catégories finance d’entreprise, comptabilité, économie, banque et investissement. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.
- **Harcèlement** : détecte une catégorie spécifique d’éléments de texte de langage choquant liés à une conduite choquante ciblant un ou plusieurs individus en fonction des caractéristiques suivantes : la course, l’ancienneté, l’origine nationale, le sexe, l’orientation sexuelle, l’âge, le handicap. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.
- **Santé** : détecte le contenu dans les aspects d’administration médicale et médicale tels que les services médicaux, les diagnostics, les traitements, les revendications, etc. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.
- **RH** : détecte le contenu dans les catégories liées aux ressources humaines de recrutement, d’entretien, d’embauche, de formation, d’évaluation, d’avertissement et de résiliation. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.
- **IP** : détecte le contenu dans les catégories liées à la propriété intellectuelle telles que les secrets commerciaux et des informations confidentielles similaires. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.
- **It**: Detects content in Information Technology and Cybersecurity categories such as network settings, information security, hardware, and software. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.
- Affaires juridiques : détecte le contenu dans les catégories juridiques liées aux affaires, telles que les litiges, les processus **juridiques, les obligations légales**, la terminologie juridique, la loi et la législation. Détecte le contenu des fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.
- **Approvisionnement** : détecte le contenu dans les catégories de fourniture, de quoting, d’achat et de paiement de la fourniture de biens et de services. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.
- **Blasphémité** : détecte une catégorie spécifique d’éléments de texte de langage choquant qui contiennent des expressions qui gênent la plupart des personnes. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.
- **Taxe** : détecte le contenu des relations fiscales telles que la planification fiscale, les déclarations fiscales, la déclaration fiscale, les réglementations fiscales. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, xla.
- **Menace** : détecte une catégorie spécifique d’éléments de texte de langage choquant liés aux menaces de violence ou d’atteinte physique à une personne ou à une propriété. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.

Ceux-ci apparaissent **dans la Centre de conformité Microsoft 365** >  **classifieurs classificationData** >  **Avec** l’état de `Ready to use`.

![classifieurs-pré-formés-classifieurs.](../media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Veuillez noter que le langage choquant, le harcèlement, la blasphémité, la discrimination et les classifieurs de menaces fonctionnent uniquement avec du texte utilisable dans une recherche et ne sont pas une liste exhaustive ou complète de termes ou de langues dans ces domaines. En outre, les normes linguistiques et culturelles changent continuellement et, à la lumière de ces exigences, Microsoft se réserve le droit de mettre à jour ces classifieurs à sa discrétion. Bien que les classifieurs aident votre organisation à détecter ces domaines, ils ne sont pas destinés à fournir l’unique moyen de détecter ou de traiter l’utilisation de ce langage dans votre organisation. Votre organisation, et non Microsoft ou ses filiales, reste responsable de toutes les décisions relatives à la surveillance, à l’analyse, au blocage, à la suppression et à la rétention de tout contenu identifié par un classificateur pré-formé, y compris la conformité avec la confidentialité locale et d’autres lois applicables. Microsoft encourage les conseils juridiques avant le déploiement et l’utilisation.

Les classifieurs pré-formés peuvent analyser le contenu dans ces langues :

• Chinois (simplifié) • anglais • français • allemand • italien • japonais • portugais • espagnol

### <a name="custom-classifiers"></a>Classifieurs personnalisés

Lorsque les classifieurs pré-formés ne répondent pas à vos besoins, vous pouvez créer et former vos propres classifieurs. Il y a beaucoup plus de travail à faire avec la création de vos propres produits, mais ils seront bien mieux adaptés aux besoins de votre organisation.

Vous commencez à créer un classifieur entraisable personnalisé en lui insumant des exemples qui sont certainement dans la catégorie. Une fois qu’il a traite ces exemples, vous le testez en lui donnant un mélange d’exemples correspondants et non correspondants. Le classifieur effectue ensuite des prédictions quant à l’entrée d’un élément donné dans la catégorie que vous construisez. Vous confirmez ensuite ses résultats, en triant les vrais positifs, les vrais négatifs, les faux positifs et les faux négatifs pour améliorer la précision de ses prédictions. 

Lorsque vous publiez le classifieur, il trie les éléments dans des emplacements tels que SharePoint Online, Exchange et OneDrive, et classifie le contenu. Après avoir publié le classificateur, vous pouvez continuer à l’entraîner à l’aide d’un processus de commentaires semblable au processus de formation initial.

Par exemple, vous pouvez créer des classifieurs entraisables pour :

- Documents juridiques : par exemple, privilège client avocat, jeux de fermeture, déclaration de travail
- Documents d’entreprise stratégiques : communiqués de presse, fusion et acquisition, transactions, plans commerciaux ou commerciaux, propriété intellectuelle, brevets, documents de conception
- Informations tarifaires : par exemple, factures, devis, commandes de travail, documents d’auteur
- Informations financières , telles que les investissements organisationnels, les résultats trimestrielles ou annuels

#### <a name="process-flow-for-creating-custom-classifiers"></a>Flux de processus pour la création de classifieurs personnalisés

La création et la publication d’un classifieur à utiliser dans les solutions de conformité, telles que les stratégies de rétention et la surveillance des communications, suivent ce flux. Pour plus d’informations sur la création d’un classifieur entraisable personnalisé, voir [Création d’un classificateur personnalisé](classifier-get-started-with.md).

![classifieur personnalisé de flux de processus.](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Retraining classifiers

Vous pouvez améliorer la précision de tous les classifieurs entra nessables personnalisés et en leur fournissant des commentaires sur la précision de la classification qu’ils effectuent. C’est ce qu’on appelle une nouvelle formation et suit ce flux de travail.

> [!NOTE]
> Les classifieurs pré-formés ne peuvent pas être ré-formés.

![flux de travail de formation de classifieur.](../media/classifier-retraining-workflow.png)

## <a name="see-also"></a>Voir aussi

- [Étiquettes de rétention](retention.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Impression des doigts du document](document-fingerprinting.md)
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
