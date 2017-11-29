---
title: "Comment : localiser des assemblys à l'aide de DEVPATH"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 70448f7ce4c00274dde14bace603e5c8852bf148
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Comment : localiser des assemblys à l'aide de DEVPATH
Les développeurs souhaitent peut-être vous assurer qu’un assembly partagé qu’ils développent fonctionne correctement avec plusieurs applications. Au lieu de mettre en permanence l’assembly dans le global assembly cache au cours du cycle de développement, le développeur peut créer une variable d’environnement DEVPATH pointant vers le répertoire de sortie de l’assembly.  
  
 Par exemple, supposez que vous générez un assembly partagé appelé MySharedAssembly et le répertoire de sortie soit C:\MySharedAssembly\Debug. Vous pouvez placer C:\MySharedAssembly\Debug dans la variable DEVPATH. Vous devez spécifier le [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) élément dans le fichier de configuration machine. Cet élément indique le common language runtime d’utiliser DEVPATH pour localiser les assemblys.  
  
 L’assembly partagé doit être détectable par le runtime.  Pour spécifier un répertoire privé pour la résolution des références d’assembly, utilisez le [ \<codeBase > élément](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) ou [ \<probing > élément](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) dans un fichier de configuration, comme décrit dans [Spécifiant l’emplacement d’un Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).  Vous pouvez également placer l’assembly dans un sous-répertoire du répertoire de l’application. Pour plus d’informations, consultez [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
>  Il s’agit d’une fonctionnalité avancée, conçue uniquement pour le développement.  
  
 L’exemple suivant montre comment le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.  
  
## <a name="example"></a>Exemple  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Ce paramètre par défaut est false.  
  
> [!NOTE]
>  Utilisez ce paramètre uniquement au moment du développement. Le runtime ne vérifie pas les versions sur les assemblys avec nom fort trouvés dans DEVPATH. Elle utilise simplement le premier assembly qu’il trouve.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des applications .NET Framework](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
