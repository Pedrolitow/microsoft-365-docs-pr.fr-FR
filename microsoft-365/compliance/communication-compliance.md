---
title: Conformité des communications
description: En savoir plus sur la conformité des communications dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 49b5491cb67f447bf8cca1d88aab807c1bf30624
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208386"
---
# <a name="communication-compliance-in-microsoft-365"></a>Conformité de la communication dans Microsoft 365

La conformité des communications fait partie de la nouvelle solution de risque initiée dans Microsoft 365 qui permet de réduire les risques de communication en vous aidant à détecter, capturer et prendre des mesures correctives pour les messages inappropriés dans votre organisation. Les stratégies prédéfinies et personnalisées vous permettent d’analyser les communications internes et externes des correspondances de stratégie pour qu’elles puissent être examinées par les relecteurs désignés. Les relecteurs peuvent analyser les e-mails analysés, Microsoft Teams, Yammer ou des communications tierces de votre organisation et prendre les mesures correctives appropriées pour s’assurer qu’elles sont conformes aux standards de messages de votre organisation.

Les stratégies de conformité des communications dans Microsoft 365 vous aident à surmonter de nombreux défis modernes associés à la conformité et aux communications internes et externes, notamment :

- Analyse des types croissants de canaux de communication
- Augmentation du volume des données de message
- Application réglementaire et risques d’amendes

Dans certaines organisations, le support informatique et le groupe de gestion de la conformité peuvent séparer les tâches. Microsoft 365 prend en charge la séparation entre la configuration de la conformité de la communication et la configuration des stratégies d’analyse des communications. Par exemple, le groupe informatique d’une organisation peut être responsable de la configuration des autorisations de rôle et des groupes afin de prendre en charge les stratégies de conformité de communication configurées et gérées par l’équipe de conformité de l’organisation.

