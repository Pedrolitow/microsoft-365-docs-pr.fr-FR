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
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
ms.custom:
- seo-marvel-mar2020
description: Dans cet article, vous allez découvrir les technologies de chiffrement que vous pouvez gérer et configurer dans Microsoft 365.
ms.openlocfilehash: bb6f9fedf915fd261266a9ed5d0c561d1352ea09
ms.sourcegitcommit: 7ecd10b302b3b3dfa4ba3be3a6986dd3c189fbff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "49921554"
---
# <a name="customer-managed-encryption-features"></a>Fonctionnalités de chiffrement gérées par le client

Parallèlement aux technologies de chiffrement de Microsoft 365 gérées par Microsoft, Microsoft 365 fonctionne également avec des technologies de chiffrement supplémentaires que vous pouvez gérer et configurer, telles que :

- [Gestion des droits Azure](https://docs.microsoft.com/azure/information-protection/what-is-azure-rms)

- [Secure Multipurpose Internet Mail Extension](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx)

- [Chiffrement de messages Office 365](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [Flux de messagerie sécurisé avec une organisation partenaire](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

Pour plus d’informations sur ces technologies, voir les descriptions du [service Microsoft 365.](https://technet.microsoft.com/library/office-365-service-descriptions.aspx)

## <a name="azure-rights-management"></a>Gestion des droits Azure

[Azure Rights Management](https://docs.microsoft.com/azure/information-protection/what-is-azure-rms) (Azure RMS) est la technologie de protection utilisée par [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection). Il utilise des stratégies de chiffrement, d’identité et d’autorisation pour sécuriser vos fichiers et messages électroniques sur plusieurs plateformes et appareils (téléphones, tablettes et PC). Les informations peuvent être protégées à la fois au sein et en dehors de votre organisation, car la protection reste avec les données. Azure RMS offre une protection permanente de tous les types de fichiers, protège les fichiers n’importe où, prend en charge la collaboration entre entreprises et un large éventail d’appareils Windows et non-Windows. La protection Azure RMS peut également augmenter les stratégies de protection contre la [perte de données (DLP).](https://docs.microsoft.com/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) Pour plus d’informations sur les applications et services qui peuvent utiliser le service Azure Rights Management à partir d’Azure Information Protection, voir comment les applications peuvent prendre en charge [le service Azure Rights Management](https://docs.microsoft.com/information-protection/understand-explore/applications-support).

Azure RMS est intégré à Microsoft 365 et disponible pour tous les clients. Pour configurer Microsoft 365 afin qu’il utilise Azure RMS, voir Configurer IRM pour utiliser Azure Rights Management et Configurer la Gestion des droits de [l’information (IRM)](https://technet.microsoft.com/library/dn151475(v=exchg.150).aspx)dans le Centre d’administration SharePoint. Si vous utilisez un serveur Active Directory (AD) RMS local, vous pouvez également configurer IRM pour utiliser un serveur [AD RMS](https://docs.microsoft.com/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server)local, mais nous vous recommandons vivement de migrer vers [Azure RMS](https://docs.microsoft.com/azure/information-protection/migrate-from-ad-rms-to-azure-rms) pour utiliser de nouvelles fonctionnalités telles que la collaboration sécurisée avec d’autres organisations.

Lorsque vous protégez les données client avec Azure RMS, Azure RMS utilise une clé asymétrique RSA 2048 bits avec algorithme de hachage SHA-256 pour l’intégrité afin de chiffrer les données. La clé symétrique pour les documents et la messagerie Office est AES 128 bits. Pour chaque document ou e-mail protégé par Azure RMS, Azure RMS crée une clé AES unique (la « clé de contenu ») et cette clé est incorporée dans le document et persiste par le biais des éditions du document. La clé de contenu est protégée avec la clé RSA de l’organisation (la « clé de client Azure Information Protection ») dans le cadre de la stratégie dans le document, et la stratégie est également signée par l’auteur du document. Cette clé de client est commune à tous les documents et messages électroniques protégés par Azure RMS pour l’organisation et cette clé ne peut être modifiée que par un administrateur Azure Information Protection si l’organisation utilise une clé de client gérée par le client. Pour plus d’informations sur les contrôles de chiffrement utilisés par Azure RMS, voir [Comment fonctionne Azure RMS ? Sous le capot](https://docs.microsoft.com/information-protection/understand-explore/how-does-it-work).

Dans une implémentation Azure RMS par défaut, Microsoft génère et gère la clé racine unique pour chaque client. Les clients peuvent gérer le cycle de vie de leur clé racine dans Azure RMS avec Azure Key Vault Services à l’aide d’une méthode de gestion de clé appelée [ByOK (Bring Your Own Key)](https://docs.microsoft.com/azure/information-protection/plan-implement-tenant-key) qui vous permet de générer votre clé dans des HSM locaux (modules de sécurité matériels) et de garder le contrôle de cette clé après le transfert vers les HSM validés de niveau 2 fiPS 140-2 de Microsoft. L’accès à la clé racine n’est accordé à aucun personnel, car les clés ne peuvent pas être exportées ou extraites des HSM qui les protègent. En outre, vous pouvez accéder à un journal en temps quasi réel affichant tous les accès à la clé racine à tout moment. Pour plus d’informations, voir [Journalisation et analyse de l’utilisation d’Azure Rights Management.](https://docs.microsoft.com/azure/information-protection/log-analyze-usage)

Azure Rights Management contribue à atténuer les menaces telles que le câblage, les attaques de l’intermédiaire de l’utilisateur, le vol de données et les violations involontaires des stratégies de partage d’organisation. En même temps, tout accès non autorisé à des données client en transit ou au repos par un utilisateur non autorisé qui ne prend pas les autorisations appropriées est empêché via des stratégies qui suivent ces données, réduisant ainsi le risque que ces données tombent entre de mauvaises mains, en connaissance de cause ou sans le savoir, et en fournissant des fonctions de protection contre la perte de données. S’il est utilisé dans le cadre d’Azure Information Protection, Azure RMS fournit également des fonctionnalités de classification et d’étiquetage des données, de marquage de contenu, de suivi d’accès aux documents et de révocation d’accès. Pour en savoir plus sur ces fonctionnalités, voir Qu’est-ce [qu’Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection), feuille de route de déploiement Azure Information [Protection](https://docs.microsoft.com/information-protection/plan-design/deployment-roadmap)et didacticiel de démarrage rapide pour Azure [Information Protection](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>Secure Multipurpose Internet Mail Extension

S/MIME (Secure/Multipurpose Internet Mail Extensions) est une norme pour le chiffrement à clé publique et la signature numérique des données MIME. S/MIME est défini dans les RFCs 3369, 3370, 3850, 3851 et autres. Il permet à un utilisateur de chiffrer un e-mail et de signer numériquement un e-mail. Un e-mail chiffré à l’aide de S/MIME peut uniquement être déchiffré par le destinataire de l’e-mail à l’aide de sa clé privée, qui est uniquement disponible pour ce destinataire. En tant que tel, les e-mails ne peuvent pas être déchiffrés par toute personne autre que le destinataire du message électronique.

[Microsoft prend en charge S/MIME.](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx) Les certificats publics sont distribués dans Active Directory local du client et stockés dans des attributs qui peuvent être répliqués vers un client Microsoft 365. Les clés privées qui correspondent aux clés publiques restent en local et ne sont jamais transmises à Office 365. Les utilisateurs peuvent composer, chiffrer, déchiffrer, lire et signer numériquement des messages électroniques entre deux utilisateurs d’une organisation à l’aide d’Outlook, d’Outlook sur le web Exchange ActiveSync clients. Pour plus d’informations, voir [chiffrement S/MIME maintenant dans Office 365.](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/)

## <a name="office-365-message-encryption"></a>Chiffrement de messages Office 365

Le chiffrement de messages [Office 365](https://products.office.com/exchange/office-365-message-encryption) (OME) intégré à [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) (AIP) vous permet d’envoyer des messages chiffrés et protégés par des droits à tout le monde. OME atténue les menaces telles que le coup de fil et les attaques de l’homme au milieu, ainsi que d’autres menaces, telles que l’accès non autorisé aux données par un utilisateur non autorisé qui n’a pas les autorisations appropriées. Nous avons réalisé des investissements qui vous offrent une expérience de messagerie électronique plus simple, plus intuitive et sécurisée, qui s’est intégrée à Azure Information Protection. Vous pouvez protéger les messages envoyés à partir de Microsoft 365 à toute personne à l’intérieur ou à l’extérieur de votre organisation. Ces messages peuvent être vus sur un ensemble divers de clients de messagerie à l’aide de n’importe quelle identité, y compris Azure Active Directory, le compte Microsoft et les ID Google. Pour plus d’informations sur la façon dont votre organisation peut utiliser les messages chiffrés, voir Chiffrement de [messages Office 365.](https://docs.microsoft.com/microsoft-365/compliance/ome)

## <a name="transport-layer-security"></a>Transport Layer Security

Si vous souhaitez assurer une communication sécurisée avec un partenaire, vous pouvez utiliser des connecteurs entrants et sortants pour assurer la sécurité et l’intégrité des messages. Vous pouvez configurer le TLS entrant et sortant forcé sur chaque connecteur à l’aide d’un certificat. L’utilisation d’un canal SMTP chiffré peut empêcher le vol de données via une attaque de l’intermédiaire de l’utilisateur. Pour plus d’informations, voir [comment Exchange Online utilise TLS pour sécuriser les connexions de messagerie.](https://docs.microsoft.com/microsoft-365/compliance/exchange-online-uses-tls-to-secure-email-connections)

## <a name="domain-keys-identified-mail"></a>Messages identifiés par des clés de domaine

Exchange Online Protection (EOP) et Exchange Online prennent en charge la validation entrante des messages DKIM (Domain Keys Identified Mail). Il s'agit d'une méthode de validation des messages envoyés depuis le domaine dont ils indiquent provenir et qui n'ont pas été usurpés par un autre utilisateur. Il lie un message électronique à l’organisation responsable de son envoi et fait partie d’un paradigme plus large de chiffrement des messages électroniques. Pour plus d’informations sur les trois parties de ce paradigme, voir :

- [Configurer SPF pour empêcher l’usurpation d’identité](https://docs.microsoft.com/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](https://docs.microsoft.com/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [Utiliser DMARC pour valider les messages électroniques](https://docs.microsoft.com/office365/SecurityCompliance/use-dmarc-to-validate-email)
