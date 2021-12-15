---
title: Renforcer la protection contre les menaces Microsoft 365 entreprise
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
description: Configurer Microsoft Defender pour Office 365 et protéger les données sensibles contre le hameçonnage, les programmes malveillants et d’autres menaces.
ms.openlocfilehash: 20e939b0717e73e3148b3bbaf93e3190414609d4
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61520991"
---
# <a name="increase-threat-protection"></a>Renforcer la protection contre les menaces

Cet article vous aide à renforcer la protection de votre abonnement Microsoft 365 protection contre le hameçonnage, les programmes malveillants et d’autres menaces. Ces recommandations sont appropriées pour les organisations ayant un besoin accru de sécurité, comme les cabinets d’avocats et les organismes de santé.

Avant de commencer, vérifiez votre score Office 365 sécurisé. Office 365 Secure Score analyse la sécurité de votre organisation en fonction de vos activités et paramètres de sécurité habituels, et affecte un score. Commencez par prendre note de votre score actuel. Pour augmenter votre score, complétez les actions recommandées dans cet article. L’objectif n’est pas d’atteindre le score maximal, mais de prendre en compte les opportunités de protection de votre environnement qui n’affectent pas la productivité de vos utilisateurs.

Pour plus d’informations, voir [Le Score de sécurité Microsoft.](../../security/defender/microsoft-secure-score.md)

## <a name="raise-the-level-of-protection-against-malware-in-mail"></a>Augmenter le niveau de protection contre les programmes malveillants dans le courrier électronique

Votre environnement Office 365 ou Microsoft 365 inclut une protection contre les programmes malveillants. Vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OA7Z?autoplay=false]

1. Dans la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365,</a>choisissez **Afficher plus,** **Centres** d’administration, puis Sécurité **& Conformité**.
1. Choisissez **Gestion des menaces,** puis **Stratégie**.
1. Dans les stratégies disponibles, choisissez **Anti-programme malveillant.**

Pour renforcer la protection contre les programmes malveillants dans la messagerie électronique :