Pour une vue d’ensemble rapide de la conformité de la communication, voir la vidéo relative à la détection d’un lieu de [travail harcèlement et à la conformité des communications dans microsoft 365,](https://youtu.be/z33ji7a7Zho) sur le [canal des mécanismes Microsoft](https://www.youtube.com/user/OfficeGarageSeries).

## <a name="scenarios-for-communication-compliance"></a>Scénarios de conformité de la communication

Les stratégies de conformité des communications peuvent vous aider à examiner les messages de votre organisation dans plusieurs zones de conformité importantes :

- **Stratégies d’entreprise**

    Les employés doivent respecter une utilisation acceptable, des normes éthiques et d’autres stratégies d’entreprise dans toutes leurs communications professionnelles. Les stratégies de conformité des communications peuvent détecter les correspondances de stratégie et vous aider à prendre des mesures correctives pour limiter ces types d’incidents. Par exemple, vous pouvez analyser les communications de l’employé au sein de votre organisation pour les ressources humaines potentielles, telles que le harcèlement ou l’utilisation d’un langage inapproprié ou choquant.

- **Gestion des risques**

    Les organisations sont responsables de toutes les communications distribuées au sein de leur infrastructure et des systèmes réseau d’entreprise. L’utilisation de stratégies de conformité des communications pour identifier et gérer les risques et les risques légaux potentiels peut vous aider à réduire les risques avant qu’ils puissent endommager les opérations de l’entreprise. Par exemple, vous pouvez analyser les messages de votre organisation pour les communications non autorisées concernant les projets confidentiels, tels que les acquisitions à venir, les fusions, les informations de résultats, les réorganisations ou les modifications apportées à l’équipe de leadership.

- **Conformité réglementaire**

    La plupart des organisations doivent se conformer à certains types de normes de conformité réglementaire dans le cadre de leurs procédures d’utilisation normales. Ces réglementations obligent souvent les organisations à mettre en place un certain type de processus de surveillance ou de supervision pour la messagerie appropriée pour leur secteur d’activité. La règle 3110 de l’autorité réglementaire du secteur financier (FINRA) est un excellent exemple d’une obligation pour les organisations de mettre en place des procédures de surveillance pour analyser les communications des employés et les types d’entreprises dans lesquelles elle s’engage. Un autre exemple peut être un besoin de passer en revue les communications avec des concessionnaires de courtiers dans votre organisation afin de se protéger contre le blanchiment potentiel, les opérations d’initiés, les opérations de collusion ou les actions de corruption. Les stratégies de conformité des communications peuvent aider votre organisation à répondre à ces exigences en fournissant un processus à l’analyse et à la création de rapports sur les communications d’entreprise. Pour plus d’informations sur la prise en charge des organisations financières, consultez [la rubrique Key Compliance and Security Considerations for US Bank and Capital Markets](../solutions/financial-services-secure-collaboration.md).

## <a name="new-enhancements"></a>Nouvelles améliorations

La conformité de la communication dans Microsoft 365 repose sur les fonctionnalités des [stratégies de surveillance dans Office 365](supervision-policies.md) avec plusieurs nouvelles améliorations :

- Modèles personnalisables intelligents
- Flux de travail de correction flexibles
- Informations exploitables

![Page d’accueil de la communication](../media/communication-compliance-home.png)

### <a name="intelligent-customizable-templates"></a>Modèles personnalisables intelligents

Les modèles personnalisables intelligents dans la conformité de la communication vous permettent d’appliquer une formation machine pour détecter intelligemment les violations de communication au sein de votre organisation.

- **Modèles préconfigurés personnalisables**: les nouveaux modèles de stratégie permettent de résoudre les risques de communication les plus courants. La création et la mise à jour de la stratégie initiale sont désormais plus rapides grâce à un langage choquant et choquant, à des informations sensibles et à des modèles de conformité réglementaire prédéfinis.
- **Nouvelle prise en charge de l’apprentissage automatique**: les [classifieurs](classifier-getting-started-with.md) de menace, de harcèlement et de virus intégrés contribuent à réduire les faux positifs dans les messages analysés, en enregistrant les temps de relecteurs pendant le processus d’enquête et de correction.
- **Générateur**de conditions amélioré : la configuration des conditions de stratégie est désormais rationalisée en une expérience unique et intégrée dans l’Assistant stratégie, ce qui réduit la confusion dans la façon dont les conditions sont appliquées aux stratégies.

### <a name="flexible-remediation-workflows"></a>Flux de travail de correction flexibles

Les flux de travail de correction intégrés vous permettent d’identifier rapidement les messages et d’agir sur ceux-ci à l’aide de correspondances de stratégie dans votre organisation. Les nouvelles fonctionnalités suivantes augmentent l’efficacité des activités d’enquête et de correction :

- **Flux de travail de correction flexible**: le nouveau flux de travail de correction vous permet d’agir rapidement sur les correspondances de stratégie, y compris les nouvelles options permettant de remonter les messages vers d’autres réviseurs et d’envoyer des notifications par courrier électronique aux utilisateurs avec des correspondances de stratégie.
- **Thème de conversation**: les messages sont maintenant regroupés visuellement par le message d’origine et tous les messages de réponse associés, ce qui vous offre un meilleur contexte lors de l’enquête et des actions correctives.
- **Mise en surbrillance des mots clés**: les conditions de la stratégie de correspondance des termes sont mises en surbrillance dans l’affichage texte du message pour aider les relecteurs à localiser et à corriger rapidement les alertes de stratégie.
- **Détection des doublons exact et near**: en plus de rechercher les termes exacts de correspondance des stratégies de conformité des communications, des groupes de détection en double, proches de façon textuelle, des termes et des messages similaires, pour accélérer le processus de révision.
- **Nouveaux filtres**: étudiez et corrigez les alertes de stratégie plus rapidement avec des filtres de message pour plusieurs champs, dont l’expéditeur, le destinataire, la date, les domaines et bien d’autres encore.
- **Vues de messages améliorées**: les actions d’enquête et de correction sont désormais plus rapides grâce aux nouvelles vues de source de message, de texte et d’annotation. Les pièces jointes des messages sont désormais affichables pour fournir un contexte complet lors de l’exécution d’actions de correction.
- **Affichage de l’historique des utilisateurs**: vue historique de toutes les activités de correction des messages utilisateur, telles que les notifications passées et les escalades pour les correspondances de stratégie, fournit désormais des relecteurs avec davantage de contexte lors du processus de flux de travail de correction. Les instances First-Time ou REPEAT des correspondances de stratégie pour les utilisateurs sont désormais archivées et faciles à afficher.

### <a name="actionable-insights"></a>Informations exploitables

Les nouveaux tableaux de bord interactifs pour les alertes, les correspondances de stratégie, les actions et les tendances vous permettent d’afficher rapidement l’état des alertes en attente et résolues dans votre organisation.

- **Alertes intelligentes proactives**: les alertes relatives aux correspondances de stratégies nécessitant une attention immédiate incluent les nouveaux tableaux de bord pour les éléments en attente triés par gravité et les nouvelles notifications automatiques par courrier électronique envoyées aux relecteurs désignés.
- **Tableaux de bord interactifs**: nouveaux tableaux de bord afficher les correspondances de stratégie, les actions en attente et résolues, ainsi que les tendances des utilisateurs et de la stratégie.
- **Prise en charge de l’audit**: un journal complet des activités de stratégie et de révision est facilement exporté du centre de conformité Microsoft 365 afin de prendre en charge les demandes de révision d’audit.

## <a name="integration-with-microsoft-365-services"></a>Intégration aux services Microsoft 365

Stratégies de conformité des communications analysez et capturez les messages sur plusieurs canaux de communication pour vous aider à examiner et à corriger rapidement les problèmes de conformité :

- **Microsoft teams**: les communications de conversation pour les canaux [Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview) publics et privés et les conversations individuelles sont prises en charge dans la conformité de la communication en tant que source de canal autonome ou avec d’autres services Microsoft 365. Vous devez ajouter manuellement des utilisateurs individuels, des groupes de distribution ou des canaux Microsoft teams spécifiques lorsque vous sélectionnez des utilisateurs et des groupes à superviser dans une stratégie de conformité de communication.
- **Exchange Online**: toutes les boîtes aux lettres hébergées sur [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online) dans votre organisation Microsoft 365 sont éligibles pour l’analyse. Les e-mails et les pièces jointes correspondant aux conditions de stratégie de conformité de communication sont immédiatement disponibles pour la surveillance et dans les rapports de conformité. Exchange Online est maintenant un canal source facultatif et n’est plus requis dans les stratégies de conformité des communications.
- **Yammer**: les messages privés et les conversations de la communauté publique dans [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page) sont pris en charge dans les stratégies de conformité de communication. Yammer est un canal facultatif qui doit être en [mode natif](https://docs.microsoft.com/yammer/configure-your-yammer-network/overview-native-mode) pour prendre en charge l’analyse des messages et des pièces jointes.
- **Skype entreprise Online**: les stratégies de conformité des communications prennent en charge l’analyse des communications de conversation et des pièces jointes associées dans [Skype entreprise Online](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online).
- **Sources**tierces : vous pouvez analyser les messages provenant de [sources](archiving-third-party-data.md) tierces pour les données importées dans des boîtes aux lettres dans votre organisation Microsoft 365. La conformité de la communication prend en charge les connexions à plusieurs plateformes populaires, notamment la connexion instant Bloomberg, Facebook, Twitter et d’autres.

Pour en savoir plus sur la prise en charge du canal de messagerie dans les stratégies de conformité de communication, voir [types de communication pris en charge](communication-compliance-feature-reference.md#supported-communication-types).

## <a name="workflow"></a>Flux de travail

La conformité de la communication vous aide à résoudre les problèmes courants associés à la conformité aux stratégies internes et aux exigences réglementaires en matière de conformité. Avec des modèles de stratégie ciblés et un flux de travail flexible, vous pouvez utiliser des informations exploitables pour résoudre rapidement les problèmes de conformité détectés.

L’identification et la résolution des problèmes de conformité à l’aide de la conformité de la communication dans Microsoft 365 utilisent le flux de travail suivant :

![Flux de travail de conformité de communication](../media/communication-compliance-workflow.png)

### <a name="configure"></a>Configurer

Dans cette étape du flux de travail, vous identifiez vos besoins en matière de conformité et configurez les stratégies de conformité de communication applicables. Les modèles de stratégie constituent un excellent moyen de configurer rapidement une nouvelle stratégie de conformité, mais aussi de modifier et de mettre à jour rapidement les stratégies à mesure que vos besoins évoluent. Par exemple, vous pouvez tester rapidement une stratégie de langue choquante et de blocage sur les communications pour un petit groupe d’utilisateurs avant de configurer une stratégie pour tous les utilisateurs de votre organisation.

>[!Important]
>Par défaut, les administrateurs globaux n’ont pas accès aux fonctionnalités de conformité des communications. Pour activer les autorisations pour les fonctionnalités de conformité de communication, consultez la rubrique [rendre la conformité de la communication disponible dans votre organisation](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).

Vous pouvez choisir parmi les modèles de stratégie suivants dans le centre de conformité Microsoft 365 :

- **Langage offensant et anti-harcèlement**: utilisez ce modèle pour créer rapidement une stratégie qui utilise le classifieur intégré pour détecter automatiquement le contenu qui peut être considéré comme injurieux ou choquant.
- **Informations sensibles**: utilisez ce modèle pour créer une stratégie d’analyse des communications contenant des types d’informations sensibles ou des mots clés définis afin de vous assurer que les données importantes ne sont pas partagées avec des personnes qui n’ont pas accès.
- **Conformité réglementaire**: utilisez ce modèle pour créer une stratégie d’analyse des communications concernant des références à des termes financiers standard associés à des normes réglementaires.
- **Stratégie personnalisée**: utilisez ce modèle pour configurer des canaux de communication spécifiques, des conditions de détection et la quantité de contenu à surveiller et à réviser dans votre organisation.

### <a name="investigate"></a>Pench

Dans cette étape, vous allez approfondir les problèmes détectés comme correspondant à vos stratégies de conformité de communication. Cette étape inclut les actions suivantes disponibles dans le centre de conformité Microsoft 365 :

- **Alertes**: lorsqu’un message correspond à une condition de stratégie, une alerte est générée automatiquement. Pour chaque alerte, vous pouvez voir l’État, la gravité, l’heure détectée et le cas échéant, ainsi que son état. Les nouvelles alertes sont affichées dans la page d’accueil de la conformité de la communication et la page des **alertes** et sont répertoriées par ordre de gravité.
- **Gestion des problèmes**: pour chaque alerte, vous pouvez prendre des mesures d’enquête afin de résoudre le problème détecté dans le message.
- **Révision de document**: lors de l’enquête sur un problème, vous pouvez utiliser plusieurs vues du message pour évaluer correctement le problème détecté. Les affichages incluent un résumé de conversation, du texte, des annotations et des affichages détaillés de la conversation de communication.
- **Examen de l’historique des activités utilisateur**: Affichez l’historique des activités des messages utilisateur et des actions de correction, telles que les notifications et les escalades passées, pour les correspondances de stratégie.
- **Filtres**: utilisez des filtres tels que sender, Recipient, date et subject pour limiter rapidement les alertes de message que vous souhaitez examiner.

### <a name="remediate"></a>Corriger

L’étape suivante consiste à corriger les problèmes de conformité de communication que vous avez examinés à l’aide des options suivantes :

- **Résolution**: après avoir examiné un problème, vous pouvez résoudre le problème en résolu l’alerte. La résolution d’une alerte entraîne sa suppression de la file d’attente d’alerte en attente et l’action est conservée sous la forme d’une entrée dans la file d’attente résolue pour la stratégie de correspondance. Les alertes sont automatiquement résolues après que l’alerte a été marquée comme faux positif, en envoyant une notification à un employé à propos de l’alerte ou en ouvrant une nouvelle demande de devis.
- **Baliser un message**: dans le cadre de la résolution d’un problème, vous pouvez marquer le message détecté comme étant conforme, non conforme ou comme étant question en relation avec les stratégies et les normes de votre organisation. Le balisage peut vous aider à filtrer les alertes de stratégie pour les escalades ou dans le cadre d’autres processus de révision interne.
- **Avertir l’utilisateur**: les utilisateurs ont souvent enfreint ou non accidentellement une stratégie de conformité de communication. Vous pouvez utiliser la fonctionnalité Notify pour avertir l’utilisateur et résoudre le problème.
- **Escalade à un autre réviseur**: parfois, le réviseur initial d’un problème a besoin d’une entrée d’autres réviseurs pour vous aider à résoudre l’incident. Vous pouvez facilement escalader les problèmes de message aux réviseurs d’autres domaines de votre organisation dans le cadre du processus de résolution.
- **Marquer comme faux positif**: les messages détectés de manière incorrecte en tant que correspondance des stratégies de conformité seront parfois déformés pour le processus de révision. Vous pouvez marquer ces types d’alertes comme faux positifs et résoudre automatiquement le problème.
- **Créer un cas**: dans les situations les plus graves, il se peut que vous deviez partager des informations de conformité de communication avec d’autres réviseurs de votre organisation. La conformité des communications est étroitement intégrée aux autres fonctionnalités de conformité de Microsoft 365 pour vous aider à résoudre les risques de bout en bout. La transmission d’un cas pour l’enquête vous permet de transférer des données et de gérer le cas vers Advanced eDiscovery dans Microsoft 365. Advanced eDiscovery fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu réactif aux investigations internes et externes de votre organisation. Elle permet aux équipes juridiques de gérer l’ensemble du flux de travail de notification de suspension légale. Pour en savoir plus sur les cas avancés de découverte électronique, consultez la rubrique [Overview of Advanced eDiscovery in Microsoft 365](overview-ediscovery-20.md).

### <a name="monitor"></a>Surveiller

Le suivi et la gestion des problèmes de conformité identifiés par les stratégies de conformité des communications s’étendent à l’ensemble du processus de flux de travail. À mesure que des alertes sont générées et que des actions d’analyse et de correction sont mises en œuvre, des stratégies existantes peuvent avoir besoin d’être réexaminées et mises à jour, et de nouvelles stratégies peuvent avoir besoin d’être créées.

- **Monitor and Report**: utilisez des tableaux de bord de conformité de communication, des rapports, des journaux d’exportation et des événements enregistrés dans les journaux d’audit unifiés pour évaluer et améliorer continuellement votre position de conformité.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

- Pour plus d’informations sur la planification des informations, voir [plan for communication Compliance](communication-compliance-plan.md).
- Consultez l' [étude de cas pour Contoso](communication-compliance-case-study.md) et découvrez comment ils ont configuré rapidement une stratégie de conformité de communication pour surveiller le langage choquant dans Microsoft Teams, Exchange Online et les communications Yammer.
- Pour configurer la conformité de la communication pour votre organisation Microsoft 365, consultez la rubrique [configure communication Compliance for microsoft 365](communication-compliance-configure.md).
