---
title: Configurer la Gestion des droits relatifs à l’information (Information Rights Management, IRM) dans le Centre d’administration SharePoint
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- SPO_Content
localization_priority: Normal
search.appverid:
- SPO160
- MET150
ms.assetid: 239ce6eb-4e81-42db-bf86-a01362fed65c
description: Découvrez comment utiliser la gestion des droits SharePoint Online par le biais Microsoft Azure Active Directory RMS (Rights Management Services) pour protéger SharePoint listes et bibliothèques de documents.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 32424165be24614a43f44d78791ffac334969bed
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59205852"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Configurer la Gestion des droits relatifs à l’information (Information Rights Management, IRM) dans le Centre d’administration SharePoint

Dans SharePoint Online, la protection IRM est appliquée aux fichiers au niveau de la liste et de la bibliothèque. Pour que votre organisation puisse utiliser la protection IRM, vous devez commencer par configurer la gestion des droits. La gestion des droits relatifs à l’information s’appuie sur le service Azure Rights Management d’Azure information protection pour chiffrer et affecter des restrictions d’utilisation. Certains Microsoft 365 incluent Azure Rights Management, mais pas tous. Pour en savoir plus, [lisez comment les applications et](/azure/information-protection/understand-explore/office-apps-services-support)les services Office la prise en charge des Azure Rights Management .
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>Activer le service IRM à l’aide SharePoint’administration centrale

Pour que votre organisation puisse protéger les SharePoint et les bibliothèques, vous devez d’abord activer le service Rights Management pour votre organisation. Pour en savoir plus, [consultez l’Azure Rights Management](/information-protection/deploy-use/activate-service). Vous devez utiliser un compte professionnel ou scolaire qui dispose de privilèges d’administrateur général pour activer le service Rights Management. Dans le cas contraire, vous ne pourrez pas utiliser les fonctionnalités IRM avec SharePoint Online.
  
Après avoir activé le service Rights Management, connectez-vous au centre d’administration SharePoint pour activer IRM.
  
1. Connectez-vous en tant qu’administrateur global ou SharePoint administrateur.
    
2. Sélectionnez l’icône du lanceur d’applications L’icône du lanceur ![ d’applications Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) dans le coin supérieur gauche et choisissez **Admin** pour ouvrir le Centre d'administration Microsoft 365. (Si vous ne voyez pas la vignette Administrateur, vous n’avez pas d’autorisations d’administrateur dans votre organisation.) 
    
3. Dans le volet gauche, choisissez Centres **d’administration** \> **SharePoint**.
    
4. Dans le volet gauche, choisissez les **paramètres,** puis choisissez **la page des paramètres classiques.**
    
5. Dans la section Gestion des droits de l’information **(IRM),** choisissez Utiliser le service IRM spécifié dans votre **configuration,** puis sélectionnez Actualiser la gestion des droits **Paramètres**. Après avoir actualisé les paramètres IRM, les membres de votre organisation peuvent commencer à utiliser irm dans leurs listes SharePoint de documents et bibliothèques de documents. Toutefois, les options de cette option peuvent prendre jusqu’à une heure pour s’Paramètres bibliothèque et liste Paramètres.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>Listes et bibliothèques de documents SharePoint irm
<a name="__toc220831191"> </a>

Après l’actualisation des paramètres IRM, les propriétaires de sites peuvent protéger leurs SharePoint listes et bibliothèques de documents. Pour plus d’informations, voir [Apply Information Rights Management to a list or library](apply-irm-to-a-list-or-library.md).
  
Lorsque les propriétaires de site activent irm pour une liste ou une bibliothèque, ils peuvent protéger tous les types de fichiers pris en charge dans cette liste ou bibliothèque. Lorsque irm est activé pour une bibliothèque, la gestion des droits s’applique à tous les fichiers de cette bibliothèque. Lorsque vous activez irm pour une liste, la gestion des droits s’applique uniquement aux fichiers joints aux éléments de liste, et non aux éléments de liste réels.
  
Lorsque des personnes téléchargent des fichiers dans une liste ou une bibliothèque activée pour IRM, les fichiers sont chiffrés afin que seules les personnes autorisées peuvent les afficher. Chaque fichier géré par des droits contient également une licence d’émission qui impose des restrictions aux personnes qui visualisent le fichier. Les restrictions classiques incluent la lecture seule d’un fichier, la désactivation de la copie du texte, l’interdiction d’enregistrer une copie locale et l’impression du fichier. Les programmes clients qui peuvent lire les types de fichiers pris en charge par IRM utilisent la licence d’émission dans le fichier géré par des droits pour appliquer ces restrictions. C’est ainsi qu’un fichier géré par des droits conserve sa protection même après son téléchargement. Pour activer irm sur une liste ou une bibliothèque, voir Appliquer la gestion des droits d’information [à une liste ou une bibliothèque.](apply-irm-to-a-list-or-library.md)
  
Vous ne pouvez pas créer ou modifier des documents dans une bibliothèque activée pour IRM à l’Office dans un navigateur. Au lieu de cela, une personne à la fois peut télécharger et modifier des fichiers chiffrés par IRM. Utilisez l’enregistrement et l’check-out pour gérer la  *co-auteur*  ou la authoring entre plusieurs utilisateurs. 
  
Lorsque vous téléchargez un fichier PDF à partir d’une bibliothèque protégée par IRM, Microsoft 365 crée un fichier PDF protégé. L’extension du fichier ne change pas, mais le fichier est protégé. Pour afficher ce fichier, vous aurez besoin de la visionneuse Azure Information Protection, du client Azure Information Protection complet ou d’une autre application qui prend en charge l’affichage des fichiers PDF protégés. 
  
SharePoint Online prend en charge le chiffrement des types de fichiers suivants :
  
- PDF
    
- Formats de fichier 97-2003 pour les programmes Microsoft Office suivants : Word, Excel et PowerPoint
    
- Les Office formats Open XML pour les programmes Microsoft Office suivants : Word, Excel et PowerPoint
    
- Format XPS (XML Paper Specification)
 
> [!NOTE]
> La protection IRM ne peut pas être appliquée aux documents protégés (tels que les fichiers PDF signés numériquement), car SharePoint doit ouvrir le document au chargement. 

## <a name="next-steps"></a>Étapes suivantes
<a name="__toc220831191"> </a>

Une fois que vous avez activé irm pour SharePoint Online, vous pouvez commencer à appliquer la gestion des droits aux listes et aux bibliothèques. Pour plus d’informations, voir [Apply Information Rights Management to a list or library](apply-irm-to-a-list-or-library.md).
  
Le nouveau client Synchronisation OneDrive pour Windows prend désormais en charge la synchronisation des bibliothèques de documents et des emplacements OneDrive protégés par SharePoint IRM (à condition que le paramètre IRM de la bibliothèque n’expire pas). Pour plus d’informations ou pour commencer à déployer le nouveau client de synchronisation, voir Déployer le nouveau [client Synchronisation OneDrive pour Windows](/onedrive/deploy-on-windows).
  
[Haut de la page](set-up-irm-in-sp-admin-center.md)