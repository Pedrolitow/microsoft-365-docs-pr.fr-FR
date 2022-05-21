---
title: Fonctionnalités de chiffrement gérées par le client
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
ms.custom:
- seo-marvel-mar2020
description: Dans cet article, vous allez découvrir les technologies de chiffrement que vous pouvez gérer et configurer dans Microsoft 365.
ms.openlocfilehash: 55bc743f83b79ac83c764af24ef4100e5f72369d
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622552"
---
# <a name="customer-managed-encryption-features"></a>Fonctionnalités de chiffrement gérées par le client

- [Gestion des droits Azure](/azure/information-protection/what-is-azure-rms)

- [Chiffrement des messages Microsoft Purview](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [Sécuriser le flux de messagerie avec une organisation partenaire](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

Pour plus d’informations sur ces technologies, consultez les [descriptions de service Microsoft 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library).

## <a name="azure-rights-management"></a>Gestion des droits Azure

[Azure Rights Management](/azure/information-protection/what-is-azure-rms) (Azure RMS) est la technologie de protection utilisée par [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection). Il utilise des stratégies de chiffrement, d’identité et d’autorisation pour sécuriser vos fichiers et vos e-mails sur plusieurs plateformes et appareils ( téléphones, tablettes et PC). Les informations peuvent être protégées à la fois à l’intérieur et à l’extérieur de votre organisation, car la protection reste avec les données. Azure RMS fournit une protection permanente de tous les types de fichiers, protège les fichiers n’importe où, prend en charge la collaboration interentraux et un large éventail d’appareils Windows et non Windows. La protection Azure RMS peut également augmenter [les stratégies de protection contre la perte de données (DLP](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)). Pour plus d’informations sur les applications et services qui peuvent utiliser le service Azure Rights Management à partir d’Azure Information Protection, consultez [Comment les applications prennent en charge le service Azure Rights Management](/information-protection/understand-explore/applications-support).

Azure RMS est intégré à Microsoft 365 et disponible pour tous les clients. Pour configurer Microsoft 365 d’utiliser Azure RMS, consultez [Configurer IRM pour utiliser Azure Rights Management et configurer des Rights Management d’informations (IRM) dans SharePoint centre d’administration](../enterprise/activate-rms-in-microsoft-365.md). Si vous utilisez Active Directory local serveur RMS (AD), vous pouvez également [configurer IRM pour utiliser un serveur AD RMS local](/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server), mais nous vous recommandons vivement de [migrer vers Azure RMS](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) pour utiliser de nouvelles fonctionnalités telles que la collaboration sécurisée avec d’autres organisations.

Lorsque vous protégez des données client avec Azure RMS, Azure RMS utilise une clé asymétrique RSA 2048 bits avec l’algorithme de hachage SHA-256 pour l’intégrité afin de chiffrer les données. La clé symétrique pour Office documents et e-mail est AES 128 bits. Pour chaque document ou e-mail protégé par Azure RMS, Azure RMS crée une clé AES unique (la « clé de contenu ») et cette clé est incorporée dans le document et conservée par le biais des éditions du document. La clé de contenu est protégée par la clé RSA de l’organisation (« clé de locataire Azure Information Protection ») dans le cadre de la stratégie du document, et la stratégie est également signée par l’auteur du document. Cette clé de locataire est commune à tous les documents et e-mails protégés par Azure RMS pour l’organisation. Cette clé ne peut être modifiée que par un administrateur Azure Information Protection si l’organisation utilise une clé de locataire gérée par le client. Pour plus d’informations sur les contrôles de chiffrement utilisés par Azure RMS, consultez [Comment fonctionne Azure RMS ? Sous le capot](/information-protection/understand-explore/how-does-it-work).

Dans une implémentation Azure RMS par défaut, Microsoft génère et gère la clé racine unique pour chaque locataire. Les clients peuvent gérer le cycle de vie de leur clé racine dans Azure RMS avec Azure Key Vault Services à l’aide d’une méthode de gestion de clé appelée [BYOK (Bring Your Own Key)](/azure/information-protection/plan-implement-tenant-key) qui vous permet de générer votre clé dans des modules HSM locaux (modules de sécurité matériel) et de garder le contrôle de cette clé après le transfert vers les modules HSM fiPS 140-2 validés par Microsoft. L’accès à la clé racine n’est donné à aucun personnel, car les clés ne peuvent pas être exportées ou extraites des HSM qui les protègent. En outre, vous pouvez accéder à un journal en quasi temps réel affichant tout accès à la clé racine à tout moment. Pour plus d’informations, consultez [Journalisation et analyse Azure Rights Management Utilisation](/azure/information-protection/log-analyze-usage).

Azure Rights Management permet d’atténuer les menaces telles que les écoutes téléphoniques, les attaques de l’intercepteur, le vol de données et les violations involontaires des stratégies de partage d’organisation. Dans le même temps, tout accès injustifié aux données client en transit ou au repos par un utilisateur non autorisé qui ne dispose pas des autorisations appropriées est empêché par le biais de stratégies qui suivent ces données, ce qui atténue le risque que ces données tombent entre de mauvaises mains, en connaissance de compte ou sans le savoir, et en fournissant des fonctions de protection contre la perte de données. S’il est utilisé dans le cadre d’Azure Information Protection, Azure RMS fournit également des fonctionnalités de classification des données et d’étiquetage, de marquage de contenu, de suivi d’accès aux documents et de révocation d’accès. Pour en savoir plus sur ces fonctionnalités, consultez [What is Azure Information Protection](/information-protection/understand-explore/what-is-information-protection), [Azure Information Protection deployment roadmap](/information-protection/plan-design/deployment-roadmap) et [quick start tutorial for Azure Information Protection](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>Secure Multipurpose Internet Mail Extension

Secure/Multipurpose Internet Mail Extensions (S/MIME) est une norme pour le chiffrement à clé publique et la signature numérique des données MIME. S/MIME est défini dans les RFC 3369, 3370, 3850, 3851 et autres. Il permet à un utilisateur de chiffrer un e-mail et de signer numériquement un e-mail. Un e-mail chiffré à l’aide de S/MIME ne peut être déchiffré que par le destinataire de l’e-mail à l’aide de sa clé privée, qui est uniquement disponible pour ce destinataire. Par conséquent, les e-mails ne peuvent être déchiffrés par personne autre que le destinataire de l’e-mail.

[Microsoft prend en charge S/MIME](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). Les certificats publics sont distribués au Active Directory local du client et stockés dans des attributs qui peuvent être répliqués vers un locataire Microsoft 365. Les clés privées qui correspondent aux clés publiques restent locales et ne sont jamais transmises à Office 365. Les utilisateurs peuvent composer, chiffrer, déchiffrer, lire et signer numériquement des e-mails entre deux utilisateurs d’une organisation à l’aide de clients Outlook, Outlook sur le web et Exchange ActiveSync. Pour plus d’informations, consultez [le chiffrement S/MIME maintenant dans Office 365](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/).

## <a name="office-365-message-encryption"></a>Chiffrement de messages Office 365

[Office 365 chiffrement](https://products.office.com/exchange/office-365-message-encryption) des messages (OME) basé sur [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) (AIP) vous permet d’envoyer des messages chiffrés et protégés par des droits à quiconque. OME atténue les menaces telles que les écoutes téléphoniques et les attaques de l’intercepteur, et d’autres menaces, telles que l’accès injustifié aux données par un utilisateur non autorisé qui ne dispose pas des autorisations appropriées. Nous avons effectué des investissements qui vous offrent une expérience de messagerie plus simple, plus intuitive et sécurisée basée sur Azure Information Protection. Vous pouvez protéger les messages envoyés de Microsoft 365 à toute personne à l’intérieur ou à l’extérieur de votre organisation. Ces messages peuvent être affichés sur un ensemble varié de clients de messagerie à l’aide de n’importe quelle identité, y compris Azure Active Directory, compte Microsoft et ID Google. Pour plus d’informations sur la façon dont votre organisation peut utiliser des messages chiffrés, consultez [Office 365 Chiffrement des](./ome.md) messages.

## <a name="transport-layer-security"></a>Transport Layer Security

Si vous souhaitez garantir une communication sécurisée avec un partenaire, vous pouvez utiliser des connecteurs entrants et sortants pour assurer la sécurité et l’intégrité des messages. Vous pouvez configurer le protocole TLS entrant et sortant forcé sur chaque connecteur à l’aide d’un certificat. L’utilisation d’un canal SMTP chiffré peut empêcher le vol de données par le biais d’une attaque de l’intercepteur. Pour plus d’informations, consultez [Comment Exchange Online utilise TLS pour sécuriser les connexions e-mail](./exchange-online-uses-tls-to-secure-email-connections.md).

## <a name="domain-keys-identified-mail"></a>Courrier identifié pour les clés de domaine

Exchange Online Protection (EOP) et Exchange Online prennent en charge la validation entrante des messages DKIM (Domain Keys Identified Mail). DKIM est une méthode permettant de valider qu’un message a été envoyé à partir du domaine dont il dit qu’il provient et qu’il n’a pas été usurpé par quelqu’un d’autre. Il lie un e-mail à l’organisation responsable de son envoi et fait partie d’un paradigme plus large de chiffrement de messagerie. Pour plus d’informations sur les trois parties de ce paradigme, consultez :

- [Configurer SPF pour empêcher l’usurpation d’identité](/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [Utiliser DMARC pour valider les messages électroniques](/office365/SecurityCompliance/use-dmarc-to-validate-email)
