---
title: Paramètres ASF dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: b286f853-b484-4af0-b01f-281fffd85e7a
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les paramètres de filtrage avancé du courrier indésirable (ASF) disponibles dans les stratégies anti-courrier indésirable dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5ade36086d1503b89b506730b98ac7965845e86b
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065641"
---
# <a name="advanced-spam-filter-asf-settings-in-eop"></a>Paramètres de filtrage avancé du courrier indésirable (ASF) dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Les paramètres ASF actuellement disponibles dans les stratégies anti-courrier indésirable sont en train d’être supprimés. Nous vous recommandons de ne pas utiliser ces paramètres dans les stratégies anti-courrier indésirable. La fonctionnalité de ces paramètres ASF est incorporée à d’autres parties de la pile de filtrage. Pour plus d’informations, consultez les paramètres de stratégie [anti-courrier indésirable EOP.](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

Dans toutes les organisations Microsoft 365, les paramètres de filtrage avancé du courrier indésirable (ASF) dans les stratégies anti-courrier indésirable dans EOP permettent aux administrateurs de marquer des messages comme courrier indésirable en fonction de propriétés de message spécifiques. ASF cible spécifiquement ces propriétés, car elles sont couramment trouvées dans le courrier indésirable. Selon la propriété, les détections ASF  marqueront le message comme courrier indésirable ou courrier **indésirable à niveau de confiance élevé.**

> [!NOTE]
> L’activation d’un ou de plusieurs paramètres ASF est une approche agressive du filtrage du courrier indésirable. Vous ne pouvez pas signaler les messages filtrés par ASF comme faux positifs. Vous pouvez identifier les messages qui ont été filtrés par ASF par :
>
> - Notifications périodiques de mise en quarantaine du courrier indésirable pour l’utilisateur final.
>
> - La présence de messages filtrés en quarantaine.
>
> - Champs `X-CustomSpam:` d’en-tête X spécifiques ajoutés aux messages comme décrit dans cet article.

Les sections suivantes décrivent les paramètres et options ASF disponibles dans les stratégies anti-courrier indésirable dans le Centre de sécurité & conformité, et dans Exchange Online PowerShell ou EOP PowerShell autonome ([New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy) et [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy)). Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

## <a name="enable-disable-or-test-asf-settings"></a>Activer, désactiver ou tester les paramètres ASF

Pour chaque paramètre ASF, les options suivantes sont disponibles dans les stratégies anti-courrier indésirable :

