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
- m365-security
ms.custom: ''
description: Les administrateurs peuvent apprendre à appliquer les paramètres de stratégie Standard et Strict dans les fonctionnalités de protection de Exchange Online Protection (EOP) et Microsoft Defender pour Office 365
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: b28c315ecfe8ee6513c8f45be6d89953d4908647
ms.sourcegitcommit: 0ca3ab2abe07810e9b2cc2d806e3c6b9f35b146c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68684759"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les stratégies de sécurité prédéfinies fournissent un emplacement centralisé pour appliquer toutes les stratégies recommandées de courrier indésirable, de programme malveillant et d’hameçonnage aux utilisateurs à la fois. Les paramètres de stratégie ne sont pas configurables. Au lieu de cela, ils sont définis par nous et sont basés sur nos observations et expériences dans les centres de données pour un équilibre entre le maintien du contenu nuisible à l’écart des utilisateurs et l’évitement des interruptions inutiles.

Le reste de cet article décrit les stratégies de sécurité prédéfinies et comment les configurer.

## <a name="what-preset-security-policies-are-made-of"></a>Quelles stratégies de sécurité prédéfinies sont constituées

Les stratégies de sécurité prédéfinies se composent des éléments suivants :

- Profils
- Stratégies
- Paramètres de stratégie

En outre, l’ordre de priorité est important si plusieurs stratégies de sécurité prédéfinies et d’autres stratégies s’appliquent à la même personne.

### <a name="profiles-in-preset-security-policies"></a>Profils dans les stratégies de sécurité prédéfinies

Un profil détermine le niveau de protection. Les profils suivants sont disponibles :

- **Protection standard** : profil de protection de base de référence adapté à la plupart des utilisateurs.
- **Protection stricte** : profil de protection plus agressif pour les utilisateurs sélectionnés (cibles à valeur élevée ou utilisateurs prioritaires).

  Pour **protection standard** et **protection stricte**, vous utilisez des règles avec des conditions et des exceptions pour déterminer les destinataires internes auxquels la stratégie s’applique (conditions de destinataire).

  Les conditions et exceptions disponibles sont les suivantes :

  - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés.
  - **Groupes** :
    - Les membres des groupes de distribution ou des groupes de sécurité activés par courrier spécifiés.
    - Groupes Microsoft 365 spécifiée

    > [!NOTE]
    >  Les groupes de distribution dynamiques ne sont pas pris en charge.

  - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

  Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

  > [!IMPORTANT]
  > Plusieurs types de conditions ou exceptions différentes ne sont pas cumulatives ; elles sont inclusives. La stratégie de sécurité prédéfinie est appliquée _uniquement_ aux destinataires qui correspondent à _tous les_ filtres de destinataires spécifiés. Par exemple, vous configurez une condition de filtre de destinataire dans la stratégie avec les valeurs suivantes :
  >
  > - Utilisateurs : romain@contoso.com
  > - Groupes : Cadres
  >
  > La stratégie s'applique à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie ne lui est pas appliquée.
  >
  > De même, si vous utilisez le même filtre de destinataires comme exception à la stratégie, la stratégie n'est pas appliquée à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie s’applique toujours à lui.

- **Protection intégrée** (Defender pour Office 365 uniquement) : profil qui active uniquement la protection des liens fiables et des pièces jointes fiables. Ce profil fournit efficacement des stratégies par défaut pour les liens fiables et les pièces jointes fiables, qui n’avaient jamais de stratégies par défaut.

  Pour la **protection intégrée**, la stratégie de sécurité prédéfinie est activée par défaut pour tous les clients Defender pour Office 365. Bien que nous ne le recommandons pas, vous pouvez également configurer des exceptions en fonction des **utilisateurs**, **des groupes** et **des domaines** afin que la protection ne soit pas appliquée à des utilisateurs spécifiques.

Tant que vous n’affectez pas les stratégies aux utilisateurs, les stratégies de sécurité **prédéfinies Standard** et **Strict** ne sont affectées à personne. En revanche, la stratégie de sécurité prédéfinie **de protection intégrée** est affectée à tous les destinataires par défaut, mais vous pouvez configurer des exceptions.

### <a name="policies-in-preset-security-policies"></a>Stratégies dans les stratégies de sécurité prédéfinies

Les stratégies de sécurité prédéfinies utilisent les stratégies correspondantes des différentes fonctionnalités de protection dans EOP et Microsoft Defender pour Office 365. Ces stratégies sont créées _après_ avoir affecté les stratégies de sécurité **prédéfinies protection standard** ou **protection stricte** aux utilisateurs. Vous ne pouvez pas modifier les paramètres de ces stratégies.

