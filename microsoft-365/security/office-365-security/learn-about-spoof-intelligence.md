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
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 978c3173-3578-4286-aaf4-8a10951978bf
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les informations sur l’usurpation d’Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 45ecbe68072441b40477d1b27953b957aeffa9e3
ms.sourcegitcommit: f3d1009840513703c38bab99a6e13a3656eae5ee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2021
ms.locfileid: "52793171"
---
# <a name="spoof-intelligence-insight-in-eop"></a>Informations sur l’usurpation d’intelligence dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et ne sont pas disponibles dans toutes les organisations. Si votre organisation ne dispose pas des fonctionnalités décrites dans cet article, consultez l’ancienne expérience de gestion de l’usurpation d’adresse chez [Manage spoof senders using the spoof intelligence policy and spoof intelligence insight in EOP](walkthrough-spoof-intelligence-insight.md).

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, les messages électroniques entrants sont automatiquement protégés contre l’usurpation d’adresses. EOP utilise **la veille contre** l’usurpation d’adresse dans le cadre de la protection globale de votre organisation contre le hameçonnage. Pour plus d’informations, voir [Protection contre l’usurpation d’adresse dans EOP.](anti-spoofing-protection.md)

Lorsqu’un expéditeur usurpe une adresse de messagerie, il semble qu’il s’agit d’un utilisateur dans l’un des domaines de votre organisation ou d’un utilisateur d’un domaine externe qui envoie du courrier électronique à votre organisation. Les personnes malveillantes qui usurpent des expéditeurs pour envoyer du courrier indésirable ou du hameçonnage doivent être bloquées. Toutefois, il existe des scénarios où des expéditeurs légitimes usurpent l’adresse. Par exemple :

- Scénarios légitimes pour l’usurpation d’un domaine interne :
  - Les expéditeurs tiers utilisent votre domaine pour envoyer des messages en bloc à vos propres employés pour les sondages de l’entreprise.
  - Une société externe génère et envoie des mises à jour publicitaires ou des mises à jour de produit en votre nom.
  - Un assistant doit régulièrement envoyer des courriers électroniques à une autre personne au sein de votre organisation.
  - Une application interne envoie des notifications par courrier électronique.

- Scénarios légitimes d’usurpation de domaines externes :
  - L’expéditeur figure sur une liste de diffusion (également appelée liste de discussion) et la liste de diffusion relaie le courrier électronique de l’expéditeur d’origine à tous les participants de la liste de diffusion.
  - Une société externe envoie du courrier électronique pour le compte d’une autre société (par exemple, un rapport automatisé ou une société de logiciels en tant que service).

Vous pouvez  utiliser la veille contre l’usurpation d’identité dans le Centre de sécurité & conformité pour identifier rapidement les expéditeurs usurpés qui vous envoient légitimement des messages électroniques non authentifiés (messages provenant de domaines ne réussissant pas les vérifications SPF, DKIM ou DMARC) et autoriser manuellement ces expéditeurs.

En permettant aux expéditeurs connus d’envoyer des messages usurpés à partir d’emplacements connus, vous pouvez réduire les faux positifs (e-mail de qualité marqué comme faux). En surveillant les expéditeurs usurpés autorisés, vous fournissez une couche de sécurité supplémentaire pour empêcher les messages non sécurisés d’arriver dans votre organisation.

De même, vous pouvez examiner les expéditeurs usurpés qui ont été autorisés par la veille contre l’usurpation d’informations et bloquer manuellement ces expéditeurs à partir de la veille contre l’usurpation d’informations.

Le reste de cet article explique comment utiliser les informations sur l’usurpation d’informations dans le Centre de sécurité & conformité et dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres en Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online).

