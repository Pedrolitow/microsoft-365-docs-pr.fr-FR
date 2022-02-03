---
title: Effectuer des recherches dans le journal d’audit pour résoudre les problèmes courants
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Découvrez comment utiliser l’outil Microsoft 365 de recherche dans le journal d’audit pour résoudre les problèmes de support courants pour les comptes de messagerie.
ms.openlocfilehash: 496729c7955448519d6cb1447e08b5a4b15aa655
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2022
ms.locfileid: "62321986"
---
# <a name="search-the-audit-log-to-investigate-common-support-issues"></a>Effectuer une recherche dans le journal d’audit pour examiner les problèmes de support courants

Cet article explique comment utiliser l’outil de recherche du journal d’audit pour vous aider à examiner les problèmes de support courants. Cela inclut l’utilisation du journal d’audit pour :

- Rechercher l’adresse IP de l’ordinateur utilisé pour accéder à un compte compromis
- Déterminer qui a installé le forwarding de courrier pour une boîte aux lettres
- Déterminer si un utilisateur a supprimé des éléments de courrier dans sa boîte aux lettres
- Déterminer si un utilisateur a créé une règle de boîte de réception
- Examiner pourquoi un utilisateur extérieur à votre organisation a réussi à se connecter
- Rechercher les activités de boîte aux lettres effectuées par les utilisateurs avec des licences non E5
- Rechercher les activités de boîte aux lettres effectuées par des utilisateurs délégués

## <a name="using-the-audit-log-search-tool"></a>Utilisation de l’outil de recherche du journal d’audit

Chacun des scénarios de dépannage décrits dans cet article est basé sur l’utilisation de l’outil de recherche du journal d’audit dans le Centre de conformité Microsoft 365. Cette section répertorie les autorisations requises pour effectuer des recherches dans le journal d’audit et décrit les étapes d’accès et d’exécuter les recherches dans le journal d’audit. Chaque section de scénario explique comment configurer une requête de recherche dans le journal d’audit et ce qu’il faut rechercher dans les informations détaillées des enregistrements d’audit qui correspondent aux critères de recherche.

### <a name="permissions-required-to-use-the-audit-log-search-tool"></a>Autorisations requises pour utiliser l’outil de recherche du journal d’audit

Le rôle Journaux View-Only audit ou Journaux d’audit doit vous être attribué dans Exchange Online pour effectuer des recherches dans le journal d’audit. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page **Autorisations** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. Les administrateurs globaux dans votre client Office 365 et Microsoft 365 sont automatiquement des membres du groupe de rôle Gestion de l'organisation dans Exchange Online. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](/Exchange/permissions-exo/role-groups).

### <a name="running-audit-log-searches"></a>Exécution de recherches dans le journal d’audit