- **On**: ASF ajoute le champ d’en-tête X correspondant  au message et marque le message comme courrier indésirable (SCL 5 ou 6 pour augmenter les [paramètres](#increase-spam-score-settings)de score de courrier indésirable) ou comme courrier indésirable à niveau de confiance **élevé** (SCL 9 pour Marquer comme paramètres de courrier [indésirable).](#mark-as-spam-settings)

- **Désactivé**: le paramètre ASF est désactivé. Il s’agit de la valeur par défaut et nous vous recommandons de ne pas la modifier.

- **Test**: ASF ajoute le champ d’en-tête X correspondant au message. Ce qui arrive au message est déterminé par la valeur **des options du mode Test** (*TestModeAction*) :

  - **Aucun**: la remise des messages n’est pas affectée par la détection ASF. Le message est toujours soumis à d’autres types de filtrage et de règles dans EOP.

  - **Ajouter le texte d’en-tête X par défaut (*AddXHeader*)**: la valeur d’en-tête X `X-CustomSpam: This message was filtered by the custom spam filter option` est ajoutée au message. Vous pouvez utiliser cette valeur dans les règles de boîte de réception ou les règles de flux de messagerie (également appelées règles de transport) pour affecter la remise du message.

  - **Envoyer un message Cci (*BccMessage*)**: les adresses de messagerie spécifiées (la valeur du paramètre *TestModeBccToRecipients* dans PowerShell) sont ajoutées au champ Cci du message et le message est remis aux destinataires Cci supplémentaires. Dans le Centre de sécurité & conformité, vous séparez plusieurs adresses de messagerie par des points-virgules (;). Dans PowerShell, vous séparez plusieurs adresses de messagerie par des virgules.

  **Remarques** :

  - Le mode test n’est pas disponible pour les paramètres ASF suivants :

    - **Filtrage conditionnel de l’ID de** l’expéditeur : échec en dur (*MarkAsSpamFromAddressAuthFail*)
    - **NDR backscatter**(*MarkAsSpamNdrBackscatter*)
    - **Enregistrement SPF : échec en dur** (*MarkAsSpamSpfRecordHardFail*)

  - La même action en mode test est appliquée à *tous les* paramètres ASF qui sont définies sur **Test**. Vous ne pouvez pas configurer différentes actions de mode test pour différents paramètres ASF.

## <a name="increase-spam-score-settings"></a>Augmenter les paramètres du score de courrier indésirable

Les paramètres ASF suivants définissent le niveau de confiance du courrier indésirable (SCL) des messages détectés sur 5 ou 6, ce qui correspond au verdict du filtre anti-courrier indésirable et à l’action correspondante dans les stratégies anti-courrier indésirable. 

****

|Paramètre de stratégie anti-courrier indésirable|Description|En-tête X ajouté|
|---|---|---|
|**Liens d'image vers des sites distants** <p> *IncreaseScoreWithImageLinks*|Les messages qui contiennent des liens de balise HTML vers des sites distants (par exemple, à l’aide de http) sont `<Img>` marqués comme courrier indésirable.|`X-CustomSpam: Image links to remote sites`|
|**Redirection de l'URL vers un autre port** <p> *IncreaseScoreWithRedirectToOtherPort*|Les messages qui contiennent des liens hypertexte qui redirigent vers des ports TCP autres que 80 (HTTP), 8080 (http de remplacement) ou 443 (HTTPS) sont marqués comme courrier indésirable.|`X-CustomSpam: URL redirect to other port`|
|**Adresse IP numérique dans l'URL** <p> *IncreaseScoreWithNumericIps*|Les messages qui contiennent des URL numériques (généralement, des adresses IP) sont marqués comme courrier indésirable.|`X-CustomSpam: Numeric IP in URL`|
|**URL vers les sites web .biz ou .info** <p> *IncreaseScoreWithBizOrInfoUrls*|Les messages qui `.biz` contiennent `.info` ou des liens dans le corps du message sont marqués comme courrier indésirable.|`X-CustomSpam: URL to .biz or .info websites`|
|

## <a name="mark-as-spam-settings"></a>Marquer comme paramètres de courrier indésirable

Les paramètres ASF suivants définissent le SCL des messages  détectés sur 9, ce qui correspond au verdict de filtrage du courrier indésirable à niveau de confiance élevé et à l’action correspondante dans les stratégies anti-courrier indésirable.

****

|Paramètre de stratégie anti-courrier indésirable|Description|En-tête X ajouté|
|---|---|---|
|**Messages vides** <p> *MarkAsSpamEmptyMessages*|Les messages sans objet, aucun contenu dans le corps du message et aucune pièce jointe ne sont marqués comme courrier indésirable à haut niveau de confiance.|`X-CustomSpam: Empty Message`|
|**JavaScript ou VBScript dans le code HTML** <p> *MarkAsSpamJavaScriptInHtml*|Les messages qui utilisent JavaScript ou Visual Basic Script Edition en HTML sont marqués comme courrier indésirable à haut niveau de confiance. <p> Ces langages de script sont utilisés dans les messages électroniques pour que des actions spécifiques se produisent automatiquement.|`X-CustomSpam: Javascript or VBscript tags in HTML`|
|**Balises Frame ou IFrame dans le code HTML** <p> *MarkAsSpamFramesInHtml*|Les messages qui `<frame>` contiennent ou `<iframe>` des balises HTML sont marqués comme courrier indésirable à niveau de confiance élevé. <p> Ces balises sont utilisées dans les messages électroniques pour mettre en forme la page pour l’affichage de texte ou de graphiques.|`X-CustomSpam: IFRAME or FRAME in HTML`|
|**Balises Object dans le code HTML** <p> *MarkAsSpamObjectTagsInHtml*|Les messages qui contiennent `<object>` des balises HTML sont marqués comme courrier indésirable à niveau de confiance élevé. <p> Cette balise permet aux plug-ins ou aux applications de s’exécuter dans une fenêtre HTML.|`X-CustomSpam: Object tag in html`|
|**Balises Embed dans le code HTML** <p> *MarkAsSpamEmbedTagsInHtml*|Les messages qui contiennent `<embed>` des balises HTML sont marqués comme courrier indésirable à niveau de confiance élevé. <p> Cette balise permet l’incorporation de différents types de documents dans un document HTML (par exemple, des sons, des vidéos ou des images).|`X-CustomSpam: Embed tag in html`|
|**Balises Form dans le code HTML** <p> *MarkAsSpamFormTagsInHtml*|Les messages qui contiennent `<form>` des balises HTML sont marqués comme courrier indésirable à niveau de confiance élevé. <p> Cette balise est utilisée pour créer des formulaires de site web. Les publicités électroniques utilisent souvent cette balise pour demander des informations au destinataire.|`X-CustomSpam: Form tag in html`|
|**Bogues web dans le code HTML** <p> *MarkAsSpamWebBugsInHtml*|Un *bogue web* (également appelé balise *web)* est un élément graphique (souvent d’un pixel par pixel) utilisé dans les messages électroniques pour déterminer si le message a été lu par le destinataire. <p> Les messages qui contiennent des bogues web sont marqués comme courrier indésirable à haut niveau de confiance. <p> Les bulletins d’informations légitimes peuvent utiliser des bogues web, même si beaucoup considèrent cela comme une question de confidentialité. |`X-CustomSpam: Web bug`|
|**Appliquer la liste de mots sensibles** <p> *MarkAsSpamSensitiveWordList*|Microsoft conserve une liste dynamique mais non modifiable de mots associés à des messages potentiellement choquants. <p> Les messages qui contiennent des mots de la liste des mots sensibles dans l’objet ou le corps du message sont marqués comme courrier indésirable à niveau de confiance élevé.|`X-CustomSpam: Sensitive word in subject/body`|
|**Enregistrement SPF : échec sévère** <p> *MarkAsSpamSpfRecordHardFail*|Les messages envoyés à partir d’une adresse IP qui n’est pas spécifiée dans l’enregistrement SPF (Sender Policy Framework) dans le DNS pour le domaine de messagerie source sont marqués comme courrier indésirable à niveau de confiance élevé. <p> Le mode test n’est pas disponible pour ce paramètre.|`X-CustomSpam: SPF Record Fail`|
|**Filtrage conditionnel de l'ID de l'expéditeur : échec sévère** <p> *MarkAsSpamFromAddressAuthFail*|Les messages qui échouent en cas d’échec de vérification conditionnelle de l’ID de l’expéditeur sont marqués comme courrier indésirable. <p> Ce paramètre combine une vérification SPF avec une vérification de l’ID de l’expéditeur pour vous protéger contre les en-têtes de message qui contiennent des expéditeurs falsifiés. <p> Le mode test n’est pas disponible pour ce paramètre.|`X-CustomSpam: SPF From Record Fail`|
|**Rétrodiffusion de rapport de non-remise** <p> *MarkAsSpamNdrBackscatter*|*La backscatter* est des rapports de non-remise inutiles (également appelés rapports de non-remise ou de non-remise) causés par des expéditeurs falsifiés dans les messages électroniques. Pour plus d’informations, voir Messages de [la backscatter et EOP](backscatter-messages-and-eop.md). <p> Vous n’avez pas besoin de configurer ce paramètre dans les environnements suivants, car les NDR légitimes sont remis et la backscatter est marquée comme courrier indésirable : <ul><li>Organisations Microsoft 365 avec boîtes aux lettres Exchange Online.</li><li>Organisations de messagerie locales où vous routez *le courrier sortant* via EOP.</li></ul> <p> Dans les environnements EOP autonomes qui protègent les messages entrants vers les boîtes aux lettres sur site, l’turning this setting on or off a le résultat suivant : <ul><li> **On**: les NDR légitimes sont remis et la backscatter est marquée comme courrier indésirable.</li><li>**Off:** Legitimate NDRs and backscatter go through normal spam filtering. La plupart des NDR légitimes sont remis à l’expéditeur du message d’origine. Certains d’entre eux, mais pas tous, sont marqués comme courrier indésirable à haut niveau de confiance. Par définition, la backscatter peut uniquement être remis à l’expéditeur usurpé, et non à l’expéditeur d’origine.</li></ul> <p> Le mode test n’est pas disponible pour ce paramètre.|`X-CustomSpam: Backscatter NDR`|
|