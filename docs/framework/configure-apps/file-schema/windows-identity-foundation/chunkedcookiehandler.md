---
title: "&lt;chunkedCookieHandler&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;chunkedCookieHandler&gt;
Configure la <xref:System.IdentityModel.Services.ChunkedCookieHandler>.  Cet élément ne peut être présent si la `mode` l'attribut de la `<cookieHandler>` élément est « Default » ou « Chunked ».  
  
## Syntaxe  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|chunkSize|La taille maximale, en caractères, les données de cookie HTTP pour tout un cookie HTTP.  Vous devez être prudent lorsque vous ajustez la taille du segment.  Les navigateurs Web ont différentes limites sur la taille des cookies et le nombre autorisé par domaine.  Par exemple, la spécification Netscape d'origine prévu ces limites : total de 300 cookies, 4096 octets par en\-tête cookie \(y compris les métadonnées, pas seulement la valeur du cookie\) et 20 cookies par domaine.  La valeur par défaut est 2000.  Obligatoire.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Configure la <xref:System.IdentityModel.Services.CookieHandler> qui le <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) utilise pour lire et écrire des cookies.|  
  
## Notes  
 Lorsque vous spécifiez une <xref:System.IdentityModel.Services.ChunkedCookieHandler> en définissant la `mode` attribut de la `<cookieHandler>` élément « Default » ou « Chunked », vous pouvez spécifier la taille de segment, le Gestionnaire de cookie utilise pour lire et écrire des cookies en incluant une `<chunkedCookieHandler>` élément enfant et paramètre sa `chunkSize` attribut.  Si la `<chunkedCookieHandler>` élément n'est pas présent, la taille de segment par défaut de 2000 octets est utilisée.  Cet élément ne peut pas être spécifié quand le `mode` attribut est défini sur « Custom ».  
  
 Le `<chunkedCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.  
  
## Exemple  
 L'exemple suivant configure un gestionnaire de cookie mémorisé en bloc qui écrit des cookies dans des segments de 3 000 octets.  
  
```  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>