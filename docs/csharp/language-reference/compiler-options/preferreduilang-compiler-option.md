---
title: "-preferreduilang (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ccf25e9a5d5d025f9024519b41c4afa17a5081f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
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
