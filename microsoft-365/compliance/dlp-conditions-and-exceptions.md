---
title: Conditions de stratégie DLP, exceptions et actions
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
recommendations: false
description: en savoir plus sur les conditions de stratégie dlp et les exceptions
ms.openlocfilehash: cd252002f2fcef3e3935dd44b1333e801bcba46d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090448"
---
# <a name="dlp-policy-conditions-exceptions-and-actions"></a>Conditions de stratégie DLP, exceptions et actions

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Les conditions et exceptions dans les stratégies DLP identifient les éléments sensibles auxquels la stratégie est appliquée. Les actions définissent ce qui se produit suite à une condition d’exception remplie.

- Les conditions définissent ce qu’il faut inclure
- Les exceptions définissent ce qu’il faut exclure.
- Les actions définissent ce qui se produit suite à la condition ou à l’exception rencontrée

La plupart des conditions et exceptions ont une propriété qui prend en charge une ou plusieurs valeurs. Par exemple, si la stratégie DLP est appliquée à Exchange e-mails, la condition **de l’expéditeur** requiert l’expéditeur du message. Certaines conditions ont deux propriétés. Par exemple, la condition **Un en-tête de message inclut n'importe lequel de ces mots** requiert une propriété pour spécifier le champ d'en-tête du message et une deuxième pour spécifier le texte à rechercher dans le champ d'en-tête. Certaines conditions ou exceptions n'ont aucune propriété. Par exemple, la **condition pièce jointe est protégée par mot de passe** recherche simplement les pièces jointes dans les messages protégés par mot de passe.

Les actions nécessitent généralement des propriétés supplémentaires. Par exemple, lorsque la règle de stratégie DLP redirige un message, vous devez spécifier où le message est redirigé.
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>Conditions et exceptions pour les stratégies DLP

Les tableaux des sections suivantes décrivent les conditions et exceptions disponibles dans DLP.

