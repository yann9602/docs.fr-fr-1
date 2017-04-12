---
title: /quiet | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
dev_langs:
- VB
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: 11
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
ms.openlocfilehash: feafed7464248c38ec70087795a28ead8b8793f3
ms.lasthandoff: 03/13/2017

---
# <a name="quiet"></a>/quiet
Empêche le compilateur d'afficher le code pour les erreurs et les avertissements liés à la syntaxe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/quiet  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, l'option `/quiet` n'est pas activée. Lorsque le compilateur signale une erreur de syntaxe ou un avertissement, il renvoie également la ligne de code source. Pour les applications qui analysent les résultats de la compilation, il peut être plus pratique pour la sortie du compilateur est uniquement le texte de diagnostic.  
  
 Dans l’exemple suivant, `Module1` génère une erreur qui inclut le code source compilé sans `/quiet`.  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 Sortie :  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 Compilé avec `/quiet`, le compilateur extrait uniquement ce qui suit :  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  La `/quiet` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et n’affiche pas de code pour les diagnostics du compilateur liés à la syntaxe :  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
