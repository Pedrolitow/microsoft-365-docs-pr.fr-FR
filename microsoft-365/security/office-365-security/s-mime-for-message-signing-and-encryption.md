---
title: S/MIME pour le chiffrement dans Exchange Online - Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 887c710b-0ec6-4ff0-8065-5f05f74afef3
description: Les administrateurs peuvent en savoir plus sur l’utilisation de S/MIME (Secure/Multipurpose Internet Mail Extensions) dans Exchange Online pour chiffrer les messages électroniques et les signer numériquement.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d189bf7f52dd6f9fb11dc360c17d5fe15729c9fa
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50908781"
---
# <a name="smime-for-message-signing-and-encryption-in-exchange-online"></a>S/MIME pour la signature et le chiffrement des messages dans Exchange Online

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


S/MIME (Secure/Multipurpose Internet Mail Extensions) est une méthode largement acceptée (ou plus précisément un protocole) pour l’envoi de messages signés et chiffrés numériquement. S/MIME vous permet de chiffrer les courriers électroniques et les signer numériquement. Lorsque vous utilisez S/MIME avec un message électronique, cela permet aux personnes qui reçoivent ce message d’être certain que ce qu’elles voient dans leur boîte de réception est le message exact qui a commencé avec l’expéditeur. Il permet également aux personnes qui reçoivent des messages de s’être certain que le message provenait de l’expéditeur spécifique et non d’une personne se faisant passer pour l’expéditeur. Pour ce faire, S/MIME fournit des services de sécurité de chiffrement tels que l'authentification, l'intégrité des messages et la non-répudiation de l'origine (à l'aide de signatures numériques). Il permet également d’améliorer la confidentialité et la sécurité des données (à l’aide du chiffrement) pour la messagerie électronique. Pour en savoir plus sur l'histoire et l'architecture du protocole S/MIME dans le cadre de la messagerie, consultez la rubrique [Présentation du protocole S/MIME](/previous-versions/tn-archive/aa995740(v=exchg.65)).

En tant qu’administrateur Exchange Online, vous pouvez activer la sécurité basée sur S/MIME pour les boîtes aux lettres de votre organisation. Utilisez les instructions des rubriques liées ici avec Exchange Online PowerShell pour configurer S/MIME. Pour utiliser S/MIME dans les clients de messagerie pris en charge, les utilisateurs de votre organisation doivent avoir émis des certificats à des fins de signature et de chiffrement, ainsi que des données publiées dans votre service de domaine Active Directory (AD DS) local. Vos services AD DS doivent se trouver sur des ordinateurs à un emplacement physique que vous contrôlez, et non sur une installation distante ou un service basé sur le cloud quelque part sur Internet. Pour plus d’informations sur les services de domaine [Active Directory, voir Vue d’ensemble](/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)des services de domaine Active Directory.

## <a name="supported-scenarios-and-technical-considerations"></a>Scénarios pris en charge et considérations techniques

Vous pouvez configurer la norme S/MIME afin qu'elle fonctionne avec n'importe lequel des points de terminaison suivants :

- Outlook 2010 ou version ultérieure
- Outlook sur le web (anciennement nommé Outlook Web App)
- Exchange ActiveSync (EAS)

Les étapes à suivre pour configurer S/MIME avec chacun de ces points de fin sont légèrement différentes. En règle générale, vous devez suivre les étapes suivantes :

