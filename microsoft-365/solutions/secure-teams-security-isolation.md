---
title: Configurer une équipe avec l’isolation de sécurité à l’aide d’une étiquette de confidentialité unique
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkCOMPLIANCE
- admindeeplinkSPO
recommendations: false
description: Découvrez comment créer une équipe avec une étiquette de confidentialité unique pour la sécurité.
ms.openlocfilehash: 4596f8b5612472108a68466635a975a6761bf28a
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67582513"
---
# <a name="configure-a-team-with-security-isolation-by-using-a-unique-sensitivity-label"></a>Configurer une équipe avec l’isolation de sécurité à l’aide d’une étiquette de confidentialité unique

Cet article fournit des recommandations et des étapes pour configurer une équipe privée dans Microsoft Teams et utiliser une étiquette de confidentialité unique pour chiffrer les fichiers de sorte que seuls les membres d’une équipe puissent les déchiffrer.

Au-delà de l’accès privé, cet article décrit comment configurer le site SharePoint associé, auquel vous pouvez accéder à partir de la section **Fichiers** d’un canal d’équipe, afin de renforcer la sécurité nécessaire pour stocker les données hautement réglementées.

Les éléments de configuration d’une équipe avec une isolation de sécurité sont les suivants :

- Une équipe privée
- Une sécurité supplémentaire sur le site SharePoint associé pour l’équipe qui :
  - Empêche les membres du site de partager le site avec d’autres personnes.
  - Empêche les non-membres du site de demander l’accès au site.
- Un étiquette de confidentialité spécifiquement réservé à cette équipe qui :
    - Empêche l’accès au contenu SharePoint à partir d’appareils non gérés
    - Autorise ou refuse l'accès des invités à l'équipe, en fonction de vos besoins
    - Chiffre les documents auxquels l'étiquette est appliquée

> [!IMPORTANT]
> Veillez à activer [étiquettes de confidentialité pour protéger le contenu de Microsoft Teams, des groupes Office 365 et des sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md) avant de passer aux étapes décrites dans cet article.

Regardez cette vidéo de présentation du processus de déploiement.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mGHf]

<a name="poster"></a> Pour un résumé d’une page de ce scénario, consultez [Microsoft Teams avec l’isolation de sécurité](../downloads/team-security-isolation-poster.pdf).

[![Microsoft Teams avec l’isolation de sécurité.](../media/secure-teams-security-isolation/team-security-isolation-poster.png)](../downloads/team-security-isolation-poster.pdf)

