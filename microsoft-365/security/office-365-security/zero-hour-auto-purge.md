---
title: 'Purge automatique zéro heure : protection contre le courrier indésirable et les programmes malveillants'
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 96deb75f-64e8-4c10-b570-84c99c674e15
ms.collection:
- M365-security-compliance
description: La suppression automatique de zéro heure (ZAP) est une fonctionnalité de protection de la messagerie qui détecte les messages contenant du courrier indésirable ou des programmes malveillants qui ont déjà été remis dans la boîte de réception de vos utilisateurs, puis rend le contenu malveillant inoffensif. Le mode de fonctionnement de ZAP dépend du type de contenu malveillant détecté.
ms.openlocfilehash: dd702e88dc2400367330d9cb1b54b5b0017334e4
ms.sourcegitcommit: caa3f681a68daf5e463093a922c3d6f378143d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "39191229"
---
# <a name="zero-hour-auto-purge---protection-against-spam-and-malware"></a>Purge automatique zéro heure : protection contre le courrier indésirable et les programmes malveillants

## <a name="overview"></a>Vue d'ensemble

La suppression automatique de zéro heure (ZAP) est une fonctionnalité de protection de la messagerie qui détecte les messages contenant des messages hameçons, des courriers indésirables ou des programmes malveillants qui ont déjà été remis dans la boîte de réception de vos utilisateurs, puis rend le contenu malveillant inoffensif. Le mode de fonctionnement de ZAP dépend du type de contenu malveillant détecté. Les messages peuvent être zapped en raison du contenu, des URL ou des pièces jointes du courrier.
  
ZAP est disponible avec la protection Exchange Online par défaut incluse avec tout abonnement Office 365 qui contient des boîtes aux lettres Exchange Online.

## <a name="how-zap-works"></a>Fonctionnement de l’ZAP

Office 365 met à jour quotidiennement les signatures du moteur de blocage du courrier indésirable et des programmes malveillants en temps réel. Toutefois, vos utilisateurs peuvent toujours recevoir des messages malveillants dans leur boîte de réception pour diverses raisons, notamment si le contenu est arme après remise aux utilisateurs. ZAP les résout en surveillant en continu les mises à jour des signatures Office 365 courrier indésirable et anti-programme malveillant. ZAP peut rechercher et supprimer les messages précédemment remis qui se trouvent déjà dans les boîtes de réception des utilisateurs.

L’action ZAP est transparente pour l’utilisateur de boîte aux lettres ; elles ne sont pas notifiées en cas de déplacement d’un message électronique. Le message ne doit pas être âgé de plus de 2 jours.
  
