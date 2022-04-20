---
title: Surveiller et répondre aux incidents de confidentialité des données dans votre organisation
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 01/04/2021
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Utilisez les stratégies d’audit et d’alerte et les demandes de personnes concernées pour surveiller et répondre aux incidents de données personnelles.
ms.openlocfilehash: 730eb42fdf6aed66f5beac69621981848ffa6510
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953324"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>Surveiller et répondre aux incidents de confidentialité des données dans votre organisation

Microsoft 365 fonctionnalités sont disponibles pour vous aider à surveiller, examiner et répondre aux incidents de confidentialité des données au sein de votre organisation lorsque vous mettez en œuvre les fonctionnalités associées. Il peut également être important de disposer de processus, de procédures et d’autres documents pour chacun d’eux pour démontrer la conformité aux organismes de réglementation.

Cela inclut ce qui suit : 

- Stratégies d’audit et d’alerte
- Demandes d’objet de données (y compris la recherche de contenu et eDiscovery)
- Outils d’enquête et rapports supplémentaires

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>Réglementation sur la confidentialité des données impactant l’utilisation des outils de surveillance et de réponse

Voici un exemple de liste des réglementations relatives à la confidentialité des données qui peuvent être liées aux contrôles de gouvernance des informations :

- LGPD Article 46
- Article 48 du LGPD
- Article RGPD (5)(1)(f)
- Article RGPD (15)(1)(e)
- HIPAA-HITECH (45 C.F.R. 164.308(a)(1)(ii)(D))
- HIPAA-HITECH (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HITECH (45 C.F.R. 164.312(b))
- CCPA (1798.105(c))

Pour plus d’informations, consultez [Évaluer les risques liés à la confidentialité des données et identifier les informations sensibles](information-protection-deploy-assess.md).

Les réglementations sur la confidentialité des données demandent généralement les éléments suivants pour la surveillance et la réponse :

- Audit, génération d’alertes et création de rapports pour les activités liées au stockage, au partage et au traitement des données personnelles
- La possibilité de répondre à une demande de sujet de données (DSR) et, dans certains cas, d’effectuer des enquêtes et d’autres mesures administratives pour se conformer à ces demandes.

Votre organisation peut également souhaiter effectuer des activités de surveillance et de réponse à d’autres fins, telles que d’autres besoins de conformité ou pour des raisons commerciales. L’établissement de votre système de surveillance et de réponse pour la confidentialité des données doit être effectué dans le cadre de la planification globale de la surveillance et de la réponse, de l’implémentation et de la gestion.

Pour vous aider à prendre en main un schéma de surveillance et de réponse dans Microsoft 365 pour les réglementations sur la confidentialité des données, cet article répertorie des fonctionnalités utiles dans Microsoft 365 pour répondre à des questions telles que : 

- Quel type de techniques quotidiennes de surveillance, d’investigation et de création de rapports sont disponibles pour les différents types et sources de données ?
- Quels mécanismes seront nécessaires pour gérer les demandes de personnes concernées (DSR) et toutes les actions correctives, telles que l’anonymisation, la réaction et la suppression.

## <a name="auditing-and-alert-policies-in-the-security-and-compliance-center"></a>Audit et stratégies d’alerte dans le Centre de sécurité et de conformité

Consultez ces articles pour configurer l’audit, l’audit avancé et les stratégies d’alerte :

- [Audit unifié](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Audit de boîte aux lettres](../compliance/enable-mailbox-auditing.md)
- [Audit (Premium)](../compliance/advanced-audit.md)
- [Stratégies d’alerte](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>Demandes de personnes concernées pour le RGPD et le CCPA

Pour plus d’informations sur la réponse à une DSR dans Microsoft 365, consultez [demandes de personnes concernées pour le RGPD et le CCPA](/compliance/regulatory/gdpr-dsr-Office365).

## <a name="manage-deleted-users-in-microsoft-stream"></a>Gérer les utilisateurs supprimés dans Microsoft Stream

Par Microsoft Stream, lorsqu’un utilisateur est supprimé de Azure Active Directory (Azure AD), si son nom a été associé à une vidéo Stream publiée avant ce point, son adresse e-mail reste associée à la vidéo. Pour le supprimer, consultez [Gérer les utilisateurs supprimés de Microsoft Stream](/stream/managing-deleted-users).

## <a name="insider-risk-management-as-an-investigative-tool"></a>Gestion des risques internes en tant qu’outil d’investigation

[La gestion des risques internes](../compliance/insider-risk-management.md) est une fonctionnalité du portail de conformité Microsoft Purview qui vous permet de réduire les risques internes en vous permettant de détecter, d’examiner et d’agir sur les activités à risque au sein de votre organisation.