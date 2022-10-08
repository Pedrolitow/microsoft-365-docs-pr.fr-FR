---
title: Déterminer si le déploiement centralisé de compléments fonctionne pour votre organisation
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
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
description: Déterminez si votre locataire et vos utilisateurs répondent aux exigences, afin que vous puissiez utiliser le déploiement centralisé pour déployer des compléments Office.
ms.openlocfilehash: c818a8824bb2c0ee49d6cc9cd27aba0b1f235475
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68187248"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>Déterminer si le déploiement centralisé de compléments fonctionne pour votre organisation

Le déploiement centralisé est le moyen le plus recommandé et le plus riche en fonctionnalités pour la plupart des clients de déployer des compléments Office sur des utilisateurs et des groupes au sein de votre organisation. Si vous êtes administrateur, utilisez ces conseils pour déterminer si votre organisation et vos utilisateurs répondent aux exigences afin de pouvoir utiliser le déploiement centralisé.

Une déploiement centralisé offre les avantages suivants :

- Un administrateur peut déployer et affecter un complément directement à un utilisateur, à plusieurs utilisateurs via un groupe ou à tous les membres de l’organisation (voir Administration section relative aux conditions requises pour plus d’informations).
- Lorsque l’application Office appropriée démarre, le complément se télécharge automatiquement. Si le complément prend en charge les commandes de complément, le complément apparaît automatiquement dans le ruban au sein de l’application Office.
- Les compléments n’apparaissent plus pour les utilisateurs si l’administrateur désactive ou supprime le complément, ou si l’utilisateur est supprimé d’Azure Active Directory ou d’un groupe auquel le complément est affecté.

Le déploiement centralisé prend en charge trois plateformes de bureau pour les applications Windows, Mac et Office en ligne. Le déploiement centralisé prend également en charge iOS et Android (compléments Outlook Mobile uniquement).

L’affichage d’un complément pour le client pour tous les utilisateurs peut prendre jusqu’à 24 heures.

## <a name="before-you-begin"></a>Avant de commencer

