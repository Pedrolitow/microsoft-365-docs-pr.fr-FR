---
title: Conserver les destinataires Cci et les destinataires de groupe de distribution étendu pour la découverte électronique
description: In-Place stratégies de conservation, de conservation pour litige et de rétention Microsoft 365 vous permettent de conserver le contenu de la boîte aux lettres pour répondre aux exigences de conformité réglementaire et d’eDiscovery.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 6/19/2017
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- ediscovery
ms.openlocfilehash: c68058974afb19778aa5674ae1217b6163ea0504
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68687986"
---
# <a name="preserve-bcc-and-expanded-distribution-group-recipients-for-ediscovery"></a>Conserver les destinataires Cci et les destinataires de groupe de distribution étendu pour la découverte électronique
  
Les conservations pour litige, les conservations eDiscovery et les [stratégies de rétention Microsoft 365](./retention.md) créées dans le portail de conformité Microsoft Purview vous permettent de conserver le contenu de la boîte aux lettres pour répondre aux exigences de conformité réglementaire et d’eDiscovery. Les informations sur les destinataires directement adressés dans les champs À et Cc d’un message sont incluses dans tous les messages par défaut. Toutefois, votre organisation peut avoir besoin de la possibilité de rechercher et de reproduire des détails sur tous les destinataires d’un message. Cela inclut les opérations suivantes :
  
- **Destinataires adressés à l’aide du champ Cci d’un message :** Les destinataires cci sont stockés dans le message dans la boîte aux lettres de l’expéditeur, mais ne sont pas inclus dans les en-têtes du message remis aux destinataires.
- **Destinataires du groupe de distribution étendu :** Destinataires qui reçoivent le message parce qu’ils sont membres d’un groupe de distribution auquel le message a été adressé, soit dans les champs À, Cc ou Cci.

Exchange Online et Exchange Server 2013 (mise à jour cumulative 7 et versions ultérieures) conservent des informations sur les destinataires cci et les groupes de distribution étendus. Vous pouvez rechercher ces informations à l’aide d’un outil eDiscovery dans le portail de conformité.
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-bcc-recipients-and-expanded-distribution-group-recipients-are-preserved"></a>Conservation des destinataires en copie carbone invisible et des destinataires de groupe de distribution étendu

Les informations sur les destinataires cci sont stockées avec le message dans la boîte aux lettres de l’expéditeur. Ces informations sont indexées et disponibles pour les recherches et les conservations eDiscovery.

Les informations sur les destinataires de groupe de distribution étendu sont stockées avec le message après vous avez placé une boîte aux lettres en conservation inaltérable ou en conservation pour litige. Dans Microsoft 365, ces informations sont également stockées lorsqu’une stratégie de rétention Microsoft Purview est appliquée à une boîte aux lettres. L'appartenance au groupe de distribution est déterminée au moment où le message est envoyé. La liste de destinataires développée stockée avec le message n’est pas affectée par les modifications apportées à l’appartenance au groupe après l’envoi du message.

|Informations sur...|Est stocké dans...|Stockage par défaut ?|Est accessible à...|
|:-------------------|:--------------|:--------------------|:------------------|
|À : et Cc : destinataires|Propriétés de message dans les boîtes aux lettres de l'expéditeur et des destinataires|Oui|Expéditeur, destinataires et responsables de la mise en conformité|
|Cci : destinataires|Propriété de message dans la boîte aux lettres de l'expéditeur|Oui|Expéditeurs et responsables de la mise en conformité|
|Destinataires de groupe de distribution étendu|Propriétés de message dans la boîte aux lettres de l'expéditeur|Non. Les informations de destinataire du groupe de distribution étendu sont stockées après qu’une boîte aux lettres a été placée en conservation In-Place ou en attente pour litige, ou affectée à une stratégie de rétention Microsoft Purview.|Agents chargés de la conformité|

## <a name="searching-for-messages-sent-to-bcc-and-expanded-distribution-group-recipients"></a>Recherche de messages envoyés aux destinataires en copie carbone invisible et aux destinataires de groupe de distribution étendu

When searching for messages sent to a recipient, eDiscovery search results now include messages sent to a distribution group that the recipient is a member of. The following table shows the scenarios where messages sent to Bcc and expanded distribution group recipients are returned in eDiscovery searches.

**Scénario 1** : John est membre du groupe de distribution US-Sales. Ce tableau présente les résultats de la recherche de découverte électronique lorsque Bob envoie un message à John directement ou indirectement via un groupe de distribution.

|Lorsque vous recherchez des messages envoyés dans la boîte aux lettres de Bob...|Et le message est envoyé avec...|Les résultats incluent le message...|
|---|---|---|
|À : John|John on To:|Oui|
|À : John|US-Sales sur À :|Oui|
|À : US-Sales|US-Sales sur À :|Oui|
|Cc: John|John on Cc:|Oui|
|Cc: John|US-Sales sur Cc :|Oui|
|Cc : US-Sales|US-Sales sur Cc :|Oui|

