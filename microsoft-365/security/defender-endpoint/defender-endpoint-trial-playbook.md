---
title: Playbook d’évaluation - Microsoft Defender pour point de terminaison
description: Utilisez ce guide pour tirer le meilleur parti de votre essai gratuit de 90 jours. Découvrez comment Defender pour point de terminaison peut aider à prévenir, détecter, examiner et répondre aux menaces avancées.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: 07/07/2022
ms.prod: m365-security
ms.technology: mde
ms.localizationpriority: medium
ms.reviewer: ''
f1.keywords: NOCSH
ms.openlocfilehash: 2b7a4d47d07fd609fb9dd424f2a8b89af2ed0b9b
ms.sourcegitcommit: 9fdb5c5b9eaf0c8a8d62b579a5fb5a5dc2d29fa9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2022
ms.locfileid: "66714800"
---
# <a name="trial-playbook-microsoft-defender-for-endpoint"></a>Playbook d’évaluation : Microsoft Defender pour point de terminaison

Bienvenue dans le playbook d’essai Microsoft Defender pour point de terminaison Plan 2 !

Ce playbook est un guide simple pour vous aider à tirer le meilleur parti de votre essai gratuit. En suivant les étapes suggérées dans cet article par l’équipe Microsoft Defender, vous allez découvrir comment Defender pour point de terminaison peut vous aider à prévenir, détecter, examiner et répondre aux menaces avancées.

## <a name="what-is-defender-for-endpoint"></a>Qu’est-ce que Defender pour point de terminaison ?

[Defender pour point de terminaison](microsoft-defender-endpoint.md) est une plateforme de sécurité de point de terminaison d’entreprise qui utilise la combinaison suivante de technologies intégrées à Windows et au service cloud robuste de Microsoft : 

- **Capteurs comportementaux de point de terminaison : incorporés** dans Windows, ces capteurs collectent et traitent les signaux comportementaux du système d’exploitation et envoient des données de capteur à votre instance cloud privée, isolée, de Defender pour point de terminaison.

- **Analyse de la sécurité cloud** : à l’aide du Big Data, de l’apprentissage des appareils et de l’optique Microsoft unique dans l’écosystème Windows, les produits cloud d’entreprise (tels que Microsoft 365) et les ressources en ligne, les signaux comportementaux sont traduits en insights, détections et réponses recommandées aux menaces avancées.

- Renseignement sur les **menaces** : généré par les chasseurs Microsoft et les équipes de sécurité, et enrichi par les informations sur les menaces fournies par les partenaires, le renseignement sur les menaces permet à Defender pour point de terminaison d’identifier les outils, techniques et procédures des attaquants et de générer des alertes lorsqu’ils sont observés dans les données collectées du capteur.

<center><h2>Microsoft Defender pour point de terminaison</center></h2>
<table>
<tr>
<td><a href="microsoft-defender-endpoint.md#tvm"><center><img src="images/logo-mdvm.png" alt="Vulnerability Management"> <br><b>Gestion des vulnérabilités Core Defender</b></center></a></td>
<td><a href="microsoft-defender-endpoint.md#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>Réduction de la surface d’attaque</b></center></a></td>
<td><center><a href="microsoft-defender-endpoint.md#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>Protection de nouvelle génération</b></a></center></td>
<td><center><a href="microsoft-defender-endpoint.md#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>Détection et réponse des points de terminaison</b></a></center></td>
<td><center><a href="microsoft-defender-endpoint.md#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>Examen et correction automatisés</b></a></center></td>
<td><center><a href="microsoft-defender-endpoint.md#mte"><img src="images/mte-icon.png" alt="Microsoft Threat Experts"><br> <b>Spécialistes des menaces Microsoft</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="microsoft-defender-endpoint.md#apis"><center><b>Configuration et administration centralisées, API</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="microsoft-defender-endpoint.md#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

**Mettons-nous au travail.**

## <a name="set-up-your-trial"></a>Configurer votre version d’évaluation

