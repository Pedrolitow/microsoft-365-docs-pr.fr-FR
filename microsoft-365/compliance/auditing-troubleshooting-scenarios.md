---
title: Rechercher dans le journal d’audit pour résoudre les problèmes courants
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Découvrez comment utiliser l’outil de recherche de journaux d’audit Microsoft 365 pour résoudre les problèmes courants de support pour les comptes de messagerie.
ms.openlocfilehash: d97e8e074c2d0e14bb75fd46a512cacb6827047a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633848"
---
# <a name="search-the-audit-log-to-investigate-common-support-issues"></a>Rechercher dans le journal d’audit pour examiner les problèmes de support courants

Cet article explique comment utiliser l’outil de recherche dans les journaux d’audit pour vous aider à examiner les problèmes de support courants. Cela inclut l’utilisation du journal d’audit pour :

- Rechercher l’adresse IP de l’ordinateur utilisé pour accéder à un compte compromis
- Déterminer qui configure le transfert d’e-mail pour une boîte aux lettres
- Déterminer si un utilisateur a supprimé des éléments de messagerie dans sa boîte aux lettres
- Déterminer si un utilisateur a créé une règle de boîte de réception
- Examiner la raison pour laquelle un utilisateur externe à votre organisation a réussi à se connecter
- Rechercher les activités de boîte aux lettres effectuées par les utilisateurs disposant de licences non E5
- Rechercher les activités de boîte aux lettres effectuées par les utilisateurs délégués

## <a name="using-the-audit-log-search-tool"></a>Utilisation de l’outil de recherche dans les journaux d’audit

Chacun des scénarios de résolution des problèmes décrits dans cet article est basé sur l’utilisation de l’outil de recherche de journaux d’audit dans le portail de conformité Microsoft Purview. Cette section répertorie les autorisations requises pour effectuer une recherche dans le journal d’audit et décrit les étapes d’accès et d’exécution des recherches dans les journaux d’audit. Chaque section de scénario explique comment configurer une requête de recherche dans le journal d’audit et ce qu’il faut rechercher dans les informations détaillées dans les enregistrements d’audit qui correspondent aux critères de recherche.

### <a name="permissions-required-to-use-the-audit-log-search-tool"></a>Autorisations requises pour utiliser l’outil de recherche de journal d’audit

Le rôle journaux d’audit ou journaux d’audit View-Only doit vous être attribué dans Exchange Online pour effectuer une recherche dans le journal d’audit. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page **Autorisations** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. Les administrateurs globaux dans votre client Office 365 et Microsoft 365 sont automatiquement des membres du groupe de rôle Gestion de l'organisation dans Exchange Online. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](/Exchange/permissions-exo/role-groups).

### <a name="running-audit-log-searches"></a>Exécution de recherches dans le journal d’audit

