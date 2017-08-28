---
title: "-recurse (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /recurse
dev_langs:
- CSharp
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: 12
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
ms.openlocfilehash: 99664f8b32f5f9e5bf491c5bfde2c1649de42dd9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="recurse-c-compiler-options"></a>/recurse (Options du compilateur C#)
L’option /recurse permet de compiler des fichiers de code source dans tous les répertoires enfants du répertoire spécifié (dir) ou du répertoire du projet.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir` (facultatif)  
 Répertoire dans lequel vous voulez commencer la recherche. Si ce répertoire n’est pas spécifié, la recherche commence dans le répertoire du projet.  
  
 `file`  
 Le ou les fichiers à rechercher. Les caractères génériques sont autorisés.  
  
## <a name="remarks"></a>Remarques  
 L’option **/recurse** permet de compiler des fichiers de code source dans tous les répertoires enfants du répertoire spécifié (`dir`) ou du répertoire du projet.  
  
 Vous pouvez utiliser des caractères génériques dans un nom de fichier pour compiler tous les fichiers correspondants dans le répertoire du projet sans utiliser **/recurse**.  
  
 Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.  
  
## <a name="example"></a>Exemple  
 Compile tous les fichiers C# qui se trouvent dans le répertoire actif :  
  
```console  
csc *.cs  
```  
  
 Compile tous les fichiers C# du répertoire dir1\dir2 et de tous les sous-répertoires qui se situent en dessous de celui-ci, puis génère dir2.dll :  
  
```console  
csc /target:library /out:dir2.dll /recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

