---
title: Gérer les autorisations et les blocs dans la liste d’autorisations/de blocs du locataire
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 08/11/2022
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Découvrez comment gérer les autorisations et les blocs dans la liste d’autorisations/blocs du locataire dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9993241a42b40fd670e83d0e28938fa9a4625086
ms.sourcegitcommit: 031b3e963478f642a0d23be37a01f23a01cb3d84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2022
ms.locfileid: "67441590"
---
# <a name="manage-your-allows-and-blocks-in-the-tenant-allowblock-list"></a>Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans Exchange Online boîtes aux lettres, vous pouvez être en désaccord avec le verdict de filtrage EOP. Par exemple, un bon message peut être marqué comme mauvais (faux positif) ou un message incorrect peut être autorisé (un faux négatif).

La liste d’autorisation/de blocage des locataires dans le portail Microsoft 365 Defender vous permet de remplacer manuellement les verdicts de filtrage Microsoft 365. La liste d’autorisation/de blocage du locataire est utilisée pendant le flux de messagerie pour les messages entrants, qui forment des expéditeurs externes (ne s’appliquent pas aux messages intra-organisation) et au moment où l’utilisateur clique.

La liste Autoriser/Bloquer du locataire est disponible dans le portail Microsoft 365 Defender dans <https://security.microsoft.com> \> **Policies & rules** \> **Threat Policies** \> **Tenant Allow/Block Lists** dans la section **Règles**. Pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

Pour obtenir des instructions de création et de configuration d’entrée, consultez les rubriques suivantes :

- **Domaines et adresses e-mail** et **expéditeurs usurpés d’identité** : [autoriser ou bloquer des e-mails à l’aide de la liste d’autorisation/de blocage du locataire](allow-block-email-spoof.md)
- **Fichiers** : [Autoriser ou bloquer des fichiers à l’aide de la liste d’autorisations/de blocs du locataire](allow-block-files.md)
- **URL** : [Autorisez ou bloquez des URL à l’aide de la liste d’autorisations/de blocs du locataire](allow-block-urls.md).

Ces articles contiennent des procédures dans le portail Microsoft 365 Defender et dans PowerShell.

## <a name="block-entries-in-the-tenant-allowblock-list"></a>Bloquer les entrées dans la liste d’autorisations/de blocs du locataire

Utilisez le portail Soumissions (également appelé *soumission d’administrateur*) <https://security.microsoft.com/reportsubmission> pour créer des entrées de bloc pour les types d’éléments suivants lorsque vous les signalez sous forme de faux positifs à Microsoft :

- **Domaines et adresses e-mail** :
  - Email messages de ces expéditeurs sont marqués comme *courrier indésirable à haut niveau de confiance* (SCL = 9). Ce qui arrive aux messages est déterminé par la [stratégie anti-courrier indésirable](configure-your-spam-filter-policies.md) qui a détecté le message pour le destinataire. Dans la stratégie anti-courrier indésirable par défaut et les nouvelles stratégies personnalisées, les messages marqués comme courrier indésirable à haut niveau de confiance sont remis par défaut au dossier Junk Email. Dans les [stratégies de sécurité prédéfinies](preset-security-policies.md) Standard et Strict, les messages indésirables à haut niveau de confiance sont mis en quarantaine.
  - Les utilisateurs de l’organisation ne peuvent pas envoyer de courrier électronique à ces domaines et adresses bloqués. Ils recevront le rapport de non-remise suivant (également appelé NDR ou message de rebond) : `5.7.1  Your message can't be delivered because one or more recipients are blocked by your organization's tenant allow/block list policy.`

- **Fichiers** : Email messages contenant ces fichiers bloqués sont bloqués en tant que *programmes malveillants*.

- **URL** : Email messages contenant ces URL bloquées sont bloqués en tant *qu’hameçonnage à haut niveau de confiance*.

Dans la liste d’autorisation/de blocage du locataire, vous pouvez également créer directement des entrées de bloc pour les types d’éléments suivants :

- **Domaines et adresses e-mail**, **fichiers** et **URL**.

- **Expéditeurs usurpés** : si vous substituez manuellement un verdict d’autorisation existant à partir de [l’intelligence](learn-about-spoof-intelligence.md) d’usurpation d’identité, l’expéditeur usurpé d’identité bloqué devient une entrée de bloc manuelle qui apparaît uniquement sous l’onglet **Expéditeurs usurpés** dans la liste d’autorisations/blocs du locataire.

Par défaut, les entrées de bloc pour **les domaines et les adresses e-mail**, **les fichiers** et **les URL** expirent au bout de 30 jours, mais vous pouvez les définir pour expirer jusqu’à 90 jours ou pour ne jamais expirer. Les entrées de bloc pour **les expéditeurs usurpés** n’expirent jamais.

## <a name="allow-entries-in-the-tenant-allowblock-list"></a>Autoriser les entrées dans la liste d’autorisations/de blocs du locataire

Dans la plupart des cas, vous ne pouvez pas créer directement des entrées d’autorisation dans la liste d’autorisations/de blocs du locataire :

