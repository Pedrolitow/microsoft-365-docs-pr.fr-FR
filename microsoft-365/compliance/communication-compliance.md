---
title: En savoir plus sur la conformité des communications
description: En savoir plus sur la conformité des communications dans Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, conformité, conformité des communications
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
ms.localizationpriority: medium
ms.collection:
- highpri
- tier1
- purview-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- highpri
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: f2bc78b9b742d47b9421af758d7109650dd6f28a
ms.sourcegitcommit: 3d7dd25abcbf923b45eae84ff4d9d2bb95ef4ca4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68777953"
---
# <a name="learn-about-communication-compliance"></a>En savoir plus sur la conformité des communications

> [!IMPORTANT]
> Conformité des communications Microsoft Purview fournit les outils pour aider les organisations à détecter les violations de conformité réglementaire (par exemple SEC ou FINRA), telles que des informations sensibles ou confidentielles, des propos harcelants ou menaçants, et le partage de contenu pour adultes. Conçu avec la confidentialité par défaut, les noms d’utilisateur sont pseudonymisés par défaut, les contrôles d’accès en fonction du rôle sont intégrés, les enquêteurs sont activés par un administrateur et les journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Conformité des communications Microsoft Purview est une solution de risque interne qui permet de réduire les risques de communication en vous aidant à détecter, capturer et agir sur les messages potentiellement inappropriés dans votre organisation. Les stratégies prédéfinies et personnalisées vous permettent de vérifier les correspondances de stratégie dans les communications internes et externes afin qu’elles puissent être examinées par les réviseurs désignés. Les réviseurs peuvent examiner les e-mails, Microsoft Teams, Yammer ou les communications tierces de votre organisation et prendre les mesures appropriées pour s’assurer qu’ils sont conformes aux normes de messagerie de votre organisation.

Les stratégies de conformité des communications dans Microsoft 365 vous aident à surmonter de nombreux défis modernes liés à la conformité et aux communications internes et externes, notamment :

- Vérification des types croissants de canaux de communication
- Volume croissant de données de message
- Application de la réglementation et risque de pénalité

En outre, il peut y avoir une séparation des tâches entre vos administrateurs informatiques et votre équipe de gestion de la conformité. La conformité des communications prend en charge la séparation entre la configuration des stratégies et l’examen et l’examen des messages. Par exemple, le groupe informatique de votre organisation peut être responsable de la configuration des autorisations, des groupes et des stratégies de rôle de conformité des communications, et les enquêteurs et les réviseurs peuvent être responsables des actions de triage, de révision et d’atténuation des messages.

