---
title: Définitions des classifieurs pouvant être formés
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
- purview-compliance
- tier2
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Il s’agit d’une liste de tous les classifieurs pouvant être entraînés, de leurs définitions et de tous les types de fichiers qu’ils recherchent pour trouver des informations sensibles.
ms.openlocfilehash: d62e3e9b32a7ab977c0b052725b472ac326967f3
ms.sourcegitcommit: a250d043a2e42ecbc7b86147468d1660af5a6ba7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68673148"
---
# <a name="trainable-classifiers-definitions"></a>Définitions des classifieurs pouvant être formés

Microsoft Purview est fourni avec plusieurs classifieurs préentraînés. Ils apparaissent dans la **vue classifieurs portail de conformité Microsoft Purview** \> Classification **de données** \> **Classifiables** avec l’état .`Ready to use`


- **Adulte, racé et gory** : détecte les images de ce type. La taille des images doit être comprise entre 50 kilo-octets (Ko) et 4 mégaoctets (Mo) et être supérieure à 50 x 50 pixels dans les dimensions de hauteur x largeur. L’analyse et la détection sont prises en charge pour Exchange Online messages électroniques, ainsi que pour les canaux et conversations Microsoft Teams. Détecte le contenu dans les fichiers .jpeg, .png, .gif et .bmp.

- **Accords** : Détecte le contenu lié aux accords juridiques tels que les accords de non-divulgation, les énoncés de travail, les contrats de prêt et de bail, les contrats d’emploi et de non-concurrence. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Relevé bancaire (préversion)** : détecte les éléments qui contiennent une transaction financière d’un compte bancaire, y compris les informations de compte, les dépôts, les retraits, le solde du compte, les intérêts courus et les frais bancaires au cours d’une période donnée. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf .txt.

- **Budget (préversion)** : détecte les documents budgétaires, les prévisions budgétaires et les états budgétaires actuels, y compris les revenus et les dépenses d’une organisation. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppsm, .pps, .ppsam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltx, .xltm, .xlt, .xlam, .xla.

- **Business Plan (préversion)** : détecte les composants d’un plan d’affaires, notamment l’opportunité commerciale, le plan d’obtention des résultats, l’étude de marché et l’analyse des concurrents. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppsm, .pps, .ppsam, .ppa.

- **Spécifications de construction (préversion)** : détecte les spécifications de construction pour les projets commerciaux et industriels tels que les usines, les usines, les bureaux commerciaux, les aéroports, les routes. Capture des recommandations sur la qualité, la quantité, les types de matériaux de construction, les processus, etc. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppsm, .ppsam, .ppa.

- **Sabotage d’entreprise (préversion)** : détecte les messages qui peuvent mentionner des actes pour endommager ou détruire des biens ou des biens de l’entreprise. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire, telles que les normes de protection de l’infrastructure critique de la NERC ou les réglementations par état comme le chapitre 9.05 RCW dans l’état de Washington. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.  
> [!IMPORTANT] 
> En préversion, ce classifieur peut capturer un grand volume de contenu d’expéditeur/bulletin d’informations en bloc en raison d’un problème connu. Bien qu’ils soient en préversion, vous pouvez traiter de grands volumes de contenu d’expéditeur/bulletin d’informations en bloc en ajoutant le **message n’est envoyé à aucun de ces domaines condition** avec une liste de domaines à exclure. 

- **Plaintes des clients** : le classifieur des plaintes des clients détecte les commentaires et les plaintes concernant les produits ou services de votre organisation. Ce classifieur peut vous aider à répondre aux exigences réglementaires en matière de détection et de tri des plaintes, comme les exigences du Consumer Financial Protection Bureau et de la Food and Drug Administration. Pour la conformité des communications, il détecte le contenu dans les fichiers .msg et .eml. Pour le reste des services Protection des données Microsoft Purview, il détecte le contenu dans les fichiers .docx, .pdf, .txt, .rtf, .jpg, .jpeg, .png, .gif, .bmp, .svg.

