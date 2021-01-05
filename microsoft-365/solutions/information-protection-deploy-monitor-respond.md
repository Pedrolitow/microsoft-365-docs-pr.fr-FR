---
title: Surveillance et réponse aux incidents de confidentialité des données au sein de votre organisation
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 01/04/2021
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Utilisez les stratégies d’audit et d’alerte et les demandes des personnes concernées pour surveiller et répondre aux incidents de données personnelles.
ms.openlocfilehash: 3ae0f2a6528f6188500c7cee7732c6447013eaa6
ms.sourcegitcommit: ae646779d84e993cf80b1207e76b856a21be5790
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "49749586"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>Surveillance et réponse aux incidents de confidentialité des données au sein de votre organisation

Les fonctionnalités de Microsoft 365 sont disponibles pour vous aider à surveiller, examiner et répondre aux incidents de confidentialité des données au sein de votre organisation lorsque vous avez opérationnel les fonctionnalités connexes. L’existence de processus, de procédures et d’autres documents pour chacun de ces éléments peut également être importante pour démontrer la conformité aux organismes de réglementation.

Cela inclut ce qui suit : 

- Stratégies d’audit et d’alerte
- Demandes des personnes concernées (y compris la recherche de contenu et eDiscovery)
- Outils et rapports d’enquête supplémentaires

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>Réglementations en matière de confidentialité des données ayant un impact sur l’utilisation des outils de surveillance et de réponse

Voici un exemple de liste de réglementations sur la confidentialité des données pouvant être liées aux contrôles de la gouvernance des informations :

- Article 46 de la LGPD
- Article 48 de la LGPD
- Article RGPD (5) (1) (f)
- Article RGPD (15) (1) (e)
- HIPAA-HI (45 C.F.R. 164.308 (a) (1) (II) (D))
- HIPAA-HI (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HI (45 C.F.R. 164.312 (b))
- CCPA (1798.105 (c))

Pour plus d’informations, consultez la rubrique [évaluation des risques de confidentialité des données et identification des informations sensibles](information-protection-deploy-assess.md).

Les réglementations en matière de confidentialité des données appellent généralement ce qui suit pour la surveillance et la réponse :

- Audit, alerte et création de rapports pour les activités liées au stockage, au partage et au traitement des données personnelles
- La possibilité de répondre à une demande d’objet de données (DSR) et, dans certains cas, d’effectuer des actions d’enquête et d’autres mesures administratives pour se conformer à ces demandes.

Votre organisation peut également souhaiter effectuer des activités de surveillance et de réponse à d’autres fins, telles que d’autres besoins en matière de conformité ou pour des raisons professionnelles. L’établissement de votre schéma de surveillance et de réponse pour la confidentialité des données doit être réalisé dans le cadre de la planification globale de la surveillance et de la réponse, de l’implémentation et de la gestion.

Pour vous aider à prendre en main un schéma de surveillance et de réponse dans Microsoft 365 pour des réglementations sur la confidentialité des données, cet article répertorie les fonctionnalités utiles dans Microsoft 365 afin de répondre à des questions telles que : 

- Quels sont les types de données de surveillance quotidienne, d’enquête et de création de rapports disponibles pour les différents types de données et sources ?
- Les mécanismes qui seront nécessaires pour gérer les demandes des personnes concernées par les données (DSR) et les actions correctives, telles que l’anonymisation, la biffure et la suppression.

## <a name="auditing-and-alert-policies-in-the-security-and-compliance-center"></a>Stratégies d’audit et d’alerte dans le centre de sécurité et conformité

Consultez les articles suivants pour configurer les stratégies d’audit, d’audit avancé et d’alerte :

- [Audit unifié](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Audit de boîte aux lettres](../compliance/enable-mailbox-auditing.md)
- [Audit avancé](../compliance/advanced-audit.md)
- [Stratégies d’alerte](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>Demandes des personnes concernées pour le RGPD et CCPA

Consultez [demandes des personnes concernées pour RGPD et CCPA](../compliance/gdpr-dsr-office365.md) pour obtenir des informations sur la réponse à un DSR dans Microsoft 365.

## <a name="manage-deleted-users-in-microsoft-stream"></a>Gérer les utilisateurs supprimés dans Microsoft Stream

Pour Microsoft Stream, lorsqu’un utilisateur est supprimé d’Azure Active Directory (Azure AD), si son nom était associé à un flux vidéo publié avant ce point, son adresse de messagerie reste associée à la vidéo. Consultez la rubrique [Manage Deleted users from Microsoft Stream](https://docs.microsoft.com/stream/managing-deleted-users) pour le supprimer.

## <a name="insider-risk-management-as-an-investigative-tool"></a>Gestion des risques initiés en tant qu’outil d’enquête

La [gestion des risques initiés dans microsoft 365](../compliance/insider-risk-management.md) est une fonctionnalité du centre d’administration de la conformité Microsoft pour vous aider à réduire les risques internes en vous permettant de détecter, d’examiner et de prendre des mesures concernant les activités à risque au sein de votre organisation.
