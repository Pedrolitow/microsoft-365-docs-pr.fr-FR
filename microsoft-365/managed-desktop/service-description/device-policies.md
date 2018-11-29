---
title: Configuration du périphérique
description: Découvrez les stratégies par défaut appliqués aux périphériques de bureau Microsoft.
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: jdeckerms
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 5a97f44641ac38a8785bde66819dbfffffee946d
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867286"
---
# <a name="device-configuration"></a>Configuration du périphérique


<!--This topic is the target for a "Learn more" link in the Enterprise Agreement (aka.ms/dev-config); do not delete.-->

<!-- Device configuration and Security Addendum-->

Lorsqu’un nouveau périphérique de bureau Microsoft est mise en service, nous assurer que la configuration, optimisée pour Microsoft de bureau, est en place. Cela inclut un ensemble de stratégies par défaut qui sont configurés dans le cadre du processus d’intégration. Pour éviter les conflits de ces stratégies ne doivent pas être modifiés. 

Appareils seront arrivent avec une image de signature, puis rejoindre le domaine Azure Active Directory lorsque le premier utilisateur se connecte. Le périphérique installe automatiquement stratégies requises et les applications sans aucune intervention de l’informatique nécessaire.

## <a name="why-mdm-over-group-policy"></a>Pourquoi Mobile Device Manager sur la stratégie de groupe

Il existe quelques raisons d’utiliser la gestion des appareils mobiles (Mobile Device Manager) au lieu de la stratégie de groupe :

- Sécurité - Stratégies Mobile Device Manager sont plus sécurisés dans le monde moderne. Stratégie de groupe est conçu pour un fonctionnement optimal avec l’identité locale. Mobile Device Manager est conçu pour un fonctionnement optimal avec la gestion des identités cloud (Azure Active Directory (AD Azure)).
- Fiabilité - stratégies de Mobile Device Manager permettent de déploiement de stratégie plus fiable. Paramètres de Mobile Device Manager remplacent les stratégies de l’objet de stratégie de groupe (GPO). Démarrage avec Windows 10, version 1803, Paramètres Mobile Device Manager auront la priorité sur les valeurs de la stratégie de groupe. Déplacement vers une gestion moderne des clients pris en charge. 
- Aligner avec vision de bureau Microsoft - mieux sur le déploiement de la stratégie de surveillance. Approche basée sur l’anneau progressivement les modifications de stratégie de déploiement prend en charge permettant de suspendre / reprendre déploiement lorsque cela est nécessaire.

## <a name="default-policies"></a>Stratégies par défaut

Ce tableau met en surbrillance les stratégies par défaut qui est appliqués à tous les périphériques de bureau Microsoft au cours de la configuration du périphérique. Pour éviter tout conflit, ces stratégies ne doivent pas être modifiés. Tous les détectés reprend les modifications non approuvées par l’équipe Microsoft gérées bureau opérations aux objets gérés par Microsoft de bureau.

