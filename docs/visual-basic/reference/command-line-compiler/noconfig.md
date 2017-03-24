---
title: /noconfig | Documents Microsoft
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
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 304d0e7fc787adb1d7776a2c047090ffc230fcc1
ms.lasthandoff: 03/13/2017

---
# <a name="noconfig"></a>/noconfig
Spécifie que le compilateur ne doit pas référencer automatiquement les communément utilisées [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblys ou importer les `System` et `Microsoft.VisualBasic` espaces de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a>Remarques  
 La `/noconfig` option indique au compilateur ne pas de compiler avec le fichier Vbc.rsp, qui se trouve dans le même répertoire que le fichier Vbc.exe. Le fichier Vbc.rsp référence couramment utilisées [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] les assemblys et les importations de la `System` et `Microsoft.VisualBasic` espaces de noms. Le compilateur référence implicitement l’assembly System.dll à moins que le `/nostdlib` option est spécifiée. La `/nostdlib` option indique au compilateur pas compiler avec Vbc.rsp ou de référencer automatiquement l’assembly System.dll.  
  
> [!NOTE]
>  Les assemblys Mscorlib.dll et de Microsoft.VisualBasic.dll sont toujours référencés.  
  
 Vous pouvez modifier le fichier Vbc.rsp pour spécifier des options de compilateur supplémentaires qui doivent être incluses dans chaque compilation Vbc.exe (sauf si vous spécifiez la `/noconfig` option). Pour plus d’informations, consultez [@ (Spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Le compilateur traite les options passées à la `vbc` commande dernier. Par conséquent, toute option de ligne de commande remplace le paramètre de la même option dans le fichier Vbc.rsp.  
  
> [!NOTE]
>  La `/noconfig` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)   
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [@ (Spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)   
 [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
