---
title: "Conditional Compilation in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conditional compilation, about conditional compilation"
  - "compilation, conditional"
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conditional Compilation in Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

La *compilation conditionnelle* permet de compiler de façon sélective des blocs de code spécifiques tout en excluant d'autres blocs.  
  
 Vous pouvez, par exemple, souhaiter écrire des instructions de débogage qui comparent la rapidité de plusieurs approches d'une même tâche de programmation ou encore localiser une application dans plusieurs langues.  Les instructions de compilation conditionnelle sont conçues pour s'exécuter au moment de la compilation et non de l'exécution.  
  
 Vous désignez des blocs de code à compiler de façon conditionnelle avec la directive `#If...Then...#Else`.  Pour créer, par exemple, des versions en langue française et allemande de la même application à partir du même code source, incorporez des segments de code propres à la plateforme dans des instructions `#If...Then` à l'aide des constantes prédéfinies `FrenchVersion` et `GermanVersion`.  L'exemple suivant vous indique comment procéder :  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 Si vous attribuez à la constante de compilation conditionnelle `FrenchVersion` la valeur `True` au moment de la compilation, le code conditionnel de la version française est compilé.  Si vous attribuez la valeur `True` à la constante `GermanVersion`, le compilateur utilise la version allemande.  Si aucune des deux n'a la valeur `True`, c'est le code écrit dans le dernier bloc `Else` qui est exécuté.  
  
> [!NOTE]
>  La saisie semi\-automatique ne fonctionne pas lorsque vous modifiez du code et que vous utilisez des directives de compilation conditionnelles si le code ne fait pas partie du branchement actuel.  
  
## Déclaration des constantes de compilation conditionnelle  
 Vous avez le choix entre trois méthodes pour définir des constantes de compilation conditionnelle :  
  
-   Dans le **Concepteur de projets**  
  
-   dans la ligne de commande lorsque vous utilisez le compilateur de ligne de commande ;  
  
-   dans votre code.  
  
 Les constantes de compilation conditionnelle sont dotées d'une portée spéciale et ne sont pas accessibles à partir du code standard.  La portée d'une constante de compilation conditionnelle varie en fonction de la façon dont elle a été définie.  Le tableau suivant répertorie la portée des constantes déclarées à l'aide de chacune des trois méthodes décrites ci\-dessus.  
  
|||  
|-|-|  
|Méthode de définition de la constante|Portée de la constante|  
|**Concepteur de projets**|Publique pour tous les fichiers du projet.|  
|Ligne de commande|Publique pour tous les fichiers passés au compilateur de ligne de commande.|  
|Instruction `#Const` dans le code|Privée pour le fichier dans lequel elle est déclarée.|  
  
||  
|-|  
|Pour définir des constantes dans le Concepteur de projets|  
|-   Avant de créer votre fichier exécutable, définissez des constantes dans le **Concepteur de projets** en suivant les étapes décrites dans [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).|  
  
||  
|-|  
|Pour définir des constantes dans la ligne de commande|  
|-   Utilisez le commutateur **\/d** pour entrer des constantes de compilation conditionnelle, comme dans l'exemple suivant :<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Aucun espace n'est nécessaire entre le commutateur **\/d** et la première constante.  Pour plus d'informations, consultez [\/define](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Les déclarations de ligne de commande se substituent aux déclarations entrées dans le **Concepteur de projets**, mais elles ne les suppriment pas.  Les arguments définis dans le **Concepteur de projets** restent en application pour des compilations ultérieures.<br />     Lorsque vous écrivez des constantes dans le code lui\-même, il n'existe aucune règle fixe quant à leur placement dans la mesure où leur portée correspond à tout le module dans lequel elles sont déclarées.|  
  
||  
|-|  
|Pour déterminer des constantes dans votre code|  
|-   Placez les constantes dans le bloc de déclaration du module dans lequel elles sont utilisées.  Cela contribue à conserver un code organisé et plus facile à lire.|  
  
## Rubriques connexes  
  
|||  
|-|-|  
|Titre|Description|  
|[Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Fournit quelques suggestions pour simplifier la lecture et la gestion de votre code.|  
  
## Référence  
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)