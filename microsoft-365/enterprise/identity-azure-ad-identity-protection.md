---
title: 'Étape 6 : Se protéger contre la compromission de confidentialité'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/01/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez Azure AD Identity Protection.
ms.openlocfilehash: b1dea9d2917c45bf87bd972f56c9eac2b074c252
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867483"
---
# <a name="step-6-protect-against-credential-compromise"></a>Étape 6 : Se protéger contre la compromission de confidentialité

*Cette étape est facultative et s’applique uniquement à la version E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Dans cette étape, vous allez découvrir comment configurer des stratégies destinées à protéger contre la compromission de confidentialité, lorsqu’un utilisateur malveillant détermine le nom et le mot de passe d’un compte d’utilisateur pour accéder aux services cloud et aux données d’une organisation. Azure AD Identity Protection fournit plusieurs méthodes permettant d’empêcher un utilisateur malveillant de consulter vos comptes et groupes et par la suite, vos données les plus précieuses.

Azure AD Identity Protection vous permet de :

|||
|:---------|:---------|
|déterminer et résoudre les vulnérabilités potentielles dans les identités de votre organisation ;|Azure AD utilise l’apprentissage automatique pour détecter les anomalies et les activités douteuses, telles que les connexions et les activités post-connexion. À l’aide de ces données, Identity Protection génère des rapports et les alertes qui vous aident à évaluer les problèmes et à prendre des mesures.|
|Détecter des actions douteuses qui sont liées aux identités de votre organisation et y répondre automatiquement|Vous pouvez configurer des stratégies de risque qui répondent automatiquement aux problèmes détectés lorsqu’un niveau de risque spécifié a été atteint. Ces stratégies, en plus des autres contrôles d’accès conditionnel fournis par Azure Active Directory et Enterprise Mobility + Security (EMS) peuvent automatiquement bloquer l’accès ou prendre des actions correctives, comme réinitialiser les mots de passe et demander l’authentification multifacteur pour les connexions suivantes.|
|Examiner les incidents suspects et les résoudre avec des actions d’administration|Vous pouvez examiner des événements à risque en utilisant les informations sur l’incident de sécurité. Des flux de travail de base sont disponibles pour effectuer le suivi des enquêtes et lancer des actions de correction, telles que des réinitialisations du mot de passe.|

[Plus d’informations sur Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection).

Reportez-vous à la rubrique des [étapes pour activer Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection-enable).

Les résultats de cette étape sont que vous avez activé Azure AD Identity Protection et que vous l’utilisez pour :

- résoudre les vulnérabilités d’identités potentielles ;
- détecter les tentatives de compromission d’informations d’identification possibles ;
- examiner et résoudre des incidents d’identités suspects en cours.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test : Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md) |
|||

Comme point de vérification temporaire, vous pouvez voir les [critères de sortie](identity-exit-criteria.md#crit-identity-ident-prot) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step7.png)| [Synchroniser des annuaires](identity-azure-ad-connect.md) |


