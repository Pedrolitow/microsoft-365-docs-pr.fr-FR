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
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à créer, modifier et supprimer les stratégies anti-hameçonnage avancées disponibles dans les organisations avec Microsoft Defender pour Office 365.
ms.openlocfilehash: 7665d0dc475909d04da209aa6c1cd6b12378f8a9
ms.sourcegitcommit: f941495e9257a0013b4a6a099b66c649e24ce8a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48993387"
---
# <a name="configure-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Les stratégies anti-hameçonnage de [Microsoft Defender pour Office 365](office-365-atp.md) peuvent vous aider à protéger votre organisation contre les attaques d’hameçonnage malveillant basées sur l’emprunt d’identité et d’autres types d’attaques par hameçonnage. Pour plus d’informations sur les différences entre les stratégies de détection d’hameçonnage dans Exchange Online Protection (EOP) et les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, consultez la rubrique [anti-phishing protection](anti-phishing-protection.md).

Les administrateurs peuvent afficher, modifier et configurer (mais pas supprimer) la stratégie anti-hameçonnage par défaut. Pour une granularité accrue, vous pouvez également créer des stratégies anti-hameçonnage personnalisées qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez cependant modifier la priorité (l'ordre d'exécution) de vos stratégies personnalisées.

Vous pouvez configurer des stratégies anti-hameçonnage dans le centre de sécurité & conformité ou dans Exchange Online PowerShell.

Pour plus d’informations sur la configuration des stratégies de blocage plus limitées disponibles dans les organisations Exchange Online Protection (autrement dit, les organisations sans Microsoft Defender pour Office 365), voir [configure anti-phishing Policies in EOP](configure-anti-phishing-policies-eop.md).

Les éléments de base d’une stratégie anti-hameçonnage sont les suivants :

- **Stratégie anti-hameçonnage** : spécifie les protections de hameçonnage à activer ou à désactiver, ainsi que les actions à appliquer.
- **La règle anti-hameçonnage** : spécifie la priorité et les filtres de destinataire (auxquels s’applique la stratégie) pour une stratégie anti-hameçonnage.

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies de détection d’hameçonnage dans le centre de sécurité & Compliance Center :

- Lorsque vous créez une stratégie, vous créez en réalité une règle anti-hameçonnage et la stratégie anti-hameçonnage associée en même temps en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie, les paramètres associés aux filtres nom, priorité, activé ou désactivé et filtre de destinataires modifient la règle anti-hameçonnage. Tous les autres paramètres modifient la stratégie anti-hameçonnage associée.
- Lorsque vous supprimez une stratégie, la règle anti-hameçonnage et la stratégie anti-hameçonnage associée sont supprimées.

