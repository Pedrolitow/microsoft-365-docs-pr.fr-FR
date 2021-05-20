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
description: Vous pouvez désormais appliquer les stratégies DLP aux Microsoft Teams chats et canaux. Lisez cet article pour en savoir plus sur son fonctionnement.
ms.openlocfilehash: 9fdce86473dcfbb7ec75b9d371b8782d4141ef57
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572464"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>Prévention des pertes de données et Microsoft Teams

> [!NOTE]
> Des capacités de prévention des pertes de données ont récemment été ajoutées à Microsoft Teams de chat et de messages de canaux pour les utilisateurs titulaires d’une licence pour les Office 365 E5/A5, Microsoft 365 E5/A5, Microsoft 365 Information Protection and Governance ou Conformité avancée Office 365. Office 365 et Microsoft 365 E3 comprennent la protection DLP pour les SharePoint en ligne, OneDrive et Exchange Online. Cela inclut également les fichiers qui sont partagés par Teams parce que Teams utilise SharePoint en ligne et OneDrive pour partager des fichiers.
La prise en charge de la protection DLP Teams chat nécessite E5.
Pour en savoir plus sur les conditions d’octroi de licences, consultez [Conseils sur la gestion des licences des services de niveau client de Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).

## <a name="overview-of-dlp-for-microsoft-teams"></a>Aperçu du DLP pour Microsoft Teams

Récemment, les [capacités de prévention des](dlp-learn-about-dlp.md) pertes de données ont été étendues pour inclure Microsoft Teams chat et les messages de canal, y **compris les messages des chaînes privées**. 

> [!IMPORTANT]
> DLP ne s’applique actuellement qu’aux messages réels dans le chat ou le thread de canal. Les notifications d’activité -- qui incluent un aperçu court de message et apparaissent en fonction des paramètres de notification d’un utilisateur -- ne **sont** pas incluses dans Teams DLP pour le moment. Toutes les informations sensibles présentes dans la partie du message qui apparaît dans l’aperçu resteront visibles dans la notification même après l’application de la stratégie DLP et supprimeront les informations sensibles du message lui-même.

Si votre organisation dispose de DLP, vous pouvez désormais définir des stratégies qui empêchent les gens de partager des informations sensibles dans un canal Microsoft Teams ou une session de chat. Voici quelques exemples du fonctionnement de cette protection :

- **Exemple 1 : Protection des informations sensibles dans les messages**. Supposons que quelqu’un tente de partager des informations sensibles dans Teams chat ou un canal avec des invités (utilisateurs externes). Si vous avez défini une stratégie DLP pour empêcher cela, les messages avec des informations sensibles qui sont envoyées aux utilisateurs externes sont supprimés. Cela se produit automatiquement, et en quelques secondes, selon la façon dont votre stratégie DLP est configurée.

    > [!NOTE]
    > DLP pour les Microsoft Teams contenu sensible lorsqu’il est partagé avec Microsoft Teams utilisateurs qui ont :<br/>- [l’accès des](/MicrosoftTeams/guest-access) invités dans les équipes et les canaux; ou<br/>- [l’accès externe](/MicrosoftTeams/manage-external-access) aux réunions et aux sessions de chat. <p>DLP pour les sessions de chat externes ne fonctionnera que si l’expéditeur et le récepteur sont en mode Teams only et [en utilisant Microsoft Teams fédération native](/microsoftteams/manage-external-access). DLP pour Teams bloque pas les messages [en interop avec](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) des sessions de chat fédérées Skype Entreprise ou non natives.

- **Exemple 2 : Protection des informations sensibles dans les documents**. Supposons que quelqu’un tente de partager un document avec des invités dans un Microsoft Teams ou un chat, et le document contient des informations sensibles. Si vous avez défini une stratégie DLP pour empêcher cela, le document ne s’ouvrira pas pour ces utilisateurs. Notez que dans ce cas, votre police DLP doit inclure SharePoint et OneDrive afin que la protection soit en place. (Il s’agit d’un exemple de DLP pour SharePoint qui apparaît en Microsoft Teams, et exige donc que les utilisateurs sont autorisés pour Office 365 DLP (inclus dans Office 365 E3), mais n’exige pas que les utilisateurs soient autorisés pour Conformité avancée Office 365.)

## <a name="policy-tips-help-educate-users"></a>Conseils politiques aider à éduquer les utilisateurs

Comme dans le cas de DLP [dans les Exchange, Outlook, Outlook sur le Web,](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web) [SharePoint Online, OneDrive Entreprise sites](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites)et Office clients de [bureau, des conseils](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs)de stratégie apparaissent lorsqu’une action entre en conflit avec une stratégie DLP. Voici un exemple d’un conseil de politique :

![Notification de message bloquée dans Teams](../media/dlp-teams-blockedmessage-notification.png)

