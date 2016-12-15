---
title: "/linkresource (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/linkresource"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/linkresource compiler option [C#]"
  - "linkres compiler option [C#]"
  - "/linkres compiler option [C#]"
  - "-linkres compiler option [C#]"
  - "-linkresource compiler option [C#]"
  - "linkresource compiler option [C#]"
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /linkresource (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Crée un lien vers une ressource .NET Framework dans le fichier de sortie.  Le fichier de ressources n'est pas ajouté au fichier de sortie.  Cela diffère de l'option [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) qui incorpore un fichier de ressources dans un fichier de sortie.  
  
## Syntaxe  
  
```  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## Arguments  
 `filename`  
 Fichier de ressources .NET Framework avec lequel vous voulez établir un lien à partir de l'assembly.  
  
 `identifier` \(facultatif\)  
 Nom logique de la ressource, c'est\-à\-dire le nom utilisé pour charger cette dernière.  La valeur par défaut est le nom du fichier.  
  
 `accessibility-modifier` \(facultatif\)  
 Accessibilité de la ressource : public ou private.  La valeur par défaut est public.  
  
## Notes  
 Par défaut, les ressources liées sont public dans l'assembly lorsqu'elles sont créées avec le compilateur C\#.  Pour que les ressources soient private, spécifiez `private` comme modificateur d'accessibilité.  Aucun autre modificateur que `public` ou `private` n'est autorisé.  
  
 L'option **\/linkresource** nécessite une option [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) différente de **\/target:module**.  
  
 Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou dans l'environnement de développement, il est accessible avec des membres dans l'espace de noms <xref:System.Resources>.  Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=fullName>.  Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource`\* dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l'exécution.  
  
 Le fichier spécifié par `filename` peut avoir n'importe quel format.  Par exemple, vous pouvez décider d'intégrer une DLL native dans l'assembly. Ainsi, elle pourra être installée dans le Global Assembly Cache et sera accessible depuis le code managé de l'assembly.  La procédure ci\-après indique comment effectuer cette opération.  Vous pouvez faire la même chose dans Assembly Linker.  La procédure ci\-après indique comment effectuer cette opération.  Pour plus d'informations, consultez [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) et [Utilisation d'assemblys et du Global Assembly Cache](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md).  
  
 **\/linkres** est la forme abrégée de **\/linkresource**.  
  
 Cette option du compilateur n'est pas disponible dans Visual Studio et ne peut pas être modifiée par programme.  
  
## Exemple  
 Compilez `in.cs` et liez ce fichier au fichier de ressources `rf.resource` :  
  
```  
csc /linkresource:rf.resource in.cs  
```  
  
## Exemple  
 Compilez `A.cs` dans une DLL, liez à une DLL native N.dll et placez la sortie dans le GAC \(Global Assembly Cache\).  Dans cet exemple, A.dll et N.dll résideront dans le GAC.  
  
```  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## Exemple  
 Cet exemple effectue la même opération que le précédent, mais en utilisant les options Assembly Linker.  
  
```  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Utilisation d'assemblys et du Global Assembly Cache](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)