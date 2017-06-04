---
title: "&lt;customCookieHandler&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# &lt;customCookieHandler&gt;
Définit le type de Gestionnaire de cookie personnalisé.  Cet élément ne peut être présent si la `mode` l'attribut de la `<cookieHandler>` élément est « Custom ».  Le type personnalisé doit être dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
## Syntaxe  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode=”Custom”>  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Spécifie un type personnalisé qui dérive de la <xref:System.IdentityModel.Services.CookieHandler> classe.  Pour plus d'informations sur la façon de spécifier la `type` d'attribut, consultez [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Configure la <xref:System.IdentityModel.Services.CookieHandler> qui le <xref:System.IdentityModel.Services.SessionAuthenticationModule> utilise pour lire et écrire des cookies.|  
  
## Notes  
 Lorsque vous spécifiez un gestionnaire de cookie personnalisé en définissant la `mode` l'attribut de la `<cookieHandler>` élément « Personnalisé », vous devez spécifier le type du Gestionnaire de cookie personnalisé en incluant une `<customCookieHandler>` élément enfant qui fait référence au type de Gestionnaire de cookie.  Cet élément ne peut pas être spécifié quand le `mode` attribut a la valeur « Chunked » ou « Default ».  Gestionnaires de cookie personnalisé doivent dériver de la <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
 Le `<customCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.  
  
## Exemple  
 L'exemple suivant configure le SAM pour utiliser un gestionnaire de cookie personnalisé de type `MyNamespace.MyCustomCookieHandler`.  
  
```  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Services.CookieHandler>