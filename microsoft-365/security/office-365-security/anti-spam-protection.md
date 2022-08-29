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
description: Les administrateurs peuvent en savoir plus sur les paramètres anti-courrier indésirable et les filtres qui vous aideront à empêcher le courrier indésirable dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9685ca45859e842ae57d3d451a3de9e16cdc9ba6
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67385834"
---
# <a name="anti-spam-protection-in-eop"></a>Protection anti-courrier indésirable dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

> [!NOTE]
> Cette rubrique est destinée aux administrateurs. Pour les rubriques relatives aux utilisateurs finaux, consultez [Vue d’ensemble du filtre de Email courrier](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089) [indésirable et en savoir plus sur les courriers indésirables et le hameçonnage](https://support.microsoft.com/office/86c1d76f-4d5a-4967-9647-35665dc17c31).

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, les messages électroniques sont automatiquement protégés contre le courrier indésirable (courrier indésirable) par EOP.

La feuille de route sécurité de messagerie de Microsoft implique une approche inter-produits sans correspondance. La technologie EOP anti-courrier indésirable et anti-hameçonnage est appliquée sur nos plateformes de messagerie pour fournir aux utilisateurs les derniers outils et innovations anti-courrier indésirable et anti-hameçonnage sur l’ensemble du réseau. L'objectif d'EOP est de proposer un service de messagerie complet et utilisable qui vous aide à détecter le courrier indésirable, les menaces d'e-mails frauduleux (hameçonnage) et les logiciels malveillants, et de protéger les utilisateurs.

Au fur et à mesure que la messagerie électronique prend de l'importance, la mauvaise utilisation qui en est faite aussi. Le courrier indésirable non surveillé peut surcharger les boîtes de réception et les réseaux, affecter la satisfaction des utilisateurs et entraver l'efficacité des communications d'e-mails légitimes. C'est pourquoi Microsoft continue à investir dans les technologies anti-spam. En bref, cela commence par la détection et le filtrage du courrier indésirable.

> [!TIP]
> Les technologies anti-courrier indésirable suivantes sont utiles lorsque vous souhaitez autoriser ou bloquer des messages en fonction de l’enveloppe du message (par exemple, le domaine de l’expéditeur ou l’adresse IP source du message). Pour autoriser ou bloquer des messages en fonction de la charge utile (par exemple, les URL dans le message ou les fichiers joints), vous devez utiliser le [portail Autoriser/Bloquer la liste](manage-tenant-allow-block-list.md) des locataires.

## <a name="anti-spam-technologies-in-eop"></a>Technologies anti-courrier indésirable dans EOP

Pour réduire le courrier indésirable, EOP inclut une protection contre les courriers indésirables qui utilise des technologies de filtrage de courrier indésirable propriétaires pour identifier et séparer les courriers indésirables des messages légitimes. Le filtrage du courrier indésirable EOP apprend des menaces connues de courrier indésirable et de hameçonnage et des commentaires des utilisateurs de notre plateforme de consommateurs, Outlook.com. Les commentaires continus des utilisateurs EOP dans le programme de classification de courrier indésirable permettent de s’assurer que les technologies EOP sont continuellement formées et améliorées.

Les paramètres anti-courrier indésirable dans EOP sont constitués des technologies suivantes :

- **Filtrage de connexion** : identifie les serveurs sources de courrier bons et incorrects au début de la connexion e-mail entrante via la liste d’adresses IP autorisées, la liste de blocage IP et la *liste sécurisée* (liste dynamique mais non modifiable d’expéditeurs approuvés maintenus par Microsoft). Vous configurez ces paramètres dans la stratégie de filtrage des connexions. Pour plus d’informations, consultez [Configurer le filtrage des connexions](configure-the-connection-filter-policy.md).

- **Filtrage du courrier indésirable (filtrage de contenu)** : EOP utilise les verdicts de filtrage du courrier indésirable **spam**, **courrier indésirable à haut niveau de confiance**, **courrier électronique en bloc**, **e-mail de hameçonnage** et **e-mail de hameçonnage à haut niveau de confiance** pour classifier les messages. Vous pouvez configurer les actions à effectuer en fonction de ces verdicts, et vous pouvez configurer ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine et si l’utilisateur reçoit des notifications de quarantaine à l’aide de [stratégies de quarantaine](quarantine-policies.md). Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

  > [!NOTE]
  > Par défaut, le filtrage du courrier indésirable est configuré pour envoyer des messages marqués comme courrier indésirable au dossier Junk Email du destinataire. Toutefois, dans les environnements hybrides où EOP protège les boîtes aux lettres Exchange locales, vous devez configurer deux règles de flux de courrier (également appelées règles de transport) dans votre organisation Exchange locale pour reconnaître les en-têtes de courrier indésirable EOP ajoutés aux messages. Pour les détails, voir [Configurer Exchange Online Protection (EOP) pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- **Filtrage du courrier indésirable sortant** : EOP vérifie également que vos utilisateurs n’envoient pas de courrier indésirable, soit dans le contenu des messages sortants, soit en dépassant les limites des messages sortants. Pour plus d’informations, consultez [Configurer le filtrage du courrier indésirable sortant dans Microsoft 365](configure-the-outbound-spam-policy.md).

- **Renseignement sur l’usurpation** d’identité : pour plus d’informations, consultez [la protection contre l’usurpation d’identité dans EOP](anti-spoofing-protection.md).

## <a name="manage-errors-in-spam-filtering"></a>Gérer les erreurs dans le filtrage du courrier indésirable

Il est possible que les bons messages puissent être identifiés comme courrier indésirable (également appelés faux positifs) ou que le courrier indésirable puisse être remis à la boîte de réception (également appelés faux négatifs). Vous pouvez utiliser les suggestions des sections suivantes pour savoir ce qui s’est passé et l’empêcher de se produire à l’avenir.

Voici quelques bonnes pratiques qui s’appliquent à l’un ou l’autre des scénarios :

- Signalez toujours les messages mal classés à Microsoft. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- **Examinez les en-têtes de message anti-courrier indésirable** : ces valeurs vous indiquent pourquoi un message a été marqué comme courrier indésirable ou pourquoi il a ignoré le filtrage du courrier indésirable. Pour plus d’informations, consultez [En-têtes de message anti-courrier indésirable dans Microsoft 365](anti-spam-message-headers.md).

- **Pointez votre enregistrement MX vers Microsoft 365** : pour qu’EOP offre la meilleure protection, nous vous recommandons toujours d’envoyer d’abord des e-mails à Microsoft 365. Pour obtenir des instructions, consultez [Créer des enregistrements DNS auprès de n’importe quel fournisseur d’hébergement DNS pour Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

  Si l’enregistrement MX pointe vers un autre emplacement (par exemple, une solution ou une appliance anti-courrier indésirable tierce), il est difficile pour EOP de fournir un filtrage précis du courrier indésirable. Dans ce scénario, vous devez configurer le filtrage amélioré pour les connecteurs (également appelé _liste d’ignorer_). Pour obtenir des instructions, consultez [Filtrage amélioré pour les connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- **Utiliser l’authentification par e-mail** : si vous possédez un domaine de messagerie, vous pouvez utiliser DNS pour vous assurer que les messages des expéditeurs de ce domaine sont légitimes. Pour éviter le courrier indésirable et l’usurpation d’identité dans EOP, utilisez toutes les méthodes d’authentification par e-mail suivantes :

  - **SPF** : Sender Policy Framework vérifie l’adresse IP source du message par rapport au propriétaire du domaine d’envoi. Pour une présentation rapide de SPF et pour le configurer rapidement, consultez [Configurer SPF pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Pour consulter des informations plus approfondies sur l’utilisation de SPF par Microsoft 365, la résolution des problèmes et les déploiements non standard tels que les déploiements hybrides, voir [Comment Microsoft 365 utilise SPF (Sender Policy Framework) pour empêcher l’usurpation d’identité](how-office-365-uses-spf-to-prevent-spoofing.md).

  - **DKIM** : DomainKeys Identified Mail ajoute une signature numérique à l’en-tête de message des messages envoyés à partir de votre domaine. Pour plus d’informations, consultez [Utiliser DKIM pour valider les e-mails sortants envoyés à partir de votre domaine personnalisé dans Microsoft 365](use-dkim-to-validate-outbound-email.md).

  - **DMARC** : L’authentification des messages basée sur le domaine, la création de rapports et la conformité aident les systèmes de messagerie de destination à déterminer ce qu’il faut faire avec les messages qui échouent aux vérifications SPF ou DKIM et fournit un autre niveau de confiance à vos partenaires de messagerie. Pour plus d’informations, consultez [Utiliser DMARC pour valider le courrier électronique dans Microsoft 365](use-dmarc-to-validate-email.md).

- **Vérifiez vos paramètres de courrier en bloc** : le seuil de niveau de réclamation en bloc (BCL) que vous configurez dans les stratégies anti-courrier indésirable détermine si le courrier électronique en bloc (également appelé _courrier gris_) est marqué comme courrier indésirable. Le paramètre PowerShell uniquement _MarkAsSpamBulkMail_ activé par défaut contribue également aux résultats. Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="prevent-the-delivery-of-spam-to-the-inbox"></a>Empêcher la remise de courrier indésirable à la boîte de réception

- **Vérifier les paramètres de votre organisation** : surveillez les paramètres qui permettent aux messages d’ignorer le filtrage du courrier indésirable (par exemple, si vous ajoutez votre propre domaine à la liste des domaines autorisés dans les stratégies anti-courrier indésirable). Pour connaître nos paramètres recommandés, consultez [Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](recommended-settings-for-eop-and-office365.md) et [Créer des listes d’expéditeurs sécurisés](create-safe-sender-lists-in-office-365.md).

- **Utilisez les listes d’expéditeurs bloqués disponibles** : pour plus d’informations, consultez [Créer des listes d’expéditeurs bloqués](create-block-sender-lists-in-office-365.md).

- **Se désabonner d’un e-mail en bloc** Si le message était quelque chose pour lequel l’utilisateur s’est inscrit (bulletins d’informations, annonces de produit, etc.) et contient un lien de désabonnement d’une source réputée, envisagez de lui demander de simplement se désabonner.

- **EOP autonome : créez des règles de flux de courrier dans les verdicts de filtrage du courrier indésirable Exchange pour EOP locaux : dans les environnements** hybrides où EOP protège les boîtes aux lettres Exchange locales, vous devez configurer des règles de flux de courrier (également appelées règles de transport) dans Exchange local. Ces règles de flux de courrier traduisent le verdict de filtrage du courrier indésirable EOP afin que la règle de courrier indésirable dans la boîte aux lettres puisse déplacer le message vers le dossier Courrier indésirable Email. Pour les détails, voir [Configurer Exchange Online Protection (EOP) pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

### <a name="prevent-good-email-from-being-identified-as-spam"></a>Empêcher l’identification d’un courrier électronique correct comme courrier indésirable

Voici quelques étapes que vous pouvez suivre pour éviter les faux positifs :

- **Vérifiez les paramètres de filtre de courrier indésirable Outlook Email de l’utilisateur** :

  - **Vérifiez que le filtre Outlook Junk Email est désactivé** : lorsque le filtre Outlook Junk Email est défini sur la valeur par défaut **Aucun filtrage automatique**, Outlook ne tente pas de classer les messages comme courrier indésirable.  Lorsqu’il est défini sur **Faible** ou **Élevé**, outlook Junk Email Filter utilise sa propre technologie de filtre SmartScreen pour identifier et déplacer le courrier indésirable vers le dossier Junk Email, afin que vous puissiez obtenir des faux positifs. Notez que Microsoft a cessé de produire des mises à jour de définition de courrier indésirable pour les filtres SmartScreen dans Exchange et Outlook en novembre 2016. Les définitions de courrier indésirable SmartScreen existantes ont été conservées, mais leur efficacité se dégradera probablement au fil du temps.

  - **Vérifiez que le paramètre « Listes fiables uniquement » d’Outlook est désactivé** : lorsque ce paramètre est activé, seuls les messages des expéditeurs de la liste Des expéditeurs approuvés ou de la liste des destinataires approuvés de l’utilisateur sont remis à la boîte de réception ; les e-mails de tous les autres utilisateurs sont automatiquement déplacés vers le dossier Junk Email.

  Pour plus d’informations sur ces paramètres, consultez [Configurer les paramètres de courrier indésirable sur Exchange Online boîtes aux lettres dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Utilisez les listes d’expéditeurs fiables disponibles** : pour plus d’informations, consultez [Créer des listes d’expéditeurs sécurisés](create-safe-sender-lists-in-office-365.md).

- **Vérifiez que les utilisateurs se trouvent dans les limites d’envoi et de réception**, comme décrit dans [les limites de réception et d’envoi](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits) dans la description du service Exchange Online.

- **EOP autonome : utilisez la synchronisation d’annuaires** : si vous utilisez EOP autonome pour protéger votre organisation Exchange locale, vous devez synchroniser les paramètres utilisateur avec le service à l’aide de la synchronisation d’annuaires. Ainsi, vos listes d’expéditeurs approuvés par les utilisateurs sont respectées par EOP. Pour plus d’informations, voir [Utilisation de la synchronisation d’annuaires pour gérer les utilisateurs de messagerie](/exchange/standalone-eop/manage-mail-users-in-eop#synchronize-directories-with-azure-active-directory-connect-aad-connect).

## <a name="anti-spam-legislation"></a>Législation anti-courrier indésirable

Chez Microsoft, nous pensons que l'évolution de nouvelles technologies et de l'auto-réglementation requiert la prise en charge de cadres juridiques et d'une politique gouvernementale efficaces. La prolifération du courrier indésirable dans le monde a poussé de nombreux organes législatifs à réglementer les e-mails commerciaux. De nombreux pays ont mis en place des lois sur la lutte contre le courrier indésirable. Aux États-Unis, des lois au niveau fédéral et au niveau de l'État régissent le courrier indésirable, et cette approche complémentaire contribue à réduire le courrier indésirable tout en permettant au commerce électronique légitime de prospérer. Le CAN-SPAM Act développe les outils disponibles pour limiter les messages électroniques frauduleux et trompeurs.
