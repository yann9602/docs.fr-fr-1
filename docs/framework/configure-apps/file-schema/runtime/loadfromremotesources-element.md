---
title: '&lt;loadFromRemoteSources&gt; Element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13b42405a0faf721c46476aadaa0cff8163883c1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadFromRemoteSources&gt; Element
Spécifie si les assemblys à partir de sources distantes doivent se voir accorder une confiance totale.  
  
> [!NOTE]
>  Si vous avez été redirigé vers cette rubrique en raison d’un message d’erreur dans la liste d’erreurs de projet Visual Studio ou une erreur de build, consultez [Comment : utiliser un Assembly à partir du Web dans Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).  
  
 \<configuration>  
\<runtime>  
\<loadFromRemoteSources>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si un assembly est chargé à partir de sources distantes doit-elle se voir accorder une confiance totale.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|N’accordez pas une confiance totale aux applications à partir de sources distantes. Il s'agit de la valeur par défaut.|  
|`true`|Accorder une confiance totale aux applications à partir de sources distantes.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 Dans le .NET Framework version 3.5 et les versions antérieures, si vous avez chargé un assembly à partir d’un emplacement distant, l’assembly s’exécute une confiance partielle avec un jeu d’autorisations qui dépendaient de la zone dans laquelle il a été chargé. Par exemple, si vous avez chargé un assembly à partir d’un site Web, il a été chargé dans la zone Internet et accordé le jeu d’autorisations Internet. En d’autres termes, elle est exécutée dans un bac à sable Internet. Si vous essayez d’exécuter cet assembly dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] et versions ultérieures, une exception est levée ; vous devez soit créer explicitement un bac à sable pour l’assembly (consultez [Comment : exécuter Partially Trusted Code dans un bac à sable](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), ou l’exécuter en mode confiance totale.  
  
 Le `<loadFromRemoteSources>` élément vous permet de spécifier que les assemblys qui auraient été exécutées de confiance partiel dans les versions antérieures du .NET Framework doivent être exécutées entièrement confiance dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures. Par défaut, les assemblys à distance ne s’exécutent pas dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures. Pour exécuter un assembly distant, vous devez l’exécuter avec une confiance totale ou créer un bac à sable <xref:System.AppDomain> dans pour son exécution.  
  
> [!NOTE]
>  Dans le [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblys sur des partages de réseau local sont exécutées avec une confiance totale par défaut ; vous n’avez pas à activer le `<loadFromRemoteSources>` élément.  
  
> [!NOTE]
>  Si une application a été copiée à partir du web, il est signalé par Windows comme étant une application web, même s’il se trouve sur l’ordinateur local. Vous pouvez modifier cette désignation en modifiant les propriétés du fichier, ou vous pouvez utiliser la `<loadFromRemoteSources>` élément à accorder à l’assembly de confiance totale. En guise d’alternative, vous pouvez utiliser la <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> méthode pour charger un assembly local que le système d’exploitation a signalé comme ayant été chargé à partir du web.  
  
 Le `enabled` d’attribut pour cet élément est efficace uniquement lorsque la sécurité d’accès du code (CAS) est désactivée. Par défaut, la stratégie CAS est désactivée dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures. Si vous définissez `enabled` à `true`, applications distantes sont de confiance totale.  
  
 Si `<loadFromRemoteSources>``enabled` n’est pas définie `true`, une exception est levée dans les conditions suivantes :  
  
-   Le comportement de bac à sable du domaine actuel est différent de son comportement dans le [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]. Cela nécessite la stratégie CAS doit être désactivée et le domaine actuel, ne pas à sable (sandbox).  
  
-   L’assembly en cours de chargement n’est pas à partir de la `MyComputer` zone.  
  
> [!NOTE]
>  Vous risquez d’obtenir un <xref:System.IO.FileLoadException> dans une application Windows Virtual PC lorsque vous essayez de charger un fichier à partir des dossiers liés sur l’ordinateur hôte. Cette erreur peut également se produire lorsque vous essayez de charger un fichier à partir d’un dossier lié via [Services Bureau à distance](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services). Pour éviter l’exception, définissez `enabled` à `true`.  
  
 Définition de la `<loadFromRemoteSources>` élément `true` empêche cette exception ne soit levée. Il permet de spécifier que vous ne comptez pas sur le common language runtime pour le bac à sable les assemblys chargés pour la sécurité, et qu’ils soient autorisés à exécuter en tant qu’une confiance totale.  
  
> [!IMPORTANT]
>  Si l’assembly ne doit pas s’exécuter en mode confiance totale, ne définissez pas cet élément de configuration. Au lieu de cela, créez un bac à sable <xref:System.AppDomain> dans lequel charger l’assembly.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément est généralement utilisé dans le fichier de configuration d’application, mais il peut être utilisé dans d’autres fichiers de configuration en fonction du contexte. Pour plus d’informations, consultez l’article [plus implicite utilise de la stratégie CAS : loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) dans le blog de sécurité .NET.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment accorder une confiance totale aux applications à partir de sources distantes.  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilise plus implicite de stratégie CAS : loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
