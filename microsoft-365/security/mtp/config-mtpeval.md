---
title: Configurer les piliers de Microsoft 365 Defender pour le laboratoire d’évaluation ou l’environnement pilote
description: Configurez les piliers de Microsoft 365 Defender, tels que Microsoft Defender pour Office 365, Microsoft Defender pour l’identité, la sécurité de l’application Cloud Microsoft et Microsoft Defender pour le point de terminaison, pour votre laboratoire d’évaluation ou votre environnement pilote.
keywords: configurer la version d’évaluation de la protection de Microsoft Threat, configuration de la version d’évaluation de Microsoft Threat Protection, configurer le projet pilote Microsoft Threat Protection, configurer la protection Microsoft contre les menaces, pilier de la protection Microsoft contre les menaces
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.openlocfilehash: 88db2182ec1a3250d2f4308858026fec97a2f91b
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844103"
---
# <a name="configure-microsoft-365-defender-pillars-for-your-trial-lab-or-pilot-environment"></a>Configurer les piliers de Microsoft 365 Defender pour votre laboratoire d’évaluation ou votre environnement pilote

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender


La création d’un laboratoire de test Microsoft 365 Defender ou d’un environnement pilote et son déploiement est un processus en trois phases :

<br>
<table border="0" width="100%" align="center">
  <tr style="text-align:center;">
    <td align="center" style="width:25%; border:0;" >
      <a href= "https://docs.microsoft.com/microsoft-365/security/mtp/prepare-mtpeval?view=o365-worldwide"> 
        <img src="../../media/prepare.png" alt="Prepare your Microsoft 365 Defender trial lab or pilot environment" title="Préparation de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft 365 Defender" />
      <br/>Phase 1 : préparer </a><br>
    </td>
     <td align="center">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/setup-mtpeval?view=o365-worldwide">
        <img src="../../media/setup.png" alt="Set up your Microsoft 365 Defender trial lab or pilot environment" title="Configuration de votre laboratoire d’évaluation Microsoft 365 Defender ou de votre environnement pilote" />
      <br/>Phase 2 : configuration </a><br>
    </td>
    <td align="center" bgcolor="#d5f5e3">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/config-mtpeval?view=o365-worldwide">
        <img src="../../media/config-onboard.png" alt="Configure & Onboard" title="Configurez chaque pilier de Microsoft 365 Defender pour votre laboratoire d’évaluation Microsoft 365 Defender, votre environnement pilote et vos points de terminaison intégrés." />
      <br/>Phase 3 : configurer & Onboard </a><br>
</td>
  </tr>
</table>

Vous êtes actuellement en phase de configuration.


La préparation est essentielle à tout déploiement réussi. Dans cet article, vous serez guidé sur les points que vous devrez prendre en compte lors de la préparation du déploiement de Microsoft Defender for Endpoint.


## <a name="microsoft-365-defender-pillars"></a>Piliers de Microsoft 365 Defender
Microsoft 365 Defender se compose de quatre piliers. Bien qu’un seul pilier puisse déjà fournir de la valeur à la sécurité de votre organisation réseau, l’activation des quatre piliers de Microsoft 365 Defender donnera à votre organisation la plus grande valeur.

![Image of_Microsoft 365 Defender solution for Users, Microsoft Defender for Identity, for Endpoints Microsoft Defender for Endpoint, for Cloud Apps, Microsoft Cloud App Security, and for Data, Microsoft Defender for Office 365](../../media/mtp-eval-31.png)

Cette section vous guidera dans la configuration des éléments suivants :
-   Microsoft Defender pour Office 365
-   Microsoft Defender pour l’identité 
-   Microsoft Cloud App Security
-   Microsoft Defender pour point de terminaison


## <a name="configure-microsoft-defender-for-office-365"></a>Configurer Microsoft Defender pour Office 365

>[!NOTE]
>Ignorez cette étape si vous avez déjà activé l’option Defender pour Office 365. 

Il existe un module PowerShell appelé *Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA)* qui permet de déterminer certains de ces paramètres. Lorsqu’il est exécuté en tant qu’administrateur dans votre client, Get-ORCAReport permet de générer une évaluation du blocage du courrier indésirable, des hameçons et d’autres paramètres d’hygiène des messages. Vous pouvez télécharger ce module à partir de https://www.powershellgallery.com/packages/ORCA/ . 

