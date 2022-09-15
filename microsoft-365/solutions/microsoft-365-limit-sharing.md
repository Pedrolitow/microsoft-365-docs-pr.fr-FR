---
title: Limiter le partage dans Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- highpri
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
search.appverid:
- SPO160
- MET150
f1.keywords: NOCSH
ms.custom:
- admindeeplinkMAC
- admindeeplinkTEAMS
- admindeeplinkSPO
ms.localizationpriority: high
recommendations: false
description: Découvrez les options pour limiter ou désactiver le partage dans Microsoft 365.
ms.openlocfilehash: c2d7233afadc49ea5f8e465783106b9d3f38a252
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67731031"
---
# <a name="limit-sharing-in-microsoft-365"></a>Limiter le partage dans Microsoft 365

Bien que vous ne puissiez pas désactiver le partage interne complètement ou supprimer le bouton partager des sites, vous pouvez limiter le partage dans Microsoft 365 pour répondre aux besoins de votre organisation.

Les méthodes de partage de fichiers sont répertoriées dans le tableau ci-dessous. Cliquez sur le lien dans la colonne **Méthode de partage** pour obtenir des informations détaillées.

|Méthode de partage|Description|Limiter les options|
|:-------------|:----------|:-------------|
|[Groupe ou équipe Microsoft 365](#microsoft-365-group-or-team)|Les personnes disposant d’un accès à une équipe Microsoft Teams ou à un groupe Microsoft 365 peuvent modifier les fichiers du site SharePoint associé.|Si le groupe ou l’équipe est privé, les invitations de partage à rejoindre l’équipe accèdent au propriétaire pour approbation. Les administrateurs peuvent désactiver l'accès invité ou utiliser des étiquettes de confidentialité pour empêcher l'accès par des personnes extérieures à l'organisation.|
|[Site SharePoint](#sharepoint-site)|Les utilisateurs peuvent bénéficier d'un accès Propriétaire, Membre ou Visiteur à un site SharePoint et auront ce niveau d'accès aux fichiers du site.|Les autorisations de site peuvent être limitées de sorte que seuls les propriétaires de site puissent partager le site. Les administrateurs peuvent définir un site sur le mode lecture seule ou bloquer entièrement l’accès à ce site.|
|[Partager avec des personnes spécifiques](#sharing-with-specific-people)|Les membres du site et les personnes disposant des autorisations de modification peuvent octroyer des autorisations directes aux fichiers et dossiers, ou les partager en utilisant *des personnes spécifiques* des liens.|Les autorisations de site peuvent être limitées de sorte que seuls les propriétaires de site puissent partager les fichiers et les dossiers. Dans ce cas, l’accès direct et le partage de liens *des personnes spécifiques* par les membres du site est transmis au propriétaire du site pour approbation.|
|[Partage invité SharePoint et OneDrive](#sharepoint-guest-sharing)|Les propriétaires et les membres du site SharePoint et propriétaires de OneDrive peuvent partager des fichiers et des dossiers avec des personnes extérieures à l’organisation.|Le partage d’invités peut être désactivé pour l’ensemble de l’organisation ou des sites individuels.|
|[*Membres de votre organisation* partage de liens](#people-in-your-organization-sharing-links)|Les propriétaires et les membres du site SharePoint peuvent partager des fichiers à l’aide des liens des *membres de votre organisation*, ce qui peut fonctionner pour toute personne au sein de l’organisation.|Les liens *des membres de votre organisation* peuvent être désactivés au niveau du site.|
|[Créer des sites, des groupes et des équipes](#create-sites-groups-and-teams)|Par défaut, les utilisateurs peuvent créer des sites, des groupes et des équipes pour partager du contenu.|Les administrateurs peuvent restreindre le nombre d’utilisateurs autorisés à créer des sites, des groupes et des équipes.|
|[Courrier électronique](#email)|Les personnes ayant accès à un fichier peuvent l'envoyer à d'autres par e-mail.|Les administrateurs peuvent crypter des fichiers en utilisant des étiquettes de sensibilité pour éviter qu'ils ne soient partagés avec des personnes non autorisées.|
|[Télécharger ou copier le dossier](#download-or-file-copy)|Les personnes qui ont accès à un fichier peuvent télécharger ou copier celle-ci et la partager avec d’autres personnes en dehors de l’étendue de Microsoft 365.|Les administrateurs peuvent crypter des fichiers en utilisant des étiquettes de sensibilité pour éviter qu'ils ne soient partagés avec des personnes non autorisées.|

Vous pouvez également restreindre les conditions d’accès des utilisateurs au contenu partagé. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Accès conditionnel](#conditional-access) plus bas dans cet article.

Bien que vous puissiez utiliser les contrôles d'administration décrits dans cet article pour limiter le partage dans votre organisation, nous vous recommandons vivement d'envisager d'utiliser les fonctionnalités de sécurité et de conformité disponibles dans Microsoft 365 pour créer un environnement de partage sécurisé. Voir [Collaboration de fichiers dans SharePoint avec Microsoft 365](/sharepoint/deploy-file-collaboration) et [Configurer une équipe avec isolation de sécurité](secure-teams-security-isolation.md) pour plus d'informations.

Pour comprendre comment le partage est utilisé au sein de votre organisation, [exécuter un rapport sur le partage de fichiers et de dossiers](/sharepoint/sharing-reports).

## <a name="microsoft-365-group-or-team"></a>Groupe ou équipe Microsoft 365

Si vous voulez limiter le partage dans un groupe Microsoft 365 ou une équipe Microsoft Teams, il est important que le groupe ou l’équipe soit privée. Les membres de votre organisation peuvent rejoindre un groupe public ou une équipe à tout moment. À moins que le groupe ou l’équipe ne soit privé, vous ne pouvez pas limiter le partage de l’équipe ou de ses fichiers au sein de l’organisation.

### <a name="guest-sharing"></a>Partage d’invités

Si vous voulez empêcher l’accès invité dans Teams, vous pouvez désactiver le partage d’invités dans le centre d’administration Teams.

Pour désactiver le partage d’invités pour les Teams
1. Dans le Centre d’administration Teams, développez **Paramètres à l’échelle de l’organisation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**puis cliquez sur l’onglet Accès invité**</a>.
2. Désactivez **Autoriser l’accès invité dans Teams**.
3. Cliquez sur **Enregistrer**.

Si vous souhaitez empêcher l’accès invité dans les groupes Microsoft 365, vous pouvez désactiver les paramètres d’accès invité des groupes dans le Centre d’administration Microsoft 365.

Pour désactiver le partage avec les invités pour les groupes Microsoft 365
1. Dans la Centre d'administration Microsoft 365, cliquez sur l’onglet **Paramètres** > **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Services**</a>.
2. Cliquez sur **Groupes Microsoft 365**.
3. Désactivez les cases à cocher **Permettre aux membres du groupe à l’extérieur de votre organisation à accéder au contenu de groupe** et **Permettre aux propriétaires de groupe d’ajouter des personnes extérieures à votre organisation à des groupes**.
4. Cliquez sur **Enregistrer les modifications**.

    ![Capture d’écran des paramètres de partage des groupes Microsoft 365 dans le Centre d’administration Microsoft 365.](../media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> Si vous souhaitez empêcher le partage d’invités pour un groupe ou une équipe spécifique, vous pouvez utiliser [Microsoft PowerShell](per-group-guest-access.md) ou des [étiquettes de confidentialité](../compliance/sensitivity-labels-teams-groups-sites.md).

Vous pouvez limiter le partage d’invités aux utilisateurs de domaines spécifiques en autorisant ou en bloquant les domaines dans Azure Active Directory. Cela affecte également le partage d’invités dans SharePoint si vous avez activé [SharePoint et l’intégration de OneDrive à l’aide d’Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview).

Pour autoriser uniquement les invitations de partage à partir de domaines spécifiés
1. Dans Azure Active Directory, dans la page vue d’ensemble, cliquez sur **relations organisationnelles**.
2. Cliquez sur **Paramètres**.
3. Sous **Restrictions de collaboration**, sélectionnez **Refuser les invitations aux domaines spécifiés** ou **Autoriser les invitations uniquement aux domaines spécifiés**, puis tapez les domaines que vous voulez utiliser.
4. Cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres de restrictions de collaboration dans Azure Active Directory.](../media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a>Site SharePoint

Vous pouvez limiter le partage de sites SharePoint uniquement aux propriétaires de sites. Cela empêche les membres du site de partager le site. Rappelez-vous que si le site est connecté à un groupe Microsoft 365, les membres du groupe peuvent inviter d’autres personnes et ces utilisateurs pourront accéder au site.

Pour limiter le partage de sites aux propriétaires
1. Sur le sites, cliquez sur l’icône d’engrenage, puis cliquez sur **Autorisations du site**.
2. Sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.
3. Sélectionnez les **Propriétaires et membres du site, et les personnes disposant des autorisations de modification peuvent partager des fichiers et des dossiers, mais seuls les propriétaires de site peuvent partager le site**.
4. Cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres d’autorisations de partage dans un site SharePoint.](../media/sharepoint-site-sharing-permissions-level-two.png)

Vous pouvez empêcher les utilisateurs qui ne sont pas membres du site de demander l’accès en désactivant les demandes d’accès.

Pour désactiver les demandes d’accès
1. Sur le sites, cliquez sur l’icône d’engrenage, puis cliquez sur **Autorisations du site**.
2. Sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.
3. Désactivez **Autoriser les demandes d’accès**, puis cliquez sur **Enregistrer**.

Vous pouvez limiter le partage de sites à des domaines spécifiques en autorisant ou en bloquant les domaines pour le site.

Pour limiter le partage de sites par domaine

1. Dans le Centre d’administration SharePoint, sous **Sites**, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a>.
2. Sélectionnez sur le site à configurer.
3. Sous l’onglet **Stratégies**, sous **Partage externe** cliquez sur **Modifier**.
4. Sous **Paramètres avancés pour le partage externe**, cochez la case **Limiter le partage externe par domaine**.
5. Ajoutez les domaines que vous souhaitez autoriser ou bloquer, puis sélectionnez **Enregistrer**.
6. Sélectionnez **Enregistrer**.

    ![Capture d’écran du paramètre au niveau du site des domaines autorisés.](../media/limit-site-sharing-by-domain.png)

### <a name="block-access-to-a-site"></a>Bloquer l’accès à la site

Vous pouvez bloquer l'accès à un site ou rendre un site en lecture seule en modifiant l'état de verrouillage du site. Pour plus de détails, voir [Verrouiller et déverrouiller des sites](/sharepoint/manage-lock-status).

### <a name="permissions-inheritance"></a>Héritage des autorisations

Nous vous déconseillons d’utiliser [l’héritage des autorisations SharePoint](/sharepoint/what-is-permissions-inheritance) pour personnaliser les niveaux d’accès aux sites et aux sous-sites.

## <a name="sharing-with-specific-people"></a>Partager avec des personnes spécifiques

Si vous voulez limiter le partage d’un site ou de son contenu, vous pouvez configurer le site pour autoriser uniquement les propriétaires de site à partager des fichiers, des dossiers et le site. Lorsque cette option est configurée, les membres du site tentent de partager des fichiers ou des dossiers à l’aide des liens *Personnes spécifiques* sont dirigés vers le propriétaire du site pour approbation.

Pour limiter le partage du site, des fichiers et des dossiers aux propriétaires
1. Sur le sites, cliquez sur l’icône d’engrenage, puis cliquez sur **Autorisations du site**.
2. Sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.
3. Sélectionnez **Seuls les propriétaires de site peuvent partager des fichiers, des dossiers et le site**.
4. Cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres d’autorisations de partage d’un site SharePoint définis sur propriétaires uniquement.](../media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a>Partage d’invités SharePoint

Si vous voulez empêcher le partage de fichiers et de dossiers SharePoint ou OneDrive avec des personnes externes à votre organisation, vous pouvez désactiver le partage d’invités pour l’ensemble de l’organisation ou pour un site individuel.

Pour désactiver le partage d’invités SharePoint pour votre organisation

1. Dans le Centre d’administration SharePoint, sous **Stratégies**, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Partage**</a>.
2. Sous **Partage externe**, faites glisser le curseur SharePoint vers le **Uniquement les membres de votre organisation.**.
3. Sélectionnez **Enregistrer**.

    ![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation définis sur Tout le monde.](../media/sharepoint-tenant-sharing-off.png)


Pour désactiver le partage d’invités pour un site
1. Dans le Centre d’administration SharePoint, sous **Sites**, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a>.
2. Sélectionnez sur le site à configurer.
3. Sous l’onglet **Stratégies**, sous **Partage externe** cliquez sur **Modifier**.
4. Sous **Partage externe**, choisissez **Uniquement les personnes de votre organisation**, puis sélectionnez **Enregistrer**.

    ![Capture d’écran des paramètres de partage au niveau du site SharePoint définis sur Uniquement les membres de votre organisation.](../media/sharepoint-site-external-sharing-settings-off.png)

Vous pouvez désactiver le partage invité pour un utilisateur OneDrive individuel en cliquant sur l’utilisateur dans le Centre d’administration Microsoft 365 et en sélectionnant **Gérer le partage externe** sous l’onglet **OneDrive**.

Si vous voulez autoriser le partage avec des personnes externes à votre organisation, mais que vous voulez vous assurer que tout le monde s’authentifie, vous pouvez désactiver les liens *Tout le monde* (partage anonyme) pour l’ensemble de l’organisation ou pour un site individuel.

Pour désactiver les liens *Tout le monde* au niveau de l’organisation

1. Dans le Centre d’administration SharePoint, sous **Stratégies**, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Partage**</a>.
2. Sous **Partage externe**, faites glisser le curseur SharePoint vers le **Invités nouveaux et existants**.
3. Sélectionnez **Enregistrer**.

    ![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation définis sur Invités nouveaux et existants.](../media/sharepoint-guest-sharing-new-existing-guests.png)

Pour désactiver les liens *Tout le monde* d’un site

1. Dans le Centre d’administration SharePoint, sous **Sites**, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a>.
2. Sélectionnez sur le site à configurer.
3. Sous l’onglet **Stratégies**, sous **Partage externe** cliquez sur **Modifier**.
4. Sous **Partage externe**, choisissez **Invités nouveaux et existants**, puis cliquez **Enregistrer**.

    ![Capture d’écran des paramètres de partage SharePoint au niveau du site définis sur Paramètres nouveaux et existants.](../media/sharepoint-site-external-sharing-settings-new-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a>*Membres de votre organisation* partage de liens

Par défaut, les membres d'un site peuvent partager des fichiers et des dossiers avec d'autres personnes de votre organisation en utilisant un lien *Personnes dans votre organisation*. Vous pouvez désactiver les liens des *personnes de votre organisation* à l'aide de PowerShell :

```powershell
Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks Disabled
```

Par exemple :

```powershell
Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks Disabled
```

## <a name="create-sites-groups-and-teams"></a>Créer des sites, des groupes et des équipes

Par défaut, les utilisateurs peuvent créer des sites, des groupes et des équipes pour partager du contenu (selon vos paramètres de partage). Vous pouvez restreindre le nombre d’utilisateurs autorisés à créer des sites, des groupes et des équipes. Si vous souhaitez en savoir plus, veuillez consulter les références suivantes :

- [Gérer la création de sites dans SharePoint](/sharepoint/manage-site-creation)
- [Gérer les personnes autorisées à créer des groupes Microsoft 365](./manage-creation-of-groups.md)

> [!NOTE]
> La restriction de la création de groupes entraîne celle de la création d’équipes.

## <a name="email"></a>E-mail

Vous pouvez empêcher le partage indésirable de messages électroniques à l’aide du chiffrement. Cela empêche les messages électroniques transférés ou partagés avec d’autres utilisateurs non autorisés. Le chiffrement de courrier peut être activé à l’aide d’étiquettes de confidentialité. Consultez [Restreindre l’accès au contenu à l’aide du chiffrement dans les étiquettes de niveau de confidentialité](../compliance/encryption-sensitivity-labels.md) pour les détails.

## <a name="download-or-file-copy"></a>Télécharger ou copier le dossier

Les utilisateurs qui ont accès à des fichiers et des dossiers dans Microsoft 365 peuvent télécharger et copier des fichiers sur un support externe. Pour réduire le risque de partage de fichiers indésirables, vous pouvez chiffrer le contenu à l’aide d’étiquettes de confidentialité.

## <a name="conditional-access"></a>Accès conditionnel

L'accès conditionnel Azure Active Directory Domain Services fournit des options pour limiter ou empêcher le partage avec des personnes en fonction de l'emplacement du réseau, de l'état de l'appareil, du risque de connexion et d'autres facteurs. Voir [Qu'est-ce que l'accès conditionnel ?](/azure/active-directory/conditional-access/overview).

SharePoint offre une intégration directe avec l'accès conditionnel Azure AD pour les appareils non gérés et l'emplacement du réseau. Voir les références suivantes pour plus de détails :

- [Contrôler l’accès à partir d’appareils non gérés](/sharepoint/control-access-from-unmanaged-devices)
- [Contrôler l’accès aux données SharePoint et OneDrive en fonction de l’emplacement réseau](/sharepoint/control-access-based-on-network-location)

## <a name="see-also"></a>Voir aussi

[Références sur les paramètres de partage d’invités de Microsoft 365](microsoft-365-guest-settings.md)
