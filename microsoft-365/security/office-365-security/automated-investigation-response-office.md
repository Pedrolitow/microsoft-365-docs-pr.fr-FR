---
title: Vue d’ensemble de l’analyse et de la réponse automatisée (AIR)
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365-initiative-defender-office365
keywords: réponse automatique aux incidents, investigation, correction, protection contre les menaces
ms.date: 09/29/2020
description: Obtenir une vue d’ensemble des fonctionnalités d’analyse et de réponse automatisées dans Microsoft Defender pour Office 365
ms.custom:
- air
- seo-marvel-mar2020
ms.openlocfilehash: 850291966c2f2da51782d8e70de23ff4f06d6136
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48413961"
---
# <a name="an-overview-of-automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Vue d’ensemble de l’analyse et de la réponse automatisées (AIR) dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


À mesure que des alertes de sécurité sont déclenchées, c’est à votre équipe chargée des opérations de sécurité d’examiner ces alertes et de prendre des mesures pour protéger votre organisation. Parfois, les équipes d’opérations de sécurité peuvent être submergées par le volume des alertes déclenchées. Les fonctionnalités d’analyse et de réponse automatisées de Microsoft Defender pour Office 365 peuvent vous aider. 

AIR permet à votre équipe des opérations de sécurité de fonctionner de manière plus efficace. Les fonctionnalités AIR incluent des processus d’enquête automatisés en réponse à des menaces connues qui existent aujourd’hui. Les actions de correction appropriées attendent l’approbation, ce qui permet à votre équipe des opérations de sécurité de répondre aux menaces détectées. 

Cet article fournit une vue d’ensemble de l’AIR. Lorsque vous êtes prêt à commencer à utiliser AIR, consultez la rubrique [enquêter et répondre aux menaces de manière automatique](office-365-air.md).

## <a name="at-a-high-level"></a>À un niveau élevé

