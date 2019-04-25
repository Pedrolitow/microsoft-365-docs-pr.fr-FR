---
title: Scénarios et charges de travail Microsoft 365 Entreprise
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Intégrez les utilisateurs de votre organisation aux charges de travail productivité de Microsoft 365 Entreprise.
ms.openlocfilehash: 30dbf913016687025c6159f1f1fc311462a13d29
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32291635"
---
# <a name="microsoft-365-enterprise-workloads-and-scenarios"></a>Scénarios et charges de travail Microsoft 365 Entreprise

Pour bénéficier des avantages de la créativité et du travail d’équipe de Microsoft 365 Entreprise, déployez sur votre infrastructure de base les charges de travail suivantes :

- [Microsoft Teams](teams-workload.md)
- [Exchange Online](exchangeonline-workload.md)
- [SharePoint Online](sharepoint-online-onedrive-workload.md)

Pour disposer d’une feuille de route générale concernant la migration de votre organisation toute entière vers Microsoft 365 Entreprise, incluant les produits clients Microsoft Office, les produits Office Server locaux et les appareils basés sur Microsoft Windows, voir la charge de travail [migration](migration-microsoft-365-enterprise-workload.md).

Les scénarios utilisent des fonctionnalités et services de Microsoft 365 Entreprise de façon intégrée pour répondre à des besoins métier. L’un de ces besoins est la protection des données hautement réglementées stockées dans Microsoft 365. Les données hautement réglementées incluent les biens numériques suivants :

- sujettes à des réglementations régionales ;
- les plus précieuses de votre organisation comme les secrets commerciaux, les informations sur les ressources humaines ou financières et la stratégie de l’organisation.

Pour protéger ces données contre des menaces internes et externes, suivez les instructions fournies dans [Sites SharePoint Online et Microsoft Teams pour les données hautement réglementées](teams-sharepoint-online-sites-highly-regulated-data.md). Ce scénario vous guide dans la configuration d’un site SharePoint Online ou d’une équipe Microsoft Teams afin de stocker en toute sécurité vos données les plus précieuses.

Les charges de travail et les scénarios décrits dans le guide de déploiement global de Microsoft 365 Entreprise sont les suivants :

![](./media/deploy-workloads/m365-deploy-content-arch-workloads.png)

## <a name="foundation-infrastructure-prerequisites"></a>Conditions préalables pour l’infrastructure de base

*Idéalement *, vous devez déployer les charges de travail et les scénarios après avoir configuré toutes les phases de l’[infrastructure de base](deploy-foundation-infrastructure.md). Cela garantit que toutes les couches sous-jacentes sont en place pour offrir une intégration, une sécurité et une expérience optimale à vos utilisateurs ainsi qu’à leurs appareils.

| Phase | Résultat |
|:-------|:-----|
| Réseau | Votre réseau est mis à jour vers les services de cloud computing de Microsoft 365 afin d’optimiser les performances. |
| Identité | L’identité est synchronisée et sécurisée avec une authentification forte pour les comptes d’utilisateurs et la protection des comptes d’administrateurs. |
| Windows 10 Entreprise | Vos ordinateurs exécutant Windows 7 ou Windows 8.1 peuvent bénéficier d’une mise à niveau vers Windows 10 Entreprise, et les nouveaux appareils sont installés avec Windows 10 Entreprise. |
| Office 365 ProPlus | Vos utilisateurs existants de Microsoft Office peuvent bénéficier d’une mise à niveau vers Office 365 ProPlus. |
| Gestion des appareils mobiles | Vos appareils peuvent être inscrit et gérés. |
| Protection des informations | Les fonctionnalités de sécurité d’Office 365 sont activées et votre niveau de confidentialité ou les étiquettes d’Azure Information Protection sont prêts à protéger les documents. |

N’oubliez pas qu’il s’agit d’un scénario idéal et que la planification, la configuration, les tests et l’implémentation de pilote peuvent prendre du temps, en particulier au sein de grandes organisations dotées d’une infrastructure existante et de plusieurs sites. La mise en place de toutes ces couches dans tous les sites n’est pas indispensable pour bénéficier plus rapidement de la valeur métier de Microsoft 365 Entreprise. 

Voici des charges de travail courantes à déployer immédiatement : 

- Une fois la couche **Identité** de l’infrastructure de base déployée vers les utilisateurs, de nombreuses organisations effectuent les déploiements suivants :
  - [Office 365 ProPlus](office365proplus-infrastructure.md) combiné avec [OneDrive Entreprise](https://docs.microsoft.com/onedrive/plan-onedrive-enterprise). Office 365 ProPlus apporte la sécurité de l’authentification moderne et l’expérience utilisateur du dernier client Microsoft Office. La migration des fichiers personnels de l’utilisateur vers OneDrive Entreprise réduit l’infrastructure et la nécessité de prendre en charge des dossiers et lecteurs locaux.
  - [Exchange Online](exchangeonline-workload.md) pour permettre aux utilisateurs de commencer à utiliser le courrier basé sur le cloud.
- Si vous n’avez pas immédiatement besoin de stocker des biens numériques hautement réglementés dans le cloud, déployez [Microsoft Teams](teams-workload.md) et [SharePoint Online](sharepoint-online-onedrive-workload.md) pour vos utilisateurs avant la couche **Protection des informations**.

Vous devez décider de la meilleure façon de commander et déployer la configuration des phases préalables de l’infrastructure de base pour répondre au mieux à vos besoins métier.

### <a name="best-practice"></a>Meilleures pratiques

Nous vous recommandons vivement d’opérer le déploiement de la phase **Identité** de l’infrastructure de base avant d’intégrer vos utilisateurs à des charges de travail ou scénarios.

La phase **Identité** garantit que votre identité basée sur le cloud, qu’elle soit uniquement cloud ou synchronisée avec vos Active Directory Domain Services (AD DS) locaux, contient les comptes et groupes d’utilisateurs et d’ordinateurs permettant de gérer l’authentification et l’accès. Une authentification forte pour tous vos utilisateurs ainsi qu’une protection forte des comptes d’administrateurs sont requises avant de placer des biens numériques de votre organisation dans le cloud Microsoft 365.

Bien que fondamentale et essentielle pour les performances globales, la phase **Mise en réseau** sur votre réseau peut être en cours lorsque vous intégrez vos utilisateurs à des charges de travail, sachant que les performances des applications et services Microsoft 365 s’amélioreront au fil du temps.

Cela vaut en particulier pour les organisations disposant de plusieurs sites et d’une grande diversité d’appareils périphériques et de connexions Internet.
