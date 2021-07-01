---
title: Configurer les Microsoft 365 Defender pour le laboratoire d’essai ou l’environnement pilote
description: Configurez Microsoft 365 Defender piliers, tels que Microsoft Defender pour Office 365, Microsoft Defender pour l’identité, Microsoft Cloud App Security et Microsoft Defender pour endpoint, pour votre laboratoire d’évaluation ou votre environnement pilote.
keywords: configurer Microsoft 365 Defender d’essai, Microsoft 365 Defender d’essai, configurer Microsoft 365 Defender projet pilote, configurer Microsoft 365 Defender piliers, Microsoft 365 Defender piliers
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
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e50210f02d14be33c357517515d456318aac4bb6
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53229778"
---
# <a name="configure-microsoft-365-defender-pillars-for-your-trial-lab-or-pilot-environment"></a>Configurer les Microsoft 365 Defender pour votre laboratoire d’essai ou votre environnement pilote

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender


La création d Microsoft 365 Defender laboratoire d’évaluation ou d’un environnement pilote et son déploiement sont un processus en trois phases :

|[![Phase 1 : préparation](../../media/phase-diagrams/prepare.png)](prepare-m365d-eval.md)<br/>[Phase 1 : préparation](prepare-m365d-eval.md) |[![Phase 2 : configuration](../../media/phase-diagrams/setup.png)](setup-m365deval.md)<br/>[Phase 2 : configuration](setup-m365deval.md) |![Phase 3 : intégration](../../media/phase-diagrams/onboard.png)<br/>Phase 3 : intégration | [![Retour au pilote](../../media/phase-diagrams/backtopilot.png)](m365d-pilot.md)<br/>[Retour au manuel pilote](m365d-pilot.md) |
|--|--|--|--|
|| |*Vous êtes là !* | |

Vous êtes actuellement en phase de configuration.

La préparation est essentielle pour tout déploiement réussi. Dans cet article, vous serez guidé sur les points que vous devrez prendre en compte lorsque vous préparerez le déploiement de Microsoft Defender pour Endpoint.

## <a name="microsoft-365-defender-pillars"></a>Microsoft 365 Defender piliers
Microsoft 365 Defender se compose de quatre piliers. Bien qu’un pilier puisse déjà apporter une valeur ajoutée à la sécurité de votre organisation réseau, l’activation des quatre piliers Microsoft 365 Defender sera la valeur la plus importante pour votre organisation.

![Image of_Microsoft solution 365 Defender pour les utilisateurs, Microsoft Defender pour l’identité, pour les points de terminaison Microsoft Defender pour endpoint, pour les applications cloud, Microsoft Cloud App Security et pour les données, Microsoft Defender pour Office 365](../../media/mtp/m365pillars.png)

Cette section vous guide pour configurer :

- Microsoft Defender pour Office 365
- Microsoft Defender pour l’identité
- Microsoft Cloud App Security
- Microsoft Defender pour point de terminaison

## <a name="configure-microsoft-defender-for-office-365"></a>Configurer Microsoft Defender pour Office 365

> [!NOTE]
> Ignorez cette étape si vous avez déjà activé Defender pour Office 365.

Il existe un module PowerShell appelé *ORCA (Advanced Threat Protection Recommended Configuration Analyzer) Office 365* qui vous aide à déterminer certains de ces paramètres. Lorsqu’il est exécuté en tant qu’administrateur dans votre client, get-ORCAReport vous aide à générer une évaluation des paramètres d’hygiène des messages anti-courrier indésirable, anti-hameçonnage et autres. Vous pouvez télécharger ce module à partir https://www.powershellgallery.com/packages/ORCA/ de .

