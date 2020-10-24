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
description: 'Résumé : Découvrez pourquoi vous devez utiliser PowerShell pour gérer Microsoft 365, dans certains cas plus efficacement et dans d’autres cas, par nécessité.'
ms.openlocfilehash: d56a2cc47a06be911f1fd38aea3a557c631d2db0
ms.sourcegitcommit: 66b8fc1d8ba4f17487cd2004ac19cf2fff472f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48754105"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Pourquoi utiliser PowerShell pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Avec le centre d’administration Microsoft 365, vous pouvez gérer vos licences et comptes d’utilisateur Microsoft 365. Vous pouvez également gérer vos services Microsoft 365, comme Exchange Online, teams et SharePoint Online. Si, à la place, vous utilisez PowerShell pour gérer ces services, vous pouvez et tirer parti de la ligne de commande et de l’environnement de langage de script pour la vitesse, l’automatisation et les fonctionnalités supplémentaires.
  
Cet article explique comment utiliser PowerShell pour gérer Microsoft 365 afin de :
  
- Révéler des informations supplémentaires qui ne sont pas visibles dans le centre d’administration Microsoft 365
    
- Configuration des fonctionnalités et des paramètres uniquement avec PowerShell
    
- Effectuer des opérations en bloc
    
- Filtrer les données
    
- Imprimer ou enregistrer des données
    
- Gérer dans les services
    
N’oubliez pas que PowerShell pour Microsoft 365 est un ensemble de modules pour Windows PowerShell, qui est un environnement de ligne de commande pour les plateformes et les services Windows. Cet environnement crée un langage de commande de l’interpréteur de commandes pouvant être étendu à l’aide de modules supplémentaires. Il permet d’exécuter des commandes ou des scripts simples ou complexes. Par exemple, après avoir installé PowerShell pour les modules Microsoft 365 et vous être connecté à votre abonnement Microsoft 365, vous pouvez exécuter la commande suivante pour répertorier toutes les boîtes aux lettres utilisateur pour Microsoft Exchange Online :
  
```powershell
Get-Mailbox
```

Vous pouvez également obtenir la liste des boîtes aux lettres à l’aide du centre d’administration Microsoft 365, mais il n’est pas facile de compter les éléments dans toutes les listes de tous les sites de toutes les applications Web.
  
PowerShell pour Microsoft 365 est conçu pour vous aider à gérer Microsoft 365, et non à remplacer le centre d’administration Microsoft 365. Les administrateurs doivent pouvoir utiliser PowerShell pour Microsoft 365, car il existe des procédures de configuration qui ne peuvent être réalisées que par le biais de commandes PowerShell pour Microsoft 365. Dans ce cas, vous devez savoir comment :
  
- Installez les modules PowerShell pour Microsoft 365 (une seule fois pour chaque ordinateur d’administrateur).
    
- Connectez-vous à votre abonnement Microsoft 365 (une fois pour chaque session PowerShell).
    
- Recueillez les informations nécessaires pour exécuter les commandes PowerShell requises pour Microsoft 365.
    
- Exécutez les commandes PowerShell pour Microsoft 365.
    
Une fois que vous avez appris ces compétences de base, vous n’avez pas besoin de répertorier les utilisateurs de votre boîte aux lettres à l’aide de la commande **Get-Mailbox** . Vous ne devez pas non plus comprendre comment créer une commande à l’instar de la commande citée précédemment pour compter tous les éléments de toutes les listes de tous les sites de toutes les applications Web. Microsoft et la communauté des administrateurs peuvent vous aider à effectuer ces tâches en fonction de vos besoins.
  
## <a name="powershell-for-microsoft-365-can-reveal-information-that-you-cant-see-with-the-microsoft-365-admin-center"></a>PowerShell pour Microsoft 365 peut révéler des informations que vous ne pouvez pas voir avec le centre d’administration Microsoft 365

Le centre d’administration Microsoft 365 affiche de nombreuses informations utiles. Toutefois, il n’affiche pas toutes les informations que Microsoft 365 stocke sur les utilisateurs, les licences, les boîtes aux lettres et les sites. Voici un exemple pour *les utilisateurs et les groupes* dans le centre d’administration 365 de Microsoft :
  
![Exemple d’affichage des utilisateurs et des groupes dans le centre d’administration 365 de Microsoft.](../media/o365-powershell-users-and-groups.png)
  