Le déploiement centralisé des compléments nécessite que les utilisateurs utilisent des licences Microsoft 365 Business (Business Basic, Business Standard, Business Premium), des licences Office 365 Entreprise (E1/E3/E5/F3) ou des licences Microsoft 365 Entreprise (E3/E5/F3) (et qu’ils soient connectés à Office à l’aide de leur ID d’organisation), Office 365 Éducation licences (A1/A3/A5) ou Microsoft 365 Éducation licences (A3/A5) et disposent de boîtes aux lettres Exchange Online et actives Exchange Online. Votre répertoire d’abonnement doit être dans Ou fédéré vers Azure Active Directory.
Vous pouvez afficher des exigences spécifiques pour Office et Exchange ci-dessous, ou utiliser le [vérificateur de compatibilité de déploiement centralisé](#centralized-deployment-compatibility-checker).

La fonctionnalité Déploiement centralisé ne prend pas en charge ce qui suit :

- Compléments qui ciblent la version MSI Office (sauf Outlook 2016)
- un service d'annuaire local ;
- Déploiement de complément dans une boîte aux lettres Exchange on-Prem
- le déploiement de compléments vers SharePoint ;
- Applications Teams
- Déploiement de compléments COM (Component Object Model) ou Visual Studio Tools pour Office (VSTO).
- Déploiements de Microsoft 365 qui n’incluent pas de Exchange Online telles que des références SKU : Microsoft 365 Apps pour les entreprises et Microsoft 365 Apps pour Entreprise.

### <a name="office-requirements"></a>Configuration requise pour Office

- Pour les compléments Word, Excel et PowerPoint, vos utilisateurs doivent utiliser l’une des options suivantes :
  - Sur un appareil Windows, version 1704 ou ultérieure des licences Microsoft 365 Business (Business Basic, Business Standard, Business Premium), Office 365 Entreprise licences (E1/E3/E5/F3) ou Microsoft 365 Entreprise licences (E3/E5/F3).
  - Sur un Mac, version 15.34 ou ultérieure.

- Pour Outlook, vos utilisateurs doivent utiliser l’une des options suivantes :
  - Version 1701 ou ultérieure des licences Microsoft 365 Business (Business Basic, Business Standard, Business Premium), Office 365 Entreprise licences (E1/E3/E5/F3) ou Microsoft 365 Entreprise licences (E3/E5/F3).
  - Version 1808 ou ultérieure de Office Professionnel Plus 2019 ou Office Standard 2019.
  - Version 16.0.4494.1000 ou ultérieure de Office Professionnel Plus 2016 (MSI) ou Office Standard 2016 (MSI)\*
  - Version 15.0.4937.1000 ou ultérieure de Office Professionnel Plus 2013 (MSI) ou Office Standard 2013 (MSI)\*
  - Version 16.0.9318.1000 ou ultérieure de Office 2016 pour Mac
- Version 2.75.0 ou ultérieure d’Outlook Mobile pour iOS
- Version 2.2.145 ou ultérieure d’Outlook Mobile pour Android

    *Les versions MSI d’Outlook affichent les compléments installés par l’administrateur dans le ruban Outlook approprié, et non dans la section « Mes compléments ».

### <a name="exchange-online-requirements"></a>exigences de Exchange Online

Microsoft Exchange stocke les manifestes de complément dans le locataire de votre organisation. L’administrateur qui déploie des compléments et les utilisateurs qui reçoivent ces compléments doivent se trouver sur une version de Exchange Online qui prend en charge l’authentification OAuth.

Check with your organization's Exchange admin to find out which configuration is in use. OAuth connectivity per user can be verified by using the [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) PowerShell cmdlet.

### <a name="admin-requirements"></a>Configuration requise pour l’administrateur

Pour déployer un complément via un déploiement centralisé, vous devez être administrateur général ou administrateur Exchange dans l’organisation.

> [!NOTE]
> Un administrateur Exchange peut déployer un complément si le rôle **Administrateur** d’application est ajouté ou si la propriété **Inscriptions d’applications** a la valeur true dans le Centre d’administration Azure Active Directory, comme illustré dans l’image suivante :
>
> ![image](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)

### <a name="centralized-deployment-compatibility-checker"></a>Vérificateur de compatibilité de déploiement centralisé

À l’aide du vérificateur de compatibilité de déploiement centralisé, vous pouvez vérifier si les utilisateurs de votre locataire sont configurés pour utiliser le déploiement centralisé pour Word, Excel et PowerPoint. Le vérificateur de compatibilité n'est pas requis pour la prise en charge d'Outlook. Téléchargez le [vérificateur de compatibilité](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).

#### <a name="run-the-compatibility-checker"></a>Exécuter le vérificateur de compatibilité

1. Démarrez une fenêtre de PowerShell.exe avec élévation de privilèges.

2. Exécutez la commande suivante :

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. Exécutez la commande **Invoke-CompatibilityCheck** :

   ```powershell
   Invoke-CompatibilityCheck
   ```

   Cette commande vous invite à entrer _les informations d’identification TenantDomain_ (par exemple, _TailspinToysIncorporated.onmicrosoft.com_) et _TenantAdmin_ (utilisez vos informations d’identification d’administrateur général), puis demande le consentement.

   > [!NOTE]
   > Selon le nombre d'utilisateurs dans votre client, l'exécution du vérificateur peut prendre quelques minutes ou plusieurs heures.

Une fois l'exécution de l'outil terminée, celui-ci génère un fichier de sortie dans un format séparé par des virgules (.csv). Par défaut, le fichier est enregistré **dans le répertoire de travail actif** . Le fichier de sortie contient les informations suivantes :

- Nom d'utilisateur
- ID d'utilisateur (adresse de courrier de l'utilisateur)
- Déploiement centralisé prêt - Si les autres éléments sont vérifiés
- Plan Office - Plan d’Office pour lequel ils sont titulaires d’une licence
- Activation d'Office - Si l'utilisateur a activé Office
- Boîte aux lettres prise en charge - Si l'utilisateur a une boîte aux lettres OAuth

Si vos rapports Microsoft 365 affichent des noms d’utilisateur anonymes au lieu de noms d’utilisateur réels, corrigez ce problème en modifiant le paramètre rapports dans Centre d'administration Microsoft 365. Pour obtenir des instructions détaillées, consultez [les rapports Microsoft 365 qui affichent des noms d’utilisateurs anonymes au lieu de noms d’utilisateurs réels](/office365/troubleshoot/miscellaneous/reports-show-anonymous-user-name).

