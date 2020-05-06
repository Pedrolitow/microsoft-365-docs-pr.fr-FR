---
title: Configurer les piliers de protection contre les menaces Microsoft pour l’environnement de laboratoire d’évaluation
description: Configurer Microsoft Threat Protection piliers, Office 365 ATP, Azure ATP, Microsoft Cloud App Security et Microsoft Defender ATP pour votre environnement de laboratoire d’évaluation
keywords: configurer la version d’évaluation de la protection de Microsoft contre les menaces, configuration de la version d’évaluation de Microsoft Threat Protection, configurer les piliers de protection de Microsoft contre les menaces
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 68d8f06803d75c3f89cae6fa7998734fd54084ca
ms.sourcegitcommit: 5476c2578400894640ae74bfe8e93c3319f685bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44049508"
---
# <a name="configure-microsoft-threat-protection-pillars-for-your-trial-lab-environment"></a>Configurer les piliers de protection contre les menaces Microsoft pour votre environnement de laboratoire d’évaluation

**S’applique à :**
- Protection Microsoft contre les menaces


La création d’un environnement de laboratoire de test Microsoft Threat Protection et son déploiement est un processus en trois phases :

<br>
<table border="0" width="100%" align="center">
  <tr style="text-align:center;">
    <td align="center" style="width:25%; border:0;" >
      <a href= "https://docs.microsoft.com/microsoft-365/security/mtp/prepare-mtpeval?view=o365-worldwide"> 
        <img src="../../media/prepare.png" alt="Prepare your Microsoft Threat Protection trial lab environment" title="Préparer votre environnement de laboratoire d’évaluation de la protection contre les menaces Microsoft" />
      <br/>Phase 1 : préparer</a><br>
    </td>
     <td align="center">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/setup-mtpeval?view=o365-worldwide">
        <img src="../../media/setup.png" alt="Set up your Microsoft Threat Protection trial lab environment" title="Configurer votre environnement de laboratoire d’évaluation de la protection contre les menaces Microsoft" />
      <br/>Phase 2 : configuration</a><br>
    </td>
    <td align="center" bgcolor="#d5f5e3">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/config-mtpeval?view=o365-worldwide">
        <img src="../../media/config-onboard.png" alt="Configure & Onboard" title="Configurer chaque pilier de protection contre les menaces Microsoft pour votre environnement de laboratoire d’évaluation de la protection contre les menaces Microsoft et les points de terminaison intégrés" />
      <br/>Phase 3 : configurer & Onboard</a><br>
</td>


  </tr>
</table>

Vous êtes actuellement en phase de configuration.


La préparation est essentielle à tout déploiement réussi. Dans cet article, vous serez guidé sur les points que vous devrez prendre en compte lors de la préparation du déploiement de Microsoft Defender ATP.


## <a name="microsoft-threat-protection-pillars"></a>Pilier de la protection Microsoft contre les menaces
La protection contre les menaces Microsoft se compose de quatre piliers. Bien qu’un seul pilier puisse déjà fournir de la valeur à la sécurité de votre organisation réseau, l’activation des quatre piliers de protection de Microsoft contre les menaces permettra à votre organisation de bénéficier de la plus grande valeur.

![Image of_page](../../media/mtp-eval-31.png) <br>

Cette section vous guidera dans la configuration des éléments suivants :
-   Office 365-Protection avancée contre les menaces
-   Azure Advanced Threat Protection 
-   Microsoft Cloud App Security
-   Microsoft Defender – Protection avancée contre les menaces


## <a name="configure-office-365-advanced-threat-protection"></a>Configurer la protection avancée contre les menaces Office 365
>[!NOTE]
>Ignorez cette étape si vous avez déjà activé la protection avancée contre les menaces d’Office 365. 

