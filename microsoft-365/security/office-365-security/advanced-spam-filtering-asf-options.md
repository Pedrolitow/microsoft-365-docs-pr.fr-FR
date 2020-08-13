---
title: Paramètres ASF dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: b286f853-b484-4af0-b01f-281fffd85e7a
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les paramètres de filtre de courrier indésirable avancés (ASF) disponibles dans les stratégies de blocage du courrier indésirable dans Exchange Online Protection (EOP).
ms.openlocfilehash: b314b8b2a2de72987d9acff688602df0e0947293
ms.sourcegitcommit: 6a1a8aa024fd685d04da97bfcbc8eadacc488534
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46653340"
---
# <a name="advanced-spam-filter-asf-settings-in-eop"></a>Paramètres du filtre de courrier indésirable avancé (ASF) dans EOP

> [!NOTE]
> Les paramètres ASF actuellement disponibles dans les stratégies de blocage du courrier indésirable sont en cours de dépréciation. Nous vous recommandons de ne pas utiliser ces paramètres dans les stratégies de blocage du courrier indésirable. La fonctionnalité de ces paramètres ASF est incorporée dans les autres parties de la pile de filtrage. Pour plus d’informations, consultez la rubrique [paramètres de stratégie anti-courrier indésirable EOP](recommended-settings-for-eop-and-office365-atp.md#eop-anti-spam-policy-settings).

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EoP) autonomes sans boîte aux lettres Exchange Online, les paramètres de filtre de courrier indésirable (ASF) des stratégies de blocage du courrier indésirable (également appelés stratégies de filtrage du courrier indésirable ou stratégies de filtrage de contenu) permettent aux administrateurs de marquer les messages comme courrier ASF cible spécifiquement ces propriétés car elles sont généralement présentes dans le courrier indésirable. En fonction de la propriété, les détections ASF marquent le message comme étant du courrier **indésirable** ou du **courrier indésirable à niveau de confiance élevée**.

> [!NOTE]
> L’activation d’un ou de plusieurs paramètres ASF est une approche agressive pour le filtrage du courrier indésirable. Vous ne pouvez pas signaler les messages qui sont filtrés par ASF comme faux positifs. Vous pouvez identifier les messages qui ont été filtrés par ASF en procédant comme suit :
> - Notifications périodiques de mise en quarantaine du courrier indésirable de l’utilisateur final.
>
> - La présence de messages filtrés en quarantaine.
>
> - Les `X-CustomSpam:` champs d’en-tête X spécifiques ajoutés aux messages, comme décrit dans cette rubrique.

Les sections suivantes décrivent les paramètres et les options ASF disponibles dans les stratégies de blocage du courrier indésirable dans le centre de sécurité & conformité et dans Exchange Online PowerShell ou autonome EOP PowerShell ([New-HostedContentFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/new-hostedcontentfilterpolicy) et [Set-HostedContentFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/set-hostedcontentfilterpolicy)). Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

## <a name="enable-disable-or-test-asf-settings"></a>Activer, désactiver ou tester les paramètres ASF

Pour chaque paramètre ASF, les options suivantes sont disponibles dans les stratégies de blocage du courrier indésirable :