> [!NOTE]
>
> - Seuls les expéditeurs usurpés qui ont été détectés par la veille contre l’usurpation d’informations apparaissent dans l’aperçu de l’usurpation d’intelligence. Lorsque vous remplacez le verdict d’autoriser ou de bloquer dans l’insight, l’expéditeur  usurpé devient une entrée d’accès ou de blocage manuelle qui apparaît uniquement sous l’onglet Usurpation d’adresse dans la liste d’adresses client autoriser/bloquer. Vous pouvez également créer manuellement des entrées d’autoriser ou de bloquer des expéditeurs usurpés avant qu’ils ne soit détectés par la veille contre l’usurpation d’adresse. Pour plus d’informations, voir [Gérer liste rouge/verte du client dans EOP](tenant-allow-block-list.md).
>
> - Les informations sur l’usurpation d’informations et l’onglet Usurpation d’adresse dans la liste d’adresses client autoriser/bloquer remplacent la fonctionnalité de la stratégie de veille contre l’usurpation d’adresses qui était disponible sur la page de stratégie anti-courrier indésirable dans le Centre de sécurité & conformité. 
>
>- La veille contre l’usurpation d’informations indique 7 jours de données. La cmdlet **Get-SpoofIntelligenceInsight** affiche 30 jours de données.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour aller directement à la page **anti-hameçonnage,** utilisez <https://protection.office.com/antiphishing> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour modifier la stratégie de veille contre l’usurpation d’informations ou activer  ou  désactiver la veille contre l’usurpation d’informations, vous devez être membre des groupes de rôles Gestion de l’organisation ou Administrateur de la sécurité.
  - Pour accéder en lecture seule à la stratégie d’intelligence contre  l’usurpation d’informations, vous devez être membre des groupes de rôles Lecteur global ou Lecteur **de** sécurité.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Vous activez et désactivez la veille contre l’usurpation d’adresse dans les stratégies anti-hameçonnage dans EOP et Microsoft Defender pour Office 365. La veille contre l’usurpation d’informations est activée par défaut. Pour plus d’informations, voir [Configure anti-phishing policies in EOP](configure-anti-phishing-policies-eop.md) or [Configure anti-phishing policies in Microsoft Defender for Office 365](configure-atp-anti-phishing-policies.md).