1. Accédez à la stratégie de gestion des menaces du [Centre de sécurité & conformité Office 365](https://protection.office.com/homepage)  >  **Threat management**  >  **Policy**.

   ![Image of_Office 365 sécurité & Centre de conformité gestion des menaces-page de stratégie](../../media/mtp-eval-32.png)
 
2. Cliquez sur **anti-hameçonnage** , sélectionnez **créer** et renseignez le nom et la description de la stratégie. Cliquez sur **Suivant**.

   ![Page de la stratégie anti-hameçonnage du centre de sécurité & de l’image of_Office 365, dans laquelle vous pouvez nommer votre stratégie](../../media/mtp-eval-33.png)

   > [!NOTE]
   > Modifiez votre stratégie anti-hameçonnage avancée dans Microsoft Defender pour Office 365. Remplacez le **seuil d’hameçonnage avancé** par **2**.

3. Cliquez sur le menu déroulant **Ajouter une condition** , puis sélectionnez vos domaines en tant que domaine du destinataire. Cliquez sur **Suivant**.

   ![Page de la stratégie anti-hameçonnage du centre de sécurité & de l’image of_Office 365, dans laquelle vous pouvez ajouter une condition pour son application](../../media/mtp-eval-34.png)
 
4. Vérifiez vos paramètres. Cliquez sur **créer cette stratégie** pour confirmer. 

   ![Image of_Office 365 sécurité & de la page de stratégie anti-hameçonnage du centre de conformité, dans laquelle vous pouvez vérifier vos paramètres et cliquer sur le bouton créer cette stratégie](../../media/mtp-eval-35.png)
 
5. Sélectionnez **pièces jointes fiables** et sélectionnez l’option Activer la protection avancée contre les menaces **pour SharePoint, OneDrive et Microsoft teams** .

   ![Image of_Office 365 page Centre de sécurité & conformité, dans laquelle vous pouvez activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams](../../media/mtp-eval-36.png)

6. Cliquez sur l’icône + pour créer une stratégie de pièces jointes fiables, appliquez-la en tant que domaine de destinataire à vos domaines. Cliquez sur **Enregistrer**.

   ![Image of_Office 365 page du centre de sécurité & conformité où vous pouvez créer une nouvelle stratégie de pièces jointes fiables](../../media/mtp-eval-37.png)
 
7. Ensuite, sélectionnez la stratégie de **liens approuvés** , puis cliquez sur l’icône représentant un crayon pour modifier la stratégie par défaut.

8. Assurez-vous que l’option **ne pas suivre lorsque les utilisateurs cliquent sur les liens approuvés** n’est pas sélectionnée, tandis que les autres options sont sélectionnées. Pour plus d’informations, voir [paramètres de liens fiables](https://docs.microsoft.com/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp) . Cliquez sur **Enregistrer**. 

   ![Image of_Office 365 page du centre de sécurité & conformité qui indique que l’option ne suit pas lorsque les utilisateurs cliquent sur Safe n’est pas sélectionné](../../media/mtp-eval-38.png)

9. Sélectionnez ensuite la stratégie **anti-programme malveillant** , sélectionnez la valeur par défaut, puis cliquez sur l’icône représentant un crayon.

10. Cliquez sur **paramètres** , puis sélectionnez **Oui et utilisez le texte de notification par défaut** pour activer la **réponse de détection de programmes malveillants**. Activez le **filtre types de pièces jointes courantes** . Cliquez sur **Enregistrer**.

    ![Image of_Office 365 page du centre de sécurité & conformité qui indique que la réponse de détection de programmes malveillants est activée avec notification par défaut et que le filtre de types de pièces jointes courantes est activé](../../media/mtp-eval-39.png)
  
11. Accédez à [Office 365 Security & Compliance Center](https://protection.office.com/homepage)  >  **Search**  >  **audit log Search** and Turn Auditing on.

    ![Image of_Office 365 de la page Centre de sécurité & conformité, dans laquelle vous pouvez activer la recherche du journal d’audit](../../media/mtp-eval-40.png)

12. Intégrez Microsoft Defender pour Office 365 à Microsoft Defender for Endpoint. Accédez à [Office 365 Security & Compliance Center](https://protection.office.com/homepage)  >  **Threat management**  >  **Explorer Management Explorer** et sélectionnez **Microsoft Defender for Endpoint Settings** dans le coin supérieur droit de l’écran. Dans la boîte de dialogue Defender pour la connexion au point de terminaison, activez **connexion à Microsoft Defender pour le point de terminaison**.

    ![Image of_Office 365 de la page Centre de sécurité & conformité, dans laquelle vous pouvez activer la connexion à Microsoft Defender pour le point de terminaison](../../media/mtp-eval-41.png)

## <a name="configure-microsoft-defender-for-identity"></a>Configurer Microsoft Defender pour l’identité

>[!NOTE]
>Ignorez cette étape si vous avez déjà activé Microsoft Defender pour l’identité

1. Accédez au [Centre de sécurité Microsoft 365](https://security.microsoft.com/info) > sélectionnez **plus**  >  **de ressources Microsoft Defender pour l’identité**.

   ![Page du centre de sécurité image of_Microsoft 365 où il existe une option pour ouvrir Microsoft Defender pour l’identité](../../media/mtp-eval-42.png)

2. Cliquez sur **créer** pour démarrer l’Assistant Microsoft Defender pour les identités. 

   ![Image of_Microsoft Defender for Identity Wizard, dans laquelle vous devez cliquer sur le bouton créer](../../media/mtp-eval-43.png)

3. Choisissez **fournir un nom d’utilisateur et un mot de passe pour vous connecter à votre forêt Active Directory**.  

   ![Image of_Microsoft Defender for Identity welcome page](../../media/mtp-eval-44.png)

4. Entrez vos informations d’identification locales Active Directory. Il peut s’agir de n’importe quel compte d’utilisateur qui dispose d’un accès en lecture à Active Directory.

   ![Image of_Microsoft Defender for Identity Directory Services où vous devez placer vos informations d’identification](../../media/mtp-eval-45.png)

5. Ensuite, choisissez **Télécharger le programme d’installation du capteur** et transférer le fichier vers votre contrôleur de domaine.

   ![Image of_Microsoft Defender pour l’identité, dans laquelle vous pouvez sélectionner l’option Télécharger le capteur de téléchargement](../../media/mtp-eval-46.png)

6. Exécutez le programme d’installation de Microsoft Defender pour le capteur d’identité et commencez à suivre l’Assistant.

   ![Image of_Microsoft Defender pour l’identité où vous devez cliquer sur suivant pour suivre l’Assistant Microsoft Defender pour le capteur d’identité](../../media/mtp-eval-47.png)
 
7. Cliquez sur **suivant** dans le type de déploiement du capteur.

   ![Image of_Microsoft Defender pour la page identité où vous devez cliquer sur suivant pour accéder à la page suivante](../../media/mtp-eval-48.png)
 
8. Copiez la clé d’accès, car vous devez l’entrer ensuite dans l’Assistant.

   ![Page capteurs d’image of_the où vous devez copier la clé d’accès que vous devez entrer dans la page suivante de l’Assistant de configuration du capteur d’identité de Microsoft Defender](../../media/mtp-eval-49.png)
 
9. Copiez la clé d’accès dans l’Assistant, puis cliquez sur **installer**. 

   ![Image of_Microsoft Defender pour l’Assistant capteur d’identité où vous devez fournir la clé d’accès, puis cliquez sur le bouton installer.](../../media/mtp-eval-50.png)

10. Félicitations, vous avez réussi à configurer Microsoft Defender pour l’identité sur votre contrôleur de domaine.

    ![Image of_Microsoft la fin de l’installation de l’Assistant capteur d’identité où vous devez cliquer sur le bouton Terminer](../../media/mtp-eval-51.png)
 
11. Sous la section [Microsoft Defender pour les paramètres d’identité](https://go.microsoft.com/fwlink/?linkid=2040449) , sélectionnez * * Microsoft Defender pour le point de terminaison * *, puis activez le bouton bascule. Cliquez sur **Enregistrer**. 

    ![Image of_the la page Microsoft Defender pour les paramètres d’identité où vous devez activer le basculement Microsoft Defender pour le point de terminaison activé](../../media/mtp-eval-52.png)

>[!NOTE]
>Windows Defender ATP a été rebaptisé Microsoft Defender for Endpoint. Les modifications apportées à la personnalisation de tous nos portails sont déployées pour la cohérence.


## <a name="configure-microsoft-cloud-app-security"></a>Configurer la sécurité des applications Cloud Microsoft

>[!NOTE]
>Ignorez cette étape si vous avez déjà activé Microsoft Cloud App Security. 

1. Accédez au [Centre de sécurité Microsoft 365](https://security.microsoft.com/info)  >  **More Resources**  >  **Microsoft Cloud App Security**.

   ![Page of_Microsoft 365 du centre de sécurité sur lequel vous pouvez voir la carte d’application Cloud de Microsoft et qui doit cliquer sur le bouton ouvrir](../../media/mtp-eval-53.png)

2. À l’invite informations pour intégrer Microsoft Defender pour identité, sélectionnez **activer l’intégration des données d’identité Microsoft Defender**.
  
   ![Image of_the informations vous invitant à intégrer Microsoft Defender pour l’identité où vous devez sélectionner le lien activer Microsoft Defender pour l’intégration des données d’identité](../../media/mtp-eval-54.png)

   > [!NOTE]
   > Si vous ne voyez pas cette invite, cela signifie que votre service Microsoft Defender pour l’intégration des données d’identité a déjà été activé. Toutefois, si vous n’êtes pas sûr, contactez votre administrateur informatique pour confirmer. 

3. Accédez à **paramètres** , activez le bouton **Microsoft Defender for Identity Integration** , puis cliquez sur **Enregistrer**. 

   ![Image of_the page Paramètres où vous devez activer le bouton Microsoft Defender for Identity Integration, puis cliquez sur Enregistrer.](../../media/mtp-eval-55.png)
   
   > [!NOTE]
   > Pour les nouvelles instances de Microsoft Defender pour les identités, ce bouton d’intégration est activé automatiquement. Vérifiez que votre Microsoft Defender pour l’intégration des identités a été activé avant de passer à l’étape suivante.
 
4. Sous paramètres de découverte du Cloud, sélectionnez **Microsoft Defender pour l’intégration de points de terminaison** , puis activez l’intégration. Cliquez sur **Enregistrer**.

   ![Image of_the la page Microsoft Defender pour les points de terminaison où la case à cocher bloquer les applications non sanctionnées sous Microsoft Defender pour l’intégration de points de terminaison est sélectionnée. Cliquez sur Enregistrer.](../../media/mtp-eval-56.png)

5. Sous paramètres de détection sur le Cloud, sélectionnez enrichissement par l' **utilisateur** , puis activez l’intégration à Azure Active Directory.

   ![Image de la section enrichissement par l’utilisateur dans laquelle la case à cocher enrichir les identificateurs utilisateur enrichis avec des noms d’utilisateur Azure Active Directory est activée](../../media/mtp-eval-57.png)


## <a name="configure-microsoft-defender-for-endpoint"></a>Configurer Microsoft Defender pour le point de terminaison

>[!NOTE]
>Ignorez cette étape si vous avez déjà activé Microsoft Defender pour le point de terminaison.

1. Accédez au [Centre de sécurité Microsoft 365](https://security.microsoft.com/info)  >  **plus de ressources**  >  **Microsoft Defender Security Center**. Cliquez sur **Ouvrir**. 

   ![Option du centre de sécurité de l’image of_Microsoft Defender dans la page Centre de sécurité Microsoft 365](../../media/mtp-eval-58.png)
 
2. Suivez l’Assistant Microsoft Defender pour les points de terminaison. Cliquez sur **Suivant**. 

   ![Image of_the page d’accueil de l’Assistant Centre de sécurité Microsoft Defender](../../media/mtp-eval-59.png)

3. Choisissez en fonction de votre emplacement de stockage de données par défaut, de la stratégie de rétention des données, de la taille de l’organisation et du opt-in pour les fonctionnalités d’aperçu.

   ![Image of_the page permettant de sélectionner votre pays de stockage des données, la stratégie de rétention et la taille de l’organisation. Cliquez sur suivant lorsque vous avez fini de sélectionner.](../../media/mtp-eval-60.png)
   
   > [!NOTE]
   > Vous ne pouvez pas modifier par la suite certains paramètres, comme l’emplacement de stockage des données. 

   Cliquez sur **Suivant**. 

4. Cliquez sur **Continuer** pour configurer votre client Microsoft Defender pour le point de terminaison.

   ![Image of_the page vous invitant à cliquer sur le bouton continuer pour créer votre instance Cloud](../../media/mtp-eval-61.png)

5. Intégrez vos points de terminaison via les stratégies de groupe, le gestionnaire de points de terminaison Microsoft ou en exécutant un script local vers Microsoft Defender pour le point de terminaison. Par souci de simplicité, ce guide utilise le script local.

6. Cliquez sur **Télécharger le package** et copiez le script d’intégration à vos points de terminaison.

   ![Image of_page invite à cliquer sur le bouton Télécharger le package pour copier le script d’intégration à votre point de terminaison ou aux points de terminaison](../../media/mtp-eval-62.png)

7. Sur votre point de terminaison, exécutez le script d’intégration en tant qu’administrateur et choisissez Y. 

   ![Image of_the CommandLine où vous exécutez le script d’intégration et choisissez Y pour continuer](../../media/mtp-eval-63.png)

8. Félicitations, vous avez intégré votre premier point de terminaison.

   ![Image of_the CommandLine où vous recevez la confirmation que vous avez intégrée votre premier point de terminaison. Appuyez sur une touche pour continuer](../../media/mtp-eval-64.png)

9. Copiez-collez le test de détection à partir de l’Assistant Microsoft Defender pour le point de terminaison.

   ![Image of_the exécutez une étape de test de détection à partir de laquelle vous devez cliquer sur copier pour copier le script de test de détection que vous devez coller dans l’invite de commandes.](../../media/mtp-eval-65.png)

10. Copiez le script PowerShell vers une invite de commandes avec élévation de privilèges et exécutez-le. 

    ![Image of_command invite où vous devez copier le script PowerShell vers une invite de commandes avec élévation de privilèges et l’exécuter](../../media/mtp-eval-66.png)

11. Sélectionnez **commencer à utiliser Microsoft Defender pour le point de terminaison** à partir de l’Assistant.

    ![Image of_the invite de confirmation à partir de l’Assistant où vous devez cliquer sur Démarrer à l’aide de Microsoft Defender for Endpoint](../../media/mtp-eval-67.png)
 
12. Visitez le [Centre de sécurité Microsoft Defender](https://securitycenter.windows.com/). Accédez à **paramètres** , puis sélectionnez **fonctionnalités avancées**. 

    ![Menu des paramètres du centre de sécurité de l’image of_Microsoft Defender dans lequel vous devez sélectionner les fonctionnalités avancées](../../media/mtp-eval-68.png)

13. Activez l’intégration à **Microsoft Defender pour l’identité**.  

    ![Les fonctionnalités avancées de l’option Centre de sécurité de l’image of_Microsoft Defender, Microsoft Defender for Identity, que vous devez activer](../../media/mtp-eval-69.png)

14. Activer l’intégration avec **Office 365 Threat Intelligence**.

    ![Image of_Microsoft Defender Security Center Advanced Features, Office 365 Threat Intelligence option permettez à activer](../../media/mtp-eval-70.png)

15. Activez l’intégration à la **sécurité des applications Cloud de Microsoft**.

    ![Image of_Microsoft Defender Security Center Advanced Features, option de sécurité de l’application Cloud Microsoft activer/désactiver](../../media/mtp-eval-71.png)

16. Faites défiler la liste vers le bas et cliquez sur **enregistrer les préférences** pour confirmer les nouvelles intégrations.

    ![Image of_Save bouton préférences que vous devez cliquer](../../media/mtp-eval-72.png)

## <a name="start-the-microsoft-365-defender-service"></a>Démarrer le service Defender Microsoft 365

>[!NOTE]
>À partir du 1er juin 2020, Microsoft active automatiquement les fonctionnalités de Microsoft 365 Defender pour tous les clients éligibles. Pour plus d’informations, consultez cet [article de la communauté Microsoft Tech sur l’éligibilité des licences](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/microsoft-threat-protection-will-automatically-turn-on-for/ba-p/1345426) . 


Accédez au [Centre de sécurité Microsoft 365](https://security.microsoft.com/homepage). Accédez à **paramètres** , puis sélectionnez **Microsoft 365 Defender**.

![Image of_Microsoft 365 Defender option capture d’écran de la page Paramètres du centre de sécurité Microsoft 365 ](../../media/mtp-eval-72b.png) <br>

Pour obtenir des instructions plus détaillées, consultez la rubrique [activer Microsoft 365 Defender](mtp-enable.md). 

Félicitations ! Vous venez de créer votre laboratoire d’évaluation ou votre environnement pilote Microsoft 365 Defender ! Vous pouvez désormais vous familiariser avec l’interface utilisateur de Microsoft 365 Defender ! Consultez ce que vous pouvez apprendre à partir du guide interactif Microsoft 365 Defender et apprenez à utiliser chaque tableau de bord pour vos tâches de sécurité quotidiennes.


>[!VIDEO https://aka.ms/MTP-Interactive-Guide]

Ensuite, vous pouvez simuler une attaque et voir comment les fonctionnalités du produit croisé détectent, créer des alertes et répondre automatiquement à une attaque en mode fichier sur un point de terminaison.

## <a name="next-step"></a>Étape suivante
|![Phase de simulation d’attaque](../../media/mtp/run-sim.png) <br>[Phase de simulation d’attaque](mtp-pilot-simulate.md) | Exécutez la simulation d’attaque pour votre environnement pilote Microsoft 365 Defender.
|:-------|:-----|
