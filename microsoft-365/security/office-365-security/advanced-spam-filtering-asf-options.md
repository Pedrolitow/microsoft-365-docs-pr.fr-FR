---
title: Paramètres ASF dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: b286f853-b484-4af0-b01f-281fffd85e7a
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les paramètres asf (Advanced Spam Filter) disponibles dans les stratégies anti-courrier indésirable dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 75fca937049e71576e1dd599b4cc0f7fba2a2211
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647664"
---
# <a name="advanced-spam-filter-asf-settings-in-eop"></a>Paramètres asf (Advanced Spam Filter) dans EOP

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans toutes les organisations Microsoft 365, les paramètres ASF (Advanced Spam Filter) dans les stratégies anti-courrier indésirable dans EOP permettent aux administrateurs de marquer les messages comme courrier indésirable en fonction de propriétés de message spécifiques. ASF cible spécifiquement ces propriétés, car elles se trouvent généralement dans le courrier indésirable. Selon la propriété, les détections ASF marquent le message comme **courrier indésirable** ou **courrier indésirable à haut niveau de confiance**.

> [!NOTE]
> L’activation d’un ou de plusieurs paramètres ASF est une approche agressive du filtrage du courrier indésirable. Vous ne pouvez pas signaler les messages filtrés par ASF en tant que faux positifs. Vous pouvez identifier les messages qui ont été filtrés par ASF par :
>
> - Notifications périodiques de mise en quarantaine du courrier indésirable et des verdicts de filtre anti-courrier indésirable à haut niveau de confiance.
> - Présence de messages filtrés en quarantaine.
> - Champs d’en-tête X spécifiques `X-CustomSpam:` qui sont ajoutés aux messages, comme décrit dans cet article.

Les sections suivantes décrivent les paramètres et options ASF disponibles dans les stratégies anti-courrier indésirable dans le portail Microsoft 365 Defender et dans Exchange Online PowerShell ou EOP PowerShell autonome ([New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy) et [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy)). Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

## <a name="enable-disable-or-test-asf-settings"></a>Activer, désactiver ou tester les paramètres ASF

Pour chaque paramètre ASF, les options suivantes sont disponibles dans les stratégies anti-courrier indésirable :

