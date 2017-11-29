---
title: "Réflexion et .NET Native"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9e4bdc26815feab7910e7518f7cd691a1f4dece
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-and-net-native"></a>Réflexion et .NET Native
Dans le .NET Framework, le développement managé prend en charge la métaprogrammation par le biais de l'API de réflexion. La réflexion vous permet d'inspecter les objets dans une application, d'appeler des méthodes sur les objets découverts au cours de l'inspection et de générer de nouveaux types au moment de l'exécution. Elle prend également en charge de nombreux autres scénarios de code dynamique, comme la sérialisation et la désérialisation, qui permettent de rendre persistantes les valeurs de champ d'un objet et de les restaurer ultérieurement. Ces scénarios nécessitent tous le compilateur juste-à-temps (JIT) du .NET Framework pour générer du code natif basé sur les métadonnées disponibles.  
  
 Le runtime [!INCLUDE[net_native](../../../includes/net-native-md.md)] n'inclut pas de compilateur JIT. Tout le code natif nécessaire doit donc être généré à l'avance. Un ensemble d'heuristiques permet de déterminer le code à générer, mais ces heuristiques ne peuvent pas couvrir tous les scénarios de métaprogrammation possibles.  Vous devez donc fournir des indications pour ces scénarios de métaprogrammation à l’aide de [directives runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Si les métadonnées ou le code d’implémentation nécessaires ne sont pas disponibles lors de l’exécution, votre application lève une exception [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) ou [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md). Deux utilitaires de résolution des problèmes sont disponibles, qui vont génèrer l'entrée appropriée pour votre fichier de directives de runtime qui élimine l'exception :  
  
-   l’ [utilitaire de résolution des problèmes MissingMetadataException](http://dotnet.github.io/native/troubleshooter/type.html) pour les types ;  
  
-   l’ [utilitaire de résolution des problèmes MissingMetadataException](http://dotnet.github.io/native/troubleshooter/method.html) pour les méthodes.  
  
> [!NOTE]
>  Pour une vue d'ensemble du processus de compilation .NET Native apportant des informations générales sur la nécessité d'un fichier de directives de runtime, voir [.NET Native et compilation](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 En outre, [!INCLUDE[net_native](../../../includes/net-native-md.md)] ne vous permet pas de réfléchir les membres privés de la bibliothèque de classes du .NET Framework. Par exemple, un appel de la propriété <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> pour récupérer les champs d'un type de bibliothèque de classes du .NET Framework retourne uniquement des champs publics ou protégés.  
  
 Les rubriques suivantes fournissent la documentation conceptuelle et de référence qui vous permet de prendre en charge la réflexion et la sérialisation dans vos applications :  
  
-   [API qui s’appuient sur la réflexion](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [Guide de référence de l'API de réflexion](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation d'applications avec .NET Native](../../../docs/framework/net-native/index.md)  
 [.NET Native et compilation](../../../docs/framework/net-native/net-native-and-compilation.md)
