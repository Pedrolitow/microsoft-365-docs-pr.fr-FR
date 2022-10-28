---
title: Étude de cas - Contoso configure une stratégie de conformité des communications pour identifier le texte potentiellement inapproprié
description: Une étude de cas pour Contoso et la façon dont elle configure rapidement une stratégie de conformité des communications pour détecter le texte potentiellement inapproprié dans les communications Microsoft Teams, Exchange Online et Yammer.
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
- tier1
- purview-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 90b2a34c879017fa867fa48c2ba2006a2560fd5b
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68769422"
---
# <a name="case-study---contoso-configures-a-communication-compliance-policy-to-identify-potentially-inappropriate-text-for-microsoft-teams-exchange-and-yammer-communications"></a>Étude de cas : Contoso configure une stratégie de conformité des communications pour identifier le texte potentiellement inapproprié pour les communications Microsoft Teams, Exchange et Yammer

> [!IMPORTANT]
> Conformité des communications Microsoft Purview fournit les outils pour aider les organisations à détecter les violations de conformité réglementaire (par exemple SEC ou FINRA), telles que des informations sensibles ou confidentielles, des propos harcelants ou menaçants, et le partage de contenu pour adultes. Conçu avec la confidentialité par défaut, les noms d’utilisateur sont pseudonymisés par défaut, les contrôles d’accès en fonction du rôle sont intégrés, les enquêteurs sont activés par un administrateur et les journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

