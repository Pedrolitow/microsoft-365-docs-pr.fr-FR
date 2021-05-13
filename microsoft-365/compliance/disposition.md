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
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Surveillez et gérez la destruction de contenu lorsque vous utilisez une révision avant destruction ou que des éléments marqués comme enregistrement sont automatiquement supprimés selon les paramètres que vous avez configurés.
ms.openlocfilehash: 13310eca369949e2b66163907be4268120aa0ed0
ms.sourcegitcommit: 94e64afaf12f3d8813099d8ffa46baba65772763
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52344942"
---
# <a name="disposition-of-content"></a>Destruction de contenu

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Utilisez la page **Destruction** de **Gestion des enregistrements** dans le Centre de conformité Microsoft 365 pour gérer les révisions de destruction et afficher les métadonnées des [enregistrements](records-management.md#records) qui ont été automatiquement supprimés à la fin de la période de rétention.

> [!NOTE]
> Déploiement dans la préversion : **révision de destruction à plusieurs étapes**.
> 
> Un administrateur peut désormais ajouter jusqu’à cinq étapes consécutives de révision de destruction dans une étiquette de rétention et les réviseurs peuvent ajouter d’autres utilisateurs à leur étape de révision de destruction. Vous pouvez également personnaliser les rappels et les notifications par e-mail. Les sections suivantes ont plus d'informations sur les modifications dans cette préversion.

## <a name="prerequisites-for-viewing-content-dispositions"></a>Conditions préalables pour l’affichage des suppressions de contenu

Pour gérer les révisions de destruction et vérifier que les enregistrements ont été supprimés, vous devez disposer d’autorisations suffisantes et l’audit doit être activé.

### <a name="permissions-for-disposition"></a>Autorisations pour la destruction

Pour accéder à l’onglet **Destruction** dans le Centre de conformité Microsoft 365, les utilisateurs doivent avoir le rôle de **Gestion des destructions**. A partir de décembre 2020, ce rôle est désormais inclus dans le groupe de rôle par défaut de **Gestion des enregistrements**.

> [!NOTE]
> Par défaut, un administrateur général ne se voit pas attribuer le rôle de **Gestion des destructions**. 

Pour accorder aux utilisateurs uniquement les autorisations dont ils ont besoin pour les révisions avant destruction sans leur permettre d'afficher et de configurer d'autres fonctionnalités pour la conservation et la gestion des documents, créez un groupe de rôles personnalisé (par exemple, appelé « Réviseurs avant destruction ») et attribuez à ce groupe le rôle de **Gestion des destructions**.

Pour obtenir des instructions pour configurer ces autorisations, reportez-vous à la rubrique [Octroi de l’accès au Centre de sécurité et conformité Office 365 aux utilisateurs](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

En outre :

- Pour afficher le contenu des éléments pendant le processus de destruction, ajoutez des utilisateurs au groupe de rôle **Visionneuse de contenu de l’Explorateur de contenu**. Si les utilisateurs n’ont pas les autorisations de ce groupe de rôle, ils peuvent toujours sélectionner une action de révision de destruction pour achever la révision de destruction, mais vous devez le faire sans avoir la possibilité d’afficher le contenu de l’élément à partir du volet de mini-préversion dans le Centre de conformité.

- Dans la préversion : par défaut, chaque personne accédant à la page **Destruction** voit uniquement les éléments à réviser qui lui sont affectés. Pour qu’un administrateur de gestion des enregistrements puissent afficher tous les éléments affectés à l’ensemble des utilisateurs et toutes les étiquettes de rétention qui sont configurées pour la révision avant destruction : naviguez vers **Paramètres de gestion des enregistrements** > **Général** > **Groupe de sécurité du gestionnaire des enregistrements** pour activer ensuite un groupe de sécurité à extension messagerie qui contient les comptes d’administrateur.
    
    Les groupes de sécurité et les groupes Microsoft 365 qui ne sont pas à extension messagerie ne prennent pas en charge cette fonctionnalité et ne sont pas affichés dans la liste à sélectionner. Si vous devez créer un groupe de sécurité à extension messagerie, utilisez le lien vers le Centre d’administration Microsoft 365 pour créer le groupe. 
    
    > [!IMPORTANT]
    > Vous ne pouvez pas désactiver cette autorisation ou remplacer le groupe activé à partir du Centre de conformité. Toutefois, vous pouvez activer un autre groupe de sécurité à extension messagerie en utilisant la cmdlet [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage).
    > 
    > Par exemple : `Enable-ComplianceTagStorage -RecordsManagementSecurityGroupEmail dispositionreviewers@contosoi.com`

- Dans la préversion : l’option **Paramètres de gestion des enregistrements** est uniquement visible par les administrateurs de gestion des enregistrements. 

### <a name="enable-auditing"></a>Activer l’audit

Assurez-vous que l’audit est activé au moins un jour avant la première action de destruction. Pour plus d’informations, reportez-vous à l’article [Effectuer des recherches dans le journal d’audit dans le Centre de sécurité &amp; de conformité Office 365](search-the-audit-log-in-security-and-compliance.md). 

## <a name="disposition-reviews"></a>Révisions avant destruction

Lorsque le contenu atteint la fin de la période de rétention, vous souhaiterez peut-être réviser ce contenu et confirmer s’il peut être supprimé définitivement (« supprimé »). Par exemple, au lieu de supprimer le contenu, vous devrez peut-être :
  
- Suspendre la destruction de contenu pertinent pour un litige ou un audit.

- Affecter une période de rétention différente au contenu, peut-être parce que les paramètres de rétention d’origine étaient une solution temporaire ou provisoire.

- Déplacez le contenu de son emplacement existant vers un emplacement d’archivage, par exemple, si ce contenu a des valeurs d’historique ou de recherche.

Lorsqu’une révision de destruction est déclenchée à la fin de la période de rétention :
  
- Les réviseurs que vous sélectionnez reçoivent une notification par courrier électronique indiquant que leur contenu doit être examiné. Ces réviseurs peuvent être des utilisateurs individuels ou des groupes de sécurité à extension messagerie. Nouveautés dans la préversion :
   - Vous pouvez personnaliser l’e-mail qu’ils reçoivent, notamment les instructions dans d’autres langues. Pour un support multilingue, vous devez vous-même spécifier les traductions et ce texte personnalisé s’affiche pour tous les réviseurs indépendamment de leurs paramètres régionaux.
   - Les utilisateurs reçoivent une notification par e-mail initiale par étiquette à la fin de la période de rétention de l’élément, avec un rappel par étiquette une fois par semaine de toutes les révisions avant destruction qui leur sont affectées. Ils peuvent cliquer sur le lien dans les e-mails de notification et de rappel pour accéder à la page **Destruction** dans le Centre de conformité Microsoft 365 pour réviser le contenu et prendre des mesures. Les réviseurs peuvent également accéder directement à la page **Destruction** dans le Centre de conformité.
   - Les réviseurs voient uniquement les révisions avant destruction qui leur sont affectées, tandis que les administrateurs qui sont ajoutés au Groupe de sécurité du gestionnaire des enregistrements voient toutes les révisions avant destruction.
   - Les réviseurs peuvent ajouter de nouveaux utilisateurs dans la même révision avant destruction. Actuellement, cette action n’accorde pas automatiquement les [autorisations requises](#permissions-for-disposition) à ces utilisateurs ajoutés.
   - Pour le processus de révision avant destruction, un volet de mini-évaluation pour chaque élément afficher un aperçu du contenu qu’ils sont autorisés à voir. S’ils ne disposent d’aucune autorisation, ils peuvent sélectionner le lien du contenu et demander des autorisations. Ce volet de mini-évaluation dispose également d’onglets pour les informations supplémentaires sur le contenu :
       - **Détails** pour afficher les propriétés indexées, leur emplacement, le créateur et la date de création, l’auteur et la date de la dernière modification.
       - **Historique** qui affiche l’historique à ce jour de toutes les actions de révision avant destruction avec les commentaires du réviseur, si disponible.

Une révision de destruction peut inclure du contenu dans les boîtes aux lettres Exchange, les sites SharePoint et les comptes OneDrive. Le contenu en attente de révision de destruction dans ces emplacements est définitivement supprimé uniquement lorsqu’un réviseur choisit de supprimer définitivement le contenu lors de l’étape finale de la destruction.

> [!NOTE]
> Une boîte aux lettres doit avoir au moins 10 Mo de données pour prendre en charge les révisions de suppression.

Les administrateurs peuvent voir une vue d’ensemble de toutes les destructions en attente dans l’onglet **Vue d’ensemble**. Les réviseurs voient uniquement leurs éléments en attente de destruction. Par exemple :

![Destructions en attente dans la vue d’ensemble de la Gestion des enregistrements](../media/dispositions-overview.png)

Lorsque vous sélectionnez l’option **Afficher toutes les destructions en attente**, vous êtes redirigé vers la page **Destruction** . Par exemple :

![Page de destruction dans le centre de conformité Microsoft 365](../media/disposition-tab.png)


### <a name="workflow-for-a-disposition-review"></a>Flux de travail pour une révision de destruction

Le diagramme suivant illustre le flux de travail de base d’une révision de destruction lorsqu’une étiquette de rétention est publiée et appliquée manuellement par un utilisateur. Une étiquette de rétention configurée pour une révision de destruction peut également être appliquée automatiquement au contenu.
  
![Graphique montrant le fonctionnement de la destruction](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)

### <a name="how-to-configure-a-retention-label-for-disposition-review"></a>Comment configurer une étiquette de rétention pour la révision avant destruction

Le déclenchement d’une révision avant destruction à la fin de la période de rétention est une option de configuration disponible uniquement avec une étiquette de rétention. La révision avant destruction n’est pas disponible pour une stratégie de rétention. Pour plus d’informations sur ces deux solutions de rétention, consultez [En savoir plus sur les stratégies de rétention et les étiquettes de rétention](retention.md).

Dans la page **Définir les paramètres de rétention** pour une étiquette de rétention :

![Paramètres de conservation pour une étiquette](../media/disposition-review-option.png)
 
Après votre sélection de l’option **Déclencher une révision avant destruction**, sur la page suivante de l’assistant, vous spécifiez le nombre souhaité d’étapes consécutives de la destruction et les réviseurs avant destruction pour chaque étape :

![Spécification des réviseurs avant destruction](../media/disposition-reviewers.png) 

Sélectionnez **Ajouter une étape**, puis nommez-la à des fins d’identification. Spécifiez ensuite les réviseurs pour cette étape.

Pour les réviseurs, spécifiez un utilisateur ou un groupe de sécurité à extension messagerie. Les groupes Microsoft 365 ([anciennement groupes Office 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) ne sont actuellement pas pris en charge pour cette option.

Si vous avez besoin de plus d’une personne pour réviser un élément à la fin de la période de rétention, sélectionnez à nouveau **Ajouter une étape**, puis répétez le processus de configuration pour le nombre d’étapes souhaitées, avec un nombre de cinq étapes maximum. 

Dans chaque étape individuelle de destruction, tout utilisateur spécifié pour cette étape est autorisé à mettre en œuvre la prochaine action pour l’élément à la fin de sa période de rétention. Cet utilisateur peut également ajouter d’autres utilisateurs à leur étape de révision avant destruction.

> [!NOTE]
> Les étiquettes de rétention existantes qui sont configurées pour la révision avant destruction peuvent être mises à niveau pour utiliser la révision avant destruction à plusieurs étapes en configurant l’étiquette. Dans l’Assistant d’étiquette, sélectionnez **Ajouter une étape** ou modifiez les réviseurs existants ou ajoutez de nouveaux réviseurs.

Pendant la phase de configuration, pour chaque étape spécifiée, vous pouvez la renommer, la réarranger ou la supprimer en sélectionnant l’option Actions de l’étape (**...**) : 

![Actions de l’étape pour les révisions avant destruction](../media/stage-actions-disposition-review.png)

Cependant, vous ne pouvez pas réarranger ou supprimer une étape après la création d’une étiquette de rétention.

Après avoir spécifié vos réviseurs, n’oubliez pas de leur accorder l’autorisation du rôle de **Gestion de destruction**. Pour plus d’informations, voir la section [Autorisations de destruction](#permissions-for-disposition) sur cette page.

### <a name="how-to-customize-email-messages-for-disposition-review"></a>Comment personnaliser des messages électroniques pour la révision avant destruction

Également dans la préversion, vous pouvez personnaliser les messages électroniques envoyés aux réviseurs avant destruction pour la notification initiale et les rappels.

À partir de l’une des pages Destruction dans le Centre de conformité, sélectionnez **Paramètres de gestion des enregistrements** :  

![Paramètres de gestion des enregistrements](../media/record-management-settings.png)

Sélectionnez ensuite l’onglet **Modèles de courrier**, puis spécifiez si vous voulez utiliser simplement les modèles d’e-mail par défaut ou ajouter votre texte au modèle par défaut. Votre texte personnalisé est ajouté aux instructions de l’e-mail après les informations sur l’étiquette de rétention et avant les instructions des étapes suivantes.

Un texte dans toutes les langues peut être ajouté, cependant, la mise en forme et les images ne sont actuellement pas prises en charge. Les adresses e-mail et les URL peuvent être saisies en tant que texte et, en fonction du client d’e-mail, affichées en tant que lien hypertexte ou de texte non mis en forme dans l’e-mail personnalisé.

Texte d’exemple à ajouter :

```console
If you need additional information, visit the helpdesk website (https://support.contoso.com) or send them an email (helpdesk@contoso.com).
```

Sélectionnez **Enregistrer** pour enregistrer toute modification.

### <a name="viewing-and-disposing-of-content"></a>Affichage et destruction de contenu

Lorsqu’un réviseur est averti par courrier électronique que le contenu est prêt à être examiné, il passe à l’onglet **Destruction** de **Gestion des enregistrements** dans le Centre de conformité Microsoft 365. Les réviseurs peuvent voir le nombre d’éléments en attente de destruction pour chaque étiquette de rétention à l’aide de **Type** qui afficher la **Destructions en attente**. Ils peuvent ensuite sélectionner une étiquette de rétention, puis **Ouvrir dans une nouvelle fenêtre** pour voir tout le contenu de cette étiquette :

![Ouvrir dans une nouvelle fenêtre pour la révision avant destruction](../media/open-in-new-window.png)

À partir de la page **Destructions en attente**, ils peuvent afficher toutes les destructions en attente pour cette étiquette. Lorsqu’un ou plusieurs éléments sont sélectionnés, ils peuvent utiliser le volet de mini-visualisation et les onglets **Source**, **Détails** et **Historique** pour inspecter le contenu avant d’agir dessus :

![Options de destruction](../media/retention-disposition-options.png)

Si vous utilisez la barre de défilement horizontal ou si vous fermez le volet de mini-évaluation, vous voyez d’autres colonnes incluant la date d’expiration et le nom de l’étape de révision avant destruction.

Comme vous pouvez le voir dans l’exemple affiché, les actions prises en charge sont les suivantes : 
  
- **Approuver la destruction** :
    - Lorsque cette action est sélectionnée pour une étape intermédiaire de la révision avant destruction (vous avez configuré plusieurs étapes) : l’élément se déplace vers la prochaine étape de la destruction.
    - Lorsque cette action est sélectionnée pour l’étape finale de la révision avant destruction ou qu’il n’existe qu’une seule étape avant destruction : l’élément est marqué comme éligible pour une suppression définitive. La durée exacte pour cette destruction dépend de la charge de travail. Pour plus d’informations, voir [Fonctionnement des paramètres de rétention avec le contenu en place](retention.md#how-retention-settings-work-with-content-in-place).
- **Attribuer un nouveau libellé** :
    - Lorsque cette action est sélectionnée, l’élément quitte le procession de révision avant destruction pour l’étiquette d’origine. L’élément est ensuite soumis aux paramètres de rétention de la nouvelle étiquette de rétention sélectionnée.
- **Étendre** :
    - Lorsque cette action est sélectionnée, la révision avant destruction est suspendue de manière effective jusqu’à la fin de la période étendue, puis la révision avant destruction est déclenchée à nouveau à partir de la première étape.
- **Ajouter des réviseurs** :
    - Lorsque cette action est sélectionnée, l’utilisateur est invité à spécifier et ajouter d’autres utilisateurs pour la révision.
    
    > [!NOTE]
    > Cette action n’accorde pas automatiquement les [autorisations requises](#permissions-for-disposition) aux utilisateurs ajoutés. S’ils n’ont pas ces autorisations, ils ne pourront pas participer à la révision avant destruction.

Chaque action engagée est enregistrée et stockée, bien que vous ne puissiez pas encore les rechercher dans le journal d’audit.

Lors d’une révision avant destruction, le contenu ne quitte jamais son emplacement d’origine et il n’est pas marqué pour une suppression définitive tant que cette action n’est pas sélectionnée par un réviseur pour l’étape finale ou la seule étape avant destruction.

## <a name="disposition-of-records"></a>Destruction des enregistrements

Utilisez l’onglet **Destruction** à partir de la page **Gestion des enregistrements** pour identifier :

- Éléments supprimés suite à une révision avant destruction.
- Les éléments marqués comme enregistrement ou enregistrement réglementaire qui ont été automatiquement supprimés à la fin de leur période de rétention.

Ces éléments affichent **Enregistrements supprimés** dans la colonne **Type**. Par exemple :

![Éléments supprimés sans révision avant destruction](../media/records-disposed2.png)

Les éléments qui s’affichent dans l’onglet **Éléments supprimés** sont conservés pendant sept ans après la suppression de l’élément, avec une limite d’un million d’éléments par enregistrement pour cette période. Si vous voyez le nombre de **Count** approcher cette limite d'un million, et que vous avez besoin d'une preuve de destruction pour vos enregistrements, contactez le [Support Microsoft](../business-video/get-help-support.md).

> [!NOTE]
> Cette fonctionnalité est basée sur les informations du [Journal d’audit unifié](search-the-audit-log-in-security-and-compliance.md) et nécessite par conséquent que l’audit soit [Activé et accessible à la recherche](turn-audit-log-search-on-or-off.md) pour la capture des événements correspondants.

Pour auditer les éléments supprimés marqués comme enregistrements ou enregistrements réglementaires, recherchez **Fichier supprimé marqué comme enregistrement** dans la catégorie **Activités des fichiers et pages**. Cet événement d’audit est applicable aux documents et messages électroniques.

## <a name="filter-and-export-the-views"></a>Filtrer et exporter les affichages

Lorsque vous sélectionnez une étiquette de rétention dans la page **Destruction** , l’onglet **Destruction en attente** (le cas échéant) et **Éléments supprimés** vous permettent de filtrer les affichages pour trouver des éléments plus facilement.

Pour les destructions en attente, la plage horaire est basée sur la date d’expiration. Pour les éléments supprimés, la plage horaire est basée sur la date de suppression.
  
Vous pouvez exporter les informations relatives aux éléments de l’une ou l’autre vue en tant que fichier .csv que vous pouvez ensuite trier et gérer à l’aide d’Excel.