1. Go to [https://protection.office.com](https://protection.office.com) and sign in with your admin account credentials.

2. Dans le Centre de conformité de sécurité, dans le volet de navigation de gauche, sous Gestion des menaces, choisissez &amp; **Stratégie**  \> **anti-programme malveillant.**

3. Double-cliquez sur la stratégie par défaut pour modifier cette stratégie à l’échelle de l’entreprise.

4. Sélectionnez **Paramètres**.

5. Sous **Filtre Types de pièces jointes courants,** **sélectionnez Sur**. Les types de fichiers bloqués sont répertoriés dans la fenêtre directement sous ce contrôle. Veillez à ajouter les types de fichiers ci-après :

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   Si nécessaire, vous pouvez ajouter ou supprimer des types de fichiers ultérieurement.

6. Sélectionnez **Enregistrer.**

Pour plus d’informations, voir [Protection contre les programmes malveillants dans EOP.](../../security/office-365-security/anti-malware-protection.md)

## <a name="protect-against-ransomware"></a>Se protéger contre les rançongiciels

Un ransomware limite l’accès aux données en chiffrant des fichiers ou en verrouiller les écrans d’ordinateur. Il tente ensuite d’extorquer de l’argent à des personnes victime en demandant « rançon », généralement sous la forme de cryptomonnaies telles que Cryptograph, en échange de l’accès aux données.

Pour vous protéger contre les ransomware, créez une ou plusieurs règles de flux de messagerie pour bloquer les extensions de fichier couramment utilisées pour les ransomware. (Vous avez ajouté ces règles dans l’augmentation du niveau de protection contre [les programmes malveillants à l’étape de messagerie.)](#raise-the-level-of-protection-against-malware-in-mail) Vous pouvez également avertir les utilisateurs qui reçoivent ces pièces jointes par courrier électronique.

Outre les fichiers que vous avez bloqués à l’étape précédente, il est bon de créer une règle pour avertir les utilisateurs avant d’ouvrir des pièces jointes de fichier Office qui incluent des macros. Les ransomware peuvent être masqués dans les macros, donc avertissez les utilisateurs de ne pas ouvrir ces fichiers à partir de personnes qu’ils ne connaissent pas.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrWGt?autoplay=false]

1. Dans le Centre d’administration, [https://admin.microsoft.com](https://admin.microsoft.com) **sélectionnez Exchange** sous **Centres d’administration.**
1. Dans le menu de gauche, choisissez **flux de messagerie.**
1. Sous l’onglet Règles, choisissez la flèche en haut du symbole plus (+), puis choisissez Créer **une règle.**
1. Dans la **page nouvelle règle,** entrez un nom pour votre règle, faites défiler vers le bas, puis choisissez **Plus d’options.**

Pour créer une règle de transport de messagerie :

1. Go to the admin center at <https://admin.microsoft.com> , and choose Admin **centers** \> **Exchange**.

2. Dans la catégorie **de flux de messagerie,** sélectionnez **des règles.**

3. **+** Sélectionnez, puis **sélectionnez Créer une règle.**

4. Sélectionnez **plus d’options** en bas de la boîte de dialogue pour voir l’ensemble complet des options.

5. Appliquez les paramètres du tableau suivant pour la règle. Utilisez les valeurs par défaut pour le reste des paramètres, sauf si vous souhaitez les modifier.

6. Cliquez sur **Enregistrer**.

|Setting|Avertir les utilisateurs avant d’ouvrir les pièces jointes Office fichiers|
|---|---|
|Nom|Règle anti-ransomware : avertir les utilisateurs|
|Appliquez cette règle si . . .|N’importe quelle pièce jointe . . . l’extension de fichier correspond à . . .|
|Spécifier des mots ou des expressions|Ajoutez les types de fichiers ci-après :  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm|
|Faites les choses suivantes . . .|Avertir le destinataire avec un message|
|Fournir le texte du message|N’ouvrez pas ces types de fichiers à partir de personnes que vous ne connaissez pas, car elles peuvent contenir des macros contenant du code malveillant.|

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Ransomware : comment réduire les risques](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Restaurer votre OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15.aspx)

## <a name="stop-auto-forwarding-for-email"></a>Arrêter le forwarding automatique pour le courrier électronique

Les pirates informatiques qui accèdent à la boîte aux lettres d’un utilisateur peuvent dérober des messages électroniques en les insérez pour qu’ils les envoient automatiquement. Cela peut se produire même sans la sensibilisation de l’utilisateur. Pour éviter que cela ne se produise, configurez une règle de flux de messagerie.

Pour créer une règle de transport de messagerie, suivez les étapes suivantes :

1. Dans la Centre d'administration Microsoft 365, sélectionnez **Centres d’administration** \> **Exchange**.

2. Dans la catégorie **de flux de messagerie,** sélectionnez **des règles.**

3. **+** Sélectionnez, puis **sélectionnez Créer une règle.**

4. Pour voir toutes les options, sélectionnez **Plus d’options** en bas de la boîte de dialogue.

5. Appliquez les paramètres du tableau suivant. Utilisez les valeurs par défaut pour le reste des paramètres, sauf si vous souhaitez les modifier.

6. Cliquez sur **Enregistrer**.

|Setting|Avertir les utilisateurs avant d’ouvrir les pièces jointes Office fichiers|
|---|---|
|Nom|Empêcher le forwarding automatique du courrier électronique vers des domaines externes|
|Appliquez cette règle si...|L’expéditeur . . . est externe/interne . . . À l’intérieur de l’organisation|
|Ajouter une condition|Propriétés du message . . . inclure le type de message . . . Auto-forward|
|Faites les choses suivantes ...|Bloquer le message . . . rejeter le message et inclure une explication.|
|Fournir le texte du message|Le courrier électronique à l’extérieur de cette organisation est interdit pour des raisons de sécurité.|

## <a name="protect-your-email-from-phishing-attacks"></a>Protéger votre courrier électronique contre les attaques par hameçonnage

Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Office 365 ou Microsoft 365, vous pouvez configurer une protection anti-hameçonnage ciblée. La protection anti-hameçonnage, qui fait partie de Microsoft Defender pour Office 365, peut aider à protéger votre organisation contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillant et d’autres attaques par hameçonnage. Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin de le faire.

Nous vous recommandons de commencer avec cette protection en créant une stratégie pour protéger vos utilisateurs les plus importants et votre domaine personnalisé.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvt9r?autoplay=false]

