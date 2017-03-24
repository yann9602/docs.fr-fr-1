---
title: /nologo (Visual Basic) | Documents Microsoft
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
- -nologo compiler option [Visual Basic]
- banners, suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
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
ms.openlocfilehash: a0e309a80082f19fb47ccbbb43c00f22c8addd3b
ms.lasthandoff: 03/13/2017

---
# <a name="nologo-visual-basic"></a>/nologo (Visual Basic)
Supprime l’affichage de la bannière de copyright et les messages d’information pendant la compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/nologo  
```  
  
## <a name="remarks"></a>Remarques  
 Si vous spécifiez `/nologo`, le compilateur n’affiche pas une bannière de copyright. Par défaut, l'option `/nologo` n'est pas activée.  
  
> [!NOTE]
>  La `/nologo` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et n’affiche pas une bannière de copyright.  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