> [!NOTE]
> L’authentification multifacteur n’est pas prise en charge lors de l’utilisation du module PowerShell de déploiement central. Le module fonctionne uniquement avec l’authentification de base.

## <a name="user-and-group-assignments"></a>Affectations à des utilisateurs et groupes

La fonctionnalité Déploiement centralisé prend actuellement en charge la majorité des groupes pris en charge par Azure Active Directory, notamment les groupes Microsoft 365, les listes de distribution, les groupes dynamiques et les groupes de sécurité.

> [!NOTE]
> Les groupes de sécurité sans extension messagerie ne sont pas actuellement pas pris en charge.

Le déploiement centralisé prend en charge les affectations à des utilisateurs individuels, à des groupes et à tous les membres du locataire. La fonctionnalité Déploiement centralisé prend en charge les utilisateurs au sein de groupes de niveau supérieur ou de groupes sans groupes parents, mais pas les utilisateurs au sein de groupes imbriqués ou qui ont des groupes parents.

Take a look at the following example where Sandra, Sheila, and the Sales Department group are assigned to an add-in. Because the West Coast Sales Department is a nested group, Bert and Fred aren't assigned to an add-in.

![MicrosoftTeams-image](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Déterminer si un groupe contient des groupes imbriqués

La manière la plus simple de détecter si un groupe contient des groupes imbriqués consiste à afficher la carte de visite du groupe dans Outlook. Si vous entrez le nom du groupe dans le champ **À** d’un e-mail, puis sélectionnez le nom du groupe lorsqu’il sera résolu, il vous indiquera s’il contient des utilisateurs ou des groupes imbriqués. Dans l'exemple ci-dessous, l'onglet **Membres** de la carte de visite Outlook du groupe Test n'affiche aucun utilisateur et seulement deux sous-groupes.

![Onglet Membres de la carte de visite Outlook.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

You can do the opposite query by resolving the group to see if it's a member of any group. In the example below, you can see under the **Membership** tab of the Outlook contact card that Sub Group 1 is a member of the Test Group.

![Onglet Appartenance de la carte de visite Outlook.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Vous pouvez également utiliser l'API Graph Azure Active Directory pour exécuter des requêtes afin d'obtenir la liste des groupes au sein d'un groupe. Pour plus d’informations, consultez [Opérations sur les groupes| API Graph référence](/previous-versions/azure/ad/graph/api/groups-operations).

### <a name="contacting-microsoft-for-support"></a>Contacter Microsoft pour obtenir une assistance

Si vous ou vos utilisateurs rencontrez des problèmes lors du chargement du complément lors de l’utilisation d’applications Office pour le web (Word, Excel, etc.), qui ont été déployées de manière centralisée, vous devrez peut-être contacter le support Microsoft ([découvrez comment](../../business-video/get-help-support.md) procéder. Fournissez les informations suivantes sur votre environnement Microsoft 365 dans le ticket de support.

|Plateforme|Informations de débogage|
|---|---|
|Office|Journaux Charles/Fiddler <br/> ID de locataire ([découvrez comment](/onedrive/find-your-office-365-tenant-id)) <br/> Correlationid. Affichez la source de l’une des pages de bureau, recherchez la valeur de l’ID de corrélation et envoyez-la à la prise en charge :  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">` <br/> `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`|
|Clients riches (Windows, Mac)|Journaux Charles/Fiddler <br/> Numéros de build de l’application cliente (de préférence sous la forme d’une capture d’écran à partir d’un **fichier/d’un compte**)|

## <a name="related-content"></a>Contenu associé

[Déployer des compléments dans le centre d’administration](../manage/manage-deployment-of-add-ins.md) (article)\
[Gérer les compléments dans le centre d’administration](manage-addins-in-the-admin-center.md) (article)\
[FAQ sur le déploiement centralisé](../manage/centralized-deployment-faq.yml) (article)\
[Mettre à niveau vos utilisateurs Microsoft 365 pour les entreprises vers le dernier client Office](../setup/upgrade-users-to-latest-office-client.md) (article)
