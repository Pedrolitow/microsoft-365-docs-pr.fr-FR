---
title: Configurer des équipes avec la protection des données hautement sensibles
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkSPO
recommendations: false
description: Découvrez comment déployer des équipes avec la protection des données hautement sensibles.
ms.openlocfilehash: 053f92f0a3f7551d747c81b13b3832798c7e953c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312595"
---
# <a name="configure-teams-with-protection-for-highly-sensitive-data"></a>Configurer des équipes avec la protection des données hautement sensibles

Dans cet article, nous étudions la configuration d’une équipe pour un niveau de protection hautement sensible. Assurez-vous d’avoir effectué les étapes décrites dans [Déployer des équipes avec une protection de base de référence](configure-teams-baseline-protection.md) avant de suivre les étapes décrites dans cet article.

Pour ce niveau de protection, nous créons une étiquette de confidentialité qui peut être utilisée dans votre organisation pour des équipes et des fichiers hautement sensibles. Seuls les membres de votre organisation et les invités que vous spécifiez peuvent déchiffrer les fichiers utilisant cette étiquette. Si vous avez besoin d’isoler davantage les autorisations pour que seuls les membres d’une équipe spécifique puissent déchiffrer des fichiers, voir [Déployer une équipe avec isolation des problèmes de sécurité](secure-teams-security-isolation.md).

Le niveau hautement sensible offre les protections supplémentaires suivantes sur le niveau de référence :

- Une étiquette de sensibilité pour l'équipe qui vous permet d'activer ou de désactiver le partage avec les invités et de bloquer l'accès au contenu SharePoint pour les appareils non gérés. Ce label peut également être utilisé pour classer et crypter les fichiers.
- Type de lien de partage par défaut plus restrictif
- Seuls les propriétaires d’équipe peuvent créer des canaux privés.
- Les demandes d’accès au site SharePoint associé sont désactivées.

## <a name="video-demonstration"></a>Démonstration vidéo

Regardez cette vidéo pour une explication pas à pas des procédures décrites dans cet article.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NzI7]

## <a name="guest-sharing"></a>Partage d’invités

Selon la nature de votre entreprise, il est possible que vous souhaitiez ou non activer le partage d’invités pour les équipes qui contiennent des données hautement sensibles. Si vous envisagez de collaborer avec des personnes extérieures à votre organisation, nous vous recommandons d’activer le partage d’invités. Microsoft 365 inclut de nombreuses fonctionnalités de sécurité et conformité qui vous permettent de partager du contenu sensible de façon sécurisée. Il s’agit généralement d’une option plus sécurisée que la messagerie électronique de contenu directement pour les personnes extérieures à votre organisation.

Pour plus d’informations sur le partage sécurisé avec des invités, consultez les ressources suivantes :

- [Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation](./share-limit-accidental-exposure.md)
- [Créer un environnement de partage sécurisé avec des invités](./create-secure-guest-sharing-environment.md)

Pour autoriser ou bloquer le partage d’invités, nous utilisons une combinaison d’une étiquette de confidentialité pour les contrôles de partage au niveau du site et des équipes pour le site SharePoint associé, les deux décrites ultérieurement.

## <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Pour le niveau de protection hautement sensible, nous allons utiliser une étiquette de confidentialité pour classer l’équipe. Cette étiquette peut également être utilisée pour classifier et chiffrer des fichiers individuels dans cette équipe ou d’autres, ou dans d’autres emplacements de fichier tels que SharePoint ou OneDrive. 

