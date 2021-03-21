---
title: Configurer la veille contre l’usurpation d’identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 978c3173-3578-4286-aaf4-8a10951978bf
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur la veille contre l’usurpation d’adresse dans Exchange Online Protection (EOP), où vous pouvez autoriser ou bloquer des expéditeurs usurpés spécifiques.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bdc68f5a7e1f21969f5cd787cfdb0b58bc26cd83
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50926911"
---
# <a name="configure-spoof-intelligence-in-eop"></a>Configurer la veille contre l’usurpation d’adresse dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, les messages électroniques entrants sont automatiquement protégés contre l’usurpation d’adresse par EOP à partir d’octobre 2018. EOP utilise la veille contre l’usurpation d’adresse dans le cadre de la protection globale de votre organisation contre le hameçonnage. Pour plus d’informations, voir [Protection contre l’usurpation d’adresse dans EOP.](anti-spoofing-protection.md)

Lorsqu’un expéditeur usurpe une adresse de messagerie, il semble qu’il s’agit d’un utilisateur dans l’un des domaines de votre organisation ou d’un utilisateur d’un domaine externe qui envoie du courrier électronique à votre organisation. Les personnes malveillantes qui usurpent des expéditeurs pour envoyer du courrier indésirable ou du hameçonnage doivent être bloquées. Toutefois, il existe des scénarios où des expéditeurs légitimes usurpent l’adresse. Par exemple :

- Scénarios légitimes pour l’usurpation d’un domaine interne :

  - Les expéditeurs tiers utilisent votre domaine pour envoyer des messages en bloc à vos propres employés pour les sondages de l’entreprise.
  - Une société externe génère et envoie des mises à jour publicitaires ou des mises à jour de produit en votre nom.
  - Un assistant doit régulièrement envoyer des courriers électroniques à une autre personne au sein de votre organisation.
  - Une application interne envoie des notifications par courrier électronique.

- Scénarios légitimes d’usurpation de domaines externes :

  - L’expéditeur figure sur une liste de diffusion (également appelée liste de discussion) et la liste de diffusion relaie le courrier électronique de l’expéditeur d’origine à tous les participants de la liste de diffusion.
  - Une société externe envoie du courrier électronique pour le compte d’une autre société (par exemple, un rapport automatisé ou une société de logiciels en tant que service).

La veille contre l’usurpation d’adresses, et plus précisément la stratégie de veille contre l’usurpation d’informations par défaut (et uniquement), permet de s’assurer que les messages électroniques usurpés envoyés par des expéditeurs légitimes ne sont pas pris en compte dans les filtres de courrier indésirable EOP ou les systèmes de messagerie externes, tout en protégeant vos utilisateurs contre les attaques de courrier indésirable ou de hameçonnage.

