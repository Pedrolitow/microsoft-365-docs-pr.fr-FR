---
title: Liens sûrs
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: Admin
ms.article: overview
f1_keywords:
- "197503"
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- ZVO160
- ZXL160
- ZPP160
- ZWD160
ms.assetid: dd6a1fef-ec4a-4cf4-a25a-bb591c5811e3
description: Dans cet article, les administrateurs peuvent en savoir plus sur la protection des liens fiables dans Defender pour Office 365 afin de protéger leur organisation contre le hameçonnage et les autres attaques qui utilisent des URL malveillantes.
ms.openlocfilehash: 066732e2f1a886e303fea86730baeb78c8152990
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49659488"
---
# <a name="safe-links-in-microsoft-defender-for-office-365"></a>Liens fiables dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](office-365-atp.md). Si vous utilisez Outlook.com, la famille Microsoft 365 ou Microsoft 365 personnel, et que vous recherchez des informations sur Safelinks dans Outlook, consultez la rubrique [Advanced Outlook.com Security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

La fonctionnalité liens fiables est une fonctionnalité de [Defender pour Office 365](office-365-atp.md) qui permet l’analyse des URL et la réécriture des messages électroniques entrants dans le flux de messagerie et la vérification des URL et des liens dans les messages électroniques et les autres emplacements. L’analyse des liens fiables se produit en plus de la protection anti- [courrier indésirable et anti-programme malveillant](anti-spam-and-anti-malware-protection.md) dans les messages électroniques entrants dans Exchange Online Protection (EoP). L’analyse des liens fiables permet de protéger votre organisation contre les liens malveillants utilisés dans le hameçonnage et les autres attaques.

La protection des liens fiables est disponible aux emplacements suivants :

