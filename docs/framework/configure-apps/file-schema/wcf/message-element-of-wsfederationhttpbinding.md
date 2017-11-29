---
title: "&lt;message&gt;, élément de &lt;wsFederationHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b17a6325b84382d9d22b4da3ccf7e1598dc42df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a>&lt;message&gt;, élément de &lt;wsFederationHttpBinding&gt;
Définit les paramètres de la sécurité au niveau du message pour le [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 \<système. ServiceModel >  
\<liaisons >  
\<wsFederatedBinding >  
\<liaison >  
\<sécurité >  
\<message >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<wsFederationBinding>  
     <binding >  
         <security>  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                              <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
                        </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
         </message>  
      </security>  
   </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|algorithmSuite|Définit les algorithmes de chiffrement de message et de clé de type WRAP. Consultez le tableau « attribut algorithmSuite » pour des valeurs valides de cet attribut. La valeur par défaut est `Basic256`.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).|  
|issuedKeyType|Spécifie le type de clé à émettre. Les valeurs valides sont les suivantes :<br /><br /> -SymmetricKey<br />-PublicKey<br /><br /> La valeur par défaut est `SymmetricKey`. Cet attribut est de type <xref:System.IdentityModel.Tokens.SecurityKeyType>.|  
|issuedTokenType|Chaîne qui contient un URI qui spécifie le type de jeton à publier. La valeur par défaut est `null`.|  
|negotiateServiceCredential|Valeur booléenne qui spécifie si les informations d'identification du service doivent être échangées dans le cadre de la négociation ou si elles sont disponibles hors bande. La valeur par défaut est `true`, ce qui signifie que les informations d'identification du service sont négociées.|  
  
## <a name="algorithmsuite-attribute"></a>Attribut algorithmSuite  
  
|Valeur|Description|  
|-----------|-----------------|  
|Basic128|Utilisez le chiffrement Basic128, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic192|Utilisez le chiffrement Basic192, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic256|Utilisez le chiffrement Basic256, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic256Rsa15|Utilisez Basic256 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic192Rsa15|Utilisez Basic192 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|TripleDes|Utilisez le chiffrement TripleDes, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic128Rsa15|Utilisez Basic128 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|TripleDesRsa15|Utilisez le chiffrement TripleDes, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic128Sha256|Utilisez Basic128 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic192Sha256|Utilisez Basic192 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic256Sha256|Utilisez Basic256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|TripleDesSha256|Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.|  
|Basic128Sha256Rsa15|Utilisez Basic128 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic192Sha256Rsa15|Utilisez Aes192 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic256Sha256Rsa15|Utilisez Basic256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|TripleDesSha256Rsa15|Utilisez TripleDes pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Spécifie une collection de types de revendication pour cette liaison. Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.|  
|issuer|Spécifie un point de terminaison qui publie un jeton de sécurité. Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.|  
|issuerMetadata|Spécifie l'adresse de point de terminaison de l'émetteur.|  
|[\<tokenRequestParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|Collection de paramètres de demande de jeton. Chaque paramètre est un élément XML.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|Définit les paramètres de sécurité d’une liaison.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 `System.ServiceModel.Configuration.FederatedMessageSecurityElement`[Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<liaison >](../../../../../docs/framework/misc/binding.md)
