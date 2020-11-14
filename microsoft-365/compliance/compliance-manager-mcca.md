---
title: Analyseur de configuration de conformité Microsoft pour le gestionnaire de conformité
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
description: Comprendre comment utiliser l’analyseur de configuration de conformité Microsoft pour être rapidement opérationnel avec le gestionnaire de conformité Microsoft.
ms.openlocfilehash: 1f7d987262a7d390cb9efe2162ae9be9f56c8757
ms.sourcegitcommit: d333d82fd5e4f3265e8b9372094e85875bee6fe5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "49071997"
---
# <a name="microsoft-compliance-configuration-analyzer-for-compliance-manager"></a>Analyseur de configuration de conformité Microsoft pour le gestionnaire de conformité

**Dans cet article :** Découvrez comment installer et exécuter l’outil Microsoft Compliance configurer Analyzer pour démarrer rapidement avec le gestionnaire de conformité Microsoft.

## <a name="microsoft-compliance-configuration-analyzer-mcca-overview"></a>Vue d’ensemble de Microsoft Compliance Configuration Analyzer (MCCA)

Microsoft Compliance Configuration Analyzer (MCCA) est un outil qui peut vous aider à commencer à utiliser le [Gestionnaire de conformité Microsoft](compliance-manager.md). MCCA est un utilitaire PowerShell qui récupère les configurations actuelles de votre organisation et les valide par rapport aux meilleures pratiques recommandées de Microsoft 365. Ces meilleures pratiques sont basées sur un ensemble de contrôles qui incluent des normes et des réglementations clés en matière de protection des données et de gouvernance des données.

MCCA peut vous aider à identifier rapidement les actions d’amélioration dans le gestionnaire de conformité qui s’appliquent à votre environnement Microsoft 365 actuel. Chaque action identifiée par MCCA vous donnera des recommandations pour l’implémentation, avec des liens directs vers le gestionnaire de conformité et la solution applicable pour commencer à prendre des mesures correctives.

