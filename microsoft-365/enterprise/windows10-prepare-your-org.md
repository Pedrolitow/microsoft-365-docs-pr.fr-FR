---
title: Préparer votre organisation pour Windows 10 Entreprise
description: Fournit un guide de haut niveau sur les étapes à suivre pour déployer Windows 10 Entreprise sur les ordinateurs dans le cadre de Microsoft 365 Entreprise.
keywords: Microsoft 365, Microsoft 365 Entreprise, documentation Microsoft 365, Windows 10 Entreprise, déploiement
author: JoeDavies-MSFT
localization_priority: Normal
ms.collection: M365-modern-desktop
audience: microsoft-business
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 06/01/2018
f1.keywords:
- NOCSH
ms.author: josephd
ms.openlocfilehash: 69ff4846e3daeef39310aa63961e0b3f5ccb9875
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41596591"
---
# <a name="step-1-prepare-your-organization-for-windows-10-enterprise"></a>Étape 1 : Préparer votre organisation pour Windows 10 Entreprise

*Cet article s'applique à la fois aux versions E3 et E5 de Microsoft 365 Entreprise*

![Phase 3 : Windows 10 Entreprise](./media/deploy-foundation-infrastructure/win10enterprise_icon-small.png)

Avant de mettre à niveau vos appareils vers Windows 10 Entreprise, tenez compte des éléments suivants :