1. [Confirmez l’état de votre licence](#step-1-confirm-your-license-state).
2. [Configurez le contrôle d’accès en fonction du rôle et accordez des autorisations à votre équipe de sécurité](#step-2-set-up-role-based-access-control-and-grant-permissions-to-your-security-team).
3. [Visitez le portail Microsoft 365 Defender](#step-3-visit-the-microsoft-365-defender-portal).
4. [Intégrer des points de terminaison à l’aide de l’un des outils de gestion pris en charge](#step-4-onboard-endpoints-using-any-of-the-supported-management-tools).
5. [Configurez les fonctionnalités](#step-5-configure-capabilities).
6. [Expérience Microsoft Defender pour point de terminaison par le biais d’attaques simulées](#step-6-experience-microsoft-defender-for-endpoint-through-simulated-attacks).
7. [Configurez le laboratoire d’évaluation Microsoft Defender pour point de terminaison](#step-7-set-up-the-microsoft-defender-for-endpoint-evaluation-lab).

## <a name="step-1-confirm-your-license-state"></a>Étape 1 : Confirmer l’état de votre licence

Pour vous assurer que votre abonnement Defender pour point de terminaison est correctement approvisionné, vous pouvez vérifier l’état de votre licence dans le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) ou Azure Active Directory ([https://portal.azure.com](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products)).

[Vérifiez l’état de votre licence](production-deployment.md#check-license-state).

## <a name="step-2-set-up-role-based-access-control-and-grant-permissions-to-your-security-team"></a>Étape 2 : Configurer le contrôle d’accès en fonction du rôle et accorder des autorisations à votre équipe de sécurité

Microsoft recommande d’utiliser le concept de privilèges minimum. Defender pour point de terminaison utilise des rôles intégrés dans Azure Active Directory. [Passez en revue les différents rôles disponibles](/azure/active-directory/roles/permissions-reference) et choisissez les rôles appropriés pour votre équipe de sécurité. Certains rôles devront peut-être être appliqués temporairement et supprimés une fois l’essai terminé.

Utilisez [Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure) pour gérer vos rôles afin de fournir un audit, un contrôle et une révision d’accès supplémentaires pour les utilisateurs disposant d’autorisations d’annuaire.

Defender pour point de terminaison prend en charge deux façons de gérer les autorisations :

- Gestion des autorisations de base : définissez les autorisations sur un accès complet ou en lecture seule. Les utilisateurs disposant de rôles Administrateur général ou Administrateur de sécurité dans Azure Active Directory ont un accès complet. Le rôle lecteur Sécurité dispose d’un accès en lecture seule et n’accorde pas l’accès pour afficher l’inventaire des machines/appareils.
- Contrôle d’accès en fonction du rôle (RBAC) : définissez des autorisations granulaires en définissant des rôles, en attribuant des groupes d’utilisateurs Azure AD aux rôles et en accordant aux groupes d’utilisateurs l’accès aux groupes d’appareils. Pour plus d’informations, consultez [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](rbac.md).

## <a name="step-3-visit-the-microsoft-365-defender-portal"></a>Étape 3 : Visitez le portail Microsoft 365 Defender

Le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) vous permet d’accéder à vos fonctionnalités Defender pour point de terminaison.

1. [Passez en revue les attentes](../defender/microsoft-365-defender-portal.md) dans le portail Microsoft 365 Defender.

2. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous.

3. Dans le volet de navigation, consultez la section **Points de terminaison** pour accéder à vos fonctionnalités. 

## <a name="step-4-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Étape 4 : Intégrer des points de terminaison à l’aide de l’un des outils de gestion pris en charge 

Cette section décrit les étapes générales à suivre pour intégrer des appareils (points de terminaison).

1. [Regardez cette vidéo](https://www.microsoft.com/videoplayer/embed/RE4bGqr) pour obtenir une vue d’ensemble rapide du processus d’intégration et découvrez les outils et méthodes disponibles.

2. Passez en revue les [options de votre outil d’intégration d’appareil](onboarding.md) et sélectionnez l’option la plus appropriée pour votre environnement. 

## <a name="step-5-configure-capabilities"></a>Étape 5 : Configurer les fonctionnalités 

Après avoir intégré des appareils (points de terminaison), vous allez configurer les différentes fonctionnalités, telles que la détection et la réponse des points de terminaison, la protection de nouvelle génération et la réduction de la surface d’attaque.

Utilisez [ce tableau](onboarding.md) pour choisir les composants à configurer. Nous vous recommandons de configurer toutes les fonctionnalités disponibles, mais vous pouvez ignorer celles qui ne s’appliquent pas.

## <a name="step-6-experience-microsoft-defender-for-endpoint-through-simulated-attacks"></a>Étape 6 : Expérience Microsoft Defender pour point de terminaison par le biais d’attaques simulées

Vous souhaiterez peut-être découvrir Defender pour point de terminaison avant d’intégrer plusieurs appareils au service. Pour ce faire, vous pouvez exécuter des simulations d’attaque contrôlées sur quelques appareils de test. Après avoir exécuté les attaques simulées, vous pouvez examiner comment Defender pour point de terminaison expose une activité malveillante et découvrir comment il permet une réponse efficace.

Pour exécuter l’une des simulations fournies, vous avez besoin [d’au moins un appareil intégré](onboard-configure.md).

1. Accédez aux didacticiels. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sous **Points** de terminaison, choisissez **Didacticiels**.

2. Lisez le document pas à pas fourni avec chaque scénario d’attaque. Chaque document inclut les exigences du système d’exploitation et de l’application, ainsi que des instructions détaillées spécifiques à un scénario d’attaque.

3. [Exécutez une simulation](attack-simulations.md).

## <a name="step-7-set-up-the-microsoft-defender-for-endpoint-evaluation-lab"></a>Étape 7 : Configurer le laboratoire d’évaluation Microsoft Defender pour point de terminaison   

Le laboratoire d’évaluation Microsoft Defender pour point de terminaison est conçu pour éliminer les complexités de la configuration de l’appareil et de l’environnement afin que vous puissiez vous concentrer sur l’évaluation des fonctionnalités de la plateforme, l’exécution de simulations et l’affichage des fonctionnalités de prévention, de détection et de correction en action. À l’aide de l’expérience de configuration simplifiée dans le laboratoire d’évaluation, vous pouvez vous concentrer sur l’exécution de vos propres scénarios de test et les simulations prédéfines pour voir comment Defender pour point de terminaison fonctionne.

- [Regardez la vue d’ensemble vidéo](https://www.microsoft.com/videoplayer/embed/RE4qLUM) du laboratoire d’évaluation
- [Prise en main du labo](evaluation-lab.md) 


## <a name="see-also"></a>Voir aussi

- [Documentation technique de Defender pour point de terminaison](microsoft-defender-endpoint.md)
- [Bibliothèque de contenu technique Microsoft Security](https://www.microsoft.com/security/content-library/Home/Index)
- [Démonstration de Defender pour point de terminaison](https://cdx.transform.microsoft.com/experience-detail/d5eca65d-13a3-464d-9171-c24cf9dd6050)

