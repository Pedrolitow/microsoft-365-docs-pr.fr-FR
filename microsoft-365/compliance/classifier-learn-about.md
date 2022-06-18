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
description: Les classifieurs pouvant être formés peuvent reconnaître différents types de contenu pour l’étiquetage ou l’application de stratégie en lui donnant des exemples positifs et négatifs à examiner.
ms.openlocfilehash: 03c0c0991188982fbfc4fb9ec908f6e5f4ab3bba
ms.sourcegitcommit: b0b1be67de8f40b199bb9b51eb3568e59377e93a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2022
ms.locfileid: "66159573"
---
# <a name="learn-about-trainable-classifiers"></a>En savoir plus sur les classifieurs avec capacité d’apprentissage

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

La classification et l’étiquetage du contenu afin qu’il puisse être protégé et géré correctement constituent le point de départ de la discipline de protection des informations. Microsoft 365 a trois façons de classer le contenu.

## <a name="manually"></a>Manuellement

La classification manuelle requiert un jugement et une action humains. Les utilisateurs et les administrateurs les appliquent au contenu lorsqu’ils le rencontrent. Vous pouvez utiliser les étiquettes préexistantes et les types d’informations sensibles ou utiliser des étiquettes créées personnalisées.  Vous pouvez ensuite protéger le contenu et gérer sa destruction.

## <a name="automated-pattern-matching"></a>Mise en correspondance automatisée des modèles

Cette catégorie de mécanismes de classification inclut la recherche de contenu par :

