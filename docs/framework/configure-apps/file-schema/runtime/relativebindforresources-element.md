---
title: "&lt;relativeBindForResources&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<relativeBindForResources> (élément)"
  - "RelativeBindForResources (élément)"
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;relativeBindForResources&gt;, &#233;l&#233;ment
Optimise le test des assemblys satellites.  
  
## Syntaxe  
  
```vb  
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le CLR \(common langage runtime\) optimise le test des assemblys satellites.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Le runtime n'optimise pas le test des assemblys satellites.  Valeur par défaut.|  
|`true`|Le runtime optimise le test des assemblys satellites.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## Notes  
 Généralement le gestionnaire de ressources test des ressources, comme décrit dans la rubrique de [Empaquetage et déploiement de ressources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  Cela signifie que lorsque le gestionnaire de ressources recherche une version localisée spécifique d'une ressource, il peut rechercher dans le Global Assembly Cache, regardez dans un dossier spécifique à la culture de la base de code de l'application, le programme d'installation de fenêtres de requête pour les assemblys satellites, et déclenche l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>.  L'élément `<relativeBindForResources>` optimise la façon dont le gestionnaire de ressources recherche les assemblys satellites.  Il peut améliorer les performances en sondant des ressources dans les conditions suivantes :  
  
-   Une fois l'assembly satellite est déployé dans le même emplacement que l'assembly de code managé.  En d'autres termes, si l'assembly de code est installé dans le Global Assembly Cache, les assemblys satellites doivent également être installés à cet endroit.  Si l'assembly de code est installé dans la base de code de l'application, les assemblys satellites doivent également être installés dans un dossier spécifique à la culture de la base de code.  
  
-   Lorsque Windows Installer n'est pas utilisé ou est rarement utilisée uniquement pour l'installation à la demande des assemblys satellites.  
  
-   Lorsque le code d'application ne gère pas l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>.  
  
 Parametrer l'attribut `enabled` de l'élément `<relativeBindForResources>` à `true` optimise le test du gestionnaire de ressources pour les assemblys satellites comme suit :  
  
-   Elle utilise l'emplacement de l'assembly de code parent pour rechercher l'assembly satellite.  
  
-   Il ne fait pas le requête auprès de Windows Installer pour les assemblys satellites.  
  
-   Cela ne déclenche pas l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>.  
  
## Voir aussi  
 [Empaquetage et déploiement de ressources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)   
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)