Une ressource supplémentaire pour comprendre MCCA est en visitant les [instructions du fichier Lisez-moi sur GitHub](https://github.com/OfficeDev/MCCA#overview). Cette page fournit des informations détaillées sur les conditions préalables et fournit des instructions d’installation complètes. Vous n’avez pas besoin d’un compte GitHub pour accéder à cette page.

## <a name="install-mcca-and-run-a-report"></a>Installer MCCA et exécuter un rapport

Vous pouvez installer l’outil MCCA à l’aide de Windows PowerShell. Une fois que vous avez téléchargé et installé l’outil, vous n’avez pas besoin de répéter ces étapes pour exécuter des rapports. Chaque fois que vous ouvrez MCCA, vous êtes invité à entrer vos informations d’identification de connexion, et il génère un nouveau rapport mis à jour.

#### <a name="step-1-install-windows-powershell"></a>Étape 1 : installer Windows PowerShell
Pour commencer, vous avez besoin du module Exchange Online PowerShell (v 2.0.3 ou version ultérieure) disponible dans la Galerie PowerShell. [Obtenir des instructions d’installation](https://www.powershellgallery.com/packages/ExchangeOnlineManagement/2.0.3).

#### <a name="step-2-install-mcca"></a>Étape 2 : installer MCCA

Pour installer MCCA, commencez par utiliser PowerShell en mode administrateur. Suivez les étapes ci-dessous :

1. Sélectionnez le bouton **Démarrer** de Windows.
2. Tapez **PowerShell** , cliquez avec le bouton droit sur **Windows PowerShell** , puis sélectionnez **exécuter en tant qu’administrateur**.
1. Depuis l’invite de commandes, tapez :

    ```powershell
    Install-Module -Name MCCAPreview
    ```

#### <a name="step-3-run-a-report"></a>Étape 3 : exécuter un rapport

Une fois que vous avez installé MCCA, vous pouvez exécuter MCCA et générer un rapport. Pour exécuter un rapport :

1. Ouvrir PowerShell
2. Exécutez l’applet de commande :

    ```powershell
    Get-MCCAReport
    ```
3. Une fois que MCCA s’exécute, il effectue une vérification de version initiale et demande des informations d’identification. À l’invite d’entrée du nom d’utilisateur, connectez-vous avec votre adresse de messagerie de compte Microsoft 365 ([Affichez les rôles autorisés à créer des rapports](#role-based-reporting)). Ensuite, entrez votre mot de passe à l’invite de mot de passe.

La génération de votre rapport prendra environ 2-5 minutes. Une fois l’opération terminée, une fenêtre de navigateur s’ouvre et affiche votre rapport HTML. Chaque fois que vous exécutez l’outil, il vous demande des informations d’identification et génère un nouveau rapport. Ce rapport est stocké localement dans le répertoire suivant :

C:\Users \<username> \AppData\Local\Microsoft\MCCA. 

Vous pouvez accéder aux rapports générés précédemment à partir de ce répertoire.

## <a name="understanding-your-report"></a>Présentation de votre rapport

Votre rapport reflète les données en fonction de la date et de l’heure auxquelles elles ont été générées. La section supérieure fournit des informations sur le moment où il a été généré, le nom de votre organisation et l’ID de client.

#### <a name="geolocation-based-reporting"></a>Création de rapports géolocalisation

La section **note** indique que votre rapport est personnalisé en fonction de l’emplacement géographique de votre client. Les recommandations indiquées dans l’outil seront propres à votre pays ou région.

Votre sélection de géolocalisation est utilisée pour évaluer les types d’informations sensibles qui sont pertinents pour cette géolocalisation et générer un rapport qui s’aligne sur votre pays ou région. Choisissez géolocalisation en fonction des données que vous avez dans votre client.

Pour modifier les informations d’emplacement de votre rapport, vous devez fournir un paramètre d’entrée géolocalisation (-géo). Vous pouvez choisir un ou plusieurs géolocalisation applicables à votre client.

Suivez ces instructions pour exécuter un rapport basé sur un emplacement spécifique :

1. Ouvrir PowerShell
2. Pour spécifier une région particulière, vous exécuterez une cmdlet en utilisant les numéros du tableau ci-dessous correspondant au pays ou à la région. Entrez plusieurs numéros en les séparant par une virgule. Par exemple, l’applet de commande ci-dessous exécutera un rapport personnalisé pour Asia-Pacific et le Japon :

    ```powershell
    Get-MCCAReport -Geo @(1,7)
    ```
  | Input |  Pays ou région | 
  | :------------- | :------------: |
  | 0,1 | Asie-Pacifique |
  | n°2 | Australie |
  | 3 | Canada |
  | 4  | Europe (à l’exception de la France)/Moyen-Orient/Afrique |
  | 5  | France |
  | 6  | Inde |
  | 7  | Japon |
  | 8  | Corée |
  | 9  | Amérique du Nord (hors Canada) |
  | 10  | Amérique du Sud |
  | 11  | Afrique du Sud |
  | 12  | Suisse |
  | 13  | Émirats arabes unis |
  | 14  | Royaume-Uni |


 > [!NOTE]
> Le rapport inclut toujours les types d’informations sensibles internationales prises en charge par MCCA, tels que le code SWIFT, le numéro de carte de crédit, etc.

#### <a name="role-based-reporting"></a>Création de rapports basés sur des rôles

Votre rapport sera également personnalisé en fonction de votre rôle.

Le tableau ci-dessous indique les rôles qui ont accès aux sections du rapport. Les autres rôles au sein de votre organisation (non mentionnés dans le tableau ci-dessous) peuvent ne pas être en mesure d’exécuter l’outil ou exécuter l’outil et disposer d’un accès limité aux informations dans le rapport final.

![MCCA-rôles](../media/compliance-manager-mcca-roles.png "Rôles MCCA")

Exceptions :
1. L’utilisateur ne peut pas générer de rapport pour IP à l’exception de la section « utiliser IRM pour Exchange Online ».
2. L’utilisateur pourra générer un rapport pour IP à l’exception de la section « utiliser IRM pour Exchange Online ».
3. L’utilisateur pourra générer un rapport pour IP à l’exception de la section « Activer la conformité de la communication dans O365 ».
4. L’utilisateur ne peut pas générer de rapport pour IP à l’exception de la section « Activer l’audit dans Office 365 ».
5. L’utilisateur pourra générer un rapport pour IP à l’exception de la section « Activer l’audit dans Office 365 ».

#### <a name="solutions-summary-section"></a>Section synthèse des solutions

La section **synthèse des solutions** du rapport offre une vue d’ensemble des actions d’amélioration que votre organisation peut effectuer dans le gestionnaire de conformité afin d’améliorer votre position de conformité.

![MCCA-Résumé des solutions](../media/compliance-manager-mcca-solutions.png "Écran de résumé des solutions MCCA")

MCCA évalue vos configurations actuelles par rapport aux actions d’amélioration recommandées dans le gestionnaire de conformité. Toute action d’amélioration identifiée par l’outil MCCA comme nécessitant une attention particulière est répertoriée dans cette section.

En regard de chaque solution Microsoft se trouvent des zones codées en couleur indiquant le nombre d’éléments correspondant aux actions d’amélioration dans le gestionnaire de conformité. Les actions sont divisées en trois États d’État :

- **OK** : actions qui répondent aux conditions recommandées et ne nécessitent aucune attention pour le moment
- **Amélioration** : actions nécessitant une attention particulière
- **Recommandation** : actions qui ne nécessitent pas d’attention, mais pour lesquelles nous recommandons des pratiques recommandées
 
Sélectionnez une zone pour afficher les améliorations et les recommandations.

**Éléments avec l’état d’amélioration**

Sélectionnez la liste déroulante en regard de l’étiquette d' **amélioration** à droite de l’action d’amélioration. Vous verrez un résumé rapide et des détails sur vos paramètres actuels et les actions d’amélioration recommandées. Le résumé inclut des liens directs vers le gestionnaire de conformité, la solution applicable dans le centre de conformité Microsoft 365 et une documentation pertinente.

Le fait de cliquer sur le lien gestionnaire de conformité vous permet d’accéder à une vue filtrée de toutes les actions d’amélioration de cette solution que vous n’avez pas encore implémentées. À partir de là, vous pouvez voir le nombre de points que vous pouvez atteindre pour augmenter votre [score de conformité](compliance-score-calculation.md)et les évaluations auxquelles il s’applique, ainsi que les règlements et certifications applicables.

Pour DLP, il existe un bouton de **script de correction** qui vous donne un script PowerShell pré-généré en fonction de ce qui est recommandé. Vous pouvez la copier et la coller directement dans votre console PowerShell. Il crée une stratégie DLP en mode test.

**Éléments avec le statut de recommandation**

Sélectionnez la liste déroulante en regard de l’étiquette de **recommandation** à droite de l’action d’amélioration. Vous verrez un résumé de l’environnement Microsoft 365 actuel de votre organisation lié à l’action d’amélioration, ainsi que les meilleures pratiques recommandées.

## <a name="resources"></a>Ressources

Pour plus d’informations sur l’installation, la configuration et l’utilisation de MCCA, consultez les [instructions du fichier Lisez-moi sur GitHub](https://github.com/OfficeDev/MCCA#overview) (aucun compte GitHub requis).

Pour plus d’informations sur Windows PowerShell, consultez la [rubrique How to use the PowerShell documentation](https://docs.microsoft.com/powershell/scripting/how-to-use-docs?view=powershell-7). Voir aussi [démarrage de Windows PowerShell](https://docs.microsoft.com/powershell/scripting/windows-powershell/starting-windows-powershell?view=powershell-7).
