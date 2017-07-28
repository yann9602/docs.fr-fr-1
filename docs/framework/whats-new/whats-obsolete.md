---
title: "Éléments obsolètes dans la bibliothèque de classes .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7afe9496ca116ed0c330c4ff9e7c3a855249cf14
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="what39s-obsolete-in-the-net-framework-class-library"></a>Éléments obsolètes dans la bibliothèque de classes .NET Framework
Le .NET Framework évolue. Chaque nouvelle version comporte de nouveaux types et membres de type qui fournissent de nouvelles fonctionnalités. Les types existants et leurs membres évoluent aussi. Par exemple, certains types deviennent moins importants quand la technologie qu'ils prennent en charge est remplacée par une nouvelle, tandis que certaines méthodes sont remplacées par de nouvelles méthodes qui sont soit plus pratiques, soit plus complètes.  
  
 Le .NET Framework et le Common Language Runtime s'efforcent de prendre en charge une compatibilité descendante (ce qui permet aux applications développées avec une version du .NET Framework de fonctionner sur la version suivante). Il est donc difficile de simplement supprimer un type ou un membre de type. C'est pourquoi le .NET Framework indique plutôt qu'un type ou un membre de type ne doit plus être utilisé en le marquant comme obsolète ou déprécié. Le fait de déprécier un type ou un membre implique de le marquer afin que les développeurs soient informés de sa future suppression et qu'ils aient le temps de réagir. Toutefois, le code existant qui utilise le type ou le membre en question continue à fonctionner dans la nouvelle version du .NET Framework.  
  
> [!NOTE]
>  Les termes *obsolète* et *déprécié* ont la même signification quand ils sont appliqués aux types et aux membres du .NET Framework.  
  
## <a name="the-obsoleteattribute-attribute"></a>Attribut ObsoleteAttribute  
 Le .NET Framework indique qu'un type ou membre de type est obsolète en le marquant avec l'attribut <xref:System.ObsoleteAttribute>. L'application de cet attribut à un type ou membre indique que ce type ou membre sera supprimé dans une version ultérieure du .NET Framework sans casser le code compilé qui utilise ce membre.  
  
 En plus d'indiquer qu'un type ou un membre de type est obsolète, <xref:System.ObsoleteAttribute> définit comment le compilateur gère le code source qui inclut ce type ou membre. Le compilateur peut compiler le code en émettant un message d'avertissement, ou il peut traiter l'utilisation du type ou du membre comme une erreur. Dans le premier cas, le code peut être compilé avec succès, mais un message d'avertissement indique que le type ou le membre est obsolète. Dans le deuxième cas, la compilation échoue.  
  
 Même si la compilation produit une erreur au lieu d'un message d'avertissement, <xref:System.ObsoleteAttribute> n'affecte pas le comportement au moment de l'exécution. Autrement dit, les applications qui utilisent le type ou le membre et qui ont été compilées avec succès s'exécuteront toujours correctement. Seule une tentative de recompilation d'une application qui utilise le type ou le membre échoue.  
  
## <a name="how-to-handle-obsolete-types-and-members"></a>Comment gérer des types et membres obsolètes  
 Quand vous mettez à niveau et recompilez du code existant, l'utilisation d'un type ou d'un membre obsolète qui génère un avertissement du compilateur dans votre application est parfaitement acceptable. Toutefois, vous devez examiner le message d'avertissement du compilateur pour déterminer si vous devez modifier le code de votre application. Si le message ne pointe pas vers une alternative appropriée, vous devez faire l'une ou l'autre des opérations suivantes :  
  
-   Modifiez votre code en supprimant l'utilisation du type ou membre, si possible.  
  
     ou  
  
-   Examinez la documentation de ce domaine technologique pour savoir que faire face à des éléments obsolètes.  
  
 Vous pouvez choisir de ne pas recompiler le code existant avec une version ultérieure du .NET Framework. À la place, vous pouvez spécifier la version du .NET Framework sur laquelle votre code compilé existant est exécuté. Supposons, par exemple, que vous possédiez une application nommée app1.exe qui a été compilée avec le [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], mais que vous souhaitiez que l'application s'exécute avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Ce processus implique les étapes suivantes :  
  
1.  Créez un fichier de configuration pour votre fichier exécutable principal et nommez-le *Nom_app*.exe.config, où *Nom_app* est le nom du fichier exécutable de l’application. Pour l'application nommée app1.exe de notre exemple, vous devez créer un fichier de configuration intitulé app1.exe.config.  
  
2.  Ajoutez le code suivant au fichier de configuration.  
  
    ```xml  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 Le tableau suivant répertorie les valeurs de chaîne que vous pouvez assigner à l'attribut `version` pour cibler une version spécifique du .NET Framework.  
  
|Version du .NET Framework|Chaîne `version`|
|-|-|  
|4.7|v4.0|  
|4.6 (y compris 4.6.1 et 4.6.2)|v4.0|  
|4.5 (y compris 4.5.1 et 4.5.2)|v4.0|  
|4|v4.0|  
|3.5|v2.0.50727|  
|2.0|v2.0.50727|  
|1.1|v1.1.4322|  
|1.0|v1.0.3705|  
  
## <a name="obsolete-lists-for-the-net-framework-45-and-46"></a>Listes des éléments obsolètes pour le .NET Framework 4.5 et 4.6  
 [Types obsolètes](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [Membres obsolètes](../../../docs/framework/whats-new/obsolete-members.md)  
  
## <a name="obsolete-lists-for-previous-versions"></a>Listes des éléments obsolètes pour les versions antérieures  
 [Types obsolètes dans le .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [Membres obsolètes dans le .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [Liste des éléments obsolètes pour le .NET Framework 3.5](http://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [Liste des éléments obsolètes pour le .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkID=125264)  
  
## <a name="see-also"></a>Voir aussi  
 [\<supportedRuntime>, élément](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)

