---
title: "Option Strict Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Strict"
  - "vb.OptionStrict"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Strict keyword"
  - "Option Strict statement"
  - "conversions, implicit"
  - "late binding"
  - "implicit conversions"
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: 49
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 49
---
# Option Strict Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Limite les conversions de types de données implicites uniquement aux conversions étendues, rejette la liaison tardive et rejette la saisie implicite qui résulte en un type `Object`.  
  
## Syntaxe  
  
```  
Option Strict { On | Off }  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`On`|Facultatif.  Active la vérification `Option Strict`.|  
|`Off`|Facultatif.  Désactive la vérification `Option Strict`.|  
  
## Notes  
 Lorsque `Option Strict On` ou `Option Strict` apparaît dans un fichier, les conditions suivantes provoquent une erreur de compilation :  
  
-   Conversions restrictives implicites  
  
-   Liaison tardive  
  
-   Type implicite qui génère un type `Object`  
  
> [!NOTE]
>  Dans les configurations d'avertissement que vous pouvez définir sur [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic), il existe trois paramètres qui correspondent aux trois conditions qui provoquent une erreur de compilation.  Pour plus d'informations sur l'utilisation de ces paramètres, consultez [Pour définir les configurations des avertissements dans l'IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) plus loin dans cette rubrique.  
  
 L'instruction `Option Strict Off` désactive l'erreur et l'avertissement examinant pour chacune des trois conditions, même si les paramètres IDE associés spécifient d'activer ces erreurs ou avertissements.  L'instruction d' `Option Strict On` active l'erreur et l'avertissement recherchant les trois conditions, même si les paramètres associés IDE spécifient d'intercepter ces erreurs ou avertissements.  
  
 Si elle est utilisée, l'instruction `Option Strict` doit apparaître avant toute autre instruction de code source dans un fichier.  
  
 Lorsque vous `Option Strict` défini à `On`, Visual Basic vérifie que les types de données sont spécifiés pour tous les éléments de programmation.  Les types de données peuvent être spécifiés explicitement, ou être spécifiés à l'aide de l'inférence de type local.  Spécifier les types de données pour tous les éléments de programmation est recommandé, pour les raisons suivantes :  
  
-   Cela permet la prise en charge de IntelliSens pour vos variables et vos paramètres.  Il vous permet de voir leurs propriétés et leurs autres membres à mesure que vous tapez le code.  
  
-   Il permet au compilateur d'effectuer la vérification des types.  La vérification de type vous aide à rechercher les instructions susceptibles d'échouer au moment de l'exécution en raison d'erreurs de conversion de type.  Il identifie également les appels de méthodes sur les objets qui ne prennent pas en charge ces méthodes.  
  
-   Elle permet d'accélérer l'exécution du code.  La raison de ceci est que si vous ne spécifiez pas de type de données pour un élément de programmation, le compilateur Visual Basic lui assigne le type d' `Object` .  Le code compilé peut peut\-être convertir dans les deux sens entre `Object` et d'autres types de données, ce qui réduit les performances.  
  
## Erreurs de conversion restrictive implicite  
 Les erreurs de conversion restrictive implicite se produisent lorsqu'il y a une conversion de types de données implicite qui est une conversion restrictive.  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] peut convertir de nombreux types de données en d'autres types de données.  Une perte de données peut se produire si la valeur de l'un des types de données est convertie en un type de données dont la précision ou la capacité est moindre.  Une erreur d'exécution se produit si une telle conversion restrictive échoue.  `Option Strict` garantit la notification de compilation de ces conversions restrictives afin qu'ils puissent être évités.  Pour plus d'informations, consultez [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) et [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Les conversions qui peuvent provoquer des erreurs se composent des conversions implicites qui se produisent dans les expressions.  Pour plus d'informations, consultez les rubriques suivantes :  
  
-   [\+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [\+\= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Lorsque vous concaténez des chaînes à l'aide de [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md), toutes les conversions en chaînes sont considérées élargir.  Pour que ces conversions ne génèrent pas d'erreur de conversion restrictive implicite, même si `Option Strict` est activée.  
  
 Lorsque vous appelez une méthode qui possède un argument qui contient un type de données différent du paramètre correspondant, une conversion restrictive provoque une erreur de compilation si `Option Strict` est activé.  Vous pouvez éviter cette erreur de compilation en utilisant une conversion étendue ou une conversion explicite.  
  
 Les erreurs de conversion restrictive implicite sont supprimées lors de la compilation pour les conversions à partir des éléments d'une collection `For Each…Next` vers la variable de contrôle de boucle.  Cela se produit même si `Option Strict` est activé.  Pour plus d'informations, consultez la section « Conversions restrictives » dans [For Each...Next, instruction](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## Erreurs de liaison tardive  
 Un objet a une liaison tardive lorsqu'il est assigné à une propriété ou à une méthode d'une variable déclarée comme étant de type `Object`.  Pour plus d'informations, consultez [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md).  
  
## Erreurs de type d'objet implicite  
 Les erreurs de type d'objet implicite se produisent lorsqu'un type approprié ne peut pas être déduit pour une variable déclarée, de sorte qu'un type `Object` est déduit.  Cela se produit essentiellement lorsque vous utilisez une instruction `Dim` pour déclarer une variable sans utiliser une clause `As` et que `Option Infer` est désactivé.  Pour plus d'informations, consultez [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) et [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md).  
  
 Pour les paramètres de méthode, la clause `As` est facultative si `Option Strict` est désactivé.  Toutefois, si un paramètre utilise une clause `As`, ils doivent tous l'utiliser.  Si `Option Strict` est activé, la clause `As` est nécessaire pour chaque définition de paramètre.  
  
 Si vous déclarez une variable sans utiliser de clause `As` et que vous la définissez sur `Nothing`, la variable a un type `Object`.  Aucune erreur de compilation ne se produit dans ce cas lorsque `Option Strict` est activé et `Option Infer` est activé.  Un exemple est `Dim something = Nothing`.  
  
### Valeurs et types de données par défaut  
 Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et de l'initialiseur dans une [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|||||  
|-|-|-|-|  
|Type de données spécifié ?|Initialiseur spécifié ?|Exemple|Résultat|  
|Non|Non|`Dim qty`|Si `Option Strict` est désactivé \(valeur par défaut\), la variable a la valeur `Nothing`.<br /><br /> Si `Option Strict` est activée, une erreur de compilation se produit.|  
|Non|Oui|`Dim qty = 5`|Si `Option Infer` est activé \(valeur par défaut\), la variable prend le type de données de l'initialiseur.  Consultez [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` et `Option Strict` sont désactivés, la variable prend le type de données de `Object`.<br /><br /> Si `Option Infer` est désactivé et `Option Strict` est activé, une erreur de compilation se produit.|  
|Oui|Non|`Dim qty As Integer`|La variable est initialisée avec la valeur par défaut du type de données.  Pour plus d'informations, consultez [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Oui|Oui|`Dim qty  As Integer = 5`|Si le type de données de l'initialiseur n'est pas convertible en type de données spécifié, une erreur de compilation se produit.|  
  
