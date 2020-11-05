---
title: Notification de violation Azure et Dynamics 365 dans le cadre du RGPD
description: Protection d’Azure et Dynamics 365 vis-à-vis des violations de données personnelles, et réponse et notification de Microsoft en cas de violation.
keywords: Azure, Microsoft 365, Dynamics 365, documentation Microsoft 365, RGPD
localization_priority: Priority
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- GDPR
- M365-security-compliance
titleSuffix: Microsoft GDPR
ms.openlocfilehash: 0cdd3a2d8e158800cef534a1488df0f25e3d232f
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48920258"
---
# <a name="azure-and-dynamics-365-breach-notification-under-the-gdpr"></a>Notification de violation Azure et Dynamics 365 dans le cadre du RGPD

Microsoft Azure prend au sérieux ses obligations dans le cadre du Règlement Général sur la Protection des Données Personnelles (RGPD). Microsoft Azure prend des mesures de sécurité étendues pour protéger contre les violations des données. Celles-ci incluent des contrôles de sécurité physique et logique, ainsi que des processus de sécurité automatisés, des politiques de confidentialité et de sécurité des informations complètes, et des formations sur la confidentialité et la sécurité pour tout le personnel.

La sécurité est intégrée à Microsoft Azure à partir de la base, en commençant par la [durée de vue du développement de la sécurité](https://www.microsoft.com/sdl/), un processus de développement obligatoire qui incorpore des méthodologies de confidentialité par conception et de confidentialité par défaut. Le principe directeur de stratégie de sécurité de Microsoft est de « partir du principe qu’il y a une violation, » qui est une extension de la stratégie de défense en profondeur. En défiant constamment les fonctionnalités de sécurité d’Azure, Microsoft peut devancer les menaces émergentes. Pour plus d’informations sur la sécurité Azure, consultez ces [ressources](https://www.microsoft.com/trustcenter/security/azure-security).

Microsoft propose un service d’intervention en cas d’incident qui fonctionne 24h/24 et 7j/7 pour atténuer les conséquences des attaques contre Microsoft Azure. Attesté par plusieurs audits de sécurité et de conformité (par exemple, [ISO/IEC 27018](offering-iso-27018.md)), Microsoft utilise des opérations et processus rigoureux au niveau de ses centres de données pour empêcher tout accès non autorisé, y compris la surveillance vidéo 24h/24 et 7j/7, du personnel de sécurité compétent, des cartes à puce et des contrôles biométriques.

## <a name="detection-of-potential-breaches"></a>Détection de violations potentielles

Due to the nature of modern cloud computing, not all data breaches occurring in a customer cloud environment involve Microsoft Azure services. Microsoft employs a shared responsibility model for Azure services to define security and operational accountabilities. Shared responsibility is important when discussing security of a cloud service, because both the cloud services provider and the customer are accountable for portions of cloud security.

Microsoft does not monitor for or respond to security incidents within the customer's realm of responsibility. A customer-only security compromise would not be processed as an Azure security incident and would require the customer tenant to manage the response effort. Customer incident response may involve collaboration with Microsoft Azure [customer support](https://azure.microsoft.com/support/options/), given appropriate service contracts. Microsoft Azure propose également différents services (comme, par exemple, [Azure Defender](https://azure.microsoft.com/services/security-center/)) que les clients peuvent utiliser pour développer et gérer les réponses aux incidents de sécurité.

Azure répond à une fuite de données potentielle selon le processus de réponse à un incident de sécurité, qui est un sous-ensemble du plan de gestion des incidents de Microsoft Azure. La réponse aux incidents de sécurité d’Azure est implémentée à l’aide d’un processus en cinq étapes : détecter, évaluer, diagnostiquer, stabiliser et fermer. L’équipe d’intervention en cas d’incidents de sécurité peut alterner entre l’étape de diagnostic et de stabilisation au fur et à mesure que l’examen avance. Vous trouverez ci-dessous une vue d’ensemble du processus de réponse aux incidents de sécurité :

|**Stade**|**Description**|
| ------- | ------------- |
| **_1 – Détecter_* _ | Première indication d’un incident potentiel. |
| _*_2 – Évaluer_*_ | Un membre de l’équipe d’invervention en cas d’incidents évalue les conséquences et la gravité de l’événement. En fonction des données probantes, l’évaluation peut ou non aboutir à un signalement supplémentaire à l’équipe d’intervention en matière de sécurité. |
| _*_3 – Diagnostiquer_*_ | Security response experts conduct the technical or forensic investigation, identify containment, mitigation, and workaround strategies. If the security team believes that customer data may have become exposed to an unlawful or unauthorized individual, execution of the Customer Incident Notification process begins in parallel. |
| _*_4 – Stabiliser et récupérer_*_ | L’équipe d’intervention en cas d’incidents crée un plan de récupération pour atténuer le problème. Les étapes de limitation de crise telles que la mise en quarantaine des systèmes concernés peuvent avoir lieu immédiatement et parallèlement au diagnostic. Des enquêtes à plus long terme peuvent être planifiées et avoir lieu une fois que le risque immédiat est passé. |
| _*_5 – Fermeture et post-mortem_*_ | L’équipe d’intervention en cas d’incidents crée un post-mortem décrivant les détails de l’incident, avec l’intention de réviser les stratégies, procédures et processus afin d’éviter que l’événement ne se reproduise. |

Le livre blanc intitulé [Microsoft Azure Security Response in the Cloud](https://gallery.technet.microsoft.com/Azure-Security-Response-in-dd18c678) donne des détails supplémentaires sur la façon dont Microsoft examine, gère et répond aux incidents de sécurité dans Azure.

Les processus de détection utilisés par Microsoft Azure sont conçus pour découvrir les événements mettant en danger la confidentialité, l’intégrité et la disponibilité des services Azure. Plusieurs événements peuvent déclencher une enquête :

- Automated system alerts via internal monitoring and alerting frameworks. These alerts could come in the way of signature-based alarms such as anti-malware, intrusion detection or via algorithms designed to profile expected activity and alert upon anomalies.
- Les rapports de première partie des services Microsoft exécutés sur Microsoft Azure et Azure Government.
- Security vulnerabilities are reported to the [Microsoft Security Response Center (MSRC)](https://technet.microsoft.com/security/dn440717) via [secure@microsoft.com](mailto:secure@microsoft.com). MSRC works with partners and security researchers around the world to help prevent security incidents and to advance Microsoft product security.
- Les rapports client via le [Portail de support client](https://www.windowsazure.com/support/contact/) ou Microsoft Azure et le portail Azure Government Management, qui décrivent une activité suspecte attribuée à l’infrastructure Azure (par opposition à l’activité ayant lieu dans le domaine de la responsabilité du client).
- Security [Red Team and Blue Team](https://azure.microsoft.com/blog/red-teaming-using-cutting-edge-threat-simulation-to-harden-the-microsoft-enterprise-cloud/) activity. This strategy uses a highly skilled Red Team of offensive Microsoft security experts to uncover and attack potential weaknesses in Azure. The security response Blue Team must detect and defend against the Red Team's activity. Both Red and Blue Team actions are used to verify that Azure security response efforts are effectively managing security incidents. Security Red Team and Blue Team activities are operated under rules of engagement to help ensure the protection of customer data.
- Les signalements par des opérateurs des services Azure. Les employés de Microsoft sont formés pour identifier et transmettre les éventuels problèmes de sécurité.

## <a name="azures-data-breach-response"></a>Réponse d’Azure à une violation des données

Microsoft assigns the investigation appropriate priority and severity levels by determining the functional impact, recoverability, and information impact of the incident. Both the priority and severity may change over the course of the investigation, based on new findings and conclusions. Security events involving imminent or confirmed risk to customer data are treated as high severity and worked around the clock to resolution. 

Microsoft Azure classe l’impact des informations de l’incident dans les catégories de violation suivantes :

| _ *Catégorie**             | **Définition**                                                                                                                   |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| **_Aucune_* _               | Aucune information n’a été dévoilée, modifiée, supprimée ni compromise d’une façon ou d’une autre.                                                      |
| _*_Violation de la confidentialité_*_     | Des données personnelles sensibles des contribuables, employés, bénéficiaires, etc. ont été consultées ou dévoilées.                                |
| _*_Violation d’informations confidentielles_*_ | Des informations confidentielles non classifiées, telles que des informations sur les infrastructures critiques protégées (PCII), ont été consultées ou dévoilées. |
| _*_Perte d’intégrité_*_     | Des informations sensibles ou confidentielles ont été modifiées ou supprimées.                                                                     |

L’équipe d’intervention de sécurité collabore avec des ingénieurs de sécurité Microsoft Azure et des experts techniques pour classer l’événement en fonction des données factuelles des éléments de preuve. Un événement de sécurité peut-être classé de la façon suivante :

- _*False Positive**: An event that meets detection criteria but is found to be part of a normal business practice and may need to be filtered. The service team identifies the root cause for false positives and will address them in a systematic way using detection sources and fine-tuning them as needed.
- **Incident de sécurité** : un incident provoqué par un accès non autorisé à des données client ou à des données du support stockées sur un équipement de Microsoft ou dans des installations de Microsoft, ou tout accès non autorisé à ces équipement ou installations provoquant la perte, divulgation ou altération des données client ou des données de support.
- **Incident de sécurité/confidentialité déclarable au client (CRSPI)** : accès illégal ou non autorisé aux systèmes, équipements ou installations de Microsoft, ou utilisation illégale ou non autorisée de ceux-ci, provoquant la divulgation, la modification ou la perte de données client.
- **Privacy Breach** : A subtype of Security Incident involving personal data. Handling procedures are no different than a security incident.

For a CRSPI to be declared, Microsoft must determine that unauthorized access to customer data has or has likely occurred and/or that there is a legal or contractual commitment that notification must occur. It is desired, but not required, that specific customer impact, resource access, and repair steps be known. An incident is generally declared a CRSPI after the conclusion of the Diagnose stage of a security incident. However, the declaration may happen at any point that all pertinent information is available. The security incident manager must establish evidence beyond reasonable doubt that a reportable event has occurred to begin execution of the Customer Incident Notification Process.

Tout au long de l’enquête, l’équipe de réponse de sécurité collabore étroitement avec des conseillers juridiques pour vérifier que l’enquête judiciaire est menée conformément aux obligations juridiques et aux engagements vis-à-vis des clients. Il existe également des restrictions importantes sur la gestion et l’affichage des données client et système dans différents environnements d’exploitation. Les données sensibles ou confidentielles, ainsi que les données client, ne sont pas transférées en dehors de l’environnement de production sans l’approbation écrite explicite du gestionnaire des incidents enregistrée dans le ticket des incidents correspondant.

Microsoft vérifie que le risque du client et de l’entreprise est maîtrisé et que les mesures correctives sont mises en œuvre. Si nécessaire, des plans d’urgence et d’atténuation visant à résoudre les risques de sécurité immédiats sont mis en œuvre.

Microsoft also completes an internal post-mortem for data breaches. As a part of this exercise, sufficiency of response and operating procedures are evaluated, and any updates that may be necessary to the Security Incident Response SOP or related processes are identified and implemented. Internal postmortems for data breaches are highly confidential records not available to customers. Postmortems may, however, be summarized and included in other customer event notifications. These reports are provided to external auditors for review as part of Azure's routine audit cycle.

## <a name="customer-notification"></a>Notification du client

Microsoft Azure avertit les clients et les autorités réglementaires en cas de violations des données, le cas échéant. Microsoft se base sur une compartimentalisation interne importante dans l’exploitation d’Azure. Les journaux de flux de données sont également puissants. Cette conception présente des avantages car la plupart des incidents peuvent être limités à des clients spécifiques. L’objectif consiste à fournir aux clients concernés une notification précise et exploitable en temps voulu dès qu’il y a violation de leurs données.

After the declaration of a CRSPI, the notification process takes place as expeditiously as possible while still considering the security risks of moving quickly. Generally, the process of drafting notifications occurs as the incident investigation is ongoing. Customer notices are delivered in no more than 72 hours from the time we declared a breach *except* in the following circumstances:

- Microsoft believes that the act of performing a notification increases the risk to other customers. For example, the act of notifying may tip off an adversary causing an inability to remediate.
- D’autres circonstances inhabituelles ou extrêmes examinées par le service juridique Corporate External and Legal Affairs (CELA) de Microsoft et le gestionnaire exécutif des incidents.
- The 72-hour timeline may leave some incident details available. These are provided to customers and regulatory authorities as the investigation proceeds.

Microsoft Azure fournit aux clients des informations détaillées leur permettant d’effectuer des enquêtes internes et de répondre aux engagements des utilisateurs finaux, sans retarder le processus de notification de façon excessive.

La notification d’une violation des données personnelles est envoyée au client par un moyen sélectionné par Microsoft, y compris par e-mail. La notification d’une violation des données est envoyée à la liste des contacts de sécurité fournie dans Azure  Defender, et peut être configurée en suivant les [instructions d’implémentation](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details). Si les informations de contact ne sont pas fournies dans Azure Defender, la notification est envoyée à un ou plusieurs administrateurs d’un abonnement Azure. Pour garantir l’envoi correct de la notification, le client doit vérifier que les informations de contact d’administration sur chaque abonnement concerné et portail de services en ligne sont correctes.

L’équipe Microsoft Azure ou Azure Government peut également choisir d’informer d’autres membres du personnel Microsoft (par exemple, le service client et le gestionnaire de compte du client ou le gestionnaire de compte technique). Ces personnes ont souvent des relations étroites avec le client et peuvent favoriser une correction plus rapide

## <a name="microsoft-dynamics-365-built-in-security-features"></a>Fonctionnalités de sécurité intégrées de Microsoft Dynamics 365

Microsoft Dynamics 365 tire parti de l’infrastructure du service cloud et des fonctionnalités de sécurité intégrées pour assurer la protection des données au moyen de mesures et de mécanismes de sécurité. Par ailleurs, Dynamics 365 offre des fonctionnalités efficaces d’accès aux données et de collaboration garantissant l’intégrité des données et la confidentialité dans les domaines suivants : [sécurisation des identités, protection des données, sécurité basée sur les rôles et gestion des menaces](https://www.microsoft.com/trustcenter/security/dynamics365-security).

L’offre Microsoft Dynamics 365 suit les mêmes mesures techniques et organisationnelles que prennent une ou plusieurs équipes de service Microsoft Azure pour la sécurisation des données contre leur divulgation. Par conséquent, les informations décrites dans le document de notification « Violation de données Microsoft Azure » sont similaires au service Microsoft Dynamics 365.

## <a name="learn-more"></a>En savoir plus

[Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/trust-center/privacy/gdpr-overview)
