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
description: Surveiller et gérer la suppression de contenu, que vous utilisiez une révision de destruction ou que le contenu soit automatiquement supprimé selon les paramètres que vous avez configurés.
ms.openlocfilehash: d2c2e4e469efe16277f34a902f6720dc2b39e908
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50918040"
---
# <a name="disposition-of-content"></a>Destruction de contenu

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Utilisez l’onglet **Destruction** de **Gestion des enregistrements** dans le Centre de conformité Microsoft 365 pour gérer les révisions de destruction et afficher les [enregistrements](records-management.md#records) qui ont été automatiquement supprimés à la fin de la période de rétention. 

## <a name="prerequisites-for-viewing-content-dispositions"></a>Conditions préalables pour l’affichage des suppressions de contenu

Pour gérer les révisions de destruction et vérifier que les enregistrements ont été supprimés, vous devez disposer d’autorisations suffisantes et l’audit doit être activé.

### <a name="permissions-for-disposition"></a>Autorisations pour la destruction

Pour accéder à l’onglet **Destruction** dans le Centre de conformité Microsoft 365, les utilisateurs doivent avoir le rôle d’administrateur de **Gestion des suppressions** . A partir de décembre 2020, ce rôle est désormais inclus dans le groupe de rôle administrateur par défaut de **Gestion des enregistrements**.

> [!NOTE]
> Par défaut, un administrateur général ne se voit pas attribuer le rôle de **Gestion des suppressions** . 

Pour accorder aux utilisateurs uniquement les autorisations dont ils ont besoin pour les révisions de disposition sans leur permettre d'afficher et de configurer d'autres fonctionnalités pour la conservation et la gestion des documents, créez un groupe de rôles personnalisé (par exemple, appelé « Réviseurs de disposition ») et attribuez à ce groupe le rôle de Gestion de suppressions.

De plus, pour afficher le contenu des éléments pendant le processus de destruction, ajoutez des utilisateurs aux deux groupes de rôles suivants : **la visionneuse de contenu de l’Explorateur de contenu** et **visionneuse de liste de l’Explorateur de contenu**. Si les utilisateurs n’ont pas les autorisations de ces groupes de rôles, ils peuvent toujours sélectionner une action de révision de destruction pour achever la révision de destruction, mais vous devez le faire sans avoir la possibilité d’afficher le contenu de l’élément à partir du centre de conformité.

Pour obtenir des instructions pour configurer ces autorisations, reportez-vous à la rubrique [Octroi de l’accès au Centre de sécurité et conformité Office 365 aux utilisateurs](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

### <a name="enable-auditing"></a>Activer l’audit

Assurez-vous que l’audit est activé au moins un jour avant la première action de destruction. Pour plus d’informations, reportez-vous à l’article [Effectuer des recherches dans le journal d’audit dans le Centre de sécurité &amp; de conformité Office 365](search-the-audit-log-in-security-and-compliance.md). 

## <a name="disposition-reviews"></a>Révisions avant destruction

Lorsque le contenu atteint la fin de la période de rétention, vous souhaiterez peut-être réviser ce contenu et confirmer s’il peut être supprimé définitivement (« supprimé »). Par exemple, au lieu de supprimer le contenu, vous devrez peut-être :
  
- Suspendre la suppression de contenu pertinent en cas de litige ou d’audit.

- Affecter une période de rétention différente au contenu, peut-être parce que les paramètres de rétention d’origine étaient une solution temporaire ou provisoire.

- Déplacez le contenu de son emplacement existant vers un emplacement d’archivage, par exemple, si ce contenu a des valeurs d’historique ou de recherche.

Lorsqu’une révision de destruction est déclenchée à la fin de la période de rétention :
  
- Les personnes que vous sélectionnez reçoivent une notification par courrier électronique indiquant que leur contenu doit être examiné. Ces réviseurs peuvent être des utilisateurs individuels ou des groupes de sécurité à extension messagerie. Notez que les notifications sont envoyées de façon hebdomadaire.
    
- Les réviseurs accèdent à l’onglet **Destruction** dans le Centre de conformité Microsoft 365 pour examiner le contenu et décider si vous voulez le supprimer définitivement, prolonger sa période de rétention ou appliquer une autre étiquette de rétention.

Une révision de destruction peut inclure du contenu dans les boîtes aux lettres Exchange, les sites SharePoint, les comptes OneDrive et les groupes Microsoft 365. Le contenu en attente de révision de destruction dans ces emplacements est supprimé uniquement lorsqu’un réviseur choisit de supprimer définitivement le contenu.

> [!NOTE]
> Une boîte aux lettres doit avoir au moins 10 Mo de données pour prendre en charge les révisions de suppression.

Vous pouvez voir une vue d’ensemble de toutes les suppressions en attente dans l’onglet **Vue d’ensemble**. Par exemple :

![Destructions en attente dans la vue d’ensemble de la Gestion des enregistrements](../media/dispositions-overview.png)

Lorsque vous sélectionnez l’option **Afficher toutes les destructions en attente**, vous êtes redirigé vers la page **Destruction** . Par exemple :

![Page de destruction dans le centre de conformité Microsoft 365](../media/disposition-tab.png)


### <a name="workflow-for-a-disposition-review"></a>Flux de travail pour une révision de destruction

Le diagramme suivant illustre le flux de travail de base d’une révision de destruction lorsqu’une étiquette de rétention est publiée et appliquée manuellement par un utilisateur. Une étiquette de rétention configurée pour une révision de destruction peut également être appliquée automatiquement au contenu.
  
![Graphique montrant le fonctionnement de la destruction](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)
  
Le déclenchement d’une révision de suppression à la fin de la période de rétention est une option de configuration disponible uniquement avec une étiquette de rétention. Cette option n’est pas disponible pour une stratégie de rétention. Pour plus d’informations sur ces deux solutions de rétention, consultez [En savoir plus sur les stratégies de rétention et les étiquettes de rétention](retention.md).

Dans la page **Définir les paramètres de rétention** pour une étiquette de rétention :

![Paramètres de conservation pour une étiquette](../media/disposition-review-option.png)
 
Une fois que vous avez sélectionné cet option **Déclencher une révision avant destruction**, vous spécifiez les relecteurs de destruction sur la page suivante de l’Assistant :

![Spécification des réviseurs avant destruction](../media/disposition-reviewers.png)

Pour les réviseurs, spécifiez un utilisateur ou un groupe de sécurité à extension messagerie. Les groupes Microsoft 365 ([anciennement groupes Office 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) ne sont pas pris en charge pour cette option.

### <a name="viewing-and-disposing-of-content"></a>Affichage et destruction de contenu

Lorsqu’un réviseur est averti par courrier électronique que le contenu est prêt à être examiné, il passe à l’onglet **Destruction** de **Gestion des enregistrements** dans le Centre de conformité Microsoft 365. Les réviseurs peuvent voir le nombre d’éléments pour chaque étiquette de rétention en attente de destruction, puis sélectionner une étiquette de rétention pour afficher tout le contenu contenant cette étiquette.

Une fois que vous avez sélectionné une étiquette de rétention, vous voyez toutes les suppressions en attente de cette étiquette dans l’onglet **Destruction en attente** . Sélectionnez un ou plusieurs éléments à partir desquels vous pouvez choisir une action et entrez un commentaire de justification :

![Options de destruction](../media/retention-disposition-options.png)

Comme vous pouvez le voir dans l’image, les actions prises en charge sont les suivantes : 
  
- Supprimer définitivement l’élément
- Prolonger la période de rétention
- Appliquer une autre étiquette de rétention

En vous fournissant les autorisations d’accès à l’emplacement et au contenu, vous pouvez utiliser le lien situé dans la colonne **Emplacement** pour afficher les documents dans leur emplacement d’origine. Lors d’une révision de destruction, le contenu ne se déplace jamais à partir de son emplacement d’origine et n’est jamais supprimé tant que le réviseur n’a pas choisi de le faire.

Les notifications par courrier électronique sont envoyées automatiquement aux réviseurs sur une base hebdomadaire. Ce processus planifié signifie qu’une fois que le contenu atteint la fin de la période de rétention, il peut arriver que les réviseurs reçoivent jusqu’à sept jours la notification par courrier électronique indiquant que le contenu est en attente de destruction.
  
Toutes les actions de destruction peuvent faire l’objet d’un audit et le texte de la justification entré par le réviseur est enregistré et affiché dans la colonne **Commentaire** sur la page **Éléments supprimés**.
  
### <a name="how-long-until-disposed-content-is-permanently-deleted"></a>Combien de temps faut-il pour supprimer définitivement du contenu supprimé

Le contenu en attente de révision de destruction est supprimé uniquement lorsqu’un réviseur choisit de supprimer définitivement le contenu. Lorsque le réviseur choisit cette option, le contenu du site SharePoint ou du compte OneDrive est éligible pour le processus de nettoyage standard décrit dans [Fonctionnement des paramètres de rétention avec le contenu en place](retention.md#how-retention-settings-work-with-content-in-place).

## <a name="disposition-of-records"></a>Destruction des enregistrements

Utilisez l’onglet **Destruction** à partir de la page **Gestion des enregistrements** pour identifier les enregistrements qui sont désormais supprimés, soit automatiquement, soit après une révision de suppression. Ces éléments affichent **Enregistrements supprimés** dans la colonne **Type**. Par exemple :

![Éléments supprimés sans révision avant destruction](../media/records-disposed2.png)

Les éléments qui apparaissent dans la **Éléments supprimés** pour les étiquettes d’enregistrement sont conservés pendant sept ans après la suppression de l’élément, avec une limite de 1 million éléments par enregistrement pour cette période. Si vous voyez le nombre de **Count** approcher cette limite d'un million, et que vous avez besoin d'une preuve de destruction pour vos enregistrements, contactez le [Support Microsoft](/office365/admin/contact-support-for-business-products).

> [!NOTE]
> Cette fonctionnalité est basée sur les informations du [journal d’audit unifié](search-the-audit-log-in-security-and-compliance.md) et nécessite par conséquent que l’audit soit [activé et puisse faire l’objet d’une recherche](turn-audit-log-search-on-or-off.md) de sorte que les événements correspondants soient capturés.

Pour l’audit, recherchez **fichier supprimé marqué comme enregistrement** dans la catégorie **activités de fichier et de page** . Cet événement d’audit est applicable aux documents et messages électroniques.

## <a name="filter-and-export-the-views"></a>Filtrer et exporter les affichages

Lorsque vous sélectionnez une étiquette de rétention dans la page **Destruction** , l’onglet **Destruction en attente** (le cas échéant) et **Éléments supprimés** vous permettent de filtrer les affichages pour trouver des éléments plus facilement. 

Pour les destructions en attente, la plage horaire est basée sur la date d’expiration. Pour les éléments supprimés, la plage horaire est basée sur la date de suppression.
  
Vous pouvez exporter les informations relatives aux éléments de l’une ou l’autre vue en tant que fichier .csv que vous pouvez ensuite trier et gérer à l’aide d’Excel :

![Option d’exportation pour destruction](../media/retention-export-option.png)