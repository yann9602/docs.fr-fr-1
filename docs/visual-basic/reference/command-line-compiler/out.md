---
title: /out (Visual Basic) | Documents Microsoft
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
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: 17
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
ms.openlocfilehash: e3eb7af88869e4fb161a12914c02f2bc2f41864e
ms.lasthandoff: 03/13/2017

---
# <a name="out-visual-basic"></a>/out (Visual Basic)
Spécifie le nom du fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`filename`|Obligatoire. Le nom du fichier de sortie, que le compilateur crée. Si le nom de fichier contient un espace, placez le nom entre guillemets (« »).|  
  
## <a name="remarks"></a>Remarques  
 Spécifiez le nom complet et l’extension du fichier à créer. Si vous ne le faites pas, le fichier .exe tire son nom du fichier de code source contenant le `Sub Main` procédure et le fichier .dll tire son nom du premier fichier de code source.  
  
 Si vous spécifiez un nom de fichier sans l’extension .exe ou .dll, le compilateur ajoute automatiquement l’extension pour vous, selon la valeur spécifiée pour la `/target` option du compilateur.  
  
|Pour définir /out dans l’environnement de développement intégré Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Application** .<br />3.  Modifiez la valeur dans la **nom de l’Assembly** boîte.|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et crée le fichier de sortie `T2.exe`.  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
