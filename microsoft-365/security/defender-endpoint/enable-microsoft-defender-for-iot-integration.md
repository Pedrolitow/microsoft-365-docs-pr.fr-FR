---
title: Intégrer Microsoft Defender pour IoT avec Microsoft Defender pour point de terminaison
description: Intégration avec Microsoft Defender pour IoT afin d’obtenir une visibilité et des évaluations de sécurité axées sur les appareils IoT.
keywords: activer le connecteur siem, siem, connecteur, informations de sécurité et événements
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f32d521fe83c9e72566228bb10efb37b851b6e05
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748074"
---
# <a name="onboard-with-microsoft-defender-for-iot"></a>Intégration avec Microsoft Defender pour IoT

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison P2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft Defender pour point de terminaison s’intègre désormais en toute transparence à Microsoft Defender pour IoT. Cette intégration étend vos fonctionnalités de découverte d’appareils avec les fonctionnalités de supervision sans agent fournies par Defender pour IoT. Cela permettra de sécuriser les appareils IoT d’entreprise connectés aux réseaux informatiques, tels que les appareils VoIP (Voice over Internet Protocol), les imprimantes et les caméras. Il permet aux organisations de tirer parti d’une solution intégrée unique qui sécurise l’ensemble de leur infrastructure IoT et de technologie opérationnelle (OT). Pour plus d’informations, consultez [Protection réseau IoT Entreprise](/azure/defender-for-iot/organizations/overview-eiot).

Une fois que vous avez défini un plan Defender pour IoT et configuré un capteur réseau IoT d’entreprise, les données d’appareil démarrent automatiquement le streaming dans les portails Defender pour point de terminaison et Defender pour IoT. 

L’intégration de Defender pour IoT offre une visibilité accrue pour vous aider à localiser, identifier et sécuriser les appareils IoT dans votre réseau. Cela vous donnera une vue unifiée de votre inventaire OT/IoT complet avec le reste de vos appareils informatiques (stations de travail, serveurs et appareils mobiles).

Les clients qui ont intégré Defender pour IoT ont également des recommandations de sécurité pour les évaluations des vulnérabilités et les configurations incorrectes pour les appareils IoT.

## <a name="prerequisites"></a>Conditions préalables

Pour modifier les paramètres de votre intégration Defender pour point de terminaison, l’utilisateur doit avoir les rôles suivants :

- Administrateur général du locataire dans Azure Active Directory
- Administrateur de sécurité pour l’abonnement Azure qui sera utilisé pour l’intégration de Microsoft Defender pour IoT

## <a name="onboard-a-defender-for-iot-plan"></a>Intégrer un plan Defender pour IoT

1. Dans le volet de navigation du [https://security.microsoft.com](https://security.microsoft.com/) portail, sélectionnez **Paramètres** \> détection **d’appareil** \> **Enterprise IoT**.

1. Sélectionnez les options suivantes pour votre plan :

   - Sélectionnez l’abonnement Azure dans la liste des abonnements disponibles dans votre locataire Azure Active Directory où vous souhaitez ajouter un plan.

   - Sélectionnez un plan tarifaire, un engagement mensuel ou annuel, ou une version d’évaluation. Microsoft Defender pour IoT fournit un essai gratuit de 30 jours pour les 1 000 premiers appareils validés à des fins d’évaluation.

      Pour plus d’informations, consultez la [page de tarification de Microsoft Defender pour IoT](https://azure.microsoft.com/pricing/details/iot-defender/).
   
   - Sélectionnez le nombre d’appareils validés que vous souhaitez surveiller. Si vous avez sélectionné une version d’évaluation, cette section n’apparaît pas, car vous avez une valeur par défaut de 1 000 appareils.

## <a name="set-up-a-network-sensor"></a>Configurer un capteur réseau

Pour configurer un capteur réseau, votre abonnement Azure doit avoir un plan Defender pour IoT avec des appareils IoT d’entreprise ajoutés. Pour plus d’informations, consultez [Prise en main de Defender pour IoT](/azure/defender-for-iot/organizations/getting-started).

Pour ajouter un capteur réseau, sous **Configurer les capteurs réseau** , choisissez le lien **Microsoft Defender pour IoT** . Cela vous amène au processus d’installation du capteur d’intégration dans le Portail Azure. Pour plus d’informations, consultez [Prise en main d’Enterprise IoT](/azure/defender-for-iot/organizations/tutorial-getting-started-eiot-sensor).

## <a name="managing-your-iot-devices"></a>Gestion de vos appareils IoT

Pour afficher et gérer vos appareils IoT dans le [portail Microsoft 365 Defender](https://security.microsoft.com/) accédez à **l’inventaire** des appareils dans le menu de navigation **Points** de terminaison, puis sélectionnez l’onglet **Appareils IoT**.

Pour plus d’informations sur la façon d’afficher les appareils dans Defender pour IoT, consultez [Gérer vos appareils IoT avec l’inventaire des appareils pour les organisations](/azure/defender-for-iot/organizations/how-to-manage-device-inventory-for-organizations).


## <a name="view-devices-alerts-recommendations-and-vulnerabilities"></a>Afficher les appareils, les alertes, les recommandations et les vulnérabilités

Après avoir défini votre plan et configuré un capteur réseau, affichez les données détectées et les évaluations de sécurité aux emplacements suivants :

- Afficher les données d’appareil dans Defender pour point de terminaison ou Defender pour IoT
- Afficher les alertes, les recommandations et les vulnérabilités dans Defender pour point de terminaison

Pour plus d’informations, consultez la [page de tarification de Defender pour IoT](https://azure.microsoft.com/pricing/details/iot-defender/). 

## <a name="cancel-your-defender-for-iot-plan"></a>Annuler votre plan Defender pour IoT

Vous pouvez annuler votre plan Defender pour IoT à partir de la page des paramètres Defender pour point de terminaison dans le [https://security.microsoft.com](https://security.microsoft.com/) portail. Une fois que vous avez annulé votre plan, l’intégration s’arrête et vous n’obtiendrez plus de valeur d’évaluation de la sécurité dans Defender pour point de terminaison, ni ne détecterez de nouveaux appareils dans Defender pour IoT.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la découverte d’appareils](configure-device-discovery.md)
- [Forum aux questions sur la découverte d’appareils](device-discovery-faq.md)