Les listes d’autorisation, les [règles de flux de messagerie](https://go.microsoft.com/fwlink/p/?LinkId=722755) (également appelées règles de transport) et les règles d’utilisateur final ou les filtres supplémentaires prévalent sur zap.

### <a name="malware-zap"></a>Programme malveillant ZAP

Pour les programmes malveillants nouvellement détectés, ZAP supprime les pièces jointes des messages électroniques, en laissant le corps du message dans la boîte aux lettres de l’utilisateur. Les pièces jointes sont supprimées, quel que soit l’état de lecture du message.

Le logiciel malveillant ZAP est activé par défaut dans la stratégie de programmes malveillants. Vous pouvez désactiver le programme malveillant ZAP à l’aide du paramètre *ZapEnabled* sur la cmdlet [Set-MalwareFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/set-malwarefilterpolicy) dans Exchange Online PowerShell ou Exchange Online Protection PowerShell. Le logiciel malveillant ZAP peut également être activé ou désactivé en modifiant la stratégie de programmes malveillants dans le centre de sécurité et de conformité.

### <a name="phish-zap"></a>Hameçon ZAP

Pour les messages identifiés comme hameçons après la remise, ZAP entreprend une action en fonction de la stratégie de courrier indésirable qui couvre un utilisateur spécifique, quel que soit l’état de lecture du message. Si l’action de hameçonnage de la stratégie est définie sur *ne pas* agir (ajouter un en-tête X, modifier l’objet, aucune action), ZAP n’effectuera aucune action sur le courrier. Si l’action de hameçonnage est définie sur déplacer vers le courrier indésirable, ZAP déplace le message vers le dossier courrier indésirable de la boîte de réception de l’utilisateur. **Pour toute autre action de hameçonnage (redirection, suppression, mise en quarantaine) zap déplace le message vers la quarantaine d’hameçons**. Lisez ci-dessous les conditions requises et exclusions de configuration. En savoir plus sur la [configuration de vos stratégies de filtrage du courrier indésirable](https://docs.microsoft.com//office365/securitycompliance/configure-your-spam-filter-policies) ici.  

Le blocage du hameçonnage est activé par défaut dans la stratégie de courrier indésirable. Le paramètre de hameçonnage ZAP peut être désactivé à l’aide du paramètre *PhishZapEnabled* de [Set-HostedContentFilterPolicy](https://go.microsoft.com/fwlink/p/?LinkId=722758), une cmdlet EOP.

### <a name="spam-zap"></a>Blocage du courrier indésirable

Pour les messages identifiés comme courrier indésirable après la remise, ZAP entreprend une action en fonction de la stratégie de courrier indésirable qui couvre l’utilisateur spécifique, uniquement si le message n’est pas lu.  Si l’action de courrier indésirable de la stratégie est définie sur ne pas agir (ajouter un en-tête X, modifier l’objet, aucune action), la fonction ZAP n’effectuera aucune action sur le courrier. Si l’action de courrier indésirable est définie sur déplacer vers le courrier indésirable, ZAP déplace le message vers le dossier courrier indésirable de la boîte de réception de l’utilisateur. **Pour toute autre action de courrier indésirable (redirection, suppression, mise en quarantaine) zap déplace le message vers la mise en quarantaine du courrier indésirable**. Lisez ci-dessous les conditions requises et exclusions de configuration. En savoir plus sur la [configuration de vos stratégies de filtrage du courrier indésirable](https://docs.microsoft.com//office365/securitycompliance/configure-your-spam-filter-policies) ici.

Le courrier indésirable ZAP est activé par défaut dans la stratégie de courrier indésirable. Vous pouvez désactiver le blocage du courrier indésirable à l’aide du paramètre *SpamZapEnabled* de l’applet de commande [Set-HostedContentFilterPolicy](https://go.microsoft.com/fwlink/p/?LinkId=722758) dans Exchange Online PowerShell ou Exchange Online Protection PowerShell.

###<a name="phish-and-spam-zap-requirements-exclusions-and-notices"></a>Exigences, exclusions et notifications pour le hameçonnage et le courrier indésirable

> [!IMPORTANT]
> le paramètre précédent de l’applet de commande *ZapEnabled* qui a contrôlé à la fois le hameçonnage et le blocage du courrier indésirable est **déconseillé le 1er février 2020**. Si vous avez écrit des scripts qui utilisent le paramètre ZapEnabled, nous vous recommandons de les mettre à jour afin d’utiliser SpamZapEnabled et PhishZapEnabled. Pendant la période de transition, tous les 3 paramètres (ZapEnabled, PhishZapEnabled et SpamZapEnabled) seront disponibles via l’applet de commande. Tant qu’il n’est pas explicitement défini via l’interface utilisateur ou PowerShell, PhishZapEnabled et SpamZapEnabled affichent une valeur héritée du paramètre ZapEnabled. Une fois les nouveaux paramètres définis, ils n’héritent plus du paramètre ZapEnabled. Une fois déconseillée, le paramètre ZapEnabled n’a aucun effet sur les propriétés PhishZapEnabled ou SpamZapEnabled et ZapEnabled sera supprimé de la liste des paramètres dans cmdlets.

ZAP ne déplace aucun message en quarantaine qui est en cours d’analyse de remise dynamique, ou qui a déjà un verdict de programme malveillant avec une pièce jointe remplacée. Si un signal de courrier indésirable ou de courrier indésirable est reçu pour ces types de messages et que la stratégie de courrier indésirable/hameçon est configurée pour entreprendre une action (déplacer vers le courrier indésirable, rediriger, supprimer, mettre en quarantaine), l’option ZAP sera par défaut une action « déplacer vers le courrier indésirable ». Pour que ZAP prenne une action « déplacer vers le courrier indésirable » sur un message, la protection contre le courrier indésirable doit être activée pour l’utilisateur, avec les paramètres de courrier indésirable par défaut. (Pour plus d’informations sur les options utilisateur dans Outlook, consultez [la rubrique modifier le niveau de protection dans le filtre courrier indésirable](https://support.office.com/article/e89c12d8-9d61-4320-8c57-d982c8d52f6b) .)

## <a name="how-to-see-if-zap-moved-your-message"></a>Comment savoir si la méthode ZAP a déplacé votre message

Pour déterminer si l’élément ZAP a déplacé votre message, vous pouvez utiliser le [rapport d’état de protection contre les menaces](../../compliance/view-email-security-reports.md#threat-protection-status-report) ou l' [Explorateur de menaces (et les détections en temps réel)](threat-explorer.md).

## <a name="disable-zap"></a>Désactiver ZAP

Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554). Pour vous connecter à Exchange Online Protection PowerShell, consultez la rubrique [Connect to Exchange Online Protection PowerShell](https://go.microsoft.com/fwlink/p/?linkid=627290).

### <a name="disable-malware-zap"></a>Désactiver le programme malveillant ZAP * *

Les programmes malveillants ZAP peuvent être désactivés via le paramètre *ZapEnabled* sur la cmdlet [Set-MalwareFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/set-malwarefilterpolicy) dans Exchange Online PowerShell ou Exchange Online Protection PowerShell. Le logiciel malveillant ZAP peut également être activé ou désactivé en modifiant la stratégie de programmes malveillants dans le centre de sécurité et de conformité.
 
Cet exemple montre comment désactiver ZAP dans la stratégie de filtrage des programmes malveillants nommée « test ».
 
```Powershell
Set-MalwareFilterPolicy -Identity Test -ZapEnabled $false
```
 
Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-MalwareFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/set-malwarefilterpolicy).

### <a name="disable-phish-zap-and-spam-zap"></a>Désactiver le hameçonnage ZAP et le blocage du courrier indésirable

Pour désactiver le hameçonnage et le courrier indésirable pour votre client O365, ou un ensemble d’utilisateurs, utilisez les paramètres *PhishZapEnabled* et *SpamZapEnabled* de [Set-HostedContentFilterPolicy](https://go.microsoft.com/fwlink/p/?LinkId=722758), une cmdlet EOP.

Dans l’exemple suivant, les messages hameçons et de courrier indésirable sont désactivés pour une stratégie de filtrage de contenu nommée « test ».

```Powershell
Set-HostedContentFilterPolicy -Identity Test -PhishZapEnabled $false -SpamZapEnabled $false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-HostedContentFilterPolicy](https://go.microsoft.com/fwlink/p/?LinkId=722758).

## <a name="faq"></a>Forum aux questions

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-mail-folder"></a>Que se passe-t-il si un message légitime est déplacé vers le dossier courrier indésirable ?
  
Vous devez suivre le processus de création de rapports normal pour les [faux positifs](../../compliance/prevent-email-from-being-marked-as-spam.md). La seule raison pour laquelle le message est déplacé de la boîte de réception vers le dossier de courrier indésirable est que le service a déterminé que le message était du courrier indésirable ou malveillant.
  
### <a name="what-if-i-use-the-office-365-quarantine-instead-of-the-junk-mail-folder"></a>Que faire en cas d’utilisation de la mise en quarantaine Office 365 au lieu du dossier courrier indésirable ?
  
ZAP entreprend une action en fonction de la configuration des paramètres d’action de courrier indésirable et de courrier indésirable dans votre stratégie de blocage du courrier indésirable. Pour plus d’informations sur les programmes malveillants, le hameçonnage et le courrier indésirable, voir ci-dessus.
  
### <a name="what-if-i-have-a-custom-mail-flow-rule-block-allow-rule"></a>Que se passe-t-il si j’utilise une règle de flux de messagerie personnalisée (règle bloquer/autoriser) ?
  
Les règles créées par les administrateurs (règles de flux de messagerie) ou les règles de blocage et d’autorisation sont prioritaires. Ces messages sont exclus des critères de fonctionnalité de sorte que le flux de messagerie suit l’action de la règle (règle bloquer/autoriser).

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rule"></a>Que se passe-t-il si un message est déplacé vers un autre dossier (par exemple, la règle de boîte de réception) ?

ZAP fonctionne toujours dans ce cas, sauf si le message a été supprimé ou se trouve dans un courrier indésirable.

## <a name="related-topics"></a>Rubriques connexes

[Protection contre le courrier indésirable pour Office 365](anti-spam-protection.md)
  
[Bloquer le courrier indésirable à l'aide du filtre d'Office 365 afin d'éviter les problèmes de faux négatifs](reduce-spam-email.md)
