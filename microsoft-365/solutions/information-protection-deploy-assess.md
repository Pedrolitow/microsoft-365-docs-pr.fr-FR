---
title: Évaluer les risques de confidentialité des données et identifier les éléments sensibles avec Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 07/13/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Déterminez la réglementation relative à la confidentialité des données, les scénarios pertinents, votre disponibilité et les types d’informations sensibles qui se trouvent dans votre environnement Microsoft 365.
ms.openlocfilehash: c2f8bd6587e399fd1e928575b3cd9dfb2a4565eb
ms.sourcegitcommit: 9841058fcc95f7c2fed6af92bc3c3686944829b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "48377114"
---
# <a name="assess-data-privacy-risks-and-identify-sensitive-items-with-microsoft-365"></a>Évaluer les risques de confidentialité des données et identifier les éléments sensibles avec Microsoft 365

L’évaluation des réglementations et des risques liés à la confidentialité des données auxquelles votre organisation est soumise est une première étape clé avant l’implémentation des actions d’amélioration associées, notamment celles réalisables avec les fonctionnalités et services de Microsoft 365. 

## <a name="potentially-applicable-data-privacy-regulations"></a>Réglementations sur la confidentialité des données potentiellement applicables

Pour en savoir plus sur le cadre réglementaire plus large pour la réglementation en matière de confidentialité des données, consultez le [portail d’approbation de services Microsoft](https://servicetrust.microsoft.com/) et la [série d’articles sur le règlement général sur la protection des données (RGPD)](../compliance/gdpr.md), ainsi que d’autres documents relatifs aux réglementations auxquelles vous pouvez être soumis dans votre secteur ou région.

### <a name="gdpr"></a>RGPD

Le RGPD, le plus connu et le plus mentionné des réglementations sur la confidentialité des données, réglemente la collecte, le stockage, le traitement et le partage des données personnelles qui se rapportent à une personne physique identifiée ou identifiable qui est un résident de l’Union européenne (UE). 

Conformément à l’article 4, RGPD : 

- « données personnelles » : toute information relative à une personne physique identifiée ou identifiable (« personne concernée »); une personne physique identifiable est une personne qui peut être identifiée, directement ou indirectement, en particulier par référence à un identificateur tel qu’un nom, un numéro d’identification, des données de localisation, un identificateur en ligne ou un ou plusieurs facteurs spécifiques à l’identité physique, physiologique, génétique, mentale, économique, culturelle ou sociale de cette personne physique.

### <a name="iso-27001"></a>ISO 27001

L’adhésion à d’autres normes, telles que ISO 27001, a également été reconnue par plusieurs autorités de surveillance européennes comme un proxy d’intention valide dans le spectre des personnes, des processus et des technologies. Les standards qu’il spécifie chevauchement et l’adhérence aux mécanismes de protection de norme ISO-27001 peuvent être considérés comme un proxy remplissant certaines obligations de confidentialité dans certaines circonstances.

### <a name="other-data-privacy-regulations"></a>Autres réglementations en matière de confidentialité des données

D’autres réglementations importantes en matière de confidentialité des données précisent également les conditions requises pour la gestion des données personnelles.

Aux États-Unis, il s’agit de la loi[CCPA](../compliance/ccpa-faq.md)(California Consumer Protection Act), de la loi HIPAA-Hi (Health Care Privacy Act) et de la Loi de Graham Leach Bliley Act (GLBA). D’autres réglementations spécifiques à l’État sont également en place ou en cours de développement. 

Dans le monde entier, il peut s’agir d’exemples supplémentaires, notamment BDSG (national RGPD Implementation Act), le Brésil (Data Protection Act), et bien d’autres.

## <a name="regulation-mapping-to-microsoft-365-technical-control-categories"></a>Mappage de la réglementation aux catégories de contrôle technique Microsoft 365

De nombreuses réglementations liées à la confidentialité des données comportent des exigences qui se chevauchent, c’est pourquoi vous devez connaître les réglementations auxquelles elles sont soumises avant de développer un modèle de contrôle technique. 

Pour référence ultérieure dans les Articles de cette solution globale, ce tableau fournit des extraits d’un échantillon de la réglementation sur la confidentialité des données. 

| Réglementations | Article/section | Quiz | Catégories de contrôle technique applicables |
|:-------|:-----|:-------|:-------|
| RGPD | Article 5 (1) (f) | Les données personnelles doivent être traitées de manière à garantir une sécurité appropriée des données personnelles, y compris la protection contre le traitement non autorisé ou illégal et contre la perte accidentelle, la destruction ou les dégâts, à l’aide de mesures techniques ou organisationnelles appropriées (« intégrité et confidentialité ».  |  Tous les <br> Identité <br> Appareil <br> Protection contre les menaces <br> Protéger les informations <br> Gestion des informations <br> Découvrir et répondre |
|  | Article (32) (1) (a) | Tenant compte de l’état de la technique, des coûts de mise en œuvre et de la nature, de l’étendue, du contexte et des objectifs du traitement, ainsi que des risques de probabilité et de gravité variables pour les droits et les libertés des personnes physiques, le responsable du traitement et le transformateur mettent en œuvre les mesures techniques et organisationnelles appropriées pour garantir un niveau de sécurité approprié pour le risque. , y compris, entre autres, selon les besoins : (a) l’pseudonymage et le chiffrement des données personnelles. | Protéger les informations |
|  | Article (13) (2) (a) | "... le contrôleur doit, au moment de l’obtention des données personnelles, fournir aux personnes concernées les informations supplémentaires suivantes nécessaires pour assurer un traitement équitable et transparent : (a) la période pendant laquelle les données personnelles seront stockées ou, si cela n’est pas possible, les critères utilisés pour déterminer cette période. | Gestion des informations |
|  | Article (15) (1) (e) | La personne concernée a le droit d’obtenir de la part du responsable de la confirmation du contrôleur si les données personnelles le concernant sont traitées, et, si c’est le cas, l’accès aux données personnelles et les informations suivantes : (e) l’existence du droit de demander la rectification ou l’effacement des données personnelles ou la limitation du traitement des données personnelles concernant la personne concernée ou l’objet de ce traitement. | Découvrir et répondre |
| LGPD | Article 46 | Les agents de traitement adoptent des mesures de sécurité, techniques et administratives capables de protéger les données personnelles des accès non autorisés et des situations fortuites ou illicites de destruction, de perte, de modification, de communication ou tout type de traitement incorrect ou illégal. | Protéger les informations <br> Gestion des informations <br> Découvrir et répondre|
|  | Article 48 | Le responsable du traitement doit informer l'autorité nationale et la personne concernée de la survenance d'un incident de sécurité susceptible de créer des risques ou des dommages importants pour les personnes concernées. | Découvrir et répondre |
| HIPPA-HI-TECH | 45 CFR 164.312(e)(1) | Implémenter des mesures de sécurité techniques pour se prémunir contre l'accès non autorisé aux informations médicales électroniques protégées qui sont transmises sur un réseau de communication électronique. | Protéger les informations |
|  | 45 C.F.R. 164.312(e)(2)(ii) | Implémenter un mécanisme de chiffrement des informations médicales électroniques protégées chaque fois que cela est jugé approprié. | Protéger les informations |
|  | 45 CFR 164.312(c)(2) | Mettre en œuvre des mécanismes électroniques pour confirmer que les informations médicales électroniques protégées n'ont pas été altérées ou détruites de manière non autorisée. | Gestion des informations |
|  | 45 CFR 164.316(b)(1)(i) | Si une action, une activité ou une évaluation est requise par cette sous-partie pour être documentée, conservez un enregistrement écrit (qui peut être électronique) de l’action, de l’activité ou de l’évaluation | Gestion des informations |
|  | 45 CFR 164.316(b)(1)(ii) | Conserver la documentation requise par le paragraphe (b)(1) du présent article pendant 6 ans à compter de la date de sa création ou de la dernière date à laquelle elle a été en vigueur, si celle-ci est postérieure. | Gestion des informations |
|  | 45 C.F.R. 164.308(a)(1)(ii)(D) | Mettre en œuvre des procédures pour examiner régulièrement les enregistrements de l’activité du système d’information, tels que les journaux d’audit, les rapports d’accès et les rapports de suivi des incidents de sécurité | Découvrir et répondre |
|  | 45 C.F.R. 164.308(a)(6)(ii) | Identifier et répondre aux incidents de sécurité connus ou suspects ; atténuer, dans la mesure du possible, les effets néfastes des incidents de sécurité qui sont connus de l'entité couverte ou de l'associé commercial ; et documenter les incidents de sécurité et leurs résultats. | Découvrir et répondre |
|  | 45 C.F.R. 164.312(b) | Mettre en œuvre des mécanismes de matériel, de logiciel et de procédure qui enregistrent et examinent l’activité dans les systèmes d’information qui contiennent ou utilisent des informations d’intégrité électronique protégées. | Découvrir et répondre |
| CCPA | 1798.105(c) | Une entreprise qui reçoit une demande vérifiable d’un consommateur pour supprimer les informations personnelles de l’utilisateur en vertu de la subdivision (a) de cette section doit supprimer les informations personnelles du consommateur de ses enregistrements et inviter les prestataires de services à supprimer les informations personnelles de l’utilisateur de leurs enregistrements. | Découvrir et répondre |
|  | 1798.105(d) | (exceptions à 1798.105 (c) <br> Un prestataire de services ou un fournisseur de services ne doit pas être tenu de se conformer à la demande d’un consommateur pour supprimer les informations personnelles du consommateur s’il est nécessaire que le prestataire de services ou de service gère les informations personnelles du consommateur afin de : (reportez-vous au règlement actuel pour plus d’informations). | Découvrir et répondre |
|||||

>[!Important]
>Il ne s’agit pas d’une liste exhaustive. Consultez le [Gestionnaire de conformité](../compliance/compliance-manager.md) ou votre conseiller juridique ou conformité pour plus d’informations sur l’applicabilité des sections citées aux catégories de contrôles techniques répertoriées.
>

## <a name="knowing-your-data"></a>Connaître vos données

Quelle que soit la réglementation sur laquelle vous êtes soumis, lorsque différents types de données utilisateur à l’intérieur et à l’extérieur de votre organisation interagissent avec vos systèmes sont tous des facteurs importants susceptibles d’avoir un impact sur votre stratégie globale de protection des données personnelles, sous réserve des réglementations sectorielles et gouvernementales qui s’appliquent à votre organisation. Cela inclut l’emplacement de stockage des données personnelles, le type et la partie de ces données, ainsi que les circonstances dans lesquelles elles ont été collectées.
 
![Connaître vos données : de quel type il s’agit, et quelle est sa partie, ainsi que les circonstances dans lesquelles il a été collecté.](../media/information-protection-deploy-assess/information-protection-deploy-assess-knowing-data.png)

### <a name="data-portability"></a>Portabilité des données 

Les données se déplacent également à mesure qu’elles sont traitées, affinées et que d’autres versions en sont dérivées. Une capture instantanée initiale n’est jamais suffisante. Il doit s’agir d’un processus continu pour connaître vos données. Cela représente l’un des plus grands défis pour les grandes organisations qui gèrent des volumes importants de données personnelles. Les organisations qui ne traitent pas du problème de « connaissance de vos données » pourraient potentiellement se terminer par des risques très élevés et des amendes possibles d’organismes de réglementation.

![Le cycle de vie des données](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-lifecycle.png)
 
### <a name="where-the-personal-data-is"></a>Où les données personnelles sont

Pour répondre aux réglementations en matière de confidentialité des données, vous ne pouvez pas compter sur les notions générales de l’endroit où vous pensez que des données personnelles peuvent exister, maintenant ou ultérieurement. Les réglementations sur la confidentialité des données exigent que les organisations prouvent qu’elles connaissent l’évolution continue des données personnelles. Il est donc important de prendre une capture instantanée initiale de toutes vos sources de données afin de stocker éventuellement des informations personnelles, notamment votre environnement Microsoft 365, et d’établir des mécanismes de surveillance et de détection en cours.

Si vous n’avez pas encore évalué votre disponibilité et tous les risques globaux associés à la réglementation en matière de confidentialité des données, utilisez l’infrastructure en trois étapes suivante pour commencer. 

![Étapes permettant d’évaluer la disponibilité et les risques globaux associés aux réglementations en matière de confidentialité des données](../media/information-protection-deploy-assess/information-protection-deploy-assess-grid.png)

>[!Note]
>Cet article et son contenu ne sont pas destinés à remplacer des services de Conseil juridiques. Il fournit simplement des conseils de base et des liens vers des outils qui peuvent vous aider lors des premières étapes de votre évaluation.
>
 
## <a name="step-1-develop-a-foundational-understanding-of-your-organizations-personal-data-scenarios"></a>Étape 1 : développer une compréhension de base des scénarios de données personnelles de votre organisation 

Vous devez évaluer l’exposition au risque de confidentialité des données en fonction du type de données personnelles gérées actuellement, de son emplacement de stockage, des contrôles de protection qui y sont associés, de la gestion du cycle de vie et des personnes qui y ont accès. 

Comme point de départ, il est important d’inventorier les types de données personnelles présentes dans votre environnement Microsoft 365. Utilisez les catégories suivantes :

- Données sur les employés requises pour effectuer les fonctions professionnelles quotidiennes
- Données de l’Organisation concernant ses clients professionnels, ses partenaires et d’autres relations dans le scénario B2B (Business-to-Business)
- Données de l’Organisation concernant les consommateurs qui fournissent des informations aux services en ligne gérés par l’organisation dans le scénario B2C (Business-to-Customer)

Voici un exemple des différents types de données pour les services d’une organisation standard.

![Types de données personnelles](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-types.png)

La plupart des données personnelles soumises au Règlement sur la confidentialité des données sont généralement collectées et stockées en dehors de Microsoft 365. Toutes les données personnelles d’applications Web ou mobiles destinées au consommateur doivent avoir été exportées de ces applications vers Microsoft 365 afin d’être soumises à un examen de confidentialité des données au sein de Microsoft 365. 

Votre exposition à la confidentialité des données dans Microsoft 365 peut être plus limitée par rapport à vos applications Web et à vos systèmes CRM, que cette solution ne permet pas de résoudre.

Il est également important de réfléchir aux défis courants suivants en matière de conformité de confidentialité des données lors de l’évaluation de votre profil de risque :

 - **Distribution de données personnelles.** Quelle est la dispersion des informations sur un sujet donné ? Est-il suffisamment connu pour convaincre les organismes de réglementation que des contrôles corrects sont en place ? Est-il possible d’examiner et de résoudre le problème si nécessaire ?
- **Protection contre l’exfiltration.** Comment protégez-vous les données personnelles d’un type ou d’une source donnée contre toute compromission et comment y répondre ?
- **Protection contre les risques.** Quels sont les mécanismes de protection des informations appropriés par rapport au risque et comment maintenir la continuité et la productivité de l’entreprise et réduire l’impact de l’utilisateur final si l’intervention de l’utilisateur final est nécessaire ? Par exemple, la classification manuelle ou le chiffrement doivent-ils être utilisés ?
- **Conservation des données personnelles.** Combien de temps les informations contenant des données personnelles doivent-elles être conservées pour des raisons professionnelles valides et comment éviter les anciennes pratiques de conservation permanente, avec des besoins de rétention pour la continuité des opérations ?
- **Gestion des demandes des personnes concernées par les données.** Quels sont les mécanismes qui seront nécessaires pour gérer les demandes des personnes concernées par les données (DSR) et les actions correctives, telles que l’anonymisation, la biffure et la suppression ?
- **Surveillance et création de rapports en cours.** Quels types de techniques de surveillance quotidienne, d’enquête et de création de rapports sont disponibles pour les différents types de données et sources ?
- **Limitations relatives au traitement des données.** Existe-t-il des limitations de l’utilisation des données pour les informations collectées ou stockées via ces méthodes que l’organisation doit refléter dans les contrôles de confidentialité ? Par exemple, les engagements que les données personnelles ne seront pas utilisées par le personnel du service des ventes peuvent obliger votre organisation à mettre en place des mécanismes pour empêcher le transfert ou le stockage de ces informations dans les systèmes associés à l’Organisation des ventes.

### <a name="employee-data-required-to-carry-out-day-to-day-business-functions"></a>Données sur les employés requises pour effectuer les fonctions professionnelles quotidiennes

Les organisations par nature doivent collecter des données sur les employés à des fins d’identité électronique et de RH, sous réserve de leurs accords avec les employés. Tant qu’une personne travaille pour une société, il ne s’agit généralement pas d’un problème. L’organisation peut souhaiter mettre en place des mécanismes pour empêcher les acteurs malveillants d’exposer ou de fuir des données personnelles d’un employé. 

Si une personne quitte une entreprise, les organisations ont généralement des processus, des procédures, ainsi que des calendriers de rétention et de suppression permettant de supprimer des comptes d’utilisateur, de désactiver des boîtes aux lettres et des lecteurs personnels, et de modifier l’état des employés comme les systèmes de ressources humaines. Pour les situations dans lesquelles un litige est impliqué, un employé ou une autre partie à une enquête juridique peut avoir des raisons valables pour obtenir des informations sur les données personnelles stockées dans les systèmes de l’organisation. Dans certains cas, cette partie peut demander que ces données soient supprimées ou anonymes. 

Pour répondre à ces besoins, les organisations doivent disposer de processus et de procédures en place qui répondent aux besoins de prévention, de détective et de réparation, afin de faciliter ces demandes, en notant que certaines informations relatives à un employé peuvent être raisonnablement considérées comme cruciales pour la continuité de l’activité. Par exemple, les informations qu’une personne a créé un fichier ou effectué une fonction. 

>[!Note]
>Pour les techniques d’enquête et de correction des données personnelles dans Microsoft 365, consultez l' [article Monitor and respond](information-protection-deploy-monitor-respond.md). Vous pouvez également utiliser des schémas de protection et de classification automatisés pour vous assurer que les données personnelles sont contrôlées au sein de l’organisation et empêcher qu’elles ne quittent l’organisation dans des situations d’acteur malveillant. Pour plus d’informations, consultez l’article relatif à la [protection des informations](information-protection-deploy-protect-information.md) .
>
 
### <a name="data-the-organization-has-about-its-business-customers-in-the-b2b-scenario"></a>Données de l’Organisation concernant ses clients professionnels dans le scénario B2B

La collecte des informations B2B est également un véritable défi, car votre organisation peut avoir besoin de conserver des enregistrements des noms de clients et des transactions dans ses différents systèmes à des fins de continuité d’activité, tout en protégeant ces informations des infiltrations involontaires ou malveillantes. Comme les données des employés, les organisations doivent disposer de stratégies, de procédures et de contrôles techniques en place pour protéger ces données, ainsi que leur âge en fonction des calendriers de rétention et de suppression définis. 

En règle générale, les contrats avec les clients externes, les partenaires et les autres entités avec lesquelles l’organisation travaille, auront accès à la langue de traitement de ces données, y compris la protection, la rétention et la suppression, pendant et après que l’entité a une relation avec l’organisation. 

### <a name="data-the-organization-has-about-consumers-who-provide-information-to-online-services-that-the-organization-manages-in-the-b2c-scenario"></a>Données de l’Organisation concernant les consommateurs qui fournissent des informations aux services en ligne gérés par l’organisation dans le scénario B2C

Cette catégorie s’intéresse à la confidentialité des données, grâce à de nombreuses instances publiques de fuite de données client. Cela peut être intentionnel, comme un tiers sous contrat pour le fournisseur, ou involontaire, tel qu’un exfiltration par un acteur malveillant. La protection des données grand public est l’une des principales raisons pour lesquelles l’UE et d’autres ont agi à ces réglementations. Les réglementations de confidentialité telles que RGPD et CCPA nécessitent que vous planifiiez les opérations suivantes :

- Listes de vérification des [plans d’action](../compliance/gdpr-action-plan.md) et de préparation de la [responsabilité](../compliance/gdpr-arc-office365.md)
- [Analyses d’impact sur la protection des données](../compliance/gdpr-data-protection-impact-assessments.md)
- [Notifications de violation](../compliance/gdpr-breach-office365.md)
- [Demandes des personnes concernées](../compliance/gdpr-dsr-office365.md)

Si votre organisation n’effectue pas beaucoup de collecte de données de grand public, cette catégorie peut être moins problématique. Toutefois, vous devrez peut-être continuer à passer en revue les processus décrits dans les articles suivants pour assurer la conformité.

### <a name="step-1-summary"></a>Étape 1-Résumé

Comprendre votre exposition aux risques et le règlement sur la confidentialité des données est une première étape importante qui repose sur une bonne compréhension des scénarios de données personnelles de votre organisation.

Si vous n’avez pas de données personnelles de la part des utilisateurs dans votre environnement Microsoft 365 ou si elles sont confinées à certaines parties de l’environnement et que la nécessité d’un contrôle technique est déterminée par le fait qu’il existe des données de type consommateur, il se peut que le contrôle technique ne doive être utilisé que dans des parties à haut risque de l’environnement, pas partout.

Tant qu’une organisation externe ou une recommandation de jeu de contrôles standard, par exemple du gestionnaire de conformité dans Microsoft 365, peut vous aider à informer votre stratégie de contrôle, votre choix d’implémentation doit être piloté par la sensibilisation aux stocks de données pour quantifier votre exposition aux risques réels.

La plupart des organisations auront une certaine exposition à l’un des scénarios ci-dessus. Une approche holistique de l’évaluation est importante.

## <a name="step-2-assess-your-readiness-for-complying-with-data-privacy-regulations"></a>Étape 2 : évaluer votre préparation pour respecter les réglementations en matière de confidentialité des données

Bien que spécifiques à RGPD, les questions posées par l’outil d’évaluation gratuit de [Microsoft RGPD](https://www.microsoft.com/cyberassessment/en/gdpr/uso365) permettent de mieux comprendre la disponibilité globale de votre confidentialité des données. 

Les organisations soumises à d’autres réglementations sur la confidentialité des données, telles que CCPA aux États-Unis ou au Brésil LGPD, peuvent également tirer parti de l’inventaire de ses dispositions en raison du chevauchement des dispositions avec le RGPD.

L’évaluation de RGPD comprend les sections suivantes :

| Section | Description |
|:-------|:-----|
| Gouvernance | <ol><li>Votre politique de confidentialité indique-t-elle explicitement les informations de données traitées ? </li><li>Exécutez-vous régulièrement des analyses d’impact sur la confidentialité (PIA) ? </li><li> Utilisez-vous un outil pour gérer les informations personnelles (PI) ? </li><li> Disposez-vous d’une autorité légale pour mener des activités commerciales à l’aide de données PI sur un individu donné ? Effectuez-vous le suivi de l’autorisation pour les données ? </li><li> Effectuez-vous le suivi, l’implémentation et la gestion des contrôles d’audit ? Surveillez-vous les fuites de données ? </li></ol>|
| Suppression et notification | <ol><li>Donnez-vous des instructions explicites sur la façon dont les données des utilisateurs sont accessibles ? </li><li> Disposez-vous de processus documentés en place pour gérer le consentement d’exclusion ? </li><li> Disposez-vous d’un processus de suppression automatisé pour les données ? </li><li>   Avez-vous un processus de validation de l’identité lors de l’implication d’un client ? </li></ol>|
| Limitation des risques et sécurité des informations | <ol><li>Utilisez-vous des outils pour analyser les données non structurées ? </li><li>Tous les serveurs sont-ils à jour et utilisez-vous des pare-feu pour les protéger ? </li><li>Exécutez-vous des sauvegardes régulières de vos serveurs ? </li><li>Surveillez-vous activement les fuites de données ? </li><li>Chiffrez-vous vos données au repos et en transmission ? </li></ol>|
| Gestion des stratégies | <ol><li>Comment gérer vos règles d’entreprise de liaison (BCRs) ? </li><li>Effectuez-vous le suivi de l’autorisation pour les données ? </li><li> Sur une balance de 1 à 5, 5 entièrement couverte, vos contrats couvrent-ils les classifications de données et les exigences en matière de gestion ? </li><li>Avez-vous testé régulièrement un plan de réponse aux incidents ? </li><li>Quelle stratégie utilisez-vous pour gérer Access ? </li></ol>|
|||
 
## <a name="step-3-identify-sensitive-information-types-that-occur-in-your-microsoft-365-environment"></a>Étape 3 : identifier les types d’informations sensibles qui se produisent dans votre environnement Microsoft 365. 

Cette étape implique l’identification de types d’informations sensibles particuliers soumis à des contrôles réglementaires spécifiques, ainsi que de l’occurrence de ces types d’informations sensibles dans votre environnement Microsoft 365. 

La recherche de contenu dans votre environnement contenant des personnes personnelles peut être une tâche colossale, qui impliquait auparavant une combinaison de la recherche de conformité, de la découverte électronique, de la découverte électronique avancée, de la fonctionnalité DLP et de l’audit. 

Avec la nouvelle solution de **classification des données** dans le centre d’administration de la conformité Microsoft, il est devenu beaucoup plus facile avec la fonctionnalité [Explorateur de contenu](../compliance/data-classification-content-explorer.md) , qui fonctionne avec des types d’informations sensibles intégrés ou personnalisés, y compris ceux liés aux données personnelles.
 
### <a name="sensitive-information-types"></a>Types d’informations sensibles

Le centre d’administration de la conformité Microsoft est préchargé avec plus de 100 types d’informations sensibles, dont la plupart sont liées à l’identification et à la localisation des données personnelles. Ces types d’informations sensibles intégrés peuvent vous aider à identifier et à protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, et bien plus encore, en fonction des modèles définis par une expression régulière (Regex) ou une fonction. Pour en savoir plus, voir [Éléments recherchés par les types d’informations sensibles](../compliance/what-the-sensitive-information-types-look-for.md).

Si vous devez identifier et protéger un type d’éléments sensibles spécifique à une organisation ou régional, tel qu’un format personnalisé pour les ID d’employé, ou d’autres informations personnelles non déjà couvertes par un type d’informations sensibles intégré, vous pouvez créer un type d’informations sensibles personnalisé à l’aide des méthodes suivantes : 

- PowerShell
- Règles personnalisées avec une correspondance de données exacte (EDM)
- Via l’interface utilisateur de l’administrateur du centre de conformité, comme indiqué dans l' [article utiliser le score de conformité et le gestionnaire de conformité](information-protection-deploy-compliance.md)

Vous pouvez également personnaliser un type d’informations sensibles intégré existant.

Pour plus d’informations, consultez les articles suivants :

- [Personnaliser un type d’informations sensibles intégré](../compliance/customize-a-built-in-sensitive-information-type.md)
- [Types d’informations sensibles personnalisés](../compliance/custom-sensitive-info-types.md)
- [Créer un type d’informations sensibles personnalisé dans le Centre de Conformité et Sécurité](../compliance/create-a-custom-sensitive-information-type.md)
- [Créer un type d’informations sensibles personnalisé dans l’interface PowerShell du Centre de sécurité et conformité](../compliance/create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Créez des types d’informations sensibles personnalisés à l’aide d’une classification Exact Data Match.](../compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)

### <a name="content-explorer"></a>Explorateur de contenu

Un outil important permettant de déterminer l’occurrence d’éléments sensibles dans votre environnement est le nouvel [Explorateur de contenu](../compliance/data-classification-content-explorer.md) dans le centre d’administration de la conformité Microsoft 365. Il s’agit d’un outil automatisé pour l’analyse initiale et continue de votre abonnement Microsoft 365 tout entier pour l’occurrence de types d’informations sensibles et l’affichage des résultats.
 
Le nouvel outil Explorateur de contenu vous permet d’identifier rapidement les emplacements des éléments sensibles dans votre environnement, en utilisant des types d’informations sensibles intégrés ou des éléments personnalisés. Cela peut impliquer la création d’un processus et la responsabilité de l’examen régulier de la présence et de l’emplacement des éléments sensibles.

Outre les autres étapes décrites dans cet article, cela fournit un point de départ pour identifier votre exposition des risques globaux, la disponibilité et l’emplacement des éléments sensibles à protéger grâce à la surveillance et à la configuration planifiées de Microsoft 365. 

### <a name="other-methods-to-identify-personal-data-in-your-environment"></a>Autres méthodes d’identification des données personnelles dans votre environnement

En plus de l’Explorateur de contenu, les organisations ont accès à la fonctionnalité de recherche de contenu pour produire des recherches personnalisées afin de trouver des données personnelles dans leur environnement, à l’aide de critères de recherche avancés et de filtres personnalisés.

[Cet article](../compliance/search-for-and-find-personal-data.md)fournit des instructions détaillées sur l’utilisation de la recherche de contenu pour la découverte des données personnelles. La recherche de contenu et les autres techniques de découverte sont également explorées dans [DSR pour RGPD et CCPA](../compliance/gdpr-dsr-office365.md#introduction-to-dsrs).

Des informations supplémentaires sur les techniques d’enquête et de correction pour les données personnelles dans Microsoft 365 sont fournies dans l' [article Monitor and respond](information-protection-deploy-monitor-respond.md).
