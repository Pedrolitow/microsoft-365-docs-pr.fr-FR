---
title: Vue d’ensemble de Exchange Online Protection (EOP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 09/18/2020
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 1270a65f-ddc3-4430-b500-4d3a481efb1e
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment Exchange Online Protection (EOP) peut aider à protéger votre organisation de messagerie locale dans des environnements autonomes et hybrides.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 90d0e4293a08b77347aace9098cc9c65851a4cab
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67388460"
---
# <a name="exchange-online-protection-overview"></a>Vue d’ensemble d’Exchange Online Protection

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) est le service de filtrage basé sur le cloud qui protège votre organisation contre le courrier indésirable, les programmes malveillants et d’autres menaces de courrier électronique. EOP est inclus dans toutes les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online.

> [!NOTE]
> EOP est également disponible en soi pour protéger les boîtes aux lettres locales et dans les environnements hybrides afin de protéger les boîtes aux lettres Exchange locales. Pour plus d’informations, consultez [Exchange Online Protection autonomes](/exchange/standalone-eop/standalone-eop).

Les étapes de configuration des fonctionnalités de sécurité EOP et une comparaison avec la sécurité ajoutée que vous obtenez dans Microsoft Defender pour Office 365, consultez [Protéger contre les menaces](protect-against-threats.md). Les paramètres recommandés pour les fonctionnalités EOP sont [disponibles dans les paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](recommended-settings-for-eop-and-office365.md).

Le reste de cet article explique le fonctionnement d’EOP et les fonctionnalités disponibles dans EOP.

## <a name="how-eop-works"></a>Fonctionnement d'EOP

Pour comprendre le fonctionnement d'EOP, il est utile devoir comment le courrier entrant est traité :

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="Graphique de l’e-mail provenant d’Internet ou de commentaires des clients passant dans EOP et via la connexion, anti-programme malveillant, filtrage de stratégie de barre oblique des règles de flux de courrier et filtrage de contenu, avant le verdict de courrier indésirable ou de mise en quarantaine, ou de remise de courrier de l’utilisateur final" lightbox="../../media/tp_emailprocessingineopt3.png":::

1. Lorsqu’un message entrant entre dans EOP, il passe initialement par le filtrage de connexion, qui vérifie la réputation de l’expéditeur. La majorité du courrier indésirable est arrêtée à ce stade et rejetée par EOP. Pour plus d’informations, consultez [Configuration du filtrage des connexions](configure-the-connection-filter-policy.md).

2. Ensuite, le message est inspecté pour détecter les programmes malveillants. Si un programme malveillant se trouve dans le message ou les pièces jointes, le message est remis en quarantaine. Par défaut, seuls les administrateurs peuvent afficher et interagir avec les messages malveillants mis en quarantaine. Toutefois, les administrateurs peuvent créer et utiliser des [stratégies de quarantaine](quarantine-policies.md) pour spécifier ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine. Pour en savoir plus sur la protection contre les programmes malveillants, consultez [protection contre les programmes malveillants dans EOP](anti-malware-protection.md).

3. Le message continue via le filtrage de stratégie, où il est évalué par rapport aux règles de flux de messagerie (également appelées règles de transport) que vous avez créées. Par exemple, une règle peut envoyer une notification à un responsable lorsqu’un message arrive d’un expéditeur spécifique.

   Dans une organisation locale avec Exchange Enterprise CAL avec licences Services, les contrôles [de protection contre la perte de données (DLP) Microsoft Purview](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) dans EOP se produisent également à ce stade.

4. Le message passe par le filtrage de contenu (anti-courrier indésirable et anti-usurpation d’identité) où les messages dangereux sont identifiés comme courrier indésirable, courrier indésirable à haut niveau de confiance, hameçonnage, hameçonnage à haut niveau de confiance, ou en bloc (stratégies anti-courrier indésirable) ou usurpation d’identité (paramètres d’usurpation d’identité dans les stratégies anti-hameçonnage). Vous pouvez configurer l’action à effectuer sur le message en fonction du verdict de filtrage (mise en quarantaine, déplacement vers le dossier Junk Email, etc.) et de ce que les utilisateurs peuvent faire pour les messages mis en quarantaine à l’aide de [stratégies de quarantaine](quarantine-policies.md). Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md) et configurer des stratégies [anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md).

Un message qui transmet correctement toutes ces couches de protection est remis aux destinataires.

Pour plus d’informations, consultez [Ordre et priorité de la protection par e-mail](how-policies-and-protections-are-combined.md).

