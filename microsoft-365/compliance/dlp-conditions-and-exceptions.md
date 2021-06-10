---
title: Conditions, exceptions et actions de stratégie DLP
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
recommendations: false
description: En savoir plus sur les conditions et les exceptions de stratégie dlp
ms.openlocfilehash: 54c66f36e6a4b59147461ad154a4012f62bda77f
ms.sourcegitcommit: 05f40904f8278f53643efa76a907968b5c662d9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52114390"
---
# <a name="dlp-policy-conditions-exceptions-and-actions"></a>Conditions, exceptions et actions de stratégie DLP

Les conditions et les exceptions des stratégies DLP identifient les éléments sensibles à appliquer à la stratégie. Les actions définissent ce qui se produit suite à la définition d’une condition d’exception.

- Les conditions définissent ce qu’il faut inclure
- Les exceptions définissent ce qu’il faut exclure.
- Les actions définissent ce qui se produit en conséquence de la condition ou de l’exception remplie
 
La plupart des conditions et des exceptions ont une propriété qui prend en charge une ou plusieurs valeurs. Par exemple, si la stratégie DLP est appliquée à  Exchange courriers électroniques, la condition « L’expéditeur est » requiert l’expéditeur du message. Certaines conditions ont deux propriétés. Par exemple, la condition **Un en-tête de message inclut n'importe lequel de ces mots** requiert une propriété pour spécifier le champ d'en-tête du message et une deuxième pour spécifier le texte à rechercher dans le champ d'en-tête. Certaines conditions ou exceptions n’ont pas de propriétés. Par exemple, la condition de pièce **jointe protégée** par mot de passe recherche simplement les pièces jointes dans les messages protégés par mot de passe.

Les actions nécessitent généralement des propriétés supplémentaires. Par exemple, lorsque la règle de stratégie DLP redirige un message, vous devez spécifier l’endroit vers lequel le message est redirigé. 
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>Conditions et exceptions pour les stratégies DLP

Les tableaux des sections suivantes décrivent les conditions et les exceptions disponibles dans DLP.

