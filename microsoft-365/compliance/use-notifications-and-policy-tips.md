---
title: Envoi des notifications et affichage des conseils de stratégie pour les stratégies DLP
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleNotifyUser
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Découvrez comment ajouter un conseil de stratégie à une stratégie de protection contre la perte de données (DLP) pour informer un utilisateur qu’il travaille avec du contenu en conflit avec une stratégie DLP.
ms.openlocfilehash: 13387890ca1096115c5c933627ae674aaad15581
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863627"
---
# <a name="send-email-notifications-and-show-policy-tips-for-dlp-policies"></a>Envoi des notifications et affichage des conseils de stratégie pour les stratégies DLP

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Vous pouvez utiliser une stratégie Microsoft Purview de protection contre la perte de données (DLP) pour identifier, surveiller et protéger les informations sensibles dans Office 365. Vous souhaitez que les personnes de votre organisation qui travaillent avec ces informations sensibles restent conformes à vos stratégies DLP, mais vous ne voulez pas les empêcher inutilement de faire leur travail. C’est là que les notifications par e-mail et les conseils de stratégie peuvent vous aider.

![La barre des messages affiche le conseil de stratégie dans Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

Lorsque vous créez une stratégie DLP, vous pouvez configurer les notifications utilisateur pour :

- Envoyez une notification par e-mail aux personnes que vous choisissez pour décrire le problème.

- Affichez un conseil de stratégie pour le contenu en conflit avec la stratégie DLP :

  - Pour les e-mails dans Outlook sur le web et Outlook 2013 et versions ultérieures, le conseil de stratégie s’affiche en haut d’un message au-dessus des destinataires pendant la composition du message.

  - Pour les documents d’un compte OneDrive Entreprise ou d’un site SharePoint Online, le conseil de stratégie est indiqué par une icône d’avertissement qui apparaît sur l’élément. Pour afficher plus d’informations, vous pouvez sélectionner un élément, puis choisir l’icône du volet **Informations**![.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) dans le coin supérieur droit de la page pour ouvrir le volet d’informations.

  - Pour Excel, les PowerPoint et les documents Word stockés sur un site OneDrive Entreprise ou SharePoint site en ligne inclus dans la stratégie DLP, le conseil de stratégie s’affiche dans la barre des messages et le mode Backstage (**Informations** sur le menu \>**Fichier**).

## <a name="add-user-notifications-to-a-dlp-policy"></a>Ajouter des notifications utilisateur à une stratégie DLP

Lorsque vous créez une stratégie DLP, vous pouvez activer **les notifications utilisateur**. Lorsque les notifications utilisateur sont activées, Microsoft 365 envoie des notifications par e-mail et des conseils de stratégie. Vous pouvez personnaliser à qui les e-mails de notification sont envoyés, le texte de l’e-mail et le texte de l’info-bulle de stratégie.

1. Accédez au [portail de conformité Microsoft Purview](https://compliance.microsoft.com/permissions).

2. Connectez-vous à l’aide de votre compte scolaire ou professionnel.

3. Dans le portail de conformité Microsoft Purview \> gauche \> stratégie de **protection contre la perte de** \>  \> données **+ Créer une stratégie**.

    ![Créez un bouton de stratégie.](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)

4. Choisissez le modèle de stratégie DLP qui protège les types d’informations sensibles que vous souhaitez protéger \> **suivant**.

    Pour commencer avec un modèle vide, choisissez **Stratégie** **personnalisée personnalisée** \>  \> Suivant.

5. Nommez la stratégie \> **Suivant**.

6. Pour choisir les emplacements que vous souhaitez protéger par la stratégie DLP, effectuez l’une des opérations suivantes :

   - Choisissez **Tous les emplacements dans Office 365** \> **Suivant**.

   - Choisissez **Laissez-moi choisir des emplacements** \> spécifiques **Suivant**.

   Pour inclure ou exclure un emplacement entier tel que tous les e-mails Exchange ou tous les comptes OneDrive, activez ou désactivez **l’état** de cet emplacement.

   Pour inclure uniquement des sites SharePoint spécifiques ou des comptes OneDrive, activez **l’état**, puis cliquez sur les liens sous **Inclure** pour choisir des sites ou des comptes spécifiques.

7. Choisissez **Utiliser les paramètres** \> avancés **Suivant**.

8. Sélectionnez **+ Nouvelle règle**.

9. Dans l’éditeur de règle, sous **Notifications utilisateur**, activez l’état.

    ![Section Notifications utilisateur de l’éditeur de règles.](../media/47705927-c60b-4054-a072-ab914f33d15d.png)

> [!NOTE]
> Les e-mails de notification sont envoyés sans protection.

## <a name="options-for-configuring-email-notifications"></a>Options de configuration des notifications par e-mail

Pour chaque règle d’une stratégie DLP, vous pouvez :

- Envoyez la notification aux personnes que vous choisissez. Ces personnes peuvent inclure le propriétaire du contenu, la personne qui a modifié le contenu pour la dernière fois, le propriétaire du site où le contenu est stocké ou un utilisateur spécifique.

- Personnalisez le texte inclus dans la notification à l’aide de code HTML ou de jetons. Consultez la rubrique ci-dessous pour plus d’informations.

> [!NOTE]
>
> - Les notifications par e-mail ne peuvent être envoyées qu’à des destinataires individuels, et non à des groupes ou des listes de distribution.
> - Seul le nouveau contenu déclenche une notification par e-mail. La modification du contenu existant déclenche des conseils de stratégie, mais pas des notifications par e-mail.
> - Les expéditeurs externes ne reçoivent pas de notifications. Les notifications sont envoyées uniquement aux utilisateurs internes.

![Options de notification par e-mail.](../media/4e7b9500-2a78-44e6-9067-09f4bfd50301.png)

### <a name="default-email-notification"></a>Notification par e-mail par défaut

Les notifications ont une ligne Objet qui commence par l’action effectuée, telle que « Notification », « Message bloqué » pour l’e-mail ou « Accès bloqué » pour les documents. Si la notification concerne un document, le corps du message de notification inclut un lien qui vous dirige vers le site où le document est stocké et ouvre le conseil de stratégie pour le document, où vous pouvez résoudre les problèmes (voir la section ci-dessous sur les conseils de stratégie). Si la notification concerne un message, la notification inclut en tant que pièce jointe le message qui correspond à une stratégie DLP.

![Message de notification.](../media/35813d40-5fd8-425f-9624-55655e74fa6b.png)

Par défaut, les notifications affichent du texte similaire à ce qui suit pour un élément sur un site. Le texte de notification étant configuré séparément pour chaque règle, le texte affiché diffère en fonction de la règle mise en correspondance.

|Si la règle de stratégie DLP effectue cette opération...|Ensuite, la notification par défaut pour SharePoint ou OneDrive Entreprise documents indique ceci...|Ensuite, la notification par défaut pour Outlook messages indique ceci...|
|---|---|---|
|Envoie une notification, mais n’autorise pas le remplacement|Cet élément est en conflit avec une stratégie de votre organisation.|Votre e-mail est en conflit avec une stratégie de votre organisation.|
|Bloque l’accès, envoie une notification et autorise le remplacement|Cet élément est en conflit avec une stratégie de votre organisation. Si vous ne résolvez pas ce conflit, l’accès à ce fichier peut être bloqué.|Votre e-mail est en conflit avec une stratégie de votre organisation. Le message n’a pas été remis à tous les destinataires.|
|Bloque l’accès et envoie une notification|Cet élément est en conflit avec une stratégie de votre organisation. L’accès à cet élément est bloqué pour tout le monde, à l’exception de son propriétaire, de son dernier modificateur et de l’administrateur de collection de sites principal.|Votre e-mail est en conflit avec une stratégie de votre organisation. Le message n’a pas été remis à tous les destinataires.|

### <a name="custom-email-notification"></a>Notification par e-mail personnalisée

Vous pouvez créer une notification par e-mail personnalisée au lieu d’envoyer la notification par e-mail par défaut à vos utilisateurs finaux ou administrateurs. La notification par e-mail personnalisée prend en charge le code HTML et a une limite de 5 000 caractères. Vous pouvez utiliser html pour inclure des images, une mise en forme et d’autres marques dans la notification.

Vous pouvez également utiliser les jetons suivants pour personnaliser la notification par e-mail. Ces jetons sont des variables qui sont remplacées par des informations spécifiques dans la notification envoyée.

|Jeton|Description|
|---|---|
|%%AppliedActions%%|Actions appliquées au contenu.|
|%%ContentURL%%|URL du document sur le site SharePoint Online ou OneDrive Entreprise site.|
|%%MatchedConditions%%|Conditions qui ont été mises en correspondance par le contenu. Utilisez ce jeton pour informer les utilisateurs des éventuels problèmes liés au contenu.|

![Message de notification indiquant l’emplacement des jetons.](../media/cd3f36b3-40db-4f30-99e4-190750bd1955.png)

## <a name="options-for-configuring-policy-tips"></a>Options de configuration des conseils de stratégie

Pour chaque règle d’une stratégie DLP, vous pouvez configurer des conseils de stratégie pour :

- Informez simplement la personne que le contenu est en conflit avec une stratégie DLP, afin qu’elle puisse prendre des mesures pour résoudre le conflit. Vous pouvez utiliser le texte par défaut (voir les tableaux ci-dessous) ou entrer du texte personnalisé sur les stratégies spécifiques de votre organisation.

- Autoriser la personne à remplacer la stratégie DLP. Si vous le souhaitez, vous pouvez :

  - Demander à la personne d’entrer une justification métier pour remplacer la stratégie. Ces informations sont journalisées et vous pouvez les afficher dans les rapports DLP de la section **Rapports** du portail.

  - Autoriser la personne à signaler un faux positif et à remplacer la stratégie DLP. Ces informations sont également consignées pour la création de rapports, afin que vous puissiez utiliser des faux positifs pour affiner vos règles.

![Options de conseil de stratégie.](../media/0d2f2c68-028a-4900-afe6-1d9fce5303ef.png)

Par exemple, une stratégie DLP peut être appliquée à OneDrive Entreprise sites qui détectent des informations d’identification personnelle (PII), et cette stratégie a trois règles :

1. Première règle : si moins de cinq instances de ces informations sensibles sont détectées dans un document et que le document est partagé avec des personnes au sein de l’organisation, l’action **Envoyer une notification** affiche un conseil de stratégie. Pour les conseils de stratégie, aucune option de remplacement n’est nécessaire, car cette règle avertit simplement les personnes et ne bloque pas l’accès.

2. Deuxième règle : si plus de cinq instances de ces informations sensibles sont détectées dans un document et que le document est partagé avec des personnes au sein de l’organisation, l’action **Bloquer l’accès au contenu** restreint les autorisations pour le fichier et l’action **Envoyer une notification** permet aux utilisateurs de remplacer les actions de cette règle en fournissant une justification métier. L’entreprise de votre organisation nécessite parfois que des personnes internes partagent des données d’identification personnelle, et vous ne souhaitez pas que votre stratégie DLP bloque ce travail.

3. Troisième règle : si plus de cinq instances de ces informations sensibles sont détectées dans un document et que le document est partagé avec des personnes extérieures à l’organisation, l’action **Bloquer l’accès au contenu** restreint les autorisations pour le fichier et l’action **Envoyer une notification** ne permet pas aux utilisateurs de remplacer les actions de cette règle, car les informations sont partagées en externe. En aucun cas, les personnes de votre organisation ne doivent être autorisées à partager des données d’identification personnelle en dehors de l’organisation.

### <a name="user-override-support"></a>Prise en charge des remplacements d’utilisateurs

Voici quelques points à comprendre concernant l’utilisation d’un conseil de stratégie pour remplacer une règle :

- L’option de remplacement est par règle, et elle remplace toutes les actions de la règle (à l’exception de l’envoi d’une notification, qui ne peut pas être substituée).

- Il est possible que le contenu corresponde à plusieurs règles dans une stratégie DLP, mais seul le conseil de stratégie de la règle la plus restrictive et la plus prioritaire s’affiche. Par exemple, un conseil de stratégie à partir d’une règle qui bloque l’accès au contenu est affiché sur un conseil de stratégie à partir d’une règle qui envoie simplement une notification. Cela évite que les personnes voient une cascade de conseils de stratégie.

- Si les conseils de stratégie de la règle la plus restrictive autorisent les utilisateurs à remplacer la règle, toute autre règle également mise en correspondance avec le contenu est aussi remplacée.

- Si l’action NotifyAllowOverride est définie avec WithoutJustification, WithJustification ou FlasePositives, vérifiez que BlockAccess a la valeur true et que BlockAccessScope a la valeur appropriée. Sinon, un conseil de stratégie apparaît, mais l’utilisateur ne trouve pas d’option pour remplacer l’e-mail par une justification.

#### <a name="availability-of-override"></a>Disponibilité du remplacement

|Règle de notification |Notification/Bloquer l’action  |Remplacement disponible  |Exiger une justification  |
|---------|---------|---------|---------|
|Notifier uniquement     |Notification         |Non         |Non         |
|Notify + AllowOverride     |Notification         |Non         |Non         |
|Notification + AllowOverride + Faux positif     |Notification         |Non         |Non         |
|Notify + AllowOverride + With justification     |Notification         |Non         |Non         |
|Notifier + AllowOverride + Faux positif + Sans justification    |Notification         |Non         |Non         |
|Notification + AllowOverride + Faux positif + Avec justification     |Notification         |Non         |Non         |
|Notifier + bloquer     |Bloquer         |Non         |Non         |
|Notify + Block + AllowOverride     |Bloquer         |Oui         |Non         |
|Notification + Bloc + AllowOverride + Faux positif     |Bloquer         |Oui         |Non         |
|Notifier + Bloquer + AllowOverride + Avec justification     |Bloquer         |Oui         |Oui         |
|Notifier + Bloquer + AllowOverride + Faux positif + Sans justification     |Bloquer         |Oui         |Non         |
|Notifier + Bloquer + AllowOverride + Faux positif + Avec justification     |Bloquer         |Oui         |Oui         |


## <a name="policy-tips-on-onedrive-for-business-sites-and-sharepoint-online-sites"></a>Conseils de stratégie sur les sites OneDrive Entreprise et les sites SharePoint Online

Lorsqu’un document sur un site OneDrive Entreprise ou un site SharePoint Online correspond à une règle dans une stratégie DLP et que cette règle utilise des conseils de stratégie, les conseils de stratégie affichent des icônes spéciales sur le document :

1. Si la règle envoie une notification sur le fichier, l’icône d’avertissement s’affiche.

2. Si la règle bloque l’accès au document, l’icône bloquée s’affiche.

   ![Icônes de conseil de stratégie sur les documents d’un compte OneDrive.](../media/d3e9f772-03f9-4d28-82f8-3064784332a2.png)

Pour effectuer une action sur un document, vous pouvez sélectionner un élément \> en sélectionnant l’icône du volet **Informations**![.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) dans le coin supérieur droit de la page pour ouvrir **l’info-bulle de stratégie d’affichage** du volet \> d’informations.

Le conseil de stratégie répertorie les problèmes liés au contenu et, si les conseils de stratégie sont configurés avec ces options, vous pouvez choisir **Résoudre**, puis **remplacer** l’info-bulle de stratégie ou **signaler** un faux positif.

![Volet d’informations montrant l’info-bulle de stratégie.](../media/0a191e70-80f0-4702-90f4-7a5b7aabcaab.png)

![Conseil de stratégie avec option de remplacement.](../media/e250bff9-41d5-4ce4-82ea-1dc2d043fab1.png)

Les stratégies DLP sont synchronisées avec les sites et leur contenu est évalué régulièrement et de façon asynchrone. Il peut donc y avoir un court délai entre le moment où vous créez la stratégie DLP et le moment où vous commencez à voir les conseils de stratégie. Il peut y avoir un délai similaire entre la résolution ou le remplacement d’un conseil de stratégie par rapport au moment où l’icône du document sur le site disparaît.

### <a name="default-text-for-policy-tips-on-sites"></a>Texte par défaut pour les conseils de stratégie sur les sites

Par défaut, les conseils de stratégie affichent du texte similaire à ce qui suit pour un élément sur un site. Le texte de notification étant configuré séparément pour chaque règle, le texte affiché diffère en fonction de la règle mise en correspondance.

|Si la règle de stratégie DLP effectue cette opération...|Ensuite, le conseil de stratégie par défaut indique ceci...|
|---|---|
|Envoie une notification, mais n’autorise pas le remplacement|Cet élément est en conflit avec une stratégie de votre organisation.|
|Bloque l’accès, envoie une notification et autorise le remplacement|Cet élément est en conflit avec une stratégie de votre organisation. Si vous ne résolvez pas ce conflit, l’accès à ce fichier peut être bloqué.|
|Bloque l’accès et envoie une notification|Cet élément est en conflit avec une stratégie de votre organisation. L’accès à cet élément est bloqué pour tout le monde, à l’exception de son propriétaire, de son dernier modificateur et de l’administrateur de collection de sites principal.|

### <a name="custom-text-for-policy-tips-on-sites"></a>Texte personnalisé pour les conseils de stratégie sur les sites

Vous pouvez personnaliser le texte des conseils de stratégie séparément de la notification par e-mail. Contrairement au texte personnalisé pour les notifications par e-mail (voir la section ci-dessus), le texte personnalisé pour les conseils de stratégie n’accepte pas de code HTML ou de jetons. Au lieu de cela, le texte personnalisé pour les conseils de stratégie est du texte brut uniquement avec une limite de 256 caractères.

## <a name="policy-tips-in-outlook-on-the-web-and-outlook-2013-and-later"></a>Conseils de stratégie dans Outlook sur le web et Outlook 2013 et versions ultérieures

Lorsque vous composez un nouvel e-mail dans Outlook sur le web et Outlook 2013 et versions ultérieures, vous verrez un conseil de stratégie si vous ajoutez du contenu qui correspond à une règle dans une stratégie DLP et que cette règle utilise des conseils de stratégie. Le conseil de stratégie s’affiche en haut du message, au-dessus des destinataires, pendant que le message est composé.

![Conseil de stratégie en haut d’un message en cours de composition.](../media/9b3b6b74-17c5-4562-82d5-d17ecaaa8d95.png)

Les conseils de stratégie déterminent si les informations sensibles apparaissent dans le corps du message, la ligne d’objet ou même une pièce jointe de message, comme illustré ici.

![Conseil de stratégie montrant qu’une pièce jointe est en conflit avec une stratégie DLP.](../media/59ae6655-215f-47d9-ad1d-39c0d1e61740.png)

Si les conseils de stratégie sont configurés pour autoriser le remplacement, vous pouvez choisir **Afficher les** \> détails **remplacer** \> entrez une justification métier ou signalez un **faux remplacement positif**\>.

![Conseil de stratégie dans le message développé pour afficher l’option Remplacer.](../media/28bfb997-48a6-41f0-8682-d5e62488458a.png)

![Boîte de dialogue Conseil de stratégie dans laquelle vous pouvez remplacer l’info-bulle de stratégie.](../media/f97e836c-04bd-44b4-aec6-ed9526ea31f8.png)

Notez que lorsque vous ajoutez des informations sensibles à un e-mail, il peut y avoir une latence entre le moment où les informations sensibles sont ajoutées et le moment où l’info-bulle de stratégie s’affiche. Lorsque les e-mails sont chiffrés avec Chiffrement de messages Microsoft Purview et que la stratégie utilisée pour les détecter utilise les conseils de stratégie de condition de chiffrement de détection ne s’affichent pas.

### <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions"></a>Outlook 2013 et versions ultérieures prend en charge l’affichage de conseils de stratégie pour certaines conditions uniquement

Actuellement, Outlook 2013 et versions ultérieures prend en charge l’affichage de conseils de stratégie uniquement pour les conditions suivantes :

- Le contenu contient
- Le contenu est partagé

Notez que les exceptions sont considérées comme des conditions et que toutes ces conditions fonctionnent dans Outlook, où elles correspondent au contenu et appliquent des actions de protection sur le contenu. Toutefois, l’affichage de conseils de stratégie aux utilisateurs n’est pas encore pris en charge. 

> [!NOTE]
> Outlook ne prend pas en charge l’affichage de conseils de stratégie pour une stratégie DLP appliquée à un groupe de distribution dynamique ou à des groupes de sécurité non activés par e-mail. 

### <a name="policy-tips-in-the-exchange-admin-center-vs-the-microsoft-purview-compliance-portal"></a>Conseils de stratégie dans le Centre d’administration Exchange par rapport au portail de conformité Microsoft Purview

Les conseils de stratégie peuvent fonctionner avec des stratégies DLP et des règles de flux de messagerie créées dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a>, ou avec des stratégies DLP créées dans le portail de conformité, mais pas les deux. Cela est dû au fait que ces stratégies sont stockées à différents emplacements, mais que les conseils de stratégie ne peuvent être utilisés qu’à partir d’un emplacement unique.

Si vous avez configuré des conseils de stratégie dans le centre d’administration Exchange, les conseils de stratégie que vous configurez dans le portail de conformité n’apparaissent pas aux utilisateurs dans Outlook sur le web et Outlook 2013 et versions ultérieures jusqu’à ce que vous désactiviez les conseils dans le centre d’administration Exchange. Cela garantit que vos règles de flux de courrier Exchange actuelles (également appelées règles de transport) continueront de fonctionner jusqu’à ce que vous choisissiez de basculer vers le portail de conformité.

Notez que même si les conseils de stratégie ne peuvent être tirés qu’à partir d’un emplacement unique, les notifications par e-mail sont toujours envoyées, même si vous utilisez des stratégies DLP dans le portail de conformité et le centre d’administration Exchange.

### <a name="default-text-for-policy-tips-in-email"></a>Texte par défaut pour les conseils de stratégie dans l’e-mail

Par défaut, les conseils de stratégie affichent du texte similaire à ce qui suit pour l’e-mail.

|Si la règle de stratégie DLP effectue cette opération...|Ensuite, le conseil de stratégie par défaut indique ceci...|
|---|---|
|Envoie une notification, mais n’autorise pas le remplacement|Votre e-mail est en conflit avec une stratégie de votre organisation.|
|Bloque l’accès, envoie une notification et autorise le remplacement|Votre e-mail est en conflit avec une stratégie de votre organisation.|
|Bloque l’accès et envoie une notification|Votre e-mail est en conflit avec une stratégie de votre organisation.|

## <a name="policy-tips-in-excel-powerpoint-and-word"></a>Conseils de stratégie dans Excel, PowerPoint et Word

Lorsque les utilisateurs travaillent avec du contenu sensible dans les versions de bureau de Excel, PowerPoint et Word, les conseils de stratégie peuvent les informer en temps réel que le contenu est en conflit avec une stratégie DLP. Cela nécessite les opérations suivantes :

- Le document Office est stocké sur un site OneDrive Entreprise ou sur un site SharePoint Online.

- Le site est inclus dans une stratégie DLP configurée pour utiliser des conseils de stratégie.

Office programmes de bureau synchronisent automatiquement les stratégies DLP directement à partir de Office 365, puis analysez vos documents pour vous assurer qu’ils ne sont pas en conflit avec vos stratégies DLP et affichez les conseils de stratégie en temps réel.

> [!NOTE]
> Office applications de bureau analysent les documents eux-mêmes pour déterminer si les conseils de stratégie DLP doivent être affichés ; ils n’affichent pas les conseils de stratégie que SharePoint sites en ligne ou OneDrive Entreprise sites ont déjà déterminés doivent être affichés dans un fichier. Par conséquent, il se peut que vous ne voyiez pas toujours un conseil de stratégie DLP dans les applications de bureau que vous voyez dans les sites SharePoint Online ou les sites OneDrive Entreprise. En revanche, les applications Office sur le web affichent uniquement les conseils de stratégie DLP que SharePoint sites en ligne ou OneDrive Entreprise sites ont déjà déterminés doivent être affichés.

Selon la façon dont vous configurez les conseils de stratégie dans la stratégie DLP, les utilisateurs peuvent choisir d’ignorer simplement l’info-bulle de stratégie, de remplacer la stratégie avec ou sans justification métier, ou de signaler un faux positif.

Les conseils de stratégie s’affichent dans la barre des messages.

![La barre de messages affiche le conseil de stratégie dans Excel 2016.](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

Les conseils de stratégie s’affichent également en mode Backstage (sous l’onglet **Fichier** ).

![Backstage affiche le conseil de stratégie dans Excel 2016.](../media/44c561f6-8f3f-4878-b1b0-b7543f8a4120.png)

Si les conseils de stratégie dans la stratégie DLP sont configurés avec ces options, vous pouvez choisir **Résoudre** pour **remplacer** un conseil de stratégie ou **signaler** un faux positif.

![Options du conseil de stratégie dans backstage dans Excel 2016.](../media/5b3857ba-907e-456e-ae43-888b594c049c.png)

Dans chacun de ces Office programmes de bureau, les utilisateurs peuvent choisir de désactiver les conseils de stratégie. S’ils sont désactivés, les conseils de stratégie qui sont des notifications simples n’apparaissent pas dans la barre des messages ou le mode Backstage (sous l’onglet **Fichier** ). Toutefois, des conseils de stratégie sur le blocage et la substitution s’affichent toujours, et ils recevront toujours la notification par e-mail. En outre, la désactivation des conseils de stratégie n’exempte pas le document des stratégies DLP qui lui ont été appliquées.

### <a name="default-text-for-policy-tips-in-excel-2016-powerpoint-2016-and-word-2016"></a>Texte par défaut pour les conseils de stratégie dans Excel 2016, PowerPoint 2016 et Word 2016

Par défaut, les conseils de stratégie affichent du texte similaire à ce qui suit dans la barre des messages et le mode Backstage d’un document ouvert. Le texte de notification étant configuré séparément pour chaque règle, le texte affiché diffère en fonction de la règle mise en correspondance.

|Si la règle de stratégie DLP effectue cette opération...|Ensuite, le conseil de stratégie par défaut indique ceci...|
|---|---|
|Envoie une notification, mais n’autorise pas le remplacement|Ce fichier est en conflit avec une stratégie de votre organisation. Pour plus d’informations, accédez au menu **Fichier** .|
|Bloque l’accès, envoie une notification et autorise le remplacement|Ce fichier est en conflit avec une stratégie de votre organisation. Si vous ne résolvez pas ce conflit, l’accès à ce fichier peut être bloqué. Pour plus d’informations, accédez au menu **Fichier** .|
|Bloque l’accès et envoie une notification|Ce fichier est en conflit avec une stratégie de votre organisation. Si vous ne résolvez pas ce conflit, l’accès à ce fichier peut être bloqué. Pour plus d’informations, accédez au menu **Fichier** .|

### <a name="custom-text-for-policy-tips-in-excel-powerpoint-and-word"></a>Texte personnalisé pour les conseils de stratégie dans Excel, PowerPoint et Word

Vous pouvez personnaliser le texte des conseils de stratégie séparément de la notification par e-mail. Contrairement au texte personnalisé pour les notifications par e-mail (voir la section ci-dessus), le texte personnalisé pour les conseils de stratégie n’accepte pas de code HTML ou de jetons. Au lieu de cela, le texte personnalisé pour les conseils de stratégie est du texte brut uniquement avec une limite de 256 caractères.

## <a name="more-information"></a>Plus d’informations

- [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
- [Conditions de stratégie DLP, exceptions et actions (préversion)](./dlp-microsoft-teams.md)
- [Créer une stratégie DLP pour protéger les documents avec l’ICF ou d’autres propriétés](protect-documents-that-have-fci-or-other-properties.md)
- [Contenu des modèles de stratégie DLP](what-the-dlp-policy-templates-include.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