- **Messages électroniques**: la protection des liens fiables pour les liens dans les messages électroniques est contrôlée par les stratégies de liens fiables. Il n’existe pas de stratégie de liens approuvés par défaut, pour **obtenir la protection des liens fiables dans les messages électroniques, vous devez créer une ou plusieurs stratégies de liens fiables**. Pour obtenir des instructions, reportez-vous à la rubrique [configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-atp-safe-links-policies.md).

  Pour plus d’informations sur la protection des liens fiables pour les messages électroniques, voir la section [paramètres de liens fiables pour les messages électroniques](#safe-links-settings-for-email-messages) plus loin dans cet article.

- **Microsoft teams** (actuellement en mode Aperçu) : la protection des liens fiables pour les liens dans les conversations de teams, les conversations de groupe ou les canaux est également contrôlée par les stratégies de liens fiables. Il n’existe pas de stratégie de liens approuvés par défaut, pour **obtenir la protection des liens fiables dans Teams, vous devez créer une ou plusieurs stratégies de liens fiables**.

  Pour plus d’informations sur la protection des liens fiables dans Teams, consultez la section [paramètres de liens approuvés pour Microsoft teams](#safe-links-settings-for-microsoft-teams) plus loin dans cet article.

- **Applications office 365**: la protection des liens fiables pour les applications Office 365 est disponible dans les APS de bureau, mobiles et Web pris en charge. Vous **configurez** la protection des liens fiables pour les applications Office 365 dans le paramètre global qui se trouvent **en dehors** des stratégies de liens fiables. Pour obtenir des instructions, consultez la rubrique [configure Global Settings for Safe Links Settings in Microsoft Defender for Office 365](configure-global-settings-for-safe-links.md).

  Toutefois, la protection des liens fiables pour les applications Office 365 s' **applique** uniquement aux utilisateurs qui sont inclus dans les stratégies de liens fiables actifs. Si un utilisateur n’est pas inclus dans une stratégie de liens fiables active, il n’obtient pas de protection de liens fiables dans les applications Office 365 prises en charge.

  Pour plus d’informations sur la protection des liens fiables dans les applications Office 365, voir la section [paramètres de liens approuvés pour les applications office 365](#safe-links-settings-for-office-365-apps) plus loin dans cet article.

Cet article décrit en détail les types de paramètres de liens fiables suivants :

- **Paramètres des stratégies de liens fiables**: ces paramètres s’appliquent uniquement aux utilisateurs qui sont inclus dans les stratégies spécifiques, et les paramètres peuvent être différents selon les stratégies. Ces paramètres sont les suivants :

  - [Paramètres de liens fiables pour les messages électroniques](#safe-links-settings-for-email-messages)
  - [Paramètres de liens fiables pour Microsoft teams](#safe-links-settings-for-microsoft-teams)
  - [Listes « ne pas réécrire les URL suivantes » dans stratégies de liens fiables](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)

- **Paramètres globaux de liens approuvés**: ces paramètres sont configurés globalement, pas dans les stratégies de liens fiables. Toutefois, les paramètres s’appliquent uniquement aux utilisateurs qui sont inclus dans les stratégies de liens fiables actifs. Ces paramètres sont les suivants :

  - [Paramètres de liens fiables pour les applications Office 365](#safe-links-settings-for-office-365-apps)
  - [Liste « bloquer les URL suivantes » pour les liens fiables](#block-the-following-urls-list-for-safe-links)

Le tableau suivant décrit les scénarios de liens fiables dans les organisations Microsoft 365 et Office 365 qui incluent Defender pour Office 365 (en d’autres termes, le manque de licence n’est jamais un problème dans les exemples).

****

|Scénario|Résultat|
|---|---|
|Jean est membre du service marketing. La protection des liens fiables pour les applications Office 365 est activée dans les paramètres globaux pour les liens fiables et une stratégie de liens fiables qui s’applique aux membres du service marketing existe. Jean ouvre une présentation PowerPoint dans un message électronique, puis clique sur une URL dans la présentation.|Jean est protégé par les liens fiables. <p> Jean est inclus dans une stratégie de liens fiables, et la protection des liens fiables pour les applications Office 365 est activée. <p> Pour plus d’informations sur la configuration requise pour la protection des liens fiables dans les applications Office 365, voir la section [paramètres de liens approuvés pour les applications office 365](#safe-links-settings-for-office-365-apps) plus loin dans cet article.|
|Aucune stratégie de liens fiables n’est configurée pour l’organisation Microsoft 365 E5 de Chris. Chris reçoit un courrier électronique d’un expéditeur externe contenant une URL vers un site Web malveillant qu’il clique finalement.|Chris n’est pas protégé par les liens fiables. <p> Un administrateur doit créer au moins une stratégie de liens fiables pour obtenir une protection des liens fiables dans les messages électroniques entrants. Chris doit être inclus dans les conditions de la stratégie pour obtenir une protection des liens fiables.|
|Dans l’organisation de Pat, aucun administrateur n’a créé de stratégies de liens fiables, mais la protection des liens fiables pour les applications Office 365 est activée. Pat ouvre un document Word et clique sur une URL dans le fichier.|Pat n’est pas protégé par les liens fiables. <p> Bien que la protection des liens fiables pour les applications Office 365 est activée globalement, Pat n’est pas inclus dans les stratégies de liens fiables actives, de sorte que la protection ne peut pas être appliquée.|
|Dans l’organisation de Lee, `https://tailspintoys.com` est configuré dans la liste **bloquer les URL suivantes** dans les paramètres globaux pour les liens fiables. Une stratégie de liens fiables qui inclut Lee existe déjà. Lee reçoit un message électronique qui contient l’URL `https://tailspintoys.com/aboutus/trythispage` . Lee clique sur l’URL.|L’URL peut être automatiquement bloquée pour Lee ; Cela dépend de l’entrée URL de la liste et du client de messagerie Lee utilisé. Pour plus d’informations, consultez la section [« bloquer les URL suivantes » pour les liens fiables](#block-the-following-urls-list-for-safe-links) plus loin dans cet article.|
|Marie et Julia fonctionnent pour contoso.com. Il y a longtemps, les administrateurs ont configuré des stratégies de liens fiables qui s’appliquent à Marie et Julia. Marie envoie un message électronique à Julia, pas de savoir que le courrier électronique contient une URL malveillante.|Julia est protégé par les liens fiables **si** la stratégie de liens fiables qui s’applique à elle est configurée pour s’appliquer aux messages entre les destinataires internes. Pour plus d’informations, consultez la section [paramètres de liens approuvés pour les messages électroniques](#safe-links-settings-for-email-messages) plus loin dans cet article.|

## <a name="safe-links-settings-for-email-messages"></a>Paramètres de liens fiables pour les messages électroniques

Liens fiables analyse les messages électroniques entrants pour détecter les liens hypertexte malveillants connus. Les URL analysées sont réécrites à l’aide du préfixe d’URL standard de Microsoft : `https://nam01.safelinks.protection.outlook.com` . Une fois le lien réécrit, il est analysé pour le contenu potentiellement malveillant.

Une fois que les liens fiables réécritnt une URL, l’URL reste réécrite, même si le message est transféré ou renvoyé. Les liens supplémentaires ajoutés au message envoyé ou auquel il est répondu ne sont pas réécrits.

Les paramètres des stratégies de liens fiables qui s’appliquent aux messages électroniques sont décrits dans la liste suivante :

- **Sélectionnez l’action pour les URL potentiellement malveillantes dans les messages**: active ou désactive l’analyse des liens fiables dans les messages électroniques. La valeur recommandée est **activé**. L’activation de ce paramètre entraîne les actions suivantes.

  - L’analyse des liens fiables est activée dans Outlook (C2R) sur Windows.
  - Les URL sont réécrites et les utilisateurs sont acheminés via la protection des liens fiables lorsqu’ils cliquent sur les URL dans les messages.
  - Lorsque l’utilisateur clique dessus, les URL sont comparées à une liste d’URL malveillantes connues et à la [liste « bloquer les URL suivantes »](#block-the-following-urls-list-for-safe-links).
  - Les URL qui n’ont pas de réputation valide sont détonations de manière asynchrone en arrière-plan.

- **Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers**: permet l’analyse en temps réel des liens, y compris les liens dans les messages électroniques qui pointent vers du contenu téléchargeable. La valeur recommandée est activée.

  - **Patientez jusqu’à la fin de l’analyse des URL avant de remettre le message**:

    - Activé : les messages qui contiennent des URL sont conservés jusqu’à la fin de l’analyse. Les messages sont remis uniquement une fois que les URL sont approuvées comme étant sûres. Il s’agit de la valeur recommandée.
    - Désactivé : si l’analyse des URL ne peut pas aboutir, envoyez le message.

- **Appliquer des liens fiables aux messages électroniques envoyés au sein de l’organisation**: active ou désactive l’analyse des liens fiables sur les messages envoyés entre des expéditeurs internes et des destinataires internes au sein de la même organisation Exchange Online. La valeur recommandée est activée.

- **Ne pas suivre les clics des utilisateurs**: active ou désactive le stockage de liens fiables cliquez sur données pour les URL sur lesquelles l’utilisateur clique dans les messages électroniques. La valeur recommandée est de laisser ce paramètre non sélectionné (pour effectuer le suivi des clics des utilisateurs).

  URL le suivi des liens dans les messages électroniques envoyés entre des expéditeurs internes et des destinataires internes n’est pas pris en charge actuellement.

- **Ne pas autoriser les utilisateurs à cliquer vers l’URL d’origine**: autorise ou empêche les utilisateurs de cliquer sur la [page d’avertissement](#warning-pages-from-safe-links) à l’URL d’origine. La valeur Recommended est activée.

- **Ne pas réécrire les URL suivantes**: laisse les URL telles quelles. Conserve une liste personnalisée d’URL sûres qui n’ont pas besoin d’être analysées. La liste est unique pour chaque stratégie de liens fiables. Pour plus d’informations sur la liste **ne pas réécrire les URL suivantes** , consultez les [listes « ne pas réécrire les URL suivantes » dans stratégies de liens approuvés](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies) plus loin dans cet article.

Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie standard et stricte pour les stratégies de liens fiables, voir [paramètres de stratégie de liens fiables](recommended-settings-for-eop-and-office365-atp.md#safe-links-policy-settings).

- **Filtres de destinataires**: vous devez spécifier les conditions de destinataire et les exceptions qui déterminent la personne à laquelle la stratégie s’applique. Vous pouvez utiliser ces propriétés pour les conditions et les exceptions :

  - **Le destinataire est**
  - **Le domaine du destinataire est**
  - **Le destinataire est membre de**

  Vous ne pouvez utiliser une condition ou une exception qu'une seule fois, mais la condition ou l'exception peut contenir plusieurs valeurs. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

- **Priority**: Si vous créez plusieurs stratégies, vous pouvez spécifier l’ordre dans lequel elles sont appliquées. Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

  Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

### <a name="how-safe-links-works-in-email-messages"></a>Fonctionnement des liens fiables dans les messages électroniques

À un niveau élevé, voici comment fonctionne la protection des liens fiables sur les URL dans les messages électroniques :

1. Tous les messages passent par EOP, où les filtres de protocole Internet (IP) et d’enveloppe, la protection contre les programmes malveillants par signature, le courrier indésirable et les filtres anti-programme malveillant avant que le message ne soit remis à la boîte aux lettres du destinataire.

2. L’utilisateur ouvre le message dans sa boîte aux lettres et clique sur une URL dans le message.

3. Les liens fiables vérifient immédiatement l’URL avant d’ouvrir le site Web :

   - Si l’URL est incluse dans la liste **bloquer les URL suivantes** , un [Avertissement d’URL bloquée](#blocked-url-warning) s’ouvre.

   - Si l’URL pointe vers un site Web qui a été jugé malveillant, une page d' [avertissement de site Web malveillant](#malicious-website-warning) (ou une page d’avertissement différente) s’ouvre.

   - Si l’URL pointe vers un fichier téléchargeable et que l’option **appliquer l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers** est activée dans la stratégie qui s’applique à l’utilisateur, le fichier téléchargeable est vérifié.

   - Si l’URL est jugée fiable, le site Web s’ouvre.

## <a name="safe-links-settings-for-microsoft-teams"></a>Paramètres de liens fiables pour Microsoft teams

> [!IMPORTANT]
> Depuis le 2020 mars, cette fonctionnalité est en aperçu et n’est accessible qu’aux membres du programme Microsoft teams adoption de la technologie (TAP). Pour plus d’informations sur le calendrier des publications, consultez la feuille de [route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=1&filters=&searchterms=Safe%2CLinks%2CProtection%2Cfor%2CMicrosoft%2CTeams).

Vous activez ou désactivez la protection des liens fiables pour Microsoft teams dans stratégies de liens fiables. Plus précisément, vous utilisez le paramètre **Sélectionner l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft teams** . La valeur recommandée est **activé**.

Les paramètres suivants des stratégies de liens fiables qui s’appliquent aux liens dans les messages électroniques s’appliquent également aux liens dans teams :

- **Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers**
- **Ne pas suivre les clics des utilisateurs**
- **Ne pas autoriser les utilisateurs à cliquer vers l’URL d’origine**

Ces paramètres sont expliqués dans la section [paramètres de liens approuvés précédents pour les messages électroniques](#safe-links-settings-for-email-messages) .

Une fois que vous avez activé la protection des liens fiables pour Microsoft Teams, les URL dans teams sont vérifiées par rapport à une liste de liens malveillants connus lorsque l’utilisateur protégé clique sur le lien (protection par période de clic). Les URL ne sont pas réécrites. Si un lien est détecté comme étant malveillant, les utilisateurs auront les expériences suivantes :

- Si vous avez cliqué sur le lien dans une conversation Teams, une conversation de groupe ou à partir de canaux, la page d’avertissement, comme illustré dans la capture d’écran ci-dessous, apparaît dans le navigateur Web par défaut.
- Si vous avez cliqué sur le lien à partir d’un onglet épinglé, la page d’avertissement s’affiche dans l’interface teams au sein de cet onglet. Pour des raisons de sécurité, l’option permettant d’ouvrir le lien dans un navigateur Web est désactivée.
- En fonction de la configuration du paramètre **ne pas autoriser les utilisateurs à cliquer sur l’URL d’origine** dans la stratégie, l’utilisateur est autorisé ou non à accéder à l’URL d’origine (**Continuer malgré tout (non recommandé)** dans la capture d’écran). Nous vous recommandons d’activer le paramètre **ne pas autoriser les utilisateurs à cliquer sur vers l’URL d’origine** afin que les utilisateurs ne puissent pas cliquer sur jusqu’à l’URL d’origine.

Si l’utilisateur qui a envoyé le lien n’est pas inclus dans une stratégie de liens fiables où la protection des équipes est activée, l’utilisateur est libre de cliquer jusqu’à l’URL d’origine sur son ordinateur ou périphérique.

![Une page liens fiables pour les équipes signalant un lien malveillant.](../../media/tp-safe-links-for-teams-malicious.png)

Si vous cliquez sur le bouton **revenir** sur la page d’avertissement, l’utilisateur reviendra à son emplacement de contexte ou d’URL d’origine. Toutefois, si vous cliquez à nouveau sur le lien d’origine, les liens fiables analysent de nouveau l’URL, de sorte que la page d’avertissement réapparaît.

### <a name="how-safe-links-works-in-teams"></a>Fonctionnement des liens fiables dans teams

À un niveau élevé, voici le fonctionnement de la protection des liens fiables pour les URL dans Microsoft teams :

1. Un utilisateur démarre l’application Teams.

2. Microsoft 365 vérifie que l’organisation de l’utilisateur inclut Microsoft Defender pour Office 365, et que l’utilisateur est inclus dans une stratégie de liens approuvés active où la protection de Microsoft teams est activée.

3. Les URL sont validées au moment où l’utilisateur clique sur les conversations, les conversations de groupe, les canaux et les onglets.

## <a name="safe-links-settings-for-office-365-apps"></a>Paramètres de liens fiables pour les applications Office 365

Protection des liens fiables pour les applications Office 365 vérifie les liens dans les documents Office, pas les liens dans les messages électroniques (mais il peut vérifier les liens des documents Office joints dans les messages électroniques une fois que le document est ouvert).

La protection des liens fiables pour les applications Office 365 a les exigences suivantes en matière de client :

- Microsoft 365 Apps ou Microsoft 365 Business Premium.
  - Versions actuelles de Word, Excel et PowerPoint sur Windows, Mac ou dans un navigateur Web.
  - Applications Office sur les appareils iOS ou Android.
  - Visio sur Windows.
  - OneNote dans un navigateur Web.

- Les applications Office 365 sont configurées pour utiliser l’authentification moderne. Pour plus d’informations, voir fonctionnement [de l’authentification moderne pour office 2013, office 2016 et les applications clientes office 2019](https://docs.microsoft.com/microsoft-365/enterprise/modern-auth-for-office-2013-and-2016).

- Les utilisateurs sont connectés à l’aide de leur compte professionnel ou scolaire. Pour plus d’informations, consultez la rubrique [se connecter à Office](https://support.microsoft.com/office/b9582171-fd1f-4284-9846-bdd72bb28426).

Vous configurez la protection des liens fiables pour les applications Office 365 dans les paramètres globaux pour les liens fiables, et non dans les stratégies de liens fiables. Toutefois, pour que la protection des liens fiables pour les applications Office 365 soit appliquée, l’utilisateur qui ouvre le document Office et clique sur le lien doit être inclus dans une stratégie de liens approuvés active.

Les paramètres de liens approuvés suivants sont disponibles pour les applications Office 365 :

- **Applications office 365**: active ou désactive l’analyse des liens fiables dans les applications Office 365 prises en charge. La valeur par défaut et recommandée est **activé**.

- **Ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables**: active ou désactive le stockage de liens fiables cliquez sur données pour les URL sur lesquelles l’utilisateur clique dans la version de bureau Word, Excel, PowerPoint et Visio. La valeur recommandée est **off**, ce qui signifie que les clics utilisateur sont suivis.

- **Ne pas autoriser les utilisateurs à cliquer sur les liens fiables vers l’URL d’origine**: autorise ou empêche les utilisateurs de cliquer sur la [page d’avertissement](#warning-pages-from-safe-links) à l’URL d’origine dans les versions de bureau Word, Excel, PowerPoint et Visio. La valeur par défaut et recommandée est **activé**.

Pour configurer les paramètres de liens approuvés pour les applications Office 365, voir [configurer la protection des liens fiables pour les applications office 365](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-security--compliance-center).

Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie standard et stricte, consultez la rubrique [Global Settings for Safe Links](recommended-settings-for-eop-and-office365-atp.md#global-settings-for-safe-links).

### <a name="how-safe-links-works-in-office-365-apps"></a>Fonctionnement des liens fiables dans les applications Office 365

À un niveau élevé, voici la manière dont la protection des liens fiables fonctionne pour les URL dans les applications Office 365. Les applications Office 365 prises en charge sont décrites dans la section précédente.

1. Un utilisateur se connecte à l’aide de son compte professionnel ou scolaire dans une organisation qui comprend les applications Microsoft 365 ou Microsoft 365 Business Premium.

2. L’utilisateur ouvre et clique sur un lien vers un document Office dans une application Office prise en charge.

3. Les liens fiables vérifient immédiatement l’URL avant d’ouvrir le site Web cible :

   - Si l’URL est incluse dans la liste et qu’elle ignore l’analyse des liens fiables (la liste **bloquer les URL suivantes** ), une page d' [Avertissement d’URL bloquée](#blocked-url-warning) s’ouvre.

   - Si l’URL pointe vers un site Web qui a été jugé malveillant, une page d' [avertissement de site Web malveillant](#malicious-website-warning) (ou une page d’avertissement différente) s’ouvre.

   - Si l’URL pointe vers un fichier téléchargeable et que la stratégie de liens approuvés qui s’applique à l’utilisateur est configurée pour analyser les liens vers du contenu téléchargeable (**appliquer l’analyse des URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers**), le fichier téléchargeable est vérifié.

   - Si l’URL est considérée comme fiable, l’utilisateur est dirigé vers le site Web.

   - Si l’analyse des liens fiables ne parvient pas à se terminer, la protection des liens fiables ne déclenche pas. Dans les clients de bureau Office, l’utilisateur est prévenu avant de passer au site Web de destination.

> [!NOTE]
> Le début de chaque session peut prendre plusieurs secondes pour vérifier que l’utilisateur dispose de liens fiables pour Office activé.

## <a name="block-the-following-urls-list-for-safe-links"></a>Liste « bloquer les URL suivantes » pour les liens fiables

La liste **bloquer les URL suivantes** définit les liens qui sont toujours bloqués par l’analyse des liens fiables aux emplacements suivants :

- Messages électroniques.
- Documents dans les applications Office 365 dans Windows et Mac.
- Documents dans Office pour iOS et Android.

Lorsqu’un utilisateur d’une stratégie de liens approuvés active clique sur un lien bloqué dans une application prise en charge, il est dirigé vers la page d’avertissement de l' [URL bloquée](#blocked-url-warning) .

Vous configurez la liste des URL dans les paramètres globaux pour les liens fiables. Pour obtenir des instructions, consultez la rubrique [configurer la liste « bloquer les URL suivantes »](configure-global-settings-for-safe-links.md#configure-the-block-the-following-urls-list-in-the-security--compliance-center).

**Remarques** :

- Pour obtenir une liste véritablement universelle des URL bloquées partout, voir [gérer les URL dans la liste des clients autorisés/bloqués](tenant-allow-block-list.md).

- Limit
  - Le nombre maximal d’entrées est de 500.
  - La longueur maximale d’une entrée est de 128 caractères.
  - Toutes les entrées ne peuvent pas dépasser 10 000 caractères.

- N’incluez pas une barre oblique ( `/` ) à la fin de l’URL. Par exemple, utilisez `https://www.contoso.com` , not `https://www.contoso.com/` .

- Un domaine uniquement-URL (par exemple `contoso.com` ou `tailspintoys.com` ) bloquera toute URL contenant le domaine.

- Vous pouvez bloquer un sous-domaine sans bloquer le domaine complet. Par exemple, `toys.contoso.com*` bloque toute URL qui contient le sous-domaine, mais elle ne bloque pas les URL qui contiennent le domaine complet `contoso.com` .

- Vous pouvez inclure jusqu’à trois caractères génériques ( `*` ) par entrée d’URL.

### <a name="entry-syntax-for-the-block-the-following-urls-list"></a>Syntaxe d’entrée pour la liste « bloquer les URL suivantes »

Des exemples de valeurs que vous pouvez entrer et leurs résultats sont décrits dans le tableau suivant :

****

|Valeur|Résultat|
|---|---|
|`contoso.com` <p> ou <p> `*contoso.com*`|Bloque le domaine, les sous-domaines et les chemins d’accès. Par exemple, `https://www.contoso.com` , `https://sub.contoso.com` et `https://contoso.com/abc` sont bloqués.|
|`https://contoso.com/a`|Bloque `https://contoso.com/a` , mais pas les sous-chemins supplémentaires comme `https://contoso.com/a/b` .|
|`https://contoso.com/a*`|Blocs `https://contoso.com/a` et sous-chemins supplémentaires comme `https://contoso.com/a/b` .|
|`https://toys.contoso.com*`|Bloque un sous-domaine ( `toys` dans cet exemple) tout en autorisant les clics sur d’autres URL de domaine (par exemple `https://contoso.com` `https://home.contoso.com` , ou).|
|

## <a name="do-not-rewrite-the-following-urls-lists-in-safe-links-policies"></a>Listes « ne pas réécrire les URL suivantes » dans stratégies de liens fiables

> [!NOTE]
> Si votre organisation utilise des stratégies de liens fiables, les listes **URL suivantes ne sont pas réécrites** sont la seule méthode prise en charge pour les tests de hameçonnage tiers.

Chaque stratégie de liens fiables contient une liste **ne pas réécrire les URL suivantes** que vous pouvez utiliser pour spécifier les URL qui ne sont pas réécrites par l’analyse des liens fiables. En d’autres termes, la liste permet aux utilisateurs qui sont inclus dans la stratégie d’accéder aux URL spécifiées qui seraient sinon bloquées par les liens fiables. Vous pouvez configurer différentes listes dans des stratégies de liens fiables différentes. Le traitement de stratégie s’arrête après que la stratégie la plus élevée (probablement, la priorité la plus élevée) est appliquée à l’utilisateur. Par conséquent, une seule **ne pas réécrire la liste des URL suivantes** est appliquée à un utilisateur qui est inclus dans plusieurs stratégies de liens fiables actives.

Pour ajouter des entrées à la liste dans des stratégies de liens fiables nouvelles ou existantes, consultez la rubrique [créer](set-up-atp-safe-links-policies.md#use-the-security--compliance-center-to-create-safe-links-policies) des stratégies de liens fiables ou [modifier des stratégies de liens fiables](set-up-atp-safe-links-policies.md#use-the-security--compliance-center-to-modify-safe-links-policies).

**Remarques** :

- Les clients suivants ne reconnaissent pas les listes **ne pas réécrire les URL suivantes dans les** stratégies de liens fiables. Les utilisateurs inclus dans les stratégies ne peuvent pas accéder aux URL en fonction des résultats de l’analyse des liens fiables dans ces clients :

  - Microsoft Teams
  - Office Web Apps

  Pour obtenir une liste véritablement universelle des URL autorisées partout, consultez [la rubrique gérer les URL dans la liste des clients autorisés/bloqués](tenant-allow-block-list.md).

- Envisagez d’ajouter des URL internes couramment utilisées à la liste pour améliorer l’expérience utilisateur. Par exemple, si vous disposez de services locaux, tels que Skype entreprise ou SharePoint, vous pouvez ajouter ces URL pour les exclure de l’analyse.

- Si vous ne disposez pas déjà des entrées de **réécriture d’URL suivantes** dans vos stratégies de liens fiables, veillez à consulter les listes et à ajouter des caractères génériques selon vos besoins. Par exemple, votre liste a une entrée like `https://contoso.com/a` et vous décidez par la suite d’inclure des sous-chemins comme `https://contoso.com/a/b` . Au lieu d’ajouter une nouvelle entrée, ajoutez un caractère générique à l’entrée existante afin qu’elle devienne `https://contoso.com/a/*` .

- Vous pouvez inclure jusqu’à trois caractères génériques ( `*` ) par entrée d’URL. Les caractères génériques incluent explicitement des préfixes ou des sous-domaines. Par exemple, l’entrée `contoso.com` n’est pas la même que celle `*.contoso.com/*` de, car elle `*.contoso.com/*` permet aux utilisateurs de visiter des sous-domaines et des chemins d’accès dans le domaine spécifié.

### <a name="entry-syntax-for-the-do-not-rewrite-the-following-urls-list"></a>Syntaxe d’entrée pour la liste « ne pas réécrire les URL suivantes »

Des exemples de valeurs que vous pouvez entrer et leurs résultats sont décrits dans le tableau suivant :

****

|Valeur|Résultat|
|---|---|
|`contoso.com`|Autorise l’accès à des `https://contoso.com` sous-domaines ou des chemins d’accès.|
|`*.contoso.com/*`|Permet d’accéder à un domaine, à des sous-domaines et à des chemins d’accès (par exemple,,, `https://www.contoso.com` `https://www.contoso.com` `https://maps.contoso.com` ou `https://www.contoso.com/a` ). <p> Cette entrée est fondamentalement plus efficace que `*contoso.com*` , car elle n’autorise pas les sites potentiellement frauduleux, comme `https://www.falsecontoso.com` ou `https://www.false.contoso.completelyfalse.com`|
|`https://contoso.com/a`|Autorise l’accès à `https://contoso.com/a` , mais pas aux sous-chemins comme `https://contoso.com/a/b`|
|`https://contoso.com/a/*`|Autorise l’accès `https://contoso.com/a` et les sous-chemins comme `https://contoso.com/a/b`|
|

## <a name="warning-pages-from-safe-links"></a>Pages d’avertissement des liens fiables

Cette section contient des exemples de différentes pages d’avertissement qui sont déclenchées par la protection des liens fiables lorsque vous cliquez sur une URL.

Notez que plusieurs pages d’avertissement ont été mises à jour. Si vous ne voyez pas les pages mises à jour, vous allez bientôt. Les pages mises à jour incluent un nouveau jeu de couleurs, des détails supplémentaires et la possibilité de passer à un site en dépit de l’avertissement et des recommandations.

### <a name="scan-in-progress-notification"></a>Notification d’analyse en cours

L’URL sur laquelle l’utilisateur a cliqué est analysée par les liens fiables. Il se peut que vous deviez patienter quelques instants avant de retenter le lien.

![Notification « la liaison est en cours d’analyse »](../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png)

La page de notification d’origine ressemble à ceci :

![Notification d’origine « le lien est en cours d’analyse »](../../media/04368763-763f-43d6-94a4-a48291d36893.png)

### <a name="suspicious-message-warning"></a>Avertissement de message suspect

L’URL sur laquelle vous avez cliqué se trouvait dans un message électronique similaire à d’autres messages suspects. Nous vous recommandons de double-vérifier le message électronique avant de passer au site.

![AVERTISSEMENT « un lien a été cliqué à partir d’un message suspect »](../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png)

### <a name="phishing-attempt-warning"></a>Avertissement de tentative d’hameçonnage

L’URL sur laquelle vous avez cliqué se trouvait dans un message électronique qui a été identifié comme une attaque par hameçonnage. Par conséquent, toutes les URL dans le message électronique sont bloquées. Nous vous recommandons de ne pas passer au site.

![« Le lien a été cliqué dans un message d’hameçonnage »](../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png)

### <a name="malicious-website-warning"></a>Avertissement de site Web malveillant

L’URL sur laquelle vous avez cliqué pointe vers un site identifié comme malveillant. Nous vous recommandons de ne pas passer au site.

![Avertissement « ce site Web est classé comme malveillant »](../../media/058883c8-23f0-4672-9c1c-66b084796177.png)

La page d’avertissement d’origine ressemble à ceci :

![Avertissement « ce site Web a été classé comme malveillant »](../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png)

### <a name="blocked-url-warning"></a>Avertissement d’URL bloquée

L’URL sur laquelle vous avez cliqué a été bloquée manuellement par un administrateur dans votre organisation (la liste **bloquer les URL suivantes** dans les paramètres globaux pour les liens fiables). Le lien n’a pas été analysé par les liens fiables, car il a été bloqué manuellement.

Il existe plusieurs raisons pour lesquelles un administrateur peut bloquer manuellement des URL spécifiques. Si vous pensez que le site ne doit pas être bloqué, contactez votre administrateur.

![Avertissement « ce site Web a été bloqué par votre administrateur »](../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png)

La page d’avertissement d’origine ressemble à ceci :

![Avertissement « ce site Web a été bloqué par la stratégie d’URL de votre organisation »](../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png)

### <a name="error-warning"></a>Avertissement d’erreur

Une erreur s’est produite et l’URL ne peut pas être ouverte.

![« AVERTISSEMENT impossible de charger la page à laquelle vous tentez d’accéder »](../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png)

La page d’avertissement d’origine ressemble à ceci :

![AVERTISSEMENT « Cette page n’a pas pu être chargée »](../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png)
