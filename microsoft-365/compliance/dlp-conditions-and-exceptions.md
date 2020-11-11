---
title: Conditions, exceptions et actions de la stratégie DLP (aperçu)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: en savoir plus sur les conditions et les exceptions de la stratégie DLP
ms.openlocfilehash: a371c564cc314c457e1d9afe667115c244e0185d
ms.sourcegitcommit: f941495e9257a0013b4a6a099b66c649e24ce8a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48993342"
---
# <a name="dlp-policy-conditions-exceptions-and-actions-preview"></a>Conditions, exceptions et actions de la stratégie DLP (aperçu)

Les conditions et les exceptions dans les stratégies DLP identifient les éléments sensibles auxquels la stratégie est appliquée. Les actions définissent ce qui se produit lorsqu’une condition d’exception est remplie.

- Les conditions définissent les éléments à inclure
- Les exceptions définissent les éléments à exclure.
- Les actions définissent ce qui se produit à la suite d’une condition ou d’une exception rencontrée.
 
La plupart des conditions et des exceptions ont une propriété qui prend en charge une ou plusieurs valeurs. Par exemple, si la stratégie DLP est appliquée à des courriers électroniques Exchange, la condition **sender** is requiert l’expéditeur du message. Certaines conditions ont deux propriétés. Par exemple, la condition **Un en-tête de message inclut n'importe lequel de ces mots** requiert une propriété pour spécifier le champ d'en-tête du message et une deuxième pour spécifier le texte à rechercher dans le champ d'en-tête. Certaines conditions ou exceptions n’ont aucune propriété. Par exemple, la **pièce jointe est** une condition de protection par mot de passe qui recherche simplement les pièces jointes dans les messages protégés par mot de passe.

Les actions nécessitent généralement des propriétés supplémentaires. Par exemple, lorsque la règle de stratégie DLP redirige un message, vous devez spécifier l’emplacement vers lequel le message est redirigé. 
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>Conditions et exceptions pour les stratégies DLP

Les tableaux présentés dans les sections suivantes décrivent les conditions et les exceptions disponibles dans DLP.

