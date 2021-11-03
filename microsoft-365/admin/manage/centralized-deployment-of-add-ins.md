---
title: Déterminer si le déploiement centralisé des add-ins fonctionne pour votre organisation
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b4527d49-4073-4b43-8274-31b7a3166f92
description: Déterminez si votre client et vos utilisateurs répondent aux exigences, afin que vous pouvez utiliser le déploiement centralisé pour déployer Office des modules.
ms.openlocfilehash: 332a2b14bb74363091df8fc18423c347d1d8c6fb
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60663027"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>Déterminer si le déploiement centralisé des add-ins fonctionne pour votre organisation

Le déploiement centralisé est le moyen recommandé et le plus riche en fonctionnalités pour la plupart des clients de déployer des Office pour des utilisateurs et des groupes au sein de votre organisation. Si vous êtes un administrateur, utilisez ces conseils pour déterminer si votre organisation et les utilisateurs répondent aux exigences afin de pouvoir utiliser le déploiement centralisé.

Une déploiement centralisé offre les avantages suivants :

- Un administrateur général peut affecter un add-in directement à un utilisateur, à plusieurs utilisateurs via un groupe ou à tous les membres de l’organisation.

- Lorsque l’application Office pertinente démarre, le add-in se télécharge automatiquement. Si le add-in prend en charge les commandes de Office, il apparaît automatiquement dans le ruban.

- Les add-ins n’apparaissent plus pour les utilisateurs si l’administrateur le éteint ou le supprime, ou si l’utilisateur est supprimé de Azure Active Directory ou d’un groupe à qui le module est affecté.

Le déploiement centralisé prend en charge trois plateformes de bureau Windows, Mac et Online Office applications. Le déploiement centralisé prend également en charge iOS et Android (Outlook uniquement les applications mobiles).

L’ouverture d’un client pour tous les utilisateurs peut prendre jusqu’à 24 heures.

## <a name="before-you-begin"></a>Avant de commencer

