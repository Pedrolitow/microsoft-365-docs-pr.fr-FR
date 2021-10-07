---
title: Configurer la boîte de réception Prioritaire pour tous les membres de votre organisation
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
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
ms.openlocfilehash: b2c315b6fb4a4c80f245bcf4731b93996753586a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60176090"
---
# <a name="configure-focused-inbox-for-everyone-in-your-organization"></a>Configurez la boîte de réception Prioritaire pour tous les membres de votre organisation

Si vous êtes responsable de la configuration de messagerie pour TOUS LES UTILISATEURS de votre entreprise, cet article s’adresse à vous ! Il explique comment la personnaliser ou la désactiver pour votre entreprise et apporte des réponses aux [questions fréquemment posées](#faq-for-focused-inbox).

Si vous voulez désactiver la boîte de réception Prioritaire uniquement pour vous, consultez l’article [Désactiver la boîte de réception Prioritaire](https://support.microsoft.com/office/f714d94d-9e63-4217-9ccb-6cb2986aa1b2).  

Si vous souhaitez que vos utilisateurs reçoivent les e-mails spécifiques à l’entreprise, comme les e-mails des services Ressources humaines et Paie, vous pouvez configurer la boîte de réception Prioritaire pour que ceux-ci apparaissent dans l’affichage Prioritaire. Vous pouvez également faire apparaître la boîte de réception Prioritaire dans les boîtes aux lettres des utilisateurs de votre organisation.
  
## <a name="turn-focused-inbox-on-or-off-in-your-organization"></a>Activez ou désactivez la boîte de réception Prioritaire dans votre organisation

Pour activer ou désactiver la boîte de réception Prioritaire pour tous les utilisateurs de votre organisation, vous devez utiliser PowerShell. Vous souhaitez effectuer cette opération dans le Centre d'administration Microsoft 365 ? Informez-en notre équipe Ingénierie. **[Votez ici !](https://go.microsoft.com/fwlink/?linkid=862489)**
  
**Pour désactiver la boîte de réception Prioritaire :**
  
L’exemple PowerShell suivant **désactive** la boîte de réception Prioritaire au sein de votre organisation. Mais cela n’empêche pas vos utilisateurs d’y accéder. S’ils le souhaitent, ils peuvent toujours réactiver la boîte de réception Prioritaire sur chacun de leurs clients.  
  
1. [Vous connecter à Exchange Online à l'aide de Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Pour effectuer ces procédures, vous devez disposer des autorisations appropriées. Pour connaître les autorisations requises, reportez-vous à l'entrée « Règles de transport » de [Autorisations relatives à la conformité et à la stratégie de messagerie](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

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

Vos utilisateurs ne verront l’affichage Prioritaire qu’après avoir fermé et redémarré Outlook. Un conseil leur donnant la possibilité d’utiliser la nouvelle boîte de réception Prioritaire apparaît alors dans l’interface utilisateur d’Outlook.
  
![Image de la boîte de réception Prioritaire lorsqu’un utilisateur ouvre Outlook sur le web pour la première fois.](../../media/f6ef79e7-0f4c-4a23-b6f0-7c15d927b5f0.png)
  
Si vous passez du Courrier pêle-mêle à la boîte de réception Prioritaire, ils peuvent décider d'activer (« Essayer ») ou d'ignorer la fonctionnalité. Si l'utilisateur dispose de plusieurs clients (pris en charge), ils peuvent activer/désactiver la boîte de réception Prioritaire individuellement dans chacun d'eux. Le conseil se présente ainsi :
  
![Une image illustrant l’apparence de la boîte de réception Prioritaire lorsqu’elle est déployée pour vos utilisateurs et qu’Outlook est rouvert.](../../media/c034f969-d650-4333-88f1-dd10ade0a94c.png)
  
Lorsqu’un utilisateur décide d’utiliser la boîte de réception Prioritaire, Courrier pêle-mêle est désactivé automatiquement. Le dossier Courrier pêle-mêle est converti en un dossier standard que l’utilisateur peut renommer ou supprimer.
  
## <a name="turn-focused-inbox-on-or-off-for-specific-users"></a>Activer ou désactiver la boîte de réception Prioritaire pour des utilisateurs spécifiques

Cet exemple **désactive** la boîte de réception Prioritaire pour Tim Matthews, de l’organisation Contoso. Mais cela ne l’empêche pas d’y accéder. S’il le souhaite, il peut toujours réactiver la boîte de réception Prioritaire sur chacun de ses clients. 
  
1. [Vous connecter à Exchange Online à l'aide de Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Pour effectuer ces procédures, vous devez disposer des autorisations appropriées. Pour connaître les autorisations requises, reportez-vous à l’entrée « Règles de transport » de la rubrique Autorisations relatives à la conformité et à la stratégie de messagerie.

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

2. Naviguez vers **Flux de courrier** \> **Règles**. Cliquez sur ![Ajouter icône EAC](../../media/795e5bdd-48bb-433f-8e07-3c7a19f8eca2.gif), puis sélectionnez **Créer une règle...** 

3. Après avoir créé la règle, cliquez sur **Enregistrer** pour démarrer la règle.

    L'image suivante présente un exemple permettant de remettre tous les messages des « Ressources Humaines » dans la boîte de réception Prioritaire.

    ![paie focusedinbox.](../../media/focusedinbox-transport-rule.PNG)

    > [!NOTE]
    > Dans cet exemple, le texte de la valeur de l’en-tête du message est **X-MS-Exchange-Organization-BypassFocusedInbox**.
  
## <a name="use-powershell-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Utilisez PowerShell pour créer une règle de transport permettant de diriger les messages e-mail vers l’affichage Prioritaire pour tous vos utilisateurs

1. [Vous connecter à Exchange Online à l'aide de Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Pour effectuer ces procédures, vous devez disposer des autorisations appropriées. Pour connaître les autorisations requises, reportez-vous à l'entrée « Règles de transport » de [Autorisations relatives à la conformité et à la stratégie de messagerie](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

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

Nous avons reçu des indications selon lesquelles le Courrier pêle-mêle a soudainement cessé de fonctionner pour certains utilisateurs. Dans ce cas, vous pouvez le réactiver pour des utilisateurs spécifiques. Voir [Configurer le Courrier pêle-mêle pour votre organisation](../email/configure-clutter.md).

## <a name="faq-for-focused-inbox"></a>FAQ sur la boîte de réception Prioritaire

Voici des réponses aux questions fréquemment posées sur la boîte de réception Prioritaire.

### <a name="can-i-control-how-i-roll-out-focused-inbox-in-my-organization"></a>Puis-je contrôler le déploiement de la boîte de réception Prioritaire au sein de mon organisation ?

Oui. Vous pouvez activer ou désactiver la boîte de réception Prioritaire pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Voir ci-dessus.
  
### <a name="is-the-focused-inbox-feature-only-available-for-office-2016-clients"></a>La fonctionnalité boîte de réception Prioritaire est-elle disponible pour les clients Office 2016 ?

Oui, seuls les utilisateurs d’Office 2016 sont concernés. La fonctionnalité ne sera pas rétroportée vers Outlook 2013 ou version précédente.
  
### <a name="how-long-does-it-take-for-focused-inbox-changes-to-take-place-in-outlook"></a>Combien de temps faut-il pour que les modifications apportées à la boîte de réception Prioritaire s’appliquent à Outlook ?

Lorsque vous activez ou désactivez la boîte de réception Prioritaire, les paramètres s’appliquent dès que vos utilisateurs ferment et redémarrent Outlook.
  
### <a name="what-happens-to-clutter-once-i-turn-on-focused-inbox"></a>Que devient le courrier pêle-mêle lorsque j’active la boîte de réception Prioritaire ?

Après avoir effectué la transition, vous ne recevrez plus d’e-mails moins actionables dans le dossier Courrier pêle-mêle. Au lieu de cela, les e-mails seront répartis entre les onglets Prioritaire et Autres dans votre boîte de réception. Le même algorithme qui déplaçait les éléments vers le dossier Courrier pêle-mêle est utilisé pour la fonctionnalité Boîte de réception Prioritaire. Cela signifie que les e-mails qui étaient auparavant paramétrés pour être déplacés dans le dossier Courrier pêle-mêle seront déplacés dans la boîte de réception Autres. Tous les e-mails déjà présents dans votre dossier Courrier pêle-mêle y resteront tant que vous n’aurez pas décidé de les supprimer ou de les déplacer.
  
Consultez ce billet rédigé par [Tony Redmond](https://www.petri.com/author/tony-redmond), Microsoft MVP : [De quelle façon la boîte de réception Prioritaire remplace-t-elle le courrier pêle-mêle dans Office 365 ?](https://www.petri.com/focused-inbox-office-365)
  
### <a name="can-i-keep-users-on-clutter-what-is-microsofts-recommendation-when-it-comes-to-using-clutter-vs-focused-inbox"></a>Puis-je maintenir des utilisateurs sur le Courrier pêle-mêle ? Microsoft recommande-t-il d'utiliser le Courrier pêle-mêle ou la boîte de réception Prioritaire ?

Oui, vous pouvez maintenir des utilisateurs sur le courrier pêle-mêle et désactiver la boîte de réception Prioritaire. Toutefois, à terme, le courrier pêle-mêle finira par être remplacé par la boîte de réception Prioritaire, par conséquent Microsoft vous recommande de migrer vers la boîte de réception Prioritaire dès maintenant. Pour en savoir plus sur quand utiliser la fonctionnalité Courrier pêle-mêle avec Exchange Online, consultez ce billet de blog : [Mise à jour sur la boîte de réception Prioritaire et nos projets pour le courrier pêle-mêle](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448).
  
### <a name="should-i-disable-clutter-for-my-end-users-if-we-are-going-to-move-everyone-to-focused-inbox"></a>Dois-je désactiver le courrier pêle-mêle pour mes utilisateurs finaux si nous migrons tout le monde vers la boîte de réception Prioritaire ?

Non. Il est possible de désactiver le courrier pêle-mêle sur une boîte aux lettres explicite en exécutant l'applet de commande Set-Clutter. En revanche, dans ce cas, les messages précédemment redirigés vers le dossier Courrier pêle-mêle resteront dans la boîte de réception et le propriétaire de la boîte aux lettres devra les traiter en attendant que son client soit mis à niveau vers une version prenant en charge la fonctionnalité Boîte de réception Prioritaire. Il est donc préférable de ne pas désactiver le courrier pêle-mêle avant que les clients mis à niveau soient disponibles.
  
### <a name="why-are-there-two-different-cmdlets-for-managing-focused-inbox"></a>Pourquoi existe-t-il deux applets de commande distinctes pour gérer de la boîte de réception Prioritaire ?

Deux états sont associés à la boîte de réception Prioritaire.
  
- **Niveau organisation** : état de la boîte de réception Prioritaire, et horodatage de la dernière mise à jour associée.

- **Niveau boîte aux lettres** : état de la boîte de réception Prioritaire, et horodatage de la dernière mise à jour associée. 

### <a name="how-does-outlook-decide-to-show-the-focused-inbox-experience-with-these-two-states"></a>Comment Outlook détermine-t-il l’expérience de boîte de réception Prioritaire affichée avec ces deux états ?

Outlook choisit l’applet de commande dont l’horodatage est le plus récent. Par défaut, les deux horodatages sont « null », auquel cas la fonctionnalité est activée.
  
### <a name="why-does-the-get-focusedinbox-cmdlet-return-true-when-ive-turned-focused-inbox-off-in-my-organization"></a>Pourquoi l’applet de commande Get-FocusedInbox renvoie « true » alors que j’ai désactivé la boîte de réception Prioritaire au sein de mon organisation ?

Deux applets de commande permettent de contrôler la boîte de réception Prioritaire. Lorsque vous exécutez Get-FocusedInbox pour une boîte aux lettres, l’état Niveau boîte aux lettres de la fonctionnalité est renvoyé. L’expérience Outlook choisie dépend du dernier état d’applet de commande qui a été modifié.
  
### <a name="can-i-run-a-script-to-see-who-has-turned-on-focused-inbox"></a>Puis-je exécuter un script pour voir qui a activé la boîte de réception Prioritaire ?

Non et c’est tout à fait normal. L’activation de la boîte de réception Prioritaire est en effet un paramètre côté client. De ce fait, tout ce que l’applet de commande peut faire, c’est vous indiquer si la boîte aux lettres de l’utilisateur est éligible pour l’expérience client. Il est possible qu’elle soit simultanément activée dans certains clients et désactivée dans d’autres, par exemple, activée dans les applications Outlook et Outlook Mobile, mais désactivée dans Outlook sur le web.

## <a name="related-content"></a>Contenu associé

[Voir Configurer le Courrier pêle-mêle pour votre organisation](../email/configure-clutter.md) (article)\
[Configurer les paramètres de boîte aux lettres partagée](../email/configure-a-shared-mailbox.md) (article)\
[Créer des signatures et des clauses d'exclusion de responsabilité](create-signatures-and-disclaimers.md) (vidéo)
