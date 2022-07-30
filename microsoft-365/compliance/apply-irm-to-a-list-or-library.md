---
title: Appliquer la gestion des droits relatifs à l’information (IRM) à une liste ou une bibliothèque
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 7/2/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.assetid: 3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1
ms.collection:
- M365-security-compliance
- SPO_Content
description: Vous pouvez utiliser la gestion des droits relatifs à l’information (IRM) pour contrôler et protéger les fichiers téléchargés à partir de listes ou de bibliothèques.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 08514bd1637a9619274bc45951af2dc2762881f5
ms.sourcegitcommit: e4882e3c66166ea7b834ad2e8fafeab42293e07d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67099885"
---
# <a name="apply-information-rights-management-irm-to-a-list-or-library"></a>Appliquer la gestion des droits relatifs à l’information (IRM) à une liste ou une bibliothèque

Vous pouvez utiliser la gestion des droits relatifs à l’information (IRM) pour contrôler et protéger les fichiers téléchargés à partir de listes ou de bibliothèques. Cette fonctionnalité est uniquement prise en charge dans le cloud global Microsoft. L’IRM n’est pas prise en charge pour les listes et bibliothèques SharePoint dans les déploiements cloud nationaux.
  
## <a name="administrator-preparations-before-applying-irm"></a>Préparations de l’administrateur avant l’application de la gestion des droits relatifs à l'

- Le service Azure Rights Management (Azure RMS) d’Azure Information Protection et l’équivalent local, Active Directory Rights Management Services (AD RMS), prennent en charge Information Rights Management pour les sites. Aucune installation distincte ou supplémentaire n’est requise.

- Avant d’appliquer irm à une liste ou une bibliothèque, vous devez activer irm pour votre site. Vous aurez besoin d’autorisations d’administrateur pour activer irm.

- Pour appliquer la gestion des droits relatifs à l’information (IRM) à une liste ou à une bibliothèque, vous devez disposer des autorisations d’administrateur pour cette liste ou cette bibliothèque.

- Si vous utilisez SharePoint Online, vos utilisateurs peuvent rencontrer des délais d’expiration lors du téléchargement de fichiers protégés par IRM plus volumineux. Pour éviter les délais d’expiration, utilisez vos programmes Office pour appliquer la protection IRM et stockez des fichiers plus volumineux dans une bibliothèque SharePoint qui n’utilise pas irm.

> [!NOTE]
> Si vous utilisez SharePoint Server 2013, un administrateur de serveur doit installer des logiciels de protection sur tous les serveurs Web frontaux pour chaque type de fichier que les membres de votre organisation souhaitent protéger à l’aide de la gestion des droits relatifs à l’information ( IRM).
  
## <a name="apply-irm-to-a-list-or-library"></a>Appliquer la gestion des droits relatifs à l’information (IRM) à une liste ou une bibliothèque
<a name="__toc256598179"> </a>

![Paramètres de gestion des droits relatifs à l’information.](../media/1b708102-9c90-42b0-b255-ef0e72d0be88.png)
  
1. Accédez à la liste ou à la bibliothèque pour laquelle vous souhaitez configurer irm.

2. Dans le ruban, sélectionnez l’onglet **Bibliothèque** , puis sélectionnez **Paramètres de bibliothèque**. (Si vous travaillez dans une liste, sélectionnez l’onglet **Liste** , puis sélectionnez **Paramètres de liste**).
    
    ![Boutons Paramètres de la bibliothèque SharePoint sur le ruban.](../media/cdf718fa-d792-40fc-8026-00c3b80b9e05.png)
  
3. Sous **Autorisations et Gestion**, sélectionnez **Gestion des droits relatifs à l’information**. Si le lien Gestion des droits relatifs à l’information n’apparaît pas, la gestion des droits relatifs à l’information peut ne pas être activée pour votre site. Contactez votre administrateur de serveur pour voir si vous pouvez activer irm pour votre site. Le lien **Gestion des droits relatifs à l’information** n’apparaît pas pour les bibliothèques d’images.

