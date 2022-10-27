---
title: Augmenter la protection contre les menaces pour Microsoft 365 pour les PME
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- highpri
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- VSBFY23
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
description: Configurez Microsoft Defender pour Office 365 et protégez les données sensibles contre le hameçonnage, les programmes malveillants et d’autres menaces.
ms.openlocfilehash: 6d604cec1925259ba1378153afe7feeb299b1628
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68731104"
---
# <a name="increase-threat-protection-for-microsoft-365-for-business"></a>Augmenter la protection contre les menaces pour Microsoft 365 pour les PME

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

Cet article vous aide à renforcer la protection de votre abonnement Microsoft 365 pour vous protéger contre l’hameçonnage, les programmes malveillants et d’autres menaces. Ces recommandations conviennent aux organisations qui ont un besoin accru de sécurité, comme les cabinets d’avocats et les cliniques de soins de santé.

Avant de commencer, vérifiez votre niveau de sécurisation Office 365. Office 365 degré de sécurité analyse la sécurité de votre organisation en fonction de vos activités régulières et de vos paramètres de sécurité, et attribue un score. Commencez par prendre note de votre score actuel. Pour augmenter votre score, effectuez les actions recommandées dans cet article. L’objectif n’est pas d’atteindre le score maximal, mais d’être conscient des opportunités de protection de votre environnement qui n’affectent pas négativement la productivité de vos utilisateurs.

Pour plus d’informations, consultez [Microsoft Secure Score](../../security/defender/microsoft-secure-score.md).

## <a name="watch-raise-the-level-of-protection-against-malware-in-mail"></a>Regarder : Augmenter le niveau de protection contre les programmes malveillants dans la messagerie

Votre environnement Office 365 ou Microsoft 365 inclut une protection contre les programmes malveillants. Vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OA7Z?autoplay=false]

1. Dans la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, choisissez **Afficher plus**, **Administration centres**, puis **Sécurité**.

1. Accédez à **Email & stratégies de collaboration** \> **& règles** \> **Stratégies de menace**.

1. Dans les stratégies disponibles, choisissez **Anti-malware**.

Pour renforcer la protection contre les programmes malveillants dans les e-mails :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, accédez à **Email & collaboration** \> **Stratégies & règles** \> **Stratégies contre les** \> **menaces Anti-programme malveillant** dans la section **Stratégies**.

1. Dans la page **Anti-malware**, double-cliquez sur **Default (Default) (Par défaut).** Un menu volant s’affiche. 

1. Sélectionnez **Modifier les paramètres de protection** en bas du menu volant. 

1. sous **Paramètres de protection**, cochez la case en regard de **Activer le filtre des pièces jointes courantes**. Les types de fichiers bloqués sont répertoriés directement sous ce contrôle. Veillez à ajouter ces types de fichiers :

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   Pour ajouter ou supprimer des types de fichiers, sélectionnez **Personnaliser les types de fichiers** à la fin de la liste.

1. Sélectionnez **Enregistrer.**

Pour plus d’informations, consultez [Protection contre les programmes malveillants dans EOP](../../security/office-365-security/anti-malware-protection.md).

## <a name="watch-protect-against-ransomware"></a>Regarder : Se protéger contre les rançongiciels

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198018).

Ransomware restreint l’accès aux données en chiffrant les fichiers ou en verrouillant les écrans de l’ordinateur. Il tente ensuite d’extorquer de l’argent aux victimes en demandant une « rançon », généralement sous la forme de crypto-monnaies comme Bitcoin, en échange de l’accès aux données.

