---
title: Gérer les expéditeurs usurpés à l’aide de la stratégie de renseignement sur l’usurpation d’identité et de l’information sur l’usurpation d’identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à utiliser la stratégie de renseignement sur l’usurpation d’identité et l’information sur l’usurpation d’identité pour autoriser ou bloquer les expéditeurs détectés d’usurpation d’identité.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 59f52e7fe10030283601aad86a1aa49ed91255ab
ms.sourcegitcommit: 363bdc517bd2564c6420cf21f352e97079f950e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2022
ms.locfileid: "65031798"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>Gérer les expéditeurs usurpés à l’aide de la stratégie de renseignement sur l’usurpation d’identité et de l’information sur l’usurpation d’identité dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article décrit l’ancienne expérience de gestion des expéditeurs usurpés qui est remplacée (stratégie **de renseignement sur l’usurpation** d’identité dans la page **Stratégies anti-courrier indésirable** ). Pour plus d’informations sur la nouvelle expérience (l’onglet **Usurpation d’identité** dans la liste d’autorisation/de blocage du locataire), consultez [Spoof Intelligence Insight dans EOP](learn-about-spoof-intelligence.md).

Dans Microsoft 365 organisations avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, les e-mails entrants sont automatiquement protégés contre l’usurpation d’identité par EOP à partir d’octobre 2018. EOP utilise **le renseignement sur l’usurpation** d’identité dans le cadre de la défense globale de votre organisation contre le hameçonnage. Pour plus d’informations, consultez [la protection contre l’usurpation d’identité dans EOP](anti-spoofing-protection.md).

La **stratégie d’usurpation d’identité** par défaut (et uniquement) permet de s’assurer que les e-mails usurpés envoyés par des expéditeurs légitimes ne sont pas interceptés dans les filtres de courrier indésirable EOP tout en protégeant vos utilisateurs contre les attaques par hameçonnage ou de courrier indésirable. Vous pouvez également utiliser **spoof intelligence insight** pour déterminer rapidement quels expéditeurs externes vous envoient légitimement des e-mails non authentifiés (messages provenant de domaines qui ne passent pas les vérifications SPF, DKIM ou DMARC).

