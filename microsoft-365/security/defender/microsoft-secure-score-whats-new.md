---
title: Nouveautés de Microsoft Secure Score
description: Décrit les nouvelles modifications apportées au score de sécurité Microsoft dans le portail Microsoft 365 Defender.
keywords: score de sécurité Microsoft, degré de sécurisation, score de sécurité Office 365, score de sécurité Microsoft, portail Microsoft 365 Defender
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.service: microsoft-365-security
ms.subservice: m365d
ms.author: siosulli
author: siosulli
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: e53c60cd2e1df2765a325f6ebe62089fe6f6b75c
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68643864"
---
# <a name="whats-new-in-microsoft-secure-score"></a>Nouveautés de Microsoft Secure Score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Pour que Microsoft Secure Score soit un meilleur représentant de votre posture de sécurité, nous continuons à ajouter de nouvelles fonctionnalités et des actions d’amélioration.

Plus vous effectuez d’actions d’amélioration, plus votre degré de sécurisation sera élevé. Pour plus d’informations, consultez [Microsoft Secure Score](microsoft-secure-score.md).

Le score de sécurité Microsoft se trouve dans <https://security.microsoft.com/securescore> le [portail Microsoft 365 Defender](microsoft-365-defender-portal.md).

## <a name="september-2022"></a>Septembre 2022

De nouvelles recommandations Microsoft Defender pour Office 365 pour les stratégies anti-hameçonnage sont désormais disponibles sous forme d’actions d’amélioration du degré de sécurisation :

- Définir le seuil de niveau d’e-mail d’hameçonnage sur 2 ou plus
- Activer la protection des utilisateurs usurpés d’identité
- Activer la protection du domaine usurpé d’identité
- Vérifier que l’intelligence de boîte aux lettres est activée
- Vérifier que l’intelligence pour la protection de l’emprunt d’identité est activée
- Messages de quarantaine détectés à partir d’utilisateurs usurpés d’identité
- Messages de quarantaine détectés à partir de domaines empruntés
- Déplacer des messages détectés comme des utilisateurs usurpés d’identité par l’intelligence de boîte aux lettres
- Activer l’option « Afficher le premier conseil de sécurité du contact »
- Activer l’info-bulle de sécurité d’emprunt d’identité de l’utilisateur
- Activer l’info-bulle de sécurité d’emprunt d’identité de domaine
- Activer le conseil de sécurité des caractères inhabituels d’emprunt d’identité de l’utilisateur

Une nouvelle recommandation SharePoint Online est désormais disponible en tant qu’action d’amélioration du degré de sécurisation :

- Déconnecter les utilisateurs inactifs dans SharePoint Online

## <a name="august-2022"></a>Août 2022

De nouvelles recommandations Protection des données Microsoft sont désormais disponibles sous forme d’actions d’amélioration du degré de sécurisation :

- **Étiquetage**
  - Étendre l’étiquetage de sensibilité M365 aux ressources dans la carte de données Azure Purview
  - Vérifier que les stratégies de classification des données d’étiquetage automatique sont configurées et utilisées
  - Publier des stratégies de classification des données d’étiquette de confidentialité M365
  - Créer des stratégies de protection contre la perte de données (DLP)

De nouvelles recommandations Microsoft Defender pour Office 365 sont désormais disponibles en tant qu’actions d’amélioration du degré de sécurisation :

- **Anti-spam - Stratégie de trafic entrant**
  - Définir le seuil de niveau de réclamation en bloc par e-mail (BCL) sur 6 ou inférieur
  - Définir une action pour effectuer la détection du courrier indésirable
  - Définir une action pour effectuer une détection de courrier indésirable à haut niveau de confiance
  - Définir une action pour effectuer la détection du hameçonnage
  - Définir une action pour effectuer une détection de hameçonnage à haut niveau de confiance
  - Définir l’action à entreprendre pour la détection du courrier indésirable en bloc
  - Conserver le courrier indésirable en quarantaine pendant 30 jours
  - Vérifier que les conseils de sécurité relatifs au courrier indésirable sont activés
  - Assurez-vous qu’aucun domaine d’expéditeur n’est autorisé pour les stratégies anti-courrier indésirable (remplacez « Assurez-vous qu’aucun domaine expéditeur n’est autorisé pour les stratégies anti-courrier indésirable » pour étendre la fonctionnalité également aux expéditeurs spécifiques)