- **Vos domaines doivent être ajoutés et vérifiés** <br>Avec un abonnement Microsoft 365, vous obtenez un nom de domaine par défaut qui se termine par onmicrosoft.com (par exemple, contoso.onmicrosoft.com). La plupart des organisations préfèrent utiliser un ou plusieurs domaines qui leur appartiennent afin que leur adresse de courrier se termine par leur propre nom de domaine (par exemple, username@contoso.com). Pour utiliser votre propre domaine, vous devez l’ajouter à Microsoft 365 et vérifier que vous en êtes propriétaire. Nous vous recommandons d’ajouter et vérifier vos domaines maintenant pour qu’ils soient prêts dès la configuration des services Microsoft 365, tels que la messagerie et Skype Entreprise.
- **Vous n’avez pas besoin d’ajouter d’utilisateurs pour le moment** <br>Pour utiliser les services Microsoft 365 ou installer les produits Microsoft 365, les utilisateurs ont besoin de comptes dans Microsoft 365 et ils ont besoin de licences de produit. La manière dont vous ajoutez des utilisateurs à Microsoft 365 dépend du nombre d'utilisateurs et si vous disposez actuellement d'Active Directory sur site. Si vous n'avez pas Active Directory (ou si vous avez Active Directory mais que vous ne souhaitez pas le synchroniser avec Microsoft 365), vous pouvez ajouter des utilisateurs directement à Microsoft 365 et attribuer des licences, individuellement ou en bloc.
  <br> Si vous avez Active Directory en local, vous pouvez le [synchroniser avec Microsoft 365](identity-add-user-accounts.md#identity-sync) pour créer des comptes d’utilisateurs dans Azure AD, l’annuaire de cloud utilisé par Microsoft 365. Avec cette méthode, vous pouvez créer des comptes pour les utilisateurs et pour les groupes de sécurité que vous utilisez pour gérer les autorisations sur les ressources (comme les collections de sites ou les documents SharePoint Online). La synchronisation de votre Active Directory avec Microsoft 365 n'attribuera pas de licences aux utilisateurs.
- **Vous n’avez pas besoin d’attribuer de licence aux utilisateurs pour le moment** <br> Avant que les utilisateurs ne puissent utiliser les services Microsoft 365 ou installer un logiciel à partir du portail Microsoft 365, ils ont besoin des licences des produits. En tant qu'administrateur de gestion globale ou utilisateur, vous pouvez attribuer directement des licences de produits dans Microsoft 365, individuellement ou en bloc. Vous pouvez également utiliser des [licences basées sur des groupes](identity-use-group-management.md#identity-group-license) pour attribuer automatiquement des licences lorsque des utilisateurs sont ajoutés à un groupe particulier. 
- **Installer Office 365 ProPlus séparément** <br>L’obtention d’une licence Microsoft 365 n’installe pas automatiquement Office 365 ProPlus sur vos ordinateurs clients. Voir [Phase 4 : Office 365 ProPlus](office365proplus-infrastructure.md) pour plus d’informations. 

## <a name="set-windows-diagnostics-data-level"></a>Définir le niveau de données de diagnostic Windows

Microsoft utilise des données de diagnostic pour garantir la sécurité des appareils Windows en identifiant les tendances des programmes malveillants et d’autres menaces et pour nous aider à améliorer la qualité des services Windows et Microsoft. Vous devez vous assurer que le service de diagnostic est activé à un niveau minimal de base sur tous les points de terminaison de votre organisation. *Par défaut, ce service est activé et défini sur le niveau étendu.* Toutefois, il est recommandé de vérifier et de s’assurer qu’ils reçoivent des données de capteur. La définition des niveaux par le biais de stratégies remplace les paramètres au niveau du périphérique. 

**Niveaux de données de diagnostic du système d’exploitation Windows 10**

Vous pouvez configurer les paramètres des données de diagnostic de votre système d’exploitation à l’aide des outils de gestion que vous utilisez, tels que la stratégie de groupe, MDM ou Windows Provisioning. Vous pouvez également modifier manuellement vos paramètres à l’aide de l’éditeur du Registre. La définition de vos niveaux de données de diagnostic par le biais d’une stratégie de gestion remplace tous les paramètres de niveau périphérique.

Utilisez la valeur appropriée dans le tableau ci-dessous lorsque vous configurez la stratégie de gestion.

| Niveau | Données collectées | Valeur |
|:--- |:--- |:--- |
| Sécurité | Données de sécurité uniquement. | 0 |
| De base | Données de sécurité, système de base et données de qualité. | 1  |
| Avancée | Données de sécurité, système de base et données de qualité, ainsi que des informations améliorées et des données de fiabilité avancées. | 2  |
| Complet | Données de sécurité, système de base et données de qualité, informations améliorées et données de fiabilité avancées et données de diagnostics complètes. | 3  |

Vous pouvez activer les données de diagnostic à l’aide de l’une des méthodes suivantes :

* **Microsoft Intune** : Si vous envisagez d’utiliser Intune pour gérer vos appareils, vous pouvez créer une stratégie de configuration pour activer les données de diagnostic en configurant la stratégie système <a href="https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry" target="blank">SystemAllowTelemetry</a> . Pour plus d’informations sur la configuration des stratégies de configuration, voir [gérer les paramètres et les fonctionnalités sur vos appareils avec les stratégies Microsoft Intune](https://aka.ms/intuneconfigpolicies).
* **Éditeur du Registre** : vous pouvez utiliser l’éditeur du Registre pour activer manuellement les données de diagnostic sur chaque appareil de votre organisation. Vous pouvez également écrire un script pour modifier le registre. Si une stratégie de gestion existe déjà, comme la stratégie de groupe ou MDM, elle remplacera ce paramètre de registre.
* **Stratégie de groupe** : Si vous n’envisagez pas d’inscrire des appareils dans Intune, vous pouvez utiliser un objet de stratégie de groupe pour définir le niveau de données de diagnostic de votre organisation.
* **Invite de commandes** : vous pouvez définir les données et le service de diagnostic Windows 10 pour qu’ils démarrent automatiquement avec l’invite de commandes. Cette méthode est recommandée si vous testez le service sur seulement quelques appareils. L’activation du démarrage automatique du service avec cette commande ne permet pas de configurer le niveau de données de diagnostic. Si vous n’avez pas configuré de niveau de données de diagnostic à l’aide des outils de gestion, le service fonctionnera avec le niveau avancé par défaut.

Voir [configurer les données de diagnostic Windows dans votre organisation](https://docs.microsoft.com/windows/configuration/configure-windows-diagnostic-data-in-your-organization) pour en savoir plus sur les données de diagnostic Windows et sur la façon dont vous pouvez les activer en fonction de la méthode que vous choisissez.

Comme point de contrôle intermédiaire, consultez les [critères de sortie](windows10-exit-criteria.md#crit-windows10-step1) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![Étape 2](./media/stepnumbers/Step2.png)| [Déployer Windows 10 Entreprise pour les appareils existants en tant que mise à niveau inaltérable](windows10-deploy-inplaceupgrade.md) |






