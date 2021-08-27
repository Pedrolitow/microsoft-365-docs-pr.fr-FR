---
title: Appliquer la Gestion des droits à l’information (IRM) à une liste ou une bibliothèque
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 7/2/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.assetid: 3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1
ms.collection:
- M365-security-compliance
- SPO_Content
description: Vous pouvez utiliser la Gestion des droits numériques (IRM) pour contrôler et protéger les fichiers téléchargés à partir de listes ou de bibliothèques.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 84f0443cd31f26549dc1f5dc06be6e7bf52b05dc
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58573666"
---
# <a name="apply-information-rights-management-irm-to-a-list-or-library"></a>Appliquer la Gestion des droits à l’information (IRM) à une liste ou une bibliothèque

Vous pouvez utiliser la Gestion des droits numériques (IRM) pour contrôler et protéger les fichiers téléchargés à partir de listes ou de bibliothèques. Cette fonctionnalité est uniquement prise en charge dans le cloud global De Microsoft. Irm n’est pas pris en charge pour SharePoint listes et bibliothèques dans les déploiements cloud nationaux.
  
## <a name="administrator-preparations-before-applying-irm"></a>Préparations de l’administrateur avant l’application de l’IRM

- Le service Azure Rights Management (Azure RMS) d’Azure Information Protection et l’équivalent local, services AD RMS (Active Directory Rights Management Services) (AD RMS), assurent la gestion des droits d’information pour les sites. Aucune installation distincte ou supplémentaire n’est requise.

- Avant d’appliquer irm à une liste ou une bibliothèque, vous devez activer irm pour votre site. Vous aurez besoin d’autorisations d’administrateur pour activer IRM.

- Pour appliquer irm à une liste ou une bibliothèque, vous devez avoir des autorisations d’administrateur pour cette liste ou bibliothèque.

- Si vous utilisez SharePoint Online, vos utilisateurs peuvent connaître des délai d’SharePoint lors du téléchargement de fichiers protégés par IRM plus volumineux. Pour éviter les délai d’Office, utilisez vos programmes d’Office pour appliquer la protection IRM et stockez des fichiers plus volumineux dans une bibliothèque SharePoint qui n’utilise pas irm.

> [!NOTE]
> Si vous utilisez SharePoint Server 2013, un administrateur de serveur doit installer des logiciels de protection sur tous les serveurs Web frontaux pour chaque type de fichier que les membres de votre organisation souhaitent protéger à l’aide de l’IRM.
  
## <a name="apply-irm-to-a-list-or-library"></a>Appliquer irm à une liste ou une bibliothèque
<a name="__toc256598179"> </a>

![Gestion des droits Paramètres.](../media/1b708102-9c90-42b0-b255-ef0e72d0be88.png)
  
1. Go to the list or library for which you want to configure IRM.

2. Dans le ruban, sélectionnez **l’onglet** Bibliothèque, puis **sélectionnez Bibliothèque Paramètres**. (Si vous travaillez dans une liste, sélectionnez l’onglet Liste, puis sélectionnez Liste **Paramètres**). 
    
    ![SharePoint Bibliothèque Paramètres boutons du Ruban.](../media/cdf718fa-d792-40fc-8026-00c3b80b9e05.png)
  
3. Sous **Autorisations et gestion,** sélectionnez **Gestion des droits de l’information.** Si le lien Gestion des droits de l’information n’apparaît pas, il se peut que la gestion des droits irm ne soit pas activée pour votre site. Contactez votre administrateur de serveur pour voir si vous pouvez activer irm pour votre site. Le **lien Gestion des droits de** l’information n’apparaît pas pour les bibliothèques d’images.

4. Dans la page Gestion des droits relatifs à l’information **Paramètres,** cochez la case Restreindre l’autorisation aux **documents** de cette bibliothèque lors du téléchargement pour appliquer une autorisation restreinte aux documents téléchargés par les utilisateurs à partir de cette liste ou bibliothèque.

5. Dans la **zone De titre Créer une stratégie d’autorisation,** entrez un nom descriptif pour la stratégie. Utilisez un nom qui vous permet d’identifier cette stratégie à partir d’autres stratégies. Par exemple, utilisez **La société confidentielle pour** appliquer des autorisations restreintes à une liste ou une bibliothèque qui contient des documents confidentiels de l’entreprise.

6. Dans la zone Ajouter une **description** de stratégie d’autorisation, tapez une description qui s’affiche pour les personnes qui utilisent cette liste ou cette bibliothèque qui explique comment elles doivent gérer les documents de cette liste ou bibliothèque. Par exemple, vous pouvez taper Discuter du contenu de ce **document** uniquement avec d’autres employés si vous souhaitez restreindre l’accès aux informations de ces documents aux employés internes. 

7. Pour appliquer des restrictions supplémentaires aux documents de cette liste ou bibliothèque, sélectionnez Afficher les **options** et faites l’une des actions suivantes :

