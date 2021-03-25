---
title: Résoudre les problèmes d’intégration de l’outil SIEM dans Microsoft Defender ATP
description: Résoudre les problèmes qui peuvent survenir lors de l’utilisation des outils SIEM avec Microsoft Defender ATP.
keywords: résoudre les problèmes, siem, secret client, secret
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: c1c8fdb0b6e84d4265defb95d91b59a584b7f4c2
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51185778"
---
# <a name="troubleshoot-siem-tool-integration-issues"></a>Résoudre les problèmes d’intégration de l’outil SIEM

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 

Vous devrez peut-être résoudre les problèmes lors de l’analyse des détections dans vos outils SIEM.

Cette page fournit des étapes détaillées pour résoudre les problèmes que vous pourriez rencontrer.


## <a name="learn-how-to-get-a-new-client-secret"></a>Découvrez comment obtenir une nouvelle secret client
Si votre secret client expire ou si vous avez mal placé la copie fournie lorsque vous activiez l’application d’outil SIEM, vous devez obtenir une nouvelle question secrète.

1. Connectez-vous au [portail de gestion Azure.](https://portal.azure.com)

2. Sélectionner **Azure Active Directory**.

3. Sélectionnez votre client.

4. Cliquez **sur Inscriptions d’applications.** Ensuite, dans la liste des applications, sélectionnez l’application.

5. Section **Sélectionner des** clés, puis fournir une description de la clé et spécifier la durée de validité de la clé.

6. Cliquez sur **Enregistrer**. La valeur de clé s’affiche.

7. Copiez la valeur et enregistrez-la dans un endroit sûr.


## <a name="error-when-getting-a-refresh-access-token"></a>Erreur lors de l’obtention d’un jeton d’accès d’actualisation
Si vous rencontrez une erreur lors de la tentative d’obtenir un jeton d’actualisation lors de l’utilisation de l’API d’intelligence des menaces ou des outils SIEM, vous devez ajouter une URL de réponse pour l’application pertinente dans Azure Active Directory.

1. Connectez-vous au [portail de gestion Azure.](https://ms.portal.azure.com)

2. Sélectionner **Azure Active Directory**.

3. Sélectionnez votre client.

4. Cliquez **sur Inscriptions d’applications.** Ensuite, dans la liste des applications, sélectionnez l’application.

5. Ajoutez l’URL suivante :
   - Pour l’Union européenne : `https://winatpmanagement-eu.securitycenter.windows.com/UserAuthenticationCallback`
   - Pour le Royaume-Uni : `https://winatpmanagement-uk.securitycenter.windows.com/UserAuthenticationCallback`
   - Pour les États-Unis  `https://winatpmanagement-us.securitycenter.windows.com/UserAuthenticationCallback` : .
 
6. Cliquez sur **Enregistrer**.

## <a name="error-while-enabling-the-siem-connector-application"></a>Erreur lors de l’activation de l’application de connecteur SIEM
Si vous rencontrez une erreur lors de la tentative d’activer l’application de connecteur SIEM, vérifiez les paramètres du bloqueur de fenêtres d’accès rapide de votre navigateur. Il peut bloquer l’ouverture de la nouvelle fenêtre lorsque vous activez la fonctionnalité.




>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-troubleshootsiem-belowfoldlink) 

## <a name="related-topics"></a>Voir aussi
- [Activer l’intégration SIEM dans Microsoft Defender pour endpoint](enable-siem-integration.md)
- [Configurer ArcSight pour tirer Microsoft Defender pour les détections de points de terminaison](configure-arcsight.md)
- [Tirer les détections vers vos outils SIEM](configure-siem.md)
- [Champs Microsoft Defender pour la détection des points de terminaison](api-portal-mapping.md)
- [Détecter Microsoft Defender pour les points de terminaison à l’aide de l’API REST](pull-alerts-using-rest-api.md)