Dans Exchange Online PowerShell, vous gérez la stratégie et la règle séparément. Pour plus d’informations, reportez-vous à la section [utiliser Exchange Online PowerShell pour configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](#use-exchange-online-powershell-to-configure-anti-phishing-policies-in-microsoft-defender-for-office-365) plus loin dans cette rubrique.

Chaque organisation Microsoft Defender pour Office 365 dispose d’une stratégie anti-hameçonnage intégrée nommée Office antiphishing par défaut, qui comporte les propriétés suivantes :

- La stratégie est appliquée à tous les destinataires de l’organisation, même s’il n’y a aucune règle anti-hameçonnage (filtres de destinataire) associée à la stratégie.
- La stratégie a la valeur de priorité personnalisée la **plus petite** , que vous ne pouvez pas modifier (la stratégie est toujours appliquée en dernier). Les stratégies personnalisées que vous créez ont toujours une priorité plus élevée.
- La stratégie est la stratégie par défaut (la propriété **IsDefault** possède la valeur`True`) et vous ne pouvez pas supprimer la stratégie par défaut.

Pour accroître l’efficacité de la protection anti-hameçonnage dans Microsoft Defender pour Office 365, vous pouvez créer des stratégies anti-hameçonnage personnalisées avec des paramètres plus stricts appliqués à des utilisateurs ou à des groupes d’utilisateurs spécifiques.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **anti-hameçonnage ATP** , utilisez <https://protection.office.com/antiphishing> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

- Avant de pouvoir effectuer les procédures décrites dans cet article, vous devez disposer des autorisations suivantes :

  - Pour ajouter, modifier et supprimer des stratégies de détection d’hameçonnage, vous devez être membre de l’un des groupes de rôles suivants :

    - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation** ou **Gestion de l’hygiène** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

  - Pour un accès en lecture seule aux stratégies de détection d’hameçonnage, vous devez être membre de l’un des groupes de rôles suivants :

    - **Lecteur de sécurité** dans le [Centre de conformité et sécurité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

- Pour connaître les paramètres recommandés pour les stratégies de détection d’hameçonnage dans Microsoft Defender pour Office 365, reportez-vous à la rubrique [anti-phishing Policy in Defender for office 365 Settings](recommended-settings-for-eop-and-office365-atp.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

- Autoriser jusqu’à 30 minutes pour l’application d’une stratégie nouvelle ou mise à jour.

- Pour plus d’informations sur l’endroit où les stratégies anti-hameçonnage sont appliquées dans le pipeline de filtrage, consultez la rubrique [Order and Precedence of e-mail protection](how-policies-and-protections-are-combined.md).

## <a name="use-the-security--compliance-center-to-create-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser le centre de sécurité & conformité pour créer des stratégies de détection d’hameçonnage dans Microsoft Defender pour Office 365

La création d’une stratégie anti-hameçonnage personnalisée dans le centre de sécurité & conformité crée la règle anti-hameçonnage et la stratégie anti-hameçonnage associée en même temps en utilisant le même nom pour les deux.

Lorsque vous créez une stratégie anti-hameçonnage, vous pouvez uniquement spécifier le nom de la stratégie, sa description et le filtre de destinataire qui identifie la personne à laquelle la stratégie s’applique. Après avoir créé la stratégie, vous pouvez modifier la stratégie pour modifier ou consulter les paramètres anti-hameçonnage par défaut.

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** pour \> **Policy** \> **le hameçonnage**.

2. Sur la page **anti-hameçonnage** , cliquez sur **créer**.

3. L’Assistant **créer une stratégie anti-hameçonnage** s’ouvre. Sur la page **nommer votre stratégie** , configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie.

   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Sur la page **appliqué à** qui s’affiche, identifiez les destinataires internes auxquels s’applique la stratégie.

   Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_ ). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_ ).

   Cliquez sur **Ajouter une condition**. Dans la liste déroulante qui apparaît, sélectionnez une condition sous **appliqué si** :

   - **Le destinataire est** : spécifie une ou plusieurs boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie dans votre organisation.
   - **Le destinataire est membre de** : spécifie un ou plusieurs groupes dans votre organisation.
   - **Le domaine du destinataire est** : spécifie des destinataires dans un ou plusieurs domaines acceptés configurés dans l’organisation.

   Une fois que vous avez sélectionné la condition, une liste déroulante correspondante apparaît avec **une case à** cocher.

   - Cliquez dans la zone et faites défiler la liste des valeurs à sélectionner.
   - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionnez une valeur.
   - Pour ajouter des valeurs supplémentaires, cliquez dans une zone vide de la zone.
   - Pour supprimer des entrées individuelles, cliquez sur **supprimer** ![ ](../../media/scc-remove-icon.png) l’icône de suppression sur la valeur.
   - Pour supprimer l’ensemble de la condition, cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/scc-remove-icon.png) dans la condition.

   Pour ajouter une condition supplémentaire, cliquez sur **Ajouter une condition** et sélectionnez une valeur restante sous **appliqué**.

   Pour ajouter des exceptions, cliquez sur **Ajouter une condition** et sélectionnez une exception sous **sauf si**. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Sur la page **vérifier vos paramètres** qui s’affiche, vérifiez vos paramètres. Vous pouvez cliquer sur **modifier** sur chaque paramètre pour le modifier.

   Lorsque vous avez terminé, cliquez sur **créer cette stratégie**.

6. Cliquez sur **OK** dans la boîte de dialogue de confirmation qui s’affiche.

Après avoir créé la stratégie anti-hameçonnage avec ces paramètres généraux, suivez les instructions de la section suivante pour configurer les paramètres de protection dans la stratégie.

## <a name="use-the-security--compliance-center-to-modify-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser le centre de sécurité & conformité pour modifier les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Utilisez les procédures suivantes pour modifier les stratégies de détection d’hameçonnage : une nouvelle stratégie que vous avez créée ou des stratégies existantes que vous avez déjà personnalisées.

1. Si vous ne l’avez pas encore fait, ouvrez le centre de sécurité & conformité, **Threat management** puis accédez à \> **Policy** \> **protection contre les menaces pour le hameçonnage**.

2. Sélectionnez la stratégie anti-hameçonnage personnalisée que vous souhaitez modifier. Si elle est déjà sélectionnée, désactivez-la et sélectionnez-la à nouveau.

