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
ms.openlocfilehash: 9f550aa2e0a79170c4651f29c23a8ed0c8c9b3a4
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52769417"
---
# <a name="create-and-configure-retention-policies"></a>Créer et configurer des stratégies de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Utilisez une stratégie de rétention pour gérer les données de votre organisation en décidant de manière proactive s'il faut conserver le contenu, le supprimer ou le conserver puis le supprimer.

Une stratégie de rétention vous permet de le faire très efficacement en attribuant les mêmes paramètres de rétention au niveau du conteneur pour qu'ils soient automatiquement hérités par le contenu de ce conteneur. Par exemple, tous les éléments des sites SharePoint, tous les messages électroniques dans les boîtes aux lettres Exchange des utilisateurs, tous les messages des canaux pour les équipes qui sont utilisés avec Microsoft Teams. Si vous ne savez pas si vous devez utiliser une stratégie de rétention au niveau du conteneur ou une étiquette de rétention au niveau de l’élément, consultez [Stratégies de rétention et étiquettes de rétention](retention.md#retention-policies-and-retention-labels).

Pour en savoir plus sur les stratégies de rétention et le fonctionnement de la rétention en Microsoft 365, consultez la page [Découvrir les stratégies et étiquettes de rétention](retention.md).

> [!NOTE]
> Les informations sur cette page sont pour les administrateurs de conformité. Si vous n'êtes pas administrateur et que vous souhaitez comprendre comment les stratégies de rétention ont été configurées pour les applications que vous utilisez, contactez votre service d'assistance, votre service informatique ou votre administrateur. Si vous voyez des messages concernant les stratégies de rétention dans les conversations Teams et dans les messages des canaux, vous trouverez peut-être utile d'examiner [Messages Teams concernant les stratégies de rétention](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de votre organisation dispose de toutes les autorisations pour créer et gérer les stratégies de confidentialité. Si vous ne vous connectez pas en tant qu’administrateur général, voir [Autorisations nécessaires pour créer et gérer des stratégies et des étiquettes de confidentialité](get-started-with-retention.md#permissions-required-to-create-and-manage-retention-policies-and-retention-labels).

## <a name="create-and-configure-a-retention-policy"></a>Créer et configurer une stratégie de rétention

Bien qu’une stratégie de rétention puisse prendre en charge plusieurs services identifiés comme « emplacements » dans la stratégie de rétention, vous ne pouvez pas créer une stratégie de rétention unique qui inclut tous les emplacements pris en charge :

- E-mails Exchange
- Site SharePoint
- Comptes OneDrive
- Groupes Microsoft 365
- Skype Entreprise
- Dossiers publics Exchange
- Messages du canal Teams
- Conversations Teams
- Messages communautaires Yammer
- Messages utilisateur de Yammer

Lorsque vous sélectionnez l’emplacement Teams ou Yammer lors de la création d’une stratégie de rétention, les autres emplacements sont automatiquement exclus. Cela signifie que les instructions à suivre varient selon que vous devez inclure les emplacements Teams ou Yammer :

