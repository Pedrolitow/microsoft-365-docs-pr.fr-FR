---
title: Azure et notification de violation dans le cadre du RGPD
description: Protection d’Azure vis-à-vis des violations de données personnelles, et réponse et notification de Microsoft en cas de violation.
keywords: Azure, Microsoft 365, Microsoft 365 Éducation, documentation Microsoft 365 documentation, RGPD
author: BrendaCarter
localization_priority: Priority
audience: itpro
ms.prod: Microsoft-365-enterprise
ms.topic: article
ms.date: 04/13/2018
ms.author: bcarter
manager: laurawi
ms.collection: GDPR
ms.openlocfilehash: 8b2a0bd52054a3228ba8c9536e6db552735b1f33
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867250"
---
# <a name="azure-and-breach-notification-under-the-gdpr"></a>Azure et notification de violation dans le cadre du RGPD

Microsoft Azure prend au sérieux ses obligations dans le cadre du Règlement Général sur la Protection des Données Personnelles (RGPD). Microsoft Azure prend des mesures de sécurité étendues pour protéger contre les violations des données. Celles-ci incluent des contrôles de sécurité physique et logique, ainsi que des processus de sécurité automatisés, des politiques de confidentialité et de sécurité des informations complètes, et des formations sur la confidentialité et la sécurité pour tout le personnel.

