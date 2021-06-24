---
title: Se protéger contre les menaces dans Microsoft Defender pour Office 365, anti-programme malveillant, anti-hameçonnage, anti-courrier indésirable, liens Coffre, pièces jointes Coffre, purge automatique heure zéro (ZAP), configuration de la sécurité MDO
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
localization_priority: Normal
ms.date: 06/22/2021
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
ms.openlocfilehash: 7e37b67dbed75e3283070ba94321fcb03979a5a6
ms.sourcegitcommit: ccbdf2638fc6646bfb89450169953f4c3ce4b9b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2021
ms.locfileid: "53105391"
---
# <a name="protect-against-threats"></a>Protéger contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Voici un guide de démarrage rapide qui décompose la configuration de Defender Office 365 en blocs. Si vous débutez avec les fonctionnalités de protection contre les menaces dans Office 365, si vous ne savez pas par où commencer, ou si vous apprenez mieux en faisant *cela,* utilisez ces instructions comme liste de contrôle et point de départ.

> [!IMPORTANT]
> **Les paramètres recommandés** initiaux sont inclus pour chaque type de stratégie ; toutefois, de nombreuses options sont disponibles et vous pouvez ajuster vos paramètres pour répondre aux besoins spécifiques de votre organisation. Laissez environ 30 minutes à vos stratégies ou modifications pour qu’elles fonctionnent dans votre centre de données.
>
> Pour ignorer la configuration manuelle de la plupart des stratégies dans Defender pour Office 365, vous pouvez utiliser des stratégies de sécurité prédéfines au niveau Standard ou Strict. Pour plus d’informations, voir [Stratégies de sécurité prédéfini dans EOP](preset-security-policies.md)et Microsoft Defender pour Office 365 .

## <a name="requirements"></a>Configuration requise

### <a name="subscriptions"></a>Abonnements

Les fonctionnalités de protection contre les menaces sont *incluses* dans tous les abonnements Office 365 Microsoft ; toutefois, certains abonnements disposent de fonctionnalités avancées. Le tableau ci-dessous répertorie les fonctionnalités de protection incluses dans cet article, ainsi que les exigences minimales d’abonnement.

> [!TIP]
> Notez qu’au-delà des instructions pour activer l’audit,  les étapes de démarrage de la protection anti-programme malveillant, anti-hameçonnage et anti-courrier indésirable, qui sont marquées dans le cadre de Office 365 Exchange Online Protection (**EOP**). Cela peut sembler étrange dans un article defender pour Office 365, jusqu’à ce que vous vous rappeliez (**Defender pour Office 365**) contient et s’appuie sur EOP.

<br>

****

