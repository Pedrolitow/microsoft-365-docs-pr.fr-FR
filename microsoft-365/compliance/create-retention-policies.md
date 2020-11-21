---
title: Créer et configurer des stratégies de rétention pour conserver ou supprimer automatiquement le contenu
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Utilisez une stratégie de rétention pour garder un contrôle efficace sur le contenu que les utilisateurs génèrent par courriers électroniques, documents et conversations. Conservez ce que vous voulez et supprimez le reste.
ms.openlocfilehash: bcf0ef5aa76113102013bc20fca02e6d516c3203
ms.sourcegitcommit: 20d1158c54a5058093eb8aac23d7e4dc68054688
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "49376577"
---
# <a name="create-and-configure-retention-policies"></a>Créer et configurer des stratégies de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Utilisez une stratégie de rétention pour décider de manière proactive si vous souhaitez conserver le contenu, supprimer le contenu ou les deux, c’est-à-dire conserver puis supprimer le contenu.

Une stratégie de rétention vous permet d’effectuer cela de façon très efficace en attribuant les mêmes paramètres de rétention au contenu par emplacement, au niveau d’un site ou d’une boîte aux lettres. Si vous ne savez pas si vous devez utiliser une stratégie ou une étiquette de rétention, voir [Stratégies et étiquettes de rétention](retention.md#retention-policies-and-retention-labels).

Pour en savoir plus sur les stratégies de rétention et le fonctionnement de la rétention, consultez la page [Découvrir les stratégies et étiquettes de rétention](retention.md).

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de votre organisation dispose de toutes les autorisations pour créer et gérer les stratégies de confidentialité. Si vous ne vous connectez pas en tant qu’administrateur général, voir [Autorisations nécessaires pour créer et gérer des stratégies et des étiquettes de confidentialité](get-started-with-retention.md#permissions-required-to-create-and-manage-retention-policies-and-retention-labels).

## <a name="create-and-configure-a-retention-policy"></a>Créer et configurer une stratégie de rétention

Bien qu’une stratégie de rétention puisse prendre en charge plusieurs emplacements, vous ne pouvez pas créer de stratégie de rétention unique qui inclut tous les emplacements pris en charge :

- E-mails Exchange
- Site SharePoint
- Comptes OneDrive
- Groupes Microsoft 365
- Skype Entreprise
- Dossiers publics Exchange
- Messages du canal Teams
- Conversations Teams
- Messages communautaires Yammer
- Messages privés Yammer

Lorsque vous sélectionnez l’emplacement Teams ou Yammer lors de la création d’une stratégie de rétention, les autres emplacements sont automatiquement exclus. Par conséquent, l’emplacement à inclure (Teams ou Yammer) détermine les instructions à suivre :

- [Instructions relatives à une stratégie de rétention pour les emplacements Teams](#retention-policy-for-teams-locations)
- [Instructions relatives à une stratégie de rétention pour les emplacements Yammer](#retention-policy-for-yammer-locations)
- [Instructions relatives à une stratégie de rétention pour les emplacements autres que Teams et Yammer](#retention-policy-for-locations-other-than-teams-and-yammer)

Lorsque vous avez plusieurs stratégies de rétention et que vous utilisez également des étiquettes de rétention, voir [Principes de rétention et priorité](retention.md#the-principles-of-retention-or-what-takes-precedence) pour comprendre le résultat lorsque plusieurs paramètres de rétention s’appliquent au même contenu.

### <a name="retention-policy-for-teams-locations"></a>Stratégie de rétention pour les emplacements Teams

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), sélectionnez **Stratégies** > **Retention**.

2. Sélectionnez **Nouvelle stratégie de rétention** pour démarrer l’assistant de création de stratégie de rétention, puis nommez votre nouvelle stratégie de rétention.

3. Pour la page **Sélectionnez les emplacements où appliquer la stratégie**, sélectionnez l’un des deux emplacements suivants sur Teams : **Message du canal Teams** ou **Conversations Teams**.

   Pour **Messages de canal Teams**, les messages provenant des canaux standard sont inclus, contrairement à ceux des [canaux privés](https://docs.microsoft.com/microsoftteams/private-channels). Les canaux privés ne sont actuellement pas pris en charge par les stratégies de rétention.

   Par défaut, [toutes les équipes et tous les utilisateurs sont sélectionnés](#a-policy-that-applies-to-entire-locations). Vous pouvez toutefois affiner cette sélection grâce aux [options **Choisir** et **Exclure**](#a-policy-with-specific-inclusions-or-exclusions).

4. Sur la page **Indiquez si vous souhaitez conserver le contenu et/ou le supprimer** de l’assistant, spécifiez les options de configuration pour la conservation et la suppression du contenu.

   Vous pouvez créer une stratégie de rétention qui conserve uniquement le contenu sans le supprimer, conserve puis supprime le contenu après une période donnée, ou supprime simplement le contenu après une période donnée. Si vous souhaitez en savoir plus, consultez [Paramètres pour la conservation et la suppression du contenu](#settings-for-retaining-and-deleting-content) sur cette page.

5. Terminez l’assistant pour enregistrer vos paramètres.

Pour plus d’informations sur les stratégies de rétention pour Teams, voir [Stratégies de rétention dans Microsoft Teams](https://docs.microsoft.com/microsoftteams/retention-policies) dans la documentation Teams.

#### <a name="additional-retention-policy-needed-to-support-teams"></a>Stratégie de rétention supplémentaire requise pour la prise en charge de Teams

Teams n’est pas seulement des conversations et des messages de canaux. Si vous avez des équipes créées à partir d’un groupe Microsoft 365 (anciennement groupe Office 365), vous devez également configurer une stratégie de rétention qui inclut ce groupe Microsoft 365 à l’aide de l’emplacement **Groupes Microsoft 365**. Cette stratégie de rétention s’applique au contenu de la boîte aux lettres, du site et des fichiers du groupe.

Si vous possédez des sites d’équipe qui ne sont pas connectés à un groupe Microsoft 365, vous avez besoin d’une stratégie de rétention qui inclut les emplacements de **sites SharePoint** ou **comptes OneDrive** pour conserver et supprimer des fichiers dans Teams :

- Les fichiers partagés dans une conversation sont stockés sur le compte OneDrive de l’utilisateur qui a partagé le fichier.

- Les fichiers chargés dans les canaux sont stockés sur le site SharePoint associé à l’équipe.

> [!TIP]
> Vous pouvez appliquer une stratégie de rétention aux fichiers d’une équipe spécifique uniquement lorsque celle-ci n’est pas connectée à un groupe Microsoft 365 en sélectionnant le site SharePoint pour l’équipe, ainsi que les comptes OneDrive des utilisateurs au sein de Teams.

Il est possible qu’une stratégie de conservation appliquée aux groupes Microsoft 365, sites SharePoint ou comptes OneDrive supprime un fichier référencé dans une conversation ou un message de canal Teams avant la suppression de ces messages. Dans ce scénario, le fichier s’affiche encore dans le message Teams, mais lorsque les utilisateurs sélectionnent le fichier, un message d’erreur « fichier introuvable » s’affiche. Ce comportement n’est pas spécifique aux stratégies de rétention et peut également se produire si un utilisateur supprime manuellement un fichier à partir de SharePoint ou de OneDrive.

### <a name="retention-policy-for-yammer-locations"></a>Stratégie de rétention pour les emplacements Yammer

> [!NOTE]
> Les stratégies de rétention Yammer sont déployées en préversion. Si vous ne voyez pas encore les nouveaux emplacements Yammer, réessayez dans quelques semaines.
>
> Pour utiliser cette fonctionnalité, votre réseau Yammer doit être [Mode Natif](https://docs.microsoft.com/yammer/configure-your-yammer-network/overview-native-mode), et non Mode Hybride.

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), sélectionnez **Stratégies** > **Retention**.

2. Sélectionnez **Nouvelle stratégie de rétention** pour créer une stratégie de rétention.

3. Sur la page **Indiquez si vous souhaitez conserver le contenu et/ou le supprimer** de l’assistant, spécifiez les options de configuration pour la conservation et la suppression du contenu. 
    
    Vous pouvez créer une stratégie de rétention qui conserve uniquement le contenu sans le supprimer, conserve puis supprime le contenu après une période donnée, ou supprime simplement le contenu après une période donnée. Si vous souhaitez en savoir plus, consultez [Paramètres pour la conservation et la suppression du contenu](#settings-for-retaining-and-deleting-content) sur cette page.
    
    Ne sélectionnez pas **Utiliser les paramètres de rétention avancée**, car cette option n’est pas prise en charge pour les emplacements Yammer. 

4. Sur la page **Choisir les emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**. Basculez ensuite sur l’un ou les deux emplacements de Yammer: **message de communauté Yammer** et **messages privés Yammer**.
    
    Par défaut, tous les utilisateurs et communautés sont sélectionnés, mais vous pouvez les affiner en spécifiant les groupes et les utilisateurs à inclure ou à exclure.
    
    Pour les messages privés Yammer: 
    - Si vous conservez la valeur par défaut à **Tous**, les utilisateurs invités B2B Azure ne sont pas inclus. 
    - Vous pouvez appliquer une stratégie de rétention à des utilisateurs externes si vous sélectionnez **Choisir Utilisateur**.

5. Terminez l’assistant pour enregistrer vos paramètres.

Pour en savoir plus sur le fonctionnement des stratégies de rétention pour Yammer, consultez la page [Découvrir les stratégies de rétention pour Yammer](retention-policies-yammer.md).

#### <a name="additional-retention-policies-needed-to-support-yammer"></a>Stratégies de rétention supplémentaires requises pour la prise en charge de Yammer

Yammer est bien plus que des messages de la communauté et des messages privés. Pour conserver et supprimer des courriers électroniques pour votre réseau Yammer, configurez une stratégie de rétention supplémentaire qui inclut les groupes Microsoft 365 utilisés pour Yammer, à l’aide de l'emplacement **Groupes Microsoft 365**. 

Pour retenir et supprimer les fichiers qui sont stockés dans Yammer, vous avez besoin d’une stratégie de rétention qui inclut les emplacements **Des sites SharePoint** ou **Des comptes OneDrive**:

- Les fichiers partagés dans les messages privés sont stockés sur le compte OneDrive de l’utilisateur qui a partagé le fichier. 

- Les fichiers chargés dans les communautés sont stockés sur le site SharePoint pour la communauté Yammer.

Il est possible qu’une stratégie de conservation appliquée aux sites SharePoint ou comptes OneDrive supprime un fichier référencé dans un message Yammer avant la suppression de ces messages. Dans ce scénario, le fichier s’affiche encore dans le message Yammer, mais lorsque les utilisateurs sélectionnent le fichier, un message d’erreur « fichier introuvable » s’affiche. Ce comportement n’est pas spécifique aux stratégies de rétention et peut également se produire si un utilisateur supprime manuellement un fichier à partir de SharePoint ou de OneDrive.

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a>Stratégie de rétention pour les emplacements autres que Teams et Yammer

Utilisez les instructions suivantes pour les stratégies de rétention qui s’appliquent ces services:

- Exchange: Email et dossiers publics
- Sites SharePoint
- OneDrive: Comptes
- Groupes Microsoft 365
- Skype Entreprise

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), sélectionnez **Stratégies** > **Retention**.

2. Sélectionnez **Nouvelle stratégie de rétention** pour démarrer l’assistant de création de stratégie de rétention, puis nommez votre nouvelle stratégie de rétention.

3. Pour la page **Choisir les emplacements**, activez ou désactivez les emplacements, à l’exception des emplacements de Teams. Pour chaque emplacement, vous pouvez la laisser par défaut à [appliquer la stratégie à l’intégralité de l’emplacement](#a-policy-that-applies-to-entire-locations), ou [spécifier inclut et exclut](#a-policy-with-specific-inclusions-or-exclusions).

    Informations spécifiques aux emplacements :
    - [Messagerie Exchange et dossiers publics Exchange](#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [Sites SharePoint et comptes OneDrive](#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [Groupes Microsoft 365](#configuration-information-for-microsoft-365-groups)
    - [Skype Entreprise](#configuration-information-for-skype-for-business)

4. Sur la page **Indiquez si vous souhaitez conserver le contenu et/ou le supprimer** de l’assistant, spécifiez les options de configuration pour la conservation et la suppression du contenu.

    Vous pouvez créer une stratégie de rétention qui conserve uniquement le contenu sans le supprimer, conserve puis supprime le contenu après une période donnée, ou supprime simplement le contenu après une période donnée. Si vous souhaitez en savoir plus, consultez [Paramètres pour la conservation et la suppression du contenu](#settings-for-retaining-and-deleting-content) sur cette page.

5. Terminez l’assistant pour enregistrer vos paramètres.

#### <a name="configuration-information-for-exchange-email-and-exchange-public-folders"></a>Informations de configuration pour la messagerie Exchange et les dossiers publics Exchange

L’emplacement **Courrier Exchange** prend en charge la rétention des e-mails, du calendrier et d’autres éléments de boîte aux lettres des utilisateurs en appliquant des paramètres de rétention au niveau d’une boîte aux lettres.

Si vous souhaitez en savoir plus sur les éléments inclus et exclus lors de la configuration des paramètres de rétention d’Exchange, veuillez consulter la rubrique [Éléments composant la rétention et la suppression](retention-policies-exchange.md#whats-included-for-retention-and-deletion).

Notez que,même si un groupe Microsoft 365 a une boîte aux lettres Exchange, une stratégie de rétention qui inclut l’emplacement **Exchange** entier n’inclut pas du contenu dans les boîtes aux lettres de groupe Microsoft 365. Pour conserver le contenu pour un groupe Microsoft 365, vous devez utiliser l’emplacement de **Groupes Microsoft 365**.

L’emplacement **Dossiers publics Exchange** applique les paramètres de rétention à tous les dossiers publics et ne peut pas être appliqué au niveau d’un dossier ou d’une boîte aux lettres.

#### <a name="configuration-information-for-sharepoint-sites-and-onedrive-accounts"></a>Informations de configuration pour les sites SharePoint et les comptes OneDrive

Lorsque vous choisissez l’emplacement **Sites SharePoint**, la stratégie de rétention peut conserver et supprimer les documents des sites de communication SharePoint, des sites d’équipe qui ne sont pas connectés par des groupes Microsoft 365 ainsi que des sites classiques. Les sites d'équipe connectés par des **groupes Microsoft 365** ne sont pas pris en charge par cette option et utilisent plutôt l'emplacement des groupes Microsoft 365 qui s'applique au contenu de la boîte aux lettres, du site et des fichiers du groupe.

Bien que la stratégie de rétention soit appliquée au niveau du site, seuls les documents ont des paramètres de rétention qui leur sont appliqués. Si vous souhaitez en savoir plus sur les éléments inclus et exclus lors de la configuration des paramètres de rétention de SharePoint et OneDrive, veuillez consulter la rubrique [Éléments composant la rétention et la suppression](retention-policies-sharepoint.md#whats-included-for-retention-and-deletion). 

Lorsque vous spécifiez vos emplacements pour les sites SharePoint ou comptes OneDrive, aucune autorisation n’est nécessaire pour accéder au site, et aucune validation n’intervient au moment où vous spécifiez l’URL sur la page **Modifier les emplacements**. Toutefois, les sites SharePoint que vous spécifiez est vérifiée à la fin de l’assistant. Si cette vérification échoue, un message apparaît pour vous informer que la validation de l’URL entrée a échoué, et que l’Assistant ne créera pas la stratégie de rétention tant que la vérification de validation n’aura pas abouti. Si ce message apparaît, revenez à l’assistant pour modifier l’URL ou supprimer le site de la stratégie de rétention.

Pour spécifier l’inclusion ou l’exclusion de comptes OneDrive individuels, l’URL présente le format suivant : `https://<tenant name>-my.sharepoint.com/personal/<user_name>_<tenant name>_com`

Par exemple, pour un utilisateur du client contoso dont le nom d’utilisateur est « rsimone » : `https://contoso-my.sharepoint.com/personal/rsimone_contoso_onmicrosoft_com`

Pour vérifier la syntaxe de votre client et identifier les URL des utilisateurs, voir [Obtenir la liste de toutes les URL OneDrive utilisateur de votre organisation](https://docs.microsoft.com/onedrive/list-onedrive-urls).

### <a name="configuration-information-for-microsoft-365-groups"></a>Informations de configuration pour les Groupes Microsoft 365

Pour conserver ou supprimer le contenu d’un groupe Microsoft 365 (anciennement groupe Office 365), utilisez l’emplacement **Groupes Microsoft 365**. Même si un groupe Microsoft 365 dispose d'une boîte aux lettres Exchange, une politique de conservation qui inclut l'ensemble de l'emplacement du **courrier électronique Exchange** n'inclura pas le contenu des boîtes aux lettres du groupe Microsoft 365. En outre, bien que l'emplacement du **courrier électronique Exchange** vous permette initialement de spécifier une boîte aux lettres de groupe à inclure ou à exclure, lorsque vous essayez d'enregistrer la stratégie de rétention, vous recevez une erreur indiquant que « RemoteGroupMailbox » n'est pas une sélection valable pour l'emplacement Exchange.

La stratégie de rétention d’un groupe Microsoft 365 comprend la boîte aux lettres du groupe et le site d’équipes SharePoint.. Les fichiers stockés sur le site d’équipes SharePoint sont couverts par cet emplacement, à la différence des conversations Teams ou des messages de canal Teams qui ont leur propre emplacements de stratégie de rétention.

### <a name="configuration-information-for-skype-for-business"></a>Informations de configuration de Skype Entreprise

Au contraire de Courrier Exchange, il est impossible de basculer l’état de l’emplacement Skype pour inclure automatiquement tous les utilisateurs : quand cet emplacement est activé, vous devez choisir manuellement les utilisateurs dont vous voulez conserver les conversations :

![Choisir l’emplacement Skype pour les stratégies de rétention](../media/skype-location-retention-policies.png)

En sélectionnant **Choisir un utilisateur**, vous pouvez facilement inclure tous les utilisateurs en sélectionnant le champ **Tout sélectionner**. Toutefois, il est important de comprendre que chaque utilisateur compte comme une inclusion spécifique dans la stratégie. Ainsi, si vous incluez 1 000 utilisateurs en sélectionnant la case **Sélectionner tout**, c'est la même chose que si vous aviez sélectionné manuellement 1 000 utilisateurs à inclure, ce qui est le maximum pris en charge par Skype® Entreprise.

Notez que **Historique des conversations**, un dossier dans Outlook, est une fonctionnalité qui n’a rien à voir avec l’archivage Skype. La fonctionnalité **Historique des conversations** peut être désactivée par l’utilisateur final, mais l’archivage pour Skype s’effectue en stockant une copie des conversations Skype dans un dossier masqué inaccessible à l’utilisateur, mais disponible pour eDiscovery.

## <a name="settings-for-retaining-and-deleting-content"></a>Paramètres pour la conservation et la suppression de contenu

Votre stratégie de rétention aura l’une des configurations suivantes pendant une période donnée lorsque vous sélectionnez les paramètres de conservation et de suppression de contenu :

- Conserver uniquement

    Pour cette configuration, choisissez **Conserver les éléments sur une période spécifique** et **À la fin de la période : ne rien faire** sélectionnez **Conserver les éléments à l’infini**.

- Conserver puis supprimer

    Pour cette configuration, choisissez **Conserver les éléments sur une période spécifique** et **À la fin de la période : supprimer automatiquement**.

- Supprimer uniquement

    Pour cette configuration, choisissez **Ne supprimer les éléments qu’une fois un certain âge atteint**.

### <a name="retaining-content-for-a-specific-period-of-time"></a>Conservation du contenu sur une période donnée

Lors de la configuration d’une stratégie de rétention, choisissez de conserver les éléments pendant un nombre donné de jours, de mois ou d’années. Ou bien de conserver les éléments indéfiniment.

Lors de la configuration d’une stratégie de rétention, vous pouvez choisir de conserver les éléments indéfiniment ou bien pendant un nombre donné de jours, de mois ou d’années. La période de rétention est calculée sur la base de l’âge du contenu et non par rapport à la date d’application de la stratégie de rétention.

Pour le début de la période de rétention, vous pouvez également choisir la date de création du contenu ou bien, pour les fichiers et les locations SharePoint, OneDrive et Office 365 uniquement, la date de dernière modification du contenu.

Exemples :

- SharePoint : Si vous souhaitez conserver des éléments dans une collection de site pendant sept ans après la date de dernière modification du contenu et qu’un document de cette collection de site n’a pas été modifié depuis six ans, celui-ci ne sera conservé que pendant une autre année sauf s’il est modifié entre-temps. Si le document est de nouveau modifié, l’âge du document est calculé à partir de la date de dernière modification, et il sera conservé pendant sept années supplémentaires.

- Exchange : Si vous souhaitez conserver les éléments dans une boîte aux lettres pendant sept ans et qu’un message a été envoyé il y a six ans, celui-ci ne sera conservé que pendant une autre année. Pour les éléments Exchange, l’âge est basé sur la date de réception du courrier entrant et d’envoi du courrier sortant. La rétention d’éléments sur la base de la date de dernière modification ne s’applique qu’au contenu de site sur OneDrive et SharePoint.

Vous pouvez choisir si vous souhaitez que le contenu soit supprimé de façon définitive à la fin de la période de rétention :

![Page Paramètres de rétention](../media/b05f84e5-fc71-4717-8f7b-d06a29dc4f29.png)

### <a name="deleting-content-thats-older-than-a-specific-age"></a>Suppression du contenu antérieur à une date spécifique

Une stratégie de rétention peut conserver puis supprimer des éléments, ou bien supprimer de vieux éléments sans les conserver.

Dans les deux cas, si la stratégie de rétention supprime des éléments, il est important de comprendre que la période donnée de celle-ci est calculée sur la base de la date de création ou de dernière modification, et non sur celle d’assignation de la stratégie.

Ainsi, lorsque vous assignez une stratégie de rétention pour la première fois et tout spécialement si cette stratégie implique la suppression d’éléments, prenez d’abord en considération l’âge du contenu existant et la manière dont cette stratégie peut l’affecter. Pensez également à communiquer sur la nouvelle stratégie avec vos utilisateurs avant de l’assigner afin de leur donner le temps de prendre en compte les effets possibles.

### <a name="a-policy-that-applies-to-entire-locations"></a>Une stratégie qui s’applique à des emplacements entiers

Lorsque vous choisissez des emplacements, à l’exception de Skype Entreprise, le paramètre par défaut est **Tout** lorsque l’état de l’emplacement est **Activé**.

Quand une stratégie de rétention s’applique sur une combinaison d’emplacements entiers, le nombre de destinataires, sites, comptes, groupes, etc., que la stratégie peut inclure n’est pas limité.

Par exemple, si la stratégie inclut tous les courriers électroniques sur Exchange et tous les sites sur SharePoint, tous les sites et destinataires seront inclus, quel qu’en soit le nombre. Pour Exchange, toute nouvelle boîte aux lettres créée après l’application de la stratégie hérite automatiquement de la stratégie.

### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>Une stratégie avec des inclusions ou des exclusions spécifiques

Ce n'est que si vous utilisez la configuration optionnelle pour étendre vos paramètres de conservation à des utilisateurs spécifiques, à des groupes spécifiques de Microsoft 365 ou à des sites spécifiques, qu'il y a certaines limites à respecter : 

- Nombre maximum pour une politique de rétention :
  - 1 000 boîtes aux lettres
  - 1 000 groupes Microsoft 365
  - 1 000 utilisateurs pour conversations privées Teams
  - 100 sites (OneDrive et SharePoint)

Il existe également un nombre maximum de politiques qui sont soutenues pour un locataire : 10,000. Ces éléments incluent les stratégies de rétention, les stratégies d’étiquette de rétention et les stratégies de rétention appliquées automatiquement.

Si vos politiques de conservation sont susceptibles d'être soumises à ces limitations, utilisez la configuration par défaut qui s'applique à l'ensemble du site car ces politiques n'ont aucune limitation.

Pour utiliser la configuration optionnelle afin de définir vos paramètres de conservation, assurez-vous que **le statut** de ce lieu est **activé**, puis utilisez les liens pour inclure ou exclure des utilisateurs, des groupes Microsoft 365 ou des sites spécifiques.

> [!WARNING]
> Si vous configurez inclut et supprimez ensuite le dernier, la configuration revient à **Tout** pour l’emplacement.  Assurez-vous qu'il s'agit bien de la configuration que vous souhaitez avant d'enregistrer la stratégie.
>
> Par exemple, si vous spécifiez un site SharePoint à inclure dans votre stratégie de rétention qui est configurée pour supprimer les données, puis supprimez le site, par défaut, tous les sites SharePoint sont soumis à la stratégie de rétention qui supprime définitivement les données. Il en va de même pour les destinataires Exchange, les comptes OneDrive, les utilisateurs de la conversation Teams, etc.
>
> Dans ce scénario, désactivez le paramètre emplacement si vous ne souhaitez pas que le paramètre **Tout** pour l’emplacement soit soumis à la stratégie de rétention. Vous pouvez également spécifier les exclusions à exempter de la stratégie.

## <a name="updating-retention-policies"></a>Mise à jour des stratégies de rétention

Si vous modifiez une stratégie de rétention et que des éléments y sont déjà sujets aux paramètres originaux, vos paramètres mis à jour seront automatiquement appliqués à ces éléments en plus des éléments qui seront nouvellement identifiés.

En règle générale, cette mise à jour est assez rapide, mais peut prendre plusieurs jours. Lorsque la réplication de la stratégie au sein de vos emplacements Microsoft 365 est terminée, l’état de la stratégie de rétention dans le Centre de conformité Microsoft 365 passe de **Activé (en attente)** à **Activé (opération réussie)**.

## <a name="locking-the-policy-to-prevent-changes"></a>Verrouillage de la stratégie pour empêcher toute modification

Si vous avez besoin de vérifier que personne ne peut désactiver la stratégie, supprimer la stratégie ou la rendre moins restrictive, veuillez consulter la rubrique [Utiliser le Verrou de Conservation pour restreindre les modifications apportées aux stratégies de rétention et aux stratégies d’étiquette de rétention](retention-preservation-lock.md).
