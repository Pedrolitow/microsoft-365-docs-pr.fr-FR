---
title: Destruction de contenu
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Surveillez et gérez la destruction de contenu lorsque vous utilisez une révision avant destruction ou que des éléments marqués comme enregistrement sont automatiquement supprimés selon les paramètres que vous avez configurés.
ms.openlocfilehash: dbc713c665367bb973fb8faded24015ad6c2d5c3
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594815"
---
# <a name="disposition-of-content"></a>Destruction de contenu

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Utilisez la page **Destruction** de **Gestion des enregistrements** dans le Centre de conformité Microsoft 365 pour gérer les révisions de destruction et afficher les métadonnées des [enregistrements](records-management.md#records) qui ont été automatiquement supprimés à la fin de la période de rétention.

## <a name="prerequisites-for-viewing-content-dispositions"></a>Conditions préalables pour l’affichage des suppressions de contenu

Pour gérer les révisions de disposition et confirmer que les enregistrements ont été supprimés, vous devez disposer des autorisations suffisantes et l'audit doit être activé. Soyez également conscient des [limites](retention-limits.md#maximum-number-of-items-for-disposition) de disposition.

### <a name="permissions-for-disposition"></a>Autorisations pour la destruction

Pour accéder à l’onglet **Destruction** dans le Centre de conformité Microsoft 365, les utilisateurs doivent avoir le rôle de **Gestion des destructions**. A partir de décembre 2020, ce rôle est désormais inclus dans le groupe de rôle par défaut de **Gestion des enregistrements**.

> [!NOTE]
> Par défaut, un administrateur général ne se voit pas attribuer le rôle de **Gestion des destructions**. 

Pour accorder aux utilisateurs uniquement les autorisations dont ils ont besoin pour les révisions avant destruction sans leur permettre d'afficher et de configurer d'autres fonctionnalités pour la conservation et la gestion des documents, créez un groupe de rôles personnalisé (par exemple, appelé « Réviseurs avant destruction ») et attribuez à ce groupe le rôle de **Gestion des destructions**.

Pour obtenir des instructions pour ajouter des utilisateurs aux rôles par défaut ou créer vos propres groupes de rôles, consultez [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md).

En outre :

- Pour afficher le contenu des éléments pendant le processus de disposition, ajoutez des utilisateurs au groupe de rôles **Content Explorer Content Viewer**. Si les utilisateurs ne disposent pas des autorisations de ce groupe de rôles, ils peuvent toujours sélectionner une action de révision de la disposition pour terminer la révision de la disposition, mais doivent le faire sans pouvoir afficher le contenu de l'élément à partir du mini-volet d'aperçu du centre de conformité.

- Par défaut, chaque personne qui accède à la page **Disposition** ne voit que les éléments qu'elle est chargée de réviser. Pour qu'un administrateur de gestion des enregistrements puisse voir tous les éléments attribués à tous les utilisateurs et toutes les étiquettes de rétention qui sont configurées pour l'examen de disposition : accédez à **Paramètres de gestion des enregistrements** > **Disposition** pour sélectionner, puis activer un groupe de sécurité à extension messagerie qui contient le comptes administrateur.
    
    Les groupes de sécurité et les groupes Microsoft 365 qui ne sont pas à extension messagerie ne prennent pas en charge cette fonctionnalité et ne sont pas affichés dans la liste à sélectionner. Si vous devez créer un nouveau groupe de sécurité compatible avec la messagerie, utilisez le lien vers le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration de Microsoft 365</a> pour créer le nouveau groupe. 
    
    > [!IMPORTANT]
    > Après avoir activé le groupe, vous ne pouvez pas le modifier dans le Centre de conformité. Consultez la section suivante pour savoir comment activer un autre groupe à l’aide de PowerShell.

- L’**option paramètres de gestion des enregistrements** est visible uniquement pour les administrateurs de gestion des enregistrements. 

#### <a name="enabling-another-security-group-for-disposition"></a>Activation d’un autre groupe de sécurité pour sa disposition

Après avoir activé un groupe de sécurité pour la disposition à partir des **paramètres de gestion des enregistrements** dans le centre de conformité Microsoft 365, vous ne pouvez pas désactiver cette autorisation pour le groupe ou remplacer le groupe sélectionné dans le centre de conformité. Cependant, vous pouvez activer un autre groupe de sécurité à extension messagerie à l'aide de la cmdlet [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage).

Par exemple : 

```PowerShell
Enable-ComplianceTagStorage -RecordsManagementSecurityGroupEmail dispositionreviewers@contosoi.com
````

### <a name="enable-auditing"></a>Activer l’audit

Assurez-vous que l’audit est activé au moins un jour avant la première action de destruction. Pour plus d’informations, consultez [Rechercher dans le journal d’audit dans le centre de conformité](search-the-audit-log-in-security-and-compliance.md). 

## <a name="disposition-reviews"></a>Révisions avant destruction

Lorsque le contenu atteint la fin de la période de rétention, vous souhaiterez peut-être réviser ce contenu et confirmer s’il peut être supprimé définitivement (« supprimé »). Par exemple, au lieu de supprimer le contenu, vous devrez peut-être :
  
- Suspendre la destruction de contenu pertinent pour un litige ou un audit.

- Affecter une période de rétention différente au contenu, peut-être parce que les paramètres de rétention d’origine étaient une solution temporaire ou provisoire.

- Déplacez le contenu de son emplacement existant vers un emplacement d’archivage, par exemple, si ce contenu a des valeurs d’historique ou de recherche.

Lorsqu'une révision de disposition est déclenchée à la fin de la période de conservation, les réviseurs que vous choisissez reçoivent une notification par e-mail indiquant qu'ils ont du contenu à réviser. Ces réviseurs peuvent être des utilisateurs individuels ou des groupes de sécurité à extension messagerie.

Vous pouvez personnaliser l’e-mail qu’ils reçoivent, notamment les instructions dans d’autres langues. Pour un support multilingue, vous devez vous-même spécifier les traductions et ce texte personnalisé s’affiche pour tous les réviseurs indépendamment de leurs paramètres régionaux.

Les utilisateurs reçoivent une notification par e-mail initiale par étiquette à la fin de la période de rétention de l’élément, avec un rappel par étiquette une fois par semaine de toutes les révisions avant destruction qui leur sont affectées. Ils peuvent cliquer sur le lien dans les e-mails de notification et de rappel pour accéder directement à la page de **Gestion des enregistrements** > **Disposition** dans le Centre de conformité Microsoft 365 pour examiner le contenu et effectuer une action. Les réviseurs peuvent également accéder à cette page **Disposition** dans le Centre de conformité. Ensuite :

- Les réviseurs voient uniquement les révisions avant destruction qui leur sont affectées, tandis que les administrateurs qui sont ajoutés au Groupe de sécurité du gestionnaire des enregistrements voient toutes les révisions avant destruction.

- Les réviseurs peuvent ajouter de nouveaux utilisateurs dans la même révision avant destruction. Notez que cette action n’accorde pas automatiquement à ces utilisateurs ajoutés les [autorisations requises.](#permissions-for-disposition)

- Pour le processus de révision avant destruction, un volet de mini-évaluation pour chaque élément afficher un aperçu du contenu qu’ils sont autorisés à voir. S’ils ne disposent d’aucune autorisation, ils peuvent sélectionner le lien du contenu et demander des autorisations. Ce volet de mini-évaluation dispose également d’onglets pour les informations supplémentaires sur le contenu :
   - **Détails** pour afficher les propriétés indexées, leur emplacement, le créateur et la date de création, l’auteur et la date de la dernière modification.
   - **Historique** qui affiche l’historique à ce jour de toutes les actions de révision avant destruction avec les commentaires du réviseur, si disponible.

Une révision de destruction peut inclure du contenu dans les boîtes aux lettres Exchange, les sites SharePoint et les comptes OneDrive. Le contenu en attente de révision de destruction dans ces emplacements est définitivement supprimé uniquement lorsqu’un réviseur choisit de supprimer définitivement le contenu lors de l’étape finale de la destruction.

> [!NOTE]
> Une boîte aux lettres doit avoir au moins 10 Mo de données pour prendre en charge les révisions de suppression.

Les administrateurs peuvent voir un aperçu de toutes les dispositions en attente dans l'onglet **Aperçu**. Les réviseurs ne voient que leurs éléments en attente de disposition. Par exemple :

![Dispositions en attente dans la vue d’ensemble de la Gestion des enregistrements](../media/dispositions-overview.png)

Lorsque vous sélectionnez l’option **Afficher toutes les dispositions en attente**, vous êtes redirigé vers la page **Disposition**. Par exemple :

![Page de destruction dans le centre de conformité Microsoft 365.](../media/disposition-tab.png)


### <a name="workflow-for-a-disposition-review"></a>Flux de travail pour une révision de destruction

Le diagramme suivant illustre le flux de travail de base pour une révision de disposition (en une seule étape) lorsqu’une étiquette de rétention est publiée, puis appliquée manuellement par un utilisateur. Une étiquette de rétention configurée pour une révision de destruction peut également être appliquée automatiquement au contenu.
  
![Graphique montrant le fonctionnement de la destruction.](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)

### <a name="how-to-configure-a-retention-label-for-disposition-review"></a>Comment configurer une étiquette de rétention pour la révision avant destruction

Le déclenchement d’une révision avant destruction à la fin de la période de rétention est une option de configuration disponible uniquement avec une étiquette de rétention. La révision avant destruction n’est pas disponible pour une stratégie de rétention. Pour plus d’informations sur ces deux solutions de rétention, consultez [En savoir plus sur les stratégies de rétention et les étiquettes de rétention](retention.md).

Dans la page **Définir les paramètres de rétention** pour une étiquette de rétention :

![Paramètres de conservation pour une étiquette](../media/disposition-review-option.png)
 
Après avoir sélectionné l'option **Déclencher une révision de disposition**, la page suivante de la configuration vous permet de spécifier le nombre d'étapes consécutives de décision que vous souhaitez et les réviseurs de décision pour chaque étape :

![Spécification des réviseurs de destruction.](../media/disposition-reviewers.png) 

Sélectionnez **Ajouter une étape**, puis nommez-la à des fins d’identification. Spécifiez ensuite les réviseurs pour cette étape.

Pour les réviseurs, spécifiez un utilisateur ou un groupe de sécurité à extension messagerie. Les groupes Microsoft 365 ([anciennement groupes Office 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) ne sont pas pris en charge pour cette option.

Si vous avez besoin de plus d’une personne pour réviser un élément à la fin de la période de rétention, sélectionnez à nouveau **Ajouter une étape**, puis répétez le processus de configuration pour le nombre d’étapes souhaitées, avec un nombre de cinq étapes maximum. 

Dans chaque étape individuelle de destruction, tout utilisateur spécifié pour cette étape est autorisé à mettre en œuvre la prochaine action pour l’élément à la fin de sa période de rétention. Cet utilisateur peut également ajouter d’autres utilisateurs à leur étape de révision avant destruction.

> [!NOTE]
> Si vous avez configuré les étiquettes de conservation avant que la révision des dispositions en plusieurs étapes ne soit disponible, vous pouvez mettre à niveau vos étiquettes pour qu'elles prennent en charge cette fonctionnalité. Dans l'assistant d'étiquette, sélectionnez **Ajouter une étape**, ou modifiez les relecteurs existants ou ajoutez-en de nouveaux.

Pendant la phase de configuration, pour chaque étape spécifiée, vous pouvez la renommer, la réarranger ou la supprimer en sélectionnant l’option Actions de l’étape (**...**) : 

![Actions d’étape pour les révisions de destruction.](../media/stage-actions-disposition-review.png)

Cependant, vous ne pouvez pas réarranger ou supprimer une étape après la création d’une étiquette de rétention.

Après avoir spécifié vos réviseurs, n’oubliez pas de leur accorder l’autorisation du rôle de **Gestion de destruction**. Pour plus d’informations, voir la section [Autorisations de destruction](#permissions-for-disposition) sur cette page.

### <a name="how-to-customize-email-messages-for-disposition-review"></a>Comment personnaliser des messages électroniques pour la révision avant destruction

Exemple de notification par défaut envoyée par e-mail au réviseur :

![Exemple de notification par e-mail avec texte par défaut lorsqu’un élément est prêt pour révision de destruction.](../media/disposition-review-email.png)

Vous pouvez personnaliser les messages électroniques envoyés aux relecteurs de disposition pour la notification initiale, puis les rappels.

Dans l’une des pages de gestion des enregistrements du Centre de conformité, sélectionnez **Paramètres de gestion des enregistrements**:  

![Paramètres de gestion des enregistrements.](../media/record-management-settings.png)

Sous l’onglet **Disposition**, dans la section **Notifications par e-mail pour les révisions de destruction**, sélectionnez et spécifiez si vous souhaitez utiliser uniquement le message électronique par défaut ou ajouter votre propre texte au message par défaut. Votre texte personnalisé est ajouté aux instructions de l’e-mail après les informations sur l’étiquette de rétention et avant les instructions des étapes suivantes.

Un texte dans toutes les langues peut être ajouté, cependant, la mise en forme et les images ne sont actuellement pas prises en charge. Les adresses e-mail et les URL peuvent être saisies en tant que texte et, en fonction du client d’e-mail, affichées en tant que lien hypertexte ou de texte non mis en forme dans l’e-mail personnalisé.

Texte d’exemple à ajouter :

```console
If you need additional information, visit the helpdesk website (https://support.contoso.com) or send them an email (helpdesk@contoso.com).
```

Sélectionnez **Enregistrer** pour enregistrer toute modification.

### <a name="viewing-and-disposing-of-content"></a>Affichage et destruction de contenu

Lorsqu’un réviseur est averti par courrier électronique que le contenu est prêt à être examiné, il peut cliquer sur un lien dans le message électronique qui l’a directement envoyé à la page **Destruction** de **Gestion des enregistrements** dans le Centre de conformité Microsoft 365. Les réviseurs peuvent voir le nombre d’éléments en attente de destruction pour chaque étiquette de rétention à l’aide de **Type** qui afficher la **Destructions en attente**. Ils peuvent ensuite sélectionner une étiquette de rétention, puis **Ouvrir dans une nouvelle fenêtre** pour voir tout le contenu de cette étiquette :

![Ouvrir dans une nouvelle fenêtre pour la révision de destruction.](../media/open-in-new-window.png)

Sur la page **Dispositions en attente**, ils voient toutes les dispositions en attente pour cette étiquette. Lorsqu'un ou plusieurs éléments sont sélectionnés, ils peuvent utiliser le volet de mini-aperçu et les onglets **Source**, **Détails**, et **Historique** pour inspecter le contenu avant de prendre des mesures :

![Options de destruction.](../media/retention-disposition-options.png)

Si vous utilisez la barre de défilement horizontal ou si vous fermez le volet de mini-évaluation, vous voyez d’autres colonnes incluant la date d’expiration et le nom de l’étape de révision avant destruction.

Comme vous pouvez le voir dans l’exemple affiché, les actions prises en charge sont les suivantes : 
  
- **Approuver la destruction** :
    - Lorsque cette action est sélectionnée pour une étape intermédiaire de la révision avant destruction (vous avez configuré plusieurs étapes) : l’élément se déplace vers la prochaine étape de la destruction.
    - Lorsque cette action est sélectionnée pour l’étape finale de la révision de destruction ou qu’il n’existe qu’une seule étape de destruction : l’élément est marqué comme éligible pour une suppression définitive, qu’un travail de minuteur actionne ensuite dans les 7 jours. Le minutage exact de la suppression définitive de l’élément dépend de la charge de travail. Pour plus d’informations, voir [Fonctionnement de la rétention pour SharePoint et OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive) et [Fonctionnement de la rétention pour Exchange](retention-policies-exchange.md#how-retention-works-for-exchange).

- **Attribuer un nouveau libellé** :
    - Lorsque cette action est sélectionnée, l’élément quitte le procession de révision avant destruction pour l’étiquette d’origine. L’élément est ensuite soumis aux paramètres de rétention de la nouvelle étiquette de rétention sélectionnée.

- **Étendre** :
    - Lorsque cette action est sélectionnée, la révision avant destruction est suspendue de manière effective jusqu’à la fin de la période étendue, puis la révision avant destruction est déclenchée à nouveau à partir de la première étape.

- **Ajouter des réviseurs** :
    - Lorsque cette action est sélectionnée, l’utilisateur est invité à spécifier et ajouter d’autres utilisateurs pour la révision.
    > [!NOTE]
    > Cette action n’accorde pas automatiquement les [autorisations requises](#permissions-for-disposition) aux utilisateurs ajoutés. S'ils n'ont pas ces autorisations, ils ne peuvent pas participer à l'examen des dispositions.

À chaque action entreprise correspond un événement d'audit dans le groupe d'activités d'audit [Activités de révision de disposition](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities).

Lors d’une révision avant destruction, le contenu ne quitte jamais son emplacement d’origine et il n’est pas marqué pour une suppression définitive tant que cette action n’est pas sélectionnée par un réviseur pour l’étape finale ou la seule étape avant destruction.

## <a name="disposition-of-records"></a>Destruction des enregistrements

À partir de la page principale **Gestion des enregistrements** > l’onglet **Disposition**, vous pouvez identifier les éléments suivants :

- Éléments supprimés suite à une révision avant destruction.
- Les éléments marqués comme enregistrement ou enregistrement réglementaire qui ont été automatiquement supprimés à la fin de leur période de rétention.

Ces éléments affichent **Records Disposed** dans la colonne **Type**. Par exemple :

![Éléments supprimés sans révision avant destruction](../media/records-disposed2.png)

> [!NOTE]
> Cette fonctionnalité est basée sur les informations du [Journal d’audit unifié](search-the-audit-log-in-security-and-compliance.md) et nécessite par conséquent que l’audit soit [Activé et accessible à la recherche](turn-audit-log-search-on-or-off.md) pour la capture des événements correspondants.

Pour l'audit des éléments supprimés qui ont été marqués comme enregistrements ou enregistrements réglementaires, recherchez **Fichier supprimé marqué comme enregistrement** dans la catégorie **Activités de fichier et de page**. Cet événement d'audit s'applique aux documents et aux e-mails.

## <a name="filter-and-export-the-views"></a>Filtrer et exporter les affichages

Lorsque vous sélectionnez une étiquette de rétention dans la page **Destruction** , l’onglet **Destruction en attente** (le cas échéant) et **Éléments supprimés** vous permettent de filtrer les affichages pour trouver des éléments plus facilement.

Pour les destructions en attente, la plage horaire est basée sur la date d’expiration. Pour les éléments supprimés, la plage horaire est basée sur la date de suppression.
  
Vous pouvez exporter les informations relatives aux éléments de l’une ou l’autre vue en tant que fichier .csv que vous pouvez ensuite trier et gérer à l’aide d’Excel.