- **Domaines et adresses e-mail**, **fichiers** et URL : vous ne pouvez pas créer d’entrées d’autorisation directement dans la liste d’autorisations/de **blocs** du locataire. Au lieu de cela, vous utilisez le portail <https://security.microsoft.com/reportsubmission> Soumissions pour signaler **l’e-mail**, la **pièce jointe** ou l’URL à Microsoft, car cela **n’aurait pas dû être bloqué (Faux positif).**

- **Expéditeurs usurpés** :
  - Si l’usurpation d’identité a déjà bloqué le message en tant qu’usurpation d’identité, utilisez le portail <https://security.microsoft.com/reportsubmission> Soumissions pour signaler **l’e-mail** à Microsoft, car il **n’aurait pas dû être bloqué (Faux positif).**
  - Vous pouvez créer de manière proactive une entrée d’autorisation pour un expéditeur **usurpé** sous l’onglet Expéditeur usurpé dans la liste d’autorisation/de blocage du locataire avant [que l’intelligence](learn-about-spoof-intelligence.md) de l’usurpation d’identité identifie et bloque le message en tant qu’usurpation d’identité.

La liste suivante décrit ce qui se passe dans la liste d’autorisations/blocages du locataire lorsque vous signalez quelque chose à Microsoft sous la forme d’un faux positif dans le portail d’envoi :

- **Email pièces jointes** et **URL** : une entrée d’autorisation est créée et s’affiche sous l’onglet **Fichiers** ou URL de la liste d’autorisations/de **blocs** du locataire.

- **Email** : si un message a été bloqué par la pile de filtrage Microsoft 365, une entrée d’autorisation peut être créée dans la liste d’autorisation/de blocage du locataire :

  - Si le message a été bloqué par [l’intelligence de l’usurpation](learn-about-spoof-intelligence.md) d’identité, une entrée d’autorisation pour l’expéditeur est créée et s’affiche sous l’onglet **Expéditeurs usurpés** dans la liste verte des locataires.

  - Si le message a été bloqué par la [protection de domaine ou d’emprunt](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) d’identité de l’utilisateur dans Defender pour Office 365, une entrée d’autorisation n’est pas créée dans la liste d’autorisation/de blocage du locataire. Au lieu de cela, le domaine ou l’expéditeur est ajouté à la **section Expéditeurs approuvés et domaines** dans la [stratégie anti-hameçonnage](configure-mdo-anti-phishing-policies.md#use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies) qui a détecté le message.

  - Si le message a été bloqué pour d’autres raisons, une entrée d’autorisation pour l’expéditeur est créée et s’affiche sous l’onglet **Domaines & adresses** dans la liste verte des locataires.

  - Si le message n’a pas été bloqué et que l’entrée d’autorisation pour l’expéditeur n’est pas créée, il ne se trouve pas sous l’onglet **Expéditeurs usurpés** ou l’onglet **Domaines & adresses** .

Par défaut, autorisez les **entrées pour les domaines et les adresses e-mail**, **les fichiers** et **les URL** qui expirent après 30 jours, ce qui est également le maximum. Les entrées autorisées pour **les expéditeurs usurpés** n’expirent jamais.

> [!NOTE]
> Étant donné que Microsoft gère les entrées d’autorisation pour vous, les entrées d’autorisation **inutiles pour les domaines et les adresses e-mail**, **les URL** ou **les fichiers** seront supprimées. Ce comportement protège votre organisation et permet d’éviter les entrées d’autorisation mal configurées. Si vous n’êtes pas d’accord avec le verdict, vous devrez peut-être ouvrir une demande de support pour déterminer pourquoi un message est toujours considéré comme incorrect.
>
> Les autorisations sont ajoutées pendant le flux de messagerie, en fonction des filtres qui ont déterminé que le message était malveillant. Par exemple, si l’expéditeur et une URL du message ont été déterminés comme étant incorrects, une entrée d’autorisation est créée pour l’expéditeur et une entrée d’autorisation est créée pour l’URL.
>
> Lorsque cette entité (adresse de domaine ou e-mail, URL, fichier) est à nouveau rencontrée, tous les filtres associés à cette entité sont ignorés.
>
> Pendant le flux de courrier, si les messages du domaine ou de l’adresse e-mail passent d’autres vérifications dans la pile de filtrage, les messages sont remis. Par exemple, si [l’authentification par e-mail](email-validation-and-authentication.md) réussit, un message d’un expéditeur dans l’entrée d’autorisation est remis.

## <a name="what-to-expect-after-you-add-an-allow-or-block-entry"></a>À quoi vous attendre après l’ajout d’une entrée d’autorisation ou de blocage

Une fois que vous avez ajouté une entrée d’autorisation via le portail Soumissions ou une entrée de bloc dans la liste d’autorisation/de blocage du locataire, l’entrée doit commencer à fonctionner immédiatement.

Nous vous recommandons de laisser les entrées expirer automatiquement après 30 jours pour voir si le système a découvert l’autorisation ou le bloc. Si ce n’est pas le cas, vous devez faire une autre entrée pour donner au système encore 30 jours pour apprendre.
