---
title: Forum Aux Questions sur la protection anti-courrier indésirable
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c534a35d-b121-45da-9d0a-ce738ce51fce
ms.collection:
- M365-security-compliance
description: Questions fréquemment posées et réponses pour les administrateurs concernant la protection contre le courrier indésirable dans Exchange Online et autonome Exchange Online Protection (EOP).
ms.openlocfilehash: 0bd34639d717b979a02272e3c2f5de243c68d3ab
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43636057"
---
# <a name="anti-spam-protection-faq"></a>Forum Aux Questions sur la protection anti-courrier indésirable

Cette rubrique fournit des questions fréquemment posées et des réponses à propos de la protection contre le courrier indésirable pour les clients Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des clients Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online.

Pour accéder à des questions et des réponses sur la mise en quarantaine, voir [FAQ sur la mise en quarantaine](quarantine-faq.md).

Pour obtenir des questions et des réponses sur la protection contre les programmes malveillants, consultez la rubrique [anti-malware protection FAQ](anti-malware-protection-faq-eop.md).

Pour obtenir des questions et des réponses sur la protection contre l’usurpation d’identité, consultez la rubrique [anti-spoofing protection FAQ](anti-spoofing-protection-faq.md).

## <a name="q-by-default-what-happens-to-a-spam-detected-message"></a>Clench. Par défaut, qu'arrive-t-il à un message identifié comme courrier indésirable ?

