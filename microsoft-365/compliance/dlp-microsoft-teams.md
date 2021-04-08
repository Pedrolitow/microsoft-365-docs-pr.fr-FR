---
title: Prévention des pertes de données et Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Vous pouvez désormais appliquer des stratégies DLP aux conversations et canaux Microsoft Teams. Lisez cet article pour en savoir plus sur son fonctionnement.
ms.openlocfilehash: bd6fa1c04a57f64997d5646374007641afa0f958
ms.sourcegitcommit: 58fbcfd6437bfb08966b79954ca09556e636ff4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51632236"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>Prévention des pertes de données et Microsoft Teams

> [!NOTE]
> Des fonctionnalités de protection contre la perte de données ont été récemment ajoutées aux messages de conversation et de canal Microsoft Teams pour les utilisateurs titulaires d’une licence Office 365 E5/A5, Microsoft 365 E5/A5, Microsoft 365 Information Protection and Governance ou Office 365 Advanced Compliance. Office 365 et Microsoft 365 E3 incluent la protection DLP pour SharePoint Online, OneDrive et Exchange Online. Cela inclut également les fichiers partagés via Teams, car Teams utilise SharePoint Online et OneDrive pour partager des fichiers.
La prise en charge de la protection DLP dans Teams Chat nécessite E5.
Pour en savoir plus sur les conditions d’octroi de licences, consultez [Conseils sur la gestion des licences des services de niveau client de Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).

## <a name="overview-of-dlp-for-microsoft-teams"></a>Aperçu du DLP pour Microsoft Teams

Récemment, [les fonctionnalités de](data-loss-prevention-policies.md) protection contre la perte de données (DLP) ont été étendues pour inclure les messages de conversation et de canal Microsoft Teams, y compris les messages de canal **privé.** 

> [!IMPORTANT]
> La DLP s’applique actuellement uniquement aux messages réels dans le thread de conversation ou de canal. Les notifications d’activité, qui incluent un aperçu de message court et  s’affichent en fonction des paramètres de notification d’un utilisateur, ne sont pas incluses dans la DLP Teams pour le moment. Toutes les informations sensibles présentes dans la partie du message qui s’affiche dans l’aperçu resteront visibles dans la notification même après l’application de la stratégie DLP et la suppression des informations sensibles du message lui-même.

Si votre organisation dispose de DLP, vous pouvez désormais définir des stratégies qui empêchent les personnes de partager des informations sensibles dans un canal ou une session de conversation Microsoft Teams. Voici quelques exemples de fonctionnement de cette protection :

- **Exemple 1 : protection des informations sensibles dans les messages**. Supposons qu’une personne tente de partager des informations sensibles dans une conversation ou un canal Teams avec des invités (utilisateurs externes). Si vous avez défini une stratégie DLP pour éviter cela, les messages avec des informations sensibles envoyés à des utilisateurs externes sont supprimés. Cela se produit automatiquement et en quelques secondes, en fonction de la configuration de votre stratégie DLP.

    > [!NOTE]
    > DLP pour Microsoft Teams bloque le contenu sensible lorsqu’il est partagé avec des utilisateurs de Microsoft Teams qui ont :<br/>- [accès invité dans](/MicrosoftTeams/guest-access) les équipes et les canaux ; ou<br/>- [accès externe dans](/MicrosoftTeams/manage-external-access) les réunions et les sessions de conversation. <p>La DLP pour les sessions de conversation externe ne fonctionne que si l’expéditeur et le destinataire sont en mode Teams uniquement et utilisent [la fédération native de Microsoft Teams.](/microsoftteams/manage-external-access) DLP pour Teams ne bloque pas les messages en [cas d’interaction](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) avec Skype Entreprise ou les sessions de conversation fédérée non natives.

- **Exemple 2 : protection des informations sensibles dans les documents**. Supposons qu’une personne tente de partager un document avec des invités dans un canal ou une conversation Microsoft Teams, et que le document contient des informations sensibles. Si vous avez défini une stratégie DLP pour éviter cela, le document ne s’ouvre pas pour ces utilisateurs. Notez que dans ce cas, votre stratégie DLP doit inclure SharePoint et OneDrive pour que la protection soit en place. (Il s’agit d’un exemple de DLP pour SharePoint qui s’affiche dans Microsoft Teams, et par conséquent nécessite que les utilisateurs soient titulaires d’une licence pour Office 365 DLP (inclus dans Office 365 E3), mais ne nécessite pas que les utilisateurs soient titulaires d’une licence pour Office 365 Conformité avancée.)

## <a name="policy-tips-help-educate-users"></a>Les conseils de stratégie aident à former les utilisateurs

De la même manière que dans [Exchange, Outlook, Outlook](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web)sur le [web, SharePoint Online, les sites OneDrive](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites)Entreprise et les clients de bureau [Office,](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs)des conseils de stratégie s’affichent lorsqu’une action entre en conflit avec une stratégie DLP. Voici un exemple de conseil de stratégie :

![Notification de message bloqué dans Teams](../media/dlp-teams-blockedmessage-notification.png)

