---
title: Protéger contre les menaces
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.date: 09/08/2020
search.appverid:
- MOE150
- MET150
ms.assetid: b10023f6-f30f-45d3-b3ad-b71aa4aa0d58
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur la protection contre les menaces dans Microsoft 365 et configurer la façon de l’utiliser pour votre organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8b96ba1735f94e80450fa4f604fc45dc60b80d12
ms.sourcegitcommit: 74ef7179887eedc696c975a82c865b2d4b3808fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "47417121"
---
# <a name="protect-against-threats"></a>Protéger contre les menaces

Voici un guide de démarrage rapide qui divise la configuration de la protection avancée contre les menaces en segments. Si vous ne connaissez pas les fonctionnalités de protection contre les menaces dans Office 365, si vous ne savez pas où commencer ou si vous êtes le plus *approprié, utilisez ces instructions en tant*que liste de vérification et point de départ.

> [!IMPORTANT]
> Les **paramètres recommandés initiaux sont inclus pour chaque type de stratégie ; Toutefois, de nombreuses options sont disponibles et vous pouvez ajuster vos paramètres afin de répondre aux besoins spécifiques de votre organisation**. Accordez environ 30 minutes à vos stratégies ou modifications pour qu’elles fonctionnent dans votre centre de centres de travail.

## <a name="requirements"></a>Configuration requise

### <a name="subscriptions"></a>Abonnements

Les fonctionnalités de protection contre les menaces sont incluses dans *tous les* abonnements Microsoft ou Office 365 ; Toutefois, certains abonnements ont des fonctionnalités avancées. Le tableau ci-dessous répertorie les fonctionnalités de protection incluses dans cet article, ainsi que les conditions minimales requises en matière d’abonnement.

> [!TIP]
> Notez que, au-delà des instructions d’activation de l’audit, effectuez les *procédures suivantes* : anti-malware, anti-hameçonnage et anti-spam, qui sont marqués dans le cadre d’Office 365 Exchange Online Protection (**EOP**). Cela peut paraître étrange dans un article de protection avancée contre les menaces, jusqu’à ce que vous ayez oublié la protection avancée contre les menaces (**ATP**) contient et repose sur EOP.

****

