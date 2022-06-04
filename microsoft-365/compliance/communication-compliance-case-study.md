---
title: Étude de cas - Contoso configure une stratégie de texte inappropriée
description: Une étude de cas pour Contoso et comment ils configurent rapidement une stratégie de conformité des communications pour surveiller le texte inapproprié dans les communications Microsoft Teams, Exchange Online et Yammer.
keywords: Microsoft 365, Microsoft Purview, conformité, conformité des communications
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
ms.openlocfilehash: 06c126eac6bdc35152b649f6a1fc27df4a96ebf2
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65893413"
---
# <a name="case-study---contoso-quickly-configures-an-inappropriate-text-policy-for-microsoft-teams-exchange-and-yammer-communications"></a>Étude de cas - Contoso configure rapidement une stratégie de texte inappropriée pour les communications Microsoft Teams, Exchange et Yammer

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Communication Compliance permet de réduire les risques de communication en vous aidant à détecter, capturer et agir sur des messages contenant du texte inapproprié dans votre organisation. le texte inapproprié peut inclure des blasphèmes, des menaces, du harcèlement et des images inappropriées. Les stratégies prédéfinies et personnalisées vous permettent d’analyser les communications relatives aux correspondances de stratégie internes et externes pour les examiner par des réviseurs désignés. Les réviseurs peuvent examiner les e-mails analysés, Microsoft Teams, Yammer ou les communications tierces de votre organisation et prendre les mesures de correction appropriées pour s’assurer qu’ils sont conformes aux normes de message de votre organisation.

Contoso Corporation est une organisation fictive qui doit configurer rapidement une stratégie pour surveiller le texte inapproprié. Ils ont principalement utilisé Microsoft 365 pour le courrier électronique, Microsoft Teams et yammer pour leurs utilisateurs, mais ont de nouvelles exigences pour appliquer la stratégie de l’entreprise concernant le harcèlement au travail. Les administrateurs informatiques et les spécialistes de la conformité de Contoso ont une compréhension de base des principes fondamentaux de l’utilisation de Microsoft 365 et recherchent des conseils de bout en bout pour savoir comment prendre rapidement en main la conformité des communications.

Cette étude de cas aborde les principes de base de la configuration rapide d’une stratégie de conformité des communications pour surveiller les communications à la recherche de texte inapproprié. Ce guide se compose de :

- Étape 1 : Planifier la conformité des communications
- Étape 2 : Accès à la conformité des communications
- Étape 3 : Configuration des conditions préalables et création d’une stratégie de conformité des communications
- Étape 4 : Enquêtes et résolutions automatiques

## <a name="step-1-planning-for-communication-compliance"></a>Étape 1 : Planification de la conformité des communications

Les administrateurs informatiques et les spécialistes de la conformité de Contoso ont participé à des webinaires en ligne sur les solutions de conformité dans Microsoft 365 et ont décidé que les stratégies de conformité des communications les aideront à répondre aux exigences mises à jour de la stratégie d’entreprise pour réduire le harcèlement au travail. En travaillant ensemble, ils ont élaboré un plan pour créer et activer une stratégie de conformité des communications qui détectera les messages inappropriés. Cette configuration inclut la détection de texte pour les conversations envoyées dans Microsoft Teams, les messages privés et les conversations de la communauté dans Yammer, ainsi que dans les messages électroniques envoyés dans Exchange Online. Leur plan inclut les déterminations suivantes :

- Administrateurs informatiques qui ont besoin d’accéder aux fonctionnalités de conformité des communications.
- Spécialistes de la conformité qui doivent créer et gérer des stratégies de communication.
- Spécialistes de la conformité et autres collègues d’autres services (ressources humaines, juridiques, etc.) qui doivent examiner et corriger les alertes de conformité des communications.
- Utilisateurs qui seront inclus dans l’étendue de la stratégie de texte inappropriée de conformité des communications.

