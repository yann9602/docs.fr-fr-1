---
title: "Comment&#160;: charger des assemblys dans un domaine d&#39;application | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "domaines d'application, charger des assemblys"
  - "charger des assemblys"
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: charger des assemblys dans un domaine d&#39;application
Il existe plusieurs manières de charger un assembly dans un domaine d'application.  Il est recommandé d'utiliser la méthode `static` \(`Shared` dans Visual Basic\) <xref:System.Reflection.Assembly.Load%2A> de la classe [System.Reflection.Assembly](https://msdn.microsoft.com/en-us/library/system.reflection.aspx).  Voici d'autres manières de charger des assemblys :  
  
-   La méthode <xref:System.Reflection.Assembly.LoadFrom%2A> de la classe [Assembly](https://msdn.microsoft.com/en-us/library/system.reflection.aspx) charge un assembly selon son emplacement de fichier.  Le chargement d'assemblys avec cette méthode utilise un contexte de chargement différent.  
  
-   Les méthodes <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> et <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> chargent un assembly dans le contexte de réflexion uniquement.  Les assemblys chargés dans ce contexte peuvent être examinés mais ne peuvent pas être exécutés, ce qui permet l'examen des assemblys qui ciblent d'autres plateformes.  Consultez [Comment : charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
>  Le contexte de réflexion uniquement est une nouveauté de la version 2.0 du .NET Framework.  
  
-   Les méthodes telles que <xref:System.AppDomain.CreateInstance%2A> et <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> de la classe <xref:System.AppDomain> peuvent charger des assemblys dans un domaine d'application.  
  
-   La méthode <xref:System.Type.GetType%2A> de la classe <xref:System.Type> peut charger des assemblys.  
  
-   La méthode <xref:System.AppDomain.Load%2A> de la classe <xref:System.AppDomain?displayProperty=fullName> peut charger des assemblys, mais est principalement utilisée pour l'interopérabilité COM.  Elle ne doit pas être utilisée pour charger des assemblys dans un domaine d'application autre que le domaine d'application duquel elle est appelée.  
  
> [!NOTE]
>  Démarrant avec le .NET Framework version 2.0, le runtime ne chargera pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est plus élevé que le runtime actuellement chargé.  Cela s'applique à la combinaison des composants majeurs et mineurs du numéro de version.  
  
 Vous pouvez spécifier la façon dont le code compilé juste\-à\-temps des assemblys chargés est partagé entre les domaines d'application.  Pour plus d'informations, consultez [Application Domains and Assemblies](http://msdn.microsoft.com/fr-fr/433b04ae-4ba8-4849-9dbd-79194f240346).  
  
## Exemple  
 Le code suivant charge un assembly nommé "example.exe" ou "example.dll" dans le domaine d'application en cours, obtient un type nommé `Example` de l'assembly, obtient une méthode sans paramètre nommée `MethodA` pour ce type, et exécute la méthode.  Pour une description complète de l'obtention d'informations à partir d'un assembly chargé, consultez [Chargement et utilisation dynamiques des types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## Voir aussi  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>   
 [Hosting Overview](http://msdn.microsoft.com/fr-fr/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/fr-fr/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)   
 [Utilisation des domaines d'application](../../../docs/framework/app-domains/use.md)   
 [Comment : charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)   
 [Application Domains and Assemblies](http://msdn.microsoft.com/fr-fr/433b04ae-4ba8-4849-9dbd-79194f240346)