Pour vous protéger contre les rançongiciels, créez une ou plusieurs règles de flux de courrier pour bloquer les extensions de fichier couramment utilisées pour les rançongiciels. (Vous avez ajouté ces règles à l’étape [Surveiller : Augmenter le niveau de protection contre les programmes malveillants dans la messagerie](#watch-raise-the-level-of-protection-against-malware-in-mail) .) Vous pouvez également avertir les utilisateurs qui reçoivent ces pièces jointes par e-mail.

En plus des fichiers que vous avez bloqués à l’étape précédente, il est recommandé de créer une règle pour avertir les utilisateurs avant d’ouvrir des pièces jointes Office qui incluent des macros. Les rançongiciels peuvent être masqués à l’intérieur des macros, donc avertir les utilisateurs de ne pas ouvrir ces fichiers à partir de personnes qu’ils ne connaissent pas.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrWGt?autoplay=false]

1. Dans le Centre d’administration, [https://admin.microsoft.com](https://admin.microsoft.com)choisissez **Exchange** sous **Administration centres**.

1. Dans le menu de gauche, choisissez **Flux de courrier**.
 
1. Sous l’onglet Règles, choisissez la flèche en regard du symbole plus (+), puis choisissez **Créer une règle**.

1. Dans la page **nouvelle règle** , entrez un nom pour votre règle, faites défiler vers le bas, puis choisissez **Plus d’options**.

Pour créer une règle de transport de courrier :

1. Accédez au Centre d’administration à l’adresse <https://admin.microsoft.com>, puis choisissez **Administration centres** \> **Exchange**.

2. Dans la catégorie **flux de messagerie** , sélectionnez **règles**.

3. Sélectionnez **+**, puis **Créer une règle**.

4. Sélectionnez **Plus d’options** en bas de la boîte de dialogue pour afficher l’ensemble complet des options.

5. Appliquez les paramètres du tableau suivant pour la règle. Utilisez les valeurs par défaut pour le reste des paramètres, sauf si vous souhaitez les modifier.

6. Sélectionnez **Enregistrer**.

|Setting|Avertir les utilisateurs avant d’ouvrir des pièces jointes de fichiers Office|
|---|---|
|Nom|Règle anti-ransomware : avertir les utilisateurs|
|Appliquez cette règle si . . .|N’importe quelle pièce jointe . . . l’extension de fichier correspond à . . .|
|Spécifier des mots ou des expressions|Ajoutez ces types de fichiers :  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm|
|Effectuez les opérations suivantes. . .|Avertir le destinataire avec un message|
|Fournir le texte du message|N’ouvrez pas ces types de fichiers à partir de personnes que vous ne connaissez pas, car ils peuvent contenir des macros avec du code malveillant.|

Pour plus d’informations, consultez l’article suivant :

- [Ransomware : comment réduire les risques](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Restaurer votre OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="stop-auto-forwarding-for-email"></a>Arrêter le transfert automatique pour les e-mails

Les pirates informatiques qui accèdent à la boîte aux lettres d’un utilisateur peuvent voler du courrier en définissant la boîte aux lettres pour transférer automatiquement le courrier électronique. Cela peut se produire même sans que l’utilisateur en soit conscient. Pour éviter cela, configurez une règle de flux de messagerie.

Pour créer une règle de transport de courrier, procédez comme suit :

1. Dans la Centre d'administration Microsoft 365, sélectionnez **Administration centres** \> **Exchange**.

2. Dans la catégorie **flux de messagerie** , sélectionnez **règles**.

3. Sélectionnez **+**, puis **Créer une règle**.

4. Pour afficher toutes les options, sélectionnez **Plus d’options** en bas de la boîte de dialogue.

5. Appliquez les paramètres du tableau suivant. Utilisez les valeurs par défaut pour le reste des paramètres, sauf si vous souhaitez les modifier.

6. Sélectionnez **Enregistrer**.

|Setting|Avertir les utilisateurs avant d’ouvrir des pièces jointes de fichiers Office|
|---|---|
|Nom|Empêcher le transfert automatique d’e-mails vers des domaines externes|
|Appliquez cette règle si ...|Expéditeur . . . est externe/interne. . . Au sein de l’organisation|
|Ajouter une condition|Propriétés du message . . . incluez le type de message . . . Transfert automatique|
|Procédez comme suit ...|Bloquez le message . . . rejeter le message et inclure une explication.|
|Fournir le texte du message|Le transfert automatique des e-mails en dehors de cette organisation est empêché pour des raisons de sécurité.|

## <a name="watch-protect-your-email-from-phishing-attacks"></a>Regarder : Protéger votre courrier contre les attaques par hameçonnage

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198014).

Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Office 365 ou Microsoft 365, vous pouvez configurer une protection anti-hameçonnage ciblée. La protection anti-hameçonnage, qui fait partie de Microsoft Defender pour Office 365, peut aider à protéger votre organisation contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillante et d’autres attaques par hameçonnage. Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin de le faire.

Nous vous recommandons de commencer à utiliser cette protection en créant une stratégie pour protéger vos utilisateurs les plus importants et votre domaine personnalisé.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvt9r?autoplay=false]

1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a>.

2. Accédez à **Email & collaboration** \> **Stratégies & règles** \> **Stratégies** \> de menace **Anti-hameçonnage** dans la section **Stratégies**.

3. Dans la page **Anti-hameçonnage** , sélectionnez **+ Créer**. Un Assistant démarre qui vous guide tout au long de la définition de votre stratégie anti-hameçonnage.

4. Spécifiez le nom, la description et les paramètres de votre stratégie, comme recommandé dans le tableau suivant. Pour plus [d’informations, consultez En savoir plus sur la stratégie anti-hameçonnage dans Microsoft Defender pour Office 365 options](../../security/office-365-security/set-up-anti-phishing-policies.md).

5. Une fois que vous avez examiné vos paramètres, choisissez **Créer cette stratégie** ou **Enregistrer**, le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Domaine et personnel de campagne le plus précieux|
|Description|Assurez-vous que le personnel le plus important et notre domaine ne sont pas usurpés d’identité.|
|Ajouter des utilisateurs à protéger|Sélectionnez **+ Ajouter une condition, Le destinataire est**. Tapez les noms d’utilisateur ou entrez l’adresse e-mail du candidat, du responsable de campagne et d’autres membres importants du personnel. Vous pouvez ajouter jusqu’à 20 adresses internes et externes que vous souhaitez protéger contre l’emprunt d’identité.|
|Ajouter des domaines à protéger|Sélectionnez **+ Ajouter une condition, Le domaine du destinataire est**. Entrez le domaine personnalisé associé à votre abonnement Microsoft 365, si vous en avez défini un. Vous pouvez entrer plusieurs domaines.|
|Choisir des actions|Si un e-mail est envoyé par un utilisateur usurpé l’identité : choisissez **Rediriger le message vers une autre adresse e-mail**, puis tapez l’adresse e-mail de l’administrateur de la sécurité ; par exemple, *Alice<span><span>@contoso.com*. Si le courrier électronique est envoyé par un domaine dont l’identité a été empruntée : sélectionnez **Mettre le message en quarantaine**.|
|Veille des boîtes aux lettres|Par défaut, la veille des boîtes aux lettres est activée lorsque vous créez une stratégie anti-hameçonnage. Laissez ce paramètre **activé** pour obtenir de meilleurs résultats.|
|Ajouter des expéditeurs et domaines de confiance|Ici, vous pouvez ajouter votre propre domaine ou tout autre domaine approuvé.|
|Appliqué à|Sélectionnez **Le domaine du destinataire est**. Sous **Un de ces éléments**, sélectionnez **Choisir**. Sélectionnez **+ Ajouter**. Cochez la case en regard du nom du domaine, par exemple *contoso.<span><span> com*, dans la liste, puis sélectionnez **Ajouter**. Sélectionnez **Terminé**.|

## <a name="watch-protect-against-malicious-attachments-and-files-with-safe-attachments"></a>Regarder : Se protéger contre les pièces jointes et les fichiers malveillants avec des pièces jointes fiables

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198019).