- [Expéditeurs](#senders)
- [Destinataires](#recipients)
- [Objet ou corps du message](#message-subject-or-body)
- [Pièces jointes](#attachments)
- [En-têtes de message](#message-headers)
- [Propriétés de message](#message-properties)

### <a name="senders"></a>Expéditeurs


|**condition ou exception dans DLP**  |**paramètres condition/exception dans Microsoft 365 PowerShell** |**type de propriété**  |**description**|
|---------|---------|---------|---------|
|L’expéditeur est |condition : *From* <br/> exception : *ExceptIfFrom*      |Adresses |     Messages envoyés par les boîtes aux lettres, les utilisateurs de messagerie, les contacts de messagerie ou les groupes Microsoft 365 spécifiés dans l’organisation.|
|L’adresse IP de l’expéditeur est     |condition : *SenderIPRanges*<br/> exception : *ExceptIfSenderIPRanges*         |  IPAddressRanges       | Messages dans lesquels l'adresse IP de l'expéditeur correspond à l'adresse IP spécifiée ou figure dans la plage d'adresses IP spécifiée.       |
|L’adresse de l’expéditeur contient des mots   | condition : *FromAddressContainsWords* <br/> exception : *ExceptIfFromAddressContainsWords*        |   Mots      |   Messages contenant les mots spécifiés dans l'adresse de l'expéditeur.|
| L’adresse de l’expéditeur correspond aux modèles    | condition : *FromAddressMatchesPatterns* <br/> exception : *ExceptFromAddressMatchesPatterns*       |      Modèles   |  Messages dans lesquels l'adresse de messagerie de l'expéditeur contient des modèles de texte qui correspondent aux expressions régulières spécifiées.  |
|Le domaine de l’expéditeur est  |  condition : *SenderDomainIs* <br/> exception : *ExceptIfSenderDomainIs*       |DomainName         |     Messages dans lesquels le domaine de l'adresse de messagerie de l'expéditeur correspond à la valeur spécifiée. Si vous devez rechercher des  domaines d’expéditeur qui contiennent le domaine spécifié (par exemple, n’importe quel sous-domaine d’un domaine), utilisez la condition « The **sender address matches**(*FromAddressMatchesPatterns*) et spécifiez le domaine à l’aide de la syntaxe : ' \. domain \. com$'.    |
|Étendue de l’expéditeur    | condition : *FromScope* <br/> exception : *ExceptIfFromScope*    | UserScopeFrom    |    Messages envoyés par des expéditeurs internes ou externes.    |
|Les propriétés spécifiées de l'expéditeur contiennent l'un de ces mots|condition : *SenderADAttributeContainsWords* <br/> exception : *ExceptIfSenderADAttributeContainsWords*|Première propriété : `ADAttribute` <p> Deuxième propriété : `Words`|Messages dans lesquels l'attribut Active Directory spécifié de l'expéditeur contient l'un des mots spécifiés.|
|Les propriétés spécifiées de l'expéditeur correspondent à ces modèles de texte|condition : *SenderADAttributeMatchesPatterns* <br/> exception : *ExceptIfSenderADAttributeMatchesPatterns*|Première propriété : `ADAttribute` <p> Deuxième propriété : `Patterns`|Messages dans lesquels l'attribut Active Directory spécifié de l'expéditeur contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|

### <a name="recipients"></a>Destinataires

|**condition ou exception dans DLP**| **paramètres condition/exception dans Microsoft 365 PowerShell** |    **type de propriété** | **description**|
|---------|---------|---------|---------|
|Le destinataire est|  condition : *SentTo* <br/> exception : *ExceptIfSentTo* | Adresses | Messages dans lequel l’un des destinataires est la boîte aux lettres, l’utilisateur de messagerie ou le contact de messagerie spécifié dans l’organisation. Les destinataires peuvent se trouver dans les champs **À,** **Cc** ou **Cci** du message.|
|Le domaine du destinataire est|   condition : *RecipientDomainIs* <br/> exception : *ExceptIfRecipientDomainIs* |   DomainName |    Messages dans lequel le domaine de l’adresse e-mail du destinataire correspond à la valeur spécifiée.|
|L’adresse du destinataire contient des mots|  condition : *AnyOfRecipientAddressContainsWords* <br/> exception : *ExceptIfAnyOfRecipientAddressContainsWords*|  Mots|  Messages contenant les mots spécifiés dans l'adresse du destinataire. <br/>**Remarque** : cette condition ne tient pas compte des messages qui sont envoyés aux adresses proxy du destinataire. Elle correspond uniquement aux messages qui sont envoyés à l’adresse de messagerie principale du destinataire.|
|L’adresse du destinataire correspond aux modèles| condition : *AnyOfRecipientAddressMatchesPatterns* <br/> exception : *ExceptIfAnyOfRecipientAddressMatchesPatterns*| Modèles    |Messages dans lesquels l'adresse de messagerie du destinataire contient des modèles de texte qui correspondent aux expressions régulières spécifiées. <br/> **Remarque** : cette condition ne tient pas compte des messages qui sont envoyés aux adresses proxy du destinataire. Elle correspond uniquement aux messages qui sont envoyés à l’adresse de messagerie principale du destinataire.|
|Envoyé au membre de| condition : *SentToMemberOf* <br/> exception : *ExceptIfSentToMemberOf*|  Adresses|  Messages contenant des destinataires membres du groupe de distribution spécifié, du groupe de sécurité à messagerie ou du groupe Microsoft 365 messagerie. Le groupe peut se trouver dans les champs **To**, **Cc** ou **Bcc** du message.|

### <a name="message-subject-or-body"></a>Objet ou corps du message

|**condition ou exception dans DLP** | **paramètres condition/exception dans Microsoft 365 PowerShell** |**type de propriété**| **description**|
|---------|---------|---------|---------|
|L’objet contient des mots ou des expressions| condition : *SubjectContainsWords* <br/> exception : *ExceptIf SubjectContainsWords*| Mots   |Messages dans lesquels le champ Subject contient les mots spécifiés.|
|L’objet correspond aux modèles|condition : *SubjectMatchesPatterns* <br/> exception : *ExceptIf SubjectMatchesPatterns*|Modèles   |Messages dans lequel le champ Objet contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|
|Le contenu contient|  condition : *ContentContainsSensitiveInformation* <br/> exception *ExceptIfContentContainsSensitiveInformation*| SensitiveInformationTypes|  Messages ou documents qui contiennent des informations sensibles telles que définies par les stratégies de protection contre la perte de données (DLP).|
| Modèle de correspondances objet ou corps    | condition : *SubjectOrBodyMatchesPatterns* <br/> exception : *ExceptIfSubjectOrBodyMatchesPatterns*    | Modèles    | Messages dans lequel le champ d’objet ou le corps du message contient des modèles de texte qui correspondent aux expressions régulières spécifiées.    |
| L’objet ou le corps contient des mots    | condition : *SubjectOrBodyContainsWords* <br/> exception : *ExceptIfSubjectOrBodyContainsWords*    | Mots    | Messages qui ont les mots spécifiés dans le champ d’objet ou le corps du message    |


### <a name="attachments"></a>Pièces jointes

|**condition ou exception dans DLP**| **paramètres condition/exception dans Microsoft 365 PowerShell**| **type de propriété**   |**description**|
|---------|---------|---------|---------|
|La pièce jointe est protégée par mot de passe|condition : *DocumentIsPasswordProtected* <br/> exception : *ExceptIfDocumentIsPasswordProtected*|aucune| Messages dans lesquels une pièce jointe est protégée par mot de passe (et ne peut donc pas être analysée). La détection de mot de passe fonctionne uniquement Office documents, .zip fichiers et fichiers .7z.|
|L’extension de fichier de la pièce jointe est|condition : *ContentExtensionMatchesWords* <br/> exception : *ExceptIfContentExtensionMatchesWords*|  Mots   |Messages dans lesquels l'extension de fichier de la pièce jointe correspond à l'un des mots spécifiés.|
|Le contenu d’une pièce jointe n’a pas pu être analysé|condition : *DocumentIsUnsupported* <br/>exception : *ExceptIf DocumentIsUnsupported*|   s/o|    Messages dans lequel une pièce jointe n’est pas reconnue en Exchange Online.|
|Le contenu d’une pièce jointe n’a pas terminé l’analyse|   condition : *ProcessingLimitExceeded* <br/> exception : *ExceptIfProcessingLimitExceeded*|    s/o |Messages pour lesquels le moteur de règles n'a pas pu terminer l'analyse des pièces jointes. Vous pouvez utiliser cette condition pour créer des règles qui fonctionnent conjointement pour identifier et traiter les messages dont le contenu n'a pas pu être entièrement analysé.|
|Le nom du document contient des mots|condition : *DocumentNameMatchesWords* <br/> exception : *ExceptIfDocumentNameMatchesWords* |Mots  |Messages dans lequel le nom de fichier d’une pièce jointe correspond à l’un des mots spécifiés.|
|Le nom du document correspond aux modèles|condition : *DocumentNameMatchesPatterns* <br/> exception : *ExceptIfDocumentNameMatchesPatterns*|    Modèles    |Messages dans lesquels le nom de fichier d'une pièce jointe contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|
|La propriété du document est|condition : *ContentPropertyContainsWords* <br/> exception : *ExceptIfContentPropertyContainsWords* |Mots| Messages ou documents dans lequel l’extension de fichier d’une pièce jointe correspond à l’un des mots spécifiés.|
|La taille du document est égale ou supérieure à| condition : *DocumentSizeOver* <br/> exception : *ExceptIfDocumentSizeOver*|    Size    |Messages dans lesquels toutes les pièces jointes sont supérieures ou égales à la valeur spécifiée.|
|Un contenu de pièce jointe, quel qu’il soit, comprend l’un de ces mots| condition : *DocumentContainsWords* <br/> exception : *ExceptIfDocumentContainsWords* |`Words`|Messages dans lesquels une pièce jointe contient les mots spécifiés.|
|Le contenu des pièces jointes correspond à ces modèles de texte|condition : *DocumentMatchesPatterns* <br/> exception : *ExceptIfDocumentMatchesPatterns* |`Patterns`|Messages dans lesquels une pièce jointe contient des modèles de texte qui correspondent aux expressions régulières spécifiées. |

### <a name="message-headers"></a>En-têtes de message

|**condition ou exception dans DLP**| **paramètres condition/exception dans Microsoft 365 PowerShell**| **type de propriété**|  **description**|
|---------|---------|---------|---------|
|L’en-tête contient des mots ou des expressions|condition : *HeaderContainsWords* <br/> exception : *ExceptIfHeaderContainsWords*|  Hash Table  |Les messages qui contiennent le champ d’en-tête spécifié et la valeur de ce champ d’en-tête contiennent les mots spécifiés.|
|L’en-tête correspond aux modèles|   condition : *HeaderMatchesPatterns* <br/> exception : *ExceptIfHeaderMatchesPatterns*|    Hash Table  |Les messages qui contiennent le champ d’en-tête spécifié et la valeur de ce champ d’en-tête contiennent les expressions régulières spécifiées.|

### <a name="message-properties"></a>Propriétés de message

|**condition ou exception dans DLP**| **paramètres condition/exception dans Microsoft 365 PowerShell**| **type de propriété**   |**description**|
|---------|---------|---------|---------|
| Avec importance    | condition : *WithImportance* <br/> exception : *ExceptIfWithImportance*    | Importance    | Messages marqués avec le niveau d’importance spécifié.    |
| Le jeu de caractères de contenu contient des mots    | condition : *ContentCharacterSetContainsWords* <br/> *ExceptIfContentCharacterSetContainsWords*    | CharacterSets    | Messages qui contiennent l'un des noms de jeux de caractères spécifiés.    |
| A remplacement de l’expéditeur    | condition : *HasSenderOverride* <br/> exception : *ExceptIfHasSenderOverride*    | s/o    | Messages dans lesquels l'expéditeur a choisi de remplacer une stratégie de protection contre la perte de données (DLP). Pour plus d’informations sur les stratégies DLP, voir [En savoir plus sur la protection contre la perte de données](./dlp-learn-about-dlp.md) |
| Correspondances de type de message    | condition : *MessageTypeMatches* <br/> exception : *ExceptIfMessageTypeMatches*    | MessageType    | Messages du type spécifié.    |
|La taille du message est supérieure ou égale à| condition : *MessageSizeOver* <br/> exception : *ExceptIfMessageSizeOver* |`Size`|Messages dans lesquels la taille totale (message plus pièces jointes) est supérieure ou égale à la valeur spécifiée. **Remarque**: Les limites de taille des messages dans les boîtes aux lettres sont évaluées avant les règles de flux de messagerie. Si un message est trop volumineux pour une boîte aux lettres, il est refusé avant qu'une règle avec cette condition puisse agir sur le message.|

## <a name="actions-for-dlp-policies"></a>Actions pour les stratégies DLP

Ce tableau décrit les actions disponibles dans DLP.


|**action dans DLP**|**paramètres d’action Microsoft 365 PowerShell**|**type de propriété**|**description**|
|---------|---------|---------|---------|
|Définir l’en-tête|SetHeader|Première propriété : *nom de l’en-tête* </br> Deuxième propriété : *valeur d’en-tête*|Le paramètre SetHeader spécifie une action pour la règle DLP qui ajoute ou modifie un champ d’en-tête et une valeur dans l’en-tête du message. Ce paramètre utilise la syntaxe « HeaderName:HeaderValue ». Vous pouvez spécifier plusieurs paires nom/valeur d’en-tête séparées par des virgules|
|Supprimer l’en-tête| RemoveHeader| Première propriété : *MessageHeaderField*</br> Deuxième propriété : *String*|  Le paramètre RemoveHeader spécifie une action pour la règle DLP qui supprime un champ d’en-tête de l’en-tête du message. Ce paramètre utilise la syntaxe « HeaderName » ou « HeaderName:HeaderValue ». Vous pouvez spécifier plusieurs noms d’en-tête ou paires nom/valeur d’en-tête séparés par des virgules|
|Rediriger le message vers des utilisateurs spécifiques|*RedirectMessageTo*|Adresses| Redirige le message vers les destinataires spécifiés. Le message n'est pas remis aux destinataires d'origine et aucune notification n'est envoyée à l'expéditeur ou aux destinataires d'origine.|
|Transmettre le message pour approbation au responsable de l’expéditeur| Modéré|Première propriété : *ModerateMessageByManager*</br> Deuxième propriété : *Boolean*|Le paramètre Moderate spécifie une action pour la règle DLP qui envoie le message électronique à un modérateur. Ce paramètre utilise la syntaxe : @{ModerateMessageByManager = <$true \| $false>;|
|Transmettre le message pour approbation à des approuveurs spécifiques| Modéré|Première propriété : *ModerateMessageByUser*</br>Deuxième propriété : *Addresses*|Le paramètre Moderate spécifie une action pour la règle DLP qui envoie le message électronique à un modérateur. Ce paramètre utilise la syntaxe : @{ ModerateMessageByUser = @(« emailaddress1 »,"emailaddress2 »,..."emailaddressN »)}|
|Ajouter un destinataire|AddRecipients|Première propriété : *Field*</br>Deuxième propriété : *Addresses*| Ajoute un ou plusieurs destinataires au champ À/Cc/Cci du message. Ce paramètre utilise la syntaxe : @{<AddToRecipients \| CopyTo \| BlindCopyTo> = « emailaddress"}|
|Ajouter le responsable de l’expéditeur en tant que destinataire|AddRecipients | Première propriété : *AddedManagerAction*</br>Deuxième propriété : *Field* | Ajoute le responsable de l'expéditeur au message en tant que type de destinataire spécifié ( To, Cc, Bcc ) ou redirige vers le responsable de l'expéditeur sans notification à l'expéditeur ou au destinataire. Cette action fonctionne uniquement si l'attribut Manager de l'expéditeur est défini dans Active Directory. Ce paramètre utilise la syntaxe : @{AddManagerAsRecipientType = « <To \| Cc \| Bcc>"}|    
Prédépender l’objet    |PrependSubject    |String    |Ajoute le texte spécifié au début du champ Subject du message. Envisagez d'utiliser un espace ou un signe deux-points (:) comme dernier caractère du texte spécifié pour le différencier du texte de l'objet d'origine.  </br>Pour empêcher l’ajout de la même chaîne aux messages qui contiennent déjà le texte dans l’objet (par exemple, les réponses), ajoutez l’exception « L’objet contient des mots » (ExceptIfSubjectContainsWords) à la règle.    
|Appliquer une clause d’exclusion de responsabilité HTML    |ApplyHtmlDisclaimer    |Première propriété : *Text*</br>Deuxième propriété : *Location*</br>Troisième propriété : *action de retour*    |Applique la clause d’exclusion de responsabilité HTML spécifiée à l’emplacement requis du message.</br>Ce paramètre utilise la syntaxe : @{ Text = " ; Location = <Append \| Prepend>; FallbackAction = <Wrap \| Ignore \| Reject> }
|Supprimer la chiffrement de messages Office 365 et la protection des droits    | RemoveRMSTemplate | s/o| Supprime le chiffrement Office 365 appliqué à un e-mail|
