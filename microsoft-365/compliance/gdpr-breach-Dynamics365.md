---
title: Dynamics 365 et notification de violation dans le cadre du RGPD
description: Protection de Dynamics 365 vis-à-vis des violations de données personnelles, et réponse et notification de Microsoft en cas de violation.
keywords: Dynamics 365, Microsoft 365, Microsoft 365 Éducation, documentation Microsoft 365, RGPD
localization_priority: Priority
ms.prod: Microsoft-365-enterprise
ms.topic: article
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: GDPR
ms.openlocfilehash: 7fbe7f277825905326a1234249e5bccf7082658d
ms.sourcegitcommit: 6e2a54ec395eaef4c4658ca52322c3d0f184ca02
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "34698316"
---
# <a name="dynamics-365-and-breach-notification-under-the-gdpr"></a>Dynamics 365 et notification de violation dans le cadre du RGPD

Dynamics 365 respecte les obligations imposées par le Règlement général sur la protection des données (RGPD) et prend des mesures de sécurité étendues pour assurer la protection contre les violations de données. Microsoft s’efforce en permanence de fournir des services de qualité professionnelle hautement sécurisés aux clients Dynamics 365. Les informations contenues dans cette section résument la façon dont Microsoft Dynamics 365 protège contre les incidents de sécurité/violations de données, et présentent le processus que nous suivons pour y répondre et en informer nos clients.

## <a name="microsoft-dynamics-365-built-in-security-features"></a>Fonctionnalités de sécurité intégrées de Microsoft Dynamics 365

