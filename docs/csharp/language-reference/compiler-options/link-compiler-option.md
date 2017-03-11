---
title: "/link (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/l compiler option [C#]"
  - "/link compiler option [C#]"
  - "-l compiler option [C#]"
  - "EmbedInteropTypes"
  - "l compiler option [C#]"
  - "embed interop types [COM Interop]"
  - "-link compiler option [C#]"
  - "link compiler option [C#]"
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# /link (C# Compiler Options)
Force le compilateur à donner des informations de type COM dans les assemblys spécifiés disponibles pour le projet en cours de compilation.  
  
## Syntaxe  
  
```  
/link:fileList  
// -or-  
/l:fileList  
```  
  
## Arguments  
 `fileList`  
 Obligatoire.  Liste délimitée par des virgules de noms de fichiers d'assembly.  Si le nom de fichier contient un espace, mettez le nom entre guillemets.  
  
## Notes  
 L'option `/link` vous permet de déployer une application qui a des informations de type incorporées.  L'application peut ensuite utiliser des types dans un assembly de runtime qui implémente les informations de type incorporées sans requérir une référence à l'assembly de runtime.  Si différentes versions de l'assembly de runtime sont publiées, l'application qui contient les informations de type incorporées peut fonctionner avec les différentes versions sans avoir à être recompilée.  Pour obtenir un exemple, consultez [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
 L'utilisation de l'option `/link` est particulièrement utile lorsque vous travaillez avec COM Interop.  Vous pouvez incorporer des types COM afin que votre application ne requière plus un assembly PIA \(Primary Interop Assembly\) sur l'ordinateur cible.  L'option `/link` instruit le compilateur d'incorporer les informations de type COM de l'assembly d'interopérabilité référencé dans le code compilé résultant.  Le type COM est identifié par la valeur CLSID \(GUID\).  Par conséquent, votre application peut s'exécuter sur un ordinateur cible qui a installé les mêmes types COM avec les mêmes valeurs CLSID.  Les applications qui automatisent Microsoft Office sont un bon exemple.  Étant donné que les applications comme Office gardent habituellement la même valeur CLSID dans différentes versions, votre application peut utiliser les types COM référencés tant que le .NET Framework 4 ou version ultérieure est installé sur l'ordinateur cible et que votre application utilise les méthodes, les propriétés ou les  événements inclus dans les types COM référencés.  
  
 L'option `/link` incorpore uniquement des interfaces, des structures et des délégués.  L'incorporation de classes COM n'est pas prise en charge.  
  
> [!NOTE]
>  Lorsque vous créez une instance d'un type COM incorporé dans votre code, vous devez créer l'instance à l'aide de l'interface appropriée.  La tentative de création d'une instance d'un type COM incorporé à l'aide de la coclasse provoque une erreur.  
  
 Pour définir l'option `/link` dans [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)], ajoutez une référence d'assembly et affectez à la propriété `Embed Interop Types` la valeur **true**.  La valeur par défaut de la propriété `Embed Interop Types` est **false**.  
  
 Si vous établissez une liaison à un assembly COM \(Assembly A\) qui lui\-même référence un autre assembly COM \(Assembly B\), vous devez aussi établir une liaison à l'Assembly B si l'un ou l'autre des éléments suivants est vrai :  
  
-   Un type utilisé à partir de l'assembly A hérite d'un type ou implémente une interface à partir de l'assembly B.  
  
-   Un champ, une propriété, un événement ou une méthode dont le type de retour ou de paramètre est issu de l'assembly B est appelé.  
  
 Comme l'option de compilateur [\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md), l'option de compilateur `/link` utilise le fichier réponse Csc.rsp, qui référence les assemblys [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] fréquemment utilisés.  Utilisez l'option de compilateur [\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) si vous ne souhaitez pas que le compilateur utilise le fichier Csc.rsp.  
  
 La forme abrégée de `/link` est `/l`.  
  
## Types génériques et imbriqués  
 Les sections suivantes décrivent les limitations de l'utilisation de types génériques dans les applications qui incorporent des types d'interopérabilité.  
  
### Interfaces génériques  
 Les interfaces génériques incorporées depuis un assembly d'interopérabilité ne peuvent pas être utilisées.  L'exemple suivant le démontre.  
  
 [!code-cs[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/program.cs#1)]  
  
### Types ayant des paramètres génériques  
 Les types qui ont un paramètre générique dont le type est incorporé depuis un assembly d'interopérabilité ne peuvent pas être utilisés si ce type est issu d'un assembly externe.  Cette restriction ne s'applique pas aux interfaces.  Par exemple, considérez l'interface <xref:Microsoft.Office.Interop.Excel.Range> définie dans l'assembly <xref:Microsoft.Office.Interop.Excel>.  Si une bibliothèque incorpore des types d'interopérabilité de l'assembly <xref:Microsoft.Office.Interop.Excel> et expose une méthode qui retourne un type générique possédant un paramètre dont le type est l'interface <xref:Microsoft.Office.Interop.Excel.Range>, cette méthode doit retourner une interface générique, comme indiqué dans l'exemple de code suivant.  
  
 [!code-cs[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/utility.cs#2)]  
[!code-cs[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/utility.cs#3)]  
[!code-cs[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/utility.cs#4)]  
  
 Dans l'exemple suivant, le code client peut appeler la méthode qui retourne l'interface générique <xref:System.Collections.IList> sans erreur.  
  
 [!code-cs[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/program.cs#5)]  
  
## Exemple  
 Le code suivant compile le fichier source `OfficeApp.cs` et référence des assemblys depuis `COMData1.dll` et `COMData2.dll` pour produire `OfficeApp.exe`.  
  
```c#  
csc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)   
 [\/noconfig \(Ignore csc.rsp\)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Vue d'ensemble de l'interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md)