- **Activé**: ASF ajoute le champ d’en-tête X correspondant au message et marque le message comme **courrier indésirable** (SCL 5 ou 6 pour [augmenter les paramètres de score de courrier indésirable](#increase-spam-score-settings)) ou courrier indésirable à **niveau de confiance élevé** (SCL 9 pour [marquer comme courrier indésirable](#mark-as-spam-settings)).

- **Désactivé**: le paramètre ASF est désactivé. Il s’agit de la valeur par défaut, et nous vous recommandons de ne pas la modifier.

- **Test**: ASF ajoute le champ d’en-tête X correspondant au message. Ce qu’il advient du message est déterminé par la valeur des **options de mode de test** (*TestModeAction*) :

  - **Aucun**: le routage et la remise des messages ne sont pas affectés par la détection ASF. Le message est toujours soumis à d’autres types de filtrage et de règles dans EOP.

  - **Ajouter un texte d’en-tête x par défaut (*AddXHeader*)**: la valeur d’en-tête x `X-CustomSpam: This message was filtered by the custom spam filter option` est ajoutée au message. Vous pouvez utiliser cette valeur dans les règles de boîte de réception ou les règles de flux de messagerie (également appelées règles de transport) pour affecter le routage et la remise du message.

  - **Envoyer un message CCI (*BccMessage*)**: les adresses de messagerie spécifiées (valeur du paramètre *TestModeBccToRecipients* dans PowerShell) sont ajoutées au champ CCI du message, et le message est remis aux destinataires CCI. Dans le centre de sécurité & conformité, séparez les adresses de messagerie par des points-virgules (;). Dans PowerShell, vous séparez plusieurs adresses de messagerie par des virgules.

  **Remarques** :

  - Le mode test n’est pas disponible pour les paramètres ASF suivants :

    - **Filtrage des ID de l’expéditeur conditionnel : échec matériel** (*MarkAsSpamFromAddressAuthFail*)
    - Notification de **non-remise rétrodiffusion**(*MarkAsSpamNdrBackscatter*)
    - **Enregistrement SPF : échec matériel** (*MarkAsSpamSpfRecordHardFail*)

  - La même action de mode test est appliquée à *tous les* paramètres ASF définis sur **test**. Vous ne pouvez pas configurer différentes actions de mode test pour différents paramètres ASF.

## <a name="increase-spam-score-settings"></a>Augmenter les paramètres de score de courrier indésirable

Les paramètres ASF suivants définissent le seuil de probabilité de courrier indésirable (SCL) de messages détectés à 5 ou 6, ce qui correspond au verdict du filtre de **courrier indésirable** et à l’action correspondante dans les stratégies anti-courrier indésirable.

****

|Paramètre de stratégie de blocage du courrier indésirable|Description|En-tête X ajouté|
|---|---|---|
|**Liens d'image vers des sites distants** <br/><br/> *IncreaseScoreWithImageLinks*|Les messages contenant `<Img>` des liens HTML vers des sites distants (par exemple, à l’aide du protocole http) sont marqués comme courrier indésirable.|`X-CustomSpam: Image links to remote sites`|
|**Redirection de l'URL vers un autre port** <br/><br/> *IncreaseScoreWithRedirectToOtherPort*|Message contenant des liens hypertexte qui redirigent vers des ports TCP autres que 80 (HTTP), 8080 (http de remplacement) ou 443 (HTTPs) sont marqués comme courrier indésirable.|`X-CustomSpam: URL redirect to other port`|
|**Adresse IP numérique dans l'URL** <br/><br/> *IncreaseScoreWithNumericIps*|Les messages qui contiennent des URL numériques (en général, des adresses IP) sont marqués comme courrier indésirable.|`X-CustomSpam: Numeric IP in URL`|
|**URL vers les sites web .biz ou .info** <br/><br/> *IncreaseScoreWithBizOrInfoUrls*|Les messages qui contiennent des liens. biz ou. info dans le corps du message sont marqués comme courrier indésirable.|`X-CustomSpam: URL to .biz or .info websites`|
|

## <a name="mark-as-spam-settings"></a>Marquer comme courrier indésirable

Les paramètres ASF suivants définissent la valeur SCL des messages détectés sur 9, ce qui correspond au verdict du filtre de courrier indésirable à **fiabilité élevée** et à l’action correspondante dans les stratégies anti-courrier indésirable.

****

|Paramètre de stratégie de blocage du courrier indésirable|Description|En-tête X ajouté|
|---|---|---|
|**Messages vides** <br/><br/> *MarkAsSpamEmptyMessages*|Les messages sans objet, aucun contenu dans le corps du message et aucune pièce jointe ne sont marqués comme courrier indésirable à niveau de confiance élevé.|`X-CustomSpam: Empty Message`|
|**JavaScript ou VBScript dans le code HTML** <br/><br/> *MarkAsSpamJavaScriptInHtml*|Les messages qui utilisent JavaScript ou Visual Basic Script Edition en HTML sont marqués comme courrier indésirable à niveau de confiance élevé. <br/><br/> Ces langages de script sont utilisés dans les messages électroniques pour déclencher automatiquement des actions spécifiques.|`X-CustomSpam: Javascript or VBscript tags in HTML`|
|**Balises Frame ou IFrame dans le code HTML** <br><br/> *MarkAsSpamFramesInHtml*|Les messages qui contiennent `<frame>` ou `<iframe>` des balises HTML sont marqués comme courrier indésirable à confiance élevée. <br/><br/> Ces balises sont utilisées dans les messages électroniques pour mettre en forme la page afin d’afficher du texte ou des graphiques.|`X-CustomSpam: IFRAME or FRAME in HTML`|
|**Balises Object dans le code HTML** <br><br/> *MarkAsSpamObjectTagsInHtml*|Les messages qui contiennent `<object>` des balises HTML sont marqués comme courrier indésirable à confiance élevée. <br/><br/> Cette balise permet aux plug-ins ou aux applications de s’exécuter dans une fenêtre HTML.|`X-CustomSpam: Object tag in html`|
|**Balises Embed dans le code HTML** <br><br/> *MarkAsSpamEmbedTagsInHtml*|Le message contenant `<embed>` des balises HTML est marqué comme courrier indésirable à niveau de confiance élevé. <br/><br/> Cette balise permet l’incorporation de différents types de documents de différents types de données dans un document HTML (par exemple, des sons, des films ou des images).|`X-CustomSpam: Embed tag in html`|
|**Balises Form dans le code HTML** <br><br/> *MarkAsSpamFormTagsInHtml*|Les messages qui contiennent `<form>` des balises HTML sont marqués comme courrier indésirable à confiance élevée. <br/><br/> Cette balise est utilisée pour créer des formulaires de site Web. Les publicités électroniques utilisent souvent cette balise pour demander des informations au destinataire.|`X-CustomSpam: Form tag in html`|
|**Bogues web dans le code HTML** <br><br/> *MarkAsSpamWebBugsInHtml*|Un *bug Web* (également appelé « *balise Web*») est un élément graphique (souvent aussi petit qu’un pixel d’un pixel) utilisé dans les messages électroniques pour déterminer si le message a été lu. <br/><br/> Les messages qui contiennent des bogues Web sont marqués comme courrier indésirable à niveau de confiance élevé. <br/><br/> Les bulletins d’information légitimes peuvent utiliser des bogues Web, bien que de nombreux considèrent cette atteinte à la vie privée. |`X-CustomSpam: Web bug`|
|**Appliquer la liste de mots sensibles** <br><br/> *MarkAsSpamSensitiveWordList*|Microsoft gère une liste dynamique, mais non modifiable, de mots qui sont associés à des messages potentiellement choquants. <br/><br/> Les messages qui contiennent des mots de la liste de mots sensibles dans l’objet ou le corps du message sont marqués comme courrier indésirable à niveau de confiance élevé.|`X-CustomSpam: Sensitive word in subject/body`|
|**Enregistrement SPF : échec sévère** <br><br/> *MarkAsSpamSpfRecordHardFail*|Les messages envoyés à partir d’une adresse IP qui n’est pas spécifiée dans l’enregistrement SPF (Sender Policy Framework) de DNS pour le domaine de messagerie source sont marqués comme courrier indésirable à confiance élevée. <br/><br/> Le mode test n’est pas disponible pour ce paramètre.|`X-CustomSpam: SPF Record Fail`|
|**Filtrage conditionnel de l'ID de l'expéditeur : échec sévère** <br><br/> *MarkAsSpamFromAddressAuthFail*|Les messages qui échouent à la vérification de l’ID de l’expéditeur conditionnel sont marqués comme courrier indésirable. <br/><br/> Ce paramètre associe un contrôle SPF à une vérification de l’ID de l’expéditeur pour vous protéger des en-têtes de message contenant des expéditeurs falsifiés. <br/><br/> Le mode test n’est pas disponible pour ce paramètre.|`X-CustomSpam: SPF From Record Fail`|
|**Rétrodiffusion de rapport de non-remise** <br><br/> *MarkAsSpamNdrBackscatter*|*Rétrodiffusion* est des notifications d’échec de remise inutiles (également appelées notifications de non-remise) causées par des expéditeurs falsifiés dans les messages électroniques. Pour plus d’informations, consultez la rubrique [messages rétrodiffusion et EOP](backscatter-messages-and-eop.md). <br/><br/> Vous n’avez pas besoin de configurer ce paramètre dans les environnements suivants, car les notifications d’échec de remise légitimes sont remises et rétrodiffusion est marqué comme courrier indésirable : <ul><li>Organisations Microsoft 365 avec des boîtes aux lettres Exchange Online.</li><li>Les organisations de messagerie locales dans lesquelles vous acheminez les messages *sortants* via EOP.</li></ul><br/> Dans les environnements EOP autonomes qui protègent les messages électroniques entrants en boîtes aux lettres locales, l’activation ou la désactivation de ce paramètre a les résultats suivants : <ul><li> **Activé**: les notifications d’échec de remise légitimes sont remises et rétrodiffusion est marqué comme courrier indésirable.</li><li>**Désactivé**: les notifications d’échec de remise et les rétrodiffusion légitimes passent par un filtrage normal. La plupart des notifications d’échec de remise légitimes seront envoyées à l’expéditeur du message d’origine. Certains rétrodiffusion, mais pas tous, sont marqués comme courrier indésirable à fiabilité élevée. Par définition, rétrodiffusion peut uniquement être remis à l’expéditeur usurpé, et non à l’expéditeur d’origine.</li></ul><br/> Le mode test n’est pas disponible pour ce paramètre.|`X-CustomSpam: Backscatter NDR`|
|
