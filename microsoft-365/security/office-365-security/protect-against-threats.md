---
title: Protection contre les menaces dans Microsoft Defender pour Office 365, anti-programmes malveillants, anti-hameçonnage, anti-courrier indésirable, liens sécurisés, pièces jointes sécurisées, vidage automatique de zéro heure (ZAP), configuration de la sécurité MDO
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
ms.date: 06/22/2021
search.appverid:
- MOE150
- MET150
ms.assetid: b10023f6-f30f-45d3-b3ad-b71aa4aa0d58
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent en savoir plus sur la protection contre les menaces dans Microsoft 365 et configurer leur utilisation pour votre organisation.
ms.custom: seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 747fe0563222b34b5ff63673a6bc350db9207b83
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67598712"
---
# <a name="protect-against-threats"></a>Protéger contre les menaces

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Voici un guide de démarrage rapide qui décompose la configuration de Defender pour Office 365 en blocs. Si vous débutez avec les fonctionnalités de protection contre les menaces dans Office 365, ne savez pas par où commencer, ou si vous apprenez le *mieux, utilisez* ces conseils comme liste de vérification et comme point de départ.

> [!IMPORTANT]
> **Les paramètres recommandés initiaux sont inclus pour chaque type de stratégie. Toutefois, de nombreuses options sont disponibles et vous pouvez ajuster vos paramètres pour répondre aux besoins de votre organisation spécifique**. Prévoyez environ 30 minutes pour que vos stratégies ou modifications fonctionnent dans votre centre de données.
>
> Pour ignorer la configuration manuelle de la plupart des stratégies dans Defender pour Office 365, vous pouvez utiliser des stratégies de sécurité prédéfinies au niveau Standard ou Strict. Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

## <a name="requirements"></a>Conditions requises

### <a name="subscriptions"></a>Abonnements

Les fonctionnalités de protection contre les menaces sont incluses dans *tous les* abonnements Microsoft ou Office 365 ; toutefois, certains abonnements ont des fonctionnalités avancées. Le tableau ci-dessous répertorie les fonctionnalités de protection incluses dans cet article, ainsi que les exigences minimales en matière d’abonnement.

> [!TIP]
> Notez qu’au-delà des instructions permettant d’activer l’audit, *les étapes* commencent par la lutte contre les programmes malveillants, l’anti-hameçonnage et la lutte contre le courrier indésirable, qui sont marqués dans le cadre de Office 365 Exchange Online Protection (**EOP**). Cela peut sembler étrange dans un article Defender pour Office 365, jusqu’à ce que vous vous souvenez (**Defender pour Office 365**) contient et s’appuie sur EOP.