1. Accédez à [https://protection.office.com](https://protection.office.com).

2. In the Security &amp; Compliance Center, in the left navigation pane, under **Threat management**, choose **Policy**.

3. Dans la page **Stratégie,** choisissez **Anti-hameçonnage.**

4. Dans la page **Anti-hameçonnage,** **sélectionnez + Créer.** Un Assistant vous lance pour définir votre stratégie anti-hameçonnage.

5. Spécifiez le nom, la description et les paramètres de votre stratégie comme recommandé dans le tableau suivant. Pour plus d’informations, voir La stratégie [anti-hameçonnage](../../security/office-365-security/set-up-anti-phishing-policies.md)dans Microsoft Defender pour Office 365 options.

6. Une fois que vous avez examiné vos paramètres, choisissez **Créer cette** stratégie ou **Enregistrer,** le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Domaine et personnel de campagne le plus précieux|
|Description|Assurez-vous que le personnel le plus important et notre domaine ne font pas l’objet d’un emprunt d’identité.|
|Ajouter des utilisateurs à protéger|Sélectionnez **+ Ajoutez une condition, le destinataire est**. Tapez les noms des utilisateurs ou entrez l’adresse e-mail du candidat, du responsable de campagne et d’autres membres importants du personnel. Vous pouvez ajouter jusqu’à 20 adresses internes et externes que vous souhaitez protéger contre l’emprunt d’identité.|
|Ajouter des domaines à protéger|Sélectionnez **+ Ajoutez une condition, le domaine du destinataire est**. Entrez le domaine personnalisé associé à votre abonnement Microsoft 365, si vous en avez défini un. Vous pouvez entrer plusieurs domaines.|
|Choisir des actions|Si un message électronique est envoyé par un utilisateur dont l’identité est emprunt d’identité : sélectionnez **Rediriger le message** vers une autre adresse de messagerie, puis tapez l’adresse e-mail de l’administrateur de sécurité . par exemple, *Alice <span> <span> @contoso.com*. Si le courrier électronique est envoyé par un domaine dont l’identité a été empruntée : sélectionnez **Mettre le message en quarantaine**.|
|Veille des boîtes aux lettres|Par défaut, la veille des boîtes aux lettres est activée lorsque vous créez une stratégie anti-hameçonnage. Laissez ce paramètre **activé** pour obtenir de meilleurs résultats.|
|Ajouter des expéditeurs et domaines de confiance|Ici, vous pouvez ajouter votre propre domaine ou tout autre domaine approuvé.|
|Appliqué à|Sélectionnez **Le domaine du destinataire est**. Sous **Un de ces éléments**, sélectionnez **Choisir**. Sélectionnez **+ Ajouter**. Cochez la case en regard du nom du domaine, par *exemple, contoso. <span> <span> com*, dans la liste, puis sélectionnez **Ajouter**. Sélectionnez **Terminé**.|

## <a name="watch-protect-against-malicious-attachments-and-files-with-safe-attachments"></a>Watch: Protect against malicious attachments and files with Coffre Attachments

Les personnes envoient, reçoivent et partagent régulièrement des pièces jointes, telles que des documents, des présentations, des feuilles de calcul, etc. Il n’est pas toujours facile de savoir si une pièce jointe est sûre ou malveillante en regardant simplement un message électronique. Microsoft Defender pour Office 365, anciennement appelé protection avancée contre les menaces Microsoft 365, inclut la protection contre les Coffre pièces jointes, mais cette protection n’est pas désactivée par défaut. Nous vous recommandons de créer une règle pour commencer à utiliser cette protection. Cette protection s’étend aux fichiers SharePoint, OneDrive et Microsoft Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWtn3I?autoplay=false]

