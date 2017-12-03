---
title: "Scénarios non pris en charge"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bb2646a500db299f164dce34fb062a509f90047
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="unsupported-scenarios"></a>Scénarios non pris en charge
Pour diverses raisons, certains modes de sécurité ne sont pas pris en charge par [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Par exemple, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Édition familiale n'implémentant pas les protocoles d'authentification SSPI ou Kerberos, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge, sur ce type de plateforme, l'exécution des services utilisant l'authentification Windows. En revanche, d'autres mécanismes d'authentification, tels que l'association nom d'utilisateur/mot de passe et l'authentification intégrée HTTP/HTTPS, sont pris en charge lorsque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute sous Windows XP Édition familiale.  
  
## <a name="impersonation-scenarios"></a>Emprunt d'identité  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Il se peut que l'identité empruntée ne fonctionne pas correctement lorsque des clients passent des appels asynchrones.  
 Lorsqu'un client WCF passe des appels asynchrones à un service WCF à l'aide de l'authentification Windows sous un emprunt d'identité, l'authentification peut se produire avec l'identité du processus client au lieu de l'identité empruntée.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP avec le cookie de jeton de contexte sécurisé activé  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge l'emprunt d'identité et une exception <xref:System.InvalidOperationException> est levée dans les cas suivants :  
  
-   Le système d'exploitation correspond à [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Le mode d'authentification aboutit à un identité Windows.  
  
-   La propriété <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> de l'objet <xref:System.ServiceModel.OperationBehaviorAttribute> a la valeur <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
-   Un jeton de contexte de sécurité basé sur l'état est créé (cette création est désactivée par défaut).  
  
 Ce jeton peut uniquement être crée à l’aide d’une liaison personnalisée. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : créer un contexte de sécurité jeton pour une Session sécurisée](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).) Dans le code, ce jeton est activé en créant un élément de liaison de sécurité (<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) à l'aide de la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> ou <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> et en affectant au paramètre `requireCancellation` la valeur `false`. Ce paramètre concerne la mise en cache du jeton. L'affectation de la valeur `false` à ce paramètre permet d'activer la fonctionnalité de jeton basé sur l'état.  
  
 Ou bien, dans la configuration, le jeton est activé en créant un <`customBinding`>, puis en ajoutant un <`security`> élément et affecter le `authenticationMode` attribut SecureConversation et le `requireSecurityContextCancellation` attribut `true`.  
  
> [!NOTE]
>  Les spécifications précédentes sont spécifiques. Par exemple, l'élément <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> crée un élément de liaison qui aboutit à une identité Windows, mais cet élément ne définit pas de jeton de contexte de sécurité avec état. Vous pouvez donc utiliser cet élément avec l'option `Required` de [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Éventuel conflit avec ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] permettent l'activation ou la désactivation de l'emprunt d'identité. Lorsque [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] héberge une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], un conflit peut survenir entre les paramètres de la configuration [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. En cas de conflit, le paramètre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est prioritaire, sauf si la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> a la valeur <xref:System.ServiceModel.ImpersonationOption.NotAllowed>, auquel cas c'est le paramètre d'emprunt d'identité de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] qui est prioritaire.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Les chargements d'assembly risquent d'échouer lorsque l'emprunt d'identité est activé  
 Si le contexte emprunté ne dispose de droits d'accès permettant le chargement d'un assembly et que l'objet CLR tente pour la première fois de le charger pour AppDomain, <xref:System.AppDomain> met l'échec en mémoire cache. Les tentatives suivantes pour charger cet assembly échoueront également, même après restauration de l'emprunt d'identité et même si le contexte restauré dispose cette fois de droits d'accès permettant de charger cet assembly. Ces échecs successifs se produisent car l'objet CLR ne tente pas une nouvelle fois de charger l'assembly après la modification du contexte utilisateur. Vous devez redémarrer le domaine d'application pour résoudre ce problème.  
  