La sécurité est intégrée à Microsoft Azure à partir de la base, en commençant par la [durée de vue du développement de la sécurité](https://www.microsoft.com/sdl/), un processus de développement obligatoire qui incorpore des méthodologies de confidentialité par conception et de confidentialité par défaut. Le principe directeur de stratégie de sécurité de Microsoft est de « partir du principe qu’il y a une violation, » qui est une extension de la stratégie de défense en profondeur. En défiant constamment les fonctionnalités de sécurité d’Azure, Microsoft peut devancer les menaces émergentes. Pour plus d’informations sur la sécurité Azure, consultez ces [ressources](https://www.microsoft.com/trustcenter/security/azure-security).

Microsoft propose un service d’intervention en cas d’incident qui fonctionne 24h/24 et 7j/7 pour atténuer les conséquences des attaques contre Microsoft Azure. Attesté par plusieurs audits de sécurité et de conformité (par exemple, [ISO/IEC 27018](https://www.microsoft.com/trustcenter/compliance/iso-iec-27018)), Microsoft utilise des opérations et processus rigoureux au niveau de ses centres de données pour empêcher tout accès non autorisé, y compris la surveillance vidéo 24h/24 et 7j/7, du personnel de sécurité compétent, des cartes à puce et des contrôles biométriques.

#### <a name="detection-of-potential-breaches"></a>Détection de violations potentielles
-------------------------------

En raison de la nature du cloud computing moderne, toutes les violations de données se produisant dans un environnement cloud client n’impliquent pas les services Microsoft Azure. Microsoft utilise un modèle de responsabilité partagée pour les services Azure pour définir la sécurité et les responsabilités opérationnelles. La responsabilité partagée est particulièrement importante dans le cas de la sécurité d’un service cloud, car le fournisseur de services cloud et le client sont responsables de certaines parties de la sécurité dans le cloud.

Microsoft ne surveille pas les incidents de sécurité et n’y répond pas dans le domaine de la responsabilité du client. Une compromission de la sécurité du client uniquement ne serait pas traitée comme un incident de sécurité Azure et exigerait que le client du client gère l’effort de réponse. La réponse à un incident client peut impliquer la collaboration du [service clientèle](https://azure.microsoft.com/support/options/) de Microsoft Azure, avec des contrats de service appropriés. Microsoft Azure propose également différents services (par exemple, le [centre de sécurité Azure](https://azure.microsoft.com/services/security-center/)) que les clients peuvent utiliser pour développer et gérer la réponse aux incidents de sécurité.

Azure répond à une violation des données potentielle selon le processus de réponse à un incident de sécurité, qui est un sous-ensemble du plan de gestion des incidents de Microsoft Azure. La réponse aux incidents de sécurité d’Azure est implémentée à l’aide d’un processus en cinq étapes : détecter, évaluer, diagnostiquer, stabiliser et fermer. L’équipe de réponse aux incidents de sécurité peut alterner entre l’étape de diagnostic et de stabilisation au fur et à mesure que l’examen avance. Vous trouverez ci-dessous une vue d’ensemble du processus de réponse aux incidents de sécurité :

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">Phase</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">Détecter</td>
<td align="left">Première indication d’un incident potentiel.</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">Évaluer</td>
<td align="left">Un membre de l’équipe de garde de réponse aux incidents de sécurité évalue les conséquences et la gravité de l’événement. En fonction des données probantes, l’évaluation peut ou non aboutir à un signalement supplémentaire à l’équipe de réponse aux incidents de sécurité.</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left">Diagnostiquer</td>
<td align="left"><p>Des spécialistes de la réponse aux incidents de sécurité effectuent des examens techniques et mènent une enquête judiciaire, identifient la limitation, l’atténuation et les stratégies de contournement.</p>
<p>Si l’équipe de sécurité pense que les données client ont peut-être été exposées à un individu non autorisé ou ayant commis des actes illicites, l’exécution du processus de notification des incidents du client débute en parallèle.</p></td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left">Stabiliser et récupérer</td>
<td align="left">L’équipe de réponse aux incidents de sécurité crée un plan de récupération pour atténuer le problème. Les étapes de limitation de la crise telles que la mise en quarantaine des systèmes concernés peuvent avoir lieu immédiatement et parallèlement au diagnostic. Des enquêtes à plus long terme peuvent être planifiées et se produire une fois que le risque immédiat est passé.</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left">Fermeture et post-mortem</td>
<td align="left">L’équipe de réponse aux incidents de sécurité crée un post-mortem qui décrit les détails de l’incident, avec l’intention de réviser les stratégies, procédures et processus afin d’éviter une récurrence de l’événement.</td>
</tr>
</tbody>
</table>

Le livre blanc intitulé [Microsoft Azure Security Response in the Cloud](https://gallery.technet.microsoft.com/Azure-Security-Response-in-dd18c678) donne des détails supplémentaires sur la façon dont Microsoft examine, gère et répond aux incidents de sécurité dans Azure.

Les processus de détection utilisés par Microsoft Azure sont conçus pour découvrir les événements mettant en danger la confidentialité, l’intégrité et la disponibilité des services Azure. Plusieurs événements peuvent déclencher une enquête :

-   Les alertes système automatisées via la surveillance interne et les infrastructures d’alertes. Ces alertes peuvent survenir en tant qu’alarmes basées sur la signature (par exemple, les programmes malveillants, la détection de l’intrusion) ou via des algorithmes conçus pour profiler l’activité prévue et signaler des anomalies.

-   Les rapports de première partie des services Microsoft exécutés sur Microsoft Azure et Azure Government.

-   Les failles de sécurité sont signalées au [centre de réponse de sécurité Microsoft (MSRC)](https://technet.microsoft.com/security/dn440717) via <secure@microsoft.com>. MSRC fonctionne avec des partenaires et des chercheurs en sécurité dans le monde entier afin d’éviter les incidents de sécurité et améliorer la sécurité des produits Microsoft.

-   Les rapports client via le [portail de support client](http://www.windowsazure.com/support/contact/) ou Microsoft Azure et le portail Azure Government Management, qui décrivent une activité suspecte attribuée à l’infrastructure Azure (par opposition à l’activité ayant lieu dans le domaine de la responsabilité du client).

-   L’activité de sécurité [Équipe rouge et équipe bleue](https://azure.microsoft.com/blog/red-teaming-using-cutting-edge-threat-simulation-to-harden-the-microsoft-enterprise-cloud/). Cette stratégie utilise une équipe rouge hautement qualifiée de spécialistes de la sécurité Microsoft pour découvrir des faiblesses potentielles dans Azure et les attaquer. L’équipe bleue de la réponse de sécurité doit détecter les activités de l’équipe rouge et se défendre contre elles. Les actions de l’équipe rouge et de l’équipe bleue servent à vérifier que tous les efforts de réponse aux incidents de sécurité Azure gèrent efficacement les incidents de sécurité. Les activités de sécurité de l’équipe rouge et de l’équipe bleue sont effectuées dans le cadre de règles d’engagement afin de garantir la protection des données client.

-   Les signalements par des opérateurs des services Azure. Les employés de Microsoft sont formés pour identifier et transmettre les éventuels problèmes de sécurité.

#### <a name="azures-data-breach-response"></a>Réponse d’Azure à une violation des données
----------------------------

Microsoft affecte les niveaux de priorité et de sévérité appropriés de l’enquête en déterminant l’impact fonctionnel, la récupérabilité et l’impact des informations de l’incident. La priorité et la sévérité peuvent changer au fur et à mesure que l’enquête avance, en fonction des nouvelles découvertes et conclusions. Les événements de sécurité impliquant un risque imminent ou confirmé pour les données client sont traités comme une sévérité élevée et résolu en priorité. Microsoft Azure classe l’impact des informations de l’incident dans les catégories de violation suivantes :

<table>
<thead>
<tr class="header">
<th align="left">Catégorie</th>
<th align="left">Définition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Aucun</td>
<td align="left">Aucune information n’a été dévoilée, modifiée, supprimée ou compromise d’une façon ou d’une autre.</td>
</tr>
<tr class="even">
<td align="left">Violation de la confidentialité</td>
<td align="left">Des données personnelles sensibles des contribuables, employés, bénéficiaires, etc. ont été consultées ou dévoilées.</td>
</tr>
<tr class="odd">
<td align="left">Violation d’informations confidentielles</td>
<td align="left">Des informations confidentielles non classifiées, telles que des informations sur les infrastructures critiques protégées (PCII), ont été consultées ou dévoilées.</td>
</tr>
<tr class="even">
<td align="left">Perte d’intégrité</td>
<td align="left">Des informations sensibles ou confidentielles ont été modifiées ou supprimées.</td>
</tr>
</tbody>
</table>

L’équipe de réponse de sécurité collabore avec des ingénieurs de sécurité Microsoft Azure et des experts techniques pour classer l’événement en fonction des données factuelles des éléments de preuve. Un événement de sécurité peut-être classé de la façon suivante :

-   **Faux positif :** un événement qui répond aux critères de détection mais qui fait partie d’une pratique d’entreprise normale et nécessite peut-être d’être filtré. L’équipe de service identifiera la cause première des faux positifs et les résoudra de manière systématique en tirant parti des sources de détection et en les ajustant<span id="_Toc350859432" class="anchor"></span> en fonction des besoins.

-   **Incident de sécurité :** un incident provoqué par un accès non autorisé à des données client ou à des données du support stockées sur un équipement de Microsoft ou dans des installations de Microsoft, ou tout accès non autorisé à ces équipement ou installations provoquant la perte, divulgation ou altération des données client ou des données de support.

-   **Incident de sécurité déclarable au client :** un accès illégal ou non autorisé ou une utilisation illégale ou non autorisée de systèmes, équipements ou installations Microsoft provoquant la divulgation, modification ou perte de données client.

-   **Violation de la confidentialité :** un sous-type d’incident de sécurité impliquant des données personnelles. La gestion des procédures ne sont pas différentes d’un incident de sécurité.

Pour déclarer les CRSI (Incident de sécurité déclarable au client), Microsoft doit déterminer qu’un accès non autorisé aux données client a eu lieu ou a très probablement eu lieu et/ou qu’il existe un engagement juridique ou contractuel qu’une notification doit se produire. Il est souhaitable, mais pas obligatoire, que l’impact du client spécifique, l’accès aux ressources et les étapes de réparation soient connus. Un incident est généralement déclaré comme un CRSI après la conclusion de l’étape de diagnostic d’un incident de sécurité ; toutefois, la déclaration peut se produire à tout moment où toutes les informations pertinentes sont disponibles. Le gestionnaire des incidents de sécurité doit établir des preuves au-delà de tout doute raisonnable qu’un événement déclarable s’est produit pour commencer l’exécution du processus de notification d’un incident client.

Tout au long de l’enquête, l’équipe de réponse de sécurité collabore étroitement avec des conseillers juridiques pour vérifier que l’enquête judiciaire est menée conformément aux obligations juridiques et aux engagements vis-à-vis des clients. Il existe également des restrictions importantes sur la gestion et l’affichage des données client et système dans différents environnements d’exploitation. Les données sensibles ou confidentielles, ainsi que les données client, ne sont pas transférées en dehors de l’environnement de production sans l’approbation écrite explicite du gestionnaire des incidents enregistrée dans le ticket des incidents correspondant.

Microsoft vérifie que le risque du client et de l’entreprise est maîtrisé et que les mesures correctives sont mises en œuvre. Si nécessaire, des plans d’urgence et d’atténuation visant à résoudre les risques de sécurité immédiats sont mis en œuvre.

Microsoft effectue aussi un post-mortem interne pour les violations de données. Dans le cadre de cet exercice, le niveau suffisant de réponse et les procédures d’exploitation sont évaluées, et les mises à jour pouvant être nécessaires à la procédure d’exploitation standard de la réponse aux incidents de sécurité ou les processus connexes sont identifiés et mis en œuvre. Les post-mortems internes pour les violations de données sont des enregistrements hautement confidentiels qui ne sont pas accessibles aux clients. Les post-mortems peuvent toutefois être synthétisés et inclus dans d’autres notifications d’événement client. Ces rapports sont fournis aux auditeurs externes pour révision, dans le cadre du cycle d’audit de routine d’Azure.

#### <a name="customer-notification"></a>Notification du client
---------------------

Microsoft Azure avertit les clients et les autorités réglementaires en cas de violations des données, le cas échéant. Microsoft se base sur une compartimentalisation interne importante dans l’exploitation d’Azure. Les journaux de flux de données sont également puissants. Cette conception présente des avantages car la plupart des incidents peuvent être limités à des clients spécifiques. L’objectif consiste à fournir aux clients concernés une notification précise et exploitable en temps voulu dès qu’il y a violation de leurs données.

Après la déclaration d’un CRSI, le processus de notification a lieu aussi rapidement que possible, en sachant que les risques de sécurité se déplacent rapidement. Généralement, le processus d’élaboration des notifications a lieu alors que l’analyse de l’incident est en cours. Les notifications client sont envoyées au plus tard 72 heures après la déclaration d’une violation *sauf* dans les cas suivants :

-   Microsoft estime que le fait d’exécuter une notification augmentera le risque pour d’autres clients. Par exemple, la notification peut avertir un adversaire, empêchant ainsi de résoudre le problème.

-   D’autres circonstances inhabituelles ou extrêmes examinées par le service juridique Corporate External and Legal Affairs (CELA) de Microsoft et le gestionnaire exécutif des incidents.

Microsoft Azure fournit aux clients des informations détaillées leur permettant d’effectuer des enquêtes internes et de répondre aux engagements des utilisateurs finaux, sans retarder le processus de notification de façon excessive.

La notification d’une violation des données personnelles est envoyée au client par un moyen sélectionné par Microsoft, y compris par e-mail. La notification d’une violation des données est envoyée à la liste des contacts de sécurité fournie dans le centre de sécurité Azure, qui peut être configurée en suivant les [instructions d’implémentation](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details). Si les informations de contact ne sont pas fournies dans le centre de sécurité Azure, la notification est envoyée à un ou plusieurs administrateurs d’un abonnement Azure. Pour garantir l’envoi correct de la notification, le client doit vérifier que les informations de contact d’administration sur chaque abonnement concerné et portail de services en ligne sont correctes.

L’équipe Microsoft Azure ou Azure Government peut également choisir d’informer d’autres membres du personnel Microsoft (par exemple, le service client et le gestionnaire de compte du client ou le gestionnaire de compte technique). Ces personnes ont souvent des relations étroites avec le client et peuvent permettre une résolution plus rapide des problèmes<span id="_Appendix_A" class="anchor"></span>

#### <a name="microsoft-intune-data-breach"></a>Violation des données Microsoft InTune
----------------------------

Microsoft Intune est un composant clé de l’offre de service cloud de la suite Microsoft Enterprise Mobility + Security. Pour prendre en charge la stratégie de gouvernance des données, tous les services de cloud computing Microsoft sont développés avec les méthodologies Microsoft de confidentialité et sécurité par conception et de confidentialité et sécurité par défaut.

Ainsi, l’offre de service cloud de Microsoft Intune suit les mêmes mesures organisationnelles et techniques que celles prises par les équipes de service de Microsoft Azure contre les processus de violation des données. Par conséquent, les informations présentées dans le document de notification « Violation des données Microsoft Azure » ici sont analogues au service Microsoft Intune. Par exemple, Microsoft Intune a le même processus de réponse aux incidents de sécurité et cycle de vie (de l’Étape 1 : Détecter à l’étape 5<strong> :</strong> Fermer et post-mortem) mais aussi le même processus de notification des incidents de sécurité au client. Par ailleurs, Microsoft Intune répond également à ses obligations en matière de notification d’une violation des données pour les clients Microsoft O365 utilisant Intune en collaborant directement avec l’équipe de Microsoft O365.

Pour plus d’informations sur la façon dont Microsoft détecte et répond à une violation des données personnelles, reportez-vous à l’article [Notification des violations de données en vertu du RGPD](https://servicetrust.microsoft.com/ViewPage/GDPRBreach) dans le portail d’approbation de services.


#### <a name="learn-more"></a>En savoir plus
[Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/TrustCenter/Privacy/gdpr/default.aspx)
