---
title: "&lt;loadFromRemoteSources&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "loadFromRemoteSources, élément"
  - "<loadFromRemoteSources>, élément"
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: 31
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 31
---
# &lt;loadFromRemoteSources&gt;, &#233;l&#233;ment
Spécifie si la confiance totale doit être accordée aux assemblys de sources distantes.  
  
> [!NOTE]
>  Si vous avez été dirigé vers cette rubrique en raison d'un message d'erreur dans la liste des erreurs de projet Visual Studio ou d'une erreur de build, consultez [Comment : utiliser un assembly à partir du Web dans Visual Studio](http://msdn.microsoft.com/fr-fr/d8635b63-89a0-41aa-90f4-f351b2111070).  
  
## Syntaxe  
  
```  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si la confiance totale doit être accordée à un assembly chargé à partir de sources distantes.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|N'accordez pas une confiance totale aux applications à partir de sources distantes.  Il s'agit de la valeur par défaut.|  
|`true`|Accordez la confiance totale aux applications de sources distantes.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## Notes  
 Dans le .NET Framework version 3.5 et versions antérieures, si vous chargiez un assembly à partir d'un emplacement distant, l'assembly s'exécutait avec un niveau de confiance partiel, avec un jeu accordé qui dépendait de la zone dans laquelle il était chargé.  Par exemple, si vous avez chargé l'assembly à partir d'un site Web, il était chargé dans la zone Internet et se voyait accorder le jeu d'autorisations Internet.  En d'autres termes, il s'exécutait dans un bac à sable \(sandbox\) Internet.  Si vous essayez d'exécuter cet assembly avec [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou avec des versions ultérieures, une exception est levée ; vous devez créer explicitement un bac à sable \(sandbox\) pour l'assembly \(voir [Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable \(sandbox\)](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)\), ou l'exécuter avec une confiance totale.  
  
 L'élément `<loadFromRemoteSources>` vous permet de spécifier que les assemblys qui auraient du s'exécuter avec un niveau de confiance partiel dans les versions antérieures du .NET Framework devront exécutés avec une confiance totale avec [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et avec les versions ultérieures.  Par défaut, les assemblys distants ne fonctionnent pas dans [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures.  Pour exécuter un assembly distants, vous devez soit de exécutez\-le sous la forme d'un niveau de confiance totale ou créer <xref:System.AppDomain> sandboxed dans lequel l'exécuter.  
  
> [!NOTE]
>  Dans [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], les assemblys sur les partages réseau local sont exécutés comme complètement approuvé par défaut ; vous ne devez pas activer l'élément `<loadFromRemoteSources>`.  
  
> [!NOTE]
>  Si une application a été copiée à partir du Web, elle est signalée par Windows comme une application Web, même si elle réside sur l'ordinateur local.  Vous pouvez modifier cette désignation en modifiant les propriétés de fichier ou utiliser l'élément `<loadFromRemoteSources>` pour accorder la confiance totale à l'assembly.  Ou bien, vous pouvez utiliser la méthode de <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> pour le chargement d'un assembly local que le système d'exploitation est marqué comme ayant été chargé à partir du Web.  
  
 L'attribut `enabled` pour cet élément est efficace uniquement lorsque la sécurité d'accès du code est désactivée.  Par défaut, la stratégie CAS est désactivée dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures.  Si vous affectez à `enabled` la valeur `true`, les applications distantes sont de confiance totale.  
  
 Si `<loadFromRemoteSources>` `enabled` n'a pas la valeur `true`, une exception est levée dans les conditions suivantes :  
  
-   Le comportement de bac à sable du domaine actuel est différent de son comportement dans [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  La stratégie CAS doit être désactivée et le domaine actuel ne doit pas être en mode Bac à sable \(sandbox\).  
  
-   L'assembly chargé ne provient pas de la zone `MyComputer`.  
  
> [!NOTE]
>  Vous pouvez obtenir une <xref:System.IO.FileLoadException> sur un PC virtuel Windows lorsque vous essayez de charger un fichier à partir des dossiers liés sur l'ordinateur d'hébergement.  Cette erreur peut également se produire lorsque vous essayez de charger un fichier d'un dossier lié \(plus [Services de bureau à distance](http://go.microsoft.com/fwlink/?LinkId=182775) des services Terminal Server\).  Pour éviter une exception, affectez à `enabled` la valeur `true`.  
  
 La définition de l'élément `<loadFromRemoteSources>` à `true` empêche la levée de cette exception.  Cela vous permet de spécifier que vous ne comptez pas sur le Common Language Runtime pour passer en mode Bac à sable \(sandbox\) les assemblys chargés pour des raisons de sécurité, et qu'ils peuvent être autorisés à s'exécuter avec une confiance totale.  
  
> [!IMPORTANT]
>  Si l'assembly ne doit pas s'exécuter avec une confiance totale, ne définissez pas cet élément de configuration.  Créez à la place un <xref:System.AppDomain> bac à sable dans lequel charger l'assembly.  
  
## Fichier de configuration  
 Cet élément est utilisé en général dans le fichier de configuration de l'application, mais peut être utilisée dans d'autres fichiers de configuration selon le contexte.  Pour plus d'informations, consultez l'article [Utilisations plus implicites de stratégie CAS : loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) du blog de sécurité.NET.  
  
## Exemple  
 L'exemple suivant indique comment accorder la confiance totale aux applications de sources distantes.  
  
```  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Utilisations plus implicites de stratégie CAS : loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)   
 [Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable \(sandbox\)](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)   
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)