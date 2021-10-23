---
title: Configurer SAP SuccessFactors en tant que source de contenu pour Apprentissage Microsoft Viva
ms.author: daisyfeller
author: daisyfell
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 10/07/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: medium
description: Découvrez comment configurer SAP SuccessFactors en tant que source de contenu d’apprentissage pour Apprentissage Microsoft Viva.
ROBOTS: NOINDEX
ms.openlocfilehash: f7df19cdfa4298c6d5f6b6700c7203205dd1c3de
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60556737"
---
# <a name="configure-sap-successfactors-as-a-content-source-for-microsoft-viva-learning"></a>Configurer SAP SuccessFactors en tant que source de contenu pour Apprentissage Microsoft Viva

Cet article vous montre comment configurer SAP SuccessFactors en tant que source de contenu tierce pour Apprentissage Microsoft Viva. Tout d’abord, vous devez modifier la configuration système dans le portail SuccessFactors, puis terminer la configuration dans le Centre d'administration Microsoft 365.

>[!NOTE]
>Le contenu accessible par le biais de Learning est soumis à des conditions autres que celles de Microsoft Product Terms. Le contenu SAP SuccessFactors et les services associés sont soumis aux conditions de confidentialité et de service SAP SuccessFactors.

## <a name="configure-the-successfactors-portal"></a>Configurer le portail SuccessFactors

>[!Note]
> L’administrateur qui active cette fonctionnalité doit avoir accès à l’application SuccessFactors Learning’administrateur.

1. Obtenez les flux de travail requis pour modifier la configuration PARTNER_EXTRACT, que vous pouvez obtenir en allant à configuration système de configuration **d’administration**  >    >    >  **du système PARTNER_EXTRACT**.

2. Utilisez l’outil PGP pour générer la clé PGP (clé publique, clé privée, phrase passphrase de clé privée) de votre taille préférée. Lors de la génération de la clé PGP, vous pouvez sélectionner l’algorithme RSA, ce qui est recommandé. L’outil GNUPG est l’un des outils de génération de clés PGP que vous pouvez utiliser.

3. Remplissez les paramètres suivants dans la configuration PARTNER_EXTRACT’ordinateur. Pour modifier la configuration d’extraction du partenaire dans SuccessFactors, vous devez obtenir l’autorisation Modifier le flux de travail **configuration** du système dans SuccessFactors.

- e-mail de notification client pour tout l’état du travail
    - defaultJob.email=

- Partner1
    - La longueur maximale de PartnerID est de 10 caractères. Il peut s’tr de votre ID de client LMS.
partners1.partnerID=

- EncryptionKey est la clé de chiffrement publique PGP, qui est la section entière entre BEGIN PGP PUBLIC KEY BLOCK et END PGP PUBLIC KEY BLOCK
    - partners1.encryptionKey=

- KeyOwner est mapué sur l’ID utilisateur de la clé publique
    - partners1.keyOwner=

- peut être « false » ou « true ». Définissez-la sur « true » pour activer l’extraction du partenaire.
    - partners1.enabled=

<!--![Image of the PARTNER_EXTRACT configuration settings filled in.](../media/learning/sap-1.png)-->

Une fois que vous avez effectué ces étapes dans le portail SuccessFactors, vous devez terminer l’installation dans le Centre d'administration Microsoft 365.

## <a name="configure-the-microsoft-365-admin-center"></a>Configurer le Centre d'administration Microsoft 365

1. Accédez à [votre Centre d'administration Microsoft 365](https://admin.microsoft.com).

2. Accédez à **Paramètres**  >  **paramètres de l’organisation.** Recherchez *Des Learning* Et activez SAP SuccessFactors à partir des options.

3. Remplissez les détails de configuration.

### <a name="configuration-details"></a>Détails de configuration

<!--![Image of the configuration details filled in in the Microsoft 365 admin center.](../media/learning/sap-2.png)-->

**Nom complet**: entrez le nom complet souhaité pour le carrousel SAP SuccessFactors.

**URL d’hôte SFTP**: accédez à **LMS Admin Application**  >  **System Administration** Configuration System  >    >  **Configuration**  >  **CONNECTORS**. Obtenir la valeur de la `connector.ftp.server` propriété.

**Nom d’utilisateur**: suivez les mêmes étapes que vous avez suivies pour l’URL d’hôte SFTP. Obtenir la valeur de la `connector.ftp.userID` propriété.

**Mot de** passe : entrez votre mot de passe. Consultez le propriétaire de votre application LMS pour obtenir de l’aide sur la récupération de votre mot de passe.

**Chemin d’accès** au dossier : accédez à configuration du système de configuration du système d’administration des applications d’administration   >    >    >    >  **LMS PARTNER_EXTRACT**. Obtenir la valeur de la `defaultFtp.path` propriété.

URL hôte du client : il **s’agit** de l’URL de domaine BizX. Vous pouvez l’obtenir à partir de votre URL de connexion BizX. Par exemple, si votre URL de connexion BizX est « organization.successfactors.com/sf/start/#/login », l’URL hôte est « organization.successfactors.com ».

URL de destination Learning client : vous pouvez **l’obtenir** à partir de l’URL du module de domaine d’apprentissage. Par exemple, si l’URL du domaine d’apprentissage est « organization.scdemo.successfactors.com/learning/... » l’URL Learning destination est alors « organization.scdemo.successfactors.com ».

**Clé privée PGP**: clé privée PGP pour le déchiffrement, qui est la section complète entre BEGIN PGP PRIVATE KEY BLOCK et END PGP PRIVATE KEY BLOCK. Vous devez copier la clé exactement telle qu’elle a été générée . ne supprimez pas les nouveaux caractères de ligne.

Phrase clé privée **PGP**: vous devez obtenir cette valeur auprès de votre administrateur informatique ou de l’équipe qui fournit votre clé PGP.

**ID de société**: connectez-vous à votre portail SuccessFactors. Sélectionnez votre icône de profil, puis **sélectionnez Afficher la version Paramètres**. Vous pouvez afficher votre ID d’entreprise ici.

<!--![Image of the steps to find your company ID.](../media/learning/sap-3.png)-->

>[!Note]
> Les cours SuccessFactors commenceront à apparaître dans Le Learning Dans les 7 jours suivant la réussite de l’installation.

>[!Note]
> Tous les utilisateurs d’une organisation pourront découvrir tous les cours spécifiques au client, mais ils pourront uniquement accéder aux cours qu’ils ont accès et y accéder. La découverte de contenu spécifique à l’utilisateur est prévue pour les prochaines sorties.

## <a name="data-residency"></a>Résidence de données

Les métadonnées du client sont stockées de manière centralisée dans nos magasins de données et non dans des magasins de données spécifiques à la région.

## <a name="roles-and-permissions"></a>Rôles et autorisations

Les utilisateurs au sein d’une organisation pourront découvrir tout le contenu disponible pour leur organisation, mais ils pourront uniquement utiliser les cours qu’ils ont accès.