Pour commencer, vous devez activer les étiquettes de confidentialité pour Teams. Pour plus d’informations, consultez [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les groupes Office 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

Si vous avez déjà déployé des étiquettes de confidentialité au sein de votre organisation, réfléchissez à la façon dont cette étiquette correspond à votre stratégie d’étiquette globale. Vous pouvez modifier le nom ou les paramètres si nécessaire pour répondre aux besoins de votre organisation.

Une fois que vous avez activé les étiquettes de confidentialité pour Teams, l’étape suivante consiste à créer l’étiquette.

Pour créer une étiquette de confidentialité
1. Ouvrez [Centre de conformité Microsoft 365](https://compliance.microsoft.com).
2. Sous **Solutions**, cliquez sur **Protection des informations**.
3. Cliquez sur **Créer une étiquette**.
4. Donnez un nom à l’étiquette. Nous vous suggérons le terme **Hautement sensible**, mais vous pouvez choisir un autre nom si celui-ci est déjà utilisé.
5. Tapez un nom et une description, puis cliquez sur **Suivant**.
6. Dans la page **Définir l’étendue de cette page d’étiquettes**, sélectionnez **Fichiers et courriers électroniques** et **Groupes et sites**, puis cliquez sur **Suivant**.
7. Sur la page **Choisir les paramètres de protection pour les fichiers et les e-mails**, sélectionnez **Chiffrer les fichiers et les e-mails**, puis cliquez sur **Suivant**.
8. Sur la page **Chiffrement**, sélectionnez **Configurer les paramètres de chiffrement**.
9. Sous **Attribuer des autorisations à des utilisateurs et à des groupes spécifiques**, cliquez sur **Attribuer des autorisations**.
10. Cliquez sur **Ajouter tous les utilisateurs et les groupes de votre organisation**.
11. Si des invités doivent avoir l’autorisation de déchiffrer des fichiers, cliquez sur **Ajouter des utilisateurs ou des groupes**, puis ajoutez-les.
12.  Cliquez sur **Enregistrer**, puis sur **Suivant**.
13. Dans la page *Étiquetage automatique des fichiers et messages électroniques**, cliquez sur **Suivant**.
14. Dans la page **Définir les paramètres de protection pour les groupes et sites**, sélectionnez **Paramètres de confidentialité et d’accès des utilisateurs externes**, et **Accès appareil et paramètres de partage externe**, puis cliquez sur **Suivant**.
15. Dans la page **Définir les paramètres de confidentialité et d’accès des utilisateurs externes**, sous **Confidentialité**, sélectionnez l’option **Privé** .
16. Si vous souhaitez autoriser l’accès invité, sous **Accès des utilisateurs externes**, sélectionnez **Autoriser les propriétaires de groupe Microsoft 365 à ajouter des personnes externes à votre organisation au groupe comme invités**.
17. Cliquez sur **Suivant**.
18. Dans la page **Définir les paramètres de partage externe et d’accès aux appareils**, sélectionnez **Contrôler le partage externe dans les sites étiquetés SharePoint**.
19. Sous **Le contenu peut être partagé avec**, sélectionnez **Invités nouveaux et existants** si vous autorisez l’accès invité ou **Uniquement les membres de votre organisation** si ce n’est pas le cas.
20. Sous **Accès à partir d’appareils non gérés**, choisissez **Bloquer l’accès**. (Si vous autorisez les invités et qu’ils n’ont pas d’appareils gérés, vous pouvez choisir **Autoriser l’accès limité, sites web uniquement**.)
21. Cliquez sur **Suivant**.
22. Dans la page **Étiquetage automatique pour les colonnes de base de données** , cliquez sur **Suivant**.
23. Cliquez sur **Créer une étiquette**, puis sur **Terminé**.

Une fois que vous avez créé l’étiquette, vous devez la publier aux utilisateurs qui l’utiliseront. Pour une protection sensible, nous allons mettre l’étiquette à la disposition de tous les utilisateurs. Vous publiez l’étiquette dans le Centre de conformité Microsoft 365, sur l’onglet **Stratégies d’étiquette** de la page **Protection des informations**. Si vous avez une stratégie existante qui s’applique à tous les utilisateurs, ajoutez cette étiquette à cette stratégie. Si vous avez besoin de créer une stratégie, consultez [Publier des étiquettes de confidentialité en créant une stratégie d’étiquette](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Créer une équipe

La configuration supplémentaire du scénario hautement sensible est effectuée sur le site SharePoint associé à l’équipe. L’étape suivante consiste à créer une équipe.

Pour créer une équipe pour les informations hautement sensibles
1. Dans Teams, cliquez sur **Teams** sur le côté gauche de l’application, puis cliquez sur **Rejoindre ou créer une équipe** en bas de la liste des équipes.
2. Cliquez sur **Créer une équipe** (première carte, coin supérieur gauche).
3. Sélectionnez **Créer une équipe à partir de zéro**.
4. Dans la liste **Sensibilité**, sélectionnez l’étiquette **Hautement sensible** que vous venez de créer.
5. Sous **Confidentialité**, cliquez sur **Privée**.
6. Tapez un nom pour l’équipe, puis cliquez sur **Créer**.
7. Ajoutez des utilisateurs à l’équipe, puis cliquez sur **Fermer**.

## <a name="private-channel-settings"></a>Paramètres du canal privé

À ce niveau, nous limitons la création de canaux privés aux propriétaires d'équipe.

Pour restreindre la création d’un canal privé
1. Dans l’équipe, cliquez sur **Autres options**, puis cliquez sur **Gérer l’équipe**.
2. Sous l’onglet **Paramètres**, développez **Autorisations de membre**.
3. Désactivez la case à cocher **Autoriser les membres à créer des canaux privés**.

Vous pouvez également utiliser les [stratégies d’équipes](/MicrosoftTeams/teams-policies) pour contrôler qui peut créer des canaux privés.

## <a name="sharepoint-settings"></a>Paramètres de SharePoint

Chaque fois que vous créez une équipe avec une étiquette de haute confidentialité, vous devez procéder de deux étapes dans SharePoint :

- Mettez à jour les paramètres de partage d’invités pour le site dans le Centre d’administration SharePoint, afin qu’ils mettent à jour le lien de partage par défaut vers *Personnes disposant d'un accès existant*.
- Mettez à jour les paramètres de partage du site lui-même pour empêcher les membres de partager des fichiers, des dossiers ou le site, et de désactiver les demandes d’accès.

### <a name="site-default-sharing-link-settings"></a>Paramètres de lien de partage par défaut du site

Pour mettre à jour le type de lien de partage par défaut du site

1. Ouvrez le Centre d’administration SharePoint et, sous **Sites**, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a>.
1. Sélectionnez le site associé à l’équipe.
1. Sous l’onglet **Stratégies**, sous **Partage externe**, cliquez sur **Modifier**.
1. Sous Type de lien de partage par défaut, désactivez la case à cocher **Identique au paramètre de niveau organisation**, puis sélectionnez **Personnes disposant d’un accès existant**.
1. Sélectionnez **Enregistrer**.

#### <a name="private-channels"></a>Canaux privés

Si vous ajoutez des canaux privés à l’équipe, chaque canal privé crée un site SharePoint avec les paramètres de partage par défaut. Ces sites ne sont pas visibles dans le Centre d’administration SharePoint. vous devez donc utiliser l’applet de commande PowerShell SPOSite pour mettre à jour les paramètres de partage d’invités.

### <a name="site-sharing-settings"></a>Paramètres de partage de site

Pour vous assurer que le site SharePoint ne soit pas partagé avec des personnes qui ne sont pas membres de l’équipe, nous limitons ce partage aux propriétaires. Nous limitons également le partage des fichiers et dossiers aux propriétaires d’équipe. Cela permet de s’assurer que les propriétaires sont conscients de l’existence d’un fichier partagé avec une personne extérieure à l’équipe.

Pour configurer le partage de sites propriétaires uniquement
1. Dans Teams, accédez à l’onglet **Général** de l’équipe que vous voulez mettre à jour.
2. Dans la barre d’outils de l’équipe, cliquez sur **Fichiers**.
3. Cliquez sur les points de suspension, puis sur **Ouvrir dans SharePoint**.
4. Dans la barre d’outils du site SharePoint sous-jacent, cliquez sur l’icône Paramètres, puis cliquez sur **Autorisations du site**.
5. Dans le volet **Autorisations de site**, sous **Partage de site**, cliquez sur **Modifier les modalités de partage par les membres**.
6. Sous **Autorisations de partage**, sélectionnez **Seuls les propriétaires du site peuvent partager des fichiers, des dossiers et le site**.
7. Définissez **Autoriser les demandes d’accès** sur **Activé**, puis cliquez sur **Enregistrer**.

## <a name="see-also"></a>Voir aussi

[Créer et configurer des étiquettes de confidentialité ainsi que leurs stratégies](../compliance/create-sensitivity-labels.md)
