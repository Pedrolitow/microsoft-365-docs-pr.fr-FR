---
title: Examen et réponse automatisés dans Microsoft Defender pour Office 365
keywords: AIR, autoIR, Microsoft Defender pour point de terminaison, automatisé, investigation, réponse, correction, menaces, avancées, menaces, protection
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.date: 01/29/2021
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- m365-security
- m365initiative-defender-office365
description: Commencez à utiliser les fonctionnalités d’investigation et de réponse automatisées dans Microsoft Defender pour Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 08e17eecfab17f5a4fc6b719e66f5eadc5e3bac3
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68622088"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Investigation et réponse automatisées (AIR) dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Microsoft Defender pour Office 365](defender-for-office-365.md) inclut de puissantes fonctionnalités d’investigation et de réponse automatisées (AIR) qui peuvent faire gagner du temps et des efforts à votre équipe chargée des opérations de sécurité. À mesure que les alertes sont déclenchées, c’est à votre équipe des opérations de sécurité de passer en revue, de hiérarchiser et de répondre à ces alertes. Suivre le volume d’alertes entrantes peut s’avérer fastidieux. L’automatisation de certaines de ces tâches peut vous aider.

AIR permet à votre équipe des opérations de sécurité de fonctionner plus efficacement et plus efficacement. Les fonctionnalités AIR incluent des processus d’investigation automatisés en réponse aux menaces connues qui existent aujourd’hui. Les actions de correction appropriées attendent l’approbation, ce qui permet à votre équipe des opérations de sécurité de répondre efficacement aux menaces détectées. Avec AIR, votre équipe des opérations de sécurité peut se concentrer sur des tâches de priorité plus élevée sans perdre de vue les alertes importantes déclenchées.

Cet article décrit les aspects suivants :

