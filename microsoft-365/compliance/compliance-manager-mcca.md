---
title: Microsoft Compliance Configuration Analyzer for Compliance Manager
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
description: Découvrez comment utiliser Microsoft Compliance Configuration Analyzer pour être opérationnel rapidement avec le Gestionnaire de conformité Microsoft Purview.
ms.openlocfilehash: a973412c2d40993b47343273675cee3922b57cdf
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012811"
---
# <a name="microsoft-compliance-configuration-analyzer-for-compliance-manager-preview"></a>Microsoft Compliance Configuration Analyzer for Compliance Manager (préversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Dans cet article :** Découvrez comment installer et exécuter l’outil Microsoft Compliance Configure Analyzer pour commencer rapidement avec Microsoft Compliance Manager.

## <a name="microsoft-compliance-configuration-analyzer-mcca-preview-overview"></a>Vue d’ensemble de Microsoft Compliance Configuration Analyzer (MCCA) (préversion)

Microsoft Compliance Configuration Analyzer (MCCA) est un outil en préversion qui peut vous aider à prendre en main [le Gestionnaire de conformité Microsoft Purview](compliance-manager.md). MCCA est un utilitaire Basé sur PowerShell qui récupère les configurations actuelles de votre organisation et les valide par rapport à Microsoft 365 meilleures pratiques recommandées. Ces meilleures pratiques sont basées sur un ensemble de contrôles qui incluent des réglementations et des normes clés pour la protection des données et la gouvernance des données.

MCCA peut vous aider à voir rapidement quelles actions d’amélioration du Gestionnaire de conformité s’appliquent à votre environnement Microsoft 365 actuel. Chaque action identifiée par MCCA vous fournira des recommandations pour l’implémentation, avec des liens directs vers le Gestionnaire de conformité et la solution applicable pour commencer à prendre des mesures correctives.

