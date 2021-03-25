---
title: Stratégies de sécurité prédéfinies
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
localization_priority: Normal
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à appliquer des paramètres de stratégie standard et stricts aux fonctionnalités de protection d’Exchange Online Protection (EOP) et de Microsoft Defender pour Office 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7579b2d2a47135ab9628d2ec8990f53c3917514b
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204355"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les stratégies de sécurité prédéfinisées fournissent un emplacement centralisé pour l’application de toutes les stratégies recommandées de courrier indésirable, de programmes malveillants et de hameçonnage aux utilisateurs à la fois. Les paramètres de stratégie ne sont pas configurables. Au lieu de cela, elles sont définies par nous et sont basées sur nos observations et expériences dans les centres de données pour trouver un équilibre entre la mise à l’écart du contenu dangereux des utilisateurs sans perturber leur travail.

Le reste de cette rubrique décrit les stratégies de sécurité prédéfinie et la façon de les configurer.

## <a name="what-preset-security-policies-are-made-of"></a>En quoi les stratégies de sécurité prédéfines sont-elles

Les stratégies de sécurité prédéfines sont composées des éléments suivants :

- Profils
- Stratégies
- Paramètres de stratégie

En outre, l’ordre de priorité est important si plusieurs stratégies de sécurité prédéfinir et autres stratégies s’appliquent à la même personne.

### <a name="profiles-in-preset-security-policies"></a>Profils dans les stratégies de sécurité prédéfines

Un profil détermine le niveau de protection. Les profils suivants sont disponibles :

- **Protection standard**: profil de protection de référence adapté à la plupart des utilisateurs.
- **Protection stricte**: profil de protection plus agressif pour les utilisateurs sélectionnés (cibles à valeur élevée ou utilisateurs prioritaires).

Vous utilisez des règles avec des conditions et des exceptions qui déterminent à qui les profils sont ou ne sont pas appliqués.

Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

Les conditions et les exceptions disponibles sont les :

- **Les destinataires sont les** boîtes aux lettres, les utilisateurs de messagerie ou les contacts de messagerie de votre organisation.
- **Les destinataires sont membres de**: Groupes de votre organisation.
- **Les domaines destinataires sont**: Domaines acceptés configurés dans Microsoft 365.

### <a name="policies-in-preset-security-policies"></a>Stratégies dans les stratégies de sécurité prédéfines

Les stratégies de sécurité prédéfines utilisent les stratégies correspondantes des différentes fonctionnalités de protection dans EOP et Microsoft Defender pour Office 365. Ces stratégies sont _créées après_ l’affectation des stratégies de sécurité prédéfinfines Protection **standard** ou **Protection** stricte aux utilisateurs. Vous ne pouvez pas modifier ces stratégies.

