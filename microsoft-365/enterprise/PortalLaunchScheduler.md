---
title: Lancer votre portail à l’aide du programme de lancement du portail
ms.author: jhendr
author: jhendr
manager: pamgreen
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: Cet article décrit comment lancer votre portail à l’aide du programme de lancement du portail
ms.openlocfilehash: a0ba40849b47af93f45bcc9c77f2ba6d8f715dc5
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53229550"
---
# <a name="launch-your-portal-using-the-sharepoint-portal-launch-scheduler"></a>Lancer votre portail à l’aide du SharePoint de lancement du portail

Un portail est un site de communication SharePoint sur votre intranet qui présente un trafic élevé : un site qui compte entre 10 000 et plus de 100 000 visiteurs sur plusieurs semaines. Utilisez le programme de lancement du portail pour lancer votre portail afin de garantir aux utilisateurs une expérience d’affichage fluide lors de l’accès à SharePoint portail.
<br>
<br>
Le programme de lancement du portail est conçu pour vous aider à suivre une approche de déploiement par étapes en par lots de visionneuses par vagues et en gérant les redirections d’URL pour le nouveau portail. Au cours du lancement de chaque vague, vous pouvez recueillir les commentaires des utilisateurs, surveiller les performances du portail et suspendre le lancement pour résoudre les problèmes avant de poursuivre la vague suivante. En savoir plus sur la [façon de planifier un lancement de portail dans SharePoint](/microsoft-365/Enterprise/Planportallaunchroll-out).

**Il existe deux types de redirections :**

- **Bidirectionnel**: lancer un nouveau portail SharePoint moderne pour remplacer un portail SharePoint classique ou moderne existant
- **Rediriger vers une page temporaire**: lancer un nouveau portail SharePoint moderne sans portail SharePoint existant

Les autorisations de site doivent être définies séparément des vagues dans le cadre du lancement. Par exemple, si vous publiez un portail à l’échelle de l’organisation, vous pouvez définir des autorisations sur « Tout le monde sauf les utilisateurs externes », puis séparer vos utilisateurs en vagues à l’aide de groupes de sécurité. L’ajout d’un groupe de sécurité à une vague ne lui donne pas accès au site.

