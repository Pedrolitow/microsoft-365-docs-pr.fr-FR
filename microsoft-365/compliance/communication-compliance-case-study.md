---
title: 'Étude de cas : Contoso configure rapidement une stratégie de contenu inappropriée pour Microsoft Teams, Exchange et Yammer communications'
description: Étude de cas pour Contoso et configuration rapide d’une stratégie de conformité des communications pour surveiller le contenu inapproprié dans les communications Microsoft Teams, Exchange Online et Yammer communications.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.custom:
- admindeeplinkMAC
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- remotework
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 33970df6b108cd5538f14e7bb6c9c7f235d55ca1
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61421965"
---
# <a name="case-study---contoso-quickly-configures-an-inappropriate-content-policy-for-microsoft-teams-exchange-and-yammer-communications"></a>Étude de cas : Contoso configure rapidement une stratégie de contenu inappropriée pour Microsoft Teams, Exchange et Yammer communications

La conformité des communications Microsoft 365 réduire les risques de communication en vous aidant à détecter, capturer et agir sur des messages avec du contenu inapproprié dans votre organisation. Le contenu inapproprié peut inclure des blasphémités, des menaces, du harcèlement et des images inappropriées. Les stratégies prédéfinies et personnalisées vous permettent d’analyser les communications relatives aux correspondances de stratégie internes et externes pour les examiner par des réviseurs désignés. Les réviseurs peuvent examiner les messages électroniques, Microsoft Teams, Yammer ou tiers analysés dans votre organisation et prendre les mesures correctives appropriées pour s’assurer qu’ils sont conformes aux normes de message de votre organisation.

Contoso Corporation est une organisation fictive qui doit configurer rapidement une stratégie pour surveiller le contenu inapproprié. Ils utilisent Microsoft 365 principalement pour la messagerie électronique, les Microsoft Teams et la Yammer pour leurs utilisateurs, mais ont de nouvelles exigences pour appliquer la stratégie de l’entreprise en matière de harcèlement au travail. Les administrateurs informatiques et les spécialistes de la conformité de Contoso ont une connaissance de base des principes de base de l’utilisation de Microsoft 365 et recherchent des conseils de bout en bout sur la façon de se lancer rapidement dans la conformité des communications.

Cette étude de cas couvre les bases de la configuration rapide d’une stratégie de conformité des communications afin de surveiller les communications pour le contenu inapproprié. Ce guide se compose de :

- Étape 1 : Planifier la conformité des communications
- Étape 2 : Accéder à la conformité des communications dans Microsoft 365
- Étape 3 : Configuration des conditions préalables et création d’une stratégie de conformité des communications
- Étape 4 : Enquêtes et résolutions automatiques

## <a name="step-1-planning-for-communication-compliance"></a>Étape 1 : Planification de la conformité des communications

Les administrateurs informatiques et les spécialistes de la conformité de Contoso ont participé à des webinaires en ligne sur les solutions de conformité dans Microsoft 365 et ont décidé que les stratégies de conformité des communications les aideront à répondre aux exigences de stratégie d’entreprise mises à jour pour réduire le harcèlement au travail. En travaillant ensemble, ils ont développé un plan pour créer et activer une stratégie de conformité des communications qui surveille le contenu inapproprié des conversations envoyées dans les Microsoft Teams, les messages privés et les conversations de la communauté en Yammer, ainsi que dans les messages électroniques envoyés dans Exchange Online. Leur plan inclut les déterminations suivantes :

- Administrateurs informatiques qui ont besoin d’accéder aux fonctionnalités de conformité des communications.
- Les spécialistes de la conformité qui doivent créer et gérer des stratégies de communication.
- Les spécialistes de la conformité et d’autres collègues dans d’autres services (ressources humaines, juridiques, etc.) qui doivent examiner et corriger les alertes de conformité des communications.
- Utilisateurs qui seront dans l’étendue de la stratégie de contenu inappropriée de conformité des communications.

