---
title: Guide de mise à niveau manuelle de Windows 7 vers Windows 10
ms.author: jogruszc
author: JGruszczyk
manager: jemed
ms.date: 06/10/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Guide de mise à niveau manuelle de Windows 7 vers Windows 10.
ms.openlocfilehash: 13cdb56b52655ed81932601dd3ff97c90c1daad8
ms.sourcegitcommit: 70e920f76526f47fc849df615de4569e0ac2f4be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033679"
---
# <a name="windows-7-to-windows-10-manual-upgrade-step-by-step-guide"></a>Guide détaillé de mise à niveau manuelle de Windows 7 vers Windows 10

Cet article décrit le processus de mise à niveau manuelle d’un PC sous Windows 7 Entreprise vers Windows 10 Entreprise. Pour les autres versions de Windows 7, telles que les versions Famille et Professionnel, le processus est très similaire, mais vous avez également la possibilité de procéder à une mise à niveau directement à l’aide de l’outil de création de support. Les mises à niveau pour toutes les versions de Windows 7 vers Windows 10 nécessitent une clé de produit valide et une version correspondante ou supérieure de Windows. Par exemple, Windows 7 Professionnel peut être mis à niveau vers Windows 10 Professionnel, mais ne peut pas être mis à niveau vers Windows 10 Famille. Windows 7 Édition Intégrale doit être mis à niveau vers Windows 10 Professionnel.

## <a name="windows-10-upgrades-using-the-media-creation-tool-or-iso-files"></a>Mises à niveau de Windows 10 à l’aide de l’outil de création de supports ou de fichiers ISO

Vous pouvez effectuer une mise à niveau vers Windows 10 directement à l’aide de [l’outil de création de supports](https://www.microsoft.com/software-download/windows10ISO) ou l’utiliser pour télécharger Windows 10 sous la forme d’un fichier ISO. Vous devez noter si votre système actuel est un système 32 ou 64 bits, quelle est la langue par défaut de votre système et la version de Windows 7 (par exemple, Famille, Professionnel ou Entreprise). Dans Windows 7, ces informations se trouvent dans Panneau de configuration \> Système et sécurité \> Système. L’outil de création de support ne prend pas en charge les mises à niveau, la création de médias d’installation ou le téléchargement de fichiers ISO pour Windows 10 Enterprise. Windows 10 Entreprise est requis si vous effectuez une mise à niveau à partir de Windows 7 Entreprise.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-1.png)

Lorsque vous procédez à la mise à niveau de Windows 7 Entreprise vers Windows 10 Entreprise, vous devez télécharger le fichier ISO qui correspond à votre langue et à l’architecture de votre système (32 bits ou 64 bits) à partir du [centre de gestion des licences en volume](https://www.microsoft.com/licensing/servicecenter/default.aspx).

Si vous envisagez d’effectuer la mise à niveau à l’aide d’un fichier ISO, vous devrez extraire les fichiers au sein de la plateforme ISO vers votre système de fichiers local ou vers un lecteur amovible. Vous pouvez également graver le fichier ISO sur un DVD. Vous pouvez extraire les fichiers d’installation dans la plateforme ISO à l’aide d’un PC Windows 8 ou version ultérieure, puis enregistrer ces fichiers sur un espace de stockage USB amovible ou utiliser une application telle que [7zip](https://www.7-zip.org/) pour extraire le contenu de votre fichier ISO vers un dossier sur votre disque local dans Windows 7.

Une fois le support d’installation disponible dans Windows 7, vous pouvez lancer la mise à niveau en exécutant setup.exe, comme expliqué ci-dessous.

**Conseil important : pour une mise à niveau sur place dans laquelle les applications et vos données sont migrées vers Windows 10, vous devez lancer le processus à partir d’une session Windows 7 en cours d’exécution. Le démarrage de l’installation de supports à partir d’un DVD ou d’un lecteur USB n’offre pas la possibilité de conserver vos applications et fichiers : le système effectue une nouvelle installation de Windows 10.**

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-2.png)

Au cours de l’installation de Windows 10, vous serez guidé dans le processus d’installation. Le premier écran offre une option permettant de télécharger les mises à jour, les pilotes ainsi que des fonctionnalités facultatives. Il est recommandé de procéder à ces téléchargements pour garantir la réussite de la mise à niveau

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-3.png)

Une fois les mises à jour appliquées, le programme d’installation de Windows 10 passe à la phase suivante, la sélection d’une image. C’est là que vous devez sélectionner votre version de Windows. Ici, étant donné que le PC tourne sous Windows 7 Entreprise, vous devez sélectionner Windows 10 Entreprise.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-4.png)

L’écran suivant de l’installation de Windows 10 affiche des notifications et les termes du contrat de licence applicables. Après avoir lu et bien compris les notifications et les termes du contrat, cliquez sur « Accepter » pour continuer ou sur « Refuser » pour annuler.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-5.png)

Le programme d’installation de Windows 10 recherche alors des mises à jour supplémentaires.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-6.png)

Quand il a fini cette recherche, le programme d’installation de Windows 10 est prêt à procéder à l’installation. Par défaut, il est configuré de manière à installer Windows 10 et à conserver vos fichiers et applications personnels. Nous vous recommandons de choisir cette option. Si vous voulez consulter des options supplémentaires, cliquez sur « Modifier les éléments à conserver ». Sinon, cliquez sur « Installer ».

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-7.png)

