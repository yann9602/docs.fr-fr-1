---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e157fb0e1fcdb3899440eed02a42b16f75541989
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="optimize"></a>/optimize
Active ou désactive les optimisations du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`+` &#124; `-`|Facultatif. Le `/optimize-` option désactive les optimisations du compilateur. Le `/optimize+` option active les optimisations. Par défaut, les optimisations sont désactivées.|  
  
## <a name="remarks"></a>Notes  
 Les optimisations du compilateur diminuent la taille du fichier de sortie, le rendent plus rapide et plus efficace. Toutefois, étant donné que les optimisations entraînent une réorganisation du code dans le fichier de sortie `/optimize+` peut compliquer le débogage.  
  
 Tous les modules générés avec `/target:module` pour un assembly doit utiliser le même `/optimize` paramètres que l’assembly. Pour plus d’informations, consultez [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Vous pouvez combiner la `/optimize` et `/debug` options.  
  
|Pour définir /optimize dans l’environnement de développement intégré Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**.<br />     <br />2.  Cliquez sur l’onglet **Compiler**.<br />3.  Cliquez sur le bouton **Avancées** .<br />4.  Modifier la **activer les optimisations** case à cocher.|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et Active les optimisations du compilateur.  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
