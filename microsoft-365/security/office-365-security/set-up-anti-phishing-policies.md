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
localization_priority: Normal
ms.assetid: 5a6f2d7f-d998-4f31-b4f5-f7cbf6f38578
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les stratégies anti-hameçonnage disponibles dans Exchange Online Protection (EOP) et Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 205fd5cd40d187eada4f6b87edf64c0d35f7e3b3
ms.sourcegitcommit: b09aee96a1e2266b33ba81dfe497f24c5300bb56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2021
ms.locfileid: "52788414"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>Stratégies anti-hameçonnage dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les stratégies de configuration des paramètres de protection anti-hameçonnage sont disponibles dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online, des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online et Microsoft Defender pour Office 365 organisations.

Les stratégies anti-hameçonnage dans Microsoft Defender Office 365 sont disponibles uniquement dans les organisations qui disposent de Defender pour Office 365. Par exemple :

- Microsoft 365 Entreprise E5, Microsoft 365 Éducation A5, etc.
- [Microsoft 365 Entreprise](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 Business](https://www.microsoft.com/microsoft-365/business)
- [Microsoft Defender pour Office 365 en tant qu’modules](https://products.office.com/exchange/advance-threat-protection)

Les différences de haut niveau entre les stratégies anti-hameçonnage dans EOP et les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 sont décrites dans le tableau suivant :

****

|Fonctionnalité|Stratégies anti-hameçonnage dans EOP|Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365|
|---|:---:|:---:|
|Stratégie par défaut créée automatiquement|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|
|Créer des stratégies d'accès externe personnalisées|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|
|Paramètres de stratégie<sup>\*</sup>|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|
|Paramètres d’emprunt d’identité||![Coche](../../media/checkmark.png)|
|Paramètres d’usurpation d’une usurpation|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|
|Seuils de hameçonnage avancés||![Coche](../../media/checkmark.png)|
|

<sup>\*</sup> Dans la stratégie par défaut, le nom et la description de la stratégie sont en lecture seule (la description est vide) et vous ne pouvez pas spécifier à qui s’applique la stratégie (la stratégie par défaut s’applique à tous les destinataires).

Pour configurer des stratégies anti-hameçonnage, consultez les articles suivants :

- [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)

- [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-atp-anti-phishing-policies.md)

Le reste de cet article décrit les paramètres disponibles dans les stratégies anti-hameçonnage dans EOP et Defender pour Office 365.

## <a name="policy-settings"></a>Paramètres de stratégie

Les paramètres de stratégie suivants sont disponibles dans les stratégies anti-hameçonnage dans EOP et Microsoft Defender pour Office 365 :

- **Nom**: vous ne pouvez pas renommer la stratégie anti-hameçonnage par défaut. Après avoir créé une stratégie anti-hameçonnage personnalisée, vous ne pouvez pas renommer la stratégie dans le Centre de sécurité & conformité.

- **Description** Vous ne pouvez pas ajouter de description à la stratégie anti-hameçonnage par défaut, mais vous pouvez ajouter et modifier la description des stratégies personnalisées que vous créez.

- **Appliqué à**: identifie les destinataires internes à qui la stratégie anti-hameçonnage s’applique. Cette valeur est requise dans les stratégies personnalisées et n’est pas disponible dans la stratégie par défaut (la stratégie par défaut s’applique à tous les destinataires).

  Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

  - **Le destinataire est**: une ou plusieurs boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie dans votre organisation.
  - **Le destinataire est membre de**: Un ou plusieurs groupes de votre organisation.
  - **Le domaine du destinataire** est : un ou plusieurs des domaines acceptés configurés dans Microsoft 365.

  - **Sauf quand**: exceptions pour la règle. Les paramètres et le comportement sont exactement comme les conditions :

    - **Le destinataire est**
    - **Le destinataire est membre de**
    - **Le domaine du destinataire est**

  > [!NOTE]
  > Le **paramètre Appliqué à** est requis dans les stratégies anti-hameçonnage personnalisées pour identifier les **destinataires** du message à qui la <u>stratégie s’applique.</u> Les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 ont également des [paramètres](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) d’emprunt d’identité dans lequel vous pouvez spécifier des adresses e-mail d’expéditeur ou des domaines d’expéditeur individuels qui bénéficieront d’une <u>protection</u> contre l’emprunt d’identité, comme décrit plus loin dans cet article.

## <a name="spoof-settings"></a>Paramètres d’usurpation d’une usurpation

L’usurpation d’adresse est lorsque l’adresse De d’un message électronique (l’adresse de l’expéditeur affichée dans les clients de messagerie) ne correspond pas au domaine de la source de courrier. Pour plus d’informations sur l’usurpation d’informations, consultez la protection contre [l’usurpation d’Microsoft 365](anti-spoofing-protection.md).

Les paramètres d’usurpation suivants sont disponibles dans les stratégies anti-hameçonnage dans EOP et Microsoft Defender pour Office 365 :

- **Activer la veille contre l’usurpation** d’informations : active ou non la veille contre l’usurpation d’informations. Nous vous recommandons de laisser ce dernier allumé.

  Lorsque la veille contre l’usurpation d’adresse est activée, la veille contre l’usurpation d’informations affiche les expéditeurs usurpés qui ont été automatiquement détectés et autorisés ou bloqués par la veille contre l’usurpation d’adresses.  Vous pouvez remplacer manuellement le verdict de veille contre l’usurpation d’adresse pour autoriser ou bloquer les expéditeurs usurpés détectés dans l’insight. Mais lorsque vous le faites, l’expéditeur usurpé disparaît de l’aperçu de l’usurpation d’intelligence et n’est désormais visible que sous l’onglet Usurpation d’adresse dans la liste d’adresses client autoriser/bloquer.  Vous pouvez également créer manuellement des entrées d’autoriser ou de bloquer des expéditeurs usurpés dans la liste d’adresses client autoriser/bloquer. Pour plus d’informations, voir les rubriques suivantes :

  - [Informations sur l’usurpation d’intelligence dans EOP](learn-about-spoof-intelligence.md)
  - [Gérer la liste d’adresses client autoriser/bloquer dans EOP](tenant-allow-block-list.md)

  > [!NOTE]
  >
  > - La protection contre l’usurpation d’emploi est activée par défaut dans la stratégie anti-hameçonnage par défaut et dans toutes les nouvelles stratégies anti-hameçonnage personnalisées que vous créez.
  >
  > - Vous n’avez pas besoin de désactiver la protection contre l’usurpation d’Microsoft 365 ; vous activez le filtrage amélioré pour les connecteurs à la place. Pour obtenir des instructions, voir [Filtrage amélioré pour les connecteurs dans Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
  >
  > - La désactivation de la protection contre l’usurpation d’identité désactive uniquement la protection implicite contre l’usurpation d’identité contre les vérifications [d’authentification composite.](email-validation-and-authentication.md#composite-authentication) Si l’expéditeur échoue aux vérifications [DMARC](use-dmarc-to-validate-email.md) explicites où la stratégie est définie sur mise en quarantaine ou rejet, le message est toujours mis en quarantaine ou rejeté.

- **Paramètres de l’expéditeur** non authentifié : consultez les informations de la section suivante.

- **Actions**: pour les messages provenant d’expéditeurs usurpés bloqués (automatiquement bloqués par la veille contre l’usurpation d’adresse ou bloqués manuellement dans la liste d’adresses client bloquées), vous pouvez également spécifier l’action à prendre sur les messages :

  - **Déplacez les messages vers les dossiers Courrier** indésirable des destinataires : il s’agit de la valeur par défaut. Le message est remis à la boîte aux lettres et déplacé vers le dossier Courrier indésirable. Dans Exchange Online, le message est déplacé vers le dossier Courrier indésirable si la règle de courrier indésirable est activée sur la boîte aux lettres (activée par défaut). Pour plus d’informations, voir [Configurer les paramètres](configure-junk-email-settings-on-exo-mailboxes.md)de courrier indésirable Exchange Online boîtes aux lettres dans Microsoft 365 .

  - **Mettre le message en** quarantaine : envoie le message en quarantaine au lieu des destinataires prévus. Pour plus d’informations sur la mise en quarantaine, consultez les articles suivants :

    - [Mise en quarantaine dans Microsoft 365](quarantine-email-messages.md)
    - [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Rechercher et libérer les messages mis en quarantaine en tant qu’utilisateur dans Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

### <a name="unauthenticated-sender"></a>Expéditeur non authentifié

Les paramètres des expéditeurs non authentifiés font partie des paramètres d’usurpation d’adresses qui sont disponibles dans les [stratégies](#spoof-settings) anti-hameçonnage dans EOP et Microsoft Defender pour Office 365 comme décrit dans la section précédente.

- Activez le symbole de point d’interrogation de l’expéditeur non authentifié **(?)**: lorsque ce paramètre est activé, un point d’interrogation  est ajouté à la photo de l’expéditeur dans la zone De si le message ne passe pas les vérifications SPF ou DKIM et si le message ne passe pas l’authentification DMARC ou [composite.](email-validation-and-authentication.md#composite-authentication) Lorsque ce paramètre est désactivé, le point d’interrogation n’est pas ajouté à la photo de l’expéditeur.

- Activez la balise « **via**» : lorsque ce paramètre est activé, la balise via (chris@contoso.com via fabrikam.com) est ajoutée dans la zone De si le domaine dans l’adresse De (l’expéditeur du message affiché dans les clients de messagerie) est différent du domaine dans la signature DKIM ou <sup>\*</sup> l’adresse **MAIL FROM.** <u></u> Pour plus d’informations sur ces adresses, voir [une vue d’ensemble des normes de message électronique.](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards)

> [!NOTE]
> Actuellement, le **paramètre Activer « via » n’est** pas disponible dans toutes les organisations. Si vous n’avez pas le paramètre Activer «  **via** » ? le point d’interrogation et la balise via sont tous deux contrôlés par le paramètre Activer le point d’interrogation de l’expéditeur non authentifié **(?)** dans votre organisation.

Pour empêcher l’ajout du point d’interrogation ou d’une balise à des messages provenant d’expéditeurs spécifiques, vous avez les options suivantes :

- Autoriser l’expéditeur usurpé dans l’aperçu de [l’usurpation d’intelligence](learn-about-spoof-intelligence.md) ou manuellement dans la liste d’adresses client [autoriser/bloquer](tenant-allow-block-list.md). Autoriser l’expéditeur usurpé empêche l’apparition de la balise via dans les messages de l’expéditeur lorsque l’identification de l’expéditeur non authentifié est désactivée.

- [Configurez l’authentification de](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own) messagerie pour le domaine de l’expéditeur.
  - Pour le point d’interrogation dans la photo de l’expéditeur, SPF ou DKIM sont les plus importants.
  - Pour la balise via, confirmez que le domaine dans la signature DKIM ou l’adresse **MAIL FROM** correspond (ou est un sous-domaine) du domaine dans l’adresse De.

Pour plus d’informations, voir Identifier les messages suspects [dans Outlook.com et Outlook sur le web](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206)

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres exclusifs dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Cette section décrit les paramètres de stratégie disponibles uniquement dans les stratégies anti-hameçonnage dans Microsoft Defender pour les Office 365.

> [!NOTE]
> La stratégie anti-hameçonnage par défaut dans Microsoft [](set-up-anti-phishing-policies.md#spoof-settings) Defender Office 365 protection contre l’usurpation d’adresses et la veille des boîtes aux lettres pour tous les destinataires. Toutefois, les autres fonctionnalités disponibles de [protection](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) contre l’emprunt d’identité et les paramètres avancés ne sont pas [configurés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ou activés dans la stratégie par défaut. Pour activer toutes les fonctionnalités de protection, modifiez la stratégie anti-hameçonnage par défaut ou créez des stratégies anti-hameçonnage supplémentaires.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

L’emprunt d’identité est l’endroit où l’expéditeur ou le domaine de messagerie de l’expéditeur dans un message ressemble à un expéditeur ou un domaine réel :

- Un exemple d'usurpation de l'identité du domaine contoso.com est ćóntoso.com.
- Un exemple d'usurpation de l'identité de l'utilisateur michelle@contoso.com est michele@contoso.com.

Un domaine usurpé pourrait autrement être considéré comme légitime (domaine enregistré, enregistrements d'authentification de courrier électronique configurés, etc.), sauf si son but est de tromper les destinataires.

Les paramètres d’emprunt d’identité suivants sont disponibles uniquement dans les stratégies anti-hameçonnage dans Microsoft Defender Office 365 :

- **Ajouter des utilisateurs à protéger**: empêche l’emprunt d’identité des adresses de messagerie internes ou externes spécifiées en tant **qu’expéditeurs de messages.** Par exemple, vous recevez un message électronique du vice-président de votre entreprise vous demandant d’envoyer des informations internes à l’entreprise. Le feriez-vous ? De nombreuses personnes envoient la réponse sans réfléchir.

  Vous pouvez utiliser des utilisateurs protégés pour ajouter des adresses de messagerie d’expéditeur internes et externes afin de vous protéger contre l’emprunt d’identité. Cette liste  d’expéditeurs protégés contre l’emprunt d’identité d’utilisateur est différente de la liste des **destinataires** à qui  la stratégie s’applique (tous les destinataires de la stratégie par défaut ; des destinataires spécifiques configurés dans le paramètre Appliqué à dans la section [Paramètres](#policy-settings) de stratégie).

  > [!NOTE]
  >
  > - Dans chaque stratégie anti-hameçonnage, vous pouvez spécifier un maximum de 60 utilisateurs protégés (adresses e-mail de l’expéditeur). Vous ne pouvez pas spécifier le même utilisateur protégé dans plusieurs stratégies. Ainsi, quel que soit le nombre de stratégies appliquées à un destinataire, le nombre maximal d’utilisateurs protégés (adresses e-mail de l’expéditeur) pour chaque destinataire individuel est de 60. Pour plus d’informations sur la priorité de stratégie et la façon dont le traitement de stratégie s’arrête après l’application de la première stratégie, voir Ordre et priorité de la [protection de la messagerie.](how-policies-and-protections-are-combined.md)
  >
  > - La protection contre l’emprunt d’identité d’utilisateur ne fonctionne pas si l’expéditeur et le destinataire ont précédemment communiqué par courrier électronique. Si l’expéditeur et le destinataire n’ont jamais communiqué par courrier électronique, le message est identifié comme une tentative d’emprunt d’identité.

  Par défaut, aucune adresse de messagerie de l’expéditeur n’est configurée pour la protection contre l’emprunt d’identité dans **Les utilisateurs à protéger.** Par conséquent, par défaut, aucune adresse de messagerie de l’expéditeur n’est couverte par la protection contre l’emprunt d’identité, que ce soit dans la stratégie par défaut ou dans les stratégies personnalisées.

  Lorsque vous ajoutez des adresses  de messagerie internes ou  externes à la liste Utilisateurs pour protéger, les messages de ces expéditeurs sont soumis à des vérifications de protection contre l’emprunt d’identité. L’emprunt d’identité  du message est vérifié  si le message est envoyé à un destinataire à qui la stratégie s’applique (tous les destinataires de la stratégie par défaut ; **Appliqué aux destinataires** dans les stratégies personnalisées). Si l’emprunt d’identité est détecté dans l’adresse e-mail de l’expéditeur, les actions de protection contre l’emprunt d’identité pour les utilisateurs sont appliquées au message (que faire avec le message, afficher ou non les conseils de sécurité des utilisateurs dont l’identité est usurpée, etc.).

- **Ajouter des domaines à protéger**: empêche **l’emprunt d’identité** des domaines spécifiés dans le domaine de l’expéditeur du message. Par exemple, tous les domaines que vous possédez (domaines[acceptés)](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)ou des domaines spécifiques (domaines que vous possédez ou domaines partenaires). Cette liste de domaines d’expéditeurs protégés contre l’emprunt d’identité est différente de la liste des **destinataires** à qui la  stratégie s’applique (tous les destinataires de la stratégie par défaut ; des destinataires spécifiques tels que configurés dans le paramètre Appliqué à dans la section [Paramètres](#policy-settings) de stratégie). 

  > [!NOTE]
  > Le nombre maximal de domaines protégés que vous pouvez définir dans toutes les stratégies anti-hameçonnage est de 50.

  Par défaut, aucun domaine d’expéditeur n’est configuré pour la protection contre l’emprunt d’identité dans **les domaines à protéger.** Par conséquent, par défaut, aucun domaine d’expéditeur n’est couvert par la protection contre l’emprunt d’identité, que ce soit dans la stratégie par défaut ou dans les stratégies personnalisées.

  Lorsque vous ajoutez des domaines à la liste **Domaines** pour protéger, les messages des expéditeurs de ces domaines sont soumis à des **vérifications** de protection contre l’emprunt d’identité. L’emprunt d’identité  du message est vérifié  si le message est envoyé à un destinataire à qui la stratégie s’applique (tous les destinataires de la stratégie par défaut ; **Appliqué aux destinataires** dans les stratégies personnalisées). Si l’emprunt d’identité est détecté dans le domaine de l’expéditeur, les actions de protection contre l’emprunt d’identité pour les domaines sont appliquées au message (que faire avec le message, afficher ou non les conseils de sécurité des utilisateurs usurpés, etc.).

- **Actions**: choisissez l’action à prendre sur les messages entrants qui contiennent des tentatives d’emprunt d’identité contre les utilisateurs protégés et les domaines protégés dans la stratégie. Vous pouvez spécifier différentes actions pour l’emprunt d’identité des utilisateurs protégés par rapport à l’emprunt d’identité de domaines protégés :

  - **Ne pas appliquer d’action**

  - **Rediriger le message vers** d’autres adresses e-mail : envoie le message aux destinataires spécifiés au lieu des destinataires prévus.

  - **Déplacer les messages vers les dossiers** Courrier indésirable des destinataires : le message est remis à la boîte aux lettres et déplacé vers le dossier Courrier indésirable. Dans Exchange Online, le message est déplacé vers le dossier Courrier indésirable si la règle de courrier indésirable est activée sur la boîte aux lettres (activée par défaut). Pour plus d’informations, voir [Configurer les paramètres](configure-junk-email-settings-on-exo-mailboxes.md)de courrier indésirable Exchange Online boîtes aux lettres dans Microsoft 365 .

  - **Mettre le message en** quarantaine : envoie le message en quarantaine au lieu des destinataires prévus. Pour plus d’informations sur la mise en quarantaine, consultez les articles suivants :
    - [Mise en quarantaine dans Microsoft 365](quarantine-email-messages.md)
    - [Gérer les fichiers et les messages mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Rechercher et libérer des messages mis en quarantaine en tant qu’utilisateur dans Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

  - **Remettre le message et** ajouter d’autres adresses à la ligne Bcc : remettre le message aux destinataires prévus et remettre silencieusement le message aux destinataires spécifiés.

  - **Supprimez le message avant qu’il ne soit** remis : supprime silencieusement l’intégralité du message, y compris toutes les pièces jointes.

- **Activer les conseils** de sécurité d’emprunt d’identité : activer ou désactiver les conseils de sécurité d’emprunt d’identité suivants qui s’affichent pour les messages qui échouent aux vérifications d’emprunt d’identité :
  - **Afficher le conseil pour les utilisateurs dont l’identité** a été usurpée : l’adresse De contient un utilisateur protégé.
  - **Afficher le conseil pour les domaines dont l’identité est usurpée**: l’adresse De contient un domaine protégé.
  - Conseil pour les caractères inhabituels : l’adresse De contient des jeux de caractères inhabituels (par exemple, des symboles mathématiques et du texte ou un mélange de lettres majuscules et minuscules) dans un expéditeur ou un domaine protégé.

  > [!IMPORTANT]
  >
  > Même lorsque les conseils de sécurité  d’emprunt d’identité sont désactivés, nous vous recommandons d’utiliser une règle de flux de messagerie (également appelée règle de transport) pour ajouter un en-tête de message nommé **X-MS-Exchange-EnableFirstContactSafetyTip** avec la valeur **activée** pour les messages. Un conseil de sécurité avertit les destinataires la première fois qu’ils obtiennent un message de l’expéditeur ou s’ils n’obtiennent pas souvent de messages de l’expéditeur. Cette fonctionnalité ajoute une couche supplémentaire de protection de sécurité contre les attaques d’emprunt d’identité potentielles.
  >
  > :::image type="content" source="../../media/safety-tip-first-contact-multiple-recipients.png" alt-text="Texte de l’conseil de sécurité protection contre l’emprunt d’identité avec plusieurs destinataires.":::

- **Intelligence de boîte** aux lettres : active ou désactive l’intelligence artificielle (IA) qui détermine les modèles de messagerie des utilisateurs avec leurs contacts fréquents. Ce paramètre permet à l’IA de faire la distinction entre les messages provenant d’expéditeurs légitimes et d’expéditeurs dont l’identité a été usurpée.

  Par exemple, Comme Elle (glaureano@contoso.com) est le PDG de votre entreprise, vous l’ajoutez  en tant qu’expéditeur protégé dans les utilisateurs pour protéger les paramètres de la stratégie. Toutefois, certains des destinataires que la stratégie s’applique pour communiquer régulièrement avec un fournisseur également nommé Glaureano@fabrikam.com). Étant donné que ces destinataires ont un historique des communications avec glaureano@fabrikam.com, l’intelligence des boîtes aux lettres n’identifie pas les messages provenant de glaureano@fabrikam.com comme une tentative d’emprunt d’glaureano@contoso.com pour ces destinataires.

  Pour utiliser des contacts fréquents qui ont été découverts par l’intelligence des boîtes aux lettres (et qui n’en  ont pas) pour protéger les utilisateurs contre les attaques d’emprunt d’identité, vous pouvez activer la **protection** contre l’emprunt d’identité basée sur l’intelligence des boîtes aux lettres et spécifier l’action à prendre si vous allumez également l’intelligence des boîtes aux **lettres.**

- **Protection contre l’emprunt** d’identité basée sur l’intelligence des boîtes aux lettres : activer ce paramètre pour spécifier l’action à prendre sur les messages pour les détections d’emprunt d’identité à partir des résultats de l’intelligence de boîte aux lettres :

  - **N’appliquez aucune action**: notez que cette  valeur a le même résultat que l’isation de la boîte aux lettres, mais la désélation de la protection contre l’usurpation d’identité basée sur l’intelligence des boîtes **aux lettres.**
  - **Rediriger le message vers d’autres adresses de messagerie**
  - **Déplacer le message vers les dossiers Courrier indésirable des destinataires**
  - **Mettre le message en quarantaine**
  - **Remettre le message et ajouter d’autres adresses à la ligne Bcc**
  - **Supprimer le message avant sa livraison**

- **Ajouter des expéditeurs et des domaines de confiance**: exceptions aux paramètres de protection contre l’emprunt d’identité. Les messages provenant des domaines des expéditeurs et des expéditeurs spécifiés ne sont jamais classés comme attaques basées sur l’emprunt d’identité par la stratégie. En d’autres termes, l’action pour les expéditeurs protégés, les domaines protégés ou la protection de l’intelligence des boîtes aux lettres n’est pas appliquée à ces expéditeurs ou domaines d’expéditeurs fiables. La limite maximale pour ces listes est d’environ 1 000 entrées.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Seuils de hameçonnage avancés dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Les seuils d’hameçonnage avancés suivants sont disponibles uniquement dans les stratégies anti-hameçonnage de Microsoft Defender Office 365. Ces seuils contrôlent la sensibilité à l’application de modèles d’apprentissage automatique aux messages pour déterminer un verdict de hameçonnage :

- **1 - Standard**: il s’agit de la valeur par défaut. La gravité de l’action entreprise sur le message dépend du degré de confiance que le message est un hameçonnage (faible, moyen, élevé ou très élevé). Par exemple, les messages identifiés comme étant du hameçonnage avec un très haut degré de confiance ont les actions les plus graves appliquées, tandis que les messages identifiés comme étant du hameçonnage avec un faible degré de confiance ont des actions moins graves appliquées.

- **2 - Agressif**: les messages identifiés comme du hameçonnage avec un haut degré de confiance sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.

- **3 - Plus** agressif : les messages identifiés comme étant du hameçonnage avec un niveau de confiance moyen ou élevé sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.

- **4 -** Plus agressif : les messages identifiés comme étant du hameçonnage avec un niveau de confiance faible, moyen ou élevé sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.

Le risque de faux positifs (messages positifs marqués comme faux) augmente lorsque vous augmentez ce paramètre. Pour plus d’informations sur les paramètres recommandés, consultez la stratégie [anti-hameçonnage](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)dans Microsoft Defender pour Office 365 paramètres.
