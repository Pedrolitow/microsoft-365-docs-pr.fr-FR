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
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
search.appverid:
- MET150
description: Les conversations et les canaux Microsoft Teams prennent en charge les stratégies de protection contre la perte de données (DLP).
ms.openlocfilehash: fa901a910cd49f1dd38a4b6fe3ca7908f9a67996
ms.sourcegitcommit: 0ad7edcfdcdd11d02fa8a14ffe4b36e120d92deb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2022
ms.locfileid: "68785636"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>Prévention des pertes de données et Microsoft Teams

Si votre organisation dispose de Protection contre la perte de données Microsoft Purview (DLP), vous pouvez définir des stratégies qui empêchent les utilisateurs de partager des informations sensibles dans un canal ou une session de conversation Microsoft Teams. Voici quelques exemples de fonctionnement de cette protection :

- **Exemple 1 : Protection des informations sensibles dans les messages**. Supposons qu’une personne tente de partager des informations sensibles dans une conversation ou un canal Teams avec des invités (utilisateurs externes). Si vous disposez d’une stratégie DLP définie pour empêcher cela, les messages contenant des informations sensibles qui sont envoyés aux utilisateurs externes sont supprimés. Cela se produit automatiquement et en quelques secondes, en fonction de la façon dont votre stratégie DLP est configurée.

    > [!NOTE]
    > DLP pour Microsoft Teams bloque le contenu sensible lorsqu’il est partagé avec les utilisateurs Microsoft Teams qui ont :<br/>- [accès invité](/MicrosoftTeams/guest-access) dans les équipes et les canaux ; Ou<br/>- [accès externe](/MicrosoftTeams/manage-external-access) dans les réunions et les sessions de conversation. <p>DLP pour les sessions de conversation externes ne fonctionne que si l’expéditeur et le destinataire sont en mode Teams uniquement et utilisant la [fédération native De Microsoft Teams](/microsoftteams/manage-external-access). DLP pour Teams ne bloque pas les messages dans [l’interopérabilité](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) avec Skype Entreprise ou les sessions de conversation fédérées non natives.

- **Exemple 2 : Protection des informations sensibles dans les documents**. Supposons qu’une personne tente de partager un document avec des invités dans un canal ou une conversation Microsoft Teams, et que le document contient des informations sensibles. Si vous avez défini une stratégie DLP pour éviter cela, le document ne s’ouvre pas pour ces utilisateurs. Votre stratégie DLP doit inclure SharePoint et OneDrive pour que la protection soit en place. Il s’agit d’un exemple de DLP pour SharePoint qui s’affiche dans Microsoft Teams et, par conséquent, exige que les utilisateurs disposent d’une licence pour Office 365 DLP (inclus dans Office 365 E3), mais ne nécessite pas que les utilisateurs disposent d’une licence pour Conformité avancée Office 365. 
   
Vous pouvez étendre la stratégie DLP Teams pour couvrir SharePoint Online et OneDrive Entreprise en sélectionnant **Protection automatique des fichiers** dans la bannière dans **Stratégies** **DLP** > . Cela permet d’activer la protection DLP pour tous les fichiers partagés dans les conversations et les canaux Teams avec les mêmes règles que celles qui s’appliquent aux messages Teams. Une fois activée, l’extension s’applique à toutes les stratégies DLP Teams existantes et futures. Vous n’avez donc pas besoin de créer des stratégies distinctes pour SharePoint et OneDrive pour la protection des fichiers. 

> [!NOTE]
> Seules les stratégies Teams qui ont des règles avec des conditions ou des exceptions de **contenu ou** de **contenu partagé à partir de Microsoft 365** peuvent être étendues pour la protection automatique des fichiers. Si la configuration de la condition ou de l’exception a **la valeur Expéditeur est**, **le domaine de l’expéditeur** est, **le destinataire est** et le **domaine du destinataire est** présent, l’action d’extension échoue, car ces conditions ne s’appliquent pas à SharePoint et OneDrive.