- **Discrimination** : Détecte un langage discriminatoire explicite et est sensible à la langue discriminatoire à l’égard des communautés afro-américaines/noires par rapport à d’autres communautés. Cela s’applique à la conformité des communications, il s’agit d’un classifieur textuel.

- **Fichiers de mesures disciplinaires de l’employé (préversion)** : détecte les fichiers liés à des mesures disciplinaires, y compris une réprimande ou une mesure corrective en réponse à l’inconduite d’un employé, à une violation de règle ou à un mauvais rendement. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Fichiers d’assurance des employés (préversion)** : détecte les documents relatifs à l’assurance maladie des employés et à l’assurance invalidité professionnelle. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppsm, .ppsam, .ppa.

- **Contrat d’emploi (préversion)** : détecte le contrat de travail contenant des détails tels que la date de début, le salaire, la rémunération, les tâches d’emploi. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf .txt.

- **Finance** : détecte le contenu dans les catégories finance d’entreprise, comptabilité, économie, banque et investissement. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Rapports d’audit financier (préversion)** : détecte les fichiers, documents et rapports relatifs à l’audit financier, audit externe ou interne effectué dans une organisation. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **État financier (préversion)** : détecte les états financiers tels que le compte de résultat, le bilan, l’état des flux de trésorerie, l’état des variations des capitaux propres. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .xlsx, .xlsm, .xlsb, .xls .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Cadeaux & divertissement (préversion)** : détecte les messages qui peuvent suggérer l’échange de cadeaux ou de divertissements en échange d’un service, ce qui enfreint les réglementations liées à la corruption. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que le Foreign Corrupt Practices Act (FCPA), la loi britannique sur la corruption et la règle 2320 de la FINRA. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.
> [!IMPORTANT] 
> En préversion, ce classifieur peut capturer un grand volume de contenu d’expéditeur/bulletin d’informations en bloc en raison d’un problème connu. Bien qu’ils soient en préversion, vous pouvez traiter de grands volumes de contenu d’expéditeur/bulletin d’informations en bloc en ajoutant le **message n’est envoyé à aucun de ces domaines condition** avec une liste de domaines à exclure. 

- **Harcèlement** : Détecte une catégorie spécifique d’éléments de texte de langue offensante liés à un comportement offensant ciblant un ou plusieurs individus en fonction des caractéristiques suivantes : race, ethnicité, religion, origine nationale, sexe, orientation sexuelle, âge, handicap. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.

- **Formulaires de santé/médicaux (préversion)** : détecte les différents formulaires et fichiers utilisés pour la documentation systématique des détails d’admission d’un patient, des antécédents médicaux, des informations sur les patients et de la demande d’autorisation préalable, et qui sont généralement utilisés dans les services médicaux/de santé. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppsm, .ppsam, .ppa.

- **Soins de santé** : détecte le contenu dans les aspects médicaux et d’administration des soins de santé tels que les services médicaux, les diagnostics, les traitements, les réclamations, etc. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **RH** : détecte le contenu dans les catégories liées aux ressources humaines de recrutement, d’entrevue, d’embauche, de formation, d’évaluation, d’avertissement et de résiliation. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Facture (préversion)** : détecte les factures contenant un récapitulatif détaillée de l’achat, le solde total dû, le paiement actuel dû et divers modes de paiement. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .eml, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **IP** : détecte le contenu dans les catégories liées à la propriété intellectuelle telles que les secrets commerciaux et les informations confidentielles similaires. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Informatique** : détecte le contenu dans les catégories Technologies de l’information et Cybersécurité telles que les paramètres réseau, la sécurité des informations, le matériel et les logiciels. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, Fichiers .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Affaires juridiques** : détecte le contenu dans les catégories liées aux affaires juridiques telles que les litiges, les procédures juridiques, les obligations juridiques, la terminologie juridique, le droit et la législation. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Contrat de licence (préversion)** : détecte les contrats de licence, contient les conditions générales d’utilisation et la rémunération du titulaire de licence. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf .txt.

