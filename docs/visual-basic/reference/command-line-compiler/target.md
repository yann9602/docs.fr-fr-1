---
title: /target (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ccdb87188b924303057d5867dccece937defe74d
ms.lasthandoff: 03/13/2017

---
# <a name="target-visual-basic"></a>/target (Visual Basic)
Spécifie le format de sortie du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Remarques  
 Le tableau suivant résume l’effet de la `/target` option.  
  
|**Option**|**Comportement**|  
|----------------|------------------|  
|`/target:exe`|Indique au compilateur de créer une application console exécutable.<br /><br /> C’est l’option par défaut lorsque aucune `/target` option est spécifiée. Le fichier exécutable est créé avec une extension .exe.<br /><br /> Sauf indication contraire la `/out` option, le nom de fichier de sortie prend le nom du fichier d’entrée qui contient le `Sub Main` procédure.<br /><br /> Seul `Sub Main` procédure est requise dans les fichiers de code source qui sont compilés dans un fichier .exe. Utilisez le `/main` option du compilateur pour spécifier la classe contenant le `Sub Main` procédure.|  
|`/target:library`|Indique au compilateur de créer une bibliothèque de liens dynamiques (DLL).<br /><br /> Le fichier de bibliothèque de liens dynamiques est créé avec l’extension .dll.<br /><br /> Sauf indication contraire la `/out` option, le nom de fichier de sortie prend le nom du premier fichier d’entrée.<br /><br /> Lorsque vous générez une DLL, un `Sub Main` procédure n’est pas nécessaire.|  
|`/target:module`|Indique au compilateur de générer un module qui peut être ajouté à un assembly.<br /><br /> Le fichier de sortie est créé avec l’extension .netmodule.<br /><br /> Le common language runtime .NET ne peut pas charger un fichier qui n’a pas d’assembly. Toutefois, vous pouvez incorporer un fichier dans le manifeste d’un assembly à l’aide de `/reference`.<br /><br /> Lorsque le code d’un module référence des types internes dans un autre module, les deux modules doivent être incorporés dans un manifeste d’assembly à l’aide de `/reference`.<br /><br /> Le [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option importe des métadonnées à partir d’un module.|  
|`/target:winexe`|Indique au compilateur de créer une application Windows exécutable.<br /><br /> Le fichier exécutable est créé avec une extension .exe. Une application basée sur Windows est celle qui fournit une interface utilisateur à partir du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] bibliothèque de classes ou avec les API Win32.<br /><br /> Sauf indication contraire la `/out` option, le nom de fichier de sortie prend le nom du fichier d’entrée qui contient le `Sub Main` procédure.<br /><br /> Seul `Sub Main` procédure est requise dans les fichiers de code source qui sont compilés dans un fichier .exe. Dans le cas où votre code possède plusieurs classes avec une `Sub Main` procédure, utilisez la `/main` option du compilateur pour spécifier la classe contenant le `Sub Main` procédure|  
|`/target:appcontainerexe`|Indique au compilateur de créer une application Windows exécutable qui doit être exécutée dans un conteneur d’application. Ce paramètre est conçu pour être utilisé pour [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] les applications.<br /><br /> Le **appcontainerexe** paramètre définit un bit dans le champ des caractéristiques de la [exécutable Portable](http://go.microsoft.com/fwlink/p/?LinkId=236960) fichier. Ce bit indique que l’application doit être exécutée dans un conteneur d’application. Lorsque ce bit est défini, une erreur se produit si le `CreateProcess` méthode tente de lancer l’application en dehors d’un conteneur d’application. Outre ce paramètre, bits **/target : appcontainerexe** équivaut à **/target : winexe**.<br /><br /> Le fichier exécutable est créé avec une extension .exe.<br /><br /> Sauf indication contraire à l’aide de la `/out` option, le nom de fichier de sortie prend le nom du fichier d’entrée qui contient le `Sub Main` procédure.<br /><br /> Seul `Sub Main` procédure est requise dans les fichiers de code source qui sont compilés dans un fichier .exe. Si votre code contient plus d’une classe qui a un `Sub Main` procédure, utilisez la `/main` option du compilateur pour spécifier la classe contenant le `Sub Main` procédure|  
|`/target:winmdobj`|Indique au compilateur de créer un fichier intermédiaire que vous pouvez convertir en fichier binaire (.winmd) Windows Runtime. Le fichier .winmd peut être consommé par des programmes JavaScript et C++, en plus des programmes en langage managé.<br /><br /> Le fichier intermédiaire est créé avec l’extension .winmdobj.<br /><br /> Sauf indication contraire à l’aide de la `/out` option, le nom de fichier de sortie prend le nom du premier fichier d’entrée. Un `Sub Main` procédure n’est pas nécessaire.<br /><br /> Le fichier .winmdobj est conçu pour être utilisé comme entrée pour le <xref:Microsoft.Build.Tasks.WinMDExp>Exporter l’outil pour générer un fichier de métadonnées (WinMD) de Windows.</xref:Microsoft.Build.Tasks.WinMDExp> Le fichier WinMD possède une extension .winmd et contient à la fois le code à partir de la bibliothèque d’origine et les définitions de WinMD que JavaScript, C++ et l’utilisation de Windows Runtime.|  
  
 Sauf si vous spécifiez `/target:module`, `/target` entraîne une [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] manifeste d’assembly à ajouter à un fichier de sortie.  
  
 Chaque instance de Vbc.exe produit, au plus, un fichier de sortie. Si vous spécifiez une option du compilateur, telles que `/out` ou `/target` plusieurs fois, il le compilateur traite est mis en oeuvre. Informations sur tous les fichiers d’une compilation sont ajoutées au manifeste. Tous les fichiers de sortie sauf ceux créés avec `/target:module` contiennent les métadonnées d’assembly dans le manifeste. Utilisez [Ildasm.exe (désassembleur IL)](https://msdn.microsoft.com/library/f7dy01k1) pour afficher les métadonnées dans un fichier de sortie.  
  
 La forme abrégée de `/target` est `/t`.  
  
### <a name="to-set-target-in-the-visual-studio-ide"></a>Pour définir /target dans l’IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l’onglet **Application** .  
  
3.  Modifiez la valeur dans la **Type d’Application** boîte.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `in.vb`, en créant `in.dll`:  
  
```  
vbc /target:library in.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/ main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)   
 [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)   
 [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
