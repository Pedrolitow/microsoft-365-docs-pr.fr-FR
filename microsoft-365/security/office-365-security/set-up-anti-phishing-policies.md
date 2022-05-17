---
title: Politiques anti-hameçonnage
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: 5a6f2d7f-d998-4f31-b4f5-f7cbf6f38578
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les stratégies anti-hameçonnage disponibles dans Exchange Online Protection (EOP) et Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 786a71e37e9602be2c8de4637ffd5f83a70e7e59
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438880"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>Stratégies anti-hameçonnage dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les stratégies de configuration des paramètres de protection anti-hameçonnage sont disponibles dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online, des organisations de Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online et Microsoft Defender pour Office 365 organisations.

Voici quelques exemples d’organisations Microsoft Defender pour Office 365 :

- Microsoft 365 Entreprise E5, Microsoft 365 Éducation A5, etc.
- [Microsoft 365 Entreprise](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 Business](https://www.microsoft.com/microsoft-365/business)
- [Microsoft Defender pour Office 365 en tant que module complémentaire](https://products.office.com/exchange/advance-threat-protection)

Les principales différences entre les stratégies anti-hameçonnage dans EOP et les stratégies anti-hameçonnage dans Defender pour Office 365 sont décrites dans le tableau suivant :

|Fonctionnalité|Stratégies anti-hameçonnage dans EOP|Stratégies anti-hameçonnage dans Defender pour Office 365|
|---|:---:|:---:|
|Stratégie par défaut créée automatiquement|![Coche.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|
|Créer des stratégies d'accès externe personnalisées|![Coche.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|
|Paramètres de stratégie courants<sup>\*</sup>|![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|Paramètres d’usurpation d’identité|![Marque de vérification.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|Premier contact conseil de sécurité|![Marque de vérification.](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|
|Paramètres d’emprunt d’identité||![Coche](../../media/checkmark.png)|
|Seuils d’hameçonnage avancés||![Coche](../../media/checkmark.png)|

<sup>\*</sup> Dans la stratégie par défaut, le nom et la description de la stratégie sont en lecture seule (la description est vide) et vous ne pouvez pas spécifier à qui la stratégie s’applique (la stratégie par défaut s’applique à tous les destinataires).

Pour configurer des stratégies anti-hameçonnage, consultez les articles suivants :

- [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)
- [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)

Le reste de cet article décrit les paramètres disponibles dans les stratégies anti-hameçonnage dans EOP et Defender pour Office 365.

## <a name="common-policy-settings"></a>Paramètres de stratégie courants

Les paramètres de stratégie suivants sont disponibles dans les stratégies anti-hameçonnage dans EOP et Defender pour Office 365 :

- **Nom** : vous ne pouvez pas renommer la stratégie anti-hameçonnage par défaut. Après avoir créé une stratégie anti-hameçonnage personnalisée, vous ne pouvez pas renommer la stratégie dans le portail Microsoft 365 Defender.

- **Description** Vous ne pouvez pas ajouter de description à la stratégie anti-hameçonnage par défaut, mais vous pouvez ajouter et modifier la description des stratégies personnalisées que vous créez.

- **Utilisateurs, groupes et domaines** : identifie les destinataires internes auxquels la stratégie anti-hameçonnage s’applique. Cette valeur est requise dans les stratégies personnalisées et n’est pas disponible dans la stratégie par défaut (la stratégie par défaut s’applique à tous les destinataires).

  Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

  - **Utilisateurs** : une ou plusieurs boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie dans votre organisation.
  - **Groupes** : un ou plusieurs groupes de votre organisation.
  - **Domaines** : un ou plusieurs des [domaines acceptés configurés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) dans Microsoft 365.

  - **Exclure ces utilisateurs, groupes et domaines** : exceptions pour la stratégie. Les paramètres et le comportement sont exactement comme les conditions :
    - **Utilisateurs**
    - **Groupes**
    - **Domaines**

  > [!NOTE]
  > Au moins une sélection dans les **paramètres Utilisateurs, groupes et domaines** est requise dans les stratégies anti-hameçonnage personnalisées pour identifier les **destinataires du** message <u>auxquels la stratégie s’applique</u>. Les stratégies anti-hameçonnage dans Defender pour Office 365 ont également [des paramètres d’emprunt d’identité](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) dans lesquels vous pouvez spécifier des adresses e-mail d’expéditeur individuel ou des domaines d’expéditeur <u>qui recevront une protection contre l’emprunt d’identité</u>, comme décrit plus loin dans cet article.

## <a name="spoof-settings"></a>Paramètres d’usurpation d’identité

L’usurpation d’identité se fait lorsque l’adresse From d’un message électronique (l’adresse de l’expéditeur affichée dans les clients de messagerie) ne correspond pas au domaine de la source de courrier. Pour plus d’informations sur l’usurpation d’identité, consultez [la protection contre l’usurpation](anti-spoofing-protection.md) d’identité dans Microsoft 365.

Les paramètres d’usurpation d’identité suivants sont disponibles dans les stratégies anti-hameçonnage dans EOP et Defender pour Office 365 :

- **Activer l’intelligence par usurpation d’identité** : active ou désactive l’intelligence par usurpation d’identité. Nous vous recommandons de le laisser activé.

  Lorsque l’intelligence par usurpation d’identité est activée, **l’insight d’intelligence** de l’usurpation d’identité affiche les expéditeurs usurpés qui ont été automatiquement détectés et autorisés ou bloqués par l’intelligence par usurpation d’identité. Vous pouvez remplacer manuellement le verdict d’usurpation d’identité pour autoriser ou bloquer les expéditeurs d’usurpation d’identité détectés dans l’insight. Mais lorsque vous le faites, l’expéditeur usurpé disparaît de l’insight d’intelligence de l’usurpation d’identité et n’est désormais visible que sous l’onglet **Usurpation** d’identité dans la liste d’autorisation/de blocage du locataire. Vous pouvez également créer manuellement des entrées d’autorisation ou de blocage pour les expéditeurs usurpés dans la liste d’autorisation/de blocage du locataire. Si vous souhaitez en savoir plus, consultez les articles suivants :

  - [Informations sur l’intelligence d’usurpation d’identité dans EOP](learn-about-spoof-intelligence.md)
  - [Gérer la liste verte/bloquée du locataire dans EOP](tenant-allow-block-list.md)

  > [!NOTE]
  >
  > - La protection contre l’usurpation d’identité est activée par défaut dans la stratégie anti-hameçonnage par défaut et dans toutes les nouvelles stratégies anti-hameçonnage personnalisées que vous créez.
  > - Vous n’avez pas besoin de désactiver la protection contre l’usurpation d’identité si votre enregistrement MX ne pointe pas vers Microsoft 365 ; vous activez plutôt le filtrage amélioré pour les connecteurs. Pour obtenir des instructions, consultez [Filtrage amélioré pour les connecteurs dans Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
  > - La désactivation de la protection contre l’usurpation d’identité désactive uniquement la protection _implicite_ contre l’usurpation d’identité contre les vérifications [d’authentification composites](email-validation-and-authentication.md#composite-authentication) . Si l’expéditeur échoue, [DMARC](use-dmarc-to-validate-email.md) _explicite_ vérifie où la stratégie est définie pour la mise en quarantaine ou le rejet, le message est toujours mis en quarantaine ou rejeté.

- **Indicateurs d’expéditeur non authentifiés** : disponibles dans la section **Conseils de sécurité & les indicateurs** uniquement lorsque l’intelligence de l’usurpation d’identité est activée. Consultez les détails de la section suivante.
- **Actions** : pour les messages provenant d’expéditeurs usurpés bloqués (automatiquement bloqués par l’intelligence par usurpation d’identité ou bloqués manuellement dans la liste d’autorisations/blocages du locataire), vous pouvez également spécifier l’action à effectuer sur les messages :
  - **Déplacer des messages vers les dossiers courrier indésirable des destinataires** : il s’agit de la valeur par défaut. Le message est remis à la boîte aux lettres et déplacé vers le dossier Courrier indésirable. Pour plus d’informations, consultez [Configurer les paramètres de courrier indésirable sur Exchange Online boîtes aux lettres dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Mettre en quarantaine le message** : envoie le message en quarantaine au lieu des destinataires prévus. Pour plus d'informations à propos de la quarantaine, consultez les rubriques suivantes:
    - [Mise en quarantaine dans Microsoft 365](quarantine-email-messages.md)
    - [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Rechercher et libérer des messages mis en quarantaine en tant qu’utilisateur dans Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Si vous sélectionnez **Mettre en quarantaine le message**, vous pouvez également sélectionner la stratégie de quarantaine qui s’applique aux messages qui ont été mis en quarantaine par la protection contre l’usurpation d’identité. Les stratégies de quarantaine définissent ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine et si les utilisateurs reçoivent des notifications de quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

### <a name="unauthenticated-sender-indicators"></a>Indicateurs d’expéditeur non authentifiés

Les indicateurs d’expéditeur non authentifiés font partie des [paramètres d’usurpation](#spoof-settings) d’identité disponibles dans la section **Conseils de sécurité & les indicateurs dans les** stratégies anti-hameçonnage dans EOP et Defender pour Office 365. Les paramètres suivants sont disponibles uniquement lorsque l’intelligence de l’usurpation d’identité est activée :

- **Afficher (?) pour les expéditeurs non authentifiés pour l’usurpation** d’identité : ajoute un point d’interrogation à la photo de l’expéditeur dans la zone From si le message ne passe pas les vérifications SPF ou DKIM **et** que le message ne passe pas [l’authentification](email-validation-and-authentication.md#composite-authentication) DMARC ou composite. Lorsque ce paramètre est désactivé, le point d’interrogation n’est pas ajouté à la photo de l’expéditeur.

- **Afficher la balise « via »** : ajoute la balise via (chris@contoso.com <u>via</u> fabrikam.com) dans la zone From si le domaine de l’adresse From (l’expéditeur de message affiché dans les clients de messagerie) est différent du domaine dans la signature DKIM ou l’adresse **MAIL FROM** . Pour plus d’informations sur ces adresses, consultez [Une vue d’ensemble des normes de courrier électronique](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

Pour empêcher l’ajout du point d’interrogation ou de l’étiquette aux messages d’expéditeurs spécifiques, vous disposez des options suivantes :

- Autorisez l’expéditeur usurpé dans [l’insight d’intelligence de l’usurpation](learn-about-spoof-intelligence.md) d’identité ou manuellement dans la [liste d’autorisation/de blocage du locataire](tenant-allow-block-list.md). L’autorisation de l’expéditeur usurpé empêchera l’étiquette via d’apparaître dans les messages de l’expéditeur, même si le paramètre **afficher la balise « via »** est activé dans la stratégie.
- [Configurez l’authentification par e-mail](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own) pour le domaine de l’expéditeur.
  - Pour le point d’interrogation dans la photo de l’expéditeur, SPF ou DKIM sont les plus importants.
  - Pour la balise via, vérifiez que le domaine dans la signature DKIM ou l’adresse **MAIL FROM** correspond (ou est un sous-domaine) au domaine dans l’adresse From.

Pour plus d’informations, consultez [Identifier les messages suspects dans Outlook.com et Outlook sur le web](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206)

## <a name="first-contact-safety-tip"></a>Premier contact conseil de sécurité

Les paramètres **Afficher le premier contact conseil de sécurité** sont disponibles dans EOP et Defender pour Office 365 organisations, et n’ont aucune dépendance vis-à-vis des paramètres de protection de l’usurpation d’identité ou de l’usurpation d’identité. Le conseil de sécurité est présenté aux destinataires dans les scénarios suivants :

- La première fois qu’ils reçoivent un message d’un expéditeur
- Ils ne reçoivent pas souvent de messages de l’expéditeur.

:::image type="content" source="../../media/safety-tip-first-contact-one-recipient.png" alt-text="Première conseil de sécurité de contact pour les messages avec un seul destinataire" lightbox="../../media/safety-tip-first-contact-one-recipient.png":::

:::image type="content" source="../../media/safety-tip-first-contact-multiple-recipients.png" alt-text="Premier contact conseil de sécurité pour les messages avec plusieurs destinataires" lightbox="../../media/safety-tip-first-contact-multiple-recipients.png":::

Cette fonctionnalité ajoute une couche supplémentaire de protection de sécurité contre les attaques d’emprunt d’identité potentielles. Nous vous recommandons donc de l’activer.

Le premier contact conseil de sécurité remplace également la nécessité de créer des règles de flux de messagerie (également appelées règles de transport) qui **ajoutent l’en-tête nommé X-MS-Exchange-EnableFirstContactSafetyTip** par la valeur **Enable** to messages (bien que cette fonctionnalité soit toujours disponible).

> [!NOTE]
> Si le message comporte plusieurs destinataires, indique si le pourboire est affiché et à qui est basé sur un modèle majoritaire. Si la majorité des destinataires n’ont jamais reçu ou ne reçoivent pas souvent de messages de l’expéditeur, les destinataires concernés recevront l’info-bulle **« Certaines personnes qui ont reçu ce message ...** ». Si vous craignez que ce comportement expose les habitudes de communication d’un destinataire à un autre, vous ne devez pas activer le premier contact conseil de sécurité et continuer à utiliser des règles de flux de courrier à la place.

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres exclusifs dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Cette section décrit les paramètres de stratégie disponibles uniquement dans les stratégies anti-hameçonnage dans Defender pour Office 365.

> [!NOTE]
> La stratégie anti-hameçonnage par défaut dans Defender pour Office 365 fournit une [protection contre l’usurpation d’identité](set-up-anti-phishing-policies.md#spoof-settings) et une intelligence de boîte aux lettres pour tous les destinataires. Toutefois, les autres fonctionnalités de [protection d’emprunt d’identité](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) [disponibles et les paramètres avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ne sont pas configurés ou activés dans la stratégie par défaut. Pour activer toutes les fonctionnalités de protection, modifiez la stratégie anti-hameçonnage par défaut ou créez des stratégies anti-hameçonnage supplémentaires.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

L’emprunt d’identité est l’endroit où l’expéditeur ou le domaine de messagerie de l’expéditeur dans un message ressemble à un véritable expéditeur ou domaine :

- Un exemple d'usurpation de l'identité du domaine contoso.com est ćóntoso.com.
- L’emprunt d’identité de l’utilisateur est la combinaison du nom d’affichage et de l’adresse e-mail de l’utilisateur. Par exemple, Valeria Barrios (vbarrios@contoso.com) peut être emprunter l’identité de Valeria Barrios, mais avec une adresse e-mail complètement différente.

> [!NOTE]
> La protection de l’emprunt d’identité recherche des domaines similaires. Par exemple, si votre domaine est contoso.com, nous vérifions que différents domaines de niveau supérieur (.com, .biz, etc.) sont des tentatives d’emprunt d’identité, mais aussi des domaines qui sont même un peu similaires. Par exemple, contosososo.com ou contoabcdef.com peuvent être considérés comme des tentatives d’emprunt d’identité de contoso.com.

Un domaine usurpé pourrait autrement être considéré comme légitime (domaine enregistré, enregistrements d'authentification de courrier électronique configurés, etc.), sauf si son but est de tromper les destinataires.

Les paramètres d’emprunt d’identité suivants sont disponibles uniquement dans les stratégies anti-hameçonnage dans Defender pour Office 365 :

- **Permettre aux utilisateurs de protéger** : empêche l’emprunt d’identité des adresses e-mail internes ou externes spécifiées **en tant qu’expéditeurs de messages**. Par exemple, vous recevez un e-mail du vice-président de votre entreprise vous demandant d’envoyer des informations internes à votre entreprise. Tu le ferais ? Beaucoup de gens enverraient la réponse sans réfléchir.

  Vous pouvez utiliser des utilisateurs protégés pour ajouter des adresses e-mail d’expéditeur internes et externes afin de vous protéger contre l’emprunt d’identité. Cette liste **d’expéditeurs protégés** contre l’emprunt d’identité de l’utilisateur est différente de la liste des **destinataires** auxquels la stratégie s’applique (tous les destinataires de la stratégie par défaut ; destinataires spécifiques configurés dans le paramètre **Utilisateurs, groupes et domaines** dans la section [Paramètres de stratégie communs](#common-policy-settings) ).

  > [!NOTE]
  >
  > - Dans chaque stratégie anti-hameçonnage, vous pouvez spécifier un maximum de 350 utilisateurs protégés (adresses e-mail de l’expéditeur). Vous ne pouvez pas spécifier le même utilisateur protégé dans plusieurs stratégies. Ainsi, quel que soit le nombre de stratégies qui s’appliquent à un destinataire, le nombre maximal d’utilisateurs protégés (adresses e-mail de l’expéditeur) pour chaque destinataire individuel est de 350. Pour plus d’informations sur la priorité de stratégie et la façon dont le traitement des stratégies s’arrête après l’application de la première stratégie, consultez [Ordre et priorité de la protection par e-mail](how-policies-and-protections-are-combined.md).
  > - La protection de l’emprunt d’identité de l’utilisateur ne fonctionne pas si l’expéditeur et le destinataire ont déjà communiqué par e-mail. Si l’expéditeur et le destinataire n’ont jamais communiqué par e-mail, le message est identifié comme une tentative d’emprunt d’identité.

  Par défaut, aucune adresse e-mail d’expéditeur n’est configurée pour la protection de l’emprunt d’identité dans **Les utilisateurs à protéger**. Par conséquent, par défaut, aucune adresse e-mail d’expéditeur n’est couverte par la protection de l’emprunt d’identité, dans la stratégie par défaut ou dans les stratégies personnalisées.

  Lorsque vous ajoutez des adresses e-mail internes ou externes aux **utilisateurs pour protéger** la liste, les messages de ces **expéditeurs** sont soumis à des vérifications de protection de l’emprunt d’identité. Le message est vérifié pour l’emprunt d’identité **si** le message est envoyé à un **destinataire** auquel la stratégie s’applique (tous les destinataires de la stratégie par défaut ; **Utilisateurs, groupes et destinataires de domaines** dans des stratégies personnalisées). Si l’emprunt d’identité est détecté dans l’adresse e-mail de l’expéditeur, les actions de protection de l’emprunt d’identité pour les utilisateurs sont appliquées au message (que faire avec le message, s’il faut afficher les conseils de sécurité des utilisateurs usurpés d’identité, etc.).

- **Activer les domaines à protéger** : empêche l’emprunt d’identité des domaines spécifiés **dans le domaine de l’expéditeur du message**. Par exemple, tous les domaines que vous possédez ([domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)) ou domaines personnalisés spécifiques (domaines que vous possédez ou domaines partenaires). Cette liste de **domaines d’expéditeur protégés** contre l’emprunt d’identité est différente de la liste des **destinataires** auxquels la stratégie s’applique (tous les destinataires de la stratégie par défaut ; destinataires spécifiques configurés dans le paramètre **Utilisateurs, groupes et domaines** dans la section [Paramètres de stratégie communs](#common-policy-settings) ).

  > [!NOTE]
  > Vous pouvez spécifier un maximum de 50 domaines personnalisés dans chaque stratégie anti-hameçonnage.

  Par défaut, aucun domaine d’expéditeur n’est configuré pour la protection de l’emprunt d’identité dans **Activer les domaines à protéger**. Par conséquent, par défaut, aucun domaine d’expéditeur n’est couvert par la protection de l’emprunt d’identité, dans la stratégie par défaut ou dans les stratégies personnalisées.

  Lorsque vous ajoutez des domaines à la liste **Activer les domaines pour protéger** la liste, les messages des **expéditeurs de ces domaines** sont soumis à des vérifications de protection de l’emprunt d’identité. Le message est vérifié pour l’emprunt d’identité **si** le message est envoyé à un **destinataire** auquel la stratégie s’applique (tous les destinataires de la stratégie par défaut ; **Utilisateurs, groupes et destinataires de domaines** dans des stratégies personnalisées). Si l’emprunt d’identité est détecté dans le domaine de l’expéditeur, les actions de protection de l’emprunt d’identité pour les domaines sont appliquées au message (que faire avec le message, s’il faut afficher les conseils de sécurité des utilisateurs usurpés d’identité, etc.).

- **Actions** : choisissez l’action à exécuter pour les messages entrants qui contiennent des tentatives d’emprunt d’identité contre les utilisateurs protégés et les domaines protégés dans la stratégie. Vous pouvez spécifier différentes actions pour l’emprunt d’identité des utilisateurs protégés et l’emprunt d’identité des domaines protégés :
  - **N’appliquez aucune action**
  - **Rediriger le message vers d’autres adresses e-mail** : envoie le message aux destinataires spécifiés au lieu des destinataires prévus.
  - **Déplacer les messages vers les dossiers courrier indésirable des destinataires** : le message est remis à la boîte aux lettres et déplacé vers le dossier Courrier indésirable. Pour plus d’informations, consultez [Configurer les paramètres de courrier indésirable sur Exchange Online boîtes aux lettres dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Mettre en quarantaine le message** : envoie le message en quarantaine au lieu des destinataires prévus. Pour plus d'informations à propos de la quarantaine, consultez les rubriques suivantes:
    - [Mise en quarantaine dans Microsoft 365](quarantine-email-messages.md)
    - [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Rechercher et libérer des messages mis en quarantaine en tant qu’utilisateur dans Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Si vous sélectionnez **Mettre en quarantaine le message**, vous pouvez également sélectionner la stratégie de quarantaine qui s’applique aux messages mis en quarantaine par l’emprunt d’identité de l’utilisateur ou la protection contre l’emprunt d’identité de domaine. Les stratégies de quarantaine définissent ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

  - **Remettre le message et ajouter d’autres adresses à la ligne CCI** : remettre le message aux destinataires prévus et remettre le message en mode silencieux aux destinataires spécifiés.
  - **Supprimez le message avant sa remise** : supprime silencieusement l’intégralité du message, y compris toutes les pièces jointes.

- **Conseils de sécurité** relatifs à l’emprunt d’identité : activez ou désactivez les conseils de sécurité d’emprunt d’identité suivants qui s’affichent dans les messages qui échouent aux vérifications d’emprunt d’identité :
  - **Afficher l’info-bulle pour les utilisateurs emprunts d’identité** : l’adresse From contient une option **Autoriser les utilisateurs à protéger** l’utilisateur. Disponible uniquement si **l’option Activer la protection des utilisateurs** est activée et configurée.
  - **Afficher l’info-bulle pour les domaines empruntés** : l’adresse From contient un **champ Activer les domaines pour protéger le** domaine. Disponible uniquement si **l’option Activer les domaines à protéger** est activée et configurée.
  - **Conseil d’affichage pour les caractères inhabituels** : l’adresse From contient des jeux de caractères inhabituels (par exemple, des symboles mathématiques et du texte ou un mélange de lettres majuscules et minuscules) dans un **paramètre Activer les utilisateurs pour protéger l’expéditeur** ou un **domaine Enable pour protéger le** domaine de l’expéditeur.  Disponible uniquement si **l’option Activer la protection des utilisateurs** _ou_ **Activer les domaines à protéger** est activée et configurée.

- **Activer l’intelligence de boîte aux lettres** : active ou désactive l’intelligence artificielle (IA) qui détermine les modèles de messagerie utilisateur avec leurs contacts fréquents. Ce paramètre permet à l’IA de faire la distinction entre les messages des expéditeurs légitimes et des expéditeurs usurpés d’identité.

  Par exemple, Gabriela Laureano (glaureano@contoso.com) est le PDG de votre entreprise. Vous l’ajoutez donc en tant qu’expéditeur protégé dans l’option **Activer les utilisateurs pour protéger** les paramètres de la stratégie. Mais, certains des destinataires que la stratégie s’applique pour communiquer régulièrement avec un fournisseur qui est également appelé Gabriela Laureano (glaureano@fabrikam.com). Étant donné que ces destinataires ont un historique de communication avec glaureano@fabrikam.com, l’intelligence de boîte aux lettres n’identifie pas les messages de glaureano@fabrikam.com comme une tentative d’emprunt d’identité de glaureano@contoso.com pour ces destinataires.

  Pour utiliser des contacts fréquents qui ont été appris par l’intelligence de boîte aux lettres (et l’absence de celui-ci) pour aider à protéger les utilisateurs contre les attaques d’emprunt d’identité, vous pouvez activer **la protection d’emprunt d’identité d’intelligence** après avoir activé **activer l’intelligence de boîte aux lettres**.

- **Activer la protection de l’emprunt d’identité d’intelligence** : activez ce paramètre pour spécifier l’action à effectuer sur les messages pour les détections d’emprunt d’identité à partir des résultats de l’intelligence de boîte aux lettres :
  - **N’appliquez aucune action** : notez que cette valeur a le même résultat que l’activation de l’intelligence de boîte **aux lettres** , mais la désactivation **de la protection activer l’emprunt d’identité du renseignement**.
  - **Rediriger le message vers d’autres adresses e-mail**
  - **Déplacer le message vers les dossiers courrier indésirable des destinataires**
  - **Mettre en quarantaine le message** : si vous sélectionnez cette action, vous pouvez également sélectionner la stratégie de quarantaine qui s’applique aux messages mis en quarantaine par la protection d’intelligence de boîte aux lettres. Les stratégies de quarantaine définissent ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine et si les utilisateurs reçoivent des notifications de quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).
  - **Remettre le message et ajouter d’autres adresses à la ligne CCI**
  - **Supprimer le message avant qu’il ne soit remis**

- **Ajouter des expéditeurs et des domaines approuvés** : exceptions aux paramètres de protection de l’emprunt d’identité. Les messages des domaines d’expéditeur et d’expéditeur spécifiés ne sont jamais classés en tant qu’attaques basées sur l’emprunt d’identité par la stratégie. En d’autres termes, l’action pour les expéditeurs protégés, les domaines protégés ou la protection d’intelligence de boîte aux lettres ne sont pas appliquées à ces domaines d’expéditeur approuvés ou d’expéditeur. La limite maximale pour ces listes est de 1 024 entrées.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Seuils de hameçonnage avancés dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Les seuils de hameçonnage avancés suivants sont disponibles uniquement dans les stratégies anti-hameçonnage dans Defender pour Office 365. Ces seuils contrôlent la sensibilité de l’application de modèles Machine Learning aux messages pour déterminer un verdict de hameçonnage :

- **1 - Standard** : il s’agit de la valeur par défaut. La gravité de l’action effectuée sur le message dépend du degré de confiance que le message est le hameçonnage (confiance faible, moyenne, élevée ou très élevée). Par exemple, les messages identifiés comme hameçonnage avec un degré de confiance très élevé ont les actions les plus sévères appliquées, tandis que les messages identifiés comme hameçonnage avec un faible degré de confiance ont des actions moins sévères appliquées.
- **2 - Agressif** : les messages identifiés comme hameçonnage avec un degré élevé de confiance sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.
- **3 - Plus agressif** : les messages identifiés comme hameçonnage avec un degré moyen ou élevé de confiance sont traités comme s’ils étaient identifiés avec un degré de confiance très élevé.
- **4 - Le plus agressif** : les messages identifiés comme hameçonnage avec un niveau de confiance faible, moyen ou élevé sont traités comme s’ils étaient identifiés avec un degré de confiance très élevé.

Le risque de faux positifs (messages marqués comme mauvais) augmente à mesure que vous augmentez ce paramètre. Pour plus d’informations sur les paramètres recommandés, consultez la [stratégie anti-hameçonnage dans Microsoft Defender pour Office 365 paramètres](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).
