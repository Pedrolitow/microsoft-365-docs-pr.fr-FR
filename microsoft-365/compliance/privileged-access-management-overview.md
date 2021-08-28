---
title: En savoir plus sur la gestion des accès privilégiés
description: Cet article fournit une vue d’ensemble de la gestion des accès privilégiés dans Microsoft 365, y compris les réponses aux questions fréquemment posées (FAQ).
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
f1.keywords:
- NOCSH
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.openlocfilehash: e66f9133959ce7f09915361e7583ae809e33647e
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58567675"
---
# <a name="learn-about-privileged-access-management"></a>En savoir plus sur la gestion des accès privilégiés

La gestion des accès privilégiés permet de contrôler l’accès de manière granulaire sur les tâches d’administration privilégiée dans Office 365. Elle peut faciliter la protection de votre organisation contre des violations utilisant les comptes d’administration privilégiés existants avec un accès permanent aux données sensibles ou un accès aux paramètres de configuration critiques. La gestion des accès privilégiés exige que les utilisateurs demandent un accès en temps réel pour effectuer des tâches avec élévation de privilèges et privilégiées par le biais d’un flux de travail d’approbation très étendu et lié au temps. Cette configuration permet aux utilisateurs d’effectuer la tâche particulière, sans risque d’exposition aux données sensibles ou aux paramètres de configuration critiques. L’activation de la gestion des accès privilégiés dans Microsoft 365 permet à votre organisation de fonctionner avec zéro privilège permanent et de fournir une couche de défense contre les vulnérabilités d’accès administratifs.

