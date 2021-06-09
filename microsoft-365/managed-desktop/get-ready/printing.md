---
title: Préparer des ressources d’impression pour le Bureau géré Microsoft
description: Étapes importantes pour s’assurer que l’impression fonctionne correctement
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 971644aafabda733bf745fae278bdfeeed3282e3
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51574546"
---
# <a name="prepare-printing-resources-for-microsoft-managed-desktop"></a>Préparer des ressources d’impression pour le Bureau géré Microsoft

Lorsque vous êtes prêt à vous inscrire à Bureau géré Microsoft, vous devez évaluer vos besoins d’impression et déterminer l’approche qui convient à votre environnement. Vous avez trois options :
 
- Déployez la solution Impression universelle Microsoft pour faciliter la découverte des imprimantes Bureau géré Microsoft appareils. Pour plus d’informations, voir [Qu’est-ce que l’impression universelle](/universal-print/fundamentals/universal-print-whatis).
- Déployez les imprimantes directement à l’aide d’un script PowerShell personnalisé. Suivez les étapes de la section Configurer [les imprimantes locales.](#set-up-local-printers)
- Utilisez une solution d’impression cloud non Microsoft compatible avec Windows 10 appareils joints à un domaine Azure Active Directory microsoft. La solution doit répondre aux exigences logicielles requises pour Bureau géré Microsoft. Pour plus d’informations, [voir Bureau géré Microsoft’application requise.](../service-description/mmd-app-requirements.md)
 
Dans tous les cas, si les pilotes d’imprimante ne sont pas disponibles à partir de Microsoft Update ou de l’Microsoft Store, vous devez les obtenir vous-même et les empaquetés pour le déploiement sur vos appareils Bureau géré Microsoft avec Microsoft Intune. Pour plus d’informations, [voir Intune Autonome - Gestion des applications Win32](/mem/intune/apps/apps-win32-app-management)

## <a name="set-up-local-printers"></a>Configurer des imprimantes locales

Si vous avez décidé de déployer des imprimantes à l’aide d’un script PowerShell personnalisé et que vous avez préparé les ressources d’impression, suivez ces étapes pour déployer des imprimantes partagées :

1.  Accédez au portail Bureau géré Microsoft web.
2.  Envoyez une demande  de déploiement d’imprimante étiquetée dans la section > **support technique du** portail d’administration, en fournissant les informations suivantes :
    - Tous les chemins d’accès UNC vers les emplacements d’imprimante partagés qui devront être déployés pour Bureau géré Microsoft périphériques
    - Groupes d’utilisateurs qui nécessitent l’accès à ces imprimantes partagées
3.  À l’aide du portail d’administration, nous allons vous faire savoir que la demande est terminée. Initialement, nous allons uniquement déployer la configuration sur les appareils du groupe de déploiement Test.
4.  Vous devez tester et vérifier si la configuration fonctionne comme prévu. Répondez à **l’aide de l’onglet Discussion** dans la demande de support pour nous faire savoir quand vous avez terminé vos tests.
5.  Nous allons ensuite déployer la configuration sur les autres groupes de déploiement.

## <a name="steps-to-get-ready"></a>Étapes de préparation

1. Examiner [les conditions préalables pour Bureau géré Microsoft](prerequisites.md).
2. Utiliser [les outils d’évaluation de la préparation.](readiness-assessment-tool.md)
3. [Conditions préalables pour les comptes invité](guest-accounts.md)
4. [Configuration du réseau pour Bureau géré Microsoft](network.md)
5. [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft](certs-wifi-lan.md)
6. [Préparer l’accès aux ressources locales pour le Bureau géré Microsoft](authentication.md)
7. [Applications dans le Bureau géré Microsoft](apps.md)
8. [Préparer les lecteurs mappés pour le Bureau géré Microsoft](mapped-drives.md)
9. [Préparer les ressources d’impression Bureau géré Microsoft](printing.md) (Cet article)
