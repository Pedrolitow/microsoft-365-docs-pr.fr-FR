---
title: Conserver les destinataires Cci et les destinataires de groupe de distribution étendu pour la découverte électronique
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
ms.assetid: eb8ddf15-0080-457e-9d83-e73e193da334
description: In-Place stratégies de conservation, de conservation des litiges et de rétention Microsoft 365 vous permettent de conserver le contenu de la boîte aux lettres pour répondre aux exigences de conformité réglementaire et de découverte électronique.
ms.openlocfilehash: fae5fa009d78cdd05e35cda2aa196d66e3944439
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67825981"
---
# <a name="preserve-bcc-and-expanded-distribution-group-recipients-for-ediscovery"></a>Conserver les destinataires Cci et les destinataires de groupe de distribution étendu pour la découverte électronique
  
Les conservations de litige, les conservations eDiscovery et les [stratégies de rétention Microsoft 365 (créées](./retention.md) dans le portail de conformité Microsoft Purview) vous permettent de conserver le contenu de la boîte aux lettres pour répondre aux exigences de conformité réglementaire et eDiscovery. Les informations sur les destinataires directement adressés dans les champs À et Cc d’un message sont incluses dans tous les messages par défaut. Toutefois, votre organisation peut avoir besoin de la possibilité de rechercher et de reproduire des détails sur tous les destinataires d’un message. Cela inclut les opérations suivantes :
  
- **Destinataires traités à l’aide du champ CCI d’un message :** Les destinataires CCI sont stockés dans le message dans la boîte aux lettres de l’expéditeur, mais ils ne sont pas inclus dans les en-têtes du message remis aux destinataires. 
    
- **Destinataires de groupes de distribution développés :** Destinataires qui reçoivent le message parce qu’ils sont membres d’un groupe de distribution auquel le message a été adressé, soit dans les champs À, Cc ou Cci. 
    
Exchange Online et Exchange Server 2013 (mise à jour cumulative 7 et versions ultérieures) conservent des informations sur Cci et les destinataires de groupes de distribution étendus. Vous pouvez rechercher ces informations à l’aide d’un outil eDiscovery dans le portail de conformité.
  
## <a name="how-bcc-recipients-and-expanded-distribution-group-recipients-are-preserved"></a>Conservation des destinataires en copie carbone invisible et des destinataires de groupe de distribution étendu

Comme indiqué précédemment, les informations sur les destinataires en copie carbone invisible sont stockées avec le message dans la boîte aux lettres de l'expéditeur. Ces informations sont indexées et disponibles pour les recherches et conservations eDiscovery.

Les informations sur les destinataires de groupe de distribution étendu sont stockées avec le message après vous avez placé une boîte aux lettres en conservation inaltérable ou en conservation pour litige. Dans Office 365, ces informations sont également stockées lorsqu’une stratégie de rétention Microsoft 365 est appliquée à une boîte aux lettres. L'appartenance au groupe de distribution est déterminée au moment où le message est envoyé. La liste des destinataires étendue stockée avec le message n'est pas concernée par les modifications d'appartenance au groupe une fois que le message est envoyé.

|Informations sur...|Est stocké dans...|Stockage par défaut ?|Est accessible à...|
|---|---|---|---|
|Destinataires À et Cc|Propriétés de message dans les boîtes aux lettres de l'expéditeur et des destinataires|Oui|Expéditeur, destinataires et responsables de la mise en conformité|
|Destinataires en copie carbone invisible|Propriété de message dans la boîte aux lettres de l'expéditeur|Oui|Expéditeurs et responsables de la mise en conformité|
|Destinataires de groupe de distribution étendu|Propriétés de message dans la boîte aux lettres de l'expéditeur|Non. Les informations de destinataire du groupe de distribution développées sont stockées après qu’une boîte aux lettres a été placée sur In-Place conservation ou conservation des litiges, ou affectée à une stratégie de rétention Microsoft 365.|Responsables de la mise en conformité|

## <a name="searching-for-messages-sent-to-bcc-and-expanded-distribution-group-recipients"></a>Recherche de messages envoyés aux destinataires en copie carbone invisible et aux destinataires de groupe de distribution étendu

Lors de la recherche de messages envoyés à un destinataire, les résultats de découverte électronique incluent désormais les messages envoyés à un groupe de distribution dont le destinataire est membre. Le tableau suivant présente les scénarios où les messages envoyés à des destinataires en copie carbone invisible et à des destinataires de groupe de distribution étendu sont renvoyés dans les recherches de découverte électronique.

Scénario 1 : John est membre du groupe de distribution Ventes aux États-Unis. Ce tableau présente les résultats de la recherche de découverte électronique lorsque Bob envoie un message à John directement ou indirectement via un groupe de distribution.

|Lorsque vous recherchez des messages envoyés dans la boîte aux lettres de Bob...|Et le message est envoyé avec...|Les résultats incluent le message...|
|---|---|---|
|À:John|John dans le champ À|Oui|
|À:John|Ventes aux États-Unis dans le champ À|Oui|
|À:Ventes aux États-Unis|Ventes aux États-Unis dans le champ À|Oui|
|Cc:John|John dans le champ Cc|Oui|
|Cc:John|Ventes aux États-Unis dans le champ Cc|Oui|
|Cc:Ventes aux États-Unis|Ventes aux États-Unis dans le champ Cc|Oui|