- [Instructions relatives à une stratégie de rétention pour les emplacements Teams](#retention-policy-for-teams-locations)
- [Instructions relatives à une stratégie de rétention pour les emplacements Yammer](#retention-policy-for-yammer-locations)
- [Instructions relatives à une stratégie de rétention pour les emplacements autres que Teams et Yammer](#retention-policy-for-locations-other-than-teams-and-yammer)

Lorsque vous avez plusieurs stratégies de rétention et que vous utilisez également des étiquettes de rétention, voir [Principes de rétention et priorité](retention.md#the-principles-of-retention-or-what-takes-precedence) pour comprendre le résultat lorsque plusieurs paramètres de rétention s’appliquent au même contenu.

### <a name="retention-policy-for-teams-locations"></a>Stratégie de rétention pour les emplacements Teams

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), sélectionnez **Stratégies** > **Retention**.

2. Sélectionnez **Nouvelle stratégie de rétention** pour démarrer l’assistant de création de stratégie de rétention, puis nommez votre nouvelle stratégie de rétention.

3. Pour la page **Sélectionnez les emplacements où appliquer la stratégie**, sélectionnez l’un des deux emplacements suivants sur Teams : **Message du canal Teams** ou **Conversations Teams**.

   Pour **Messages de canal Teams**, les messages provenant des canaux standard sont inclus, contrairement à ceux des [canaux privés](/microsoftteams/private-channels). Les canaux privés ne sont actuellement pas pris en charge par les stratégies de rétention.

   Par défaut, [toutes les équipes et tous les utilisateurs sont sélectionnés](#a-policy-that-applies-to-entire-locations). Vous pouvez toutefois affiner cette sélection grâce aux [options **Choisir** et **Exclure**](#a-policy-with-specific-inclusions-or-exclusions). Toutefois, avant de modifier la valeur par défaut, n’ignorez pas les conséquences suivantes pour une stratégie de rétention qui supprime des messages lorsqu’elle est configurée pour inclut ou exclut :
    
    - Pour les conversations de groupe, étant donné qu'une copie des messages est enregistrée dans la boîte aux lettres de chaque utilisateur participant à la conversation, des copies de messages continueront d'être renvoyées dans les résultats d'eDiscovery pour les utilisateurs auxquels la politique n'a pas été attribuée.
    - Pour les utilisateurs qui n’ont pas reçu la stratégie, les messages supprimés sont renvoyés dans les résultats de recherche de leur Teams, mais n’affichent pas le contenu du message suite à la suppression définitive de la stratégie affectée aux utilisateurs.

4. Sur la page **Indiquez si vous souhaitez conserver le contenu et/ou le supprimer** de l’assistant, spécifiez les options de configuration pour la conservation et la suppression du contenu.

   Vous pouvez créer une stratégie de rétention qui conserve uniquement le contenu sans le supprimer, conserve puis supprime le contenu après une période donnée, ou supprime simplement le contenu après une période donnée. Si vous souhaitez en savoir plus, voir [Paramètres pour la conservation et la suppression du contenu](#settings-for-retaining-and-deleting-content) sur cette page.

5. Terminez l’assistant pour enregistrer vos paramètres.

Pour obtenir des conseils permettant de déterminer quand utiliser les stratégies de rétention pour Teams et comprendre l’expérience de l’utilisateur final, voir [Gérer les stratégies de rétention pour Microsoft Teams](/microsoftteams/retention-policies) dans la documentation Teams.

Pour obtenir des détails techniques sur le fonctionnement de la rétention pour Teams, y compris les éléments de messages pris en charge pour la rétention et le minutage des informations avec des exemples pas à pas, consultez [En savoir plus sur la rétention de Microsoft Teams](retention-policies-teams.md).

#### <a name="known-configuration-issues"></a>Problèmes de configuration connus

- Bien que vous puissiez sélectionner l’option pour démarrer la période de rétention lorsque les éléments ont été modifiés pour la dernière fois, la valeur **Lorsque les éléments ont été créés** est toujours utilisée. Pour les messages qui sont modifiés, une copie du message d’origine est enregistrée avec son timestamp d’origine pour identifier les cas où ce message avant modification a été créé, et le message après modification dispose d’un timestamp plus nouveau.

- Lorsque vous sélectionnez **Choisir les équipes** pour l’emplacement des **messages de canal d’équipes**, les groupes Microsoft 365, qui ne sont pas des équipes, peuvent s’afficher. Ne sélectionnez pas ces groupes.

- Lorsque vous sélectionnez **Choisir les utilisateurs pour l’emplacement des conversations Teams**, les invités et les utilisateurs qui n’utilisent pas de boîte aux lettres peuvent s’afficher. Les stratégies de rétention ne sont pas conçues pour ces utilisateurs. Ne les sélectionnez pas.


#### <a name="additional-retention-policy-needed-to-support-teams"></a>Stratégie de rétention supplémentaire requise pour la prise en charge de Teams

Teams n’est pas seulement des conversations et des messages de canaux. Si vous avez des équipes créées à partir d’un groupe Microsoft 365 (anciennement groupe Office 365), vous devez également configurer une stratégie de rétention qui inclut ce groupe Microsoft 365 à l’aide de l’emplacement **Groupes Microsoft 365**. Cette stratégie de rétention s’applique au contenu de la boîte aux lettres, du site et des fichiers du groupe.

Si vous possédez des sites d’équipe qui ne sont pas connectés à un groupe Microsoft 365, vous avez besoin d’une stratégie de rétention qui inclut les emplacements de **sites SharePoint** ou **comptes OneDrive** pour conserver et supprimer des fichiers dans Teams :

- Les fichiers partagés dans une conversation sont stockés sur le compte OneDrive de l’utilisateur qui a partagé le fichier.

- Les fichiers chargés dans les canaux sont stockés sur le site SharePoint associé à l’équipe.

> [!TIP]
> Vous pouvez appliquer une stratégie de rétention aux fichiers d’une équipe spécifique uniquement lorsque celle-ci n’est pas connectée à un groupe Microsoft 365 en sélectionnant le site SharePoint pour l’équipe, ainsi que les comptes OneDrive des utilisateurs au sein de Teams.

Il est possible qu’une stratégie de conservation appliquée aux groupes Microsoft 365, sites SharePoint ou comptes OneDrive supprime un fichier référencé dans une conversation ou un message de canal Teams avant la suppression de ces messages. Dans ce scénario, le fichier s’affiche encore dans le message Teams, mais lorsque les utilisateurs sélectionnent le fichier, un message d’erreur « fichier introuvable » s’affiche. Ce comportement n’est pas spécifique aux stratégies de rétention et peut également se produire si un utilisateur supprime manuellement un fichier à partir de SharePoint ou de OneDrive.

### <a name="retention-policy-for-yammer-locations"></a>Stratégie de rétention pour les emplacements Yammer

> [!NOTE]
> Les stratégies de rétention pour Yammer sont déployées en version préliminaire. Si vous ne voyez pas encore de nouveaux emplacements pour Yammer, veuillez réessayer dans quelques semaines.
>
> Pour utiliser cette fonctionnalité, votre réseau Yammer doit être [Mode Natif](/yammer/configure-your-yammer-network/overview-native-mode), et non Mode Hybride.

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), sélectionnez **Stratégies** > **Retention**.

2. Sélectionnez **Nouvelle stratégie de rétention** pour créer une stratégie de rétention.

3. Sur la page **Indiquez si vous souhaitez conserver le contenu et/ou le supprimer** de l’assistant, spécifiez les options de configuration pour la conservation et la suppression du contenu. 
    
    Vous pouvez créer une stratégie de rétention qui conserve uniquement le contenu sans le supprimer, conserve puis supprime le contenu après une période donnée, ou supprime simplement le contenu après une période donnée. Si vous souhaitez en savoir plus, voir [Paramètres pour la conservation et la suppression du contenu](#settings-for-retaining-and-deleting-content) sur cette page.
    
    Ne sélectionnez pas **Utiliser les paramètres de rétention avancée**, car cette option n’est pas prise en charge pour les emplacements Yammer. 

4. Sur la page **Choisir les emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**. Basculez ensuite sur l’un ou les deux emplacements de Yammer: **message de communauté Yammer** et **messages utilisateur Yammer**.
    
    Par défaut, tous les utilisateurs et communautés sont sélectionnés, mais vous pouvez les affiner en spécifiant les groupes et les utilisateurs à inclure ou à exclure.
    
    Pour les messages privés Yammer : 
    - Si vous conservez la valeur par défaut à **Tous**, les utilisateurs invités B2B Azure ne sont pas inclus. 
    - Vous pouvez appliquer une stratégie de rétention à des utilisateurs externes si vous sélectionnez **Choisir Utilisateur**.

5. Terminez l’assistant pour enregistrer vos paramètres.

Pour en savoir plus sur le fonctionnement des stratégies de rétention pour Yammer, consultez la page [Découvrir les stratégies de rétention pour Yammer](retention-policies-yammer.md).

#### <a name="additional-retention-policies-needed-to-support-yammer"></a>Stratégies de rétention supplémentaires requises pour la prise en charge de Yammer

Yammer est bien plus que des messages de la communauté et des messages privés. Pour conserver et supprimer des courriers électroniques pour votre réseau Yammer, configurez une stratégie de rétention supplémentaire qui inclut les groupes Microsoft 365 utilisés pour Yammer, à l’aide de l'emplacement **Groupes Microsoft 365**. 

Pour retenir et supprimer les fichiers qui sont stockés dans Yammer, vous avez besoin d’une stratégie de rétention qui inclut les emplacements **Des sites SharePoint** ou **Des comptes OneDrive**:

- Les fichiers partagés dans les messages privés sont stockés sur le compte OneDrive de l’utilisateur qui a partagé le fichier. 

- Les fichiers chargés dans les communautés sont stockés sur le site SharePoint pour la communauté Yammer.

Il est possible qu’une stratégie de rétention appliquée à des comptes SharePoint ou OneDrive supprime un fichier référencé dans un message Yammer avant la suppression de ces messages. Dans ce scénario, le fichier s’affiche encore dans le message Yammer, mais lorsque les utilisateurs sélectionnent le fichier, un message d’erreur « fichier introuvable » s’affiche. Ce comportement n’est pas spécifique aux stratégies de rétention et peut également se produire si un utilisateur supprime manuellement un fichier à partir de SharePoint ou de OneDrive.

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a>Stratégie de rétention pour les emplacements autres que Teams et Yammer

Utilisez les instructions suivantes pour les stratégies de rétention qui s’appliquent ces services:

- Exchange: Email et dossiers publics
- Sites SharePoint
- OneDrive: Comptes
- Groupes Microsoft 365
- Skype Entreprise

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), sélectionnez **Stratégies** > **Retention**.

2. Sélectionnez **Nouvelle stratégie de rétention** pour démarrer l’assistant de création de stratégie de rétention, puis nommez votre nouvelle stratégie de rétention.

3. Pour la page **Choisir les emplacements**, activez ou désactivez les emplacements, à l’exception des emplacements de Teams. Vous pouvez laisser pour chaque emplacement la valeur par défaut [Appliquer la stratégie à l’intégralité de l’emplacement](#a-policy-that-applies-to-entire-locations) ou [Spécifier des inclusions et des exclusions](#a-policy-with-specific-inclusions-or-exclusions).

    Informations spécifiques aux emplacements :
    - [Messagerie Exchange et dossiers publics Exchange](#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [Sites SharePoint et comptes OneDrive](#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [Groupes Microsoft 365](#configuration-information-for-microsoft-365-groups)
    - [Skype Entreprise](#configuration-information-for-skype-for-business)

4. Sur la page **Indiquez si vous souhaitez conserver le contenu et/ou le supprimer** de l’assistant, spécifiez les options de configuration pour la conservation et la suppression du contenu.

    Vous pouvez créer une stratégie de rétention qui conserve uniquement le contenu sans le supprimer, conserve puis supprime le contenu après une période donnée, ou supprime simplement le contenu après une période donnée. Si vous souhaitez en savoir plus, voir [Paramètres pour la conservation et la suppression du contenu](#settings-for-retaining-and-deleting-content) sur cette page.

5. Terminez l’assistant pour enregistrer vos paramètres.

#### <a name="configuration-information-for-exchange-email-and-exchange-public-folders"></a>Informations de configuration pour la messagerie Exchange et les dossiers publics Exchange

L’emplacement **Courrier Exchange** prend en charge la rétention du courrier électronique, du calendrier et d’autres éléments de boîte aux lettres des utilisateurs en appliquant des paramètres de rétention au niveau d’une boîte aux lettres.

Si vous souhaitez en savoir plus sur les éléments inclus et exclus lors de la configuration des paramètres de rétention d’Exchange, veuillez consulter la rubrique [Éléments composant la rétention et la suppression](retention-policies-exchange.md#whats-included-for-retention-and-deletion).

Notez que même si un groupe Microsoft 365 possède une boîte aux lettres Exchange, une stratégie de rétention qui inclut l’ensemble de l’emplacement **Courrier Exchange** n’inclut pas le contenu des boîtes aux lettres du groupe Microsoft 365. Pour conserver le contenu de ces boîtes aux lettres, sélectionnez l’emplacement **Groupes Microsoft 365**.

L’emplacement **Dossiers publics Exchange** applique les paramètres de rétention à tous les dossiers publics et ne peut pas être appliqué au niveau d’un dossier ou d’une boîte aux lettres.

#### <a name="configuration-information-for-sharepoint-sites-and-onedrive-accounts"></a>Informations de configuration pour les sites SharePoint et les comptes OneDrive

Lorsque vous choisissez l’emplacement **Sites SharePoint**, la stratégie de rétention peut conserver et supprimer les documents des sites de communication SharePoint, des sites d’équipe qui ne sont pas connectés par des groupes Microsoft 365 ainsi que des sites classiques. Cette option ne prend pas en charge les sites d’équipe connectés par des groupes Microsoft 365. Utilisez plutôt des emplacements de **groupes Microsoft 365** qui s’appliquent au contenu de la boîte aux lettres, du site et des fichiers du groupe.

Bien que la stratégie de rétention s’applique au niveau du site, seuls les documents ont des paramètres de rétention qui leur sont appliqués. Si vous souhaitez en savoir plus sur les éléments inclus et exclus lors de la configuration des paramètres de rétention de SharePoint et OneDrive, veuillez consulter la rubrique [Éléments composant la rétention et la suppression](retention-policies-sharepoint.md#whats-included-for-retention-and-deletion). 

Lorsque vous spécifiez vos emplacements pour les sites SharePoint ou comptes OneDrive, aucune autorisation n’est nécessaire pour accéder au site, et aucune validation n’intervient au moment où vous spécifiez l’URL sur la page **Modifier les emplacements**. Toutefois, les sites SharePoint que vous spécifiez est vérifiée à la fin de l’assistant. Si cette vérification échoue, un message apparaît pour vous informer que la validation de l’URL entrée a échoué, et que l’Assistant ne créera pas la stratégie de rétention tant que la vérification de validation n’aura pas abouti. Si ce message apparaît, revenez à l’assistant pour modifier l’URL ou supprimer le site de la stratégie de rétention.

Pour spécifier l’inclusion ou l’exclusion de comptes OneDrive individuels, l’URL présente le format suivant : `https://<tenant name>-my.sharepoint.com/personal/<user_name>_<tenant name>_com`

Par exemple, pour un utilisateur du client contoso dont le nom d’utilisateur est « rsimone » : `https://contoso-my.sharepoint.com/personal/rsimone_contoso_onmicrosoft_com`

Pour vérifier la syntaxe de votre client et identifier les URL des utilisateurs, voir [Obtenir la liste de toutes les URL OneDrive utilisateur de votre organisation](/onedrive/list-onedrive-urls).

### <a name="configuration-information-for-microsoft-365-groups"></a>Informations de configuration pour les Groupes Microsoft 365

Pour conserver ou supprimer le contenu d’un groupe Microsoft 365 (anciennement groupe Office 365), utilisez l’emplacement **Groupes Microsoft 365**. Même si un groupe Microsoft 365 possède une boîte aux lettres Exchange, une stratégie de rétention qui inclut l’ensemble de l’emplacement de la **messagerie Exchange** n’inclut pas le contenu des boîtes aux lettres du groupe Microsoft 365. Bien que l’emplacement de la **messagerie Exchange** vous permette initialement de spécifier une boîte aux lettres de groupe à inclure ou à exclure, vous recevez une erreur indiquant que « RemoteGroupMailbox » n’est pas une sélection valide pour l’emplacement Exchange, lorsque vous essayez d’enregistrer la stratégie de rétention.

Par défaut, la stratégie de rétention d’un groupe Microsoft 365 comprend la boîte aux lettres de groupe et le site d’équipes SharePoint.. Les fichiers stockés sur le site d’équipes SharePoint sont couverts par cet emplacement, à la différence des conversations Teams ou des messages de canal Teams qui ont leur propre emplacements de stratégie de rétention.

Pour modifier la valeur par défaut afin que la stratégie de rétention s’applique uniquement aux boîtes aux lettres Microsoft 365 ou aux sites d’équipe SharePoint connectés, utilisez l’applet de commande PowerShell [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) avec le paramètre *Applications* avec l’une des valeurs suivantes :

- `Group:Exchange` pour les boîtes aux lettres Microsoft 365 uniquement connectées au groupe.
- `Group:SharePoint` pour les sites SharePoint uniquement connectées au groupe.

Pour revenir à la valeur par défaut de la boîte aux lettres et du site SharePoint pour les groupes Microsoft 365 sélectionnés, spécifiez `Group:Exchange,SharePoint`.

### <a name="configuration-information-for-skype-for-business"></a>Informations de configuration de Skype Entreprise

Contrairement à d’autres emplacements, vous ne pouvez pas activer ou désactiver l’état de l’emplacement Skype pour inclure automatiquement tous les utilisateurs. Au lieu de cela, lorsque vous activez cet emplacement, vous devez sélectionner l’option **Modifier** pour choisir manuellement les utilisateurs dont vous souhaitez conserver les conversations :

![Choisir l’emplacement Skype pour les stratégies de rétention](../media/skype-location-retention-policies.png)

Après avoir sélectionné cette option **Modifier**, dans le volet **Skype Entreprise**, vous pouvez inclure rapidement tous les utilisateurs en sélectionnant la zone masquée avant la colonne **Nom**. Toutefois, il est important de comprendre que chaque utilisateur compte comme une inclusion particulière dans la stratégie. Par conséquent, si vous incluez 1 000 utilisateurs en sélectionnant cette zone équivaut à sélectionner manuellement 1 000 utilisateurs à inclure, ce qui est le maximum pris en charge pour Skype Entreprise.

Notez que le dossier Outlook **Historique des conversations** est un composant qui n’a rien à voir avec l’archivage de Skype. L’**historique des conversations** peut être désactivé par l’utilisateur final, mais l’archivage de Skype s’effectue par le stockage d’une copie des conversations Skype dans un dossier masqué qui n’est pas accessible par l’utilisateur mais est visible par eDiscovery.

## <a name="settings-for-retaining-and-deleting-content"></a>Paramètres pour la conservation et la suppression de contenu

Votre stratégie de rétention aura l’une des configurations suivantes pendant une période donnée lorsque vous sélectionnez les paramètres de conservation et de suppression de contenu :

- Conserver uniquement

    Pour cette configuration, choisissez **Conserver les éléments sur une période spécifique** et **À la fin de la période : ne rien faire**. Ou bien sélectionnez **Conserver les éléments indéfiniment**.

- Conserver puis supprimer

    Pour cette configuration, choisissez **Conserver les éléments sur une période spécifique** et **À la fin de la période : supprimer automatiquement**.

- Supprimer uniquement

    Pour cette configuration, choisissez **Ne supprimer les éléments qu’une fois un certain âge atteint**.

### <a name="retaining-content-for-a-specific-period-of-time"></a>Conservation du contenu sur une période donnée

Lors de la configuration d’une stratégie de rétention, choisissez de conserver les éléments pendant un nombre donné de jours, de mois ou d’années. Ou bien de conserver les éléments indéfiniment.

Lors de la configuration d’une stratégie de rétention, vous pouvez choisir de conserver les éléments indéfiniment ou bien pendant un nombre donné de jours, de mois ou d’années. La période de rétention est calculée sur la base de l’âge du contenu et non par rapport à la date d’application de la stratégie de rétention.

Pour le début de la période de rétention, vous pouvez choisir la date de création ou de la prise en charge du contenu uniquement pour les fichiers et les emplacements SharePoint, OneDrive et Office 365, pour la date de la dernière modification du contenu.

Exemples :

- SharePoint : si vous souhaitez conserver des éléments dans une collection de site pendant sept ans après la date de dernière modification du contenu et qu’un document de cette collection de site n’a pas été modifié depuis six ans, celui-ci ne sera conservé que pendant une autre année sauf s’il est modifié entre-temps. Si le document est de nouveau modifié, l’âge du document est calculé à partir de la date de dernière modification, et il sera conservé pendant sept années supplémentaires.

- Exchange : Si vous souhaitez conserver les éléments dans une boîte aux lettres pendant sept ans et qu’un message a été envoyé il y a six ans, celui-ci ne sera conservé que pendant une autre année. Pour les éléments Exchange, l’âge est basé sur la date de réception du courrier entrant et d’envoi du courrier sortant. La rétention d’éléments sur la base de la date de dernière modification ne s’applique qu’au contenu de site sur OneDrive et SharePoint.

Vous pouvez choisir si vous souhaitez que le contenu soit supprimé de façon définitive à la fin de la période de rétention :

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

Sachez que si vous utilisez la configuration optionnelle pour étendre vos paramètres de rétention à des utilisateurs spécifiques, des groupes Microsoft 365 spécifiques ou des sites spécifiques, il faut tenir compte de certaines limites par politique. Pour plus d’informations, voir [En savoir plus sur les stratégies et les étiquettes de rétention](retention-limits.md). 

Pour utiliser la configuration optionnelle afin de définir vos paramètres de conservation, assurez-vous que **le statut** de ce lieu est **activé**, puis utilisez les liens pour inclure ou exclure des utilisateurs, des groupes Microsoft 365 ou des sites spécifiques.

> [!WARNING]
> Si vous configurez inclut et supprimez ensuite le dernier, la configuration revient à **Tout** pour l’emplacement.  Assurez-vous qu'il s'agit bien de la configuration que vous souhaitez avant d'enregistrer la stratégie.
>
> Par exemple, si vous spécifiez un site SharePoint à inclure dans votre stratégie de rétention qui est configurée pour supprimer les données, puis supprimez le site, par défaut, tous les sites SharePoint sont soumis à la stratégie de rétention qui supprime définitivement les données. Il en va de même pour les destinataires Exchange, les comptes OneDrive, les utilisateurs de la conversation Teams, etc.
>
> Dans ce scénario, désactivez le paramètre emplacement si vous ne souhaitez pas que le paramètre **Tout** pour l’emplacement soit soumis à la stratégie de rétention. Vous pouvez également spécifier les exclusions à exempter de la stratégie.

## <a name="updating-retention-policies"></a>Mise à jour des stratégies de rétention

Certains paramètres ne peuvent pas être modifiés une fois la stratégie de rétention créée et enregistrée, notamment :
- Le nom de la stratégie de rétention et les paramètres de rétention à l’exception de la période de rétention et le début de la période de rétention.

Si vous modifiez une stratégie de rétention et que des éléments y sont déjà sujets aux paramètres originaux, vos paramètres mis à jour seront automatiquement appliqués à ces éléments en plus des éléments qui seront nouvellement identifiés.

En règle générale, cette mise à jour est assez rapide, mais peut prendre plusieurs jours. Lorsque la réplication de la stratégie au sein de vos emplacements Microsoft 365 est terminée, l’état de la stratégie de rétention dans le Centre de conformité Microsoft 365 passe de **Activé (en attente)** à **Activé (opération réussie)**.

## <a name="locking-the-policy-to-prevent-changes"></a>Verrouillage de la stratégie pour empêcher toute modification

Si vous avez besoin de vérifier que personne ne peut désactiver la stratégie, supprimer la stratégie ou la rendre moins restrictive, veuillez consulter la rubrique [Utiliser le Verrou de Conservation pour restreindre les modifications apportées aux stratégies de rétention et aux stratégies d’étiquette de rétention](retention-preservation-lock.md).
