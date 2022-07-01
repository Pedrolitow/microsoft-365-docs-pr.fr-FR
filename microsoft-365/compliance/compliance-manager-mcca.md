---
title: Analyseur de configuration pour Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment utiliser Configuration Analyzer pour Microsoft Purview pour être opérationnel rapidement avec le Gestionnaire de conformité Microsoft Purview.
ms.openlocfilehash: d2e5fbc0d928fb5931139a274cf9cce5bdc4d983
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573944"
---
# <a name="configuration-analyzer-for-microsoft-purview-camp"></a>Analyseur de configuration pour Microsoft Purview (CAMP)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Dans cet article :** Découvrez comment installer et exécuter l’outil Configuration Analyzer for Microsoft Purview (CAMP) pour commencer rapidement avec Microsoft Purview Compliance Manager.

## <a name="compliance-configuration-analyzer-camp-overview"></a>Vue d’ensemble de l’analyseur de configuration de conformité (CAMP)

L’analyseur de configuration pour Microsoft Purview (CAMP) est un outil qui peut vous aider à bien démarrer avec [le Gestionnaire de conformité Microsoft Purview](compliance-manager.md). CAMP est un utilitaire Basé sur PowerShell qui récupère les configurations actuelles de votre organisation et les valide par rapport aux meilleures pratiques recommandées par Microsoft 365. Ces meilleures pratiques sont basées sur un ensemble de contrôles qui incluent des réglementations et des normes clés pour la protection des données et la gouvernance des données.

CAMP peut vous aider à identifier rapidement les actions d’amélioration du Gestionnaire de conformité qui s’appliquent à votre environnement Microsoft 365 actuel. Chaque action identifiée par CAMP vous fournira des recommandations pour l’implémentation, avec des liens directs vers le Gestionnaire de conformité et la solution applicable pour commencer à prendre des mesures correctives.

