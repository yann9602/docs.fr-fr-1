---
title: -main (Options du compilateur C#) | Microsoft Docs
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fa8c02a6521b65e2cc4f7c8d779c1091ce399fba
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

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
 [NIB Guide pratique pour modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
