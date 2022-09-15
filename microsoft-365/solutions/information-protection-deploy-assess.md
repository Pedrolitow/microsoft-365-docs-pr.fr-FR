---
title: Évaluer les risques liés à la confidentialité des données et identifier les éléments sensibles avec Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 07/13/2020
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
description: Déterminez les réglementations relatives à la confidentialité des données, les scénarios pertinents, votre préparation et les types d’informations sensibles qui se trouvent dans votre environnement Microsoft 365.
ms.openlocfilehash: 8ce944c8caee3c89def04d7367efbd4f46bf51e7
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67730790"
---
# <a name="assess-data-privacy-risks-and-identify-sensitive-items-with-microsoft-365"></a>Évaluer les risques liés à la confidentialité des données et identifier les éléments sensibles avec Microsoft 365

L’évaluation des réglementations de confidentialité des données et des risques auxquels votre organisation est soumise est une première étape avant d’implémenter les actions d’amélioration associées, y compris les actions réalisables avec les fonctionnalités et services Microsoft 365.

## <a name="potentially-applicable-data-privacy-regulations"></a>Réglementations potentiellement applicables en matière de confidentialité des données

Pour obtenir une bonne référence sur le cadre réglementaire plus large pour les réglementations sur la confidentialité des données, consultez le portail d’approbation des [services Microsoft](https://servicetrust.microsoft.com/) et la [série d’articles sur le Règlement général sur la protection des données (RGPD](/compliance/regulatory/gdpr)). Passez également en revue les documents relatifs aux règlements que vous pouvez être soumis dans votre secteur d’activité ou région.

### <a name="gdpr"></a>RGPD

Le RGPD est le plus connu et le plus cité des réglementations sur la confidentialité des données. Il réglemente la collecte, le stockage, le traitement et le partage des données personnelles relatives à une personne physique identifiée ou identifiable résidant dans l’Union européenne (UE).

Conformément à l’article 4 du RGPD :

- « données personnelles » désigne toutes les informations relatives à une personne physique identifiée ou identifiable (« objet de données ») ; une personne physique identifiable est une personne qui peut être identifiée, directement ou indirectement, en particulier par référence à un identificateur tel qu’un nom, un numéro d’identification, des données d’emplacement, un identificateur en ligne ou à un ou plusieurs facteurs spécifiques à l’identité physique, physiologique, génétique, mentale, économique, culturelle ou sociale de cette personne naturelle.

### <a name="iso-27001"></a>ISO 27001

L’adhésion à d’autres normes comme ISO 27001 a également été reconnue par plusieurs autorités de surveillance européennes comme un proxy d’intention valide pour l’ensemble des personnes, des processus et du spectre technologique. Les normes qu’il spécifie se chevauchent et le respect des mécanismes de protection pilotés par iso-27001 peuvent être considérés comme un proxy répondant à certaines obligations en matière de confidentialité dans certaines circonstances.

### <a name="other-data-privacy-regulations"></a>Autres réglementations sur la confidentialité des données

D’autres réglementations importantes en matière de confidentialité des données spécifient également des exigences pour la gestion des données personnelles.

Dans le Estados Unidos, il s’agit notamment de la California Consumer Protection Act ([CCPA](/compliance/regulatory/ccpa-faq)), HIPAA-HITECH (Estados Unidos health care privacy act) et de la Graham Leach Bliley Act (GLBA). D’autres réglementations spécifiques à l’État sont également en place ou en cours de développement.

Dans le monde entier, d’autres exemples incluent la Loi d’implémentation du RGPD national (BDSG) allemande, la Loi sur la protection des données du Brésil (LGPD) et bien d’autres.

## <a name="regulation-mapping-to-microsoft-365-technical-control-categories"></a>Mappage de réglementation aux catégories de contrôle technique Microsoft 365

La plupart des réglementations relatives à la confidentialité des données ont des exigences qui se chevauchent. Vous devez donc comprendre les réglementations auxquelles elles sont soumises avant d’élaborer un schéma de contrôle technique.

Pour une référence ultérieure dans les articles de cette solution globale, ce tableau fournit des extraits d’un échantillonnage des réglementations relatives à la confidentialité des données.

|Règlement|Article/section|Extrait|Catégories de contrôle technique applicables|
|---|---|---|---|
|RGPD|Article 5(1)(f)|Les données personnelles doivent être traitées de manière à garantir une sécurité appropriée des données personnelles, notamment la protection contre le traitement non autorisé ou illégal et contre les pertes, destructions ou dommages accidentels, à l’aide de mesures techniques ou organisationnelles appropriées (« intégrité et confidentialité ».|(Tout) <br> Identité <br> Device <br> Protection contre les menaces <br> Protéger les informations <br> Gérer les informations <br> Découvrir et répondre|
||Article (32)(1)(a)|Compte tenu de l’état de l’art, des coûts de mise en œuvre et de la nature, de l’étendue, du contexte et des objectifs du traitement, ainsi que du risque de probabilité et de gravité variables pour les droits et libertés des personnes physiques, le contrôleur et le processeur mettent en œuvre des mesures techniques et organisationnelles appropriées pour garantir un niveau de sécurité adapté au risque,  y compris, entre autres, le cas échéant : (a) le pseudonyme et le chiffrement des données personnelles.|Protéger les informations|
||Article (13)(2)(a)|"... le contrôleur doit, au moment où les données personnelles sont obtenues, fournir à la personne concernée les informations supplémentaires suivantes nécessaires pour garantir un traitement équitable et transparent : (a) la période pendant laquelle les données personnelles seront stockées, ou si cela n’est pas possible, les critères utilisés pour déterminer cette période.|Gérer les informations|
||Article (15)(1)(e)|La personne concernée doit avoir le droit d’obtenir de la part du contrôleur la confirmation de l’existence ou non du traitement des données personnelles qui le concernent et, dans ce cas, de l’accès aux données personnelles et des informations suivantes : (e) l’existence du droit de demander au contrôleur la rectification ou l’effacement des données personnelles ou la restriction du traitement des données personnelles concernant la personne concernée ou de s’y opposer Traitement|Découvrir et répondre|
|LGPD|Article 46|Les agents de traitement doivent adopter des mesures de sécurité, techniques et administratives capables de protéger les données personnelles contre les accès non autorisés et les situations accidentelles ou illégales de destruction, de perte, de modification, de communication ou de tout type de traitement inapproprié ou illégal.|Protéger les informations <br> Gérer les informations <br> Découvrir et répondre|
||Article 48|Le responsable du traitement doit informer l'autorité nationale et la personne concernée de la survenance d'un incident de sécurité susceptible de créer des risques ou des dommages importants pour les personnes concernées.|Découvrir et répondre|
|HIPPA-HITECH|45 CFR 164.312(e)(1)|Implémenter des mesures de sécurité techniques pour se prémunir contre l'accès non autorisé aux informations médicales électroniques protégées qui sont transmises sur un réseau de communication électronique.|Protéger les informations|
||45 C.F.R. 164.312(e)(2)(ii)|Implémenter un mécanisme de chiffrement des informations médicales électroniques protégées chaque fois que cela est jugé approprié.|Protéger les informations|
||45 CFR 164.312(c)(2)|Implémenter des mécanismes électroniques pour corroborer que les informations médicales protégées électroniques n’ont pas été modifiées ou détruites de manière non autorisée.|Gérer les informations|
||45 CFR 164.316(b)(1)(i)|Si ce sous-composant doit documenter une action, une activité ou une évaluation, conservez un enregistrement écrit (qui peut être électronique) de l’action, de l’activité ou de l’évaluation.|Gérer les informations|
||45 CFR 164.316(b)(1)(ii)|Conserver la documentation requise par le paragraphe (b)(1) du présent article pendant 6 ans à compter de la date de sa création ou de la dernière date à laquelle elle a été en vigueur, si celle-ci est postérieure.|Gérer les informations|
||45 C.F.R. 164.308(a)(1)(ii)(D)|Implémenter des procédures pour examiner régulièrement les enregistrements de l’activité du système d’information, tels que les journaux d’audit, les rapports d’accès et les rapports de suivi des incidents de sécurité|Découvrir et répondre|
||45 C.F.R. 164.308(a)(6)(ii)|Identifier et répondre aux incidents de sécurité connus ou suspects ; atténuer, dans la mesure du possible, les effets néfastes des incidents de sécurité qui sont connus de l'entité couverte ou de l'associé commercial ; et documenter les incidents de sécurité et leurs résultats.|Découvrir et répondre|
||45 C.F.R. 164.312(b)|Implémentez des mécanismes matériels, logiciels et procéduraux qui enregistrent et examinent les activités dans les systèmes d’information qui contiennent ou utilisent des informations de santé protégées électroniquement.|Découvrir et répondre|
|ACCP|1798.105(c)|Une entreprise qui reçoit une demande vérifiable d’un consommateur de supprimer les informations personnelles du consommateur conformément à la sous-section (a) de cette section doit supprimer les informations personnelles du consommateur de ses dossiers et demander à tous les fournisseurs de services de supprimer les informations personnelles du consommateur de ses dossiers.|Découvrir et répondre|
||1798.105(d)|(exceptions à 1798.105(c) <br> Une entreprise ou un fournisseur de services ne doit pas être tenu de se conformer à la demande d’un consommateur de supprimer les informations personnelles du consommateur s’il est nécessaire que l’entreprise ou le fournisseur de services conserve les informations personnelles du consommateur afin de : (reportez-vous au règlement actuel pour plus d’informations).|Découvrir et répondre|
|||||

> [!IMPORTANT]
> Il ne s’agit pas d’une liste exhaustive. Reportez-vous au [Gestionnaire de conformité](../compliance/compliance-manager.md) ou à votre conseiller juridique ou de conformité pour plus d’informations sur l’applicabilité des sections citées dans les catégories de contrôle technique répertoriées.

## <a name="knowing-your-data"></a>Connaître vos données

Quels que soient les règlements auxquels vous êtes soumis, où différents types de données utilisateur à l’intérieur et à l’extérieur de votre organisation interagissent avec vos systèmes sont tous des facteurs importants susceptibles d’avoir un impact sur votre stratégie globale de protection des données personnelles, sous réserve des réglementations du secteur et du gouvernement qui s’appliquent à votre organisation. Cela inclut l’emplacement de stockage des données personnelles, leur type et leur quantité, et dans quelles circonstances elles ont été collectées.

![Connaissance de vos données : de quel type il s’agit, de leur quantité et des circonstances dans lesquelles elles ont été collectées.](../media/information-protection-deploy-assess/information-protection-deploy-assess-knowing-data.png)

### <a name="data-portability"></a>Portabilité des données

Les données se déplacent également au fil du temps à mesure qu’elles sont traitées, affinées et que d’autres versions en sont dérivées. Un instantané initial ne suffit jamais. Il doit y avoir un processus continu pour connaître vos données. Cela représente l’un des plus grands défis pour les grandes organisations qui gèrent des volumes significatifs de données personnelles. Les organisations qui ne traitent pas le problème de « connaître vos données » pourraient potentiellement se retrouver avec des risques très élevés et des amendes potentielles de la part des organismes de réglementation.

![Cycle de vie des données.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-lifecycle.png)

### <a name="where-the-personal-data-is"></a>Où se trouvent les données personnelles

Pour répondre aux réglementations en matière de confidentialité des données, vous ne pouvez pas vous appuyer sur des notions générales d’endroit où vous pensez que des données personnelles peuvent exister, maintenant ou à l’avenir. Les réglementations sur la confidentialité des données exigent que les organisations prouvent qu’elles savent où se trouvent les données personnelles en permanence. Il est donc important de prendre une capture instantanée initiale de toutes vos sources de données pour le stockage possible d’informations personnelles, y compris votre environnement Microsoft 365, et d’établir des mécanismes de surveillance et de détection en cours.

Si vous n’avez pas encore évalué votre état de préparation global et les risques associés aux réglementations sur la confidentialité des données, utilisez l’infrastructure en 3 étapes suivante pour commencer.

![Étapes d’évaluation de votre préparation globale et des risques associés aux réglementations sur la confidentialité des données.](../media/information-protection-deploy-assess/information-protection-deploy-assess-grid.png)

> [!NOTE]
> Cet article et son contenu ne sont pas destinés à prendre la place des services de conseil juridique. Il fournit simplement des conseils de base et des liens vers des outils qui peuvent être d’aide dans les premières étapes de votre évaluation.

## <a name="step-1-develop-a-foundational-understanding-of-your-organizations-personal-data-scenarios"></a>Étape 1 : Développer une compréhension fondamentale des scénarios de données personnelles de votre organisation

Vous devez évaluer l’exposition au risque de confidentialité des données en fonction du type de données personnelles qu’elle gère actuellement, de l’emplacement où elles sont stockées, des contrôles de protection qui y sont placés, de la façon dont leur cycle de vie est géré et de la personne qui y a accès.

À titre de point de départ, il est important d’inventorier les types de données personnelles qui existent dans votre environnement Microsoft 365. Utilisez les catégories suivantes :

- Données des employés nécessaires pour effectuer des fonctions métier quotidiennes
- Données que l’organisation a sur ses clients professionnels, ses partenaires et d’autres relations dans le scénario B2B
- Les données de l’organisation concernant les consommateurs qui fournissent des informations à serviços online que l’organisation gère dans le scénario B2C (Business-to-Customer)

Voici un exemple des différents types de données pour les services typiques d’une organisation.

![Types de données personnelles.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-types.png)

La plupart des données personnelles soumises à la réglementation sur la confidentialité des données sont généralement collectées et stockées en dehors de Microsoft 365. Toutes les données personnelles provenant d’applications web ou mobiles destinées aux consommateurs doivent avoir été exportées de ces applications vers Microsoft 365 afin d’être soumises à l’examen de la confidentialité des données dans Microsoft 365.

Votre exposition à la confidentialité des données dans Microsoft 365 peut être plus limitée par rapport à vos applications web et systèmes CRM, que cette solution ne traite pas.

Il est également important de réfléchir aux défis courants de conformité à la confidentialité des données suivants lors de l’évaluation de votre profil de risque :

- **Distribution des données personnelles.** À quel point les informations sur un sujet donné sont-ils dispersées ? Est-il suffisamment connu pour convaincre les organismes de réglementation que des contrôles appropriés sont en place? Peut-il être examiné et corrigé si nécessaire ?
- **Protection contre l’exfiltration.** Comment protéger les données personnelles d’un type ou d’une source donné contre la compromission et comment y répondre si c’était le cas ?
- **Protection et risque.** Quels sont les mécanismes de protection des informations appropriés par rapport au risque et comment maintenir la continuité et la productivité de l’entreprise et réduire l’impact de l’utilisateur final si une intervention de l’utilisateur final est nécessaire ? Par exemple, faut-il utiliser la classification manuelle ou le chiffrement ?
- **Conservation des données personnelles.** Combien de temps les informations contenant des données personnelles doivent-elles être conservées pour des raisons commerciales valides et comment éviter les pratiques de conservation définitive passées, en équilibre avec les besoins de rétention pour la continuité de l’activité ?
- **Gestion des demandes de personnes concernées par les données.** Quels mécanismes seront nécessaires pour gérer les demandes de personnes concernées et toutes les actions correctives, telles que l’anonymisation, la réinitialisation et la suppression ?
- **Surveillance et création de rapports en continu.** Quel type de techniques quotidiennes de surveillance, d’investigation et de création de rapports sont disponibles pour les différents types et sources de données ?
- **Limitations du traitement des données.** Existe-t-il des limitations sur l’utilisation des données pour les informations collectées ou stockées par le biais de ces méthodes que l’organisation doit refléter dans les contrôles de confidentialité ? Par exemple, les engagements que les données personnelles ne seront pas utilisées par le personnel des ventes peuvent obliger votre organisation à mettre en place des mécanismes pour empêcher le transfert ou le stockage de ces informations dans les systèmes associés à l’organisation commerciale.

### <a name="employee-data-required-to-carry-out-day-to-day-business-functions"></a>Données des employés nécessaires pour effectuer des fonctions métier quotidiennes

Par nature, les organisations doivent collecter des données sur les employés à des fins d’identité électronique et de RH, sous réserve de ce qu’elles acceptent dans leurs contrats d’employés. Tant qu’une personne travaille pour une entreprise, ce n’est généralement pas un problème. L’organisation peut souhaiter mettre en place des mécanismes pour empêcher les acteurs malveillants d’exfiltration ou de fuite de données personnelles d’employés.

Si une personne quitte une entreprise, les organisations ont généralement des processus, des procédures et des planifications de rétention et de suppression pour la suppression de comptes d’utilisateurs, la désaffectation des boîtes aux lettres et des lecteurs personnels, et la modification de l’état des employés dans des éléments tels que les systèmes de ressources humaines. En cas de litige, un employé ou une autre partie à une enquête juridique peut avoir des raisons valables d’obtenir des informations sur les données personnelles stockées dans les systèmes de l’organisation. Dans certains cas, cette partie peut demander la suppression ou l’anonymisation de ces données.

Pour répondre à ces besoins, les organisations doivent disposer de processus et de procédures qui répondent aux besoins préventifs, de détection et de réparation afin de faciliter ces demandes, en notant que certaines informations sur un employé peuvent être considérées comme cruciales pour la continuité de l’activité. Par exemple, les informations qu’un individu a créées un fichier ou effectué une fonction.

> [!NOTE]
> Pour connaître les techniques d’investigation et de correction des données personnelles dans Microsoft 365, consultez [l’article de surveillance et de réponse](information-protection-deploy-monitor-respond.md). Vous souhaiterez peut-être également utiliser des schémas de classification et de protection automatisés pour vous assurer que les données personnelles sont contrôlées au sein de l’organisation, et empêcher qu’elles ne quittent l’organisation dans des situations d’acteur malveillant. Pour plus d’informations, consultez [l’article protéger les informations](information-protection-deploy-protect-information.md) .

### <a name="data-the-organization-has-about-its-business-customers-in-the-b2b-scenario"></a>Données de l’organisation concernant ses clients professionnels dans le scénario B2B

La collecte d’informations B2B est également un défi, car votre organisation peut avoir besoin de conserver des enregistrements des noms de clients et des transactions dans ses différents systèmes à des fins de continuité d’activité, tout en protégeant ces informations contre l’exfiltration accidentelle ou malveillante. À l’instar des données des employés, les organisations doivent avoir des stratégies, des procédures et des contrôles techniques en place pour protéger ces données, ainsi que les vieillir en fonction des planifications de rétention et de suppression définies.

En règle générale, les contrats avec des clients externes, des partenaires et les autres entités avec lesquelles l’organisation fait affaire ont un langage traitant de la gestion de ces données, notamment la protection, la rétention et la suppression pendant et après que l’entité a une relation avec l’organisation.

### <a name="data-the-organization-has-about-consumers-who-provide-information-to-online-services-that-the-organization-manages-in-the-b2c-scenario"></a>Données de l’organisation sur les consommateurs qui fournissent des informations à serviços online que l’organisation gère dans le scénario B2C

Cette catégorie est celle à laquelle la plupart des personnes pensent pour la confidentialité des données, en raison de nombreuses instances publiques de fuite de données client. Cela peut être intentionnel, tel qu’un tiers sous contrat avec le fournisseur, ou involontaire, comme l’exfiltration par un acteur malveillant. La protection des données des consommateurs est l’une des principales raisons pour lesquelles l’UE et d’autres ont adopté ces réglementations. Les réglementations relatives à la confidentialité des données telles que le RGPD et le CCPA vous obligent à planifier les opérations suivantes :

- [Plans d’action](/compliance/regulatory/gdpr-action-plan) et [listes de vérification de préparation à la responsabilité](/compliance/regulatory/gdpr-arc-Office365)
- [Analyses d’impact sur la protection des données](/compliance/regulatory/gdpr-data-protection-impact-assessments)
- [Notifications de violation](/compliance/regulatory/gdpr-breach-Office365)
- [Demandes des personnes concernées](/compliance/regulatory/gdpr-dsr-Office365)

Si votre organisation ne collecte pas beaucoup de données directes à partir de consommateurs, cette catégorie peut être moins problématique. Toutefois, vous devrez peut-être passer par les processus décrits dans ces articles pour obtenir la conformité.

### <a name="step-1-summary"></a>Résumé de l’étape 1

Comprendre votre exposition aux risques et à la réglementation de la confidentialité des données est une première étape importante basée sur une compréhension fondamentale des scénarios de données personnelles de votre organisation.

Si vous n’avez pas de données personnelles provenant de consommateurs dans votre environnement Microsoft 365 ou qu’elles sont limitées à certaines parties de l’environnement et que la nécessité d’un contrôle technique est fondée sur l’exposition des données de type consommateur, ce contrôle technique ne peut être utilisé que dans des parties à haut risque de l’environnement, pas partout.

Bien qu’une recommandation d’organisation externe ou d’ensemble de contrôles standard, telle que le Gestionnaire de conformité dans Microsoft 365, puisse aider à orienter votre stratégie de contrôle, votre choix d’implémentation doit être piloté par la sensibilisation à l’inventaire des données pour quantifier votre exposition réelle aux risques.

La plupart des organisations auront une certaine exposition à l’un des scénarios ci-dessus. Il est important d’adopter une approche holistique de l’évaluation.

## <a name="step-2-assess-your-readiness-for-complying-with-data-privacy-regulations"></a>Étape 2 : Évaluer votre préparation à la conformité aux réglementations en matière de confidentialité des données

Bien que spécifiques au RGPD, les questions posées dans [l’outil d’évaluation gratuit du RGPD Microsoft](https://clouddamcdnprodep.azureedge.net/gdc/1863571/original) constituent un bon point de départ pour comprendre votre préparation globale à la confidentialité des données.

Les organisations soumises à d’autres réglementations sur la confidentialité des données, telles que le CCPA dans le Estados Unidos ou le LGPD du Brésil, peuvent également tirer parti de l’inventaire de préparation de cet outil en raison du chevauchement des dispositions avec le RGPD.

L’évaluation du RGPD se compose des sections suivantes :

|Section|Description|
|:-------|:-----|
|Gouvernance|<ol><li>Votre politique de confidentialité indique-t-elle explicitement quelles informations de données sont traitées ? </li><li>Exécutez-vous régulièrement des évaluations d’impact sur la confidentialité ( PIA) ? </li><li> Utilisez-vous un outil pour gérer les informations personnelles (PI) ? </li><li> Disposez-vous d’un pouvoir juridique pour effectuer des activités à l’aide de données PI sur une personne donnée ? Effectuez-vous le suivi du consentement pour les données ? </li><li> Effectuez-vous le suivi, l’implémentation et la gestion des contrôles d’audit ? Surveillez-vous les fuites de données ? </li></ol>|
|Suppression et notification|<ol><li>Donnez-vous des instructions explicites sur la façon dont les données des utilisateurs sont accessibles ? </li><li> Avez-vous mis en place des processus documentés pour gérer le consentement de refus ? </li><li> Disposez-vous d’un processus de suppression automatisée des données ? </li><li> Avez-vous un processus pour valider l’identité lors de l’engagement avec un client ? </li></ol>|
|Atténuation des risques et sécurité des informations|<ol><li>Utilisez-vous des outils pour analyser des données non structurées ? </li><li>Tous les serveurs sont-ils à jour et tirez-vous parti des pare-feu pour les protéger ? </li><li>Exécutez-vous des sauvegardes régulières de vos serveurs ? </li><li>Surveillez-vous activement les fuites de données ? </li><li>Chiffrez-vous vos données au repos et en transmission ? </li></ol>|
|Gestion des stratégies|<ol><li>Comment gérez-vous vos règles d’entreprise de liaison (BCR) ? </li><li>Effectuez-vous le suivi du consentement pour les données ? </li><li> Sur une échelle de 1 à 5, 5 étant entièrement couverte, vos contrats couvrent-ils les classifications de données et les exigences de gestion ? </li><li>Avez-vous et testez-vous régulièrement un plan de réponse aux incidents ? </li><li>Quelle stratégie utilisez-vous pour gérer l’accès ? </li></ol>|
|||

## <a name="step-3-identify-sensitive-information-types-that-occur-in-your-microsoft-365-environment"></a>Étape 3 : Identifier les types d’informations sensibles qui se produisent dans votre environnement Microsoft 365

Cette étape implique l’identification de types d’informations sensibles particuliers soumis à des contrôles réglementaires spécifiques, ainsi que l’occurrence de ces types dans votre environnement Microsoft 365.

La recherche de contenu dans votre environnement contenant des données personnelles peut être une tâche formidable, impliquant auparavant une combinaison d’utilisation de la Recherche de conformité, eDiscovery, eDiscovery (Premium), DLP et audit.

Avec la nouvelle solution **de classification des données** dans le portail de conformité Microsoft Purview, cela est devenu beaucoup plus facile avec la fonctionnalité [Explorateur](../compliance/data-classification-content-explorer.md) de contenu, qui fonctionne avec des types d’informations sensibles intégrés ou personnalisés, y compris ceux liés aux données personnelles.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Le portail de conformité Microsoft Purview est pré-chargé avec plus de 100 types d’informations sensibles, la plupart liés à l’identification et à la localisation des données personnelles. Ces types d’informations sensibles intégrés peuvent aider à identifier et protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, etc., en fonction de modèles définis par une expression régulière (expression régulière) ou une fonction. Pour en savoir plus, voir [Éléments recherchés par les types d’informations sensibles](../compliance/sensitive-information-type-entity-definitions.md).

Si vous devez identifier et protéger un type d’éléments sensibles propre à l’organisation ou régional, tel qu’un format personnalisé pour les ID d’employé ou d’autres informations personnelles non déjà couvertes par un type d’informations sensibles intégré, vous pouvez créer un type d’informations sensibles personnalisé avec les méthodes suivantes :

- Centre de conformité et sécurité PowerShell
- Règles personnalisées avec correspondance exacte des données (EDM)
- Via le portail de conformité Microsoft 365 Purview, comme indiqué dans [l’article Utiliser le score de conformité et le Gestionnaire de conformité](information-protection-deploy-compliance.md)

Vous pouvez également personnaliser un type d’informations sensibles intégré existant.

Pour plus d’informations, consultez ces articles :

- [Personnaliser un type d’informations sensibles intégré](../compliance/customize-a-built-in-sensitive-information-type.md)
- [En savoir plus sur les types d’informations confidentielles](../compliance/sensitive-information-type-learn-about.md).
- [Créer un type d’informations sensibles personnalisé dans le Centre de Conformité et Sécurité](../compliance/create-a-custom-sensitive-information-type.md)
- [Créer un type d’informations sensibles personnalisé dans l’interface PowerShell du Centre de sécurité et conformité](../compliance/create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Créez des types d’informations sensibles personnalisés à l’aide d’une classification Exact Data Match.](/microsoft-365/compliance/sit-get-started-exact-data-match-based-sits-overview)

### <a name="content-explorer"></a>Explorateur de contenu

Un outil important qui permet de déterminer l’occurrence d’éléments sensibles dans votre environnement est le nouvel [Explorateur de contenu](../compliance/data-classification-content-explorer.md) dans le Centre d’administration Microsoft Purview. Il s’agit d’un outil automatisé pour l’analyse initiale et continue de l’ensemble de votre abonnement Microsoft 365 pour l’occurrence de types d’informations sensibles et l’affichage des résultats.

Le nouvel outil Explorateur de contenu vous permet d’identifier rapidement les emplacements des éléments sensibles dans votre environnement, à l’aide de types d’informations sensibles intégrés ou personnalisés. Cela peut impliquer l’établissement d’un processus et la responsabilité d’examiner régulièrement la présence et l’emplacement des éléments sensibles.

En plus des autres étapes mises en évidence dans cet article, cela constitue un point de départ pour identifier l’exposition globale au risque, la préparation et l’emplacement des éléments sensibles à protéger par le biais de la configuration et de la surveillance planifiées de Microsoft 365.

### <a name="other-methods-to-identify-personal-data-in-your-environment"></a>Autres méthodes pour identifier les données personnelles dans votre environnement

En plus de l’Explorateur de contenu, les organisations ont accès à la fonctionnalité De recherche de contenu pour produire des recherches personnalisées afin de rechercher des données personnelles dans leur environnement, à l’aide de critères de recherche avancés et de filtres personnalisés.

Des instructions détaillées sur l’utilisation de la recherche de contenu pour la découverte de données personnelles sont fournies dans [cet article](/compliance/regulatory/gdpr). La recherche de contenu et d’autres techniques de découverte sont également explorées dans [les DSR pour le RGPD et le CCPA](/compliance/regulatory/gdpr-dsr-Office365#introduction-to-dsrs).

Des informations supplémentaires sur les techniques d’investigation et de correction des données personnelles dans Microsoft 365 sont fournies dans [l’article de surveillance et de réponse](information-protection-deploy-monitor-respond.md).

> [!NOTE]
> Pour rechercher les informations sensibles que vous avez dans les fichiers stockés localement, reportez-vous à [Azure Information Protection](/azure/information-protection/quickstart-findsensitiveinfo).