Scénario 2 : Bob envoie un courrier électronique à John (À/Cc) et Jack (Cci, directement ou indirectement via un groupe de distribution). Le tableau ci-dessous montre les résultats de la recherche de découverte électronique.

|Lorsque vous effectuez une recherche...|Pour les messages envoyés...|Les résultats incluent le message...|Remarques|
|---|---|---|---|
|Boîte aux lettres de Bob|À/Cc:John|Oui|Indique que Jack était inclus dans le champ Cci|
|Boîte aux lettres de Bob|Cci:Jack|Oui|Indique que Jack était inclus dans le champ Cci|
|Boîte aux lettres de Bob|Cci:Jack (via un groupe de distribution)|Oui|La liste des membres du groupe de distribution Cci’ed, développée lors de l’envoi du message, est visible dans la préversion, l’exportation et les journaux de recherche eDiscovery.|
|Boîte aux lettres de John|À/Cc:John|Oui|Aucune indication des destinataires en copie carbone invisible.|
|Boîte aux lettres de John|Cci:Jack (directement ou via un groupe de distribution)|Non|Les informations du champ Cci ne sont pas stockées dans le message remis aux destinataires. Vous devez les rechercher dans la boîte aux lettres de l'expéditeur.|
|Boîte aux lettres de Jack|À/Cc:John (directement ou via un groupe de distribution)|Oui|Les informations des champs À/Cc sont incluses dans le message remis à tous les destinataires.|
|Boîte aux lettres de Jack|Cci:Jack (directement ou via un groupe de distribution)|Non|Les informations du champ Cci ne sont pas stockées dans le message remis aux destinataires. Vous devez les rechercher dans la boîte aux lettres de l'expéditeur.|

## <a name="frequently-asked-questions"></a>Foire aux questions

 **Q. Quand les informations sur le destinataire en Cci sont-elles stockées et à quel emplacement ?**

R. Les informations relatives au destinataire en Cci sont conservées par défaut dans le message d'origine, dans la boîte aux lettres de l'expéditeur. Si le destinataire CCI est un groupe de distribution, l’appartenance au groupe de distribution n’est développée que si la boîte aux lettres de l’expéditeur est en attente ou affectée à une stratégie de rétention Microsoft 365.

 **Q. Quand la liste des destinataires de groupe de distribution étendu est-elle stockée et à quel emplacement ?**

R. L'appartenance au groupe est étendue au moment de l'envoi du message. La liste des membres de groupe de distribution étendu est stockée dans le message d'origine, dans la boîte aux lettres de l'expéditeur. La boîte aux lettres de l’expéditeur doit être en attente In-Place, conservation du litige ou affectée à une stratégie de rétention Microsoft 365.

 **Q. Les destinataires indiqués dans les champs À et Cc peuvent-ils voir les destinataires indiqués dans le champ Cci ?**

R. Non. Ces informations ne sont pas incluses dans les en-têtes de message et ne sont pas visibles pour les destinataires indiqués dans les champs À et Cc. L'expéditeur peut voir le champ Cci stocké dans le message original de sa boîte aux lettres. Les responsables de la mise en conformité peuvent voir ces informations lors d'une recherche dans la boîte aux lettres de l'expéditeur.

 **Q. Comment puis-je m’assurer que les destinataires de groupes de distribution étendus sont toujours conservés ?**

A. Pour vous assurer que les membres du groupe de distribution développés sont toujours conservés avec un message, [mettez toutes les boîtes aux lettres en attente](/Exchange/policy-and-compliance/holds/place-all-mailboxes-on-hold) ou créez une stratégie de rétention Microsoft 365 à l’échelle de l’organisation.

 **Q. Quels types de groupe sont pris en charge ?**

R. Les groupes de distribution, les groupes de sécurité à extension messagerie et les groupes de distribution dynamique sont pris en charge.

 **Q. Y a-t-il une limite en ce qui concerne le nombre de destinataires de groupes de distribution étendus et stockés dans le message ?**

R. Jusqu'à 10 000 membres d'un groupe de distribution sont conservés.

 **Q. Les groupes de distribution imbriqués sont-ils pris en charge ?**

R. Oui, 25 niveaux de groupes de distribution imbriqués sont étendus.

 **Q. Où les informations du champ Cci et les informations relatives aux destinataires de groupe de distribution étendu sont-elles visibles ?**

R. Ces informations sont visibles pour les responsables de la mise en conformité lors d'une recherche de découverte électronique. Les destinataires en Cci et les destinataires de groupe de distribution étendu sont inclus dans les résultats de recherche copiés vers une boîte aux lettres de découverte ou exportés vers un fichier PST et dans le journal de découverte électronique inclus dans les résultats de la recherche. Les informations relatives aux destinataires en copie carbone invisible sont également disponibles dans l'aperçu de la recherche.

 **Q. Que se passe-t-il si un membre d'un groupe de distribution est masqué dans la liste d'adresses globale (LAG) de l'organisation ?**

R. Il n'y a aucune conséquence. Si les destinataires sont masqués de la gal, ils sont toujours inclus dans la liste des destinataires pour le groupe de distribution étendu.
