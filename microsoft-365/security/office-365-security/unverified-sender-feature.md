---
title: Expéditeur non vérifié
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Pour empêcher les messages de hameçonnage d’atteindre votre boîte aux lettres, Outlook.com et Outlook sur le Web Vérifiez que l’expéditeur est bien ce qu’il dit, et marquez les messages suspects comme courrier indésirable.
ms.openlocfilehash: 513a45594dd41db56abe143ea6edca7074539d2f
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42082000"
---
# <a name="unverified-sender"></a>Expéditeur non vérifié

> [!NOTE]
> Ces mises à jour s’exécutent désormais et peuvent ne pas être disponibles pour tous les utilisateurs. Cette fonctionnalité est prise en charge pour les utilisateurs d’Enterprise Outlook.com et d’entreprise Outlook Win32. Il n’est pas disponible actuellement pour les utilisateurs d’Office 365.

Pour empêcher les messages de hameçonnage d’atteindre votre boîte aux lettres, Office 365 vérifie que les expéditeurs sont bien ceux qu’ils disent être et marquent les messages suspects comme du courrier indésirable.

> [!IMPORTANT]
> Lorsqu’un message est marqué comme une escroquerie de type hameçonnage, Outlook affiche un avertissement en haut de la page, mais tous les liens dans le message peuvent toujours être ouverts.

## <a name="how-can-i-identify-a-suspicious-message-in-my-inbox"></a>Comment puis-je identifier un message suspect dans ma boîte de réception ?

Outlook affiche des indicateurs lorsque l’expéditeur d’un message ne peut pas être identifié ou que son identité est différente de ce que vous voyez dans l’adresse de l’expéditeur.

## <a name="you-see-a--in-the-sender-image"></a>Un «  ? » apparaît dans l’image de l’expéditeur

Lorsque Office 365 ne peut pas vérifier l’identité de l’expéditeur à l’aide de techniques d’authentification de messagerie, un «  ? » s’affiche dans l’image de l’expéditeur.

![Le message n’a pas passé la vérification](../../media/message-did-not-pass-verification.jpg)

Les messages qui ne parvient pas à s’authentifier ne sont pas tous malveillants. Toutefois, vous devez être prudent quant à l’interaction avec les messages qui ne sont pas authentifiés si vous ne reconnaissez pas l’expéditeur. Ou, si vous reconnaissez un expéditeur qui ne possède pas de «  ? » normalement dans l’image de l’expéditeur, mais que vous le voyez soudainement, cela peut être un signe que l’expéditeur est usurpé.

## <a name="how-to-manage-which-messages-receive-the-unverified-sender-treatment"></a>Comment gérer les messages qui reçoivent le traitement de l’expéditeur non vérifié 

Si vous êtes un client Office 365, vous pouvez gérer cette fonctionnalité via le centre de sécurité & conformité d’Office 365.

- Dans le centre de sécurité & conformité, les administrateurs globaux ou de sécurité peuvent activer ou désactiver la fonctionnalité via la protection contre l’usurpation d’identité dans le cadre de la stratégie anti-hameçonnage. En outre, vous pouvez utiliser la cmdlet **Set-antiphishpolicy permet** dans Exchange Online PowerShell. Pour plus d’informations, consultez la rubrique [anti-hameçonnage protection dans Office 365](anti-phishing-protection.md) et [Set-antiphishpolicy permet](https://docs.microsoft.com/powershell/module/exchange/advanced-threat-protection/set-antiphishpolicy).

    ![Modification des expéditeurs non authentifiés dans l’interface graphique.](../../media/unverified-sender-article-editing-unauthenticated-senders.jpg)

- Si un administrateur a identifié un faux positif et qu’un expéditeur ne doit pas recevoir le traitement de l’expéditeur non vérifié, vous pouvez effectuer l’une des actions suivantes pour ajouter l’expéditeur à la liste des usurpations d’identité usurpée :

  - Ajoutez la paire de domaines par le biais de la vue d’aide à la décision. Pour plus d’informations, consultez la [procédure pas à pas : usurpation](walkthrough-spoof-intelligence-insight.md)d’information.

  - Ajoutez la paire de domaines via la cmdlet **Set-PhishFilterPolicy** dans Exchange Online PowerShell. Pour plus d’informations, reportez-vous à [Set-PhishFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/advanced-threat-protection/set-phishfilterpolicy) et à [configurer les stratégies anti-hameçonnage et anti-hameçonnage d’Office 365 ATP](set-up-anti-phishing-policies.md).

De plus, nous n’appliquons pas le traitement de l’expéditeur non vérifié si le message a été remis à la boîte de réception via des règles de flux de messagerie (également appelées règles de transport) ou la liste des domaines approuvés (stratégies anti-courrier indésirable).

## <a name="how-to-manage-the-via-tag"></a>Gestion de la balise « via » 

Si vous êtes un client Office 365, vous pouvez gérer cette fonctionnalité via le centre de sécurité & conformité d’Office 365, de la même manière que vous gérez le traitement des expéditeurs non vérifiés. Si vous ajoutez l’expéditeur à la liste d’usurpation d’identité usurpée, le traitement « via » ne sera pas appliqué.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

### <a name="what-criteria-does-outlookcom-and-outlook-win32-desktop-use-to-add-the--and-the-via-properties"></a>Quels sont les critères utilisés par Outlook.com et le bureau Win32 Outlook pour ajouter les propriétés «  ? » et « via » ?

Pour le «  ? » de l’image de l’expéditeur : Outlook.com nécessite que le message passe l’authentification SPF ou DKIM et reçoit une passe dMarc ou une authentification composite à partir de l’aide à l’usurpation d’Office 365. Pour plus d’informations, reportez-vous à la rubrique [set up SPF in Office 365 pour éviter l’usurpation](set-up-spf-in-office-365-to-help-prevent-spoofing.md) et l' [utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Office 365](use-dkim-to-validate-outbound-email.md).

Pour la balise via : si le domaine de l’adresse de l’expéditeur est différent du domaine dans la signature DKIM ou SMTP MAIL FROM, Outlook.com affiche le domaine dans l’un de ces deux champs (en préférant la signature DKIM).

### <a name="how-do-i-remove-the--without-utilizing-the-spoof-intelligence-spoof-allow-list"></a>Comment supprimer le «  ? » sans utiliser la liste d’usurpation d’identité d’aide à la décision ?

Pour le «  ? » de l’image de l’expéditeur : en tant qu’expéditeur, vous devez authentifier votre message avec SPF ou DKIM.

Pour la balise via : en tant qu’expéditeur, vous devez vous assurer que le domaine dans la signature DKIM ou SMTP MAIL FROM est le même que le domaine de l’adresse de provenance ou qu’il s’agit d’un sous-domaine de celui-ci.

### <a name="do-outlookcom-and-outlook-win32-desktop-show-this-for-every-message-that-doesnt-pass-authentication"></a>Est-ce que Outlook.com et le bureau Win32 d’Outlook indiquent cela pour chaque message qui ne passe pas l’authentification ?

Pas nécessairement. Office 365 peut avoir d’autres propriétés dans le message pour authentifier l’expéditeur.

## <a name="related-topics"></a>Voir aussi

[Protéger votre compte de messagerie Outlook.com](https://support.office.com/article/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

[Gérer le hameçonnage ou l’usurpation d’identité dans Outlook.com](https://support.office.com/article/0d882ea5-eedc-4bed-aebc-079ffa1105a3)

[Filtrage du courrier indésirable et du courrier indésirable dans Outlook sur le Web](https://support.office.com/article/db786e79-54e2-40cc-904f-d89d57b7f41d)