Cette section décrit les principes de base de la création et de l’exécution de recherches dans les journaux d’audit. Utilisez ces instructions comme point de départ pour chaque scénario de résolution des problèmes dans cet article. Pour obtenir des instructions détaillées, consultez [Rechercher dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md#step-1-run-an-audit-log-search).

1. Allez sur <https://compliance.microsoft.com/auditlogsearch> et connectez-vous à l’aide de votre compte professionnel ou scolaire.
  
    La page **Audit** s’affiche.
  
    ![Configurez les critères, puis sélectionnez Rechercher pour exécuter la recherche.](../media/AuditLogSearchPage1.png)
  
2. Vous pouvez configurer les critères de recherche suivants. Chaque scénario de résolution des problèmes de cet article recommande des conseils spécifiques pour la configuration de ces champs.
  
   a. **Date de début** et **date de fin :** sélectionnez une plage de dates et d’heures pour afficher les événements qui se sont produits au cours de cette période. Les sept derniers jours sont sélectionnés par défaut. Les date et heure sont présentées au format UTC (temps universel coordonné). La plage de dates maximale que vous pouvez spécifier est de 90 jours.

   b. **Activités:** Sélectionnez la liste déroulante pour afficher les activités que vous pouvez rechercher. Une fois la recherche terminée, seuls les enregistrements d’audit correspondant aux activités sélectionnées apparaissent. La sélection **d’Afficher les résultats pour toutes les activités affiche les** résultats de toutes les activités qui répondent aux autres critères de recherche. Vous devrez également laisser ce champ vide dans certains des scénarios de résolution des problèmes.
  
    c. **Utilisateurs:** Cliquez dans cette zone, puis sélectionnez un ou plusieurs utilisateurs pour lequel afficher les résultats de la recherche. Les enregistrements d’audit de l’activité sélectionnée effectuées par les utilisateurs que vous sélectionnez dans cette zone sont affichés dans la liste des résultats. Laissez cette zone vide pour renvoyer les entrées pour tous les utilisateurs (et les comptes de service) dans votre organisation.
  
    d. **Fichier, dossier ou site :** Tapez une partie ou la totalité d’un nom de fichier ou de dossier pour rechercher l’activité liée au fichier de dossier qui contient le mot clé spécifié. Vous pouvez également spécifier l’URL d’un fichier ou d’un dossier. Si vous utilisez une URL, assurez-vous que le type du chemin d’URL complet ou si vous tapez uniquement une partie de l’URL, n’incluez pas de caractères ou d’espaces spéciaux. Laissez cette zone vide pour renvoyer les entrées correspondant à tous les fichiers et dossiers dans votre organisation. Ce champ est laissé vide dans tous les scénarios de résolution des problèmes de cet article.
  
3. Sélectionnez **Rechercher** pour exécuter la recherche à l’aide de vos critères de recherche.
  
    Les résultats de la recherche sont chargés et, après quelques instants, ils sont affichés sur une page de l’outil de recherche dans le journal d’audit. Chacune des sections de cet article fournit des conseils sur les éléments à rechercher dans le contexte du scénario de dépannage spécifique.

    Pour plus d’informations sur l’affichage et l’exportation des résultats de la recherche dans le journal d’audit, consultez :

    - [Afficher les résultats de la recherche](search-the-audit-log-in-security-and-compliance.md#step-2-view-the-search-results)
  
    - [Exporter les résultats de la recherche](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file)

## <a name="find-the-ip-address-of-the-computer-used-to-access-a-compromised-account"></a>Rechercher l’adresse IP de l’ordinateur utilisé pour accéder à un compte compromis

L’adresse IP correspondant à une activité effectuée par n’importe quel utilisateur est incluse dans la plupart des enregistrements d’audit. Les informations sur le client utilisé sont également incluses dans l’enregistrement d’audit.

Voici comment configurer une requête de recherche dans le journal d’audit pour ce scénario :

**Activités:** Si elle est pertinente pour votre cas, sélectionnez une activité spécifique à rechercher. Pour résoudre les problèmes de comptes compromis, envisagez de sélectionner **l’utilisateur connecté à** l’activité de boîte aux **lettres sous activités de boîte aux lettres Exchange**. Cette opération retourne des enregistrements d’audit montrant l’adresse IP utilisée lors de la connexion à la boîte aux lettres. Sinon, laissez ce champ vide pour retourner les enregistrements d’audit pour toutes les activités. 

> [!TIP]
> Le fait de laisser ce champ vide renvoie les activités **UserLoggedIn** , qui est une activité Azure Active Directory qui indique qu’une personne s’est connectée à un compte d’utilisateur. Utilisez le filtrage dans les résultats de la recherche pour afficher les enregistrements **d’audit UserLoggedIn** .

**Date de début** et **date de fin :** sélectionnez une plage de dates applicable à votre enquête.

**Utilisateurs:** Si vous examinez un compte compromis, sélectionnez l’utilisateur dont le compte a été compromis. Cette opération retourne des enregistrements d’audit pour les activités effectuées par ce compte d’utilisateur.

**Fichier, dossier ou site :** Laissez ce champ vide.

Après avoir exécuté la recherche, l’adresse IP de chaque activité s’affiche dans la colonne **d’adresse IP** dans les résultats de la recherche. Sélectionnez l’enregistrement dans les résultats de la recherche pour afficher des informations plus détaillées sur la page de menu volant.

## <a name="determine-who-set-up-email-forwarding-for-a-mailbox"></a>Déterminer qui configure le transfert d’e-mail pour une boîte aux lettres

Lorsque le transfert de courrier est configuré pour une boîte aux lettres, les messages électroniques envoyés à la boîte aux lettres sont transférés vers une autre boîte aux lettres. Les messages peuvent être transférés aux utilisateurs à l’intérieur ou à l’extérieur de votre organisation. Lorsque le transfert de courrier est configuré sur une boîte aux lettres, l’applet de commande **sous-jacente Exchange Online utilisée est Set-Mailbox**.

Voici comment configurer une requête de recherche dans le journal d’audit pour ce scénario :

**Activités:** Laissez ce champ vide afin que la recherche retourne des enregistrements d’audit pour toutes les activités. Cela est nécessaire pour retourner les enregistrements d’audit liés à l’applet **de commande Set-Mailbox** .

**Date de début** et **date de fin :** sélectionnez une plage de dates applicable à votre enquête.

**Utilisateurs:** Sauf si vous examinez un problème de transfert d’e-mail pour un utilisateur spécifique, laissez ce champ vide. Cela vous permet d’identifier si le transfert d’e-mail a été configuré pour n’importe quel utilisateur.

**Fichier, dossier ou site :** Laissez ce champ vide.

Après avoir exécuté la recherche, sélectionnez **Filtrer les résultats** dans la page des résultats de la recherche. Dans la zone sous l’en-tête **de colonne Activité** , **tapez Set-Mailbox** afin que seuls les enregistrements d’audit liés à l’applet de commande **Set-Mailbox** soient affichés.

![Filtrage des résultats d’une recherche dans le journal d’audit.](../media/emailforwarding1.png)

À ce stade, vous devez examiner les détails de chaque enregistrement d’audit pour déterminer si l’activité est liée au transfert de courrier électronique. Sélectionnez l’enregistrement d’audit pour afficher la page de menu volant **Détails** , puis sélectionnez **Plus d’informations**. La capture d’écran et les descriptions suivantes mettent en évidence les informations qui indiquent que le transfert d’e-mail a été défini sur la boîte aux lettres.

![Informations détaillées de l’enregistrement d’audit.](../media/emailforwarding2.png)

a. Dans le champ **ObjectId** , l’alias de la boîte aux lettres sur laquelle le transfert de courrier a été défini s’affiche. Cette boîte aux lettres s’affiche également dans la colonne **Élément** dans la page des résultats de la recherche.

b. Dans le champ **Paramètres** , la valeur *ForwardingSmtpAddress* indique que le transfert d’e-mail a été défini sur la boîte aux lettres. Dans cet exemple, le courrier est transféré à l’adresse e-mail mike@contoso.com, qui n’appartient pas à l’organisation alpinehouse.onmicrosoft.com.

c. La valeur *True* du paramètre *DeliverToMailboxAndForward* indique qu’une copie du message est remise à sarad@alpinehouse.onmicrosoft.com *et* est transférée à l’adresse e-mail spécifiée par le paramètre *ForwardingSmtpAddress* , qui est mike@contoso.com dans cet exemple. Si la valeur du paramètre *DeliverToMailboxAndForward* est définie sur *False*, le courrier électronique est uniquement transféré à l’adresse spécifiée par le paramètre *ForwardingSmtpAddress* . Il n’est pas remis à la boîte aux lettres spécifiée dans le champ **ObjectId** .

d. Le champ **UserId** indique l’utilisateur qui a défini le transfert d’e-mail sur la boîte aux lettres spécifiée dans le champ **ObjectId** . Cet utilisateur s’affiche également dans la colonne **Utilisateur** de la page des résultats de la recherche. Dans ce cas, il semble que le propriétaire de la boîte aux lettres a défini le transfert de courrier électronique sur sa boîte aux lettres.

Si vous déterminez que le transfert de courrier ne doit pas être défini sur la boîte aux lettres, vous pouvez le supprimer en exécutant la commande suivante dans Exchange Online PowerShell :

```powershell
Set-Mailbox <mailbox alias> -ForwardingSmtpAddress $null 
```

Pour plus d’informations sur les paramètres liés au transfert de courrier électronique, consultez l’article [Set-Mailbox](/powershell/module/exchange/set-mailbox) .

## <a name="determine-if-a-user-deleted-email-items"></a>Déterminer si un utilisateur a supprimé des éléments de messagerie

À compter de janvier 2019, Microsoft active la journalisation de l’audit de boîte aux lettres par défaut pour toutes les organisations Office 365 et Microsoft. Cela signifie que certaines actions effectuées par les propriétaires de boîtes aux lettres sont automatiquement journalisées et que les enregistrements d’audit de boîte aux lettres correspondants sont disponibles lorsque vous les recherchez dans le journal d’audit de la boîte aux lettres. Avant d’activer l’audit de boîte aux lettres par défaut, vous deviez l’activer manuellement pour chaque boîte aux lettres utilisateur de votre organisation. 

Les actions de boîte aux lettres enregistrées par défaut incluent les actions de boîte aux lettres SoftDelete et HardDelete effectuées par les propriétaires de boîtes aux lettres. Cela signifie que vous pouvez utiliser les étapes suivantes pour rechercher dans le journal d’audit les événements liés aux éléments de courrier supprimés. Pour plus d’informations sur l’audit de boîte aux lettres par défaut, consultez [Gérer l’audit de boîte aux lettres](enable-mailbox-auditing.md).

Voici comment configurer une requête de recherche dans le journal d’audit pour ce scénario :

**Activités:** Sous **activités de boîte aux lettres Exchange**, sélectionnez une ou les deux activités suivantes :

- **Messages supprimés du dossier Éléments supprimés :** Cette activité correspond à l’action d’audit de boîte aux lettres **SoftDelete** . Cette activité est également journalisée lorsqu’un utilisateur supprime définitivement un élément en le sélectionnant et en appuyant sur **Maj+Supprimer**. Une fois qu’un élément a été supprimé définitivement, l’utilisateur peut le récupérer jusqu’à ce que la période de rétention des éléments supprimés expire.

- **Messages supprimés de la boîte aux lettres :** Cette activité correspond à l’action d’audit de boîte aux lettres **HardDelete** . Cette opération est journalisée lorsqu’un utilisateur vide un élément du dossier Éléments récupérables. Les administrateurs peuvent utiliser l’outil Recherche de contenu dans le Centre de sécurité et de conformité pour rechercher et récupérer des éléments purgés jusqu’à ce que la période de rétention des éléments supprimés expire ou plus longtemps si la boîte aux lettres de l’utilisateur est en attente.

**Date de début** et **date de fin :** sélectionnez une plage de dates applicable à votre enquête.

**Utilisateurs:** Si vous sélectionnez un utilisateur dans ce champ, l’outil de recherche du journal d’audit retourne les enregistrements d’audit pour les éléments de courrier qui ont été supprimés (supprimés de manière réversible ou supprimés en dur) par l’utilisateur que vous spécifiez. Parfois, l’utilisateur qui supprime un e-mail peut ne pas être le propriétaire de la boîte aux lettres.

**Fichier, dossier ou site :** Laissez ce champ vide.

Après avoir exécuté la recherche, vous pouvez filtrer les résultats de la recherche pour afficher les enregistrements d’audit pour les éléments supprimés de manière réversible ou pour les éléments supprimés en dur. Sélectionnez l’enregistrement d’audit pour afficher la page de menu volant **Détails** , puis sélectionnez **Plus d’informations**. Des informations supplémentaires sur l’élément supprimé, telles que la ligne d’objet et l’emplacement de l’élément lors de sa suppression, sont affichées dans le champ **AffectedItems** . Les captures d’écran suivantes montrent un exemple de champ **AffectedItems** à partir d’un élément supprimé de manière réversible et d’un élément supprimé en dur.

**Exemple de champ AffectedItems pour l’élément supprimé de manière réversible**

![Enregistrement d’audit pour l’élément supprimé de manière réversible.](../media/softdeleteditem.png)

**Exemple de champ AffectedItems pour l’élément supprimé en dur**

![Enregistrement d’audit pour l’élément de courrier supprimé en dur.](../media/harddeleteditem.png)

### <a name="recover-deleted-email-items"></a>Récupérer les éléments de courrier supprimés

Les utilisateurs peuvent récupérer des éléments supprimés de manière réversible si la période de rétention des éléments supprimés n’a pas expiré. Dans Exchange Online, la période de rétention des éléments supprimés par défaut est de 14 jours, mais les administrateurs peuvent augmenter ce paramètre à un maximum de 30 jours. Pointez les utilisateurs vers [l’article Récupérer les éléments supprimés ou l’e-mail dans Outlook sur le web](https://support.office.com/article/Recover-deleted-items-or-email-in-Outlook-Web-App-C3D8FC15-EEEF-4F1C-81DF-E27964B7EDD4) article pour obtenir des instructions sur la récupération des éléments supprimés.

Comme expliqué précédemment, les administrateurs peuvent être en mesure de récupérer des éléments supprimés en dur si la période de rétention des éléments supprimés n’a pas expiré ou si la boîte aux lettres est en attente, auquel cas les éléments sont conservés jusqu’à ce que la durée de conservation expire. Lorsque vous exécutez une recherche de contenu, les éléments supprimés de manière réversible et supprimés en dur dans le dossier Éléments récupérables sont renvoyés dans les résultats de la recherche s’ils correspondent à la requête de recherche. Pour plus d’informations sur l’exécution de recherches de contenu, consultez [Recherche de contenu dans Office 365](content-search.md).

> [!TIP]
> Pour rechercher des éléments de courrier supprimés, recherchez tout ou partie de la ligne d’objet affichée dans le champ **AffectedItems** dans l’enregistrement d’audit.

## <a name="determine-if-a-user-created-an-inbox-rule"></a>Déterminer si un utilisateur a créé une règle de boîte de réception

Lorsque les utilisateurs créent une règle de boîte de réception pour leur boîte aux lettres Exchange Online, un enregistrement d’audit correspondant est enregistré dans le journal d’audit. Pour plus d’informations sur les règles de boîte de réception, consultez :

- [Utiliser des règles de boîte de réception dans Outlook sur le web](https://support.office.com/article/use-inbox-rules-in-outlook-on-the-web-8400435c-f14e-4272-9004-1548bb1848f2)
- [Gérer les messages électroniques dans Outlook à l’aide de règles](https://support.office.com/article/Manage-email-messages-by-using-rules-C24F5DEA-9465-4DF4-AD17-A50704D66C59)

Voici comment configurer une requête de recherche dans le journal d’audit pour ce scénario :

**Activités:** Sous **activités de boîte aux lettres Exchange**, sélectionnez une ou les deux activités suivantes :

- **New-InboxRule Créez une règle de boîte de réception à partir d’Outlook Web App**. Cette activité retourne des enregistrements d’audit lorsque des règles de boîte de réception sont créées à l’aide d’une application web Outlook ou Exchange Online PowerShell.

- **Mise à jour des règles de boîte de réception à partir du client Outlook**. Cette activité retourne des enregistrements d’audit lorsque des règles de boîte de réception sont créées, modifiées ou supprimées à l’aide du client de bureau Outlook.

**Date de début** et **date de fin :** sélectionnez une plage de dates applicable à votre enquête.

**Utilisateurs:** Sauf si vous examinez un utilisateur spécifique, laissez ce champ vide. Cela vous permet d’identifier les nouvelles règles de boîte de réception configurées par n’importe quel utilisateur.

**Fichier, dossier ou site :** Laissez ce champ vide.

Après avoir exécuté la recherche, tous les enregistrements d’audit de cette activité sont affichés dans les résultats de la recherche. Sélectionnez un enregistrement d’audit pour afficher la page de menu volant **Détails** , puis sélectionnez **Plus d’informations**. Des informations sur les paramètres de règle de boîte de réception sont affichées dans le champ **Paramètres** . La capture d’écran et les descriptions suivantes mettent en évidence les informations sur les règles de boîte de réception.

![Enregistrement d’audit pour la nouvelle règle de boîte de réception.](../media/NewInboxRuleRecord.png)

a. Dans le champ **ObjectId** , le nom complet de la règle de boîte de réception s’affiche. Ce nom inclut l’alias de la boîte aux lettres de l’utilisateur (par exemple, SaraD) et le nom de la règle de boîte de réception (par exemple, « Déplacer les messages de l’administrateur »).

b. Dans le champ **Paramètres** , la condition de la règle de boîte de réception s’affiche. Dans cet exemple, la condition est spécifiée par le paramètre *From* . La valeur définie pour le paramètre *From* indique que la règle de boîte de réception agit sur les e-mails envoyés par admin@alpinehouse.onmicrosoft.com. Pour obtenir la liste complète des paramètres qui peuvent être utilisés pour définir les conditions des règles de boîte de réception, consultez l’article [New-InboxRule](/powershell/module/exchange/new-inboxrule) .

c. Le paramètre *MoveToFolder* spécifie l’action de la règle de boîte de réception. Dans cet exemple, les messages reçus de admin@alpinehouse.onmicrosoft.com sont déplacés vers le dossier nommé *AdminSearch*. Consultez également l’article [New-InboxRule](/powershell/module/exchange/new-inboxrule) pour obtenir la liste complète des paramètres qui peuvent être utilisés pour définir l’action d’une règle de boîte de réception.

d. Le champ **UserId** indique l’utilisateur qui a créé la règle de boîte de réception spécifiée dans le champ **ObjectId** . Cet utilisateur s’affiche également dans la colonne **Utilisateur** de la page des résultats de la recherche.

## <a name="investigate-why-there-was-a-successful-login-by-a-user-outside-your-organization"></a>Examiner la raison pour laquelle un utilisateur externe à votre organisation a réussi à se connecter

Lorsque vous examinez les enregistrements d’audit dans le journal d’audit, vous pouvez voir des enregistrements qui indiquent qu’un utilisateur externe a été authentifié par Azure Active Directory et s’est connecté avec succès à votre organisation. Par exemple, un administrateur dans contoso.onmicrosoft.com peut voir un enregistrement d’audit indiquant qu’un utilisateur d’une autre organisation (par exemple, fabrikam.onmicrosoft.com) s’est connecté avec succès à contoso.onmicrosoft.com. De même, vous pouvez voir des enregistrements d’audit qui indiquent que les utilisateurs disposant d’un compte Microsoft (MSA), comme un Outlook.com ou Live.com, se sont connectés avec succès à votre organisation. Dans ces situations, l’activité auditée est **connectée par l’utilisateur**. 

Ce comportement est inhérent au produit. Azure Active Directory (Azure AD), le service d’annuaire, autorise une *authentification directe* lorsqu’un utilisateur externe tente d’accéder à un site SharePoint ou à un emplacement OneDrive dans votre organisation. Lorsque l’utilisateur externe tente de le faire, il est invité à entrer ses informations d’identification. Azure AD utilise les informations d’identification pour authentifier l’utilisateur, ce qui signifie que seul Azure AD vérifie que l’utilisateur est celui qu’il prétend être. L’indication de la connexion réussie dans l’enregistrement d’audit est le résultat de l’authentification de l’utilisateur par Azure AD. La connexion réussie ne signifie pas que l’utilisateur a pu accéder à des ressources ou effectuer d’autres actions dans votre organisation. Il indique uniquement que l’utilisateur a été authentifié par Azure AD. Pour qu’un utilisateur direct accède aux ressources SharePoint ou OneDrive, un utilisateur de votre organisation doit partager explicitement une ressource avec l’utilisateur externe en lui envoyant une invitation de partage ou un lien de partage anonyme. 

> [!NOTE]
> Azure AD autorise l’authentification directe uniquement pour les *applications tierces*, telles que SharePoint Online et OneDrive Entreprise. Elle n’est pas autorisée pour les autres applications tierces.

Voici un exemple et des descriptions des propriétés pertinentes dans un enregistrement d’audit pour un utilisateur **connecté à** un événement résultant de l’authentification directe. Sélectionnez l’enregistrement d’audit pour afficher la page de menu volant **Détails** , puis sélectionnez **Plus d’informations**.

![Exemple d’enregistrement d’audit pour une authentification directe réussie.](../media/PassThroughAuth1.png)

   a. Ce champ indique que l’utilisateur qui a tenté d’accéder à une ressource de votre organisation est introuvable dans Azure AD de votre organisation.

   b. Ce champ affiche l’UPN de l’utilisateur externe qui a tenté d’accéder à une ressource dans votre organisation. Cet ID d’utilisateur est également identifié dans les propriétés **User** et **UserId** de l’enregistrement d’audit.

   c. La propriété **ApplicationId** identifie l’application qui a déclenché la demande d’ouverture de session. La valeur de 00000003-0000-0ff1-ce00-0000000000 affichée dans la propriété ApplicationId dans cet enregistrement d’audit indique SharePoint Online. OneDrive Entreprise a également ce même ApplicationId.

   d. Cela indique que l’authentification directe a réussi. En d’autres termes, l’utilisateur a été authentifié avec succès par Azure AD. 

   e. La valeur **RecordType** de **15** indique que l’activité auditée (UserLoggedIn) est un événement d’ouverture de session STS (Secure Token Service) dans Azure AD.

Pour plus d’informations sur les autres propriétés affichées dans un enregistrement d’audit UserLoggedIn, consultez les informations de schéma liées à Azure AD dans [Office 365 schéma de l’API Activité de gestion](/office/office-365-management-api/office-365-management-activity-api-schema#azure-active-directory-base-schema).

Voici deux exemples de scénarios qui aboutiraient à une activité d’audit **correctement enregistrée par l’utilisateur en** raison de l’authentification directe : 

  - Un utilisateur disposant d’un compte Microsoft (tel que SaraD@outlook.com) a essayé d’accéder à un document dans un compte OneDrive Entreprise dans fourthcoffee.onmicrosoft.com et il n’existe pas de compte d’utilisateur invité correspondant pour SaraD@outlook.com dans fourthcoffee.onmicrosoft.com.

  - Un utilisateur disposant d’un compte professionnel ou scolaire dans une organisation (par exemple, pilarp@fabrikam.onmicrosoft.com) a essayé d’accéder à un site SharePoint dans contoso.onmicrosoft.com et il n’existe pas de compte d’utilisateur invité correspondant pour pilarp@fabrikam.com dans contoso.onmicrosoft.com.

### <a name="tips-for-investigating-successful-logins-resulting-from-pass-through-authentication"></a>Conseils pour examiner les connexions réussies résultant de l’authentification directe

- Recherchez dans le journal d’audit les activités effectuées par l’utilisateur externe identifié dans **l’enregistrement d’audit connecté par l’utilisateur** . Tapez l’UPN de l’utilisateur externe dans la zone **Utilisateurs** et utilisez une plage de dates si pertinente pour votre scénario. Par exemple, vous pouvez créer une recherche à l’aide des critères de recherche suivants :

   ![Recherchez toutes les activités effectuées par l’utilisateur externe.](../media/PassThroughAuth2.png)

    Outre les activités **connectées par l’utilisateur** , d’autres enregistrements d’audit peuvent être retournés, tels que ceux qui indiquent qu’un utilisateur de votre organisation a partagé des ressources avec l’utilisateur externe et si l’utilisateur externe a accédé, modifié ou téléchargé un document qui a été partagé avec lui.

- Recherchez les activités de partage SharePoint qui indiquent qu’un fichier a été partagé avec l’utilisateur externe identifié par un **utilisateur connecté à** l’enregistrement d’audit. Pour plus d’informations, voir [Utiliser l’audit du partage dans le journal d’audit](use-sharing-auditing.md).

- Exportez les résultats de la recherche dans le journal d’audit qui contiennent des enregistrements pertinents pour votre investigation afin que vous puissiez utiliser Excel pour rechercher d’autres activités liées à l’utilisateur externe. Pour plus d’informations, consultez  [Exporter, configurer et afficher les enregistrements du journal d’audit](export-view-audit-log-records.md).

## <a name="search-for-mailbox-activities-performed-by-users-with-non-e5-licenses"></a>Rechercher les activités de boîte aux lettres effectuées par les utilisateurs disposant de licences non E5

Même lorsque [l’audit de boîte aux lettres activé par défaut](enable-mailbox-auditing.md) est activé pour votre organisation, vous pouvez remarquer que les événements d’audit de boîte aux lettres pour certains utilisateurs sont introuvables dans les recherches dans les journaux d’audit à l’aide du Centre de conformité, de l’applet de commande **Search-UnifiedAuditLog** ou de l’API d’activité de gestion Office 365. La raison en est que les événements d’audit de boîte aux lettres sont retournés uniquement pour les utilisateurs disposant de licences E5 lorsque vous avez l’une des méthodes précédentes pour rechercher dans le journal d’audit unifié.

Pour récupérer les enregistrements du journal d’audit de boîte aux lettres pour les utilisateurs non-E5, vous pouvez effectuer l’une des solutions de contournement suivantes :

- Activez manuellement l’audit de boîte aux lettres sur des boîtes aux lettres individuelles (exécutez la `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true` commande dans Exchange Online PowerShell). Après cela, recherchez les activités d’audit de boîte aux lettres à l’aide du Centre de conformité, de l’applet de commande **Search-UnifiedAuditLog** ou de l’API d’activité de gestion Office 365.
  
  > [!NOTE]
  > Si l’audit de boîte aux lettres semble déjà être activé sur la boîte aux lettres, mais que vos recherches ne retournent aucun résultat, remplacez la valeur du paramètre `$false` `$true`_AuditEnabled_ par .
  
- Utilisez les applets de commande suivantes dans Exchange Online PowerShell :

  - [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) pour rechercher des utilisateurs spécifiques dans le journal d’audit de boîte aux lettres.

  - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) pour rechercher des utilisateurs spécifiques dans le journal d’audit de boîte aux lettres et envoyer les résultats par e-mail aux destinataires spécifiés.

## <a name="search-for-mailbox-activities-performed-in-a-specific-mailbox-including-shared-mailboxes"></a>Rechercher les activités de boîte aux lettres effectuées dans une boîte aux lettres spécifique (y compris les boîtes aux lettres partagées)

Lorsque vous utilisez la liste déroulante **Utilisateurs** dans l’outil de recherche de journal d’audit dans le centre de conformité ou la commande **Search-UnifiedAuditLog -UserIds** dans Exchange Online PowerShell, vous pouvez rechercher les activités effectuées par un utilisateur spécifique. Pour les activités d’audit de boîte aux lettres, ce type de recherche recherche les activités effectuées par l’utilisateur spécifié. Cela ne garantit pas que toutes les activités effectuées dans la même boîte aux lettres sont retournées dans les résultats de la recherche. Par exemple, une recherche dans le journal d’audit ne retourne pas d’enregistrements d’audit pour les activités effectuées par un utilisateur délégué, car la recherche des activités de boîte aux lettres effectuées par un utilisateur spécifique ne retourne pas les activités effectuées par un utilisateur délégué qui a reçu des autorisations pour accéder à la boîte aux lettres d’un autre utilisateur. (Un utilisateur délégué est une personne qui a reçu l’autorisation SendAs, SendOnBehalf ou FullAccess pour la boîte aux lettres d’un autre utilisateur.)

En outre, l’utilisation de la liste déroulante **Utilisateur** dans l’outil de recherche du journal d’audit ou **search-unifiedAuditLog -UserIds** ne renvoie pas de résultats pour les activités effectuées dans une boîte aux lettres partagée.

Pour rechercher les activités effectuées dans une boîte aux lettres spécifique ou rechercher des activités effectuées dans une boîte aux lettres partagée, utilisez la syntaxe suivante lors de l’exécution de l’applet **de commande Search-UnifiedAuditLog** :

```powershell
Search-UnifiedAuditLog  -StartDate <date> -EndDate <date> -FreeText (Get-Mailbox <mailbox identity).ExchangeGuid
```

Par exemple, la commande suivante retourne des enregistrements d’audit pour les activités effectuées dans la boîte aux lettres partagée de l’équipe de conformité Contoso entre août 2020 et octobre 2020 :

```powershell
Search-UnifiedAuditLog  -StartDate 08/01/2020 -EndDate 10/31/2020 -FreeText (Get-Mailbox complianceteam@contoso.onmicrosoft.com).ExchangeGuid
```

Vous pouvez également utiliser l’applet de commande **Search-MailboxAuditLog** pour rechercher des enregistrements d’audit pour l’activité effectuée dans une boîte aux lettres spécifique. Cela inclut la recherche d’activités effectuées dans une boîte aux lettres partagée.

L’exemple suivant retourne les enregistrements du journal d’audit de boîte aux lettres pour les activités effectuées dans la boîte aux lettres partagée de l’équipe de conformité Contoso :

```powershell
Search-MailboxAuditLog -Identity complianceteam@contoso.onmicrosoft.com -StartDate 08/01/2020 -EndDate 10/31/2020 -ShowDetails
```

L’exemple suivant retourne les enregistrements du journal d’audit de boîte aux lettres pour les activités effectuées dans la boîte aux lettres spécifiée par les utilisateurs délégués :

```powershell
Search-MailboxAuditLog -Identity <mailbox identity> -StartDate <date> -EndDate <date> -LogonTypes Delegate -ShowDetails
```

Vous pouvez également utiliser l’applet de commande **New-MailboxAuditLogSearch** pour rechercher une boîte aux lettres spécifique dans le journal d’audit et envoyer les résultats par e-mail aux destinataires spécifiés.