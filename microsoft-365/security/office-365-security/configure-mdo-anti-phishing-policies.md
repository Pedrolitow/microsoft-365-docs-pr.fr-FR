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
ms.openlocfilehash: 5faf4533110fe5abad8606c9c859f82549dc2fce
ms.sourcegitcommit: 677dcc74aa898b2a17eb8430a32e675fea4e3fe5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63557920"
---
# <a name="configure-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les stratégies anti-hameçonnage dans [Microsoft Defender pour Office 365](defender-for-office-365.md) peuvent aider à protéger votre organisation contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillant et d’autres types d’attaques par hameçonnage. Pour plus d’informations sur les différences entre les stratégies anti-hameçonnage dans Exchange Online Protection (EOP) et les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, voir [Protection anti-hameçonnage](anti-phishing-protection.md).

Les administrateurs peuvent afficher, modifier et configurer (mais pas supprimer) la stratégie anti-hameçonnage par défaut. Pour plus de granularité, vous pouvez également créer des stratégies anti-hameçonnage personnalisées qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez cependant modifier la priorité (l'ordre d'exécution) de vos stratégies personnalisées.

Vous pouvez configurer des stratégies anti-hameçonnage dans Defender pour Office 365 dans le portail Microsoft 365 Defender ou dans Exchange Online PowerShell.

Pour plus d’informations sur la configuration des stratégies anti-hameçonnage les plus limitées disponibles dans Exchange Online Protection (c’est-à-dire, les organisations sans Defender pour Office 365), voir Configurer des stratégies [anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md).

Les éléments de base d’une stratégie anti-hameçonnage sont :

- **La stratégie anti-hameçonnage :** spécifie les protections de hameçonnage à activer ou désactiver, ainsi que les actions à appliquer.
- **La règle anti-hameçonnage** : spécifie la priorité et les filtres de destinataires (à qui la stratégie s’applique) pour une stratégie anti-hameçonnage.

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies anti-hameçonnage dans Microsoft 365 Defender portail :

- Lorsque vous créez une stratégie, vous créez en fait une règle anti-hameçonnage et la stratégie anti-hameçonnage associée en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie, les paramètres liés au nom, à la priorité, activés ou désactivés, et aux filtres de destinataire modifient la règle anti-hameçonnage. Tous les autres paramètres modifient la stratégie anti-hameçonnage associée.
- Lorsque vous supprimez une stratégie, la règle anti-hameçonnage et la stratégie anti-hameçonnage associée sont supprimées.

