---
title: -main (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /main
dev_langs:
- CSharp
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: 14
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
ms.openlocfilehash: eee7ef4698f4b6bf7c90ff8e22a1a3ae106bec35
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="main-c-compiler-options"></a>/main (Options du compilateur C#)
Cette option spécifie la classe qui contient le point d’entrée du programme dans le cas où plusieurs classes contiennent une méthode **Main**.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/main:class  
```  
  
## <a name="arguments"></a>Arguments  
 `class`  
 Type contenant la méthode **Main**.  
  
## <a name="remarks"></a>Notes  
 Si votre compilation comprend plusieurs types avec une méthode [Main](../../../csharp/programming-guide/main-and-command-args/index.md), vous pouvez spécifier le type qui contient la méthode **Main** à utiliser comme point d’entrée dans le programme.  
  
 Cette option est à utiliser lors de la compilation d’un fichier .exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Modifiez la propriété **Objet de démarrage**.  
  
     Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Exemple  
 Compilez `t2.cs` et `t3.cs`, en spécifiant que la **Main** se trouve dans `Test2` :  
  
```console  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

