---
title: "&lt;add&gt;, élément de &lt;claimTypeRequirements&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc644648ad244eb642f96fdc93213fbd38152f48
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a>&lt;add&gt;, élément de &lt;claimTypeRequirements&gt;
Spécifie les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées. Par exemple, les services déclarent les exigences relatives aux informations d’identification entrantes devant posséder un certain jeu de types de revendications.  
  
 \<système. ServiceModel >  
\<liaisons >  
\<wsFederatedBinding >  
\<liaison >  
\<sécurité >  
\<message >  
\<claimTypeRequirements >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
        isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|claimType|URI définissant le type d'une revendication. Par exemple, pour acheter un produit d'un site Web, l'utilisateur doit présenter une carte de crédit valide avec limite de crédit suffisante. Le type de revendication est l'URI de la carte de crédit.|  
|isOptional|Valeur booléenne indiquant si l'opération concerne une revendication facultative. Affectez à cet attribut la valeur `false` si c'est une revendication requise.<br /><br /> Vous pouvez utiliser cet attribut lorsque le service demande certaines informations sans pour autant les exiger. Par exemple, si vous décidez que l'utilisateur doit indiquer ses prénom, nom et adresse mais pas forcément son numéro de téléphone.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Spécifie une collection de types de revendications requis. Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes. Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini. Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d’identification fédérées.|  
  
## <a name="remarks"></a>Remarques  
 Dans un scénario fédéré, les services déclarent les exigences relatives aux informations d’identification entrantes. Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini. Cette spécification est explicitée dans une stratégie de sécurité. Lorsqu’un client requiert des informations d’identification à partir d’un service fédéré (CardSpace, par exemple), il indique ces exigences dans une demande de jeton (RequestSecurityToken) afin que le service fédéré puisse publier ces informations et répondre aux exigences.  
  
## <a name="example"></a>Exemple  
 La configuration suivante ajoute deux exigences de type de revendication à une liaison de sécurité.  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