Vous pouvez gérer la veille contre l’usurpation d’adresse dans le Centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://protection.office.com/antispam>. Pour aller directement à la page **anti-hameçonnage,** utilisez <https://protection.office.com/antiphishing> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour modifier la stratégie de veille contre l’usurpation d’informations ou activer  ou  désactiver la veille contre l’usurpation d’informations, vous devez être membre des groupes de rôles Gestion de l’organisation ou Administrateur de la sécurité.
  - Pour accéder en lecture seule à la stratégie d’intelligence contre  l’usurpation d’informations, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité. 

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour obtenir nos paramètres recommandés pour la veille contre l’usurpation d’adresse, consultez les paramètres de stratégie [anti-hameçonnage par défaut d’EOP.](recommended-settings-for-eop-and-office365-atp.md#eop-default-anti-phishing-policy-settings)

## <a name="use-the-security--compliance-center-to-manage-spoofed-senders"></a>Utiliser le Centre de sécurité & conformité pour gérer les expéditeurs usurpés

> [!NOTE]
> Si vous avez un abonnement Microsoft 365 Entreprise E5 ou que vous avez acheté séparément un module add-on Microsoft Defender pour Office 365, vous pouvez également gérer les expéditeurs qui usurpent votre domaine via [spoof Intelligence insight](walkthrough-spoof-intelligence-insight.md).

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier** indésirable, cliquez sur Développer l’icône pour développer la stratégie ![ de veille contre ](../../media/scc-expand-icon.png) **l’usurpation d’adresse .**

   ![Sélectionner la stratégie de veille contre l’usurpation d’informations](../../media/anti-spam-settings-spoof-intelligence-policy.png)

3. Faites l’une des sélections suivantes :

   - **Passer en revue les nouveaux expéditeurs**
   - **Afficher les expéditeurs que j’ai déjà examinés**

4. Dans **l’onglet Décider si ces** expéditeurs sont autorisés à usurper l’adresse de vos utilisateurs qui s’affiche, sélectionnez l’un des onglets suivants :

   - **Vos domaines : expéditeurs** usurpant des utilisateurs dans vos domaines internes.
   - **Domaines externes : expéditeurs** usurpant des utilisateurs dans des domaines externes.

5. Cliquez ![ sur Développer ](../../media/scc-expand-icon.png) l’icône dans **la colonne Usurpation d’usurpation d’accès.** Choisissez **Oui** pour autoriser l’expéditeur usurpé  ou non pour marquer le message comme usurpant l’usurpation. L’action est contrôlée par la stratégie anti-hameçonnage par défaut ou les stratégies anti-hameçonnage personnalisées (la valeur par défaut est Déplacer le message dans le dossier **Courrier indésirable).** Pour plus d’informations, voir Paramètres d’usurpation [d’informations dans les stratégies anti-hameçonnage.](set-up-anti-phishing-policies.md#spoof-settings)

   ![Screenshot showing the spoofed senders flyout, and whether the sender is allowed to spoof](../../media/c0c062fd-f4a4-4d78-96f7-2c22009052bb.jpg)

   Les colonnes et les valeurs que vous voyez sont expliquées dans la liste suivante :

   - **Utilisateur usurpé :** compte d’utilisateur usurpé. Il s’agit de l’expéditeur du message dans l’adresse de provenance (également appelée adresse) qui est affichée dans les `5322.From` clients de messagerie. La validité de cette adresse n’est pas vérifiée par SPF.

     - Sous **l’onglet** Vos domaines, la valeur contient une seule adresse de messagerie, ou si le serveur de messagerie source usurpe plusieurs comptes d’utilisateur, il en contient **plusieurs.**

     - Sous **l’onglet Domaines externes,** la valeur contient le domaine de l’utilisateur usurpé, et non l’adresse de messagerie complète.

   - **Infrastructure d’envoi**: domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source. Si l’adresse IP source n’a pas d’enregistrement PTR, l’infrastructure d’envoi est identifiée comme \<source IP\> /24 (par exemple, 192.168.100.100/24).

     Pour plus d’informations sur les sources de messages et les expéditeurs de messages, voir [une vue d’ensemble des normes de message électronique.](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards)

   - **# des messages**: nombre de messages de l’infrastructure d’envoi à votre organisation qui contiennent l’expéditeur ou les expéditeurs usurpés spécifiés au cours des 30 derniers jours.

   - **# des réclamations des utilisateurs**: réclamations déposées par vos utilisateurs contre cet expéditeur au cours des 30 derniers jours. Les réclamations se font généralement sous la forme de soumissions de courrier indésirable à Microsoft.

   - **Résultat de l’authentification**: l’une des valeurs suivantes :
      - **Réussi :** l’expéditeur a réussi les vérifications d’authentification de courrier électronique de l’expéditeur (SPF ou DKIM).
      - **Échec :** l’expéditeur a échoué aux vérifications d’authentification de l’expéditeur EOP.
      - **Inconnu**: le résultat de ces vérifications est inconnu.

   - **Décision définie par**: indique qui a déterminé si l’infrastructure d’envoi est autorisée à usurper l’utilisateur :
       - **Stratégie de veille contre l’usurpation** d’informations (automatique)
       - **Administrateur** (manuel)

   - **Dernière vue**: date de la dernière réception d’un message de l’infrastructure d’envoi contenant l’utilisateur usurpé.

   - **Autorisé à usurper l’usurpation d’accès ?**: les valeurs que vous voyez ici sont les :
     - **Oui**: les messages provenant de la combinaison de l’utilisateur usurpé et de l’infrastructure d’envoi sont autorisés et ne sont pas traités comme des e-mails usurpés.
     - **Non**: les messages provenant de la combinaison de l’utilisateur usurpé et de l’infrastructure d’envoi sont marqués comme usurpés. L’action est contrôlée par la stratégie anti-hameçonnage par défaut ou les stratégies anti-hameçonnage personnalisées (la valeur par défaut est Déplacer le message dans le dossier **Courrier indésirable).** Pour plus d’informations, voir la section suivante.

     - **Certains utilisateurs** (onglet Vos domaines uniquement) : une infrastructure d’envoi usurpe plusieurs **utilisateurs,** où certains utilisateurs usurpés sont autorisés et d’autres non. Utilisez **l’onglet Détails** pour voir les adresses spécifiques.

6. En bas de la page, cliquez sur **Enregistrer.**

## <a name="use-powershell-to-manage-spoofed-senders"></a>Utiliser PowerShell pour gérer les expéditeurs usurpés

Pour afficher les expéditeurs autorisés et bloqués dans la veille contre l’usurpation d’adresse, utilisez la syntaxe suivante :

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

Cet exemple renvoie des informations détaillées sur tous les expéditeurs autorisés à usurper des noms d’utilisateurs dans vos domaines.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-PhishFilterPolicy.](/powershell/module/exchange/get-phishfilterpolicy)

Pour configurer les expéditeurs autorisés et bloqués dans la veille contre l’usurpation d’adresse, suivez les étapes suivantes :

1. Capturez la liste actuelle des expéditeurs usurpés détectés en écrivant la sortie de l’cmdlet **Get-PhishFilterPolicy** dans un fichier CSV :

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Modifiez le fichier CSV pour ajouter ou modifier les valeurs **SpoofedUser** (adresse e-mail) et **AllowedToSpoof** (Oui ou Non). Enregistrez le fichier, lisez-le et stockez le contenu en tant que variable nommée `$UpdateSpoofedSenders` :

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Utilisez la `$UpdateSpoofedSenders` variable pour configurer la stratégie d’intelligence contre l’usurpation d’informations :

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-PhishFilterPolicy.](/powershell/module/exchange/set-phishfilterpolicy)