Microsoft Dynamics 365 tire parti de l’infrastructure du service cloud et des fonctionnalités de sécurité intégrées pour assurer la protection des données au moyen de mesures et de mécanismes de sécurité. Par ailleurs, Dynamics 365 offre des fonctionnalités efficaces d’accès aux données et de collaboration garantissant l’intégrité des données et la confidentialité dans les domaines suivants : [sécurisation des identités, protection des données, sécurité basée sur les rôles et gestion des menaces](https://www.microsoft.com/trustcenter/security/dynamics365-security).

## <a name="incident-response-training"></a>Formation à la réponse aux incidents

Chaque employé travaillant sur Microsoft Dynamics 365 reçoit une formation relative aux incidents de sécurité et aux procédures de réponse appropriées à son rôle. Chaque employé Microsoft Dynamics 365 suit une formation initiale, puis une formation d’actualisation chaque année par la suite. Cette formation a pour objectif de présenter à l’employé les concepts de base de l’approche de la sécurité de Microsoft, de manière à ce qu’à l’issue de la formation, tous les collaborateurs puissent comprendre :

- la définition d’un incident de sécurité ;
- la responsabilité qui incombe à tous les employés de signaler les incidents de sécurité ;
- la procédure de transmission d’un incident de sécurité potentiel à l’équipe de réponse aux incidents de sécurité Dynamics 365 ;
- la manière dont l’équipe de réponse aux incidents de sécurité Dynamics 365 répond à l’incident ;
- les questions spéciales concernant la confidentialité, en particulier celle du client ;
- où trouver des informations complémentaires sur la sécurité et la confidentialité, ainsi que les contacts auxquels les informations doivent être remontées.

## <a name="how-does-microsoft-dynamics-365-define-security-incidentpotential-breaches"></a>Définition d’un incident de sécurité/d’une violation potentielle par Microsoft Dynamics 365

Les termes « incident de sécurité » ou « violation de données » désignent des événements tels que des accès illégaux aux données du client stockées sur du matériel Microsoft ou dans des installations Microsoft, ou tout accès non autorisé à ces équipements ou installations risquant d’entraîner la perte, la divulgation ou l’altération des données client. Les réponses de Microsoft aux incidents de sécurité/volations de données ont pour objectif de protéger les données client et les services Dynamics 365. L’approche de la gestion d’un incident de sécurité par Microsoft est conforme à la publication spéciale (SP) [800 61](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) du NIST ([National Institute of Standards and Technology)](https://www.nist.gov/).

Microsoft ne surveille pas les incidents de sécurité et n’y répond pas dans le domaine de la responsabilité du client. Une compromission de la sécurité du client uniquement ne serait pas traitée comme un incident de sécurité Dynamics 365 et exigerait que le client du client gère l’effort de réponse. La réponse à un incident client peut impliquer la collaboration du service clientèle de Microsoft Dynamics 365, avec les contrats de service appropriés.

## <a name="detection-of-potential-breaches"></a>Détection de violations potentielles

Dynamics 365 répond à une violation des données potentielle selon le processus de réponse à un incident de sécurité, qui est un sous-ensemble du plan de gestion des incidents de Microsoft Dynamics 365. La réponse aux incidents de sécurité de Dynamics 365 est implémentée à l’aide d’un processus en cinq étapes : détecter, évaluer, diagnostiquer, stabiliser et fermer. L’équipe de réponse aux incidents de sécurité peut alterner entre les étapes de diagnostic et de stabilisation à mesure que l’examen avance. Vous trouverez ci-dessous une vue d’ensemble du processus de réponse aux incidents de sécurité :

|**Stade**|**Description**|
|:-----|:-----|
| ***1 : Détecter*** | Première indication d’un incident potentiel. |
| ***2 : Évaluer*** | Un membre de l’équipe de garde de réponse aux incidents de sécurité évalue les conséquences et la gravité de l’événement. En fonction des données probantes, l’évaluation peut ou non aboutir à un signalement supplémentaire à l’équipe de réponse aux incidents de sécurité. |
| ***3 : Diagnostiquer*** | Des spécialistes de la réponse aux incidents de sécurité effectuent des examens techniques et mènent une enquête judiciaire, identifient des stratégies de limitation, d’atténuation et de contournement. Si l’équipe de sécurité pense que les données client ont peut-être été exposées à un individu non autorisé ou ayant commis des actes illicites, l’exécution du processus de notification des incidents du client débute en parallèle.|
| ***4 : Stabiliser et récupérer*** | L’équipe de réponse aux incidents de sécurité crée un plan de récupération pour atténuer le problème. Les étapes de limitation de la crise telles que la mise en quarantaine des systèmes concernés peuvent avoir lieu immédiatement et parallèlement au diagnostic. Des enquêtes à plus long terme peuvent être planifiées et se produire une fois que le risque immédiat est passé. |
| ***5 : Fermeture et post-mortem*** | L’équipe de réponse aux incidents de sécurité crée un post-mortem décrivant les détails de l’incident, avec l’intention de réviser les stratégies, procédures et processus afin d’éviter que l’événement se reproduise. |

Le livre blanc intitulé [Dynamics Security Incident Management](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=266d445f-ea95-42de-9124-4b2118a639ee&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers) donne des détails supplémentaires sur la façon dont Microsoft examine, gère et répond aux incidents de sécurité dans Dynamics 365.

Les processus de détection utilisés par Microsoft Dynamics 365 sont conçus pour découvrir les événements mettant en danger la confidentialité, l’intégrité et la disponibilité des services Dynamics 365. Plusieurs événements peuvent déclencher une enquête :

- Les alertes système automatisées via la surveillance interne et les infrastructures d’alertes. Ces alertes peuvent survenir en tant qu’alarmes basées sur la signature (par exemple, les programmes malveillants, la détection de l’intrusion) ou via des algorithmes conçus pour profiler l’activité prévue et signaler des anomalies.
- Une première partie signale l’exécution de services Microsoft Dynamics 365 déployés dans un cloud public et de services Microsoft Dynamics 365 déployés dans un cloud souverain.
- Les failles de sécurité sont signalées au [centre de réponse de sécurité Microsoft (MSRC)](https://technet.microsoft.com/security/dn440717) via <secure@microsoft.com>. Le MSRC fonctionne avec des partenaires et des chercheurs en sécurité dans le monde entier afin d’éviter les incidents de sécurité et améliorer la sécurité des produits Microsoft.
- Des rapports client qui décrivent une activité suspecte attribuée aux Services Microsoft Dynamics 365 (par opposition à une activité se produisant dans le cadre du domaine de responsabilité du client).
- Sécurité activité [d’Équipe Rouge et Équipe Bleue](https://azure.microsoft.com/blog/red-teaming-using-cutting-edge-threat-simulation-to-harden-the-microsoft-enterprise-cloud/). Cette stratégie utilise une équipe rouge hautement qualifiée d’experts en matière de sécurité pour découvrir et attaquer les faiblesses potentielles dans les services Microsoft Dynamics 365. L’équipe de sécurité couleur bleue doit détecter et se défendre contre l’activité de l’équipe rouge. Les actions des équipes rouge et bleue sont utilisées pour vérifier que le travail de réponse de sécurité Microsoft Dynamics 365 gère efficacement les incidents de sécurité. Les activités de la sécurité des équipes rouge et bleue sont régies par les exigences de la responsabilité, afin de garantir la protection des données client.
- Signalements par les opérateurs des services Microsoft Dynamics 365. Les employés de Microsoft sont formés pour identifier et transmettre les éventuels problèmes de sécurité.

## <a name="microsoft-dynamics-365-data-breach-response"></a>Réponse aux violations de données Microsoft Dynamics 365

Microsoft affecte les niveaux de priorité et de gravité appropriés de l’enquête en déterminant l’incidence fonctionnelle, la capacité de récupération et l’incidence des informations de l’incident. La priorité et la gravité peuvent changer au fur et à mesure que l’enquête avance, en fonction des nouvelles découvertes et conclusions. Les événements de sécurité impliquant un risque imminent ou confirmé pour les données client sont traités comme étant de gravité élevée et sont résolus en priorité. Microsoft Dynamics 365 définit une violation de données comme une violation des « données personnelles d’un utilisateur de services en ligne ou d’employés de Microsoft ».

L’équipe de réponse de sécurité collabore avec des ingénieurs de sécurité Microsoft Dynamics 365 et des experts techniques pour classer l’événement en fonction des données factuelles des éléments de preuve. Un événement de sécurité peut être classé de la façon suivante :

- **Faux positif :** un événement qui répond aux critères de détection mais qui fait partie d’une pratique d’entreprise normale et nécessite peut-être d’être filtré. L’équipe de service identifiera la cause première des faux positifs et les résoudra de manière systématique en tirant parti des sources de détection et en les ajustant<span id="_Toc350859432" class="anchor"></span> en fonction des besoins.
- **Incident de sécurité :** un incident provoqué par un accès non autorisé à des données client ou à des données du support stockées sur des équipements de Microsoft ou dans des installations de Microsoft, ou tout accès non autorisé à ces équipements ou installations provoquant la perte, la divulgation ou l’altération des données client ou des données de support.
- **Incident de sécurité déclarable au client :** accès illégal ou non autorisé aux systèmes, équipements ou installations de Microsoft, ou utilisation illégale ou non autorisée de ceux-ci, provoquant la divulgation, la modification ou la perte de données client.
- **Incident de confidentialité :** un sous-type d’incident de sécurité impliquant des données personnelles. Les procédures de gestion sont les mêmes que celles qui concernent les incidents de sécurité.

Pour qu’un CRSI soit déclaré, Microsoft doit déterminer que l’accès non autorisé aux données client a ou a probablement eu lieu et/ou qu’une notification juridique ou contractuelle doit être envoyée. Il est possible, mais ce n’est pas obligatoire, de connaître l’impact de certains clients, l’accès aux ressources et les étapes de réparation. Un incident est généralement déclaré comme CRSI à la fin de l’étape de diagnostic d’un incident de sécurité. Toutefois, la déclaration peut arriver à tout moment lorsque toutes les informations pertinentes soient disponibles. Le responsable des incidents de sécurité doit établir des preuves irréfutables qu’un événement signalable a eu lieu pour commencer l’exécution du processus de notification d’incident client.

Tout au long de l’enquête, l’équipe de réponse de sécurité collabore étroitement avec des conseillers juridiques pour vérifier que l’enquête judiciaire est menée conformément aux obligations juridiques et aux engagements vis-à-vis des clients. Il existe également des restrictions importantes sur la gestion et l’affichage des données client et système dans différents environnements d’exploitation. Les données sensibles ou confidentielles, ainsi que les données client, ne sont pas transférées en dehors de l’environnement de production sans l’approbation écrite explicite du gestionnaire des incidents enregistrée dans le ticket des incidents correspondant.

Microsoft vérifie que le risque du client et de l’entreprise est maîtrisé et que les mesures correctives sont mises en œuvre. Si nécessaire, des plans d’urgence et d’atténuation visant à résoudre les risques de sécurité immédiats sont mis en œuvre.

Microsoft effectue aussi un post-mortem interne pour les violations de données. Dans le cadre de cet exercice, le niveau suffisant de réponse et les procédures d’exploitation sont évalués, et les mises à jour pouvant être nécessaires pour les stratégies de sécurité internes de Microsoft ou des processus connexes sont identifiées et mises en œuvre. Les post-mortems internes pour les violations de données sont des enregistrements hautement confidentiels qui ne sont pas accessibles aux clients. Les post-mortems peuvent toutefois être synthétisés et inclus dans d’autres notifications d’événement au client. Ces rapports sont fournis à des auditeurs externes pour révision dans le cadre du cycle d’audit de routine de Dynamics 365.

## <a name="customer-notification"></a>Notification du client

Microsoft Dynamics 365 peut avertir les clients et les autorités réglementaires en cas de violations des données. Microsoft se base sur une compartimentalisation interne importante dans l’exploitation des services Dynamics 365. Les journaux de flux de données sont également puissants. Cette conception présente des avantages, car la plupart des incidents peuvent être limités à des clients spécifiques. L’objectif consiste à fournir aux clients concernés une notification précise et exploitable en temps voulu dès qu’il y a violation de leurs données.

Suite à un CRSI déclaré, le processus de notification a lieu aussi rapidement que possible, en sachant que les risques de sécurité se déplacent rapidement. Généralement, le processus d’élaboration des notifications a lieu alors que l’analyse de l’incident est en cours. Les notifications client sont envoyées rapidement après la déclaration d’une violation *sauf* dans les cas suivants :

- Microsoft estime que le fait d’exécuter une notification augmentera le risque pour d’autres clients. Par exemple, la notification peut avertir un adversaire, et ainsi empêcher de résoudre le problème.
- D’autres circonstances inhabituelles ou extrêmes examinées par le service juridique de Microsoft et le gestionnaire exécutif des incidents.

Microsoft Dynamics 365 fournit aux clients des informations détaillées leur permettant d’effectuer des recherches internes et de répondre aux engagements des utilisateurs finaux, sans retarder le processus de notification de façon excessive.

La notification d’une violation des données personnelles est envoyée au client par un moyen sélectionné par Microsoft, y compris par e-mail. La notification d’une violation des données est envoyée à la liste des contacts client / administrateurs (uniquement des clients concernés) fournie dans le centre de sécurité Office, qui peut être configurée par l’administrateur du client. Pour garantir l’envoi correct de la notification, le client doit vérifier que les informations de contact d’administration sur chaque portail de services en ligne et chaque abonnement concerné sont correctes.

L’équipe Microsoft Dynamics 365 peut également choisir d’informer d’autres membres du personnel Microsoft (par exemple, le service client et le gestionnaire de compte du client ou le gestionnaire de compte technique). Ces personnes ont souvent des relations étroites avec le client et peuvent permettre une résolution plus rapide des problèmes.<span id="_Appendix_A" class="anchor"></span>

## <a name="learn-more"></a>En savoir plus

- [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/TrustCenter/Privacy/gdpr/default.aspx)