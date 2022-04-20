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
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Les administrateurs peuvent apprendre à appliquer des paramètres de stratégie standard et strict aux fonctionnalités de protection de Exchange Online Protection (EOP) et Microsoft Defender pour Office 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 01fd969461b47b0208dcfd20ff608e829b6a3336
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64915970"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les stratégies de sécurité prédéfinies fournissent un emplacement centralisé pour appliquer toutes les stratégies de courrier indésirable, de programmes malveillants et de hameçonnage recommandées aux utilisateurs en même temps. Les paramètres de stratégie ne sont pas configurables. Au lieu de cela, ils sont définis par nous et sont basés sur nos observations et expériences dans les centres de données pour un équilibre entre le maintien du contenu nocif loin des utilisateurs et d’éviter les interruptions inutiles.

Le reste de cet article décrit les stratégies de sécurité prédéfinies et comment les configurer.

## <a name="what-preset-security-policies-are-made-of"></a>Quelles sont les stratégies de sécurité prédéfinies ?

Les stratégies de sécurité prédéfinies se composent des éléments suivants :

- Profils
- Stratégies
- Paramètres de stratégie

En outre, l’ordre de priorité est important si plusieurs stratégies de sécurité prédéfinies et d’autres stratégies s’appliquent à la même personne.

### <a name="profiles-in-preset-security-policies"></a>Profils dans les stratégies de sécurité prédéfinies

Un profil détermine le niveau de protection. Les profils suivants sont disponibles :

- **Protection standard** : profil de protection de base de référence adapté à la plupart des utilisateurs.
- **Protection stricte** : profil de protection plus agressif pour les utilisateurs sélectionnés (cibles à valeur élevée ou utilisateurs prioritaires).

  pour **la protection standard** et **la protection stricte**, vous utilisez des règles avec des conditions et des exceptions pour déterminer les destinataires internes auxquels la stratégie s’applique (conditions de destinataire).

  Les conditions et exceptions disponibles sont les suivantes :

  - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés.
  - **Groupes** :
    - Les membres des groupes de distribution ou des groupes de sécurité activés par courrier spécifiés.
    - Groupes Microsoft 365 spécifiée
  - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

  Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

- **Protection intégrée** (Defender pour Office 365 uniquement) : profil qui active uniquement la protection des liens Coffre et des pièces jointes Coffre. Ce profil fournit efficacement des stratégies par défaut pour les liens Coffre et les pièces jointes Coffre, qui n’ont jamais eu de stratégies par défaut.

  Pour **la protection intégrée**, la stratégie de sécurité prédéfinies est activée par défaut pour tous les clients Defender pour Office 365. Bien que nous ne le recommandons pas, vous pouvez également configurer des exceptions en fonction des **utilisateurs**, **des groupes** et **des domaines** afin que la protection ne soit pas appliquée à des utilisateurs spécifiques.

Tant que vous n’affectez pas les stratégies aux utilisateurs, les stratégies de sécurité prédéfinies **Standard** et **Strict** ne sont affectées à personne. En revanche, la stratégie de sécurité prédéfinies de **protection intégrée** est affectée par défaut à tous les destinataires, mais vous pouvez configurer des exceptions.

### <a name="policies-in-preset-security-policies"></a>Stratégies dans les stratégies de sécurité prédéfinies

Les stratégies de sécurité prédéfinies utilisent les stratégies correspondantes des différentes fonctionnalités de protection dans EOP et Microsoft Defender pour Office 365. Ces stratégies sont créées _une fois_ que vous avez affecté les stratégies de sécurité prédéfinies **de protection standard** ou **strict** aux utilisateurs. Vous ne pouvez pas modifier les paramètres de ces stratégies.

