---
title: Configurer l’intelligence des usurpations d’identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 978c3173-3578-4286-aaf4-8a10951978bf
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à configurer les expéditeurs usurpés pour autoriser ou non l’autorisation, ainsi que d’autres paramètres d’aide à la décision dans Exchange Online et Exchange Online Protection (EOP).
ms.openlocfilehash: 96a1442c893444108aaf6814484bc4e4d55aa731
ms.sourcegitcommit: 9ed3283dd6dd959faeca5c22613f9126261b9590
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "43528736"
---
# <a name="configure-spoof-intelligence-in-office-365"></a>Configurer l’intelligence des usurpations d’identité dans Office 365

Si vous êtes un client Office 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection (EOP) autonome sans boîte aux lettres Exchange Online, les messages électroniques entrants sont automatiquement protégés contre l’usurpation par EOP au 1er octobre 2018. EOP utilise l’intelligence d’usurpation d’identité dans le cadre de la protection globale de votre organisation contre le hameçonnage. Pour plus d’informations, consultez la rubrique [protection contre l’usurpation d’identité dans Office 365](anti-spoofing-protection.md).

Lorsqu’un expéditeur usurpe une adresse de messagerie, il semble être un utilisateur de l’un des domaines de votre organisation ou un utilisateur dans un domaine externe qui envoie des messages à votre organisation. Les agresseurs qui usurpent des expéditeurs pour envoyer du courrier indésirable ou des tentatives de hameçonnage doivent être bloqués. Toutefois, il existe des scénarios dans lesquels les expéditeurs légitimes sont usurpés. Par exemple :

- Scénarios légitimes pour l’usurpation des domaines internes :

  - Les expéditeurs tiers utilisent votre domaine pour envoyer du courrier en nombre à vos employés pour les sondages de sociétés.

  - Une société externe génère et envoie des mises à jour de la publicité ou des produits en votre nom.

  - Un assistant doit régulièrement envoyer un message électronique à une autre personne au sein de votre organisation.

  - Une application interne envoie des notifications par courrier électronique.

- Scénarios légitimes pour l’usurpation de domaines externes :

  - L’expéditeur figure sur une liste de publipostage (également appelée liste de discussion) et la liste de distribution relaie le courrier de l’expéditeur d’origine vers tous les participants de la liste de distribution.

  - Une société externe envoie un courrier électronique au nom d’une autre société (par exemple, un rapport automatisé ou une société de service de logiciel).

L’intelligence d’usurpation d’identité, et en particulier la stratégie d’intelligence d’usurpation par défaut (et uniquement), permet de s’assurer que le courrier électronique usurpé envoyé par des expéditeurs légitimes ne se trouve pas dans les filtres de courrier indésirable dans Office 365 ou les systèmes de messagerie externes, tout en protégeant vos utilisateurs contre le courrier indésirable ou le hameçonnage.

