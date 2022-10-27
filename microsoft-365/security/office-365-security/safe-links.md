---
title: Vue d’ensemble complète des liens fiables pour Microsoft Defender pour Office 365
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
- m365-security
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
description: Découvrez la protection des liens fiables dans Defender pour Office 365 pour protéger une organisation contre le hameçonnage et d’autres attaques qui utilisent des URL malveillantes. Découvrez les liens fiables Teams et consultez les graphiques des messages de liens fiables.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 174c4b7c4dd36af990920a22abb34fb85fb833d5
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68734030"
---
# <a name="safe-links-in-microsoft-defender-for-office-365"></a>Liens fiables dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](defender-for-office-365.md). Si vous utilisez Outlook.com, Microsoft 365 Famille ou Microsoft 365 Personnel et que vous recherchez des informations sur safelinks dans Outlook, voir [Advanced Outlook.com security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Les liens fiables sont une fonctionnalité [de Defender pour Office 365](defender-for-office-365.md) qui fournit l’analyse des URL et la réécriture des messages électroniques entrants dans le flux de courrier, ainsi que la vérification de l’heure de clic des URL et des liens dans les messages électroniques et d’autres emplacements. L’analyse des liens fiables se produit en plus des [anti-courrier indésirable](anti-spam-protection.md) et [anti-programme malveillant](anti-malware-protection.md) classiques dans les messages électroniques entrants dans Exchange Online Protection (EOP). L’analyse des liens fiables peut permettre de votre organisation contre les liens malveillants utilisés dans le hameçonnage et d’autres attaques.

Regardez cette courte vidéo sur la protection contre les liens malveillants avec des liens fiables dans Microsoft Defender pour Office 365.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGzjb]

> [!NOTE]
> Bien qu’il n’existe aucune stratégie de liens fiables par défaut, la stratégie de sécurité prédéfinie de **protection intégrée** fournit une protection des liens fiables dans les messages électroniques, Microsoft Teams et les fichiers dans les applications Office prises en charge à tous les destinataires disposant d’une licence pour Defender pour Office 365 (utilisateurs qui ne sont pas définis dans les stratégies de sécurité prédéfinies Standard ou Strict ou dans les stratégies de liens fiables personnalisées). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md). Vous pouvez également créer des stratégies de liens fiables qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques. Pour obtenir des instructions, consultez [Configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md).

La protection Liens fiables est disponible dans les emplacements suivants :

