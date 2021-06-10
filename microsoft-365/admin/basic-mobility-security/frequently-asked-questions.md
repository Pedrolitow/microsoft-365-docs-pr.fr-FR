---
title: Questions fréquemment posées sur la mobilité et la sécurité de base (FAQ)
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Questions fréquemment posées sur basic Mobility and Security.
ms.openlocfilehash: 14e12678ec210325f63914594fb6debcf7abb880
ms.sourcegitcommit: 72795ec56a7c4db863dcaaff5e9f7c41c653fda8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52023892"
---
# <a name="basic-mobility-and-security-frequently-asked-questions-faq"></a>Questions fréquemment posées sur la mobilité et la sécurité de base (FAQ)

Cet article contient des questions fréquemment posées sur Basic Mobility and Security, une fonctionnalité qui vous aide à gérer et sécuriser les appareils mobiles dans Microsoft 365. Si vous ne trouvez pas de réponse à votre question, faites-le nous savoir en laissant un commentaire sur la page afin que nous pouvons envisager d’ajouter votre question à cet article.

## <a name="how-can-i-get-basic-mobility-and-security-i-dont-see-it-in-the-microsoft-365-admin-center"></a>Comment puis-je obtenir la mobilité et la sécurité de base ? Je ne le vois pas dans le Centre d’administration Microsoft 365 de gestion