Vous pouvez gérer les informations d’usurpation d’identité dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans Exchange Online  boîtes aux lettres).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Stratégies anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour modifier la stratégie de renseignement d’usurpation d’identité ou activer ou désactiver l’usurpation d’identité, vous devez être membre de 
    -   **Gestion de l'organisation**
    -   **Administrateur de sécurité** <u>et</u> **configuration en mode seul** ou gestion de l’organisation **en mode affichage uniquement**.
  - Pour accéder en lecture seule à la stratégie de renseignement sur l’usurpation d’identité, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L'ajout d'utilisateurs au rôle Azure Active Directory Domain Services correspondant dans le centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations requises pour d'autres fonctionnalités dans Microsoft 365. Pour plus d'informations, consultez [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Les options d’intelligence par usurpation d’identité sont [décrites dans les paramètres d’usurpation d’identité dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings).

- Vous pouvez activer, désactiver et configurer les paramètres d’intelligence d’usurpation d’identité dans les stratégies anti-hameçonnage. Pour obtenir des instructions basées sur votre abonnement, consultez l’une des rubriques suivantes :

  - [Configurez des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md).
  - [Configurez des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

- Pour connaître les paramètres recommandés pour l’intelligence par usurpation d’identité, consultez [les paramètres de stratégie anti-hameçonnage EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

## <a name="manage-spoofed-senders"></a>Gérer les expéditeurs usurpés

Il existe deux façons d’autoriser et de bloquer les expéditeurs usurpés :

- [Utiliser la stratégie de renseignement sur l’usurpation d’identité](#manage-spoofed-senders-in-the-spoof-intelligence-policy)
- [Utiliser l’insight d’intelligence de l’usurpation d’identité](#manage-spoofed-senders-in-the-spoof-intelligence-insight)

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-policy"></a>Gérer les expéditeurs usurpés dans la stratégie de renseignement sur l’usurpation d’identité

> [!IMPORTANT]
> Cet article décrit l’ancienne expérience de gestion des expéditeurs usurpés qui est remplacée (stratégie **de renseignement sur l’usurpation** d’identité dans la page **Stratégies anti-courrier indésirable** ). Pour plus d’informations sur la nouvelle expérience (l’onglet **Usurpation d’identité** dans la liste d’autorisation/de blocage du locataire), consultez [Spoof Intelligence Insight dans EOP](learn-about-spoof-intelligence.md).

1. Dans le Portail Microsoft 365 Defender sur <https://security.microsoft.com>, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**. Pour accéder directement à la page **Stratégies anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

2. Dans la page **Stratégies anti-courrier indésirable**, sélectionnez Stratégie de renseignement sur l’usurpation d’identité en cliquant sur le nom.

   :::image type="content" source="../../media/anti-spam-settings-spoof-intelligence-policy.png" alt-text="Option permettant de sélectionner la stratégie de renseignement sur l’usurpation d’identité" lightbox="../../media/anti-spam-settings-spoof-intelligence-policy.png":::

3. Dans le menu volant **de la stratégie de renseignement** sur l’usurpation d’identité qui s’affiche, effectuez l’une des sélections suivantes :
   - **Afficher les expéditeurs que j’ai déjà examinés**
   - **Passer en revue les nouveaux expéditeurs**

4. Dans le volet **Décider si ces expéditeurs sont autorisés à usurper le menu volant de vos utilisateurs** qui s’affiche, sélectionnez l’un des onglets suivants :
   - **Vos domaines : expéditeurs** usurpant des utilisateurs dans vos domaines internes.
   - **Domaines externes : expéditeurs** usurpant des utilisateurs dans des domaines externes.

5. Cliquez sur l’icône ![Développer.](../../media/scc-expand-icon.png) dans la colonne **Autoriser l’usurpation d’identité et** effectuer l’une des sélections suivantes :
   - **Oui** : autorisez l’expéditeur usurpé.
   - **Non** : marquez le message comme usurpé d’identité. L’action est contrôlée par la stratégie anti-hameçonnage par défaut ou les stratégies anti-hameçonnage personnalisées. Si vous souhaitez en savoir plus, consultez l’article [Paramètres d’usurpation dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings).

   :::image type="content" source="../../media/spoof-allow-block-flyout.png" alt-text="Menu volant des expéditeurs usurpés et indique si l’expéditeur est autorisé à usurper l’identité" lightbox="../../media/spoof-allow-block-flyout.png":::

   Les colonnes et valeurs que vous voyez sont expliquées dans la liste suivante :

   - **Utilisateur usurpé** : compte d’utilisateur usurpé. Il s’agit de l’expéditeur du message dans l’adresse From (également appelée `5322.From` adresse) qui s’affiche dans les clients de messagerie. La validité de cette adresse n’est pas vérifiée par SPF.
     - Sous l’onglet **Vos domaines** , la valeur contient une seule adresse e-mail, ou si le serveur de messagerie source usurpe plusieurs comptes d’utilisateur, il en contient **plusieurs**.
     - Sous l’onglet **Domaines externes** , la valeur contient le domaine de l’utilisateur usurpé, et non l’adresse e-mail complète.

   - **Infrastructure d’envoi** : domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source. Si l’adresse IP source n’a pas d’enregistrement PTR, l’infrastructure d’envoi est identifiée comme \<source IP\>/24 (par exemple, 192.168.100.100/24).

     Pour plus d’informations sur les sources de messages et les expéditeurs de messages, consultez [Une vue d’ensemble des normes de courrier électronique](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

   - **Nombre de messages** : nombre de messages de l’infrastructure d’envoi à votre organisation qui contiennent l’expéditeur ou les expéditeurs usurpés spécifiés au cours des 30 derniers jours.

   - **Nombre de plaintes d’utilisateurs** : plaintes déposées par vos utilisateurs contre cet expéditeur au cours des 30 derniers jours. Les plaintes se présentent généralement sous la forme de soumissions indésirables à Microsoft.

   - **Résultat de l’authentification** : l’une des valeurs suivantes :
      - **Passé** : l’expéditeur a passé les vérifications d’authentification par e-mail de l’expéditeur (SPF ou DKIM).
      - **Échec** : échec des vérifications d’authentification de l’expéditeur EOP de l’expéditeur.
      - **Inconnu** : le résultat de ces vérifications n’est pas connu.

   - **Dernière vue** : dernière date à laquelle un message a été reçu de l’infrastructure d’envoi qui contient l’utilisateur usurpé.

   - **Autorisé à usurper l’identité ?** : les valeurs que vous voyez ici sont les suivantes :
     - **Oui** : les messages provenant de la combinaison de l’utilisateur usurpé et de l’infrastructure d’envoi sont autorisés et ne sont pas traités comme des e-mails usurpés.
     - **Non** : les messages de la combinaison de l’utilisateur usurpé et de l’infrastructure d’envoi sont marqués comme usurpés. L’action est contrôlée par la stratégie anti-hameçonnage par défaut ou les stratégies anti-hameçonnage personnalisées (la valeur par défaut est **Déplacer le message vers le dossier Courrier indésirable**). Pour plus d’informations, consultez la section suivante.

     - **Certains utilisateurs** (onglet **Vos domaines** uniquement) : une infrastructure d’envoi usurpe plusieurs utilisateurs, où certains utilisateurs usurpés sont autorisés et d’autres non. Utilisez l’onglet **Détaillé** pour afficher les adresses spécifiques.

6. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

#### <a name="use-powershell-to-manage-spoofed-senders"></a>Utiliser PowerShell pour gérer les expéditeurs usurpés

> [!IMPORTANT]
> Cet article décrit l’ancienne expérience de gestion des expéditeurs usurpés qui est remplacée (stratégie **de renseignement sur l’usurpation** d’identité dans la page **Stratégies anti-courrier indésirable** ). Pour plus d’informations sur la nouvelle expérience (l’onglet **Usurpation d’identité** dans la liste d’autorisation/de blocage du locataire), consultez [Spoof Intelligence Insight dans EOP](learn-about-spoof-intelligence.md).

Pour afficher les expéditeurs autorisés et bloqués dans l’intelligence d’usurpation d’identité, utilisez la syntaxe suivante :

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

Cet exemple retourne des informations détaillées sur tous les expéditeurs autorisés à usurper des utilisateurs dans vos domaines.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Pour configurer les expéditeurs autorisés et bloqués dans l’intelligence d’usurpation d’identité, procédez comme suit :

1. Capturez la liste actuelle des expéditeurs usurpés détectés en écrivant la sortie de l’applet de commande **Get-PhishFilterPolicy** dans un fichier CSV en exécutant la commande suivante :

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Modifiez le fichier CSV pour ajouter ou modifier les valeurs suivantes :
   - **Expéditeur** (domaine dans l’enregistrement PTR du serveur source ou l’adresse IP/24)
   - **SpoofedUser** : l’une des valeurs suivantes :
     - Adresse e-mail de l’utilisateur interne.
     - Domaine de messagerie de l’utilisateur externe.
     - Valeur vide qui indique que vous souhaitez bloquer ou autoriser tous les messages usurpés de **l’expéditeur** spécifié, quelle que soit l’adresse e-mail usurpée.
   - **AllowedToSpoof** (Oui ou Non)
   - **SpoofType** (interne ou externe)

   Enregistrez le fichier, lisez le fichier et stockez le contenu sous la forme d’une variable nommée `$UpdateSpoofedSenders` en exécutant la commande suivante :

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Utilisez la `$UpdateSpoofedSenders` variable pour configurer la stratégie de renseignement sur l’usurpation d’identité en exécutant la commande suivante :

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-insight"></a>Gérer les expéditeurs usurpés dans l’insight d’intelligence de l’usurpation d’identité

> [!IMPORTANT]
> Cet article décrit l’ancienne expérience de gestion des expéditeurs usurpés qui est remplacée (stratégie **de renseignement sur l’usurpation** d’identité dans la page **Stratégies anti-courrier indésirable** ). Pour plus d’informations sur la nouvelle expérience (l’onglet **Usurpation d’identité** dans la liste d’autorisation/de blocage du locataire), consultez [Spoof Intelligence Insight dans EOP](learn-about-spoof-intelligence.md).

1. Dans le Centre de sécurité & conformité, accédez au tableau **de bord de gestion des** \> **menaces**.

2. Dans la ligne **Informations**, recherchez l’un des éléments suivants :

   - **Domaines usurpés probables au cours des sept derniers jours** : cet insight indique que l’intelligence par usurpation d’identité est activée (elle est activée par défaut).
   - **Activer la protection** contre l’usurpation d’identité : cet insight indique que l’intelligence par usurpation d’identité est désactivée, et le fait de cliquer sur l’insight vous permet d’activer l’intelligence par usurpation d’identité.

3. L’insight sur le tableau de bord vous montre des informations comme celle-ci :

   :::image type="content" source="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png" alt-text="L’information sur l’usurpation d’identité" lightbox="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png":::

   Cet insight a deux modes :

   - **Mode Insight** : si l’intelligence par usurpation d’identité est activée, l’insight vous indique le nombre de messages qui ont été affectés par nos fonctionnalités de renseignement sur l’usurpation d’identité au cours des sept derniers jours.
   - **Que se passe-t-il si le mode** : si l’intelligence par usurpation d’identité est désactivée, l’insight vous indique le nombre de messages qui *auraient* été affectés par nos fonctionnalités d’usurpation d’identité au cours des sept derniers jours.

   Dans les deux cas, les domaines usurpés affichés dans l’insight sont séparés en deux catégories : **domaines suspects** et **domaines non suspects**.

   - **Domaines suspects** :
     - **Usurpation de confiance élevée** : en fonction des modèles d’envoi historiques et du score de réputation des domaines, nous sommes très confiants que les domaines sont usurpants, et les messages de ces domaines sont plus susceptibles d’être malveillants.
     - **Usurpation de confiance modérée** : En fonction des modèles d’envoi historiques et du score de réputation des domaines, nous sommes modérément convaincus que les domaines sont usurpants et que les messages envoyés à partir de ces domaines sont légitimes. Les faux positifs sont plus susceptibles dans cette catégorie que l’usurpation de confiance élevée.
   - **Domaines non suspects** : l’authentification par e-mail explicite du domaine a échoué vérifie [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) et [DMARC](use-dmarc-to-validate-email.md). Toutefois, le domaine a passé nos vérifications d’authentification par e-mail implicites ([authentification composite](email-validation-and-authentication.md#composite-authentication)). Par conséquent, aucune action anti-usurpation d’identité n’a été effectuée sur le message.

#### <a name="view-detailed-information-about-suspicious-and-nonsuspicious-domains"></a>Afficher des informations détaillées sur les domaines suspects et non propices

1. Dans spoof intelligence insight, cliquez sur **Domaines suspects** ou **domaines non suspects** pour accéder à la page **d’informations sur l’usurpation d’identité** . La page **Informations sur l’usurpation d’identité** contient les informations suivantes :

   - **Domaine usurpé** : domaine de l’utilisateur usurpé qui s’affiche dans la zone **From** dans les clients de messagerie. Cette adresse est également appelée adresse `5322.From` .
   - **Infrastructure** : également appelée _infrastructure d’envoi_. Domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source. Si l’adresse IP source n’a pas d’enregistrement PTR, l’infrastructure d’envoi est identifiée comme \<source IP\>/24 (par exemple, 192.168.100.100/24).
   - **Nombre** de messages : nombre de messages de l’infrastructure d’envoi à votre organisation qui contiennent le domaine usurpé spécifié au cours des 7 derniers jours.
   - **Dernière vue** : dernière date à laquelle un message a été reçu de l’infrastructure d’envoi qui contient le domaine usurpé.
   - **Type d’usurpation** d’identité : cette valeur est **externe**.
   - **Autorisé à usurper l’identité ?** : les valeurs que vous voyez ici sont les suivantes :
     - **Oui** : les messages provenant de la combinaison du domaine de l’utilisateur usurpé et de l’infrastructure d’envoi sont autorisés et ne sont pas traités comme des e-mails usurpés.
     - **Non** : les messages de la combinaison du domaine de l’utilisateur usurpé et de l’infrastructure d’envoi sont marqués comme usurpés. L’action est contrôlée par la stratégie anti-hameçonnage par défaut ou les stratégies anti-hameçonnage personnalisées (la valeur par défaut est **Déplacer le message vers le dossier Courrier indésirable**).

2. Sélectionnez un élément dans la liste pour afficher des détails sur la paire domaine/envoi d’infrastructure dans un menu volant. Les informations incluent :
   - Pourquoi on a pris ça.
   - Ce que vous devez faire.
   - Récapitulatif du domaine.
   - Données WhoIs sur l’expéditeur.
   - Messages similaires que nous avons vus dans votre locataire à partir du même expéditeur.

   À partir de là, vous pouvez également choisir d’ajouter ou de supprimer la paire domaine/envoi d’infrastructure dans la liste verte **de l’expéditeur autorisé à usurper d’identité** . Définissez simplement le bouton bascule en conséquence.

   :::image type="content" source="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png" alt-text="Un domaine dans le volet Informations sur l’usurpation d’identité" lightbox="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png":::

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez configuré l’intelligence d’usurpation d’identité avec les expéditeurs autorisés et non autorisés à usurper d’identité, effectuez l’une des étapes suivantes :

- Collaboration & \> **par e-mail** **Règles de & de stratégies** \> \> **Stratégies de menace** **Dans** la section **Stratégies**, dans la section \> Stratégie d’usurpation d’identité  \>, **sélectionnez Afficher les expéditeurs que j’ai déjà examinés**\>, sélectionnez l’onglet **Vos domaines** ou **Domaines externes**, puis vérifiez la valeur **Autorisée à usurper ?** pour l’expéditeur.

- Dans PowerShell, exécutez les commandes suivantes pour afficher les expéditeurs autorisés et non autorisés à usurper l’identité :

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- Dans PowerShell, exécutez la commande suivante pour exporter la liste de tous les expéditeurs usurpés dans un fichier CSV :

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
