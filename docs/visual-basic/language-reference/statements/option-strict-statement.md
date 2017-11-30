---
title: Option Strict Statement
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: "49"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 238f64001b097b86306e0ed9630bd5df2e6a189f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="option-strict-statement"></a>Option Strict Statement
Restreint les conversions de types de données implicites aux seules conversions étendues, n’autorise pas la liaison tardive et n’autorise pas le typage implicite qui entraîne une `Object` type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`On`|Facultatif. Permet de `Option Strict` la vérification.|  
|`Off`|Facultatif. Désactive `Option Strict` la vérification.|  
  
## <a name="remarks"></a>Remarques  
 Lorsque `Option Strict On` ou `Option Strict` apparaît dans un fichier, les conditions suivantes provoquent une erreur de compilation :  
  
-   Conversions restrictives implicites  
  
-   Liaison tardive  
  
-   Typage implicite qui entraîne une `Object` type  
  
> [!NOTE]
>  Dans les configurations d’avertissement que vous pouvez définir sur le [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), il existe trois paramètres qui correspondent aux trois conditions qui provoquent une erreur de compilation. Pour plus d’informations sur la façon d’utiliser ces paramètres, consultez [pour définir les configurations des avertissements dans l’IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) plus loin dans cette rubrique.  
  
 La `Option Strict Off` instruction désactive l’erreur et la vérification de l’avertissement pour tous les trois conditions, même si les paramètres IDE associés spécifient d’activer sur ces erreurs ou avertissements. La `Option Strict On` instruction active d’erreur et avertissement recherchant tous les trois conditions, même si les paramètres IDE associés spécifient pour désactiver ces erreurs ou avertissements.  
  
 Si utilisé, la `Option Strict` instruction doit apparaître avant toute autre instruction de code dans un fichier.  
  
 Lorsque vous définissez `Option Strict` à `On`, Visual Basic vérifie que les types de données sont spécifiés pour tous les éléments de programmation. Types de données peuvent être spécifiés explicitement ou spécifiés à l’aide de l’inférence de type local. Spécification des types de données pour tous les éléments de programmation est recommandé pour les raisons suivantes :  
  
-   Il permet la prise en charge IntelliSense pour les variables et des paramètres. Cela vous permet de vous permet de voir leurs propriétés et autres membres que vous tapez le code.  
  
-   Il permet au compilateur d’effectuer la vérification du type. Vérification de type vous permet de trouver des instructions qui peuvent échouer au moment de l’exécution en raison d’erreurs de conversion de type. Il identifie également les appels aux méthodes sur des objets qui ne prennent pas en charge ces méthodes.  
  
