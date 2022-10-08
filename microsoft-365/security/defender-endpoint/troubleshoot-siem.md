---
title: Résoudre les problèmes d’intégration de l’outil SIEM dans Microsoft Defender pour point de terminaison
description: Résolvez les problèmes qui peuvent survenir lors de l’utilisation des outils SIEM avec Microsoft Defender pour point de terminaison.
keywords: résoudre les problèmes, siem, clé secrète client, secret
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: troubleshooting
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 0027544968ccc056698b0e09ecce5ce8a0f97427
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68228797"
---
# <a name="troubleshoot-siem-tool-integration-issues"></a>Résoudre des problèmes d’intégration de l’outil SIEM

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Vous devrez peut-être résoudre les problèmes lors de l’extraction des détections dans vos outils SIEM.

Cette page fournit des étapes détaillées pour résoudre les problèmes que vous pouvez rencontrer.

## <a name="learn-how-to-get-a-new-client-secret"></a>Découvrez comment obtenir une nouvelle clé secrète client

Si votre clé secrète client expire ou si vous avez mal placé la copie fournie lorsque vous activiez l’application d’outil SIEM, vous devez obtenir un nouveau secret.

1. Connectez-vous au [portail de gestion Azure](https://portal.azure.com).

2. Sélectionnez **Azure Active Directory**.

3. Sélectionnez votre locataire.

4. Cliquez sur **inscriptions d'applications**. Ensuite, dans la liste des applications, sélectionnez l’application.

5. Sélectionnez **Certificats & section Secrets** , cliquez sur Nouveau secret client, puis fournissez une description et spécifiez la durée de validité.

6. Cliquez sur **Enregistrer**. La valeur de clé s’affiche.

7. Copiez la valeur et enregistrez-la dans un endroit sûr.

## <a name="error-when-getting-a-refresh-access-token"></a>Erreur lors de l’obtention d’un jeton d’accès d’actualisation

Si vous rencontrez une erreur lors de la tentative d’obtention d’un jeton d’actualisation lors de l’utilisation de l’API Threat Intelligence ou des outils SIEM, vous devez ajouter l’URL de réponse pour l’application appropriée dans Azure Active Directory.

1. Connectez-vous au [portail de gestion Azure](https://ms.portal.azure.com).

2. Sélectionnez **Azure Active Directory**.

3. Sélectionnez votre locataire.

4. Cliquez sur **Inscriptions d’applications**. Ensuite, dans la liste des applications, sélectionnez l’application.

5. Ajoutez l’URL suivante :
   - Pour l’Union européenne : `https://winatpmanagement-eu.securitycenter.windows.com/UserAuthenticationCallback`
   - Pour le Royaume-Uni : `https://winatpmanagement-uk.securitycenter.windows.com/UserAuthenticationCallback`
   - Pour le États-Unis : `https://winatpmanagement-us.securitycenter.windows.com/UserAuthenticationCallback`.

6. Cliquez sur **Enregistrer**.

## <a name="error-while-enabling-the-siem-connector-application"></a>Erreur lors de l’activation de l’application de connecteur SIEM

Si vous rencontrez une erreur lors de la tentative d’activation de l’application de connecteur SIEM, vérifiez les paramètres du bloqueur contextuel de votre navigateur. Il peut bloquer l’ouverture de la nouvelle fenêtre lorsque vous activez la fonctionnalité.

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshootsiem-belowfoldlink)

## <a name="related-topics"></a>Voir aussi

- [Détections d’extraction vers vos outils SIEM](configure-siem.md)

