---
title: Déterminer si le déploiement centralisé des compléments fonctionne pour votre organisation
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b4527d49-4073-4b43-8274-31b7a3166f92
description: Déterminez si votre client et vos utilisateurs satisfont à la configuration requise, afin que vous puissiez utiliser un déploiement centralisé pour déployer des compléments Office.
ms.openlocfilehash: 4b9ca7213f36440114d39ef491fe934f13ca96ea
ms.sourcegitcommit: f80c6c52e5b08290f74baec1d64c4070046c32e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44717272"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>Déterminer si le déploiement centralisé des compléments fonctionne pour votre organisation

Le déploiement centralisé est la méthode recommandée et la plus riche en fonctionnalités pour la plupart des clients qui déploient des compléments Office pour les utilisateurs et les groupes au sein de votre organisation. Si vous êtes administrateur, utilisez ce guide pour déterminer si votre client et vos utilisateurs satisfont à la configuration requise afin que vous puissiez utiliser un déploiement centralisé.
Le déploiement centralisé prend en charge trois plateformes de bureau Windows, Mac et les applications Office en ligne. Le déploiement centralisé prend également en charge iOS et Android (compléments Outlook Mobile uniquement).
Un complément peut prendre jusqu’à 24 heures pour s’afficher pour le client pour tous les utilisateurs.
  
## <a name="requirements"></a>Configuration requise

