---
title: '#<a name="externalsource-directive"></a>ExternalSource (Directive)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="externalsource-directive"></a>#ExternalSource, directive
Indique un mappage entre des lignes spécifiques de code source et du texte externe à la source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Composants  
 `StringLiteral`  
 Le chemin d’accès à la source externe.  
  
 `IntLiteral`  
 Le numéro de ligne de la première ligne de la source externe.  
  
 `LogicalLine`  
 La ligne où l’erreur se produit dans la source externe.  
  
 `#End ExternalSource`  
 Met fin au bloc `#ExternalSource`.  
  
## <a name="remarks"></a>Remarques  
 Cette directive est utilisée uniquement par le compilateur et le débogueur.  
  
 Un fichier source peut inclure des directives de source externe, qui indiquent un mappage entre des lignes spécifiques de code dans le fichier source et du texte externe à la source, tel qu’un fichier .aspx. Si des erreurs sont rencontrées dans le code source désigné lors de la compilation, ils sont identifiés comme provenant de la source externe.  
  
 Directives de source externe n’ont aucun effet sur la compilation et ne peut pas être imbriquées. Ils sont destinés à un usage interne par l’application uniquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