- **stratégies Exchange Online Protection (EOP)** : ces stratégies se trouvent dans toutes les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online et des organisations EOP autonomes sans boîtes aux lettres Exchange Online :

  - [Stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md) nommées **Stratégie de sécurité prédéfinie standard** et **Stratégie de sécurité prédéfinie stricte**.
  - [Stratégies anti-programmes malveillants](configure-anti-malware-policies.md) nommées **Stratégie de sécurité prédéfinie standard** et **Stratégie de sécurité prédéfinie stricte**.
  - [Stratégies anti-hameçonnage (protection contre l’usurpation d’identité)](set-up-anti-phishing-policies.md#spoof-settings) nommées **Stratégie de sécurité prédéfinie standard** et **Stratégie de sécurité prédéfinie stricte** (paramètres d’usurpation d’identité).

  > [!NOTE]
  > Les stratégies de courrier indésirable sortant ne font pas partie des stratégies de sécurité prédéfinies. La stratégie de courrier indésirable sortant par défaut protège automatiquement les membres des stratégies de sécurité prédéfinies. Vous pouvez également créer des stratégies de courrier indésirable sortant personnalisées pour personnaliser la protection des membres des stratégies de sécurité prédéfinies. Pour plus d’informations, consultez [Configurer le filtrage du courrier indésirable sortant dans EOP](configure-the-outbound-spam-policy.md).

- **Microsoft Defender pour Office 365 stratégies** : ces stratégies se trouvent dans les organisations disposant d’abonnements Microsoft 365 E5 ou Defender pour Office 365 modules complémentaires :
  - Les stratégies anti-hameçonnage dans Defender pour Office 365 **nommées Stratégie de sécurité prédéfinie standard et Stratégie** de **sécurité prédéfinie stricte**, qui incluent :
    - Les mêmes [paramètres d’usurpation d’identité](set-up-anti-phishing-policies.md#spoof-settings) qui sont disponibles dans les stratégies anti-hameçonnage EOP.
    - [Paramètres d’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Seuils d’hameçonnage avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Stratégies de liens fiables](set-up-safe-links-policies.md) nommées **Stratégie de sécurité prédéfinie standard**, **Stratégie de sécurité prédéfinie stricte** et **Stratégie de protection intégrée**.
  - [Stratégies de pièces jointes sécurisées nommées](set-up-safe-attachments-policies.md) **Stratégie de sécurité prédéfinie standard**, **Stratégie de sécurité prédéfinie stricte** et **Stratégie de protection intégrée**.

Vous pouvez appliquer des protections EOP à d’autres utilisateurs que les protections Defender pour Office 365, ou vous pouvez appliquer EOP et Defender pour Office 365 aux mêmes destinataires.

### <a name="policy-settings-in-preset-security-policies"></a>Paramètres de stratégie dans les stratégies de sécurité prédéfinies

Vous ne pouvez pas modifier les paramètres de stratégie dans les profils de protection. Les valeurs des paramètres de stratégie **de protection Standard**, **Strict** et **Intégrée** sont décrites dans [Paramètres recommandés pour la sécurité EOP et Microsoft Defender pour Office 365](recommended-settings-for-eop-and-office365.md).

> [!NOTE]
> Dans Defender pour Office 365 protections, vous devez identifier les expéditeurs pour la [protection contre l’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) utilisateur et les domaines internes ou externes pour la [protection contre l’emprunt d’identité de domaine](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).
>
> Tous les domaines que vous possédez ([domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)) reçoivent automatiquement la protection contre l’emprunt d’identité de domaine dans les stratégies de sécurité prédéfinies.
>
> Tous les destinataires reçoivent automatiquement une protection contre l’emprunt d’identité de [l’intelligence des boîtes aux lettres](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) dans les stratégies de sécurité prédéfinies.

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Ordre de priorité pour les stratégies de sécurité prédéfinies et d’autres stratégies

Lorsque plusieurs stratégies sont appliquées à un utilisateur, l’ordre suivant est appliqué de la priorité la plus élevée à la priorité la plus basse :

1. Stratégie de sécurité prédéfinie stricte.
2. Stratégie de sécurité prédéfinie standard.
3. Stratégies personnalisées. Les stratégies personnalisées sont appliquées en fonction de la valeur de priorité de la stratégie.
4. Stratégie de sécurité prédéfinie de protection intégrée pour les liens fiables et les pièces jointes fiables ; stratégies par défaut pour les programmes malveillants, anti-courrier indésirable et anti-hameçonnage.

En d’autres termes, les paramètres de la stratégie de sécurité prédéfinie **Strict** remplacent les paramètres de la stratégie de sécurité prédéfinie **Standard** , qui remplace les paramètres de toutes les stratégies personnalisées, qui remplacent les paramètres de la stratégie de sécurité prédéfinie **de protection intégrée** pour les liens fiables et les pièces jointes fiables, ainsi que les stratégies par défaut pour l’anti-courrier indésirable, les programmes malveillants et l’anti-hameçonnage.

Par exemple, un paramètre de sécurité existe dans **la protection Standard** et un administrateur spécifie un utilisateur pour la **protection Standard**. Le paramètre **de protection Standard** est appliqué à l’utilisateur au lieu de ce qui est configuré pour ce paramètre dans une stratégie personnalisée ou dans la stratégie par défaut pour le même utilisateur.

Vous pouvez appliquer les stratégies de sécurité **prédéfinies Standard** ou **Strict** à un sous-ensemble d’utilisateurs, et appliquer des stratégies personnalisées à d’autres utilisateurs de votre organisation pour répondre à des besoins spécifiques. Pour répondre à cette exigence, procédez comme suit :

- Configurez les utilisateurs qui doivent obtenir les paramètres de la stratégie de sécurité prédéfinie **Standard** et des stratégies personnalisées en tant qu’exceptions dans la stratégie de sécurité prédéfinie **Strict** .
- Configurez les utilisateurs qui doivent obtenir les paramètres des stratégies personnalisées en tant qu’exceptions dans la stratégie de sécurité prédéfinie **Standard** .

**La protection intégrée** n’affecte pas les destinataires dans les stratégies de liens fiables ou de pièces jointes fiables existantes. Si vous avez déjà configuré **protection standard**, **protection stricte** , liens fiables personnalisés ou pièces jointes fiables, ces stratégies sont _toujours_ appliquées _avant_ la **protection intégrée**, de sorte qu’il n’y a aucun impact sur les destinataires qui sont déjà définis dans ces stratégies prédéfinies ou personnalisées existantes.

## <a name="assign-preset-security-policies-to-users"></a>Affecter des stratégies de sécurité prédéfinies aux utilisateurs

### <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Stratégies de sécurité prédéfinies** , utilisez <https://security.microsoft.com/presetSecurityPolicies>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cette rubrique.
  - Pour configurer des stratégies de sécurité prédéfinies, vous devez être membre des groupes de rôles **Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour accéder en lecture seule aux stratégies de sécurité prédéfinies, vous devez être membre du groupe de rôles **Lecteur global** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarque** : l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations requises pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Utiliser le portail Microsoft 365 Defender pour affecter des stratégies de sécurité prédéfinies Standard et Strict aux utilisateurs

1. Dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>, accédez à **Email & Stratégies de collaboration** \> **& Règles** \> **Stratégies** \> de **menace prédéfinies Stratégies de sécurité prédéfinies** dans la section **Stratégies modèles**. Pour accéder directement à la page **Stratégies de sécurité prédéfinies** , utilisez <https://security.microsoft.com/presetSecurityPolicies>.

2. Dans la page **Stratégies de sécurité prédéfinies** , cliquez sur **Gérer** dans les sections **Protection standard** ou **Protection stricte** .

3. L’Assistant **Appliquer une protection standard** ou **Appliquer une protection stricte** démarre dans un menu volant.

   Dans la page **Appliquer Exchange Online Protection**, identifiez les destinataires internes [auxquels les protections EOP](#policies-in-preset-security-policies) s’appliquent (conditions de destinataire) :
   - **Tous les destinataires**
   - **Destinataires spécifiques** :
     - **Utilisateurs**
     - **Groupes** :
       - Les membres des groupes de distribution ou des groupes de sécurité activés par courrier spécifiés.
       - Groupes Microsoft 365 spécifiée

       Les groupes de distribution dynamiques ne sont pas pris en charge.

   - **Domaines**

     Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

     For users or groups, you can use most identifiers (name, display name, alias, email address, account name, etc.), but the corresponding display name is shown in the results. For users, enter an asterisk (\*) by itself to see all available values.

   - **Aucune**

   - **Exclure ces destinataires** : pour ajouter des exceptions pour les destinataires internes auxquels la stratégie s’applique (exceptions de destinataire), sélectionnez cette option et configurez les exceptions. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

   > [!NOTE]
   > Dans les organisations sans Defender pour Office 365, cliquez sur **Suivant** pour accéder à la page **Révision**. Les étapes/pages restantes avant la page **Révision** sont disponibles uniquement dans les organisations disposant de Defender pour Office 365.

4. Dans la page **Appliquer la protection Defender pour Office 365**, identifiez les destinataires internes [auxquels les protections Defender pour Office 365](#policies-in-preset-security-policies) s’appliquent (conditions de destinataire).

   Les paramètres et le comportement sont exactement comme les **protections EOP s’appliquent à** la page à l’étape précédente.

   Vous pouvez également sélectionner **Destinataires précédemment sélectionnés** pour utiliser les mêmes destinataires que ceux que vous avez sélectionnés pour la protection EOP sur la page précédente.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Protection contre l’emprunt d’identité** , cliquez sur **Suivant**.

6. Dans la page **Ajouter des adresses e-mail à signaler en cas d’emprunt d’identité par des attaquants** , ajoutez les expéditeurs internes et externes qui sont protégés par la [protection contre l’emprunt d’identité des utilisateurs](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   > [!NOTE]
   > Tous les destinataires reçoivent automatiquement une protection contre l’emprunt d’identité de [l’intelligence des boîtes aux lettres](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) dans les stratégies de sécurité prédéfinies.

   Chaque entrée se compose d’un nom d’affichage et d’une adresse e-mail. Entrez chaque valeur dans les zones, puis cliquez sur **Ajouter**. Répétez cette étape autant de fois que nécessaire.

   Vous pouvez spécifier un maximum de 301 utilisateurs, et vous ne pouvez pas spécifier le même utilisateur dans les paramètres de protection contre l’emprunt d’identité d’utilisateur dans plusieurs stratégies.

   Pour supprimer une entrée existante de la liste, cliquez sur ![Supprimer l’utilisateur de l’icône de protection contre l’emprunt d’identité.](../../media/m365-cc-sc-remove.png).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

7. Dans la page **Ajouter des domaines à marquer en cas d’emprunt d’identité par des attaquants** , ajoutez des domaines internes et externes protégés par la [protection contre l’emprunt d’identité de domaine](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   > [!NOTE]
   > Tous les domaines que vous possédez ([domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)) reçoivent automatiquement la protection contre l’emprunt d’identité de domaine dans les stratégies de sécurité prédéfinies.

   Tous les expéditeurs des domaines spécifiés sont protégés par la protection contre l’emprunt d’identité de domaine.

   Entrez le domaine dans la zone, puis cliquez sur **Ajouter**. Répétez cette étape autant de fois que nécessaire.

   Pour supprimer une entrée existante de la liste, sélectionnez-la, puis cliquez sur ![Supprimer le domaine de l’icône de protection contre l’emprunt d’identité.](../../media/m365-cc-sc-remove.png).

   Le nombre maximal de domaines que vous pouvez spécifier pour la protection contre l’emprunt d’identité de domaine dans toutes les stratégies anti-hameçonnage est de 50.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

8. Dans la page **Ajouter des adresses e-mail et des domaines approuvés à ne pas marquer comme emprunt d’identité** , entrez les adresses e-mail et les domaines de l’expéditeur que vous souhaitez exclure de la protection contre l’emprunt d’identité. Les messages de ces expéditeurs ne seront jamais marqués comme une attaque d’emprunt d’identité, mais les expéditeurs sont toujours analysés par d’autres filtres dans EOP et Defender pour Office 365.

   Entrez l’adresse e-mail ou le domaine dans la zone, puis cliquez sur **Ajouter**. Répétez cette étape autant de fois que nécessaire.

   Pour supprimer une entrée existante de la liste, sélectionnez-la, puis cliquez sur ![Supprimer les exceptions à l’icône de protection contre l’emprunt d’identité.](../../media/m365-cc-sc-remove.png).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

9. Dans la page **Vérifier et confirmer cette stratégie** , vérifiez vos sélections, puis cliquez sur **Confirmer**.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Utiliser le portail Microsoft 365 Defender pour modifier les affectations des stratégies de sécurité prédéfinies Standard et Strict

Les étapes pour modifier l’attribution de la stratégie de sécurité prédéfinie **protection standard** ou **protection stricte** sont les mêmes que lorsque vous [avez initialement affecté les stratégies de sécurité prédéfinies aux utilisateurs](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

Pour désactiver les stratégies de sécurité **prédéfinies protection standard** ou **Protection stricte** tout en conservant les conditions et exceptions existantes, faites glisser le bouton bascule sur **Désactivé**![](../../media/scc-toggle-off.png). Pour activer les stratégies, faites glisser le bouton bascule sur **Activé**![](../../media/scc-toggle-on.png).

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Utiliser le portail Microsoft 365 Defender pour modifier les affectations de la stratégie de sécurité prédéfinie de protection intégrée

N’oubliez pas que la stratégie de sécurité prédéfinie de **protection intégrée** est affectée à tous les destinataires et n’affecte pas les destinataires qui sont définis dans les stratégies de sécurité **prédéfinies protection standard** ou **protection stricte** , ni les stratégies personnalisées de liens fiables ou de pièces jointes fiables.

Par conséquent, nous ne recommandons généralement pas d’exceptions à la stratégie de sécurité prédéfinie **de protection intégrée** .

1. Dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>, accédez à **Email & Stratégies de collaboration** \> **& Règles** \> **Stratégies** \> de **menace prédéfinies Stratégies de sécurité prédéfinies** dans la section **Stratégies modèles**. Pour accéder directement à la page **Stratégies de sécurité prédéfinies** , utilisez <https://security.microsoft.com/presetSecurityPolicies>.

2. Dans la page **Stratégies de sécurité prédéfinies** , sélectionnez **Ajouter des exclusions (non recommandé)** dans la section **Protection intégrée** .

3. Dans le menu volant **Exclure de la protection intégrée** qui s’affiche, identifiez les destinataires internes exclus de la protection intégrée liens fiables et pièces jointes fiables :
   - **Utilisateurs**
   - **Groupes** :
       - Les membres des groupes de distribution ou des groupes de sécurité activés par courrier spécifiés.
       - Groupes Microsoft 365 spécifiée

     Les groupes de distribution dynamiques ne sont pas pris en charge.

   - **Domaines**

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Supprimer les exclusions de l’icône protection intégrée.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   For users or groups, you can use most identifiers (name, display name, alias, email address, account name, etc.), but the corresponding display name is shown in the results. For users, enter an asterisk (\*) by itself to see all available values.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement affecté la stratégie de sécurité **Protection standard** ou **Protection stricte** à un utilisateur, utilisez un paramètre de protection où la valeur par défaut est différente du paramètre **de protection Standard** , qui est différent de celui du paramètre **Protection stricte** .

Par exemple, pour les e-mails détectés comme courrier indésirable (courrier indésirable non à haut niveau de confiance), vérifiez que le message est remis au dossier Email de courrier indésirable pour les utilisateurs de **la protection Standard** et mis en quarantaine pour les utilisateurs **de protection stricte**.

Ou, pour le [courrier en bloc](bulk-complaint-level-values.md), vérifiez que la valeur BCL 6 ou supérieure remet le message dans le dossier Email indésirable pour les utilisateurs **de la protection Standard**, et que la valeur BCL 4 ou supérieure met le message en quarantaine pour les utilisateurs **de protection stricte**.

## <a name="preset-security-policies-in-exchange-online-powershell"></a>Stratégies de sécurité prédéfinies dans Exchange Online PowerShell

Dans PowerShell, les stratégies de sécurité prédéfinies se composent des éléments suivants :

- **Stratégies de sécurité individuelles** : par exemple, les stratégies anti-programme malveillant, les stratégies anti-courrier indésirable, les stratégies anti-hameçonnage, les stratégies de liens fiables et les stratégies de pièces jointes fiables.

  > [!WARNING]
  > N’essayez pas de créer, modifier ou supprimer les stratégies de sécurité individuelles associées à des stratégies de sécurité prédéfinies. La seule méthode prise en charge pour créer les stratégies de sécurité individuelles pour les stratégies de sécurité prédéfinies Standard ou Strict consiste à activer la stratégie de sécurité prédéfinie dans le portail Microsoft 365 Defender pour la première fois.

- **Règles** : des règles distinctes pour la stratégie de sécurité prédéfinie Standard, la stratégie de sécurité prédéfinie Strict et la stratégie de sécurité prédéfinie de protection intégrée définissent les conditions de destinataire et les exceptions pour les stratégies (identifiez les destinataires auxquels les protections de la stratégie s’appliquent).

  Pour les stratégies de sécurité prédéfinies Standard et Strict, ces règles sont créées la première fois que vous activez la stratégie de sécurité prédéfinie dans le portail Microsoft 365 Defender. Si vous n’avez jamais activé la stratégie de sécurité prédéfinie, les règles associées n’existent pas. Par la suite, la désactivation de la stratégie de sécurité prédéfinie ne supprime pas les règles associées.

  La stratégie de sécurité prédéfinie de protection intégrée a une règle unique qui contrôle les exceptions à la protection par défaut des liens fiables et des pièces jointes fiables de la stratégie.

  Les stratégies de sécurité prédéfinies Standard et Strict ont les règles suivantes :

  - **Règles pour les protections Exchange Online Protection (EOP)** : la règle de la stratégie de sécurité prédéfinie standard et la règle de la stratégie de sécurité prédéfinie Strict contrôlent à qui les protections EOP dans la stratégie (anti-programme malveillant, anti-courrier indésirable et anti-hameçonnage) s’appliquent (conditions de destinataire et exceptions pour les protections EOP).
  - **Règles pour les protections Defender pour Office 365** : la règle pour la stratégie de sécurité prédéfinie standard et la règle pour la stratégie de sécurité prédéfinie Strict contrôle les Defender pour Office 365 protections dans la stratégie (liens fiables et pièces jointes fiables) s’appliquent (conditions de destinataire et exceptions pour protections Defender pour Office 365).

  Les règles pour les stratégies de sécurité prédéfinies Standard et Strict vous permettent également d’activer ou d’activer la stratégie de sécurité prédéfinie en activant ou en désactivant les règles associées aux stratégies.

  Les règles pour les stratégies de sécurité prédéfinies ne sont pas disponibles pour les applets de commande de règle standard qui fonctionnent pour des stratégies de sécurité individuelles (par exemple, **Get-AntiPhishRule**). Au lieu de cela, les applets de commande suivantes sont requises :

  - Stratégie de sécurité prédéfinie de protection intégrée : **\*applets de commande -ATPBuiltInProtectionRule** .
  - Stratégies de sécurité prédéfinies standard et strictes : **\*applets de commande -EOPProtectionPolicyRule** et **\*-ATPProtectionPolicyRule** .

Les sections suivantes décrivent comment utiliser ces applets de commande dans les **scénarios pris en charge**.

Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="use-powershell-to-view-individual-security-policies-for-preset-security-policies"></a>Utiliser PowerShell pour afficher des stratégies de sécurité individuelles pour les stratégies de sécurité prédéfinies

N’oubliez pas que si vous n’avez jamais activé la stratégie de sécurité prédéfinie Standard ou la stratégie de sécurité prédéfinie Strict dans le portail Microsoft 365 Defender, les stratégies de sécurité associées pour la stratégie de sécurité prédéfinie n’existent pas.

> [!WARNING]
> N’essayez pas de créer, modifier ou supprimer les stratégies de sécurité individuelles associées à des stratégies de sécurité prédéfinies. La seule méthode prise en charge pour créer les stratégies de sécurité individuelles pour les stratégies de sécurité prédéfinies Standard ou Strict consiste à activer la stratégie de sécurité prédéfinie dans le portail Microsoft 365 Defender pour la première fois.

- **Stratégie de sécurité prédéfinie de protection intégrée** : les stratégies associées sont nommées Built-In Stratégie de protection. La valeur de la propriété IsBuiltInProtection a la valeur True pour ces stratégies.

  Pour afficher les stratégies de sécurité individuelles pour la stratégie de sécurité prédéfinie de protection intégrée, exécutez la commande suivante :

  ```powershell
  Write-Output -InputObject ("`r`n"*3),"Built-in protection Safe Attachments policy",("-"*79);Get-SafeAttachmentPolicy -Identity "Built-In Protection Policy" | Format-List; Write-Output -InputObject ("`r`n"*3),"Built-in protection Safe Links policy",("-"*79);Get-SafeLinksPolicy -Identity "Built-In Protection Policy" | Format-List
  ```

- **Stratégie de sécurité prédéfinie standard** : les stratégies associées sont nommées `Standard Preset Security Policy<13-digit number>`. Par exemple : `Standard Preset Security Policy1622650008019`. La valeur de la propriété RecommendPolicyType est Standard.

  - **Organisations sans Defender pour Microsoft 365** :

    Pour afficher les stratégies de sécurité individuelles pour la stratégie de sécurité prédéfinie Standard dans les organisations sans Defender pour Microsoft 365, exécutez la commande suivante :

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"Standard anti-malware policy",("-"*79);Get-MalwareFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard anti-spam policy",("-"*79);Get-HostedContentFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard anti-phishing policy",("-"*79);Get-AntiPhishPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"
    ```

  - **Organisations disposant de Defender pour Microsoft 365** :

    Pour afficher les stratégies de sécurité individuelles pour la stratégie de sécurité prédéfinie Standard dans les organisations avec Defender pour Microsoft 365, exécutez la commande suivante :

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"Standard anti-malware policy",("-"*79);Get-MalwareFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard anti-spam policy",("-"*79);Get-HostedContentFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard anti-phishing policy",("-"*79);Get-AntiPhishPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard Safe Attachments policy",("-"*79);Get-SafeAttachmentPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"; Write-Output -InputObject ("`r`n"*3),"Standard Safe Links policy",("-"*79);Get-SafeLinksPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Standard"
    ```

- **Stratégie de sécurité prédéfinie stricte** : les stratégies associées sont nommées `Strict Preset Security Policy<13-digit number>`. Par exemple : `Strict Preset Security Policy1642034872546`. La valeur de la propriété RecommendPolicyType est Strict.

  - **Organisations sans Defender pour Microsoft 365** :

    - Pour afficher les stratégies de sécurité individuelles pour la stratégie de sécurité prédéfinie Strict dans les organisations sans Defender pour Microsoft 365, exécutez la commande suivante :

      ```powershell
      Write-Output -InputObject ("`r`n"*3),"Strict anti-malware policy",("-"*79);Get-MalwareFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict anti-spam policy",("-"*79);Get-HostedContentFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict anti-phishing policy",("-"*79);Get-AntiPhishPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"
      ```

  - **Organisations disposant de Defender pour Microsoft 365** :

    - Pour afficher les stratégies de sécurité individuelles pour la stratégie de sécurité prédéfinie Strict dans les organisations avec Defender pour Microsoft 365, exécutez la commande suivante :

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"Strict anti-malware policy",("-"*79);Get-MalwareFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict anti-spam policy",("-"*79);Get-HostedContentFilterPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict anti-phishing policy",("-"*79);Get-AntiPhishPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict Safe Attachments policy",("-"*79);Get-SafeAttachmentPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"; Write-Output -InputObject ("`r`n"*3),"Strict Safe Links policy",("-"*79);Get-SafeLinksPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Strict"
    ```

### <a name="use-powershell-to-view-rules-for-preset-security-policies"></a>Utiliser PowerShell pour afficher les règles des stratégies de sécurité prédéfinies

N’oubliez pas que si vous n’avez jamais activé la stratégie de sécurité prédéfinie Standard ou la stratégie de sécurité prédéfinie Strict dans le portail Microsoft 365 Defender, les règles associées à ces stratégies n’existent pas.

- **Stratégie de sécurité prédéfinie de protection intégrée** : la règle associée est nommée RÈGLE de protection ATP Built-In.

  Pour afficher la règle associée à la stratégie de sécurité prédéfinie de protection intégrée, exécutez la commande suivante :

  ```powershell
  Get-ATPBuiltInProtectionRule
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-ATPBuiltInProtectionRule](/powershell/module/exchange/get-atpbuiltinprotectionrule).

- **Stratégie de sécurité prédéfinie standard** : les règles associées sont nommées Stratégie de sécurité prédéfinie standard.

  Utilisez les commandes suivantes pour afficher les règles associées à la stratégie de sécurité prédéfinie Standard :

  - Pour afficher la règle associée aux protections EOP dans la stratégie de sécurité prédéfinie Standard, exécutez la commande suivante :

    ```powershell
    Get-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"
    ```

  - Pour afficher la règle associée aux protections Defender pour Office 365 dans la stratégie de sécurité prédéfinie Standard, exécutez la commande suivante :

    ```powershell
    Get-ATPProtectionPolicyRule -Identity "Standard Preset Security Policy"
    ```

  - Pour afficher les deux règles en même temps, exécutez la commande suivante :

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"EOP rule - Standard preset security policy",("-"*79);Get-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"; Write-Output -InputObject ("`r`n"*3),"Defender for Office 365 rule - Standard preset security policy",("-"*79);Get-ATPProtectionPolicyRule -Identity "Standard Preset Security Policy"
    ```

- **Stratégie de sécurité prédéfinie stricte** : les règles associées sont nommées Stratégie de sécurité prédéfinie stricte.

  Utilisez les commandes suivantes pour afficher les règles associées à la stratégie de sécurité prédéfinie Strict :

  - Pour afficher la règle associée aux protections EOP dans la stratégie de sécurité prédéfinie Strict, exécutez la commande suivante :

    ```powershell
    Get-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"
    ```

  - Pour afficher la règle associée aux protections Defender pour Office 365 dans la stratégie de sécurité prédéfinie Strict, exécutez la commande suivante :

    ```powershell
    Get-ATPProtectionPolicyRule -Identity "Strict Preset Security Policy"
    ```

  - Pour afficher les deux règles en même temps, exécutez la commande suivante :

    ```powershell
    Write-Output -InputObject ("`r`n"*3),"EOP rule - Strict preset security policy",("-"*79);Get-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"; Write-Output -InputObject ("`r`n"*3),"Defender for Office 365 rule - Strict preset security policy",("-"*79);Get-ATPProtectionPolicyRule -Identity "Strict Preset Security Policy"
    ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-EOPProtectionPolicyRule](/powershell/module/exchange/get-eopprotectionpolicyrule) et [Get-ATPProtectionPolicyRule](/powershell/module/exchange/get-atpprotectionpolicyrule).

### <a name="use-powershell-to-turn-on-or-turn-off-preset-security-policies"></a>Utiliser PowerShell pour activer ou désactiver des stratégies de sécurité prédéfinies

Comme décrit précédemment, pour activer ou désactiver les stratégies de sécurité prédéfinies Standard ou Strict, vous activez ou désactivez les règles associées à la stratégie. La valeur de la propriété State de la règle indique si la règle est Activée ou Désactivée.

Selon que votre organisation a Defender pour Office 365, vous devrez peut-être activer ou désactiver une règle (la règle pour les protections EOP) ou deux règles (une règle pour les protections EOP et une règle pour les protections Defender pour Office 365) pour activer ou désactiver la stratégie de sécurité prédéfinie.

- **Stratégie de sécurité prédéfinie standard** :

  - **Organisations sans Defender pour Office 365** :

    - Dans les organisations sans Defender pour Office 365, exécutez la commande suivante pour déterminer si la règle de la stratégie prédéfinie Standard est actuellement activée ou désactivée :

      ```powershell
      Get-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy" | Format-Table Name,State
      ```

    - Exécutez la commande suivante pour désactiver la stratégie de sécurité prédéfinie Standard si elle est activée :

      ```powershell
      Disable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"
      ```

    - Exécutez la commande suivante pour activer la stratégie de sécurité prédéfinie Standard si elle est désactivée :

      ```powershell
      Enable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"
      ```

  - **Organisations avec Defender pour Office 365** :

    - Dans les organisations avec Defender pour Office 365, exécutez la commande suivante pour déterminer si les règles de la stratégie prédéfinie Standard sont actuellement activées ou désactivées :

      ```powershell
      Write-Output -InputObject ("`r`n"*3),"EOP rule - Standard preset security policy",("-"*63);Get-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy" | Format-Table Name,State; Write-Output -InputObject `r`n,"Defender for Office 365 rule - Standard preset security policy",("-"*63);Get-ATPProtectionPolicyRule -Identity "Standard Preset Security Policy" | Format-Table Name,State
      ```

    - Exécutez la commande suivante pour désactiver la stratégie de sécurité prédéfinie Standard si elle est activée :

      ```powershell
      Disable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"; Disable-ATPProtectionPolicyRule -Identity "Standard Preset Security Policy"
      ```

    - Exécutez la commande suivante pour activer la stratégie de sécurité prédéfinie Standard si elle est désactivée :

      ```powershell
      Enable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"; Enable-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy"
      ```

- **Stratégie de sécurité prédéfinie stricte** :

  - **Organisations sans Defender pour Office 365** :

    - Dans les organisations avec Defender pour Office 365, exécutez la commande suivante pour déterminer si la règle de la stratégie prédéfinie Strict est actuellement activée ou désactivée :

      ```powershell
      Get-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy" | Format-Table Name,State
      ```

    - Exécutez la commande suivante pour désactiver la stratégie de sécurité prédéfinie Strict si elle est activée :

      ```powershell
      Disable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"
      ```

    - Exécutez la commande suivante pour activer la stratégie de sécurité prédéfinie Strict si elle est désactivée :

      ```powershell
      Enable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"
      ```

  - **Organisations avec Defender pour Office 365** :

    - Dans les organisations avec Defender pour Office 365, exécutez la commande suivante pour déterminer si les règles de la stratégie prédéfinie Strict sont actuellement activées ou désactivées :

      ```powershell
      Write-Output -InputObject ("`r`n"*3),"EOP rule - Strict preset security policy",("-"*63);Get-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy" | Format-Table Name,State; Write-Output -InputObject `r`n,"Defender for Office 365 rule - Strict preset security policy",("-"*63);Get-ATPProtectionPolicyRule -Identity "Strict Preset Security Policy" | Format-Table Name,State
      ```

    - Exécutez la commande suivante pour désactiver la stratégie de sécurité prédéfinie Strict si elle est activée :

      ```powershell
      Disable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"; Disable-ATPProtectionPolicyRule -Identity "Strict Preset Security Policy"
      ```

    - Exécutez la commande suivante pour activer la stratégie de sécurité prédéfinie Strict si elle est désactivée :

      ```powershell
      Enable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"; Enable-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy"
      ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Enable-EOPProtectionPolicyRule](/powershell/module/exchange/enable-eopprotectionpolicyrule), [Enable-ATPProtectionPolicyRule](/powershell/module/exchange/enable-atpprotectionpolicyrule), [Disable-EOPProtectionPolicyRule](/powershell/module/exchange/disable-eopprotectionpolicyrule) et [Disable-ATPProtectionPolicyRule](/powershell/module/exchange/disable-atpprotectionpolicyrule).

### <a name="use-powershell-to-specify-recipient-conditions-and-exceptions-for-preset-security-policies"></a>Utiliser PowerShell pour spécifier des conditions de destinataire et des exceptions pour les stratégies de sécurité prédéfinies

> [!IMPORTANT]
  > Plusieurs types de conditions ou exceptions différentes ne sont pas cumulatives ; elles sont inclusives. La stratégie de sécurité prédéfinie est appliquée _uniquement_ aux destinataires qui correspondent à _tous les_ filtres de destinataires spécifiés. Par exemple, vous configurez une condition de filtre de destinataire dans la stratégie avec les valeurs suivantes :
  >
  > - Utilisateurs : romain@contoso.com
  > - Groupes : Cadres
  >
  > La stratégie s'applique à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie ne lui est pas appliquée.
  >
  > De même, si vous utilisez le même filtre de destinataires comme exception à la stratégie, la stratégie n'est pas appliquée à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie s’applique toujours à lui.

Pour la stratégie de sécurité prédéfinie de protection intégrée, vous pouvez uniquement spécifier des exceptions de destinataire. Si toutes les valeurs de paramètre d’exception sont vides (`$null`), il n’existe aucune exception à la stratégie.

Pour les stratégies de sécurité prédéfinies Standard et Strict, vous pouvez spécifier des conditions de destinataire et des exceptions pour les protections EOP et les protections Defender pour Office 365. Si toutes les conditions et valeurs de paramètre d’exception sont vides (`$null`), il n’existe aucune condition de destinataire ni aucune exception aux stratégies de sécurité prédéfinies Standard ou Strict.

Même si aucune condition de destinataire ou aucune exception n’est appliquée à une stratégie de sécurité prédéfinie, le fait que la stratégie soit appliquée à tous les destinataires dépend [de l’ordre de priorité des stratégies](#order-of-precedence-for-preset-security-policies-and-other-policies) , comme décrit précédemment dans cet article.

- **Stratégie de sécurité prédéfinie de protection intégrée** :

  Utilisez la syntaxe suivante :

  ```powershell
  Set-ATPBuiltInProtectionRule -Identity "ATP Built-In Protection Rule" -ExceptIfRecipientDomainIs <"domain1","domain2",... | $null> -ExceptIfSentTo <"user1","user2",... | $null> -ExceptIfSentToMemberOf <"group1","group2",... | $null>
  ```

  Cet exemple supprime toutes les exceptions de destinataire de la stratégie de sécurité prédéfinie de protection intégrée.

  ```powershell
  Set-ATPBuiltInProtectionRule -Identity "ATP Built-In Protection Rule" -ExceptIfRecipientDomainIs $null -ExceptIfSentTo $null -ExceptIfSentToMemberOf $null
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-ATPBuiltInProtectionRule](/powershell/module/exchange/set-atpbuiltinprotectionrule).

- **Stratégies de sécurité prédéfinies Standard ou Strict**

  Utilisez la syntaxe suivante :

  ```powershell
  <Set-EOPProtectionPolicyRule | SetAtpProtectionPolicyRule> -Identity "<Standard Preset Security Policy | Strict Preset Security Policy>" -SentTo <"user1","user2",... | $null> -ExceptIfSentTo <"user1","user2",... | $null> -SentToMemberOf <"group1","group2",... | $null> -ExceptIfSentToMemberOf <"group1","group2",... | $null> -RecipientDomainIs <"domain1","domain2",... | $null> -ExceptIfRecipientDomainIs <"domain1","domain2",... | $null>
  ```

  Cet exemple configure des exceptions à partir des protections EOP dans la stratégie de sécurité prédéfinie Standard pour les membres du groupe de distribution nommé Cadres.

  ```powershell
  Set-EOPProtectionPolicyRule -Identity "Standard Preset Security Policy" -ExceptIfSentToMemberOf Executives
  ```

  Cet exemple configure des exceptions des protections Defender pour Office 365 dans la stratégie de sécurité prédéfinie Strict pour les boîtes aux lettres d’opérations de sécurité (SecOps) spécifiées.

  ```powershell
  Set-EOPProtectionPolicyRule -Identity "Strict Preset Security Policy" -ExceptIfSentTo "SecOps1","SecOps2"
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-EOPProtectionPolicyRule](/powershell/module/exchange/set-eopprotectionpolicyrule) et [Set-ATPProtectionPolicyRule](/powershell/module/exchange/Set-atpprotectionpolicyrule).
