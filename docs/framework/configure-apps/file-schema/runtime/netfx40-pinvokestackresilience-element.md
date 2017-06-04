---
title: "&lt;NetFx40_PInvokeStackResilience&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<NetFx40_PInvokeStackResilience> (élément)"
  - "NetFx40_PInvokeStackResilience (élément)"
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;NetFx40_PInvokeStackResilience&gt;, &#233;l&#233;ment
Spécifie si le runtime résout automatiquement les déclarations d'appel de code non managé au moment de l'exécution, au prix de transitions plus lentes entre le code managé et non managé.  
  
## Syntaxe  
  
```  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime détecte des déclarations d'appel de code non managé incorrectes et résout automatiquement la pile au moment de l'exécution sur les plateformes 32 bits.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`0`|Le runtime utilise l'architecture de marshaling d'interopérabilité la plus rapide introduite dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], qui ne détecte pas et ne résout pas les déclarations d'appel de plateforme.  Il s'agit de la valeur par défaut.|  
|`1`|Le runtime utilise les transitions lentes qui détectent et résolvent les déclarations d'appel de plateforme.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## Notes  
 Cet élément vous permet d'échanger du marshaling d'interopérabilité plus rapide contre une résistance de temps d'exécution pour des déclarations d'appel de plateforme incorrectes.  
  
 Lors du démarrage avec le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], une architecture de marshaling d'interopérabilité simplifiée offre une amélioration significative des performances pour les transitions du code managé au code non managé.  Dans les versions antérieures du .NET Framework, la couche de marshaling détectait des déclarations d'appel de code non managé sur les plateformes 32 bits et résolvait automatiquement la pile.  La nouvelle architecture de marshaling élimine cette étape.  Par conséquent, les transitions sont très rapides, mais une déclaration d'appel de code non managé peut provoquer une défaillance de programme.  
  
 Pour faciliter la détection des déclarations incorrectes pendant le développement, le débogage Visual Studio a été amélioré.  L'Assistant Débogage managé \(MDA\) [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) vous notifie des déclarations d'appel de plateforme incorrectes lorsque votre application s'exécute avec le débogueur attaché.  
  
 Pour les scénarios dans lesquels votre application utilise des composants que vous ne pouvez pas recompiler et les déclarations d'appel de plateforme sont incorrectes, vous pouvez utiliser l'élément `NetFx40_PInvokeStackResilience`.  L'ajout de cet élément à votre fichier de configuration de l'application avec `enabled="1"` opte pour un mode de compatibilité avec le comportement des versions antérieures du .NET Framework, au prix de transitions plus lentes.  Les assemblys compilés avec les versions antérieures du .NET Framework optent automatiquement pour ce mode de compatibilité et n'ont pas besoin de cet élément.  
  
## Fichier de configuration  
 Cet élément peut être utilisé uniquement dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment opter pour une résistance accrue contre les déclarations d'appel de plateforme incorrectes pour une application, mais avec des transitions plus lentes entre le code managé et le code non managé.  
  
```  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)