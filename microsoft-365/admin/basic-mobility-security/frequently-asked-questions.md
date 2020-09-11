---
title: Questions fréquemment posées sur la mobilité et la sécurité de base
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
description: Questions fréquemment posées sur la mobilité et la sécurité de base.
ms.openlocfilehash: e05815392510ad54bb530457d7f0f6490ece4a95
ms.sourcegitcommit: aeb94601a81db3ead8610c2f36cff30eb9fe10e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "47430164"
---
# <a name="basic-mobility-and-security-frequently-asked-questions-faq"></a>Questions fréquemment posées sur la mobilité et la sécurité de base

Cet article contient des questions fréquemment posées sur la mobilité et la sécurité de base, une fonctionnalité qui vous permet de gérer et de sécuriser les appareils mobiles dans Microsoft 365. Si vous ne trouvez pas de réponse à votre question, faites-nous part de vos commentaires sur la page pour pouvoir ajouter votre question à cet article.

## <a name="how-can-i-get-basic-mobility-and-security-i-dont-see-it-in-the-microsoft-365-admin-center"></a>Comment puis-je obtenir une mobilité et une sécurité de base ? Je ne la vois pas dans le centre d’administration Microsoft 365

1.  Activez la mobilité et la sécurité de base en accédant à la page [conformité des & de sécurité Office 365](https://protection.office.com/) .   

2.  Accédez à la protection contre la perte de données > la gestion des appareils.   

## <a name="how-can-i-get-started-with-device-management-in-basic-mobility-and-security"></a>Comment puis-je commencer à utiliser la gestion des appareils dans la sécurité et la mobilité de base ?

Pour commencer à utiliser la sécurité et la mobilité de base, vous devez suivre les quatre étapes suivantes : 

1. Activez la mobilité et la sécurité de base en accédant à la [sécurité des & de sécurité Office 365](https://protection.office.com/).
    
2. Accédez à protection contre la perte de données > gestion des périphériques > les stratégies d’appareil.
    
3. Créez des stratégies de gestion des appareils et appliquez-les à des groupes d’utilisateurs qui sont configurés dans des groupes de sécurité. Nous vous recommandons de commencer par déployer les stratégies sur un petit groupe de test. Pour plus d’informations, consultez la rubrique [créer des stratégies de sécurité de périphérique dans Basic Mobility and Security](create-device-security-policies.md).      

4. Les utilisateurs auxquels une stratégie a été appliquée sont invités à inscrire leurs appareils lorsqu’ils tentent d’accéder aux données Microsoft 365. Pour plus d’informations, consultez [la rubrique inscrire votre appareil mobile à l’aide de la sécurité et de la sécurité de base](enroll-your-mobile-device.md).

Pour plus d’informations, consultez la rubrique [Set Up Basic Mobility and Security](set-up.md).

## <a name="im-trying-to-set-up-basic-mobility-and-security-but-it-seems-stuck-the-microsoft-365-service-health-has-been-showing-provisioning-for-a-while-what-can-i-do"></a>J’essaie de configurer la sécurité et la mobilité de base, mais elle semble bloquée. L’intégrité du service Microsoft 365 a montré la « mise en service » pendant un certain temps. Que puis-je faire ?

La préparation du service peut prendre un certain temps. Lorsque la mise en service est terminée, la page gestion des appareils mobiles pour Microsoft 365 s’affiche. Si vous avez attendu 24 heures et que le statut est toujours en cours de mise en service, veuillez contacter le support technique et nous allons vous aider à déterminer la nature du problème. Pour les options de support, consultez la rubrique [quand vous avez besoin d’aide ?](https://support.microsoft.com/office/frequently-asked-questions-about-basic-mobility-and-security-3871f99c-c9db-4a23-86f9-902c1b02f58d#bkmk_needhelp) 

## <a name="what-can-i-do-if-device-enrollment-fails"></a>Que faire en cas d’échec de l’enregistrement de l’appareil ?

Si vous rencontrez des problèmes lors de l’obtention d’un appareil, vérifiez d’abord les points suivants :

- Assurez-vous que l’appareil n’est pas déjà associé à un autre fournisseur de gestion des appareils mobiles, comme Intune.
    
- Assurez-vous que l’appareil est défini sur la date et l’heure correctes.
    
- Basculez vers un autre réseau Wi-Fi ou cellulaire sur l’appareil.
    
- Pour les appareils Android ou iOS, désinstallez et réinstallez l’application portail d’entreprise Intune sur l’appareil.
    
Si l’enregistrement ne fonctionne toujours pas, consultez la rubrique [Troubleshoot Basic Mobility and Security](troubleshoot.md).

## <a name="whats-the-difference-between-intune-and-basic-mobility-and-security"></a>Quelle est la différence entre Intune et la mobilité et la sécurité de base ?

La sécurité et la mobilité de base sont hébergées par le service Intune. Il s’agit d’un sous-ensemble des services Intune fournis comme un avantage supplémentaire pour Microsoft 365 et est une solution informatique intégrée pour la gestion des appareils dans votre organisation. Pour une comparaison côte à côte des deux services afin de vous aider à déterminer si l’utilisation d’Intune ou de Basic Mobility and Security for Microsoft 365 est la meilleure solution, voir [Choose between Basic Mobility Security and Intune](choose-between-basic-mobility-and-security-and-intune.md).

## <a name="how-do-policies-work-for-basic-mobility-and-security-how-do-i-set-them-up-disable-them"></a>Comment les stratégies fonctionnent-elles pour la mobilité et la sécurité de base ? Comment les configurer ? Les désactiver ?

Après avoir terminé la configuration initiale de la mobilité et de la sécurité de base, vous créez des stratégies et les appliquez à des groupes d’utilisateurs dans le centre de sécurité & Compliance Center. Les stratégies nécessitent que les utilisateurs des stratégies inscrivent leurs appareils dans la sécurité et la mobilité de base avant que l’appareil ne puisse être utilisé pour accéder aux données Microsoft 365. Les stratégies que vous configurez déterminent les paramètres des appareils mobiles, par exemple, la fréquence à laquelle les mots de passe doivent être rétablis ou si le chiffrement des données est requis. Pour plus d’informations, consultez la rubrique [créer des stratégies de sécurité des périphériques dans Basic Mobility and Security](create-device-security-policies.md)   et [Microsoft 365 Compliance Center](https://support.microsoft.com/office/7e696a40-b86b-4a20-afcc-559218b7b1b8).

Pour obtenir des instructions détaillées sur la création et le déploiement de stratégies de périphérique, voir [créer des stratégies de sécurité des appareils dans la section mobilité et sécurité de base](create-device-security-policies.md).

Si vous souhaitez exclure un groupe spécifique d’utilisateurs d’une stratégie, vous pouvez ajouter un groupe au groupe d’exclusion.

## <a name="can-i-switch-from-exchange-activesync-device-management-to-basic-mobility-and-security-for-microsoft-365"></a>Puis-je basculer de la gestion des appareils Exchange ActiveSync vers la mobilité et la sécurité de base pour Microsoft 365 ?

Si vous utilisez déjà des stratégies Exchange ActiveSync pour gérer des appareils mobiles, vous pouvez commencer à utiliser la sécurité et la mobilité de base en suivant les étapes de configuration de la sécurité et de la mobilité de base. Pour plus d’informations, consultez la rubrique [protéger l’accès des utilisateurs et des appareils](https://go.microsoft.com/fwlink/?LinkId=615145) et [configurer la sécurité et la mobilité de base](set-up.md).

Lorsque vous appliquez les stratégies que vous créez dans le cadre de la mobilité et de la sécurité de base à des groupes d’utilisateurs, ces stratégies remplacent les stratégies de boîte aux lettres d’appareil mobile Exchange ActiveSync et les règles d’accès des appareils que vous avez créées précédemment dans le centre d’administration Exchange pour ces utilisateurs.

Après l’enregistrement d’un appareil dans la sécurité et la mobilité de base, toute stratégie de boîte aux lettres d’appareil mobile Exchange ActiveSync ou règle d’accès aux appareils appliquée à l’appareil est ignorée.

## <a name="i--set-up-basic-mobility-and-security-but-now-i-want-to-remove-it-what-are-the-steps"></a>J’ai configuré la mobilité et la sécurité de base, mais maintenant je veux la supprimer. Quelles sont les étapes ?

Malheureusement, vous ne pouvez pas simplement « mettre hors service » la mobilité et la sécurité de base une fois que vous l’avez configurée. Toutefois, vous pouvez le supprimer pour des groupes d’utilisateurs en supprimant les groupes de sécurité des utilisateurs des stratégies d’appareil que vous avez créées. Vous pouvez aussi le désactiver pour tout le monde en supprimant les stratégies d’appareil afin qu’elles ne soient pas en place et ne soient pas appliquées. Pour plus d’informations, reportez-vous à la rubrique [désactiver la mobilité et la sécurité de base](turn-off.md).

