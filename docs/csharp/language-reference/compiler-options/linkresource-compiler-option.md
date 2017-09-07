---
title: -linkresource (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /linkresource
dev_langs:
- CSharp
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 022d6c1a53eab98fc033c902f903e7bc66e6da3f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="linkresource-c-compiler-options"></a>/linkresource (Options du compilateur C#)
Crée un lien vers une ressource .NET Framework dans le fichier de sortie. Le fichier de ressources n’est pas ajouté au fichier de sortie. Cette option diffère de l’option [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) qui incorpore un fichier de ressources dans le fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Fichier de ressources .NET Framework que vous voulez lier à l’assembly.  
  
 `identifier`(facultatif)  
 Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource. La valeur par défaut est le nom du fichier.  
  
 `accessibility-modifier`(facultatif)  
 Accessibilité de la ressource : publique ou privée. La valeur par défaut est « public ».  
  
## <a name="remarks"></a>Remarques  
 Par défaut, les ressources liées sont publiques dans l’assembly quand elles sont créées avec le compilateur C#. Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`. Aucun autre modificateur que `public` ou `private` n’est autorisé.  
  
 **/linkresource** nécessite une option [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) autre que **/target:module**.  
  
 Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou dans l'environnement de développement, il est accessible à l'aide des membres de l'espace de noms <xref:System.Resources>. Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=fullName>. Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource`* dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l'exécution.  
  
 Le fichier spécifié dans `filename` peut avoir n’importe quel format. C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly. Le deuxième des exemples suivants montre comment effectuer cette opération. Vous pouvez effectuer la même opération dans Assembly Linker. Le troisième des exemples suivants montre comment effectuer cette opération. Pour plus d’informations, consultez [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) et [Utilisation d’assemblys et du Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **/linkres** est la forme abrégée de **/linkresource**.  
  
 Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.  
  
## <a name="example"></a>Exemple  
 Compiler `in.cs` et créer un lien vers le fichier de ressources `rf.resource` :  
  
```console  
csc /linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Exemple  
 Compiler `A.cs` dans une DLL, créer un lien vers une DLL native N.dll et placer la sortie dans le Global Assembly Cache (GAC). Dans cet exemple, A.dll et N.dll résident dans le GAC.  
  
```console  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple obtient le même résultat, mais en utilisant des options Assembly Linker.  
  
```console  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex)   
 [Utilisation d’assemblys et du Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