Le déploiement centralisé des compléments nécessite que les utilisateurs utilisent les applications Microsoft 365 pour Enterprise (et sont connectés à Office à l’aide de leur ID d’organisation) et disposent de boîtes aux lettres Exchange Online et Exchange Online actives. Le répertoire de votre abonnement doit être dans ou fédéré à Azure Active Directory.
Vous pouvez afficher les conditions requises spécifiques pour Office et Exchange ci-dessous, ou utiliser le [Vérificateur de compatibilité de déploiement centralisé](https://docs.microsoft.com/office365/admin/manage/centralized-deployment-of-add-ins?view=o365-worldwide#office-365-centralized-deployment-compatibility-checker).

La fonctionnalité Déploiement centralisé ne prend pas en charge ce qui suit :
  
- des compléments ciblant Word, Excel ou PowerPoint dans Office 2013 ;
    
- un service d'annuaire local ;
    
- le déploiement de compléments vers SharePoint ;  

- Applications teams
   
- le déploiement de compléments COM (Component Object Model) ou Visual Studio Tools pour Office (VSTO).
    
- Déploiements de Microsoft 365 qui n’incluent pas Exchange, comme Microsoft 365 apps pour les entreprises

### <a name="office-requirements"></a>Configuration requise pour Office

- Pour les compléments Word, Excel et PowerPoint, vos utilisateurs doivent utiliser l’un des éléments suivants :
  - Sur un appareil Windows, version 1704 ou ultérieure de Microsoft 365 apps pour entreprises.
  - Sur un Mac, version 15,34 ou ultérieure.

- Pour Outlook, vos utilisateurs doivent utiliser l’un des éléments suivants : 
  - Version 1701 ou ultérieure des applications Microsoft 365 pour entreprises.
  - Version 1808 ou ultérieure d’Office professionnel plus 2019 ou Office standard 2019.
  - Version 16.0.4494.1000 ou ultérieure d’Office professionnel plus 2016 (MSI) ou Office standard 2016 (MSI)\*
  - Version 15.0.4937.1000 ou ultérieure d’Office professionnel plus 2013 (MSI) ou Office standard 2013 (MSI)\*
  - Version 16.0.9318.1000 ou ultérieure d’Office 2016 pour Mac 
- Version 2.75.0 ou ultérieure d’Outlook Mobile pour iOS 
- Version 2.2.145 ou ultérieure d’Outlook Mobile pour Android 
    
    * Les versions MSI d’Outlook affichent les compléments installés par l’administrateur dans le ruban Outlook approprié, et non dans la section « mes compléments ».
    

#### <a name="find-out-if-microsoft-365-apps-for-enterprise-is-installed"></a>Déterminer si les applications Microsoft 365 pour les entreprises sont installées

Pour utiliser les applications Microsoft 365 pour Enterprise, un utilisateur doit disposer d’un compte Microsoft 365 et avoir reçu une licence. Pour plus d’informations, reportez-vous à la rubrique [Overview of Microsoft 365 Apps for Enterprise](https://go.microsoft.com/fwlink/p/?linkid=846328).

Le moyen le plus simple de détecter si les applications Microsoft 365 pour Enterprise sont installées sur un utilisateur et de l’utiliser récemment est d’utiliser le rapport des activations de Microsoft Office, qui est disponible dans le centre d’administration Microsoft 365. Le rapport fournit la liste de tous les utilisateurs qui ont activé les applications Microsoft 365 pour les entreprises au cours des 7, 30, 90 ou 180 derniers jours. À des fins de déploiement centralisé, les activations de bureau pour Windows ou Mac sont les colonnes importantes dans le rapport. Vous pouvez exporter le rapport vers Excel. Pour plus d’informations sur le rapport, reportez-vous à [la rubrique rapports microsoft 365 dans le centre d’administration-activations de Microsoft Office](../activity-reports/microsoft-office-activations.md).
  
Si vous ne souhaitez pas utiliser le rapport d’activation, vous pouvez demander à un utilisateur d’ouvrir une application Office telle que Word sur son ordinateur, puis choisir le compte de **fichier** \> **Account**. Sous **informations sur le produit**, vous devez voir le **produit abonnement** et **Microsoft 365 pour entreprise**, comme illustré dans l’image suivante.

![Informations sur le produit dans une application Office](../../media/product-information-microsoft-365-enterprise.png)
  
Pour obtenir de l’aide concernant les applications Microsoft 365 pour les entreprises, consultez la rubrique [Troubleshooting Tips for microsoft 365 Apps for Enterprise](https://go.microsoft.com/fwlink/p/?linkid=846339).


### <a name="exchange-online-requirements"></a>Configuration requise pour Exchange Online

Microsoft Exchange stocke les manifestes des compléments au sein du client de votre organisation. L’administrateur déployant des compléments et les utilisateurs qui les reçoivent doivent se trouver sur une version d’Exchange Online qui prend en charge l’authentification OAuth.
  
Check with your organization's Exchange admin to find out which configuration is in use. OAuth connectivity per user can be verified by using the [Test-OAuthConnectivity](https://go.microsoft.com/fwlink/p/?linkid=846351) PowerShell cmdlet. 


### <a name="centralized-deployment-compatibility-checker"></a>Vérificateur de compatibilité de déploiement centralisé

À l’aide du vérificateur de compatibilité du déploiement centralisé, vous pouvez vérifier si les utilisateurs de votre client sont configurés pour utiliser un déploiement centralisé pour Word, Excel et PowerPoint. Le vérificateur de compatibilité n'est pas requis pour la prise en charge d'Outlook. Téléchargez le vérificateur de compatibilité [ici](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).
  
#### <a name="run-the-compatibility-checker"></a>Exécuter le vérificateur de compatibilité
  
1. Démarrez une fenêtre PowerShell.exe élevée.
    
2. Exécutez la commande suivante :

```powershell
Import-Module O365CompatibilityChecker
```
    
3. Exécutez la commande **Invoke-CompatabilityCheck** :

```powershell
Invoke-CompatibilityCheck
```
   qui vous demande *_TenantDomain_* (par exemple, *TailspinToysIncorporated. onmicrosoft. </span> com*) et *_TENANTADMIN_* (utilisez vos informations d’identification d’administrateur général), puis demande le consentement.
    
> [!NOTE]
> Selon le nombre d'utilisateurs dans votre client, l'exécution du vérificateur peut prendre quelques minutes ou plusieurs heures. 
  
Une fois l'exécution de l'outil terminée, celui-ci génère un fichier de sortie dans un format séparé par des virgules (.csv). Par défaut, le fichier est enregistré dans **C:\Windows\System32** . Le fichier de sortie contient les informations suivantes :
  
- Nom d'utilisateur
    
- ID d'utilisateur (adresse de courrier de l'utilisateur)
    
- Déploiement centralisé prêt - Si les autres éléments sont vérifiés
    
- Plan Office : le plan d’Office pour lequel il existe une licence pour
    
- Activation d'Office - Si l'utilisateur a activé Office
    
- Boîte aux lettres prise en charge - Si l'utilisateur a une boîte aux lettres OAuth


  
## <a name="user-and-group-assignments"></a>Affectations à des utilisateurs et groupes

La fonctionnalité de déploiement centralisé prend actuellement en charge la majorité des groupes pris en charge par Azure Active Directory, y compris les groupes Microsoft 365, les listes de distribution et les groupes de sécurité.
  
> [!NOTE]
> Les groupes de sécurité sans extension messagerie ne sont pas actuellement pas pris en charge. 
  
Le déploiement centralisé prend en charge les affectations à des utilisateurs individuels, des groupes et tout le monde dans le client. La fonctionnalité Déploiement centralisé prend en charge les utilisateurs au sein de groupes de niveau supérieur ou de groupes sans groupes parents, mais pas les utilisateurs au sein de groupes imbriqués ou qui ont des groupes parents.
   
Take a look at the following example where Sandra, Sheila, and the Sales Department group are assigned to an add-in. Because the West Coast Sales Department is a nested group, Bert and Fred aren't assigned to an add-in.
  
![Diagramme du service des ventes](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

   
### <a name="find-out-if-a-group-contains-nested-groups"></a>Déterminer si un groupe contient des groupes imbriqués

La manière la plus simple de détecter si un groupe contient des groupes imbriqués consiste à afficher la carte de visite du groupe dans Outlook. Si vous entrez le nom du groupe dans le champ **à** d’un e-mail, puis que vous sélectionnez le nom du groupe lorsqu’il est résolu, il vous indique s’il contient des utilisateurs ou des groupes imbriqués. Dans l'exemple ci-dessous, l'onglet **Membres** de la carte de visite Outlook du groupe Test n'affiche aucun utilisateur et seulement deux sous-groupes. 
  
![Onglet membres de la carte de visite Outlook](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)
  
You can do the opposite query by resolving the group to see if it's a member of any group. In the example below, you can see under the **Membership** tab of the Outlook contact card that Sub Group 1 is a member of the Test Group. 
  
![Onglet appartenance de la carte de visite Outlook](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)
  
Alternately, you can use the Azure Active Directory Graph API to run queries to find the list of groups within a group. For more information, see [Operations on groups | Graph API reference](https://go.microsoft.com/fwlink/p/?linkid=846342).
  
### <a name="contacting-microsoft-for-support"></a>Contacter Microsoft pour obtenir une assistance

Si vous ou vos utilisateurs rencontrez des problèmes lors du chargement du complément lors de l’utilisation d’applications Office pour le Web (Word, Excel, etc.), qui ont été déployées de manière centralisée, vous devrez peut-être contacter le support technique Microsoft ([Découvrez comment](../contact-support-for-business-products.md)). Fournissez les informations suivantes sur votre environnement Microsoft 365 dans le ticket de support.
  
|**Plateforme**|**Informations de débogage**|
|:-----|:-----|
|Office  <br/> | Journaux Charles/Fiddler  <br/>  ID de client ( [Découvrez comment](https://docs.microsoft.com/onedrive/find-your-office-365-tenant-id.aspx))  <br/>  Corrélation. Affichez la source d’une des pages Office et recherchez la valeur de l’ID de corrélation et envoyez-la au support technique :  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">`  <br/>  `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`  <br/> |
|Clients riches (Windows, Mac)  <br/> | Journaux Charles/Fiddler  <br/>  Numéros de build de l’application cliente (de préférence sous la forme d’une capture d’écran du **fichier/compte**)  <br/> |
   

