---
title: Fonctionnement des étiquettes de confidentialité dans les applications Office
ms.author: greglin
author: greg-lindsay
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Avec les étiquettes de sensibilité, vous pouvez classer et protéger le contenu sensible, tout en vous assurant que la productivité et la possibilité de collaboration des membres de votre organisation ne sont pas altérées. Vous pouvez utiliser les étiquettes de sensibilité afin d’appliquer des paramètres de protection, comme le chiffrement ou les filigranes, sur le contenu étiqueté.
ms.openlocfilehash: 1de7eadfcf95a54917c1d5e2cc0d42cc1ad486a5
ms.sourcegitcommit: c7f7ff463141f7d7f0970b64e5a04341db7e4fa8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "37378649"
---
# <a name="how-sensitivity-labels-work-in-office-apps"></a>Fonctionnement des étiquettes de confidentialité dans les applications Office

## <a name="what-prerequisites-are-there-to-use-sensitivity-labels-in-office-applications"></a>Quels sont les conditions préalables à l’utilisation des étiquettes de confidentialité dans les applications Office ?

### <a name="common-requirements"></a>Conditions courantes 

- Les étiquettes de confidentialité unifiée doivent être [configurées et publiées dans le Centre de sécurité et conformité](https://aka.ms/managemip)
- Les utilisateurs doivent être connectés à Office à l’aide de leur compte professionnel.
- Les utilisateurs doivent disposer d’une licence Office 365 E3 ou supérieure.

### <a name="additional-requirements-for-office-for-windows"></a>Conditions requises supplémentaires pour Office pour Windows 

- Le client Azure Information Protection ne doit pas être exécuté dans Office. Voir aussi : [Les étiquettes de confidentialité peuvent-elles fonctionner avec le client Azure Information Protection dans Office pour Windows ?](#can-sensitivity-labels-run-alongside-the-azure-information-protection-client-in-office-for-windows).

### <a name="additional-requirements-for-outlook-on-all-platforms"></a>Conditions requises supplémentaires pour Outlook sur toutes les plateformes 

- Dans la configuration d’étiquette, si vous activez le marquage de contenu, vous devez utiliser Exchange Online pour que ce marquage de contenu soit insérée en transit.

## <a name="what-sensitivity-label-capabilities-are-supported-in-office-today"></a>Quelles fonctionnalités d’étiquette de confidentialité sont prises en charge dans Office actuellement ? 

<table border="1" cellspacing="0" cellpadding="0">
<th><font size="-1">Fonctionnalité<th><font size="-1">Windows<th><font size="-1">Mac<th colspan="2"><font size="-1">iOS<th colspan="2"><font size="-1">Android<th colspan="2"><font size="-1">Web</tr>
<tr><td>

<td><font size="-1"> Word<br>
Excel<br>
PowerPoint<br>
Outlook


<td><font size="-1"> Word<br>
Excel<br>
PowerPoint<br>
Outlook

<td><font size="-1"> Word<br>
Excel<br>
PowerPoint
<td><font size="-1">Outlook

<td><font size="-1"> Word<br>
Excel<br>
PowerPoint
<td><font size="-1">Outlook

<td><font size="-1"> Word<br>
Excel<br>
PowerPoint
<td><font size="-1"> Outlook </b>
</tr>

<tr>
<td><font size="-1">Appliquer, modifier ou supprimer manuellement une étiquette<td><font size="-1"><b>Oui</b><br><font size="-1">1910+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">16.21.0+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">2.21+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1"><b>Oui</b><br><font size="-1">16.0.11231+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup><td><font size="-1">Bientôt disponible<sup>3</sup>

<tr>
<td><font size="-1"><a href="https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels#what-label-policies-can-do">Appliquer une étiquette par défaut</a>
<td><font size="-1"><b>Oui</b><br><font size="-1">1910+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">16.21.0+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">2.21+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1"><b>Oui</b><br><font size="-1">16.0.11231+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>

<tr><td><font size="-1"><a href="https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels#what-label-policies-can-do">Demander une justification pour changer une étiquette</a><sup>1</sup>
<td><font size="-1"><b>Oui</b><br><font size="-1">1910+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">16.21.0+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">2.21+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1"><b>Oui</b><br><font size="-1">16.0.11231+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>

<tr><td><font size="-1"><a href="https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels#what-label-policies-can-do">Fournir un lien d’aide vers une page d’aide personnalisée</a>
<td><font size="-1"><b>Oui</b><br><font size="-1">1910+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">16.21.0+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">2.21+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1"><b>Oui</b><br><font size="-1">16.0.11231+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>

<tr><td><font size="-1"><a href="https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels#what-sensitivity-labels-can-do">Marquer le contenu</a>
<td><font size="-1"><b>Oui</b><br><font size="-1">1910+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">16.21.0+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">2.21+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1"><b>Oui</b><br><font size="-1">16.0.11231+</font
><td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>

<tr><td><font size="-1">Attribuer des autorisations prédéfinies
<td><font size="-1"><b>Oui</b><br><font size="-1">1910+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">16.21.0+</font>

<td><font size="-1"><b>Oui</b><br><font size="-1">2.21+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1"><b>Oui</b><br><font size="-1">16.0.11231+</font>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">Bientôt disponible<sup>3</sup>

<tr><td><font size="-1"><a href="https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions">Permettre aux utilisateurs d’attribuer des autorisations</a>
<td><font size="-1"><b>Oui</b><sup>2</sup><br><font size="-1">1910+</font>

<td><font size="-1"><b>Oui</b><sup>2</sup><br><font size="-1">16.21.0+</font>

<td><font size="-1">À DÉFINIR
<td><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">À DÉFINIR<td
><font size="-1">Bientôt disponible<sup>3</sup>
<td><font size="-1">À DÉFINIR
<td><font size="-1">Bientôt disponible<sup>3</sup>

<tr><td><font size="-1">Envoyer les données d’<a href="https://docs.microsoft.com/microsoft-365/compliance/label-analytics">analyse des étiquettes</a> pour les administrateurs
<td><font size="-1">À DÉFINIR

<td><font size="-1">À DÉFINIR

<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR

<tr><td><font size="-1">Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents
<td><font size="-1">À DÉFINIR

<td><font size="-1">À DÉFINIR

<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR

<tr><td><font size="-1"><a href="https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically">Appliquer automatiquement une étiquette de confidentialité au contenu</a>
<td><font size="-1">À DÉFINIR

<td><font size="-1">À DÉFINIR

<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
<td><font size="-1">À DÉFINIR
</table>

<br><sup>1</sup>Si elles sont configurées, les utilisateurs sont invités à justifier les rétrogradations d’étiquettes. Toutefois, les données de justification ne sont pas encore disponibles pour les administrateurs. Elles seront disponibles lorsque la fonctionnalité « envoyer les données d’analyse des étiquettes pour les administrateurs » est prise en charge.
<br><sup>2</sup>Permettre aux utilisateurs d'attribuer des autorisations n'est actuellement disponible que dans Outlook pour Windows et Mac. La disponibilité pour Word, Excel et PowerPoint est à définir.
<br><sup>3</sup>Prévu pour le quatrième trimestre de l'année civile 2019.

## <a name="when-do-content-marks-or-encryption-get-applied-after-content-is-given-a-sensitivity-label"></a>Quand les marques de contenu ou le chiffrement sont-ils appliqués une fois qu’une étiquette de confidentialité est attribuée au contenu ?

| Application | Marquage du contenu | Chiffrement
| --- | --- | --- |
| Word, Excel, PowerPoint sur toutes les plateformes | Immédiatement | Immédiatement |
| Outlook pour PC et Mac | Une fois l’e-mail envoyé par Exchange Online | Immédiatement |
| Word, Excel, PowerPoint sur toutes les plateformes | Une fois l’e-mail envoyé par Exchange Online | Une fois l’e-mail envoyé par Exchange Online |

## <a name="can-sensitivity-labels-run-alongside-the-azure-information-protection-client-in-office-for-windows"></a>Les étiquettes de confidentialité peuvent-elles fonctionner avec le client Azure Information Protection dans Office pour Windows ?

Non. Les étiquettes de confidentialité sont désactivées si le client Azure Information Protection est chargé dans Office pour Windows.

Si le client Azure Information Protection est installé sur votre ordinateur, mais que vous préférez utiliser des étiquettes de confidentialité, vous pouvez :

1. Configurer le paramètre de stratégie de groupe  **Utiliser la fonctionnalité Confidentialité d’Office pour appliquer et afficher les étiquettes de confidentialité**, accessible sous **Configuration utilisateur/Modèles d’administration/Microsoft Office 2016/Paramètres de sécurité**.

  >Remarque : ce paramètre peut être déployé via les mécanismes de déploiement de stratégie de groupe traditionnels ou par le [service de stratégie Cloud Office](https://docs.microsoft.com/DeployOffice/overview-office-cloud-policy-service). 
 
  Vous pouvez également désinstaller ou  [désactiver](https://support.office.com/article/view-manage-and-install-add-ins-in-office-programs-16278816-1948-4028-91e5-76dca5380f8d) le client Azure Information Protection. 

2. Redémarrez toutes les applications Office.

## <a name="will-sensitivity-labels-be-supported-in-non-subscription-versions-of-office-like-office-2016-or-office-2019"></a>Les étiquettes de confidentialité seront-elles prises en charge dans les versions sans abonnement d'Office comme Office 2016 ou Office 2019 ?

Non. Les étiquettes de confidentialité ne sont prises en charge que dans l’abonnement Office 365 et ne seront pas prises en charge dans les versions sans abonnement. Toutefois, le client de l’étiquetage unifié Azure Information Protection peut être utilisé dans les versions sans abonnement d’Office. 

## <a name="i-previously-deployed-protection-templates-before-setting-up-sensitivity-labels-where-did-they-go"></a>J’ai précédemment déployé les modèles de protection avant de configurer les étiquettes de confidentialité. Où sont-ils passés ?

Les [modèles de protection](https://docs.microsoft.com/azure/information-protection/configure-policy-templates) définis par l’administrateur sont masqués dans l’expérience utilisateur Office lorsque les étiquettes de confidentialité sont activées, car elles sont redondantes avec les étiquettes de confidentialité pour lesquelles le chiffrement est activé. 

## <a name="can-a-file-or-email-have-more-than-one-classification"></a>Un fichier ou un e-mail peut-il avoir plusieurs classifications ?

Les utilisateurs ne peuvent sélectionner qu’une seule étiquette à la fois pour chaque document ou e-mail, ce qui se traduit souvent par une seule classification. Toutefois, si les utilisateurs sélectionnent une sous-étiquette, cela a pour effet d’appliquer deux étiquettes en même temps : une étiquette primaire et une étiquette secondaire. L’utilisation de sous-étiquettes permet à un fichier d’avoir deux classifications indiquant une relation parent/enfant pour un niveau de contrôle supplémentaire. 

Par exemple, l’étiquette  **Confidentiel**  pourrait contenir des sous-étiquettes telles que  **Légal** et **Finance**. Vous pouvez appliquer différentes marquages visuels de classification et différents modèles de gestion des droits à ces sous-étiquettes. Un utilisateur ne peut pas sélectionner l’étiquette **Confidentiel** , mais une seule de ses sous-étiquettes, par exemple  **Légal**. Par conséquent, l’étiquette qu’ils voient s’afficher est **Confidentiel** / **Légal**. Les métadonnées associées à ce fichier incluent une propriété de texte personnalisée pour **Confidentiel**, une propriété de texte personnalisée pour **Légal** et une autre qui contient les deux valeurs (**Confidentiel Légal**). 

Lorsque vous utilisez des sous-étiquettes, ne configurez pas les marquages visuels, la protection et les conditions sur l’étiquette primaire. Lorsque vous utilisez des sous-niveaux, configurez ces paramètres sur la sous-étiquette uniquement. Si vous configurez ces paramètres sur l’étiquette primaire et sur sa sous-étiquette, les paramètres de la sous-étiquette sont prioritaires.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Lorsqu’un message électronique est étiqueté, les pièces jointes reçoivent-elles automatiquement la même étiquette ?

Non. Lorsque vous étiquetez un message électronique comportant des pièces jointes, celles-ci n’héritent pas de la même étiquette. Les pièces jointes restent sans étiquette ou ne conservent qu’une étiquette appliquée séparément. Toutefois, si l’étiquette de l’e-mail applique la protection, cette protection est appliquée aux pièces jointes Office.

## <a name="additional-resources"></a>Ressources supplémentaires

[Forum aux questions sur la classification et l’étiquetage dans Azure Information Protection](https://docs.microsoft.com/azure/information-protection/faqs-infoprotect)<br>
[Appliquer des étiquettes de niveau de confidentialité à vos documents et vos e-mails dans Office](https://support.office.com/article/apply-sensitivity-labels-to-your-documents-and-email-within-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)