1. Accédez à [Office 365 stratégie de gestion des menaces & du Centre](https://protection.office.com/homepage)de sécurité et  >    >  **conformité.**

   ![Image of_Office page de stratégie de gestion des menaces du Centre de sécurité & conformité 365](../../media/mtp-eval-32.png)

2. Cliquez **sur Anti-hameçonnage,** **sélectionnez Créer** et remplir le nom et la description de la stratégie. Cliquez sur **Suivant**.

   ![Image of_Office page de stratégie anti-hameçonnage du Centre de sécurité & conformité 365 dans laquelle vous pouvez nommer votre stratégie](../../media/mtp-eval-33.png)

   > [!NOTE]
   > Modifiez votre stratégie anti-hameçonnage avancée dans Microsoft Defender pour Office 365. Modifiez **le seuil de hameçonnage** avancé **sur 2 - Agressif**.

3. Cliquez sur le menu déroulant Ajouter une **condition** et sélectionnez vos domaines comme domaine de destinataire. Cliquez sur **Suivant**.

   ![Image of_Office page de stratégie anti-hameçonnage du Centre de sécurité & conformité 365 dans laquelle vous pouvez ajouter une condition pour son application](../../media/mtp-eval-34.png)

4. Examinez vos paramètres. Cliquez **sur Créer cette stratégie pour** confirmer.

   ![Image of_Office page de stratégie anti-hameçonnage du Centre de sécurité & et conformité 365 365 dans laquelle vous pouvez passer en revue vos paramètres et cliquer sur le bouton Créer cette stratégie](../../media/mtp-eval-35.png)

5. Sélectionnez **Coffre pièces jointes** et l’option Activer la SharePoint **de SharePoint, OneDrive et Microsoft Teams** de saisie.

   ![Image of_Office page du Centre de sécurité & conformité 365 dans laquelle vous pouvez activer la protection contre les SharePoint, les OneDrive et les Microsoft Teams](../../media/mtp-eval-36.png)

6. Cliquez sur l’icône + pour créer une stratégie de pièces jointes sécurisées, puis appliquez-la en tant que domaine de destinataire à vos domaines. Cliquez sur **Enregistrer**.

   ![Image of_Office page du Centre de sécurité & conformité 365 dans laquelle vous pouvez créer une stratégie de pièces jointes sécurisées](../../media/mtp-eval-37.png)

7. Ensuite, sélectionnez la **stratégie Coffre liens,** puis cliquez sur l’icône de crayon pour modifier la stratégie par défaut.

8. Assurez-vous que l’option Ne pas **me** suivre lorsque les utilisateurs cliquent sur l’option Liens sécurisés n’est pas sélectionnée, tandis que les autres options sont sélectionnées. Pour [plus d Coffre, voir les paramètres](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365) des liens. Cliquez sur **Enregistrer**.

   ![Image of_Office page du Centre de sécurité & conformité 365 qui indique que l’option Ne pas suivre quand les utilisateurs cliquent sur la sécurité n’est pas sélectionnée](../../media/mtp-eval-38.png)

9. Sélectionnez ensuite la **stratégie anti-programme** malveillant, sélectionnez la stratégie par défaut, puis choisissez l’icône de crayon.

10. Cliquez **Paramètres** sélectionnez Oui et **utilisez le texte** de notification par défaut pour activer la réponse de détection de **programmes malveillants.** Activer le **filtre Types de pièces jointes courants.** Cliquez sur **Enregistrer**.

    ![Image of_Office 365 Security & Compliance Center qui indique que la réponse de détection de programmes malveillants est allumée avec la notification par défaut et que le filtre des types de pièces jointes courants est allumé](../../media/mtp-eval-39.png)

11. Accédez à [Office 365 recherche dans](https://protection.office.com/homepage)& du journal d’audit du Centre de sécurité et conformité et activer  >    >   l’audit.

    ![Image of_Office 365 Security & Compliance Center où vous pouvez activer la recherche dans le journal d’audit](../../media/mtp-eval-40.png)

12. Intégrez Microsoft Defender pour Office 365 microsoft Defender pour le point de terminaison. Accédez [à Office 365 l&](https://protection.office.com/homepage)de gestion des menaces du Centre de sécurité et conformité et sélectionnez Microsoft Defender pour le point de terminaison Paramètres dans le coin supérieur droit  >    >   de l’écran.  Dans la boîte de dialogue de connexion Defender pour point de terminaison, Connecter **à Microsoft Defender pour le point de terminaison.**

    ![Image of_Office page du Centre de sécurité & conformité 365 dans laquelle vous pouvez activer la connexion Microsoft Defender pour le point de terminaison](../../media/mtp-eval-41.png)

## <a name="configure-microsoft-defender-for-identity"></a>Configurer Microsoft Defender pour l’identité

> [!NOTE]
> Ignorez cette étape si vous avez déjà activé Microsoft Defender pour l’identité

1. Accédez à [Microsoft 365 Centre de](https://security.microsoft.com/info) sécurité > sélectionnez Plus de **ressources** Microsoft Defender  >  **pour l’identité.**

   ![Image of_Microsoft page du Centre de sécurité 365 dans laquelle il existe une option pour ouvrir Microsoft Defender pour l’identité](../../media/mtp-eval-42.png)

2. Cliquez **sur Créer** pour démarrer l’Assistant Microsoft Defender pour l’identité.

   ![Image of_Microsoft page de l’Assistant Defender pour l’identité où vous devez cliquer sur le bouton Créer](../../media/mtp-eval-43.png)

3. Choisissez **Fournir un nom d’utilisateur et un mot de passe pour vous connecter à votre forêt Active Directory.**

   ![Image of_Microsoft page d’accueil de Defender for Identity](../../media/mtp-eval-44.png)

4. Entrez vos informations d’identification actives sur site. Il peut s’y trouver n’importe quel compte d’utilisateur qui dispose d’un accès en lecture à Active Directory.

   ![Image of_Microsoft page Defender for Identity Directory services où vous devez placer vos informations d’identification](../../media/mtp-eval-45.png)

5. Ensuite, **sélectionnez Télécharger le programme d’installation du** capteur et transférer le fichier vers votre contrôleur de domaine.

   ![Image of_Microsoft page Defender for Identity dans laquelle vous pouvez sélectionner Télécharger le programme d’installation du capteur](../../media/mtp-eval-46.png)

6. Exécutez le programme d’installation de Microsoft Defender for Identity Sensor et commencez à suivre l’Assistant.

   ![Image of_Microsoft page Defender pour l’identité dans laquelle vous devez cliquer en suivant l’Assistant Capteur Microsoft Defender pour l’identité](../../media/mtp-eval-47.png)

7. Cliquez **sur Suivant** au niveau du type de déploiement du capteur.

   ![Image of_Microsoft page Defender pour l’identité où vous devez cliquer en suivant pour passer à la page suivante](../../media/mtp-eval-48.png)

8. Copiez la touche d’accès rapide, car vous devez la saisir ensuite dans l’Assistant.

   ![Page of_the capteurs d’image où vous devez copier la touche d’accès rapide que vous devez entrer dans la prochaine page de l’Assistant Configuration du capteur Microsoft Defender pour l’identité](../../media/mtp-eval-49.png)

9. Copiez la touche d’accès rapide dans l’Assistant, puis cliquez sur **Installer.**

   ![Image of_Microsoft’Assistant Capteur d’identité dans laquelle vous devez fournir la touche d’accès rapide, puis cliquer sur le bouton d’installation](../../media/mtp-eval-50.png)

10. Félicitations, vous avez correctement configuré Microsoft Defender pour l’identité sur votre contrôleur de domaine.

    ![Image of_Microsoft l’installation de l’Assistant Capteur d’identité, où vous devez cliquer sur le bouton Terminer](../../media/mtp-eval-51.png)

11. Sous la section [Paramètres de Microsoft Defender pour](https://go.microsoft.com/fwlink/?linkid=2040449) l’identité, sélectionnez **Microsoft Defender pour le point de terminaison **, puis activer le basculement. Cliquez sur **Enregistrer**.

    ![Image of_the page des paramètres de Microsoft Defender pour l’identité dans laquelle vous devez activer le basculement De Microsoft Defender pour le point de terminaison](../../media/mtp-eval-52.png)

## <a name="configure-microsoft-cloud-app-security"></a>Configurer Microsoft Cloud App Security

> [!NOTE]
> Ignorez cette étape si vous avez déjà activé Microsoft Cloud App Security.

1. Accédez à [Microsoft 365 centre de sécurité Plus](https://security.microsoft.com/info)de  >  **ressources**  >  **Microsoft Cloud App Security**.

   ![Image of_Microsoft page centre de sécurité 365 dans laquelle vous pouvez voir la carte Microsoft Cloud App et qui doit cliquer sur le bouton d’ouverture](../../media/mtp-eval-53.png)

2. À l’invite d’informations pour intégrer Microsoft Defender pour l’identité, sélectionnez **Activer Microsoft Defender pour l’intégration des données d’identité.**

   ![Image of_the’invite d’informations pour intégrer Microsoft Defender pour l’identité où vous devez sélectionner le lien Activer Microsoft Defender pour l’intégration des données d’identité](../../media/mtp-eval-54.png)

   > [!NOTE]
   > Si vous ne voyez pas cette invite, cela peut signifier que l’intégration des données microsoft Defender pour l’identité a déjà été activée. Toutefois, si vous n’êtes pas sûr, contactez votre administrateur informatique pour confirmer.

3. Go to **Paramètres,** turn on the **Microsoft Defender for Identity integration** toggle, then click **Save**.

   ![Image of_the page des paramètres dans laquelle vous devez activer le bouton bascule d’intégration Microsoft Defender pour l’identité, puis cliquez sur Enregistrer](../../media/mtp-eval-55.png)

   > [!NOTE]
   > Pour les nouvelles instances de Microsoft Defender pour l’identité, ce basculement d’intégration est automatiquement allumé. Confirmez que l’intégration de Microsoft Defender for Identity a été activée avant de passer à l’étape suivante.

4. Sous les paramètres de découverte cloud, sélectionnez **Microsoft Defender pour l’intégration de point** de terminaison, puis activez l’intégration. Cliquez sur **Enregistrer**.

   ![Image of_the page Microsoft Defender pour point de terminaison dans laquelle la case à cocher Bloquer les applications non sélectionnées sous Microsoft Defender pour l’intégration de point de terminaison est sélectionnée. Cliquez sur Enregistrer.](../../media/mtp-eval-56.png)

5. Sous Paramètres de découverte cloud, sélectionnez **Enrichissement de** l’utilisateur, puis activez l’intégration avec Azure Active Directory.

   ![Image de la section Enrichissement d’utilisateurs dans laquelle la case à cocher Enrichissement d’utilisateurs découverts Azure Active Directory des noms d’utilisateurs est cocher](../../media/mtp-eval-57.png)

## <a name="configure-microsoft-defender-for-endpoint"></a>Configurer Microsoft Defender pour le point de terminaison

> [!NOTE]
> Ignorez cette étape si vous avez déjà activé Microsoft Defender pour endpoint.

1. Accédez à [Microsoft 365 centre de sécurité Plus](https://security.microsoft.com/info)de  >  **ressources**  >  **Centre de sécurité Microsoft Defender**. Cliquez sur **Ouvrir**. 

   ![Image of_Microsoft’option Centre de sécurité Defender dans la page centre Microsoft 365 sécurité](../../media/mtp-eval-58.png)

2. Suivez l’Assistant Microsoft Defender pour point de terminaison. Cliquez sur **Suivant**.

   ![Image of_the Centre de sécurité Microsoft Defender page de l’Assistant d’accueil](../../media/mtp-eval-59.png)

3. Choisissez en fonction de votre emplacement de stockage de données préféré, de votre stratégie de rétention des données, de la taille de l’organisation et de votre choix pour les fonctionnalités de prévisualisation.

   ![Image of_the page pour sélectionner votre pays de stockage de données, votre stratégie de rétention et la taille de votre organisation. Cliquez sur suivant lorsque vous avez terminé la sélection.](../../media/mtp-eval-60.png)

   > [!NOTE]
   > Vous ne pouvez pas modifier certains paramètres, tels que l’emplacement de stockage des données, par la suite.

   Cliquez sur **Suivant**.

4. Cliquez **sur Continuer** pour mettre en service votre client Microsoft Defender for Endpoint.

   ![Image of_the page vous invite à cliquer sur le bouton Continuer pour créer votre instance cloud](../../media/mtp-eval-61.png)

5. Intégrer vos points de terminaison via des stratégies de groupe, Microsoft Endpoint Manager ou en exécutant un script local dans Microsoft Defender pour point de terminaison. Par souci de simplicité, ce guide utilise le script local.

6. Cliquez **sur Télécharger le package** et copiez le script d’intégration sur vos points de terminaison.

   ![Image of_page vous invite à cliquer sur le bouton Télécharger le package pour copier le script d’intégration sur vos points de terminaison ou points de terminaison](../../media/mtp-eval-62.png)

7. Sur votre point de terminaison, exécutez le script d’intégration en tant qu’administrateur et choisissez Y.

   ![Image of_the ligne de commande dans laquelle vous exécutez le script d’intégration et choisissez Y pour continuer](../../media/mtp-eval-63.png)

8. Félicitations, vous avez intégré votre premier point de terminaison.

   ![Image of_the ligne de commande dans laquelle vous obtenez la confirmation que vous avez intégré votre premier point de terminaison. Appuyez sur n’importe quelle touche pour continuer](../../media/mtp-eval-64.png)

9. Copiez-collez le test de détection à partir de l’Assistant Microsoft Defender for Endpoint.

   ![Image of_the exécuter une étape de test de détection dans laquelle vous devez cliquer sur Copier pour copier le script de test de détection à coller dans l’invite de commandes](../../media/mtp-eval-65.png)

10. Copiez le script PowerShell dans une invite de commandes avec élévation de niveaux et exécutez-le.

    ![Image of_command’invite de commandes où vous devez copier le script PowerShell dans une invite de commandes avec élévation de élévation de niveaux et l’exécuter](../../media/mtp-eval-66.png)

11. Sélectionnez **Démarrer à l’aide de Microsoft Defender pour le point de terminaison à partir** de l’Assistant.

    ![Image of_the’invite de confirmation à partir de l’Assistant où vous devez cliquer sur Démarrer à l’aide de Microsoft Defender pour le point de terminaison](../../media/mtp-eval-67.png)

12. Visitez le [Centre de sécurité Microsoft Defender](https://securitycenter.windows.com/). Go to **Paramètres** and then select **Advanced features**.

    ![Image of_Microsoft du centre de sécurité Defender Paramètres dans lequel vous devez sélectionner les fonctionnalités avancées](../../media/mtp-eval-68.png)

13. Activer l’intégration avec **Microsoft Defender pour l’identité.**

    ![Image of_Microsoft fonctionnalités avancées du Centre de sécurité Defender, bascule de l’option Microsoft Defender pour l’identité que vous devez activer](../../media/mtp-eval-69.png)

14. Activer l’intégration avec **Office 365 Threat Intelligence**.

    ![Image of_Microsoft fonctionnalités avancées du Centre de sécurité Defender, Office 365'option Threat Intelligence que vous devez activer](../../media/mtp-eval-70.png)

15. Activer l’intégration avec **Microsoft Cloud App Security**.

    ![Image of_Microsoft fonctionnalités avancées du Centre de sécurité Defender, Microsoft Cloud App Security d’option que vous devez activer](../../media/mtp-eval-71.png)

16. Faites défiler vers le bas et cliquez **sur Enregistrer les préférences** pour confirmer les nouvelles intégrations.

    ![Bouton of_Save des préférences de l’image que vous devez cliquer](../../media/mtp-eval-72.png)

## <a name="start-the-microsoft-365-defender-service"></a>Démarrer le service Microsoft 365 Defender

> [!NOTE]
> À compter du 1er juin 2020, Microsoft active automatiquement les fonctionnalités Microsoft 365 Defender pour tous les clients éligibles. Consultez cet [article microsoft Tech Community sur l’éligibilité](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/microsoft-threat-protection-will-automatically-turn-on-for/ba-p/1345426) aux licences pour plus d’informations.

Go to [Microsoft 365 Security Center](https://security.microsoft.com/homepage). Accédez **à Paramètres** puis sélectionnez **Microsoft 365 Defender**.

![Image of_Microsoft’option 365 Defender à partir de la page Microsoft 365 de sécurité Paramètres de sécurité](../../media/mtp-eval-72b.png)

Pour obtenir des instructions plus complètes, voir [Activer Microsoft 365 Defender](m365d-enable.md).

Félicitations ! Vous viennent de créer votre laboratoire d Microsoft 365 Defender d’essai ou votre environnement pilote ! Vous pouvez maintenant vous familiariser avec l’interface Microsoft 365 Defender’utilisateur. Découvrez ce que vous pouvez apprendre à partir du guide Microsoft 365 Defender interactif et découvrez comment utiliser chaque tableau de bord pour vos tâches quotidiennes d’opération de sécurité.

[Consulter le guide interactif](https://aka.ms/MTP-Interactive-Guide)

Ensuite, vous pouvez simuler une attaque et voir comment les fonctionnalités entre produits détectent, créent des alertes et répondent automatiquement à une attaque sans fichier sur un point de terminaison.

## <a name="next-step"></a>Étape suivante

- [Générez une alerte de test](generate-test-alert.md) : exécutez une simulation d’attaque dans Microsoft 365 Defender laboratoire d’essai.
