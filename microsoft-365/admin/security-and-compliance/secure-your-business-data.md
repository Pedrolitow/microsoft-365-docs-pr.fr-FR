---
title: 10 principales façons de sécuriser les Microsoft 365 pour les plans d’entreprise
f1.keywords:
- CSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: de2da300-dbb6-4725-bb12-b85a9d296e75
description: Comment protéger votre messagerie et vos données professionnelles contre les cybermenaces, y compris les ransomware, le hameçonnage et les pièces jointes malveillantes.
ms.openlocfilehash: 301aa152d462dc7fc712d4b6aa56f4a521463690
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58566915"
---
# <a name="top-10-ways-to-secure-microsoft-365-for-business-plans"></a>10 principales façons de sécuriser les Microsoft 365 pour les plans d’entreprise

Si vous êtes une petite ou moyenne entreprise utilisant l’un des plans d’entreprise de Microsoft et que votre type d’organisation est ciblé par des cybercriminels et des pirates informatiques, utilisez les instructions de cet article pour renforcer la sécurité de votre organisation. Ces conseils aident votre organisation à atteindre les objectifs décrits dans le Manuel de campagne de [cyber-sécurité de l’établissement d’état de L’État de Nouvelle-France.](https://go.microsoft.com/fwlink/p/?linkid=2015598)

Microsoft recommande d’effectuer les tâches répertoriées dans le tableau suivant qui s’appliquent à votre plan de service.

|*Number*|Tâche|Microsoft 365 Business Standard|Microsoft 365 Business Premium|
|---|---|---|---|
|1 |[Configurer l’authentification multifacteur](secure-your-business-data.md#setup)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2 |[Former vos utilisateurs](secure-your-business-data.md#train)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3 |[Utiliser des comptes d’administrateur dédiés](secure-your-business-data.md#admin)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4 |[Augmenter le niveau de protection contre les programmes malveillants dans le courrier électronique](secure-your-business-data.md#malware)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5 |[Se protéger contre les rançongiciels](secure-your-business-data.md#ransomware)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6 |[Arrêter le forwarding automatique pour le courrier électronique](secure-your-business-data.md#forwarding)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7 |[Utiliser Office chiffrement de messages](secure-your-business-data.md#encryption)||![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8 |[Protéger votre courrier électronique contre les attaques par hameçonnage](secure-your-business-data.md#phishing)||![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9 |[Se protéger contre les pièces jointes et les fichiers malveillants Coffre pièces jointes](secure-your-business-data.md#atp)||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10 |[Se protéger contre les attaques par hameçonnage à l’Coffre liens](secure-your-business-data.md#phishingatp)||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|

Si vous avez Microsoft Business Premium, la façon la plus rapide de configurer la sécurité et de commencer à collaborer en toute sécurité consiste à suivre les instructions de cette bibliothèque : [Microsoft 365 pour les petites entreprises et les campagnes](../../campaigns/index.md). Ces conseils ont été développés en partenariat avec l’équipe Microsoft Microsoft Defending Democracy pour protéger tous les clients de PME contre les menaces informatiques lancées par des pirates informatiques sophistiqués.

Avant de commencer, vérifiez votre score [de Microsoft 365 dans](../../security/defender/microsoft-secure-score.md) le centre Microsoft 365 sécurité. À partir d’un tableau de bord centralisé, vous pouvez surveiller et améliorer la sécurité de votre Microsoft 365, données, applications, appareils et infrastructure. Des points vous sont attribués pour configurer les fonctionnalités de sécurité recommandées, effectuer des tâches liées à la sécurité (telles que l’affichage de rapports) ou répondre à des recommandations avec une application ou un logiciel tiers. Grâce à des informations supplémentaires et à une visibilité accrue sur un ensemble plus large de produits et de services Microsoft, vous pouvez être certain de signaler l’état de sécurité de votre organisation.

![Capture d’écran du score de sécurité Microsoft.](../../media/secure-score.png)

## <a name="1-set-up-multi-factor-authentication"></a>1 : configurer l’authentification multifacteur
<a name="setup"> </a>

L’utilisation de l’authentification multifacteur est l’un des moyens les plus simples et les plus efficaces d’augmenter la sécurité de votre organisation. Il est plus facile que cela n’y paraît : lorsque vous vous connectez, l’authentification multifacteur signifie que vous tapez un code à partir de votre téléphone pour accéder à Microsoft 365. Cela peut empêcher les pirates informatiques de prendre le contrôle s’ils connaissent votre mot de passe. L’authentification multifacteur est également appelée vérification en deux étapes. Les utilisateurs peuvent facilement ajouter la vérification en deux étapes à la plupart des comptes, par exemple, à leurs comptes Google ou Microsoft. Voici comment ajouter la vérification en [deux étapes à votre compte Microsoft personnel.](https://go.microsoft.com/fwlink/p/?linkid=2016403)

Pour les entreprises utilisant Microsoft 365, ajoutez un paramètre qui exige que vos utilisateurs se connectent à l’aide de l’authentification multifacteur. Lorsque vous a effectuer cette modification, les utilisateurs sont invités à configurer leur téléphone pour l’authentification à deux facteurs la prochaine fois qu’ils se connectent.
Pour voir une vidéo de formation sur la façon de configurer l’famf et la façon dont les utilisateurs terminent la mise en place, voir [configurer](../../business-video/turn-on-mfa.md) l’mf et configurer [l’utilisateur.](../../business-video/set-up-mfa.md)

Pour configurer l’authentification multifacteur, vous devez activer les paramètres de sécurité par défaut :

Pour la plupart des organisations, les valeurs de sécurité par défaut offrent un niveau de sécurité de connexion supplémentaire. Pour plus d’informations, voir [Présentation des paramètres de sécurité par défaut](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Si votre abonnement est nouveau, les paramètres par défaut de sécurité peuvent déjà être activés automatiquement.

Pour activer ou désactiver les paramètres de sécurité par défaut, accédez au volet **Propriétés** pour Azure Active Directory (Azure AD) dans le Portail Azure.

1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) avec des informations d'identification d'administrateur général.
2. Dans le volet de navigation gauche, sélectionnez **Afficher tout** puis sous **Centres d’administration**, sélectionnez **Azure Active Directory**.
3. Dans le centre d’administration **Azure Active Directory** sélectionnez **Azure Active Directory** > **Propriétés**.
4. Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
5. Sélectionnez **Oui** pour activer les paramètres de sécurité par défaut ou **Non** pour désactiver les paramètres de sécurité par défaut, puis choisissez **Enregistrer**.

Une fois défini Multi-Factor Authentification pour votre organisation, vos utilisateurs doivent configurer la vérification en deux étapes. Pour plus d’informations, voir [Configurer la vérification en deux étapes pour Microsoft 365](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

Pour obtenir des informations complètes et des recommandations complètes, voir [Configurer l’authentification multifacteur pour les utilisateurs.](set-up-multi-factor-authentication.md)

## <a name="2-train-your-users"></a>2 : Former vos utilisateurs
<a name="train"> </a>

Le manuel de campagne de [cyber-sécurité](https://go.microsoft.com/fwlink/p/?linkid=2015598) de l’établissement de Contrôles School fournit d’excellents conseils sur l’établissement d’une culture forte de sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage.

En plus de ces conseils, Microsoft recommande à vos utilisateurs d’prendre les mesures décrites dans cet article : Protéger votre compte et vos appareils contre les pirates [informatiques et les programmes malveillants.](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6) Ces actions incluent :

- Utilisation de mots de passe forts

- Protection des appareils

- Activation des fonctionnalités de sécurité sur Windows 10 mac et pc

Microsoft recommande également aux utilisateurs de protéger leurs comptes de messagerie personnels en prenant les mesures recommandées dans les articles suivants :

- [Protéger votre compte Outlook.com](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Protéger votre compte Gmail avec la vérification en deux étapes](https://go.microsoft.com/fwlink/p/?linkid=2015688&)

## <a name="3-use-dedicated-admin-accounts"></a>3 : utiliser des comptes d’administrateur dédiés
<a name="admin"> </a>

Les comptes d’administration que vous utilisez pour administrer Microsoft 365 environnement de gestion incluent des privilèges élevés. Ce sont des cibles précieuses pour les pirates informatiques et les cybercriminels. Utilisez des comptes d’administrateur uniquement pour l’administration. Les administrateurs doivent avoir un compte d’utilisateur distinct pour une utilisation normale et non administrative et utiliser leur compte administratif uniquement si nécessaire pour effectuer une tâche associée à leur fonction. Recommandations supplémentaires :

- Assurez-vous que les comptes d’administrateur sont également mis en place pour l’authentification multifacteur.

- Avant d’utiliser des comptes d’administrateur, fermez toutes les applications et sessions de navigateur non liées, y compris les comptes de messagerie personnels.

- Après avoir terminé les tâches d’administration, n’oubliez pas de vous déconnecter de la session du navigateur.

## <a name="4-raise-the-level-of-protection-against-malware-in-mail"></a>4 : augmenter le niveau de protection contre les programmes malveillants dans le courrier électronique
<a name="malware"> </a>

Votre environnement Microsoft 365 inclut une protection contre les programmes malveillants, mais vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants. Pour faire monter la protection contre les programmes malveillants dans le courrier électronique, regardez une courte vidéo de [formation](../../business-video/anti-malware.md)ou complétez les étapes suivantes :

1. Connectez-vous <https://protection.office.com> avec vos informations d’identification de compte d’administrateur.

2. Dans le Centre de sécurité & conformité, dans le volet de  navigation de gauche, sous Gestion des menaces, choisissez Stratégie \> **anti-programme malveillant.**

3. Double-cliquez sur la stratégie par défaut pour modifier cette stratégie à l’échelle de l’entreprise.

4. Sélectionnez **Paramètres**.

5. Sous **Filtre Types de pièces jointes courants,** **sélectionnez Sur**. Les types de fichiers bloqués sont répertoriés dans la fenêtre directement sous ce contrôle. Vous pouvez ajouter ou supprimer des types de fichiers ultérieurement, si nécessaire.

6. Sélectionnez **Enregistrer.**

Pour plus d’informations, voir [Protection contre les programmes malveillants dans EOP.](../../security/office-365-security/anti-malware-protection.md)

## <a name="5-protect-against-ransomware"></a>5 : se protéger contre les ransomware
<a name="ransomware"> </a>

Un ransomware limite l’accès aux données en chiffrant des fichiers ou en verrouiller les écrans d’ordinateur. Il tente ensuite d’extorquer de l’argent à des personnes victime en demandant « rançon », généralement sous forme de cryptomonnaie telle que Cryptograph, en échange de l’accès aux données.

Vous pouvez vous protéger contre les ransomware en créant une ou plusieurs règles de flux de messagerie pour bloquer les extensions de fichier couramment utilisées pour les ransomware, ou pour avertir les utilisateurs qui reçoivent ces pièces jointes par courrier électronique. Un bon point de départ consiste à créer deux règles :

- Avertissez les utilisateurs avant Office pièces jointes qui incluent des macros. Les ransomware peuvent être masqués dans les macros. Nous avertirons donc les utilisateurs de ne pas ouvrir ces fichiers à partir de personnes qu’ils ne connaissent pas.

- Bloquer les types de fichiers qui peuvent contenir un ransomware ou un autre code malveillant. Nous allons commencer par une liste commune d’exécutables (répertoriés dans le tableau ci-dessous). Si votre organisation utilise l’un de ces types d’exécutables et que vous prévoyez qu’ils soient envoyés par courrier électronique, ajoutez-les à la règle précédente (avertir les utilisateurs).

Pour créer une règle de transport de courrier, regardez une courte vidéo de [formation](../../business-video/prevent-ransom-in-email.md)ou complétez les étapes suivantes :

1. Accédez au [Centre d’administration Exchange](https://go.microsoft.com/fwlink/p/?linkid=2059104).

2. Dans la catégorie **de flux de messagerie,** sélectionnez **des règles.**

3. **+** Sélectionnez, puis **créez une règle.**

4. Sélectionnez **** en bas de la boîte de dialogue pour voir l’ensemble complet des options.

5. Appliquez les paramètres du tableau suivant pour chaque règle. Laissez le reste des paramètres par défaut, sauf si vous souhaitez les modifier.

6. Cliquez sur **Enregistrer**.
    
| Paramètre | Avertir les utilisateurs avant d’ouvrir les pièces jointes Office fichiers | Bloquer les types de fichiers qui peuvent contenir un ransomware ou un autre code malveillant |
|:-----|:-----|:-----|
|Nom  <br/> |Règle anti-ransomware : avertir les utilisateurs  <br/> |Règle anti-ransomware : bloquer les types de fichiers  <br/> |
|Appliquez cette règle si . . .  <br/> |N’importe quelle pièce jointe . . . l’extension de fichier correspond à . . .  <br/> |N’importe quelle pièce jointe . . . l’extension de fichier correspond à . . .  <br/> |
|Spécifier des mots ou des expressions  <br/> |Ajoutez les types de fichiers ci-après :  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm  <br/> |Ajoutez les types de fichiers ci-après :  <br/> ade, adp, ani, bas, bat, chm, cmd, com, bdc, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pifif  <br/> |
|Faites les choses suivantes . . .  <br/> |Préséance d’une clause d’exclusion de responsabilité  <br/> |Bloquer le message . . . rejeter le message et inclure une explication  <br/> |
|Fournir le texte du message  <br/> |N’ouvrez pas ces types de fichiers, sauf si vous les attendiez, car les fichiers peuvent contenir du code malveillant et savoir que l’expéditeur n’est pas une garantie de sécurité.  <br/> ||
   
> [!TIP]
> Vous pouvez également ajouter les fichiers que vous souhaitez bloquer à la liste anti-programme malveillant à [l’étape 4.](#4-raise-the-level-of-protection-against-malware-in-mail)

Pour plus d’informations, voir :

- [Ransomware : comment réduire les risques](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Restaurer votre OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="6-stop-auto-forwarding-for-email"></a>6 : Arrêter le forwarding automatique pour le courrier électronique
<a name="forwarding"> </a>

Les pirates informatiques qui accèdent à la boîte aux lettres d’un utilisateur peuvent exfiltrer le courrier en configurant la boîte aux lettres de manière à ce qu’elle le soit automatiquement. Cela peut se produire même sans la sensibilisation de l’utilisateur. Vous pouvez empêcher cela en configurant une règle de flux de messagerie.

Pour créer une règle de transport de messagerie :

1. Accédez au [Centre d’administration Exchange](https://go.microsoft.com/fwlink/p/?linkid=2059104).

2. Dans la catégorie **de flux de messagerie,** sélectionnez **des règles.**

3. **+** Sélectionnez, puis **créez une règle.**

4. Sélectionnez **plus d’options** en bas de la boîte de dialogue pour voir l’ensemble complet des options.

5. Appliquez les paramètres du tableau suivant. Laissez le reste des paramètres par défaut, sauf si vous souhaitez les modifier.

6. Cliquez sur **Enregistrer**.

|Paramètre|Rejeter les e-mails de forward automatique vers des domaines externes|
|---|---|
|Nom|Empêcher le forwarding automatique du courrier électronique vers des domaines externes|
|Appliquez cette règle si...|L’expéditeur . . . est externe/interne . . . À l’intérieur de l’organisation|
|Ajouter une condition|Le destinataire . . . est externe/interne . . . En dehors de l’organisation|
|Ajouter une condition|Propriétés du message . . . inclure le type de message . . . Auto-forward|
|Faites les choses suivantes ...|Bloquer le message . . . rejeter le message et inclure une explication.|
|Fournir le texte du message|Le courrier électronique à l’extérieur de cette organisation est interdit pour des raisons de sécurité.|

## <a name="7-use-office-message-encryption"></a>7 : Utiliser le chiffrement Office messages
<a name="encryption"> </a>

Office Le chiffrement de messages est inclus dans Microsoft 365. Il est déjà installé. Grâce Office chiffrement de messages, votre organisation peut envoyer et recevoir des messages électroniques chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. Chiffrement de messages Office 365 fonctionne avec Outlook.com, Yahoo !, Gmail et d’autres services de messagerie. Le chiffrement des messages électroniques permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu des messages.

Office Le chiffrement de messages offre deux options de protection lors de l’envoi de messages :

- Ne pas avancer

- Chiffrer

Votre organisation a peut-être configuré des options supplémentaires qui appliquent une étiquette à un e-mail, telles que Confidentiel.

### <a name="to-send-protected-email"></a>Pour envoyer des e-mails protégés

In Outlook for PC, select **Options** in the email, and then choose **Permissions**.

![Chiffrement des messages électroniques dans Outlook.](../../media/08e90a7e-a2d2-41a4-bae9-0a46b4ce639a.png)

Dans Outlook.com, **sélectionnez Protéger** dans le courrier électronique. La protection par défaut est **Ne pas avancer.** Pour modifier ce chiffrement, **sélectionnez Modifier les autorisations** \> **Chiffrer.**

![Chiffrement des messages électroniques dans Outlook.com.](../../media/329ccf50-f6b1-4fb8-b249-60b907a82b7e.png)

### <a name="to-receive-encrypted-email"></a>Pour recevoir des e-mails chiffrés

Si le destinataire dispose de Outlook 2013 ou Outlook 2016 et d’un compte de messagerie Microsoft, une alerte s’affichant concernant les autorisations restreintes de l’élément s’affichant dans le volet de lecture. Une fois le message ouvert, le destinataire peut afficher le message comme n’importe quel autre message.

Si le destinataire utilise un autre client de messagerie ou compte de messagerie, tel que Gmail ou Yahoo, il voit un lien qui lui permet de se connecter pour lire le message électronique ou de demander un code secret à usage unique pour afficher le message dans un navigateur web. Si les utilisateurs ne reçoivent pas le courrier électronique, leur faire vérifier leur dossier Courrier indésirable ou Courrier indésirable.

Pour plus d’informations, voir [Envoyer, afficher et](https://support.microsoft.com/office/eaa43495-9bbb-4fca-922a-df90dee51980)répondre à des messages chiffrés Outlook pc.

## <a name="8-protect-your-email-from-phishing-attacks"></a>8. Protéger votre courrier électronique contre les attaques par hameçonnage
<a name="phishing"> </a>

Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Microsoft 365, vous pouvez configurer une protection anti-hameçonnage ciblée. La protection anti-hameçonnage, qui fait partie de Microsoft Defender pour Office 365, peut vous aider à protéger votre organisation contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillant et d’autres attaques par hameçonnage. Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin de le faire.

Nous vous recommandons de commencer avec cette protection en créant une stratégie pour protéger vos utilisateurs les plus importants et votre domaine personnalisé.

![Création d’une stratégie anti-hameçonnage dans Microsoft Defender pour Office 365.](../../media/security-and-compliance-center.png)

Pour créer une stratégie anti-hameçonnage dans Defender pour Office 365, regardez une courte vidéo de [formation](../../business-video/setup-anti-phishing.md)ou complétez les étapes suivantes :

1. Accédez à <https://protection.office.com>.

2. Dans le Centre de sécurité & conformité, dans le volet de navigation de gauche, sous Gestion des menaces, sélectionnez **Stratégie**.

3. Dans la page Stratégie, sélectionnez **Anti-hameçonnage.**

4. Dans la page Anti-hameçonnage, **sélectionnez + Créer.** Un Assistant vous lance pour définir votre stratégie anti-hameçonnage.

5. Spécifiez le nom, la description et les paramètres de votre stratégie comme recommandé dans le graphique ci-dessous. Pour [plus d’informations,](../../security/office-365-security/set-up-anti-phishing-policies.md) voir la stratégie anti-hameçonnage dans Microsoft Defender Office 365 options de protection.

6. Après avoir examiné vos paramètres, **sélectionnez Créer cette stratégie ou** **Enregistrer,** le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Domaine et personnel de campagne le plus précieux|
|Description|Assurez-vous que le personnel le plus important et notre domaine ne sont pas usurpés.|
|Ajouter des utilisateurs à protéger|Select **+ Add a condition, The recipient is**. Tapez les noms des utilisateurs ou entrez l’adresse e-mail du candidat, du responsable de campagne et d’autres membres importants du personnel. Vous pouvez ajouter jusqu’à 20 adresses internes et externes que vous souhaitez protéger contre l’emprunt d’identité.|
|Ajouter des domaines à protéger|Sélectionnez **+ Ajoutez une condition, le domaine du destinataire est**. Entrez le domaine personnalisé associé à votre abonnement Microsoft 365, si vous en avez défini un. Vous pouvez entrer plusieurs domaines.|
|Choisir des actions|Si un message électronique est envoyé par un utilisateur dont l’identité est usurpée : sélectionnez **Rediriger le message** vers une autre adresse e-mail, puis tapez l’adresse de messagerie de l’administrateur de la sécurité . par exemple, securityadmin@contoso.com. <br/> Si le courrier électronique est envoyé par un domaine dont l’identité est usurpée : sélectionnez **le message de mise en quarantaine.**|
|Veille des boîtes aux lettres|Par défaut, la veille des boîtes aux lettres est activée lorsque vous créez une stratégie anti-hameçonnage. Laissez ce paramètre **activé** pour obtenir de meilleurs résultats.|
|Ajouter des expéditeurs et domaines de confiance|Pour cet exemple, ne définissez pas de remplacement.|
|Appliqué à|Sélectionnez **Le domaine du destinataire est**. Sous **Un de ces éléments**, sélectionnez **Choisir**. Sélectionnez **+ Ajouter**. Cochez la case en regard du nom du domaine, par exemple, contoso.com, dans la liste, puis sélectionnez **Ajouter**. Sélectionnez **Terminé**.|
|

Pour plus d’informations, voir [Configurer des stratégies anti-hameçonnage dans Defender pour Office 365](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

## <a name="9-protect-against-malicious-attachments-and-files-with-safe-attachments"></a>9 : Se protéger contre les pièces jointes et les fichiers malveillants Coffre pièces jointes
<a name="atp"> </a>

Les personnes envoient, reçoivent et partagent régulièrement des pièces jointes, telles que des documents, des présentations, des feuilles de calcul, etc. Il n’est pas toujours facile de savoir si une pièce jointe est sûre ou malveillante en regardant simplement un message électronique. Microsoft Defender pour Office 365 inclut Coffre protection contre les pièces jointes, mais cette protection n’est pas désactivée par défaut. Nous vous recommandons de créer une règle pour commencer à utiliser cette protection. Cette protection s’étend aux fichiers SharePoint, OneDrive et Microsoft Teams.

Pour créer une stratégie Coffre pièces jointes, regardez une courte vidéo de [formation](../../business-video/safe-attachments.md)ou complétez les étapes suivantes :

1. Go to <https://protection.office.com> and sign in with your admin account.

2. Dans le Centre de sécurité & conformité, dans le volet de navigation de gauche, sous Gestion des menaces, sélectionnez **Stratégie**.

3. Dans la page Stratégie, **sélectionnez Coffre pièces jointes.**

4. Sur la page Coffre pièces jointes, appliquez cette protection à grande étendue en selecting the **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams** check box.

5. Sélectionnez **+** pour créer une stratégie.

6. Appliquez les paramètres du tableau suivant.

7. Après avoir examiné vos paramètres, **sélectionnez Créer cette stratégie ou** **Enregistrer,** le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Bloquer les messages électroniques actuels et futurs avec les programmes malveillants détectés.|
|Description|Bloquer les messages électroniques et pièces jointes actuels et futurs avec les programmes malveillants détectés.|
|Enregistrer les pièces jointes d’une réponse anti-programme malveillant inconnue|Select **Block - Block the current and future emails and attachments with detected malware**.|
|Rediriger la pièce jointe lors de la détection|Activer la redirection (sélectionnez cette case) <br/> Entrez le compte d’administrateur ou une boîte aux lettres configurée pour la mise en quarantaine. <br/> Appliquez la sélection ci-dessus si l’analyse des programmes malveillants pour les pièces jointes arrive à son moment ou si une erreur se produit (sélectionnez cette zone).|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|
|

Pour plus d’informations, voir [Configurer des stratégies anti-hameçonnage dans Defender pour Office 365](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

## <a name="10-protect-against-phishing-attacks-with-safe-links"></a>10 : Se protéger contre les attaques par hameçonnage à l’Coffre liens
<a name="phishingatp"> </a>

Les pirates informatiques masquent parfois des sites web malveillants dans des liens dans des e-mails ou d’autres fichiers. Coffre Les liens, qui font partie de Microsoft Defender pour Office 365, peuvent aider à protéger votre organisation en fournissant la vérification au moment du clic des adresses web (URL) dans les messages électroniques et les documents Office documents. La protection est définie par le biais Coffre de liens.

Nous vous recommandons d’y faire les choses suivantes :

- Modifiez la stratégie par défaut pour renforcer la protection.

- Ajoutez une nouvelle stratégie destinée à tous les destinataires de votre domaine.

Pour obtenir des Coffre, regardez une courte vidéo de [formation](../../business-video/safe-links.md)ou complétez les étapes suivantes :

1. Go to <https://protection.office.com> and sign in with your admin account.

2. Dans le Centre de sécurité & conformité, dans le volet de navigation de gauche, sous Gestion des menaces, sélectionnez **Stratégie**.

3. Dans la page Stratégie, sélectionnez **Coffre liens.**

Pour modifier la stratégie par défaut :

1. Dans la page Coffre liens, sous **Stratégies** qui s’appliquent à l’ensemble de l’organisation, double-cliquez sur la **stratégie par** défaut.

2. Sous Paramètres qui s’appliquent au contenu dans **Office 365,** entrez une URL à bloquer, telle que _example.com,_ puis sélectionnez **+** .

3. Sous **Paramètres** qui s’appliquent au contenu à l’exception de la messagerie, sélectionnez **Office 365 applications**, Ne pas suivre quand les utilisateurs cliquent sur les liens sécurisés et Ne pas laisser les utilisateurs cliquer sur les liens sécurisés vers l’URL d’origine.  

4. Cliquez sur **Enregistrer**.

Pour créer une stratégie destinée à tous les destinataires de votre domaine :

1. Dans la page Coffre liens, sous Stratégies qui s’appliquent à des **destinataires spécifiques,** sélectionnez **+** pour créer une stratégie.

2. Appliquez les paramètres répertoriés dans le tableau suivant.

3. Cliquez sur **Enregistrer**.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Coffre de liens pour tous les destinataires du domaine|
|Sélectionner l’action pour les URL potentiellement malveillantes inconnues dans les messages|Sélectionnez Sur : les URL seront réécrites et vérifiées par rapport à une liste de liens malveillants connus lorsque l’utilisateur **clique sur le lien.**|
|Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers|Sélectionnez cette case.|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|
|

Pour plus d’informations, [Coffre liens vers Microsoft Defender pour Office 365](../../security/office-365-security/atp-safe-links.md).

## <a name="related-content"></a>Contenu associé

[Authentification multifacteur pour Microsoft 365](multi-factor-authentication-microsoft-365.md) (article)\
[Gérer et surveiller les comptes de priorité](../setup/priority-accounts.md) (article)\
[Microsoft 365 rapports dans le Centre d’administration](../activity-reports/activity-reports.md) (vidéo)