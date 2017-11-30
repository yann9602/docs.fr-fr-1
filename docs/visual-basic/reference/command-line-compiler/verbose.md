---
title: /verbose
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5480f828fa1f0b6d71fa649bf44513ce806bb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="verbose"></a>/verbose
Indique au compilateur générer des messages d’état et d’erreur détaillés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Facultatif. Spécification de `/verbose` est identique à la spécification `/verbose+`, ce qui entraîne le compilateur à émettre des messages détaillés. La valeur par défaut de cette option est `/verbose-`.  
  
## <a name="remarks"></a>Remarques  
 Le `/verbose` option affiche des informations sur le nombre total d’erreurs émises par le compilateur, signale les assemblys chargés par un module et affiche les fichiers qui sont en cours de compilation.  
  
> [!NOTE]
>  Le `/verbose` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et indique au compilateur d’afficher des informations d’état détaillées.  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
