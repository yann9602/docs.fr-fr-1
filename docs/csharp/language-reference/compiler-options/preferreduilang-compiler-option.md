---
title: "-preferreduilang (Options du compilateur C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /preferreduilang
dev_langs:
- CSharp
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 0fd8ccca016b598b14780ac6cd2190442777fb53
ms.contentlocale: fr-fr
ms.lasthandoff: 03/24/2017

---
# <a name="preferreduilang-c-compiler-options"></a>/preferreduilang (Options du compilateur C#)
L’option de compilateur `/preferreduilang` vous permet de spécifier la langue dans laquelle le compilateur C# affiche la sortie, comme les messages d’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a>Arguments  
 `language`  
 Le [nom de la langue](http://go.microsoft.com/fwlink/p/?LinkId=236992) à utiliser pour la sortie du compilateur.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser l’option de compilateur `/preferreduilang` pour spécifier la langue que le compilateur C# doit utiliser pour les messages d’erreur et d’autres types de sortie de ligne de commande. Si le module linguistique de la langue n’est pas installé, le paramètre de langue du système d’exploitation est utilisé et aucune erreur n’est signalée.  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)
