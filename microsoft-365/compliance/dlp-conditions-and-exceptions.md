---
title: Conditions et exceptions de la stratégie DLP (aperçu)
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
ms.openlocfilehash: 2ce49b15bdb13035a37f6895b4b8865b55a62f78
ms.sourcegitcommit: e56894917d2aae05705c3b9447388d10e2156183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48841470"
---
# <a name="dlp-policy-conditions-and-exceptions-preview"></a>Conditions et exceptions de la stratégie DLP (aperçu)

Les conditions et les exceptions dans les stratégies DLP identifient les éléments sensibles auxquels la stratégie est appliquée. Les conditions définissent les éléments à inclure et les exceptions définissent les éléments à exclure. Pour chaque condition, il existe une exception correspondante qui utilise la même syntaxe.

 La plupart des conditions et des exceptions ont une propriété qui prend en charge une ou plusieurs valeurs. Par exemple, si la stratégie DLP est appliquée à des courriers électroniques Exchange, la condition **sender** is requiert l’expéditeur du message. Certaines conditions ont deux propriétés. Par exemple, la condition **Un en-tête de message inclut n'importe lequel de ces mots** requiert une propriété pour spécifier le champ d'en-tête du message et une deuxième pour spécifier le texte à rechercher dans le champ d'en-tête. Certaines conditions ou exceptions n’ont aucune propriété. Par exemple, la **pièce jointe est** une condition de protection par mot de passe qui recherche simplement les pièces jointes dans les messages protégés par mot de passe.

## <a name="conditions-and-exceptions-for-dlp-policies"></a>Conditions et exceptions pour les stratégies DLP

Les tableaux présentés dans les sections suivantes décrivent les conditions et les exceptions disponibles dans DLP.