Les personnes envoient, reçoivent et partagent régulièrement des pièces jointes, telles que des documents, des présentations, des feuilles de calcul, etc. Il n’est pas toujours facile de savoir si une pièce jointe est sécurisée ou malveillante simplement en examinant un message électronique. Microsoft Defender pour Office 365, anciennement Appelé Microsoft 365 ATP ou Advanced Threat Protection, inclut la protection des pièces jointes sécurisées, mais cette protection n’est pas activée par défaut. Nous vous recommandons de créer une règle pour commencer à utiliser cette protection. Cette protection s’étend aux fichiers dans SharePoint, OneDrive et Microsoft Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWtn3I?autoplay=false]

1. Accédez au [Centre d’administration](https://admin.microsoft.com), puis sélectionnez **Configuration**.
1. Faites défiler vers le bas jusqu’à **Augmenter la protection contre les menaces avancées**. Sélectionnez **Afficher**, **Gérer**, puis **Pièces jointes sécurisées ATP**.
1. Sélectionnez votre règle de pièces jointes sécurisées, puis choisissez l’icône **Modifier** .
1. Sélectionnez **paramètres**, puis vérifiez que Bloquer est sélectionné.
1. Faites défiler. Choisissez **Activer la redirection**, puis entrez votre adresse e-mail ou l’adresse de la personne à laquelle vous souhaitez examiner les pièces jointes bloquées.
1. Sélectionnez **Appliqué à**, puis sélectionnez votre nom de domaine.
1. Choisissez les domaines supplémentaires que vous possédez (tels que votre domaine onmicrosoft.com) auxquels vous souhaitez appliquer la règle. Sélectionnez **Ajouter**, puis **OK**.
1. Sélectionnez **Enregistrer**.

Votre règle de pièces jointes sécurisées ATP a été mise à jour. Maintenant que la protection est en place, vous ne pourrez plus ouvrir un fichier malveillant à partir d’Outlook, OneDrive, SharePoint ou Teams. Les fichiers affectés auront des boucliers rouges à côté d’eux. Si une personne tente d’ouvrir un fichier bloqué, elle reçoit un message d’avertissement.

Une fois votre stratégie en place depuis un certain temps, visitez la page Rapports pour voir ce qui a été analysé.

1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a> et connectez-vous avec votre compte administrateur.

2. Accédez à **Email & collaboration** \> **Stratégies & règles** \> **Stratégies contre les** \> **menaces Anti-programme malveillant** dans la section **Stratégies**.

3. Sélectionnez **+ Créer** pour créer une stratégie.

4. Appliquez les paramètres du tableau suivant.

5. Après avoir examiné vos paramètres, sélectionnez **Créer cette stratégie** ou **Enregistrer**, le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Bloquer les e-mails actuels et futurs avec des programmes malveillants détectés.|
|Description|Bloquez les e-mails et pièces jointes actuels et futurs avec des programmes malveillants détectés.|
|Enregistrer les pièces jointes réponse aux programmes malveillants inconnus|Sélectionnez **Bloquer : bloquer les e-mails et pièces jointes actuels et futurs avec des programmes malveillants détectés**.|
|Rediriger la pièce jointe lors de la détection|Activer la redirection (cochez cette case) Entrez le compte d’administrateur ou une configuration de boîte aux lettres pour la mise en quarantaine.          Appliquez la sélection ci-dessus si l’analyse des pièces jointes par un programme malveillant expire ou si une erreur se produit (cochez cette case).|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|

Pour plus d’informations, consultez [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](../../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="watch-protect-against-phishing-attacks-with-safe-links"></a>Regarder : Se protéger contre les attaques par hameçonnage avec des liens fiables

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198201).

Les pirates informatiques masquent parfois des sites web malveillants dans des liens dans des e-mails ou d’autres fichiers. Les liens fiables, qui font partie de Microsoft Defender pour Office 365, peuvent aider à protéger votre organisation en fournissant une vérification au moment du clic des adresses web (URL) dans les messages électroniques et les documents Office. La protection est définie par le biais de stratégies de liens fiables.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvdwy?autoplay=false]

