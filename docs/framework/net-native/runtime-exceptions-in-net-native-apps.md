---
title: "Exceptions du runtime dans les applications natives .NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Exceptions du runtime dans les applications natives .NET
Il est important de tester les versions release de votre application de plateforme Windows universelle sur leurs plateformes cibles, car les configurations debug et release sont totalement différentes. Par défaut, la configuration debug utilise le runtime .NET Core pour compiler votre application, mais la configuration release utilise .NET Native pour compiler votre application en code natif.  
  
> [!IMPORTANT]
>  Pour plus d’informations sur le traitement des exceptions [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) et [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) que vous pouvez rencontrer quand vous testez les versions release de votre application, consultez « Étape 4 : résoudre manuellement les métadonnées manquantes » dans la rubrique [Prise en main](../../../docs/framework/net-native/getting-started-with-net-native.md), ainsi que [Réflexion et .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) et [Guide de référence du fichier de configuration des directives runtime \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## Versions debug et release  
 Quand la version debug s’exécute sur le runtime .NET Core, elle n’a pas été compilée en code natif. Ainsi, tous les services normalement fournis par le runtime sont accessibles à votre application.  
  
 D’autre part, la version release est compilée en code natif pour ses plateformes cibles, elle supprime la plupart des dépendances vis\-à\-vis des runtimes et bibliothèques externes et elle optimise largement le code à des fins de performances maximales.  
  
 Quand vous déboguez des versions release qui sont compilées à l’aide de .NET Native :  
  
-   Vous utilisez le moteur de débogage .NET Native, qui est différent des outils de débogage .NET normaux.  
  
-   La taille de votre fichier exécutable est réduite autant que possible. L’une des façons employées par .NET Native pour réduire la taille d’un fichier exécutable est en filtrant considérablement les messages d’exception d’exécution, un sujet abordé de façon plus détaillée dans la section [Messages d’exception du runtime](#Messages).  
  
-   Votre code est largement optimisé. Cela signifie que cette incorporation est utilisée dès que possible. \(L’incorporation déplace le code depuis les routines externes vers la routine d’appel.\)   Le fait que .NET Native fournisse un runtime spécialisé et implémente une incorporation agressive affecte la pile des appels qui s’affiche lors du débogage.  Pour plus d’informations, consultez la section [Pile des appels du runtime](#CallStack).  
  
> [!NOTE]
>  Vous pouvez déterminer si les versions debug et release sont compilées avec la chaîne d’outils .NET Native en cochant ou non la case **Compiler avec la chaîne de l’outil du code natif .NET**. Notez quand même que le Windows Store compile toujours la version de production de votre application avec la chaîne d’outils .NET Native.  
  
<a name="Messages"></a>   
## Messages d’exception du runtime  
 Pour réduire la taille de l’exécutable de l’application, .NET Native n’inclut pas le texte complet des messages d’exception. Ainsi, les exceptions du runtime levées dans les versions release risquent de ne pas afficher le texte complet des messages d’exception. Le texte peut plutôt consister en une sous\-chaîne assortie d’un lien à suivre pour plus d’informations. Par exemple, les informations sur l’exception peuvent apparaître comme suit :  
  
```  
  
Exception thrown: '$16_System.AggregateException' in Unknown Module. Additional information: AggregateException_ctor_DefaultMessage If there is a handler for this exception, the program may be safely continued.  
  
```  
  
 Si vous avez besoin de consulter la totalité du message d’exception, exécutez plutôt la version debug. Par exemple, les informations sur l’exception précédente issues de la version release peuvent apparaître comme suit dans la version debug :  
  
```  
  
Exception thrown: 'System.AggregateException' in NativeApp.exe. Additional information: Value does not fall within the expected range.  
  
```  
  
<a name="CallStack"></a>   
## Pile des appels du runtime  
 Du fait de l’incorporation et des autres optimisations, la pile des appels affichée par une application compilée par la chaîne d’outils .NET Native risque de ne pas vous aider à identifier clairement le chemin vers une exception runtime.  
  
 Pour obtenir la pile complète, exécutez plutôt la version debug.  
  
## Voir aussi  
 [Débogage des applications Windows universelles .NET Native](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)   
 [Prise en main](../../../docs/framework/net-native/getting-started-with-net-native.md)