Stratégie | Description
--- | ---
Guide de sécurité | [Guide de sécurité Microsoft](https://docs.microsoft.com/windows/device-security/windows-security-baselines) pour Mobile Device Manager est configuré pour tous les périphériques de bureau Microsoft. Cette ligne de base est la configuration standard de l’industrie. Il sera diffusé commercialement, bien testé, a été révisé par des experts de sécurité de Microsoft pour que les périphériques de bureau Microsoft et sécuriser les applications dans l’espace de travail moderne.<br><br>Afin d’atténuer les menaces dans le paysage des menaces de sécurité en constante évolution, le Guide de sécurité Microsoft sera mis à jour et déployé sur les périphériques de bureau Microsoft à chaque mise à jour de la fonctionnalité Windows 10.<br><br>Pour plus d’informations, voir le [Guide de sécurité pour Windows 10](https://blogs.technet.microsoft.com/secguide/2017/10/18/security-baseline-for-windows-10-fall-creators-update-v1709-final/).
Ordinateur de bureau Microsoft recommandé de modèle de sécurité | Un ensemble de modifications recommandées pour la sécurité de base permettant d’optimiser l’expérience utilisateur.  Ces modifications sont documentées dans [L’Addendum de sécurité](#security-addendum). Mises à jour à l’addendum stratégie se produisent sur selon vos besoins.  
Conformité de périphérique | Ces stratégies sont configurés par défaut pour tous les périphériques de bureau Microsoft. Un périphérique est indiqué comme non conformes lors d’une des conditions de sécurité suivantes n’est pas remplie :<br>-Le chiffrement BitLocker périphérique activé, pour protéger les données sur les périphériques. Pour plus d’informations, voir [vue d’ensemble de périphérique chiffrement BitLocker dans Windows 10.](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10)<br>-Initialisation sécurisée activée et appliquée, pour valider les images du microprogramme sur les périphériques avant qu’ils peuvent exécuter. Pour plus d’informations, voir [sécurisée présentation du chiffrement de démarrage et des périphériques.](https://docs.microsoft.com/windows-hardware/drivers/bringup/secure-boot-and-device-encryption-overview)<br>-Le mot de passe requis pour accéder aux périphériques de bureau Microsoft.
Déploiement de la mise à jour | Utilisez Windows Update pour les entreprises (WUfB) pour effectuer un déploiement progressif des mises à jour logicielles. Les administrateurs informatiques ne peuvent pas modifier les paramètres pour les stratégies de déploiement de sonnerie. Pour plus d’informations sur le déploiement en fonction de sonnerie, voir [la gestion des mises à jour](../working-with-managed-desktop/updates.md).
Télémétrie | Périphériques seront définis pour fournir des données de diagnostic améliorée à Microsoft sous un identificateur commercial connu. Pour les clients en général régions règlement de Protection de données (PIBR), les utilisateurs finaux peuvent réduire le niveau de données de diagnostic qui sont fournis. Vous pouvez personnaliser cette configuration, mais il y aura une réduction de service. Pour plus d’informations, voir [des données de diagnostic configurer Windows dans votre organisation.](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enhanced-level)

## <a name="advanced-policies"></a>Stratégies avancées

 Voici les stratégies supplémentaires qui peuvent être configurées pour un environnement plus sécurisé/verrouillé, pour les secteurs hautement régulé.

 Stratégie | Description
 --- | ---
 Fonctionnalités avancées | Protection des informations de Windows (TEC) & Azure informations Protection (AIP) sont utilisées pour protéger les données d’entreprise, en autorisant uniquement l’accès à certaines personnes ou un sous-ensemble des applications de service. Pour plus d’informations, voir<br>- [Protéger les données de votre entreprise à l’aide de la Protection des informations](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip)<br>- [Guide d’administrateur Azure la Protection des informations client](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)<br>- [Microsoft gérées sécurité bureautique Addendum](#security-addendum)

 ## <a name="security-addendum"></a>Addendum de sécurité

 Cette section présente les stratégies qui seront déployés comme supplémentaires aux stratégies de bureau Microsoft standards. Stratégies standards sont répertoriés dans [les stratégies par défaut](#default-policies). Cette configuration est conçue avec les Services financiers et hautement régulé secteurs d’activité à l’esprit : optimisation de la position la plus sécurisée, tout en maintenant la productivité des utilisateurs.

Dans une modification dans le **Guide de sécurité**de publié, le paramètre [**ne pas afficher l’interface utilisateur de sélection de réseau**](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowslogon#windowslogon-dontdisplaynetworkselectionui) sera désactivé.

 ### <a name="additional-security-policies"></a>Stratégies de sécurité supplémentaires

 Ces stratégies sont ajoutées pour renforcer la sécurité pour les secteurs hautement régulé. 
 - **Application de liste verte**: applications doivent être approuvées par l’organisation à exécuter sur les périphériques de bureau Microsoft. Il fournit un environnement verrouillé. Les applications qui doivent être onboarded doivent être communiquées à l’équipe des opérations Microsoft géré du bureau. Pour plus d’informations, voir [Windows Defender périphérique Guard](https://docs.microsoft.com/windows/device-security/device-guard/device-guard-deployment-guide).
 - **Surveillance de la sécurité**: Microsoft surveillera périphériques à l’aide de [Windows Defender avancée protection contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection). Si une menace est détectée, Microsoft avertir le client, isoler le périphérique et corriger le problème à distance. 
 - **Protection contre les exploiter**: nous permet de garantir que les périphériques de bureau Microsoft sont toujours sécurisées avec la dernière mise à jour de sécurité, système d’exploitation et applications, à l’aide de [Windows Update pour les entreprises](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb). Exploiter Guard sera configuré avec ces paramètres :

 Paramètre | Stratégie
 --- | ---
 Marquer les informations d’identification de vol à partir du sous-système d’autorité de sécurité locale Windows | Audit uniquement
 Applications Office injection dans d’autres processus | Audit uniquement
 Création d’un contenu exécutable applications/macros Office | Bloc
 Lancement du processus enfants les applications Office | Audit uniquement
 Win32 importe Office code de macro | Bloc
 Code js/vbs/ps/macro masqué | Bloc
 L’exécution de charge utile js/vbs téléchargé à partir d’internet (sans exception) | Bloc
 Création du processus de commandes PSExec et WMI | Audit uniquement
 Non approuvés et les processus qui s’exécutent de USB | Bloc
 Fichiers exécutables qui ne répondent pas aux critères de la liste approuvée, âge ou une fréquence | Audit uniquement
 L’exécution d’un contenu exécutable supprimés du courrier électronique | Bloc
 Protection avancée des logiciels | Audit uniquement