Cet affichage fournit les informations dont vous avez besoin dans de nombreux cas. Toutefois, il peut arriver que vous ayez besoin de plus d'informations. Par exemple, les licences Microsoft 365 (et les fonctionnalités Microsoft 365 disponibles pour un utilisateur) dépendent en partie de l’emplacement géographique de l’utilisateur. Les stratégies et les fonctionnalités que vous pouvez étendre à un utilisateur résidant aux États-Unis peuvent ne pas être les mêmes que celles que vous pouvez étendre à un utilisateur en Inde ou en Belgique. Suivez ces étapes dans le centre d’administration 365 de Microsoft pour déterminer l’emplacement géographique d’un utilisateur :
  
1. Double-cliquez sur l'élément **Nom d'affichage** de l'utilisateur.
    
2. Dans le volet d’affichage des propriétés utilisateur, sélectionnez **Détails**.
    
3. Dans l’affichage des détails, sélectionnez **Détails supplémentaires**.
    
4. Faites défiler jusqu’à ce que vous trouviez le **pays ou la région**de titre :
    
     ![Exemple d’informations de région pour un utilisateur dans le centre d’administration Microsoft 365.](../media/o365-powershell-usage-location.png)
  
5. Écrivez le nom d'affichage et l'emplacement de l'utilisateur sur un morceau de papier, ou copiez-le et collez-le dans le Bloc-notes.
    
Vous devez répéter cette procédure pour chaque utilisateur. Si vous avez un grand nombre d’utilisateurs, ce processus peut être fastidieux. Avec PowerShell pour Microsoft 365, vous pouvez afficher ces informations pour tous vos utilisateurs à l’aide de la commande suivante :
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour les applets de commande et le module Windows PowerShell dont le nom est *MSOL* . Vous devez exécuter ces applets de commande à partir de Windows PowerShell.
>

Voici un exemple des résultats :
  
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

L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs dans l’abonnement Microsoft 365 actuel (**Get-AzureADUser**), mais afficher uniquement le nom et l’emplacement de chaque utilisateur (**Select DisplayName, UsageLocation**).
  
Étant donné que PowerShell pour Microsoft 365 prend en charge une langue de commande, vous pouvez manipuler les informations obtenues par la commande **Get-AzureADUser** . Par exemple, vous voudrez peut-être trier ces utilisateurs en fonction de leur emplacement, en regroupant tous les utilisateurs brésiliens, tous les utilisateurs des États-Unis, et ainsi de suite. Voici la commande :
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Voici un exemple des résultats :
  
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

L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel, mais afficher uniquement le nom et l’emplacement de chaque utilisateur et les trier d’abord en fonction de leur emplacement, puis leur nom (**Trier UsageLocation, DisplayName**).
  
Vous pouvez également utiliser un filtrage supplémentaire. Par exemple, si vous voulez uniquement voir les informations relatives aux utilisateurs basés au Brésil, utilisez cette commande :
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

Voici un exemple des résultats :
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel dont l’emplacement est le Brésil (**où {$ \_ . UsageLocation-EQ "BR"}**), puis affichez le nom et l’emplacement de chaque utilisateur.
  
 **Remarque sur les grands domaines**
  
Si vous disposez d’un grand domaine avec des dizaines de milliers d’utilisateurs, essayez quelques-uns des exemples présentés dans cet article peuvent conduire à une limitation. En fonction de facteurs comme la puissance de calcul et la bande passante réseau disponible, il se peut que vous essayiez d’effectuer trop de tâches à la fois. Les grandes organisations peuvent souhaiter fractionner certaines de ces opérations PowerShell en deux commandes.

Par exemple, la commande suivante renvoie tous les comptes d’utilisateur et indique le nom et l’emplacement de chacun :
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

Cela fonctionne bien pour les petits domaines. Toutefois, dans une organisation de grande taille, vous pouvez fractionner cette opération en deux commandes : une pour stocker les informations de compte d’utilisateur dans une variable et une autre pour afficher les informations nécessaires. Voici un exemple :
  
