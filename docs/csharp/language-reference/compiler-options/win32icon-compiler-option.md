---
title: "-win32icon (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32icon
dev_langs:
- CSharp
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: 18
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
ms.openlocfilehash: af5b9c3a44163167d932d378cbac4976e07eacbf
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="win32icon-c-compiler-options"></a>/win32icon (Options du compilateur C#)
L’option **/win32icon** insère un fichier .ico dans le fichier de sortie, ce qui lui donne l’apparence souhaitée dans l’Explorateur de fichiers.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Fichier .ico que vous voulez ajouter à votre fichier de sortie.  
  
## <a name="remarks"></a>Remarques  
 Un fichier .ico peut être créé avec le [compilateur de ressources](http://go.microsoft.com/fwlink/?LinkId=148370). Le compilateur de ressources est appelé quand vous compilez un programme Visual C++ ; un fichier .ico est alors créé à partir du fichier .rc.  
  
 Consultez [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) pour référencer ou [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) pour attacher un fichier de ressources .NET Framework. Consultez [/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) pour importer un fichier .res.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez les pages **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Modifiez la propriété **Icône d’application**.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## <a name="example"></a>Exemple  
 Compilez `in.cs` et attachez un fichier .ico `rf.ico` afin de générer le fichier `in.exe` :  
  
```console  
csc /win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

