<a name="crit-infoprotect-step1"></a>
### <a name="required-security-and-information-protection-levels-for-your-organization-are-defined"></a>Obligatoire : définition des niveaux de protection des informations et de sécurité pour votre organisation

Vous avez planifié et défini les niveaux de sécurité dont votre organisation a besoin. Ces niveaux définissent un niveau minimal de sécurité et des niveaux supplémentaires pour les informations de plus en plus sensibles et la sécurité requise de leurs données.

Vous utilisez au moins trois niveaux de sécurité :

- Baseline
- Sensible
- Hautement réglementé

Si nécessaire, l’[Étape 1](../infoprotect-define-sec-infoprotect-levels.md) peut vous aider à répondre à cette exigence. 

<a name="crit-infoprotect-step3"></a>
### <a name="required-increased-security-for-microsoft-365-is-configured"></a>Obligatoire : le paramètre Sécurité accrue de Microsoft 365 est configuré

Vous avez configuré les paramètres de [Sécurité accrue d’Office 365](https://docs.microsoft.com/office365/securitycompliance/tenant-wide-setup-for-increased-security) suivants :

- Stratégies de gestion des menaces dans le Centre de sécurité Microsoft 365
- Autres paramètres à l’échelle du client Exchange Online
- Stratégies de partage à l’échelle du client dans le Centre d’administration SharePoint Online
- Paramètres d’Azure Active Directory (Azure AD)

Vous avez également [activé Office 365 - Protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams](https://docs.microsoft.com/office365/securitycompliance/turn-on-atp-for-spo-odb-and-teams).

Si nécessaire, l’[Étape 3](../infoprotect-configure-increased-security-office-365.md) peut vous aider à répondre à cette exigence. 

<a name="crit-infoprotect-step2"></a>
### <a name="optional-classification-is-configured-across-your-environment"></a>Facultatif : configurer la classification au sein de votre environnement

Vous avez travaillé avec vos équipes juridiques et de conformité afin de développer une classification et un système d’étiquetage appropriés pour les stratégies de sécurité et de gouvernance des données de votre organisation. 

Ces stratégies correspondent à la configuration et au déploiement de ce qui suit :

- Types de données sensibles
- Étiquettes de rétention
- Étiquettes de niveau de confidentialité
- Étiquettes Azure Information Protection

Si nécessaire, l’[Étape 2](../infoprotect-configure-classification.md) peut vous aider à répondre à cette exigence. 


<a name="crit-infoprotect-step4"></a>
### <a name="optional-windows-information-protection-is-deployed-across-your-environment"></a>Facultatif : la Protection des informations Windows est déployée dans votre environnement

Une stratégie Intune est déployée et appliquée sur vos appareils Windows 10 Entreprise inscrits, qui définit les aspects suivants :

- Applications à protéger.
- Niveau de protection.
- Étendue de la protection.

Si nécessaire, l’[Étape 4](../infoprotect-deploy-windows-information-protection.md) peut vous aider à respecter cette exigence. 

<a name="crit-infoprotect-step5"></a>
### <a name="optional-office-365-data-loss-prevention-dlp-is-deployed"></a>Facultatif : la protection contre la perte de données Office 365 (DLP) est déployée.

Vous avez analysé, testé, puis déployé l’ensemble des stratégies DLP (avec des emplacements et des règles assortis de conditions et d’actions) que votre organisation exige pour protéger les données des clients et d’autres types de données privées, ainsi que pour se conformer aux réglementations et exigences sectorielles et régionales.

Votre personnel chargé de la conformité et de la sécurité des données utilise le tableau de bord de sécurité et conformité Office 365 pour surveiller les incidents DLP.

Si nécessaire, l’[Étape 5](../infoprotect-data-loss-prevention.md) peut vous aider à respecter cette exigence. 


<a name="crit-infoprotect-step6"></a>
### <a name="optional-configure-privileged-access-management-in-office-365"></a>Facultatif : configurer la gestion des accès privilégiés pour Office 365

Vous avez utilisé les informations de la rubrique [Configurer la gestion des accès privilégiés dans Office 365](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration) pour activer l’accès privilégié et créer une ou plusieurs stratégies d’accès privilégié au sein de votre organisation. Vous avez configuré ces stratégies et l’accès juste-à-temps est activé pour l’accès aux données sensibles ou aux paramètres de configuration critiques.

Si nécessaire, l’[Étape 6](../infoprotect-configure-privileged-access-management.md) peut vous aider à respecter cette exigence. 
