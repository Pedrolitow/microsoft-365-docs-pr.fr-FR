---
title: En savoir plus sur la gestion des accès privilégiés
description: Cet article fournit une vue d’ensemble de la gestion des accès privilégiés dans Microsoft Purview, y compris des réponses aux questions fréquentes (FAQ).
keywords: Microsoft 365, Microsoft Purview, conformité, gestion des accès privilégiés
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
f1.keywords:
- NOCSH
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- highpri
- tier3
- purview-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- highpri
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.openlocfilehash: 2f00f1898ccdf5505a0b4873ff83485e065320bf
ms.sourcegitcommit: b439d097e55bba35d9328447d993bbcac7a178a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68802958"
---
# <a name="learn-about-privileged-access-management"></a>En savoir plus sur la gestion des accès privilégiés

Microsoft Purview Privileged Access Management permet un contrôle d’accès granulaire sur les tâches d’administration privilégiées dans Office 365. Elle peut faciliter la protection de votre organisation contre des violations utilisant les comptes d’administration privilégiés existants avec un accès permanent aux données sensibles ou un accès aux paramètres de configuration critiques. La gestion des accès privilégiés exige que les utilisateurs demandent un accès en temps réel pour effectuer des tâches avec élévation de privilèges et privilégiées par le biais d’un flux de travail d’approbation très étendu et lié au temps. Cette configuration permet aux utilisateurs d’effectuer la tâche particulière, sans risque d’exposition aux données sensibles ou aux paramètres de configuration critiques. L’activation de la gestion des accès privilégiés permet à votre organisation de fonctionner sans privilèges permanents et de fournir une couche de défense contre les vulnérabilités d’accès administratif permanents.

