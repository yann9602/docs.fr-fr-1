---
title: "-addmodule (Options du compilateur C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /addmodule
dev_langs:
- CSharp
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: 13
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 614dbefbb472ef2cd03fcb1ba7a44f08c450bf4a
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="addmodule-c-compiler-options"></a>/addmodule (Options du compilateur C#)
Cette option ajoute un module créé avec le commutateur target:module à la compilation actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Arguments  
 `file`, `file2`  
 Fichier de sortie qui contient des métadonnées. Le fichier ne peut pas contenir un manifeste d’assembly. Pour importer plusieurs fichiers, séparez les noms des fichiers par une virgule ou un point-virgule.  
  
## <a name="remarks"></a>Remarques  
 Tous les modules ajoutés par **/addmodule** doivent se trouver dans le même répertoire que le fichier de sortie au moment de l’exécution. Vous pouvez donc spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l’application au moment de l’exécution. Si le module n’est pas dans le répertoire de l’application au moment de l’exécution, vous obtiendrez <xref:System.TypeLoadException>.  
  
 `file` ne peut pas contenir un assembly. Si, par exemple, le fichier de sortie a été créé avec [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), ses métadonnées peuvent être importées avec **/addmodule**.  
  
 Si le fichier de sortie a été créé avec une option **/target** autre que **/target:module**, ses métadonnées ne peuvent pas être importées avec **/addmodule**, mais peuvent l’être avec [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Cette option du compilateur n’est pas disponible dans Visual Studio ; un projet ne peut pas référencer un module. Par ailleurs, cette option du compilateur ne peut pas être changée par programmation.  
  
## <a name="example"></a>Exemple  
 Compilez le fichier source `input.cs` et ajoutez les métadonnées de `metad1.netmodule` et `metad2.netmodule` pour produire `out.exe` :  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Assemblys multifichiers](../../../framework/app-domains/multifile-assemblies.md)   
 [Guide pratique pour générer un assembly multifichier](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
