---
title: Lancer votre portail à l’aide du planificateur de lancement du portail
ms.author: jhendr
author: jhendr
manager: pamgreen
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: Cet article explique comment lancer votre portail à l’aide du planificateur de lancement du portail.
ms.openlocfilehash: 9d04cd984ee194e10d8372e8ed1246ba2b389aea
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67669881"
---
# <a name="launch-your-portal-using-the-sharepoint-portal-launch-scheduler"></a>Lancer votre portail à l’aide du planificateur de lancement du portail SharePoint

Un portail est un site de communication SharePoint sur votre intranet qui est à fort trafic, un site qui compte entre 10 000 et plus de 100 000 visiteurs au cours de plusieurs semaines. Utilisez le planificateur de lancement du portail pour lancer votre portail afin de garantir aux utilisateurs une expérience d’affichage fluide lors de l’accès à votre nouveau portail SharePoint.
<br>
<br>
Le planificateur de lancement du portail est conçu pour vous aider à suivre une approche de déploiement progressive en mettant en lots les visionneuses par vagues et en gérant les redirections d’URL pour le nouveau portail. Pendant le lancement de chaque vague, vous pouvez recueillir les commentaires des utilisateurs, surveiller les performances du portail et suspendre le lancement pour résoudre les problèmes avant de passer à la vague suivante. En savoir plus sur la [planification d’un lancement de portail dans SharePoint](/microsoft-365/Enterprise/Planportallaunchroll-out).

**Il existe deux types de redirections :**

- **Bidirectionnel** : lancer un nouveau portail SharePoint moderne pour remplacer un portail SharePoint classique ou moderne existant
- **Rediriger vers une page temporaire** : lancer un nouveau portail SharePoint moderne sans portail SharePoint existant

Les autorisations de site doivent être configurées séparément des ondes dans le cadre du lancement. Par exemple, si vous publiez un portail à l’échelle de l’organisation, vous pouvez définir des autorisations sur « Tout le monde sauf les utilisateurs externes », puis séparer vos utilisateurs en vagues à l’aide de groupes de sécurité. L’ajout d’un groupe de sécurité à une vague ne donne pas à ce groupe de sécurité l’accès au site.