- [Expéditeurs](#senders)
- [Destinataires](#recipients)
- [Objet ou corps du message](#message-subject-or-body)
- [Pièces jointes](#attachments)
- [En-têtes de message](#message-headers)
- [Propriétés de message](#message-properties)

### <a name="senders"></a>Expéditeurs

Si vous utilisez l’adresse de l’expéditeur comme condition ou exception, le champ réel où la valeur est recherchée varie en fonction de l’emplacement de l’adresse de l’expéditeur configuré. Par défaut, les règles DLP utilisent l’adresse d’en-tête comme adresse de l’expéditeur.

![Image d’un en-tête de courrier montrant la différence entre l’adresse d’enveloppe (P1) et l’adresse d’en-tête (P2)](../media/dlp-conditions-exceptions-meetinginvite-callouts.png)

Au niveau du locataire, vous pouvez configurer un emplacement d’adresse d’expéditeur à utiliser sur toutes les règles, sauf si elle est remplacée par une seule règle. Pour définir la configuration de stratégie DLP du locataire afin d’évaluer l’adresse de l’expéditeur à partir de l’enveloppe sur toutes les règles, vous pouvez exécuter la commande suivante :

```PowerShell
Set-PolicyConfig -SenderAddressLocation Envelope
```

Pour configurer l’emplacement de l’adresse de l’expéditeur au niveau d’une règle DLP, le paramètre est *SenderAddressLocation*. Les valeurs disponibles sont :

- **En-tête** : examinez uniquement les expéditeurs dans les en-têtes de message (par exemple, les champs **From**, **Sender** ou **Reply-To** ). Il s’agit de la valeur par défaut.

- **Enveloppe** : examinez uniquement les expéditeurs de l’enveloppe de message (valeur **MAIL FROM** utilisée dans la transmission SMTP, qui est généralement stockée dans le champ **Chemin d’accès de retour** ).

- **En-tête ou enveloppe** (`HeaderOrEnvelope`) Examinez les expéditeurs dans l’en-tête de message et l’enveloppe du message.

|condition ou exception dans DLP|paramètres de condition/exception dans Microsoft 365 PowerShell|type de propriété|description|
|---|---|---|---|
|L’expéditeur est|condition : *à partir de* <br/><br/> exception : *ExceptIfFrom*|Adresses|Messages envoyés par les boîtes aux lettres, les utilisateurs de messagerie, les contacts de messagerie ou les groupes Microsoft 365 spécifiés dans l’organisation.|
|L'expéditeur est membre de |*FromMemberOf* <br/><br/> *ExceptIfFromMemberOf*|Adresses|Messages envoyés par un membre du groupe de distribution, du groupe de sécurité à extension messagerie ou du groupe Microsoft 365 spécifié.|
|L’adresse IP de l’expéditeur est|condition : *SenderIPRanges*<br/><br/> exception : *ExceptIfSenderIPRanges*|IPAddressRanges|Messages dans lesquels l'adresse IP de l'expéditeur correspond à l'adresse IP spécifiée ou figure dans la plage d'adresses IP spécifiée.|
|L’adresse de l’expéditeur contient des mots|condition : *FromAddressContainsWords* <br/><br/> exception : *ExceptIfFromAddressContainsWords*|Mots|Messages contenant les mots spécifiés dans l'adresse de l'expéditeur.|
|L’adresse de l’expéditeur correspond aux modèles|condition : *FromAddressMatchesPatterns* <br/><br/> exception : *ExceptFromAddressMatchesPatterns*|Modèles|Messages dans lesquels l'adresse de messagerie de l'expéditeur contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|
|Le domaine de l’expéditeur est|condition : *SenderDomainIs* <br/><br/> exception : *ExceptIfSenderDomainIs*|DomainName|Messages dans lesquels le domaine de l'adresse de messagerie de l'expéditeur correspond à la valeur spécifiée. Si vous devez rechercher des domaines d’expéditeur qui *contiennent* le domaine spécifié (par exemple, tout sous-domaine d’un domaine), utilisez la condition *FromAddressMatchesPatterns* (L’adresse de l’expéditeur **correspond**) et spécifiez le domaine à l’aide de la syntaxe «\. domaincom\.$ ».|
|Étendue de l’expéditeur|condition : *FromScope* <br/><br/> exception : *ExceptIfFromScope*|UserScopeFrom|Messages envoyés par des expéditeurs internes ou externes.|
|Les propriétés spécifiées de l'expéditeur contiennent l'un de ces mots|condition : *SenderADAttributeContainsWords* <br/><br/> exception : *ExceptIfSenderADAttributeContainsWords*|Première propriété : `ADAttribute` <br/><br/> Deuxième propriété : `Words`|Messages dans lesquels l'attribut Active Directory spécifié de l'expéditeur contient l'un des mots spécifiés.|
|Les propriétés spécifiées de l'expéditeur correspondent à ces modèles de texte|condition : *SenderADAttributeMatchesPatterns* <br/><br/> exception : *ExceptIfSenderADAttributeMatchesPatterns*|Première propriété : `ADAttribute` <br/><br/> Deuxième propriété : `Patterns`|Messages dans lesquels l'attribut Active Directory spécifié de l'expéditeur contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|

### <a name="recipients"></a>Destinataires

|condition ou exception dans DLP|paramètres de condition/exception dans Microsoft 365 PowerShell|type de propriété|description|
|---|---|---|---|
|Le destinataire est|condition : *SentTo* <br/><br/> exception : *ExceptIfSentTo*|Adresses|Messages où l’un des destinataires est la boîte aux lettres, l’utilisateur de messagerie ou le contact de messagerie spécifié dans l’organisation. Les destinataires peuvent se trouver dans les champs **À**, **Cc** ou **Cci** du message.|
|Le domaine du destinataire est|condition : *RecipientDomainIs* <br/><br/> exception : *ExceptIfRecipientDomainIs*|DomainName|Messages où le domaine de l’adresse e-mail du destinataire correspond à la valeur spécifiée.|
|L'adresse du destinataire contient les mots|condition : *AnyOfRecipientAddressContainsWords* <br/><br/> exception : *ExceptIfAnyOfRecipientAddressContainsWords*|Mots|Messages contenant les mots spécifiés dans l'adresse du destinataire. <br/><br/>**Remarque** : cette condition ne tient pas compte des messages qui sont envoyés aux adresses proxy du destinataire. Elle correspond uniquement aux messages qui sont envoyés à l’adresse de messagerie principale du destinataire.|
|L’adresse du destinataire correspond aux modèles|condition : *AnyOfRecipientAddressMatchesPatterns* <br/><br/> exception : *ExceptIfAnyOfRecipientAddressMatchesPatterns*|Modèles|Messages dans lesquels l'adresse de messagerie du destinataire contient des modèles de texte qui correspondent aux expressions régulières spécifiées. <br/><br/> **Remarque** : cette condition ne tient pas compte des messages qui sont envoyés aux adresses proxy du destinataire. Elle correspond uniquement aux messages qui sont envoyés à l’adresse de messagerie principale du destinataire.|
|Envoyé au membre de|condition : *SentToMemberOf* <br/><br/> exception : *ExceptIfSentToMemberOf*|Adresses|Messages contenant des destinataires membres du groupe de distribution spécifié, du groupe de sécurité à extension messagerie ou du groupe Microsoft 365. Le groupe peut se trouver dans les champs **To**, **Cc** ou **Bcc** du message.|
|Les propriétés spécifiées de l'expéditeur contiennent l'un de ces mots |*RecipientADAttributeContainsWords* <br/><br/> *ExceptIfRecipientADAttributeContainsWords*|Première propriété : `ADAttribute` <br/><br/> Deuxième propriété : `Words`|Messages dans lesquels l'attribut Active Directory spécifié d'un destinataire contient certains mots spécifiés. <br/><br/> Notez que l'attribut **Country** requiert la valeur de code pays à deux lettres (par exemple, DE pour l'Allemagne).|
|Les propriétés spécifiées du destinataire correspondent à ces modèles de texte |*RecipientADAttributeMatchesPatterns* <br/><br/> *ExceptIfRecipientADAttributeMatchesPatterns*|Première propriété : `ADAttribute` <br/><br/> Deuxième propriété : `Patterns`|Messages dans lesquels l'attribut Active Directory spécifié d'un destinataire contient des modèles de texte qui correspondent à l'expression régulière spécifiée.|

### <a name="message-subject-or-body"></a>Objet ou corps du message

|condition ou exception dans DLP|paramètres de condition/exception dans Microsoft 365 PowerShell|type de propriété|description|
|---|---|---|---|
|L’objet contient des mots ou des expressions|condition : *SubjectContainsWords* <br/> exception : *ExceptIf SubjectContainsWords*|Mots|Messages dans lesquels le champ Subject contient les mots spécifiés.|
|L’objet correspond aux modèles|condition : *SubjectMatchesPatterns* <br/> exception : *ExceptIf SubjectMatchesPatterns*|Modèles|Messages où le champ Objet contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|
|Le contenu contient|condition : *ContentContainsSensitiveInformation* <br/> exception *ExceptIfContentContainsSensitiveInformation*|SensitiveInformationTypes|Messages ou documents contenant des informations sensibles tels que définis par les stratégies de protection contre la perte de données (DLP) Microsoft Purview.|
|Modèle de correspondance de l’objet ou du corps|condition : *SubjectOrBodyMatchesPatterns* <br/> exception : *ExceptIfSubjectOrBodyMatchesPatterns*|Modèles|Messages où le champ objet ou le corps du message contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|
|Objet ou corps contient des mots|condition : *SubjectOrBodyContainsWords* <br/> exception : *ExceptIfSubjectOrBodyContainsWords*|Mots|Messages qui ont les mots spécifiés dans le champ d’objet ou le corps du message|
|

### <a name="attachments"></a>Pièces jointes

|condition ou exception dans DLP|paramètres de condition/exception dans Microsoft 365 PowerShell|type de propriété|description|
|---|---|---|---|
|La pièce jointe est protégée par mot de passe|condition : *DocumentIsPasswordProtected* <br/><br/> exception : *ExceptIfDocumentIsPasswordProtected*|none|Messages dans lesquels une pièce jointe est protégée par mot de passe (et ne peut donc pas être analysée). La détection de mot de passe fonctionne uniquement pour les documents Office, les fichiers .zip et les fichiers .7z.|
|L’extension du fichier de pièce jointe est|condition : *ContentExtensionMatchesWords* <br/><br/> exception : *ExceptIfContentExtensionMatchesWords*|Mots|Messages dans lesquels l'extension de fichier de la pièce jointe correspond à l'un des mots spécifiés.|
|Le contenu de la pièce jointe n’a pas pu être analysé|condition : *DocumentIsUnsupported* <br/><br/>exception : *ExceptIf DocumentIsUnsupported*|s/o|Messages où une pièce jointe n’est pas reconnue en mode natif par Exchange Online.|
|L’analyse du contenu de la pièce jointe n’a pas été terminée|condition : *ProcessingLimitExceeded* <br/><br/> exception : *ExceptIfProcessingLimitExceeded*|s/o|Messages pour lesquels le moteur de règles n'a pas pu terminer l'analyse des pièces jointes. Vous pouvez utiliser cette condition pour créer des règles qui fonctionnent conjointement pour identifier et traiter les messages dont le contenu n'a pas pu être entièrement analysé.|
|Le nom du document contient des mots|condition : *DocumentNameMatchesWords* <br/><br/> exception : *ExceptIfDocumentNameMatchesWords*|Mots|Messages où le nom de fichier d’une pièce jointe correspond à l’un des mots spécifiés.|
|Le nom du document correspond aux modèles|condition : *DocumentNameMatchesPatterns* <br/><br/> exception : *ExceptIfDocumentNameMatchesPatterns*|Modèles|Messages dans lesquels le nom de fichier d'une pièce jointe contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|
|La propriété du document est|condition : *ContentPropertyContainsWords* <br/><br/> exception : *ExceptIfContentPropertyContainsWords*|Mots|Messages ou documents dans lesquels l’extension de fichier d’une pièce jointe correspond à l’un des mots spécifiés.|
|La taille du document est égale ou supérieure à|condition : *DocumentSizeOver* <br/><br/> exception : *ExceptIfDocumentSizeOver*|Size|Messages dans lesquels toutes les pièces jointes sont supérieures ou égales à la valeur spécifiée.|
|Un contenu de pièce jointe, quel qu’il soit, comprend l’un de ces mots|condition : *DocumentContainsWords* <br/><br/> exception : *ExceptIfDocumentContainsWords*|`Words`|Messages dans lesquels une pièce jointe contient les mots spécifiés.|
|Tout contenu de pièces jointes correspond à ces modèles de texte|condition : *DocumentMatchesPatterns* <br/><br/> exception : *ExceptIfDocumentMatchesPatterns*|`Patterns`|Messages dans lesquels une pièce jointe contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|

### <a name="message-headers"></a>En-têtes de message

|condition ou exception dans DLP|paramètres de condition/exception dans Microsoft 365 PowerShell|type de propriété|description|
|---|---|---|---|
|L’en-tête contient des mots ou des expressions|condition : *HeaderContainsWords* <br/><br/> exception : *ExceptIfHeaderContainsWords*|Table de hachage|Les messages qui contiennent le champ d’en-tête spécifié et la valeur de ce champ d’en-tête contiennent les mots spécifiés.|
|L’en-tête correspond aux modèles|condition : *HeaderMatchesPatterns* <br/><br/> exception : *ExceptIfHeaderMatchesPatterns*|Table de hachage|Les messages qui contiennent le champ d’en-tête spécifié et la valeur de ce champ d’en-tête contiennent les expressions régulières spécifiées.|

### <a name="message-properties"></a>Propriétés de message

|condition ou exception dans DLP|paramètres de condition/exception dans Microsoft 365 PowerShell|type de propriété|description|
|---|---|---|---|
|Avec importance|condition : *WithImportance* <br/><br/> exception : *ExceptIfWithImportance*|Importance|Messages marqués avec le niveau d’importance spécifié.|
|Le jeu de caractères de contenu contient des mots|condition : *ContentCharacterSetContainsWords* <br/><br/> *ExceptIfContentCharacterSetContainsWords*|Jeux de caractères|Messages qui contiennent l'un des noms de jeux de caractères spécifiés.|
|A le remplacement de l’expéditeur|condition : *HasSenderOverride* <br/><br/> exception : *ExceptIfHasSenderOverride*|s/o|Messages dans lesquels l'expéditeur a choisi de remplacer une stratégie de protection contre la perte de données (DLP). Pour plus d’informations sur les stratégies DLP, consultez [En savoir plus sur la protection contre la perte de données](./dlp-learn-about-dlp.md)|
|Correspondances de type de message|condition : *MessageTypeMatches* <br/><br/> exception : *ExceptIfMessageTypeMatches*|MessageType|Messages du type spécifié. **Remarque** : les types de messages disponibles sont Réponse automatique, Transfert automatique, Chiffrement (S/MIME), Calendrier, Autorisation contrôlée (gestion des droits), Messagerie vocale, Signature, Confirmation de lecture et Demande d’approbation. |
|La taille du message est supérieure ou égale à|condition : *MessageSizeOver* <br/><br/> exception : *ExceptIfMessageSizeOver*|`Size`|Messages dans lesquels la taille totale (message plus pièces jointes) est supérieure ou égale à la valeur spécifiée. **Remarque**: Les limites de taille des messages dans les boîtes aux lettres sont évaluées avant les règles de flux de messagerie. Si un message est trop volumineux pour une boîte aux lettres, il est refusé avant qu'une règle avec cette condition puisse agir sur le message.|

## <a name="actions-for-dlp-policies"></a>Actions pour les stratégies DLP

Ce tableau décrit les actions disponibles dans DLP.

|action dans DLP|paramètres d’action dans Microsoft 365 PowerShell|type de propriété|description|
|---|---|---|---|
|Définir l’en-tête|SetHeader|Première propriété : *Nom de l’en-tête* <br/><br/> Deuxième propriété : *Valeur d’en-tête*|Le paramètre SetHeader spécifie une action pour la règle DLP qui ajoute ou modifie un champ d’en-tête et une valeur dans l’en-tête de message. Ce paramètre utilise la syntaxe « HeaderName:HeaderValue ». Vous pouvez spécifier plusieurs paires nom-valeur d’en-tête séparées par des virgules|
|Supprimer l’en-tête|RemoveHeader|Première propriété : *MessageHeaderField*<br/><br/> Deuxième propriété : *String*|Le paramètre RemoveHeader spécifie une action pour la règle DLP qui supprime un champ d’en-tête de l’en-tête de message. Ce paramètre utilise la syntaxe « HeaderName » ou « HeaderName:HeaderValue ». Vous pouvez spécifier plusieurs noms d’en-tête ou paires nom-valeur d’en-tête séparées par des virgules|
|Rediriger le message vers des utilisateurs spécifiques|*RedirectMessageTo*|Adresses|Redirige le message vers les destinataires spécifiés. Le message n'est pas remis aux destinataires d'origine et aucune notification n'est envoyée à l'expéditeur ou aux destinataires d'origine.|
|Transférer le message pour approbation au responsable de l’expéditeur|Modéré|Première propriété : *ModerateMessageByManager*<br/><br/> Deuxième propriété : *Boolean*|Le paramètre Moderate spécifie une action pour la règle DLP qui envoie le message électronique à un modérateur. Ce paramètre utilise la syntaxe : @{ModerateMessageByManager = <$true \|$false>;|
|Transférer le message pour approbation à des approbateurs spécifiques|Modéré|Première propriété : *ModerateMessageByUser*<br/><br/>Deuxième propriété : *Addresses*|Le paramètre Moderate spécifie une action pour la règle DLP qui envoie le message électronique à un modérateur. Ce paramètre utilise la syntaxe : @{ ModerateMessageByUser = @(« emailaddress1 »,"emailaddress2 »,..."emailaddressN »)}|
|Ajouter un destinataire|AddRecipients|Première propriété : *Field*<br/><br/>Deuxième propriété : *Addresses*|Ajoute un ou plusieurs destinataires au champ To/Cc/Cci du message. Ce paramètre utilise la syntaxe : @{<AddToRecipients \<CopyTo \| BlindCopyTo\> = « emailaddress"}|
|Ajouter le gestionnaire de l’expéditeur en tant que destinataire|AddRecipients|Première propriété : *AddedManagerAction*<br/><br/>Deuxième propriété : *Field*|Ajoute le responsable de l’expéditeur au message en tant que type de destinataire spécifié (To, Cc, Bcc) ou redirige vers le responsable de l’expéditeur sans notification à l’expéditeur ou au destinataire. Cette action fonctionne uniquement si l'attribut Manager de l'expéditeur est défini dans Active Directory. Ce paramètre utilise la syntaxe : @{AddManagerAsRecipientType = « \<To \| Cc \| Bcc\>"}|
Sujet de pré-ajout|PrependSubject|Chaîne|Ajoute le texte spécifié au début du champ Subject du message. Envisagez d'utiliser un espace ou un signe deux-points (:) comme dernier caractère du texte spécifié pour le différencier du texte de l'objet d'origine.  <br/><br/>Pour empêcher l’ajout de la même chaîne aux messages qui contiennent déjà le texte dans l’objet (par exemple, les réponses), ajoutez l’exception « L’objet contient des mots » (ExceptIfSubjectContainsWords) à la règle.|
|Appliquer la clause d’exclusion de responsabilité HTML|ApplyHtmlDisclaimer|Première propriété : *Text*<br/><br/>Deuxième propriété : *Location*<br/><br/>Troisième propriété : *action de secours*|Applique la clause d’exclusion de responsabilité HTML spécifiée à l’emplacement requis du message.<br/><br/>Ce paramètre utilise la syntaxe : @{ Text = " " ; Emplacement = \<Append \| Prepend\>; FallbackAction = \<Wrap \| Ignore \| Reject\> }|
|Supprimer le chiffrement des messages et la protection des droits|RemoveRMSTemplate|s/o|Supprime le chiffrement des messages appliqué à un e-mail|
|Remettre le message à la quarantaine hébergée |*Quarantine*|s/o| Cette action est actuellement en **préversion publique**. Au cours de cette phase, les e-mails mis en quarantaine par les stratégies DLP affichent le type de stratégie ExchangeTransportRule.<br/><br/> Remet le message à la quarantaine dans EOP. Pour plus d’informations, consultez [messages électroniques mis en quarantaine dans EOP](/microsoft-365/security/office-365-security/quarantine-email-messages).|
|Modifier l’objet|ModifySubject|PswsHashTable | Supprimez du texte de la ligne d’objet qui correspond à un modèle spécifique et remplacez-le par un texte différent. Voir l'exemple ci-dessous. Vous pouvez : <br/><br/>- **Remplacer** toutes les correspondances de l’objet par le texte de remplacement <br/><br/>- **Ajoutez** pour supprimer toutes les correspondances dans le sujet et insère le texte de remplacement à la fin de l’objet. <br/><br/>- **Ajouter** pour supprimer toutes les correspondances et insérer le texte de remplacement au début de l’objet. Voir le paramètre ModifySubject in, /powershell/module/exchange/new-dlpcompliancerule|