- [Expéditeurs](#senders)
- [Destinataires](#recipients)
- [Objet ou corps du message](#message-subject-or-body)
- [Pièces jointes](#attachments)
- [En-têtes de message](#message-headers)
- [Propriétés de message](#message-properties)

### <a name="senders"></a>Expéditeurs


|**condition ou exception dans DLP**  |**paramètres de condition/d’exception dans Microsoft 365 PowerShell** |**type de propriété**  |**description**|
|---------|---------|---------|---------|
|L’expéditeur est |condition : *from* <br/> exception : *ExceptIfFrom*      |Adresses |     Messages envoyés par les groupes de boîtes aux lettres, les utilisateurs de messagerie, les contacts de messagerie ou les groupes Microsoft 365 de l’organisation.|
|L’adresse IP de l’expéditeur est     |condition : *SenderIPRanges*<br/> exception : *ExceptIfSenderIPRanges*         |  IPAddressRanges       | Messages dans lesquels l'adresse IP de l'expéditeur correspond à l'adresse IP spécifiée ou figure dans la plage d'adresses IP spécifiée.       |
|L’adresse de l’expéditeur contient des mots   | condition : *FromAddressContainsWords* <br/> exception : *ExceptIfFromAddressContainsWords*        |   Mots      |   Messages contenant les mots spécifiés dans l'adresse de l'expéditeur.|
| L’adresse de l’expéditeur correspond à des modèles    | condition : *FromAddressMatchesPatterns* <br/> exception : *ExceptFromAddressMatchesPatterns*       |      Modèles   |  Messages dans lesquels l'adresse de messagerie de l'expéditeur contient des modèles de texte qui correspondent aux expressions régulières spécifiées.  |
|Le domaine de l’expéditeur est  |  condition : *SenderDomainIs* <br/> exception : *ExceptIfSenderDomainIs*       |DomainName         |     Messages dans lesquels le domaine de l'adresse de messagerie de l'expéditeur correspond à la valeur spécifiée. Si vous avez besoin de trouver des domaines d’expéditeur qui *contiennent* le domaine spécifié (par exemple, n’importe quel sous-domaine d’un domaine), utilisez la condition *FromAddressMatchesPatterns* ( **sender Address matches** ) et spécifiez le domaine à l’aide de la syntaxe : « \. Domain \. com $ ».    |

### <a name="recipients"></a>Destinataires

|**condition ou exception dans DLP**| **paramètres de condition/d’exception dans Microsoft 365 PowerShell** |    **type de propriété** | **description**|
|---------|---------|---------|---------|
|Le destinataire est|  condition : *SentTo* <br/> exception : *ExceptIfSentTo* | Adresses | Messages dans lesquels l’un des destinataires est la boîte aux lettres, l’utilisateur de messagerie ou le contact de messagerie spécifié dans l’organisation. Les destinataires peuvent figurer dans les champs **à** , **CC** ou **CCI** du message.|
|Le domaine du destinataire est|   condition : *RecipientDomainIs* <br/> exception : *ExceptIfRecipientDomainIs* |   DomainName |    Messages dans lesquels le domaine de l'adresse de messagerie de l'expéditeur correspond à la valeur spécifiée.|
|L’adresse du destinataire contient des mots|  condition : *RecipientAddressContainsWords* <br/> exception : *ExceptIfRecipientAddressContainsWords*|    Mots|  Messages contenant les mots spécifiés dans l'adresse du destinataire. <br/>**Remarque**  : cette condition ne tient pas compte des messages qui sont envoyés aux adresses proxy du destinataire. Elle correspond uniquement aux messages qui sont envoyés à l’adresse de messagerie principale du destinataire.|
|L’adresse du destinataire correspond aux modèles| condition : *RecipientAddressMatchesPatterns* <br/> exception : *ExceptIfRecipientAddressMatchesPatterns*|   Modèles    |Messages dans lesquels l'adresse de messagerie du destinataire contient des modèles de texte qui correspondent aux expressions régulières spécifiées. <br/> **Remarque**  : cette condition ne tient pas compte des messages qui sont envoyés aux adresses proxy du destinataire. Elle correspond uniquement aux messages qui sont envoyés à l’adresse de messagerie principale du destinataire.|
|Envoyé au membre du| condition : *SentToMemberOf* <br/> exception : *ExceptIfSentToMemberOf*|  Adresses|  Messages contenant des destinataires qui sont membres du groupe de distribution spécifié, d’un groupe de sécurité à extension messagerie ou d’un groupe Microsoft 365. Le groupe peut se trouver dans les champs **To** , **Cc** ou **Bcc** du message.|

### <a name="message-subject-or-body"></a>Objet ou corps du message

|**condition ou exception dans DLP** | **paramètres de condition/d’exception dans Microsoft 365 PowerShell** |**type de propriété**| **description**|
|---------|---------|---------|---------|
|L’objet contient des mots ou des expressions| condition : *SubjectContainsWords* <br/> exception : *ExceptIf SubjectContainsWords*| Mots   |Messages dans lesquels le champ Subject contient les mots spécifiés.|
|L’objet correspond à des modèles|condition : *SubjectMatchesPatterns* <br/> exception : *ExceptIf SubjectMatchesPatterns*|Modèles   |Messages dans lesquels le champ Subject contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|
|Le contenu contient|  condition : *ContentContainsSensitiveInformation* <br/> exception *ExceptIfContentContainsSensitiveInformation*| SensitiveInformationTypes|  Messages ou documents qui contiennent des informations sensibles, comme défini par les stratégies de protection contre la perte de données (DLP).|


### <a name="attachments"></a>Attachments

|**condition ou exception dans DLP**| **paramètres de condition/d’exception dans Microsoft 365 PowerShell**| **type de propriété**   |**description**|
|---------|---------|---------|---------|
|La pièce jointe est protégée par mot de passe|condition : *DocumentIsPasswordProtected* <br/> exception : *ExceptIfDocumentIsPasswordProtected*|none| Messages dans lesquels une pièce jointe est protégée par mot de passe (et ne peut donc pas être analysée). La détection de mot de passe fonctionne uniquement pour les documents Office et les fichiers .zip.|
|L’extension de fichier de la pièce jointe est|condition : *ContentExtensionMatchesWords* <br/> exception : *ExceptIfContentExtensionMatchesWords*|  Mots   |Messages dans lesquels l'extension de fichier de la pièce jointe correspond à l'un des mots spécifiés.|
|Le contenu d’une pièce jointe de courrier électronique n’a pas pu être analysé|condition : *DocumentIsUnsupported* <br/>exception : *ExceptIf DocumentIsUnsupported*|   s/o|    Messages dans lesquels une pièce jointe n’est pas reconnue en mode natif par Exchange Online.|
|Le contenu d’une pièce jointe de courrier électronique n’a pas terminé l’analyse|   condition : *ProcessingLimitExceeded* <br/> exception : *ExceptIfProcessingLimitExceeded*|    s/o |Messages pour lesquels le moteur de règles n'a pas pu terminer l'analyse des pièces jointes. Vous pouvez utiliser cette condition pour créer des règles qui fonctionnent conjointement pour identifier et traiter les messages dont le contenu n'a pas pu être entièrement analysé.|
|Le nom du document contient des mots|condition : *DocumentNameMatchesWords* <br/> exception : *ExceptIfDocumentNameMatchesWords* |Mots  |Messages dans lesquels le nom de fichier d’une pièce jointe correspond à l’un des mots spécifiés.|
|Le nom du document correspond aux modèles|condition : *DocumentNameMatchesPatterns* <br/> exception : *ExceptIfDocumentNameMatchesPatterns*|    Modèles    |Messages dans lesquels le nom de fichier d'une pièce jointe contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|
|La propriété du document est|condition : *ContentPropertyContainsWords* <br/> exception : *ExceptIfContentPropertyContainsWords* |Mots| Messages ou documents dans lesquels l’extension de fichier d’une pièce jointe correspond à l’un des mots spécifiés.|
|La taille du document est supérieure ou égale à| condition : *DocumentSizeOver* <br/> exception : *ExceptIfDocumentSizeOver*|    Size    |Messages dans lesquels toutes les pièces jointes sont supérieures ou égales à la valeur spécifiée.|

### <a name="message-headers"></a>En-têtes de message

|**condition ou exception dans DLP**| **paramètres de condition/d’exception dans Microsoft 365 PowerShell**| **type de propriété**|  **description**|
|---------|---------|---------|---------|
|L’en-tête contient des mots ou des expressions|condition : *HeaderContainsWords* <br/> exception : *ExceptIfHeaderContainsWords*|  Table de hachage  |Les messages qui contiennent le champ d’en-tête spécifié et la valeur de ce champ d’en-tête contient les mots spécifiés.|
|Les en-têtes correspondent à des modèles|   condition : *HeaderMatchesPatterns* <br/> exception : *ExceptIfHeaderMatchesPatterns*|    Table de hachage  |Les messages qui contiennent le champ d’en-tête spécifié et la valeur de ce champ d’en-tête contient les expressions régulières spécifiées.|

### <a name="message-properties"></a>Propriétés de message

|**condition ou exception dans DLP**| **paramètres de condition/d’exception dans Microsoft 365 PowerShell**| **type de propriété**   |**description**|
|---------|---------|---------|---------|
|Taille du message sur|condition : *MessageSizeOver* <br/> exception : *ExceptIfMessageSizeOver*| Size    |Messages dans lesquels la taille totale (message plus pièces jointes) est supérieure ou égale à la valeur spécifiée. <br/>**Remarque** : Les limites de taille des messages dans les boîtes aux lettres sont évaluées avant les règles de flux de messagerie. Si un message est trop volumineux pour une boîte aux lettres, il est refusé avant qu'une règle avec cette condition puisse agir sur le message.  |

## <a name="actions-for-dlp-policies"></a>Actions pour les stratégies DLP

Ce tableau décrit les actions de règle de flux de messagerie Exchange Online disponibles dans DLP.


|**action dans DLP**|**paramètres d’action dans Microsoft 365 PowerShell**|**type de propriété**|**description**|
|---------|---------|---------|---------|
|En-tête Set|SetHeader|First, propriété : nom de l' *en-tête* </br> Deuxième propriété : *valeur d’en-tête*|Le paramètre SetHeader spécifie une action pour la règle DLP qui ajoute ou modifie un champ d’en-tête et une valeur dans l’en-tête du message. Ce paramètre utilise la syntaxe « HeaderName : HeaderValue ». Vous pouvez spécifier plusieurs paires nom/valeur d’en-tête séparées par des virgules|
|Supprimer l’en-tête| RemoveHeader| Première propriété : *MessageHeaderField*</br> Deuxième propriété : *String*|  Le paramètre RemoveHeader spécifie une action pour la règle DLP qui supprime un champ d’en-tête de l’en-tête du message. Ce paramètre utilise la syntaxe « HeaderName » ou « HeaderName : HeaderValue ». Vous pouvez spécifier plusieurs noms d’en-tête ou d’en-tête et paires de valeurs séparées par des virgules|
|Rediriger le message vers des utilisateurs spécifiques|*RedirectMessageTo*|Adresses| Redirige le message vers les destinataires spécifiés. Le message n'est pas remis aux destinataires d'origine et aucune notification n'est envoyée à l'expéditeur ou aux destinataires d'origine.|
|Transférer le message pour approbation au responsable de l’expéditeur| Modéré|Première propriété : *ModerateMessageByManager*</br> Deuxième propriété : *Boolean*|Le paramètre modéré spécifie une action pour la règle DLP qui envoie le message électronique à un modérateur. Ce paramètre utilise la syntaxe suivante : @ {ModerateMessageByManager = <$true \| $false> ;|
|Transférer le message pour approbation à des approbateurs spécifiques| Modéré|Première propriété : *ModerateMessageByUser*</br>Deuxième propriété : *Addresses*|Le paramètre modéré spécifie une action pour la règle DLP qui envoie le message électronique à un modérateur. Ce paramètre utilise la syntaxe suivante : @ {ModerateMessageByUser = @ ("EmailAddress1", "EmailAddress2",... "emailaddressN")}|
|Ajouter un destinataire|AddRecipients|Première propriété : *Field*</br>Deuxième propriété : *Addresses*| Ajoute un ou plusieurs destinataires dans le champ à/CC/CCI du message. Ce paramètre utilise la syntaxe suivante : @ {<AddToRecipients \| CopyTo \|> BlindCopyTo = "EmailAddress"}|
|Ajouter le gestionnaire de l’expéditeur en tant que destinataire|AddRecipients | Première propriété : *AddedManagerAction*</br>Deuxième propriété : *Field* | Ajoute le responsable de l'expéditeur au message en tant que type de destinataire spécifié ( To, Cc, Bcc ) ou redirige vers le responsable de l'expéditeur sans notification à l'expéditeur ou au destinataire. Cette action fonctionne uniquement si l'attribut Manager de l'expéditeur est défini dans Active Directory. Ce paramètre utilise la syntaxe suivante : @ {AddManagerAsRecipientType = "<à \| cc \| CCI>"}|

