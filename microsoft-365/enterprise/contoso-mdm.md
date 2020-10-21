---
title: Gestion des appareils mobiles pour Contoso
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 10/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez comment Contoso utilise Microsoft Intune dans Microsoft 365 pour entreprise pour gérer ses appareils et les applications qui s’y exécutent.
ms.openlocfilehash: d3f973827a9b05a415efe9225a2bdb3d83ccaf38
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48649644"
---
# <a name="mobile-device-management-for-contoso"></a>Gestion des appareils mobiles pour Contoso

Microsoft 365 pour Enterprise inclut Intune et un ensemble de services Azure qui prennent en charge la gestion et la sécurité des applications et des appareils mobiles.

Contoso possède un grand nombre d’employés à extension mobile. Certains d’entre eux ont des bureaux dans contoso et d’autres n’ont pas de bureau. Contoso a nécessité un moyen d’activer la productivité des employés tout en conservant les appareils, les données Contoso stockées sur ces appareils et le comportement de l’application sécurisé.

## <a name="plan"></a>Prévision

Contoso a identifié les cas d’utilisation Intune suivants de la gestion des appareils mobiles pour Microsoft 365 pour les entreprises :

- Protégez les messages électroniques et les données Exchange Online afin qu’ils puissent être utilisés en toute sécurité par les appareils mobiles.
- Implémentez un programme de mise à BYOD pour les employés de contoso.
- Émettre des téléphones appartenant à l’organisation et des tablettes partagées à usage limité aux employés de contoso.

Contoso n’utilise pas Intune pour :

- Autoriser les employés à accéder en toute sécurité à Microsoft 365 à partir d’un kiosque public non géré.
- Protégez les données et les messages électroniques sur site afin qu’ils puissent être utilisés en toute sécurité par les appareils mobiles, car il n’existe pas de serveurs Microsoft Exchange locaux.

## <a name="deploy"></a>Déployer

Voici la configuration de l’infrastructure de gestion des appareils mobiles de Contoso :

- Définir Intune en tant qu’autorité de gestion des appareils mobiles (MDM) et utiliser Intune sur Azure pour administrer le contenu et gérer les appareils
- Les groupes Azure Active Directory (Azure AD) créés pour les paramètres d’enregistrement et d’Intune et les stratégies d’accès conditionnel basées sur les appareils.

  Pour plus d’informations, consultez la rubrique [stratégies d’accès conditionnel contoso](contoso-identity.md#conditional-access-policies-for-identity-and-device-access).

- Activation de la plateforme d’appareils Apple pour prendre en charge les employés avec iPad, iMac et iPhone, ainsi que les iPhone appartenant à l’entreprise
- Les politiques de conditions générales de Contoso ont été créées. Elles sont affichées pendant l’installation du portail de l’entreprise sur les appareils mobiles.
- Pour les appareils qui ne sont pas déployés, implémentez un ensemble de stratégies de gestion des applications mobiles (MAM) pour exiger l’authentification pour l’accès aux services Microsoft 365
- Des stratégies Intune ont été créées pour appliquer :
  - Applications autorisées.
  - Chiffrement de l’appareil pour empêcher les accès non autorisés.
  - Un code confidentiel ou un mot de passe à six chiffres.
  - Période d’inactivité-délai d’attente.
  - Protection antivirus et programmes malveillants et mises à jour de signature avec Windows Defender sur les appareils Windows 10.
  - Mises à jour automatiques sur les appareils Windows 10 qui incluent les dernières mises à jour de sécurité.
  - Envoi de certificats à des appareils gérés.
  - Une séparation claire des données professionnelles et personnelles. Les utilisateurs ou les administrateurs peuvent effacer de l’appareil les données d’entreprise sélectionnées, tout en conservant des données personnelles telles que des images, des comptes de messagerie personnels et des fichiers personnels.

Contoso a déployé des PC et des smartphones et tablettes appartenant à la société en les ajoutant aux groupes d’appareils Intune appropriés. Ils ont également établi un programme BYOD pour les employés afin d’inscrire leurs appareils personnels. Les périphériques apportés reçoivent des stratégies Intune, qui génèrent des appareils gérés et sécurisés, ainsi que leurs applications. Les appareils qui ne sont pas s’inscrivent ont des stratégies de gestion des applications mobiles (MAM) qui spécifient les applications autorisées.

Voici l’architecture de déploiement de la gestion des appareils mobiles contoso.

![Infrastructure de déploiement de la gestion des appareils mobiles contoso](../media/contoso-mdm/contoso-mdm-fig1.png)

## <a name="next-step"></a>Étape suivante

[Découvrez](contoso-info-protect.md) comment Contoso utilise les fonctionnalités de protection des informations de Microsoft 365 pour Enterprise pour classer, identifier et protéger les biens numériques stratégiques au sein de son organisation.

## <a name="see-also"></a>Voir aussi

[Gestion des appareils pour Microsoft 365](device-management-roadmap-microsoft-365.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)

