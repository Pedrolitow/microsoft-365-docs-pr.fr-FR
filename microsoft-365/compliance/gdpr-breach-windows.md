---
title: Service de traitement de données pour la notification Windows sous RGPD
description: Service de traitement de données pour la protection de Windows vis-à-vis des violations de données personnelles, et réponse et notification de Microsoft en cas de violation.
keywords: Service de traitement des données pour Windows, Microsoft 365, documentation Microsoft 365, RGPD
localization_priority: Priority
ROBOTS: NOINDEX, NOFOLLOW
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: daniha
author: DaniHalfin
manager: dansimp
audience: itpro
ms.collection:
- GDPR
- M365-security-compliance
ms.openlocfilehash: bfadeae0f4f0b01197f58f0610d1040da3080922
ms.sourcegitcommit: 3ddcf08e8deec087df1fe524147313f1cb12a26d
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "45023606"
---
# <a name="data-processor-service-for-windows-breach-notification-under-the-gdpr"></a>Service de traitement de données pour la notification de violation Windows sous RGPD

>[!NOTE]
>Cette rubrique est destinée aux participants au programme de prévisualisation du service de traitement des données pour Windows et nécessite l'acceptation de conditions d'utilisation spécifiques. Pour en savoir plus sur le programme et accepter les conditions d’utilisation, voir [https://aka.ms/dpswpublicpreview](https://aka.ms/dpswpublicpreview).

Le service de traitement des données de Microsoft pour Windows prend au sérieux ses obligations au titre du règlement général sur la protection des données (RGDP). Le service de traitement des données de Microsoft pour Windows prend des mesures de sécurité étendues pour se protéger contre les violations de données. Il s’agit notamment d’équipes spécialisées dans la gestion des menaces, qui anticipent, bloquent et atténuent les accès malveillants de manière proactive.  Les mesures de sécurité interne telles que l’analyse des ports, l’analyse des vulnérabilités du périmètre et la détection des intrusions détectent et bloquent l’accès malveillant, ainsi que les processus de sécurité automatisés, les stratégies de sécurité et de confidentialité des informations, ainsi que la sécurité et la confidentialité pour tous les membres du personnel. 

La sécurité est intégrée dans le service de traitement des données de Microsoft pour Windows depuis le début, en commençant par le [Cycle de développement de la sécurité](https://www.microsoft.com/sdl/), un processus de développement obligatoire qui incorpore des méthodologies de confidentialité par conception et de confidentialité par défaut. Le principe de base de la stratégie de sécurité de Microsoft consiste à « assumer une violation », qui est une extension de la stratégie de défense en profondeur. En remettant constamment en question les fonctionnalités de sécurité du service de traitement des données pour Windows, Microsoft peut garder une longueur d'avance sur les nouvelles menaces. Pour plus d’informations sur le service de traitement de données pour la sécurité Windows, consultez ces [ressources](https://www.microsoft.com/TrustCenter/Security/windows10-security) le service de traitement de données pour Windows répond à une violation potentielle de données en fonction du processus de réponse aux incidents de sécurité. Le service de traitement des données pour la réponse aux incidents de sécurité de Windows est implémenté à l'aide d'un processus en cinq étapes : détecter, évaluer, diagnostiquer, stabiliser et fermer. L’équipe de réponse aux incidents de sécurité peut alterner entre les étapes de diagnostique et de stabilisation au fur et à mesure de la progression de l’examen. Voici une vue d’ensemble du processus de réponse aux incidents de sécurité : 

|**Stade**|**Description**|
| ------- | ------------- |
| ***1 — Détecter*** | Première indication d’un incident potentiel. |
| ***2 — Évaluer*** | An on-call incident response team member assesses the impact and severity of the event. Based on evidence, the assessment may or may not result in further escalation to the security response team. |
| ***3 — Diagnostiquer*** | Des spécialistes de la réponse aux incidents de sécurité effectuent des examens techniques et mènent une enquête judiciaire, identifient des stratégies de limitation, d’atténuation et de contournement. Si l’équipe de sécurité pense que les données client ont peut-être été exposées à un individu non autorisé ou ayant commis des actes illicites, l’exécution du processus de notification des incidents du client débute en parallèle. |
| ***4 — Stabiliser et récupérer*** | The incident response team creates a recovery plan to mitigate the issue. Crisis containment steps such as quarantining impacted systems may occur immediately and in parallel with diagnosis. Longer term mitigations may be planned which occur after the immediate risk has passed. |
| ***5 — Fermeture et post-mortem*** | L’équipe de réponse aux incidents de sécurité crée un post-mortem qui décrit les détails de l’incident, avec l’intention de réviser les stratégies, procédures et processus afin d’éviter une récurrence de l’événement. |

Les processus de détection utilisés par le service de traitement de données Microsoft pour Windows sont conçus pour découvrir les événements susceptibles de menacer la confidentialité, l’intégrité et la disponibilité du service de traitement de données pour Windows. Plusieurs événements peuvent déclencher un examen : 

 - Alertes système automatisées via des infrastructures de surveillance interne et d’alertes. Ces alertes peuvent survenir en tant qu’alarmes basées sur la signature (par exemple, les programmes malveillants, la détection de l’intrusion) ou via des algorithmes conçus pour profiler l’activité prévue et signaler des anomalies.
 - Les rapports de première partie des services Microsoft exécutés sur Microsoft Azure et Azure Government.
 - Les vulnérabilités de sécurité sont signalées à [MSRC (Microsoft Security Response Center)](https://technet.microsoft.com/security/dn440717) via [secure@microsoft.com] (mailto:secure@microsoft.com). MSRC fonctionne avec des partenaires et des chercheurs en sécurité dans le monde entier afin d’éviter les incidents de sécurité et améliorer la sécurité des produits Microsoft.
 - Les rapports client via le portail de support client ou Microsoft Azure et le portail Azure Government Management, qui décrivent une activité suspecte attribuée à l’infrastructure Azure (par opposition à l’activité ayant lieu dans le domaine de la responsabilité du client).
 - Sécurité activité [d’Équipe Rouge et Équipe Bleue](https://azure.microsoft.com/blog/red-teaming-using-cutting-edge-threat-simulation-to-harden-the-microsoft-enterprise-cloud/). Cette stratégie utilise une équipe rouge hautement qualifiée d’experts en matière de sécurité Microsoft pour découvrir et attaquer les faiblesses potentielles dans Azure. L’équipe de sécurité couleur bleue doit détecter et se défendre contre l’activité de l’équipe rouge. Les actions des équipes rouge et bleue sont utilisées pour vérifier que le travail de réponse de sécurité Azure gère efficacement les incidents de sécurité. Les activités de la sécurité des équipes rouge et bleue sont régies par les règles d'engagement, afin de garantir la protection des données client.
 - Escalades des opérateurs des services Azure. Les employés de Microsoft sont formés pour identifier et transmettre les éventuels problèmes de sécurité.

 ## <a name="data-processor-service-for-windows-data-breach-response"></a>Service de traitement de données pour la réponse aux violations de données Windows 

 Microsoft affecte l’enquête à des niveaux de priorité et de gravité appropriés en déterminant l’impact fonctionnel, la récupérabilité et l’impact sur les informations de l’incident. La priorité et la gravité peuvent changer au cours des enquêtes, sur la base de nouveaux résultats et conclusions. Les événements de sécurité impliquant des risques imminents ou confirmés pour les données client sont traités comme présentant un niveau de gravité élevé et 24 heures sur 24 pour résoudre le problème. Le service de traitement des données de Microsoft pour Windows classe l'impact des informations de l'incident dans les catégories de violation suivantes : 

| **Catégorie**             | **Définition**                                                                                                                   |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| ***Aucune***               | Aucune information n’a été dévoilée, modifiée, supprimée ou compromise d’une façon ou d’une autre. |
| ***Violation de la confidentialité***     | Des données personnelles sensibles des contribuables, employés, bénéficiaires, etc. ont été consultées ou dévoilées. |
| ***Violation d’informations confidentielles*** | Des informations confidentielles non classifiées, telles que des informations sur les infrastructures critiques protégées (PCII), ont été consultées ou dévoilées. |
| ***Perte d’intégrité***     | Des informations sensibles ou confidentielles ont été modifiées ou supprimées. |

L’équipe de réponse de sécurité collabore avec le service de traitement des données de Microsoft pour les ingénieurs de sécurité Windows et les PME pour classer l’événement en fonction des données factuelles des éléments de preuve. Un événement de sécurité peut être classifié comme suit : 

 - **Faux positif** : un événement qui répond aux critères de détection, mais qui est considéré comme faisant partie d’une pratique commerciale normale et peut nécessiter un filtrage. L’équipe de service identifie la cause première des faux positifs et les traite d’une manière systématique en exploitant des sources de détection et en les ajustant au besoin. 
 - **Incident de sécurité** : un incident provoqué par un accès non autorisé à des données client ou à des données du support stockées sur un équipement de Microsoft ou dans des installations de Microsoft, ou tout accès non autorisé à ces équipement ou installations provoquant la perte, divulgation ou altération des données client ou des données de support. 
 - **Incident de sécurité déclarable au client** : un accès illégal ou non autorisé ou une utilisation illégale ou non autorisée de systèmes, équipements ou installations Microsoft provoquant la divulgation, modification ou perte de données client. 
 - **Violation de la confidentialité** : sous-type d’incident de sécurité impliquant des données personnelles. Les procédures de gestion sont les mêmes que celles concernant un incident de sécurité. 

 For a CRSI to be declared, Microsoft must determine that unauthorized access to customer data has or has very likely occurred and/or that there is a legal or contractual commitment that notification must occur. It is desired, but not required, that specific customer impact, resource access, and repair steps be known. An incident is generally declared a CRSI after the conclusion of the Diagnose stage of a security incident; however, the declaration may happen at any point that all pertinent information is available. The security incident manager must establish evidence beyond reasonable doubt that a reportable event has occurred to begin execution of the Customer Incident Notification Process. 

Throughout the investigation, the security response team works closely with global legal advisors to help ensure that forensics are performed in accordance with legal obligations and commitments to customers. There are also significant restrictions on system and customer data viewing and handling in various operating environments. Sensitive or confidential data, as well as Customer Data, are not transferred out of the production environment without explicit written approval from the Incident Manager recorded in the corresponding incident ticket. 

Microsoft verifies that customer and business risk is successfully contained, and that corrective measures are implemented. If necessary, emergency mitigation steps to resolve immediate security risks associated with the event are taken. 

Microsoft effectue aussi un post-mortem interne pour les violations de données. Dans le cadre de cet exercice, le niveau suffisant de réponse et les procédures d’exploitation sont évalués, et les mises à jour pouvant être nécessaires pour les stratégies de l’équipe de réponse de sécurité ou des processus connexes sont identifiées et mises en œuvre. Les post-mortems internes pour les violations de données sont des enregistrements hautement confidentiels qui ne sont pas accessibles aux clients. Les post-mortems peuvent toutefois être synthétisés et inclus dans d’autres notifications d’événement au client. Ces rapports sont fournis à des auditeurs externes pour révision dans le cadre du cycle d’audit de routine du service de traitement de données pour Windows. 

## <a name="customer-notice"></a>Avis client

Le service de traitement des données de Microsoft pour Windows informe les clients et les autorités de régulation des violations de données, le cas échéant. Microsoft s'appuie sur une forte compartimentation interne dans le fonctionnement du service de traitement des données pour Windows. Les journaux de flux de données sont également fiables. L'avantage de cette conception est que la plupart des incidents peuvent être liés à des clients spécifiques. L’objectif est de donner aux clients concernés un avis précis, exploitable et opportun, lorsque leurs données ont été violées. 

Suite à un CRSI déclaré, le processus de notification intervient dans les meilleurs délais, sachant que les risques de sécurité évoluent rapidement. En règle générale, le processus d’élaboration des notifications a lieu alors que l’analyse de l’incident est en cours. Les notifications du client sont livrées dans un délai maximal de 72 heures à partir du moment où nous avons déclaré une violation, sauf dans les cas suivants : 

 - Microsoft believes the act of performing a notification will increase the risk to other customers. For example, the act of notifying may tip off an adversary causing an inability to remediate. 
 - D’autres circonstances inhabituelles ou extrêmes examinées par le service juridique Corporate External and Legal Affairs (CELA) de Microsoft et le gestionnaire exécutif des incidents. 

 Le service de traitement des données de Microsoft pour Windows fournit aux clients des informations détaillées leur permettant d’effectuer des enquêtes internes et de répondre aux engagements des utilisateurs finaux, sans retarder le processus de notification de façon excessive. 

La notification d’une divulgation de données personnelles sera envoyée au client par tout moyen que Microsoft sélectionne, y compris par courrier électronique. La notification d’une divulgation de données sera envoyée à la liste des contacts de sécurité fournis dans Azure Security Center, qui peut être configurée en suivant les [instructions d’implémentation](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details). Si les informations de contact ne sont pas fournies dans Azure Security Center (centre de sécurité Azure), la notification est envoyée à un ou plusieurs administrateurs dans un abonnement Azure. Pour vous assurer que les notifications peuvent être remises correctement, il incombe au client de s’assurer que les informations de contact des administrateurs sur les portails de services en ligne et les abonnements concernés sont correctes.

Le service de traitement des données de Microsoft pour l’équipe Windows peut également choisir d’informer d’autres membres du personnel Microsoft (par exemple, le service client et le gestionnaire de compte du client ou le gestionnaire de compte technique). Ces personnes ont souvent des relations étroites avec le client et peuvent favoriser une correction plus rapide 

Pour plus d’informations sur la façon dont Microsoft détecte et répond à une violation des données personnelles, reportez-vous à l’article [Notification des violations de données en vertu du RGPD](https://servicetrust.microsoft.com/ViewPage/GDPRBreach) dans le portail d’approbation de services.