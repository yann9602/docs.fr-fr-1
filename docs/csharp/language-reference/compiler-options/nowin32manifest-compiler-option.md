---
title: -nowin32manifest (options du compilateur C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowin32manifest
dev_langs:
- CSharp
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: 15
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
ms.openlocfilehash: ce96938ee00df7bfae742369673f75f8d39abd12
ms.lasthandoff: 03/13/2017

---
# <a name="nowin32manifest-c-compiler-options"></a>/nowin32manifest (options du compilateur C#)
Utilisez l’option **/nowin32manifest** pour indiquer au compilateur de ne pas incorporer le manifeste de l’application dans le fichier exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/nowin32manifest  
```  
  
## <a name="remarks"></a>Remarques  
 Quand cette option est utilisée, l’application est soumise à la virtualisation sur Windows Vista, sauf si vous fournissez un manifeste de l’application dans un fichier de ressources Win32 ou au cours d’une étape de génération ultérieure.  
  
 Dans Visual Studio, définissez cette option dans la page de propriétés **Application** en sélectionnant l’option **Créer une application sans fichier manifeste** dans la zone de liste déroulante **Manifeste**. Pour plus d’informations, consultez [Application, page du Concepteur de projet (C#)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Pour plus d’informations sur la création d’un manifeste, consultez [/win32manifest (options du compilateur C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB Guide pratique pour modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