Si vous sélectionnez « Modifier ce que vous voulez conserver », les options suivantes s’affichent :

« Conserver uniquement les fichiers personnels » empêche le transfert des applications que vous avez installées et de vos paramétrages de Windows 7 vers Windows 10. Seuls vos fichiers et vos comptes d’utilisateurs seront transférés. Si vous choisissez cette option, vous devrez réinstaller vos applications. Nous vous recommandons donc d’utiliser uniquement cette option si vous êtes certain de pouvoir réinstaller et configurer les applications dont vous aurez besoin après l’installation de Windows. Si ce n’est pas le cas, choisissez l’option par défaut « Conserver les fichiers personnels et applications ».

« Ne rien conserver » supprime vos fichiers, applications et paramètres et effectue une nouvelle installation de Windows. Utilisez cette option uniquement si vous avez précédemment sauvegardé les données que vous voulez conserver et si vous pouvez réinstaller vos applications vous-même.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-8.png)

Le programme d’installation de Windows 10 recherche de nouveau les mises à jour en fonction de ce que vous avez sélectionné dans l’écran précédent.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-9.png)

Windows 10 procède alors à l’installation, ce qui va prendre plusieurs minutes, et, si vous avez choisi de conserver vos fichiers personnels et applications, tous ces éléments se trouveront aux mêmes emplacements et vos applications seront désormais disponibles sous Windows 10.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-10.png)

## 

## <a name="recovery-in-windows-10"></a>Récupération dans Windows 10

Lorsque Windows 10 est installé, l’option de récupération dans Windows 10 vous laisse un délai de 10 jours pour effectuer une rétrogradation vers Windows 7. Ceci est utile si un appareil ou une application de votre système ne fonctionne pas correctement et que vous devez revenir à l’installation précédente de Windows 7. Après 10 jours, par défaut, Windows 10 libère l’espace utilisé par vos fichiers de récupération Windows 7 sur votre disque dur et supprime les fichiers de l’installation précédente. Windows 7 sera alors définitivement supprimé et vous ne pourrez pas le rétablir, mais vos applications et fichiers personnels sont conservés dans Windows 10.

Pour démarrer le processus de rétrogradation vers Windows 7, veuillez accéder à la section Paramètres \> Mise à jour et sécurité \> Récupération. Dans la section Revenir à Windows 7, sélectionnez « Démarrer ».

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-11.png)

Windows 10 vous demande alors pourquoi vous revenez à la version précédente. Si c’est pour une raison technique, votre réponse est utile pour nous aider à résoudre le problème et assurer que d’autres utilisateurs peuvent profiter de votre expérience.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-12.png)

Dans de nombreux cas, il existe déjà des mises à jour de votre version de Windows 10, ce qui peut résoudre ces problèmes techniques. Nous vous recommandons de rechercher des mises à jour et, si elles existent et que vous les installez, de vérifier si ces mises à jour ont résolu le problème.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-13.png)

Si les mises à jour ne permettent pas de résoudre les problèmes et que vous devez revenir à l’installation précédente de Windows 7, il est possible que certaines applications nécessitent une réinstallation (par exemple, toutes les applications installées pendant que le PC tournait sous Windows 10) et certains paramètres peuvent être perdus. Toutefois, tous les fichiers et documents enregistrés en local pendant l’utilisation sous Windows 10 sont préservés lorsque vous revenez à Windows 7. 

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-14.png)

Avant de commencer, vérifiez que vous avez sous la main les informations concernant votre compte local ou un compte de domaine et le mot de passe pour l’installation précédente de Windows 7.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-15.png)

Vous pouvez alors lancer le processus pour revenir à Windows 7. Après quelques minutes, votre PC redémarre sous Windows 7 avec la même expérience utilisateur que celle précédant la mise à niveau vers Windows 10.

![](media/windows-7-to-windows-10-upgrade-manual-media/windows-7-to-windows-10-upgrade-manual-media-16.png)

## <a name="moving-to-windows-10-on-a-new-pc"></a>Migration vers Windows 10 sur un nouveau PC

Une autre option recommandée consiste à migrer vers Windows 10 sur un nouvel ordinateur. Si c’est votre choix, vous pouvez transférer vos fichiers à partir de votre ancien ordinateur à l'aide de la sauvegarde [OneDrive](https://support.office.com/article/b5e918be-0fd4-4095-98da-bceed57f8e0c?ocid=MoveToWindows10), de la fonctionnalité [Sauvegarder et restaurer intégrée à Windows](https://support.microsoft.com/help/4469209?ocid=MoveToWindows10), manuellement à l’aide d’un [périphérique de stockage externe](https://support.microsoft.com/help/4465814/windows-7-move-files-off-pc-with-an-external-storage-device?ocid=MoveToWindows10) ou avec des outils tels que [PCmover Express de Laplink](https://www.microsoft.com/windows/transfer-your-data). Quelle que soit l’option que vous choisissez, vous devrez réinstaller toutes les applications requises non incluses dans Windows 10. Si vous souhaitez en apprendre davantage sur les options de migration manuelle d’un PC existant exécutant Windows 7 vers un nouveau PC exécutant Windows 10, veuillez consulter la page [Passage à un PC Windows 10](https://support.microsoft.com/help/4229823?ocid=MoveToWindows10) du site Windows support.

## <a name="desktop-deployment-centerhttpsakamshowtoshift"></a>[Centre de déploiement du bureau moderne](https://aka.ms/howtoshift)