- **Contrats de prêt et lettres d’offre (préversion)** : détecte les contrats de prêt, les lettres d’offre et les conditions générales contenues dans le document. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Fichiers de fusion et d’acquisition (préversion)** : ce classifieur détecte les documents, y compris les lettres d’intention, les feuilles de termes et les fichiers associés. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Enregistrements de lots de fabrication (préversion)** : ce classifieur détecte les documents de traitement par lots de fabrication qui incluent des détails sur l’ensemble du processus de fabrication et l’historique d’un lot de produits. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Notes de réunion** (préversion) : ce classifieur détecte les notes de réunion. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppsm, .ppsam, .ppa.

- **Blanchiment d’argent (préversion)** : Détecte les signes qui peuvent suggérer le blanchiment d’argent ou l’engagement dans des actes de dissimulation ou de déguise l’origine ou la destination des produits. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que la Bank Secrecy Act, l’USA Patriot Act, la règle 3310 de la FINRA et la loi anti-blanchiment de 2020. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.
> [!IMPORTANT] 
> En préversion, ce classifieur peut capturer un grand volume de contenu d’expéditeur/bulletin d’informations en bloc en raison d’un problème connu. Bien qu’ils soient en préversion, vous pouvez traiter de grands volumes de contenu d’expéditeur/bulletin d’informations en bloc en ajoutant le **message n’est envoyé à aucun de ces domaines condition** avec une liste de domaines à exclure. 

- **Fichiers de conception de réseau (préversion)** : ce classifieur détecte la documentation technique sur les réseaux d’ordinateurs, y compris les différents composants du réseau, la façon dont ils sont connectés, leur architecture, Comment ils s’exécutent et où ils résolvent les problèmes Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppsam, .ppa.

- **Accord de non-divulgation (préversion)** : ce classifieur détecte les accords de non-divulgation. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf .txt.

- **Paystub (préversion)** : ce classifieur détecte les fichiers de paytub/salary statement. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .xlsx, .xlsm, .xlsb, .xls .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Approvisionnement** : détecte le contenu dans les catégories d’enchères, de devis, d’achat et de paiement pour la fourniture de biens et de services. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Documents de projet (préversion)** : ce classifieur détecte les rapports et les documents de projet, notamment les documents de planification de projet, les documents de charte de projet et les planifications. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppsm, .ppsam, .ppa.

- **Grossièreté** : détecte une catégorie spécifique d’éléments de texte de langage offensant qui contiennent des expressions qui embarrassent la plupart des gens. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.

- **Collusion réglementaire (préversion)** : détecte les messages susceptibles d’enfreindre les exigences réglementaires anti-collusion, telles qu’une tentative de dissimulation d’informations sensibles. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que le Sherman Antitrust Act, Securities Exchange Act 1933, Securities Exchange Act of 1934, Investment Advisors Act of 1940, Federal Commission Act, and Robinson-Patman Act. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.
> [!IMPORTANT] 
> En préversion, ce classifieur peut capturer un grand volume de contenu d’expéditeur/bulletin d’informations en bloc en raison d’un problème connu. Bien qu’ils soient en préversion, vous pouvez traiter de grands volumes de contenu d’expéditeur/bulletin d’informations en bloc en ajoutant le **message n’est envoyé à aucun de ces domaines condition** avec une liste de domaines à exclure. 

- **Resume** : ce classifieur détecte la reprise. Un CV est un document qu’un demandeur d’emploi fournit à un employeur, qui contient une déclaration détaillée de son expérience de travail antérieure, de ses études et de ses réalisations. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf .txt.

- **Ventes et revenus (préversion)** : ce classifieur détecte les rapports de ventes, le chiffre d’affaires/le compte de résultat et les rapports de prévision des ventes/de la demande pour les organisations. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppsm, .pps, .ppam, .ppa.

- **Fichiers de développement de produits logiciels (préversion)** : ce classifieur détecte les fichiers utilisés dans le développement de logiciels, notamment le document relatif aux exigences du produit, les tests et la planification des produits, les fichiers, y compris les cas de test et les rapports de test. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml.

