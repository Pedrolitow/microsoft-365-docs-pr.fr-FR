---
title: Meilleures pratiques pour sécuriser Microsoft 365 pour les entreprises
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- VSBFY23
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkDEFENDER
- adminvideo
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: de2da300-dbb6-4725-bb12-b85a9d296e75
description: Protégez vos e-mails et données professionnels contre les cybermenaces, y compris les ransomware, le hameçonnage et les pièces jointes malveillantes.
ms.openlocfilehash: db9822a87c180577afe4040e7828471b993bd0d5
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67087438"
---
# <a name="best-practices-for-securing-microsoft-365-for-business"></a>Meilleures pratiques pour sécuriser Microsoft 365 pour les entreprises

Consultez l'[aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

Si vous êtes une petite ou moyenne organisation utilisant l’un des plans d’entreprise de Microsoft, les conseils de cet article vous aident à renforcer la sécurité de votre organisation. Parmi vos choix, Microsoft 365 Business Premium ouvre la voie, car il inclut désormais Microsoft Defender pour entreprises et d’autres [protections de sécurité](../../business-premium/get-microsoft-365-business-premium.md). Les actions recommandées présentées ici vous aideront à atteindre les objectifs décrits dans le Manuel de la [campagne de cybersécurité](https://go.microsoft.com/fwlink/p/?linkid=2015598) de l’École Harvard Kennedy.

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes décrites dans cet article, envisagez de [travailler avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="watch-a-quick-overview-of-security"></a>Regarder : Vue d’ensemble rapide de la sécurité

Regardez cette vidéo ainsi que d’autres sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198012).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mzxI?autoplay=false]

Tous les plans Microsoft 365 offrent une protection et une sécurité de base avec l’antivirus Defender, mais avec Microsoft 365 Business Premium vous disposez également de fonctionnalités de protection contre les menaces, de protection des données et de gestion des appareils en raison de l’inclusion de Microsoft Defender pour entreprises.  Ces fonctionnalités supplémentaires protègent votre organisation contre les menaces en ligne et l’accès non autorisé, ainsi que vous permettent de gérer les données d’entreprise sur vos téléphones, tablettes et ordinateurs.

## <a name="security-features-comparison"></a>Comparaison des fonctionnalités de sécurité

Pour en savoir plus sur l’une des fonctionnalités du plan de service, cliquez sur le titre du tableau suivant. 