Le déploiement centralisé des add-ins nécessite que les utilisateurs utilisent des licences Microsoft 365 Business (Business Basic, Business Standard, Business Premium), des licences Office 365 Entreprise (E1/E3/E5/F3) ou des licences Microsoft 365 Entreprise (E3/E5/F3) (et soient inscrits à Office à l’aide de leur ID d’organisation) et qu’ils ont des boîtes aux lettres Exchange Online et Exchange Online actives. Votre annuaire d’abonnement doit être dans ou fédéré pour Azure Active Directory.
Vous pouvez afficher les exigences spécifiques Office et Exchange ci-dessous, ou utiliser le contrôle de compatibilité [de déploiement centralisé.](#centralized-deployment-compatibility-checker)

La fonctionnalité Déploiement centralisé ne prend pas en charge ce qui suit :

- des compléments ciblant Word, Excel ou PowerPoint dans Office 2013 ;
- un service d'annuaire local ;
- Déploiement de la mise en Exchange d’une boîte aux lettres sur place
- le déploiement de compléments vers SharePoint ;
- Teams applications
- Déploiement de composants COM (Component Object Model) ou Visual Studio Tools pour Office (VSTO) de composants.
- Déploiements de Microsoft 365 qui n’incluent pas de Exchange Online telles que les S SKUs : Microsoft 365 Apps for Business et Microsoft 365 Apps for Enterprise.

### <a name="office-requirements"></a>Office Conditions requises

- Pour word, Excel et les PowerPoint, vos utilisateurs doivent utiliser l’une des utilisations suivantes :
  - Sur un appareil Windows, version 1704 ou ultérieure des licences Microsoft 365 Business (Business Basic, Business Standard, Business Premium), des licences Office 365 Entreprise (E1/E3/E5/F3) ou des licences Microsoft 365 Entreprise (E3/E5/F3).
  - Sur un Mac, version 15.34 ou ultérieure.

- Pour Outlook, vos utilisateurs doivent utiliser l’une des utilisations suivantes :
  - Version 1701 ou ultérieure des licences Microsoft 365 Business (Business Basic, Business Standard, Business Premium), licences Office 365 Entreprise (E1/E3/E5/F3) ou licences Microsoft 365 Entreprise (E3/E5/F3).
  - Version 1808 ou ultérieure de Office Professionnel Plus 2019 ou Office Standard 2019.
  - Version 16.0.4494.1000 ou ultérieure de Office Professionnel Plus 2016 (MSI) ou Office Standard 2016 (MSI)\*
  - Version 15.0.4937.1000 ou ultérieure de Office Professionnel Plus 2013 (MSI) ou Office Standard 2013 (MSI)\*
  - Version 16.0.9318.1000 ou ultérieure de Office 2016 pour Mac
- Version 2.75.0 ou ultérieure de Outlook mobile pour iOS
- Version 2.2.145 ou ultérieure de Outlook mobile pour Android

    *Les versions MSI de Outlook afficher les add-ins installés par l’administrateur dans le ruban Outlook approprié, et non dans la section « Mes modules ».

### <a name="exchange-online-requirements"></a>Exchange Online requise

Microsoft Exchange les manifestes de votre organisation. L’administrateur déployant des applications et les utilisateurs qui les reçoivent doivent se trouver sur une version de Exchange Online qui prend en charge l’authentification OAuth.

Pour connaître la configuration utilisée, consultez l'administrateur Exchange de votre organisation. Vous pouvez vérifier la connectivité OAuth de chaque utilisateur à l'aide de l'applet de commande PowerShell [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity).


### <a name="centralized-deployment-compatibility-checker"></a>Contrôle de compatibilité du déploiement centralisé

À l’aide du contrôle de compatibilité du déploiement centralisé, vous pouvez vérifier si les utilisateurs de votre client sont configurer pour utiliser le déploiement centralisé pour Word, Excel et PowerPoint. Le vérificateur de compatibilité n'est pas requis pour la prise en charge d'Outlook. Téléchargez [le contrôle de compatibilité.](https://aka.ms/officeaddindeploymentorgcompatibilitychecker)

#### <a name="run-the-compatibility-checker"></a>Exécuter le contrôle de compatibilité

1. Démarrez une fenêtre avec PowerShell.exe élevée.

2. Exécutez la commande suivante :

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. Exécutez **la commande Invoke-CompatabilityCheck** :

   ```powershell
   Invoke-CompatibilityCheck
   ```
   Cette commande vous demande  *_TenantDomain_* (par exemple, *TailspinToysIncorporated.onmicrosoft). </span> com*) et  *_les informations d’identification TenantAdmin_* (utilisez vos informations d’identification d’administrateur global), puis demande le consentement.

   > [!NOTE]
   > Selon le nombre d'utilisateurs dans votre client, l'exécution du vérificateur peut prendre quelques minutes ou plusieurs heures. 
  
Une fois l'exécution de l'outil terminée, celui-ci génère un fichier de sortie dans un format séparé par des virgules (.csv). Le fichier est enregistré dans **le répertoire de travail actuel** par défaut. Le fichier de sortie contient les informations suivantes :

- Nom d'utilisateur

- ID d'utilisateur (adresse de courrier de l'utilisateur)

- Déploiement centralisé prêt - Si les autres éléments sont vérifiés

- Office plan : le plan de Office dont ils sont titulaires d’une licence

- Activation d'Office - Si l'utilisateur a activé Office

- Boîte aux lettres prise en charge - Si l'utilisateur a une boîte aux lettres OAuth

> [!NOTE]
> L’authentification multifacteur n’est pas prise en charge lors de l’utilisation du module PowerShell de déploiement central. Le module fonctionne uniquement avec l’authentification de base.

## <a name="user-and-group-assignments"></a>Affectations à des utilisateurs et groupes

La fonctionnalité déploiement centralisé prend actuellement en charge la majorité des groupes pris en charge par les Azure Active Directory, y compris les groupes Microsoft 365, les listes de distribution et les groupes de sécurité.

