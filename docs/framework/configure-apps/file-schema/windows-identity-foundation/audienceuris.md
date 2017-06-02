---
title: "&lt;audienceUris&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;audienceUris&gt;
Spécifie le jeu d'URI qui sont des identificateurs acceptables de la partie utilisatrice \(RP\).  Les jetons ne seront pas acceptées à moins qu'ils ont une portée limitées pour l'un de l'audience URI autorisée.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|mode|Un <xref:System.IdentityModel.Selectors.AudienceUriMode> valeur qui spécifie si la restriction de l'audience doit être appliquée à un jeton entrant.  Les valeurs possibles sont "Toujours," "Jamais" et « BearerKeyOnly ».  La valeur par défaut est « Toujours ».  Facultatif.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`<add value=xs:string>`|Ajoute l'URI spécifié par le `value` d'attribut à la collection audienceUris.  L'attribut `value` est requis.  L'URI est sensible à la casse.|  
|`<clear>`|Efface la collection audienceUris.  Tous les identificateurs sont supprimés de la collection.|  
|`<remove value=xs:string>`|Supprime l'URI spécifié par le `value` l'attribut de la collection audienceUris.  L'attribut `value` est requis.  L'URI est sensible à la casse.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fournit les gestionnaires de jetons de configuration pour une collection de sécurité.|  
  
## Notes  
 Par défaut, la collection est vide ; Utilisez `<add>`, `<clear>`, et `<remove>` éléments pour modifier la collection.  <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>et <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objets utilisent les valeurs dans la collection d'URI audience pour configurer toutes autorisées audience restrictions URI dans <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objets.  
  
 Le `<audienceUris>` élément est représenté par la <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> classe.  Un URI individuel ajouté à la collection est représentée par la <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.  
  
> [!NOTE]
>  L'utilisation de la `<audienceUris>` élément comme un élément enfant de le [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément a été dépréciée, mais est toujours pris en charge pour la compatibilité ascendante.  Paramètres de la `<securityTokenHandlerConfiguration>` élément prévalent sur ceux sur le `<identityConfiguration>` élément.  
  
## Exemple  
 Le code XML suivant montre comment configurer l'audience URI acceptable pour une application.  Cet exemple configure un URI unique.  Jetons de portée pour cet URI seront acceptées, tous les autres seront rejetés.  
  
```  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```