Pour obtenir une vue d’ensemble rapide du flux de travail intégré Customer Lockbox et de la gestion des accès privilégiés, consultez cette [vidéo Customer Lockbox et la gestion des accès privilégiés](https://go.microsoft.com/fwlink/?linkid=2066800).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="layers-of-protection"></a>Niveaux de protection

La gestion de l’accès privilégié complète les autres protections de fonctionnalités d’accès et de données au sein de l’architecture de sécurité Microsoft 365. L’inclusion de la gestion de l’accès privilégié dans le cadre d’une approche intégrée et multiniveau de la sécurité fournit un modèle de sécurité qui optimise la protection des informations sensibles et des paramètres de configuration de Microsoft 365. Comme le montre le diagramme, la gestion de l’accès privilégié s’appuie sur la protection fournie avec le chiffrement natif des données Microsoft 365 et le modèle de sécurité de contrôle d’accès basé sur les rôles des services Microsoft 365. Lorsqu’elles sont utilisées avec [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure), ces deux fonctionnalités fournissent un contrôle d’accès avec un accès juste-à-temps à différentes étendues.

![Protection en couches dans Microsoft 365.](../media/pam-layered-protection.png)

La gestion des accès privilégiés est définie et étendue au niveau de la **tâche**, tandis qu’Azure AD Privileged Identity Management applique une protection au niveau du **rôle** avec la possibilité d’exécuter plusieurs tâches. Azure AD Privileged Identity Management permet principalement de gérer les accès pour les rôles AD et les groupes de rôles, tandis que la gestion des accès privilégiés Microsoft Purview s’applique uniquement au niveau de la tâche.

- **Activation de la gestion des accès privilégiés tout en utilisant déjà Azure AD Privileged Identity Management :** L’ajout de la gestion des accès privilégiés fournit une autre couche granulaire de fonctionnalités de protection et d’audit pour l’accès privilégié aux données Microsoft 365.

- **Activation d’Azure AD Privileged Identity Management tout en utilisant déjà Microsoft Purview Privileged Access Management :** l’ajout d’Azure AD Privileged Identity Management à Microsoft Purview Privileged Access Management peut étendre l’accès privilégié aux données en dehors de Microsoft 365 qui sont principalement définies par les rôles d’utilisateur ou l’identité .  

## <a name="privileged-access-management-architecture-and-process-flow"></a>Architecture et flux de processus de gestion des accès privilégiés

Chacun des flux de processus suivants décrit l’architecture de l’accès privilégié et la façon dont il interagit avec le substrat Microsoft 365, l’audit et l’espace d’exécution de gestion Exchange.

### <a name="step-1-configure-a-privileged-access-policy"></a>Étape 1 : Configurer une stratégie d’accès privilégié

Lorsque vous configurez une stratégie d’accès privilégié avec le [Centre d'administration Microsoft 365](https://admin.microsoft.com) ou la commande PowerShell de gestion Exchange, vous définissez la stratégie et les processus de fonctionnalité d’accès privilégié, ainsi que les attributs de stratégie dans le substrat Microsoft 365. Les activités sont enregistrées dans le journal d’audit. La stratégie est désormais activée et prête à gérer les demandes entrantes pour approbation.

![Étape 1 : création de stratégie.](../media/pam-step1-policy-creation.jpg)

### <a name="step-2-access-request"></a>Étape 2 : Demande d’accès

Dans le [Centre d'administration Microsoft 365](https://admin.microsoft.com) ou avec la commande PowerShell de gestion Exchange, les utilisateurs peuvent demander l’accès aux tâches avec élévation de privilèges ou avec élévation de privilèges. La fonctionnalité d’accès privilégié envoie la demande au substrat Microsoft 365 pour traitement par rapport à la stratégie d’accès aux privilèges configurée et enregistre l’activité dans les journaux d’audit.

![Étape 2 : Demande d’accès.](../media/pam-step2-access-request.jpg)

### <a name="step-3-access-approval"></a>Étape 3 : Approbation d’accès

Une demande d’approbation est établie et la notification de demande en attente est envoyée par e-mail aux approbateurs. En cas d’acceptation, la demande d’accès privilégié est traitée comme une approbation et la tâche est prête pour son exécution. En cas de refus, la tâche est bloquée et aucun accès n’est accordé au demandeur. Le demandeur est informé de l’approbation ou du refus par message électronique.

![Étape 3 : Approbation de l’accès.](../media/pam-step3-access-approval.jpg)

### <a name="step-4-access-processing"></a>Étape 4 : Traitement de l’accès

Pour une demande approuvée, la tâche est traitée par l’instance d’exécution d’Exchange Management. L’approbation est vérifiée par rapport à la stratégie d’accès privilégié et traitée par le substrat Microsoft 365. Toutes les activités de la tâche sont consignées dans les journaux d’audit.

![Étape 4 : Traitement de l’accès.](../media/pam-step4-access-processing.jpg)

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

### <a name="what-skus-can-use-privileged-access-in-office-365"></a>Quelles références SKU peuvent utiliser l’accès privilégié dans Office 365 ?

La gestion des accès privilégiés est disponible pour les clients d’un large choix d’abonnements et de modules complémentaires Microsoft 365 et Office 365. Pour plus d’informations, consultez [Prise en main de la gestion des accès privilégiés](privileged-access-management-configuration.md) .

### <a name="when-will-privileged-access-support-office-365-workloads-beyond-exchange"></a>Quand l’accès privilégié prendra-t-il en charge les charges de travail Office 365 au-delà d’Exchange ?

La gestion des accès privilégiés sera bientôt disponible dans d’autres charges de travail Office 365. Pour plus d’informations, consultez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) .

### <a name="my-organization-needs-more-than-30-privileged-access-policies-will-this-limit-be-increased"></a>Mon organisation a besoin de plus de 30 stratégies d’accès privilégié. Cette limite sera-t-elle augmentée ?

Oui, l’augmentation de la limite actuelle de 30 stratégies d’accès privilégié par organisation est sur la feuille de route des fonctionnalités.

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Dois-je être un Administration global pour gérer l’accès privilégié dans Office 365 ?

Non, vous avez besoin du rôle Gestion des rôles Exchange attribué aux comptes qui gèrent l’accès privilégié dans Office 365. Si vous ne souhaitez pas configurer le rôle Gestion des rôles en tant qu’autorisation de compte autonome, le rôle Administrateur général inclut ce rôle par défaut et peut gérer l’accès privilégié. Les utilisateurs inclus dans un groupe d’approbateurs n’ont pas besoin d’être un Administration global ou d’avoir le rôle Gestion des rôles attribué pour examiner et approuver les demandes avec PowerShell.

### <a name="how-is-privileged-access-management-related-to-customer-lockbox"></a>Comment la gestion des accès privilégiés est-elle liée à Customer Lockbox ?

[Customer Lockbox](/office365/admin/manage/customer-lockbox-requests) autorise un niveau de contrôle d’accès pour les organisations lorsque Microsoft accède aux données. La gestion des accès privilégiés permet un contrôle d’accès granulaire au sein d’une organisation pour toutes les tâches privilégiées Microsoft 365.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Commencez [à configurer votre organisation pour la gestion des accès privilégiés](privileged-access-management-configuration.md).

## <a name="learn-more"></a>En savoir plus

[Guide interactif : Surveiller et contrôler les tâches de l’administrateur avec la gestion des accès privilégiés](https://content.cloudguides.com/guides/Privileged%20Access%20Management)
