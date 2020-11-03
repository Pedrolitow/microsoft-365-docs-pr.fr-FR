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
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à appliquer des paramètres de stratégie standard et stricts pour les fonctionnalités de protection d’Exchange Online Protection (EOP) et Office 365 Advanced Threat Protection (ATP).
ms.openlocfilehash: a624d48944965c217fb8547e4f09da0ec388e615
ms.sourcegitcommit: 9d1351ea6d9942550b52132817f9f9693ddef2fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "48830536"
---
# <a name="preset-security-policies-in-eop-and-office-365-atp"></a>Stratégies de sécurité prédéfinies dans EOP et Office 365 ATP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Les stratégies de sécurité prédéfinies fournissent un emplacement centralisé pour l’application de toutes les stratégies de courrier indésirable, de programmes malveillants et de hameçonnage recommandées aux utilisateurs en même temps. Les paramètres de stratégie ne sont pas configurables. Au lieu de cela, ils sont définis par nous et basés sur nos observations et expériences dans les centres de données pour un équilibre entre la conservation d’un contenu nuisible aux utilisateurs sans interrompre leur travail.

Le reste de cette rubrique décrit les stratégies de sécurité prédéfinies et leur configuration.

## <a name="what-preset-security-policies-are-made-of"></a>Quelles stratégies de sécurité prédéfinies sont établies

Les stratégies de sécurité prédéfinies se composent des éléments suivants :

- Profils
- Stratégies
- Paramètres de stratégie

Par ailleurs, l’ordre de priorité est important si plusieurs stratégies de sécurité prédéfinies et d’autres stratégies s’appliquent à la même personne.

### <a name="profiles-in-preset-security-policies"></a>Profils dans les stratégies de sécurité prédéfinies

Un profil détermine le niveau de protection. Les profils suivants sont disponibles :

- **Protection standard** : profil de protection de base adapté à la plupart des utilisateurs.
- **Protection stricte** : un profil de protection plus agressif pour les utilisateurs sélectionnés (cibles de valeur élevée ou utilisateurs prioritaires).

Vous utilisez des règles avec des conditions et des exceptions qui déterminent les personnes auxquelles les profils sont ou qui ne sont pas appliqués.

Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_ ). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_ ).

Les conditions et les exceptions disponibles sont les suivantes :

- **Les destinataires sont** : des boîtes aux lettres, des utilisateurs de messagerie ou des contacts de messagerie dans votre organisation.
- **Les destinataires sont membres de** : groupes de votre organisation.
- **Les domaines de destinataire sont** : domaines acceptés configurés dans Microsoft 365.

### <a name="policies-in-preset-security-policies"></a>Stratégies dans les stratégies de sécurité prédéfinies

Les stratégies de sécurité prédéfinies utilisent les stratégies correspondantes des différentes fonctionnalités de protection dans EOP et Office 365 ATP. Ces stratégies sont créées _une fois_ que vous avez affecté aux utilisateurs les stratégies de sécurité **standard** ou prédéfinies protection **stricte** . Vous ne pouvez pas modifier ces stratégies.