- Pour obtenir nos paramètres recommandés pour la veille contre l’usurpation d’adresse, consultez les paramètres de stratégie [anti-hameçonnage EOP.](recommended-settings-for-eop-and-office365-atp.md#eop-anti-phishing-policy-settings)

## <a name="open-the-spoof-intelligence-insight-in-the-security--compliance-center"></a>Ouvrez les informations sur l’usurpation d'& conformité

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **Anti-phishing**.

2. Dans la **page principale anti-hameçonnage,** la veille contre l’usurpation d’informations a deux modes :

   - **Mode Insight**: si la veille contre l’usurpation d’informations est activée, l’aperçu vous montre le nombre de messages détectés par la veille contre l’usurpation d’informations au cours des sept derniers jours.
   - **Que se** passe-t-il si le mode : si la veille contre l’usurpation d’informations est désactivée, l’information vous indique le nombre de *messages* détectés par la veille contre l’usurpation d’informations au cours des sept derniers jours.

   Dans les deux cas, les domaines usurpés affichés dans l’aperçu sont séparés en deux **catégories** : domaines suspects et domaines **non suspects.**

   - **Les domaines suspects sont les suivants** :

     - Usurpation d’un niveau de confiance élevé : en fonction des modèles d’envoi historiques et du score de réputation des domaines, nous sommes très certains que les domaines sont usurpés et que les messages provenant de ces domaines sont plus susceptibles d’être malveillants.

     - Usurpation de confiance modérée : en fonction des modèles d’envoi historiques et du score de réputation des domaines, nous sommes modérément certains que les domaines sont usurpés et que les messages envoyés à partir de ces domaines sont légitimes. Les faux positifs sont plus probables dans cette catégorie que l’usurpation d’identité à haut niveau de confiance.

   **Domaines non suspects**: le domaine a échoué aux vérifications explicites de l’authentification de courrier électronique [SPF,](how-office-365-uses-spf-to-prevent-spoofing.md) [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC](use-dmarc-to-validate-email.md). Toutefois, le domaine a réussi nos vérifications d’authentification de messagerie implicites[(authentification composite).](email-validation-and-authentication.md#composite-authentication) Par conséquent, aucune action anti-usurpation n’a été prise sur le message.

### <a name="view-information-about-spoofed-messages"></a>Afficher des informations sur les messages usurpés

Dans la veille contre l’usurpation d’informations, cliquez sur Domaines **suspects** ou **Domaines non suspects** pour aller à la page Informations sur l’usurpation **d’informations sur l’usurpation d’informations.** La page contient les informations suivantes :

- **Domaine usurpé**: domaine de l’utilisateur usurpé qui s’affiche dans la zone De des clients de messagerie.  Cette adresse est également appelée `5322.From` adresse.
- **Infrastructure**: également appelée infrastructure _d’envoi._ Il s’ra de l’une des valeurs suivantes :
  - Domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source.
  - Si l’adresse IP source n’a pas d’enregistrement PTR, l’infrastructure d’envoi est identifiée comme \<source IP\> /24 (par exemple, 192.168.100.100/24).
- **Nombre de** messages : nombre de messages provenant de  la combinaison du domaine usurpé et de l’infrastructure d’envoi à votre organisation au cours des 7 derniers jours.
- **Dernière vue**: date de la dernière réception d’un message de l’infrastructure d’envoi qui contient le domaine usurpé.
- **Type d’usurpation**: l’une des valeurs suivantes :
  - **Interne**: l’expéditeur usurpé se trouve dans un domaine appartenant à votre organisation [(un domaine accepté).](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)
  - **Externe**: l’expéditeur usurpé se trouve dans un domaine externe.
- **Autorisé à usurper**: la valeur varie selon que vous avez cliqué sur des domaines **suspects** ou non **suspects** dans l’aperçu :
  - **Domaines suspects**: la **valeur d’usurpation** d’usurpation d’accès est toujours **Non**. Les messages provenant de la combinaison  du domaine usurpé et de l’infrastructure d’envoi sont marqués comme étant mauvais par la veille contre l’usurpation d’informations. L’action entreprise sur les messages usurpés est contrôlée par la stratégie anti-hameçonnage par défaut ou les stratégies anti-hameçonnage personnalisées (la valeur par défaut est Déplacer **le message** vers le dossier Courrier indésirable). Pour plus d’informations, voir [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-atp-anti-phishing-policies.md).
  - **Domaines non suspects**: la **valeur d’usurpation** d’accès est toujours **Oui**. Les messages provenant de la combinaison  du domaine usurpé et de l’infrastructure d’envoi sont marqués comme étant bons par la veille contre l’usurpation d’informations.

Vous pouvez cliquer sur les en-tête de colonne sélectionnés pour trier les résultats.

Pour filtrer les résultats, vous avez les options suivantes :

- Utilisez la **zone Filtrer le** domaine usurpé pour entrer une liste de valeurs de domaine usurpées séparées par des virgules pour filtrer les résultats.
- Utilisez la **zone d’infrastructure** Filtre pour entrer une liste de valeurs d’infrastructure séparées par des virgules pour filtrer les résultats.
- Cliquez sur **le bouton** Filtrer pour filtrer les résultats par **type d’usurpation d’accès.**

### <a name="view-details-about-spoofed-messages"></a>Afficher les détails sur les messages usurpés

Sélectionnez un élément dans la liste pour afficher les détails. Un volant s’affiche avec les informations et fonctionnalités suivantes :

- **Autorisé à usurper**: utilisez ce basculement pour remplacer le verdict de veille contre l’usurpation d’informations :
  - Si vous avez initialement sélectionné des domaines **suspects** dans l’aperçu, **l’usurpation** d’informations est désactivée. Pour l’activer, qui déplace l’entrée de l’aperçu de l’intelligence contre l’usurpation d’informations vers la liste des locataires autoriser/bloquer en tant qu’entrée d’usurpation d’accès, faites glisser le basculement sur : Activer/ ![ ](../../media/scc-toggle-on.png) Activer.
  - Si vous avez initialement sélectionné des domaines **non suspects** dans l’aperçu,  l’usurpation d’informations est désactivée. Pour la désactiver, qui déplace l’entrée de l’aperçu de l’intelligence contre l’usurpation d’informations vers la liste des locataires autoriser/bloquer en tant qu’entrée de blocage pour l’usurpation d’informations, faites glisser le basculement sur : Désactiver ![ ](../../media/scc-toggle-off.png) .

- Pourquoi nous l’avons capturé.
- Ce que vous devez faire.
- Résumé de domaine qui inclut la plupart des informations de la page principale de veille contre l’usurpation d’informations.
- WhoIs data about the sender.
- Messages similaires que nous avons vus dans votre client à partir du même expéditeur.

### <a name="about-allowed-spoofed-senders"></a>À propos des expéditeurs usurpés autorisés

Un expéditeur usurpé autorisé dans des domaines **non suspects** dans la veille contre l’usurpation d’informations  ou un expéditeur bloqué dans des domaines **suspects** que  vous avez manuellement modifié en « autorisé à usurper » autorise uniquement les messages provenant de la combinaison du domaine usurpé et de l’infrastructure d’envoi. Il n’autorise pas le courrier électronique provenant du domaine usurpé d’aucune source, ni le courrier provenant de l’infrastructure d’envoi pour n’importe quel domaine.

Par exemple, l’expéditeur usurpé suivant est autorisé à usurper :

- **Domaine**: gmail.com
- **Infrastructure**: tms.mx.com

Seul le courrier électronique provenant de cette paire d’infrastructure de domaine/d’envoi est autorisé à usurper l’adresse. Les autres expéditeurs qui tentent d’usurper gmail.com ne sont pas automatiquement autorisés. Les messages provenant d’expéditeurs d’autres domaines tms.mx.com sont toujours vérifiés par la veille contre l’usurpation d’adresse et peuvent être bloqués.

## <a name="use-the-spoof-intelligence-insight-in-exchange-online-powershell-or-standalone-eop-powershell"></a>Utiliser la veille contre l’usurpation d’Exchange Online PowerShell ou powerShell EOP autonome

Dans PowerShell, vous utilisez la cmdlet **Get-SpoofIntelligenceInsight** pour afficher les expéditeurs usurpés autorisés et bloqués qui ont été détectés par la veille contre l’usurpation d’adresse.  Pour autoriser ou bloquer manuellement les expéditeurs usurpés, vous devez utiliser la cmdlet **New-TenantAllowBlockListSpoofItems.** Pour plus d’informations, [voir Utiliser PowerShell pour configurer la liste d’attente des locataires.](tenant-allow-block-list.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-the-tenant-allowblock-list)

Pour afficher les informations dans l’aperçu de l’usurpation d’intelligence, exécutez la commande suivante :

```powershell
Get-SpoofIntelligenceInsight
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-SpoofIntelligenceInsight.](/powershell/module/exchange/get-spoofintelligenceinsight)

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Autres façons de gérer l’usurpation et le hameçonnage

Soyez prudent sur l’usurpation d’informations et la protection contre le hameçonnage. Voici quelques méthodes connexes pour vérifier les expéditeurs qui usurpent votre domaine et les empêcher d’endommager votre organisation :

- Vérifiez le **rapport de courrier d’usurpation d’adresse .** Vous pouvez souvent utiliser ce rapport pour afficher et gérer les expéditeurs usurpés. Pour plus d’informations, [voir le rapport sur les détections d’usurpation d’informations.](view-email-security-reports.md#spoof-detections-report)

- Examinez votre configuration SPF (Sender Policy Framework). Pour consulter une brève présentation de SPF et le configurer rapidement, voir [Configurer SPF dans Microsoft 365 pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Pour consulter des informations plus approfondies sur l’utilisation de SPF par Office 365, la résolution des problèmes et les déploiements non standard tels que les déploiements hybrides, voir Comment Office 365 utilise SPF (Sender Policy Framework) pour empêcher l’usurpation d’identité.

- Examinez votre configuration DKIM (DomainKeys Identified Mail). Vous devez utiliser DKIM en plus de SPF et DMARC pour empêcher les attaquants d’envoyer des messages qui semblent provenant de votre domaine. DKIM vous permet d'ajouter une signature numérique aux messages électroniques dans l'en-tête du message. Pour plus d’informations, [voir Utiliser DKIM pour valider](use-dkim-to-validate-outbound-email.md)les messages sortants envoyés à partir de votre domaine personnalisé dans Office 365 .

- Examinez votre configuration DMARC (Domain-based Message Authentication, Reporting, and Conformance). L’implémentation de DMARC avec SPF et DKIM fournit une protection supplémentaire contre l’usurpation et les courriers de hameçonnage. DMARC permet aux systèmes de messagerie de réception de déterminer ce qu’ils doivent faire des messages envoyés à partir de votre domaine qui sont rejetés par les contrôles de SPF ou de DKIM. Pour plus d’informations, [voir Utiliser DMARC pour valider le courrier électronique Office 365](use-dmarc-to-validate-email.md).
