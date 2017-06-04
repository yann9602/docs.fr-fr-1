---
title: "&lt;add&gt; de &lt;allowAccounts&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;add&gt; de &lt;allowAccounts&gt;
Indique un compte d'utilisateur correspondant aux processus qui hébergent des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] et qui disposent d'un accès de connexion au service de partage.  
  
 \<system.serviceModel.activation\>  
  
## Syntaxe  
  
```  
  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|securityIdentifier|Chaîne indiquant un identificateur unique utilisée pour identifier un compte d'utilisateur.  Les valeurs par défaut sont LocalSystem, Administrateurs, NS, LS et IIS\_USRS.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<allowAccounts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Collection d'éléments de configuration qui contiennent un attribut `securityIdentifier` permettant de spécifier les comptes d'utilisateurs correspondant aux processus qui hébergent des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] et qui disposent d'un accès de connexion au service de partage.|  
  
## Exemple  
 L'exemple de configuration suivant ajoute à cette collection les cinq identificateurs par défaut correspondant aux comptes d'utilisateurs.  
  
```  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>   
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>   
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>   
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>