Une ressource supplémentaire pour comprendre MCCA consiste à consulter les [instructions README sur GitHub](https://github.com/OfficeDev/MCCA#overview). Cette page fournit des informations détaillées sur les prérequis et fournit des instructions d’installation complètes. Vous n’avez pas besoin d’un compte GitHub pour accéder à cette page.

**Disponibilité** : MCCA est disponible pour toutes les organisations disposant de licences Office 365 et Microsoft 365 et des Community du gouvernement des États-Unis (Cloud de la communauté du secteur public) modérés, Cloud de la communauté du secteur public  Clients de haut niveau et du ministère de la Défense (DoD).

## <a name="install-mcca-and-run-a-report"></a>Installer MCCA et exécuter un rapport

Vous pouvez installer l’outil MCCA à l’aide de Windows PowerShell. Une fois que vous avez téléchargé et installé l’outil, vous n’avez pas besoin de répéter ces étapes pour exécuter des rapports. Chaque fois que vous ouvrez MCCA, il vous demande vos informations d’identification de connexion et génère un nouveau rapport mis à jour.

### <a name="step-1-install-the-exchange-online-powershell-v2-module"></a>Étape 1 : Installer le module Exchange Online PowerShell V2

Pour commencer, vous aurez besoin du module PowerShell Exchange Online (v2.0.3 ou version ultérieure) disponible dans la galerie PowerShell. Pour obtenir des instructions d’installation, consultez [Installer et gérer le module EXO V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

### <a name="step-2-install-mcca"></a>Étape 2 : Installer MCCA

Pour installer MCCA, commencez par utiliser PowerShell en mode administrateur. Suivez les étapes ci-dessous :

1. Sélectionnez le bouton Windows **Démarrer**.
1. Tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell**, puis sélectionnez **Exécuter en tant qu’administrateur**.
1. À l’invite de commandes, tapez :

    ```powershell
    Install-Module -Name MCCAPreview
    ```

### <a name="step-3-run-a-report"></a>Étape 3 : Exécuter un rapport

Après avoir installé MCCA, vous pouvez exécuter MCCA et générer un rapport. Pour exécuter un rapport :

1. Ouvrir PowerShell
2. Exécutez l’applet de commande :

    ```powershell
    Get-MCCAReport
    ```

    Si vous êtes un client Cloud de la communauté du secteur public High, vous devez fournir un paramètre d’entrée supplémentaire pour exécuter le rapport :

    ```powershell
    Get-MCCAReport -ExchangeEnvironmentName O365USGovGCCHigh
    ```

3. Une fois MCCA exécuté, il effectue une vérification de version initiale et demande des informations d’identification. À l’invite Entrée du nom d’utilisateur, connectez-vous avec votre adresse e-mail de compte Microsoft 365 ([affichez les rôles éligibles pour créer des rapports](#role-based-reporting)). Entrez ensuite votre mot de passe à l’invite de mot de passe.

La génération de votre rapport prendra ensuite environ 2 à 5 minutes. Une fois l’opération terminée, une fenêtre de navigateur s’ouvre et affiche votre rapport HTML. Chaque fois que vous exécutez l’outil, il vous demande vos informations d’identification et génère un nouveau rapport. Ce rapport est stocké localement dans le répertoire C: \ Users \ *username* \ AppData \ Local \ Microsoft \ MCCA.

Vous pouvez accéder aux rapports précédemment générés à partir de ce répertoire.

## <a name="understanding-your-report"></a>Présentation de votre rapport

Votre rapport reflète les données en fonction de la date et de l’heure auxquelles elles ont été générées. La section supérieure fournit des détails sur le moment où elle a été générée, le nom de votre organisation et l’ID de locataire.

### <a name="geolocation-based-reporting"></a>Rapports basés sur la géolocalisation

La section **Note** indique que votre rapport est personnalisé en fonction de l’emplacement géographique de votre locataire. Recommandations répertoriés dans l’outil seront spécifiques à votre pays ou région.

Votre sélection de géolocalisation est utilisée pour évaluer les types d’informations sensibles (SIT) qui sont pertinents pour cette géolocalisation et générer un rapport qui s’aligne sur votre pays ou région. Choisissez des géolocalisations en fonction des données que vous avez dans votre locataire.

Pour modifier les informations d’emplacement de votre rapport, vous devez fournir un paramètre d’entrée de géolocalisation (-Geo). Vous pouvez choisir une ou plusieurs géolocalisations applicables à votre locataire.

Suivez ces instructions pour exécuter un rapport en fonction d’un emplacement spécifique :

1. Ouvrir PowerShell
2. Pour spécifier une certaine région, vous allez exécuter une applet de commande à l’aide des nombres du tableau ci-dessous qui correspondent au pays ou à la région. Entrez plusieurs nombres en les séparant par une virgule. Par exemple, l’applet de commande ci-dessous exécute un rapport personnalisé pour Asia-Pacific et le Japon :

    ```powershell
    Get-MCCAReport -Geo @(1,7)
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
  > Le rapport inclut toujours les types d’informations sensibles internationaux pris en charge par MCCA, tels que le code SWIFT, le numéro de carte de crédit, etc.

### <a name="role-based-reporting"></a>Création de rapports en fonction du rôle

Votre rapport sera également personnalisé en fonction de votre rôle.

Le tableau ci-dessous indique quels rôles ont accès aux sections du rapport. D’autres rôles au sein de votre organisation (non répertoriés dans le tableau ci-dessous) peuvent ne pas être en mesure d’exécuter l’outil, ou ils peuvent exécuter l’outil et avoir un accès limité aux informations dans le rapport final.

![MCCA - rôles.](../media/compliance-manager-mcca-roles.png "Rôles MCCA")

Exceptions :

1. Les utilisateurs ne pourront pas générer de rapport pour l’adresse IP en dehors de la section « Utiliser irm pour Exchange Online ».
2. Les utilisateurs pourront générer un rapport pour l’adresse IP en dehors de la section « Utiliser irm pour Exchange Online ».
3. Les utilisateurs pourront générer un rapport pour l’adresse IP en dehors de la section « Activer la conformité des communications dans O365 ».
4. Les utilisateurs ne pourront pas générer de rapport pour IP en dehors de la section « Activer l’audit dans Office 365 ».
5. Les utilisateurs pourront générer un rapport pour l’adresse IP en dehors de la section « Activer l’audit dans Office 365 ».

### <a name="solutions-summary-section"></a>Section Résumé des solutions

La section **Récapitulatif des solutions** du rapport donne une vue d’ensemble des actions d’amélioration que votre organisation peut prendre dans le Gestionnaire de conformité pour améliorer votre posture de conformité.

![MCCA - Récapitulatif des solutions.](../media/compliance-manager-mcca-solutions.png "Écran Récapitulatif des solutions MCCA")

MCCA évalue vos configurations actuelles par rapport aux actions d’amélioration recommandées dans le Gestionnaire de conformité. Toute action d’amélioration identifiée par l’outil MCCA comme nécessitant une attention particulière sera répertoriée dans cette section.

À côté de chaque solution Microsoft se trouvent des zones codées en couleurs indiquant le nombre d’éléments qui correspondent aux actions d’amélioration dans le Gestionnaire de conformité. Les actions sont divisées en trois états d’état :

- **OK** : les actions qui répondent aux conditions recommandées et qui n’ont pas besoin d’attention pour l’instant
- **Amélioration** : actions qui nécessitent une attention particulière
- **Recommandation** : actions qui n’ont pas besoin d’attention, mais pour lesquelles nous recommandons les meilleures pratiques

Sélectionnez une zone pour afficher les améliorations et les recommandations.

#### <a name="items-with-the-improvement-status"></a>Éléments avec l’état d’amélioration

Sélectionnez la liste déroulante en regard de l’étiquette **d’amélioration** à droite de l’action d’amélioration. Vous verrez un résumé rapide et des détails sur vos paramètres actuels et les actions d’amélioration recommandées. Le résumé inclut des liens directs vers le Gestionnaire de conformité, la solution applicable dans le portail de conformité Microsoft Purview et la documentation pertinente.

En cliquant sur le lien Gestionnaire de conformité, vous accédez à une vue filtrée de toutes les actions d’amélioration au sein de cette solution que vous n’avez pas encore implémentées. À partir de là, vous pouvez voir le nombre de points que vous pouvez atteindre pour augmenter votre [score de conformité](compliance-score-calculation.md), les évaluations aux laquelle ils s’appliquent, ainsi que les réglementations et certifications applicables.

Pour DLP, il existe un bouton **Script de correction** qui vous donne un script PowerShell pré-généré en fonction de ce qui est recommandé. Vous pouvez le copier et le coller directement dans votre console PowerShell. Il crée une stratégie DLP en mode test

#### <a name="items-with-recommendation-status"></a>Éléments avec l’état Recommandation

Sélectionnez la liste déroulante en regard de l’étiquette **Recommandation** à droite de l’action d’amélioration. Vous verrez un résumé de l’environnement Microsoft 365 actuel de votre organisation lié à l’action d’amélioration, ainsi que les meilleures pratiques recommandées.

## <a name="resources"></a>Ressources

Pour plus d’informations sur l’installation, la configuration et l’utilisation de MCCA, consultez les [instructions README sur GitHub](https://github.com/OfficeDev/MCCA#overview) (aucun compte GitHub requis).

Pour plus d’informations sur Windows PowerShell, [commencez par utiliser la documentation PowerShell](/powershell/scripting/how-to-use-docs). Voir aussi [Démarrage Windows PowerShell](/powershell/scripting/windows-powershell/starting-windows-powershell).
