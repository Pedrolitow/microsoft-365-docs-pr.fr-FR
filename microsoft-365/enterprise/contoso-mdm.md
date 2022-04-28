---
title: Gestion des appareils mobiles pour Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez comment Contoso utilise Microsoft Intune dans Microsoft 365 pour l’entreprise afin de gérer ses appareils et les applications qui s’exécutent sur ces appareils.
ms.openlocfilehash: c321fc9bdaf27577e32d934aa771c92d1a0bdd79
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092688"
---
# <a name="mobile-device-management-for-contoso"></a>Gestion des appareils mobiles pour Contoso

Microsoft 365 pour les entreprises inclut Intune et un ensemble de services Azure qui prennent en charge la gestion et la sécurité des appareils mobiles et des applications.

Contoso compte de nombreux employés mobiles. Certains ont des bureaux à Contoso et d’autres n’ont pas de bureaux. Contoso avait besoin d’un moyen d’activer la productivité des employés, mais de sécuriser les appareils, les données Contoso stockées sur ces appareils et le comportement de l’application.

## <a name="plan"></a>Prévision

Contoso a identifié les cas d’utilisation Intune suivants de la gestion des appareils mobiles pour Microsoft 365 pour les entreprises :

- Protégez Exchange Online e-mail et les données afin qu’ils soient accessibles en toute sécurité par les appareils mobiles.
- Implémentez un programme BYOD (bring-your-own-device) pour les employés de Contoso.
- Émettez des téléphones appartenant à l’organisation et des tablettes partagées à utilisation limitée aux employés de Contoso.

Contoso n’utilise pas Intune pour :

- Permettre aux employés d’accéder en toute sécurité à Microsoft 365 à partir d’une borne publique non managée.
- Protégez les e-mails et les données locaux afin qu’ils soient accessibles en toute sécurité par les appareils mobiles, car il n’existe aucun serveur Microsoft Exchange local.

## <a name="deploy"></a>Déployer

Voici la configuration de l’infrastructure de gestion des appareils mobiles de Contoso :

- Définissez Intune en tant qu’autorité mobile Gestion des appareils (GPM) et utilisez Intune sur Azure pour administrer le contenu et gérer les appareils
- Création de groupes Azure Active Directory (Azure AD) pour les appareils pour l’inscription et les paramètres de Intune et les stratégies d’accès conditionnel basées sur les appareils

  Pour plus d’informations, consultez [les stratégies d’accès conditionnel de Contoso](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).

- Activation de la plateforme d’appareils Apple pour prendre en charge les employés avec des iPad, des iMacs et des iPhone, ainsi que des iPhone appartenant à l’entreprise
- Les politiques de conditions générales de Contoso ont été créées. Elles sont affichées pendant l’installation du portail de l’entreprise sur les appareils mobiles.
- Pour les appareils qui ne sont pas inscrits, implémenté un ensemble de stratégies de gestion des applications mobiles (GAM) pour exiger l’authentification pour l’accès aux services Microsoft 365
- Des stratégies Intune ont été créées pour appliquer :
  - Applications autorisées.
  - Chiffrement de l’appareil pour empêcher l’accès non autorisé.
  - Code confidentiel ou mot de passe à six chiffres.
  - Période d’inactivité-délai d’attente.
  - Protection antivirus et contre les programmes malveillants, et mises à jour des signatures avec Windows Defender sur Windows 10 appareils.
  - Mises à jour automatiques sur Windows 10 appareils qui incluent les dernières mises à jour de sécurité.
  - Envoi de certificats aux appareils gérés.
  - Une séparation claire des données professionnelles et personnelles. Les utilisateurs ou les administrateurs peuvent effacer de l’appareil les données d’entreprise sélectionnées, tout en conservant des données personnelles telles que des images, des comptes de messagerie personnels et des fichiers personnels.

Contoso a inscrit des PC déployés et des smartphones et tablettes appartenant à l’entreprise en les ajoutant aux groupes d’appareils Intune appropriés. Ils ont également mis en place un programme BYOD pour permettre aux employés d’inscrire leurs appareils personnels. Les appareils inscrits reçoivent Intune stratégies, ce qui entraîne des appareils gérés et sécurisés et leurs applications. Les appareils qui ne sont pas inscrits ont des stratégies de gestion des applications mobiles (MAM) qui spécifient les applications autorisées.

Voici l’architecture de déploiement de la gestion des appareils mobiles Contoso.

![Infrastructure de déploiement de la gestion des appareils mobiles Contoso.](../media/contoso-mdm/contoso-mdm-fig1.png)

## <a name="next-step"></a>Étape suivante

Découvrez comment Contoso utilise les [fonctionnalités de protection des informations](contoso-info-protect.md) de Microsoft 365 pour l’entreprise afin de classifier, d’identifier et de protéger les ressources numériques essentielles au sein de son organisation.

## <a name="see-also"></a>Voir aussi

[Gestion des appareils pour Microsoft 365](device-management-roadmap-microsoft-365.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)