Cette section décrit les bases de la création et de l’exécution de recherches dans le journal d’audit. Utilisez ces instructions comme point de départ pour chaque scénario de résolution des problèmes de cet article. Pour obtenir des instructions détaillées détaillées, consultez [la recherche dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md#step-1-run-an-audit-log-search).

1. Allez sur <https://compliance.microsoft.com/auditlogsearch> et connectez-vous à l’aide de votre compte professionnel ou scolaire.
  
    La page **Audit** s’affiche.
  
    ![Configurez les critères, puis sélectionnez Rechercher pour exécuter la recherche.](../media/AuditLogSearchPage1.png)
  
2. Vous pouvez configurer les critères de recherche suivants. Chaque scénario de résolution des problèmes décrit dans cet article recommande des instructions spécifiques pour la configuration de ces champs.
  
   a. **Date de début** et **date de fin : sélectionnez** une plage de dates et d’heures pour afficher les événements qui se sont produits au cours de cette période. Les sept derniers jours sont sélectionnés par défaut. Les date et heure sont présentées au format UTC (temps universel coordonné). La plage de dates maximale que vous pouvez spécifier est de 90 jours.

   b. **Activités :** Sélectionnez la liste de listes pour afficher les activités que vous pouvez rechercher. Une fois la recherche terminée, seuls les enregistrements d’audit correspondant aux activités sélectionnées apparaissent. La sélection **Afficher les résultats pour toutes les activités** affiche les résultats de toutes les activités qui répondent aux autres critères de recherche. Vous devez également laisser ce champ vide dans certains scénarios de dépannage.
  
    c. **Utilisateurs :** Cliquez dans cette zone, puis sélectionnez un ou plusieurs utilisateurs pour afficher les résultats de la recherche. Les enregistrements d’audit pour l’activité sélectionnée effectuée par les utilisateurs que vous sélectionnez dans cette zone sont affichés dans la liste des résultats. Laissez cette zone vide pour renvoyer les entrées pour tous les utilisateurs (et les comptes de service) dans votre organisation.
  
    d. **Fichier, dossier ou site :** Tapez tout ou partie d’un nom de fichier ou de dossier pour rechercher l’activité liée au fichier de dossier qui contient le mot clé spécifié. Vous pouvez également spécifier l’URL d’un fichier ou d’un dossier. Si vous utilisez une URL, assurez-vous que vous tapez le chemin d’accès complet de l’URL ou si vous tapez uniquement une partie de l’URL, n’incluez pas de caractères ou d’espaces spéciaux. Laissez cette zone vide pour renvoyer les entrées correspondant à tous les fichiers et dossiers dans votre organisation. Ce champ est laissé vide dans tous les scénarios de dépannage de cet article.
  
3. **Sélectionnez Rechercher** pour exécuter la recherche à l’aide de vos critères de recherche.
  
    Les résultats de la recherche sont chargés et, après quelques instants, ils sont affichés sur une page de l’outil de recherche du journal d’audit. Chacune des sections de cet article fournit des conseils sur les éléments à rechercher dans le contexte du scénario de dépannage spécifique.

    Pour plus d’informations sur l’affichage et l’exportation des résultats de recherche dans le journal d’audit, voir :

    - [Afficher les résultats de la recherche](search-the-audit-log-in-security-and-compliance.md#step-2-view-the-search-results)
  
    - [Exporter les résultats de la recherche](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file)

## <a name="find-the-ip-address-of-the-computer-used-to-access-a-compromised-account"></a>Rechercher l’adresse IP de l’ordinateur utilisé pour accéder à un compte compromis

L’adresse IP correspondant à une activité effectuée par n’importe quel utilisateur est incluse dans la plupart des enregistrements d’audit. Les informations sur le client utilisé sont également incluses dans l’enregistrement d’audit.

Voici comment configurer une requête de recherche de journal d’audit pour ce scénario :

**Activités :** Si cela est pertinent pour votre cas, sélectionnez une activité spécifique à rechercher. Pour résoudre les problèmes de comptes compromis, songez à sélectionner l’utilisateur qui s’est inscrit à l’activité de boîte aux lettres **Exchange activités de boîte aux lettres**. Cela renvoie les enregistrements d’audit montrant l’adresse IP qui a été utilisé lors de la signature à la boîte aux lettres. Dans le cas contraire, laissez ce champ vide pour renvoyer les enregistrements d’audit pour toutes les activités. 

> [!TIP]
> Laisser ce champ vide retourne les activités **UserLoggedIn**, qui est une activité Azure Active Directory qui indique qu’une personne s’est connectée à un compte d’utilisateur. Utilisez le filtrage dans les résultats de recherche pour afficher les enregistrements d’audit **UserLoggedIn** .

**Date de début** **et de fin : sélectionnez** une plage de dates applicable à votre enquête.

**Utilisateurs :** Si vous examinez un compte compromis, sélectionnez l’utilisateur dont le compte a été compromis. Cette action renvoie des enregistrements d’audit pour les activités effectuées par ce compte d’utilisateur.

**Fichier, dossier ou site :** Laissez ce champ vide.

Après avoir exécuté la recherche, l’adresse IP de chaque activité s’affiche dans la colonne d’adresse **IP** dans les résultats de la recherche. Sélectionnez l’enregistrement dans les résultats de la recherche pour afficher des informations plus détaillées sur la page volante.

## <a name="determine-who-set-up-email-forwarding-for-a-mailbox"></a>Déterminer qui a installé le forwarding de courrier pour une boîte aux lettres

Lorsque le forwarding de courrier est configuré pour une boîte aux lettres, les messages électroniques envoyés à la boîte aux lettres sont transmis à une autre boîte aux lettres. Les messages peuvent être transmis à des utilisateurs à l’intérieur ou à l’extérieur de votre organisation. Lorsque le forwarding de courrier est installé sur une boîte aux lettres, la cmdlet Exchange Online **sous-jacente utilisée est Set-Mailbox**.

Voici comment configurer une requête de recherche de journal d’audit pour ce scénario :

**Activités :** Laissez ce champ vide afin que la recherche renvoie des enregistrements d’audit pour toutes les activités. Cette étape est nécessaire pour retourner les enregistrements d’audit liés à la cmdlet **Set-Mailbox** .

**Date de début** **et de fin : sélectionnez** une plage de dates applicable à votre enquête.

**Utilisateurs :** À moins que vous n’enquêtiez sur un problème de forwarding de courrier électronique pour un utilisateur spécifique, laissez ce champ vide. Cela vous permet d’identifier si le forwarding de courrier a été mis en place pour un utilisateur.

**Fichier, dossier ou site :** Laissez ce champ vide.

Après avoir exécuté la recherche, sélectionnez **Filtrer les résultats** sur la page des résultats de la recherche. Dans la zone sous  l’en-tête de colonne Activité, tapez **Set-Mailbox** afin que seuls les enregistrements d’audit liés à la cmdlet **Set-Mailbox** soient affichés.

![Filtrage des résultats d’une recherche dans le journal d’audit.](../media/emailforwarding1.png)

À ce stade, vous devez examiner les détails de chaque enregistrement d’audit pour déterminer si l’activité est liée au forwarding de courrier. Sélectionnez l’enregistrement d’audit pour afficher la page **de présentation des détails** , puis sélectionnez **Plus d’informations**. La capture d’écran et les descriptions suivantes mettent en évidence les informations qui indiquent que le forwarding de courrier a été définie sur la boîte aux lettres.

![Informations détaillées de l’enregistrement d’audit.](../media/emailforwarding2.png)

a. Dans le **champ ObjectId** , l’alias de la boîte aux lettres sur qui a été définie le forwarding de courrier s’affiche. Cette boîte aux lettres s’affiche également dans la colonne **Élément** de la page des résultats de la recherche.

b. Dans le **champ Paramètres** , la valeur *ForwardingSmtpAddress* indique que le forwarding de courrier électronique a été définie sur la boîte aux lettres. Dans cet exemple, le courrier est transmis à l’adresse mike@contoso.com, qui se trouve en dehors de l’alpinehouse.onmicrosoft.com organisation.

c. La valeur *True* pour le paramètre *DeliverToMailboxAndForward* indique qu’une copie du message est remis à sarad@alpinehouse.onmicrosoft.com et est transmis à l’adresse de messagerie spécifiée par le paramètre *ForwardingSmtpAddress*, qui dans cet exemple est mike@contoso.com. Si la valeur du paramètre *DeliverToMailboxAndForward* est définie sur *False*, le courrier électronique est uniquement transmis à l’adresse spécifiée par le paramètre *ForwardingSmtpAddress* . Il n’est pas remis à la boîte aux lettres spécifiée dans le **champ ObjectId** .

d. Le **champ UserId** indique l’utilisateur qui a définie le forwarding de courrier sur la boîte aux lettres spécifiée dans le **champ ObjectId** . Cet utilisateur est également affiché dans la colonne **Utilisateur** sur la page des résultats de la recherche. Dans ce cas, il semble que le propriétaire de la boîte aux lettres définisse le forwarding de courrier sur sa boîte aux lettres.

Si vous déterminez que le forwarding de courrier ne doit pas être définie sur la boîte aux lettres, vous pouvez le supprimer en exécutant la commande suivante dans Exchange Online PowerShell :

```powershell
Set-Mailbox <mailbox alias> -ForwardingSmtpAddress $null 
```

Pour plus d’informations sur les paramètres liés au forwarding de courrier, consultez l’article [Set-Mailbox](/powershell/module/exchange/set-mailbox) .

## <a name="determine-if-a-user-deleted-email-items"></a>Déterminer si un utilisateur a supprimé des éléments de courrier

À compter de janvier 2019, Microsoft démarre l’enregistrement d’audit des boîtes aux lettres par défaut pour toutes les Office 365 et les organisations Microsoft. Cela signifie que certaines actions effectuées par les propriétaires de boîtes aux lettres sont enregistrées automatiquement et que les enregistrements d’audit de boîte aux lettres correspondants sont disponibles lorsque vous les recherchez dans le journal d’audit de la boîte aux lettres. Avant que l’audit de boîte aux lettres ne soit activé par défaut, vous deviez l’activer manuellement pour chaque boîte aux lettres utilisateur de votre organisation. 

Les actions de boîte aux lettres consignées par défaut incluent les actions de boîte aux lettres SoftDelete et HardDelete effectuées par les propriétaires de boîtes aux lettres. Cela signifie que vous pouvez utiliser les étapes suivantes pour rechercher dans le journal d’audit les événements liés aux éléments de courrier supprimés. Pour plus d’informations sur l’audit de boîte aux lettres par défaut, voir [Gérer l’audit de boîte aux lettres](enable-mailbox-auditing.md).

Voici comment configurer une requête de recherche de journal d’audit pour ce scénario :

**Activités :** Sous **Exchange activités de boîte aux lettres**, sélectionnez l’une des activités suivantes ou les deux :

- **Messages supprimés du dossier Éléments supprimés :** Cette activité correspond à l’action d’audit de boîte aux lettres **SoftDelete** . Cette activité est également enregistrée lorsqu’un utilisateur supprime définitivement un élément en le sélectionnant et en appuyant sur **Shift+Supprim.** Une fois qu’un élément est supprimé définitivement, l’utilisateur peut le récupérer jusqu’à l’expiration de la période de rétention des éléments supprimés.

- **Messages purgés de la boîte aux lettres :** Cette activité correspond à l’action d’audit de boîte aux lettres **HardDelete** . Cette information est consignée lorsqu’un utilisateur purge un élément du dossier Éléments récupérables. Les administrateurs peuvent utiliser l’outil de recherche de contenu dans le centre de sécurité et conformité pour rechercher et récupérer des éléments purgés jusqu’à ce que la période de rétention des éléments supprimés expire ou plus longtemps si la boîte aux lettres de l’utilisateur est en conservation.

**Date de début** **et de fin : sélectionnez** une plage de dates applicable à votre enquête.

**Utilisateurs :** Si vous sélectionnez un utilisateur dans ce champ, l’outil de recherche du journal d’audit renvoie les enregistrements d’audit pour les éléments de courrier supprimés (SoftDeleted ou HardDeleted) par l’utilisateur que vous spécifiez. Parfois, l’utilisateur qui supprime un message électronique n’est peut-être pas le propriétaire de la boîte aux lettres.

**Fichier, dossier ou site :** Laissez ce champ vide.

Après avoir exécuté la recherche, vous pouvez filtrer les résultats de la recherche afin d’afficher les enregistrements d’audit pour les éléments supprimés (supprimés(s) (supprimés(s) (logiciels) ou les éléments supprimés (supprimés définitivement). Sélectionnez l’enregistrement d’audit pour afficher la page **de présentation des détails** , puis sélectionnez **Plus d’informations**. Des informations supplémentaires sur l’élément supprimé, telles que la ligne d’objet et l’emplacement de l’élément lors de sa suppression, sont affichées dans le champ **AffectedItems** . Les captures d’écran suivantes illustrent un exemple du champ **AffectedItems** à partir d’un élément supprimé (supprimé de nouveau) et d’un élément supprimé (supprimé définitivement).

**Exemple de champ AffectedItems pour l’élément supprimé (supprimé de la demande)**

![Enregistrement d’audit pour l’élément supprimé (supprimé de nouveau).](../media/softdeleteditem.png)

**Exemple de champ AffectedItems pour l’élément supprimé définitivement**

![Enregistrement d’audit pour l’élément de courrier supprimé définitivement.](../media/harddeleteditem.png)

### <a name="recover-deleted-email-items"></a>Récupérer les éléments de courrier supprimés

Les utilisateurs peuvent récupérer des éléments supprimés (récupérables) si la période de rétention des éléments supprimés n’a pas expiré. Dans Exchange Online, la période de rétention des éléments supprimés par défaut est de 14 jours, mais les administrateurs peuvent augmenter ce paramètre jusqu’à un maximum de 30 jours. Pointez les utilisateurs vers le courrier électronique ou les éléments supprimés dans [Outlook sur le web’article](https://support.office.com/article/Recover-deleted-items-or-email-in-Outlook-Web-App-C3D8FC15-EEEF-4F1C-81DF-E27964B7EDD4) pour obtenir des instructions sur la récupération des éléments supprimés.

Comme indiqué précédemment, les administrateurs peuvent récupérer des éléments supprimés définitivement si la période de rétention des éléments supprimés n’a pas expiré ou si la boîte aux lettres est en conservation, auquel cas les éléments sont conservés jusqu’à l’expiration de la durée de la conservation. Lorsque vous exécutez une recherche de contenu, les éléments supprimés (récupérables) et supprimés (récupérables) dans le dossier Éléments récupérables sont renvoyés dans les résultats de recherche s’ils correspondent à la requête de recherche. Pour plus d’informations sur l’exécution de recherches de contenu, voir [Recherche de contenu dans Office 365](content-search.md).

> [!TIP]
> Pour rechercher des éléments de courrier supprimés, recherchez tout ou partie de la ligne d’objet affichée dans le champ **AffectedItems** de l’enregistrement d’audit.

## <a name="determine-if-a-user-created-an-inbox-rule"></a>Déterminer si un utilisateur a créé une règle de boîte de réception

Lorsque les utilisateurs créent une règle de boîte de réception pour Exchange Online boîte aux lettres, un enregistrement d’audit correspondant est enregistré dans le journal d’audit. Pour plus d’informations sur les règles de boîte de réception, voir :

- [Utiliser des règles de boîte de réception dans Outlook sur le web](https://support.office.com/article/use-inbox-rules-in-outlook-on-the-web-8400435c-f14e-4272-9004-1548bb1848f2)
- [Gérer les messages électroniques dans Outlook à l’aide de règles](https://support.office.com/article/Manage-email-messages-by-using-rules-C24F5DEA-9465-4DF4-AD17-A50704D66C59)

Voici comment configurer une requête de recherche de journal d’audit pour ce scénario :

**Activités :** Sous **Exchange activités de boîte aux lettres**, sélectionnez l’une des activités suivantes ou les deux :

- **New-InboxRule Créer une règle de boîte de réception à partir Outlook Web App**. Cette activité renvoie des enregistrements d’audit lorsque des règles de boîte de réception sont créées à l’aide Outlook application web ou Exchange Online PowerShell.

- **Règles de boîte de réception mises à jour Outlook client.** Cette activité renvoie des enregistrements d’audit lorsque des règles de boîte de réception sont créées, modifiées ou supprimées à l’aide Outlook client de bureau.

**Date de début** **et de fin : sélectionnez** une plage de dates applicable à votre enquête.

**Utilisateurs :** À moins que vous n’enquêtiez sur un utilisateur spécifique, laissez ce champ vide. Cela vous permet d’identifier les nouvelles règles de boîte de réception définies par n’importe quel utilisateur.

**Fichier, dossier ou site :** Laissez ce champ vide.

Après avoir exécuté la recherche, tous les enregistrements d’audit pour cette activité sont affichés dans les résultats de la recherche. Sélectionnez un enregistrement d’audit pour afficher la page **de présentation des détails** , puis sélectionnez **Plus d’informations**. Les informations sur les paramètres de règle de boîte de réception sont **affichées dans le champ Paramètres** . La capture d’écran et les descriptions suivantes mettent en évidence les informations sur les règles de boîte de réception.

![Enregistrement d’audit pour la nouvelle règle de boîte de réception.](../media/NewInboxRuleRecord.png)

a. Dans le **champ ObjectId** , le nom complet de la règle de boîte de réception s’affiche. Ce nom inclut l’alias de la boîte aux lettres de l’utilisateur (par exemple, SaraD) et le nom de la règle de boîte de réception (par exemple, « Déplacer des messages de l’administrateur »).

b. Dans le **champ Paramètres** , la condition de la règle de boîte de réception s’affiche. Dans cet exemple, la condition est spécifiée par le *paramètre From* . La valeur définie pour le *paramètre From* indique que la règle de boîte de réception agit sur les messages envoyés par admin@alpinehouse.onmicrosoft.com. Pour obtenir la liste complète des paramètres qui peuvent être utilisés pour définir les conditions des règles de boîte de réception, consultez l’article [New-InboxRule](/powershell/module/exchange/new-inboxrule) .

c. Le *paramètre MoveToFolder* spécifie l’action de la règle de boîte de réception. Dans cet exemple, les messages reçus de admin@alpinehouse.onmicrosoft.com sont déplacés vers le dossier *adminSearch*. Consultez également [l’article New-InboxRule](/powershell/module/exchange/new-inboxrule) pour obtenir la liste complète des paramètres qui peuvent être utilisés pour définir l’action d’une règle de boîte de réception.

d. Le **champ UserId** indique l’utilisateur qui a créé la règle de boîte de réception spécifiée dans le **champ ObjectId** . Cet utilisateur est également affiché dans la colonne **Utilisateur** sur la page des résultats de la recherche.

## <a name="investigate-why-there-was-a-successful-login-by-a-user-outside-your-organization"></a>Examiner pourquoi un utilisateur extérieur à votre organisation a réussi à se connecter

Lors de l’examen des enregistrements d’audit dans le journal d’audit, vous pouvez voir des enregistrements qui indiquent qu’un utilisateur externe a été authentifié par Azure Active Directory et connecté à votre organisation. Par exemple, un administrateur dans contoso.onmicrosoft.com peut voir un enregistrement d’audit indiquant qu’un utilisateur d’une autre organisation (par exemple, fabrikam.onmicrosoft.com) s’est connecté contoso.onmicrosoft.com. De même, vous pouvez voir des enregistrements d’audit qui indiquent que les utilisateurs  ayant un compte Microsoft (MSA), tels qu’un compte Outlook.com ou Live.com, se sont connectés avec succès à votre organisation. Dans ce cas, l’activité auditée est connectée **par l’utilisateur**. 

Ce comportement est inhérent au produit. Azure Active Directory (Azure AD), le service d’annuaire, autorise une authentification directe lorsqu’un utilisateur externe  tente d’accéder à un site SharePoint ou à un emplacement OneDrive dans votre organisation. Lorsque l’utilisateur externe tente de le faire, il est invité à entrer ses informations d’identification. Azure AD utilise les informations d’identification pour authentifier l’utilisateur, Azure AD vérifie que l’utilisateur est bien celui qu’il dit être. L’indication de la connexion réussie dans l’enregistrement d’audit est le résultat Azure AD authentifier l’utilisateur. La connexion réussie ne signifie pas que l’utilisateur a pu accéder à des ressources ou effectuer d’autres actions dans votre organisation. Il indique uniquement que l’utilisateur a été authentifié par Azure AD. Pour qu’un utilisateur pass-through accède aux ressources SharePoint ou OneDrive, un utilisateur de votre organisation doit explicitement partager une ressource avec l’utilisateur externe en lui envoyant une invitation de partage ou un lien de partage anonyme. 

> [!NOTE]
> Azure AD permet l’authentification directe uniquement pour les *applications* tierces, telles que SharePoint Online et OneDrive Entreprise. Elle n’est pas autorisée pour les autres applications tierces.

Voici un exemple et des descriptions des propriétés pertinentes dans un enregistrement d’audit pour un utilisateur connecté **dans** un événement résultant de l’authentification directe. Sélectionnez l’enregistrement d’audit pour afficher la page **de présentation des détails** , puis sélectionnez **Plus d’informations**.

![Exemple d’enregistrement d’audit pour l’authentification directe réussie.](../media/PassThroughAuth1.png)

   a. Ce champ indique que l’utilisateur qui a tenté d’accéder à une ressource de votre organisation n’a pas été trouvé dans l’Azure AD.

   b. Ce champ affiche l’UPN de l’utilisateur externe qui a tenté d’accéder à une ressource dans votre organisation. Cet ID d’utilisateur est également identifié dans les **propriétés User** **et UserId** de l’enregistrement d’audit.

   c. La **propriété ApplicationId** identifie l’application qui a déclenché la demande d’inscription. La valeur 00000003-0000-0ff1-ce00-0000000000000 affichée dans la propriété ApplicationId de cet enregistrement d’audit indique SharePoint Online. OneDrive Entreprise également le même ApplicationId.

   d. Cela indique que l’authentification directe a réussi. En d’autres termes, l’utilisateur a été authentifié par Azure AD. 

   e. La **valeur RecordType** de **15** indique que l’activité auditée (UserLoggedIn) est un événement de session du service STS (Secure Token Service) dans Azure AD.

Pour plus d’informations sur les autres propriétés affichées dans un enregistrement d’audit UserLoggedIn, voir les informations de schéma Azure AD dans le schéma de [l’API activité](/office/office-365-management-api/office-365-management-activity-api-schema#azure-active-directory-base-schema) de gestion Office 365.

Voici deux exemples de scénarios qui entraîneraient la réussite de l’activité **d’audit de** l’utilisateur connecté en raison de l’authentification directe : 

  - Un utilisateur avec un compte Microsoft (tel que SaraD@outlook.com) a tenté d’accéder à un document dans un compte OneDrive Entreprise dans fourthcoffee.onmicrosoft.com et il n’existe pas de compte d’utilisateur invité correspondant pour SaraD@outlook.com dans fourthcoffee.onmicrosoft.com.

  - Un utilisateur  ayant un compte scolaire ou de travail dans une organisation (tel que pilarp@fabrikam.onmicrosoft.com) a tenté d’accéder à un site SharePoint dans contoso.onmicrosoft.com et il n’existe pas de compte d’utilisateur invité correspondant pour pilarp@fabrikam.com dans contoso.onmicrosoft.com.

### <a name="tips-for-investigating-successful-logins-resulting-from-pass-through-authentication"></a>Astuces pour examiner les connexions réussies résultant de l’authentification directe

- Recherchez dans le journal d’audit les activités effectuées par l’utilisateur externe identifié dans l’enregistrement **d’audit connecté par l’utilisateur** . Tapez l’UPN de l’utilisateur  externe dans la zone Utilisateurs et utilisez une plage de dates si cela est pertinent pour votre scénario. Par exemple, vous pouvez créer une recherche à l’aide des critères de recherche suivants :

   ![Recherchez toutes les activités effectuées par l’utilisateur externe.](../media/PassThroughAuth2.png)

    Outre les activités de  l’utilisateur connecté, d’autres enregistrements d’audit peuvent être renvoyés, tels que ceux qui indiquent qu’un utilisateur de votre organisation a partagé des ressources avec l’utilisateur externe et si l’utilisateur externe a accédé, modifié ou téléchargé un document qui a été partagé avec lui.

- Recherchez SharePoint activités de partage qui indiquent qu’un fichier a été partagé avec l’utilisateur externe identifié par un enregistrement **d’audit connecté** par un utilisateur. Pour plus d’informations, voir [Utiliser l’audit du partage dans le journal d’audit](use-sharing-auditing.md).

- Exportez les résultats de recherche du journal d’audit qui contiennent des enregistrements pertinents pour votre enquête afin de pouvoir utiliser Excel pour rechercher d’autres activités liées à l’utilisateur externe. Pour plus d’informations,  [voir Exporter, configurer et afficher les enregistrements du journal d’audit](export-view-audit-log-records.md).

## <a name="search-for-mailbox-activities-performed-by-users-with-non-e5-licenses"></a>Rechercher les activités de boîte aux lettres effectuées par les utilisateurs avec des licences non E5

Même lorsque [l’audit](enable-mailbox-auditing.md) de boîte aux lettres est allumé par défaut pour votre organisation, vous remarquerez peut-être que les événements d’audit de boîte aux lettres pour certains utilisateurs ne sont pas trouvés dans les recherches du journal d’audit à l’aide du centre de conformité, de la cmdlet **Search-UnifiedAuditLog** ou de l’API activité de gestion Office 365. En effet, les événements d’audit de boîte aux lettres sont renvoyés uniquement pour les utilisateurs  titulaires d’une licence E5 lorsque vous recherchez l’une des méthodes précédentes dans le journal d’audit unifié.

Pour récupérer les enregistrements du journal d’audit des boîtes aux lettres pour les utilisateurs autres que E5, vous pouvez effectuer l’une des solutions de contournement suivantes :

- Activez manuellement l’audit des boîtes aux lettres sur des boîtes aux lettres individuelles (exécutez `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true` la commande dans Exchange Online PowerShell). Après cela, recherchez les activités d’audit de boîte aux lettres à l’aide du centre de conformité, de la cmdlet **Search-UnifiedAuditLog** ou de l’API activité Office 365 gestion des boîtes aux lettres.
  
  > [!NOTE]
  > Si l’audit de boîte aux lettres semble déjà être activé sur la boîte aux lettres, mais que vos recherches ne retournent aucun résultat, modifiez la valeur du paramètre _AuditEnabled_ `$false` `$true`de et revenir à .
  
- Utilisez les cmdlets suivantes dans Exchange Online PowerShell :

  - [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) pour rechercher des utilisateurs spécifiques dans le journal d’audit de la boîte aux lettres.

  - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) pour rechercher des utilisateurs spécifiques dans le journal d’audit de la boîte aux lettres et envoyer les résultats par courrier électronique à des destinataires spécifiés.

## <a name="search-for-mailbox-activities-performed-in-a-specific-mailbox-including-shared-mailboxes"></a>Rechercher les activités de boîte aux lettres effectuées dans une boîte aux lettres spécifique (y compris les boîtes aux lettres partagées)

Lorsque vous utilisez la  liste de listes d’utilisateurs dans l’outil de recherche du journal d’audit dans le centre de conformité ou la commande **Search-UnifiedAuditLog -UserIds** dans Exchange Online PowerShell, vous pouvez rechercher les activités effectuées par un utilisateur spécifique. Pour les activités d’audit de boîte aux lettres, ce type de recherche recherche les activités effectuées par l’utilisateur spécifié. Il ne garantit pas que toutes les activités effectuées dans la même boîte aux lettres sont renvoyées dans les résultats de la recherche. Par exemple, une recherche dans le journal d’audit ne retourne pas d’enregistrements d’audit pour les activités effectuées par un utilisateur délégué, car la recherche d’activités de boîte aux lettres effectuées par un utilisateur spécifique ne retourne pas les activités effectuées par un utilisateur délégué qui a reçu des autorisations pour accéder à la boîte aux lettres d’un autre utilisateur. (Un utilisateur délégué est une personne qui a reçu l’autorisation de boîte aux lettres SendAs, SendOnBehalf ou FullAccess sur la boîte aux lettres d’un autre utilisateur.)

En outre, l’utilisation de la liste de listes d’utilisateurs dans l’outil de recherche du journal d’audit ou de **Search-UnifiedAuditLog -UserIds** ne retourne pas de résultats pour les activités effectuées dans une boîte aux lettres partagée.

Pour rechercher les activités effectuées dans une boîte aux lettres spécifique ou pour rechercher des activités effectuées dans une boîte aux lettres partagée, utilisez la syntaxe suivante lors de l’exécution de la cmdlet **Search-UnifiedAuditLog** :

```powershell
Search-UnifiedAuditLog  -StartDate <date> -EndDate <date> -FreeText (Get-Mailbox <mailbox identity).ExchangeGuid
```

Par exemple, la commande suivante renvoie des enregistrements d’audit pour les activités effectuées dans la boîte aux lettres partagée de l’équipe de conformité Contoso entre août 2020 et octobre 2020 :

```powershell
Search-UnifiedAuditLog  -StartDate 08/01/2020 -EndDate 10/31/2020 -FreeText (Get-Mailbox complianceteam@contoso.onmicrosoft.com).ExchangeGuid
```

Vous pouvez également utiliser la cmdlet **Search-MailboxAuditLog** pour rechercher des enregistrements d’audit pour les activités effectuées dans une boîte aux lettres spécifique. Cela inclut la recherche d’activités effectuées dans une boîte aux lettres partagée.

L’exemple suivant renvoie les enregistrements du journal d’audit des boîtes aux lettres pour les activités effectuées dans la boîte aux lettres partagée de l’équipe de conformité Contoso :

```powershell
Search-MailboxAuditLog -Identity complianceteam@contoso.onmicrosoft.com -StartDate 08/01/2020 -EndDate 10/31/2020 -ShowDetails
```

L’exemple suivant renvoie les enregistrements du journal d’audit des boîtes aux lettres pour les activités effectuées dans la boîte aux lettres spécifiée par les utilisateurs délégués :

```powershell
Search-MailboxAuditLog -Identity <mailbox identity> -StartDate <date> -EndDate <date> -LogonTypes Delegate -ShowDetails
```

Vous pouvez également utiliser la cmdlet **New-MailboxAuditLogSearch** pour rechercher dans le journal d’audit une boîte aux lettres spécifique et envoyer les résultats par courrier électronique à des destinataires spécifiés.