> [!NOTE]
>
> - Cette fonctionnalité sera accessible à partir du panneau **Paramètres** sur la page d’accueil des sites de communication SharePoint pour les clients de publication ciblée à partir de mai 2021 et sera disponible pour tous les clients d’ici juillet 2021.
> - La version PowerShell de cet outil est disponible aujourd’hui
> - Cette fonctionnalité ne peut être utilisée que sur les sites de communication SharePoint modernes
> - Vous devez avoir des autorisations de propriétaire de site pour personnaliser et planifier le lancement d’un portail
> - Les lancements doivent être programmés au moins sept jours à l’avance et chaque vague peut durer entre un et sept jours.
> - Le nombre de vagues requis est automatiquement déterminé par le nombre d’utilisateurs attendu
> - Avant de planifier le lancement d’un portail, l’outil Diagnostic de page [pour SharePoint](https://aka.ms/perftool) doit être exécuté pour vérifier que la page d’accueil du site est saine
> - À la fin du lancement, tous les utilisateurs ayant des autorisations sur le site pourront accéder au nouveau site.
> - Si votre organisation utilise [Connections,](/SharePoint/viva-connections)les utilisateurs peuvent voir l’icône de votre organisation dans la barre d’application Microsoft Teams. Toutefois, lorsque l’icône est sélectionnée, les utilisateurs ne pourront pas accéder au portail tant que leur vague n’aura pas été lancée.
> - Cette fonctionnalité n’est pas disponible pour Office 365 Germany, Office 365 géré par 21Vianet (Chine) ou les plans Microsoft 365 gouvernement américain

## <a name="understand-the-differences-between-portal-launch-scheduler-options"></a>Comprendre les différences entre les options du programme de planification de lancement du portail :

Auparavant, les lancements de portail pouvaient uniquement être programmés SharePoint PowerShell. Vous avez maintenant deux options pour vous aider à planifier et gérer le lancement de votre portail. Découvrez les principales différences entre les deux outils :

**SharePoint Version de PowerShell :**

- Les informations d’identification d’administrateur sont requises [pour SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell)
- Exigence minimale d’une vague
- Planifier votre lancement en fonction du fuseau horaire UTC (Temps universel coordonné)

**Version du produit :**

- Les informations d’identification du propriétaire du site sont requises
- Exigence minimale de deux vagues
- Planifier votre lancement en fonction du fuseau horaire local du portail, comme indiqué dans les paramètres régionaux

## <a name="get-started-using-the-portal-launch-scheduler"></a>Commencer à utiliser le programme de lancement du portail

1. Avant d’utiliser l’outil de planification de lancement du portail, ajoutez tous les utilisateurs qui auront besoin d’accéder à ce [site](https://support.microsoft.com/office/share-a-site-958771a8-d041-4eb8-b51c-afea2eae3658) via les **autorisations** site en tant que propriétaire du site, membre du site ou visiteur.

2. Ensuite, commencez à planifier le lancement de votre portail en accédant au programme de lancement du portail de deux manières :

   **Option 1**: les premières fois que vous modifiez et repupuyez les modifications apportées à votre page d’accueil (ou jusqu’à la version 3.0 de la page d’accueil), vous êtes invité à utiliser l’outil de planification de lancement du portail. Sélectionnez **Planifier le lancement** pour aller de l’avant avec la planification. Vous pouvez également **sélectionner Republish** pour republier vos modifications de page sans planifier le lancement.

   ![Image de l’invite d’utilisation du programme de lancement du portail lors de la republier de la page d’accueil](../media/portal-launch-republish-2.png)

   **Option 2**: à tout moment, vous pouvez accéder à la page d’accueil du site de communication SharePoint, sélectionner **Paramètres** puis planifier le lancement du **site** pour planifier le lancement de votre portail.

   ![Image du volet Paramètres avec planification d’un lancement de site mis en évidence](../media/portal-launch-settings-2.png)

3. Ensuite, confirmez le score d’état du portail et a amélioré le portail si nécessaire à l’aide de l’outil [Diagnostics](https://aka.ms/perftool) de page pour SharePoint jusqu’à ce que votre portail reçoit un **score** d’état d’santé. Puis sélectionnez **Suivant**.

   ![Image de l’outil de planification de lancement du portail](../media/portal-launch-panel-2.png)

   > [!NOTE]
   > Le nom et la description du site ne peuvent pas être modifiés à partir du programme de lancement du portail et peuvent être modifiés en sélectionnant **Paramètres** puis les informations du **site** dans la page d’accueil.

4. Sélectionnez **le nombre d’utilisateurs attendus** dans la baisse. Cette figure représente le nombre d’utilisateurs qui auront probablement besoin d’accéder au site. Le programme de lancement du portail détermine automatiquement le nombre idéal de vagues en fonction des utilisateurs attendus comme ceci :

   - Moins de 10 000 utilisateurs : deux vagues
   - 10 000 à 30 000 utilisateurs : trois vagues
   - 30 000 à 100 000 utilisateurs : cinq vagues
   - Plus de 100 000 utilisateurs : cinq vagues et contactez microsoft via les étapes répertoriées dans la section Portail de lancement avec plus de 100 000 utilisateurs.

5. Ensuite, déterminez le **type de redirection** nécessaire :

   Option 1 : envoyer les utilisateurs vers une **page SharePoint existante (bidirectionnelle)** : utilisez cette option lors du lancement d’un nouveau portail SharePoint moderne pour remplacer un portail SharePoint existant. Les utilisateurs en vagues actives sont redirigés vers le nouveau site, qu’ils naviguent vers l’ancien ou le nouveau site. Les utilisateurs d’une vague non lancée qui tentent d’accéder au nouveau site sont redirigés vers l’ancien site jusqu’à ce que leur vague soit lancée.

   > [!NOTE]
   > Lorsque vous utilisez l’option bidirectionnelle, la personne qui planifiera le lancement doit également avoir des autorisations de propriétaire de site sur l’SharePoint portail.

   **Option 2 :** Envoyer les utilisateurs vers une page temporaire auto-genrée (redirection de page temporaire) : utilisez une redirection de page temporaire lorsqu’il n’existe aucun portail SharePoint existant. Les utilisateurs sont dirigés vers un nouveau portail SharePoint moderne et si un utilisateur est dans une vague qui n’a pas été lancée, il est redirigé vers une page temporaire.

   **Option 3 : Envoyer** des utilisateurs vers une page externe : fournissez une URL externe à une expérience de page d’accueil temporaire jusqu’à ce que la vague de l’utilisateur soit lancée.

6. Décomposez votre audience en vagues. Ajoutez jusqu’à 20 groupes de sécurité par vague. Les détails des vagues peuvent être modifiés jusqu’au lancement de chaque vague. Chaque vague peut durer au moins un jour (24 heures) et au maximum sept jours. Cela permet à SharePoint et à votre environnement technique d’insérabler et de s’adapter au grand volume d’utilisateurs du site. Lors de la planification d’un lancement via l’interface utilisateur, le fuseau horaire est basé sur les paramètres régionaux du site.

   > [!NOTE]
   >
   > - Par défaut, le planning de lancement du portail est automatiquement de 2 vagues au minimum. Toutefois, la version PowerShell de cet outil autorise la vague 1.
   > - Microsoft 365 groupes ne sont pas pris en charge par cette version du programme de lancement du portail.

7. Déterminez qui doit afficher le site immédiatement et entrez leurs informations dans le champ **Utilisateurs exemptés des vagues.** Ces utilisateurs sont exclus des vagues et ne sont pas redirigés avant, pendant ou après le lancement.

    > [!NOTE]
    > Vous pouvez utiliser jusqu’à 50 utilisateurs ou groupes de sécurité distincts maximum pour l’ensemble du lancement. Chaque lancement est indépendant l’un de l’autre. Ainsi, si vous programmez un lancement sur un autre portail, vous pouvez utiliser jusqu’à 50 utilisateurs/groupes de sécurité pour ce lancement. En outre, vous pouvez utiliser jusqu’à 20 utilisateurs ou groupes de sécurité distincts par vague. 

>Le programme de lancement du portail prend en charge les groupes de sécurité et les groupes de sécurité à messagerie. 


8. Confirmez les détails du lancement du portail et sélectionnez **Planifier.** Une fois le lancement programmé, les modifications apportées à la page d’accueil du portail SharePoint doivent recevoir un résultat de diagnostic sain avant que le lancement du portail reprenne.

### <a name="launch-a-portal-with-over-100k-users"></a>Lancer un portail avec plus de 100 000 utilisateurs

Si vous envisagez de lancer un portail avec plus de 100 000 utilisateurs, envoyez une demande de support en suivant les étapes répertoriées ci-dessous. Veillez à inclure toutes les informations demandées.

**Procédez comme suit :**

1. Accédez à <https://admin.microsoft.com>.
2. Vérifier que vous utilisez la nouvelle prévisualisation du Centre d’administration
3. Dans le volet de navigation de gauche, sélectionnez **Support,** puis **sélectionnez Nouvelle demande de service**

   Cette opération active le volet **Besoin d'aide ?** sur le côté droit de l’écran.

4. Pour **décrire brièvement votre problème,** entrez « Lancer SharePoint portail avec 100 000 utilisateurs »</br>
5. Ensuite, sélectionnez **Contacter le support technique**
6. Sous **Description,** entrez « Lancer SharePoint portail avec 100 000 utilisateurs »
7. Remplissez les informations restantes, puis sélectionnez **Me contacter**
8. Une fois le ticket créé, veillez à fournir à l’agent de support les informations suivantes :
   - URL du portail
   - Nombre d’utilisateurs attendus
   - Planification de lancement estimée

## <a name="make-changes-to-a-scheduled-portal-launch"></a>Apporter des modifications à un lancement de portail programmé

Les détails du lancement peuvent être modifiés pour chaque vague jusqu’à la date de lancement de la vague.

1. Pour modifier les détails du lancement du portail, **accédez à Paramètres** puis sélectionnez **Planifier le lancement du site.**
2. Ensuite, sélectionnez **Modifier**.
3. Lorsque vous avez terminé vos modifications, sélectionnez **Mettre à jour.**

## <a name="delete-a-scheduled-portal-launch"></a>Supprimer un lancement de portail programmé

Les lancements programmés à l’aide de l’outil de planification de lancement du portail peuvent être annulés ou supprimés à tout moment, même si certaines vagues ont déjà été lancées.

1. Pour annuler le lancement de votre portail, accédez à **Paramètres** et **planifier le lancement du site.**

2. Ensuite, **sélectionnez Supprimer,** puis, lorsque vous voyez le message ci-dessous, **sélectionnez Supprimer** à nouveau.

   ![Image de l’outil de planification de lancement du portail](../media/portal-launch-delete-2.png)

## <a name="use-the-powershell-portal-launch-scheduler"></a>Utiliser le programme de lancement du portail PowerShell

À l’origine, l’outil de planification de lancement du portail SharePoint était disponible uniquement via [SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) et continuera d’être pris en charge via PowerShell pour les clients qui préfèrent utiliser cette méthode. Les mêmes remarques au début de cet article s’appliquent aux deux versions du programme de lancement du portail.

> [!NOTE]
> Vous avez besoin d’autorisations d’administrateur pour SharePoint PowerShell.
> Les détails de lancement du portail pour les lancements créés dans PowerShell s’affichent et peuvent être gérés dans le nouvel outil de planification de lancement du portail dans SharePoint.

### <a name="app-setup-and-connecting-to-sharepoint-online"></a>Configuration de l’application et connexion à SharePoint Online

1. [Téléchargez la dernière version de SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > Si vous avez installé une version antérieure de SharePoint Online Management Shell, accédez à Ajouter ou supprimer des programmes et désinstaller « SharePoint Online Management Shell ».<br>Dans la page du Centre de téléchargement, sélectionnez votre langue, puis cliquez sur le bouton Télécharger. Vous serez invité à choisir entre le téléchargement d’un fichier .msi x64 et x86. Téléchargez le fichier x64 si vous exécutez la version 64 bits de Windows ou le fichier x86 si vous exécutez la version 32 bits. En cas de doute, consultez [Quelle est la version du système d’exploitation Windows que j’utilise ?](https://support.microsoft.com/help/13443/windows-which-operating-system). Une fois le fichier téléchargé, exécutez-le, puis suivez les étapes de l'Assistant d'installation.

2. Connectez-vous à SharePoint en tant qu’[administrateur général ou administrateur SharePoint](/sharepoint/sharepoint-admin-role) dans Microsoft 365. Pour savoir comment procéder, reportez-vous à l’article [Prise en main de SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

### <a name="view-any-existing-portal-launch-setups"></a>Afficher les configurations de lancement de portail existantes

Pour voir s’il existe des configurations de lancement de portail :

   ```PowerShell
   Get-SPOPortalLaunchWaves -LaunchSiteUrl <object> -DisplayFormat <object>
   ```

### <a name="schedule-a-portal-launch-on-the-site"></a>Planifier un lancement de portail sur le site

Le nombre de vagues requises dépend de la taille de lancement attendue.

- Moins de 10 000 utilisateurs : une vague
- 10 000 à 30 000 utilisateurs : trois vagues 
- 30 000 à 100 000 utilisateurs : cinq vagues
- Plus de 100 000 utilisateurs : cinq vagues et contactez votre équipe de compte Microsoft

#### <a name="steps-for-bidirectional-redirection"></a>Étapes de redirection bidirectionnelle

La redirection bidirectionnelle implique le lancement d’un nouveau portail SharePoint Online pour remplacer un portail SharePoint classique ou moderne existant. Les utilisateurs en vagues actives sont redirigés vers le nouveau site, qu’ils naviguent vers l’ancien ou le nouveau site. Les utilisateurs d’une vague non lancée qui tentent d’accéder au nouveau site sont redirigés vers l’ancien site jusqu’à ce que leur vague soit lancée.

La redirection est uniquement prise en charge entre la page d’accueil par défaut sur l’ancien site et la page d’accueil par défaut sur le nouveau site. Si vous avez des administrateurs ou des propriétaires qui ont besoin d’accéder aux anciens et nouveaux sites sans être redirigés, assurez-vous qu’ils sont répertoriés à l’aide du `WaveOverrideUsers` paramètre.

Pour migrer les utilisateurs d’un site SharePoint existant vers un nouveau site SharePoint de manière par étape :

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

2. Validation complète. La redirection peut prendre entre 5 et 10 minutes pour terminer sa configuration dans le service.

#### <a name="steps-for-redirection-to-temporary-page"></a>Étapes de redirection vers une page temporaire

La redirection de page temporaire doit être utilisée lorsqu’il n’existe SharePoint portail existant. Les utilisateurs sont dirigés vers un nouveau portail SharePoint Online moderne de manière par étape. Si un utilisateur est dans une vague qui n’a pas été lancée, il est redirigé vers une page temporaire (toute URL).

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

2. Validation complète. La redirection peut prendre entre 5 et 10 minutes pour terminer sa configuration dans le service.

### <a name="pause-or-restart-a-portal-launch-on-the-site"></a>Suspendre ou redémarrer un lancement de portail sur le site

1. Pour interrompre un lancement du portail en cours et empêcher temporairement les progressions de vague à venir, exécutez la commande suivante :

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl <object>
   ```

2. Vérifier que tous les utilisateurs sont redirigés vers l’ancien site.

3. Pour redémarrer un lancement de portail qui a été suspendu, exécutez la commande suivante :

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl <object>
   ```

4. Vérifier que la redirection est maintenant restaurée.

### <a name="delete-a-portal-launch-on-the-site"></a>Supprimer un lancement de portail sur le site

1. Exécutez la commande suivante pour supprimer un lancement de portail prévu ou en cours pour un site.

   ```PowerShell
   Remove-SPOPortalLaunchWaves -LaunchSiteUrl <object>
   ```

2. Vérifier qu’aucune redirection ne se produit pour tous les utilisateurs.

## <a name="learn-more"></a>En savoir plus

[Planification de votre plan de déploiement de lancement de portail dans SharePoint Online](./planportallaunchroll-out.md)

[Planifier votre site de communication](https://support.microsoft.com/office/plan-your-sharepoint-communication-site-35d9adfe-d5cc-462f-a63a-bae7f2529182)