|Type de protection|Configuration requise pour l’abonnement|
|---|---|
|Journalisation d’audit (à des fins de création de rapports)|[Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Protection anti-programme malveillant|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Protection anti-hameçonnage|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Protection anti-courrier indésirable|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Protection contre les URL et fichiers malveillants dans les e-mails et les documents Office (liens sécurisés et pièces jointes sécurisées)|[Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Rôles et autorisations

Pour configurer Defender pour Office 365 stratégies, vous devez disposer d’un rôle approprié. Examinez le tableau ci-dessous pour les rôles qui peuvent effectuer ces actions.

|Rôle ou groupe de rôles|Où en savoir plus|
|---|---|
|administrateur général|[À propos des rôles d’administrateur Microsoft 365](../../admin/add-users/about-admin-roles.md)|
|Administrateur de sécurité|[Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference#security-administrator)
|Gestion d’Organisation Exchange Online|[Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo)|

Pour en savoir plus, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

### <a name="turn-on-audit-logging-for-reporting-and-investigation"></a>Activer la journalisation d’audit pour la création de rapports et l’investigation

- Démarrez votre journalisation d’audit tôt. L’audit doit être **activé** pour certaines des étapes suivantes. La journalisation d’audit est disponible dans les abonnements qui incluent [Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Pour afficher les données dans les rapports de protection contre les menaces, [les rapports de sécurité par e-mail](view-email-security-reports.md) et [l’Explorateur](threat-explorer.md), la journalisation d’audit doit être *activée*. Pour en savoir plus, voir [Activer ou désactiver la recherche dans le journal d'audit](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="part-1---anti-malware-protection-in-eop"></a>Partie 1 - Protection contre les programmes malveillants dans EOP

Pour plus d’informations sur les paramètres recommandés pour les logiciels anti-programme malveillant, consultez [les paramètres de stratégie anti-programme malveillant EOP](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings).

1. Ouvrez la page **Anti-programme malveillant** dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com/antimalwarev2>.

2. Dans la page **Anti-programme malveillant** , sélectionnez la stratégie nommée **Par défaut (par défaut)** en cliquant sur le nom.

3. Dans le menu volant des détails de stratégie qui s’ouvre, cliquez sur **Modifier les paramètres de protection**, puis configurez les paramètres suivants :
   - **Section Paramètres de protection** :
     - **Activez le filtre de pièces jointes courant** : Sélectionner (activer). Cliquez sur **Personnaliser les types de fichiers** pour ajouter d’autres types de fichiers.
     - **Activez le vidage automatique de zéro heure pour les programmes malveillants** : vérifiez que ce paramètre est sélectionné. Pour plus d’informations sur ZAP pour les programmes malveillants, consultez [vidage automatique de zéro heure (ZAP) pour les programmes malveillants](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-malware).
   - **Stratégie de quarantaine** : laissez la valeur par défaut AdminOnlyAccessPolicy sélectionnée. Les stratégies de quarantaine définissent ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine et si les utilisateurs reçoivent des notifications de quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).
   - **Section Notification** : Vérifiez qu’aucun des paramètres de notification n’est sélectionné.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. Dans le menu volant des détails de la stratégie, cliquez sur **Fermer**.

Pour obtenir des instructions détaillées sur la configuration des stratégies anti-programme malveillant, consultez Configurer des stratégies [anti-programme malveillant dans EOP](configure-anti-malware-policies.md).

## <a name="part-2---anti-phishing-protection-in-eop-and-defender-for-office-365"></a>Partie 2 : Protection anti-hameçonnage dans EOP et Defender pour Office 365

[La protection anti-hameçonnage](anti-phishing-protection.md) est disponible dans les abonnements qui incluent [EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). Une protection anti-hameçonnage avancée est disponible dans [Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

Pour plus d’informations sur les paramètres recommandés pour les stratégies anti-hameçonnage, consultez [les paramètres de stratégie anti-hameçonnage EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) et [les paramètres de stratégie anti-hameçonnage dans Microsoft Defender pour Office 365](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

La procédure suivante décrit comment configurer la stratégie anti-hameçonnage par défaut. Les paramètres disponibles uniquement dans Defender pour Office 365 sont clairement marqués.

1. Ouvrez la page **Anti-hameçonnage** dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , sélectionnez la stratégie nommée **Office365 AntiPhish Default (Par défaut)** en cliquant sur le nom.

3. Dans le menu volant des détails de stratégie qui s’affiche, configurez les paramètres suivants :
   - **Seuil d’hameçonnage & section protection** : cliquez sur **Modifier les paramètres de protection** et configurez les paramètres suivants dans le menu volant qui s’ouvre :
     - Seuil <sup>\*</sup>**d’e-mail d’hameçonnage** : Sélectionnez **2 - Agressif** (Standard) ou **3 - Plus agressif** (strict).
     - Section <sup>\*</sup> **Emprunt d’identité** : Configurez les valeurs suivantes :
       - Sélectionnez **Activer la protection des utilisateurs**, cliquez sur le lien **Gérer (nn) expéditeurs** qui s’affiche, puis ajoutez des expéditeurs internes et externes pour vous protéger contre l’emprunt d’identité, tels que les membres du conseil d’administration de votre organisation, votre PDG, le directeur financier et d’autres hauts dirigeants.
       - Sélectionnez **Activer les domaines à protéger**, puis configurez les paramètres suivants qui s’affichent :
         - Sélectionnez **Inclure les domaines dont je suis propriétaire** pour protéger les expéditeurs internes dans vos domaines acceptés (visibles en cliquant sur **Afficher mes domaines**) contre l’emprunt d’identité.
         - Pour protéger les expéditeurs dans d’autres domaines, **sélectionnez Inclure des domaines personnalisés**, cliquez sur le lien **Gérer (nn) domaines personnalisés** qui s’affiche, puis ajoutez d’autres domaines pour protéger contre l’emprunt d’identité.
     - **Section Ajouter des expéditeurs approuvés et des**<sup>\*</sup> domaines : Cliquez sur **Gérer (nn) les expéditeurs approuvés et les domaines** pour configurer les exceptions de domaine de l’expéditeur et de l’expéditeur afin de protéger l’emprunt d’identité si nécessaire.
     - Paramètres d’intelligence de boîte aux lettres <sup>\*</sup> : vérifiez que **l’option Activer l’intelligence de boîte aux lettres** et **Activer l’intelligence pour la protection de l’emprunt d’identité** sont sélectionnées.
     - **Section Usurpation d’identité** : Vérifiez que **l’option Activer l’intelligence de l’usurpation d’identité** est sélectionnée.

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Section Actions** : Cliquez sur **Modifier les actions** et configurez les paramètres suivants dans le menu volant qui s’ouvre :
     - **Section Actions** de message : Configurez les paramètres suivants :
       - **Si le message est détecté comme un utilisateur emprunt d’identité**<sup>\*</sup> : sélectionnez **Mettre en quarantaine le message**. Une zone **Appliquer la stratégie de quarantaine** s’affiche où vous sélectionnez la stratégie de [quarantaine](quarantine-policies.md) qui s’applique aux messages mis en quarantaine par la protection d’emprunt d’identité de l’utilisateur.
       - **Si le message est détecté comme un domaine**<sup>\*</sup> emprunté : sélectionnez **Mettre en quarantaine le message**. Une zone **Appliquer la stratégie de quarantaine** s’affiche où vous sélectionnez la stratégie de [quarantaine](quarantine-policies.md) qui s’applique aux messages mis en quarantaine par la protection d’emprunt d’identité de domaine.
       - **Si l’intelligence de boîte aux lettres détecte un utilisateur emprunt d’identité**<sup>\*</sup> : sélectionnez **Déplacer le message vers les dossiers Courrier indésirable Email des destinataires (** Standard) ou **Mettez le message en quarantaine** (Strict). Si vous sélectionnez **Mettre en quarantaine le message**, une zone **Appliquer la stratégie de mise en quarantaine** s’affiche où vous sélectionnez la [stratégie de quarantaine](quarantine-policies.md) qui s’applique aux messages mis en quarantaine par la protection d’intelligence de boîte aux lettres.
       - **Si le message est détecté comme usurpation d’identité** : sélectionnez **Déplacer le message vers les dossiers Courrier indésirable Email des destinataires** (Standard) ou **Mettez le message en quarantaine** (Strict).  Si vous sélectionnez **Mettre en quarantaine le message**, une zone **Appliquer la stratégie de mise en quarantaine** s’affiche, où vous sélectionnez la [stratégie de quarantaine](quarantine-policies.md) qui s’applique aux messages mis en quarantaine par la protection contre l’usurpation d’identité.
     - **Conseils de sécurité & section Indicateurs** : Configurez les paramètres suivants :
       - **Afficher le premier conseil de sécurité du contact** : Sélectionnez (activer).
       - **Afficher l’info-bulle de sécurité de l’emprunt d’identité de l’utilisateur** : Sélectionnez (activer).<sup>\*</sup>
       - **Afficher l’info-bulle de sécurité d’emprunt d’identité de domaine** : Sélectionnez (activer).<sup>\*</sup>
       - **Afficher le conseil de sécurité des caractères inhabituels d’emprunt d’identité de l’utilisateur** : Sélectionner (activer).<sup>\*</sup>
       - **Afficher (?) pour les expéditeurs non authentifiés pour l’usurpation d’identité** : Sélectionner (activer).
       - **Afficher la balise « via »** : Sélectionner (activer).

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   <sup>\*</sup>Ce paramètre est disponible uniquement dans Defender pour Office 365.

4. Cliquez sur **Enregistrer** , puis sur **Fermer**

Pour obtenir des instructions détaillées sur la configuration des stratégies anti-hameçonnage, consultez Configurer les stratégies [anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md) et Configurer les stratégies [anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="part-3---anti-spam-protection-in-eop"></a>Partie 3 : Protection contre le courrier indésirable dans EOP

Pour plus d’informations sur les paramètres recommandés pour la lutte contre le courrier indésirable, consultez [les paramètres de stratégie anti-courrier indésirable EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

1. Ouvrez la page **Des stratégies anti-courrier indésirable** dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com/antispam>.

2. Dans la page **Stratégies anti-courrier indésirable** , sélectionnez la stratégie nommée **Stratégie de trafic entrant anti-courrier indésirable (par défaut) dans** la liste en cliquant sur le nom.

3. Dans le menu volant des détails de stratégie qui s’affiche, configurez les paramètres suivants :
   - **Seuil d’e-mail en bloc & section propriétés du courrier indésirable** : Cliquez sur **Modifier le seuil et les propriétés du courrier indésirable**. Dans le menu volant qui s’affiche, configurez les paramètres suivants :
     - **Seuil d’e-mail en bloc** : définissez cette valeur sur 5 (Strict) ou 6 (Standard).
     - Laissez les autres paramètres à leurs valeurs par défaut (**Désactivé** ou **Aucun**).

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Section Actions** : Cliquez sur **Modifier les actions**. Dans le menu volant qui s’affiche, configurez les paramètres suivants :
     - **Section Actions de message** :
       - **Courrier indésirable** : vérifiez que **le dossier Déplacer le message vers le courrier indésirable Email** est sélectionné (Standard) ou sélectionnez **Message de quarantaine** (Strict).
       - **Courrier indésirable à haut niveau de confiance** : sélectionnez **le message de mise en quarantaine**.
       - **Hameçonnage** : sélectionner le **message de mise en quarantaine**.
       - **Hameçonnage à haut niveau de confiance** : vérifiez que les **messages de quarantaine** sont sélectionnés.
       - **En bloc** : vérifiez que **le dossier Déplacer le message vers le courrier indésirable Email** est sélectionné (Standard) ou sélectionnez **Message de quarantaine** (Strict).

       Pour chaque action dans laquelle vous sélectionnez **Message de mise en quarantaine**, une zone **de stratégie de mise en quarantaine s’affiche** , dans laquelle vous sélectionnez la [stratégie de quarantaine](quarantine-policies.md) qui s’applique aux messages mis en quarantaine par la protection anti-courrier indésirable.

     - **Conserver le courrier indésirable en quarantaine pendant ce nombre de jours** : vérifiez la valeur **30** jours.
     - **Activer les conseils de sécurité relatifs au courrier indésirable** : vérifiez que ce paramètre est sélectionné (activé).
     - **Activer le vidage automatique de zéro heure (ZAP)** : vérifiez que ce paramètre est sélectionné (activé).
       - **Activer les messages d’hameçonnage** : vérifiez que ce paramètre est sélectionné (activé). Pour plus d’informations, consultez [le vidage automatique de zéro heure (ZAP) pour le hameçonnage](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-phishing).
       - **Activer pour les messages indésirables** : vérifiez que ce paramètre est sélectionné (activé). Pour plus d’informations, consultez [le vidage automatique zero-hour (ZAP) pour le courrier indésirable](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-spam).

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Section Expéditeurs et domaines autorisés et bloqués** : passez en revue ou modifiez vos expéditeurs autorisés et domaines autorisés, comme décrit dans Créer des [listes d’expéditeurs bloqués dans EOP](create-block-sender-lists-in-office-365.md) ou [Créer des listes d’expéditeurs approuvés dans EOP](create-safe-sender-lists-in-office-365.md).

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. Lorsque vous avez terminé, cliquez sur **Fermer**.

Pour obtenir des instructions détaillées sur la configuration des stratégies anti-courrier indésirable, consultez Configurer les stratégies [anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365"></a>Partie 4 : Protection contre les URL et fichiers malveillants (liens sécurisés et pièces jointes sécurisées dans Defender pour Office 365)

La protection contre les URL et fichiers malveillants est disponible dans les abonnements qui incluent [Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Il est configuré via [des pièces jointes sécurisées et des](safe-attachments.md) [stratégies de liens fiables](safe-links.md) .

### <a name="safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Stratégies de pièces jointes sécurisées dans Microsoft Defender pour Office 365

Pour plus d’informations sur les paramètres recommandés pour les pièces jointes sécurisées, consultez . [Paramètres des pièces jointes sécurisées](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

1. Ouvrez la page **Pièces jointes sécurisées** dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com/safeattachmentv2>.

2. Dans la page **Pièces jointes sécurisées** , cliquez sur **Paramètres globaux**, puis configurez les paramètres suivants dans le menu volant qui s’affiche :
   - **Activez Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams** : activez ce paramètre (![activer/désactiver).](../../media/scc-toggle-on.png)

     > [!IMPORTANT]
     > **Avant d’activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams, vérifiez que la journalisation d’audit est activée dans votre organisation**. Cette action est généralement effectuée par une personne qui a le rôle Journaux d’audit attribué dans Exchange Online. Pour plus d’informations, consultez [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md) !

   - **Activer les documents sécurisés pour les clients Office** : activez ce paramètre (![activer/désactiver).](../../media/scc-toggle-on.png) Notez que cette fonctionnalité est disponible et significative uniquement avec les types de licences requis. Pour plus d’informations, consultez [Documents sécurisés dans Microsoft 365 E5](safe-docs.md).
   - **Autoriser les utilisateurs à cliquer sur l’affichage protégé même si des documents sécurisés ont identifié le fichier comme malveillant** : vérifiez que ce paramètre est désactivé (![désactiver).](../../media/scc-toggle-off.png))

   Lorsque vous avez terminé, cliquez sur **Enregistrer**

3. De retour sur la page **Pièces jointes sécurisées**, cliquez sur ![l’icône Créer.](../../media/m365-cc-sc-create-icon.png)

4. Dans l’Assistant **Création d’une stratégie de pièces jointes sécurisées** qui s’ouvre, configurez les paramètres suivants :
   - **Nommez votre page de stratégie** :
     - **Nom** : entrez quelque chose d’unique et de descriptif.
     - **Description** : entrez une description facultative.
   - **Page Utilisateurs et domaines** : étant donné qu’il s’agit de votre première stratégie et que vous souhaitez probablement optimiser la couverture, envisagez d’entrer vos [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) dans la zone **Domaines** . Sinon, vous pouvez utiliser les zones **Utilisateurs** et **groupes** pour un contrôle plus précis. Vous pouvez spécifier des exceptions en sélectionnant **Exclure ces utilisateurs, groupes et domaines et** en entrant des valeurs.
   - **Page Paramètres** :
     - **Réponse de programmes malveillants inconnus pièces jointes fiables** : Sélectionnez **Bloquer**.
     - **Stratégie de quarantaine** : la valeur par défaut est vide, ce qui signifie que la stratégie AdminOnlyAccessPolicy est utilisée. Les stratégies de quarantaine définissent ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine et si les utilisateurs reçoivent des notifications de quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).
     - **Redirection de la pièce jointe avec les pièces jointes détectées** : **activez la redirection** : activez ce paramètre (sélectionnez) et entrez une adresse e-mail pour recevoir les messages détectés.
     - **Appliquez la réponse de détection des pièces jointes sécurisées si l’analyse ne peut pas se terminer (délai d’expiration ou erreurs)** : vérifiez que ce paramètre est sélectionné.

5. Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

6. (Recommandé) En tant qu’administrateur général ou administrateur SharePoint Online, exécutez l’applet de commande **[Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant)** avec le paramètre _DisallowInfectedFileDownload_ défini `$true` sur SharePoint Online PowerShell.
   - `$true` bloque toutes les actions (à l’exception de Supprimer) pour les fichiers détectés. Personnes ne peut pas ouvrir, déplacer, copier ou partager des fichiers détectés.
   - `$false` bloque toutes les actions, à l’exception de Delete et Download. Personnes pouvez choisir d’accepter le risque et de télécharger un fichier détecté.

7. Autorisez jusqu’à 30 minutes pour que vos modifications s’étendent à tous les centres de données Microsoft 365.

Pour obtenir des instructions détaillées sur la configuration des stratégies de pièces jointes sécurisées et des paramètres globaux pour les pièces jointes sécurisées, consultez les rubriques suivantes :

- [Configurer des stratégies de pièces jointes sécurisées dans Microsoft Defender pour Office 365](set-up-safe-attachments-policies.md)
- [Activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md)
- [Documents sécurisés dans Microsoft 365 E5](safe-docs.md)

### <a name="safe-links-policies-in-microsoft-defender-for-office-365"></a>Stratégies de liens sécurisés dans Microsoft Defender pour Office 365

Pour plus d’informations sur les paramètres recommandés pour les liens sécurisés, consultez [Les paramètres liens fiables](recommended-settings-for-eop-and-office365.md#safe-links-settings).

1. Ouvrez la page **Liens sécurisés** dans le portail Microsoft 365 Defender, <https://security.microsoft.com/safelinksv2>puis cliquez sur ![Créer une icône.](../../media/m365-cc-sc-create-icon.png)

2. Dans l’Assistant **Créer des liens fiables** qui s’ouvre, configurez les paramètres suivants :
   - **Nommez votre page de stratégie** :
     - **Nom** : entrez quelque chose d’unique et de descriptif.
     - **Description** : entrez une description facultative.
   - **Page Utilisateurs et domaines** : étant donné qu’il s’agit de votre première stratégie et que vous souhaitez probablement optimiser la couverture, envisagez d’entrer vos [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) dans la zone **Domaines** . Sinon, vous pouvez utiliser les zones **Utilisateurs** et **groupes** pour un contrôle plus précis. Vous pouvez spécifier des exceptions en sélectionnant **Exclure ces utilisateurs, groupes et domaines et** en entrant des valeurs.
   - **Url & cliquez sur la page des paramètres de protection** :
     - **Action sur les URL potentiellement malveillantes dans la section e-mails** :
       - **Activé : Liens fiables vérifie une liste de liens connus et malveillants lorsque les utilisateurs cliquent sur des liens dans l’e-mail** : sélectionnez son paramètre (activer).
       - **Appliquer des liens sécurisés aux messages électroniques envoyés au sein de l’organisation** : sélectionnez ce paramètre (activer).
       - **Appliquez l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers** : sélectionnez ce paramètre (activer).
         - **Attendez que l’analyse d’URL se termine avant de remettre le message** : Sélectionnez ce paramètre (activer).
       - **Ne réécrivez pas les URL, effectuez des vérifications via l’API Liens fiables uniquement** : vérifiez que ce paramètre n’est pas sélectionné (désactivez).
     - **Ne réécrivez pas les URL suivantes dans l’e-mail** : nous n’avons aucune recommandation spécifique pour ce paramètre. Pour plus d’informations, consultez [les listes « Ne pas réécrire les URL suivantes » dans les stratégies liens fiables](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).
     - **Action pour les URL potentiellement malveillantes dans la section Microsoft Teams** :
       - ***Activé : Liens fiables vérifie une liste de liens malveillants connus lorsque les utilisateurs cliquent sur des liens dans Microsoft Teams** : sélectionnez ce paramètre (activer).
     - **Cliquez sur la section Paramètres de protection** :
       - **Suivre les clics de l’utilisateur** : vérifiez que ce paramètre est sélectionné (activé).
         - **Laissez les utilisateurs cliquer sur l’URL d’origine** : désactivez ce paramètre (non sélectionné).
         - **Afficher la personnalisation de l’organisation sur les pages de notification et d’avertissement** : la sélection de ce paramètre (activation) n’est significative qu’après avoir suivi les instructions du [thème Personnaliser 365 pour que votre organisation](../../admin/setup/customize-your-organization-theme.md) charge le logo de votre entreprise.
   - **Page de notification** :
     - **Comment voulez-vous informer les utilisateurs ?** section : Si vous le souhaitez, vous pouvez sélectionner **Utiliser le texte de notification personnalisé** pour entrer le texte de notification personnalisé à utiliser. Vous pouvez également sélectionner **Utiliser Microsoft Translator pour la localisation automatique afin** de traduire le texte de notification personnalisé dans la langue de l’utilisateur. Sinon, laissez **utiliser le texte de notification par défaut** sélectionné.

3. Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

Pour obtenir des instructions détaillées sur la configuration des stratégies de liens fiables et des paramètres globaux pour les liens sécurisés, consultez [Configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md).

### <a name="now-set-up-alerts-for-detected-files-in-sharepoint-online-or-onedrive-for-business"></a>À présent, configurez des alertes pour les fichiers détectés dans SharePoint Online ou OneDrive Entreprise

Pour recevoir une notification lorsqu’un fichier dans SharePoint Online ou OneDrive Entreprise a été identifié comme malveillant, vous pouvez configurer une alerte comme décrit dans cette section.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Email & stratégie** **d’alerte** **de règles** \> de & polices de collaboration\>.

2. Dans la page **Stratégie d’alerte** , cliquez sur **Nouvelle stratégie d’alerte**.

3. **L’Assistant Nouvelle stratégie d’alerte** s’ouvre. Dans la page **Nom** , configurez les paramètres suivants :
   - **Nom** : entrez un nom unique et descriptif. Par exemple, vous pouvez taper des fichiers malveillants dans des bibliothèques.
   - **Description** : entrez une description facultative.
   - **Gravité** : sélectionnez **Faible**, **Moyen** ou **Élevé**.
   - **Catégorie** : Sélectionner **la gestion des menaces**.

   Lorsque vous avez terminé, cliquez sur **Suivant**

4. Dans la page **Créer des paramètres d’alerte** , configurez les paramètres suivants :
   - **Sur quoi voulez-vous alerter ?** section : **L’activité est** \> **détectée dans un fichier de logiciels malveillants**.
   - **Comment voulez-vous que l’alerte soit déclenchée** section : Vérifier **chaque fois qu’une activité correspond à la règle** est sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**

5. Dans la page **Définir vos destinataires** , configurez les paramètres suivants :
   - **Envoyer des notifications par e-mail** : vérifiez que ce paramètre est sélectionné.
   - **Email destinataires** : sélectionnez un ou plusieurs administrateurs généraux, administrateurs de sécurité ou lecteurs de sécurité qui doivent recevoir une notification lorsqu’un fichier malveillant est détecté.
   - **Limite de notification quotidienne** : vérifiez **qu’aucune limite n’est** sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**

6. Dans la page **Vérifier vos paramètres** , passez en revue vos paramètres, vérifiez **que Oui, activez-le immédiatement** , puis cliquez sur **Terminer**

Pour en savoir plus sur les stratégies d’alerte, consultez Stratégies [d’alerte dans le portail de conformité Microsoft Purview](../../compliance/alert-policies.md).

> [!NOTE]
> Une fois la configuration terminée, utilisez ces liens pour démarrer les investigations de charge de travail :
>
> - [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
> - [Utilisez le portail Microsoft 365 Defender pour gérer les fichiers mis en quarantaine dans Defender pour Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365)
> - [Que faire lorsqu’un fichier malveillant est trouvé dans SharePoint Online, OneDrive ou Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
> - [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)

## <a name="post-setup-tasks-and-next-steps"></a>Tâches post-installation et étapes suivantes

Après avoir configuré les fonctionnalités de protection contre les menaces, veillez à surveiller le fonctionnement de ces fonctionnalités ! Examinez et modifiez vos stratégies afin qu’elles fassent ce dont vous avez besoin. Surveillez également les nouvelles fonctionnalités et mises à jour de service qui peuvent ajouter de la valeur.

|Procédure|Ressources pour en savoir plus|
|---|---|
|Découvrez comment les fonctionnalités de protection contre les menaces fonctionnent pour votre organisation en consultant les rapports|[Email rapports de sécurité](view-email-security-reports.md) <p> [Rapports pour Microsoft Defender pour Office 365](view-reports-for-mdo.md) <p> [Threat Explorer](threat-explorer.md)|
|Passez régulièrement en revue et modifiez vos stratégies de protection contre les menaces en fonction des besoins|[Degré de sécurisation](../defender/microsoft-secure-score.md) <p> [Fonctionnalités d’investigation et de réponse aux menaces Microsoft 365](./office-365-ti.md)|
|Surveiller les nouvelles fonctionnalités et mises à jour du service|[Options de publication standard et ciblée](../../admin/manage/release-options-in-office-365.md) <p> [Centre de messages](../../admin/manage/message-center.md) <p> [Feuille de route de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) <p> [Service Descriptions](/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
