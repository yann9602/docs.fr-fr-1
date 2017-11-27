---
title: Compilation conditionnelle en Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 559380dc9baceb2fba4dca782e83f335f1bcd92d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="conditional-compilation-in-visual-basic"></a>Compilation conditionnelle en Visual Basic
Dans *compilation conditionnelle*, blocs de code dans un programme spécifiques compiler de façon sélective tandis que d’autres sont ignorés.  
  
 Par exemple, vous souhaitez écrire des instructions de débogage qui comparent la rapidité de différentes approches pour la même tâche de programmation, ou vous peuvent souhaiter localiser une application dans plusieurs langues. Instructions de compilation conditionnelle sont conçues pour s’exécuter pendant la compilation, pas au moment de l’exécution.  
  
 Vous désignez des blocs de code à compiler de façon conditionnelle avec la `#If...Then...#Else` la directive. Par exemple, pour créer le Français et allemand versions de la même application à partir de la même du code source, incorporez des segments de code spécifique à la plateforme dans `#If...Then` instructions à l’aide de l’une des constantes prédéfinies `FrenchVersion` et `GermanVersion`. L’exemple suivant montre comment :  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 Si vous définissez la valeur de la `FrenchVersion` constante de compilation conditionnelle à `True` au moment de la compilation, le code conditionnel de la version Français est compilé. Si vous définissez la valeur de la `GermanVersion` constante `True`, le compilateur utilise la version allemande. Si aucune n’est définie `True`, le code de la dernière `Else` bloc s’exécute.  
  
> [!NOTE]
>  La saisie semi-automatique ne fonctionne pas lorsque vous modifiez du code et à l’aide de directives de compilation conditionnelles si le code ne fait pas partie de la branche active.  
  
## <a name="declaring-conditional-compilation-constants"></a>Déclarer des constantes de Compilation conditionnelle  
 Vous pouvez définir des constantes de compilation conditionnelle dans un des trois façons :  
  
-   Dans la **Concepteur de projets**  
  
-   Sur la ligne de commande lorsque vous utilisez le compilateur de ligne de commande  
  
-   Dans votre code  
  
 Constantes de compilation conditionnelle ont une portée spéciale et ne sont pas accessibles à partir du code standard. La portée d’une constante de compilation conditionnelle est dépendante de la façon dont elle est définie. Le tableau suivant répertorie la portée des constantes déclarées à l’aide de chacune des trois méthodes mentionnées ci-dessus.  
  
|La constante a la valeur|Étendue de constante|  
|---|---|  
|**Concepteur de projets**|Public à tous les fichiers dans le projet|  
|Ligne de commande|Public à tous les fichiers passés au compilateur de ligne de commande|  
|`#Const`instruction dans le code|Privé pour le fichier dans lequel elle est déclarée|  
  
|Pour définir des constantes dans le Concepteur de projets|  
|---|  
|-Avant de créer votre fichier exécutable, définissez des constantes dans le **Concepteur de projets** en suivant les étapes fournies dans [gestion de projet et les propriétés de la Solution](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Pour définir des constantes au niveau de la ligne de commande|  
|---|  
|-Utilisez le **/d** commutateur pour entrer des constantes de compilation conditionnelle, comme dans l’exemple suivant :<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Aucun espace n’est nécessaire entre la **/d** commutateur et la première constante. Pour plus d’informations, consultez [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Les déclarations de ligne de commande substituent les déclarations entrées dans le **Concepteur de projet**, mais ne les suppriment pas. Arguments définis **Concepteur de projets** restent en vigueur pour les compilations ultérieures.<br />     Lorsque vous écrivez des constantes dans le code lui-même, ne sont pas des règles strictes sur leur emplacement, car leur étendue est l’ensemble du module dans lequel ils sont déclarés.|  
  
|Pour définir des constantes dans votre code|  
|---|  
|-Placez les constantes dans le bloc de déclaration du module dans lequel ils sont utilisés. Cela permet de garder votre code organisé et plus facile à lire.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|---|---|  
|[Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Fournit des suggestions pour rendre votre code facile à lire et mettre à jour.|  
  
## <a name="reference"></a>Référence  
 [#Const (directive)](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