-   Cela accélère l’exécution du code. Une des raisons sont que si vous ne spécifiez pas un type de données pour un élément de programmation, le compilateur Visual Basic lui assigne la `Object` type. Code compilé peut avoir à convertir entre `Object` et d’autres types de données, ce qui réduit les performances.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Erreurs de Conversion restrictive implicite  
 Erreurs de conversion restrictive implicite se produisent lorsqu’il existe une conversion de type de données implicite est une conversion restrictive.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]peut convertir les nombreux types de données à d’autres types de données. Une perte de données peut se produire lorsque la valeur d’un type de données est convertie en un type de données qui a moins de précision ou une capacité réduite. Une erreur d’exécution se produit si une telle conversion restrictive échoue. `Option Strict`garantit la notification de compilation de ces conversions restrictives afin que vous puissiez les éviter. Pour plus d’informations, consultez [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) et [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Les conversions qui peuvent provoquer des erreurs incluent des conversions implicites qui se produisent dans les expressions. Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [+ (opérateur)](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= (opérateur)](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/ =, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char (type de données)](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Lorsque vous concaténez des chaînes à l’aide de la [& opérateur](../../../visual-basic/language-reference/operators/concatenation-operator.md), toutes les conversions en chaînes sont considérées comme des étendues. Pour ces conversions ne génèrent pas d’une erreur de conversion restrictive implicite, même `Option Strict` sur.  
  
 Lorsque vous appelez une méthode qui a un argument qui a un type de données différent du paramètre correspondant, une conversion restrictive provoque une erreur de compilation si `Option Strict` se trouve sur. Vous pouvez éviter l’erreur de compilation à l’aide d’une conversion étendue ou une conversion explicite.  
  
 Erreurs de conversion restrictive implicite sont supprimées au moment de la compilation pour les conversions entre les éléments dans un `For Each…Next` collection à la variable de contrôle de boucle. Cela se produit même si `Option Strict` se trouve sur. Pour plus d’informations, consultez la section « Conversions restrictives » dans [For Each... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Erreurs de liaison tardive  
 Un objet est tardive lorsqu’elle est assignée à une propriété ou méthode d’une variable qui est déclarée comme étant de type `Object`. Pour plus d’informations, consultez [anticipée et liaison tardive](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Erreurs de Type d’objet implicite  
 Erreurs de type d’objet implicite se produisent lorsqu’un type approprié ne peut pas être déduit pour une variable déclarée, par conséquent, un type de `Object` est déduit. Cela se produit principalement lorsque vous utilisez un `Dim` instruction pour déclarer une variable sans utiliser un `As` clause, et `Option Infer` est désactivée. Pour plus d’informations, consultez [Option Infer, instruction](../../../visual-basic/language-reference/statements/option-infer-statement.md) et [spécification du langage Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 Pour les paramètres de méthode, le `As` clause est facultative si `Option Strict` est désactivée. Toutefois, si un paramètre utilise un `As` clause, tous les ils doivent l’utiliser. Si `Option Strict` est activé, le `As` clause est requise pour chaque définition de paramètre.  
  
 Si vous déclarez une variable sans utiliser un `As` clause et affectez-lui la valeur `Nothing`, la variable a un type de `Object`. Aucune erreur de compilation se produit dans ce cas lorsque `Option Strict` sur et `Option Infer` sur. Est un exemple de ce `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Types de données et valeurs par défaut  
 Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d’un initialiseur dans une [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Type de données spécifié ?|Initialiseur spécifié ?|Exemple|Résultat|  
|---|---|---|---|  
|Non|Non|`Dim qty`|Si `Option Strict` est désactivé (par défaut), la valeur affectée à la variable est `Nothing`.<br /><br /> Si `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Non|Oui|`Dim qty = 5`|Si `Option Infer` est activée (par défaut), la variable prend le type de données de l'initialiseur. Consultez [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Oui|Non|`Dim qty As Integer`|La variable est initialisée avec la valeur par défaut du type de données. Pour plus d’informations, consultez [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Oui|Oui|`Dim qty  As Integer = 5`|Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Lorsqu’une instruction Option Strict n’est pas présente  
 Si le code source ne contient pas un `Option Strict` instruction, le **Option stricte** définition sur le [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé. Le **Page Compiler** possède des paramètres qui offrent un contrôle supplémentaire sur les conditions qui génèrent une erreur.  
  
 Si vous utilisez le compilateur de ligne de commande, vous pouvez utiliser la [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) option du compilateur pour spécifier un paramètre pour `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Pour définir Option Strict dans l’IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  Dans l’**Explorateur de solutions**, sélectionnez un projet. Dans le menu **Projet**, cliquez sur **Propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Sur le **compiler** onglet, définissez la valeur dans la **Option Strict** boîte.  
  
###  <a name="conditions"></a>Pour définir les configurations des avertissements dans l’IDE  
 Lorsque vous utilisez la [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) au lieu d’un `Option Strict` instruction, vous avez un contrôle supplémentaire sur les conditions qui génèrent des erreurs. Le **configurations des avertissements** section de la **Page Compiler** possède des paramètres qui correspondent aux trois conditions qui provoquent une erreur de compilation lorsque `Option Strict` sur. Voici ces paramètres :  
  
-   **Conversion implicite**  
  
-   **Liaison tardive ; appel peut échouer au moment de l’exécution**  
  
-   **Type implicite ; Object pris par défaut**  
  
 Lorsque vous définissez **Option Strict** à **sur**, tous les trois de ces paramètres de configuration d’avertissement sont définis sur **erreur**. Lorsque vous définissez **Option Strict** à **hors**, tous les trois paramètres sont définies sur **aucun**.  
  
 Vous pouvez modifier individuellement chaque avertissement paramètre de configuration sur **aucun**, **avertissement**, ou **erreur**. Si tous les trois paramètres de configuration de l’avertissement sont définies sur **erreur**, `On` s’affiche dans le `Option strict` boîte. Si les trois sont définies sur **aucun**, `Off` apparaît dans cette zone. Pour toute autre combinaison de ces paramètres, **(personnalisé)** s’affiche.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Pour définir l’Option Strict de valeur par défaut pour les nouveaux projets  
 Lorsque vous créez un projet, le **Option Strict** définition sur le **compiler** onglet est définie sur le **Option Strict** définition dans le **Options** boîte de dialogue.  
  
 Pour définir `Option Strict` dans cette boîte de dialogue, sur le **outils** menu, cliquez sur **Options**. Dans le **Options** boîte de dialogue, développez **projets et Solutions**, puis cliquez sur **valeurs par défaut VB**. Le paramètre par défaut initial dans **valeurs par défaut VB** est `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Pour définir Option Strict sur la ligne de commande  
 Inclure le [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) option du compilateur dans le **vbc** commande.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent des erreurs de compilation provoquées par les conversions de types implicites qui sont des conversions restrictives. Cette catégorie d’erreurs correspond à la **conversion implicite** condition sur la **Page Compiler**.  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une erreur de compilation due à liaison tardive. Cette catégorie d’erreurs correspond à la **en retard de liaison ; l’appel peut échouer au moment de l’exécution** condition sur la **Page Compiler**.  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent des erreurs provoquées par des variables qui sont déclarées avec un type implicite de `Object`. Cette catégorie d’erreurs correspond à la **type implicite ; object pris par défaut** condition sur la **Page Compiler**.  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Page Compiler, Concepteur de projet (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Option Explicit (instruction)](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Guide pratique : accéder aux membres d’un objet](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Conversion simplifiée des délégués](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Liaison tardive dans les solutions Office](https://msdn.microsoft.com/library/3xxe951d)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