Vous pouvez gérer l’intelligence des usurpations d’identité dans le centre de sécurité & de sécurité Office 365 ou dans PowerShell (clients Exchange Online PowerShell pour Office 365 ; Exchange Online Protection PowerShell pour les clients EOP autonomes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://protection.office.com/antispam>. Pour accéder directement à la page **anti-hameçonnage** , utilisez <https://protection.office.com/antiphishing>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection autonome, voir [Se connecter à PowerShell d’Exchange Online Protection](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Pour modifier la stratégie d’aide à la décision d’usurpation d’identité ou activer ou désactiver l’intelligence d’usurpation d’identité, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** . Pour un accès en lecture seule à la stratégie d’aide à la décision, vous devez être membre du groupe de rôles **lecteur de sécurité** . Pour plus d’informations sur les groupes de rôles dans le Centre de sécurité et conformité, voir [Autorisations dans le Centre de sécurité et conformité Office 365](permissions-in-the-security-and-compliance-center.md).

- Pour les paramètres recommandés pour l’aide à l’usurpation, [paramètres de stratégie anti-hameçonnage par défaut EOP](recommended-settings-for-eop-and-office365-atp.md#eop-default-anti-phishing-policy-settings).

## <a name="use-the-security--compliance-center-to-manage-spoofed-senders"></a>Utiliser le centre de sécurité & conformité pour gérer les expéditeurs usurpés

> [!NOTE]
> Si vous disposez d’un abonnement Office 365 entreprise E5 ou si vous avez acheté séparément un complément de protection avancée contre les menaces (ATP), vous pouvez également gérer les expéditeurs qui usurpent votre domaine via la fonctionnalité d’aide à la [décision](walkthrough-spoof-intelligence-insight.md).

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **paramètres de blocage du courrier indésirable** , cliquez ![sur développer](../../media/scc-expand-icon.png) pour développer stratégie d’aide à la **décision**.

   ![Sélectionner la stratégie d’intelligence d’usurpation d’identité](../../media/anti-spam-settings-spoof-intelligence-policy.png)

3. Effectuez l’une des sélections suivantes :

   - **Vérifier les nouveaux expéditeurs**
   - **Afficher les expéditeurs que j’ai déjà consultés**

4. Dans la fenêtre **décider si ces expéditeurs sont autorisés à usurper votre** sélection, sélectionnez l’un des onglets suivants :

   - **Vos domaines**: les expéditeurs usurpant l’identité des utilisateurs dans vos domaines internes.
   - **Domaines externes**: les expéditeurs usurpant l’identité des utilisateurs dans les domaines externes.

5. Cliquez ![sur développer](../../media/scc-expand-icon.png) une icône dans la colonne **autorisé à usurper** . Choisissez **Oui** pour autoriser l’expéditeur usurpé ou **non** pour marquer le message comme falsifié. L’action est contrôlée par la stratégie anti-hameçonnage par défaut ou par des stratégies anti-hameçonnage personnalisées ATP (la valeur par défaut est **déplacer le message vers le dossier courrier indésirable**). Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings).

   ![Capture d’écran montrant le menu volant des expéditeurs falsifiés et indique si l’expéditeur est autorisé à usurper](../../media/c0c062fd-f4a4-4d78-96f7-2c22009052bb.jpg)

   Les colonnes et les valeurs que vous voyez sont expliquées dans la liste suivante :

   - **Utilisateur usurpé**: le compte d’utilisateur qui est usurpé. Il s’agit de l’expéditeur du message dans l’adresse de provenance (également `5322.From` appelée adresse) qui apparaît dans les clients de messagerie. La validité de cette adresse n’est pas vérifiée par SPF.

     - Dans l’onglet **vos domaines** , la valeur contient une adresse de messagerie unique, ou si le serveur de messagerie source usurpe plusieurs comptes d’utilisateur, il en contient **plusieurs**.

     - Sous l’onglet **domaines externes** , la valeur contient le domaine de l’utilisateur usurpé, et non l’adresse de messagerie complète.

   - **Infrastructure d’envoi**: domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source ou adresse IP si la source n’a pas d’enregistrement PTR.

     Pour plus d’informations sur les sources de messages et les expéditeurs de messages, voir [une vue d’ensemble des normes des messages électroniques](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

   - **Nbre de messages**: nombre de messages provenant de l’infrastructure d’envoi à votre organisation qui contiennent l’expéditeur ou les expéditeurs usurpés au cours des 30 derniers jours.

   - **nombre de plaintes de l’utilisateur**: plaintes déposées par vos utilisateurs par rapport à cet expéditeur au cours des 30 derniers jours. Les plaintes se présentent généralement sous la forme d’envois de courrier indésirable à Microsoft.

   - **Résultat de l’authentification**: l’une des valeurs suivantes :

      - **Réussite**: l’expéditeur a passé des vérifications d’authentification de courrier électronique de l’expéditeur (SPF ou DKIM).
      - **Échec**: l’expéditeur a échoué aux vérifications d’authentification de l’expéditeur EOP.
      - **Inconnu**: le résultat de ces vérifications n’est pas connu.

   - **Décision définie par**: indique qui a déterminé si l’infrastructure d’envoi est autorisée à usurper l’identité de l’utilisateur :

       - **Stratégie d’intelligence infalsifiable** (automatique)
       - **Administrateur** (manuel)

   - **Dernière**détection : dernière date à laquelle un message a été reçu de l’infrastructure d’envoi qui contient l’utilisateur usurpé.

   - **Autorisé à usurper ?**: les valeurs que vous voyez ici sont les suivantes :

     - **Oui**: les messages provenant de la combinaison d’une infrastructure utilisateur et d’une infrastructure d’envoi usurpés sont autorisés et ne sont pas traités comme des messages falsifiés.

     - **Non**: les messages provenant de la combinaison d’une infrastructure d’utilisateur et d’expéditeur usurpée sont marqués comme falsifiés. L’action est contrôlée par la stratégie anti-hameçonnage par défaut ou par des stratégies anti-hameçonnage personnalisées ATP (la valeur par défaut est **déplacer le message vers le dossier courrier indésirable**). Pour plus d’informations, consultez la section suivante.

     - **Certains utilisateurs** (**votre onglet domaines** uniquement) : une infrastructure d’envoi usurpe l’identité de plusieurs utilisateurs, où certains utilisateurs usurpés sont autorisés et d’autres non. Utilisez l’onglet **détaillé** pour afficher les adresses spécifiques.

6. Au bas de la page, cliquez sur **Enregistrer**.

## <a name="use-powershell-to-manage-spoofed-senders"></a>Utiliser PowerShell pour gérer les expéditeurs usurpés

Pour afficher les expéditeurs autorisés et bloqués dans l’intelligence des usurpations d’identité, utilisez la syntaxe suivante :

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

Cet exemple renvoie des informations détaillées sur tous les expéditeurs autorisés à usurper des utilisateurs dans vos domaines.

```powershell
Get-PhishFilter -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-PhishFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/advanced-threat-protection/get-phishfilterpolicy).

Pour configurer les expéditeurs autorisés et bloqués dans l’intelligence des usurpations d’identité, procédez comme suit :

1. Capturez la liste actuelle des expéditeurs usurpés détectés en écrivant la sortie de la cmdlet **Get-PhishFilterPolicy** dans un fichier CSV :

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Modifiez le fichier CSV pour ajouter ou modifier les valeurs **SpoofedUser** (adresse de messagerie) et **AllowedToSpoof** (oui ou non). Enregistrez le fichier, lisez le fichier, puis stockez le contenu en tant que `$UpdateSpoofedSenders`variable nommée :

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Utilisez la `$UpdateSpoofedSenders` variable pour configurer la stratégie d’intelligence d’usurpation d’identité :

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-PhishFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/advanced-threat-protection/set-phishfilterpolicy).

## <a name="use-the-security--compliance-center-to-configure-spoof-intelligence"></a>Utiliser le centre de sécurité & conformité pour configurer l’aide à l’usurpation d’identité

Les options de configuration de l’intelligence d’usurpation sont décrites dans la rubrique [usurpation Settings in anti-phishing Policies](set-up-anti-phishing-policies.md#spoof-settings).

Les options disponibles dépendent de votre abonnement :

- Les organisations EOP autonomes sans boîtes aux lettres Exchange Online ne peuvent pas configurer les paramètres d’aide à la décision.

- Les organisations Office 365 avec des boîtes aux lettres Exchange Online peuvent configurer des paramètres d’aide à la décision par défaut (et uniquement). Pour obtenir des instructions, consultez [la rubrique Configurer la stratégie anti-hameçonnage par défaut dans EOP](configure-anti-phishing-policies-eop.md).

- Les organisations Office 365 avec ATP peuvent configurer les paramètres d’aide à la décision contre le hameçonnage par défaut, ainsi que les stratégies anti-hameçonnage personnalisées ATP. Pour obtenir des instructions, consultez la rubrique [configure ATP anti-phishing Policies in Office 365](configure-atp-anti-phishing-policies.md).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez configuré l’intelligence des usurpations d’identité avec des expéditeurs autorisés et non autorisés à usurper, et que vous avez configuré les paramètres d’aide à la décision, suivez l’une des étapes suivantes :

- Dans le centre de sécurité & conformité, accédez à **Policy** \> **protection contre les** \> **menaces** \> -courrier indésirable développer la **stratégie** \> d’intelligence frauduleux : sélectionner **afficher les expéditeurs que j’ai déjà consultés** \> sélectionnez l’onglet **domaines** ou **domaines externes** , et vérifier la valeur **autorisé à usurper ?** pour l’expéditeur.

- Dans PowerShell, exécutez les commandes suivantes pour afficher les expéditeurs autorisés et non autorisés à usurper les conditions suivantes :

  ```powershell
  Get-PhishFilter -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilter -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilter -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilter -AllowedToSpoof No -SpoofType External
  ```

- Dans PowerShell, exécutez la commande suivante pour exporter la liste de tous les expéditeurs usurpés vers un fichier CSV :

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

- Dans les organisations Office 365 avec des boîtes aux lettres Exchange Online, effectuez l’une des opérations suivantes :

  - Dans le centre de sécurité & conformité, accédez à **stratégie** \> de **gestion** \> **des menaces-hameçonnage** \> , cliquez sur **stratégie par défaut** et affichez les détails dans le menu volant.

  - Dans Exchange Online PowerShell, exécutez la commande suivante et vérifiez les paramètres :

    ```PowerShell
    Get-AntiPhishPolicy -Identity "Office365 AntiPhish Default"
    ```

- Dans les organisations Office 365 ATP, effectuez l’une des opérations suivantes :

  - Dans le centre de sécurité & conformité, accédez à **protection contre le hameçonnage** de la **stratégie** \> de **gestion** \> des menaces et effectuez l’une des opérations suivantes :

    - Sélectionnez une stratégie dans la liste. Dans le menu volant qui s’affiche, vérifiez les valeurs de la section **usurpation** .
    - Cliquez sur **stratégie par défaut**. Dans le menu volant qui s’affiche, vérifiez les valeurs de la section **usurpation** .

  - Dans Exchange Online PowerShell, remplacez \<nom\> par la valeur par défaut Office 365 antiphishing ou le nom d’une stratégie anti-hameçonnage personnalisée ATP, puis exécutez la commande suivante et vérifiez les paramètres :

    ```PowerShell
    Get-AntiPhishPolicy -Identity "<Name>"
    ```

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Autres façons de gérer l’usurpation d’identité et le hameçonnage

Soyez très à la protection contre l’usurpation d’identité et la protection antiphishing. Voici des méthodes relatives pour vérifier les expéditeurs qui usurpent votre domaine et les empêcher d’endommager votre organisation :

- Vérifiez le **rapport de courrier infalsifiable**. Vous pouvez utiliser ce rapport fréquemment pour afficher et gérer les expéditeurs usurpés. Pour plus d’informations, reportez-vous à la rubrique [Subdetections Report](view-email-security-reports.md#spoof-detections-report).

- Passez en revue votre configuration SPF (Sender Policy Framework). Pour consulter une brève présentation de SPF et le configurer rapidement, voir [Configurer SPF dans Office 365 pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Pour consulter des informations plus approfondies sur l’utilisation de SPF par Office 365, la résolution des problèmes et les déploiements non standard tels que les déploiements hybrides, voir Comment Office 365 utilise SPF (Sender Policy Framework) pour empêcher l’usurpation d’identité.

- Passez en revue votre configuration DKIM (DomainKeys Identified Identified Mail). Vous devez utiliser DKIM en plus de SPF et de DMARC pour empêcher les agresseurs d’envoyer des messages qui semblent provenir de votre domaine. DKIM vous permet d'ajouter une signature numérique aux messages électroniques dans l'en-tête du message. Pour plus d’informations, consultez [la rubrique use DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Office 365](use-dkim-to-validate-outbound-email.md).

- Passez en revue votre configuration d’authentification de message basée sur un domaine, de création de rapports et de conformité (DMARC). L’implémentation de DMARC avec SPF et DKIM fournit une protection supplémentaire contre l’usurpation et les courriers de hameçonnage. DMARC permet aux systèmes de messagerie de réception de déterminer ce qu’ils doivent faire des messages envoyés à partir de votre domaine qui sont rejetés par les contrôles de SPF ou de DKIM. Pour plus d’informations, consultez la rubrique [utiliser DMARC pour valider le courrier électronique dans Office 365](use-dmarc-to-validate-email.md).
