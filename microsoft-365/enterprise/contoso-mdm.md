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
ms.openlocfilehash: 40d9473bcadfa636f6fd2b2c6c861c27dae8497c
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46685841"
---
# <a name="mobile-device-management-for-contoso"></a>Gestion des appareils mobiles pour Contoso

Microsoft 365 pour Enterprise inclut Intune et un ensemble de services Azure pour la prise en charge de la gestion et de la sécurité des appareils mobiles et des applications.

Chez Contoso, de nombreux employés sont équipés d’appareils mobiles. Certains d’entre eux ont leur bureau sur les sites de Contoso et d’autres n’ont pas de bureau. Contoso cherchait une solution pour renforcer la productivité des employés, tout en garantissant la sécurité des appareils, des données Contoso stockées sur ces appareils et du comportement des applications.

## <a name="plan"></a>Prévision

Au début de l’analyse de la gestion des appareils mobiles pour Microsoft 365 pour les entreprises, Contoso a identifié les cas d’utilisation Intune suivants :

- Protection des données et des e-mails Exchange Online pour y accéder en toute sécurité sur les appareils mobiles
- Implémentation d’un programme BYOD (Apportez votre propre appareil) destiné aux employés de Contoso
- Fourniture de téléphones appartenant à l’organisation et de tablettes partagées à usage limité aux employés de Contoso

Contoso n’utilise pas Intune pour :

- Autoriser les employés à accéder en toute sécurité à Microsoft 365 à partir d’un kiosque public non géré
- Protéger les données et les e-mails dans l’environnement local pour pouvoir y accéder en toute sécurité sur les appareils mobiles, car il n’y a plus de serveurs Microsoft Exchange locaux.

## <a name="deploy"></a>Déployer

Voici la configuration de l’infrastructure de gestion des appareils mobiles de Contoso :

- Intune est devenu l’autorité de gestion des appareils mobiles (GAM). Il est utilisé sur Azure pour administrer le contenu et gérer les appareils.
- Des groupes Azure AD ont été créés pour inscrire des groupes d’appareil, pour les paramètres Intune et pour les stratégies d’accès conditionnel.

  Pour plus d’informations, consultez [Stratégies d’accès conditionnel personnalisées de Contoso](contoso-identity.md#conditional-access-policies-for-identity-and-device-access).

- Une plateforme d’appareils Apple a été mise en place pour prendre en charge les employés équipés d’appareils Apple (iPad, iMac, iPhone) et pour les téléphones de type iPhone appartenant à l’entreprise.
- Les politiques de conditions générales de Contoso ont été créées. Elles sont affichées pendant l’installation du portail de l’entreprise sur les appareils mobiles.
- Pour les appareils qui ne sont pas déployés, un ensemble de stratégies de gestion des applications mobiles (MAM) pour exiger l’authentification pour l’accès aux services Microsoft 365
- Des stratégies Intune ont été créées pour appliquer :
  - Des applications autorisées
  - Le chiffrement de l’appareil pour empêcher tout accès non autorisé
  - Un code confidentiel ou un mot de passe à six chiffres
  - Un délai d’inactivité
  - Une protection antivirus et contre les programmes malveillants et des mises à jour de signature avec Windows Defender sur les appareils Windows 10
  - Des mises à jour automatiques sur les appareils Windows 10 qui incluent les dernières mises à jour de sécurité
  - L’envoi de certificats aux appareils gérés
  - Une séparation claire des données professionnelles et personnelles. Les utilisateurs ou les administrateurs peuvent effacer de l’appareil les données d’entreprise sélectionnées, tout en conservant des données personnelles telles que des images, des comptes de messagerie personnels et des fichiers personnels.

Une fois l’infrastructure déployée, Contoso a inscrit les PC et les smartphones et tablettes appartenant à l’entreprise en les ajoutant aux groupes d’appareils Intune appropriés et a déployé un programme BYOD pour que les employés inscrivent leurs appareils personnels. Les appareils inscrits ont reçu les stratégies Intune pour gérer et sécuriser les appareils et leurs applications. Les appareils qui ne sont pas inscrits ont des stratégies de gestion des applications mobiles (GAM) qui spécifient les applications autorisées.

Voici l’architecture de déploiement de la gestion des appareils mobiles de Contoso.

![Infrastructure de déploiement de la gestion des appareils mobiles de Contoso](../media/contoso-mdm/contoso-mdm-fig1.png)

## <a name="next-step"></a>Étape suivante

[Découvrez](contoso-info-protect.md) comment Contoso utilise les fonctionnalités de protection des informations de Microsoft 365 pour Enterprise pour classer, identifier et protéger les biens numériques stratégiques au sein de son organisation.

## <a name="see-also"></a>Voir aussi

[Gestion des appareils pour Microsoft 365](device-management-roadmap-microsoft-365.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)