### <a name="licensing"></a>Licences

La première étape consiste à vérifier que la licence Microsoft 365 contoso inclut la prise en charge de la solution de conformité des communications. Pour accéder à la conformité des communications et l’utiliser, les administrateurs informatiques de Contoso doivent vérifier que Contoso dispose de l’une des conditions suivantes :

- Microsoft 365 E5 abonnement (version payante ou d’essai)
- Microsoft 365 E3 abonnement + le module Microsoft 365 E5 Conformité’abonnement
- Microsoft 365 E3 abonnement + le module Microsoft 365 E5 gestion des risques internes
- Microsoft 365 A5 abonnement (version payante ou d’essai)
- Microsoft 365 A3 abonnement + le module Microsoft 365 A5 conformité de l’application
- Microsoft 365 A3 abonnement + le module Microsoft 365 A5 gestion des risques internes
- Abonnement Microsoft 365 G5 (version payante ou d’essai)
- Microsoft 365 abonnement G5 + le module Microsoft 365 conformité G5
- Microsoft 365 abonnement G5 + le module Microsoft 365 gestion des risques internes G5
- Office 365 Entreprise abonnement E5 (version payante ou d’essai)
- Office 365 Entreprise abonnement E3 + le module Conformité avancée Office 365 de service (non disponible pour les nouveaux abonnements, voir la remarque)

Ils doivent également confirmer que l’une des licences ci-dessus doit être attribuée aux utilisateurs inclus dans les stratégies de conformité des communications.

> [!IMPORTANT]
> Conformité avancée Office 365 n’est plus vendu en tant qu’abonnement autonome. Lorsque les abonnements actuels expirent, les clients doivent passer à l’un des abonnements ci-dessus, qui contient les mêmes fonctionnalités de conformité ou des fonctionnalités supplémentaires.

Les administrateurs informatiques de Contoso prennent les mesures suivantes pour vérifier la prise en charge des licences pour Contoso :

1. Les administrateurs informatiques se connectent au Centre d'administration Microsoft 365 et Centre d'administration Microsoft 365 > <https://admin.microsoft.com>   >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">**licences de facturation.**</a>

