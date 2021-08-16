---
title: Renforcer la protection contre les menaces
f1.keywords:
- NOCSH
ms.author: sharik
author: Skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 5abfef7b-5957-484a-b06b-a7c55e013e44
description: Obtenir de l’aide pour augmenter le niveau de protection dans Microsoft 365
ms.openlocfilehash: 840c9ba2db5408d539722db45528a3db728698b311e55a7c3803cee32468aafa
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53887707"
---
# <a name="increase-threat-protection-for-microsoft-365-subscription"></a>Renforcer la protection contre les menaces pour Microsoft 365 abonnement

Cet article vous aide à renforcer la protection de votre abonnement Microsoft 365 protection contre le hameçonnage, les programmes malveillants et d’autres menaces. Ces recommandations sont appropriées pour les organisations ayant un besoin accru de sécurité, telles que les campagnes électorales, les bureaux juridiques et les organismes de santé.

Avant de commencer, vérifiez votre score de sécurité Microsoft. Le Niveau de sécurité Microsoft analyse la sécurité de votre organisation en fonction de vos activités régulières et de vos paramètres de sécurité et affecte un score. Commencez par prendre note de votre score actuel. La prise des actions recommandées dans cet article augmente votre score. L’objectif n’est pas d’atteindre le score maximum, mais de prendre en compte les opportunités de protection de votre environnement qui n’affectent pas la productivité de vos utilisateurs.

Pour plus d’informations, voir [Le Score de sécurité Microsoft.](../security/defender/microsoft-secure-score.md)

## <a name="raise-the-level-of-protection-against-malware-in-mail"></a>Augmenter le niveau de protection contre les programmes malveillants dans le courrier électronique

Votre environnement Office 365 ou Microsoft 365 inclut une protection contre les programmes malveillants, mais vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants. Pour faire monter en haut la protection contre les programmes malveillants dans les e-mails :

1. Connectez-vous <https://protection.office.com> avec vos informations d’identification de compte d’administrateur.

2. In the Security & Compliance Center, in the left navigation pane, under **Threat management**, choose **Policy** \> **Anti-Malware**.

3. Double-cliquez sur la stratégie par défaut pour modifier cette stratégie à l’échelle de l’entreprise.

4. Cliquez sur **Paramètres**.

5. Sous **Filtre Types de pièces jointes courants,** **sélectionnez Sur**. Les types de fichiers bloqués sont répertoriés dans la fenêtre directement sous ce contrôle. Veillez à ajouter les types de fichiers ci-après :

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   Vous pouvez ajouter ou supprimer des types de fichiers ultérieurement, si nécessaire.

6. Cliquez sur **Enregistrer**.

Pour plus d’informations, voir [Protection contre les programmes malveillants dans EOP.](../security/office-365-security/anti-malware-protection.md)

## <a name="protect-against-ransomware"></a>Se protéger contre les rançongiciels

Un ransomware limite l’accès aux données en chiffrant des fichiers ou en verrouiller les écrans d’ordinateur. Il tente ensuite d’extorquer de l’argent à des personnes victime en demandant « rançon », généralement sous la forme de cryptomonnaies telles que Cryptograph, en échange de l’accès aux données.