1.  Activez La mobilité et la sécurité de base en allant sur la page [Office 365 sécurité & conformité.](https://protection.office.com/)

2.  Go to Data loss prevention > Device management.

## <a name="how-can-i-get-started-with-device-management-in-basic-mobility-and-security"></a>Comment puis-je commencer à gérer les appareils dans Basic Mobility and Security ?

La mise en place de la mobilité et de la sécurité de base se fait en quatre étapes : 

1. Activez La mobilité et la sécurité de base en allant à la [Office 365 sécurité & conformité.](https://protection.office.com/)

2. Go to Data loss prevention > Device management > Device policies.
    
3. Créez des stratégies de gestion des appareils et appliquez-les à des groupes d’utilisateurs qui sont configurer dans des groupes de sécurité. Nous vous recommandons de commencer par déployer les stratégies dans un petit groupe de test. Pour plus d’informations, voir [Créer des stratégies de sécurité des appareils dans Basic Mobility and Security.](create-device-security-policies.md)

4. Les utilisateurs qui ont appliqué une stratégie sont invités à inscrire leurs appareils lorsqu’ils tentent d’accéder Microsoft 365 données. Pour plus d’informations, voir [Inscrire votre appareil mobile à l’aide de Basic Mobility and Security](enroll-your-mobile-device.md).

Pour plus d’informations, voir [Set up Basic Mobility and Security](set-up.md).

## <a name="im-trying-to-set-up-basic-mobility-and-security-but-it-seems-stuck-the-microsoft-365-service-health-has-been-showing-provisioning-for-a-while-what-can-i-do"></a>J’essaie de configurer la mobilité et la sécurité de base, mais elle semble bloquée. L Microsoft 365 l’état du service affiche la « mise en service » depuis un certain temps. Que puis-je faire ?

La préparation du service peut prendre un certain temps. Une fois l’approvisionnement terminé, vous verrez la page Mobilité et sécurité de base. Si vous avez attendu 24 heures et que l’état est toujours en cours d’approvisionnement, contactez le support technique et nous vous aiderons à déterminer le problème.

## <a name="what-can-i-do-if-device-enrollment-fails"></a>Que puis-je faire en cas d’échec de l’inscription des appareils ?

Si vous avez des difficultés à obtenir l’enregistrement d’un appareil, vérifiez d’abord les étapes suivantes :

- Assurez-vous que l’appareil n’est pas déjà inscrit auprès d’un autre fournisseur de gestion d’appareils mobiles, tel qu’Intune.

- Assurez-vous que la date et l’heure de l’appareil sont correctes.

- Basculez vers un autre réseau WIFI ou cellulaire sur l’appareil.

- Pour les appareils Android ou iOS, désinstallez et réinstallez l’application Portail d’entreprise Intune sur l’appareil.
    
Si l’inscription ne fonctionne toujours pas, voir [Résoudre les problèmes de mobilité et de sécurité de base.](troubleshoot.md)

## <a name="whats-the-difference-between-intune-and-basic-mobility-and-security"></a>Quelle est la différence entre Intune et Basic Mobility and Security ?

Basic Mobility and Security est hébergé par le service Intune. Il s’agit d’un sous-ensemble de services Intune fournis en tant qu’avantage supplémentaire pour Microsoft 365 et d’une solution cloud intégrée pour la gestion des appareils dans votre organisation. Pour obtenir une comparaison côte à côte des deux services pour vous aider à déterminer si l’utilisation d’Intune ou de Basic Mobility and Security pour Microsoft 365 vous convient le mieux, voir Choisir entre Basic Mobility Security et [Intune.](choose-between-basic-mobility-and-security-and-intune.md)

## <a name="how-do-policies-work-for-basic-mobility-and-security-how-do-i-set-them-up-disable-them"></a>Comment fonctionnent les stratégies pour la mobilité et la sécurité de base ? Comment les configurer ? Les désactiver ?

Une fois la configuration initiale de Basic Mobility and Security terminée, vous créez des stratégies et les appliquez à des groupes d’utilisateurs dans le Centre de sécurité & conformité. Les stratégies exigent que les utilisateurs des stratégies inscrivent leurs appareils dans Basic Mobility and Security avant que l’appareil puisse être utilisé pour accéder Microsoft 365 données. Les stratégies que vous avez définies déterminent les paramètres des appareils mobiles, par exemple, la fréquence de réinitialisation des mots de passe ou la nécessité d’un chiffrement des données. Pour plus d’informations, voir [Créer des stratégies](create-device-security-policies.md)de sécurité des appareils dans le Centre de conformité et de mobilité   Microsoft 365 de [base.](../../compliance/microsoft-365-compliance-center.md)

Pour obtenir des instructions détaillées sur la création et le déploiement de stratégies d’appareil, voir Créer des stratégies de sécurité d’appareil [dans Basic Mobility and Security](create-device-security-policies.md).

Si vous souhaitez exclure un groupe spécifique d’utilisateurs de l’impact des stratégies, vous pouvez ajouter un groupe au groupe d’exclusions.

## <a name="can-i-switch-from-exchange-activesync-device-management-to-basic-mobility-and-security-for-microsoft-365"></a>Puis-je passer de la gestion Exchange ActiveSync des appareils à la mobilité et à la sécurité de base pour Microsoft 365 ?

Si vous utilisez déjà des stratégies Exchange ActiveSync pour gérer les appareils mobiles, vous pouvez commencer à utiliser Basic Mobility and Security en suivant les étapes de mise en place de Basic Mobility and Security. Pour plus d’informations, voir [Protéger l’accès](../../compliance/protect-access-to-data-and-services.md) des utilisateurs et des appareils et [Configurer la mobilité et la sécurité de base.](set-up.md)

Lorsque vous appliquez les stratégies que vous créez dans Basic Mobility and Security à des groupes d’utilisateurs Exchange ActiveSync, ces stratégies remplacent les stratégies de boîte aux lettres d’appareil mobile et les règles d’accès aux appareils que vous avez précédemment créées dans le Centre d’administration Exchange pour ces utilisateurs.

Une fois qu’un appareil est inscrit à Basic Mobility and Security, toute stratégie de boîte aux lettres ou règle d’accès Exchange ActiveSync’appareil mobile appliquée à l’appareil est ignorée.

## <a name="i--set-up-basic-mobility-and-security-but-now-i-want-to-remove-it-what-are-the-steps"></a>J’ai installé Basic Mobility and Security, mais je veux maintenant le supprimer. Quelles sont les étapes ?

Malheureusement, vous ne pouvez pas simplement « mettre en service » Basic Mobility and Security après l’avoir installé. Toutefois, vous pouvez le supprimer pour des groupes d’utilisateurs en supprimant des groupes de sécurité d’utilisateurs des stratégies d’appareil que vous avez créées. Vous pouvez également la désactiver pour tout le monde en supprimant les stratégies d’appareil afin qu’elles ne soient pas en place et ne soient pas appliquées. Pour plus d’informations, voir [Désactiver la mobilité et la sécurité de base.](turn-off.md)