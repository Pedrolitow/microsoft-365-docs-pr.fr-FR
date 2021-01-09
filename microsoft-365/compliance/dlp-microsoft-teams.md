---
title: Protection contre la perte de données et Microsoft Teams
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
ms.openlocfilehash: 25ba5850f496c188c2a38d6cc5b68960a85e5e5f
ms.sourcegitcommit: 7d4aa58ae9fc893825b6e648fa3f072c3ac59628
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2021
ms.locfileid: "49790158"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>Protection contre la perte de données et Microsoft Teams

> [!NOTE]
> Des fonctionnalités de protection contre la perte de données ont été récemment ajoutées aux messages de conversation et de canal Microsoft Teams pour les utilisateurs titulaires d’une licence Office 365 E5/A5, Microsoft 365 E5/A5, Microsoft 365 Information Protection and Governance ou Office 365 Advanced Compliance. Office 365 et Microsoft 365 E3 incluent la protection DLP pour SharePoint Online, OneDrive et Exchange Online. Cela inclut également les fichiers partagés via Teams, car Teams utilise SharePoint Online et OneDrive pour partager des fichiers.
La prise en charge de la protection DLP dans Teams Chat nécessite E5.
Pour en savoir plus sur les conditions d’octroi de licences, consultez [Conseils sur la gestion des licences des services de niveau client de Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).

> [!IMPORTANT]
> La DLP pour Teams n’est prise en charge que lorsque l’utilisateur dispose d’une boîte aux lettres dans Exchange Online.

## <a name="overview-of-dlp-for-microsoft-teams"></a>Vue d’ensemble de la DLP pour Microsoft Teams

Récemment, [les fonctionnalités de](data-loss-prevention-policies.md) protection contre la perte de données (DLP) ont été étendues pour inclure les messages de conversation et de canal Microsoft Teams, y compris les messages de canal **privé.**


Si votre organisation dispose d’une DLP, vous pouvez désormais définir des stratégies qui empêchent les personnes de partager des informations sensibles dans un canal ou une session de conversation Microsoft Teams. Voici quelques exemples de fonctionnement de cette protection :

