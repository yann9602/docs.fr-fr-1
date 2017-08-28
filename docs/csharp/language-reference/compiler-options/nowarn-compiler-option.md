---
title: -nowarn (options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowarn
dev_langs:
- CSharp
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 24
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
ms.openlocfilehash: 3bae7e6d16c044b8f1aeba26de434cdf17479e82
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="nowarn-c-compiler-options"></a>/nowarn (options du compilateur C#)
L’option **/nowarn** vous permet de désactiver l’affichage d’un ou de plusieurs avertissements par le compilateur. Séparez les numéros des avertissements par une virgule.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Arguments  
 `number1`, `number2`  
 Numéro de chaque avertissement que le compilateur ne doit pas afficher.  
  
## <a name="remarks"></a>Remarques  
 Vous devez spécifier uniquement la partie numérique de l’identificateur d’avertissement. Par exemple, si vous souhaitez supprimer l’avertissement CS0028, spécifiez `/nowarn:28`.  
  
 Le compilateur ignore automatiquement les numéros des avertissements passés à `/nowarn` qui étaient valides dans les versions précédentes, mais qui ont été supprimés dans le compilateur. Par exemple, l’avertissement CS0679 était valide dans le compilateur dans Visual Studio .NET 2002, mais il a été supprimé depuis cette version.  
  
 Les avertissements suivants ne peuvent pas être supprimés avec l’option `/nowarn` :  
  
-   Avertissement du compilateur (niveau 1) CS2002  
  
-   Avertissement du compilateur (niveau 1) CS2023  
  
-   Avertissement du compilateur (niveau 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet. Pour plus de détails, consultez [Générer, page du Concepteur de projet (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Modifiez la propriété **Supprimer les avertissements**.  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)   
 [Erreurs du compilateur C#](../../../csharp/language-reference/compiler-messages/index.md)