- **Stratégies Exchange Online Protection (EoP)** : cela inclut les organisations Microsoft 365 avec les boîtes aux lettres Exchange Online et les organisations EOP autonomes sans boîtes aux lettres Exchange Online :
  
  - [Stratégies de blocage du courrier indésirable](configure-your-spam-filter-policies.md) nommées **stratégie de sécurité prédéfinie standard** et **stratégie de sécurité prédéfinie stricte** .
  - [Stratégies de protection contre les programmes malveillants](configure-anti-malware-policies.md) nommées **stratégie de sécurité** prédéfinie standard et **stratégie de sécurité prédéfinie stricte** .
  - [Stratégies de hameçonnage d’EOP](set-up-anti-phishing-policies.md#spoof-settings) nommées **stratégie de sécurité** prédéfinie standard et **stratégie de sécurité prédéfinie stricte** (paramètres d’usurpation).

- **Stratégies Office 365 Advanced Threat Protection (ATP)** : cela inclut les organisations avec les abonnements complémentaires Microsoft 365 E5 ou Office 365 ATP :

  - Stratégies anti-hameçonnage ATP nommées stratégie de sécurité prédéfinie **standard** et **stratégie de sécurité prédéfinie stricte** , qui incluent :

    - Les mêmes [paramètres d’usurpation](set-up-anti-phishing-policies.md#spoof-settings) qui sont disponibles dans les stratégies anti-hameçonnage EOP.
    - [Paramètres d’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-atp-anti-phishing-policies)
    - [Seuils de hameçonnage avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-atp-anti-phishing-policies)

  - [Stratégies de liens fiables](set-up-atp-safe-links-policies.md) nommées **stratégie de sécurité prédéfinie standard** et **stratégie de sécurité avec présélection stricte** .

  - [Stratégies de pièces jointes approuvées](set-up-atp-safe-attachments-policies.md) nommées **stratégie de sécurité prédéfinie standard** et **stratégie de sécurité avec présélection stricte** .

Notez que vous pouvez appliquer des protections EOP à différents utilisateurs que les protections ATP.

### <a name="policy-settings-in-preset-security-policies"></a>Paramètres de stratégie dans les stratégies de sécurité prédéfinies

Vous ne pouvez pas modifier les paramètres de stratégie dans les profils de protection. Les valeurs **standard** et **stricte** des paramètres de stratégie sont décrites dans la rubrique [paramètres recommandés pour la sécurité de l’ATP et d’Office 365](recommended-settings-for-eop-and-office365-atp.md).

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Ordre de priorité pour les stratégies de sécurité prédéfinies et les autres stratégies

Lorsque plusieurs stratégies sont appliquées à un utilisateur, l’ordre suivant est appliqué de la priorité la plus élevée à la priorité la plus faible :

1. Stratégie de sécurité prédéfinie de **protection stricte**
2. Stratégie de sécurité prédéfinie **protection standard**
3. Stratégies de sécurité personnalisées
4. Stratégies de sécurité par défaut

En d’autres termes, les paramètres de la stratégie de **protection stricte** remplacent les paramètres de la stratégie de **protection standard** , qui remplace les paramètres d’une stratégie personnalisée, ce qui remplace les paramètres de la stratégie par défaut.

## <a name="assign-preset-security-policies-to-users"></a>Affecter des stratégies de sécurité prédéfinies aux utilisateurs

### <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **paramètres prédéfinis des stratégies de sécurité** , utilisez <https://protection.office.com/presetSecurityPolicies> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. décrites dans cette rubrique :

  - Pour configurer des stratégies de sécurité prédéfinies, vous devez être membre de l’un des groupes de rôles suivants :

    - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation** ou **Gestion de l’hygiène** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

  - Pour un accès en lecture seule aux stratégies de sécurité prédéfinies, vous devez être membre de l’un des groupes de rôles suivants :

    - **Lecteur de sécurité** dans le [Centre de conformité et sécurité](permissions-in-the-security-and-compliance-center.md).
    - Le **lecteur global** dans le [centre de sécurité & conformité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

### <a name="use-the-security--compliance-center-to-assign-preset-security-policies-to-users"></a>Utiliser le centre de sécurité & conformité pour affecter des stratégies de sécurité prédéfinies aux utilisateurs

1. Dans le centre de sécurité & conformité, accédez **Threat management** aux stratégies de \> **Policy** \> **sécurité prédéfinies** stratégie de gestion des menaces.

2. Sous **protection standard** ou **protection stricte** , cliquez sur **modifier** .

3. L’Assistant **appliquer la protection standard** ou **appliquer une protection stricte** démarre. Sur les **protections EOP s’appliquent à** l’étape, identifiez les destinataires internes auxquels les [protections EOP](#policies-in-preset-security-policies) s’appliquent :

   1. Cliquez sur **Ajouter une condition** . Dans la liste déroulante qui apparaît, sélectionnez une condition sous **appliqué si** :

      - **Les destinataires sont**
      - **Les destinataires sont membres de**
      - **Les domaines de destinataires sont**

      Vous ne pouvez utiliser une condition qu’une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition. Plusieurs valeurs de la même condition utilisent ou logique (par exemple, _\<recipient1\>_ ou _\<recipient2\>_ ).

   2. La condition que vous avez sélectionnée apparaît dans une section grisée. Dans cette section, cliquez dans la zone **une de ces** zones. Si vous patientez un moment, une liste s’affiche pour vous permettre de sélectionner une valeur. Sinon, vous pouvez commencer à taper une valeur pour filtrer la liste et sélectionner une valeur. Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur individuelle, cliquez sur **supprimer** ![ ](../../media/scc-remove-icon.png) l’icône de suppression sur la valeur. Pour supprimer l’ensemble de la condition, cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/scc-remove-icon.png) dans la condition.

   3. Pour ajouter une autre condition, cliquez sur **Ajouter une condition** , puis sélectionnez l’une des conditions restantes. Conditions d’utilisation et logique différentes (par exemple, _\<recipient1\>_ and _\<member of group 1\>_ ).

      Répétez l’étape précédente pour ajouter des valeurs à la condition, puis répétez cette étape autant de fois que nécessaire ou jusqu’à ce que les conditions soient insuffisantes.

   4. Pour ajouter une exception, cliquez sur **Ajouter une condition** . Dans la liste déroulante qui apparaît, sélectionnez une condition sous **sauf quand** . Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant** .

4. Si votre organisation dispose d’Office 365 ATP, les **protections contre les disponibilités s’appliquent à** l’étape pour identifier les destinataires internes auxquels les [protections ATP Office 365](#policies-in-preset-security-policies) s’appliquent.

   Les paramètres et le comportement sont les mêmes que les **protections EOP s’appliquent à** l’étape.

   Lorsque vous avez terminé, cliquez sur **Suivant** .

5. Dans l’étape **confirmer** , vérifiez vos sélections, puis cliquez sur **confirmer** .

### <a name="use-the-security--compliance-center-to-modify-the-assignments-of-preset-security-policies"></a>Utiliser le centre de sécurité & conformité pour modifier les affectations des stratégies de sécurité prédéfinies

Les étapes de modification de l’affectation de la stratégie de sécurité de protection **standard** ou de protection **stricte** sont les mêmes que lorsque vous avez initialement [affecté les stratégies de sécurité prédéfinies aux utilisateurs](#use-the-security--compliance-center-to-assign-preset-security-policies-to-users).

Pour désactiver les stratégies de **protection standard** ou de protection **stricte** tout en conservant les conditions et les exceptions existantes, faites glisser le bouton bascule sur **désactivé** . Pour activer les stratégies, faites glisser le bouton bascule sur **activé** .

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement attribué la **protection standard** ou une stratégie de sécurité **stricte** à un utilisateur, utilisez un paramètre de protection dont la valeur par défaut est différente de celle du paramètre **protection standard** , qui est différente du paramètre de protection **strict** .

Par exemple, pour le courrier électronique détecté comme courrier indésirable (pas de courrier indésirable à niveau de confiance élevé), vérifiez que le message est remis dans le dossier courrier indésirable pour les utilisateurs de **protection standard** et mis en quarantaine pour les utilisateurs de **protection stricte** .

Ou, pour le [courrier en masse](bulk-complaint-level-values.md), vérifiez que la valeur BCL 6 ou supérieure remet le message au dossier courrier indésirable pour les utilisateurs de **protection standard** et que la valeur BCL 4 ou supérieur met en quarantaine le message pour les utilisateurs de **protection stricte** .
