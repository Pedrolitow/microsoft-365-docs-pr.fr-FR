---
title: Protégez-vous contre les programmes malveillants et autres menaces avec Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-business
ms.subservice: business-premium
ms.localizationpriority: high
ms.date: 08/18/2022
ms.collection:
- M365-Campaigns
- m365solution-smb
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: Obtenir de l’aide pour augmenter le niveau de protection dans Microsoft 365 Business Premium
ms.openlocfilehash: 1a723de38467f62cf191ac485714423fba9b63e4
ms.sourcegitcommit: 651610ca73bfd1d008d97311b59782790df664fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67613975"
---
# <a name="protect-against-malware-and-other-cyberthreats-with-microsoft-365-business-premium"></a>Protégez-vous contre les programmes malveillants et autres cybermenaces avec Microsoft 365 Business Premium

Dans cet objectif, vous augmentez votre protection contre les menaces avec Microsoft 365 Business Premium. Il est essentiel de protéger votre entreprise contre le hameçonnage, les programmes malveillants et d’autres menaces. Cet article contient également des informations sur :

- [Les stratégies de sécurité prédéfinies](#review-and-apply-preset-security-policies) qui peuvent faire gagner beaucoup de temps dans l’installation et la configuration.
- [Stratégies de sécurité personnalisées](#create-custom-security-policies) que vous pouvez définir en fonction des besoins de votre entreprise.
- [Comment ajuster vos paramètres de partage pour les fichiers et dossiers SharePoint et OneDrive](#set-sharing-settings-for-sharepoint-and-onedrive-files-and-folders).
- [Stratégies d’alerte](#review-your-alert-policies) qui surveillent des fichiers spécifiques et comment ils sont utilisés.
- [Gérez le partage de calendrier](#manage-calendar-sharing) pour permettre aux utilisateurs de planifier des réunions de manière appropriée.
- [Vos objectifs suivants](#next-objectives).

## <a name="review-and-apply-preset-security-policies"></a>Examiner et appliquer des stratégies de sécurité prédéfinies

Votre abonnement inclut des [stratégies de sécurité prédéfinies](../security/office-365-security/preset-security-policies.md) qui utilisent les paramètres recommandés pour la protection anti-courrier indésirable, anti-programme malveillant et anti-hameçonnage. Par défaut, la protection intégrée est activée ; toutefois, envisagez d’appliquer une protection standard ou stricte pour renforcer la sécurité.

:::image type="content" source="media/m365bp-presetsecuritypolicies.png" alt-text="Capture d’écran des stratégies de sécurité prédéfinies.":::

> [!NOTE]
> Les stratégies de sécurité prédéfinies ne sont pas les mêmes que [paramètres de sécurité par défaut](m365bp-conditional-access.md#security-defaults). En règle générale, vous utiliserez *soit* les paramètres de sécurité par défaut *ou* [l’accès conditionnel](m365bp-conditional-access.md#conditional-access) en premier, puis vous ajouterez vos stratégies de sécurité. [Les stratégies de sécurité prédéfinies](#what-are-preset-security-policies) simplifient le processus d’ajout de vos stratégies de sécurité. Vous pouvez également [ajouter vos propres formulaires de réponse personnalisés](#create-custom-security-policies). 

### <a name="what-are-preset-security-policies"></a>Que sont les stratégies de sécurité prédéfinies ?

Les stratégies de sécurité prédéfinies fournissent une protection pour votre contenu de messagerie et de collaboration. Ces stratégies se composent des éléments suivants :

- *Profils*, qui déterminent le niveau de protection
- *Stratégies* (par exemple, anti-courrier indésirable, anti-programme malveillant, anti-hameçonnage, paramètres d’usurpation d’identité, pièces jointes fiables et liens fiables)
- *Paramètres de stratégie* (tels que les groupes, les utilisateurs ou les domaines pour recevoir les stratégies et toutes les exceptions)

Le tableau suivant récapitule les niveaux de protection et les types de stratégie prédéfinies.

| Niveau de protection | Description |
|:---|:---|
| **Protection standard** <br/>(*recommandé pour la plupart des entreprises*) | Protection standard : profil de protection de base de référence adapté à la plupart des utilisateurs. La protection standard inclut la protection anti-courrier indésirable, anti-programme malveillant, anti-hameçonnage, paramètres d’usurpation d’identité, paramètres d’emprunt d’identité, liens fiables et stratégies de pièces jointes fiables.  |
| **Protection stricte**  | La protection stricte inclut les mêmes types de stratégies que la protection standard, mais avec des paramètres plus stricts. Si votre entreprise doit respecter des exigences ou réglementations de sécurité supplémentaires, envisagez d’appliquer une protection stricte à au moins vos utilisateurs prioritaires ou à vos cibles à valeur élevée. |
| **Protection intégrée** | Protège contre les liens malveillants et les pièces jointes dans le courrier électronique. La protection intégrée est activée et appliquée à tous les utilisateurs par défaut.  |

> [!TIP]
> Vous pouvez spécifier les utilisateurs, les groupes et les domaines à recevoir des stratégies prédéfinies, et vous pouvez définir certaines exceptions, mais vous ne pouvez pas modifier les stratégies prédéfinies elles-mêmes. Si vous souhaitez utiliser différents paramètres pour vos stratégies de sécurité, vous pouvez créer vos propres stratégies personnalisées en fonction des besoins de votre entreprise.

### <a name="policy-order-of-priority"></a>Ordre de priorité de la stratégie

Si plusieurs stratégies sont affectées aux utilisateurs, un ordre de priorité est utilisé pour appliquer les stratégies. L’ordre de priorité fonctionne comme suit :

1. **La protection stricte** reçoit la priorité la plus élevée et remplace toutes les autres stratégies.

2. **Protection standard** 

3. **Stratégies de sécurité personnalisées**

4. **La protection intégrée** reçoit la priorité la plus basse et est remplacée par une protection stricte, une protection standard et des stratégies personnalisées.

La protection stricte remplace toutes les autres stratégies, et la protection intégrée est remplacée par les autres stratégies. 

Pour en savoir plus sur les stratégies de sécurité prédéfinies, consultez [De quoi les stratégies de sécurité prédéfinies sont constituées](../security/office-365-security/preset-security-policies.md#what-preset-security-policies-are-made-of).

### <a name="how-do-i-assign-preset-security-policies-to-users"></a>Comment faire attribuer des stratégies de sécurité prédéfinies aux utilisateurs ?

> [!IMPORTANT]
> Avant de commencer, assurez-vous que vous disposez de l’un des rôles suivants attribués dans Exchange Online (inclus dans votre abonnement) :
> 
> - Administrateur général
> - Gestion de l’organisation
> - Administrateur de sécurité
> 
> Pour plus d’informations, consultez [Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo) et [À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md).

Pour affecter des stratégies de sécurité prédéfinies, procédez comme suit :

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Accédez à **E-mail et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies de sécurité prédéfinies** dans la section **Stratégies prédéfinies**. (Pour accéder directement à la page **Stratégies de sécurité prédéfinies**, utilisez <https://security.microsoft.com/presetSecurityPolicies>.)

3. Dans la page **Stratégies de sécurité prédéfinies** , dans la section **Protection standard** ou **Protection stricte**, remplacez le bouton bascule **Désactivé** par **Activé**, puis sélectionnez **Gérer**.

4. L’Assistant **Appliquer une protection standard** ou **Appliquer une protection stricte** démarre dans un menu volant. Dans les **protections EOP s’appliquent à** la page, identifiez les destinataires internes auxquels les stratégies s’appliquent (conditions de destinataire) :
   - **Utilisateurs**
   - **Groupes**
   - **Domaines**

   Cliquez dans la zone appropriée, commencez à taper une valeur, puis sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, sélectionnez l’icône **Supprimer** en regard de la valeur.

   Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identificateurs (nom, nom d’affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom complet correspondant apparaît dans les résultats. Pour les utilisateurs, tapez un astérisque (\*) seul pour afficher toutes les valeurs disponibles.

   Pour spécifier une exclusion, cochez la case **Exclure ces utilisateurs, groupes et domaines**, puis spécifiez les utilisateurs, groupes ou domaines à exclure.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **les protections Defender pour Office 365 s’appliquent à** pour identifier les destinataires internes auxquels les stratégies s’appliquent (conditions des destinataires). Spécifiez des utilisateurs, des groupes et des domaines comme vous l’avez fait à l’étape précédente.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Vérifier et confirmer vos modifications**, vérifiez vos sélections, puis sélectionnez **Confirmer**.

> [!TIP]
> Pour en savoir plus sur l’attribution de stratégies de sécurité prédéfinies, consultez les articles suivants :
> - [Affecter des stratégies de sécurité prédéfinies aux utilisateurs](../security/office-365-security/preset-security-policies.md#assign-preset-security-policies-to-users)
> - [Paramètres recommandés pour le contenu de messagerie et de collaboration](../security/office-365-security/recommended-settings-for-eop-and-office365.md) (Microsoft 365 Business Premium inclut Exchange Online Protection et Microsoft Defender pour Office 365 Plan 1)

## <a name="create-custom-security-policies"></a>Créer des stratégies de sécurité personnalisées

Les [stratégies de sécurité prédéfinies décrites](#what-are-preset-security-policies) plus haut dans cet article offrent une protection renforcée à la plupart des entreprises. Toutefois, vous n’êtes pas limité à l’utilisation de stratégies de sécurité prédéfinies uniquement. Vous pouvez définir vos propres stratégies de sécurité personnalisées en fonction des besoins de votre entreprise. 

Utilisez notre guide de démarrage rapide, [Protéger contre les menaces](../security/office-365-security/protect-against-threats.md), pour commencer à créer vos propres stratégies personnalisées. Les instructions vous guident non seulement dans la configuration de vos propres stratégies de sécurité, mais elles fournissent également des paramètres recommandés à utiliser comme point de départ pour :

- [Protection anti-programme malveillant](../security/office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Protection avancée contre le hameçonnage](../security/office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [Protection anti-courrier indésirable](../security/office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Liens fiables et pièces jointes fiables](../security/office-365-security/protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

## <a name="set-sharing-settings-for-sharepoint-and-onedrive-files-and-folders"></a>Définir les paramètres de partage pour les fichiers et dossiers SharePoint et OneDrive

Par défaut, les niveaux de partage sont définis sur le niveau le plus permissif pour SharePoint et OneDrive. Nous vous recommandons de modifier les paramètres par défaut pour mieux protéger votre entreprise.

1. Accédez à la page de <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Partage** du nouveau Centre d’administration SharePoint</a>, puis connectez-vous à l’aide d’un compte disposant des [autorisations d’administrateur pour votre organisation](/sharepoint/sharepoint-admin-role).

2. Sous **Partage externe**, spécifiez le niveau de partage. (Nous vous recommandons d’utiliser **le moins permissif** pour empêcher le partage externe.)

3. Sous **Liens de fichiers et de dossiers**, sélectionnez une option (par exemple **Personnes spécifiques**). Choisissez ensuite d’accorder des autorisations d’affichage ou de modification par défaut pour les liens partagés (par exemple, **Afficher**).

4. Sous **Autres paramètres**, sélectionnez les options que vous souhaitez utiliser.

5. Choisissez ensuite **Enregistrer**.

> [!TIP]
> Pour en savoir plus sur ces paramètres, consultez [Gérer les paramètres de partage](/sharepoint/turn-external-sharing-on-or-off).

## <a name="review-your-alert-policies"></a>Passer en revue vos stratégies d’alerte

Les stratégies d’alerte sont utiles pour le suivi des activités des utilisateurs et des administrateurs, des menaces potentielles contre les programmes malveillants et des incidents de perte de données dans votre entreprise. Votre abonnement inclut un ensemble de stratégies par défaut, mais vous pouvez également en créer des personnalisées. Par exemple, si vous stockez un fichier important dans SharePoint que personne ne souhaite partager en externe, vous pouvez créer une notification qui vous avertit si quelqu’un le partage.

L’image suivante montre certaines des stratégies par défaut incluses dans Microsoft 365 Business Premium.

![Stratégies d’alerte par défaut incluses dans Microsoft 365.](../media/alertpolicies.png)

### <a name="view-your-alert-policies"></a>Afficher vos stratégies d’alerte

1. Allez sur le portail de conformité Microsoft Purview à l'adresse [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous.

2. Dans le volet de navigation, choisissez **Stratégies**, puis choisissez **Stratégies d’alerte**.

3. Sélectionnez une stratégie individuelle pour afficher plus de détails ou pour modifier la stratégie. L’image suivante montre une liste de stratégies d’alerte avec une stratégie sélectionnée :

   :::image type="content" source="media/selected-alert-policy.png" lightbox="media/selected-alert-policy.png" alt-text="Capture d’écran d’une stratégie d’alerte sélectionnée.":::

> [!TIP]
> Pour plus d’informations, consultez [stratégies d’alerte](../compliance/alert-policies.md).

### <a name="how-to-view-alerts"></a>Comment afficher les alertes

Vous pouvez afficher vos alertes dans le portail Microsoft 365 Defender ou dans le portail de conformité Microsoft Purview.

| Type d’alerte  | Procédure  |
|---------|---------|
| Alerte de sécurité, par exemple lorsqu’un utilisateur clique sur un lien malveillant, qu’un e-mail est signalé comme programme malveillant ou hameçonnage, ou qu’un appareil est détecté comme contenant des programmes malveillants     | Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> et sous **Email et collaboration**, sélectionnez **Stratégies et règles** > **stratégie d’alerte**. Vous pouvez également accéder directement à <https://security.microsoft.com/alertpolicies>. |
| Alerte de conformité, par exemple lorsqu’un utilisateur partage des informations sensibles ou confidentielles (alerte de protection contre la perte de données) ou qu’il existe un volume inhabituel de partage de fichiers externes (alerte de gouvernance des informations)    | Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Portail de conformité Microsoft Purview</a>, puis sélectionnez **Stratégies** > **Alerte** > **Stratégies d’alerte**.  |

Pour plus d’informations, consultez [Afficher les alertes](../compliance/alert-policies.md#view-alerts).

## <a name="manage-calendar-sharing"></a>Gérer le partage de calendrier

Vous pouvez aider les membres de votre organisation à partager leurs calendriers de manière appropriée pour une meilleure collaboration. Vous pouvez gérer le niveau de détail qu’ils peuvent partager, par exemple en limitant les détails partagés aux heures de disponibilité uniquement.

1. Accédez à[Paramètres de l’organisation dans le Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2053743) et connectez-vous.

2. Choisissez **Calendrier** et indiquez si les membres de votre organisation peuvent partager leurs calendriers avec des personnes extérieures à Office 365 ou Exchange, ou avec n’importe qui. Nous vous recommandons d’effacer l’option de **Partage externe**. Si vous choisissez de partager des calendriers avec n’importe qui, vous pouvez également partager des informations gratuites/occupées uniquement.

3. Sélectionnez **Enregistrer les modifications** en bas de la page.

   L’image suivante montre que le partage de calendrier n’est pas autorisé.

   ![Capture d’écran montrant le partage de calendrier externe comme non autorisé.](../media/nocalendarsharing.png)

   L’image suivante montre les paramètres lorsque le partage de calendrier est autorisé avec un lien d’e-mail contenant uniquement des informations de disponibilité.

   ![Capture d’écran du partage de disponibilité du calendrier avec tout le monde.](../media/sharefreebusy.png)

Si vos utilisateurs sont autorisés à partager leurs calendriers, consultez [ces instructions](https://support.office.com/article/7ecef8ae-139c-40d9-bae2-a23977ee58d5) pour savoir comment partager à partir d’Outlook sur le web.

## <a name="next-objectives"></a>Objectifs suivants

Effectuez les actions suivantes:

- [Configurer des appareils non gérés (BYOD)](m365bp-devices-overview.md)
- [Protéger tous les e-mails](m365bp-protect-email-overview.md)
- [Collaborer et partager de manière sécurisée](m365bp-collaborate-share-securely.md)
- [Configurer et sécuriser des appareils gérés](m365bp-protect-devices.md)