- **Email messages** : les protections de liens fiables pour les liens dans les messages électroniques sont contrôlées par les stratégies de liens fiables.

  Pour plus d’informations sur la protection des liens fiables pour les messages électroniques, consultez la section [Paramètres des liens fiables pour les messages électroniques](#safe-links-settings-for-email-messages) plus loin dans cet article.

  > [!NOTE]
  > Les liens fiables ne fonctionnent pas sur les dossiers publics à extension messagerie.
  >
  > Les liens fiables prennent uniquement en charge les formats HTTP(S) et FTP.
  >
  > L’utilisation d’un autre service pour encapsuler des liens avant Defender pour Office 365 peut invalider la capacité des liens fiables à traiter les liens, y compris l’encapsulation, l’explosation ou la validation de la « malveillance » du lien.

- **Microsoft Teams** : La protection des liens fiables pour les liens dans les conversations Teams, les conversations de groupe ou à partir de canaux est contrôlée par les stratégies de liens fiables.

  Pour plus d’informations sur la protection des liens fiables dans Teams, consultez la section [Paramètres des liens fiables pour Microsoft Teams](#safe-links-settings-for-microsoft-teams) plus loin dans cet article.

  > [!NOTE]
  > Actuellement, la protection des liens fiables pour Microsoft Teams n’est pas disponible dans Microsoft 365 GCC High ou Microsoft 365 DoD.

- **Applications Office** : la protection des liens fiables pour les applications de bureau, mobiles et web Office prises en charge est contrôlée par des stratégies de liens fiables.

  Pour plus d’informations sur la protection des liens fiables dans les applications Office, consultez la section [Paramètres des liens fiables pour les applications Office](#safe-links-settings-for-office-apps) plus loin dans cet article.

Cet article inclut des descriptions détaillées des types suivants de paramètres de liens fiables :

- **Paramètres dans les stratégies de liens** fiables : ces paramètres s’appliquent uniquement aux utilisateurs inclus dans les stratégies spécifiques, et les paramètres peuvent être différents d’une stratégie à l’autre. Ces paramètres sont les suivants :

  - [Paramètres des liens fiables pour les messages électroniques](#safe-links-settings-for-email-messages)
  - [Coffre paramètres de liens pour Microsoft Teams](#safe-links-settings-for-microsoft-teams)
  - [Paramètres des liens fiables pour les applications Office](#safe-links-settings-for-office-apps)
  - [Listes « Ne pas réécrire les URL suivantes » dans les stratégies de liens fiables](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)

- **Paramètres globaux des liens fiables** : ces paramètres sont configurés globalement, et non dans les stratégies de liens fiables. Ces paramètres sont les suivants :

  - [Liste « Bloquer les URL suivantes » pour les liens fiables](#block-the-following-urls-list-for-safe-links)

  > [!NOTE]
  > Le menu **Paramètres globaux** et la liste **Bloquer les URL suivantes** pour les liens fiables sont en cours de dépréciation. Utilisez plutôt des entrées de bloc pour les URL dans la [liste verte/bloquée du locataire](allow-block-urls.md#use-the-microsoft-365-defender-portal-to-create-block-entries-for-urls-in-the-tenant-allowblock-list) .

Le tableau suivant décrit des scénarios pour les liens fiables dans Microsoft 365 et les organisations Office 365 qui incluent Defender pour Office 365 (notez que l’absence de licences n’est jamais un problème dans les exemples).

|Scénario|Résultat|
|---|---|
|Jean est membre du service marketing. La protection des liens fiables pour les applications Office est activée dans une stratégie de liens fiables qui s’applique aux membres du service marketing. Jean ouvre une présentation PowerPoint dans un e-mail, puis clique sur une URL dans la présentation.|Jean est protégé par des liens sécurisés. <p> Jean est inclus dans une stratégie de liens fiables où la protection des liens fiables pour les applications Office est activée. <p> Pour plus d’informations sur la configuration requise pour la protection des liens fiables dans les applications Office, consultez la section [Paramètres des liens fiables pour les applications Office](#safe-links-settings-for-office-apps) plus loin dans cet article.|
|Aucune stratégie de liens fiables n’est configurée pour l’organisation Microsoft 365 E5 de Chris. Chris reçoit un e-mail d’un expéditeur externe qui contient une URL vers un site web malveillant qu’il finit par cliquer.|Chris est protégé par des liens fiables. <p> La stratégie de sécurité prédéfinie de **protection intégrée** fournit une protection des liens fiables à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de sécurité prédéfinies Standard ou Strict ou dans les stratégies de liens fiables personnalisées). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).|
|Dans l’organisation de Pat, les administrateurs ont créé une stratégie de liens fiables qui applique Pat, mais la protection des liens fiables pour les applications Office est désactivée. Pat ouvre un document Word et clique sur une URL dans le fichier.|Pat n’est pas protégé par des liens fiables. <p> Bien que Pat soit inclus dans une stratégie de liens fiables active, la protection des liens fiables pour les applications Office est désactivée dans cette stratégie, de sorte que la protection ne peut pas être appliquée.|
|Jamie et Julia travaillent tous deux pour contoso.com. Il y a longtemps, les administrateurs ont configuré des stratégies de liens fiables qui s’appliquent à la fois à Jamie et Julia. Jamie envoie un e-mail à Julia, ne sachant pas que l’e-mail contient une URL malveillante.|Julia est protégée par des liens fiables **si** la stratégie de liens fiables qui s’applique à elle est configurée pour s’appliquer aux messages entre destinataires internes. Pour plus d’informations, consultez la section [Paramètres des liens fiables pour les messages électroniques](#safe-links-settings-for-email-messages) plus loin dans cet article.|

## <a name="recipient-filters-in-safe-links-policies"></a>Filtres de destinataires dans les stratégies de liens fiables

Vous devez spécifier les conditions de destinataire et les exceptions qui déterminent à qui la stratégie s’applique. Vous pouvez utiliser ces propriétés pour les conditions et les exceptions :

- **Utilisateurs**
- **Groupes**
- **Domaines**

Vous ne pouvez utiliser une condition ou une exception qu'une seule fois, mais la condition ou l'exception peut contenir plusieurs valeurs. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

> [!IMPORTANT]
> Plusieurs types de conditions ou exceptions différentes ne sont pas cumulatives ; elles sont inclusives. La stratégie est appliquée _uniquement_ aux destinataires qui correspondent à _tous les_ filtres de destinataires spécifiés. Par exemple, vous configurez une condition de filtre de destinataire dans la stratégie avec les valeurs suivantes :
>
> - Utilisateurs : romain@contoso.com
> - Groupes : Cadres
>
> La stratégie s'applique à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie ne lui est pas appliquée.
>
> De même, si vous utilisez le même filtre de destinataires comme exception à la stratégie, la stratégie n'est pas appliquée à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie s’applique toujours à lui.

## <a name="safe-links-settings-for-email-messages"></a>Paramètres des liens fiables pour les messages électroniques

Liens fiables analysent le courrier électronique entrant pour les liens hypertexte malveillants connus. Les URL analysées sont réécrites ou _encapsulées_ à l’aide du préfixe d’URL standard de Microsoft : `https://nam01.safelinks.protection.outlook.com`. Une fois le lien réécrit, il est analysé pour le contenu potentiellement malveillant.

Une fois que les liens fiables ont réécrit une URL, celle-ci reste réécrite même si la réponse et le transfert du message sont _manuels_ (pour les destinataires internes et externes). Les liens supplémentaires ajoutés au message transféré ou répondu ne sont pas réécrits.

Dans le cas d’un transfert _automatique_ par les règles de boîte de réception ou le transfert SMTP, l’URL n’est pas réécrite dans le message destiné au destinataire final, _sauf si_ l’une des instructions suivantes est vraie :

- Le destinataire est également protégé par des liens fiables.
- L’URL a déjà été réécrite dans une communication précédente.

Tant que la protection des liens fiables est activée, les URL sont analysées avant la remise du message, que les URL soient réécrites ou non. Dans les versions prises en charge d’Outlook (Outlook pour le bureau version 16.0.12513 ou ultérieure), les URL non compressées sont vérifiées par un appel d’API côté client aux liens fiables au moment du clic.

Les paramètres des stratégies de liens fiables qui s’appliquent aux messages électroniques sont décrits dans la liste suivante :

- **Activé : les liens fiables vérifient une liste de liens malveillants connus lorsque les utilisateurs cliquent sur des liens dans un e-mail** : Activez ou désactivez l’analyse des liens fiables dans les messages électroniques. La valeur recommandée est sélectionnée (on) et entraîne les actions suivantes :
  - L’analyse des liens fiables est activée dans Outlook (C2R) sur Windows.
  - Les URL sont réécrites et les utilisateurs sont routés via la protection des liens fiables lorsqu’ils cliquent sur des URL dans les messages.
  - Lorsque vous cliquez dessus, les URL sont vérifiées par rapport à une liste d’URL malveillantes connues et à la [liste « Bloquer les URL suivantes ».](#block-the-following-urls-list-for-safe-links)
  - Les URL qui n'ont pas une réputation valide sont déclenchées de manière asynchrone en arrière-plan.

  Les paramètres suivants sont disponibles uniquement si l’analyse des liens fiables dans les messages électroniques est activée :

  - **Appliquer des liens fiables aux messages électroniques envoyés au sein de l’organisation** : activez ou désactivez l’analyse des liens fiables sur les messages envoyés entre les expéditeurs internes et les destinataires internes au sein de la même organisation Exchange Online. La valeur recommandée est sélectionnée (activée).

  - **Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens pointant vers des fichiers** : active l’analyse en temps réel des liens, y compris les liens dans les e-mails qui pointent vers du contenu téléchargeable. La valeur recommandée est sélectionnée (activée).

    - **Attendez la fin de l’analyse des URL avant de remettre le message** :
      - Sélectionné (activé) : les messages qui contiennent des URL sont conservés jusqu’à ce que l’analyse soit terminée. Les messages ne sont remis qu’une fois que les URL sont confirmées comme sûres. Il s’agit de la valeur recommandée.
      - Non sélectionné (désactivé) : si l’analyse de l’URL ne peut pas se terminer, remettre le message quand même.

  - **Ne réécrire pas d’URL, effectuez des vérifications via l’API SafeLinks uniquement** : si ce paramètre est sélectionné (activé), aucun wrapper d’URL n’a lieu. Dans les versions prises en charge d’Outlook (Outlook pour bureau version 16.0.12513 ou ultérieure), les liens fiables sont appelés exclusivement via les API au moment du clic sur l’URL.

  Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie Standard et Stricte pour les politiques Safe Links, consultez [Paramètres des stratégie de liens fiables](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

### <a name="how-safe-links-works-in-email-messages"></a>Fonctionnement des liens fiables dans les messages électroniques

À un niveau élevé, voici comment la protection des liens fiables fonctionne sur les URL dans les messages électroniques :

1. Tous les e-mails passent par EOP, où le protocole Internet (IP) et les filtres d’enveloppe, la protection contre les programmes malveillants basés sur la signature, les filtres anti-courrier indésirable et anti-programme malveillant avant que le message ne soit remis à la boîte aux lettres du destinataire.

2. L’utilisateur ouvre le message dans sa boîte aux lettres et clique sur une URL dans le message.

3. Les liens fiables vérifient immédiatement l’URL avant d’ouvrir le site web :

   - Si l’URL pointe vers un site web qui a été déterminé comme malveillant, une page [d’avertissement de site web malveillant](#malicious-website-warning) (ou une autre page d’avertissement) s’ouvre.

   - Si l’URL pointe vers un fichier téléchargeable et que le paramètre **Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens pointant vers des fichiers** est activé dans la stratégie qui s’applique à l’utilisateur, le fichier téléchargeable est vérifié.

   - Si l’URL est considérée comme sûre, le site web s’ouvre.

## <a name="safe-links-settings-for-microsoft-teams"></a>Coffre paramètres de liens pour Microsoft Teams

Vous activez ou désactivez la protection des liens fiables pour Microsoft Teams dans les stratégies de liens fiables. Plus précisément, vous utilisez le paramètre **Activé : Liens fiables vérifie une liste de liens malveillants connus lorsque les utilisateurs cliquent sur des liens dans Microsoft Teams** . La valeur recommandée est activée (sélectionnée).

> [!NOTE]
> Lorsque vous activez ou désactivez la protection des liens fiables pour Teams, l’application de la modification peut prendre jusqu’à 24 heures.
>
> Actuellement, la protection des liens fiables pour Microsoft Teams n’est pas disponible dans Microsoft 365 GCC High ou Microsoft 365 DoD.

Une fois que vous avez Coffre la protection des liens pour Microsoft Teams, les URL de Teams sont vérifiées par rapport à la liste des liens malveillants connus lorsque l’utilisateur protégé clique sur le lien (protection en temps de clic). Les URL ne sont pas réécrites. Si un lien est jugé malveillant, les utilisateurs auront les expériences suivantes :

- Si vous avez cliqué sur le lien dans une conversation Teams, une conversation de groupe ou à partir de canaux, la page d’avertissement comme illustré dans la capture d’écran ci-dessous s’affiche dans le navigateur web par défaut.
- Si le lien a été cliqué depuis un onglet épinglé, la page d'avertissement apparaîtra dans l'interface Teams de cet onglet. L'option permettant d'ouvrir le lien dans un navigateur Web est désactivée pour des raisons de sécurité.
- Selon la façon dont le paramètre **Autoriser les utilisateurs à cliquer sur l’URL d’origine** dans la stratégie est configuré, l’utilisateur sera autorisé ou non à cliquer sur l’URL d’origine (**Continuer quand même (non recommandé)** dans la capture d’écran). Nous vous recommandons de ne pas sélectionner le paramètre **Autoriser les utilisateurs à cliquer sur l’URL d’origine** afin que les utilisateurs ne puissent pas cliquer sur l’URL d’origine.

Si l’utilisateur qui a envoyé le lien n’est pas protégé par une stratégie de liens fiables dans laquelle la protection Teams est activée, l’utilisateur est libre de cliquer sur l’URL d’origine sur son ordinateur ou appareil.

:::image type="content" source="../../media/tp-safe-links-for-teams-malicious.png" alt-text="Une page Coffre liens vers Teams rapport d’un lien malveillant" lightbox="../../media/tp-safe-links-for-teams-malicious.png":::

Cliquer sur le bouton **Revenir en arrière** dans la page d’avertissement permet de renvoyer l’utilisateur à son contexte d’origine ou à son emplacement d’URL. Toutefois, si vous cliquez à nouveau sur le lien original, Safe Links analysera à nouveau l'URL et la page d'avertissement s'affichera à nouveau.

### <a name="how-safe-links-works-in-teams"></a>Fonctionnement des liens Coffre dans Teams

À un niveau élevé, voici comment fonctionne la protection Coffre liens pour les URL dans Microsoft Teams :

1. Un utilisateur lance l'application Teams.

2. Microsoft 365 vérifie que l’organisation de l’utilisateur inclut Microsoft Defender pour Office 365 et que l’utilisateur est inclus dans une stratégie de liens fiables active où la protection pour Microsoft Teams est activée.

3. Les URL sont validées au moment du clic pour l’utilisateur dans les conversations, les conversations de groupe, les canaux et les onglets.

## <a name="safe-links-settings-for-office-apps"></a>Paramètres des liens fiables pour les applications Office

La protection des liens fiables pour les applications Office vérifie les liens dans les documents Office, et non les liens dans les messages électroniques. Toutefois, il peut vérifier les liens dans les documents Office joints dans les messages électroniques après l’ouverture du document.

Vous activez ou désactivez la protection des liens fiables pour les applications Office dans les stratégies de liens fiables. Plus précisément, vous utilisez le paramètre **Activé : Liens fiables vérifie une liste de liens malveillants connus lorsque les utilisateurs cliquent sur des liens dans les applications Microsoft Office** . La valeur recommandée est activée (sélectionnée).

La protection des liens fiables pour les applications Office présente les exigences client suivantes :

- Microsoft 365 Apps ou Microsoft 365 Business Premium.
  - Versions actuelles de Word, Excel et PowerPoint sur Windows, Mac ou dans un navigateur web.
  - Applications Office sur des appareils iOS ou Android.
  - Visio sur Windows.
  - OneNote dans un navigateur web.
  - Outlook pour Windows lors de l’ouverture des fichiers EML ou MSG enregistrés.

- Les applications Office sont configurées pour utiliser l’authentification moderne. Pour plus d’informations, voir [Fonctionnement de l’authentification moderne pour les applications clientes Office 2013, Office 2016 et Office 2019](../../enterprise/modern-auth-for-office-2013-and-2016.md).

- Les utilisateurs sont connectés à l’aide de leur compte professionnel ou scolaire. Pour plus d’informations, voir [Se connecter à Office](https://support.microsoft.com/office/b9582171-fd1f-4284-9846-bdd72bb28426).

Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie Standard et Strict, consultez [Paramètres globaux pour les liens fiables](recommended-settings-for-eop-and-office365.md#global-settings-for-safe-links).

### <a name="how-safe-links-works-in-office-apps"></a>Fonctionnement des liens fiables dans les applications Office

À un niveau élevé, voici comment la protection des liens fiables fonctionne pour les URL dans les applications Office. Les applications Office prises en charge sont décrites dans la section précédente.

1. Un utilisateur se connecte à l’aide de son compte professionnel ou scolaire dans une organisation qui inclut Microsoft 365 Apps ou Microsoft 365 Business Premium.

2. L’utilisateur ouvre et clique sur un lien d’un document Office dans une application Office prise en charge.

3. Les liens fiables vérifient immédiatement l’URL avant d’ouvrir le site web cible :

   - Si l’URL est incluse dans la liste qui ignore l’analyse des liens fiables (la liste **Bloquer les URL suivantes** ), une page [d’avertissement d’URL bloquée](#blocked-url-warning) s’ouvre.

   - Si l’URL pointe vers un site web qui a été déterminé comme malveillant, une page [d’avertissement de site web malveillant](#malicious-website-warning) (ou une autre page d’avertissement) s’ouvre.

   - Si l’URL pointe vers un fichier téléchargeable et que la stratégie de liens fiables qui s’applique à l’utilisateur est configurée pour analyser les liens vers du contenu téléchargeable (**Appliquer l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers**), le fichier téléchargeable est vérifié.

   - Si l’URL est considérée comme sûre, l’utilisateur est dirigé vers le site web.

   - Si l’analyse des liens fiables ne peut pas se terminer, la protection des liens fiables ne se déclenche pas. Dans les clients de bureau Office, l’utilisateur est averti avant de passer au site web de destination.

> [!NOTE]
> Plusieurs secondes peuvent être nécessaires au début de chaque session pour vérifier que les liens fiables pour les applications Office sont disponibles pour l’utilisateur.

## <a name="click-protection-settings-in-safe-links-policies"></a>Cliquez sur paramètres de protection dans les stratégies de liens fiables

Ces paramètres s’appliquent aux liens fiables dans les e-mails, Teams et les applications Office :

- **Suivre les clics utilisateur** : activez ou désactivez le stockage des données de clic de liens fiables pour les URL sur lesquelles vous avez cliqué. Nous vous recommandons de laisser ce paramètre sélectionné (activé).

  Dans liens fiables pour les applications Office, ce paramètre s’applique aux versions de bureau Word, Excel, PowerPoint et Visio.

  Si vous sélectionnez ce paramètre, les paramètres suivants sont disponibles :

  - **Autoriser les utilisateurs à cliquer sur l’URL d’origine** : détermine si les utilisateurs peuvent cliquer sur la [page d’avertissement](#warning-pages-from-safe-links) pour atteindre l’URL d’origine. La valeur recommandée n’est pas sélectionnée (désactivée).

    Dans Liens fiables pour les applications Office, ce paramètre s’applique à l’URL d’origine dans les versions de bureau Word, Excel, PowerPoint et Visio.

  - **Afficher la personnalisation de l’organisation sur les pages de notification et d’avertissement** : cette option affiche la personnalisation de votre organisation sur les pages d’avertissement. La personnalisation permet aux utilisateurs d’identifier les avertissements légitimes, car les pages d’avertissement Microsoft par défaut sont souvent utilisées par les attaquants. Pour plus d’informations sur la personnalisation de la personnalisation, consultez [Personnaliser le thème Microsoft 365 pour votre organisation](../../admin/setup/customize-your-organization-theme.md).

## <a name="priority-of-safe-links-policies"></a>Priorité des stratégies de liens fiables

Après avoir créé plusieurs stratégies, vous pouvez spécifier l’ordre dans lequel elles sont appliquées. Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée. La stratégie **de protection intégrée** est toujours appliquée en dernier. Les stratégies de sécurité prédéfinies **Standard** et **Strict** associées aux liens fiables sont toujours appliquées avant les stratégies de liens fiables personnalisées.

Pour plus d’informations sur l’ordre de précédence et la façon dont plusieurs stratégies sont évaluées et appliquées, consultez [Ordre de priorité pour les stratégies de sécurité prédéfinies et d’autres stratégies](preset-security-policies.md#order-of-precedence-for-preset-security-policies-and-other-policies) et [Ordre et priorité de la protection des e-mails](how-policies-and-protections-are-combined.md).

## <a name="block-the-following-urls-list-for-safe-links"></a>Liste « Bloquer les URL suivantes » pour les liens fiables

> [!NOTE]
> La liste **Bloquer les URL suivantes pour les** liens fiables est en cours de dépréciation. Utilisez plutôt des entrées de bloc pour les URL dans la [liste verte/bloquée du locataire](allow-block-urls.md#use-the-microsoft-365-defender-portal-to-create-block-entries-for-urls-in-the-tenant-allowblock-list) . Les messages contenant l’URL bloquée sont mis en quarantaine.

La liste **Bloquer les URL suivantes** définit les liens qui sont toujours bloqués par l’analyse des liens fiables aux emplacements suivants :

- Messages électroniques.
- Documents dans les applications Office sous Windows et Mac.
- Documents dans Office pour iOS et Android.

Lorsqu’un utilisateur d’une stratégie de liens fiables active clique sur un lien bloqué dans une application prise en charge, il est redirigé vers la page [d’avertissement d’URL bloquée](#blocked-url-warning) .

Vous configurez la liste des URL dans les paramètres globaux des liens fiables. Pour obtenir des instructions, consultez [Configurer la liste « Bloquer les URL suivantes ».](configure-global-settings-for-safe-links.md#configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal)

**Remarques** :

- Pour obtenir une liste véritablement universelle des URL bloquées partout, consultez [Gérer la liste verte/bloquée du locataire](manage-tenant-allow-block-list.md).
- Limites de la liste **Bloquer les URL suivantes** :
  - Le nombre maximal d’entrées est de 500.
  - La longueur maximale d’une entrée est de 128 caractères.
  - Toutes les entrées ne peuvent pas dépasser 10 000 caractères.
- N’incluez pas de barre oblique (`/`) à la fin de l’URL. Par exemple, utilisez `https://www.contoso.com`, et non `https://www.contoso.com/`.
- Une URL de domaine uniquement (par exemple `contoso.com` ou `tailspintoys.com`) bloque toute URL qui contient le domaine.
- Vous pouvez bloquer un sous-domaine sans bloquer le domaine complet. Par exemple, `toys.contoso.com*` bloque toute URL qui contient le sous-domaine, mais il ne bloque pas les URL qui contiennent le domaine `contoso.com`complet.
- Vous pouvez inclure jusqu’à trois caractères génériques (`*`) par entrée d’URL.

### <a name="entry-syntax-for-the-block-the-following-urls-list"></a>Syntaxe d’entrée pour la liste « Bloquer les URL suivantes »

Le tableau suivant décrit des exemples de valeurs que vous pouvez entrer et de leurs résultats :

|Valeur|Résultat|
|---|---|
|`contoso.com` <p> or <p> `*contoso.com*`|Bloque le domaine, les sous-domaines et les chemins d’accès. Par exemple, `https://www.contoso.com`, `https://sub.contoso.com`et `https://contoso.com/abc` sont bloqués.|
|`https://contoso.com/a`|Blocs `https://contoso.com/a` , mais pas sous-chemins supplémentaires comme `https://contoso.com/a/b`.|
|`https://contoso.com/a*`|Blocs `https://contoso.com/a` et sous-chemins supplémentaires comme `https://contoso.com/a/b`.|
|`https://toys.contoso.com*`|Bloque un sous-domaine (`toys` dans cet exemple), mais autorise les clics vers d’autres URL de domaine (comme `https://contoso.com` ou `https://home.contoso.com`).|

## <a name="do-not-rewrite-the-following-urls-lists-in-safe-links-policies"></a>Listes « Ne pas réécrire les URL suivantes » dans les stratégies de liens fiables

> [!NOTE]
> Les entrées de la liste « Ne pas réécrire les URL suivantes » ne sont pas analysées ni encapsulées par les liens fiables pendant le flux de courrier. Utilisez [les entrées d’URL d’autorisation dans la liste verte/bloquée du locataire](allow-block-urls.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-urls-in-the-submissions-portal) afin que les URL ne soient pas analysées ou encapsulées par des liens fiables pendant le flux de messagerie _et_ au moment du clic.

Chaque stratégie de liens fiables contient une liste **Ne pas réécrire les URL suivantes** que vous pouvez utiliser pour spécifier des URL qui ne sont pas réécrites par l’analyse des liens fiables. En d’autres termes, la liste permet aux utilisateurs inclus dans la stratégie d’accéder aux URL spécifiées qui seraient autrement bloquées par des liens fiables. Vous pouvez configurer différentes listes dans différentes stratégies de liens fiables. Le traitement de la stratégie s’arrête une fois que la première stratégie (probablement la priorité la plus élevée) est appliquée à l’utilisateur. Par conséquent, une seule liste **d’URL Ne pas réécrire est** appliquée à un utilisateur inclus dans plusieurs stratégies de liens fiables actives.

Pour ajouter des entrées à la liste dans des stratégies de liens fiables nouvelles ou existantes, consultez [Créer des stratégies de liens fiables](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) ou [Modifier des stratégies de liens fiables](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-modify-safe-links-policies).

**Remarques** :

- Les clients suivants ne reconnaissent pas les listes **Ne pas réécrire les URL suivantes dans les** stratégies de liens fiables. Les utilisateurs inclus dans les stratégies peuvent être empêchés d’accéder aux URL en fonction des résultats de l’analyse des liens fiables dans ces clients :
  - Microsoft Teams
  - Applications web Office

  Pour obtenir une liste véritablement universelle des URL autorisées partout, consultez [Gérer la liste verte/bloquée des locataires](manage-tenant-allow-block-list.md). Toutefois, notez que les URL ajoutées ne seront pas exclues de la réécriture des liens fiables, car cela doit être fait dans une stratégie de liens fiables.

- Envisagez d’ajouter des URL internes couramment utilisées à la liste pour améliorer l’expérience utilisateur. Par exemple, si vous avez des services locaux, tels que Skype Entreprise ou SharePoint, vous pouvez ajouter ces URL pour les exclure de l’analyse.
- Si vous avez déjà les entrées **Ne pas réécrire les URL suivantes** dans vos stratégies de liens fiables, veillez à consulter les listes et à ajouter des caractères génériques si nécessaire. Par exemple, votre liste a une entrée comme `https://contoso.com/a` et vous décidez par la suite d’inclure des sous-chemins comme `https://contoso.com/a/b`. Au lieu d’ajouter une nouvelle entrée, ajoutez un caractère générique à l’entrée existante afin qu’elle devienne `https://contoso.com/a/*`.
- Vous pouvez inclure jusqu’à trois caractères génériques (`*`) par entrée d’URL. Les caractères génériques incluent explicitement des préfixes ou des sous-domaines. Par exemple, l’entrée `contoso.com` n’est pas identique `*.contoso.com/*`à , car `*.contoso.com/*` permet aux utilisateurs de visiter des sous-domaines et des chemins d’accès dans le domaine spécifié.
- Si une URL utilise la redirection automatique pour HTTP vers HTTPS (par exemple, redirection 302 pour `http://www.contoso.com` vers `https://www.contoso.com`), et que vous essayez d’entrer les entrées HTTP et HTTPS pour la même URL vers la liste, vous remarquerez peut-être que la deuxième entrée d’URL remplace la première entrée d’URL. Ce comportement ne se produit pas si les versions HTTP et HTTPS de l’URL sont complètement séparées.
- Ne spécifiez pas http:// ou https:// (c’est-à-dire, contoso.com) afin d’exclure les versions HTTP et HTTPS.
- `*.contoso.com` ne couvre **pas** contoso.com. Vous devez donc exclure les deux pour couvrir à la fois le domaine spécifié et les domaines enfants.
- `contoso.com/*` ne couvre **que** contoso.com, il n’est donc pas nécessaire d’exclure à la fois `contoso.com` et `contoso.com/*`; il suffirait simplement `contoso.com/*` .
- Pour exclure toutes les itérations d’un domaine, deux entrées d’exclusion sont nécessaires ; `contoso.com/*` et `*.contoso.com/*`. Ceux-ci se combinent pour exclure à la fois HTTP et HTTPS, le domaine principal contoso.com et tous les domaines enfants, ainsi que toute partie ou ne se terminant pas (par exemple, les deux contoso.com et contoso.com/vdir1 sont couverts).

### <a name="entry-syntax-for-the-do-not-rewrite-the-following-urls-list"></a>Syntaxe d’entrée pour la liste « Ne pas réécrire les URL suivantes »

Le tableau suivant décrit des exemples de valeurs que vous pouvez entrer et de leurs résultats :

|Valeur|Résultat|
|---|---|
|`contoso.com`|Autorise l’accès aux `https://contoso.com` sous-domaines ou chemins d’accès, mais pas.|
|`*.contoso.com/*`|Autorise l’accès à un domaine, à des sous-domaines et à des chemins d’accès (par exemple, `https://www.contoso.com`, `https://www.contoso.com`, `https://maps.contoso.com`ou `https://www.contoso.com/a`). <p> Cette entrée est intrinsèquement meilleure que `*contoso.com*`, car elle n’autorise pas les sites potentiellement frauduleux, comme `https://www.falsecontoso.com` ou `https://www.false.contoso.completelyfalse.com`|
|`https://contoso.com/a`|Autorise l’accès à , mais pas aux `https://contoso.com/a`sous-chemins comme `https://contoso.com/a/b`|
|`https://contoso.com/a/*`|Autorise l’accès aux `https://contoso.com/a` sous-chemins et comme `https://contoso.com/a/b`|

## <a name="warning-pages-from-safe-links"></a>Pages d’avertissement des liens fiables

Cette section contient des exemples des différentes pages d’avertissement déclenchées par la protection des liens fiables lorsque vous cliquez sur une URL.

Notez que plusieurs pages d’avertissement ont été mises à jour. Si vous ne voyez pas encore les pages mises à jour, vous le serez bientôt. Les pages mises à jour incluent un nouveau modèle de couleurs, plus de détails et la possibilité de passer à un site en dépit de l’avertissement et des recommandations donnés.

### <a name="scan-in-progress-notification"></a>Notification d’analyse en cours

L’URL cliquée est analysée par des liens fiables. Vous devrez peut-être attendre quelques instants avant de réessayer le lien.

:::image type="content" source="../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png" alt-text="Notification indiquant que le lien est analysé" lightbox="../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png":::

La page de notification d’origine ressemblait à ceci :

:::image type="content" source="../../media/04368763-763f-43d6-94a4-a48291d36893.png" alt-text="Notification du lien en cours d’analyse" lightbox="../../media/04368763-763f-43d6-94a4-a48291d36893.png":::

### <a name="suspicious-message-warning"></a>Avertissement de message suspect

L’URL cliquée se trouvait dans un e-mail similaire à d’autres messages suspects. Nous vous recommandons de vérifier le message électronique avant de passer au site.

:::image type="content" source="../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png" alt-text="Un lien a été cliqué à partir d’un avertissement de message suspect" lightbox="../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png":::

### <a name="phishing-attempt-warning"></a>Avertissement de tentative d’hameçonnage

L’URL cliquée se trouvait dans un message électronique qui a été identifié comme une attaque par hameçonnage. Par conséquent, toutes les URL de l’e-mail sont bloquées. Nous vous recommandons de ne pas passer au site.

:::image type="content" source="../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png" alt-text="Avertissement indiquant qu’un lien a été cliqué à partir d’un message d’hameçonnage" lightbox="../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png":::

### <a name="malicious-website-warning"></a>Avertissement de site web malveillant

L’URL cliquée pointe vers un site qui a été identifié comme malveillant. Nous vous recommandons de ne pas passer au site.

:::image type="content" source="../../media/058883c8-23f0-4672-9c1c-66b084796177.png" alt-text="L’avertissement indiquant que le site web est classifié comme malveillant" lightbox="../../media/058883c8-23f0-4672-9c1c-66b084796177.png":::

La page d’avertissement d’origine ressemblait à ceci :

:::image type="content" source="../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png" alt-text="Avertissement d’origine indiquant que le site web est classé comme malveillant" lightbox="../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png":::

### <a name="blocked-url-warning"></a>Avertissement d’URL bloquée

L’URL cliquée a été bloquée manuellement par un administrateur de votre organisation (la liste **Bloquer les URL suivantes** dans les paramètres globaux des liens fiables). Le lien n’a pas été analysé par les liens fiables, car il a été bloqué manuellement.

Il existe plusieurs raisons pour lesquelles un administrateur bloque manuellement des URL spécifiques. Si vous pensez que le site ne doit pas être bloqué, contactez votre administrateur.

:::image type="content" source="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png" alt-text="Avertissement indiquant que le site web a été bloqué par votre administrateur" lightbox="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png":::

La page d’avertissement d’origine ressemblait à ceci :

:::image type="content" source="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png" alt-text="Avertissement d’origine indiquant que le site web a été bloqué conformément à la stratégie d’URL de votre organisation" lightbox="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png":::

### <a name="error-warning"></a>Avertissement d’erreur

Une erreur s’est produite et l’URL ne peut pas être ouverte.

:::image type="content" source="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png" alt-text="L’avertissement indiquant que la page à laquelle vous essayez d’accéder ne peut pas être chargé" lightbox="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png":::

La page d’avertissement d’origine ressemblait à ceci :

:::image type="content" source="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png" alt-text="Avertissement indiquant que la page web n’a pas pu être chargée" lightbox="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png":::
