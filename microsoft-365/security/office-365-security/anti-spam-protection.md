---
title: Protection anti-courrier indésirable
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les paramètres et filtres anti-courrier indésirable qui contribuent à empêcher le courrier indésirable dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1bc5d81b1221b73bcb701345b8db2f160380ba37
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60657112"
---
# <a name="anti-spam-protection-in-eop"></a>Protection contre le courrier indésirable dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

> [!NOTE]
> Cette rubrique est destinée aux administrateurs. Pour les rubriques de l’utilisateur final, voir [Vue d’ensemble](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089) du filtre de courrier indésirable et en savoir plus sur le courrier indésirable [et le hameçonnage.](https://support.microsoft.com/office/86c1d76f-4d5a-4967-9647-35665dc17c31)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, les messages électroniques sont automatiquement protégés contre le courrier indésirable (courrier indésirable) par EOP.

La feuille de route sécurité de messagerie de Microsoft implique une approche inter-produits sans correspondance. La technologie anti-courrier indésirable et anti-hameçonnage EOP est appliquée sur nos plateformes de messagerie pour fournir aux utilisateurs les derniers outils et innovations anti-courrier indésirable et anti-hameçonnage sur l’ensemble du réseau. L'objectif d'EOP est de proposer un service de messagerie complet et utilisable qui vous aide à détecter le courrier indésirable, les menaces d'e-mails frauduleux (hameçonnage) et les logiciels malveillants, et de protéger les utilisateurs.

Au fur et à mesure que la messagerie électronique prend de l'importance, la mauvaise utilisation qui en est faite aussi. Le courrier indésirable non surveillé peut surcharger les boîtes de réception et les réseaux, affecter la satisfaction des utilisateurs et entraver l'efficacité des communications d'e-mails légitimes. C'est pourquoi Microsoft continue à investir dans les technologies anti-spam. En bref, cela commence par la détection et le filtrage du courrier indésirable.

> [!TIP]
> Les technologies anti-courrier indésirable suivantes sont utiles lorsque vous souhaitez autoriser ou bloquer des messages en fonction de l’enveloppe de message (par exemple, le domaine de l’expéditeur ou l’adresse IP source du message). Pour autoriser ou bloquer les messages en fonction de la charge utile (par exemple, les URL dans le message ou les fichiers joints), vous devez utiliser le portail De listes d’adresses client [autoriser/bloquer](tenant-allow-block-list.md).

## <a name="anti-spam-technologies-in-eop"></a>Technologies anti-courrier indésirable dans EOP

Pour réduire le courrier indésirable, EOP inclut une protection contre le courrier indésirable qui utilise des technologies propriétaires de filtrage du courrier indésirable pour identifier et séparer le courrier indésirable du courrier légitime. Le filtrage du courrier indésirable EOP apprend les menaces connues de courrier indésirable et de hameçonnage, ainsi que les commentaires des utilisateurs de notre plateforme grand public, Outlook.com. Les commentaires continus des utilisateurs EOP dans le cadre du programme de classification du courrier indésirable permettent de s’assurer que les technologies EOP sont continuellement formées et améliorées.

Les paramètres anti-courrier indésirable dans EOP sont composés des technologies suivantes :

- Filtrage des connexions : identifie les serveurs de sources de courriers électroniques bons et non fiables au début de la connexion de messagerie entrante via la liste d’adresses IP permises, la liste d’adresses IP bloqués et la liste fiable *(liste* dynamique mais non modifiable d’expéditeurs fiables conservée par Microsoft). Vous configurez ces paramètres dans la stratégie de filtrage des connexions. Pour plus d’informations, [plus d’informations sur la configuration du filtrage des connexions.](configure-the-connection-filter-policy.md)

- Filtrage du courrier  indésirable (filtrage du **contenu)**: EOP utilise les verdicts de filtrage du courrier indésirable spam, courrier indésirable à niveau de confiance élevé, courrier électronique en masse, courrier de hameçonnage et e-mail de hameçonnage à haut niveau de confiance pour classer les messages.     Vous pouvez configurer les actions à prendre en fonction de ces verdicts, et vous pouvez configurer ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine et si l’utilisateur reçoit des notifications de mise en quarantaine à l’aide de stratégies de mise en [quarantaine.](quarantine-policies.md) Pour plus d’informations, voir [Configurer des stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

  > [!NOTE]
  > Par défaut, le filtrage du courrier indésirable est configuré pour envoyer des messages marqués comme courrier indésirable dans le dossier Courrier indésirable du destinataire. Toutefois, dans les environnements hybrides où EOP protège les boîtes aux lettres Exchange sur site, vous devez configurer deux règles de flux de messagerie (également appelées règles de transport) dans votre organisation Exchange sur site pour reconnaître les en-têtes de courrier indésirable EOP ajoutés aux messages. Pour les détails, voir [Configurer Exchange Online Protection (EOP) pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- **Filtrage du** courrier indésirable sortant : EOP vérifie également que vos utilisateurs n’envoient pas de courrier indésirable, que ce soit dans le contenu des messages sortants ou en dépassant les limites des messages sortants. Pour plus d’informations, [voir Configurer le filtrage](configure-the-outbound-spam-policy.md)du courrier indésirable sortant dans Microsoft 365 .

- **Veille contre l’usurpation** d’adresse : pour plus d’informations, voir Protection contre l’usurpation [d’adresse dans EOP.](anti-spoofing-protection.md)

## <a name="manage-errors-in-spam-filtering"></a>Gérer les erreurs de filtrage du courrier indésirable

Il est possible que les messages de qualité soient identifiés comme courrier indésirable (également appelé faux positifs) ou qu’ils soient remis à la boîte de réception (également appelée faux négatifs). Vous pouvez utiliser les suggestions des sections suivantes pour découvrir ce qui s’est passé et éviter qu’il ne se produise à l’avenir.

Voici quelques meilleures pratiques qui s’appliquent à l’un ou l’autre scénario :

- Signalez toujours les messages mal classés à Microsoft. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- **Examinez les en-têtes de message anti-courrier** indésirable : ces valeurs vous indiquent pourquoi un message a été marqué comme courrier indésirable ou pourquoi il a ignoré le filtrage du courrier indésirable. Pour plus d’informations, consultez [les en-têtes de message anti-courrier indésirable.](anti-spam-message-headers.md)

- **Pointez votre enregistrement MX** sur Microsoft 365 : pour qu’EOP offre la meilleure protection possible, nous vous recommandons de remettre d’abord les messages Microsoft 365' Pour obtenir des instructions, voir Créer des enregistrements DNS chez un fournisseur [d’hébergement DNS Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

  Si l’enregistrement MX pointe vers un autre emplacement (par exemple, une solution ou un dispositif anti-courrier indésirable tiers), il est difficile pour EOP de fournir un filtrage précis du courrier indésirable. Dans ce scénario, vous devez configurer le filtrage amélioré pour les connecteurs (également appelé ignorer la _liste)._ Pour obtenir des instructions, voir [Filtrage amélioré pour les connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- **Utiliser l’authentification** de messagerie : si vous possédez un domaine de messagerie, vous pouvez utiliser DNS pour vous assurer que les messages provenant d’expéditeurs de ce domaine sont légitimes. Pour éviter le courrier indésirable et l’usurpation d’identité indésirable dans EOP, utilisez toutes les méthodes d’authentification de courrier électronique suivantes :

  - **SPF**: Sender Policy Framework vérifie l’adresse IP source du message par rapport au propriétaire du domaine d’envoi. Pour une présentation rapide de SPF et pour le configurer rapidement, voir Configurer SPF pour éviter [l’usurpation d’accès.](set-up-spf-in-office-365-to-help-prevent-spoofing.md) Pour consulter des informations plus approfondies sur l’utilisation de SPF par Microsoft 365, la résolution des problèmes et les déploiements non standard tels que les déploiements hybrides, voir [Comment Microsoft 365 utilise SPF (Sender Policy Framework) pour empêcher l’usurpation d’identité](how-office-365-uses-spf-to-prevent-spoofing.md).

  - **DKIM**: DomainKeys Identified Mail ajoute une signature numérique à l’en-tête de message des messages envoyés à partir de votre domaine. Pour plus d’informations, [voir Utiliser DKIM pour valider](use-dkim-to-validate-outbound-email.md)les messages sortants envoyés à partir de votre domaine personnalisé dans Microsoft 365 .

  - **DMARC**: l’authentification, la signalement et la conformité des messages basés sur un domaine aident les systèmes de messagerie de destination à déterminer ce qu’ils doivent faire avec les messages qui échouent aux vérifications SPF ou DKIM et offrent un autre niveau de confiance à vos partenaires de messagerie. Pour plus d’informations, [voir Utiliser DMARC pour valider le courrier électronique Microsoft 365](use-dmarc-to-validate-email.md).

- Vérifiez vos **paramètres** de courrier en nombre : le seuil BCL (Bulk Complaint Level) que vous configurez dans les stratégies anti-courrier indésirable détermine si les messages électroniques en nombre (également appelés messages _gris)_ sont marqués comme courrier indésirable. Le paramètre PowerShell uniquement _MarkAsSpamBulkMail_ qui est sur par défaut contribue également aux résultats. Pour plus d’informations, voir [Configurer des stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="prevent-the-delivery-of-spam-to-the-inbox"></a>Empêcher la remise de courrier indésirable à la boîte de réception

- Vérifiez les **paramètres** de votre organisation : surveillez les paramètres qui permettent aux messages d’ignorer le filtrage du courrier indésirable (par exemple, si vous ajoutez votre propre domaine à la liste des domaines autorisés dans les stratégies anti-courrier indésirable). Pour nos paramètres recommandés, voir [Paramètres recommandés](recommended-settings-for-eop-and-office365.md) pour EOP et Microsoft Defender pour la sécurité Office 365 et créer des listes d’expéditeurs [sûrs.](create-safe-sender-lists-in-office-365.md)

- **Utilisez les listes d’expéditeurs bloqués disponibles**: pour plus d’informations, voir Créer des [listes d’expéditeurs bloqués.](create-block-sender-lists-in-office-365.md)

- **Se désabonner du courrier électronique en masse** Si l’utilisateur s’est inscrit au message (bulletins d’informations, annonces de produits, etc.) et qu’il contient un lien de désabonnement provenant d’une source digne de confiance, demandez-lui simplement de se désabonner.

- **EOP** autonome : créez des règles de flux de messagerie dans les Exchange locaux pour les verdicts de filtrage du courrier indésirable EOP : dans les environnements hybrides où EOP protège les boîtes aux lettres Exchange sur site, vous devez configurer des règles de flux de messagerie (également appelées règles de transport) dans des Exchange locaux. Ces règles de flux de messagerie traduisent le verdict de filtrage du courrier indésirable EOP afin que la règle de courrier indésirable de la boîte aux lettres puisse déplacer le message vers le dossier Courrier indésirable. Pour les détails, voir [Configurer Exchange Online Protection (EOP) pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

### <a name="prevent-good-email-from-being-identified-as-spam"></a>Empêcher l’identification de courriers électroniques de qualité comme courrier indésirable

Voici quelques étapes que vous pouvez suivre pour éviter les faux positifs :

- **Vérifiez les paramètres de filtrage du courrier Outlook courrier indésirable de l’utilisateur**:

  - Vérifiez que le filtre **de** courrier indésirable Outlook est désactivé : lorsque le filtre de courrier indésirable Outlook est définie sur la valeur par défaut Aucun filtrage **automatique,** Outlook ne tente pas de classer les messages comme courrier indésirable.  Lorsqu’il est  réglé sur Faible ou **Élevé,** le filtre de courrier indésirable Outlook utilise sa propre technologie de filtrage SmartScreen pour identifier et déplacer le courrier indésirable vers le dossier Courrier indésirable, afin que vous receviez des faux positifs. Notez que Microsoft a cessé de produire des mises à jour des définitions de courrier indésirable pour les filtres SmartScreen Exchange et Outlook en novembre 2016. Les définitions de courrier indésirable SmartScreen existantes ont été laissées en place, mais leur efficacité se dégradera probablement au fil du temps.

  - Vérifiez que le paramètre **Outlook**« listes Coffre uniquement » est désactivé : lorsque ce paramètre est activé, seuls les messages provenant d’expéditeurs de la liste des expéditeurs Coffre ou de la liste des destinataires Coffre de l’utilisateur sont remis dans la boîte de réception . Les messages provenant de tous les autres utilisateurs sont automatiquement déplacés vers le dossier Courrier indésirable.

  Pour plus d’informations sur ces paramètres, voir [Configure junk email settings on Exchange Online mailboxes in Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Utilisez les listes d’expéditeurs sûrs disponibles**: pour plus d’informations, voir [Créer des listes d’expéditeurs sûrs.](create-safe-sender-lists-in-office-365.md)

- **Vérifiez que les utilisateurs sont dans les limites** d’envoi et de réception, comme décrit dans les [limites](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits) de réception et d’envoi dans la description Exchange Online service.

- **EOP** autonome : utilisez la synchronisation d’annuaires : si vous utilisez EOP autonome pour protéger votre organisation Exchange sur site, vous devez synchroniser les paramètres utilisateur avec le service à l’aide de la synchronisation d’annuaires. Ainsi, vos listes d’expéditeurs approuvés par les utilisateurs sont respectées par EOP. Pour plus d’informations, voir [Utilisation de la synchronisation d’annuaires pour gérer les utilisateurs de messagerie](/exchange/standalone-eop/manage-mail-users-in-eop#synchronize-directories-with-azure-active-directory-connect-aad-connect).

## <a name="anti-spam-legislation"></a>Législation anti-courrier indésirable

Chez Microsoft, nous pensons que l'évolution de nouvelles technologies et de l'auto-réglementation requiert la prise en charge de cadres juridiques et d'une politique gouvernementale efficaces. La prolifération du courrier indésirable dans le monde a poussé de nombreux organes législatifs à réglementer les e-mails commerciaux. De nombreux pays ont désormais des lois de lutte contre le courrier indésirable en place. Aux États-Unis, des lois au niveau fédéral et au niveau de l'État régissent le courrier indésirable, et cette approche complémentaire contribue à réduire le courrier indésirable tout en permettant au commerce électronique légitime de prospérer. Le CAN-SPAM Act développe les outils disponibles pour limiter les messages électroniques frauduleux et trompeurs.
