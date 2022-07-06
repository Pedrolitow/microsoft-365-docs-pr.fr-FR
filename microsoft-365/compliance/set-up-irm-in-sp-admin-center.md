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
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 239ce6eb-4e81-42db-bf86-a01362fed65c
description: Découvrez comment utiliser la gestion des droits relatifs à l’information (IRM) SharePoint Online par le biais de Microsoft Azure Active Directory Rights Management Services (RMS) pour protéger les listes Et bibliothèques de documents SharePoint.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: af8f19fe455c1aca1d6b7aab045a9aea5b5efee5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632044"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Configurer la Gestion des droits relatifs à l’information (Information Rights Management, IRM) dans le Centre d’administration SharePoint

Dans SharePoint Online, la protection IRM est appliquée aux fichiers au niveau de la liste et de la bibliothèque. Pour que votre organisation puisse utiliser la protection IRM, vous devez commencer par configurer la gestion des droits. La gestion des droits relatifs à l’information s’appuie sur le service Azure Rights Management d’Azure information protection pour chiffrer et affecter des restrictions d’utilisation. Certains plans Microsoft 365 incluent Azure Rights Management, mais pas tous. Pour en savoir plus, consultez [comment les applications et services Office prennent en charge Azure Rights Management](/azure/information-protection/understand-explore/office-apps-services-support).
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>Activer le service IRM à l’aide du Centre d’administration SharePoint

Pour que votre organisation puisse protéger les listes et bibliothèques SharePoint par IRM, vous devez d’abord activer le service Rights Management pour votre organisation. Pour savoir comment voir [Activation de Azure Rights Management](/information-protection/deploy-use/activate-service). Vous devez utiliser un compte professionnel ou scolaire disposant de privilèges d’administrateur général pour activer le service Rights Management. Sinon, vous ne pourrez pas utiliser les fonctionnalités IRM avec SharePoint Online.
  
Après avoir activé le service Rights Management, connectez-vous au Centre d’administration SharePoint pour activer irm.
  
1. Connectez-vous en tant qu’administrateur général ou administrateur SharePoint.
    
2. Sélectionnez l’icône ![du lanceur d’applications L’icône du lanceur d’applications dans Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) en haut à gauche et choisissez **Administration** pour ouvrir le Centre d'administration Microsoft 365. (Si vous ne voyez pas la vignette Administration, vous n’avez pas d’autorisations d’administrateur dans votre organisation.) 
    
3. Dans le volet gauche, choisissez **Administration centre** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">d’administration SharePoint</a>.
    
4. Dans le volet gauche, choisissez **paramètres**, puis choisissez **la page des paramètres classiques**.
    
5. Dans la section **Gestion des droits relatifs à l’information (IRM),** choisissez **Utiliser le service IRM spécifié dans votre configuration**, puis choisissez **Actualiser les paramètres** IRM. Après avoir actualisé les paramètres IRM, les membres de votre organisation peuvent commencer à utiliser irm dans leurs listes SharePoint et bibliothèques de documents. Toutefois, l’affichage des options à cette fin peut prendre jusqu’à une heure dans les paramètres de bibliothèque et les paramètres de liste.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>Bibliothèques et listes de documents SharePoint compatibles avec IRM
<a name="__toc220831191"> </a>

Après avoir actualisé les paramètres IRM, les propriétaires de sites peuvent protéger leurs listes Et bibliothèques de documents SharePoint. Pour plus d’informations, consultez [Appliquer la gestion des droits relatifs à l’information à une liste ou une bibliothèque](apply-irm-to-a-list-or-library.md).
  
Lorsque les propriétaires de sites activent irm pour une liste ou une bibliothèque, ils peuvent protéger tous les types de fichiers pris en charge dans cette liste ou bibliothèque. Lorsque irm est activée pour une bibliothèque, la gestion des droits s’applique à tous les fichiers de cette bibliothèque. Lorsque vous activez irm pour une liste, la gestion des droits s’applique uniquement aux fichiers attachés aux éléments de liste, et non aux éléments de liste réels.
  
Lorsque des personnes téléchargent des fichiers dans une liste ou une bibliothèque compatible IRM, les fichiers sont chiffrés afin que seules les personnes autorisées puissent les afficher. Chaque fichier géré par des droits contient également une licence d’émission qui impose des restrictions aux personnes qui consultent le fichier. Les restrictions classiques incluent la création d’un fichier en lecture seule, la désactivation de la copie de texte, l’interdiction pour les utilisateurs d’enregistrer une copie locale et l’impression du fichier. Les programmes clients qui peuvent lire les types de fichiers pris en charge par IRM utilisent la licence d’émission dans le fichier géré par des droits pour appliquer ces restrictions. C’est ainsi qu’un fichier géré par des droits conserve sa protection même après son téléchargement. Pour activer la gestion des droits relatifs à l’information sur une liste ou une bibliothèque, consultez [Appliquer la gestion des droits relatifs à l’information à une liste ou une bibliothèque](apply-irm-to-a-list-or-library.md).
  
Vous ne pouvez pas créer ou modifier des documents dans une bibliothèque compatible IRM à l’aide d’Office dans un navigateur. Au lieu de cela, une personne à la fois peut télécharger et modifier des fichiers chiffrés par IRM. Utilisez l’archivage et l’extraction pour gérer  *la co-création* ou la création entre plusieurs utilisateurs. 
  
Lorsque vous téléchargez un fichier PDF à partir d’une bibliothèque protégée par IRM, Microsoft 365 crée un fichier PDF protégé. L’extension du fichier ne change pas, mais le fichier est protégé. Pour afficher ce fichier, vous avez besoin de la visionneuse Azure Information Protection, du client Azure Information Protection complet ou d’une autre application qui prend en charge l’affichage des fichiers PDF protégés.
  
SharePoint Online prend en charge le chiffrement des types de fichiers suivants :
  
- PDF
    
- Formats de fichier 97-2003 pour les programmes Microsoft Office suivants : Word, Excel et PowerPoint
    
- Formats Office Open XML pour les programmes Microsoft Office suivants : Word, Excel et PowerPoint
    
- Format XPS (XML Paper Specification)
 
> [!NOTE]
> La protection IRM ne peut pas être appliquée aux documents protégés (tels que les fichiers PDF signés numériquement), car SharePoint doit ouvrir le document lors du chargement. 

## <a name="next-steps"></a>Étapes suivantes
<a name="__toc220831191"> </a>

Une fois que vous avez activé irm pour SharePoint Online, vous pouvez commencer à appliquer la gestion des droits aux listes et bibliothèques. Pour plus d’informations, consultez [Appliquer la gestion des droits relatifs à l’information à une liste ou bibliothèque](apply-irm-to-a-list-or-library.md).
  
Le nouveau client Synchronisation OneDrive pour Windows prend désormais en charge la synchronisation des bibliothèques de documents SharePoint protégées par IRM et des emplacements OneDrive (tant que le paramètre IRM de la bibliothèque n’est pas défini pour expirer les droits d’accès aux documents). Pour plus d’informations ou pour commencer à déployer le nouveau client de synchronisation, consultez [Déployer le nouveau client Synchronisation OneDrive pour Windows](/onedrive/deploy-on-windows).
  
[Haut de la page](set-up-irm-in-sp-admin-center.md)