[Conformité des communications Microsoft Purview](/microsoft-365/compliance/communication-compliance) permet de réduire les risques de communication en vous aidant à détecter, capturer et agir sur les messages contenant du texte potentiellement inapproprié dans votre organisation. Un texte potentiellement inapproprié peut inclure des grossièretés, des menaces, du harcèlement et du contenu pour adultes. Les [stratégies prédéfinies](/microsoft-365/compliance/communication-compliance-policies) et personnalisées vous permettent d’examiner les communications internes et externes pour les correspondances de stratégie, afin qu’elles puissent être examinées par les réviseurs désignés. Les réviseurs peuvent [examiner les alertes](/microsoft-365/compliance/communication-compliance-investigate-remediate#investigate-alerts) pour les e-mails, Microsoft Teams, Yammer ou les communications tierces au sein de votre organisation et prendre [les mesures correctives](/microsoft-365/compliance/communication-compliance-investigate-remediate#remediate-alerts) appropriées pour s’assurer qu’elles sont conformes aux normes de message de votre organisation.

Contoso Corporation est une organisation fictive qui doit configurer rapidement une stratégie pour détecter le texte potentiellement inapproprié. Ils utilisent Microsoft 365 principalement pour la messagerie, Microsoft Teams et le support Yammer pour leurs utilisateurs, mais ont de nouvelles exigences pour appliquer la stratégie de l’entreprise concernant le harcèlement au travail. Les administrateurs informatiques et les spécialistes de la conformité de Contoso ont une compréhension de base des principes fondamentaux de l’utilisation de Microsoft 365 et recherchent des conseils de bout en bout pour prendre rapidement en main la conformité des communications.

Cette étude de cas couvre les principes de base de la configuration rapide d’une stratégie de conformité des communications afin de détecter un texte potentiellement inapproprié. Ce guide se compose de :

- [Étape 1 : Planification de la conformité des communications](#step-1-planning-for-communication-compliance)
- [Étape 2 : Accès à la conformité des communications](#step-2-accessing-communication-compliance)
- [Étape 3 : Configuration des prérequis et création d’une stratégie de conformité des communications](#step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy)
- [Étape 4 : Examiner et corriger les alertes](#step-4-investigate-and-remediate-alerts)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="step-1-planning-for-communication-compliance"></a>Étape 1 : Planification de la conformité des communications

Les administrateurs informatiques et les spécialistes de la conformité de Contoso ont assisté à des webinaires en ligne sur les solutions de conformité dans Microsoft Purview et ont décidé que les stratégies de conformité des communications les aideront à répondre aux exigences de stratégie d’entreprise mises à jour pour réduire le harcèlement au travail. Ensemble, ils ont développé un plan pour créer et activer une stratégie de conformité des communications qui détectera les messages potentiellement inappropriés. Cette configuration inclut la détection de texte pour les conversations envoyées dans Microsoft Teams, les messages privés et les conversations de la communauté dans Yammer, ainsi que dans les messages électroniques envoyés dans Exchange Online.

Leur plan comprend l’identification des éléments suivants :

- Administrateurs informatiques qui ont besoin d’accéder aux fonctionnalités de conformité des communications.
- Spécialistes de la conformité qui ont besoin de créer et de gérer des stratégies de conformité des communications.
- Des spécialistes de la conformité et d’autres collègues d’autres services (Ressources humaines, Juridique, etc.) qui doivent examiner et corriger les alertes de conformité des communications.
- Utilisateurs qui seront dans le cadre de la stratégie de conformité de la communication de texte potentiellement inappropriée.

### <a name="licensing"></a>Licences

La première étape consiste à vérifier si les licences Microsoft 365 de Contoso incluent la prise en charge de la solution de conformité des communications. Pour accéder à la conformité des communications et l’utiliser, les administrateurs informatiques de Contoso doivent vérifier que Contoso dispose de l’un des éléments suivants :

- Abonnement Microsoft 365 E5/A5/F5/G5 (version payante ou d’évaluation)
- Abonnement Microsoft 365 E3/A3/F3/G5 + le module complémentaire conformité Microsoft 365 E5/A5/F5/G5
- Abonnement Microsoft 365 E3/A3/F3/G5 + module complémentaire Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- abonnement Office 365 Entreprise E5 (version payante ou d’évaluation)
- abonnement Office 365 A5 (version payante ou d’évaluation)
- Office 365 Entreprise abonnement E3 + le module complémentaire Conformité avancée Office 365 (plus disponible pour les nouveaux abonnements, voir remarque)

Les utilisateurs inclus dans les stratégies de conformité des communications doivent se voir attribuer l’une des licences ci-dessus. Pour plus d’informations sur les abonnements et les licences, consultez [Les conseils microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> Conformité avancée Office 365 n’est plus vendu en tant qu’abonnement autonome. Lorsque les abonnements actuels expirent, les clients doivent passer à l’un des abonnements ci-dessus, qui contiennent les fonctionnalités de conformité identiques ou supplémentaires.

Les administrateurs informatiques de Contoso effectuent les étapes suivantes pour vérifier la prise en charge des licences pour Contoso :

1. Les administrateurs informatiques se connectent au [Centre d'administration Microsoft 365](https://admin.microsoft.com) et accèdent à Centre d'administration Microsoft 365 > **Licences de facturation** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

2. Ici, ils confirment qu’ils disposent de l’une des [options de licence](/microsoft-365/compliance/communication-compliance-configure#subscriptions-and-licensing) qui inclut la prise en charge de la conformité des communications.

![Licences de conformité des communications.](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Autorisations pour la conformité des communications

Cinq groupes de rôles sont utilisés pour configurer les autorisations pour gérer les fonctionnalités de conformité des communications. Pour rendre la **conformité des communications** disponible en tant qu’option de menu dans portail de conformité Microsoft Purview et poursuivre ces étapes de configuration, les administrateurs contoso se voient attribuer le rôle *Administrateurs de conformité des communications*.

Contoso décide d’utiliser le groupe de rôles *Conformité des communications* pour affecter tous les administrateurs, analystes, enquêteurs et observateurs de conformité des communications au groupe. Cette configuration de groupe de rôles facilite la prise en main rapide de Contoso et répond au mieux à ses exigences en matière de gestion de la conformité.

|**Role**|**Autorisations de rôle**|
|:-----|:-----|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité des communications. Cette configuration de groupe de rôles est le moyen le plus simple de démarrer rapidement avec la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateurs de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications, puis pour séparer les administrateurs de conformité des communications dans un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité des communications, des paramètres globaux et des attributions de groupes de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analystes de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies où ils sont affectés en tant que réviseurs, afficher les métadonnées de message (et non le contenu des messages), remonter à d’autres réviseurs ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteurs de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, les réaffecter à d’autres réviseurs, passer à un cas eDiscovery (Premium), envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuses de la conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui géreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de création de rapports sur la page d’accueil de conformité des communications et afficher tous les rapports de conformité des communications. |

1. Les administrateurs informatiques de Contoso se connectent à la page d’autorisations [portail de conformité Microsoft Purview](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur général et sélectionnez le lien pour afficher et gérer les rôles dans Microsoft 365.
2. Dans la portail de conformité Microsoft Purview, ils accèdent à <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Autorisations**</a> et sélectionnent le lien pour afficher et gérer les rôles dans Office 365.
3. Les administrateurs sélectionnent le groupe de rôles *Conformité des communications* , puis **Modifier le groupe de rôles**.
4. Les administrateurs **sélectionnent Choisir des membres** dans le volet de navigation gauche, puis **sélectionnez Modifier**.
5. Ils sélectionnent **Ajouter** , puis cochent la case pour tous les utilisateurs de Contoso qui gèrent la conformité des communications, examinent et examinent les alertes.
6. Les administrateurs **sélectionnent Ajouter**, puis **Terminé**.
7. Ils **sélectionnent Enregistrer** pour ajouter des utilisateurs Contoso au groupe de rôles. Ils sélectionnent **Fermer** pour effectuer les étapes.

## <a name="step-2-accessing-communication-compliance"></a>Étape 2 : Accès à la conformité des communications

Après avoir configuré les autorisations pour la conformité des communications, les administrateurs informatiques de Contoso et les spécialistes de la conformité affectés au groupe de rôles Conformité des communications peuvent accéder à la solution de conformité des communications dans Microsoft Purview. Les administrateurs informatiques et les spécialistes de la conformité de Contoso disposent de plusieurs façons d’accéder à la conformité des communications et de commencer à créer une stratégie :

- À partir directement de la solution de conformité des communications
- À partir de la portail de conformité Microsoft Purview
- À partir du catalogue de solutions Microsoft Purview
- À partir de la Centre d'administration Microsoft 365

### <a name="starting-directly-from-the-communication-compliance-solution"></a>À partir directement de la solution de conformité des communications

Le moyen le plus rapide d’accéder à la solution consiste à se connecter directement à la [solution de conformité des communications](https://compliance.microsoft.com/supervisoryreview). À l’aide de ce lien, les administrateurs informatiques et les spécialistes de la conformité de Contoso sont dirigés vers la page d’accueil de la conformité des communications, où vous pouvez rapidement passer en revue l’état des alertes et créer des stratégies à partir des modèles prédéfinis.

![Page d’accueil de la conformité des communications.](../media/communication-compliance-home.png)

### <a name="starting-from-the-microsoft-purview-compliance-portal"></a>À partir de la portail de conformité Microsoft Purview

Un autre moyen simple pour les administrateurs informatiques et les spécialistes de la conformité de Contoso d’accéder à la solution de conformité des communications consiste à se connecter directement au [portail de conformité Microsoft Purview](https://compliance.microsoft.com). Une fois connectés, les utilisateurs doivent simplement sélectionner le contrôle **Afficher tout** pour afficher toutes les solutions de conformité, puis sélectionner la solution **de conformité des communications** pour commencer.

![Centre de conformité.](../media/communication-compliance-compliance-portal.png)

### <a name="starting-from-the-microsoft-purview-solution-catalog"></a>À partir du catalogue de solutions Microsoft Purview

Les administrateurs informatiques et les spécialistes de la conformité de Contoso peuvent également choisir d’accéder à la solution de conformité des communications en sélectionnant le catalogue de solutions Microsoft Purview. En sélectionnant **Catalogue** dans la section **Solutions** du volet de navigation gauche dans le **portail de conformité Microsoft Purview**, ils peuvent ouvrir le catalogue de solutions répertoriant toutes les solutions Microsoft Purview. En faisant défiler vers le bas jusqu’à la section **Gestion des risques internes** , les administrateurs informatiques de Contoso peuvent sélectionner Conformité des communications pour commencer. Les administrateurs informatiques de Contoso décident également d’utiliser le contrôle Afficher dans la navigation pour épingler la solution de conformité des communications au volet de navigation gauche pour un accès plus rapide lorsqu’ils se connectent à l’avenir.

![Catalogue de solutions.](../media/m365-solution-catalog-home.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>À partir de la Centre d'administration Microsoft 365

Pour accéder à la conformité des communications à partir du Centre d'administration Microsoft 365, les administrateurs informatiques et les spécialistes de la conformité de Contoso se connectent au [Centre d'administration Microsoft 365](https://admin.microsoft.com) et accédez à [ portail de conformité Microsoft Purview](https://compliance.microsoft.com)

![Lien de conformité des communications.](../media/communication-compliance-case-compliance-link.png)

Cette action ouvre le **centre de sécurité et de conformité Office 365**, et ils doivent sélectionner le lien vers le **portail de conformité Microsoft Purview** fourni dans la bannière en haut de la page.

![Office 365 centre de sécurité et de conformité.](../media/communication-compliance-case-scc.png)

Une fois dans le **portail de conformité Microsoft Purview**, les administrateurs informatiques de Contoso **sélectionnent Afficher tout** pour afficher la liste complète des solutions de conformité.

![Menu Conformité des communications.](../media/communication-compliance-case-show-all.png)

Après avoir sélectionné **Afficher tout**, les administrateurs informatiques de Contoso peuvent accéder à la solution de conformité des communications.

![Vue d’ensemble de la conformité des communications.](../media/communication-compliance-case-overview.png)

## <a name="step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Étape 3 : Configuration des prérequis et création d’une stratégie de conformité des communications

Pour commencer à utiliser une stratégie de conformité des communications, les administrateurs informatiques de Contoso doivent configurer plusieurs prérequis avant de configurer la nouvelle stratégie afin de détecter le texte potentiellement inapproprié. Une fois ces prérequis remplis, les administrateurs informatiques et les spécialistes de la conformité de Contoso peuvent configurer la nouvelle stratégie, et les spécialistes de la conformité peuvent commencer à examiner et à corriger les alertes générées.

### <a name="enabling-auditing-in-microsoft-365"></a>Activation de l’audit dans Microsoft 365

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les mesures correctives prises par les réviseurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie organisationnelle définie ou à chaque modification d’une stratégie de conformité des communications.

Les administrateurs informatiques de Contoso étudient et complètent les [instructions pas à pas](/microsoft-365/compliance/turn-audit-log-search-on-or-off) pour activer l’audit. Après activation de l’audit, un message qui apparaît indique que le journal d’audit est en cours de préparation et qu’ils peuvent effectuer une recherche environ deux heures après la fin de la préparation. Les administrateurs informatiques de Contoso n’exécutent cette action qu’une seule fois.

### <a name="configuring-yammer-tenant-for-native-mode"></a>Configuration du locataire Yammer pour le mode natif

La conformité des communications exige que le locataire Yammer d’une organisation soit en mode natif pour détecter le texte potentiellement inapproprié dans les messages privés et les conversations de la communauté publique.

Les administrateurs informatiques de Contoso vérifient qu’ils passent en revue les informations de [l’article Vue d’ensemble du mode natif Yammer dans Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode) et suivent les étapes d’exécution de l’outil de migration dans l’article [Configurer votre réseau Yammer en mode natif pour Microsoft 365](/yammer/configure-your-yammer-network/native-mode) .

### <a name="setting-up-a-group-for-in-scope-users"></a>Configuration d’un groupe pour des utilisateurs dans l’étendue

Les spécialistes de la conformité contoso souhaitent ajouter tous les utilisateurs à la stratégie de communication qui détectera les messages potentiellement inappropriés. Ils peuvent décider d’ajouter séparément chaque compte d’utilisateur à la stratégie, mais ils ont décidé qu’il était beaucoup plus facile et d’utiliser un groupe de distribution **Tous les utilisateurs** pour les utilisateurs pour cette stratégie.

Ils doivent créer un groupe pour inclure tous les utilisateurs de Contoso. Ils doivent donc effectuer les étapes suivantes :

1. Les administrateurs informatiques de Contoso se connectent au [Centre d'administration Microsoft 365](https://admin.microsoft.com) et accédez à Centre d'administration Microsoft 365 > **Groupes** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
2. Ils sélectionnent **Ajouter un groupe** et terminent l’Assistant pour créer un *groupe Microsoft 365* ou un *groupe de distribution*.

    ![Groupes.](../media/communication-compliance-case-all-employees.png)

3. Une fois le groupe créé, ils doivent ajouter tous les utilisateurs Contoso à celui-ci. Ils ouvrent le [Centre d’administration Exchange](https://outlook.office365.com/ecp) et accèdent à <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**Groupes**</a> **de destinataires** >  du **Centre** >  d’administration Exchange. Les administrateurs informatiques de Contoso sélectionnent la zone Appartenance et le nouveau groupe *Tous les employés* qu’ils ont créés, puis sélectionnez le contrôle **Modifier** pour ajouter tous les utilisateurs Contoso au nouveau groupe dans l’Assistant.

    ![Centre d’administration Exchange.](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-detect-potentially-inappropriate-text"></a>Création de la stratégie pour détecter le texte potentiellement inapproprié

Une fois toutes les conditions préalables remplies, les administrateurs informatiques et les spécialistes de la conformité de Contoso sont prêts à configurer la stratégie de conformité des communications pour détecter les textes potentiellement inappropriés. À l’aide du modèle de stratégie de texte, la configuration de cette nouvelle stratégie est simple et rapide.

1. Les administrateurs informatiques et les spécialistes de la conformité de Contoso se connectent au **portail de conformité Microsoft Purview** et sélectionnent **Communication conformité** dans le volet de navigation de gauche. Cette action ouvre le tableau de bord qui contient des liens rapides pour les modèles de stratégie de conformité des communications. Ils choisissent **Stratégies**, font défiler jusqu’au modèle **Détecter le texte inapproprié** , puis **sélectionnent le modèle Créer une stratégie** .

    ![Modèle de texte de détection de conformité des communications inapproprié](../media/communication-compliance-case-template.png)

2. Dans l’Assistant modèle de stratégie, les administrateurs informatiques et les spécialistes de la conformité de Contoso collaborent pour compléter les trois champs obligatoires : **Nom de la stratégie**, **Utilisateurs ou groupes à surveiller**, puis **Réviseurs**.
3. Étant donné que l’Assistant de stratégie a déjà suggéré un nom pour la stratégie, les administrateurs informatiques et les spécialistes de la conformité décident de conserver le nom suggéré et de se concentrer sur les champs restants. Ils sélectionnent le groupe *Tous les utilisateurs* pour le champ **Utilisateurs ou groupes à superviser** , puis sélectionnent les spécialistes de la conformité qui doivent examiner et corriger les alertes de stratégie pour le champ **Réviseurs** . La dernière étape pour configurer la stratégie et commencer à collecter des informations d’alerte consiste à sélectionner **Créer une stratégie**.

    ![Assistant Détection de texte inapproprié pour la conformité des communications](../media/communication-compliance-case-wizard.png)

## <a name="step-4-investigate-and-remediate-alerts"></a>Étape 4 : Enquêter et corriger les alertes

Maintenant que la stratégie de conformité des communications pour détecter le texte potentiellement inapproprié est configurée, l’étape suivante pour les spécialistes de la conformité de Contoso consiste à examiner et à corriger toutes les alertes générées par la stratégie. Il faudra jusqu’à une heure pour que la stratégie traite entièrement les communications dans tous les canaux sources de communication et que les alertes s’affichent dans le **tableau de bord Alerte**.

Une fois les alertes générées, les spécialistes de la conformité contoso continueront de suivre [les instructions du flux de travail](/microsoft-365/compliance/communication-compliance-investigate-remediate) pour examiner et corriger les problèmes de texte potentiellement inappropriés.