- **Exemple 3 : Protection des communications dans les canaux partagés Teams**. Pour les canaux partagés, la stratégie DLP de l’équipe Teams hôte est appliquée. Par exemple, supposons qu’il existe un canal partagé appartenant à TeamA de Contoso. TeamA a une stratégie DLP P1. Il existe 3 façons de partager un canal :
    - **Partager avec un membre** : vous invitez user1 à partir de Contoso à rejoindre le canal partagé sans en faire un membre de TeamA. Tous les utilisateurs de ce canal partagé, y compris user1, seront couverts par P1.
    - **Partager avec l’équipe (en interne)** : vous partagez le canal avec une autre équipe TeamB dans Contoso. Une autre équipe peut avoir une stratégie DLP différente, mais cela n’a pas d’importance. P1 s’applique à tous les utilisateurs de ce canal partagé, y compris les utilisateurs TeamA et TeamB.
    - **Partager avec l’équipe (interlocataire)** : vous partagez le canal avec une équipe TeamF dans Fabrikam. Fabrikam peut avoir sa propre stratégie DLP, mais cela n’a pas d’importance. P1 s’applique à tous les utilisateurs de ce canal partagé, y compris les utilisateurs TeamA (Contoso) et TeamF (Fabrikam).
 
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="dlp-licensing-for-microsoft-teams"></a>Gestion des licences DLP pour Microsoft Teams

Les fonctionnalités de [protection contre la perte de données](dlp-learn-about-dlp.md) incluent les messages de conversation et de canal Microsoft Teams, **y compris les messages de canal privé** pour :

- Office 365 E5/A5/G5
- Microsoft 365 E5/A5/G5
- Microsoft 365 E5/A5/G5 Information Protection et gouvernance
- Conformité Microsoft 365 E5/A5/G5/F5 et conformité & de sécurité F5

Office 365 et Microsoft 365 E3 incluent la protection DLP pour SharePoint Online, OneDrive et Exchange Online. Cela inclut également les fichiers partagés via Teams, car Teams utilise SharePoint Online et OneDrive pour partager des fichiers.

La prise en charge de la protection DLP dans Teams Chat nécessite E5.

