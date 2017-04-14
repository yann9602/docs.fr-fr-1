---
title: "&lt;serviceTokenResolver&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;serviceTokenResolver&gt;
Inscrit le résolveur de jeton de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jeton.  Le résolveur de jeton de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
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
|type|Spécifie le type du résolveur token service.  Soit la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type ou un type qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.  Pour plus d'informations sur la façon de spécifier la `type` d'attribut, consultez [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences).  Obligatoire.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fournit les gestionnaires de jetons de configuration pour une collection de sécurité.|  
  
## Notes  
 Le résolveur de jeton de service peut servir à résoudre le jeton de chiffrement sur les jetons et les messages entrants.  Il est utilisé pour récupérer la clé doit être utilisée pour décrypter les jetons entrants.  Vous devez spécifier la `type` attribut.  Le type spécifié peut être soit <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.  
  
 Certains gestionnaires de jetons permettent de spécifier des paramètres de résolution de jeton du service dans configuration.  Paramètres de gestionnaires de jetons individuels remplacent celles spécifiées dans la collection de gestionnaires de jeton de sécurité.  
  
> [!NOTE]
>  Spécifiant le `<serviceTokenResolver>` élément comme un élément enfant de le [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément a été dépréciée, mais est toujours pris en charge pour la compatibilité ascendante.  Paramètres de la `<securityTokenHandlerConfiguration>` élément prévalent sur ceux sur le `<identityConfiguration>` élément.  
  
## Exemple  
  
```  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```