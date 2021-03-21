---
title: Service de localisation Windows 10
description: Comment faire pour que les services de localisation Windows sont allumés pour vos appareils
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 210356dd21b36efbb27d8faa4f8616145584159c
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50929500"
---
# <a name="windows-10-location-service"></a>Service de localisation Windows 10

Les appareils du Bureau géré Microsoft sont enregistrés à l’aide de Windows Autopilot. Ce processus nous permet de les gérer avec Azure Active Directory et Microsoft Intune. Par défaut, le service d’emplacement De Windows 10 est désactivé lorsqu’un appareil est activé pour la première fois, sauf si cette fonctionnalité est activée dans les paramètres de confidentialité pendant l'« expérience d’out-of-box ». Ces paramètres sont masqués lors de l’inscription Autopilot dans bureau géré Microsoft. Pour plus d’informations sur la façon dont Autopilot est installé, voir l’expérience de première expérience avec Autopilot et la page État de [l’inscription.](esp-first-run.md)

Pour cette raison, les appareils bureau géré Microsoft ne peuvent pas obtenir leur emplacement d’appareil, ce qui limite les fonctionnalités de plusieurs fonctionnalités Windows, telles que les fuseaux horaires. Pour plus d’informations sur le service d’emplacement Windows 10, voir [Service d’emplacement windows 10 et confidentialité.](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088)

Vous n’avez pas besoin d’utiliser le service de localisation pour participer au Bureau géré Microsoft, mais l’expérience utilisateur sera limitée. Par exemple, les appareils ne seront pas en mesure de déterminer automatiquement le fuseau horaire dans le cas où vos utilisateurs travaillent dans un autre fuseau horaire.

## <a name="enable-the-location-service"></a>Activer le service de localisation

Vous pouvez choisir d’utiliser le service de localisation lorsque vous inscrivez des appareils dans le service Bureau géré Microsoft ou vous pouvez activer ou désactiver le service après l’inscription.

### <a name="opt-in-during-enrollment"></a>S’inscrire lors de l’inscription

Le service Bureau géré Microsoft peut activer le service de localisation. Au cours de la séquence d’inscription, vous serez invité à choisir si vous souhaitez activer le service d’emplacement Windows 10 sur les appareils.

### <a name="control-the-location-service-after-enrollment"></a>Contrôler le service d’emplacement après l’inscription

Vous pouvez que le service d’emplacement soit allumé (ou désactivé) à tout moment en envoyant une demande de [support](../working-with-managed-desktop/admin-support.md) via le portail [d’administration.](access-admin-portal.md)

## <a name="how-microsoft-managed-desktop-configures-the-windows-10-location-service"></a>Comment Bureau géré Microsoft configure le service d’emplacement Windows 10

Si vous optez pour l’utilisation du service d’emplacement, nous utilisons les paramètres minimaux nécessaires sans affecter la confidentialité des utilisateurs. Pour plus d’informations, voir le service d’emplacement et la confidentialité [de Windows 10.](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088)

Bureau géré Microsoft active le paramètre de confidentialité **Emplacement** dans les **paramètres Windows** pour autoriser l’accès **à l’emplacement sur cet appareil.** L’interface utilisateur ressemble à ceci :

 :::image type="content" source="../../media/MMD-location-services-UI.png" alt-text="Paramètres d’emplacement dans les paramètres Windows":::

> [!NOTE]
> Si vous optez pour l’utilisation du service de localisation, cela s’applique uniquement au système d’exploitation Windows lui-même. Les applications ne sont pas autorisées à utiliser les services de localisation. Chaque utilisateur peut choisir d’autoriser ou non les applications à accéder à leur emplacement.