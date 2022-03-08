---
title: Examen et réponse automatisés dans Microsoft Defender pour Office 365
keywords: AIR, autoIR, Microsoft Defender pour point de terminaison, automatisé, examen, réponse, correction, menaces, avancé, menace, protection
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 01/29/2021
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Commencer à utiliser les fonctionnalités d’investigation et de réponse automatisées dans Microsoft Defender pour Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e01fe2bdc5765c77500ae98e9c8177a35c683fca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324562"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Examen et réponse automatisés (AIR) dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Microsoft Defender pour Office 365 inclut de puissantes](defender-for-office-365.md) fonctionnalités d’investigation et de réponse automatisées (AIR) qui peuvent faire gagner du temps et des efforts à votre équipe en matière d’opérations de sécurité. À mesure que les alertes sont déclenchées, c’est à votre équipe des opérations de sécurité de passer en revue, de hiérarchiser et de répondre à ces alertes. Suivre le volume d’alertes entrantes peut être difficile à suivre. L’automatisation de certaines de ces tâches peut vous aider.

AIR permet à votre équipe des opérations de sécurité de fonctionner plus efficacement. Les fonctionnalités AIR incluent des processus d’examen automatisés en réponse aux menaces connues qui existent aujourd’hui. Les actions de correction appropriées attendent l’approbation, ce qui permet à votre équipe des opérations de sécurité de répondre efficacement aux menaces détectées. Avec AIR, votre équipe en charge des opérations de sécurité peut se concentrer sur des tâches prioritaires sans perdre de vue les alertes importantes déclenchées.

Cet article décrit les aspects suivants :

