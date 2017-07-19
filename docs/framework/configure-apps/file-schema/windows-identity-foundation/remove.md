---
title: "&lt;remove&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;remove&gt;
Supprime le Gestionnaire de jetons de sécurité spécifié dans la collection de gestionnaires de jeton.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Le nom de type CLR du jeton gestionnaire à supprimer.  Pour plus d'informations sur la façon de spécifier la `type` d'attribut, consultez [Custom Type References](http://msdn.microsoft.com/fr-fr/7286d2e3-c63d-49fd-abdc-ce2705f22c24).  Obligatoire.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jeton de sécurité qui sont enregistrés avec le point de terminaison.|  
  
## Exemple  
 Le code XML suivant illustre l'utilisation de la `<add>` et `<remove>` éléments pour remplacer le Gestionnaire de jetons de session par défaut avec un gestionnaire de jetons de session personnalisé.  Le code XML provient de la `ClaimsAwareWebFarm` exemple.  
  
```  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```