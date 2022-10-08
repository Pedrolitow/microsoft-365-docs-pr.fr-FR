---
title: Aperçu de l'intelligence artificielle
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 978c3173-3578-4286-aaf4-8a10951978bf
ms.collection:
- m365-security
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur l’information sur l’usurpation d’identité dans Exchange Online Protection (EOP).
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 3846db81cf6378e7e1bb5570927f452068ee2431
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68048613"
---
# <a name="spoof-intelligence-insight-in-eop"></a>Informations sur l’intelligence d’usurpation d’identité dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, les messages électroniques entrants sont automatiquement protégés contre l’usurpation d’identité. EOP utilise **le renseignement sur l’usurpation** d’identité dans le cadre de la défense globale de votre organisation contre le hameçonnage. Pour plus d’informations, consultez [la protection contre l’usurpation d’identité dans EOP](anti-spoofing-protection.md).

Lorsqu’un expéditeur usurpe une adresse e-mail, il semble qu’il s’agit d’un utilisateur dans l’un des domaines de votre organisation ou d’un utilisateur d’un domaine externe qui envoie des e-mails à votre organisation. Les attaquants qui usurpent les expéditeurs pour envoyer du courrier indésirable ou de hameçonnage doivent être bloqués. Toutefois, dans certains scénarios, les expéditeurs légitimes s’usurpent. Par exemple :

- Scénarios légitimes pour usurper des domaines internes :
  - Les expéditeurs tiers utilisent votre domaine pour envoyer des messages en bloc à vos propres employés pour les sondages d’entreprise.
  - Une entreprise externe génère et envoie des mises à jour de publicités ou de produits en votre nom.
  - Un assistant doit envoyer régulièrement un e-mail à une autre personne au sein de votre organisation.
  - Une application interne envoie des notifications par e-mail.

- Scénarios légitimes pour usurper des domaines externes :
  - L’expéditeur se trouve sur une liste de diffusion (également appelée liste de discussion) et la liste de diffusion transmet l’e-mail de l’expéditeur d’origine à tous les participants de la liste de diffusion.
  - Une entreprise externe envoie un e-mail au nom d’une autre entreprise (par exemple, un rapport automatisé ou une société de logiciel en tant que service).

Vous pouvez utiliser **l’information sur l’usurpation d’identité** dans le portail Microsoft 365 Defender pour identifier rapidement les expéditeurs usurpés qui vous envoient légitimement des e-mails non authentifiés (messages provenant de domaines qui ne passent pas les vérifications SPF, DKIM ou DMARC) et autoriser manuellement ces expéditeurs.

En permettant aux expéditeurs connus d’envoyer des messages usurpés à partir d’emplacements connus, vous pouvez réduire les faux positifs (bon e-mail marqué comme incorrect). En surveillant les expéditeurs d’usurpation d’identité autorisés, vous fournissez une couche de sécurité supplémentaire pour empêcher l’arrivée de messages non sécurisés dans votre organisation.

De même, vous pouvez examiner les expéditeurs usurpés qui ont été autorisés par le renseignement sur l’usurpation d’identité et bloquer manuellement ces expéditeurs de l’insight d’intelligence d’usurpation d’identité.

Le reste de cet article explique comment utiliser les informations d’usurpation d’identité dans le portail Microsoft 365 Defender et dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans Exchange Online  boîtes aux lettres).