- **Code source** : détecte les éléments qui contiennent un ensemble d’instructions et d’instructions écrites dans des langages de programmation informatique sur GitHub : ActionScript, C, C#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script. Détecte le contenu dans .msg, .as, .h, .cs, .cc, .cpp, .hpp, .cxx, .hh, .c++, .clj, .edn, .cljc, .cljs, .coffee, .litcoffee, .go, .hs, .lhs, .java, .jar, .js, .mjs, .lua, .m, .mm, .pl, .pm, .t, .xs, .pod, .php, .phar, .php4, .pyc, . R, .r, .rda, . Fichiers RData, .rds, .rb, .scala, .sc, .sh, .swift.

  > [!NOTE]
  > Le code source est formé pour détecter quand la majeure partie du texte est du code source. Il ne détecte pas le texte du code source entrecoupé de texte brut.

- **Énoncé de travail (préversion)** : ce classifieur détecte l’énoncé de travail contenant des détails tels que les exigences, les responsabilités, les conditions générales pour les deux parties. Détecte le contenu dans les fichiers .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf .txt.

- **Manipulation d’actions (préversion)** : détecte des signes de manipulation d’actions possibles, tels que des recommandations d’achat, de vente ou de conservation d’actions qui peuvent suggérer une tentative de manipulation du cours de l’action. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que la Loi sur la bourse de valeurs mobilières de 1934, la règle 2372 de la FINRA et la règle 5270 de la FINRA. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.
> [!IMPORTANT] 
> En préversion, ce classifieur peut capturer un grand volume de contenu d’expéditeur/bulletin d’informations en bloc en raison d’un problème connu. Bien qu’ils soient en préversion, vous pouvez traiter de grands volumes de contenu d’expéditeur/bulletin d’informations en bloc en ajoutant le **message n’est envoyé à aucun de ces domaines condition** avec une liste de domaines à exclure.   

- **Taxe** : détecte le contenu fiscal tel que la planification fiscale, les formulaires fiscaux, les déclarations fiscales, les réglementations fiscales. Détecte le contenu dans .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .pot, .ppsx, .ppsm, .ppsm, .ppsm, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, xla.

- **Menace** : détecte une catégorie spécifique d’éléments de texte de langue offensante liés aux menaces de commettre des violences ou de causer des dommages physiques ou des dommages à une personne ou à des biens. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.

- **Divulgation non autorisée (préversion)** : détecte le partage d’informations contenant du contenu qui est explicitement désigné comme confidentiel ou interne à des personnes non autorisées. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que la règle FINRA 2010 et la règle SEC 10b-5. Détecte le contenu dans les fichiers .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.
> [!IMPORTANT] 
> En préversion, ce classifieur peut capturer un grand volume de contenu d’expéditeur/bulletin d’informations en bloc en raison d’un problème connu. Bien qu’ils soient en préversion, vous pouvez traiter de grands volumes de contenu d’expéditeur/bulletin d’informations en bloc en ajoutant le **message n’est envoyé à aucun de ces domaines condition** avec une liste de domaines à exclure. 





> [!IMPORTANT]
> Notez que les classifieurs globaux et entraînables intégrés ne fournissent pas de liste exhaustive ou complète de termes ou de langues dans ces domaines. En outre, les normes linguistiques et culturelles changent continuellement, et à la lumière de ces réalités, Microsoft se réserve le droit de mettre à jour ces classifieurs à sa discrétion. Bien que les classifieurs puissent aider votre organisation à détecter ces zones, les classifieurs ne sont pas destinés à fournir le seul moyen de votre organisation de détecter ou de traiter l’utilisation de ce langage. Votre organisation, et non Microsoft ou ses filiales, reste responsable de toutes les décisions relatives à la surveillance, à l’analyse, au blocage, à la suppression et à la conservation de tout contenu identifié par un classifieur préentraîné, y compris la conformité à la confidentialité locale et aux autres lois applicables. Microsoft encourage les conseillers juridiques avant le déploiement et l’utilisation.

Nos classifieurs de menaces, de grossièretés et de harcèlement peuvent analyser le contenu dans ces langues :

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

Tous les autres sont en anglais uniquement.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="see-also"></a>Voir aussi

- [Étiquettes de rétention](retention.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Impression de doigts de document](document-fingerprinting.md)
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
