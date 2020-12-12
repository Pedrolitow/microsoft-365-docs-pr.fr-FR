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
description: Les administrateurs peuvent apprendre à appliquer des paramètres de stratégie standard et stricte dans les fonctionnalités de protection d’Exchange Online Protection (EOP) et de Microsoft Defender pour Office 365
ms.openlocfilehash: a77201835652fb36822fbc603f5211c1f7a9521b
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49659231"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365

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

- **Protection standard**: profil de protection de base adapté à la plupart des utilisateurs.
- **Protection stricte**: un profil de protection plus agressif pour les utilisateurs sélectionnés (cibles de valeur élevée ou utilisateurs prioritaires).

Vous utilisez des règles avec des conditions et des exceptions qui déterminent les personnes auxquelles les profils sont ou qui ne sont pas appliqués.

Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

Les conditions et les exceptions disponibles sont les suivantes :

- **Les destinataires sont**: des boîtes aux lettres, des utilisateurs de messagerie ou des contacts de messagerie dans votre organisation.
- **Les destinataires sont membres de**: groupes de votre organisation.
- **Les domaines de destinataire sont**: domaines acceptés configurés dans Microsoft 365.

### <a name="policies-in-preset-security-policies"></a>Stratégies dans les stratégies de sécurité prédéfinies

Les stratégies de sécurité prédéfinies utilisent les stratégies correspondantes des différentes fonctionnalités de protection dans EOP et Microsoft Defender pour Office 365. Ces stratégies sont créées _une fois_ que vous avez affecté aux utilisateurs les stratégies de sécurité **standard** ou prédéfinies protection **stricte** . Vous ne pouvez pas modifier ces stratégies.

