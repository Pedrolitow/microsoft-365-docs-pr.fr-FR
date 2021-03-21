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
ms.openlocfilehash: eeb15040f0e47f7d51852dadf68c4b0c37de0975
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50929227"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>Stratégies anti-hameçonnage dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Les stratégies de configuration des paramètres de protection anti-hameçonnage sont disponibles dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online, des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online et des organisations Microsoft Defender pour Office 365.

Les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 sont disponibles uniquement dans les organisations qui disposent de Defender pour Office 365. Par exemple :

- Microsoft 365 Entreprise E5, Microsoft 365 Éducation A5, etc.
- [Microsoft 365 Entreprise](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 Business](https://www.microsoft.com/microsoft-365/business)
- [Microsoft Defender pour Office 365 en tant que module ajouté](https://products.office.com/exchange/advance-threat-protection)

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
  - **Le domaine du destinataire** est : Un ou plusieurs domaines configurés acceptés dans Microsoft 365.

  - **Sauf quand**: exceptions pour la règle. Les paramètres et le comportement sont exactement comme les conditions :

    - **Le destinataire est**
    - **Le destinataire est membre de**
    - **Le domaine du destinataire est**

  > [!NOTE]
  > Le **paramètre Appliqué à** est requis dans les stratégies anti-hameçonnage personnalisées pour identifier les **destinataires** du message à qui la <u>stratégie s’applique.</u> Les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 ont également des [paramètres](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) d’emprunt d’identité dans lequel vous pouvez spécifier des adresses de messagerie d’expéditeur ou des domaines d’expéditeur individuels qui bénéficieront d’une <u>protection</u> contre l’emprunt d’identité, comme décrit plus loin dans cet article.

## <a name="spoof-settings"></a>Paramètres d’usurpation d’une usurpation

L’usurpation d’adresse est lorsque l’adresse De d’un message électronique (l’adresse de l’expéditeur qui s’affiche dans les clients de messagerie) ne correspond pas au domaine de la source de courrier. Pour plus d’informations sur l’usurpation d’informations, voir Protection contre l’usurpation d’informations [dans Microsoft 365.](anti-spoofing-protection.md)

Les paramètres d’usurpation suivants sont disponibles dans les stratégies anti-hameçonnage dans EOP et Microsoft Defender pour Office 365 :

- **Protection contre l’usurpation**: active ou désactive la protection contre l’usurpation d’usurpation d’accès. Nous vous recommandons de laisser ce dernier activé. Vous utilisez la stratégie **de veille** contre l’usurpation d’adresse pour autoriser ou bloquer des expéditeurs internes et externes usurpés spécifiques. Si vous souhaitez en savoir plus, consultez l’article [Configurer la veille contre l’usurpation d’identité dans Microsoft 365](learn-about-spoof-intelligence.md).

  > [!NOTE]
  >
  > - La protection contre l’usurpation d’emploi est activée par défaut dans la stratégie anti-hameçonnage par défaut et dans toutes les nouvelles stratégies anti-hameçonnage personnalisées que vous créez.
  >
  > - Vous n’avez pas besoin de désactiver la protection contre l’usurpation d’usurpation si votre enregistrement MX ne pointe pas vers Microsoft 365 ; vous activez le filtrage amélioré pour les connecteurs à la place. Pour obtenir des instructions, voir [Filtrage amélioré pour les connecteurs dans Exchange Online.](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)
  >
  > - La désactivation de la protection contre l’usurpation d’identité désactive uniquement la protection implicite contre l’usurpation d’identité contre les vérifications [d’authentification composite.](email-validation-and-authentication.md#composite-authentication) Si l’expéditeur échoue aux vérifications [DMARC](use-dmarc-to-validate-email.md) explicites lorsque la stratégie est définie sur mise en quarantaine ou rejet, le message est toujours mis en quarantaine ou rejeté.

  Pour les messages provenant d’expéditeurs usurpés bloqués, vous pouvez également spécifier l’action à prendre sur les messages :

  - **Déplacer le message vers le dossier Courrier indésirable**: il s’agit de la valeur par défaut. Le message est remis à la boîte aux lettres et déplacé vers le dossier Courrier indésirable. Dans Exchange Online, le message est déplacé vers le dossier Courrier indésirable si la règle de courrier indésirable est activée sur la boîte aux lettres (activée par défaut). Pour plus d’informations, voir Configurer les paramètres de courrier indésirable sur les boîtes aux lettres [Exchange Online dans Microsoft 365.](configure-junk-email-settings-on-exo-mailboxes.md)

  - **Mettre le message en** quarantaine : envoie le message en quarantaine au lieu des destinataires prévus. Pour plus d’informations sur la mise en quarantaine, consultez les articles suivants :

    - [Mise en quarantaine dans Microsoft 365](quarantine-email-messages.md)
    - [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Rechercher et libérer des messages mis en quarantaine en tant qu’utilisateur dans Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

- **Expéditeur non authentifié :** consultez les informations de la section suivante.

### <a name="unauthenticated-sender"></a>Expéditeur non authentifié

L’identification de l’expéditeur non authentifié fait partie des paramètres d’usurpation d’identité disponibles dans les [stratégies](#spoof-settings) anti-hameçonnage dans EOP et Microsoft Defender pour Office 365, comme décrit dans la section précédente.

Le paramètre Expéditeur non **authentifié** active ou désactive l’identification de l’expéditeur non authentifié dans Outlook. Notamment :

- Un point d’interrogation (?) est ajouté à la photo de l’expéditeur si  le message ne passe pas les vérifications SPF ou DKIM et s’il ne passe pas l’authentification DMARC ou [composite.](email-validation-and-authentication.md#composite-authentication) La désactivation de l’identification de l’expéditeur non authentifié empêche l’ajout du point d’interrogation à la photo de l’expéditeur.

- La balise via (chris@contoso.com <u>via</u> fabrikam.com) est ajoutée si le domaine dans l’adresse De (l’expéditeur du message affiché dans les clients de messagerie) est différent du domaine dans la signature DKIM ou l’adresse **MAIL FROM.** Pour plus d’informations sur ces adresses, voir [une vue d’ensemble des normes de message électronique.](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards)

  La désactivation de l’identification de l’expéditeur non authentifié n’empêche pas l’ajout de la balise via si le domaine dans l’adresse De est différent du domaine dans la signature DKIM ou l’adresse MAIL FROM.

Pour empêcher l’ajout du point d’interrogation ou d’une balise à des messages provenant d’expéditeurs spécifiques, vous avez les options suivantes :

- Autorisez l’expéditeur à usurper l’adresse dans la stratégie d’usurpation d’informations. Cette action empêche l’apparition de la balise via dans les messages de l’expéditeur lorsque l’identification de l’expéditeur non authentifié est désactivée. Pour obtenir des instructions, voir [Configurer la veille contre l’usurpation d’informations dans Microsoft 365.](learn-about-spoof-intelligence.md)

- [Configurez l’authentification de messagerie](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own) pour le domaine de l’expéditeur.
  - Pour le point d’interrogation dans la photo de l’expéditeur, SPF ou DKIM sont les plus importants.
  - Pour la balise via, confirmez que le domaine dans la signature DKIM ou l’adresse **MAIL FROM** correspond (ou est un sous-domaine) du domaine dans l’adresse De.

Pour plus d’informations, voir Identifier les messages suspects [dans Outlook.com et Outlook sur le web](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206)

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres exclusifs dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Cette section décrit les paramètres de stratégie disponibles uniquement dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.

> [!NOTE]
> La stratégie anti-hameçonnage par défaut dans Microsoft Defender pour Office 365 fournit une [protection](set-up-anti-phishing-policies.md#spoof-settings) contre l’usurpation d’adresse et une intelligence des boîtes aux lettres pour tous les destinataires. Toutefois, les autres fonctionnalités de [protection](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) contre l’emprunt d’identité disponibles et les paramètres avancés ne sont pas [configurés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ou activés dans la stratégie par défaut. Pour activer toutes les fonctionnalités de protection, modifiez la stratégie anti-hameçonnage par défaut ou créez des stratégies anti-hameçonnage supplémentaires.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

L’emprunt d’identité est l’endroit où l’expéditeur ou le domaine de messagerie de l’expéditeur dans un message ressemble à un expéditeur ou un domaine réel :

- Un exemple d'usurpation de l'identité du domaine contoso.com est ćóntoso.com.
- Un exemple d'usurpation de l'identité de l'utilisateur michelle@contoso.com est michele@contoso.com.

Un domaine usurpé pourrait autrement être considéré comme légitime (domaine enregistré, enregistrements d'authentification de courrier électronique configurés, etc.), sauf si son but est de tromper les destinataires.

Les paramètres d’emprunt d’identité suivants sont disponibles uniquement dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 :

- **Utilisateurs à protéger**: empêche les adresses de messagerie internes ou externes spécifiées d’être usurpées en tant **qu’expéditeurs de messages.** Par exemple, vous recevez un message électronique du vice-président de votre entreprise vous demandant d’envoyer des informations internes à l’entreprise. Le feriez-vous ? De nombreuses personnes envoient la réponse sans réfléchir.

  Vous pouvez utiliser des utilisateurs protégés pour ajouter des adresses de messagerie d’expéditeur internes et externes afin de vous protéger contre l’emprunt d’identité. Cette liste  d’expéditeurs protégés contre l’emprunt d’identité d’utilisateur est différente de la liste des **destinataires** à qui  la stratégie s’applique (tous les destinataires de la stratégie par défaut ; des destinataires spécifiques configurés dans le paramètre Appliqué à dans la section [Paramètres](#policy-settings) de stratégie).

  > [!NOTE]
  >
  > - Dans chaque stratégie anti-hameçonnage, vous pouvez spécifier un maximum de 60 utilisateurs protégés (adresses e-mail de l’expéditeur). Vous ne pouvez pas spécifier le même utilisateur protégé dans plusieurs stratégies. Ainsi, quel que soit le nombre de stratégies appliquées à un destinataire, le nombre maximal d’utilisateurs protégés (adresses e-mail de l’expéditeur) pour chaque destinataire individuel est de 60. Pour plus d’informations sur la priorité de stratégie et la façon dont le traitement des stratégies s’arrête après l’application de la première stratégie, voir Ordre et priorité [de la protection du courrier électronique.](how-policies-and-protections-are-combined.md)
  >
  > - La protection contre l’emprunt d’identité d’utilisateur ne fonctionne pas si l’expéditeur et le destinataire ont précédemment communiqué par courrier électronique. Si l’expéditeur et le destinataire n’ont jamais communiqué par courrier électronique, le message est identifié comme une tentative d’emprunt d’identité.

  Par défaut, aucune adresse de messagerie de l’expéditeur n’est configurée pour la protection contre l’emprunt d’identité dans **Les utilisateurs à protéger.** Par conséquent, par défaut, aucune adresse de messagerie de l’expéditeur n’est couverte par la protection contre l’emprunt d’identité, que ce soit dans la stratégie par défaut ou dans les stratégies personnalisées.

  Lorsque vous ajoutez des adresses  de messagerie internes ou  externes à la liste Utilisateurs pour protéger, les messages de ces expéditeurs sont soumis à des vérifications de protection contre l’emprunt d’identité. L’emprunt d’identité  du message est vérifié  si le message est envoyé à un destinataire à qui la stratégie s’applique (tous les destinataires de la stratégie par défaut ; **Appliqué aux destinataires** dans les stratégies personnalisées). Si l’emprunt d’identité est détecté dans l’adresse e-mail de l’expéditeur, les actions de protection contre l’emprunt d’identité pour les utilisateurs sont appliquées au message (que faire avec le message, afficher ou non les conseils de sécurité des utilisateurs usurpés, etc.).

- **Domaines à protéger :** empêche les domaines spécifiés d’être usurpés dans le domaine de **l’expéditeur du message.** Par exemple, tous les domaines que vous possédez (domaines[acceptés)](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)ou des domaines spécifiques (domaines que vous possédez ou domaines partenaires). Cette liste de domaines d’expéditeurs protégés contre l’emprunt d’identité est différente de la liste des **destinataires** à qui la  stratégie s’applique (tous les destinataires de la stratégie par défaut ; des destinataires spécifiques tels que configurés dans le paramètre Appliqué à dans la section [Paramètres](#policy-settings) de stratégie). 

  > [!NOTE]
  > Le nombre maximal de domaines protégés que vous pouvez définir dans toutes les stratégies anti-hameçonnage est de 50.

  Par défaut, aucun domaine d’expéditeur n’est configuré pour la protection contre l’emprunt d’identité dans **les domaines à protéger.** Par conséquent, par défaut, aucun domaine d’expéditeur n’est couvert par la protection contre l’emprunt d’identité, que ce soit dans la stratégie par défaut ou dans les stratégies personnalisées.

  Lorsque vous ajoutez des domaines à la liste **Domaines** pour protéger, les messages des expéditeurs de ces domaines sont soumis à des **vérifications** de protection contre l’emprunt d’identité. L’emprunt d’identité  du message est vérifié  si le message est envoyé à un destinataire à qui la stratégie s’applique (tous les destinataires de la stratégie par défaut ; **Appliqué aux destinataires** dans les stratégies personnalisées). Si l’emprunt d’identité est détecté dans le domaine de l’expéditeur, les actions de protection contre l’emprunt d’identité pour les domaines sont appliquées au message (que faire avec le message, afficher ou non les conseils de sécurité des utilisateurs usurpés, etc.).

- Actions pour les **utilisateurs** ou les domaines protégés : choisissez l’action à prendre sur les messages entrants qui contiennent des tentatives d’emprunt d’identité contre les utilisateurs protégés et les domaines protégés dans la stratégie. Vous pouvez spécifier différentes actions pour l’emprunt d’identité des utilisateurs protégés par rapport à l’emprunt d’identité des domaines protégés :

  - **Ne pas appliquer d’action**

  - **Rediriger le message vers** d’autres adresses e-mail : envoie le message aux destinataires spécifiés au lieu des destinataires prévus.

  - **Déplacer le message vers le dossier Courrier** indésirable : le message est remis à la boîte aux lettres et déplacé vers le dossier Courrier indésirable. Dans Exchange Online, le message est déplacé vers le dossier Courrier indésirable si la règle de courrier indésirable est activée sur la boîte aux lettres (activée par défaut). Pour plus d’informations, voir Configurer les paramètres de courrier indésirable sur les boîtes aux lettres [Exchange Online dans Microsoft 365.](configure-junk-email-settings-on-exo-mailboxes.md)

    - **Mettre le message en** quarantaine : envoie le message en quarantaine au lieu des destinataires prévus. Pour plus d’informations sur la mise en quarantaine, consultez les articles suivants :

    - [Mise en quarantaine dans Microsoft 365](quarantine-email-messages.md)
    - [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Rechercher et libérer des messages mis en quarantaine en tant qu’utilisateur dans Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

  - **Remettre le message et ajouter** d’autres adresses à la ligne Bcc : remettre le message aux destinataires prévus et remettre silencieusement le message aux destinataires spécifiés.

  - **Supprimez le message avant qu’il ne soit** remis : supprime silencieusement l’intégralité du message, y compris toutes les pièces jointes.

- **Conseils de sécurité**: active ou désactive les conseils de sécurité d’emprunt d’identité suivants qui s’affichent pour les messages qui échouent aux vérifications d’emprunt d’identité :

  - **Utilisateurs usurpés :** l’adresse De contient un utilisateur protégé.
  - **Domaines usurpés :** l’adresse De contient un domaine protégé.
  - **Caractères inhabituels**: l’adresse De contient des jeux de caractères inhabituels (par exemple, des symboles mathématiques et du texte ou un mélange de lettres majuscules et minuscules) dans un expéditeur ou un domaine protégé.


  > [!IMPORTANT]
  >
  > Recommandation pour l’activation d’un conseil de sécurité qui s’affiche lors du premier contact entre l’expéditeur et le ou les destinataires : même lorsque les conseils de sécurité d’emprunt d’identité sont désactivés, nous vous  recommandons d’utiliser une règle de flux de messagerie (également appelée règle de transport) pour ajouter un **en-tête** de message nommé **X-MS-Exchange-EnableFirstContactSafetyTip** avec valeur activée pour les messages.  Un conseil de sécurité avertit les destinataires la première fois qu’ils obtiennent un message de l’expéditeur ou s’ils n’obtiennent pas souvent de messages de l’expéditeur. Cette fonctionnalité ajoute une couche supplémentaire de protection de sécurité contre les attaques d’emprunt d’identité potentielles. 
  > :::image type="content" source="../../media/safety-tip-first-contact-multiple-recipients.png" alt-text="Texte du conseil de sécurité pour la protection contre l’emprunt d’identité avec plusieurs destinataires.":::

- **Intelligence de boîte** aux lettres : active ou désactive l’intelligence artificielle (IA) qui détermine les modèles de messagerie des utilisateurs avec leurs contacts fréquents. Ce paramètre permet à l’IA de faire la distinction entre les messages électroniques légitimes et usurpés de ces contacts. La veille de boîte aux lettres est disponible uniquement pour les boîtes aux lettres Exchange Online.

- **Protection contre l’emprunt** d’identité basée sur l’intelligence des boîtes aux lettres : active ou désactive les résultats d’emprunt d’identité améliorés en fonction de la carte d’expéditeur individuelle de chaque utilisateur. Cette intelligence permet à Microsoft 365 de personnaliser la détection d’emprunt d’identité d’utilisateur et de mieux gérer les faux positifs. Lorsque l’emprunt d’identité d’utilisateur est détecté, vous pouvez définir une action spécifique à prendre sur le message :

  - **Ne pas appliquer d’action**
  - **Rediriger le message vers d’autres adresses de messagerie**
  - **Déplacer le message dans le dossier Courrier indésirable**
  - **Mettre le message en quarantaine**
  - **Remettre le message et ajouter d’autres adresses à la ligne Bcc**
  - **Supprimer le message avant sa livraison**

- **Expéditeurs et domaines de confiance**: exceptions aux paramètres de protection contre l’emprunt d’identité. Les messages provenant des domaines des expéditeurs et des expéditeurs spécifiés ne sont jamais classés comme attaques basées sur l’emprunt d’identité par la stratégie. En d’autres termes, l’action pour les expéditeurs protégés, les domaines protégés ou la protection de l’intelligence des boîtes aux lettres n’est pas appliquée à ces expéditeurs ou domaines d’expéditeurs fiables. La limite maximale pour ces listes est d’environ 1 000 entrées.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Seuils de hameçonnage avancés dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Les seuils de hameçonnage avancés suivants sont disponibles uniquement dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365. Ces seuils contrôlent la sensibilité à l’application de modèles d’apprentissage automatique aux messages pour déterminer un verdict de hameçonnage :

- **1 - Standard**: il s’agit de la valeur par défaut. La gravité de l’action entreprise sur le message dépend du degré de confiance que le message est un hameçonnage (faible, moyen, élevé ou très élevé). Par exemple, les messages identifiés comme étant du hameçonnage avec un très haut degré de confiance ont les actions les plus graves appliquées, tandis que les messages identifiés comme étant du hameçonnage avec un faible degré de confiance ont des actions moins graves appliquées.

- **2 - Agressif**: les messages identifiés comme du hameçonnage avec un haut degré de confiance sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.

- **3 - Plus** agressif : les messages identifiés comme étant du hameçonnage avec un niveau de confiance moyen ou élevé sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.

- **4 -** Plus agressif : les messages identifiés comme étant du hameçonnage avec un niveau de confiance faible, moyen ou élevé sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.

Le risque de faux positifs (messages positifs marqués comme faux) augmente lorsque vous augmentez ce paramètre. Pour plus d’informations sur les paramètres recommandés, voir la stratégie [anti-hameçonnage dans Microsoft Defender pour les paramètres Office 365.](recommended-settings-for-eop-and-office365-atp.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)