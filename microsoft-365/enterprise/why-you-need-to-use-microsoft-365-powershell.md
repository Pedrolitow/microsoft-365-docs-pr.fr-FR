---
title: Pourquoi utiliser PowerShell pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Résumé : Comprendre pourquoi vous devez utiliser PowerShell pour gérer les Microsoft 365, dans certains cas plus efficacement et dans d’autres cas par nécessité.'
ms.openlocfilehash: baae3f5682edb65f1bc8114fcc96021b144b93ab
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53228422"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Pourquoi utiliser PowerShell pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Grâce aux Centre d’administration Microsoft 365, vous pouvez gérer vos comptes d Microsoft 365 utilisateur et vos licences. Vous pouvez également gérer vos services Microsoft 365, tels que Exchange Online, Teams et SharePoint Online. Si vous utilisez PowerShell à la place pour gérer ces services, vous pouvez tirer parti de l’environnement de langage de script et de ligne de commande pour la vitesse, l’automatisation et des fonctionnalités supplémentaires.

Cet article montre comment utiliser PowerShell pour gérer les Microsoft 365 à :

- Révéler des informations supplémentaires que vous ne pouvez pas voir dans la Centre d’administration Microsoft 365

- Configurer les fonctionnalités et les paramètres uniquement possible avec PowerShell

- Faire des opérations en bloc

- Filtrer les données

- Imprimer ou enregistrer des données

- Gérer entre les services

N’oubliez pas que PowerShell pour Microsoft 365 est un ensemble de modules pour Windows PowerShell, qui est un environnement de ligne de commande pour les plateformes et les services basés sur Windows. Cet environnement crée un langage d’environnement de commande qui peut être étendu avec des modules supplémentaires. Il permet d’exécuter des commandes ou des scripts simples ou complexes. Par exemple, après avoir installé les modules PowerShell pour Microsoft 365 et vous être connecté à votre abonnement Microsoft 365, vous pouvez exécuter la commande suivante pour lister toutes les boîtes aux lettres utilisateur pour Microsoft Exchange Online :

```powershell
Get-Mailbox
```

Vous pouvez également obtenir la liste des boîtes aux lettres à l’aide du Centre d’administration Microsoft 365 mais il n’est pas facile de compter les éléments de toutes les listes de tous les sites pour toutes vos applications web.

PowerShell pour Microsoft 365 est conçu pour vous aider à gérer les Microsoft 365, et non à remplacer les Centre d’administration Microsoft 365. Les administrateurs doivent être en mesure d’utiliser PowerShell pour Microsoft 365 car certaines procédures de configuration peuvent uniquement être réalisées via PowerShell pour Microsoft 365 commandes. Pour ces cas, vous devez savoir comment :

- Installez PowerShell pour Microsoft 365 modules (effectués une seule fois pour chaque ordinateur administrateur).

- Connecter à votre abonnement Microsoft 365 (une fois pour chaque session PowerShell).

- Collectez les informations nécessaires pour exécuter le PowerShell requis Microsoft 365 commandes.

- Exécutez PowerShell pour Microsoft 365 commandes.

Une fois que vous avez appris ces compétences de base, vous n’avez pas besoin de lister vos utilisateurs de boîte aux lettres à l’aide de la **commande Get-Mailbox.** Vous n’avez pas non plus besoin de comprendre comment créer une commande comme celle mentionnée précédemment pour compter tous les éléments de toutes les listes pour tous les sites de toutes vos applications web. Microsoft et la communauté d’administrateurs peuvent vous aider à effectuer les tâches nécessaires.

## <a name="powershell-for-microsoft-365-can-reveal-information-that-you-cant-see-with-the-microsoft-365-admin-center"></a>PowerShell pour Microsoft 365 peut révéler des informations que vous ne pouvez pas voir avec le Centre d’administration Microsoft 365

Le Centre d’administration Microsoft 365 affiche de nombreuses informations utiles. Toutefois, il n’affiche pas toutes les informations que vous Microsoft 365 stockez sur les utilisateurs, les licences, les boîtes aux lettres et les sites. Voici un exemple pour les *utilisateurs et les groupes* de la Centre d’administration Microsoft 365 :

![Exemple d’affichage des utilisateurs et des groupes dans le Centre d’administration Microsoft 365.](../media/o365-powershell-users-and-groups.png)

