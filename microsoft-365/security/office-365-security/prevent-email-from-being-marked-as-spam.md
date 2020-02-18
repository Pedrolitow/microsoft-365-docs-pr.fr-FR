---
title: Comment empêcher les faux positifs de se produire dans Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MET150
description: Découvrez le moyen d’empêcher les faux positifs et de conserver les e-mails véritables en dehors du courrier indésirable dans Office 365, Exchange Online et Exchange Online Protection (EOP) en mode autonome.
ms.openlocfilehash: bf6149d21a5088e4507b65c6474918327faf3510
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41598691"
---
# <a name="how-to-prevent-good-email-messages-from-being-marked-as-spam-in-office-365"></a>Éviter le marquage de courrier régulier comme courrier indésirable dans Office 365

 **Votre courrier est marqué comme courrier indésirable dans Office 365 ? Suivez ces conseils.**

Si un e-mail entrant régulier est marqué comme courrier indésirable (un _faux positif_) dans Office 365, Exchange Online ou Exchange Online Protection (EOP) en mode autonome, vous devez en faire état à Microsoft à l’aide de [Utiliser le complément Signaler un message](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2). Vous pouvez de plus envoyer le message à l’aide de l’[Explorateur de soumissions](admin-submission.md).

## <a name="determine-why-the-message-was-marked-as-spam"></a>Déterminer la raison pour laquelle le message a été marqué comme courrier indésirable