- Mots clés ou valeurs de métadonnées (langage de requête de mot clé).
- Utilisation de modèles précédemment identifiés d’informations sensibles telles que les numéros de sécurité sociale, de carte de crédit ou de compte bancaire [(définitions d’entités de type Informations sensibles).](sensitive-information-type-entity-definitions.md)
- Reconnaissance d’un élément, car il s’agit d’une variante d’un modèle [(impression par doigt de document).](document-fingerprinting.md)
- Utilisation de la présence de chaînes exactes [correspondant exactement aux données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

Les étiquettes de confidentialité et de rétention peuvent ensuite être appliquées automatiquement pour rendre le contenu disponible pour une utilisation dans [En savoir plus sur Protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md) et [appliquer automatiquement des stratégies pour les étiquettes de rétention](apply-retention-labels-automatically.md).

## <a name="classifiers"></a>Classificateurs

Cette méthode de classification est bien adaptée au contenu qui n’est pas facile à identifier par les méthodes manuelles ou automatisées de mise en correspondance des modèles. Cette méthode de classification consiste davantage à utiliser un classifieur pour identifier un élément en fonction de ce qu’est l’élément, et non par les éléments qui se trouvent dans l’élément (critères spéciaux). Un classifieur apprend à identifier un type de contenu en examinant des centaines d’exemples de contenu que vous souhaitez classifier.

> [!NOTE]
> En préversion : vous pouvez afficher les classifieurs pouvant être formés dans l’Explorateur de contenu en développant les **classifieurs pouvant être entraînés** dans le panneau filtres. Les classifieurs pouvant être formés affichent automatiquement le nombre d’incidents trouvés dans SharePoint, Teams et OneDrive, sans nécessiter d’étiquetage.
> Si vous ne souhaitez pas utiliser cette fonctionnalité, vous devez envoyer une demande auprès de Support Microsoft. Cela désactive l’affichage de vos données sensibles qui ne sont utilisées dans aucune stratégie d’étiquetage dans l’Explorateur de contenu. Vous pouvez également désactiver l’analyse de vos données. Si l’analyse est désactivée, l’étiquetage de sensibilité et les stratégies DLP avec ces classifieurs ne fonctionnent pas

### <a name="where-you-can-use-classifiers"></a>Où vous pouvez utiliser des classifieurs

Les classifieurs peuvent être utilisés comme condition pour [Office l’étiquetage automatique avec des étiquettes de confidentialité](apply-sensitivity-label-automatically.md), [l’application automatique d’une stratégie d’étiquette de rétention en fonction d’une condition](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) et de [la conformité des communications](communication-compliance.md).

Les étiquettes de confidentialité peuvent utiliser des classifieurs comme conditions. [Consultez Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md).

> [!IMPORTANT]
> Les classifieurs fonctionnent uniquement avec des éléments qui ne sont pas chiffrés.

## <a name="types-of-classifiers"></a>Types de classifieurs

- **classifieurs préentrifiés** : Microsoft a créé et préentragé plusieurs classifieurs que vous pouvez commencer à utiliser sans les former. Ces classifieurs s’affichent avec l’état .`Ready to use`
- **classifieurs entraînés personnalisés** : si vous avez des besoins de classification qui dépassent ce que couvrent les classifieurs préentrifiés, vous pouvez créer et entraîner vos propres classifieurs.

### <a name="pre-trained-classifiers"></a>Classifieurs préentrifiés

Microsoft 365 est fourni avec plusieurs classifieurs préformés :

- **Adult, racy et gory** : détecte les images de ces types. Les images doivent avoir une taille comprise entre 50 kilo-octets (Ko) et 4 mégaoctets (Mo) et être supérieures à 50 x 50 pixels dans les dimensions hauteur x largeur. L’analyse et la détection sont prises en charge pour Exchange Online messages électroniques et Microsoft Teams canaux et conversations. Détecte le contenu dans les fichiers .jpeg, .png, .gif et .bmp.

- **Contrats** : détecte le contenu relatif aux contrats juridiques tels que les contrats de non-divulgation, les déclarations de travail, les contrats de prêt et de bail, les contrats d’emploi et de non-concurrence. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Plaintes des** clients : le classifieur de plaintes des clients détecte les commentaires et les plaintes concernant les produits ou services de votre organisation. Ce classifieur peut vous aider à répondre aux exigences réglementaires en matière de détection et de tri des plaintes, comme les exigences du Bureau de protection financière des consommateurs et de la Food and Drug Administration. Pour la conformité des communications, il détecte le contenu dans les fichiers .msg et .eml. Pour le reste des services Protection des données Microsoft Purview, il détecte le contenu dans les fichiers .docx, .pdf, .txt, .rtf, .jpg, .jpeg, .png, .gif, .bmp et .svg.

- **Discrimination** : détecte une langue discriminatoire explicite et est sensible à la langue discriminatoire à l’égard des communautés afro-américaines/noires par rapport à d’autres communautés.

- **Finance** : détecte le contenu dans les catégories finance d’entreprise, comptabilité, économie, banque et investissement. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla files.

- **Harcèlement** : détecte une catégorie spécifique d’éléments de texte de langue offensants liés à une conduite offensante ciblant une ou plusieurs personnes en fonction des caractéristiques suivantes : race, ethnicité, religion, origine nationale, sexe, orientation sexuelle, âge, handicap. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp et .svg.

- **Santé** : détecte le contenu dans les aspects de l’administration médicale et des soins de santé tels que les services médicaux, les diagnostics, le traitement, les revendications, etc. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla files.

- **RH** : détecte le contenu des catégories de recrutement, d’entretien, d’embauche, de formation, d’évaluation, d’avertissement et de résiliation liées aux ressources humaines. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla files.

- **IP** : détecte le contenu dans les catégories liées à la propriété intellectuelle, telles que les secrets commerciaux et les informations confidentielles similaires. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla files.

- **Informatique** : détecte le contenu dans les catégories Technologies de l’information et Cybersécurité, telles que les paramètres réseau, la sécurité des informations, le matériel et les logiciels. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla files.

- **Affaires juridiques** : détecte le contenu dans les catégories liées aux affaires juridiques telles que les litiges, les procédures juridiques, les obligations juridiques, la terminologie juridique, le droit et la législation. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Approvisionnement** : détecte le contenu dans les catégories d’enchères, de citations, d’achats et de paiement pour la fourniture de biens et de services. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Blasphème** : détecte une catégorie spécifique d’éléments de texte de langage offensant qui contiennent des expressions qui gênent la plupart des gens. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp et .svg.

- **Cv** : détecte les éléments docx, .pdf, .rtf .txt qui sont des comptes textuels des qualifications personnelles, éducatives, professionnelles, professionnelles et autres informations d’identification personnelle d’un candidat

- **Code source** : détecte les éléments qui contiennent un ensemble d’instructions et d’instructions écrites en langages de programmation informatique sur GitHub : ActionScript, C, C#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script. Détecte le contenu dans .msg, .as, .h, .c, .cs, .cc, .cpp, .hpp, .cxx, .hh, .c++, .clj, .edn, .cljc, .cljs, .coffee, .litcoffee, .go, .hs, .lhs, .java, .jar, .js, .mjs, .lua, .m, .mm, .pl, .pm, .t, .xs, .pod, .php, .phar, .php4, .pyc. R, .r, .rda, . RData, .rds, .rb, .scala, .sc, .sh, .swift files.

  > [!NOTE]
  > Le code source est formé pour détecter quand la majeure partie du texte est du code source. Il ne détecte pas le texte du code source qui est entrecoupé de texte brut.

- **Tax**: Detects Tax relation content such as tax planning, tax forms, tax filing, tax regulations. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, xla files.

- **Menace** : détecte une catégorie spécifique d’éléments de texte de langue offensants liés aux menaces de commettre de la violence ou de causer des dommages physiques ou des dommages à une personne ou à des biens.

- **Menace** : détecte une catégorie spécifique d’éléments de texte de langue offensants liés aux menaces de commettre de la violence ou de causer des dommages physiques ou des dommages à une personne ou à des biens. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp et .svg.

Ces classifieurs apparaissent dans la **vue portail de conformité Microsoft Purview** \> **Classifieurs de** **classification** \> des données pouvant être formés avec l’état .`Ready to use`

![classifiers-pre-trained-classifiers.](../media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Notez que les classifieurs intégrés pouvant être formés et globaux ne fournissent pas de liste exhaustive ou complète de termes ou de langues dans ces domaines. De plus, les normes linguistiques et culturelles changent continuellement, et à la lumière de ces réalités, Microsoft se réserve le droit de mettre à jour ces classifieurs à sa discrétion. Bien que les classifieurs puissent aider votre organisation à détecter ces domaines, les classifieurs ne sont pas destinés à fournir à votre organisation le seul moyen de détecter ou de traiter l’utilisation de ce langage. Votre organisation, et non Microsoft ou ses filiales, reste responsable de toutes les décisions relatives à la surveillance, à l’analyse, au blocage, à la suppression et à la rétention de tout contenu identifié par un classifieur préentragé, y compris la conformité avec la confidentialité locale et d’autres lois applicables. Microsoft encourage la consultation avec des conseillers juridiques avant le déploiement et l’utilisation.

Nos classifieurs de menace, de blasphème, de harcèlement et de discrimination peuvent analyser le contenu dans les langues suivantes :

- Arabe
- Chinois (simplifié)
- Chinois (traditionnel)
- Néerlandais
- Anglais
- Français
- Allemand
- Italien
- Korean
- Japanese
- Portugais
- Espagnol

Tous les autres ne sont anglais qu’en ce moment.

### <a name="custom-classifiers"></a>Classifieurs personnalisés

Lorsque les classifieurs préformés ne répondent pas à vos besoins, vous pouvez créer et entraîner vos propres classifieurs. Il y a davantage de travail à faire pour créer les vôtres, mais ils seront beaucoup mieux adaptés aux besoins de votre organisation.

Vous commencez à créer un classifieur entraîné personnalisé en lui fournissant des exemples qui sont certainement dans la catégorie. Une fois qu’il traite ces exemples, vous le testez en lui donnant un mélange d’exemples correspondants et non correspondants. Le classifieur effectue ensuite des prédictions quant à savoir si un élément donné appartient à la catégorie que vous créez. Vous confirmez ensuite ses résultats, en triant les vrais positifs, les vrais négatifs, les faux positifs et les faux négatifs pour améliorer la précision de ses prédictions.

Lorsque vous publiez le classifieur, il trie les éléments dans des emplacements tels que SharePoint Online, Exchange et OneDrive, et classifie le contenu. Après avoir publié le classifieur, vous pouvez continuer à l’entraîner à l’aide d’un processus de commentaires similaire au processus de formation initial.

Par exemple, vous pouvez créer des classifieurs pouvant être formés pour :

- Documents juridiques , tels que le privilège client d’avocat, les ensembles fermants, la déclaration de travail
- Documents commerciaux stratégiques , tels que les communiqués de presse, les fusions et acquisitions, les transactions, les plans commerciaux ou marketing, la propriété intellectuelle, les brevets, les documents de conception
- Informations de tarification , telles que les factures, les devis de prix, les commandes professionnelles, les documents d’enchères
- Informations financières, telles que les investissements organisationnels, les résultats trimestriels ou annuels

#### <a name="process-flow-for-creating-custom-classifiers"></a>Flux de processus pour la création de classifieurs personnalisés

La création et la publication d’un classifieur à utiliser dans les solutions de conformité, telles que les stratégies de rétention et la supervision des communications, suivent ce flux. Pour plus d’informations sur la création d’un classifieur pouvant être entraîné personnalisé, consultez [La création d’un classifieur personnalisé](classifier-get-started-with.md).

![classifieur personnalisé de flux de processus.](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Reformation des classifieurs

Vous pouvez aider à améliorer la précision de tous les classifieurs entraînés personnalisés et en leur fournissant des commentaires sur la précision de la classification qu’ils effectuent. Il s’agit d’un réentraînement qui suit ce flux de travail.

> [!NOTE]
> Les classifieurs préentraînés ne peuvent pas être réentraînés.

![workflow de réentraînement du classifieur.](../media/classifier-retraining-workflow.png)

## <a name="see-also"></a>Voir aussi

- [Étiquettes de rétention](retention.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Impression de doigts de document](document-fingerprinting.md)
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