3. Le menu volant **modifier \<name\> votre stratégie** apparaît. Si vous cliquez sur **modifier** dans une section, vous pouvez accéder aux paramètres de cette section.

   - Les étapes suivantes sont présentées dans l’ordre dans lequel les sections apparaissent, mais elles ne sont pas séquentielles (vous pouvez sélectionner et modifier les sections dans n’importe quel ordre).

   - Une fois que vous avez cliqué sur **modifier** dans une section, les paramètres disponibles sont présentés dans un format d’Assistant, mais vous pouvez sauter les pages dans n’importe quel ordre, et vous pouvez cliquer sur **Enregistrer** sur n’importe quelle page (ou sur **Annuler** ou **Fermer** l' ![ icône ](../../media/scc-remove-icon.png) pour revenir à la page **modifier votre stratégie \<name\>** (vous n’avez pas besoin de consulter la dernière page de l’Assistant pour enregistrer ou quitter

4. **Paramètre de stratégie** : cliquez sur **modifier** pour modifier les mêmes paramètres que ceux qui étaient disponibles lorsque vous avez [créé la stratégie](#use-the-security--compliance-center-to-create-anti-phishing-policies-in-microsoft-defender-for-office-365) dans la section précédente :

   - **Name**
   - **Description**
   - **Appliqué à**
   - **Vérifier vos paramètres**

   Lorsque vous avez terminé, cliquez sur **Enregistrer** sur une page.

5. **Emprunt d’identité** : cliquez sur **modifier** pour modifier les expéditeurs et les domaines protégés protégés dans la stratégie. Ces paramètres sont une condition pour la stratégie qui identifie les expéditeurs usurpés à rechercher (individuellement ou par domaine) dans l’adresse de provenance des messages entrants. Pour plus d’informations, reportez-vous à la rubrique [emprunt d’identité des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   - **Ajouter des utilisateurs à protéger** : la valeur par défaut est **off**. Pour l’activer, faites glisser le bouton bascule sur **activé** , puis cliquez sur le bouton **Ajouter un utilisateur** qui s’affiche.

     Dans la fenêtre mobile **Ajouter un utilisateur** qui s’affiche, configurez les valeurs suivantes :

     - **Adresse de messagerie** :

       - Cliquez dans la zone et faites défiler la liste des utilisateurs à sélectionner.
       - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionnez un utilisateur.
       - Pour supprimer une entrée, cliquez sur **supprimer** ![ l’icône Supprimer ](../../media/scc-remove-icon.png) de l’utilisateur.

     - **Name** : cette valeur est renseignée en fonction de l’adresse de messagerie que vous avez sélectionnée, mais vous pouvez la modifier.

     Lorsque vous avez terminé, cliquez sur **Enregistrer** sur une page.

     Pour modifier une entrée existante, sélectionnez-la dans la liste.

     > [!NOTE]
     >
     > - Dans chaque stratégie anti-hameçonnage, vous pouvez spécifier un maximum de 60 utilisateurs protégés (adresses e-mail de l’expéditeur). Vous ne pouvez pas spécifier le même utilisateur protégé dans plusieurs stratégies.
     >
     > - La protection contre l’usurpation d’identité d’utilisateur ne fonctionne pas si l’expéditeur et le destinataire ont déjà communiqué par courrier électronique. Si l’expéditeur et le destinataire n’ont jamais communiqué par courrier électronique, le message est identifié en tant que tentative d’emprunt d’identité.

   - **Ajouter des domaines à protéger** : configurez l’un des paramètres suivants ou les deux :

     - **Inclure automatiquement les domaines dont je suis propriétaire** : la valeur par défaut est **off**. Pour l’activer, faites glisser le bouton bascule sur **activé**.
     - **Inclure les domaines personnalisés** : la valeur par défaut est **off**. Pour l’activer, faites glisser le bouton bascule sur **activé** , puis dans la zone **Ajouter des domaines** , entrez le nom de domaine (par exemple, contoso.com), appuyez sur entrée et répétez l’opération si nécessaire.

     > [!NOTE]
     > Vous pouvez avoir un maximum de 50 domaines dans toutes les stratégies de détection d’hameçonnage.

   - **Actions** : cliquez sur **modifier**

     - **Si un message électronique est envoyé par un utilisateur représenté** : configurez l’une des actions suivantes pour les messages dans lesquels l’expéditeur usurpé est l’un des utilisateurs protégés que vous avez spécifié dans **Ajouter des utilisateurs à protéger** :

       - **Ne pas appliquer d’action**
       - **Rediriger le message vers d’autres adresses de messagerie**
       - **Déplacer le message dans le dossier Courrier indésirable**
       - **Mettre en quarantaine le message**
       - **Remise du message et ajout d’autres adresses à la ligne CCI**
       - **Supprimer le message avant qu’il ne soit remis**

     - **Si le courrier électronique est envoyé par un domaine emprunté** : configurez l’une des actions suivantes pour les messages dans lesquels l’expéditeur usurpé se trouve dans l’un des domaines protégés que vous avez spécifiés dans **Ajouter des domaines à protéger** :

       - **Ne pas appliquer d’action**
       - **Rediriger le message vers d’autres adresses de messagerie**
       - **Déplacer le message dans le dossier Courrier indésirable**
       - **Mettre en quarantaine le message**
       - **Remise du message et ajout d’autres adresses à la ligne CCI**
       - **Supprimer le message avant qu’il ne soit remis**

   - Cliquez sur **conseils de sécurité pour l’emprunt d’identité** et configurez les paramètres suivants :

     - **Afficher l’astuce pour les utilisateurs empruntés** : la valeur par défaut est **off**. Pour l’activer, faites glisser le bouton bascule sur **activé**.
     - **Afficher le Conseil pour les domaines empruntés** : la valeur par défaut est **off**. Pour l’activer, faites glisser le bouton bascule sur **activé**.
     - **Afficher le Conseil pour les caractères inhabituels** : la valeur par défaut est **off**. Pour l’activer, faites glisser le bouton bascule sur **activé**.

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Intelligence des boîtes aux lettres** :

     - **Activer l’intelligence des boîtes aux lettres ?** : la valeur par défaut est **activé**. Pour le désactiver, faites glisser le bouton de bascule sur **désactivé**.

     - **Activer la protection contre l’usurpation d’identité basée sur les boîtes aux lettres ?** : ce paramètre est disponible uniquement si **activer l’intelligence des boîtes aux lettres** est **activé**.

       Dans **si un message électronique est envoyé par un utilisateur emprunté** , vous pouvez spécifier l’une des actions suivantes à effectuer sur les messages qui échouent à la boîte aux lettres (les mêmes actions que celles disponibles pour les utilisateurs protégés et les domaines protégés) :

       - **Ne pas appliquer d’action**
       - **Rediriger le message vers d’autres adresses de messagerie**
       - **Déplacer le message dans le dossier Courrier indésirable**
       - **Mettre en quarantaine le message**
       - **Remise du message et ajout d’autres adresses à la ligne CCI**
       - **Supprimer le message avant qu’il ne soit remis**

   - **Ajouter des expéditeurs et des domaines approuvés** : spécifiez les exceptions pour la stratégie :

     - **Expéditeurs approuvés** :

       - Cliquez dans la zone et faites défiler la liste des utilisateurs à sélectionner.
       - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionnez un utilisateur.
       - Pour supprimer une entrée, cliquez sur **supprimer** ![ l’icône Supprimer ](../../media/scc-remove-icon.png) de l’utilisateur.

     - **Domaines approuvés** : saisissez le nom de domaine (par exemple, contoso.com), appuyez sur entrée et répétez l’opération autant de fois que nécessaire.

   - **Vérifiez vos paramètres** : au lieu de cliquer sur chaque étape individuelle, les paramètres sont affichés dans un résumé.

     - Vous pouvez cliquer sur **modifier** dans chaque section pour revenir à la page appropriée.
     - Vous pouvez activer ou **Désactiver** les paramètres suivants **directement sur cette** page :

       - **Utilisateurs protégés**
       - **Domaines protégés** \> **Inclure les domaines dont je suis propriétaire**
       - **Domaines protégés** \> **Domaines protégés** (domaines personnalisés)
       - **Veille des boîtes aux lettres**

   Lorsque vous avez terminé, cliquez sur **Enregistrer** sur une page.

6. **Spoof** : cliquez sur **modifier** pour activer ou désactiver l’Assistant usurpation d’identité, activez ou désactivez l’identification de l’expéditeur non authentifié dans Outlook, puis configurez l’action à appliquer aux messages provenant d’expéditeurs usurpés bloqués. Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings).

   Notez que ces mêmes paramètres sont également disponibles dans les stratégies de détection d’hameçonnage dans EOP.

   - **Usurpation des paramètres de filtrage** : la valeur par défaut est **activée** , et nous vous recommandons de la laisser activée. Pour le désactiver, faites glisser le bouton de bascule sur **désactivé**. Pour plus d’informations, consultez la rubrique [configure usurpation Intelligence in EOP](learn-about-spoof-intelligence.md).

     > [!NOTE]
     > Vous n’avez pas besoin de désactiver la protection contre l’usurpation d’identité si votre enregistrement MX ne pointe pas vers Microsoft 365 ; vous activez le filtrage amélioré pour les connecteurs à la place. Pour obtenir des instructions, voir [Enhanced Filtering for Connectors in Exchange Online](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   - **Activer la fonctionnalité d’expéditeur non authentifié** : la valeur par défaut est **activé**. Pour le désactiver, faites glisser le bouton de bascule sur **désactivé**.

   - **Actions** : spécifiez l’action à effectuer sur les messages qui échouent à l’aide d’usurpation d’identité :

     **Si un message électronique est envoyé par un utilisateur qui n’est pas autorisé à usurper votre domaine** :

     - **Déplacer le message vers les dossiers de courrier indésirable des destinataires**
     - **Mettre en quarantaine le message**

   - **Vérifiez vos paramètres** : au lieu de cliquer sur chaque étape individuelle, les paramètres sont affichés dans un résumé.

     - Vous pouvez cliquer sur **modifier** dans chaque section pour revenir à la page appropriée.
     - Vous pouvez activer ou **Désactiver** les paramètres suivants **directement sur cette** page :
       - **Activer la protection contre l’usurpation d’identité**
       - **Activer la fonctionnalité d’expéditeur non authentifié**

   Lorsque vous avez terminé, cliquez sur **Enregistrer** sur une page.

7. **Paramètres avancés** : cliquez sur **modifier** pour configurer les seuils avancés de hameçonnage. Pour plus d’informations, reportez-vous à [seuils d’hameçonnage avancés dans la rubrique anti-hameçonnage Policies in Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   - **Seuils de hameçonnage avancés** : sélectionnez l’une des valeurs suivantes :

   - **1-standard** (il s’agit de la valeur par défaut.)
   - **2-agressif**
   - **3-plus agressif**
   - **4-le plus agressif**

   - **Vérifiez vos paramètres** : cliquez sur **modifier** pour revenir à la page **seuils avancés de hameçonnage** .

   Lorsque vous avez terminé, cliquez sur **Enregistrer** sur une page.

8. Sur la page **modifier votre stratégie \<Name\>** , vérifiez vos paramètres, puis cliquez sur **Fermer**.

### <a name="use-the-security--compliance-center-to-modify-the-default-anti-phishing-policy-in-microsoft-defender-for-office-365"></a>Utiliser le centre de sécurité & conformité pour modifier la stratégie anti-hameçonnage par défaut dans Microsoft Defender pour Office 365

La stratégie anti-hameçonnage par défaut dans Microsoft Defender pour Office 365 est appelée Office antiphishing par défaut et n’apparaît pas dans la liste des stratégies. Pour modifier la stratégie anti-hameçonnage par défaut, procédez comme suit :

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** pour \> **Policy** \> **le hameçonnage**.

2. Sur la page **anti-hameçonnage** , cliquez sur **stratégie par défaut**.

3. La page **modifier votre stratégie d’anti-hameçonnage Office 365 par défaut** apparaît. Les sections suivantes sont disponibles, qui contiennent les paramètres identiques lorsque vous [modifiez une stratégie personnalisée](#use-the-security--compliance-center-to-modify-anti-phishing-policies-in-microsoft-defender-for-office-365):

   - **Emprunt d’identité**
   - **Tromp**
   - **Paramètres avancés**

   Les paramètres suivants ne sont pas disponibles lorsque vous modifiez la stratégie par défaut :

   - Vous pouvez voir la section paramètres de **stratégie** et les valeurs, mais il n’existe aucun lien de **modification** , afin que vous ne puissiez pas modifier les paramètres (nom de stratégie, description et personnes auxquelles la stratégie s’applique (elle s’applique à tous les destinataires)).
   - Vous ne pouvez pas supprimer la stratégie par défaut.
   - Vous ne pouvez pas modifier la priorité de la stratégie par défaut (elle est toujours appliquée en dernier).

4. Sur la page **modifier votre stratégie par défaut pour les antiphishing Office 365** , vérifiez vos paramètres, puis cliquez sur **Fermer**.

### <a name="enable-or-disable-custom-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Activer ou désactiver les stratégies anti-hameçonnage personnalisées dans Microsoft Defender pour Office 365

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** pour \> **Policy** \> **le hameçonnage**.

2. Notez la valeur dans la colonne **État** :

   - Faites glisser le bouton bascule sur **désactivé** pour désactiver la stratégie.

   - Faites glisser le bouton bascule sur **activé** pour activer la stratégie.

Vous ne pouvez pas désactiver la stratégie anti-hameçonnage par défaut.

### <a name="set-the-priority-of-custom-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Définir la priorité des stratégies anti-hameçonnage personnalisées dans Microsoft Defender pour Office 365

Par défaut, les stratégies de détection d’hameçonnage reçoivent une priorité basée sur l’ordre dans lequel elles ont été créées (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

Les stratégies anti-hameçonnage personnalisées sont affichées dans l’ordre dans lequel elles sont traitées (la première stratégie a la valeur de **priorité** 0). La stratégie anti-hameçonnage par défaut nommée Office antiphishing par défaut a une valeur de priorité personnalisée la **plus faible** et vous ne pouvez pas la modifier.

 **Remarque** : dans le centre de sécurité & conformité, vous pouvez uniquement modifier la priorité de la stratégie anti-hameçonnage une fois que vous l’avez créée. Dans PowerShell, vous pouvez remplacer la priorité par défaut lors de la création de la règle anti-hameçonnage (qui peut avoir une incidence sur la priorité des règles existantes).

Pour modifier la priorité d’une stratégie, cliquez sur **augmenter la priorité** ou sur **diminuer la priorité** dans les propriétés de la stratégie (vous ne pouvez pas modifier directement le numéro de **priorité** dans le centre de sécurité & conformité). La modification de la priorité d’une stratégie n’a de sens que si vous disposez de plusieurs stratégies.

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** pour \> **Policy** \> **le hameçonnage**.

2. Sélectionnez la stratégie que vous souhaitez modifier. Si elle est déjà sélectionnée, désactivez-la et sélectionnez-la à nouveau.

3. Le menu volant **modifier \<name\> votre stratégie** apparaît.

   - La stratégie anti-hameçonnage personnalisée avec la valeur **Priority** de priorité **0** a uniquement le bouton **diminuer la priorité** disponible.

   - La stratégie anti-hameçonnage personnalisée avec la valeur de **priorité** la plus faible (par exemple, **3** ) a uniquement le bouton **augmenter la priorité** disponible.

   - Si vous avez au moins trois stratégies anti-hameçonnage personnalisées, les stratégies de priorité la plus élevée et la plus faible ont les deux boutons **augmenter la priorité** et **diminuer la priorité** .

4. Cliquez sur **augmenter** la priorité ou sur **diminuer la priorité** pour modifier la valeur de **priorité** .

5. Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="use-the-security--compliance-center-to-view-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser le centre de sécurité & conformité pour afficher les stratégies de détection d’hameçonnage dans Microsoft Defender pour Office 365

1. Dans le centre de sécurité & conformité, puis accédez **Threat management** à \> **Policy** \> **protection contre les** menaces pour le hameçonnage.

2. Effectuez l’une des étapes suivantes :

   - Sélectionnez une stratégie anti-hameçonnage personnalisée que vous souhaitez afficher. Si elle est déjà sélectionnée, désactivez-la et sélectionnez-la à nouveau.

   - Cliquez sur **stratégie par défaut** pour afficher la stratégie anti-hameçonnage par défaut.

3. Le menu volant **modifier \<name\> votre stratégie** apparaît, dans lequel vous pouvez afficher les paramètres et les valeurs.

## <a name="use-the-security--compliance-center-to-remove-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser le centre de sécurité & conformité pour supprimer les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** pour \> **Policy** \> **le hameçonnage**.

2. Sélectionnez la stratégie que vous souhaitez supprimer. Si elle est déjà sélectionnée, désactivez-la et sélectionnez-la à nouveau.

3. Dans le menu volant **modifier \<name\> votre stratégie** qui s’affiche, cliquez sur **Supprimer la stratégie** , puis cliquez sur **Oui** dans la boîte de dialogue d’avertissement qui s’affiche.

Vous ne pouvez pas supprimer la stratégie par défaut.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser Exchange Online PowerShell pour configurer les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Comme décrit précédemment, une stratégie de blocage du courrier indésirable se compose d’une stratégie anti-hameçonnage et d’une règle anti-hameçonnage.

Dans Exchange Online PowerShell, la différence entre les stratégies anti-hameçonnage et les règles anti-hameçonnage est apparente. Vous pouvez gérer les stratégies anti-hameçonnage à l’aide des cmdlets **\* -antiphishpolicy permet** et gérer les règles anti-hameçonnage à l’aide des cmdlets **\* -antiphishrule permet** .

- Dans PowerShell, vous devez d’abord créer la stratégie anti-hameçonnage, puis créer la règle anti-hameçonnage qui identifie la stratégie à laquelle s’applique la règle.
- Dans PowerShell, vous modifiez les paramètres de la stratégie anti-hameçonnage et de la règle anti-hameçonnage séparément.
- Lorsque vous supprimez une stratégie anti-hameçonnage de PowerShell, la règle anti-hameçonnage correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Utiliser PowerShell pour créer des stratégies anti-hameçonnage

La création d’une stratégie anti-hameçonnage dans PowerShell est un processus en deux étapes :

1. Créez la stratégie anti-hameçonnage.
2. Créez la règle anti-hameçonnage qui spécifie la stratégie anti-hameçonnage à laquelle la règle s’applique.

 **Remarques**  :

- Vous pouvez créer une nouvelle règle anti-hameçonnage et lui affecter une stratégie anti-hameçonnage existante non associée. Une règle anti-hameçonnage ne peut pas être associée à plusieurs stratégies anti-hameçonnage.

- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies anti-hameçonnage de PowerShell qui ne sont pas disponibles dans le centre de sécurité & de sécurité tant que vous n’avez pas créé la stratégie :

  - Créez la nouvelle stratégie comme désactivé ( _activé_ `$false` sur la cmdlet **New-antiphishrule permet** ).
  - Définir la priorité de la stratégie lors de la création ( _priorité_ _\<Number\>_ ) sur la cmdlet **New-antiphishrule permet** ).

- Une nouvelle stratégie anti-hameçonnage que vous créez dans PowerShell n’est pas visible dans le centre de sécurité & de conformité tant que vous n’avez pas affecté la stratégie à une règle anti-hameçonnage.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>Étape 1 : utiliser PowerShell pour créer une stratégie anti-hameçonnage

Pour créer une stratégie anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Cet exemple crée une stratégie anti-hameçonnage nommée Research Quarantine avec les paramètres suivants :

- La stratégie est activée (nous n’utilisons pas le paramètre _Enabled_ et la valeur par défaut est `$true` ).
- Description : stratégie de service de recherche.
- Active la protection des domaines de l’Organisation pour tous les domaines acceptés et la protection des domaines ciblés pour fabrikam.com.
- Spécifie Mai Fujito (mfujito@fabrikam.com) en tant qu’utilisateur pour empêcher l’emprunt d’identité.
- Active la boîte aux lettres décisionnelle.
- Active la protection contre les boîtes aux lettres et spécifie l’action de mise en quarantaine.
- Active les conseils de sécurité.

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainsToProtect fabrikam.com -TargetedDomainProtectionAction Quarantine -EnableTargetedUserProtection $true -TargetedUsersToProtect "Mai Fujito;mfujito@fabrikam.com" -TargetedUserProtectionAction Quarantine -EnableMailboxIntelligence $true -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -EnableSimilarUsersSafetyTips $true -EnableSimilarDomainsSafetyTips $true -EnableUnusualCharactersSafetyTips $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-antiphishpolicy permet](https://docs.microsoft.com/powershell/module/exchange/New-AntiPhishPolicy).

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>Étape 2 : utiliser PowerShell pour créer une règle anti-hameçonnage

Pour créer une règle anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Cet exemple crée une règle anti-hameçonnage nommée Research Department avec les conditions suivantes :

- La règle est associée à la stratégie anti-hameçonnage nommée Research Quarantine.
- La règle s’applique aux membres du groupe nommé Research Department.
- Étant donné que nous n’utilisons pas le paramètre _Priority_ , la priorité par défaut est utilisée.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-antiphishrule permet](https://docs.microsoft.com/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Utiliser PowerShell pour afficher les stratégies anti-hameçonnage

Pour afficher les stratégies anti-hameçonnage existantes, utilisez la syntaxe suivante :

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie la liste récapitulative de toutes les stratégies anti-hameçonnage, ainsi que les propriétés spécifiées.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

Cet exemple renvoie toutes les valeurs de propriété pour la stratégie anti-hameçonnage nommée Executives.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-antiphishpolicy permet](https://docs.microsoft.com/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Utiliser PowerShell pour afficher les règles de hameçonnage

Pour afficher les règles anti-hameçonnage existantes, utilisez la syntaxe suivante :

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie la liste récapitulative de toutes les règles anti-hameçonnage, ainsi que les propriétés spécifiées.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-antiphishrule permet](https://docs.microsoft.com/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Utiliser PowerShell pour modifier des stratégies anti-hameçonnage

À l’exception des éléments suivants, les mêmes paramètres sont disponibles lorsque vous modifiez une stratégie anti-hameçonnage dans PowerShell comme lors de la création de la stratégie, comme décrit dans la section [étape 1 : utiliser PowerShell pour créer une stratégie anti-hameçonnage](#step-1-use-powershell-to-create-an-anti-phish-policy) plus haut dans cette rubrique.

- Le commutateur _MakeDefault_ qui désactive la stratégie spécifiée dans la stratégie par défaut (appliquée à tout le monde, toujours à la priorité la **plus basse** et vous ne pouvez pas le supprimer) n’est disponible que lorsque vous modifiez une stratégie anti-hameçonnage dans PowerShell.

- Vous ne pouvez pas renommer une stratégie anti-hameçonnage (l’applet de commande **Set-antiphishpolicy permet** n’a pas de paramètre _Name_ ). Lorsque vous renommez une stratégie anti-hameçonnage dans le centre de sécurité & conformité, vous renommez uniquement la _règle_ anti-hameçonnage.

Pour modifier une stratégie anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-antiphishpolicy permet](https://docs.microsoft.com/powershell/module/exchange/Set-AntiPhishPolicy).

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Utiliser PowerShell pour modifier des règles anti-hameçonnage

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle anti-hameçonnage dans PowerShell est le paramètre _activé_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver les règles anti-hameçonnage existantes, reportez-vous à la section suivante.

Dans le cas contraire, aucun paramètre supplémentaire n’est disponible lorsque vous modifiez une règle anti-hameçonnage dans PowerShell. Les mêmes paramètres sont disponibles lorsque vous créez une règle, comme décrit dans la section [étape 2 : utiliser PowerShell pour créer une règle anti-hameçonnage](#step-2-use-powershell-to-create-an-anti-phish-rule) , plus haut dans cette rubrique.

Pour modifier une règle anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-antiphishrule permet](https://docs.microsoft.com/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Utiliser PowerShell pour activer ou désactiver les règles anti-hameçonnage

L’activation ou la désactivation d’une règle anti-hameçonnage dans PowerShell active ou désactive la totalité de la stratégie anti-hameçonnage (la règle anti-hameçonnage et la stratégie anti-hameçonnage affectée). Vous ne pouvez pas activer ou désactiver la stratégie anti-hameçonnage par défaut (elle est toujours appliquée à tous les destinataires).

Pour activer ou désactiver une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Enable-antiphishrule permet](https://docs.microsoft.com/powershell/module/exchange/enable-antiphishrule) et [Disable-antiphishrule permet](https://docs.microsoft.com/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Utiliser PowerShell pour définir la priorité des règles anti-hameçonnage

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d’une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Remarques**  :

- Pour définir la priorité d’une nouvelle règle lors de sa création, utilisez plutôt le paramètre _Priority_ sur la cmdlet **New-antiphishrule permet** .

- La stratégie anti-hameçonnage par défaut n’a pas de règle anti-hameçonnage correspondante, elle a toujours la valeur de priorité non modifiable la **plus faible**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Utiliser PowerShell pour supprimer des stratégies anti-hameçonnage

Lorsque vous utilisez PowerShell pour supprimer une stratégie anti-hameçonnage, la règle anti-hameçonnage correspondante n’est pas supprimée.

Pour supprimer une stratégie anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

Cet exemple supprime la stratégie anti-hameçonnage nommée Marketing Department.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-antiphishpolicy permet](https://docs.microsoft.com/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Utiliser PowerShell pour supprimer des règles anti-hameçonnage

Lorsque vous utilisez PowerShell pour supprimer une règle anti-hameçonnage, la stratégie anti-hameçonnage correspondante n’est pas supprimée.

Pour supprimer une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle anti-hameçonnage nommée Marketing Department.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-antiphishrule permet](https://docs.microsoft.com/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez bien configuré les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, effectuez l’une des opérations suivantes :

- Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** pour \> **Policy** \> **le hameçonnage**. Vérifiez la liste des stratégies, leurs valeurs d' **État** et leurs valeurs de **priorité** . Pour afficher plus de détails, effectuez l’une des opérations suivantes :

  - Sélectionnez la stratégie dans la liste, puis affichez les détails dans le menu volant.
  - Cliquez sur **stratégie par défaut** et affichez les détails dans le menu volant.

- Dans Exchange Online PowerShell, remplacez \<Name\> par le nom de la stratégie ou de la règle, puis exécutez la commande suivante et vérifiez les paramètres :

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