Vous pouvez également télécharger cette affiche au format [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/team-security-isolation-poster.pdf) ou [PowerPoint](https://download.microsoft.com/download/8/0/5/8057fc16-c044-40b6-a652-7ed555ba2895/team-security-isolation-poster.pptx) et l’imprimer sur du papier au format lettre, légal ou tabloïd (11 x 17).

Essayez cette configuration dans votre propre environnement de laboratoire de test avec [ces instructions](team-security-isolation-dev-test.md).

Voir comment Contoso Corporation a utilisé une équipe isolée pour un projet top secret dans [cette étude de cas](contoso-team-for-top-secret-project.md).

## <a name="initial-protections"></a>Protections initiales

Pour vous aider à protéger l’accès à l’équipe et à son site SharePoint sous-jacent, consultez les pratiques recommandées suivantes :
- [Stratégies pour les accès aux identités et appareils](../security/office-365-security/identity-access-policies.md)
- [Stratégies d’accès à SharePoint Online](../security/office-365-security/sharepoint-file-access-policies.md)
- [Déployer les équipes avec la protection Base de référence](configure-teams-baseline-protection.md)

## <a name="guest-sharing"></a>Partage d’invités

Selon la nature de votre entreprise, il est possible que vous souhaitiez ou non activer le partage d’invités pour cette équipe. Si vous envisagez de collaborer avec des personnes extérieures à votre organisation, activez le partage d’invités. 

Pour plus d’informations sur le partage sécurisé avec des invités, consultez les ressources suivantes :

- [Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation](./share-limit-accidental-exposure.md)
- [Créer un environnement de partage sécurisé avec des invités](./create-secure-guest-sharing-environment.md)

Pour autoriser ou bloquer le partage d’invités, nous utilisons une combinaison d’une étiquette de confidentialité pour les contrôles de partage au niveau du site et des équipes pour le site SharePoint associé, les deux décrites ultérieurement.

## <a name="create-a-private-team"></a>Création d’une équipe privée

Étant donné que nous créons une étiquette de confidentialité spécifiquement pour cette équipe, l’étape suivante consiste à créer l’équipe. Si vous avez une équipe existante, vous pouvez l’utiliser.

Pour créer une équipe pour les informations sensibles
1. Dans Teams, cliquez sur **Teams** sur le côté gauche de l’application, puis cliquez sur **Rejoindre ou créer une équipe** en bas de la liste des équipes.
2. Cliquez sur **Créer une équipe** (première carte, coin supérieur gauche).
3. Sélectionnez **Créer une équipe à partir de zéro**.
4. Dans la liste **Sensibilité**, conservez la valeur par défaut.
5. Sous **Confidentialité**, cliquez sur **Privée**.
6. Tapez un nom pour l'équipe qui est lié à votre projet sensible. Par exemple, **Projet Saturne**.
7. Cliquez sur **Créer**.
8. Ajoutez des utilisateurs à l’équipe, puis cliquez sur **Fermer**.

## <a name="private-channel-settings"></a>Paramètres du canal privé

Nous vous recommandons de limiter la création de canaux privés aux propriétaires d’équipe.

Pour restreindre la création d’un canal privé
1. Dans l’équipe, cliquez sur **Autres options**, puis cliquez sur **Gérer l’équipe**.
2. Sous l’onglet **Paramètres**, développez **Autorisations de membre**.
3. Désactivez la case à cocher **Autoriser les membres à créer des canaux privés**.

Vous pouvez également utiliser les [stratégies d’équipes](/MicrosoftTeams/teams-policies) pour contrôler qui peut créer des canaux privés.

## <a name="create-a-sensitivity-label"></a>Créer une étiquette de confidentialité

Pour configurer une équipe pour l’isolation de la sécurité, nous allons utiliser une étiquette de confidentialité créée spécifiquement pour cette équipe. Cette étiquette est utilisée au niveau de l’équipe pour contrôler le partage d’invités et bloquer l’accès à partir d’appareils non gérés. Elle permet également de classifier et de chiffrer des fichiers individuels au sein de l’équipe de sorte que seuls les propriétaires d’équipe et les membres puissent les ouvrir.

Si vous avez un partenaire interne ou un groupe des parties prenantes devant pouvoir afficher les documents chiffrés, mais pas les modifier, vous pouvez les ajouter à l’étiquette avec les autorisations d’affichage seul. Vous pouvez ensuite ajouter ces personnes au site SharePoint de l’équipe avec des autorisations de lecture, et accéder en lecture seule au site où sont conservées les documents, mais pas à l’équipe elle-même.

Pour créer une étiquette de confidentialité

1. Ouvrez le portail de conformité Microsoft Purview, puis sous **Solutions**, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Protection des données**</a>.
1. Cliquez sur **Créer une étiquette**.
1. Entrez un nom pour l’étiquette. Nous vous suggérons de donner le même nom que l’équipe avec qui vous allez l’utiliser.
1. Tapez un nom et une description, puis cliquez sur **Suivant**.
1. Dans la page **Définir l’étendue de cette page d’étiquettes**, sélectionnez **Fichiers et courriers électroniques** et **Groupes et sites**, puis cliquez sur **Suivant**.
1. Sur la page **Choisir les paramètres de protection pour les fichiers et les e-mails**, sélectionnez **Chiffrer les fichiers et les e-mails**, puis cliquez sur **Suivant**.
1. Sur la page **Chiffrement**, sélectionnez **Configurer les paramètres de chiffrement**.
1. Cliquez sur **Ajouter des utilisateurs ou des groupes**, sélectionnez l’équipe que vous avez créée, puis cliquez sur **Ajouter**
1. Cliquez sur **Choisir les autorisations**.
1. Sélectionnez **Co-auteur** dans la liste déroulante, puis cliquez sur **Enregistrer**.
1. Si vous voulez inclure des utilisateurs ou des groupes qui ont accès en lecture seule aux fichiers avec l’étiquette :
    1. Cliquez sur **Attribuer des autorisations**.
    1. Cliquez sur **Ajouter des utilisateurs ou des groupes**, sélectionnez les utilisateurs ou les groupes que vous voulez ajouter, puis cliquez sur **Ajouter**.
    1. Cliquez sur **Choisir les autorisations**.
    1. Sélectionnez **Visionneuse** dans la liste déroulante, puis cliquez sur **Enregistrer**.
13.  Cliquez sur **Enregistrer**, puis sur **Suivant**.
14. Dans la page *Étiquetage automatique des fichiers et messages électroniques**, cliquez sur **Suivant**.
15. Dans la page **Définir les paramètres de protection pour les groupes et sites**, sélectionnez **Paramètres de confidentialité et d’accès des utilisateurs externes**, et **Accès appareil et paramètres de partage externe**, puis cliquez sur **Suivant**.
16. Dans la page **Définir les paramètres de confidentialité et d’accès des utilisateurs externes**, sous **Confidentialité**, sélectionnez l’option **Privé** .
17. Si vous souhaitez autoriser l’accès invité, sous **Accès des utilisateurs externes**, sélectionnez **Autoriser les propriétaires de groupe Microsoft 365 à ajouter des personnes externes à votre organisation au groupe comme invités**.
18. Cliquez sur **Suivant**.
19. Dans la page **Définir les paramètres de partage externe et d’accès aux appareils**, sélectionnez **Contrôler le partage externe dans les sites étiquetés SharePoint**.
20. Sous **Le contenu peut être partagé avec**, sélectionnez **Invités nouveaux et existants** si vous autorisez l’accès invité ou **Uniquement les membres de votre organisation** si ce n’est pas le cas.
21. Sous **Accès à partir d’appareils non gérés**, sélectionnez **Bloquer l’accès**.
22. Cliquez sur **Suivant**.
23. Dans la page **Étiquetage automatique pour les colonnes de base de données** , cliquez sur **Suivant**.
24. Cliquez sur **Créer une étiquette**, puis sur **Terminé**.

Une fois que vous avez créé l’étiquette, vous devez la publier aux utilisateurs qui l’utiliseront. Dans ce cas, l’étiquette est disponible uniquement pour les membres de l’équipe.

Pour publier une étiquette de niveau de sensibilité :

1. Dans le portail de conformité Microsoft Purview, sur la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Protection des données**</a>, choisissez l’onglet **Stratégies d’étiquette**.
2. Cliquez sur **Publier des étiquettes**.
3. Dans la page **Choisir des étiquettes de confidentialité à publier**, cliquez sur **Choisir des étiquettes de confidentialité à publier**.
4. Sélectionnez l’étiquette que vous avez créée, puis cliquez sur **Ajouter**.
5. Cliquez sur **Suivant**.
6. Dans la page Publier pour les utilisateurs et groupes, cliquez sur **Sélectionnez Utilisateurs et groupes**.
7. Cliquez sur **Ajouter**, puis sélectionnez l’équipe que vous avez créée.
8. Cliquez sur **Ajouter**, puis sur **Terminé**.
9. Cliquez sur **Suivant**.
10. Dans la page Paramètres de stratégie, activez la case à cocher **Les utilisateurs doivent fournir une justification pour supprimer une étiquette ou une étiquette de classification inférieure**, puis cliquez sur **Suivant**.
11. Tapez un nom pour la stratégie, puis cliquez sur **Suivant**.
12. Cliquez sur **Envoyer**, puis sur **Terminé**.

## <a name="apply-the-label-to-the-team"></a>Appliquer l’étiquette à l’équipe

Une fois l’étiquette publiée, vous devez l’appliquer à l’équipe pour que les paramètres de partage et d’appareils gérés soient pris en compte. Pour ce faire, dans le Centre d’administration SharePoint. Notez que l'étiquette peut prendre un certain temps avant de devenir disponible une fois qu'elle a été publiée.

Pour appliquer l’étiquette de confidentialité, procédez comme suit :

1. Ouvrez le Centre d’administration SharePoint et, sous **Sites**, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a>.
1. Sélectionnez le site associé à l’équipe.
1. Sous l’onglet **Stratégies**, sous **Confidentialité**, cliquez sur **Modifier**.
1. Sélectionnez l’étiquette que vous avez créée, puis cliquez sur **Enregistrer**.

## <a name="sharepoint-settings"></a>Paramètres de SharePoint

Il y a trois étapes à effectuer dans SharePoint :

- Mettez à jour les paramètres de partage d’invités pour le site dans le Centre d’administration SharePoint, afin qu’ils correspondent à ce que vous avez choisi lors de la création de l’étiquette, puis mettez à jour le lien de partage par défaut vers *Personnes disposant d'un accès existant*.
- Mettez à jour les paramètres de partage du site lui-même pour empêcher les membres de partager des fichiers, des dossiers ou le site, et de désactiver les demandes d’accès.
- Si vous avez ajouté des personnes ou des groupes à l’étiquette avec les autorisations Visionneuse, vous pouvez les ajouter au site SharePoint avec des autorisations de lecture.

### <a name="sharepoint-guest-settings"></a>Paramètres d’invités SharePoint

Le paramètre de partage d’invités que vous avez choisi lors de la création de l’étiquette (qui affecte uniquement l’appartenance à l’équipe) doit correspondre aux paramètres de partage d’invités pour le site SharePoint associé, comme suit :

|Paramètre d’étiquette|Paramètre du site SharePoint|
|:------------|:----------------------|
|**Permettre aux propriétaires du groupe Office 365 d’ajouter au groupe des personnes en dehors de l’organisation** sélectionné.|**Invités nouveaux et existants** (par défaut pour les nouvelles équipes)|
|**Permettre aux propriétaires du groupe Office 365 d’ajouter au groupe des personnes en dehors de l’organisation** non sélectionné.|**Uniquement les personnes de votre organisation**|

Nous mettrons également à jour le type de lien de partage par défaut pour réduire le risque de partager accidentellement des fichiers et des dossiers avec un public plus large que prévu.

Pour mettre à jour les paramètres du site

1. Ouvrez le Centre d’administration SharePoint et, sous **Sites**, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a>
1. Sélectionnez le site associé à l’équipe.
1. Sous l’onglet **Stratégies**, sous **Partage externe**, cliquez sur **Modifier**.
1. Si vous avez autorisé le partage d’invités lorsque vous avez créé l’étiquette de confidentialité, assurez-vous de sélectionner **Invités nouveaux et existants**. Si vous n’avez pas autorisé le partage lors de la création de l’étiquette, sélectionnez **Uniquement les membres de votre organisation**.
1. Sous Type de lien de partage par défaut, désactivez la case à cocher **Identique au paramètre de niveau organisation**, puis sélectionnez **Personnes disposant d’un accès existant**.
1. Sélectionnez **Enregistrer**.

#### <a name="private-channels"></a>Canaux privés

Si vous ajoutez des canaux privés à l’équipe, chaque canal privé crée un site SharePoint avec les paramètres de partage par défaut. Ces sites ne sont pas visibles dans le Centre d’administration SharePoint, vous devez donc utiliser l’applet de commande PowerShell [SPOSite](/powershell/module/sharepoint-online/set-sposite) avec les paramètres suivants pour mettre à jour les paramètres de partage d’invités :

- `-SharingCapability Disabled` pour désactiver le partage d’invités (activé par défaut)
- `-DefaultSharingLinkType Internal` pour modifier le lien de partage par défaut en *Personnes spécifiques*

Si vous n’envisagez pas d’utiliser des canaux privés avec votre équipe, songez à désactiver la possibilité pour les membres de l’équipe de les créer sous **Autorisations des membres** dans [Paramètres de l’équipe](https://support.microsoft.com/office/ce053b04-1b8e-4796-baa8-90dc427b3acc).

### <a name="site-sharing-settings"></a>Paramètres de partage de site

Pour vous assurer que le site SharePoint ne soit pas partagé avec des personnes qui ne sont pas membres de l’équipe, nous limitons ce partage aux propriétaires. Nous limitons également le partage des fichiers et dossiers aux propriétaires d’équipe. Cela permet de s’assurer que les propriétaires sont conscients de l’existence d’un fichier partagé avec une personne extérieure à l’équipe.

Pour configurer le partage de sites propriétaires uniquement
1. Dans Teams, accédez à l’onglet **Général** de l’équipe que vous voulez mettre à jour.
2. Dans la barre d’outils de l’équipe, cliquez sur **Fichiers**.
3. Cliquez sur les points de suspension, puis sur **Ouvrir dans SharePoint**.
4. Dans la barre d’outils du site SharePoint sous-jacent, cliquez sur l’icône Paramètres, puis cliquez sur **Autorisations du site**.
5. Dans le volet Autorisations de site, sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.
6. Sous **Autorisations de partage**, sélectionnez **Seuls les propriétaires du site peuvent partager des fichiers, des dossiers et le site**, puis cliquez sur **Enregistrer**.

### <a name="custom-site-permissions"></a>Autorisations de site personnalisées

Si vous avez ajouté des personnes disposant d’autorisations d’affichage sur l’étiquette de confidentialité, vous pouvez les ajouter au site SharePoint avec l’accès en lecture afin qu'elles puissent accéder facilement aux fichiers.

Pour ajouter des utilisateurs au site, procédez comme suit :
1. Dans le site, cliquez sur l’icône des paramètres, puis cliquez sur **Autorisations du site**.
2. Cliquez sur **Inviter des personnes**, puis cliquez sur **Partager le site uniquement**.
3. Tapez les noms des utilisateurs et des groupes que vous voulez inviter.
4. Pour chaque personne ou groupe que vous ajoutez, modifiez les autorisations de **Modifier** à **Lire**.
5. Choisissez si vous voulez leur envoyer un courriel avec un lien vers le site.
6. Cliquez sur **Ajouter**.

## <a name="additional-protections"></a>Autres protections

Microsoft 365 offre d’autres méthodes pour la sécurisation de votre contenu. Envisagez d’utiliser les options suivantes pour renforcer la sécurité au sein de votre organisation.

- Demandez à vos invités d’accepter les [conditions d’utilisation](/azure/active-directory/conditional-access/terms-of-use).
- Configurez une [stratégie de délai d’expiration de session](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) pour les invités.
- Créez les [Types d’informations sensibles](../compliance/sensitive-information-type-learn-about.md) et utilisez [Protection contre la perte de données](../compliance/dlp-learn-about-dlp.md) pour définir des stratégies autour de l’accès aux informations sensibles.
- Utilisez révisions d’[Accès Azure Active Directory](/azure/active-directory/governance/access-reviews-overview) pour examiner régulièrement les membres de l’équipe.

## <a name="drive-user-adoption-for-team-members"></a>Favorisez l’adoption par les utilisateurs pour les membres de l’équipe

Une fois l’équipe en place, il est temps de stimuler l’adoption de cette équipe et de sa sécurité supplémentaire pour les membres de l’équipe.

### <a name="train-your-users"></a>Former vos utilisateurs

Les membres de l’équipe peuvent accéder à l’équipe et à toutes ses ressources, y compris aux conversations, réunions et autres applications. Lorsque vous travaillez avec des fichiers de la section **Fichiers** d’un canal, les membres de l’équipe doivent affecter l’étiquette de confidentialité aux fichiers qu’ils créent.

Lorsque l’étiquette est appliquée au fichier, celui-ci devient chiffré. Les membres de l’équipe peuvent l’ouvrir et collaborer en temps réel. Si le fichier quitte le site et est transmis à un utilisateur malveillant, celui-ci devra fournir les informations d’identification d’un compte d’utilisateur membre de l’équipe pour ouvrir le fichier et afficher son contenu. 

Formez les membres de votre équipe :

- Sur l’importance de l’utilisation de la nouvelle équipe pour les conversations, les réunions, les fichiers et les autres ressources du site SharePoint, et les conséquences d’une fuite de données hautement réglementées, telles que des conséquences juridiques, des amendes réglementaires, des rançongiciels ou la perte de l’avantage concurrentiel.
- Accès à l’équipe.
- Création de nouveaux fichiers sur le site et chargement de nouveaux fichiers stockés localement.
- Mode d’étiquetage de fichiers à l’aide de l’étiquette de confidentialité appropriée pour l’équipe.
- Comment l’étiquette protège des fichiers même lorsque ceux-ci ont été divulgués hors du site.

Cette formation doit inclure des exercices pratiques pour que les membres de votre équipe puissent se familiariser avec ces fonctionnalités et leurs résultats.

### <a name="conduct-periodic-reviews-of-usage-and-address-team-member-feedback"></a>Révisez périodiques de l’utilisation et donner suite aux commentaires des membres de l’équipe

Dans les semaines suivant la formation :

- Aborder rapidement les commentaires des membres de l’équipe et affinez les stratégies et les configurations.
- Analysez l’utilisation pour l’équipe et comparez-la avec les attentes en matière d’utilisation.
- Vérifiez que les fichiers hautement réglementés ont été correctement étiquetés avec l’étiquette de confidentialité. (Vous pouvez voir quels fichiers disposent d'une étiquette attribuée en affichant un dossier dans SharePoint Online et en ajoutant la colonne **Confidentialité** via l'option **Afficher/masquer les colonnes** de **Ajouter un colonne**.

Formez à nouveau vos utilisateurs si nécessaire.

## <a name="see-also"></a>Voir aussi

[Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure)
