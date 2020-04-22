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
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
description: Découvrez les paramètres de blocage du courrier indésirable et les filtres qui vous permettront d’éviter le courrier indésirable dans Exchange Online et Microsoft 365. Vous recevez trop de courrier indésirable dans Microsoft 365 ? Vous pouvez personnaliser vos filtres de courrier indésirable et de blocage du courrier indésirable.
ms.openlocfilehash: 3bb1c81af0061cc20b4c7bb2a963c0d06b7914e3
ms.sourcegitcommit: d4d082292dc711a579fe925ad989ea54ec2e27f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "43708570"
---
# <a name="anti-spam-protection-in-microsoft-365"></a>Protection contre le courrier indésirable dans Microsoft 365

> [!NOTE]
> Cette rubrique est destinée aux administrateurs 365 de Microsoft. Pour les rubriques destinées aux utilisateurs finaux, consultez [la rubrique vue d’ensemble du filtre courrier indésirable](https://support.Microsoft.com/article/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089) et [en savoir plus sur le courrier indésirable et le hameçonnage](https://support.Microsoft.com/article/86c1d76f-4d5a-4967-9647-35665dc17c31).

Si vous êtes un client Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection (EOP) autonome sans boîte aux lettres Exchange Online, vos messages électroniques sont automatiquement protégés contre le courrier indésirable (courrier indésirable) par EOP.

La feuille de route sécurité de messagerie de Microsoft implique une approche inter-produits sans correspondance. La technologie de blocage du courrier indésirable et anti-hameçonnage EOP est appliquée sur nos plates-formes de messagerie pour fournir aux utilisateurs les derniers outils de blocage du courrier indésirable et anti-hameçonnage, ainsi que leurs innovations sur le réseau. L'objectif d'EOP est de proposer un service de messagerie complet et utilisable qui vous aide à détecter le courrier indésirable, les menaces d'e-mails frauduleux (hameçonnage) et les logiciels malveillants, et de protéger les utilisateurs.

Au fur et à mesure que la messagerie électronique prend de l'importance, la mauvaise utilisation qui en est faite aussi. Le courrier indésirable non surveillé peut surcharger les boîtes de réception et les réseaux, affecter la satisfaction des utilisateurs et entraver l'efficacité des communications d'e-mails légitimes. C'est pourquoi Microsoft continue à investir dans les technologies anti-spam. En bref, cela commence par la détection et le filtrage du courrier indésirable.

## <a name="anti-spam-technologies-in-eop"></a>Technologies de blocage du courrier indésirable dans EOP

Pour réduire le courrier indésirable, EOP inclut la protection du courrier indésirable qui utilise des technologies de filtrage du courrier indésirable pour identifier et séparer le courrier indésirable des messages légitimes. Le filtrage du courrier indésirable EOP apprend les menaces connues de courrier indésirable et de hameçonnage et les commentaires des utilisateurs de notre plate-forme grand public, Outlook.com. Les commentaires des utilisateurs EOP dans le programme de classification du courrier indésirable permettent de s’assurer que les technologies EOP sont continuellement formées et améliorées.

Les paramètres de blocage du courrier indésirable dans EOP sont les suivants :

- **Filtrage des connexions**: identifie les serveurs sources de messagerie bons et incorrects au début de la connexion de messagerie entrante via la liste d’adresses IP autorisées, la liste d’adresses IP bloquées et la *liste sécurisée* (une liste dynamique mais non modifiable des expéditeurs approuvés gérés par Microsoft). Vous configurez ces paramètres dans la stratégie de filtrage des connexions. Pour plus d’informations, consultez la rubrique [configurer le filtrage des connexions dans Microsoft 365](configure-the-connection-filter-policy.md).

  > [!NOTE]
  > Usurpation d’identité utilise le filtrage des connexions pour créer des listes verte et rouge d’expéditeurs qui usurpent votre domaine de messagerie. Pour plus d’informations, consultez la rubrique [en savoir plus sur les informations d’usurpation d’identité dans Microsoft 365](learn-about-spoof-intelligence.md).

- **Filtrage du courrier indésirable (filtrage du contenu)**: EOP utilise le filtrage du courrier indésirable : **le courrier indésirable, le**courrier indésirable à **fiabilité élevée**, le courrier électronique **en masse**, le courrier électronique de **hameçonnage** et le **courrier électronique de hameçonnage à haute** Vous pouvez configurer les actions à effectuer en fonction de ces verdicts, et vous pouvez configurer les options de notification de l’utilisateur final pour les messages mis en quarantaine au lieu d’être remis. Pour plus d’informations, consultez la rubrique [configurer des stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

  > [!NOTE]
  > Par défaut, le filtrage du courrier indésirable est configuré pour envoyer des messages marqués comme courrier indésirable dans le dossier courrier indésirable du destinataire. Toutefois, dans les environnements hybrides où EOP protège les boîtes aux lettres Exchange locales, vous devez configurer deux règles de flux de messagerie (également appelées règles de transport) dans votre organisation Exchange locale afin de reconnaître les en-têtes de courrier indésirable EOP ajoutés aux messages. Pour les détails, voir [Configurer une protection Exchange Online (EOP) autonome pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md).

- **Filtrage du courrier indésirable sortant**: EOP vérifie également que les utilisateurs n’envoient pas de courrier indésirable, que ce soit dans le contenu de messages sortants ou en dépassant les limites de messages sortants. Pour plus d’informations, consultez la rubrique [configurer le filtrage du courrier indésirable sortant dans Microsoft 365](configure-the-outbound-spam-policy.md).

- Aide à l' **usurpation**: pour plus d’informations, consultez la rubrique [en savoir plus sur l’aide à l’usurpation dans Microsoft 365](learn-about-spoof-intelligence.md).

## <a name="manage-errors-in-spam-filtering"></a>Gérer les erreurs de filtrage du courrier indésirable

Il est possible que des messages corrects puissent être identifiés comme courrier indésirable (également appelés faux positifs) ou que le courrier indésirable puisse être remis dans la boîte de réception. Vous pouvez utiliser les suggestions des sections suivantes pour savoir ce qui s’est passé et vous aider à le prévenir à l’avenir.

Voici quelques-unes des meilleures pratiques qui s’appliquent à l’un ou l’autre scénario :

- Envoyez toujours des messages mal classés à Microsoft. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- **Examinez les en-têtes de message anti-courrier indésirable**: ces valeurs vous indiquent pourquoi un message a été marqué comme courrier indésirable, ou pourquoi il a ignoré le filtrage du courrier indésirable. Pour plus d’informations, consultez la rubrique [en-têtes de message anti-courrier indésirable](anti-spam-message-headers.md).

- **Pointez votre enregistrement MX vers microsoft 365**: pour que EOP fournisse la meilleure protection, nous vous recommandons de toujours recevoir d’abord les messages remis à Microsoft 365. Pour obtenir des instructions, consultez la rubrique [créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).

  Si l’enregistrement MX pointe vers un autre emplacement (par exemple, une solution ou un équipement de blocage du courrier indésirable), il est difficile pour EOP de fournir un filtrage de courrier indésirable précis. Dans ce scénario, vous devez configurer un filtrage amélioré pour les connecteurs (également appelé _liste de sauts_). Pour obtenir des instructions, voir [Enhanced Filtering for Connectors in Exchange Online](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- **Utiliser l’authentification de messagerie**: Si vous êtes propriétaire d’un domaine de messagerie, vous pouvez utiliser DNS pour vous assurer que les messages provenant d’expéditeurs de ce domaine sont légitimes. Pour éviter le courrier indésirable et l’usurpation indésirable dans EOP, utilisez toutes les méthodes d’authentification de messagerie suivantes :

  - **SPF**: l’infrastructure des stratégies des expéditeurs vérifie l’adresse IP source du message par rapport au propriétaire du domaine d’envoi. Pour une présentation rapide de SPF et pour qu’il soit configuré rapidement, reportez-vous à la rubrique [configurer SPF pour éviter l’usurpation](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Pour mieux comprendre comment Microsoft 365 utilise SPF, ou pour résoudre des problèmes ou des déploiements non standard tels que des déploiements hybrides, commencez par [Comment Microsoft 365 utilise SPF (Sender Policy Framework) pour éviter l’usurpation](how-office-365-uses-spf-to-prevent-spoofing.md).

  - **DKIM**: DomainKeys Identified de messagerie identifiée ajoute une signature numérique à l’en-tête de message des messages envoyés à partir de votre domaine. Pour plus d’informations, consultez [la rubrique use DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Microsoft 365](use-dkim-to-validate-outbound-email.md).

  - **DMARC**: l’authentification de message basée sur un domaine, la création de rapports et la conformité aident les systèmes de messagerie de destination à déterminer la procédure à suivre pour les messages qui échouent aux contrôles SPF ou DKIM et fournit un autre niveau de confiance pour vos partenaires de messagerie. Pour plus d’informations, consultez la rubrique [utiliser DMARC pour valider le courrier électronique dans Microsoft 365](use-dmarc-to-validate-email.md).

- **Vérifiez vos paramètres de courrier en masse**: le seuil de niveau de conformité en bloc (BCL) que vous configurez dans les stratégies de blocage du courrier indésirable détermine si le courrier en masse (également appelé _courrier gris_) est marqué comme courrier indésirable. Le paramètre PowerShell uniquement _MarkAsSpamBulkMail_ qui est activé par défaut contribue également aux résultats. Pour plus d’informations, consultez la rubrique [configurer des stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="prevent-the-delivery-of-spam-to-the-inbox"></a>Empêcher la remise du courrier indésirable dans la boîte de réception

- **Vérifiez les paramètres de votre organisation**: Méfiez-vous des paramètres permettant aux messages d’ignorer le filtrage du courrier indésirable (par exemple, si vous ajoutez votre propre domaine à la liste des domaines autorisés dans les stratégies de blocage du courrier indésirable). Pour connaître les paramètres recommandés, reportez-vous aux [paramètres recommandés pour EOP et Microsoft 365 Security ATP](recommended-settings-for-eop-and-office365-atp.md) and [Create Safe sender lists](create-safe-sender-lists-in-office-365.md).

- **Vérifier que la règle de courrier indésirable est activée dans la boîte aux lettres de l’utilisateur**: elle est activée par défaut, mais si elle est désactivée, les messages marqués comme courrier indésirable ne peuvent pas être déplacés dans le dossier courrier indésirable. Pour plus d’informations, consultez la rubrique [configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Utiliser les listes d’expéditeurs bloqués disponibles**: pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs bloqués](create-block-sender-lists-in-office-365.md).

- **Annuler l’abonnement à des messages électroniques en masse** S’il s’agissait d’un message que l’utilisateur s’est inscrit (bulletins d’information, annonces de produits, etc.) et qu’il contient un lien de résiliation d’abonnement provenant d’une source fiable, demandez-lui simplement de se désabonner.

- **EOP autonome : créer des règles de flux de messagerie dans un échange local pour le filtrage du courrier indésirable EOP**: dans les environnements EOP autonomes où EOP protège les boîtes aux lettres Exchange locales, vous devez configurer des règles de flux de messagerie (également appelées règles de transport) dans Exchange sur site afin de traduire le verdict de filtrage du courrier indésirable. Pour les détails, voir [Configurer une protection Exchange Online (EOP) autonome pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md).

### <a name="prevent-good-email-from-being-identified-as-spam"></a>Empêcher l’identification du courrier électronique en tant que courrier indésirable

Voici quelques étapes à suivre pour éviter les faux positifs :

- **Vérifiez les paramètres du filtre de courrier indésirable Outlook de l’utilisateur**:

  - **Vérifiez que le filtre de courrier indésirable Outlook est désactivé**: lorsque le filtre de courrier indésirable Outlook est défini sur la valeur par défaut **aucun filtrage automatique**, Outlook n’essaie pas de classer les massages comme courrier indésirable.  Lorsqu’il est défini sur **faible** ou **élevé**, le filtre de courrier indésirable d’Outlook utilise sa propre technologie de filtrage SmartScreen pour identifier et déplacer le courrier indésirable dans le dossier courrier indésirable, afin que vous puissiez obtenir des faux positifs. Notez que Microsoft a cessé de produire des mises à jour de définition de courrier indésirable pour les filtres SmartScreen dans Exchange et Outlook en novembre 2016. Les définitions de courrier indésirable SmartScreen existantes étaient conservées, mais leur efficacité sera vraisemblablement dégradée au fil du temps.

  - **Vérifiez que le paramètre « listes approuvées » d’Outlook est désactivé**: lorsque ce paramètre est activé, seuls les messages provenant d’expéditeurs figurant dans la liste des expéditeurs approuvés de l’utilisateur ou dans la liste des destinataires fiables sont remis à la boîte de réception ; les messages provenant d’autres personnes sont automatiquement déplacés vers le dossier courrier indésirable.

  Pour plus d’informations sur ces paramètres, consultez la rubrique [configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Utiliser les listes d’expéditeurs approuvés disponibles**: pour plus d’informations, reportez-vous à [créer des listes d’expéditeurs approuvés] (Create Safe-sender-Lists-in-office-365.MD.

- **Vérifiez que les utilisateurs respectent les limites d’envoi et de réception** , comme décrit dans la rubrique [réception et envoi de limites](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits) dans la description du service Exchange Online.

- **EOP autonome : utiliser la synchronisation d’annuaires**: Si vous utilisez EOP autonome pour protéger votre organisation Exchange locale, vous devez synchroniser les paramètres utilisateur avec le service à l’aide de la synchronisation d’annuaires. Ainsi, vos listes d’expéditeurs approuvés par les utilisateurs sont respectées par EOP. Pour plus d’informations, voir [Utilisation de la synchronisation d’annuaires pour gérer les utilisateurs de messagerie](manage-mail-users-in-eop.md#use-directory-synchronization-to-manage-mail-users).

## <a name="anti-spam-legislation"></a>Législation contre le courrier indésirable

Chez Microsoft, nous pensons que l'évolution de nouvelles technologies et de l'auto-réglementation requiert la prise en charge de cadres juridiques et d'une politique gouvernementale efficaces. La prolifération du courrier indésirable dans le monde a poussé de nombreux organes législatifs à réglementer les e-mails commerciaux. De nombreux pays ont à présent des réglementations en matière de lutte contre le courrier indésirable. Aux États-Unis, des lois au niveau fédéral et au niveau de l'État régissent le courrier indésirable, et cette approche complémentaire contribue à réduire le courrier indésirable tout en permettant au commerce électronique légitime de prospérer. Le CAN-SPAM Act développe les outils disponibles pour limiter les messages électroniques frauduleux et trompeurs.