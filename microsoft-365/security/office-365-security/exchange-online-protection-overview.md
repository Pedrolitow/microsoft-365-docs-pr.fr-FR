---
title: Exchange Online Protection vue d’ensemble (EOP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 09/18/2020
audience: ITPro
ms.topic: overview
localization_priority: Normal
ms.assetid: 1270a65f-ddc3-4430-b500-4d3a481efb1e
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment Exchange Online Protection (EOP) peut vous aider à protéger votre organisation de messagerie sur site dans des environnements autonomes et hybrides.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a925b251ff79aec5acaa0b2c1da2aee3f5a6d70d
ms.sourcegitcommit: 3d30ec03628870a22c54b6ec5d865cbe94f34245
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2021
ms.locfileid: "52930162"
---
# <a name="exchange-online-protection-overview"></a>Vue d’ensemble d’Exchange Online Protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) est le service de filtrage informatique qui protège votre organisation contre le courrier indésirable, les programmes malveillants et d’autres menaces de courrier électronique. EOP est inclus dans toutes les organisations Microsoft 365 avec Exchange Online boîtes aux lettres.

> [!NOTE]
> EOP est également disponible seul pour protéger les boîtes aux lettres sur site et dans les environnements hybrides afin de protéger les boîtes aux lettres Exchange sur site. Pour plus d’informations, [voir Exchange Online Protection](/exchange/standalone-eop/standalone-eop).

Les étapes de la mise en place des fonctionnalités de sécurité EOP et une comparaison avec la sécurité ajoutée que vous obtenez dans Microsoft Defender pour Office 365, voir protéger contre [les menaces](protect-against-threats.md). Les paramètres recommandés pour les fonctionnalités EOP sont disponibles dans les [paramètres recommandés](recommended-settings-for-eop-and-office365.md)pour EOP et Microsoft Defender pour Office 365 sécurité.

Le reste de cet article explique le fonctionnement d’EOP et les fonctionnalités disponibles dans EOP.

## <a name="how-eop-works"></a>Fonctionnement d'EOP

Pour comprendre le fonctionnement d'EOP, il est utile devoir comment le courrier entrant est traité :

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="Graphique du courrier électronique provenant d’Internet ou des commentaires des clients passant dans EOP et via la connexion, la protection contre les programmes malveillants, le filtrage des règles de flux de messagerie et la stratégie de contenu, avant le verdict de courrier indésirable ou de mise en quarantaine, ou la remise du courrier de l’utilisateur final.":::

1. Lorsqu’un message entrant entre dans EOP, il passe initialement par le filtrage des connexions, qui vérifie la réputation de l’expéditeur. La majorité du courrier indésirable est arrêté à ce stade et rejeté par EOP. Pour plus d’informations, consultez [Configuration du filtrage des connexions](configure-the-connection-filter-policy.md).

2. Le message est ensuite inspecté à la recherche de programmes malveillants. Si un programme malveillant est détecté dans le message ou la ou les pièces jointes, le message est acheminé vers une mise en quarantaine de l’administrateur uniquement. Pour en savoir plus sur la protection contre les programmes malveillants, consultez la [protection contre les programmes malveillants dans EOP.](anti-malware-protection.md)

3. Le message continue par le filtrage des stratégies, où il est évalué par rapport aux règles de flux de messagerie (également appelées règles de transport) que vous avez créées. Par exemple, une règle peut envoyer une notification à un responsable lorsqu’un message arrive d’un expéditeur spécifique.

   Dans une organisation sur site avec Exchange Enterprise licences d’accès aux données avec licences Services, les vérifications de protection contre la perte de données [(DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) dans EOP se produisent également à ce stade.

4. Le message passe par le filtrage de contenu (anti-courrier indésirable et anti-usurpation) dans lequel les messages dangereux sont identifiés comme courrier indésirable, courrier indésirable à niveau de confiance élevé, hameçonnage, hameçonnage à haut niveau de confiance, ou en bloc (stratégies anti-courrier indésirable) ou usurpation d’adresse (paramètres d’usurpation dans les stratégies anti-hameçonnage). Vous pouvez configurer l’action à prendre sur le message en fonction du verdict de filtrage (mise en quarantaine, déplacement vers le dossier Courrier indésirable, etc.). Pour plus d’informations, voir [Configure anti-spam policies](configure-your-spam-filter-policies.md) and [Configure anti-phishing policies in EOP](configure-anti-phishing-policies-eop.md).

Un message qui transmet correctement toutes ces couches de protection est remis aux destinataires.

Pour plus d’informations, voir [Ordre et priorité de la protection de la messagerie.](how-policies-and-protections-are-combined.md)

### <a name="eop-datacenters"></a>Centres de données EOP

EOP s’exécute sur un réseau mondial de centres de données conçus pour offrir une disponibilité optimale. Par exemple, si un centre de données devient indisponible, les courriers électroniques sont automatiquement routés vers un autre centre de données sans interruption du service. Les serveurs de chaque centre de données acceptent des messages en votre nom, ce qui fournit une couche de séparation entre votre organisation et Internet, réduisant ainsi la charge sur vos serveurs. Grâce à ce réseau à haut niveau de disponibilité, Microsoft peut garantir que le courrier atteint votre organisation en temps opportun.

EOP effectue l'équilibrage de charge entre les centres de données, mais uniquement au sein d'une région. Si votre système est mis en service dans une région, tous vos messages seront traités sur la base du routage de courrier propre à cette région. La liste suivante présente le fonctionnement du routage de courrier régional pour les centres de données EOP :

- En Europe, au Moyen-Orient et en Afrique (région EMEA), toutes les boîtes aux lettres Exchange Online sont situées dans des centres de données EMEA et tous les messages sont routés via des centres de données EMEA pour le filtrage EOP.
- Dans Asia-Pacific (APAC), toutes les boîtes aux lettres Exchange Online sont situées dans des centres de données APAC et les messages sont actuellement acheminés via des centres de données APAC pour le filtrage EOP.
- En Amérique, les services sont distribués aux emplacements suivants :
  - Amérique du Sud : Exchange Online boîtes aux lettres sont situées dans des centres de données au Brésil et au Chili. Tous les messages sont acheminés via des centres de données locaux pour le filtrage EOP. Les messages mis en quarantaine sont stockés dans le centre de données où se trouve le client.
  - Canada : Exchange Online boîtes aux lettres sont situées dans des centres de données au Canada. Tous les messages sont acheminés via des centres de données locaux pour le filtrage EOP. Les messages mis en quarantaine sont stockés dans le centre de données où se trouve le client.
  - États-Unis : Exchange Online boîtes aux lettres sont situées dans des centres de données américains. Tous les messages sont acheminés via des centres de données locaux pour le filtrage EOP. Les messages mis en quarantaine sont stockés dans le centre de données où se trouve le client.
- En ce qui concerne le nuage communautaire propre aux gouvernements (CCG), toutes les boîtes aux lettres Exchange Online sont situées dans des centres de données américains et tous les messages sont routés via ces centres de données pour le filtrage EOP.

### <a name="eop-features"></a>Fonctionnalités EOP

Cette section fournit une vue d’ensemble des principales fonctionnalités disponibles dans EOP.

Pour plus d’informations sur les exigences, les limites importantes et la disponibilité des fonctionnalités dans tous les plans d’abonnement EOP, voir la [description Exchange Online Protection service.](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)

**Remarques** :

- EOP utilise plusieurs listes rouges d'URL qui permettent de détecter les liens malveillants connus au sein des messages.
- EOP utilise une vaste liste de domaines connus pour envoyer du courrier indésirable.
- EOP utilise plusieurs moteurs anti-programme malveillant pour protéger automatiquement nos clients en permanence.
- EOP inspecte la charge utile active dans le corps du message et toutes les pièces jointes des messages à la recherche de programmes malveillants.
- Pour obtenir les valeurs recommandées pour les stratégies de protection, voir [Paramètres recommandés](recommended-settings-for-eop-and-office365.md)pour EOP et Microsoft Defender pour Office 365 sécurité.
- Pour obtenir des instructions rapides sur la configuration des stratégies de protection, voir [Protéger contre les menaces.](protect-against-threats.md)

<br>

****
|Fonctionnalité|Commentaires|
|---|---|
|**Protection**||
|Anti-programme malveillant|[Protection contre les programmes malveillants dans EOP](anti-malware-protection.md) <p> [Forum Aux Questions sur la protection contre les programmes malveillants](anti-malware-protection-faq-eop.yml) <p> [Configurer des stratégies anti-programme malveillant dans EOP](configure-anti-malware-policies.md)|
|Courrier indésirable entrant|[Protection contre le courrier indésirable dans EOP](anti-spam-protection.md) <p> [Forum Aux Questions sur la protection anti-courrier indésirable](anti-spam-protection-faq.yml) <p> [Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)|
|Courrier indésirable sortant|[Protection contre le courrier indésirable sortant dans EOP](outbound-spam-controls.md) <p> [Configurer le filtrage du courrier indésirable sortant dans EOP](configure-the-outbound-spam-policy.md) <p> [Contrôler le forwarding automatique du courrier externe dans Microsoft 365](external-email-forwarding.md)|
|Filtrage des connexions|[Configuration du filtrage des connexions](configure-the-connection-filter-policy.md)|
|Anti-hameçonnage|[Stratégies anti-hameçonnage dans Microsoft 365](set-up-anti-phishing-policies.md) <p> [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)|
|Protection contre l’usurpation d’identité|[Informations sur l’intelligence contre l’usurpation d’adresse dans EOP](learn-about-spoof-intelligence.md) <p> [Gérer la liste Autoriser/Bloquer du client](tenant-allow-block-list.md)|
|Purge automatique sans heure (ZAP) pour les programmes malveillants, le courrier indésirable et les messages de hameçonnage remis|[ZAP dans Exchange Online](zero-hour-auto-purge.md)|
|Stratégies de sécurité prédéfinies|[Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md) <p> [Analyseur de configuration des stratégies de protection dans EOP et Microsoft Defender pour Office 365](configuration-analyzer-for-security-policies.md)|
|Liste d’locataires autoriser/bloquer|[Gérer la liste Autoriser/Bloquer du client](tenant-allow-block-list.md)|
|Listes de blocage pour les expéditeurs de messages|[Créer des listes d’expéditeurs bloqués dans EOP](create-block-sender-lists-in-office-365.md)|
|Autoriser les listes pour les expéditeurs de messages|[Créer des listes d’expéditeurs sûrs dans EOP](create-safe-sender-lists-in-office-365.md)|
|Directory Based Edge Blocking (DBEB)|[Utiliser le blocage du périmètre basé sur l'annuaire pour rejeter les messages envoyés à des destinataires non valides](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**Mise en quarantaine et soumissions**||
|Envoi de l’administrateur|[Utiliser la soumission d’administrateur pour soumettre des courriers indésirables, du hameçonnage, des URL et des fichiers suspectés à Microsoft](admin-submission.md)|
|Envois d’utilisateurs (boîte aux lettres personnalisée)|[Stratégie de soumissions d’utilisateurs](user-submission.md)|
|Quarantaine : administrateurs|[Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Exchange Online PowerShell](manage-quarantined-messages-and-files.md) <p> [FAQ sur les messages mis en quarantaine](quarantine-faq.yml) <p> [Signaler les messages et fichiers à Microsoft](report-junk-email-messages-to-microsoft.md) <p> [En-têtes de message anti-courrier indésirable dans Microsoft 365](anti-spam-message-headers.md) <p> Vous pouvez analyser les en-têtes de message des messages mis en quarantaine à l’aide de l’analyseur [d’en-tête de message sur](https://mha.azurewebsites.net/).|
|Quarantaine : utilisateurs finaux|[Rechercher et publier des messages mis en quarantaine en tant qu’utilisateur dans Exchange Online PowerShell](find-and-release-quarantined-messages-as-a-user.md) <p> [Utiliser les notifications de courrier indésirable de l’utilisateur pour libérer et signaler les messages mis en quarantaine](use-spam-notifications-to-release-and-report-quarantined-messages.md)|
|**Flux de messagerie**||
|Règles de flux de messagerie|[Règles de flux de messagerie (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [Conditions de règle de flux de messagerie et exceptions (prédicats) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [Actions de règle de flux de courrier dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [Gérer les règles de flux de messagerie dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [Procédures de règle de flux de messagerie Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|Domaines acceptés|[Gestion des domaines acceptés dans Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|Connecteurs|[Configurer le flux de messagerie à l’aide de connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|Filtrage amélioré pour les connecteurs|[Filtrage amélioré pour les connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**Analyse**||
|Suivi des messages|[Suivi des messages](message-trace-scc.md) <p> [Suivi des messages dans le centre d Exchange’administration de l’utilisateur](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|Envoyer des & rapports de collaboration|[Afficher les rapports sur la sécurité des e-mails](view-email-security-reports.md)|
|Rapports de flux de messagerie|[Afficher les rapports sur les flux de courrier](view-mail-flow-reports.md) <p> [Rapports de flux de messagerie dans le centre d Exchange’administration de l’utilisateur](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|Informations sur le flux de messagerie|[Informations sur le flux de messagerie](mail-flow-insights-v2.md) <p> [Informations sur le flux de messagerie dans le centre d Exchange’administration de l’utilisateur](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|Rapports d’audit|[Rapports d’audit dans le centre d Exchange’administration de l’utilisateur](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|Stratégies d’alerte|[Stratégies d’alerte](../../compliance/alert-policies.md)|
|**Contrats de niveau de service (SLA) et prise en charge**||
|SLA d'efficacité de courrier électronique|\> 99%|
|SLA de rapport de faux positif|\< 1:250,000|
|SLA de détection et de blocage de virus|100 % des virus connus|
|SLA de disponibilité mensuelle|99,999 %|
|Support technique par téléphone ou par Internet 24 heures sur 24, 7 jours sur 7|[Aide et support pour EOP](help-and-support-for-eop.md).|
|**Autres fonctionnalités**||
|Réseau de serveurs mondial géo-redondant|EOP s'exécute sur un réseau mondial de centres de données conçus pour contribuer à offrir une disponibilité optimale. Pour plus d’informations, consultez la section des centres de données [EOP](#eop-datacenters) plus tôt dans cet article.|
|Mise en file d'attente du message lorsque le serveur local ne peut pas accepter le courrier|Les messages en attente restent dans nos files d’attente pendant un jour. Les nouvelles tentatives d'envoi de message sont basées sur les erreurs que nous recevons à partir du système de messagerie du destinataire. En moyenne, les messages sont renvoyés toutes les 5 minutes. Pour plus d'informations, voir [Questions fréquemment posées sur les messages mis en file d'attente, différés et retournés dans EOP](eop-queued-deferred-and-bounced-messages-faq.yml).|
|chiffrement de messages Office 365 disponible en tant qu’modules|Pour plus d'informations, voir [Chiffrement dans Office 365](../../compliance/encryption.md).|
|||
