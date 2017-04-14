---
title: "&lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;add&gt;
Ajoute le Gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jeton.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Le nom de type CLR du jeton gestionnaire à ajouter.  Pour plus d'informations sur la façon de spécifier la `type` d'attribut, consultez [Custom Type References](http://msdn.microsoft.com/fr-fr/7286d2e3-c63d-49fd-abdc-ce2705f22c24).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|Fournit la configuration pour le <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> \(classe\), le <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée d'une de ces classes.|  
|[\<sessionTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|Fournit la configuration pour le <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou les classes dérivées.|  
|[\<userNameSecurityTokenHandlerRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|Fournit la configuration pour le <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou les classes dérivées.|  
|[\<x509SecurityTokenHandlerRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|Fournit la configuration facultative pour le <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou les classes dérivées.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jeton de sécurité qui sont enregistrés avec le point de terminaison.|  
  
## Notes  
 Le `<add>` élément peut accepter un seul élément enfant qui spécifie la configuration pour le Gestionnaire de jeton.  Cela dépend si la classe du gestionnaire référencé par le biais de la `type` attribut de la `<add>` élément prend en charge cette fonctionnalité.  Classes de Gestionnaire de jetons qui offrent cette fonctionnalité doivent exposer un constructeur qui prend un <xref:System.Xml.XmlElement> objet.  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Parmi les classes de Gestionnaire de jetons de sécurité intégrée fournissent cette fonctionnalité.  These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
>  La collection de gestionnaires de jeton peut contenir qu'un seul gestionnaire de n'importe quel type de donnée.  Cela signifie, par exemple, que si vous voulez ajouter un gestionnaire qui est dérivé de la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe à la collection, vous devez d'abord supprimer la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, qui est présente par défaut, à partir de la collection.  Vous pouvez utiliser le [\<remove\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) élément pour supprimer un seul gestionnaire de la collecte ou l'utilisation du [\<vide\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) élément à supprimer tous les gestionnaires de la collection.  
  
 Paramètres spécifiés dans un gestionnaire remplacent les paramètres équivalents spécifiés dans la collection de gestionnaires de jeton sous la [\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) élément et ceux spécifiés au niveau du service sous la [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément.  
  
## Exemple  
 Le code XML suivant illustre l'utilisation de la `<add>` et `<remove>` éléments pour remplacer le Gestionnaire de jetons de session par défaut avec un gestionnaire de jetons de session personnalisé.  Le code XML provient de la `ClaimsAwareWebFarm` exemple.  
  
```  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```