Pour plus d’informations sur CAMP, notamment les prérequis et les instructions d’installation complètes, consultez les [instructions README sur GitHub](https://github.com/OfficeDev/CAMP#overview). Vous n’avez pas besoin d’un compte GitHub pour accéder à cette page.

#### <a name="availability"></a>Disponibilité
CAMP est disponible pour toutes les organisations disposant de licences Office 365 et Microsoft 365 et des clients de la Communauté du gouvernement des États-Unis (GCC) Moderate, GCC High et Department of Defense (DoD).

#### <a name="roles"></a>Rôles

Certains rôles d’utilisateur sont nécessaires pour accéder à CAMP et l’utiliser, ainsi que pour accéder aux informations dans les rapports. Consultez les [informations sur les prérequis de CAMP sur GitHub](https://github.com/OfficeDev/CAMP#pre-requisites).

## <a name="install-camp-and-run-a-report"></a>Installer CAMP et exécuter un rapport

Vous pouvez installer l’outil CAMP à l’aide de Windows PowerShell. Une fois que vous avez téléchargé et installé l’outil, vous n’avez pas besoin de répéter ces étapes pour exécuter des rapports. Chaque fois que vous ouvrez CAMP, il vous demande de vous connecter et génère un nouveau rapport mis à jour.

### <a name="step-1-install-the-exchange-online-powershell-v2-module"></a>Étape 1 : Installer le module Exchange Online PowerShell V2

Pour commencer, vous aurez besoin du module PowerShell Exchange Online (v2.0.3 ou version ultérieure) disponible dans la galerie PowerShell. Pour obtenir des instructions d’installation, consultez [Installer et gérer le module EXO V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

### <a name="step-2-install-camp"></a>Étape 2 : Installer CAMP

Pour installer CAMP, commencez par utiliser PowerShell en mode administrateur. Suivez les étapes ci-dessous :

1. Sélectionnez le bouton **Démarrer** de Windows.
1. Tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell**, puis sélectionnez **Exécuter en tant qu’administrateur**.
1. À l’invite de commandes, tapez :

    ```powershell
    Install-Module -Name CAMP
    ```

### <a name="step-3-run-a-report"></a>Étape 3 : Exécuter un rapport

Après avoir installé CAMP, vous pouvez exécuter CAMP et générer un rapport. Pour exécuter un rapport :

1. Ouvrir PowerShell
2. Exécutez l’applet de commande :

    ```powershell
    Get-CAMPReport
    ```

    Si vous êtes un client GCC High, vous devez fournir un paramètre d’entrée supplémentaire pour exécuter le rapport :

    ```powershell
    Get-CAMPReport -ExchangeEnvironmentName O365USGovGCCHigh
    ```

3. Une fois camp exécuté, il effectue une vérification de version initiale et demande des informations d’identification. À l’invite entrée du nom d’utilisateur, connectez-vous avec votre adresse e-mail de compte Microsoft 365 ([affichez les rôles éligibles pour créer des rapports](https://github.com/OfficeDev/CAMP#pre-requisites)). Entrez ensuite votre mot de passe à l’invite de mot de passe.

La génération de votre rapport prendra ensuite environ 2 à 5 minutes. Une fois l’opération terminée, une fenêtre de navigateur s’ouvre et affiche votre rapport HTML. Chaque fois que vous exécutez l’outil, il vous demande vos informations d’identification et génère un nouveau rapport. Ce rapport est stocké localement dans le répertoire C: \ Users \ *username* \ AppData \ Local \ Microsoft \ CAMP.

Vous pouvez accéder aux rapports précédemment générés à partir de ce répertoire.

## <a name="understanding-your-report"></a>Présentation de votre rapport

Votre rapport reflète les données en fonction de la date et de l’heure auxquelles elles ont été générées. La section supérieure fournit des détails sur le moment où elle a été générée, le nom de votre organisation et l’ID de locataire.

### <a name="geolocation-based-reporting"></a>Rapports basés sur la géolocalisation

La section **Note** indique que votre rapport est personnalisé en fonction de l’emplacement géographique de votre locataire. Les recommandations répertoriées dans l’outil seront spécifiques à votre pays ou région.

Votre sélection de géolocalisation est utilisée pour évaluer les types d’informations sensibles (SIT) qui sont pertinents pour cette géolocalisation et générer un rapport qui s’aligne sur votre pays ou région. Choisissez des géolocalisations en fonction des données que vous avez dans votre locataire.

Pour modifier les informations d’emplacement de votre rapport, vous devez fournir un paramètre d’entrée de géolocalisation (-Geo). Vous pouvez choisir une ou plusieurs géolocalisations applicables à votre locataire.

Suivez ces instructions pour exécuter un rapport en fonction d’un emplacement spécifique :

1. Ouvrir PowerShell
2. Pour spécifier une certaine région, vous allez exécuter une applet de commande à l’aide des nombres du tableau ci-dessous qui correspondent au pays ou à la région. Entrez plusieurs nombres en les séparant par une virgule. Par exemple, l’applet de commande ci-dessous exécute un rapport personnalisé pour Asia-Pacific et le Japon :

    ```powershell
    Get-CAMPReport -Geo @(1,7)
    ```

  | Input |  Pays ou région |
  | :------------- | :------------: |
  | 1 | Asie-Pacifique |
  | 2 | Australie |
  | 3 | Canada |
  | 4 | Europe (hors France) / Moyen-Orient / Afrique |
  | 5 | France |
  | 6  | Inde |
  | 7  | Japon |
  | 8  | Corée |
  | 9  | Amérique du Nord (à l’exception du Canada) |
  | 10 | Amérique du Sud |
  | 11 | Afrique du Sud |
  | 12  | Suisse |
  | 13 | Émirats arabes unis |
  | 14 | Royaume-Uni |

  > [!NOTE]
  > Le rapport inclut toujours les types d’informations sensibles internationaux pris en charge par CAMP, tels que le code SWIFT, le numéro de carte de crédit, etc.

### <a name="role-based-reporting"></a>Création de rapports en fonction du rôle

Votre rapport sera également personnalisé en fonction de votre rôle. Les [informations préalables de CAMP sur GitHub](https://github.com/OfficeDev/CAMP#pre-requisites) décrivent les rôles qui ont accès aux sections du rapport. D’autres rôles au sein de votre organisation peuvent ne pas être en mesure d’exécuter l’outil, ou ils peuvent exécuter l’outil et avoir un accès limité aux informations dans le rapport final.

### <a name="solutions-summary-section"></a>Section Résumé des solutions

La section **Récapitulatif des solutions** du rapport donne une vue d’ensemble des actions d’amélioration que votre organisation peut prendre dans le Gestionnaire de conformité pour améliorer votre posture de conformité.

![MCCA - Récapitulatif des solutions.](../media/compliance-manager-mcca-solutions.png "Écran Résumé des solutions CAMP")

CAMP évalue vos configurations actuelles par rapport aux actions d’amélioration recommandées dans le Gestionnaire de conformité. Toute action d’amélioration identifiée par l’outil CAMP comme nécessitant une attention particulière sera répertoriée dans cette section.

À côté de chaque solution Microsoft se trouvent des zones codées en couleurs indiquant le nombre d’éléments qui correspondent aux actions d’amélioration dans le Gestionnaire de conformité. Les actions sont divisées en trois états d’état :

- **OK** : les actions qui répondent aux conditions recommandées et qui n’ont pas besoin d’attention pour l’instant
- **Amélioration** : actions qui nécessitent une attention particulière
- **Recommandation** : actions qui n’ont pas besoin d’attention, mais pour lesquelles nous recommandons les meilleures pratiques

Sélectionnez une zone pour afficher les améliorations et les recommandations.

#### <a name="items-with-the-improvement-status"></a>Éléments avec l’état d’amélioration

Sélectionnez la liste déroulante en regard de l’étiquette **d’amélioration** à droite de l’action d’amélioration. Vous verrez un résumé rapide et des détails sur vos paramètres actuels et les actions d’amélioration recommandées. Le résumé inclut des liens directs vers le Gestionnaire de conformité, la solution applicable dans le portail de conformité Microsoft Purview et la documentation pertinente.

La sélection du lien Gestionnaire de conformité vous permet d’accéder à une vue filtrée de toutes les actions d’amélioration au sein de cette solution que vous n’avez pas encore implémentées. À partir de là, vous pouvez voir le nombre de points que vous pouvez atteindre pour augmenter votre [score de conformité](compliance-score-calculation.md), les évaluations aux laquelle ils s’appliquent, ainsi que les réglementations et certifications applicables.

Pour DLP, il existe un bouton **Script de correction** qui vous donne un script PowerShell pré-généré en fonction de ce qui est recommandé. Vous pouvez le copier et le coller directement dans votre console PowerShell. Il crée une stratégie DLP en mode test

#### <a name="items-with-recommendation-status"></a>Éléments avec l’état Recommandation

Sélectionnez la liste déroulante en regard de l’étiquette **Recommandation** à droite de l’action d’amélioration. Vous verrez un résumé de l’environnement Microsoft 365 actuel de votre organisation lié à l’action d’amélioration, ainsi que les meilleures pratiques recommandées.

## <a name="resources"></a>Ressources

Pour plus d’informations sur l’installation, la configuration et l’utilisation de CAMP, consultez les [instructions README sur GitHub](https://github.com/OfficeDev/CAMP#overview) (aucun compte GitHub requis).

Pour plus d’informations sur Windows PowerShell, [commencez par utiliser la documentation PowerShell](/powershell/scripting/how-to-use-docs). Voir aussi [Démarrage Windows PowerShell](/powershell/scripting/windows-powershell/starting-windows-powershell).