2. Ici, ils confirme qu’ils ont l’une des [options de licence](communication-compliance-configure.md#subscriptions-and-licensing) qui inclut la prise en charge de la conformité des communications.

![Gestion des licences de conformité des communications.](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Autorisations pour la conformité des communications

Il existe cinq groupes de rôles utilisés pour configurer les autorisations pour gérer les fonctionnalités de conformité des communications. Pour rendre **la conformité des** communications disponible en tant qu’option de menu dans Centre de conformité Microsoft 365  et pour poursuivre ces étapes de configuration, le rôle Administrateur de conformité des communications est attribué aux administrateurs Contoso.

Contoso décide d’utiliser le groupe de rôles Conformité des communications pour affecter tous les administrateurs de conformité des communications, analystes, enquêteurs et visionneuses au groupe.  Cela facilite la prise en charge rapide de Contoso et répond au mieux à ses besoins en matière de gestion de la conformité.

|**Role**|**Autorisations de rôle**|
|:-----|:-----|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation au sein d’un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et visionneuses désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité des communications. Cette configuration est le moyen le plus simple de se lancer rapidement dans la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateur de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications, puis pour séparer les administrateurs de conformité des communications en un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité des communications, des paramètres globaux et des attributions de groupe de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies où ils sont affectés en tant que réviseurs, afficher les métadonnées des messages (et non le contenu du message), passer à des réviseurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteur de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à des réviseurs supplémentaires, passer à un cas Advanced eDiscovery, envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui gèreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de rapports sur la page d’accueil de conformité des communications et peuvent afficher tous les rapports de conformité des communications. |

1. Les administrateurs informatiques contoso se connectent à la page d’autorisations [Centre de conformité Microsoft 365](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur général et sélectionnent le lien pour afficher et gérer les rôles dans Microsoft 365.
2. Dans la Centre de conformité Microsoft 365, ils vont sur Autorisations et sélectionnent le lien pour afficher et gérer les <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**rôles**</a> dans Office 365.
3. Les administrateurs sélectionnent le *groupe de rôles Conformité* des communications, puis **sélectionnent Modifier le groupe de rôles.**
4. Les administrateurs **sélectionnent Choisir des membres** dans le volet de navigation de gauche, puis sélectionnent **Modifier.**
5. Ils **sélectionnent Ajouter,** puis cochent la case pour tous les utilisateurs de Contoso qui gèrent la conformité des communications, examinent et examinent les alertes.
6. Les administrateurs **sélectionnent Ajouter,** puis **Terminé**.
7. Ils **sélectionnent Enregistrer** pour ajouter des utilisateurs Contoso au groupe de rôles. Ils **sélectionnent Fermer** pour effectuer les étapes.

## <a name="step-2-accessing-communication-compliance-in-microsoft-365"></a>Étape 2 : accès à la conformité des communications dans Microsoft 365

Après avoir configuré les autorisations pour la conformité des communications, les administrateurs informatiques de Contoso et les spécialistes de la conformité affectés au groupe de rôles Conformité des communications peuvent accéder à la solution de conformité des communications dans Microsoft 365. Les administrateurs informatiques et les spécialistes de la conformité de Contoso ont plusieurs moyens d’accéder à la conformité des communications et de commencer à créer une stratégie :

- En commençant directement à partir de la solution de conformité des communications
- À partir de la Centre de conformité Microsoft 365
- À partir du catalogue Microsoft 365 solutions
- À partir de la Centre d'administration Microsoft 365

### <a name="starting-directly-from-the-communication-compliance-solution"></a>En commençant directement à partir de la solution de conformité des communications

Le moyen le plus rapide d’accéder à  la solution consiste à se connecter directement à la solution de conformité des <https://compliance.microsoft.com/supervisoryreview> communications ( ). À l’aide de ce lien, les administrateurs informatiques et les spécialistes de la conformité de Contoso sont dirigés vers le tableau de bord de vue d’ensemble de la conformité des communications où vous pouvez rapidement passer en revue l’état des alertes et créer de nouvelles stratégies à partir des modèles prédéfinie.

![Vue d’ensemble de la conformité des communications.](../media/communication-compliance-case-overview.png)

### <a name="starting-from-the-microsoft-365-compliance-center"></a>À partir de la Centre de conformité Microsoft 365

Un autre moyen simple pour les administrateurs informatiques et les spécialistes de la conformité de Contoso d’accéder à la solution de conformité des communications consiste à se connecter directement au [Centre de conformité Microsoft 365](https://compliance.microsoft.com). Une fois connectés, les utilisateurs doivent simplement sélectionner le contrôle **Afficher tout** pour exposer toutes les solutions de conformité, puis sélectionner la solution **Conformité des communications** pour démarrer.

![Centre de conformité.](../media/communication-compliance-case-center.png)

### <a name="starting-from-the-microsoft-365-solution-catalog"></a>À partir du catalogue Microsoft 365 solutions

Les administrateurs informatiques et les spécialistes de la conformité de Contoso pouvaient également choisir d’accéder à la solution de conformité des communications en sélectionnant Microsoft 365 catalogue de solutions. En sélectionnant catalogue dans la section **Solutions** du volet de navigation de gauche dans le **Centre de conformité Microsoft 365,** ils peuvent ouvrir le catalogue de solutions répertoriant toutes les solutions de conformité Microsoft 365 solutions.  En faisant défiler vers le bas jusqu’à la section **Gestion** des risques internes, les administrateurs informatiques de Contoso peuvent sélectionner la conformité des communications pour commencer. Les administrateurs informatiques de Contoso décident également d’utiliser le contrôle d’affichage dans la navigation pour épingler la solution de conformité des communications au volet de navigation gauche pour un accès plus rapide lorsqu’ils se connectent à l’avenir.

![Catalogue de solutions.](../media/communication-compliance-case-solution.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>À partir de la Centre d'administration Microsoft 365

Pour accéder à la conformité des communications à partir du Centre d'administration Microsoft 365, les administrateurs informatiques et les spécialistes de la conformité de Contoso se connectent au Centre d'administration Microsoft 365 [( https://admin.microsoft.com) ](https://admin.microsoft.com) et accèdent à [ Centre de conformité Microsoft 365](https://compliance.microsoft.com)

![Lien conformité des communications.](../media/communication-compliance-case-compliance-link.png)

Cette action ouvre le Centre de sécurité et conformité **Office 365** et doit sélectionner le lien vers le **Centre de conformité Microsoft 365** fourni dans la bannière en haut de la page.

![Office 365 sécurité et conformité.](../media/communication-compliance-case-scc.png)

Une fois dans la **Centre de conformité Microsoft 365,** les administrateurs  informatiques de Contoso sélectionnent Afficher tout pour afficher la liste complète des solutions de conformité.

![Menu Conformité des communications.](../media/communication-compliance-case-show-all.png)

Après avoir sélectionné **Afficher tout,** les administrateurs informatiques de Contoso peuvent accéder à la solution de conformité des communications.

![Vue d’ensemble de la conformité des communications.](../media/communication-compliance-case-overview.png)

## <a name="step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Étape 3 : Configuration des conditions préalables et création d’une stratégie de conformité des communications

Pour commencer à mettre en place une stratégie de conformité des communications, les administrateurs informatiques de Contoso doivent configurer plusieurs conditions préalables avant de configurer la nouvelle stratégie afin de surveiller le contenu inapproprié. Une fois ces conditions préalables achevées, les administrateurs informatiques et les spécialistes de la conformité de Contoso peuvent configurer la nouvelle stratégie et les spécialistes de la conformité peuvent démarrer une enquête et corriger les alertes générées.

### <a name="enabling-auditing-in-microsoft-365"></a>Activation de l’audit dans Microsoft 365

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les mesures correctives prises par les réviseurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie d’organisation définie, ou à chaque fois qu’une modification intervient dans une stratégie de conformité aux communications.

Les administrateurs informatiques de Contoso étudient et complètent les [instructions pas à pas](turn-audit-log-search-on-or-off.md) pour activer l’audit. Après activation de l’audit, un message qui apparaît indique que le journal d’audit est en cours de préparation et qu’ils peuvent effectuer une recherche environ deux heures après la fin de la préparation. Les administrateurs informatiques de Contoso n’exécutent cette action qu’une seule fois.

### <a name="configuring-yammer-tenant-for-native-mode"></a>Configuration du Yammer client pour le mode natif

La conformité des communications nécessite que le client Yammer d’une organisation soit en mode natif pour surveiller le contenu inapproprié dans les messages privés et les conversations de la communauté publique.

Les administrateurs informatiques contoso s’assurent qu’ils examinent les informations de [l’article](/yammer/configure-your-yammer-network/overview-native-mode) Vue d’ensemble du mode natif Yammer dans Microsoft 365 et suivent les étapes d’exécution de l’outil de migration dans l’article Configurer votre réseau Yammer pour le mode natif pour [Microsoft 365.](/yammer/configure-your-yammer-network/native-mode)

### <a name="setting-up-a-group-for-in-scope-users"></a>Configuration d’un groupe pour des utilisateurs dans l’étendue

Les spécialistes de la conformité Contoso souhaitent ajouter tous les utilisateurs à la stratégie de communication qui surveille le contenu inapproprié. Ils peuvent décider d’ajouter chaque compte d’utilisateur à la stratégie séparément, mais ils ont décidé qu’il est beaucoup plus facile et gagnent du temps d’utiliser un groupe de **distribution** Tous les utilisateurs pour les utilisateurs de cette stratégie.

Ils doivent créer un groupe pour inclure tous les utilisateurs de Contoso, de sorte qu’ils prennent les mesures suivantes :

1. Les administrateurs informatiques de Contoso se connectent au Centre d'administration Microsoft 365 [ https://admin.microsoft.com) (](https://admin.microsoft.com) et Centre d'administration Microsoft 365 > **groupes de**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**groupes.**</a>
2. Ils **sélectionnent Ajouter un groupe et** terminent l’Assistant pour créer un groupe Microsoft 365 *ou* un groupe *de distribution.*

    ![Groupes.](../media/communication-compliance-case-all-employees.png)

3. Une fois le groupe créé, ils doivent ajouter tous les utilisateurs Contoso à celui-ci. Ils ouvrent le **Exchange d’administration** [( https://outlook.office365.com/ecp)](https://outlook.office365.com/ecp) et naviguent jusqu’Exchange **groupes** de  >  **destinataires du Centre d’administration.**  >  <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a> Les administrateurs informatiques de Contoso  sélectionnent la zone d’appartenance et le nouveau groupe Tous les employés qu’ils ont créé et sélectionnent le contrôle Modifier pour ajouter tous les utilisateurs Contoso au nouveau groupe dans l’Assistant. 

    ![Exchange’administration centrale.](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-monitor-for-inappropriate-content"></a>Création de la stratégie pour surveiller le contenu inapproprié

Une fois toutes les conditions préalables terminées, les administrateurs informatiques et les spécialistes de la conformité de Contoso sont prêts à configurer la stratégie de conformité des communications pour surveiller le contenu inapproprié. À l’aide du nouveau modèle de stratégie de contenu inapproprié, la configuration de cette stratégie est simple et rapide.

1. Les administrateurs informatiques et les spécialistes de la conformité de Contoso se connectent au **Centre de conformité Microsoft 365**, puis sélectionnent **Conformité des communications** dans le volet de navigation gauche. Cette action ouvre le tableau de bord de **Vue d’ensemble** comportant des liens rapides pour des modèles de stratégie de conformité des communications. Ils choisissent le **moniteur pour le modèle de contenu** inapproprié en sélectionnant **Commencer** pour le modèle.

    ![Modèle de contenu inapproprié de conformité des communications.](../media/communication-compliance-case-template.png)

2. Dans l’Assistant modèle de stratégie, les administrateurs informatiques et les spécialistes de la conformité de Contoso collaborent pour compléter les trois champs obligatoires : **Nom de la stratégie**, **Utilisateurs ou groupes à surveiller**, puis **Réviseurs**.
3. Étant donné que l’Assistant de stratégie a déjà suggéré un nom pour la stratégie, les administrateurs informatiques et les spécialistes de la conformité décident de conserver le nom suggéré et de se concentrer sur les champs restants. Ils sélectionnent le groupe  Tous les utilisateurs pour le champ Utilisateurs ou groupes à surveiller et sélectionnent les spécialistes de la conformité qui doivent examiner et corriger les alertes de stratégie pour le champ **Relecteurs.**  La dernière étape pour configurer la stratégie et commencer à collecter des informations d’alerte consiste à sélectionner **Créer une stratégie.**

    ![Assistant Contenu inapproprié de conformité des communications.](../media/communication-compliance-case-wizard.png)

## <a name="step-4-investigate-and-remediate-alerts"></a>Étape 4 : Enquêter et corriger les alertes

Maintenant que la stratégie de conformité des communications à surveiller pour le contenu inapproprié est configurée, l’étape suivante pour les spécialistes de la conformité Contoso consiste à examiner et corriger les alertes générées par la stratégie. Le traitement total des communications dans tous les canaux sources par la stratégie et l’affichage des alertes dans le **Tableau de bord d’alerte** peut prendre jusqu’à 24 heures.

Une fois les alertes générées, les spécialistes de la conformité Contoso suivent les [instructions](communication-compliance-investigate-remediate.md) de flux de travail pour examiner et corriger les problèmes de contenu inappropriés.