- Le [flux global d’AIR](#the-overall-flow-of-air);
- [Comment obtenir air](#how-to-get-air); Et
- [Autorisations requises](#required-permissions-to-use-air-capabilities) pour configurer ou utiliser les fonctionnalités AIR.
- Modifications qui seront bientôt apportées à votre portail Microsoft 365 Defender

Cet article inclut également les [étapes suivantes](#next-steps) et les ressources pour en savoir plus.

## <a name="the-overall-flow-of-air"></a>Le flux global d’AIR

Une alerte est déclenchée et un playbook de sécurité démarre une enquête automatisée, ce qui entraîne des résultats et des actions recommandées. Voici le flux global d’AIR, étape par étape :

1. Une enquête automatisée est lancée de l’une des manières suivantes :
   - Une [alerte est déclenchée](#which-alert-policies-trigger-automated-investigations) par un élément suspect par e-mail (par exemple, un message, une pièce jointe, une URL ou un compte d’utilisateur compromis). Un incident est créé et une enquête automatisée commence ; Ou
   - Un analyste de sécurité [démarre une enquête automatisée](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) lors de l’utilisation de [l’Explorateur](threat-explorer.md).
2. Pendant l’exécution d’une enquête automatisée, elle collecte des données sur l’e-mail en question et les entités associées à cet e-mail. Ces entités peuvent inclure des fichiers, des URL et des destinataires. L’étendue de l’investigation peut augmenter à mesure que des alertes nouvelles et associées sont déclenchées.
3. Pendant et après une enquête automatisée, [des détails et des résultats](air-view-investigation-results.md) sont disponibles. Les résultats incluent [des actions recommandées](air-remediation-actions.md) qui peuvent être prises pour répondre aux menaces détectées et les corriger.
4. Votre équipe chargée des opérations de sécurité examine les [résultats et les recommandations de l’enquête](air-view-investigation-results.md), puis [approuve ou rejette les actions de correction](air-review-approve-pending-completed-actions.md).
5. À mesure que les actions de correction en attente sont approuvées (ou rejetées), l’enquête automatisée se termine.

Dans Microsoft Defender pour Office 365, aucune action de correction n’est effectuée automatiquement. Les actions correctives sont mises en œuvre uniquement après approbation par l’équipe de sécurité de votre organisation. Les fonctionnalités AIR permettent à votre équipe chargée des opérations de sécurité d’économiser du temps en identifiant les actions de correction et en fournissant les détails nécessaires pour prendre une décision éclairée.

Pendant et après chaque enquête automatisée, votre équipe des opérations de sécurité peut :

- [Afficher les détails d’une alerte liée à une enquête](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [Afficher les détails des résultats d’une enquête](air-view-investigation-results.md#view-details-of-an-investigation)
- [Examiner et approuver les actions à la suite d’une enquête](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Pour obtenir une vue d’ensemble plus détaillée, consultez [le fonctionnement d’AIR](automated-investigation-response-office.md).

## <a name="how-to-get-air"></a>Comment obtenir AIR

Les fonctionnalités AIR sont incluses dans [Microsoft Defender pour Office 365](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2), à condition que vos stratégies et alertes soient configurées. Vous avez besoin d’aide ? Suivez les instructions de [Protection contre les menaces](protect-against-threats.md) pour configurer ou configurer les paramètres de protection suivants :

- [Journalisation d’audit](../../compliance/turn-audit-log-search-on-or-off.md) (doit être activée)
- [Protection contre les programmes malveillants](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Protection anti-hameçonnage](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [Anti-spam protection](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Liens fiables et pièces jointes fiables](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

En outre, veillez à [examiner les stratégies d’alerte de votre organisation](../../compliance/alert-policies.md), en particulier les [stratégies par défaut dans la catégorie Gestion des menaces](../../compliance/alert-policies.md#default-alert-policies).

## <a name="which-alert-policies-trigger-automated-investigations"></a>Quelles stratégies d’alerte déclenchent des investigations automatisées ?

Microsoft 365 fournit de nombreuses stratégies d’alerte intégrées qui permettent d’identifier les abus d’autorisations d’administrateur Exchange, l’activité des programmes malveillants, les menaces externes et internes potentielles et les risques de gouvernance des informations. Plusieurs des stratégies [d’alerte par défaut](../../compliance/alert-policies.md#default-alert-policies) peuvent déclencher des investigations automatisées. Le tableau suivant décrit les alertes qui déclenchent des investigations automatisées, leur gravité dans le portail Microsoft 365 Defender et la façon dont elles sont générées :

|Alerte|Severity|Comment l’alerte est générée|
|---|---|---|
|Un clic d’URL potentiellement malveillant a été détecté|**High**|Cette alerte est générée lorsque l’une des opérations suivantes se produit : <ul><li>Un utilisateur protégé par [des liens fiables](safe-links.md) dans votre organisation clique sur un lien malveillant</li><li>Les modifications de verdict pour les URL sont identifiées par Microsoft Defender pour Office 365</li><li>Les utilisateurs remplacent les pages d’avertissement liens sécurisés (en fonction de la [stratégie liens sécurisés](set-up-safe-links-policies.md) de votre organisation.</li></ul> <p> Pour plus d’informations sur les événements qui déclenchent cette alerte, consultez [Configurer des stratégies de liens fiables](set-up-safe-links-policies.md).|
|Un message électronique est signalé par un utilisateur comme un programme malveillant ou un hameçonnage|**Informatif**|Cette alerte est générée lorsque les utilisateurs de votre organisation signalent des messages en tant qu’e-mail de hameçonnage à l’aide du [complément Message de rapport](enable-the-report-message-add-in.md) ou du [complément d’hameçonnage de rapport](enable-the-report-phish-add-in.md).|
|Email messages contenant des programmes malveillants sont supprimés après la remise|**Informatif**|Cette alerte est générée lorsque tous les messages électroniques contenant des programmes malveillants sont remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés des boîtes aux lettres Exchange Online à l’aide du [vidage automatique de zéro heure (ZAP).](zero-hour-auto-purge.md)|
|Email messages contenant des URL de hameçonnage sont supprimés après la remise|**Informatif**|Cette alerte est générée lorsque tous les messages contenant du hameçonnage sont remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés des boîtes aux lettres Exchange Online à l’aide de [ZAP](zero-hour-auto-purge.md).|
|Des modèles d’envoi de courrier suspect sont détectés|**Medium**|Cette alerte est générée lorsqu’une personne de votre organisation a envoyé des e-mails suspects et risque d’être empêchée d’envoyer des e-mails. L’alerte est un avertissement précoce pour le comportement qui peut indiquer que le compte est compromis, mais pas assez grave pour restreindre l’utilisateur. <p> Bien qu’il soit rare, une alerte générée par cette stratégie peut être une anomalie. Toutefois, il est judicieux de [vérifier si le compte d’utilisateur est compromis](responding-to-a-compromised-email-account.md).|
|Un utilisateur ne peut pas envoyer de courrier électronique|**High**|Cette alerte est générée lorsqu’une personne de votre organisation ne peut pas envoyer de courrier sortant. Cette alerte se produit généralement lorsqu’un [compte de messagerie est compromis](responding-to-a-compromised-email-account.md). <p> Pour plus d’informations sur les utilisateurs restreints, consultez [Supprimer les utilisateurs bloqués du portail Utilisateurs restreints dans Microsoft 365](removing-user-from-restricted-users-portal-after-spam.md).|

> [!TIP]
> Pour en savoir plus sur les stratégies d’alerte ou modifier les paramètres par défaut, consultez Stratégies [d’alerte dans le portail de conformité Microsoft Purview](../../compliance/alert-policies.md).

## <a name="required-permissions-to-use-air-capabilities"></a>Autorisations requises pour utiliser les fonctionnalités AIR

Les autorisations sont accordées par le biais de certains rôles, tels que ceux décrits dans le tableau suivant :

|Tâche|Rôles requis|
|---|---|
|Configurer les fonctionnalités AIR|L’un des rôles suivants : <ul><li>Administrateur général</li><li>Administrateur de sécurité</li></ul> <p> Ces rôles peuvent être attribués dans [Azure Active Directory](/azure/active-directory/roles/permissions-reference) ou dans le [portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).|
|Démarrer une analyse automatisée <p> --- ou --- <p> Approuver ou rejeter les actions recommandées|L’un des rôles suivants, attribués dans [Azure Active Directory](/azure/active-directory/roles/permissions-reference) ou dans le [portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md) : <ul><li>Administrateur général</li><li>Administrateur de sécurité</li><li>Opérateur de sécurité</li><li>Lecteur de sécurité <br> --- et --- </li><li>Recherche et vidage (ce rôle est attribué uniquement dans le [portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md). Vous devrez peut-être créer un nouveau groupe de rôles **de collaboration Email &** et ajouter le rôle De recherche et de vidage à ce nouveau groupe de rôles.</li></ul>|

## <a name="required-licenses"></a>Licences requises

[Microsoft Defender pour Office 365 licences Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) doivent être affectées à :

- Administrateurs de sécurité (y compris les administrateurs généraux)
- L’équipe des opérations de sécurité de votre organisation (y compris les lecteurs de sécurité et ceux qui ont le rôle **De recherche et purge** )
- Utilisateurs finaux

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>Les modifications seront bientôt apportées dans votre portail Microsoft 365 Defender

Si vous utilisez déjà les fonctionnalités AIR dans Microsoft Defender pour Office 365, vous allez voir certaines modifications dans le [portail Microsoft 365 Defender amélioré](../defender/microsoft-365-defender-portal.md).

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Centre d’action unifiée" lightbox="../../media/m3d-action-center-unified.png":::

Le portail <https://security.microsoft.com> Microsoft 365 Defender nouveau et amélioré réunit les fonctionnalités AIR dans [Microsoft Defender pour Office 365](defender-for-office-365.md) et dans [Microsoft Defender pour point de terminaison](../defender-endpoint/automated-investigations.md). Avec ces mises à jour et améliorations, votre équipe des opérations de sécurité sera en mesure d’afficher des détails sur les enquêtes automatisées et les actions de correction d’e-mail, le contenu de collaboration, les comptes d’utilisateurs, et les appareils, le tout au même endroit.

> [!TIP]
> Le nouveau portail Microsoft 365 Defender remplace les centres d’administration suivants :
>
> - Security & Compliance Center (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> En plus de la modification de l’URL, il existe une nouvelle apparence, conçue pour offrir à votre équipe de sécurité une expérience plus rationalisée, avec une visibilité sur plus de détections de menaces au même endroit.

### <a name="what-to-expect"></a>À quoi s'attendre

Le tableau suivant répertorie les modifications et améliorations apportées à AIR dans Microsoft Defender pour Office 365.

|Élément|Qu’est-ce qui change ?|
|---|---|
|**Page Investigations**|La page **Investigations** mise à jour est plus cohérente avec ce que vous voyez dans [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations). Vous verrez des modifications générales de format et de style qui s’alignent sur la nouvelle vue **Investigations** unifiée. Par exemple, le graphique d’investigation a un format plus unifié.|
|**Onglet Utilisateurs**|**L’onglet Utilisateurs** est désormais l’onglet **Boîtes aux lettres**. Les détails sur les utilisateurs sont répertoriés sous l’onglet **Boîte aux lettres**.|
|**onglet Email**|**L’onglet Email** a été supprimé ; accédez à l’onglet **Entités** pour afficher la liste des éléments de cluster de courrier électronique et de courrier électronique.|
|**Onglet Entités**|L’onglet **Entités** a un style tab-in-tab qui inclut une vue tout récapitulative et la possibilité de filtrer par type d’entité. **L’onglet Entités** inclut désormais une option **de chasse Go** en plus de l’option **Ouvrir dans l’Explorateur**. Vous pouvez maintenant utiliser [l’Explorateur](threat-explorer.md) ou [la recherche avancée](../defender-endpoint/advanced-hunting-overview.md) pour rechercher des entités et des menaces, et filtrer les résultats.|
|**Onglet Actions**|L’onglet **Actions** mis à jour inclut désormais un onglet **Actions en attente** et un onglet **Historique des actions** . Les actions peuvent être approuvées (ou rejetées) dans un volet latéral qui s’ouvre lorsque vous sélectionnez une action en attente.|
|**Onglet Preuves**|Un nouvel onglet **Preuve** affiche les principales conclusions d’entité liées aux actions. Les actions liées à chaque élément de preuve peuvent être approuvées (ou rejetées) dans un volet latéral qui s’ouvre lorsque vous sélectionnez une action en attente.|
|**Centre d’action**|Le **centre d’actions** mis à jour (<https://security.microsoft.com/action-center>) regroupe les actions en attente et terminées sur les e-mails, les appareils et les identités. Pour en savoir plus, consultez le Centre d’actions. (Pour en savoir plus, consultez [le Centre d’action](../defender/m365d-action-center.md).)|
|**Page Incidents**|La page **Incidents** met désormais en corrélation plusieurs enquêtes pour fournir une meilleure vue consolidée des enquêtes. ([En savoir plus sur les incidents](../defender/incidents-overview.md).)|

## <a name="next-steps"></a>Prochaines étapes

- [Voir les détails et les résultats d’une enquête automatisée](air-view-investigation-results.md#view-details-of-an-investigation)
- [Examiner et approuver les actions en attente](air-remediation-actions.md)