Cette vue fournit les informations dont vous avez besoin dans de nombreux cas. Toutefois, il peut arriver que vous ayez besoin de plus d'informations. Par exemple, Microsoft 365 licences (et les fonctionnalités Microsoft 365 disponibles pour un utilisateur) dépendent en partie de l’emplacement géographique de l’utilisateur. Les stratégies et fonctionnalités que vous pouvez étendre à un utilisateur qui réside aux États-Unis peuvent ne pas être identiques à celles que vous pouvez étendre à un utilisateur en Inde ou en Belgique. Suivez ces étapes dans la Centre d’administration Microsoft 365 pour déterminer l’emplacement géographique d’un utilisateur :

1. Double-cliquez sur l'élément **Nom d'affichage** de l'utilisateur.

2. Dans le volet d’affichage des propriétés utilisateur, sélectionnez **détails.**

3. Dans l’affichage des détails, sélectionnez **des détails supplémentaires.**

4. Faites défiler jusqu’à ce que vous trouviez le titre **Pays ou région**:

     ![Exemple d’informations de région pour un utilisateur dans le Centre d’administration Microsoft 365.](../media/o365-powershell-usage-location.png)

5. Écrivez le nom d'affichage et l'emplacement de l'utilisateur sur un morceau de papier, ou copiez-le et collez-le dans le Bloc-notes.

Vous devez répéter cette procédure pour chaque utilisateur. Si vous avez de nombreux utilisateurs, ce processus peut être fastidieux. Avec PowerShell pour Microsoft 365, vous pouvez afficher ces informations pour tous vos utilisateurs à l’aide de la commande suivante :

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les cmdlets dont le nom comprend *Msol.* Vous devez exécuter ces cmdlets à partir Windows PowerShell.
>

Voici un exemple des résultats :

```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

L’interprétation de cette commande PowerShell est : Obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel (**Get-AzureADUser**), mais afficher uniquement le nom et l’emplacement de chaque utilisateur (**Sélectionnez DisplayName, UsageLocation**).

Étant donné que PowerShell pour Microsoft 365 prend en charge un langage d’shell de commande, vous pouvez manipuler davantage les informations obtenues par la commande **Get-AzureADUser.** Par exemple, vous souhaitez peut-être trier ces utilisateurs en fonction de leur emplacement, en regroupéssant tous les utilisateurs brésiliens, tous les utilisateurs des États-Unis, etc. Voici la commande :

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Voici un exemple des résultats :

```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

L’interprétation de cette commande PowerShell est : Obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel, mais afficher uniquement le nom et l’emplacement de chaque utilisateur et les trier d’abord par leur emplacement, puis leur nom (**Sort UsageLocation, DisplayName**).

Vous pouvez également utiliser un filtrage supplémentaire. Par exemple, si vous voulez uniquement voir les informations relatives aux utilisateurs basés au Brésil, utilisez cette commande :

```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation
```

Voici un exemple des résultats :

```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

L’interprétation de cette commande PowerShell est : Obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel dont l’emplacement est le Brésil (**Où {$ \_ . UsageLocation -eq « BR"}**), puis affiche le nom et l’emplacement de chaque utilisateur.

 **Remarque sur les domaines de grande taille**

Si vous avez un grand domaine avec des dizaines de milliers d’utilisateurs, la tentative de certains des exemples que nous présentons dans cet article peut entraîner une limitation. En fonction de facteurs tels que la puissance de calcul et la bande passante réseau disponible, vous essayez peut-être d’en faire trop en même temps. Les grandes organisations peuvent vouloir fractionner certaines de ces opérations PowerShell en deux commandes.

Par exemple, la commande suivante renvoie tous les comptes d’utilisateur et affiche le nom et l’emplacement de chacun d’eux :

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

Cela fonctionne bien pour les petits domaines. Toutefois, dans une grande organisation, vous pouvez fractionner cette opération en deux commandes : une commande pour stocker les informations du compte d’utilisateur dans une variable et une autre pour afficher les informations nécessaires. Voici un exemple :

```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

L’interprétation de cet ensemble de commandes PowerShell est la :
1. Obtenez tous les utilisateurs de l’abonnement Microsoft 365 actuel et stockez les informations dans une variable nommée $x (**$x = Get-AzureADUser**).
1.  Afficher le contenu de la variable *$x,* mais inclure uniquement le nom et l’emplacement de chaque utilisateur (**$x | Sélectionnez DisplayName, UsageLocation**).

## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 comporte des fonctionnalités que vous pouvez uniquement configurer avec PowerShell pour Microsoft 365

Le Centre d’administration Microsoft 365 est destiné à fournir un accès aux tâches administratives courantes et utiles qui s’appliquent à la plupart des environnements. En d’autres termes, le Centre d’administration Microsoft 365 a été conçu pour que l’administrateur classique puisse effectuer les tâches de gestion les plus courantes. Certaines tâches ne peuvent toutefois pas être réalisées dans le Centre d’administration.

Par exemple, le Centre d Skype Entreprise Online propose quelques options pour créer des invitations personnalisées aux réunions :

![Exemple d’affichage d’invitations personnalisées à une réunion dans le Centre d’administration de Skype Entreprise Online.](../media/o365-powershell-meeting-invitation.png)

Avec ces paramètres, vous pouvez ajouter une touche de personnalisation et de professionnalisme aux invitations aux réunions. Toutefois, les paramètres de configuration de réunion ne se contentent pas de créer des invitations personnalisées à une réunion. Par défaut, les réunions autorisent :

- les utilisateurs anonymes à obtenir une entrée automatique à chaque réunion ;

- les participants à enregistrer la réunion ;

- tous les utilisateurs de votre organisation à être désignés en tant que présentateurs lorsqu’ils rejoignent la réunion.

