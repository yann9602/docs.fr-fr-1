---
title: -noconfig (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /noconfig
dev_langs:
- CSharp
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: 11
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
ms.openlocfilehash: 594e972dc834ab74412e30a48428f850ae02b5ac
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="noconfig-c-compiler-options"></a>/noconfig (Options du compilateur C#)
L’option **/noconfig** indique au compilateur de ne pas compiler avec le fichier csc.rsp, qui se trouve dans le même répertoire que le fichier csc.exe d’où il est chargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/noconfig  
```  
  
## <a name="remarks"></a>Remarques  
 Le fichier csc.rsp fait référence à tous les assemblys fournis avec le .NET Framework. Les références réelles qui sont incluses dans l’environnement de développement Visual Studio .NET varient en fonction du type de projet.  
  
 Vous pouvez modifier le fichier csc.rsp et spécifier les options de compilateur supplémentaires qui doivent être incluses dans chaque compilation avec csc.exe via la ligne de commande (à l’exception de l’option **/noconfig**).  
  
 Le compilateur traite les options passées à la commande **csc** en dernier. De ce fait, toute option sur la ligne de commande se substitue au paramètre de la même option dans le fichier csc.rsp.  
  
 Si vous ne voulez pas que le compilateur recherche et utilise les paramètres du fichier csc.rsp, spécifiez **/noconfig**.  
  
 Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