- [Expéditeurs](#senders)
- [Destinataires](#recipients)
- [Objet ou corps du message](#message-subject-or-body)
- [Pièces jointes](#attachments)
- [En-têtes de message](#message-headers)
- [Propriétés de message](#message-properties)

## <a name="senders"></a>Expéditeurs


|**condition ou exception dans DLP**  |**paramètres de condition/d’exception dans Microsoft 365 PowerShell** |**type de propriété**  |**description**|
|---------|---------|---------|---------|
|L’expéditeur est |condition : *from* <br/> exception : *ExceptIfFrom*      |Adresses |     Messages envoyés par les groupes de boîtes aux lettres, les utilisateurs de messagerie, les contacts de messagerie ou les groupes Microsoft 365 de l’organisation.|
|L’adresse IP de l’expéditeur est     |condition : *SenderIPRanges*<br/> exception : *ExceptIfSenderIPRanges*         |  IPAddressRanges       | Messages dans lesquels l'adresse IP de l'expéditeur correspond à l'adresse IP spécifiée ou figure dans la plage d'adresses IP spécifiée.       |
|L’adresse de l’expéditeur contient des mots   | condition : *FromAddressContainsWords* <br/> exception : *ExceptIfFromAddressContainsWords*        |   Mots      |   Messages contenant les mots spécifiés dans l'adresse de l'expéditeur.|
| L’adresse de l’expéditeur correspond à des modèles    | condition : *FromAddressMatchesPatterns* <br/> exception : *ExceptFromAddressMatchesPatterns*       |      Modèles   |  Messages dans lesquels l'adresse de messagerie de l'expéditeur contient des modèles de texte qui correspondent aux expressions régulières spécifiées.  |
|Le domaine de l’expéditeur est  |  condition : *SenderDomainIs* <br/> exception : *ExceptIfSenderDomainIs*       |DomainName         |     Messages dans lesquels le domaine de l'adresse de messagerie de l'expéditeur correspond à la valeur spécifiée. Si vous avez besoin de trouver des domaines d’expéditeur qui *contiennent* le domaine spécifié (par exemple, n’importe quel sous-domaine d’un domaine), utilisez la condition *FromAddressMatchesPatterns* ( **sender Address matches** ) et spécifiez le domaine à l’aide de la syntaxe : « \. Domain \. com $ ».    |

## <a name="recipients"></a>Destinataires

|**condition ou exception dans DLP**| **paramètres de condition/d’exception dans Microsoft 365 PowerShell** |    **type de propriété** | **description**|
|---------|---------|---------|---------|
|Le destinataire est|  condition : *SentTo* <br/> exception : *ExceptIfSentTo* | Adresses | Messages dans lesquels l’un des destinataires est la boîte aux lettres, l’utilisateur de messagerie ou le contact de messagerie spécifié dans l’organisation. Les destinataires peuvent figurer dans les champs **à** , **CC** ou **CCI** du message.|
|Le domaine du destinataire est|   condition : *RecipientDomainIs* <br/> exception : *ExceptIfRecipientDomainIs* |   DomainName |    Messages dans lesquels le domaine de l'adresse de messagerie de l'expéditeur correspond à la valeur spécifiée.|
|L’adresse du destinataire contient des mots|  condition : *RecipientAddressContainsWords* <br/> exception : *ExceptIfRecipientAddressContainsWords*|    Mots|  Messages contenant les mots spécifiés dans l'adresse du destinataire. <br/>**Remarque**  : cette condition ne tient pas compte des messages qui sont envoyés aux adresses proxy du destinataire. Elle correspond uniquement aux messages qui sont envoyés à l’adresse de messagerie principale du destinataire.|
|L’adresse du destinataire correspond aux modèles| condition : *RecipientAddressMatchesPatterns* <br/> exception : *ExceptIfRecipientAddressMatchesPatterns*|   Modèles    |Messages dans lesquels l'adresse de messagerie du destinataire contient des modèles de texte qui correspondent aux expressions régulières spécifiées. <br/> **Remarque**  : cette condition ne tient pas compte des messages qui sont envoyés aux adresses proxy du destinataire. Elle correspond uniquement aux messages qui sont envoyés à l’adresse de messagerie principale du destinataire.|
|Envoyé au membre du| condition : *SentToMemberOf* <br/> exception : *ExceptIfSentToMemberOf*|  Adresses|  Messages contenant des destinataires qui sont membres du groupe de distribution spécifié, d’un groupe de sécurité à extension messagerie ou d’un groupe Microsoft 365. Le groupe peut se trouver dans les champs **To** , **Cc** ou **Bcc** du message.|

## <a name="message-subject-or-body"></a>Objet ou corps du message

|**condition ou exception dans DLP** | **paramètres de condition/d’exception dans Microsoft 365 PowerShell** |**type de propriété**| **description**|
|---------|---------|---------|---------|
|L’objet contient des mots ou des expressions| condition : *SubjectContainsWords* <br/> exception : *ExceptIf SubjectContainsWords*| Mots   |Messages dans lesquels le champ Subject contient les mots spécifiés.|
|L’objet correspond à des modèles|condition : *SubjectMatchesPatterns* <br/> exception : *ExceptIf SubjectMatchesPatterns*|Modèles   |Messages dans lesquels le champ Subject contient des modèles de texte qui correspondent aux expressions régulières spécifiées.|
|Le contenu contient|  condition : *ContentContainsSensitiveInformation* <br/> exception *ExceptIfContentContainsSensitiveInformation*| SensitiveInformationTypes|  Messages ou documents qui contiennent des informations sensibles, comme défini par les stratégies de protection contre la perte de données (DLP).|


## <a name="attachments"></a>Attachments

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

## <a name="message-headers"></a>En-têtes de message

|**condition ou exception dans DLP**| **paramètres de condition/d’exception dans Microsoft 365 PowerShell**| **type de propriété**|  **description**|
|---------|---------|---------|---------|
|L’en-tête contient des mots ou des expressions|condition : *HeaderContainsWords* <br/> exception : *ExceptIfHeaderContainsWords*|  Table de hachage  |Les messages qui contiennent le champ d’en-tête spécifié et la valeur de ce champ d’en-tête contient les mots spécifiés.|
|Les en-têtes correspondent à des modèles|   condition : *HeaderMatchesPatterns* <br/> exception : *ExceptIfHeaderMatchesPatterns*|    Table de hachage  |Les messages qui contiennent le champ d’en-tête spécifié et la valeur de ce champ d’en-tête contient les expressions régulières spécifiées.|

## <a name="message-properties"></a>Propriétés de message

|**condition ou exception dans DLP**| **paramètres de condition/d’exception dans Microsoft 365 PowerShell**| **type de propriété**   |**description**|
|---------|---------|---------|---------|
|Taille du message sur|condition : *MessageSizeOver* <br/> exception : *ExceptIfMessageSizeOver*| Size    |Messages dans lesquels la taille totale (message plus pièces jointes) est supérieure ou égale à la valeur spécifiée. <br/>**Remarque** : Les limites de taille des messages dans les boîtes aux lettres sont évaluées avant les règles de flux de messagerie. Si un message est trop volumineux pour une boîte aux lettres, il est refusé avant qu'une règle avec cette condition puisse agir sur le message.  |

