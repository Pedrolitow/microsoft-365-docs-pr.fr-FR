---
title: Service de traitement de données pour la notification Windows Enterprise sous RGPD
description: Service de traitement de données pour la protection de Windows Enterprise vis-à-vis des violations de données personnelles, et réponse et notification de Microsoft en cas de violation.
keywords: Service de traitement des données pour Windows Enterprise, Microsoft 365, documentation Microsoft 365, RGPD
localization_priority: Priority
ROBOTS: NOINDEX, NOFOLLOW
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: dc921215ef8e1e1a1a187a5b8be46916c30d5f2c
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48920278"
---
# <a name="data-processor-service-for-windows-enterprise-breach-notification-under-the-gdpr"></a>Service de traitement de données pour la notification de violation Windows Enterprise sous RGPD

>[!NOTE]
>This topic is intended for participants in the data processor service for Windows Enterprise preview program and requires acceptance of specific terms of use. To learn more about the program and agree to the terms of use, see [https://aka.ms/WindowsEnterprisePublicPreview](https://aka.ms/WindowsEnterprisePublicPreview).

Microsoft data processor service for Windows Enterprise takes its obligations under the General Data Protection Regulation (GDPR) seriously. Microsoft data processor service for Windows Enterprise takes extensive security measures to protect against data breaches. These include dedicated threat management teams that proactively anticipate, prevent, and mitigate malicious access.  Internal security measures such as port scanning, perimeter vulnerability scanning, and intrusion detection detect and prevent malicious access, as well as automated security processes, comprehensive information security and privacy policies, and security and privacy training for all personnel. 

Security is built into the Microsoft data processor service for Windows Enterprise from the ground up, starting with the [Security Development Lifecycle](https://www.microsoft.com/sdl/), a mandatory development process that incorporates privacy-by-design and privacy-by-default methodologies. The guiding principle of Microsoft's security strategy is to 'assume breach', which is an extension of the defense-in-depth strategy. By constantly challenging the security capabilities of the data processor service for Windows Enterprise, Microsoft can stay ahead of emerging threats. For more information on the data processor service for Windows Enterprise security, please review these [resources](https://www.microsoft.com/TrustCenter/Security/windows10-security) the data processor service for Windows Enterprise responds to a potential data breach according to the security incident response process. The data processor service for Windows Enterprise security incident response is implemented using a five-stage process: Detect, Assess, Diagnose, Stabilize, and Close. The Security Incident Response Team may alternate between the diagnose and stabilize stages as the investigation progresses. An overview of the security incident response process is below: 

|**Stade**|**Description**|
| ------- | ------------- |
| **_1 – Détecter_* _ | Première indication d’un incident potentiel. |
| _*_2 – Évaluer_*_ | Un membre de l’équipe d’invervention en cas d’incidents évalue les conséquences et la gravité de l’événement. En fonction des données probantes, l’évaluation peut ou non aboutir à un signalement supplémentaire à l’équipe d’intervention en matière de sécurité. |
| _*_3 – Diagnostiquer_*_ | Security response experts conduct the technical or forensic investigation, identify containment, mitigation, and workaround strategies. If the security team believes that customer data may have become exposed to an unlawful or unauthorized individual, execution of the Customer Incident Notification process begins in parallel. |
| _*_4 – Stabiliser et récupérer_*_ | L’équipe d’intervention en cas d’incidents crée un plan de récupération pour atténuer le problème. Les étapes de limitation de crise telles que la mise en quarantaine des systèmes concernés peuvent avoir lieu immédiatement et parallèlement au diagnostic. Des enquêtes à plus long terme peuvent être planifiées et avoir lieu une fois que le risque immédiat est passé. |
| _*_5 – Fermeture et post-mortem_*_ | L’équipe d’intervention en cas d’incidents crée un post-mortem qui décrit les détails de l’incident, avec l’intention de réviser les stratégies, procédures et processus afin d’éviter la récurrence de l’événement. |

The detection processes used by Microsoft data processor service for Windows Enterprise are designed to discover events that risk the confidentiality, integrity, and availability of the data processor service for Windows Enterprise. Several events can trigger an investigation: 

 - Automated system alerts via internal monitoring and alerting frameworks. These alerts could come in the way of signature-based alarms such as anti-malware, intrusion detection or via algorithms designed to profile expected activity and alert upon anomalies.
 - Les rapports de première partie des services Microsoft exécutés sur Microsoft Azure et Azure Government.
 - Security vulnerabilities are reported to the [Microsoft Security Response Center (MSRC)](https://technet.microsoft.com/security/dn440717) via [secure@microsoft.com] (mailto:secure@microsoft.com). MSRC works with partners and security researchers around the world to help prevent security incidents and to advance Microsoft product security.
 - Les rapports client via le portail de support client ou Microsoft Azure et le portail Azure Government Management, qui décrivent une activité suspecte attribuée à l’infrastructure Azure (par opposition à l’activité ayant lieu dans le domaine de la responsabilité du client).
 - Security [Red Team and Blue Team](https://azure.microsoft.com/blog/red-teaming-using-cutting-edge-threat-simulation-to-harden-the-microsoft-enterprise-cloud/) activity. This strategy uses a highly skilled Red Team of offensive Microsoft security experts to uncover and attack potential weaknesses in Azure. The security response Blue Team must detect and defend against the Red Team’s activity. Both Red and Blue Team actions are used to verify that Azure security response efforts are effectively managing security incidents. Security Red Team and Blue Team activities are operated under rules of engagement to help ensure the protection of customer data.
 - Les signalements par des opérateurs des services Azure. Les employés de Microsoft sont formés pour identifier et transmettre les éventuels problèmes de sécurité.

 ## <a name="data-processor-service-for-windows-enterprise-data-breach-response"></a>Service de traitement de données pour la réponse aux violations de données Windows Enterprise 

 Microsoft assigns the investigation appropriate priority and severity levels by determining the functional impact, recoverability, and information impact of the incident. Both the priority and severity may change over the course of the investigation, based on new findings and conclusions. Security events involving imminent or confirmed risk to customer data are treated as high severity and worked around the clock to resolution. Microsoft data processor service for Windows Enterprise categorizes the information impact of the incident into the following breach categories: 

| _ *Catégorie**             | **Définition**                                                                                                                   |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| **_Aucune_* _               | Aucune information n’a été supprimée, modifiée, supprimée ni compromise d’une façon ou d’une autre. |
| _*_Violation de la confidentialité_*_     | Des données personnelles sensibles des contribuables, employés, bénéficiaires, etc. ont été consultées ou supprimées. |
| _*_Violation d’informations confidentielles_*_ | Des informations confidentielles non classifiées, telles que des informations sur les infrastructures critiques protégées (PCII), ont été consultées ou supprimées. |
| _*_Perte d’intégrité_*_     | Des informations sensibles ou confidentielles ont été modifiées ou supprimées. |

The Security Response Team works with Microsoft data processor service for Windows Enterprise Security Engineers and SMEs to classify the event based on factual data from the evidence. A security event may be classified as: 

 - _*False Positive**: An event that meets detection criteria but is found to be part of a normal business practice and may need to be filtered. The service team will identify the root cause for false positives and will address them in a systematic way leveraging detection sources and fine-tuning them as needed. 
 - **Incident de sécurité** : un incident provoqué par un accès non autorisé à des données client ou à des données du support stockées sur un équipement de Microsoft ou dans des installations de Microsoft, ou tout accès non autorisé à ces équipement ou installations provoquant la perte, divulgation ou altération des données client ou des données de support. 
 - **Incident de sécurité déclarable au client**  : un accès illégal ou non autorisé ou une utilisation illégale ou non autorisée de systèmes, équipements ou installations Microsoft provoquant la divulgation, modification ou perte de données client. 
 - **Privacy Breach** : A subtype of Security Incident involving personal data. Handling procedures are no different than a security incident. 

 Pour déclarer les CRSI (Incident de sécurité déclarable au client), Microsoft doit déterminer qu’un accès non autorisé aux données client a eu lieu ou a très probablement eu lieu et/ou qu’il existe un engagement juridique ou contractuel qu’une notification doit se produire. Il est souhaitable, mais pas obligatoire, que l’impact du client spécifique, l’accès aux ressources et les étapes de réparation soient connus. Un incident est généralement déclaré comme un CRSI après la conclusion de l’étape de diagnostic d’un incident de sécurité ; toutefois, la déclaration peut se produire à tout moment où toutes les informations pertinentes sont disponibles. Le gestionnaire des incidents de sécurité doit établir des preuves au-delà de tout doute raisonnable qu’un événement déclarable s’est produit pour commencer l’exécution du processus de notification d’un incident client. 

Tout au long de l’enquête, l’équipe de réponse de sécurité collabore étroitement avec des conseillers juridiques pour vérifier que l’enquête judiciaire est menée conformément aux obligations juridiques et aux engagements vis-à-vis des clients. Il existe également des restrictions importantes sur la gestion et l’affichage des données client et système dans différents environnements d’exploitation. Les données sensibles ou confidentielles, ainsi que les données client, ne sont pas transférées en dehors de l’environnement de production sans l’approbation écrite explicite du gestionnaire des incidents enregistrée dans le ticket des incidents correspondant. 

Microsoft vérifie que le risque du client et de l’entreprise est maîtrisé et que les mesures correctives sont mises en œuvre. Si nécessaire, des plans d’urgence et d’atténuation visant à résoudre les risques de sécurité immédiats sont mis en œuvre. 

Microsoft also completes an internal post-mortem for data breaches. As a part of this exercise, sufficiency of response and operating procedures are evaluated, and any updates that may be necessary to the Security Incident Response SOP or related processes are identified and implemented. Internal postmortems for data breaches are highly confidential records not available to customers. Postmortems may, however, be summarized and included in other customer event notifications. These reports are provided to external auditors for review as part of the data processor service for Windows Enterprise routine audit cycle. 

## <a name="customer-notice"></a>Avis client

Microsoft data processor service for Windows Enterprise notifies customers and regulatory authorities of data breaches as required. Microsoft relies on heavy internal compartmentalization in the operation of the data processor service for Windows Enterprise. Data flow logs are also robust. As a benefit of this design, most incidents can be scoped to specific customers. The goal is to provide impacted customers with an accurate, actionable, and timely notice when their data has been breached. 

After the declaration of a CRSI, the notification process takes place as expeditiously as possible while still considering the security risks of moving quickly. Generally, the process of drafting notifications occurs as the incident investigation is ongoing. Customer notices are delivered in no more than 72 hours from the time we declared a breach except for the following circumstances: 

 - Microsoft estime que le fait d’exécuter une notification augmentera le risque pour d’autres clients. Par exemple, la notification peut avertir un adversaire, et ainsi empêcher de résoudre le problème. 
 - D’autres circonstances inhabituelles ou extrêmes examinées par le service juridique Corporate External and Legal Affairs (CELA) de Microsoft et le gestionnaire exécutif des incidents. 

 Le service de traitement des données de Microsoft pour Windows Enterprise fournit aux clients des informations détaillées leur permettant d’effectuer des enquêtes internes et de répondre aux engagements des utilisateurs finaux, sans retarder le processus de notification de façon excessive. 

La notification d’une violation des données personnelles est envoyée au client par un moyen sélectionné par Microsoft, y compris par e-mail. La notification d’une violation des données est envoyée à la liste des contacts de sécurité fournie dans Azure  Defender, et peut être configurée en suivant les [instructions d’implémentation](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details). Si les informations de contact ne sont pas fournies dans Azure Defender, la notification est envoyée à un ou plusieurs administrateurs d’un abonnement Azure. Pour garantir l’envoi correct de la notification, le client doit vérifier que les informations de contact d’administration sur chaque abonnement concerné et portail de services en ligne sont correctes.

Le service de traitement des données de Microsoft pour l’équipe Windows Enterprise peut également choisir d’informer d’autres membres du personnel Microsoft (par exemple, le service client et le gestionnaire de compte du client ou le gestionnaire de compte technique). Ces personnes ont souvent des relations étroites avec le client et peuvent favoriser une correction plus rapide 

Pour plus d’informations sur la façon dont Microsoft détecte et répond à une violation des données personnelles, reportez-vous à l’article [Notification des violations de données en vertu du RGPD](https://servicetrust.microsoft.com/ViewPage/GDPRBreach) dans le portail d’approbation de services.