- **Exemple 1 : protection des informations sensibles dans les messages**. Supposons qu’une personne tente de partager des informations sensibles dans une conversation ou un canal Teams avec des invités (utilisateurs externes). Si vous avez défini une stratégie DLP pour éviter cela, les messages avec des informations sensibles envoyés à des utilisateurs externes sont supprimés. Cela se produit automatiquement et en quelques secondes, en fonction de la configuration de votre stratégie DLP.

    > [!NOTE]
    > DLP pour Microsoft Teams bloque le contenu sensible lorsqu’il est partagé avec des utilisateurs de Microsoft Teams qui ont :<br/>- [accès invité dans](https://docs.microsoft.com/MicrosoftTeams/guest-access) les équipes et les canaux ; ou<br/>- [accès externe](https://docs.microsoft.com/MicrosoftTeams/manage-external-access) dans les réunions et les sessions de conversation. <p>La DLP pour les sessions de conversation externe ne fonctionne que si l’expéditeur et le destinataire sont en mode Teams uniquement et utilisent [la fédération native de Microsoft Teams.](https://docs.microsoft.com/microsoftteams/manage-external-access) DLP pour Teams ne bloque pas les messages en [cas d’interaction](https://docs.microsoft.com/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) avec Skype Entreprise ou les sessions de conversation fédérée non natives.

- **Exemple 2 : protection des informations sensibles dans les documents**. Supposons qu’une personne tente de partager un document avec des invités dans un canal ou une conversation Microsoft Teams, et que le document contient des informations sensibles. Si vous avez défini une stratégie DLP pour éviter cela, le document ne s’ouvre pas pour ces utilisateurs. Notez que dans ce cas, votre stratégie DLP doit inclure SharePoint et OneDrive pour que la protection soit en place. (Il s’agit d’un exemple de DLP pour SharePoint qui s’affiche dans Microsoft Teams, et par conséquent nécessite que les utilisateurs soient titulaires d’une licence pour Office 365 DLP (inclus dans Office 365 E3), mais ne nécessite pas que les utilisateurs soient titulaires d’une licence pour Office 365 Conformité avancée.)

## <a name="policy-tips-help-educate-users"></a>Les conseils de stratégie aident à former les utilisateurs

De la même manière que dans [Exchange, Outlook, Outlook](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web)sur le [web, SharePoint Online,](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites)les sites OneDrive Entreprise et les clients de bureau [Office,](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs)des conseils de stratégie s’affichent lorsqu’une action entre en conflit avec une stratégie DLP. Voici un exemple de conseil de stratégie :

![Notification de message bloqué dans Teams](../media/dlp-teams-blockedmessage-notification.png)

Dans ce cas, l’expéditeur a tenté de partager un numéro de sécurité sociale dans un canal Microsoft Teams. Le **lien Que puis-je faire ?** ouvre une boîte de dialogue qui fournit des options à l’expéditeur pour résoudre le problème. Notez que dans ce cas, l’expéditeur peut choisir de remplacer la stratégie ou d’avertir un administrateur de la réviser et de la résoudre.

![Options pour résoudre le message bloqué](../media/dlp-teams-blockedmessage-possibleactions.png)

Dans votre organisation, vous pouvez choisir d’autoriser les utilisateurs à remplacer une stratégie DLP. De plus, lorsque vous configurez vos stratégies DLP, vous pouvez utiliser les conseils de stratégie par défaut ou personnaliser les conseils de stratégie [pour](#to-customize-policy-tips) votre organisation.

Pour revenir à notre exemple, où un expéditeur a partagé un numéro de sécurité sociale dans un canal Teams, voici ce que le destinataire a vu :

![Message bloqué](../media/dlp-teams-blockedmessage-notification-to-user.png)

Le **lien Qu’est-ce que c’est ?** ouvre un [article](data-loss-prevention-policies.md) sur les stratégies DLP, qui explique pourquoi le message a été bloqué.

### <a name="to-customize-policy-tips"></a>Pour personnaliser les conseils de stratégie

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Go to the Security & Compliance Center ( [https://protection.office.com](https://protection.office.com) ) and sign in.

2. Choisissez **la stratégie de protection contre la perte de**  >  **données.**

3. Select a policy, and next to **Policy settings**, choose **Edit**.

4. Créez une règle ou modifiez une règle existante pour la stratégie.<br/>![Modification d’une règle pour une stratégie](../media/dlp-teams-editrule.png)<br/>

5. Sous **l’onglet Notifications de** l’utilisateur, sélectionnez Personnaliser le texte **du message** électronique et/ou personnaliser les options de texte du **conseil de** stratégie.<br/>![Personnaliser les notifications utilisateur et les conseils de stratégie](../media/dlp-teams-editrule-usernotifications.png)<br/>  

6. Spécifiez le texte que vous souhaitez utiliser pour les notifications par courrier électronique et/ou les conseils de stratégie, puis sélectionnez **Enregistrer**.

7. Sous **l’onglet Paramètres de stratégie,** sélectionnez **Enregistrer.**

Laissez environ une heure à vos modifications pour qu’elles fonctionnent dans votre centre de données et se synchronisent avec les comptes d’utilisateurs.
 <!-- why are these syncing to user accounts? -->

## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>Ajouter Microsoft Teams en tant qu’emplacement aux stratégies DLP existantes

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Go to the Security & Compliance Center ( [https://protection.office.com](https://protection.office.com) ) and sign in.

2. Choisissez **la stratégie de protection contre la perte de**  >  **données.**

3. Sélectionnez une stratégie et regardez les valeurs sous **Emplacements.** Si vous voyez des messages de conversation et de canal **Teams,** tout est prêt. Si ce n’est pas le cas, cliquez sur **Modifier.**<br/>![Emplacements pour la stratégie existante](../media/dlp-teams-editexistingpolicy.png)<br/>

4. Dans la **colonne État,** activer la stratégie pour les messages de conversation et **de canal Teams.**<br/>![DLP pour les conversations et les canaux Teams](../media/dlp-teams-addteamschatschannels.png)<br/>

5. Sous  l’onglet Choisir des emplacements, conservez  le paramètre par défaut de tous les comptes, ou sélectionnez Choisir des emplacements spécifiques et spécifier les comptes, les listes de distribution ou les groupes de sécurité à inclure et à exclure. Sélectionnez **Suivant**.

6. Cliquez sur **Enregistrer**.

Laissez environ une heure à vos modifications pour qu’elles fonctionnent dans votre centre de données et se synchronisent avec les comptes d’utilisateurs.
<!-- again, why user accounts? -->

## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>Définir une nouvelle stratégie DLP pour Microsoft Teams

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Go to the Security & Compliance Center ( [https://protection.office.com](https://protection.office.com) ) and sign in.

2. Choisissez **stratégie de protection contre la perte**  >  **de**  >  **données + Créer une stratégie.**

3. Choisissez un [modèle,](data-loss-prevention-policies.md#dlp-policy-templates)puis choisissez **Suivant.**<br/>Dans notre exemple, nous avons choisi le modèle de données d’informations d’identification personnelle des États-Unis.<br/>![Modèle de confidentialité pour la stratégie DLP](../media/dlp-teams-createnewpolicy-template.png)<br/>

4. Sous **l’onglet Nom de votre stratégie,** spécifiez un nom et une description pour la stratégie, puis choisissez **Suivant**.

5. Sous  l’onglet Choisir des emplacements, conservez  le paramètre par défaut de tous les comptes, ou sélectionnez Choisir des emplacements spécifiques et spécifier les comptes, les listes de distribution ou les groupes de sécurité à inclure et à exclure. Sélectionnez **Suivant**.

![Emplacements de stratégie DLP](../media/dlp-teams-selectlocationsnewpolicy.png)

> [!NOTE]
> Si vous souhaitez vous assurer que les documents qui contiennent des informations sensibles ne sont pas partagés de manière inappropriée dans Teams, assurez-vous que les **sites SharePoint** et les comptes OneDrive sont **allumés,** ainsi que les messages de conversation et de canal **Teams.**


6. Sous **l’onglet Paramètres** de stratégie, sous Personnaliser le **type** de contenu que vous souhaitez protéger, conservez les paramètres simples par défaut, ou choisissez Utiliser les **paramètres** avancés, puis choisissez **Suivant**. Si vous choisissez des paramètres avancés, vous pouvez créer ou modifier des règles pour votre stratégie. (Pour obtenir de l’aide, voir [Paramètres simples et paramètres avancés.)](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings)

7.  Sous **l’onglet Paramètres de stratégie,** sous Que voulez-vous faire si nous détectons des informations sensibles **?**, examinez les paramètres. (C’est ici que vous pouvez choisir de conserver les conseils de stratégie par défaut et les [notifications par](use-notifications-and-policy-tips.md)courrier électronique, ou de les personnaliser.)<br/>![Paramètres de stratégie DLP avec conseils et notifications](../media/dlp-teams-policysettings-tipsemails.png)<br/>Lorsque vous avez terminé de passer en revue ou de modifier les paramètres, choisissez **Suivant**.

8. Sous l’onglet **Paramètres** de stratégie, sous Voulez-vous activer la stratégie ou d’abord tester les éléments **?**, choisissez d’activer la [stratégie,](data-loss-prevention-policies.md#roll-out-dlp-policies-gradually-with-test-mode)de la tester en premier ou de la maintenir désactivée pour l’instant, puis choisissez **Suivant.**<br/>![Spécifier s’il faut activer la stratégie](../media/dlp-teams-policysettings-turnonnow.png)<br/>

9. Sous **l’onglet Examiner vos paramètres,** examinez les paramètres de votre nouvelle stratégie. Sélectionnez **Modifier** pour apporter des modifications. Lorsque vous avez terminé, choisissez **Créer.**

Laissez environ une heure à votre nouvelle stratégie pour passer par votre centre de données et se synchroniser avec les comptes d’utilisateurs.

## <a name="prevent-external-access-to-sensitive-documents"></a>Empêcher l’accès externe aux documents sensibles

Pour vous assurer que les documents SharePoint qui contiennent des informations sensibles ne sont pas accessibles par des invités externes à partir de SharePoint ou Teams par défaut, sélectionnez les éléments suivants :

- Vous pouvez vous assurer que les documents sont protégés jusqu’à ce que DLP analyse et les marque comme étant sûrs à partager en marquant les nouveaux fichiers comme sensibles [par défaut.](https://docs.microsoft.com/sharepoint/sensitive-by-default)
- Structure de stratégie DLP recommandée
    - **Conditions**
        - Le contenu contient l’un de ces types d’informations sensibles : [Sélectionner tout ce qui s’applique]
        - Le contenu est partagé à partir de Microsoft 365 avec des personnes extérieures à mon organisation
        <br/>![Conditions DLP pour détecter le partage externe de contenu sensible](../media/dlp-teams-external-sharing/external-condition.png)<br/>


    - **Actions**
        - Restreindre l’accès au contenu pour les utilisateurs externes
        - Avertir les utilisateurs par courrier électronique et conseils de stratégie
        - Envoyer des rapports d’incident à l’administrateur    
        <br/>![Action DLP pour bloquer le partage externe de contenu sensible](../media/dlp-teams-external-sharing/external-action.png)<br/>

Stratégie DLP en action lors de la tentative de partage d’un document dans SharePoint qui contient des informations sensibles avec un invité externe :
<br/>![Partage externe bloqué](../media/dlp-teams-external-sharing/external-sharing-blocked.png)<br/>


Stratégie DLP en action lorsque l’invité tente d’ouvrir un document dans Teams avec blocage externe :
<br/>![Accès externe bloqué](../media/dlp-teams-external-sharing/external-access-blocked.png)<br/>

## <a name="related-articles"></a>Articles connexes

[Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)

[Envoi des notifications et affichage des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md)