Vous pouvez résoudre de nombreux problèmes relatifs aux faux positifs en consultant l’en-tête du courrier électronique afin de déterminer la raison pour laquelle le message a été marqué comme courrier indésirable. Pour afficher l’en-tête du courrier, consulter [Affichage dans Outlook des en-têtes de courrier électronique](https://support.office.com/article/cd039382-dc6e-4264-ac74-c048563d212c).

De façon plus spécifique, vous devez rechercher un champ d’en-tête appelé **X-Forefront-Antispam-Report**. Les données importantes à rechercher sont les suivantes :

- **SFV : SPM** : le message a été marqué comme courrier indésirable par le filtre anti-courrier indésirable (également connu sous le nom de _filtre de contenu_). Pour plus d’informations, voir [Protection de la messagerie Office 365 contre le courrier indésirable](anti-spam-protection.md).

- **SFV:BLK** : indique que l’e-mail a été marqué comme courrier indésirable, car l’adresse d’envoi figure dans la liste des Expéditeurs bloqués du **destinataire**. Pour plus d’informations, consulter [Filtrer le courrier indésirable dans Outlook sur le web](https://support.office.com/article/db786e79-54e2-40cc-904f-d89d57b7f41d) et [Vue d’ensemble du filtre de Courrier indésirable](https://support.office.com/article/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089).

- **SFV : SKS** : le message a été marqué comme courrier indésirable **avant** d’être examiné par le filtre anti-courrier indésirable. Par exemple, une règle de flux de courrier (également appelée règle de transport) définit le seuil de probabilité de courrier indésirable (SCL) d’un e-mail élevé (9) indiquant que celui-ci est un courrier indésirable. Pour en savoir plus sur le SCL, consulter les [Seuils de probabilité de courrier indésirable](spam-confidence-levels.md).

  Exécutez un suivi de message pour déterminer si la règle de flux de messagerie est responsable de la valeur SCL élevée. Pour en savoir plus, voir [Suivi de message dans le Centre de sécurité et de conformité](message-trace-scc.md).

- **SFV : SKB** : le message a été marqué comme courrier indésirable car il correspondait à une entrée de bloc dans une stratégie de filtrage de courrier indésirable (par exemple, expéditeurs ou domaines d’expéditeurs bloqués). Pour plus d’informations, consulter [Configurer vos stratégies de filtre de courrier indésirable](configure-your-spam-filter-policies.md).

- **SFV : BULK** : le message a été identifié comme e-mail en nombre plutôt que comme courrier indésirable par le filtre anti-courrier indésirable. Ceci intervient lorsque la valeur du niveau de réclamations en bloc (BCL) de l’e-mail est **supérieure** au seuil en bloc défini dans les paramètres de stratégie anti-courrier indésirable (une valeur BCL plus faible indique que l’e-mail est probablement un courrier indésirable). Vous pouvez consulter la valeur BCL dans le champ d’en-tête **X-Microsoft-Antispam**.

  Le courrier en nombre (également connu sous le nom de _courrier gris_) est indésirable, mais ne fait pas partie des e-mails marketing ou publicitaires malveillants, qui ont été volontairement ou involontairement demandés par l’utilisateur. Chaque utilisateur a des attentes différentes quant à la façon dont les courriers en nombre doivent être gérés. Vous pouvez ainsi créer des stratégies ou des règles différentes autorisant ou bloquant les courriers en nombre en conséquence. Pour plus d’informations, voir les rubriques suivantes :

  - [Quelle est la différence entre courrier indésirable et message électronique en masse ?](what-s-the-difference-between-junk-email-and-bulk-email.md)

  - [Valeurs BCL](bulk-complaint-level-values.md)

- **CAT:SPOOF** ou **CAT:PHISH** : indique que le message apparaît comme falsifié. Cela signifie que la source du message ne peut pas être validée et peut être suspecte.

  Si l’e-mail provient d’un expéditeur dont l’identité a été usurpée, l’expéditeur légitime correspondant doit vérifier les enregistrements SPF et DKIM de son domaine de courrier dans son DNS public. Consultez le champ d’en-tête **Authentication-Results** pour obtenir plus d'informations. Même s’il peut être difficile de faire en sorte que tous les expéditeurs utilisent des méthodes d’authentification d’e-mail correctes, il peut être extrêmement dangereux de contourner ces vérifications. Il s’agit en effet de la principale cause de courriers d’hameçonnage ou provenant d’un expéditeur dont l’identité a été usurpée.

> [!NOTE]
> • Pour en savoir plus sur les autres valeurs et en-têtes de messages anti-courrier indésirable, voir [En-têtes de message anti-courrier indésirable](anti-spam-message-headers.md). <br/><br/>• Les autres valeurs et champs d’en-têtes n’étant pas expressément décrites sont exclusivement utilisés par l’équipe Microsoft dédiée à la lutte contre les courriers indésirables à des fins de diagnostic. <br/><br/>• Un champ d’en-tête **X-CustomSpam** dans l’en-tête d’un courrier indique que celui-ci a été marqué comme courrier indésirable par le Filtrage avancé de courrier indésirable (ASF). Nous procédons actuellement au déplacement de la fonctionnalité ASF vers d’autres parties de la pile de filtrage. Nous vous recommandons de **désactiver** les paramètres ASF actuellement disponibles dans les stratégies anti-courrier indésirable. Pour plus d’informations, voir [Options avancées de filtrage du courrier indésirable](advanced-spam-filtering-asf-options.md).

## <a name="solutions-for-too-much-spam"></a>Solutions dans le cas d’un nombre important de courrier indésirable

Afin de rendre le filtrage anti-courrier indésirable le plus efficace possible, un administrateur doit configurer certains paramètres dans l’organisation. Si vous n’êtes pas un administrateur, veuillez vous rendre directement à la section utilisateur.

### <a name="for-admins"></a>Pour les administrateurs

- **Pointez l’enregistrement MX de votre domaine de messagerie vers Office 365** : pour que Office 365 offre une protection, l’enregistrement MX de tous les domaines de courrier Office 365 doit pointer vers Office 365 uniquement (autrement dit, la messagerie électronique pour les destinataires de ces domaines est continuellement livrée en premier sur Office 365). Si l’enregistrement MX pointe vers un autre emplacement (par exemple, une solution ou un appareil anti-courrier indésirable tiers), Office 365 ne peut pas fournir de filtrage anti-courrier indésirable à vos utilisateurs. Dans ce scénario, créez une règle de flux de courrier qui ignore le filtrage de courrier indésirable pour tous les messages (attribuez la valeur -1 à la valeur SCL de tous les messages entrants). Si vous décidez par la suite de pointer votre enregistrement MX vers Office 365 en premier, n’oubliez pas de supprimer la règle.

- **Activer le complément Signaler un message pour les utilisateurs** : nous vous recommandons vivement d’activer le complément Signaler un message pour vos utilisateurs. Consultez [Activer le complément Signaler un message](enable-the-report-message-add-in.md)pour obtenir des instructions.

- **Utiliser l’explorateur de soumissions** : les administrateurs peuvent désormais envoyer des courriers électroniques à des fins d’analyse par Microsoft. Vous pouvez également voir, en tant qu’administrateur, les commentaires envoyés par vos utilisateurs. Vous pouvez utiliser les modèles de leurs états de faux positif pour ajuster vos paramètres de filtrage du courrier indésirable. Pour plus d’informations, voir [Envoyer, pour analyse, des fichiers et URL suspectés d’être indésirables ou de l’hameçonnage à Microsoft pour Office 365](admin-submission.md).

- **Vérifiez que vos utilisateurs se trouvent dans les limites autorisées** tel que décrit dans les [Limites de réception et d’envoi](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits) de la description de service Exchange Online.

- **Vérifiez les niveaux de BCL dans vos stratégies anti-courrier indésirable** tel que décrit plus haut dans cette rubrique.

### <a name="for-users"></a>Pour les utilisateurs

- **Ajoutez l’expéditeur à votre liste d’expéditeurs approuvés** dans [Outlook](https://support.office.com/article/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089) ou [Outlook sur le web](https://support.office.com/article/db786e79-54e2-40cc-904f-d89d57b7f41d).

  Office 365 utilise votre liste d’expéditeurs approuvés et la liste des destinataires approuvés, mais ne tient pas compte de votre liste de domaines sécurisés. Ceci s’applique, quelle que soit la façon dont vous ajoutez le domaine à la liste (dans Outlook, Outlook sur le web ou dans Outlook, puis synchronisé via la synchronisation d’annuaires).

- **Désactiver le filtrage SmartScreen dans Outlook** : pour les anciens clients de bureau Outlook, n’activez pas le filtrage SmartScreen dans vos **Options de courrier indésirable**. Les mises à jour de filtrage SmartScreen ont pris fin en novembre 2016. Si vous activez la protection contre le courrier indésirable en mode **Faible** ou **Élevé** dans Outlook, vous utilisez le filtrage SmartScreen et vous pouvez obtenir des faux positifs. Veuillez noter que le filtrage SmartScreen n’est pas disponible pour les clients du nouveau bureau d’Outlook. Pour plus d’informations, voir l’[Arrêt de la prise en charge de SmartScreen dans Outlook et Exchange](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/Deprecating-support-for-SmartScreen-in-Outlook-and-Exchange/ba-p/605332).

## <a name="troubleshooting-a-message-is-delivered-to-the-junk-email-folder-after-passing-anti-spam-filtering"></a>Résolution des problèmes : un message est remis dans le dossier courrier indésirable suite à l’exécution du filtrage anti-courrier indésirable

Si un utilisateur a sélectionné l’option **Listes approuvées uniquement** dans ses options de courrier indésirable d’Outlook, tous les messages provenant de personnes qui ne figurent pas dans sa liste d’expéditeurs approuvés ou de la liste des destinataires approuvés sont envoyés vers son **dossier de courrier indésirable**, même si l’e-mail a passé avec succès le filtrage anti-courrier indésirable de votre organisation ou si une règle de flux de courrier n’a pas marqué le message comme courrier indésirable (valeur SCL de -1).

Dans Outlook sur le web, un conseil de sécurité de couleur jaune s’affiche, indiquant au destinataire que le message se trouve dans le dossier **Courrier indésirable** car l’expéditeur ne fait pas partie de la liste des expéditeurs approuvés ou la liste des destinataires approuvés.

L’en-tête de l’e-mail inclut la valeur **X-Forefront-Antispam-Report** du champ d’en-tête, soit `SFV:SKN` (le courrier n’a pas été marqué comme courrier indésirable avant d’être traité par le filtre anti-courrier indésirable) ou `SFV:NSPM` (le filtre anti-courrier indésirable a déterminé que l’e-mail n’était pas indésirable), mais le courrier est toutefois envoyé vers le dossier de **courrier indésirable** de l’utilisateur.

Aucun élément dans l’en-tête d’e-mail indique que le courrier est indésirable en raison du paramètre **Listes approuvées de l’utilisateur uniquement**. En revanche, vous pouvez utiliser le cmdlet **Get-MailboxJunkEmailConfiguration** dans Exchange Online PowerShell pour déterminer si un utilisateur autorise seulement la remise de courriers provenant d’expéditeurs approuvés dans sa boîte de réception.

Remplacez \<MailboxIdentity\> par le nom, l’alias ou l’adresse d’e-mail de la boîte aux lettres, puis exécutez la commande suivante dans [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) :

```PowerShell
Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List TrustedListsOnly,ContactsTrusted,TrustedSendersAndDomains
```

- Si la valeur de la propriété *TrustedListsOnly*est `True` : les messages qui ne proviennent pas d’expéditeurs ou de destinataires approuvés (c’est-à-dire, les personnes ne figurant pas dans la liste des expéditeurs approuvés de l’utilisateur et la liste des destinataires approuvés) seront envoyés vers leur dossier de **Courrier indésirable**.

- Si la valeur de la propriété *ContactsTrusted* est `True` : les contacts de l’utilisateur sont également identifiés comme expéditeurs approuvés. Si la valeur de la propriété *TrustedListsOnly*est `True` : les courriers qui ne proviennent pas d’expéditeurs ou de destinataires approuvés ou des Contacts seront envoyés vers leur dossier de **Courrier indésirable**.

- La valeur de la propriété *TrustedSendersAndDomains* répertorie le contenu de la liste des expéditeurs approuvés de l’utilisateur.

Pour modifier ces paramètres dans la boîte aux lettres, remplacez \<MailboxIdentity\> par le nom, l’alias ou l’adresse de courrier de la boîte aux lettres, puis exécutez la commande suivante :

```PowerShell
Set-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" -TrustedListsOnly $false -ContactsTrusted $false
```

Pour obtenir des informations détaillées sur la syntaxe, les paramètres et les autorisations requises, voir les rubriques [Get-MailboxJunkEmailConfiguration](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/get-mailboxjunkemailconfiguration) et [Set-MailboxJunkEmailConfiguration](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/set-mailboxjunkemailconfiguration).

## <a name="directory-synchronization-for-standalone-eop-customers"></a>Synchronisation d’annuaires pour les clients EOP autonomes

Si vous utilisez la fonction EOP autonome pour protéger votre organisation Exchange locale, vous devez synchroniser les paramètres d’utilisateur avec le service à l’aide de la synchronisation d’annuaires. Ainsi, vos listes d’expéditeurs approuvés par les utilisateurs sont respectées par EOP. Pour plus d’informations, voir [Utilisation de la synchronisation d’annuaires pour gérer les utilisateurs de messagerie](manage-mail-users-in-eop.md#use-directory-synchronization-to-manage-mail-users).