> [!NOTE]
>  La valeur par défaut de la propriété <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> de la classe <xref:System.ServiceModel.Security.WindowsClientCredential> est <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. Dans la plupart des cas, les contextes d'emprunt d'identité de niveau identification ne disposent pas de droits leur permettant de charger d'autres assemblys. Il s'agit de la valeur par défaut. Il est donc important de garder à l'esprit ce cas très fréquent. L'emprunt d'identité de niveau identification se produit lorsque le processus d'emprunt ne dispose pas du droit `SeImpersonate`. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Délégation et emprunt d’identité](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>La délégation nécessite la négociation des informations d'identification  
 Pour pouvoir utiliser le protocole d'authentification Kerberos avec la délégation, vous devez implémenter le protocole Kerberos en utilisant la négociation des informations d'identification (parfois appelé Kerberos multi-segment ou multi-étape). Si vous implémentez l'authentification Kerberos sans négociation d'informations d'identification (parfois appelée Kerberos « one-shot » ou Kerberos « single-leg »), une exception est levée. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]comment implémenter la négociation des informations d’identification, consultez [débogage des erreurs de l’authentification Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Chiffrement  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256 uniquement pris en charge lorsque des clés symétriques sont utilisées  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge différents algorithmes Digest de création de chiffrement et de signature que vous pouvez spécifier à l'aide de la suite algorithmique figurant dans les liaisons fournies par le système. Afin d'améliorer la sécurité, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge les algorithmes Secure Hash Algorithm (SHA) 2 et plus particulièrement les algorithmes SHA-256, lesquels permettent la création de signatures hachées Digest. Cette version prend uniquement en charge SHA-256 lorsque des clés symétriques, telles que les clés Kerberos sont utilisées et lorsque les messages ne sont pas signés par les certificats X.509. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge les signatures RSA (utilisées dans les certificats X.509) à l'aide du hachage SHA-256 en raison de l'absence de prise en charge de RSA-SHA256 dans [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>Hachage SHA-256 conforme FIPS non pris en charge  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prenant pas en charge les hachages SHA-256 conformes FIPS, les suites algorithmiques qui utilisent SHA-256 ne sont pas prises en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sur les systèmes nécessitant l'utilisation d'algorithmes conformes FIPS.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Les algorithmes conformes FIPS risquent d'échouer si le registre est modifié  
 Vous pouvez activer ou désactiver les algorithmes conformes FIPS en utilisant les paramètres de sécurité locale de l'outil enfichable MMC. Ces paramètres sont également accessibles à partir du registre. Remarque : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge l'utilisation du registre pour modifier ces paramètres. Si vous affectez à ces paramètres une valeur autre que 1 ou 0, cela risque de générer des résultats incohérents entre CLR et le système d'exploitation.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>Limites d'utilisation concernant le chiffrement AES conforme FIPS  
 Le chiffrement AES conforme FIPS n'est pas compatible avec les rappels duplex dans le cadre des emprunts d'identité de niveau identification.  
  
### <a name="cngksp-certificates"></a>Certificats CNG/KSP  
 *Cryptography API : Next Generation (CNG)* se substitue à CryptoAPI. Cette API est disponible dans le code non managé sur [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] et versions ultérieures de Windows.  
  
 .NET framework 4.6.1 et versions antérieures ne prennent pas en charge ces certificats car ils utilisent CryptoAPI hérité pour gérer les certificats CNG/KSP. L’utilisation de ces certificats avec .NET Framework 4.6.1 et versions antérieures, une exception.  
  
 Pour indiquer si un certificat utilise KSP, deux méthodes sont possibles :  
  
-   Exécutez `p/invoke` de `CertGetCertificateContextProperty` et inspectez `dwProvType` sur la `CertGetCertificateContextProperty` retournée.  
  
-   Utilisez la `certutil` commande à partir de la ligne de commande pour interroger des certificats. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tâches Certutil pour le dépannage des certificats](http://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>La sécurité de message échouera si l'emprunt d'identité ASP.NET est utilisé et si la compatibilité ASP.NET est requise  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge l'utilisation combinée des paramètres suivants, une telle utilisation pouvant empêcher l'authentification client :  
  
-   L'emprunt d'identité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] est activé. Cette opération est effectuée dans le fichier Web.config en définissant le `impersonate` attribut de la <`identity`> élément `true`.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]mode de compatibilité est activé en définissant le `aspNetCompatibilityEnabled` attribut de la [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) à `true`.  
  
-   Le mode de sécurité de niveau message est utilisé.  
  
 Pour contourner cette difficulté, il suffit de désactiver le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Si le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] est requis, désactivez la fonctionnalité d'emprunt d'identité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et utilisez la fonctionnalité d'emprunt d'identité fournie par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à la place. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Délégation et emprunt d’identité](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>Échec d'adresse littérale IPv6  
 Les demandes de sécurité échouent si le client et le service s'exécutent sur le même ordinateur et les adresses littérales IPv6 sont utilisées pour le service.  
  
 L'utilisation d'adresses littérales IPv6 est possible à condition que le client et le service ne s'exécutent pas sur le même ordinateur.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Échecs de récupération WSDL avec approbation fédérée  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert exactement un document WSDL pour chaque nœud dans la chaîne d'approbation fédérée. Veillez à ne pas définir de boucle lors de la spécification des points de terminaison. Des boucles peuvent résulter de l'utilisation d'un téléchargement WSDL de chaînes d'approbation fédérée avec au moins deux liens dans le même document WSDL. Un scénario courant pouvant induire ce problème est un service fédéré où le serveur de jeton de sécurité et le service sont contenus dans le même ServiceHost.  
  
 Un service comportant les trois adresses de point de terminaison suivantes est un exemple illustrant cette situation :  
  
-   http://localhost/CalculatorService/service (le service)  
  
-   http://localhost/CalculatorService/issue_ticket (le STS)  
  
-   http://localhost/CalculatorService/mex (le point de terminaison de métadonnées)  
  
 Ce scénario lève une exception.  
  
 Pour qu'il fonctionne, vous pouvez placer le point de terminaison `issue_ticket` ailleurs.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>Risques de perte des attributs d'importation WSDL  
 WCF perd la trace des attributs sur un élément `<wst:Claims>` dans un modèle `RST` lors de l'exécution d'une importation WSDL. Cela se produit pendant une importation WSDL si vous spécifiez directement `<Claims>` dans `WSFederationHttpBinding.Security.Message.TokenRequestParameters` ou `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` au lieu d'utiliser directement les collections de types de revendication.  Puisque l'importation perd les attributs, la liaison ne fait pas l'aller-retour correctement dans WSDL et est donc incorrecte du côté client.  
  
 pour corriger cette situation, il convient de modifier directement la liaison sur le client après l’importation.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Divulgation d’informations](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Élévation de privilèges](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Déni de Service](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Falsification](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Attaques par relecture](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