Comme les alertes sont déclenchées, les règles de sécurité entrent en vigueur. En fonction de la situation, un [processus d’enquête automatisé](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air) peut commencer. Pendant et après une enquête automatisée, les [actions correctives](air-remediation-actions.md) sont recommandées. Aucune action n’est effectuée automatiquement dans Microsoft Defender pour Office 365. Votre équipe de gestion des opérations de sécurité examine, puis [approuve ou rejette chaque action de correction](air-review-approve-pending-completed-actions.md). Lorsque toutes les actions effectuées après une enquête sont approuvées ou rejetées, l’enquête se termine. Toutes ces activités sont suivies et affichables dans le centre de sécurité Microsoft 365 ( [https://security.microsoft.com](https://security.microsoft.com) ). (Pour en savoir plus, consultez la rubrique [afficher les détails d’une enquête](air-view-investigation-results.md#view-details-of-an-investigation)).

Les sections suivantes fournissent plus d’informations sur les alertes, les règles de sécurité et des exemples d’AIR en action.

## <a name="alerts"></a>Alertes

Les [alertes](../../compliance/alert-policies.md#viewing-alerts) représentent des déclencheurs pour les flux de travail d’équipe des opérations de sécurité pour la réponse aux incidents. La définition de la priorité des alertes à droite pour l’enquête, tout en s’assurant qu’aucune menace n’est sans adresse est complexe. Lorsque les enquêtes dans les alertes sont effectuées manuellement, les équipes des opérations de sécurité doivent rechercher et corréler les entités (telles que le contenu, les appareils et les utilisateurs) menacées. Ces tâches et les flux de travail peuvent être très longs et impliquer plusieurs outils et systèmes. Avec AIR, l’enquête et la réponse pour les événements de sécurité sont automatisées en ayant des alertes de gestion des menaces et de sécurité clés déclenchant automatiquement des règles de réponse de sécurité. 

Pour l’AIR, les alertes générées à partir des types de stratégies d’alerte suivants sont analysées automatiquement :  

- Un clic d’URL potentiellement malveillant a été détecté
- Courrier électronique signalé par l’utilisateur comme hameçonnage`*`
- Messages électroniques contenant des programmes malveillants supprimés après la remise`*`
- Messages électroniques contenant des URL d’hameçonnage supprimées après la remise`*`
- Modèles d’envoi de courrier électronique suspects détectés
- Utilisateur non autorisé à envoyer un message électronique
- Enquête manuelle déclenchée par l’administrateur du courrier électronique`*`

> [!NOTE]
> Les alertes signalées par un astérisque ( `*` ) sont affectées d’une gravité *informatif* dans les stratégies d’alerte respectives au sein du centre de sécurité Microsoft 365, les notifications par courrier étant désactivées. Les notifications par courrier électronique peuvent être activées par le biais de la [Configuration des stratégies d’alerte](../../compliance/alert-policies.md#alert-policy-settings). 

Pour afficher les alertes, dans le centre de sécurité & conformité, sélectionnez **alertes**  >  **afficher les alertes**. Sélectionnez une alerte pour afficher ses détails, puis, à partir de là, utilisez le lien **consulter l’enquête** pour accéder à l' [enquête](air-view-investigation-results.md#investigation-graph)correspondante.  

> [!NOTE]
> Les alertes d’information sont masquées par défaut dans l’affichage des alertes. Pour les afficher, modifiez le filtrage des alertes de manière à inclure des alertes d’information.

Si votre organisation gère vos alertes de sécurité via un système de gestion des alertes, un système de gestion des services ou un système de gestion des événements et des informations de sécurité (SIEM), vous pouvez envoyer des alertes à ce système via une notification par courrier électronique ou via l' [API activité de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference). Les notifications d’alerte d’enquête via le courrier électronique ou l’API incluent des liens permettant d’accéder aux alertes dans le centre de sécurité Microsoft 365, permettant ainsi à l’administrateur de sécurité affecté de naviguer rapidement dans l’enquête.

![Alertes liées à des enquêtes](../../media/air-alerts-page-details.png) 

## <a name="security-playbooks"></a>Règles de sécurité

Les règles de sécurité sont des stratégies principales qui sont au cœur de l’automatisation dans Microsoft Defender pour Office 365 et Microsoft Threat Protection. Les règles de sécurité fournies dans AIR sont basées sur des scénarios de sécurité réels courants et sont développés en fonction des commentaires des équipes d’opérations de sécurité. Un manuel de sécurité est lancé automatiquement lorsque des alertes spécifiques sont déclenchées au sein de votre organisation. Une fois que l’alerte est déclenchée, le manuel associé est exécuté par le système automatisé d’enquête et de réponse. L’enquête passe par l’analyse de l’alerte en fonction du manuel de cette alerte en examinant toutes les métadonnées associées (notamment les messages électroniques, les utilisateurs, les objets, les expéditeurs, etc.). En fonction des conclusions du manuel d’enquête, AIR recommande un ensemble d’actions que l’équipe de sécurité de votre organisation peut prendre pour contrôler et atténuer la menace. 

Les règles de sécurité que vous obtenez avec AIR sont conçues pour aborder les menaces les plus fréquentes auxquelles les entreprises rencontrent actuellement des courriers électroniques. Elles sont basées sur les opérations de sécurité et les équipes de réponse aux incidents, y compris les personnes qui permettent de défendre Microsoft et les ressources de nos clients.

- Message hameçon signalé par l’utilisateur
- URL-clic sur la modification de verdict
- Détection de programmes malveillants après la livraison (programmes malveillants ZAP)
- Hameçonnage détecté après la livraison ZAP (hameçon ZAP)
- Utilisateur signalé comme compromis 
- Enquête manuelle par courrier électronique (déclenché par un administrateur à partir de programmes malveillants d’explorer, de hameçonnage ou de tout le courrier électronique)

De plus en plus de règles et de mises à jour de manuels seront publiées à mesure qu’elles sont terminées. Consultez la feuille de [route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour voir les autres éléments planifiés et bientôt disponibles.

### <a name="playbooks-include-investigation-and-recommendations"></a>Les règles incluent une enquête et des recommandations

Dans AIR, chaque manuel de sécurité inclut les éléments suivants : 

- une enquête racine des entités d’un e-mail (par exemple, des fichiers, des URL, des destinataires, des adresses IP, etc.),
- la chasse aux courriels similaires reçus par l’Organisation ; 
- les étapes à suivre pour identifier et corréler les autres menaces potentielles, et 
- actions de correction des menaces recommandées.

Chaque étape de haut niveau inclut un certain nombre de sous-étapes qui sont exécutées pour fournir une réponse approfondie, détaillée et exhaustive aux menaces.

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Exemple : un message hameçon signalé par un utilisateur lance un manuel d’enquête.

Supposons qu’un utilisateur de votre organisation reçoit un message indiquant qu’il s’agit d’une tentative de hameçonnage. L’utilisateur, formé pour signaler de tels messages, utilise le [complément de message de rapport](enable-the-report-message-add-in.md) pour l’envoyer à Microsoft pour analyse. L’envoi est également envoyé à votre système et est visible dans l’Explorateur dans l’affichage des **soumissions** (anciennement appelé vue **signalée** par l’utilisateur). En outre, le message signalée par l’utilisateur déclenche désormais une alerte d’information basée sur le système, qui lance automatiquement le manuel d’enquête.

Lors de la phase d’enquête de racine, différents aspects du courrier électronique sont évalués. Ces aspects sont les suivants :

- Détermination du type de menace susceptible de se présenter ;
- Expéditeur ;
- Emplacement d’envoi du courrier électronique (infrastructure émettrice);
- Si d’autres instances du courrier électronique ont été remises ou bloquées ;
- Une évaluation de nos analystes ;
- Si le courrier électronique est associé à des campagnes connues ;
- et bien plus encore.

Une fois l’enquête terminée, le manuel fournit une liste des actions recommandées à effectuer sur le courrier électronique d’origine et les entités qui lui sont associées.
  
Ensuite, plusieurs étapes d’enquête sur les menaces et de chasse sont exécutées :

- Les messages électroniques similaires sont identifiés par des recherches de cluster de messagerie.
- Le signal est partagé avec d’autres plateformes, telles que [Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Une détermination est effectuée sur le fait que les utilisateurs aient cliqué sur les liens malveillants dans les messages électroniques suspects.
- Une vérification est effectuée sur Exchange Online Protection ([EOP](exchange-online-protection-overview.md)) et Office 365 Advanced Threat Protection ([ATP](office-365-atp.md)) pour voir s’il existe d’autres messages similaires signalés par les utilisateurs.
- Une vérification est exécutée pour déterminer si un utilisateur a été compromis. Cette vérification exploite les signaux entre Office 365, [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)et [Azure Active Directory](https://docs.microsoft.com/azure/active-directory), en mettant en corrélation les anomalies d’activité de l’utilisateur associées.

Au cours de la phase de chasse, les risques et les menaces sont affectés à différentes étapes de la chasse. 

La correction est la phase finale du manuel. Pendant cette phase, les étapes de correction sont prises, en fonction des phases d’enquête et de chasse. 

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces

En plus des recherches automatisées déclenchées par une alerte, l’équipe des opérations de sécurité de votre organisation peut déclencher une enquête automatisée à partir d’une vue dans l' [Explorateur de menaces](threat-explorer.md).  Cette enquête crée également une alerte, de sorte que les incidents de Microsoft Defender et les outils SIEM externes puissent voir que cette enquête a été déclenchée. 

Par exemple, supposons que vous utilisiez l’affichage **programme malveillant** dans l’Explorateur. À l’aide des onglets situés sous le graphique, sélectionnez l’onglet **courrier électronique** . Si vous sélectionnez un ou plusieurs éléments dans la liste, le bouton **+ actions** est activé. 

![Explorateur avec des messages sélectionnés](../../media/Explorer-Malware-Email-ActionsInvestigate.png)

Dans le menu **actions** , vous pouvez sélectionner l' **enquête du déclencheur**.

![Menu actions pour les messages sélectionnés](../../media/explorer-malwareview-selectedemails-actions.jpg)

À l’instar des règles déclenchées par une alerte, les recherches automatiques déclenchées à partir d’une vue dans l’Explorateur incluent une enquête de racine, des étapes permettant d’identifier et de corréler les menaces, ainsi que les actions recommandées pour atténuer ces menaces.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Exemple : une équipe d’opérations de sécurité intègre AIR avec sa SIEM à l’aide de l’API activité de gestion d’Office 365

Les fonctionnalités AIR de Microsoft Defender pour Office 365 incluent des [rapports & les détails](air-view-investigation-results.md) que les équipes des opérations de sécurité peuvent utiliser pour surveiller et résoudre les menaces. Toutefois, vous pouvez également intégrer les fonctionnalités AIR à d’autres solutions. Les exemples incluent un système de gestion des événements et des informations de sécurité (SIEM), un système de gestion des cas ou une solution de création de rapports personnalisée. Ces types d’intégration peuvent être effectués à l’aide de l' [API activité de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference). 

Par exemple, une organisation a récemment mis en place un moyen pour l’équipe des opérations de sécurité d’afficher les alertes de hameçonnage signalées par l’utilisateur et déjà traitées par AIR. Leur solution intègre les alertes appropriées avec le serveur SIEM de l’organisation et son système de gestion de la casse. La solution réduit considérablement le nombre de faux positifs afin que l’équipe des opérations de sécurité puisse concentrer leur temps et leur efforts sur des menaces réelles. Pour en savoir plus sur cette solution personnalisée, consultez le [blog de la communauté technique : améliorer l’efficacité de votre SOC avec Office 365 ATP et l’API de gestion d’Office 365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>Étapes suivantes

- [Prise en main de l’utilisation de l’AIR](office-365-air.md)

- [Consultez la feuille de route Microsoft 365 pour voir ce qui est planifié et publié bientôt](https://www.microsoft.com/microsoft-365/roadmap?filters=)

- [En savoir plus sur les fonctionnalités d’analyse et de réponse automatisées supplémentaires dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir?view=o365-worldwide&preserve-view=true)