### <a name="licensing"></a>Licences

La première étape consiste à confirmer que la licence Microsoft 365 de Contoso inclut la prise en charge de la solution de conformité des communications. Pour accéder à la conformité des communications et l’utiliser, les administrateurs informatiques de Contoso doivent vérifier que Contoso dispose de l’une des opérations suivantes :

- Abonnement Microsoft 365 E5/A5/F5/G5 (version payante ou d’évaluation)
- Abonnement Microsoft 365 E3/A3/F3/G5 + module complémentaire conformité Microsoft 365 E5/A5/F5/G5
- Abonnement Microsoft 365 E3/A3/F3/G5 + module complémentaire Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- Abonnement Office 365 Entreprise E5 (version payante ou d’évaluation)
- Abonnement Office 365 A5 (version payante ou d’évaluation)
- Abonnement Office 365 Entreprise E3 + module complémentaire Conformité avancée Office 365 (plus disponible pour les nouveaux abonnements, voir note)

L’une des licences ci-dessus doit être attribuée aux utilisateurs inclus dans les stratégies de conformité des communications. Pour plus d’informations sur les abonnements et les licences, consultez les [conseils microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> La conformité avancée Office 365 n’est plus vendue en tant qu’abonnement autonome. Lorsque les abonnements actuels expirent, les clients doivent passer à l’un des abonnements ci-dessus, qui contiennent les mêmes fonctionnalités de conformité ou d’autres.

Les administrateurs informatiques de Contoso effectuent les étapes suivantes pour vérifier la prise en charge des licences pour Contoso :

1. Les administrateurs informatiques se connectent au Centre <https://admin.microsoft.com> d’administration Microsoft 365 et accédent au Centre d’administration Microsoft 365 ><a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">**licences**</a> **de facturation** > .

2. Ici, ils confirment qu’ils disposent de l’une des [options de licence](communication-compliance-configure.md#subscriptions-and-licensing) qui inclut la prise en charge de la conformité des communications.

![Licences de conformité des communications.](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Autorisations pour la conformité des communications

Cinq groupes de rôles sont utilisés pour configurer des autorisations pour gérer les fonctionnalités de conformité des communications. Pour rendre **la conformité des communications** disponible en tant qu’option de menu dans le portail de conformité Microsoft Purview et pour poursuivre ces étapes de configuration, le rôle *Administrateur de conformité* des communications est attribué aux administrateurs de Contoso.

Contoso décide d’utiliser le groupe de rôles *Conformité* des communications pour affecter tous les administrateurs de conformité des communications, les analystes, les enquêteurs et les observateurs au groupe. Cette configuration de groupe de rôles permet à Contoso de commencer rapidement et de mieux répondre à ses exigences de gestion de la conformité.

|**Role**|**Autorisations de rôle**|
|:-----|:-----|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité de communication. Cette configuration de groupe de rôles est le moyen le plus simple de démarrer rapidement avec la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateur de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications et, plus tard, pour séparer les administrateurs de conformité des communications dans un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité de communication, des paramètres globaux et des attributions de groupes de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui joueront le rôle d’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies à l’endroit où ils sont affectés en tant que réviseurs, afficher les métadonnées de message (et non le contenu du message), effectuer une escalade vers des réviseurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteur de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui joueront le rôle d’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à des réviseurs supplémentaires, passer à un cas eDiscovery (Premium), envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui gèreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de création de rapports sur la page d’accueil de conformité des communications et peuvent afficher tous les rapports de conformité des communications. |

1. Les administrateurs informatiques de Contoso se connectent à la page d’autorisations du [portail de conformité Microsoft Purview](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur général et sélectionnent le lien pour afficher et gérer les rôles dans Microsoft 365.
2. Dans le portail de conformité Microsoft Purview, ils accédent à <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Autorisations**</a> et sélectionnent le lien pour afficher et gérer les rôles dans Office 365.
3. Les administrateurs sélectionnent le groupe de rôles *Conformité des communications* , puis sélectionnent **Modifier le groupe de rôles**.
4. Les administrateurs **sélectionnent Choisir des membres** dans le volet de navigation gauche, puis sélectionnez **Modifier**.
5. Ils sélectionnent **Ajouter** , puis cochent la case pour tous les utilisateurs de Contoso qui gèrent la conformité des communications, examinent et examinent les alertes.
6. Les administrateurs sélectionnent **Ajouter**, puis **Terminé**.
7. Ils sélectionnent **Enregistrer** pour ajouter des utilisateurs Contoso au groupe de rôles. Ils sélectionnent **Fermer** pour effectuer les étapes.

## <a name="step-2-accessing-communication-compliance"></a>Étape 2 : Accès à la conformité des communications

Après avoir configuré les autorisations pour la conformité des communications, les administrateurs informatiques et les spécialistes de conformité contoso affectés au groupe de rôles Conformité des communications peuvent accéder à la solution de conformité des communications dans Microsoft Purview. Les administrateurs informatiques et les spécialistes de la conformité de Contoso ont plusieurs façons d’accéder à la conformité des communications et de commencer à créer une stratégie :

- Démarrage direct à partir de la solution de conformité des communications
- À partir du portail de conformité Microsoft Purview
- À partir du catalogue de solutions Microsoft Purview
- À partir du Centre d’administration Microsoft 365

### <a name="starting-directly-from-the-communication-compliance-solution"></a>Démarrage direct à partir de la solution de conformité des communications

Le moyen le plus rapide d’accéder à la solution consiste à se connecter directement à la solution **de conformité des communications** (<https://compliance.microsoft.com/supervisoryreview>). À l’aide de ce lien, les administrateurs informatiques et les spécialistes de la conformité contoso sont dirigés vers le tableau de bord vue d’ensemble de la conformité des communications, où vous pouvez rapidement examiner l’état des alertes et créer de nouvelles stratégies à partir des modèles prédéfinis.

![Vue d’ensemble de la conformité des communications.](../media/communication-compliance-case-overview.png)

### <a name="starting-from-the-microsoft-purview-compliance-portal"></a>À partir du portail de conformité Microsoft Purview

Un autre moyen simple pour les administrateurs informatiques et les spécialistes de la conformité contoso d’accéder à la solution de conformité des communications consiste à se connecter directement au [portail de conformité Microsoft Purview](https://compliance.microsoft.com). Une fois connectés, les utilisateurs doivent simplement sélectionner le contrôle **Afficher tout** pour exposer toutes les solutions de conformité, puis sélectionner la solution **Conformité des communications** pour démarrer.

![Centre de conformité.](../media/communication-compliance-case-center.png)

### <a name="starting-from-the-microsoft-purview-solution-catalog"></a>À partir du catalogue de solutions Microsoft Purview

Les administrateurs informatiques et les spécialistes de la conformité de Contoso peuvent également choisir d’accéder à la solution de conformité des communications en sélectionnant le catalogue de solutions Microsoft Purview. En sélectionnant **Catalog** dans la section **Solutions** de la navigation de gauche dans le **portail de conformité Microsoft Purview**, ils peuvent ouvrir le catalogue de solutions répertoriant toutes les solutions Microsoft Purview. En faisant défiler jusqu’à la section **Gestion des risques Insider** , les administrateurs informatiques de Contoso peuvent sélectionner La conformité des communications pour commencer. Les administrateurs informatiques de Contoso décident également d’utiliser le contrôle Afficher dans la navigation pour épingler la solution de conformité des communications au volet de navigation gauche pour un accès plus rapide lorsqu’ils se connectent à l’avenir.

![Catalogue de solutions.](../media/communication-compliance-case-solution.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>À partir du Centre d’administration Microsoft 365

Pour accéder à la conformité des communications à partir du Centre d’administration Microsoft 365, les administrateurs informatiques et les spécialistes de la conformité de Contoso se connectent au Centre d’administration Microsoft 365 [(https://admin.microsoft.com)](https://admin.microsoft.com)et accédent au [portail de conformité Microsoft Purview](https://compliance.microsoft.com)).

![Lien de conformité des communications.](../media/communication-compliance-case-compliance-link.png)

Cette action ouvre le **Centre de sécurité et de conformité Office 365** et doit sélectionner le lien vers le **portail de conformité Microsoft Purview** fourni dans la bannière en haut de la page.

![Centre de sécurité et de conformité Office 365.](../media/communication-compliance-case-scc.png)

Une fois dans le **portail de conformité Microsoft Purview**, les administrateurs informatiques de Contoso sélectionnent **Afficher tout** pour afficher la liste complète des solutions de conformité.

![Menu Conformité des communications.](../media/communication-compliance-case-show-all.png)

Après avoir sélectionné **Afficher tout**, les administrateurs informatiques de Contoso peuvent accéder à la solution de conformité des communications.

![Vue d’ensemble de la conformité des communications.](../media/communication-compliance-case-overview.png)

## <a name="step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Étape 3 : Configuration des prérequis et création d’une stratégie de conformité des communications

Pour commencer à utiliser une stratégie de conformité des communications, les administrateurs informatiques de Contoso doivent configurer plusieurs conditions préalables avant de configurer la nouvelle stratégie pour surveiller le texte inapproprié. Une fois ces conditions préalables achevées, les administrateurs informatiques et les spécialistes de la conformité de Contoso peuvent configurer la nouvelle stratégie et les spécialistes de la conformité peuvent démarrer une enquête et corriger les alertes générées.

### <a name="enabling-auditing-in-microsoft-365"></a>Activation de l’audit dans Microsoft 365

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les mesures correctives prises par les réviseurs. Les journaux d’audit sont un récapitulatif de toutes les activités associées à une stratégie organisationnelle définie ou chaque fois qu’une stratégie de conformité des communications est modifiée.

Les administrateurs informatiques de Contoso étudient et complètent les [instructions pas à pas](turn-audit-log-search-on-or-off.md) pour activer l’audit. Après activation de l’audit, un message qui apparaît indique que le journal d’audit est en cours de préparation et qu’ils peuvent effectuer une recherche environ deux heures après la fin de la préparation. Les administrateurs informatiques de Contoso n’exécutent cette action qu’une seule fois.

### <a name="configuring-yammer-tenant-for-native-mode"></a>Configuration du locataire Yammer pour le mode natif

La conformité des communications nécessite que le locataire Yammer d’une organisation soit en mode natif pour surveiller le texte inapproprié dans les messages privés et les conversations de la communauté publique.

Les administrateurs informatiques de Contoso vérifient qu’ils passent en revue les informations [de l’article Vue d’ensemble du mode natif Yammer dans Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode) et suivent les étapes d’exécution de l’outil de migration dans l’article [Configurer votre réseau Yammer pour le mode natif pour Microsoft 365](/yammer/configure-your-yammer-network/native-mode) .

### <a name="setting-up-a-group-for-in-scope-users"></a>Configuration d’un groupe pour des utilisateurs dans l’étendue

Les spécialistes de la conformité de Contoso souhaitent ajouter tous les utilisateurs à la stratégie de communication qui surveille le texte inapproprié. Ils peuvent décider d’ajouter chaque compte d’utilisateur à la stratégie séparément, mais ils ont décidé qu’il était beaucoup plus facile et gagner du temps pour utiliser un groupe de distribution **Tous les utilisateurs** pour les utilisateurs pour cette stratégie.

Ils doivent créer un groupe pour inclure tous les utilisateurs de Contoso. Ils effectuent donc les étapes suivantes :

1. Les administrateurs informatiques de Contoso se connectent au Centre d’administration Microsoft 365 [(https://admin.microsoft.com)](https://admin.microsoft.com)et accédent au Centre d’administration Microsoft 365 > **groupes de groupes** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
2. Ils sélectionnent **Ajouter un groupe** et terminent l’Assistant pour créer un *groupe Microsoft 365* ou un *groupe de distribution*.

    ![Groupes.](../media/communication-compliance-case-all-employees.png)

3. Une fois le groupe créé, ils doivent ajouter tous les utilisateurs Contoso à celui-ci. Ils ouvrent le **Centre d’administration Exchange** [(https://outlook.office365.com/ecp)](https://outlook.office365.com/ecp)et accèdent aux <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**groupes**</a> **de destinataires** >  du **Centre** >  d’administration Exchange). Les administrateurs informatiques de Contoso sélectionnent la zone Appartenance et le nouveau groupe *Tous les employés* qu’ils ont créé, puis sélectionnent le contrôle **Modifier** pour ajouter tous les utilisateurs de Contoso au nouveau groupe dans l’Assistant.

    ![Centre d’administration Exchange.](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-monitor-for-inappropriate-text"></a>Création de la stratégie pour surveiller le texte inapproprié

Une fois toutes les conditions préalables remplies, les administrateurs informatiques et les spécialistes de la conformité de Contoso sont prêts à configurer la stratégie de conformité des communications pour surveiller le texte inapproprié. À l’aide du nouveau modèle de stratégie de texte inapproprié, la configuration de cette stratégie est simple et rapide.

1. Les administrateurs informatiques et les spécialistes de la conformité de Contoso se connectent au **portail de conformité Microsoft Purview** et sélectionnent **Communication conformité** dans le volet de navigation de gauche. Cette action ouvre le tableau de bord de **Vue d’ensemble** comportant des liens rapides pour des modèles de stratégie de conformité des communications. Ils choisissent le **modèle de texte inapproprié Monitor for inappropriate en** sélectionnant **Prise en main** du modèle.

    ![Modèle de texte inapproprié pour la conformité des communications.](../media/communication-compliance-case-template.png)

2. Dans l’Assistant modèle de stratégie, les administrateurs informatiques et les spécialistes de la conformité de Contoso collaborent pour compléter les trois champs obligatoires : **Nom de la stratégie**, **Utilisateurs ou groupes à surveiller**, puis **Réviseurs**.
3. Étant donné que l’Assistant de stratégie a déjà suggéré un nom pour la stratégie, les administrateurs informatiques et les spécialistes de la conformité décident de conserver le nom suggéré et de se concentrer sur les champs restants. Ils sélectionnent le groupe *Tous les utilisateurs* pour les **utilisateurs ou les groupes pour superviser** le champ et sélectionnent les spécialistes de conformité qui doivent examiner et corriger les alertes de stratégie pour le champ **Réviseurs** . La dernière étape pour configurer la stratégie et commencer à collecter des informations d’alerte consiste à sélectionner **Créer une stratégie**.

    ![Assistant De texte inapproprié pour la conformité des communications.](../media/communication-compliance-case-wizard.png)

## <a name="step-4-investigate-and-remediate-alerts"></a>Étape 4 : Enquêter et corriger les alertes

Maintenant que la stratégie de conformité des communications à surveiller pour détecter le texte inapproprié est configurée, l’étape suivante pour les spécialistes de conformité contoso consistera à examiner et à corriger les alertes générées par la stratégie. Le traitement total des communications dans tous les canaux sources par la stratégie et l’affichage des alertes dans le **Tableau de bord d’alerte** peut prendre jusqu’à 24 heures.

Une fois les alertes générées, les spécialistes de conformité de Contoso suivent les [instructions de flux de travail](communication-compliance-investigate-remediate.md) pour examiner et corriger les problèmes de texte inappropriés.
