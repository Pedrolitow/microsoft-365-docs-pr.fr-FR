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
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 5a6f2d7f-d998-4f31-b4f5-f7cbf6f38578
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les stratégies anti-hameçonnage disponibles dans Exchange Online Protection (EOP) et Microsoft Defender pour Office 365.
ms.openlocfilehash: b54f452fb984f61913f2ade53ad45ed169a43832
ms.sourcegitcommit: f941495e9257a0013b4a6a099b66c649e24ce8a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48993353"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>Stratégies anti-hameçonnage dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Les stratégies de configuration des paramètres de protection anti-hameçonnage sont disponibles dans les organisations Microsoft 365 avec les boîtes aux lettres Exchange Online, les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online et les organisations Microsoft Defender pour Office 365.

Les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 sont disponibles uniquement dans les organisations qui disposent de Defender pour Office 365. Par exemple :

- Microsoft 365 entreprise E5, Microsoft 365 éducation a5, etc.
- [Microsoft 365 Entreprise](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 Business](https://www.microsoft.com/microsoft-365/business)
- [Microsoft Defender pour Office 365 en tant que module complémentaire](https://products.office.com/exchange/advance-threat-protection)

Les principales différences entre les stratégies de détection d’hameçonnage dans les stratégies EOP et anti-hameçonnage dans Microsoft Defender pour Office 365 sont décrites dans le tableau suivant :

****

|Fonctionnalité|Stratégies de détection d’hameçonnage dans EOP|Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365|
|---|:---:|:---:|
|Stratégie par défaut créée automatiquement|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|Créer des stratégies personnalisées|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|Paramètres de stratégie<sup>\*</sup>|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|Paramètres d’emprunt d’identité||![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|Paramètres d’usurpation|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|Seuils de hameçonnage avancés||![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|

<sup>\*</sup> Dans la stratégie par défaut, le nom et la description de la stratégie sont en lecture seule (la description est vide), et vous ne pouvez pas spécifier à qui la stratégie s’applique (la stratégie par défaut s’applique à tous les destinataires).

Pour configurer les stratégies anti-hameçonnage, consultez les articles suivants :

- [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)

- [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-atp-anti-phishing-policies.md)

Le reste de cet article décrit les paramètres disponibles dans les stratégies de détection d’hameçonnage dans EOP et Defender pour Office 365.

## <a name="policy-settings"></a>Paramètres de stratégie

Les paramètres de stratégie suivants sont disponibles dans les stratégies de détection d’hameçonnage dans EOP et Microsoft Defender pour Office 365 :

- **Name** : vous ne pouvez pas renommer la stratégie anti-hameçonnage par défaut, mais vous pouvez nommer et renommer les stratégies personnalisées que vous créez.

- **Description** Vous ne pouvez pas ajouter de description à la stratégie anti-hameçonnage par défaut, mais vous pouvez ajouter et modifier la description des stratégies personnalisées que vous créez.

- **Appliqué à** : identifie les destinataires internes auxquels s’applique la stratégie anti-hameçonnage. Cette valeur est requise dans les stratégies personnalisées et n’est pas disponible dans la stratégie par défaut (la stratégie par défaut s’applique à tous les destinataires).

  Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_ ). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_ ).

  - **Destinataire** : une ou plusieurs boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie dans votre organisation.
  - Le **destinataire est membre de** : un ou plusieurs groupes de votre organisation.
  - **Le domaine du destinataire est** : un ou plusieurs domaines acceptés configurés dans Microsoft 365.

  - **Sauf** dans les cas suivants : exceptions pour la règle. Les paramètres et le comportement sont exactement comme les conditions :

    - **Le destinataire est**
    - **Le destinataire est membre de**
    - **Le domaine du destinataire est**

  > [!NOTE]
  > Le paramètre **appliqué à** est requis dans les stratégies anti-hameçonnage personnalisées pour identifier les **destinataires** <u>de messages auxquels la stratégie s’applique</u>. Les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 ont également des [paramètres d’emprunt d’identité](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) dans lesquels vous pouvez spécifier des adresses de messagerie d’expéditeur ou des domaines d’expéditeur <u>qui recevront une protection contre l’emprunt d’identité</u> , comme décrit plus loin dans cette rubrique.

## <a name="spoof-settings"></a>Paramètres d’usurpation

L’usurpation se fait lorsque l’adresse de l’expéditeur d’un message électronique (l’adresse de l’expéditeur affichée dans les clients de messagerie) ne correspond pas au domaine de la source de messagerie. Pour plus d’informations sur l’usurpation, consultez la rubrique [protection contre l’usurpation d’identité dans Microsoft 365](anti-spoofing-protection.md).

Les paramètres d’usurpation suivants sont disponibles dans les stratégies de détection d’hameçonnage dans EOP et Microsoft Defender pour Office 365 :

- **Protection** contre l’usurpation d’identité : active ou désactive la protection contre l’usurpation d’identité. Nous vous recommandons de le laisser activé. Vous utilisez la **stratégie** d’aide à la décision pour autoriser ou bloquer des expéditeurs internes et externes falsifiés spécifiques. Si vous souhaitez en savoir plus, consultez l’article [Configurer la veille contre l’usurpation d’identité dans Microsoft 365](learn-about-spoof-intelligence.md).

  > [!NOTE]
  >
  > - La protection contre l’usurpation d’identité est activée par défaut dans la stratégie anti-hameçonnage par défaut et dans toute nouvelle stratégie anti-hameçonnage personnalisée que vous créez.
  >
  > - Vous n’avez pas besoin de désactiver la protection contre l’usurpation d’identité si votre enregistrement MX ne pointe pas vers Microsoft 365 ; vous activez le filtrage amélioré pour les connecteurs à la place. Pour obtenir des instructions, voir [Enhanced Filtering for Connectors in Exchange Online](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

  Pour les messages provenant d’expéditeurs usurpés bloqués, vous pouvez également spécifier l’action à effectuer sur les messages :

  - **Déplacer le message vers le dossier courrier indésirable** : il s’agit de la valeur par défaut. Le message est remis à la boîte aux lettres et déplacé vers le dossier courrier indésirable. Dans Exchange Online, le message est déplacé vers le dossier courrier indésirable si la règle de courrier indésirable est activée dans la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, consultez la rubrique [configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

  - **Mettre en quarantaine le message** : envoie le message en quarantaine au lieu des destinataires prévus. Pour plus d’informations sur la mise en quarantaine, consultez les articles suivants :

    - [Mise en quarantaine dans Microsoft 365](quarantine-email-messages.md)
    - [Gérer les messages et les fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

- **Expéditeur non authentifié** : consultez les informations de la section suivante.

### <a name="unauthenticated-sender"></a>Expéditeur non authentifié

L’identification de l’expéditeur non authentifié fait partie des [paramètres d’usurpation d’identité](#spoof-settings) disponibles dans les stratégies de détection d’hameçonnage dans EOP et Microsoft Defender pour Office 365, comme décrit dans la section précédente.

Le paramètre **expéditeur non authentifié** active ou désactive l’identification de l’expéditeur non authentifié dans Outlook. Notamment :

- Un point d’interrogation ( ?) est ajouté à la photo de l’expéditeur si le message ne passe pas les vérifications SPF ou DKIM **et** que le message ne passe pas l’authentification DMARC ou [composite](email-validation-and-authentication.md#composite-authentication). La désactivation de l’identification de l’expéditeur non authentifié empêche l’ajout du point d’interrogation à la photo de l’expéditeur.

- La balise via (chris@contoso.com <u>via</u> Michelle@fabrikam.com) est ajoutée si le domaine de l’adresse de provenance (l’expéditeur du message affiché dans les clients de messagerie) est différent du domaine dans la signature DKIM ou l’adresse **de provenance du courrier** . Pour plus d’informations sur ces adresses, consultez la rubrique [vue d’ensemble des normes relatives aux messages électroniques](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

  La désactivation de l’identification de l’expéditeur non authentifié n’empêche pas l’ajout de la balise via si le domaine de l’adresse de l’expéditeur est différent du domaine dans la signature DKIM ou l’adresse de l’expéditeur du message.

Pour empêcher l’ajout d’un point d’interrogation ou d’une balise à des messages provenant d’expéditeurs spécifiques, vous disposez des options suivantes :

- Autoriser l’expéditeur à usurper la stratégie d’intelligence d’usurpation d’identité. Cette action empêche l’affichage de la balise via dans les messages provenant de l’expéditeur lorsque l’identification de l’expéditeur non authentifié est désactivée. Pour obtenir des instructions, consultez la rubrique [configure usurpation Intelligence in Microsoft 365](learn-about-spoof-intelligence.md).

- [Configurez l’authentification de messagerie](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own) pour le domaine de l’expéditeur.
  
  - Pour le point d’interrogation de la photo de l’expéditeur, SPF ou DKIM sont les plus importants.
  - Pour la balise via, vérifiez le domaine dans la signature DKIM ou l’adresse **Mail from** correspond (ou est un sous-domaine du) au domaine dans l’adresse de l’expéditeur.

Pour plus d’informations, consultez [la rubrique identifier les messages suspects dans Outlook.com et Outlook sur le Web](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206) .

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres exclusifs dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Cette section décrit les paramètres de stratégie qui sont disponibles uniquement dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.

> [!NOTE]
> Par défaut, les paramètres exclusifs de l’option Defender pour Office 365 ne sont pas configurés ou activés, même dans la stratégie par défaut. Pour tirer parti de ces fonctionnalités, vous devez les activer et les configurer dans la stratégie anti-hameçonnage par défaut ou créer et configurer des stratégies anti-hameçonnage personnalisées.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

L’emprunt d’identité est l’endroit où l’expéditeur ou le domaine de messagerie de l’expéditeur d’un message doit ressembler à un expéditeur ou un domaine réel :

- Un exemple d'usurpation de l'identité du domaine contoso.com est ćóntoso.com.
- Un exemple d'usurpation de l'identité de l'utilisateur michelle@contoso.com est michele@contoso.com.

Un domaine usurpé pourrait autrement être considéré comme légitime (domaine enregistré, enregistrements d'authentification de courrier électronique configurés, etc.), sauf si son but est de tromper les destinataires.

Les paramètres d’emprunt d’identité suivants sont disponibles uniquement dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 :

- **Utilisateurs à protéger** : empêche l’usurpation d’identité des adresses de messagerie internes ou externes spécifiées **en tant qu’expéditeurs de messages**. Par exemple, vous recevez un message électronique du vice-président de votre société qui vous demande d’envoyer des informations internes sur l’entreprise. Voulez-vous le faire ? De nombreuses personnes envoient la réponse sans l’avoir pensée.

  Vous pouvez utiliser des utilisateurs protégés pour ajouter des adresses de messagerie d’expéditeurs internes et externes afin de protéger l’emprunt d’identité. Cette liste d' **expéditeurs** protégés de l’emprunt d’identité de l’utilisateur est différente de la liste des **destinataires** auxquels la stratégie s’applique (tous les destinataires de la stratégie par défaut ; des destinataires spécifiques, comme configuré dans le paramètre **appliqué à** dans la section [paramètres de stratégie](#policy-settings) ).

  > [!NOTE]
  >
  > - Dans chaque stratégie anti-hameçonnage, vous pouvez spécifier un maximum de 60 utilisateurs protégés (adresses e-mail de l’expéditeur). Vous ne pouvez pas spécifier le même utilisateur protégé dans plusieurs stratégies.
  >
  > - La protection contre l’usurpation d’identité d’utilisateur ne fonctionne pas si l’expéditeur et le destinataire ont déjà communiqué par courrier électronique. Si l’expéditeur et le destinataire n’ont jamais communiqué par courrier électronique, le message est identifié en tant que tentative d’emprunt d’identité.

  Par défaut, aucune adresse de messagerie d’expéditeur n’est configurée pour la protection contre l’emprunt d’identité des **utilisateurs pour protéger**. Par conséquent, par défaut, aucune adresse de messagerie d’expéditeur n’est couverte par la protection contre l’emprunt d’identité, soit dans la stratégie par défaut, soit dans des stratégies personnalisées.

  Lorsque vous ajoutez des adresses de messagerie électronique internes ou externes aux **utilisateurs pour protéger** la liste, les messages provenant de ces **expéditeurs** sont soumis aux contrôles de protection contre l’emprunt d’identité. Le message est vérifié pour l’emprunt d’identité **si** le message est envoyé à un **destinataire** auquel la stratégie s’applique (tous les destinataires de la stratégie par défaut ; **S’applique aux** destinataires dans les stratégies personnalisées). Si l’emprunt d’identité est détecté dans l’adresse de messagerie de l’expéditeur, les actions de protection contre l’emprunt d’identité pour les utilisateurs sont appliquées au message (ce qu’il faut faire avec le message, s’il faut afficher les conseils de sécurité des utilisateurs empruntés, etc.).

- **Domaines à protéger** : empêche l’emprunt d’identité des domaines spécifiés **dans le domaine de l’expéditeur du message**. Par exemple, tous les domaines que vous possédez ([domaines acceptés](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)) ou des domaines spécifiques (domaines que vous possédez ou domaines partenaires). Cette liste de **domaines d’expéditeur** protégés de l’emprunt d’identité est différente de la liste des **destinataires** auxquels la stratégie s’applique (tous les destinataires de la stratégie par défaut ; des destinataires spécifiques tels que configurés dans le paramètre **appliqué à** dans la section [paramètres de stratégie](#policy-settings) ).

  > [!NOTE]
  > Le nombre maximal de domaines protégés que vous pouvez définir dans toutes les stratégies de protection contre le hameçonnage est de 50.

  Par défaut, aucun domaine d’expéditeur n’est configuré pour la protection contre l’emprunt d’identité dans les **domaines à protéger**. Par conséquent, par défaut, aucun domaine d’expéditeur n’est couvert par la protection contre l’emprunt d’identité, soit dans la stratégie par défaut, soit dans des stratégies personnalisées.

  Lorsque vous ajoutez des domaines à la liste **domaines à protéger** , les messages provenant d' **expéditeurs de ces domaines** sont soumis aux contrôles de protection contre l’emprunt d’identité. Le message est vérifié pour l’emprunt d’identité **si** le message est envoyé à un **destinataire** auquel la stratégie s’applique (tous les destinataires de la stratégie par défaut ; **S’applique aux** destinataires dans les stratégies personnalisées). Si l’emprunt d’identité est détecté dans le domaine de l’expéditeur, les actions de protection contre l’emprunt d’identité pour les domaines sont appliquées au message (ce qu’il faut faire avec le message, s’il faut afficher les conseils de sécurité des utilisateurs empruntés, etc.).

- **Actions pour les utilisateurs ou domaines protégés** : choisissez l’action à effectuer sur les messages entrants qui contiennent des tentatives d’emprunt d’identité pour les utilisateurs protégés et les domaines protégés de la stratégie. Vous pouvez spécifier différentes actions pour l’emprunt d’identité des utilisateurs protégés et l’emprunt d’identité des domaines protégés :

  - **Ne pas appliquer d’action**

  - **Rediriger le message vers d’autres adresses de messagerie** : envoie le message aux destinataires spécifiés au lieu des destinataires prévus.

  - **Déplacer le message vers le dossier courrier indésirable** : le message est remis à la boîte aux lettres et déplacé vers le dossier courrier indésirable. Dans Exchange Online, le message est déplacé vers le dossier courrier indésirable si la règle de courrier indésirable est activée dans la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, consultez la rubrique [configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

    - **Mettre en quarantaine le message** : envoie le message en quarantaine au lieu des destinataires prévus. Pour plus d’informations sur la mise en quarantaine, consultez les articles suivants :

    - [Mise en quarantaine dans Microsoft 365](quarantine-email-messages.md)
    - [Gérer les messages et les fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

  - **Remise du message et ajout d’autres adresses à la ligne CCI** : remet le message aux destinataires concernés et remet en silence le message aux destinataires spécifiés.

  - **Supprimer le message avant qu’il ne soit remis** : supprime silencieusement le message entier, y compris toutes les pièces jointes.

- **Conseils de sécurité** : active ou désactive les conseils de sécurité d’emprunt d’identité suivants qui apparaîtront pour les messages qui échouent aux vérifications de l’emprunt d’identité :

  - **Utilisateurs empruntés** : l’adresse de l’utilisateur contient un utilisateur protégé.
  - **Domaines empruntés** : l’adresse de provenance contient un domaine protégé.
  - **Caractères inhabituels** : l’adresse de l’expéditeur contient des jeux de caractères inhabituels (par exemple, des symboles mathématiques, du texte ou une combinaison de majuscules et minuscules) dans un expéditeur ou un domaine protégé.

  > [!NOTE]
  > Même lorsque les conseils de sécurité pour l’emprunt d’identité sont désactivés, vous pouvez utiliser une règle de flux de messagerie (également appelée règle de transport) pour ajouter un en-tête de message nommé **X-MS-Exchange-EnableFirstContactSafetyTip** aux messages. Des conseils de sécurité spécifiques seront affichés pour avertir les destinataires qu’ils ne reçoivent pas de courrier électronique de l’expéditeur ou dans les cas où le destinataire reçoit un message électronique pour la première fois de l’expéditeur.

- **Intelligence des boîtes aux lettres** : active ou désactive l’intelligence artificielle (ai) qui détermine les modèles de courrier des utilisateurs avec leurs contacts fréquents. Ce paramètre permet à l’AI de faire la distinction entre les messages légitimes et falsifiés de ces contacts. La boîte aux lettres n’est disponible que pour les boîtes aux lettres Exchange Online.

- **Protection contre l’usurpation d’identité basée sur les boîtes aux lettres** : active ou désactive les résultats d’emprunt d’identité améliorés en fonction du mappage d’expéditeur individuel de chaque utilisateur. Cette intelligence permet à Microsoft 365 de personnaliser la détection de l’emprunt d’identité de l’utilisateur et de mieux gérer les faux positifs. Lorsque l’emprunt d’identité de l’utilisateur est détecté, vous pouvez définir une action spécifique à effectuer sur le message :

  - **Ne pas appliquer d’action**
  - **Rediriger le message vers d’autres adresses de messagerie**
  - **Déplacer le message dans le dossier Courrier indésirable**
  - **Mettre en quarantaine le message**
  - **Remise du message et ajout d’autres adresses à la ligne CCI**
  - **Supprimer le message avant qu’il ne soit remis**

- **Expéditeurs et domaines approuvés** : exceptions aux paramètres de protection contre l’emprunt d’identité. Les messages provenant des domaines des expéditeurs et des expéditeurs spécifiés ne sont jamais classés comme attaques par emprunt d’identité par la stratégie. En d’autres termes, l’action pour les expéditeurs protégés, les domaines protégés ou la protection contre les boîtes aux lettres n’est pas appliquée à ces expéditeurs approuvés ou domaines d’expéditeurs. La limite maximale de ces listes est d’environ 1000 entrées.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Seuils de hameçonnage avancés dans les stratégies de détection d’hameçonnage dans Microsoft Defender pour Office 365

Les seuils de hameçonnage avancés suivants sont disponibles uniquement dans les stratégies anti-hameçonnage de Microsoft Defender pour Office 365. Ces seuils contrôlent la sensibilité pour l’application des modèles d’apprentissage automatique aux messages permettant de déterminer un verdict de phishing :

- **1-standard** : il s’agit de la valeur par défaut. La gravité de l’action effectuée sur le message dépend du degré de certitude que le message est de type hameçonnage (faible, moyenne, haute ou très élevée). Par exemple, les messages qui sont identifiés comme un hameçonnage avec un degré de confiance très élevé ont les actions les plus graves appliquées, tandis que les messages identifiés comme du hameçonnage avec un faible degré de confiance ont des actions moins graves appliquées.

- **2-agressif** : les messages identifiés comme du hameçonnage avec un haut degré de confiance sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.

- **3-plus agressif** : les messages identifiés comme hameçonnage avec un niveau de confiance moyen ou élevé sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.

- **4-le plus agressif** : les messages identifiés comme hameçonnage avec un niveau de confiance faible, moyen ou élevé sont traités comme s’ils étaient identifiés avec un très haut degré de confiance.

Le risque de faux positifs (bons messages marqués comme incorrects) augmente à mesure que vous augmentez ce paramètre. Pour plus d’informations sur les paramètres recommandés, reportez-vous à la rubrique [anti-hameçonnage Policy in Microsoft Defender for Office 365 Settings](recommended-settings-for-eop-and-office365-atp.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).