4. Dans la page **Paramètres de gestion des droits relatifs** à l’information, activez la case à cocher **Restreindre l’autorisation aux documents de cette bibliothèque** pour appliquer une autorisation restreinte aux documents que les utilisateurs téléchargent à partir de cette liste ou bibliothèque.

5. Dans la zone **de titre Créer une stratégie d’autorisation** , entrez un nom descriptif pour la stratégie. Utilisez un nom qui vous permet d’identifier cette stratégie à partir d’autres stratégies. Par exemple, utilisez **Company Confidential** pour appliquer des autorisations restreintes à une liste ou une bibliothèque qui contient des documents d’entreprise confidentiels.

6. Dans la zone **Ajouter une description de stratégie d’autorisation** , tapez une description qui s’affiche aux personnes qui utilisent cette liste ou cette bibliothèque qui explique comment gérer les documents de cette liste ou bibliothèque. Par exemple, vous pouvez taper **Discuss the contents of this document only with other employees** if you want to restrict access to the information in these documents to internal employees. 

7. Pour appliquer des restrictions supplémentaires aux documents de cette liste ou bibliothèque, sélectionnez **Afficher les options** et effectuez l’une des opérations suivantes :

|**Pour cela :**|**Procédez comme suit :**|
|:-----|:-----|
|Autoriser les utilisateurs à imprimer des documents à partir de cette liste ou bibliothèque|Cochez la case **Autoriser les visionneuses à imprimer** .|
|Autoriser les personnes disposant au moins de l’autorisation Afficher les éléments à exécuter du code incorporé ou des macros sur un document.|Activez la case à cocher **Autoriser les visionneuses à exécuter le script et le lecteur d’écran pour qu’ils fonctionnent sur les documents téléchargés** . Si vous sélectionnez cette option, les utilisateurs peuvent exécuter du code pour extraire le contenu d’un document.           |
|Sélectionnez cette option si vous souhaitez restreindre l’accès au contenu à une période spécifiée. Si vous sélectionnez cette option, les licences d’émission des utilisateurs pour accéder au contenu expireront après le nombre de jours spécifié, et les utilisateurs devront revenir sur le serveur pour vérifier leurs informations d’identification et télécharger une nouvelle copie.|Activez la case à cocher **Après le téléchargement, les droits d’accès au document expireront après ces jours (1-365),** puis spécifiez le nombre de jours pendant lesquels vous souhaitez que le document soit visible.|
| Empêchez les personnes de charger des documents qui ne prennent pas en charge la gestion des droits relatifs à la gestion des droits relatifs à l’information dans cette liste ou cette bibliothèque. Si vous sélectionnez cette option, les utilisateurs ne pourront charger aucun des types de fichiers suivants : les types de fichiers qui n’ont pas de logiciels de protection IRM correspondants installés sur tous les serveurs web frontaux. Types de fichiers que SharePoint Server 2010 ne peut pas déchiffrer. Types de fichiers protégés par IRM dans un autre programme.|Activez la case à cocher **Ne pas autoriser les utilisateurs à charger des documents qui ne prennent pas en charge** irm.|
|Supprimez les autorisations restreintes de cette liste ou bibliothèque à une date spécifique.|Activez la case à cocher **Arrêter la restriction d’accès à la bibliothèque** , puis sélectionnez la date souhaitée.|
|Contrôlez l’intervalle pendant lequel les informations d’identification Azure RMS sont mises en cache pour le programme sous licence pour ouvrir le document.|Sélectionnez les **utilisateurs qui doivent vérifier leurs informations d’identification à l’aide de cette case à cocher intervalle (jours),** puis entrez l’intervalle de mise en cache des informations d’identification en nombre de jours.|
|Autorisez la protection de groupe afin que les utilisateurs puissent partager avec les membres du même groupe.|Sélectionnez **Autoriser la protection du groupe**, puis entrez le nom du groupe pour le partage.|

