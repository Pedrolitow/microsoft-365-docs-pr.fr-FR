---
title: Vue d’ensemble des liens fiables complets pour Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
f1_keywords:
- "197503"
ms.date: 09/08/2021
ms.localizationpriority: medium
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
description: Découvrez la protection des liens sécurisés dans Defender pour Office 365 pour protéger une organisation contre le hameçonnage et d’autres attaques qui utilisent des URL malveillantes. Découvrez les liens fiables Teams et consultez les graphiques des messages Liens fiables.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b3eb2ee76beb106d26d5b7b65d13c7aa0a0d5c1e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487046"
---
# <a name="safe-links-in-microsoft-defender-for-office-365"></a>Liens sécurisés dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](defender-for-office-365.md). Si vous utilisez Outlook.com, Microsoft 365 Famille ou Microsoft 365 Personnel et que vous recherchez des informations sur safelinks dans Outlook, consultez [Advanced Outlook.com security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Les liens sécurisés sont une fonctionnalité de [Defender pour Office 365](defender-for-office-365.md) qui fournit l’analyse et la réécriture d’URL des messages électroniques entrants dans le flux de courrier, ainsi que la vérification au moment du clic des URL et des liens dans les messages électroniques et d’autres emplacements. L’analyse des liens sécurisés se produit en plus du [courrier anti-courrier indésirable](anti-spam-protection.md) et [anti-programme malveillant](anti-malware-protection.md) dans les messages électroniques entrants dans Exchange Online Protection (EOP). L’analyse des liens fiables peut permettre de votre organisation contre les liens malveillants utilisés dans le hameçonnage et d’autres attaques.

Regardez cette courte vidéo sur la façon de se protéger contre les liens malveillants avec des liens fiables dans Microsoft Defender pour Office 365.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGzjb]

La protection Liens fiables est disponible dans les emplacements suivants :

