---
title: Préparer votre organisation pour Windows 10 Entreprise
description: Fournit un guide de haut niveau sur les étapes à suivre pour déployer Windows 10 Entreprise sur les ordinateurs dans le cadre de Microsoft 365 Entreprise.
keywords: Microsoft 365, Microsoft 365 Entreprise, documentation Microsoft 365, Windows 10 Entreprise, déploiement
author: JoeDavies-MSFT
localization_priority: Normal
audience: microsoft-business
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 06/01/2018
ms.author: josephd
ms.openlocfilehash: 21a4198c688e1865a029f18ff3ceeb2155d419e4
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867373"
---
# <a name="step-1-prepare-your-organization-for-windows-10-enterprise"></a>Étape 1 : Préparer votre organisation pour Windows 10 Entreprise

*Cet article s'applique à la fois aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/win10enterprise_icon-small.png)

Avant de mettre à niveau vos appareils vers Windows 10 Entreprise, tenez compte des éléments suivants :

- **Vos domaines doivent être ajoutés et vérifiés** <br>Avec un abonnement Microsoft 365, vous obtenez un nom de domaine par défaut qui se termine par onmicrosoft.com (par exemple, contoso.onmicrosoft.com). La plupart des organisations préfèrent utiliser un ou plusieurs domaines qui leur appartiennent afin que leur adresse de courrier se termine par leur propre nom de domaine (par exemple, username@contoso.com). Pour utiliser votre propre domaine, vous devez l’ajouter à Microsoft 365 et vérifier que vous en êtes propriétaire. Nous vous recommandons d’ajouter et vérifier vos domaines maintenant pour qu’ils soient prêts dès la configuration des services Microsoft 365, tels que la messagerie et Skype Entreprise.
- **Vous n’avez pas besoin d’ajouter d’utilisateurs pour le moment** <br>Pour utiliser les services Microsoft 365 ou installer les produits Microsoft 365, les utilisateurs ont besoin de comptes dans Microsoft 365 et ils ont besoin de licences de produit. La manière dont vous ajoutez des utilisateurs à Microsoft 365 dépend du nombre d'utilisateurs et si vous disposez actuellement d'Active Directory sur site. Si vous n'avez pas Active Directory (ou si vous avez Active Directory mais que vous ne souhaitez pas le synchroniser avec Microsoft 365), vous pouvez ajouter des utilisateurs directement à Microsoft 365 et attribuer des licences, individuellement ou en bloc.
  <br> Si vous avez Active Directory en local, vous pouvez le [synchroniser avec Microsoft 365](identity-azure-ad-connect-health.md) pour créer des comptes d’utilisateurs dans Azure AD, l’annuaire de cloud utilisé par Microsoft 365. Avec cette méthode, vous pouvez créer des comptes pour les utilisateurs et pour les groupes de sécurité que vous utilisez pour gérer les autorisations sur les ressources (comme les collections de sites ou les documents SharePoint Online). La synchronisation de votre Active Directory avec Microsoft 365 n'attribuera pas de licences aux utilisateurs.
- **Vous n’avez pas besoin d’attribuer de licence aux utilisateurs pour le moment** <br> Avant que les utilisateurs ne puissent utiliser les services Microsoft 365 ou installer un logiciel à partir du portail Microsoft 365, ils ont besoin des licences des produits. En tant qu'administrateur de gestion globale ou utilisateur, vous pouvez attribuer directement des licences de produits dans Microsoft 365, individuellement ou en bloc. Vous pouvez également utiliser des [licences basées sur des groupes](identity-group-based-licensing.md) pour attribuer automatiquement des licences lorsque des utilisateurs sont ajoutés à un groupe particulier. 
- **Installer Office 365 ProPlus séparément** <br>L’obtention d’une licence Microsoft 365 n’installe pas automatiquement Office 365 ProPlus sur vos ordinateurs clients. Voir [Phase 4 : Office 365 ProPlus](office365proplus-infrastructure.md) pour plus d’informations. 

