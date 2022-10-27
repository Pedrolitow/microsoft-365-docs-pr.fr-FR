---
title: Gestion des risques internes
description: Découvrez comment configurer la gestion des risques internes. La gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risque.
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- tier1
- purview-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- m365solution-scenario
- highpri
ms.openlocfilehash: c3d4e6662806cbf2a821e0ef4228e5efa87a012e
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68733590"
---
# <a name="insider-risk-management"></a>Gestion des risques internes

> [!IMPORTANT]
> Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Les employés ont désormais plus d’accès pour créer, gérer et partager des données sur un large éventail de plateformes et de services. Dans la plupart des cas, les organisations disposent de ressources et d’outils limités pour identifier et atténuer les risques à l’échelle de l’organisation tout en répondant aux exigences de conformité et aux normes de confidentialité des employés. Ces risques incluent le vol potentiel de données par des employés sortants et le risque de fuites de données d’informations en dehors de votre organisation par surpartage accidentel ou intention malveillante.

Gestion des risques internes Microsoft Purview utilise toute l’étendue des indicateurs de service et tiers pour vous aider à identifier, trier et agir rapidement sur les activités potentiellement risquées. En utilisant les journaux de Microsoft 365 et de Microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risque. Après avoir identifié les risques, vous pouvez prendre des mesures pour atténuer ces risques et, si nécessaire, ouvrir des dossiers d’enquête et prendre les mesures juridiques appropriées.

Regardez les vidéos ci-dessous pour découvrir comment la gestion des risques internes peut aider votre organisation à prévenir, détecter et contenir les risques :


**Solution de gestion des risques internes & développement** :
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4j9CN]
<br>

**Workflow de gestion des risques internes** :
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="configure-insider-risk-management"></a>Configurer la gestion des risques internes

Procédez comme suit pour configurer la gestion des risques internes pour votre organisation :

![Étapes de gestion des risques internes de la solution de risque interne](../media/ir-solution-ir-steps.png)

1. En savoir plus sur [la gestion des risques internes](insider-risk-management.md)
2. Planifier [la gestion des risques internes et vérifier les licences](insider-risk-management-plan.md)
3. Configurer les [paramètres de gestion des risques internes](insider-risk-management-settings.md)
4. Configurer [les autorisations](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management) et [les prérequis de stratégie & connecteurs](insider-risk-management-configure.md#step-4-recommended-configure-prerequisites-for-policies)
5. Créer et configurer [des stratégies de gestion des risques internes](insider-risk-management-configure.md#step-6-required-create-an-insider-risk-management-policy)

## <a name="more-information-about-insider-risk-management"></a>Plus d’informations sur la gestion des risques internes

- [Gérer les stratégies de risque interne](insider-risk-management-policies.md)
- [Identifier les activités de risques internes](insider-risk-management-activities.md)
- [Agir sur les cas de risque interne](insider-risk-management-cases.md)