Dans ce cas, l’expéditeur a tenté de partager un numéro de sécurité sociale dans un canal Microsoft Teams. Le **lien Que puis-je faire ?** ouvre une boîte de dialogue qui fournit des options à l’expéditeur pour résoudre le problème. Notez que dans ce cas, l’expéditeur peut choisir de remplacer la stratégie ou d’avertir un administrateur de la réviser et de la résoudre.

![Options pour résoudre le message bloqué](../media/dlp-teams-blockedmessage-possibleactions.png)

Dans votre organisation, vous pouvez choisir d’autoriser les utilisateurs à remplacer une stratégie DLP. De plus, lorsque vous configurez vos stratégies DLP, vous pouvez utiliser les conseils de stratégie par défaut ou personnaliser les conseils de stratégie [pour](#to-customize-policy-tips) votre organisation.

Pour revenir à notre exemple, où un expéditeur a partagé un numéro de sécurité sociale dans un canal Teams, voici ce que le destinataire a vu :

> [!div class="mx-imgBorder"]
> ![Message bloqué](../media/dlp-teams-blockedmessage-notification-to-user.png)

Le **lien Qu’est-ce que c’est ?** ouvre un [article](data-loss-prevention-policies.md) sur les stratégies DLP, qui explique pourquoi le message a été bloqué.

### <a name="to-customize-policy-tips"></a>Pour personnaliser les conseils de stratégie

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Go to the Security & Compliance Center ( [https://protection.office.com](https://protection.office.com) ) and sign in.

2. Choisissez **la stratégie de protection contre la perte de**  >  **données.**

3. Select a policy, and next to **Policy settings**, choose **Edit**.

4. Créez une règle ou modifiez une règle existante pour la stratégie.

    > [!div class="mx-imgBorder"]
    > ![Modification d’une règle pour une stratégie](../media/dlp-teams-editrule.png)

5. Sous **l’onglet Notifications de** l’utilisateur, sélectionnez Personnaliser le texte de l’e-mail et/ou personnaliser les options de texte du **conseil de** stratégie. 

    > [!div class="mx-imgBorder"]
    > ![Personnaliser les notifications utilisateur et les conseils de stratégie](../media/dlp-teams-editrule-usernotifications.png)<br/>  

6. Spécifiez le texte que vous souhaitez utiliser pour les notifications par courrier électronique et/ou les conseils de stratégie, puis sélectionnez **Enregistrer**.

7. Sous **l’onglet Paramètres de stratégie,** sélectionnez **Enregistrer.**

Laissez environ une heure à vos modifications pour qu’elles fonctionnent dans votre centre de données et se synchronisent avec les comptes d’utilisateurs.
 <!-- why are these syncing to user accounts? -->

## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>Ajouter Microsoft Teams comme emplacement aux stratégies DLP existantes

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Go to the Security & Compliance Center ( [https://protection.office.com](https://protection.office.com) ) and sign in.

2. Choisissez **la stratégie de protection contre la perte de**  >  **données.**

3. Sélectionnez une stratégie et regardez les valeurs sous **Emplacements.** Si vous voyez des messages de conversation et de canal **Teams,** tout est prêt. Si ce n’est pas le cas, cliquez sur **Modifier.**

    > [!div class="mx-imgBorder"]
    > ![Emplacements pour la stratégie existante](../media/dlp-teams-editexistingpolicy.png)

4. Dans la **colonne État,** activer la stratégie pour les messages de conversation et **de canal Teams.**

    > [!div class="mx-imgBorder"]
    > ![DLP pour les conversations et les canaux Teams](../media/dlp-teams-addteamschatschannels.png)

5. Sous **l’onglet** Choisir des emplacements, conservez le paramètre par défaut de tous les comptes, ou sélectionnez **Choisir des emplacements spécifiques.** Vous pouvez spécifier :

    1. jusqu’à 1 000 comptes individuels à inclure ou à exclure
    1. listes de distribution et groupes de sécurité à inclure ou à exclure; **Il s’agit d’une fonctionnalité de prévisualisation publique.**
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**--> 
    
6. Sélectionnez **Suivant**.

7. Cliquez sur **Enregistrer**.

Laissez environ une heure à vos modifications pour qu’elles fonctionnent dans votre centre de données et se synchronisent avec les comptes d’utilisateurs.
<!-- again, why user accounts? -->

## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>Définir une nouvelle stratégie DLP pour Microsoft Teams

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Go to the Security & Compliance Center ( [https://protection.office.com](https://protection.office.com) ) and sign in.

2. Choisissez **stratégie de protection contre la perte**  >  **de**  >  **données + Créer une stratégie.**

3. Choisissez un [modèle,](data-loss-prevention-policies.md#dlp-policy-templates)puis choisissez **Suivant.**

    Dans notre exemple, nous avons choisi le modèle de données d’informations d’identification personnelle des États-Unis.

    > [!div class="mx-imgBorder"]
    > ![Modèle de confidentialité pour la stratégie DLP](../media/dlp-teams-createnewpolicy-template.png)<br/>

4. Sous **l’onglet Nom de votre stratégie,** spécifiez un nom et une description pour la stratégie, puis choisissez **Suivant**.

5. Sous **l’onglet** Choisir des emplacements, conservez le paramètre par défaut de tous les comptes, ou sélectionnez **Choisir des emplacements spécifiques.** Vous pouvez spécifier :

    1. jusqu’à 1 000 comptes individuels à inclure ou à exclure
    1. listes de distribution et groupes de sécurité à inclure ou à exclure; **Il s’agit d’une fonctionnalité de prévisualisation publique.**
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**-->  

    ![Emplacements de stratégie DLP](../media/dlp-teams-selectlocationsnewpolicy.png)

    > [!NOTE]
    > Si vous souhaitez vous assurer que les documents qui contiennent des informations sensibles ne sont pas partagés de manière inappropriée dans Teams, assurez-vous que les **sites SharePoint** et les comptes OneDrive sont **allumés,** ainsi que les messages de conversation et de canal **Teams.**

6. Sous **l’onglet Paramètres** de stratégie, sous Personnaliser le **type** de contenu à protéger, conservez les paramètres simples par défaut, ou choisissez Utiliser les **paramètres** avancés, puis choisissez **Suivant**. Si vous choisissez des paramètres avancés, vous pouvez créer ou modifier des règles pour votre stratégie. (Pour obtenir de l’aide, voir [Paramètres simples et paramètres avancés.)](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings)

7.  Sous **l’onglet Paramètres de stratégie,** sous Que voulez-vous faire si nous détectons des informations sensibles **?**, examinez les paramètres. (C’est ici que vous pouvez choisir de conserver les conseils de stratégie par défaut et les [notifications par](use-notifications-and-policy-tips.md)courrier électronique, ou de les personnaliser.)

    > [!div class="mx-imgBorder"]
    > ![Paramètres de stratégie DLP avec conseils et notifications](../media/dlp-teams-policysettings-tipsemails.png)

    Lorsque vous avez terminé de passer en revue ou de modifier les paramètres, choisissez **Suivant**.

8. Sous l’onglet **Paramètres** de stratégie, sous Voulez-vous activer la stratégie ou d’abord tester les éléments **?**, choisissez d’activer la [stratégie,](data-loss-prevention-policies.md#roll-out-dlp-policies-gradually-with-test-mode)de la tester en premier ou de la désactiver pour l’instant, puis choisissez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Spécifier s’il faut activer la stratégie](../media/dlp-teams-policysettings-turnonnow.png)

9. Sous **l’onglet Examiner vos paramètres,** examinez les paramètres de votre nouvelle stratégie. Sélectionnez **Modifier** pour apporter des modifications. Lorsque vous avez terminé, choisissez **Créer.**

Laissez environ une heure à votre nouvelle stratégie pour passer par votre centre de données et se synchroniser avec les comptes d’utilisateurs.

## <a name="prevent-external-access-to-sensitive-documents"></a>Empêcher l'accès externe aux documents sensibles

Pour vous assurer que les documents SharePoint qui contiennent des informations sensibles ne peuvent pas être accessibles par des invités externes à partir de SharePoint ou Teams par défaut, sélectionnez les éléments suivants :

- Vous pouvez vous assurer que les documents sont protégés jusqu’à ce que DLP analyse et les marque comme étant sûrs à partager en marquant les nouveaux fichiers comme sensibles [par défaut.](/sharepoint/sensitive-by-default)

- Structure de stratégie DLP recommandée

    - **Conditions**
        - Le contenu contient l’un de ces types d’informations sensibles : [Sélectionner tout ce qui s’applique]
        
        - Le contenu est partagé à partir de Microsoft 365 avec des personnes extérieures à mon organisation
        
          > [!div class="mx-imgBorder"]
          > ![Conditions DLP pour détecter le partage externe de contenu sensible](../media/dlp-teams-external-sharing/external-condition.png)

    - **Actions**
        - Restreindre l’accès au contenu pour utilisateurs externe
        
        - Informer les utilisateurs à l’aide de courriers électroniques et de conseils de stratégie
        
        - Envoyer des rapports d’incident à l’administrateur
        
        > [!div class="mx-imgBorder"]
        > ![Action DLP pour bloquer le partage externe de contenu sensible](../media/dlp-teams-external-sharing/external-action.png)

Stratégie DLP en action lors de la tentative de partage d’un document dans SharePoint qui contient des informations sensibles avec un invité externe :

> [!div class="mx-imgBorder"]
> ![Partage externe bloqué](../media/dlp-teams-external-sharing/external-sharing-blocked.png)


Stratégie DLP en action lorsque l’invité tente d’ouvrir un document dans Teams avec blocage externe :

> [!div class="mx-imgBorder"]
> ![Accès externe bloqué](../media/dlp-teams-external-sharing/external-access-blocked.png)

## <a name="related-articles"></a>Articles connexes

[Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)

[Envoi des notifications et affichage des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md)
