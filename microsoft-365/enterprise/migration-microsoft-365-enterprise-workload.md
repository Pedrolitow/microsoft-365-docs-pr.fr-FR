---
title: Migration vers Microsoft 365 Entreprise
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/23/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Suivez le processus de migration des versions de Microsoft Office, des serveurs Office et de Windows vers Microsoft 365 Entreprise au sein de votre organisation.
ms.openlocfilehash: 7506d374391e05202be685d8ebfe8a04e8d62761
ms.sourcegitcommit: 144c0f3c2c6112bffc5a9b04392a38123a979ebc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "43053082"
---
# <a name="migration-to-microsoft-365-enterprise"></a>Migration vers Microsoft 365 Entreprise

La plupart des entreprises disposent d’un environnement hétérogène avec plusieurs versions de systèmes d’exploitation, de logiciels clients et de logiciels serveurs. Microsoft 365 Entreprise inclut les versions les plus sécurisées de ces composants clés de votre infrastructure informatique, avec des fonctionnalités de productivité conçues pour tirer parti des technologies de cloud.

Afin d’optimiser la valeur commerciale de la suite intégrée Microsoft 365 Entreprise, commencez par planifier et implémenter une stratégie pour migrer les versions :

- du client Office installé sur vos ordinateurs vers Office 365 ProPlus ;
- des serveurs Office installés sur vos serveurs vers leurs services équivalents dans Office 365 ;
- Windows 7 et Windows 8.1 sur vos appareils vers Windows 10 Entreprise

