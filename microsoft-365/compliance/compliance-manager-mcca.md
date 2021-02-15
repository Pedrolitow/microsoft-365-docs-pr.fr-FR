---
title: Analyseur de configuration de conformité Microsoft pour le Gestionnaire de conformité
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Comprendre comment utiliser l’Analyseur de configuration de conformité Microsoft pour être rapidement opérationnel avec le Gestionnaire de conformité Microsoft.
ms.openlocfilehash: 86c4b04deb8313f3013a6d9ad349c0f4112db773
ms.sourcegitcommit: 719b89baca1bae14455acf2e517ec18fc473636c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "50122394"
---
# <a name="microsoft-compliance-configuration-analyzer-for-compliance-manager-preview"></a>Analyseur de configuration de la conformité Microsoft pour le Gestionnaire de conformité (prévisualisation)

**Dans cet article :** Découvrez comment installer et exécuter l’outil Microsoft Compliance Configure Analyzer pour commencer rapidement avec le gestionnaire de conformité Microsoft.

## <a name="microsoft-compliance-configuration-analyzer-mcca-preview-overview"></a>Présentation de l’Analyseur de configuration de la conformité Microsoft (MCCA) (prévisualisation)

L’Analyseur de configuration de la conformité Microsoft (MCCA) est un outil de prévisualisation qui peut vous aider à démarrer avec le Gestionnaire de [conformité Microsoft.](compliance-manager.md) MCCA est un utilitaire basé sur PowerShell qui récupère les configurations actuelles de votre organisation et les valide par rapport aux meilleures pratiques recommandées de Microsoft 365. Ces meilleures pratiques sont basées sur un ensemble de contrôles qui incluent des réglementations clés et des normes pour la protection des données et la gouvernance des données.

MCCA peut vous aider à voir rapidement quelles actions d’amélioration du Gestionnaire de conformité s’appliquent à votre environnement Microsoft 365 actuel. Chaque action identifiée par MCCA vous donne des recommandations pour l’implémentation, avec des liens directs vers le Gestionnaire de conformité et la solution applicable pour commencer à prendre des mesures correctives.