> [!NOTE]
>
> - Cette fonctionnalité sera accessible à partir du panneau **Paramètres** de la page d’accueil des sites de communication SharePoint.
> - Cette fonctionnalité ne peut être utilisée que sur les sites de communication SharePoint modernes à l’aide de pages de site, car il s’agit du type par défaut et recommandé à utiliser pour les portails.
> - Vous devez disposer des autorisations du propriétaire du site pour personnaliser et planifier le lancement d’un portail.
> - Les lancements doivent être planifiés au moins sept jours à l’avance et chaque vague peut durer de un à sept jours.
> - Le nombre d’ondes requises est automatiquement déterminé par le nombre attendu d’utilisateurs.
> - Avant de planifier le lancement d’un portail, [l’outil Diagnostics de page pour SharePoint](https://aka.ms/perftool) doit être exécuté pour vérifier que la page d’accueil du site est saine.
> - À la fin du lancement, tous les utilisateurs disposant d’autorisations sur le site pourront accéder au nouveau site.
> - Si votre organisation utilise [Viva Connections](https://microsoft.sharepoint.com/teams/MicrosoftViva/SitePages/Viva-Connections.aspx), les utilisateurs peuvent voir l’icône de votre organisation dans la barre d’applications Microsoft Teams. Toutefois, lorsque l’icône est sélectionnée, les utilisateurs ne pourront pas accéder au portail tant que leur vague n’aura pas été lancée.
> - Cette fonctionnalité n’est pas disponible pour Office 365 Allemagne, Office 365 géré par 21Vianet (Chine) ou les plans Microsoft 365 US Government.

## <a name="understand-the-differences-between-portal-launch-scheduler-options"></a>Comprendre les différences entre les options du planificateur de lancement du portail :

Auparavant, les lancements du portail pouvaient uniquement être planifiés via SharePoint PowerShell. Vous disposez maintenant de deux options pour vous aider à planifier et gérer le lancement de votre portail. Découvrez les principales différences entre les deux outils :

**Version de SharePoint PowerShell :**

- Administration informations d’identification sont requises pour utiliser [SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell)
- Exigence minimale d’une vague
- Planifier votre lancement en fonction du fuseau horaire UTC (Coordinated Universal Time)

**Version intégrée au produit :**

- Les informations d’identification du propriétaire du site sont requises
- Exigence minimale de deux vagues
- Planifier votre lancement en fonction du fuseau horaire local du portail, comme indiqué dans les paramètres régionaux

## <a name="get-started-using-the-portal-launch-scheduler"></a>Prise en main du planificateur de lancement du portail

1. Avant d’utiliser l’outil planificateur de lancement du portail, [ajoutez tous les utilisateurs qui auront besoin d’accéder à ce site](https://support.microsoft.com/office/share-a-site-958771a8-d041-4eb8-b51c-afea2eae3658) via **des autorisations de** site en tant que propriétaire du site, membre du site ou visiteur.

2. Ensuite, commencez à planifier le lancement de votre portail en accédant au planificateur de lancement du portail de l’une des deux manières suivantes :

   **Option 1** : Les premières fois que vous modifiez et republiez les modifications apportées à votre page d’accueil ( ou jusqu’à la page d’accueil version 3.0 ), vous êtes invité à utiliser l’outil planificateur de lancement du portail. Sélectionnez **Planifier le lancement** pour aller de l’avant avec la planification. Ou sélectionnez **Republier** pour republier vos modifications de page sans planifier le lancement.

   ![Image de l’invite à utiliser le planificateur de lancement du portail lors de la republication de la page d’accueil.](../media/portal-launch-republish-2.png)

   **Option 2** : À tout moment, vous pouvez accéder à la page d’accueil du site de communication SharePoint, sélectionner **Paramètres** , puis **planifier le lancement du site** pour planifier le lancement de votre portail.

   ![Image du volet Paramètres avec planifier le lancement d’un site mis en surbrillance.](../media/portal-launch-settings-2.png)

3. Ensuite, confirmez le score d’intégrité du portail et apportez des améliorations au portail si nécessaire à l’aide de l’outil [Diagnostics de page pour SharePoint](https://aka.ms/perftool) jusqu’à ce que votre portail reçoive un score **Sain** . Puis sélectionnez **Suivant**.

   ![Image de l’outil planificateur de lancement du portail.](../media/portal-launch-panel-2.png)

   > [!NOTE]
   > Le nom et la description du site ne peuvent pas être modifiés à partir du planificateur de lancement du portail et peuvent être modifiés en sélectionnant **Paramètres** , puis **les informations de site** dans la page d’accueil.

4. Sélectionnez le **nombre d’utilisateurs attendus** dans la liste déroulante. Cette figure représente le nombre d’utilisateurs qui auront probablement besoin d’accéder au site. Le planificateur de lancement du portail détermine automatiquement le nombre idéal d’ondes en fonction des utilisateurs attendus comme suit :

   - Moins de 10 000 utilisateurs : deux vagues
   - 10 000 à 30 000 utilisateurs : trois vagues
   - 30 000 à 100 000 utilisateurs : cinq vagues
   - Plus de 100 000 utilisateurs : cinq vagues et contactez le support Microsoft via les étapes répertoriées dans la section Lancer le portail avec plus de 100 000 utilisateurs.

5. Déterminez ensuite le **type de redirection** nécessaire :

   **Option 1 : Envoyer des utilisateurs à une page SharePoint existante (bidirectionnelle)** : utilisez cette option lors du lancement d’un nouveau portail SharePoint moderne pour remplacer un portail SharePoint existant. Les utilisateurs des vagues actives sont redirigés vers le nouveau site, qu’ils accèdent à l’ancien ou au nouveau site. Les utilisateurs d’une vague non lancée qui tentent d’accéder au nouveau site seront redirigés vers l’ancien site jusqu’à ce que leur vague soit lancée.

   > [!NOTE]
   > Lorsque vous utilisez l’option bidirectionnelle, la personne qui planifie le lancement doit disposer d’autorisations de propriétaire de site sur le nouveau portail SharePoint et le portail SharePoint existant. En outre, les deux URL de site doivent exister dans le même locataire/domaine afin de valider les autorisations appropriées. 

   **Option 2 : Envoyer des utilisateurs à une page temporaire générée automatiquement (redirection de page temporaire)** : utilisez une redirection de page temporaire lorsqu’il n’existe aucun portail SharePoint existant. Les utilisateurs sont dirigés vers un nouveau portail SharePoint moderne et, si un utilisateur est dans une vague qui n’a pas été lancée, il est redirigé vers une page temporaire.

   **Option 3 : Envoyer des utilisateurs à une page externe** : fournissez une URL externe à une expérience de page d’accueil temporaire jusqu’à ce que la vague de l’utilisateur soit lancée.

6. Divisez votre audience en vagues. Ajoutez jusqu’à 20 groupes de sécurité par vague. Les détails de l’onde peuvent être modifiés jusqu’au lancement de chaque vague. Chaque vague peut durer au moins un jour (24 heures) et au maximum sept jours. Cela permet à SharePoint et à votre environnement technique d’adapter et de mettre à l’échelle le grand nombre d’utilisateurs du site. Lors de la planification d’un lancement via l’interface utilisateur, le fuseau horaire est basé sur les paramètres régionaux du site.

   > [!NOTE]
   >
   > - Le planificateur de lancement du portail a automatiquement une valeur par défaut d’au moins 2 vagues. Toutefois, la version PowerShell de cet outil autorise 1 vague.
   > - Les groupes Microsoft 365 ne sont pas pris en charge par cette version du planificateur de lancement du portail.

7. Déterminez qui doit afficher le site immédiatement et entrez ses informations dans le champ **Utilisateurs exemptés des ondes** . Ces utilisateurs sont exclus des vagues et ne seront pas redirigés avant, pendant ou après le lancement.

    >[!NOTE]
    > Jusqu’à 50 utilisateurs distincts ou groupes de sécurité maximum peuvent être ajoutés. Utilisez des groupes de sécurité lorsque vous avez besoin de plus de 50 personnes pour accéder au portail avant le lancement des vagues.

8. Confirmez les détails du lancement du portail et sélectionnez **Planifier**. Une fois le lancement planifié, toutes les modifications apportées à la page d’accueil du portail SharePoint doivent recevoir un résultat de diagnostic sain avant la reprise du lancement du portail.

### <a name="launch-a-portal-with-over-100k-users"></a>Lancer un portail avec plus de 100 000 utilisateurs

Si vous envisagez de lancer un portail avec plus de 100 000 utilisateurs, envoyez une demande de support en suivant les étapes répertoriées ci-dessous. Veillez à inclure toutes les informations demandées.

> [!NOTE]
>
> - Ce processus ne doit être suivi que si vous répondez aux exigences suivantes :
> - La page de lancement est terminée.
> - [Les conseils d’intégrité du portail](https://aka.ms/portalhealth) ont été suivis.
> - La date de lancement est de 14 jours.

**Procédez comme suit :**

1. En tant qu’administrateur, cliquez sur le lien suivant qui remplira une requête d’aide dans le Centre d’administration.

[Lancer le portail SharePoint avec 100 000 utilisateurs](https://admin.microsoft.com/AdminPortal/?searchSolutions=Launch%20SharePoint%20Portal%20with%20100k%20users)

2. En bas du volet, sélectionnez **Contacter le support** technique, puis sélectionnez **Nouvelle demande de service.**

3. Sous **Description**, entrez « Lancer le portail SharePoint avec 100 000 utilisateurs ».

4. Renseignez les informations restantes, puis sélectionnez **Me contacter**.

5. Une fois le ticket créé, veillez à fournir à l’agent de support les informations suivantes :
   - URL du portail
   - Nombre d’utilisateurs attendus
   - Planification de lancement estimée (détail des tailles d’onde)
   - Utiliser l’outil Diagnostics de page pour « Exporter le fichier HAR » de la page de lancement et partager le fichier avec prise en charge

## <a name="make-changes-to-a-scheduled-portal-launch"></a>Apporter des modifications à un lancement planifié du portail

Les détails du lancement peuvent être modifiés pour chaque vague jusqu’à la date de lancement de la vague.

1. Pour modifier les détails du lancement du portail, accédez à **Paramètres** et sélectionnez **Planifier le lancement du site**.
2. Ensuite, **sélectionnez Modifier**.
3. Lorsque vous avez terminé d’apporter vos modifications, sélectionnez **Mettre à jour**.

## <a name="delete-a-scheduled-portal-launch"></a>Supprimer un lancement planifié du portail

Les lancements planifiés à l’aide de l’outil planificateur de lancement du portail peuvent être annulés ou supprimés à tout moment, même si certaines vagues ont déjà été lancées.

1. Pour annuler le lancement de votre portail, **accédez à Paramètres** et **Planifiez le lancement du site**.

2. Ensuite, **sélectionnez Supprimer** , puis, lorsque vous voyez le message ci-dessous, **sélectionnez Supprimer** à nouveau.

   ![Image de l’invite qui vous demande si vous souhaitez supprimer ou conserver un lancement planifié.](../media/portal-launch-delete-2.png)

## <a name="use-the-powershell-portal-launch-scheduler"></a>Utiliser le planificateur de lancement du portail PowerShell

À l’origine, l’outil planificateur de lancement du portail SharePoint était uniquement disponible via [SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) et continuera d’être pris en charge via PowerShell pour les clients qui préfèrent cette méthode. Les mêmes notes au début de cet article s’appliquent aux deux versions du planificateur de lancement du portail.

> [!NOTE]
> Vous avez besoin d’autorisations d’administrateur pour utiliser SharePoint PowerShell.
> Les détails du lancement du portail pour les lancements créés dans PowerShell s’affichent et peuvent être gérés dans le nouvel outil du planificateur de lancement du portail dans SharePoint.

### <a name="app-setup-and-connecting-to-sharepoint-online"></a>Configuration de l’application et connexion à SharePoint Online

1. [Téléchargez la dernière version de SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > Si vous avez installé une version antérieure de SharePoint Online Management Shell, accédez à Ajouter ou supprimer des programmes et désinstaller « SharePoint Online Management Shell ».
    >
    > Dans la page du Centre de téléchargement, sélectionnez votre langue, puis cliquez sur le bouton Télécharger. Vous serez invité à choisir entre le téléchargement d’un fichier .msi x64 et x86. Téléchargez le fichier x64 si vous exécutez la version 64 bits de Windows ou le fichier x86 si vous exécutez la version 32 bits. En cas de doute, consultez [Quelle est la version du système d’exploitation Windows que j’utilise ?](https://support.microsoft.com/help/13443/windows-which-operating-system). Une fois le fichier téléchargé, exécutez-le, puis suivez les étapes de l'Assistant d'installation.

2. Connectez-vous à SharePoint en tant [qu'administrateur général ou administrateur SharePoint](/sharepoint/sharepoint-admin-role) dans Microsoft 365. Pour savoir comment, voir [Prise en main de SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

### <a name="view-any-existing-portal-launch-setups"></a>Afficher les configurations de lancement du portail existantes

Pour voir s’il existe des configurations de lancement de portail existantes :

   ```PowerShell
   Get-SPOPortalLaunchWaves -LaunchSiteUrl <object> -DisplayFormat <object>
   ```

### <a name="schedule-a-portal-launch-on-the-site"></a>Planifier le lancement d’un portail sur le site

Le nombre d’ondes requises dépend de la taille de lancement attendue.

- Moins de 10 000 utilisateurs : une vague
- 10 000 à 30 000 utilisateurs : trois vagues
- 30 000 à 100 000 utilisateurs : cinq vagues
- Plus de 100 000 utilisateurs : cinq vagues et contactez votre équipe de compte Microsoft

#### <a name="steps-for-bidirectional-redirection"></a>Étapes de redirection bidirectionnelle

La redirection bidirectionnelle implique le lancement d’un nouveau portail SharePoint Online moderne pour remplacer un portail SharePoint classique ou moderne existant. Les utilisateurs des vagues actives sont redirigés vers le nouveau site, qu’ils accèdent à l’ancien ou au nouveau site. Les utilisateurs d’une vague non lancée qui tentent d’accéder au nouveau site seront redirigés vers l’ancien site jusqu’à ce que leur vague soit lancée.

Nous prenons uniquement en charge la redirection entre la page d’accueil par défaut sur l’ancien site et la page d’accueil par défaut sur le nouveau site. Si vous avez des administrateurs ou des propriétaires qui ont besoin d’accéder aux anciens et nouveaux sites sans être redirigés, assurez-vous qu’ils sont répertoriés à l’aide du `WaveOverrideUsers` paramètre.

Pour migrer des utilisateurs d’un site SharePoint existant vers un nouveau site SharePoint de manière intermédiaire :

1. Exécutez la commande suivante pour désigner les vagues de lancement du portail.

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType Bidirectional -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
   ```

   Exemple :

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType Bidirectional -RedirectUrl "https://contoso.sharepoint.com/teams/oldsite" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves '
   [{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"},
   {Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"},
   {Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Terminer la validation. La redirection peut prendre 5 à 10 minutes pour terminer sa configuration sur le service.

#### <a name="steps-for-redirection-to-temporary-page"></a>Étapes de redirection vers une page temporaire

La redirection de page temporaire doit être utilisée lorsqu’il n’existe aucun portail SharePoint existant. Les utilisateurs sont dirigés vers un nouveau portail SharePoint Online moderne de manière intermédiaire. Si un utilisateur est dans une vague qui n’a pas été lancée, il est redirigé vers une page temporaire (n’importe quelle URL).

1. Exécutez la commande suivante pour désigner les vagues de lancement du portail.

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType ToTemporaryPage -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
   ```

   Exemple :

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType ToTemporaryPage -RedirectUrl "https://portal.contoso.com/UnderConstruction.aspx" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves '
   [{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"},
   {Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"},
   {Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Terminer la validation. La redirection peut prendre 5 à 10 minutes pour terminer sa configuration sur le service.

### <a name="pause-or-restart-a-portal-launch-on-the-site"></a>Suspendre ou redémarrer un lancement du portail sur le site

1. Pour suspendre un lancement du portail en cours et empêcher temporairement les progressions d’onde à venir de se produire, exécutez la commande suivante :

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl <object>
   ```

2. Vérifiez que tous les utilisateurs sont redirigés vers l’ancien site.

3. Pour redémarrer un lancement du portail qui a été suspendu, exécutez la commande suivante :

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl <object>
   ```

4. Vérifiez que la redirection est maintenant restaurée.

### <a name="delete-a-portal-launch-on-the-site"></a>Supprimer un lancement du portail sur le site

1. Exécutez la commande suivante pour supprimer un lancement du portail planifié ou en cours pour un site.

   ```PowerShell
   Remove-SPOPortalLaunchWaves -LaunchSiteUrl <object>
   ```

2. Vérifiez qu’aucune redirection ne se produit pour tous les utilisateurs.

## <a name="learn-more"></a>En savoir plus

[Planification du plan de lancement de votre portail dans SharePoint Online](./planportallaunchroll-out.md)

[Planifier votre site de communication](https://support.microsoft.com/office/plan-your-sharepoint-communication-site-35d9adfe-d5cc-462f-a63a-bae7f2529182)