**Scénario 2** : Bob envoie un e-mail à John (To/Cc) et Jack (Cci directement ou indirectement via un groupe de distribution). Le tableau ci-dessous montre les résultats de la recherche de découverte électronique.

|Lorsque vous effectuez une recherche...|Pour les messages envoyés...|Les résultats incluent le message...|Remarques|
|---|---|---|---|
|Boîte aux lettres de Bob|To:/Cc: John|Oui|Indique que Jack était inclus dans le champ Cci|
|Boîte aux lettres de Bob|Cci: Jack|Oui|Indique que Jack était inclus dans le champ Cci|
|Boîte aux lettres de Bob|Cci : Jack (via le groupe de distribution)|Oui|La liste des membres du groupe de distribution Cci, développée lors de l’envoi du message, est visible dans la préversion, l’exportation et les journaux de recherche eDiscovery.|
|Boîte aux lettres de John|To:/Cc: John|Oui|Aucune indication des destinataires en copie carbone invisible.|
|Boîte aux lettres de John|Cci : Jack (directement ou via le groupe de distribution)|Non|Cci : les informations ne sont pas stockées dans le message remis aux destinataires. Vous devez les rechercher dans la boîte aux lettres de l'expéditeur.|
|Boîte aux lettres de Jack|To:/Cc : John (directement ou via le groupe de distribution)|Oui|To:/Cc : les informations sont incluses dans le message remis à tous les destinataires.|
|Boîte aux lettres de Jack|Cci : Jack (directement ou via le groupe de distribution)|Non|Cci : les informations ne sont pas stockées dans le message remis aux destinataires. Vous devez les rechercher dans la boîte aux lettres de l'expéditeur.|

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

**Quand et où les informations de destinataire cci sont-elles stockées ?**

Les informations relatives au destinataire en Cci sont conservées par défaut dans le message d'origine, dans la boîte aux lettres de l'expéditeur. Si le destinataire Cci est un groupe de distribution, l’appartenance au groupe de distribution est développée uniquement si la boîte aux lettres de l’expéditeur est en attente ou affectée à une stratégie de rétention Microsoft 365.

**Quand et où la liste des destinataires du groupe de distribution développé est-elle stockée ?**

L'appartenance au groupe est étendue au moment de l'envoi du message. La liste des membres de groupe de distribution étendu est stockée dans le message d'origine, dans la boîte aux lettres de l'expéditeur. La boîte aux lettres de l’expéditeur doit être en attente In-Place, en attente pour litige ou affectée à une stratégie de rétention Microsoft 365.

**Les destinataires To/Cc peuvent-ils voir quels destinataires ont été cci’ed ?**

Non. Ces informations ne sont pas incluses dans les en-têtes de message et ne sont pas visibles par les destinataires To/Cc. L'expéditeur peut voir le champ Cci stocké dans le message original de sa boîte aux lettres. Les responsables de la mise en conformité peuvent voir ces informations lors d'une recherche dans la boîte aux lettres de l'expéditeur.

**Comment puis-je m’assurer que les destinataires du groupe de distribution étendu sont toujours conservés ?**

Pour vous assurer que les membres du groupe de distribution étendu sont toujours conservés avec un message, [placez toutes les boîtes aux lettres en attente](/Exchange/policy-and-compliance/holds/place-all-mailboxes-on-hold) ou créez une stratégie de rétention Microsoft 365 à l’échelle de l’organisation.

**Quels sont les types de groupes pris en charge ?**

Les groupes de distribution, les groupes de sécurité à extension messagerie et les groupes de distribution dynamique sont pris en charge.

**Existe-t-il une limite au nombre de destinataires du groupe de distribution qui sont développés et stockés dans le message ?**

Jusqu'à 10 000 membres d'un groupe de distribution sont conservés.

**Les groupes de distribution imbriqués sont-ils pris en charge ?**

Oui, 25 niveaux de groupes de distribution imbriqués sont étendus.

**Où les informations de destinataire cci et groupe de distribution étendu sont-elles visibles ?**

Ces informations sont visibles pour les responsables de la mise en conformité lors d'une recherche de découverte électronique. Les destinataires en Cci et les destinataires de groupe de distribution étendu sont inclus dans les résultats de recherche copiés vers une boîte aux lettres de découverte ou exportés vers un fichier PST et dans le journal de découverte électronique inclus dans les résultats de la recherche. Les informations relatives aux destinataires en copie carbone invisible sont également disponibles dans l'aperçu de la recherche.

**Que se passe-t-il si un membre d’un groupe de distribution est masqué dans la liste d’adresses globale de l’organisation ?**

Il n'y a aucune conséquence. Même si des destinataires sont masqués dans la LAG, ils restent inclus dans la liste des destinataires pour le groupe de distribution étendu.