8. Une fois que vous avez terminé de sélectionner les options souhaitées, sélectionnez **OK**.
  
## <a name="what-is-information-rights-management"></a>Qu’est-ce que la gestion des droits relatifs à l’information ?
<a name="__toc256598175"> </a>

La gestion des droits relatifs à l’information (IRM) vous permet de limiter les actions que les utilisateurs peuvent effectuer sur les fichiers qui ont été téléchargés à partir de listes ou de bibliothèques. IRM chiffre les fichiers téléchargés et limite l’ensemble des utilisateurs et des programmes autorisés à déchiffrer ces fichiers. IRM peut également limiter les droits des utilisateurs qui sont autorisés à lire des fichiers, pour leur interdire par exemple d’effectuer des actions telles qu’imprimer des copies des fichiers ou copier du texte de ceux-ci.
  
Vous pouvez utiliser IRM sur des listes ou des bibliothèques pour limiter la diffusion de contenu sensible. Par exemple, si vous créez une bibliothèque de documents pour partager des informations sur les produits à venir avec des représentants marketing sélectionnés, vous pouvez utiliser irm pour empêcher ces personnes de partager ce contenu avec d’autres employés de l’entreprise.
  
Sur un site, vous appliquez irm à une liste ou bibliothèque entière, plutôt qu’à des fichiers individuels. Cela facilite la garantie d’un niveau de protection cohérent pour l’ensemble d’un ensemble de documents ou de fichiers. Irm peut ainsi aider votre organisation à appliquer des stratégies d’entreprise qui régissent l’utilisation et la diffusion d’informations confidentielles ou propriétaires.
  
> [!NOTE]
> Les informations de cette page concernant Information Rights Management remplacent les termes qui référencent « Information Rights Management » dans les contrats de licence Microsoft SharePoint Server 2013 et SharePoint Server 2016. 
  
### <a name="how-irm-can-help-protect-content"></a>Comment la gestion des droits relatifs à l’information (IRM) peut aider à protéger le contenu
<a name="__toc256598176"> </a>

La gestion des droits relatifs à l’information (IRM) permet de protéger le contenu restreint des manières suivantes :
  
- Permet d’empêcher une visionneuse autorisée de copier, modifier, imprimer, faxer ou copier et coller le contenu pour une utilisation non autorisée
    
- Permet d’empêcher une visionneuse autorisée de copier le contenu à l’aide de la fonctionnalité Écran d’impression dans Microsoft Windows
    
- Permet d’empêcher une visionneuse non autorisée d’afficher le contenu s’il est envoyé par e-mail après son téléchargement à partir du serveur
    
- Limite l’accès au contenu à une période spécifiée, après laquelle les utilisateurs doivent confirmer leurs informations d’identification et télécharger à nouveau le contenu
    
- Permet d’appliquer des stratégies d’entreprise qui régissent l’utilisation et la diffusion de contenu au sein de votre organisation
    
### <a name="how-irm-cannot-help-protect-content"></a>Comment irm ne peut pas aider à protéger le contenu
<a name="__toc256598177"> </a>

IRM ne peut pas protéger le contenu restreint des éléments suivants :
  
- Effacement, vol, capture ou transmission par des programmes malveillants tels que des chevaux de Troie, des enregistreurs de frappe et certains types de logiciels espions
    
- Perte ou corruption à cause des actions des virus informatiques
    
- Copie manuelle ou retypage du contenu à partir de l’affichage sur un écran
    
- Photographie numérique ou cinématographique de contenu affiché sur un écran
    
- Copie à l’aide de programmes de capture d’écran tiers
    
- Copie de métadonnées de contenu (valeurs de colonne) à l’aide de programmes de capture d’écran tiers ou d’une action de copie-collage
  