Pour obtenir une vue d’ensemble rapide du flux de travail de gestion des accès privilégiés et customer Lockbox intégré, voir cette vidéo sur la gestion des accès privilégiés et [Customer Lockbox.](https://go.microsoft.com/fwlink/?linkid=2066800)

## <a name="layers-of-protection"></a>Niveaux de protection

La gestion de l’accès privilégié complète les autres protections de fonctionnalités d’accès et de données au sein de l’architecture de sécurité Microsoft 365. L’inclusion de la gestion de l’accès privilégié dans le cadre d’une approche intégrée et multiniveau de la sécurité fournit un modèle de sécurité qui optimise la protection des informations sensibles et des paramètres de configuration de Microsoft 365. Comme le montre le diagramme, la gestion de l’accès privilégié s’appuie sur la protection fournie avec le chiffrement natif des données Microsoft 365 et le modèle de sécurité de contrôle d’accès basé sur les rôles des services Microsoft 365. Lorsqu’elles sont [utilisées avec Azure AD Privileged Identity Management,](/azure/active-directory/active-directory-privileged-identity-management-configure)ces deux fonctionnalités fournissent un contrôle d’accès avec un accès juste-à-temps à différentes étendues.

![Protection en couches dans Microsoft 365.](../media/pam-layered-protection.png)

La gestion des accès privilégiés  est définie et étendue au niveau des tâches, tandis qu’Azure AD Privileged Identity Management applique une protection au niveau du rôle avec la possibilité d’exécuter plusieurs tâches.  Azure AD Privileged Identity Management permet principalement de gérer les accès aux rôles et aux groupes de rôles Azure AD, tandis que la gestion de l’accès privilégié dans Microsoft 365 s’applique uniquement au niveau de la tâche.

- **Activation de la gestion des accès privilégiés lors de l’utilisation d’Azure AD Privileged Identity Management :** L’ajout de la gestion des accès privilégiés fournit une couche granulaire de fonctionnalités de protection et d’audit pour l’accès privilégié Microsoft 365 données.

- **Activation d’Azure AD Privileged Identity Management tout en utilisant déjà** la gestion des accès privilégiés dans Office 365 :  L’ajout d’Privileged Identity Management Azure AD à la gestion des accès privilégiés peut étendre l’accès privilégié aux données en dehors des Microsoft 365 principalement définies par les rôles d’utilisateur ou l’identité.  

## <a name="privileged-access-management-architecture-and-process-flow"></a>Architecture et flux de processus de gestion des accès privilégiés

Chacun des flux de processus suivants décrit l’architecture de l’accès privilégié et la façon dont il interagit avec le substrat Microsoft 365, l’audit et l’espace d’Exchange management.

### <a name="step-1-configure-a-privileged-access-policy"></a>Étape 1 : Configurer une stratégie d’accès privilégié

Lorsque vous configurez une stratégie d’accès privilégié avec [Centre d’administration Microsoft 365](https://admin.microsoft.com) ou Exchange Management PowerShell, vous définissez la stratégie et les processus de fonctionnalité d’accès privilégié et les attributs de stratégie dans le substrat Microsoft 365. Les activités sont enregistrées dans le Centre de &amp; conformité de sécurité. La stratégie est désormais activée et prête à gérer les demandes entrantes pour approbation.

![Étape 1 : création de stratégie.](../media/pam-step1-policy-creation.jpg)

### <a name="step-2-access-request"></a>Étape 2 : Demande d’accès

Dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com) ou avec l’Exchange PowerShell de gestion, les utilisateurs peuvent demander l’accès à des tâches élevées ou privilégiées. La fonctionnalité d’accès privilégié envoie la demande au substrat Microsoft 365 pour traitement par rapport à la stratégie d’accès privilégié configurée et enregistre l’activité dans les journaux du Centre de conformité de &amp; sécurité.

![Étape 2 : Demande d’accès.](../media/pam-step2-access-request.jpg)

### <a name="step-3-access-approval"></a>Étape 3 : Approbation d’accès

Une demande d’approbation est établie et la notification de demande en attente est envoyée par e-mail aux approbateurs. En cas d’acceptation, la demande d’accès privilégié est traitée comme une approbation et la tâche est prête pour son exécution. En cas de refus, la tâche est bloquée et aucun accès n’est accordé au demandeur. Le demandeur est informé de l’approbation ou du refus par message électronique.

![Étape 3 : Approbation de l’accès.](../media/pam-step3-access-approval.jpg)

### <a name="step-4-access-processing"></a>Étape 4 : Traitement de l’accès

Pour une demande approuvée, la tâche est traitée par l’instance d’exécution d’Exchange Management. L’approbation est vérifiée par rapport à la stratégie d’accès privilégié et traitée par le substrat Microsoft 365. Toutes les activités de la tâche sont enregistrées dans le Centre de &amp; conformité de sécurité.

![Étape 4 : Traitement de l’accès.](../media/pam-step4-access-processing.jpg)

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="what-skus-can-use-privileged-access-in-office-365"></a>Quelles S SKUs peuvent utiliser l’accès privilégié dans Office 365 ?

La gestion des accès privilégiés est disponible pour les clients pour un large éventail d’abonnements Microsoft 365 et Office 365 et des modules. Pour [plus d’informations,](privileged-access-management-configuration.md) voir Prise en charge de la gestion des accès privilégiés.

### <a name="when-will-privileged-access-support-office-365-workloads-beyond-exchange"></a>Quand l’accès privilégié prendra-t-il en charge Office 365 charges de travail au-delà Exchange ?

La gestion des accès privilégiés sera bientôt disponible dans d’autres Office 365 charges de travail. Consultez la [Microsoft 365 feuille de route pour](https://www.microsoft.com/microsoft-365/roadmap) plus d’informations.

### <a name="my-organization-needs-more-than-30-privileged-access-policies-will-this-limit-be-increased"></a>Mon organisation a besoin de plus de 30 stratégies d’accès privilégié, cette limite sera-t-elle augmentée ?

Oui, l’augmentation de la limite actuelle de 30 stratégies d’accès privilégié par organisation se trouve dans la feuille de route des fonctionnalités.

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Ai-je besoin d’être administrateur global pour gérer l’accès privilégié dans Office 365 ?

Non, vous avez besoin du rôle Exchange gestion des rôles attribué aux comptes qui gèrent l’accès privilégié dans Office 365. Si vous ne souhaitez pas configurer le rôle gestion des rôles en tant qu’autorisation de compte autonome, le rôle Administrateur général inclut ce rôle par défaut et peut gérer l’accès privilégié. Les utilisateurs inclus dans un groupe d’approbations n’ont pas besoin d’être administrateur global ou le rôle de gestion des rôles est attribué pour examiner et approuver les demandes avec PowerShell.

### <a name="how-is-privileged-access-management-related-to-customer-lockbox"></a>Comment la gestion des accès privilégiés est-elle liée à Customer Lockbox ?

[Customer Lockbox autorise](/office365/admin/manage/customer-lockbox-requests) un niveau de contrôle d’accès pour les organisations lorsque Microsoft accède aux données. La gestion des accès privilégiés permet un contrôle d’accès granulaire au sein d’une organisation pour Microsoft 365 tâches privilégiées.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Commencez [à configurer votre organisation pour la gestion des accès privilégiés.](privileged-access-management-configuration.md)

## <a name="learn-more"></a>En savoir plus

[Guide interactif : Surveiller et contrôler les tâches d’administrateur avec la gestion des accès privilégiés](https://content.cloudguides.com/guides/Privileged%20Access%20Management)