- **Stratégies Exchange Online Protection (EOP)** : cela inclut les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online et des organisations EOP autonomes sans boîtes aux lettres Exchange Online :

  - [Stratégies anti-courrier indésirable nommées](configure-your-spam-filter-policies.md) **Stratégie de sécurité prédéfinies standard** et **Stratégie de sécurité prédéfinies strictes**.
  - [Stratégies anti-programme malveillant nommées](configure-anti-malware-policies.md) **stratégie de sécurité prédéfinies standard** et **stratégie de sécurité prédéfinies strictes**.
  - [Stratégies anti-hameçonnage EOP nommées](set-up-anti-phishing-policies.md#spoof-settings) Stratégie **de sécurité prédéfinie standard** et **Stratégie de sécurité prédéfinie stricte** (paramètres d’usurpation d’identité).

  > [!NOTE]
  > Les stratégies de courrier indésirable sortant ne font pas partie des stratégies de sécurité prédéfinies. La stratégie de courrier indésirable sortant par défaut protège automatiquement les membres des stratégies de sécurité prédéfinies. Vous pouvez également créer des stratégies de courrier indésirable sortant personnalisées pour personnaliser la protection des membres des stratégies de sécurité prédéfinies. Pour plus d’informations, consultez [Configurer le filtrage du courrier indésirable sortant dans EOP](configure-the-outbound-spam-policy.md).

- **Microsoft Defender pour Office 365 stratégies** : cela inclut les organisations avec des abonnements Microsoft 365 E5 ou Defender pour Office 365 module complémentaire :
  - Les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 nommées **stratégie de sécurité prédéfinies standard** et stratégie **de sécurité prédéfinies strictes**, qui incluent :
    - Paramètres [d’usurpation d’identité disponibles](set-up-anti-phishing-policies.md#spoof-settings) dans les stratégies anti-hameçonnage EOP.
    - [Paramètres d’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Seuils d’hameçonnage avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Coffre lie les stratégies nommées](set-up-safe-links-policies.md) **Stratégie de sécurité prédéfinies standard**, **Stratégie de sécurité prédéfinies stricte** et **Stratégie de protection intégrée**.
  - [Coffre stratégies de pièces jointes nommées](set-up-safe-attachments-policies.md) Stratégie **de sécurité prédéfinies standard**, **Stratégie de sécurité prédéfinies stricte** et **Stratégie de protection intégrée**.

Vous pouvez appliquer des protections EOP à des utilisateurs différents des protections Microsoft Defender pour Office 365.

### <a name="policy-settings-in-preset-security-policies"></a>Paramètres de stratégie dans les stratégies de sécurité prédéfinies

Vous ne pouvez pas modifier les paramètres de stratégie dans les profils de protection. Les valeurs des paramètres de **stratégie de protection** **standard**, **strict** et intégré sont décrites dans [les paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](recommended-settings-for-eop-and-office365.md).

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Ordre de priorité pour les stratégies de sécurité prédéfinies et autres stratégies

Lorsque plusieurs stratégies sont appliquées à un utilisateur, l’ordre suivant est appliqué de la priorité la plus élevée à la priorité la plus basse :

1. Stratégie de sécurité prédéfinies de **protection stricte**
2. Stratégie de sécurité prédéfinies de **protection standard**
3. Stratégies de sécurité personnalisées
4. **Stratégie de sécurité prédéfinies de protection intégrée** et stratégies de sécurité par défaut

En d’autres termes, les paramètres de la **stratégie de protection stricte** remplacent les paramètres de la stratégie de **protection Standard**, qui remplace les paramètres d’une stratégie personnalisée, qui remplace les paramètres de la stratégie de sécurité prédéfinies de **protection intégrée** (Coffre Liens et pièces jointes Coffre) et de la stratégie par défaut (anti-spam, anti-programmes malveillants et anti-hameçonnage).

Par exemple, si un paramètre de sécurité existe dans **la protection Standard** et qu’un administrateur a activé la **protection Standard** pour un utilisateur, le paramètre de **protection Standard** est appliqué au lieu de ce qui est configuré pour ce paramètre dans une stratégie personnalisée ou dans la stratégie par défaut (pour le même utilisateur). Notez que vous pouvez avoir une partie de votre organisation à laquelle vous souhaitez appliquer uniquement la stratégie de **protection** **standard** ou stricte tout en appliquant une stratégie personnalisée à d’autres utilisateurs de votre organisation pour répondre à des besoins spécifiques.

**La protection intégrée** n’affecte pas les destinataires dans les stratégies de liens Coffre ou de pièces jointes Coffre existantes. Si vous avez déjà configuré la **protection standard**, la **protection stricte** ou les liens Coffre personnalisés ou les stratégies de Coffre pièces jointes, ces stratégies sont _toujours_ appliquées _avant_ la **protection intégrée**, de sorte qu’il n’y a aucun impact sur les destinataires qui sont déjà définis dans ces stratégies prédéfinies ou personnalisées existantes.

## <a name="assign-preset-security-policies-to-users"></a>Affecter des stratégies de sécurité prédéfinies aux utilisateurs

### <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Stratégies de sécurité prédéfinies** , utilisez <https://security.microsoft.com/presetSecurityPolicies>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cette rubrique.
  - Pour configurer des stratégies de sécurité prédéfinies, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour accéder en lecture seule aux stratégies de sécurité prédéfinies, vous devez être membre du groupe de **rôles Lecteur général** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarque** : l’ajout d’utilisateurs au rôle de Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations nécessaires pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Utiliser le portail Microsoft 365 Defender pour affecter des stratégies de sécurité prédéfinies Standard et Strict aux utilisateurs

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Preset Security Policies** dans la section **Stratégies modèles**. Pour accéder directement à la page **Stratégies de sécurité prédéfinies** , utilisez <https://security.microsoft.com/presetSecurityPolicies>.

2. Dans la page **Stratégies de sécurité prédéfinies** , cliquez sur **Gérer** dans les sections **Protection standard** ou **Protection stricte** .

3. L’Assistant **Appliquer la protection standard** ou **Appliquer une protection stricte** démarre dans un menu volant. Dans les **protections EOP s’appliquent à** la page, identifiez les destinataires internes auxquels les [protections EOP](#policies-in-preset-security-policies) s’appliquent (conditions de destinataire) :
   - **Utilisateurs**
   - **Groupes**
   - **Domaines**

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identifiants (nom, nom d'affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant est affiché dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour voir toutes les valeurs disponibles.

   - **Exclure ces utilisateurs, groupes et domaines** : Pour ajouter des exceptions pour les destinataires internes auxquels la stratégie s'applique (exceptions des destinataires), sélectionnez cette option et configurez les exceptions. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans Microsoft Defender pour Office 365 organisations, vous êtes redispilé dans les **Defender pour Office 365 protections s’appliquent à** la page pour identifier les destinataires internes auxquels les [protections Microsoft Defender pour Office 365](#policies-in-preset-security-policies) s’appliquent vers (conditions du destinataire).

   Les paramètres et le comportement sont exactement comme les **protections EOP s’appliquent à** la page de l’étape précédente.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Vérifier et confirmer vos modifications** , vérifiez vos sélections, puis cliquez sur **Confirmer**.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Utiliser le portail Microsoft 365 Defender pour modifier les affectations de stratégies de sécurité prédéfinies Standard et Strict

Les étapes de modification de l’affectation de la **stratégie de sécurité de protection standard** ou **de protection stricte** sont les mêmes que lorsque vous [avez initialement affecté les stratégies de sécurité prédéfinies aux utilisateurs](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

Pour désactiver la **protection standard** ou les stratégies de sécurité prédéfinies de **protection stricte** tout en conservant les conditions et exceptions existantes, faites glisser le bouton bascule vers **désactivé**![](../../media/scc-toggle-off.png). Pour activer les stratégies, faites glisser le bouton bascule sur **Activé** ![activé](../../media/scc-toggle-on.png).

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Utiliser le portail Microsoft 365 Defender pour modifier les affectations de la stratégie de sécurité prédéfinies de protection intégrée

N’oubliez pas que la stratégie de sécurité prédéfinie de **protection intégrée** est affectée à tous les destinataires et n’affecte pas les destinataires définis dans les stratégies de sécurité prédéfinies de **protection standard** ou **stricte**, ni les liens Coffre personnalisés ou les stratégies de pièces jointes Coffre.

Par conséquent, nous ne recommandons généralement pas d’exceptions à la stratégie de sécurité prédéfinies de **protection intégrée** .

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Preset Security Policies** dans la section **Stratégies modèles**. Pour accéder directement à la page **Stratégies de sécurité prédéfinies** , utilisez <https://security.microsoft.com/presetSecurityPolicies>.

2. Dans la page **Stratégies de sécurité prédéfinies** , **sélectionnez Ajouter des exclusions (non recommandé)** dans la section **Protection intégrée** .

3. Dans le menu volant **Exclure de la protection intégrée** qui s’affiche, identifiez les destinataires internes exclus de la protection intégrée Coffre Liens et pièces jointes Coffre :
   - **Utilisateurs**
   - **Groupes**
   - **Domaines**

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identifiants (nom, nom d'affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant est affiché dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour voir toutes les valeurs disponibles.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement affecté la stratégie de **sécurité de protection standard** ou **stricte** à un utilisateur, utilisez un paramètre de protection où la valeur par défaut est différente du paramètre de **protection Standard** , qui est différent du paramètre **de protection strict** .

Par exemple, pour les e-mails détectés comme courrier indésirable (courrier indésirable non fiable), vérifiez que le message est remis au dossier Courrier indésirable pour les utilisateurs de **la protection Standard** et mis en quarantaine pour les utilisateurs de **la protection stricte** .

Ou, pour le [courrier en bloc](bulk-complaint-level-values.md), vérifiez que la valeur BCL 6 ou supérieure remet le message au dossier Courrier indésirable pour les utilisateurs de **protection Standard** , et que la valeur BCL 4 ou supérieure met le message en quarantaine pour les utilisateurs de **la protection stricte** .