|**Pour cela :**|**Pour ce faire :**|
|:-----|:-----|
|Autoriser les utilisateurs à imprimer des documents à partir de cette liste ou bibliothèque|Cochez **la case Autoriser les visionneuses à** imprimer.|
|Autorisez les personnes ayant au moins l’autorisation Afficher les éléments à exécuter du code ou des macros incorporés sur un document.|Cochez la case Autoriser les **visionneuses à exécuter** un script et un lecteur d’écran pour fonctionner sur les documents téléchargés. Si vous sélectionnez cette option, les utilisateurs peuvent exécuter du code pour extraire le contenu d’un document.           |
|Sélectionnez cette option si vous souhaitez restreindre l’accès au contenu à une période spécifiée. Si vous sélectionnez cette option, les licences d’émission des personnes pour accéder au contenu expireront après le nombre de jours spécifié, et les utilisateurs devront revenir sur le serveur pour vérifier leurs informations d’identification et télécharger une nouvelle copie.|Cochez la case Après le téléchargement, les droits d’accès aux documents expireront après ce nombre de jours **(1-365),** puis spécifiez le nombre de jours pendant lesquels vous souhaitez que le document soit consultable.|
| Empêcher les personnes de télécharger des documents qui ne la prise en charge de l’IRM dans cette liste ou cette bibliothèque. Si vous sélectionnez cette option, les personnes ne pourront télécharger aucun des types de fichiers suivants : les types de fichiers qui n’ont pas de logiciels de protection IRM correspondants installés sur tous les serveurs web frontaux. Types de fichiers SharePoint Server 2010 ne peuvent pas déchiffrer. Types de fichiers protégés par IRM dans un autre programme.|Cochez la case Ne pas autoriser les utilisateurs à télécharger des documents qui **ne la prisent pas en charge.**|
|Supprimez les autorisations restreintes de cette liste ou bibliothèque à une date spécifique.|Cochez la case Arrêter **de restreindre l’accès** à la bibliothèque, puis sélectionnez la date de votre choix.|
|Contrôler l’intervalle de mise en cache des informations d’identification pour le programme sous licence pour ouvrir le document.|Sélectionnez **la case à cocher Utilisateurs** pour vérifier leurs informations d’identification à l’aide de cet intervalle (jours), puis entrez l’intervalle de mise en cache des informations d’identification en nombre de jours.|
|Autorisez la protection de groupe afin que les utilisateurs peuvent partager avec les membres du même groupe.|Sélectionnez **Autoriser la protection de** groupe, puis entrez le nom du groupe pour le partage.|

8. Une fois que vous avez terminé de sélectionner les options de votre choix, sélectionnez **OK.**
  
## <a name="what-is-information-rights-management"></a>Qu’est-ce que la Gestion des droits de l’information ?
<a name="__toc256598175"> </a>

La Gestion des droits numériques (IRM) vous permet de limiter les actions que les utilisateurs peuvent prendre sur les fichiers qui ont été téléchargés à partir de listes ou de bibliothèques. IRM chiffre les fichiers téléchargés et limite l’ensemble des utilisateurs et des programmes autorisés à déchiffrer ces fichiers. IRM peut également limiter les droits des utilisateurs qui sont autorisés à lire des fichiers, pour leur interdire par exemple d’effectuer des actions telles qu’imprimer des copies des fichiers ou copier du texte de ceux-ci.
  
Vous pouvez utiliser irm sur des listes ou des bibliothèques pour limiter la diffusion de contenu sensible. Par exemple, si vous créez une bibliothèque de documents pour partager des informations sur les produits à venir avec des représentants commerciaux sélectionnés, vous pouvez utiliser la gestion des droits numériques pour empêcher ces personnes de partager ce contenu avec d’autres employés de l’entreprise.
  
Sur un site, vous appliquez la gestion des droits numériques à l’ensemble d’une liste ou d’une bibliothèque, plutôt qu’à des fichiers individuels. Cela facilite la mise en place d’un niveau de protection cohérent pour l’ensemble d’un ensemble de documents ou de fichiers. Irm peut ainsi aider votre organisation à appliquer des stratégies d’entreprise qui régissent l’utilisation et la diffusion d’informations confidentielles ou propriétaires.
  
> [!NOTE]
> Les informations de cette page concernant la gestion des droits de l’information ont la place sur les termes qui font référence à la « Gestion des droits informatiques » dans les contrats de licence Microsoft SharePoint Server 2013 et SharePoint Server 2016. 
  
### <a name="how-irm-can-help-protect-content"></a>Comment IRM peut aider à protéger le contenu
<a name="__toc256598176"> </a>

La gestion des droits numériques permet de protéger le contenu restreint des manières suivantes :
  
- Permet d’empêcher une visionneuse autorisée de copier, modifier, imprimer, télécopier ou copier et coller le contenu pour une utilisation non autorisée
    
- Permet d’empêcher une visionneuse autorisée de copier le contenu à l’aide de la fonctionnalité d’impression de l’écran dans Microsoft Windows
    
