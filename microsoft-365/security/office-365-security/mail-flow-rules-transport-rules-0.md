---
title: Règles de flux de messagerie dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: 9c2cf227-eff7-48ef-87fb-487186e47363
description: Vous pouvez utiliser des règles de flux de messagerie (règles de transport) pour identifier et prendre des mesures sur les messages qui circulent dans votre organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7f3edb8b764df0699a9837fc1ce261837c636255
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50926843"
---
# <a name="mail-flow-rules-transport-rules-in-standalone-eop"></a>Règles de flux de courriers (règles de transport) dans EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, vous pouvez utiliser des règles de flux de messagerie (également appelées règles de transport) pour identifier les messages qui circulent dans votre organisation et agir sur ces derniers.

Cette rubrique explique les composants des règles de flux de messagerie et leur fonctionnement.

Pour obtenir la procédure de création, de copie et de gestion des règles de flux de messagerie, voir Gérer les règles de [flux de messagerie dans Exchange Online.](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) Pour chaque règle, vous avez la possibilité de l'appliquer, de la tester ou bien de la tester et d'avertir l'expéditeur. Pour en savoir plus sur les options de test, voir Tester les règles de [flux de messagerie](/exchange/security-and-compliance/mail-flow-rules/test-mail-flow-rules) et les [conseils de stratégie dans Exchange Online.](/exchange/security-and-compliance/data-loss-prevention/policy-tips)

Pour obtenir des rapports récapitulatifs et détaillés sur les messages qui correspondent aux règles de flux de messagerie, voir Utiliser les rapports de protection de messagerie pour afficher les données sur les programmes malveillants, le courrier indésirable et les [détections de règles.](/exchange/monitoring/use-mail-protection-reports)

Pour mettre en œuvre des stratégies de messagerie spécifiques à l'aide de règles de flux de messagerie, consultez ces rubriques :

- [Utiliser des règles de flux de messagerie pour inspecter les pièces jointes des messages dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments)

- [Configurer le chiffrement dans Office 365 Entreprise](../../compliance/set-up-encryption.md)

- [Clauses d’exclusion de responsabilité, signatures, pieds de ligne ou en-têtes de message à l’échelle de l’organisation dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers)

- [Utilisation des règles de flux de courrier pour définir le seuil de probabilité de courrier indésirable (SCL) dans les messages](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md)

- [Créer des listes d’expéditeurs bloqués dans EOP](create-block-sender-lists-in-office-365.md)

- [Réduction des menaces de programmes malveillants par le biais du blocage des pièces jointes de fichier dans Exchange Online Protection](reducing-malware-threats-through-file-attachment-blocking-in-exchange-online-pro.md)

- [Définir des règles pour chiffrer ou déchiffrer des messages électroniques dans Office 365](../../compliance/define-mail-flow-rules-to-encrypt-email.md)

La vidéo suivante présente une démonstration de la configuration des règles de flux de messagerie dans EOP autonome.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/7cdcd2cb-9382-4065-98e1-81257b32a189?autoplay=false]

## <a name="mail-flow-rule-components"></a>Composants de règle de flux de messagerie

Une règle de flux de messagerie est constituée de conditions, d’exceptions, d’actions et de propriétés :

- **Conditions**: identifiez les messages à appliquer aux actions. Certaines conditions examinent les champs d’en-tête de message (par exemple, les champs À, De ou Cc). D’autres examinent les propriétés des messages (par exemple l’objet, le corps, les pièces jointes, la taille ou la classification du message). La plupart des conditions font appel à un opérateur de comparaison (par exemple, « égal à », « différent de » ou « contient ») ainsi qu’à une valeur de concordance que vous devez spécifier. S’il n’y a ni conditions ni d’exceptions, la règle s’applique à tous les messages.