- **Anti-spam - Stratégie de trafic sortant**
  - Définir le nombre maximal de destinataires externes qu’un utilisateur peut envoyer par e-mail par heure
  - Définir le nombre maximal de destinataires internes auxquels un utilisateur peut envoyer dans l’heure
  - Définir une limite quotidienne de messages
  - Bloquer les utilisateurs qui ont atteint la limite de messages
  - Définir les règles de transfert automatique de courrier électronique pour qu’ils soient contrôlés par le système

- **Anti-spam - Filtre de connexion**
  - N’ajoutez pas d’adresses IP autorisées dans la stratégie de filtre de connexion

## <a name="june-2022"></a>Juin 2022

- De nouvelles recommandations Microsoft Defender pour point de terminaison et Gestion des vulnérabilités Microsoft Defender sont désormais disponibles sous forme d’actions d’amélioration du degré de sécurisation :

  - Interdire l’accès hors connexion aux partages
  - Supprimer l’autorisation d’écriture de partage définie sur **Tout le monde**
  - Supprimer des partages du dossier racine
  - Définir l’énumération basée sur l’accès aux dossiers pour les partages
  - Mettre à jour Microsoft Defender pour point de terminaison composants principaux

- Une nouvelle recommandation Microsoft Defender pour Identity est disponible en tant qu’action d’amélioration du degré de sécurisation :

  - Résoudre les configurations de domaine non sécurisées

- Une nouvelle recommandation de [gouvernance des applications](/defender-cloud-apps/app-governance-manage-app-governance) est désormais disponible en tant qu’action d’amélioration du degré de sécurisation :

  - Réglementer les applications avec le consentement des comptes prioritaires

- Les nouvelles recommandations Salesforce et ServiceNow sont désormais disponibles en tant qu’actions d’amélioration du degré de sécurisation pour Microsoft Defender for Cloud Apps clients. Pour plus d’informations, consultez la [vue d’ensemble de SaaS Security Posture Management](https://aka.ms/saas_security_posture_management).

> [!NOTE]
> Les contrôles Salesforce et ServiceNow sont désormais disponibles en préversion publique.

## <a name="april-2022"></a>Avril 2022

- Activer l’authentification utilisateur pour les connexions à distance

## <a name="december-2021"></a>Décembre 2021

- Activer les pièces jointes sécurisées en mode bloc
- Empêcher le partage Exchange Online détails du calendrier avec des utilisateurs externes
- Activer les documents sécurisés pour les clients Office
- Activer le paramètre de filtre des pièces jointes courant pour les stratégies anti-programme malveillant
- Vérifier qu’aucun domaine d’expéditeur n’est autorisé pour les stratégies anti-courrier indésirable
- Créer des stratégies de liens sécurisés pour les messages électroniques
- Créer des stratégies de vidage automatique de zéro heure pour les programmes malveillants
- Activer Microsoft Defender pour Office 365 dans SharePoint, OneDrive et Microsoft Teams
- Créer des stratégies de vidage automatique de zéro heure pour les messages d’hameçonnage
- Créer des stratégies de vidage automatique de zéro heure pour les messages indésirables
- Bloquer l’abus de pilotes signés vulnérables exploités
- Activer l’analyse des lecteurs amovibles pendant une analyse complète

## <a name="we-want-to-hear-from-you"></a>Votre avis nous intéresse

Si vous rencontrez des problèmes, faites-le nous savoir en publiant dans la communauté [Sécurité, confidentialité et conformité](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous supervisons la communauté et vous fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Évaluer votre posture de sécurité](microsoft-secure-score-improvement-actions.md)
- [Suivez votre historique de score de sécurité Microsoft et répondez aux objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Ce qui est à venir](microsoft-secure-score-whats-coming.md)