```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

L’interprétation de cet ensemble de commandes PowerShell est la suivante :
1. Obtenez tous les utilisateurs dans l’abonnement Microsoft 365 actuel et stockez les informations dans une variable nommée $x (**$x = Get-AzureADUser**).
1.  Affiche le contenu de la variable *$x*, mais inclut uniquement le nom et l’emplacement de chaque utilisateur (**$x | Sélectionnez DisplayName, UsageLocation**).
  
## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 dispose de fonctionnalités que vous pouvez configurer uniquement avec PowerShell pour Microsoft 365

Le centre d’administration Microsoft 365 est destiné à fournir un accès à des tâches d’administration courantes et utiles qui s’appliquent à la plupart des environnements. En d’autres termes, le centre d’administration 365 de Microsoft a été conçu de sorte que l’administrateur par défaut puisse effectuer les tâches de gestion les plus courantes. Toutefois, certaines tâches ne peuvent pas être effectuées dans le centre d’administration.
  
Par exemple, le centre d’administration de Skype entreprise Online offre quelques options pour créer des invitations personnalisées à une réunion :
  
![Exemple d’affichage d’invitations personnalisées à une réunion dans le Centre d’administration de Skype Entreprise Online.](../media/o365-powershell-meeting-invitation.png)
  
Avec ces paramètres, vous pouvez ajouter une touche de personnalisation et de professionnalisme aux invitations aux réunions. Toutefois, il existe d’autres paramètres de configuration de réunion que la simple création d’invitations aux réunions personnalisées. Par défaut, les réunions autorisent :
  
- les utilisateurs anonymes à obtenir une entrée automatique à chaque réunion ;
    
- les participants à enregistrer la réunion ;
    
- tous les utilisateurs de votre organisation à être désignés en tant que présentateurs lorsqu’ils rejoignent la réunion.
    
Ces paramètres ne sont pas disponibles dans le centre d’administration de Skype entreprise online. Vous pouvez les contrôler à partir de PowerShell pour Microsoft 365. Voici une commande qui désactive ces trois paramètres :
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Pour exécuter cette commande, vous devez installer le [module Skype entreprise Online PowerShell ](https://www.microsoft.com/download/details.aspx?id=39366).
  
L’interprétation de cette commande PowerShell est la suivante :
 
1. Dans les paramètres des nouvelles réunions Skype entreprise Online (**Set-CsMeetingConfiguration**), désactivez la fonctionnalité permettant aux utilisateurs anonymes d’accéder automatiquement aux réunions (**-AdmitAnonymousUsersByDefault $false**).
2.  Désactiver la possibilité pour les participants d’enregistrer des réunions (**-AllowConferenceRecording $false**).
3. Ne désignez pas tous les utilisateurs de votre organisation en tant que présentateurs (**-DesignateAsPresenter "none"**).
  
Pour restaurer ces paramètres par défaut (activer les options), exécutez la commande suivante :
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Il existe également d’autres scénarios similaires, c’est pourquoi les administrateurs doivent savoir exécuter les commandes PowerShell pour Microsoft 365.
  
## <a name="powershell-for-microsoft-365-is-great-for-bulk-operations"></a>PowerShell pour Microsoft 365 est idéal pour les opérations en bloc

Les interfaces visuelles comme le centre d’administration Microsoft 365 sont particulièrement utiles lorsque vous avez une seule opération à effectuer. Par exemple, si vous avez besoin de désactiver un compte d’utilisateur, vous pouvez utiliser le centre d’administration pour localiser et désactiver rapidement une case à cocher. Cela peut être plus simple que d’effectuer une opération similaire dans PowerShell.
  
Toutefois, si vous devez modifier de nombreux éléments ou des éléments sélectionnés dans un grand nombre d’autres choses, le centre d’administration Microsoft 365 peut ne pas être le meilleur outil. Par exemple, imaginons que vous devez modifier le préfixe sur des milliers de numéros de téléphone ou supprimer l’utilisateur spécifique *Ken Myer* de tous vos sites SharePoint Online. Comment pouvez-vous effectuer cette opération dans le centre d’administration 365 de Microsoft ?
  
Pour le dernier exemple, imaginons que vous avez plusieurs centaines de sites SharePoint Online et que vous ne sachiez pas à qui elle appartient. Vous devez commencer par le centre d’administration 365 de Microsoft, puis effectuer cette procédure pour chaque site :
  
1. Sélectionnez l' **URL** du site.
    
2. Dans la zone Propriétés de la **collection de sites** , sélectionnez le lien adresse du **site Web** pour ouvrir le site.
    
3. Sur le site, sélectionnez **partager**.
    
4. Dans la boîte de dialogue **partager** , sélectionnez le lien qui affiche tous les utilisateurs disposant d’autorisations sur le site :
    
     ![Exemple d’affichage des membres d’un site SharePoint Online dans le Centre d’administration SharePoint Online.](../media/o365-powershell-view-permissions.png)
  
5. Dans la boîte de dialogue **partagé avec** , sélectionnez **avancé**.
    
6. Faites défiler vers le bas la liste des utilisateurs, recherchez et sélectionnez Ken Myer (en supposant qu’il dispose d’autorisations sur le site), puis sélectionnez **Supprimer les autorisations des utilisateurs**.
    
Cela prendrait *beaucoup* de temps pour plusieurs centaines de sites.
  
L’alternative consiste à exécuter la commande suivante dans PowerShell pour Microsoft 365 afin de supprimer Ken Myer de tous vos sites :
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Cette commande exige que vous installiez le [module SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps). 
  
L’interprétation de cette commande PowerShell est la suivante : obtenir tous les sites SharePoint dans l’abonnement Microsoft 365 actuel (**Get-SPOSite**) et pour chaque site supprimez Ken Meyer de la liste des utilisateurs qui peuvent y accéder (**foreach {Remove-épouser-site $ \_ . URL-LoginName "kenmyer \@ litwareinc.com"}**).
  
Nous disons que Microsoft 365 supprime Ken Meyer de chaque site, y compris ceux auxquels il n’a pas accès. Par conséquent, les résultats affichent des erreurs pour les sites auxquels il n’a pas accès. Nous pouvons utiliser une condition supplémentaire sur cette commande pour supprimer Ken Meyer uniquement des sites qui l’ont sur leur liste de connexion. Toutefois, les erreurs renvoyées n’ont aucun effet sur les sites eux-mêmes. L’exécution de cette commande peut prendre quelques minutes sur des centaines de sites, et non sur des heures de travail par le biais du centre d’administration Microsoft 365.
  
Voici un autre exemple d’opération en bloc. Utilisez cette commande pour ajouter *Bonnie Kearney*, un nouvel administrateur SharePoint, à tous les sites de l’Organisation :
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

L’interprétation de cette commande PowerShell est la suivante : obtenir tous les sites SharePoint de l’abonnement Microsoft 365 actuel et pour chaque site autoriser l’accès à Bonnie Kearney en ajoutant son nom de connexion au groupe membres du site (**foreach {Add-époux-site $ \_ . URL-LoginName "bkearney \@ litwareinc.com"-Group "members"}**).
  
## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>PowerShell pour Microsoft 365 est idéal pour le filtrage des données

Le centre d’administration 365 de Microsoft offre plusieurs méthodes pour filtrer vos données afin de localiser facilement un sous-ensemble ciblé d’informations. Par exemple, Exchange facilite le filtrage sur pratiquement toutes les propriétés de la boîte aux lettres d'un utilisateur. Par exemple, voici la liste des boîtes aux lettres de tous les utilisateurs vivant dans la ville de Bloomington :
  
![Exemple de recherche avancée dans le centre d’administration Microsoft 365 pour obtenir la liste des boîtes aux lettres de tous les utilisateurs vivant dans la ville de Bloomington.](../media/o365-powershell-advanced-search.png)
  
Le Centre d'administration Exchange vous permet également de combiner des critères de filtre. Par exemple, vous pouvez rechercher les boîtes aux lettres de toutes les personnes vivant dans Bloomington et travailler dans le service financier.
  
Toutefois, il existe des limitations à ce que vous pouvez faire dans le centre d’administration Exchange. Par exemple, vous ne pouviez pas trouver facilement les boîtes aux lettres de personnes vivant dans Bloomington *ou* San Diego, ou les boîtes aux lettres de toutes les personnes qui ne vivent pas dans Bloomington.
  
Vous pouvez utiliser la commande PowerShell suivante pour Microsoft 365 pour obtenir la liste des boîtes aux lettres de toutes les personnes vivant dans Bloomington ou San Diego :
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

Voici un exemple des résultats :
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel disposant d’une boîte aux lettres dans la ville de San Diego ou Bloomington (**où {$ \_ . RecipientTypeDetails-EQ "UserMailbox"-et ($ \_ . City-EQ "San Diego"-ou $ \_ . City-EQ "Bloomington")}**), puis affichez le nom et la ville de chacune d’entre elles (**Sélectionnez DisplayName, City**).
  
Et voici la commande permettant de répertorier toutes les boîtes aux lettres pour les personnes vivant à l’exception de Bloomington :
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Voici un exemple des résultats :
  
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

L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel disposant d’une boîte aux lettres qui ne se trouve pas dans la ville de Bloomington (**où {$ \_ . RecipientTypeDetails-EQ "UserMailbox"-et $ \_ . City-ne "Bloomington"}**), puis affichez le nom et la ville de chacun d’eux.
  
### <a name="use-wildcards"></a>Utiliser des caractères génériques

Vous pouvez également utiliser des caractères génériques dans vos filtres PowerShell pour faire correspondre une partie d’un nom. Par exemple, supposons que vous recherchez un compte d’utilisateur. Tout ce dont vous pouvez vous souvenir est que le nom de famille de l’utilisateur était *Anderson* ou peut-être *sur Henderson* ou *Jorgenson*.
  
Vous pouvez identifier cet utilisateur dans le centre d’administration 365 de Microsoft à l’aide de l’outil de recherche et en effectuant trois recherches différentes :
  
- Une sur  *Anderson* 
    
- Une sur  *Henderson* 
    
- Une sur  *Jorgenson* 
    
Étant donné que ces trois noms se terminent par « fils », vous pouvez indiquer à PowerShell d’afficher tous les utilisateurs dont le nom se termine par « fils ». Voici la commande :
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de l’abonnement Microsoft 365 actuel, mais utiliser un filtre qui répertorie uniquement les utilisateurs dont le nom de famille se termine par « fils » (**-Filter « {LastName-like " \* fils »}»**). \*Représente un jeu de caractères quelconque, c’est-à-dire des lettres dans le nom de famille de l’utilisateur.
  
## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>PowerShell pour Microsoft 365 facilite l’impression ou l’enregistrement des données

Le centre d’administration Microsoft 365 vous permet d’afficher des listes de données. Voici un exemple du centre d’administration de Skype entreprise Online affichant une liste d’utilisateurs qui ont été activés pour Skype entreprise Online :
  
![Exemple de liste d’utilisateurs ayant été activés pour Skype Entreprise Online, affichée dans le Centre d’administration de Skype Entreprise Online.](../media/o365-powershell-lync-users.png)
  
Pour enregistrer ces informations dans un fichier, vous devez le coller dans un document ou une feuille de calcul Microsoft Excel. Les deux cas peuvent nécessiter une mise en forme supplémentaire. En outre, le centre d’administration Microsoft 365 ne permet pas d’imprimer directement la liste affichée.
  
Heureusement, vous pouvez utiliser PowerShell pour non seulement afficher la liste, mais aussi l’enregistrer dans un fichier facile à importer dans Excel. Voici un exemple de commande permettant d’enregistrer des données utilisateur Skype entreprise Online dans un fichier de valeurs séparées par des virgules (CSV), qui peut ensuite être importé facilement sous forme de tableau dans une feuille de calcul Excel :
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Voici un exemple des résultats :
  
![Exemple de tableau importé dans une feuille de calcul Excel pour les données utilisateur de Skype entreprise Online qui a été enregistré dans un fichier de valeurs séparées par des virgules.](../media/o365-powershell-data-in-excel.png)
  
L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de Skype entreprise Online dans l’abonnement Microsoft 365 actuel (**Get-CsOnlineUser**); obtenez uniquement le nom d’utilisateur, l’UPN et l’emplacement (**Sélectionnez DisplayName, userPrincipalName, UsageLocation**); Enregistrez ensuite ces informations dans un fichier CSV nommé C : \\ logs \\SfBUsers.csv (**Export-CSV-path "C : \\ logs \\SfBUsers.csv"-NoTypeInformation**).
  
Vous pouvez également utiliser les options pour enregistrer cette liste sous la forme d’un fichier XML ou d’une page HTML. En fait, avec des commandes PowerShell supplémentaires, vous pouviez l’enregistrer directement sous forme de fichier Excel, avec n’importe quelle mise en forme personnalisée souhaitée.
  
Vous pouvez également envoyer la sortie d’une commande PowerShell qui affiche une liste directement sur l’imprimante par défaut dans Windows. Voici un exemple de commande :
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Le document imprimé aura l'apparence suivante :
  
![Exemple de document imprimé correspondant à la sortie d’une commande PowerShell envoyée directement à l’imprimante par défaut dans Windows.](../media/o365-powershell-printed-data.png)
  
L’interprétation de cette commande PowerShell est la suivante : obtenir tous les utilisateurs de Skype entreprise Online dans l’abonnement Microsoft 365 actuel ; obtenir uniquement le nom d’utilisateur, l’UPN et l’emplacement ; puis envoyez ces informations à l’imprimante Windows par défaut (**out-Printer**).
  
Le document imprimé a la même mise en forme que l’affichage dans la fenêtre de commande PowerShell. Pour obtenir une copie papier, ajoutez simplement **| Out-Printer** à la fin de la commande.
  
## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>PowerShell pour Microsoft 365 vous permet de gérer tous les produits serveur

Les composants qui composent Microsoft 365 sont conçus pour fonctionner ensemble. Par exemple, supposons que vous ajoutez un nouvel utilisateur à Microsoft 365 et que vous spécifiez des informations telles que le service et le numéro de téléphone de l’utilisateur. Ces informations seront disponibles si vous accédez aux informations de l’utilisateur dans l’un des services Microsoft 365 : Skype entreprise Online, Exchange ou SharePoint.
  
Toutefois, ceci concerne les informations communes qui couvrent une suite de produits. Les informations propres au produit, telles que les informations sur la boîte aux lettres Exchange d’un utilisateur, ne sont généralement pas disponibles dans la suite. Par exemple, les informations indiquant si la boîte aux lettres d’un utilisateur est activée ou non sont disponibles uniquement dans le centre d’administration Exchange.
  
Supposons que vous souhaitiez établir un rapport qui présente les informations suivantes pour tous les utilisateurs :
  
- Nom complet de l'utilisateur
    
- Si l’utilisateur est titulaire d’une licence pour Microsoft 365
    
- Si la boîte aux lettres Exchange de l'utilisateur a été activée
    
- Si l'utilisateur est activé pour Skype Entreprise Online
    
Vous ne pouvez pas facilement produire un tel rapport dans le centre d’administration Microsoft 365. Au lieu de cela, vous devez créer un document distinct pour stocker les informations, telles qu’une feuille de calcul Excel. Ensuite, obtenez tous les noms d’utilisateur et les informations de licence à partir du centre d’administration Microsoft 365, obtenez des informations de boîte aux lettres à partir du centre d’administration Exchange, obtenez des informations Skype entreprise Online à partir du centre d’administration de Skype entreprise Online, puis Combinez ces informations.
  
L’alternative consiste à utiliser un script PowerShell pour compiler le rapport pour vous.
  
L’exemple de script suivant est plus compliqué que les commandes que vous avez vues dans cet article. Toutefois, il illustre la possibilité d’utiliser PowerShell pour créer des vues d’informations difficiles à obtenir autrement. Voici le script à compiler et afficher la liste dont vous avez besoin :
  
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

Voici un exemple des résultats :
  
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

L’interprétation de ce script PowerShell est la suivante :  

1. Obtenir tous les utilisateurs dans l’abonnement Microsoft 365 actuel et stocker les informations dans une variable nommée *$x* (**$x = Get-AzureADUser**).
1. Démarrez une boucle qui s’exécute sur tous les utilisateurs de la variable $x (**foreach ($i dans $x)**).  
1. Définissez une variable nommée *$y* et stockez-y les informations de boîte aux lettres de l’utilisateur (**$y = Get-Mailbox-Identity $i. userPrincipalName**).
1. Ajoutez une nouvelle propriété aux informations utilisateur nommées *IsMailBoxEnabled*. Définissez-la sur la valeur de la propriété IsMailBoxEnabled de la boîte aux lettres de l’utilisateur (**$i | Add-Member-MemberType NoteProperty-Name IsMailBoxEnabled-value $y. IsMailBoxEnabled**).
1. Définissez une variable nommée *$y*et stockez-y les informations Skype entreprise Online de l’utilisateur (**$y = Get-CsOnlineUser-Identity $i. userPrincipalName**).
1. Ajoutez une nouvelle propriété aux informations utilisateur nommées *EnabledForSfB*. Définissez-la sur la valeur de la propriété Enabled des informations Skype entreprise Online de l’utilisateur (**$i | Add-Member-MemberType NoteProperty-Name EnabledForSfB-value $y. Enabled**).
1. Affichez la liste des utilisateurs, mais n’incluez que leur nom, qu’ils soient sous licence, et les deux nouvelles propriétés qui indiquent si leur boîte aux lettres est activée et si elles sont activées pour Skype entreprise Online (**$x | Sélectionnez DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).
  
## <a name="see-also"></a>Voir aussi

[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
  
[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Utilisez Windows PowerShell pour créer des rapports dans Microsoft 365](use-windows-powershell-to-create-reports-in-microsoft-365.md)
