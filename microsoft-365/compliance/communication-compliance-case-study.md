---
title: 'Etude de cas : contoso configure rapidement une stratégie de langue offensante'
description: Une étude de cas pour contoso et la façon dont ils configurent rapidement une stratégie de conformité des communications pour surveiller le langage choquant dans Microsoft teams et les communications Exchange Online
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
ms.openlocfilehash: 6b5ce3b9ca738ddf94edbb035daeb730f5e3f96a
ms.sourcegitcommit: 242f051c4cf3683f8c1a5da20ceca81bde212cfc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "42982354"
---
# <a name="case-study---contoso-quickly-configures-an-offensive-language-policy"></a>Etude de cas : contoso configure rapidement une stratégie de langue offensante

La conformité de la communication dans Microsoft 365 aide à réduire les risques de communication en vous aidant à détecter, capturer et prendre des mesures correctives pour les messages inappropriés dans votre organisation. Les stratégies prédéfinies et personnalisées vous permettent d’analyser les communications internes et externes des correspondances de stratégie pour qu’elles puissent être examinées par les relecteurs désignés. Les relecteurs peuvent analyser les e-mails analysés, Microsoft teams ou les communications tierces au sein de votre organisation et prendre les mesures correctives appropriées pour s’assurer qu’ils sont conformes aux standards de messages de votre organisation.

Contoso Corporation est une organisation fictive qui doit rapidement configurer une stratégie pour surveiller le langage offensant. Ils utilisaient principalement Microsoft 365 pour le courrier électronique et la prise en charge de Microsoft teams pour leurs employés, mais ont de nouvelles exigences pour appliquer la stratégie de l’entreprise concernant Workplace harcèlement. Les administrateurs informatiques contoso et les spécialistes de la conformité ont une bonne compréhension des notions de base relatives à l’utilisation de Microsoft 365 et cherchent des conseils de bout en bout sur la mise en route rapide de la conformité de la communication.

Cette étude de cas portera sur les principes de base permettant de configurer rapidement une stratégie de conformité des communications pour surveiller les communications dans un langage offensant. Ce guide inclut les éléments suivants :

- Étape 1 : planification de la conformité de la communication
- Étape 2 : accès à la conformité de communication dans Microsoft 365
- Étape 3 : configuration des éléments prérequis et de la création d’une stratégie de conformité des communications
- Étape 4 : enquête et correction des alertes

## <a name="step-1---planning-for-communication-compliance"></a>Étape 1 : planification de la conformité de la communication

Les administrateurs informatiques contoso et les spécialistes en conformité ont participé à des conférences en ligne sur les solutions de conformité dans Microsoft 365 et décidé que les stratégies de conformité des communications les aident à répondre aux exigences de stratégie d’entreprise mises à jour pour la réduction du travail. harcèle. En travaillant ensemble, ils ont développé un plan de création et d’activation d’une stratégie de conformité de communication qui analysera le langage offensant pour les conversations envoyées dans Microsoft teams dans les messages électroniques envoyés dans Exchange Online. Leur plan inclut l’identification des éléments suivants :

- Les administrateurs informatiques qui ont besoin d’accéder aux fonctionnalités de conformité des communications.
- Les spécialistes de la conformité qui ont besoin de créer et de gérer des stratégies de communication.
- Les spécialistes de la conformité et d’autres collègues d’autres services (ressources humaines, services juridiques, etc.) qui doivent examiner et corriger les alertes de conformité des communications.
- Les utilisateurs qui feront l’objet d’une stratégie de conformité de la communication.

### <a name="licensing"></a>Licence

La première étape consiste à vérifier que les licences Microsoft 365 de contoso incluent la prise en charge de la solution de conformité des communications. Pour accéder à la conformité de la communication et l’utiliser, les administrateurs informatiques de contoso doivent vérifier que contoso dispose de l’un des éléments suivants :

- Abonnement Microsoft 365 E5 (payant ou version d’évaluation)
- Office 365 entreprise E3 avec le complément de conformité avancé
- Office 365 entreprise E5 abonnement (payant ou version d’évaluation)

Ils doivent également confirmer que les utilisateurs inclus dans les stratégies de conformité des communications doivent être affectés à l’une des licences répertoriées ci-dessus.