1. Go to the [admin center](https://admin.microsoft.com), and select **Setup**.
1. Faites défiler vers le bas **pour renforcer la protection contre les menaces avancées.** Sélectionnez **Afficher,** **Gérer,** puis **Pièces jointes sécurisées ATP.**
1. Sélectionnez votre règle de pièces jointes sécurisées, puis sélectionnez **l’icône** Modifier.
1. Sélectionnez **les paramètres,** puis vérifiez que Bloquer est sélectionné.
1. Faites défiler vers le bas. Sélectionnez **Activer la redirection,** puis entrez votre adresse e-mail ou l’adresse de la personne que vous souhaitez consulter les pièces jointes bloquées.
1. Sélectionnez **Appliqué à,** puis sélectionnez votre nom de domaine.
1. Choisissez les domaines supplémentaires que vous possédez (tels que onmicrosoft.com domaine) que vous souhaitez que la règle s’applique. Sélectionnez **Ajouter,** puis **OK**.
1. Cliquez sur **Enregistrer**.

Votre règle de pièces jointes sécurisées ATP a été mise à jour. Maintenant que la protection est en place, vous ne pourrez pas ouvrir un fichier malveillant à partir de Outlook, OneDrive, SharePoint ou Teams. Les fichiers affectés auront des boucliers rouges à côté d’eux. Si une personne tente d’ouvrir un fichier bloqué, elle reçoit un message d’avertissement.

Une fois votre stratégie en place pendant un certain temps, visitez la page Rapports pour voir ce qui a été analysé.

1. Go to [https://protection.office.com](https://protection.office.com) , and sign in with your admin account.

2. In the Security &amp; Compliance Center, in the left navigation pane, under **Threat management**, choose **Policy**.

3. Dans la page Stratégie, choisissez **Coffre pièces jointes.**

4. Sur la page Coffre pièces jointes, appliquez cette protection à grande étendue en élecntant la case à cocher Activer la protection **SharePoint, OneDrive** et Microsoft Teams protection.

5. Sélectionnez **+** pour créer une stratégie.

6. Appliquez les paramètres du tableau suivant.

7. Après avoir examiné vos paramètres, **sélectionnez Créer cette stratégie ou** **Enregistrer,** le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Bloquer les messages électroniques actuels et futurs avec les programmes malveillants détectés.|
|Description|Bloquer les messages électroniques et pièces jointes actuels et futurs avec les programmes malveillants détectés.|
|Enregistrer les pièces jointes d’une réponse anti-programme malveillant inconnue|Select **Block - Block the current and future emails and attachments with detected malware**.|
|Rediriger la pièce jointe lors de la détection|Activer la redirection (sélectionnez cette zone) Entrez le compte d’administrateur ou une boîte aux lettres configurée pour la mise en quarantaine.          Appliquez la sélection ci-dessus si l’analyse des programmes malveillants pour les pièces jointes arrive à arriver à son moment ou si une erreur se produit (sélectionnez cette zone).|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|

Pour plus d’informations, voir [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](../../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="protect-against-phishing-attacks-with-safe-links"></a>Se protéger contre les attaques par hameçonnage à l’Coffre liens

Les pirates informatiques masquent parfois des sites web malveillants dans des liens dans des e-mails ou d’autres fichiers. Coffre liens, qui font partie de Microsoft Defender pour Office 365, peuvent aider à protéger votre organisation en fournissant la vérification au moment du clic des adresses web (URL) dans les messages électroniques et les documents Office documents. La protection est définie par le biais Coffre de liens.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvdwy?autoplay=false]

Microsoft Defender pour Office 365 , anciennement appelé protection avancée contre les menaces Microsoft 365, permet de protéger votre entreprise contre les sites malveillants lorsque les utilisateurs cliquent sur des liens dans Office applications.

1. Go to the [admin center](https://admin.microsoft.com), and select **Setup**.
2. Faites défiler vers le bas **pour renforcer la protection contre les menaces avancées.** Sélectionnez **Gérer,** puis **Coffre liens.**
3. Sélectionnez **Global Paramètres** et dans Bloquer les URL **suivantes,** entrez l’URL que vous souhaitez bloquer.

Nous vous recommandons d’y faire les choses suivantes :

- Modifiez la stratégie par défaut pour renforcer la protection.

- Ajoutez une nouvelle stratégie destinée à tous les destinataires de votre domaine.

Pour configurer Coffre liens, complétez les étapes suivantes :

1. Go to [https://protection.office.com](https://protection.office.com) , and sign in with your admin account.

2. In the Security &amp; Compliance Center, in the left navigation pane, under **Threat management**, choose **Policy**.

3. Dans la page Stratégie, choisissez **Coffre liens.**

Pour modifier la stratégie par défaut :

1. Dans la page Coffre liens, sous **Stratégies** qui s’appliquent à l’ensemble de l’organisation, sélectionnez la **stratégie par** défaut.

2. Sous **Paramètres qui s’appliquent au** contenu à l’exception de la messagerie, sélectionnez **Applications Microsoft 365 pour les grandes entreprises, Office pour iOS et Android**.

3. Cliquez sur **Enregistrer**.

Pour créer une stratégie destinée à tous les destinataires de votre domaine :

1. Dans la page Coffre liens, sous **Stratégies** qui s’appliquent à l’ensemble de l’organisation, sélectionnez **+** pour créer une stratégie.

2. Appliquez les paramètres répertoriés dans le tableau suivant.

3. Cliquez sur **Enregistrer**.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Coffre de liens pour tous les destinataires du domaine|
|Sélectionner l’action pour les URL potentiellement malveillantes inconnues dans les messages|Sélectionnez Sur : les URL seront réécrites et vérifiées par rapport à une liste de liens malveillants connus lorsque l’utilisateur **clique sur le lien.**|
|Utiliser Coffre pièces jointes pour analyser le contenu téléchargeable|Sélectionnez cette case.|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|

Pour plus d’informations, [voir Coffre liens.](../../security/office-365-security/safe-links.md)

## <a name="go-to-intune-admin-center"></a>Go to Intune admin center

1. Connectez-vous au [portail Azure.](https://portal.azure.com/)

2. Sélectionnez **Tous les services** et tapez *Intune* dans la **zone de recherche.**

3. Une fois que les résultats apparaissent, sélectionnez le début en **Microsoft Intune** pour en faire un favori et facile à trouver ultérieurement.

Outre le Centre d’administration, vous pouvez utiliser Intune pour inscrire et gérer les appareils de votre organisation. Pour plus d’informations, voir [Fonctionnalités par](/intune/enrollment/enrollment-method-capab) méthode d’inscription Windows et options d’inscription pour les appareils [gérés par Intune.](/intune/enrollment-options)