Dans Exchange Online PowerShell, vous gérez la stratégie et la règle séparément. Pour plus d’informations, voir la section [Utiliser Exchange Online PowerShell pour configurer des stratégies anti-hameçonnage](#use-exchange-online-powershell-to-configure-anti-phishing-policies) plus loin dans cet article.

Chaque defender pour Office 365 organisation dispose d’une stratégie anti-hameçonnage intégrée nommée Office 365 AntiPhish Default qui possède les propriétés ci-après :

- La stratégie est appliquée à tous les destinataires de l’organisation, même si aucune règle anti-hameçonnage (filtres de destinataires) n’est associée à la stratégie.
- La stratégie a la valeur de priorité personnalisée la **plus petite**, que vous ne pouvez pas modifier (la stratégie est toujours appliquée en dernier). Les stratégies personnalisées que vous créez disposent d’une priorité plus élevée.
- La stratégie est la stratégie par défaut (la propriété **IsDefault** possède la valeur`True`) et vous ne pouvez pas supprimer la stratégie par défaut.

Pour accroître l’efficacité de la protection anti-hameçonnage dans Defender pour Office 365, vous pouvez créer des stratégies anti-hameçonnage personnalisées avec des paramètres plus stricts qui sont appliqués à des utilisateurs ou des groupes d’utilisateurs spécifiques.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à la page **anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cette rubrique.
  - Pour ajouter, modifier et supprimer des stratégies anti-hameçonnage, vous devez être membre des groupes de  rôles Gestion de l’organisation ou **Administrateur** de la sécurité.
  - Pour accéder en lecture seule aux stratégies anti-hameçonnage, vous devez être membre des groupes de  rôles Lecteur  global ou Lecteur de sécurité<sup>\*</sup>.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L'ajout d'utilisateurs au rôle Azure Active Directory Domain Services correspondant dans le centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations requises pour d'autres fonctionnalités dans Microsoft 365. Pour plus d'informations, consultez [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour obtenir les paramètres recommandés pour les stratégies anti-hameçonnage dans Defender pour Office 365, consultez stratégie [anti-hameçonnage dans Defender pour Office 365 paramètres](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

- Autorisez jusqu’à 30 minutes pour qu’une stratégie nouvelle ou mise à jour soit appliquée.

- Pour plus d’informations sur l’endroit où les stratégies anti-hameçonnage sont appliquées dans le pipeline de filtrage, voir Ordre et priorité [de la protection du courrier électronique](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Utiliser le portail Microsoft 365 Defender pour créer des stratégies anti-hameçonnage

La création d’une stratégie anti-hameçonnage personnalisée dans le portail Microsoft 365 Defender crée la règle anti-hameçonnage et la stratégie anti-hameçonnage associée en utilisant le même nom pour les deux.

1. Dans le portail Microsoft 365 Defender <https://security.microsoft.com>à l’adresse , go to **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Anti-phishing** in the **Policies** section. Pour aller directement à la page **anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , cliquez sur Créer ![une icône.](../../media/m365-cc-sc-create-icon.png) **Création**.

3. L’assistant d'application de stratégies s’ouvre. Dans la page **Nom de la** stratégie, configurez les paramètres ci-après :
   - **Nom** Entrez un nom unique et descriptif pour la stratégie.
   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Utilisateurs, groupes et domaines** qui s’affiche, identifiez les destinataires internes auxquels la stratégie s’applique (conditions de destinataire) :
   - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés dans votre organisation.
   - **Groupes** : groupes de distribution, groupes de sécurité à extension messagerie ou groupes Microsoft 365 spécifiés dans votre organisation.
   - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identifiants (nom, nom d'affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant est affiché dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour voir toutes les valeurs disponibles.

   Plusieurs valeurs dans la même condition utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

   - **Exclure ces utilisateurs, groupes et domaines** : pour ajouter des exceptions pour les destinataires internes auxquels la stratégie s’applique (exceptions pour les destinataires), sélectionnez cette option et configurez les exceptions. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **de protection & seuil** de hameçonnage qui s’affiche, configurez les paramètres suivants :

   - **Seuil de courrier d’hameçonnage** : utilisez le curseur pour sélectionner l’une des valeurs suivantes :
     - **1 - Standard** (il s’agit de la valeur par défaut.)
     - **2 - Agressif**
     - **3 - Plus agressif**
     - **4 - Plus agressif**

     Pour plus d’informations, voir [Seuils de hameçonnage avancés dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   - **Emprunt d’identité** : ces paramètres sont une condition de la stratégie qui identifie des expéditeurs spécifiques à rechercher (individuellement ou par domaine) dans l’adresse De des messages entrants. Pour plus d’informations, voir paramètres d’emprunt d’identité dans les [stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

     > [!NOTE]
     >
     > - Dans chaque stratégie anti-hameçonnage, vous pouvez spécifier un maximum de 350 utilisateurs protégés (adresses e-mail de l’expéditeur). Vous ne pouvez pas spécifier le même utilisateur protégé dans plusieurs stratégies.
     > - La protection contre l’emprunt d’identité d’utilisateur ne fonctionne pas si l’expéditeur et le destinataire ont précédemment communiqué par courrier électronique. Si l’expéditeur et le destinataire n’ont jamais communiqué par courrier électronique, le message est identifié comme une tentative d’emprunt d’identité.

     - **Activer la protection des utilisateurs** : la valeur par défaut est off (non sélectionnée). Pour l’activer, cochez la case, puis cliquez sur le **(s) lien Gérer (nn)** des expéditeurs qui s’affiche.

       Dans le **volant Gérer les expéditeurs pour la protection** contre l’emprunt d’identité qui s’affiche, faites les étapes suivantes :

       - **Expéditeurs internes :** cliquez sur Ajouter ![une icône interne.](../../media/m365-cc-sc-add-internal-icon.png) **Sélectionnez interne**. Dans le **volant Ajouter des expéditeurs internes** qui s’affiche, cliquez dans la zone et sélectionnez un utilisateur interne dans la liste. Vous pouvez filtrer la liste en tapant l’utilisateur, puis en sélectionnant l’utilisateur dans les résultats. Vous pouvez utiliser la plupart des identificateurs (nom, nom d’affichage, alias, adresse e-mail, nom du compte, etc.), mais le nom complet correspondant est affiché dans les résultats.

         Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

         Lorsque vous avez terminé, cliquez sur **Ajouter**

       - **Expéditeurs externes :** cliquez sur Ajouter ![une icône externe.](../../media/m365-cc-sc-create-icon.png) **Sélectionnez externe**. Dans le  volant Ajouter des expéditeurs externes qui s’affiche, entrez un nom complet dans la zone Ajouter un nom et une adresse  e-mail dans la zone Ajouter un message électronique, puis cliquez sur **Ajouter**.

         Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

         Lorsque vous avez terminé, cliquez sur **Ajouter**

       De retour dans **le volant Gérer les** expéditeurs pour l’emprunt d’identité, vous pouvez supprimer des entrées en sélectionnant une ou plusieurs entrées dans la liste. Vous pouvez rechercher des entrées à l’aide de l’icône ![Rechercher.](../../media/m365-cc-sc-create-icon.png) **Zone de** recherche.

       Une fois que vous avez sélectionné au moins une entrée, l’icône ![Supprimer les utilisateurs sélectionnés.](../../media/m365-cc-sc-remove-selected-users-icon.png) **L’icône Supprimer les utilisateurs** sélectionnés s’affiche, que vous pouvez utiliser pour supprimer les entrées sélectionnées.

       Lorsque vous avez terminé, cliquez sur **Terminé**.

     - **Activer les domaines à protéger** : la valeur par défaut est off (non sélectionnée). Pour l’activer, cochez la case, puis configurez l’un des paramètres suivants ou les deux :
       - **Incluez les domaines que je possède** : pour activer ce paramètre, cochez la case. Pour afficher les domaines que vous possédez, cliquez **sur Afficher mes domaines**.
       - **Inclure des domaines personnalisés** : pour activer ce paramètre, cochez la case, puis cliquez sur le lien **Gérer (nn)** des domaines personnalisés qui s’affiche. Dans le **volant Gérer les domaines personnalisés pour la protection** contre l’emprunt d’identité qui s’affiche, ![cliquez sur Icône Ajouter des domaines.](../../media/m365-cc-sc-create-icon.png) **Ajouter des domaines**.

         Dans le volant Ajouter des domaines **personnalisés** qui s’affiche, cliquez  dans la zone Domaine, entrez une valeur, puis appuyez sur Entrée ou sélectionnez la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur l’![icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) suivant la valeur.

         Lorsque vous avez terminé, cliquez sur **Ajouter des domaines**

         > [!NOTE]
         > Vous pouvez avoir un maximum de 50 domaines dans toutes les stratégies anti-hameçonnage.

       De retour sur le volant Gérer les domaines **personnalisés** pour l’emprunt d’identité, vous pouvez supprimer des entrées en sélectionnant une ou plusieurs entrées dans la liste. Vous pouvez rechercher des entrées à l’aide de l’icône ![Rechercher.](../../media/m365-cc-sc-create-icon.png) **Zone de** recherche.

       Une fois que vous avez sélectionné au moins une entrée, l’icône ![Supprimer les domaines.](../../media/m365-cc-sc-delete-icon.png) **L’icône** Supprimer s’affiche, que vous pouvez utiliser pour supprimer les entrées sélectionnées.

   - **Ajouter des expéditeurs** et des domaines de confiance : spécifiez des exceptions de protection contre l’emprunt d’identité pour la stratégie en cliquant sur Gérer **(nn)** les expéditeurs de confiance et les domaines. Dans le **volant Gérer les domaines personnalisés pour la protection** contre l’emprunt d’identité qui s’affiche, configurez les paramètres suivants :
      - **Expéditeurs :** vérifiez que **l’onglet Expéditeur** est sélectionné et cliquez sur ![Icône Ajouter des expéditeurs](../../media/m365-cc-sc-create-icon.png). Dans le **volant Ajouter des expéditeurs de** confiance qui s’affiche, entrez une adresse de messagerie dans la zone, puis cliquez sur **Ajouter**. Répétez cette étape autant de fois que nécessaire. Pour supprimer une entrée existante, cliquez sur ![Supprimer l’icône](../../media/m365-cc-sc-close-icon.png) de l’entrée.

        Lorsque vous avez terminé, cliquez sur **Ajouter**.

      - **Domaines :** sélectionnez **l’onglet** Domaine, puis cliquez sur ![Icône Ajouter des domaines](../../media/m365-cc-sc-create-icon.png).

        Dans **le volant** Ajouter des domaines de confiance qui s’affiche, cliquez  dans la zone Domaine, entrez une valeur, puis appuyez sur Entrée ou sélectionnez la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur l’![icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) suivant la valeur.

        Lorsque vous avez terminé, cliquez sur **Ajouter**.

     De retour dans le volant Gérer les domaines **personnalisés** pour l’emprunt d’identité, vous pouvez  supprimer des entrées des onglets Expéditeur et Domaine en sélectionnant une ou plusieurs entrées dans la liste. Vous pouvez rechercher des entrées à l’aide de l’icône ![Rechercher.](../../media/m365-cc-sc-create-icon.png) **Zone de** recherche.

     Une fois que vous avez sélectionné au moins une  entrée, l’icône Supprimer s’affiche, que vous pouvez utiliser pour supprimer les entrées sélectionnées.

     Lorsque vous avez terminé, cliquez sur **Terminé**.

     > [!NOTE]
     > Le nombre maximal d’entrées d’expéditeur et de domaine est de 1 024.

   - **Activer l’intelligence de** boîte aux lettres : la valeur par défaut est activée (sélectionnée) et nous vous recommandons de la laisser activée. Pour la désactiver, cochez la case.

     - **Activer la protection contre l’usurpation** d’identité basée sur l’intelligence : ce paramètre est disponible uniquement si **l’intelligence** de boîte aux lettres est activée (sélectionnée). Ce paramètre permet à l’intelligence de boîte aux lettres d’agir sur les messages identifiés comme des tentatives d’emprunt d’identité. Vous spécifiez l’action à prendre dans la boîte aux lettres Si l’intelligence de boîte aux lettres **détecte** un paramètre utilisateur dont l’identité est usurpée sur la page suivante.

       Nous vous recommandons d’activer ce paramètre en cocher la case. Pour désactiver ce paramètre, cochez la case.

   - **Usurpation :** dans cette section, utilisez la case  à cocher Activer la veille contre l’usurpation d’informations pour activer ou désactiver l’usurpation d’informations. La valeur par défaut est sur (sélectionnée) et nous vous recommandons de la laisser. Vous spécifiez l’action à prendre sur les messages provenant d’expéditeurs usurpés bloqués dans le paramètre Si **le message** est détecté comme usurpant une adresse sur la page suivante.

     Pour désactiver la veille contre l’usurpation d’informations, cochez la case.

     > [!NOTE]
     > Vous n’avez pas besoin de désactiver la protection contre l’usurpation d’usurpation si votre enregistrement MX ne pointe pas vers Microsoft 365 ; vous activez plutôt le filtrage amélioré pour les connecteurs. Pour obtenir des instructions, voir [Filtrage amélioré pour les connecteurs dans Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Action** qui s’affiche, configurez les paramètres suivants :

   - **Actions de message** : configurez les actions suivantes dans cette section :
     - **Si le message est détecté comme** un utilisateur dont l’identité est usurpée : ce paramètre est disponible uniquement  si vous avez sélectionné Activer la protection des utilisateurs sur la page précédente. Sélectionnez l’une des actions suivantes dans la liste bas pour les messages pour lequel l’expéditeur est l’un des utilisateurs protégés que vous avez spécifiés sur la page précédente :
       - **Ne pas appliquer d’action**
       - **Rediriger le message vers d’autres adresses de messagerie**
       - **Déplacer le message vers les dossiers Courrier indésirable des destinataires**
       - **Mettre le message** en quarantaine : si vous sélectionnez cette  action, une zone de stratégie Appliquer la quarantaine s’affiche lorsque vous sélectionnez la stratégie de mise en quarantaine qui s’applique aux messages mis en quarantaine par la protection contre l’usurpation d’identité d’utilisateur. Les stratégies de mise en quarantaine définissent ce que les utilisateurs peuvent faire pour mettre en quarantaine les messages et si les utilisateurs reçoivent des notifications de mise en quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

         Une valeur de stratégie **Appliquer la quarantaine** vide signifie que la stratégie de mise en quarantaine par défaut est utilisée (DefaultFullAccessPolicy pour les détections d’emprunt d’identité d’utilisateur). Lorsque vous modifiez ultérieurement la stratégie anti-hameçonnage ou que vous affichez les paramètres, le nom de la stratégie de mise en quarantaine par défaut s’affiche.
  
       - **Remettre le message et ajouter d’autres adresses à la ligne  Bcc**
       - **Supprimer le message avant sa livraison**

     - **Si le message est détecté** comme un domaine dont l’identité a été usurpée : ce paramètre n’est  disponible que si vous avez sélectionné Activer les domaines à protéger sur la page précédente. Sélectionnez l’une des actions suivantes dans la liste suivante pour les messages pour lequel l’adresse de messagerie de l’expéditeur se trouve dans l’un des domaines protégés que vous avez spécifiés sur la page précédente :
       - **Ne pas appliquer d’action**
       - **Rediriger le message vers d’autres adresses de messagerie**
       - **Déplacer le message vers les dossiers Courrier indésirable des destinataires**
       - **Mettre le message** en quarantaine : si vous sélectionnez cette  action, une zone de stratégie Appliquer la quarantaine s’affiche lorsque vous sélectionnez la stratégie de mise en quarantaine qui s’applique aux messages mis en quarantaine par la protection contre l’usurpation d’identité de domaine.

         Une valeur de stratégie **Appliquer la quarantaine** vide signifie que la stratégie de mise en quarantaine par défaut est utilisée (DefaultFullAccessPolicy pour les détections d’emprunt d’identité de domaine). Lorsque vous modifiez ultérieurement la stratégie anti-hameçonnage ou que vous affichez les paramètres, le nom de la stratégie de mise en quarantaine par défaut s’affiche.

       - **Remettre le message et ajouter d’autres adresses à la ligne  Bcc**
       - **Supprimer le message avant sa livraison**

     - **Si l’intelligence de** boîte aux lettres détecte un utilisateur dont l’identité est usurpée : ce paramètre est disponible uniquement si vous avez sélectionné Activer l’intelligence pour la **protection** contre l’emprunt d’identité sur la page précédente. Sélectionnez l’une des actions suivantes dans la liste bas pour les messages identifiés comme tentatives d’emprunt d’identité par l’intelligence des boîtes aux lettres :
       - **Ne pas appliquer d’action**
       - **Rediriger le message vers d’autres adresses de messagerie**
       - **Déplacer le message vers les dossiers Courrier indésirable des destinataires**
       - **Mettre le message** en quarantaine : si vous sélectionnez cette  action, une zone de stratégie Appliquer la quarantaine s’affiche lorsque vous sélectionnez la stratégie de mise en quarantaine qui s’applique aux messages mis en quarantaine par la protection d’intelligence des boîtes aux lettres. Les stratégies de mise en quarantaine définissent ce que les utilisateurs peuvent faire pour mettre en quarantaine les messages et si les utilisateurs reçoivent des notifications de mise en quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

         Une valeur de stratégie **Appliquer la quarantaine** vide signifie que la stratégie de mise en quarantaine par défaut est utilisée (DefaultFullAccessPolicy pour les détections d’intelligence des boîtes aux lettres). Lorsque vous modifiez ultérieurement la stratégie anti-hameçonnage ou que vous affichez les paramètres, le nom de la stratégie de mise en quarantaine par défaut s’affiche.

       - **Remettre le message et ajouter d’autres adresses à la ligne  Bcc**
       - **Supprimer le message avant sa livraison**

     - **Si le message est détecté comme** usurpant une usurpation d’informations : ce paramètre n’est disponible que si vous avez sélectionné Activer la veille contre l’usurpation d’informations **sur la** page précédente. Sélectionnez l’une des actions suivantes dans la liste bas pour les messages provenant d’expéditeurs usurpés bloqués :
       - **Déplacer le message vers les dossiers Courrier indésirable des destinataires**
       - **Mettre le message** en quarantaine : si vous sélectionnez cette  action, une zone de stratégie Appliquer la mise en quarantaine s’affiche lorsque vous sélectionnez la stratégie de mise en quarantaine qui s’applique aux messages mis en quarantaine par la protection contre l’usurpation d’intelligence. Les stratégies de mise en quarantaine définissent ce que les utilisateurs peuvent faire pour mettre en quarantaine les messages et si les utilisateurs reçoivent des notifications de mise en quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

         Une valeur vide **de stratégie Appliquer** la mise en quarantaine signifie que la stratégie de mise en quarantaine par défaut est utilisée (DefaultFullAccessPolicy pour les détections d’usurpation d’informations). Lorsque vous modifiez ultérieurement la stratégie anti-hameçonnage ou que vous affichez les paramètres, le nom de la stratégie de mise en quarantaine par défaut s’affiche.

   - **Conseils de & indicateurs de sécurité** : configurez les paramètres suivants :
     - **Afficher le premier contact conseil de sécurité** : pour plus d’informations, voir [First contact conseil de sécurité](set-up-anti-phishing-policies.md#first-contact-safety-tip).
     - **Afficher l’emprunt** d conseil de sécurité utilisateur : ce paramètre est disponible uniquement si vous avez sélectionné Activer la protection des utilisateurs **sur la** page précédente.
     - **Afficher l’emprunt d conseil de sécurité** domaine : ce paramètre est disponible uniquement si vous avez sélectionné Activer les  domaines à protéger sur la page précédente.
     - **Affichez les caractères** inhabituels d’emprunt d’identité conseil de sécurité Ce paramètre est disponible uniquement si  vous avez sélectionné Activer les **utilisateurs** pour protéger ou Activer les domaines à protéger sur la page précédente.
     - **Afficher (?)** pour les expéditeurs non authentifiés pour l’usurpation d’adresse : ce paramètre est  disponible uniquement si vous avez sélectionné Activer l’intelligence contre l’usurpation d’adresse sur la page précédente. Ajoute un point d’interrogation (?) à la photo de l’expéditeur dans la zone De de Outlook si le message ne passe pas les vérifications SPF ou DKIM  et s’il ne passe pas l’authentification DMARC ou [composite](email-validation-and-authentication.md#composite-authentication).
     - **Afficher la balise « via »** : ce paramètre est disponible uniquement si vous avez sélectionné Activer la veille contre l’usurpation d’informations **sur la** page précédente. Ajoute une balise via (chris@contoso.com via fabrikam.com) à l’adresse De si elle est différente du domaine dans la signature DKIM ou l’adresse **MAIL FROM** . La valeur par défaut est sur (sélectionné). Pour la désactiver, cochez la case.

     Pour activer un paramètre, cochez la case. Pour la désactiver, cochez la case.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

7. Dans la page **Révision** qui s’affiche, passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

8. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Utiliser le portail Microsoft 365 Defender pour afficher les stratégies anti-hameçonnage

1. Dans le portail Microsoft 365 Defender, dans **la section** **Stratégies** \>  \>  \>, & stratégies de collaboration & règles **anti-hameçonnage**.

2. Dans la page **Anti-hameçonnage** , les propriétés suivantes sont affichées dans la liste des stratégies anti-hameçonnage :

   - **Name**
   - **État**
   - **Priorité**
   - **Dernière modification**

3. Lorsque vous sélectionnez une stratégie en cliquant sur le nom, les paramètres de stratégie s’affichent dans un volant.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Utiliser le portail Microsoft 365 Defender pour modifier des stratégies anti-hameçonnage

1. Dans le portail Microsoft 365 Defender <https://security.microsoft.com>à l’adresse , go to **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Anti-phishing** in the **Policies** section. Pour aller directement à la page **anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. Dans le menu volant des détails de stratégie qui s’affiche, sélectionnez **Modifier** dans chaque section pour modifier les paramètres de la section. Pour plus d’informations sur les paramètres, consultez la section Utiliser le portail Microsoft 365 Defender pour créer des stratégies [anti-hameçonnage](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) plus tôt dans cet article.

   Pour la stratégie anti-hameçonnage par défaut, la section **Utilisateurs,** groupes et domaines n’est pas disponible (la stratégie s’applique à tout le monde) et vous ne pouvez pas renommer la stratégie.

Pour activer ou désactiver une stratégie ou définir l’ordre de priorité de la stratégie, consultez les sections suivantes.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Activer ou désactiver des stratégies anti-hameçonnage personnalisées

Vous ne pouvez pas désactiver la stratégie anti-hameçonnage par défaut.

1. Dans le portail Microsoft 365 Defender <https://security.microsoft.com>à l’adresse , go to **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Anti-phishing** in the **Policies** section. Pour aller directement à la page **anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , sélectionnez une stratégie personnalisée dans la liste en cliquant sur le nom.

3. En haut du menu volant des détails de stratégie qui s’affiche, vous verrez l’une des valeurs suivantes :
   - **Stratégie désactivée** : Pour activer la stratégie, cliquez sur l’![icône Activer.](../../media/m365-cc-sc-turn-on-off-icon.png) **Activer**.
   - **Stratégie sur**: Pour désactiver la stratégie,cliquez sur ![l’icône Désactiver.](../../media/m365-cc-sc-turn-on-off-icon.png) **Désactiver**.

4. Dans la boîte de dialogue de confirmation qui s’affiche, cliquez sur **Activer** ou **Désactiver**.

5. Cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

De retour sur la page principale de la stratégie, la valeur **État** de la stratégie sera **Activée** ou **Désactivée**.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Définir la priorité des stratégies anti-hameçonnage personnalisées

Par défaut, les stratégies anti-hameçonnage se voir donner une priorité basée sur l’ordre de leur création (les nouvelles stratégies sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour modifier la priorité d'une stratégie, vous cliquez sur **Augmenter la priorité** ou **Diminuer la priorité** dans les propriétés de la stratégie (vous ne pouvez pas modifier directement le numéro de **priorité** dans le portail Microsoft 365 Defender). Changer la priorité d'une stratégie n'a de sens que si vous avez plusieurs stratégies.

 **Remarques** :

- Dans le Microsoft 365 Defender, vous ne pouvez modifier la priorité de la stratégie anti-hameçonnage qu’une fois que vous l’avez créé. Dans PowerShell, vous pouvez remplacer la priorité par défaut lorsque vous créez la règle anti-hameçonnage (ce qui peut affecter la priorité des règles existantes).
- Les stratégies anti-hameçonnage sont traitées dans l’ordre d’affichage (la première stratégie a la  valeur Priority 0). La stratégie anti-hameçonnage par défaut a la valeur de priorité **La** plus faible et vous ne pouvez pas la modifier.

1. Dans le portail Microsoft 365 Defender <https://security.microsoft.com>à l’adresse , go to **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Anti-phishing** in the **Policies** section. Pour aller directement à la page **anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , sélectionnez une stratégie personnalisée dans la liste en cliquant sur le nom.

3. En haut du menu volant détails de la stratégie qui s’affiche, vous verrez **Augmenter la priorité** ou **Diminuer la priorité** en fonction de la valeur de priorité actuelle et du nombre de stratégies personnalisées :
   - La stratégie dont la valeur **de** priorité **est 0** ne dispose que de l’option Diminuer **la** priorité disponible.
   - La stratégie dont la valeur **de** priorité est la plus faible ( **par** exemple, 3) ne dispose que **de l’option** Augmenter la priorité.
   - Si vous avez au moins trois stratégies, les stratégies entre les valeurs de priorité les plus élevées et les plus faibles ont les options Augmenter la priorité et Diminuer **la** priorité disponibles.

   Cliquez sur l’![Icône Augmenter la priorité](../../media/m365-cc-sc-increase-icon.png) **Augmenter la priorité** ou ![Icône Diminuer la priorité](../../media/m365-cc-sc-decrease-icon.png) **Diminuer la priorité** pour modifier la valeur **Priorité**.

4. Lorsque vous avez terminé, cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Utiliser le portail Microsoft 365 Defender pour supprimer des stratégies anti-hameçonnage personnalisées

Lorsque vous utilisez le portail Microsoft 365 Defender pour supprimer une stratégie anti-hameçonnage personnalisée, la règle anti-hameçonnage et la stratégie anti-hameçonnage correspondante sont toutes deux supprimées. Vous ne pouvez pas supprimer la stratégie anti-hameçonnage par défaut.

1. Dans le portail Microsoft 365 Defender <https://security.microsoft.com>à l’adresse , go to **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Anti-phishing** in the **Policies** section. Pour aller directement à la page **anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , sélectionnez une stratégie personnalisée dans la liste en cliquant sur le nom de la stratégie.

3. En haut du menu volant des détails de la stratégie qui s’affiche, cliquez sur l’![icône Autres actions. ](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’actions**\>![icône Supprimer la stratégie](../../media/m365-cc-sc-delete-icon.png)**Supprimer la stratégie**.

4. Dans la boîte de dialogue de confirmation qui s'affiche, cliquez sur **Oui**.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Utiliser Exchange Online PowerShell pour configurer des stratégies anti-hameçonnage

Comme décrit précédemment, une stratégie anti-courrier indésirable se compose d’une stratégie anti-hameçonnage et d’une règle anti-hameçonnage.

Dans Exchange Online PowerShell, la différence entre les stratégies anti-hameçonnage et les règles anti-hameçonnage est évidente. Vous gérez les stratégies anti-hameçonnage à l’aide des cmdlets -AntiPhishPolicy et vous gérez les règles anti-hameçonnage **à l’aide des cmdlets -AntiPhishRule.\*** **\***

- Dans PowerShell, vous créez d’abord la stratégie anti-hameçonnage, puis vous créez la règle anti-hameçonnage qui identifie la stratégie à qui s’applique la règle.
- Dans PowerShell, vous modifiez séparément les paramètres de la stratégie anti-hameçonnage et de la règle anti-hameçonnage.
- Lorsque vous supprimez une stratégie anti-hameçonnage de PowerShell, la règle anti-hameçonnage correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Utiliser PowerShell pour créer des stratégies anti-hameçonnage

La création d’une stratégie anti-hameçonnage dans PowerShell est un processus en deux étapes :

1. Créez la stratégie anti-hameçonnage.
2. Créez la règle anti-hameçonnage qui spécifie la stratégie anti-hameçonnage à l’application de la règle.

 **Remarques** :

- Vous pouvez créer une règle anti-hameçonnage et lui attribuer une stratégie anti-hameçonnage existante et non dissociée. Une règle anti-hameçonnage ne peut pas être associée à plusieurs stratégies anti-hameçonnage.
- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies anti-hameçonnage dans PowerShell qui ne sont pas disponibles dans le portail Microsoft 365 Defender tant que vous n’avez pas créé la stratégie :
  - Créez la stratégie comme _désactivée (_ `$false` activée sur la cmdlet **New-AntiPhishRule** ).
  - Définissez la priorité de la stratégie lors de la création (_Priorité__\<Number\>_) sur la cmdlet **New-AntiPhishRule**).
- Une nouvelle stratégie anti-hameçonnage que vous créez dans PowerShell n’est pas visible dans le portail Microsoft 365 Defender tant que vous n’avez pas attribué la stratégie à une règle anti-hameçonnage.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>Étape 1 : Utiliser PowerShell pour créer une stratégie anti-hameçonnage

Pour créer une stratégie anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Cet exemple crée une stratégie anti-hameçonnage nommée Research Quarantine avec les paramètres suivants :

- La stratégie est activée (nous n’utilisons pas le paramètre _Enabled_ et la valeur par défaut est `$true`).
- La description est la suivante : stratégie du service de recherche.
- Modifie l’action par défaut pour les détections d’usurpation d’informations en [](quarantine-policies.md) quarantaine et utilise la stratégie de mise en quarantaine par défaut pour les messages mis en quarantaine (nous n’utilisons pas le paramètre _SpoofQuarantineTag_).
- Active la protection des domaines d’organisation pour tous les domaines acceptés et la protection des domaines ciblés pour fabrikam.com.
- Spécifie la mise en quarantaine comme action pour les détections d’emprunt d’identité de [](quarantine-policies.md) domaine et utilise la stratégie de mise en quarantaine par défaut pour les messages mis en quarantaine (nous n’utilisons pas le paramètre _TargetedDomainQuarantineTag_).
- Spécifie Mai Fujito (mfujito@fabrikam.com) en tant qu’utilisateur pour empêcher l’emprunt d’identité.
- Spécifie la mise en quarantaine comme action pour les détections d’emprunt d’identité d’utilisateur et utilise la stratégie de mise en quarantaine par défaut pour les messages mis en quarantaine (nous n’utilisons pas le paramètre _TargetedUserQuarantineTag_).[](quarantine-policies.md)
- Active l’intelligence de boîte aux lettres (_EnableMailboxIntelligence_), permet à la protection d’intelligence de boîte aux lettres d’agir sur les messages (_EnableMailboxIntelligenceProtection_), spécifie la quarantaine comme [](quarantine-policies.md) action pour les messages détectés et utilise la stratégie de mise en quarantaine par défaut pour les messages mis en quarantaine (nous n’utilisons pas le paramètre _MailboxIntelligenceQuarantineTag_).
- Active tous les conseils de sécurité.

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainsToProtect fabrikam.com -TargetedDomainProtectionAction Quarantine -EnableTargetedUserProtection $true -TargetedUsersToProtect "Mai Fujito;mfujito@fabrikam.com" -TargetedUserProtectionAction Quarantine -EnableMailboxIntelligence $true -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -EnableSimilarUsersSafetyTips $true -EnableSimilarDomainsSafetyTips $true -EnableUnusualCharactersSafetyTips $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Pour obtenir des instructions détaillées sur [](quarantine-policies.md) la spécification des stratégies de mise en quarantaine à utiliser dans une stratégie anti-hameçonnage, voir Utiliser PowerShell pour spécifier la stratégie de mise en quarantaine dans les stratégies [anti-hameçonnage](quarantine-policies.md#anti-phishing-policies).

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>Étape 2 : Utiliser PowerShell pour créer une règle anti-hameçonnage

Pour créer une règle anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Cet exemple crée une règle anti-hameçonnage nommée Research Department avec les conditions suivantes :

- La règle est associée à la stratégie anti-hameçonnage nommée Research Quarantine.
- La règle s’applique aux membres du groupe nommé Research Department.
- Étant donné que nous n’utilisons pas le _paramètre Priority_ , la priorité par défaut est utilisée.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Utiliser PowerShell pour afficher les stratégies anti-hameçonnage

Pour afficher les stratégies anti-hameçonnage existantes, utilisez la syntaxe suivante :

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie une liste récapitulatif de toutes les stratégies anti-hameçonnage, ainsi que les propriétés spécifiées.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

Cet exemple renvoie toutes les valeurs de propriété pour la stratégie anti-hameçonnage nommée Executives.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Utiliser PowerShell pour afficher les règles anti-hameçonnage

Pour afficher les règles anti-hameçonnage existantes, utilisez la syntaxe suivante :

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie une liste récapitulatif de toutes les règles anti-hameçonnage ainsi que les propriétés spécifiées.

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

Cet exemple renvoie toutes les valeurs de propriété pour la règle anti-hameçonnage nommée Contoso Executives.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Utiliser PowerShell pour modifier des stratégies anti-hameçonnage

Outre les éléments suivants, les mêmes paramètres sont disponibles lorsque vous modifiez une stratégie anti-hameçonnage dans PowerShell que lorsque vous créez la stratégie comme décrit à l’étape 1 : Utiliser PowerShell pour créer une section de stratégie [anti-hameçonnage](#step-1-use-powershell-to-create-an-anti-phish-policy) plus tôt dans cet article.

- Le _commutateur MakeDefault_ qui transforme la stratégie spécifiée en stratégie par défaut (appliquée à tout le monde, toujours la plus faible priorité et que vous ne pouvez pas supprimer) est disponible uniquement lorsque vous modifiez une stratégie anti-hameçonnage dans PowerShell.

- Vous ne pouvez pas renommer une stratégie anti-hameçonnage (la cmdlet **Set-AntiPhishPolicy** n’a pas de _paramètre Name_ ). Lorsque vous renommez une stratégie anti-hameçonnage dans le portail Microsoft 365 Defender, vous renommez uniquement la règle anti-hameçonnage.

Pour modifier une stratégie anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AntiPhishPolicy](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Pour obtenir des instructions détaillées sur [](quarantine-policies.md) la spécification des stratégies de mise en quarantaine à utiliser dans une stratégie anti-hameçonnage, voir Utiliser PowerShell pour spécifier la stratégie de mise en quarantaine dans les stratégies [anti-hameçonnage](quarantine-policies.md#anti-phishing-policies).

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Utiliser PowerShell pour modifier des règles anti-hameçonnage

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle anti-hameçonnage dans PowerShell est le paramètre _Enabled_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver des règles anti-hameçonnage existantes, consultez la section suivante.

Sinon, aucun paramètre supplémentaire n’est disponible lorsque vous modifiez une règle anti-hameçonnage dans PowerShell. Les mêmes paramètres sont disponibles lorsque vous créez une règle comme décrit à l’étape 2 : Utiliser PowerShell pour créer une section de règle [anti-hameçonnage](#step-2-use-powershell-to-create-an-anti-phish-rule) plus tôt dans cet article.

Pour modifier une règle anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AntiPhishRule](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Utiliser PowerShell pour activer ou désactiver des règles anti-hameçonnage

L’activation ou la désactivation d’une règle anti-hameçonnage dans PowerShell active ou désactive l’ensemble de la stratégie anti-hameçonnage (la règle anti-hameçonnage et la stratégie anti-hameçonnage affectée). Vous ne pouvez pas activer ou désactiver la stratégie anti-hameçonnage par défaut (elle est toujours appliquée à tous les destinataires).

Pour activer ou désactiver une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Enable-AntiPhishRule](/powershell/module/exchange/enable-antiphishrule) et [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

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

**Remarques** :

- Pour définir la priorité d’une nouvelle règle lorsque vous la créez, utilisez plutôt le paramètre _Priority_ de la cmdlet **New-AntiPhishRule** .

- La stratégie anti-hameçonnage par défaut n’a pas de règle anti-hameçonnage correspondante et a toujours la valeur de priorité nonmodifiable **La plus faible**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Utiliser PowerShell pour supprimer des stratégies anti-hameçonnage

Lorsque vous utilisez PowerShell pour supprimer une stratégie anti-hameçonnage, la règle anti-hameçonnage correspondante n’est pas supprimée.

Pour supprimer une stratégie anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

Cet exemple supprime la stratégie anti-hameçonnage nommée Marketing Department.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Utiliser PowerShell pour supprimer des règles anti-hameçonnage

Lorsque vous utilisez PowerShell pour supprimer une règle anti-hameçonnage, la stratégie anti-hameçonnage correspondante n’est pas supprimée.

Pour supprimer une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle anti-hameçonnage nommée Marketing Department.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-AntiPhishRule](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement configuré les stratégies anti-hameçonnage dans Defender pour Office 365, faites l’une des opérations suivantes :

- Dans la page **Anti-hameçonnage** du portail Microsoft 365 Defender <https://security.microsoft.com/antiphishing>, vérifiez la liste des stratégies, leurs valeurs d’état et leurs valeurs **de** priorité. Pour afficher plus de détails, sélectionnez la stratégie dans la liste en cliquant sur le nom et en visualnant les détails dans le volant qui s’affiche.

- Dans Exchange Online PowerShell, \<Name\> remplacez par le nom de la stratégie ou de la règle, puis exécutez la commande suivante et vérifiez les paramètres :

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