|Type de protection|Configuration requise pour l’abonnement|
|---|---|
|Journalisation d’audit (à des fins de création de rapports)|[Exchange Online](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Protection anti-programme malveillant|[Exchange Online Protection](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Protection anti-hameçonnage|[Exchange Online Protection](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Protection anti-courrier indésirable|[Exchange Online Protection](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Purge automatique avec zéro heure (pour la messagerie électronique)|[Exchange Online Protection](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Protection contre les URL et les fichiers malveillants dans les e-mails et les documents Office (liens fiables et pièces jointes fiables)|[Office 365 Advanced Threat Protection](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) (**ATP**)|
|Activer la protection avancée contre les menaces pour les charges de travail SharePoint, OneDrive et Microsoft teams| [ATP](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?view=o365-worldwide)|
|Protection avancée contre le hameçonnage|[ATP](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Rôles et autorisations

Pour configurer des stratégies ATP, vous devez disposer d’un rôle approprié dans le [Centre de sécurité & conformité](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center). Consultez le tableau ci-dessous pour les rôles qui peuvent effectuer ces actions.

****

|Rôle ou groupe de rôles|Où en savoir plus|
|---|---|
|administrateur général|[À propos des rôles d’administrateur Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)|
|Administrateur de sécurité|[Autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Gestion d’Organisation Exchange Online|[Autorisations dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo) <br>et<br> [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell)|
|

Pour en savoir plus, consultez [la rubrique autorisations dans le centre de sécurité &amp; conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="before-you-begin-turn-on-audit-logging-for-reporting-and-investigation"></a>Avant de commencer, activez la journalisation d’audit pour la création de rapports et l’enquête.

Commencez la journalisation d’audit au plus tôt. L’audit doit être **activé** pour certaines étapes qui suivent. La journalisation d’audit est disponible dans les abonnements qui incluent [Exchange Online](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Pour afficher les données des rapports de protection contre les menaces, tels que le [tableau de bord de sécurité](security-dashboard.md), les rapports de sécurité de [messagerie](view-email-security-reports.md)et l' [Explorateur](threat-explorer.md), la journalisation d’audit doit être *activée*. Pour en savoir plus, consultez la rubrique [activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="part-1---anti-malware-protection"></a>Partie 1 : protection anti-programme malveillant

La [protection contre les programmes malveillants](anti-malware-protection.md) est disponible dans les abonnements incluant [EOP](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

1. Dans le [Centre de sécurité & conformité](https://protection.office.com), **Threat management**choisissez  >  **Policy**  >  **protection contre les programmes malveillants**pour la stratégie de gestion des menaces.

2. Double-cliquez sur la stratégie **par défaut** , puis sélectionnez **paramètres**.

3. Spécifiez les paramètres suivants :

    - Dans la section réponse à la **détection de programmes malveillants** , conservez le paramètre par défaut **non**.

    - Dans la section **filtre de types de pièces jointes courantes** , choisissez **activé**.

4. Cliquez sur **Enregistrer**.

Pour en savoir plus sur les options de stratégie anti-programme malveillant, consultez la rubrique [configure anti-malware Policies](configure-anti-malware-policies.md).

## <a name="part-2---anti-phishing-protection"></a>Partie 2 : protection anti-hameçonnage

[Anti-hameçonnage]

La [protection anti-hameçonnage](anti-phishing-protection.md) est disponible dans les abonnements incluant [EOP](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). La protection avancée contre le hameçonnage est [disponible dans la](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)protection avancée contre les menaces.

La procédure suivante décrit comment configurer une stratégie anti-hameçonnage ATP. Les étapes sont similaires pour la configuration d’une stratégie anti-hameçonnage (sans ATP).

1. Dans le [Centre de sécurité & conformité](https://protection.office.com), **Threat management**sélectionnez  >  **Policy**  >  **protection contre les**menaces pour le hameçonnage.

2. Cliquez sur **stratégie par défaut**.

3. Dans la section **emprunt d’identité** , cliquez sur **modifier**, puis spécifiez les paramètres suivants :

   - Sous l’onglet **Ajouter des utilisateurs à protéger** , *activez la* protection. Ajoutez ensuite des utilisateurs, tels que les membres du tableau de bord de votre organisation, votre directeur général, votre directeur financier et d’autres dirigeants. (Vous pouvez taper une adresse de messagerie individuelle ou cliquer pour afficher une liste.)

   - Dans l’onglet **Ajouter des domaines à protéger** , activez **la fonction inclure automatiquement les domaines dont je suis propriétaire**. Si vous avez des domaines personnalisés, ajoutez-les maintenant.

   - Sous l’onglet **actions** , sélectionnez **mettre en quarantaine le message** pour les options **utilisateur emprunté** et **domaine emprunté** . En outre, activez les conseils de sécurité pour l’emprunt d’identité.

   - Sous l’onglet **intelligence des boîtes aux lettres** , assurez-vous que l’intelligence des boîtes aux lettres est activée et activez la protection contre l’emprunt d’identité basée sur les boîtes aux lettres. Dans la liste **si un message électronique est envoyé par un utilisateur emprunté** , choisissez **mettre en quarantaine le message**.

   - Dans l’onglet **Ajouter des expéditeurs et des domaines approuvés** , spécifiez tous les expéditeurs ou domaines approuvés que vous souhaitez ajouter.

   - **Enregistrer** sous l’onglet **vérifier vos paramètres** une fois que vous avez vérifié vos paramètres.

4. Dans la section **usurpation** , cliquez sur **modifier**, puis spécifiez les paramètres suivants :

   - Dans l’onglet **paramètres du filtre d’usurpation d’identité** , assurez-vous que la protection contre l’usurpation d’identité est activée.

   - Sous l’onglet **actions** , choisissez **mettre en quarantaine le message**.

   - **Enregistrer** sous l’onglet **vérifier vos paramètres** une fois que vous avez vérifié vos modifications. (Si vous n’avez apporté aucune modification, **annulez**.)

5. Fermez la page Paramètres de stratégie par défaut.

Pour en savoir plus sur les options de stratégie anti-hameçonnage, consultez la rubrique [configure ATP anti-phishing Policies](configure-atp-anti-phishing-policies.md).

## <a name="part-3---anti-spam-protection"></a>Partie 3-protection contre le courrier indésirable

La [protection contre le courrier indésirable](anti-spam-protection.md) est disponible dans les abonnements incluant [EOP](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

1. Dans le [Centre de sécurité & conformité](https://protection.office.com), **Threat management**choisissez  >  **Policy**  >  **protection contre le courrier indésirable**pour la stratégie de gestion des menaces.

2. Sous l’onglet **personnalisé** , activez les paramètres personnalisés.

3. Développez **stratégie de filtrage du courrier indésirable par défaut**, cliquez sur **modifier la stratégie**, puis spécifiez les paramètres suivants :

   - Dans la section **actions de courrier indésirable et en bloc** , définissez le seuil sur une valeur de 5 ou 6.

   - Dans la section **autoriser les listes** , vérifiez (et/ou modifiez) vos expéditeurs et domaines autorisés.

4. Cliquez sur **Enregistrer**.

Pour en savoir plus sur les options de votre stratégie de blocage du courrier indésirable, consultez la rubrique [configure anti-spam Policies in EOP](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments"></a>Partie 4-protection contre les URL et les fichiers malveillants (liens fiables et pièces jointes fiables)

La protection du temps de clic à partir d’URL et de fichiers malveillants est disponible dans les abonnements incluant [Office 365 ATP](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) (ATP). Elle est configurée par le biais de [pièces jointes approuvées ATP](atp-safe-attachments.md) et des stratégies de [liens fiables ATP](atp-safe-links.md) .

### <a name="atp-safe-attachments-policies"></a>Stratégies de pièces jointes approuvées ATP

Pour configurer des [pièces jointes sûres ATP](atp-safe-attachments.md), vous devez définir au moins une stratégie de pièces jointes approuvées ATP.

1. Dans le [Centre de sécurité & conformité](https://protection.office.com), sélectionnez **gestion des menaces**-  >  **Policy**  >  **pièces jointes ATP**.

2. Sélectionnez l’option Activer la protection avancée contre **les menaces pour SharePoint, OneDrive et Microsoft teams**.

3. Dans la section **protéger les pièces jointes** , cliquez sur le signe plus ( **+** ).

4. Spécifiez les paramètres suivants :

   - Dans la zone **nom** , tapez `Block malware` .

   - Dans la section réponse, sélectionnez **bloquer**.

   - Dans la section **pièce jointe de redirection** , sélectionnez l’option **activer la redirection**. Spécifiez l’adresse de messagerie de l’administrateur ou de l’opérateur de sécurité de votre organisation, qui examinera les fichiers détectés.

   - Dans la section **appliqué à** , choisissez **le domaine du destinataire**. Ensuite, sélectionnez votre domaine, cliquez sur **Ajouter**, puis sur **OK**.

5. **Enregistrer**.

6. (**Étape supplémentaire recommandée**) En tant qu’administrateur général ou administrateur SharePoint Online, exécutez la cmdlet **[Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant)** avec le paramètre **DisallowInfectedFileDownload** défini sur  *true* pour votre environnement Microsoft 365. (Cela empêche les personnes d’ouvrir, de transférer, de copier ou de partager des fichiers détectés comme malveillants.)

Pour en savoir plus, consultez la rubrique [configurer des stratégies de pièces jointes approuvées ATP office 365](set-up-atp-safe-attachments-policies.md) et [activer Office 365 ATP pour SharePoint, OneDrive et Microsoft teams](turn-on-atp-for-spo-odb-and-teams.md).

### <a name="atp-safe-links-policies"></a>Stratégies de liens fiables ATP

Pour configurer [des liens approuvés ATP](atp-safe-links.md), vérifiez et modifiez votre stratégie par défaut, puis ajoutez une stratégie pour des utilisateurs spécifiques.

1. Dans le [Centre de sécurité & conformité](https://protection.office.com), sélectionnez **gestion des menaces**-  >  **Policy**  >  **liens fiables ATP**.

2. Double-cliquez sur la stratégie **par défaut** .

3. Dans la section **utiliser les liens approuvés dans** , sélectionnez l’option **applications Microsoft 365 pour les entreprises, Office pour iOS et Android**, puis cliquez sur **Enregistrer**.

4. Dans la section **stratégies qui s’appliquent à des destinataires spécifiques** , cliquez sur le signe plus ( **+** ).

5. Spécifiez les paramètres suivants :

   - Dans la zone **nom** , tapez un nom, tel que `Safe Links` .

   - Dans la section **Sélectionnez l’action** , choisissez **activé**.

   - Sélectionnez les options suivantes :

     - **Utiliser les pièces jointes fiables pour analyser le contenu téléchargeable**

     - **Appliquer des liens fiables aux messages électroniques envoyés au sein de l’Organisation**

     - **Ne pas autoriser les utilisateurs à cliquer sur les liens fiables vers l’URL d’origine**

   - Dans la section **appliqué à** , choisissez **le domaine du destinataire**. Ensuite, sélectionnez votre domaine, cliquez sur **Ajouter**, puis sur **OK**.

6. **Enregistrer**.

Pour plus d’informations, reportez-vous à [Configurer les stratégies de liens fiables Office 365 – Protection avancée contre les menaces](set-up-atp-safe-links-policies.md).

## <a name="part-5---turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams-workloads"></a>Partie 5 : activation de la protection avancée contre les menaces pour les charges de travail SharePoint, OneDrive et Microsoft teams

Les charges de travail telles que SharePoint, OneDrive et teams sont conçues pour la collaboration. L’utilisation de la protection avancée contre les menaces permet de bloquer et de détecter les fichiers identifiés comme étant malveillants dans les sites d’équipe et les bibliothèques de documents. Vous pouvez en savoir plus sur la façon dont [cela fonctionne.](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-for-spo-odb-and-teams?view=o365-worldwide)

> [!IMPORTANT]
> **Avant de commencer cette procédure, assurez-vous que la journalisation d’audit est déjà activée pour votre environnement Microsoft 365**. Cette opération est généralement réalisée par une personne disposant du rôle journaux d’audit dans Exchange Online. Pour plus d’informations, consultez la rubrique [activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md)!

1. Accédez à <https://protection.office.com> , puis connectez-vous à l’aide de votre compte professionnel ou scolaire.

2. Dans le centre de sécurité & Security Center, dans le volet de navigation de gauche, sous **gestion des menaces**, sélectionnez **stratégie** de \> **pièces jointes approuvées**par la stratégie.

   ![Dans le centre de sécurité & conformité, sélectionnez stratégie de gestion des menaces. \>](../../media/08849c91-f043-4cd1-a55e-d440c86442f2.png)

3. Sélectionnez Activer la protection avancée contre **les menaces pour SharePoint, OneDrive et Microsoft teams**.

   ![Activer la protection avancée contre les menaces pour SharePoint Online, OneDrive entreprise et Microsoft teams](../../media/48cfaace-59cc-4e60-bf86-05ff6b99bdbf.png)

4. **Enregistrer**.

5. Vérifiez (et, le cas échéant, modifiez) les stratégies de [pièces jointes](set-up-atp-safe-attachments-policies.md) approuvées et les [stratégies de liens fiables](set-up-atp-safe-links-policies.md)de votre organisation.

6. Recommandation En tant qu’administrateur général ou administrateur SharePoint Online, exécutez la cmdlet **[Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant)** avec le paramètre _DisallowInfectedFileDownload_ défini sur *true*.

   - La définition du paramètre sur *true* bloque toutes les actions (à l’exception de la suppression) des fichiers détectés. Les utilisateurs ne peuvent pas ouvrir, déplacer, copier ou partager des fichiers détectés.

   - La définition du paramètre sur *false* bloque toutes les actions à l’exception de Delete et download. Les utilisateurs peuvent choisir d’accepter le risque et de télécharger un fichier détecté.
   > [!TIP] Pour en savoir plus sur l’utilisation de PowerShell avec Microsoft 365, consultez la rubrique [Manage Microsoft 365 with PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/manage-microsoft-365-with-microsoft-365-powershell).

7. Autorisez jusqu’à 30 minutes pour que vos modifications soient diffusées sur tous les centres de calcul Microsoft 365.


#### <a name="now-set-up-alerts-for-detected-files"></a>À présent, configurez les alertes pour les fichiers détectés.

Pour recevoir une notification lorsqu’un fichier dans SharePoint Online, OneDrive entreprise ou Microsoft teams a été identifié comme malveillant, vous pouvez configurer une alerte.

1. Dans le [Centre de sécurité & conformité](https://protection.office.com), sélectionnez **alertes** \> **gérer les alertes**.

2. Choisissez **nouvelle stratégie d’alerte**.

3. Spécifiez un nom pour l’alerte. Par exemple, vous pouvez taper des fichiers malveillants dans les bibliothèques.

4. Tapez une description pour l’alerte. Par exemple, vous pouvez taper avertir les administrateurs lorsque des fichiers malveillants sont détectés dans SharePoint Online, OneDrive ou Microsoft Teams.

5. Dans la section **Envoyer cette alerte quand...** , définissez :

   a. Dans la liste **activités** , sélectionnez **programmes malveillants détectés dans le fichier**.

   b. Laissez le champ **utilisateurs** vide.

6. Dans la section **Envoyer cette alerte à...** , sélectionnez un ou plusieurs administrateurs globaux, administrateurs de sécurité ou lecteurs de sécurité qui doivent recevoir une notification lorsqu’un fichier malveillant est détecté.

7. **Enregistrer**.

Pour en savoir plus sur les alertes, voir [créer des alertes d’activité dans le centre de sécurité & conformité](../../compliance/create-activity-alerts.md).

> [!NOTE]
> Lorsque vous avez terminé la configuration, utilisez ces liens pour lancer des enquêtes de charge de travail :
>- [Afficher des informations sur les fichiers malveillants détectés dans SharePoint, OneDrive ou Microsoft teams](malicious-files-detected-in-spo-odb-or-teams.md)
>- [Procédure à suivre lorsqu’un fichier malveillant est trouvé dans SharePoint Online, OneDrive ou Microsoft teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
>- [Gérer les messages et les fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md) 

## <a name="part-6---additional-settings-to-configure"></a>Partie 6-paramètres supplémentaires à configurer

En plus de la configuration de la protection contre les programmes malveillants, les URL et les fichiers malveillants, le hameçonnage et le courrier indésirable, nous vous recommandons de configurer la purge automatique des heures zéro.

### <a name="zero-hour-auto-purge-for-email-in-eop"></a>Purge automatique avec zéro heure pour le courrier électronique dans EOP

La purge automatique (ZAP) [zéro heure](zero-hour-auto-purge.md) est disponible dans les abonnements incluant [EOP](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). Cette protection est activée par défaut ; Toutefois, les conditions suivantes doivent être remplies pour que la protection soit appliquée :

- Les actions de courrier indésirable sont définies pour **déplacer le message vers le dossier courrier indésirable** des [stratégies de blocage du courrier](anti-spam-protection.md)indésirable.

- Les utilisateurs ont conservé leurs [paramètres de courrier indésirable](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md)par défaut et n’ont pas désactivé la protection contre le courrier indésirable.

Pour en savoir plus, consultez la rubrique [Zero-Hour auto-protection-protection contre le courrier indésirable et les programmes malveillants](zero-hour-auto-purge.md).

## <a name="post-setup-tasks-and-next-steps"></a>Tâches consécutives à l’installation et étapes suivantes

Après avoir configuré les fonctionnalités de protection contre les menaces, veillez à surveiller le fonctionnement de ces fonctionnalités. Examinez et révisez vos stratégies pour qu’elles fassent ce dont elles ont besoin. De plus, surveillez les nouvelles fonctionnalités et les mises à jour de service pouvant ajouter de la valeur.

****

|Procédure|Ressources pour en savoir plus|
|---|---|
|Découvrez comment les fonctionnalités de protection contre les menaces fonctionnent pour votre organisation en affichant des rapports|[Tableau de bord de sécurité](security-dashboard.md)<br/>[Rapports de sécurité de messagerie](view-email-security-reports.md)<br/>[Rapports pour la protection avancée contre les menaces Office 365](view-reports-for-atp.md)<br/>[Threat Explorer](threat-explorer.md)|
|Vérifier et réviser régulièrement vos stratégies de protection contre les menaces selon vos besoins|[Degré de sécurisation](../mtp/microsoft-secure-score.md)<br/>[Rapports intelligents et Insights](reports-and-insights-in-security-and-compliance.md)<br/>[Fonctionnalités d’enquête et de réponse aux menaces Microsoft 365](keep-users-safe-with-office-365-ti.md)|
|Surveillez les nouvelles fonctionnalités et les mises à jour de service|[Options de publication standard et ciblées](https://docs.microsoft.com/microsoft-365/admin/manage/release-options-in-office-365)<br/>[Centre de messages](https://docs.microsoft.com/microsoft-365/admin/manage/message-center)<br/>[Feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection)<br/>[Descriptions des services](https://docs.microsoft.com/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
|Découvrez les détails des configurations de sécurité standard et rigoureuses recommandées pour EOP et la protection avancée contre les menaces | [Paramètres recommandés pour la sécurité ATP d’Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp?view=o365-worldwide) |
