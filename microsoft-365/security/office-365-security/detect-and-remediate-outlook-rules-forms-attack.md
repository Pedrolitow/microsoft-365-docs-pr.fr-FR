---
title: Détectez et remédiez aux Outlook et aux attaques par injection de formulaires personnalisés.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
ms.date: 04/23/2018
audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- M365-security-compliance
localization_priority: Normal
search.appverid:
- MET150
description: Découvrez comment reconnaître et corriger les règles de Outlook et les attaques par injections de formulaires personnalisés dans Office 365
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0846051b65b34ec26358f87bb4ca49302573e6e7
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59163528"
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks"></a>Détecter et corriger les Outlook et les attaques par injection de formulaires personnalisés

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


**Résumé** Découvrez comment reconnaître et corriger les règles de Outlook et les attaques par injections de formulaires personnalisées dans Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Qu’est-ce que l Outlook d’injection de formulaires personnalisés et de règles de sécurité ?

Une fois qu’un attaquant a accédé à votre organisation, il essaiera d’établir un point d’accès pour rester dans votre organisation ou y revenir une fois qu’il a été détecté. Cette activité est appelée *établissement d’un mécanisme de persistance.* Une personne malveillante peut utiliser deux méthodes Outlook pour établir un mécanisme de persistance :

- En exploitant Outlook règles.
- En injectant des formulaires personnalisés dans Outlook.

Réinstaller Outlook, ou même donner à la personne concernée un nouvel ordinateur ne vous aidera pas. Lorsque la nouvelle installation de Outlook se connecte à la boîte aux lettres, toutes les règles et tous les formulaires sont synchronisés à partir du cloud. Les règles ou les formulaires sont généralement conçus pour exécuter du code à distance et installer des programmes malveillants sur l’ordinateur local. Le programme malveillant volera les informations d’identification ou effectuera d’autres activités illicites.

La bonne nouvelle est que si vous conservez vos clients Outlook corrigés sur la dernière version, vous n’êtes pas vulnérable à la menace, car les valeurs par défaut du client Outlook bloquent les deux mécanismes.

Les attaques suivent généralement les modèles ci-après :

**L’exploit des règles**:

1. L’attaquant volera les informations d’identification d’un utilisateur.

2. L’attaquant se permet de se Exchange boîte aux lettres de l’utilisateur (Exchange Online ou local Exchange).

3. L’attaquant crée une règle de boîte de réception de forwarding dans la boîte aux lettres. La règle de forwarding est déclenchée lorsque la boîte aux lettres reçoit un message spécifique de l’attaquant qui correspond aux conditions de la règle. Les conditions de règle et le format des messages sont personnalisés les uns pour les autres.

4. L’attaquant envoie le message électronique de déclencheur à la boîte aux lettres compromise, qui est toujours utilisée normalement par l’utilisateur qui ne s’en doute pas.

5. Lorsque la boîte aux lettres reçoit un message qui correspond aux conditions de règle, l’action de la règle est appliquée. En règle générale, l’action de la règle consiste à lancer une application sur un serveur distant (WebDAV).

