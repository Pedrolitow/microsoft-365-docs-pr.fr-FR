---
title: Protéger contre les menaces
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
localization_priority: Normal
ms.date: 09/08/2020
search.appverid:
- MOE150
- MET150
ms.assetid: b10023f6-f30f-45d3-b3ad-b71aa4aa0d58
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent en savoir plus sur la protection contre Microsoft 365 et configurer son utilisation pour votre organisation.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5d61b17fc4575249bb592fc4ca865c34a628361a
ms.sourcegitcommit: 337e8d8a2fee112d799edd8a0e04b3a2f124f900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "52878327"
---
# <a name="protect-against-threats"></a>Protéger contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Voici un guide de démarrage rapide qui décompose la configuration de Defender Office 365 en blocs. Si vous débutez avec les fonctionnalités de protection contre les menaces dans Office 365, que vous ne savez pas par où commencer, ou si vous apprenez mieux en faisant *cela,* utilisez ces instructions comme liste de contrôle et point de départ.

> [!IMPORTANT]
> **Les paramètres recommandés** initiaux sont inclus pour chaque type de stratégie ; toutefois, de nombreuses options sont disponibles et vous pouvez ajuster vos paramètres pour répondre aux besoins spécifiques de votre organisation. Laissez environ 30 minutes à vos stratégies ou modifications pour qu’elles fonctionnent dans votre centre de données.

## <a name="requirements"></a>Conditions requises

### <a name="subscriptions"></a>Abonnements

Les fonctionnalités de protection contre les menaces sont *incluses* dans tous les abonnements Office 365 Microsoft ; toutefois, certains abonnements disposent de fonctionnalités avancées. Le tableau ci-dessous répertorie les fonctionnalités de protection incluses dans cet article, ainsi que les exigences minimales d’abonnement.

> [!TIP]
> Notez qu’au-delà des instructions  pour activer l’audit, les étapes de démarrage de la protection anti-programme malveillant, anti-hameçonnage et anti-courrier indésirable, qui sont marquées dans le cadre de Office 365 Exchange Online Protection (**EOP**). Cela peut sembler étrange dans un article defender pour Office 365, jusqu’à ce que vous vous rappeliez (**Defender pour Office 365**) contient et s’appuie sur EOP.

<br>

****