Pour en savoir plus sur les conditions d’octroi de licences, consultez [Conseils sur la gestion des licences des services de niveau client de Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

> [!IMPORTANT]
> La protection contre la perte de données s’applique uniquement aux messages réels dans le thread de conversation ou de canal. Les notifications d’activité, qui incluent un aperçu court des messages et qui s’affichent en fonction des paramètres de notification d’un utilisateur, **ne sont pas** incluses dans Teams DLP. Toutes les informations sensibles présentes dans la partie du message qui apparaît dans l’aperçu restent visibles dans la notification même après l’application de la stratégie DLP et la suppression des informations sensibles du message lui-même.

## <a name="scope-of-dlp-protection"></a>Étendue de la protection DLP

La protection DLP est appliquée différemment aux entités Teams.

|Quand la stratégie est délimitée par |Ces entités Teams |La protection DLP sera disponible|
|---------|---------|---------|
|Comptes d’utilisateur individuels     |1:1/n conversations         |Oui         |
|     |Messages de canal standard et partagés         |Non         |
|     |Messages de canal privé         |Oui         |
|Groupes de sécurité/listes de distribution  | 1:1/n conversations         |Oui         |
|     |Messages de canal standard et partagés  |Non         |
|     |Messages de canal privé         |Oui        |
|Groupe Microsoft 365    |1:1/n conversations          |Non         |
|     |Messages de canal standard et partagés          |Oui        |
|     |Messages de canal privé|Non| 


## <a name="policy-tips-help-educate-users"></a>Des conseils de stratégie aident à éduquer les utilisateurs

À l’instar du fonctionnement de DLP dans [Exchange, Outlook, Outlook sur le web](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web), [SharePoint Online, les sites OneDrive Entreprise](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites) et les clients de [bureau Office](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs), des conseils de stratégie s’affichent lorsqu’une action se déclenche avec une stratégie DLP. Voici un exemple de conseil de stratégie :

![Notification de message bloqué dans Teams.](../media/dlp-teams-blockedmessage-notification.png)

Ici, l’expéditeur a tenté de partager un numéro de sécurité sociale dans un canal Microsoft Teams. Le lien **Que puis-je faire ?** ouvre une boîte de dialogue qui fournit des options permettant à l’expéditeur de résoudre le problème. Notez que l’expéditeur peut choisir de remplacer la stratégie ou d’avertir un administrateur de la réviser et de la résoudre.

![Options pour résoudre le message bloqué.](../media/dlp-teams-blockedmessage-possibleactions.png)

Dans votre organisation, vous pouvez choisir d’autoriser les utilisateurs à remplacer une stratégie DLP. Lorsque vous configurez vos stratégies DLP, vous pouvez utiliser les conseils de stratégie par défaut ou [personnaliser les conseils de stratégie](#to-customize-policy-tips) pour votre organisation.

Pour revenir à notre exemple, où un expéditeur a partagé un numéro de sécurité sociale dans un canal Teams, voici ce que le destinataire a vu :

> [!div class="mx-imgBorder"]
> ![Message bloqué.](../media/dlp-teams-blockedmessage-notification-to-user.png)

### <a name="to-customize-policy-tips"></a>Pour personnaliser les conseils de stratégie

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Accédez au Centre de conformité Purview ([https://compliance.microsoft.com](https://compliance.microsoft.com)) et connectez-vous.

2. Cliquez sur **Protection contre la perte de données** > **(Stratégie)**.

3. Sélectionnez une stratégie, puis en regard de **Paramètres de** stratégie, choisissez **Modifier**.

4. Créez une règle ou modifiez une règle existante pour la stratégie.

5. Sous **l’onglet Notifications utilisateur** , sélectionnez **Personnaliser le texte de l’e-mail** et/ou **Personnaliser les options de texte de conseil de stratégie** .

6. Spécifiez le texte que vous souhaitez utiliser pour les notifications par e-mail et/ou les conseils de stratégie, puis choisissez **Enregistrer**.

7. Sous l’onglet **Paramètres de** stratégie, choisissez **Enregistrer**.

Prévoyez environ une heure pour que vos modifications fonctionnent dans votre centre de données et se synchronisent avec les comptes d’utilisateur.
 <!-- why are these syncing to user accounts? -->

## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>Ajouter Microsoft Teams comme emplacement aux stratégies DLP existantes

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Accédez au Centre de conformité ([https://compliance.microsoft.com](https://compliance.microsoft.com)) et connectez-vous.

2. Cliquez sur **Protection contre la perte de données** > **(Stratégie)**.

3. Sélectionnez une stratégie et examinez les valeurs sous **Emplacements**. Si vous voyez **des messages de conversation et de canal Teams**, vous êtes prêt. Si ce n’est pas le cas, cliquez sur **Modifier**.

4. Dans la colonne **État** , activez la stratégie pour les **messages de conversation et de canal Teams**.

5. Sous l’onglet **Choisir des emplacements** , conservez le paramètre par défaut de tous les comptes ou sélectionnez **Me laisser choisir des emplacements spécifiques**. Vous pouvez spécifier :

    1. Jusqu’à 1 000 comptes individuels à inclure ou à exclure
    1. Listes de distribution et groupes de sécurité (avec messagerie activée) à inclure ou à exclure. 
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**--> 
    
6. Sélectionnez **Suivant**.

7. Cliquez sur **Enregistrer**.

Prévoyez environ une heure pour que vos modifications fonctionnent dans votre centre de données et se synchronisent avec les comptes d’utilisateur.
<!-- again, why user accounts? -->

## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>Définir une nouvelle stratégie DLP pour Microsoft Teams

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Accédez au Centre de conformité ([https://compliance.microsoft.com](https://compliance.microsoft.com)) et connectez-vous.

2. Cliquez sur **Protection contre la perte de données** > **(Stratégie)** > **+ Créer une stratégie**.

3. Choisissez un [modèle](data-loss-prevention-policies.md#dlp-policy-templates), **puis suivant.**

    Dans notre exemple, nous avons choisi le modèle données d’identification personnelle des États-Unis.

4. Sous l’onglet **Nommez votre stratégie** , spécifiez un nom et une description pour la stratégie, puis choisissez **Suivant**.

5. Sous l’onglet **Choisir des emplacements** , conservez le paramètre par défaut de tous les comptes ou sélectionnez **Me laisser choisir des emplacements spécifiques**. Vous pouvez spécifier :

    1. Jusqu’à 1 000 comptes individuels à inclure ou à exclure
    1. Listes de distribution et groupes de sécurité à inclure ou exclure. **Il s’agit d’une fonctionnalité en préversion publique.**
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**-->  

 
    > [!NOTE]
    > Si vous souhaitez vous assurer que les documents qui contiennent des informations sensibles ne sont pas partagés de manière inappropriée dans Teams, assurez-vous que les **sites SharePoint** et les **comptes OneDrive** sont activés, ainsi que les **messages de conversation et de canal Teams**.

6. Sous l’onglet **Paramètres de** stratégie, sous **Personnaliser le type de contenu que vous souhaitez protéger**, conservez les paramètres simples par défaut, ou choisissez **Utiliser les paramètres avancés**, **puis suivant.** Si vous choisissez des paramètres avancés, vous pouvez créer ou modifier des règles pour votre stratégie. Pour obtenir de l’aide à ce sujet, consultez [Paramètres simples et paramètres avancés](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings).

7.  Sous l’onglet **Paramètres de** stratégie, sous **Que voulez-vous faire si nous détectons des informations sensibles ?**, passez en revue les paramètres. Voici où vous pouvez choisir de conserver les [conseils de stratégie par défaut et les notifications par e-mail](use-notifications-and-policy-tips.md), ou de les personnaliser.



    Lorsque vous avez terminé d’examiner ou de modifier les paramètres, choisissez **Suivant**.

8. Sous l’onglet **Paramètres de** stratégie, sous **Voulez-vous activer la stratégie ou tester d’abord les éléments ?**, choisissez d’activer la stratégie, de la [tester en premier](dlp-overview-plan-for-dlp.md#policy-deployment) ou de la désactiver pour l’instant, puis choisissez **Suivant**.

9. Sous l’onglet **Vérifier vos paramètres** , passez en revue les paramètres de votre nouvelle stratégie. Choisissez **Modifier** pour apporter des modifications. Lorsque vous avez terminé, choisissez **Créer**.

Prévoyez environ une heure pour que votre nouvelle stratégie fonctionne dans votre centre de données et se synchronise avec les comptes d’utilisateur.

## <a name="prevent-external-access-to-sensitive-documents"></a>Empêcher l'accès externe aux documents sensibles

Pour vous assurer que les documents SharePoint qui contiennent des informations sensibles ne sont pas accessibles par les invités externes à partir de SharePoint ou teams par défaut, sélectionnez les éléments suivants :

- Vous pouvez vous assurer que les documents sont protégés jusqu’à ce que DLP les analyse et les marque comme étant sûrs à partager en [marquant les nouveaux fichiers comme sensibles par défaut](/sharepoint/sensitive-by-default).

- Structure de stratégie DLP recommandée

    - **Conditions**
        - Le contenu contient l’un des types d’informations sensibles suivants : [Sélectionner tout ce qui s’applique]
        
        - Le contenu est partagé à partir de Microsoft 365 avec des personnes extérieures à mon organisation
        
          > [!div class="mx-imgBorder"]
          > ![Conditions DLP pour détecter le partage externe de contenu sensible.](../media/dlp-teams-external-sharing/external-condition.png)

    - **Actions**
        - Restreindre l’accès au contenu pour utilisateurs externe
        
        - Informer les utilisateurs à l’aide de courriers électroniques et de conseils de stratégie
        
        - Envoyer des rapports d’incident à l’administrateur
        
        > [!div class="mx-imgBorder"]
        > ![Action DLP pour bloquer le partage externe de contenu sensible.](../media/dlp-teams-external-sharing/external-action.png)

Stratégie DLP en action lors de la tentative de partage d’un document dans SharePoint qui contient des informations sensibles avec un invité externe :

> [!div class="mx-imgBorder"]
> ![Partage externe bloqué.](../media/dlp-teams-external-sharing/external-sharing-blocked.png)

<!--DLP policy in action when guest attempts to open a document in Teams with block external:
can't use the below image it contains a non-approved name.
> [!div class="mx-imgBorder"]
> ![External access blocked.](../media/dlp-teams-external-sharing/external-access-blocked.png)-->

## <a name="related-articles"></a>Articles connexes

- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Envoi des notifications et affichage des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md)
