---
title: Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365
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
description: Les administrateurs peuvent apprendre à créer, modifier et supprimer les stratégies anti-hameçonnage avancées disponibles dans les organisations avec Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8311da9d67a9835163ee3eaa34a38a7132977055
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67386579"
---
# <a name="configure-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les stratégies anti-hameçonnage dans [Microsoft Defender pour Office 365](defender-for-office-365.md) peuvent aider à protéger votre organisation contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillantes et d’autres types d’attaques par hameçonnage. Pour plus d’informations sur les différences entre les stratégies anti-hameçonnage dans Exchange Online Protection (EOP) et les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, consultez [La protection anti-hameçonnage](anti-phishing-protection.md).

Les administrateurs peuvent afficher, modifier et configurer (mais pas supprimer) la stratégie anti-hameçonnage par défaut. Pour une plus grande granularité, vous pouvez également créer des stratégies anti-hameçonnage personnalisées qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez cependant modifier la priorité (l'ordre d'exécution) de vos stratégies personnalisées.

Vous pouvez configurer des stratégies anti-hameçonnage dans Defender pour Office 365 dans le portail Microsoft 365 Defender ou dans Exchange Online PowerShell.

Pour plus d’informations sur la configuration des stratégies anti-hameçonnage les plus limitées disponibles dans Exchange Online Protection (autrement dit, les organisations sans Defender pour Office 365), consultez Configurer des [stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md).

Les éléments de base d’une stratégie anti-hameçonnage sont les suivants :

- **Stratégie anti-hameçonnage** : spécifie les protections contre le hameçonnage à activer ou désactiver, ainsi que les actions à appliquer.
- **Règle anti-hameçonnage** : spécifie les filtres de priorité et de destinataire (auxquels la stratégie s’applique) pour une stratégie anti-hameçonnage.

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies anti-hameçonnage dans le portail Microsoft 365 Defender :

- Lorsque vous créez une stratégie, vous créez en fait une règle anti-hameçonnage et la stratégie anti-hameçonnage associée en même temps en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie, les paramètres liés au nom, à la priorité, activé ou désactivé, et les filtres de destinataire modifient la règle anti-hameçonnage. Tous les autres paramètres modifient la stratégie anti-hameçonnage associée.
- Lorsque vous supprimez une stratégie, la règle anti-hameçonnage et la stratégie anti-hameçonnage associée sont supprimées.