## <a name="use-the-security--compliance-center-to-configure-spoof-intelligence"></a>Utiliser le Centre de sécurité & conformité pour configurer la veille contre l’usurpation d’informations

Les options de configuration pour la veille contre l’usurpation d’informations sont décrites dans les paramètres d’usurpation d’informations dans les [stratégies anti-hameçonnage.](set-up-anti-phishing-policies.md#spoof-settings)

Vous pouvez configurer les paramètres de veille contre l’usurpation d’informations dans la stratégie anti-hameçonnage par défaut, ainsi que dans les stratégies personnalisées. Pour obtenir des instructions basées sur votre abonnement, consultez l’une des rubriques suivantes :

- [Configurer des stratégies anti-hameçonnage dans EOP.](configure-anti-phishing-policies-eop.md)

- [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.](configure-atp-anti-phishing-policies.md)

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez configuré la veille contre l’usurpation d’identité avec des expéditeurs autorisés et non autorisés à usurper l’identité, et que vous avez configuré les paramètres de veille contre l’usurpation d’identité, utilisez l’une des étapes suivantes :

- In the Security & Compliance Center, go to **Threat management** \> **Policy** \> **Anti-spam** \> expand **Spoof intelligence policy** select Show me \> **senders I already reviewed** select the Your \> **Domains** or External **Domains** tab, and verify the **Allowed to spoof?** value for the sender.

- Dans PowerShell, exécutez les commandes suivantes pour afficher les expéditeurs autorisés et non autorisés à usurper :

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- Dans PowerShell, exécutez la commande suivante pour exporter la liste de tous les expéditeurs usurpés vers un fichier CSV :

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

- Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **Anti-phishing** or **ATP anti-phishing**, and do either the following steps:  

  - Sélectionnez une stratégie dans la liste. Dans le volant qui s’affiche, vérifiez les valeurs dans la section **Usurpation d’identité.**
  - Cliquez **sur Stratégie par défaut.** Dans le volant qui s’affiche, vérifiez les valeurs dans la section **Usurpation d’identité.**

- Dans Exchange Online PowerShell, remplacez par Office 365 AntiPhish Default ou le nom d’une stratégie personnalisée, puis exécutez la commande suivante pour vérifier \<Name\> les paramètres :

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>" | Format-List EnableSpoofIntelligence,EnableUnauthenticatedSender,AuthenticationFailAction
  ```

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Autres façons de gérer l’usurpation et le hameçonnage

Soyez prudent sur l’usurpation d’informations et la protection contre le hameçonnage. Voici quelques méthodes connexes pour vérifier les expéditeurs usurpant votre domaine et les empêcher d’endommager votre organisation :

- Vérifiez le **rapport de courrier d’usurpation d’adresse .** Vous pouvez souvent utiliser ce rapport pour afficher et gérer les expéditeurs usurpés. Pour plus d’informations, [voir le rapport sur les détections d’usurpation d’informations.](view-email-security-reports.md#spoof-detections-report)

- Examinez votre configuration SPF (Sender Policy Framework). Pour consulter une brève présentation de SPF et le configurer rapidement, voir [Configurer SPF dans Microsoft 365 pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Pour consulter des informations plus approfondies sur l’utilisation de SPF par Office 365, la résolution des problèmes et les déploiements non standard tels que les déploiements hybrides, voir Comment Office 365 utilise SPF (Sender Policy Framework) pour empêcher l’usurpation d’identité.

- Examinez votre configuration DKIM (DomainKeys Identified Mail). Vous devez utiliser DKIM en plus de SPF et DMARC pour empêcher les attaquants d’envoyer des messages qui semblent provenant de votre domaine. DKIM vous permet d'ajouter une signature numérique aux messages électroniques dans l'en-tête du message. Pour plus d’informations, voir Utiliser DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé [dans Office 365.](use-dkim-to-validate-outbound-email.md)

- Examinez votre configuration DMARC (Domain-based Message Authentication, Reporting, and Conformance). L’implémentation de DMARC avec SPF et DKIM fournit une protection supplémentaire contre l’usurpation et les courriers de hameçonnage. DMARC permet aux systèmes de messagerie de réception de déterminer ce qu’ils doivent faire des messages envoyés à partir de votre domaine qui sont rejetés par les contrôles de SPF ou de DKIM. Pour plus d’informations, [voir Utiliser DMARC pour valider le courrier électronique dans Office 365.](use-dmarc-to-validate-email.md)