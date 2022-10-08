---
title: Configurer la boîte de réception Prioritaire pour tous les membres de votre organisation
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 613a845c-4b71-41de-b331-acdcf5b6625d
description: Si vous êtes chargé de la configuration des paramètres de messagerie pour tout le monde dans une entreprise, cette article explique comment configurer la Boîte de réception Prioritaire pour les utilisateurs.
ms.openlocfilehash: fd2a8e82297eb7b3298688e72a0f01f7c0b98fc6
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68169098"
---
# <a name="configure-focused-inbox-for-everyone-in-your-organization"></a>Configurez la boîte de réception Prioritaire pour tous les membres de votre organisation

Si vous êtes responsable de la configuration de messagerie pour TOUS LES UTILISATEURS de votre entreprise, cet article s’adresse à vous ! Il explique comment la personnaliser ou la désactiver pour votre entreprise et apporte des réponses aux [questions fréquemment posées](#faq-for-focused-inbox).

Si vous voulez désactiver la boîte de réception Prioritaire uniquement pour vous, consultez l’article [Désactiver la boîte de réception Prioritaire](https://support.microsoft.com/office/f714d94d-9e63-4217-9ccb-6cb2986aa1b2).  

If you want to be sure that your users receive business-specific email messages, for example, from HR or payroll, you can configure Focused Inbox so these messages reach the Focused view. You can also control whether users in your organization see the Focused Inbox in their mailbox.
  
## <a name="turn-focused-inbox-on-or-off-in-your-organization"></a>Activez ou désactivez la boîte de réception Prioritaire dans votre organisation

Pour activer ou désactiver la boîte de réception Prioritaire pour tous les utilisateurs de votre organisation, vous devez utiliser PowerShell. Vous souhaitez effectuer cette opération dans le Centre d'administration Microsoft 365 ? Informez-en notre équipe Ingénierie. **[Votez ici !](https://go.microsoft.com/fwlink/?linkid=862489)**
  
**Pour désactiver la boîte de réception Prioritaire :**
  
The following PowerShell example turns Focused Inbox **Off** in your organization. However, it doesn't block the availability of the feature for your users. If they want, they can still re-enable Focused Inbox again on each of their clients. 
  
1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Transport rules" entry in [Messaging policy and compliance permissions](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. Exécutez l’applet de commande **Get-OrganizationConfig**. 

    ```powershell
    Get-OrganizationConfig
    ```

4. Recherchez **FocusedInboxOn** pour afficher son paramètre actuel : 

    ![Réponse de PowerShell sur l’état de la boîte de réception Prioritaire.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Exécutez l'applet de commande suivante pour désactiver la boîte de réception Prioritaire.

    ```powershell
    Set-OrganizationConfig -FocusedInboxOn $false
    ```

6. Exécutez de nouveau l’applet de commande **Get-OrganizationConfig** et vous verrez que FocusedInboxOn est défini sur $false, ce qui signifie qu’elle a été désactivée. 

**Pour activer la boîte de réception Prioritaire :**
  
- À l’étape 5 ci-dessus, exécutez l’applet de commande suivante pour activer la boîte de réception Prioritaire.

  ```powershell
  Set-OrganizationConfig -FocusedInboxOn $true
  ```
    
## <a name="what-do-users-see-after-i-turn-on-focused-inbox"></a>Que voient les utilisateurs une fois la boîte de réception Prioritaire activée ? 

Your users will see the Focused view only after they close and restart Outlook. When they restart Outlook, they'll see a Tip in the Outlook user interface giving them to the option to use the new Focused Inbox.
  
![Image de la boîte de réception Prioritaire lorsqu’un utilisateur ouvre Outlook sur le web pour la première fois.](../../media/f6ef79e7-0f4c-4a23-b6f0-7c15d927b5f0.png)
  
If you're switching from Clutter to Focused Inbox, they can decide to enable it ("Try it") or dismiss the feature. If the user has multiple (supported) clients, they can enable/disable Focused Inbox individually on each one. The tip looks like this:
  
![Une image illustrant l’apparence de la boîte de réception Prioritaire lorsqu’elle est déployée pour vos utilisateurs et qu’Outlook est rouvert.](../../media/c034f969-d650-4333-88f1-dd10ade0a94c.png)
  
When a user decides to start using Focused Inbox, Clutter gets disabled automatically. The Clutter folder gets converted into a standard folder, that allows the user to rename or delete it.
  
## <a name="turn-focused-inbox-on-or-off-for-specific-users"></a>Activer ou désactiver la boîte de réception Prioritaire pour des utilisateurs spécifiques

This example turns Focused Inbox **Off** for Tim Matthews in the Contoso organization. However, it doesn't block the availability of the feature to him. If he wants, he can still re-enable Focused Inbox again on each of his clients. 
  
1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Transport rules" entry in the Messaging policy and compliance permissions topic.

3. Exécutez l’applet de commande **Get-FocusedInbox**, par exemple : 

    ```powershell
    Get-FocusedInbox -Identity <tim@contoso.com>
    ```

4. Recherchez FocusedInboxOn pour afficher son paramètre actuel :

    ![Réponse de PowerShell sur l’état de la boîte de réception Prioritaire.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Exécutez l'applet de commande suivante pour désactiver la boîte de réception Prioritaire :

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $false
    ```

    OU, exécutez l’applet de commande suivante pour l’activer :

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $true
    ```

## <a name="use-the-ui-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Utilisez l’interface utilisateur pour créer une règle de transport permettant de diriger les messages e-mail vers l’affichage Prioritaire pour tous vos utilisateurs

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.

2. Navigate to **mail flow** \> **Rules**. Select ![EAC Add icon.](../../media/795e5bdd-48bb-433f-8e07-3c7a19f8eca2.gif) and then select **Create a new rule...**. 

3. Après avoir créé la règle, cliquez sur **Enregistrer** pour démarrer la règle.

    L'image suivante présente un exemple permettant de remettre tous les messages des « Ressources Humaines » dans la boîte de réception Prioritaire.

    ![paie focusedinbox.](../../media/focusedinbox-transport-rule.PNG)

    > [!NOTE]
    > Dans cet exemple, le texte de la valeur de l’en-tête du message est **X-MS-Exchange-Organization-BypassFocusedInbox**.
  
## <a name="use-powershell-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Utilisez PowerShell pour créer une règle de transport permettant de diriger les messages e-mail vers l’affichage Prioritaire pour tous vos utilisateurs

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Transport rules" entry in [Messaging policy and compliance permissions](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. Exécutez la commande suivante pour remettre tous les messages du « Service Paie », par exemple, à la boîte de réception Prioritaire.

    ```powershell
    New-TransportRule -Name <name_of_the_rule> -From "Payroll Department" -SetHeaderName "X-MS-Exchange-Organization-BypassFocusedInbox" -SetHeaderValue "true"
    ```

> [!IMPORTANT]
> Dans cet exemple, « X-MS-Exchange-Organization-BypassFocusedInbox » et « true » sont sensibles à la casse.
> De plus, la boîte de réception Prioritaire respectera l’en-tête X qui contourne le courrier pêle-mêle. Par conséquent, si vous utilisez ce paramètre dans le courrier pêle-mêle, il sera utilisé dans la boîte de réception Prioritaire. Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](/powershell/module/exchange/new-transportrule).

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Vérifiez les en-têtes des messages e-mail pour déterminer si les messages sont acheminés vers la boîte de réception suite au contournement de la règle de transport Boîte de réception Prioritaire. Sélectionnez un e-mail dans une boîte aux lettres de votre organisation sur laquelle la règle de transport Boîte de réception Prioritaire est appliquée. Examinez les en-têtes du message. L’en-tête suivant doit y figurer : **X-MS-Exchange-Organization-BypassFocusedInbox: true**. Cela signifie que le contournement fonctionne. Consultez l'article [Afficher les informations d'en-tête Internet des messages électroniques](https://go.microsoft.com/fwlink/p/?LinkId=822530) pour plus d'informations sur la façon de rechercher des informations d'en-tête.

### <a name="what-will-the-user-see"></a>Que verra l’utilisateur ?

Si une règle de transport est en place, une notification s’affichera pour le remplacement. Outlook sur le web désactivera l’option « Toujours déplacer vers Autres » et affichera une info-bulle. Les clients Outlook sur la version de bureau autoriseront la sélection de l’option « Toujours déplacer vers Autres » et afficheront une zone de dialogue.

## <a name="turn-onoff-clutter"></a>Activer/désactiver la fonctionnalité Courrier pêle-mêle

We've received reports that Clutter suddenly stopped working for some users. If this happens, you can enable it again for specific users. See [Configure Clutter for your organization](../email/configure-clutter.md).

## <a name="faq-for-focused-inbox"></a>FAQ sur la boîte de réception Prioritaire

Voici des réponses aux questions fréquemment posées sur la boîte de réception Prioritaire.

### <a name="can-i-control-how-i-roll-out-focused-inbox-in-my-organization"></a>Puis-je contrôler le déploiement de la boîte de réception Prioritaire au sein de mon organisation ?

Yes. You can turn Focused Inbox on or off for your entire organization, or you can turn it on or off for specified users. See above.
  
### <a name="is-the-focused-inbox-feature-only-available-for-office-2016-clients"></a>La fonctionnalité boîte de réception Prioritaire est-elle disponible pour les clients Office 2016 ?

Yes, only users with Office 2016 are affected. The feature is not going to be backported to Outlook 2013 or earlier.
  
### <a name="how-long-does-it-take-for-focused-inbox-changes-to-take-place-in-outlook"></a>Combien de temps faut-il pour que les modifications apportées à la boîte de réception Prioritaire s’appliquent à Outlook ?

Lorsque vous activez ou désactivez la boîte de réception Prioritaire, les paramètres s’appliquent dès que vos utilisateurs ferment et redémarrent Outlook.
  
### <a name="what-happens-to-clutter-once-i-turn-on-focused-inbox"></a>Que devient le courrier pêle-mêle lorsque j’active la boîte de réception Prioritaire ?

After switching, you'll no longer receive less actionable email in the Clutter folder. Instead, email will be split between the Focused and Other tabs in your inbox. The same algorithm that moved items to the Clutter folder now powers Focused Inbox, meaning that any emails that were set to move to Clutter will now be moved to Other. Any messages already in your Clutter folder will remain there until you decide to delete or move them.
  
Consultez ce billet rédigé par [Tony Redmond](https://www.petri.com/author/tony-redmond), Microsoft MVP : [De quelle façon la boîte de réception Prioritaire remplace-t-elle le courrier pêle-mêle dans Office 365 ?](https://www.petri.com/focused-inbox-office-365)
  
### <a name="can-i-keep-users-on-clutter-what-is-microsofts-recommendation-when-it-comes-to-using-clutter-vs-focused-inbox"></a>Can I keep users on Clutter? What is Microsoft's recommendation when it comes to using Clutter vs Focused Inbox?

Yes, you can keep users on Clutter and disable Focused Inbox, however, eventually Clutter will be fully replaced with Focused Inbox so Microsoft's recommends moving to Focused Inbox now. To learn more about when you use Clutter with Exchange Online, see this blog post: [Update on Focused Inbox and our plans for Clutter](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448).
  
### <a name="should-i-disable-clutter-for-my-end-users-if-we-are-going-to-move-everyone-to-focused-inbox"></a>Dois-je désactiver le courrier pêle-mêle pour mes utilisateurs finaux si nous migrons tout le monde vers la boîte de réception Prioritaire ?

No. It's possible to disable Clutter for a mailbox explicitly by running the Set-Clutter cmdlet. However, if you do this, the mailbox owner will see messages that were previously redirected to the Clutter folder remain in the Inbox and they'll have to process those messages until their client is upgraded to a version that supports the Focused Inbox. It's therefore best not to disable Clutter until the upgraded clients are available.
  
### <a name="why-are-there-two-different-cmdlets-for-managing-focused-inbox"></a>Pourquoi existe-t-il deux applets de commande distinctes pour gérer de la boîte de réception Prioritaire ?

Deux états sont associés à la boîte de réception Prioritaire.
  
- **Niveau organisation** : état de la boîte de réception Prioritaire, et horodatage de la dernière mise à jour associée.

- **Niveau boîte aux lettres** : état de la boîte de réception Prioritaire, et horodatage de la dernière mise à jour associée. 

### <a name="how-does-outlook-decide-to-show-the-focused-inbox-experience-with-these-two-states"></a>Comment Outlook détermine-t-il l’expérience de boîte de réception Prioritaire affichée avec ces deux états ?

Outlook decides to show the experience by choosing which cmdlet has the latest time stamp. By default, both time stamps are "null" and in this case, the feature is enabled.
  
### <a name="why-does-the-get-focusedinbox-cmdlet-return-true-when-ive-turned-focused-inbox-off-in-my-organization"></a>Pourquoi l’applet de commande Get-FocusedInbox renvoie « true » alors que j’ai désactivé la boîte de réception Prioritaire au sein de mon organisation ?

There are two cmdlets for controlling Focused Inbox. When you run Get-FocusedInbox for a mailbox, it returns the mailbox level state of the feature. The experience in Outlook is chosen based on which cmdlet state was last modified.
  
### <a name="can-i-run-a-script-to-see-who-has-turned-on-focused-inbox"></a>Puis-je exécuter un script pour voir qui a activé la boîte de réception Prioritaire ?

No, and this is by design. Focused Inbox enablement is a client-side setting, so all the cmdlet can do is tell you if the user's mailbox is eligible for the client experience. It is possible for it to be simultaneously enabled in some clients and disabled in others, for example, enabled in Outlook app and Outlook Mobile but disabled in Outlook on the web.

## <a name="related-content"></a>Contenu associé

[Voir Configurer le Courrier pêle-mêle pour votre organisation](../email/configure-clutter.md) (article)\
[Configurer les paramètres de boîte aux lettres partagée](../email/configure-a-shared-mailbox.md) (article)\
[Créer des signatures et des clauses d'exclusion de responsabilité](create-signatures-and-disclaimers.md) (vidéo)