|Type de protection|Configuration requise pour l’abonnement|
|---|---|
|Journalisation d’audit (à des fins de rapport)|[Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Protection anti-programme malveillant|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Protection anti-hameçonnage|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Protection anti-courrier indésirable|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Purge automatique de zéro heure (pour le courrier électronique)|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Protection contre les URL et fichiers malveillants dans les e-mails Office documents (liens et pièces jointes sécurisées)|[Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|
|Activer les pièces jointes sécurisées pour SharePoint charges OneDrive, Microsoft Teams charges de travail|[Microsoft Defender pour Office 365](turn-on-mdo-for-spo-odb-and-teams.md)|
|Protection avancée contre le hameçonnage|[Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Rôles et autorisations

Pour configurer Defender pour les stratégies Office 365, vous devez avoir un rôle approprié dans le Centre de sécurité [& conformité.](/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center) Voir le tableau ci-dessous pour les rôles qui peuvent faire ces actions.

<br>

****

|Rôle ou groupe de rôles|Où en savoir plus|
|---|---|
|administrateur général|[À propos des rôles d’administrateur Microsoft 365](../../admin/add-users/about-admin-roles.md)|
|Administrateur de sécurité|[Autorisations des rôles d’administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Gestion d’Organisation Exchange Online|[Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo) <p> et <p> [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)|
|

Pour plus d’informations, voir Autorisations dans le [Centre de sécurité & conformité.](permissions-in-the-security-and-compliance-center.md)

### <a name="turn-on-audit-logging-for-reporting-and-investigation"></a>Activer la journalisation d’audit pour la rapport et l’examen

- Démarrez votre journalisation d’audit tôt. Pour certaines des étapes  suivantes, l’audit doit être en cours. La journalisation d’audit est disponible dans les abonnements qui [incluent Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Pour afficher les données dans les rapports de [](view-email-security-reports.md)protection contre les menaces, tels que le tableau de bord de [sécurité,](security-dashboard.md)les rapports de sécurité du courrier électronique et [l’Explorateur,](threat-explorer.md)la journalisation d’audit doit être *sur .* Pour en savoir plus, voir Activer ou désactiver la [recherche dans le journal d’audit.](../../compliance/turn-audit-log-search-on-or-off.md)

## <a name="part-1---anti-malware-protection-in-eop"></a>Partie 1 : protection contre les programmes malveillants dans EOP

Pour plus d’informations sur les paramètres recommandés pour la protection contre les programmes malveillants, voir les paramètres de stratégie [anti-programme malveillant EOP.](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)

1. Ouvrez <https://security.microsoft.com/antimalwarev2> .

2. Dans la page **Anti-programme** malveillant, sélectionnez la stratégie nommée **Stratégie** par défaut en cliquant sur le nom.

3. Dans le volant de détails de stratégie qui s’ouvre, cliquez sur Modifier les paramètres de **protection,** puis configurez les paramètres suivants :
   - Sélectionnez **Activer le filtre des pièces jointes courantes** pour activer le filtre de pièces jointes communes. Cliquez **sur Personnaliser les types de fichiers** pour ajouter d’autres types de fichiers.
   - Vérifiez que **la fonction Activer la purge automatique heure zéro pour les programmes** malveillants est sélectionnée.
   - Vérifiez qu’aucun des paramètres de la section **Notification** n’est sélectionné.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. Dans le menu volant des détails de la stratégie, cliquez sur **Fermer**.

Pour obtenir des instructions détaillées sur la configuration des stratégies anti-programme malveillant, voir Configurer des stratégies [anti-programme malveillant dans EOP.](configure-anti-malware-policies.md)

## <a name="part-2---anti-phishing-protection-in-eop-and-defender-for-office-365"></a>Partie 2 : protection anti-hameçonnage dans EOP et Defender pour Office 365

[La protection anti-hameçonnage](anti-phishing-protection.md) est disponible dans les abonnements qui incluent [EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). La protection anti-hameçonnage avancée est disponible dans [Defender pour les Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

Pour plus d’informations sur les paramètres recommandés pour les stratégies anti-hameçonnage, consultez les paramètres de stratégie [anti-hameçonnage EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) et de stratégie [anti-hameçonnage](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)dans Microsoft Defender pour Office 365 .

La procédure suivante décrit comment configurer la stratégie anti-hameçonnage par défaut. Paramètres disponibles uniquement dans Defender pour les Office 365 sont clairement marqués.

1. Ouvrez <https://security.microsoft.com/antiphishing> .

2. Dans la page **Anti-hameçonnage,** sélectionnez la stratégie **office 365** anti-hameçonnage par défaut (par défaut) en cliquant sur le nom.

3. Dans le volant de détails de stratégie qui s’affiche, configurez les paramètres suivants :

   - **Seuil de hameçonnage & section protection** : cliquez sur Modifier les **paramètres** de protection et configurez les paramètres suivants dans le flyout Modifier les **paramètres** de protection qui s’ouvre :
     - **Seuil de courrier d’hameçonnage** <sup>\*</sup> : **sélectionnez 2 - Agressif** (Standard) ou **3 - Plus agressif** (strict).
     - **Section Emprunt d’identité** <sup>\*</sup> : configurez les valeurs suivantes :
       - Sélectionnez Activer la protection des **utilisateurs,** cliquez sur le lien Gérer **(nn)** les expéditeurs qui s’affiche, puis ajoutez des expéditeurs internes et externes pour vous protéger contre l’emprunt d’identité, tels que les membres du conseil d’administration de votre organisation, votre PDG, votre directeur financier et d’autres cadres supérieurs.
       - Sélectionnez **Activer les domaines à protéger,** puis configurez les paramètres suivants qui s’affichent :
         - Sélectionnez **Inclure les domaines que** je possède pour protéger les expéditeurs internes dans vos domaines acceptés (visibles en cliquant sur Afficher mes domaines) contre l’emprunt d’identité. 
         - Pour protéger les expéditeurs dans d’autres domaines, sélectionnez Inclure des domaines **personnalisés,** cliquez sur le **lien Gérer (nn)** des domaines personnalisés qui s’affiche, puis ajoutez d’autres domaines pour vous protéger contre l’emprunt d’identité.
     - Section Ajouter des **expéditeurs** et des domaines de confiance : cliquez sur Gérer <sup>\*</sup> **(nn)** les expéditeurs et domaines de confiance pour configurer des exceptions de domaine d’expéditeur et d’expéditeur pour la protection contre l’emprunt d’identité si nécessaire.
     - Paramètres d’intelligence de boîte aux lettres : vérifiez que les paramètres Activer l’intelligence des boîtes aux lettres et Activer l’intelligence pour la protection contre l’emprunt <sup>\*</sup> d’identité sont sélectionnés.  
     - **Section Usurpation** : Vérifiez que **l’intelligence contre** l’usurpation d’identité est sélectionnée.

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Section Actions** : cliquez **sur Modifier les actions** et configurez les paramètres suivants dans le flyout Modifier les **actions** qui s’ouvre :
     - **Section Actions de** message : Configurez les paramètres suivants :
       - **Si le message est détecté comme un utilisateur** dont l’identité est usurpée : <sup>\*</sup> sélectionnez mettre le message en **quarantaine.**
       - **Si le message est détecté comme un domaine** dont l’identité est usurpée : <sup>\*</sup> sélectionnez mettre le message en **quarantaine.**
       - **Si l’intelligence de** boîte aux lettres détecte un utilisateur dont l’identité est usurpée : sélectionnez Déplacer le message vers les dossiers Courrier indésirable (Standard) des destinataires ou mettre le message en quarantaine <sup>\*</sup> (Strict).  
       - **Si le message est détecté comme** usurpant l’adresse : sélectionnez Déplacer le message vers les dossiers Courrier indésirable (Standard) des **destinataires** ou mettre le **message** en quarantaine (Strict).
     - **Conseils de & section sur les** indicateurs de sécurité : Configurez les paramètres suivants :
       - **Afficher l’emprunt d’conseil de sécurité** <sup>\*</sup> : Sélectionner (activer).
       - **Afficher l’emprunt d’conseil de sécurité** <sup>\*</sup> : Sélectionner (activer).
       - **Afficher les caractères inhabituels d’emprunt d’conseil de sécurité** <sup>\*</sup> : Sélectionner (activer).
       - **Afficher (?) pour les expéditeurs non authentifiés** pour l’usurpation d’adresse : Sélectionnez (activer).
       - **Afficher la balise « via »**: sélectionnez (activer) si ce paramètre est disponible.

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   <sup>\*</sup>Ce paramètre est disponible uniquement dans Defender pour les Office 365.

4. Cliquez **sur Enregistrer,** puis sur **Fermer**

Pour obtenir des instructions détaillées sur la configuration des stratégies anti-hameçonnage, voir [Configure anti-phishing policies in EOP](configure-anti-phishing-policies-eop.md) and [Configure anti-phishing policies in Microsoft Defender for Office 365](configure-atp-anti-phishing-policies.md).

## <a name="part-3---anti-spam-protection-in-eop"></a>Partie 3 : protection contre le courrier indésirable dans EOP

Pour plus d’informations sur les paramètres recommandés pour la détection du courrier indésirable, consultez la liste des paramètres de stratégie [anti-courrier indésirable EOP.](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

1. Ouvrez <https://security.microsoft.com/antispam> .

2. Dans la page **Stratégies anti-courrier** indésirable, sélectionnez la stratégie nommée Stratégie de courrier indésirable entrant **(par défaut)** dans la liste en cliquant sur le nom.

3. Dans le volant de détails de stratégie qui s’affiche, faites les étapes suivantes :
   - **Seuil de courrier électronique en & section Propriétés du** courrier indésirable : cliquez sur **Modifier le seuil de courrier indésirable et les propriétés.** Dans le **seuil de** courrier indésirable et  le flyout des propriétés qui s’affiche, définissez la valeur du seuil de courrier en bloc sur 5 (Strict) ou 6 (Standard). Lorsque vous avez terminé, cliquez sur **Enregistrer**.
   - **Section Expéditeurs et** domaines autorisés et bloqués : examinez ou modifiez vos expéditeurs et domaines autorisés.

4. Lorsque vous avez terminé, cliquez sur **Fermer**.

Pour obtenir des instructions détaillées sur la configuration des stratégies anti-courrier indésirable, voir [Configure anti-spam policies in EOP](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365"></a>Partie 4 : protection contre les URL et les fichiers malveillants (liens et pièces jointes sécurisées dans Defender pour Office 365)

La protection au moment du clic contre les URL et fichiers malveillants est disponible dans les abonnements qui incluent [Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Elle est définie par le biais de [stratégies de](safe-attachments.md) pièces jointes et de liens [sécurisés.](safe-links.md)

### <a name="safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Stratégies de pièces jointes sécurisées dans Microsoft Defender pour Office 365

Pour configurer les [pièces jointes sécurisées,](safe-attachments.md)créez au moins une stratégie de liens sécurisés.

1. In the [Security & Compliance Center,](https://protection.office.com)choose **Threat management** \> **Policy** \> **ATP Safe Attachments,** and then click **Create**.

2. Dans **l’Assistant Nouvelle stratégie de pièces jointes sécurisées** qui s’affiche, configurez les paramètres suivants :

   - Dans la **zone** Nom, `Block malware` tapez, puis cliquez sur **Suivant.**

   - Sur la **Paramètres** page, configurez les paramètres suivants :
     - In the **Safe attachments unknown malware response** section, choose **Block**.
     - Dans la section **Rediriger la** pièce jointe, sélectionnez l’option **Activer la redirection.** Spécifiez l’adresse de messagerie de l’administrateur ou de l’opérateur de sécurité de votre organisation, qui examinera les fichiers détectés.

     Cliquez sur **Suivant**.

3. Dans **la page** Appliqué à, cliquez sur Ajouter une **condition,** choisissez Appliqué si **:** Le domaine du destinataire est , cliquez sur **Ajouter,** sélectionnez votre ou vos domaines, cliquez sur **Ajouter,** cliquez sur **Terminé,** puis sur **Suivant**.

4. Examinez vos paramètres, puis cliquez sur **Terminer.**

### <a name="safe-links-policies-in-microsoft-defender-for-office-365"></a>Stratégies de liens sécurisés dans Microsoft Defender pour Office 365

Pour configurer des [liens sécurisés,](safe-links.md)examiner et modifier vos paramètres globaux pour les liens sécurisés et créer au moins une stratégie de liens sécurisés.

1. Dans le [Centre de sécurité & conformité,](https://protection.office.com)sélectionnez Stratégie de gestion des menaces - Liens  \>  \> sécurisés **ATP,** cliquez sur **Paramètres** globaux, puis configurez les paramètres suivants :

   - Vérifiez **l’utilisation des liens sécurisés dans : Office 365 applications** est désactivée : ![ Basculez sur ](../../media/scc-toggle-on.png) .
   - **Ne pas suivre le moment où les utilisateurs cliquent sur** Liens sécurisés : désactiver ce paramètre pour suivre les clics de l’utilisateur : ![ désactiver ](../../media/scc-toggle-off.png) .
   - **Ne laissez pas les utilisateurs cliquer sur les** liens sécurisés vers l’URL d’origine : vérifiez que ce paramètre est allumé : ![ Basculez sur ](../../media/scc-toggle-on.png) .

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

2. De retour sur la page principale des liens sécurisés, cliquez sur **Créer.**

3. Dans **l’Assistant Créer une stratégie de** liens sécurisés qui s’affiche, configurez les paramètres suivants :

   - Dans la **zone** Nom, tapez un nom, par `Safe Links` exemple, puis cliquez sur **Suivant**.

   - Sur la **Paramètres** page, configurez les paramètres suivants :
     - **Sélectionnez l’action pour les URL potentiellement malveillantes inconnues dans les messages**: **Choisir.**
     - **Sélectionnez l’action pour les URL inconnues** ou potentiellement malveillantes dans Microsoft Teams : **Choisir.**
     - **Appliquer des liens sûrs aux messages électroniques envoyés au sein de l’organisation**
     - **Attendre la fin de l’analyse de l’URL avant de remettre le message**
     - **Appliquer des liens sûrs aux messages électroniques envoyés au sein de l’organisation**
     - **Ne pas autoriser les utilisateurs à accéder à l’URL d’origine**

     Cliquez sur **Suivant**.

4. Dans **la page** Appliqué à, cliquez sur Ajouter une **condition,** choisissez Appliqué si **:** Le domaine du destinataire est , cliquez sur **Ajouter,** sélectionnez votre ou vos domaines, cliquez sur **Ajouter,** cliquez sur **Terminé,** puis sur **Suivant**.

5. Examinez vos paramètres, puis cliquez sur **Terminer.**

Pour plus d’informations, reportez-vous à [Configurer les stratégies de liens fiables](set-up-safe-links-policies.md).

## <a name="part-5---verify-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams-is-turned-on"></a>Partie 5 : vérifier les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams est allumée

Les charges de travail telles SharePoint, OneDrive et Teams sont conçues pour la collaboration. L’utilisation de Defender pour Office 365 permet de bloquer et de détecter les fichiers identifiés comme malveillants dans les sites d’équipe et les bibliothèques de documents. Vous pouvez en savoir plus sur le fonctionnement [ici.](mdo-for-spo-odb-and-teams.md)

> [!IMPORTANT]
> **Avant de commencer cette procédure, assurez-vous** que la journalisation d’audit est déjà Microsoft 365 environnement. Cette tâche est généralement effectuée par une personne dont le rôle Journaux d’audit est Exchange Online. Pour plus d’informations, voir Activer ou désactiver la [recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md)!

1. Dans le [Centre de sécurité & conformité,](https://protection.office.com)sélectionnez Stratégie de gestion des menaces pièces  \>  \> **jointes sécurisées ATP,** puis cliquez sur **Paramètres globaux.**

2. Vérifiez que le bouton bascule Activer Defender pour Office 365 pour **SharePoint, OneDrive** et Microsoft Teams est à droite : Activer, puis cliquez sur ![ ](../../media/scc-toggle-on.png) Enregistrer. 

3. Examinez (et, le cas échéant, modifiez) les stratégies de pièces [jointes sécurisées et](set-up-safe-attachments-policies.md) les stratégies [de liens sécurisés de votre organisation.](set-up-safe-links-policies.md)

4. (Recommandé) En tant qu’administrateur général ou administrateur SharePoint Online, exécutez la cmdlet **[Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant)** avec le paramètre _DisallowInfectedFileDownload_ définie sur `$true` .

   - `$true` bloque toutes les actions (à l’exception de Supprimer) pour les fichiers détectés. Les utilisateurs ne peuvent pas ouvrir, déplacer, copier ou partager les fichiers détectés.
   - `$false` bloque toutes les actions à l’exception de Supprimer et télécharger. Les personnes peuvent choisir d’accepter le risque et de télécharger un fichier détecté.

   > [!TIP]
   > Pour en savoir plus sur l’utilisation de PowerShell Microsoft 365, voir [Gérer Microsoft 365 avec PowerShell.](../../enterprise/manage-microsoft-365-with-microsoft-365-powershell.md)

5. Autorisez jusqu’à 30 minutes pour que vos modifications se propagent à tous Microsoft 365 centres de données.

### <a name="now-set-up-alerts-for-detected-files"></a>À présent, configurer des alertes pour les fichiers détectés

Pour recevoir une notification lorsqu’un fichier dans SharePoint Online, OneDrive Entreprise ou Microsoft Teams a été identifié comme malveillant, vous pouvez configurer une alerte.

1. Dans le [Centre de sécurité & conformité,](https://protection.office.com)choisissez **Alertes Gérer** les \> **alertes.**

2. Choisissez **Nouvelle stratégie d’alerte.**

3. Spécifiez un nom pour l’alerte. Par exemple, vous pouvez taper Des fichiers malveillants dans des bibliothèques.

4. Tapez une description pour l’alerte. Par exemple, vous pouvez taper Notifie les administrateurs lorsque des fichiers malveillants sont détectés dans SharePoint Online, OneDrive ou Microsoft Teams.

5. Dans la section **Envoyer cette alerte quand...** , définissez :

   a. Dans la **liste Activités,** sélectionnez **Programmes malveillants détectés dans le fichier.**

   b. Laissez le **champ Utilisateurs** vide.

6. Dans la section Envoyer cette alerte **à...** sélectionnez un ou plusieurs administrateurs globaux, administrateurs de sécurité ou lecteurs de sécurité qui doivent recevoir une notification lorsqu’un fichier malveillant est détecté.

7. **Enregistrer**.

Pour en savoir plus sur les alertes, voir Créer des alertes d’activité dans le Centre de [sécurité & conformité.](../../compliance/create-activity-alerts.md)

> [!NOTE]
> Lorsque vous avez terminé la configuration, utilisez ces liens pour lancer des enquêtes sur la charge de travail :
>
>- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
>- [Utilisez le portail Microsoft 365 Defender pour gérer les fichiers mis en quarantaine dans Defender Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365)
>- [Que faire lorsqu’un fichier malveillant est trouvé dans SharePoint Online, OneDrive ou Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
>- [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)

## <a name="part-6---additional-settings-to-configure"></a>Partie 6 : paramètres supplémentaires à configurer

Outre la configuration de la protection contre les programmes malveillants, les URL et les fichiers malveillants, le hameçonnage et le courrier indésirable, nous vous recommandons de configurer la purge automatique d’heure zéro.

### <a name="zero-hour-auto-purge-for-email-in-eop"></a>Purge automatique zéro heure pour le courrier électronique dans EOP

[La purge automatique d’heure](zero-hour-auto-purge.md) zéro (ZAP) est disponible dans les abonnements qui incluent [EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). Cette protection est désactivée par défaut . Toutefois, les conditions suivantes doivent être remplies pour que la protection soit en vigueur :

- Les actions de courrier indésirable sont définies sur **Déplacer le message vers** le dossier Courrier indésirable dans les [stratégies anti-courrier indésirable.](anti-spam-protection.md)

- Les utilisateurs ont conservé leurs [paramètres de courrier](configure-junk-email-settings-on-exo-mailboxes.md)indésirable par défaut et n’ont pas désactivé la protection contre le courrier indésirable.

Pour en savoir plus, [consultez Purge automatique heure zéro - Protection contre le courrier indésirable et les programmes malveillants.](zero-hour-auto-purge.md)

## <a name="post-setup-tasks-and-next-steps"></a>Tâches post-installation et étapes suivantes

Après avoir configuré les fonctionnalités de protection contre les menaces, veillez à surveiller leur fonctionnement ! Examinez et révisez vos stratégies afin qu’elles s’en sortent comme vous le souhaitez. Observez également les nouvelles fonctionnalités et mises à jour de service qui peuvent ajouter de la valeur.

****

|Procédure|Ressources pour en savoir plus|
|---|---|
|Découvrez comment fonctionnent les fonctionnalités de protection contre les menaces pour votre organisation en visualxant des rapports|[Tableau de bord de sécurité](security-dashboard.md) <p> [Rapports de sécurité de messagerie](view-email-security-reports.md) <p> [Rapports pour Microsoft Defender pour Office 365](view-reports-for-mdo.md) <p> [Threat Explorer](threat-explorer.md)|
|Examiner et réviser régulièrement vos stratégies de protection contre les menaces selon vos besoins|[Degré de sécurisation](../defender/microsoft-secure-score.md) <p> [Rapports intelligents et informations](reports-and-insights-in-security-and-compliance.md) <p> [Microsoft 365 d’investigation et de réponse aux menaces](./office-365-ti.md)|
|Surveiller les nouvelles fonctionnalités et les mises à jour de service|[Options de publication standard et ciblée](../../admin/manage/release-options-in-office-365.md) <p> [Centre de messages](../../admin/manage/message-center.md) <p> [Feuille de route de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) <p> [Service Descriptions](/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
|Découvrez les détails des configurations de sécurité standard et stricte recommandées pour EOP et Defender pour Office 365|[Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](recommended-settings-for-eop-and-office365.md)|