- Permet d’empêcher une visionneuse non autorisée d’afficher le contenu s’il est envoyé par courrier électronique après son téléchargement à partir du serveur
    
- Limite l’accès au contenu à une période spécifiée, après quoi les utilisateurs doivent confirmer leurs informations d’identification et télécharger à nouveau le contenu.
    
- Permet d’appliquer des stratégies d’entreprise qui régissent l’utilisation et la diffusion de contenu au sein de votre organisation
    
### <a name="how-irm-cannot-help-protect-content"></a>Comment irm ne peut pas contribuer à protéger le contenu
<a name="__toc256598177"> </a>

La gestion des droits numériques ne peut pas protéger le contenu restreint des cas suivants :
  
- Effacement, vol, capture ou transmission par des programmes malveillants tels que les chevaux de France, les enregistreurs de frappes et certains types de logiciels espions
    
- Perte ou corruption en raison des actions des virus de l’ordinateur
    
- Copie ou retypage manuel du contenu à partir de l’écran
    
- Photographie numérique ou cinématographique de contenu affiché à l’écran
    
- Copie via l’utilisation de programmes tiers de capture d’écran
    
- Copie des métadonnées de contenu (valeurs de colonne) via l’utilisation de programmes de capture d’écran tiers ou d’une action copier-coller
  
## <a name="how-irm-works-for-lists-and-libraries"></a>Fonctionnement de l’IRM pour les listes et les bibliothèques
<a name="__toc256598178"> </a>

La protection IRM est appliquée aux fichiers au niveau de la liste ou de la bibliothèque. Lorsque irm est activé pour une bibliothèque, la gestion des droits s’applique à tous les fichiers de cette bibliothèque. Lorsque irm est activé pour une liste, la gestion des droits s’applique uniquement aux fichiers joints aux éléments de liste, et non aux éléments de liste réels.
  
Lorsque des personnes téléchargent des fichiers dans une liste ou une bibliothèque activée pour IRM, les fichiers sont chiffrés afin que seules les personnes autorisées peuvent les afficher. Chaque fichier géré par des droits contient également une licence d’émission qui impose des restrictions aux personnes qui visualisent le fichier. Les restrictions classiques incluent la lecture seule d’un fichier, la désactivation de la copie du texte, l’interdiction d’enregistrer une copie locale et l’impression du fichier. Les programmes clients qui peuvent lire les types de fichiers pris en charge par IRM utilisent la licence d’émission dans le fichier géré par des droits pour appliquer ces restrictions. C’est ainsi qu’un fichier géré par des droits conserve sa protection même après son téléchargement à partir du serveur.
  
Les types de restrictions qui sont appliquées à un fichier lorsqu’il est téléchargé à partir d’une liste ou d’une bibliothèque sont basés sur les autorisations de l’utilisateur individuel sur le site qui contient le fichier. Le tableau suivant explique comment les autorisations sur les sites correspondent aux autorisations IRM.
  
|**Autorisations**|**Autorisations IRM**|
|:-----|:-----|
|Gérer les autorisations, Gérer un site Web|**Contrôle total** (tel que défini par le programme client) : cette autorisation permet généralement à un utilisateur de lire, modifier, copier, enregistrer et modifier des autorisations de contenu géré par des droits.|
|Modifier des éléments, gérer des listes, ajouter et personnaliser des pages|**Modifier,** **copier** et enregistrer : un utilisateur ne peut imprimer un fichier que si la case Autoriser les utilisateurs à imprimer des **documents** est cocher sur la page gestion des droits relatifs à l’information Paramètres de la liste ou de la bibliothèque.|
|Afficher les éléments|**Lecture**: un utilisateur peut lire le document, mais ne peut pas copier ou modifier son contenu. Un utilisateur ne peut imprimer que si la case Autoriser les utilisateurs à imprimer des **documents** est sélectionnée sur la page de gestion des droits relatifs à l’information Paramètres de la liste ou de la bibliothèque.|
|Autres|Aucune autre autorisation ne correspond directement aux autorisations IRM.|
   
Lorsque vous activez irm pour une liste ou une bibliothèque dans SharePoint Server 2013, vous ne pouvez protéger que les types de fichiers de cette liste ou bibliothèque pour lesquels un logiciel de protection est installé sur tous les serveurs web frontux. Un logiciel de protection est un programme qui contrôle le chiffrement et le déchiffrement des fichiers gérés par des droits d’un format de fichier spécifique. SharePoint comprend des protecteurs pour les types de fichiers suivants :
  
- Microsoft Office Formulaires InfoPath
    
- Formats de fichier 97-2003 pour les programmes Microsoft Office suivants : Word, Excel et PowerPoint
    
- Les Office formats Open XML pour les programmes Microsoft Office suivants : Word, Excel et PowerPoint
    
- Format XPS (XML Paper Specification)
    
Si votre organisation prévoit d’utiliser irm pour protéger d’autres types de fichiers en plus de ceux répertoriés ci-dessus, votre administrateur de serveur doit installer des logiciels de protection pour ces formats de fichiers supplémentaires.
  