- **Stratégies Exchange Online Protection (EOP)**: cela inclut les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online et les organisations EOP autonomes sans boîtes aux lettres Exchange Online :

  - [Stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md) **nommées Standard Preset Security Policy** et Strict **Preset Security Policy**.
  - [Stratégies anti-programme malveillant](configure-anti-malware-policies.md) nommées Stratégie de sécurité **prédéfinë standard** et **Stratégie de sécurité prédéfinë stricte.**
  - [Stratégies anti-hameçonnage EOP](set-up-anti-phishing-policies.md#spoof-settings) nommées Stratégie de sécurité prédéfini **standard** et Stratégie de sécurité prédéfini stricte **(paramètres** d’usurpation).

- **Stratégies de Microsoft Defender pour Office 365**: cela inclut les organisations 365 E5 ou Defender pour les abonnements de modules office 365 :

  - Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 nommées **Stratégie** de sécurité prédéfinë standard et Stratégie de sécurité prédéfinë **stricte,** qui incluent :

    - Paramètres [d’usurpation disponibles](set-up-anti-phishing-policies.md#spoof-settings) dans les stratégies anti-hameçonnage EOP.
    - [Paramètres d’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Seuils de hameçonnage avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)

  - [Stratégies de liens sécurisés](set-up-safe-links-policies.md) nommées Stratégie de sécurité **prédéfinfine standard** et **Stratégie de sécurité prédéfine stricte.**

  - [Stratégies de pièces jointes sécurisées](set-up-safe-attachments-policies.md) nommées Stratégie de sécurité **prédéfinfine standard** et **Stratégie de sécurité prédéfine stricte.**

Notez que vous pouvez appliquer des protections EOP à différents utilisateurs que Microsoft Defender pour les protections Office 365.

### <a name="policy-settings-in-preset-security-policies"></a>Paramètres de stratégie dans les stratégies de sécurité prédéfines

Vous ne pouvez pas modifier les paramètres de stratégie dans les profils de protection. Les **valeurs des** paramètres de stratégie Standard et **Strict** sont décrites dans les paramètres recommandés pour EOP et Microsoft Defender pour la sécurité [Office 365.](recommended-settings-for-eop-and-office365.md)

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Ordre de priorité pour les stratégies de sécurité prédéfinir et autres stratégies

Lorsque plusieurs stratégies sont appliquées à un utilisateur, l’ordre suivant est appliqué de la priorité la plus élevée à la priorité la plus faible :

1. **Stratégie de sécurité** prédéfinfine de protection stricte
2. **Stratégie de sécurité** prédéfinfine de protection standard
3. Stratégies de sécurité personnalisées
4. Stratégies de sécurité par défaut

En d’autres termes, les paramètres de la stratégie De **protection** stricte remplacent les paramètres de la stratégie de **protection standard,** qui remplace les paramètres d’une stratégie personnalisée, qui remplace les paramètres de la stratégie par défaut.

## <a name="assign-preset-security-policies-to-users"></a>Affecter des stratégies de sécurité prédéfines aux utilisateurs

### <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour aller directement à la page Stratégies de **sécurité prédéfines,** utilisez <https://protection.office.com/presetSecurityPolicies> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cette rubrique.
  - Pour configurer des stratégies de sécurité prédéfinie, vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur** de la sécurité. 
  - Pour accéder en lecture seule aux stratégies de sécurité prédéfinis, vous devez être membre du **groupe** de rôles Lecteur global.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarque**: l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux _utilisateurs_ les autorisations et autorisations requises pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-security--compliance-center-to-assign-preset-security-policies-to-users"></a>Utiliser le Centre de sécurité & conformité pour affecter des stratégies de sécurité prédéfines aux utilisateurs

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **Preset security policies**.

2. Sous **Protection standard ou** Protection **stricte,** cliquez sur **Modifier.**

3. **L’Assistant Appliquer une protection standard** ou Appliquer une **protection** stricte démarre. Sur les **protections EOP s’appliquent** à l’étape, identifiez les destinataires internes à qui les [protections EOP](#policies-in-preset-security-policies) s’appliquent :

   1. Cliquez **sur Ajouter une condition.** Dans ladown qui s’affiche, sélectionnez une condition sous **Applied si**:

      - **Les destinataires sont**
      - **Les destinataires sont membres de**
      - **Les domaines destinataires sont**

      Vous ne pouvez utiliser une condition qu’une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition. Plusieurs valeurs de la même condition utilisent la logique OR (par exemple, _\<recipient1\>_ ou _\<recipient2\>_ ).

   2. La condition que vous avez sélectionnée apparaît dans une section ombrée. Dans cette section, cliquez dans **l’une de ces sections.** Si vous patientez un instant, une liste s’affiche pour vous aider à sélectionner une valeur. Vous pouvez également commencer à taper une valeur pour filtrer la liste et sélectionner une valeur. Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur individuelle, cliquez **sur Supprimer** ![ l’icône ](../../media/scc-remove-icon.png) sur la valeur. Pour supprimer la condition entière, cliquez **sur Supprimer** ![ l’icône ](../../media/scc-remove-icon.png) sur la condition.

   3. Pour ajouter une autre condition, cliquez **sur Ajouter une condition** et sélectionnez-la parmi les conditions restantes. Différentes conditions utilisent la logique AND (par exemple, _\<recipient1\>_ et _\<member of group 1\>_ ).

      Répétez l’étape précédente pour ajouter des valeurs à la condition, puis répétez cette étape autant de fois que nécessaire ou jusqu’à ce que vous n’entiez plus dans les conditions.

   4. Pour ajouter une exception, cliquez **sur Ajouter une condition.** In the dropdown that appears, select a condition under **Except when**. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Si votre organisation dispose de Microsoft Defender pour Office 365, les **protections ATP** s’appliquent pour identifier les destinataires internes à qui s’appliquent les protections Microsoft Defender pour [Office 365.](#policies-in-preset-security-policies)

   Les paramètres et le comportement sont exactement comme les **protections EOP s’appliquent à l’étape.**

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. À **l’étape** Confirmer, vérifiez vos sélections, puis cliquez sur **Confirmer.**

### <a name="use-the-security--compliance-center-to-modify-the-assignments-of-preset-security-policies"></a>Utiliser le Centre de sécurité & conformité pour modifier les affectations de stratégies de sécurité prédéfines

Les étapes de modification de l’attribution de la stratégie de **sécurité Protection standard** ou **Protection** stricte sont les mêmes que lorsque vous avez initialement affecté les stratégies de sécurité prédéfines [aux utilisateurs.](#use-the-security--compliance-center-to-assign-preset-security-policies-to-users)

Pour désactiver les stratégies de **sécurité de protection standard** ou stricte tout en conservant les conditions et les exceptions existantes, faites glisser le basculement vers **Désactivé.**  Pour activer les stratégies, faites glisser le basculement sur **Activé.**

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez bien  affecté la stratégie de sécurité **Protection standard** ou Protection stricte à un utilisateur, utilisez un paramètre de protection dont la valeur par défaut est différente de celle de la **protection standard,** ce qui est différent du paramètre **Strict Protection.**

Par exemple, pour les e-mails détectés comme courrier indésirable (et non comme courrier indésirable à niveau de confiance élevé), vérifiez que le message est remis dans le dossier Courrier indésirable pour les utilisateurs de **la protection standard** et mis en quarantaine pour les utilisateurs à **protection** stricte.

Ou, pour les messages électroniques en [nombre,](bulk-complaint-level-values.md)vérifiez que la valeur BCL 6 ou supérieure fournit le message au dossier  Courrier indésirable pour les utilisateurs de **la protection standard,** et que la valeur BCL 4 ou supérieure met le message en quarantaine pour les utilisateurs de protection stricte.