Ces paramètres ne sont pas disponibles dans le centre d’administration Skype Entreprise Online. Vous pouvez les contrôler à partir de PowerShell pour Microsoft 365. Voici une commande qui désactive ces trois paramètres :

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Pour exécuter cette commande, vous devez installer le [module Skype Entreprise Online PowerShell](https://www.microsoft.com/download/details.aspx?id=39366).

L’interprétation de cette commande PowerShell est la :

1. Dans les paramètres des nouvelles réunions Skype Entreprise Online (**Set-CsMeetingConfiguration**), désactivez l’accès automatique des utilisateurs anonymes aux réunions (**-AdmitAnonymousUsersByDefault $False**).
2.  Désactivez la possibilité pour les participants d’enregistrer les réunions (**-AllowConferenceRecording $False**).
3. Ne désignez pas tous les utilisateurs de votre organisation comme présentateurs (**-DesignateAsPresenter « None »**).

Pour restaurer ces paramètres par défaut (activer les options), exécutez la commande ci-après :

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Il existe également d’autres scénarios similaires, c’est pourquoi les administrateurs doivent savoir comment exécuter PowerShell pour Microsoft 365 commandes.

## <a name="powershell-for-microsoft-365-is-great-for-bulk-operations"></a>PowerShell pour les Microsoft 365 est idéal pour les opérations en bloc

Les interfaces visuelles telles que Centre d’administration Microsoft 365 sont plus utiles lorsque vous avez une seule opération à faire. Par exemple, si vous devez désactiver un compte d’utilisateur, vous pouvez utiliser le Centre d’administration pour localiser et désactiver rapidement une case à cocher. Cela peut être plus facile que d’effectuer une opération similaire dans PowerShell.

Toutefois, si vous devez modifier de nombreux éléments ou certains éléments sélectionnés dans un grand nombre d’autres éléments, le Centre d’administration Microsoft 365 peut ne pas être le meilleur outil. Par exemple, vous devez modifier le préfixe sur des milliers de numéros de téléphone ou supprimer l’utilisateur *spécifique Ken Myer* de tous vos sites SharePoint Online. Comment le feriez-vous dans la Centre d’administration Microsoft 365 ?

Pour le dernier exemple, dites que vous avez plusieurs centaines de sites SharePoint Online et que vous ne connaissez pas ceux dont Ken Meyer est membre. Vous devez commencer à l’Centre d’administration Microsoft 365 puis effectuer cette procédure pour chaque site :

1. Sélectionnez **l’URL** du site.

2. Dans la **zone des propriétés de la collection** de sites, sélectionnez le lien Adresse du site **Web** pour ouvrir le site.

3. Sur le site, sélectionnez **Partager.**

4. Dans la **boîte de** dialogue Partager, sélectionnez le lien qui affiche tous les utilisateurs qui ont des autorisations sur le site :

     ![Exemple d’affichage des membres d’un site SharePoint Online dans le Centre d’administration SharePoint Online.](../media/o365-powershell-view-permissions.png)

5. Dans la **boîte de dialogue Partagé avec,** sélectionnez **Avancé.**

6. Faites défiler la liste des utilisateurs vers le bas, recherchez et sélectionnez Ken Myer (en supposant qu’il dispose d’autorisations sur le site), puis sélectionnez Supprimer les **autorisations utilisateur.**

Cela peut prendre beaucoup *de temps* pour plusieurs centaines de sites.

L’alternative consiste à exécuter la commande suivante dans PowerShell pour Microsoft 365 pour supprimer Ken Myer de tous vos sites :

```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Cette commande nécessite que vous installiez SharePoint [module PowerShell en ligne.](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

L’interprétation de cette commande PowerShell est : Obtenir tous les sites SharePoint dans l’abonnement Microsoft 365 actuel (**Get-SPOSite**) et pour chaque site, supprimez KenLier de la liste des utilisateurs qui peuvent y accéder (**ForEach {Remove-SPOUser -Site $ \_ . Url -LoginName « kenmyer \@ litwareinc.com"}**).

Nous vous Microsoft 365 de supprimer Ken Meyer de chaque site, y compris ceux à lesquels il n’a pas accès. Les résultats indiquent donc des erreurs pour les sites à qui il n’a pas accès. Nous pouvons utiliser une condition supplémentaire sur cette commande pour supprimer KenCourir uniquement des sites qui l’ont sur leur liste de connexion. Toutefois, les erreurs renvoyées ne provoquent aucun dommage pour les sites eux-mêmes. Cette commande peut prendre quelques minutes pour s’exécuter sur des centaines de sites, plutôt que des heures de travail sur le Centre d’administration Microsoft 365.

Voici un autre exemple d’opération en bloc. Utilisez cette commande pour ajouter Une nouvelle administrateur SharePoint *à* tous les sites de l’organisation :

```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

L’interprétation de cette commande PowerShell est la : Obtenir tous les sites SharePoint dans l’abonnement Microsoft 365 actuel et pour chaque site autoriser l’accès à Las Kearney en ajoutant son nom de connexion au groupe Membres du site (**ForEach {Add-SPOUser -Site $ \_ . Url -LoginName « bkearney \@ litwareinc.com » -Group « Members"}**).

## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>PowerShell pour Microsoft 365 est idéal pour filtrer des données

Le Centre d’administration Microsoft 365 propose plusieurs façons de filtrer vos données pour localiser facilement un sous-ensemble ciblé d’informations. Par exemple, Exchange facilite le filtrage sur pratiquement toutes les propriétés de la boîte aux lettres d'un utilisateur. Par exemple, voici la liste des boîtes aux lettres pour tous les utilisateurs qui habitent à Bloomington :

![Exemple d’une recherche avancée dans le Centre d’administration Microsoft 365 liste des boîtes aux lettres de tous les utilisateurs qui habitent à Bloomington.](../media/o365-powershell-advanced-search.png)

Le Centre d'administration Exchange vous permet également de combiner des critères de filtre. Par exemple, vous pouvez trouver les boîtes aux lettres de toutes les personnes qui habitent à Bloomington et travaillent au service financier.

Toutefois, il existe des limites à ce que vous pouvez faire dans le Centre d Exchange’administration. Par exemple, vous ne pouviez pas trouver aussi facilement les boîtes aux lettres des personnes qui habitent à *Bloomington* ou San Diego, ou les boîtes aux lettres de toutes les personnes qui n’habitent pas à Bloomington.

Vous pouvez utiliser la commande PowerShell pour Microsoft 365 suivante pour obtenir la liste des boîtes aux lettres de toutes les personnes qui habitent à Bloomington ou San Diego :

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox&quot; -and ($_.City -eq &quot;San Diego&quot; -or $_.City -eq &quot;Bloomington")} | Select DisplayName, City
```

Voici un exemple des résultats :

```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

L’interprétation de cette commande PowerShell est : Obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel qui ont une boîte aux lettres dans la ville de San Diego ou Bloomington (**Où {$ \_ . RecipientTypeDetails -eq « UserMailbox » -and ($ \_ . City -eq « San Diego » -or $ \_ . Ville -eq « Bloomington »)}**), puis afficher le nom et la ville pour chaque (**Sélectionnez DisplayName, Ville**).

Et voici la commande pour lister toutes les boîtes aux lettres des personnes qui habitent n’importe où à l’exception de Bloomington :

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Voici un exemple des résultats :

```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

L’interprétation de cette commande PowerShell est : Obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel qui ont une boîte aux lettres qui ne se trouve pas dans la ville de Bloomington (**Où {$ \_ . RecipientTypeDetails -eq « UserMailbox » -and $ \_ . City -ne « Bloomington"}**), puis afficher le nom et la ville pour chacun d’eux.

### <a name="use-wildcards"></a>Utiliser des caractères génériques

Vous pouvez également utiliser des caractères génériques dans vos filtres PowerShell pour faire correspondre une partie d’un nom. Par exemple, supposons que vous recherchiez un compte d’utilisateur. Tout ce que vous vous souvenez, c’est que le nom de famille de l’utilisateur était *Anderson* ou *peut-être À la place* de *Sondesser ou Dersonson*.

Vous pouvez suivre cet utilisateur dans le Centre d’administration Microsoft 365 l’aide de l’outil de recherche et effectuer trois recherches différentes :

- Une sur  *Anderson*

- Une sur  *Henderson*

- Une sur  *Jorgenson*

Étant donné que ces trois noms se terminent par « son », vous pouvez indiquer à PowerShell d’afficher tous les utilisateurs dont le nom se termine par « son ». Voici la commande :

```powershell
Get-User -Filter '{LastName -like "*son"}'
```

L’interprétation de cette commande PowerShell est : Obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel, mais utiliser un filtre qui répertorie uniquement les utilisateurs dont le nom de famille se termine par « son » (**-Filter '{LastName -like " \* son"}'**). Signifie tout ensemble de caractères, qui sont des lettres dans le nom \* de famille de l’utilisateur.

## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>PowerShell pour Microsoft 365 facilite l’impression ou l’enregistrer des données

Le Centre d’administration Microsoft 365 vous permet d’afficher des listes de données. Voici un exemple du Centre d’administration Skype Entreprise Online affichant la liste des utilisateurs qui ont été activés pour Skype Entreprise Online :

![Exemple de liste d’utilisateurs ayant été activés pour Skype Entreprise Online, affichée dans le Centre d’administration de Skype Entreprise Online.](../media/o365-powershell-lync-users.png)

Pour enregistrer ces informations dans un fichier, vous devez les coller dans un document ou Microsoft Excel feuille de calcul. Les deux cas peuvent nécessiter une mise en forme supplémentaire. En outre, le Centre d’administration Microsoft 365 ne fournit pas un moyen d’imprimer directement la liste affichée.

Heureusement, vous pouvez utiliser PowerShell non seulement pour afficher la liste, mais aussi pour l’enregistrer dans un fichier qui peut être facilement importé dans Excel. Voici un exemple de commande pour enregistrer les données utilisateur Skype Entreprise Online dans un fichier de valeurs séparées par des virgules (CSV), qui peut ensuite être facilement importé en tant que table dans une feuille de calcul Excel :

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Voici un exemple des résultats :

![Exemple de tableau importé dans une feuille de calcul Excel pour Skype Entreprise données utilisateur en ligne enregistrées dans un fichier de valeurs séparées par des virgules.](../media/o365-powershell-data-in-excel.png)

L’interprétation de cette commande PowerShell est : Obtenir tous les utilisateurs Skype Entreprise Online dans l’abonnement Microsoft 365 actuel (**Get-CsOnlineUser**) ; obtenir uniquement le nom d’utilisateur, l’UPN et l’emplacement (**Select DisplayName, UserPrincipalName, UsageLocation**) ; puis enregistrez ces informations dans un fichier CSV nommé C: \\ Logs \\SfBUsers.csv (**Export-Csv -Path « C: \\ Logs \\SfBUsers.csv » -NoTypeInformation**).

Vous pouvez également utiliser des options pour enregistrer cette liste en tant que fichier XML ou page HTML. En fait, avec des commandes PowerShell supplémentaires, vous pouvez l’enregistrer directement en tant que fichier Excel, avec n’importe quelle mise en forme personnalisée que vous souhaitez.

Vous pouvez également envoyer la sortie d’une commande PowerShell qui affiche une liste directement à l’imprimante par défaut dans Windows. Voici un exemple de commande :

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Le document imprimé aura l'apparence suivante :

![Exemple de document imprimé qui était la sortie d’une commande PowerShell envoyée directement à l’imprimante par défaut dans Windows.](../media/o365-powershell-printed-data.png)

L’interprétation de cette commande PowerShell est la Skype Entreprise utilisateurs en ligne dans l’abonnement Microsoft 365 actuel ; obtenir uniquement le nom d’utilisateur, l’UPN et l’emplacement ; puis envoyez ces informations à l’imprimante Windows par défaut (**Out-Printer**).

Le document imprimé a la même mise en forme simple que l’affichage dans la fenêtre de commande PowerShell. Pour obtenir une copie papier, ajoutez **simplement | Out-Printer** à la fin de la commande.

## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>PowerShell pour Microsoft 365 vous permet de gérer les différents produits serveur

Les composants qui Microsoft 365 sont conçus pour fonctionner ensemble. Par exemple, supposons que vous ajoutez un nouvel utilisateur à Microsoft 365 et que vous spécifiez des informations telles que le service et le numéro de téléphone de l’utilisateur. Ces informations seront ensuite disponibles si vous accédez aux informations de l’utilisateur dans l’un des services Microsoft 365 : Skype Entreprise Online, Exchange ou SharePoint.

Toutefois, ceci concerne les informations communes qui couvrent une suite de produits. Les informations spécifiques au produit, telles que les informations sur la boîte aux lettres Exchange’un utilisateur, ne sont généralement pas disponibles dans la suite. Par exemple, les informations permettant d’activer ou non la boîte aux lettres d’un utilisateur sont disponibles uniquement dans Exchange’administration centrale.

Supposons que vous souhaitiez établir un rapport qui présente les informations suivantes pour tous les utilisateurs :

- Nom complet de l'utilisateur

- Si l’utilisateur est titulaire d’une licence Microsoft 365

- Si la boîte aux lettres Exchange de l'utilisateur a été activée

- Si l'utilisateur est activé pour Skype Entreprise Online

Vous ne pouvez pas facilement produire un tel rapport dans le Centre d’administration Microsoft 365. Au lieu de cela, vous devez créer un document distinct pour stocker les informations, telles qu’Excel feuille de calcul. Ensuite, obtenez tous les noms d’utilisateur et les informations de licence du Centre d’administration Microsoft 365, obtenez des informations de boîte aux lettres à partir du Centre d’administration Exchange, obtenez des informations Skype Entreprise Online à partir du Centre d’administration Skype Entreprise Online, puis combinez ces informations.

L’alternative consiste à utiliser un script PowerShell pour compiler le rapport à votre place.

L’exemple de script suivant est plus compliqué que les commandes que vous avez vues jusqu’à présent dans cet article. Toutefois, il montre le potentiel de l’utilisation de PowerShell pour créer des affichages d’informations difficiles à obtenir autrement. Voici le script pour compiler et afficher la liste dont vous avez besoin :

```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

Voici un exemple des résultats :

```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

L’interprétation de ce script PowerShell est la suivant :

1. Obtenez tous les utilisateurs de l’abonnement Microsoft 365 actuel et stockez les informations dans une variable nommée *$x* (**$x = Get-AzureADUser**).
1. Démarrez une boucle qui s’exécute sur tous les utilisateurs de la variable $x **(foreach ($i en $x)**).
1. Définissez une variable nommée *$y* et stockez-y les informations de boîte aux lettres de l’utilisateur (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
1. Ajoutez une nouvelle propriété aux informations utilisateur *nommées IsMailBoxEnabled*. Définissez-la sur la valeur de la propriété IsMailBoxEnabled de la boîte aux lettres de l’utilisateur (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
1. Définissez une variable nommée *$y* et stockez-y les informations Skype Entreprise Online de l’utilisateur (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
1. Ajoutez une nouvelle propriété aux informations utilisateur *nommées EnabledForSfB*. Définissez-la sur la valeur de la propriété Enabled des informations Skype Entreprise Online de l’utilisateur (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).
1. Affichez la liste des utilisateurs, mais incluez uniquement leur nom, s’ils sont titulaires d’une licence ou non, et les deux nouvelles propriétés qui indiquent si leur boîte aux lettres est activée et si elles sont activées pour Skype Entreprise Online (**$x | Sélectionnez DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).

## <a name="see-also"></a>Voir aussi

[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Utilisez Windows PowerShell pour créer des rapports dans Microsoft 365](use-windows-powershell-to-create-reports-in-microsoft-365.md)