1. Installez une autorité de certification Basée sur Windows et définissez une infrastructure à clé publique pour émettre des certificats S/MIME. Les certificats émis par des fournisseurs de certificats tiers sont également pris en charge. Pour plus de détails, reportez-vous à [Vue d'ensemble des services de certificats Active Directory](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831740(v=ws.11)).

   **Remarques** :

   - Les certificats émis par une cae tierce ont l’avantage d’être automatiquement fiables par tous les clients et appareils. Les certificats émis par une ca privée interne ne sont pas automatiquement fiables par les clients et les appareils, et tous les appareils (par exemple, les téléphones) ne peuvent pas être configurés pour faire confiance aux certificats privés.

   - Envisagez d’utiliser un certificat intermédiaire au lieu du certificat racine pour émettre des certificats aux utilisateurs. Ainsi, si vous avez besoin de révoquer et de rééditer des certificats, le certificat racine est toujours intact.

2. Publiez le certificat utilisateur dans un compte AD DS local dans les attributs **UserSMIMECertificate** et/ou **UserCertificate.**

3. Pour les organisations Exchange Online, synchronisez les certificats utilisateur d’AD DS avec Azure Active Directory à l’aide d’une version appropriée d’Azure AD Connect. Ces certificats seront ensuite synchronisés à partir d’Azure Active Directory vers l’annuaire Exchange Online et seront utilisés lors du chiffrement d’un message à un destinataire.

4. Configurer une collection de certificats virtuelle afin de valider S/MIME. Ces informations sont utilisées par Outlook sur le web lorsqu'il valide la signature d'un courrier électronique et vérifie qu'il a été signé par un certificat approuvé.

5. Configurer le point de terminaison Outlook ou EAS de sorte qu'il utilise S/MIME.

> [!NOTE]
> Vous ne pouvez pas installer le contrôle S/MIME dans Outlook sur le web sur Mac, iOS, Android ou d’autres appareils autres que Windows. Pour plus d’informations, voir [Chiffrer des messages à l’aide de S/MIME dans Outlook sur le web.](https://support.microsoft.com/office/878c79fc-7088-4b39-966f-14512658f480)

## <a name="set-up-smime-with-outlook-on-the-web"></a>Configuration de S/MIME avec Outlook sur le web

La configuration de S/MIME pour Exchange Online avec Outlook sur le web implique les étapes clés suivantes :

1. [Configurer des paramètres S/MIME pour Outlook sur le web](configure-s-mime-settings-for-outlook-web-app.md)
2. [Configuration d’une collection de certificats virtuelle pour la validation des certificats S/MIME](set-up-virtual-certificate-collection-to-validate-s-mime.md)
3. [Synchronisation des certificats utilisateur vers Office 365 pour S/MIME](sync-user-certificates-to-office-365-for-s-mime.md)

## <a name="related-message-encryption-technologies"></a>Technologies liées au chiffrement des messages

À mesure que la sécurité des messages devient plus importante, les administrateurs doivent comprendre les principes et les concepts de la messagerie sécurisée. Cette compréhension est particulièrement importante en raison de la variété croissante de technologies liées à la protection (y compris S/MIME) disponibles. Pour en savoir plus sur S/MIME et son fonctionnement dans le contexte de la messagerie, voir [Understanding S/MIME](/previous-versions/tn-archive/aa995740(v=exchg.65)). Diverses technologies de chiffrement fonctionnent ensemble pour assurer la protection des messages au repos et en transit. S/MIME peut fonctionner simultanément avec les technologies suivantes, mais n’en dépend pas :

- **Le chiffrement TLS (Transport Layer Security)** chiffre le tunnel ou l’itinéraire entre les serveurs de messagerie afin d’empêcher l’espion et l’écoute clandestine.

- **SSL (Secure Sockets Layer)** chiffre la connexion entre les clients de messagerie et les serveurs Microsoft 365.

- **BitLocker** chiffre les données sur un disque dur dans un centre de données afin que si une personne obtient un accès non autorisé, elle ne puisse pas la lire.

### <a name="smime-compared-with-office-365-message-encryption"></a>S/MIME comparé au chiffrement de messages Office 365

S/MIME requiert un certificat et une infrastructure de publication qui est souvent utilisée dans les situations entreprise-entreprise et entreprise-client. L'utilisateur contrôle les clés de chiffrement dans S/MIME et peut choisir de les utiliser ou non pour chaque message qu'il envoie. Les programmes de messagerie (par exemple, Outlook) recherchent un emplacement de certification racine approuvée pour effectuer la signature numérique et vérifier la signature. Le chiffrement de messages Office 365 est un service de chiffrement basé sur une stratégie qui peut être configuré par un administrateur, et non par un utilisateur individuel, pour chiffrer les messages envoyés à toute personne à l’intérieur ou à l’extérieur de l’organisation. Il s’agit d’un service en ligne qui repose sur Azure Rights Management (RMS) et ne repose pas sur une infrastructure à clé publique. Le chiffrement de messages Office 365 offre également des fonctionnalités supplémentaires, telles que la possibilité de personnaliser le courrier électronique avec la marque de l’organisation. Pour plus d’informations sur le chiffrement de messages Office 365, voir [Chiffrement dans Office 365.](../../compliance/encryption.md)

## <a name="more-information"></a>Informations supplémentaires

[Outlook sur le web](/exchange/exchange-admin-center)

[Secure Mail (2000)](/previous-versions/windows/it-pro/windows-2000-server/cc962043(v=technet.10))