|Tâche|Microsoft 365 Business Standard|Microsoft 365 Business Premium|
|---|---|---|
[Protéger contre les mots de passe perdus ou volés](#set-up-multi-factor-authentication) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
[Former vos utilisateurs](#train-your-users) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
[Utiliser des comptes d’administrateur dédiés](#use-dedicated-admin-accounts)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | 
[Se protéger contre les programmes malveillants](#protect-against-malware) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(protection de l’e-mail) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(protection accrue pour les e-mails et les appareils) |
[Se protéger contre les rançongiciels](#protect-against-ransomware) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(protection pour le courrier électronique et le stockage cloud) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(protection accrue pour les appareils, les e-mails et le stockage cloud) |
[Chiffrer les e-mails sensibles](#send-encrypted-email) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
[Protéger votre courrier contre les attaques par hameçonnage](#protect-sensitive-emails) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(Protection anti-hameçonnage) | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(protection avancée contre le hameçonnage) |
[Protéger contre les pièces jointes, fichiers et URL malveillants dans les fichiers e-mail et Office](#protect-against-malicious-attachments-files-and-urls) | | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(Liens sécurisés et pièces jointes sécurisées) |
[Augmenter la protection des appareils de votre organisation](#increase-protection-for-your-organizations-devices) | | ![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(protection des appareils de niveau entreprise) |

Vous pouvez rapidement configurer la sécurité et commencer à collaborer en toute sécurité avec les conseils que nous fournissons dans la bibliothèque [Microsoft 365 Business Premium](../../business-premium/index.md). Les informations Business Premium ont été développées en partenariat avec l’équipe Microsoft Defending Democracy pour protéger tous les clients des petites entreprises contre les cybermenaces lancées par des cyberattaques sophistiquées et des pirates informatiques.

### <a name="about-the-microsoft-365-secure-score"></a>À propos du degré de sécurisation de Microsoft 365

Avant de commencer, il est important de vérifier votre degré de [sécurisation Microsoft 365](../../security/defender/microsoft-secure-score.md) dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. À partir d’un tableau de bord centralisé, vous pouvez surveiller et améliorer la sécurité de vos identités, données, applications, appareils et infrastructure Microsoft 365. Des points vous sont attribués pour configurer les fonctionnalités de sécurité recommandées, effectuer des tâches liées à la sécurité (telles que l’affichage de rapports) ou répondre aux recommandations avec une application ou un logiciel tiers. Grâce à des insights supplémentaires et à une meilleure visibilité sur un ensemble plus large de produits et services Microsoft, vous pouvez créer des rapports fiables sur l’intégrité de la sécurité de votre organisation.

![Capture d’écran de Microsoft Secure Score.](../../media/secure-score.png)

## <a name="set-up-multi-factor-authentication"></a>Configurer Multi-factor Authentification (MFA)

Protégez-vous contre les mots de passe perdus ou volés à l’aide de l’authentification multifacteur (MFA). Lorsque l’authentification multifacteur est configurée, les utilisateurs doivent utiliser un code sur leur téléphone pour se connecter à Microsoft 365. Cette étape supplémentaire peut empêcher les pirates de prendre le relais s’ils connaissent votre mot de passe. 

L’authentification multifacteur est également appelée vérification en 2 étapes. Les personnes peuvent facilement ajouter la vérification en deux étapes à la plupart des comptes, par exemple, à leurs comptes Google ou Microsoft. Voici comment [ajouter la vérification en deux étapes à votre compte Microsoft personnel](https://go.microsoft.com/fwlink/p/?linkid=2016403).

Pour les entreprises qui utilisent Microsoft 365, ajoutez un paramètre qui oblige vos utilisateurs à se connecter à l’aide de l’authentification multifacteur. Lorsque vous apportez cette modification, les utilisateurs sont invités à configurer leur téléphone pour l’authentification à deux facteurs la prochaine fois qu’ils se connectent.
Pour voir une vidéo de formation sur la configuration de l’authentification multifacteur et la façon dont les utilisateurs terminent la configuration, consultez [configurer l’authentification multifacteur](set-up-multi-factor-authentication.md) et configurer [l’utilisateur](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

### <a name="turn-on-security-defaults"></a>Activer les paramètres de sécurité par défaut

Pour la plupart des organisations, les paramètres de sécurité par défaut offrent un bon niveau de sécurité de connexion ajoutée. Pour plus d’informations, consultez [Présentation des paramètres de sécurité par défaut](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) Si votre abonnement est nouveau, les paramètres de sécurité par défaut peuvent déjà être activés automatiquement.

Activez ou désactivez les paramètres de sécurité par défaut dans le volet **Propriétés** d’Azure Active Directory (Azure AD) dans le Portail Azure.

1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) avec des informations d'identification d'administrateur général.

2. Dans le volet de navigation gauche, sélectionnez **Afficher tout** puis sous **Centres d’administration**, sélectionnez **Azure Active Directory**.

3. Dans le Centre d’administration **Azure Active Directory**, choisissez **Propriétés** **Azure Active Directory** > .

4. Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.

5. Sélectionnez **Oui** pour activer les paramètres de sécurité par défaut ou **Non** pour désactiver les paramètres de sécurité par défaut, puis choisissez **Enregistrer**.

Une fois défini Multi-Factor Authentification pour votre organisation, vos utilisateurs doivent configurer la vérification en deux étapes. Pour plus d’informations, consultez [Configurer la vérification en 2 étapes pour Microsoft 365](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

> [!Tip]
> Si vous avez besoin d’un contrôle plus précis de l’authentification multifacteur, vous pouvez activer l’accès conditionnel avec Microsoft 365 Business Premium. Si vous effectuez cette opération, nous vous recommandons d’implémenter les stratégies équivalentes aux paramètres par défaut de sécurité. Pour plus d’informations sur [les paramètres de sécurité par défaut,](/microsoft-365/business-premium/m365bp-conditional-access) consultez cet article.

Pour plus d’informations et de recommandations, consultez [Configurer l’authentification multifacteur pour les utilisateurs](set-up-multi-factor-authentication.md).

## <a name="train-your-users"></a>Former vos utilisateurs

Le [Manuel de la campagne de cybersécurité](https://go.microsoft.com/fwlink/p/?linkid=2015598) de l’École Harvard Kennedy fournit d’excellents conseils sur l’établissement d’une culture forte de la sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage.

En outre, Microsoft recommande à vos utilisateurs d’effectuer les actions décrites dans cet article : [Protéger votre compte et vos appareils contre les pirates et les programmes malveillants](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Ces actions incluent :

- Utilisation de mots de passe forts
- Protection des appareils
- Activation des fonctionnalités de sécurité sur les PC Windows 10 et Mac

Microsoft recommande également aux utilisateurs de protéger leurs comptes de messagerie personnels en effectuant les actions recommandées dans les articles suivants :

- [Protéger votre compte de messagerie Outlook.com](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Protéger votre compte Gmail avec la vérification en 2 étapes](https://go.microsoft.com/fwlink/p/?linkid=2015688&)

## <a name="use-dedicated-admin-accounts"></a>Utiliser des comptes d’administrateur dédiés

Les comptes d’administration que vous utilisez pour administrer votre environnement Microsoft 365 incluent des privilèges élevés. Il s’agit de cibles précieuses pour les pirates informatiques et les cyber-attaquants. Utilisez des comptes d’administrateur uniquement pour l’administration. Les administrateurs doivent disposer d’un compte d’utilisateur distinct pour une utilisation régulière et non administrative et utiliser uniquement leur compte d’administration si nécessaire pour effectuer une tâche associée à leur fonction de travail. Recommandations supplémentaires :

- Assurez-vous que les comptes sont ajoutés à [Azure Active Directory](../../admin/add-users/add-users.md).
- Assurez-vous que les comptes d’administrateur sont également configurés pour l’authentification multifacteur.
- Avant d’utiliser des comptes d’administrateur, fermez toutes les sessions et applications de navigateur non liées, y compris les comptes de messagerie personnels.
- Une fois les tâches d’administration terminées, veillez à vous déconnecter de la session du navigateur.

## <a name="protect-against-malware"></a>Se protéger contre les programmes malveillants

Votre environnement Microsoft 365 inclut une protection contre les programmes malveillants. Vous pouvez augmenter la protection contre les programmes malveillants en :

- Utilisation [de stratégies prédéfines pour Microsoft Office 365](../../../microsoft-365/security/office-365-security/preset-security-policies.md).
- Blocage des pièces jointes avec certains types de fichiers.
- Utilisation de la protection antivirus/anti-programme malveillant sur vos appareils, en particulier Microsoft Defender pour entreprises. Il inclut des fonctionnalités telles que le [rapport d’investigation automatisé](../../security/office-365-security/air-view-investigation-results.md) (AIR) et le tableau de bord de gestion des menaces et des vulnérabilités (TVM). Lorsque Microsoft Defender pour entreprises n’est pas votre logiciel antivirus principal, vous pouvez toujours l’exécuter en mode passif et utiliser la protection et la réponse de point de [terminaison (EDR),](../../security/defender-endpoint/overview-endpoint-detection-response.md) en particulier en [mode bloc](../../security/defender-endpoint/edr-in-block-mode.md) où il fonctionne en arrière-plan pour corriger les artefacts malveillants détectés par les fonctionnalités d’EDR et manqués par le logiciel détecteur de virus principal.

### <a name="block-attachments-with-certain-file-types"></a>Bloquer les pièces jointes avec certains types de fichiers

Vous pouvez augmenter la protection contre les programmes malveillants en bloquant les pièces jointes avec les types de fichiers couramment utilisés pour les programmes malveillants. Pour augmenter la protection contre les programmes malveillants dans l’e-mail, consultez [Espion : augmentez le niveau de protection contre les programmes malveillants dans le courrier](increase-threat-protection.md#watch-raise-the-level-of-protection-against-malware-in-mail) ou effectuez les étapes suivantes :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, accédez à Email & stratégies de **collaboration** \> **& règles** \> **de** \> protection **contre les programmes malveillants** dans la section **Stratégies**.
2. Dans la page **Anti-programme malveillant** , double-cliquez sur **Par défaut**. Un menu volant s’affiche.
3. Sélectionnez **Modifier les paramètres de protection** en bas du menu volant.
4. Dans la page suivante, sous **Paramètres de protection**, cochez la case en regard **du filtre Activer les pièces jointes courantes**. Les types de fichiers bloqués sont répertoriés directement sous cette option. Pour ajouter ou supprimer des types de fichiers, sélectionnez **Personnaliser les types de fichiers** à la fin de la liste.
5. Sélectionnez **Enregistrer**.

Pour plus d’informations, consultez [Protection anti-programme malveillant dans EOP](../../security/office-365-security/anti-malware-protection.md).

### <a name="use-antivirus-and-anti-malware-protection"></a>Utiliser la protection antivirus et anti-programme malveillant

L’antivirus Microsoft Defender offre une protection antivirus et anti-programme malveillant renforcée, et est intégré au système d’exploitation Windows.

Si votre organisation utilise Microsoft 365 Business Premium, vous bénéficiez d’une protection supplémentaire des appareils, notamment :

- Protection de nouvelle génération
- Protection pare-feu
- Filtrage du contenu web

Ces fonctionnalités sont incluses dans Microsoft Defender pour entreprises, une offre qui commencera à être déployée pour Microsoft 365 Business Premium clients, à compter du 1er mars 2022.

[En savoir plus sur Microsoft Defender pour les PME](../../security/defender-business/mdb-overview.md).

## <a name="protect-against-ransomware"></a>Se protéger contre les rançongiciels

Le ransomware restreint l’accès aux données en chiffrant les fichiers ou en verrouillant les écrans d’ordinateur. Il tente ensuite d’extorquer de l’argent aux victimes en demandant une « rançon », généralement sous la forme de crypto-monnaies comme Le Bitcoin, en échange de l’accès aux données.

Vous bénéficiez d’une protection contre les ransomwares pour les e-mails hébergés dans Microsoft 365 et pour les fichiers stockés dans OneDrive. Si vous avez Microsoft 365 Business Premium, vous bénéficiez d’une protection supplémentaire contre les ransomwares pour les appareils de votre organisation.

Vous pouvez vous protéger contre les ransomwares en créant une ou plusieurs règles de flux de courrier pour bloquer les extensions de fichier couramment utilisées pour les ransomwares, ou pour avertir les utilisateurs qui reçoivent ces pièces jointes par e-mail. Un bon point de départ consiste à créer deux règles :

- Utilisez OneDrive pour déplacer des fichiers, afin qu’ils soient toujours contrôlés par l’accès et protégés.

- Avertir les utilisateurs avant d’ouvrir des pièces jointes de fichier Office qui incluent des macros. Les ransomware peuvent être masqués à l’intérieur des macros. Nous avertirons donc les utilisateurs de ne pas ouvrir ces fichiers à partir de personnes qu’ils ne connaissent pas.

- Bloquez les types de fichiers qui peuvent contenir des ransomware ou tout autre code malveillant. Nous allons commencer par une liste commune d’exécutables (répertoriées dans le tableau ci-dessous). Si votre organisation utilise l’un de ces types exécutables et que vous vous attendez à ce qu’ils soient envoyés par e-mail, ajoutez-les à la règle précédente (avertir les utilisateurs).

Pour créer une règle de transport de courrier, consultez [Espion : Protéger contre les ransomware](increase-threat-protection.md#watch-protect-against-ransomware) ou effectuez les étapes suivantes :

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.

2. Dans la catégorie **de flux de messagerie** , sélectionnez **des règles**.

3. Sélectionnez **+**, puis **créez une règle**.

4. Sélectionnez **** en bas de la boîte de dialogue pour afficher l’ensemble complet des options.

5. Appliquez les paramètres du tableau suivant pour chaque règle. Laissez le reste des paramètres par défaut, sauf si vous souhaitez les modifier.

6. Sélectionnez **Enregistrer**.

| Setting | Avertir les utilisateurs avant d’ouvrir des pièces jointes de fichiers Office | Bloquer les types de fichiers qui peuvent contenir un ransomware ou un autre code malveillant |
|:-----|:-----|:-----|
|Nom  <br/> |Règle anti-ransomware : avertir les utilisateurs  <br/> |Règle anti-ransomware : types de fichiers de blocage  <br/> |
|Appliquez cette règle si . . .  <br/> |Toute pièce jointe . . . correspond à l’extension de fichier . . .  <br/> |Toute pièce jointe . . . correspond à l’extension de fichier . . .  <br/> |
|Spécifier des mots ou des expressions  <br/> |Ajoutez les types de fichiers suivants :  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm  <br/> |Ajoutez les types de fichiers suivants :  <br/> ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, jse, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif  <br/> |
|Procédez comme suit . . .  <br/> |Ajouter une clause d’exclusion de responsabilité  <br/> |Bloquer le message . . . rejeter le message et inclure une explication  <br/> |
|Fournir le texte du message  <br/> |N’ouvrez pas ces types de fichiers, sauf si vous les attendiez, car ils peuvent contenir du code malveillant et savoir que l’expéditeur n’est pas une garantie de sécurité.  <br/> ||

> [!TIP]
> Vous pouvez également ajouter les fichiers que vous souhaitez bloquer à la liste anti-programmes malveillants dans [Protéger contre les programmes malveillants](#protect-against-malware).

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Ransomware : comment réduire les risques](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Mieux ensemble : Antivirus Microsoft Defender et Office 365](../../security/defender-endpoint/office-365-microsoft-defender-antivirus.md)

- [Restaurer votre OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)


## <a name="protect-sensitive-emails"></a>Protéger les e-mails sensibles

Microsoft 365 inclut Le chiffrement des messages Office qui vous permet d’envoyer et de recevoir des messages électroniques chiffrés entre des personnes internes et externes à votre organisation, et seuls les destinataires prévus peuvent les afficher. Le chiffrement fonctionne avec Outlook.com, Yahoo!, Gmail et d’autres services de messagerie.

> [!Tip]
> Si un niveau de sécurité plus strict est nécessaire, votre organisation doit également configurer et utiliser l’étiquetage de confidentialité pour les e-mails ou les fichiers. [Les étiquettes de confidentialité](../../compliance/sensitivity-labels.md) permettent de contrôler le contenu, où qu’il aille.

### <a name="send-encrypted-email"></a>Envoyer un message électronique chiffré

Pour chiffrer votre e-mail :

1. Avec un nouvel e-mail ouvert, sélectionnez le menu **Options** .
1. Dans la liste **déroulante Chiffrer** , choisissez le niveau d’autorisation approprié.

:::image type="content" source="../../media/08e90a7e-a2d2-41a4-bae9-0a46b4ce639b.png" alt-text="Email chiffrement des messages dans Outlook":::

### <a name="receive-encrypted-email"></a>Recevoir un e-mail chiffré

Si le destinataire a Outlook 2013 ou Outlook 2016 et un compte de messagerie Microsoft, une alerte sur les autorisations restreintes de l’élément s’affiche dans le volet de lecture. Après avoir ouvert le message, le destinataire peut afficher le message comme n’importe quel autre.

Si le destinataire utilise un autre client de messagerie ou un autre compte de messagerie, tel que Gmail ou Yahoo, il voit un lien qui lui permet de se connecter pour lire le message électronique ou de demander un code secret unique pour afficher le message dans un navigateur web. Si les utilisateurs ne reçoivent pas l’e-mail, ils doivent vérifier leur dossier courrier indésirable ou courrier indésirable.

> [!TIP]
> Pour plus d’informations, consultez [Envoyer, afficher et répondre à des messages chiffrés dans Outlook pour PC](https://support.microsoft.com/office/eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="protect-the-organization"></a>Protéger l’organisation

Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Microsoft 365, vous pouvez configurer la protection anti-hameçonnage ciblée. La protection anti-hameçonnage est incluse dans Microsoft Defender pour Office 365 et peut aider à protéger votre organisation contre le hameçonnage basé sur l’emprunt d’identité malveillant et d’autres attaques.

> [!Note]
> Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin de le faire.

Nous vous recommandons de commencer à utiliser cette protection en créant une stratégie pour vos utilisateurs les plus importants et votre domaine personnalisé. Un bon endroit pour le faire est dans Microsoft 365 Defender, inclus avec Microsoft Business Premium. Pour créer une stratégie anti-hameçonnage dans Defender pour Office 365, effectuez les étapes suivantes :

1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a>.

2. Accédez à Email & stratégies de **collaboration** \> **& règles** \>  \> **anti-hameçonnage** dans la section **Stratégies**.

3. Dans la page Anti-hameçonnage, sélectionnez **+ Créer**. Un Assistant vous guide tout au long de la définition de votre stratégie anti-hameçonnage.

4. Spécifiez le nom, la description et les paramètres de votre stratégie, comme recommandé dans le graphique ci-dessous. Pour plus d’informations, consultez [En savoir plus sur la stratégie anti-hameçonnage dans Microsoft Defender pour Office 365 options](../../security/office-365-security/set-up-anti-phishing-policies.md).

5. Une fois que vous avez examiné vos paramètres, **sélectionnez Créer cette stratégie** ou **Enregistrer**, le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Domaine et personnel de campagne le plus précieux|
|Description|Assurez-vous que le personnel le plus important et notre domaine ne sont pas usurpés d’identité.|
|Ajouter des utilisateurs à protéger|Sélectionnez **+ Ajouter une condition, le destinataire l’est**. Tapez des noms d’utilisateur ou entrez l’adresse e-mail du candidat, du responsable de campagne et d’autres membres importants du personnel. Vous pouvez ajouter jusqu’à 20 adresses internes et externes que vous souhaitez protéger contre l’emprunt d’identité.|
|Ajouter des domaines à protéger|Sélectionnez **+ Ajouter une condition, le domaine du destinataire est**. Entrez le domaine personnalisé associé à votre abonnement Microsoft 365, si vous en avez défini un. Vous pouvez entrer plusieurs domaines.|
|Choisir des actions|Si l’e-mail est envoyé par un utilisateur emprunt d’identité : sélectionnez **Rediriger le message vers une autre adresse e-mail**, puis tapez l’adresse e-mail de l’administrateur de sécurité; par exemple, securityadmin@contoso.com. <br/> Si l’e-mail est envoyé par un domaine emprunt d’identité : sélectionnez **Message de quarantaine**.|
|Veille des boîtes aux lettres|Par défaut, la veille des boîtes aux lettres est activée lorsque vous créez une stratégie anti-hameçonnage. Laissez ce paramètre **activé** pour obtenir de meilleurs résultats.|
|Ajouter des expéditeurs et domaines de confiance|Pour cet exemple, ne définissez pas de remplacement.|
|Appliqué à|Sélectionnez **Le domaine du destinataire est**. Sous **Un de ces éléments**, sélectionnez **Choisir**. Sélectionnez **+ Ajouter**. Cochez la case en regard du nom du domaine, par exemple, contoso.com, dans la liste, puis **sélectionnez Ajouter**. Sélectionnez **Terminé**.|

> [!TIP]
> Pour plus d’informations, consultez Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

## <a name="protect-against-malicious-attachments-files-and-urls"></a>Protéger contre les pièces jointes, fichiers et URL malveillants

Les personnes envoient, reçoivent et partagent régulièrement des pièces jointes, telles que des documents, des présentations, des feuilles de calcul, etc. Il n’est pas toujours facile de savoir si une pièce jointe est sécurisée ou malveillante simplement en examinant un message électronique. Microsoft Defender pour Office 365 inclut la protection des pièces jointes sécurisées, mais cette protection n’est pas activée par défaut. Nous vous recommandons de créer une règle pour commencer à utiliser cette protection. Cette protection s’étend aux fichiers dans SharePoint, OneDrive et Microsoft Teams.

### <a name="set-up-safe-attachments"></a>Configurer des pièces jointes sécurisées

Vous pouvez utiliser des stratégies de pièces jointes sécurisées prédéfines ou créer les vôtres. Pour créer une stratégie pièces jointes sécurisées, affichez une [courte vidéo de formation](increase-threat-protection.md) ou effectuez les étapes suivantes :

1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a> et connectez-vous avec votre compte d’administrateur.

2. Accédez à Email & stratégies de **collaboration** \> **& règles** \> **Anti-programme**  \> malveillant dans la section **Stratégies**.

3. Sélectionnez **+ Créer** pour créer une stratégie.

4. Appliquez les paramètres dans le tableau suivant.

5. Une fois que vous avez examiné vos paramètres, **sélectionnez Créer cette stratégie** ou **Enregistrer**, le cas échéant.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Bloquez les e-mails actuels et futurs avec les programmes malveillants détectés.|
|Description|Bloquez les courriers électroniques et pièces jointes actuels et futurs avec des programmes malveillants détectés.|
|Enregistrer les pièces jointes réponse de programmes malveillants inconnus|Sélectionnez **Bloquer : bloquez les e-mails et pièces jointes actuels et futurs avec les programmes malveillants détectés**.|
|Redirection d’une pièce jointe lors de la détection|Activer la redirection (sélectionnez cette zone) <br/> Entrez le compte d’administrateur ou une configuration de boîte aux lettres pour la mise en quarantaine. <br/> Appliquez la sélection ci-dessus si l’analyse des programmes malveillants pour les pièces jointes expire ou si une erreur se produit (sélectionnez cette zone).|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|

> [!TIP]
> Pour plus d’informations, consultez Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

### <a name="set-up-safe-links"></a>Configurer des liens fiables

Les pirates informatiques masquent parfois des sites web malveillants dans des liens dans des e-mails ou d’autres fichiers. Les liens fiables, qui font partie de Microsoft Defender pour Office 365, peuvent aider à protéger votre organisation en fournissant la vérification au moment du clic des adresses web (URL) dans les e-mails et les documents Office. La protection est définie par le biais de stratégies de liaisons sécurisées.

Procédez comme suit pour vous protéger contre les attaques :

- Modifiez la stratégie par défaut pour augmenter la protection.

- Ajoutez une nouvelle stratégie destinée à tous les destinataires de votre domaine.

Pour accéder à Liens sécurisés, consultez [Espion : Protégez votre courrier contre les attaques par hameçonnage](increase-threat-protection.md#watch-protect-your-email-from-phishing-attacks), ou effectuez les étapes suivantes :

1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a> et connectez-vous avec votre compte d’administrateur.

2. Accédez à Email & stratégies de **collaboration** \> **& règles** \> **Anti-programme**  \> malveillant dans la section **Stratégies**.

3. Sélectionnez **+ Créer** pour créer une stratégie ou modifiez la stratégie par défaut.

Pour modifier la stratégie par défaut :

1. Double-cliquez sur la stratégie **par défaut** . Un menu volant s’affiche. 

2. Sélectionnez **Modifier les paramètres de protection** en bas du menu volant.

3. Après avoir modifié la stratégie par défaut, **sélectionnez Enregistrer**.

|Paramètre ou option|Valeur recommandée|
|---|---|
|Nom|Stratégie de liens sécurisés pour tous les destinataires du domaine|
|Sélectionnez l’action pour les URL potentiellement malveillantes inconnues dans les messages|Sélectionnez **Activé : les URL sont réécrites et vérifiées par rapport à une liste de liens malveillants connus lorsque l’utilisateur clique sur le lien**.|
|Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers|Sélectionnez cette zone.|
|Appliqué à|Le domaine du destinataire est . . . sélectionnez votre domaine.|

> [!TIP]
> Pour plus d’informations, consultez [Liens sécurisés dans Microsoft Defender pour Office 365](../../security/office-365-security/atp-safe-links.md).

## <a name="increase-protection-for-your-organizations-devices"></a>Augmenter la protection des appareils de votre organisation

L’antivirus Microsoft Defender est intégré au système d’exploitation Windows et offre une bonne protection contre les virus et les programmes malveillants. Toutefois, vous pouvez renforcer la protection des appareils de votre organisation en les intégrant à Microsoft Defender pour entreprises qui est une nouvelle offre pour les petites et moyennes entreprises comme la vôtre, et qui est incluse dans [Microsoft 365 Business Premium](../../business-premium/index.md). Avec Defender entreprise, les appareils de votre organisation sont mieux protégés contre les ransomware, les programmes malveillants, le hameçonnage et d’autres menaces.

Avec Microsoft 365 Business Premium vous bénéficiez de fonctionnalités de sécurité renforcées telles que la gestion des appareils et la protection avancée contre les menaces. Lorsque vous inscrivez des appareils dans Microsoft 365 Business pour Defender, les appareils sont surveillés et protégés par InTune.


Pour en savoir plus, consultez les ressources suivantes :

- [Vue d’ensemble de Microsoft Defender pour entreprises](../../security/defender-business/mdb-overview.md)

- [Configurer et configurer Microsoft Defender pour entreprises](../../security/defender-business/mdb-setup-configuration.md)

- [Prise en main du portail Microsoft 365 Defender](../../security/defender-business/mdb-get-started.md)

## <a name="related-content"></a>Contenu associé

[Authentification multifacteur pour Microsoft 365](multi-factor-authentication-microsoft-365.md) (article)\
[Gérer et surveiller les comptes prioritaires](../setup/priority-accounts.md) (article)\
[Rapports Microsoft 365 dans le centre d’administration](../activity-reports/activity-reports.md) (vidéo)\
[Microsoft 365 Business Premium — cybersécurité pour les petites entreprises](/microsoft-365/business-premium/) (article)\