- **Stratégies Exchange Online Protection (EoP)**: cela inclut les organisations Microsoft 365 avec les boîtes aux lettres Exchange Online et les organisations EOP autonomes sans boîtes aux lettres Exchange Online :

  - [Stratégies de blocage du courrier indésirable](configure-your-spam-filter-policies.md) nommées **stratégie de sécurité prédéfinie standard** et **stratégie de sécurité prédéfinie stricte**.
  - [Stratégies de protection contre les programmes malveillants](configure-anti-malware-policies.md) nommées **stratégie de sécurité** prédéfinie standard et **stratégie de sécurité prédéfinie stricte**.
  - [Stratégies de hameçonnage d’EOP](set-up-anti-phishing-policies.md#spoof-settings) nommées **stratégie de sécurité** prédéfinie standard et **stratégie de sécurité prédéfinie stricte** (paramètres d’usurpation).

- **Stratégies Microsoft Defender pour office 365**: cela inclut les organisations avec Microsoft 365 E5 ou Defender pour Office 365 abonnements complémentaires :

  - Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 nommé stratégie de **sécurité** prédéfinie standard et **stratégie de sécurité prédéfinie stricte**, notamment :

    - Les mêmes [paramètres d’usurpation](set-up-anti-phishing-policies.md#spoof-settings) qui sont disponibles dans les stratégies anti-hameçonnage EOP.
    - [Paramètres d’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Seuils de hameçonnage avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)

  - [Stratégies de liens fiables](set-up-atp-safe-links-policies.md) nommées **stratégie de sécurité prédéfinie standard** et **stratégie de sécurité avec présélection stricte**.

  - [Stratégies de pièces jointes approuvées](set-up-atp-safe-attachments-policies.md) nommées **stratégie de sécurité prédéfinie standard** et **stratégie de sécurité avec présélection stricte**.

Notez que vous pouvez appliquer des protections EOP à différents utilisateurs que les protections Microsoft Defender pour Office 365.

### <a name="policy-settings-in-preset-security-policies"></a>Paramètres de stratégie dans les stratégies de sécurité prédéfinies

Vous ne pouvez pas modifier les paramètres de stratégie dans les profils de protection. Les valeurs **standard** et **stricte** des paramètres de stratégie sont décrites dans [paramètres recommandés pour EOP et Microsoft Defender pour Office 365 Security](recommended-settings-for-eop-and-office365-atp.md).

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

- Pour pouvoir utiliser ce cmdlet, vous devez disposer des autorisations dans le centre de sécurité et conformité Office 365.
  - Pour configurer des stratégies de sécurité prédéfinies, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** .
  - Pour un accès en lecture seule aux stratégies de sécurité prédéfinies, vous devez être membre du groupe de rôles **lecteur global** .

  Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

  **Remarque**: l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le centre d’administration 365 de Microsoft donne aux utilisateurs les autorisations requises dans le centre de sécurité & conformité _et_ des autorisations pour d’autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

### <a name="use-the-security--compliance-center-to-assign-preset-security-policies-to-users"></a>Utiliser le centre de sécurité & conformité pour affecter des stratégies de sécurité prédéfinies aux utilisateurs

1. Dans le centre de sécurité & conformité, accédez  aux stratégies de \>  \> **sécurité prédéfinies** stratégie de gestion des menaces.

2. Sous **protection standard** ou **protection stricte**, cliquez sur **modifier**.

3. L’Assistant **appliquer la protection standard** ou **appliquer une protection stricte** démarre. Sur les **protections EOP s’appliquent à** l’étape, identifiez les destinataires internes auxquels les [protections EOP](#policies-in-preset-security-policies) s’appliquent :

   1. Cliquez sur **Ajouter une condition**. Dans la liste déroulante qui apparaît, sélectionnez une condition sous **appliqué si**:

      - **Les destinataires sont**
      - **Les destinataires sont membres de**
      - **Les domaines de destinataires sont**

      Vous ne pouvez utiliser une condition qu’une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition. Plusieurs valeurs de la même condition utilisent ou logique (par exemple, _\<recipient1\>_ ou _\<recipient2\>_ ).

   2. La condition que vous avez sélectionnée apparaît dans une section grisée. Dans cette section, cliquez dans la zone **une de ces** zones. Si vous patientez un moment, une liste s’affiche pour vous permettre de sélectionner une valeur. Sinon, vous pouvez commencer à taper une valeur pour filtrer la liste et sélectionner une valeur. Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur individuelle, cliquez sur **supprimer** ![ ](../../media/scc-remove-icon.png) l’icône de suppression sur la valeur. Pour supprimer l’ensemble de la condition, cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/scc-remove-icon.png) dans la condition.

   3. Pour ajouter une autre condition, cliquez sur **Ajouter une condition** , puis sélectionnez l’une des conditions restantes. Conditions d’utilisation et logique différentes (par exemple, _\<recipient1\>_ and _\<member of group 1\>_ ).

      Répétez l’étape précédente pour ajouter des valeurs à la condition, puis répétez cette étape autant de fois que nécessaire ou jusqu’à ce que les conditions soient insuffisantes.

   4. Pour ajouter une exception, cliquez sur **Ajouter une condition**. Dans la liste déroulante qui apparaît, sélectionnez une condition sous **sauf quand**. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Si votre organisation a Microsoft Defender pour Office 365, les **protections contre les disponibilités s’appliquent** à l’étape pour identifier les destinataires internes auxquels les [protections Microsoft defender pour Office 365](#policies-in-preset-security-policies) s’appliquent.

   Les paramètres et le comportement sont les mêmes que les **protections EOP s’appliquent à** l’étape.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans l’étape **confirmer** , vérifiez vos sélections, puis cliquez sur **confirmer**.

### <a name="use-the-security--compliance-center-to-modify-the-assignments-of-preset-security-policies"></a>Utiliser le centre de sécurité & conformité pour modifier les affectations des stratégies de sécurité prédéfinies

Les étapes de modification de l’affectation de la stratégie de sécurité de protection **standard** ou de protection **stricte** sont les mêmes que lorsque vous avez initialement [affecté les stratégies de sécurité prédéfinies aux utilisateurs](#use-the-security--compliance-center-to-assign-preset-security-policies-to-users).

Pour désactiver les stratégies de **protection standard** ou de protection **stricte** tout en conservant les conditions et les exceptions existantes, faites glisser le bouton bascule sur **désactivé**. Pour activer les stratégies, faites glisser le bouton bascule sur **activé**.

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement attribué la **protection standard** ou une stratégie de sécurité **stricte** à un utilisateur, utilisez un paramètre de protection dont la valeur par défaut est différente de celle du paramètre **protection standard** , qui est différente du paramètre de protection **strict** .

Par exemple, pour le courrier électronique détecté comme courrier indésirable (pas de courrier indésirable à niveau de confiance élevé), vérifiez que le message est remis dans le dossier courrier indésirable pour les utilisateurs de **protection standard** et mis en quarantaine pour les utilisateurs de **protection stricte** .

Ou, pour le [courrier en masse](bulk-complaint-level-values.md), vérifiez que la valeur BCL 6 ou supérieure remet le message au dossier courrier indésirable pour les utilisateurs de **protection standard** et que la valeur BCL 4 ou supérieur met en quarantaine le message pour les utilisateurs de **protection stricte** .