Les administrateurs informatiques de contoso effectuent les opérations suivantes pour vérifier la prise en charge des licences pour Contoso :

1. Les administrateurs informatiques se connectent **au centre d’administration Microsoft 365** [(https://admin.microsoft.com) ](https://admin.microsoft.com) pour accéder aux**licences**de**facturation** > du centre > d' **administration Microsoft 365**.

2. Ils confirment qu’ils disposent d’une des [options de licence](https://docs.microsoft.com/microsoft-365/compliance/communication-compliance-configure?view=o365-worldwide#before-you-begin) qui incluent la prise en charge de la conformité de communication.

![Licence de conformité des communications](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Autorisations pour la conformité des communications

Par défaut, les administrateurs globaux n’ont pas accès aux fonctionnalités de conformité des communications. Les [autorisations doivent être configurées](https://docs.microsoft.com/microsoft-365/compliance/communication-compliance-configure?view=o365-worldwide#step-1-required-enable-permissions-for-communication-compliance) de sorte que les administrateurs informatiques contoso et les spécialistes de la conformité aient accès à la conformité de la communication.

1. Les administrateurs informatiques de contoso se connectent à la page autorisations du **Centre de sécurité et de conformité Office 365** [(https://protection.office.com/permissions) ](https://protection.office.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur général et sélectionnent le lien pour afficher et gérer les rôles dans Office 365.
2. Après avoir sélectionné **créer**, le nouveau groupe de rôles a le nom convivial «*conformité*de la communication », puis sélectionnez **suivant**.
3. Sélectionnez **choisir les rôles** , puis **Ajouter**. Ils ajoutent les rôles requis en activant la case à cocher *administrateur de révision de surveillance*, gestion des *cas*, *administrateur de conformité*et *révision*, puis sélectionnez **Ajouter**, **Terminer** et **suivant**.

![Rôles de conformité de communication](../media/communication-compliance-case-roles.png)

4. Ensuite, les administrateurs informatiques peuvent sélectionner **choisir les membres** , puis **Ajouter**. Activez la case à cocher pour tous les utilisateurs et les groupes pour lesquels ils veulent créer des stratégies et gérer les messages avec des correspondances de stratégie. Ils ajoutent les administrateurs informatiques, les spécialistes de la conformité et d’autres collègues aux services légaux et aux ressources humaines qu’ils ont identifiés lors de la planification initiale, puis sélectionnez **Ajouter**, **Terminer**et **suivant**.
5. Pour finaliser les autorisations, les administrateurs informatiques peuvent sélectionner **créer un groupe de rôles** à terminer. Il faudra environ 30 minutes pour que les rôles soient efficaces dans le service Microsoft 365 de contoso.

![Examen de conformité de la communication](../media/communication-compliance-case-review.png)

## <a name="step-2---accessing-communication-compliance-in-microsoft-365"></a>Étape 2 : accès à la conformité de communication dans Microsoft 365

Après avoir configuré les autorisations pour la conformité des communications, les administrateurs informatiques contoso et les spécialistes de la conformité définis dans le nouveau groupe de rôles peuvent accéder à la solution de conformité de la communication dans Microsoft 365. Les administrateurs informatiques contoso et les spécialistes de la conformité disposent de plusieurs méthodes pour accéder à la conformité de la communication et commencer à créer une nouvelle stratégie :

- En commençant directement à partir de la solution de conformité de communication
- À partir du centre de conformité Microsoft 365
- À partir du catalogue de solutions Microsoft 365
- À partir du centre d’administration Microsoft 365

### <a name="starting-directly-from-the-communication-compliance-solution"></a>En commençant directement à partir de la solution de conformité de communication

Le moyen le plus rapide d’accéder à la solution est de se connecter directement à la solution<https://compliance.microsoft.com/supervisoryreview>de conformité des **communications** (). À l’aide de ce lien, les administrateurs informatiques contoso et les spécialistes de la conformité seront dirigés vers le tableau de bord de présentation de la conformité des communications, qui vous permet de consulter rapidement l’état des alertes et de créer de nouvelles stratégies à partir des modèles prédéfinis.

![Présentation de la conformité de la communication](../media/communication-compliance-case-overview.png)

### <a name="starting-from-the-microsoft-365-compliance-center"></a>À partir du centre de conformité Microsoft 365

Un autre moyen simple pour les administrateurs informatiques contoso et les spécialistes de la conformité à accéder à la solution de conformité des communications est de se connecter directement au **Centre de conformité Microsoft 365** [(https://compliance.microsoft.com)](https://compliance.microsoft.com). Une fois connecté, les utilisateurs doivent simplement sélectionner le contrôle **Afficher tout** pour afficher toutes les solutions de conformité, puis sélectionner la solution de **conformité des communications** pour commencer.

![Centre de conformité](../media/communication-compliance-case-center.png)

### <a name="starting-from-the-microsoft-365-solution-catalog"></a>À partir du catalogue de solutions Microsoft 365

Les administrateurs informatiques contoso et les spécialistes de la conformité peuvent également choisir d’accéder à la solution de conformité des communications en sélectionnant le catalogue de solutions Microsoft 365. En sélectionnant **catalogue** dans la section **solutions** du volet de navigation de gauche dans le **Centre de conformité Microsoft 365**, il peut ouvrir le catalogue de solutions répertoriant toutes les solutions de conformité Microsoft 365. En faisant défiler jusqu’à la section **gestion des risques Insiders** , les administrateurs informatiques de contoso peuvent sélectionner la conformité des communications pour commencer. Les administrateurs informatiques de contoso décident également d’utiliser le diaporama dans le contrôle de navigation pour épingler la solution de conformité de communication dans le volet de navigation de gauche pour un accès plus rapide lorsqu’ils se connectent à l’avenir.

![Catalogue de solutions](../media/communication-compliance-case-solution.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>À partir du centre d’administration Microsoft 365

Pour accéder à la conformité de la communication lorsque vous démarrez à partir du centre d’administration Microsoft 365, les administrateurs informatiques contoso et les spécialistes de la conformité se connectent au centre d’administration de Microsoft 365 [https://admin.microsoft.com) (](https://admin.microsoft.com) et naviguent vers la > **conformité**du **Centre d’administration Microsoft 365**.

![Lien de conformité de la communication](../media/communication-compliance-case-compliance-link.png)

Le centre de **sécurité et conformité Office 365**s’ouvre et vous devez sélectionner le lien vers le **Centre de conformité Microsoft 365** fourni dans la bannière en haut de la page.

![Centre de sécurité et conformité Office 365](../media/communication-compliance-case-scc.png)

Une fois dans le **Centre de conformité Microsoft 365**, les administrateurs informatiques de contoso peuvent sélectionner **Afficher tout** pour afficher la liste complète des solutions de conformité.

![Menu conformité de la communication](../media/communication-compliance-case-show-all.png)

Une fois que vous avez sélectionné **Afficher tout**, les administrateurs informatiques de contoso peuvent accéder à la solution de conformité de communication.

![Présentation de la conformité de la communication](../media/communication-compliance-case-overview.png)

## <a name="step-3---configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Étape 3 : configuration des éléments prérequis et de la création d’une stratégie de conformité des communications

Pour commencer à utiliser une stratégie de conformité des communications, il existe plusieurs conditions préalables que les administrateurs informatiques de contoso doivent configurer avant de configurer la nouvelle stratégie pour surveiller le langage offensant. Une fois ces conditions préalables terminées, les administrateurs informatiques de contoso et les spécialistes de la conformité peuvent configurer la nouvelle stratégie et les spécialistes de la conformité peuvent lancer une enquête et corriger les alertes générées.

### <a name="enabling-auditing-in-office-365"></a>Activation de l’audit dans Office 365

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les actions de correction effectuées par les relecteurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie d’organisation définie ou à chaque fois qu’une stratégie de conformité des communications est modifiée.

Les administrateurs informatiques de contoso examinent et exécutent les [instructions pas à pas](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off) pour activer l’audit. Une fois l’audit activé, un message s’affiche indiquant que le journal d’audit est en cours de préparation et qu’il peut exécuter une recherche dans quelques heures après la fin de la préparation. Les administrateurs informatiques de contoso ne doivent effectuer cette action qu’une seule fois.

### <a name="setting-up-a-group-for-in-scope-users"></a>Configuration d’un groupe pour les utilisateurs dans l’étendue

Les spécialistes de la conformité de contoso souhaitent ajouter tous les employés à la stratégie de communication qui analysera le langage offensant. Ils peuvent décider d’ajouter chaque compte d’utilisateur employé à la stratégie séparément, mais ils ont décidé qu’il est beaucoup plus facile et gagner beaucoup de temps à utiliser un groupe de distribution **tous les employés** pour les utilisateurs de cette stratégie.

Ils doivent créer un groupe pour inclure tous les employés de contoso, de sorte qu’ils effectuent les opérations suivantes :

1. Les administrateurs informatiques contoso se connectent au **Centre d’administration Microsoft 365** [(https://admin.microsoft.com) ](https://admin.microsoft.com) et naviguent vers le centre**Groups** > **Groups** > d' **administration Microsoft 365**groupes.
2. Ils sélectionnent **Ajouter un groupe** et terminent l’Assistant pour créer un groupe de *distribution*ou un groupe *Office 365* .

![Groupes](../media/communication-compliance-case-all-employees.png)

3. Après avoir créé le groupe, vous devez ajouter tous les utilisateurs contoso au nouveau groupe. Ils ouvrent **le centre d’administration Exchange** [https://outlook.office365.com/ecp) (](https://outlook.office365.com/ecp) et naviguent jusqu’à**groupes**de**destinataires** > du **Centre** > d’administration Exchange). Les administrateurs informatiques de contoso peuvent sélectionner la zone appartenance et le nouveau groupe *tous les employés* qu’ils ont créés et sélectionner le contrôle d' **édition** pour ajouter tous les employés contoso au nouveau groupe dans l’Assistant.

![Centre d’administration Exchange](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-monitor-for-offensive-language"></a>Création de la stratégie à surveiller pour le langage offensant

Une fois tous les éléments prérequis terminés, les administrateurs informatiques et les spécialistes de la conformité pour Contoso sont prêts à configurer la stratégie de conformité des communications pour surveiller le langage offensant. En utilisant le nouveau modèle de stratégie de langue offensant, la configuration de cette stratégie est simple et rapide.

1. Les administrateurs informatiques contoso et les spécialistes de la conformité se connectent au **Centre de conformité Microsoft 365** et sélectionnent **conformité des communications** dans le volet de navigation de gauche. Cette action ouvre le tableau de bord de **Présentation** qui contient des liens rapides pour les modèles de stratégie de conformité de communication. Ils choisissent le modèle **de langue de surveillance pour offensant** en sélectionnant **prendre en main** pour le modèle.

![Modèle de langue offensant de conformité de communication](../media/communication-compliance-case-template.png)

2. Dans l’Assistant modèle de stratégie, les administrateurs et les spécialistes de la conformité de contoso travaillent ensemble pour remplir les trois champs obligatoires : nom de la **stratégie**, **utilisateurs ou groupes à superviser**et **Relecteurs**.
3. Étant donné que l’Assistant stratégie a déjà suggéré un nom pour la stratégie, les administrateurs informatiques et les spécialistes de la conformité décident de conserver le nom suggéré et de se concentrer sur les champs restants. Ils sélectionnent le groupe *tous les employés* pour le champ **utilisateurs ou groupes à superviser** et sélectionnent les spécialistes de la conformité qui doivent examiner et corriger les alertes de stratégie pour le champ **Relecteurs** . La dernière étape de configuration de la stratégie et de démarrage de la collecte des informations d’alerte consiste à sélectionner **créer une stratégie**.

![Assistant langue offensant de conformité de la communication](../media/communication-compliance-case-wizard.png)

## <a name="step-4--investigate-and-remediate-alerts"></a>Étape 4 – examiner et corriger les alertes

Maintenant que la stratégie de conformité de la communication à surveiller pour un langage offensant est configurée, l’étape suivante pour les spécialistes de la conformité de contoso est d’examiner et de corriger les alertes générées par la stratégie. Jusqu’à 24 heures peuvent être nécessaires pour que la stratégie traite entièrement les communications de tous les canaux sources de communication et pour que les alertes s’affichent dans le **tableau de bord d’alerte**.

Une fois les alertes générées, les spécialistes de conformité de contoso suivront les [instructions de flux de travail](https://docs.microsoft.com/microsoft-365/compliance/communication-compliance-investigate-remediate) pour examiner et corriger les problèmes de langue offensants.