- **Activé** : ASF ajoute le champ d’en-tête X correspondant au message et marque le message en tant que **courrier indésirable** (SCL 5 ou 6 pour [augmenter les paramètres de score de courrier indésirable](#increase-spam-score-settings)) ou **courrier indésirable à confiance élevée** (SCL 9 pour [marquer comme paramètres de courrier indésirable](#mark-as-spam-settings)).
- **Désactivé** : le paramètre ASF est désactivé. Il s’agit de la valeur par défaut, et nous vous recommandons de ne pas la modifier.
- **Test** : ASF ajoute le champ d’en-tête X correspondant au message. Ce qui arrive au message est déterminé par la valeur **du mode test** (*TestModeAction*) :
  - **Aucun** : la remise des messages n’est pas affectée par la détection ASF. Le message est toujours soumis à d’autres types de filtrage et de règles dans EOP.
  - **Ajouter le texte d’en-tête X par défaut (*AddXHeader*)** : la valeur `X-CustomSpam: This message was filtered by the custom spam filter option` d’en-tête X est ajoutée au message. Vous pouvez utiliser cette valeur dans les règles de boîte de réception ou les règles de flux de courrier (également appelées règles de transport) pour affecter la remise du message.
  - **Envoyer un message CCI (*BccMessage*) : les adresses** e-mail spécifiées (valeur du paramètre *TestModeBccToRecipients* dans PowerShell) sont ajoutées au champ CCI du message et le message est remis aux destinataires CCI supplémentaires. Dans le portail Microsoft 365 Defender, vous séparez plusieurs adresses e-mail par points-virgules (;). Dans PowerShell, vous séparez plusieurs adresses e-mail par virgules.

  **Remarques** :

  - Le mode test n’est pas disponible pour les paramètres ASF suivants :
    - **Filtrage de l’ID de l’expéditeur conditionnel : échec dur** (*MarkAsSpamFromAddressAuthFail*)
    - **Backscatter NDR**(*MarkAsSpamNdrBackscatter*)
    - **Enregistrement SPF : échec dur** (*MarkAsSpamSpfRecordHardFail*)
  - La même action de mode test est appliquée à *tous les* paramètres ASF définis sur **Test**. Vous ne pouvez pas configurer différentes actions de mode de test pour différents paramètres ASF.

## <a name="increase-spam-score-settings"></a>Augmenter les paramètres de score de courrier indésirable

Les paramètres ASF **augmenter le score de courrier indésirable** suivants définissent le niveau de confiance du courrier indésirable (SCL) des messages détectés sur 5 ou 6, ce qui correspond à un verdict de filtre **de courrier indésirable** et à l’action correspondante dans les stratégies anti-courrier indésirable.

|Paramètre de stratégie anti-courrier indésirable|Description|En-tête X ajouté|
|---|---|---|
|**Liens d’image vers des sites web distants** <p> *IncreaseScoreWithImageLinks*|Les messages qui contiennent des `<Img>` liens de balise HTML vers des sites distants (par exemple, à l’aide de http) sont marqués comme courrier indésirable.|`X-CustomSpam: Image links to remote sites`|
|**Adresse IP numérique dans l'URL** <p> *IncreaseScoreWithNumericIps*|Les messages qui contiennent des URL numériques (généralement des adresses IP) sont marqués comme courrier indésirable.|`X-CustomSpam: Numeric IP in URL`|
|**Redirection de l'URL vers un autre port** <p> *IncreaseScoreWithRedirectToOtherPort*|Les messages qui contiennent des liens hypertexte qui redirigent vers des ports TCP autres que 80 (HTTP), 8080 (http alternatif) ou 443 (HTTPS) sont marqués comme courrier indésirable.|`X-CustomSpam: URL redirect to other port`|
|**Liens vers des sites web .biz ou .info** <p> *IncreaseScoreWithBizOrInfoUrls*|Les messages qui contiennent ou `.info` des `.biz` liens dans le corps du message sont marqués comme courrier indésirable.|`X-CustomSpam: URL to .biz or .info websites`|

## <a name="mark-as-spam-settings"></a>Marquer comme paramètres de courrier indésirable

Les paramètres **ASF mark as spam** suivants définissent la liste SCL des messages détectés sur 9, ce qui correspond à un verdict de filtre **anti-courrier indésirable de confiance élevée** et à l’action correspondante dans les stratégies anti-courrier indésirable.

|Paramètre de stratégie anti-courrier indésirable|Description|En-tête X ajouté|
|---|---|---|
|**Messages vides** <p> *MarkAsSpamEmptyMessages*|Les messages sans objet, aucun contenu dans le corps du message et aucune pièce jointe ne sont marqués comme courrier indésirable à haut niveau de confiance.|`X-CustomSpam: Empty Message`|
|**Balises incorporées en HTML** <p> *MarkAsSpamEmbedTagsInHtml*|Les messages qui contiennent des `<embed>` balises HTML sont marqués comme courrier indésirable à haut niveau de confiance. <p> Cette balise permet l’incorporation de différents types de documents dans un document HTML (par exemple, des sons, des vidéos ou des images).|`X-CustomSpam: Embed tag in html`|
|**JavaScript ou VBScript dans le code HTML** <p> *MarkAsSpamJavaScriptInHtml*|Les messages qui utilisent JavaScript ou Visual Basic Script Edition en HTML sont marqués comme courrier indésirable à haut niveau de confiance. <p> Ces langages de script sont utilisés dans les messages électroniques pour provoquer automatiquement des actions spécifiques.|`X-CustomSpam: Javascript or VBscript tags in HTML`|
|**Balises Form dans le code HTML** <p> *MarkAsSpamFormTagsInHtml*|Les messages qui contiennent des `<form>` balises HTML sont marqués comme courrier indésirable à haut niveau de confiance. <p> Cette balise est utilisée pour créer des formulaires de site web. Les publicités électroniques utilisent souvent cette balise pour demander des informations au destinataire.|`X-CustomSpam: Form tag in html`|
|**Balises frame ou iframe en HTML** <p> *MarkAsSpamFramesInHtml*|Les messages qui contiennent ou `<iframe>` des `<frame>` balises HTML sont marqués comme courrier indésirable à haut niveau de confiance. <p> Ces balises sont utilisées dans les messages électroniques pour mettre en forme la page pour afficher du texte ou des graphiques.|`X-CustomSpam: IFRAME or FRAME in HTML`|
|**Bogues web dans le code HTML** <p> *MarkAsSpamWebBugsInHtml*|Un *bogue web* (également appelé *balise web*) est un élément graphique (souvent aussi petit qu’un pixel par pixel) utilisé dans les messages électroniques pour déterminer si le message a été lu par le destinataire. <p> Les messages contenant des bogues web sont marqués comme courrier indésirable à haut niveau de confiance. <p> Les bulletins d’informations légitimes peuvent utiliser des bogues web, bien que beaucoup considèrent qu’il s’agit d’une atteinte à la vie privée. |`X-CustomSpam: Web bug`|
|**Balises Object dans le code HTML** <p> *MarkAsSpamObjectTagsInHtml*|Les messages qui contiennent des `<object>` balises HTML sont marqués comme courrier indésirable à haut niveau de confiance. <p> Cette balise permet aux plug-ins ou applications de s’exécuter dans une fenêtre HTML.|`X-CustomSpam: Object tag in html`|
|**Mots sensibles** <p> *MarkAsSpamSensitiveWordList*|Microsoft gère une liste dynamique mais non modifiable de mots associés à des messages potentiellement offensants. <p> Les messages qui contiennent des mots de la liste de mots sensibles dans l’objet ou le corps du message sont marqués comme courrier indésirable à haut niveau de confiance.|`X-CustomSpam: Sensitive word in subject/body`|
|**Enregistrement SPF : échec sévère** <p> *MarkAsSpamSpfRecordHardFail*|Les messages envoyés à partir d’une adresse IP qui n’est pas spécifiée dans l’enregistrement SPF Sender Policy Framework (SPF) dans DNS pour le domaine de messagerie source sont marqués comme courrier indésirable à haut niveau de confiance. <p> Le mode test n’est pas disponible pour ce paramètre.|`X-CustomSpam: SPF Record Fail`|

Les paramètres **ASF Mark as spam** suivants définissent la liste SCL des messages détectés sur 6, ce qui correspond à un verdict de filtre **de courrier indésirable** et à l’action correspondante dans les stratégies anti-courrier indésirable.

|Paramètre de stratégie anti-courrier indésirable|Description|En-tête X ajouté|
|---|---|---|
|**Échec du filtrage de l’ID de l’expéditeur** <p> *MarkAsSpamFromAddressAuthFail*|Les messages qui échouent fortement à une vérification conditionnelle de l’ID de l’expéditeur sont marqués comme courrier indésirable. <p> Ce paramètre combine une vérification SPF avec une vérification d’ID d’expéditeur pour vous protéger contre les en-têtes de message qui contiennent des expéditeurs falsifiés. <p> Le mode test n’est pas disponible pour ce paramètre.|`X-CustomSpam: SPF From Record Fail`|
|**Rétrodiffusion** <p> *MarkAsSpamNdrBackscatter*|*La rétrodiffusion* est un rapport de non-remise inutile (également appeléS DNR ou messages de rebond) causé par des expéditeurs falsifiés dans les messages électroniques. Pour plus d’informations, consultez [Les messages de rétrodiffusion et EOP](backscatter-messages-and-eop.md). <p> Vous n’avez pas besoin de configurer ce paramètre dans les environnements suivants, car les DNR légitimes sont remis et la rétrodiffusion est marquée comme courrier indésirable : <ul><li>Microsoft 365 organisations avec des boîtes aux lettres Exchange Online.</li><li>Organisations de messagerie locales où vous routez le courrier *sortant* via Exchange Online Protection (EOP).</li></ul> <p> Dans les environnements EOP autonomes qui protègent les e-mails entrants vers des boîtes aux lettres locales, l’activation ou la désactivation de ce paramètre a le résultat suivant : <ul><li> **Activé** : Les DNR légitimes sont remises et la rétrodiffusion est marquée comme courrier indésirable.</li><li>**Désactivé** : les DNR légitimes et la rétrodiffusion passent par un filtrage normal du courrier indésirable. La plupart des NDR légitimes seront remises à l’expéditeur du message d’origine. Certains, mais pas tous, la rétrodiffusion est marquée comme courrier indésirable. Par définition, la rétrodiffusion ne peut être remise qu’à l’expéditeur usurpé, et non à l’expéditeur d’origine.</li></ul> <p> Le mode test n’est pas disponible pour ce paramètre.|`X-CustomSpam: Backscatter NDR`|