A. **Pour les messages entrants :** La majorité du courrier indésirable est supprimée via le filtrage des connexions, qui est basé sur l’adresse IP du serveur de messagerie source. Les stratégies de blocage du courrier indésirable (également appelées stratégies de filtrage du courrier indésirable ou stratégies de filtrage de contenu) inspectent et classifient les messages comme courrier indésirable, en bloc ou par hameçonnage. Par défaut, les messages classés comme courrier indésirable ou en bloc sont remis dans le dossier de courrier indésirable du destinataire, tandis que les messages classés comme hameçonnage sont mis en quarantaine. Vous pouvez modifier la stratégie de blocage du courrier indésirable par défaut (s’applique à tous les destinataires) ou vous pouvez créer des stratégies de blocage du courrier indésirable personnalisées avec des paramètres plus stricts pour des groupes d’utilisateurs spécifiques (par exemple, vous pouvez mettre en quarantaine le courrier indésirable envoyé aux cadres dirigeants). Pour plus d’informations, consultez la rubrique [configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md) et les [paramètres de stratégie anti-courrier indésirable recommandés](recommended-settings-for-eop-and-office365-atp.md#eop-anti-spam-policy-settings).

> [!IMPORTANT]
> Dans les déploiements hybrides où EOP protège les boîtes aux lettres locales, vous devez configurer deux règles de flux de messagerie Exchange (également appelées règles de transport) dans votre organisation Exchange locale pour détecter les en-têtes de filtrage du courrier indésirable EOP ajoutés aux messages. Pour les détails, voir [Configurer une protection Exchange Online (EOP) autonome pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md).

 **Pour les messages sortants :** Le message est routé via le pool de [remise à haut risque](high-risk-delivery-pool-for-outbound-messages.md) ou renvoyé à l’expéditeur dans une notification d’échec de remise (également appelée notification de non-remise). Pour plus d’informations sur la protection contre le courrier indésirable sortant, consultez la rubrique [Sorted spam Controls](outbound-spam-controls.md).

## <a name="q-whats-a-zero-day-spam-variant-and-how-is-it-handled-by-the-service"></a>Clench. Qu’est-ce qu’une variante de courrier indésirable de zéro jour et comment est-elle gérée par le service ?

A. Une variante de courrier indésirable du jour zéro est une variante de courrier indésirable précédemment inconnue du courrier indésirable qui n’a jamais été capturée ou analysée, de sorte que nos filtres anti-courrier indésirable n’ont aucune information disponible pour la détecter. Une fois qu’un échantillon de courrier indésirable de zéro jour est capturé et analysé par nos analystes du courrier indésirable s’il répond aux critères de classification du courrier indésirable, nos filtres de blocage du courrier indésirable sont mis à jour pour le détecter et ne sont plus considérés comme « Zero-Day ».

**Remarque :** Si vous recevez un message qui peut être une variante de courrier indésirable de zéro jour, afin de nous aider à améliorer le service, envoyez le message à Microsoft à l’aide de l’une des méthodes décrites dans [rapport messages and files to Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="q-do-i-need-to-configure-the-service-to-provide-anti-spam-protection"></a>Clench. Dois-je configurer le service pour bénéficier d'une protection anti-courrier indésirable ?

A. Une fois que vous vous êtes inscrit au service et ajouté votre domaine, le filtrage du courrier indésirable est automatiquement activé. Par défaut, le filtrage du courrier indésirable est réglé pour vous protéger sans nécessiter aucune configuration supplémentaire (hormis l’exception décrite précédemment pour les clients autonomes EOP autonomes dans les environnements hybrides). En tant qu’administrateur, vous pouvez modifier les paramètres de filtrage du courrier indésirable par défaut pour répondre au mieux aux besoins de votre organisation. Pour une granularité accrue, vous pouvez également créer des stratégies de blocage du courrier indésirable et de blocage du courrier indésirable pour les utilisateurs, les groupes ou les domaines spécifiés dans votre organisation. Les stratégies personnalisées ont toujours priorité sur la stratégie par défaut, mais vous pouvez modifier la priorité (c’est-à-dire, l’ordre d’exécution) de vos stratégies personnalisées.

Pour plus d’informations, voir les rubriques suivantes :

[Paramètres recommandés pour la sécurité ATP d’Office 365](recommended-settings-for-eop-and-office365-atp.md)

[Configurer la protection contre les stratégies](configure-the-connection-filter-policy.md)

[Configuration de stratégies de blocage du courrier indésirable dans Office 365](configure-your-spam-filter-policies.md)

[Configurer la stratégie anti-courrier indésirable sortant](configure-the-outbound-spam-policy.md)

## <a name="q-if-i-make-a-change-to-an-anti-spam-policy-how-long-does-it-take-after-i-save-my-changes-for-them-to-take-effect"></a>Clench. Si je modifie une stratégie anti-courrier indésirable, combien de temps après l'enregistrement de mes changements ces derniers prennent-ils effet ?

A. Les changements devraient prendre effet au bout d’une heure maximum.

## <a name="q-is-bulk-email-filtering-automatically-enabled"></a>Clench. Le filtrage des messages électroniques en bloc est-il automatiquement activé ?

A. Oui. Pour plus d’informations sur les messages électroniques en masse, consultez [la rubrique quelle est la différence entre courrier indésirable et courrier électronique en masse ?](what-s-the-difference-between-junk-email-and-bulk-email.md).

## <a name="q-does-the-service-provide-url-filtering"></a>Clench. Le service fournit-il le filtrage d’URL ?

A. Oui, le service dispose d’un filtre d’URL qui recherche les URL dans les messages. Si des URL associées à du contenu indésirable ou malveillant connu sont détectées, le message est marqué comme courrier indésirable.

## <a name="q-how-can-customers-using-the-service-send-false-negative-spam-and-false-positive-non-spam-messages-to-microsoft"></a>Clench. Comment les clients utilisant le service peuvent-ils signaler des faux négatifs (courrier indésirable) et des faux positifs (messages légitimes) à Microsoft ?

A. Les messages de courrier indésirable et de courrier non indésirable peuvent être envoyés à Microsoft pour être analysés de plusieurs façons. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="q-can-i-get-spam-reports"></a>Clench. Puis-je obtenir des rapports sur le courrier indésirable ?

A. Oui, par exemple, vous pouvez obtenir un rapport de détection de courrier indésirable dans le centre d’administration 365 de Microsoft. Ce rapport indique le volume du courrier indésirable sous forme de nombre de messages uniques. Pour plus d'informations sur les rapports, consultez les liens suivants :

Clients Exchange Online : [surveillance, création de rapports et suivi des messages dans Exchange Online](https://docs.microsoft.com/exchange/monitoring/monitoring)

Clients EOP autonomes : [création de rapports et suivi des messages dans Exchange Online Protection](reporting-and-message-trace-in-exchange-online-protection.md)

## <a name="q-someone-sent-me-a-message-and-i-cant-find-it-i-suspect-that-it-may-have-been-detected-as-spam-is-there-a-tool-that-i-can-use-to-find-out"></a>Clench. Quelqu’un m’a envoyé un message et je ne le trouve pas. Je pense qu'il a peut-être été détecté comme courrier indésirable. Existe-t-il un outil qui me permettrait de m'en assurer ?

A. Oui, l'outil de suivi des messages vous permet de suivre les messages électroniques quand ils sont acheminés via le service afin de déterminer ce qui leur est arrivé. Pour plus d’informations sur l’utilisation de l’outil de suivi des messages afin de déterminer pourquoi un message a été marqué comme courrier indésirable, voir was a- [t-il un message marqué comme courrier indésirable ?](https://docs.microsoft.com/exchange/monitoring/trace-an-email-message/message-trace-faq#was-a-message-marked-as-spam)

## <a name="q-will-the-service-throttle-rate-limit-my-mail-if-my-users-send-outbound-spam"></a>Clench. Le service limite-t-il (limite de débit) ma messagerie si mes utilisateurs envoient du courrier indésirable sortant ?

R. Si plus de la moitié du courrier envoyé via le service par un même utilisateur au cours d'une certain laps de temps (par exemple, par heure) est considéré comme indésirable par Office 365, l'utilisateur ne peut plus envoyer de messages. Dans la plupart des cas, si un message sortant est déterminé comme étant du courrier indésirable, il est routé via le pool de remises à haut risque, ce qui réduit la probabilité d'ajout du pool d'IP sortantes normales à une liste rouge.

Vous pouvez envoyer une notification à une adresse de messagerie spécifique quand un utilisateur est bloqué en relation avec l'envoi de courrier indésirable sortant. Pour plus d'informations sur ce paramètre, consultez la rubrique [Configurer la stratégie anti-courrier indésirable sortant](configure-the-outbound-spam-policy.md).

## <a name="q-can-i-use-a-third-party-anti-spam-and-anti-malware-provider-in-conjunction-with-exchange-online"></a>Clench. Puis-je utiliser un fournisseur tiers de blocage de courrier indésirable et de programme malveillant en association avec Exchange Online ?

A. Oui. Bien que nous vous recommandons de faire pointer votre enregistrement MX vers Microsoft, nous savons qu’il existe des raisons professionnelles légitimes pour acheminer votre courrier électronique vers un autre emplacement que Microsoft.

- **Entrant**: modifiez vos enregistrements MX pour qu’ils pointent vers le fournisseur tiers, puis redirigez les messages vers EOP pour un traitement supplémentaire. Pour plus d’informations, reportez-vous à la rubrique [filtrage amélioré pour les connecteurs dans Exchange Online](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- **Sortant**: configurez le routage d’hôte actif de Microsoft 365 vers le fournisseur de destination tiers.

## <a name="q-does-microsoft-have-any-documentation-about-how-i-can-protect-myself-from-phishing-scams"></a>Clench. Est-ce que Microsoft dispose de documentation concernant la façon dont je peux me protéger contre les tentatives de hameçonnage ?

A. Oui. Pour plus d’informations, consultez [la rubrique Protégez votre confidentialité sur Internet](https://support.microsoft.com/help/4091455) .

## <a name="q-are-spam-and-malware-messages-being-investigated-as-to-who-sent-them-or-being-transferred-to-law-enforcement-entities"></a>Clench. Le courrier indésirable et les messages malveillants font-ils l’objet d’une enquête pour savoir qui les a envoyés, ou sont-ils transférés à des services chargés de l’application de la loi ?

R. Le service se concentre sur la détection et la suppression du courrier indésirable et des programmes malveillants. Il nous arrive toutefois d'enquêter sur des campagnes de courrier indésirable ou d'attaque particulièrement dangereuses ou nuisibles, et de poursuivre leurs auteurs. Cela peut impliquer une collaboration avec nos unités criminalité numérique et juridique afin de retrouver le réseau zombie de l'expéditeur du courrier indésirable, d'empêcher celui-ci d'utiliser le service (s'il l'utilise pour envoyer des messages sortants) et de transmettre les informations à la justice en vue de poursuites pénales.

## <a name="q-what-are-a-set-of-best-outbound-mailing-practices-that-will-ensure-that-my-mail-is-delivered"></a>Clench. Quelles sont les meilleures pratiques d'envoi de courrier sortant pour garantir la remise de mes messages électroniques ?

R. Les instructions ci-dessous constituent les meilleures pratiques pour l'envoi de messages électroniques sortants.

- **Le domaine de messagerie source doit être résolu dans le système DNS.**

  Par exemple, si l’expéditeur est user@fabrikam, le domaine fabrikam est résolu en adresse IP 192.0.43.10.
  
  Si aucun enregistrement A ou enregistrement MX ne correspond au domaine d’envoi dans DNS, le service route le message via son pool de remise à risque plus élevé, que le contenu du message soit du courrier indésirable ou non. Pour plus d’informations sur le pool de remise à risque plus élevé, consultez la rubrique [pool de remise à haut risque pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md).

- **Le courrier sortant eServer doit avoir une entrée DNS (PTR) inverse.**

  Par exemple, si l’adresse IP de la source de courrier électronique est 192.0.43.10, l’entrée `43-10.any.icann.org`DNS inverse serait.

- **Les commandes HELO/EHLO et MAIL FROM doivent être cohérentes, et se présenter sous la forme d'un nom de domaine plutôt que d'une adresse IP.**

  La commande HELO/EHLO doit être configurée pour correspondre à la DNS inversée de l'adresse IP d'envoi, de façon à ce que le domaine ne change pas dans les diverses parties des en-têtes de message.

- **Veillez à ce que les enregistrements SPF appropriés soient configurés dans DNS.**

  Les enregistrements SPF constituent un mécanisme permettant de valider le fait que du courrier électronique envoyé par un domaine provient réellement de ce dernier et n'est pas falsifié. Pour plus d'informations sur les enregistrements SPF, consultez les liens suivants :

  [Configurer SPF pour éviter l’usurpation](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  [Foire aux questions domaines](https://docs.microsoft.com/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

- **Signature de courrier électronique avec DKIM, canonisation assouplie.**

  Si un expéditeur souhaite signer ses messages à l'aide de la technologie DKIM (Domain Keys Identified Mail) et envoyer du courrier sortant via le service, il doit utiliser l'algorithme de canonisation d'en-tête assouplie. Signer avec une canonisation d'en-tête stricte peut entraîner une invalidation de la signature par le service.

- **Les propriétaires de domaine doivent disposer d'informations exactes dans la base de données WHOIS.**

  Ces informations identifient les propriétaires de domaine et indiquent comment les contacter en entrant la société mère stable, le point de contact et les serveurs de noms.

- **For bulk mailers, the From: name should reflect who is sending the message, while the subject line of the message should be a brief summary on what the message is about.**

  Le corps du message doit contenir une indication claire concernant l'offre, le service ou le produit. Par exemple, si un expéditeur envoie un publipostage pour le compte de la société Contoso, voici à quoi doit ressembler le contenu des champs De et Objet du message électronique :

  > De : marketing@contoso.com <br/> Objet : Nouveau catalogue à jour pour la période de Noël

  Voici un exemple de ce qu'il ne faut pas faire parce que ce n'est pas assez descriptif :

  > De : utilisateur@hotmail.com <br/> Objet : Catalogues

- **Si vous envoyez un publipostage à un grand nombre de destinataires et que le message présente le format d'un bulletin d'informations, il doit contenir un lien de désabonnement au bas du texte de contenu.**

  L'option de désabonnement doit ressembler à ceci :

  > Ce message a été adressé à exemple@contoso.com par expéditeur@fabrikam.com. Mettre à jour le profil/adresse de messagerie | Suppression instantanée avec **SafeUnsubscribe** &trade; | Politique de confidentialité

- **En cas d'envoi d'un publipostage, l'acquisition de liste doit être effectuée à l'aide d'un contrôle de consentement double (double opt-in). Si vous êtes un expéditeur de publipostage, cette pratique est recommandée par le secteur.**

  La pratique de contrôle de consentement double consiste à demander à un utilisateur d'effectuer deux actions pour confirmer son abonnement à un courrier électronique marketing :

  1. une première fois en cliquant sur une case à cocher non encore activée pour indiquer qu'il consent à recevoir d'autres offres ou messages électroniques du mercaticien ;

  2. une deuxième fois lorsque le mercaticien envoie un message électronique de confirmation à l'adresse de messagerie fournie par l'utilisateur, lui demandant de cliquer sur un lien sensible au temps pour valider sa confirmation.

  Pour les expéditeurs de publipostages, le recours au contrôle de consentement double a pour effet de leur forger une bonne réputation.

- **Les expéditeurs de publipostage doivent proposer un contenu transparent dont ils peuvent être jugés responsables :**

  1. Tout texte demandant au destinataire d'ajouter l'expéditeur à son carnet d'adresses devrait clairement indiquer qu'une telle action ne constitue par une garantie de remise.

  2. Lors de l'élaboration de redirections dans le corps du message, utilisez un style de lien cohérent.

  3. N'envoyez pas d'images ou de pièces jointes volumineuses, ou des messages contenant uniquement une image.

  4. Si vous utilisez des pixels de suivi (bogues ou balises web), signalez clairement leur présence dans vos paramètres publics de confidentialité ou P3P.

- **Formatez les messages de retour sortants.**

  Lors de la génération de messages de notification d’état de remise (également appelés notifications d’échec de remise ou notifications de non-remise), les expéditeurs doivent suivre le format d’un rebond comme spécifié dans la [norme RFC 3464](https://www.ietf.org/rfc/rfc3464.txt).

- **Supprimez les adresses de messagerie de notification de non-remise pour les utilisateurs inexistants.**

  Si vous recevez une notification d'échec de remise (NDR) indiquant qu'une adresse de messagerie n'est plus utilisée, supprimez l'alias correspondant de votre liste. Les adresses électroniques changent au fil du temps et certaines personnes les abandonnent.

- **Utilisez le programme Smart Network Data Services (SNDS) de Hotmail.**

  Hotmail utilise un programme nommé Smart Network Data Services qui permet aux expéditeurs de consulter des plaintes d'utilisateurs finaux. Le programme SNDS est le portail principal pour le dépannage des problèmes de remise liés à Hotmail.
