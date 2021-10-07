---
title: Service d’emplacement Windows 10
description: Comment faire en Windows services de localisation pour vos appareils
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 76b6778d68fe5ed12034e3350170cf017093584e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60170078"
---
# <a name="windows-10-location-service"></a>Service d’emplacement Windows 10

Les appareils Microsoft Manged Desktop sont enregistrés à l’aide Windows Autopilot. Ce processus nous permet de les gérer avec Azure Active Directory et Microsoft Intune. Par défaut, le service d’emplacement Windows 10 est désactivé lorsqu’un appareil est activé pour la première fois, sauf si cette fonctionnalité est activée dans les paramètres de confidentialité lors de l’expérience « out of box experience ». Ces paramètres sont masqués lors de l’inscription Autopilot dans Microsoft Manged Desktop. Pour plus d’informations sur la façon dont Autopilot est installé, voir l’expérience de première expérience avec Autopilot et la page État de [l’inscription.](esp-first-run.md)

Pour cette raison, les Microsoft Manged Desktop ne peuvent pas obtenir leur emplacement d’appareil, ce qui limite les fonctionnalités de plusieurs fonctionnalités Windows, telles que les fuseaux horaires. Pour plus d’informations sur Windows 10 service de localisation, voir Windows 10 [service de localisation et la confidentialité.](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088)

Vous n’avez pas besoin d’utiliser le service d’emplacement pour participer à Microsoft Manged Desktop, mais l’expérience utilisateur sera limitée. Par exemple, les appareils ne seront pas en mesure de déterminer automatiquement le fuseau horaire dans le cas où vos utilisateurs travaillent dans un autre fuseau horaire.

## <a name="enable-the-location-service"></a>Activer le service de localisation

Vous pouvez choisir d’utiliser le service de localisation lorsque vous inscrivez des appareils dans le service Microsoft Manged Desktop ou vous pouvez activer ou désactiver le service après l’inscription.

### <a name="opt-in-during-enrollment"></a>S’inscrire lors de l’inscription

Vous pouvez faire en Microsoft Manged Desktop service d’emplacement le service de localisation. Au cours de la séquence d’inscription, vous serez invité à choisir si vous souhaitez autoriser l’Windows 10 de localisation sur les appareils.

### <a name="control-the-location-service-after-enrollment"></a>Contrôler le service d’emplacement après l’inscription

Vous pouvez que le service d’emplacement soit allumé (ou désactivé) à tout moment en envoyant une demande de [support](../working-with-managed-desktop/admin-support.md) via le [portail d’administration.](access-admin-portal.md)

## <a name="how-microsoft-managed-desktop-configures-the-windows-10-location-service"></a>Comment Microsoft Manged Desktop configurer le service Windows 10 localisation

Si vous optez pour l’utilisation du service d’emplacement, nous utilisons les paramètres minimaux nécessaires sans affecter la confidentialité des utilisateurs. Pour plus d’informations, [voir Windows 10 service de localisation et la confidentialité.](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088)

Microsoft Manged Desktop active le **paramètre** de confidentialité de l’emplacement Windows **paramètres pour** autoriser l’accès à l’emplacement sur cet **appareil.** L’interface utilisateur ressemble à ceci :

 :::image type="content" source="../../media/MMD-location-services-UI.png" alt-text="Paramètres d’emplacement Windows paramètres de localisation.":::

> [!NOTE]
> Si vous optez pour l’utilisation du service d’emplacement, cela s’applique uniquement au Windows d’exploitation proprement dit. Les applications ne sont pas autorisées à utiliser les services de localisation. Chaque utilisateur peut choisir d’autoriser ou non les applications à accéder à leur emplacement.