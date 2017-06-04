---
title: "&lt;issuedTokenParameters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;issuedTokenParameters&gt;
Indique les paramètres d'un jeton de sécurité émis dans un scénario de sécurité fédéré.  
  
## Syntaxe  
  
```  
  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## Type  
 `Type`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|defaultMessageSecurityVersion|Spécifie les versions des caractéristiques de sécurité \(WS\-Security, WS\-Trust, WS\-Secure Conversation et WS\-Security Policy\) devant être prises en charge par la liaison.  Cette valeur est de type <xref:System.ServiceModel.MessageSecurityVersion>.|  
|inclusionMode|Indique les spécifications d'inclusion de jeton.  Cet attribut est de type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.|  
|keySize|Entier qui spécifie la taille de clé de jeton.  La valeur par défaut est 256.|  
|keyType|Valeur correcte de <xref:System.IdentityModel.Tokens.SecurityKeyType> indiquant le type de clé.  La valeur par défaut est `SymmetricKey`.|  
|tokenType|Chaîne indiquant le type de jeton.  La valeur par défaut est « http:\/\/docs.oasis\-open.org\/wss\/oasis\-wss\-saml\-token\-profile\-1.1\#SAML ».|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<additionalRequestParameters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|Collection d'éléments de configuration indiquant des paramètres de demande supplémentaires.|  
|[\<claimTypeRequirements\>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Spécifie une collection de types de revendications requis.<br /><br /> Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.  Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.  Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.|  
|[\<issuer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|Élément de configuration qui spécifie le point de terminaison émettant le jeton actuel.|  
|[\<issuerMetadata\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|Élément de configuration qui spécifie l'adresse de point de terminaison correspondant aux métadonnées de l'émetteur de jeton.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<secureConversationBootstrap\>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Spécifie les options de sécurité d'une liaison personnalisée.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>   
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>   
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [Custom Binding Security](../../../../../docs/framework/wcf/samples/custom-binding-security.md)   
 [Identité du service et authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)   
 [Fédération et jetons émis](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)