6. En règle générale, l’application installe un programme malveillant sur l’ordinateur de l’utilisateur (par exemple, [PowerShell Dernier](https://www.powershellempire.com/)).

7. Le programme malveillant permet à l’attaquant de voler (ou de voler à nouveau) le nom d’utilisateur et le mot de passe de l’utilisateur ou d’autres informations d’identification de l’ordinateur local et d’effectuer d’autres activités malveillantes.

**L’exploit de formulaires**:

1. L’attaquant volera les informations d’identification d’un utilisateur.

2. L’attaquant se permet de se Exchange boîte aux lettres de l’utilisateur (Exchange Online ou local Exchange).

3. L’attaquant insère un modèle de formulaire de courrier personnalisé dans la boîte aux lettres de l’utilisateur. Le formulaire personnalisé est déclenché lorsque la boîte aux lettres reçoit un message spécifique de l’attaquant qui exige que la boîte aux lettres charge le formulaire personnalisé. Le formulaire personnalisé et le format de message sont personnalisés les uns pour les autres.

4. L’attaquant envoie le message électronique de déclencheur à la boîte aux lettres compromise, qui est toujours utilisée normalement par l’utilisateur qui ne s’en doute pas.

5. Lorsque la boîte aux lettres reçoit le message, elle charge le formulaire requis. Le formulaire lance une application sur un serveur distant (WebDAV).

6. En règle générale, l’application installe un programme malveillant sur l’ordinateur de l’utilisateur (par exemple, [PowerShell Dernier](https://www.powershellempire.com/)).

7. Le programme malveillant permet à l’attaquant de voler (ou de voler à nouveau) le nom d’utilisateur et le mot de passe de l’utilisateur ou d’autres informations d’identification de l’ordinateur local et d’effectuer d’autres activités malveillantes.

## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>À quoi pourrait ressembler une attaque par injection de règles et de formulaires personnalisés Office 365 ?

Ces mécanismes de persistance sont peu susceptibles d’être remarqués par vos utilisateurs et peuvent même, dans certains cas, leur être invisibles. Cet article vous indique comment rechercher l’un des sept signes (Indicateurs de compromis) répertoriés ci-dessous. Si vous trouvez l’un de ces éléments, vous devez prendre des mesures correctives.

- **Indicateurs de compromission des règles**:
  - L’action de la règle consiste à démarrer une application.
  - La règle fait référence à un FICHIER EXE, ZIP ou URL.
  - Sur l’ordinateur local, recherchez les nouveaux processus qui proviennent du piD Outlook de l’ordinateur local.

- **Indicateurs de compromission des formulaires personnalisés**:
  - Les formulaires personnalisés présents sont enregistrés en tant que classe de message.
  - La classe de message contient du code exécutable.
  - En règle générale, les formulaires malveillants sont stockés dans des dossiers de la bibliothèque de formulaires personnels ou de la boîte de réception.
  - Le formulaire est nommé IPM. Remarque. [nom personnalisé].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Étapes de recherche et de confirmation de cette attaque

Vous pouvez utiliser l’une des méthodes suivantes pour confirmer l’attaque :

- Examinez manuellement les règles et les formulaires de chaque boîte aux lettres à l’aide Outlook client. Cette méthode est minutieuse, mais vous ne pouvez vérifier qu’une seule boîte aux lettres à la fois. Cette méthode peut prendre beaucoup de temps si vous avez de nombreux utilisateurs à vérifier et peut également infecter l’ordinateur que vous utilisez.

- Utilisez le script [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell pour vider automatiquement toutes les règles de forwarding de courrier et les formulaires personnalisés pour tous les utilisateurs de votre location. Il s’agit de la méthode la plus rapide et la plus sûre avec la charge de traitement la moins importante.

### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Confirmer l’attaque par règles à l’aide Outlook client

1. Ouvrez les utilisateurs Outlook client en tant qu’utilisateur. L’utilisateur peut avoir besoin de votre aide pour examiner les règles de sa boîte aux lettres.

2. [Reportez-vous à l’article](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) Gérer les messages électroniques à l’aide de l’article règles pour les procédures d’ouverture de l’interface de règles dans Outlook.

3. Recherchez les règles que l’utilisateur n’a pas créés, ou les règles ou règles inattendues avec des noms suspects.

4. Dans la description de la règle, recherchez les actions de règle qui démarrent et s’applicationnt ou qui font référence à un fichier .EXE, .ZIP ou au lancement d’une URL.

5. Recherchez les nouveaux processus qui commencent à utiliser l’ID Outlook processus. [Reportez-vous à Rechercher l’ID de processus.](/windows-hardware/drivers/debugger/finding-the-process-id)

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Étapes de confirmation de l’attaque par formulaires à l’aide Outlook client

1. Ouvrez le client Outlook utilisateur en tant qu’utilisateur.

2. Suivez les étapes de la procédure [, Afficher l’onglet](https://support.microsoft.com/office/e1192344-5e56-4d45-931b-e5fd9bea2d45) Développeur pour la version d’Outlook.

3. Ouvrez l’onglet développeur désormais visible dans Outlook puis cliquez **sur Concevoir un formulaire.**

4. Sélectionnez **la boîte de réception** dans la liste **Rechercher** dans. Recherchez les formulaires personnalisés. Les formulaires personnalisés sont suffisamment rares pour que si vous avez des formulaires personnalisés, cela vaut la peine d’avoir une apparence plus approfondie.

5. Examinez tous les formulaires personnalisés, en particulier ceux marqués comme masqués.

6. Ouvrez tous les formulaires personnalisés et, dans le groupe **Formulaire,** cliquez sur Afficher le **code** pour voir ce qui s’exécute lorsque le formulaire est chargé.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>Étapes de confirmation de l’attaque par règles et formulaires à l’aide de PowerShell

Le moyen le plus simple de vérifier une attaque par des règles ou des formulaires personnalisés consiste à exécuter [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) script PowerShell. Ce script se connecte à chaque boîte aux lettres de votre client et vide toutes les règles et formulaires dans deux .csv.

#### <a name="pre-requisites"></a>Conditions préalables

Vous devez avoir des droits d’administrateur général pour exécuter le script, car il se connecte à chaque boîte aux lettres de la location pour lire les règles et les formulaires.

1. Connectez-vous à l’ordinateur à partir de qui vous exécuterez le script avec des droits d’administrateur local.

2. Téléchargez ou copiez Get-AllTenantRulesAndForms.ps1 script de GitHub vers un dossier à partir duquel vous l’exécuterez. Le script crée deux fichiers horodatés dans ce dossier, MailboxFormsExport-yyyy-mm-dd.csv et MailboxRulesExport-yyyy-mm-dd.csv.

3. Ouvrez une instance PowerShell en tant qu’administrateur et ouvrez le dossier dans qui vous avez enregistré le script.

4. Exécutez cette ligne de commande PowerShell comme `.\Get-AllTenantRulesAndForms.ps1` suit.\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Interprétation de la sortie

- **MailboxRulesExport-*yyyy-mm-dd*.csv**: examinez les règles (une par ligne) pour les conditions d’action qui incluent des applications ou des exécutables :

  - **ActionType (colonne A)**: si vous voyez la valeur « ID_ACTION_CUSTOM », la règle est probablement malveillante.

  - **IsPotentiallyMalicious (colonne D)**: si cette valeur est « TRUE », la règle est probablement malveillante.

  - **ActionCommand (colonne G)**: si cette colonne répertorie une application ou un fichier avec des extensions .exe ou .zip, ou une entrée inconnue qui fait référence à une URL, la règle est probablement malveillante.

- **MailboxFormsExport-*yyyy-mm-dd*.csv**: en règle générale, l’utilisation de formulaires personnalisés est rare. Si vous en trouvez dans ce workbook, vous ouvrez la boîte aux lettres de cet utilisateur et examinez le formulaire lui-même. Si votre organisation ne l’a pas placé intentionnellement, il est probablement malveillant.

## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Comment arrêter et corriger les attaques Outlook règles et formulaires

Si vous trouvez des preuves de l’une de ces attaques, la correction est simple, supprimez simplement la règle ou le formulaire de la boîte aux lettres. Vous pouvez le faire avec le client Outlook ou à l’aide de PowerShell à distance pour supprimer des règles.

### <a name="using-outlook"></a>Utilisation de Outlook

1. Identifiez tous les appareils que l’utilisateur a utilisés avec Outlook. Ils devront tous être nettoyés des programmes malveillants potentiels. N’autorisez pas l’utilisateur à se connecter et à utiliser le courrier tant que tous les appareils n’ont pas été nettoyés.

2. Suivez les étapes de [la procédure de suppression d’une règle](https://support.microsoft.com/office/2f0e7139-f696-4422-8498-44846db9067f) pour chaque appareil.

3. Si vous n’êtes pas sûr de la présence d’autres programmes malveillants, vous pouvez formater et réinstaller tous les logiciels sur l’appareil. Pour les appareils mobiles, vous pouvez suivre les étapes des fabricants pour réinitialiser l’appareil à l’image d’usine.

4. Installez les versions les plus récentes de Outlook. N’oubliez pas que la version actuelle de Outlook bloque les deux types d’attaque par défaut.

5. Une fois toutes les copies hors connexion de la boîte aux lettres supprimées, réinitialisez le mot de passe de l’utilisateur (utilisez une copie de haute qualité) et suivez les étapes de l’authentification [multifacteur](../../admin/security-and-compliance/set-up-multi-factor-authentication.md) du programme d’installation pour les utilisateurs si l’authentification multifacteur n’a pas encore été activée. Cela garantit que les informations d’identification de l’utilisateur ne sont pas exposées par d’autres moyens (par exemple, hameçonnage ou nouvelle utilisation du mot de passe).

### <a name="using-powershell"></a>Utiliser PowerShell

Il existe deux cmdlets PowerShell distantes que vous pouvez utiliser pour supprimer ou désactiver des règles dangereuses. Suivez simplement les étapes.

#### <a name="steps-for-mailboxes-that-are-on-an-exchange-server"></a>Étapes pour les boîtes aux lettres qui se sont sur un Exchange serveur

1. Connecter au serveur Exchange à l’aide de PowerShell distant. Suivez les étapes de [la Connecter pour Exchange à l’aide de PowerShell à distance.](/powershell/exchange/connect-to-exchange-servers-using-remote-powershell)

2. Si vous souhaitez supprimer complètement une règle unique, plusieurs règles ou toutes les règles d’une boîte aux lettres, utilisez la cmdlet [Remove-InboxRule.](/powershell/module/exchange/Remove-InboxRule)

3. Si vous souhaitez conserver la règle et son contenu pour un examen plus approfondie, utilisez la cmdlet [Disable-InboxRule.](/powershell/module/exchange/disable-inboxrule)

#### <a name="steps-for-mailboxes-in-exchange-online"></a>Étapes pour les boîtes aux lettres dans Exchange Online

1. Suivez les étapes de [la Connecter pour Exchange Online à l’aide de PowerShell.](/powershell/exchange/connect-to-exchange-online-powershell)

2. Si vous souhaitez supprimer complètement une règle unique, plusieurs règles ou toutes les règles d’une boîte aux lettres, utilisez la cmdlet [Remove-Inbox Rule.](/powershell/module/exchange/Remove-InboxRule)

3. Si vous souhaitez conserver la règle et son contenu pour un examen plus approfondie, utilisez la cmdlet [Disable-InboxRule.](/powershell/module/exchange/disable-inboxrule)

## <a name="how-to-minimize-future-attacks"></a>Comment réduire les attaques futures

### <a name="first-protect-your-accounts"></a>Tout d’abord : protéger vos comptes

Les attaques par règles et formulaires sont utilisées uniquement par un attaquant après le vol ou la violation de l’un des comptes de votre utilisateur. Par conséquent, la première étape pour empêcher l’utilisation de ces attaques contre votre organisation consiste à protéger de manière agressive vos comptes d’utilisateurs. Certaines des façons les plus courantes d’enfreiner les comptes sont par le biais d’attaques par hameçonnage ou par pulvérisation [de mots de passe.](https://www.microsoft.com/security/blog/2020/04/23/protecting-organization-password-spray-attacks/)

La meilleure façon de protéger vos comptes d’utilisateur, et en particulier vos comptes d’administrateur, consiste à configurer l’authentification [multifacteur pour les utilisateurs.](../../admin/security-and-compliance/set-up-multi-factor-authentication.md) Vous devez également :

- Surveillez l’accès et l’utilisation de [vos comptes d’utilisateur.](/azure/active-directory/active-directory-view-access-usage-reports) Vous n’empêcherez peut-être pas la violation initiale, mais vous raccourcirez la durée et l’impact de la violation en la détectant plus rapidement. Vous pouvez utiliser ces [stratégies Sécurité des applications cloud Office 365 pour](/cloud-app-security/what-is-cloud-app-security) surveiller vos comptes et alerter sur les activités inhabituelles :

  - **Plusieurs tentatives** de connexion ayant échoué : cette stratégie profile votre environnement et déclenche des alertes lorsque les utilisateurs effectuent plusieurs activités de connexion ayant échoué en une seule session par rapport à la ligne de base acquise, ce qui peut indiquer une tentative de violation.

  - **Voyage impossible**: cette stratégie profile votre environnement et déclenche des alertes lorsque des activités sont détectées par le même utilisateur à différents emplacements dans une période plus courte que le temps de déplacement prévu entre les deux emplacements. Cela peut indiquer qu’un autre utilisateur utilise les mêmes informations d’identification. La détection de ce comportement anormal nécessite une période d’apprentissage initiale de sept jours au cours de laquelle elle apprend le modèle d’activité d’un nouvel utilisateur.

  - Activité d’emprunt d’identité inhabituelle **(par utilisateur)**: cette stratégie profile votre environnement et déclenche des alertes lorsque les utilisateurs effectuent plusieurs activités usurpées d’identité dans une seule session par rapport à la ligne de base acquise, ce qui peut indiquer une tentative de violation.

- Utilisez un outil tel que [Office 365 Secure Score](https://securescore.office.com/) pour gérer les configurations et comportements de sécurité des comptes.

### <a name="second-keep-your-outlook-clients-current"></a>Deuxième : maintenez vos clients Outlook jour

Les versions entièrement mises à jour et mises à jour de Outlook 2013 et 2016 désactivent l’action de formulaire/règle « Démarrer l’application » par défaut. Cela garantit que même si un attaquant enfreint le compte, les actions de règle et de formulaire seront bloquées. Vous pouvez installer les dernières mises à jour et correctifs de sécurité en suivant les étapes de [l’Office mises à jour.](https://support.microsoft.com/office/2ab296f3-7f03-43a2-8e50-46de917611c5)

Voici les versions des correctifs pour Outlook clients 2013 et 2016 :

- **Outlook 2016**: 16.0.4534.1001 ou supérieur.

- **Outlook 2013**: 15.0.4937.1000 ou supérieur.

Pour plus d’informations sur les correctifs de sécurité individuels, voir :

- [Outlook 2016 Correctif de sécurité](https://support.microsoft.com/help/3191883)

- [Outlook 2013 Security Patch](https://support.microsoft.com/help/3191938)

### <a name="third-monitor-your-outlook-clients"></a>Troisième : surveiller vos clients Outlook client

Notez que même avec les correctifs et mises à jour installés, il est possible pour un attaquant de modifier la configuration de l’ordinateur local afin de ré-activer le comportement « Démarrer l’application ». Vous pouvez utiliser la [gestion avancée des stratégies de](/microsoft-desktop-optimization-pack/agpm/) groupe pour surveiller et appliquer des stratégies d’ordinateur local sur vos clients.

Vous pouvez voir si « Démarrer l’application » a été ré-activé via une substitution dans le Registre à l’aide des informations de la procédure d’affichage du Registre système à l’aide de [versions 64 bits](https://support.microsoft.com/help/305097)de Windows . Vérifiez les sous-clés ci-après :

- **Outlook 2016**:`HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\`

- **Outlook 2013**:`HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\`

Recherchez la clé EnableUnsafeClientMailRules. S’il est là et est définie sur 1, le correctif de sécurité Outlook a été mis en place et l’ordinateur est vulnérable à l’attaque par formulaire/règles. Si la valeur est 0, l’action « Démarrer l’application » est désactivée. Si la version mise à jour et corrigé de Outlook est installée et que cette clé de Registre n’est pas présente, un système n’est pas vulnérable à ces attaques.

Les clients qui disposent d’installations Exchange sur site doivent envisager de bloquer les versions antérieures de Outlook qui ne disposent pas de correctifs. Pour plus d’informations sur ce processus, voir l’article [Configure Outlook client blocking](/exchange/configure-outlook-client-blocking-exchange-2013-help).

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Sécuriser Microsoft 365 comme un pro de la cyber-sécurité

Votre abonnement Microsoft 365 inclut un ensemble puissant de fonctionnalités de sécurité que vous pouvez utiliser pour protéger vos données et vos utilisateurs. Utilisez la [Feuille de route du Centre de sécurité Microsoft 365 : principales priorités pour les 30 premiers jours, 90 premiers jours et au-delà](security-roadmap.md), pour implémenter les meilleures pratiques recommandées par Microsoft pour sécuriser votre client Microsoft 365.

- Tâches à effectuer lors des 30 premiers jours. Celles-ci ont un effet immédiat et ont un faible impact sur vos utilisateurs.

- Tâches à accomplir en 90 jours. Celles-ci prennent un peu plus de temps à planifier et à implémenter, mais améliorent considérablement votre posture de sécurité.

- Au-delà de 90 jours. Ces améliorations s’appuient sur vos 90 premiers jours de travail.

## <a name="see-also"></a>Voir aussi :

- [Le message Outlook de](https://silentbreaksecurity.com/malicious-outlook-rules/) sécurité SilentBreak sur le vecteur de règles fournit un examen détaillé de la façon dont les règles Outlook malveillantes.

- [MAPI sur HTTP et Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) sur le blog Sensepost sur Mailrule Pwnage traite d’un outil appelé Ruler qui vous permet d’exploiter des boîtes aux lettres par Outlook règles.

- [Outlook formulaires et shells](https://sensepost.com/blog/2017/outlook-forms-and-shells/) sur le blog Sensepost sur le vecteur de menace de formulaires.

- [Ruler Codebase](https://github.com/sensepost/ruler)

- [Indicateurs de règle de compromis](https://github.com/sensepost/notruler/blob/master/iocs.md)