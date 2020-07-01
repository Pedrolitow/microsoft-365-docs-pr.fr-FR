---
title: Étude de cas-contoso configure rapidement une stratégie de langage offensant pour les communications Microsoft Teams, Exchange et Yammer
description: Une étude de cas pour contoso et la façon dont ils configurent rapidement une stratégie de conformité des communications pour surveiller le langage choquant dans Microsoft Teams, Exchange Online et les communications Yammer.
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
- remotework
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: d35179d38277ada22db9bc7ad879f1f7405a9aec
ms.sourcegitcommit: c43ebb915fa0eb7eb720b21b62c0d1e58e7cde3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "44936859"
---
# <a name="case-study---contoso-quickly-configures-an-offensive-language-policy-for-microsoft-teams-exchange-and-yammer-communications"></a>Étude de cas-contoso configure rapidement une stratégie de langage offensant pour les communications Microsoft Teams, Exchange et Yammer

La conformité de la communication dans Microsoft 365 aide à réduire les risques de communication en vous aidant à détecter, capturer et prendre des mesures correctives pour les messages inappropriés dans votre organisation. Les stratégies prédéfinies et personnalisées vous permettent d’analyser les communications internes et externes des correspondances de stratégie pour qu’elles puissent être examinées par les relecteurs désignés. Les relecteurs peuvent analyser les e-mails analysés, Microsoft Teams, Yammer ou des communications tierces de votre organisation et prendre les mesures correctives appropriées pour s’assurer qu’elles sont conformes aux standards de messages de votre organisation.

Contoso Corporation est une organisation fictive qui doit configurer rapidement une stratégie pour contrôler le langage choquant. Ils utilisaient principalement Microsoft 365 pour la messagerie, Microsoft teams et la prise en charge de Yammer pour leurs employés, mais ont de nouvelles exigences pour appliquer la stratégie de l’entreprise concernant Workplace harcèlement. Les administrateurs informatiques contoso et les spécialistes de la conformité ont une bonne compréhension des notions de base relatives à l’utilisation de Microsoft 365 et cherchent des conseils de bout en bout sur la mise en route rapide de la conformité de la communication.

Cette étude de cas aborde les concepts de base de la configuration rapide d’une stratégie de conformité des communications pour contrôler le langage choquant dans les communications. Ce guide se compose de :

- Étape 1 : Planifier la conformité des communications
- Étape 2 : Accéder à la conformité des communications dans Microsoft 365
- Étape 3 : Configuration des conditions préalables et création d’une stratégie de conformité des communications
- Étape 4 : Enquêtes et résolutions automatiques

## <a name="step-1-planning-for-communication-compliance"></a>Étape 1 : planification de la conformité de la communication

Les administrateurs informatiques et les spécialistes de la conformité de contoso ont participé à des conférences en ligne sur les solutions de conformité dans Microsoft 365 et ont décidé que les stratégies de conformité des communications les aident à répondre aux exigences de stratégie d’entreprise mises à jour pour réduire le harcèlement. En travaillant ensemble, ils ont développé un plan de création et d’activation d’une stratégie de conformité de communication qui analysera le langage offensant pour les conversations envoyées dans Microsoft Teams, les messages privés et les conversations communautaires dans Yammer, ainsi que dans les messages électroniques envoyés dans Exchange Online. Leur plan inclut les déterminations suivantes :

- Les administrateurs informatiques qui ont besoin d’accéder aux fonctionnalités de conformité des communications.
- Les spécialistes de la conformité qui ont besoin de créer et de gérer des stratégies de communication.
- Les spécialistes de la conformité et d’autres collègues d’autres services (ressources humaines, services juridiques, etc.) qui doivent examiner et corriger les alertes de conformité des communications.
- Les utilisateurs qui feront l’objet d’une stratégie de conformité de la communication.

### <a name="licensing"></a>Licence