Dans ce cas, l’expéditeur a tenté de partager un numéro de sécurité sociale dans un Microsoft Teams chaîne. Le **lien Que puis-je faire ?** ouvre une boîte de dialogue qui fournit des options à l’expéditeur pour résoudre le problème. Notez que dans ce cas, l’expéditeur peut choisir de passer outre à la stratégie, ou aviser un administrateur de l’examiner et de le résoudre.

![Options pour résoudre le message bloqué](../media/dlp-teams-blockedmessage-possibleactions.png)

Dans votre organisation, vous pouvez choisir de permettre aux utilisateurs de passer outre à une stratégie DLP. De plus, lorsque vous configurez vos stratégies DLP, vous pouvez utiliser les conseils de stratégie par défaut ou [personnaliser des conseils de stratégie](#to-customize-policy-tips) pour votre organisation.

Pour en revenir à notre exemple, où un expéditeur a partagé un numéro de sécurité sociale dans un canal Teams, voici ce que le destinataire a vu :

> [!div class="mx-imgBorder"]
> ![Message bloqué](../media/dlp-teams-blockedmessage-notification-to-user.png)

### <a name="to-customize-policy-tips"></a>Pour personnaliser les conseils de stratégie

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Rendez-vous au Centre & sécurité [https://protection.office.com](https://protection.office.com) () et connectez-vous.

2. Choisissez la **politique de prévention des pertes** de  >  **données**.

3. Sélectionnez une stratégie, et à côté des **paramètres de stratégie,** choisissez **Modifier**.

4. Créez une nouvelle règle ou modifiez une règle existante pour la stratégie.

    > [!div class="mx-imgBorder"]
    > ![Modification d’une règle pour une politique](../media/dlp-teams-editrule.png)

5. Sur **l’onglet Notifications utilisateur,** sélectionnez **Personnaliser le texte de l’e-mail** et/ou **personnalisez les** options de texte de la pointe de stratégie.

    > [!div class="mx-imgBorder"]
    > ![Personnaliser les notifications des utilisateurs et les conseils de stratégie](../media/dlp-teams-editrule-usernotifications.png)<br/>  

6. Spécifiez le texte que vous souhaitez utiliser pour les notifications par e-mail et/ou les conseils de stratégie, puis choisissez **Enregistrer**.

7. Sur **l’onglet Paramètres de** stratégie, choisissez **Enregistrer**.

Prévoyez environ une heure pour que vos modifications se passent à travers votre centre de données et se synchronisent avec les comptes des utilisateurs.
 <!-- why are these syncing to user accounts? -->

## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>Ajouter Microsoft Teams comme emplacement aux stratégies DLP existantes

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Rendez-vous au Centre & sécurité [https://protection.office.com](https://protection.office.com) () et connectez-vous.

2. Choisissez la **politique de prévention des pertes** de  >  **données**.

3. Sélectionnez une stratégie et examinez les valeurs sous **Emplacements**. Si vous voyez **Teams de chat et de canaux,** vous êtes tous prêts. Si vous ne le faites pas, cliquez sur **Modifier**.

    > [!div class="mx-imgBorder"]
    > ![Emplacements de la politique existante](../media/dlp-teams-editexistingpolicy.png)

4. Dans la **colonne Statut,** activez la stratégie pour les **messages Teams chat et de canal**.

    > [!div class="mx-imgBorder"]
    > ![DLP pour les chats Teams les canaux](../media/dlp-teams-addteamschatschannels.png)

5. Sur **l’onglet Choisir les** emplacements, conserver le paramètre par défaut de tous les comptes, ou **sélectionnez Laissez-moi choisir des emplacements spécifiques**. Vous pouvez spécifier :

    1. jusqu’à 1000 comptes individuels à inclure ou à exclure
    1. listes de distribution et groupes de sécurité à inclure ou à exclure. 
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**--> 
    
6. Sélectionnez **Suivant**.

7. Cliquez sur **Enregistrer**.

Prévoyez environ une heure pour que vos modifications se passent à travers votre centre de données et se synchronisent avec les comptes des utilisateurs.
<!-- again, why user accounts? -->

## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>Définir une nouvelle stratégie DLP pour Microsoft Teams

Pour effectuer cette tâche, vous devez avoir un rôle qui dispose des autorisations pour modifier les stratégies DLP. Pour en savoir plus, voir [Autorisations](data-loss-prevention-policies.md#permissions).

1. Rendez-vous au Centre & sécurité [https://protection.office.com](https://protection.office.com) () et connectez-vous.

2. Choisissez la **politique de prévention des** pertes  >  **de** données + Créez une  >  **stratégie**.

3. Choisissez un [modèle,](data-loss-prevention-policies.md#dlp-policy-templates)puis choisissez **Next**.

    Dans notre exemple, nous avons choisi le modèle américain de données d’information personnellement identifiables.

    > [!div class="mx-imgBorder"]
    > ![Modèle de confidentialité pour la politique DLP](../media/dlp-teams-createnewpolicy-template.png)<br/>

4. Sur **l’onglet Nom de votre** police, spécifiez un nom et une description de la stratégie, puis choisissez **Suivant**.

5. Sur **l’onglet Choisir les** emplacements, conserver le paramètre par défaut de tous les comptes, ou **sélectionnez Laissez-moi choisir des emplacements spécifiques**. Vous pouvez spécifier :

    1. jusqu’à 1000 comptes individuels à inclure ou à exclure
    1. listes de distribution et groupes de sécurité à inclure ou à exclure. **Il s’agit d’une fonctionnalité d’aperçu public.**
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**-->  

    ![Emplacements des politiques DLP](../media/dlp-teams-selectlocationsnewpolicy.png)

    > [!NOTE]
    > Si vous voulez vous assurer que les documents contenant des informations sensibles ne sont pas partagés de manière inappropriée en Teams, **assurez-vous que les sites de SharePoint** et les comptes **OneDrive** sont activés, ainsi que les messages de chat et de **canal Teams**.

6. Sur **l’onglet Paramètres** de stratégie, **sous Personnaliser le type de contenu que vous souhaitez protéger,** conserver les paramètres simples par défaut, ou choisir **Utiliser des paramètres avancés,** puis choisir **Suivant**. Si vous choisissez des paramètres avancés, vous pouvez créer ou modifier des règles pour votre stratégie. (Pour obtenir de l’aide avec cela, [voir Paramètres simples vs paramètres avancés](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings).)

7.  Sur **l’onglet Paramètres** de stratégie, **sous Que voulez-vous faire si nous détectons des informations sensibles ?**, passez en revue les paramètres. (Voici où vous pouvez choisir de conserver des conseils de stratégie [par défaut et des notifications par](use-notifications-and-policy-tips.md)courriel, ou de les personnaliser.)

    > [!div class="mx-imgBorder"]
    > ![Paramètres de stratégie DLP avec conseils et notifications](../media/dlp-teams-policysettings-tipsemails.png)

    Lorsque vous avez terminé l’examen ou l’édition des paramètres, choisissez **Suivant**.

8. Sur **l’onglet Paramètres de** stratégie, **sous Voulez-vous activer la stratégie ou tester les choses en premier?**, choisissez d’activer la stratégie, [de la tester d’abord,](dlp-overview-plan-for-dlp.md#policy-deployment)ou de la désactiver pour l’instant, puis choisissez **Next**.

    > [!div class="mx-imgBorder"]
    > ![Spécifiez s’il y a lieu d’activer la politique](../media/dlp-teams-policysettings-turnonnow.png)

9. Sur **l’onglet Examiner vos** paramètres, examinez les paramètres de votre nouvelle stratégie. Choisissez **Modifier pour** apporter des modifications. Lorsque vous avez terminé, choisissez **Créer**.

Prévoyez environ une heure pour que votre nouvelle politique se passe à travers votre centre de données et se synchronise avec les comptes des utilisateurs.

## <a name="prevent-external-access-to-sensitive-documents"></a>Empêcher l'accès externe aux documents sensibles

Pour vous assurer que SharePoint documents contenant des informations sensibles ne peuvent pas être consultés par des invités externes, que ce soit à partir de SharePoint ou Teams par défaut, sélectionnez les éléments suivants :

- Vous pouvez vous assurer que les documents sont protégés jusqu’à ce que DLP les analyse et les marque comme sûrs à partager [en marquant de nouveaux fichiers comme sensibles par défaut](/sharepoint/sensitive-by-default).

- Structure de stratégie DLP recommandée

    - **Conditions**
        - Le contenu contient l’un de ces types d’informations sensibles : [Sélectionnez tout ce qui s’applique]
        
        - Le contenu est partagé à partir Microsoft 365 personnes extérieures à mon organisation
        
          > [!div class="mx-imgBorder"]
          > ![Conditions DLP pour détecter le partage externe de contenu sensible](../media/dlp-teams-external-sharing/external-condition.png)

    - **Actions**
        - Restreindre l’accès au contenu pour utilisateurs externe
        
        - Informer les utilisateurs à l’aide de courriers électroniques et de conseils de stratégie
        
        - Envoyer des rapports d’incident à l’administrateur
        
        > [!div class="mx-imgBorder"]
        > ![Action DLP pour bloquer le partage externe de contenu sensible](../media/dlp-teams-external-sharing/external-action.png)

Politique DLP en action lorsque vous tentez de partager un document dans SharePoint qui contient des informations sensibles avec un invité externe :

> [!div class="mx-imgBorder"]
> ![Partage externe bloqué](../media/dlp-teams-external-sharing/external-sharing-blocked.png)


Politique DLP en action lorsque l’invité tente d’ouvrir un document en Teams avec bloc externe:

> [!div class="mx-imgBorder"]
> ![Accès externe bloqué](../media/dlp-teams-external-sharing/external-access-blocked.png)

## <a name="related-articles"></a>Articles connexes

[Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)

[Envoi des notifications et affichage des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md)