- Le [flux global d’AIR](#the-overall-flow-of-air) ;
- [Comment obtenir AIR](#how-to-get-air) ; et
- [Autorisations requises pour](#required-permissions-to-use-air-capabilities) configurer ou utiliser les fonctionnalités AIR.
- Modifications bientôt apportées à votre portail Microsoft 365 Defender web

Cet article inclut également [les étapes suivantes](#next-steps) et des ressources pour en savoir plus.

## <a name="the-overall-flow-of-air"></a>Le flux global d’AIR

Une alerte est déclenchée et un manuel de sécurité démarre une enquête automatisée, ce qui se traduit par des résultats et des actions recommandées. Voici le flux global d’AIR, étape par étape :

1. Une enquête automatisée est lancée de l’une des manières suivantes :
   - Une [alerte est déclenchée par un](#which-alert-policies-trigger-automated-investigations) message électronique suspect (par exemple, un message, une pièce jointe, une URL ou un compte d’utilisateur compromis). Un incident est créé et un examen automatisé commence . ou
   - Un analyste de [sécurité démarre une enquête automatisée lors](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) de l’utilisation de [l’Explorateur](threat-explorer.md).
2. Pendant qu’une enquête automatisée s’exécute, elle collecte des données sur le courrier électronique en question et les entités associées à ce courrier électronique. Ces entités peuvent inclure des fichiers, des URL et des destinataires. L’étendue de l’enquête peut augmenter à mesure que de nouvelles alertes et des alertes associées sont déclenchées.
3. Pendant et après un examen automatisé, des [détails et des résultats](air-view-investigation-results.md) sont disponibles. Les résultats [incluent des actions recommandées](air-remediation-actions.md) qui peuvent être prises pour répondre aux menaces qui ont été trouvées et y remédier.
4. Votre équipe des opérations de sécurité examine les résultats [et les recommandations](air-view-investigation-results.md) de l’examen, [et approuve ou rejette les actions de correction](air-review-approve-pending-completed-actions.md).
5. Comme les actions de correction en attente sont approuvées (ou rejetées), l’examen automatisé se termine.

Dans Microsoft Defender pour Office 365, aucune action de correction n’est prise automatiquement. Les actions correctives sont mises en œuvre uniquement après approbation par l’équipe de sécurité de votre organisation. Les fonctionnalités AIR font gagner du temps à votre équipe en matière d’opérations de sécurité en identifiant les actions de correction et en fournissant les détails nécessaires pour prendre une décision éclairée.

Pendant et après chaque examen automatisé, votre équipe des opérations de sécurité peut :

- [Afficher les détails d’une alerte liée à un examen](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [Afficher les détails des résultats d’une enquête](air-view-investigation-results.md#view-details-of-an-investigation)
- [Examiner et approuver des actions à la suite d’un examen](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Pour obtenir une vue d’ensemble plus détaillée, voir [Fonctionnement d’AIR](automated-investigation-response-office.md).

## <a name="how-to-get-air"></a>Comment obtenir AIR

Les fonctionnalités AIR sont incluses [dans Microsoft Defender Office 365](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2), à condition que vos stratégies et alertes soient configurées. Vous avez besoin d’aide ? Suivez les instructions de [la protection contre les](protect-against-threats.md) menaces pour configurer les paramètres de protection suivants :

- [Journalisation d’audit](../../compliance/turn-audit-log-search-on-or-off.md) (doit être désactivée)
- [Protection contre les programmes malveillants](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Protection anti-hameçonnage](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [Anti-spam protection](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Coffre liens et pièces jointes Coffre jointes](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

En outre, veillez à passer en revue les stratégies [d’alerte](../../compliance/alert-policies.md) de votre organisation, en particulier les stratégies par défaut dans [la catégorie de gestion des menaces](../../compliance/alert-policies.md#default-alert-policies).

## <a name="which-alert-policies-trigger-automated-investigations"></a>Quelles stratégies d’alerte déclenchent des enquêtes automatisées ?

Microsoft 365 fournit de nombreuses stratégies d’alerte intégrées qui permettent d’identifier les abus des autorisations d’administrateur Exchange, l’activité des programmes malveillants, les menaces externes et internes potentielles et les risques de gouvernance des informations. Plusieurs des [stratégies d’alerte par défaut peuvent](../../compliance/alert-policies.md#default-alert-policies) déclencher des enquêtes automatisées. Le tableau suivant décrit les alertes qui déclenchent des enquêtes automatisées, leur gravité dans le portail Microsoft 365 Defender et la façon dont elles sont générées :

<br>

****

|Alerte|Severity|Comment l’alerte est générée|
|---|---|---|
|Un clic d’URL potentiellement malveillant a été détecté|**High**|Cette alerte est générée lorsque l’une des alertes suivantes se produit : <ul><li>Un utilisateur protégé par des liens [Coffre de](safe-links.md) votre organisation clique sur un lien malveillant</li><li>Les modifications de verdict pour les URL sont identifiées par Microsoft Defender Office 365</li><li>Les utilisateurs remplacent Coffre pages d’avertissement de liens (en fonction de la stratégie de liens Coffre [de votre organisation](set-up-safe-links-policies.md).</li></ul> <p> Pour plus d’informations sur les événements qui déclenchent cette alerte, voir [Configurer Coffre de liens.](set-up-safe-links-policies.md)|
|Un message électronique est signalé par un utilisateur comme programme malveillant ou hameçonnage|**Informatif**|Cette alerte est générée lorsque les utilisateurs de votre organisation signalent des messages comme courrier de hameçonnage à l’aide du module de signalement du [message](enable-the-report-message-add-in.md) ou du [module de signalement du hameçonnage](enable-the-report-phish-add-in.md).|
|Les messages électroniques contenant des programmes malveillants sont supprimés après la remise|**Informatif**|Cette alerte est générée lorsqu’un message électronique contenant un programme malveillant est remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés de Exchange Online boîtes aux lettres à l’aide de la [purge automatique d’heure zéro (ZAP).](zero-hour-auto-purge.md)|
|Les messages électroniques contenant des URL de hameçonnage sont supprimés après la remise|**Informatif**|Cette alerte est générée lorsqu’un message contenant du hameçonnage est remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés de Exchange Online boîtes aux lettres à l’aide de [ZAP](zero-hour-auto-purge.md).|
|Des modèles d’envoi de courrier suspects sont détectés|**Medium**|Cette alerte est générée lorsqu’une personne de votre organisation a envoyé des messages suspects et risque d’être limitée à l’envoi de courriers électroniques. L’alerte est un avertissement précoce pour un comportement qui peut indiquer que le compte est compromis, mais pas assez grave pour restreindre l’utilisateur. <p> Bien que cela soit rare, une alerte générée par cette stratégie peut être une anomalie. Toutefois, il est bon de vérifier si le compte [d’utilisateur est compromis](responding-to-a-compromised-email-account.md).|
|Un utilisateur est limité à l’envoi de courriers électroniques|**High**|Cette alerte est générée lorsqu’une personne de votre organisation est limitée à l’envoi de messages sortants. Cette alerte se produit généralement [lorsqu’un compte de messagerie est compromis](responding-to-a-compromised-email-account.md). <p> Pour plus d’informations sur les utilisateurs restreints, voir Supprimer les utilisateurs bloqués du portail Utilisateurs restreints [dans Microsoft 365](removing-user-from-restricted-users-portal-after-spam.md).|
|

> [!TIP]
> Pour en savoir plus sur les stratégies d’alerte ou modifier les paramètres par défaut, consultez stratégies [d’alerte dans la Centre de conformité Microsoft 365](../../compliance/alert-policies.md).

## <a name="required-permissions-to-use-air-capabilities"></a>Autorisations requises pour utiliser les fonctionnalités AIR

Les autorisations sont accordées par le biais de certains rôles, tels que ceux décrits dans le tableau suivant :

<br>

****

|Tâche|Rôle(s) requis(s)|
|---|---|
|Configurer les fonctionnalités AIR|L’un des rôles suivants : <ul><li>Administrateur général</li><li>Administrateur de sécurité</li></ul> <p> Ces rôles peuvent être attribués [dans Azure Active Directory](/azure/active-directory/roles/permissions-reference) ou dans [le portail Microsoft 365 Defender web](permissions-microsoft-365-security-center.md).|
|Démarrer une analyse automatisée <p> --- ou --- <p> Approuver ou rejeter les actions recommandées|L’un des rôles suivants, [attribués dans Azure Active Directory](/azure/active-directory/roles/permissions-reference) ou dans [le portail Microsoft 365 Defender web](permissions-microsoft-365-security-center.md) : <ul><li>Administrateur général</li><li>Administrateur de sécurité</li><li>Opérateur de sécurité</li><li>Lecteur de sécurité <br> --- et --- </li><li>Recherche et purge (ce rôle est attribué uniquement dans le [portail Microsoft 365 Defender web](permissions-microsoft-365-security-center.md). Vous devrez peut-être créer un groupe de rôles de **collaboration** & messagerie et ajouter le rôle Recherche et purge à ce nouveau groupe de rôles.</li></ul>|

## <a name="required-licenses"></a>Licences requises

[Les licences Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) doivent être affectées à :

- Administrateurs de sécurité (y compris les administrateurs globaux)
- L’équipe des opérations de sécurité de votre organisation (y compris les lecteurs de sécurité et ceux ayant le rôle **Recherche et purge** )
- Utilisateurs finaux

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>Des modifications seront bientôt apportées à votre portail Microsoft 365 Defender client

Si vous utilisez déjà les fonctionnalités AIR dans Microsoft Defender pour Office 365, vous êtes sur le point de voir des modifications dans le portail Microsoft 365 Defender [amélioré](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal).

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Centre de l’action unifiée.":::

Le portail d’Microsoft 365 Defender <https://security.microsoft.com> nouveau et amélioré regroupe les fonctionnalités AIR dans [Microsoft Defender pour Office 365](defender-for-office-365.md) et [dans Microsoft Defender pour le point de terminaison](../defender-endpoint/automated-investigations.md). Avec ces mises à jour et améliorations, votre équipe des opérations de sécurité sera en mesure d’afficher des détails sur les enquêtes automatisées et les actions de correction d’e-mail, le contenu de collaboration, les comptes d’utilisateurs, et les appareils, le tout au même endroit.

> [!TIP]
> Le nouveau portail Microsoft 365 Defender remplace les centres d’administration suivants :
>
> - Centre de sécurité & conformité (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> En plus de la modification de l’URL, il existe une nouvelle apparence, conçue pour donner à votre équipe de sécurité une expérience plus rationalisée, avec une visibilité à un plus grand nombre de détections de menaces au même endroit.

### <a name="what-to-expect"></a>À quoi s’attendre

Le tableau suivant répertorie les modifications et améliorations apportées à AIR dans Microsoft Defender pour Office 365.

<br>

****

|Élément|Qu’est-ce qui change ?|
|---|---|
|**Page Enquêtes**|La page **Enquêtes mise** à jour est plus cohérente avec ce que vous voyez [dans Microsoft Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations). Vous verrez des modifications générales de mise en forme et de style qui s’alignent sur le nouvel affichage **Examens** unifié. Par exemple, le graphique d’investigation a un format plus unifié.|
|**Onglet Utilisateurs**|**L’onglet** Utilisateurs est désormais **l’onglet Boîtes aux** lettres. Les détails sur les utilisateurs sont répertoriés sous **l’onglet Boîte aux** lettres.|
|**Onglet Courrier** électronique|**L’onglet** Courrier a été supprimé . consultez **l’onglet Entités** pour voir la liste des éléments de cluster de messagerie et de messagerie.|
|**Onglet Entités**|**L’onglet Entités** possède un style onglet dans l’onglet qui inclut un affichage récapitulatif et la possibilité de filtrer par type d’entité. **L’onglet Entités** inclut désormais une option de **recherche** d’accès en plus de l’option **Ouvrir dans l’Explorateur**. Vous pouvez désormais utiliser [l’Explorateur](threat-explorer.md) ou la [recherche avancée pour](../defender-endpoint/advanced-hunting-overview.md) rechercher des entités et des menaces, et filtrer les résultats.|
|**Onglet Actions**|L’onglet **Actions mis** à jour inclut désormais un onglet **Actions en attente** et un onglet **Historique des actions** . Les actions peuvent être approuvées (ou rejetées) dans un volet latéral qui s’ouvre lorsque vous sélectionnez une action en attente.|
|**Onglet Preuve**|Un nouvel **onglet Preuves** affiche les principales conclusions d’entité liées aux actions. Les actions liées à chaque élément de preuve peuvent être approuvées (ou rejetées) dans un volet latéral qui s’ouvre lorsque vous sélectionnez une action en attente.|
|**Centre de notifications**|Le centre **de actions** mis à jour regroupe<https://security.microsoft.com/action-center> les actions en attente et terminées sur les messages électroniques, les appareils et les identités. Pour en savoir plus, consultez le Centre de l’action. (Pour en savoir plus, [consultez le centre de actions](../defender/m365d-action-center.md).)|
|**Page Incidents**|La page **Incidents** met désormais en corrélation plusieurs enquêtes afin de fournir une meilleure vue consolidée des enquêtes. ([En savoir plus sur les incidents](../defender/incidents-overview.md).)|
|

## <a name="next-steps"></a>Étapes suivantes

- [Voir les détails et les résultats d’une enquête automatisée](air-view-investigation-results.md#view-details-of-an-investigation)
- [Examiner et approuver les actions en attente](air-remediation-actions.md)