La première étape consiste à vérifier que les licences Microsoft 365 de contoso incluent la prise en charge de la solution de conformité des communications. Pour accéder à la conformité de la communication et l’utiliser, les administrateurs informatiques de contoso doivent vérifier que contoso dispose de l’un des éléments suivants :

- Abonnement Microsoft 365 E5 (payant ou version d’évaluation)
- Microsoft 365 E3 subscription + le complément de conformité Microsoft 365 E5
- Microsoft 365 E3 subscription + le complément de gestion des risques de Microsoft 365 E5 Insider
- Abonnement Microsoft 365 a5 (payant ou version d’évaluation)
- Abonnement Microsoft 365 a3 + complément Microsoft 365 a5 Compliance
- Abonnement Microsoft 365 a3 + complément de gestion des risques Microsoft 365 a5 Insider
- Abonnement Microsoft 365 G5 (payant ou version d’évaluation)
- Abonnement Microsoft 365 G5 + le complément de conformité Microsoft 365 G5
- Abonnement Microsoft 365 G5 + le complément de gestion des risques Microsoft 365 G5 Insider
- Office 365 entreprise E5 abonnement (payant ou version d’évaluation)
- Office 365 entreprise E3 abonnement + le complément Office 365 Advanced Compliance (qui n’est plus disponible pour les nouveaux abonnements, reportez-vous à la rubrique note)

Ils doivent également confirmer que les utilisateurs inclus dans les stratégies de conformité des communications doivent disposer de l’une des licences ci-dessus.

>[!IMPORTANT]
>Office 365 Advanced Compliance n’est plus vendu en tant qu’abonnement autonome. Lorsque les abonnements actuels arrivent à expiration, les clients doivent effectuer une transition vers l’un des abonnements ci-dessus, qui contiennent les mêmes fonctionnalités de conformité ou des fonctionnalités de conformité supplémentaires.

Les administrateurs informatiques de contoso effectuent les opérations suivantes pour vérifier la prise en charge des licences pour Contoso :