## <a name="how-irm-works-for-lists-and-libraries"></a>Fonctionnement de la gestion des droits relatifs à l’information (IRM) pour les listes et les bibliothèques
<a name="__toc256598178"> </a>

La protection IRM est appliquée aux fichiers au niveau de la liste ou de la bibliothèque. Lorsque irm est activée pour une bibliothèque, la gestion des droits s’applique à tous les fichiers de cette bibliothèque. Lorsque l’IRM est activée pour une liste, la gestion des droits s’applique uniquement aux fichiers attachés aux éléments de liste, et non aux éléments de liste réels.
  
Lorsque des personnes téléchargent des fichiers dans une liste ou une bibliothèque compatible IRM, les fichiers sont chiffrés afin que seules les personnes autorisées puissent les afficher. Chaque fichier géré par des droits contient également une licence d’émission qui impose des restrictions aux personnes qui consultent le fichier. Les restrictions classiques incluent la création d’un fichier en lecture seule, la désactivation de la copie de texte, l’interdiction pour les utilisateurs d’enregistrer une copie locale et l’impression du fichier. Les programmes clients qui peuvent lire les types de fichiers pris en charge par IRM utilisent la licence d’émission dans le fichier géré par des droits pour appliquer ces restrictions. C’est ainsi qu’un fichier géré par des droits conserve sa protection même après son téléchargement à partir du serveur.
  
Les types de restrictions appliqués à un fichier lorsqu’il est téléchargé à partir d’une liste ou d’une bibliothèque sont basés sur les autorisations de chaque utilisateur sur le site qui contient le fichier. Le tableau suivant explique comment les autorisations sur les sites correspondent aux autorisations IRM.
  
|**Autorisations**|**Autorisations IRM**|
|:-----|:-----|
|Gérer les autorisations, gérer le site web|**Contrôle total** (tel que défini par le programme client) : cette autorisation permet généralement à un utilisateur de lire, modifier, copier, enregistrer et modifier des autorisations de contenu géré par des droits.|
|Modifier des éléments, gérer des listes, ajouter et personnaliser des pages|**Modifier**, **copier** et **enregistrer** : un utilisateur ne peut imprimer un fichier que si la case **Autoriser les utilisateurs à imprimer des documents** est cochée dans la page Paramètres de gestion des droits relatifs à l’information pour la liste ou la bibliothèque.|
|Afficher les éléments|**Lecture** : un utilisateur peut lire le document, mais ne peut pas copier ou modifier son contenu. Un utilisateur ne peut imprimer que si la case **Autoriser les utilisateurs à imprimer des documents** est cochée dans la page Paramètres de gestion des droits relatifs à l’information pour la liste ou la bibliothèque.|
|Autre|Aucune autre autorisation ne correspond directement aux autorisations IRM.|
   
Lorsque vous activez irm pour une liste ou une bibliothèque dans SharePoint Server 2013, vous pouvez uniquement protéger les types de fichiers dans cette liste ou bibliothèque pour laquelle un logiciel de protection est installé sur tous les serveurs web frontaux. Un logiciel de protection est un programme qui contrôle le chiffrement et le déchiffrement des fichiers gérés par des droits d’un format de fichier spécifique. SharePoint inclut des protecteurs pour les types de fichiers suivants :
  
- Formulaires Microsoft Office InfoPath
    
- Formats de fichier 97-2003 pour les programmes Microsoft Office suivants : Word, Excel et PowerPoint
    
- Formats Office Open XML pour les programmes Microsoft Office suivants : Word, Excel et PowerPoint
    
- Format XPS (XML Paper Specification)
    
Si votre organisation envisage d’utiliser irm pour protéger d’autres types de fichiers en plus de ceux répertoriés ci-dessus, votre administrateur de serveur doit installer des logiciels de protection pour ces formats de fichiers supplémentaires.
  

