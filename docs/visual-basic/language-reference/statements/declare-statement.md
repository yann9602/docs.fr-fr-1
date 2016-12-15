---
title: "Declare Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Declare"
  - "vb.Lib"
  - "vb.Any"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Lib keyword"
  - "declaring procedures, Declare statement"
  - "functions [Visual Basic], function procedures"
  - "declarations, procedures"
  - "procedures, declaration"
  - "procedures, external"
  - "Alias keyword"
  - "external references, Visual Basic"
  - "DLLs, declaring procedures"
  - "Declare statement"
  - "declarations, external"
  - "Visual Basic code, Function procedures"
  - "As keyword, in Declare statement"
  - "resources [Visual Basic], declaring"
  - "Public keyword, Declare statement"
  - "platform invoke, Visual Basic external references"
  - "Sub procedures, declarations"
  - "APIs, declaring API functions"
  - "Visual Basic code, Sub procedures"
  - "Function procedures, declaring"
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declare Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Déclare une référence à une procédure implémentée dans un fichier externe.  
  
## Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ]  
' -or-  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`attributelist`|Facultatif.  Consultez [Liste d'attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Facultatif.  Il peut s'agir de l'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Facultatif.  Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|Facultatif.  Spécifie le jeu de caractères et les informations de recherche de fichier.  Il peut s'agir de l'une des valeurs suivantes :<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) \(par défaut\)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Auto](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|Facultatif, mais `Sub` ou `Function` doit être indiqué.  Indique que la procédure externe ne retourne pas de valeur.|  
|`Function`|Facultatif, mais `Sub` ou `Function` doit être indiqué.  Indique que la procédure externe retourne une valeur.|  
|`name`|Obligatoire.  Nom de cette référence externe.  Pour plus d'informations, consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Lib`|Obligatoire.  Introduit une clause `Lib` qui identifie le fichier externe \(DLL ou ressource de code\) contenant une procédure externe.|  
|`libname`|Obligatoire.  Nom du fichier contenant la procédure déclarée.|  
|`Alias`|Facultatif.  Indique que la procédure déclarée ne peut pas être identifiée dans son fichier par le nom spécifié dans `name`.  Vous spécifiez son identification dans `aliasname`.|  
|`aliasname`|Requis si vous utilisez le mot clé `Alias`.  Chaîne qui identifie la procédure de l'une des deux manières suivantes :<br /><br /> Nom du point d'entrée de la procédure dans son fichier, entre guillemets \(`""`\)<br /><br /> ou<br /><br /> Signe dièse \(`#`\) suivi d'un entier qui spécifie le nombre ordinal du point d'entrée de la procédure dans son fichier|  
|`parameterlist`|Requis si la procédure prend des paramètres.  Consultez [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Obligatoire si `Function` est spécifié et que `Option Strict` a la valeur `On`.  Type de données de la valeur retournée par la procédure.|  
  
## Notes  
 Parfois, vous devez appeler une procédure définie dans un fichier \(par exemple une DLL ou une ressource de code\) en dehors de votre projet.  Lorsque vous procédez ainsi, le compilateur Visual Basic n'a pas accès aux informations nécessaires pour appeler la procédure correctement, à savoir l'emplacement de la procédure, son mode d'identification, sa séquence d'appel et son type de retour, ainsi que le jeu de caractères qu'elle utilise.  L'instruction `Declare` crée une référence à une procédure externe et fournit ces informations nécessaires.  
  
 Vous pouvez utiliser `Declare` seulement au niveau du module.  Cela signifie que le *contexte de déclaration* pour une référence externe doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Les références externes prennent par défaut l'accès [Public](../../../visual-basic/language-reference/modifiers/public.md).  Vous pouvez régler leurs niveaux d'accès avec les modificateurs d'accès.  
  
## Règles  
  
-   **Attributs.** Vous pouvez appliquer des attributs à une référence externe.  Les attributs que vous appliquez n'ont effet que sur votre projet et non sur le fichier externe.  
  
-   **Modificateurs.** Les procédures externes sont implicitement [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  Vous ne pouvez pas utiliser le mot clé `Shared` lorsque vous déclarez une référence externe et vous ne pouvez pas modifier son état partagé.  
  
     Une procédure externe ne peut pas participer à la substitution, à l'implémentation des membres d'interface ou à la gestion d'événements.  Par conséquent, vous ne pouvez pas utiliser le mot clé `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements` ou `Handles` dans une instruction `Declare`.  
  
-   **Nom de la procédure externe.** Il n'est pas nécessaire d'attribuer à cette référence externe le même nom \(dans `name`\) que celui du point d'entrée de la procédure dans son fichier externe \(`aliasname`\).  Vous pouvez utiliser une clause `Alias` pour spécifier le nom du point d'entrée.  Elle peut s'avérer utile si la procédure externe porte le même nom qu'un modificateur réservé Visual Basic, une variable, une procédure ou tout autre élément de programmation de la même portée.  
  
    > [!NOTE]
    >  Dans la plupart des DLL, les noms de points d'entrée respectent les majuscules et les minuscules.  
  
-   **Numéro de la procédure externe.** Vous pouvez également utiliser une clause `Alias` pour spécifier le nombre ordinal du point d'entrée dans la table d'exportation du fichier externe.  Pour ce faire, commencez `aliasname` par un signe dièse \(`#`\).  Ce procédé peut s'avérer utile si un caractère du nom de la procédure externe n'est pas admis en Visual Basic ou si le fichier externe exporte la procédure sans nom.  
  
## Règles relatives aux types de données  
  
-   **Types de données des paramètres.** Si `Option Strict` a la valeur `On`, vous devez spécifier le type de données de chaque paramètre dans `parameterlist`.  Il peut s'agir de n'importe quel type de données ou du nom d'une énumération, d'une structure, d'une classe ou d'une interface.  Dans `parameterlist`, vous utilisez une clause `As` pour spécifier le type de données de l'argument à passer à chaque paramètre.  
  
    > [!NOTE]
    >  Si la procédure externe n'a pas été écrite pour .NET Framework, vous devez veiller à ce que les types de données correspondent.  Si, par exemple, vous déclarez une référence à une procédure Visual Basic 6.0 avec un argument `Integer` \(16 bits dans Visual Basic 6.0\), vous devez identifier l'argument correspondant comme `Short` dans l'instruction `Declare`, puisqu'il s'agit du type entier de 16 bits dans Visual Basic.  De même, `Long` a une largeur de données différente dans Visual Basic 6.0 et `Date` est implémenté différemment.  
  
-   **Type de données retournées.** Si la procédure externe est une `Function` et que `Option Strict` a la valeur `On`, vous devez spécifier le type de données de la valeur retournée au code appelant.  Il peut s'agir de n'importe quel type de données ou du nom d'une énumération, d'une structure, d'une classe ou d'une interface.  
  
    > [!NOTE]
    >  Le compilateur Visual Basic ne vérifie pas que vos types de données sont compatibles avec ceux de la procédure externe.  En cas d'incompatibilité, le Common Language Runtime génère une exception <xref:System.Runtime.InteropServices.MarshalDirectiveException> au moment de l'exécution.  
  
-   **Types de données par défaut.** Si `Option Strict` a la valeur `Off` et que vous ne spécifiez pas le type de données d'un paramètre dans `parameterlist`, le compilateur Visual Basic convertit l'argument correspondant en type de données [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).  De même, si vous ne spécifiez pas `returntype`, le compilateur considère le type de données retournées comme `Object`.  
  
    > [!NOTE]
    >  Étant donné que vous gérez une procédure externe qui a pu être écrite sur une plateforme différente, il est risqué de faire des hypothèses sur les types de données ou de leur affecter des valeurs par défaut.  Il est beaucoup plus sûr de spécifier le type de données de chaque paramètre et de la valeur de retour, le cas échéant.  La lisibilité de votre code est également améliorée.  
  
## Comportement  
  
-   **Portée.** Une référence externe est à portée dans toute sa classe, sa structure ou son module.  
  
-   **Durée de vie.** Une référence externe a la même durée de vie que la classe, la structure ou le module dans lequel elle est déclarée.  
  
-   **Appel d'une procédure externe.** Vous appelez une procédure externe de la même manière que vous appelez une procédure `Function` ou `Sub`, en l'utilisant dans une expression si elle retourne une valeur ou en la spécifiant dans un [Call Statement](../../../visual-basic/language-reference/statements/call-statement.md) si elle ne retourne pas de valeur.  
  
     Vous passez des arguments à la procédure externe exactement comme spécifié par `parameterlist` dans l'instruction `Declare`.  Ne prenez pas en compte comment les paramètres ont été initialement déclarés dans le fichier externe.  De même, s'il y a une valeur de retour, utilisez\-la exactement comme spécifié par `returntype` dans l'instruction `Declare`.  
  
-   **Jeux de caractères.** Vous pouvez spécifier dans `charsetmodifier` comment Visual Basic doit marshaler les chaînes lorsqu'il appelle la procédure externe.  Le modificateur `Ansi` demande à Visual Basic de marshaler toutes les chaînes en valeurs ANSI, tandis que le modificateur `Unicode` lui demande de les marshaler en valeurs Unicode.  Le modificateur `Auto` demande à Visual Basic de marshaler les chaînes en fonction des règles .NET Framework basées sur le `name` de la référence externe ou de `aliasname` si spécifié.  La valeur par défaut est `Ansi`.  
  
     `charsetmodifier` spécifie également comment Visual Basic doit rechercher la procédure externe dans son fichier externe.  Les deux langages `Ansi` et `Unicode` orientent Visual Basic à le rechercher sans modifier son nom pendant la recherche.  `Auto` dirige Visual Basic pour déterminer le jeu de caractères de base de la plateforme à l'exécution et peut\-être modifier le nom de procédure externe, comme suit :  
  
    -   sur une plateforme ANSI, telle que Windows 95, Windows 98 ou Windows Millennium, recherchez d'abord la procédure externe sans modifier son nom.  En cas d'échec, ajoutez « A » à la fin du nom de la procédure externe et recherchez\-la à nouveau ;  
  
    -   sur une plateforme Unicode, telle que Windows NT, Windows 2000 ou Windows XP, recherchez d'abord la procédure externe sans modifier son nom.  En cas d'échec, ajoutez « W » à la fin du nom de la procédure externe et recherchez\-la à nouveau.  
  
-   **Mécanisme.** Visual Basic utilise le mécanisme d'*appel de code non managé* \(PInvoke\) .NET Framework pour résoudre et accéder aux procédures externes.  L'instruction `Declare` et la classe <xref:System.Runtime.InteropServices.DllImportAttribute> utilisent ce mécanisme automatiquement et il n'est pas nécessaire d'avoir des connaissances sur PInvoke.  Pour plus d'informations, consultez [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  Si la procédure externe s'exécute en dehors du Common Language Runtime \(CLR\), il s'agit de *code non managé*.  Lorsque vous appelez une telle procédure, par exemple une fonction API Win32 ou une méthode COM, vous pouvez exposer votre application à des risques de violation de sa sécurité.  Pour plus d'informations, consultez [Instructions de codage sécurisé pour le code non managé](../Topic/Secure%20Coding%20Guidelines%20for%20Unmanaged%20Code.md).  
  
## Exemple  
 L'exemple suivant déclare une référence externe à une procédure `Function` qui retourne le nom d'utilisateur actuel.  Elle appelle ensuite la procédure externe `GetUserNameA` dans le cadre de la procédure `getUser`.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## Exemple  
 L'<xref:System.Runtime.InteropServices.DllImportAttribute> fournit une solution de remplacement pour l'utilisation des fonctions dans du code non managé.  L'exemple suivant déclare une fonction importée sans le recours à une instruction `Declare`.  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Call Statement](../../../visual-basic/language-reference/statements/call-statement.md)   
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)