>[!Note]
>Windows 7 a atteint la fin du support le **14 janvier 2020**. Pour plus d’informations, cliquez [ici](https://support.microsoft.com/help/4057281/windows-7-support-will-end-on-january-14-2020).
>

Effectuer toutes ces migrations au fil du temps permet à votre entreprise de bénéficier d’un [espace de travail moderne](https://www.microsoft.com/microsoft-365/blog/2018/04/27/making-it-simpler-with-a-modern-workplace/), ainsi que d’un environnement intégré et sécurisé qui favorise le travail d’équipe et la créativité dans votre organisation, grâce à Microsoft 365 Entreprise. 

Pour plus d’informations sur la migration des utilisateurs et données pour des charges de travail Office 365 spécifiques :

- Boîtes aux lettres utilisateur d’Exchange Server vers Exchange Online, voir [Charge de travail Exchange Online](exchangeonline-workload.md).
- Données SharePoint de SharePoint Server vers SharePoint Online, voir [Charge de travail SharePoint Online](sharepoint-online-onedrive-workload.md).
- Skype Entreprise Online vers Microsoft Teams, voir la [Charge de travail Microsoft Teams](teams-workload.md).

## <a name="migration-for-microsoft-office-client-products"></a>Migration pour les produits client Microsoft Office

De nombreuses petites et grandes entreprises utilisent peut-être une combinaison d’anciennes versions des produits clients Office, tels que Word, Excel et PowerPoint. Ces anciennes versions :

- peuvent être [mises à jour](https://support.office.com/article/install-office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5) avec les derniers correctifs d’assistance et mises à jour de sécurité, mais le processus est parfois manuel et peut ne pas convenir à votre entreprise ;
- ne sont pas configurées de façon optimale pour tirer parti des technologies cloud de Microsoft et pour vous aider à transformer numériquement votre entreprise.
- Ne contiennent pas de nouvelles fonctionnalités.
 
Microsoft 365 Entreprise inclut Office 365 ProPlus, une version des produits client Office disponible avec une licence Microsoft 365 Entreprise, installée et mise à jour à partir du cloud de Microsoft. Office 365 ProPlus inclut des mises à jour de sécurité et les fonctionnalités les plus récentes. Si vous souhaitez en savoir plus, consultez la page [À propos d'Office 365 ProPlus en entreprise](https://docs.microsoft.com/deployoffice/about-office-365-proplus-in-the-enterprise).

### <a name="office-2007"></a>Office 2007

Pour les versions d’Office dans la version Office 2007, la date de fin de l’assistance est déjà passée. Pour plus d’informations, consultez la page relative à la [feuille de route pour la fin de l’assistance pour Office 2007](https://docs.microsoft.com/deployoffice/office-2007-end-support-roadmap).

Au lieu de mettre à niveau vos ordinateurs exécutant Office 2007 avec Office 2010, Office 2013 ou Office 2016, vous pouvez :

1. obtenir une licence Microsoft 365 et l’affecter à vos utilisateurs ;
2. désinstaller Office 2007 sur leur ordinateur ;
3. installer Office 365 ProPlus, individuellement ou conjointement avec un déploiement informatique. Pour plus d’informations, consultez la page [Phase 4 : Office 365 ProPlus](office365proplus-infrastructure.md).

Office 365 ProPlus installe automatiquement les mises à jour et peut tirer parti des services sur le cloud d’Office 365 pour renforcer la productivité et la sécurité.

### <a name="office-2010"></a>Office 2010

Pour les versions d’Office dans la version Office 2010, la fin de la prise en charge est le **13 octobre 2020**. Pour plus d’informations, voir [Feuille de route de la fin de la prise en charge d’Office 2010](https://docs.microsoft.com/deployoffice/office-2010-end-support-roadmap).

Au lieu de mettre à niveau vos ordinateurs exécutant Office 2010 avec Office 2013 ou Office 2016, les deux devant être mis à jour manuellement, vous pouvez : 

1. obtenir une licence Microsoft 365 et l’affecter à vos utilisateurs ;
2. désinstaller Office 2010 de leur ordinateur ;
3. installer Office 365 ProPlus, individuellement ou conjointement avec un déploiement informatique. Pour plus d’informations, consultez la page [Phase 4 : Office 365 ProPlus](office365proplus-infrastructure.md).

Office 365 ProPlus installe automatiquement à la fois les mises à jour de sécurité et de nouvelle fonctionnalité, et peut tirer parti des services sur le cloud de Microsoft 365 pour renforcer la productivité et la sécurité.

### <a name="office-2013-and-office-2016"></a>Office 2013 et Office 2016

La fin de la feuille de route du support technique pour les versions d’Office 2013 et Office 2016 n’a pas encore été déterminée. Cependant, comme avec Office 2010, vous devez encore [installer les mises à jour de sécurité](https://support.office.com/article/install-office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5), qui peuvent ne pas évoluer correctement en fonction de la taille de votre organisation.

Plutôt que de continuer à mettre à jour vos ordinateurs avec les mises à jour de sécurité les plus récentes d’Office 2013 ou Office 2016, ou à mettre à jour vos ordinateurs d’Office 2013 vers Office 2016, prévoyez ce qui suit :

1. obtenir une licence Microsoft 365 et l’affecter à vos utilisateurs ;
2. désinstaller Office 2013 ou Office 2016 de leur ordinateur ;
3. installer Office 365 ProPlus, individuellement ou conjointement avec un déploiement informatique. Pour plus d’informations, consultez la page [Phase 4 : Office 365 ProPlus](office365proplus-infrastructure.md).

Office 365 ProPlus installe automatiquement à la fois les mises à jour de sécurité et de nouvelle fonctionnalité, et peut tirer parti des services sur le cloud de Microsoft 365 pour renforcer la productivité et la sécurité.

## <a name="migration-for-microsoft-office-server-products"></a>Migration pour les produits serveur Microsoft Office

De nombreuses petites et grandes entreprises utilisent peut-être une combinaison d’anciennes versions des produits serveur Office, tels que Exchange Server et SharePoint. Ces anciennes versions :

- doivent être mises à jour avec les derniers correctifs d’assistance et mises à jour de sécurité. Dans certains cas, ces mises à jour sont publiées tous les mois ;
- ne sont pas configurées de façon optimale pour tirer parti des technologies cloud de Microsoft et pour vous aider à transformer numériquement votre entreprise.
- n’incluent pas de nouvelles applications de productivité, telles que Microsoft Teams ;
- n’incluent pas les dernières fonctionnalités de sécurité, telles que la protection avancée contre les menaces pour Exchange.

Microsoft 365 Entreprise inclut Office 365, qui inclut les versions Cloud des services Office Server qui utilisent en partie les mêmes outils que les versions locales du logiciel Office Server, tels que les navigateurs Web et le client Outlook. Ces services sont continuellement mis à jour pour la sécurité sans impliquer d’informatique, ce qui vous permet de gagner du temps pour la maintenance et la mise à jour des serveurs locaux. Ces services présentent également de nouvelles fonctionnalités qui ne sont pas disponibles dans les logiciels Office Server. 

### <a name="office-server-2007"></a>Office Server 2007

Pour les produits serveurs de la version Office 2007, la date de fin de l’assistance est déjà passée. Pour plus d’informations, consultez les articles suivants :

- [Feuille de route pour la fin de l’assistance pour Exchange 2007](https://docs.microsoft.com/office365/enterprise/exchange-2007-end-of-support)
- [Feuille de route pour la fin de l’assistance pour SharePoint Server 2007](https://docs.microsoft.com/office365/enterprise/sharepoint-2007-end-of-support)
- [Feuille de route pour la fin de l’assistance pour Project Server 2007](https://docs.microsoft.com/office365/enterprise/project-server-2007-end-of-support)
- [Feuille de route pour la fin de l’assistance pour Office Communications Server](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/upgrade)
- [Feuille de route pour la fin de l’assistance pour PerformancePoint Server 2007](https://docs.microsoft.com/office365/enterprise/pps-2007-end-of-support)

Au lieu de mettre à niveau vos produits serveur de la version Office 2007 avec les produits serveur des versions Office 2010, Office 2013 ou Office 2016, vous pouvez :

1. migrer les données de vos serveurs Office 2007 vers Office 365. Pour vous aider, faites appel à un partenaire Microsoft ;
2. déployer les nouveaux processus de travail et fonctionnalités pour vos utilisateurs ;
3. supprimer les serveurs locaux exécutant les produits serveurs Office 2007 lorsque vous n’en avez plus besoin.

### <a name="office-server-2010"></a>Office Server 2010

Pour les produits serveurs suivants de la version Office 2010, la fin de l’assistance est fixée au **13 octobre 2020** :

- [Exchange Server 2010](https://docs.microsoft.com/office365/enterprise/exchange-2010-end-of-support)
- [SharePoint Server 2010](https://docs.microsoft.com/office365/enterprise/upgrade-from-sharepoint-2010)

Au lieu de mettre à niveau ces produits serveur de la version Office 2010 avec les produits serveur des versions Office 2013 ou Office 2016, vous pouvez :

1. Migrer les données sur vos serveurs Office 2010 vers Microsoft 365. Pour plus d’informations, voir [FastTrack pour Microsoft 365](https://fasttrack.microsoft.com/microsoft365). Sinon, embauchez un partenaire Microsoft.
2. déployer les nouveaux processus de travail et fonctionnalités pour vos utilisateurs ;
3. supprimer les serveurs locaux exécutant les produits serveurs Office 2010 lorsque vous n’en avez plus besoin.

### <a name="office-server-2013"></a>Office Server 2013

Pour les produits serveur de la version Office 2013, la fin de l’assistance n’a pas été déterminée. Au lieu de mettre à niveau vos produits serveurs de la version Office 2013 avec les produits serveurs de la version Office 2016, vous pouvez :

1. migrer les données de vos serveurs Office 2013 vers Office 365. Pour vous aider, consultez la page [FastTrack pour Microsoft 365](https://fasttrack.microsoft.com/microsoft365) ou faites appel à un partenaire Microsoft ;
2. déployer les nouveaux processus de travail et fonctionnalités pour vos utilisateurs ;
3. supprimer les serveurs locaux exécutant les produits serveur Office 2013 lorsque vous n’en avez plus besoin.

### <a name="office-server-2016"></a>Office Server 2016

Pour les produits serveurs de la version Office 2016, la fin de l’assistance n’a pas été déterminée. Pour tirer parti du service cloud et des améliorations apportées pour transformer numériquement votre entreprise, vous pouvez :

1. migrer les données de vos serveurs Office 2016 vers Office 365. Pour vous aider, consultez la page [FastTrack pour Microsoft 365](https://fasttrack.microsoft.com/microsoft365) ou faites appel à un partenaire Microsoft ;
2. déployer les nouveaux processus de travail et fonctionnalités pour vos utilisateurs ;
3. supprimer les serveurs locaux exécutant les produits serveur Office 2016 lorsque vous n’en avez plus besoin.

## <a name="migration-for-microsoft-windows-7-and-81"></a>Migration pour Microsoft Windows 7 et 8.1

Windows 7 a atteint la fin du support le **14 janvier 2020**. Pour migrer vos appareils exécutant Windows 7 ou Windows 8.1, vous pouvez effectuer une [mise à niveau sur place](https://docs.microsoft.com/microsoft-365/enterprise/windows10-deploy-inplaceupgrade). 

Pour accéder à d’autres méthodes, voir [Scénarios de déploiement de Windows 10](https://docs.microsoft.com/windows/deployment/windows-10-deployment-scenarios). Vous pouvez également [planifier le déploiement de Windows 10](https://aka.ms/planforwin10deployment) par vous-même.

## <a name="summary-of-options-for-office-2010-clients-and-servers-and-windows-7"></a>Résumé des options pour les clients et serveurs Office 2010 et Windows 7

Pour consulter un résumé visuel des options de mise à niveau, de migration et de déplacement vers le Cloud pour ces produits, voir l’[affiche de fin du support technique](../media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf).

[![Image de l’affiche de la fin de la prise en charge pour les clients et serveurs Office 2010 et Windows 7](../media/migration-microsoft-365-enterprise-workload/office2010-windows7-end-of-support.png)](../media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf)

Cette affiche d’une page est un moyen rapide de comprendre les différents chemins que vous pouvez prendre pour empêcher les produits client et serveur Office 2010 et Windows 7 d’atteindre la fin du support, avec les chemins d’accès favoris et la prise en charge de la destination qui en résulte dans Microsoft 365 Entreprise mis en surbrillance.

Vous pouvez [télécharger cette affiche](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf) et l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Découvrez comment les experts informatiques de Microsoft ont migré l’entreprise vers Microsoft 365 Entreprise en lisant les ressources suivantes : 

- [Déploiement et mise à jour de Microsoft Office 365 ProPlus](https://www.microsoft.com/itshowcase/Article/Content/757/Deploying-and-updating-Microsoft-Office-365-ProPlus)
- [Microsoft migre 150 000 boîtes aux lettres vers Exchange Online](https://www.microsoft.com/itshowcase/Article/Content/577/Microsoft-migrates-150000-mailboxes-to-Exchange-Online)
- [SharePoint dans le cloud : découvrez comment Microsoft a mis en œuvre sa propre migration](https://www.microsoft.com/itshowcase/Article/Content/691/SharePoint-to-the-cloud-Learn-how-Microsoft-ran-its-own-migration)
- [Déploiement de Windows 10 chez Microsoft en tant que mise à niveau sur place](https://www.microsoft.com/itshowcase/Article/Content/668/Deploying-Windows-10-at-Microsoft-as-an-inplace-upgrade)
- [Déploiement de Windows 10 : conseils et astuces de Microsoft IT](https://www.microsoft.com/itshowcase/Article/Content/951/Windows-10-deployment-tips-and-tricks-from-Microsoft-IT) (vidéo)

## <a name="transition-your-entire-organization"></a>Migration de l’organisation entière

Pour tirer le meilleur parti de la migration de l’ensemble de votre organisation vers les produits et services de Microsoft 365 Entreprise, téléchargez l’[affiche de transition](../media/deploy-microsoft-365-enterprise/transition-org-to-m365.pdf).

[![Image de l’affiche pour la transition vers Microsoft 365](../media/deploy-microsoft-365-enterprise/transition-org-to-m365.png)](../media/deploy-microsoft-365-enterprise/transition-org-to-m365.pdf)

Cette affiche en double page vous permet d’inventorier rapidement votre infrastructure et de trouver des instructions pour effectuer la migration vers les produits ou services correspondants dans Microsoft 365 Entreprise. Elle reprend les produits Windows et Office et d’autres éléments d’infrastructure et de sécurité comme la gestion des appareils, l’identité, les informations et la protection contre les menaces.

Vous pouvez [télécharger cette affiche](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/deploy-microsoft-365-enterprise/transition-org-to-m365.pdf) et l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="result"></a>Résultat

Votre entreprise a migré les anciennes versions de Microsoft Office, des serveurs Office et de Windows vers Microsoft 365 Entreprise.