> [!NOTE]
> Les groupes de sécurité sans extension messagerie ne sont pas actuellement pas pris en charge.

Le déploiement centralisé prend en charge les affectations à des utilisateurs individuels, des groupes et à tous les utilisateurs du client. La fonctionnalité Déploiement centralisé prend en charge les utilisateurs au sein de groupes de niveau supérieur ou de groupes sans groupes parents, mais pas les utilisateurs au sein de groupes imbriqués ou qui ont des groupes parents.

Examinons l'exemple suivant où un complément est affecté à Nicoletta, à Ariane et au groupe Service commercial. Le Service des ventes Région ouest étant un groupe imbriqué, aucun complément n'est affecté à Noël et Jérôme.

![Diagramme du service des ventes.](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)


### <a name="find-out-if-a-group-contains-nested-groups"></a>Déterminer si un groupe contient des groupes imbriqués

La manière la plus simple de détecter si un groupe contient des groupes imbriqués consiste à afficher la carte de visite du groupe dans Outlook. Si vous entrez le nom du groupe dans le champ **À** d’un e-mail, puis sélectionnez le nom du groupe lorsqu’il est résolu, il vous indique s’il contient des utilisateurs ou des groupes imbrmbrés. Dans l'exemple ci-dessous, l'onglet **Membres** de la carte de visite Outlook du groupe Test n'affiche aucun utilisateur et seulement deux sous-groupes.

![Onglet Membres de la Outlook de contact.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Vous pouvez effectuer la requête inverse en résolvant le groupe pour voir s'il est membre d'un groupe. Dans l'exemple ci-dessous, vous pouvez voir sous l'onglet **Appartenance** de la carte de visite Outlook que le Sous-groupe 1 est membre du groupe Test.

![Onglet Appartenance de la carte Outlook contact.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Vous pouvez également utiliser l'API Graph Azure Active Directory pour exécuter des requêtes afin d'obtenir la liste des groupes au sein d'un groupe. Pour plus d'informations, voir [Opérations sur les groupes | Référence de l'API Graph](/previous-versions/azure/ad/graph/api/groups-operations).

### <a name="contacting-microsoft-for-support"></a>Contacter Microsoft pour obtenir une assistance

Si vous ou vos utilisateurs rencontrez des problèmes lors du chargement du add-in lors de l’utilisation d’applications Office pour le web (Word, Excel, etc.), qui ont été déployées de manière centralisée, vous devrez peut-être contacter le support Microsoft[(](../../business-video/get-help-support.md)découvrez comment ). Fournissez les informations suivantes sur votre environnement Microsoft 365 dans le ticket de support.

| Plateforme | Informations de débogage |
|:-----|:-----|
|Bureau | Journaux Charles/Fiddler  <br/>  ID de client ([découvrez comment](/onedrive/find-your-office-365-tenant-id))  <br/>  CorrelationID. Affichez la source de l’une des pages Office et recherchez la valeur de l’ID de corrélation et envoyez-la pour prendre en charge :  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">`  <br/>  `<input name="user_id" type="hidden" value="1003bffd96933623"></form>` |
|Clients riches (Windows, Mac) | Journaux Charles/Fiddler  <br/>  Numéros de build de l’application cliente (de préférence en tant que capture d’écran de **Fichier/Compte)** |

## <a name="related-content"></a>Contenu associé

[Déployer des add-ins dans le Centre d’administration](../manage/manage-deployment-of-add-ins.md) (article)\
[Gérer les add-ins dans le Centre d’administration](manage-addins-in-the-admin-center.md) (article)\
[FAQ sur le déploiement centralisé](../manage/centralized-deployment-faq.yml) (article)\
[Mettre à niveau votre Microsoft 365 pour les utilisateurs professionnels](../setup/upgrade-users-to-latest-office-client.md) vers le client Office le plus récent (article)
 
