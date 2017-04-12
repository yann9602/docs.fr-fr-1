---
title: /verbose | Documents Microsoft
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
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
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
ms.openlocfilehash: f6d8a8b914ccffff72128bbc907482816b95b8a0
ms.lasthandoff: 03/13/2017

---
# <a name="verbose"></a>/verbose
Indique au compilateur de générer des messages d’état et d’erreur détaillés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Facultatif. Spécification de `/verbose` est identique à `/verbose+`, ce qui entraîne le compilateur à émettre des messages documentés. La valeur par défaut pour cette option est `/verbose-`.  
  
## <a name="remarks"></a>Remarques  
 La `/verbose` option affiche des informations sur le nombre total d’erreurs émises par le compilateur, signale les assemblys chargés par un module et affiche les fichiers qui sont en cours de compilation.  
  
> [!NOTE]
>  La `/verbose` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et demande au compilateur d’afficher des informations d’état détaillées.  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
