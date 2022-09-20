---
title: Détecter et corriger les règles Outlook et les attaques par injection de formulaires personnalisés.
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
ms.localizationpriority: medium
search.appverid:
- MET150
description: Découvrez comment reconnaître et corriger les règles Outlook et les attaques par injection de formulaires personnalisés dans Office 365
ms.custom: seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 55ecde2b4ded073e53b27abb72ebe22e25006c1b
ms.sourcegitcommit: 95ac076310ab9006ed92c69938f7ae771cd10826
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67850148"
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks"></a>Détecter et corriger les règles Outlook et les attaques par injection de formulaires personnalisés

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Résumé** Découvrez comment reconnaître et corriger les règles Outlook et les attaques d’injections de formulaires personnalisés dans Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Qu’est-ce que les règles Outlook et l’attaque par injection de formulaires personnalisés ?

Une fois qu’un attaquant a accès à votre organisation, il essaiera d’établir un pied de page pour rester ou revenir une fois qu’il aura été découvert. Cette activité est appelée *établissement d’un mécanisme de persistance*. Il existe deux façons pour un attaquant d’utiliser Outlook pour établir un mécanisme de persistance :

- En exploitant les règles Outlook.
- En injectant des formulaires personnalisés dans Outlook.

La réinstallation d’Outlook ou même l’attribution d’un nouvel ordinateur à la personne concernée n’aideront pas. Lorsque la nouvelle installation d’Outlook se connecte à la boîte aux lettres, toutes les règles et formulaires sont synchronisés à partir du cloud. Les règles ou formulaires sont généralement conçus pour exécuter du code distant et installer des programmes malveillants sur l’ordinateur local. Le programme malveillant vole des informations d’identification ou effectue d’autres activités illicites.

La bonne nouvelle est que si vous conservez vos clients Outlook corrigés à la dernière version, vous n’êtes pas vulnérable à la menace, car les valeurs par défaut actuelles du client Outlook bloquent les deux mécanismes.

Les attaques suivent généralement les modèles suivants :

**L’exploit des règles** :

1. L’attaquant vole les informations d’identification d’un utilisateur.

2. L’attaquant se connecte à la boîte aux lettres Exchange de cet utilisateur (Exchange Online ou Exchange local).

3. L’attaquant crée une règle de boîte de réception de transfert dans la boîte aux lettres. La règle de transfert est déclenchée lorsque la boîte aux lettres reçoit un message spécifique de l’attaquant qui correspond aux conditions de la règle. Les conditions de règle et le format de message sont personnalisés les uns pour les autres.

4. L’attaquant envoie l’e-mail du déclencheur à la boîte aux lettres compromise, qui est toujours utilisée comme d’habitude par l’utilisateur peu averti.

5. Lorsque la boîte aux lettres reçoit un message qui correspond aux conditions de la règle, l’action de la règle est appliquée. En règle générale, l’action de règle consiste à lancer une application sur un serveur distant (WebDAV).