Il existe un module PowerShell appelé *Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA)* qui permet de déterminer certains de ces paramètres. Lorsqu’il est exécuté en tant qu’administrateur dans votre client, Get-ORCAReport permet de générer une évaluation du blocage du courrier indésirable, des hameçons et d’autres paramètres d’hygiène des messages. Vous pouvez télécharger ce module à https://www.powershellgallery.com/packages/ORCA/partir de. 

1. Accédez à la**stratégie**de**gestion** > des menaces du centre > de [sécurité & conformité Office 365](https://protection.office.com/homepage).
![Image of_page](../../media/mtp-eval-32.png) <br>
 
2. Cliquez sur **protection contre le hameçonnage ATP**, sélectionnez **créer** et renseignez le nom et la description de la stratégie. Cliquez sur **Suivant**.
![Image of_page](../../media/mtp-eval-33.png) <br>

>[!NOTE]
>Modifiez votre stratégie anti-hameçonnage avancée ATP. Remplacez le **seuil d’hameçonnage avancé** par **2**.
<br>

3. Cliquez sur le menu déroulant **Ajouter une condition** , puis sélectionnez vos domaines en tant que domaine du destinataire. Cliquez sur **Suivant**.
![Image of_page](../../media/mtp-eval-34.png) <br>
 
4. Vérifiez vos paramètres. Cliquez sur **créer cette stratégie** pour confirmer. 
![Image of_page](../../media/mtp-eval-35.png) <br>
 
5. Sélectionnez **pièces jointes fiables ATP** et sélectionnez l’option Activer la protection avancée contre les menaces **pour SharePoint, OneDrive et Microsoft teams** .  
![Image of_page](../../media/mtp-eval-36.png) <br>

6. Cliquez sur l’icône + pour créer une stratégie de pièces jointes fiables, appliquez-la en tant que domaine de destinataire à vos domaines. Cliquez sur **Enregistrer**.
![Image of_page](../../media/mtp-eval-37.png) <br>
 
7. Ensuite, sélectionnez la stratégie de **liens approuvés ATP** , puis cliquez sur l’icône représentant un crayon pour modifier la stratégie par défaut.

8. Assurez-vous que l’option **ne pas suivre lorsque les utilisateurs cliquent sur les liens approuvés** n’est pas sélectionnée, tandis que les autres options sont sélectionnées. Pour plus d’informations, voir [paramètres de liens fiables](https://docs.microsoft.com/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp?view=o365-worldwide) . Cliquez sur **Enregistrer**. 
![Image of_page](../../media/mtp-eval-38.png) <br>

9. Sélectionnez ensuite la stratégie **anti-programme malveillant** , sélectionnez la valeur par défaut, puis cliquez sur l’icône représentant un crayon.

10. Cliquez sur **paramètres** , puis sélectionnez **Oui et utilisez le texte de notification par défaut** pour activer la **réponse de détection de programmes malveillants**. Activez le **filtre types de pièces jointes courantes** . Cliquez sur **Enregistrer**.
<br>![Image of_page](../../media/mtp-eval-39.png) <br>
  
11. Accédez à [Office 365 Security & Compliance Center](https://protection.office.com/homepage) > **Search** > Search**audit log Search** and Turn Auditing on.  
![Image of_page](../../media/mtp-eval-40.png) <br>

12. Intégrer la protection avancée contre les menaces Office 365 à Microsoft Defender ATP. Accédez à [Office 365 Security & Compliance Center](https://protection.office.com/homepage) > Explorer**Management** > **Explorer** et sélectionnez **WDATP Settings** dans le coin supérieur droit de l’écran. Dans la boîte de dialogue connexion Microsoft Defender ATP, activez **connexion à Windows ATP**.
![Image of_page](../../media/mtp-eval-41.png) <br>

## <a name="configure-azure-advanced-threat-protection"></a>Configuration d’Azure protection avancée contre les menaces
>[!NOTE]
>Ignorez cette étape si vous avez déjà activé Azure protection avancée contre les menaces.


1. Accédez au [Centre de sécurité Microsoft 365](https://security.microsoft.com/info) > sélectionnez **plus de ressources** > **Azure Advanced Threat Protection**.
![Image of_page](../../media/mtp-eval-42.png) <br>

2. Cliquez sur **créer** pour démarrer l’Assistant protection avancée contre les menaces. 
<br>![Image of_page](../../media/mtp-eval-43.png) <br>

3. Choisissez **fournir un nom d’utilisateur et un mot de passe pour vous connecter à votre forêt Active Directory**.  
![Image of_page](../../media/mtp-eval-44.png) <br>

4. Entrez vos informations d’identification locales Active Directory. Il peut s’agir de n’importe quel compte d’utilisateur qui dispose d’un accès en lecture à Active Directory.
![Image of_page](../../media/mtp-eval-45.png) <br>

5. Ensuite, choisissez **Télécharger le programme d’installation du capteur** et transférer le fichier vers votre contrôleur de domaine. 
![Image of_page](../../media/mtp-eval-46.png) <br>

6. Exécutez le programme d’installation du capteur ATP Azure et commencez à suivre l’Assistant.
<br>![Image of_page](../../media/mtp-eval-47.png) <br>
 
7. Cliquez sur **suivant** dans le type de déploiement du capteur.
<br>![Image of_page](../../media/mtp-eval-48.png) <br>
 
8. Copiez la clé d’accès, puis entrez-la dans l’Assistant.
![Image of_page](../../media/mtp-eval-49.png) <br>
 
9. Copiez la clé d’accès dans l’Assistant, puis cliquez sur **installer**. 
<br>![Image of_page](../../media/mtp-eval-50.png) <br>

10. Félicitations, vous avez réussi à configurer Azure Advanced Threat Protection sur votre contrôleur de domaine.
![Image of_page](../../media/mtp-eval-51.png) <br>
 
11. Sous la section paramètres [Azure Azure ATP](https://go.microsoft.com/fwlink/?linkid=2040449) , sélectionnez **Windows Defender ATP**, puis activez le bouton bascule. Cliquez sur **Enregistrer**. 
![Image of_page](../../media/mtp-eval-52.png) <br>

>[!NOTE]
>Windows Defender ATP a été rebaptisé en tant que Microsoft Defender ATP. Les modifications apportées à la personnalisation de tous nos portails sont déployées pour la cohérence.


## <a name="configure-microsoft-cloud-app-security"></a>Configurer la sécurité des applications Cloud Microsoft
>[!NOTE]
>Ignorez cette étape si vous avez déjà activé Microsoft Cloud App Security. 

1.  > Accédez au [Centre de sécurité Microsoft 365](https://security.microsoft.com/info)**More Resources** > **Microsoft Cloud App Security**.
![Image of_page](../../media/mtp-eval-53.png) <br>

2. À l’invite d’informations pour intégrer Azure ATP, sélectionnez **activer l’intégration de données Azure ATP**. 
<br>![Image of_page](../../media/mtp-eval-54.png) <br>

>[!NOTE]
>Si vous ne voyez pas cette invite, cela signifie que votre intégration de données ATP Azure a déjà été activée. Toutefois, si vous n’êtes pas sûr, contactez votre administrateur informatique pour confirmer. 

3. Accédez à **paramètres**, activez l’option **intégration Azure ATP** activée, puis cliquez sur **Enregistrer**. 
![Image of_page](../../media/mtp-eval-55.png) <br>
>[!NOTE]
>Pour les nouvelles instances Azure ATP, ce bouton d’intégration est activé automatiquement. Vérifiez que votre intégration Azure ATP a été activée avant de passer à l’étape suivante.
 
4. Sous paramètres de découverte du Cloud, sélectionnez **intégration de Microsoft Defender ATP**, puis activez l’intégration. Cliquez sur **Enregistrer**.
![Image of_page](../../media/mtp-eval-56.png) <br>

5. Sous paramètres de détection sur le Cloud, sélectionnez enrichissement par l' **utilisateur**, puis activez l’intégration à Azure Active Directory.
![Image of_page](../../media/mtp-eval-57.png) <br>

## <a name="configure-microsoft-defender-advanced-threat-protection"></a>Configurer Microsoft Defender-protection avancée contre les menaces
>[!NOTE]
>Ignorez cette étape si vous avez déjà activé la protection avancée contre les menaces Microsoft Defender.

1. Accédez > au [Centre de sécurité Microsoft 365](https://security.microsoft.com/info)**plus de ressources** > **Microsoft Defender Security Center**. Cliquez sur **Ouvrir**. 
<br>![Image of_page](../../media/mtp-eval-58.png) <br>
 
2. Suivez l’Assistant protection avancée contre les menaces Microsoft. Cliquez sur **Suivant**. 
<br>![Image of_page](../../media/mtp-eval-59.png) <br>

3. Choisissez en fonction de votre emplacement de stockage de données par défaut, de la stratégie de rétention des données, de la taille de l’organisation et du opt-in pour les fonctionnalités d’aperçu. 
<br>![Image of_page](../../media/mtp-eval-60.png) <br>
>[!NOTE]
>Vous ne pouvez pas modifier par la suite certains paramètres, comme l’emplacement de stockage des données. 
<br>

Cliquez sur **Suivant**. 

4. Cliquez sur **Continuer** pour mettre en service votre locataire Microsoft Defender ATP.
<br>![Image of_page](../../media/mtp-eval-61.png) <br>

5. Intégrez vos points de terminaison via les stratégies de groupe, le gestionnaire de points de terminaison Microsoft ou en exécutant un script local vers Microsoft Defender ATP. Par souci de simplicité, ce guide utilise le script local.

6. Cliquez sur **Télécharger le package** et copiez le script d’intégration à vos points de terminaison.  
<br>![Image of_page](../../media/mtp-eval-62.png) <br>

7. Sur votre point de terminaison, exécutez le script d’intégration en tant qu’administrateur et choisissez Y.
<br>![Image of_page](../../media/mtp-eval-63.png) <br>

8. Félicitations, vous avez intégré votre premier point de terminaison.  
<br>![Image of_page](../../media/mtp-eval-64.png) <br>

9. Copiez-collez le test de détection à partir de l’Assistant Microsoft Defender ATP.
<br>![Image of_page](../../media/mtp-eval-65.png) <br>

10. Copiez le script PowerShell vers une invite de commandes avec élévation de privilèges et exécutez-le. 
<br>![Image of_page](../../media/mtp-eval-66.png) <br>

11. Sélectionnez **commencer à utiliser Microsoft Defender ATP** à partir de l’Assistant.
<br>![Image of_page](../../media/mtp-eval-67.png) <br>
 
12. Visitez le [Centre de sécurité Microsoft Defender](https://securitycenter.windows.com/). Accédez à **paramètres** , puis sélectionnez **fonctionnalités avancées**. 
<br>![Image of_page](../../media/mtp-eval-68.png) <br>

13. Activer l’intégration avec **Azure Advanced Threat Protection**.  
<br>![Image of_page](../../media/mtp-eval-69.png) <br>

14. Activer l’intégration avec **Office 365 Threat Intelligence**.
<br>![Image of_page](../../media/mtp-eval-70.png) <br>

15. Activez l’intégration à la **sécurité des applications Cloud de Microsoft**.
<br>![Image of_page](../../media/mtp-eval-71.png) <br>

16. Faites défiler la liste vers le bas et cliquez sur **enregistrer les préférences** pour confirmer les nouvelles intégrations.
<br>![Image of_page](../../media/mtp-eval-72.png) <br>

## <a name="next-steps"></a>Étapes suivantes
[Activez Microsoft Threat Protection](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable?view=o365-worldwide#start-using-the-service) , puis [générez une alerte de test](generate-test-alert.md).
