---
title: Gérer le déploiement des compléments Office 365 dans le centre d’administration
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Découvrez comment déployer des compléments pour les utilisateurs et les groupes de votre organisation à l’aide du déploiement centralisé dans le centre d’administration.
ms.openlocfilehash: b2fe57bd2b3b51ac5097723613c608580da06bea
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42361949"
---
# <a name="manage-deployment-of-office-365-add-ins-in-the-microsoft-365-admin-center"></a>Gérer le déploiement de compléments Office 365 dans le Centre d’administration Microsoft 365

[] Les compléments Office vous aident à personnaliser vos documents et à accéder plus simplement aux informations sur le web (voir [Commencer à utiliser votre complément Office](https://support.office.com/article/82e665c4-6700-4b56-a3f3-ef5441996862.aspx)). En tant qu’administrateur, vous pouvez déployer des compléments Office pour les utilisateurs de votre organisation. Vous pouvez effectuer cette opération à l’aide de la fonctionnalité déploiement centralisé dans le centre d’administration 365 de Microsoft.
  
Le déploiement centralisé est la méthode recommandée et la plus riche en fonctionnalités permettant à la plupart des administrateurs de déployer des compléments pour les utilisateurs et les groupes au sein d’une organisation. Pour plus d'informations sur la manière de déterminer si votre organisation peut prendre en charge un déploiement centralisé, voir [Déterminer si un déploiement centralisé de compléments est approprié pour votre organisation Office 365](centralized-deployment-of-add-ins.md).
  
Une déploiement centralisé offre les avantages suivants :
  
- Un administrateur général peut attribuer un complément directement à un utilisateur, à plusieurs utilisateurs via un groupe ou à tout le monde dans le client.
    
- Lorsque l'application Office pertinente démarre, le complément est automatiquement téléchargé pour l'utilisateur. Si le complément prend en charge les commandes de complément, il apparaît automatiquement sur le ruban dans l'application Office.
    
- Les compléments ne s’affichent plus pour les utilisateurs si l’administrateur désactive ou supprime le complément, ou si l’utilisateur est supprimé d’Azure Active Directory ou d’un groupe auquel le complément est affecté.
    
> [!NOTE]
>  Pour Word, Excel et PowerPoint utilisent un [catalogue d’applications SharePoint](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) pour déployer des compléments pour les utilisateurs dans un environnement local sans connexion à Office 365 et/ou prise en charge des compléments SharePoint requis. >  Pour Outlook, utilisez le panneau de configuration Exchange pour déployer les compléments dans un environnement local sans connexion Office 365. > 
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Approche recommandée pour le déploiement des compléments Office

Vous pouvez déployer des compléments de façon progressive pour vous assurer que le déploiement se déroule sans problème. Nous vous recommandons de planifier le déploiement comme suit :
  
1. Déployez le complément vers un petit groupe de parties intéressées et de membres du service informatique. Évaluez si le déploiement a réussi et, si c'est le cas, passez à l'étape 2.
    
2. Déployez le complément vers un groupe plus important de membres de l'organisation appelés à l'utiliser. Une fois encore, évaluez les résultats et, si l'opération s'est bien déroulée, accédez à l'étape suivante de déploiement complet.
    
3. Effectuez un déploiement complet vers un groupe cible d'utilisateurs.
    
Selon la taille du groupe cible, vous pouvez ajouter ou supprimer des étapes de déploiement.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Déployer un complément Office à l’aide du centre d’administration

Avant de commencer, reportez-vous à la rubrique [Déterminer si un déploiement centralisé de compléments est approprié pour votre organisation Office 365](centralized-deployment-of-add-ins.md).

  
1. Dans le centre d’administration, accédez à la page **compléments** de **paramètres** \> .
    
2. Sélectionnez **déployer un complément** en haut de la page. Sur la page vue d’ensemble, sélectionnez **suivant**.
    
3. Sélectionnez une option et suivez les instructions.
  
4. Si vous avez sélectionné l’option d’ajout d’un complément à partir de l’Office Store, vous pouvez maintenant effectuer votre sélection de complément. Notez que vous pouvez afficher les compléments disponibles via l'une des catégories **Suggestions**, **Évaluation** ou **Nom**. Seuls les compléments gratuits peuvent être ajoutés à partir de l'Office Store. Les compléments payants ne sont pas pris en charge pour le moment. Une fois que vous avez sélectionné votre complément, vous devez accepter les termes et conditions supplémentaires pour pouvoir continuer. <br/><br/> Remarque : avec l’option Office Store, les mises à jour et les améliorations apportées au complément seront automatiquement mises à la disposition des utilisateurs sans votre intervention.

5. Sur la page suivante, sélectionnez **tout le monde**, **utilisateurs/groupes spécifiques** ou **seulement moi** pour spécifier les personnes vers lesquelles le complément est déployé. Utilisez la zone de recherche pour trouver les utilisateurs ou groupes vers lesquels vous voulez déployer le complément. <br/>Remarque : Découvrez les autres États qui s’appliquent à un complément. Consultez la section [États des compléments](#add-in-states) plus loin dans cette rubrique.
  
6. Sélectionnez **Déployer**.
  
7. Une coche verte apparaît lorsque le complément a été déployé. Vous pouvez suivre les instructions sur la page pour vérifier que le complément a été déployé avec succès.

> [!NOTE]
> Les utilisateurs devront peut-être relancer Office pour voir l’icône de complément apparaissent sur le ruban de l’application. Les compléments Outlook peuvent prendre jusqu’à 12 heures pour apparaître sur les rubans des utilisateurs.
    
8. Lorsque vous avez terminé, sélectionnez **suivant**. Si vous avez déjà déployé, vous pouvez sélectionner Modifier les utilisateurs **qui ont accès au complément** afin de le déployer sur un plus grand nombre d’utilisateurs.



Si vous avez déployé le complément vers des membres de votre organisation autre que vous-même, suivez les instructions affichées afin d’annoncer efficacement le déploiement du complément. <br/>Votre complément apparaît à présent avec d’autres applications dans Office 365.
  
Il est recommandé d'informer les utilisateurs et les groupes vers lesquels vous déployez le complément afin qu'ils sachent que celui-ci est disponible. Songez à leur envoyer un courrier décrivant quand et comment utiliser le complément, et expliquant comment celui-ci peut les aider à mieux accomplir leur travail. Inclure ou créer un lien vers du contenu d’aide pertinent ou des questions fréquentes susceptibles d’aider les utilisateurs à rencontrer des problèmes avec le complément.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Points à considérer lors de l'affectation d'un complément à des utilisateurs et groupes

Les administrateurs peuvent affecter un complément à tout le monde ou à des utilisateurs et groupes spécifiques. Chaque option a des conséquences spécifiques :
  
- **Tout le monde** : comme son nom l’indique, cette option affecte le complément à tous les utilisateurs du client. Utilisez-la avec parcimonie et uniquement pour les compléments qui sont réellement universels pour l’ensemble de votre organisation. 
    
- **Utilisateurs**: si vous affectez un complément à un utilisateur particulier, pour le déployer ensuite vers un nouvel utilisateur, vous devez commencer par ajouter ce dernier. Il en va de même pour la suppression d'utilisateurs. 
    
- **Groupes**: si vous affectez un complément à un groupe, le complément est automatiquement affecté aux utilisateurs ajoutés au groupe. Par ailleurs, quand un utilisateur est supprimé d'un groupe, il perd l'accès au complément. Dans les deux cas, aucune action supplémentaire n'est requise de votre part en tant qu'administrateur. 

- **Je me contente**: Si vous affectez un complément à vous-même, le complément est affecté uniquement à votre compte. Cette solution est idéale si vous souhaitez tester le complément en premier.
    
L’option la plus adaptée à votre organisation dépend de votre configuration. Toutefois, nous vous recommandons d'effectuer les affectations via des groupes. En tant qu'administrateur, vous trouverez probablement plus facile de gérer les compléments à l'aide de groupes, et de contrôler l'appartenance aux groupes au lieu de devoir modifier à chaque fois les utilisateurs auxquels le complément est affecté. En revanche, dans certains cas, il peut être préférable de restreindre l'accès à un très petit groupe d'utilisateurs et donc d'affecter le complément à des utilisateurs spécifiques. Par conséquent, vous devez alors gérer manuellement les utilisateurs auxquels le complément est affecté.
  
### <a name="add-in-states"></a>États de complément

Un complément peut avoir l’état **activé** ou **désactivé** .
  
|**État**|**Comment l'état se produit**|**Impact**|
|:-----|:-----|:-----|
|**Active**  <br/> |Un administrateur a chargé le complément et l’a affecté à des utilisateurs ou à des groupes.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté voient celui-ci dans les clients concernés.  <br/> |
|**Désactivé**  <br/> |Un administrateur a désactivé le complément.  <br/> |Les utilisateurs et les groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> Si l'état du complément est modifié en Actif, les utilisateurs et groupes ont de nouveau accès à celui-ci.  <br/> |
|**Deleted**  <br/> |Un administrateur a supprimé le complément.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> |
   
Envisagez de supprimer un complément s’il n’est plus utilisé. Désactiver un complément peut être judicieux si celui-ci est utilisé uniquement à des moments spécifiques au cours d'une année.
  
### <a name="security-of-office-add-ins"></a>Sécurité des compléments Office

Les compléments Office combinent un fichier manifeste XML qui inclut certaines métadonnées sur le complément, mais surtout qui pointe vers une application web contenant tout le code et la logique. Les fonctionnalités des compléments peuvent varier. Par exemple, les compléments peuvent :
  
- afficher des données.
    
- lire le document d'un utilisateur pour fournir des services contextuels.
    
- lire et écrire des données vers le document d'un utilisateur et à partir de celui-ci pour fournir une valeur à cet utilisateur.
    
Pour plus d'informations sur les types et fonctionnalités des compléments Office, voir [Vue d'ensemble de la plateforme des compléments Office](https://go.microsoft.com/fwlink/p/?linkid=846362), notamment la section « Anatomie d'un complément Office ».
  
Pour interagir avec le document de l'utilisateur, le complément doit déclarer les autorisations dont il a besoin dans le fichier manifeste. Un modèle d'autorisations d'accès d'une API JavaScript à cinq niveaux fournit la base de la confidentialité et de la sécurité pour les utilisateurs des compléments du volet Office. La plupart des compléments de l'Office Store sont au niveau ReadWriteDocument. Presque tous les compléments prennent en charge le niveau ReadDocument au minimum. Pour plus d'informations sur les niveaux d'autorisation, voir [Demande d'autorisations pour l'utilisation d'API dans les compléments de contenu et du volet Office](https://go.microsoft.com/fwlink/p/?linkid=848863).
  
Lors de la mise à jour d'un manifeste, les modifications standard sont apportées à l'icône et au texte d'un complément. Les commandes de complément changent parfois, contrairement aux autorisations du complément. L'application web dans laquelle le code et la logique du complément sont exécutés peut changer à tout moment, ce qui est la nature même des applications web.
  
Les mises à jour des compléments se produisent comme suit :
  
- **Complément métier :** dans ce cas, lorsqu'un administrateur a chargé explicitement un manifeste, le complément nécessite que l'administrateur charge un nouveau fichier manifeste pour prendre en charge la modification des métadonnées. Le complément est mis à jour au démarrage suivant des applications Office concernées. L'application web peut changer à tout moment. 

    > [!NOTE]
    > L’administrateur n’a pas besoin de supprimer un complément LOB pour effectuer une mise à jour.   Dans la section compléments, l’administrateur peut simplement cliquer sur le complément LOB et cliquer sur le **bouton mettre à jour** dans le coin inférieur droit. La mise à jour ne fonctionnera que si la version du nouveau complément est supérieure à celle du complément existant.   
    
- **Complément de l'Office Store :** lorsqu'un administrateur a sélectionné un complément à partir de l'Office Store, si un complément est mis à jour dans l'Office Store, le complément sera mis à jour plus tard dans le déploiement centralisé. Le complément est mis à jour au démarrage suivant des applications Office concernées. L'application web peut changer à tout moment. 

### <a name="edit-add-in-access"></a>Modifier l’accès au complément

Post-déploiement, les administrateurs peuvent également modifier l’accès des utilisateurs aux compléments.

1. Dans le centre d’administration, accédez à la page **paramètres** > de **& des compléments** .

2. Sélectionnez le complément déployé.

3. Cliquez sur **modifier** sous la rubrique **qui a accès**.
4. Enregistrez les modifications.
    
### <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Empêcher les téléchargements de compléments en désactivant l’Office Store sur tous les clients (sauf Outlook)

> [!NOTE]
> L’installation d’un complément Outlook est gérée par un [autre processus](https://technet.microsoft.com/library/jj943754%28v=exchg.150%29.aspx).

En tant qu’organisation, vous souhaiterez peut-être empêcher le téléchargement de nouveaux compléments Office à partir de l’Office Store. Il peut être utilisé conjointement avec un déploiement centralisé afin de s’assurer que seuls les compléments approuvés par l’organisation sont déployés pour les utilisateurs au sein de votre organisation.
  
Pour désactiver l’acquisition du complément :
  
1. Dans le centre d’administration, cliquez sur la page **Paramètres** \> [Services &amp; Compléments](https://go.microsoft.com/fwlink/p/?linkid=2053743).
    
3. Sélectionnez **applications et services appartenant**à l’utilisateur.
    
4. Désactivez l’option pour permettre aux utilisateurs d’accéder à l’Office Store.

Cela empêchera tous les utilisateurs d’acquérir les compléments suivants à partir de la Banque.
  
- Compléments pour Word, Excel et PowerPoint 2016 à partir de :
    
  - Windows
    
  - Mac
    
  - Office
    
  - iOS (iPad uniquement)
    
- Acquisitions à partir de **AppSource**
    
- Compléments dans Office 365
    
Un utilisateur qui tente d’accéder au magasin verra apparaître le message suivant : **Désolé, Office 365 a été configuré pour empêcher l’acquisition individuelle des compléments de l’Office Store.**
  
La prise en charge de la désactivation de l’Office Store est disponible dans les versions suivantes :
  
- Windows : 16.0.9001 actuellement disponible.
    
- Mac : 16.10.18011401-actuellement disponible.
    
- iOS : 2.9.18010804-actuellement disponible.
    
- Le Web est actuellement disponible.
    
Cela n’empêche pas un administrateur d’utiliser un déploiement centralisé pour affecter un complément à partir de l’Office Store.
  
Pour empêcher un utilisateur de se connecter à l’aide d’un compte Microsoft, vous pouvez limiter l’ouverture de session pour utiliser uniquement le compte d’organisation. Pour plus d’informations, consultez la [rubrique](https://technet.microsoft.com/library/jj683102%28v=office.16%29.aspx).
 
  
## <a name="minors-and-acquiring-add-ins-from-the-store"></a>Mineurs et acquisition de compléments à partir du magasin

Le règlement général sur la protection des données (RGPD) est un règlement de l’Union européenne qui devient effectif le 25 mai 2018. Il donne aux utilisateurs des droits et la protection de leurs données. L’un des aspects du RGPD est que les mineurs ne peuvent pas avoir leurs données personnelles envoyées aux parties que leur parent ou tuteur n’a pas approuvées. L’âge spécifique défini comme un mineur dépend de la région où se trouve la personne.
  
Les régions dont la réglementation statutaire est relative au consentement parental incluent les États-Unis, la Corée du Sud, le Royaume-Uni et l’Union européenne. Pour ces régions, un mineur est bloqué (via Azure Active Directory) pour obtenir les nouveaux compléments Office à partir du Store et exécuter des compléments qui ont été précédemment acquis. Pour les pays sans réglementation réglementaire, il n’y aura pas de restrictions de téléchargement.
  
Un utilisateur est considéré comme mineur en fonction des données spécifiées dans Azure Active Directory. L’administrateur client est responsable de la déclaration du groupe d’âge légal et de l’autorisation parentale pour cet utilisateur.
  
Si le parent/tuteur est accepté par un utilisateur secondaire à l’aide d’un complément spécifique, l’administrateur client peut utiliser un déploiement centralisé pour déployer ce complément sur tous les mineurs qui ont le consentement.
  
Pour être conforme à RGPD pour les mineurs, vous devez vous assurer que l’une des versions suivantes d’Office est déployée dans votre établissement scolaire ou votre organisation.
  
 **Pour Word, Excel, PowerPoint et Project**: 
  
|||
|:-----|:-----|
|**Plateforme** <br/> |**Numéro de build** <br/> |
|Office 2016 ProPlus mensuel pour Windows  <br/> |9001,2138   <br/> |
|Office 2016 ProPlus semi-annuel  <br/> |8431,2159  <br/> |
|Office 2016 pour Windows  <br/> |16.0.4672.1000  <br/> |
|Office 2013 pour Windows  <br/> |15.0.5023.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.11.18020200  <br/> |
|Office 2016 pour iOS (iPad uniquement)  <br/> |2.12.18032600  <br/> |
|Office pour le web  <br/> |S/O  <br/> |
   
 **Pour Outlook**: 
  
|||
|:-----|:-----|
|**Plateforme** <br/> |**Numéro de build** <br/> |
|Outlook 2016 pour Windows (MSI)  <br/> |Générer non TBD  <br/> |
|Outlook 2016 pour Windows (C2R)  <br/> |16.0.9323.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.0.9318.1000  <br/> |
|Outlook Mobile pour iOS  <br/> |2.75.0  <br/> |
|Outlook Mobile pour Android  <br/> |2.2.145  <br/> |
|Outlook.com  <br/> |S/O  <br/> |
   
 **Configuration requise pour Office 2013**
  
Word, Excel et PowerPoint 2013 pour Windows prend en charge les mêmes vérifications mineures si la bibliothèque d’authentification Active Directory (ADAL) est activée. Il existe deux options pour la conformité, comme expliqué ci-dessous.
  
- **Activez Adal**. Cet article explique comment activer ADAL pour Office 2013 : [using office 365 moderne Authentication with Office clients](https://support.office.com/article/776c0036-66fd-41cb-8928-5495c0f9168a).<br/>Vous devez également définir les clés de Registre pour activer ADAL, comme expliqué dans la rubrique [activation de l’authentification moderne pour Office 2013 sur les appareils Windows](../security-and-compliance/enable-modern-authentication.md).<br/>En outre, vous devez installer les mises à jour d’avril suivantes pour Office 2013 :
    
  - [Description de la mise à jour de sécurité pour Office 2013:10 avril 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [2018 avril, mise à jour pour Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- **N’activez pas Adal**. Si vous ne parvenez pas à activer ADAL dans Office 2013, nous vous recommandons d’utiliser la stratégie de groupe pour désactiver le magasin pour les clients Office. Vous trouverez [ici](https://technet.microsoft.com/library/cc178992.aspx)des informations sur la façon de désactiver les paramètres de l’application pour Office.
    
## <a name="end-user-experience-with-add-ins"></a>Expérience des utilisateurs finaux avec les compléments

À présent que vous avez déployé le complément, vos utilisateurs peuvent commencer à l'utiliser dans leurs applications Office (voir [Commencer à utiliser votre complément Office](https://support.office.com/article/82e665c4-6700-4b56-a3f3-ef5441996862.aspx)). Le complément apparaît sur toutes les plateformes qui le prennent en charge.
  
Si le complément prend en charge les commandes de complément, celles-ci apparaissent sur le ruban Office. Dans l'exemple suivant, la commande **Search Citation** (Rechercher une citation) apparaît pour le complément **Citations**. 

![Ruban Office avec des citations de recherche](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Si le complément déployé ne prend pas en charge les commandes de complément ou si vous souhaitez afficher tous les compléments déployés, vous pouvez les consulter via **mes compléments**. 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>Dans Word 2016, Excel 2016 ou PowerPoint 2016

1. Sélectionnez **insérer \> mes compléments**. 
    
2. Sélectionnez l'onglet **Géré par l'administrateur** dans la fenêtre Compléments Office. 
    
3. Double-cliquez sur le complément que vous avez déployé précédemment (dans cet exemple, **Citations** ). <br/>![Onglet géré par l’administrateur de la page compléments Office](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>Dans Outlook

1. Sur le ruban **Accueil** , sélectionnez **obtenir des compléments**.<br/>![Bouton Store dans Outlook](../../media/getaddinsicon.png)
  
2. Sélectionnez **géré** par l’administrateur dans le volet de navigation de gauche.

## <a name="delete-the-add-in"></a>Supprimer le complément

Vous pouvez également supprimer un complément qui a été déployé.

1. Dans le centre d’administration, accédez à la page **paramètres** > de **& des compléments** .

2. Sélectionnez le complément déployé.

3. Cliquez sur **supprimer le complément**. Supprimez le bouton de complément dans le coin inférieur droit.
4. Validez vos sélections, puis choisissez **supprimer le complément**.
  
## <a name="learn-more"></a>En savoir plus

Pour en savoir plus sur la création et la génération de compléments, voir [Compléments Office](https://go.microsoft.com/fwlink/p/?linkid=846362).
  
[Utilisez les cmdlets PowerShell de déploiement centralisé pour gérer les compléments](https://support.office.com/article/94f4e86d-b8e5-42dd-b558-e6092f830ec9).
  
[Résolution des problèmes : l’utilisateur ne voit pas les compléments](https://docs.microsoft.com/office365/troubleshoot/access-management/user-not-seeing-add-ins)
