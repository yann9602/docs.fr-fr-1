---
title: "-target (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4666f0305fc2de35c1fa594ccef3dd3a64c0f67c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="target-c-compiler-options"></a>/target (Options du compilateur C#)
L’option du compilateur **/target** peut être spécifiée sous quatre formes différentes :  
  
 [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Pour créer un fichier .exe pour des applications [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].  
  
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
  
 Sauf si vous spécifiez **/target:module**, **/target** entraîne le placement d’un manifeste de l’assembly .NET Framework dans un fichier de sortie. Pour plus d’informations, consultez [Assemblys dans le Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) et [Attributs communs](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 Le manifeste de l’assembly est placé dans le premier fichier de sortie .exe dans la compilation ou dans le premier fichier DLL, en l’absence de fichier de sortie .exe. Par exemple, dans la ligne de commande suivante, le manifeste est placé dans `1.exe` :  
  
```console  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 Le compilateur crée un seul manifeste d’assembly par compilation. Les informations sur tous les fichiers d’une compilation sont placées dans le manifeste de l’assembly. Tous les fichiers de sortie sauf ceux créés avec **/target:module** peuvent contenir un manifeste d’assembly. Lorsque vous générez plusieurs fichiers de sortie sur la ligne de commande, un seul manifeste d’assembly peut être créé et il doit aller dans le premier fichier de sortie spécifié sur la ligne de commande. Quel que soit le premier fichier de sortie (**/target:exe**, **/target:winexe**, **/target:library** ou **/target:module**), tous les autres fichiers de sortie générés dans la même compilation doivent être des modules (**/target:module**).  
  
 Si vous créez un assembly, vous pouvez indiquer que tout ou partie de votre code est conforme CLS avec l’attribut <xref:System.CLSCompliantAttribute>.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Pour plus d’informations sur la définition de cette option de compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)  
 [/subsystemversion (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