> [!NOTE]
>
> - Seuls les expéditeurs usurpés qui ont été détectés par le renseignement sur l’usurpation d’identité apparaissent dans l’insight sur l’usurpation d’identité. Lorsque vous remplacez le verdict d’autorisation ou de blocage dans l’insight, l’expéditeur usurpé devient une entrée d’autorisation ou de blocage manuelle qui apparaît uniquement sous l’onglet **Expéditeurs usurpés** dans la liste d’autorisation/de blocage du locataire. Vous pouvez également créer manuellement des entrées d’autorisation ou de blocage pour les expéditeurs usurpés avant qu’elles ne soient détectées par l’intelligence de l’usurpation d’identité. Pour plus d’informations, voir [Gérer liste rouge/verte du client dans EOP](manage-tenant-allow-block-list.md).
>
> - L’information sur l’usurpation d’identité et l’onglet **Expéditeurs usurpés** dans la liste Autoriser/Bloquer du locataire remplacent les fonctionnalités de la stratégie de renseignement sur l’usurpation d’identité qui était disponible sur la page de stratégie anti-courrier indésirable dans le Centre de sécurité & conformité.
>
> - L’information sur l’usurpation d’identité affiche 7 jours de données. **L’applet de commande Get-SpoofIntelligenceInsight** affiche 30 jours de données.
>
> - Les dernières données disponibles datent de 3 à 4 jours.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à l’onglet **Expéditeurs usurpés** sur la page **Autoriser/Bloquer la liste** des locataires, utilisez <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>. Pour accéder directement à la page **Informations sur l’usurpation d’identité** , utilisez <https://security.microsoft.com/spoofintelligence>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour modifier la stratégie d’usurpation d’identité ou activer ou désactiver l’usurpation d’identité, vous devez être membre de l’un des groupes de rôles suivants :
    - **Gestion de l'organisation**
    - **Administrateur de sécurité** <u>et</u> **configuration en mode seul** ou gestion de l’organisation **en mode affichage uniquement**.
  - Pour accéder en lecture seule à la stratégie de renseignement sur l’usurpation d’identité, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Adding users to the corresponding Azure Active Directory role in the Microsoft 365 admin center gives users the required permissions _and_ permissions for other features in Microsoft 365. For more information, see [About admin roles](../../admin/add-users/about-admin-roles.md).
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Vous activez et désactivez l’usurpation d’identité dans les stratégies anti-hameçonnage dans EOP et Microsoft Defender pour Office 365. L’intelligence par usurpation d’identité est activée par défaut. Pour plus d’informations, consultez [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md) ou [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

- Pour connaître les paramètres recommandés pour l’intelligence par usurpation d’identité, consultez [les paramètres de stratégie anti-hameçonnage EOP](recommended-settings-for-eop-and-office365-atp.md#eop-anti-phishing-policy-settings).

## <a name="open-the-spoof-intelligence-insight-in-the-microsoft-365-defender-portal"></a>Ouvrez l’information sur l’usurpation d’identité dans le portail Microsoft 365 Defender

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & les stratégies de **menaces** \> **de règles** \> **dans** la section **Règles**. Pour accéder directement à l’onglet **Expéditeurs usurpés** sur la page **Autoriser/Bloquer la liste** des locataires, utilisez <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>.

2. Dans la page **Autoriser/Bloquer des listes de locataires** , l’insight d’intelligence de l’usurpation d’identité se présente comme suit :

   :::image type="content" source="../../media/m365-sc-spoof-intelligence-insight.png" alt-text="Informations sur l’usurpation d’identité dans la page de stratégie anti-hameçonnage" lightbox="../../media/m365-sc-spoof-intelligence-insight.png":::

   L’insight a deux modes :

   - **Mode Insight** : si l’intelligence par usurpation d’identité est activée, l’insight vous indique le nombre de messages détectés par l’intelligence par usurpation d’identité au cours des sept derniers jours.
   - **Que se passe-t-il si le mode** : si l’intelligence par usurpation d’identité est désactivée, l’insight vous indique le nombre de messages qui *auraient* été détectés par l’intelligence par usurpation d’identité au cours des sept derniers jours.

Pour afficher des informations sur les détections d’usurpation d’identité, cliquez sur **Afficher l’activité d’usurpation** d’identité dans l’insight sur l’usurpation d’identité.

### <a name="view-information-about-spoofed-messages"></a>Afficher des informations sur les messages usurpés

> [!NOTE]
> N’oubliez pas que seuls les expéditeurs usurpés qui ont été détectés par l’usurpation d’identité apparaissent sur cette page. Lorsque vous remplacez le verdict d’autorisation ou de blocage dans l’insight, l’expéditeur usurpé devient une entrée d’autorisation ou de blocage manuelle qui apparaît uniquement sous l’onglet **Expéditeurs usurpés** dans la liste d’autorisation/de blocage du locataire.

Dans la page **Informations sur l’usurpation d’identité** qui s’affiche après avoir cliqué sur **Afficher l’activité d’usurpation** d’identité dans l’insight d’usurpation d’identité, la page contient les informations suivantes :

- **Utilisateur usurpé** : **domaine** de l’utilisateur usurpé qui s’affiche dans la zone **From** dans les clients de messagerie. L’adresse From est également appelée adresse `5322.From` .
- **Infrastructure d’envoi** : également appelée _infrastructure_. L’infrastructure d’envoi sera l’une des valeurs suivantes :
  - Domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source.
  - Si l’adresse IP source n’a pas d’enregistrement PTR, l’infrastructure d’envoi est identifiée comme \<source IP\>/24 (par exemple, 192.168.100.100/24).
  - Domaine DKIM vérifié.
- **Nombre** de messages : nombre de messages provenant de la combinaison du domaine usurpé _et_ de l’infrastructure d’envoi à votre organisation au cours des 7 derniers jours.
- **Dernière vue** : dernière date à laquelle un message a été reçu de l’infrastructure d’envoi qui contient le domaine usurpé.
- **Type d’usurpation** d’identité : l’une des valeurs suivantes :
  - **Interne** : l’expéditeur usurpé se trouve dans un domaine qui appartient à votre organisation ( [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
  - **Externe** : l’expéditeur usurpé se trouve dans un domaine externe.
- **Action** : cette valeur est **autorisée** ou **bloquée** :
  - **Autorisé** : L’authentification par e-mail explicite du domaine a échoué vérifie [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) et [DMARC](use-dmarc-to-validate-email.md). Toutefois, le domaine a passé nos vérifications d’authentification par e-mail implicites ([authentification composite](email-validation-and-authentication.md#composite-authentication)). Par conséquent, aucune action anti-usurpation d’identité n’a été effectuée sur le message.
  - **Bloqué** : les messages de la combinaison du domaine usurpé _et_ de l’infrastructure d’envoi sont marqués comme incorrects par l’intelligence par usurpation d’identité. L’action effectuée sur les messages usurpés est contrôlée par la stratégie anti-hameçonnage par défaut ou les stratégies anti-hameçonnage personnalisées (la valeur par défaut est **Déplacer le message vers le dossier Courrier indésirable Email**). Pour plus d’informations, consultez [Paramètres exclusifs des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

Vous pouvez cliquer sur les en-têtes de colonne sélectionnés pour trier les résultats.

Pour filtrer les résultats, vous disposez des options suivantes :

- Cliquez sur le bouton **Filtrer** . Dans le menu volant **Filtre** qui s’affiche, vous pouvez filtrer les résultats en procédant comme suit :
  - **Type d’usurpation d’identité**
  - **Action**
- Utilisez la zone **de recherche** pour entrer une liste séparée par des virgules de valeurs de domaine usurpées ou envoyer des valeurs d’infrastructure pour filtrer les résultats.

### <a name="view-details-about-spoofed-messages"></a>Afficher les détails sur les messages usurpés

Lorsque vous sélectionnez une entrée dans la liste, un menu volant de détails s’affiche qui contient les informations et fonctionnalités suivantes :

- **Autoriser l’usurpation** d’identité ou **bloquer l’usurpation** d’identité : sélectionnez l’une de ces valeurs pour remplacer le verdict d’intelligence de l’usurpation d’identité d’origine et déplacer l’entrée de l’information sur l’usurpation d’identité vers la liste d’autorisation/de blocage du locataire en tant qu’entrée d’autorisation ou de blocage pour l’usurpation d’identité.
- Pourquoi on a pris ça.
- Ce que vous devez faire.
- Résumé de domaine qui inclut la plupart des mêmes informations de la page principale de renseignements sur l’usurpation d’identité.
- Données WhoIs sur l’expéditeur.
- Lien permettant d’ouvrir [l’Explorateur de menaces](threat-explorer.md) pour afficher des détails supplémentaires sur l’expéditeur sous **Afficher** \> **le hameçonnage** dans Microsoft Defender pour Office 365.
- Messages similaires que nous avons vus dans votre locataire à partir du même expéditeur.

### <a name="about-allowed-spoofed-senders"></a>À propos des expéditeurs usurpés autorisés

Un expéditeur d’usurpation d’identité autorisé dans l’insight d’intelligence de l’usurpation d’identité ou un expéditeur d’usurpation d’identité bloqué que vous avez modifié manuellement **pour autoriser l’usurpation d’identité** autorise uniquement les messages provenant de la combinaison du domaine usurpé _et_ de l’infrastructure d’envoi. Il n’autorise pas les e-mails provenant du domaine usurpé d’identité à partir d’une source quelconque, ni les e-mails provenant de l’infrastructure d’envoi pour n’importe quel domaine.

Par exemple, l’expéditeur usurpé d’identité suivant est autorisé à usurper l’identité :

- **Domaine** : gmail.com
- **Infrastructure** : tms.mx.com

Seuls les e-mails provenant de cette paire d’infrastructure domaine/envoi sont autorisés à usurper l’identité. Les autres expéditeurs qui tentent d’usurper gmail.com ne sont pas automatiquement autorisés. Les messages des expéditeurs d’autres domaines qui proviennent de tms.mx.com sont toujours vérifiés par l’usurpation d’identité et peuvent être bloqués.

## <a name="use-the-spoof-intelligence-insight-in-exchange-online-powershell-or-standalone-eop-powershell"></a>Utiliser l’insight d’intelligence d’usurpation d’identité dans Exchange Online PowerShell ou PowerShell EOP autonome

Dans PowerShell, vous utilisez l’applet de commande **Get-SpoofIntelligenceInsight** pour **afficher** les expéditeurs autorisés et bloqués qui ont été détectés par l’intelligence par usurpation d’identité. Pour autoriser ou bloquer manuellement les expéditeurs usurpés, vous devez utiliser l’applet de commande **New-TenantAllowBlockListSpoofItems** . Pour plus d’informations, consultez [Utiliser PowerShell pour gérer les entrées d’expéditeur usurpées dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md).

Pour afficher les informations dans l’insight sur l’usurpation d’identité, exécutez la commande suivante :

```powershell
Get-SpoofIntelligenceInsight
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Get-SpoofIntelligenceInsight](/powershell/module/exchange/get-spoofintelligenceinsight).

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Autres façons de gérer l’usurpation d’identité et le hameçonnage

Soyez diligent à l’égard de l’usurpation d’identité et de la protection contre le hameçonnage. Voici des moyens connexes de vérifier les expéditeurs qui usurpent votre domaine et de les empêcher d’endommager votre organisation :

- Vérifiez le **rapport de courrier d’usurpation** d’identité. Vous pouvez souvent utiliser ce rapport pour afficher et aider à gérer les expéditeurs usurpés. Pour plus d’informations, consultez le [rapport détections d’usurpation](view-email-security-reports.md#spoof-detections-report) d’identité.

- Passez en revue la configuration de votre infrastructure de stratégie d’expéditeur (SPF). Pour consulter une brève présentation de SPF et le configurer rapidement, voir [Configurer SPF dans Microsoft 365 pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Pour consulter des informations plus approfondies sur l’utilisation de SPF par Office 365, la résolution des problèmes et les déploiements non standard tels que les déploiements hybrides, voir Comment Office 365 utilise SPF (Sender Policy Framework) pour empêcher l’usurpation d’identité.

- Passez en revue votre configuration DKIM (DomainKeys Identified Mail). Vous devez utiliser DKIM en plus de SPF et DMARC pour empêcher les attaquants d’envoyer des messages qui semblent provenir de votre domaine. DKIM vous permet d'ajouter une signature numérique aux messages électroniques dans l'en-tête du message. Pour plus d’informations, consultez [Utiliser DKIM pour valider les e-mails sortants envoyés à partir de votre domaine personnalisé dans Office 365](use-dkim-to-validate-outbound-email.md).

- Passez en revue votre configuration DMARC (Domain-based Message Authentication, Reporting, and Conformance). L’implémentation de DMARC avec SPF et DKIM fournit une protection supplémentaire contre l’usurpation et les courriers de hameçonnage. DMARC permet aux systèmes de messagerie de réception de déterminer ce qu’ils doivent faire des messages envoyés à partir de votre domaine qui sont rejetés par les contrôles de SPF ou de DKIM. Pour plus d’informations, consultez [Utiliser DMARC pour valider l’e-mail dans Office 365](use-dmarc-to-validate-email.md).