1. Les administrateurs informatiques se connectent au **Centre d’administration Microsoft 365** [( https://admin.microsoft.com) ](https://admin.microsoft.com) pour accéder aux licences de facturation du centre d' **administration Microsoft 365**  >  **Billing**  >  **Licenses**.

2. Ils confirment qu’ils disposent d’une des [options de licence](https://docs.microsoft.com/microsoft-365/compliance/communication-compliance-configure?view=o365-worldwide#before-you-begin) qui incluent la prise en charge de la conformité de communication.

![Licence de conformité des communications](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Autorisations pour la conformité des communications

Par défaut, les administrateurs globaux n’ont pas accès aux fonctionnalités de conformité des communications. [Les autorisations doivent être configurées](https://docs.microsoft.com/microsoft-365/compliance/communication-compliance-configure?view=o365-worldwide#step-1-required-enable-permissions-for-communication-compliance) pour que les administrateurs informatiques et les spécialistes de la conformité de Contoso aient accès à la conformité des communications.

1. Les administrateurs informatiques de contoso se connectent à la page autorisations du **Centre de sécurité et de conformité Office 365** [( https://protection.office.com/permissions) ](https://protection.office.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur général et sélectionnent le lien pour afficher et gérer les rôles dans Microsoft 365.
2. Après avoir sélectionné **créer**, le nouveau groupe de rôles a le nom convivial «*conformité*de la communication », puis sélectionnez **suivant**.
3. Ils cliquent sur **Sélectionner des rôles**, puis sélectionnent **Ajouter**. Ils ajoutent les rôles requis en activant la case à cocher *administrateur de révision de surveillance*, gestion des *cas*, *administrateur de conformité*et *révision*, puis sélectionnez **Ajouter**, **Terminer** et **suivant**.

![Rôles de conformité de communication](../media/communication-compliance-case-roles.png)

4. Les administrateurs informatiques choisissent ensuite **Sélectionner des membres** puis cliquent sur **Ajouter**. Activez la case à cocher pour tous les utilisateurs et les groupes pour lesquels ils veulent créer des stratégies et gérer les messages avec des correspondances de stratégie. Ils ajoutent les administrateurs informatiques, les spécialistes de la conformité et d’autres collègues des Ressources Humaines et du Service Juridique qu’ils ont identifiés dans le cadre de la planification initiale, puis sélectionnent **Ajouter**, **Terminé**, puis **Suivant**.
5. Pour finaliser les autorisations, les administrateurs informatiques sélectionnent **Créer un groupe de rôles** pour terminer. La prise en compte effective des rôles dans Contoso par le service Microsoft 365 prend environ 30 minutes.

![Examen de conformité de la communication](../media/communication-compliance-case-review.png)

## <a name="step-2-accessing-communication-compliance-in-microsoft-365"></a>Étape 2 : accès à la conformité de la communication dans Microsoft 365

Après configuration des autorisations pour la conformité des communications, les administrateurs informatiques et les spécialistes de la conformité de Contoso définis dans le nouveau groupe de rôles peuvent accéder à la solution de conformité des communications dans Microsoft 365. Les administrateurs informatiques contoso et les spécialistes de la conformité disposent de plusieurs méthodes pour accéder à la conformité de la communication et commencer à créer une nouvelle stratégie :

- En commençant directement à partir de la solution de conformité de communication
- À partir du centre de conformité Microsoft 365
- À partir du catalogue de solutions Microsoft 365
- À partir du centre d’administration Microsoft 365

### <a name="starting-directly-from-the-communication-compliance-solution"></a>En commençant directement à partir de la solution de conformité de communication

Le moyen le plus rapide d’accéder à la solution est de se connecter directement à la solution de **conformité des communications** ( <https://compliance.microsoft.com/supervisoryreview> ). À l’aide de ce lien, les administrateurs informatiques contoso et les spécialistes de la conformité seront dirigés vers le tableau de bord de présentation de la conformité des communications, qui vous permet de consulter rapidement l’état des alertes et de créer de nouvelles stratégies à partir des modèles prédéfinis.

![Présentation de la conformité des communications](../media/communication-compliance-case-overview.png)

### <a name="starting-from-the-microsoft-365-compliance-center"></a>À partir du centre de conformité Microsoft 365

Un autre moyen simple pour les administrateurs informatiques contoso et les spécialistes de la conformité à accéder à la solution de conformité des communications est de se connecter directement au **Centre de conformité Microsoft 365** [( https://compliance.microsoft.com) ](https://compliance.microsoft.com). Une fois connectés, les utilisateurs doivent simplement sélectionner le contrôle **Afficher tout** pour exposer toutes les solutions de conformité, puis sélectionner la solution **Conformité des communications** pour démarrer.

![Centre de conformité](../media/communication-compliance-case-center.png)

### <a name="starting-from-the-microsoft-365-solution-catalog"></a>À partir du catalogue de solutions Microsoft 365

Les administrateurs informatiques contoso et les spécialistes de la conformité peuvent également choisir d’accéder à la solution de conformité des communications en sélectionnant le catalogue de solutions Microsoft 365. En sélectionnant **catalogue** dans la section **solutions** du volet de navigation de gauche dans le **Centre de conformité Microsoft 365**, il peut ouvrir le catalogue de solutions répertoriant toutes les solutions de conformité Microsoft 365. En faisant défiler jusqu’à la section **gestion des risques Insiders** , les administrateurs informatiques de contoso peuvent sélectionner la conformité des communications pour commencer. Les administrateurs informatiques de contoso décident également d’utiliser le diaporama dans le contrôle de navigation pour épingler la solution de conformité de communication dans le volet de navigation de gauche pour un accès plus rapide lorsqu’ils se connectent à l’avenir.

![Catalogue de solutions](../media/communication-compliance-case-solution.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>À partir du centre d’administration Microsoft 365

Pour accéder à la conformité de la communication lorsque vous démarrez à partir du centre d’administration Microsoft 365, les administrateurs informatiques contoso et les spécialistes de la conformité se connectent au centre d’administration de Microsoft 365 [( https://admin.microsoft.com) ](https://admin.microsoft.com) et naviguent vers la conformité du **Centre d’administration Microsoft 365**  >  **Compliance**.

![Lien de conformité de la communication](../media/communication-compliance-case-compliance-link.png)

Le centre de **sécurité et conformité Office 365**s’ouvre et vous devez sélectionner le lien vers le **Centre de conformité Microsoft 365** fourni dans la bannière en haut de la page.

![Centre de sécurité et conformité Office 365](../media/communication-compliance-case-scc.png)

Une fois dans le **Centre de conformité Microsoft 365**, les administrateurs informatiques de contoso peuvent sélectionner **Afficher tout** pour afficher la liste complète des solutions de conformité.

![Menu conformité de la communication](../media/communication-compliance-case-show-all.png)

Une fois que vous avez sélectionné **Afficher tout**, les administrateurs informatiques de contoso peuvent accéder à la solution de conformité de communication.

![Présentation de la conformité des communications](../media/communication-compliance-case-overview.png)

## <a name="step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Étape 3 : configuration des éléments prérequis et de la création d’une stratégie de conformité des communications

Afin de démarrer la stratégie de conformité des communications, les administrateurs informatiques de Contoso doivent configurer plusieurs prérequis avant de définir la nouvelle stratégie pour contrôler le langage choquant. Une fois ces conditions préalables achevées, les administrateurs informatiques et les spécialistes de la conformité de Contoso peuvent configurer la nouvelle stratégie et les spécialistes de la conformité peuvent démarrer une enquête et corriger les alertes générées.

### <a name="enabling-auditing-in-microsoft-365"></a>Activation de l’audit dans Microsoft 365

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les mesures correctives prises par les réviseurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie d’organisation définie, ou à chaque fois qu’une modification intervient dans une stratégie de conformité aux communications.

Les administrateurs informatiques de Contoso étudient et complètent les [instructions pas à pas](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off) pour activer l’audit. Après activation de l’audit, un message qui apparaît indique que le journal d’audit est en cours de préparation et qu’ils peuvent effectuer une recherche environ deux heures après la fin de la préparation. Les administrateurs informatiques de Contoso n’exécutent cette action qu’une seule fois.

### <a name="configuring-yammer-tenant-for-native-mode"></a>Configuration du client Yammer pour le mode natif

La conformité de la communication nécessite que le client Yammer d’une organisation soit en mode natif pour surveiller le langage choquant dans les messages privés et les conversations de la communauté publique.

Les administrateurs informatiques de contoso doivent vérifier les informations dans la [rubrique vue d’ensemble du mode natif Yammer dans Microsoft 365](https://docs.microsoft.com/yammer/configure-your-yammer-network/overview-native-mode) et suivre les étapes nécessaires à l’exécution de l’outil de migration dans la rubrique [Configure Your Yammer Network for Native Mode for Microsoft 365](https://docs.microsoft.com/yammer/configure-your-yammer-network/native-mode) .

### <a name="setting-up-a-group-for-in-scope-users"></a>Configuration d’un groupe pour des utilisateurs dans l’étendue

Les spécialistes de la conformité de Contoso souhaitent ajouter tous les employés à la stratégie des communications qui contrôle le langage choquant. Ils peuvent choisir d’ajouter séparément chaque compte d’utilisateur employé à la stratégie, mais ils déterminent qu’il est plus facile et rapide d’utiliser un groupe de distribution **Tous les employés** pour les utilisateurs de cette stratégie.

Ils doivent créer un groupe pour inclure tous les employés de Contoso afin d’effectuer les étapes suivantes :

1. Les administrateurs informatiques contoso se connectent au **Centre d’administration Microsoft 365** [( https://admin.microsoft.com) ](https://admin.microsoft.com) et naviguent vers le **Centre d’administration Microsoft 365**  >  **groupes**  >  **Groups**.
2. Ils sélectionnent **Ajouter un groupe** et terminent l’Assistant pour créer un groupe de *distribution*ou un groupe *Microsoft 365* .

![Groupes](../media/communication-compliance-case-all-employees.png)

3. Une fois le groupe créé, ils doivent ajouter tous les utilisateurs Contoso à celui-ci. Ils ouvrent le **Centre d’administration Exchange** [ https://outlook.office365.com/ecp) (](https://outlook.office365.com/ecp) et naviguent jusqu’à groupes de destinataires du centre d' **administration Exchange**)  >  **recipients**  >  **groups**. Les administrateurs informatiques de Contoso sélectionnent la zone de l’Appartenance et le groupe *Tous les employés* qu’ils ont créé, puis sélectionnent le contrôle **Modifier** pour ajouter tous les employés de Contoso au nouveau groupe dans l’Assistant.

![Centre d’administration Exchange](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-monitor-for-offensive-language"></a>Création de la stratégie pour contrôler le langage choquant

Une fois toutes les conditions préalables remplies, les administrateurs informatiques et les spécialistes de la conformité de Contoso sont prêts à configurer la stratégie de conformité des communications pour surveiller le langage grossier. La configuration de cette stratégie à l’aide du nouveau modèle de stratégie de langage grossier est simple et rapide.

1. Les administrateurs informatiques et les spécialistes de la conformité de Contoso se connectent au **Centre de conformité Microsoft 365**, puis sélectionnent **Conformité des communications** dans le volet de navigation gauche. Cette action ouvre le tableau de bord de **Vue d’ensemble** comportant des liens rapides pour des modèles de stratégie de conformité des communications. Ils choisissent le modèle **Surveiller le langage offensant** en sélectionnant **Commencer** pour le modèle.

![Modèle de langue offensant de conformité de communication](../media/communication-compliance-case-template.png)

2. Dans l’Assistant modèle de stratégie, les administrateurs informatiques et les spécialistes de la conformité de Contoso collaborent pour compléter les trois champs obligatoires : **Nom de la stratégie**, **Utilisateurs ou groupes à surveiller**, puis **Réviseurs**.
3. Étant donné que l’Assistant de stratégie a déjà suggéré un nom pour la stratégie, les administrateurs informatiques et les spécialistes de la conformité décident de conserver le nom suggéré et de se concentrer sur les champs restants. Ils sélectionnent le groupe *tous les employés* pour le champ **utilisateurs ou groupes à superviser** et sélectionnent les spécialistes de la conformité qui doivent examiner et corriger les alertes de stratégie pour le champ **Relecteurs** . La dernière étape de configuration de la stratégie et de démarrage de la collecte des informations d’alerte consiste à sélectionner **créer une stratégie**.

![Assistant langue offensant de conformité de la communication](../media/communication-compliance-case-wizard.png)

## <a name="step-4-investigate-and-remediate-alerts"></a>Étape 4 : examiner et corriger les alertes

À présent que la stratégie de conformité des communications est configurée pour surveiller le langage choquant, l’étape suivante pour les spécialistes de la conformité de Contoso est d’enquêter et de corriger les alertes générées par la stratégie. Le traitement total des communications dans tous les canaux sources par la stratégie et l’affichage des alertes dans le **Tableau de bord d’alerte** peut prendre jusqu’à 24 heures.

Une fois les alertes générées, les spécialistes de conformité de contoso suivront les [instructions de flux de travail](https://docs.microsoft.com/microsoft-365/compliance/communication-compliance-investigate-remediate) pour examiner et corriger les problèmes de langue offensants.