---
title: "Durée de vie dans Visual Basic | Documents Microsoft"
ms.custom: 
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
- static variables, lifetime
- static variables, Visual Basic
- declared elements, lifetime
- Shared variable lifetime
- lifetime, declared elements
- lifetime, Visual Basic
- lifetime
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: 14
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
ms.openlocfilehash: fa0cbdf4a8fe5e8fc41e4e4f373c79451fb7b75f
ms.lasthandoff: 03/13/2017

---
# <a name="lifetime-in-visual-basic"></a>Durée de vie dans Visual Basic
Le *durée de vie* d’un élément déclaré est la période pendant laquelle il est disponible pour utilisation. Les variables sont les seuls éléments ayant une durée de vie. À cet effet, le compilateur traite les paramètres de procédure et retours de fonction comme des cas spéciaux de variables. La durée de vie d’une variable représente la période pendant laquelle elle peut contenir une valeur. Sa valeur peut changer pendant sa durée de vie, mais elle conserve toujours une valeur.  
  
## <a name="different-lifetimes"></a>Durées de vie différentes  
 A *variable membre* (déclaré au niveau du module, en dehors de toute procédure) a en général la même durée de vie que l’élément dans lequel elle est déclarée. Une variable non partagée déclarée dans une classe ou une structure existe en tant que copie distincte pour chaque instance de la classe ou la structure dans laquelle elle est déclarée. Chacune des variables a la même durée de vie que son instance. Toutefois, une `Shared` variable possède uniquement une seule durée de vie, qui dure toute la durée d’exécution de votre application.  
  
 A *variable locale* (déclaré à l’intérieur d’une procédure) existe uniquement pendant l’exécution de la procédure dans laquelle elle est déclarée. Cela s’applique également aux paramètres de cette procédure et de tout retour de fonction. Toutefois, si la procédure appelle d’autres procédures, les variables locales conservent leurs valeurs pendant l’exécutant des procédures appelées.  
  
## <a name="beginning-of-lifetime"></a>Début de la durée de vie  
 Durée de vie d’une variable locale commence lorsque le contrôle pénètre dans la procédure dans laquelle elle est déclarée. Chaque variable locale est initialisée à la valeur par défaut pour son type de données dès que la procédure commence en cours d’exécution. Lorsque la procédure rencontre une `Dim` instruction qui spécifie les valeurs initiales, elle définit ces variables à ces valeurs, même si votre code a déjà affecté des autres valeurs y.  
  
 Chaque membre d’une variable de structure est initialisé comme s’il s’agissait d’une variable distincte. De même, chaque élément d’une variable tableau est initialisé individuellement.  
  
 Les variables déclarées dans un bloc à l’intérieur d’une procédure (comme un `For` boucle) sont initialisées sur entrée dans la procédure. Ces initialisations prennent effet que votre code n’exécute le bloc ou non.  
  
## <a name="end-of-lifetime"></a>Fin de la durée de vie  
 Lorsqu’une procédure se termine, les valeurs de ses variables locales ne sont pas conservées, et [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] libère leur mémoire. La prochaine fois que vous appelez la procédure, toutes ses variables locales sont recréés et réinitialisés.  
  
 Lorsqu’une instance d’une classe ou une structure prend fin, ses variables non partagées perdent leur mémoire et leurs valeurs. Chaque nouvelle instance de la classe ou structure crée et réinitialise ses variables non partagées. Toutefois, `Shared` variables sont conservées jusqu'à ce que votre application s’arrête en cours d’exécution.  
  
## <a name="extension-of-lifetime"></a>Extension de la durée de vie  
 Si vous déclarez une variable locale avec le `Static` (mot clé), sa durée de vie est plus longue que la durée d’exécution de sa procédure. Le tableau suivant montre comment la déclaration de procédure détermine la durée pendant laquelle une `Static` variable existe.  
  
|Emplacement de procédure et partage|Durée de vie de variable statique commence|Fin de la durée de vie de variable statique|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|Dans un module (partagé par défaut)|La première fois que la procédure est appelée.|Lorsque votre application s’arrête en cours d’exécution|  
|Dans une classe, `Shared` (la procédure n’est pas un membre d’instance)|La première fois que la procédure est appelée sur une instance spécifique ou sur le nom de classe ou la structure elle-même|Lorsque votre application s’arrête en cours d’exécution|  
|Dans une instance d’une classe, pas `Shared` (la procédure est un membre d’instance)|La première fois que la procédure est appelée sur une instance spécifique|Lorsque l’instance est libérée pour le garbage collection (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Variables statiques du même nom  
 Vous pouvez déclarer des variables statiques avec le même nom dans plusieurs procédures. Dans ce cas, le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur considère chacune des variables comme un élément distinct. L’initialisation d’une de ces variables n’affecte pas les valeurs des autres. Ces conditions s’appliquent si vous définissez une procédure avec un ensemble de surcharges et que vous déclarez une variable statique avec le même nom dans chaque surcharge.  
  
## <a name="containing-elements-for-static-variables"></a>Contenant les éléments pour les Variables statiques  
 Vous pouvez déclarer une variable locale statique dans une classe, c'est-à-dire à l’intérieur d’une procédure dans cette classe. Toutefois, vous ne pouvez pas déclarer une variable locale statique dans une structure, en tant qu’un membre de structure ou une variable locale d’une procédure dans cette structure.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant déclare une variable avec le [statique](../../../../visual-basic/language-reference/modifiers/static.md) (mot clé). (Notez que vous n’avez pas besoin du `Dim` (mot clé) lors de la [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md) utilise un modificateur tel que `Static`.)  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrKeywords&#13;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a>Commentaires  
 Dans l’exemple précédent, la variable `applesSold` continue d’exister après la procédure `runningTotal` retourne au code appelant. La prochaine fois `runningTotal` est appelée, `applesSold` conserve sa valeur précédemment calculée.  
  
 Si `applesSold` avait été déclaré sans utiliser `Static`, les valeurs précédemment accumulées n’auraient pas être conservées entre les appels à `runningTotal`. La prochaine fois `runningTotal` a été appelé, `applesSold` aurait été recréé et initialisé à 0, et `runningTotal` aurait simplement retourné la même valeur avec laquelle elle a été appelée.  
  
### <a name="compiling-the-code"></a>Compilation du code  
 Vous pouvez initialiser la valeur d’une variable locale statique dans le cadre de sa déclaration. Si vous déclarez un tableau `Static`, vous pouvez initialiser son rang (nombre de dimensions), la longueur de chaque dimension et les valeurs des éléments individuels.  
  
### <a name="security"></a>Sécurité  
 Dans l’exemple précédent, vous pouvez obtenir la même durée de vie en déclarant `applesSold` au niveau du module. Si vous avez modifié la portée d’une variable de cette façon, cependant, la procédure n’aient plus accès exclusif à celle-ci. Étant donné que les autres procédures peuvent accéder `applesSold` et changer sa valeur, le total évolutif n’est plus fiable et le code est plus difficile à gérer.  
  
## <a name="see-also"></a>Voir aussi  
 [Partagé](../../../../visual-basic/language-reference/modifiers/shared.md)   
 [Rien](../../../../visual-basic/language-reference/nothing.md)   
 [Noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Dépannage des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)