Pour plus d’informations sur les conditions de règle de flux de messagerie dans EOP autonome, voir Conditions et exceptions de règle de flux de messagerie [(prédicats) dans Exchange Online.](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

- **Exceptions**: identifient éventuellement les messages à qui les actions ne doivent pas s’appliquer. Les identificateurs de message disponibles dans les conditions le sont également dans les exceptions. Les exceptions ont la priorité sur les conditions et empêchent l’application d’actions à un message, même s’il remplit toutes les conditions configurées.

- **Actions**: spécifiez ce qu’il faut faire aux messages qui correspondent aux conditions de la règle et qui ne correspondent à aucune des exceptions. De nombreuses actions sont possibles, notamment le rejet, la suppression ou la redirection de messages, l’ajout de destinataires supplémentaires, l’ajout de préfixes à l’objet des messages ou l’insertion de clauses d’exclusion de responsabilité dans le corps des messages.

Pour plus d’informations sur les actions de règle de flux de messagerie disponibles dans EOP autonome, voir Actions de règle de flux de messagerie [dans Exchange Online.](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)

- **Propriétés**: spécifiez d’autres paramètres de règles qui ne sont pas des conditions, des exceptions ou des actions. Par exemple, lorsque la règle doit être appliquée, les propriétés indiquent s’il faut appliquer ou tester la règle, ainsi que la période de temps sur laquelle la règle reste active.

  Pour plus d’informations, voir la section [Propriétés des](#mail-flow-rule-properties) règles de flux de messagerie dans cet article.

### <a name="multiple-conditions-exceptions-and-actions"></a>Plusieurs conditions, exceptions et actions

Use a transport rule so messages can bypass Clutter

****

|Composant|Logique|Commentaires|
|---|---|---|
|Commentaires|AND|Un message doit remplir toutes les conditions de la règle. Si vous souhaitez qu'une condition ou une autre s'applique, utilisez des règles distinctes pour chaque condition. Par exemple, si vous souhaitez ajouter la même clause d'exclusion de responsabilité aux messages comportant des pièces jointes et aux messages contenant un texte spécifique, créez une règle pour chaque condition. Vous pouvez facilement copier une règle dans le CAE.|
|Un message doit remplir toutes les conditions de la règle. Si vous souhaitez qu’une condition ou une autre s’applique, utilisez des règles distinctes pour chaque condition. Par exemple, si vous souhaitez ajouter la même clause d’exclusion de responsabilité aux messages comportant des pièces jointes et aux messages dont le contenu correspond à un modèle, créez une règle pour chaque condition. Vous pouvez facilement copier une règle.|OR|Certaines conditions vous permettent de spécifier plusieurs valeurs. Le message doit correspondre à l'une des valeurs spécifiées (pas toutes). Par exemple, si l'objet d'un message électronique est Informations sur le cours des actions et que la condition **L'objet inclut l'un de ces mots** est configurée pour établir une correspondance avec le mot Contoso ou actions, la condition est remplie, car l'objet du message contient au moins l'une des valeurs spécifiées.  |
|Certaines conditions vous permettent de spécifier plusieurs valeurs. Si plusieurs valeurs peuvent être spécifiées pour une condition, le message doit correspondre à l’une des valeurs spécifiées pour cette condition. Par exemple, si l’objet d’un message électronique est Informations sur le cours des actions et que la condition L’objet inclut l’un de ces mots est configurée pour établir une correspondance avec le mot Contoso ou actions, la condition est remplie, car l’objet du message contient au moins l’une des valeurs de condition.|OR|Si un message établit une correspondance avec l'une des exceptions, les actions ne sont pas appliquées. Le message ne doit pas forcément correspondre à toutes les exceptions.|
|Si un message établit une correspondance avec l’une des exceptions, les actions ne sont pas traitées. Le message ne doit pas forcément correspondre à toutes les exceptions.|AND|Les messages qui répondent aux conditions d'une règle permettent d'obtenir toutes les actions qui sont spécifiées dans la règle. Par exemple, si les actions **Ajouter à l'objet du message le préfixe** et **Ajouter des destinataires au champ Cci** sont sélectionnées, les deux actions sont appliquées au message.  <p> Si un message remplit les conditions d’une règle, toutes les actions spécifiées dans la règle en question lui sont appliquées. Par exemple, si les actions Ajouter à l’objet du message le préfixe et Ajouter des destinataires au champ Cci sont sélectionnées, les deux actions sont appliquées au message. La chaîne spécifiée sera ajoutée en préfixe de l’objet du message et les destinataires indiqués seront ajoutés en tant que destinataires Cci.<p> Vous pouvez également définir une action sur une règle de sorte que lorsque cette règle est appliquée, les règles suivantes ne sont pas appliquées au message.|
|

### <a name="mail-flow-rule-properties"></a>Propriétés de règle de flux de messagerie

Le tableau suivant décrit les propriétés de règle qui sont disponibles dans les règles de flux de messagerie.

****

|Nom de la propriété dans le CAE|Nom du paramètre dans PowerShell|Description|
|---|---|---|
|**Priorité**|_Priority_|Indique l'ordre dans lequel les règles sont appliquées aux messages. La priorité par défaut est définie en fonction de la date de création de la règle (les règles plus anciennes ont une priorité plus élevée que les règles plus récentes et les règles haute priorité sont traitées avant les règles basse priorité).   <p> Vous modifiez la priorité de la règle dans le CAE en la déplaçant vers le haut ou le bas de la liste des règles. Dans PowerShell, vous définissez le numéro de priorité (0 est la priorité la plus élevée). <p> Par exemple, si vous disposez d'une règle qui rejette les messages dans lesquels figure un numéro de carte de crédit et d'une autre règle qui exige une approbation, vous voudrez certainement que la règle de rejet soit appliquée en premier et que les autres règles ne s'appliquent pas.  |
|**Mode**|_Mode_|Vous pouvez spécifier si vous souhaitez que la règle commence immédiatement le traitement des messages ou si vous souhaitez tester les règles sans affecter la remise du message (avec ou sans prévention contre la perte de données ou conseils de stratégie DLP). <p> Les conseils de stratégie affichent une courte note dans Outlook ou Outlook sur le web afin d'avertir une personne créant un message de possibles violations de stratégie. Pour plus d'informations, consultez la rubrique **Conseils de stratégie**.  <p> Pour plus d’informations sur les modes, voir **Test a mail flow rule**.|
|**Activer cette règle à la date suivante** <p> **Désactiver cette règle à la date suivante**|_ActivationDate_ <p> _ExpiryDate_|Spécifie la plage de dates au cours de laquelle la règle est active.|
|Case à cocher **Activé** sélectionnée ou non|Nouvelles règles _: paramètre Activé_ sur la cmdlet **New-TransportRule.** <p> Règles existantes : Utilisez les cmdlets **Enable-TransportRule** ou **Disable-TransportRule**. <p> La valeur est affichée dans la propriété **State** de la règle.|Vous pouvez créer une règle désactivée, puis l'activer lorsque vous êtes prêt à la tester. Vous pouvez également désactiver une règle sans la supprimer pour en conserver les paramètres.|
|**Différer le message si le traitement de la règle ne se termine pas**|_RuleErrorAction_|Vous pouvez spécifier la manière dont le message doit être pris en charge si le traitement des règles ne se termine pas. Par défaut, la règle est ignorée, mais vous pouvez choisir de renvoyer ce message en vue de son traitement.|
|**Faire correspondre l'adresse de l'expéditeur dans le message**|_SenderAddressLocation_|Si la règle utilise des conditions ou des exceptions qui examinent l'adresse de messagerie de l'expéditeur, vous pouvez rechercher la valeur dans l'en-tête du message, dans l'enveloppe du message ou dans les deux.|
|**Ne plus traiter de règles**|_SenderAddressLocation_|Il s'agit d'une action de la règle, mais celle-ci ressemble à une propriété dans le CAE. Vous pouvez décider d'arrêter d'appliquer des règles à un message après qu'il a été traité par une règle.|
|**Commentaires**|_Comments_|Vous pouvez entrer des commentaires descriptifs sur la règle.|
|

## <a name="how-mail-flow-rules-are-applied-to-messages"></a>Application des règles de flux de messagerie au courrier électronique

Tous les messages qui transitent par votre organisation sont évalués par rapport aux règles de flux de messagerie activées de celle-ci. Les règles sont traitées dans  l’ordre répertorié dans la page Règles de flux de messagerie dans leAC, ou en fonction de la valeur du paramètre Priority correspondante \>  dans PowerShell. 

Chaque règle offre également la possibilité d'arrêter le traitement des autres règles lorsqu'elle détecte une correspondance. Ce paramètre est important pour les messages qui répondent aux conditions de plusieurs règles de flux de messagerie (quelle règle souhaitez-vous appliquer au message ? Toutes ? Une seule ?).

### <a name="differences-in-processing-based-on-message-type"></a>Différences de traitement selon le type de message

Plusieurs types de messages transitent par une organisation. Le tableau suivant montre ceux qui peuvent être traités par les règles de flux de messagerie.

****

|Il existe plusieurs types de messages qui transitent par une organisation. Le tableau suivant montre quels types de messages peuvent être traités par les règles de transport.|Type de message|
|---|---|
|**Messages ordinaires**: messages qui contiennent un corps de message au format RTF, HTML ou texte brut, ou un ensemble de corps de message en plusieurs parties ou un autre ensemble.|Oui|
|**Chiffrement de messages Office 365**: messages chiffrés par le chiffrement de messages Office 365 dans Office 365. Pour plus d'informations, voir [Chiffrement dans Office 365](../../compliance/encryption.md).|Les règles peuvent toujours accéder aux en-têtes des enveloppes contenus dans des messages protégés et traiter les messages en se basant sur les conditions qui analysent les en-têtes. <p> Pour qu'une règle examine ou modifie le contenu d'un message chiffré, vous devez vérifier que le déchiffrement du transport est activé (Obligatoire ou Facultatif ; la valeur par défaut est Facultatif). Pour plus d’informations, voir [Définir des règles pour chiffrer ou déchiffrer des messages électroniques dans Office 365.](../../compliance/define-mail-flow-rules-to-encrypt-email.md)|
|**Messages chiffrés S/MIME**|Les règles peuvent uniquement accéder aux en-têtes d'enveloppe et traiter les messages en fonction de conditions qui inspectent ces en-têtes. <p> Les règles avec conditions qui requièrent l'inspection du contenu des messages ou les actions qui modifient le contenu des messages ne peuvent pas être traitées.|
|**Messages protégés par RMS**: messages sur services AD RMS (Active Directory Rights Management Services) (AD RMS) ou Azure Rights Management (RMS).|Les règles peuvent toujours accéder aux en-têtes des enveloppes contenus dans des messages protégés et traiter les messages en se basant sur les conditions qui analysent les en-têtes. <p> Pour qu'une règle examine ou modifie le contenu d'un message protégé par RMS, vous devez vérifier que le déchiffrement du transport est activé (Obligatoire ou Facultatif ; la valeur par défaut est Facultatif).|
|**Messages signés en clair**: messages signés mais non chiffrés.|Oui|
|**Messages** de messagerie unifiée : messages créés ou traitées par le service de messagerie unifiée, tels que la messagerie vocale, la télécopie, les notifications d’appels manqués et les messages créés ou transmis à l’aide de Microsoft Outlook Voice Access.|Oui|
|**Messages anonymes**: messages envoyés par des expéditeurs anonymes.|Oui|
|**Rapports de** lecture : rapports générés en réponse aux demandes de réception de lecture des expéditeurs. Les rapports de lecture ont une classe de `IPM.Note*.MdnRead` message de ou `IPM.Note*.MdnNotRead` .|Oui|
|

## <a name="what-else-should-i-know"></a>Que dois-je savoir d’autre ?

- La **valeur de** la propriété Version ou **RuleVersion** d’une règle n’est pas importante dans Exchange Online Protection.

- Une fois que vous avez créé ou modifié une règle de flux de messagerie, l’application de la nouvelle règle ou de la règle mise à jour au courrier électronique peut prendre jusqu’à 30 minutes.

## <a name="for-more-information"></a>Pour plus d'informations

[Utiliser des règles de flux de messagerie pour inspecter les pièces jointes des messages dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments)

[Chiffrement du courrier électronique dans Office 365](../../compliance/email-encryption.md)

[Limites concernant les règles de journal, de transport et de boîte de réception](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#journal-transport-and-inbox-rule-limits)