Vous pouvez vous protéger contre les ransomware en créant une ou plusieurs règles de flux de messagerie pour bloquer les extensions de fichiers couramment utilisées pour les ransomware (celles-ci ont été ajoutées lors de l’augmentation du niveau de [protection](#raise-the-level-of-protection-against-malware-in-mail) contre les programmes malveillants à l’étape de messagerie), ou pour avertir les utilisateurs qui reçoivent ces pièces jointes par courrier électronique.

Outre les fichiers que vous avez bloqués à l’étape précédente, il est également bon de créer une règle pour avertir les utilisateurs avant d’ouvrir des pièces jointes Office fichiers qui incluent des macros. Les ransomware peuvent être masqués dans les macros, donc avertissez les utilisateurs de ne pas ouvrir ces fichiers à partir de personnes qu’ils ne connaissent pas.

Pour créer une règle de transport de messagerie :

1. Go to the admin center at <https://admin.microsoft.com> and choose Admin **centers** \> **Exchange**.

2. Dans la catégorie **de flux de messagerie,** cliquez sur **Règles.**

3. Cliquez **+** sur , puis cliquez sur Créer une **règle.**

4. Cliquez **sur Plus d’options** en bas de la boîte de dialogue pour voir l’ensemble complet des options.

5. Appliquez les paramètres du tableau suivant pour la règle. Laissez le reste des paramètres par défaut, sauf si vous souhaitez les modifier.

6. Cliquez sur **Save (Enregistrer)**.

|Paramètre|Avertir les utilisateurs avant d’ouvrir les pièces jointes Office fichiers|
|---|---|
|Nom|Règle anti-ransomware : avertir les utilisateurs|
|Appliquez cette règle si . . .|N’importe quelle pièce jointe . . . l’extension de fichier correspond à . . .|
|Spécifier des mots ou des expressions|Ajoutez les types de fichiers ci-après : <br/> `dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm`|
|Faites les choses suivantes . . .|Avertir le destinataire avec un message|
|Fournir le texte du message|N’ouvrez pas ces types de fichiers à partir de personnes que vous ne connaissez pas, car elles peuvent contenir des macros contenant du code malveillant.|

Pour plus d’informations, voir :

- [Ransomware : comment réduire les risques](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Restaurer votre OneDrive](https://support.microsoft.com//office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="stop-auto-forwarding-for-email"></a>Arrêter le forwarding automatique pour le courrier électronique

Les pirates informatiques qui accèdent à la boîte aux lettres d’un utilisateur peuvent dérober votre courrier en l’insérez pour qu’elle les envoie automatiquement. Cela peut se produire même sans la sensibilisation de l’utilisateur. Vous pouvez empêcher cela en configurant une règle de flux de messagerie.

Pour créer une règle de transport de messagerie, regardez [cette courte vidéo](https://support.office.com/article/f9d693ba-5c78-47c0-b156-8e461e062aa7) ou suivez les étapes suivantes :

1. Dans la Centre d’administration Microsoft 365, cliquez **sur Centres d’administration** \> **Exchange**.

2. Dans la catégorie **de flux de messagerie,** cliquez sur **Règles.**

3. Cliquez **+** sur , puis cliquez sur Créer une **règle.**

4. Cliquez **sur Plus d’options** en bas de la boîte de dialogue pour voir l’ensemble complet des options.

5. Appliquez les paramètres du tableau suivant. Laissez le reste des paramètres par défaut, sauf si vous souhaitez les modifier.

6. Cliquez sur **Save (Enregistrer)**.

|Paramètre|Avertir les utilisateurs avant d’ouvrir les pièces jointes Office fichiers|
|---|---|
|Nom|Empêcher le forwarding automatique du courrier électronique vers des domaines externes|
|Appliquez cette règle si...|L’expéditeur . . . est externe/interne . . . À l’intérieur de l’organisation|
|Ajouter une condition|Propriétés du message . . . inclure le type de message . . . Auto-forward|
|Faites les choses suivantes ...|Bloquer le message . . . rejeter le message et inclure une explication.|
|Fournir le texte du message|Le courrier électronique à l’extérieur de cette organisation est interdit pour des raisons de sécurité.|

## <a name="protect-your-email-from-phishing-attacks"></a>Protéger votre courrier électronique contre les attaques par hameçonnage

Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Office 365 ou Microsoft 365, vous pouvez configurer une protection anti-hameçonnage ciblée. La protection anti-hameçonnage, qui fait partie de Microsoft Defender pour Office 365, peut vous aider à protéger votre organisation contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillant et d’autres attaques par hameçonnage. Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin de le faire.

Nous vous recommandons de commencer avec cette protection en créant une stratégie pour protéger vos utilisateurs les plus importants et votre domaine personnalisé.

Pour créer une stratégie anti-hameçonnage dans Defender pour Office 365, regardez cette courte vidéo de [formation](https://support.office.com/article/86c425e1-1686-430a-9151-f7176cce4f2c)ou suivez les étapes suivantes :

1. Accédez à <https://protection.office.com>.

2. In the Security & Compliance Center, in the left navigation pane, under **Threat management**, choose **Policy**.

3. Dans la page **Stratégie,** choisissez **Anti-hameçonnage.**

4. Dans la page **Anti-hameçonnage,** **sélectionnez + Créer.** Un Assistant vous lance pour définir votre stratégie anti-hameçonnage.

5. Spécifiez le nom, la description et les paramètres de votre stratégie comme recommandé dans le graphique ci-dessous. Pour plus d’informations, voir [La stratégie anti-hameçonnage](../security/office-365-security/set-up-anti-phishing-policies.md)dans Microsoft Defender pour Office 365 options.

6. Une fois que vous avez examiné vos paramètres, **sélectionnez Créer cette** stratégie ou **Enregistrer,** le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Domaine et personnel le plus précieux|
|Description|Assurez-vous que le personnel le plus important et notre domaine ne sont pas usurpés.|
|Ajouter des utilisateurs à protéger|Select **+ Add a condition, The recipient is**. Tapez des noms d’utilisateurs ou entrez l’adresse e-mail des propriétaires d’entreprise, des partenaires ou du candidat, des responsables et d’autres membres importants du personnel. Vous pouvez ajouter jusqu’à 20 adresses internes et externes que vous souhaitez protéger contre l’emprunt d’identité.|
|Ajouter des domaines à protéger|Sélectionnez **+ Ajoutez une condition, le domaine du destinataire est**. Entrez le domaine personnalisé associé à votre abonnement Microsoft 365, si vous en avez défini un. Vous pouvez entrer plusieurs domaines.|
|Choisir des actions|Si un message électronique est envoyé par un utilisateur dont l’identité est emprunt d’identité : sélectionnez **Rediriger le message** vers une autre adresse de messagerie, puis tapez l’adresse e-mail de l’administrateur de sécurité . par exemple, *Alice <span> <span> @contoso.com*. <br/> Si le courrier électronique est envoyé par un domaine dont l’identité a été empruntée : sélectionnez **Mettre le message en quarantaine**.|
|Veille des boîtes aux lettres|Par défaut, la veille des boîtes aux lettres est activée lorsque vous créez une stratégie anti-hameçonnage. Laissez ce paramètre **activé** pour obtenir de meilleurs résultats.|
|Ajouter des expéditeurs et domaines de confiance|Ici, vous pouvez ajouter votre propre domaine ou tout autre domaine approuvé.|
|Appliqué à|Sélectionnez **Le domaine du destinataire est**. Sous **Un de ces éléments**, sélectionnez **Choisir**. Sélectionnez **+ Ajouter**. Cochez la case en regard du nom du domaine, par *exemple, contoso. <span> <span> com*, dans la liste, puis sélectionnez **Ajouter**. Sélectionnez **Terminé**.|

Pour plus d’informations, voir [Configurer des stratégies anti-hameçonnage dans Defender pour Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="protect-against-malicious-attachments-files-and-links-with-defender-for-office-365"></a>Se protéger contre les pièces jointes, les fichiers et les liens malveillants avec Defender for Office 365

![Bannière pointant vers https://aka.ms/aboutM365preview .](../media/m365admincenterchanging.png)

Tout d’abord, assurez-vous que la nouvelle version d’aperçu du Centre d’administration est allumée dans le Centre <https://admin.microsoft.com> d’administration. Activer le basculement en côté du texte **Nouveau centre d’administration.**

   ![La nouvelle version d’aperçu du Centre d’administration est alors en cours.](../media/previewon.png)

Si vous ne voyez pas encore la **page** d’installation avec des cartes dans votre client, découvrez comment effectuer ces étapes dans le Centre de sécurité & conformité. Voir [Configurer Coffre pièces jointes](#set-up-safe-attachments-in-the-security--compliance-center) dans le Centre de sécurité & conformité et Configurer des liens Coffre dans le Centre de sécurité & [conformité.](#set-up-safe-links-in-the-security--compliance-center)

1. In the left nav, choose **Setup**.
2. Dans la page **Installation,** choisissez **Afficher sur** la carte Augmenter la protection contre **les menaces avancées.**

   ![Choisissez Afficher sur l’augmentation de la protection contre les menaces avancées.](../media/startatp.png)

3. On the **Increase protection from advanced threats** page, choose Get **started**.
4. Dans le volet qui s’ouvre, cochez les cases en regard des liens et des pièces **jointes** dans le courrier électronique, Analysez les fichiers dans **SharePoint, OneDrive** et Teams et analysez les liens dans les applications Office de bureau et **Office Online** sous Analyser les éléments pour le contenu malveillant. 

   Sous **Liens et pièces jointes dans le courrier électronique,** tapez Tous les utilisateurs ou les utilisateurs spécifiques dont vous souhaitez scanner le courrier électronique.

   ![Cochez toutes les cases dans Renforcer la protection contre les menaces avancées.](../media/setatp.png)

5. Choisissez **Créer des stratégies** pour activer Coffre pièces jointes et Coffre liens.

### <a name="set-up-safe-attachments-in-the-security--compliance-center"></a>Configurer des Coffre jointes dans le Centre de conformité & sécurité

Les personnes envoient, reçoivent et partagent régulièrement des pièces jointes, telles que des documents, des présentations, des feuilles de calcul, etc. Il n’est pas toujours facile de savoir si une pièce jointe est sûre ou malveillante simplement en regardant un message électronique. Microsoft Defender pour Office 365 inclut Coffre protection contre les pièces jointes, mais cette protection n’est pas désactivée par défaut. Nous vous recommandons de créer une règle pour commencer à utiliser cette protection. Cette protection s’étend aux fichiers SharePoint, OneDrive et Microsoft Teams.

Pour créer une stratégie Coffre pièces jointes, regardez cette [courte](https://support.office.com/article/e7e68934-23dc-4b9c-b714-e82e27a8f8a5)vidéo ou suivez les étapes suivantes :

1. Go to <https://protection.office.com> and sign in with your admin account.

2. Dans le Centre de sécurité & conformité, dans le volet de navigation de gauche, sous Gestion des menaces, choisissez **Stratégie**.

3. Dans la page Stratégie, choisissez **Coffre pièces jointes.**

4. Sur la page Coffre pièces jointes, appliquez cette protection à grande étendue en selecting the **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams** check box.

5. Sélectionnez **+** pour créer une stratégie.

6. Appliquez les paramètres du tableau suivant.

7. Après avoir passé en revue vos paramètres, **sélectionnez Créer cette stratégie ou** **Enregistrer,** le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Bloquer les messages électroniques actuels et futurs avec les programmes malveillants détectés.|
|Description|Bloquer les messages électroniques et pièces jointes actuels et futurs avec les programmes malveillants détectés.|
|Enregistrer les pièces jointes d’une réponse anti-programme malveillant inconnue|Select **Block - Block the current and future emails and attachments with detected malware**.|
|Rediriger la pièce jointe lors de la détection|Activer la redirection (sélectionnez cette case) <br/> Entrez le compte d’administrateur ou une boîte aux lettres configurée pour la mise en quarantaine. <br/> Appliquez la sélection ci-dessus si l’analyse des programmes malveillants pour les pièces jointes arrive à son moment ou si une erreur se produit (sélectionnez cette zone).|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|

Pour plus d’informations, voir [Configurer des stratégies anti-hameçonnage dans Defender pour Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

### <a name="set-up-safe-links-in-the-security--compliance-center"></a>Configurer des liens Coffre dans le Centre de sécurité & conformité

Les pirates informatiques masquent parfois des sites web malveillants dans des liens dans des e-mails ou d’autres fichiers. Coffre Les liens, qui font partie de Microsoft Defender pour Office 365, peuvent aider à protéger votre organisation en fournissant la vérification au moment du clic des adresses web (URL) dans les messages électroniques et les documents Office documents. La protection est définie par le biais Coffre de liens.

Nous vous recommandons d’y faire les choses suivantes :

- Modifiez la stratégie par défaut pour renforcer la protection.

- Ajoutez une nouvelle stratégie destinée à tous les destinataires de votre domaine.

Pour configurer des Coffre, regardez cette courte vidéo de [formation](https://support.office.com/article/61492713-53c2-47da-a6e7-fa97479e97fa)ou suivez les étapes suivantes :

1. Go to <https://protection.office.com> and sign in with your admin account.

2. Dans le Centre de sécurité & conformité, dans le volet de navigation de gauche, sous Gestion des menaces, choisissez **Stratégie**.

3. Dans la page Stratégie, choisissez **Coffre liens.**

Pour modifier la stratégie par défaut :

1. Dans la page Coffre liens, sous Stratégies qui s’appliquent à l’ensemble de **l’organisation,** sélectionnez la **stratégie par** défaut.

2. Sous **Paramètres qui s’appliquent au** contenu à l’exception de la messagerie, sélectionnez **Applications Microsoft 365 pour les grandes entreprises, Office pour iOS et Android**.

3. Cliquez sur **Save (Enregistrer)**.

Pour créer une stratégie destinée à tous les destinataires de votre domaine :

1. Dans la page Coffre liens, sous **Stratégies** qui s’appliquent à l’ensemble de l’organisation, cliquez **+** pour créer une stratégie.

2. Appliquez les paramètres répertoriés dans le tableau suivant.

3. Cliquez sur **Save (Enregistrer)**.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Coffre de liens pour tous les destinataires du domaine|
|Sélectionnez l’action pour les URL potentiellement malveillantes inconnues dans les messages|Sélectionnez Sur : les URL seront réécrites et vérifiées par rapport à une liste de liens malveillants connus lorsque l’utilisateur **clique sur le lien.**|
|Utiliser Coffre pièces jointes pour analyser le contenu téléchargeable|Sélectionnez cette case.|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|

Pour plus d’informations, [voir Coffre liens dans Defender pour Office 365](../security/office-365-security/safe-links.md).

## <a name="turn-on-the-unified-audit-log"></a>Activer le journal d’audit unifié

Après avoir activer la recherche dans le journal d’audit dans le Centre de sécurité & conformité, vous pouvez conserver l’activité de l’administrateur et d’autres utilisateurs dans le journal et le rechercher.

Le rôle Journaux d’audit doit vous être attribué dans Exchange Online pour activer ou désactiver la recherche dans le journal d’audit dans Microsoft 365 abonnement. Par défaut, ce rôle est affecté aux groupes de rôles Gestion de la conformité et Gestion de l’organisation dans la page Autorisations du Centre d Exchange de conformité. Les administrateurs globaux Microsoft 365 sont membres de ce groupe par défaut.

1. Pour activer la recherche dans le journal d’audit, allez au Centre d’administration à l’adresse et sélectionnez Sécurité sous Centres d’administration <https://admin.microsoft.com> dans le navigation gauche.  
2. Dans la page **Microsoft 365 sécurité,** sélectionnez  Plus de **ressources,** puis ouvrez sur la carte du Centre de sécurité **&** conformité Office 365.

    ![Choisissez Ouvrir sur les voitures de conformité & sécurité.](../media/gotosecandcomp.png)
3. Dans la page Sécurité et conformité, choisissez **Recherche,** puis **Recherche dans le journal d’audit.**
4. En haut de la page de **recherche du journal d’audit,** **sélectionnez Activer l’audit.**

Une fois la fonctionnalité désactivée, vous pouvez rechercher des fichiers, des dossiers et de nombreuses activités. Pour plus d’informations, [consultez le journal d’audit.](../compliance/search-the-audit-log-in-security-and-compliance.md)

## <a name="tune-up-anonymous-sharing-settings-for-sharepoint-and-onedrive-files-and-folders"></a>Régler les paramètres de partage anonyme pour SharePoint et OneDrive fichiers et dossiers

(modifiez l’expiration du lien anonyme par défaut à 14 jours, modifiez le type de partage par défaut en « Personnes spécifiques ») Pour modifier les paramètres de partage pour OneDrive et SharePoint :

1. Go to the admin center at <https://admin.microsoft.com> and then choose **SharePoint** under **Admin centers** in the left nav.
2. Dans le centre SharePoint’administration, allez à **Partage de** \> **stratégies.**
3. Dans la **page** Partage, sous Liens de fichiers et de dossiers, sélectionnez Des personnes **spécifiques,** et sous Paramètres avancés pour les liens « Tout le monde », sélectionnez Ces liens doivent **expirer** dans ce nombre de jours, puis tapez 14 (ou un autre nombre de jours pour limiter la durée de vie du lien). 

   ![Choisissez des personnes spécifiques et définissez l’expiration du lien sur 14 jours.](../media/anyonelinks.png)

## <a name="activity-alerts"></a>Alertes d’activité

Vous pouvez utiliser les alertes d’activité pour suivre les activités des administrateurs et des utilisateurs et détecter les incidents de protection contre la perte de données et les programmes malveillants au sein de votre organisation. Votre abonnement inclut un ensemble de stratégies par défaut, mais vous pouvez également en créer des personnalisées. Pour plus d’informations, voir [stratégies d’alerte.](../compliance/alert-policies.md) Par exemple, si vous stockez un fichier important dans SharePoint que personne ne doit partager en externe, vous pouvez créer une notification qui vous avertit si quelqu’un le partage.

La figure suivante illustre les stratégies par défaut incluses dans Microsoft 365.

![Stratégies d’alerte par défaut incluses dans Microsoft 365](../media/alertpolicies.png)

## <a name="disable-or-manage-calendar-sharing"></a>Désactiver ou gérer le partage de calendrier

Vous pouvez empêcher les membres de votre organisation de partager leurs calendriers, ou vous pouvez également gérer ce qu’ils peuvent partager. Par exemple, vous pouvez limiter le partage aux heures de libre/occupé uniquement.

1. Go to the admin center at <https://admin.microsoft.com> and choose **Paramètres** \> **Org Paramètres**.
2. Dans la page  **Services,** choisissez Calendrier et choisissez si les membres de votre organisation peuvent partager leurs calendriers avec des personnes extérieures qui ont des Office 365 ou des Exchange, ou avec n’importe qui.

   Si vous choisissez l’option partager avec tout le monde, vous pouvez également décider de partager uniquement les informations de libre/occupé.

3. Sélectionnez **Enregistrer les** modifications en bas de la page.

   La figure suivante montre le partage de calendrier non autorisé.

   ![Capture d’écran montrant que le partage de calendrier externe n’est pas autorisé.](../media/nocalendarsharing.png)

   La figure suivante illustre les paramètres lorsque le partage de calendrier est autorisé avec un lien de messagerie avec uniquement des informations de libre/occupé.

   ![Capture d’écran du partage de la période de libre/occupé du calendrier avec tout le monde.](../media/sharefreebusy.png)

Si vos utilisateurs sont autorisés à partager leurs calendriers, consultez ces [instructions](https://support.office.com/article/7ecef8ae-139c-40d9-bae2-a23977ee58d5) pour savoir comment partager à partir de Outlook sur le web.