- **Messages électroniques** : bien qu’il n’existe aucune stratégie de liens fiables par défaut, la stratégie de sécurité prédéfinie de **protection intégrée** fournit une protection des liens sécurisés à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de liens sécurisés personnalisées). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md). Vous pouvez également créer des stratégies de liens fiables qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques. Pour obtenir des instructions, consultez [Configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md).

  Pour plus d’informations sur la protection des liens sécurisés pour les messages électroniques, consultez la section [Liens sécurisés pour les messages électroniques](#safe-links-settings-for-email-messages) plus loin dans cet article.
  
  > [!NOTE]
  > Les liens sécurisés ne fonctionnent pas sur les dossiers publics à extension messagerie.
  >
  > Les liens sécurisés prennent uniquement en charge les formats HTTP(S) et FTP.

- **Microsoft Teams** : la protection Liens fiables pour les liens dans les conversations Teams, les conversations de groupe ou à partir de canaux est également contrôlée par des stratégies de Liens fiables.

  Pour plus d’informations sur la protection des liens fiables dans Teams, consultez la section [Liens fiables pour Microsoft Teams](#safe-links-settings-for-microsoft-teams) plus loin dans cet article.

  > [!NOTE]
  > Actuellement, la protection des liens sécurisés pour Microsoft Teams n’est pas disponible dans Microsoft 365 GCC High ou Microsoft 365 DoD.

- **Applications Office 365** : la protection Liens fiables pour les applications Office 365 est disponible dans les applications de bureau, mobiles et web prises en charge. Vous **configurez** la protection des liens sécurisés pour Office 365 applications dans le paramètre global qui sont **en dehors** des stratégies liens sécurisés. Pour obtenir des instructions, consultez [Configurer les paramètres globaux pour les paramètres Liens fiables dans Microsoft Defender pour Office 365](configure-global-settings-for-safe-links.md).

  La protection Liens fiables pour les applications Office 365 est appliquée à tous les utilisateurs de l’organisation qui sont titulaires d’une licence Defender pour Office 365, que les utilisateurs soient inclus ou non dans les stratégies de liens fiables actives.

  Pour plus d’informations sur la protection des liens sécurisés dans Office 365 applications, consultez la section [Liens sécurisés pour Office 365 section applications](#safe-links-settings-for-office-365-apps) plus loin dans cet article.

Cet article inclut des descriptions détaillées des types suivants de paramètres liens fiables :

- **Paramètres dans les stratégies liens fiables** : ces paramètres s’appliquent uniquement aux utilisateurs inclus dans les stratégies spécifiques, et les paramètres peuvent être différents entre les stratégies. Ces paramètres sont les suivants :

  - [Paramètres liens sécurisés pour les messages électroniques](#safe-links-settings-for-email-messages)
  - [Coffre paramètres de liens pour Microsoft Teams](#safe-links-settings-for-microsoft-teams)
  - [Listes « Ne pas réécrire les URL suivantes » dans les stratégies liens fiables](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)

- **Paramètres de liens sécurisés globaux** : ces paramètres sont configurés globalement, et non dans les stratégies liens sécurisés. Ces paramètres sont les suivants :

  - [Paramètres liens sécurisés pour les applications Office 365](#safe-links-settings-for-office-365-apps)
  - [Liste « Bloquer les URL suivantes » pour les liens fiables](#block-the-following-urls-list-for-safe-links)

Le tableau suivant décrit les scénarios de liaisons sécurisées dans Microsoft 365 et les organisations Office 365 qui incluent des Defender pour Office 365 (notez que l’absence de licences n’est jamais un problème dans les exemples).

|Scénario|Résultat|
|---|---|
|Jean est membre du service marketing. La protection des liens sécurisés pour les applications Office 365 est activée dans les paramètres globaux des liens sécurisés, et une stratégie liens sécurisés qui s’applique aux membres du service marketing existe. Jean ouvre une présentation PowerPoint dans un message électronique, puis clique sur une URL dans la présentation.|Jean est protégé par des liens fiables. <p> Jean est inclus dans une stratégie liens sécurisés, et la protection des liens sécurisés pour Office 365 applications est activée. <p> Pour plus d’informations sur la configuration requise pour la protection des liens sécurisés dans les applications Office 365, consultez la section [Liens sécurisés pour les applications Office 365](#safe-links-settings-for-office-365-apps) plus loin dans cet article.|
|Aucune stratégie de liens fiables n’est configurée dans l’organisation Microsoft 365 E5 de Chris. Chris reçoit un e-mail d’un expéditeur externe qui contient une URL vers un site web malveillant qu’il clique finalement.|Chris n’est pas protégé par des liens fiables. <p> Un administrateur doit créer au moins une stratégie de liens sécurisés pour que toute personne bénéficie d’une protection des liens sécurisés dans les messages électroniques entrants. Chris doit être inclus dans les conditions de stratégie pour obtenir la protection des liens sécurisés.|
|Dans l’organisation de Pat, aucun administrateur n’a créé de stratégies de liens sécurisés, mais la protection des liens sécurisés pour Office 365 applications est activée. Pat ouvre un document Word et clique sur une URL dans le fichier.|Pat n’est pas protégé par des liens fiables. <p> Bien que la protection des liens sécurisés pour Office 365 applications soit activée globalement, Pat n’est pas incluse dans les stratégies de liens fiables actives, de sorte que la protection ne peut pas être appliquée.|
|Dans l’organisation de Lee, `https://tailspintoys.com` est configuré dans la liste **Bloquer les URL suivantes** dans les paramètres globaux des liens fiables. Une stratégie liens sécurisés qui inclut Lee existe déjà. Lee reçoit un e-mail qui contient l’URL `https://tailspintoys.com/aboutus/trythispage`. Lee clique sur l’URL.|L’URL peut être automatiquement bloquée pour Lee ; cela dépend de l’entrée d’URL dans la liste et du client d’e-mail Lee utilisé. Pour plus d’informations, consultez la [liste « Bloquer les URL suivantes » pour la section Liens fiables](#block-the-following-urls-list-for-safe-links) plus loin dans cet article.|
|Jamie et Julia travaillent pour contoso.com. Il y a longtemps, les administrateurs ont configuré des stratégies safe links qui s’appliquent à la fois à Jamie et Julia. Jamie envoie un e-mail à Julia, ne sachant pas que l’e-mail contient une URL malveillante.|Julia est protégée par liens sécurisés **si** la stratégie liens sécurisés qui s’applique à elle est configurée pour s’appliquer aux messages entre destinataires internes. Pour plus d’informations, consultez la section [Liens sécurisés pour les messages électroniques](#safe-links-settings-for-email-messages) plus loin dans cet article.|

## <a name="safe-links-settings-for-email-messages"></a>Paramètres liens sécurisés pour les messages électroniques

Liens fiables analysent le courrier électronique entrant pour les liens hypertexte malveillants connus. Les URL analysées sont réécrites à l’aide du préfixe d’URL standard Microsoft : `https://nam01.safelinks.protection.outlook.com`. Une fois le lien réécrit, il est analysé pour le contenu potentiellement malveillant.

Une fois que les liens fiables ont réécrit une URL, celle-ci reste réécrite même si la réponse et le transfert du message sont _manuels_ (pour les destinataires internes et externes). Les liens supplémentaires ajoutés au message transféré ou répondu ne sont pas réécrits. Toutefois, dans le cas d’un transfert _automatique_ par les règles de boîte de réception ou le transfert SMTP, l’URL ne sera pas réécrite dans le message destiné au destinataire final _, sauf si_ ce destinataire est également protégé par des liens fiables ou si l’URL a déjà été réécrite dans une communication précédente. Tant que les liens fiables sont activés, les URL sont toujours analysées avant la remise, qu’elles aient été réécrites ou non. Les URL non compressées seront également vérifiées par un appel d’API côté client à liens sécurisés au moment du clic dans Outlook pour Desktop version 16.0.12513 ou ultérieure.

Les paramètres des stratégies liens fiables qui s’appliquent aux messages électroniques sont décrits dans la liste suivante :

- **Activé : Liens fiables vérifie une liste de liens malveillants connus lorsque les utilisateurs cliquent sur des liens dans l’e-mail** : active ou désactive l’analyse des liens sécurisés dans les messages électroniques. La valeur recommandée est sélectionnée (activée) et entraîne les actions suivantes :
  - L’analyse des liens fiables est activée dans Outlook (C2R) sur Windows.
  - Les URL sont réécrites et les utilisateurs sont routées via la protection Liens sécurisés lorsqu’ils cliquent sur des URL dans les messages.
  - Lorsque vous cliquez dessus, les URL sont vérifiées par rapport à une liste d’URL malveillantes connues et à la [liste « Bloquer les URL suivantes](#block-the-following-urls-list-for-safe-links) ».
  - Les URL qui n'ont pas une réputation valide sont déclenchées de manière asynchrone en arrière-plan.

  Les paramètres suivants sont disponibles uniquement si l’analyse des liens fiables est activée dans les messages électroniques :

  - **Appliquer des liens sécurisés aux messages électroniques envoyés au sein de l’organisation** : active ou désactive l’analyse des liens sécurisés sur les messages envoyés entre les expéditeurs internes et les destinataires internes au sein de la même Exchange Online organisation. La valeur recommandée est sélectionnée (activée).

  - **Appliquer une analyse en temps réel des URL pour détecter les liens suspects et les liens qui pointent vers des fichiers** : Permet d'analyser en temps réel les liens, y compris les liens dans les messages électroniques qui pointent vers du contenu téléchargeable. La valeur recommandée est sélectionnée (activée).

  - **Attendez la fin de l’analyse des URL avant de remettre le message** :
    - Sélectionné (activé) : les messages qui contiennent des URL sont conservés jusqu’à ce que l’analyse soit terminée. Les messages ne sont remis qu’une fois que les URL sont confirmées comme sûres. Il s’agit de la valeur recommandée.
    - Non sélectionné (désactivé) : si l’analyse d’URL ne peut pas se terminer, remettre le message de toute façon.

  - **Ne réécrivez pas d’URL, effectuez des vérifications via l’API SafeLinks uniquement** : si ce paramètre est activé, aucun habillage d’URL n’a lieu. Les liens sécurisés sont appelés exclusivement par le biais d’API au moment du clic d’URL par les clients Outlook qui la prennent en charge. La valeur recommandée est désactivée.

- **Suivre les clics de l’utilisateur** : active ou désactive le stockage des données de clic liens sécurisés pour les URL cliqués dans les e-mails. La valeur recommandée consiste à laisser ce paramètre sélectionné (suivre les clics de l’utilisateur).

  Le suivi des clics d’URL pour les liens dans les messages électroniques envoyés entre des expéditeurs internes et des destinataires internes n’est actuellement pas pris en charge.

- **Permettre aux utilisateurs de cliquer sur l’URL d’origine** : autorise ou empêche les utilisateurs de cliquer sur la [page d’avertissement](#warning-pages-from-safe-links) vers l’URL d’origine. La valeur recommandée est désactivée.

- **Afficher la personnalisation de l’organisation sur les pages de notification et d’avertissement** : cette option affiche la personnalisation de votre organisation sur les pages d’avertissement. La personnalisation permet aux utilisateurs d’identifier les avertissements légitimes, car les pages d’avertissement Microsoft par défaut sont souvent utilisées par les attaquants. Pour plus d’informations sur la personnalisation de la personnalisation, consultez [Personnaliser le thème Microsoft 365 pour votre organisation](../../admin/setup/customize-your-organization-theme.md).

  Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie Standard et Stricte pour les politiques Safe Links, consultez [Paramètres des stratégie de liens fiables](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- **Filtres de destinataires** : vous devez spécifier les conditions de destinataire et les exceptions qui déterminent à qui la stratégie s’applique. Vous pouvez utiliser ces propriétés pour les conditions et les exceptions :
  - **Le destinataire est**
  - **Le domaine du destinataire est**
  - **Le destinataire est membre de**

  Vous ne pouvez utiliser une condition ou une exception qu'une seule fois, mais la condition ou l'exception peut contenir plusieurs valeurs. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

  > [!IMPORTANT]
  > Plusieurs conditions ou exceptions différentes ne sont pas additives; elles sont inclusives. La stratégie est appliquée _uniquement_ aux destinataires qui correspondent à _tous les_ filtres de destinataires spécifiés. Par exemple, vous configurez une condition de filtre de destinataire dans la stratégie avec les valeurs suivantes :
  >
  > - Le destinataire est : romain@contoso.com
  > - Le destinataire est membre de : Exécutifs
  >
  > La stratégie est appliquée à romain@contoso.com _uniquement_ s’il est également membre des groupes exécutifs. S’il n’est pas membre du groupe, la stratégie ne lui est pas appliquée.
  >
  > De même, si vous utilisez le même filtre de destinataires comme exception à la stratégie, la stratégie n’est pas appliquée à romain@contoso.com _uniquement_ s’il est également membre exécutif. S’il n’est pas membre du groupe, la stratégie s’applique toujours à lui.

- **Priorité** : si vous créez plusieurs stratégies, vous pouvez spécifier l’ordre dans lequel elles sont appliquées. Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

  Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).
  
### <a name="how-safe-links-works-in-email-messages"></a>Fonctionnement des liens sécurisés dans les messages électroniques

À un niveau élevé, voici comment la protection des liens sécurisés fonctionne sur les URL dans les messages électroniques :

1. Tous les e-mails passent par EOP, où le protocole Internet (IP) et les filtres d’enveloppe, la protection contre les programmes malveillants basée sur les signatures, les filtres anti-courrier indésirable et anti-programme malveillant avant la remise du message à la boîte aux lettres du destinataire.

2. L’utilisateur ouvre le message dans sa boîte aux lettres et clique sur une URL dans le message.

3. Safe Links vérifie immédiatement l’URL avant d’ouvrir le site web :

   - Si l’URL est incluse dans la liste **Bloquer les URL suivantes** , un [avertissement d’URL bloquée](#blocked-url-warning) s’ouvre.

   - Si l’URL pointe vers un site web qui a été déterminé comme malveillant, une page [d’avertissement de site web malveillant](#malicious-website-warning) (ou une autre page d’avertissement) s’ouvre.

   - Si l’URL pointe vers un fichier téléchargeable et **que l’analyse d’URL Appliquer en temps réel pour les liens suspects et les liens pointant vers le paramètre de fichiers** est activée dans la stratégie qui s’applique à l’utilisateur, le fichier téléchargeable est vérifié.

   - Si l’URL est déterminée comme étant sécurisée, le site web s’ouvre.

## <a name="safe-links-settings-for-microsoft-teams"></a>Coffre paramètres de liens pour Microsoft Teams

Vous activez ou désactivez la protection Coffre liens pour les Microsoft Teams dans Coffre de liens. Plus précisément, vous utilisez **l’action Sélectionner l’action pour les URL inconnues ou potentiellement malveillantes dans le paramètre Microsoft Teams** . La valeur recommandée est **Activée**.

> [!NOTE]
> Lorsque vous activez ou désactivez la protection des liens sécurisés pour Teams, l’application de la modification peut prendre jusqu’à 24 heures.
>
> Actuellement, la protection des liens sécurisés pour Microsoft Teams n’est pas disponible dans Microsoft 365 GCC High ou Microsoft 365 DoD.

Les paramètres suivants dans les stratégies Liens fiables qui s’appliquent aux liens dans les messages électroniques s’appliquent également aux liens dans Teams :

- **Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers**
- **Ne pas suivre les clics des utilisateurs**
- **Ne pas autoriser les utilisateurs à cliquer sur l’URL d’origine**

Ces paramètres sont expliqués précédemment dans [les paramètres Liens fiables pour les messages électroniques](#safe-links-settings-for-email-messages).

Une fois que vous avez Coffre la protection des liens pour Microsoft Teams, les URL de Teams sont vérifiées par rapport à la liste des liens malveillants connus lorsque l’utilisateur protégé clique sur le lien (protection en temps de clic). Les URL ne sont pas réécrites. Si un lien est jugé malveillant, les utilisateurs auront les expériences suivantes :

- Si le lien a été cliqué dans une conversation Teams, une conversation de groupe ou à partir de canaux, la page d’avertissement, comme illustré dans la capture d’écran ci-dessous, s’affiche dans le navigateur web par défaut.
- Si le lien a été cliqué depuis un onglet épinglé, la page d'avertissement apparaîtra dans l'interface Teams de cet onglet. L'option permettant d'ouvrir le lien dans un navigateur Web est désactivée pour des raisons de sécurité.
- En fonction de la configuration du paramètre **Ne pas autoriser les utilisateurs à cliquer sur l'URL d'origine** dans la stratégie, l'utilisateur sera ou non autorisé à cliquer sur l'URL d'origine (**Continuer quand même (non recommandé)** dans la capture d'écran). Nous vous recommandons d’activer l’option **Ne pas autoriser les utilisateurs à cliquer sur le paramètre d’URL d’origine** pour que les utilisateurs ne puissent pas cliquer sur l’URL d’origine.

Si l’utilisateur qui a envoyé le lien n’est pas inclus dans une stratégie de liens Coffre dans laquelle la protection Teams est activée, l’utilisateur est libre de cliquer sur l’URL d’origine sur son ordinateur ou son appareil.

:::image type="content" source="../../media/tp-safe-links-for-teams-malicious.png" alt-text="Une page Coffre liens vers Teams rapport d’un lien malveillant" lightbox="../../media/tp-safe-links-for-teams-malicious.png":::

Cliquer sur le bouton **Revenir en arrière** dans la page d’avertissement permet de renvoyer l’utilisateur à son contexte d’origine ou à son emplacement d’URL. Toutefois, si vous cliquez à nouveau sur le lien original, Safe Links analysera à nouveau l'URL et la page d'avertissement s'affichera à nouveau.

### <a name="how-safe-links-works-in-teams"></a>Fonctionnement des liens Coffre dans Teams

À un niveau élevé, voici comment fonctionne la protection Coffre liens pour les URL dans Microsoft Teams :

1. Un utilisateur lance l'application Teams.

2. Microsoft 365 vérifie que l'organisation de l'utilisateur inclut Microsoft Defender for Office 365, et que l'utilisateur est inclus dans une politique Safe Links active où la protection pour Microsoft Teams est activée.

3. Les URL sont validées au moment du clic pour l’utilisateur dans les conversations, les conversations de groupe, les canaux et les onglets.

## <a name="safe-links-settings-for-office-365-apps"></a>Paramètres liens sécurisés pour les applications Office 365

La protection des liens sécurisés pour Office 365 applications vérifie les liens dans les documents Office, et non les liens dans les messages électroniques (mais elle peut vérifier les liens dans les documents Office joints dans les messages électroniques une fois le document ouvert).

La protection des liens sécurisés pour les applications Office 365 a les exigences client suivantes :

- Microsoft 365 Apps ou Microsoft 365 Business Premium.
  - Versions actuelles de Word, Excel et PowerPoint sur Windows, Mac ou dans un navigateur web.
  - Applications Office sur des appareils iOS ou Android.
  - Visio sur Windows.
  - OneNote dans un navigateur web.
  - Outlook pour Windows lors de l’ouverture de fichiers EML ou MSG enregistrés.

- Office 365 applications sont configurées pour utiliser l’authentification moderne. Pour plus d’informations, consultez [le fonctionnement de l’authentification moderne pour les applications clientes Office 2013, Office 2016 et Office 2019](../../enterprise/modern-auth-for-office-2013-and-2016.md).

- Les utilisateurs sont connectés à l’aide de leur compte professionnel ou scolaire. Pour plus d’informations, consultez [Se connecter à Office](https://support.microsoft.com/office/b9582171-fd1f-4284-9846-bdd72bb28426).

Vous configurez la protection des liens sécurisés pour Office 365 applications dans les paramètres globaux des liens sécurisés, et non dans les stratégies liens sécurisés. La protection est appliquée à tous les utilisateurs de l’organisation qui disposent d’une licence pour Defender pour Office 365, que les utilisateurs soient inclus ou non dans des stratégies de liens fiables actifs.

Les paramètres Safe Links suivants sont disponibles pour les applications Office 365 :

- **Office 365 applications** : active ou désactive l’analyse des liens sécurisés dans les applications Office 365 prises en charge. La valeur par défaut et recommandée est **Activé**.

- **Ne suivez pas le moment où les utilisateurs cliquent sur Liens sécurisés** : active ou désactive le stockage des liens sécurisés cliquez sur les données pour les URL qui ont cliqué dans les versions de bureau Word, Excel, PowerPoint et Visio. La valeur recommandée est **Désactivée**, ce qui signifie que les clics de l’utilisateur sont suivis.

- **Ne laissez pas les utilisateurs cliquer sur des liens sécurisés vers l’URL d’origine** : autorise ou empêche les utilisateurs de cliquer sur la [page d’avertissement](#warning-pages-from-safe-links) vers l’URL d’origine dans les versions de bureau Word, Excel, PowerPoint et Visio. La valeur par défaut et recommandée est **Activé**.

Pour configurer les paramètres Liens sécurisés pour les applications Office 365, consultez [Configurer la protection des liens sécurisés pour les applications Office 365](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie Standard et Strict, consultez [Paramètres globaux pour liens fiables](recommended-settings-for-eop-and-office365.md#global-settings-for-safe-links).

### <a name="how-safe-links-works-in-office-365-apps"></a>Fonctionnement des liens sécurisés dans les applications Office 365

À un niveau élevé, voici comment la protection des liens sécurisés fonctionne pour les URL dans Office 365 applications. Les applications Office 365 prises en charge sont décrites dans la section précédente.

1. Un utilisateur se connecte à l’aide de son compte professionnel ou scolaire dans une organisation qui inclut Microsoft 365 Apps ou Microsoft 365 Business Premium.

2. L’utilisateur s’ouvre et clique sur un lien vers un document Office dans une application Office prise en charge.

3. Les liens sécurisés vérifient immédiatement l’URL avant d’ouvrir le site web cible :

   - Si l’URL est incluse dans la liste qui ignore l’analyse des liens fiables (la liste **Bloquer les URL suivantes** ), une page [d’avertissement d’URL bloquée](#blocked-url-warning) s’ouvre.

   - Si l’URL pointe vers un site web qui a été déterminé comme malveillant, une page [d’avertissement de site web malveillant](#malicious-website-warning) (ou une autre page d’avertissement) s’ouvre.

   - Si l’URL pointe vers un fichier téléchargeable et que la stratégie Liens fiables qui s’applique à l’utilisateur est configurée pour analyser les liens vers le contenu téléchargeable (**Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers**), le fichier téléchargeable est vérifié.

   - Si l’URL est considérée comme sécurisée, l’utilisateur est emmené sur le site web.

   - Si l’analyse des liens sécurisés ne peut pas se terminer, la protection des liens sécurisés ne se déclenche pas. Dans les clients de bureau Office, l’utilisateur est averti avant de passer au site web de destination.

> [!NOTE]
> Plusieurs secondes peuvent être nécessaires au début de chaque session pour vérifier que les liens sécurisés pour Office sont activés pour l’utilisateur.

## <a name="block-the-following-urls-list-for-safe-links"></a>Liste « Bloquer les URL suivantes » pour les liens fiables

> [!NOTE]
> Vous pouvez désormais gérer les entrées d’URL de bloc dans la [liste d’autorisations/de blocs du locataire](allow-block-urls.md#create-block-url-entries-in-the-tenant-allowblock-list). La liste « Bloquer les URL suivantes » est en cours de dépréciation. Nous allons essayer de migrer des entrées existantes de la liste « Bloquer les URL suivantes » pour bloquer les entrées d’URL dans la liste d’autorisations/de blocs du locataire. Les messages contenant l’URL bloquée seront mis en quarantaine.

La liste **Bloquer les URL suivantes** définit les liens qui sont toujours bloqués par l’analyse des liens fiables aux emplacements suivants :

- Messages électroniques.
- Documents dans Office 365 applications dans Windows et Mac.
- Documents dans Office pour iOS et Android.

Lorsqu’un utilisateur d’une stratégie de liens fiables active clique sur un lien bloqué dans une application prise en charge, il est redirigé vers la page [d’avertissement de l’URL bloquée](#blocked-url-warning) .

Vous configurez la liste des URL dans les paramètres globaux des liens fiables. Pour obtenir des instructions, consultez [Configurer la liste « Bloquer les URL suivantes](configure-global-settings-for-safe-links.md#configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal) ».

**Remarques** :

- Pour obtenir une liste véritablement universelle d’URL bloquées partout, consultez [Gérer la liste d’autorisation/de blocage du locataire](tenant-allow-block-list.md).
- Limites de la liste **Bloquer les URL suivantes** :
  - Le nombre maximal d’entrées est de 500.
  - La longueur maximale d’une entrée est de 128 caractères.
  - Toutes les entrées ne peuvent pas dépasser 10 000 caractères.
- N’incluez pas de barre oblique (`/`) à la fin de l’URL. Par exemple, utilisez `https://www.contoso.com`, pas `https://www.contoso.com/`.
- Une URL de domaine uniquement (par exemple `contoso.com` ou `tailspintoys.com`) bloque toute URL qui contient le domaine.
- Vous pouvez bloquer un sous-domaine sans bloquer le domaine complet. Par exemple, `toys.contoso.com*` bloque toute URL qui contient le sous-domaine, mais elle ne bloque pas les URL qui contiennent le domaine `contoso.com`complet.
- Vous pouvez inclure jusqu’à trois caractères génériques (`*`) par entrée d’URL.

### <a name="entry-syntax-for-the-block-the-following-urls-list"></a>Syntaxe d’entrée pour la liste « Bloquer les URL suivantes »

Les exemples des valeurs que vous pouvez entrer et leurs résultats sont décrits dans le tableau suivant :

|Valeur|Résultat|
|---|---|
|`contoso.com` <p> ou <p> `*contoso.com*`|Bloque le domaine, les sous-domaines et les chemins d’accès. Par exemple, `https://www.contoso.com`, `https://sub.contoso.com`et `https://contoso.com/abc` sont bloqués.|
|`https://contoso.com/a`|Blocs `https://contoso.com/a` , mais pas des sous-chemins supplémentaires comme `https://contoso.com/a/b`.|
|`https://contoso.com/a*`|Blocs `https://contoso.com/a` et sous-chemins supplémentaires comme `https://contoso.com/a/b`.|
|`https://toys.contoso.com*`|Bloque un sous-domaine (`toys` dans cet exemple), mais autorise les clics sur d’autres URL de domaine (like `https://contoso.com` ou `https://home.contoso.com`).|

## <a name="do-not-rewrite-the-following-urls-lists-in-safe-links-policies"></a>Listes « Ne pas réécrire les URL suivantes » dans les stratégies liens fiables

> [!NOTE]
> L’objectif de la liste « Ne pas réécrire les URL suivantes » est d’ignorer l’habillage liens fiables des URL spécifiées. Au lieu d’utiliser cette liste, vous pouvez désormais [créer des entrées d’URL d’autorisation dans la liste d’autorisation/de blocage du locataire](allow-block-urls.md#create-allow-url-entries).

Chaque stratégie De liens fiables contient une liste **Ne pas réécrire les URL suivantes** que vous pouvez utiliser pour spécifier des URL qui ne sont pas réécrites par l’analyse des liens fiables. En d’autres termes, la liste permet aux utilisateurs inclus dans la stratégie d’accéder aux URL spécifiées qui seraient autrement bloquées par des liens fiables. Vous pouvez configurer différentes listes dans différentes stratégies de liens fiables. Le traitement des stratégies s’arrête après l’application de la première stratégie (probablement la priorité la plus élevée) à l’utilisateur. Par conséquent, une seule option **Ne réécrivez pas la liste d’URL suivante** est appliquée à un utilisateur qui est inclus dans plusieurs stratégies de liens fiables actives.

Pour ajouter des entrées à la liste dans des stratégies de liens fiables nouvelles ou existantes, consultez [Créer des stratégies de liens fiables](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) ou [Modifier des stratégies de liens fiables](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-modify-safe-links-policies).

**Remarques** :

- Les clients suivants ne **reconnaissent pas les listes Ne pas réécrire les URL suivantes dans les stratégies Liens** fiables. Les utilisateurs inclus dans les stratégies peuvent être bloqués pour accéder aux URL en fonction des résultats de l’analyse des liens fiables dans ces clients :
  - Microsoft Teams
  - Applications web Office

  Pour obtenir une liste véritablement universelle d’URL autorisées partout, consultez [Gérer la liste d’autorisation/de blocage du locataire](tenant-allow-block-list.md). Toutefois, notez que les URL ajoutées ne seront pas exclues de la réécriture des liens fiables, comme cela doit être fait dans une stratégie liens sécurisés.

- Envisagez d’ajouter des URL internes couramment utilisées à la liste pour améliorer l’expérience utilisateur. Par exemple, si vous avez des services locaux, tels que Skype Entreprise ou SharePoint, vous pouvez ajouter ces URL pour les exclure de l’analyse.
- Si vous n’avez **pas encore réécrit les entrées d’URL suivantes dans vos stratégies Liens sécurisés** , veillez à consulter les listes et à ajouter des caractères génériques si nécessaire. Par exemple, votre liste comporte une entrée similaire `https://contoso.com/a` et vous décidez ultérieurement d’inclure des sous-chemins comme `https://contoso.com/a/b`. Au lieu d’ajouter une nouvelle entrée, ajoutez un caractère générique à l’entrée existante pour qu’elle devienne `https://contoso.com/a/*`.
- Vous pouvez inclure jusqu’à trois caractères génériques (`*`) par entrée d’URL. Les caractères génériques incluent explicitement des préfixes ou des sous-domaines. Par exemple, l’entrée `contoso.com` n’est pas identique `*.contoso.com/*`à , car `*.contoso.com/*` elle permet aux utilisateurs de visiter des sous-domaines et des chemins d’accès dans le domaine spécifié.
- Si une URL utilise la redirection automatique pour HTTP vers HTTPS (par exemple, la redirection 302 pour `http://www.contoso.com` vers `https://www.contoso.com`), et que vous essayez d’entrer les entrées HTTP et HTTPS pour la même URL vers la liste, vous remarquerez peut-être que la deuxième entrée d’URL remplace la première entrée d’URL. Ce comportement ne se produit pas si les versions HTTP et HTTPS de l’URL sont complètement séparées.
- Ne spécifiez pas http:// ou https:// (autrement dit, contoso.com) afin d’exclure les versions HTTP et HTTPS.
- `*.contoso.com` ne couvre **pas** contoso.com, vous devez donc exclure les deux pour couvrir à la fois le domaine spécifié et tous les domaines enfants.
- `contoso.com/*`**couvre uniquement** contoso.com, il n’est donc pas nécessaire d’exclure les deux `contoso.com` et `contoso.com/*`; suffit.`contoso.com/*`
- Pour exclure toutes les itérations d’un domaine, deux entrées d’exclusion sont nécessaires ; `contoso.com/*` et `*.contoso.com/*`. Elles s’associent pour exclure http et HTTPS, les contoso.com de domaine principaux et tous les domaines enfants, ainsi que toute partie ou partie non terminée (par exemple, les contoso.com et les contoso.com/vdir1 sont couverts).

### <a name="entry-syntax-for-the-do-not-rewrite-the-following-urls-list"></a>Syntaxe d’entrée pour la liste « Ne pas réécrire les URL suivantes »

Les exemples des valeurs que vous pouvez entrer et leurs résultats sont décrits dans le tableau suivant :

|Valeur|Résultat|
|---|---|
|`contoso.com`|Autorise l’accès à `https://contoso.com` des sous-domaines ou des chemins d’accès, mais pas à des sous-domaines.|
|`*.contoso.com/*`|Autorise l’accès à un domaine, à des sous-domaines et à des chemins d’accès (par exemple, `https://www.contoso.com`, `https://www.contoso.com`, `https://maps.contoso.com`ou `https://www.contoso.com/a`). <p> Cette entrée est intrinsèquement meilleure que `*contoso.com*`, parce qu’elle n’autorise pas les sites potentiellement frauduleux, comme `https://www.falsecontoso.com` ou `https://www.false.contoso.completelyfalse.com`|
|`https://contoso.com/a`|Autorise l’accès aux `https://contoso.com/a`sous-chemins, mais pas aux sous-chemins comme `https://contoso.com/a/b`|
|`https://contoso.com/a/*`|Autorise l’accès et `https://contoso.com/a` les sous-chemins comme `https://contoso.com/a/b`|

## <a name="warning-pages-from-safe-links"></a>Pages d’avertissement à partir de liens fiables

Cette section contient des exemples des différentes pages d’avertissement déclenchées par la protection des liens sécurisés lorsque vous cliquez sur une URL.

Notez que plusieurs pages d’avertissement ont été mises à jour. Si vous ne voyez pas encore les pages mises à jour, vous le verrez bientôt. Les pages mises à jour incluent un nouveau jeu de couleurs, plus de détails et la possibilité de passer à un site en dépit de l’avertissement et des recommandations donnés.

### <a name="scan-in-progress-notification"></a>Notification d’analyse en cours

L’URL cliqué est analysée par liens fiables. Vous devrez peut-être attendre quelques instants avant de réessayer le lien.

:::image type="content" source="../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png" alt-text="Notification indiquant que le lien est analysé" lightbox="../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png":::

La page de notification d’origine ressemblait à ceci :

:::image type="content" source="../../media/04368763-763f-43d6-94a4-a48291d36893.png" alt-text="Le lien est en cours de notification analysée" lightbox="../../media/04368763-763f-43d6-94a4-a48291d36893.png":::

### <a name="suspicious-message-warning"></a>Avertissement de message suspect

L’URL cliqué se trouvait dans un message électronique similaire à d’autres messages suspects. Nous vous recommandons de vérifier le message électronique avant de passer au site.

:::image type="content" source="../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png" alt-text="Un lien a été cliqué à partir d’un avertissement de message suspect" lightbox="../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png":::

### <a name="phishing-attempt-warning"></a>Avertissement de tentative d’hameçonnage

L’URL cliqué se trouvait dans un e-mail qui a été identifié comme une attaque par hameçonnage. Par conséquent, toutes les URL du message électronique sont bloquées. Nous vous recommandons de ne pas passer au site.

:::image type="content" source="../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png" alt-text="Avertissement indiquant qu’un lien a été cliqué à partir d’un message de hameçonnage" lightbox="../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png":::

### <a name="malicious-website-warning"></a>Avertissement de site web malveillant

L’URL cliqué pointe vers un site identifié comme malveillant. Nous vous recommandons de ne pas passer au site.

:::image type="content" source="../../media/058883c8-23f0-4672-9c1c-66b084796177.png" alt-text="Avertissement indiquant que le site web est classé comme malveillant" lightbox="../../media/058883c8-23f0-4672-9c1c-66b084796177.png":::

La page d’avertissement d’origine ressemblait à ceci :

:::image type="content" source="../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png" alt-text="Avertissement d’origine indiquant que le site web est classé comme malveillant" lightbox="../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png":::

### <a name="blocked-url-warning"></a>Avertissement d’URL bloquée

L’URL cliqué a été bloquée manuellement par un administrateur de votre organisation (la liste **Bloquer les URL suivantes dans les paramètres** globaux des liens fiables). Le lien n’a pas été analysé par safe links, car il a été bloqué manuellement.

Il existe plusieurs raisons pour lesquelles un administrateur bloque manuellement des URL spécifiques. Si vous pensez que le site ne doit pas être bloqué, contactez votre administrateur.

:::image type="content" source="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png" alt-text="Avertissement indiquant que le site web a été bloqué par votre administrateur" lightbox="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png":::

La page d’avertissement d’origine ressemblait à ceci :

:::image type="content" source="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png" alt-text="Avertissement d’origine indiquant que le site web a été bloqué conformément à la stratégie d’URL de votre organisation" lightbox="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png":::

### <a name="error-warning"></a>Avertissement d’erreur

Une erreur s’est produite et l’URL ne peut pas être ouverte.

:::image type="content" source="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png" alt-text="L’avertissement indiquant la page à laquelle vous essayez d’accéder ne peut pas être chargé" lightbox="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png":::

La page d’avertissement d’origine ressemblait à ceci :

:::image type="content" source="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png" alt-text="Avertissement indiquant que la page web n’a pas pu être chargée" lightbox="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png":::
