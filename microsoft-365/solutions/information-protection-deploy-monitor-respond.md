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
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Utilisez des stratégies d’audit et d’alerte, ainsi que des demandes des personnes qui répondent aux incidents de données personnelles.
ms.openlocfilehash: 4070cd772d243bcfba33bfb164fd05e1f0911b3b
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59203688"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>Surveiller et répondre aux incidents de confidentialité des données dans votre organisation

Microsoft 365 fonctionnalités sont disponibles pour vous aider à surveiller, examiner et répondre aux incidents de confidentialité des données dans votre organisation au cours de l’opérationnalisation des fonctionnalités associées. Il peut également être important d’avoir des processus, des procédures et d’autres documents pour chacun d’eux pour démontrer la conformité aux organismes de réglementation.

Cela comprend : 

- Stratégies d’audit et d’alerte
- Demandes des personnes objet de données (y compris la recherche de contenu et eDiscovery)
- Outils d’investigation et rapports supplémentaires

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>Réglementations en matière de confidentialité des données qui ont un impact sur l’utilisation des outils de surveillance et de réponse

Voici un exemple de liste des réglementations de confidentialité des données qui peuvent être liées aux contrôles de gouvernance des informations :

- LGPD Article 46
- LGPD Article 48
- Article R GDPR (5)(1)(f)
- Article R GDPR (15)(1)(e)
- HIPAA-HITECH (45 C.F.R. 164.308(a)(1)(ii)(D))
- HIPAA-HITECH (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HITECH (45 C.F.R. 164.312(b))
- CCPA (1798.105(c))

Pour plus d’informations, voir [Évaluer les risques de confidentialité des données et identifier les informations sensibles.](information-protection-deploy-assess.md)

Les réglementations en matière de confidentialité des données demandent généralement les informations suivantes pour la surveillance et la réponse :

- Audit, alerte et rapport pour les activités liées au stockage, au partage et au traitement des données personnelles
- La possibilité de répondre à une demande d’objet de données (DSR) et, dans certains cas, d’effectuer des enquêtes et d’autres mesures administratives pour se conformer à ces demandes.

Votre organisation peut également effectuer des activités de surveillance et de réponse à d’autres fins, telles que d’autres besoins de conformité ou pour des raisons professionnelles. L’établissement de votre schéma de surveillance et de réponse pour la confidentialité des données doit être effectué dans le cadre de la planification globale de la surveillance et de la réponse, de l’implémentation et de la gestion.

Pour vous aider à démarrer avec un schéma de surveillance et de réponse dans Microsoft 365 pour les réglementations en matière de confidentialité des données, cet article répertorie les fonctionnalités utiles dans Microsoft 365 pour répondre à des questions telles que : 

- Quels types de techniques de surveillance, d’investigation et de rapports au quotidien sont disponibles pour les différents types de données et sources ?
- Les mécanismes qui seront nécessaires pour gérer les demandes des personnes qui traitent des données (DSR) et les mesures correctives, telles que l’anonymisation, la suppression et la suppression.

## <a name="auditing-and-alert-policies-in-the-security-and-compliance-center"></a>Stratégies d’audit et d’alerte dans le Centre de sécurité et conformité

Consultez les articles suivants pour la configuration de l’audit, de l’audit avancé et des stratégies d’alerte :

- [Audit unifié](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Audit de boîte aux lettres](../compliance/enable-mailbox-auditing.md)
- [Audit avancé](../compliance/advanced-audit.md)
- [Stratégies d’alerte](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>Demandes des personnes responsables des données concernant le R GDPR et le CCPA

Pour [plus d’informations](/compliance/regulatory/gdpr-dsr-Office365) sur la réponse à une DPC dans le Microsoft 365, voir Demandes des personnes objet de données concernant le R GDPR et le CCPA.

## <a name="manage-deleted-users-in-microsoft-stream"></a>Gérer les utilisateurs supprimés dans Microsoft Stream

Pour Microsoft Stream, lorsqu’un utilisateur est supprimé de Azure Active Directory (Azure AD), si son nom était associé à une vidéo Stream publiée avant ce point, son adresse de messagerie reste associée à la vidéo. Pour [le supprimer, voir](/stream/managing-deleted-users) Gérer les utilisateurs supprimés de Microsoft Stream.

## <a name="insider-risk-management-as-an-investigative-tool"></a>Gestion des risques internes en tant qu’outil d’investigation

La gestion des risques internes dans [Microsoft 365](../compliance/insider-risk-management.md) est une fonctionnalité du Centre d’administration de la conformité Microsoft qui vous permet de minimiser les risques internes en vous permettant de détecter, d’examiner et d’agir sur les activités à risque dans votre organisation.