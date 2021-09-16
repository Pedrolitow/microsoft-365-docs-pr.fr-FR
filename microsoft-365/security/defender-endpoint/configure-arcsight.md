---
title: Configurer Micro Focus ArcSight pour tirer Microsoft Defender pour les détections de points de terminaison
description: Configurer Micro Focus ArcSight pour recevoir et tirer des détections à partir de Centre de sécurité Microsoft Defender
keywords: configurer Micro Focus ArcSight, outils de gestion des informations de sécurité et des événements, arcsight
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 41d07ae2c6acc4bdbe828bc98d8bdfecdbf45f2e
ms.sourcegitcommit: 4740e69326eb7f8302eec7bab5bd516d498e4492
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2021
ms.locfileid: "59401721"
---
# <a name="configure-micro-focus-arcsight-to-pull-defender-for-endpoint-detections"></a>Configurer Micro Focus ArcSight pour tirer Defender pour les détections de points de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configurearcsight-abovefoldlink)

Vous devez installer et configurer certains fichiers et outils pour utiliser Micro Focus ArcSight afin qu’il puisse tirer Defender pour les détections de points de terminaison.

> [!NOTE]
>
> - [Defender pour l’alerte de point de terminaison](alerts.md) se compose d’une ou de plusieurs détections
> - [Defender for Endpoint Detection est](api-portal-mapping.md) composé de l’événement suspect qui s’est produit sur l’appareil et de ses détails d’alerte associés.

## <a name="before-you-begin"></a>Avant de commencer

La configuration de l’outil Micro Focus ArcSight Connector nécessite plusieurs fichiers de configuration pour qu’il tire et pare les détections à partir de votre application Azure Active Directory (AAD).

Cette section vous guide dans l’obtention des informations nécessaires pour définir et utiliser correctement les fichiers de configuration requis.

- Assurez-vous que vous avez activé la fonctionnalité d’intégration SIEM à partir **Paramètres** menu. Pour plus d’informations, voir [Enable SIEM integration in Defender for Endpoint](enable-siem-integration.md).

- Préparez le fichier que vous avez enregistré en activant la fonctionnalité d’intégration SIEM. Vous devez obtenir les valeurs suivantes :
  - URL d’actualisation du jeton OAuth 2.0
  - OAuth 2.0 Client ID
  - OAuth 2.0 Client Secret

- Préparez les fichiers de configuration suivants :
- 
  - WDATP-connector.properties
  - WDATP-connector.jsonparser.properties

    Vous ariez enregistré un fichier .zip qui contient ces deux fichiers lorsque vous avez choisi Micro Focus ArcSight comme type SIEM que vous utilisez dans votre organisation.

- Veillez à générer les jetons suivants et à les préparer :
  - Access token (Jeton d’accès)
  - Jeton d’actualisation

  Vous pouvez générer ces jetons à partir de la section de configuration de **l’intégration SIEM** du portail.

## <a name="install-and-configure-micro-focus-arcsight-flexconnector"></a>Installer et configurer Micro Focus ArcSight FlexConnector