### <a name="eop-datacenters"></a>Centres de données EOP

EOP s’exécute sur un réseau mondial de centres de données conçus pour offrir une disponibilité optimale. Par exemple, si un centre de données devient indisponible, les courriers électroniques sont automatiquement routés vers un autre centre de données sans interruption du service. Les serveurs de chaque centre de données acceptent les messages en votre nom, ce qui fournit une couche de séparation entre votre organisation et Internet, réduisant ainsi la charge sur vos serveurs. Grâce à ce réseau à haut niveau de disponibilité, Microsoft peut garantir que le courrier atteint votre organisation en temps opportun.

EOP effectue l'équilibrage de charge entre les centres de données, mais uniquement au sein d'une région. Si vous êtes approvisionné dans une région, tous vos messages sont traités à l’aide du routage de courrier pour cette région.

### <a name="eop-features"></a>Fonctionnalités EOP

Cette section fournit une vue d’ensemble générale des principales fonctionnalités disponibles dans EOP.

Pour plus d’informations sur les exigences, les limites importantes et la disponibilité des fonctionnalités dans tous les plans d’abonnement EOP, consultez la [description du service Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

**Remarques** :

- EOP utilise plusieurs listes rouges d'URL qui permettent de détecter les liens malveillants connus au sein des messages.
- EOP utilise une vaste liste de domaines connus pour envoyer du courrier indésirable.
- EOP utilise plusieurs moteurs anti-programmes malveillants pour protéger automatiquement nos clients en tout temps.
- EOP inspecte la charge utile active dans le corps du message et toutes les pièces jointes de message pour détecter les programmes malveillants.
- Pour connaître les valeurs recommandées pour les stratégies de protection, consultez [Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](recommended-settings-for-eop-and-office365.md).
- Pour obtenir des instructions rapides sur la configuration des stratégies de protection, consultez [Protéger contre les menaces](protect-against-threats.md).

|Fonctionnalité|Comments|
|---|---|
|**Protection**||
|Ant-programme malveillant|[Protection contre les programmes malveillants dans EOP](anti-malware-protection.md) <p> [Forum Aux Questions sur la protection contre les programmes malveillants](anti-malware-protection-faq-eop.yml) <p> [Configurer des stratégies anti-programme malveillant dans EOP](configure-anti-malware-policies.md)|
|Anti-courrier indésirable entrant|[Protection anti-courrier indésirable dans EOP](anti-spam-protection.md) <p> [Forum Aux Questions sur la protection anti-courrier indésirable](anti-spam-protection-faq.yml) <p> [Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
|Anti-courrier indésirable sortant|[Protection contre le courrier indésirable sortant dans EOP](outbound-spam-controls.md) <p> [Configurer le filtrage du courrier indésirable sortant dans EOP](configure-the-outbound-spam-policy.md) <p> [Contrôler le transfert automatique d’e-mails externes dans Microsoft 365](external-email-forwarding.md)|
|Filtrage des connexions|[Configuration du filtrage des connexions](configure-the-connection-filter-policy.md)|
|Anti-hameçonnage|[Stratégies anti-hameçonnage dans Microsoft 365](set-up-anti-phishing-policies.md) <p> [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)|
|Protection contre l’usurpation d’identité|[Informations sur l’intelligence d’usurpation d’identité dans EOP](learn-about-spoof-intelligence.md) <p> [Gérer la liste Autoriser/Bloquer du client](manage-tenant-allow-block-list.md)|
|Vidage automatique de zéro heure (ZAP) pour les programmes malveillants, les courriers indésirables et les messages de hameçonnage remis|[ZAP dans Exchange Online](zero-hour-auto-purge.md)|
|Stratégies de sécurité prédéfinies|[Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md) <p> [Analyseur de configuration pour les stratégies de protection dans EOP et Microsoft Defender pour Office 365](configuration-analyzer-for-security-policies.md)|
|Liste Autoriser/Bloquer du client|[Gérer la liste Autoriser/Bloquer du client](manage-tenant-allow-block-list.md)|
|Listes de blocs pour les expéditeurs de messages|[Créer des listes d’expéditeurs bloqués dans EOP](create-block-sender-lists-in-office-365.md)|
|Autoriser les listes pour les expéditeurs de messages|[Créer des listes d’expéditeurs fiables dans EOP](create-safe-sender-lists-in-office-365.md)|
|Directory Based Edge Blocking (DBEB)|[Utiliser le blocage du périmètre basé sur l'annuaire pour rejeter les messages envoyés à des destinataires non valides](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**Mise en quarantaine et soumissions**||
|soumission Administration|[Utiliser Administration soumission pour envoyer des fichiers suspects de courrier indésirable, de hameçonnage, d’URL et de courrier indésirable à Microsoft](admin-submission.md)|
|Soumissions d’utilisateurs (boîte aux lettres personnalisée)|[Stratégie d’envoi des utilisateurs](user-submission.md)|
|Mise en quarantaine - administrateurs|[Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Exchange Online PowerShell](manage-quarantined-messages-and-files.md) <p> [FAQ sur les messages mis en quarantaine](quarantine-faq.yml) <p> [Signaler les messages et fichiers à Microsoft Corporation](report-junk-email-messages-to-microsoft.md) <p> [En-têtes de message anti-courrier indésirable dans Microsoft 365](anti-spam-message-headers.md) <p> Vous pouvez analyser les en-têtes de messages en quarantaine à l’aide de [l’analyseur d’en-tête de message.](https://mha.azurewebsites.net/)|
|Mise en quarantaine - Utilisateurs finaux|[Rechercher et publier des messages mis en quarantaine en tant qu’utilisateur dans Exchange Online PowerShell](find-and-release-quarantined-messages-as-a-user.md) <p> [Utiliser des notifications de quarantaine pour publier et signaler des messages mis en quarantaine](use-spam-notifications-to-release-and-report-quarantined-messages.md) <p> [Stratégies de mise en quarantaine](quarantine-policies.md)|
|**Flux de messagerie**||
|Règles de flux de messagerie|[Règles de flux de messagerie (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [Conditions de règle de flux de messagerie et exceptions (prédicats) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [Actions de règle de flux de courrier dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [Gérer les règles de flux de messagerie dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [Procédures de règle de flux de messagerie dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|Domaines acceptés|[Gestion des domaines acceptés dans Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|Connecteurs|[Configurer le flux de messagerie à l’aide de connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|Filtrage amélioré pour les connecteurs|[Filtrage amélioré pour les connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**Analyse**||
|Suivi des messages|[Suivi des messages](message-trace-scc.md) <p> [Suivi des messages dans le Centre d’administration Exchange](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|rapports de collaboration Email &|[Afficher les rapports sur la sécurité des e-mails](view-email-security-reports.md)|
|Rapports de flux de courrier|[Afficher les rapports sur les flux de courrier](view-mail-flow-reports.md) <p> [Rapports de flux de courrier dans le Centre d’administration Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|Insights sur le flux de courrier|[Insights sur le flux de courrier](mail-flow-insights-v2.md) <p> [Informations sur les flux de messagerie dans le Centre d’administration Exchange](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|Rapports d’audit|[Audit des rapports dans le Centre d’administration Exchange](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|Stratégies d’alerte|[Stratégies d’alerte](../../compliance/alert-policies.md)|
|**Contrats de niveau de service (SLA) et prise en charge**||
|SLA d'efficacité de courrier électronique|\> 99 %|
|SLA de rapport de faux positif|\< 1:250,000|
|SLA de détection et de blocage de virus|100 % des virus connus|
|SLA de disponibilité mensuelle|99,999 %|
|Support technique par téléphone ou par Internet 24 heures sur 24, 7 jours sur 7|[Aide et support pour EOP](help-and-support-for-eop.md).|
|**Autres fonctionnalités**||
|Réseau de serveurs mondial géo-redondant|EOP s'exécute sur un réseau mondial de centres de données conçus pour contribuer à offrir une disponibilité optimale. Pour plus d’informations, consultez la section Centres de [données EOP](#eop-datacenters) plus haut dans cet article.|
|Mise en file d'attente du message lorsque le serveur local ne peut pas accepter le courrier|Les messages en report restent dans nos files d’attente pendant une journée. Les nouvelles tentatives d'envoi de message sont basées sur les erreurs que nous recevons à partir du système de messagerie du destinataire. En moyenne, les messages sont renvoyés toutes les 5 minutes. Pour plus d'informations, voir [Questions fréquemment posées sur les messages mis en file d'attente, différés et retournés dans EOP](eop-queued-deferred-and-bounced-messages-faq.yml).|
|Office 365 Message Encryption disponible en tant que module complémentaire|Pour plus d'informations, voir [Chiffrement dans Office 365](../../compliance/encryption.md).|
|||
