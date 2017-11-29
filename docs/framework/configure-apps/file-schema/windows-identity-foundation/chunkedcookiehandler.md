---
title: '&lt;chunkedCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 906a9e7cafca14dc4ee13dcb9eb9e59736464fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
Configure le <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Cet élément peut uniquement être présent si la `mode` attribut de la `<cookieHandler>` élément est « Default » ou « Mémorisé en bloc ».  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
\<chunkedCookieHandler >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|taille du segment|La taille maximale, en caractères, les données de cookie HTTP pour un cookie HTTP. Vous devez être prudent lors de l’ajustement de la taille du segment. Navigateurs Web ont des limites différentes sur la taille des cookies et le nombre autorisé par domaine. Par exemple, la spécification Netscape d’origine prévu ces limites : total de 300 cookies, 4096 octets par en-tête cookie (y compris les métadonnées, pas seulement la valeur du cookie) et 20 cookies par domaine. La valeur par défaut est 2000. Obligatoire.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Configure le <xref:System.IdentityModel.Services.CookieHandler> qui le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) utilise pour lire et écrire des cookies.|  
  
## <a name="remarks"></a>Remarques  
 Lorsque vous spécifiez un <xref:System.IdentityModel.Services.ChunkedCookieHandler> en définissant le `mode` attribut de la `<cookieHandler>` élément « Default » ou « Chunked », vous pouvez spécifier la taille de segment par le Gestionnaire de cookie pour lire et écrire des cookies en incluant un `<chunkedCookieHandler>` élément enfant et définition de sa `chunkSize` attribut. Si le `<chunkedCookieHandler>` élément n’est pas présent, la taille de segment par défaut de 2 000 octets est utilisée. Cet élément ne peut pas être spécifié quand le `mode` attribut est défini sur « Custom ».  
  
 Le `<chunkedCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant configure un gestionnaire de cookie mémorisé en bloc qui écrit des cookies par segments de 3 000 octets.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
