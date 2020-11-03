---
title: 10 façons de sécuriser les offres Microsoft 365 pour les entreprises
f1.keywords:
- CSH
ms.author: sirkkuw
author: sirkkuw
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: de2da300-dbb6-4725-bb12-b85a9d296e75
description: 'Protégez votre courrier électronique et vos données professionnelles contre les menaces informatiques, notamment les ransomware, le hameçonnage et les pièces jointes malveillantes. '
ms.openlocfilehash: c74b8a096afe1dbdd0e0d0cdc7ca5ce3fe8f9ea8
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48843317"
---
# <a name="top-10-ways-to-secure-microsoft-365-for-business-plans"></a>10 façons de sécuriser les offres Microsoft 365 pour les entreprises

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

Si vous êtes une petite ou moyenne organisation utilisant l’un des plans de gestion de Microsoft et que votre type d’organisation est ciblé par les cybercriminels et les pirates, utilisez les conseils fournis dans cet article pour renforcer la sécurité de votre organisation. Ces instructions aident votre organisation à atteindre les objectifs décrits dans le manuel de [campagne](https://go.microsoft.com/fwlink/p/?linkid=2015598)Harvard Kennedy School Cybersecurity.

Microsoft vous recommande d’effectuer les tâches indiquées dans le tableau suivant qui s’appliquent à votre plan de service.

||Tâche|Microsoft 365 Business Standard|Microsoft 365 Business Premium|
|---|---|---|---|
|0,1|[Configurer l’authentification multifacteur](secure-your-business-data.md#setup)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|n°2|[Former vos utilisateurs](secure-your-business-data.md#train)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[Utiliser des comptes d’administration dédiés](secure-your-business-data.md#admin)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4 |[Augmenter le niveau de protection contre les programmes malveillants dans les messages](secure-your-business-data.md#malware)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5 |[Se protéger contre les rançongiciels](secure-your-business-data.md#ransomware)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6 |[Arrêter le transfert automatique pour le courrier électronique](secure-your-business-data.md#forwarding)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7 |[Utiliser le chiffrement de messages Office](secure-your-business-data.md#encryption)||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8 |[Protéger votre courrier électronique contre les attaques par hameçonnage](secure-your-business-data.md#phishing)||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9 |[Se protéger contre les pièces jointes et les fichiers malveillants avec des pièces jointes fiables](secure-your-business-data.md#atp)||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10 |[Protection contre les attaques par hameçonnage avec des liens fiables](secure-your-business-data.md#phishingatp)||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|

Avant de commencer, vérifiez votre [score de sécurité microsoft 365](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-secure-score) dans le centre de sécurité Microsoft 365. À partir d’un tableau de bord centralisé, vous pouvez surveiller et améliorer la sécurité de vos identités, données, applications, périphériques et infrastructure Microsoft 365. Vous disposez de points pour la configuration des fonctionnalités de sécurité recommandées, l’exécution de tâches liées à la sécurité (telles que l’affichage de rapports) ou l’adressage de recommandations avec une application ou un logiciel tiers. Avec des informations supplémentaires et une meilleure visibilité sur un ensemble plus large de produits et services Microsoft, vous pouvez vous sentir confiant des rapports sur l’état de la sécurité de votre organisation.

![Capture d’écran du score de sécurité Microsoft](../../media/secure-score.png)

## <a name="1-set-up-multi-factor-authentication"></a>1 : configurer l’authentification multifacteur
<a name="setup"> </a>

L’utilisation de l’authentification multifacteur est l’une des méthodes les plus simples et les plus efficaces pour renforcer la sécurité de votre organisation. Il est plus facile qu’il ne le semble lorsque vous vous connectez, l’authentification multifacteur vous permet de taper un code à partir de votre téléphone pour accéder à Microsoft 365. Cela peut empêcher les pirates de prendre le relais s’ils connaissent votre mot de passe. L’authentification multifacteur est également appelée vérification en deux étapes. Les utilisateurs peuvent ajouter facilement la vérification en deux étapes à la plupart des comptes, par exemple, à leurs comptes Google ou Microsoft. Voici comment [Ajouter une vérification en deux étapes à votre compte Microsoft personnel](https://go.microsoft.com/fwlink/p/?linkid=2016403).

Pour les entreprises qui utilisent Microsoft 365, ajoutez un paramètre qui exige que vos utilisateurs se connectent à l’aide de l’authentification multifacteur. Lorsque vous effectuez cette modification, les utilisateurs sont invités à configurer leur téléphone pour l’authentification à deux facteurs la prochaine fois qu’ils se connectent.
Pour voir une vidéo de formation sur la configuration de l’authentification multifacteur et sur la façon dont les utilisateurs terminent la configuration, consultez la rubrique [configurer l’authentification multifacteur](https://support.microsoft.com/office/e12187b8-216a-4490-9e3b-df34a06fb787) et l' [utilisateur](https://support.microsoft.com/office/a32541df-079c-420d-9395-9d59354f7225).

Pour configurer l’authentification multifacteur, vous activez les paramètres de sécurité par défaut :

Pour la plupart des organisations, les valeurs de sécurité par défaut offrent un niveau de sécurité de connexion supplémentaire. Pour plus d’informations, voir [Présentation des paramètres de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Si votre abonnement est nouveau, les paramètres par défaut de sécurité peuvent déjà être activés automatiquement.

Pour activer ou désactiver les paramètres de sécurité par défaut, accédez au volet **Propriétés** pour Azure Active Directory (Azure AD) dans le Portail Azure.

1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) avec des informations d'identification d'administrateur général.
2. Dans le volet de navigation gauche, sélectionnez **Afficher tout** puis sous **Centres d’administration** , sélectionnez **Azure Active Directory**.
3. Dans le centre d’administration **Azure Active Directory** sélectionnez **Azure Active Directory** > **Propriétés**.
4. Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
5. Sélectionnez **Oui** pour activer les paramètres de sécurité par défaut ou **Non** pour désactiver les paramètres de sécurité par défaut, puis choisissez **Enregistrer**.

Une fois défini Multi-Factor Authentification pour votre organisation, vos utilisateurs doivent configurer la vérification en deux étapes. Pour plus d’informations, reportez-vous à la rubrique [set up 2-Step Verification for Microsoft 365](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

Pour obtenir des informations complètes et des recommandations complètes, consultez la rubrique [set up Multi-Factor Authentication for Users](set-up-multi-factor-authentication.md).

## <a name="2-train-your-users"></a>2 : former vos utilisateurs
<a name="train"> </a>

Le manuel de la [campagne](https://go.microsoft.com/fwlink/p/?linkid=2015598) Harvard Kennedy School Cybersecurity fournit des conseils excellents sur l’établissement d’une culture forte de la sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage.

En plus de ces conseils, Microsoft recommande à vos utilisateurs d’effectuer les actions décrites dans cet article : [protéger votre compte et vos appareils contre les pirates et les programmes malveillants](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Ces actions incluent :

- Utilisation de mots de passe forts

- Protection des appareils

- Activation des fonctionnalités de sécurité sur les PC Windows 10 et Mac

Microsoft recommande également aux utilisateurs de protéger leurs comptes de messagerie personnels en effectuant les actions recommandées dans les articles suivants :

- [Protéger votre compte de messagerie Outlook.com](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Protégez votre compte Gmail à l’aide de la vérification en deux étapes](https://go.microsoft.com/fwlink/p/?linkid=2015688&)

## <a name="3-use-dedicated-admin-accounts"></a>3 : utiliser des comptes d’administration dédiés
<a name="admin"> </a>

Les comptes d’administration que vous utilisez pour administrer votre environnement Microsoft 365 incluent des privilèges élevés. Il s’agit de cibles précieuses pour les pirates et les cybercriminels. Utilisez les comptes administrateur uniquement pour l’administration. Les administrateurs doivent disposer d’un compte d’utilisateur distinct pour une utilisation normale et non administrative et n’utiliser leur compte d’administrateur que si nécessaire pour effectuer une tâche associée à leur fonction. Recommandations supplémentaires :

- Assurez-vous que les comptes administrateur sont également configurés pour l’authentification multifacteur.

- Avant d’utiliser les comptes d’administrateur, fermez toutes les sessions de navigateur et les applications qui ne sont pas associées, y compris les comptes de messagerie personnels.

- Après avoir effectué les tâches d’administration, veillez à vous déconnecter de la session du navigateur.

## <a name="4-raise-the-level-of-protection-against-malware-in-mail"></a>4 : augmenter le niveau de protection contre les programmes malveillants dans les messages
<a name="malware"> </a>

Votre environnement Microsoft 365 inclut une protection contre les programmes malveillants, mais vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants. Pour augmenter la protection contre les programmes malveillants dans le courrier électronique, consultez une [vidéo de formation courte](https://support.microsoft.com/office/02b5783a-eea0-42e8-8856-62440718c3f0)ou effectuez les étapes suivantes :

1. Accédez à <https://protection.office.com> et connectez-vous avec vos informations d’identification de compte d’administrateur.

2. Dans le centre de navigation de gauche du centre de sécurité & conformité, sous **gestion des menaces** , sélectionnez **stratégie** \> **anti-programme malveillant**.

3. Double-cliquez sur la stratégie par défaut pour modifier cette stratégie à l’échelle de l’entreprise.

4. Sélectionnez **Paramètres**.

5. Sous **Common Attachment types Filter** , sélectionnez **activé**. Les types de fichiers bloqués sont répertoriés dans la fenêtre située directement en dessous de ce contrôle. Vous pouvez ajouter ou supprimer des types de fichiers ultérieurement, si nécessaire.

6. Sélectionnez **Enregistrer.**

Pour plus d’informations, consultez la rubrique [protection contre les programmes malveillants dans EOP](https://docs.microsoft.com/microsoft-365/security/office-365-security/anti-malware-protection).

## <a name="5-protect-against-ransomware"></a>5 : protéger contre les ransomware
<a name="ransomware"> </a>

Les ransomware limitent l’accès aux données en chiffrant les fichiers ou en verrouillant les écrans d’ordinateur. Il tente ensuite de extort l’argent des victimes en demandant « ransomware », généralement sous forme de cryptocurrencies comme Bitcoin, dans Exchange pour accéder aux données.

Vous pouvez vous protéger contre les ransomware en créant une ou plusieurs règles de flux de messagerie pour bloquer les extensions de fichiers couramment utilisées pour les ransomware ou pour avertir les utilisateurs qui reçoivent ces pièces jointes par courrier électronique. Un point de départ est de créer deux règles :

- Avertissez les utilisateurs avant l’ouverture de pièces jointes Office qui incluent des macros. Les ransomware peuvent être masqués dans les macros, nous les avertirons donc que les utilisateurs ne pourront pas ouvrir ces fichiers à partir de personnes qu’ils ne connaissent pas.

- Bloquer des types de fichiers pouvant contenir des ransomware ou d’autres codes malveillants. Nous allons commencer par une liste commune des fichiers exécutables (répertoriés dans le tableau ci-dessous). Si votre organisation utilise l’un de ces types d’exécutable et que vous prévoyez de l’envoyer par courrier électronique, ajoutez-les à la règle précédente (avertir les utilisateurs).

Pour créer une règle de transport de messagerie, affichez une [vidéo de formation courte](https://support.microsoft.com/office/a9ecca03-42a6-4867-b9fd-38e3f6bb06ad)ou effectuez les étapes suivantes :

1. Accédez au [Centre d’administration Exchange](https://go.microsoft.com/fwlink/p/?linkid=2059104).

2. Dans la catégorie **flux de messagerie** , sélectionnez **règles**.

3. Sélectionnez **+** , puis **créez une règle**.

4. Sélectionnez * * * * en bas de la boîte de dialogue pour afficher l’ensemble complet des options.

5. Appliquez les paramètres du tableau suivant pour chaque règle. Conservez les autres paramètres par défaut, sauf si vous souhaitez les modifier.

6. Sélectionnez **Enregistrer**.
    
| Paramètres | Avertir les utilisateurs avant l’ouverture de pièces jointes de fichiers Office | Bloquer des types de fichiers pouvant contenir des ransomware ou d’autres codes malveillants |
|:-----|:-----|:-----|
|Nom  <br/> |Règle anti-ransomware : avertir les utilisateurs  <br/> |Règle anti-ransomware : bloquer des types de fichiers  <br/> |
|Appliquez cette règle si. . .  <br/> |N’importe quelle pièce jointe. . . l’extension de fichier correspond à. . .  <br/> |N’importe quelle pièce jointe. . . l’extension de fichier correspond à. . .  <br/> |
|Spécifier des mots ou des expressions  <br/> |Ajoutez les types de fichiers suivants :  <br/> dotm, docm, xlsm, SLTM, xla, xlam, XLL, pptm, potm, ppam, PPSM, sldm  <br/> |Ajoutez les types de fichiers suivants :  <br/> ADE, ADP, Ani, bas, bat, chm, cmd, com, cpl, CRT, HLP, HT, HTA, inf, ins, fournisseur de services Internet, Job, js, jse, lnk, MDA, de mdb, MDE, mdz, MSC, MSI, MSP, MST, PCD, reg, SCR, SCT, SHS, URL, VB, VBE, vbs, WSC, wsf, WSH  <br/> |
|Procédez comme suit. . .  <br/> |Ajouter une clause d’exclusion de responsabilité  <br/> |Bloquer le message. . . rejeter le message et inclure une explication  <br/> |
|Fournir le texte du message  <br/> |N’ouvrez pas ces types de fichiers (sauf s’ils vous attendiez), car les fichiers peuvent contenir du code malveillant et connaître l’expéditeur n’est pas une garantie de sécurité.  <br/> ||
   
> [!TIP]
> Vous pouvez également ajouter les fichiers que vous souhaitez bloquer à la liste anti-programmes malveillants à l' [étape 4](#4-raise-the-level-of-protection-against-malware-in-mail).

Pour plus d’informations, voir :

- [Ransomware : Comment réduire les risques](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Restaurer votre espace OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="6-stop-auto-forwarding-for-email"></a>6 : arrêter le transfert automatique pour le courrier électronique
<a name="forwarding"> </a>

Les pirates qui accèdent à la boîte aux lettres d’un utilisateur peuvent exfiltrer les messages en configurant la boîte aux lettres pour qu’elle transfère automatiquement le courrier électronique. Cela peut se produire même sans la sensibilisation de l’utilisateur. Vous pouvez éviter cela en configurant une règle de flux de messagerie.

Pour créer une règle de transport de messagerie :

1. Accédez au [Centre d’administration Exchange](https://go.microsoft.com/fwlink/p/?linkid=2059104).

2. Dans la catégorie **flux de messagerie** , sélectionnez **règles**.

3. Sélectionnez **+** , puis **créez une règle**.

4. Sélectionnez **plus d’options** en bas de la boîte de dialogue pour afficher l’ensemble complet des options.

5. Appliquez les paramètres dans le tableau suivant. Conservez les autres paramètres par défaut, sauf si vous souhaitez les modifier.

6. Sélectionnez **Enregistrer**.

|Paramètres|Rejeter les messages électroniques de transfert automatique vers les domaines externes|
|---|---|
|Nom|Empêcher le transfert automatique des courriers électroniques vers des domaines externes|
|Appliquer cette règle si...|Expéditeur. . . est externe/interne. . . Au sein de l’Organisation|
|Ajouter une condition|Destinataire. . . est externe/interne. . . À l’extérieur de l’Organisation|
|Ajouter une condition|Propriétés du message. . . inclure le type de message. . . Transfert automatique|
|Procédez comme suit...|Bloquer le message. . . rejeter le message et inclure une explication.|
|Fournir le texte du message|Le transfert automatique du courrier électronique en dehors de cette organisation est interdit pour des raisons de sécurité.|

## <a name="7-use-office-message-encryption"></a>7 : utiliser le chiffrement de messages Office
<a name="encryption"> </a>

Le chiffrement de messages Office est inclus dans Microsoft 365. Elle est déjà configurée. Avec le chiffrement de messages Office, votre organisation peut envoyer et recevoir des messages électroniques chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. Le chiffrement de messages Office 365 fonctionne avec Outlook.com, Yahoo !, Gmail et d’autres services de messagerie. Le chiffrement des messages électroniques permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu du message.

Le chiffrement de messages Office offre deux options de protection lors de l’envoi de messages :

- Ne pas transférer

- Crypté

Il se peut que votre organisation ait configuré des options supplémentaires qui appliquent une étiquette à la messagerie électronique, par exemple, confidentielle.

### <a name="to-send-protected-email"></a>Pour envoyer des messages électroniques protégés

Dans Outlook pour PC, sélectionnez les **options** dans le courrier électronique, puis choisissez **autorisations**.

![Chiffrement des messages électroniques dans Outlook](../../media/08e90a7e-a2d2-41a4-bae9-0a46b4ce639a.png)

Dans Outlook.com, sélectionnez **protéger** dans le message électronique. La protection par défaut est **ne pas transférer**. Pour modifier ce chiffre, sélectionnez **modifier les autorisations** de \> **chiffrement**.

![Chiffrement des messages électroniques dans Outlook.com](../../media/329ccf50-f6b1-4fb8-b249-60b907a82b7e.png)

### <a name="to-receive-encrypted-email"></a>Pour recevoir des messages chiffrés

Si le destinataire dispose d’Outlook 2013 ou Outlook 2016 et d’un compte de messagerie Microsoft, il voit une alerte sur les autorisations restreintes de l’élément dans le volet de lecture. Après l’ouverture du message, le destinataire peut afficher le message comme n’importe quel autre.

Si le destinataire utilise un autre client de messagerie ou un autre compte de messagerie, tel que Gmail ou Yahoo, il voit un lien qui lui permet de se connecter pour lire le message électronique ou de demander un code secret à usage unique pour afficher le message dans un navigateur Web. Si les utilisateurs ne reçoivent pas le courrier électronique, demandez-leur de vérifier leur courrier indésirable ou leur dossier de courrier indésirable.

Pour plus d’informations, consultez la rubrique [Envoyer, afficher et répondre à des messages chiffrés dans Outlook pour PC](https://support.microsoft.com/office/eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="8-protect-your-email-from-phishing-attacks"></a>8. protéger votre courrier électronique contre les attaques de hameçonnage
<a name="phishing"> </a>

Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Microsoft 365, vous pouvez configurer une protection anti-hameçonnage ciblée. La protection anti-hameçonnage, qui fait partie de Microsoft Defender pour Office 365, peut vous aider à protéger votre organisation contre les attaques de hameçonnage malveillant basées sur l’emprunt d’identité et d’autres attaques par hameçonnage. Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin d’effectuer cette opération.

Nous vous recommandons de prendre en main cette protection en créant une stratégie de protection des utilisateurs les plus importants et de votre domaine personnalisé.

![Création d’une stratégie anti-hameçonnage dans Microsoft Defender pour Office 365](../../media/security-and-compliance-center.png)

Pour créer une stratégie anti-hameçonnage dans Defender pour Office 365, affichez une [vidéo de formation courte](https://support.microsoft.com/office/86c425e1-1686-430a-9151-f7176cce4f2c)ou effectuez les étapes suivantes :

1. Accédez à <https://protection.office.com>.

2. Dans le centre de sécurité & sécurité, dans le volet de navigation de gauche, sous **gestion des menaces** , sélectionnez **stratégie**.

3. Sur la page stratégie, sélectionnez **anti-hameçonnage**.

4. Sur la page anti-hameçonnage, sélectionnez **+ créer**. Un Assistant s’ouvre et vous guide tout au long de la définition de votre stratégie anti-hameçonnage.

5. Spécifiez le nom, la description et les paramètres de votre stratégie, comme recommandé dans le graphique ci-dessous. Pour plus d’informations, consultez la rubrique [en savoir plus sur la stratégie anti-hameçonnage dans Microsoft Defender pour Office 365 options](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-anti-phishing-policies) .

6. Une fois que vous avez vérifié vos paramètres, sélectionnez **créer cette stratégie** ou **Enregistrer** , selon le cas.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Domaine et équipe de campagne la plus intéressante|
|Description|Assurez-vous que le personnel le plus important et que notre domaine ne sont pas empruntés.|
|Ajouter des utilisateurs à protéger|Sélectionnez **+ Ajouter une condition, le destinataire est**. Tapez noms d’utilisateur ou entrez l’adresse de messagerie du candidat, du gestionnaire de campagnes et d’autres membres importants du personnel. Vous pouvez ajouter jusqu’à 20 adresses internes et externes que vous souhaitez protéger contre l’emprunt d’identité.|
|Ajouter des domaines à protéger|Sélectionnez **+ Ajouter une condition, le domaine du destinataire est**. Entrez le domaine personnalisé associé à votre abonnement Microsoft 365, si vous en avez défini un. Vous pouvez entrer plusieurs domaines.|
|Choisir des actions|Si un message électronique est envoyé par un utilisateur représenté : sélectionnez **Rediriger le message vers une autre adresse de messagerie** , puis tapez l’adresse de messagerie de l’administrateur de sécurité ; par exemple, securityadmin@contoso.com. <br/> Si le courrier électronique est envoyé par un domaine emprunté : sélectionnez **mettre en quarantaine le message**.|
|Veille des boîtes aux lettres|Par défaut, la veille des boîtes aux lettres est activée lorsque vous créez une stratégie anti-hameçonnage. Laissez ce paramètre **activé** pour obtenir de meilleurs résultats.|
|Ajouter des expéditeurs et domaines de confiance|Pour cet exemple, ne définissez pas de remplacement.|
|Appliqué à|Sélectionnez **Le domaine du destinataire est**. Sous **Un de ces éléments** , sélectionnez **Choisir**. Sélectionnez **+ Ajouter**. Activez la case à cocher en regard du nom du domaine, par exemple, contoso.com, dans la liste, puis sélectionnez **Ajouter**. Sélectionnez **Terminé**.|
|

Pour plus d’informations, consultez la rubrique [configurer des stratégies anti-hameçonnage dans Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/configure-atp-anti-phishing-policies).

## <a name="9-protect-against-malicious-attachments-and-files-with-safe-attachments"></a>9 : se protéger contre les pièces jointes et les fichiers malveillants avec des pièces jointes fiables
<a name="atp"> </a>

Les personnes envoient, reçoivent et partagent régulièrement des pièces jointes, telles que des documents, des présentations, des feuilles de calcul, etc. Il n’est pas toujours facile de déterminer si une pièce jointe est fiable ou malveillante en regardant un message électronique. Microsoft Defender pour Office 365 inclut la protection des pièces jointes sécurisées, mais cette protection n’est pas activée par défaut. Nous vous recommandons de créer une règle pour commencer à utiliser cette protection. Cette protection s’étend aux fichiers dans SharePoint, OneDrive et Microsoft Teams.

Pour créer une stratégie de pièces jointes fiables, affichez une [courte vidéo de formation](https://support.microsoft.com/office/e7e68934-23dc-4b9c-b714-e82e27a8f8a5)ou effectuez les étapes suivantes :

1. Accédez à <https://protection.office.com> et connectez-vous à l’aide de votre compte d’administrateur.

2. Dans le centre de sécurité & sécurité, dans le volet de navigation de gauche, sous **gestion des menaces** , sélectionnez **stratégie**.

3. Sur la page stratégie, sélectionnez **pièces jointes approuvées**.

4. Sur la page pièces jointes fiables, appliquez largement cette protection en activant la case à cocher Activer la protection avancée contre **les menaces pour SharePoint, OneDrive et Microsoft teams** .

5. Sélectionnez cette option **+** pour créer une stratégie.

6. Appliquez les paramètres dans le tableau suivant.

7. Une fois que vous avez vérifié vos paramètres, sélectionnez **créer cette stratégie** ou **Enregistrer** , selon le cas.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Bloquer les courriers électroniques actuels et futurs avec des programmes malveillants détectés.|
|Description|Bloquer les e-mails et pièces jointes en cours et à venir avec des programmes malveillants détectés.|
|Enregistrer les pièces jointes réponse inconnue contre les programmes malveillants|Sélectionnez **bloquer-bloquer les courriers électroniques et pièces jointes actuels et futurs avec des programmes malveillants détectés**.|
|Redirection de la pièce jointe sur la détection|Activer la redirection (activez cette case à cocher) <br/> Entrez le compte administrateur ou une configuration de boîte aux lettres pour la mise en quarantaine. <br/> Appliquer la sélection ci-dessus si l’analyse anti-programmes malveillants pour les pièces jointes expire ou si une erreur se produit (sélectionnez cette case).|
|Appliqué à|Le domaine du destinataire est. . . Sélectionnez votre domaine.|
|

Pour plus d’informations, consultez la rubrique [configurer des stratégies anti-hameçonnage dans Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/configure-atp-anti-phishing-policies).

## <a name="10-protect-against-phishing-attacks-with-safe-links"></a>10 : se protéger contre les attaques par hameçonnage avec des liens fiables
<a name="phishingatp"> </a>

Les pirates masquent parfois des sites Web malveillants dans des liens dans des courriers électroniques ou dans d’autres fichiers. Les liens fiables, qui font partie de Microsoft Defender pour Office 365, peuvent aider à protéger votre organisation en fournissant un temps de vérification des adresses Web (URL) dans les messages électroniques et les documents Office. La protection est définie via les stratégies de liens fiables.

Nous vous recommandons d’effectuer les opérations suivantes :

- Modifiez la stratégie par défaut pour augmenter la protection.

- Ajoutez une nouvelle stratégie ciblée pour tous les destinataires de votre domaine.

Pour accéder aux liens fiables, affichez une [vidéo de formation courte](https://support.microsoft.com/office/61492713-53c2-47da-a6e7-fa97479e97fa)ou effectuez les étapes suivantes :

1. Accédez à <https://protection.office.com> et connectez-vous à l’aide de votre compte d’administrateur.

2. Dans le centre de sécurité & sécurité, dans le volet de navigation de gauche, sous **gestion des menaces** , sélectionnez **stratégie**.

3. Sur la page stratégie, sélectionnez **liaisons approuvées**.

Pour modifier la stratégie par défaut :

1. Sur la page Liens approuvés, sous **stratégies qui s’appliquent à l’ensemble de l’organisation** , double-cliquez sur la stratégie **par défaut** .

2. Sous **paramètres qui s’appliquent au contenu dans Office 365** , entrez une URL à bloquer, telle que _example.com_ , puis sélectionnez **+** .

3. Sous **paramètres qui s’appliquent au contenu à l’exception du courrier électronique** , sélectionnez **applications Office 365** , **ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables** et **ne permettent pas aux utilisateurs de cliquer sur les liens fiables vers l’URL d’origine**.

4. Sélectionnez **Enregistrer**.

Pour créer une stratégie ciblée pour tous les destinataires de votre domaine, procédez comme suit :

1. Sur la page Liens approuvés, sous **stratégies qui s’appliquent à des destinataires spécifiques** , sélectionnez **+** pour créer une nouvelle stratégie.

2. Appliquez les paramètres présentés dans le tableau suivant.

3. Sélectionnez **Enregistrer**.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Stratégie de liens fiables pour tous les destinataires dans le domaine|
|Sélectionner l’action pour les URL potentiellement malveillantes dans les messages|Sélectionnez **les URL activées seront réécrites et vérifiées par rapport à une liste de liens malveillants connus lorsque l’utilisateur clique sur le lien**.|
|Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers|Activez cette case à cocher.|
|Appliqué à|Le domaine du destinataire est. . . Sélectionnez votre domaine.|
|

Pour plus d’informations, reportez-vous à [liens fiables dans Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-links).