Les étapes suivantes supposent que vous avez effectué toutes les étapes requises dans [Avant de commencer.](#before-you-begin)

1. Installez le dernier programme d’installation Windows 32 bits de FlexConnector. Vous pouvez le trouver dans le centre logiciel HPE. L’outil est généralement installé à l’emplacement par défaut suivant : `C:\Program Files\ArcSightFlexConnectors\current\bin` .</br></br>Vous pouvez choisir où enregistrer l’outil, par exemple C : \\ *folder_location*\current\bin *où folder_location* représente l’emplacement d’installation.

2. Suivez l’Assistant Installation à travers les tâches suivantes :
   - Introduction
   - Choose Install Folder
   - Choose Install Set
   - Choose Shortcut Folder
   - Résumé de la pré-installation
   - Installation...

   Vous pouvez conserver les valeurs par défaut pour chacune de ces tâches ou modifier la sélection en fonction de vos besoins.

3. Ouvrez l’Explorateur de fichiers et recherchez les deux fichiers de configuration que vous avez enregistrés lorsque vous avez activé la fonctionnalité d’intégration SIEM. Placez les deux fichiers à l’emplacement d’installation de FlexConnector, par exemple :

   - WDATP-connector.jsonparser.properties: C: \\ *folder_location*\current\user\agent\flexagent\
   - WDATP-connector.properties: C: \\ *folder_location*\current\user\agent\flexagent\

   > [!NOTE]
   > Vous devez placer les fichiers de configuration à cet emplacement, où *folder_location* représente l’emplacement où vous avez installé l’outil.

4. Une fois l’installation du connecteur principal terminée, la fenêtre d’installation du connecteur s’ouvre. Dans la fenêtre d’installation du connecteur, **sélectionnez Ajouter un connecteur.**

5. Select Type: **ArcSight FlexConnector REST** and click **Next**.

6. Tapez les informations suivantes dans le formulaire de détails des paramètres. Toutes les autres valeurs du formulaire sont facultatives et peuvent être laissées vides.

   <br>

   ****

   |Champ|Valeur|
   |---|---|
   |Fichier de configuration|Tapez le nom du fichier de propriétés client. Le nom doit correspondre au fichier fourni dans la .zip que vous avez téléchargée. <p> Par exemple, si le fichier de configuration dans le répertoire « flexagent » est nommé « WDATP-Connector.jsonparser.properties », vous devez taper « WDATP-Connector » comme nom du fichier de propriétés du client.|
   |URL des événements|Selon l’emplacement de votre centre de données, sélectionnez l’UE, les États-Unis ou l’URL du Royaume-Uni : <ul><li>**Pour l’UE**:  `https://wdatp-alertexporter-eu.windows.com/api/alerts/?sinceTimeUtc=$START_AT_TIME`</li><li>**Pour les États-Unis**: `https://wdatp-alertexporter-us.windows.com/api/alerts/?sinceTimeUtc=$START_AT_TIME`</li><li>**Pour le Royaume-Uni**: `https://wdatp-alertexporter-uk.windows.com/api/alerts/?sinceTimeUtc=$START_AT_TIME`</li></ul>|
   |Type d’authentification|OAuth 2|
   |Fichier de propriétés du client OAuth 2|Accédez à l’emplacement du *fichier wdatp-connector.properties.* Le nom doit correspondre au fichier fourni dans la .zip que vous avez téléchargée.|
   |Jeton d’actualisation|Vous pouvez obtenir un jeton d’actualisation de deux manières : en générant un jeton d’actualisation à partir de la page des **paramètres SIEM** ou en utilisant l’outil restutil. <p> Pour plus d’informations sur la génération d’un jeton d’actualisation à partir de la configuration **préférences,** voir Activer l’intégration [SIEM dans Defender for Endpoint](enable-siem-integration.md). <p> **Obtenez votre jeton d’actualisation à l’aide de l’outil restutil**: <ol><li>Ouvrez une invite de commandes. Accédez à C: \\ *emplacement \_ du* dossier \current\bin où *\_ l’emplacement* du dossier représente l’emplacement où vous avez installé l’outil.</li><li>Type : `arcsight restutil token -config` à partir du répertoire bin. Par exemple : **arcsight restutil boxtoken -proxy proxy.location.hp.com:8080**. Une fenêtre de navigateur Web s’ouvre.</li><li>Tapez vos informations d’identification, puis cliquez sur le champ mot de passe pour que la page soit redirigée. Dans l’invite de connexion, entrez vos informations d’identification.</li><li>Un jeton d’actualisation est affiché dans l’invite de commandes.</li><li>Copiez-le et collez-le dans **le champ Jeton d’actualisation.**|
   |

7. Une fenêtre de navigateur est ouverte par le connecteur. Connectez-vous avec vos informations d’identification d’application. Une fois que vous vous êtes connecter, vous êtes invité à accorder l’autorisation à votre client OAuth2. Vous devez accorder des autorisations à votre client OAuth 2 pour que la configuration du connecteur puisse s’authentifier.

   `redirect_uri`S’il s’agit d’une URL https, vous serez redirigé vers une URL sur l’hôte local. Vous verrez une page qui vous demande d’faire confiance au certificat fourni par le connecteur s’exécutant sur l’hôte local. Vous devez faire confiance à ce certificat si l’redirect_uri est un https.

   Toutefois, si vous spécifiez une URL http pour redirect_uri, vous n’avez pas besoin de donner votre consentement pour l’approbation du certificat.

8. Poursuivez l’installation du connecteur en revenant à la fenêtre d’installation du connecteur Micro Focus ArcSight.

9. Sélectionnez **le Gestionnaire ArcSight (chiffré)** comme destination, puis cliquez sur **Suivant**.

10. Tapez l’adresse IP/nom d’hôte de destination dans **le nom** d’hôte du gestionnaire et vos informations d’identification dans le formulaire de paramètres. Toutes les autres valeurs du formulaire doivent être conservées avec les valeurs par défaut. Cliquez sur **Suivant**.

11. Tapez un nom pour le connecteur dans le formulaire de détails du connecteur. Toutes les autres valeurs du formulaire sont facultatives et peuvent être laissées vides. Cliquez sur **Suivant**.

12. La fenêtre d’importation du certificat esM Manager s’affiche. Sélectionnez **Importer le certificat vers le connecteur à partir de la destination,** puis cliquez sur **Suivant.** La **fenêtre Résumé du connecteur d’ajout** s’affiche et le certificat est importé.

13. Vérifiez que les détails dans la fenêtre Résumé du **connecteur** d’ajout sont corrects, puis cliquez sur **Suivant**.

14. Sélectionnez **Installer en tant que service,** puis cliquez sur **Suivant.**

15. Tapez un nom dans le **champ Nom interne du** service. Toutes les autres valeurs du formulaire peuvent être conservées avec les valeurs par défaut ou laissées vides. Cliquez sur **Suivant**.

16. Tapez les paramètres du service, puis cliquez sur **Suivant.** Une fenêtre avec le **résumé du service d’installation** s’affiche. Cliquez sur **Suivant**.

17. Terminez l’installation en **sélectionnant Exit** et **Next**.

## <a name="install-and-configure-the-micro-focus-arcsight-console"></a>Installer et configurer la console Micro Focus ArcSight

1. Suivez l’Assistant Installation à travers les tâches suivantes :
   - Introduction
   - Contrat de licence
   - Avis spécial
   - Choisir le répertoire d’installation ArcSight
   - Choose Shortcut Folder
   - Résumé de la pré-installation

2. Cliquez sur **Installer**. Une fois l’installation terminée, l’Assistant Configuration de la console ArcSight s’ouvre.

3. Tapez localhost dans **le nom d’hôte** du gestionnaire et 8443 dans le port du **gestionnaire,** puis cliquez sur **Suivant**.

4. Sélectionnez **Utiliser la connexion directe,** puis cliquez sur **Suivant.**

5. Sélectionnez **Authentification par mot de** passe, puis cliquez sur **Suivant.**

6. Sélectionnez **Il s’agit d’une installation utilisateur unique. (Recommandé),** puis cliquez sur **Suivant.**

7. Cliquez **sur Terminé** pour quitter le programme d’installation.

8. Connectez-vous à la console Micro Focus ArcSight.

9. Accédez à **l’ensemble de canaux actifs** \> **Nouveau produit** \> **d’appareil** \> **condition.**

10. Définir **le produit de l’appareil = Microsoft Defender ATP**. Une fois que vous avez vérifié que les événements sont en cours de flux vers l’outil, arrêtez à nouveau le processus et Windows Services et démarrez le REST ArcSight FlexConnector.

Vous pouvez désormais exécuter des requêtes dans la console Micro Focus ArcSight.

Les détections defender pour les points de terminaison apparaissent en tant qu’événements discrets, avec « Microsoft » comme fournisseur et « Windows Defender ATP » comme nom d’appareil.

## <a name="troubleshooting-micro-focus-arcsight-connection"></a>Résolution des problèmes de connexion Micro Focus ArcSight

**Problème :** Échec de l’actualisation du jeton. Le journal se trouve dans C: \\ *folder_location*\current\logs où folder_location représente l’emplacement où vous avez installé  l’outil. Ouvrez _agent.log_ et recherchez `ERROR/FATAL/WARN` .

**Symptôme :** Vous obtenez le message d’erreur suivant :

`Failed to refresh the token. Set reauthenticate to true: com.arcsight.common.al.e: Failed to refresh access token: status=HTTP/1.1 400 Bad Request FATAL EXCEPTION: Could not refresh the access token`

**Solution :**

1. Arrêtez le processus en cliquant sur Ctrl + C dans la fenêtre Connecteur. Cliquez **sur Y** lorsque vous avez demandé « Terminer le travail par lots Y/N ? ».

2. Accédez au dossier dans lequel vous avez stocké le fichier WDATP-connector.properties et modifiez-le pour ajouter la valeur suivante :

   `reauthenticate=true`.

3. Redémarrez le connecteur en exécutant la commande suivante :

   `arcsight.bat connectors`.

   Une fenêtre de navigateur s’affiche. Autorisez-le à s’exécuter, il doit disparaître et le connecteur doit maintenant être en cours d’exécution.

> [!NOTE]
> Vérifiez que le connecteur est en cours d’exécution en arrêtant à nouveau le processus. Ensuite, démarrez à nouveau le connecteur et aucune fenêtre de navigateur ne doit s’apparaître.

## <a name="related-topics"></a>Voir aussi

- [Activer l’intégration SIEM dans Defender for Endpoint](enable-siem-integration.md)
- [Tirer les détections vers vos outils SIEM](/windows/security/threat-protection/microsoft-defender-atp/configure-siem)
- [Détections pull Defender pour les points de terminaison à l’aide de l’API REST](pull-alerts-using-rest-api.md)
- [Résoudre des problèmes d’intégration de l’outil SIEM](troubleshoot-siem.md)