Pour plus d’informations et pour obtenir une vue d’ensemble du processus de planification pour traiter les activités de conformité et à risque dans votre organisation, consultez [Démarrage d’un programme de gestion des risques internes](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Pour obtenir les dernières vidéos Ignite sur la conformité des communications, consultez les rubriques suivantes :

- [Favoriser une culture de sécurité et d’inclusion grâce à la conformité des communications](https://www.youtube.com/watch?v=oLVzxcaef3w)
- [Découvrez comment réduire les risques de communication au sein de votre organisation](https://www.youtube.com/watch?v=vzARb1YaxGo)
- [Respecter les exigences de conformité réglementaire avec la conformité des communications](https://www.youtube.com/watch?v=gagOhtCBfgU)
- [Améliorer avec Microsoft Teams - En savoir plus sur les dernières fonctionnalités intégrées de Teams natives en matière de conformité des communications](https://www.youtube.com/watch?v=m4jukD5Fh-o)

Pour obtenir une vue d’ensemble rapide de la conformité des communications, consultez la vidéo [Détecter le harcèlement au travail et répondre avec la conformité des communications](https://youtu.be/z33ji7a7Zho) sur le [canal Microsoft Mechanics](https://www.youtube.com/user/OfficeGarageSeries).

Découvrez comment [Valeurs Mobilières TD utilise la conformité des communications](https://customers.microsoft.com/story/1391545301764211731-td-securities-banking-capital-markets-compliance) pour s’acquitter de ses obligations réglementaires et répondre à ses besoins en matière de sécurité et de stabilité.

Regardez la [vidéo Microsoft Mechanics](https://www.youtube.com/watch?v=Ynkfu8OF0wQ) sur la façon dont la gestion des risques internes et la conformité des communications fonctionnent ensemble pour réduire les risques liés aux données des utilisateurs de votre organisation.

Pour suivre les dernières mises à jour de conformité des communications, sélectionnez **Nouveautés de la** [conformité des communications](https://compliance.microsoft.com/) pour votre organisation.

> [!IMPORTANT]
> La conformité des communications est actuellement disponible dans les locataires hébergés dans des régions et des pays géographiques pris en charge par les dépendances de service Azure. Pour vérifier que la conformité des communications est prise en charge pour votre organisation, consultez [Disponibilité des dépendances Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="scenarios-for-communication-compliance"></a>Scénarios de conformité des communications

Les stratégies de conformité des communications peuvent vous aider à examiner les messages de votre organisation dans plusieurs domaines de conformité importants :

- **Stratégies d’entreprise**

    Les utilisateurs doivent se conformer à une utilisation acceptable, à des normes éthiques et à d’autres stratégies d’entreprise dans toutes leurs communications liées à l’entreprise. Les stratégies de conformité des communications peuvent détecter les correspondances de stratégie et vous aider à prendre des mesures correctives pour atténuer ces types d’incidents. Par exemple, vous pouvez vérifier les communications utilisateur au sein de votre organisation pour les problèmes liés aux ressources humaines, tels que le harcèlement ou l’utilisation d’un langage potentiellement inapproprié ou offensant.

- **Gestion des risques**

    Les organisations sont responsables de toutes les communications distribuées dans l’ensemble de leur infrastructure et de leurs systèmes réseau d’entreprise. L’utilisation de stratégies de conformité des communications pour aider à identifier et à gérer les risques juridiques potentiels peut aider à réduire les risques avant qu’ils ne puissent nuire aux opérations de l’entreprise. Par exemple, vous pouvez vérifier dans les messages de votre organisation les communications non autorisées et les conflits d’intérêts concernant des projets confidentiels tels que les acquisitions à venir, les fusions, les divulgations de bénéfices, les réorganisations ou les changements d’équipe de direction.

- **Conformité réglementaire**

    La plupart des organisations doivent se conformer à un certain type de normes de conformité réglementaire dans le cadre de leurs procédures normales de fonctionnement. Ces réglementations exigent souvent que les organisations implémentent un certain type de processus de supervision ou de surveillance pour la messagerie qui convient à leur secteur d’activité. La règle 3110 de l’Autorité de réglementation du secteur financier (FINRA) est un bon exemple de l’obligation pour les organisations de mettre en place des procédures de surveillance pour vérifier les communications des utilisateurs et les types d’entreprises dans lesquelles elle s’engage. Un autre exemple peut être la nécessité d’examiner les communications entre les courtiers et les courtiers de votre organisation pour vous protéger contre les activités potentielles de délit d’initié, de collusion ou de corruption. Les stratégies de conformité des communications peuvent aider votre organisation à répondre à ces exigences en fournissant un processus d’analyse et de création de rapports sur les communications d’entreprise. Pour plus d’informations sur la prise en charge des organisations financières, consultez [Considérations clés en matière de conformité et de sécurité pour les marchés bancaires et financiers américains](../solutions/financial-services-secure-collaboration.md).

## <a name="key-feature-areas"></a>Principaux domaines de fonctionnalités

La conformité des communications offre plusieurs fonctionnalités importantes pour vous aider à résoudre les problèmes de conformité sur vos plateformes de messagerie :

- Modèles personnalisables intelligents
- Workflows de correction flexibles
- Informations exploitables

![Page d’accueil de conformité des communications.](../media/communication-compliance-home.png)

### <a name="intelligent-customizable-templates"></a>Modèles personnalisables intelligents

Les modèles personnalisables intelligents dans la conformité des communications vous permettent d’appliquer le Machine Learning pour détecter intelligemment les violations de communication dans votre organisation.

- **Modèles préconfigurés personnalisables** : les modèles de stratégie permettent de résoudre les risques de communication les plus courants. La création initiale de stratégie et la mise à jour de suivi sont désormais plus rapides avec des modèles prédéfinis pour analyser et atténuer les contenus potentiellement inappropriés, les informations sensibles, les conflits d’intérêts et les problèmes de conformité réglementaire.
- **Nouvelle prise en charge du Machine Learning** : [classifieurs](/microsoft-365/compliance/classifier-get-started-with) intégrés pour analyser et atténuer la discrimination, les menaces, le harcèlement, les grossièretés et les images potentiellement inappropriées, et aider à réduire le contenu mal classé dans les messages de communication, ce qui permet aux réviseurs de gagner du temps pendant le processus d’investigation et de correction.
- **Générateur de conditions amélioré** : configurez les conditions de stratégie qui sont désormais rationalisées dans une expérience unique et intégrée dans l’Assistant Stratégie, ce qui réduit la confusion dans la façon dont les conditions sont appliquées aux stratégies.

### <a name="flexible-remediation-workflows"></a>Workflows de correction flexibles

Les workflows de correction intégrés vous permettent d’identifier et d’agir rapidement sur les messages avec des correspondances de stratégie dans votre organisation. Les nouvelles fonctionnalités suivantes augmentent l’efficacité des activités d’investigation et de correction :

- **Workflow de correction flexible** : le nouveau flux de travail de correction vous permet de prendre rapidement des mesures sur les correspondances de stratégie, y compris de nouvelles options pour faire remonter les messages à d’autres réviseurs et envoyer des notifications par e-mail aux utilisateurs avec des correspondances de stratégie.
- **Correspondance** de stratégie de conversation : les messages dans les conversations sont regroupés par correspondances de stratégie pour vous donner une meilleure visibilité sur la façon dont les conversations sont liées à vos stratégies de communication. Par exemple, la correspondance de stratégie de conversation dans la vue *Alertes en attente* affiche automatiquement tous les messages d’un canal Teams qui ont des correspondances pour vos stratégies de communication pour analyser et atténuer les messages potentiellement inappropriés. Les autres messages dans les conversations qui ne correspondent pas à vos stratégies de communication ne s’affichent pas.
- **Mise en surbrillance des mots clés** : les conditions de stratégie de correspondance des termes sont mises en surbrillance dans l’affichage de texte des messages pour aider les réviseurs à analyser et corriger rapidement les alertes de stratégie.
- **Reconnaissance optique de caractères (OCR) (préversion)** : vérifiez, détectez et examinez le texte imprimé et manuscrit dans les images incorporées ou jointes à des messages électroniques ou à des messages de conversation Microsoft Teams.
- **Nouveaux filtres** : examinez et corrigez les alertes de stratégie plus rapidement avec des filtres de messages pour plusieurs champs, notamment expéditeur, destinataire, date, domaines et bien plus encore.
- **Affichages de messages améliorés** : les actions d’investigation et de correction sont désormais plus rapides avec les nouvelles sources de message et les nouvelles vues de texte. Les pièces jointes de message sont désormais visibles pour fournir un contexte complet lors de l’exécution d’actions de correction.
- **Historique utilisateur** : la vue historique de toutes les activités de correction des messages utilisateur, telles que les notifications passées et les escalades pour les correspondances de stratégie, fournit désormais aux réviseurs davantage de contexte pendant le processus de workflow de correction. Les instances initiales ou répétées de correspondances de stratégie pour les utilisateurs sont désormais archivées et facilement visibles.
- **Notification de modèle détecté** : de nombreuses actions de harcèlement et d’intimidation ont lieu au fil du temps et impliquent des instances récurrentes du même comportement par un utilisateur. Le modèle de notification détecté affiché dans les détails de l’alerte permet d’attirer l’attention sur ces alertes et ce type de comportement.
- **Traduction** : examinez rapidement les détails des messages dans huit langues à l’aide de la prise en charge de la traduction dans le workflow de correction. Les messages dans d’autres langues sont automatiquement convertis en langue d’affichage du réviseur.
- **Détection des pièces jointes** : vérifiez, détectez et examinez le contenu lié (pièces jointes modernes) de OneDrive et Microsoft Teams qui correspondent aux classifieurs de stratégie et aux conditions pour les messages Microsoft Teams. Le contenu de la pièce jointe est automatiquement extrait dans un fichier texte pour une révision et une action détaillées.

### <a name="actionable-insights"></a>Informations exploitables

De nouveaux tableaux de bord interactifs pour les alertes, correspondances de stratégie, actions et tendances vous permettent d’afficher rapidement l’état des alertes en attente et résolues au sein de votre organisation.

- **Alertes intelligentes proactives** : les alertes relatives aux correspondances de stratégie nécessitant une attention immédiate incluent de nouveaux tableaux de bord pour les éléments en attente triés par gravité et les nouvelles notifications par courrier électronique automatiques envoyées aux relecteurs désignés.
- **Tableaux de bord interactifs** : les nouveaux tableaux de bord affichent les correspondances de stratégie, les actions en attente et résolues, et les tendances des utilisateurs et de la stratégie.
- **Prise en charge de l’audit** : un journal complet des activités de stratégie et de révision est facilement exporté à partir du portail de conformité Microsoft Purview pour aider à prendre en charge les demandes de révision d’audit.

## <a name="integration-with-microsoft-365-services"></a>Intégration aux services Microsoft 365

Les stratégies de conformité des communications vérifient, détectent et capturent les messages sur plusieurs canaux de communication pour vous aider à examiner et à corriger rapidement les problèmes de conformité :

- **Microsoft Teams** : les communications de conversation pour les canaux [Microsoft Teams](/MicrosoftTeams/Teams-overview) publics et privés et les conversations individuelles sont prises en charge dans la conformité des communications en tant que source de canal autonome ou avec d’autres services Microsoft 365. Vous devez ajouter manuellement des utilisateurs individuels, des groupes de distribution ou des canaux Microsoft Teams spécifiques lorsque vous sélectionnez des utilisateurs et des groupes à superviser dans une stratégie de conformité des communications. Les utilisateurs De Teams peuvent également signaler eux-mêmes les messages potentiellement inappropriés dans les canaux et conversations privés et de groupe à des fins de révision et de correction.
- **Exchange Online** : toutes les boîtes aux lettres hébergées sur [Exchange Online](/Exchange/exchange-online) dans votre organisation Microsoft 365 peuvent faire l’objet d’analyses. Les e-mails et pièces jointes correspondant aux conditions de stratégie de conformité des communications sont instantanément disponibles pour investigation et dans les rapports de conformité. Exchange Online est désormais un canal source facultatif et n’est plus nécessaire dans les stratégies de conformité des communications.
- **Yammer** : les messages privés et les conversations de la communauté publique dans [Yammer](/yammer/yammer-landing-page) sont pris en charge dans les stratégies de conformité des communications. Yammer est un canal facultatif et doit être en [mode natif](/yammer/configure-your-yammer-network/overview-native-mode) pour prendre en charge la vérification des messages et des pièces jointes.
- **Sources tierces** : vous pouvez vérifier les données importées dans les boîtes aux lettres de votre organisation Microsoft 365 dans les messages provenant de [sources tierces](/microsoft-365/compliance/archiving-third-party-data) . La conformité des communications prend en charge les connexions à plusieurs plateformes populaires, notamment Instant Bloomberg et d’autres.

Pour en savoir plus sur la prise en charge des canaux de messagerie dans les stratégies de conformité des communications, consultez [Détecter les signaux de canal avec la conformité des communications](/microsoft-365/compliance/communication-compliance-channels).

## <a name="integration-with-insider-risk-management-preview"></a>Intégration à la gestion des risques internes (préversion)

La conformité des communications peut fournir des signaux de risque détectés dans les messages destinés aux stratégies utilisateur à risque de gestion des risques internes. À l’aide d’une stratégie [de détection de texte inapproprié](/microsoft-365/compliance/communication-compliance-policies#policy-templates) dédiée dans la conformité des communications, vous pouvez choisir d’ajouter cette stratégie à une [stratégie fuites de données par des employés à risque](/microsoft-365/compliance/insider-risk-management-policies#data-leaks-by-risky-users-preview) ou [violations de stratégie de sécurité par les employés à risque](/microsoft-365/compliance/insider-risk-management-policies#security-policy-violations-by-risky-users-preview) dans la gestion des risques internes. Les utilisateurs à risque détectés dans les messages par la stratégie de conformité des communications agissent comme un événement déclencheur pour amener les utilisateurs dans l’étendue des stratégies de gestion des risques internes.

Pour en savoir plus sur l’intégration à la gestion des risques internes, consultez [Créer et gérer des](/microsoft-365/compliance/communication-compliance-policies#integration-with-insider-risk-management-preview) stratégies de conformité des communications.
Pour en savoir plus sur la gestion des risques internes, consultez [En savoir plus sur la gestion des risques internes](/microsoft-365/compliance/insider-risk-management).

## <a name="get-started-with-recommended-actions-preview"></a>Prise en main des actions recommandées (préversion)

Que vous configuriez la conformité des communications pour la première fois ou que vous ayez commencé à créer de nouvelles stratégies, l’expérience des nouvelles [actions recommandées](/microsoft-365/compliance/communication-compliance-configure#recommended-actions-preview) peut vous aider à tirer le meilleur parti des fonctionnalités de conformité des communications. Les actions recommandées incluent la configuration des autorisations, la création de groupes de distribution, la création de stratégies, etc.

## <a name="workflow"></a>Flux de travail

La conformité des communications vous aide à résoudre les problèmes courants associés à la conformité aux stratégies internes et aux exigences de conformité réglementaire. Avec des modèles de stratégie ciblés et un workflow flexible, vous pouvez utiliser des insights actionnables pour résoudre rapidement les problèmes de conformité détectés.

L'identification et la résolution des problèmes de conformité de la communication utilisent le flux de travail suivant :

![Workflow de conformité des communications.](../media/communication-compliance-workflow.png)

### <a name="configure"></a>Configurer

Dans cette étape de workflow, vous identifiez vos exigences de conformité et configurez les stratégies de conformité de communication applicables. Les modèles de stratégie sont un excellent moyen non seulement de configurer rapidement une nouvelle stratégie de conformité, mais également de modifier et de mettre à jour rapidement les stratégies à mesure que vos besoins évoluent. Par exemple, vous pouvez tester rapidement une stratégie de contenu potentiellement inapproprié sur les communications d’un petit groupe d’utilisateurs avant de configurer une stratégie pour tous les utilisateurs de votre organisation.

>[!IMPORTANT]
>Par défaut, les administrateurs généraux n’ont pas accès aux fonctionnalités de conformité des communications. Pour activer les autorisations pour les fonctionnalités de conformité des communications, consultez [Rendre la conformité des communications disponible dans votre organisation](/microsoft-365/compliance/communication-compliance-configure#step-1-required-enable-permissions-for-communication-compliance).

Vous pouvez choisir parmi les modèles de stratégie suivants dans le portail de conformité Microsoft Purview :

- **Détecter le texte inapproprié** : utilisez ce modèle pour créer rapidement une politique qui utilise des classificateurs intégrés pour détecter automatiquement le texte dans les messages qui peuvent être considérés comme inappropriés, abusifs ou offensants.
- **Détecter les images inappropriées** : Utilisez ce modèle pour créer rapidement une stratégie qui utilise des classificateurs intégrés pour détecter automatiquement le contenu contenant des images adultes et racoleuses qui peuvent être considérées comme inappropriées dans votre organisation.
- **Surveiller les informations sensibles** : utilisez ce modèle pour créer rapidement une stratégie afin de vérifier les communications contenant des types d’informations sensibles définis ou des mots clés pour vous assurer que les données importantes ne sont pas partagées avec des personnes qui ne devraient pas y avoir accès.
- **Surveiller la conformité aux réglementations financières** : utilisez ce modèle pour créer rapidement une stratégie afin de vérifier les communications pour les références aux termes financiers standard associés aux normes réglementaires.
- **Surveillance des conflits d'intérêts** : Utilisez ce modèle pour créer rapidement une stratégie visant à détecter les communications entre deux groupes ou deux utilisateurs afin d'éviter les conflits d'intérêts.
- **Stratégie personnalisée** : Utilisez ce modèle pour configurer des canaux de communication spécifiques, des conditions de détection individuelles et la quantité de contenu à détecter et à examiner dans votre organisation.
- **Stratégie de messages signalés par l’utilisateur** : cette stratégie système prend en charge les messages signalés par l’utilisateur à partir de messages de canal, de groupe et de conversation privée. Activé par défaut dans le Centre d’administration Teams.

> [!TIP]
> Utilisez [les actions recommandées](/microsoft-365/compliance/communication-compliance-configure#recommended-actions) pour vous aider à déterminer si vous avez besoin d’une stratégie de type d’informations sensibles ou si vous devez mettre à jour les stratégies de contenu inapproprié existantes.

### <a name="investigate"></a>Examiner

Dans cette étape, vous pouvez examiner plus en détail les problèmes détectés comme correspondant à vos stratégies de conformité des communications. Cette étape inclut les actions suivantes disponibles dans le portail de conformité Microsoft Purview :

- **Alertes** : lorsqu’un message correspond à une stratégie, une alerte est générée automatiquement. Pour chaque alerte, vous pouvez voir le statut, la gravité, l'heure à laquelle elle a été détectée, et si un cas d'eDiscovery (Premium) est attribué et son statut. Les nouvelles alertes sont affichées sur la page d’accueil de conformité des communications et la page **Alertes** et sont répertoriées par ordre de gravité.
- **Gestion des problèmes** : pour chaque alerte, vous pouvez prendre des mesures d’examen afin de résoudre le problème détecté dans le message.
- **Révision d’un document :** pendant l’examen d’un problème, vous pouvez utiliser plusieurs types d’affichages pour vous aider à évaluer correctement le problème détecté. Les vues incluent un résumé de la conversation, un affichage texte uniquement et des affichages détaillés de la conversation de communication.
- **Examen de l’historique des activités des utilisateurs**: affichez l’historique des activités des messages utilisateur et des actions de correction pour les correspondances de stratégie telles que les notifications et réaffectations passées.
- **Filtres** : utilisez des filtres tels que expéditeur, destinataire, date et objet pour restreindre rapidement les alertes de message que vous souhaitez réviser.

### <a name="remediate"></a>Corriger

L’étape suivante consiste à corriger les problèmes de conformité des communications que vous avez examinés à l’aide des options suivantes :

- **Résoudre** : une fois que vous avez révisé un problème, vous pouvez résoudre le problème en résolvant l’alerte. La résolution d’une alerte la supprime de la file d’attente des alertes en attente, et l’action est conservée en tant qu’entrée dans la *file d’attente résolue* pour la stratégie correspondante. Les alertes sont automatiquement résolues après avoir marqué l’alerte comme mal classée, envoyé une notification à un utilisateur concernant l’alerte ou ouvert un nouveau cas pour l’alerte.
- **Marquer un message** : dans le cadre de la résolution d’un problème, vous pouvez baliser le message détecté comme étant conforme ou non conforme, ou comme il est lié aux stratégies et normes de votre organisation. La balise peut vous aider à microfiltrer des alertes de stratégie pour les réaffectations ou dans le cadre d’autres processus de révision interne.
- **Avertir l’utilisateur** : souvent, les utilisateurs violent accidentellement ou par inadvertance une stratégie de conformité des communications. Vous pouvez utiliser la fonctionnalité Notification pour avertir l’utilisateur et résoudre le problème.
- **Réaffecter à un autre réviseur** : parfois, le réviseur initial d’un problème doit être saisi par d’autres réviseurs pour résoudre l’incident. Vous pouvez facilement transmettre les problèmes de message aux réviseurs d’autres zones de votre organisation dans le cadre du processus de résolution.
- **Marquer comme un faux positif** : les messages détectés de façon incorrecte comme correspondances pour les stratégies de conformité peuvent arriver dans le processus de révision. Vous pouvez marquer ces types d'alertes comme mal classées, soumettre des commentaires à Microsoft sur la mauvaise classification pour aider à améliorer les classificateurs globaux et résoudre automatiquement le problème.
- **Supprimer un message dans Teams (préversion)** : les messages potentiellement inappropriés peuvent être supprimés de l’affichage dans les canaux Microsoft Teams ou les messages de conversation personnels et de groupe. Les messages identifiés qui sont supprimés sont remplacés par une notification indiquant que le message a été supprimé en cas de violation de stratégie.
- **Transférer pour enquête** : dans les situations les plus graves, vous devrez peut-être partager les informations relatives à la conformité des communications avec d'autres examinateurs de votre organisation. La conformité de la communication est étroitement intégrée aux autres fonctionnalités de Microsoft Purview pour vous aider à résoudre les risques de bout en bout. L’escalade d’un cas pour investigation vous permet de transférer des données et la gestion du cas vers Microsoft Purview eDiscovery (Premium). eDiscovery (Premium) fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu qui répond aux investigations internes et externes de votre organisation. Il permet aux équipes juridiques de gérer l’ensemble du flux de travail de notification de conservation légale. Pour en savoir plus sur les cas eDiscovery (Premium), consultez [Vue d’ensemble de Microsoft Purview eDiscovery (Premium)](/microsoft-365/compliance/overview-ediscovery-20).

### <a name="maintain"></a>Maintenir

Le suivi et l’atténuation des problèmes de conformité identifiés par les stratégies de conformité des communications couvrent l’ensemble du processus de workflow. À mesure que des alertes sont générées et que des actions d’investigation et de correction sont implémentées, les stratégies existantes peuvent nécessiter une révision et des mises à jour, et de nouvelles stratégies peuvent avoir besoin d’être créées.

- **Révision et rapport** : utilisez des widgets de tableau de bord de conformité des communications, des journaux d’exportation et des événements enregistrés dans les journaux d’audit unifiés pour évaluer et améliorer continuellement votre posture de conformité.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

- Pour plus d’informations sur la planification, consultez [Planifier la conformité des communications](/microsoft-365/compliance/communication-compliance-plan).
- Consultez [l’étude de cas pour Contoso](/microsoft-365/compliance/communication-compliance-case-study) et découvrez comment elle a rapidement configuré une stratégie de conformité des communications pour détecter du contenu potentiellement inapproprié dans les communications Microsoft Teams, Exchange Online et Yammer.
- Pour configurer la conformité des communications pour votre organisation Microsoft 365, consultez [Configurer la conformité des communications](/microsoft-365/compliance/communication-compliance-configure).