6. En règle générale, l’application installe des programmes malveillants sur l’ordinateur de l’utilisateur (par exemple, [PowerShell Empire](https://www.powershellempire.com/)).

7. Le programme malveillant permet à l’attaquant de voler (ou de voler à nouveau) le nom d’utilisateur et le mot de passe de l’utilisateur ou d’autres informations d’identification de l’ordinateur local et d’effectuer d’autres activités malveillantes.

**L’exploit des formes** :

1. L’attaquant vole les informations d’identification d’un utilisateur.

2. L’attaquant se connecte à la boîte aux lettres Exchange de cet utilisateur (Exchange Online ou Exchange local).

3. L’attaquant insère un modèle de formulaire de messagerie personnalisé dans la boîte aux lettres de l’utilisateur. Le formulaire personnalisé est déclenché lorsque la boîte aux lettres reçoit un message spécifique de l’attaquant qui exige que la boîte aux lettres charge le formulaire personnalisé. Le formulaire personnalisé et le format de message sont personnalisés les uns pour les autres.

4. L’attaquant envoie l’e-mail du déclencheur à la boîte aux lettres compromise, qui est toujours utilisée comme d’habitude par l’utilisateur peu averti.

5. Lorsque la boîte aux lettres reçoit le message, la boîte aux lettres charge le formulaire requis. Le formulaire lance une application sur un serveur distant (WebDAV).

6. En règle générale, l’application installe des programmes malveillants sur l’ordinateur de l’utilisateur (par exemple, [PowerShell Empire](https://www.powershellempire.com/)).

7. Le programme malveillant permet à l’attaquant de voler (ou de voler à nouveau) le nom d’utilisateur et le mot de passe de l’utilisateur ou d’autres informations d’identification de l’ordinateur local et d’effectuer d’autres activités malveillantes.

## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>À quoi peut ressembler une attaque par injection de règles et de formulaires personnalisés Office 365 ?

Ces mécanismes de persistance sont peu susceptibles d’être remarqués par vos utilisateurs et peuvent même, dans certains cas, être invisibles pour eux. Cet article vous explique comment rechercher l’un des sept signes (Indicateurs de compromission) répertoriés ci-dessous. Si vous trouvez l’un de ces éléments, vous devez effectuer des étapes de correction.

- **Indicateurs de la compromission des règles** :
  - L’action de règle consiste à démarrer une application.
  - La règle fait référence à un FICHIER EXE, zip ou URL.
  - Sur l’ordinateur local, recherchez les nouveaux démarrages de processus qui proviennent du PID Outlook.

- **Indicateurs de compromission des formulaires personnalisés** :
  - Les formulaires personnalisés présents sont enregistrés comme leur propre classe de message.
  - La classe message contient du code exécutable.
  - En règle générale, les formulaires malveillants sont stockés dans des dossiers de bibliothèque de formulaires personnels ou de boîte de réception.
  - Le formulaire est nommé IPM. Note. [nom personnalisé].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Étapes permettant de trouver des signes de cette attaque et de la confirmer

Vous pouvez utiliser l’une des méthodes suivantes pour confirmer l’attaque :

- Examinez manuellement les règles et formulaires de chaque boîte aux lettres à l’aide du client Outlook. Cette méthode est complète, mais vous ne pouvez vérifier qu’une seule boîte aux lettres à la fois. Cette méthode peut prendre beaucoup de temps si vous avez de nombreux utilisateurs à vérifier, et peut également infecter l’ordinateur que vous utilisez.

- Utilisez le [ script ](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShellGet-AllTenantRulesAndForms.ps1pour vider automatiquement toutes les règles de transfert de courrier et les formulaires personnalisés pour tous les utilisateurs de votre location. Il s’agit de la méthode la plus rapide et la plus sûre avec le moins de surcharge.

### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Confirmer l’attaque par règles à l’aide du client Outlook

1. Ouvrez le client Outlook des utilisateurs en tant qu’utilisateur. L’utilisateur peut avoir besoin de votre aide pour examiner les règles de sa boîte aux lettres.

2. Reportez-vous à [l’article Gérer les messages électroniques à l’aide de l’article de règles](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) pour connaître les procédures permettant d’ouvrir l’interface de règles dans Outlook.

3. Recherchez les règles que l’utilisateur n’a pas créées, ou les règles inattendues ou les règles avec des noms suspects.

4. Recherchez dans la description de règle les actions de règle qui démarrent et l’application, ou font référence à un .EXE, à un fichier .ZIP ou au lancement d’une URL.

5. Recherchez les nouveaux processus qui commencent à utiliser l’ID de processus Outlook. Reportez-vous à [Rechercher l’ID de processus](/windows-hardware/drivers/debugger/finding-the-process-id).

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Étapes de confirmation de l’attaque par formulaires à l’aide du client Outlook

1. Ouvrez le client Outlook de l’utilisateur en tant qu’utilisateur.

2. Suivez les étapes ci-dessous, [afficher l’onglet Développeur](https://support.microsoft.com/office/e1192344-5e56-4d45-931b-e5fd9bea2d45) pour la version d’Outlook de l’utilisateur.

3. Ouvrez l’onglet développeur maintenant visible dans Outlook, puis cliquez sur **concevoir un formulaire**.

4. Sélectionnez la **boîte de réception dans** la liste **Regarder dans** . Recherchez des formulaires personnalisés. Les formulaires personnalisés sont assez rares pour que si vous avez des formulaires personnalisés, il vaut la peine d’un examen plus approfondi.

5. Examinez les formulaires personnalisés, en particulier ceux marqués comme masqués.

6. Ouvrez les formulaires personnalisés et, dans le groupe **Formulaire** , cliquez sur **Afficher le code** pour voir ce qui s’exécute lorsque le formulaire est chargé.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>Étapes de confirmation de l’attaque par règles et formulaires à l’aide de PowerShell

Le moyen le plus simple de vérifier une attaque de règles ou de formulaires personnalisés consiste à exécuter le script PowerShell [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) . Ce script se connecte à chaque boîte aux lettres de votre locataire et vide toutes les règles et formulaires dans deux fichiers .csv.

#### <a name="pre-requisites"></a>Conditions préalables

Vous devez disposer de droits d’administrateur général pour exécuter le script, car le script se connecte à chaque boîte aux lettres de la location pour lire les règles et les formulaires.

1. Connectez-vous à la machine à partir de laquelle vous allez exécuter le script avec des droits d’administrateur local.

2. Téléchargez ou copiez le script Get-AllTenantRulesAndForms.ps1 à partir de GitHub dans un dossier à partir duquel vous l’exécuterez. Le script crée deux fichiers horodatés de date dans ce dossier, MailboxFormsExport-yyyy-mm-dd.csv et MailboxRulesExport-yyyy-mm-dd.csv.

3. Ouvrez une instance PowerShell en tant qu’administrateur et ouvrez le dossier dans lequel vous avez enregistré le script.

4. Exécutez cette ligne de commande PowerShell comme suit `.\Get-AllTenantRulesAndForms.ps1`: .\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Interprétation de la sortie

- ***MailboxRulesExport-yyyy-mm-dd*.csv**: examinez les règles (une par ligne) pour les conditions d’action qui incluent des applications ou des exécutables :

  - **ActionType (colonne A)** : si vous voyez la valeur « ID_ACTION_CUSTOM », la règle est probablement malveillante.

  - **IsPotentiallyMalicious (colonne D)** : si cette valeur est « TRUE », la règle est probablement malveillante.

  - **ActionCommand (colonne G)** : si cette colonne répertorie une application ou un fichier avec des extensions .exe ou .zip, ou une entrée inconnue qui fait référence à une URL, la règle est probablement malveillante.

- ***MailboxFormsExport-yyyy-mm-dd*.csv**: en général, l’utilisation de formulaires personnalisés est rare. Si vous en trouvez dans ce classeur, ouvrez la boîte aux lettres de cet utilisateur et examinez le formulaire lui-même. Si votre organisation ne l’a pas mise là intentionnellement, elle est probablement malveillante.

## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Comment arrêter et corriger l’attaque des règles et formulaires Outlook

Si vous trouvez des preuves de l’une de ces attaques, la correction est simple. Supprimez simplement la règle ou le formulaire de la boîte aux lettres. Vous pouvez le faire avec le client Outlook ou à l’aide d’Exchange PowerShell pour supprimer des règles.

### <a name="using-outlook"></a>Utilisation d’Outlook

1. Identifiez tous les appareils que l’utilisateur a utilisés avec Outlook. Ils devront tous être nettoyés des programmes malveillants potentiels. N’autorisez pas l’utilisateur à se connecter et à utiliser l’e-mail tant que tous les appareils ne sont pas nettoyés.

2. Suivez les étapes décrites dans [Supprimer une règle](https://support.microsoft.com/office/2f0e7139-f696-4422-8498-44846db9067f) pour chaque appareil.

3. Si vous n’êtes pas sûr de la présence d’autres programmes malveillants, vous pouvez mettre en forme et réinstaller tous les logiciels sur l’appareil. Pour les appareils mobiles, vous pouvez suivre les étapes des fabricants pour réinitialiser l’appareil à l’image d’usine.

4. Installez les versions les plus récentes d’Outlook. N’oubliez pas que la version actuelle d’Outlook bloque les deux types de cette attaque par défaut.

5. Une fois que toutes les copies hors connexion de la boîte aux lettres ont été supprimées, réinitialisez le mot de passe de l’utilisateur (utilisez un mot de passe de haute qualité) et suivez les étapes de configuration de [l’authentification multifacteur pour les utilisateurs si l’authentification](../../admin/security-and-compliance/set-up-multi-factor-authentication.md) multifacteur n’a pas déjà été activée. Cela garantit que les informations d’identification de l’utilisateur ne sont pas exposées par d’autres moyens (par exemple, hameçonnage ou réutilisation du mot de passe).

### <a name="using-powershell"></a>Utiliser PowerShell

Vous pouvez utiliser deux applets de commande Exchange PowerShell pour supprimer ou désactiver des règles dangereuses. Suivez simplement les étapes.

#### <a name="steps-for-mailboxes-that-are-on-an-exchange-server"></a>Étapes pour les boîtes aux lettres qui se trouvent sur un serveur Exchange

1. Connectez-vous au serveur Exchange à l’aide de PowerShell distant ou d’Exchange Management Shell. Suivez les étapes décrites dans [Se connecter aux serveurs Exchange à l’aide de PowerShell distant](/powershell/exchange/connect-to-exchange-servers-using-remote-powershell) ou [ouvrez Exchange Management Shell](/powershell/exchange/open-the-exchange-management-shell).

2. Si vous souhaitez supprimer complètement une seule règle, plusieurs règles ou toutes les règles d’une boîte aux lettres, utilisez l’applet de commande [Remove-InboxRule](/powershell/module/exchange/Remove-InboxRule) .

3. Si vous souhaitez conserver la règle et son contenu pour une investigation plus approfondie, utilisez l’applet de commande [Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

#### <a name="steps-for-mailboxes-in-exchange-online"></a>Étapes pour les boîtes aux lettres dans Exchange Online

1. Suivez les étapes décrites dans [Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Si vous souhaitez supprimer complètement une règle unique, plusieurs règles ou toutes les règles d’une boîte aux lettres, utilisez l’applet de commande [Remove-Inbox Rule](/powershell/module/exchange/Remove-InboxRule) .

3. Si vous souhaitez conserver la règle et son contenu pour une investigation plus approfondie, utilisez l’applet de commande [Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

## <a name="how-to-minimize-future-attacks"></a>Comment réduire les attaques futures

### <a name="first-protect-your-accounts"></a>Tout d’abord : protéger vos comptes

Les exploits de règles et de formulaires sont utilisés uniquement par un attaquant après avoir volé ou violé l’un des comptes de votre utilisateur. Ainsi, votre première étape pour empêcher l’utilisation de ces exploits contre votre organisation consiste à protéger vos comptes d’utilisateur de manière agressive. Certaines des manières les plus courantes de violation des comptes sont le hameçonnage ou les [attaques par pulvérisation de mots de passe](https://www.microsoft.com/security/blog/2020/04/23/protecting-organization-password-spray-attacks/).

La meilleure façon de protéger vos comptes d’utilisateur, et en particulier vos comptes d’administrateur, consiste à [configurer l’authentification multifacteur pour les utilisateurs](../../admin/security-and-compliance/set-up-multi-factor-authentication.md). Vous devez également :

- Surveillez la façon dont vos comptes d’utilisateur sont [accessibles et utilisés](/azure/active-directory/active-directory-view-access-usage-reports). Vous ne pouvez pas empêcher la violation initiale, mais vous raccourcirez la durée et l’impact de la violation en la détectant plus tôt. Vous pouvez utiliser ces [stratégies de Sécurité des applications cloud Office 365](/cloud-app-security/what-is-cloud-app-security) pour surveiller vos comptes et alerter les activités inhabituelles :

  - **Plusieurs tentatives de connexion ayant échoué** : cette stratégie profile votre environnement et déclenche des alertes lorsque les utilisateurs effectuent plusieurs activités de connexion ayant échoué dans une même session par rapport à la base de référence apprise, ce qui peut indiquer une tentative de violation.

  - **Voyage impossible** : cette stratégie profile votre environnement et déclenche des alertes lorsque des activités sont détectées par le même utilisateur à différents emplacements dans un délai plus court que le temps de trajet attendu entre les deux emplacements. Cela peut indiquer qu’un autre utilisateur utilise les mêmes informations d’identification. La détection de ce comportement anormal nécessite une période d’apprentissage initiale de sept jours pendant laquelle il apprend le modèle d’activité d’un nouvel utilisateur.

  - Activité d’emprunt **d’identité inhabituelle (par l’utilisateur)** : cette stratégie profile votre environnement et déclenche des alertes lorsque les utilisateurs effectuent plusieurs activités empruntant l’identité dans une même session par rapport à la base de référence apprise, ce qui peut indiquer une tentative de violation.

- Utilisez un outil comme [Office 365 Degré de sécurisation](/microsoft-365/security/defender/microsoft-secure-score) pour gérer les configurations et les comportements de sécurité des comptes.

### <a name="second-keep-your-outlook-clients-current"></a>Deuxièmement : maintenir vos clients Outlook à jour

Les versions entièrement mises à jour et mises à jour correctives d’Outlook 2013 et 2016 désactivent l’action de règle/formulaire « Démarrer l’application » par défaut. Cela garantit que, même si une personne malveillante viole le compte, les actions de règle et de formulaire sont bloquées. Vous pouvez installer les dernières mises à jour et correctifs de sécurité en suivant les étapes décrites dans [Installer les mises à jour d’Office](https://support.microsoft.com/office/2ab296f3-7f03-43a2-8e50-46de917611c5).

Voici les versions correctives pour vos clients Outlook 2013 et 2016 :

- **Outlook 2016** : 16.0.4534.1001 ou supérieur.

- **Outlook 2013** : 15.0.4937.1000 ou version ultérieure.

Pour plus d’informations sur les correctifs de sécurité individuels, consultez :

- [correctif de sécurité Outlook 2016](https://support.microsoft.com/help/3191883)

- [Correctif de sécurité Outlook 2013](https://support.microsoft.com/help/3191938)

### <a name="third-monitor-your-outlook-clients"></a>Troisièmement : Surveiller vos clients Outlook

Notez que même avec les correctifs et les mises à jour installés, il est possible pour un attaquant de modifier la configuration de l’ordinateur local pour réactiver le comportement « Démarrer l’application ». Vous pouvez utiliser [Advanced stratégie de groupe Management](/microsoft-desktop-optimization-pack/agpm/) pour surveiller et appliquer des stratégies de machine locale sur vos clients.

Vous pouvez voir si « Démarrer l’application » a été réactivé par le biais d’une substitution dans le Registre à l’aide des informations de [la procédure d’affichage du registre système à l’aide de versions 64 bits de Windows](https://support.microsoft.com/help/305097). Vérifiez ces sous-clés :

- **Outlook 2016** :`HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\`

- **Outlook 2013** : `HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\`

Recherchez la clé EnableUnsafeClientMailRules. S’il est là et est défini sur 1, le correctif de sécurité Outlook a été remplacé et l’ordinateur est vulnérable à l’attaque par formulaire/règles. Si la valeur est 0, l’action « Démarrer l’application » est désactivée. Si la version mise à jour et mise à jour corrective d’Outlook est installée et que cette clé de Registre n’est pas présente, un système n’est pas vulnérable à ces attaques.

Les clients disposant d’installations Exchange locales doivent envisager de bloquer les versions antérieures d’Outlook qui n’ont pas de correctifs disponibles. Pour plus d’informations sur ce processus, consultez l’article [Configurer le blocage du client Outlook](/exchange/configure-outlook-client-blocking-exchange-2013-help).

## <a name="see-also"></a>Voir aussi :

- [Les règles Outlook malveillantes](https://silentbreaksecurity.com/malicious-outlook-rules/) de SilentBreak Security Post sur Rules Vector fournissent une révision détaillée de la façon dont les règles Outlook.

- [MAPI sur HTTP et Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) sur le blog Sensepost sur Mailrule Pwnage traite d’un outil appelé Ruler qui vous permet d’exploiter des boîtes aux lettres via des règles Outlook.

- [Formulaires et interpréteurs de commandes Outlook](https://sensepost.com/blog/2017/outlook-forms-and-shells/) sur le blog Sensepost sur Forms Threat Vector.

- [Ruler Codebase](https://github.com/sensepost/ruler)

- [Indicateurs de règle de compromission](https://github.com/sensepost/notruler/blob/master/iocs.md)