## <a name="set-windows-diagnostics-data-level"></a>Choisissez diagnostics Windows

Microsoft utilise les données de diagnostics pour maintenir les appareil Windows sécurisés en identifiant les tendances de programmes malveillants et d’autres menaces et nous aider à améliorer la qualité de Windows et des services Windows. Vous devez vous assurer que le service client diagnostics est activé à un niveau minimum de base sur les points de terminaison de votre organisation. *Par défaut, ce service est activé et configuré sur le niveau Amélioré. * Toutefois, il est recommandé de vérifier et de vous assurer qu’ils reçoivent les données de détection. La définition des niveaux via des stratégies remplace les paramètres au niveau des appareils. 

**Niveaux de données de diagnostic de système d’exploitation Windows 10**

Vous pouvez configurer vos paramètres de données de diagnostic de système d’exploitation en utilisant les outils de gestion que vous utilisez déjà, telles que la stratégie de groupe, Mobile Device Manager ou la mise en service Windows. Vous pouvez également modifier manuellement vos paramètres à l’aide de l’Éditeur du Registre. Définition des niveaux de vos données de diagnostic via une stratégie de gestion remplace les paramètres au niveau du périphérique.

Utilisez la valeur appropriée dans le tableau ci-dessous lorsque vous configurez la stratégie de gestion.

| Niveau | Données collectées | Valeur |
|:--- |:--- |:--- |
| Sécurité | Données de sécurité uniquement. | 0 |
| De base | Données de sécurité et données système de base et de qualité. | 1  |
| Améliorée. | Des données de sécurité, des données système de base et de qualité, des perspectives améliorées et des données de fiabilité avancées. | 2  |
| Complet | Des données de sécurité, des données système de base et de qualité, des perspectives améliorées et des données de fiabilité avancées et des données de diagnostics complètes. | 3  |

Vous pouvez activer les diagnostics de données via une de ces méthodes :

* 
  **Microsoft Intune** - si vous envisagez d’utiliser Intune pour gérer vos appareils, vous pouvez créer une stratégie de configuration pour activer les données de diagnostics en configurant la stratégie système<a href="https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry" target="blank">SystemAllowTelemetry</a>. Pour plus d’informations sur la configuration des stratégies de configuration, voir [gérer les paramètres et fonctionnalités sur vos appareils avec Microsoft Intune stratégies](https://aka.ms/intuneconfigpolicies).
* **L’Éditeur du Registre** - vous pouvez utiliser l’Éditeur du Registre pour activer manuellement les données de diagnostic sur chaque appareil de votre organisation. Vous pouvez également écrire un script pour modifier le Registre. Si une stratégie de gestion existe déjà, telles que la stratégie de groupe ou la gestion des périphériques, elle remplace ce paramètre du Registre.
* La **Stratégie de groupe** - si vous n’envisagez pas d’inscrire des périphériques dans Intune, vous pouvez utiliser un objet de stratégie de groupe pour définir le niveau de données de diagnostic de votre organisation.
* **Invite de commandes** - vous pouvez définir des données de diagnostics et des services Windows 10 pour démarrer automatiquement avec l’invite de commande. Cette méthode est préférable si vous testez le service sur plusieurs appareils uniquement. L’activation du service pour un démarrage automatique avec cette commande ne configure pas le niveau de données de diagnostic. Si vous n’avez pas configuré un niveau de diagnostic de données à l’aide des outils de gestion, le service sera accessible avec la valeur par défaut Enhanced.

Voir [Configurer les données de Diagnostics Windows de votre organisation](https://docs.microsoft.com/windows/configuration/configure-windows-diagnostic-data-in-your-organization) pour en savoir plus sur les données de diagnostic de Windows et comment les activer selon la méthode choisie.

Comme point de contrôle intermédiaire, consultez les [critères de sortie](windows10-exit-criteria.md#crit-windows10-step1) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step2.png)| [Déployer Windows 10 Entreprise pour les appareils existants en tant que mise à niveau inaltérable](windows10-deploy-inplaceupgrade.md) |