Une ressource supplémentaire pour comprendre MCCA consiste à consulter les [instructions README sur GitHub.](https://github.com/OfficeDev/MCCA#overview) Cette page fournit des informations détaillées sur les conditions préalables et fournit des instructions d’installation complètes. Vous n’avez pas besoin d’un compte GitHub pour accéder à cette page.

Disponibilité : MCCA est disponible pour toutes les organisations titulaires de licences Office 365 et Microsoft 365 et clients modérés de la Communauté du gouvernement américain (GCC), avec des plans en cours d’extension du service pour les clients GCC High.

## <a name="install-mcca-and-run-a-report"></a>Installer MCCA et exécuter un rapport

Vous pouvez installer l’outil MCCA à l’aide Windows PowerShell. Une fois que vous avez téléchargé et installé l’outil, vous n’avez pas besoin de répéter ces étapes pour exécuter des rapports. Chaque fois que vous ouvrez MCCA, il vous demande vos informations d’identification de connexion et génère un nouveau rapport mis à jour.

#### <a name="step-1-install-windows-powershell"></a>Étape 1 : Installer Windows PowerShell
Pour commencer, vous aurez besoin du module Exchange Online PowerShell (version 2.0.3 ou supérieure) disponible dans la galerie PowerShell. [Obtenir des instructions d’installation.](https://www.powershellgallery.com/packages/ExchangeOnlineManagement/2.0.3)

#### <a name="step-2-install-mcca"></a>Étape 2 : Installer MCCA

Pour installer MCCA, commencez par utiliser PowerShell en mode administrateur. Suivez les étapes ci-dessous :

1. Sélectionnez le bouton **Démarrer** de Windows.
2. Tapez **PowerShell,** cliquez avec le bouton **droit sur Windows PowerShell,** puis **sélectionnez Exécuter en tant qu’administrateur.**
1. Depuis l’invite de commandes, tapez :

    ```powershell
    Install-Module -Name MCCAPreview
    ```

#### <a name="step-3-run-a-report"></a>Étape 3 : Exécuter un rapport

Après avoir installé MCCA, vous pouvez exécuter MCCA et générer un rapport. Pour exécuter un rapport :

1. Ouvrir PowerShell
2. Exécutez l’cmdlet :

    ```powershell
    Get-MCCAReport
    ```
3. Une fois que MCCA s’exécute, il vérifie la version initiale et demande des informations d’identification. À l’invite d’entrée du nom d’utilisateur, connectez-vous avec votre adresse de messagerie de compte Microsoft 365 (affichez les rôles éligibles[pour créer des rapports).](#role-based-reporting) Entrez ensuite votre mot de passe à l’invite de mot de passe.

Votre rapport prendra ensuite environ 2 à 5 minutes pour être généré. Une fois l’application effectuée, une fenêtre de navigateur s’ouvre et affiche votre rapport HTML. Chaque fois que vous exécutez l’outil, il vous demande vos informations d’identification et génère un nouveau rapport. Ce rapport est stocké localement dans le répertoire suivant :

C:\Users \<username> \AppData\Local\Microsoft\MCCA. 

Vous pouvez accéder aux rapports générés précédemment à partir de ce répertoire.

## <a name="understanding-your-report"></a>Comprendre votre rapport

Votre rapport reflète les données en fonction de la date et de l’heure à laquelle il a été généré. La section supérieure fournit des détails sur la moment où elle a été générée, le nom de votre organisation et l’ID de client.

#### <a name="geolocation-based-reporting"></a>Rapports basés sur la géolocalisation

La  section Remarque indique que votre rapport est personnalisé en fonction de l’emplacement géographique de votre client. Les recommandations répertoriées dans l’outil seront spécifiques à votre pays ou région.

Votre sélection de géolocalisation permet d’évaluer les types d’informations sensibles (SIT) qui sont pertinents pour cette géolocalisation et de générer un rapport qui s’aligne sur votre pays ou région. Choisissez des géolocalisations en fonction des données que vous avez dans votre client.

Pour modifier les informations d’emplacement de votre rapport, vous devez fournir un paramètre d’entrée de géolocalisation (-Geo). Vous pouvez choisir une ou plusieurs géolocalisations applicables à votre client.

Suivez ces instructions pour exécuter un rapport basé sur un emplacement spécifique :

1. Ouvrir PowerShell
2. Pour spécifier une région, vous devez exécuter une cmdlet à l’aide des numéros du tableau ci-dessous qui correspondent au pays ou à la région. Entrez plusieurs nombres en les séparant par une virgule. Par exemple, l’cmdlet ci-dessous exécute un rapport personnalisé pour Asia-Pacific et le Japon :

    ```powershell
    Get-MCCAReport -Geo @(1,7)
    ```
  | Input |  Pays ou région | 
  | :------------- | :------------: |
  | 1  | Asie-Pacifique |
  | 2  | Australie |
  | 3  | Canada |
  | 4  | Europe (à l’exception de la France) / Moyen-Orient / Afrique |
  | 5  | France |
  | 6  | Inde |
  | 7  | Japon |
  | 8  | Corée |
  | 9  | Amérique du Nord (à l’exception du Canada) |
  | 10  | Amérique du Sud |
  | 11  | Afrique du Sud |
  | 12  | Suisse |
  | 13  | Émirats arabes unis |
  | 14  | Royaume-Uni |


 > [!NOTE]
> Le rapport inclut toujours les types d’informations sensibles internationaux pris en charge par MCCA, tels que le code SWIFT, le numéro de carte de crédit, etc.

#### <a name="role-based-reporting"></a>Rapports basés sur les rôles

Votre rapport sera également personnalisé en fonction de votre rôle.

Le tableau ci-dessous indique les rôles qui ont accès aux sections du rapport. D’autres rôles au sein de votre organisation (non répertoriés dans le tableau ci-dessous) peuvent ne pas être en mesure d’exécuter l’outil, ou ils peuvent exécuter l’outil et avoir un accès limité aux informations dans le rapport final.

![MCCA : rôles](../media/compliance-manager-mcca-roles.png "Rôles MCCA")

Exceptions :
1. L’utilisateur ne peut pas générer de rapport pour l’adresse IP en dehors de la section « Utiliser IRM pour Exchange Online ».
2. L’utilisateur peut générer un rapport pour l’adresse IP en dehors de la section « Utiliser IRM pour Exchange Online ».
3. L’utilisateur pourra générer un rapport pour l’adresse IP en dehors de la section « Activer la conformité des communications dans O365 ».
4. L’utilisateur ne pourra pas générer de rapport pour l’adresse IP à part la section « Activer l’audit dans Office 365 ».
5. L’utilisateur peut générer un rapport pour l’adresse IP en dehors de la section « Activer l’audit dans Office 365 ».

#### <a name="solutions-summary-section"></a>Section Résumé des solutions

La section **Résumé des** solutions du rapport donne une vue d’ensemble des actions d’amélioration que votre organisation peut prendre dans le Gestionnaire de conformité pour vous aider à améliorer votre posture de conformité.

![MCCA - Résumé des solutions](../media/compliance-manager-mcca-solutions.png "Écran Résumé des solutions MCCA")

MCCA évalue vos configurations actuelles par rapport aux actions d’amélioration recommandées dans le Gestionnaire de conformité. Toute action d’amélioration identifiée par l’outil MCCA comme devant être attentive est répertoriée dans cette section.

En plus de chaque solution Microsoft, des zones codées en couleur indiquent le nombre d’éléments qui correspondent aux actions d’amélioration dans le Gestionnaire de conformité. Les actions sont décomposées en trois états d’état :

- **OK**: actions qui répondent aux conditions recommandées et qui n’ont pas besoin d’être attentives pour le moment
- **Amélioration :** actions qui ont besoin d’attention
- **Recommandation**: actions qui n’ont pas besoin d’attention, mais pour lesquelles nous vous recommandons les meilleures pratiques
 
Sélectionnez une zone pour afficher les améliorations et les recommandations.

**Éléments avec l’état d’amélioration**

Sélectionnez la dropdown en face de l’étiquette **d’amélioration** à droite de l’action d’amélioration. Vous verrez un résumé rapide et des détails sur vos paramètres actuels et les actions d’amélioration recommandées. Le résumé inclut des liens directs vers le Gestionnaire de conformité, la solution applicable dans le Centre de conformité Microsoft 365 et la documentation appropriée.

Le fait de cliquer sur le lien Gestionnaire de conformité vous permet d’afficher une vue filtrée de toutes les actions d’amélioration au sein de cette solution que vous n’avez pas encore implémentées. À partir de là, vous pouvez voir le nombre de points que vous pouvez atteindre pour augmenter votre [score](compliance-score-calculation.md)de conformité, les évaluations qu’ils s’appliquent, ainsi que les réglementations et certifications applicables.

Pour la DLP, il existe un bouton **Script** de correction qui vous donne un script PowerShell pré-généré en fonction des recommandations. Vous pouvez le copier et le coller directement dans votre console PowerShell. Il crée une stratégie DLP en mode test

**Éléments avec l’état Recommandation**

Sélectionnez la dropdown en face de **l’étiquette Recommandation** à droite de l’action d’amélioration. Vous verrez un résumé de l’environnement Microsoft 365 actuel de votre organisation lié à l’action d’amélioration, ainsi que les meilleures pratiques recommandées.

## <a name="resources"></a>Ressources

Pour plus d’informations sur l’installation, la configuration et l’utilisation de MCCA, voir les [instructions README](https://github.com/OfficeDev/MCCA#overview) sur GitHub (aucun compte GitHub requis).

Pour plus d’informations Windows PowerShell, commencez par utiliser [la documentation PowerShell.](https://docs.microsoft.com/powershell/scripting/how-to-use-docs?view=powershell-7) Voir aussi [Démarrage Windows PowerShell](https://docs.microsoft.com/powershell/scripting/windows-powershell/starting-windows-powershell?view=powershell-7).
