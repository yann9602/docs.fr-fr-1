---
title: -target (Options du compilateur C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 615a0e2993dc78919008e8f9245504a486e2fb77
ms.lasthandoff: 03/13/2017

---
# <a name="target-c-compiler-options"></a>/target (Options du compilateur C#)
L’option du compilateur **/target** peut être spécifiée sous quatre formes différentes :  
  
 [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Pour créer un fichier .exe pour des applications [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
 [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 Pour créer un fichier .exe.  
  
 [/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 Pour créer une bibliothèque de code.  
  
 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Pour créer un module.  
  
 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Pour créer un programme Windows.  
  
 [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Pour créer un fichier .winmdobj intermédiaire.  
  
 Sauf si vous spécifiez **/target:module**, **/target** entraîne le placement d’un manifeste de l’assembly .NET Framework dans un fichier de sortie. Pour plus d’informations, consultez [Assemblys dans le Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) et [Attributs communs](http://msdn.microsoft.com/library/2f48a7ec-9683-4899-a1d2-a08be8fc558b).  
  
 Le manifeste de l’assembly est placé dans le premier fichier de sortie .exe dans la compilation ou dans le premier fichier DLL, en l’absence de fichier de sortie .exe. Par exemple, dans la ligne de commande suivante, le manifeste est placé dans `1.exe` :  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 Le compilateur crée un seul manifeste d’assembly par compilation. Les informations sur tous les fichiers d’une compilation sont placées dans le manifeste de l’assembly. Tous les fichiers de sortie sauf ceux créés avec **/target:module** peuvent contenir un manifeste d’assembly. Lorsque vous générez plusieurs fichiers de sortie sur la ligne de commande, un seul manifeste d’assembly peut être créé et il doit aller dans le premier fichier de sortie spécifié sur la ligne de commande. Quel que soit le premier fichier de sortie (**/target:exe**, **/target:winexe**, **/target:library** ou **/target:module**), tous les autres fichiers de sortie générés dans la même compilation doivent être des modules (**/target:module**).  
  
 Si vous créez un assembly, vous pouvez indiquer que tout ou partie de votre code est conforme à CLS avec l’attribut <xref:System.CLSCompliantAttribute>.  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Pour plus d’informations sur la définition par programmation de cette option du compilateur, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB Guide pratique pour modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [/subsystemversion (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