|Type de protection|Configuration requise pour l’abonnement|
|---|---|
|Journalisation d’audit (à des fins de rapport)|[Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Protection anti-programme malveillant|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Protection anti-hameçonnage|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Protection anti-courrier indésirable|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Protection contre les URL et fichiers malveillants dans les e-mails et les documents Office (Coffre liens et Coffre pièces jointes)|[Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Rôles et autorisations

Pour configurer Defender pour les stratégies Office 365, vous devez avoir un rôle approprié. Voir le tableau ci-dessous pour les rôles qui peuvent faire ces actions.

<br>

****

|Rôle ou groupe de rôles|Où en savoir plus|
|---|---|
|administrateur général|[À propos des rôles d’administrateur Microsoft 365](../../admin/add-users/about-admin-roles.md)|
|Administrateur de sécurité|[Autorisations des rôles d’administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Gestion d’Organisation Exchange Online|[Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo)|
|

Pour en savoir plus, [consultez Autorisations dans le portail Microsoft 365 Defender.](permissions-microsoft-365-security-center.md)

### <a name="turn-on-audit-logging-for-reporting-and-investigation"></a>Activer la journalisation d’audit pour la rapport et l’examen

- Démarrez votre journalisation d’audit tôt. L’audit doit être **en cours pour** certaines des étapes suivantes. La journalisation d’audit est disponible dans les abonnements qui [incluent Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Pour afficher les données dans [](view-email-security-reports.md)les rapports de protection contre les menaces, les rapports de sécurité du courrier électronique et [l’Explorateur,](threat-explorer.md)la journalisation d’audit doit être *en cours.* Pour en savoir plus, voir Activer ou désactiver la [recherche dans le journal d’audit.](../../compliance/turn-audit-log-search-on-or-off.md)

## <a name="part-1---anti-malware-protection-in-eop"></a>Partie 1 : protection contre les programmes malveillants dans EOP

Pour plus d’informations sur les paramètres recommandés pour la protection contre les programmes malveillants, voir les paramètres de stratégie [anti-programme malveillant EOP.](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)

1. Ouvrez la page **Anti-programme** malveillant dans le portail Microsoft 365 Defender sur <https://security.microsoft.com/antimalwarev2> .

2. Dans la page **Anti-programme** malveillant, sélectionnez la stratégie nommée Par défaut **en** cliquant sur le nom.

3. Dans le volant de détails de stratégie qui s’ouvre, cliquez sur Modifier les paramètres de **protection,** puis configurez les paramètres suivants :
   - **Section Paramètres de** protection :
     - **Activez le filtre des pièces jointes courantes**: Sélectionner (activer). Cliquez **sur Personnaliser les types de fichiers** pour ajouter d’autres types de fichiers.
     - Activer la purge automatique zéro heure **pour les programmes malveillants**: vérifiez que ce paramètre est sélectionné. Pour plus d’informations sur ZAP pour les programmes malveillants, voir purge automatique heure zéro [(ZAP) pour les programmes malveillants.](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-malware)
   - **Section Notification** : vérifiez qu’aucun des paramètres de notification n’est sélectionné.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. Dans le menu volant des détails de la stratégie, cliquez sur **Fermer**.

Pour obtenir des instructions détaillées sur la configuration des stratégies anti-programme malveillant, voir Configurer des stratégies [anti-programme malveillant dans EOP.](configure-anti-malware-policies.md)

## <a name="part-2---anti-phishing-protection-in-eop-and-defender-for-office-365"></a>Partie 2 : protection anti-hameçonnage dans EOP et Defender pour Office 365

[La protection anti-hameçonnage](anti-phishing-protection.md) est disponible dans les abonnements qui incluent [EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). La protection anti-hameçonnage avancée est disponible dans [Defender pour les Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

Pour plus d’informations sur les paramètres recommandés pour les stratégies anti-hameçonnage, consultez les paramètres de stratégie [anti-hameçonnage EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) et de stratégie [anti-hameçonnage](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)dans Microsoft Defender pour Office 365 .

La procédure suivante décrit comment configurer la stratégie anti-hameçonnage par défaut. Paramètres disponibles uniquement dans Defender pour les Office 365 sont clairement marqués.

1. Ouvrez la page **Anti-hameçonnage** dans le portail Microsoft 365 Defender sur <https://security.microsoft.com/antiphishing> .

2. Dans la page **Anti-hameçonnage,** sélectionnez la stratégie **office 365** anti-hameçonnage par défaut (par défaut) en cliquant sur le nom.

3. Dans le volant de détails de stratégie qui s’affiche, configurez les paramètres suivants :
   - **Seuil de hameçonnage & section protection** : cliquez sur Modifier les **paramètres** de protection et configurez les paramètres suivants dans le volant qui s’ouvre :
     - **Seuil de courrier d’hameçonnage** <sup>\*</sup> : **sélectionnez 2 - Agressif** (Standard) ou **3 - Plus agressif** (Strict).
     - **Section Emprunt d’identité** <sup>\*</sup> : configurez les valeurs suivantes :
       - Sélectionnez Activer la protection des **utilisateurs,** cliquez sur le lien Gérer **(nn)** des expéditeurs qui s’affiche, puis ajoutez des expéditeurs internes et externes pour vous protéger contre l’emprunt d’identité, tels que les membres du conseil d’administration de votre organisation, votre PDG, votre directeur financier et d’autres cadres supérieurs.
       - Sélectionnez **Activer les domaines à protéger,** puis configurez les paramètres suivants qui s’affichent :
         - Sélectionnez **Inclure les domaines que** je possède pour protéger les expéditeurs internes dans vos domaines acceptés (visibles en cliquant sur Afficher mes domaines) contre l’emprunt d’identité. 
         - Pour protéger les expéditeurs dans d’autres domaines, sélectionnez Inclure des domaines **personnalisés,** cliquez sur le **lien Gérer (nn)** des domaines personnalisés qui s’affiche, puis ajoutez d’autres domaines pour vous protéger contre l’emprunt d’identité.
     - Section Ajouter des **expéditeurs** et des domaines de confiance : cliquez sur Gérer <sup>\*</sup> **(nn)** les expéditeurs et domaines de confiance pour configurer des exceptions de domaine d’expéditeur et d’expéditeur pour la protection contre l’emprunt d’identité si nécessaire.
     - Paramètres d’intelligence de boîte aux lettres : vérifiez que les paramètres Activer l’intelligence des boîtes aux lettres et Activer l’intelligence pour la protection contre l’emprunt <sup>\*</sup> d’identité sont sélectionnés.  
     - **Section Usurpation** : vérifiez que **l’intelligence contre l’usurpation** d’identité est sélectionnée.

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Section Actions** : cliquez **sur Modifier les actions** et configurez les paramètres suivants dans le volant qui s’ouvre :
     - **Section Actions de** message : Configurez les paramètres suivants :
       - **Si le message est détecté comme un utilisateur** dont l’identité est usurpée : <sup>\*</sup> sélectionnez mettre le message en **quarantaine.**
       - **Si le message est détecté comme un domaine** dont l’identité est usurpée : <sup>\*</sup> sélectionnez mettre le message en **quarantaine.**
       - **Si la veille de boîte** aux lettres détecte un utilisateur dont l’identité est usurpée : sélectionnez Déplacer le message vers les dossiers Courrier indésirable (Standard) des destinataires ou mettre le message en quarantaine <sup>\*</sup> (Strict).  
       - **Si le message est détecté comme** usurpant l’adresse : sélectionnez Déplacer le message vers les dossiers Courrier indésirable (Standard) des **destinataires** ou mettre le **message** en quarantaine (Strict).
     - **Conseils de & section sur les** indicateurs de sécurité : Configurez les paramètres suivants :
       - **Afficher le premier contact conseil de sécurité**: Sélectionner (activer).
       - **Afficher l’emprunt d’conseil de sécurité** <sup>\*</sup> : Sélectionner (activer).
       - **Afficher l’emprunt d’conseil de sécurité** <sup>\*</sup> : Sélectionner (activer).
       - **Afficher les caractères inhabituels d’emprunt d’conseil de sécurité** <sup>\*</sup> : Sélectionner (activer).
       - **Afficher (?) pour les expéditeurs non authentifiés** pour l’usurpation d’adresse : Sélectionnez (activer).
       - **Afficher la balise « via »**: Sélectionner (activer).

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   <sup>\*</sup>Ce paramètre est disponible uniquement dans Defender pour les Office 365.

4. Cliquez **sur Enregistrer,** puis sur **Fermer**

Pour obtenir des instructions détaillées sur la configuration des stratégies anti-hameçonnage, voir [Configure anti-phishing policies in EOP](configure-anti-phishing-policies-eop.md) and [Configure anti-phishing policies in Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="part-3---anti-spam-protection-in-eop"></a>Partie 3 : protection contre le courrier indésirable dans EOP

Pour plus d’informations sur les paramètres recommandés pour la détection du courrier indésirable, consultez la liste des paramètres de stratégie [anti-courrier indésirable EOP.](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

1. Ouvrez la page **Stratégies anti-courrier** indésirable dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com/antispam> .

2. Dans la page **Stratégies anti-courrier** indésirable, sélectionnez la stratégie nommée Stratégie de courrier indésirable entrant **(par défaut)** dans la liste en cliquant sur le nom.

3. Dans le volant de détails de stratégie qui s’affiche, configurez les paramètres suivants :
   - **Seuil de courrier électronique en & section Propriétés du** courrier indésirable : cliquez sur **Modifier le seuil de courrier indésirable et les propriétés.** Dans le volant qui s’affiche, configurez les paramètres suivants :
     - **Seuil de courrier en masse**: définissez cette valeur sur 5 (Strict) ou 6 (Standard).
     - Laissez les autres paramètres à leurs valeurs par défaut (**Off** ou **None**).

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Section Actions** : Cliquez sur **Modifier les actions.** Dans le volant qui s’affiche, configurez les paramètres suivants :
     - **Section Actions de** message :
       - **Courrier** indésirable : vérifiez **que le déplacement du message** vers le dossier Courrier indésirable est sélectionné (Standard) ou sélectionnez Message de mise en quarantaine (Strict). 
       - **Courrier indésirable à niveau de confiance élevé**: sélectionnez le message de mise en **quarantaine.**
       - **Hameçonnage :** sélectionner un **message de mise en quarantaine.**
       - **Hameçonnage à haut niveau de confiance**: vérifier que les messages de **mise** en quarantaine sont sélectionnés.
       - **En bloc**: vérifiez **que le déplacement du message** vers le dossier Courrier indésirable est sélectionné (Standard) ou sélectionnez Message de mise en quarantaine (Strict). 
     - **Conserver le courrier indésirable en quarantaine pendant ce nombre de jours**: vérifiez la valeur **30** jours.
     - **Activer les conseils de sécurité contre** le courrier indésirable : vérifiez que ce paramètre est sélectionné (activé).
     - **Activer la purge automatique d’heure zéro (ZAP)**: vérifiez que ce paramètre est sélectionné (activé).
       - **Activer les messages de hameçonnage**: vérifiez que ce paramètre est sélectionné (activé). Pour plus d’informations, voir [zap (zero-hour auto purge) for phishing](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-phishing).
       - **Activer pour les messages indésirables**: vérifiez que ce paramètre est sélectionné (activé). Pour plus d’informations, voir [la purge automatique d’heure zéro (ZAP) pour le courrier indésirable.](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-spam)
     - **Section Notifications** :
       - Sélectionnez **Activer les notifications de courrier indésirable pour l’utilisateur final.**
         - **Envoyer des notifications de courrier indésirable** à l’utilisateur final tous les (jours) : vérifiez la valeur **3** jours.
         - **Langue**: vérifiez la valeur **par** défaut ou sélectionnez une langue.

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Section Expéditeurs** et domaines autorisés et bloqués : Examinez ou modifiez vos expéditeurs et domaines autorisés, comme décrit dans Créer des listes d’expéditeurs bloqués dans [EOP](create-block-sender-lists-in-office-365.md) ou Créer des listes d’expéditeurs autorisés [dans EOP.](create-safe-sender-lists-in-office-365.md)

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. Lorsque vous avez terminé, cliquez sur **Fermer**.

Pour obtenir des instructions détaillées sur la configuration des stratégies anti-courrier indésirable, voir [Configure anti-spam policies in EOP](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365"></a>Partie 4 : protection contre les URL et les fichiers malveillants (Coffre liens et Coffre pièces jointes dans Defender pour Office 365)

La protection au moment du clic contre les URL et fichiers malveillants est disponible dans les abonnements qui incluent [Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Elle est définie par le biais de Coffre [pièces jointes et](safe-attachments.md) [Coffre de liens.](safe-links.md)

### <a name="safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Coffre Stratégies de pièces jointes dans Microsoft Defender Office 365

Pour plus d’informations sur les paramètres recommandés pour Coffre pièces jointes, voir . [Coffre de pièces jointes.](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)

1. Ouvrez la page **Coffre pièces jointes** dans le portail Microsoft 365 Defender à l’Microsoft 365 Defender. <https://security.microsoft.com/safeattachmentv2>

2. Dans la page **Coffre pièces jointes,** cliquez sur **Paramètres** globaux, puis configurez les paramètres suivants dans le volant qui s’affiche :
   - **Activer Defender pour Office 365** pour SharePoint, OneDrive et Microsoft Teams : activer ce paramètre (activer). ![ ](../../media/scc-toggle-on.png)

     > [!IMPORTANT]
     > **Avant d’activer Coffre pièces jointes** pour SharePoint, OneDrive et Microsoft Teams, vérifiez que la journalisation d’audit est désactivée dans votre organisation. Cette action est généralement effectuée par une personne dont le rôle Journaux d’audit est attribué Exchange Online. Pour plus d’informations, voir Activer ou désactiver la [recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md)!

   - **Activer Coffre documents pour Office clients :** activer ce paramètre ![ ](../../media/scc-toggle-on.png) (activer). Notez que cette fonctionnalité est disponible et significative uniquement avec Microsoft 365 E5 ou Microsoft 365 E5 Sécurité licences.
   - **Autoriser les utilisateurs** à cliquer dans le affichage protégé, même si Coffre Documents a identifié le fichier comme malveillant : vérifiez que ce paramètre est désactivé ![ (bascule). ](../../media/scc-toggle-off.png)

   Lorsque vous avez terminé, cliquez sur **Enregistrer**

3. De retour sur la page **Coffre pièces jointes,** cliquez sur ![ Créer une ](../../media/m365-cc-sc-create-icon.png) icône.

4. Dans **l’Assistant Créer Coffre pièces jointes** qui s’ouvre, configurez les paramètres suivants :
   - **Nommez votre** page de stratégie :
     - **Nom**: entrez quelque chose d’unique et de descriptif.
     - **Description**: entrez une description facultative.
   - **Page Utilisateurs** et domaines : comme il s’agit de votre première stratégie et que vous souhaitez probablement optimiser la couverture, envisagez d’entrer vos domaines [acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) dans la zone **Domaines.** Dans le cas contraire, vous pouvez utiliser les zones **Utilisateurs** et groupes pour un contrôle plus granulaire.  Vous pouvez spécifier des exceptions en sélectionnant **Exclure ces utilisateurs,** groupes et domaines et en entrant des valeurs.
   - **Paramètres** page :
     - **Coffre de programmes malveillants inconnus pièces jointes**: **sélectionnez Bloquer**.
     - **Rediriger la pièce** jointe avec les pièces jointes détectées : activer la **redirection**: activer (sélectionner) ce paramètre et entrer une adresse de messagerie pour recevoir les messages détectés.
     - Appliquez la Coffre détection des pièces jointes si l’analyse ne peut pas se terminer **(délai d’Coffre** ou erreurs) : vérifiez que ce paramètre est sélectionné.

5. Lorsque vous avez terminé, cliquez sur **Envoyer,** puis sur **Terminé.**

6. (Recommandé) En tant qu’administrateur général ou administrateur SharePoint Online, exécutez la cmdlet **[Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant)** avec le paramètre _DisallowInfectedFileDownload_ dans `$true` SharePoint Online PowerShell.
   - `$true` bloque toutes les actions (à l’exception de Supprimer) pour les fichiers détectés. Les personnes ne peuvent pas ouvrir, déplacer, copier ou partager des fichiers détectés.
   - `$false` bloque toutes les actions à l’exception de Supprimer et télécharger. Les personnes peuvent choisir d’accepter le risque et de télécharger un fichier détecté.

7. Autorisez jusqu’à 30 minutes pour que vos modifications se propagent à tous Microsoft 365 centres de données.

Pour obtenir des instructions détaillées sur la configuration des stratégies Coffre pièces jointes et des paramètres globaux pour Coffre pièces jointes, consultez les rubriques suivantes :

- [Configurer des stratégies Coffre pièces jointes dans Microsoft Defender pour Office 365](set-up-safe-attachments-policies.md)
- [Activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md)
- [Documents sécurisés dans Microsoft 365 E5](safe-docs.md)

### <a name="safe-links-policies-in-microsoft-defender-for-office-365"></a>Coffre Stratégies de liens dans Microsoft Defender pour Office 365

Pour plus d’informations sur les paramètres recommandés pour les liens Coffre, voir Coffre [liens recommandés.](recommended-settings-for-eop-and-office365.md#safe-links-settings)

1. Ouvrez la page **Coffre liens dans** le portail Microsoft 365 Defender à <https://security.microsoft.com/safelinksv2> l’Microsoft 365 Defender.

2. Dans la page **Coffre** liens, cliquez sur **Paramètres** globaux, puis configurez les paramètres suivants dans le volant qui s’affiche :
   - **Paramètres qui s’appliquent au contenu de la** section Office 365 applications suivantes :
     - **Utilisez Coffre liens dans Office 365 applications :** vérifiez que ce paramètre est allumé ![ ](../../media/scc-toggle-on.png) (bascule).
     - **Ne pas suivre le moment où les** utilisateurs cliquent sur les liens protégés dans Office 365 applications : désactiver ce paramètre ![ ](../../media/scc-toggle-off.png) (désactiver).
     - **Ne laissez pas les utilisateurs** accéder à l’URL d’origine dans Office 365 applications : vérifiez que ce paramètre est allumé ![ (basculement). ](../../media/scc-toggle-on.png)

   Lorsque vous avez terminé, cliquez sur **Enregistrer**

3. De retour sur la page **Coffre liens,** cliquez sur ![ Créer une ](../../media/m365-cc-sc-create-icon.png) icône.

4. Dans **l’Assistant Créer Coffre liens** qui s’ouvre, configurez les paramètres suivants :
   - **Nommez votre** page de stratégie :
     - **Nom**: entrez quelque chose d’unique et de descriptif.
     - **Description**: entrez une description facultative.
   - **Page Utilisateurs** et domaines : comme il s’agit de votre première stratégie et que vous souhaitez probablement optimiser la couverture, envisagez d’entrer vos domaines [acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) dans la zone **Domaines.** Dans le cas contraire, vous pouvez utiliser les zones **Utilisateurs** et groupes pour un contrôle plus granulaire.  Vous pouvez spécifier des exceptions en sélectionnant **Exclure ces utilisateurs,** groupes et domaines et en entrant des valeurs.
   - **Page Paramètres de** protection :
     - **Sélectionnez l’action pour les URL potentiellement malveillantes inconnues dans** les messages : Activer ce **paramètre.**
     - **Sélectionnez l’action pour les URL inconnues** ou potentiellement malveillantes dans Microsoft Teams : activer ce **paramètre.** À partir de mars 2020, ce paramètre est en prévisualisation et est disponible ou fonctionnel uniquement pour les membres du Microsoft Teams Technology Adoption Program (TAP).
     - **Appliquez l’analyse d’URL en** temps réel pour les liens suspects et les liens qui pointent vers des fichiers : sélectionnez ce paramètre (activer).
       - **Attendez que l’analyse de l’URL se termine avant de remettre le message**: sélectionnez ce paramètre (activer).
     - **Appliquer Coffre liens vers les messages électroniques envoyés** au sein de l’organisation : sélectionnez ce paramètre (activer).
     - **Ne pas suivre les clics de l’utilisateur**: vérifiez que ce paramètre n’est pas sélectionné (désactivé).
     - **Ne laissez pas les utilisateurs cliquer sur l’URL d’origine**: vérifiez que ce paramètre est allumé (sélectionné).
     - Affichez la personnalisation de l’organisation sur les pages de **notification** et d’avertissement : la sélection de ce paramètre (l’allumer) n’est significative qu’après avoir suivi les instructions de personnaliser le thème [Microsoft 365](../../admin/setup/customize-your-organization-theme.md) pour que votre organisation télécharge le logo de votre entreprise.
     - **Ne réécrivez pas les URL suivantes**: nous n’avons aucune recommandation spécifique pour ce paramètre. Pour plus d’informations, voir [« Ne pas réécrire](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)les URL suivantes » dans Coffre de liens.
   - **Page de** notification :
     - **Comment souhaitez-vous avertir les utilisateurs ?** section : Si vous le souhaitez, vous pouvez sélectionner Utiliser un texte de **notification** personnalisé pour entrer le texte de notification personnalisé à utiliser. Vous pouvez également sélectionner **Utiliser Traducteur Microsoft pour** la localisation automatique afin de traduire le texte de notification personnalisé dans la langue de l’utilisateur. Sinon, laissez **le texte de notification par** défaut sélectionné.

5. Lorsque vous avez terminé, cliquez sur **Envoyer,** puis sur **Terminé.**

Pour obtenir des instructions détaillées sur la configuration des stratégies Coffre liens et des paramètres globaux pour Coffre liens, consultez les rubriques suivantes :

- [Configurer des stratégies Coffre de liens dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md)
- [Configurer les paramètres globaux pour Coffre liens vers Microsoft Defender pour Office 365](configure-global-settings-for-safe-links.md)

### <a name="now-set-up-alerts-for-detected-files-in-sharepoint-online-or-onedrive-for-business"></a>À présent, configurer des alertes pour les fichiers détectés dans SharePoint Online ou OneDrive Entreprise

Pour recevoir une notification lorsqu’un fichier dans SharePoint Online ou OneDrive Entreprise a été identifié comme malveillant, vous pouvez configurer une alerte comme décrit dans cette section.

1. In the Microsoft 365 Defender portal at <https://security.microsoft.com> , go to Email & **collaboration** \> **Polices & rules** Alert \> **policy**.

2. Dans la page **Stratégie d’alerte,** cliquez **sur Nouvelle stratégie d’alerte.**

3. **L’Assistant Nouvelle stratégie d’alerte** s’ouvre. Dans la page **Nom,** configurez les paramètres suivants :
   - **Nom**: entrez un nom unique et descriptif. Par exemple, vous pouvez taper Des fichiers malveillants dans des bibliothèques.
   - **Description**: entrez une description facultative.
   - **Gravité :** sélectionnez **Faible,** **Moyen** ou **Élevé**.
   - **Catégorie :** sélectionnez **Gestion des menaces.**

   Lorsque vous avez terminé, cliquez sur **Suivant**

4. Dans la page **Créer des paramètres d’alerte,** configurez les paramètres suivants :
   - **Sur quoi voulez-vous alerter ?** section: **Activity is** \> **Detected malware in file**.
   - **Comment voulez-vous que l’alerte soit** déclenchée : Vérifiez chaque fois qu’une activité **correspond à la** règle est sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**

5. Dans la page **Définir vos destinataires,** configurez les paramètres suivants :
   - **Envoyer des notifications par courrier** électronique : vérifiez que ce paramètre est vérifié.
   - **Destinataires du courrier électronique**: sélectionnez un ou plusieurs administrateurs globaux, administrateurs de sécurité ou lecteurs de sécurité qui doivent recevoir une notification lorsqu’un fichier malveillant est détecté.
   - **Limite de notification quotidienne**: vérifiez **qu’aucune limite** n’est sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**

6. Dans la page **Vérifier vos paramètres,** vérifiez vos paramètres, vérifiez que **oui,** l’activer immédiatement est sélectionné, puis cliquez sur **Terminer**

Pour en savoir plus sur les stratégies d’alerte, consultez [stratégies d’alerte dans la Centre de conformité Microsoft 365](../../compliance/alert-policies.md).

> [!NOTE]
> Lorsque vous avez terminé la configuration, utilisez ces liens pour lancer des enquêtes sur la charge de travail :
>
>- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
>- [Utilisez le portail Microsoft 365 Defender pour gérer les fichiers mis en quarantaine dans Defender pour Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365)
>- [Que faire lorsqu’un fichier malveillant est trouvé dans SharePoint Online, OneDrive ou Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
>- [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)

## <a name="post-setup-tasks-and-next-steps"></a>Tâches post-installation et étapes suivantes

Après avoir configuré les fonctionnalités de protection contre les menaces, veillez à surveiller leur fonctionnement ! Examinez et révisez vos stratégies afin qu’elles s’en sortent comme vous le souhaitez. Observez également les nouvelles fonctionnalités et mises à jour de service qui peuvent ajouter de la valeur.

<br>

****

|Procédure|Ressources pour en savoir plus|
|---|---|
|Découvrez comment fonctionnent les fonctionnalités de protection contre les menaces pour votre organisation en visualxant des rapports|[Rapports de sécurité de messagerie](view-email-security-reports.md) <p> [Rapports pour Microsoft Defender pour Office 365](view-reports-for-mdo.md) <p> [Threat Explorer](threat-explorer.md)|
|Examiner et réviser régulièrement vos stratégies de protection contre les menaces selon vos besoins|[Degré de sécurisation](../defender/microsoft-secure-score.md) <p> [Microsoft 365 d’investigation et de réponse aux menaces](./office-365-ti.md)|
|Surveiller les nouvelles fonctionnalités et les mises à jour de service|[Options de publication standard et ciblée](../../admin/manage/release-options-in-office-365.md) <p> [Centre de messages](../../admin/manage/message-center.md) <p> [Feuille de route de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) <p> [Service Descriptions](/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
|