## Lorsqu'aucune instruction Option Strict n'est présente  
 Si le code source ne contient pas d'instruction `Option Strict`, le paramètre **Option strict** sur [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) est utilisé.  La **Page Compiler** dispose des paramètres qui fournissent un contrôle supplémentaire sur les conditions qui génèrent une erreur.  
  
 Si vous utilisez le compilateur de ligne de commande, vous pouvez utiliser l'option du compilateur [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) pour spécifier un paramètre pour `Option Strict`.  
  
### Pour définir Option Strict dans l'IDE  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez un projet.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l'onglet **Compilation** et définissez la valeur figurant dans la zone **Option Strict**.  
  
###  <a name="conditions"></a> Pour définir les configurations des avertissements dans l'IDE  
 Lorsque vous utilisez [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) au lieu d'une instruction `Option Strict`, vous avez le contrôle supplémentaire des conditions qui génèrent des erreurs.  La section **Configurations des avertissements** de **Compiler la page** contient des paramètres qui correspondent aux trois conditions qui provoquent une erreur de compilation lorsque `Option Strict` est activé.  Vous trouverez ci\-dessous ces paramètres :  
  
-   **Conversion implicite**  
  
-   **Liaison tardive ; l'appel pourrait échouer lors de l'exécution**  
  
-   **Type implicite ; objet supposé**  
  
 Lorsque vous affectez la valeur **On** à **Option Strict**, chacun de ces trois paramètres de configuration d'avertissement prend la valeur **Erreur**.  Lorsque vous affectez la valeur **Off** à **Option Strict**, chacun des trois paramètres prend la valeur **Aucun**.  
  
 Vous pouvez remplacer individuellement chaque paramètre de configuration d'avertissement par **Aucun**, **Avertissement** ou **Erreur**.  Si les trois paramètres de configuration de l'avertissement sont définis sur **Erreur**, `On` apparaît dans la zone `Option strict`.  Si les trois sont définis sur **None**, `Off` apparaît dans cette zone.  Pour toute autre combinaison de ces paramètres, **\(personnalisé\)** apparaît.  
  
### Pour définir la valeur par défaut d'Option Strict pour les nouveaux projets  
 Lorsque vous créez un projet, le paramètre **Option Strict** de l'onglet **Compiler** a la valeur du paramètre **Option Strict** de la boîte de dialogue **Options**.  
  
 Pour définir la boîte de dialogue `Option Strict`, dans le menu **Outils**, cliquez sur **Options**.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  Le paramètre par défaut initial dans **Valeurs par défaut VB** est `Off`.  
  
### Pour définir Option Strict sur la ligne de commande  
 Incluez l'option du compilateur [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) dans la commande **vbc**.  
  
## Exemple  
 Les exemples suivants illustrent des erreurs de compilation provoquées par les conversions de types implicites qui sont des conversions restrictives.  Cette catégorie d'erreurs correspond à la condition **Conversion implicite** sur la **Page Compiler**.  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## Exemple  
 L'exemple suivant illustre une erreur de compilation provoquée par la liaison tardive.  Cette catégorie d'erreurs correspond à la condition **Liaison tardive ; l'appel peut échouer au moment de l'exécution** sur la **Page Compiler**.  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## Exemple  
 Les exemples suivants illustrent des erreurs provoquées par des variables qui sont déclarées avec un type implicite d'`Object`.  Cette catégorie d'erreurs correspond à la condition **Type implicite ; objet pris par défaut** sur la **Page Compiler**.  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## Voir aussi  
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [How to: Access Members of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Liaison tardive dans les solutions Office](/office-dev/office-dev/late-binding-in-office-solutions)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)