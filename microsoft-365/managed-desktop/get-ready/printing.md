---
title: Préparer des ressources d’impression pour le Bureau géré Microsoft
description: Étapes importantes pour s’assurer que l’impression fonctionne correctement
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: a66075637a15eb39eda38e318070af2bcbdc8fe6
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2022
ms.locfileid: "62444520"
---
# <a name="prepare-printing-resources-for-microsoft-managed-desktop"></a>Préparer des ressources d’impression pour le Bureau géré Microsoft

Lorsque vous êtes prêt à vous inscrire à Microsoft Manged Desktop, vous devez évaluer vos besoins d’impression et déterminer l’approche qui convient à votre environnement. Vous avez trois options :

| Option | Description |
| ------ | ------ |
| Déployer la solution d’impression universelle Microsoft | La solution d’impression universelle Microsoft pour faciliter la découverte des imprimantes Microsoft Manged Desktop les appareils. Pour plus d’informations, voir [Qu’est-ce que l’impression universelle](/universal-print/fundamentals/universal-print-whatis) . |
| Déployer des imprimantes directement à l’aide d’un script PowerShell personnalisé | Suivez les étapes de la section Configurer [les imprimantes locales](#set-up-local-printers) . |
| Utiliser une solution d’impression cloud non Microsoft | Utilisez une solution d’impression cloud non Microsoft compatible avec Windows 10 et jointe à un domaine Azure Active Directory microsoft. La solution doit répondre aux exigences logicielles requises pour Microsoft Manged Desktop. Pour plus d’informations, [voir Microsoft Manged Desktop’application requise](../service-description/mmd-app-requirements.md). |

Dans toutes les options ci-dessus, si les pilotes d’imprimante ne sont pas disponibles à partir de Microsoft Update ou de l’Microsoft Store, vous devez les obtenir vous-même et les empaquetés pour le déploiement sur vos appareils Microsoft Manged Desktop avec Microsoft Intune. Pour plus d’informations, [voir Intune Autonome - Gestion des applications Win32](/mem/intune/apps/apps-win32-app-management)

## <a name="set-up-local-printers"></a>Configurer des imprimantes locales

Les instructions suivantes supposent que vous avez préparé les ressources d’impression et décidé de déployer des imprimantes à l’aide d’un script PowerShell personnalisé.

**Pour déployer des imprimantes à l’aide d’un script PowerShell personnalisé :**

1. Accédez au portail Microsoft Manged Desktop’entreprise.
1. Envoyez une demande de déploiement d’imprimante *étiquetée* dans la section **> support technique du** portail d’administration.
1. Fournissez les détails suivants :
    - Tous les chemins d’accès UNC vers les emplacements d’imprimante partagés qui devront être déployés pour Microsoft Manged Desktop périphériques.
    - Groupes d’utilisateurs qui nécessitent l’accès à ces imprimantes partagées.
1. À l’aide du portail d’administration, nous allons vous faire savoir que la demande est terminée. Initialement, nous allons uniquement déployer la configuration sur les appareils du groupe de déploiement Test.
1. Testez et confirmez si la configuration fonctionne comme prévu.
1. Répondez à **l’aide de l’onglet Discussion** dans la demande de support pour nous faire savoir quand vous avez terminé vos tests.
1. Nous allons ensuite déployer la configuration sur les autres groupes de déploiement.

## <a name="steps-to-get-ready"></a>Étapes de préparation

1. Examinez [Configuration requise pour le Bureau géré Microsoft](prerequisites.md).
1. Exécutez les [outils d’évaluation de la préparation](readiness-assessment-tool.md).
1. Achetez [Portail d’entreprise](../get-started/company-portal.md).
1. Passez en revue les [prérequis pour les comptes invités](guest-accounts.md).
1. Vérifiez la[configuration réseau](network.md).
1. [Préparer les certificats et les profils réseau](certs-wifi-lan.md).
1. [Préparer l’accès utilisateur aux données](authentication.md).
1. [Préparer les applications](apps.md).
1. [Préparer les lecteurs mappés](mapped-drives.md).
1. Préparer les ressources d’impression (cet article).
1. [noms d’appareil](address-device-names.md) d’une adresse.