Dans Exchange Online PowerShell, vous gérez la stratégie et la règle séparément. Pour plus d’informations, consultez la section [Utiliser Exchange Online PowerShell pour configurer les stratégies anti-hameçonnage](#use-exchange-online-powershell-to-configure-anti-phishing-policies) plus loin dans cet article.

Chaque Defender pour Office 365 organisation dispose d’une stratégie anti-hameçonnage intégrée nommée Office 365 Par défaut anti-hameçonnage qui a les propriétés suivantes :

- La stratégie est appliquée à tous les destinataires de l’organisation, même s’il n’existe aucune règle anti-hameçonnage (filtres de destinataires) associée à la stratégie.
- La stratégie a la valeur de priorité personnalisée la **plus petite**, que vous ne pouvez pas modifier (la stratégie est toujours appliquée en dernier). Les stratégies personnalisées que vous créez disposent d’une priorité plus élevée.
- La stratégie est la stratégie par défaut (la propriété **IsDefault** possède la valeur`True`) et vous ne pouvez pas supprimer la stratégie par défaut.

Pour augmenter l’efficacité de la protection anti-hameçonnage dans Defender pour Office 365, vous pouvez créer des stratégies anti-hameçonnage personnalisées avec des paramètres plus stricts qui sont appliqués à des utilisateurs ou des groupes d’utilisateurs spécifiques.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cette rubrique.
  - Pour ajouter, modifier et supprimer des stratégies anti-hameçonnage, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour accéder en lecture seule aux stratégies anti-hameçonnage, vous devez être membre des groupes <sup>\*</sup> de **rôles Lecteur général** ou **Lecteur de sécurité**.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L'ajout d'utilisateurs au rôle Azure Active Directory Domain Services correspondant dans le centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations requises pour d'autres fonctionnalités dans Microsoft 365. Pour plus d'informations, consultez [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour connaître les paramètres recommandés pour les stratégies anti-hameçonnage dans Defender pour Office 365, consultez [la stratégie anti-hameçonnage dans Defender pour Office 365 paramètres](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

- Autorisez jusqu’à 30 minutes pour l’application d’une stratégie nouvelle ou mise à jour.

- Pour plus d’informations sur l’endroit où les stratégies anti-hameçonnage sont appliquées dans le pipeline de filtrage, consultez [Ordre et priorité de la protection par e-mail](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Utiliser le portail Microsoft 365 Defender pour créer des stratégies anti-hameçonnage

La création d’une stratégie anti-hameçonnage personnalisée dans le portail Microsoft 365 Defender crée la règle anti-hameçonnage et la stratégie anti-hameçonnage associée en même temps en utilisant le même nom pour les deux.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **de règles** \> **anti-hameçonnage** dans la section **Stratégies**. Pour accéder directement à la page **Anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , cliquez sur ![l’icône Créer.](../../media/m365-cc-sc-create-icon.png) **Création**.

3. L’assistant d'application de stratégies s’ouvre. Dans la page **Nom de** la stratégie, configurez les paramètres suivants :
   - **Nom** Entrez un nom unique et descriptif pour la stratégie.
   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Utilisateurs, groupes et domaines** qui s’affiche, identifiez les destinataires internes auxquels la stratégie s’applique (conditions de destinataire) :
   - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés.
   - **Groupes** :
     - Les membres des groupes de distribution ou des groupes de sécurité activés par courrier spécifiés.
     - Groupes Microsoft 365 spécifiée
   - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identifiants (nom, nom d'affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant est affiché dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour voir toutes les valeurs disponibles.

   Plusieurs valeurs dans la même condition utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

   - **Exclure ces utilisateurs, groupes et domaines** : Pour ajouter des exceptions pour les destinataires internes auxquels la stratégie s'applique (exceptions des destinataires), sélectionnez cette option et configurez les exceptions. Les paramètres et le comportement sont exactement comme les conditions.

   > [!IMPORTANT]
   > Plusieurs types de conditions ou exceptions différentes ne sont pas cumulatives ; elles sont inclusives. La stratégie est appliquée _uniquement_ aux destinataires qui correspondent à _tous les_ filtres de destinataires spécifiés. Par exemple, vous configurez une condition de filtre de destinataire dans la stratégie avec les valeurs suivantes :
   >
   > - Le destinataire est : romain@contoso.com
   > - Le destinataire est membre de : Exécutifs
   >
   > La stratégie s'applique à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie ne lui est pas appliquée.
   >
   > De même, si vous utilisez le même filtre de destinataires comme exception à la stratégie, la stratégie n'est pas appliquée à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie s’applique toujours à lui.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page de **protection & seuil d’hameçonnage** qui s’affiche, configurez les paramètres suivants :

   - **Seuil d’e-mail d’hameçonnage** : utilisez le curseur pour sélectionner l’une des valeurs suivantes :
     - **1 - Standard** (il s’agit de la valeur par défaut.)
     - **2 - Agressif**
     - **3 - Plus agressif**
     - **4 - Plus agressif**

     Pour plus d’informations, consultez [Seuils de hameçonnage avancés dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   - **Emprunt d’identité** : ces paramètres sont une condition pour la stratégie qui identifie des expéditeurs spécifiques à rechercher (individuellement ou par domaine) dans l’adresse From des messages entrants. Pour plus d’informations, consultez [les paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

     > [!NOTE]
     >
     > - Dans chaque stratégie anti-hameçonnage, vous pouvez spécifier un maximum de 350 utilisateurs protégés (adresses e-mail de l’expéditeur). Vous ne pouvez pas spécifier le même utilisateur protégé dans plusieurs stratégies.
     > - La protection de l’emprunt d’identité de l’utilisateur ne fonctionne pas si l’expéditeur et le destinataire ont déjà communiqué par e-mail. Si l’expéditeur et le destinataire n’ont jamais communiqué par e-mail, le message est identifié comme une tentative d’emprunt d’identité.

     - **Permettre aux utilisateurs de protéger** : la valeur par défaut est désactivée (non sélectionnée). Pour l’activer, activez la case à cocher, puis cliquez sur le lien **Gérer (nn) expéditeur(s)** qui s’affiche.

       Dans le menu volant **Gérer les expéditeurs pour la protection contre l’emprunt d’identité** qui s’affiche, procédez comme suit :

       - **Expéditeurs internes** : cliquez sur ![Ajouter une icône interne.](../../media/m365-cc-sc-add-internal-icon.png) **Sélectionnez interne**. Dans le menu volant **Ajouter des expéditeurs internes** qui s’affiche, cliquez dans la zone et sélectionnez un utilisateur interne dans la liste. Vous pouvez filtrer la liste en tapant l’utilisateur, puis en sélectionnant l’utilisateur dans les résultats. Vous pouvez utiliser la plupart des identificateurs (nom, nom d’affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d’affichage correspondant s’affiche dans les résultats.

         Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

         Lorsque vous avez terminé, cliquez sur **Ajouter**

       - **Expéditeurs externes** : cliquez sur ![Ajouter une icône externe.](../../media/m365-cc-sc-create-icon.png) **Sélectionnez externe**. Dans le menu volant **Ajouter des expéditeurs externes** qui s’affiche, entrez un nom d’affichage dans la zone **Ajouter un nom** et une adresse e-mail dans la zone **Ajouter un message électronique,** puis cliquez sur **Ajouter**.

         Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

         Lorsque vous avez terminé, cliquez sur **Ajouter**

       De retour sur le menu volant **Gérer les expéditeurs pour l’emprunt d’identité** , vous pouvez supprimer des entrées en sélectionnant une ou plusieurs entrées dans la liste. Vous pouvez rechercher des entrées à l’aide de l’icône ![Rechercher.](../../media/m365-cc-sc-create-icon.png) **Zone de recherche** .

       Après avoir sélectionné au moins une entrée, l’icône Supprimer les ![utilisateurs sélectionnés.](../../media/m365-cc-sc-remove-selected-users-icon.png) **L’icône Supprimer les utilisateurs sélectionnés** s’affiche, que vous pouvez utiliser pour supprimer les entrées sélectionnées.

       Lorsque vous avez terminé, cliquez sur **Terminé**.

     - **Activer les domaines à protéger** : la valeur par défaut est désactivée (non sélectionnée). Pour l’activer, activez la case à cocher, puis configurez l’un ou les deux des paramètres suivants qui s’affichent :
       - **Incluez les domaines que je possède** : pour activer ce paramètre, activez la case à cocher. Pour afficher les domaines dont vous êtes propriétaire, cliquez sur **Afficher mes domaines**.
       - **Inclure des domaines personnalisés** : pour activer ce paramètre, cochez la case, puis cliquez sur le lien **Gérer (nn) domaine personnalisé** qui s’affiche. Dans le menu volant **Gérer les domaines personnalisés pour la protection de l’emprunt d’identité** qui s’affiche, cliquez sur ![l’icône Ajouter des domaines.](../../media/m365-cc-sc-create-icon.png) **Ajouter des domaines**.

         Dans le menu volant **Ajouter des domaines personnalisés** qui s’affiche, cliquez dans la zone **Domaine** , entrez une valeur, puis appuyez sur Entrée ou sélectionnez la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur l’![icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) suivant la valeur.

         Lorsque vous avez terminé, cliquez sur **Ajouter des domaines**

         > [!NOTE]
         > Vous pouvez avoir un maximum de 50 domaines dans toutes les stratégies anti-hameçonnage.

       De retour sur le **menu volant Gérer les domaines personnalisés pour l’emprunt d’identité** , vous pouvez supprimer des entrées en sélectionnant une ou plusieurs entrées dans la liste. Vous pouvez rechercher des entrées à l’aide de l’icône ![Rechercher.](../../media/m365-cc-sc-create-icon.png) **Zone de recherche** .

       Après avoir sélectionné au moins une entrée, l’icône ![Supprimer les domaines.](../../media/m365-cc-sc-delete-icon.png) **L’icône Supprimer** s’affiche, que vous pouvez utiliser pour supprimer les entrées sélectionnées.

   - **Ajouter des expéditeurs et des domaines approuvés** : spécifiez les exceptions de protection d’emprunt d’identité pour la stratégie en cliquant sur **Gérer (nn) les expéditeurs approuvés et les domaines**. Dans le menu volant **Gérer les domaines personnalisés pour la protection de l’emprunt d’identité** qui s’affiche, configurez les paramètres suivants :
      - **Expéditeurs** : vérifiez que l’onglet **Expéditeur** est sélectionné, puis cliquez sur ![l’icône Ajouter des expéditeurs.](../../media/m365-cc-sc-create-icon.png) Dans le menu volant **Ajouter des expéditeurs approuvés** qui s’affiche, entrez une adresse e-mail dans la zone, puis cliquez sur **Ajouter**. Répétez cette étape autant de fois que nécessaire. Pour supprimer une entrée existante, cliquez sur ![l’icône](../../media/m365-cc-sc-close-icon.png) Supprimer pour l’entrée.

        Lorsque vous avez terminé, cliquez sur **Ajouter**.

      - **Domaines** : sélectionnez l’onglet **Domaine**, puis cliquez sur ![l’icône Ajouter des domaines.](../../media/m365-cc-sc-create-icon.png)

        Dans le menu volant **Ajouter des domaines approuvés** qui s’affiche, cliquez dans la zone **Domaine** , entrez une valeur, puis appuyez sur Entrée ou sélectionnez la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur l’![icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) suivant la valeur.

        Lorsque vous avez terminé, cliquez sur **Ajouter**.

     > [!NOTE]
     > Si les messages système Microsoft 365 des expéditeurs suivants sont identifiés comme des tentatives d’emprunt d’identité, vous pouvez ajouter les expéditeurs à la liste des expéditeurs approuvés :
     >
     > - `⁠noreply@email.teams.microsoft.com`
     > - `noreply@emeaemail.teams.microsoft.com`
     > - `no-reply@sharepointonline.com`

     De retour dans le menu volant **Gérer les domaines personnalisés pour l’emprunt d’identité** , vous pouvez supprimer des entrées des onglets **Expéditeur** et **Domaine** en sélectionnant une ou plusieurs entrées dans la liste. Vous pouvez rechercher des entrées à l’aide de l’icône ![Rechercher.](../../media/m365-cc-sc-create-icon.png) **Zone de recherche** .

     Une fois que vous avez sélectionné au moins une entrée, l’icône **Supprimer** s’affiche, que vous pouvez utiliser pour supprimer les entrées sélectionnées.

     Lorsque vous avez terminé, cliquez sur **Terminé**.

     > [!NOTE]
     > Le nombre maximal d’entrées d’expéditeur et de domaine est de 1 024.

   - **Activer l’intelligence de boîte aux lettres** : la valeur par défaut est activée (sélectionnée) et nous vous recommandons de la laisser activée. Pour la désactiver, désactivez la case à cocher.

     - **Activer la protection d’emprunt d’identité basée sur l’intelligence** : ce paramètre est disponible uniquement si **l’option Activer l’intelligence de boîte aux lettres** est activée (sélectionnée). Ce paramètre permet à l’intelligence de boîte aux lettres d’agir sur les messages identifiés comme des tentatives d’emprunt d’identité. Vous spécifiez l’action à effectuer dans **l’intelligence si la boîte aux lettres détecte un paramètre utilisateur emprunté** sur la page suivante.

       Nous vous recommandons d’activer ce paramètre en cochant la case. Pour désactiver ce paramètre, désactivez la case à cocher.

   - **Usurpation d’identité** : dans cette section, utilisez la case à cocher **Activer l’usurpation d’identité** pour activer ou désactiver l’intelligence par usurpation d’identité. La valeur par défaut est activée (sélectionnée) et nous vous recommandons de la laisser activée. Vous spécifiez l’action à effectuer sur les messages des expéditeurs avec usurpation d’identité bloqués dans le **si le message est détecté comme paramètre d’usurpation** d’identité sur la page suivante.

     Pour désactiver l’intelligence par usurpation d’identité, désactivez la case à cocher.

     > [!NOTE]
     > Vous n’avez pas besoin de désactiver la protection contre l’usurpation d’identité si votre enregistrement MX ne pointe pas vers Microsoft 365 ; vous activez plutôt le filtrage amélioré pour les connecteurs. Pour obtenir des instructions, consultez [Filtrage amélioré pour les connecteurs dans Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Action** qui s’affiche, configurez les paramètres suivants :

   - **Actions de message** : configurez les actions suivantes dans cette section :
     - **Si le message est détecté comme un utilisateur emprunt d’identité** : ce paramètre n’est disponible que si vous avez sélectionné **Activer la protection des utilisateurs** sur la page précédente. Sélectionnez l’une des actions suivantes dans la liste déroulante pour les messages où l’expéditeur est l’un des utilisateurs protégés que vous avez spécifiés sur la page précédente :
       - **N’appliquez aucune action**
       - **Rediriger le message vers d’autres adresses e-mail**
       - **Déplacer le message vers les dossiers de Email indésirables des destinataires**
       - **Mettre en quarantaine le message** : si vous sélectionnez cette action, une zone Appliquer la stratégie de **quarantaine** s’affiche où vous sélectionnez la stratégie de quarantaine qui s’applique aux messages mis en quarantaine par la protection d’emprunt d’identité de l’utilisateur. Les stratégies de quarantaine définissent ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine et si les utilisateurs reçoivent des notifications de quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

         Une valeur de stratégie **appliquer la mise en quarantaine** vide signifie que la stratégie de quarantaine par défaut est utilisée (DefaultFullAccessPolicy pour les détections d’emprunt d’identité d’utilisateur). Lorsque vous modifiez ultérieurement la stratégie anti-hameçonnage ou affichez les paramètres, le nom de la stratégie de quarantaine par défaut s’affiche.
  
       - **Remettre le message et ajouter d’autres adresses à la ligne CCI**
       - **Supprimer le message avant qu’il ne soit remis**

     - **Si le message est détecté comme un domaine emprunté :** ce paramètre n’est disponible que si vous avez sélectionné **Activer les domaines à protéger** sur la page précédente. Sélectionnez l’une des actions suivantes dans la liste déroulante pour les messages où l’adresse e-mail de l’expéditeur se trouve dans l’un des domaines protégés que vous avez spécifiés sur la page précédente :
       - **N’appliquez aucune action**
       - **Rediriger le message vers d’autres adresses e-mail**
       - **Déplacer le message vers les dossiers de Email indésirables des destinataires**
       - **Mettre en quarantaine le message** : si vous sélectionnez cette action, une zone Appliquer la stratégie de **quarantaine** s’affiche où vous sélectionnez la stratégie de quarantaine qui s’applique aux messages mis en quarantaine par la protection d’emprunt d’identité de domaine.

         Une valeur de **stratégie appliquer en quarantaine** vide signifie que la stratégie de quarantaine par défaut est utilisée (DefaultFullAccessPolicy pour les détections d’emprunt d’identité de domaine). Lorsque vous modifiez ultérieurement la stratégie anti-hameçonnage ou affichez les paramètres, le nom de la stratégie de quarantaine par défaut s’affiche.

       - **Remettre le message et ajouter d’autres adresses à la ligne CCI**
       - **Supprimer le message avant qu’il ne soit remis**

     - **Si l’intelligence de boîte aux lettres détecte un utilisateur emprunt d’identité** : ce paramètre n’est disponible que si vous avez sélectionné **Activer l’intelligence pour la protection de l’emprunt d’identité** sur la page précédente. Sélectionnez l’une des actions suivantes dans la liste déroulante pour les messages identifiés comme tentatives d’emprunt d’identité par l’intelligence de boîte aux lettres :
       - **N’appliquez aucune action**
       - **Rediriger le message vers d’autres adresses e-mail**
       - **Déplacer le message vers les dossiers de Email indésirables des destinataires**
       - **Mettre en quarantaine le message** : si vous sélectionnez cette action, une zone Appliquer la stratégie de **mise en quarantaine** s’affiche où vous sélectionnez la stratégie de quarantaine qui s’applique aux messages mis en quarantaine par la protection d’intelligence de boîte aux lettres. Les stratégies de quarantaine définissent ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine et si les utilisateurs reçoivent des notifications de quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

         Une valeur de stratégie **appliquer la mise en quarantaine** vide signifie que la stratégie de quarantaine par défaut est utilisée (DefaultFullAccessPolicy pour les détections d’intelligence de boîte aux lettres). Lorsque vous modifiez ultérieurement la stratégie anti-hameçonnage ou affichez les paramètres, le nom de la stratégie de quarantaine par défaut s’affiche.

       - **Remettre le message et ajouter d’autres adresses à la ligne CCI**
       - **Supprimer le message avant qu’il ne soit remis**

     - **Si le message est détecté comme usurpation d’identité** : ce paramètre n’est disponible que si vous avez sélectionné **Activer l’intelligence de l’usurpation d’identité** sur la page précédente. Sélectionnez l’une des actions suivantes dans la liste déroulante pour les messages provenant d’expéditeurs usurpés bloqués :
       - **Déplacer le message vers les dossiers de Email indésirables des destinataires**
       - **Mettre en quarantaine le message** : si vous sélectionnez cette action, une zone Appliquer la stratégie de **mise en quarantaine** s’affiche, où vous sélectionnez la stratégie de quarantaine qui s’applique aux messages mis en quarantaine par la protection contre l’usurpation d’identité. Les stratégies de quarantaine définissent ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine et si les utilisateurs reçoivent des notifications de quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

         Une valeur de stratégie **appliquer la mise en quarantaine** vide signifie que la stratégie de quarantaine par défaut est utilisée (DefaultFullAccessPolicy pour les détections d’usurpation d’identité). Lorsque vous modifiez ultérieurement la stratégie anti-hameçonnage ou affichez les paramètres, le nom de la stratégie de quarantaine par défaut s’affiche.

   - **Conseils de sécurité & indicateurs** : Configurez les paramètres suivants :
     - **Afficher le premier conseil de sécurité de contact** : pour plus d’informations, consultez [premier conseil de sécurité de contact](set-up-anti-phishing-policies.md#first-contact-safety-tip).
     - **Afficher l’info-bulle de sécurité d’emprunt d’identité de l’utilisateur** : ce paramètre est disponible uniquement si vous avez sélectionné **Activer la protection des utilisateurs** sur la page précédente.
     - **Afficher l’info-bulle de sécurité d’emprunt d’identité de domaine** : ce paramètre n’est disponible que si vous avez sélectionné **Activer les domaines à protéger** sur la page précédente.
     - **Afficher le conseil de sécurité des caractères inhabituels d’emprunt d’identité de l’utilisateur** Ce paramètre n’est disponible que si vous avez sélectionné **Activer les utilisateurs pour protéger** ou **Activer les domaines à protéger** sur la page précédente.
     - **Afficher (?) pour les expéditeurs non authentifiés pour l’usurpation** d’identité : ce paramètre est disponible uniquement si vous avez sélectionné **Activer l’intelligence de l’usurpation d’identité** sur la page précédente. Ajoute un point d’interrogation (?) à la photo de l’expéditeur dans la zone From d’Outlook si le message ne réussit pas les vérifications SPF ou DKIM **et** que le message ne passe pas [l’authentification](email-validation-and-authentication.md#composite-authentication) DMARC ou composite.
     - **Afficher la balise « via »** : ce paramètre est disponible uniquement si vous avez sélectionné **Activer l’intelligence de l’usurpation d’identité** sur la page précédente. Ajoute une balise via (chris@contoso.com via fabrikam.com) à l’adresse From si elle est différente du domaine dans la signature DKIM ou l’adresse **MAIL FROM** . La valeur par défaut est activée (sélectionnée). Pour la désactiver, désactivez la case à cocher.

     Pour activer un paramètre, cochez la case. Pour la désactiver, désactivez la case à cocher.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

7. Dans la page **Révision** qui s’affiche, passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

8. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Utiliser le portail Microsoft 365 Defender pour afficher les stratégies anti-hameçonnage

1. Dans le portail Microsoft 365 Defender, accédez à Email & Stratégies de  **collaboration** \> **& stratégies** **anti-hameçonnage** des règles \> \> dans la section **Stratégies**.

2. Dans la page **Anti-hameçonnage** , les propriétés suivantes s’affichent dans la liste des stratégies anti-hameçonnage :

   - **Name**
   - **État**
   - **Priorité**
   - **Dernière modification**

3. Lorsque vous sélectionnez une stratégie en cliquant sur le nom, les paramètres de stratégie s’affichent dans un menu volant.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Utiliser le portail Microsoft 365 Defender pour modifier les stratégies anti-hameçonnage

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **de règles** \> **anti-hameçonnage** dans la section **Stratégies**. Pour accéder directement à la page **Anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. Dans le menu volant des détails de stratégie qui s’affiche, sélectionnez **Modifier** dans chaque section pour modifier les paramètres de la section. Pour plus d’informations sur les paramètres, consultez [la section Utiliser le portail Microsoft 365 Defender pour créer des stratégies anti-hameçonnage](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) plus haut dans cet article.

   Pour la stratégie anti-hameçonnage par défaut, la section **Utilisateurs, groupes et domaines** n’est pas disponible (la stratégie s’applique à tout le monde) et vous ne pouvez pas renommer la stratégie.

Pour activer ou désactiver une stratégie ou définir l’ordre de priorité de la stratégie, consultez les sections suivantes.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Activer ou désactiver des stratégies anti-hameçonnage personnalisées

Vous ne pouvez pas désactiver la stratégie anti-hameçonnage par défaut.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **de règles** \> **anti-hameçonnage** dans la section **Stratégies**. Pour accéder directement à la page **Anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , sélectionnez une stratégie personnalisée dans la liste en cliquant sur le nom.

3. En haut du menu volant des détails de stratégie qui s’affiche, vous verrez l’une des valeurs suivantes :
   - **Stratégie désactivée** : Pour activer la stratégie, cliquez sur l’![icône Activer.](../../media/m365-cc-sc-turn-on-off-icon.png) **Activer**.
   - **Stratégie sur**: Pour désactiver la stratégie,cliquez sur ![l’icône Désactiver.](../../media/m365-cc-sc-turn-on-off-icon.png) **Désactiver**.

4. Dans la boîte de dialogue de confirmation qui s’affiche, cliquez sur **Activer** ou **Désactiver**.

5. Cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

De retour sur la page principale de la stratégie, la valeur **État** de la stratégie sera **Activée** ou **Désactivée**.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Définir la priorité des stratégies anti-hameçonnage personnalisées

Par défaut, les stratégies anti-hameçonnage reçoivent une priorité basée sur l’ordre dans lequel elles ont été créées (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour modifier la priorité d'une stratégie, vous cliquez sur **Augmenter la priorité** ou **Diminuer la priorité** dans les propriétés de la stratégie (vous ne pouvez pas modifier directement le numéro de **priorité** dans le portail Microsoft 365 Defender). Changer la priorité d'une stratégie n'a de sens que si vous avez plusieurs stratégies.

 **Remarques** :

- Dans le portail Microsoft 365 Defender, vous ne pouvez modifier la priorité de la stratégie anti-hameçonnage qu’après la avoir créée. Dans PowerShell, vous pouvez remplacer la priorité par défaut lorsque vous créez la règle anti-hameçonnage (qui peut affecter la priorité des règles existantes).
- Les stratégies anti-hameçonnage sont traitées dans l’ordre dans lequel elles sont affichées (la première stratégie a la valeur **Priority** 0). La stratégie anti-hameçonnage par défaut a la valeur de priorité **la plus basse**, et vous ne pouvez pas la modifier.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **de règles** \> **anti-hameçonnage** dans la section **Stratégies**. Pour accéder directement à la page **Anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , sélectionnez une stratégie personnalisée dans la liste en cliquant sur le nom.

3. En haut du menu volant détails de la stratégie qui s’affiche, vous verrez **Augmenter la priorité** ou **Diminuer la priorité** en fonction de la valeur de priorité actuelle et du nombre de stratégies personnalisées :
   - La stratégie avec la valeur **de priorité** **0** a uniquement l’option **Réduire la priorité** disponible.
   - La stratégie avec la valeur **de priorité** la plus basse (par exemple, **3**) a uniquement l’option **Augmenter la priorité** disponible.
   - Si vous avez au moins trois stratégies, les stratégies entre les valeurs de priorité la plus élevée et la plus basse ont les options **Augmenter la priorité** et Diminuer la **priorité** disponibles.

   Cliquez sur l’![Icône Augmenter la priorité](../../media/m365-cc-sc-increase-icon.png) **Augmenter la priorité** ou ![Icône Diminuer la priorité](../../media/m365-cc-sc-decrease-icon.png) **Diminuer la priorité** pour modifier la valeur **Priorité**.

4. Lorsque vous avez terminé, cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Utiliser le portail Microsoft 365 Defender pour supprimer les stratégies anti-hameçonnage personnalisées

Lorsque vous utilisez le portail Microsoft 365 Defender pour supprimer une stratégie anti-hameçonnage personnalisée, la règle anti-hameçonnage et la stratégie anti-hameçonnage correspondante sont toutes deux supprimées. Vous ne pouvez pas supprimer la stratégie anti-hameçonnage par défaut.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **de règles** \> **anti-hameçonnage** dans la section **Stratégies**. Pour accéder directement à la page **Anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , sélectionnez une stratégie personnalisée dans la liste en cliquant sur le nom de la stratégie.

3. En haut du menu volant des détails de la stratégie qui s’affiche, cliquez sur l’![icône Autres actions. ](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’actions**\>![icône Supprimer la stratégie](../../media/m365-cc-sc-delete-icon.png)**Supprimer la stratégie**.

4. Dans la boîte de dialogue de confirmation qui s'affiche, cliquez sur **Oui**.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Utiliser Exchange Online PowerShell pour configurer des stratégies anti-hameçonnage

Comme décrit précédemment, une politique anti-spam se compose d’une politique anti-hameçonnage et d’une règle anti-hameçonnage.

Dans Exchange Online PowerShell, la différence entre les stratégies anti-hameçonnage et les règles anti-hameçonnage est évidente. Vous gérez les stratégies anti-hameçonnage à l’aide des **\*applets de commande -AntiPhishPolicy** , et vous gérez les règles anti-hameçonnage à l’aide **\*des applets de commande -AntiPhishRule** .

- Dans PowerShell, vous créez d’abord la stratégie anti-hameçonnage, puis vous créez la règle anti-hameçonnage qui identifie la stratégie à laquelle la règle s’applique.
- Dans PowerShell, vous modifiez séparément les paramètres de la stratégie anti-hameçonnage et de la règle anti-hameçonnage.
- Lorsque vous supprimez une stratégie anti-hameçonnage de PowerShell, la règle anti-hameçonnage correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Utiliser PowerShell pour créer des stratégies anti-hameçonnage

La création d’une stratégie anti-hameçonnage dans PowerShell est un processus en deux étapes :

1. Créez la stratégie anti-hameçonnage.
2. Créez la règle anti-hameçonnage qui spécifie la stratégie anti-hameçonnage à laquelle la règle s’applique.

 **Remarques** :

- Vous pouvez créer une règle anti-hameçonnage et lui attribuer une stratégie anti-hameçonnage non associée existante. Une règle anti-hameçonnage ne peut pas être associée à plusieurs stratégies anti-hameçonnage.
- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies anti-hameçonnage dans PowerShell qui ne sont pas disponibles dans le portail Microsoft 365 Defender tant que vous n’avez pas créé la stratégie :
  - Créez la nouvelle stratégie comme désactivée (_activée_ `$false` sur l’applet de commande **New-AntiPhishRule** ).
  - Définissez la priorité de la stratégie lors de la création (_Priorité__\<Number\>_) sur l’applet de commande **New-AntiPhishRule**).
- Une nouvelle stratégie anti-hameçonnage que vous créez dans PowerShell n’est pas visible dans le portail Microsoft 365 Defender tant que vous n’avez pas affecté la stratégie à une règle anti-hameçonnage.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>Étape 1 : Utiliser PowerShell pour créer une stratégie anti-hameçonnage

Pour créer une stratégie anti-hameçonnage, utilisez cette syntaxe :

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Cet exemple crée une stratégie anti-hameçonnage nommée Research Quarantine avec les paramètres suivants :

- La stratégie est activée (nous n’utilisons pas le paramètre _Activé_ , et la valeur par défaut est `$true`).
- La description est la suivante : Politique du département de recherche.
- Modifie l’action par défaut pour les détections d’usurpation en quarantaine et utilise la [stratégie de quarantaine](quarantine-policies.md) par défaut pour les messages mis en quarantaine (nous n’utilisons pas le paramètre _SpoofQuarantineTag_ ).
- Active la protection des domaines d’organisation pour tous les domaines acceptés et la protection des domaines ciblés pour fabrikam.com.
- Spécifie la quarantaine comme action pour les détections d’emprunt d’identité de domaine et utilise la [stratégie de quarantaine](quarantine-policies.md) par défaut pour les messages mis en quarantaine (nous n’utilisons pas le paramètre _TargetedDomainQuarantineTag_ ).
- Spécifie Mai Fujito (mfujito@fabrikam.com) en tant qu’utilisateur pour empêcher l’emprunt d’identité.
- Spécifie la mise en quarantaine comme action pour les détections d’emprunt d’identité de l’utilisateur et utilise la [stratégie de quarantaine](quarantine-policies.md) par défaut pour les messages mis en quarantaine (nous n’utilisons pas le paramètre _TargetedUserQuarantineTag_ ).
- Active l’intelligence de boîte aux lettres (_EnableMailboxIntelligence_), permet à la protection de l’intelligence de boîte aux lettres d’agir sur les messages (_EnableMailboxIntelligenceProtection_), spécifie quarantaine comme action pour les messages détectés et utilise la [stratégie de quarantaine](quarantine-policies.md) par défaut pour les messages mis en quarantaine (nous n’utilisons pas le paramètre _MailboxIntelligenceQuarantineTag_ ).
- Active tous les conseils de sécurité.

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainsToProtect fabrikam.com -TargetedDomainProtectionAction Quarantine -EnableTargetedUserProtection $true -TargetedUsersToProtect "Mai Fujito;mfujito@fabrikam.com" -TargetedUserProtectionAction Quarantine -EnableMailboxIntelligence $true -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -EnableSimilarUsersSafetyTips $true -EnableSimilarDomainsSafetyTips $true -EnableUnusualCharactersSafetyTips $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Pour obtenir des instructions détaillées pour spécifier les [stratégies de quarantaine](quarantine-policies.md) à utiliser dans une stratégie anti-hameçonnage, consultez [Utiliser PowerShell pour spécifier la stratégie de quarantaine dans les stratégies anti-hameçonnage](quarantine-policies.md#anti-phishing-policies).

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>Étape 2 : Utiliser PowerShell pour créer une règle anti-hameçonnage

Pour créer une règle anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Cet exemple crée une règle anti-hameçonnage nommée Research Department avec les conditions suivantes :

- La règle est associée à la stratégie anti-hameçonnage nommée Research Quarantine.
- La règle s’applique aux membres du groupe nommé Research Department.
- Étant donné que nous n’utilisons pas le paramètre _Priority_ , la priorité par défaut est utilisée.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Utiliser PowerShell pour afficher les stratégies anti-hameçonnage

Pour afficher les stratégies anti-hameçonnage existantes, utilisez la syntaxe suivante :

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple retourne une liste récapitulative de toutes les stratégies anti-hameçonnage, ainsi que les propriétés spécifiées.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

Cet exemple retourne toutes les valeurs de propriété pour la stratégie anti-hameçonnage nommée Executives.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Utiliser PowerShell pour afficher les règles anti-hameçonnage

Pour afficher les règles anti-hameçonnage existantes, utilisez la syntaxe suivante :

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple retourne une liste récapitulative de toutes les règles anti-hameçonnage, ainsi que les propriétés spécifiées.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

```PowerShell
Get-AntiPhishRule -State Disabled | Format-Table Name,Priority
```

```PowerShell
Get-AntiPhishRule -State Enabled | Format-Table Name,Priority
```

Cet exemple retourne toutes les valeurs de propriété pour la règle anti-hameçonnage nommée Contoso Executives.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Utiliser PowerShell pour modifier des stratégies anti-hameçonnage

Outre les éléments suivants, les mêmes paramètres sont disponibles lorsque vous modifiez une stratégie anti-hameçonnage dans PowerShell que lorsque vous créez la stratégie comme décrit à [l’étape 1 : Utiliser PowerShell pour créer une section de stratégie anti-hameçonnage](#step-1-use-powershell-to-create-an-anti-phish-policy) plus haut dans cet article.

- Le commutateur _MakeDefault_ qui transforme la stratégie spécifiée en stratégie par défaut (appliquée à tout le monde, toujours **priorité la plus basse** et vous ne pouvez pas la supprimer) est disponible uniquement lorsque vous modifiez une stratégie anti-hameçonnage dans PowerShell.

- Vous ne pouvez pas renommer une stratégie anti-hameçonnage (l’applet **de commande Set-AntiPhishPolicy** n’a aucun paramètre _Name_ ). Lorsque vous renommez une stratégie anti-hameçonnage dans le portail Microsoft 365 Defender, vous renommez uniquement la _règle_ anti-hameçonnage.

Pour modifier une stratégie anti-hameçonnage, utilisez cette syntaxe :

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-AntiPhishPolicy](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Pour obtenir des instructions détaillées pour spécifier les [stratégies de quarantaine](quarantine-policies.md) à utiliser dans une stratégie anti-hameçonnage, consultez [Utiliser PowerShell pour spécifier la stratégie de quarantaine dans les stratégies anti-hameçonnage](quarantine-policies.md#anti-phishing-policies).

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Utiliser PowerShell pour modifier les règles anti-hameçonnage

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle anti-hameçonnage dans PowerShell est le paramètre _Activé_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver les règles anti-hameçonnage existantes, consultez la section suivante.

Sinon, aucun paramètre supplémentaire n’est disponible lorsque vous modifiez une règle anti-hameçonnage dans PowerShell. Les mêmes paramètres sont disponibles lorsque vous créez une règle comme décrit à [l’étape 2 : Utiliser PowerShell pour créer une section de règle anti-hameçonnage](#step-2-use-powershell-to-create-an-anti-phish-rule) plus haut dans cet article.

Pour modifier une règle anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-AntiPhishRule](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Utiliser PowerShell pour activer ou désactiver les règles anti-hameçonnage

L’activation ou la désactivation d’une règle anti-hameçonnage dans PowerShell active ou désactive l’ensemble de la stratégie anti-hameçonnage (la règle anti-hameçonnage et la stratégie anti-hameçonnage attribuée). Vous ne pouvez pas activer ou désactiver la stratégie anti-hameçonnage par défaut (elle est toujours appliquée à tous les destinataires).

Pour activer ou désactiver une règle anti-hameçonnage dans PowerShell, utilisez cette syntaxe :

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

Cet exemple désactive la règle anti-hameçonnage nommée Marketing Department.

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

Cet exemple montre comment activer la même règle.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Enable-AntiPhishRule](/powershell/module/exchange/enable-antiphishrule) et [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Utiliser PowerShell pour définir la priorité des règles anti-hameçonnage

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d'une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Remarques** :

- Pour définir la priorité d’une nouvelle règle lorsque vous la créez, utilisez plutôt le paramètre _Priority_ sur l’applet de commande **New-AntiPhishRule** .

- La stratégie anti-hameçonnage par défaut n’a pas de règle anti-hameçonnage correspondante, et elle a toujours la valeur de priorité non modifiable **la plus basse**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Utiliser PowerShell pour supprimer les stratégies anti-hameçonnage

Lorsque vous utilisez PowerShell pour supprimer une stratégie anti-hameçonnage, la règle anti-hameçonnage correspondante n’est pas supprimée.

Pour supprimer une stratégie anti-hameçonnage dans PowerShell, utilisez cette syntaxe :

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

Cet exemple montre comment supprimer la stratégie anti-hameçonnage nommée Marketing Department.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Utiliser PowerShell pour supprimer les règles anti-hameçonnage

Lorsque vous utilisez PowerShell pour supprimer une règle anti-hameçonnage, la stratégie anti-hameçonnage correspondante n’est pas supprimée.

Pour supprimer une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

Cet exemple montre comment supprimer la règle anti-hameçonnage nommée Marketing Department.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-AntiPhishRule](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement configuré les stratégies anti-hameçonnage dans Defender pour Office 365, effectuez l’une des étapes suivantes :

- Dans la page **Anti-hameçonnage** du portail <https://security.microsoft.com/antiphishing>Microsoft 365 Defender, vérifiez la liste des stratégies, leurs valeurs **d’état** et leurs valeurs **de priorité**. Pour afficher plus de détails, sélectionnez la stratégie dans la liste en cliquant sur le nom et en affichant les détails dans le menu volant qui s’affiche.

- Dans Exchange Online PowerShell, remplacez \<Name\> par le nom de la stratégie ou de la règle, exécutez la commande suivante et vérifiez les paramètres :

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
