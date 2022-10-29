---
title: Passage d’une offre Microsoft 365 E à une offre Microsoft 365 F
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: conceptual
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez les éléments à prendre en compte et comment vous préparer si vous basculez certains de vos utilisateurs d’un Microsoft 365 E vers une offre Microsoft 365 F.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_FLW
- m365-frontline
- highpri
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 4b8580759cef1319a53eb425d20a2b0fb87d7016
ms.sourcegitcommit: 0ad7edcfdcdd11d02fa8a14ffe4b36e120d92deb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2022
ms.locfileid: "68786670"
---
# <a name="changing-from-a-microsoft-365-e-plan-to-a-microsoft-365-f-plan"></a>Passage d’une offre Microsoft 365 E à une offre Microsoft 365 F

Si vous envisagez de basculer certains de vos utilisateurs d’une offre Microsoft 365 E vers une offre Microsoft 365 [F3](https://www.microsoft.com/microsoft-365/enterprise/f3) ou [F1](https://www.microsoft.com/microsoft-365/enterprise/f1), cet article fournit des conseils pour vous aider à préparer votre organisation à la modification. Le passage d’une offre E à une offre F affecte les services et fonctionnalités auxquels les utilisateurs ont accès.

Les offres E sont destinées aux travailleurs de l’information (employés qui travaillent généralement à un bureau) et les offres F sont destinées aux employés de première ligne (employés en déplacement, souvent sur des appareils mobiles et qui travaillent directement avec des clients ou le grand public). Chaque offre peut continuer à évoluer au fil du temps pour devenir plus adaptée aux travailleurs de l’information et aux travailleurs de première ligne, respectivement. Pour plus d’informations, consultez [Comprendre les types d’utilisateurs employés de première ligne et les licences](flw-licensing-options.md).

Vous obtenez une vue d’ensemble de ce à quoi s’attendre lorsque les utilisateurs basculent vers une offre F, comment préparer la modification et ce qu’il faut faire après avoir basculé les offres pour faire passer les employés de première ligne de votre organisation.

## <a name="understand-the-key-differences-between-e-and-f-plans"></a>Comprendre les principales différences entre les offres E et F

Commencez par vous familiariser avec les différences de service et de fonctionnalité entre les offres.

Voici quelques-unes des principales différences :

- Les offres F n’incluent pas les applications de bureau Office ou l’application de bureau Outlook.
- Les offres F sont limitées aux appareils avec des écrans intégrés de moins de 10,1 pouces sur les applications mobiles Office.
- Les offres F [épinglent les applications de travail de première ligne](pin-teams-apps-based-on-license.md) telles que Walkie Talkie, Tasks, Shifts et Approvals par défaut dans Microsoft Teams.

Dans cette section, nous avons inclus plus d’informations sur ces principales différences et mis en évidence certaines différences supplémentaires à prendre en compte. N’oubliez pas qu’il ne s’agit pas d’une liste complète. Pour en savoir plus :

- Consultez [la comparaison des offres de travail modernes](https://go.microsoft.com/fwlink/p/?linkid=2139145) pour obtenir une comparaison détaillée de ce qui est inclus dans les offres E et F.
- Consultez [la disponibilité des services](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options#service-availability-within-each-microsoft-365-and-office-365-plan) et [des fonctionnalités entre les offres](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description#feature-availability-across-some-plans) pour obtenir la liste des fonctionnalités et des services disponibles dans les offres E et F.

### <a name="office-apps"></a>Applications Office

Les applications de bureau Office ne sont pas incluses dans les offres F3 et F1. Vos employés de première ligne peuvent utiliser Office sur le Web et les applications mobiles Office pour accomplir vos tâches. Gardez à l’esprit que les utilisateurs F3 ont un accès complet aux documents dans Office sur le Web et que les utilisateurs de F1 ont un accès en lecture seule.

|Service ou fonctionnalité|Microsoft 365 E3/E5  |Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Applications de bureau Office (Word, Excel, OneNote, PowerPoint, Access, Publisher)|Oui|Non|Non|
|Office sur le Web (Word, Excel, OneNote, PowerPoint)|Oui|Oui|Lecture seule|
|Applications mobiles Office (Word, Excel, PowerPoint, Outlook, OneNote)|Oui|Oui&sup1;|Lecture seule|

&sup1; Modification des fichiers pris en charge sur les appareils avec des écrans intégrés de moins de 10,1 pouces.

#### <a name="office-for-the-web"></a>Office pour le web

Avec Office sur le Web, vos employés de première ligne utilisent un navigateur web pour ouvrir des fichiers Word, Excel, OneNote et PowerPoint.

Voici quelques différences à connaître lors de l’utilisation de Office sur le Web. Pour obtenir une comparaison détaillée des fonctionnalités entre les applications de bureau Office sur le Web et Office, consultez [Description du service Office sur le Web](/office365/servicedescriptions/office-online-service-description/office-online-service-description).

|Service ou fonctionnalité|Quelques différences |En savoir plus|
|---------|---------|---------|
|**Word pour le web**|<ul><li> Peut ouvrir et modifier des documents prenant en charge les macros (.docm) et des modèles (.dotm), mais les macros ne s’exécutent pas.</li><li>Peut ouvrir, mais pas modifier, les documents protégés par la Gestion des droits relatifs à l’information (IRM) de l’utilisateur (UDP).</li></ul>|<ul><li>[Description du service Office pour le web](/office365/servicedescriptions/office-online-service-description/word-online)</li><li>[Différences entre l’utilisation d’un document dans le navigateur et dans Word](https://support.microsoft.com//office/differences-between-using-a-document-in-the-browser-and-in-word-3e863ce3-e82c-4211-8f97-5b33c36c55f8)</li></ul>|
|**Excel pour le web**|<ul><li>Peut ouvrir et modifier des classeurs prenant en charge les macros (.xlsm), mais les macros ne s’exécutent pas.</li><li>[Limitations de taille de fichier](https://support.microsoft.com/office/file-size-limits-for-workbooks-in-sharepoint-9e5bc6f8-018f-415a-b890-5452687b325e)<ul><li>Pour afficher ou interagir avec un classeur stocké dans SharePoint Online, le classeur doit être inférieur à 100 Mo. </li><li>Pour ouvrir un classeur joint à un e-mail dans Outlook sur le web, le classeur doit être inférieur à 10 Mo.</li></ul></ul>|<ul><li>[Description du service Excel pour le web](/office365/servicedescriptions/office-online-service-description/excel-online)</li><li>[Différences entre l'utilisation d'un classeur dans le navigateur et dans Excel](https://support.microsoft.com/office/differences-between-using-a-workbook-in-the-browser-and-in-excel-f0dc28ed-b85d-4e1d-be6d-5878005db3b6)</li><li>La plupart des fonctions Excel fonctionnent dans un navigateur comme dans Excel. Pour obtenir la liste des exceptions, consultez [Fonctions dans Excel et dans Excel sur le Web](https://support.microsoft.com/office/differences-between-using-a-workbook-in-the-browser-and-in-excel-f0dc28ed-b85d-4e1d-be6d-5878005db3b6#__functions).</li></ul>|
|**OneNote pour le web**|<ul><li>La recherche est limitée à la section actuelle.</li><li>Le zoom avant et arrière n’est pas disponible. Au lieu de cela, les utilisateurs peuvent utiliser la fonctionnalité de zoom de leur navigateur.</li></ul>|<ul><li>[Description du service OneNote pour le web](/office365/servicedescriptions/office-online-service-description/onenote-online)</li><li>[Différences entre l’utilisation d’un bloc-notes dans le navigateur et dans OneNote](https://support.microsoft.com/office/differences-between-using-a-notebook-in-the-browser-and-in-onenote-a3d1fc13-ac74-456b-b391-b633a62aa83f)</li></ul>|
|**PowerPoint pour le web**|<ul><li>Peut ouvrir des fichiers jusqu’à 2 Go.</li><li>Peut ouvrir et modifier des présentations prenant en charge les macros (.pptm, .potm, .ppsm), mais les macros ne s’exécutent pas.</li></ul>|<ul><li>[Description du service PowerPoint pour le web](/office365/servicedescriptions/office-online-service-description/powerpoint-online)</li><li>[Comportement de certaines fonctionnalités dans PowerPoint basé sur le web](https://support.microsoft.com/office/how-certain-features-behave-in-web-based-powerpoint-a931f0c8-1305-4428-8f7c-9cfa00ef28c5)</li></ul>|

#### <a name="office-mobile"></a>Office mobile

Vos employés de première ligne peuvent obtenir Office sur leurs appareils mobiles de deux manières :

- Installez l’application mobile Office qui combine Word, Excel et PowerPoint.
- Installez des applications mobiles Office individuelles pour Word, Excel, PowerPoint et OneNote.

Pour en savoir plus, consultez [Installer et configurer Office sur un appareil Android](https://support.microsoft.com/office/install-and-set-up-office-on-an-android-cafe9d6f-8b0c-4b03-b20a-12438a82a22d) et [Installer et configurer Office sur un iPhone ou iPad](https://support.microsoft.com/office/install-and-set-up-office-on-an-iphone-or-ipad-9df6d10c-7281-4671-8666-6ca8e339b628).

Pour plus d’informations sur les fonctionnalités disponibles dans Office Mobile, consultez [Ce que vous pouvez faire dans les applications Office sur les appareils mobiles avec un abonnement Microsoft 365](https://support.microsoft.com/office/what-you-can-do-in-the-office-apps-on-mobile-devices-with-a-microsoft-365-subscription-9ef8b63a-05fd-4f9c-bac5-29da046833ea).

#### <a name="email"></a>E-mail

Les utilisateurs F3 disposent d’une boîte aux lettres de 2 Go auxquelles ils peuvent accéder via Outlook sur le web. Pour obtenir une comparaison des fonctionnalités entre Outlook sur le web et l’application de bureau Outlook, consultez [Comparer Outlook pour PC, Outlook sur le web et Outlook pour iOS & Android](https://support.microsoft.com/office/compare-outlook-for-pc-outlook-on-the-web-and-outlook-for-ios-android-b26a7bf5-0ac7-48ba-97af-984e0645dde5).

Les utilisateurs F1 n’ont pas de droits de boîte aux lettres. Bien qu’une boîte aux lettres soit approvisionnée pour les utilisateurs via l’offre Kiosque Exchange, ils ne sont pas autorisés à l’utiliser. Nous vous recommandons de [désactiver Outlook sur le web](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-outlook-web-app) pour les utilisateurs F1.

|Service ou fonctionnalité|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Boîte aux lettres Exchange Online|Oui (boîte aux lettres de 100 Go)|Oui (boîte aux lettres de 2 Go)|Non&sup1;|
|Application de bureau Outlook|Oui|Non|Non|
|Boîte aux lettres d'archivage|Oui|Non|Non|
|Accès délégué|Oui|Non|Non|

&sup1; F1 inclut l’offre Kiosque Exchange pour activer le calendrier Teams uniquement et n’inclut pas les droits de boîte aux lettres.

Pour en savoir plus, consultez [Description du service Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description).

#### <a name="teams"></a>Teams

Les offres F3 et F1 incluent l’application de bureau Teams, l’application mobile et l’application web pour la communication et la collaboration de travail de première ligne. Vos employés de première ligne ont accès aux fonctionnalités de Teams, notamment aux réunions, aux conversations, aux canaux, au contenu et aux applications. Toutefois, ils ne seront pas en mesure de créer des événements en direct et des webinaires ou d’utiliser les fonctionnalités de Téléphone Teams.

|Service ou fonctionnalité|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Événements en direct|Oui|Non|Non|
|Séminaires web|Oui|Non|Non|
|Téléphone Teams|Oui|Non|Non|

#### <a name="sharepoint"></a>SharePoint

Les utilisateurs F3 et F1 peuvent collaborer sur des documents et accéder à des ressources à l’échelle de l’organisation, telles que des supports de formation stockés dans SharePoint. N’oubliez pas que les offres F3 et F1 n’incluent pas les boîtes aux lettres de site ou les sites personnels.

|Service ou fonctionnalité|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Site mailbox|Oui|Non|Non|
|Site personnel |Oui|Non|Non|

Pour en savoir plus sur les limites de SharePoint, consultez [Limites de SharePoint](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits).

#### <a name="content-services"></a>Services de contenu

Les utilisateurs F3 et F1 disposent de 2 Go de stockage OneDrive pour stocker et partager des fichiers. Pour en savoir plus, consultez [la description du service OneDrive](/office365/servicedescriptions/onedrive-for-business-service-description).

|Service ou fonctionnalité|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|OneDrive|Stockage illimité&sup1 ;|2 Go de stockage|2 Go de stockage|
|Microsoft Stream|Oui|Oui&sup2;|Oui&sup2;|
|Sway|Oui|Oui|Non|
|Visio pour le web|Oui|Oui|Lecture seule|
|Delve|Oui|Non|Non|

&sup1; Jusqu’à 5 To de stockage OneDrive initial par utilisateur en fonction du [quota par défaut](/onedrive/set-default-storage-space) du client pour les abonnements de plus de cinq utilisateurs. Vous pouvez demander davantage de stockage.</br>
&sup2; Les utilisateurs peuvent enregistrer des réunions et consommer du contenu Stream, mais ne peuvent pas publier ou partager dans Stream.

#### <a name="insights-and-analytics"></a>Informations et analyses

|Service ou fonctionnalité|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Viva Insights|Oui|Non|Non|
|Power BI|Oui|Non|Non|

#### <a name="work-management-and-automation"></a>Gestion et automatisation du travail

|Service ou fonctionnalité|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Power Apps|Oui|Oui|Non|
|Power Automate|Oui|Oui|Non|
|Power Virtual Agents|Oui|Oui|Non|
|Dataverse pour Teams|Oui|Oui|Non|
|Microsoft Forms|Oui&sup1;|Oui&sup1;|Non|
|Microsoft To-Do|Oui|Oui|Non|

&sup1; Les utilisateurs sous licence peuvent créer, partager et gérer des formulaires. Une licence n’est pas nécessaire pour remplir ou répondre à un formulaire.

#### <a name="windows"></a>Windows

|Service ou fonctionnalité|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Windows 11 Entreprise|Oui|Oui&sup1;|Non|

&sup1; Aucun Canal de maintenance à long terme (LTSC) ou MDOP (Microsoft Desktop Optimization Pack). Infrastructure de bureau virtuel (VDI) uniquement pour les utilisateurs sous licence d’un appareil partagé avec une qualité de service (QoS), (à l’exception d’Azure Virtual Desktop).

## <a name="what-to-expect"></a>À quoi s'attendre

Le tableau suivant répertorie les éléments importants à prendre en compte et les actions recommandées à prendre pendant le processus de modification. Utilisez ces informations pour vous aider à identifier ce qu’il faut faire avant le commutateur et ce qu’il faut planifier une fois le commutateur terminé. 

Nous allons faire référence à ce tableau dans les sections ultérieures de cet article.

|Service ou fonctionnalité |Avant le changement|Après le changement|
|---------|---------|---------|
|Applications Office| <ul><li>Identifiez les fichiers stockés sur les ordinateurs locaux des utilisateurs et aidez les utilisateurs à les déplacer vers leur OneDrive.</li><li>N’oubliez pas que les applications de bureau Office passeront en mode de fonctionnalités réduites après la modification d’une offre F. Préparez-vous à désinstaller les applications de bureau Office après le changement.</li></ul>| Utilisateurs :</br> <ul><li>Connectez-vous à [office.com](https://www.office.com) pour accéder à Office sur le Web.</li><li>[Installez et utilisez des applications mobiles Office](https://support.microsoft.com/office/set-up-office-apps-and-email-on-a-mobile-device-7dabb6cb-0046-40b6-81fe-767e0b1f014f) (si ce n’est pas déjà fait).</li><li>Les utilisateurs peuvent également collaborer directement sur des documents à partir de bibliothèques de documents SharePoint, OneDrive, Teams et Yammer.</li></ul>Administrateurs :<ul><li>Désinstallez les applications de bureau Office des ordinateurs des utilisateurs.</li></ul>      |
|E-mail, Exchange, Outlook|<ul><li>Identifiez les boîtes aux lettres utilisateur de plus de 2 Go à l’aide de l’applet de commande Exchange PowerShell [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics?view=exchange-ps), puis réduisez la taille de boîte aux lettres, si nécessaire. Pour plus d’informations, consultez [Limites de stockage des boîtes aux lettres dans Outlook sur le web](https://support.microsoft.com/office/mailbox-storage-limits-in-outlook-on-the-web-f170fe90-b859-4034-bcda-e186fc6a26f5).</li><li>Si les utilisateurs disposent d’une boîte aux lettres d’archivage :</li><ul><li>Déplacez le contenu de la boîte aux lettres d’archivage vers la boîte aux lettres de l’utilisateur.</li><li>Recherchez toutes les stratégies d’archivage qui peuvent déplacer automatiquement le courrier en fonction de l’âge des messages à l’aide de l’applet de commande Exchange Online PowerShell [Get-EXOMailbox](/powershell/module/exchange/get-exomailbox?view=exchange-ps).</li></ul> <li>Identifiez l’accès et l’utilisation de la boîte aux lettres de site.</li><li>Application de bureau Outlook, données et configuration :</li><ul><li>Identifiez les utilisateurs et les ordinateurs qui utilisent des fichiers de données Outlook (.pst).</li><li>Identifiez et documentez les règles clientes Outlook existantes uniquement.</li><li>Exportez les signatures par e-mail.</li></ul></ul>|Utilisateurs :</br><ul><li>Connectez-vous à [office.com](https://www.office.com) pour accéder à Outlook sur le web.</li><li>[Configurer l’e-mail sur les appareils mobiles](https://support.microsoft.com/office/set-up-office-apps-and-email-on-a-mobile-device-7dabb6cb-0046-40b6-81fe-767e0b1f014f) (si ce n’est pas déjà fait).</li><li>Vérifiez et mettez à jour les signatures de courrier.</li><li>Vérifiez et mettez à jour les règles de boîte aux lettres.</li></ul>Administrateurs :<ul><li> [Désactivez Outlook sur le web](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-outlook-web-app) pour les utilisateurs F1 et demandez-leur de ne pas accéder à la boîte aux lettres par le biais d’autres méthodes.</li></ul>|
|Teams | <ul><li>Identifiez l’utilisation des événements en direct et des webinaires.</li><li>Identifiez les utilisateurs pour qui Teams Phone est activé. Si les utilisateurs utilisent cette fonctionnalité, il se peut qu’ils ne soient pas l’ensemble approprié d’utilisateurs pour passer à une offre F.</li></ul>      ||
|OneDrive | <ul><li>Identifiez les utilisateurs qui utilisent plus ou près de 2 Go de stockage. (OneDrive devient en lecture seule pour les utilisateurs qui dépassent la limite de 2 Go après le passage à une offre F.)</li><li>Aider les utilisateurs à réduire le nombre de fichiers stockés dans OneDrive et la quantité globale de stockage utilisée.</li><li>Assurez-vous que tous les fichiers sont entièrement synchronisés entre les ordinateurs des utilisateurs et OneDrive.</li></ul>| |

## <a name="prepare-to-switch-plans"></a>Préparer le changement d’offre

### <a name="create-a-change-management-strategy"></a>Créez une stratégie de gestion des modifications

Une stratégie de gestion optimale des changements inclut la façon dont vous communiquerez avec vos utilisateurs, les formerez et les prendrez en charge avant et après leur basculement vers une offre F. Avant de commencer, voici quelques éléments à prendre en compte :

- Comment les utilisateurs seront-ils informés du changement ?
- Comment les utilisateurs apprendront-ils à parcourir les différences entre les services et les fonctionnalités ? Le passage à une offre F peut nécessiter un effort accru dans l’entraînement, car il nécessite un changement de comportement.
- Comment les utilisateurs recevront-ils de l’aide et du support ?

Lorsque vous créez votre stratégie, tenez compte des préférences de communication et de formation. Pour assurer une transition réussie, adaptez votre messagerie, votre formation et votre support aux besoins spécifiques de vos employés de première ligne et de la culture de votre entreprise.

Voici quelques idées pour vous aider à planifier votre stratégie.

|Communication|Formation|Support|
|---------|---------|---------|
|<ul><li>E-mail</li><li>Gestionnaires de départements ou de magasins</li><li>Champions </li><li>Équipes et canaux</li><li>Communautés Yammer</li></ul> |<ul><li>Ressources d’aide, de formation et de vidéo en ligne Microsoft</li><li>Formation en interne</li></ul>|<ul><li>Support technique interne</li><li>Site intranet libre-service</li><li>Ressources d’aide, de formation et de vidéo en ligne Microsoft</li><li>Marcheurs et champions</li></ul>         |

Vous pouvez également consulter ces ressources d’adoption pour vous aider à impliquer et à former vos utilisateurs :

- [Microsoft 365 – Adoption de Microsoft](https://adoption.microsoft.com/microsoft-365/)
- [Teams pour les travailleurs de première ligne – Adoption de Microsoft](https://adoption.microsoft.com/microsoft-teams/frontline-workers/)

### <a name="back-up-or-prepare-data"></a>Sauvegarder ou préparer des données

Identifiez et sauvegardez ou préparez les données que les utilisateurs souhaitent conserver. Suivez les instructions de la section [À quoi s’attendre](#what-to-expect) plus haut dans cet article et effectuez les actions recommandées dans la colonne **Avant le changement** de la table pour chacun des composants suivants :

- Applications Office
- E-mail, Exchange, Outlook
- Teams
- OneDrive

Pour plus d’informations, consultez [Sauvegarder les données avant de changer d’offre](/microsoft-365/commerce/subscriptions/move-users-different-subscription).

## <a name="switch-users-to-a-microsoft-365-f-plan"></a>Basculez les utilisateurs vers une offre Microsoft 365 F

Vous pouvez utiliser le Centre d'administration Microsoft 365 pour modifier manuellement des offres ou une approche scriptée via des applets de commande PowerShell. Quelle que soit la méthode choisie, il est important d’effectuer l’attribution du changement de licence en une seule opération. En d’autres termes, supprimez une licence E existante et remplacez-la en affectant une licence F dans la même opération.

Évitez de supprimer une licence existante pour un utilisateur, puis réattribuez-en une nouvelle ultérieurement. Cela peut avoir un impact sur les données d’un utilisateur. Pour en savoir plus, consultez [Que se passe-t-il pour les données d’un utilisateur lorsque vous supprimez sa licence ?](/microsoft-365/admin/manage/remove-licenses-from-users?view=o365-worldwide#what-happens-to-a-users-data-when-you-remove-their-license)

Pour obtenir des conseils pas à pas sur la modification des offres dans le Centre d’administration Microsoft, consultez [Modifier manuellement les offres Microsoft](/microsoft-365/commerce/subscriptions/change-plans-manually).

## <a name="what-to-do-after-switching-plans"></a>Que faire après le changement d’offre

Suivez les instructions de la section [À quoi s’attendre](#what-to-expect) plus haut dans cet article et effectuez les actions recommandées dans la colonne **Après le changement** de la table pour chacun des composants suivants :

- Applications Office
- E-mail, Exchange, Outlook
- Teams
- OneDrive

Indiquez à vos utilisateurs que la modification est terminée et indiquez-leur comment obtenir de l’aide telle que définie dans votre stratégie de gestion des changements. Vous pouvez inclure des liens vers des [ressources d’aide et d’apprentissage](#user-setup-help-and-learning-resources) pour les prendre en charge dans la transition.

## <a name="user-setup-help-and-learning-resources"></a>Ressources d’installation, d’aide et d’apprentissage de l’utilisateur

Voici quelques liens vers les ressources d’installation, d’aide et d’apprentissage que vous pouvez partager avec vos employés de terrain à des fins de formation et de support.

|Application|Liens |
|---------|---------|
|Office pour le web|<ul><li>[Formation sur Office pour le web](https://support.microsoft.com/office/office-for-the-web-training-e315b031-2bd5-40a1-99ca-264ebf2c8f96)</li><li>[Prise en main de Office sur le web dans Microsoft 365](https://support.microsoft.com/office/get-started-with-office-for-the-web-in-microsoft-365-5622c7c9-721d-4b3d-8cb9-a7276c2470e5)</li></ul>|
|Outlook sur le web|<ul><li>[Découvrir Outlook sur le web](https://support.microsoft.com/office/get-to-know-outlook-on-the-web-3f1a229b-0d60-438f-b515-dd7a28026bc1)</li><li>[Obtenir de l’aide sur Outlook sur le web](https://support.microsoft.com/office/get-help-with-outlook-on-the-web-cf659288-35cc-4c6c-8c75-e8e4317fda11)</li><li>[Outlook sur le web](https://support.microsoft.com/office/learn-more-about-outlook-on-the-web-adbacbab-fe59-4259-a550-6cb7f85f19ec)</li></ul>|
|Office mobile|Configuration :</br><ul><li>[Configurer des applications Office et la messagerie sur Android](https://support.microsoft.com/office/set-up-office-apps-and-email-on-android-6ef2ebf2-fc2d-474a-be4a-5a801365c87f)</li><li>[Configurer des applications Office et la messagerie sur des appareils iOS](https://support.microsoft.com/office/set-up-the-office-app-and-outlook-on-ios-devices-0402b37e-49c4-4419-a030-f34c2013041f)</li></ul>Aide de l’application mobile Office :<ul><li>[Aide de l’application mobile Office pour Android](https://support.microsoft.com/office/microsoft-office-app-for-android-0383d031-a1c6-46c9-b734-53cd1d22765b)</li><li>[Aide de l’application Office pour iOS](https://support.microsoft.com/office/microsoft-office-app-for-ios-c8880c05-883a-46b6-ad32-9bffa31228d0)</li></ul>Aide d’une application mobile Office individuelle :<ul><li>[Word pour téléphones Android](https://support.microsoft.com/office/word-for-android-phones-help-764afb31-ad50-4645-8f51-820ecf731d8f), [Word pour tablettes Android](https://support.microsoft.com/office/word-for-android-tablets-help-8a0dcd56-fb32-4e0d-95d8-997c066125c8),[Word pour iPhone](https://support.microsoft.com/office/word-for-iphone-help-d41a5299-f6fa-4cca-b529-46a8069c5796), [Word pour iPad](https://support.microsoft.com/office/word-for-ipad-help-6567cf2a-c949-4213-912d-f7a14f6264c5)</li><li>[Excel pour téléphones Android](https://support.microsoft.com/office/excel-for-android-phones-help-f818cb37-bfac-485d-8480-363b3da40596), [Excel pour tablettes Android](https://support.microsoft.com/office/word-for-android-tablets-help-8a0dcd56-fb32-4e0d-95d8-997c066125c8), [Excel pour iPhone](https://support.microsoft.com/office/excel-for-iphone-help-b367819b-05b4-4a56-ab1c-678da62e1fd3), [Excel pour iPad](https://support.microsoft.com/office/excel-for-ipad-help-6b5dc2e1-a8e4-48e6-bb69-cb9a3964bc91)</li><li>[PowerPoint pour téléphones Android](https://support.microsoft.com/office/powerpoint-for-android-phones-help-f6714e00-0ee2-48d1-bd3d-e1997565861f), [PowerPoint pour tablettes Android](https://support.microsoft.com/office/powerpoint-for-android-tablets-help-2ada1d22-3784-4943-bc47-9d1ede42875c), [PowerPoint pour iPhone](https://support.microsoft.com/office/powerpoint-for-iphone-help-754fcb37-783b-4e8a-afca-edb900221b8b), [PowerPoint pour iPad](https://support.microsoft.com/office/powerpoint-for-ipad-help-b75ce3bb-03e3-46df-a792-647573fef84a)</li><li>[OneNote pour Android](https://support.microsoft.com/office/microsoft-onenote-for-android-46b4b49d-2bef-4746-9c30-6abb5e20b688), [OneNote pour iPhone](https://support.microsoft.com/office/microsoft-onenote-for-iphone-b93a0ea8-1285-4d31-a7c5-86a849731902), [OneNote pour iPad](https://support.microsoft.com/office/microsoft-onenote-help-ipad-f44e5bcd-5203-4553-9de4-0c56e6500825)</li></ul>
|Teams|<ul><li>[Formation vidéo Teams](https://support.microsoft.com/office/microsoft-teams-video-training-4f108e54-240b-4351-8084-b1089f0d21d7)</li><li>[Aide et apprentissage Teams](https://support.microsoft.com/teams)</li></ul>|