Microsoft Defender pour Office 365, anciennement Microsoft 365 ATP, ou Advanced Threat Protection, permet de protéger votre entreprise contre les sites malveillants lorsque des personnes cliquent sur des liens dans des applications Office.

1. Accédez au [Centre d’administration](https://admin.microsoft.com), puis sélectionnez **Configuration**.

1. Faites défiler vers le bas jusqu’à **Augmenter la protection contre les menaces avancées**. Sélectionnez **Gérer**, puis **Liens fiables**.

1. Sélectionnez **Paramètres globaux** et dans **Bloquer les URL suivantes**, entrez l’URL que vous souhaitez bloquer.

Nous vous recommandons d’effectuer les opérations suivantes :

- Modifiez la stratégie par défaut pour augmenter la protection.

- Ajoutez une nouvelle stratégie destinée à tous les destinataires de votre domaine.

Pour configurer des liens fiables, procédez comme suit :

1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a> et connectez-vous avec votre compte administrateur.

2. o pour **Email &** stratégies de collaboration \> **& règles** \> **Stratégies contre les menaces** \> **Anti-programme malveillant** dans la section **Stratégies**.

3. Sélectionnez **+ Créer** pour créer une stratégie ou modifiez la stratégie par défaut.

Pour modifier la stratégie par défaut :

1. Double-cliquez sur la **stratégie par défaut** . Un menu volant s’affiche. 

2. Sélectionnez **Modifier les paramètres de protection** en bas du menu volant.

3. Après avoir modifié la stratégie par défaut, sélectionnez **Enregistrer**.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Stratégie de liens fiables pour tous les destinataires du domaine|
|Sélectionner l’action pour les URL potentiellement malveillantes inconnues dans les messages|Sélectionnez **Activé : les URL seront réécrites et vérifiées par rapport à une liste de liens malveillants connus lorsque l’utilisateur clique sur le lien**.|
|Utilisez les pièces jointes approuvées pour analyser le contenu téléchargeable|Cochez cette case.|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|

Pour plus d’informations, consultez [Liens fiables](../../security/office-365-security/safe-links.md).

## <a name="go-to-intune-admin-center"></a>Accédez au Centre d’administration Intune

1. Connectez-vous au [portail Azure](https://portal.azure.com/).

2. Sélectionnez **Tous les services** et tapez *Intune* dans la **zone de recherche**.

3. Une fois les résultats affichés, sélectionnez le début en regard **de Microsoft Intune** pour en faire un favori et facile à trouver ultérieurement.

En plus du centre d’administration, vous pouvez utiliser Intune pour inscrire et gérer les appareils de votre organisation. Pour plus d’informations, consultez [Fonctionnalités par méthode d’inscription pour les appareils Windows](/intune/enrollment/enrollment-method-capab) et [Options d’inscription pour les appareils gérés par Intune](/intune/enrollment-options).
