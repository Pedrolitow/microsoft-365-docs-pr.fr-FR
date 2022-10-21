---
title: Stratégies d’alerte Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkDEFENDER
description: Créez des stratégies d’alerte dans le portail portail de conformité Microsoft Purview ou Microsoft 365 Defender pour surveiller les menaces potentielles, la perte de données et les problèmes d’autorisations.
ms.openlocfilehash: 5057bdc3db61dcd3fd313574c8db411c8b391036
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68663562"
---
# <a name="alert-policies-in-microsoft-365"></a>Stratégies d’alerte dans Microsoft 365

Vous pouvez utiliser des stratégies d’alerte et le tableau de bord d’alerte dans le portail de conformité Microsoft Purview ou le portail Microsoft 365 Defender pour créer des stratégies d’alerte, puis afficher les alertes générées lorsque les utilisateurs effectuent des activités qui correspondent aux conditions d’une stratégie d’alerte. Il existe plusieurs stratégies d’alerte par défaut qui vous aident à surveiller les activités telles que l’attribution de privilèges d’administrateur dans Exchange Online, les attaques par programme malveillant, les campagnes d’hameçonnage et les niveaux inhabituels de suppressions de fichiers et de partage externe.

> [!TIP]
> Accédez à la section [Stratégies d’alerte par défaut](#default-alert-policies) de cet article pour obtenir la liste et la description des stratégies d’alerte disponibles.

Les politiques d'alerte vous permettent de catégoriser les alertes déclenchées par une politique, d'appliquer cette politique à tous les utilisateurs de votre organisation, de définir un niveau de seuil pour le déclenchement d'une alerte et de décider si vous souhaitez recevoir des notifications par courriel lorsque des alertes sont déclenchées. Il existe également une page **Alertes** dans laquelle vous pouvez afficher et filtrer les alertes, définir un état d’alerte pour vous aider à gérer les alertes, puis ignorer les alertes une fois que vous avez résolu ou résolu l’incident sous-jacent.

> [!NOTE]
> Les stratégies d’alerte sont disponibles pour les organisations disposant d’un abonnement Microsoft 365 Entreprise, Office 365 Entreprise ou Office 365 gouvernement des États-Unis E1/F1/G1, E3/F3/G3 ou E5/G5. Les fonctionnalités avancées sont disponibles uniquement pour les organisations disposant d’un abonnement E5/G5, ou pour les organisations disposant d’un abonnement E1/F1/G1 ou E3/F3/G3 et d’un abonnement Microsoft Defender pour Office 365 P2 ou Microsoft 365 E5 Conformité ou E5 eDiscovery et Audit. La fonctionnalité qui nécessite un abonnement E5/G5 ou un abonnement complémentaire est mise en évidence dans cette rubrique. Notez également que les stratégies d’alerte sont disponibles dans Office 365 environnements gcc, GCC High et DoD us government.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-alert-policies-work"></a>Fonctionnement des stratégies d’alerte

Voici une vue d’ensemble rapide du fonctionnement des stratégies d’alerte et des alertes déclenchées lorsque l’activité de l’utilisateur ou de l’administrateur correspond aux conditions d’une stratégie d’alerte.

![Vue d’ensemble du fonctionnement des stratégies d’alerte.](../media/M365ComplianceDefender-AlertPolicies-Overview.png)

1. Un administrateur de votre organisation crée, configure et active une stratégie d’alerte à l’aide de la page **Stratégies d’alerte** du portail de conformité ou du portail Microsoft 365 Defender. Vous pouvez également créer des stratégies d’alerte à l’aide de l’applet [de commande New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) dans PowerShell Security & Compliance.

   Pour créer des stratégies d’alerte, vous devez disposer du rôle Gérer les alertes ou Configuration de l’organisation dans le portail de conformité ou le portail Defender.

   > [!NOTE]
   > Il faut jusqu’à 24 heures après la création ou la mise à jour d’une stratégie d’alerte avant que les alertes puissent être déclenchées par la stratégie. Cela est dû au fait que la stratégie doit être synchronisée avec le moteur de détection des alertes.

2. Un utilisateur effectue une activité qui correspond aux conditions d’une stratégie d’alerte. En cas d’attaques par programme malveillant, les messages électroniques infectés envoyés aux utilisateurs de votre organisation déclenchent une alerte.

3. Microsoft 365 génère une alerte qui s’affiche sur la page **Alertes** du portail de conformité ou du portail Defender. En outre, si les notifications par e-mail sont activées pour la stratégie d’alerte, Microsoft envoie une notification à une liste de destinataires. Les alertes qu’un administrateur ou d’autres utilisateurs peuvent voir dans la page Alertes sont déterminées par les rôles attribués à l’utilisateur. Pour plus d’informations, consultez [Autorisations RBAC requises pour afficher les alertes](#rbac-permissions-required-to-view-alerts).

4. Un administrateur gère les alertes dans le portail de conformité Microsoft Purview. La gestion des alertes consiste à attribuer un état d’alerte pour faciliter le suivi et la gestion de toute investigation.

## <a name="alert-policy-settings"></a>Paramètres de stratégie d’alerte

Une politique d'alerte consiste en un ensemble de règles et de conditions qui définissent l'activité de l'utilisateur ou de l'administrateur qui génère une alerte, une liste d'utilisateurs qui déclenchent l'alerte s'ils effectuent l'activité, et un seuil qui définit combien de fois l'activité doit se produire avant qu'une alerte soit déclenchée. Vous classez également la stratégie et lui affectez un niveau de gravité. Ces deux paramètres vous aident à gérer les stratégies d’alerte (et les alertes déclenchées lorsque les conditions de stratégie sont mises en correspondance), car vous pouvez filtrer sur ces paramètres lors de la gestion des stratégies et de l’affichage des alertes dans le portail de conformité Microsoft Purview. Par exemple, vous pouvez afficher les alertes qui correspondent aux conditions de la même catégorie ou afficher les alertes avec le même niveau de gravité.

Pour afficher et créer des stratégies d’alerte :

- **portail de conformité Microsoft Purview** :

  Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a>, puis sélectionnez **Stratégies** \> **d’alerte Stratégies d’alerte**\>.

  ![Dans le portail de conformité Microsoft Purview, sélectionnez Stratégies, puis sous Alerte, sélectionnez Stratégies d’alerte pour afficher et créer des stratégies d’alerte.](../media/LaunchAlertPoliciesMCC.png)

- **Microsoft 365 Defender portail** :

  Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> et sous **Email & collaboration**, sélectionnez **Stratégies & règles** \> **Stratégie d’alerte**. Vous pouvez également accéder directement à <https://security.microsoft.com/alertpolicies>.

  ![Dans le portail Defender, sélectionnez Stratégies & règles sous Email & collaboration, puis sélectionnez Stratégie d’alerte pour afficher et créer des stratégies d’alerte.](../media/LaunchAlertPoliciesDefenderPortal.png)

> [!NOTE]
> Vous devez disposer du rôle View-Only Gérer les alertes pour afficher les stratégies d’alerte dans le portail de conformité Microsoft Purview ou le portail Microsoft 365 Defender. Le rôle Gérer les alertes doit vous être attribué pour créer et modifier des stratégies d’alerte. Pour plus d’informations, consultez la rubrique [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md).

Une stratégie d’alerte se compose des paramètres et conditions suivants.

- **Activité que l’alerte suit**. Vous créez une stratégie pour suivre une activité ou, dans certains cas, quelques activités connexes, telles qu’un partage d’un fichier avec un utilisateur externe en le partageant, en attribuant des autorisations d’accès ou en créant un lien anonyme. Lorsqu’un utilisateur effectue l’activité définie par la stratégie, une alerte est déclenchée en fonction des paramètres de seuil d’alerte.

    > [!NOTE]
    > Les activités que vous pouvez suivre dépendent de la Office 365 Entreprise de votre organisation ou Office 365 plan du gouvernement des États-Unis. En général, les activités liées aux campagnes de programmes malveillants et aux attaques par hameçonnage nécessitent un abonnement E5/G5 ou un abonnement E1/F1/G1 ou E3/F3/G3 avec un abonnement [Defender pour Office 365](../security/office-365-security/defender-for-office-365.md) Plan 2.

- **Conditions d’activité**. Pour la plupart des activités, vous pouvez définir des conditions supplémentaires qui doivent être remplies pour déclencher une alerte. Les conditions courantes incluent les adresses IP (afin qu’une alerte soit déclenchée lorsque l’utilisateur effectue l’activité sur un ordinateur avec une adresse IP spécifique ou dans une plage d’adresses IP), si une alerte est déclenchée si un utilisateur spécifique effectue cette activité et si l’activité est effectuée sur un nom de fichier ou une URL spécifique. Vous pouvez également configurer une condition qui déclenche une alerte lorsque l’activité est effectuée par un utilisateur de votre organisation. Les conditions disponibles dépendent de l’activité sélectionnée.

Vous pouvez également définir des balises utilisateur comme condition d’une stratégie d’alerte. Il en résulte les alertes déclenchées par la stratégie pour inclure le contexte de l’utilisateur concerné. Vous pouvez utiliser des balises utilisateur système ou des étiquettes utilisateur personnalisées. Pour plus d’informations, consultez [Balises utilisateur dans Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/user-tags).

- **Lorsque l’alerte est déclenchée**. Vous pouvez configurer un paramètre qui définit la fréquence à laquelle une activité peut se produire avant le déclenchement d’une alerte. Cela vous permet de configurer une stratégie pour générer une alerte chaque fois qu’une activité correspond aux conditions de stratégie, lorsqu’un certain seuil est dépassé ou lorsque l’occurrence de l’activité que l’alerte suit devient inhabituelle pour votre organisation.

    ![Configurez la façon dont les alertes sont déclenchées, en fonction du moment où l’activité se produit, d’un seuil ou d’une activité inhabituelle pour votre organisation.](../media/howalertsaretriggered.png)

    Si vous sélectionnez le paramètre en fonction d’une activité inhabituelle, Microsoft établit une valeur de base qui définit la fréquence normale de l’activité sélectionnée. L’établissement de cette base de référence prend jusqu’à sept jours, pendant lesquels les alertes ne seront pas générées. Une fois la ligne de base établie, une alerte est déclenchée lorsque la fréquence de l’activité suivie par la stratégie d’alerte dépasse considérablement la valeur de base. Pour les activités liées à l’audit (telles que les activités de fichiers et de dossiers), vous pouvez établir une base de référence basée sur un seul utilisateur ou sur tous les utilisateurs de votre organisation. Pour les activités liées aux programmes malveillants, vous pouvez établir une base de référence basée sur une seule famille de programmes malveillants, un seul destinataire ou tous les messages de votre organisation.

    > [!NOTE]
    > La possibilité de configurer des stratégies d’alerte en fonction d’un seuil ou d’une activité inhabituelle nécessite un abonnement E5/G5, ou un abonnement E1/F1/G1 ou E3/F3/G3 avec un abonnement Microsoft Defender pour Office 365 P2, Microsoft 365 E5 Conformité ou Microsoft 365 eDiscovery and Audit. Les organisations disposant d’un abonnement E1/F1/G1 et E3/F3/G3 peuvent uniquement créer des stratégies d’alerte lorsqu’une alerte est déclenchée chaque fois qu’une activité se produit.

- **Catégorie d’alerte**. Pour faciliter le suivi et la gestion des alertes générées par une stratégie, vous pouvez affecter l’une des catégories suivantes à une stratégie.

  - Protection contre la perte de données
  - Gouvernance des informations
  - Flux de messagerie
  - Autorisations
  - Gestion des menaces
  - Autres

  Lorsqu’une activité qui correspond aux conditions de la stratégie d’alerte se produit, l’alerte générée est marquée avec la catégorie définie dans ce paramètre. Cela vous permet de suivre et de gérer les alertes qui ont le même paramètre de catégorie dans la page **Alertes** du portail Microsoft Purview, car vous pouvez trier et filtrer les alertes en fonction de la catégorie.

- **Gravité de l’alerte**. Comme pour la catégorie d’alerte, vous affectez un attribut de gravité (**Faible**, **Moyen**, **Élevé** ou **Informationnel**) aux stratégies d’alerte. Comme pour la catégorie d'alerte, lorsqu'une activité correspondant aux conditions de la politique d'alerte se produit, l'alerte générée est étiquetée avec le même niveau de gravité que celui défini pour la politique d'alerte. Là encore, cela vous permet de suivre et de gérer les alertes qui ont le même paramètre de gravité dans la page **Alertes** . Par exemple, vous pouvez filtrer la liste des alertes afin que seules les alertes avec une gravité **élevée** soient affichées.

    > [!TIP]
    > Lors de la configuration d’une stratégie d’alerte, envisagez d’affecter une gravité plus élevée à des activités qui peuvent entraîner des conséquences négatives graves, telles que la détection de programmes malveillants après la remise aux utilisateurs, l’affichage de données sensibles ou classifiées, le partage de données avec des utilisateurs externes ou d’autres activités pouvant entraîner une perte de données ou des menaces de sécurité. Cela peut vous aider à hiérarchiser les alertes et les actions que vous effectuez pour examiner et résoudre les causes sous-jacentes.

- **Enquêtes automatisées**. Certaines alertes déclenchent des investigations automatisées pour identifier les menaces et les risques potentiels qui nécessitent une correction ou une atténuation. Dans la plupart des cas, ces alertes sont déclenchées par la détection d’e-mails ou d’activités malveillants, mais dans certains cas, les alertes sont déclenchées par des actions de l’administrateur dans le portail de sécurité. Pour plus d’informations sur les investigations automatisées, consultez [Investigation et réponse automatisées (AIR) dans Microsoft Defender pour Office 365](../security/office-365-security/office-365-air.md).

- **Email notifications**. Vous pouvez configurer la stratégie afin que les notifications par e-mail soient envoyées (ou non) à une liste d’utilisateurs lorsqu’une alerte est déclenchée. Vous pouvez également définir une limite de notification quotidienne afin qu’une fois le nombre maximal de notifications atteint, aucune autre notification ne soit envoyée pour l’alerte au cours de cette journée. En plus des notifications par e-mail, vous ou d’autres administrateurs pouvez afficher les alertes déclenchées par une stratégie dans la page **Alertes** . Envisagez d’activer les notifications par e-mail pour les stratégies d’alerte d’une catégorie spécifique ou qui ont un paramètre de gravité plus élevé.

## <a name="default-alert-policies"></a>Stratégies d’alerte par défaut

Microsoft fournit des stratégies d’alerte intégrées qui permettent d’identifier les abus d’autorisations d’administrateur Exchange, l’activité des programmes malveillants, les menaces externes et internes potentielles et les risques de gouvernance des informations. Dans la page **Stratégies d’alerte** , les noms de ces stratégies intégrées sont en gras et le type de stratégie est défini comme **Système**. Ces stratégies sont activées par défaut. Vous pouvez désactiver ces stratégies (ou réactiver), configurer une liste de destinataires auxquels envoyer des notifications par e-mail et définir une limite de notification quotidienne. Les autres paramètres de ces stratégies ne peuvent pas être modifiés.

Les tableaux suivants répertorient et décrivent les stratégies d’alerte par défaut disponibles et la catégorie à laquelle chaque stratégie est affectée. La catégorie est utilisée pour déterminer les alertes qu’un utilisateur peut afficher dans la page Alertes. Pour plus d’informations, consultez [Autorisations RBAC requises pour afficher les alertes](#rbac-permissions-required-to-view-alerts).

Les tableaux indiquent également les Office 365 Entreprise et Office 365 plan du gouvernement des États-Unis requis pour chacun d’eux. Certaines stratégies d’alerte par défaut sont disponibles si votre organisation dispose de l’abonnement complémentaire approprié en plus d’un abonnement E1/F1/G1 ou E3/F3/G3.

> [!NOTE]
> L’activité inhabituelle surveillée par certaines des stratégies intégrées est basée sur le même processus que le paramètre de seuil d’alerte décrit précédemment. Microsoft établit une valeur de base qui définit la fréquence normale de l’activité « habituelle ». Les alertes sont ensuite déclenchées lorsque la fréquence des activités suivies par la stratégie d’alerte intégrée dépasse considérablement la valeur de base.

### <a name="information-governance-alert-policies"></a>Stratégies d’alerte de gouvernance des informations

> [!NOTE]
> Les stratégies d’alerte de cette section sont en cours de dépréciation en fonction des commentaires des clients en tant que faux positifs. Pour conserver les fonctionnalités de ces stratégies d’alerte, vous pouvez créer des stratégies d’alerte personnalisées avec les mêmes paramètres.

|Nom|Description|Severity|Investigation automatisée|Abonnement Entreprise|
|---|---|---|---|---|
|**Activité inhabituelle des fichiers d’utilisateur externe**|Génère une alerte lorsqu’un nombre inhabituellement élevé d’activités sont effectuées sur des fichiers dans SharePoint ou OneDrive par des utilisateurs extérieurs à votre organisation. Cela inclut des activités telles que l’accès aux fichiers, le téléchargement de fichiers et la suppression de fichiers.|Élevé|Non|Abonnement E5/G5, Microsoft Defender pour Office 365 P2 ou Microsoft 365 E5 extension|
|**Volume inhabituel de partage de fichiers externes**|Génère une alerte lorsqu’un nombre inhabituellement élevé de fichiers dans SharePoint ou OneDrive sont partagés avec des utilisateurs en dehors de votre organisation.|Moyen|Non|Abonnement E5/G5, Defender pour Office 365 P2 ou Microsoft 365 E5 extension|
|**Volume inhabituel de suppression de fichier**|Génère une alerte lorsqu’un nombre inhabituellement élevé de fichiers sont supprimés dans SharePoint ou OneDrive dans un court laps de temps.|Moyen|Non|Abonnement E5/G5, Defender pour Office 365 P2 ou Microsoft 365 E5 extension|

### <a name="mail-flow-alert-policies"></a>Stratégies d’alerte de flux de messagerie

|Nom|Description|Severity|Investigation automatisée|Abonnement Entreprise|
|---|---|---|---|---|
|**Les messages ont été retardés**|Génère une alerte lorsque Microsoft ne peut pas remettre des messages électroniques à votre organisation locale ou à un serveur partenaire à l’aide d’un connecteur. Dans ce cas, le message est mis en file d’attente dans Office 365. Cette alerte est déclenchée lorsqu’au moins 2 000 messages sont mis en file d’attente depuis plus d’une heure.|Élevé|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|

### <a name="permissions-alert-policies"></a>Stratégies d’alerte d’autorisations

|Nom|Description|Severity|Investigation automatisée|Abonnement Entreprise|
|---|---|---|---|---|
|**Élévation du privilège d’administrateur Exchange**|Génère une alerte lorsqu’une personne se voit attribuer des autorisations d’administration dans votre organisation Exchange Online. Par exemple, lorsqu’un utilisateur est ajouté au groupe de rôles Gestion de l’organisation dans Exchange Online.|Faible|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|

### <a name="threat-management-alert-policies"></a>Stratégies d’alerte de gestion des menaces

|Nom|Description|Severity|Investigation automatisée|Abonnement Entreprise|
|---|---|---|---|---|
|**Un clic d’URL potentiellement malveillant a été détecté**|Génère une alerte lorsqu’un utilisateur protégé par [des liens](/microsoft-365/security/office-365-security/safe-links) fiables dans votre organisation clique sur un lien malveillant. Cette alerte est générée lorsqu’un utilisateur clique sur un lien et que cet événement déclenche une identification de changement de verdict d’URL par Microsoft Defender pour Office 365. Cette alerte déclenche automatiquement une [investigation et une réponse automatisées dans Office 365](/microsoft-365/security/office-365-security/office-365-air). Pour plus d’informations sur les événements qui déclenchent cette alerte, consultez [Configurer des stratégies de liens fiables](/microsoft-365/security/office-365-security/set-up-safe-links-policies).|Élevé|Oui|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Un utilisateur a cliqué sur une URL potentiellement malveillante**|Génère une alerte lorsqu’un utilisateur protégé par [des liens](/microsoft-365/security/office-365-security/safe-links) fiables dans votre organisation clique sur un lien malveillant. Cet événement est déclenché lorsque l’utilisateur clique sur une URL (qui est identifiée comme malveillante ou en attente de validation) et remplace la page d’avertissement liens fiables (basée sur la stratégie liens fiables Microsoft 365 pour les entreprises de votre organisation) pour passer à la page/au contenu hébergé par l’URL. Pour Defender pour Office 365 clients P2, E5 et G5, cette alerte déclenche automatiquement une [investigation et une réponse automatisées dans Office 365](/microsoft-365/security/office-365-security/office-365-air). Pour plus d’informations sur les événements qui déclenchent cette alerte, consultez [Configurer des stratégies de liens fiables](/microsoft-365/security/office-365-security/set-up-safe-links-policies).|Élevé|Oui|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Administration résultat de la soumission terminée**|Génère une alerte lorsqu’une [soumission de Administration](../security/office-365-security/admin-submission.md) termine la nouvelle analyse de l’entité envoyée. Une alerte est déclenchée chaque fois qu’un résultat de nouvelle analyse est rendu à partir d’une soumission Administration. <br/><br/> Ces alertes sont destinées à vous rappeler [d’examiner les résultats des soumissions précédentes](https://compliance.microsoft.com/reportsubmission), d’envoyer des messages signalés par l’utilisateur pour obtenir la dernière vérification de stratégie et d’analyser à nouveau les verdicts, et de vous aider à déterminer si les stratégies de filtrage de votre organisation ont l’impact prévu.|Informatif|Non|E1/F1, E3/F3 ou E5|
|**Administration’examen manuel des e-mails a été déclenché**|Génère une alerte lorsqu’un administrateur déclenche l’examen manuel d’un e-mail à partir de l’Explorateur de menaces. Pour plus d’informations, consultez [Exemple : Un administrateur de sécurité déclenche une investigation à partir de l’Explorateur de menaces](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer). <br/><br/> Cette alerte informe votre organisation que l’enquête a été lancée. L’alerte fournit des informations sur les personnes qui l’ont déclenchée et inclut un lien vers l’enquête.|Informatif|Oui|Abonnement au module complémentaire E5/G5 ou Microsoft Defender pour Office 365 P2|
|**Administration’enquête sur la compromission de l’utilisateur déclenchée**|Génère une alerte lorsqu’un administrateur déclenche l’examen manuel de compromission utilisateur d’un expéditeur ou d’un destinataire d’e-mail à partir de l’Explorateur de menaces. Pour plus d’informations, consultez [Exemple : Un administrateur de sécurité déclenche une investigation à partir de l’Explorateur de](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) menaces, qui montre le déclenchement manuel associé d’une investigation sur un e-mail. Cette alerte informe votre organisation que l’enquête de compromission de l’utilisateur a été lancée. <br/><br/> L’alerte fournit des informations sur les personnes qui l’ont déclenchée et inclut un lien vers l’enquête.|Moyen|Oui|Abonnement au module complémentaire E5/G5 ou Microsoft Defender pour Office 365 P2|
|**Action administrative soumise par un administrateur**|Les administrateurs peuvent effectuer des actions manuelles par e-mail sur les entités de messagerie à l’aide de différentes surfaces. Par exemple, l’Explorateur de menaces, la chasse avancée ou la détection personnalisée. Lorsque la correction démarre, elle génère une alerte. Cette alerte s’affiche dans la file d’attente des alertes avec le nom **Action administrative soumise par un administrateur** pour indiquer qu’un administrateur a effectué l’action de correction d’une entité. L’alerte contient des détails tels que le type d’action, le lien d’investigation de prise en charge, l’heure, etc. Il est utile de savoir quand une action sensible telle que la correction est effectuée sur les entités.|Informatif|Oui|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Création de règle de redirection/transfert**|Génère une alerte lorsqu’une personne de votre organisation crée une règle de boîte de réception pour sa boîte aux lettres qui transfère ou redirige les messages vers un autre compte de messagerie. Cette stratégie suit uniquement les règles de boîte de réception créées à l’aide de Outlook sur le web (anciennement Outlook Web App) ou Exchange Online PowerShell. Pour plus d’informations sur l’utilisation de règles de boîte de réception pour transférer et rediriger des messages électroniques dans Outlook sur le web, consultez [Utiliser des règles dans Outlook sur le web pour transférer automatiquement des messages vers un autre compte](https://support.office.com/article/1433e3a0-7fb0-4999-b536-50e05cb67fed).|Informatif|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Recherche eDiscovery démarrée ou exportée**|Génère une alerte lorsqu’une personne utilise l’outil de recherche de contenu dans le portail Microsoft Purview. Une alerte est déclenchée lorsque les activités de recherche de contenu suivantes sont effectuées : <br><br> <li> Une recherche de contenu est démarrée <li> Les résultats d’une recherche de contenu sont exportés <li> Un rapport de recherche de contenu est exporté <br><br> Des alertes sont également déclenchées lorsque les activités de recherche de contenu précédentes sont effectuées en association avec un cas eDiscovery. Pour plus d’informations sur les activités de recherche de contenu, consultez [Rechercher des activités eDiscovery dans le journal d’audit](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-activities).|Informatif|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Messages de courrier contenant un fichier malveillant supprimé après la remise**|Génère une alerte quand des messages contenant un fichier malveillant sont remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés de Exchange Online boîtes aux lettres à l’aide du [vidage automatique zéro heure](../security/office-365-security/zero-hour-auto-purge.md). Cette stratégie déclenche automatiquement une [investigation et une réponse automatisées dans Office 365](../security/office-365-security/office-365-air.md). Pour plus d’informations sur cette nouvelle stratégie, consultez [Nouvelles stratégies d’alerte dans Microsoft Defender pour Office 365](new-defender-alert-policies.md).|Informatif|Oui|Abonnement au module complémentaire E5/G5 ou Microsoft Defender pour Office 365 P2|
|**Messages de courrier contenant une URL malveillante supprimée après la remise**|Génère une alerte quand des messages contenant une URL malveillante sont remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés de Exchange Online boîtes aux lettres à l’aide du [vidage automatique zéro heure](../security/office-365-security/zero-hour-auto-purge.md). Cette stratégie déclenche automatiquement une [investigation et une réponse automatisées dans Office 365](../security/office-365-security/office-365-air.md). Pour plus d’informations sur cette nouvelle stratégie, consultez [Nouvelles stratégies d’alerte dans Microsoft Defender pour Office 365](new-defender-alert-policies.md).|Informatif|Oui|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Messages de courrier contenant un programme malveillant supprimé après la remise**|**Remarque** : cette stratégie d’alerte a été remplacée par **Email messages contenant des fichiers malveillants supprimés après la remise**. Cette stratégie d’alerte finira par disparaître. Nous vous recommandons donc de désactiver cette stratégie d’alerte et d’utiliser **Email messages contenant des fichiers malveillants supprimés après la remise**. Pour plus d’informations, consultez [Nouvelles stratégies d’alerte dans Microsoft Defender pour Office 365](new-defender-alert-policies.md).|Informatif|Oui|Abonnement au module complémentaire E5/G5 ou Microsoft Defender pour Office 365 P2|
|**Messages de courrier contenant des URL d’hameçonnage supprimées après la remise**|**Remarque** : Cette stratégie d’alerte a été remplacée par **des messages Email contenant des URL malveillantes supprimées après la remise**. Cette stratégie d’alerte finira par disparaître. Nous vous recommandons donc de désactiver cette stratégie d’alerte et d’utiliser **Email messages contenant des URL malveillantes supprimées après la remise**. Pour plus d’informations, consultez [Nouvelles stratégies d’alerte dans Microsoft Defender pour Office 365](new-defender-alert-policies.md).|Informatif|Oui|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Email messages d’une campagne supprimés après la remise**|Génère une alerte quand des messages associés à une [campagne](../security/office-365-security/campaigns.md) sont remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés de Exchange Online boîtes aux lettres à l’aide du [vidage automatique zéro heure](../security/office-365-security/zero-hour-auto-purge.md). Cette stratégie déclenche automatiquement une [investigation et une réponse automatisées dans Office 365](../security/office-365-security/office-365-air.md). Pour plus d’informations sur cette nouvelle stratégie, consultez [Nouvelles stratégies d’alerte dans Microsoft Defender pour Office 365](new-defender-alert-policies.md).|Informatif|Oui|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Messages électroniques supprimés après la remise**|Génère une alerte quand des messages malveillants qui ne contiennent pas d’entité malveillante (URL ou fichier) ou associés à une campagne sont remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés de Exchange Online boîtes aux lettres à l’aide du [vidage automatique zéro heure](../security/office-365-security/zero-hour-auto-purge.md). Cette stratégie déclenche automatiquement une [investigation et une réponse automatisées dans Office 365](../security/office-365-security/office-365-air.md). Pour plus d’informations sur cette nouvelle stratégie, consultez [Nouvelles stratégies d’alerte dans Microsoft Defender pour Office 365](new-defender-alert-policies.md).|Informatif|Oui|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**E-mail signalé par l’utilisateur en tant que programme malveillant ou hameçonnage**|Génère une alerte lorsque les utilisateurs de votre organisation signalent des messages en tant qu’e-mail d’hameçonnage à l’aide du complément Signaler un message. Pour plus d’informations sur ce complément, consultez [Utiliser le complément De message de rapport](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2). Pour Defender pour Office 365 clients P2, E5 et G5, cette alerte déclenche automatiquement une [investigation et une réponse automatisées dans Office 365](../security/office-365-security/office-365-air.md).|Faible|Oui|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Email limite d’envoi dépassée**|Génère une alerte lorsqu’une personne de votre organisation a envoyé plus de messages que ce qui est autorisé par la stratégie de courrier indésirable sortant. Cela indique généralement que l’utilisateur envoie trop d’e-mails ou que le compte peut être compromis. Si vous recevez une alerte générée par cette stratégie d’alerte, il est judicieux de [vérifier si le compte d’utilisateur est compromis](../security/office-365-security/responding-to-a-compromised-email-account.md).|Moyen|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Formulaire bloqué en raison d’une tentative d’hameçonnage potentielle**|Génère une alerte lorsqu’une personne de votre organisation a été empêchée de partager des formulaires et de collecter des réponses à l’aide de Microsoft Forms en raison d’un comportement de tentative d’hameçonnage répété détecté.|Élevé|Non|E1, E3/F3 ou E5|
|**Formulaire marqué d'un indicateur et confirmé comme hameçonnage**|Génère une alerte lorsqu’un formulaire créé dans Microsoft Forms au sein de votre organisation a été identifié comme un hameçonnage potentiel via Signaler un abus et confirmé comme hameçonnage par Microsoft.|Élevé|Non|E1, E3/F3 ou E5|
|**Campagne de programmes malveillants détecté après la livraison**<sup>\*</sup>|Génère une alerte lorsqu’un nombre inhabituellement élevé de messages contenant des programmes malveillants sont remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés de Exchange Online boîtes aux lettres.|Élevé|Non|Abonnement au module complémentaire E5/G5 ou Microsoft Defender pour Office 365 P2|
|**Campagne de programmes malveillants détectée et bloquée**<sup>\*</sup>|Génère une alerte lorsqu’une personne a tenté d’envoyer un nombre inhabituellement élevé de messages électroniques contenant un certain type de programme malveillant aux utilisateurs de votre organisation. Si cet événement se produit, les messages infectés sont bloqués par Microsoft et ne sont pas remis aux boîtes aux lettres.|Faible|Non|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Campagne de programmes malveillants détecté dans SharePoint et OneDrive**<sup>\*</sup>|Génère une alerte lorsqu’un volume inhabituellement élevé de programmes malveillants ou de virus est détecté dans des fichiers situés dans des sites SharePoint ou des comptes OneDrive de votre organisation.|Élevé|Non|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Programme malveillant non zapé, car ZAP est désactivé**| Génère une alerte lorsque Microsoft détecte la remise d’un message malveillant à une boîte aux lettres, car Zero-Hour purge automatique des messages de hameçonnage est désactivé.|Informatif|Non|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Messages contenant une entité malveillante non supprimée après la remise**|Génère une alerte lorsqu’un message contenant du contenu malveillant (fichier, URL, campagne, aucune entité) est remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft a tenté de supprimer les messages infectés de Exchange Online boîtes aux lettres à l’aide du [vidage automatique zero-hour](../security/office-365-security/zero-hour-auto-purge.md), mais le message n’a pas été supprimé en raison d’un échec. Une investigation supplémentaire est recommandée. Cette stratégie déclenche automatiquement une [investigation et une réponse automatisées dans Office 365](../security/office-365-security/office-365-air.md).|Moyen|Oui|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Hameçonnage remis parce que le dossier courrier indésirable d’un utilisateur est désactivé**|**Remarque** : cette stratégie d’alerte est en cours de dépréciation. Les paramètres de boîte aux lettres ne déterminent plus si les messages détectés peuvent être déplacés vers le dossier Email indésirables. Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online](/microsoft-365/security/office-365-security/configure-junk-email-settings-on-exo-mailboxes).|Informatif|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Hameçonnage livré en raison d’un remplacement ETR**<sup>\*\*</sup>|Génère une alerte lorsque Microsoft détecte une règle de transport Exchange (également appelée règle de flux de courrier) qui a autorisé la remise d’un message d’hameçonnage à haut niveau de confiance à une boîte aux lettres. Pour plus d’informations sur les règles de transport Exchange (règles de flux de courrier), consultez [Règles de flux de courrier (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).|Informatif|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Hameçonnage livré en raison d’une stratégie d’autorisation d’adresse IP**<sup>\*\*</sup>|Génère une alerte lorsque Microsoft détecte une stratégie d’autorisation d’adresse IP qui autorisait la remise d’un message d’hameçonnage à haut niveau de confiance à une boîte aux lettres. Pour plus d’informations sur la stratégie d’autorisation IP (filtrage de connexion), consultez [Configurer la stratégie de filtre de connexion par défaut - Office 365](../security/office-365-security/configure-the-connection-filter-policy.md).|Informatif|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Hameçonnage non zapé, car ZAP est désactivé**<sup>\*\*</sup>|Génère une alerte lorsque Microsoft détecte la remise d’un message d’hameçonnage à haut niveau de confiance dans une boîte aux lettres, car Zero-Hour purge automatique des messages hameçonnage est désactivé.|Informatif|Non|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Activité potentielle de l’État-nation**|Microsoft Threat Intelligence Center a détecté une tentative de compromission des comptes de votre locataire.|Élevé|Non|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Action de correction effectuée par l’administrateur sur les e-mails, l’URL ou l’expéditeur**|**Remarque** : Cette stratégie d’alerte a été remplacée par **l’action administrative soumise par une stratégie d’alerte Administrateur** . Cette stratégie d’alerte finira par disparaître. Nous vous recommandons donc de désactiver cette stratégie d’alerte et d’utiliser **l’action administrative envoyée par un administrateur** à la place. <br/><br/> Cette alerte est déclenchée lorsqu’un administrateur effectue une action de correction sur l’entité sélectionnée|Informatif|Oui|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Activité suspecte du connecteur**|Génère une alerte lorsqu’une activité suspecte est détectée sur un connecteur entrant dans votre organisation. Le courrier ne peut pas utiliser le connecteur entrant. L’administrateur reçoit une notification par e-mail et une alerte. Cette alerte fournit des conseils sur la façon d’examiner, d’annuler les modifications et de débloquer un connecteur restreint. Pour savoir comment répondre à cette alerte, consultez [Répondre à un connecteur compromis](/microsoft-365/security/office-365-security/respond-compromised-connector).|Élevé|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Activité suspecte de transfert d’e-mail**|Génère une alerte lorsqu’une personne de votre organisation a envoyé automatiquement un e-mail à un compte externe suspect. Il s’agit d’un avertissement précoce pour un comportement qui peut indiquer que le compte est compromis, mais pas assez sévère pour restreindre l’utilisateur. Bien qu’elle soit rare, une alerte générée par cette stratégie peut être une anomalie. Il est judicieux de [vérifier si le compte d’utilisateur est compromis](../security/office-365-security/responding-to-a-compromised-email-account.md).|Élevé|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Modèles d’envoi d’e-mails suspects détectés**|Génère une alerte lorsqu’une personne de votre organisation a envoyé des e-mails suspects et qu’elle risque d’être empêchée d’envoyer des e-mails. Il s’agit d’un avertissement précoce pour un comportement qui peut indiquer que le compte est compromis, mais pas suffisamment sévère pour restreindre l’utilisateur. Bien qu’elle soit rare, une alerte générée par cette stratégie peut être une anomalie. Toutefois, il est judicieux de [vérifier si le compte d’utilisateur est compromis](../security/office-365-security/responding-to-a-compromised-email-account.md).|Moyen|Oui|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**L’entrée d’autorisation/liste bloquée du locataire est sur le point d’expirer**|Génère une alerte lorsqu’une entrée d’autorisation/liste de blocage de locataire est sur le point d’être supprimée. Cet événement est déclenché trois jours avant la date d’expiration, qui est basée sur la date de création ou de dernière mise à jour de l’entrée. <br/><br/> Pour les blocs, vous pouvez étendre la date d’expiration pour conserver le bloc en place. Pour les permis, vous devez soumettre à nouveau l’élément afin que nos analystes puissent jeter un autre coup d’œil. Toutefois, si l’autorisation a déjà été classée comme faux positif, l’entrée n’expire que lorsque les filtres système ont été mis à jour pour autoriser naturellement l’entrée. Pour plus d’informations sur les événements qui déclenchent cette alerte, consultez [Gérer la liste Des locataires autorisés/bloqués](../security/office-365-security/tenant-allow-block-list.md).|Informatif|Non|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**Le locataire n’est pas autorisé à envoyer des e-mails**|Génère une alerte lorsque la majeure partie du trafic de courrier électronique de votre organisation a été détectée comme suspecte et que Microsoft a restreint l’envoi de messages électroniques à votre organisation. Examinez les comptes d’utilisateur et d’administrateur potentiellement compromis, les nouveaux connecteurs ou les relais ouverts, puis contactez Support Microsoft pour débloquer votre organisation. Pour plus d’informations sur la raison pour laquelle les organisations sont bloquées, consultez [Résoudre les problèmes de remise des e-mails pour le code d’erreur 5.7.7xx dans Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Élevé|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Le locataire est limité à l’envoi d’e-mails non approvisionnés**|Génère une alerte lorsque trop d’e-mails sont envoyés à partir de domaines non inscrits (également appelés domaines _non approvisionnés_ ). Office 365 autorise l'envoi d'un certain nombre d'e-mails à partir de domaines non enregistrés, mais nous vous recommandons de configurer chaque domaine utilisé pour envoyer du courrier en tant que domaine accepté. Cette alerte indique que tous les utilisateurs de l’organisation ne peuvent plus envoyer d’e-mail. Pour plus d’informations sur la raison pour laquelle les organisations sont bloquées, consultez [Résoudre les problèmes de remise des e-mails pour le code d’erreur 5.7.7xx dans Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Élevé|Non|E1/F1/G1, E3/F3/G3 ou E5/G5|
|**Augmentation inhabituelle des e-mails signalés comme hameçonnage**<sup>\*</sup>|Génère une alerte en cas d’augmentation significative du nombre de personnes au sein de votre organisation qui utilisent le complément Signaler un message dans Outlook pour signaler les messages en tant que courrier d’hameçonnage. Pour plus d’informations sur ce complément, consultez [Utiliser le complément De message de rapport](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).|Moyen|Non|Abonnement au module complémentaire E5/G5 ou Defender pour Office 365 P2|
|**L’utilisateur a demandé à publier un message mis en quarantaine**|Génère une alerte lorsqu’un utilisateur demande la libération d’un message mis en quarantaine. Pour demander la libération des messages mis en quarantaine, l’autorisation **Autoriser les destinataires à demander la libération d’un message de la quarantaine** (_PermissionToRequestRelease_) est requise dans la stratégie de mise en quarantaine (par exemple, à partir du groupe Autorisations **prédéfinies à accès limité** ). Pour plus d’informations, consultez [Autoriser les destinataires à demander la libération d’un message de l’autorisation de mise en quarantaine](../security/office-365-security/quarantine-policies.md#allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission).|Informatif|Non|Microsoft Business Basic, Microsoft Business Standard, Microsoft Business Premium, E1/F1/G1, E3/F3/G3 ou E5/G5|
|**L’utilisateur n’est pas autorisé à envoyer des e-mails**|Génère une alerte lorsqu’une personne de votre organisation n’est pas autorisé à envoyer des messages sortants. Cela se produit généralement lorsqu’un compte est compromis et que l’utilisateur est répertorié dans la page **Utilisateurs restreints** du portail de conformité. (Pour accéder à cette page, accédez à **Gestion des menaces \> Passer en revue les \> utilisateurs restreints**). Pour plus d’informations sur les utilisateurs restreints, consultez [Suppression d’un utilisateur, d’un domaine ou d’une adresse IP d’une liste bloquée après l’envoi d’un courrier indésirable](/office365/securitycompliance/removing-user-from-restricted-users-portal-after-spam).|Élevé|Oui|Microsoft Business Basic, Microsoft Business Standard, Microsoft Business Premium, E1/F1/G1, E3/F3/G3 ou E5/G5|
|**L’utilisateur ne peut pas partager de formulaires et collecter des réponses**.|Génère une alerte lorsqu’une personne de votre organisation a été empêchée de partager des formulaires et de collecter des réponses à l’aide de Microsoft Forms en raison d’un comportement de tentative d’hameçonnage répété détecté.|Élevé|Non|E1, E3/F3 ou E5|

<sup>\*</sup> Cette stratégie d’alerte est en cours de dépréciation en fonction des commentaires des clients en tant que faux positif. Pour conserver les fonctionnalités de cette stratégie d’alerte, vous pouvez créer une stratégie d’alerte personnalisée avec les mêmes paramètres.

<sup>\*\*</sup> Cette stratégie d’alerte fait partie des fonctionnalités de remplacement des stratégies **d’alerte Hameçon remises en raison d’une substitution de locataire ou d’utilisateur et** de **phish d’emprunt d’identité d’utilisateur remises aux stratégies d’alerte de boîte de réception/dossier** qui ont été supprimées en fonction des commentaires de l’utilisateur. Pour plus d’informations sur l’anti-hameçonnage dans Office 365, consultez [Configurer des stratégies anti-hameçonnage et anti-hameçonnage](../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="view-alerts"></a>Afficher les alertes

Lorsqu’une activité effectuée par des utilisateurs de votre organisation correspond aux paramètres d’une stratégie d’alerte, une alerte est générée et affichée sur la page **Alertes** du portail Microsoft Purview ou du portail Defender. Selon les paramètres d’une stratégie d’alerte, une notification par e-mail est également envoyée à une liste d’utilisateurs spécifiés lorsqu’une alerte est déclenchée. Pour chaque alerte, le tableau de bord de la page **Alertes** affiche le nom de la stratégie d’alerte correspondante, la gravité et la catégorie de l’alerte (définies dans la stratégie d’alerte), ainsi que le nombre de fois où une activité s’est produite et que l’alerte a été générée. Cette valeur est basée sur le paramètre de seuil de la stratégie d’alerte. Le tableau de bord affiche également l’état de chaque alerte. Pour plus d’informations sur l’utilisation de la propriété status pour gérer les alertes, consultez [Gestion des alertes](#manage-alerts).

Pour afficher les alertes :

### <a name="microsoft-purview-compliance-portal"></a>Portail de conformité Microsoft Purview

 Accédez à <https://compliance.microsoft.com> , puis sélectionnez **Alertes**. Vous pouvez également accéder directement à <https://compliance.microsoft.com/compliancealerts>.

![Dans le portail de conformité, sélectionnez Alertes.](../media/ViewAlertsMCC.png)

### <a name="microsoft-365-defender-portal"></a>Portail Microsoft 365 Defender

Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a>, puis sélectionnez **Incidents & alertes** > **Alertes**. Vous pouvez également accéder directement à <https://security.microsoft.com/alerts>.

![Dans le portail Microsoft 365 Defender, sélectionnez Incidents & alertes, puis Alertes.](../media/ViewAlertsDefenderPortal.png)

Vous pouvez utiliser les filtres suivants pour afficher un sous-ensemble de toutes les alertes dans la page **Alertes** :

- **État** : affiche les alertes auxquelles un état particulier est attribué. L’état par défaut est **Actif**. Vous ou d’autres administrateurs pouvez modifier la valeur d’état.
- **Stratégie** : afficher les alertes qui correspondent au paramètre d’une ou plusieurs stratégies d’alerte. Vous pouvez également afficher toutes les alertes pour toutes les stratégies d’alerte.
- **Intervalle de temps** : affiche les alertes qui ont été générées dans un intervalle de date et d’heure spécifique.
- **Gravité** : affiche les alertes auxquelles une gravité spécifique est affectée.
- **Catégorie** : afficher les alertes d’une ou plusieurs catégories d’alertes.
- **Balises** : afficher les alertes d’une ou plusieurs balises utilisateur. Les étiquettes sont reflétées en fonction des boîtes aux lettres étiquetées ou des utilisateurs qui apparaissent dans les alertes. Pour en savoir plus, [consultez Étiquettes utilisateur dans Defender pour Office 365](../security/office-365-security/user-tags.md).
- **Source** : utilisez ce filtre pour afficher les alertes déclenchées par des stratégies d’alerte dans le portail Microsoft Purview ou les alertes déclenchées par des stratégies Microsoft Defender for Cloud Apps, ou les deux. Pour plus d’informations sur les alertes Defender for Cloud Apps, consultez la section [Afficher les alertes Defender for Cloud Apps](#view-defender-for-cloud-apps-alerts) de cet article.

> [!IMPORTANT]
> Le filtrage et le tri par étiquettes utilisateur sont actuellement en préversion publique et peuvent être considérablement modifiés avant d’être mis à la disposition générale. Microsoft n’offre aucune garantie, expresse ou implicite, concernant les informations fournies à son sujet.

## <a name="alert-aggregation"></a>Agrégation d’alertes

Lorsque plusieurs événements qui correspondent aux conditions d’une stratégie d’alerte se produisent sur une courte période, ils sont ajoutés à une alerte existante par un processus appelé _agrégation d’alertes_. Lorsqu’un événement déclenche une alerte, l’alerte est générée et affichée sur la page **Alertes** et une notification est envoyée. Si le même événement se produit dans l’intervalle d’agrégation, Microsoft 365 ajoute des détails sur le nouvel événement à l’alerte existante au lieu de déclencher une nouvelle alerte. L’objectif de l’agrégation des alertes est de réduire la « fatigue » des alertes et de vous permettre de vous concentrer et d’agir sur moins d’alertes pour le même événement.

La longueur de l’intervalle d’agrégation dépend de votre abonnement Office 365 ou Microsoft 365.

|Abonnement|Agrégation<br>interval|
|---|:---:|
|Office 365 ou Microsoft 365 E5/G5|1 minute|
|Microsoft Defender pour Office 365 Plan 2 |1 minute|
|Module complémentaire de conformité E5 ou module complémentaire de découverte et d’audit E5|1 minute|
|Office 365 ou Microsoft 365 E1/F1/G1 ou E3/F3/G3|15 minutes|
|Defender pour Office 365 Plan 1 ou Exchange Online Protection|15 minutes|

Lorsque des événements qui correspondent à la même stratégie d’alerte se produisent dans l’intervalle d’agrégation, des détails sur l’événement suivant sont ajoutés à l’alerte d’origine. Pour tous les événements, des informations sur les événements agrégés sont affichées dans le champ détails et le nombre de fois où un événement s’est produit avec l’intervalle d’agrégation est affiché dans le champ activité/nombre d’accès. Vous pouvez afficher plus d’informations sur toutes les instances d’événements agrégés en consultant la liste des activités.

La capture d’écran suivante montre une alerte avec quatre événements agrégés. La liste des activités contient des informations sur les quatre messages électroniques pertinents pour l’alerte.

![Exemple d’agrégation d’alertes.](../media/AggregatedAlertExample.png)

Gardez les éléments suivants à l’esprit sur l’agrégation des alertes :

- Les alertes déclenchées par la stratégie [d’alerte par défaut](#default-alert-policies) **Un clic sur une URL potentiellement malveillante a été détectée** ne sont pas agrégées. Cela est dû au fait que les alertes déclenchées par cette stratégie sont propres à chaque utilisateur et à chaque e-mail.

- À ce stade, la propriété Alerte **de nombre** de correspondances n’indique pas le nombre d’événements agrégés pour toutes les stratégies d’alerte. Pour les alertes déclenchées par ces stratégies d’alerte, vous pouvez afficher les événements agrégés en cliquant sur **Afficher la liste des messages** ou **Afficher l’activité** sur l’alerte. Nous nous efforçons de rendre disponible le nombre d’événements agrégés répertoriés dans la propriété d’alerte **nombre** d’accès pour toutes les stratégies d’alerte.

## <a name="rbac-permissions-required-to-view-alerts"></a>Autorisations RBAC requises pour afficher les alertes

Les autorisations RBAC (Role Based Access Control) attribuées aux utilisateurs de votre organisation déterminent les alertes qu’un utilisateur peut voir dans la page **Alertes**. Comment cela est-il accompli ? Les rôles de gestion attribués aux utilisateurs (en fonction de leur appartenance à des groupes de rôles dans le portail de conformité ou le portail Microsoft 365 Defender) déterminent les catégories d’alerte qu’un utilisateur peut voir dans la page **Alertes**. Voici quelques exemples :

- Les membres du groupe de rôles Gestion des documents ne peuvent visualiser que les alertes générées par les politiques d'alerte auxquelles est attribuée la catégorie **Gouvernance de l'information**.
- Les membres du groupe de rôles Administrateur de la conformité ne peuvent pas visualiser les alertes générées par les politiques d'alerte auxquelles est attribuée la catégorie **Gestion des menaces**.
- Les membres du groupe de rôles eDiscovery Manager ne peuvent pas afficher d'alertes car aucun des rôles attribués ne permet d'afficher les alertes d'une quelconque catégorie d'alerte.

Cette conception (basée sur les autorisations RBAC) vous permet de déterminer quelles alertes peuvent être consultées (et gérées) par les utilisateurs dans des rôles de travail spécifiques dans votre organisation.

Le tableau suivant répertorie les rôles requis pour afficher les alertes des six catégories d’alertes différentes. Une coche indique qu’un utilisateur auquel ce rôle est attribué peut afficher les alertes de la catégorie d’alerte correspondante répertoriée dans la ligne de titre.

Pour connaître la catégorie à laquelle une stratégie d’alerte par défaut est affectée, consultez les tableaux dans [Stratégies d’alerte par défaut](#default-alert-policies).

|Rôle|Informations<br>Gouvernance|Perte de données<br>Prévention|Courrier<br>Flux|Autorisations|Menaces<br>gestion|Autres|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|Administrateur de conformité|✔|✔||✔||✔|
|Gestion de la conformité DLP||✔|||||
|Administrateur Information Protection||✔|||||
|Analyste Information Protection||✔|||||
|Enquêteur Information Protection||✔|||||
|Gérer les alertes||||||✔|
|Configuration de l’organisation||||||✔|
|Gestion de la confidentialité|||||||
|Quarantaine|||||||
|Gestion des enregistrements|✔||||||
|Gestion de la rétention|✔||||||
|Gestion des rôles||||✔|||
|Administrateur de sécurité||✔||✔|✔|✔|
|Lecteur de sécurité||✔||✔|✔|✔|
|Hygiène du transport|||||||
|View-Only gestion de la conformité DLP||✔|||||
|Afficher uniquement la configuration|||||||
|View-Only Gérer les alertes||||||✔|
|Afficher uniquement les destinataires|||✔||||
|gestion des enregistrements View-Only|✔||||||
|gestion de la rétention View-Only|✔||||||

> [!TIP]
> Pour afficher les rôles attribués à chacun des groupes de rôles par défaut, exécutez les commandes suivantes dans Security & Compliance PowerShell :
>
> ```powershell
> $RoleGroups = Get-RoleGroup
>
> $RoleGroups | foreach {Write-Output -InputObject `r`n,$_.Name,("-"*25); Get-RoleGroup $_.Identity | Select-Object -ExpandProperty Roles}
> ```
>
> Vous pouvez également afficher les rôles attribués à un groupe de rôles dans le portail de conformité ou le portail Microsoft 365 Defender. Accédez à la page **Autorisations** , puis sélectionnez un groupe de rôles. Les rôles attribués sont répertoriés dans la page de menu volant.

## <a name="manage-alerts"></a>Gérer des alertes

Une fois les alertes générées et affichées dans la page **Alertes** du portail Microsoft Purview, vous pouvez les trier, les examiner et les résoudre. Les mêmes [autorisations RBAC](#rbac-permissions-required-to-view-alerts) qui donnent aux utilisateurs l’accès aux alertes leur donnent également la possibilité de gérer les alertes.

Voici quelques tâches que vous pouvez effectuer pour gérer les alertes.

- **Affecter un état aux alertes** : vous pouvez affecter l’un des états suivants aux alertes : **Actif** (valeur par défaut), **Examen**, **Résolution** ou **Ignoré**. Ensuite, vous pouvez filtrer sur ce paramètre pour afficher les alertes avec le même paramètre d’état. Ce paramètre d’état peut vous aider à suivre le processus de gestion des alertes.

- **Afficher les détails de l’alerte** : vous pouvez sélectionner une alerte pour afficher une page de menu volant avec des détails sur l’alerte. Les informations détaillées dépendent de la stratégie d’alerte correspondante, mais elles incluent généralement les informations suivantes :

  - Nom de l’opération réelle qui a déclenché l’alerte, par exemple une applet de commande ou une opération de journal d’audit.
  - Description de l’activité qui a déclenché l’alerte.
  - L’utilisateur (ou la liste des utilisateurs) qui a déclenché l’alerte. Cela est inclus uniquement pour les stratégies d’alerte configurées pour suivre un seul utilisateur ou une seule activité.
  - Nombre de fois où l’activité suivie par l’alerte a été effectuée. Ce nombre peut ne pas correspondre au nombre réel d’alertes associées répertoriées dans la page Alertes, car d’autres alertes peuvent avoir été déclenchées.
  - Lien vers une liste d’activités qui inclut un élément pour chaque activité effectuée qui a déclenché l’alerte. Chaque entrée de cette liste identifie le moment où l’activité s’est produite, le nom de l’opération réelle (par exemple, « FileDeleted »), l’utilisateur qui a effectué l’activité, l’objet (tel qu’un fichier, un cas eDiscovery ou une boîte aux lettres) sur lequel l’activité a été effectuée et l’adresse IP de l’ordinateur de l’utilisateur. Pour les alertes liées aux programmes malveillants, ce lien renvoie à une liste de messages.
  - Nom (et lien) de la stratégie d’alerte correspondante.

- **Supprimer les notifications par e-mail** : vous pouvez désactiver (ou supprimer) les notifications par e-mail à partir de la page de menu volant pour une alerte. Lorsque vous supprimez des notifications par e-mail, Microsoft n’envoie pas de notifications lorsque des activités ou des événements qui correspondent aux conditions de la stratégie d’alerte se produisent. Toutefois, les alertes sont déclenchées lorsque les activités effectuées par les utilisateurs correspondent aux conditions de la stratégie d’alerte. Vous pouvez également désactiver les notifications par e-mail en modifiant la stratégie d’alerte.

- **Résoudre les alertes** : vous pouvez marquer une alerte comme résolue sur la page volante d’une alerte (ce qui définit l’état de l’alerte sur **Résolu**). Sauf si vous modifiez le filtre, les alertes résolues ne s’affichent pas dans la page **Alertes** .

## <a name="view-defender-for-cloud-apps-alerts"></a>Afficher les alertes Defender for Cloud Apps

Les alertes déclenchées par les stratégies Defender for Cloud Apps s’affichent désormais sur la page **Alertes** du portail Microsoft Purview. Cela inclut les alertes déclenchées par les stratégies d’activité et les alertes déclenchées par les stratégies de détection d’anomalie dans Defender for Cloud Apps. Cela signifie que vous pouvez afficher toutes les alertes dans le portail Microsoft Purview. Defender for Cloud Apps est disponible uniquement pour les organisations disposant d’un abonnement Office 365 Entreprise E5 ou Office 365 us Government G5. Pour plus d’informations, consultez [Vue d’ensemble de Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security).

Les organisations qui ont Microsoft Defender for Cloud Apps dans le cadre d’un abonnement Enterprise Mobility + Security E5 ou en tant que service autonome peuvent également afficher les alertes Defender for Cloud Apps liées aux applications et services Microsoft 365 dans le portail de conformité ou le Microsoft 365 Defender portail.

Pour afficher uniquement les alertes Defender for Cloud Apps dans le portail Microsoft Purview ou le portail Defender, utilisez le filtre **Source** et sélectionnez **Defender pour les applications cloud**.

![Utilisez le filtre Source pour afficher uniquement les alertes Defender for Cloud Apps.](../media/FilterCASAlerts.png)

À l’instar d’une alerte déclenchée par une stratégie d’alerte dans le portail Microsoft Purview, vous pouvez sélectionner une alerte Defender for Cloud Apps pour afficher une page de menu volant avec des détails sur l’alerte. L’alerte inclut un lien pour afficher les détails et gérer l’alerte dans le portail Defender for Cloud Apps, ainsi qu’un lien vers la stratégie Defender for Cloud Apps correspondante qui a déclenché l’alerte. Consultez [Surveiller les alertes dans Defender for Cloud Apps](/cloud-app-security/monitor-alerts).

![Les détails de l’alerte contiennent des liens vers le portail Defender for Cloud Apps.](../media/CASAlertDetail.png)

> [!IMPORTANT]
> La modification de l’état d’une alerte Defender for Cloud Apps dans le portail Microsoft Purview ne met pas à jour l’état de résolution de la même alerte dans le portail Defender for Cloud Apps. Par exemple, si vous marquez l’état de l’alerte comme **Résolu** dans le portail Microsoft Purview, l’état de l’alerte dans le portail Defender for Cloud Apps reste inchangé. Pour résoudre ou ignorer une alerte Defender for Cloud Apps, gérez-la dans le portail Defender for Cloud Apps.
